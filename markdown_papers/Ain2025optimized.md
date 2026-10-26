---
title: "Ain2025optimized"
source: "Ain2025optimized.pdf"
source_sha256: "a626bcb1d6aa009305da63ceb595ccb6126bcabe2f2101aad2b99979f2bb2d10"
converted_at: "2026-10-26T07:04:53.789022+00:00"
markitdown_version: "0.1.9"
---
An Optimized Pipeline for Automatic
Educational Knowledge Graph Construction
Qurat Ul Ain1⋆[0000−0003−2691−0267], Mohamed Amine
Chatti1[0000−0002−1311−7852], Jean Qussa1[0009−0003−3006−1111], Amr
Shakhshir1[0009−0005−4278−9681], Rawaa Alatrash1[0000−0003−2192−028X], and
Shoeb Joarder1[0000−0003−4591−9742]
Social Computing Group, Faculty of Computer Science, University of
Duisburg-Essen, Germany
Abstract. TheautomaticconstructionofEducationalKnowledgeGraphs
(EduKGs) is essential for domain knowledge modeling by extracting
meaningful representations from learning materials. Despite growing in-
terest,identifyingascalableandreliableapproachforautomaticEduKG
generation remains a challenge. In an attempt to develop a unified and
robustpipelineforautomaticEduKGconstruction,inthisstudywepro-
pose a pipeline for automatic EduKG construction from PDF learning
materials. The process begins with generating slide-level EduKGs from
individual pages/slides, which are then merged to form a comprehen-
sive EduKG representing the entire learning material. We evaluate the
accuracy of the EduKG generated from the proposed pipeline in our
MOOC platform, CourseMapper. The observed accuracy, while indica-
tive of partial success, is relatively low particularly in the educational
context, where the reliability of knowledge representations is critical
for supporting meaningful learning. To address this, we introduce tar-
getedoptimizationsacrossmultiplepipelinecomponents.Theoptimized
pipelineachievesa17.5%improvementinaccuracyandatenfoldincrease
inprocessingefficiency.Ourapproachoffersaholistic,scalableandend-
to-endpipelineforautomaticEduKGconstruction,adaptabletodiverse
educationalcontexts,andsupportsimprovedsemanticrepresentationof
learning content.
Keywords: Educational Knowledge Graphs · Knowledge Modeling ·
LLM-based Keyphrase Extraction · Natural Language Processing
1 Introduction
Knowledge graphs (KGs) have gained significant attention in recent years due
to their ability to structure and integrate diverse information across various do-
mains [14]. Educational knowledge graphs (EduKGs) refer to the application of
KGs in the educational domain, structuring knowledge concepts and their rela-
tionshipstosupportpersonalizedlearningandadaptiveeducation[1].Theyplay
⋆ Email: qurat.ain@stud.uni-due.de
5202
peS
5
]YC.sc[
1v29350.9052:viXra

a crucial role in technology-enhanced learning (TEL) systems such as massive
openonlinecourses(MOOCs)andlearningmanagementsystems(LMSs)byex-
tracting and visualizing key learning concepts [20]. Structurally, an EduKG is
a heterogeneous graph where nodes represent educational entities (e.g., knowl-
edge concepts, learning materials) and edges define various types of semantic
relationships between them [20]. EduKGs serve a wide range of purposes in the
educational domain, including enhancing learning and scientific discovery [9],
educationalassessment[11],trainingKGpractitioners[10],learnermodeling[5],
personalized learning resource recommendation [3], and so on.
With the exponential growth of digital learning content, there is an increas-
ing need for automated and scalable methods to organize and interpret do-
mainknowledgeeffectively.EduKGsofferarobustframeworkformodelingsuch
knowledge, yet the automatic construction of high-quality EduKGs remains a
significant challenge. Traditionally, EduKGs were constructed manually by do-
main experts. However, due to the time and effort required for this approach,
recent research has shifted towards automating EduKG generation using ma-
chine learning (ML) and natural language processing (NLP) techniques [28]. In
parallel, the emergence of Generative AI and Large Language Models (LLMs)
has sparked interest in their potential for EduKG generation [16,29]. Despite
theirpromise,LLMsfacesignificantchallengesinautomaticEduKGgeneration,
such as token limits that restrict processing large datasets, inefficient human-
machine interaction that either lacks oversight or increases labor costs, and a
tendency to generate inaccurate information due to their hallucinating nature.
TheselimitationsmakeLLMsunreliableforfullyautonomousEduKGconstruc-
tion [29]. Despite growing research interest in automatic EduKG construction,
there remains a pressing need for a holistic, reliable, and scalable end-to-end
pipeline that can automatically generate high-quality EduKGs across diverse
educational settings. Existing efforts such as EduKG for K-12 [27] are ontology-
driven, requiring a predefined schema before extraction rather than fully auto-
maticextractionfromunstructuredPDFs.Aspartofourongoingresearchefforts
to address this challenge [1,4], this study focuses on refining and optimizing the
automaticEduKGconstructionprocesstodevelopaunifiedandrobustsolution.
We first propose a pipeline for automatic EduKG construction that can process
any PDF-based learning material, starting from a single page/slide of a PDF,
leading to a slide-EduKG per slide which are then combined to form an EduKG
to represent the whole learning material. We then evaluate the accuracy of the
EduKGgeneratedbytheproposedpipelineinourMOOCplatform,CourseMap-
per[2].TheaccuracyoftheEduKGwasnotveryhighwhichcallsforaneedfor
further improvements in the pipeline. Subsequently, we introduce a series of op-
timizations,includingenhancementstothepipelinearchitecture,improveddata
preprocessing, and refined modules for text extraction, concept annotation and
EduKG expansion. The optimized pipeline is then compared against its initial
version in terms of accuracy and efficiency, achieving a 17.5% improvement in
accuracy and a tenfold increase in processing efficiency. All experiments were
conducted within CourseMapper, to demonstrate the pipeline’s applicability in

real-worldeducationalenvironments.Theresultingpipelineoffersastate-of-the-
art,domain-independentsolutionforautomaticEduKGconstructionandcanbe
easily adapted to a wide range of educational contexts.
2 EduKG Construction Pipeline
The EduKG construction pipeline consists of several steps, as described below.
2.1 Text Extraction
ThefirststepinbuildingEduKGinvolvesextractingtextfromindividualpages/
slidesofPDFlearningmaterials.Thisstepisparticularlychallengingduetothe
diverse and often inconsistent layouts and structures of educational PDFs. To
ensurecoherentinputforthesubsequentkeyphraseextractionstep,itisessential
to accurately identify and reconstruct logically connected text segments in the
correct reading order. We address this using PDFMiner [21] which applies a
layout-awarestrategybydetectingtextblocks,applyingrule-basedclassification,
and merging them to preserve the intended textual sequence.
2.2 Keyphrase Extraction
Oncetextisextractedfromapage/slideofthePDFlearningmaterial,keyphrase
extraction is performed as a preliminary step to Wikipedia entity linking, op-
timizing the process by minimizing the amount of text processed by the entity
linking service. To determine the most effective keyphrase extraction method,
we evaluate both state-of-the-art Large Language Model (LLM) approaches in-
cluding Zero-Shot, Few-Shot, and KeyBERT-assisted prompts, and traditional
techniques, including SingleRank, PatternRank, and SIFRank variants. The In-
spec [15] and SemEval [6] datasets serve as benchmarks for performance evalua-
tion,astheycontainscholarlytextsrelevanttotheeducationaldomain,making
them suitable for this evaluation. Our experiments apply the LLM-based meth-
odsusingtheMistral-7B-Instruct-v0.1model[25],whilethetraditionalmethods
are implemented following their respective original configurations. Mistral-7B,
an open-source instruction-tuned LLM with 7 billion parameters, is well-suited
forthistaskduetoitsstronglanguageunderstanding,abilitytofollowprompts,
and scalability for large datasets. In the Zero-Shot setting, the LLM extracts
keyphrases based solely on its pre-trained knowledge, using prompts such as
“Identify key phrases from the following text: [Document Text]”. The Few-Shot
setting improves performance by including a few example text–keyphrase pairs
in the prompt. The LLM-KeyBERT approach combines LLM prompting with
KeyBERT [13], which uses BERT embeddings to extract contextually relevant
keywords,enhancedbytheLLM’snuancedunderstandingoftheinput.Allmeth-
ods are evaluated by comparing the top-n extracted keyphrases against expert
annotationsintheInspecandSemEvaldatasets.Effectivenessismeasuredusing
Precision,Recall,andF1-score,capturingeachmethod’saccuracy,coverage,and

balance. The results are presented in Table 1. This comparative analysis shows
that LLM-based approaches, particularly with Few-Shot learning, outperform
othersinkeyphraseextraction.ThishighlightsthesignificanceofLLMs’nuanced
understandingandadaptabilityincapturingsemanticallyrichkeyphrases.While
traditional methods lag behind in performance, they still hold significant value,
especially in contexts where access to advanced models is limited. It is worth
noting that the reported results for LLM-based methods reflect their best-case
performance; in practice, some runs show a 10–15% drop in effectiveness, em-
phasizing the need for careful validation when deploying these models. Another
| Table        | 1. A comparison   | of different keyphrase         |         | extraction | methods     |
| ------------ | ----------------- | ------------------------------ | ------- | ---------- | ----------- |
| K Keyphrase  | Extraction Method | Inspec                         | Dataset | SemEval    | Dataset     |
|              |                   | P                              | R F1    | P          | R F1        |
| Zero-shot    | LLM               | 72.95 75.17                    | 74.04   | 72.95      | 75.17 73.2  |
| Few-shot     | LLM               | 74.2876.1475.2074.2876.1476.33 |         |            |             |
| LLM_KeyBERT  |                   | 71.51 73.81                    | 72.64   | 71.51      | 73.81 72.12 |
| 5 SingleRank |                   | 64.78 67.04                    | 67.86   | 64.75      | 67.04 67.15 |
| PatternRank  |                   | 60.83 62.98                    | 61.89   | 60.83      | 62.98 61.45 |
| SIFRank      |                   | 65.21 67.49                    | 66.33   | 65.21      | 67.49 68.11 |
| SIFRank      |                   | 66.75 67.04                    | 65.89   | 66.75      | 69.01 66.24 |
SqueezeBERT
| Zero-shot    | LLM         | 69.14 84.98 | 76.25                | 69.14 | 84.98 75.6  |
| ------------ | ----------- | ----------- | -------------------- | ----- | ----------- |
| Few-shot     | LLM         | 84.57       |                      |       |             |
|              |             | 72.04       | 77.8172.0484.5778.18 |       |             |
| LLM_KeyBERT  |             | 66.79 83.00 | 74.02                | 66.79 | 83.00 74.31 |
| 10SingleRank |             | 66.11 81.19 | 73.09                | 66.11 | 81.19 73.23 |
| PatternRank  |             | 64.11 79.02 | 70.79                | 64.11 | 79.02 70.91 |
| SIFRank      |             | 62.74 77.06 | 69.16                | 62.74 | 77.06 69.23 |
|              |             | 66.34 81.37 | 72.87                | 66.34 | 81.37 73.86 |
| SIFRank      | SqueezeBERT |             |                      |       |             |
| Zero-shot    | LLM         | 59.16 89.08 | 71.10                | 59.16 | 89.08 71.2  |
| Few-shot     | LLM         | 66.61 88.15 | 75.8866.61           |       | 88.15 75.68 |
| LLM_KeyBERT  |             | 55.65 87.27 | 67.96                | 55.65 | 87.27 68.16 |
| 15SingleRank |             | 57.12 87.02 | 69.01                | 57.12 | 87.00 69.12 |
| PatternRank  |             | 55.86 85.98 | 67.72                | 55.86 | 85.98 68.09 |
| SIFRank      |             | 54.49 83.05 | 65.81                | 54.49 | 83.05 66.21 |
| SIFRank      |             | 57.17 87.00 | 68.96                | 57.17 | 87.00 69.33 |
SqueezeBERT
importantdimensionofourevaluationisruntimeefficiency.LLM-basedmethods,
althoughaccurate,demandsignificantlymoretimeandcomputationalresources
perdocumentthantraditionalmethods(seeTable2).Despitelackingthedepth
of LLM-based analysis, traditional approaches offer dependable and efficient so-
lutions, particularly when computational constraints or real-time processing are
priorities. Among these, SIFRank demonstrates a strong balance
SqueezeBERT
between accuracy and efficiency, making it a practical choice for keyphrase ex-
tractioninourpipeline.Thekeyphraseextractorextractsn=15keyphrasesfrom
each slide of the PDF material, because in a learning environment it would be
overwhelmingforthelearnerstofocusonmorethan15conceptswithinaslide.

| Table 2. Runtime | required to       | extract (N=5) | keyphrases per document |
| ---------------- | ----------------- | ------------- | ----------------------- |
| Keyphrase        | extraction        | methodRuntime | (min:sec)               |
|                  | LLM-based methods |               | 1:40                    |
|                  | SingleRank        |               | <0:01                   |
|                  | PatternRank       |               | <0:01                   |
|                  | SIFRank           |               | 0:03                    |
|                  | SIFRank           |               | 0:24                    |
SqueezeBERT
| 2.3 Concept Identification |     |     |     |
| -------------------------- | --- | --- | --- |
The extracted keyphrases are used for concept identification by linking them to
external knowledge bases. Following [17], we use DBpedia Spotlight [19] to map
keyphrases to DBpedia concepts through spotting, candidate selection, and dis-
ambiguation based on their contextual information. The annotated keyphrases
are then referred to as Main Concepts (MCs) of the slide. Nevertheless, entity-
linking tools like DBpedia Spotlight can occasionally produce incorrect annota-
tions where keyphrases are linked to irrelevant concepts, due to its fully auto-
matednature[17].Toaddressthisissue,weimplementaconcept-weightingstrat-
egy that emphasizes semantic and contextual relevance. We use a transformer-
based method (w ), where weights of the MCs (w ) are computed via
| SBERT |     |     | LM  |
| ----- | --- | --- | --- |
cosinesimilaritybetweenSBERT[22]embeddingsofthewholelearningmaterial
andcorrespondingWikipediaarticles.Additionally,thesimilarityscorebetween
the embedding of the text of the slide and the embedding of the Wikipedia ab-
stract of the concept is obtained, resulting in a slide similarity score (w ).
Slide
The relevance of the concepts per slide is determined by using the sum of these
two similarity scores ((w ) and (w )). After obtaining the slide’s MCs and
|     | LM  | Slide |     |
| --- | --- | ----- | --- |
their weights, relations between MCs and the corresponding slide, as well as re-
lations between MCs and the learning material, are established to ensure that
concepts exist at both the learning material and slide levels. At this point, the
Slide-EduKG containing the current slide, MCs, learning material, and their re-
lations are stored in a Neo4j database and made available for learners, even if
the construction process has not yet been completed. By storing the data after
annotating each slide, allows learners to explore Slide-EduKGs for completed
slides without waiting for the full EduKG construction to finish. Additionally,
combining slide-level and learning material-level weights ensures balanced con-
cept importance, reducing bias toward either the slide or the overall learning
material. Once all slides have been annotated, the concept expansion step is
activated.
| 2.4 Concept Expansion |     |     |     |
| --------------------- | --- | --- | --- |
Since keyphrase extraction and concept identification may overlook some rele-
vant concepts [18], we expand the identified concepts to increase EduKG cov-
erage and diversity to better support knowledge exploration. To achieve this,
we apply two expansion strategies based on semantic relationships in DBpedia,

as proposed by Manrique et al. [17]: related concept expansion and category-
based expansion. In related concept expansion, semantically linked concepts are
added to the EduKG using SPARQL queries over the dbo:wikiPageWikiLink
property. Whereas, in category-based expansion, hierarchical categories are re-
trievedviathedct:subjectproperty.Afteridentifyingtherelatedconcepts(RCs)
and categories (Cts), their embeddings are generated using SBERT. For RCs,
theembeddingsarederivedfromtheabstractsoftheircorrespondingWikipedia
articles, whereas Cts’ embeddings are based on their names. Cosine similarity is
thencalculatedbetweentheembeddingsofeachMCanditsassociatedRCsand
Ctstoassesstheirsemanticcloseness.Additionally,cosinesimilarityismeasured
between the RCs and Cts and the whole learning material. These two similarity
scores are summed up to compute a unified weight for each RC and Ct. This
overallweightisusedtorankthemallowingthemostrelevantRCsandCtstobe
selected.Specifically,thetop20RCsandtop3CtsforeachMCareretainedand
integrated into the EduKG. This method enhances the structure of the EduKG
by incorporating and exploring semantically related concepts and categories.
After building the EduKG slide by slide, it is then aggregated to create a
LM-EduKG,thatisacompositeofalltheslide-EduKGs.Thisapproachenforces
two key constraints: 1) The concepts related to a slide must adequately capture
the content of that slide, and, 2) Any concept appearing at the lower level i.e.,
Slide-EduKG should also be included at the higher level i.e., LM-EduKG.
3 Evaluation
For the evaluation we used CourseMapper, to construct and visualize EduKG
fromPDFlearningmaterialsusingtheproposedpipeline.Weevaluatetheaccu-
racy of the generated EduKG using the simple random sampling (SRS) method
proposedbyGaoetal.[12].Thismethodevaluatesthecorrectnessofsamplesin
a KG, which consist of triples of (subject, predicate, object), where subject and
object can be any two nodes in the KG, and predicate is the relation that links
them.Theevaluationinvolvestwokeytasks:entityidentificationwhichrequires
theevaluatorstoverifythecorrectnessofanodeentitybyconsideringcontextual
information, and relationship validation which assesses the correctness of rela-
tionsbetweensubjectandobjectnodes.Thefinalaccuracyscoreµ iscomputed
s
as the mean of sample judgments. To ensure statistical reliability, the method
followsaniterativesamplingprocesswithapredefinedmarginoferrorthreshold.
If the margin of error for the initial sample set exceeds the threshold, additional
samples are evaluated until the accuracy stabilizes within the acceptable range.
The results are presented using the normal approximation, which is the mean
value ± the standard deviation value σ. The mean value of the evaluated sam-
ple set µ represents accuracy and falls between 0 and 1, where higher values
s
indicate greater accuracy. Two course experts of the same course were recruited
andanEduKGwasgeneratedforevaluationusingarandomPDFmaterialfrom
their course in CourseMapper. The evaluation process took 4 hours where the
firstannotatorevaluated200randomsamplesfromthegeneratedEduKG,while

the second annotator evaluated 180 random samples, making sure that each an-
notatorevaluatedadifferentsampleset.Themeanvalueofaccuracy±standard
deviation (µ ±σ) is found to be 0.4 ± 0.049. This indicates that approximately
s
40% of the evaluated triples were judged as correct with respect to both entity
identification and relationship validation. The standard deviation of 0.049 indi-
catesrelativelylowvariabilityinthejudgmentsacrossthesample,implyingthat
the accuracy estimates are consistent and reliable within the evaluated subset.
The narrow spread strengthens confidence in the stability of the reported accu-
racyandsuggeststhattheresultsarerepresentativeoftheoverallqualityofthe
EduKG.
4 Pipeline Optimization
The observed accuracy of EduKG generated by the proposed pipeline, while
indicativeofpartialsuccess,isrelativelylowparticularlyintheeducationalcon-
text, where the reliability of knowledge representations is critical for support-
ingmeaningfullearning.Thisunderscorestheneedforsystematicoptimizations
withinthepipelinetoensuretheEduKGsaremoreaccurate,efficient,andeasily
accessible,tosupporteffectivelearningexperiences.Inanefforttoaddressthese
limitations,weproposeaseriesofoptimizationsacrossvariousstepsoftheinitial
pipeline, with the anticipation of achieving higher accuracy and efficiency.
4.1 Worker-based Architecture
One major limitation of the proposed pipeline is its implementation as an API
within a Python-Flask application. While generally a reasonable approach, it is
unsuitable for the time-intensive EduKG generation process. Handling multiple
simultaneousrequestscanoverloadthesystem,especiallywhenusersrequestthe
EduKGs for multiple materials at once. Additionally, failures at any stage leave
the database in an inconsistent state with no straightforward recovery method.
Thecurrentsystemalsolacksrequestqueuing,forcinguserstoretryiftheserver
is busy. To address these issues, a worker-based architecture is proposed. This
approach utilizes job queues and multiple workers that continuously process
queued EduKG construction tasks. Each worker retrieves a job, executes it,
stores the results in the database, and updates the user about its status. This
architecture enables horizontal scalability by adding more workers as needed,
ensuresfailedjobsareautomaticallyre-queued,andallowsrequestqueuingwhen
all workers are busy. Redis is chosen as the message broker due to its simplicity,
reliability, and efficiency as an in-memory database.
4.2 Data Preprocessing
AmajorbottleneckintheproposedpipelineisitsrelianceontheWikipediaAPI
particularly in concept annotation, weighting and expansion modules, which in-
troducessignificantlatencyduetoahugenumberofnetworkrequests.Addition-
ally,generatingembeddingsforidentifiedconceptsfurtherimpactsperformance.

Tomitigatetheseissues,anofflinedatapreprocessingstepisproposed.Thisstep,
executed once a month, extracts relevant data from the Wikipedia XML dump,
includingarticlenames,abstracts,inter-articlelinks,categoryassociations,redi-
rections,anddisambiguationpages.Theextracteddataisthenusedtogenerate
embeddings for concept abstracts and category names using the SBERT all-
mpnet-base-v2 sentence embedding model. The processed information is stored
in a PostgreSQL database, allowing near-instant access to embeddings, cate-
gories, and relationships during EduKG generation. While this approach in-
creases storage requirements and preprocessing time, the benefits of eliminating
network latency and reducing redundant computations significantly outweigh
thesecosts.Moreover,thedatabaseremainsaccessibletoEduKGpipelinework-
ers even if Wikipedia API is down or being updated.
4.3 Optimization of Text Extraction
The current pipeline originally employed a naive text extraction method using
PDFMiner.However,thisapproachlackedanypreprocessing,resultinginsignif-
icant inaccuracies caused by the inclusion of noisy elements such as slide titles,
page numbers, references, and footers. To improve the reliability of extracted
content, the text extraction module is substantially enhanced to include struc-
tured analysis aimed at determining the relevance of extracted elements and
ensuring accurate segmentation of sentences and bullet points. The improved
approach incorporates several analytical techniques to ensure cleaner and more
meaningful output. Font size analysis is used to assess whether adjacent text
elementsshouldbetreatedaspartofthesamesentence.Ifthedifferenceinfont
size between two elements exceeds 0.5 points, they are considered separate sen-
tences. In addition, text distance analysis is applied to account for vertical and
horizontal spacing; when the distance between two adjacent elements is more
than 1.5 times the respective line height or width, segmentation occurs at that
point. To filter out repetitive or irrelevant content such as footers, sidebars, and
page numbers, text similarity analysis is also employed. After removing non-
alphabetical characters, any text fragment that appears in the same location on
more than half of the pages, or on at least five pages in documents with fewer
than ten pages, is classified as noise and removed. Furthermore, bullet point
analysis is integrated to correctly segment list items, addressing inconsistencies
introduced by various PDF rendering tools. Bullet points embedded within text
naturallyserveassentenceseparators.However,whenbulletpointsarerendered
as separate graphical elements, such as circles or rectangles, additional spatial
analysisisrequired.Theseelementsareidentifiedbasedontheirpositionrelative
to adjacent text, under the assumption of a left-to-right writing system. Once
a bullet point is detected, the following text is treated as the start of a new
sentence. Overall, this enhanced methodology substantially improves the accu-
racy of the text extraction module and consequently keyphrase identification by
filtering irrelevant content and preserving the semantic structure of the learning
material.

Evaluation and Results: Toevaluatetheimpactoftheproposedchanges,we
comparedthetextextractedfromtheoptimizedmodulewiththeinitialone(see
Section2.1).ExistingdatasetslikeGrotoap2[26],PubMedandBioMedCentral
[8] etc., mainly contain text from scientific articles, which do not align with our
use case of extracting text from slides and PDF learning materials. Therefore, a
different evaluation approach is required. Bast et al. [7] recommend extracting
structure from TeX files and evaluating text extraction based on the rendered
PDFs, but this method is applicable only to LaTeX-based presentations, which
areasmallsubsetofalllearningmaterials.Forthisevaluation,anewdatasetwas
created with materials from various sources i.e. LaTeX, Microsoft PowerPoint,
andMicrosoftWord.Atotalof24PDFmaterialswereselected,ensuringvariety
in layout and content types. The evaluation consisted of three steps. First, text
was extracted from the slides using PDFMiner. Second, a human annotator
labeled each text block with categories: header, content, footer, page number,
navigation, figure, or empty. The final dataset contained 643 annotated text
parts from 24 slides across 7 different learning materials. Third, comparing the
human annotations to the output of both text extraction modules and calculate
precision,recallandF1scores.Wefurtherutilizedthetextextractionevaluation
criteria proposed by Bast et al. [7], which is divided into three groups: newline
differences, which capture the quality of the detection of paragraph boundaries
(NL+ is the number of spurious newlines in the output file, whereas NL− is
the number of missing newlines in the output file); paragraph differences, which
capture the quality of the distinction between body and non-body text and of
(P+ P−
the reading order is the number of spurious paragraphs, is the number
of missing paragraphs, and P↕ is the number of rearranged paragraphs in the
outputfile);andworddifferences,whichcapturethequalityoftherecognitionof
individualwordsandtheirboundaries(W+isthenumberofspuriouswords,W−
isthenumberofmissingwords,andW∼isthenumberofmisspelledwordsinthe
output file). The results are shown in Table 3 and 4, which clearly demonstrate
that our new optimizations outperform the earlier one in nearly every measure.
| Table 3. Comparison | of the optimized | text extraction | vs. earlier one |
| ------------------- | ---------------- | --------------- | --------------- |
| Text Extraction     | Type             | Module Type     | P R F1          |
|                     |                  | Initial         | 0.64 0.96 0.77  |
Content and figure
|     |     | Optimized | 1.0 0.970.98 |
| --- | --- | --------- | ------------ |
|     |     | Initial   | 0.0 0.0 0.0  |
Non-content
|                       |            | Optimized | 0.93 1.0 0.96  |
| --------------------- | ---------- | --------- | -------------- |
|                       |            | Initial   | 0.82 0.08 0.14 |
| Beginning of sentence | in content |           |                |
|                       |            | Optimized | 0.940.950.95   |
|                       |            | Initial   | 0.0 0.0 0.0    |
| Beginning of sentence | in figure  |           |                |
|                       |            | Optimized | 0.360.380.37   |

Table 4. Results of the evaluation of the initial vs. optimized text extraction using
the differences criteria proposed by [7]
Module NL+ NL− P+ P− P↕ W+ W− W∼
Initial 3 230 230 12 1 0 0 1
Optimized 52 49 1 17 1 0 0 1
4.4 Optimization of Concept Annotation
In the concept annotation module, extracted keyphrases are sent to the DB-
pedia Spotlight API for annotation. Multiple requests are processed simulta-
neously, making the total annotation time dependent on the longest individual
request, aside from network overhead. However, this approach has three main
limitations: (1) DBpedia Spotlight may return irrelevant or miss relevant an-
notations, (2) sending only keyphrases omits contextual information crucial for
accurate interpretation, and (3) as an online service, DBpedia Spotlight can be
inconsistent and unreliable. To mitigate these issues, a concept weighting and a
concept disambiguation modules are integrated to filter irrelevant concepts and
enhance annotation accuracy in the EduKG. Earlier we determined the weight
of each MC with respect to each slide and to the whole learning material (see
Section 2.3). We use this same strategy (named as concept weighting) further
in concept disambiguation; a process that enhances EduKG accuracy by iden-
tifying better alternatives to DBpedia-annotated concepts. It checks whether
an annotated concept is the title of or linked from a Wikipedia disambiguation
page. A disambiguation page is a Wikipedia page that lists articles sharing the
same or a similar title. If this condition is met, all linked pages are considered
alternative concepts, which are then weighted by the concept weighting strat-
egy. The highest-weighted concept replaces the original annotation. This step
helps improve the quality of the EduKG by providing alternative annotations
for keyphrases that may have been incorrectly annotated in the concept anno-
tation step. This is because DBpedia only knows the keyphrase that is passed,
but not the context thereof. The next step is knowledge graph pruning, i.e., re-
moving irrelevant concepts from the EduKG. Irrelevant concepts are defined as
conceptswithalowweightasdeterminedbytheweightingstrategy.Allconcepts
whose weight falls below the weight threshold i.e. 0.192 (based on experiments
mentioned below), are removed from the EduKG.
Evaluation and Results: The performance of this module is influenced by
three parameters: the sentence embedding model, the weight threshold, and
the inclusion of the disambiguation step. The sentence embedding model, used
to compute concept-material similarity, significantly impacts concept weight-
ing. Three pretrained transformer models are compared: all-mpnet-base-v2 [24],
known for its accuracy but slow performance; all-MiniLM-L6-v2 [24], offering
a balance between speed and accuracy; and msmarco-distilbert-base-tas-b [23],
optimized for retrieval tasks. The evaluation uses the CCI dataset [17], consist-
ing of transcripts from 96 programming-related learning videos annotated by

seven experts. The weight threshold is ignored, and instead, the top-1, top-2,
top-3, top-5, and top-10 concepts per resource are selected and evaluated using
Precision (see Table 5). Results show that all-mpnet-base-v2 matches expert-
annotatedconceptshighest,followedcloselybyall-MiniLM-L6-v2andmsmarco-
distilbert-base-tas-b, which perform similarly. Due to its superior performance,
all-mpnet-base-v2 is selected to be used for embeddings generation.
Table 5. Precision of the sentence embedding models
Model Top-1Top-2Top-3Top-5Top-10
msmarco-distilbert 0.18 0.16 0.14 0.10 0.07
all-MiniLM-L6-v2 0.17 0.15 0.13 0.09 0.06
all-mpnet-base-v2 0.25 0.19 0.16 0.13 0.09
An additional experiment was conducted to determine the optimal weight
threshold for knowledge graph pruning. Using the CCI dataset [17], expert-
annotatedconceptswereweightedagainsttranscriptsusingourweightingstrat-
egy.Resultsshowthat50%ofconceptshaveaweightabove0.471,whereweight
falls in the range of [−1,1] with all the weights falling between 0.028 and 0.744.
However,usingsuchalowthresholdwouldintroduceexcessivenoiseintoEduKG.
Since95%ofweightsfallbetween0.192and0.774,0.192isselectedastheweight
threshold, meaning that all concepts having a weight less than 0.192 will be re-
moved from the EduKG (knowledge graph pruning step).
Lastly, we evaluated the impact of introducing disambiguation step on the
generated EduKG accuracy. Using the CCI dataset [17], EduKG was gener-
ated twice, once with and once without disambiguation. Precision, Recall, and
F1-score were computed (see Table 6). Results confirm that disambiguation en-
hances EduKG accuracy, emphasizing the importance of considering context
rather than just keyphrases during annotation. Consequently, the disambigua-
tion step is included in the optimized EduKG construction pipeline.
Table 6. Concept annotation with and without concept disambiguation
Method PrecisionRecallF1-Score
Initial Pipeline (Without Disambiguation) 0.13 0.17 0.14
Optimized Pipeline (With Disambiguation) 0.18 0.29 0.23
4.5 Optimization of Concept Expansion
Concept expansion is the process of assigning related concepts (RCs) and Cat-
egories (Cts) to the identified main concepts (MCs). In the proposed initial
pipeline,theseRCsandCtswereretrievedfromDBpediausingSPARQLqueries.

While SPARQL queries offer a straightforward method for retrieving RCs and
Cts,theycomewithpracticallimitations.Specifically,queryingpublicSPARQL
endpoints at scale can lead to performance bottlenecks due to latency, rate lim-
iting,orinconsistentresponsetimes,makingtheapproachlesssuitableforhigh-
throughput or time-sensitive applications. Moreover, relying on external infras-
tructure introduces risks related to availability and long-term stability, as these
endpoints may become temporarily inaccessible or deprecated without warning.
Toaddresstheseissues,weinsteadretrieveRCsandCtsfromourlocallyhosted
Wikipedia dump (Section 4.2). This alternative ensures faster and more reliable
access to the required data while giving us full control over the extraction pro-
cess.Italsoeliminatesexternaldependencies,enablingmorescalableandrobust
integration within our pipeline.
Related-concept expansion consists of three steps: candidate set creation,
candidate set weighting, and candidate pruning. It works by creating a set of
expansion candidates for each MC. This expansion candidate set contains all
Wikipedia pages linking and linked to from the Wikipedia page of the MC.
These candidates are then weighted by computing the cosine similarity between
the embedding of the abstract of the Wikipedia page of the candidate and the
embedding of the text of the whole PDF material. After every candidate RC
hasbeenassignedaweight,theyaresortedbyweightandthetop-20candidates
for each MC are chosen as the final set of RCs for that MC. Similarly, category
expansion process consists of candidate set creation, candidate set weighting,
andcandidatepruning.Thecategoryexpansioncandidatesetconsistsofallcat-
egoriesofthealltheMCsofthePDFmaterial.Thecategoriesoftheconceptsare
the Wikipedia categories to which the Wikipedia article of the concept belongs.
This list of categories is retrieved from the Wikipedia dump database which
was created in the preprocessing step (Section 4.2). The candidate set is then
weighted by computing the product of the normalized category weight and the
connected concepts weight. The normalized category weight (w ) is the cosine
nc
similarity between the embedding of the category name and the embedding of
the text of whole PDF material. The connected concepts weight (w ) is the in-
cc
verseofthelogarithmofthenumberofMCsconnectedtothecategoryplusone.
The one is added to avoid zero weights. Using the number of connected MCs
to a category allows more relevant categories to the learning material, being
assigned a higher weight. The embedding of the category name is precomputed
and is simply retrieved from the database. Based on this final weight, the top-5
categories for each MC are then kept and the rest are discarded.
5 Evaluation of the Optimized Pipeline
TheoptimizationsproposedinvariousstepsoftheEduKGconstructionpipeline
were evaluated in terms of efficiency and accuracy of the generated EduKG.

5.1 Evaluation of EduKG Efficiency
Theruntimeoftheoptimizedpipelinewasevaluatedandcomparedtotheinitial
versionofthepipelineonamachinewiththefollowingspecifications:CPU:AMD
Ryzen 5 5600, RAM: 32GB, Storage: 4TB NVMe M.2 SSD, GPU: None. The
GPU was intentionally excluded to reflect performance on a typical commodity
server. The speed and memory usage of the pipeline was measured using the
following metrics: 1) Mean time per slide, computed as the time required to
extract MCs from a PDF learning material divided by the number of slides in
the material, and 2) Mean time per concept, computed as the time required to
expandtheknowledgegraphinalearningmaterialdividedbythenumberofMCs
in the material. Furthermore, EduKG creation and expansion were evaluated
separately. A diverse dataset of learning materials, varying in size, structure,
density, and topics, was created. To test scalability, the dataset included one
largematerialwith279pages,whiletheremainingmaterialshad31to52pages.
The initial and optimized version of the pipeline were run on each material in
thedataset,withDBpediaresponsecachingdisabledtoensureresultsaccurately
reflect performance on new, unseen data.
The evaluation results (see Table 7) show that the optimized pipeline is
over 10 times faster in EduKG construction and more than 100 times faster in
EduKGexpansion.Thissubstantialimprovementinexecutiontimecomparedto
the initial version is primarily due to the use of a preprocessed local Wikipedia
database with precomputed embeddings. Leveraging this local dump for both
concept annotation and concept expansion significantly reduces computational
overhead and enhances the overall reliability of the pipeline.
5.2 Evaluation of EduKG Accuracy
This evaluation aims to assess the accuracy of the EduKG generated with the
proposed optimizations in the pipeline and compare it to the EduKG generated
with the initial version of the pipeline (Section 2). The optimized pipeline is
evaluated using the same approach as earlier, employing SRS and expert an-
notators. To ensure comparability, the same evaluation method, PDF material,
metrics, and parameters are used. The process begins with randomly selecting
a sample from the EduKG generated by the optimized pipeline, which is then
annotated by the same two experts until the stopping criteria are met. The ex-
pert annotation part of the evaluation took around 2.5 hours in total. The first
expert annotated a random set of 200 triples and the second one annotated 203
triples till we met the stopping criteria. The results of the evaluation are shown
in Table 7.
The evaluation reveals a 17.5% improvement in EduKG accuracy compared
to the initial version of the pipeline, underscoring the effectiveness of the pro-
posedoptimizations.Particularly,improvementsinthetextextractionstepplayed
a critical role by significantly reducing noise in text, which previously led to
incorrectorredundantannotations.Furthermore,theintegrationofconceptdis-
ambiguationandknowledgegraphpruningeffectivelyfilteredoutirrelevantcon-
cepts, contributing to a more accurate and semantically coherent EduKG. The

adoption of the all-mpnet-base-v2 embedding model further strengthened the
pipeline, enabling the generation of high-quality embeddings that substantially
improvedtheperformanceoftheconceptweightingstep.Despitetheseadvance-
ments,theoverallincreaseinaccuracyremainsmoderate.Thiscanbeattributed
to the continued dependence on DBpedia as the primary external knowledge
baseforconceptannotationwhichisanelementcommontobothversionsofthe
pipeline. While the shared knowledge source may have limited the potential for
drasticaccuracygains,theproposedoptimizationsnonethelessyieldedmeaning-
ful improvements in both the accuracy and efficiency of EduKG construction,
| demonstrating | the       | robustness    | and          | scalability | of      | the optimized     | pipeline.      |          |
| ------------- | --------- | ------------- | ------------ | ----------- | ------- | ----------------- | -------------- | -------- |
|               | Table     | 7. Evaluation | results      | of          | EduKG   | accuracy          | and efficiency |          |
|               | Metric    |               |              |             | Initial | PipelineOptimized |                | Pipeline |
|               | Avg. Time | per Slide     | (Generation) |             |         | 24.35 s           |                | 2.3 s    |
Efficiency
|              | Avg. Time | per Concept |        | (Expansion) |     | 222 s     |     | 1.89 s     |
| ------------ | --------- | ----------- | ------ | ----------- | --- | --------- | --- | ---------- |
|              | Accuracy  | (µ )        |        |             |     | 0.4       |     | 0.47       |
| Accuracy     |           | s           |        |             |     |           |     |            |
|              | Accuracy  | (µ ±σ)      |        |             |     |           |     |            |
|              |           | s           |        |             |     | 0.4±0.049 |     | 0.47±0.049 |
| 6 Conclusion |           | and         | Future | Work        |     |           |     |            |
This study presents an end-to-end pipeline for the automatic construction of
Educational Knowledge Graphs (EduKGs) from PDF learning materials within
theMOOCplatform,CourseMapper.Thepipelinegeneratesslide-levelEduKGs
from individual pages/slides of the PDF learning material and subsequently
merges them into a comprehensive EduKG representing the entire learning ma-
terial. Initial evaluation of the EduKG generated by the proposed pipeline indi-
cated moderate performance, emphasizing the importance of further optimiza-
tion to ensure that EduKGs accurately reflect educational content and support
meaningful learning experiences. To address this, we proposed several optimiza-
tions across multiple steps of the pipeline and re-evaluated its performance.
The optimized version achieved a 17.5% improvement in accuracy, along with
significant gains in efficiency where concept annotation became over 10 times
faster, and knowledge graph expansion over 100 times faster. These improve-
ments stem from enhanced text extraction that uses sentence boundary detec-
tionandfilteringofnon-contenttext,theintegrationofapreprocessedWikipedia
dumpdatabasewithprecomputedembeddingsreducingon-the-flycomputation,
and the use of a stronger transformer model all-mpnet-base-v2 for high qual-
ity embedding generation. Furthermore, the disambiguation module improved
concept weighting, resulting in only highly relevant concepts being included in
the EduKG. The updated worker-queue architecture also contributed to im-
proved stability and reduced resource consumption, trading higher storage use
for much lower CPU and memory demands. The pipeline is implemented within

our MOOC platform, CourseMapper, to showcase its practical applicability in
authenticeducationalsettings.Thefinalpipelinepresentsastate-of-the-artsolu-
tionforautomaticEduKGconstruction,withtheflexibilitytobeadaptedacross
| various | educational |           | settings | and use | cases.      |           |              |         |     |
| ------- | ----------- | --------- | -------- | ------- | ----------- | --------- | ------------ | ------- | --- |
| Despite | these       | advances, |          | some    | limitations | remain. A | considerable | portion | of  |
runtime is spent saving expanded concepts in Neo4j, indicating a need for op-
timization in database interactions. The current data preprocessing step lacks
supportforincrementalupdatesoftheWikipediadump,requiringfullreprocess-
ing even for minor changes. Additionally, the text extraction module struggles
withligatures,hyphenatedwords,umlauts,andaccents,andwouldbenefitfrom
moresophisticatedlayoutanalysistobetterhandlecomplexelementsliketables
and figures. The evaluation dataset (CCI) is also limited in coverage and out-
dated, constraining the benchmarking accuracy. A more representative dataset
withlearningmaterialsactivelyusedinpracticeandannotatedbyexpertswould
provideastrongerevaluationframework.Asfuturework,weplantoincorporate
ahuman-in-the-loopmechanism,enablingdomainexpertstorefine,validate,and
enhance the automatically generated EduKGs before publishing it for the end
users. This integration aims to strike a balance between automation and human
expertise,ensuringhigh-qualityEduKGswhilesignificantlyreducingthemanual
effort involved.
Disclosure of Interests. The authors have no competing interests to declare that
| are relevant | to  | the content |     | of this article. |     |     |     |     |     |
| ------------ | --- | ----------- | --- | ---------------- | --- | --- | --- | --- | --- |
References
1. Ain, Q.U., Chatti, M.A., Bakar, K.G.C., Joarder, S., Alatrash, R.: Automatic
constructionofeducationalknowledgegraphs:Awordembedding-basedapproach.
| Information |     | (2023). |     | https://doi.org/10.3390/info14100526 |     |     |     |     |     |
| ----------- | --- | ------- | --- | ------------------------------------ | --- | --- | --- | --- | --- |
14
2. Ain, Q.U., Chatti, M.A., Joarder, S., Nassif, I., Wobiwo Teda, B.S., Guesmi,
| M., | Alatrash, | R.: | Learning | channels | to  | support interaction | and | collaboration | in  |
| --- | --------- | --- | -------- | -------- | --- | ------------------- | --- | ------------- | --- |
coursemapper.In:Proceedingsofthe14thInternationalConferenceonEducation
| Technology |     | and | Computers. | pp. | 252–260 | (2022) |     |     |     |
| ---------- | --- | --- | ---------- | --- | ------- | ------ | --- | --- | --- |
3. Ain, Q.U., Chatti, M.A., Meteng Kamdem, P.A., Alatrash, R., Joarder, S., Siep-
mann,C.:Learnermodelingandrecommendationoflearningresourcesusingper-
sonalknowledgegraphs.In:Proceedingsofthe14thLearningAnalyticsandKnowl-
| edge | Conference. |     | p. 273–283 | (2024). | https://doi.org/10.1145/3636555.3636881 |     |     |     |     |
| ---- | ----------- | --- | ---------- | ------- | --------------------------------------- | --- | --- | --- | --- |
4. Ain, Q.U., Chatti, M.A., Shakhshir, A., Qussa, J., Alatrash, R., Joarder, S.: Top-
| down      | vs. | bottom-up        | approaches |       | for automatic | educational      | knowledge | graph | con- |
| --------- | --- | ---------------- | ---------- | ----- | ------------- | ---------------- | --------- | ----- | ---- |
| struction |     | in coursemapper. |            | arXiv | preprint      | arXiv:2505.10069 | (2025)    |       |      |
5. Alatrash,R.,Chatti,M.A.,Ain,Q.U.,Joarder,S.:Transparentlearnerknowledge
| state | modeling | using | personal | knowledge |     | graphs and graph | neural | networks. | In: |
| ----- | -------- | ----- | -------- | --------- | --- | ---------------- | ------ | --------- | --- |
AdjunctProceedingsofthe32ndACMConferenceonUserModeling,Adaptation
| and | Personalization. |     | p.  | 591–596 | (2024). | https://doi.org/10.1145/3631700.3665230 |     |     |     |
| --- | ---------------- | --- | --- | ------- | ------- | --------------------------------------- | --- | --- | --- |
6. Augenstein, I., Das, M., Riedel, S., Vikraman, L., McCallum, A.: Semeval 2017
task10:Scienceie-extractingkeyphrasesandrelationsfromscientificpublications.
| arXiv | preprint | arXiv:1704.02853 |     |     | (2017) |     |     |     |     |
| ----- | -------- | ---------------- | --- | --- | ------ | --- | --- | --- | --- |
7. Bast,H.,Korzen,C.:Abenchmarkandevaluationfortextextractionfrompdf(06
| 2017). | https://doi.org/10.1109/JCDL.2017.7991564 |     |     |     |     |     |     |     |     |
| ------ | ----------------------------------------- | --- | --- | --- | --- | --- | --- | --- | --- |

8. BMC: Bmc, research in progress (2018), https://www.biomedcentral.com/
9. Chen, P., Lu, Y., Zheng, V.W., Chen, X., Yang, B.: Knowedu: A system to con-
struct knowledge graph for education. Ieee Access 6, 31553–31563 (2018)
10. Engelbrecht, E., Ilkou, E., Abu-Rasheed, H., Chaves-Fraga, D., Jiménez-Ruiz, E.,
Labra-Gayo,J.E.: Teachingknowledgegraph forknowledgegraphs education.Se-
mantic Web: interoperability, usability, applicability (2024)
11. Fettach,Y.,Ghogho,M.,Benatallah,B.:Knowledgegraphsineducationandem-
ployability: A survey on applications and techniques. IEEE Access 10 (2022)
12. Gao, J., Li, X., Xu, Y.E., Sisman, B., Dong, X.L., Yang, J.: Efficient knowledge
graph accuracy evaluation. arXiv preprint arXiv:1907.09657 (2019)
13. Grootendorst, M.: Keybert: Minimal keyword extraction with bert. https://
maartengr.github.io/KeyBERT (2020)
14. Hogan, A., Blomqvist, E., Cochez, M., d’Amato, C., Melo, G.D., Gutierrez, C.,
Kirrane, S., Gayo, J.E.L., Navigli, R., Neumaier, S., et al.: Knowledge graphs.
ACM Computing Surveys (CSUR) 54(4), 1–37 (2021)
15. Hulth, A.: Improved automatic keyword extraction given more linguistic knowl-
edge. In: Proceedings of the 2003 conference on Empirical methods in natural
language processing. pp. 216–223 (2003)
16. Jhajj, G., Zhang, X., Gustafson, J.R., Lin, F., Lin, M.P.C.: Educational knowl-
edge graph creation and augmentation via llms. In: International Conference on
Intelligent Tutoring Systems. pp. 292–304. Springer (2024)
17. Manrique, R., Grévisse, C., Mariño, O., Rothkugel, S.: Knowledge graph-based
core concept identification in learning resources. In: Joint International Semantic
Technology Conference. pp. 36–51. Springer (2018)
18. Manrique,R.,Marino,O.:Knowledgegraph-basedweightingstrategiesforaschol-
arly paper recommendation scenario. In: KaRS@ RecSys. pp. 5–8 (2018)
19. Mendes, P.N., Jakob, M., García-Silva, A., Bizer, C.: Dbpedia spotlight: shedding
lightonthewebofdocuments.In:Proceedingsofthe7thinternationalconference
on semantic systems. pp. 1–8 (2011)
20. Qu, K., Li, K.C., Wong, B.T., Wu, M.M., Liu, M.: A survey of knowledge graph
approaches and applications in education. Electronics 13(13), 2537 (2024)
21. Ramakrishnan,C.,Patnia,A.,Hovy,E.,Burns,G.A.:Layout-awaretextextraction
fromfull-textpdfofscientificarticles.Sourcecodeforbiologyandmedicine(2012)
22. Reimers,N.,Gurevych,I.:Sentence-bert:Sentenceembeddingsusingsiamesebert-
networks. arXiv preprint arXiv:1908.10084 (2019)
23. Reimers, N., Gurevych, I.: msmarco-distilbert-base-tas-b. https://huggingface.
co/sentence-transformers/msmarco-distilbert-base-tas-b (2023)
24. Reimers,N.,Gurevych,I.:Sentence-bert:Pretrainedmodels(2023),https://www.
sbert.net/docs/sentence_transformer/pretrained_models.html
25. TheBloke: TheBloke/Mistral-7B-Instruct-v0.1-GGUF. https://huggingface.co/
TheBloke/Mistral-7B-Instruct-v0.1-GGUF (2024)
26. Tkaczyk, D., Szostek, P., Bolikowski, L.: Grotoap2-the methodology of creating a
largegroundtruthdatasetofscientificarticles.D-LibMagazine20(11/12)(2014)
27. Zhao,B.,Sun,J.,Xu,B.,Lu,X.,Li,Y.,Yu,J.,Liu,M.,Zhang,T.,Chen,Q.,Li,
H., et al.: Edukg: a heterogeneous sustainable k-12 educational knowledge graph.
arXiv preprint arXiv:2210.12228 (2022)
28. Zhong,L.,Wu,J.,Li,Q.,Peng,H.,Wu,X.:Acomprehensivesurveyonautomatic
knowledge graph construction. ACM Comput. Surv. (2023)
29. Zhu,Y.,Wang,X.,Chen,J.,Qiao,S.,Ou,Y.,Yao,Y.,Deng,S.,Chen,H.,Zhang,
N.:Llmsforknowledgegraphconstructionandreasoning:Recentcapabilitiesand
future opportunities. World Wide Web 27(5), 58 (2024)