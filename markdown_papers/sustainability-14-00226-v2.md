---
title: "sustainability-14-00226-v2"
source: "sustainability-14-00226-v2.pdf"
source_sha256: "17518636477bc51a7fe41e030b084c105e230a78c28cea91fb2766d3d148ffd5"
converted_at: "2026-10-26T07:05:16.602102+00:00"
markitdown_version: "0.1.9"
---
sustainability
Article
Topic Extraction and Interactive Knowledge Graphs for
Learning Resources
AhmedBadawy1,2,* ,JesusA.Fisteus1 ,TarekM.Mahmoud2,3 andTarekAbdEl-Hafeez2,4
1 TelematicEngineeringDepartment,UniversityCarlosIIIdeMadrid,28911Legane,Spain;
jesus.arias@uc3m.es
2 ComputerScienceDepartment,FacultyofScience,MiniaUniversity,EL-Minia61519,Egypt;
d.tarek@mu.edu.eg(T.M.M.);tarek@mu.edu.eg(T.A.E.-H.)
3 FacultyofComputersandArtificialIntelligence,SadatCityUniversity,SadatCity32897,Egypt
4 ComputerScienceUnit,DerayaUniversity,EL-Minia61765,Egypt
* Correspondence:ahmed.badawy2000@mu.edu.eg
Abstract:Humanitydevelopmentthrougheducationisanimportantmethodofsustainabledevel-
opment.Thisguaranteescommunitydevelopmentatpresenttimewithoutanynegativeeffectsin
thefutureandalsoprovidesprosperityforfuturegenerations.E-learningisanaturaldevelopment
oftheeducationaltoolsinthiseraandcurrentcircumstances.Thankstotherapiddevelopmentof
computersciencesandtelecommunicationtechnologies,thishasevolvedimpressively.Inspiteof
facilitatingtheeducationalprocess,thisdevelopmenthasalsoprovidedamassiveamountoflearn-
ingresources,whichmakesthetaskofsearchingandextractingusefullearningresourcesdifficult.
Therefore,newtoolsneedtobeadvancedtofacilitatethisdevelopment. Inthispaperwepresent
(cid:1)(cid:2)(cid:3)(cid:1)(cid:4)(cid:5)(cid:6)(cid:7)(cid:8)(cid:1) anewalgorithmthathastheabilitytoextractthemaintopicsfromtextuallearningresources,link
(cid:1)(cid:2)(cid:3)(cid:4)(cid:5)(cid:6)(cid:7)
relatedresourcesandgenerateinteractivedynamicknowledgegraphs. Thisalgorithmaccurately
Citation:Badawy,A.;Fisteus,J.A.; andefficientlyaccomplishesthosetasksnomatterhowbigorsmallthetextsare.WeusedWikipedia
Mahmoud,T.M.;AbdEl-Hafeez,T. Miner,TextRank,andGensimwithinouralgorithm.Ouralgorithm’saccuracywasevaluatedagainst
TopicExtractionandInteractive Gensim,largelyimprovingitsaccuracy. Thiscouldbeasteptowardsstrengtheningself-learning
KnowledgeGraphsforLearning andsupportingthesustainabledevelopmentofcommunities,andmorebroadlyofhumanity,across
Resources.Sustainability2022,14,226.
differentgenerations.
https://doi.org/10.3390/su14010226
AcademicEditors:Maria Keywords: education; e-learning; topic identification; natural language processing; interactive
SoledadRamirez, knowledgegraph
EbbaOssiannilsson,Arturo
MolinaGutierreaand
Jane-FrancesAgbu
1. Introduction
Received:30October2021
Accepted:23December2021 Thesustainabledevelopmentofthecommunityisagreatresponsibilityandalofty
Published:26December2021 goal that could be achieved in many ways; education is a very important one of them.
Educationqualityisthemainindicatorofacommunity’sdevelopment[1],however,the
Publisher’sNote:MDPIstaysneutral
cost of a high quality education is unaffordable in many countries [2], especially with
withregardtojurisdictionalclaimsin
the effect that COVID-19 has had on many systems [3]. In this context, e-learning was
publishedmapsandinstitutionalaffil-
aninevitablesolution: itcanbeusedbyeducationalsystemsasanaffordable,safe,and
iations.
progressingalternativetoclassicaleducation. Althoughe-learningisnotnew,thecurrent
circumstancesrequiremorecapabilitiesandefficiencyfrome-learningsystems. Oneofthe
manyadvantagesofe-learningsystemsfortheirusersisthatitcanbeavailableanytime
Copyright: © 2021 by the authors. and anywhere, with the lowest costs. Learning resourcesare available in awide range
Licensee MDPI, Basel, Switzerland. offormatsthatcoveralmostanythingthatonecouldneedtolearn[4]. E-learningisalso
This article is an open access article a great facilitator of self-learning, as it helps learners to autonomously get appropriate
distributed under the terms and materialsfortheskillstheywanttodevelop,withouttheneedtotakefullcoursesatformal
conditionsoftheCreativeCommons educationinstitutionssuchasschoolsandcolleges.Self-learninghasthepotentialtochange
Attribution(CCBY)license(https:// thewaypeoplearegoingtobeeducated. Aseverystudentisunique,theeducationsystem
creativecommons.org/licenses/by/ hastheopportunitytoadoptnewtoolsthathelpittoadaptuniquely,accordingtoevery
4.0/).
Sustainability2022,14,226.https://doi.org/10.3390/su14010226 https://www.mdpi.com/journal/sustainability

Sustainability2022,14,226 2of21
individualstudent’sneeds. Asreportedin[5],91%ofelementaryschoolstudentsand71%
ofmiddleandhighschoolstudentsusee-learningforlearningthingsontheirown.
Sofar,wecannotethatstudentsinthecurrenteraareluckytohaveallthesepossi-
bilities,toolsandeducationalresourcesattheirfingertips. Moreover,severalstudieshave
shownthatthenumberofavailablelearningresourcesisgrowingeveryday[6,7].
However,thegrowingnumberoflearningresourcesisadouble-edgedsword,asit
willprovideagreatopportunityforstudentstolearnanythingtheywishindifferentstyles
andwaysofexploration,however,italsorepresentsachallengeforstudentstofindand
selecttherequiredoneamongthisgrowingoceanofresources.
Therefore,learnerswouldbenefitfromhavingnewtoolsandtechniquesforexploring,
browsingandsearchinglearningresources. Thosetoolswouldnotonlysavelearnerstime
andeffort,butalsoprotectthemfromboredom.
ThemassiveprogressoftechnologiessuchasArtificialIntelligence,MachineLearn-
ing[8],NaturalLanguageProcessing[9],SemanticWeb[10]andVirtualReality[11]could
facilitatebuildingsuchtools.
Weplantoapplyresultsintheseareastobuildane-learningsystem,inspiredbythe
LearningasaNetworklearningtheory[12],whichaimstofacilitatethelearningprocess
forstudentsindifferentways: (1)atopicextractionsystem,toautomaticallyobtainthe
maintopicsfromlearningresourcesandbuildamultilayertopicstructure;(2)aclustering
system, to connect learning resources based on the relationships between their topics;
(3) dynamic interactive knowledge graphs, to show learning resources in an easy and
searchabledynamicconnectedgraph;and(4)asociallearningnetwork,toconnectdifferent
users with common interests or common learning goals, and to facilitate self-learning.
In particular,inthispaperwefocusonitsfirstthreefeatures: topicextraction,clustering
anddynamicinteractiveknowledgegraphs,leavingthesociallearningnetworkforfuture
work. Ourmaincontributionisatopicextractionalgorithmthatisabletoanalyzethetext
oflearningresources,includinglargebooks,andidentifytheirmaintopicsasunambiguous
references to categories in the Wikipedia collaborative encyclopedia. Based on these
extractedtopics,thesystemisabletoconnectandgrouprelatedlearningresources. These
connectionscanbepresentedtolearnersintheformofknowledgegraphsthattheycan
browsegraphicallyandinteractivelyinordertosearchandexploreresourcestheymight
beinterestedin.
The rest of this article is organized as follows. Section 2 reviews related research.
Section3describestheresearchmethodologywefollowedandourproposal,includinga
thoroughdescriptionofourtopicextractionalgorithmandsomeexamplesoftheknowledge
graphsproducedbythesystem. Section4describestheexperimentsweperformedonthe
topicextractionalgorithmandtheirresults,whicharediscussedandcomparedtoresearch
workinSection5. Finally,Section6concludesthearticleanddescribesourfuturelines
ofwork.
2. LiteratureReview
AutomaticTopicIdentificationinthecurrentinformationeraisvitalforfindingthe
requiredlearningmaterialamongthedailygiantgrowthofdataontheWeb. Toestablish
unequivocaltopicidentifiersweneedacomprehensiveandup-to-datevocabulary,knowl-
edgesource,orontologythatcouldbeusedforrepresentinganypossibletopicalearning
resourcemightbeabout. TheonlineencyclopediaWikipediaisthemostfeasiblechoice
forthistask. Assuch,itrepresentsagiantmultilingualdatabaseofconceptsandsemantic
relations. AspecifictopicofanarticlecanbeidentifiedwiththeidentifieroftheWikipedia
articlethatdescribesthattopic. WikipediaMiner[13]isanopen-sourcesoftwaresystem
thatusesthearticlesinWikipediatoextractandidentifythemaintopicsintextthrough
itsrichsemantics,soweuseitinoursystem. Itappliesparallelizeddumpprocessingand
machine-learnedsemanticrelatednessmeasures. Furthermore,itcontainsatopicdetector
featurethatgathersalllabelsinthedocument. Formostdocuments,Wikipediaprobably
knowssomethingaboutthetopicsdiscussedandcouldlikelyaddadditionalinformation.

Sustainability2022,14,226 3of21
OnceWikipediaMinerdetectsthetopicswithinadocument,itiseasierforautomaticsys-
temstoprocessthoselearningresourcesfortaskssuchasclassification,recommendation,
ordataretrieval.
WikipediaandWikipediaMinerhavebeenusedinmanyfieldssuchasautomatictopic
indexing[14],documentclustering[15],documentsummarization[16],theclassification
ofmultilingualbiomedicaldocuments[17],convertingconcept-basedrepresentationsof
documentsfromonelanguagetoanother[18],identifyingtheprerequisiterelationships
amonglearningobjects[19],classifyingnewsarticles[20],evaluatingandclassifyingOpen
EducationalResources(OERs)andOpenCourseware(OCW)basedonqualitycriteria[21],
andforgrouprecommendationbycombiningtopicidentificationandsocialnetworks[22].
Aswecansee,Wikipediaanditssemanticinformationcanbeusedforawidevariety
ofapplicationsandfieldsduetoitsreliability,efficiency,andthecontinuousupdatingof
contentbyalargecommunityofusers.
The process applied by Wikipedia Miner begins by gathering overlapping word
n-grams(wherenrangesbetweenoneandthemaximumlabellengthinWikipedia)from
theprocesseddocumentandconsultingthelabelvocabularytoascertainwhichtermsand
phrases correspond to concepts in Wikipedia. A limitation of this technique is that the
biggerthetextsizeinthedocument,thehardertheprocesswillbe.
WealsousedTextRank[23],whichisagraph-basedrankingmodelfortextprocess-
ing. TextRank is an unsupervised algorithm for the automated summarization of text.
Thealgorithmcanobtainthemostimportantkeywordsinadocumentwithouttheneed
foratrainingcorpusorlabeling. ThisalgorithmwaslaterimproveduponbyFederico
et al. in [24], by introducing something called a “BM25 ranking function”, which is a
rankingfunctionwidelyusedinthestateoftheartinformationretrievaltasks. BM25is
avariationoftheTF-IDFmodelusingaprobabilisticmodel. Theyachievedanimprove-
ment of 2.92% above the original TextRank result by using BM25. The combination of
TextRankwithmoderninformationretrievalrankingfunctionssuchasBM25andBM25+
createsarobustmethodforautomaticsummarizationthatperformsbetterthanprevious
standardtechniques[24].
Next,wearegoingtodiscusstopicidentificationtechniquesandsomeoftheirappli-
cations. Topicidentificationisacrucialfieldinnaturallanguageprocessing. Thistechnique
has many applications such as information retrieval, document summarization, topic
detectionandtracking,textclassification,etc.
In[25]Chrisetal. presentedTopCat(TopicCategories),atechniqueforidentifying
topics that recur in articles in a text corpus. Chris et al. identified related items based
ontraditionaldataminingtechniques. Frequentitemsetsaregeneratedfromthegroups
ofitems,followedbyclustersformedwithahypergraphpartitioningscheme. Natural
languagetechnologywasusedtoextractnamedentitiesfromadocument,andthenlook
forfrequentitemsets. Next,groupsofnamedentitieswereclustered,capturingclosely
relatedentitiesthatmaynotactuallyoccurinthesamedocument. Finally,arefinedsetof
clusterswasproduced,witheachclusterrepresentingasetofnamedentitiesthatreferto
atopic.
In[26]Veselinetal. presentedanalgorithmforopiniontopicidentificationthrough
developingamethodologyforthemanualannotationofopiniontopicswiththeuseoffine-
grainedsubjectivityanalysis,whichcouldbeusefulforquestionanswering,summarization,
andinformationextraction.
In [27] Kino et al. presented a method for automatic topic identification using an
encyclopedicgraphderivedfromWikipedia. Kinoetal. usedtheunsupervisedsystem
Wikify[28]toidentifytheimportantencyclopedicconceptsinaninputtextautomatically.
AsKinoetal. mentioned“topicidentificationgoesbeyondkeywordextraction,instead
hastobeobtainedfromsomerepositoriesofexternalknowledge”. Kinoetal. aimedto
findtopics(orcategories)thatarerelevanttothedocumentathand,whichcanbeusedto
enrichthecontentofthedocumentwithrelevantexternalknowledge.

Sustainability2022,14,226 4of21
In[29]Freidrichetal. presentedaframeworkfortheidentificationofprimaryresearch
topicsfromwithinacorpusofrelatedpublications. Theirmethodusesanunsupervised
topic modeling approach to classify new and emerging topics from the entire corpus.
Machinelearningtechniqueswereused,suchasNon-negativeMatrixFactorizationfor
NaturalLanguageProcessing,aswellasanadaptivetopicmodelBayesianclassifierthat
allowsfortheidentificationofnewprimarytopicsaspapersareadded.
In[30]Khaderetal. designedanensemblemethodforautomatictopicextractionfrom
acollectionofscientificpublicationsbasedonamulti-verseoptimizeralgorithmasthe
clusteringalgorithm.
Documentsthatrefertoaspecifictopicmightalsorefertoseveralsub-topicsofit.Then
thesingle-layermethodcouldpresentproblemstodefinetheintendedtopics,evenwhena
documentisanalyzedmanuallybyhumanexperts. Anewmultilayertopicstructurewas
proposedin[31]. Themultilayertopicstructureaimstoautomaticallybuildamultilayer
topic structure. This technique is intended to identify sub-topics where units within
thesamesub-topicshouldbeverysimilarandunitsfromdifferentsub-topicsshouldbe
dissimilar. Thementionedpaperusedthehierarchicalagglomerativeclusteringalgorithm
to establish the hierarchical topic tree. It started by using each unit as an independent
cluster. Then,thesimilaronesmergedtogether. Thisprocesswasrepeateduntilallclusters
mergedintoonecluster,andfromthishierarchyatreestructurewasestablished.
Oursystemalsohastheabilitytocreatethistreestructureoftopics. Wewillelaborate
onthestepsforthisextractioninouralgorithminSection3.
Bookswithcommontopicsaresemanticallysimilar,andcouldbelinkedtogetherto
provide a network of resources that are related to a general topic. We can provide this
informationinaDynamicInteractiveKnowledgeGraph,whichcanbeupdatedcontinu-
ouslywitheverynewbookaddedtothedatabase,andcanbebrowsedbyeveryuser. This
graph-basedlearningtechniqueisanemergingsearchfieldandprovedtobeeffectiveand
usefulforthelearningprocessforstudentsandteachers: asWeberetal. mentionedin[32]
thegraph-basedlearningtechniqueimprovessearchabilityfornewsourcesandprovides
explainableresultsandresultrecommendations.
In [33] Zhijun et al. used an interactive group knowledge graph to visualize the
relationship between knowledge points concluding that interactive group knowledge
graphshaveasignificantpromotionaleffectonteachers’onlinelearning,thatitisbeneficial
to teachers’ professional development, and that it is an effective method of enhancing
thedepthandbreadthoftheinteractionofstudents’learning. Inaddition,Zhijunetal.
defendthattheprocessofgeneratingcollectiveknowledgegraphscanenhancestudents’
enthusiasmforautonomouslearningandpromotemeaningfulandin-depthinteractions
betweendifferentstudents.
Inordertoputourresearchintocontextwemustalsoundergoaquickoverviewon
learningtheories. In[34]Phillipsetal. mentionedPlato’stheory,whichpostulatesthat
individual’sknowledgeispresentatbirth,whichiscalledtheTheoryofRecollectionor
Platonic epistemology. In [35] Brain et al. mentioned Locke’s theory, which postulates
that humans are born into the world with no innate knowledge and are ready to be
writtenonandinfluencedbytheenvironment. Therearemanyotherlearningtheories
suchasBehaviorism[34],Sociallearningtheory[36],CognitivismorGestalttheory[37],
Constructivism[38]orTransformativelearningtheory[39].
OurproposalisbasedontheLearningasaNetworklearningtheory[12]. Thisstarts
withthelearnerandviewslearningasthecontinuouscreationofapersonalknowledge
network. TheLearningasaNetworkbuildsuponconnectivism[40,41]. Connectivismisa
recenttheoryofnetworkedlearning[42],whichfocusesonlearningasmakingconnections.
The Learning as a Network theory is considered the most appropriate for the current
conditions and for the tools that we will study and use in this research, such as the
interactiveknowledgegraphthatwewillproduceandillustrateinSection3.

Sustainability2022,14,226 5of21
3. MaterialsandMethods
AswasexplainedinSection1, themaincontributionofourworkisthealgorithm
wedesignedtoextractmaintopicsfromtextuallearningresources. Wewilldescribethe
algorithminthissection,aswellashowitsresultscanbeappliedtoclusteringlearning
resourcesandcreatinginteractiveanddynamicknowledgegraphs.
Weappliedaquantitativeresearchmethodologytoevaluateourproposal. Theexper-
imentsweperformedonthealgorithmaredescribedinSection4. Theirobjectiveswere
tooptimizeaconfigurationparameterofthealgorithm(theparentcategorylevel,which
willbeexplainedlaterinthissection),toevaluatetheprecisionofthemaintopicsextracted
bythealgorithmandmeasurethetimeittakestoproducethosetopics,incomparisonto
anotherstateoftheartalgorithm. Theexperimentswerebasedonadatasetofmorethan
500fulltextlearningbookswecollectedfromseveralrepositories. Wedescribethisdataset
inSection4.
OursystemusesSemanticinformation[43]tostoretheinformationabouteverystu-
dentandeverylearningresource,asitismachine-understandable,productiveininference
andrecommendation,andeffectiveinsociallearningnetworks. Forstudents,werecord
theirage,learninggoals,currentandrequiredskills,andtheirlearningbackground. For
learningresources,werecordtitle,author,abstract,level,type,andsize. Inthispaperwe
will focus on analyzing textbooks to identify main topics and classify them to produce
dynamicinteractivegraphsoflearningresources.
Thelearningresourcesanalysisphasestartsbyextractingtextfrombooks,thenpro-
cessingtextandextractingmainkeywordsusingnaturallanguageprocessingtechniques.
As we mentioned before, we are going to use TextRank [23] combined with the BM25
ranking function [24] to improve the results. By using Gensim (we used Gensim 4.1.2
https://pypi.org/project/gensim/(accessedon29October2021)),whichisaverypopular
open-sourcelibraryforunsupervisedlearningimplementedinPython[44],wecanapply
thatalgorithmonthetextofthebooksinordertoextractmainkeywords.
To identify the Main Topics in each learning resource we have to understand the
difference between Keywords and Main Topics. Keywords are important words in a
textthatcouldrepresentatopicmentionedinthebook. Theyareanexactmatchtotext
thatappearsinthebook. MainTopicsarethemostimportanttopicsfoundinthebook
accordingtothecategoryretrievedfromtheWikipediadatabase,whichhaveaspecific
idandaURL(https://en.wikipedia.org/wiki/Wikipedia:FAQ/Categories(accessedon
29October2021)). Theyarenotnecessarilyanexactmatchtowordsmentionedinthebook,
sincetheycouldalsoappearwithsemanticallyrelatedwords.
An example of a keyword is the word “business” appearing in the text of a book.
A Main Topic, related to that keyword, could be the Wikipedia category titled “Busi-
ness”,withidentifier771152andURLhttps://en.wikipedia.org/wiki/Category:Business
(accessedon29October2021).
Therefore, Main Topics consist of a category in Wikipedia, which could provide
moreinformationandlinktorelatedresourcesthatarenotnecessarilymentionedinthe
originaltext.
AllthestepsofouralgorithmareexplainedinthenextAlgorithm1pseudocodeand
Figure1.

Sustainability 2022, 14, 226 Sustainability2022,14,226 7 of 261o f21
Figure1.Ouralgorithmstructure.
Figure 1. Our algorithm structure.
The Main Topics extraction phase uses Wikipedia Miner [13] where Wikipedia’s
articles,categoriesandredirectsarerepresentedasclasses,andcanbeefficientlysearched,
Now we will show some examples of our algorithm’s results in Table 1.
browsed,anditeratedover. Thisisaplatformforsharingdataminingtechniquesbasedon
Wikipediadata. ThisdataisgatheredfromWikipedia’sXMLdumps. Weusedadumpof
Table 1. Examples of our algorithm’s results.
theEnglishversionofWikipediadatedon22July2011,whichincludes3.3millionarticles
and37.4GBofuncompressedmarkup. WikipediaMineristhefundamentaltoolinour
Book main topic (Biology)
TopicIdentificationsystemthatenablesustoassigntherightmaintopictothelearning
resources. Thereisalsoapa1resntt lceavteeglo: ryfeaturethatenablesustofindtheparentcategory
(Immune soyfsttheemsp/Oecrifigeadnc astyesgtoermy/st/oMpicic.robiology/Biology/Clinical pathology)
InourinitialtestsweranGensimwiththeWikifyservice[28]ofWikipediaMiner,
2nd level:
whichisusedforkeywordextractionandwordsensedisambiguation,howeverwefound
ma(nByiomloisgsiyn/gLriefseu/Nltsa,teuvreanla sfcteirenrecpeesa/tBinogtathneye/xApneraitmoemntys)s. everaltimes. Tosolvethis
problemweaugmentedthe3crodm bleinvaetlio: nofGensimandWikipediaMiner(Wikify)withthe
SearchserviceofWikipediaMiner,whichsolvedtheproblembysearchingallavailable
(Biology/Life/Society/Natural sciences/scientific disciplines).
articles for those that are related to the identified keywords. The actual data of this
4th level:
experimentwillbepresentedintheexplanationofexperiment2inSection4.
(LFiofer/eBaciohlloegaryn/iNngarteusroeu/rNcea,atufterrale xstcriaecnticnegst/hUenmiavienrkseey)w. ordswithGensim,weuse
WikipediaMinertoextractmaintopics,thenforeachtopicweidentifytheparentcategories
Book main topic (Math)
atdifferentlevels. Weiterateovertheretrievedcategoriestoextractmulti-levelresults.
1st level:
This step produces a hierarchy of topics that represents a multilayer topic structure as
(Mathematicaml eanntiaolnyesdisin/C[3a1l]c.uWluhse/nSwuebmdievnitsioionnins tohfi smpaaptheretmheasteiccosn/Adnleavleylsoifst/hIenpteagrernatlc ategory
wemeantheseconditeratiocnalocfuthluesp)a rentcategoryservice,andsoon.
2nd level:
(Subdivisions of mathematics/Mathematics/Abstraction/Dimension/Geometry)
3rd level:
(Mathematics/Subdivisions of mathematics/Abstraction/Structure/Dimension)
4th level:
(Structure/Scientific disciplines/Academic disciplines/Abstraction/Dimension)
As we can see from the examples, the higher the level the more general and com-
prehensive the results are, yet at some level those results are too broad and not so useful.
We describe in the Results section how we empirically chose the best level of parent
category to use in our system.
For each learning resource we select the top five main topics retrieved by the algo-
rithm. After assigning those main topics to the learning resource we will establish the
base for the dynamic interactive knowledge graph that will contain all the learning re-
sources. We insert each learning resource and main topics as nodes, then we create a link
between each main topic and all related learning resources. The result is a connected
graph of related learning objects as shown in Figures 2–5.
Students can use this graph in different useful ways. They can find the required
main topic and browse all related learning objects, find a learning object then identify all

Sustainability2022,14,226 7of21
Algorithm1Pseudocode
HereweexplainourAlgorithmforTopicIdentification:
1. Foreach(LearningResource)inthedataset:
2. Extract(Text)
3. Process(Text)withGensimtoextract(Keywords)
4. “Process(Keywords)withWikipediaMinerservices(Wikify,Search)toextract(ArticleIDs)”
5. Copy(Keywords)to(Wikify_Keywords)
6. Copy(Keywords)to(Search_Keywords)
7. While(numberofretrievedArticleIDs<20)
8. Process(Wikify_Keywords)with(Wikify)toextracttopicIDs
9. Removethelastkeywordfrom(Wikify_Keywords)list“toenableWikifytofindmore
results”
10. Iflengthof(Wikify_Keywords)=0:
11. ForeachKeywordin(Search_Keywords):
12. ProcessKeywordwith(Search)toextracttopicIDs
13. “Process(ArticleIDs)withWikipediaMinerservices(exploreArticle,suggest,
exploreCategory,
14. parentCategory)toextract(Definition,Title)”
15. Appendall(ArticleIDs)inoneArticleIDslist
16. ForeachIDinArticleIDs:
17. ProcessIDwith(exploreArticle)toextractDefinitionandTitle
18. ProcessIDwith(suggest)toextractsuggestedCategoriesIDs
19. ForeachsuggestedCategoryID:
20. ProcessIDwith(exploreCategory)toextractDefinitionandTitle
21. GetParentCategorywith(parentCategory)property
22. “[(parentCategory)couldberepeatedtoreachtherequiredlevel
23. for(2nd–3rd–4th)levelofparentcategories”
24. CollectallParentCategorieswithrepetitionnumbers.
25. SortParentCategoriesfromhightolowrepetitiontoextractthemostimportantones.
Nowwewillshowsomeexamplesofouralgorithm’sresultsinTable1.
Table1.Examplesofouralgorithm’sresults.
Bookmaintopic(Biology)
1stlevel:
(Immunesystem/Organsystems/Microbiology/Biology/Clinicalpathology)
2ndlevel:
(Biology/Life/Naturalsciences/Botany/Anatomy).
3rdlevel:
(Biology/Life/Society/Naturalsciences/scientificdisciplines).
4thlevel:
(Life/Biology/Nature/Naturalsciences/Universe).
Bookmaintopic(Math)
1stlevel:
(Mathematicalanalysis/Calculus/Subdivisionsofmathematics/Analysis/Integralcalculus)
2ndlevel:
(Subdivisionsofmathematics/Mathematics/Abstraction/Dimension/Geometry)
3rdlevel:
(Mathematics/Subdivisionsofmathematics/Abstraction/Structure/Dimension)
4thlevel:
(Structure/Scientificdisciplines/Academicdisciplines/Abstraction/Dimension)
Aswecanseefromtheexamples,thehigherthelevelthemoregeneralandcompre-
hensivetheresultsare,yetatsomelevelthoseresultsaretoobroadandnotsouseful. We
describeintheResultssectionhowweempiricallychosethebestlevelofparentcategory
touseinoursystem.

Sustainability 2022, 14, 226 8 of 21
Sustainability 2022, 14, 226 related main topics, or find related learning objects and explore common main topics8 of 21
between them.
SustainabiliBtyu20i2l2d,1i4n,2g26 knowledge graphs from the text in learning resources is another key f8eoaf2-1
ture inr eolautre dp lamtfaoirnm t,o wpihcse,r eo rw fei ncda nr efolactuesd olnea srenlifn-dgi roebcjteecdt sl eaanrdn inexgp tloo reen acbolme mstound emntasi nto t opics
identifbye ttwhee erenq tuhiermed. topic or learning resource easily and in a joyful way. In Figure 2 we
Foreachlearningresourceweselectthetopfivemaintopicsretrievedbythealgorithm.
can see theB ruelialdtiionng bkentowweelend lgeea rgnrianpgh rse sforoumrc etsh e(i nte bxltu ien) ,l eaanrdn imngai nre tsoopuirccse (si nis y aenllootwh)e.r key fea-
Afterassigningthosemaintopicstothelearningresourcewewillestablishthebaseforthe
ture in our platdfyonrammi,c wintherearceti vweken ocwanle dfgoecgurasp ohnth astewlfi-lldciornetacitneadll ltheealrenarinnigng troe seounracebsl.eW setiunsdeertnts to
eachlearningresourceandmaintopicsasnodes,thenwecreatealinkbetweeneachmain
identify the required topic or learning resource easily and in a joyful way. In Figure 2 we
topicandallrelatedlearningresources. Theresultisaconnectedgraphofrelatedlearning
can see the relation between learning resources (in blue), and main topics (in yellow).
objectsasshowninFigures2–5.
Figure 2. Relation between learning resource (blue), and main topics (yellow).
In Figure 3 we can see the relation between learning resources (in blue), a nd main
topics (in yellow). Figure2.Relationbetweenlearningresource(blue),andmaintopics(yellow).
Figure 2. Relation between learning resource (blue), and main topics (yellow).
In Figure 3 we can see the relation between learning resources (in blue), and main
topics (in yellow).
Figure 3. Relation betwFeiegnur lee3a.rRneilantgio nrebsetowuerecnelesa (rbnilnuger)e,s oaunrdce sm(baluine) ,taonpdicmsa i(nyteolpliocws(y).e llow).
In Figure 4 we can see the relation between one learning resource (in blue), main
topics (in red), and chapters (in yellow). To obtain this graph we apply our algorithm
Figure 3. Relation between learning resources (blue), and main topics (yellow).
separately on each learning resource and each chapter on it.
In Figure 4 we can see the relation between one learning resource (in blue), main
topics (in red), and chapters (in yellow). To obtain this graph we apply our algorithm
separately on each learning resource and each chapter on it.

Sustainability 2022, 14, 226 9 of 21
Sustainability2022,14,226 9of21
Sustainability 2022, 14, 226 9 of 21
Figure 4. Relation between one learning resource (blue), main topics (red), and chapters (yellow).
Figure 4In. R Feilgautioren 5b ewtwee ceann o sneee l etahren irnegla rteisoonu rbceet w(belueen) , lmeaarinn itnogp ircess (oreudr)c, easn d(i nch balputee)r,s m(yaelilno wto)p. ics
Figure4.Relationbetweenonelearningresource(blue),maintopics(red),andchapters(yellow).
(in yellow), and chapters (in red).
In Figure 5 we can see the relation between learning resources (in blue), main topics
(in yellow), and chapters (in red).
Figure 5. Relation between learning resources (blue), main topics (yellow), and chapters (red).
Figure5.Relationbetweenlearningresources(blue),maintopics(yellow),andchap ters(red).
Figure 5. Relation between learning resources (blue), main topics (yellow), and chapters (red).

Sustainability2022,14,226 10of21
Students can use this graph in different useful ways. They can find the required
main topic and browse all related learning objects, find a learning object then identify
allrelatedmaintopics,orfindrelatedlearningobjectsandexplorecommonmaintopics
betweenthem.
Buildingknowledgegraphsfromthetextinlearningresourcesisanotherkeyfeature
inourplatform,wherewecanfocusonself-directedlearningtoenablestudentstoidentify
therequiredtopicorlearningresourceeasilyandinajoyfulway. InFigure2wecansee
therelationbetweenlearningresources(inblue),andmaintopics(inyellow).
InFigure3wecanseetherelationbetweenlearningresources(inblue), andmain
topics(inyellow).
InFigure4wecanseetherelationbetweenonelearningresource(inblue),maintopics
(inred),andchapters(inyellow). Toobtainthisgraphweapplyouralgorithmseparately
oneachlearningresourceandeachchapteronit.
InFigure5wecanseetherelationbetweenlearningresources(inblue),maintopics
(inyellow),andchapters(inred).
AswasexplainedinSection1,weplantocompleteinthefutureoure-learningsystem
with a social learning network. This system would be responsible for storing students’
informationincludingtheirlearninggoals,currentandrequiredskills,andtheirlearning
background. Thesystemwillassigntoeachstudent’slearningpatheverylearningresource
theyfinish. Withthisinformationandthetopicsouralgorithmextracts,thesystemwillbe
abletorecommendlearningresourcesorcompletelearningpathsforotherstudentswith
thesamegoalsorlearningbackground.
Afterwehaveexplainedourmethodologyandthestructureofoursystem,weare
goingtoillustrateourexperimentstoevaluateourtopicidentificationalgorithm.
4. Results
Weconductedtwoexperimentstoevaluateouralgorithm. Inthefirstexperimentwe
ranouralgorithmonadatasetof579bookswithdifferentconfigurationsofparentcategory
level,inordertoanalyzeitsaccuracyandselecttheoptimalvalueforthatparameter. Inthe
secondexperimentwecomparedtheaccuracyofouralgorithm’sresultsagainstanother
topicextractiontechnique,andwealsocomparedcomputationtimeforbothofthem.
Theseexperimentswererunonacollectionof579booksindifferentsubjects,levels,
and from different learning repositories. We selected them for the levels of secondary
schoolandfirstyearsofuniversity/college.Thetopicsofthebooksincluded:Anatomy,Art,
Astronomy,Automotive,Biology,Biostatistics,Business,Chemistry,ComputationalPhysics,
Computing,Economics,Education,Engineering,FirstAid,Hardware,History,Humanities,
Languages, Law, Math, Medicine, Organic Chemistry, Parenting, Physics, Physics and
Environment,Psychology,Science,Socialsciences,Software,Statistics,andTravel.
4.1. Experiment1
Weextractedtheresultsfromthesysteminfourdifferentlevels(1st,2nd,3rd,and4th)
dependingonthenumberofparentcategoriesusedinWikipediaMiner. Weusedtop-5
accuracy[45]toevaluatetheresultsineachleveltoidentifythemostsuitableleveltouse.
Foreachlearningresourceweretrievedthetopfivemaintopics,andthenweevaluated
eachtopicmanuallyandgaveeachlearningresourceascoreoutoffive. Iftheresourcegot
fiveoffivethenallthefivetopicswerecorrect,howeveriftheresourcegottwooffive,then
onlytwoofthetopicswerecorrect.
Nextwesummedalltheresultsanddividedthetotalbythenumberofresourcesto
findtheaveragescore(averagetruevalue).
Figure6shows,foreachparentcategorylevel,thenumberofresourcesforwhichthe
algorithmgotthefivetopicscorrect,fourtopicscorrect,etc.

Sustainability 2022, 14, 226 Sustainability2022,14,226 11 of 2111 of21
Comparison between the 4 levels of
Parent-Category
350
300
250
200
150
100
50
0
Num. of Num. of 1's Num. of 2's Num. of 3's Num. of 4's Num. of 5's
Zeros
4th level 3rd level 2nd level 1st level
Figure 6. Comparison between the four levels of parent-category.
Figure6.Comparisonbetweenthefourlevelsofparent-category.
Table 2 lists, for eaTcahbl ep2alriestns,t fcoarteeagchorpyar elenvtecal,t etghoery pleevrecle,nthteagpeer coefn tdaogecuofmdeoncutsm feonrts wfohriwchhi chat
at least one of thel efaisvteo nteoopfitchse fiwveasto pciocrsrweacst c(o“rrTercut(e“ Ttroueptiocp iicdiednentitfifiieedd””)),,t htehpee rpceenrtcaegnetoafgdeo cuomf ents
for which none of the five topics was correct (“False topic identified”) and the average
documents for which none of the five topics was correct (“False topic identified”) and the
numberofcorrectlyidentifiedtopics(“Averagetrue”).
average number of correctly identified topics (“Average true”).
Table2.Comparisonbetweenthefourlevels.
Table 2. Comparison between the four levels.
TrueTopicIdentified FalseTopicIdentified AverageTrue
4thTlreuveel Topic Identified False Topic Identified Average True
0.884 0.116 0.527
Parent-Category
4th level Parent-Category 0.884 0.116 0.527
3rdlevel
3rd level Parent-Category 0.946 0.946 0.054 0.054 0.640 0.640
Parent-Category
2nd level Parent-Category 0.959 0.041 0.714
2ndlevel
0.959 0.041 0.714
1st level Parent-CategPoarryen t-Category 0.867 0.133 0.752
1stlevel
0.867 0.133 0.752
Parent-Category
We can find that the results of using both the first and second level parent categories
show a high number of resources with a five of five in top-5 accuracy, especially for the
Wecanfindthattheresultsofusingboththefirstandsecondlevelparentcategories
first level. In addition, the average number of correctly identified topics is higher (0.752)
showahighnumberofresourceswithafiveoffiveintop-5accuracy,especiallyforthe
for the first level thfianrs tfolerv ethl.eI nseacdodnitido nle,tvheel.a vTehreagreefnourme,b wereo cfhcoorsreec tthlyei dfiernstti fileedvetol poifc sthiseh pigahreern(t0 .752)
category in our algoforritthhemfi rfsotrl etvheel trheasnt foofr tthhee seexcopnedrilmeveeln.tTsh, earletfhoroeu,wghe cwhoes erethtaeifinr stthlee vaebliolfittyhe tpoa rent
use many levels to cparteogdourycein hoiuerraalrgcohriitchaml sftorruthcteurerset ooff tmheaeixnp teoripmiecnst. s,althoughweretaintheabilityto
usemanylevelstoproducehierarchicalstructureofmaintopics.
4.2. Experiment 2 4.2. Experiment2
The goal of this exTpheergimoaelnotf twhiasse xtpoe criommenptawrea stthoec ocmompapreutthaeticoonm tpiumtaet iaonndti mtheea nadccthueraacccyu racy
ofouralgorithmagainstothertopicidentificationtechniques. AsGensimandWikipedia
of our algorithm against other topic identification techniques. As Gensim and Wikipedia
Miner have the ability to identify topics from text, we compared them against our al-
Miner have the ability to identify topics from text, we compared them against our algo-
gorithm,whichisbuiltontopofGensimandWikipediaMineraswasexplainedinthe
rithm, which is built on top of Gensim and Wikipedia Miner as was explained in the
Methodologysection.
Methodology section.
In this experiment we sampled 350 books from the dataset that we used in the first
experiment. The books in this sample of the dataset contain between 95 and 1800 pages.
In Figure 7 we can see the distribution of the number of pages of the books in the dataset.

Sustainability2022,14,226 12of21
Inthisexperimentwesampled350booksfromthedatasetthatweusedinthefirst
Sustainability 2022, 14, 226 experiment. Thebooksinthissampleofthedatasetcontainbetween95and1800p1a2 goef s2.1
Sustainability 2022, 14, 226 InFigure7wecanseethedistributionofthenumberofpagesofthebooksintheda1t2a soeft .21
Number of Pages vs. Number of Books
Number of Pages vs. Number of Books
160
160
140
140
s 120
k
so 120
k o o b 100
o
b f
f
o
o r e
10
8
8
0
0
0
r e b m 60
b 60
mu
N 40
u
N 40
20
20
0
0
Number of pages
Number of pages
Figure 7. Number of pages vs. number of books.
Figure7.Numberofpagesvs.numberofbooks.
Figure 7. Number of pages vs. number of books.
HHowoweveevre,rw, ewhea vheavseee nsetehna tthcoamt cpoumtaptiuotnattiiomne tciomrree lcaotrerseblaettetesr bweittthert ewxtitshi zteex(itn stiezrem (sin
However, we have seen that computation time correlates better with text size (in
oftenrumms boef rnoufmcbhearr aocft ecrhsa)rathctaenrsw) tithhanth weinthu mthbee nruomfbpearg eosf poafgaebs ooof ka. bTohoakt. hTahpatp ehnasp,pfeonrs,
terms of number of characters) than with the number of pages of a book. That happens,
exfaomr epxlaem,apslwe, eaasr wepe raorcee spsrioncgetsesxint,ga tnedxts, oamnde bsooomkes bcoonoktasi ncoanbtaiginn au mbibge nruomfpbaegr eosffi pllaegdes
for example, as we are processing text, and some books contain a big number of pages
wfiitlhlecdh awrtisth,fi cghuarretss,, afnigdupreicst,u arneds, wpihcticuhreasr,e wnohticphr oacrees sneodt bpyrothceesaslegdo rbityh tmhse. aTlhgeorhiitshtmogsr.a Tmhe
filled with charts, figures, and pictures, which are not processed by the algorithms. The
ofhtihsteongurammb eorf othfec hnaurmacbteerrs opf ecrhbaroaockteirsss pheorw bnooink Fisig suhroew8n. in Figure 8.
histogram of the number of characters per book is shown in Figure 8.
Text Size vs. Number of Books
Text Size vs. Number of Books
180
180
160
s k 1 1 4 6 0 0
s k o o o b 1 1 2 4 0 0
o b f o 1 1 0 2 0 0
f o r e 10 80 0
r e b b m 6 8 0 0
mu u N 4 6 0 0
N 40
20 187 118 27 9 7 1 1
20 0 187 118 27 9 7 1 1
0
Number of characters (milions)
Number of characters (milions)
Figure 8. Text size vs. number of books.
Figure 8. Text size vs. number of books.
Figure8.Textsizevs.numberofbooks.
When we started our comparison we found that the maximum number of pages that
When we started our comparison we found that the maximum number of pages that
we Wcahne pnrwoceesstsa wrteitdh oWurikciopmedpiaar Misoinnewr eisf boeutnwdetehna t25th aenmd a3x5i mpaugmesn. uWmitbhe rmoofrpea pgaegsetsh athte
we can process with Wikipedia Miner is between 25 and 35 pages. With more pages the
wWecikainppedroiac eMssinweirt hseWrviekri pfreedqiuaeMntilnye srtoispbpeetdw reeesnpo2n5dainndg.3 O5np athgee so.tWheirt hhamnodr,e Gpeangseimst hhead
Wikipedia Miner server frequently stopped responding. On the other hand, Gensim had
no problem with the number of pages, so we continued our experiment comparing Gen-
no problem with the number of pages, so we continued our experiment comparing Gen-
sim alone against our algorithm.
sim alone against our algorithm.
A first version of our algorithm was only based on Gensim and the “Wikify” Wik-
A first version of our algorithm was only based on Gensim and the “Wikify” Wik-
ipedia Miner service. However, as we mentioned in the Methodology section, it did not
ipedia Miner service. However, as we mentioned in the Methodology section, it did not

Sustainability2022,14,226 13of21
WikipediaMinerserverfrequentlystoppedresponding. Ontheotherhand,Gensimhad
noproblemwiththenumberofpages,sowecontinuedourexperimentcomparingGensim
aloneagainstouralgorithm.
Sustainability 2022, 14, 226 13 of 21
AfirstversionofouralgorithmwasonlybasedonGensimandthe“Wikify”Wikipedia
Sustainability 2022, 14, 226 Minerservice. However,aswementionedintheMethodologysection,itdidno1t3p orfo 2d1u ce
anytopicsuggestionforabigportionofthebooksinthedataset,morethan200booksout
ofpr3o5d0u.cAes aanyre tsouplitco sfutghgaets,ttihoen fifonra al vbeigrs pioonrtioofno oufr tahleg booriotkhsm inu tshees ,diantaasdedt,i tmioonr,et thhea“nS 2e0a0r ch”
Wb pio rko oipd kes u dc o eiua a t Mn o y fi n3 toe5 pr0 i .s c Ae srs uv g aic g ree e sfsot u iro lt nt ho fef o t rch aa as t be, si t g hi ne p owfi r n thi a oilcn hv o etf rh s tei h o e“n Wb o oifko o kifu syr i” n as l t gehro evr iid tch aet m ads ou eet s ,se m sn, oo in rte pa trd hod adn iut i 2co 0en 0 ,a ny
the “Search” Wikipedia Miner service for the cases in which the “Wikify” service does
rebsouolkt.s Touhte ofif n3a5l0.v Aerss aio rnesoufltt hoef tahlagto, rthiteh mfinaplr voedrusicoend osfu ogugre asltgioonristhfmor uaslelsb, uint 1ad1dbiotiookns, in
not produce any result. The final version of the algorithm produced suggestions for all
ththeed “aStaesaertc.h” Wikipedia Miner service for the cases in which the “Wikify” service does
but 11 books in the dataset.
not Fpirrosdt,uwcee acnoym rpeasrueldt. cTohme pfiuntaalt ivoenrstiiomne offo trhbeo atlhgoGreitnhsmim parondduocuedr asluggogrietshtimon,sta fkoirn agllt ext
First, we compared computation time for both Gensim and our algorithm, taking
sibzueti 1n1t oboaockcos uinn tth,ien dFaitgasuerte. s9and10. Twoplotsarepresented: onethatpresentsadata
text size into account, in Figures 9 and 10. Two plots are presented: one that presents a
pointFfoirrste, awche dcoomcupmareendt caonmdpauntaottihoner tiomnee ftohra tbogtrho uGpesnsbiomo kasndb yourar naglgeosraitnhdm,s htaokwinsgt he
data point for each document and another one that groups books by ranges and shows
avteexrta gsiezec oinmtop uatcactoiuonntt, iimn eFifgourrtehse 9b aonodk s1a0t. eTawcoh pralontgs ea.re presented: one that presents a
the average computation time for the books at each range.
data point for each document and another one that groups books by ranges and shows
the average computation time for the books at each range.
120
Computation time vs. text size
120
)s 100 Computation time vs. text size
d
n
o c )s d 100
en 80
s (
e m
o
c e s 80
it
n
(
e
m
60
o it
a
it
n 4
6
0
0
t u p m o C o it a t u p 2 4 0 0
m
o 20
C 0
0.00 2.00 4.00 6.00
0
0.00 2N.0u0mber of characters (4m.0i0llions) 6.00
our algorithm Gensim
Number of characters (millions)
our algorithm Gensim
Figure 9. Computation time vs. text size.
Figure9.Computationtimevs.textsize.
Figure 9. Computation time vs. text size.
Average Computation time vs. Text Size
)s
d Average Computation time vs. Text Size
n
o)s
cd
en120
s (
e m
o
c e s 110200
it
n
( e
m
18000
o it
a
it
n
6800
t u p m o it a t 2 4 4 6 0 0 0 0
o C
e
u p m 200
go
aC 0
r e e
v A g a Number of characters (milions)
r
e
v A Number of characters (milions)
Gensim our algorithm
Gensim our algorithm
Figure 10. Average computation time vs. text size.
Figure 10. Average computation time vs. text size.
FigureF1i0g.uArevse r1a1g eacnodm 1p2u tsahtoiown ttihmee svasm.tee xdtastiaz ei.n the form of box plots, where minimum,
maximum and median values for each range, as well as their 25 and 75 percentiles, can be
Figures 11 and 12 show the same data in the form of box plots, where minimum,
identified.
maximum and median values for each range, as well as their 25 and 75 percentiles, can be
identified.

Sustainability2022,14,226 14of21
Figures 11 and 12 show the same data in the form of box plots, where minimum,
Sustainability 2022, 14, 226 maximumandmedianvaluesforeachrange,aswellastheir25and75percenti1le4 so,fc a21n
Sustainability 2022, 14, 226 beidentified. 14 of 21
Gensim (Computation time vs. Text Size)
Gensim (Computation time vs. Text Size)
120
)
s d 120
n)100
os
d
c en 100
so 80
(c
ee
m it
n o
it
s ( e
m
it
n 4
6
6
8
0
0
0
0
ao
t u
p
it
a 2
4
0
0
mt
u
op 20
Cm 0
o C 0 (0..1) Mil (1..2) Mil (2..3) Mil (3..4) Mil (4..5) Mil (5..6) Mil (6..7) Mil
(0..1) Mil (1..2) Mil N(u2.m.3) bMeilr of ch(3a..r4a) Mctilers (m(4i.l.i5o) nMsil) (5..6) Mil (6..7) Mil
Number of characters (milions)
Figure 11. Gensim (computation time vs. text size).
Figure11.Gensim(computationtimevs.textsize).
Figure 11. Gensim (computation time vs. text size).
Our algorithm (Computation time vs. Text Size)
Our algorithm (Computation time vs. Text Size)
120
) 120
s
d 100
n)
o c e s d n 100
so 80
(c
ee
ms 80
(
it
n
e
m
60
oit 60
it a n o 40
t u p it a 40
mt u 20
op
Cm 20
o 0
C
0 (0..1) Mil (1..2) Mil (2..3) Mil (3..4) Mil (4..5) Mil (5..6) Mil (6..7) Mil
(0..1) Mil (1..2) Mil N(u2.m.3)b Meilr of ch(3a..r4a) Mctilers (m(4i.l.i5o) Mnsil) (5..6) Mil (6..7) Mil
Number of characters (milions)
Figure 12. Our algorithm (computation time vs. text size).
Figure 12. Our algorithm (computation time vs. text size).
Figure12.Ouralgorithm(computationtimevs.textsize).
Table 3 presents the total computation time for the 350 books in the dataset and the
averaTgaeb cloe m3 ppuretasteinotns ttihme et optearl bcoomokp. utation time for the 350 books in the dataset and the
Table3presentsthetotalcomputationtimeforthe350booksinthedatasetandthe
average computation time per book.
averagecomputationtimeperbook.
Table 3. Total computation time.
Table 3. Total computation time.
Table3.Totalcom putationtime. Total Time (s) Average Time (s)
Gens im Total5 7T2i1m e (s) Avera1g6e. 3T5i me (s)
TotalTime(s) AverageTime(s)
OurG aelgnosirmith m 65773291 1196..2355
Gensim 5721 16.35
Our algorithm 6739 19.25
WeO ucarna lgseoeri tihnm the plots that our algo6r7i3t9hm takes slightly more tim19e. 2t5han Gensim,
whichW we acsa enx speeec tiend tahse opulro tasl gtohraitt homur r ualngso Griethnmsim ta iknetse rsnliagllhyt.l yT hme oorvee trihmeae dt hisa nd uGee tnos tihme,
WecanseeintheplotsthatouralgorithmtakesslightlymoretimethanGensim,which
uwshe icohf Wwaiks iepxepdeiact eMdi naes ro suerr valigceosr iothnm th reu nress Guletns spimro vinidteerdn ablyly G. Tehnesi omv,e irnhcelaudd iins gd ucoem tom thue-
wasexpectedasouralgorithmrunsGensiminternally. Theoverheadisduetotheuseof
nuiscea toiof nW tiikmipe ecdaiuas eMdi nbeyr tsheer vruicnensi nong othf ea rdeisfufelrtse nptr soevrivdeerd. Ibny s pGieten soifm th, einsecl euxdtirnag t acsokms,m thue-
anviceartaigoen otivmereh ceaauds eodf obuyr tahleg orurinthnmin gis o 1f7 a.7 d%if, fleorwenetr stehravne r3. sIn p sepr ibteo ookf .t hese extra tasks, the
averaAgfete orv hearvhienagd aonf aoluyzr eadlg coormithpmut iast i1o7n.7 t%im, elosw anerd t thhaeni r3 r se lpaetiro bno took t. ext size, we will an-
alyzeA thftee ra chcauvriancgy aonf athlyez reeds uclotms ppruotvaitdioend tbimy Gese annsidm t haenidr oreulra tailogno rtiot htemx.t Fsiirzset,, wwee pwriells eannt-
alyze the accuracy of the results provided by Gensim and our algorithm. First, we present

Sustainability2022,14,226 15of21
WikipediaMinerservicesontheresultsprovidedbyGensim,includingcommunication
timecausedbytherunningofadifferentserver. Inspiteoftheseextratasks,theaverage
overheadofouralgorithmis17.7%,lowerthan3sperbook.
After having analyzed computation times and their relation to text size, we will
analyze the accuracy of the results provided by Gensim and our algorithm. First, we
presentanexampleoftheresultsthatwegotforthreebookswesampledfromthedataset
inTable4.
Table4.Exampleofresults.
|     | Title:PrinciplesofAccounting, | Title:CollegePhysicsforAP® |     |
| --- | ----------------------------- | -------------------------- | --- |
Title:Anatomy&Physiology
Volume1:FinancialAccounting
| BookInformation | Pages:1055 | CoursesPages:1694 | Pages:1420       |
| --------------- | ---------- | ----------------- | ---------------- |
|                 |            | Category:Physics  | Category:Anatomy |
Category:Business
Wikipediaminer Failstoprovideananswer. Failstoprovideananswer. Failstoprovideananswer.
Companies/company/
accounting/accountants/ Credit/credited/credits/ Figure/figures/figurative/
Gensim account/accounts/ figures/figure/figured/ cell/cells/called/calling/
accountant/accountable/ figuring/energy/energies/force muscle/muscles/blood
accountancy/accounted
|     | Accountancy/Investment/ | Physics/ | Anatomy/Biology/ |
| --- | ----------------------- | -------- | ---------------- |
|     | Financialmarkets/       |          | Tissues/Organs/  |
Fundamentalphysics/
|     | Accountingsystems/ |     | Musculoskeletalsystem/ |
| --- | ------------------ | --- | ---------------------- |
concepts/
|              | Management/               | Subjectstaughtinmedicalschool/ |                       |
| ------------ | ------------------------- | ------------------------------ | --------------------- |
| OurAlgorithm |                           | Conceptsbyfield/               |                       |
|              | Appliedsciences/Business/ |                                | Cardiovascularsystem/ |
Introductoryphysics/
|     | Businesseconomics/ |     | Circulatorysystem/ |
| --- | ------------------ | --- | ------------------ |
Physicseducation/Motion/
|     | Accountability/ |     | Medicalspecialties/ |
| --- | --------------- | --- | ------------------- |
SpaceTime/Force/Phenomena
|     | Legalentities |     | Greekloanwords |
| --- | ------------- | --- | -------------- |
Wecanseefromtheresultsthatouralgorithmprovidesthemostrelevantandaccu-
rateresults. Inaddition,whereasGensimproducesjustwords,ouralgorithmproduces
unambiguousWikipediacategories,referencedbytheiruniqueidentifieratWikipedia. The
identifiersarenotshowninthetableforreadability.
Inordertoevaluateaccuracy,inthisexperimentwemadeGensimandouralgorithm
produce10topicsforeachbook.
For each book we evaluated these 10 results and computed accuracy (number of
correcttopicsdividedby10). Topiccorrectnesswasdecidedbyahumanevaluator. Wecan
seeinTable5thatoursystemachievesamuchbetteraccuracythanusingGensimalone.
Table5.Top-10accuracy.
|     |                 | OurAlgorithm | Gensim      |
| --- | --------------- | ------------ | ----------- |
|     | Averageaccuracy | 0.712285714  | 0.240857143 |
Then we evaluated these topics by using top-k accuracy [45]. We compared top-1,
top-5,andtop-10accuracyinFigure13andinTable6. Foreachbookweevaluatedthe
resultsaccordingtothethreelevels. Ifthefirsttopicreturnedbythealgorithmsisthemain
categoryofthebookorcloseenoughtoit,thenthebookcountsfortop-1accuracy. Ifone
ofthefirst5topicsisthemaincategoryorcloseenough,thenthebookcountsfortop-5
accuracy. Likewise,ifoneofthefirst10topicsisthemaincategoryorcloseenough,the
bookcountsfortop-10accuracy. Again,ahumanevaluatordecidedthatbookbybook.

Sustainability 2022, 14, 226S ustainability2022,14,226 16 of 21 16of21
Top-K accuracy
100
Sustainability 2022, 14, 226 16 of 21
80
y
c
a
r 60
u
c Top-K accuracy
c
A
K 40
- 100
p
o
T
20
80
y
c
a r 6 0 0
u
c Top-1 Top-5 Top-10
c
A
K 40
- our algorithm Gensim
p
o
T
20
Figure 13. Top-K accuracy.
Figure13.Top-Kaccuracy.
0
Now we want to analyze the relation between accuracy and text size. We start by
TableT6o.pTo-1p-kaccuracy. Top-5 Top-10
plotting all accuracy values for all books against text size in Figure 14.
TOP-1 TOP-5 TOP-10
our algorithm Gensim
Gensim 22.9% 45.5% 67.5%
Accuracy vs. Text Size (all)
Figure 13. Top-K accuraOcyu.r algorithm 48.0% 74.0% 86.0%
1
Now we want to analyze the relation between accuracy and text size. We start by
Now we want to analyze the relation between accuracy and text size. We start by
0.8 plottingallaccuracyvaluesforallbooksagainsttextsizeinFigure14.
plotting all accuracy values for all books against text size in Figure 14.
y 0.6
c
a
r Accuracy vs. Text Size (all)
u
c
c 0.4
A
1
0.2
0.8
0
y 0.6
c a 0 1 2 3 4 5 6
r
u
c Number of characters (milions)
c 0.4
A
our algorithm Gensim
0.2
Figure 14. Accuracy vs. text size (all).
0
0 1 2 3 4 5 6
Next we present top 1, top 5, and top 10 values for Gensim and our algorithms, in
groups of different text sizes in NFiugmubree r1 o5f. characters (milions)
our algorithm Gensim
Figure 14. Accuracy vs. text size (all).
Figure14.Accuracyvs.textsize(all).
Next we present top 1, top 5, and top 10 values for Gensim and our algorithms, in
groups of different text sizes in Figure 15.

Sustainability2022,14,226 17of21
Sustainability 2022, 14, 226 17 of 21
Sustainability 2022, 14, 226
Nextwepresenttop1,top5,andtop10valuesforGensimandour
17
a l
o
g
f
o r
2
i
1
t hms,in
groupsofdifferenttextsizesinFigure15.
Average Accuracy vs. Text Size (detailed)
Average Accuracy vs. Text Size (detailed)
1
1
0.8
y 0.8
cy
ac
ra
ur 0.6
cu 0.6
cc
ac
e
g
a
e 0.4
ag 0.4
ra
er
ve
Av
A 0.2
0.2
0
0
(0..1) Mil (1..2) Mil (2..3) Mil (3..4) Mil (4..5) Mil (5..6) Mil (6..7) Mil
(0..1) Mil (1..2) Mil (2..3) Mil (3..4) Mil (4..5) Mil (5..6) Mil (6..7) Mil
Number of characters (milions)
Number of characters (milions)
Gensim-TOP-1 our algorithm-TOP-1 Gensim-TOP-5 our algorithm-TOP-5 Gensim-TOP-10 our algorithm-TOP-10
Gensim-TOP-1 our algorithm-TOP-1 Gensim-TOP-5 our algorithm-TOP-5 Gensim-TOP-10 our algorithm-TOP-10
Figure 15. Average accuracy vs. text size (detailed).
Figure 15. Average accuracy vs. text size (detailed).
Figure15.Averageaccuracyvs.textsize(detailed).
We can see in this graph that there are 0-sized bars with text sizes between 5 and 7
We can see in thisW gercaapnhse tehinatt htihsegrreap ahrteh a0t-tshiezreeda rbea0r-ssi zweditbha rtsewxtit hsitzeextss bizeetswbeetewne e5n a5nandd 77 million
million characters. The reason is the small number of books these groups contain, as we
million characters.c hTahreac rteerass.oTnh eisre tahsoen simstahlel snmuamllbneurm obfe rboofobkoso kthsethsees egrgorouuppss ccoonnttaainin,,a saws ewcea nseein
can see in Figure 8F. igure8.
can see in Figure 8.
Finally, the averagFein valalylu,tehse oafv ethraeg eacvcaulureascyof itsh ceaalcccuulraatceydi sacnadlc ucloamtedpaarneddc otom gpraoreudptso ogfr oupsof
Finally, the average values of the accuracy is calculated and compared to groups of
textsizesinFigure16.
text sizes in Figure 16.
text sizes in Figure 16.
Average accuracy vs. Text Size
Average accuracy vs. Text Size
1
1
y 0.8
cy 0.8
ac
ra
ur
cu 0.6
cc 0.6
ac
e
g a
a
e g 0 0 . . 4 4
ra
er
ve 0.2
Av 0.2
A
0
0
Number of characters (milions)
Number of characters (milions)
Gensim our algorithm
Gensim our algorithm
Figure 16. Average accuracy vs. text size.
Figure 16. Average aFcicguurreac1y6. vAsv. etreaxgte saiczceu. racyvs.textsize.
5. Discussion
5. Discussion
We developed an algorithm to process learning topics in order to extract main top-
We developed an algorithm to process learning topics in order to extract main top-
ics. In our algorithm we start by extracting text, then we use Gensim to extract the main
ics. In our algorithm we start by extracting text, then we use Gensim to extract the main
keywords from the text, and finally we use Wikipedia Miner with both the Wikify and
keywords from the text, and finally we use Wikipedia Miner with both the Wikify and
Search services to extract main topics. We can use different levels of the parent category,
Search services to extract main topics. We can use different levels of the parent category,
so we tried many levels in experiment 1 to find out the best one to use in our algorithm.
so we tried many levels in experiment 1 to find out the best one to use in our algorithm.
From the main topics extracted by our algorithm we produced interactive
From the main topics extracted by our algorithm we produced interactive
knowledge graphs to facilitate finding the required main topic, browsing all related
knowledge graphs to facilitate finding the required main topic, browsing all related
learning objects, finding a specific learning object, identifying all related main topics,
learning objects, finding a specific learning object, identifying all related main topics,

Sustainability2022,14,226 18of21
5. Discussion
Wedevelopedanalgorithmtoprocesslearningtopicsinordertoextractmaintopics.
In our algorithm we start by extracting text, then we use Gensim to extract the main
keywords from the text, and finally we use Wikipedia Miner with both the Wikify and
Searchservicestoextractmaintopics. Wecanusedifferentlevelsoftheparentcategory,so
wetriedmanylevelsinexperiment1tofindoutthebestonetouseinouralgorithm.
Fromthemaintopicsextractedbyouralgorithmweproducedinteractiveknowledge
graphstofacilitatefindingtherequiredmaintopic,browsingallrelatedlearningobjects,
findingaspecificlearningobject,identifyingallrelatedmaintopics,findingrelatedlearning
objects,andexploringcommonmaintopicsbetweenlearningobjects.
Inexperiment1weproducedresultswithouralgorithmfordifferentlevelsofparent
category. Wefoundthatthefirstlevelisthebestchoicetouseinouralgorithm,however
wecanusedifferentlevelsifahierarchicaltopicstructureisneeded.
Inexperiment2weprovedthattheWikifyserviceofWikipediaMinerdoesnotwork
properlyforthebooksinourdataset,asitdoesnotproduceresultsformorethan57%of
thebooks. Withouralgorithmthishappensforjust3%ofthem.
WealsoanalyzedthecomputationtimeforbothouralgorithmandGensim. Asex-
pected, ouralgorithmtakesslightlymoretimethanGensim, duetoitusingWikipedia
MinerservicesontheresultsprovidedbyGensim. Whatisimportanttomentionisthatthe
experimentshowstherelationshipbetweenthecomputationtimeofouralgorithmand
textsizeislinear.
Finally,weshowedthatouralgorithmlargelyoutperformsGensimintermsofthe
accuracyofthetopicsitextracts,withtheadditionaladvantageofproducingtheminan
unambiguouswayasreferencestoWikipediacategories. Accordingtoourexperiments,
textsizedoesnotaffecttheaccuracyofthetopicsouralgorithmextracts.
5.1. ComparisontoPreviousStudies
Severalattemptshavebeenmadeinthepasttoaccomplishsomeofourgoalsaswe
mentionedinSection2.
In[13]DavidandIanpresentedWikipediaMineralthoughtheyevaluateditfornews
articles. In [14] Olena et al. used Wikipedia and Wikipedia Miner for automatic topic
indexing,howevertheydidnotmentionthedocumentsizes. In[27]Kinoetal. presented
a method for automatic topic identification using an encyclopedic graph derived from
Wikipedia. TheyusedtheunsupervisedWikifyservice. However,aswereportinSection4,
theWikifyserviceisnotabletoproduceresultsforlargerresourcessuchasmanyofthe
booksinourdataset.
In [25] Chris et al. presented TopCat, which was effective in identifying topics in
collectionsofnewsarticles. In[26]VeselinandClairepresentedanalgorithmforopinion
topicidentification. In[29]Freidrichetal. presentedaframeworkfortheidentificationof
primaryresearchtopics. In[30]Khaderetal. designedanensemblemethodforautomatic
topicextractionfromacollectionofscientificpublications. However,allthisresearchfo-
cusesonnewsarticles,opiniontopicidentification,researchtopicsorscientificpublications,
whicharesmallerthanthelearningresourcesinourdataset.
Wecanconcludethatthemainadvantageofourproposalincomparisontoprevious
workisitsabilitytoworkonlargeresourcessuchasbig-sizedlearningbooksthatnormally
containhundredsofpagesandevenreachtwothousandpagesinsomecases.
5.2. ResearchRestrictionsandPracticalImplications
Sofar,wehaveappliedouralgorithmontextualeducationalresourcesonly. Recent
advancesinspeech-to-texttechniquessuggestthatitcouldalsoprobablyworkforextracting
themaintopicsofotherkindsoflearningresourcessuchasvideosandaudio. However,
furtherresearchisneededinordertoprovethat.
Applyingouralgorithmrequiresthecomputationalpowerofahigh-endcomputeror
acomputercluster,especiallyforrunningtheWikipediaMinerservices,whichworkona

Sustainability2022,14,226 19of21
massivedatabaseofinformationextractedfromWikipedia. Sincethistaskisintendedto
berunatthecoreofthee-learningsystem,thislimitationwouldnotaffectlearners,which
wouldbeabletousethesystemfromthedeviceoftheirchoice.
6. Conclusions
Attheendofourexperiments,andafterallthefactsthatwehaveseenandillustrated,
wecanconcludethatWikipediaMinerisaveryusefultoolthatcanbeusedinvariousfields,
however,itpresentsanimportantlimitationwithrespecttothesizeofthetextitcanprocess
asoneunit. Gensimisalsoaneffectivetoolalthoughouralgorithm,whichworksontopof
WikipediaMinerandGensim,outperformsbothofthemandfixestheirdisadvantages.
Ouralgorithmtakesaverysmallamountofextracomputingtimeyetproducesresults
withahighervalueofaccuracy. Usingouralgorithmcanalsoproducedynamicinteractive
knowledgegraphsthatcouldbeaugmentedinanye-learningplatformorusedonitsown
fordifferentgoals. Thisgiveslearnerstheabilitytoexploreahugenumberoflearning
resourcesinashorttimeandinaninteractiveandexcitingway. Thisisapromisingwayof
exploringlearningresourceswiththecurrentgrowingdatarateontheInternet.
Inthefuturewecanintegrateothertoolstoanalyzelearningresourcesindifferent
formatslikevideo,audio,andgraphics. Thiscouldproduceastrongsystemfore-learning
thatwillbeatthehugeamountoflearningresourcescurrentlyavailableandhelplearners
findtheresourcestheyneed. Wewillalsocompletethesystemwithsociallearningnetwork
features,tohelplearnerssocializeduringthelearningprocess.
SupplementaryMaterials: Thefollowingsupportinginformationcanbedownloadedat: Thelist
ofdatasetbookisavailableonlineat:https://docs.google.com/spreadsheets/d/1hjEcUft-QnYvv5
SVZSAt-EjJbfDGDUzK/edit?usp=sharing&ouid=111160959031654571802&rtpof=true&sd=true
(accessedon29October2021),allfiguresandtablesinthearticleareavailableonlineat:https://drive.
google.com/file/d/1uIaZkV202K4aRmS8GnLkPKVOZjmnV2m1/view?usp=sharing(accessedon
29October2021).
AuthorContributions:A.B.:Conceptualization,methodology,software,validation,formalanalysis,
investigation,resources,datacuration,writing—originaldraftpreparation,writing—reviewand
editing, visualization, funding acquisition. J.A.F.: Conceptualization, methodology, validation,
formalanalysis,investigationresources,datacuration,writing—originaldraftpreparation,writing—
reviewandediting,visualization,supervision,projectadministration,fundingacquisition.T.M.M.:
Conceptualization,writing—reviewandediting.T.A.E.-H.:Conceptualization,writing—reviewand
editing.Allauthorshavereadandagreedtothepublishedversionofthemanuscript.
Funding:TheresearcherwaspartiallyfundedbytheEgyptianMinistryofHigherEducationand
MiniaUniversityintheArabRepublicofEgypt. [Jointsupervisionmissionfromthefourthyear
missions(2015–2016)oftheseventhfive-yearplan(2012–2017)].
InstitutionalReviewBoardStatement:Notapplicable.
InformedConsentStatement:Notapplicable.
DataAvailabilityStatement:(ThirdPartyData)Copyrightholdersofthebooksinthedatasetare
thirdpartiesandwecannotsharebookcontents.”Disclaimer”:wearesharingonlythetitlesofall
thebooksasSupplementaryMaterial.
ConflictsofInterest:Theauthorsdeclarenoconflictofinterest.
References
1. Psacharopoulos,G.;Woodhall,M.EducationforDevelopment;OxfordUniversityPress:Oxford,UK,1993.
2. Kremer, M.; Brannen, C.; Glennerster, R. The challenge of education and learning in the developing world. Science 2013,
340,297–300.[CrossRef][PubMed]
3. Tarkar,P.ImpactofCOVID-19pandemiconeducationsystem.Int.J.Adv.Sci.Technol.2020,29,3812–3814.
4. Soni,V.D.GlobalImpactofE-learningduringCOVID19.SSRN2020,3630073.[CrossRef]
5. Duffin,E.Statista.Com.Availableonline:https://www.statista.com/statistics/1076776/us-k-12-students-reasons-using-digital-
learning-tools-level/(accessedon15September2021).

Sustainability2022,14,226 20of21
6. Yoon,L.Statista.Com.Availableonline:https://www.statista.com/statistics/710512/south-korea-number-of-e-books-academic-
libraries/(accessedon28March2021).
7. Watson,A.Statista.Com.Availableonline:https://www.statista.com/statistics/652610/number-of-new-primary-school-books-
released-in-norway/(accessedon12August2021).
8. Agrawal,A.;Gans,J.;Goldfarb,A.Whattoexpectfromartificialintelligence.MITSloanManag.Rev.2017,589,1486511104226.
9. Liddy,E.D.NaturalLanguageProcessing.InEncyclopediaofLibraryandInformationScience,2nded.;MarcelDekker,Inc.:New
York,NY,USA,2001.
10. Berners-Lee,T.;Hendler,J.;Lassila,O.Thesemanticweb.Sci.Am.2001,284,34–43.[CrossRef]
11. Zheng,J.M.;Chan,K.W.;Gibson,I.Virtualreality.IeeePotentials1998,17,20–23.[CrossRef]
12. Chatti,M.A.PersonalizationinTechnologyEnhancedLearning: ASocialSoftwarePerspective;RWTHAachen,AachenUniversity:
Aachen,Germany,2010.
13. Milne,D.;Witten,I.H.Anopen-sourcetoolkitforminingWikipedia.Artif.Intell.2013,194,222–239.[CrossRef]
14. Medelyan,O.;Witten,I.H.;Milne,D.TopicindexingwithWikipedia.InProceedingsoftheAAAIWikiAIWorkshop;AAAIWikiAI
Workshop:Chicago,IL,USA,2008;Volume1,pp.19–24.
15. AHuang,A.;Milne,D.;Frank,E.;Witten,I.H.ClusteringDocumentsUsingaWikipedia-BasedConceptRepresentation,Pacific-Asia
ConferenceonKnowledgeDiscoveryandDataMining;Springer:Berlin/Heidelberg,Germany,2009.
16. Nastase,V.;Filippova,K.;Milne,D.N.Nastase,SummarizingwithEncyclopedicKnowledge;NationalInstituteofStandardsand
Technology(NIST):Gaithersburg,MD,USA,2009.
17. Garcia,M.A.M.;Rodriguez,R.P.;Rifon,L.A.LeveragingWikipediaknowledgetoclassifymultilingualbiomedicaldocuments.
Artif.Intell.Med.2018,88,37–57.[CrossRef][PubMed]
18. García,M.A.M.;Rodríguez,R.P.;Rifón,L.A.Wikipedia-basedcross-languagetextclassification.Inf.Sci.2017,406–407,12–28.
[CrossRef]
19. DeMedio,C.;Gasparetti,F.;Limongelli,C.;Sciarrone,F.;Temperini,M.Automaticextractionofprerequisitesamonglearning
objectsusingwikipedia-basedcontentanalysis.InProceedingsoftheInternationalConferenceonIntelligentTutoringSystems,
Zagreb,Croatia,6–10June2016;pp.375–381.
20. Garcia,M.A.M.;Rodriguez,R.P.;Ferro,M.V.;Rifon,L.A.Wikipedia-BasedHybridDocumentRepresentationforTextualNews
Classification. InProceedingsofthe20163rdInternationalConferenceonSoftComputing&MachineIntelligence(ISCMI),
Dubai,UnitedArabEmirates,23–25November2016;pp.148–153.
21. Moise,G.;Vladoiu,M.;Constantinescu,Z.MASECO:AMulti-AgentSystemforEvaluationandClassificationofOERsandOCW
BasedonQualityCriteria,E-LearningParadigmsandApplications;Springer:Berlin/Heidelberg,Germany,2014;pp.185–227.
22. Wang,J.;Liu,Z.;Zhao,H.Grouprecommendationusingtopicidentificationinsocialnetworks. InProceedingsoftheSixth
International Conference on Intelligent Human-Machine Systems and Cybernetics, Hangzhou, China, 26–27 August 2014;
Volume1,pp.355–358.
23. Mihalcea, R.; Tarau, P.Textrank: Bringingorderintotext. InProceedingsofthe2004ConferenceonEmpiricalMethodsin
NaturalLanguageProcessing,Barcelona,Spain,January2004;AssociationforComputationalLinguistics:Barcelona,Spain,2004;
pp.404–411.
24. Barrios,F.;López,F.;Argerich,L.;Wachenchauzer,R.Variationsofthesimilarityfunctionoftextrankforautomatedsummariza-
tion.arXiv2016,arXiv:1602.03606.
25. Clifton,C.;Cooley,R.;Rennie,J.Topcat:Dataminingfortopicidentificationinatextcorpus.IEEETrans.Knowl.DataEng.2004,
16,949–964.[CrossRef]
26. Stoyanov,V.;Cardie,C.Topicidentificationforfine-grainedopinionanalysis.InProceedingsofthe22ndInternationalConference
onComputationalLinguistics(Coling2008),Manchester,UK,18–22August2008;pp.817–824.
27. Coursey, K.; Mihalcea, R.; Moen, W. Using encyclopedic knowledge for automatic topic identification. In Proceedings of
theThirteenthConferenceonComputationalNaturalLanguageLearning(CoNLL-2009),Boulder,CO,USA,4–5June2016;
AssociationforComputationalLinguistics:Boulder,CO,USA,2009;pp.210–218.
28. Mihalcea, R.; Csomai, A. Wikify! Linking documents to encyclopedic knowledge. In Proceedings of the Sixteenth ACM
ConferenceonConferenceonInformationandKnowledgeManagement,Lisbon,Portugal,6–10November2007;pp.233–242.
29. Crane,A.;Freidrich,B.;Fehlman,W.;Frolow,I.;Engels,D.W.ANovelMethodologytoIdentifythePrimaryTopicsContained
WithintheCOVID-19ResearchCorpus.SMUDataSci.Rev.2020,3,1.
30. Abasi,A.K.; Khader,A.T.; Al-Betar,M.A.; Naim,S.; Makhadmeh,S.N.; Alyasseri,Z.A.A.Anovelensemblestatisticaltopic
extractionmethodforscientificpublicationsbasedonoptimizationclustering.Multimed.ToolsAppl.2021,80,37–82.[CrossRef]
31. Yong-Dong,X.;Guang-Ri,Q.;Zhi-Ming,X.;Ya-Dong,W.Researchontexthierarchicaltopicidentificationalgorithmbasedon
thedynamicdiversethresholdsclustering.InProceedingsofthe2009InternationalConferenceonAsianLanguageProcessing,
Singapore,7–9December2009;pp.206–210.
32. Abu-Rasheed,H.;Weber,C.;Zenkert,J.;Krumm,R.;Fathi,M.ExplainableGraph-BasedSearchforLessons-LearnedDocumentsinthe
SemiconductorIndustry,IntelligentComputing;Springer:Cham,Switzerland,2022;pp.1097–1106.
33. Yang, Z.; Pan, W.; Wang, Y. Group Cooperative Learning Model and Its Application Based on Group Knowledge Graph.
InProceedingsofthe2021IEEE3rdInternationalConferenceonComputerScienceandEducationalInformatization(CSEI),
Xinxiang,China,18–20June2021;pp.324–327.

Sustainability2022,14,226 21of21
34. Phillips, D.; Soltis, J.F. Perspectives on learning. In Perspectives on Learning; Teachers College Press, Colombia University:
NewYork,NY,USA,2015.
35. Brain,C.;Mukherji,P.Understandingchildpsychology. InUnderstandingChildPsycholog;NelsonThornesLtd.:London,UK,
2005.
36. Bandura,A.SocialLearningTheory;Morristown,N.J.,Ed.;GeneralLearningPress:NewYork,NY,USA,1971.
37. Boeree, C.G. Gestalt Psychology. 2000. Available online: https://intranet.newriver.edu/images/stories/library/Stennett_
Psychology_Articles/Gestalt_Psychology.pdf(accessedon29October2021).
38. Bodner,G.;Klobuchar,M.;Geelan,D.Themanyformsofconstructivism.J.Chem.Educ.2001,78,1107.[CrossRef]
39. Taylor,E.W.Transformativelearningtheory.InTransformativeLearningTheory;WileyPeriodicals,Inc.:Hoboken,NJ,USA,2018;
pp.301–320.
40. Siemens,G.Connectivism:Alearningtheoryforthedigitalage.Int.J.Instr.Technol.DistanceLearn.2005,2,1–9.
41. Downes,S.Newtechnologysupportinginformallearning.J.Emerg.Technol.WebIntell.2010,2,27–33.[CrossRef]
42. Dirckinck-Holmfeld, L.; Jones, C.; Lindström, B. Analysing Networked Learning Practices in Higher Education and Continuing
ProfessionalDevelopment;SensePublishers:Rotterdam,TheNetherlands,2009.
43. Berners-Lee,T.;Hendler,J.Publishingonthesemanticweb.Nature2001,410,1023–1024.[CrossRef][PubMed]
44. Rehurek,R.;Sojka,P.Softwareframeworkfortopicmodellingwithlargecorpora.InProceedingsoftheLREC2010Workshopon
NewChallengesforNlpFrameworks,Valletta,Malta,22May2010.
45. Ravuri,S.;Vinyals,O.Classificationaccuracyscoreforconditionalgenerativemodels.arXiv2019,arXiv:1905.10887.