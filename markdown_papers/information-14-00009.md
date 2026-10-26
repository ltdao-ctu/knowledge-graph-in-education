---
title: "information-14-00009"
source: "information-14-00009.pdf"
source_sha256: "d7f17abe30532830f153aed2c64094abbfd32d7c7be2f55664bc35bd35945320"
converted_at: "2026-10-26T07:05:09.923843+00:00"
markitdown_version: "0.1.9"
---
informatio n
Article
Path-Based Recommender System for Learning Activities Using
Knowledge Graphs
ChristosTroussas* andAkriviKrouska
DepartmentofInformaticsandComputerEngineering,UniversityofWestAttica,12243Egaleo,Greece
* Correspondence:ctrouss@uniwa.gr
Abstract:Recommendersystemscanofferafertilegroundine-learningsoftware,sincetheycanassist
usersbypresentingthemwithlearningmaterialinwhichtheycanbemoreinterested,basedontheir
preferences.Tothisend,inthispaper,wepresentanewmethodforaknowledge-graph-based,path-
basedrecommendersystemforlearningactivities.Thesuggestedapproachmakesbetterlearning
activityrecommendationsbyusingconnectionsbetweenpeopleand/orproducts.Bypre-defining
meta-paths or automatically mining connective patterns, our method uses the student-learning
activitygraphtofindpath-levelcommonalitiesforlearningactivities.Thepath-basedapproachcan
provideanexplanationfortheresultaswell. Ourmethodologyisusedinanintelligenttutoring
systemwithJavaprogrammingasthedomainbeingtaught.Thesystemkeepstrackofuserbehavior
andcanrecommendlearningactivitiestostudentsusingaknowledge-graph-basedrecommender
system.Numerousmetadata,suchaskind,complexity,andnumberofquestions,areusedtodescribe
eachactivity.Thesystemhasbeenevaluatedwithpromisingresultsthathighlighttheeffectivenessof
thepath-basedrecommendationsforlearningactivities,whilepreservingthepedagogicalaffordance.
Keywords:knowledgegraphs;knowledge-graph-basedrecommendersystem;path-basedreasoning;
recommendersystem;intelligenttutoringsystem;learningactivityrecommendations
1. Introduction
Citation:Troussas,C.;Krouska,A.
The amount of available data has multiplied tremendously with the quick devel-
Path-BasedRecommenderSystemfor
opmentoftheinternet. Assuch, usersmayfaceanunfriendlyenvironmentwhenthey
LearningActivitiesUsingKnowledge
use a system, since they struggle to select what may interest them from a plethora of
Graphs.Information2023,14,9.
optionsduetotheoverabundanceofinformation. Towardassistingusersintheprocess
https://doi.org/10.3390/
ofproceedingtothemostadequateselection,recommendersystemshavebeenusedto
info14010009
providesuggestionsforitemsthataremostrelevanttoacertainuser[1]. Intheliterature,
AcademicEditors:PierpaoloBasile recommendersystemshavebeenusedindifferentfieldsofapplication,e.g.,e-shops,online
andAnnalinaCaputo movierecommendations,andsongsrecommendations.
Recommender systems have been used to support e-learning software [2]. In e-
Received:22November2022
learningrecommendersystems,therecommendationmostlydependsontheitemcontent
Revised:20December2022
Accepted:21December2022 anduserbehaviorsobservedwhentheuserisinteractingwiththeonlinetutoringsystem.
Published:23December2022 Forinstance,recommendersystemsine-learningsoftwarecanproviderecommendations
concerning students’ learning styles, learning resources, learning activities, courses, or
evenlearningpathways[3–5]. Learningactivities’contentandtypesmaybeambiguous
anduncertaininformationforstudents. Inmanye-learningsystems,studentsareprovided
Copyright: © 2022 by the authors.
withspecificlearningactivitiestoconduct. However,recommendersystemscanhelpin
Licensee MDPI, Basel, Switzerland.
this direction by proposing specific activities to students in a personalized way, while
This article is an open access article
preservingtheeducationalqualityofthelearningprocess.
distributed under the terms and
Forthedevelopmentofrecommendersystems,theapproachesthathavebeenmainly
conditionsoftheCreativeCommons
usedbyresearchersarecollaborativefiltering,content-basedfiltering,orhybridapproaches[6].
Attribution(CCBY)license(https://
Thepremisebehindcollaborativefilteringisthatpeoplewhohavepreviouslyagreedwill
creativecommons.org/licenses/by/
dosoagainandthattheywillcontinuetoenjoythesamekindsofthings.Recommendations
4.0/).
Information2023,14,9.https://doi.org/10.3390/info14010009 https://www.mdpi.com/journal/information

Information2023,14,9 2of13
aregeneratedbythealgorithmsolelybasedondatafromratingprofilesforvariouspersons
orobjects. Itproducesrecommendationsbyusingthislocationtofindpeerusersorobjects
withratinghistoriessimilartotheoneofthecurrentuseroritem. However,adescription
of the item and a profile of the user’s preferences serve as the foundation for content-
basedfilteringtechniques. Thesetechniquesworkbestwheninformationabouttheitem
(name,location,description,etc.),butnottheuser,isknown. Content-basedrecommenders
approachrecommendationsasauser-specificclassificationissueandlearnaclassifierfora
user’spreferencesbasedonthecharacteristicsofanitem. Inthisapproach,thethingsare
describedusingkeywords,andauserprofileiscreatedtoshowthekindsofitemsthisuser
prefers. Inotherwords,thesealgorithmsstrivetosuggestproductsthatarecomparableto
thosethataconsumerhaspreviouslyenjoyedorisnowlookingat. Finally,thecombination
oftheaforementionedtechniquescanformhybridrecommendersystems.
Recently,researchershavebecomeinterestedinaddingaknowledgegraph(KG)as
sideinformationtorecommendersystems[7]. AKGisaheterogeneousnetworkinwhich
thenodesserveasentitiesandtherelationssignifytheconnectionsamongsuchentities.
To comprehend the relationships between items, it is possible to map items and their
propertiesintotheKG.Furthermore,theincorporationofusersanduser-sidedatainto
the KG allows for a more precise recording of user relationships with items as well as
userpreferences. Theexplainabilityofrecommendationresultsisanotheradvantageof
KG-basedrecommendersystems.
Knowledge-graph-basedrecommendersystemsareclassifiedaccordingtohowthey
usetheKGdata,asfollows: embedding-basedmethods,path-basedmethods,andunified
methods[6]. Embedding-basedmethodsdirectlyaugmenttherepresentationofitemsor
userswithdatafromtheKG.Knowledgegraphembedding(KGE)techniquesmustbe
usedtoencodetheKGintolow-rankembeddingsbeforetheKGinformationcanbeused.
Path-basedtechniquescreateauser–itemgraphandusetheentity’sconnectivitypatterns
inthenetworktoproviderecommendations. Path-basedapproacheshavebeenreferredto
inresearchstudiesasrecommendationsintheheterogeneousinformationnetwork. The
connection similarity of users and/or objects is typically exploited by these models to
improverecommendations. Unifiedtechniquesthatincorporateboththesemanticrepre-
sentationofentitiesandrelationsandtheconnectivityinformationhavebeenproposedin
ordertofullyusethedataintheKGforimprovedsuggestions. Embeddingpropagation
theoryservesasthefoundationfortheunifiedmethod. Thesetechniquesimproveentity
representationunderthedirectionoftheKG’sconnectivestructure.
In this paper, we present a novel approach for a path-based recommender system
forlearningactivitiesusingknowledgegraphs. Thepresentedmodelusestheconnection
similarity of users and/or items in order to improve the recommendation of learning
activities. Ourapproachusestheuser(student)–item(learningactivity)graphtouncover
path-levelsimilaritiesforitems(learningactivities),eitherbypre-definingmeta-pathsor
byautomaticallyminingconnectivepatterns. Thepath-basedmethodcanalsodeliveran
explanationfortheoutcome. Ourmodelisincorporatedinanintelligenttutoringsystem,
andthedomaintobetaughtistheprogramminglanguageJava. Thesystemmonitorsthe
actionsofusersandthroughtheknowledge-graph-basedrecommendersystemcansuggest
learningactivitiestostudents. Eachactivityischaracterizedbyseveralmetadata,suchas
type,difficulty,numberofquestions,andrevisedBloom’staxonomy(RBT)level. Thenovel
recommendersystemcanpreservethepedagogicalaffordancethroughthesophisticated
wayofsuggestinglearningactivities. Inviewofthis,thecontributionofthispaperliesin
thepresentationofanovelpath-basedrecommendersystemusingknowledgegraphsinthe
fieldofeducationandspecificallyforsuggestingadequatelearningactivities. Furthermore,
it includes the use of specific learning activity metadata as well as the monitoring of
learners’actions.
The main research questions that this paper answers are (1) how effective are the
recommendationsoflearningactivitiestousersand(2)doestherecommendersystemhave
apositiveimpactonlearning?

Information2023,14,9 3of13
Therestof thispaper is organized asfollows. In Section 2, areviewof therelated
researchworksispresented. InSection3,adescriptionofthepath-basedrecommender
systemisprovided,asitsincorporationinthee-learningsoftwareisshownandanexample
ofoperationisprovided. InSection4,theevaluationresultsarepresentedandadiscussion
onthemisprovided. Finally,inSection5,conclusionsaredrawnandfutureresearchsteps
aredescribed.
2. RelatedLiterature
Inthissection,therelatedliteratureonrecommendersystemsingeneralandknowledge-
graph-basedrecommendersystemsisanalyzed.
2.1. RecommenderSystems
Recommender systems have been investigated for various fields in the related sci-
entific literature. Their application in e-learning environments [2,8–10], entertainment
websites[11–14],socialsettings[15–18],andtouristsystems[19–22]areafewexamples.
Collaborativefiltering,content-basedfiltering,machinelearning,andhybridapproaches
arethealgorithmicstrategiesthathavebeenusedmostfrequentlyintheresearchpapers
mentionedbefore. Accordingtoastudyof2019[23],asingle-criteriaratingservesasthe
mainsourcefortherecommendationprocessforthemajorityofrecommendersystems
(overallrating). Anotherstudyof2020[24]reportsthatcollaborativefiltering,atechnique
thathasbeenwidelyusedintheliteraturetoconstructrecommendersystems,hasavariety
ofdrawbacks,includingthecold-startproblem,whichmeansthatthesystemcannotmake
inferencesaboutpeopleorthingsforwhichinsufficientdatahavebeencollected.
Asmentionedearlier,theresearchfieldofrecommendersystemsine-learningenviron-
mentsisactive. Insuchsystems,therearetwocrucialelements: (1)thelearnerstowhom
thesystemoffersrecommendationshavespecificcharacteristicsthatmaybedifficulttobe
defined,suchasknowledgelevel,and(2)thesuggestionsthataretobedeliveredtothe
learnersmayhaveastrongimpactonknowledgeacquisition,suchaslearningactivities,
learningmaterial,andassessmentunits.
Inlightofthesefindings,itisevidentthatadditionalresearchisneededintheareaof
recommendersystemdevelopment.
2.2. Knowledge-Graph-BasedRecommenderSystems
Knowledgegraphshavebeenintroducedinrecommendersystemsasauxiliarydata
that can track changes in user interests and add insight to recommendations. Indeed,
therehasbeenanactiveresearchareathatexploresknowledge-graph-basedrecommender
systems. Theyhavebeenusedinvariousdomains,suchastravelwebsites[25–27],online
museums[28–30],biomedicalsystems[31–33],e-commerceservices[34–36],andmovie
websites[37–39]. Intheaforementionedstudies,andasclearlystatedintworecentreview
papers [6,7], the methods of recommender systems with knowledge graphs that have
beenusedintheliteratureareembedding-basedmethods,connection-basedmethods,and
propagation-basedmethods.
Morespecifically,concerningpath-basedrecommendersystems,in[40],theauthors
developedtheSemRec,whichconsiderstheinteractionoftheuser’sfavoriteanddisliked
prior items. To integrate attribute values in the link, this architecture uses a weighted
meta-path. Moreaccurateitemrelationsandusersimilaritiescanbedepictedusingthese
channelstodisseminatetheactualuserpreferencebymodelingbothpositiveandnegative
preferencepatterns. In[41],theauthorsintroducedMCRec,whichgeneratesexplicitmeta-
pathrepresentationstoreflecttheinteractioncontextofuser–itempairs. In[42],theauthors
introducedarecurrentknowledgegraphembeddingtechniquethatautomaticallymines
theroutelinkbetweenuseranditemwithoutrequiringtheusertoprovidemeta-paths.
In[43]. Theauthorsdesignedatechniqueforsequentialrecommendationthatleverages
users’fluctuatinginterests. Finally,in[44],theauthors’strategyseekstoofferanordered
pathofimportantacademicpapers,whichareextremelyusefulinassistingresearchers

Information2023,14,9 4of13
in understanding the evolution of a certain issue. They use both content and network
structuretolearntherepresentationofadocumentduringtheprocess. Followingthat,the
representationisusedtoassessthesimilarityofpapers.
Analyzingtherelatedliteratureoftheareaofknowledge-graph-basedrecommender
systemsinthefieldofe-learning(needlesstosay,fortherecommendationoflearningactiv-
itiestostudents),itneedstobeemphasizedthatthereissignificantroomforimprovement
inthisdirection.
Inviewofthis,themotivationforthisresearchemergedfromthefactthattheafore-
mentioned technological advancements create a fertile ground for the development of
knowledge-graph-based systems that embrace a high degree of sophistication in their
recommendationmechanismtailoredtothefieldofe-learning. Theresearcheffortinthis
fieldisstillinitsinfancy,andmanyaspectsremainunexplored.
3. DescriptionoftheKnowledge-Graph-BasedRecommenderSystem
3.1. Path-BasedMethodforRecommendations
Inourapproach,theincorporatedpath-basedmethodcreatesauser–itemgraphand
usestheentity’sconnectivitypatternsinthenetworktoproviderecommendations. The
connectionsimilarityofusersand/orobjectsisexploitedtoimprovetherecommendation
oflearningactivities. Inthegenerateduser–itemgraph,thenodesconcernusersoritems,
whileedgesconcerntheinteractionsbetweenusersanditems.
3.1.1. RepresentationoftheNetwork
AgraphG=(E,R)isusedtorepresentournetwork,whereE={e ,e ,...,e }denotesn
1 2 n
entitiesandRisthesetofrelationsinG.Everynodeeandeverylinkrareconnectedwith
theirrespectivemappingfunctions,y(e): E→K andz(e): R→K . Thesetsofpre-defined
E R
objectsandrelationtypesaredenotedbyK andK . Tolearnthelatentrepresentationof
E R
learningactivities,amappingfunctionΓ: E→Rh(h≤|E|)isused.
3.1.2. RepresentationoftheLearningActivity
Apathintheformofe →e →... →e thatrepresentsachainfromnewlearning
i,1 i,2 i,k
activities to previous learning activities is referred to as a learning activity path. There
isarelationshipbetweenthepath’snearbynodese i,k−1 ande i,k . Itshouldbenotedthat
learningactivitiesarecharacterizedbymetadata,asmentionedbefore.
3.1.3. RepresentationofthePathRecommendationProbability
Theprobabilityofrecommendingalearningactivitypathisdefinedasthesimilarity
betweentherepresentationoftheprovidedlearningactivityandthatofthesuggestedpath,
givenapathP={e e ... e },whichsignifiesapathofrecommendedlearningactivities.
i,1 i,2 i,k
3.1.4. RepresentationoftheMulti-RelationalGraph
Initsmostbasicform,thenetworkisamulti-relationalheterogeneousgraph,whose
relationsdenotenumerousconnectionsandcontainvariousdegreesofsemanticrelatedness.
Inourmodel,weconsiderthelearningactivity–learningactivitynetworkanduser–learning
activity–RBTlevel–difficultynetwork.
Learningactivity–RBTlevel: Thegraph’shomogeneousnetworkiscreatedbythe
relationshipbetweenlearningactivities. Weusearandomwalk-basedsamplingtechnique
tolearnthelatentrepresentationofthenodesinordertoassessthelatentrelationships
betweenthem. Weusethetwoparameterspandqtobiasourrandomwalkstowardthe
localareaortotendtomovefurtherawaywhenwegeneratethem. Wedefineawindow
sizeofkafterproducingarandomwalk,andNs(u)standsfortheneighborhoodfornodeu
intheslidingwindow. Assumethatγ :
E→Rhisthefunctionthatmapsnodestofeature
1

Information2023,14,9 5of13
representations. Thesimilarityoftwonodese ande inlearningactivity–learningactivity
i j
spaceare:
γ (e)γ (e )
1 i 1 j
f c (e i ,e j ) =cos(γ 1 (e i ), γ 1 (e j )) = ||γ 1 (e i )|| (cid:12) (cid:12) (cid:12) (cid:12)γ 1 (e j ) (cid:12) (cid:12) (cid:12) (cid:12)
Student–LearningActivity–RBTlevel–Difficulty–NumberofUnits: Withoutade-
finedrelationship,thelearningactivity–learningactivityrelationshipcannotproviderelat-
ednessinformationbetweenlearningactivities. Wealsoconsideradditionaltiestoobtaina
betterrelatednessrating. Weusethe“student–learningactivity–student”and“student–
learningactivity–RBTlevel–learningactivity–student”meta-pathschemes,whicharethe
twomostpopularandusefulmeta-pathschemes. Welearnefficientnoderepresentations
byincludingvarioustypesofnodesintoskip-gramsusingameta-path-basedrandomwalk
technique. Weadditionallysuenegativesamplingfornetworklearningtoachieveeffective
optimization. Thesimilarityofthetwonodese ande inthe“student–learningactivity–
i j
RBTlevel–difficulty–numberofunits”spacecanbedefinedasfollowsafterlearningthe
networkrepresentation:
γ (e)γ (e )
2 i 2 j
f a (e i ,e j ) =cos(γ 2 (e i ), γ 2 (e j )) = ||γ 2 (e i )|| (cid:12) (cid:12) (cid:12) (cid:12)γ 2 (e j ) (cid:12) (cid:12) (cid:12) (cid:12)
3.1.5. ExplanationofNotations
G:TheknowledgegraphGconsistsofasetofnodesEandasetofrelationshipsR.
E:ThesetofnodesEincludesacollectionofentities,suchasstudents.
R:ThesetofrelationshipsRincludesacollectionofedgesthatconnectnodesinthegraph
andrepresentvarioustypesofrelationshipsbetweenentities. Forexample,Rcaninclude
edgesrepresenting“complete,”“level,”etc.
e: Aspecificedgeinthegraphisreferredtoase.
K : K isasetofattributesthatdescribeeachentityinthegraph. Forexample,K can
E E E
includeattributessuchas“complexity”forlearningactivity.
K : K isasetofattributesthatdescribeeachrelationshipinthegraph.
R R
γ: γisafunctionthatmapseachentitynodetoafeaturevectorrepresentation.
h: histhedimensionalityofthefeaturevectorrepresentationsproducedbyγ.
Anexampleofthedescribedknowledgegraphcanbeasfollows:
Matchingactivity:
Entity: “Matchingactivity”
Properties:
Name: “MatchingJavaconceptswithexplanation”
Type: “Matchingactivity”
Difficultylevel: “Easy”
RBT-level: “RBT-L1”
Score: “90%”
Numberofunits: “5”
Memoryactivity:
Entity: “Memoryactivity”
Properties:
Name: “RemembertheoperatorsinJava”
Type: “Memoryactivity”
Difficultylevel: “Moderate”
RBT-level: “RBT-L1”
Score: “75%”
Numberofunits: 6
Multiple-choiceactivity:
Entity: “Multiple-choiceactivity”
Properties:
Name: “Multiple-choiceJavaquiz”

Information2023,14,9 6of13
Type: “Multiple-choiceactivity”
Difficultylevel: “Challenging”
RBT-level: “RBT-L1”
Score: “65%”
Numberofunits: “8”
Theknowledgegraphcouldthenincluderelationshipsbetweenthedifferentactivities
andthestudent,suchasthestudentcompletingtheactivitiesandreceivingacertainscore
onthem. Thisinformationcouldbeusedtotrackthestudent’sprogressandtoidentify
areaswheretheymayneedadditionalsupport. Hereisanexampleofaknowledgegraph
thatcouldbeusedtorepresentastudent’sactivities:
G:Thesetofallentitiesintheknowledgegraph,includingstudentsandactivities.
G={student,matchingactivity,memoryactivity,multiple-choiceactivity}
E:Thesetofalledgesintheknowledgegraph,representingrelationshipsbetweenentities.
E={(student,completes,matchingactivity),(student,completes,memoryactivity),(student,
completes,multiple-choiceactivity),(matchingactivity,level,RBT-L1),(memoryactivity,
level,RBT-L1),(multiple-choiceactivity,difficulty,moderate)}
R:Thesetofallentitytypesintheknowledgegraph,suchas“student”and“learningactivity.”
R={student,activity}
e: Afunctionthatmapsanedgetoitscorrespondingentities.
e(student,completes,matchingactivity)=(student,matchingactivity)
K : Thesetofalledgetypesintheknowledgegraph,e.g.,“completes.”
E
K : Thesetofallpossibleattribute–valuepairsforeachentitytype.
R
K (student)={name,age,gradelevel}
R
KR(activity)={name,type,difficultylevel,RBT-level,score,numberofunits}
γ: Afunctionthatmapsanentitytoitscorrespondingentitytype.
γ(student)=student
γ(matchingactivity)=activity
h: Afunctionthatmapsanentitytoitscorrespondingattribute–valuepairs.
h(student)={name: “AkriviKrouska”,age: “20”,gradelevel: “undergraduate”}
h(matchingactivity)={name:“MatchingJavaconceptswithexplanation”,type:“Matching
activity”,difficultylevel: “Easy”,RBT-level: “RBT-L1”,score: “90%”,Numberofunits: “5”}
Inourexample,thefunctionf (e,e)isusedtomeasurethesimilarityoftwostudents
c i j
basedonthelearningactivitiestheycompleted. Thefunctionconsidersthesedataand
calculates a similarity score based on the degree of overlap between the two sets. The
highertheoverlap,thehigherthesimilarityscore.
Ingeneral,thefunctionf (e,e)isdesignedtomeasureanytypeofsimilaritybetween
c i j
twonodesinthepresentedknowledgegraph.
3.2. OverviewoftheRecommendedItemsoftheE-LearningSoftware
Thedomainknowledgeofthee-learningsoftwarecomprisesconceptsoftheprogram-
minglanguageJavainanundergraduatelevelofthecomputerengineeringcurriculum.
Thedomainknowledgeconsistsof13chapters,rangingincomplexityfrombasicideasto
morecomplexones.
Thedomainknowledgeincludesvariouslearningactivitiesofdifferenttypesbased
on the revised Bloom’s taxonomy (RBT) [45]. This taxonomy offers a framework for
categorizinglearningoutcomesintosixcategories,fromthemostfundamentaltothemost
complicated,inaccordancewithstudents’cognitiveabilities. TheRBTlevelsareasfollows:
remembering(RBT-L1),understanding(RBT-L2),applying(RBT-L3),analyzing(RBT-L4),
evaluating(RBT-L5),andcreating(RBT-L6).
Inadditiontothis,thelearningactivitiescanrangeindifficulty,meaningthateach
activity can be either easier or more difficult. The levels of difficulty are three: easy,
moderate,andchallenging. InformationaboutthelearningactivitiesispresentedinTable1.

Information2023,14,9 7of13
Table1.RBTlevels.
RBTLevel TypesofLearningActivities DifficultyLevel
True/falseactivity,bookmarking,flashcards,readingmaterial,memory
RBT-L1
activities,watchingpresentationsandvideos,matchingactivity
Createananalogy,groupdiscussions,takingnotes,storytelling,
RBT-L2
diagrams,flowcharts
Conceptmaps,problem-solvingexamples,learningthroughshortanswers,
RBT-L3 Easy,moderate,challenging
demonstrations,groupwork,practiceandcalculate
(appliedtoallRBTlevels)
Fishbowls,debating,runatest,casestudies,compareandcontrast
RBT-L4
(withcharts,tables),groupinvestigation,questionnaires
RBT-L5 Survey,reviewpapers,blogging,listswithadvantages/disadvantages
Createanewmodel,programmingordebuggingactivities,research
RBT-L6
projects,developanddescribenewsolutionsorplans,brainstorming
Finally,metadataoflearningactivitiesincludethenumberofunits,existingineach
learningactivity,e.g.,atrue/falseactivitymayinclude10questionstobeanswered.
Itneedstobenotedthatthenumberofrecommendedactivitiescanbechangedby
theinstructor.
3.3. ExampleofOperation
Figure1illustratesanexampleofoperationofaknowledge-graph-basedrecommen-
dationprovidedbythesystem. Oursystemrecommendsamatchingactivity,amemory
activity, and a multiple-choice activity to Student 1. The presented knowledge graph
isasnapshotofthedevelopedrecommendersystem,anditcontainsstudents,learning
activities,RBTlevels,difficultylevel,andnumberofunitsasentities,whilecompletelevel,
difficulty,belong,number,andclassmatesaretherelationshipsbetweenentities.Theknowl-
edgegraphconnectslearningactivitiesandstudentswithmanylatentrelationships,which
helpstoincreasetheaccuracyofrecommendations. Theresultsofrecommendationscanbe
betterillustratedandexplained,whichisanotheradvantageoftheknowledge-graph-based
recommendersystem.Followingtherelationshipsequencesinthestudent–learningactivity
graphinthesamescenariowillrevealthejustificationsforsuggestingtheseaforementioned
Information 2023, 14, x FOR PEER REVlIeEaWrn ingactivitiestoStudent1. Forinstance,onereasonforrecommendingthema8t cohf in14g
activityisthatitbelongstothesameRBTlevelasflashcards,whichhasbeenpreviously
completedbyStudent1successfully.
FFiigguurree 11. .EExxaammpplele oof fooppeerraatitoionn. .
4. System Evaluation
The phase of software evaluation is significant in order to assess its level of efficacy
and acceptance by its users. In our case, the duration of the evaluation phase was an aca-
demic semester. The students used the e-learning software in the context of their compul-
sory course on object-oriented programming with Java language. Though the evaluation,
we answered the two research questions (of Section 1). Particularly, both research ques-
tions are answered in the first part of the evaluation, while the second part of the evalua-
tion answers additionally answers the second research question.
4.1. Population
The students who participated in the experiment are in their undergraduate studies,
and their field of study is informatics and computer engineering in a public university in
the capital city of the country (Table 2). In total, 100 students took part in the experiment
and were divided into two equal groups by the evaluators and their university professors.
Students in group 1 used the presented e-learning software incorporating the knowledge-
graph-based recommender system. Students in group 2 used another version of the sys-
tem, which had the same domain to be taught as well as the same interface. The difference
was that the recommendations of the learning activities were given solely based on the
RBT level to which they belonged.
Table 2. Characteristics of the population.
Characteristics Group 1 Group 2
Average age 19.4 19.3
Gender 24 female, 26 male 25 female, 25 male
Demographics Same number of students of urban and rural origins
Computer expertise Advanced computer skills
Prior knowledge level in All participants are students in the same year of studies and
computer programming have successfully passed the previous programming courses.
All students attended the “Programming with Java” course and
Motivation
wanted to achieve a high grade.

Information2023,14,9 8of13
4. SystemEvaluation
Thephaseofsoftwareevaluationissignificantinordertoassessitslevelofefficacyand
acceptancebyitsusers. Inourcase,thedurationoftheevaluationphasewasanacademic
semester. Thestudentsusedthee-learningsoftwareinthecontextoftheircompulsory
courseonobject-orientedprogrammingwithJavalanguage. Thoughtheevaluation,we
answeredthetworesearchquestions(ofSection1). Particularly,bothresearchquestions
areansweredinthefirstpartoftheevaluation,whilethesecondpartoftheevaluation
answersadditionallyanswersthesecondresearchquestion.
4.1. Population
Thestudentswhoparticipatedintheexperimentareintheirundergraduatestudies,
andtheirfieldofstudyisinformaticsandcomputerengineeringinapublicuniversityin
thecapitalcityofthecountry(Table2). Intotal,100studentstookpartintheexperiment
andweredividedintotwoequalgroupsbytheevaluatorsandtheiruniversityprofessors.
Studentsingroup1usedthepresentede-learningsoftwareincorporatingtheknowledge-
graph-basedrecommendersystem. Studentsingroup2usedanotherversionofthesystem,
whichhadthesamedomaintobetaughtaswellasthesameinterface. Thedifferencewas
thattherecommendationsofthelearningactivitiesweregivensolelybasedontheRBT
leveltowhichtheybelonged.
Table2.Characteristicsofthepopulation.
Characteristics Group1 Group2
Averageage 19.4 19.3
Gender 24female,26male 25female,25male
Demographics Samenumberofstudentsofurbanandruralorigins
Computerexpertise Advancedcomputerskills
Priorknowledgelevelin Allparticipantsarestudentsinthesameyearofstudiesand
computerprogramming havesuccessfullypassedthepreviousprogrammingcourses.
Allstudentsattendedthe“ProgrammingwithJava”courseand
Motivation
wantedtoachieveahighgrade.
Itneedstobenotedthatthepresentedsystemwasusedasasupplementtoformal
education. Thesameappliestothesystem’sleaningactivities,whichsupplementthein-
classactivities. Theinstructorsprovidedhelptostudentswhileusingthesystem,butthey
didnotinterferewiththerecommendationsdeliveredtolearnersbythesystem. Finally,
theonlinelearningactivitiesweregraded,butthisgradedidnotaffectthefinalgradeof
learners in the course; the students participated in the final examination, and only this
gradewasconsideredinordertopassthecoursesuccessfully.
4.2. ResultsandDiscussion
First,thesystemevaluationconsidersthreeaspects: userexperience,effectivenessof
therecommendersystem,andimpactonlearning[46,47]. Asaresult,aquestionnairewith
a10-pointLikertscale,withtwoquestionsfortheevaluationofthefirstaspectaswellas
threequestionsfortheevaluationofthesecondandthirdaspects,respectively(Table3),
wasdeliveredtostudents. Towardevaluatingthereliabilityofthequestionnaire,weused
Cronbach’salpha,whichwasrunonthesample. Thealphacoefficientwas0.96,showing
thatourscaleandtheparticularsamplehadahighlevelofinternalconsistency.
Table3.Questionnaire.
Aspect No. Questions
Q1 Ratetheuserinterfaceofthee-learningsoftware.
Userexperience
Ratethelearningexperienceafteryourlastinteractionwith
(UE) Q2
thesoftware.

Information2023,14,9 9of13
Table3.Cont.
| Aspect |     | No. |     |     |     | Questions |     |     |     |
| ------ | --- | --- | --- | --- | --- | --------- | --- | --- | --- |
Q3 Didthelearningactivitiescorrespondtoyourcognitivelevel?
Effectivenessofthe Ratetheadequacyofdifficultylevelofthelearningactivities
Q4
| recommender |     |     |     |     | thathavebeenrecommendedtoyou. |     |     |     |     |
| ----------- | --- | --- | --- | --- | ----------------------------- | --- | --- | --- | --- |
system(ER) Ratetheadequacyofthedegreeofcomplexityofthelearning
Q5
activitiesthathavebeenrecommendedtoyou.
Didyoufindthee-learningsoftwarehelpyouadvanceyour
Q6
| Impacton |     |     |     |     | knowledgeinJavaprogramming? |     |     |     |     |
| -------- | --- | --- | --- | --- | --------------------------- | --- | --- | --- | --- |
learning(IL) Q7 Wouldyouliketousethisplatforminothercoursesaswell?
|     |     | Q8  | Wouldyousuggestthesoftwaretoyourfriendstouseit? |     |     |     |     |     |     |
| --- | --- | --- | ----------------------------------------------- | --- | --- | --- | --- | --- | --- |
All the students answered the questionnaire when delivered at the end of the aca-
demicsemester.
Thestudents’answerswereaggregatedbasedontheaspecttowhichthecorrespond-
ingquestionsbelong. Furthermore,the10-pointLikertscaleanswerswereconvertedinto
threecategories,namely:
• Low: rangingfrom1to3;
• Average: rangingfrom4to7;
• High: rangingfrom8to10.
Information 2023, 14, x FOR PEER REVIEW  10 of 14
  In Figure 2, the results concerning the answers of students in groups 1 and 2
arepresented.

FFiigguurree 22.. QQuueessttiioonnnnaaiirree rreessuullttss..
CCoonncceerrnniinngg ththeea sapsepcetcotf oufs eurseexrp eerxipenerciee,ntchee, rtehspe ornessepsoonfssetsu doef nsttsuidnegnrtosu pin1 gsrhoouwpe d1
ashhoigwhedra tai nhgig(h72 r%at)i,nwgh (i7le2%th)e, wrehspiloen tshees roefssptuondseenst soifn sgturoduepnt2s sinho gwroeudpa 23 2s%horwateindg a. T3h2%is
draiftfienrge.n Tcheirse dveifafelsrethnacet trheeveeaxlpse trhieant cteheo fexstpuedrieenntcsei nofg srotuudpe1ntws ains mgrooruepp 1o switaivs em,porroeb paobslyi-
btievcea,u psreotbhaebilryr ebsepcoanussees thweeirr ereasffpeocntesdesb wyethree aafdfeecqtuedat ebya ntdhep aedrseoqnuaaltiez eadndre cpoemrsmoneanlidzeedd
lreeacronminmgeancdtievdit ileesar(envinegn athcotiuvgithietsh (eeyvewne rtheonuogthe xtphleiyci twlyeraes kneodt eaxbpoulictiittlyin atshkeedqu aebsotiuotn ist oinf
tthhee fiqrusetsatisopnesc to)f. Mtheo rfeirosvt ears,p7e6c%t).o Mfsoturedoevnetrs, i7n6%gr oouf pst1udaepnptrsa iinse gdrothuepe 1ff aepctpivraeinseesds tohfet hefe-
recommendersystem,whileonly10%ofstudentsingroup2appraisedtheeffectivenessof fectiveness of the recommender system, while only 10% of students in group 2 appraised
therecommendersystem. Thisdifferencewasexpectedsincethepresentedrecommender
the effectiveness of the recommender system. This difference was expected since the pre-
systemincorporatesthepath-basedmethodofarecommendersystemwithaknowledge sented recommender system incorporates the path-based method of a recommender sys-
graph.Thepresentedmethodsuggestslearningactivitiestostudentsbasedonsophisticated
tem with a knowledge graph. The presented method suggests learning activities to stu-
reasoning, whereas the RBT-based method of recommendations of the system used by
dents based on sophisticated reasoning, whereas the RBT-based method of recommenda-
group 2 explores solely the RBT levels of learning activities. Finally, the results of the
tions of the system used by group 2 explores solely the RBT levels of learning activities.
responsesinthequestionsoftheaspectimpactoflearningwere70%forgroup1and10%
Finally, the results of the responses in the questions of the aspect impact of learning were
70% for group 1 and 10% for group 2. This fact accentuates the importance of the presented
knowledge-graph-based recommender system, highlighting its positive impact on learn-
ing.
Toward further exploring the effect of the recommender system on students, the sta-
tistical hypothesis test (t-test) was used, comparing the presented system (used by group
1) to its conventional version (used by group 2). The t-test was applied in questions Q3–
Q5. Table 4 presents the t-test findings.
Table 4. The t-test findings.
|     |     |     |     | Q3  |     | Q4  |     | Q5  |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

|                  |           |     | Group 1   |     | Group 2   | Group 1 Group 2 Group 1 Group 2  |       |          |     |
| ---------------- | --------- | --- | --------- | --- | --------- | -------------------------------- | ----- | -------- | --- |
|                  | Mean      |     | 8.48      |     | 3.64      | 8                                | 3.54  | 8.38     | 4   |
|                  | Variance  |     | 2.703673  |     | 4.888163  | 3.142857 3.559592 4.117959       |       |          | 6   |
| Observations     |           |     | 50        |     | 50        | 50                               | 50    | 50       | 50  |
| Pooled variance  |           |     | 3.795918  |     |           | 3.351224                         |       | 5.05898  |     |
Hypothesized mean differ-
|     |     |     |     | 0   |     | 0   |     | 0   |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
ence
|                      | df      |     | 98            |     |     | 98         |     | 98         |     |
| -------------------- | ------- | --- | ------------- | --- | --- | ---------- | --- | ---------- | --- |
|                      | t-Stat  |     | 12.42101      |     |     | 12.18157   |     | 9.736719   |     |
|                      |         |     |               |     |     | 1.24 × 10- |     | 2.26 × 10- |     |
| P(T ≤ t) one-tailed  |         |     | 3.85 × 10-22  |     |     |            |     |            |     |
|                      |         |     |               |     |     | 21         |     | 16         |     |

| Information2023,14,9 |     |     |     |     |     |     |     |     |     | 10of13 |
| -------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ------ |
forgroup2. Thisfactaccentuatestheimportanceofthepresentedknowledge-graph-based
recommendersystem,highlightingitspositiveimpactonlearning.
Toward further exploring the effect of the recommender system on students, the
statistical hypothesis test (t-test) was used, comparing the presented system (used by
group1)toitsconventionalversion(usedbygroup2). Thet-testwasappliedinquestions
|     |     | Q3–Q5. |     | Table4presentsthet-testfindings. |     |     |     |     |     |     |
| --- | --- | ------ | --- | -------------------------------- | --- | --- | --- | --- | --- | --- |
Table4.Thet-testfindings.
|                |              |          | Q3  |          |          | Q4  |          |          | Q5  |        |
| -------------- | ------------ | -------- | --- | -------- | -------- | --- | -------- | -------- | --- | ------ |
|                |              | Group1   |     | Group2   | Group1   |     | Group2   | Group1   |     | Group2 |
|                | Mean         | 8.48     |     | 3.64     | 8        |     | 3.54     | 8.38     |     | 4      |
|                | Variance     | 2.703673 |     | 4.888163 | 3.142857 |     | 3.559592 | 4.117959 |     | 6      |
|                | Observations | 50       |     | 50       | 50       |     | 50       | 50       |     | 50     |
| Pooledvariance |              | 3.795918 |     |          | 3.351224 |     |          | 5.05898  |     |        |
Hypothesized
|     |     | 0   |     |     | 0   |     |     | 0   |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
meandifference
|                  | df     | 98         |     |     | 98         |     |     | 98         |     |     |
| ---------------- | ------ | ---------- | --- | --- | ---------- | --- | --- | ---------- | --- | --- |
|                  | t-Stat | 12.42101   |     |     | 12.18157   |     |     | 9.736719   |     |     |
| P(T≤t)one-tailed |        | 3.85×10−22 |     |     | 1.24×10−21 |     |     | 2.26×10−16 |     |     |
| P(T≤t)two-tailed |        | 7.71×10−22 |     |     | 2.47×10−21 |     |     | 4.51×10−16 |     |     |
Basedontheseresults,itcanbeinferredthatthatthereisastatisticallysignificantdif-
ferencebetweenthemeansofthetwotrialsconcerningQ3,Q4,andQ5. Morespecifically,it
wasobservedthatthesoftwareusedbygroup1performedsignificantlywellinrecommend-
inglearningactivitiestostudentsthatcorrespondedtotheircognitivelevelincomparison
totheconventionalversionusedbygroup1(Q3: t-stat≈16.42,p<0.05). Additionally,
there was a significant difference in the adequacy of the difficulty level of the learning
activitiesthatwererecommendedtostudents(Q4)ingroup1(mean=8,variance≈3.14)
andgroup2(mean=3.54,variance≈3.55),wheret-stat≈12.18andp≈2.47×10−21.
The
sameappliesfortheadequacyofthedegreeofcomplexityofthelearningactivitiesthat
wererecommendedtostudents(Q5)ingroup1(mean=8.38,variance≈4.11)andgroup2
(mean=4,variance=6),wheret-stat≈9.73andp≈4.51×10−16.
Thesefindingsimplythatthesuggestedapproachperformsbetterthanitsconven-
tional version in terms of the appropriateness of learning activities that correspond to
students’cognitivelevel,theadequacyofthedifficultylevel,andthedegreeofcomplexity
ofthelearningactivitiesthatwererecommendedtostudents. Theseresultswereexpected
since the software, which uses a path-based method for recommender systems using a
knowledgegraph,recommendsadequatelearningactivitiestostudents. Suchactivities
cancreateapersonalizedlearningpathforstudentsandimprovefurthertheirlearning
outcomes. Thispath-basedreasoningforselectinglearningactivitiesmayhaveimportant
pedagogicalimplicationssincetherecommendationofappropriatelearningactivitiescould
furtherenhancethelearningexperience.
AsmentionedinSection2,similarknowledge-graph-basedrecommendersystems
have not yet been applied sufficiently in e-learning settings. Comparing the presented
approachtoothersthathavebeenusedinrecommendersystemsine-learningsoftware
(e.g.,content-basedfiltering,collaborativefiltering,hybridmethods,machinelearning),
it should be highlighted that the user–item graph’s inclusion of the potential informa-
tionbetweenusersanditems,whichcarriestheentireinformation,particularlysemantic
information,intothegraph,isoneofmajoradvantagesofthepath-basedmethod.

Information2023,14,9 11of13
5. ConclusionsandFutureWork
Inthispaper,weexploredthepath-basedmethodforrecommendersystemsusing
knowledge graphs in an e-learning environment. The system monitors the actions of
usersandthroughtheknowledge-graph-basedrecommendersystemcansuggestlearning
activitiestothem.Eachactivityischaracterizedbyseveralmetadata,suchastype,difficulty,
and number of questions. The novel recommender system has pedagogical affordance
throughthesophisticatedwayofsuggestinglearningactivities. Ourinvestigationshows
thatthismethodhaspositiveresultsandcancreateafertilegroundforfutureresearchto
thisdirection.
Limitations of this research include the exploration of only one method of recom-
mendersystemswithknowledgegraphs,namelythepath-basedmethod. Intherelated
literature, there are other methods as well, such as embedding-based methods or even
unifiedmethodsthathavenotbeenexploredaswell.
Future work includes the incorporation of machine learning into the presented
techniquetoexplorewhetheritcouldbefurtherimproved. Moreover,futureresearch
plansincludetheenrichmentofrecommendationstostudentswithpeerstocollaborate.
Finally,partofourfutureplansistoexplorethenumberofthelearningactivitiesthat
is required to incorporate in the recommender system to render it robust and offer
adequatepersonalization.
AuthorContributions:Conceptualization,C.T.andA.K.;methodology,C.T.andA.K.;software,C.T.
andA.K.; validation, C.T.andA.K.; formalanalysis,C.T.andA.K.; investigation,C.T.andA.K.;
resources,C.T.andA.K.;datacuration,C.T.andA.K.;writing—originaldraftpreparation,C.T.and
A.K.;writing—reviewandediting,C.T.andA.K.;visualization,C.T.andA.K.Allauthorshaveread
andagreedtothepublishedversionofthemanuscript.
Funding:Thisresearchreceivednoexternalfunding.
DataAvailabilityStatement:Dataareavailableonrequest.
ConflictsofInterest:Theauthorsdeclarenoconflictofinterest.
References
1. Ko,H.;Lee,S.;Park,Y.;Choi,A.ASurveyofRecommendationSystems:RecommendationModels,Techniques,andApplication
Fields.Electronics2022,11,141.[CrossRef]
2. Marques,G.A.;Rigo,S.J.;Alves,I.M.D.R.GraduationMentoringRecommender—HybridRecommendationSystemforCustomiz-
ingtheUndergraduateStudent’sFormativePath.InProceedingsofthe2021XVIIEEELatinAmericanConferenceonLearning
Technologies(LACLO),Arequipa,Peru,19–21October2021;pp.342–349.[CrossRef]
3. Papakostas,C.;Troussas,C.;Krouska,A.;Sgouropoulou,C.PersonalizationoftheLearningPathwithinanAugmentedReality
SpatialAbilityTrainingApplicationBasedonFuzzyWeights.Sensors2022,22,7059.[CrossRef][PubMed]
4. Agarwal,A.;Mishra,D.S.;Kolekar,S.V.Knowledge-basedrecommendationsystemusingsemanticwebrulesbasedonLearning
stylesforMOOCs.CogentEng.2022,9,2022568.[CrossRef]
5. Li, J.; Ye, Z. Course Recommendations in Online Education Based on Collaborative Filtering Recommendation Algorithm.
Complexity2020,2020,6619249.[CrossRef]
6. Guo,Q.;Zhuang,F.;Qin,C.;Zhu,H.;Xie,X.;Xiong,H.;He,Q.ASurveyonKnowledgeGraph-BasedRecommenderSystems.
IEEETrans.Knowl.DataEng.2022,34,3549–3568.[CrossRef]
7. Liu,J.;Duan,L.ASurveyonKnowledgeGraph-BasedRecommenderSystems.InProceedingsofthe2021IEEE5thAdvanced
Information Technology, Electronic and Automation Control Conference (IAEAC), Chongqing, China, 12–14 March 2021;
pp.2450–2453.[CrossRef]
8. Amara,S.;Subramanian,R.R.Collaboratingpersonalizedrecommendersystemandcontent-basedrecommendersystemusing
TextCorpus.InProceedingsofthe20206thIEEEInternationalConferenceonAdvancedComputingandCommunicationSystems
(ICACCS),Coimbatore,India,6–7March2020;pp.105–109.[CrossRef]
9. Fernández-García,A.J.;Rodríguez-Echeverría,R.;Preciado,J.C.;Manzano,J.M.C.;Sánchez-Figueroa,F.CreatingaRecommender
SystemtoSupportHigherEducationStudentsintheSubjectEnrollmentDecision.IEEEAccess2020,8,189069–189088.[CrossRef]
10. Chrysafiadi,K.;Troussas,C.;Virvou,M.AFrameworkforCreatingAutomatedOnlineAdaptiveTestsUsingMultiple-Criteria
DecisionAnalysis.InProceedingsofthe2018IEEEInternationalConferenceonSystems,Man,andCybernetics(SMC),Miyazaki,
Japan,7–10October2018;pp.226–231.[CrossRef]

Information2023,14,9 12of13
11. Kannikaklang,N.;Wongthanavasu,S.;Thamviset,W.AHybridRecommenderSystemforImprovingRatingPredictionofMovie
Recommendation. InProceedingsofthe202219thIEEEInternationalJointConferenceonComputerScienceandSoftware
Engineering(JCSSE),Bangkok,Thailand,22–25June2022;pp.1–6.[CrossRef]
12. Gupta,M.;Thakkar,A.;Gupta,V.;Rathore,D.P.S.Movierecommendersystemusingcollaborativefiltering.InProceedingsofthe
2020IEEEInternationalConferenceonElectronicsandSustainableCommunicationSystems(ICESC),Coimbatore,India,2–4July
2020;pp.415–420.
13. Singla,R.;Gupta,S.;Gupta,A.;Vishwakarma,D.K.FLEX:Acontent-basedmovierecommender.InProceedingsofthe2020IEEE
InternationalConferenceforEmergingTechnology(INCET),Belgaum,India,5–7June2020;pp.1–4.
14. Troussas,C.;Krouska,A.;Virvou,M.Multi-algorithmictechniquesandahybridmodelforincreasingtheefficiencyofrecom-
mendersystems. InProceedingsofthe2018IEEE30thInternationalConferenceonToolswithArtificialIntelligence(ICTAI),
Volos,Greece,5–7November2018;pp.184–188.
15. Yang,X.;Dong,M.;Chen,X.;Ota,K.Recommendersystem-baseddiffusioninferringforopensocialnetworks. IEEETrans.
Comput.Soc.Syst.2020,7,24–34.[CrossRef]
16. Wongkhamchan,T.;Namvong,A.;Surawanitkun,C.Personalizedrecommendersystemusingasocialnetworkbasedcollabora-
tivefilteringtechnique.InProceedingsofthe201916thIEEEInternationalConferenceonElectricalEngineering/Electronics,
Computer,TelecommunicationsandInformationTechnology(ECTI-CON),Pattaya,Thailand,10–13July2019;pp.846–849.
17. Mughaid,A.;Obeidat,I.;Hawashin,B.;AlZu’bi,S.;Aqel,D.Asmartgeo-locationjobrecommendersystembasedonsocial
mediaposts.InProceedingsofthe2019SixthIEEEInternationalConferenceonSocialNetworksAnalysis,Managementand
Security(SNAMS),Granada,Spain,22–25October2019;pp.505–510.
18. Liang,B.;Xu,B.;Wu,X.;Wu,D.;Yang,D.;Xiao,Y.;Wang,W.Acommunity-basedcollaborativefilteringmethodforsocial
recommendersystems.InProceedingsofthe2019IEEEInternationalConferenceonWebServices(ICWS),Milan,Italy,8–13July
2019;pp.159–162.
19. Baker, O.; Yuan, Q. Machine learning: Factorization Machines and Normalized Discounted Cumulative Gain for Tourism
RecommenderSystemOptimisation.InProceedingsofthe2021IEEEInternationalConferenceonComputing(ICOCO),Kuala
Lumpur,Malaysia,17–19November2021;pp.31–36.[CrossRef]
20. Srisawatsakul,C.;Boontarig,W.TourismRecommenderSystemusingMachineLearningBasedonUser’sPublicInstagram
Photos.InProceedingsofthe5thIEEEInternationalConferenceonInformationTechnology(InCIT),Chonburi,Thailand,21–22
October2020;pp.276–281.[CrossRef]
21. Chen,C.;Wu,X.;Chen,J.;Pardalos,P.M.;Ding,S.Dynamicgroupingofheterogeneousagentsforexplorationandstrikemissions.
Front.Inform.Technol.Electron.Eng.2022,23,86–100.[CrossRef]
22. Kbaier,M.E.B.H.;Masri,H.;Krichen,S.APersonalizedHybridTourismRecommenderSystem. InProceedingsofthe2017
IEEE/ACS14thInternationalConferenceonComputerSystemsandApplications(AICCSA),Hammamet,Tunisia,30October–3
November2017;pp.244–250.[CrossRef]
23. Al-Ghuribi,S.M.;MohdNoah,S.A.Multi-CriteriaReview-BasedRecommenderSystem–TheStateoftheArt.IEEEAccess2019,7,
169446–169468.[CrossRef]
24. Choi,S.-M.;Jang,K.;Lee,T.-D.;Khreishah,A.;Noh,W.Alleviatingitem-sidecold-startproblemsinrecommendersystemsusing
weaksupervision.IEEEAccess2020,8,167747–167756.[CrossRef]
25. Lan,J.;Shi,R.;Cao,Y.;Lv,J.KnowledgeGraph-basedConversationalRecommenderSysteminTravel.InProceedingsofthe2022
IEEEInternationalJointConferenceonNeuralNetworks(IJCNN),Padua,Italy,18–23July2022;pp.1–8.[CrossRef]
26. Dai,G.R.;Xu,J.Y.;Zhou,H.;Zhou,L.;Cao,Z.H.;Zhu,M.D.ATravellingRecommendationSystembasedonKnowledgeGraph.
InProceedingsofthe20213rdInternationalAcademicExchangeConferenceonScienceandTechnologyInnovation(IAECST),
Guangzhou,China,10–12December2021;pp.407–412.[CrossRef]
27. Dadoun,A.;Troncy,R.;Defoin-Platel,M.;Solano,G.A.Predictingyournexttrip:Aknowledgegraph-basedmulti-tasklearning
approachfortraveldestinationrecommendation.InProceedingsofthe2021WorkshoponRecommendersinTourism,RecTour
2021,Amsterdam,TheNetherlands,26September2021;Volume2974.
28. Deladiennee, L.; Naudet, Y. A graph-based semantic recommender system for a reflective and personalised museum visit:
Extendedabstract.InProceedingsofthe2017IEEE12thInternationalWorkshoponSemanticandSocialMediaAdaptationand
Personalization(SMAP),Bratislava,Slovakia,9–10July2017;pp.88–89.[CrossRef]
29. Minkov,E.;Kahanov,K.;Kuflik,T.Graph-basedrecommendationintegratingratinghistoryanddomainknowledge:Application
toon-siteguidanceofmuseumvisitors.J.Assoc.Inf.Sci.Technol.2017,68,1911–1924.[CrossRef]
30. Angelis,S.;Kotis,K.;Spiliotopoulos,D.SemanticTrajectoryAnalyticsandRecommenderSystemsinCulturalSpaces.BigData
Cogn.Comput.2021,5,80.[CrossRef]
31. Sousa,D.;Couto,F.M.BiomedicalRelationExtractionWithKnowledgeGraph-BasedRecommendations.IEEEJ.Biomed.Health
Inform.2022,26,4207–4217.[CrossRef][PubMed]
32. Gogleva,A.; Polychronopoulos,D.; Pfeifer,M.; Poroshin,V.; Ughetto,M.; Martin,M.J.; Thorpe,H.; Bornot,A.; Smith,P.D.;
Sidders,B.;etal.Knowledgegraph-basedrecommendationframeworkidentifiesdriversofresistanceinEGFRmutantnon-small
celllungcancer.Nat.Commun.2022,13,1667.[CrossRef][PubMed]

Information2023,14,9 13of13
33. Fecho,K.;Bizon,C.;Miller,F.;Schurman,S.;Schmitt,C.;Xue,W.;Morton,K.;Wang,P.;Tropsha,A.ABiomedicalKnowledge
GraphSystemtoProposeMechanisticHypothesesforReal-WorldEnvironmentalHealthObservations: CohortStudyand
InformaticsApplication.JMIRMed.Inform.2021,9,e26714.[CrossRef][PubMed]
34. Vijayakumar,S.;Jetcheva,J.G.SMARTREC:AConversationalRecommendationSystemUsingSemanticKnowledgeGraphs.In
Proceedingsofthe2022IEEEEighthInternationalConferenceonBigDataComputingServiceandApplications(BigDataService),
Newark,CA,USA,15–18August2022;pp.53–60.[CrossRef]
35. Lully,V.;Laublet,P.;Stankovic,M.;Radulovic,F.Enhancingexplanationsinrecommendersystemswithknowledgegraphs.
ProcediaComput.Sci.2018,137,211–222.[CrossRef]
36. Kartheek,M.;Sajeev,G.P.BuildingSemanticBasedRecommenderSystemUsingKnowledgeGraphEmbedding.InProceedings
of the 2021 Sixth International Conference on Image Information Processing (ICIIP), Shimla, India, 26–28 November 2021;
pp.25–29.[CrossRef]
37. Han,W.;Wang,Q.Movierecommendationalgorithmbasedonknowledgegraph.InProceedingsofthe20192ndInternational
ConferenceonSafetyProduceInformatization(IICSPI),Chongqing,China,28–30November2019;pp.409–412.[CrossRef]
38. Sarkar,R.;Goswami,K.;Arcan,M.;McCrae,J.P.Suggestmeamoviefortonight:LeveragingKnowledgeGraphsforConversa-
tionalRecommendation.InProceedingsofthe28thInternationalConferenceonComputationalLinguistics,Barcelona,Spain,
8–13December2020;pp.4179–4189.
39. Lee,C.;Han,D.;Han,K.;Yi,M.ImprovingGraph-BasedMovieRecommenderSystemUsingCinematicExperience.Appl.Sci.
2022,12,1493.[CrossRef]
40. Shi,C.;Zhang,Z.;Luo,P.;Yu,P.S.;Yue,Y.;Wu,B.Semanticpathbasedpersonalizedrecommendationonweightedheterogeneous
informationnetworks.InProceedingsofthe24thACMInternationalonConferenceonInformationandKnowledgeManagement,
Melbourne,Australia,18–23October2015;pp.453–462.
41. Hu,B.;Shi,C.;Zhao,W.X.;Yu,P.S.Leveragingmetapathbasedcontextfortop-nrecommendationwithaneuralco-attention
model.InProceedingsofthe24thACMSIGKDDInternationalConferenceonKnowledgeDiscovery&DataMining,London,
UK,19–23August2018;pp.1531–1540.
42. Sun,Z.;Yang,J.;Zhang,J.;Bozzon,A.;Huang,L.-K.;Xu,C.Recurrentknowledgegraphembeddingforeffectiverecommendation.
InProceedingsofthe12thACMConferenceonRecommenderSystems,Vancouver,BC,Canada,2October2018;pp.297–305.
43. Huang,X.;Fang,Q.;Qian,S.;Sang,J.;Li,Y.;Xu,C.Explainableinteraction-drivenusermodelingoverknowledgegraphfor
sequentialrecommendation. InProceedingsofthe27thACMInternationalConferenceonMultimedia,Nice,France,21–25
October2019;pp.548–556.
44. Hua,S.;Chen,W.;Li,Z.;Zhao,P.;Zhao,L.Path-BasedAcademicPaperRecommendation.InWebInformationSystemsEngineering—
WISE2020.WISE2020;Huang,Z.,Beek,W.,Wang,H.,Zhou,R.,Zhang,Y.,Eds.;LectureNotesinComputerScience;Springer:
Cham,Switzerland,2020;Volume12343.[CrossRef]
45. Krathwohl,D.R.ArevisionofBloom’staxonomy:Anoverview.TheoryPract.2002,41,212–218.[CrossRef]
46. Alepis,E.;Troussas,C.M-learningprogrammingplatform:Evaluationinelementaryschools.Informatica2017,41,471–478.
47. Krouska,A.;Troussas,C.;Sgouropoulou,C.ACognitiveDiagnosticModuleBasedontheRepairTheoryforaPersonalizedUser
ExperienceinE-LearningSoftware.Computers2021,10,140.[CrossRef]
Disclaimer/Publisher’s Note: The statements, opinions and data contained in all publications are solely those of the individual
author(s)andcontributor(s)andnotofMDPIand/ortheeditor(s).MDPIand/ortheeditor(s)disclaimresponsibilityforanyinjuryto
peopleorpropertyresultingfromanyideas,methods,instructionsorproductsreferredtointhecontent.