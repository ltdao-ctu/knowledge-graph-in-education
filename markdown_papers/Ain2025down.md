---
title: "Ain2025down"
source: "Ain2025down.pdf"
source_sha256: "ca5d18f045684ed04729d5b7e459ce94e259e388ad02fa60f0fa24f924dfd932"
converted_at: "2026-10-26T07:04:53.121353+00:00"
markitdown_version: "0.1.9"
---
Top-Down vs. Bottom-Up Approaches for
Automatic Educational Knowledge Graph
Construction in CourseMapper
Qurat Ul Ain, Mohamed Amine Chatti, Amr Shakhshir, Jean Qussa, Rawaa
Alatrash, and Shoeb Joarder
Social Computing Group, Faculty of Computer Science, University of
Duisburg-Essen, Germany
Abstract. TheautomaticconstructionofEducationalKnowledgeGraphs
(EduKGs) is crucial for modeling domain knowledge in digital learning
environments, particularly in Massive Open Online Courses (MOOCs).
However, identifying the most effective approach for constructing accu-
rate EduKGs remains a challenge. This study compares Top-down and
Bottom-up approaches for automatic EduKG construction, evaluating
theireffectivenessincapturingandstructuringknowledgeconceptsfrom
learning materials in our MOOC platform CourseMapper. Through a
userstudyandexpertvalidationusingSimpleRandomSampling(SRS),
resultsindicatethattheBottom-upapproachoutperformstheTop-down
approachinaccuratelyidentifyingandmappingkeyknowledgeconcepts.
TofurtherenhanceEduKGaccuracy,weintegrateaHuman-in-the-Loop
approach, allowing course moderators to review and refine the EduKG
beforepublication.Thisstructuredcomparisonprovidesascalableframe-
workforimprovingknowledgerepresentationinMOOCs,ultimatelysup-
porting more personalized and adaptive learning experiences.
Keywords: Massive Open Online Courses · Educational Knowledge
Graphs · Top-down vs. Bottom-up Approaches · Human-in-the-Loop
1 Introduction
The rapid growth of online education has led to the widespread adoption of
Massive Open Online Courses (MOOCs), offering learners open access to high-
qualityeducationatscaleandfosteringlifelonglearningopportunities[10][1].As
MOOCscontinuetoevolve,ArtificialIntelligence(AI)isplayingatransformative
roleinenhancingtheireffectiveness.AmongthevariousAI-driveninnovationsin
education, Knowledge Graphs (KGs) have emerged as a powerful tool for struc-
turing and organizing knowledge, and enabling personalized and interconnected
learning experiences. Their application in education, referred to as Educational
Knowledge Graphs (EduKGs), is revolutionizing how knowledge is organized,
represented, and applied, ultimately enriching the learning experiences [1].
EduKGsareincreasinglybeingintegratedintoMOOCsforvariouspurposes,
e.g.optimizinglearningresourceutilization[6],predictinglearningbehavior[19],
5202
yaM
51
]YC.sc[
1v96001.5052:viXra

2 Ain et al.
recommendingknowledgeconceptsandcourses[10][12],andmanymore.Despite
their benefits, constructing accurate EduKGs remains a significant challenge.
Traditional methods depend on domain experts, making EduKGs construction
time-consuming and resource-intensive [2]. Moreover, the increasing volume of
educational data has driven the need for automated EduKG construction, yet
existing approaches often struggle with accuracy and performance [13][2]. Re-
centadvancementsinLargeLanguageModels(LLMs)havedrivenresearchinto
enhancing EduKG generation with LLM-based approaches as well [9]. However,
there is currently no standard approach for constructing EduKGs in MOOCs,
particularly in terms of evaluating different methodologies such as Top-down
and Bottom-up. Identifying the most effective strategy is crucial, as the accu-
racy of EduKGs directly impacts their usefulness in MOOCs. Moreover, given
that MOOCs consist of multiple materials structured into pages, it is essential
to explore whether EduKGs should be constructed holistically from entire ma-
terials or incrementally page-by-page. To address this gap, in this paper, we
experiment with two pipelines of automatic EduKG construction, namely Top-
downandBottom-upapproachesinourMOOCplatformCourseMapper[3].Our
findings indicate that the Bottom-up approach achieves the highest accuracy,
demonstrating its effectiveness in constructing reliable EduKGs for MOOCs.
Additionally, acknowledging the importance of human involvement in EduKG
construction, we integrate a Human-in-the-Loop approach in our pipeline, en-
abling course experts to review and refine the automatically generated EduKGs
before publication. This balances automation with human expertise, ensuring
quality while minimizing manual effort.
2 CourseMapper
Our MOOC platform CourseMapper consists of a range of unique features de-
signed to enhance the online learning experience by addressing various learner
needs. These features set our platform apart from existing MOOC platforms
by offering innovative functionalities that improve interaction and communica-
tion in online learning, foster learner engagement, enhance personalization, and
support learning analytics (see Figure 1).
Learning Channels: EachcourseinCourseMapperincludesmultiplelearning
channels,whichserveascollaborativespaceswithintheMOOCplatform.These
learning channels (Figure 1a, L1) are created for each course topic (Figure 1a,
L2), enabling learners to engage with PDF and video learning materials (Figure
1a,L3),discussconceptswithpeersandinstructors,andsharerelevantresources
within the designated space. The concept of learning channels provides a more
organizedandinteractivewaytostructurecourses,fosteringdeeperengagement
and knowledge sharing among learners.
Collaboration and Communication: Learners can collaborate on PDF and
video learning materials using three different annotation tools (i.e., highlight,

|        | Top-Down           | vs. Bottom-Up EduKG   | Construction |               | in CourseMapper    | 3   |
| ------ | ------------------ | --------------------- | ------------ | ------------- | ------------------ | --- |
|        | (a) Learning       | Channels              | (b)          | Collaboration | and Communication  |     |
|        | (c) Awareness      |                       |              | (d) Learner   | Modeling           |     |
|        | (e) Recommendation |                       |              | (f) Learning  | Analytics          |     |
| Fig.1: | An overview        | of UI of CourseMapper |              | demonstrating | different features |     |
draw,pinpoint)(Figure1b,C1)tomarkspecificpartsofalearningmaterialand
add a note, question, or external resource link, referred to as annotation types
(Figure1b,C2).Additionally,thementionfeature(using@)(Figure1b,C3),al-
lowslearnerstotagothersbyname,enablingdirectinteraction.Allannotations
appear in the discussion panel (Figure 1b, C4) alongside the learning material,
where learners can view, respond to, or like/dislike them. Using shared annota-
tions, learners can engage in deeper discussions on learning materials, enhance
| collaboration, | and | improve communication | with | both peers | and instructors. |     |
| -------------- | --- | --------------------- | ---- | ---------- | ---------------- | --- |
Awareness: CourseMapper includes a notification system to enhance aware-
ness of course activities among course participants. Learner’s activities (e.g.,
annotations,repliesetc.)areloggedasxAPIstatementsandthenusedtogener-
ate relevant notifications. Based on their personalized settings, learners receive
tailored notifications in their newsfeed (Figure 1c, A1), categorized into course

4 Ain et al.
updates, replies and mentions, and annotations. In addition to notifications, an
orange dot indicator (Figure 1c, A2) serves as a visual cue, highlighting the
respective course, topic, learning channel, and/or learning material whenever a
new activity occurs. This feature helps learners stay informed and engaged by
drawing their attention to recent course updates.
Educational Knowledge Graphs: InCourseMapper,EducationalKnowledge
Graphs (EduKGs) provide learners a structured overview of key concepts and
their relationships. EduKGs are built at three levels: Slide-EduKG (concepts
withinaslide)(Figure1b,E1),LM-EduKG(conceptsacrossalearningmaterial)
(Figure1b,E2),andCourse-EduKG(conceptsthroughoutacourse)(Figure1b,
E3). Stored in a Neo4j graph database, nodes represent concepts, categories,
slides, and learning materials, connected by edges representing the relationships
between them. EduKGs construction details are disucssed in Section 4.
Learner Modeling: Learnermodelingplaysacrucialroleinenhancingperson-
alization, engagement, and learning effectiveness in MOOCs. In CourseMapper,
each PDF learning material includes a "Did Not Understand (DNU)" button
at the bottom (Figure 1b, E1). When clicked, learners are presented with the
Slide-EduKG containing the top five main concepts extracted from the content
ofthecurrentpage(Figure1d,LM1).Theycanthenmarktheconceptstheydo
not understand (DNU) (Figure 1d, LM2), allowing them to explicitly communi-
cate their knowledge state to the system rather than having the system infer it
implicitlybasedontheirbehavioraldata.TheseDNUconceptsarelinkedtothe
learner to formulate their Personal Knowledge Graph (PKG), creating a struc-
tured representation of the learner. This PKG-based learner model is further
leveraged to provide personalized recommendations.
Recommendation: PKG-based learner models are further used to generate
personalized recommendations of related knowledge concepts (Figure 1e, R1),
using Graph Convolutional Networks (GCNs) and pre-trained transformer lan-
guage model encoders. To increase transparency, explanations of the recom-
mended concepts are provided using the structural and semantic information in
the EduKG [5]. Moreover, the learners are provided personalized recommenda-
tions of external learning resources (Figure 1e, R2) including YouTube videos
andWikipediaarticles[4],usingbothPKG-basedandcontent-basedrecommen-
dation algorithms.
Learning Analytics: In CourseMapper, learners’ activity data collected as
xAPI statements, is used to analyze user engagement patterns and generate
meaningful learning insights through an external open Learning Analytics (LA)
platform, OpenLAP [11]. OpenLAP supports self-service LA by empowering
end-users to take control of the LA indicator design process, through intuitive
user interfaces. Using OpenLAP, various LA indicators are generated from the
xAPI data (Figure 1f, LA1) and visually represented in dashboards at different

Top-Down vs. Bottom-Up EduKG Construction in CourseMapper 5
levels (Figure 1f, LA2-3-4) within CourseMapper through iframes. These ana-
lyticsenablelearnersandeducatorstotrackprogress,identifylearningpatterns,
and make informed decisions to improve the learning experience.
3 EduKG Construction Phases
EduKG construction is a multi-phase process involving several key steps de-
scribed below.
Text Extraction: This phase extracts text from PDF learning materials while
preservingdocumentstructure.Standardextractionmethodsoftenoverlooklay-
out variations, so we use a simplified layout-aware approach. It involves: (1)
identifying contiguous text blocks, (2) categorizing them using rules, and (3)
merging them in sequence. We used PDFMiner [18] that retrieves character po-
sitions,groupingthemintostructuredtextblocksbasedoncoordinateproximity.
Keyphrase Extraction: After extracting text, we apply keyphrase extraction
as a pre-step for entity linking to Wikipedia. This approach improves efficiency
by reducing the volume of text sent to the entity-linking service. For keyphrase
extraction algorithm, we used SIFRank [2] chosen based on its
SqueezeBERT
accuracy and performance results [2].
Concept Identification: Extracted keyphrases are mapped to relevant con-
cepts from external knowledge base DBpedia. Following [13], we use DBpedia
Spotlight [16] to link keyphrases to DBpedia concepts through spotting, candi-
dateselection,anddisambiguation,withthesupportvaluesetto5andtheconfi-
dencethresholdto0.35[8].However,entity-linkingtoolslikeDBpediaSpotlight
can produce incorrect annotations due to automatic processing without manual
verification. To mitigate this, we apply a weighting strategy to assess semantic
similarity between identified concepts and learning materials, described later.
Concept Expansion: To improve EduKG coverage, diversity, and knowledge
exploration,weexpandidentifiedconcepts,askeyphraseextractionandconcept
identification may miss some relevant concepts [15]. This expansion follows two
approaches:relatedconceptexpansion,whichenrichesEduKGwithsemantically
related DBpedia concepts (e.g., linking “Natural language processing” to “Nat-
ural language understanding” via dbo:wikiPageWikiLink), and category-based
expansion, which associates concepts with their DBpedia categories (e.g., link-
ing “Natural language processing” to “Category:Computational linguistics” via
dct:subject)usingSPARQLqueries,providinghierarchicalcontextandfacilitate
broader concept discovery.
Concept Weighting: While concept expansion enriches the EduKG, it may
introduce noise by adding irrelevant concepts [14]. To address this, we apply a
concept-weighting strategy that prioritizes contextually and semantically rele-
vant concepts while minimizing noise. Building upon the strategy by Manrique

6 Ain et al.
etal.[13],weproposeatransformer-basedweightingapproachusingSBERT[17]
forembeddinggeneration.Ourapproach(w )assignsweightsbasedonco-
SBERT
sine similarity between embeddings of learning material content and Wikipedia
article text of the concept, retrieved via the Wikipedia API. The same method
is used for related concepts, while Wikipedia categories lacking descriptive text
are weighted based on similarity between the learning material content embed-
dingandthecategorynameembedding.Thisensuresonlythemostcontextually
relevant concepts, related concepts, and categories are included in the EduKG.
4 EduKG Construction Pipelines
We propose and experiment with two pipelines for EduKG construction in
MOOCs, namely Top-down and Bottom-up, discussed below.
4.1 Top-down EduKG Construction
The Top-down approach (Figure ??a) starts by extracting text from the entire
PDFlearningmaterial,whichispassedtothekeyphraseextractionmodule.The
keyphrase extractor identifies n keyphrases from the learning material, where
n=15*thenumberofslidesinthematerial,asthisformulaprovedtocoverallthe
possible keyphrases based on experiment. These keyphrases are annotated with
DBpediaSpotlighttoidentifyMainConcepts(MCs),whicharethenweightedby
computing the cosine similarity between the MC’s Wikipedia article embedding
andthelearningmaterial’stextembedding.RelationshipsbetweentheMCsand
the learning material are stored in a Neo4j database. This method generates a
single EduKG for the entire learning material (LM-EduKG). To provide more
granular views, the approach is extended to generate EduKGs for individual
slides (Slide-EduKG). Text is extracted from each slide, keyphrases are iden-
tified, and the corresponding MCs are checked against the LM-EduKG. If the
conceptalreadyexists,itisweighted,andrelationshipsarecreated;otherwise,it
is discarded. After covering all slides, concept expansion is applied on the whole
EduKG to include related concepts and categories from Wikipedia.
4.2 Bottom-up EduKG Construction
The Bottom-up approach (Figure ??b) constructs the EduKG starting from
eachslide/PDFpageofthelearningmaterial,withthetextextractedfromeach
slide as the initial reference. From each slide, 15 keyphrases are extracted, as
morethan95%ofslidescontainfewerthan15keyphrases.Thesekeyphrasesare
linked to MCs via DBpedia Spotlight, and each concept’s weight is calculated
based on the cosine similarity between the SBERT embedding of the concept’s
Wikipedia abstract and the SBERT embedding of the learning material text
(w ). Additionally, a slide similarity score (w ) is calculated based on the
LM Slide
cosine similarity between the SBERT embedding of the concept’s Wikipedia
abstractandtheSBERTembeddingoftheslidetext.Thefinalimportanceofthe

Top-Down vs. Bottom-Up EduKG Construction in CourseMapper 7
concept per slide is determined by the sum of the slide similarity score (w )
Slide
and the concept weight (w ). Relations are established between the MCs and
LM
boththeslideandthelearningmaterial.Afterannotatingeachslide,thedatais
stored in the Neo4j database for immediate access, allowing users to explore the
Slide-EduKGevenbeforetheentireLM-EduKGiscompleted.Thisensuresthat
users can access partial results while the construction continues. Once all slides
are annotated, concept expansion is performed. Lastly, the EduKGs for each
slide are aggregated into a comprehensive LM-EduKG. This approach ensures
that concepts related to a slide are accurately represented, and any concepts at
the slide level are carried over to the learning material level.
5 Evaluation
For the evaluation, using our MOOC platform CourseMapper, we conducted an
onlineuserstudyfollowedbyahumanannotationstudytoassesswhichpipeline
produces the most accurate and performant EduKG.
5.1 Evaluation of EduKG Performance
Toevaluate theperformanceof Top-downvs.Bottom-uppipelines, auserstudy
wasconductedwith19participants(11M,8F)fromthreedifferentcoursestaught
inourchair.Invitationsweresentto47individuals,with19respondingtoevalu-
ate34learningmaterialsintotal.EduKGswereconstructedfordifferentlearning
materials using both the Top-down and Bottom-up pipelines in CourseMapper.
The evaluation involved assessing Precision(P), Mean Reciprocal Rank (MRR),
andMeanAveragePrecision(MAP)fortop-kresultsbasedonparticipants’feed-
back. Participants were introduced to the platform, the research goals, and the
evaluationtask.Theyrandomlyselectedalearningmaterialthattheyweremost
familiar with, and the corresponding EduKG (consisting of Top-15 MCs) was
shown to them. Afterwards, they completed a questionnaire for each Top-down
and Bottom-up EduKG. The questionnaire included questions on: 1) Familiar-
ity with the topic (1: Not familiar, 5: Expert), 2) Relevance of concepts to the
material (1 to 15 concepts), 3) Expected concepts not included in the list, and
4)Rankingtheconceptsfrommosttoleastrelevant.Inaddition,usersprovided
feedback on whether the EduKG covered important content, helped them form
an understanding of the material, and overall satisfaction with the results. The
results (Table 1) showed similar performance between both models. However,
the bottom-up approach showed slightly better precision at higher k-values and
MAP, suggesting that it retrieved more effective information. A T-test revealed
no significant differences between the models. In terms of user experience, the
bottom-up EduKG was rated more favorably by the participants.
5.2 Evaluation of EduKG Accuracy
To assess the accuracy of EduKGs generated using the Top-down and Bottom-
up approaches, we employed the Simple Random Sampling (SRS) method by

8 Ain et al.
Table 1: Results of the evaluation of Top-down vs. Bottom-up approaches
Pipeline User study SRS evaluation
P@15 MRR MAP Mean Value µ Normal Approximation Value µ ±σ
s s
Top-down 0.807 0.941 0.807 0.38 0.38 ± 0.048
Bottom-up0.812 0.941 0.812 0.40 0.4 ± 0.049
Gao et al. [7]. This method evaluates the correctness of knowledge graph (KG)
triples (subject, predicate, object) through two key tasks: entity identification
(verifying node meanings using contextual information) and relationship valida-
tion (ensuring correct links between nodes). In this way, accuracy is calculated
asthemeanofsamplejudgments.Ifthemarginoferror(MoE)exceedsaprede-
finedthreshold,additionalsamplesareevaluateduntilaccuracystabilizes.There
are several matrices involved in the calculation of accuracy. The mean accuracy
(µ ) of a sample set with (n ) samples in SRS is computed as:
s s
µ = 1 (cid:80)ns f(t )
s ns i=1 i
wheref(t )is1foraccuratesamplesand0otherwise.Thenormalapproximation
i
estimates the accuracy range:
(cid:113)
µ ±z µs(1−µs)
s α/2 ns
wherez dependsontheconfidenceinterval.Themarginoferror(MoE)quan-
α/2
tifies estimation precision and helps to determine the potential amount of error
that could occur when using a sample instead of the entire population:
(cid:113)
MoE =z σ2
α/2 ns
The evaluation took 4 hours, with two annotators reviewing different random
samples.Thesampleswereoftypee.g.(Slide,contains,MC),and(LM,contains,
MC). The first annotator evaluated 200 samples per model, while the second
evaluated 183 Top-down and 180 Bottom-up samples. Evaluation stopped when
all criteria were met. Results (Table 1) showed that the Bottom-up approach
more accurately identified key concepts and their associations with the learning
materials and the slides. However, a T-test found no statistically significant
difference. Overall, across all evaluations, the Bottom-up pipeline emerged as
the most effective and accurate method for EduKG construction in MOOCs.
6 EduKG Construction with Human-in-the-Loop
Our evaluation revealed that while the Bottom-up approach produced more ac-
curateEduKGs,theoverallaccuracywasstillrelativelylow.Toaddressthis,we
integrateaHuman-in-the-Loopapproachinourpipeline,allowingcoursecreators
to review and refine the EduKG before publication. Once the main concepts in
thelearningmaterialareextracted,instructorscanpreviewthem(Figure2,H1),

|     | Top-Down |     | vs. Bottom-Up |     | EduKG | Construction | in  | CourseMapper | 9   |
| --- | -------- | --- | ------------- | --- | ----- | ------------ | --- | ------------ | --- |
editorremoveirrelevantconcepts(Figure2,H2),andaddmissingconcepts(Fig-
ure2,H3)andlinkthemtotherelevantslide(s)ofthelearningmaterial(Figure
2, H4). After finalizing the edits (Figure 2, H5), the concept expansion step is
appliedandtheverifiedEduKGispublishedandpresentedtolearners.Thispro-
cess guarantees accurate EduKGs while striking a balance between automation
andhumanexpertise.Moreover,itensuresthatlearnersreceiveanaccurateand
instructor-approved EduKG, minimizing the risk of disseminating incorrect or
| incomplete |        | information. |                 |     |     |             |      |           |     |
| ---------- | ------ | ------------ | --------------- | --- | --- | ----------- | ---- | --------- | --- |
|            | Fig.2: | UI           | of CourseMapper |     | to  | Preview and | Edit | the EduKG |     |
7 Conclusion
In this paper, we explored Top-down vs. Bottom-up approaches for the auto-
matic construction of Educational Knowledge Graphs (EduKGs) in the MOOC
platform CourseMapper. We evaluated both approaches and found the Bottom-
upapproachtobemoreaccurateandeffectiveforEduKGconstructionatvarious
levels. To further improve EduKG accuracy, we proposed a human-in-the-loop
| approach, | allowing |     | expert | refinement | while | maintaining | efficiency. |     |     |
| --------- | -------- | --- | ------ | ---------- | ----- | ----------- | ----------- | --- | --- |
Disclosure of Interests. The authors have no competing interests to declare that
| are relevant |     | to the | content of | this article. |     |     |     |     |     |
| ------------ | --- | ------ | ---------- | ------------- | --- | --- | --- | --- | --- |
References
1. Abu-Salih, B., Alotaibi, S.: A systematic literature review of knowledge graph
| construction |     | and | application | in  | education. | Heliyon | (2024) |     |     |
| ------------ | --- | --- | ----------- | --- | ---------- | ------- | ------ | --- | --- |
2. Ain, Q.U., Chatti, M.A., Bakar, K.G.C., Joarder, S., Alatrash, R.: Automatic
constructionofeducationalknowledgegraphs:Awordembedding-basedapproach.
| Information |     | 14(10) | (2023) |     |     |     |     |     |     |
| ----------- | --- | ------ | ------ | --- | --- | --- | --- | --- | --- |
3. Ain, Q.U., Chatti, M.A., Joarder, S., Nassif, I., Wobiwo Teda, B.S., Guesmi,
| M., | Alatrash, | R.: | Learning | channels | to  | support interaction |     | and collaboration | in  |
| --- | --------- | --- | -------- | -------- | --- | ------------------- | --- | ----------------- | --- |
coursemapper.In:Proceedingsofthe14thInternationalConferenceonEducation
| Technology |     | and | Computers. | pp. | 252–260 | (2022) |     |     |     |
| ---------- | --- | --- | ---------- | --- | ------- | ------ | --- | --- | --- |

10 Ain et al.
4. Ain, Q.U., Chatti, M.A., Meteng Kamdem, P.A., Alatrash, R., Joarder, S., Siep-
mann,C.:Learnermodelingandrecommendationoflearningresourcesusingper-
sonalknowledgegraphs.In:Proceedingsofthe14thLearningAnalyticsandKnowl-
edge Conference. p. 273–283. LAK ’24 (2024)
5. Alatrash, R., Chatti, M.A., Ain, Q.U., Fang, Y., Joarder, S., Siepmann, C.: Con-
ceptgcn:Knowledgeconceptrecommendationinmoocsbasedonknowledgegraph
convolutionalnetworksandsbert.ComputersandEducation:ArtificialIntelligence
6, 100193 (2024)
6. Dang, F., Tang, J., Li, S.: Mooc-kg: a mooc knowledge graph for cross-platform
online learning resources. In: IEEE 9th International Conference on Electronics
Information and Emergency Communication (ICEIEC). IEEE (2019)
7. Gao, J., Li, X., Xu, Y.E., Sisman, B., Dong, X.L., Yang, J.: Efficient knowledge
graph accuracy evaluation. arXiv preprint arXiv:1907.09657 (2019)
8. Grévisse, C., Manrique, R., Mariño, O., Rothkugel, S.: Knowledge graph-based
teachersupportforlearningmaterialauthoring.In:ColombianConferenceonCom-
puting. pp. 177–191. Springer (2018)
9. Jhajj, G., Zhang, X., Gustafson, J.R., Lin, F., Lin, M.P.C.: Educational knowl-
edge graph creation and augmentation via llms. In: International Conference on
Intelligent Tutoring Systems. pp. 292–304. Springer (2024)
10. Jiang, L., Liu, K., Wang, Y., Wang, D., Wang, P., Fu, Y., Yin, M.: Reinforced
explainableknowledgeconceptrecommendationinmoocs.ACMTrans.Intell.Syst.
Technol. 14(3) (Apr 2023)
11. Joarder, S., Chatti, M.A., Sun, A.: A no-code environment for implementing
human-centered learning analytics indicators. In: Companion Proceedings of the
14th International Learning Analytics and Knowledge Conference (2024)
12. Liu, T., Chen, Y., Chang, L., Zhu, C.: Knowledge graph-assisted collaborative fil-
tering for course recommendation in Mooc. In: International Conference on Elec-
tronic Information Engineering and Data Processing (2023)
13. Manrique, R., Grévisse, C., Mariño, O., Rothkugel, S.: Knowledge graph-based
core concept identification in learning resources. In: Joint International Semantic
Technology Conference. pp. 36–51. Springer (2018)
14. Manrique, R., Herazo, O., Mariño, O.: Exploring the use of linked open data for
user research interest modeling. In: Colombian Conference on Computing (2017)
15. Manrique,R.,Marino,O.:Knowledgegraph-basedweightingstrategiesforaschol-
arly paper recommendation scenario. In: KaRS@ RecSys. pp. 5–8 (2018)
16. Mendes, P.N., Jakob, M., García-Silva, A., Bizer, C.: Dbpedia spotlight: shedding
lightonthewebofdocuments.In:Proceedingsofthe7thinternationalconference
on semantic systems. pp. 1–8 (2011)
17. Reimers,N.,Gurevych,I.:Sentence-bert:Sentenceembeddingsusingsiamesebert-
networks. arXiv preprint arXiv:1908.10084 (2019)
18. Shinyama, Y.: Pdfminer-python pdf parser. GitHub https://github.
com/pdfminer/pdfminer. six (2007)
19. Xia, X., Qi, W.: Learning behaviour prediction and multi-task recommendation
basedonaknowledgegraphinmoocs.Technology,PedagogyandEducation(2025)