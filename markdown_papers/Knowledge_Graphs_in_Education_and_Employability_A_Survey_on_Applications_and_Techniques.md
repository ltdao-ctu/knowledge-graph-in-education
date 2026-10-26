---
title: "Knowledge Graphs in Education and Employability A Survey on Applications and Techniques"
source: "Knowledge_Graphs_in_Education_and_Employability_A_Survey_on_Applications_and_Techniques.pdf"
source_sha256: "ac540e90775af925c8b5f614b3ac8bd8688827b0c282f39a22f5970665b39a78"
converted_at: "2026-10-26T07:04:59.609805+00:00"
markitdown_version: "0.1.9"
---
Received20May2022,accepted16July2022,dateofpublication26July2022,dateofcurrentversion4August2022.
DigitalObjectIdentifier10.1109/ACCESS.2022.3194063
Knowledge Graphs in Education and
Employability: A Survey on Applications
and Techniques
YOUSRAFETTACH 1,MOUNIRGHOGHO 1,2,AND
BOUALEMBENATALLAH3,4,(Fellow,IEEE)
1TICLaboratory,CollegeofEngineering&Architecture,InternationalUniversityofRabat,Sale11103,Morocco
2FacultyofEngineering,UniversityofLeeds,LeedsLS29JT,U.K.
3SchoolofComputing,DublinCityUniversity,Dublin9,D09W6Y4Ireland
4SchoolofComputerScienceandEngineering,UNSWSydney,Sydney,NSW2052,Australia
Correspondingauthor:YousraFettach(yousra.fettach@uir.ac.ma)
ABSTRACT Studiesontherelationshipbetweeneducationandemployabilityareofparamountimportance
forpolicymakers,traininginstitutions,companiesandstudents.Theavailabilityoflargescaledataonthe
Internet,suchasonlinejobads,hasbeenleveragedtobetterinvestigatethisrelationship.Recentstudieshave
shownthatrepresentingthisdatausingknowledgegraphscanbeusefulinidentifyingthejobmarketneeds
andestablishingbetterassessmentmethods.Suchstudiesalsohighlighttheskillmismatchbetweeneducation
andthejobmarketandhelpmitigateit.Inthispaper,weprovideacomprehensivereviewoftheapplications
of knowledge graphs in education and employability. We review knowledge graph based frameworks that
have been proposed in previous work on different aspects of education and employability. The survey
introducesnewtaxonomiesfortheseapplicationsandtheirmethodologies,andprovidesathoroughoutlook
onpromisingresearchdirections.Wealsopresentausecasetoillustratehowknowledgegraphscanbeused
toinvestigatetherelationshipbetweeneducationandthejobmarket.
INDEXTERMS Educationaltechnologies,employability,knowledgegraphs,representationlearning.
I. INTRODUCTION resumes, has been incorporated in order to examine and
Educationhasbeenanimportanttoolforeconomicandsocial analyzetheissue.
growth throughout the modern era. Higher education cre- Theincreasedavailabilityoflargeamountofdataofdiffer-
dentials in particular are considered by many people to be enttypesalsoimpelledresearcherstoleveragesemanticand
essentialtoenterthelabormarket.However,recentresearch comceptualrepresentation.Thatledtothebirthofknowledge
demonstrated that sometimeshigher education falls shortin graphs (KG). A KG is a structured representation of facts,
fulfillingtheneedsofthejobmarket.Therefore,theissueof consisting of entities, relationships, and semantic descrip-
skill disparities between the job market and education has tions [1]. KGs are core component for several information
received much attention from policy makers, higher educa- systems which require access to structured knowledge [2].
tion institutions, employers as well as researchers. With the WiththesupportofKGsasarepresentationtoolforeducation
availability of massive amounts of structured and unstruc- andlabormarketentities,onecanunravelcorrelationsacross
tured data engendered by the digital transformation, online these entities and construct semantic connections between
content such as job ads, massive open online courses and theminordertoturndataintousableknowledge.
Previousworkproposednumerousmethodsbasedondata
analysis to improve education by learning student behav-
The associate editor coordinating the review of this manuscript and ior [3] or building recommender systems for students [4]
approvingitforpublicationwasAliShariqImran . for a better academic performance and education-to-job
80174 ThisworkislicensedunderaCreativeCommonsAttribution4.0License.Formoreinformation,seehttps://creativecommons.org/licenses/by/4.0/ VOLUME10,2022

Y.Fettachetal.:KnowledgeGraphsinEducationandEmployability:ASurveyonApplicationsandTechniques
matching [5]. Several studies investigated ways to eval- one [16]–[18]. Several approaches were utilized to tackle
uate the job market using job representations [6], pre- this problem. One of the first studies in this realm was
senting taxonomies to help job seekers [7] and predicting to enable prerequisite prediction for within-university and
job market trends [8]. Furthermore, many large-scale KGs cross-universitysettings.Theinitialintuitionoftheworkwas
have been developed by various academic and corporate thefactthatcoursesmaybespecifictooneinstitutionwhereas
institutions[9],[10]. concepts are shared across different providers [19]. Some
Thisreviewisbasedontheanalysisofresearchpaperson of the approaches adopted supervised learning to perform
theuseofknowledgegraphsasatooltoimproveeducation binaryclassification,usingasetoffeaturesextractedvianat-
and employability for job seekers and employers. Based on urallanguageprocessingmethods,inordertoautomatically
thisanalysis,wesuggestaunifiedKG-basedframeworkfor identifyprerequisites[20].Panetal.[17]haveimplemented
educationandemployability.Themaincontributionsofthis different classification methods using novel contextual and
paperareasfollows: structural features extracted from MOOCs. Authors of [16]
|                   |     |     |        |       |              |     |     | applied | active | learning | based | on  | graph-based | features | for |
| ----------------- | --- | --- | ------ | ----- | ------------ | --- | --- | ------- | ------ | -------- | ----- | --- | ----------- | -------- | --- |
| • A comprehensive |     |     | survey | of KG | applications |     | in  |         |        |          |       |     |             |          |     |
representingconceptpairs.In[21],theauthorsclaimedthat
education.
• A comprehensive survey of KG applications for theproblemofdetermininganeffectivelearningpathfroma
|     |     |     |     |     |     |     |     | corpus of | documents |     | depends | on the | accurate | identification |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --------- | --------- | --- | ------- | ------ | -------- | -------------- | --- |
employability.
ofconceptsthatarelearningobjectivesandtheidentification
| • A unified |     | KG-based | framework |     | for education |     | and |     |     |     |     |     |     |     |     |
| ----------- | --- | -------- | --------- | --- | ------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
employability. of concepts that are prerequisites. The authors of [21] then
|     |     |     |     |     |     |     |     | implemented | a   | supervised |     | machine | learning | approach | for |
| --- | --- | --- | --- | --- | --- | --- | --- | ----------- | --- | ---------- | --- | ------- | -------- | -------- | --- |
• Anoutlookonfuturedirections.
|          |       |     |           |                  |     |         |     | annotation | based | on    | multiple | extracted | local | features         | and |
| -------- | ----- | --- | --------- | ---------------- | --- | ------- | --- | ---------- | ----- | ----- | -------- | --------- | ----- | ---------------- | --- |
| • A case | study | for | exploring | the relationship |     | between |     |            |       |       |          |           |       |                  |     |
|          |       |     |           |                  |     |         |     | contextual | ones. | Other | studies  | focused   | on    | the relationship |     |
educationandthejobmarket.
betweenlearningresourcesinsteadofconcepts[22].In[23],
theauthorssuggestedanapproachtoacquireconceptsmaps
A. RELATEDSURVEYS
|          |        |        |        |        |       |     |       | from textbooks, |     | where | concepts | are | associated | with | prereq- |
| -------- | ------ | ------ | ------ | ------ | ----- | --- | ----- | --------------- | --- | ----- | -------- | --- | ---------- | ---- | ------- |
| Previous | survey | papers | on KGs | mainly | focus | on  | tech- |                 |     |       |          |     |            |      |         |
uisiterelationships.
| nical aspects    | [1],      | KG    | applications | in   | general  | [2]         | and  |         |         |         |             |         |          |           |       |
| ---------------- | --------- | ----- | ------------ | ---- | -------- | ----------- | ---- | ------- | ------- | ------- | ----------- | ------- | -------- | --------- | ----- |
|                  |           |       |              |      |          |             |      | Various | studies | were    | established |         | in order | to assist | job   |
| their embeddings |           | [11]. | Surveys      | like | [12] and | [13]        | pro- |         |         |         |             |         |          |           |       |
|                  |           |       |              |      |          |             |      | seekers | for the | purpose | of          | finding | a good   | fit [24], | [25]. |
| vide general     | overviews |       | of research  | from | the      | perspective |      |         |         |         |             |         |          |           |       |
Graphswerefirstincorporatedintothesemethodologieswith
| of job market    |        | evaluation | using        | data     | analysis  | methods.      |     |             |         |             |                |         |       |                |           |
| ---------------- | ------ | ---------- | ------------ | -------- | --------- | ------------- | --- | ----------- | ------- | ----------- | -------------- | ------- | ----- | -------------- | --------- |
|                  |        |            |              |          |           |               |     | graph-based | job     | recommender |                | systems |       | [26]. In       | [27], the |
| Other literature |        | reviews    | highlighted  | the      | potential | of KGs        | in  |             |         |             |                |         |       |                |           |
|                  |        |            |              |          |           |               |     | authors     | created | a job       | transition     | network |       | that presented | the       |
| education        | [14],  | [15]. Our  | survey       | combines | all       | these aspects |     |             |         |             |                |         |       |                |           |
|                  |        |            |              |          |           |               |     | talent flow | between |             | organizations, |         | which | was then       | used to   |
| and dives        | deeper | into the   | applications | of       | KGs       | in education  |     |             |         |             |                |         |       |                |           |
buildatalentcircledetectionmodelfortalentexchangepre-
| and the techniques |     | behind | them. | Besides, | our | paper | pro- |     |     |     |     |     |     |     |     |
| ------------------ | --- | ------ | ----- | -------- | --- | ----- | ---- | --- | --- | --- | --- | --- | --- | --- | --- |
diction.Otherstudiespresentedmethodologiesthataimedto
| vides a comprehensive |     |     | review | of KG-based | methodologies |     |     |     |     |     |     |     |     |     |     |
| --------------------- | --- | --- | ------ | ----------- | ------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
createnewtaxonomiesorenhanceexistingonesforjob-skill
foremployabilityinadditiontoshowcasingtheroleofKGs
matching[7].
inevaluatingthelinkbetweeneducationandthejobmarket.
|     |     |     |     |     |     |     |     | Overall, | KGs | started | getting | more | attention |     | in recent |
| --- | --- | --- | --- | --- | --- | --- | --- | -------- | --- | ------- | ------- | ---- | --------- | --- | --------- |
years[28]andbeingincorporatedinvarioustoolsforeduca-
B. SURVEYORGANIZATION
tionandjobmarketassessment.Thenextsectionrepresents
In Section II, we describe the background of KG method- abriefreportonKGtechniquesandhowtheyareappliedin
ologies for education and employability. Section III dis- educationandemployability.
| cusses the | KG  | techniques | in  | education | and employability. |     |     |     |     |     |     |     |     |     |     |
| ---------- | --- | ---------- | --- | --------- | ------------------ | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
KGapplicationsineducationandemployabilityarediscussed III. KGTECHNIQUESINEDUCATIONAND
| in Section | IV and | V, respectively. |     | In Section |     | VI, we | elabo- |     |     |     |     |     |     |     |     |
| ---------- | ------ | ---------------- | --- | ---------- | --- | ------ | ------ | --- | --- | --- | --- | --- | --- | --- | --- |
EMPLOYABILITY
| rate on the | importance | of  | building | a unified | framework |     | for |           |                |     |     |              |     |      |            |
| ----------- | ---------- | --- | -------- | --------- | --------- | --- | --- | --------- | -------------- | --- | --- | ------------ | --- | ---- | ---------- |
|             |            |     |          |           |           |     |     | Knowledge | representation |     |     | went through |     | many | iterations |
representing education and employability data in a single basedonframesemantics,whichistheideathatunderstand-
| knowledge | graph. | This | framework | is illustrated |     | using | a use |         |             |     |                   |     |     |                  |     |
| --------- | ------ | ---- | --------- | -------------- | --- | ----- | ----- | ------- | ----------- | --- | ----------------- | --- | --- | ---------------- | --- |
|           |        |      |           |                |     |       |       | ing one | word relies | on  | the understanding |     |     | of the knowledge |     |
caseinSectionVII.Futureresearchdirectionsarediscussed related to it, representing coherent structure of related con-
in VIIIandconclusionsaredrawninSectionIX. cepts. The concretization of this concept in computational
linguisticscanbefoundintheSemanticWebandKGs.The
II. BACKGROUND SemanticWebstartedbydevelopingtheconceptsofthetech-
Studies took different directions in order to use semantic nical standards such as Uniform Resource Identifier (URI),
metadata to improve education. One of these directions is ResourceDescriptionFramework(RDF)andWebOntology
exploringwaystoautomaticallydefineprerequisiterelation- Language (OWL). The concept of Linked Data started as
ships between concepts. From a pedagogical point of view, linking datasets to each other in the Semantic Web to make
a prerequisite is a dependency relation that states which them as a unified large KG. In 2012, the concept of KGs
concepts a student has to learn before moving to the next becamemorepopularasGooglelauncheditandutilizedthe
| VOLUME10,2022 |     |     |     |     |     |     |     |     |     |     |     |     |     |     | 80175 |
| ------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ----- |

Y.Fettachetal.:KnowledgeGraphsinEducationandEmployability:ASurveyonApplicationsandTechniques
semantic knowledge in web search in order to identify and byjointlylearningtopologyview,semanticview,jobtransi-
differentiateentitiesinadditiontoprovidinglinkstorelated tionbalanceview,andjobtransitiondurationview.Inaddi-
entitiesforthepurposeofcreatingmoreofaconnectedand tion,theypresentedanencode-decodebasedfusionmethodto
uniformsearchresults. obtainaunifiedrepresentationfromthemulti-viewrepresen-
TherearemanytechnicalaspectsinKGs[1].Inthissection tations.JobBERTisthelatesteffortinthistrajectory,where
we try to tackle the most prominent ones in the field of the authors of [39] presented a neural representation model
educationandemployability. for job titles, by augmenting a pre-trained language model
|                         |     |     |     |     |     |     |     | with co-occurrence |     | information | from | skill | labels | extracted |
| ----------------------- | --- | --- | --- | --- | --- | --- | --- | ------------------ | --- | ----------- | ---- | ----- | ------ | --------- |
| A. KNOWLEDGEACQUISITION |     |     |     |     |     |     |     | fromjobvacancies.  |     |             |      |       |        |           |
In KGs, knowledge acquisition aims to extract knowledge Due to the literature gap in the area, using specific KG
from unstructured text or various other structured or semi embedding techniques in educational KG construction was
|     |     |     |     |     |     |     |     | one of the | direction | [40] have | undertaken. |     | The authors | pre- |
| --- | --- | --- | --- | --- | --- | --- | --- | ---------- | --------- | --------- | ----------- | --- | ----------- | ---- |
structuredsources.ItalsoaimsatcompletingestablishedKGs
andrecognizingentitiesandrelations.Knowledgeacquisition sented a model for embedding learning of eduational KGs.
consistsofmanytasksincludingentityrecognitionandalign- Notably, the displayed method jointly learns embeddings
mentandrelationextraction[1].Thesetaskshavebeentack- from pre-trained structural (i.e. TransE) and literal embed-
ledusingvariousmethods.Forexample,in[29],entityrecog- ding vectors (i.e. BERT). These are considered to be pro-
jectionsofKGsintheknowledgerepresentationspacese.g.
| nition was | carried | out using | a   | Gated Recurrent |     | Unit | (GRU) |     |     |     |     |     |     |     |
| ---------- | ------- | --------- | --- | --------------- | --- | ---- | ----- | --- | --- | --- | --- | --- | --- | --- |
network,andrelationextractionwasperformedusingproba- Euclidean,non-Euclideanwhichiscomputationallyefficient
bilisticmethods.In[30],theauthorsadoptedaconceptprun- andrepresentativebuttheysufferfromlackofinterpretability.
ThisissueisremediedbyrulebasedKGcompletionmethods,
| ing strategy | that | is based | on a | measure | called | SemRefD | to  |     |     |     |     |     |     |     |
| ------------ | ---- | -------- | ---- | ------- | ------ | ------- | --- | --- | --- | --- | --- | --- | --- | --- |
analyzereferencesbetweenconcepts.Thismeasurehasbeen whichtakeadvantageoftheinherentstructureoftheKGsin
ordertofindmeaningfulpatterns.
utilizedinKGstoassessthelikelihoodofoneconceptbeing
a prerequisite of another. In order to evaluate the relation WhatfollowsisareviewofrecentKGapplicationsinedu-
extraction,thealgorithmXGBoostwasusedforbinaryclas- cation.Then,wepresentananalysisofKGbasedapplications
|             |            |       |             |     |        |            |     | for employability, |     | highlighting | several | factors | that | we think |
| ----------- | ---------- | ----- | ----------- | --- | ------ | ---------- | --- | ------------------ | --- | ------------ | ------- | ------- | ---- | -------- |
| sification. | In several | other | techniques, |     | entity | extraction | was |                    |     |              |         |         |      |          |
cast as a classification problem which was addressed using arecriticallyimportantforaunifiedKG-basedframeworkfor
algorithms like Support Vector Machine (SVM) [31] and educationandthelabormarket.
| Conditional | Random | Field | classifier |     | (CRFClassifier) |     | [32]. |     |     |     |     |     |     |     |
| ----------- | ------ | ----- | ---------- | --- | --------------- | --- | ----- | --- | --- | --- | --- | --- | --- | --- |
Other methodologies focused on entity extraction using IV. KGAPPLICATIONSINEDUCATION
SeveralstudieshaveproposedmethodologiestouseKGsas
semanticsimilarity[33]orStackLongShortTermMemory
(Stack-LSTM) with Spacy1 [34]. In a similar way, some a tool to improve education and its outcomes. We classify
researchers used KGs for job market data representation. the reviewed studies into three main categories as shown
inFigure1.
Forexample,theauthorsof[35]implementedentitylinking
| using rule-based |            | methods.    | Qinetal.[36] |            | proposed | a        | novel |                        |     |     |     |     |     |     |
| ---------------- | ---------- | ----------- | ------------ | ---------- | -------- | -------- | ----- | ---------------------- | --- | --- | --- | --- | --- | --- |
|                  |            |             |              |            |          |          |       | A. ASSISTEDINSTRUCTION |     |     |     |     |     |     |
| approach         | for entity | recognition |              | by feeding |          | the word | vec-  |                        |     |     |     |     |     |     |
torsintoabidirectionalLongShortTermMemoryandhav- Assisted instruction refers to approaches to support instruc-
ing the outputs fed into Conditional Random Fields layer tors and faculty members in different aspects of their tasks.
|             |      |      |          |     |                 |     |        | Several | studies | have addressed | this | area using | KGs. | In the |
| ----------- | ---- | ---- | -------- | --- | --------------- | --- | ------ | ------- | ------- | -------------- | ---- | ---------- | ---- | ------ |
| (LSTM-CRF). | They | also | improved |     | the reliability |     | of the |         |         |                |      |            |      |        |
extractedskillentitiesusingclickthroughdataasawayfor next subsections, we describe two subcategories in which
assistedinstructionisthemaintopic.
| entity filtering. | Additionally, |     |     | the relation | extraction | process |     |     |     |     |     |     |     |     |
| ----------------- | ------------- | --- | --- | ------------ | ---------- | ------- | --- | --- | --- | --- | --- | --- | --- | --- |
wasdonethroughdiscoveringthehypernym-hyponymrela-
| tionsbetweenskillentities. |     |     |     |     |     |     |     | 1) INSTRUCTIONALCONCEPTION |     |     |     |     |     |     |
| -------------------------- | --- | --- | --- | --- | --- | --- | --- | -------------------------- | --- | --- | --- | --- | --- | --- |
Oneofthemainareasofeducationalresearchisinstructional
B. REPRESENTATIONLEARNING conceptionanditsroleinstudentslearning.Instructionalcon-
ceptionisthecreationoflearningexperiencesandmaterials
Knowledgerepresentationlearningaimstomapentitiesand
relationsofaKGontoadenselow-dimensionfeaturespace in a manner that results in the acquisition and application
ofknowledgeandskills.Theauthorsof[29]conceptualized
thatcapturestheinformationandthestructureofthegraph.
|          |        |         |     |         |                |     |       | a system | called | KnowEDU | that constructs |     | a KG | for edu- |
| -------- | ------ | ------- | --- | ------- | -------------- | --- | ----- | -------- | ------ | ------- | --------------- | --- | ---- | -------- |
| This was | mainly | carried | out | for job | market-related |     | graph |          |        |         |                 |     |      |          |
applications. Studies such as [37] proposed representation cation automatically. The result was a KG with nodes that
|          |            |      |     |                |     |              |     | represent | instructional | concepts | that | learners | should | master. |
| -------- | ---------- | ---- | --- | -------------- | --- | ------------ | --- | --------- | ------------- | -------- | ---- | -------- | ------ | ------- |
| learning | algorithms | such | as  | Joint Bayesian |     | Personalized |     |           |               |          |      |          |        |         |
Ranking (Joint-BPR) and Joint-Margin In [38], the authors The main purpose of KnowEDU is to identify the prereq-
proposed new algorithms for job representation learning uisite relations between concepts in one course or subject,
|     |     |     |     |     |     |     |     | so that | inter-course | and inter-subject |     | relations |     | can be fur- |
| --- | --- | --- | --- | --- | --- | --- | --- | ------- | ------------ | ----------------- | --- | --------- | --- | ----------- |
usingadirectedgraphasinput.Otherstudies,suchas[6],pro-
posedacollectivemulti-viewrepresentationlearningmethod therexplored.Theinstructionalconceptsareidentifiedfrom
|     |     |     |     |     |     |     |     | pedagogical | data | using recurrent |     | neural | networks | (RNN). |
| --- | --- | --- | --- | --- | --- | --- | --- | ----------- | ---- | --------------- | --- | ------ | -------- | ------ |
1https://spacy.io/universe/project/video-spacys-ner-model
Thelinksbetweentheinstructionalconceptsareestablished
| 80176 |     |     |     |     |     |     |     |     |     |     |     |     | VOLUME10,2022 |     |
| ----- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ------------- | --- |

Y.Fettachetal.:KnowledgeGraphsinEducationandEmployability:ASurveyonApplicationsandTechniques
FIGURE1. TaxonomyofKGapplicationsineducation.
through the probabilistic association rule mining algorithm corresponding relations, including 4 platforms, 604 univer-
byusingstudents’performancedata.Thesamemethodology sities, 18671 teachers and 9312 courses. [35] constructed a
was used for the automatic construction of an educational KG from video lectures by following a methodology that
KGfromK-12educationalsubjects[41].In[42],theauthors consistsoftranscriptextractionfromthevideothenapplying
devised a procedure that enables the automatic construction namedentityrecognition,co-referencerecognitionandtriple
ofaneducationalKGusingamodelthatcombinesBidirec- extraction. The proposed methodology however has many
tionalEncoderRepresentationsfromTransformers(BERT), limitationssuchaslanguagerestrictions,timerestrictionsand
Bidirectional LSTM (BiLSTM) and the CRF model. Their accentrestrictions.
KG was built using two large datasets, specifically subject
teachingresourcesandanonlineencyclopedia. 2) KNOWLEDGEMANAGEMENT
[30]developedastrategyforidentifyingconcepts’prereq- Knowledge management using KGs explored tools such
uisites based on the semantic relations found in a KG. The as SoLeMiO [31] to integrate learning material in popular
process consists of two phases: i) a candidate prerequisite authoring software The study focused on semantic repre-
searchingmodulethatgeneratesaninitiallistofcandidates, sentationbyexploitinginformationfromopenKGsthrough
which are concepts that are members of the same cate- expansion and filtering strategies in order to assist teachers
gory as the target concepts; the associations are established in the authoring process of learning material through semi-
using properties like Common Memberships (CM), Linked automatic annotations. The authors used the identified con-
Concepts (LC) in addition to novel pruning methods; and ceptstoextractandretrieverelatedlearningresourcesfroman
ii) a prerequisite evaluation module, that determines pre- opencorpus.Furthermore,[44]presentedaKG-baseddesign
requisite relationships between concepts using a machine of a scientific publication management model for scientific
learningapproachthatmodelstheproblemasabinaryclas- metadata using data analysis technologies. For evaluation,
sification. In [43], the authors presented a process to sup- theyimplementedtheusecaseofanentrepreneurshipscien-
port domain experts in creating KGs by automating parts tific publication management prototype system, in order to
of their generation. They utilized a method that consisted encouragesustainablelearning.Similarworktackledcourses
of entity recognition, relation extraction and graph comple- allocation and management using KGs [45]. One of the lat-
tionusingtheT-Mitocartool.Thestudyresultedincreating est studies in this direction of research was ELODIE [46],
annotatededucationalKGsforpersonalizedlearning.Inthe a mechanism for knowledge management. The study pre-
same context, [33] adopted an acknowledged educational sented the task at hand as an information retrieval problem.
ontologytoconceptualizeandbuildaKGforMassiveOpen The authors proposed a faceted search interface enhanced
OnlineCourses.Entitiesrepresent28591instanceswiththeir byanaturallanguagequerycapabilities.ELODIEorganises
VOLUME10,2022 80177

Y.Fettachetal.:KnowledgeGraphsinEducationandEmployability:ASurveyonApplicationsandTechniques
nodesandlinksoftheKGbyfacets.Studentscanclickonany systembasedonamulti-viewKG.Thestudystartedbycon-
providedoptiontoformulatetheirqueries.Theusercanthen structingaKGthatpresentsfacultyinformationsuchassci-
manipulate the dataset and visualizations according to their entificresearchpapers,patents,funds,monographs,awards,
needs. The system presents a simple approach for engaging professional activities and teaching performance. Based on
theuserininformationretrievalandknowledgemanagement. the KG embeddings of this data, an academic development
|     |     |     |     |     |     |     |     | factor (ADF) | was | proposed | for | making | predictions | about |
| --- | --- | --- | --- | --- | --- | --- | --- | ------------ | --- | -------- | --- | ------ | ----------- | ----- |
facultyacademicdevelopment.
B. ASSISTEDLEARNING
| Researchers   | argued | that        | using     | KGs | in assessing | students |        |                                   |     |     |     |     |     |     |
| ------------- | ------ | ----------- | --------- | --- | ------------ | -------- | ------ | --------------------------------- | --- | --- | --- | --- | --- | --- |
|               |        |             |           |     |              |          |        | V. KGAPPLICATIONSFOREMPLOYABILITY |     |     |     |     |     |     |
| would improve |        | educational | outcomes. |     | Based        | on our   | inves- |                                   |     |     |     |     |     |     |
Inpreviousstudies,KGsareusedtorepresentandvisualize
tigation,wegrouptheseapplicationsintotwosubcategories,
|     |     |     |     |     |     |     |     | the entities | and | relationships |     | related | to social | commerce, |
| --- | --- | --- | --- | --- | --- | --- | --- | ------------ | --- | ------------- | --- | ------- | --------- | --------- |
asdescribednext.
e.g.[54].Inductivelogicprogrammingtechniqueswereused
| • Personalized |     | Learning | Personalized |     | learning | in  | KGs |     |     |     |     |     |     |     |
| -------------- | --- | -------- | ------------ | --- | -------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
todiscoverimplicitinformationthatcaninterpretthebehav-
| was | presented | as  | techniques | to  | help students |     | engage |          |            |        |        |         |          |            |
| --- | --------- | --- | ---------- | --- | ------------- | --- | ------ | -------- | ---------- | ------ | ------ | ------- | -------- | ---------- |
|     |           |     |            |     |               |     |        | iors and | intentions | of the | users. | In this | section, | we explore |
and understand their study material. [47] constructed a morestudiesthatfocusedonanalyzingthejobmarketusing
personalizedlearningsystembasedonknowledgestruc-
knowledgegraphs.
| tural     | graphs. | They         | then           | defined  | and implemented |             | an  |                      |     |                        |     |     |        |              |
| --------- | ------- | ------------ | -------------- | -------- | --------------- | ----------- | --- | -------------------- | --- | ---------------------- | --- | --- | ------ | ------------ |
| optimized |         | learning     | path generator |          | in order        | to provide  |     |                      |     |                        |     |     |        |              |
|           |         |              |                |          |                 |             |     | A. JOBRECOMMENDATION |     |                        |     |     |        |              |
| learners  | with    | personalized |                | learning | content.        | Interactive |     |                      |     |                        |     |     |        |              |
|           |         |              |                |          |                 |             |     | [38] tackled         |     | the job representation |     |     | aspect | in knowledge |
applications using KGs is a relatively new direction to graphs. The authors developed a representation of job posi-
improveeducation.In[50],theauthorsaddressedinter-
tionsconsistingofjobtitleandcompanypairswhichcaptures
activevisualnavigationandinductivereasoninginKGs. thesimilarityandtheorderingrelationsamongjobpositions.
Visualizationwasalsothetopicofthestudycarriedout
|     |     |     |     |     |     |     |     | In the context |     | of job recommendation, |     |     | [37] | created three |
| --- | --- | --- | --- | --- | --- | --- | --- | -------------- | --- | ---------------------- | --- | --- | ---- | ------------- |
by[49].Theworkevaluatedtheutilityoftheeducational
typesofinformationnetworksfromthehistoricaljobdata:job
KG by a visualization analysis in order to provide a transitionnetwork,job-skillnetwork,andskillco-occurrence
bettercomprehensionofitsstructure.
network.Theauthorsof[37]conceptualizedarepresentation
| Question | Answering |     | [48] | relied | on crowdsourcing |     | to  |     |     |     |     |     |     |     |
| -------- | --------- | --- | ---- | ------ | ---------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
• learning model that uses the information from all three net-
enrichamath-relatedKG(MathGraph).Themainpur-
|     |     |     |     |     |     |     |     | works. This | study | presented | the | pair wise | ranking | objective |
| --- | --- | --- | --- | --- | --- | --- | --- | ----------- | ----- | --------- | --- | --------- | ------- | --------- |
poseoftheKGwastohelpstudentssolvemathematical
whichlearnsjobandskillvectorrepresentationsintoashared
exercises with mathematical derivations and calcula- latentspaceusingthreepre-processedgraphs.
| tions. | The | authors | also presented |     | an algorithm | to  | align |        |         |         |           |     |       |              |
| ------ | --- | ------- | -------------- | --- | ------------ | --- | ----- | ------ | ------- | ------- | --------- | --- | ----- | ------------ |
|        |     |         |                |     |              |     |       | Recent | studies | started | exploring | the | graph | based recom- |
asemanticallyparsedexercisetoMathGraphinorderto
|     |     |     |     |     |     |     |     | mendation | systems. | For | example, | [55] | developed | a recom- |
| --- | --- | --- | --- | --- | --- | --- | --- | --------- | -------- | --- | -------- | ---- | --------- | -------- |
automaticallyresolvethemathematicalproblem. mender system by measuring the skill importance of each
occupationforeachcountryandfeedingthebestvectormodel
C. EDUCATIONALASSESSMENT toagraphdatabase.[56]builtaKGbasedrecommendersys-
Educationalassessmentfocusesonassessmentofalearner’s temforjobscalledGUApp.Thelatterrecommendsrelevant
knowledgeandthelevelofskilltheyhaveacquired.Multiple jobstotheusers.Thesystemalsointegratesadomain-specific
|     |     |     |     |     |     |     |     | KG that | allows | it to support | natural |     | dialogues | with users |
| --- | --- | --- | --- | --- | --- | --- | --- | ------- | ------ | ------------- | ------- | --- | --------- | ---------- |
studiestacklethisaspectusingKGs.[32]exploredestablish-
ingteachersupportmethodologieswheretheauthorsadopted about the discussed domain. This leads to an improvement
a KG-based approach to detect plagiarism. They focus on inthequalityofrecommendationsresults.Lastbutnotleast,
buildingasemanticKGfromunstructureddata.Thebuiltsys- [57] proposed an explainable job recommendation system,
temimplementsentityrecognition,followedbyrelationship whichusesaKGstomodeljob-postingsanduserprofilesinto
extraction, then performs a co-reference resolution. It uses aunifiedframework.Thesystemgenerateshuman-readable
semanticsimilarityandsentencereplacementforpurposeof explanation for each recommendation based on the graph
plagiarismdetection. structureitselfandanamedentityclassifier.
KGsalsocontributedtoadvancingthequestiongeneration
fieldespeciallyineducation.[51]implementedanend-to-end B. JOB-SKILLMATCHINGANDTALENTINTELLIGENCE
approachtogeneratenaturallanguagequestionsfromknowl- ThelateststudiesinthisdirectionistheSkills&Occupation
edgegraphs.Anentityisfirstselectedasananswer.Astruc- KG that was created in [58]. The KG was built by leverag-
turedtriple-patternqueryhavingthisanswerasitssoleresult ingexistingskillsandoccupationtaxonomiesenrichedwith
isthengenerated.Ifamultiple-choicequestionisdesired,the externaljobposting.[35]builtaKGrepresentingtheartificial
approachselectsalternativeansweroptions.Italsoadoptsa intelligencejobmarketandthecorrespondingskillsrequired.
templatebasedmethodtoverbalizethestructuredqueryand TheKGwasusedtoexploretherelationshipofdifferentkey
yield a natural language question. The authors based their skillsofartificialintelligence.
approach on an earlier methodology that follows the same Talentintelligenceexplorationstartedwith[6]presentinga
pattern [52]. [53] presented a university faculty evaluation data-drivenapproachforjobtitlebenchmarking.Theauthors
| 80178 |     |     |     |     |     |     |     |     |     |     |     |     |     | VOLUME10,2022 |
| ----- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ------------- |

Y.Fettachetal.:KnowledgeGraphsinEducationandEmployability:ASurveyonApplicationsandTechniques
TABLE1. KGapplicationsineducation.
constructedajobtitletransitiongraphwherenodesrepresent in mediating between the needs of industry and research.
jobtitlesandlinksdenotethecorrelationsbetweenjobs.They [63]emphasizedtheimportanceofsoftbusiness-relatedskills
purpose of the study was to provide an accurate guidance andcompetenciesandtheneedforpriorwork-experiences.
andconsiderableconvenienceforbothtalentrecruitmentand Investigatingthedynamicsbetweeneducationandthejob
jobseekersforpositionandsalarycalibrationandprediction. market is a very relevant issue which has been investigated
Otherlike[36]constructedaKGofjobskillsthroughmining in many ways before. Addressing this issue using KGs is
theabundanthistoricalrecruitmentdata.Theauthorsutilized aninterestingresearchdirection.Weillustratethisusingthe
theconstructedSkill-Graphforbuildingapersonalizedques- followingcasestudy.
tionrecommendationalgorithmforimprovingjobinterview
assessment.
VII. CASESTUDY:DATASCIENCE/AI
A summary of the studies is provided in the reference Here, we propose a framework to showcase the use of KG
tables1and2. in the fusion of education and employability information.
Theframeworkisbasedontheideathateducationprovides
studentswithcertainskillsandthejobmarketneedscertain
VI. TOWARDSAUNIFIEDFRAMEWORKFOREDUCATION skillstoaccomplishtasksinacertainjob.Thisleadsustorely
ANDEMPLOYABILITY onskillstobuildlinksbetweenthejobmarketandeducation.
Researchhasshownalotofinterestindiagnosingtheissues Figure 3 illustrates a subgraph of the entire KG, built to
thateducationandespeciallyhighereducationsuffersfrom,
describetheskillsneededforacertainjobandthecoursesthat
specificallywhenconsideringthejobmarket.Previouswork
|     |     |     |     |     | offer to teach | those skills. | We choose | as a case | study about |
| --- | --- | --- | --- | --- | -------------- | ------------- | --------- | --------- | ----------- |
hasanalyzedtherelationshipbetweenacademiaandthejob datasciencejobs.Weaimtogiveafullpictureofwhatskills
markettounderstandhowtheyinfluenceeachother[59].[60]
|     |     |     |     |     | one would | need in order | to compete | for a certain | job. The |
| --- | --- | --- | --- | --- | --------- | ------------- | ---------- | ------------- | -------- |
examinedthecollaborationsbetweenstakeholdersandhigher schema should encompass all aspects of data science jobs,
educationinstitutionstoidentifythelackofcommunication
|         |                |                |               |       | the skills | needed for a | given job | and the courses | that teach |
| ------- | -------------- | -------------- | ------------- | ----- | ---------- | ------------ | --------- | --------------- | ---------- |
| between | the job market | and the youth. | Other studies | aimed |            |              |           |                 |            |
theseskills.TheKGmaybeusedasrecommendersystemfor
to determine the relationship between skill mismatch and studentstoidentifytheskillsneededforthejobtheywant,for
| the regional | unemployment. | Researchers | found that | regions |     |     |     |     |     |
| ------------ | ------------- | ----------- | ---------- | ------- | --- | --- | --- | --- | --- |
institutionstoupdatetheircoursesaccordingtothejobmarket
with higher skilled populations have lower unemployment evolutionandeventuallyalsotopredictadditionallinks.
rates [61]. [62] presented multiple data analyses and visu- We used a public dataset of data science/AI job offers
| alizations | to understand | discrepancies | and temporal | delays |           |               |           |                |          |
| ---------- | ------------- | ------------- | ------------ | ------ | --------- | ------------- | --------- | -------------- | -------- |
|            |               |               |              |        | collected | from Indeed.2 | Each line | in the dataset | contains |
between evolving job market needs, course offerings, and the job title, the company that posted the job offer and the
| science | and technology | developments. | The findings | of this |     |     |     |     |     |
| ------- | -------------- | ------------- | ------------ | ------- | --- | --- | --- | --- | --- |
2www.indeed.com
worksuggestthateducationaleffortsplayanimportantrole
| VOLUME10,2022 |     |     |     |     |     |     |     |     | 80179 |
| ------------- | --- | --- | --- | --- | --- | --- | --- | --- | ----- |

Y.Fettachetal.:KnowledgeGraphsinEducationandEmployability:ASurveyonApplicationsandTechniques
TABLE2. KGapplicationsinemployability.
| FIGURE2. | Methodologyforjob-skill-courseKGconstruction. |     |     |     |     |     |     |
| -------- | --------------------------------------------- | --- | --- | --- | --- | --- | --- |
hard skills needed for the job. We define hard skills as the goals. The weight of the relationship between nodes is the
technical skills needed to complete a certain task, whereas numberofco-occurrencesoftheseentities.Wenormalizethe
soft skills are abilities that are related to how an individual weightsinordertohavevaluesbetween0and1.
worksandinteractswithothers.Inourstudy,wefocussolely For visualization purposes, we chose the top ten skills
onhardskillsforsimplicityreasons.Wecollecteddataabout required for a data scientist (the edges with the highest
Massive Open Online Courses using a Web crawler where weights that are connected to the node ’data scientist’),
we gathered attributes such as the name of the course, the as shown in Figure 3 and the top two courses for each skill
university that offers the course, and the language in which (theedgeswiththehighestweightsthatareconnectedtothe
thecourseistaught.Inaddition,usingthecategoriesoffered chosenskills).
| by the Website | and entity | recognition, we | created a list of |     |     |     |     |
| -------------- | ---------- | --------------- | ----------------- | --- | --- | --- | --- |
skills for each course, extracted from the course title, the VIII. FUTURERESEARCHDIRECTIONS
descriptionofthecourseanditscategory.Afullviewofthe Inthissection,wediscussthelimitationsoftheexistingwork
pipelineadoptedinourframeworkispresentedinFigure2. andproposeresearchdirectionsforfuturework.
We created two weighted directed graphs: the first one • KGConstructionandDataQualityMostoftheexist-
has nodes as jobs and skill entities (Skill-Job KG) and ing work paid very little attention to discussing the
the second one has nodes representing skills and courses detailsofandthemotivationsbehindthetechniquesused
(Skill-CourseKG).InordertocreatethefinalKG,werelyon for entity recognition and relation extraction. It would
|     |     |     |     | be interesting | to compare these | techniques | in order to |
| --- | --- | --- | --- | -------------- | ---------------- | ---------- | ----------- |
semanticmatchingforentityalignmentbetweentheSkill-Job
KG and Skill-Course KG for the skill entity. The KG is identifythosethatperformthebestinthedifferenttasks.
heterogeneousasitcontainsthreetypesofnodes:jobs,skills Furthermore, to the best of our knowledge, there are
and courses. The job nodes are linked to certain skill nodes no methods to fully automate the process of KG con-
based on the skills needed for the job, and skill nodes are struction.Developingsuchmethodswouldbeapromis-
|                   |              |          |                     | ing research | direction, particularly | when | dealing with |
| ----------------- | ------------ | -------- | ------------------- | ------------ | ----------------------- | ---- | ------------ |
| linked to certain | course nodes | based on | the fact that these |              |                         |      |              |
courses offer teaching those skills as part of their course large-scaleunstructuredcontent.
| 80180 |     |     |     |     |     |     | VOLUME10,2022 |
| ----- | --- | --- | --- | --- | --- | --- | ------------- |

Y.Fettachetal.:KnowledgeGraphsinEducationandEmployability:ASurveyonApplicationsandTechniques
FIGURE3. Asnapshotofjob-skill-courseknowledgegraph.Thebluenodesrepresentthejobtitles,thepink
nodesrepresenttheskills,andthegreennodesrepresentthecourses.
Themethodologiesreviewedinthispaperdidnotcon- limitation of traditional knowledge representation and
sidertheuseofstandardizedandappropriatedataquality reasoningbyconsideringthetemporaldimension[1].
measures when constructing KGs. The data collection • KG-based recommendation KG-based recommender
processgavelittleconsiderationtothecredibilityofthe systems attracted considerable interest in recent years.
generatedinformation.Aninterestingresearchdirection Unliketraditionalrecommendersystems,KG-basedrec-
wouldbetodevelopmethodstoevaluatethecredibility ommendersystemspresentavarietyofentitiesandrela-
of the information generated from KGs. This could be tions linking users and items, and illustrate better the
carried out by building probabilistic KGs where each reasoning process. Generating recommendations with
relation/linkisassociatedwithameasureofitscertainty. theKGassideinformationforjobrecommendationand
• TemporalKGsTemporalKGsareoneofthenewdirec- curriculumdesignwouldbenefitinstitutions,jobseekers
tions that researchers have recently started to explore and employers. Advancements in this field focus on
especially in education. This need to expansion comes multi-tasklearningwheretransferringknowledgefrom
fromthefactthatstaticKGsdonotgiveafullrepresen- KG-related tasks, such as entity representation, classi-
tationaboutrealworlddataandareonlyconsideredto ficationandresolutionwouldenhancerecommendation
beastaticsnapshotofmulti-relationaldata.Studiessuch performance[67].
as[64]initiatedresearchinthisdirectionbyconstruct-
ing a novel deep evolutionary knowledge network that
efficientlylearnsnon-linearlyevolvingentityrepresen- IX. CONCLUSION
tationsovertimeinamulti-relationalsetting. The use of knowledge graphs to improve education and
WorkonincorporatingtemporalKGsinthejobmarketis employability has received much attention in recent liter-
verylimited.Therehasbeensomedescriptiveworkdone ature. This study examined the different applications of
onusingtime-seriesonclustersofskillsetsforjobmar- such knowledge graphs as well as the approaches taken to
ketforecasting[65],[66].AdynamicKG,togetherwith construct them. We detailed these studies by categorizing
learningalgorithmscapturingdynamics,canaddressthe them into different aspects of education and employability.
VOLUME10,2022 80181

Y.Fettachetal.:KnowledgeGraphsinEducationandEmployability:ASurveyonApplicationsandTechniques
Tocontributetoreducingthemismatchbetweenhigheredu- [21] S.Changuel,N.Labroche,andB.Bouchon-Meunier,‘‘Resourcessequenc-
cation and market need, we advocate the development and ingusingautomaticprerequisite-outcomeannotation,’’ACMTrans.Intell.
Syst.Technol.,vol.6,no.1,pp.1–30,Mar.2015.
exploitationofknowledgegraphsthatjointlyrepresentedu-
[22] F.Gasparetti,C.DeMedio,C.Limongelli,F.Sciarrone,andM.Temperini,
cationandjobmarketdata.Asasteptowardsthis,weintro- ‘‘Prerequisitesbetweenlearningobjects:Automaticextractionbasedon
ducedaframeworkforbuildingsuchknowledgegraphs,and a machine learning approach,’’ Telematics Informat., vol. 35, no. 3,
pp.595–610,Jun.2018.
use the field of data science/AI as a case study. A number
[23] S. Wang, A. Ororbia, Z. Wu, K. Williams, C. Liang, B. Pursel, and
of research avenues remain to be explored, and this article C.L.Giles,‘‘UsingprerequisitestoextractconceptmapsfromTextbooks,’’
discussedafew. inProc.25thACMInt.Conf.Inf.Knowl.Manage.,Oct.2016,pp.317–326.
[24] C.Zhu,H.Zhu,H.Xiong,C.Ma,F.Xie,P.Ding,andP.Li,‘‘Person-jobfit:
Adaptingtherighttalentfortherightjobwithjointrepresentationlearn-
REFERENCES ing,’’ACMTrans.Manage.Inf.Syst.,vol.9,no.3,pp.1–17,Sep.2018.
[1] S. Ji, S. Pan, E. Cambria, P. Marttinen, and P. S. Yu, ‘‘A survey on [25] C. Qin, H. Zhu, T. Xu, C. Zhu, C. Ma, E. Chen, and H. Xiong,
knowledgegraphs:Representation,acquisitionandapplications,’’2020, ‘‘Anenhancedneuralnetworkapproachtoperson-jobfitintalentrecruit-
arXiv:2002.00388. ment,’’ACMTrans.Inf.Syst.,vol.38,no.2,pp.1–33,Mar.2020.
[2] X.Zou,‘‘Asurveyonapplicationofknowledgegraph,’’J.Phys.,Conf., [26] W.Shalaby,B.Alaila,M.Korayem,L.Pournajaf,K.AlJadda,S.Quinn,
vol.1487,Mar.2020,Art.no.012016. andW.Zadrozny,‘‘Helpmefindajob:Agraph-basedapproachforjob
[3] M.Hussain,W.Zhu,W.Zhang,S.M.R.Abidi,andS.Ali,‘‘Usingmachine recommendationatscale,’’inProc.IEEEInt.Conf.BigData(BigData),
learningtopredictStudentdifficultiesfromlearningsessiondata,’’Artif. Dec.2017,pp.1544–1553.
Intell.Rev.,vol.52,no.1,pp.381–407,Jun.2019. [27] H.Xu,Z.Yu,J.Yang,H.Xiong,andH.Zhu,‘‘Talentcircledetectionin
[4] F. Bousbahi and H. Chorfi, ‘‘MOOC-Rec: A case based recommender jobtransitionnetworks,’’inProc.22ndACMSIGKDDInt.Conf.Knowl.
systemforMOOCs,’’Proc.SocialBehav.Sci.,vol.195,pp.1813–1822, DiscoveryDataMining,Aug.2016,pp.655–664.
Jul.2015. [28] Y.Mao,‘‘Summaryandevaluationoftheapplicationofknowledgegraphs
[5] A. Fedorets, F. Lottmann, and M. Stops, ‘‘Job matching in connected ineducation2007–2020,’’DiscreteDyn.NatureSoc.,vol.2021,pp.1–10,
regionalandoccupationallabourmarkets,’’RegionalStud.,vol.53,no.8, Sep.2021.
pp.1085–1098,Aug.2019. [29] P. Chen, Y. Lu, V. W. Zheng, X. Chen, and B. Yang, ‘‘KnowEdu: A
[6] D. Zhang, J. Liu, H. Zhu, Y. Liu, L. Wang, P. Wang, and H. Xiong, systemtoconstructknowledgegraphforeducation,’’IEEEAccess,vol.6,
‘‘Job2Vec:Jobtitlebenchmarkingwithcollectivemulti-viewrepresenta- pp.31553–31563,2018.
tionlearning,’’inProc.28thACMInt.Conf.Inf.Knowl.Manage.,2019, [30] R.Manrique,B.Pereira,andO.Mariño,‘‘Exploringknowledgegraphsfor
pp.2763–2771. theidentificationofconceptprerequisites,’’SmartLearn.Environments,
[7] I.Khaouja,G.Mezzour,K.M.Carley,andI.Kassou,‘‘Buildingasoftskill vol.6,no.1,pp.1–18,Dec.2019.
taxonomyfromjobopenings,’’SocialNetw.Anal.Mining,vol.9,no.1, [31] C. Grévisse, R. Manrique, O. Mariño, and S. Rothkugel, ‘‘Knowl-
pp.1–19,Dec.2019. edge graph-based teacher support for learning material authoring,’’ in
[8] N.Pontika,‘‘Rolesandjobsintheopenresearchscholarlycommunications Proc. Colombian Conf. Comput. Cham, Switzerland: Springer, 2018,
environment:Analysingjobdescriptionstopredictfuturetrends,’’LIBER pp.177–191.
Quarterly,J.Assoc.Eur.Res.Libraries,vol.29,no.1,pp.1–20,Jul.2019. [32] K. Khadilkar, S. Kulkarni, and P. Bone, ‘‘Plagiarism detection using
[9] X. Dong, E. Gabrilovich, G. Heitz, W. Horn, N. Lao, K. Murphy, semanticknowledgegraphs,’’inProc.4thInt.Conf.Comput.Commun.
T.Strohmann, S.Sun,and W.Zhang,‘‘Knowledge vault:Aweb-scale ControlAutom.(ICCUBEA),Aug.2018,pp.1–6.
approachtoprobabilisticknowledgefusion,’’inProc.20thACMSIGKDD [33] F.Dang,J.Tang,andS.Li,‘‘MOOC-KG:AMOOCknowledgegraph
Int.Conf.Knowl.DiscoveryDataMining,Aug.2014,pp.601–610. forcross-platformonlinelearningresources,’’inProc.IEEE9thInt.Conf.
[10] A.Hogan,E.Blomqvist,M.Cochez,C.d’Amato,G.deMelo,C.Gutierrez, Electron.Inf.EmergencyCommun.(ICEIEC),Jul.2019,pp.1–8.
J. E. L. Gayo, S. Kirrane, S. Neumaier, A. Polleres, R. Navigli, [34] G.S.Shanmukhaa,S.K.Nandita,andM.V.K.Kiran,‘‘Constructionof
A.-C.N.Ngomo,S.M.Rashid,A.Rula,L.Schmelzeisen,J.Sequeda, knowledgegraphsforvideolectures,’’inProc.6thInt.Conf.Adv.Comput.
S. Staab, and A. Zimmermann, ‘‘Knowledge graphs,’’ 2020, Commun.Syst.(ICACCS),Mar.2020,pp.127–131.
arXiv:2003.02320. [35] S. Jia, X. Liu, P. Zhao, C. Liu, L. Sun, and T. Peng, ‘‘Representation
[11] Y. Dai, S. Wang,N. N. Xiong, and W. Guo, ‘‘Asurvey on knowledge ofjob-skillinartificialintelligencewithknowledgegraphanalysis,’’in
graphembedding:Approaches,applicationsandbenchmarks,’’Electron- Proc.IEEESymp.ProductComplianceEng.Asia(ISPCE-CN),Dec.2018,
ics,vol.9,no.5,p.750,May2020. pp.1–6.
[12] M.Papoutsoglou,A.Ampatzoglou,N.Mittas,andL.Angelis,‘‘Extracting [36] C.Qin,H.Zhu,C.Zhu,T.Xu,F.Zhuang,C.Ma,J.Zhang,andH.Xiong,
knowledgefromon-linesourcesforsoftwareengineeringlabormarket:A ‘‘DuerQuiz:Apersonalizedquestionrecommendersystemforintelligent
mappingstudy,’’IEEEAccess,vol.7,pp.157595–157613,2019. jobinterview,’’inProc.25thACMSIGKDDInt.Conf.Knowl.Discovery
[13] I.Khaouja,I.Kassou,andM.Ghogho,‘‘Asurveyonskillidentification DataMining,Jul.2019,pp.2165–2173.
fromonlinejobads,’’IEEEAccess,vol.9,pp.118134–118153,2021. [37] V. S. Dave, B. Zhang, M. Al Hasan, K. AlJadda, and M. Korayem,
[14] M. Rizun, ‘‘Knowledge graph application in education: A literature ‘‘A combined representation learning approach for better job and skill
review,’’ActaUniversitatisLodziensis.FoliaOeconomica,vol.3,no.342, recommendation,’’ in Proc. 27th ACM Int. Conf. Inf. Knowl. Manage.,
pp.7–19,Aug.2019. Oct.2018,pp.1997–2005.
[15] B.Abu-Salih,‘‘Domain-specificknowledgegraphs:Asurvey,’’J.Netw. [38] H.Luo,S.Ma,A.J.B.Selvaraj,andY.Sun,‘‘Learningjobrepresentation
Comput.Appl.,vol.185,Jul.2021,Art.no.103076. usingdirectedgraphembedding,’’inProc.1stInt.WorkshopDeepLearn.
[16] C. Liang, J. Ye, Z. Wu, B. Pursel, and C. Giles, ‘‘Recovering concept PracticeHigh-DimensionalSparseData,2019,pp.1–5.
prerequisiterelationsfromuniversitycoursedependencies,’’inProc.AAAI [39] J.-J.Decorte,J.VanHautte,T.Demeester,andC.Develder,‘‘JobBERT:
Conf.Artif.Intell.,2017,pp.1–6. Understandingjobtitlesthroughskills,’’2021,arXiv:2109.09605.
[17] L.Pan,C.Li,J.Li,andJ.Tang,‘‘Prerequisiterelationlearningforconcepts [40] S.Yao,R.Wang,S.Sun,D.Bu,andJ.Liu,‘‘Jointembeddinglearningof
inmoocs,’’inProc.55thAnnu.MeetingAssoc.Comput.Linguistics,vol.1, educationalknowledgegraphs,’’inArtificialIntelligenceSupportedEdu-
2017,pp.1447–1456. cationalTechnologies.Cham,Switzerland:Springer,2020,pp.209–224.
[18] J.Gordon,L.Zhu,A.Galstyan,P.Natarajan,andG.Burns,‘‘Modeling [41] P.Chen,Y.Lu,V.W.Zheng,X.Chen,andX.Li,‘‘Anautomaticknowledge
conceptdependenciesinascientificcorpus,’’inProc.54thAnnu.Meeting graphconstructionsystemforK-12education,’’inProc.5thAnnu.ACM
Assoc.Comput.Linguistics,2016,pp.866–875. Conf.Learn.atScale,Jun.2018,pp.1–4.
[19] Y.Yang,H.Liu,J.Carbonell,andW.Ma,‘‘Conceptgraphlearningfrom [42] Y.SuandY.Zhang,‘‘Automaticconstructionofsubjectknowledgegraph
educationaldata,’’inProc.8thACMInt.Conf.WebSearchDataMining, basedoneducationalbigdata,’’inProc.3rdInt.Conf.BigDataEduc.,
Feb.2015,pp.159–168. Apr.2020,pp.30–36.
[20] P. Talukdar and W. Cohen, ‘‘Crowdsourced comprehension: Predicting [43] R.Manrique,B.Pereira,andO.Marino,‘‘Exploringknowledgegraphsfor
prerequisitestructureinWikipedia,’’inProc.7thWorkshopBuildingEduc. theidentificationofconceptprerequisites,’’SmartLearn.Environ.,vol.6,
Appl.UsingNLP,pp.307–315.2012. pp.1–18,Dec.2019.
80182 VOLUME10,2022

Y.Fettachetal.:KnowledgeGraphsinEducationandEmployability:ASurveyonApplicationsandTechniques
[44] Y.Chi,Y.Qin,R.Song,andH.Xu,‘‘Knowledgegraphinsmarteducation: [66] E. M. Sibarani and S. Scerri, ‘‘SCoDis: Job advert-derived time series
A case study of entrepreneurship scientific publication management,’’ for high-demand skillset discovery and prediction,’’ in Proc. Int. Conf.
Sustainability,vol.10,no.4,p.995,Mar.2018. DatabaseExpertSyst.Appl.Springer,2020,pp.366–381.
[45] I.Aliyu,A.F.D.Kana,andS.Aliyu,‘‘Developmentofknowledgegraph [67] Q.Guo,F.Zhuang,C.Qin,H.Zhu,X.Xie,H.Xiong,andQ.He,‘‘Asurvey
foruniversitycoursesmanagement,’’Int.J.Educ.Manage.Eng.,vol.10, onknowledgegraph-basedrecommendersystems,’’IEEETrans.Knowl.
no.2,p.1,2020. DataEng.,vol.34,no.8,pp.3549–3568,Aug.2020.
[46] D.R.De,M.Garofalo,D.Malandrino,M.A.Pellegrino,andA.Petta,
| ‘‘Education | meets | knowledge | graphs | for the | knowledge | management,’’ |     |     |     |     |
| ----------- | ----- | --------- | ------ | ------- | --------- | ------------- | --- | --- | --- | --- |
inProc.Int.Conf.MethodologiesIntell.Syst.Technol.EnhancedLearn.
Cham,Switzerland:Springer,2020,pp.272–280.
[47] X.Huang,‘‘StudyofpersonalizedE-learningsystembasedonknowledge
structuralgraph,’’Proc.Eng.,vol.15,pp.3366–3370,Jan.2011.
[48] T.Zhao,C.Chai,Y.Luo,J.Feng,Y.Huang,S.Yang,H.Yuan,H.Li,K.Li, YOUSRA FETTACH received the M.Sc. degree
F.Zhu,andK.Pan,‘‘Towardsautomaticmathematicalexercisesolving,’’ fromENSIAS,Rabat,Morocco,in2019,witha
DataSci.Eng.,vol.4,no.3,pp.179–192,Sep.2019. majorindatascienceandbigdata.Sheiscurrently
[49] K.Sun,Y.Liu,Z.Guo,andC.Wang,‘‘EduVis:Visualizationforeducation
pursuingthePh.D.degreewiththeInternational
knowledgegraphbasedonwebdata,’’inProc.9thInt.Symp.Vis.Inf.
UniversityofRabat.Herresearchinterestsinclude
Commun.Interact.,Sep.2016,pp.138–139.
knowledgegraphsandNLP.Shewasarecipientof
| [50] V. Telnov | and | Y. Korovin, | ‘‘Semantic | web | and interactive | knowledge |     |     |     |     |
| -------------- | --- | ----------- | ---------- | --- | --------------- | --------- | --- | --- | --- | --- |
graphs as an educational technology,’’ in Cloud Computing Security- theUIRresearchscholarship,in2020.
ConceptsandPractice.London,U.K.:IntechOpen,2020.
| [51] D. Seyler, | M.        | Yahya, and | K. Berberich, | ‘‘Knowledge |       | questions from     |     |     |     |     |
| --------------- | --------- | ---------- | ------------- | ----------- | ----- | ------------------ | --- | --- | --- | --- |
| knowledge       | graphs,’’ | in         | Proc. ACM     | SIGIR Int.  | Conf. | Theory Inf. Retr., |     |     |     |     |
Oct.2017,pp.11–18.
[52] D.Seyler,M.Yahya,andK.Berberich,‘‘Generatingquizquestionsfrom
knowledgegraphs,’’inProc.24thInt.Conf.WorldWideWeb,May2015,
pp.113–114.
[53] Q.Lin,Y.Zhu,H.Lu,K.Shi,andZ.Niu,‘‘Improvinguniversityfaculty
|             |     |            |           |          |        |                | MOUNIR | GHOGHO | received the | M.Sc. and |
| ----------- | --- | ---------- | --------- | -------- | ------ | -------------- | ------ | ------ | ------------ | --------- |
| evaluations | via | multi-view | knowledge | graph,’’ | Future | Gener. Comput. |        |        |              |           |
Syst.,vol.117,pp.181–192,Apr.2021. Ph.D. degrees from the National Polytechnic
[54] L. Yuan, Z. Huang, W. Zhao, and P. Stakhiyevich, ‘‘Interpreting and Institute of Toulouse, France, in 1993 and
predictingsocialcommerceintentionbasedonknowledgegraphanalysis,’’ 1997, respectively. He was an EPSRC Research
Electron.CommerceRes.,vol.20,no.1,pp.197–222,Mar.2020. Fellow with the University of Strathclyde
[55] A.Giabelli,L.Malandri,F.Mercorio,M.Mezzanzanica,andA.Seveso, (Scotland), from September 1997 to November
| ‘‘Skills2Job: | A   | recommender | system | that | encodes | job offer embed- |     |     |     |     |
| ------------- | --- | ----------- | ------ | ---- | ------- | ---------------- | --- | --- | --- | --- |
2001.InDecember2001,hejoinedtheSchoolof
| dings | on graph | databases,’’ | Appl. | Soft Comput., | vol. | 101, Mar. 2021, |     |     |     |     |
| ----- | -------- | ------------ | ----- | ------------- | ---- | --------------- | --- | --- | --- | --- |
ElectronicandElectricalEngineering,University
Art.no.107049.
ofLeeds,U.K.,wherehewaspromotedtoaFull
[56] G.M.Biancofiore,T.DiNoia,E.DiSciascio,F.Narducci,andP.Pastore,
Professor,in2008.Whilestillaffiliatedwiththe
‘‘Enhancingjobrecommendationswithknowledgegraphs,’’MDPI,Basel,
Switzerland,Tech.Rep.116-138,2021. University of Leeds, in 2010, he joined the International University of
Rabat(Morocco),whereheiscurrentlytheDeanoftheCollegeofDoctoral
| [57] C. Upadhyay, |     | H. Abu-Rasheed, |     | C. Weber, | and M. | Fathi, ‘‘Explain- |     |     |     |     |
| ----------------- | --- | --------------- | --- | --------- | ------ | ----------------- | --- | --- | --- | --- |
StudiesandtheDirectoroftheICTResearchLaboratory(TICLab).Hewas
| able | job-posting | recommendations |     | using knowledge | graphs | and named |     |     |     |     |
| ---- | ----------- | --------------- | --- | --------------- | ------ | --------- | --- | --- | --- | --- |
arecipientofthe2013IBMFacultyAward,andarecipientofthe2000U.K.
entityrecognition,’’inProc.IEEEInt.Conf.Syst.,Man,Cybern.(SMC),
RoyalAcademyofEngineeringResearchFellowship.HeistheCo-Founder
Oct.2021,pp.3291–3296.
[58] M.deGroot,J.Schutte,andD.Graus,‘‘Jobposting-enrichedknowledge andtheCo-DirectoroftheCNRS-AssociatedInternationalResearchLab-
graphforskills-basedmatching,’’2021,arXiv:2109.02554. oratory DataNet, in the field of big data and artificial intelligence. His
[59] S.Angioni,A.A.Salatino,F.Osborne,D.R.Recupero,andE.Motta, researchinterestsincludemachinelearning,signalprocessing,andwireless
‘‘Integrating knowledge graphs for analysing academia and industry communication,onwhichhehaspublishedover300papersinjournalsand
dynamics,’’inProc.ADBIS,TPDLEDACommonWorkshopsDoctoral
conferences.Hehascoordinatedaround20researchprojectsandsupervised
Consortium.Cham,Switzerland:Springer,2020,pp.219–225.
over30Ph.D.studentsintheU.K.andMorocco.Inthepast,heservedasan
| [60] I. Khaouja, | I.  | Makdoun, | G. Mezzour, | I.  | Rahhal, | H. Benchekroun, |     |     |     |     |
| ---------------- | --- | -------- | ----------- | --- | ------- | --------------- | --- | --- | --- | --- |
AssociateEditorformanyjournals,includingtheIEEESignalProcessing
Y.ElHatib,andI.Kassou,‘‘Socialnetworkanalysisofjobmarketstake- MagazineandtheIEEETRANSACTIONSONSIGNALPROCESSING.
holdersinMorocco,’’inProc.Int.Conf.SocialComput.,Behav.-Cultural
Modeling,Predict.Behav.Represent.ModelingSimulation,Washington,
DC,USA,2017.
| [61] A. Newell, | ‘‘Skill  | mismatch | and     | regional unemployment |     | in Poland,’’    |     |     |     |     |
| --------------- | -------- | -------- | ------- | --------------------- | --- | --------------- | --- | --- | --- | --- |
| in The          | European | Labour   | Market. | Cham, Switzerland:    |     | Springer, 2006, |     |     |     |     |
pp.187–202.
[62] K.Börner,O.Scrivner,M.Gallant,S.Ma,X.Liu,K.Chewning,L.Wu,
|     |     |     |     |     |     |     | BOUALEM | BENATALLAH | (Fellow, | IEEE) has |
| --- | --- | --- | --- | --- | --- | --- | ------- | ---------- | -------- | --------- |
andJ.A.Evans,‘‘Skilldiscrepanciesbetweenresearch,education,andjobs
|     |     |     |     |     |     |     | beenaFullProfessorincomputing |     |     | withDublin |
| --- | --- | --- | --- | --- | --- | --- | ----------------------------- | --- | --- | ---------- |
revealthecriticalneedtosupplysoftskillsforthedataeconomy,’’Proc.
|     |     |     |     |     |     |     | City University | (DCU), | Ireland, since | January |
| --- | --- | --- | --- | --- | --- | --- | --------------- | ------ | -------------- | ------- |
Nat.Acad.Sci.USA,vol.115,no.50,pp.12630–12637,Dec.2018.
2022.Hehashadover21yearsasaSeniorLec-
[63] J.AndrewsandH.Higson,‘‘Graduateemployability,‘Softskills’versus
‘hard’businessknowledge:AEuropeanstudy,’’HigherEduc.Eur.,vol.33, turer,anAssociateProfessor,aProfessor,thena
no.4,pp.411–422,Dec.2008. ScientiaProfessorwithUNSWSydney,Australia.
|     |     |     |     |     |     |     | His research | interests include | developing | funda- |
| --- | --- | --- | --- | --- | --- | --- | ------------ | ----------------- | ---------- | ------ |
[64] R.Trivedi,H.Dai,Y.Wang,andL.Song,‘‘Know-evolve:Deeptemporal
|           |             |     |           |           |          |                  | mental concepts | and techniques        | in    | web service |
| --------- | ----------- | --- | --------- | --------- | -------- | ---------------- | --------------- | --------------------- | ----- | ----------- |
| reasoning | for dynamic |     | knowledge | graphs,’’ | in Proc. | Int. Conf. Mach. |                 |                       |       |             |
|           |             |     |           |           |          |                  | composition,    | services engineering, | crowd | sourc-      |
Learn.,2017,pp.3462–3471.
[65] E.M.SibaraniandS.Scerri,‘‘Generatinganevolvingskillsnetworkfrom ingservices,datacuration,cognitiveservices,and
jobadvertsforhigh-demandskillsetdiscovery,’’inProc.Int.Conf.Web businessprocessesmanagement.
Inf.Syst.Eng.Cham,Switzerland:Springer,2020,pp.441–457.
| VOLUME10,2022 |     |     |     |     |     |     |     |     |     | 80183 |
| ------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ----- |