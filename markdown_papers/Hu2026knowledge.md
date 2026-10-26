---
title: "Hu2026knowledge"
source: "Hu2026knowledge.pdf"
source_sha256: "dab20c119b4ec8eedb349fef59219bed3a066775906fa533d2730b09c5f8eaa3"
converted_at: "2026-10-26T07:04:57.637658+00:00"
markitdown_version: "0.1.9"
---
|     |     |     |     |     |     |     |     | TYPE | OriginalResearch |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | ---- | ---------------- | --- | --- |
03September2026
PUBLISHED
|     |                  |     |     |     |         |     |          | DOI 10.3389/fmed.2026.1943401 |     |     |     |
| --- | ---------------- | --- | --- | --- | ------- | --- | -------- | ----------------------------- | --- | --- | --- |
|     | Knowledge-guided |     |     |     |         |     | adaptive |                               |     |     |     |
|     | educational      |     |     |     | support |     |          | for                           |     |     |     |
OPENACCESS
|     | traditional |     |     | Chinese |     |     | medicine |     |     |     |     |
| --- | ----------- | --- | --- | ------- | --- | --- | -------- | --- | --- | --- | --- |
EDITEDBY
NinaPereza,
| UniversityofRijeka,Croatia | using | large |     | language |     |     |     | models |     | and |     |
| -------------------------- | ----- | ----- | --- | -------- | --- | --- | --- | ------ | --- | --- | --- |
REVIEWEDBY
| AnasAlhur, | knowledge |     |     | graphs: |     |     | integrating |     |     |     |     |
| ---------- | --------- | --- | --- | ------- | --- | --- | ----------- | --- | --- | --- | --- |
UniversityofHail,SaudiArabia
PutiXu,
|     | Confucian |     |     | educational |     |     |     | principles |     |     |     |
| --- | --------- | --- | --- | ----------- | --- | --- | --- | ---------- | --- | --- | --- |
VictoriaUniversity,Australia
*CORRESPONDENCE
HongxingKan
ffdkhx@ahtcm.edu.cn JiliHu1,2†,YuchenDuan1†,QingqingZhou1,DenggaoZheng1,
FanXu
xufanahcm@qq.com YuLi1,ChiQin1,YuLiu1,2,HongxingKan1,2* andFanXu3,4*
†Theseauthorshavecontributedequally 1SchoolofMedicalInformationEngineering,AnhuiUniversityofChineseMedicine,Hefei,China,
tothisworkandsharefirstauthorship 2CenterforXin’anMedicineandModernizationofTraditionalChineseMedicineofIHM,Anhui
UniversityofChineseMedicine,Hefei,China,3SchoolofPharmacy,AnhuiUniversityofChinese
RECEIVED20July2026 Medicine,Hefei,China,4AnhuiProvincialKeyLaboratoryofChineseMedicinalFormula,Hefei,China
REVISED05August2026
ACCEPTED10August2026
PUBLISHED03September2026
Introduction:TheConfucianprincipleof“teachingstudentsinaccordancewith
CITATION
HuJ,DuanY,ZhouQ,ZhengD,LiY, theiraptitude”remainschallengingtoimplementatscaleinTraditionalChinese
QinC,LiuY,KanHandXuF(2026)
|     | Medicine | (TCM) | education. |     | We developed |     | an Intelligent | TCM | Tutoring | System |     |
| --- | -------- | ----- | ---------- | --- | ------------ | --- | -------------- | --- | -------- | ------ | --- |
Knowledge-guidedadaptiveeducational
|     | integrating | a large | language |     | model | (LLM) | with | a domain-specific |     | knowledge |     |
| --- | ----------- | ------- | -------- | --- | ----- | ----- | ---- | ----------------- | --- | --------- | --- |
supportfortraditionalChinesemedicine
usinglargelanguagemodelsand graph(KG)derivedfromtheGoldenMirrorofMedicineandevaluateditssystem
knowledgegraphs:integrating performanceandshort-termeducationaloutcomes.
Confucianeducationalprinciples.
Front.Med.13:1943401. Methods: System outputs were rated by five TCM teachers. In a three-group
doi:10.3389/fmed.2026.1943401 pedagogical experiment, 125 student volunteers were randomly allocated to
|     | self-directed | learning, |     | LLM-assisted |     | learning, | or  | learning | with | the integrated |     |
| --- | ------------- | --------- | --- | ------------ | --- | --------- | --- | -------- | ---- | -------------- | --- |
COPYRIGHT
©2026 Hu,Duan,Zhou,Zheng,Li,Qin, system,and102questionnaireswereincludedinthefinalanalysis.
Liu,KanandXu.Thisisanopen-access
|     | Results: | The integrated |     | system | received |     | higher | expert | ratings | than the | LLM |
| --- | -------- | -------------- | --- | ------ | -------- | --- | ------ | ------ | ------- | -------- | --- |
articledistributedunderthetermsofthe
|     | baseline | without | KG integration |     | in  | instructional |     | content generation, |     | intelligent |     |
| --- | -------- | ------- | -------------- | --- | --- | ------------- | --- | ------------------- | --- | ----------- | --- |
CreativeCommonsAttributionLicense
(CCBY).Theuse,distributionor questionanswering,andautomatedtestgenerationandgrading.Studentsusing
reproductioninotherforumsis theintegratedsystem achievedsignificantlyhigher immediatepost-testscores
permitted,providedtheoriginalauthor(s)
andthecopyrightowner(s)arecredited thanbothcomparisongroupsandreportedmorefavorablepost-sessionlearning
andthattheoriginalpublicationinthis experienceratingsinrelevantcomparisons.
journaliscited,inaccordancewith Discussion: ThesefindingsprovidepreliminaryevidencethatanLLM-KGsystem
acceptedacademicpractice.Nouse,
distributionorreproductionispermitted can enhance immediate learning outcomes and learning experiences in this
| whichdoesnotcomplywiththeseterms. | educationalsetting. |     |     |     |     |     |     |     |     |     |     |
| --------------------------------- | ------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
KEYWORDS
|     | adaptive educational |     | support, |     | intelligent | tutoring |     | system, knowledge |     | graphs, | large |
| --- | -------------------- | --- | -------- | --- | ----------- | -------- | --- | ----------------- | --- | ------- | ----- |
languagemodels,traditionalChinesemedicine
1 Introduction
TraditionalChineseMedicine(TCM)referstoatraditionalmedicalsystemoriginating
|                     | in China    | that emphasizes  |              | a holistic | approach  |              | and diagnosis | and        | treatment    | based             | on      |
| ------------------- | ----------- | ---------------- | ------------ | ---------- | --------- | ------------ | ------------- | ---------- | ------------ | ----------------- | ------- |
|                     | syndrome    | differentiation. |              | As an      | integral  | component    |               | of Chinese | culture,     | it encompasses    |         |
|                     | theoretical | and practical    |              | knowledge  | developed |              | through       | centuries  | of           | clinical practice |         |
|                     | (1, 2). The | effective        | transmission |            | of        | this complex |               | knowledge  | is paramount |                   | for its |
| FrontiersinMedicine |             |                  | 01           |            |           |              |               |            |              | frontiersin.org   |         |

Huetal. 10.3389/fmed.2026.1943401
sustaineddevelopment.Historically,TCMeducationcenteredon Proposing an LLM-KG integrated teaching method designed
an apprenticeship model, where masters imparted theoretical toenhanceinstructionalefficiencyandstudentlearningoutcomes
knowledge and clinical experience through personalized inTCM.
instruction (3, 4). This approach is rooted in the Confucian Evaluating the method’s pedagogical performance through a
principleof“teachingstudentsinaccordancewiththeiraptitude” classroom experiment, using student performance and subjective
(Yin Cai Shi Jiao), which advocates for instruction tailored to feedbacktoassessitspracticalityandeffectiveness.
individual learner differences (5, 6). This philosophy aligns with This research not only offers a novel approach to the
modern learner-centered teaching theories (7), which prioritize digitalization of TCM education but also presents a transferable
studentinitiativeanddevelopment,underscoringitscross-cultural modelforapplyingintegratedLLMandKGtechnologiesinother
educationalvalue,especiallyinaspecializedfieldlikeTCM(8,9). educational domains. It explores how the principle of “teaching
However, the traditional apprenticeship model lacked studentsinaccordancewiththeiraptitude”caninformamodern
standardization for large-scale talent cultivation. Consequently, digitalframeworkforlearner-responsiveeducationalsupport.
university-based education became the primary training pathway
inChinatoensurescaleanduniformity(3).Despiteitssystematic
approach, the expansion of modern higher TCM education
has led to challenges such as faculty shortages and resource
constraints.Thisoftenresultsinhomogenizedtraining,hindering 2 Related work
the implementation of personalized instruction and failing to
2.1 Applications of large language models
cater to individual student needs (10). Students face a vast,
fragmented curriculum presented in classical Chinese, making in education
core concepts difficult to grasp (11). The predominant teacher-
centered pedagogical model is often inefficient, while existing In recent years, significant progress has been made in the
formative assessments provide feedback with significant delays applicationofLLMsineducation,wheretheyhavedemonstrated
and lack specificity (12). As a result, instructors struggle to immensepotential,particularlyinsupportingadaptiveandlearner-
track student progress dynamically and provide the necessary responsiveeducationalexperiences.LLMscanprovidecustomized
personalizedguidance. knowledge generation, answer queries, and recommend learning
To address these challenges, integrating modern information paths tailored to learners’ proficiency levels, interests, and needs,
technology is crucial for enabling intelligent teaching and thereby facilitating a paradigm shift in education from “one-
personalizedlearning(13,14).Therapiddevelopmentofartificial size-fits-all instruction” to “personalized guidance.” For instance,
intelligence (AI), particularly large language models (LLMs), Mihaljevic´ et al. (23) utilized an LLM-supported tool in a
offerspowerfultoolsforpersonalizededucationthroughadvanced softwaredevelopmentcourse,whichenhancedstudents’efficiency
language understanding and generation capabilities (15, 16). in learning programming skills and significantly improved
Concurrently,KnowledgeGraphs(KGs)providearobustmethod their comprehension and completion of programming tasks,
for structuring the vast, complex knowledge of TCM into a demonstrating the model’s adaptive support for students at
coherent semantic network, facilitating knowledge visualization varying proficiency levels. Spina et al. (24) leveraged GPT-
andmanagement(17). 4 to simplify medical literature on glaucoma, which not only
ThisstudyproposesthatintegratingKGswithLLMscancreate enhanced patient comprehension but also enabled audiences
a powerful synergy for TCM education. This approach allows a with diverse educational backgrounds to effectively access key
system to leverage semantic relationships for more precise and information, showcasing the LLM’s capacity to tailor content
logically structured responses to complex queries (18). It can to individual cognitive differences. Guo et al. (25) integrated
visualizetheknowledgesystemandgeneratelearningresourcesin an LLM into middle school science and engineering practice
response to selected topics and user queries, thereby supporting courses and found that, compared to traditional methods, this
adaptive educational interactions. Inspired by the principle of integratedapproachsignificantlyenhancedstudents’individualized
“teachingstudentsinaccordancewiththeiraptitude,”wedesigned development across multiple dimensions, including scientific
a functional framework for an Intelligent TCM Tutoring System, knowledge, attitudes toward technology, and problem-solving
as illustratedin Figure1. We investigatethis approachthrough a skills.Wangetal.(26)validatedthefeasibilityofusingChatGPT
case study of the Golden Mirror of Medicine (19), a foundational as a standardized patient simulation tool, demonstrating that
Qingdynastytextrenownedforitssystematicandcomprehensive an optimized LLM can personalize roles and feedback for
content (20, 21). Despite its importance, its classical language different learning scenarios, thus enhancing the interactivity and
and abstract semantics present significant learning challenges for realism of medical education. Ye et al. (27), by optimizing the
modernstudents,necessitatinginnovativepedagogicaltools(22). LLM’s reasoning chain, provided personalized explanations for
Therefore,thisstudyaimstodevelopandevaluateanIntelligent mathematics learners, effectively improving learning outcomes,
TCM Tutoring System that integrates LLMs and KGs to provide comprehension,andengagement,furtherdemonstratingthevalue
adaptiveeducationalsupport.Themaincontributionsare: ofLLMsinpromotingdeeplypersonalizedlearning.TheKhanmigo
Constructing a systematic Golden Mirror of Medicine system(28)launchedbyKhanAcademydoesnotdirectlyprovide
KG as a foundation for the digital transformation of TCM answers but instead guides learners, acting as a tutor, to explore
educationalresources. solutionsindependently,promotingcriticalthinkingandfostering
FrontiersinMedicine 02 frontiersin.org

| Huetal. |     |     |     |     |     |     |     |     | 10.3389/fmed.2026.1943401 |     |
| ------- | --- | --- | --- | --- | --- | --- | --- | --- | ------------------------- | --- |
FIGURE1
ConceptualframeworkoftheIntelligentTCMTutoringSystem.ThisschematicmapstheConfucianprincipleof“teachingstudentsaccordingtotheir
aptitude”ontolearner-responsivesystemsupport.TheleftpanelillustrateshowConfuciusprovideddifferentiatedexplanationsof“Ren”
(benevolence)toYanYuan,FanChi,andSimaNiuaccordingtotheircharacteristicsandlevelsofunderstanding.Therightpanelshowshowthe
systemcombinesaknowledgegraph,intelligentquestionanswering,andintelligentquestiongenerationtosupportadvancedlearners,average
learners,andlearnerswithweakfoundationsthroughdifferentiatedlearningresourcesandactivities.AdaptedfromUnknownartist.Portraitof
ConfuciusatLeisure,Mingdynasty(1368–1644),ConfuciusMuseum,Qufu,China.PhotographbyGaryTodd.CreativeCommonsCC01.0Universal
(CC01.0).Thesourceimagewasmodifiedforintegrationintothisfigure.
independent problem-solving abilities, which aligns with the andnaturallanguageprocessing(NLP)techniquestoanalyzeand
student-centeredphilosophyofpersonalizededucation. matchskills.Thisapproachprovidedpersonalizedcourseandjob
Taken together, these studies show that LLMs can support recommendationsintendedtobridgethegapbetweeneducational
educationalcontentadaptation,guidedinquiry,simulated-patient curriculaandthechangingdemandsofthelabormarket.Luand
interaction,andpersonalizedexplanationsacrossdiverselearning Li (33) proposed a delivery method for Chinese language course
contexts. However, these applications are primarily general- resources based on KGs and similarity algorithms, introducing a
purposeortask-specific.Inmedicine,persistentconcernsregarding dual-deliverymodulethateffectivelyreducedthesimilarityamong
domain accuracy, reliability, and traceability constrain their use delivereddata,therebyimprovingdeliveryefficiency.
for specialized instruction. Evidence in TCM education remains Collectively, KG-based studies demonstrate benefits for
particularly limited, especially regarding the grounding of an learning-path planning, resource recommendation, semantic
LLM in a structured classical TCM knowledge source and organization, and retrieval. However, many existing KG-based
its application across multiple instructional tasks. These gaps educational applications primarily focus on resource selection
highlight the need for integrating LLMs with explicit domain and delivery, with relatively limited exploration of generative
knowledgestructurestosupportmorereliableandcontext-specific questionanswering,assessment,grading,andcoordinatedsupport
educationalapplications. across teaching stages. Applications to classical TCM knowledge
|     |     |     |     |     |     |     | are also scarce. | Thus, although | KGs can organize | complex |
| --- | --- | --- | --- | --- | --- | --- | ---------------- | -------------- | ---------------- | ------- |
educationalknowledge,theiruseasadomain-groundinglayerfor
2.2 Role of knowledge graphs in education interactive and evaluative functions in TCM education remains
insufficientlyexamined.
| Knowledge       | graphs        | have              | been widely | applied      | in the   | field of  |                 |             |         |         |
| --------------- | ------------- | ----------------- | ----------- | ------------ | -------- | --------- | --------------- | ----------- | ------- | ------- |
| education.      | Hou et        | al. (29) proposed | a           | personalized | learning | path      |                 |             |         |         |
| planning method |               | based on KGs,     | which       | effectively  | enhanced | the       |                 |             |         |         |
|                 |               |                   |             |              |          |           | 2.3 Synergistic | integration | of LLMs | and KGs |
| consistency     | and relevance | of                | recommended | learning     |          | paths and |                 |             |         |         |
|                 |               |                   |             |              |          |           | in education    |             |         |         |
improvedlearners’learningefficiency.Weietal.(30)investigated
| a KG-based | recommender | system | designed | to  | address | the issues |     |     |     |     |
| ---------- | ----------- | ------ | -------- | --- | ------- | ---------- | --- | --- | --- | --- |
of information overload and knowledge fragmentation in online The integration of LLMs and KGs combines the generative
education; their experimental results indicated that the system capabilitiesofLLMswiththestructuredknowledgerepresentation
improvedstudents’interestandknowledgeretentionrates.Zhong ofKGs.Priorstudieshavereportedimprovementsineducational
etal.(31)constructedarecommendationmodelusingmulti-task chatbot accuracy and responsiveness (34), cross-source question
feature learning, which embeds the KG into tasks and utilizes answering (35), recommendation under cold-start and data-
a cross-compress unit to build high-order connections between scarcity conditions (36), educational-content review (37),
latent features and entities across tasks, thereby recommending and multimodal question answering for a TCM course
professional music course teaching resources. Ramazanova et al. (38). These findings indicate that structured knowledge can
(32)studiedtheuseofaheterogeneousKGtobuildarecommender improve the grounding and task specificity of LLM-supported
system.Theyemployedmultilingualsemanticsimilarityalgorithms educationalapplications.
| FrontiersinMedicine |     |     |     |     |     |     | 03  |     |     | frontiersin.org |
| ------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --------------- |

Huetal. 10.3389/fmed.2026.1943401
Nevertheless,thereviewedstudiesgenerallyaddressindividual only visualizes knowledge but also supports in-depth learning
functions and provide limited evidence on systems that combine through powerful query capabilities, enabling instructors and
a human-validated domain KG with an end-to-end instructional students to explore the intricate relationships between concepts
workflow encompassing content generation, question answering, like diseases and treatments, thereby enhancing both teaching
assessment, grading, and feedback. They also provide limited andlearning.
within-studyevidencecomparingsuchanintegratedsystemwith
the same underlying LLM without KG support. To address
these gaps, this study constructs a human-validated KG from 3.1.3Constructionprocessofknowledgegraph
the Golden Mirror of Medicine, integrates it with an LLM
across the instructional workflow, and evaluates both expert- The construction process of our Golden Mirror of Medicine
rated system performance and students’ immediate learning KG involved three main stages: automated extraction, expert
outcomes and post-session experiences. This design enables a validation,anddatastorage.First,weemployedanLLMtoperform
context-specific evaluation of how KG grounding influences the an initial extraction of entities and relations from the source
reliabilityandeducationalutilityofLLM-basedsupportinclassical text, forming a foundational information framework. Second, to
TCMeducation. ensureaccuracyandreliability,weimplementedarigorousexpert
validation protocol. The text was segmented by book, and for
eachsegment,twoTCMprofessionalsindependentlyreviewedthe
LLM-extracted data. A cross-checking methodology was used to
3 Materials and methods
resolve discrepancies, reduce subjective bias, and standardize the
KG’scontent.Akeyprincipleduringthisstagewastopreservethe
3.1 Construction of knowledge graph
originalclassicalexpressionsfromtheGoldenMirrorofMedicine,
rather than modernizing them, to foster a deeper understanding
3.1.1Datasource
amongstudentsoftheclassictext.Finally,thevalidatedrelational
triples were exported into node and relation CSV files and
This study investigates the construction, application, and
subsequently batch-imported into a Neo4j graph database using
effectivenessoftheIntelligentTCMTutoringSystemthroughacase
theneo4j-adminutility.Thischoiceofdatabasefacilitatesefficient
studyoftheGoldenMirrorofMedicine.Thedataaredrawnfrom
storage,rapidretrieval,andintuitivevisualizationofthecomplex
the People’s Medical Publishing House edition, a comprehensive
knowledge network, enhancing the KG’s utility as a pedagogical
collection of 90 volumes (1.766 million Chinese characters) that
tool.ApartialviewoftheresultingKGisshowninFigure2.
systematically organizes TCM knowledge into 15 medical texts.
Thisversionwasselectedforitshighacademicauthority,ensured
by expert review and a reputable publisher, and its completeness
3.2 Model
incoveringthecorecontentoftheoriginalwork,thusprovidinga
reliableandsystematicdatafoundation.
We selected GLM-4-Flash (https://bigmodel.cn/) as the core
of our educational system due to its advantages in Chinese
language processing and accessibility. Foremost, it provides
3.1.2Architecturedesignofknowledgegraph
strong Chinese semantic understanding, which is crucial for
accurately parsing the specialized terminology and classical
ThearchitecturaldesignofourGoldenMirrorofMedicineKGis
literature inherent to TCM. The model also integrates seamlessly
crucialforitspedagogicalapplicationinTCMcourses.Adoptinga
with our specialized TCM knowledge graph via the LangChain
top-downapproach,wedefinedtheKG’sentitytypesandrelations
library (https://www.langchain.com/). This synergy enables the
basedontheHealthinformatics—Semanticnetworkframeworkof
systemtoleveragestructuredknowledgeformoreprecisereasoning
traditional Chinese medicine language system (39) to ensure its
andretrieval,therebysupportingthegenerationofstructuredand
semanticaccuracyandalignmentwithTCMeducationalneeds.
context-relevant educational content. Finally, its computational
The KG architecture encompasses core entity types such as
efficiency and accessibility offer practical benefits for educational
Diseases, Symptoms, Formulas, Medicinals, and Administration
applications. These characteristics make GLM-4-Flash a suitable
Methods. These entities are interconnected through several
foundationforourIntelligentTCMTutoringSystem.
key relations. Hierarchical relations, represented by includes,
structure the text’s contents, chapters, and sections. Treatment-
related connections are established through Formula and Herbs
3.3 Overall architecture of the Intelligent
relations, which link diseases or texts to their corresponding
formulas and constituent medicinals. Furthermore, Symptoms TCM Tutoring System
relations serve a diagnostic purpose by connecting diseases to
their clinical manifestations, while explanatory relations like The Intelligent TCM Tutoring System, based on LLMs and
Annotation, Note, and Collected Annotation link main texts to KGs, employs a three-tier architecture—data, architecture, and
theirvariouscommentaries. application layers—to ensure scalability and interoperability (see
Thisstructuredrepresentationisdesignedtofacilitateadeeper Figure3). The Data Layer constructs a structured knowledge
understandingofTCM’scomplextheoreticalsystem.TheKGnot base by integrating domain-specific texts (e.g., Golden Mirror of
FrontiersinMedicine 04 frontiersin.org

| Huetal. |     |     |     |     |     |     | 10.3389/fmed.2026.1943401 |     |
| ------- | --- | --- | --- | --- | --- | --- | ------------------------- | --- |
FIGURE2
PartialvisualizationoftheconstructedGoldenMirrorofMedicineknowledgegraphinNeo4j,showingrepresentativeentitytypesandsemantic
relations.ThegraphwasgeneratedfromrelationaltriplesextractedfromthesourcetextwithLLMassistance,manuallyverifiedbyTCMprofessionals,
andimportedintoNeo4j.Nodecolorsdenotedifferententitytypes:booktitles(purple),catalogs(orange),chapters(darkblue),clausetexts(red),
symptoms(lightbrown),formulas(green),herbs(pink),andadministrationmethods(lightblue).
Medicine), LLMs, and human validation. Raw text is converted assessment after class with automatic test creation, grading, and
| intorelationaltriplesviaanLLM-driven,human-verifiedprocess |                          |           |                         |         | detailedfeedback. |     |     |     |
| ---------------------------------------------------------- | ------------------------ | --------- | ----------------------- | ------- | ----------------- | --- | --- | --- |
| and stored                                                 | in a Neo4j graph         | database. | This approach           | ensures |                   |     |     |     |
| semantic                                                   | integrity and relational |           | traceability, providing | high-   |                   |     |     |     |
quality knowledge for upper-layer functions. The Architecture 3.3.1TheInstructionalContentGeneration
| Layer manages | user-resource      | interactions. | It uses             | an intent | Module |     |     |     |
| ------------- | ------------------ | ------------- | ------------------- | --------- | ------ | --- | --- | --- |
| recognition   | algorithm to parse | user          | queries, leveraging | the LLM   |        |     |     |     |
for semantic analysis and Neo4j for precise KG retrieval and The Instructional Content Generation Module automates
reasoning.Amodulartool-callingmechanismenablesflexibletask the creation of teaching syllabi, instructional schedules, and
execution, such as generating task-specific content by combining presentation slides to meet pedagogical needs. By leveraging an
semanticunderstandingwithgraphpathanalysis.TheApplication
|     |     |     |     |     | LLM, the module | analyzes instructor-uploaded |     | e-textbooks (PDF |
| --- | --- | --- | --- | --- | --------------- | ---------------------------- | --- | ---------------- |
Layer delivers educational services across pre-class, in-class, and format) to generate a structured teaching plan detailing weekly
after-classstages.Functionally,itcomprisesthreecoremodules: topics, learning objectives, and instructional requirements. The
Instructionalcontentgeneration:automaticallycreatessyllabi, process invokes the LLM’s API to extract and process data; the
schedules, and presentation slides, and facilitates KG-based extracted data then populate predefined templates. The system
explorationtoaidinteachingpreparationandstructuredlearning.
|     |     |     |     |     | produces editable | Word documents | for | syllabi and schedules, |
| --- | --- | --- | --- | --- | ----------------- | -------------- | --- | ---------------------- |
Intelligentquestionanswering(Q&A):providesquery-specific and caches files to ensure fault tolerance. Furthermore, it can
answersgeneratedbytheLLMandgroundedintheKG,promoting generate presentation slides from specified knowledge points,
knowledgeconsolidation. reducinginstructorpreparationtime.Themoduleaimstoenhance
Automated test generation and grading: supports real- instructional efficiency and quality, facilitate flexible content
| time formative | assessment | during | class and | summative |     |     |     |     |
| -------------- | ---------- | ------ | --------- | --------- | --- | --- | --- | --- |
delivery,andsupportstudentlearning.
| FrontiersinMedicine |     |     |     |     | 05  |     |     | frontiersin.org |
| ------------------- | --- | --- | --- | --- | --- | --- | --- | --------------- |

| Huetal. |     |     |     |     |     |     | 10.3389/fmed.2026.1943401 |     |
| ------- | --- | --- | --- | --- | --- | --- | ------------------------- | --- |
FIGURE3
Three-layerarchitectureandend-to-endworkflowoftheIntelligentTCMTutoringSystemintegratingalargelanguagemodel(LLM)witha
knowledgegraph(KG).Thedatalayersummarizessource-textcollation,LLM-assistedrelationextraction,manualverification,andNeo4jstorage.The
architecturelayertracesauserquerythroughLLM-basedintentprocessing,KGretrieval,responsesynthesis,andfinaloutput.Theapplicationlayer
presentstheteacher-andstudent-facingfunctionsacrosspre-class,in-class,andafter-classactivities.
3.3.2TheIntelligentQ&AModule modulealsogeneratesdetailedexplanationsforincorrectanswers,
providingstudentswithimmediate,formativefeedbacktoimprove
The Intelligent Q&A Module, a core system component, theircomprehensionandlearningoutcomes.
| integrates         | a KG with an | LLM to provide | real-time | responses           | to  |     |     |     |
| ------------------ | ------------ | -------------- | --------- | ------------------- | --- | --- | --- | --- |
| student inquiries. | Upon         | receiving      | a query,  | the system extracts |     |     |     |     |
keywords, retrieves relevant knowledge from the KG, and then 3.4 Interface of the Intelligent TCM
employs the LLM to synthesize a precise natural-language Tutoring System
| answer. This    | KG-grounded     | approach | enhances   | Q&A efficiency     |                      |              |         |                 |
| --------------- | --------------- | -------- | ---------- | ------------------ | -------------------- | ------------ | ------- | --------------- |
| and facilitates | deeper learning | by       | accurately | addressing complex |                      |              |         |                 |
|                 |                 |          |            |                    | The system interface | is primarily | divided | into two parts: |
theoreticalquestionsinTCM. the teacher terminal and the student terminal, each presenting
functionalitiestailoredtoitsrespectiveusergroup.
3.3.3TheAutomatedTestGenerationand
| GradingModule |     |     |     |     | 3.4.1Theuserinterfaceofthestudentterminal |     |     |     |
| ------------- | --- | --- | --- | --- | ----------------------------------------- | --- | --- | --- |
The Automated Test Generation and Grading Module Figure4 shows the student interface of the Intelligent TCM
streamlinestheassessmentlifecycle,fromitemcreationtofeedback TutoringSystem,designedwithastudent-centeredphilosophy.The
delivery. Leveraging the instructional content from e-textbooks, interfaceisstructuredintothreemodulesthatmirrorthecomplete
the system uses an LLM to generate test items (including learning workflow: “Pre-class Preview,” “Learning in class,” and
questions and standard answers) relevant to specific courses and “After-class consolidation,” supporting systematic learning across
| chapters. | Instructors can | then compile | and | distribute these | tests differentstages. |     |     |     |
| --------- | --------------- | ------------ | --- | ---------------- | ---------------------- | --- | --- | --- |
via the user interface. Upon submission, the system performs The“Pre-classPreview”moduleincludesaSyllabus,Teaching
automatedgrading,includingLLM-poweredscoringofquestions Schedule, and a KG. The KG visually represents the course’s
bycomparingstudentresponsestostandardanswers.Crucially,the knowledge structure, allowing users to explore interconnected
| FrontiersinMedicine |     |     |     |     | 06  |     |     | frontiersin.org |
| ------------------- | --- | --- | --- | --- | --- | --- | --- | --------------- |

Huetal. 10.3389/fmed.2026.1943401
FIGURE4
Screenshotsfromtheimplementedstudentinterface,illustratinghowthesystemsupportslearningacrosspre-class,in-class,andafter-classstages.
(a)Thestudent-sidenavigationstructure,includingPre-classPreview,LearninginClass,andAfter-classConsolidation.(b)Theinteractiveknowledge
graph,inwhichselectinganodedisplaysitsassociatedinformation.(c)The“MyTests”moduleforcompletingassignedassessments.(d)The“Test
Analysis”reportpresentingitem-levelanswers,results,andexplanations.
concepts by clicking on nodes to retrieve detailed information, enhancement.”Itorganizestheentireteachingworkflowintofour
such as content, annotations, and related TCM formulas. This core modules: Yizong Q&A, Preparation before class, In-class
feature is designed to foster a systematic understanding. The Teaching,andAfter-classServices.
“Learning in class” module offers “My Tests” for immediate The Yizong Q&A module features an intelligent engine that
knowledge consolidation and “Test analysis” for detailed usesNLPforsemanticanalysisofqueriesabouttheGoldenMirror
feedback. The analysis function provides correct answers and ofMedicine.Itprovidestext-basedanswerslinkedtorelevantKG
rationales for incorrect responses, helping students identify nodes,enhancingresponseexplainabilityandallowingfordeeper
knowledge gaps. The “After-class consolidation” module, exploration. The “Preparation before class” module facilitates
featuring After-class Assignments and Intelligent Q&A, resource organization and planning through functions such
supports extended practice and review. While functionally as structured management of uploaded textbooks, standardized
similar to the in-class module, its pedagogical focus shifts from generation of syllabi and schedules, and KG visualization to help
formative assessment to in-depth mastery. Collectively, these instructors build a coherent knowledge framework. To enhance
integrated modules provide holistic support throughout the classroom interaction and formative assessment, the “In-class
learning process, guiding students from initial preparation to Teaching”modulesupportsautomatedgenerationofpresentation
deepconsolidation. slides from keywords, customizable in-class tests, and real-time
gradingwithfeedback.Thisenablesteacherstodynamicallyadjust
their instruction. Subsequently, the “After-class Services” module
3.4.2Theuserinterfaceoftheteacherterminal supports summative assessment and instructional refinement. It
includes tools for creating and grading homework, focusing on
The teacher terminal of our Intelligent TCM Tutoring independent practice, and features an intelligent Q&A to assist
System (Figure5) is designed based on the principles of an teachersinpreparingmaterialsorrefiningtheirteachingstrategies.
“integratedteachingprocess”and“human-computercollaborative Thisintegrateddesignprovidescomprehensivesupportacrossthe
FrontiersinMedicine 07 frontiersin.org

Huetal. 10.3389/fmed.2026.1943401
FIGURE5
Screenshotsfromtheimplementedinstructorinterface,illustratingtheteacher-facinginstructionalworkflowandknowledge-graph-linkedquestion
answering.(a)Theinstructor-sidenavigationstructureorganizedaroundPreparationbeforeclass,In-classTeaching,andAfter-classServices.(b)The
intelligentquestion-answeringmodule,inwhichgeneratedanswersincludeclickablelinkstorelevantentitiesintheknowledgegraph.(c)The
knowledge-graphvisualizationopenedbyselectingalinkedentityinthegeneratedanswer.
entireteachinglifecycle,augmentingtheinstructor’scapabilitiesat All five evaluators received the same evaluation materials
eachstage. and a standardized ARS assessment form with identical scoring
criteria and completed their assessments independently. The
ARS evaluation used a 3-point scoring scale, with higher scores
indicating better system performance. The scoring criteria are
4 Results definedasfollows.Ascoreof1indicatesthatthegeneratedcontent
iscompletelyunacceptablebecauseofseriousissuessuchasfactual
errors, incompleteness, or logical inconsistencies. A score of 2
This section outlines the experimental design for evaluating
signifies that the content is largely acceptable but requires some
system performance and the impact on student learning by
improvement. A score of 3 represents high-quality content that
comparing the Intelligent TCM Tutoring System with GLM-4-
effectivelysupportstheoverallteachingobjectives.Theevaluation
FlashwithoutKGintegration.
results are presented in Table1. For the inter-rater reliability
analysis,eachevaluator’sitem-levelscoreswereaveragedseparately
bysystemmodule,evaluatedsystem,andARSdimension,following
4.1 Evaluation of system performance the structure presented in Table1. The reliability of the mean
ratings across the five evaluators was assessed using a two-way
System performance was assessed using the Accuracy, random-effects, absolute-agreement, average-measures intraclass
Relevance,andSmoothness(ARS)evaluationmethod.FiveTCM correlation coefficient (ICC). The resulting ICC (A,5) was 0.847,
teachers with prior experience in teaching the Golden Mirror of indicatinggoodinter-raterreliability.
Medicine were selected as evaluators. None of the evaluators had The evaluation results indicated that the Intelligent TCM
participatedinthedevelopmentofthesystem. Tutoring System received higher ARS ratings than GLM-4-Flash
Theteachersassessedtheinstructionalmaterialsgeneratedby across instructional content generation, intelligent Q&A, and
the system across different modules, including the Instructional automatedtestgenerationandgrading.
Content Generation Module, the Intelligent Q&A Module, and In the Instructional Content Generation Module, the system
the Automated Test Generation and Grading Module. The five received higher ratings than GLM-4-Flash for accuracy (2.82),
teachersreviewedthegeneratedcontent,focusingoninformational relevance(2.90),andsmoothness(2.60),demonstratingitsability
accuracy, relevance to the textbook, and linguistic smoothness. topreciselygenerateteachingmaterialsthatarehighlyalignedwith
In the Instructional Content Generation Module, the generated textbookcontent.Moreover,theIntelligentTCMTutoringSystem
presentation slides were evaluated; since the native GLM-4-Flash generated structured textual content and automatically created
model cannot generate presentation slides, it was instructed to supplementary teaching materials such as presentation slides,
generateonlythetextcontentforcomparison.FortheIntelligent thereby supporting teaching efficiency. This content-generation
Q&A Module, a list of 20 questions covering the content of capability may facilitate a more systematic and complete transfer
the Golden Mirror of Medicine was prepared for evaluating the ofknowledgeduringtheteachingprocess.
generatedanswers.IntheAutomatedTestGenerationandGrading IntheIntelligentQ&AModule,theIntelligentTCMTutoring
Module,theassessmentfocusedonthegeneratedexampapersand System received consistently high ratings. Its scores for accuracy
theircorrespondingquestionanalyses. (2.77), relevance (2.82), and smoothness (2.82) were higher than
FrontiersinMedicine 08 frontiersin.org

| Huetal. |     |     |     |     |     |     |     |     |     |     |     | 10.3389/fmed.2026.1943401 |     |     |     |
| ------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ------------------------- | --- | --- | --- |
TABLE1ARSassessmentresults.
| Module |     |     |     | Model |     |     |     | Accuracy |     | Relevance |     |     | Smoothness |     |     |
| ------ | --- | --- | --- | ----- | --- | --- | --- | -------- | --- | --------- | --- | --- | ---------- | --- | --- |
TheInstructionalContentGenerationModule GLM-4-Flash 2.18 2.24 2.34
|                         |     |     |     | IntelligentTCMTutoringSystem |     |     |     |     | 2.82 |     | 2.90 |     |     | 2.60 |     |
| ----------------------- | --- | --- | --- | ---------------------------- | --- | --- | --- | --- | ---- | --- | ---- | --- | --- | ---- | --- |
| TheIntelligentQ&AModule |     |     |     | GLM-4-Flash                  |     |     |     |     | 1.76 |     | 2.13 |     |     | 2.23 |     |
|                         |     |     |     | IntelligentTCMTutoringSystem |     |     |     |     | 2.77 |     | 2.82 |     |     | 2.82 |     |
TheAutomatedTestGenerationandGrading GLM-4-Flash 1.83 1.75 2.26
Module
|     |     |     |     | IntelligentTCMTutoringSystem |     |     |     |     | 2.92 |     | 2.88 |     |     | 2.84 |     |
| --- | --- | --- | --- | ---------------------------- | --- | --- | --- | --- | ---- | --- | ---- | --- | --- | ---- | --- |
Boldvaluesindicatethehighermeanratingwithineachmoduleandevaluationcriterion.
thoseofGLM-4-Flash,indicatingitsabilitytogenerateaccurateand Thequestionnaireconsistedoffoursections.Thefirstsection
relevantresponsestoTCM-relatedquestions.Thesystemprovides collected sociodemographic information. The second section was
precise answers that conform to medical theory and are logically a scale measuring the overall learning experience, including
structured and clearly expressed, thereby reducing factual and engagement,perceiveddifficulty,andperceivedperformance.The
logicalinconsistencies.Thismayhelpstudentsobtainmorereliable thirdsection,completedonlybystudentsinGroups2and3,was
andcoherentanswersduringself-studyorwhenseekingassistance. ascaleassessingtheexperiencewiththeLLMandtheIntelligent
In the Automated Test Generation and Grading Module, the TCMTutoringSystem,coveringperceivedusefulness,easeofuse,
IntelligentTCMTutoringSystemreceivedhighratingsforaccuracy and behavioral intention to use. The fourth section comprised
(2.92), relevance (2.88), and smoothness (2.84). The system seven test questions related to the learning content, with each
generatestestquestionsbasedontheteachingcontentandsupports question worth one point. The questionnaire included attention
automated grading. It can automatically grade student answer check questions to ensure data quality. The learning-experience
sheets, potentially improving grading efficiency and supporting scale items are detailed in Table2. The questionnaire items were
consistencyintheprocess. translated into Chinese by the research team and contextually
Overall,theexpertratingsindicatedthattheIntelligentTCM adapted to refer to the learning content and systems used in the
| Tutoring | System | produced | accurate, | relevant, | and fluent | outputs | presentstudy. |     |     |     |     |     |     |     |     |
| -------- | ------ | -------- | --------- | --------- | ---------- | ------- | ------------- | --- | --- | --- | --- | --- | --- | --- | --- |
across the evaluated modules. In this TCM setting, the system Internal consistency was assessed using the final analyzed
generated instructional content, provided question-answering sample for each applicable scale. Cronbach’s alpha values for all
multi-itemscalesarereportedinTable2(n=102forengagement
support,andcreatedandgradedtestitems.Thesefindingssupport
thesystem’spotentialasasupplementarytoolforstudentlearning and understanding; n = 68 for usefulness, ease of use, and
andinstructor-ledteaching. intentiontouse,whichwereadministeredonlytoGroups2and3).
|     |     |     |     |     |     |     | Cronbach’s | alpha | was | not applicable |     | to the | single-item | measures. |     |
| --- | --- | --- | --- | --- | --- | --- | ---------- | ----- | --- | -------------- | --- | ------ | ----------- | --------- | --- |
Constructvaliditywasnotassessedthroughfactoranalysisinthe
| 4.2 Evaluation |     | of student |     | learning |     |     | currentstudy. |            |     |               |     |      |      |             |     |
| -------------- | --- | ---------- | --- | -------- | --- | --- | ------------- | ---------- | --- | ------------- | --- | ---- | ---- | ----------- | --- |
|                |     |            |     |          |     |     | After         | collecting | the | questionnaire |     | data | from | all groups, | we  |
effectiveness
conductedastatisticalanalysisofthedifferencesamongthem.For
|     |     |     |     |     |     |     | comparisons |     | involving | the three | groups, | the | Kruskal–Wallis |     | H-  |
| --- | --- | --- | --- | --- | --- | --- | ----------- | --- | --------- | --------- | ------- | --- | -------------- | --- | --- |
To investigate the impact on student learning, we recruited test was used to assess overall differences, followed by pairwise
| 125 volunteers |     | from Anhui     | University | of          | Chinese Medicine |        |             |         |          |            |            |          |              |     |         |
| -------------- | --- | -------------- | ---------- | ----------- | ---------------- | ------ | ----------- | ------- | -------- | ---------- | ---------- | -------- | ------------ | --- | ------- |
|                |     |                |            |             |                  |        | comparisons |         | with a   | Bonferroni | correction |          | to control   |     | for the |
| to participate | in  | an experiment. | After      | recruitment | and              | before |             |         |          |            |            |          |              |     |         |
|                |     |                |            |             |                  |        | risk        | of Type | I errors | associated | with       | multiple | comparisons. |     | For     |
the learning session, a researcher randomly allocated the 125 comparisons involving only two groups, the Mann–Whitney U-
participantstothethreestudygroupsbydrawinglots,resultingin
|     |     |     |     |     |     |     | test was | employed | for | non-parametric |     | statistical | analysis. |     | A two- |
| --- | --- | --- | --- | --- | --- | --- | -------- | -------- | --- | -------------- | --- | ----------- | --------- | --- | ------ |
initialgroupsizesof43,41,and41,respectively.Groupassignments sided p-value below 0.05 was considered statistically significant.
| remained   | concealed | until       | each lot     | was drawn, | preventing   | the |           |          |          |                |        |          |         |               |     |
| ---------- | --------- | ----------- | ------------ | ---------- | ------------ | --- | --------- | -------- | -------- | -------------- | ------ | -------- | ------- | ------------- | --- |
|            |           |             |              |            |              |     | This      | design   | aimed to | systematically |        | evaluate | the     | effectiveness | of  |
| researcher | from      | influencing | or selecting | group      | assignments. | All |           |          |          |                |        |          |         |               |     |
|            |           |             |              |            |              |     | different | teaching | methods  | and            | inform | the      | further | optimization  |     |
threegroupsstudiedthecontentofVolume26oftheGoldenMirror of the Intelligent TCM Tutoring System. Given the non-normal
| of Medicine. | Group | 1 was | provided | with no | Q&A support | and |              |     |              |      |       |           |         |         |     |
| ------------ | ----- | ----- | -------- | ------- | ----------- | --- | ------------ | --- | ------------ | ---- | ----- | --------- | ------- | ------- | --- |
|              |       |       |          |         |             |     | distribution |     | of the data, | this | study | primarily | reports | medians |     |
reliedentirelyonself-study.Group2wasprovidedwithanLLM and interquartile ranges (IQRs) to more accurately reflect the
forQ&A,alongwithreviewquestionsandsolutionsgeneratedby
|     |     |     |     |     |     |     | data’s | central | tendency | and dispersion. |     | Additionally, |     | to  | provide |
| --- | --- | --- | --- | --- | --- | --- | ------ | ------- | -------- | --------------- | --- | ------------- | --- | --- | ------- |
theLLM.Group3wasprovidedwiththeIntelligentTCMTutoring
|     |     |     |     |     |     |     | a comprehensive |     | overview |     | of the | data, | means | and standard |     |
| --- | --- | --- | --- | --- | --- | --- | --------------- | --- | -------- | --- | ------ | ----- | ----- | ------------ | --- |
System,whichintegratesanLLMwithaKGforQ&A,alongwith deviations (SDs) are also reported. Effect sizes were reported
corresponding review questions and solutions. After completing (ε2)
|     |     |     |     |     |     |     | as epsilon-squared |     |     | for | Kruskal–Wallis |     | tests | and | rank- |
| --- | --- | --- | --- | --- | --- | --- | ------------------ | --- | --- | --- | -------------- | --- | ----- | --- | ----- |
thelearningsession,students’learningoutcomesandexperiences biserial correlation r for Mann–Whitney U-tests. The 95%
rb
wereassessedviaaquestionnairefeaturingscalesadaptedfromthe
|     |     |     |     |     |     |     | confidence | intervals | (CIs) | for | effect | sizes | were estimated |     | using |
| --- | --- | --- | --- | --- | --- | --- | ---------- | --------- | ----- | --- | ------ | ----- | -------------- | --- | ----- |
workofPengetal.(40).
|                     |     |     |     |     |     |     | a non-parametric |     | percentile |     | bootstrap | with | 10,000 | resamples       |     |
| ------------------- | --- | --- | --- | --- | --- | --- | ---------------- | --- | ---------- | --- | --------- | ---- | ------ | --------------- | --- |
| FrontiersinMedicine |     |     |     |     |     |     | 09               |     |            |     |           |      |        | frontiersin.org |     |

| Huetal. |     |     |     |     |     |     | 10.3389/fmed.2026.1943401 |     |     |
| ------- | --- | --- | --- | --- | --- | --- | ------------------------- | --- | --- |
TABLE2Questionnairesusedinthestudy.
|     |     | performed     | separately | within       | each | group. | Two-sided |       | p-values  |
| --- | --- | ------------- | ---------- | ------------ | ---- | ------ | --------- | ----- | --------- |
|     |     | were reported |            | numerically, | with | values | below     | 0.001 | presented |
Measurement Items
|     |     | in scientific | notation; | pairwise | p-values |     | following | Kruskal–Wallis |     |
| --- | --- | ------------- | --------- | -------- | -------- | --- | --------- | -------------- | --- |
Perceived Engagement(Cronbach’sα=0.796)Duringthis testswereBonferroni-adjusted.Anapproximatesensitivityanalysis
engagement learningsession,Iwashighlyfocusedonlearningthe based on the final group sizes (34, 39, and 29), a two-sided
α
GoldenMirrorofMedicine.Duringthislearningsession,I of 0.05, and 80% power indicated minimum detectable effect
|     |     | sizes of | ε2 = | 0.097 for | the three-group |     | comparisons |     | and r |
| --- | --- | -------- | ---- | --------- | --------------- | --- | ----------- | --- | ----- |
wassoabsorbedinlearningtheGoldenMirrorof rb
=
MedicinethatIlosttrackoftime.Duringthislearning 0.400 for the two-group comparisons involving Groups 2
and3.
session,Iinvestedasignificantamountofeffortin
learningtheGoldenMirrorofMedicine. Wetestedthefollowinghypotheses:
Perceiveddifficulty Duringthislearningsession,Ifounditverydifficultto
|     |     | • H1: | Learning | outcomes. | H1a: | Post-test | scores | do  | not differ |
| --- | --- | ----- | -------- | --------- | ---- | --------- | ------ | --- | ---------- |
understandthecontentoftheGoldenMirrorofMedicine.
|     |     | significantly |     | among | the three | groups. | H1b: | Post-test | scores |
| --- | --- | ------------- | --- | ----- | --------- | ------- | ---- | --------- | ------ |
Understanding(Cronbach’sα=0.951)Afterthis
Perceived differsignificantlyamongthethreegroups,withtheIntelligent
performance learningsession,Iamabletogainanin-depth
|     |     | TCM | Tutoring | System | group | expected |     | to achieve | higher |
| --- | --- | --- | -------- | ------ | ----- | -------- | --- | ---------- | ------ |
understandingoftheknowledgeintheGoldenMirrorof scoresthantheothergroups.
Medicineandanalyzeitspracticalapplications.Afterthis • H2: Learning experience. H2a: Learning-experience ratings
learningsession,Iamabletoclearlyarticulatethekey do not differ significantly across the measured dimensions
knowledgeintheGoldenMirrorofMedicineinmyown amongthethreegroups.H2b:TheIntelligentTCMTutoring
wordsandexplainitsunderlyinglogic.Afterthislearning System group is expected to report more favorable ratings
session,Iamabletoidentifyareasforfurtherstudy than both comparison groups for engagement, perceived
|     |     | difficulty, |     | and perceived | understanding. |     |     | It is also | expected |
| --- | --- | ----------- | --- | ------------- | -------------- | --- | --- | ---------- | -------- |
withintheGoldenMirrorofMedicineanddeepenmy
understandingofitusinglearningtools. toreportmorefavorableratingsforfrequency,interruption,
perceivedusefulness,usability,andacceptancethantheLLM-
Frequency IfrequentlyusedtheIntelligentTCMTutoringSystemto
supportmystudyoftheGoldenMirrorofMedicine. assistedgroup.
Interruption IfoundthattheIntelligentTCMTutoringSystem
|     |     | During | the | data | cleaning | process, |     | we excluded | 23  |
| --- | --- | ------ | --- | ---- | -------- | -------- | --- | ----------- | --- |
interruptedmylearningprocess.
|     |     | questionnaires |     | that failed | attention | checks | or  | exhibited | careless |
| --- | --- | -------------- | --- | ----------- | --------- | ------ | --- | --------- | -------- |
Usefulness(Cronbach’sα=0.945)UsingtheIntelligent
| Technology |     | completion,yieldingafinalsampleof102. |     |     |     |     |     |     |     |
| ---------- | --- | ------------------------------------- | --- | --- | --- | --- | --- | --- | --- |
acceptance TCMTutoringSystemenablesmetounderstandthe
knowledgeintheGoldenMirrorofMedicineata
deeperlevel.UsingtheIntelligentTCMTutoringSystem
4.2.1Descriptivestatisticalanalysis
enhancesmyabilitytomastertheknowledgeinthe
GoldenMirrorofMedicine.UsingtheIntelligentTCM
|     |     | Table3 | presents | the | demographic |     | characteristics |     | and prior |
| --- | --- | ------ | -------- | --- | ----------- | --- | --------------- | --- | --------- |
TutoringSystemmademylearningoftheGoldenMirror
learningexperienceofthe102participantsincludedintheanalysis
ofMedicinemoreefficient.IfindtheIntelligentTCM
acrossthethreegroups,includingsex,age,major,andpriorstudy
TutoringSystemhighlyusefulformystudyoftheGolden
oftheGoldenMirrorofMedicine.
MirrorofMedicine.
|     |     | Group-level |     | comparisons | of  | learning | outcomes | and | learning |
| --- | --- | ----------- | --- | ----------- | --- | -------- | -------- | --- | -------- |
Easeofuse(Cronbach’sα=0.924)IfindtheIntelligent
|     |     | experiences | are | summarized | in  | Tables4–6 |     | and visualized | in  |
| --- | --- | ----------- | --- | ---------- | --- | --------- | --- | -------------- | --- |
TCMTutoringSystemflexibletointeractwith.Ifindmy Figure6.
interactionwiththeIntelligentTCMTutoringSystemto
beclearandstraightforward.UsingtheIntelligentTCM
TutoringSystemtoaidmystudyoftheGoldenMirrorof
4.2.2Learningoutcomes
Medicinedoesnotrequiresignificantmentaleffort.Ifind
iteasytoaccomplishmylearningtasksusingthe
IntelligentTCMTutoringSystem. Table4presentsthelearningoutcomescoresforthreegroups
|     |     | employing | different | learning | methods. |     | The self-directed |     | learning |
| --- | --- | --------- | --------- | -------- | -------- | --- | ----------------- | --- | -------- |
Intentiontouse(Cronbach’sα=0.912)Ifthe
|     |     | group (Group |     | 1) had a | median | score | of 2.50 | (IQR | = 4.00), a |
| --- | --- | ------------ | --- | -------- | ------ | ----- | ------- | ---- | ---------- |
IntelligentTCMTutoringSystemwereavailableto
meanof3.21,andastandarddeviationof2.25.TheLLM-assisted
supportmyin-depthstudyoftheGoldenMirrorof =
|     |     | group (Group | 2)  | had a median |     | of 4.00 | (IQR | 2.00), | a mean of |
| --- | --- | ------------ | --- | ------------ | --- | ------- | ---- | ------ | --------- |
Medicine,Iwoulduseit.Inmyfuturestudiesofthe 3.82,andastandarddeviationof1.67.Incontrast,theIntelligent
GoldenMirrorofMedicineorotherTraditionalChinese
|     |     | TCM Tutoring |     | System group | (Group |     | 3) had | a median | of 6.00 |
| --- | --- | ------------ | --- | ------------ | ------ | --- | ------ | -------- | ------- |
=
Medicinecontent,IplantousetheIntelligentTCM (IQR 2.00), a mean of 5.52, and a standard deviation of 1.46.
TutoringSystemextensively. Statistical analysis revealed that the differences between Group 3
Allitemsweremeasuredona7-pointLikertscale(1=StronglyDisagree;7=Strongly and both Group 1 and Group 2 were significant, with Group 3
Agree). In the questionnaire, “intelligent teaching system” was used as an abbreviated demonstratingsignificantlyhigherlearningoutcomesthanGroup
referencetotheIntelligentTCMTutoringSystem.ForstudentsinGroup2,thistermwas = × −5
|                                                                                   |     | 1 and Group | 2     | (Bonferroni-adjusted |     |     | p 2.17 | 10  | and p |
| --------------------------------------------------------------------------------- | --- | ----------- | ----- | -------------------- | --- | --- | ------ | --- | ----- |
| correspondinglychangedto“LLM”.Boldtextindicatesmulti-itemscalesandtheirCronbach’s |     | =           | × −4, |                      |     |     |        |     |       |
alphacoefficients. 9.31 10 respectively). However, the difference between
| FrontiersinMedicine | 10  |     |     |     |     |     |     | frontiersin.org |     |
| ------------------- | --- | --- | --- | --- | --- | --- | --- | --------------- | --- |

Huetal. 10.3389/fmed.2026.1943401
TABLE3Participantcharacteristicsacrossexperimentalgroups.
Characteristic Category Group1(n=34) Group2(n=39) Group3(n=29) Total(N=102)
Sex Male 28(82.4%) 30(76.9%) 21(72.4%) 79(77.5%)
Female 6(17.6%) 9(23.1%) 8(27.6%) 23(22.5%)
Age 18–25years 24(70.6%) 29(74.4%) 22(75.9%) 75(73.5%)
26–30years 10(29.4%) 10(25.6%) 7(24.1%) 27(26.5%)
Major TCM 8(23.5%) 14(35.9%) 8(27.6%) 30(29.4%)
Non-TCM 26(76.5%) 25(64.1%) 21(72.4%) 72(70.6%)
PriorstudyoftheGolden Yes 10(29.4%) 10(25.6%) 9(31.0%) 29(28.4%)
MirrorofMedicine
No 24(70.6%) 29(74.4%) 20(69.0%) 73(71.6%)
Valuesarepresentedasn(%),withpercentagescalculatedwithineachgroup.
Group1andGroup2wasnotstatisticallysignificant(Bonferroni- TABLE4Learningoutcomesbygroup.
adjusted p = 0.861). These findings indicate that, in this single-
Groups Learningoutcomes
session evaluation, the Intelligent TCM Tutoring System group
achievedhigherpost-testscoresthantheself-directedlearningand Self-directedlearning 2.50(4.00)
LLM-assistedgroups. 3.21±2.25
These findings support H1b: post-test scores differed
LLM-assistedlearning 4.00(2.00)
significantly among the three groups, and the Intelligent TCM
3.82±1.67
Tutoring System group achieved higher scores than the other
groups.Accordingly,H1awasnotsupported. IntelligentTCMTutoring 6.00(2.00)
System-assisted
5.52±1.46
4.2.3Learningexperience
Median(IQR).Mean±SD.(∗∗p<0.01,∗∗∗p<0.001).Exactnumericalp-valuesarereported
inTable6.Boldvaluesindicatethehighestdescriptivescoresamongthethreegroups.
Table5 presents the evaluation results of the learning
experienceacrossdifferentgroups,coveringmultipledimensions: difficulty ratings than Group 1 (p = 7.19 × 10 −11) and Group 2
Engagement, Difficulty, Understanding, Frequency, Interruption, (p=4.77×10 −5).ThedifferencebetweenGroup1andGroup2
Usefulness, Usability, and Acceptance. For the dimensions of wasalsosignificant(p=0.0217).
Engagement, Difficulty, and Understanding, which involved For Understanding, the Intelligent TCM Tutoring System
comparisons among three groups, the Kruskal–Wallis test was group scored 6.33 (IQR = 1.00), compared with 2.67 (IQR =
employed to analyze overall differences, followed by post-hoc 2.33)forGroup1and4.33(IQR=1.33)forGroup2.Significant
pairwisecomparisonswithBonferronicorrection;thereportedp- differences were observed among the three groups (Kruskal–
valuesareBonferroni-corrected.Fortheotherdimensions,which Wallistest,p=6.33×10 −12;ε2 =0.501,95%CI:0.353–0.666).
involvedcomparisonsbetweenGroups2and3,theMann–Whitney Bonferroni-adjusted pairwise comparisons showed that Group 3
U-testwasused. hadsignificantlyhigherunderstandingratingsthanGroup1(p=
IntermsofEngagement,theIntelligentTCMTutoringSystem 4.12 × 10 −12) and Group 2 (p = 2.75 × 10 −6). The difference
group (Group 3) scored 5.67 (IQR = 0.67), compared with 3.33 betweenGroup1andGroup2wasalsosignificant(p=0.0368).
(IQR = 1.58) for the self-directed learning group (Group 1) and ForthedimensionsadministeredonlytoGroups2and3,the
4.33 (IQR = 1.33) for the LLM-assisted group (Group 2). The Mann–WhitneyU-testsshowedthattheIntelligentTCMTutoring
Kruskal–Wallis test indicated significant differences among the System group reported more favorable ratings than the LLM-
threegroups(p=3.41×10 −8;ε2=0.327,95%CI:0.196–0.500). assisted group for frequency [6.00 (IQR = 1.00) vs. 5.00 (IQR =
Bonferroni-adjusted pairwise comparisons showed that Group 3 2.00)], interruption [1.00 (IQR = 1.00) vs. 4.00 (IQR = 3.00)],
hadsignificantlyhigherengagementratingsthanGroup1(p=7.15 usefulness[6.50(IQR=0.75)vs.4.75(IQR=1.25)],usability[6.25
×10 −8)andGroup2(p=1.27×10 −5),whereasnosignificant (IQR=1.00)vs.4.50(IQR=1.00)],andacceptance[7.00(IQR=
differencewasobservedbetweenGroup1andGroup2(p=0.682). 0.50)vs.4.50(IQR=1.50)].Effectsizesandexactp-valuesforthese
Regarding Difficulty, the Intelligent TCM Tutoring System comparisonsaresummarizedinTable6.
group had the lowest score (2.00, IQR = 2.00), compared with Insummary,thestatisticalanalysisresultssupportHypothesis
the LLM-assisted group (4.00, IQR = 2.00) and the self-directed H2b: the Intelligent TCM Tutoring System group reported more
learninggroup(6.00,IQR=2.00).TheKruskal–Wallistestshowed
favorable ratings than both comparison groups for engagement,
significantdifferencesamongthethreegroups(p=1.58×10 −10;
difficulty,andunderstanding,andthantheLLM-assistedgroupfor
ε2 = 0.436, 95% CI: 0.280–0.613). Bonferroni-adjusted pairwise frequency, interruption, usefulness, usability, and acceptance. In
comparisons indicated that Group 3 reported significantly lower thissingle-sessionevaluation,theIntelligentTCMTutoringSystem
FrontiersinMedicine 11 frontiersin.org

| Huetal. |     |     |     |     |     |     |     |     |     | 10.3389/fmed.2026.1943401 |     |     |
| ------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ------------------------- | --- | --- |
group reported more favorable post-session learning-experience this domain grounding across an integrated instructional
ratings within the applicable group comparisons. Effect sizes for workflow encompassing content generation, intelligent question
the learning-outcome and learning-experience comparisons are answering, assessment, grading, and feedback, rather than
summarizedinTable6. limiting KG support to a single educational task. Accordingly,
|     |     |     |     |     |     | this study  | contributes  |     | a domain-specific, |           | human-validated |            |
| --- | --- | --- | --- | --- | --- | ----------- | ------------ | --- | ------------------ | --------- | --------------- | ---------- |
|     |     |     |     |     |     | LLM–KG      | framework    | and | provides           | empirical | evidence        | of its     |
|     |     |     |     |     |     | application | in classical | TCM | education.         | The       | internal        | comparison |
5 Discussion
|             |               |              |          |               |     | with GLM-4-Flash     |          | without   | KG  | integration     | further | provides      |
| ----------- | ------------- | ------------ | -------- | ------------- | --- | -------------------- | -------- | --------- | --- | --------------- | ------- | ------------- |
|             |               |              |          |               |     | context-specific     | evidence | regarding |     | the educational |         | value of this |
| Inspired by | the principle | of “teaching | students | in accordance |     | integratedframework. |          |           |     |                 |         |               |
with their aptitude,” this study examined how an integrated The system’s performance was assessed using the ARS
LLM–KG system can provide learner-responsive support in evaluation method. For the experiment, 125 student volunteers
TCM education. The system combines language generation with wererecruitedfromAnhuiUniversityofChineseMedicine.This
structuredTCMknowledgetoprovideKG-groundedexplanations experiment investigated the effects of three different learning
|     |     |     |     |     |     | modalities—self-directed |     |     | learning, | LLM-assisted |     | learning, and |
| --- | --- | --- | --- | --- | --- | ------------------------ | --- | --- | --------- | ------------ | --- | ------------- |
inresponsetostudents’queriesandgeneratefeedbackonsubmitted
answers. In the present implementation, adaptation is initiated learning with the Intelligent TCM Tutoring System based on the
throughlearnerinteractionratherthanthroughanexplicitlearner LLMandKG—onstudents’learningoutcomesandexperiences.A
detailedanalysisofeachgroup’sperformancewasthenconducted.
modelorautomatedlongitudinallearning-pathoptimization.
Existing educational AI systems provide support through To evaluatesystemperformance, theARSevaluation method
|                       |          |            |         |          |     | was employed | to  | compare | the Intelligent | TCM | Tutoring | System |
| --------------------- | -------- | ---------- | ------- | -------- | --- | ------------ | --- | ------- | --------------- | --- | -------- | ------ |
| different mechanisms: | Khanmigo | emphasizes | guided, | inquiry- |     |              |     |         |                 |     |          |        |
based interaction (28), GPT-based tools in medical education with GLM-4-Flash (without KG integration) across several
have been used for specific tasks such as standardized-patient modules: instructional content generation, intelligent Q&A, and
|                  |                         |     |         |      |     | automated | test generation |     | and | grading. | The results | indicated |
| ---------------- | ----------------------- | --- | ------- | ---- | --- | --------- | --------------- | --- | --- | -------- | ----------- | --------- |
| simulation (26), | and retrieval-augmented |     | systems | such | as  |           |                 |     |     |          |             |           |
MedTutor (41) generate case-based materials from retrieved that the Intelligent TCM Tutoring System received higher ARS
|                   |             |     |                       |     |     | ratings than | GLM-4-Flash |     | across | all evaluated | modules. | In the |
| ----------------- | ----------- | --- | --------------------- | --- | --- | ------------ | ----------- | --- | ------ | ------------- | -------- | ------ |
| medical evidence. | In contrast | to  | these general-purpose |     | or  |              |             |     |        |               |          |        |
task-specific applications, the present system incorporates a Instructional Content Generation Module, the system received
human-validatedKGderivedfromtheGoldenMirrorofMedicine, higher ratings for accuracy, relevance, and smoothness. The
systemgeneratedinstructionalcontentalignedwiththetextbooks
| in which explicit | relationships | among | diseases, | symptoms, |     |     |     |     |     |     |     |     |
| ----------------- | ------------- | ----- | --------- | --------- | --- | --- | --- | --- | --- | --- | --- | --- |
formulas,andmedicinalssupportstructuredknowledgeretrieval, and also created supplementary teaching materials, such as
|              |                 |               |     |         |         | presentation | slides, | which | may support | instructional |     | efficiency. |
| ------------ | --------------- | ------------- | --- | ------- | ------- | ------------ | ------- | ----- | ----------- | ------------- | --- | ----------- |
| exploration, | and node-linked | explanations. | It  | further | extends |              |         |       |             |               |     |             |
TABLE5Learningexperiencebygroup.
| Groups                |     |            |     |     |     | Learningexperience |     |               |            |     |     |           |
| --------------------- | --- | ---------- | --- | --- | --- | ------------------ | --- | ------------- | ---------- | --- | --- | --------- |
|                       |     | Engagement |     |     |     | Difficulty         |     | Understanding |            |     |     | Frequency |
| Self-directedlearning |     | 3.33(1.58) |     |     |     | 6.00(2.00)         |     |               | 2.67(2.33) |     |     | —         |
|                       |     | 3.81±1.69  |     |     |     | 5.62±1.72          |     |               | 3.13±1.69  |     |     |           |
LLM-assistedlearning 4.33(1.33) 4.00(2.00) 4.33(1.33) 5.00(2.00)
|     |     | 4.27±0.95 |     |     |     | 4.44±1.29 |     |     | 4.27±0.86 |     |     | 4.92±1.04 |
| --- | --- | --------- | --- | --- | --- | --------- | --- | --- | --------- | --- | --- | --------- |
IntelligentTCMTutoring 5.67(0.67) 2.00(2.00) 6.33(1.00) 6.00(1.00)
System-assisted
|                       |     | 5.71±0.69    |     |     |     | 2.31±1.42          |     |     | 6.09±0.73 |     |     | 6.38±0.68  |
| --------------------- | --- | ------------ | --- | --- | --- | ------------------ | --- | --- | --------- | --- | --- | ---------- |
| Groups                |     |              |     |     |     | Learningexperience |     |     |           |     |     |            |
|                       |     | Interruption |     |     |     | Usefulness         |     |     | Usability |     |     | Acceptance |
| Self-directedlearning |     |              | —   |     |     | —                  |     |     | —         |     |     | —          |
LLM-assistedlearning 4.00(3.00) 4.75(1.25) 4.50(1.00) 4.50(1.50)
|     |     | 3.46±1.59 |     |     |     | 4.72±0.98 |     |     | 4.47±0.96 |     |     | 4.82±1.09 |
| --- | --- | --------- | --- | --- | --- | --------- | --- | --- | --------- | --- | --- | --------- |
IntelligentTCMTutoring 1.00(1.00) 6.50(0.75) 6.25(1.00) 7.00(0.50)
System
|     |     | 1.45±0.99 |     |     | 6.53±0.41 |     |     |     | 6.16±0.65 |     |     | 6.69±0.36 |
| --- | --- | --------- | --- | --- | --------- | --- | --- | --- | --------- | --- | --- | --------- |
Adash(—)indicatesthataquestionwasnotadministeredunderthecorrespondingcondition.Median(IQR).Mean±SD.(∗p<0.05,∗∗∗p<0.001).OveralldifferencesfortheEngagement,
Difficulty,andUnderstandingcolumnswereassessedusingtheKruskal–Wallistest,followedbypairwisecomparisonswithBonferroni-correctedp-values.TheMann–WhitneyU-testwasused
forallothercolumns.Boldvaluesindicatethemostfavorabledescriptivescoresforeachoutcome;lowerscoresindicatemorefavorableresultsfordifficultyandinterruption.
| FrontiersinMedicine |     |     |     |     |     | 12  |     |     |     |     |     | frontiersin.org |
| ------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --------------- |

| Huetal. |     |     |     |     |     |     |     | 10.3389/fmed.2026.1943401 |     |     |     |
| ------- | --- | --- | --- | --- | --- | --- | --- | ------------------------- | --- | --- | --- |
TABLE6Effectandp-valuesforgroupcomparisons.
|         |             |            |         | students  | in the    | system group | reported | higher         |     | engagement | and    |
| ------- | ----------- | ---------- | ------- | --------- | --------- | ------------ | -------- | -------------- | --- | ---------- | ------ |
|         |             |            |         | perceived | knowledge | mastery,     | fewer    | interruptions, |     | and        | higher |
| Outcome | Comparison/ | Effectsize | p-value |           |           |              |          |                |     |            |        |
usefulness,ease-of-use,andintention-to-useratings.Thesefindings
|     | test | (95%CI) |     |     |     |     |     |     |     |     |     |
| --- | ---- | ------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
indicateamorefavorableimmediatelearningexperienceduringthe
|     |     | ε2=0.201(95% | p=1.74× |     |     |     |     |     |     |     |     |
| --- | --- | ------------ | ------- | --- | --- | --- | --- | --- | --- | --- | --- |
Learning Three-group evaluatedactivitybutdonotestablishsustainedengagement.The
outcome Kruskal–Wallis CI:0.083,0.377) 10−5 LLM-assistedgroupperformedwellonsomedimensions,suchas
engagementandcomprehension,butitsoverallpost-sessionratings
| Engagement |     | ε2=0.327(95% | p=3.41× |                                                          |     |     |     |     |     |     |     |
| ---------- | --- | ------------ | ------- | -------------------------------------------------------- | --- | --- | --- | --- | --- | --- | --- |
|            |     |              | 10−8    | didnotexceedthoseoftheIntelligentTCMTutoringSystemgroup. |     |     |     |     |     |     |     |
CI:0.196,0.500)
OnepossibleexplanationisthestandaloneLLM’slackofdomain-
|     |     | ε2=0.436(95% | p=1.58× |     |     |     |     |     |     |     |     |
| --- | --- | ------------ | ------- | --- | --- | --- | --- | --- | --- | --- | --- |
Difficulty
|               |     |                 |         | specific knowledge |     | support;    | integrating | the      | LLM | with a   | KG may |
| ------------- | --- | --------------- | ------- | ------------------ | --- | ----------- | ----------- | -------- | --- | -------- | ------ |
|               |     | CI:0.280,0.613) | 10−10   |                    |     |             |             |          |     |          |        |
|               |     |                 |         | have contributed   |     | to the more | favorable   | outcomes |     | observed | after  |
| Understanding |     | ε2=0.501(95%    | p=6.33× | theactivity.       |     |             |             |          |     |          |        |
10−12
CI:0.353,0.666) Overall, the results of this single-session evaluation support
Frequency Group3vsGroup rrb =0.747(95% p=5.61× Hypotheses H1b and H2b: the Intelligent TCM Tutoring System
10−8
2,Mann–Whitney CI:0.576,0.889) group achieved higher immediate post-test scores and reported
U more favorable post-session learning-experience ratings than the
|              |     |             |         | comparison | groups. | These | findings | provide | preliminary |     | evidence |
| ------------ | --- | ----------- | ------- | ---------- | ------- | ----- | -------- | ------- | ----------- | --- | -------- |
| Interruption |     | rrb =−0.708 | p=2.67× |            |         |       |          |         |             |     |          |
(95%CI:−0.878, 10−7 of the system’s short-term educational value in this setting
|     |     |     |     | and should | not | be interpreted |     | as evidence |     | of sustained | or  |
| --- | --- | --- | --- | ---------- | --- | -------------- | --- | ----------- | --- | ------------ | --- |
−0.508)
|            |     |                |         | long-term  | effectiveness. | Furthermore,  |        | the     | system | performance     |     |
| ---------- | --- | -------------- | ------- | ---------- | -------------- | ------------- | ------ | ------- | ------ | --------------- | --- |
| Usefulness |     | rrb =0.877(95% | p=6.65× |            |                |               |        |         |        |                 |     |
|            |     |                |         | evaluation | also           | showed higher | expert | ratings | for    | the Intelligent |     |
10−10
CI:0.744,0.976) TCM Tutoring System in its modules for instructional content
|     |     | =0.872(95% | p=8.91× |     |     |     |     |     |     |     |     |
| --- | --- | ---------- | ------- | --- | --- | --- | --- | --- | --- | --- | --- |
Usability rrb generation, intelligent question-answering, and automated test
CI:0.742,0.972) 10−10 generation and grading, supporting its potential application
Acceptance rrb =0.825(95% p=4.08× in TCM education. Together, these functions indicate that
CI:0.663,0.954) 10−9 knowledge-grounded,learner-responsivesupportcansupplement
theinstructor’sguidingrole.
CI,confidenceinterval;ε2,epsilon-squared;rrb,rank-biserialcorrelation.Positiverrbvalues
indicatehigherscoresinGroup3thanGroup2,whereasnegativevaluesindicatelower
scoresinGroup3.Forthree-groupcomparisons,p-valuesrepresentKruskal–WallisH-tests;
Bonferroni-adjustedpairwisecomparisonsaredescribedintheResultssection.
|                    |             |                 |              | 6 Limitations |     | and | future | directions |     |     |     |
| ------------------ | ----------- | --------------- | ------------ | ------------- | --- | --- | ------ | ---------- | --- | --- | --- |
| In the Intelligent | Q&A Module, | the Intelligent | TCM Tutoring |               |     |     |        |            |     |     |     |
System received higher expert ratings for accuracy, relevance, 6.1 Limitations
| and smoothness, | indicating | better performance | in generating |     |     |     |     |     |     |     |     |
| --------------- | ---------- | ------------------ | ------------- | --- | --- | --- | --- | --- | --- | --- | --- |
precise and coherent responses. Furthermore, in the Automated Despite the positive findings of this study, several limitations
Test Generation and Grading Module, the Intelligent TCM shouldbeacknowledged.First,thesensitivityanalysischaracterized
TutoringSystemalsoreceivedhigherexpertratingsforaccuracy, the minimum detectable effect sizes under the final group sizes;
relevance, and smoothness across both test-item generation and however, the modest sample size may have limited the detection
automatedgrading. of smaller group differences. More broadly, this study provides
Regarding student learning outcomes, the results for preliminaryempiricalevidenceonanintegratedLLM–KGtutoring
Hypothesis H1 showed that the Intelligent TCM Tutoring systeminadefinedTCMeducationalcontext;however,theexternal
System group achieved significantly higher immediate post-test validity of these findings remains bounded by the study setting.
scores than the self-directed learning and LLM-assisted groups. TheevaluationwasconductedatasingleChineseuniversity,used
Thesefindingsindicatebetterknowledgemasteryimmediatelyafter theGoldenMirrorofMedicineasthesoledomainsourcetext,and
thelearningactivitybutdonotestablishsustainedimprovementin examinedasystembasedononeunderlyingLLM(GLM-4-Flash).
academic performance. Within this activity, the Intelligent TCM Accordingly, the findings should not be assumed to generalize
Tutoring System provided structured, domain-specific learning directly to other institutions, healthcare disciplines, cultural or
support.AlthoughtheLLM-assistedgroupscoredhigherthanthe linguisticsettings,instructionalsources,orAImodels.
self-directed learning group, the difference was not statistically Second, learning outcomes and experiences were assessed
significant,suggestingthatstandaloneLLMsupportmaybelimited only after a single learning session, and no delayed follow-
whenstructuredandspecializedknowledgesupportisabsent. up was conducted. Consequently, the study cannot determine
In terms of learning experience, the results for Hypothesis long-term knowledge retention, sustained engagement, transfer
H2 showed that the Intelligent TCM Tutoring System group to clinical or academic practice, or effectiveness over a longer
reportedsignificantlymorefavorablepost-sessionratingsthanboth educational period. Although major and prior study of the
comparisongroupsforengagement,difficulty,andunderstanding. Golden Mirror of Medicine were available as limited indicators of
Forfrequency,interruption,usefulness,usability,andacceptance, TCM-related background, prior AI or LLM use, digital literacy,
the system group reported significantly more favorable ratings academic performance, and broader TCM knowledge were not
than the LLM-assisted group. In this post-session assessment, measured;residualconfoundingbythesecharacteristicstherefore
| FrontiersinMedicine |     |     |     | 13  |     |     |     |     |     | frontiersin.org |     |
| ------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --------------- | --- |

Huetal. 10.3389/fmed.2026.1943401
FIGURE6
Groupcomparisonsoflearningoutcomesandlearningexperiences.(a)Individualpost-testscoresfortheself-directedlearning(n=34),
LLM-assistedlearning(n=39),andIntelligentTCMTutoringSystem-assisted(n=29)groups;boxesshowmediansandinterquartileranges,whiskers
extendto1.5timestheinterquartilerange,andpointsrepresentindividualparticipants.(b)Median(interquartilerange)scoresforengagement,
difficulty,andunderstandingacrossthethreegroups.(c)Median(interquartilerange)scoresforfrequency,interruption,usefulness,usability,and
acceptanceinGroups2and3.Dashedlinesinpanelsbandcindicatethemidpointofthe1–7responsescale.Lowerscoresindicatemorefavorable
experiencesfordifficultyandinterruption.
cannot be excluded. The construct validity of the adapted longer-termfollow-upinreal-worldinstructionalsettingsarealso
questionnaire was not independently established in this sample; needed to examine knowledge retention, sustained engagement,
therefore, the questionnaire dimensions should be interpreted transfer,longer-termeffectiveness,anduseracceptance.
cautiously and validated in larger independent samples. The Furthermore, as technology continues to advance, the
current system did not maintain an explicit learner model functionality and design of the Intelligent TCM Tutoring
or automatically adapt longitudinal learning pathways from System are amenable to continuous improvement. Future
individual performance data; accordingly, the present findings studies could integrate more advanced AI models with enhanced
concern learner-responsive educational support rather than fully reasoning capabilities to more effectively emulate the decision-
automatedpersonalizedlearning. making processes of human teachers, thereby improving the
flexibilityandintelligenceofpedagogicalresponses.Anintelligent
recommendationmodulecouldalsobedevelopedtodynamically
identifyandanalyzestudents’knowledgegapsduringthelearning
6.2 Future directions
process. This module would then proactively deliver relevant
learning resources and personalized guidance, thereby providing
Futureresearchshouldassesstheseparticipantcharacteristics more precise learning path recommendations and personalized
prospectivelyandusemulti-institutional,larger,andmorediverse interventions to improve both the user experience and learning
samples. It should also evaluate additional instructional sources outcomes. Additionally, the potential application of the system
andhealthcaredisciplinesacrossculturalandlinguisticsettingsand in other academic disciplines could be explored to validate its
comparesystemsbasedondifferentLLMs.Delayedpost-testsand cross-disciplinary applicability. This would not only enhance the
FrontiersinMedicine 14 frontiersin.org

Huetal. 10.3389/fmed.2026.1943401
technology’s versatility but also provide innovative solutions for Funding
intelligenteducationacrossvariousfields.
The author(s) declared that financial support was received
for this work and/or its publication. This research was
Data availability statement funded by the University Synergy Innovation Program of
Anhui Province (GXXT-2023-071), the Research Funds
of Center for Xin’an Medicine and Modernization of
Thedatasetspresentedinthisarticlearenotreadilyavailable
Traditional Chinese Medicine of IHM (2024CXMMTCM003),
because data will be made available on reasonable request.
the Key Projects of University Scientific Research
Requests to access the datasets should be directed to Jili
Plan in Anhui Province (Grant no. 2024AH050917)
Hu,hujili@ahtcm.edu.cn.
and The Open Fund of High-level Key Discipline of
Basic Theory of TCM of the State Administration of
Traditional Chinese Medicine, Anhui University of Chinese
Ethics statement Medicine(ZYJCLLZD-07).
Ethical review and approval were not required under Article
32 of the Chinese Measures for Ethical Review of Life Science Conflict of interest
andMedicalResearchInvolvingHumanSubjects(2023),because
this minimal-risk educational study involved only anonymized
The author(s) declared that this work was conducted in the
questionnaire data, posed no additional risk to participants, and
absenceofanycommercialorfinancialrelationshipsthatcouldbe
collected no sensitive personal information. The questionnaire
construedasapotentialconflictofinterest.
datawereanonymizedbeforeanalysis,andonlyanonymizeddata
were included in the analysis. All participants were adults and
received study information before participation. Before starting
thequestionnaire,participantswerepresentedwithaninformation Generative AI statement
page describing the study purpose, voluntary participation, and
righttowithdraw.Initiatingthequestionnaireafterreviewingthis Theauthor(s)declaredthatGenerativeAIwasnotusedinthe
information indicated electronic informed consent for the use of creationofthismanuscript.
theiranonymizedresponsesforresearchpurposes.Thestudieswere Any alternative text (alt text) provided alongside figures
conductedinaccordancewiththelocallegislationandinstitutional in this article has been generated by Frontiers with the
requirements.Theparticipantsprovidedtheirinformedconsentto support of artificial intelligence and reasonable efforts have
participateinthisstudy. been made to ensure accuracy, including review by the
authors wherever possible. If you identify any issues, please
contactus.
Author contributions
JH: Conceptualization, Investigation, Methodology, Publisher’s note
Supervision, Writing – review & editing. YD: Conceptualization,
Data curation, Formal analysis, Visualization, Writing – original All claims expressed in this article are solely those
draft.QZ:Formalanalysis,Validation,Writing–review&editing. of the authors and do not necessarily represent those of
DZ:Datacuration,Writing–review&editing.YLi:Datacuration, their affiliated organizations, or those of the publisher,
Writing–review&editing.CQ:Datacuration,Writing–review the editors and the reviewers. Any product that may be
&editing.YLiu:Formalanalysis,Writing–review&editing.HK: evaluated in this article, or claim that may be made by
Conceptualization, Supervision, Writing – review & editing. FX: its manufacturer, is not guaranteed or endorsed by the
Conceptualization,Supervision,Writing–review&editing. publisher.
References
1.Fu R, Li J, Yu H, Zhang Y, Xu Z, Martin C. The Yin and Yang of traditional 3.LiN,Wang T,XueX,WuX,ZhaoY,ZhaoL.Thoughtontheintegrationof
Chineseandwesternmedicine.MedResRev.(2021)41:3182–200.doi:10.1002/med. apprenticeeducationandcollegeeducationinthetalentscultivationinTCM.World
21793 JIntegrTraditWestMed.(2019)14:1612–5.doi:10.13935/j.cnki.sjzx.191132
2.YuanC,ZhangW,WangJ,HuangC,ShuB,LiangQ,etal.Chinesemedicine 4.WangF,ZhangH.Theimportantvalueandpracticalpathsofmaster-apprentice
phenomics (chinmedphenomics): personalized, precise and promising. Phenomics. educationintheinheritanceandinnovationoftraditionalChinesemedicineculture.J
(2022)2:383–8.doi:10.1007/s43657-022-00074-x TraditChinMed(2023)64:1513–8.doi:10.13288/j.11-2166/r.2023.15.001
FrontiersinMedicine 15 frontiersin.org

Huetal. 10.3389/fmed.2026.1943401
5.Tian J. Individualized teaching from ancient academies and addressing health disparities in patient comprehension. Medicine. (2025)
personalization of modern higher education. Univ Educ Sci. (2020):94–101. 104:e41059.doi:10.1097/MD.0000000000041059
doi:10.3969/j.issn.1672-0717.2020.06.13
25.GuoQ,ZhenJ,WuF,HeY,QiaoC.CanstudentsmakeSTEMprogresswith
6.Liu T. Guidance and respect: the meaning and path of teaching students thelargelanguagemodels(LLMs)?AnempiricalstudyofLLMsintegrationwithin
in accordance with their aptitude from the analects of confucius. Guizhou Soc middleschoolscienceandengineeringpractice.JEducComputRes.(2025)63:372–405.
Sci.(2022):103–8.doi:10.13713/j.cnki.cssci.2022.06.004 doi:10.1177/07356331241312365
7.ShahPhD,KumarR.Conceptsoflearner-centredteaching.ShanlaxIntJEduc. 26.Wang C, Li S, Lin N, Zhang X, Han Y, Wang X, et al. Application of large
(2020)8:45–60.doi:10.34293/education.v8i3.2926 languagemodelsinmedicaltrainingevaluation—usingChatGPTasastandardized
patient:multimetricassessment.JMedInternetRes.(2025)27:e59435.doi:10.2196/
8.Cheng L. “Changes” and “Constants”: rational reflection on large-scale
59435
individualized teaching in the age of digital intelligence. e-Education Res. (2025)
46:34–9+46.doi:10.13811/j.cnki.eer.2025.01.005 27.Ye B, Xi Y, Zhao Q. Optimizing mathematical problem-solving
reasoning chains and personalized explanations using large language
9.Zhang S. Development model, external challenges, and future path exploration
of Confucius institutes. J Sichuan Norm Univ. (2025) 52:137–45 + 205–6. models: a study in applied mathematics education. JAPMI. (2024)
3:67–83.doi:10.60087/Japmi.Vol.03.Issue.01.Id.005
doi:10.13734/j.cnki.1000-5315.2025.0608
28.KhanAcademy.MeetKhanmigo:KhanAcademy’sAI-poweredteachingassistant
10.Shen R, Wang Y. Research on logic, problems and action paths of
&tutor.https://www.khanmigo.ai/(AccessedMay8,2025).
“Emerging Medical Education” construction. Med Philos. (2020) 41:69–73.
doi:10.12014/j.issn.1002-0772.2020.12.16 29.HouB,LinY,LiY,FangC,LiC,WangX.KG-PLPPM:aknowledgegraph-based
personallearningpathplanningmethodusedinonlinelearning.Electronics.(2025)
11.CuiS,MaJ,GaoX,LiuZ,LiangH,BaoH,etal.Theconstructionandpractice
14:255.doi:10.3390/electronics14020255
of the “Theory - Classic - Clinical” three-in-one teaching system of basic theory
of traditional Chinese medicine. J Li-shizhen Tradit Chin Med. (2022) 33:1737–9. 30.WuW,YangS,TianF,WeiX,PanY.Knowledgegraphenhancedrecommendation
doi:10.3969/j.issn.1008-0805.2022.07.62 forsemanticstructureconstructionandfeedbackinonlinelearning.PhysCommun.
(2025)69:102590.doi:10.1016/j.phycom.2024.102590
12.MinL,LinX,LiangW.Researchontheoptimizationofteachinginteraction
in diagnosis of traditional Chinese medicine. J Li-shizhen Tradit Chin Med. 31.Zhong Y, Zhang X, Su Y. Recommendation method of teaching resources for
(2022)33:2757–8.doi:10.3969/j.issn.1008-0805.2022.11.56 professionalmusiccoursesbasedonknowledgegraph.IntJHiSpeEleSyst.(2025)
34:2540212.doi:10.1142/S0129156425402128
13.RenH,WangW,XuL,LiH,JiangT,YangT,etal.Thinkingontheresearchof
smarttraditionalChinesemedicineunderthebackgroundofintelligentera.JNanjing 32.Ramazanova V, Sambetbayeva M, Serikbayeva S, Sadirmekova Z, Yerimbetova
UnivTraditChinMed.(2024)40:1291–302.doi:10.14148/j.issn.1672-0482.2024.1291 A.Developmentofaknowledgegraph-basedmodelforrecommendingMOOCsto
supplementuniversityeducationalprogramsinlinewithemployerrequirements.IEEE
14.YangT,RenH,ZhouZ,ZhuX,HuK.IssuesandchallengesintheAI-empowered
Access.(2024)12:193313–31.doi:10.1109/ACCESS.2024.3519263
high-qualitydevelopmentoftraditionalChinesemedicine.JNanjingUnivTraditChin
Med.(2024)40:1285–1290.doi:10.14148/j.issn.1672-0482.2024.1285 33.Lu H, Li X. Chinese language curriculum resources pushing method
based on knowledge graph and similarity algorithm. IJCEELL. (2025)
15.Brown TB, Mann B, Ryder N, Subbiah M, Kaplan J, Dhariwal P, et al.
35:77–94.doi:10.1504/IJCEELL.2025.143804
Languagemodelsarefew-shotlearners.AdvancesinNeuralInformationProcessing
Systems CurranAssociates,Inc.(2020)33:1877–1901. 34.Villegas-Ch W, Govea J, Gutierrez R. Optimizing language model-based
educationalassistantsusingknowledgegraphs:integrationwithMoodleLMS.IEEE
16.Denny P, Gulwani S, Heffernan NT, Käser T, Moore S, Rafferty AN, et al.
Access.(2024)12:191994–2012.doi:10.1109/ACCESS.2024.3518952
Generative AI for education (GAIED): advances, opportunities, and challenges.
arXiv:2402.0158(2024) 35.BuiT,TranO,NguyenP,HoB,NguyenL,BuiT,etal.Cross-dataknowledge
graphconstructionforLLM-enablededucationalquestion-answeringsystem:acase
17.Xu C. Intelligent recommendation method for digital teaching
study at HCMUT. In: Proceedings of the 1st ACM workshop on AI-powered Q&A
resources of online courses based on knowledge graph. IJCEELL. (2025)
systems for multimedia. Phuket: ACM (2024). p. 36–43. doi: 10.1145/3643479.366
35:62–76.doi:10.1504/IJCEELL.2025.143802
2055
18.Ji S, Liu L, Xi J, Zhang X, Li X, KLR-KGC: knowledge-guided
36.ZhangX,ZhangL,YanS,HouM,ZhaoY.Personalizedlearningrecommendation
LLM reasoning for knowledge graph completion. Electronics. (2024)
incollaborationofknowledgegraphandlargelanguagemodel.JComputAppl.45:773–
13:5037.doi:10.3390/electronics13245037
784.doi:10.11772/j.issn.1001-9081.2024070971
19.WuQ.TheGoldenMirrorofMedicine(Volume1,2,3).Beijing:People’sHealth 37.LiuJ,SunX,ZhangY.Educationalresourcecontentreviewmethodbasedon
PublishingHouse.(2017). knowledge graph and large language model collaboration. J East China Normal
20.Wang Y, Wang Y, Dong C, Du J, Sun J. Discussion on the feasibility Univ.(2024):57–69.doi:10.3969/j.issn.1000-5641.2024.05.006
of incorporating Yizong Jinjian into undergraduate teaching of traditional 38.LiuX,TangC,XiC.Constructionofanintelligentquestion-answeringsystemfor
Chinese medicine. Chin Med Modern Distance Educ China. (2021) 19:17–8. selectedreadingsoftheinnercanonbasedonamultimodalknowledgegraph.Educ
doi:10.3969/j.issn.1672-2779.2021.09.007 ChinMed.(2025)44:143–148.doi:10.3969/j.issn.1003-305X.2025.01.438
21.Zheng X, Yuan Y, Han J. Clinical teaching enlightenment from the Golden 39.InstituteofInformationonTraditionalChineseMedicine,ChinaNationalInstitute
Mirror of Medicine. Chin Med Modern Distance Educ China. (2023) 21:4–6. ofStandardization.HealthInformatics—SemanticNetworkFrameworkofTraditional
doi:10.3969/j.issn.1672-2779.2023.06.002 ChineseMedicineLanguageSystem(2020).GB/T38324-2019.
22.Ruan X. The design and implementation of the Golden Mirror of Medicine 40.Peng Z, Liu Y, Zhou H, Xu Z, Ma X. CReBot: Exploring interactive
cultural town based on unity 3D (Master’s thesis). Hunan University of Chinese question prompts for critical paper reading. Int J Hum Comput Stud. (2022)
Medicine(2023). 167:102898.doi:10.1016/j.ijhcs.2022.102898
23.Mihaljevic´ B, Radovan A, Beronic´ D. Integrating AI-assisted learning of 41.Jang D, Shangguan Z, Tegtmeyer K, Gupta A, Czerminski JT, Chheang
programming in software development courses. Seville, Spain (2024), p. 10273– S, et al. MedTutor: a retrieval-augmented LLM system for case-based medical
83.doi:10.21125/iceri.2024.2623 education. In: Habernal I, Schulam P, Tiedemann J, editors. Proceedings of the
2025 conference on empirical methods in natural language processing: system
24.Spina AC, Fereydouni P, Tang JN, Andalib S, Picton BG, Fox demonstrations.Suzhou:AssociationforComputationalLinguistics(2025).p.319–
AR. Tailoring glaucoma education using large language models: 53.doi:10.18653/v1/2025.emnlp-demos.24
FrontiersinMedicine 16 frontiersin.org