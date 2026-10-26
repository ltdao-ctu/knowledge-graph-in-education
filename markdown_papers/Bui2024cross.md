---
title: "Bui2024cross"
source: "Bui2024cross.pdf"
source_sha256: "7ff07484900b9b778f12e3a0eef3addfc93ef541ccb3e6392e5aa4c3b82f859c"
converted_at: "2026-10-26T07:04:55.157811+00:00"
markitdown_version: "0.1.9"
---
Cross-Data Knowledge Graph Construction for LLM-enabled
Educational Question-Answering System:
A Case Study at HCMUT
TuanBui∗ OanhTran PhuongNguyen
tuanbc88@hcmut.edu.vn oanh.tranotsc1123@hcmut.edu.vn phuong.nguyenvoid@hcmut.edu.vn
HoChiMinhCityUniversityof HoChiMinhCityUniversityof HoChiMinhCityUniversityof
Technology(HCMUT) Technology(HCMUT) Technology(HCMUT)
HoChiMinhCity,VietNam HoChiMinhCity,VietNam HoChiMinhCity,VietNam
BaoHo LongNguyen ThangBui†
bao.ho64qubit@hcmut.edu.vn long.nguyencse2023@hcmut.edu.vn bhthang@hcmut.edu.vn
HoChiMinhCityUniversityof HoChiMinhCityUniversityof HoChiMinhCityUniversityof
Technology(HCMUT) Technology(HCMUT) Technology(HCMUT)
HoChiMinhCity,VietNam HoChiMinhCity,VietNam HoChiMinhCity,VietNam
ThoQuan†
qttho@hcmut.edu.vn
HoChiMinhCityUniversityof
Technology(HCMUT)
HoChiMinhCity,VietNam
ABSTRACT Graphfrommultipledatasourcesanddiscussessomeinitialappli-
Intoday’srapidlyevolvinglandscapeofArtificialIntelligence,large cations(experimentaltrials)ofKGinconjunctionwithLLMsfor
languagemodels(LLMs)haveemergedasavibrantresearchtopic. question-answeringtasks.
LLMsfindapplicationsinvariousfieldsandcontributesignificantly.
Despitetheirpowerfullanguagecapabilities,similartopre-trained CCSCONCEPTS
languagemodels(PLMs),LLMsstillfacechallengesinremembering •Computingmethodologies→Informationextraction;On-
events,incorporatingnewinformation,andaddressingdomain- tologyengineering;•Informationsystems→Ontologies;Ques-
specificissuesorhallucinations.Toovercometheselimitations, tionanswering;Clusteringandclassification.
researchershaveproposedRetrieval-AugmentedGeneration(RAG)
techniques,someothershaveproposedtheintegrationofLLMs KEYWORDS
withKnowledgeGraphs(KGs)toprovidefactualcontext,thereby OpenIntentDiscovery,KnowledgeGraph,Largelanguagemodel,
improvingperformanceanddeliveringmoreaccuratefeedbackto Education,Question-AnsweringSystem
userqueries.
Educationplaysacrucialroleinhumandevelopmentandprogress. ACMReferenceFormat:
TuanBui,OanhTran,PhuongNguyen,BaoHo,LongNguyen,ThangBui,
Withthetechnologytransformation,traditionaleducationisbeing
andThoQuan.2024.Cross-DataKnowledgeGraphConstructionforLLM-
replacedbydigitalorblendededucation.Therefore,educational
enabledEducationalQuestion-AnsweringSystem:ACaseStudyatHCMUT.
data in the digital environment is increasing day by day. Data InProceedingsofACMConference(Conference’17).ACM,NewYork,NY,
inhighereducationinstitutionsarediverse,comprisingvarious USA,8pages.https://doi.org/10.1145/nnnnnnn.nnnnnnn
sourcessuchasunstructured/structuredtext,relationaldatabases,
web/app-basedAPIaccess,etc.ConstructingaKnowledgeGraph 1 INTRODUCTION
from these cross-data sources is not a simple task. This article
ALargeLanguageModel(LLM)isalanguagemodeltrainedona
proposesamethodforautomaticallyconstructingaKnowledge
considerablylargesizecorpus.Nowadays,LLMsattractmuchatten-
tionfromvariouscommunitiesduetotheircapacitytoaccomplish
Permissiontomakedigitalorhardcopiesofallorpartofthisworkforpersonalor versatilelanguagegenerationandcomprehension.NotableLLM
classroomuseisgrantedwithoutfeeprovidedthatcopiesarenotmadeordistributed
forprofitorcommercialadvantageandthatcopiesbearthisnoticeandthefullcitation modelsreportedtothepublicincludeOpenAI’sGPT[23],Google’s
onthefirstpage.CopyrightsforcomponentsofthisworkownedbyothersthanACM BART[15],LLaMa[26].Toachieveabroadspectrumofgeneral
mustbehonored.Abstractingwithcreditispermitted.Tocopyotherwise,orrepublish,
knowledge[22]andrefinetheirlanguageability[30],state-of-the-
topostonserversortoredistributetolists,requirespriorspecificpermissionand/ora
fee.Requestpermissionsfrompermissions@acm.org. artLLMsnowadaysaretrainedonamassivecorpusoftextualdata.
Conference’17,July2017,Washington,DC,USA However,anLLM’scompletionmightcontain"hallucinations"[11]
©2024AssociationforComputingMachinery. becauseoflimitedaccesstoinformationthatisasup-to-date,propri-
ACMISBN978-x-xxxx-xxxx-x/YY/MM...$15.00
https://doi.org/10.1145/nnnnnnn.nnnnnnn etary,ordomain-specificashumans.Toaddressthisissueandother
4202
peS
7
]LC.sc[
2v69290.4042:viXra

Conference’17,July2017,Washington,DC,USA TuanBui,etal.
limitations,somehybridmodelshaveshownprominentresultsby anopen-worldsetting.Creatinglabeleddatasetsforeverypotential
combiningparametricmemorywithnon-parametricmemory[13]. intentbecomesimpractical,especiallywhendealingwithawide
Sincetheirknowledgebasescanbedirectlyrevisedandexpanded, rangeofdomainsandapplications.Thisscarcityofannotatedexam-
andretrievedknowledgecanbeinspectedandinterpreted.This plesfornovelintentsmakesitchallengingformodelstogeneralize
technique,whichreceivedalotoftractionafterthepublication effectivelyandaccuratelyidentifyopenintents.Inrecentyears,
ofthefamousFacebookresearchpaper[16],iswell-knownand therehasbeenanincreasedinterestindetermininguserintent
coinedasRetrieval-AugmentedGeneration(RAG). frombothwrittenandspokenlanguage,withafocusonmodeling
However,inmostreal-worlddomainssuchaseducation,the andcomprehendinginteractions.Recentstudies,suchasamethod
data/informationoftenoriginatefromvariousdepartmentsand employing a bidirectional LSTM and CRF for detecting user in-
facultieswithinaninstitution,resultingindiversedatasources tentefficiently[27],anunsupervisedtwo-stageapproachaimed
withdifferentnaturessuchasstructuredtext,unstructuredtext, atdiscoveringintentsandgeneratingmeaningfulintentlabelsau-
databases,images,oraccessthroughAPImechanismsfromexisting tomaticallyfromunlabeledutterances[28],andamethodmining
web/app-basedsystems.Forinstance,atHoChiMinhCityUniver- unlabeledutterancedatatouncovercommonintents[17].These
sity of Technology (HCMUT) 1, unstructured data originate from studiescollectivelyhighlightthesignificanceofrobustapproaches
legaldocuments,frequentlyaskedquestions(FAQs)fromstudent forunderstandinguserintent,pavingthewayforenhanceddia-
supportsystemsBKSI2(HelpDeskSystem),newsfromthewebsite, loguesystemsandvirtualassistants.Openintentshasbeenstudied
datafromdatabases,andinformationretrievedfromAPI-enabled infieldssuchasCustomerCareinbusinesses[17,28]andHealth-
systemsliketeachingmanagementsystemsLMS3.Duetothecross- carefacilities[19];however,intherealmofeducation,particularly
datanature,KnowledgeGraphs(KGs)[9]serveasasuitablenon- inStudentCare,itremainsrelativelyunexplored.
parametricmemoryformalismforknowledgerepresentationinthe
educationalenvironment,allowingtheeffectivedeploymentofa
RAGsysteminthiscontext.However,constructingaKnowledge
Graphfrommultipledatasources,notspecificallydesignedtobe
interoperable,isnotatrivialtask,inparticularwhenoneneeds
2.2 KnowledgeGraphinEducationDomain
to deal with open intents [ref] commonly arising during casual
KnowledgeGraphs(KGs)haveevolvedasaneffectivewaytorep-
conversationsbetweenstudentsandtheuniversitystaffs.Hence,
resentknowledge.KGspresentastructuredandintegratedrep-
tothebestofourknowledge,therehasnotbeenabest-practice
resentationofconcepts,relationships,andattributeswithinado-
applicationofRAGfromKGforLLMsinpracticalscenarios.
main. There have been many studies on Educational KGs such
Inthispaper,weaimtopioneeraKG-basedRAGapproachforan
asknowledgegraphformathematics[4],ontologymodelinguni-
EducationalQuestion-Answeringsystem.Weproposeaframework
versityteachingprogramsandstudentprofiles(EducOnto)[10],
forthecross-dataknowledgegraphconstructionintheeducational
knowledgeschemaforuniversityteaching[24],andknowledge
domain,whichiscurrentlyimplementedatHCMUTandleverages
graphstoidentifylabormarketneeds(educationandemployment)
theVietnameselanguage.Thisframeworkisappliedasapilotin
[5].Notably,researchonKGsfortheVietnameseeducationalarea
aLanguageModel(LLM)-basedsystem.Ourcontributionsareof
issparse.HuongandPhuc[25]introducedaframeworkforextract-
three-fold:(i)Weintroducethetechniqueofintentalentitydiscov-
ingtriples(subject-predicate-objectrelationships)fromVietnamese.
eryforunstructuredtextinVietnameseFAQconversations;(ii)we
However,theirtechniquehaslimitationsinhandlingcomplexsen-
presenttheembedding-basedcross-dataforrelationdiscoveryon
tencesandisappliedtothetravelarea.
educationKGconstruction;and(iii)weconductreal-worldexperi-
ments,specifically,LLM-enabledKG-basedQuestion-Answeringat
HCMUTusingRAGwiththeconstructededucationalKG.
2 RELATEDWORK
2.3 KG-augmentedLLMs
2.1 OpenIntentDiscovery
OnemajorhurdleforLLMsistheiroccasionalstrugglewithfactual
ThetaskofOpenIntentDiscovery[3]presentsseveralchallenges
accuracyandhallucinations.ThisiswhereKGscomein.KGsoffer
anddifficultiesinthefieldofNaturalLanguageUnderstandingand
astructuredrepresentationofknowledge,encodingentitiesand
dialoguesystems.Onesignificantchallengeistheinherentambi-
theirrelationshipsinamachine-readableformat.KG-augmented
guityandvariabilityinuserexpressions.Unliketraditionalintent
LLMsaimtobridgethisgapbyleveragingthestrengthsofboth
recognition,whereapredefinedsetofcategoriesisusedforclassifi-
approaches.IfthegeneratedinformationfromLLMsalignswith
cation,openintentdiscoveryinvolvesidentifyinguserintentsthat
the"groundtruth"representedbytheKGs,itcanbeconsidered
maynothavebeenencounteredduringthetrainingphase.This
factuallyaccurateandnon-hallucinatory.Thisenhancingmethod
introducesalevelofuncertaintyandunpredictability,asuserscan
involvesrefiningtheinferenceprocessofLLMs[1],optimizing
expresstheirintentsindiverseandunanticipatedways.Another
learning mechanisms [14] , and establishing a result validation
challengeisthelackofsufficientlabeleddatafortrainingmodelsin
mechanism[12].Significantprogresshasbeenmadethroughthese
studies,highlightingtheimportanceofcontinuousinnovationand
1https://hcmut.edu.vn
supporting the advancement of more advanced KG-augmented
2https://mybk.hcmut.edu.vn/bksi/public/vi/
3https://lms.hcmut.edu.vn/ LLMs.

Cross-DataKnowledgeGraphConstructionforLLM-enabledEducationalQuestion-AnsweringSystem:ACaseStudyatHCMUTConference’17,July2017,Washington,DC,USA
3 TOWARDSCROSS-DATAKNOWLEDGE policies/regulations,andcourseinformation.Knowledgeex-
GRAPHCONSTRUCTIONFOR tractablefromthissourceincludesguidancedocuments,de-
tailedcurricula,andprogramdescriptionsofferedbyHC-
LLM-ENABLEDEDUCATIONAL
MUT,alongwithotherentitiessuchasorganizations(uni-
QUESTION-ANSWERINGSYSTEM
versity,faculty,department),locations(addressnumber,city,
In this section, we delve into the methodological approach em- district),andpersonnames(students,lecturers,staffs).
ployedinourresearchtoextractvaluableinsightsfromamulti-
• LearningManagementSystem(LMS)andothersupportingsys-
sourceeducationaldataenvironmentforKGconstruction,served tems:Thesesystemshelpstudentskeeptrackoftheircourse-
asthefoundationofanLLM-enablededucationalQAsystem.We workthroughouttheschoolyear.Knowledgeextractable
beginbydiscussingthenatureofthedatasourcesintheuniversity fromthissourceincludescourses,keywords,disciplineter-
environmentofHCMUTandhowtheycontributetoacomprehen- minology,disciplinetheory,books,documents,journals,and
siveunderstandingoftheeducationalecosystem.Wethenintroduce courseparticipants(students,lecturers,teachingassistants).
theE-OEDFramework(EducationalOpenEntityDiscovery),aro-
bustmethodologydesignedtoexploreintentsusingunsupervised
3.2 TheE-OEDFramework
learning methods. This framework is particularly adept at han-
dlingchallengessuchasoverlappingentities,openintents,and
datafusionfrommultiplesources.Lastly,wepresentourmethod
forRelationDiscovery,allowingustoexplorerelationshipsamong Academicaffairsoffice Transcriptinquiry
differenttypesofentitiesandconstructaKGrepresentingtheedu- Studentstatus Classtransfer
cationdomain. Coursedeferral
Student Class
Tuitionpolicy Gradecomplaint
3.1 Multi-sourceeducationaldataatHCMUT Tuitionfee Lecturer Course Subject
InthedynamiclandscapeofauniversityenvironmentlikeHCMUT,
Coursedrop Semester Subjectinformation
datastreamsfromamyriadofsources,formingacomplexmulti- Coursewithdrawal Courseregistration
sourceecosystem.Thisdiverseandinterconnectedwebofentities Department
providesacomprehensivepictureoftheuniversityecosystem,en- Coursewithdrawalpolicy
Courseregistrationschedule Courseregistrationpolicy
ablingadeeperunderstandingofuserneeds,educationalprocesses,
andtheoveralluniversityenvironment.includesthefollowingdata Faculty
sources.
Figure1presentsacross-dataenvironmentatHCMUT,which Fig.2:Entitytypeineducationdomain
includesthefollowingdatasources.
Figure2depictstheintricatetaskofextractingrelationships
withintheeducationaldomainandexploringintents.Forinstance,
UniversityResources acertainStudentmayhavehisStudentstatus,whichismanagedby
FAQ&HelpDeskSystem Portals/Websites LMS Othersystems Academicaffairsoffice.ThisstudentalsobelongstoacertainFaculty
andisenrollinginvariousinstancesofClass.Thestudentcanalso
leveragesomeacademicservicewhennecessarysuchasCourse
droporTranscriptinquiry.Thegraphshowcasesthecomplexity
Intentionentity Academicentity Policy/Document
ofmappingintentstoacademicentities,illustratingthenuanced
EducationalOpenEntityDiscovery connectionsthatexistwithinthisdomain.Thiscomplexityunder-
scoresthenecessityforrobustmethodologiestoaccuratelydecipher
andanalyzesuchrelationships.Themostchallengingtasktowards
HCMUTLLM-basedVirtualAssistant suchaKGconstructionisperhapseducationalopenentitydiscovery.
Thesechallengesincludehandlingoverlappingentities,exploring
openintents(whichlackextensiveresearchcomparedtoclassified
Fig.1:Multi-sourceeducationaldataatHCMUT
intents),andfusingdatafrommultiplesources.Moreover,theViet-
nameselanguagepresentsadditionalhurdlesduetoitsstatusasa
low-resourcelanguage.Furthermore,withineducationalenviron-
• FAQandHelpDeskSystem:InHCMUT,thereisanonline ments,theintentofconversationsaredynamicratherthanfixed,
interactivesystemallowingstudentstoraisetheirconcerns andopenedratherthanlimited.Consequently,theidentificationof
arisingduringtheirstudyandfeedbackreceivedfromaca- openentitiesiscrucialintheeducationalsphere.TheE-OEDFrame-
demicstaff.Knowledgeextractablefromthissourceincludes work(EducationalOpenEntityDiscovery),representedbyFigure3,
openintents,events,studentissues,universityservices,the aimstodiscoverintentsfromFAQdata.Thisframeworkincludes
softwaresystemoftheuniversity. threeprocessingmodulesknownasDataPreprocessing,Semantic
• AcademicPortals/Websites:Theseareallthewebsitesthat Clustering,andAutomaticClusterLabeling,eachofwhichplaysa
HCMUTupdatesfrequentlyforacademicnews,university crucialroleintheintentdiscoveryprocess.

Conference’17,July2017,Washington,DC,USA TuanBui,etal.
studyconsultation subjectschedule exampostponement
Input DataPreprocessing gradeadjustment
FAQData Sentencetokenization gradereview studyplan timetablecheck make-upexamarrangement
Uniquesentenceacquisition gradechecking gradeinquiry studymaterials overlappingschedul s e tudyschedulech c e o c u k rseregistrationdeadline
Shortsentenceremoval classopening
classchangesupport classsizeincrease courseregistration subjectregistration
coursewithdrawal
SemanticClustering classtransfersuppor n t ewclassopening coursedrop classregistration
SentenceEmbedding(SimCSE) classadditionsupport coursewithdrawalregistration
DimensionReduction(UMAP)
Sentence-densityclustering(HDBSCAN) Fig.4:Listofsomediscoveredintents
AutomaticClusterLabelling
Wordsegmentation WeuseSentence-BERTtoembedintententitiesandpolicyenti-
POSandDependencyTagging
Output ties.Oncetheembeddingsaregenerated,wemapdifferenttypes
ExtractedIntentions Rule-basedtagextraction
ofentitiesbymeasuringsimilarityorproximitybetweenentity
embeddingsinmultidimensionalspace.
OpenEntityDiscoveryFramework
Aftergettingmappingbetweenentitiesusingembedding,weuse
Fig.3:EducationalOpenEntityDiscoveryFramework tf_idftorerankandgivehigherscorestopoliciesthathavesimilar
keywordswiththeintents.[8],weidentifyimplicitconnections
DataPreprocessingInthisstep,wesplitparagraphstoalist betweenentities.Thisanalysisenablesustouncovermeaningful
ofsinglesentences,filteringoutthenoise,etc.Thisinitialfiltering associationsanddependenciesthatmightnotbereadilyapparent
helpsusfocusonthemeatofthetext. from raw data alone. Figure 5 illustrates the approach of using
SemanticClusteringToobtainsentenceembedding,weem- Embedding-based methods for relation discovery. Based on the
ploySimCSE[6]asourchosenembeddingmodel.Themodelweuse discoveredrelationships,weconstructaKnowledgeGraph(KG)
adherestotheSimCSEframeworkandhasbeendevelopedutilizing representingtheeducationdomain.Eachentitytypeisdepictedas
therenownedpre-trainedPhoBERT[20]base.Beforeapplyingthe anodeinthegraph,andrelationshipsbetweenentitiesaredepicted
embeddingstotheclusteringalgorithm,itisessentialtoconduct asedges.TheKGoffersastructuredrepresentationoftheseman-
dimensionreductionmethods.Thisprecautionarystepistakento ticlandscapewithintheeducationdomain,facilitatingefficient
addressthe"curseofdimensionality,"whichcanadverselyimpact traversal,queryprocessing,andinferencetasks.
theaccuracyofclusteringalgorithmsbyinfluencingdistancemet-
ricsandintroducingunintendednoise.WeoptforUMAPoverPCA
EntityEnrich
andLDA.Afterimplementingdimensionalityreduction,weoptfor Entity
HDBSCAN[18]asourclusteringalgorithm. P In o t l e ic n y t Input EntityEmbedding Output EntityRelationships
AutomaticClusterLabelingThefinalstepinthisprocessin-
SimilarityMeasuring
volvestheautomaticlabelingoftheclusters.Toaccomplishthis
task,ourinitialapproachentailsemployingtheword-segmentation RelationDiscoveryModule
toolforsentencesegmentationwithineachcluster.Subsequently,
Fig.5:RelationDiscoveryModuleusingEmbedding-based
thesegmentedsentencesundergoanalysisusingthePhoNLP[21]
method
toexecutebothPOStagginganddependencytagging.Following
theextractionoftagsbythePhoNLP,arule-basedapproachisim-
plemented.Furtherrefinementisachievedbyidentifyingthemost
frequentlyoccurringtokenswithineachsubset,whicharethen 4 EXPERIMENTS
designatedasourclusterlabels.Figure4presentsacompilationof 4.1 Datasets
someofthediscoveredintentsfromtheFAQdatasetastheresults
TheexperimentaldatasetsconsistofthreedifferentdatasetsBank-
ofSemanticClusteringandClusterLabellingprocesses.Involving
ing77_eng,Banking77_vni,andFAQ_HCMUT_vnipresentedinTable
coursesandclassgroups,thereexistsamultitudeofinquiriesrang-
1.Banking77_en[2]isanEnglishdatasetthatcontains77customer
ingfromcourseenrollment,classtransfers,andcapacityexpansions,
intentsfromover10,000questionsinthebankingdomain.Bank-
totimetablematters.Investigatingtheintentsandassociatedenti-
ing77_vniisaVietnamesedatasetthatisanauto-translation(using
tiescanaidinprovidinggoodresponsesorinitiatingsubsequent
GoogleTranslate)oftheBanking77_engdataset.FAQ_HCMUT_vni
actions.
isaVietnamesedatasetthatcontainsover200,000frequentlyasked
questions(FAQs)collectedfromtheHelpDesksystemoftheHC-
3.3 Embedding-basedmethodforRelation
MUT.TheBanking77_engandBanking77_vnidatasetsareusedto
Discovery evaluatetheperformanceoftheourframework.WhileFAQ_HCMUT_vni
InthecontextofRelationDiscoverybetweenIntentsandother datasetisusedtodemonstratetheresultoftheOEDframework.
entities,weadoptanEmbedding-basedapproach.Duetoresource Toinvestigatetheimpactofdifferentembeddingsonclustering
andtimeconstraints,weinitiallyexperimentedwithtwomajor performance,ourframeworkutilizesVietnameseSimCSEforViet-
typesofentities:intentandpolicy.Toaccommodatealargeamount namesedatasets,whiletheoriginalBERTopicemploysasentence-
ofdiversedatawithvaryinglengths,weemploytwo-stageretriever. transformersmodel(all-miniLM-L6variant).

Cross-DataKnowledgeGraphConstructionforLLM-enabledEducationalQuestion-AnsweringSystem:ACaseStudyatHCMUTConference’17,July2017,Washington,DC,USA
4.2 DiscoveredEducationalOpenIntents generalpipelineofthequestion-answeringsystemfollowingthe
Table1illustratestheoutcomesofourexperimentationindiscov- Figure6(a).Theprocessofansweringuserquestionsinvolvesfeed-
eringintentsacrossthespecifieddatasets.TovalidatetheOED ingthequestionintoourinstitution’sLLM,URA,whichgenerates
Framework,weexecutedtheBERTopicframeworkontwodatasets, astructuredqueryintheformofNeo4j’sCypherlanguage,asour
Banking77_engandBanking77_vni.TheclusteringresultsinCases knowledgegraphdatabaseisbuiltonNeo4j.Thisquerysearches
1and2demonstratethesuperiorperformanceoftheBERTopic aknowledgegraphdatabasehandcraftedusingintentdiscovery’s
frameworkwiththeEnglishdataset,where73intentswereidenti- resulttoretrievematchingsub-graphsandrelevanttriples.Next,
fied,closelyaligningwiththe77predeterminedcategories.How- thetriplesareconvertedintoanaturallanguageformatandcom-
ever,intheBanking77_vnidataset,thecountofidentifiedintents binedwiththeoriginaluserquestiontocreateafinalpromptfor
notablydecreasedto65.InCase3,theOEDFrameworkexhibited theLLM.ThepromptguidestheLLMingeneratingacoherentand
betterperformancewiththeBanking77_vnidatasetcomparedto accurateanswerasdemonstratedinFigure6(b).
theBERTopicframeworkfortheVietnameselanguage,yielding76
extractedintents.Subsequently,weappliedtheOEDFrameworkto
Retriever KnowledgeGraph
theHCMUT_FAQ_vnidataset(Case4),resultinginatotalof284 UserQuestion KG-Retrieval
Utterance
clusterswithsignificantnoisedclusters,andduplicatedclusters.
Despitethis,approximately372intentswerederivedfromthese LargeLanguageModel
clusters,althoughasubstantialnumberofintentsremainundiscov- RelevantKnowledge URALLM GeneratedAnswer
ered.Aspreviouslymentioned,Figure4illustratessomeremarkable
(a)KG-augmentedLLMsApproach
openintentsdiscoveredbyourapproach.
Table1:Openintentdiscoveryresult
Case Framework Dataset Cluster’sNo Extractedintent
1 BERTopic Banking77_eng 157 73
2 BERTopic Banking77_vni 147 65
3 OEDFramework Banking77_vni 257 76
4 OEDFramework HCMUT_FAQ_vni 284 372
4.3 Embedding-basedmethodforRelation
DiscoveryResult
Theembedding-basedapproachforrelationdiscoveryhasyielded (b)Demonstrationofcoursewithdrawalcase
promisingresultsinexploringrelationshipsbetweenentities,partic-
ularlyintheeducationdomain.Table2showtheresultofEmbedding- Fig.6:KG-augmentedLLMsApproachandDemonstration
basedapproach,inthisexperiment,thereare243intententitiesand ofcoursewithdrawalcase
237policyentities.Followingourapproach,andafterseveraltrials,
we’vesettledonathresholdof0.32.Atotalof613relationships
4.5 Discussion
betweenentitypairs(intentandpolicy)havebeenidentified.Out
ofthese,53intententitiesdonothaveanyassociationswithpol- Thesectionaboveoutlinestheoutcomesofourresearchefforts
icyentities.Forinstance,theintent"downloadform"isbroadand focusedonthreekeyareas:Discoveringopen-intents,Developing
lacksspecificentityreferences.Additionally,amongthese53intent anembedding-basedtechniqueforRelationDiscovery,andImple-
entitieswithoutrelationships,22intentsareoverlooked,indicating mentingKG-augmentedLLMsapproach.
theyindeedhaveconnectionswithpoliciesbutwerenotdetected. First,discoveringopen-intentsthroughunsupervisedapproach
Forexample,"Cancelcourse"and"Withdrawcourse"arelinkedto showspromisingresults,butapplyingittoVietnameseencounters
theWithdrawalPolicy. variousdifficultiesduetothelanguage’sspecificcharacteristics.
Thereisaconsiderableamountofoverlappingandrepetitiveclus-
Table2:Relationdiscoveryresult tersduetotheinadequateperformanceofNLPtoolkitsforViet-
namese.NamedEntity(NE)withinsentencesfurtherinterfereswith
theclusteringprocess.Duetothesubparclusteringstep,automatic
Entitypair [Intent,Policy]
Noofentities [243,237] labelingisalsoaffectedaccordingly.ApplyingHyponym-approach
Discoveredrelationships 613 totheseNERsrepresentsapotentialapproachforoptimizingclus-
Non-associativeintents 53 tering.
Overlookedintents 22
Second,theEmbedding-basedmethodforRelationDiscovery
hasshownpromisingresultsinidentifyingrelationshipsbetween
4.4 KG-augmentedLLMsApproachin
entities.However,furtherresearchisneededtoexplorethediffer-
EducationalContext enttypesofrelationsthatcanbediscoveredusingthismethod.
Toaddressthe"KG-augmentedLLMs"aspectoftheresearchand Additionally,thereisaneedtodevelopmorerobustandaccurate
itsapplicationintheeducationdomainatHCMUT,weconducta methodsforrelationextractionandclassification.

Conference’17,July2017,Washington,DC,USA TuanBui,etal.
Finally, the KG-augmented LLMs approach is initially imple- Linguistics,Singapore,12685–12708. https://doi.org/10.18653/v1/2023.emnlp-
mentedbyusingoff-the-shelftoolsfromNeo4J.TheKG-retrieval main.782
[15] MikeLewis,YinhanLiu,NamanGoyal,MarjanGhazvininejad,Abdelrahman
engineextractstriplets.Theadvantagesofthismethodarethatthe
Mohamed,OmerLevy,VesStoyanov,andLukeZettlemoyer.2019.BART:De-
informationiscondensedandaccurate,andthetripletsalsorepre- noisingSequence-to-SequencePre-trainingforNaturalLanguageGeneration,
sentrelationstohelptheLLManswerquestionsbetter.However, Translation,andComprehension. arXiv:1910.13461[cs.CL]
[16] PatrickLewis,EthanPerez,AleksandraPiktus,FabioPetroni,VladimirKarpukhin,
thetripletsretrievalengineonlyextractsrelevanttriplesanddoes NamanGoyal,HeinrichKüttler,MikeLewis,WentauYih,TimRocktäschel,
nothavearankingmechanismtohelpeliminateredundanttriples. SebastianRiedel,andDouweKiela.2021.Retrieval-AugmentedGenerationfor
Knowledge-IntensiveNLPTasks. arXiv:2005.11401[cs.CL]
[17] PengfeiLiu,YouzhangNing,KingKeungWu,KunLi,andHelenMeng.2021.Open
5 CONCLUSION IntentDiscoverythroughUnsupervisedSemanticClusteringandDependency
Parsing. arXiv:2104.12114[cs.CL]
Inthisarticle,weintroduceanapproachtoopenintentdiscovery
[18] LelandMcInnes,JohnHealy,SteveAstels,etal.2017. hdbscan:Hierarchical
usingunsupervisedlearningmethods.Tothebestofourknowledge, densitybasedclustering.J.OpenSourceSoftw.2,11(2017),205.
thisisthefirstpapertousethisapproachforopenintentdiscovery [19] AnkanMullick,IshaniMondal,SourjyadipRay,RRaghav,GSaiChaitanya,and
PawanGoyal.2023.IntentIdentificationandEntityExtractionforHealthcare
inVietnamese.Theresultsareevaluatedonthreedatasets:Bank- QueriesinIndicLanguages. arXiv:2302.09685[cs.IR]
inf77_eng,Banking77_vni,andHCMUT_FAQ_vni.Additionally,we [20] DatQuocNguyenandAnhTuanNguyen.2020.PhoBERT:Pre-trainedlanguage
performpreliminaryexperimentsondiscoveringtherelationships
modelsforVietnamese.InFindingsoftheAssociationforComputationalLinguis-
tics:EMNLP2020,TrevorCohn,YulanHe,andYangLiu(Eds.).Associationfor
betweenintentsandotherentitiestobuildaKGfortheeducation ComputationalLinguistics,Online,1037–1042. https://doi.org/10.18653/v1/2020.
domain.WealsoconductsomeexperimentsonapplyingtheKGto findings-emnlp.92
[21] LinhTheNguyenandDatQuocNguyen.2021.PhoNLP:Ajointmulti-tasklearn-
LLM.
ingmodelforVietnamesepart-of-speechtagging,namedentityrecognitionand
dependencyparsing.InProceedingsofthe2021ConferenceoftheNorthAmerican
REFERENCES
ChapteroftheAssociationforComputationalLinguistics:Demonstrations.1–7.
[22] FabioPetroni,TimRocktäschel,PatrickLewis,AntonBakhtin,YuxiangWu,
[1] JinheonBaek,AlhamFikriAji,andAmirSaffari.2023.Knowledge-Augmented AlexanderH.Miller,andSebastianRiedel.2019.LanguageModelsasKnowledge
LanguageModelPromptingforZero-ShotKnowledgeGraphQuestionAnswer- Bases? arXiv:1909.01066[cs.CL]
ing.InProceedingsofthe1stWorkshoponNaturalLanguageReasoningandStruc- [23] AlecRadford,KarthikNarasimhan,TimSalimans,IlyaSutskever,etal.2018.
turedExplanations(NLRSE),BhavanaDalviMishra,GregDurrett,PeterJansen, Improvinglanguageunderstandingbygenerativepre-training.(2018).
DaniloNevesRibeiro,andJasonWei(Eds.).AssociationforComputationalLin- [24] MariiaRizun.2019. KnowledgeGraphApplicationinEducation:aLiterature
guistics,Toronto,Canada,78–106. https://doi.org/10.18653/v1/2023.nlrse-1.7 Review.ActaUniversitatisLodziensis.FoliaOeconomica3(082019),7–19. https:
[2] IñigoCasanueva,TadasTemčinas,DanielaGerz,MatthewHenderson,and //doi.org/10.18778/0208-6018.342.01
IvanVulić.2020. EfficientIntentDetectionwithDualSentenceEncoders. [25] HuongDuongToandPhucDo.2020.ExtractingtriplesfromVietnamesetext
arXiv:2003.04807[cs.CL] tocreateknowledgegraph.In12thInternationalConferenceonKnowledgeand
[3] MinhuaChen,BadrinathJayakumar,MichaelJohnston,S.EmanMahmoodi, SystemsEngineering,KSE2020,CanThoCity,Vietnam,November12-14,2020.
andDanielPressel.2022. IntentDiscoveryforEnterpriseVirtualAssistants: IEEE,219–223. https://doi.org/10.1109/KSE50997.2020.9287471
ApplicationsofUtteranceEmbeddingandClusteringtoIntentMining.InNorth [26] HugoTouvron,LouisMartin,KevinStone,PeterAlbert,AmjadAlmahairi,Yas-
AmericanChapteroftheAssociationforComputationalLinguistics. https://api. mineBabaei,NikolayBashlykov,SoumyaBatra,PrajjwalBhargava,ShrutiBhos-
semanticscholar.org/CorpusID:250390998 ale,DanBikel,LukasBlecher,CristianCantonFerrer,MoyaChen,GuillemCucu-
[4] PengheChen,YuLu,VincentW.Zheng,XiyangChen,andBodaYang.2018. rull,DavidEsiobu,JudeFernandes,JeremyFu,WenyinFu,BrianFuller,Cynthia
KnowEdu:ASystemtoConstructKnowledgeGraphforEducation.IEEEAccess Gao,VedanujGoswami,NamanGoyal,AnthonyHartshorn,SagharHosseini,
6(2018),31553–31563. https://doi.org/10.1109/ACCESS.2018.2839607 RuiHou,HakanInan,MarcinKardas,ViktorKerkez,MadianKhabsa,Isabel
[5] YousraFettach,MounirGhogho,andBoualemBenatallah.2022. Knowledge Kloumann,ArtemKorenev,PunitSinghKoura,Marie-AnneLachaux,Thibaut
GraphsinEducationandEmployability:ASurveyonApplicationsandTech- Lavril,JenyaLee,DianaLiskovich,YinghaiLu,YuningMao,XavierMartinet,
niques.IEEEAccess10(2022),80174–80183. https://doi.org/10.1109/ACCESS. TodorMihaylov,PushkarMishra,IgorMolybog,YixinNie,AndrewPoulton,
2022.3194063 JeremyReizenstein,RashiRungta,KalyanSaladi,AlanSchelten,RuanSilva,
[6] TianyuGao,XingchengYao,andDanqiChen.2022.SimCSE:SimpleContrastive EricMichaelSmith,RanjanSubramanian,XiaoqingEllenTan,BinhTang,Ross
LearningofSentenceEmbeddings. arXiv:2104.08821[cs.CL] Taylor,AdinaWilliams,JianXiangKuan,PuxinXu,ZhengYan,IliyanZarov,
[7] MaartenGrootendorst.2022.BERTopic:Neuraltopicmodelingwithaclass-based YuchenZhang,AngelaFan,MelanieKambadur,SharanNarang,AurelienRo-
TF-IDFprocedure.arXivpreprintarXiv:2203.05794(2022). driguez,RobertStojnic,SergeyEdunov,andThomasScialom.2023. Llama2:
[8] ChengGuoandFelixBerkhahn.2016.EntityEmbeddingsofCategoricalVariables. OpenFoundationandFine-TunedChatModels. arXiv:2307.09288[cs.CL]
arXiv:1604.06737[cs.LG] [27] Nikhita Vedula, Nedim Lipka, Pranav Maneriker, and Srinivasan
[9] AidanHogan,EvaBlomqvist,MichaelCochez,ClaudiaD’amato,GerardDeMelo, Parthasarathy. 2019. Towards Open Intent Discovery for Conversational
ClaudioGutierrez,SabrinaKirrane,JoséEmilioLabraGayo,RobertoNavigli,Se- Text. arXiv:1904.08524[cs.IR]
bastianNeumaier,Axel-CyrilleNgongaNgomo,AxelPolleres,SabbirM.Rashid, [28] NikhitaVedula,NedimLipka,PranavManeriker,andSrinivasanParthasarathy.
AnisaRula,LukasSchmelzeisen,JuanSequeda,SteffenStaab,andAntoineZim- 2020.OpenIntentExtractionfromNaturalLanguageInteractions.InProceed-
mermann.2021. KnowledgeGraphs. Comput.Surveys54,4(July2021),1–37. ingsofTheWebConference2020(Taipei,Taiwan)(WWW’20).Associationfor
https://doi.org/10.1145/3447772 ComputingMachinery,NewYork,NY,USA,2009–2020. https://doi.org/10.1145/
[10] NicolasHubert,ArmelleBrun,andDavyMonticolo.2022.NewOntologyand 3366423.3380268
KnowledgeGraphforUniversityCurriculumRecommendation. [29] WenhuiWang,FuruWei,LiDong,HangboBao,NanYang,andMingZhou.
[11] ZiweiJi,NayeonLee,RitaFrieske,TiezhengYu,DanSu,YanXu,EtsukoIshii, 2020.MiniLM:DeepSelf-AttentionDistillationforTask-AgnosticCompression
YeJinBang,AndreaMadotto,andPascaleFung.2023.SurveyofHallucination ofPre-TrainedTransformers. arXiv:2002.10957[cs.CL]
inNaturalLanguageGeneration. Comput.Surveys55,12(March2023),1–38. [30] Jason Wei, Yi Tay, Rishi Bommasani, Colin Raffel, Barret Zoph, Sebastian
https://doi.org/10.1145/3571730 Borgeaud,DaniYogatama,MaartenBosma,DennyZhou,DonaldMetzler,EdH.
[12] MinkiKang,JinMyungKwak,JinheonBaek,andSungJuHwang.2023.Knowl- Chi,TatsunoriHashimoto,OriolVinyals,PercyLiang,JeffDean,andWilliamFe-
edgeGraph-AugmentedLanguageModelsforKnowledge-GroundedDialogue dus.2022.EmergentAbilitiesofLargeLanguageModels.arXiv:2206.07682[cs.CL]
Generation. arXiv:2305.18846[cs.CL]
[13] VladimirKarpukhin,BarlasOğuz,SewonMin,PatrickLewis,LedellWu,Sergey
Edunov,DanqiChen,andWentauYih.2020.DensePassageRetrievalforOpen-
DomainQuestionAnswering. arXiv:2004.04906[cs.CL]
[14] SeungoneKim,SeJoo,DoyoungKim,JoelJang,SeonghyeonYe,JaminShin,
andMinjoonSeo.2023.TheCoTCollection:ImprovingZero-shotandFew-shot
LearningofLanguageModelsviaChain-of-ThoughtFine-Tuning.InProceedings
ofthe2023ConferenceonEmpiricalMethodsinNaturalLanguageProcessing,
HoudaBouamor,JuanPino,andKalikaBali(Eds.).AssociationforComputational

Cross-DataKnowledgeGraphConstructionforLLM-enabledEducationalQuestion-AnsweringSystem:ACaseStudyatHCMUTConference’17,July2017,Washington,DC,USA
A APPENDIX Sentence-DensityClustering(HDBSCAN):
| A.1 E-OEDFrameworkAnalysis |     |     | • MinimumClusterSize:15 |     |     |     |
| -------------------------- | --- | --- | ----------------------- | --- | --- | --- |
• MinimumClusterSize:20
Thisappendixprovidesfurtherdetailsontheimplementationof
the E-OED framework. We discuss key design choices, such as Weevaluateddifferentcombinationsofthesehyperparametersto
hyperparameterselectionandembeddingmodels,alongwiththe identifytheoptimalconfigurationforourtask.
insightsgainedfromrelatedexperiments.
|     |     |     | A.1.3 AutomaticClusterLabeling. |     | Thissectiondetailstheprocess |     |
| --- | --- | --- | ------------------------------- | --- | ---------------------------- | --- |
ThissectionwillalsodiscussthreecoremodulesinE-OEDframe-
forextractingdescriptivelabelsforouridentifiedclusters.Wefirst
worksknownasDataPreprocessing,SemanticClusteringandAuto-
|     |     |     | select the | seven most | representative sentences | for each cluster. |
| --- | --- | --- | ---------- | ---------- | ------------------------ | ----------------- |
maticClusterLabeling
Thesesentencesarechosenbasedontheirsimilaritytokeywords
Theresultachievedbydifferentdesignchoicesisrepresentedin
generatedusingcTF-IDF.
detailat4
Withinthisapproach,akeyhyperparameteristherangeofword
A.1.1 Data Preprocessing. Due to Vietnamese being a predom- lengthsconsideredforkeywordextraction.Weexperimentwith
inantlyanalyticlanguagewithalargenumberofmonosyllabic twosettings:arangeof5-7wordsandarangeof4-11words.The
morphemes(meaningfulunits),wordsareoftenformedbycombin- first setting targets terms with lengths between 5 and 7 words,
ingthesemorphemes.Thiscanpresentchallengesfortheoriginal whilethesecondallowsfortermsbetween4and11words.
| BERTopic framework, | which relies | on cTF-IDF (class-based | TF- |     |     |     |
| ------------------- | ------------ | ----------------------- | --- | --- | --- | --- |
Followingkeywordextraction,thechosensentencesarepro-
IDF)[7]fortopicmodeling.Toaddressthis,weimplementedan cessed using the PhoNLP model to obtain Part-of-Speech (PoS)
additionalpreprocessingstepthatleveragesawordsegmentation anddependencytags.Wethenleveragethesetagsinconjunction
modeltocombinesub-wordunitsintocompletewords.Thesenewly withpre-definedrules(detailedintheAlgorithm1)togenerate
formedwordsarethenjoinedusinganunderscorecharacter("_"). descriptivelabelsforeachcluster.
(e.g.,subject-"mônho.c"becomes"môn_ho.c",course-"khóaho.c"
becomes"khóa_ho.c").
Algorithm1Tagextractionalgorithms
Furthermore,tocomplywithdatasetprivacypolicies,weimple-
mentedatextanonymizationtooltocensoranypersonallyidenti- 1:functionExtractSentenceElements(𝑐𝑎𝑡𝑒𝑔𝑜𝑟𝑦_𝑑𝑜𝑐𝑠)
2:
| fiableinformation(PII)withinthesentences.Detailsregardingthe |     |     | Initializelistoflabels              |     |     |     |
| ------------------------------------------------------------ | --- | --- | ----------------------------------- | --- | --- | --- |
|                                                              |     |     | 3: foreachsentencein𝑐𝑎𝑡𝑒𝑔𝑜𝑟𝑦_𝑑𝑜𝑐𝑠do |     |     |     |
specificobjectscensoredandthecorrespondingreplacementterms 4: Cleanthesentencebystrippingwhitespace
|     |     |     | 5: Gettheannotationresultfrom𝑃ℎ𝑜𝑁𝐿𝑃 |     |     |     |
| --- | --- | --- | ----------------------------------- | --- | --- | --- |
arepresentedinTable3 6: Extractthepart-of-speech(POS)anddependency(DEP)information
7:
Initializelistsforverbs,directobjects,verbmodifiers,andotherlist
|     |     |     | 8: Initializevariablesforrootposition,directobjectpositions,verbmodifierposition,and |     |     |     |
| --- | --- | --- | ------------------------------------------------------------------------------------ | --- | --- | --- |
Table3:Datacensoredtool prepositionposition
#Extractallrelatedpositions
|     |     |     | 9: Createasettostoretherelevantpositions |     |     |     |
| --- | --- | --- | ---------------------------------------- | --- | --- | --- |
1 0 :
Objects Method TermReplace for e a c h to k e n in t h e s e n t e n ce d o
|            |           |             | 1 1 : | i f t h e to k e n is t h e r | o o t o f th e sentencethen |     |
| ---------- | --------- | ----------- | ----- | ----------------------------- | --------------------------- | --- |
| PersonName | NER(BERT) | [full_name] | 12:   | Additspositiontotheset        |                             |     |
StudentID Regex(7numberformat) [student_id] 13: whilethelengthofthepositionsetischangingdo
|             |                       |                | 14: | foreachtokeninthedocumentdo |     |     |
| ----------- | --------------------- | -------------- | --- | --------------------------- | --- | --- |
| Phonenumber | Regex(10numberformat) | [phone_number] |     |                             |     |     |
Email Regex(ordinaryemailwith@) [email] 15: ifthetoken’sdependencyisrelatedtotherootorotherrelevantpositions
then
16:
Additspositiontotheset
|                           |                                |     | 17:                             | ifthelengthofthesetdoesn’tchangethen |     |     |
| ------------------------- | ------------------------------ | --- | ------------------------------- | ------------------------------------ | --- | --- |
|                           | Ourmodelconsistsofthreeprimary |     | 18:                             |                                      |     |     |
| A.1.2 SemanticClustering. |                                |     |                                 | Breaktheloop                         |     |     |
| components:               |                                |     | #Extractthesentenceelements     |                                      |     |     |
|                           |                                |     | 19: foreachtokeninthedocumentdo |                                      |     |     |
• SentenceEmbedding:extractsvectorrepresentationsofsen- 20: ifthetoken’sdependencyis’root’then
21:
| tences. |     |     |     | Addittotheverbsandconsecutivelists                        |     |     |
| ------- | --- | --- | --- | --------------------------------------------------------- | --- | --- |
|         |     |     | 22: | ifthetoken’sdependencyis’prp’anditspositionisinthesetthen |     |     |
DimensionReduction:addressesthe"curseofdimensional- 23: Addittothedirectobjectslists
•
|     |     |     | 2 4 : | ifth e t ok e n ’s d ep e | n d e n c y i s ’ d o b ’then |     |
| --- | --- | --- | ----- | ------------------------- | ----------------------------- | --- |
ity"bycompressingtheseembeddingsintoalower-dimensional 2 5 : A d d it t o th e d ir e c t o b je c t s l i st
space,improvingcomputationalefficiency. 26: ifthetoken’sdependencyis’vmod’anditspositionisrelatedtotheroot,preposition,
orverbmodifie r p os i ti o n s
| • Sentence-densityclustering:groupssentencesbasedontheir |     |     |     | t h e                   | n               |     |
| -------------------------------------------------------- | --- | --- | --- | ----------------------- | --------------- | --- |
|                                                          |     |     | 27: | A d d i t t o t h e v e | rbmodifierslist |     |
reduced-dimensionalrepresentations. 28: ifthetoken’sdependencyis’nmod’anditspositionisrelatedtoadirectobject
positionthen
Ourmodel’sperformanceishighlysensitivetothechosenhyper- 29: Addittotheotherlist
|     |     |     | 30: | ifthetoken’spositionoritsdependency’spositionisinthesetandthedependency |     |     |
| --- | --- | --- | --- | ----------------------------------------------------------------------- | --- | --- |
parameters.Weexploredvariousoptionsforeachmodule:
isinapredefinedlistthen
| SentenceEmbedding: |     |     | 31: | Addthetokentotheotherlist |     |     |
| ------------------ | --- | --- | --- | ------------------------- | --- | --- |
32:
Extractthemostfrequenttokensineachlist.
• BERTopicBaseModel(MiniLM-L6):A6-layerMicrosoftMiniLM 33: Addthetokensintolistoflabels
|     |     |     | 34: returnlistoflabels |     |     |     |
| --- | --- | --- | ---------------------- | --- | --- | --- |
[29]fine-tunedona1billionsentencepairdataset.
• SupervisedVietnameseSimCSE:Fine-tunedfromthePhoBERT
model.
Inordertoreducenoisesonnewlyextractedtags,wethentake
DimensionReduction(UMAP): themostfrequentlyoccurringtokenswithineachsubset,which
Numberofneighbors:20,Numberofcomponents:4 arethendesignatedasourclusterlabels.Forbetterclusterlabels,
•
| • Numberofneighbors:15,Numberofcomponents:9 |     |     | LLMscanbeused. |     |     |     |
| ------------------------------------------- | --- | --- | -------------- | --- | --- | --- |

Conference’17,July2017,Washington,DC,USA TuanBui,etal.
A.1.4 ResultandInsights. Thereare5experimentswithdifferent Finally,theframeworkissensitivetohyperparameterselection.
designselectionintotal: Duetothepresenceofnumeroushyperparametersrequiringtuning,
(1) Experiment1: carefulconsiderationshouldbegivenwhenapplyingthismethod
• Dataset:Banking77_eng toyourspecificdomainorFAQdataset.
• NumberofNeighbors:20
• NumberofComponents:4
• MinimumClusterSize:20
• cTF-IDFRange:[5-7]
(2) Experiment2:
• Dataset:Banking77_vni
(a) Experiment2.1:
• NumberofNeighbors:20
• NumberofComponents:4
• MinimumClusterSize:20
• cTF-IDFRange:[5-7]
(b) Experiment2.2:
• NumberofNeighbors:15
• NumberofComponents:9
• MinimumClusterSize:15
• cTF-IDFRange:[4-11]
(3) Experiment3:
• Dataset:Banking77_vni
• LanguageModel:SimCSE(insteadofMiniLM)
(a) Experiment3.1
• NumberofNeighbors:20
• NumberofTopics:4
• MinimumClusterSize:20
• cTF-IDFRange:[5-7]
(b) Experiment3.2
• NumberofNeighbors:15
• NumberofComponents:9
• MinimumClusterSize:15
• cTF-IDFRange:[4-11]
Table4:Designselectionresult
Experiment IntentionsDiscovered
Experiment1 73
Experiment2.1 65
Experiment2.2 74
Experiment3.1 71
Experiment3.2 76
Ourexperimentsrevealedseveralkeyinsights.Firstly,theorigi-
nalembeddingmodel,despitenotbeingtrainedonVietnamesedata,
achievedreasonableperformanceonourbanking77_vnidataset.
Thissuggestspotentialtransferabilityduetostructuralsimilari-
tiesacrosslanguages.However,fine-tuningadedicatedembedding
modelspecificallyforVietnamesecouldlikelyyieldfurtherim-
provements.Evaluatingthequalityoftheembeddingmodelcan
beachievedbyanalyzingtherepresentativesentenceswithineach
cluster.Greatersemanticsimilaritywithinclusterssignifiesamore
effectivemodel.
Secondly,ahighernumberofcomponentsinUMAPincreases
focusonlocalattributes,leadingtogreaterseparationandpoten-
tiallyclearervisualizations.However,it’scrucialtobemindfulof
the"curseofdimensionality"whenemployingthisapproach.