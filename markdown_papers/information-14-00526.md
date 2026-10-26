---
title: "information-14-00526"
source: "information-14-00526.pdf"
source_sha256: "fd33d4df34c257b89e510d4a274e5af4d2036f7a789073f9dea8a414f79855d3"
converted_at: "2026-10-26T07:05:10.788445+00:00"
markitdown_version: "0.1.9"
---
informatio n
Article
Automatic Construction of Educational Knowledge Graphs:
A Word Embedding-Based Approach
QuratUlAin* ,MohamedAmineChatti* ,KomlanGluckCharlesBakar,ShoebJoarderandRawaaAlatrash
SocialComputingGroup,FacultyofEngineering,UniversityofDuisburg-Essen,47057Duisburg,Germany;
komlan.bakar@stud.uni-due.de(K.G.C.B.);shoeb.joarder@uni-due.de(S.J.);
rawaa.alatrash@stud.uni-due.de(R.A.)
* Correspondence:qurat.ain@stud.uni-due.de(Q.U.A.);mohamed.chatti@uni-due.de(M.A.C.)
Abstract: Knowledgegraphs(KGs)arewidelyusedintheeducationdomaintoofferlearnersa
semanticrepresentationofdomainconceptsfromeducationalcontentandtheirrelations,termedas
educationalknowledgegraphs(EduKGs).PreviousstudiesonEduKGshaveincorporatedconcept
extractionandweightingmodules. However,thesestudiesfacelimitationsintermsofaccuracy
andperformance. Toaddressthesechallenges,thisworkaimstoimprovetheconceptextraction
andweightingmechanismsbyleveragingstate-of-the-artwordandsentenceembeddingtechniques.
Concretely, we enhance the SIFRank keyphrase extraction method by using SqueezeBERT and
we propose a concept-weighting strategy based on SBERT. Furthermore, we conduct extensive
experimentsondifferentdatasets,demonstratingsignificantimprovementsoverseveralstate-of-the-
artkeyphraseextractionandconcept-weightingtechniques.
Keywords: technology-enhancedlearning;massiveopenonlinecourses;educationalknowledge
graphs;courseknowledgegraphs;naturallanguageprocessing
1. Introduction
Citation:Ain,Q.U.;Chatti,M.A.;
Inrecentyears,knowledgegraphs(KGs),asformsofstructuredhumanknowledge,
Bakar,K.G.C.;Joarder,S.;Alatrash,R.
havegarneredconsiderableresearchattentionfrombothacademiaandindustry[1,2]. A
AutomaticConstructionof
EducationalKnowledgeGraphs:A KG,whereinnodesrepresententitiesandedgesdepictrelationshipsbetweenentities,serves
WordEmbedding-BasedApproach. asanintegratedinformationrepositorythatinterlinksheterogeneousdatafromdiverse
Information2023,14,526. https:// domains[3,4]. KGshavedemonstratedrobustcapabilitytoprovidemoreefficientservices
doi.org/10.3390/info14100526 inavastnumberofapplicationdomains,suchasrecommendersystems(Netflix[5]),search
engines(Microsoft’sSatoriandGoogle’sKnowledgeGraph[1]),personalassistantapps
AcademicEditors:MohamedHedi
(Apple’sSiri[6]),andquestionanswering(e.g.,IBM’sWatson[7],WolframAlpha[8]),and
Karray,LindaElmhadhbi,Arkopaul
manymore[9]. However,thesegenericKGstypicallydonotoffersubstantialsupportfor
SarkarandAntonioDeNicola
manydomain-specificapplicationsbecausetheyrequiredeepdomaininformationand
Received:16August2023 knowledge[3].Learningandeducationisoneofsuchdomains.Inthisresearch,wefocuson
Revised:15September2023 theapplicationofKGintheeducationaldomain,referredtoastheeducationalknowledge
Accepted:25September2023 graph(EduKG).RelatedtoEduKGsareconceptmaps[3]andconceptgraphs[10],which
Published:27September2023
areoftenusedintechnology-enhancedlearning(TEL)systems. Thesesystems,suchas
massive open online courses (MOOCs) and learning management systems (LMSs), are
instrumentalinextractingconceptsfromlearningmaterialsandvisualizingthemtolearners
inordertohelpthemjudgethevitalpartsofthelearningmaterials[11].
Copyright: © 2023 by the authors.
Awell-constructedEduKGhasmanybenefits. Itcanassistlearnersineasilyunder-
Licensee MDPI, Basel, Switzerland.
standingfactsandconnectingdifferentconcepts,andispivotalinaccuratelymodelingthe
This article is an open access article
knowledgestateoflearners. Moreover,itcancontributefacilitatetheprovisionofmore
distributed under the terms and
accurateandpersonalizedrecommendationsofrelatedconceptstobemasteredorrele-
conditionsoftheCreativeCommons
Attribution(CCBY)license(https:// vantlearningresourcestobridgetheunderstandinggap. Previousworksonconstructing
creativecommons.org/licenses/by/ EduKGstypicallyreliedondomainexpertstobuildtheKGmanually, aprocessthatis
4.0/). time-consumingandcostly[12]. Furthermore,theenormousincreaseineducationaldata
Information2023,14,526.https://doi.org/10.3390/info14100526 https://www.mdpi.com/journal/information

Information2023,14,526 2of18
on TEL platforms necessitates an automatic approach to building EduKGs. Automatic
construction of an EduKG is, however, a difficult problem, and brings new challenges,
suchasaccuracyandperformance,whichrequireaddressingfortheeffectiveassembly
ofEduKGs. Tothisend,inthispaper,wefocusonthetaskofautomaticallyconstructing
anEduKGinaMOOCplatform,takingintoconsiderationtheaccuracyandperformance
aspects. TheproposedapproachcanbeeasilyextendedtoanyotherTELplatform.
Theprimarygoalofthisresearchistoinvestigatethepotentialofusingword/sentence
embeddingtechniquestoeffectivelyandefficientlyconstructanEduKG.Thisresearchaims
toanswerthefollowingresearchquestion(RQ): Howcanweleverageknowledgebasesand
word/sentenceembeddingtechniquestoautomaticallyconstructanEduKGbasedontheconcepts
extractedfromlearningmaterials? Toaddresstheaccuracyandperformancechallenges,we
proposeapipelinefortheautomatic,unsupervisedconstructionofEduKGs,relyingon
state-of-the-artwordandsentenceembeddingtechniques. Tothisend,ourmethodology
effectivelycombinesseveralmethods. Theseincludeanunsupervisedembedding-based
method that extracts keyphrases from the learning materials, a concept identification
methodthatidentifiesconceptsfromthekeyphrases, aconceptexpansionmethodthat
provides more context to the learners by introducing them to new concepts, a concept-
weightingapproachthatrankstheconceptsaccordingtotheirrelevancetothelearning
materials,andthevisualizationoftheconceptsandrelationshipswithinanEduKG.
Throughthisresearch,wemakethefollowingcontributions: (1)weadoptandadapt
state-of-the-artword/sentenceembeddingtechniquestoautomaticallyconstructanEduKG,
(2)weenhancetheSIFRankkeyphraseextractionmethodproposedin[13]byadopting
SqueezeBERT[14],atransformermodelforwordembedding,(3)weproposeanembedding-
basedconcept-weightingstrategyusingthesentenceembeddingtechniqueSBERT[15],and
(4)weconductempiricalstudiesondifferentdatasets,demonstratingtheeffectivenessof
theSqueezeBERT-enhancedSIFRankkeyphraseextractionmethodaswellastheefficiency
ofSBERT-basedconcept-weightingstrategyagainstseveralbaselines.
Therestofthispaperisorganizedasfollows: Section2outlinesthetheoreticalback-
ground of this research and discusses related work. Section 3 introduces our MOOC
platform,CourseMapper. Section4describesourproposedmethodologyfortheautomatic
constructionofEduKGs. Section5demonstratestheexperimentalevaluationandresults.
Finally,Section6concludesthepaperandhighlightsfutureresearchdirections.
2. BackgroundandRelatedWork
2.1. EducationalKnowledgeGraphs
EduKGsareusedforvariouseducationalpurposes,e.g.,tosupportlearningandsci-
entificdiscovery[3],predictprerequisitedependenciesamongcoursesinMOOCs[10,16],
providecomputer-aidededucation[17],supportscientificresourceretrieval[18],andrec-
ommendlearningresources[19],learningpaths,knowledgelevels[20],andcurricula[21].
A variant of EduKG, the course knowledge graph (CKG), integrates scattered courses
withknowledgepoints,andfullyreflectstherelationshipbetweencoursesandknowledge
points[22,23]. TheseCKGsarealsobeingwidelyusedtoimprovelearningoutcomes,solve
problemsintraditionalteaching,andenhancethepossibilityofeffectivelearning[23].More-
over,CKGsarebeingusedasthebasisforanintelligentquestion–answeringsystemfor
highschoolcourses[24]andcourserecommendationsbasedonstudentinformation[25].
In general, an EduKG is a heterogeneous graph, where nodes denote entities, and
edgesrepresentrelationsbetweenentities. Theseentitiesandedgescanmodeldifferent
aspectsinTELenvironments. Forinstance,theseEduKGsusuallycomprisevariousenti-
ties,namelycourseconceptsorknowledgepoints[3,26–32],courses[26,29,30,32],course
groups[26],courseinstructorsorlecturers[26,32],universities[26,32],websites[26],learn-
ingplatforms[32],wikiexplanationsofconcepts[27],coursesections[28],questions[28],
keywords [33], and categories [28,33]. In general, it can be concluded that concepts or
knowledge points are the basic building blocks of every EduKG and, hence, must be
extractedaccuratelyandefficiently.

Information2023,14,526 3of18
Previously, EduKGs were manually constructed by course experts. However, due
tothelimitationsofthismanualapproachintermsoftimeandeffort,differentworksin
recentyearshaveaddressedtheproblemofautomaticallygeneratingEduKGsbyemploy-
ingmachinelearning(ML)andnaturallanguageprocessing(NLP)techniques. Various
methodshavebeenintroducedbyresearchersdependingontherequirementsandtasks
to be achieved. The most essential task in the construction of EduKGs is entity extrac-
tion. ThistaskhasbeenachievedbasedonavarietyofMLandNLP-basedmethodsand
willbediscussedindetailinSection2.2. Anotherimportanttaskintheconstructionof
EduKGsisrelationextraction,whichinvolvesconnectingdifferententitiesintheEduKG.
Theserelationshipsaremainlysequentialorsemanticrelationshipsandarefoundusing
DBpediaspotlight[25],ruleprocessing,KNN[26],probabilisticassociationrulemining[3],
binaryclassificationonmodelstrainedwithlabeleddatasets[34],binaryclassificationon
trainedmodelsusingfeedforwardneuralnetworks[35],prompt-tuningwithsynergistic
optimization[36],cosinesimilarity[27,29],PMI,normalizedgoogledistance[31],semantic
rolelabeling[37],prerequisiterelationcalculationsbasedonthepreliminaryknowledge
tagsofthecourses[20],andrule-basedrelationextraction[38]. Anotherwidelyadopted
task in the construction of EduKGs is entity linking with an external knowledge base,
mainlyWikipedia[25,27,28,32,33,39]. ThisisachievedusingWikipediaAPIordifferent
entity-linkingservices,suchasDBpediaSpotlight[25,39]andBabelfy[39]. Someofthe
research studies have also focused on concept expansion for the semantic enrichment
withnewrelatedconcepts,forexample,usingWikipediacategories[25,33,39]ortheBaidu
Encyclopedia [31]. Furthermore, some of the studies have also incorporated concept-
weightingstrategiestoranktheidentifiedconceptsbasedontheirweights. Theweighting
strategyusedinmostofthestudiesistermfrequency–inversedocumentfrequency(TF-
IDF)[25,26,37,39].
Mostrelatedworksprimarilyfocusonasubsetofthetasksmentionedabove.Only[25]
adoptedamorecompletesetofsteps,includingconceptlinking,expansion,andweighting.
UnliketheEduKGconstructionpipelinein[25],weperformkeyphraseextractionbeforethe
conceptlinkingstep. Thisstepisintroducedtothepipelinetoachievebetterefficiencyand
performancebyannotatingonlytheextractedkeyphraseswiththeentity-linkingservice
ratherthansendingthewholetextofthelearningmaterialforannotation. Furthermore,
in the concept-weighting step, we use word embedding techniques instead of TF-IDF.
Althoughefficient,TF-IDF-basedconcept-weightingmethodsareusuallyimprecisebecause
theydonotconsiderthesemanticrelatednessbetweenconcepts.
2.2. AutomaticConceptExtraction
Concepts represent the core part of any EduKG. Thus, concept extraction is an es-
sentialstepintheconstructionofEduKGs. Toobtainconcept-levelknowledge,manual
indexingoflearningmaterialsortextbooksischallenging,time-consuming,andproneto
errors[40]. Therehasbeenincreasedresearchonautomaticconceptextractionfromlearn-
ingmaterials,mainlythroughdirectentitylinkingofthematerialstoexternalknowledge
bases,orbyperformingkeyphraseextractiononthetextofthelearningmaterials.
Several research studies have used direct entity linking via named entity recogni-
tion(NER)[38,41,42]andentity-linkingservices[25,26,28,32,33,39,41,43]. Itisacommon
practicetouseentitylinkingtoidentifyconceptsfromthetext. However,applyingentity
linkingtolearningmaterialswithalargeamountoftextisnotefficient,asthissteprequires
sendingmultiplerequeststoanentity-linkingservice. Toovercomethisissue,fewworks
havefocusedonfirstextractingkeyphrasesfromthetextandthenusingthesekeyphrases
toidentifyconcepts. Theseworkshaveemployedvariousmachinelearningmethods,such
asrule-basedlearning[44],supervisedlearning[40],unsupervisedlearning[37],anddeep
neuralnetworks[3,31].
In our work, we apply keyphrase extraction as a pre-step to entity linking from
Wikipedia. Ouraimistofilterthelistofconceptcandidates,thusmakingtheautomatic
concept extraction more efficient. We focus on unsupervised methods for keyphrase

Information2023,14,526 4of18
extraction,asthesupervisedmethodsneedmodelstrainedonthedomain-specificcorpus
todetectconcepts,requiringasignificantamountoftrainingdata,whicharenotavailable
inourcontext. Weadopt,enhance,andcompareastate-of-the-artwordembedding-based
keyphraseextractionapproachwithseveralbaselines.Tothebestofourknowledge,itisthe
firstworkapplyingwordembedding-basedkeyphraseextractionmethodsforeducational
conceptextraction. OtherworksusedwordembeddingstoconstructanEduKGbutfora
purposeotherthanautomaticconceptextraction[20,27].
3. EduKGinCourseMapper
OurmaingoalistoautomaticallyconstructanEduKGforthelearningmaterialin
CourseMapper. CourseMapperisaMOOCplatformthatwedevelopedtohelplearnersef-
fectivelycreateandmanagecourses,collaboratewitheachother,andinteractwithlearning
materialsusingsharedannotations[45]. Generally,anEduKGontopofaMOOCplatform
isaheterogeneousinformationnetworkconsistingofdifferententitiesandrelationships
between them. Concepts represent important entities to be modeled in any EduKG in
ordertoprovideanoverviewofthemainconceptsinthelearningmaterials,helplearners
beawareofwhatistobelearned,anddrawtheirattentiontothemostcrucialconcepts.
Consequently,thisfacilitatesthelearners’achievementandcreatesapositiveperception
ofthematerials[46]. Inadditiontoconcepts,theEduKGnormallycontainsotherentities,
suchaslearners,teachers,courses,andvideos,aswellastherelationshipsamongthose
entities. Figure1showsapartofthenetworkschemaofourEduKGinCourseMapperwith
differententitytypesandthesemanticlinksbetweenthem. ThispartoftheEduKGconsists
offivetypesofentities,namelytheuser,learningmaterial(slidesorvideo),concept,related
concept,andcategory,aswellastherelationshipsbetweentheseentities.
Figure1.NetworkschemarepresentingtheEduKGentitiesandtherelationshipsbetweenthem.
Witheverylearningmaterial(slidesinourexample), learnersareprovidedwitha
“DidNotUnderstand(DNU)”button,whichtheycanclicktoviewtheconceptsextracted
fromthecurrentslide(seeFigure2). Then,theycanclicktoselecttheconcreteconceptsthat
theydonotunderstandfromthatslide. Thisinformationisusedtomodeltherelationships
“Understand”(U)and“Did-Not-Understand”(DNU)betweenlearnersandconceptsin
the EduKG. This can provide an effective way to model the learner’s knowledge state,

Information2023,14,526 5of18
whichcanbeusedtoprovidepersonalizedrecommendationsofprerequisiteconceptsto
bemastered,aswellasrelevantrelatedexternallearningresourcesthatcanhelplearners
understandtheconceptsontheslide. Theconceptsextractedfromthelearningmaterials
are expanded based on related concepts and categories in Wikipedia (see Figure 1). In
thenextsection,wewilldiscussourproposedapproachfortheautomaticextractionof
conceptsintheEduKG.
Figure2.CourseMapper’suserinterface,showingtheDNUbutton.
4. Methodology
RegardingthedevelopmentoftheKGforlearningmaterials,thefollowingessential
factors must be considered: The KG aims to highlight the relevant concepts inside the
learningmaterials,aswellasallowlearnerstodiscovernewconceptsthatarenotnecessarily
mentionedinthelearningmaterials. Thissectiondescribesthepipelineweusedforthe
automaticextractionofconceptstobuildtheEduKGinCourseMapper(seeFigure3);we
specificallyfocusonthekeyphraseextractionandconcept-weightingmodules,whichare
the core contributions of this paper. Note that, although we are building an EduKG in
a MOOC platform, all the components of our pipeline can be replicated for any other
TELenvironment.
Figure3.PipelinefortheautomaticconstructionofanEduKG.

Information2023,14,526 6of18
4.1. TextExtraction
ThefirststepintheconstructionofourEduKGistextextractionfromPDFlearning
materialsinCourseMapper. ExtractingtexteffectivelyandaccuratelyfromthePDFisone
of the most challenging tasks in text mining because of the variation in text styles and
formats. Usually,theextractionmethodlacksawarenessofthelayoutofthePDFfile. To
solvethisproblem,thelayoutaspectofthePDFfilehastobetakenintoconsiderationto
makesurethatwordsinthesameboxareaccuratelyextracted.Weusedasimpleformofthe
methodproposedin[47],alayout-awarePDFtextextraction. Themethodconsistsofthree
steps: (1)detectingcontiguoustextblocks,(2)classifyingtextblocksintocategoriesusing
arule-basedmethod,and(3)stitchingclassifiedtextblockstogetherinthecorrectorder.
Forthefirststep,contiguoustextblocksaredetectedfromthePDFusinganopen-source
toolPDFMiner[48]. WithPDFMiner,informationaboutcharactersandtheirpositionsin
thePDFfileisobtained. Thenasinstep(3)ofthementionedapproach[47],basedonthe
proximityoftheircoordinates,charactersaregroupedintolinesandblocksoftext.
4.2. KeyphraseExtraction
Weappliedkeyphraseextractionasapre-steptoentitylinkingfromWikipedia. This
step is motivated by the need to avoid sending learning materials with large amounts
oftexttoanentity-linkingservice,thusitimprovestheefficiencyofthenextstepinthe
pipeline,i.e.,conceptidentification(seeSection4.3). Thekeyphraseextractionstepisbuilt
onthebasisofSIFRank[13],astate-of-the-artunsupervisedkeyphraseextractionmethod
thatisbasedonapre-trainedlanguagemodel. ThefirststepintheSIFRankprocessistext
preprocessing. TokenizationisperformedonthetextusingtheCoreNLPlibrary. Then,
part-of-speech (POS) tagging is applied to the generated tokens using the same library.
Lastly,embeddingsofthesePOS-taggedtokensaregeneratedusingembeddingtechniques.
Theauthorsin[13]createdwordembeddingsofthetokenswithELMo[49],andsentence
embeddingswithsentenceinversefrequency(SIF)[50]. Accordingtotheauthorsin[13],
SIFRankachievedthebestperformanceinkeyphraseextractionforshortdocuments. For
longdocuments,theauthorsextendedSIFRanktoSIFRankplus,whichusesposition-biased
weighttoimproveitsperformanceinlongdocuments.
WeadoptedtheSIFRankkeyphraseextractionprocesswithsomemodificationsto
achievebetterresults,basedonourexperiments. Firstly,weperformedtokenizationon
the text. Then, we applied POS tagging on the generated tokens. Lastly, we generated
embeddingsofthesePOS-taggedtokensusingtheSIFRankandSIFRankplusembedding
techniquesforshortandlongdocuments,respectively. Recognizingtheperformanceof
state-of-the-arttransformer-basedpre-trainedlanguagemodels,wereplacedELMowiththe
pre-trainedSqueezeBERT[14]asawordembeddingmethodinSIFRankandSIFRankplus.
ThedecisiontouseSqueezeBERTismotivatedbyitslightweighttransformerarchitecture
with higher information flow between the layers; moreover, it is faster than the BERT
model[14]. WeconductedextensiveexperimentsusingtheSIFRank/SIFRankpluswith
ELMo-basedandSIFRank/SIFRankpluswithSqueezeBERT-basedpre-trainedmodelsand
comparedthemwithdifferentstatistical,graph-based,andembedding-basedkeyphrase
extractionmethodsintermsofaccuracy(seeSection 5.1). Theresultsshowthatwhileour
proposedSIFRank/SIFRankpluswithSqueezeBERTmethodsoutperformedotherbaseline
models,theaccuracyofthekeyphraseextractiontaskwasrelativelylowwithanF1-score
of40.38%inthebestcase.
4.3. ConceptIdentification
Thekeyphrasesobtainedinthepreviousstepareusedasinputfortheconceptiden-
tification step. Identifying concepts from the keyphrases requires the use of external
knowledge bases. Similar to [25], we use DBpedia Spotlight [51] to link keyphrases to
conceptsinDBpedia. DBpediaSpotlightisapowerfulentity-linkingtoolthatcanquickly
and efficiently identify meaningful substrings (or annotations) in a text and link them
to related DBpedia concepts. DBpedia Spotlight is used for automatically annotating

Information2023,14,526 7of18
mentionsofDBpediaresourcesintext,basedonthreesteps: (1)spotting,i.e.,applyinga
string-matchingalgorithmbasedontheDBpedialexicontoidentifyanymentioninthe
textmatchingaDBpediaresource,withprioritygiventothelongestcase-insensitivematch;
(2)candidateselection,i.e.,selectingcandidateDBpediaresourcesforeachspottedmention
to narrow down the space of disambiguation possibilities; and (3) disambiguation, i.e.,
finding the best candidate DBpedia resource for the spotted mention using contextual
information. We use the DBpedia Spotlight web service, which supplies endpoints for
spotting,disambiguation,andannotationbykeepingthesupportparametersetto5andthe
confidenceparameterto0.35,asusedby[39]. Wealsousethecontextualscoreassignedby
DBpediaSpotlighttoacandidateDBpediaresourceusingitscontextualinformation[51].
Concepts can, however, wrongly be identified when using DBpedia Spotlight or
anyotherentity-linkingservices. Manriqueetal. [25]refertothisproblemasincorrect
annotation,i.e.,“theconceptsaremistakenlylinked”. Sincethisisanautomaticprocess
and,thus,theidentifiedconceptsarenotmanuallyevaluated,weuseaweightingstrategy
thatlooksatthesemanticsimilaritiesoftheidentifiedconceptstothelearningmaterials.
ThisweightingstrategyisdiscussedindetailinSection4.5.
4.4. ConceptExpansion
ToenrichtheEduKG,weapplyanexpansionsteptotheidentifiedconcepts. Con-
sideringthatthekeyphraseextractionstepdoesnotproduceresultswithhighaccuracy
(seeSection 4.2)and,consequently,theconceptidentificationstepdoesnotdetermineall
conceptsrelevanttothelearningmaterials,weexpandtheEduKGwithadditionalconcepts.
Theseadditionalconceptscanimprovethecoverageanddiversityoftheidentifiedconcepts,
enhancethestructureoftheEduKG,helpfurtherdevelopthelearners’knowledge,and
promote concept exploration and discovery. Expanded concepts can also be important
toreinforcethemaintopicofthelearningmaterialiftheyarenotpresentinthelearning
material[52]. Theexpansionisperformedwhileconsideringthesemanticrelationships
of the concepts in the knowledge base. We adopt the two types of expansion, namely
category-basedexpansionandproperty-basedexpansion,asproposedin[25]. Wereferto
property-basedexpansionasarelatedconceptexpansioninthiswork.
4.4.1. Category-BasedExpansion
TheEduKGisenrichedwiththecategoriesoftheidentifiedconcepts. Forexample,for
theconceptof“Naturallanguageprocessing”,thecategories“Category:Computational
linguistics”and“Category:Artificialintelligence”areaddedtotheEduKG.Theseadded
categoriesprovidehierarchicalinformationabouttheconceptsandallowuserstodiscover
more broad concepts. SPARQL queries retrieving the categories (through the ontology
propertydct:subject)oftheconceptsareexecutedagainstthepublicSPARQLendpoint
ofDBpedia.
4.4.2. RelatedConceptExpansion
The EduKG is enriched with the related concepts of the identified concepts. For
example,fortheconceptof“Naturallanguageprocessing”,therelatedconceptof“Natural
languageunderstanding”isaddedtothegraph. Therelatedconceptsareextractedusing
SPARQLandtheontologypropertydbo:wikiPageWikiLink. Todeterminetheexistenceof
apathbetweenthetwoconcepts,SPARQLqueriesareexecutedagainstthepublicSPARQL
endpointofDBpediatoretrievethepropertypathsbetweenthetwoconcepts. Anedgeis
createdbetweenthetwonodesifapropertypathisfound.
4.5. ConceptWeighting
The expansion is a beneficial step in creating the EduKG; however, the expansion
canintroduceevenmorenoisyconceptsinthegraph[53]. Toovercomethisproblem,the
concept-weightingstrategyisusedtoweighttheconceptsinthegraph.Withthisweighting

Information2023,14,526 8of18
strategy,conceptsthatarecontextuallyandsemanticallysimilartothelearningmaterials
willhavehighweightsasopposedtonoisyconceptswhoseweightswillbelower.
Manrique et al. [25] proposed a weighting strategy to solve the aforementioned
problem, basedonthreesteps: (1)conceptfrequency: aTF-IDF-basedweightingofthe
concepts in the KG, which helps determine the importance of a concept to a particular
pieceoflearningmaterialbypenalizingconceptsthatappearoftenacrossmultiplelearning
materials;(2)categorydiscount: thispenalizescategoriesthataretoobroadandgeneric
in the hierarchy of the KG; and (3) related concept discount: this penalizes frequently
relatedconcepts. Thisstrategy,albeiteffectiveasaweightingstrategy,failstoconsiderthe
contextofthewordsandcapturethesemanticawarenessfromboththelearningmaterials
and the concepts. Recently, word and sentence embedding techniques have garnered
increasingattentionduetotheimpressiveperformancetheyhavedemonstratedacross
awiderangeofNLP-relatedscenarios. Thesetechniquesexcelatcapturingthesemantic
meaningofwordsordocumentsandthecontextualrelationshipsbetweenthem,which
canbeeffectivelyusedtoextractmeaningfuldatarepresentations, gainasemanticand
relationalunderstandingofthedata,andmeasuresemanticsimilaritiesbetweenwordsor
documents[54,55]. Forthisreason,weproposeanotherweightingstrategyfortheconcepts
byleveragingtheadvantagesoftransformermodels,particularlytheSBERTmodel[15].
Ourapproach(w )worksasfollows.
SBERT
4.5.1. ConceptWeighting
Theembeddingofthecontentofthelearningmaterialemb andtheembeddingof
lmi
thecontentoftheconcept(i.e.,thetextcontentofitsWikipediaarticle)emb aredefined
c
usingSBERT.ToretrievetheWikipediaarticletext,theWikipediaAPI(https://pypi.org/
project/Wikipedia-API/, accessed on 1 August 2023 ) is used. Then, the weight of the
conceptinthelearningmaterialiscomputedasthecosinesimilarityscorebetweenemb
lmi
andemb .
c
4.5.2. RelatedConceptWeighting
The embedding of the content of the learning material emb and the embedding
lmi
ofthecontentoftherelatedconcept(thetextcontentoftheWikipediaarticle)emb are
rel
computedusingSBERT.Theweightoftherelatedconceptisthecosinesimilarityscore
betweenemb andemb .
lmi rel
4.5.3. CategoryWeighting
Theembeddingofthecontentofthelearningmaterialemb andtheembeddingof
lmi
thecategorynameemb arecomputedusingSBERT.Wikipediacategorypagesarenot
cat
Wikipediaarticlesand,thus,donothavetextcontent. Therefore,thenameofthecategory
isused. Theweightofthecategoryisthecosinesimilarityscorebetweenemb andemb .
lmi cat
Thiswillhelpdeterminethecategory’simportanceinthelearningmaterial.
4.6. KnowledgeGraphStorage
AgraphdatabaseishighlysuitableforstoringtheKGdatasincetheconceptswill
needtobestoredwithseveralproperties. TheconstructedKGisstoredinaNeo4jgraph
databaseasfollows:
• EachconceptintheKGisstoredasanode. Theconceptisattachedtoproperties,such
asthenameoftheconcept.
• Arelationshipofthetyperelated_toisstoredtoconnecttwonodes,eitheraconcept
fromtheidentificationmoduleorarelatedconceptfromtheexpansionmodule.
• Arelationshipofthetypebelongs_toisstoredtoconnectanodetoanodeofthetype
category.
• Thelearningmaterialisstoredasanode.
• Arelationshipofthetypecontainsisstoredtoconnectthelearningmaterialtothe
concepts.

Information2023,14,526 9of18
Figure4showstheillustrationoftheKGstoredinagraphdatabase. Therearefour
typesofnodestobeobserved: ThelearningmaterialLM1,whichcontainsaconceptC1,
a related concept C2 and a category C3. Supposing that following the expansion and
weightingsteps,conceptC1isfoundtoberelatedtoC2andiscategorizedunderC3and,
thus,addedtotheKG,relationshipsofthetyperelated_toandbelongs_toarecreatedbetween
C1andC2,andbetweenC1andC3,respectively.
id: ...
| id: ... | name: ... |     |
| ------- | --------- | --- |
name: ...
| type: ... | type: ... |     |
| --------- | --------- | --- |
uri: ...
| uri: ... | mid: ... |     |
| -------- | -------- | --- |
mid: ...
| weight: ... | weight: ... |     |
| ----------- | ----------- | --- |
type: related_concept
| type: concept | wikipedia: ... |     |
| ------------- | -------------- | --- |
wikipedia: ...
| C1  | related_to | C2  |
| --- | ---------- | --- |
belongs_to
contains
contains
C3
|     | contains | id: ... |
| --- | -------- | ------- |
name: ...
| LM1 |     | type: ... |
| --- | --- | --------- |
uri: ...
mid: ...
weight: ...
| id: ... |     | type: category |
| ------- | --- | -------------- |
wikipedia: ...
name: ...
Figure4.KGillustrationinagraphdatabase.
4.7. KnowledgeGraphVisualization
TheKGisvisualizedinCourseMapperbyshowingabuttonatthetopofeachlearning
material,tomakeiteasilyaccessibletousers,asshowninFigure5. Withthisbutton,users
areabletodisplayorhidetheKGinterface. AsillustratedinFigure6,usersarealsoable
tointeractwiththeKGthroughselectionandfilteringactions,toonlyviewspecificparts
of the KG, based on their needs. Additionally, users can obtain more information on a
concept by selecting its node. Once the node is selected, the Wikipedia abstract of the
conceptwillappearontherightsideoftheKGinterface. Ifneeded,userscanalsoseea
detaileddescriptionoftheconceptbyclickingthe“ReadfullarticleonWikipedia”button
(seeFigure6).
Figure5.LearningmaterialwiththeKGbutton.

Information2023,14,526 10of18
Figure6.VisualizingandinteractingwithaKGinCourseMapper.
5. ExperimentalEvaluation
Experimentsarecarriedouttoevaluatetheperformanceoftheproposedmethods
relatedtothekeyphraseextractionandconcept-weightingstepsoftheEduKGconstruc-
tionpipeline.
5.1. KeyphraseExtractionEvaluation
Wecomparetheextractionaccuraciesandefficienciesofdifferentkeyphraseextraction
methods, such as statistical, graph-based, and embedding-based keyphrase extraction
methods. Theembedding-basedmethodsincludetheoriginalSIFRankandSIFRankplus
methodsbasedonELMo[13],andourproposedkeyphraseextractionmethods,SIFRank
andSIFRankplus,basedonSqueezeBERTforshortandlongdocuments,respectively.
5.1.1. Datasets
Inordertoconducttheexperiments,threewell-knownbenchmarkdatasetsareused:
(1)Inspec[56],adocumentcollectionof2000scientificabstractswithsetsofkeyphrasesiden-
tifiedbyexpertannotators,(2)SemEval2017[57],adoubleannotateddocumentcollection
of493paragraphsextractedfrom500ScienceDirectjournalarticles,and(3)DUC2001[58],
acollectionof308newsarticlescollectedfromTREC-9. Table1presentsasummaryof
thedatasets.
Table1.Summaryofdatasets.
Dataset Inspec SemEval2017 DUC2001
TypeofDocuments Abstracts Paragraph News
No.ofDocuments 500 493 308
AverageWords 134.4 194.7 828.4
Averagekeyphrases 9.8 17.3 8.1
5.1.2. Baselines
Theproposedkeyphraseextractionmethods(SIFRank andSIFRankplus )
SqueezeBERT SqueezeBERT
arecomparedagainstdifferentunsupervisedkeyphraseextractionmethodsontheselected
datasets. Thesemethodsincludestatistical-basedmethods(YAKE[59],RAKE[60],and
TF-IDF[61]), graph-basedmethods(MultiPartiteRank[62], TopicalPageRank[63], Topi-
cRank[64],PositionRank[65],SingleRank[66],TextRank[67]),embedding-basedmodels

Information2023,14,526 11of18
(EmbedRank[68],SIFRank,andSIFRankplus[13]).EmbedRankisevaluatedusingsent2vec
(s2v)anddoc2vec(d2v). Thebaselinesgeneratecandidatephrasesusingnounphrases.
ThePythonkeyphraseextraction(PKE)(https://github.com/boudinfl/pke,accessedon
1August2023)isusedtorunthestatistical-basedmodelsandthegraph-basedmodels.
EmbedRank(https://github.com/swisscom/ai-research-keyphrase-extraction,accessed
on1August2023)andSIFRank(https://github.com/sunyilgdx/SIFRank, accessedon
1 August 2023) are used to produce the results of the embedding-based models on the
selecteddatasets.
|     | 5.1.3. | ResultsandAnalysis |     |     |     |     |     |     |
| --- | ------ | ------------------ | --- | --- | --- | --- | --- | --- |
Weconductedexperimentsusingtheabove-mentionedbaselinemodelsandthepro-
|     | posed | SIFRank |             | and SIFRankplus |             | methodsontheintroducedshort |     |     |
| --- | ----- | ------- | ----------- | --------------- | ----------- | --------------------------- | --- | --- |
|     |       |         | SqueezeBERT |                 | SqueezeBERT |                             |     |     |
documentdatasets(InspecandSemEval2017)andlongdocumentdataset(DUC2001),to
extractthetop5,10,and15keyphrases. Themetricsusedforevaluationwereprecision,
recall, and F1-score. The results are presented in Table 2. Here, metrics are denoted as
percentagepointsandboldindicatesthebestmetric.
Table2.Evaluationresultsofkeyphraseextractionmethods.Kisthenumberofkeyphrasesextracted
fromasingledocumentbythemodels.
|     |     |     | Inspec |     | SemEval2017 |     | DUC2001 |     |
| --- | --- | --- | ------ | --- | ----------- | --- | ------- | --- |
K Method
|                  |       | P     | R     | F1          | P R   | F1    | P R | F1  |
| ---------------- | ----- | ----- | ----- | ----------- | ----- | ----- | --- | --- |
|                  | YAKE  | 22.48 | 11.44 | 15.16 25.15 | 7.27  | 11.28 | - - | -   |
|                  | RAKE  | 30.33 | 15.43 | 20.45 29.61 | 8.56  | 13.28 | - - | -   |
|                  | TFIDF | 16.52 | 8.41  | 11.14 30.06 | 8.69  | 13.48 | - - | -   |
| MultiPartiteRank |       | 28.94 | 14.72 | 19.51 34.40 | 9.94  | 15.43 | - - | -   |
| TopicalPageRank  |       | 32.96 | 16.77 | 22.23 35.74 | 10.33 | 16.03 | - - | -   |
| TopicRank        |       | 28.66 | 14.57 | 19.32 33.95 | 9.81  | 15.23 | - - | -   |
| PositionRank     |       | 31.98 | 16.27 | 21.56 35.82 | 10.35 | 16.06 | - - | -   |
| SingleRank       |       | 31.52 | 16.04 | 21.26 34.04 | 9.84  | 15.26 | - - | -   |
5
| TextRank |     | 17.85 | 8.81 | 11.80 18.33 | 5.30 | 8.22 | - - | -   |
| -------- | --- | ----- | ---- | ----------- | ---- | ---- | --- | --- |
EmbedRank d2v 26.36 13.41 17.78 29.24 8.45 13.11 9.70 6.00 7.42
EmbedRank s2v 40.24 20.48 27.14 47.74 13.79 21.41 33.81 20.91 25.84
SIFRank 43.20 21.99 29.14 48.64 14.06 21.81 31.79 19.67 24.30
ELMo
SIFRankplus 42.12 21.44 28.41 47.99 13.87 21.52 40.26 24.91 30.78
ELMo
SIFRank 44.00 22.39 29.68 49.21 14.22 22.07 30.75 19.02 23.50
SqueezeBERT
| SIFRankplus    | SqueezeBERT | -     | -     | -           | - -   | -     | 41.69 25.80 | 31.87 |
| -------------- | ----------- | ----- | ----- | ----------- | ----- | ----- | ----------- | ----- |
| Improvement(%) |             | 1.85  | 1.81  | 1.85 1.17   | 1.14  | 1.19  | 3.51 3.57   | 3.54  |
|                | YAKE        | 18.00 | 18.32 | 18.16 22.74 | 13.14 | 16.66 | - -         | -     |
|                | RAKE        | 27.60 | 27.89 | 27.74 28.42 | 16.43 | 20.82 | - -         | -     |
TFIDF
|                  |     | 14.62 | 14.88 | 14.75 24.16 | 13.96 | 17.70 | - - | -   |
| ---------------- | --- | ----- | ----- | ----------- | ----- | ----- | --- | --- |
| MultiPartiteRank |     | 24.19 | 24.28 | 24.24 29.00 | 16.75 | 21.24 | - - | -   |
| TopicalPageRank  |     | 29.60 | 29.86 | 29.73 33.04 | 19.10 | 24.21 | - - | -   |
| TopicRank        |     | 24.09 | 23.92 | 24.00 27.41 | 15.84 | 20.08 | - - | -   |
| PositionRank     |     | 27.45 | 27.62 | 27.54 31.87 | 18.42 | 23.34 | - - | -   |
| SingleRank       |     | 28.77 | 29.11 | 28.94 32.45 | 18.76 | 23.77 | - - | -   |
10
| TextRank |     | 14.81 | 12.70 | 13.68 17.31 | 9.72 | 12.45 | - - | -   |
| -------- | --- | ----- | ----- | ----------- | ---- | ----- | --- | --- |
EmbedRank 24.90 25.02 24.96 27.44 15.86 20.10 8.91 11.00 9.85
d2v
EmbedRank 34.96 35.09 35.03 42.88 24.78 31.41 28.05 34.62 30.99
s2v
SIFRank 38.63 38.84 38.73 43.45 25.11 31.83 24.97 30.83 27.60
ELMo
SIFRankplus 36.44 36.64 36.54 42.49 24.56 31.13 30.20 37.28 33.37
ELMo
SIFRank SqueezeBERT 39.36 39.58 39.47 43.73 25.28 32.04 26.04 32.16 28.78
| SIFRankplus |     | -   | -   | -   | - - | -   | 31.79 39.26 | 35.13 |
| ----------- | --- | --- | --- | --- | --- | --- | ----------- | ----- |
SqueezeBERT

Information2023,14,526 12of18
Table2.Cont.
|     |     | Inspec |     | SemEval2017 | DUC2001 |     |
| --- | --- | ------ | --- | ----------- | ------- | --- |
K Method
|                  | P     | R     | F1    | P R F1            | P R       | F1   |
| ---------------- | ----- | ----- | ----- | ----------------- | --------- | ---- |
| Improvement(%)   | 1.89  | 1.9   | 1.91  | 0.64 0.67 0.65    | 5.26 5.31 | 5.27 |
| YAKE             | 16.10 | 24.59 | 19.46 | 21.73 18.84 20.18 | - -       | -    |
| RAKE             | 24.34 | 36.20 | 29.11 | 25.79 22.35 23.94 | - -       | -    |
| TFIDF            | 13.88 | 21.19 | 16.77 | 20.76 18.00 19.28 | - -       | -    |
| MultiPartiteRank | 22.16 | 32.14 | 26.23 | 25.95 22.45 24.07 | - -       | -    |
| TopicalPageRank  | 26.65 | 39.15 | 31.71 | 30.52 26.44 28.33 | - -       | -    |
| TopicRank        | 21.49 | 30.09 | 25.08 | 24.02 20.68 22.23 | - -       | -    |
| PositionRank     | 24.31 | 35.50 | 28.86 | 29.12 25.21 27.02 | - -       | -    |
| SingleRank       | 25.71 | 38.05 | 30.69 | 29.84 25.85 27.70 | - -       | -    |
15
| TextRank | 13.00 | 13.64 | 13.31 | 15.80 12.05 13.68 | - - | -   |
| -------- | ----- | ----- | ----- | ----------------- | --- | --- |
EmbedRank 23.58 34.30 27.95 26.90 23.28 24.96 8.31 15.31 10.77
d2v
EmbedRank s2v 31.70 45.98 37.53 38.43 33.26 35.66 24.12 44.45 31.27
SIFRank ELMo 33.49 48.76 39.71 39.14 33.88 36.32 21.56 39.74 27.95
SIFRankplus 32.64 47.52 38.70 38.61 33.43 35.83 24.86 45.83 32.24
ELMo
SIFRank 34.06 49.59 40.38 39.78 34.43 36.91 23.06 42.52 29.91
SqueezeBERT
| SIFRankplus | -   | -   | -   | - - - | 26.91 49.62 | 34.90 |
| ----------- | --- | --- | --- | ----- | ----------- | ----- |
SqueezeBERT
| Improvement(%) | 1.7 | 1.7 | 1.68 | 1.63 1.62 1.63 | 8.24 8.26 | 8.25 |
| -------------- | --- | --- | ---- | -------------- | --------- | ---- |
These methods include statistical-based methods (YAKE [13], RAKE [44], and TF-
IDF[46]),graph-basedmethods(MultiPartiteRank[11],TopicalPageRank[28],TopicRank[12],
PositionRank[22],SingleRank[52],andTextRank[35]),andembedding-basedmodels(Em-
bedRank[8],SIFRank,andSIFRankplus.
Theresultsshowthatembedding-basedmodels(EmbedRank,SIFRank,SIFRankplus)
perform better than statistical-based (YAKE, RAKE, TF-IDF) and graph-based models
(MultiPartiteRank,TopicalPageRank,TopicRank,PositionRank,SingleRank,TextRank)in
alldatasets.
|     | OurproposedSIFRank |     |             | andSIFRankplus | methods(markedin |     |
| --- | ------------------ | --- | ----------- | -------------- | ---------------- | --- |
|     |                    |     | SqueezeBERT | SqueezeBERT    |                  |     |
boldinTable2)consistentlyyieldthebestperformancescomparedwithotherbaselinemod-
elsinshortdocumentdatasets(InspecandSemEval2017)andthelongdocumentdataset
(DUC2001),respectively. Inparticular,SIFRank P lus SqueezeBERT demonstratesimprovement
over the strongest baseline SIFRankplus (underlined in Table 2) w.r.t precision by
ELMo
3.51%,recallby3.57%,andF1-scoreby3.54%whenextracting5keyphrases. Whenextract-
ing10keyphrases,theimprovementsare5.26%w.r.tprecision,5.31%w.r.trecall,and5.27%
w.r.t the F1-score. Lastly, SIFRank P lus SqueezeBERT demonstrates improvement over the
strongestbaselineSIFRankplus w.r.tprecisionby8.24%,recallby8.26%,andF1-score
ELMo
by8.25%whenextracting15keyphrases. ThisindicatesthatusingSIFRankcombinedwith
SqueezeBERTallowsforbetterandmoreaccurateextractionofkeyphrasesfromdocuments
incomparisontoSIFRankbasedonELMo.
Referringtotheexecutiontime,SIFRankwithSqueezeBERTis6xfasterthanSIFRank
withELMoatextractingthekeyphrasesfromtheInspecdataset, 4xfasteratextracting
keyphrases from the SemEval2017 dataset, and almost 3x faster at extracting from the
DUC2001dataset. ThisshowsthatELMo,whichisanLSTMlanguagemodel,isslower
thanSqueezeBERT.
Furthermore,weconductedexperimentstoevaluatetheperformancesofdifferent
layersofSqueezeBERT.SqueezeBERToriginallyhad12layers,andtheexperimentsaimed
tofindthelayersthatperformedbestonthekeyphraseextractiontask. Theexperimentwas
performedbyactivatinganddeactivatingcertainlayersofSqueezeBERTeachtimebefore
computingthewordembeddingsofthetexts. Theresultsoftheexperimentsareshownin
Table3. Tosavespace,weonlypresentafewresultsinthetable. Thelayersarereferred
to as ALL (all layers are utilized for word embeddings, and the resultant embeddings
are derived from the averaged output of all 12 layers), LX (e.g., L0 represents the first

Information2023,14,526 13of18
layer)andLX_Y,i.e.,thewordembeddingsaretheaverageoftheoutputoftheXandY
layers. The results indicate that out of all 12 layers, layers 3 and 5 combined delivered
thebestperformanceresults(markedboldinthetable)onshortdocuments(Inspecand
SemEval2017 datasets). When layers 3 and 5 were used individually, the performance
deterioratedastheywerenotcapableofefficientlycapturingthesemanticcontextofthe
words. Inlongdocuments(DUC2001dataset),layers0and1outperformedotherlayers
(markedboldinthetable). Theselayerscombinedcanefficientlycapturethecontextual
featuresofwordsinlongdocuments.
Table3.PerformanceevaluationofSqueezeBERTlayersondifferentdatasets.
Inspec SemEval2017 DUC2001
K Method Layers
P R F1 P R F1 P R F1
ALL 43.16 21.97 29.11 48.23 13.94 21.63 - - -
SIFRank−
5 L3 43.0 21.88 29.00 49.13 14.20 22.03 - - -
SqueezeBERT
L3_5 44.0 22.39 29.68 49.21 14.22 22.06 - - -
L0 - - - - - - 41.17 25.47 31.47
SIFRankplus−
5 L1 - - - - - - 39.93 24.70 30.52
SqueezeBERT
L0_1 - - - - - - 41.69 25.79 31.87
5.2. Concept-WeightingEvaluation
Theexperimentalevaluationoftheconcept-weightingstepispresentedtoshowthe
performance of our proposed SBERT-based concept-weighting method, referred to as
w (seeSection4.5),ascomparedtothebaselines.
SBERT
5.2.1. ExperimentalSetup
Toevaluatetheproposedconcept-weightingmethodagainstthebaselines,weusethe
DBpedia2016-10releaseversion,whichisoneofthemostusedKGforNLPresearch. We
furtheruseDBpediaSpotlightintheconceptidentificationsteptoannotatethekeyphrases.
TheEduKGconstructedinthisresearchistobeappliedinCourseMapper,whichisaMOOC
platform. Therefore,theCCIdataset(https://github.com/Ruframapi/CCI,accessedon1
August2023)isusedastheevaluationdataset. Itconsistsof96videotranscriptsoflearning
resources extracted from Coursera (https://www.coursera.org/, accessed on 1 August
2023)intheareaofprogrammingfundamentals. Foralllearningresources, thedataset
containsthecoreconcepts,whichwereannotatedbysevenexperts[25]. Inthekeyphrase
extractionstep,thetop15keyphrasesareextractedfromthelearningresources. Thesame
evaluationmetricsusedtoevaluatethekeyphraseextractions,i.e.,precision,recall,and
F1-score,areusedtodeterminetheaccuraciesofthetopkrankedconcepts.
5.2.2. Baselines
Several weighting strategies are used as baselines to compare the accuracy of our
proposedw concept-weightingmethod. Thefirststrategy,referredtoasw ,uses
SBERT cf
simpletermfrequency(TF)toweighttheconcepts[69]. Thesecondstrategy,referredtoas
w cf−idf ,involvestheenhancementoftheTF-basedstrategybyaddinginversedocument
frequency(IDF)withadiscountforexpandedconcepts,asproposedbyManriqueetal.[25].
Theotherstrategiesusecentralitymeasures[70], suchas(1)degreecentrality(DE):the
weight of a node (concept or related concept or category), c, is the number of nodes
connectedtocdividedbythetotalnumberofnodesintheKGl;(2)betweennesscentrality
(BET):theweightofanode,c,isthefractionoftheshortestpathsbetweenallpossiblenode
pairsthatpassthroughc;(3)PageRank(PR):itrankstheimportanceofnodesintheKG;
PRestimatesthatanoderankshighifthesumoftheranksofitsbacklinksishigh. The
weightofanode,c,isthePRscore.

Information2023,14,526 14of18
5.2.3. ResultsandAnalysis
Figure 7 shows the distribution of concepts in the CCI dataset when we map the
experts’annotatedconceptstotheconcepts, relatedconcepts, andcategoriesidentified
by our approach. Most of the concepts annotated by the experts are related concepts
(183). Noneoftheannotatedconceptsinthedatasetisofthecategorytype;98concepts
(unknownconcepts)annotatedbytheexpertshavenotbeenidentifiedafterourconcept
identificationandexpansionsteps. Basedontheresultsobtainedduringtheexperiments
forthetop3,5,and10rankedconcepts,itisobservedthatourstrategyw SBERT (marked
in bold in Table 4) is more precise than the other strategies, as the precision for all top
k-rankedconceptsishigher(seeTable4,withoutharmonicmean). Inparticular,forthe
top10rankedconcepts,w demonstratesimprovementoverthestrongestbaselines
SBERT
(underlinedinTable4)w.r.tprecisionby17.8%andw.r.ttheF1-scoreby14.5%. Thisshows
that w is the better strategy for selecting a high number of concepts. Despite the
SBERT
higherprecisionofourstrategy, w SBERT , PR showsbetterrecallandanF1-scoreforthe
topthreeandtopfiverankedconcepts. Thiscanbeexplainedbythefactthatduringthe
annotationofconcepts,theexpertsfocusedmoreonthediversityoftheconceptsinthe
learning resource collection. Another explanation for these results is that, while in our
approach,conceptswereidentifiedfromonlythetop15keyphrasesextractedfromthe
learningresource,Manriqueetal. [25]didnotuseanintermediatekeyphraseextraction
moduleintheirexperimentsbutdirectlyfedthelearningresourcecontenttotheDBpedia
Spotlight,whichresultedinahighercountofidentifiedconcepts.
Table4.Evaluationresultsofconcept-weightingtechniquesforthetopk-rankedconcepts.
|     | WithoutHarmonicMean | WithHarmonicMean |     |
| --- | ------------------- | ---------------- | --- |
K Method
|     | P R       | F1 P      | R F1      |
| --- | --------- | --------- | --------- |
| w   | 23.6 20.5 | 21.9 23.6 | 20.5 21.9 |
cf
| w   | 24.2 25.4 | 24.8 24.2 | 25.4 24.8 |
| --- | --------- | --------- | --------- |
cf−idf
| DE  | 18.5 17.1 | 17.8 18.5 | 17.1 17.8 |
| --- | --------- | --------- | --------- |
3
| BET      | 19.4 20.3 | 19.8 19.4 | 20.3 19.8 |
| -------- | --------- | --------- | --------- |
| PR       | 23.9 30.1 | 26.6 23.9 | 30.1 26.6 |
| w (Ours) | 24.3 20.7 | 22.3 23.9 | 20.3 22.0 |
SBERT
| Improvement(%) | 0.4 -     | - -       | - -       |
| -------------- | --------- | --------- | --------- |
| w cf           | 17.9 25.7 | 21.1 17.9 | 25.7 21.1 |
| w cf−idf       | 19.2 27.2 | 22.5 19.2 | 27.2 22.5 |
| DE             | 14.9 20.1 | 17.1 14.9 | 20.1 17.1 |
5
| BET            | 16.7 26.3 | 20.4 16.7 | 26.3 20.4 |
| -------------- | --------- | --------- | --------- |
| PR             | 18.7 35.1 | 24.4 18.7 | 35.1 24.4 |
| w SBERT (Ours) | 20.0 28.3 | 23.4 21.3 | 30.2 25.0 |
| Improvement(%) | 4.1 -     | - 11      | - 2.5     |
| w              | 11.4 32.7 | 16.8 11.4 | 32.7 16.8 |
cf
w
| cf−idf | 11.8 37.3 | 17.9 11.8 | 37.3 17.9 |
| ------ | --------- | --------- | --------- |
| DE     | 8.5 28.1  | 13.1 08.5 | 28.1 13.1 |
10
| BET      | 9.6 33.2  | 14.9 09.6 | 33.2 14.9 |
| -------- | --------- | --------- | --------- |
| PR       | 11.6 39.7 | 18.0 11.6 | 39.7 18.0 |
| w (Ours) | 13.9 39.5 | 20.6 14.0 | 39.8 20.7 |
SBERT
| Improvement(%) | 17.8 - | 14.5 18.6 | 0.25 15 |
| -------------- | ------ | --------- | ------- |
Recognizing the benefits of incorporating context to enhance the accuracy of the
generatedconcepts,wefurtherleveragethecontextualscoreassignedbyDBpediaSpotlight,
obtained as a result of the concept identification step (see Section 4.3), to increase the
weightsoftheidentifiedconcepts. Thecontextualscoreconsidersthesurroundingcontext
of the text. It is calculated for each potential entity, based on various factors. These
includethefrequencyoftheentityintheDBpediaknowledgebase,thecontextinwhich

Information2023,14,526 15of18
it appears in the text, and the co-occurrence of other words in the text that are related
totheentity[51]. Wemodifytheweightsoftheconceptsinthelearningmaterialtothe
harmonic mean of the similarity score between the learning material and the concept,
andthecontextualscoreassignedbyDBpediaSpotlight, asdefinedinEquation1. The
weightsoftherelatedconceptsandthecategoriesremainthesameasdescribedearlier.
ThisresultedinanenhancementoftheF1-scorefortheselectionofthetop5andtop10
ranked concepts utilizing the w strategy (see Table 4, with harmonic mean). For
SBERT
thetopthreerankedconcepts,thePRstrategyremainsthebeststrategyfollowedbythe
w cf−idf strategy. Overall,ourevaluationresultsshowthatw SBERT withtheharmonicmean
isthebest-performingconcept-weightingstrategywhenextractingfiveormoreconcepts
inlearningmaterials.
2×contextualScore(c)×cos(emb ,emb )
w(lm,c) = c lmi (1)
i contextualScore(c)+cos(emb ,emb )
c lmi
Figure7.AnnotatedconceptdistributionintheCCIdataset,mappedtoourresults.
6. ConclusionsandFutureWork
Inthiswork,weaimedtoanswertheresearchquestion“Howtoleverageknowledge
basesandword/sentenceembeddingtechniquestoautomaticallyconstructanEducational
KnowledgeGraph(EduKG)basedontheconceptsextractedfromlearningmaterials?”.
Toanswerthis,weproposedapipelinefortheautomaticconstructionofEduKGs,inan
unsupervisedmanner,relyingonstate-of-the-artwordandsentenceembeddingtechniques.
Furthermore,weconductedextensiveexperimentsondifferentdatasets,demonstrating
significantaccuracyandefficientimprovementsoverseveralstate-of-the-artkeyphrase
extractionandconcept-weightingstrategies. Ourevaluationresultsconfirmthatwordand
sentenceembeddingsprovideasimple,yetpowerfulmethodtoeffectivelyandefficiently
construct EduKGs in an automatic manner. As part of future research, we will aim to
extensivelyevaluatetheaccuraciesoftheconstructedEduKGswithCourseMapperusers.
Moreover, we plan to follow a human-in-the-loop approach to improve the quality of
theautomaticallyconstructedEduKGs. Furthermore,weplantoutilizetheconstructed
EduKGs for learning materials in CourseMapper to recommend personalized learning
resources(e.g.,YouTubevideosandWikipediaarticles),aswellasrelatedconcepts,based
onthelearners’currentknowledgestate.
AuthorContributions:Conceptualization,Q.U.A.andM.A.C.;methodology,Q.U.A.,M.A.C.and
K.G.C.B.;software,K.G.C.B.andS.J.;validation,M.A.C.;writing—originaldraftpreparation,Q.U.A.
andK.G.C.B.;writing—reviewandediting,Q.U.A.andM.A.C.;visualization,Q.U.A.,S.J.,K.G.C.B.
andR.A.;supervision,M.A.C.,S.J.andQ.U.A.Allauthorshavereadandagreedtothepublished
versionofthemanuscript.
Funding:Thisresearchreceivednoexternalfunding.

Information2023,14,526 16of18
DataAvailabilityStatement:Nonewdatawerecreatedoranalyzedinthisstudy.Datasharingis
notapplicabletothisarticle.
Acknowledgments: WeacknowledgethesupportfromtheOpenAccessPublicationFundofthe
UniversityofDuisburg-Essen.
ConflictsofInterest:Theauthorsdeclarenoconflictofinterest.
References
1. Dong,X.;Gabrilovich,E.;Heitz,G.;Horn,W.;Lao,N.;Murphy,K.;Strohmann,T.;Sun,S.;Zhang,W. Knowledgevault: A
web-scaleapproachtoprobabilisticknowledgefusion. InProceedingsofthe20thACMSIGKDDInternationalConferenceon
KnowledgeDiscoveryandDataMining,NewYork,NY,USA,24–27August2014;pp.601–610.
2. Hogan,A.;Blomqvist,E.;Cochez,M.;d’Amato,C.;Melo,G.D.;Gutierrez,C.;Kirrane,S.;Gayo,J.E.L.;Navigli,R.;Neumaier,S.;
etal. Knowledgegraphs. ACMComput.Surv.(CSUR)2021,54,1–37.[CrossRef]
3. Chen,P.;Lu,Y.;Zheng,V.W.;Chen,X.;Yang,B. Knowedu:Asystemtoconstructknowledgegraphforeducation. IEEEAccess
2018,6,31553–31563.[CrossRef]
4. Novak,J.D.;Cañas,A.J. Thetheoryunderlyingconceptmapsandhowtoconstructandusethem.Fla.Inst.Hum.Mach.Cogn.
2008,1,1–31.
5. Netflix. Availableonline:https://www.netflix.com/de/(accessedon3April2023).
6. AppleSiri.2017. Availableonline:https://www.apple.com/siri/(accessedon23April2023).
7. IBMWatson.2017. Availableonline:https://www.ibm.com/watson/(accessedon30April2023).
8. WolframAlpha. Availableonline:https://www.wolframalpha.com/(accessedon30April2023).
9. Ji,S.;Pan,S.;Cambria,E.;Marttinen,P.;Philip,S.Y. Asurveyonknowledgegraphs:Representation,acquisition,andapplications.
IEEETrans.NeuralNetw.Learn.Syst.2021,33,494–514.[CrossRef][PubMed]
10. Yang,Y.; Liu,H.; Carbonell,J.; Ma,W. Conceptgraphlearningfromeducationaldata. InProceedingsoftheEighthACM
InternationalConferenceonWebSearchandDataMining,Shanghai,China,2–6February2015;pp.159–168.
11. Shukla,H.;Kakkar,M. KeywordextractionfromEducationalVideotranscriptsusingNLPtechniques. InProceedingsofthe
20166thInternationalConference—CloudSystemandBigDataEngineering(Confluence),Noida,India,14–15January2016;
pp.105–108.[CrossRef]
12. Wang,S. KnowledgeGraphCreationfromStructureKnowledge;ThePennsylvaniaStateUniversity:StateCollege,PA,USA,2017.
13. Sun,Y.;Qiu,H.;Zheng,Y.;Wang,Z.;Zhang,C. SIFRank: ANewBaselineforUnsupervisedKeyphraseExtractionBasedon
Pre-TrainedLanguageModel. IEEEAccess2020,8,10896–10906.[CrossRef]
14. Iandola,F.N.;Shaw,A.E.;Krishna,R.;Keutzer,K.W. SqueezeBERT:WhatcancomputervisionteachNLPaboutefficientneural
networks? arXiv2020,arXiv:2006.11316.
15. Reimers,N.;Gurevych,I. Sentence-bert:Sentenceembeddingsusingsiamesebert-networks. arXiv2019,arXiv:1908.10084.
16. Liu, H.; Ma, W.; Yang, Y.; Carbonell, J. Learning concept graphs from online educational data. J. Artif. Intell. Res. 2016,
55,1059–1090.[CrossRef]
17. Shen,Y.;Chen,Z.;Cheng,G.;Qu,Y. CKGG:AChineseknowledgegraphforhigh-schoolgeographyeducationandbeyond. In
ProceedingsoftheSemanticWeb—ISWC2021:20thInternationalSemanticWebConference,ISWC2021,VirtualEvent,24–28
October2021;Proceedings20;Springer:Berlin/Heidelberg,Germany,2021;pp.429–445.
18. Chi,Y.;Qin,Y.;Song,R.;Xu,H. Knowledgegraphinsmarteducation:Acasestudyofentrepreneurshipscientificpublication
management. Sustainability2018,10,995.[CrossRef]
19. Yang,X.;Tan,L. TheConstructionofAccurateRecommendationModelofLearningResourcesofKnowledgeGraphunderDeep
Learning. Sci.Program.2022,2022,1010122.[CrossRef]
20. Chen, Q.; Xia, J.; Feng, J.; Tong, M. ResearchonKnowledgeGraphConstructionforPythonProgrammingLanguage. In
ProceedingsoftheInternationalConferenceonSmartLearningEnvironments,Hangzhou,China,18–20August2022;Springer:
Berlin/Heidelberg,Germany,2022;pp.119–126.
21. Hubert,N.;Brun,A.;Monticolo,D. NewOntologyandKnowledgeGraphforUniversityCurriculumRecommendation. In
ProceedingsoftheISWC2022—The21stInternationalSemanticWebConference,VirtualEvent,23–27October2022.
22. Morsi,R.;Ibrahim,W.;Williams,F. Conceptmaps:Developmentandvalidationofengineeringcurricula. InProceedingsofthe
200737thAnnualFrontiersinEducationConference-GlobalEngineering:KnowledgewithoutBorders,Opportunitieswithout
Passports,Milwaukee,WI,USA,10–13October2007;IEEE:Piscataway,NJ,USA,2007;pp.T3H-3–T3H-6.
23. Zhu,P.;Zhong,W.;Yao,X. Auto-ConstructionofCourseKnowledgeGraphbasedonCourseKnowledge. Int.J.Perform.Eng.
2019,15,2228.
24. Yang,Z.;Wang,Y.;Gan,J.;Li,H.;Lei,N. Designandresearchofintelligentquestion-answering(Q&A)systembasedonhigh
schoolcourseknowledgegraph. Mob.Netw.Appl.2021,26,1884–1890.
25. Manrique,R.;Grévisse,C.;Mariño,O.;Rothkugel,S. Knowledgegraph-basedcoreconceptidentificationinlearningresources.
In Proceedings of the Joint International Semantic Technology Conference, Awaji, Japan, 26–28 November 2018; Springer:
Berlin/Heidelberg,Germany,2018;pp.36–51.

Information2023,14,526 17of18
26. Zheng,Y.;Liu,R.;Hou,J. TheconstructionofhigheducationalknowledgegraphbasedonMOOC. InProceedingsofthe2017
IEEE2ndInformationTechnology,Networking,ElectronicandAutomationControlConference(ITNEC), Chengdu,China,15–17
December2017;IEEE:Piscataway,NJ,USA,2017;pp.260–263.
27. Deng,Y.;Lu,D.;Huang,D.;Chung,C.J.;Lin,F. Knowledgegraphbasedlearningguidanceforcybersecurityhands-onlabs. In
ProceedingsoftheACMConferenceonGlobalComputingEducation,Chengdu,China,17–19May2019;pp.194–200.
28. Rahdari,B.;Brusilovsky,P.;Thaker,K.;Barria-Pineda,J. Usingknowledgegraphforexplainablerecommendationofexternal
contentinelectronictextbooks. InProceedingsoftheiTextbooks@AIED,Virtual,6–9July2020.
29. Qiao,L.;Yin,C.;Chen,H.;Sun,H.;Rong,W.;Xiong,Z. AutomatedConstructionofCourseKnowledgeGraphBasedonChina
MOOCPlatform. InProceedingsofthe2019IEEEInternationalConferenceonEngineering,TechnologyandEducation(TALE),
Yogyakarta,Indonesia,10–13December2019;pp.1–7.[CrossRef]
30. Chen, H.; Yin, C.; Fan, X.; Qiao, L.; Rong, W.; Zhang, X. LearningpathrecommendationforMOOCplatformsbasedona
knowledgegraph. InProceedingsoftheInternationalConferenceonKnowledgeScience,EngineeringandManagement,Tokyo,
Japan,14–16August2021;Springer:Berlin/Heidelberg,Germany,2021;pp.600–611.
31. Su,Y.;Zhang,Y. Automaticconstructionofsubjectknowledgegraphbasedoneducationalbigdata. InProceedingsofthe3rd
InternationalConferenceonBigDataandEducation,Chengdu,China,21–23August2020;pp.30–36.
32. Dang,F.R.;Tang,J.T.;Pang,K.Y.;Wang,T.;Li,S.S.;Li,X. ConstructinganEducationalKnowledgeGraphwithConceptsLinked
toWikipedia. J.Comput.Sci.Technol.2021,36,1200–1211.[CrossRef]
33. Rahdari,B.;Brusilovsky,P. BuildingaKnowledgeGraphforRecommendingExperts. InProceedingsoftheDI2KG@KDD,
Anchorage,Alaska,5August 2019.
34. Mondal, I.; Hou, Y.; Jochim, C. End-to-endconstructionofNLPknowledgegraph. InProceedingsoftheFindingsofthe
AssociationforComputationalLinguistics:ACL-IJCNLP2021,OnlineEvent,1–6August2021;pp.1885–1895.
35. Stewart,M.;Liu,W. Seq2kg:Anend-to-endneuralmodelfordomainagnosticknowledgegraph(nottextgraph)construction
fromtext. InProceedingsoftheInternationalConferenceonPrinciplesofKnowledgeRepresentationandReasoning,Rhodes,
Greece,12–18September2020;Volume17,pp.748–757.
36. Chen,X.;Zhang,N.;Xie,X.;Deng,S.;Yao,Y.;Tan,C.;Huang,F.;Si,L.;Chen,H. Knowprompt:Knowledge-awareprompt-tuning
withsynergisticoptimizationforrelationextraction. InProceedingsoftheACMWebConference2022,Lyon,France,25–29April
2022;pp.2778–2788.
37. Wang,T.;Li,H. Coreferenceresolutionimproveseducationalknowledgegraphconstruction. InProceedingsofthe2020IEEE
InternationalConferenceonKnowledgeGraph(ICKG),Nanjing,China,9–11August2020;IEEE:Piscataway,NJ,USA,2020;
pp.629–634.
38. Qin,Y.;Cao,H.;Xue,L. ResearchandApplicationofKnowledgeGraphinTeaching:Takethedatabasecourseasanexample.
Proc.J.Phys.Conf.Ser.2020,1607,012127.[CrossRef]
39. Grévisse,C.;Manrique,R.;Mariño,O.;Rothkugel,S. Knowledgegraph-basedteachersupportforlearningmaterialauthor-
ing. InProceedingsoftheColombianConferenceonComputing, Cartagena,Colombia,26–28September 2018; Springer:
Berlin/Heidelberg,Germany,2018;pp.177–191.
40. Chau,H.;Labutov,I.;Thaker,K.;He,D.;Brusilovsky,P. Automaticconceptextractionfordomainandstudentmodelingin
adaptivetextbooks. Int.J.Artif.Intell.Educ.2021,31,820–846.[CrossRef]
41. Zhao,B.;Sun,J.;Xu,B.;Lu,X.;Li,Y.;Yu,J.;Liu,M.;Zhang,T.;Chen,Q.;Li,H.;etal. EDUKG:AHeterogeneousSustainableK-12
EducationalKnowledgeGraph. arXiv2022,arXiv:2210.12228.
42. Zhang,N.;Xu,X.;Tao,L.;Yu,H.;Ye,H.;Qiao,S.;Xie,X.;Chen,X.;Li,Z.;Li,L.;etal. Deepke:Adeeplearningbasedknowledge
extractiontoolkitforknowledgebasepopulation. arXiv2022,arXiv:2201.03335.
43. Sultan,M.A.;Bethard,S.;Sumner,T. Towardsautomaticidentificationofcoreconceptsineducationalresources. InProceedings
oftheIEEE/ACMJointConferenceonDigitalLibraries,London,UK,8–12September2014;IEEE:Piscataway,NJ,USA,2014;
pp.379–388.
44. Wang,X.;Feng,W.;Tang,J.;Zhong,Q. CourseconceptextractioninMOOCviaexplicit/implicitrepresentation. InProceedings
ofthe2018IEEEThirdInternationalConferenceonDataScienceinCyberspace(DSC),Guangzhou,China,18–21June2018;IEEE:
Piscataway,NJ,USA,2018;pp.339–345.
45. Ain, Q.U.; Chatti, M.A.; Joarder, S.; Nassif, I.; WobiwoTeda, B.S.; Guesmi, M.; Alatrash, R. LearningChannelstoSupport
InteractionandCollaborationinCourseMapper. InProceedingsofthe14thInternationalConferenceonEducationTechnology
andComputers,Barcelona,Spain,28–30October2022;pp.252–260.
46. Bonwell,C.C. Usingactivelearningtoenhancelectures. Appl.Econ.Perspect.Policy1999,21,542–550.[CrossRef]
47. Ramakrishnan,C.;Patnia,A.;Hovy,E.;Burns,G.A. Layout-awaretextextractionfromfull-textPDFofscientificarticles. Source
CodeBiol.Med.2012,7,1–10.[CrossRef]
48. Shinyama, Y. PDFMiner—Python PDF Parser. 2007. Available online: https://unixuser.org/~euske/python/pdfminer/
(accessedon23April2023).
49. ELMo. Availableonline:https://allenai.org/allennlp/software/elmo(accessedon23April2023).
50. Arora,S.;Liang,Y.;Ma,T. Asimplebuttough-to-beatbaselineforsentenceembeddings. InProceedingsoftheInternational
ConferenceonLearningRepresentations,Toulon,France,24–26April 2017.

Information2023,14,526 18of18
51. Mendes,P.N.;Jakob,M.;García-Silva,A.;Bizer,C. DBpediaspotlight:Sheddinglightonthewebofdocuments. InProceedings
ofthe7thInternationalConferenceonSemanticSystems,Graz,Austria,7–9September2011;pp.1–8.
52. Manrique,R.;Marino,O. KnowledgeGraph-basedWeightingStrategiesforaScholarlyPaperRecommendationScenario. In
ProceedingsoftheKaRS@RecSys,Vancouver,BC,Canada,7October 2018;pp.5–8.
53. Manrique,R.;Herazo,O.;Mariño,O. Exploringtheuseoflinkedopendataforuserresearchinterestmodeling. InProceedings
oftheColombianConferenceonComputing,Cali,Colombia, 19–22September 2017;Springer:Berlin/Heidelberg,Germany,
2017;pp.3–16.
54. Hassan,H.A.M. Personalizedresearchpaperrecommendationusingdeeplearning. InProceedingsofthe25thConferenceon
UserModeling,AdaptationandPersonalization,Bratislava,Slovakia,9–12July2017;pp.327–330.
55. Hassan,H.A.M.;Sansonetti,G.;Gasparetti,F.;Micarelli,A.;Beel,J. Bert,elmo,useandinfersentsentenceencoders:Thepanacea
forresearch-paperrecommendation? InProceedingsoftheRecSys(Late-BreakingResults), Copenhagen, Denmark, 16–20
September2019;pp.6–10.
56. Hulth,A. Improvedautomatickeywordextractiongivenmorelinguisticknowledge. InProceedingsofthe2003Conferenceon
EmpiricalMethodsinNaturalLanguageProcessing, Sapporo,Japan,11–12July2003;pp.216–223.
57. Augenstein,I.;Das,M.;Riedel,S.;Vikraman,L.;McCallum,A. Semeval2017task10: Scienceie-extractingkeyphrasesand
relationsfromscientificpublications. arXiv2017,arXiv:1704.02853.
58. Wan,X.;Xiao,J. Singledocumentkeyphraseextractionusingneighborhoodknowledge. InProceedingsoftheTwenty-Third
AAAIConferenceonArtificialIntelligence,Chicago,IL,USA,13–17July2008;Volume8,pp.855–860.
59. Campos,R.;Mangaravite,V.;Pasquali,A.;Jorge,A.M.;Nunes,C.;Jatowt,A. YAKE!Keywordextractionfromsingledocuments
usingmultiplelocalfeatures. Inf.Sci.2020,509,257–289.[CrossRef]
60. Rose, S.; Engel, D.; Cramer, N.; Cowley, W. Automatic Keyword Extraction from Individual Documents. In Text Mining:
ApplicationsandTheory;JohnWiley&Sons,Ltd.:Hoboken,NJ,USA,2010;pp.1–20.[CrossRef]
61. Salton,G.;Buckley,C. Term-weightingapproachesinautomatictextretrieval. Inf.Process.Manag.1988,24,513–523.[CrossRef]
62. Boudin,F. UnsupervisedKeyphraseExtractionwithMultipartiteGraphs. InProceedingsoftheNAACL,NewOrleans,LA,
26–30June2018; pp.667–672.[CrossRef]
63. Jardine,J.G.;Teufel,S. TopicalPageRank:AModelofScientificExpertiseforBibliographicSearch. InProceedingsoftheEACL,
Gothenburg,Sweden,26–30April 2014.
64. Bougouin,A.;Boudin,F.;Daille,B. TopicRank:Graph-BasedTopicRankingforKeyphraseExtraction. InProceedingsofthe
IJCNLP,Nagoya,Japan,14–19October2013.
65. Florescu,C.;Caragea,C. PositionRank:AnUnsupervisedApproachtoKeyphraseExtractionfromScholarlyDocuments. In
Proceedingsofthe55thAnnualMeetingoftheAssociationforComputationalLinguistics(Volume1: LongPapers); Associationfor
ComputationalLinguistics:Vancouver,BC,Canada,2017;pp.1105–1115.[CrossRef]
66. Wan,X.;Xiao,J. CollabRank:TowardsaCollaborativeApproachtoSingle-DocumentKeyphraseExtraction. InProceedingsof
theCOLING,Manchester,UK,18–22August2008.
67. Mihalcea,R.;Tarau,P. TextRank:BringingOrderintoText. InProceedingsoftheEMNLP,Barcelona,Spain,25–26July2004.
68. Bennani-Smires, K.; Musat, C.; Hossmann, A.; Baeriswyl, M.; Jaggi, M. SimpleUnsupervisedKeyphraseExtractionUsing
SentenceEmbeddings.arXiv2018,arXiv:1801.04470.
69. Roy,D.;Sarkar,S.;Ghose,S. AutomaticExtractionofPedagogicMetadatafromLearningContent. Int.J.Artif.Intell.Educ.2008,
18,97–118.
70. Boudin,F.AComparisonofCentralityMeasuresforGraph-BasedKeyphraseExtraction. InProceedingsoftheSixthInternational
JointConferenceonNaturalLanguageProcessing,Nagoya,Japan,14–19October2013;AsianFederationofNaturalLanguage
Processing:Nagoya,Japan,2013;pp.834–838.
Disclaimer/Publisher’s Note: The statements, opinions and data contained in all publications are solely those of the individual
author(s)andcontributor(s)andnotofMDPIand/ortheeditor(s).MDPIand/ortheeditor(s)disclaimresponsibilityforanyinjuryto
peopleorpropertyresultingfromanyideas,methods,instructionsorproductsreferredtointhecontent.