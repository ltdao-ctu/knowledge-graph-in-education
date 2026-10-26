---
title: "Hu2024foke"
source: "Hu2024foke.pdf"
source_sha256: "5033fdd6160b9b464ec6278fc0488b2c469c4a39b23e858d1db1076f72e45731"
converted_at: "2026-10-26T07:04:56.519681+00:00"
markitdown_version: "0.1.9"
---
FOKE: A PERSONALIZED AND EXPLAINABLE EDUCATION
FRAMEWORK INTEGRATING FOUNDATION MODELS,
KNOWLEDGE GRAPHS, AND PROMPT ENGINEERING
SILANHU XiaoningWang
MacauUniversityofScienceandTechnology CommunicationUniversityofChina
Macau,China Beijing,China
2240000339@student.must.edu.mo sdwangxiaoning@cuc.edu.cn
ABSTRACT
Integratinglargelanguagemodels(LLMs)andknowledgegraphs(KGs)holdsgreatpromisefor
revolutionizingintelligenteducation,butchallengesremaininachievingpersonalization,interactivity,
and explainability. We propose FOKE, a Forest Of Knowledge and Education framework that
synergizesfoundationmodels,knowledgegraphs,andpromptengineeringtoaddressthesechallenges.
FOKEintroducesthreekeyinnovations: (1)ahierarchicalknowledgeforestforstructureddomain
knowledge representation; (2) a multi-dimensional user profiling mechanism for comprehensive
learner modeling; and (3) an interactive prompt engineering scheme for generating precise and
tailoredlearningguidance.
WeshowcaseFOKE’sapplicationinprogrammingeducation,homeworkassessment,andlearning
pathplanning,demonstratingitseffectivenessandpracticality. Additionally,weimplementScholar
Hero, a real-world instantiation of FOKE. Our research highlights the potential of integrating
foundationmodels,knowledgegraphs,andpromptengineeringtorevolutionizeintelligenteducation
practices,ultimatelybenefitinglearnersworldwide. FOKEprovidesaprincipledandunifiedapproach
toharnessingcutting-edgeAItechnologiesforpersonalized,interactive,andexplainableeducational
services,pavingthewayforfurtherresearchanddevelopmentinthiscriticaldirection.
Keywords: Intelligenteducation,LargeLanguageModels,PromptEngineering,Personalization,KnowledgeRepresen-
tation
1 Introduction
1.1 Background
The rapid development of Artificial Intelligence (AI) has profoundly impacted various domains, and education is
noexception. AI-empowerededucationhasthepotentialtorevolutionizetraditionalteachingandlearningpractices,
makinghigh-qualityeducationmoreaccessibleandaffordabletolearnersfromdiversebackgrounds. Byleveraging
advancedAItechnologies,suchasLargeLanguageModels(LLMs),intelligenttutoringsystems,andadaptivelearning
platforms, AI-powerededucationaltoolscanprovidepersonalized, interactive, andengaginglearningexperiences,
cateringtotheindividualneedsandpreferencesofeachlearner[1][2].
AmongthevariousAItechnologies, LLMshaveemergedasagame-changerintheeducationallandscape. LLMs,
suchasGPT-4[3]andPaLM2[4],possessremarkablecapabilitiesinnaturallanguageunderstanding,generation,and
reasoning,enablingawiderangeofapplicationsineducation,includingautomaticquestionanswering,essayscoring,
andknowledgerecommendation[5]. Forinstance,theintegrationofChatGPT,astate-of-the-artconversationalAI
model,intolanguagelearningenvironmentshasshownpromisingresultsinenhancinglearners’motivation,engagement,
andlearningoutcomes[6].
ThepotentialofLLMstodemocratizeaccesstohigh-qualityeducationalresourcesandsupporthasattractedincreasing
attentionfromresearchersandpractitioners. [7]exploredtheopportunitiesandchallengesofintegratingLLMsintodata
4202
yaM
6
]CH.sc[
1v43730.5042:viXra

RunningTitleforHeader
scienceeducation,highlightingtheirrolesingeneratingpersonalizedlearningcontent,providingadaptivefeedback,and
fosteringinteractivelearningexperiences. ByharnessingthepowerofLLMs,educationalinstitutionsandplatforms
canofferaffordable,scalable,andeffectiveeducationalservicestolearnerswhomaynothaveaccesstotraditional
high-qualityeducationalresources,suchasexpertteachersorwell-equippedclassrooms.
However, the application of LLMs in educational scenarios is still in its early stages and faces several challenges.
First, educational contexts often involve complex domain knowledge and diverse learner backgrounds, requiring
LLMstoprovidepersonalizedandadaptivelearningsupport. Second,effectiveeducationreliesoninteractiveand
engaginglearningexperiences,whichdemandsLLMstomaintaincoherentandmeaningfuldialoguewithlearners.
Third,educationalapplicationsofLLMsshouldofferinterpretableandtrustworthyexplanationstofacilitatelearners’
understandingandteachers’intervention[8].
ToaddressthesechallengesandfullyunleashthepotentialofLLMsindemocratizinghigh-qualityeducation,wepropose
FOKE(ForestOfKnowledgeandEducation),anovelframeworkthatintegratesfoundationmodels,knowledgegraphs,
andpromptengineering. FOKEaimstoprovidepersonalized,interactive,andexplainableeducationalservicesby
leveragingthestrengthsoftheseadvancedtechniques. Inthefollowingsections,wewillintroducethekeycomponents
andmethodologiesofFOKEindetail.
1.2 Motivation
Promptengineering,anemergingparadigminLLMapplication,hasshownpromisingpotentialtoaddresstheaforemen-
tionedchallenges. Promptengineeringreferstotheprocessofdesigningandoptimizingprompttemplates,whichare
naturallanguageinstructionsthatguideLLMstoperformspecifictasks[9]. Bycarefullycraftingprompts,researchers
havesuccessfullyadaptedLLMstoavarietyofdownstreamapplications,suchasvisualquestionanswering[10],text
classification[11],andcodeaugmentation[12]. Thesuccessofpromptengineeringcanbeattributedtoitsabilityto
leveragetheknowledgeandskillsembeddedinLLMswhileprovidingaflexibleandcontrollableinterfacefortask
customization.
Inthecontextofintelligenteducation,promptengineeringholdsgreatpromiseforenablingpersonalized,interactive,
and explainable LLM-based services. By incorporating learner-specific information and domain knowledge into
prompts, LLMs can generate tailored learning content and provide adaptive feedback to individual students. By
designingconversation-orientedprompts,LLMscanengageinmeaningfuldialoguewithlearnersandoffertimely
supportandguidance. Byinjectingrationalesandexplanationsintoprompts,LLMscanproduceinterpretableand
trustworthyeducationalsuggestionsandassessments. Therefore,theintegrationofpromptengineeringandLLMs
opensupnewopportunitiesforrevolutionizingintelligenteducationpractices.
1.3 ResearchObjectives
Motivated by the potential of prompt engineering and LLMs in intelligent education, we propose FOKE, a novel
frameworkthataimstoachievethefollowingobjectives:
• Objective1: Developknowledgerepresentationandusermodelingtechniquesforpersonalizedlearning.
This objective includes (1) designing a hierarchical knowledge representation scheme to encode domain
knowledgeandsupportpersonalizedlearningpaths;and(2)developingamulti-dimensionaluserprofiling
mechanismtocapturelearnercharacteristics,preferences,andstyles,enablingadaptiveeducationalservices.
• Objective2: Explorepromptengineeringapproachesforgeneratingpreciseandinterpretablelearning
guidance. Underthisobjective,weaimto(1)designastructuredpromptrepresentationapproachtoelicit
accurateandcoherentfeedbackfromLLMs;and(2)investigatetheintegrationofknowledgerepresentation
andusermodelingtofacilitatepersonalizedrecommendationandadaptiveinstruction.
• Objective3: ShowcasetheapplicationscenariosandpotentialimpactofFOKEineducationalcontexts.
Thisobjectiveinvolves(1)demonstratingtheeffectivenessandadvantagesofFOKEthroughcasestudiesin
programmingeducation,homeworkassessment,learningpathplanning,etc.;and(2)discussingthepotential
ofFOKEinenhancingintelligenteducationpracticesandimprovinglearningoutcomes.
By achieving these objectives, FOKE is expected to provide a powerful and flexible framework for designing and
deploying LLM-based intelligent education applications, while addressing the key challenges of personalization,
interactivity,andinterpretability.
2

RunningTitleforHeader
1.4 Contributions
Themaincontributionsofthisworkaresummarizedasfollows:
1. WeproposeFOKE,anovelframeworkthatsynergizespromptengineeringandLLMstoenablepersonalized,
interactive,andexplainableintelligenteducationservices. CentraltoFOKEisahierarchicalknowledgeforest,
whichrepresentsdomainknowledgeasatupleKF =(C,R),whereCdenotesthesetofconceptnodesandR
representsthesetofrelationedges.
2. Wedesignamulti-dimensionaluserprofilingmechanismthatintegratesstructuredattributes,unstructured
behaviors,andtemporaltrajectoriestocomprehensivelymodellearnercharacteristics,whichcanbeformulated
as UP = (A,B,T), where A, B, and T correspond to the attribute, behavior, and trajectory dimensions,
respectively. Basedontheuserprofile,weproposeastructuredpromptrepresentationschemethatincorporates
goal specification, explanatory information, and feedback indicators to generate precise and informative
learningguidance,withtheprompttemplaterepresentedasPT =(G,E,F),whereG,E,andF denotethe
goal,explanation,andfeedbackcomponents,respectively.
3. Wedevelopagraphembedding-basedapproachtofuseknowledgerepresentationandusermodeling,which
learnslow-dimensionalvectorrepresentationsforconceptsandlearners. Theembeddinglearningprocesscan
beformulatedasanoptimizationproblem:
(cid:88)
min L(h ,h ,h ), (1)
h
ci cj r
(ci,cj,r)∈D
where h , h , and h are the embeddings of concepts c , c , and relation r, respectively, and D is the
ci cj r i j
set of concept-relation triples. We designed three educational tasks to showcase the application of the
FOKEframework: interactiveprogrammingeducation,personalizedlearningpathplanning,andintelligent
homeworkassessment. Althoughacomprehensiveevaluationoftheframeworkisyettobecompleted,AI
educationalproductsbasedonFOKEhavealreadybegunexperimentsandoptimizationinactualclassroom
teaching. Bycollectingfeedbackfromstudentsandteachers,wearecontinuouslyimprovingthesystem’s
performanceanduserexperience. However,itisworthnotingthatcurrentlyinthefieldofintelligenteducation,
thereisalackofstandardizedevaluationmethodstocomparedifferentproducts,frameworks,orservices,
mainlyduetothediversityofintelligenteducationsystems,domainspecificity,anddifferencesinuserneeds.
Establishingacomprehensive,fair,andeffectivesetofevaluationcriteriaandmethodsiscrucialforadvancing
thedevelopmentoftheintelligenteducationfield. Inourfuturework,weplantocollaboratewithdomain
expertstoprovidemoreexperienceandsuggestionsfortheevaluationofintelligenteducationsystemswhile
continuingtofocusonimprovingandapplyingtheFOKEframework,strivingtoachievegreaterbreakthroughs
inpersonalization,interactivity,andinterpretability,andcontributemoreinnovativesolutionstothefieldof
intelligenteducation.
1.5 Organization
Theremainderofthispaperisorganizedasfollows. Section2reviewstherelatedworkonintelligenttutoringsystems,
knowledgerepresentation, andpersonalizedlearning. Section3presentstheproposedFOKEframeworkindetail,
including the integration of foundation models and knowledge graphs, the construction of knowledge forests, the
profilingofusers,theengineeringofinteractiveprompts,andthegenerationofexplainablerecommendations. Section
4describesthreerepresentativeapplicationscenariosofFOKE,i.e.,programmingeducation,writingassessment,and
learningpathplanning,andshowcasestheworkflowandexamplesineachscenario. Section5introducestheScholar
Herosystem,aninstantiationofFOKEinreal-worldeducationalsettings,andreportsitsdeployment,evaluation,and
impact. Section6concludesthepaperanddiscussesfutureresearchdirections.
2 RelatedWork
Inthissection,wereviewtherelatedworkonAIineducation,largelanguagemodels,andpromptengineering,which
formthetheoreticalandtechnicalfoundationsofourproposedFOKEframework.
2.1 AIinEducation
TheapplicationofAIineducationhasalonghistory,datingbacktothe1970swhenintelligenttutoringsystems(ITS)
werefirstintroduced[13]. Sincethen,AItechniqueshavebeenextensivelyexploredtoenhancevariousaspectsof
3

RunningTitleforHeader
education, suchaspersonalizedlearning[14], adaptiveassessment[15], andlearninganalytics[16]. Forexample,
Bayesianknowledgetracing[17]wasproposedtomodelstudentknowledgeacquisitionandpredicttheirperformance.
Reinforcementlearning[18]wasemployedtooptimizeinstructionalstrategiesandimprovelearningoutcomes. Deep
learning[19]wasappliedtocapturecomplexlearningpatternsandenableintelligenttutoringinterventions.
Despitethesignificantprogress,existingAI-enhancededucationalsystemsstillfacelimitationsintermsofadaptability,
interactivity,andinterpretability. Mostsystemsrelyonpre-definedrulesormodels,whichmaynoteffectivelycapture
thediversityanddynamicsofreal-worldeducationalscenarios. Moreover,theinteractionbetweenAIsystemsand
learnersisoftenrestrictedtosimplisticforms,suchasmultiple-choicequestionsorshort-answerresponses,lackingthe
flexibilityandnaturalnessofhuman-likecommunication.Furthermore,manyAImodelsareblackboxes,providinglittle
explanatoryinformationtohelplearnersunderstandandtrustthegeneratededucationalfeedback. Theselimitations
highlighttheneedformoreadvancedAItechniquesthatcanenablepersonalized,interactive,andexplainableeducation.
2.2 LargeLanguageModels
Theemergenceoflargelanguagemodels(LLMs)hasrevolutionizedthefieldofnaturallanguageprocessing(NLP)and
openedupnewopportunitiesforAIapplicationsinvariousdomains. LLMs,suchasGPT-4[3],BERT[20],aredeep
neuralnetworkspre-trainedonmassivetextcorpora,whichcanlearnrichlinguisticknowledgeandperformawide
rangeoflanguagetasks. Forexample,GPT-4hasshownimpressivecapabilitiesinlanguagegeneration,translation,
summarization,andquestionanswering,surpassinghumanperformanceinsomecases[3]. BERThasachievedstate-of-
the-artresultsonvariousNLPbenchmarks,suchasGLUE[21]andSQuAD[22],demonstratingitseffectivenessin
languageunderstandingandreasoning.
ThesuccessofLLMscanbeattributedtotheirabilitytocapturetheintricatepatternsandsemanticsofnaturallanguage
fromlarge-scaleunsupervisedlearning. Bytrainingondiversetextdata,LLMscanacquireabroadrangeofknowledge
andskills,whichcanbetransferredtodownstreamtaskswithminimalfine-tuning. Thistransferlearningparadigm
hasgreatlyreducedtheneedfortask-specificlabeleddataandenabledthedevelopmentofgeneralizableandscalable
AIsystems. Moreover,thepre-trainingobjectivesofLLMs,suchasmaskedlanguagemodeling[23]andpermutation
languagemodeling[24],havebeendesignedtoencouragethemodelstolearncontextualrepresentationsandlong-range
dependencies,whichareessentialforunderstandingandgeneratingcoherentandinformativetext.
However,theapplicationofLLMsineducationisstillanemergingareathatrequiresfurtherexploration. Existingwork
hasmainlyfocusedonusingLLMsforautomatedessayscoring[25],questionanswering[26]. Forexample,Xue.Jetal.
[27]fine-tunedBERTonalargedatasetofstudentessaysandtheircorrespondingscores,andachievedstate-of-the-art
performanceonautomatedessayscoring. Abdelghanietal. [28]employedGPT-3togeneratediverseandinformative
answerstostudentquestions,anddemonstrateditspotentialforintelligenttutoringsystems. Whilethesestudieshave
shownpromisingresults,theyhavenotfullyexploitedthepotentialofLLMsforinteractiveandexplainableeducation,
whichisthefocusofourFOKEframework.
2.3 PromptEngineering
Prompt engineering is an emerging technique that aims to elicit desired behaviors from LLMs by designing and
optimizing natural language prompts. Unlike traditional fine-tuning approaches that adapt LLMs to specific tasks
throughend-to-endtraining,promptengineeringkeepstheLLMparametersfixedandinsteadcraftsinputprompts
thatcanguidethemodeltoperformthetargettask. Thisparadigmhasseveraladvantages,suchasreducingtheneed
for task-specific training data, enabling zero-shot or few-shot learning, and preserving the general knowledge and
capabilitiesofLLMs.
The key idea of prompt engineering is to frame the task objective as a natural language prompt that can be easily
understoodandfollowedbyLLMs.Forexample,toperformsentimentclassification,aprompttemplatecanbedesigned
as"Classifythesentimentofthefollowingtext: [Text]. Thesentimentis[Sentiment].",where[Text]istheinputtext
and[Sentiment]isthetargetsentimentlabel. Byfillinginthetemplatewithspecifictextinstancesandfeedingthem
to LLMs, the models can generate the corresponding sentiment labels based on their language understanding and
reasoningabilities.
Inthecontextofeducation,promptengineeringhasthepotentialtoenablepersonalized,interactive,andexplainable
LLM-basedservices. Byincorporatinglearner-specificinformationanddomainknowledgeintoprompts,LLMscan
generateadaptivelearningcontentandprovidecustomizedfeedback. Bydesigningconversation-orientedprompts,
LLMscanengageinmeaningfuldialoguewithlearnersandoffertimelysupportandguidance. Byinjectingexpla-
nationsandjustificationsintoprompts,LLMscanproduceinterpretableandtrustworthyeducationalsuggestionsand
4

RunningTitleforHeader
Figure1: OverviewoftheFOKEFramework
assessments. However,existingworkonpromptengineeringineducationisstilllimited,whichmotivatesustodevelop
theFOKEframeworktofillthisgap.
3 FOKEFramework
Inthissection,wepresenttheproposedFOKEframeworkindetail.Wefirstprovideanoverviewoftheframeworkarchi-
tectureandthenelaborateonitskeycomponents,includingtheknowledgeforest,userprofiling,promptrepresentation,
andgraphembeddingmodules.
3.1 Overview
Theframeworktakesasinputadomainknowledgebase, auserprofiledatabase, andalearningtaskspecification,
andgeneratespersonalized,interactive,andexplainablelearningguidanceandfeedbackthroughtheintegrationof
knowledgerepresentation,usermodeling,promptengineering,andgraphembeddingtechniques.
Specifically,thedomainknowledgebaseisfirstprocessedbytheknowledgeforestmoduletoconstructahierarchical
andstructuredrepresentationofthekeyconceptsandtheirrelationships. Theuserprofiledatabaseisthenencodedby
theuserprofilingmoduletocapturethelearners’attributes,behaviors,andtemporaltrajectoriesinamulti-dimensional
manner. Thelearningtaskspecification,alongwiththeextractedknowledgeanduserrepresentations,isfedintothe
prompt representation module to generate a set of structured prompts that guide the LLM to produce tailored and
informative learning support. Finally, the graph embedding module fuses the knowledge and user representations
throughgraphembeddingtechniques,whichenablespersonalizedrecommendationandadaptiveinstructionbasedon
thesimilarityandrelevanceofconceptsandlearnersintheembeddingspace.
Inthefollowingsubsections,wepresenteachmoduleofFOKEinmoredetailandformulatetheirkeycomponentsand
algorithms.
5

RunningTitleforHeader
3.2 KnowledgeForest
Theknowledgeforestmoduleintroducesanovelandflexibleapproachtorepresentingandorganizingdomainknowledge,
addressingthelimitationsoftraditionalknowledgegraphs. Unlikeknowledgegraphs,whichtypicallyfocusonasingle,
staticrepresentationofknowledge,theknowledgeforestallowsforthedynamicintegrationofmultipleknowledge
trees,providingamoreadaptableandefficientframeworkforknowledgeacquisitionandreasoning.
Formally,wedefineaknowledgeforestasacollectionofknowledgetreesKF ={T ,T ,...,T },whereeachtree
1 2 K
T =(C ,R ,A )representsahierarchicalstructureofconceptsC ,relationsR ,andattributesA . Thekeyidea
k k k k k k k
behindtheknowledgeforestistoenablethedynamicinsertionandremovalofknowledgetreesbasedonthespecific
learningcontextandrequirements,allowingforamoreflexibleandefficientknowledgerepresentationcomparedto
traditionalknowledgegraphs[29].
Theconstructionoftheknowledgeforestfollowsatwo-stageapproach,similartothesingle-treecase. Inthefirststage,
weextractconceptsandtheirattributesfromthedomainknowledgebaseusingnaturallanguageprocessingtechniques,
suchasnamedentityrecognition[30],relationextraction[31],andsemanticrolelabeling[32]. However,insteadof
constructingasingleglobalconceptset,weallowforthecreationofmultipleconceptsets{C }K ,eachcorresponding
k k=1
to a specific knowledge tree. This enables the knowledge forest to capture different aspects or subdomains of the
knowledgebase,providingamorefine-grainedandcontext-specificrepresentation.
Inthesecondstage,weinferthesemanticrelationshipswithineachknowledgetreeT usinggraphminingandlearning
k
algorithms. However,thekeydifferenceliesinthetimecomplexityoftheinferenceprocess. Intraditionalknowledge
graphs,therelationinferencetypicallyinvolvesaglobalsearchovertheentireconceptspace,resultinginahightime
complexityofO(|C|2),where|C|isthetotalnumberofconcepts. Incontrast,theknowledgeforestallowsforalocal
search within each knowledge tree, reducing the time complexity to O( (cid:80)K |C |2), where |C | is the number of
k=1 k k
concepts in the k-th tree [33]. Since |C | is typically much smaller than |C|, the knowledge forest enables a more
k
efficientrelationinferenceprocess.
Moreover,theknowledgeforestintroducesanoveltree-levelinferencemechanismtocapturetherelationshipsbetween
differentknowledgetrees. Leth(L) betherootembeddingofthek-thknowledgetree,obtainedbyaggregatingthe
k
embeddingsofitsconceptsusingapoolingfunction,suchasmeanormaxpooling. Wecantheninferthetree-level
relationshipsbymeasuringthesimilaritybetweentherootembeddings:
(cid:40)
1, ifsim(h(L),h(L))≥τ,
r(T ,T )= i j (2)
i j
0, otherwise,
wheresim(·)isasimilarityfunction,andτ isapredefinedthreshold. Thistree-levelinferenceallowstheknowledge
foresttocapturethehigh-levelrelationshipsbetweendifferentsubdomainsoraspectsofknowledge,providingamore
comprehensiveandstructuredrepresentationofthedomain.
Thedynamicnatureoftheknowledgeforestenablesefficientupdatesandadaptationstonewknowledge. Whenanew
knowledgetreeT isdiscoveredorconstructed,itcanbeseamlesslyinsertedintotheknowledgeforestwithoutthe
K+1
needtoreconstructtheentiregraph. Similarly,whenaknowledgetreebecomesobsoleteorirrelevant,itcanbeeasily
removedfromtheforest. Thisdynamicpropertyallowstheknowledgeforesttoevolveandgrowwiththeexpanding
knowledgebase,makingitamorescalableandmaintainablesolutioncomparedtotraditionalknowledgegraphs.
Theknowledgeforestalsoenablesmoreefficientandtargetedknowledgeretrievalandreasoning. Givenaqueryconcept
c ,wecanfirstidentifythemostrelevantknowledgetreeT basedonthetree-levelsimilarity:
q k∗
k∗ = argmax sim(h ,h(L)), (3)
q k
k∈{1,2,...,K}
whereh istheembeddingofthequeryconcept,andh(L)istherootembeddingofthek-thknowledgetree. Oncethe
q k
relevanttreeisidentified,wecanperformalocalsearchwithinT toretrievethemostrelevantconceptsandrelations,
k∗
avoidingtheneedtosearchtheentireknowledgegraph[29]. Thistargetedretrievalprocesssignificantlyreducesthe
searchspaceandimprovestheefficiencyofknowledgereasoning.
Furthermore,theknowledgeforestenablespersonalizedlearningandrecommendationbyleveragingthehierarchical
structure and tree-level relationships. By maintaining a student’s knowledge state s = (s ,s ,...,s ), where
1 2 K
s ∈ [0,1]representsthestudent’smasterylevelofthek-thknowledgetree,wecanrecommendthemostsuitable
k
knowledgetreeforthestudenttoexplorenext:
6

RunningTitleforHeader
(cid:32) K (cid:33)
(cid:88)
k = argmax r(T ,T )·s ·(1−s ) (4)
next i k i k
k∈{1,2,...,K} i=1
where the first term measures the relevance of the k-th knowledge tree to the student’s current knowledge state,
andthesecondtermensuresthattherecommendedtreeisnotyetfullyexploredbythestudent. Thispersonalized
recommendation strategy helps students navigate the knowledge forest efficiently and effectively, enhancing their
learningexperienceandoutcomes.
The knowledge forest also facilitates the integration of multi-modal learning resources, such as text, images, and
videos,byassociatingthemwiththerelevantconceptsandrelationsintheknowledgetrees[34]. Thismulti-modal
representationenhancestherichnessanddiversityofthelearningcontent, cateringtodifferentlearningstylesand
preferences.
Moreover,theknowledgeforestsupportsexplainablereasoninganddecision-makingbyprovidingatransparentand
interpretablerepresentationoftheknowledgestructure. Thehierarchicalorganizationofconceptsandtheexplicit
modelingofsemanticrelationshipsenablethegenerationofhuman-understandableexplanationsfortherecommended
learningpathsandresources.
Insummary,theknowledgeforestmoduleintroducesadynamic,flexible,andefficientapproachtorepresentingand
organizingdomainknowledge. Byallowingfortheintegrationofmultipleknowledgetreesandenablingtree-level
inference, personalized recommendation, multi-modal learning, and explainable reasoning, the knowledge forest
addresses the limitations of traditional knowledge graphs and provides a more scalable and adaptable solution for
knowledgeacquisitionandreasoningineducationalapplications.
3.3 UserProfiling
Theuserprofilingmoduleaimstocapturethelearners’characteristicsandpreferencesinamulti-dimensionalmanner
toenablepersonalizedandadaptivelearningsupport. WedefineauserprofileasatupleUP =(A,B,T),whereA,B,
andT denotetheattribute,behavior,andtrajectorydimensions,respectively.
TheattributedimensionArepresentsthelearner’sstaticanddemographicinformation,suchasage,gender,education
level, and learning style. The behavior dimension B captures the learner’s dynamic and interactive patterns, such
aslearningactivities,quizperformance,andforumparticipation. ThetrajectorydimensionT modelsthelearner’s
temporalandsequentialcharacteristics,suchaslearningpaths,knowledgestates,andskillacquisition.
Toconstructtheuserprofiles, weproposeamulti-viewrepresentationlearningapproach. Foreachdimension, we
extracttherelevantfeaturesfromtheuserprofiledatabaseandlearnalow-dimensionalvectorrepresentationusing
techniquessuchasmatrixfactorization[35],deeplearning[36],andsequentialmodeling[37]. Wethenfusethelearned
representationsfromdifferentdimensionsusingattentionmechanisms[38]orgraphconvolutionalnetworks[39]to
obtainaunifieduserembedding.
Formally,leta ,b ,andt denotetheattribute,behavior,andtrajectoryembeddingsofuseru,respectively. The
u u u
unifieduserembeddingh canbeobtainedas:
u
h =f(a ,b ,t ;Θ), (5)
u u u u
wheref isthefusionfunctionwithparametersΘ. Forexample,anattention-basedfusionfunctioncanbedefinedas:
α ,α ,α =softmax(w⊤a ,w⊤b ,w⊤t ), (6)
a b t a u b u t u
h =α a +α b +α t , (7)
u a u b u t u
wherew ,w ,andw aretheattentionweightvectorsfortheattribute,behavior,andtrajectorydimensions,respectively.
a b t
3.4 PromptRepresentation
ThepromptrepresentationmoduleaimstogeneratestructuredandinformativepromptsthatcanguidetheLLMto
producepersonalizedandexplainablelearningsupport. WedefineapromptasatuplePT =(G,E,F),whereG,E,
andF denotethegoal,explanation,andfeedbackcomponents,respectively.
ThegoalcomponentG specifiesthelearningobjectiveandtaskrequirements,suchasknowledgeacquisition,problem-
solving,orskillpractice. TheexplanationcomponentE providestherelevantbackgroundinformationandreasoning
process to help learners understand the key concepts and their relationships. The feedback component F offers
personalizedsuggestionsandassessmentsbasedonthelearner’sperformanceandcharacteristics.
7

RunningTitleforHeader
Togeneratethestructuredprompts,weproposeatemplate-basedapproachthatleveragestheknowledgeforestanduser
profilerepresentations. Specifically,foreachlearningtask,wefirstretrievetherelevantconceptsandrelationsfromthe
knowledgeforestbasedonthetaskspecification. Wetheninstantiatetheprompttemplatewiththeretrievedknowledge
andthelearner’sattributesandpreferences. Finally,weoptimizetheprompttemplateandinstantiationusingtechniques
suchasreinforcementlearning[40]toimprovethequalityanddiversityofthegeneratedprompts.
Formally,letKF ⊆KF denotethesubsetoftheknowledgeforestrelevanttotaskt,andh denotetheuserembedding
|             | t                                            |     |     |     |         |           |      | u   |      |
| ----------- | -------------------------------------------- | --- | --- | --- | ------- | --------- | ---- | --- | ---- |
| oflearneru. | Thepromptgenerationprocesscanbeformulatedas: |     |     |     |         |           |      |     |      |
|             |                                              |     |     | G   | =g(KF   | ,h ;Θ     | ),   |     | (8)  |
|             |                                              |     |     |     | t       | t u       | g    |     |      |
|             |                                              |     |     | E   | t =e(KF | t ,h u ;Θ | e ), |     | (9)  |
|             |                                              |     |     | F   | =f(KF   | ,h ;Θ     | ),   |     | (10) |
|             |                                              |     |     |     | t       | t u       | f    |     |      |
|             |                                              |     |     | PT  | =(G     | ,E ,F ),  |      |     | (11) |
|             |                                              |     |     |     | t       | t t t     |      |     |      |
whereg,e,andf arethegenerationfunctionsforthegoal,explanation,andfeedbackcomponents,respectively,with
| parametersΘ | ,Θ ,andΘ | .   |     |     |     |     |     |     |     |
| ----------- | -------- | --- | --- | --- | --- | --- | --- | --- | --- |
|             | g e      | f   |     |     |     |     |     |     |     |
Forexample,atemplateforthegoalcomponentcanbedefinedas:
Acquireknowledgeabout[Concept]anditsrelationsto[RelatedConcepts]tosolveproblems
oftype[ProblemType].
where[Concept],[RelatedConcepts],and[ProblemType]areslotstobefilledwiththeretrievedknowledgeand
userinformation.
Thetemplatecanbeinstantiatedas:
Acquireknowledgeaboutdynamicprogramminganditsrelationstorecursionandmemoizationto
solveproblemsoftypeoptimization,givenyourinterestinalgorithmsandcompetitiveprogramming.
ThequalityofthegeneratedpromptPTtcanbeevaluatedbasedonmetricssuchasrelevance,coherence,anddiversity,
andoptimizedusingreinforcementlearningobjectivessuchas:
E
|     |     |     | maxΘ | g ,Θ e ,Θ | f   |     | [R(PT t )], |     | (12) |
| --- | --- | --- | ---- | --------- | --- | --- | ----------- | --- | ---- |
PTt∼p(·|KFt,hu)
whereR(PT t )istherewardfunctionthatmeasuresthequalityandeffectivenessoftheprompt.
3.5 GraphEmbedding
The graph embedding module aims to learn a unified representation of the knowledge forest and user profiles to
enablepersonalizedrecommendationandadaptiveinstruction. Weproposeagraphembeddingapproachthatlearns
low-dimensionalvectorrepresentationsofconceptsandusersbasedontheirstructuralandsemanticrelationships.
Formally,letG =(V,E)denotethegraphconstructedfromtheknowledgeforestKF anduserprofilesUP
u ,where
V =C∪U isthesetofnodes(conceptsandusers)andE isthesetofedges(relationsandinteractions). Thegoalisto
→Rdthatmapseachnodetoad-dimensionalvector,suchthatthegraphstructureandsemantics
| learnafunctionf | :V  |     |     |     |     |     |     |     |     |
| --------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
arepreservedintheembeddingspace.
Weadoptagraphneuralnetwork(GNN)approachtolearnthenodeembeddings. Ateachlayerl,theembeddingof
nodevisupdatedas:
|     | m(l) =AGG(h(l−1) |     |           |     | h(l) |     | =UPDATE(h(l−1),m(l)), |     |      |
| --- | ---------------- | --- | --------- | --- | ---- | --- | --------------------- | --- | ---- |
|     |                  |     | :u∈N(v)), |     |      |     |                       |     | (13) |
|     | v                |     | u         |     | v    |     |                       | v v |      |
whereh(l)
istheembeddingofnodev atlayerl,N(v)isthesetofneighborsofv,andAGGandUPDATEarethe
v
aggregationandupdatefunctions,respectively.
TheGNNistrainedusingacombinationofsupervisedandunsupervisedobjectives. Forsupervisedlearning,weuse
thenodeembeddingstopredictthenodelabels(e.g.,conceptcategoriesoruserclusters)basedonacross-entropyloss:
|     |     |     |      | (cid:88) |       | (cid:88) |          |     |      |
| --- | --- | --- | ---- | -------- | ----- | -------- | -------- | --- | ---- |
|     |     |     | Ls=− |          | v ∈VL | c=1Cy    | logyˆvc, |     | (14) |
vc
whereVL⊆V isthesetoflabelednodes,C isthenumberofclasses,yvcisthetruelabelofnodevforclassc,and
yˆvcisthepredictedprobability.
8

RunningTitleforHeader
Figure2: ScholarHero: TheApplicationoftheFOKEframework.
Forunsupervisedlearning,weuseacontrastiveloss[41]toenforcethesimilarityofembeddingsforneighboringnodes
andthedissimilarityofembeddingsforrandompairsofnodes:
Lu=− (cid:88) (u,v)∈Elog exp(sim(h u ,hv)) , (15)
(cid:80) v′ ∈Vexp(sim(hu,hv′))
wheresim(·,·)isasimilarityfunctionsuchascosinesimilarityordotproduct.
Theoveralltrainingobjectiveisaweightedcombinationofthesupervisedandunsupervisedlosses:
L=λ L +λ L , (16)
s s u u
whereλ andλ aretheweightingcoefficients.
s u
Aftertraining,thelearnednodeembeddingscanbeusedforvariousdownstreamtasks,suchasconceptrecommendation,
prerequisiteprediction,andlearningpathgeneration,basedonthesimilarityandrelevanceoftheembeddings.
4 ApplicationScenarios
TodemonstratethepracticalvalueandwideapplicabilityoftheproposedFOKEframework,weshowcaseitspotential
inthreerepresentativeeducationalscenarios: interactiveprogrammingeducation,personalizedlearningpathplanning,
andintelligentwritingassessment. Inthissection,wedescribetheworkflowandkeyfunctionalitiesofFOKEineach
scenario,andprovideillustrativeexamplestoshowitseffectivenessingeneratingpersonalizedandexplainablelearning
support.
4.1 InteractiveProgrammingEducation
Programmingeducationisachallengingyetimportantdomainthatrequireslearnerstoacquirecomplexconceptsand
skills. FOKEcanbeappliedtoprovideinteractiveandadaptiveprogrammingtutorialsandfeedbacktoenhancethe
learningexperienceandoutcome.
TheworkflowofFOKEinprogrammingeducationisasfollows:
1. Theknowledgeforestofprogrammingconceptsandskillsisconstructedfromvariouslearningresourcessuch
astextbooks,onlinecourses,andcodingplatforms.
2. Theuserprofileofeachlearnerisbuiltbasedontheirbackground,performance,andlearningactivitiesin
programming.
3. Foreachprogrammingtaskorproject,FOKEgeneratesasetofpersonalizedpromptsthatguidethelearner
throughtheproblem-solvingprocess,suchasunderstandingtherequirements,designingthesolution,and
debuggingthecode.
9

RunningTitleforHeader
4. Thelearnerinteractswiththepromptsandreceivesadaptivefeedbackandsuggestionsbasedontheirinputand
progress.
5. Theknowledgeforestanduserprofileareupdatedbasedonthelearner’sperformanceandfeedbacktoenable
continuousoptimizationandpersonalization.
Forexample,supposealearnerisworkingonaPythonprojecttoimplementarecommendationsystem. FOKEmay
generatethefollowingpromptstoguidethelearner:
Prompt1: Let’sbreakdowntheprojectrequirementsintosmallertasks. Basedonyourexperience
withPythonandmachinelearning,whatarethekeystepsyouwouldtaketobuildarecommendation
system?
Prompt 2: Great insights! To implement the collaborative filtering algorithm, you need to first
constructtheuser-iteminteractionmatrix. Hereareafewexamplesofhowtorepresentthematrix
usingNumPyorPandas. Whichrepresentationdoyouthinkismoresuitableforyourprojectand
why?
Prompt3: Yourcodelooksgoodsofar. Inoticedthatyouusedanestedlooptocalculatetheuser
similarity scores, which may be inefficient for large datasets. Have you considered using matrix
operationsorlibrarieslikeSciPytospeedupthecomputation? Hereareafewsuggestions...
Throughtheinteractiveandexplainableprompts,FOKEcanhelplearnersdeepentheirunderstandingofprogramming
concepts,improvetheirproblem-solvingskills,andreceivetimelyandactionablefeedback. Thepersonalizationand
adaptivityofthepromptsalsocatertothediverseneedsandpreferencesoflearners,makingthelearningprocessmore
engagingandeffective.
4.2 PersonalizedLearningPathPlanning
Learningpathplanningisacriticaltaskineducationthataimstorecommendasequenceofcoursesorlearningactivities
forlearnerstoachievetheirlearninggoals. FOKEcanbeappliedtogeneratepersonalizedlearningpathsbasedonthe
learner’sknowledgestate,learningstyle,andcareeraspiration.
TheapplicationmechanismofFOKEinlearningpathplanningisasfollows:
1. Theknowledgeforestofcourseprerequisites,topics,andlearningoutcomesisconstructedfromthecourse
catalogandsyllabus.
2. Theuserprofileofeachlearnerisbuiltbasedontheiracademicrecord,learningpreferences,andcareergoals.
3. FOKEgeneratesasetofcandidatelearningpathsbasedontheknowledgeforestandthelearner’sprofile,
usingtechniquessuchasprerequisite-basedfiltering,collaborativefiltering,andgoal-basedreasoning.
4. Thecandidatelearningpathsarerankedandrecommendedtothelearnerbasedontheirpredictedperformance,
satisfaction,andalignmentwiththeirgoals.
5. The learner explores and selects the learning paths, and provides feedback and preference to update their
profileandrefinetherecommendation.
Forinstance,consideracollegestudentmajoringincomputersciencewhowantstobecomeadatascientist. FOKE
mayrecommendthefollowinglearningpath:
Step 1: Take the "Introduction to Data Science" course to learn the basics of data manipulation,
visualization,andmachinelearning. Thiscoursealignswellwithyourbackgroundinprogramming
andstatistics,andwillprovideasolidfoundationformoreadvancedtopics.
Step2: Enrollinthe"DatabaseSystems"and"DataMining"coursestodeepenyourknowledgeof
datamanagementandanalysis. Thesecoursesbuildupontheconceptsyoulearnedintheintroductory
courseandarehighlyrelevanttoyourcareergoal.
Step3: Gainpracticalexperiencebyparticipatingindatascienceprojectsorinternships. Basedon
yourperformanceinthepreviouscoursesandyourinterestinhealthcare,werecommendjoiningthe
"MedicalImageAnalysis"projectledbyProf. Smith. Thisprojectwillhelpyouapplyyourskillsto
real-worldproblemsandenhanceyourresume.
By providing personalized and explainable learning path recommendations, FOKE can help learners navigate the
complexcoursespace,discovertheirinterestsandstrengths,andachievetheirlearningandcareergoalsmoreeffectively
andefficiently. Theinteractiveanddynamicnatureoftherecommendationprocessalsoallowslearnerstoactively
shapetheirlearningexperienceandadapttotheirchangingneedsandpreferences.
10

RunningTitleforHeader
4.3 IntelligentHomeworkAssessment
Writing assessment(A Example of Homework Assessment) is a time-consuming and subjective task that requires
teacherstoprovidedetailedandconstructivefeedbacktohelpstudentsimprovetheirwritingskills. FOKEcanbe
appliedtoautomatethewritingassessmentprocessandgenerateobjective,comprehensive,andactionablefeedback.
ThetechnicalworkflowofFOKEinwritingassessmentisasfollows:
1. The knowledge forest of writing aspects, criteria, and examples is constructed from the rubrics, writing
prompts,andexemplaressays.
2. Theuserprofileofeachstudentisbuiltbasedontheirwritinghistory,performance,andfeedback.
3. Foreachwritingassignment, FOKEgeneratesasetofpromptstoelicitthestudent’sself-assessmentand
reflectionontheirwritingstrengthsandweaknesses.
4. Thestudent’sessayisanalyzedusingnaturallanguageprocessingtechniquestoidentifythekeyaspectssuch
ascoherence,argument,andgrammar. Theresultsarecomparedwiththewritingcriteriaandexamplesinthe
knowledgeforesttogenerateanevaluationreport.
5. Theevaluationreportispresentedtothestudentinaninteractiveformat,withdetailedfeedback,suggestions,
andexamplesforeachaspectoftheirwriting. Thestudentcanexplorethefeedback,askquestions,andrevise
theiressayaccordingly.
Forexample,supposeastudentsubmitsanargumentativeessayonthetopicof"socialmediaandmentalhealth". FOKE
maygeneratethefollowingfeedbackreport:
Aspect1: ThesisStatementYourthesisstatementisclearandconcise,statingyourmainargument
thatsocialmediahasnegativeimpactsonmentalhealth. However,youcouldmakeitmorespecific
bymentioningthekeypointsyouwillusetosupportyourargument,suchasaddiction,self-esteem,
andcyberbullying.
Aspect2: EvidenceandExamplesYouprovidedsomerelevantevidencetosupportyourargument,
suchasthestudyshowingthecorrelationbetweensocialmediauseanddepression. However,your
examplesaremostlyanecdotalandlackcredibility. Considerusingmoreresearchfindingsorexpert
opinionstostrengthenyourcase.
Aspect3: CounterargumentandRebuttalYoumentionedacounterargumentthatsocialmedia
canalsohavepositiveeffectsonmentalhealth,suchasconnectingpeopleandprovidingsupport.
However,yourrebuttalisweakanddoesnoteffectivelyaddressthecounterargument. Youcould
arguethatthenegativeeffectsoutweighthepositiveones,orprovideevidencetoshowthelimitations
ofthecounterargument.
Bygeneratingobjective, detailed, andactionablefeedbackonvariousaspectsofwriting, FOKEcanhelpstudents
identifytheirstrengthsandweaknesses,understandthecriteriaandexpectations,andimprovetheirwritingskillsthrough
iterativerevisionandreflection. Theinteractiveandpersonalizednatureofthefeedbackalsofacilitatesstudent-teacher
communicationandcollaboration,makingthewritingassessmentprocessmoreefficient,effective,andengaging.
5 ScholarHero: EmpoweringEducationwithFOKE
ScholarHeroisapioneeringAI-driveneducationalapplicationthatembodiesthecoreprinciplesandinnovationsof
theFOKEframework. ByseamlesslyintegratingadvancedAIagentsandRAG(Retrieval-AugmentedGeneration)
technologies,ScholarHeroaimstorevolutionizethetraditionaleducationlandscapeandbringtangiblebenefitstoevery
student’slearningjourneyandcampuslife.
5.1 SystemArchitectureandWorkflow
ThearchitectureofScholarHeroisbuiltupontheFOKEframework,leveragingitshierarchicalknowledgerepresenta-
tion,multi-dimensionaluserprofiling,andstructuredpromptgeneration.
Thesystemconsistsofthreemaincomponents: 1)KnowledgeBaseConstruction,2)UserProfilingandPersonalization,
and3)InteractiveLearningServices.
IntheKnowledgeBaseConstructionphase,ScholarHeroemploysadvanceddataminingandknowledgeextraction
techniquestobuildacomprehensiveandhierarchicalknowledgebasecoveringawiderangeofeducationaltopicsand
11

RunningTitleforHeader
Figure3: AstudentinteractingwithanAIagentinScholarHero
campus-relatedinformation. Theknowledgebaseiscontinuouslyupdatedandexpandedtoensureitsrelevanceand
accuracy.
TheUserProfilingandPersonalizationcomponentisresponsibleforcreatingandmaintainingmulti-dimensionaluser
profilesbasedonstudents’learningpreferences,academicperformance,interests,andbehavioraldata. Theseprofiles
enableScholarHerotodeliverhighlypersonalizedcontent,recommendations,andservicestailoredtoeachindividual
student’sneeds.
TheInteractiveLearningServicescomponentisthecoreofScholarHero,poweredbyAIagentsandRAGtechnology.
Itprovidesawidearrayofintelligenteducationalservices,includingpersonalizedcourserecommendations,interactive
tutoring, intelligent homework assistance, and AI-generated learning materials. The AI agents engage in natural
language interactions with students, answering their questions, providing explanations, and offering guidance and
supportthroughouttheirlearningprocess.
5.2 UniqueFeaturesandInnovations
ScholarHerodistinguishesitselffromtraditionaleducationalapplicationsthroughitsuniquefeaturesandinnovations,
whicharedeeplyrootedintheFOKEframework:
• PersonalizedLearningPaths: ScholarHerogeneratesdynamicandpersonalizedlearningpathsforeach
student based on their knowledge level, learning style, and goals. The system continuously adapts and
optimizesthesepathsasstudentsprogress,ensuringatrulypersonalizedlearningexperience.
• InteractiveandEngagingLearning:TheAIagentsinScholarHeroprovideinteractiveandengaginglearning
experiencesthroughnaturallanguageconversations,real-timefeedback,andmultimediacontent. Studentscan
askquestions,seekclarifications,andreceiveinstantsupport,fosteringamoreactiveandimmersivelearning
environment. Figure4demonstratesastudentinteractingwithanAIagentinScholarHero.
• IntelligentHomeworkAssistance: ScholarHerooffersintelligenthomeworkassistancebyleveragingthe
knowledgebaseandAIagents. Itcanautomaticallygenerateexplanations,providestep-by-stepguidance,and
offerpersonalizedfeedbackonstudents’assignments,helpingthemtoidentifytheirstrengthsandweaknesses
andimprovetheirunderstandingofthesubjectmatter.
• SeamlessIntegrationwithCampusLife:ScholarHerogoesbeyondacademiclearningbyintegratingvarious
aspectsofcampuslifeintoitsservices. Fromfindingthebestfoodoptionsoncampustomanagingschedules
andextracurricularactivities,ScholarHeroservesasacomprehensiveandintelligentcompanionforstudents
throughouttheiruniversityjourney.
• Continuous Learning and Improvement: Scholar Hero is designed to continuously learn and improve
throughuserinteractionsandfeedback. Thesystememploysadvancedmachinelearningalgorithmstorefine
12

RunningTitleforHeader
Figure4: teachersettinganAIagentinScholarHero.
Figure5: teachersettingtheKnowledgeForestofAIagent.
13

RunningTitleforHeader
itsknowledgebase,userprofiles,andrecommendationmodels,ensuringitsservicesremainaccurate,relevant,
andup-to-date.
5.3 Real-WorldImpactandFutureDirections
ScholarHerohasbeensuccessfullydeployedinseveralpilotuniversities,receivingenthusiasticfeedbackfromstudents
andeducatorsalike. Theapplicationhasdemonstratedsignificantpotentialinenhancingstudentengagement,improving
academicperformance,andpromotingamorepersonalizedandeffectivelearningexperience.
AswecontinuetodevelopandexpandScholarHero,weenvisionafuturewhereAI-driveneducationalapplications
becomeanintegralpartoftheeducationalecosystem. ByleveragingthepoweroftheFOKEframeworkandthelessons
learnedfromScholarHero,weaimtocreatemoreintelligent,adaptive,andinclusiveeducationalsolutionsthatcaterto
thediverseneedsoflearnersworldwide.
Furthermore,weplantoconductextensiveuserstudiesandevaluationstoassessthelong-termimpactofScholarHero
onstudentlearningoutcomes,satisfaction,andoveralleducationalexperience. Theinsightsgainedfromthesestudies
willnotonlyinformthefuturedevelopmentofScholarHerobutalsocontributetothebroaderresearchcommunityin
AI-driveneducation.
Inconclusion,ScholarHerostandsasatestamenttothetransformativepotentialoftheFOKEframeworkinreshaping
the educational landscape. By harnessing the power of AI, we are paving the way for a new era of personalized,
engaging,andeffectivelearningexperiencesthatempowerstudentstothriveintheiracademicandpersonallives.
6 ConclusionandFutureWork
Inthiswork,weproposedanovelframeworknamedFOKEthatintegratesfoundationmodelsandknowledgegraphs
forintelligentandpersonalizededucation. FOKEleveragesthepoweroflargelanguagemodelsanddomainknowledge
togenerateadaptivelearningsupport,suchasinteractiveprompts,personalizedfeedback,andexplainablerecommenda-
tions. Throughacomprehensiveanalysisofthreerepresentativeapplicationscenarios,wedemonstratedthepotentialof
FOKEinenhancingtheeffectiveness,efficiency,andengagementofvariouseducationaltasks,suchasprogramming
education,learningpathplanning,andwritingassessment.
Thekeycontributionsofthisworkinclude:
• Aflexibleandextensibleframeworkthatincorporatesfoundationmodelsandknowledgegraphstocapturethe
complexrelationshipsamonglearningcontent,learnercharacteristics,andpedagogicalstrategies;
• Asetofinnovativetechniques,suchaspromptengineering,knowledgeforestconstruction,andexplainable
recommendation,togeneratepersonalizedandinteractivelearningsupport;
• A systematic analysis of the application scenarios, workflows, and examples of FOKE in three important
educationaldomains,showcasingitswideapplicabilityandpracticalvalue.
Our work explores a promising direction in developing next-generation AI-powered educational systems that can
adapttothediverseneedsandpreferencesoflearners,andprovideintelligentandengaginglearningexperiencesat
scale. ThegenericandmodulardesignofFOKEalsomakesitpotentiallyapplicabletoothereducationalcontexts,
suchascorporatetraining,onlinelearning,andlifelonglearning. Byleveragingtherapidadvancementoffoundation
modelsandknowledgegraphs,FOKEcancontinuouslyevolveandimproveitscapabilitiesinunderstandinglearners,
knowledge,andpedagogy.
AsaconcreteapplicationoftheFOKEframework,wehavedevelopedanintelligenteducationalsystemnamed"Scholar
Hero". ScholarHero is designedto provide personalized andinteractive learningsupport for various subjectsand
domains,withaspecialfocusondatascienceeducation. Currently,ScholarHeroisbeingpilotedinanintroductory
datasciencecourseattheCommunicationUniversityofChina,whereitservesasavirtualteachingassistanttoprovide
adaptivelearningmaterials,formativeassessments,andreal-timefeedbacktostudents.
ThedevelopmentanddeploymentofScholarHeroisanongoingprocess,withcontinuousiterationsandimprovements
basedonthefeedbackanddatacollectedfromthepilotstudy. PreliminaryresultsshowthatScholarHerohasthe
potentialtoimprovestudents’learningoutcomes,engagement,andsatisfaction,byprovidingthemwithtailoredand
timelysupportthatcaterstotheirindividualneedsandprogress. Weplantoconductmorerigorousandlarge-scale
evaluationsofScholarHerointhefuture,andexploreitsapplicationinothereducationalsettingsanddomains.
Despitethepromisingprogress,ourworkstillhasseverallimitationsandchallenges.First,theknowledgeforestanduser
profilesinScholarHeroarecurrentlyconstructedbasedonlimitedanddomain-specificdata,whichmaynotcapturethe
14

RunningTitleforHeader
fullcomplexityanddiversityoflearnersandsubjects. Second,thepromptengineeringandrecommendationtechniques
usedinScholarHeroarestillrudimentaryandneedtobefurtheroptimizedforefficiencyandeffectiveness. Third,the
long-termimpactandgeneralizabilityofScholarHeroneedtobevalidatedthroughlongitudinalandcross-domain
studies.
Therefore,weplantopursuethefollowingdirectionsinourfuturework:
• ExpandtheknowledgeforestanduserprofilingcapabilitiesofScholarHerobyincorporatingmorediverse
andlarge-scaleeducationaldata,suchaslearningresources,assessments,andstudentrecords;
• Developmoreadvancedandscalabletechniquesforpromptengineeringandrecommendation,leveragingthe
state-of-the-artresearchinnaturallanguageprocessing,knowledgerepresentation,andrecommendersystems;
• Conductmorecomprehensiveandlong-termevaluationsofScholarHero,bothinthecurrentpilotstudyandin
othereducationalcontexts,toassessitseffectiveness,usability,andgeneralizability;
• InvestigatethepedagogicalandethicalimplicationsofusingAI-powerededucationalsystemslikeScholar
Hero,suchasthealignmentwithlearningtheories,thefairnessandtransparencyofthegeneratedsupport,and
theimpactonteacher-studentrelationships.
WebelievethatourworkontheFOKEframeworkanditsapplicationinScholarHerorepresentsanimportantstep
towards realizing the full potential of AI in education. By integrating foundation models, knowledge graphs, and
educationaldomainknowledge,wecancreateintelligentandpersonalizedlearningexperiencesthatcanbenefitlearners
ofdiversebackgroundsandabilities. Wehopethatourworkcaninspiremoreresearchanddevelopmenteffortsinthis
direction,andcontributetotheadvancementofAI-powerededucation.
References
[1] Pratama,M.P.,Sampelolo,R.,&Lura,H.(2023).Revolutionizingeducation: harnessingthepowerofartificial
intelligence for personalized learning. Klasikal: Journal of Education, Language Teaching and Science, 5(2),
350-357.
[2] Hashim,S.,Omar,M.K.,AbJalil,H.,&Sharef,N.M.(2022).Trendsontechnologiesandartificialintelligencein
educationforpersonalizedlearning: systematicliterature.JournalofAcademicResearchinProgressiveEducation
andDevelopment,12(1),884-903.
[3] Achiam,J.,Adler,S.,Agarwal,S.,Ahmad,L.,Akkaya,I.,Aleman,F.L.,...&McGrew,B.(2023).Gpt-4technical
report.arXivpreprintarXiv:2303.08774.
[4] Anil,R.,Dai,A.M.,Firat,O.,Johnson,M.,Lepikhin,D.,Passos,A.,...&Wu,Y.(2023).Palm2technicalreport.
arXivpreprintarXiv:2305.10403.
[5] Kasneci, E., Seßler, K., Küchemann, S., Bannert, M., Dementieva, D., Fischer, F., ... & Kasneci, G. (2023).
ChatGPT for good? On opportunities and challenges of large language models for education. Learning and
individualdifferences,103,102274.
[6] Qu,K.,&Wu,X.(2024).ChatGPTasaCALLtoolinlanguageeducation: Astudyofhedonicmotivationadoption
modelsinEnglishlearningenvironments.EducationandInformationTechnologies,1-33.
[7] Tu,X.,Zou,J.,Su,W.J.,&Zhang,L.(2023).Whatshoulddatascienceeducationdowithlargelanguagemodels.
arXivpreprintarXiv:2307.02792.
[8] Myers,D.,Mohawesh,R.,Chellaboina,V.I.,Sathvik,A.L.,Venkatesh,P.,Ho,Y.H.,...&Jararweh,Y.(2023).
Foundation and large language models: fundamentals, challenges, opportunities, and social impacts. Cluster
Computing,1-26.
[9] White,J.,Fu,Q.,Hays,S.,Sandborn,M.,Olea,C.,Gilbert,H.,...&Schmidt,D.C.(2023).Apromptpattern
catalogtoenhancepromptengineeringwithchatgpt.arXivpreprintarXiv:2302.11382.
[10] Shao, Z., Yu, Z., Wang, M., & Yu, J. (2023). Prompting large language models with answer heuristics for
knowledge-basedvisualquestionanswering.InProceedingsoftheIEEE/CVFConferenceonComputerVisionand
PatternRecognition(pp.14974-14983).
[11] Mayer,C.W.,Ludwig,S.,&Brandt,S.(2023).Prompttextclassificationswithtransformermodels!Anexemplary
introductiontoprompt-basedlearningwithlargelanguagemodels.JournalofResearchonTechnologyinEducation,
55(1),125-141.
15

RunningTitleforHeader
[12] Ahmed, T., Pai, K. S., Devanbu, P., & Barr, E. T. (2024, March). Automatic semantic augmentation of lan-
guagemodelprompts(forcodesummarization).In2024IEEE/ACM46thInternationalConferenceonSoftware
Engineering(ICSE)(pp.1004-1004).IEEEComputerSociety.
[13] Carbonell,J.R.(1970).AIinCAI:Anartificial-intelligenceapproachtocomputer-assistedinstruction.IEEE
transactionsonman-machinesystems,11(4),190-202.
[14] Bernacki,M.L.,Greene,M.J.,&Lobczowski,N.G.(2021).Asystematicreviewofresearchonpersonalized
learning: Personalizedbywhom,towhat,how,andforwhatpurpose(s)?.EducationalPsychologyReview,33(4),
1675-1715.
[15] Vie,J.J.,Popineau,F.,Bruillard,É.,&Bourda,Y.(2017).Areviewofrecentadvancesinadaptiveassessment.
Learning analytics: Fundaments, applications, and trends: A view of the current state of the art to enhance
e-learning,113-142.
[16] Banihashem,S.K.,Aliabadi,K.,PourroostaeiArdakani,S.,Delaver,A.,&NiliAhmadabadi,M.(2018).Learning
analytics: Asystematicliteraturereview.InterdisciplinaryJournalofVirtualLearninginMedicalSciences,9(2).
[17] Yudelson,M.V.,Koedinger,K.R.,&Gordon,G.J.(2013).Individualizedbayesianknowledgetracingmodels.In
ArtificialIntelligenceinEducation: 16thInternationalConference,AIED2013,Memphis,TN,USA,July9-13,
2013.Proceedings16(pp.171-180).SpringerBerlinHeidelberg.
[18] Singla,A.,Rafferty,A.N.,Radanovic,G.,&Heffernan,N.T.(2021).Reinforcementlearningforeducation:
Opportunitiesandchallenges.arXivpreprintarXiv:2107.08828.
[19] Warburton,K.(2003).Deeplearningandeducationforsustainability.InternationalJournalofSustainabilityin
HigherEducation,4(1),44-56.
[20] Devlin,J.,Chang,M.W.,Lee,K.,&Toutanova,K.(2018).Bert: Pre-trainingofdeepbidirectionaltransformers
forlanguageunderstanding.arXivpreprintarXiv:1810.04805.
[21] Wang,A.,Singh,A.,Michael,J.,Hill,F.,Levy,O.,&Bowman,S.R.(2018).GLUE:Amulti-taskbenchmark
andanalysisplatformfornaturallanguageunderstanding.arXivpreprintarXiv:1804.07461.
[22] Rajpurkar,P.,Zhang,J.,Lopyrev,K.,&Liang,P.(2016).Squad: 100,000+questionsformachinecomprehension
oftext.arXivpreprintarXiv:1606.05250.
[23] Salazar,J.,Liang,D.,Nguyen,T.Q.,&Kirchhoff,K.(2019).Maskedlanguagemodelscoring.arXivpreprint
arXiv:1910.14659.
[24] Cui,Y.,Yang,Z.,&Liu,T.(2022).PERT:pre-trainingBERTwithpermutedlanguagemodel.arXivpreprint
arXiv:2203.06906.
[25] Rodriguez,P.U.,Jafari,A.,&Ormerod,C.M.(2019).Languagemodelsandautomatedessayscoring.arXiv
preprintarXiv:1909.09482.
[26] Yasunaga, M., Ren, H., Bosselut, A., Liang, P., & Leskovec, J. (2021). QA-GNN: Reasoning with language
modelsandknowledgegraphsforquestionanswering.arXivpreprintarXiv:2104.06378.
[27] Xue,J.,Tang,X.,&Zheng,L.(2021).AhierarchicalBERT-basedtransferlearningapproachformulti-dimensional
essayscoring.IeeeAccess,9,125403-125415.
[28] Abdelghani,R.,Wang,Y.H.,Yuan,X.,Wang,T.,Lucas,P.,Sauzéon,H.,&Oudeyer,P.Y.(2023).Gpt-3-driven
pedagogicalagentstotrainchildren’scuriousquestion-askingskills.InternationalJournalofArtificialIntelligence
inEducation,1-36.
[29] Ji,S.,Pan,S.,Cambria,E.,Marttinen,P.,&Philip,S.Y.(2021).Asurveyonknowledgegraphs: Representation,
acquisition,andapplications.IEEEtransactionsonneuralnetworksandlearningsystems,33(2),494-514.
[30] Li,J.,Sun,A.,Han,J.,&Li,C.(2020).Asurveyondeeplearningfornamedentityrecognition.IEEEtransactions
onknowledgeanddataengineering,34(1),50-70.
[31] Pawar, S., Palshikar, G. K., & Bhattacharyya, P. (2017). Relation extraction: A survey. arXiv preprint
arXiv:1712.05191.
[32] Màrquez,L.,Carreras,X.,Litkowski,K.C.,&Stevenson,S.(2008).Semanticrolelabeling: anintroductionto
thespecialissue.Computationallinguistics,34(2),145-159.
[33] Jiang, C., Coenen, F., &Zito, M.(2013).Asurveyoffrequentsubgraphminingalgorithms.TheKnowledge
EngineeringReview,28(1),75-105.
[34] Yager,R.R.(2006).Knowledgetreesandprotoformsinquestion-answeringsystems.JournaloftheAmerican
SocietyforInformationScienceandTechnology,57(4),550-563.
16

RunningTitleforHeader
[35] Mnih, A., & Salakhutdinov, R. R. (2007). Probabilistic matrix factorization. Advances in neural information
processingsystems,20.
[36] Cheng,H.T.,Koc,L.,Harmsen,J.,Shaked,T.,Chandra,T.,Aradhye,H.,...&Shah,H.(2016,September).Wide
&deeplearningforrecommendersystems.InProceedingsofthe1stworkshopondeeplearningforrecommender
systems(pp.7-10).
[37] Kang, W. C., & McAuley, J. (2018, November). Self-attentive sequential recommendation. In 2018 IEEE
internationalconferenceondatamining(ICDM)(pp.197-206).IEEE.
[38] Lu, J., Chen, L., Meng, K., Wang, F., Xiang, J., Chen, N., ... & Li, B. (2019). Identifying user profile by
incorporatingself-attentionmechanismbasedonCSDNdataset.DataIntelligence,1(2),160-175.
[39] Yu,J.,Yin,H.,Li,J.,Gao,M.,Huang,Z.,&Cui,L.(2020).Enhancingsocialrecommendationwithadversarial
graphconvolutionalnetworks.IEEETransactionsonknowledgeanddataengineering,34(8),3727-3739.
[40] Deng,M.,Wang,J.,Hsieh,C.P.,Wang,Y.,Guo,H.,Shu,T.,...&Hu,Z.(2022).Rlprompt: Optimizingdiscrete
textpromptswithreinforcementlearning.arXivpreprintarXiv:2205.12548.
[41] Wang,F.,&Liu,H.(2021).Understandingthebehaviourofcontrastiveloss.InProceedingsoftheIEEE/CVF
conferenceoncomputervisionandpatternrecognition(pp.2495-2504).
17