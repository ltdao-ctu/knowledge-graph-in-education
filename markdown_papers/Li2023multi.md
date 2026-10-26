---
title: "Li2023multi"
source: "Li2023multi.pdf"
source_sha256: "ff5fbf9db2e36249a834e5a67d8e00cb699c3d6177c5e5c7939497d293af17e4"
converted_at: "2026-10-26T07:05:00.050053+00:00"
markitdown_version: "0.1.9"
---
Multi-source Education Knowledge Graph
Construction and Fusion for College Curricula
Zeju Li, Linya Cheng, Chunhong Zhang*, Xinning Zhu, Hui Zhao
Beijing University of Posts and Telecommunications
lizeju@bupt.edu.cn, chenglinya@bupt.edu.cn, zhangch@bupt.edu.cn, zhuxn@bupt.edu.cn, hzhao@bupt.edu.cn
Abstract—The field of education has undergone a significant Recently, an increasing number of researchers introduce
transformation due to the rapid advancements in Artificial knowledge graphs into education by the embedding knowl-
Intelligence(AI).AmongthevariousAItechnologies,Knowledge edge for representational learning [6], [7]. However, there are
Graphs (KGs) using Natural Language Processing (NLP) have
limitations in the current research and accomplishments. One
emerged as powerful visualization tools for integrating multi-
faceted information. In the context of university education, the is that the human and material resources required to construct
availability of numerous specialized courses and complicated curriculum knowledge graphs are too large and the quality
learning resources often leads to inferior learning outcomes for of knowledge extraction may be subpar. Moreover, most of
students.Inthispaper,weproposeanautomatedframeworkfor
the knowledge graphs constructed for the education field are
knowledgeextraction,visualKGconstruction,andgraphfusion,
small-scale graphs, or a graph of a particular chapter or a
tailored for the major of Electronic Information. Furthermore,
we perform data analysis to investigate the correlation degree particular course. In hence, we introduce Natural Language
and relationship between courses, rank hot knowledge concepts, Processing(NLP)[8]andknowledgegraph[5]intouniversity
and explore the intersection of courses. Our objective is to education in the field of Electronic Information. Students in
enhance the learning efficiency of students and to explore new
the major of Electronic Information mainly learn basic circuit
educational paradigms enabled by AI. The proposed framework
knowledge and master the methods of processing information
isexpectedtoenablestudentstobetterunderstandandappreciate
the intricacies of their field of study by providing them with a with computers. We integrate the knowledge concepts of
comprehensive understanding of the relationships between the curriculaandconstructavisualknowledgegraphofElectronic
various concepts and courses. Information automatically. Students can search for knowledge
Index Terms—Knowledge graph construction, Knowledge concepts, view the attributes of knowledge nodes and so on.
graph fusion, Electronic information
They can master the pivotal knowledge of the curriculum
more efficiently and quickly. At the same time, students can
I. INTRODUCTION
also grasp the related knowledge concepts to enhance the
TheintegrationofArtificialIntelligence(AI)intoeducation understanding and cognition of other associated courses.
has received significant attention due to the rapid advance- We summarize our contributions as follows:
ments in technology and the growing demand for innovative • We construct multi-source and large-scale knowledge
teachingmethods[1]–[3].Expertsproposetoutilizeintelligent graphs for hundreds of courses in Electronic Information
technologytoacceleratethereformoftalenttrainingmodeand and import them into graph database for visualization
teachingmethods,andbuildaneweducationsystemincluding automatically, covering more than 60k entities and 80k
intelligentlearningandinteractivelearning.Foruniversityed- triples.
ucation,eachcoursecontainsawealthofcomplicatedlearning • We propose an automated knowledge extraction, data
materials, such as syllabi, textbooks, and slides, making it cleaning and graph fusion [9], [10] framework for het-
challenging for students to ensure quality learning outcomes erogeneous learning resources, which also is applicable
and efficiency. Therefore, it is essential to explore novel and to other disciplines.
practical methods that integrate AI into university education. • We develop auxiliary information statistics in our con-
Knowledge graphs [4], [5] link distributed knowledge con- structed graphs such as curriculum relevance calculation,
cepts which is scattered in various positions of the textbook ranking of hot knowledge concepts, relevant keyword
together to form a large knowledge base, which describes index of knowledge nodes and their attributes.
complex relationships between entities in a structured form
II. METHOD
in the objective world. Furthermore, the application scenarios
of knowledge graph are extensive, such as natural language We perform automated construction of knowledge graphs
understanding, question and answer systems based on knowl- and graphs fusion can be divided as follows: We convert text-
edge graph, recommendation systems, and providing visual booksandcourseslidesfromoriginalformattoeditableformat
knowledge representation. respectively. Next we divide the documents of textbooks and
course slides into “Knowledge Units, Knowledge Chapters,
*ChunhongZhangisthecorrespondingauthor KnowledgeBlocks,KnowledgePoints”automaticallybyusing
3202
yaM
8
]IA.sc[
1v76540.5032:viXra

regularized expressions and named entity recognition (NER) edgeChapter, KnowledgeBlock and TeachingContent. For the
[11] methods. After that, we import chapters and knowledge entity KnowledgePoint, we set seven basic attributes (name,
points into “Neo4j” graph database automatically to construct ranker, start, word frequency, url, level, description). The
alarge-scaleknowledgegraph.Inordertoimprovethequality attribute “description” can be divided into three categories:
ofourgraphs,weutilizelanguageerrorcorrectionmodel[12] description wikiE, description wikiC and description baidu.
enabledbydeeplearningfordatacleaning.Finally,wedevelop
momentous information statistics in our constructed graphs. TABLEI
ENTITYTYPESANDCORRESPONDINGATTRIBUTES
| A. Ontology | Construction |     | of Subject | Knowledge |     | Graph |     |     |     |     |     |     |     |
| ----------- | ------------ | --- | ---------- | --------- | --- | ----- | --- | --- | --- | --- | --- | --- | --- |
Attributes
|     |     |     |     |     |     |     |     | EntityType |     | EntityAttributes |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | ---------- | --- | ---------------- | --- | --- | --- |
Number
| Ontology | construction |     | [13] guides | the | construction |     | of uni- |     |     |     |     |     |     |
| -------- | ------------ | --- | ----------- | --- | ------------ | --- | ------- | --- | --- | --- | --- | --- | --- |
school term,name,
| fied knowledge | structure |     | with | strong | hierarchy | and | low re- |        |     |                 |     |     |     |
| -------------- | --------- | --- | ---- | ------ | --------- | --- | ------- | ------ | --- | --------------- | --- | --- | --- |
|                |           |     |      |        |           |     |         | Course |     | background,url, |     |     | 6   |
dundancy. In order to construct an ontology structure that can coursePrerequisites,
educationalAlignments
| reflect the | knowledge | level | of  | the college | curricula |     | and the |               |     |                       |     |     |     |
| ----------- | --------- | ----- | --- | ----------- | --------- | --- | ------- | ------------- | --- | --------------------- | --- | --- | --- |
|             |           |       |     |             |           |     |         | KnowledgeUnit |     | name,ranker,level,url |     |     | 4   |
coreconceptsoftheknowledgecontent,wedefineclassesand
|     |     |     |     |     |     |     |     | KnowledgeChapter |     | name,ranker,level,url |     |     | 4   |
| --- | --- | --- | --- | --- | --- | --- | --- | ---------------- | --- | --------------------- | --- | --- | --- |
class inheritance. A class contains many knowledge entities KnowledgeBlock name,ranker,level,url 4
and different classes imply different levels or granularity. TeachingContent name,ranker,level,url 4
We analyze the knowledge hierarchy division of teaching name,ranker,start,
word frequency,url,
resources and design the class division of knowledge entities KnowledgePoint level,description wikiE, 9
to obtain ontology classes and attributes. Then we define the description wikiC,
|              |               |          |              |        |               |     |          |     |     | description |     | baidu |     |
| ------------ | ------------- | -------- | ------------ | ------ | ------------- | --- | -------- | --- | --- | ----------- | --- | ----- | --- |
| relation     | type between  | entities | to           | obtain | the ontology  |     | relation |     |     |             |     |       |     |
| to represent | the knowledge |          | associations |        | structurally. |     |          |     |     |             |     |       |     |
1) Subject knowledge graph entity type definition: An 3) Theentityrelationdefinitionofsubjectknowledgegraph:
entity type is an abstraction of a set of entities that share Entity relationship embodies the inner relation between dif-
the same characteristics or attributes and is used to distin- ferent entity types. For knowledge systems, it is crucial to
guish the course content and knowledge granularity. Since explore the correlation between knowledge entities, which
the knowledge system was processed according to different helps students to form a deeper cumulative understanding of
levels of granularity based on discipline rules, we take the thecurriculumknowledgesystemandprovidesaclearknowl-
hierarchical catalog of teaching resources as the main basis edge structure for teachers to carry out curriculum reform.
for the construction of our knowledge graph ontology. To Therefore, in our curriculum knowledge system, knowledge
| be specific, | We start | with | the | coarsest | grain | of knowledge, |     |              |                 |     |           |           |          |
| ------------ | -------- | ---- | --- | -------- | ----- | ------------- | --- | ------------ | --------------- | --- | --------- | --------- | -------- |
|              |          |      |     |          |       |               |     | entities are | interdependent. | We  | establish | knowledge | correla- |
and then refine gradually according to the catalog level of tion through the appearing chapters of teaching resource and
teaching resources, to determine the maximum granularity hierarchical structure of each knowledge entity.
(KnowledgeUnit) and minimum granularity (KnowledgePoint) KG textbook ,KG slide andKG syllabus allhavearelationship
of our knowledge system. named “haspartOf” to represent knowledge granularity and
| KG  | indicates |     | the | knowledge | graph | from | the |     |     |     |     |     |     |
| --- | --------- | --- | --- | --------- | ----- | ---- | --- | --- | --- | --- | --- | --- | --- |
textbook hierarchy. The entity category of node links from top to
textbook, KG indicates the knowledge graph from the bottom on KG and KG is [ Course − h − as − p − ar − tO → f
|     | slide |     |     |     |     |     |     |     | textbook |     | slide |     |     |
| --- | ----- | --- | --- | --- | --- | --- | --- | --- | -------- | --- | ----- | --- | --- |
class handout, and KG indicates the knowledge haspartOf haspartOf
|     |     |     | syllabus |     |     |     |     | KnowledgeUnit | −−−−−→ |     | KnowledgeChapter |     | −−−−−→ |
| --- | --- | --- | -------- | --- | --- | --- | --- | ------------- | ------ | --- | ---------------- | --- | ------ |
graph from the course syllabus. On KG textbook and h as p ar tO f
|       |              |        |     |           |     |        |         | KnowledgeBlock | − − | − − − → KnowledgePoint |     |     | ].        |
| ----- | ------------ | ------ | --- | --------- | --- | ------ | ------- | -------------- | --- | ---------------------- | --- | --- | --------- |
| KG    | , we further | refine | the | knowledge |     | system | of each |                |     |                        |     |     |           |
| slide |              |        |     |           |     |        |         |                |     |                        |     |     | haspartOf |
discipline into 5-level structure: Course-KnowledgeUnit- Analogously, on KG syllabus , link [ Course −−−−−→
haspartOf
KnowledgeChapter-KnowledgeBlock-KnowledgePoint. TeachingContent−−−−−→KnowledgePoint ] to indicate
KnowledgePoint is concept-level knowledge with fine the top-down knowledge system.
| granularity, | while | others    | are         | course-level |     | knowledge. |     |                  |     |     |     |     |     |
| ------------ | ----- | --------- | ----------- | ------------ | --- | ---------- | --- | ---------------- | --- | --- | --- | --- | --- |
|              |       |           |             |              |     |            |     | B. Data Cleaning |     |     |     |     |     |
| On KG        | ,     | knowledge | granularity |              | was | classified | as  |                  |     |     |     |     |     |
syllabus
“Course-TeachingContent-KnowledgePoint”. The quality of knowledge concepts determines the quality
2) Subjectknowledgegraphentityattributedefinition: The ofourconstructedgraphs,the process ofgraphfusionandthe
definition of entity attribute is a supplement to the semantic learningeffectofstudents.Inhence,datacleaningisanimper-
information of entity, and its coverage and accuracy affect the ative step to guarantee the quality of our knowledge graphs.
accuracy of the representation information of the knowledge It occurs text conversion errors, format encoding and other
graph. Different types of ontology attributes can enhance problems when we construct knowledge graphs. And there
classinformationandfacilitatedifferentiationbetweenclasses. are entity anomalies in entities and their attributes, such as
Therefore,wedesigncorrespondingattributesetsforeachtype text mixed with this incomplete formula and symbols, mixed
of knowledge entity. These attributes present comprehensive Chinese and English, misspellings, syntax error of entities.
and specific information about the entity. Moreover, because of the algorithm limitations of the NER
Forexample,WecanfindinTableIthatfourbasicattributes model and regularized expressions for knowledge concepts
(name, ranker, level, url) are set for KnowledgeUnit, Knowl- extraction,itmayleadtosyntaxerrorintheextractedentities.

Based on the above, we have to perform data cleaning on the to more completely retain the hierarchical structure in the
originalgraphsweconstructed.Datacleaningisamomentous knowledge graph, e f is located at the coarsest node in E and
| step to | ensure the accuracy | of  | entities, | their attributes | and | l   | =highest(L). |     |     |     |     |     |     |     |
| ------- | ------------------- | --- | --------- | ---------------- | --- | --- | ------------ | --- | --- | --- | --- | --- | --- | --- |
f
the effect of graph fusion because uncleaned data may lead c. Taking Union of Attributes
to wrong decisions and unreliable data mining. We use the In order to maintain the amount of information of the
language error correction model to check and identify the knowledgegraphaftertheknowledgefusionwork,inaddition
toretainingthehierarchicalrelationship,wealsoneedtoretain
| location | in the entity | where the | incorrect | word | occurs. For |     |     |     |     |     |     |     |     |     |
| -------- | ------------- | --------- | --------- | ---- | ----------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
the suspected error words, the corrected results are ranked theunionoperationfortheattributeinformation(except“url”)
according to the language model to select the best result, and of each knowledge concept (entity) before fusion.
then correct the error automatically. We define attribute set A = {A 1 ,A 2 ,...,A n } to represent
|              |       |        |     |     |     | all        | attribute    | information      |        | corresponding |          | to entity  | set        | E to      |
| ------------ | ----- | ------ | --- | --- | --- | ---------- | ------------ | ---------------- | ------ | ------------- | -------- | ---------- | ---------- | --------- |
| C. Knowledge | Graph | Fusion |     |     |     |            |              |                  |        |               |          |            |            |           |
|              |       |        |     |     |     | be         | fused.       | A =              | {...,a | ,b ,...},A    | =        | {...,a     | ,b ,...},A | =         |
|              |       |        |     |     |     |            |              | 1                |        | 1 1           | 2        |            | 2 2        | i         |
|              |       |        |     |     |     | {...,a     | ,b           | ,...}, where     | a      | represents    | the      | a property |            | of entity |
|              |       |        |     |     |     |            | i            | i                |        | i             |          |            |            |           |
|              |       |        |     |     |     | e          | ∈E,          | and b represents |        | the b         | property | of entity  | e          | ∈E. A     |
|              |       |        |     |     |     | i          |              | i                |        |               |          |            | i          | f         |
|              |       |        |     |     |     | represents |              | the attribute    |        | set of the    | node     | e f after  | fusion,    | which     |
|              |       |        |     |     |     | can        | be expressed |                  | as:    |               |          |            |            |           |
n n
|     |     |     |     |     |     |          |          |          |            |             | (cid:88)     | (cid:88)            |           |      |
| --- | --- | --- | --- | --- | --- | -------- | -------- | -------- | ---------- | ----------- | ------------ | ------------------- | --------- | ---- |
|     |     |     |     |     |     |          | A        | =A ∪A    | ...∪A      | ={...,      |              | a ,                 | b ,.....} |      |
|     |     |     |     |     |     |          |          | f 1      | 2          | n           |              | i                   | i         |      |
|     |     |     |     |     |     |          |          |          |            |             | i=1          | i=1                 |           |      |
|     |     |     |     |     |     | For      | example, | the      | two        | “anti-noise | performance” |                     | knowledge |      |
|     |     |     |     |     |     | concepts |          | have the | attributes | shown       | in           | Fig.1 respectively, |           | then |
theuniqueknowledgeconceptsobtainedafterthefusionwork
|              |                |                 |     |             |                | had                               | the           | union of    | the attributes |         | of the                | two nodes, | that | is, the |
| ------------ | -------------- | --------------- | --- | ----------- | -------------- | --------------------------------- | ------------- | ----------- | -------------- | ------- | --------------------- | ---------- | ---- | ------- |
|              |                |                 |     |             |                | attributesofname,description,word |               |             |                |         | frequencyandranker,so |            |      |         |
|              |                |                 |     |             |                | the                               | attribute     | information |                | is most | reserved.             |            |      |         |
| Fig. 1. This | is an example  | of KG fusion.   | The | highlighted | node is the    |                                   |               |             |                |         |                       |            |      |         |
|              |                |                 |     |             |                |                                   | d. Preserving |             | Original       | Edges   |                       |            |      |         |
| node with    | the same name. | In the diagram, | the | pink node   | represents the |                                   |               |             |                |         |                       |            |      |         |
course,theorangenoderepresentsKnowledgeChapter,therednoderepresents In different textbooks, the topological structure and con-
Knowledgechapter,thegreennoderepresentsKnowledgeBlock,andtheblue nection relationship between knowledge nodes (entities) are
| node represents | the AlignmentObject | level, | which | is the lowest | knowledge |            |     |             |     |               |     |           |              |     |
| --------------- | ------------------- | ------ | ----- | ------------- | --------- | ---------- | --- | ----------- | --- | ------------- | --- | --------- | ------------ | --- |
|                 |                     |        |       |               |           | different. |     | In addition | to  | the retention |     | of entity | information, |     |
point.
relationalinformationshouldalsobeprocessedaccordinglyto
We carry out knowledge fusion to alleviate the redun- achieveinformationretention.Sincetheonlynoderefertoone
| dant knowledge | nodes | and improve | the | data quality | for our |         |     |                 |     |         |          |       |        |       |
| -------------- | ----- | ----------- | --- | ------------ | ------- | ------- | --- | --------------- | --- | ------- | -------- | ----- | ------ | ----- |
|                |       |             |     |              |         | concept |     | in the textbook |     | will be | obtained | after | fusion | work, |
knowledge graph. Meanwhile, in order to protect the content all the connection relationships existing before the fusion
diversityofknowledgeconcepts,entitiesreferringtothesame work should exist and be connected to the unique knowledge
knowledge concept will be fused. Their attributes and con- concept after the fusion work.
nection relationships are reserved to maintain the information Our graph fusion types are divided into different source
content of knowledge graph. Our main fusion method can be fusion and different course fusion. We utilize the methods
dividedintofourparts:entitynamematching,locatingcoarse- above for graph fusion of the same course. Moreover, we
grainedentities,attributeunion,andpreservingoriginaledges utilizeentityattributematching,preservingoriginaledgesand
as follows: creating equivalent edges for graph fusion between courses.
| a. Entity | Name Matching   |             |           |          |         |     |          |        |                       |        |     |         |             |     |
| --------- | --------------- | ----------- | --------- | -------- | ------- | --- | -------- | ------ | --------------------- | ------ | --- | ------- | ----------- | --- |
|           |                 |             |           |          |         |     |          | III.   | EXPERIMENTANDANALYSIS |        |     |         |             |     |
| First,    | we match entity | names to    | determine | whether  | the two |     |          |        |                       |        |     |         |             |     |
|           |                 |             |           |          |         | A.  | Analysis | of the | correlation           | degree |     | between | two courses |     |
| or more   | entities refer  | to the same | knowledge | concept. | We      |     |          |        |                       |        |     |         |             |     |
used string matching, literal similarity and semantic similarity In this part, we judge the degree of correlation between
to name matching and subsequent integration.As shown in any two courses by calculating the proportion of the number
Fig.1. The first step of knowledge graph fusion is to integrate of equivalence relation edges between two courses in the
these fragmentary nodes referring to the same knowledge into total knowledge concepts. First of all, we integrate within the
a unique node. curriculum and the same course. Under the condition that the
b. Locating Coarse-grained Entities originalknowledgegraphstructuresystemremainsunchanged.
As described in the previous section, knowledge concepts According to the result of fusion, we propose that there was a
(entities)oftenexistatdifferentlevelsintheknowledgesystem similarrelationshipbetweencourses,soweproposedtheindex
oftextbooks.Thehigherthelevel,thelargerthecoverageand of correlation degree between courses, which was defined by
the coarser the granularity. We define the entities to be fused the proportion of the number of knowledge concepts between
as E ={e ,e ,....,e } and their levels are L={l ,l ,...l }. courses and the total nodes of the course.
|     | 1 2 n |     |     |     | 1 2 n |     |     |     |     |     |     |     |     |     |
| --- | ----- | --- | --- | --- | ----- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
For example, e is used to represent the fused Knowledge We check the coverage of knowledge concepts between
f
node (entity), l f represents the unique level of e f . In order courses by counting the number of equivalent relation

TABLEII
CALCULATINGRESULTOFTHECORRELATIONDEGREESWITH“CommunicationPrinciples”
Coursei Coursej Su(i,j) Sv(i,j) S(i,j)
CommunicationPrinciples SignalsandSystems 0.11389 0.14008 0.12698
CommunicationPrinciples CommunicationElectronicCircuit 0.11676 0.05589 0.08632
CommunicationPrinciples FundamentalsofInformationTheory 0.09912 0.05589 0.07751
FundamentalsofProbabilityTheoryand
CommunicationPrinciples 0.06768 0.05078 0.05923
Mathematics
CommunicationPrinciples LinearAlgebraandGeometry 0.08368 0.01761 0.05065
CommunicationPrinciples DigitalCircuitsandLogicDesign 0.2265 0.05723 0.03994
CommunicationPrinciples ElectronicandCircuitFoundation 0.02702 0.04336 0.03519
CommunicationPrinciples DigitalSignalProcessing 0.01923 0.04813 0.03368
CommunicationPrinciples C/C++Programming 0.04177 0.02548 0.03362
CommunicationPrinciples ElectromagneticFieldandElectromagneticWave 0.03956 0.00998 0.02477
CommunicationPrinciples UniversityPhysics 0.03242 0.00540 0.01891
edges established between two courses. KG textbook = TABLEIII
{...V ,V ,....},KG = {...U ,U ,....}, V represents the THEMOSTRELEVANTCOURSESWITHEACHCOURSEAND
i j slide i j i
CORRESPONDINGCORRELATIONDEGREES
course in the knowledge graph of the textbook, and the total
Correla-
number of nodes of this course is Nv i ; U i represents the Course MostRelevantCourse tion
course in the slide knowledge graph, and the total number of Degree
CommunicationPrinciples SignalsandSystems 0.127
coursenodesisNu .Thenumberofmappingequivalentedges
i CommunicationElectronic
SignalsandSystems 0.119
established between course V and course V is expressed Circuit
i j
DigitalCircuitsandLogic ElectronicandCircuit
as sim v , and the number of mapping equivalent edges 0.201
i,j Design Foundation
established between course U and course U is expressed as FundamentalsofProbability LinearAlgebraand
i j 0.084
TheoryandMathematics Geometry
sim u . The knowledge graph of the two data sources is
i,j ElectronicandCircuit CommunicationElectronic
0.345
fused respectively, and an overall course correlation degree is Foundation Circuit
defined as S: ElectromagneticFieldand UniversityPhysics 0.029
ElectromagneticWave
LinearAlgebraand FundamentalsofInformation
Su(i,j)+Sv(i,j) 0.015
S(i,j)= Geometry Theory
2 DigitalSignalProcessing SignalsandSystems 0.064
ElectromagneticFieldand
UniversityPhysics 0.101
The correlation degree calculated by the slide database is the ElectromagneticWave
LinearAlgebraand
correlation degree Su, and the correlation degree calculated C/C++Programming Geometry 0.046
by the textbook database is the correlation degree Sv. We CommunicationElectronic
SignalsandSystems 0.035
Circuit
comprehensively analyzed the data results by combining the
FundamentalsofInformation
CommunicationPrinciples 0.149
datafromtwodatasourcesandtookthemastheaveragetotal Theory
correlationdegreeofthecorrelationdegreeofthetwocourses.
Su and Sv are calculated as follows:
B. Explore the relationship between multiple courses
sim u sim v
Su(i,j)= i,j,Sv(i,j)= i,j According to the method of calculating the correlation
Nu Nv
i i degree of two courses, we can sort each subject with other
Taking the course of Communication Principles as an ex- subjects in the order of correlation degree, so as to analyze
ample,theresultofcalculatingthecorrelationdegreewiththe the relationship between multiple courses and classify them.
courseisshowninTableII.Themostrelevantcoursesofother We used the spectral clustering method [14] and input
courses in Electronic Information and their corresponding the correlation degree matrix, and the results obtained are
correlation degrees are shown in Table III. we can see the highly similar to the results of the manual classification
courses that are highly related to Communication Principles. mentioned above, which can be used as the clustering method
Intheactualteachingapplicationscenario,itcanbeshownthat of course classification. Firstly, we choose ten subjects with
thesecourseswithhighcorrelationcanplayanauxiliaryrolein relatively complete data resources, and the set of courses
the study of Communication Principles, which helps teachers supported by data is C, C = {c ,c ,...c ,...c }(n = 10).
1 2 i n
toarrangeappropriateteachingprogramsandenablesstudents Correlation degree S(i,j) represents the degree of corre-
to have a macro overall control over the relationship between lation between c and c . So for every c course, there’s
j i i
the courses they need to learn. The method we proposed has S (i) = {S(i,1),S(i,2),.....,S(i,j),...}, represents c ’s set
w i
greatadvantagesincomparingthesimilaritybetweencourses, of correlation degrees with other courses. When the corre-
because we not only consider the correlation between the two lation comparison of multiple courses is needed, we pro-
coursenames,butalsoconsidertheoverlaprateofknowledge pose W(i,j) to represent the correlation weight of c to c .
j i
concepts at each level of the course, so as to determine the Therefore, each course c has correlation with other courses
i
relationship between courses. set weight W(i) = {W(i,1),W(i,2),...,W(i,j),...}. In the

same course, we normalize the correlation degree to get the framework for heterogeneous learning resources and is ap-
normalizedcorrelationdegreeofeachc ofothercoursesabout plicable and suitable to other disciplines. Through our graph
j
the c of this course, which can better represent the degree of fusion method, the individual knowledge graph is fused into
i
correlation in the same dimension. the knowledge graph from multiple data sources. Meanwhile,
In order to visualize the relationship more intuitively be- throughthedataminingandanalysis,weinfertherelationship
tweenmultiplecourses,weusethethicknessofthecorrelation between courses in Electronic Information and create the
edge to reflect the weight of the correlation degree. In order relationship between disciplines to sort out the discipline
to facilitate the observation of the correlation degree between knowledge framework.
courses, we remove the correlation edge with the weight less Our method not only conforms to the cognitive habits of
than0.25,asshownintheFig.2.Theresultsoftherelationship learners, but also improves learning efficiency by helping stu-
between multiple courses obtained in this part are of certain dents to understand the knowledge concepts between various
reference value for teachers to make teaching plans. coursesandgraspsintegralknowledgeconceptsofonecertain
subject comprehensively. Moreover, it can provide powerful
data support for teachers to achieve the corresponding teach-
# key words popularity
1 Fourier transform 120 ing objectives and highlight the core knowledge concepts to
2 Channel 102 improve teaching quality.
3 AM 99
ACKNOWLEDGMENT
4 Convolution 90
5 Filter 87 This work is supported by 2022 Beijing Higher Education
6 Gaussian White Noise 86 “Undergraduate Teaching Reform and Innovation Project”
7 Z-transform 80 and 2022 Education and Teaching Reform Project of Beijing
8 FM 71
UniversityofPostsandTelecommunications(2022JXYJ-F01).
Fig.2. GraphofcorrelationdegreeFig.3. Therankingoftheknowl-
weightofmultiplecourses edgeconceptsfrequencyinthein- REFERENCES
terfaceofourKGvisualsystem.
[1] A. Siren and V. Tzerpos, “Automatic learning path creation using
oer:Asystematicliteraturemapping,”IEEETransactionsonLearning
Technologies,vol.15,no.4,pp.493–507,2022.
C. Explorethemostvaluableandintegralknowledgeconcepts [2] A.Kulkarni,S.L.Chu,N.Sharma,andS.Sathe,“Interest-basedlearn-
ing through a contextualizing chatbot for video-based online learning
Since our knowledge graphs contain massive knowledge
platforms,” in 2022 International Conference on Advanced Learning
concepts, it is difficult for students to focus on the most Technologies(ICALT),2022,pp.66–70.
valuable and significant knowledge concepts among them. In [3] H.Li,“Astudyontheconstructionandapplicationofknowledgemap-
pingofmiddleschoolmathematicssubjectsbasedonneuralnetwork,”
hence, we separately count the number of occurrences and
Master’sthesis,YunnanNormalUniversity,2022.
calculate the intersection of all knowledge concepts in the [4] S.Ji,S.Pan,E.Cambria,P.Marttinen,andS.Y.Philip,“Asurveyon
database.Firstly,wecountthefrequencyofoccurrencesofall knowledgegraphs:Representation,acquisition,andapplications,”IEEE
TransactionsonNeuralNetworksandLearningSystems,vol.33,no.2,
knowledge concepts. We can obtain the ranking of the knowl-
pp.494–514,2021.
edge concepts frequency in Fig.3, so we can explore the most [5] Z.Wang,J.Zhang,J.Feng,andZ.Chen,“Knowledgegraphembedding
significant knowledge concepts in Electronic Information. bytranslatingonhyperplanes,”inProceedingsoftheAAAIconference
onartificialintelligence,vol.28,no.1,2014.
And then, we count the intersection of knowledge concepts
[6] Y.Shen,Z.Chen,G.Cheng,andY.Qu,“Ckgg:Achineseknowledge
of the same course among its KG textbook , KG slide and graphforhigh-schoolgeographyeducationandbeyond,”inInternational
KG after the fusion of graphs. In this way, we can SemanticWebConference. Springer,2021,pp.429–445.
syllabus
[7] C. Wang and S. Xu, “Construction of the evaluation index system
obtain the most valuable knowledge concepts in one course,
of physical education teaching in colleges and universities based on
because they appear in KG textbook , KG slide and KG syllabus scientific knowledge graph,” Mobile Information Systems, vol. 2022,
at the same time. We can find that 16 knowledge concepts 2022.
[8] A.Vaswani,N.Shazeer,N.Parmar,J.Uszkoreit,L.Jones,A.N.Gomez,
in Communication Principles appear in KG , KG
textbook slide Ł. Kaiser, and I. Polosukhin, “Attention is all you need,” Advances in
and KG syllabus : “inner product, orthogonality, correlation neuralinformationprocessingsystems,vol.30,2017.
coefficient, energy power spectral density, Hilbert transform, [9] H. L. Nguyen, D. T. Vu, and J. J. Jung, “Knowledge graph fusion for
smartsystems:Asurvey,”InformationFusion,vol.61,pp.56–70,2020.
analytic signal, band-pass signal, matched filter, FDM, TDM,
[10] Z. Kang, G. Shi, S. Huang, W. Chen, X. Pu, J. T. Zhou, and Z. Xu,
Nyquistcriterion,raisedcosineroll-off,phaseambiguity,opti- “Multi-graph fusion for multi-view spectral clustering,” Knowledge-
mumReception,constellation,spectrum”.Inthisway,Wecan BasedSystems,vol.189,p.105102,2020.
[11] A. L. F. Han, D. F. Wong, and L. S. Chao, “Chinese named entity
findthemostvaluableknowledgeconceptsinCommunication
recognition with conditional random fields in the light of chinese
Principles. So teachers and students will focus on these characteristics,” in Language Processing and Intelligent Information
knowledge concepts when teaching and learning. Systems. SpringerBerlinHeidelberg,2013,pp.57–68.
[12] Y. Li, Q. Zhou, Y. Li, Z. Li, R. Liu, R. Sun, Z. Wang, C. Li, Y. Cao,
andH.T.Zheng,“Thepastmistakeisthefuturewisdom:Error-driven
IV. DISCUSSIONANDCONCLUSION
contrastiveprobabilityoptimizationforchinesespellchecking,”2022.
We propose a novel method of knowledge graph con- [13] N.Guarino,D.Oberle,andS.Staab,“Whatisanontology?”Handbook
onontologies,pp.1–17,2009.
struction and graphs fusion by means of natural language [14] U. Von Luxburg, “A tutorial on spectral clustering,” Statistics and
processing and machine learning tools, which is a automatic computing,vol.17,pp.395–416,2007.