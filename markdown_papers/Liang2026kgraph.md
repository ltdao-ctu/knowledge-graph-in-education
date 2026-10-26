---
title: "Liang2026kgraph"
source: "Liang2026kgraph.pdf"
source_sha256: "25b8c9cfc60f3f70ae0fcc0eb49b54cc1ae45f40bd218ff00142104b3a761591"
converted_at: "2026-10-26T07:05:01.892973+00:00"
markitdown_version: "0.1.9"
---
October6,2026
K12-KGraph: A Curriculum-Aligned Knowledge
Graph for Benchmarking and Training Educational
LLMs
Hao Liang∗,1,4, Qihan Lin∗,1, Mingrui Chen2,4, Hengyi Feng1, Zhaoyang
Han1, Xiaochen Ma3, Zhen Hao Wong1, Meiyi Qiang1, Linzhuang Sun2,
Wentao Zhang‡,1,4
1PekingUniversity,2UniversityofChineseAcademyofSciences3HKUST
4ZhongguancunAcademy
Large language models (LLMs) are increasingly deployed in K–12 education, yet existing bench-
marks such as C-Eval, CMMLU, GaokaoBench, and EduEval measure only whether a model
can answer an exam question, i.e., factual recall. Effective educational AI further requires
: the structured understanding of how knowledge is organized and visually
curriculumcognition
presented, including prerequisite chains, concept taxonomies, experiment–concept links, and
pedagogical sequencing. Curriculum cognition is neither probed by current benchmarks nor
explicitly taught by current instruction-tuning data. To close this gap, we introduce ,
K12-KGraph
a curriculum-aligned knowledge graph extracted from the official People’s Education Press text-
books, covering mathematics, physics, chemistry, and biology across primary, middle, and high
school, with nine node types (Book, Chapter, Section,Concept, Skill, Experiment, Exercise,
Figure, VisualElement) and fourteen relation types spanning both curriculum structure and
visual grounding. Building on this single graph, we derive two complementary resources:
K12-
,a23,640-questionmulti-selectbenchmarkacrossfivegraph-derivedtaskfamilies(Ground,
Bench
Prereq, Neighbor, Evidence, and Locate) that jointly probe curriculum cognition; and
,aKG-guidedsupervisedfine-tuningcorpusof7,335samples(K12-Train-Full),including
K12-Train
2,267 text-only QA pairs (K12-Train-Text) and 5,068 multimodal VQA pairs (K12-Train-MM).
Experiments expose a clear gap and a clear remedy: on K12-Bench, even a strong proprietary
model (Gemini-3-Flash) reaches only 57% exact match and a strong open-source model (Gemma-
4-31B-IT)only46%,withPrereqandNeighborbeingthehardest;yetourtrainingexperiments
show that domain-specific supervision from K12-Train can effectively address this limitation.
For LLMs, under a strictly matched 2,300-sample SFT budget, K12-Train-Text consistently
outperforms equally sized subsets of eight mainstream instruction-tuning corpora (OpenHermes,
Infinity, UltraChat, WizardLM, DataFlow, LMSYS, SmolTalk, Tulu-3) on both GaokaoBench
and EduEval, demonstrating the sample efficiency of structurally grounded curriculum data. For
VLMs, K12-Train-Full achieves the best overall performance on Gaokao-MM, MDK12-medium,
and K12Vista among all compared training configurations despite using fewer samples than the
full DataFlow and WizardLM baselines, and consistently outperforms both K12-Train-Text and
K12-Train-MM, showing the complementarity of textual and visual supervision.
∗Equal Contribution, ‡Corresponding author
SourceCode: https://github.com/haolpku/K12-Dataset
Dataset: https://huggingface.co/datasets/lhpku20010120/K12-KGraph
@ DatasetWebsite: https://haolpku.github.io/K12-KGraph-page/
6202
tcO
3
]LC.sc[
4v53690.5062:viXra

Contents
1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3
2 RelatedWork . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4
3 K12-KGraph . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 5
3.1 Schema Design . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 5
3.2 Construction Pipeline . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 5
3.3 Graph Statistics . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 6
4 BenchmarkandTrainingDatafromK12-KGraph . . . . . . . . . . . . . . . . . . . . . . . . . 6
4.1 K12-Bench: Benchmark Construction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 6
4.2 K12-Train: KG-Guided Data Synthesis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 7
5 ExperimentsandResults . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 8
5.1 Experimental Settings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 8
5.2 Benchmarking LLMs on K12-Bench . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 10
5.3 K12-Train for Educational SFT . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 11
5.3.1 Text-Only Fine-Tuning Results . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 11
5.3.2 Multimodal Fine-Tuning Results . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 12
5.3.3 Analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 13
6 Conclusion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 14
A K12-KGraphConstructionDetails . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 18
A.1 Node and Edge Attribute Specification . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 18
A.2 Source Documents and Preprocessing Setup . . . . . . . . . . . . . . . . . . . . . . . . . . . . 18
A.3 Prompt for KG Extraction. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 19
B K12-BenchConstructionDetailsandEvaluationProtocol . . . . . . . . . . . . . . . . . . . . 23
B.1 Distractor Pool and Structural Sampling Rules . . . . . . . . . . . . . . . . . . . . . . . . . . 23
B.2 Prompt for Pedagogical Filtering . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 24
B.3 Benchmark Composition Statistics . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 25
B.4 Answering Prompt and Decoding Rules . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 26
B.5 Baseline EM/F1 Computation for the Random Predictor. . . . . . . . . . . . . . . . . . . . . 27
B.6 Illustrative Example of KG-Grounded Resource Derivation. . . . . . . . . . . . . . . . . . . . 28
C K12-TrainConstructionDetailsandSFTProtocol . . . . . . . . . . . . . . . . . . . . . . . . . 28
C.1 Prompt for QA Synthesis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 28
C.2 Training Configuration . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 31
C.3 Baseline Subsampling and Fairness Controls . . . . . . . . . . . . . . . . . . . . . . . . . . . . 31
D ValidationandQualityAssurance . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 31
D.1 Validation Strategy, Annotator Background, and Ethics . . . . . . . . . . . . . . . . . . . . . 32
D.2 KG Validation: Structural Checks and Human Verification. . . . . . . . . . . . . . . . . . . . 32
D.3 Spot-Check Validation of K12-Bench and K12-Train . . . . . . . . . . . . . . . . . . . . . . . 33
E ExtendedResultsandSanityChecks . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 34
E.1 Full Benchmark Results . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 34
E.2 Stability Across Random Seeds . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 34
E.3 Overlap and Leakage Analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 35
2

K12-KGraph 3
1 Introduction
Large language models (LLMs) have become strikingly proficient at answering K–12 exam questions. On
benchmarks such as C-Eval [9], CMMLU [14], GaokaoBench [33], and EduEval [21], frontier models now
rival, and sometimes surpass, top human students, fueling rapid interest in LLM-powered tutoring and exam
preparation [11]. Taken at face value, this progress suggests that educational AI is close to being solved. Yet
anyone who has tried to build a real tutoring product knows that answering a question is only a small fraction
of what a good teacher actually does, and it is precisely the larger fraction that today’s benchmarks leave
untested.
The untested part is what we call : the structured understanding of why a topic must
curriculumcognition
be learned before another, how a laboratory experiment connects to a theoretical concept, and where in the
textbook each idea actually lives. A competent 7th-grade mathematics teacher does not merely know that
“linear equations” is a topic; she knows it requires arithmetic operations as a prerequisite, that it sits as a
sibling of “inequalities” under “algebraic expressions”, and that it first appears in Chapter 3 of the People’s
Education Press textbook. Curriculum knowledge is also communicated through textbook figures: diagrams,
experimentalsetups,geometricfigures,andexerciseillustrationscanexplainaconcept,providevisualevidence
for a relation, or supply information required to solve a problem. None of today’s K–12 benchmarks probe
this kind of structural and visual understanding, and consequently none of today’s training data explicitly
teaches it either. If we care about building AI that supports students, rather than merely testing them, this
gap is the bottleneck.
Tocloseit,webuildeverythingfromasingleresource: acurriculum-alignedknowledgegraphextracteddirectly
from the official Chinese K–12 textbooks (People’s Education Press). The resulting graph, , is a
K12-KGraph
heterogeneous property graph covering mathematics, physics, chemistry, and biology across primary, middle,
and high school. It comprises two components: a textual component that captures curriculum structure and a
multimodal component that captures visual grounding. The textual component contains seven node types
(Concept, Skill, Experiment, Exercise, Section, Chapter, and Book), and edge types encoding taxonomy
(is_a), prerequisite (prerequisites_for), associations (relates_to), verification (verifies), assessment
(tests_concept, tests_skill), location (appears_in), and order (leads_to). The multimodal component
contains two node types (Figure and VisualElement) and edge types encoding composition (contains_-
visual_element), visual semantics (refers_to, illustrates), location (appears_in), exercise dependence
on figures (requires_figure), and visual evidence (supports_edge). Because the graph faithfully mirrors
how the curriculum is organized, we can turn it into evaluation questions by traversing neighborhoods, and
into training data by rendering node properties and edge semantics into QA pairs. A single graph thus yields
both a benchmark that measures curriculum cognition and a training set that explicitly teaches it.
Contributions. Our work makes three contributions:
1. , a large-scale, multi-subject, official-textbook-grounded curriculum-aligned knowledge graph
K12-KGraph
for Chinese K–12, together with a reproducible LLM-based extraction and hierarchical-merge pipeline with
DAG validation on taxonomic and prerequisite relations.
2. , a 23,640-question benchmark of graph-derived multi-select items grouped into five task families:
K12-Bench
Ground (Knowledge Grounding), Prereq (Prerequisite Reasoning), Neighbor (Neighbor Recommenda-
tion), Evidence (Experiment Evidence Chain), and Locate (Cross-Chapter Indexing). These families
together probe structural curriculum understanding. Evaluating ten open-source and proprietary LLMs,
we find that even Gemini-3-Flash reaches only 57% exact match, and a strong open-source model (Gemma-
4-31B-IT [24]) reaches only 46%.
3. , a KG-guided QA synthesis pipeline yielding 7,335 high-quality educational SFT samples,
K12-Train
including a K12-Train-Text containing 2,267 text-only samples, and a K12-Train-MM containing 5,068
multimodal samples. For LLMs, under a strictly matched 2,300-sample budget, SFT on K12-Train-Text
consistently outperforms eight mainstream instruction-tuning corpora (OpenHermes [25], Infinity [15],
UltraChat[4],WizardLM[20],DataFlow[16],LMSYS[34],SmolTalk[1],Tulu-3[12])acrosstwobasemodels
on GaokaoBench and EduEval (e.g., +24.1/+32.4 over the strongest SFT baseline and +114.6/+221.0
over official instruction-tuned variants on GaokaoBench). For VLMs, SFT on K12-Train-Full achieves the

| K12-KGraph |     |     |     |     |     |     |     |     |     | 4   |
| ---------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
Based on
| (i) OCR-based Parser |     |     |                         |     |     |     | (ii) Table-of-Contents Parser |           |             |     |
| -------------------- | --- | --- | ----------------------- | --- | --- | --- | ----------------------------- | --------- | ----------- | --- |
|                      |     |     | ## 1.1 Rational Numbers |     |     |     |                               | Chapter 1 | Rule-based  |     |
|                      |     |     | …                       |     |     |     |                               | Section 1 | Splitting   |     |
Calculate:$(-20)+(+3)–(-5)$
|                  |     |          | …                                       |     |     |     |     | Section 2 |                    |     |
| ---------------- | --- | -------- | --------------------------------------- | --- | --- | --- | --- | --------- | ------------------ | --- |
|                  |     |          | C alculate: $(-5) \times 4 \times (-2)$ |     |     |     |     | Chapter 1 |                    |     |
|                  |     |          | …                                       |     |     |     |     | …         |                    |     |
| K12 TextbookPDFs |     | Markdown |                                         |     |     |     |     |           | Per-sections Files |     |
TOC
(iii) Knowledge Extraction & Knowledge Graph Construction
|     |     |     |     | Positive Number |     |       |             |     |     | Concept   |
| --- | --- | --- | --- | --------------- | --- | ----- | ----------- | --- | --- | --------- |
|     |     |     |     |                 |     | prere | q u isites  |     |     | S k i l l |
Per - s e c t i o n s   F i l e N o d e  • t y p e :   C o n c e p t Usi n g  p o s i t i v e   a n d   n e g a t i ve  E x p e ri m ent
…   +   • d e f :  N u m b e r s  g reater  f o r n u m b e r s   t o   r e p r e s e n t
“ N u m b e r s   g r e a t e r   t h a n   t h a n   0 . o p p o s i t e   q u a n t i t ie s   in   E x e rc i se
| 0 ,   s u c | h   a s   3   a n d   1 . 8 % ,   a r e   |     | Ed g e | • e x | a m p l e : 3 ,  1 .8 % |     |     |     |     |     |
| ----------- | ----------------------------------------- | --- | ------ | ----- | ----------------------- | --- | --- | --- | --- | --- |
c a l l e d   p o s i t i v e   n u m b e r s   … ” p r a c t i c a l  p r o b l e m s
|                               |     |     |     | Q u a n t i ti e     | s  w i th   relatesto | prere | q u isites  | t e s ts     |             |     |
| ----------------------------- | --- | --- | --- | -------------------- | --------------------- | ----- | ----------- | ------------ | ----------- | --- |
|                               |     | LLM |     | opp o s it e   m e a | n in g s.             |       |             |              | tests skill |     |
|                               |     |     |     |                      |                       |       | f o r       | co n c e p t |             |     |
| Graph Schema Constraint Rules |     |     |     | Negative Number      |                       |       |             |              | Exercise 1  |     |
tests concept
(iv) Hierarchical Merge (v) Topological Validation K12-KGraph
| Positive  | Grade 3  |     |     |     |     |     |     |     |     |     |
| --------- | -------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
Merge Section-level
| Number | Section 4 |     |     |     |     |     |     |     |     |     |
| ------ | --------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
to Subject-level
Positive
Number
Grade 7
| Positive  |           |     | Math |     |       |     |     |     |     |     |
| --------- | --------- | --- | ---- | --- | ----- | --- | --- | --- | --- | --- |
|           | Section 1 |     |      |     | Cycle |     |     | DAG |     |     |
Number
Figure 1 Overview of the K12-KGraph construction pipeline. The process consists of five stages: OCR-based
parsingoftextbooks,hierarchicalsegmentationintosections,LLM-basedschema-guidedextractionofnodesandedges,
hierarchical graph merging across sections and books, and structural validation with lightweight human verification.
The design combines automated extraction with rule-based processing and human-in-the-loop checks to ensure both
| scalability and | correctness. |     |     |     |     |     |     |     |     |     |
| --------------- | ------------ | --- | --- | --- | --- | --- | --- | --- | --- | --- |
best overall performance on Gaokao-MM, MDK12-Bench, and K12Vista, surpassing the full DataFlow and
WizardLMbaselineswithamuchsmallersamplesize(7,335vs.10,000/142,759), aswellastheperformance
of K12-Train-Text and K12-Train-MM. These results highlight both the value of in-domain educational
| data and           | the complementarity | of      | textual    | and visual | supervision. |      |     |         |                |            |
| ------------------ | ------------------- | ------- | ---------- | ---------- | ------------ | ---- | --- | ------- | -------------- | ---------- |
| 2 Related          | Work                |         |            |            |              |      |     |         |                |            |
|                    |                     | Several | benchmarks |            | evaluate     | LLMs | on  | Chinese | K–12 subjects. | C-Eval [9] |
| K–12 and education | benchmarks.         |         |            |            |              |      |     |         |                |            |
and CMMLU [14] are broad multi-discipline suites that include K–12 categories but focus on multiple-choice
factual questions. GaokaoBench [33] targets the Chinese college entrance exam (Gaokao) with both objective
and subjective questions. EduEval [21] covers six educational capability dimensions (application, creativity,
ethics, memory, reasoning, understanding). E-Eval [8] and K–12 EduBench [30] further expand coverage.
Multimodal benchmarks such as Gaokao-MM [37], MDK12-Bench [36], and K12Vista [13] evaluate visual
reasoning over educational questions. CK12 [31] incorporates a knowledge graph but focuses on holistic
cognition rather than structural curriculum understanding. All of these benchmarks test whether a model
can answer domain questions; none systematically evaluate whether models understand the structure of the
curriculum, i.e., prerequisite dependencies, concept taxonomies, or pedagogical sequencing.
Educational knowledge graphs. Knowledge graphs have been applied in education for knowledge tracing [19]
andprerequisitediscovery[3]. However,existingeducationalKGstypicallyfocusonasinglesubjectorEnglish-
language courses, and are rarely aligned to an official K–12 curriculum, and generally represent textbook
knowledge as textual entities and relations without explicitly grounding textbook figures. Recent work has
explored using LLMs for KG construction [2, 28], but no prior work has built a large-scale, multi-subject,
curriculum-aligned KG from Chinese K–12 textbooks and used it to both benchmark and train LLMs.

| K12-KGraph |     |     |     |     |     |     |     | 5   |
| ---------- | --- | --- | --- | --- | --- | --- | --- | --- |
Table1 StatisticsofthetextualcomponentofK12-KGraphbysubject. Wereporttheselectedcurriculum-content
node types and relation types after hierarchical merging and deduplication. The total number of leads_to edges is
computed globally and includes cross-subject links, and therefore does not equal the sum of the subject-specific rows.
|     |     | Nodes |     |     |     | Edges |     |     |
| --- | --- | ----- | --- | --- | --- | ----- | --- | --- |
Subject
Book Cpt Skl Exp Exe is_a prereq rel_to verif tes_cpt tes_skl lea_to
| Mathematics | 23 1,475 | 428     | 0 471 288 | 855   | 405   | 0 464   | 229 | 44  |
| ----------- | -------- | ------- | --------- | ----- | ----- | ------- | --- | --- |
| Physics     | 9 1,154  | 197 220 | 186 247   | 648   | 300   | 251 248 | 104 | 19  |
| Chemistry   | 7 2,302  | 451 309 | 270 856   | 1,344 | 1,083 | 468 571 | 251 | 21  |
| Biology     | 9 1,648  | 288 123 | 244 505   | 858   | 386   | 170 391 | 116 | 11  |
Total 48 6,579 1,364 652 1,171 1,896 3,705 2,174 889 1,674 700 282
Table2 StatisticsofthemultimodalcomponentofK12-KGraphbysubject. Countsarereportedafterhierarchical
| merging and | deduplication. |       |     |     |       |     |     |     |
| ----------- | -------------- | ----- | --- | --- | ----- | --- | --- | --- |
|             |                | Nodes |     |     | Edges |     |     |     |
Subject
|     |             | Fig   | Vis_Ele con_ve | ref_to | illus req_fig | sup_edge  |     |     |
| --- | ----------- | ----- | -------------- | ------ | ------------- | --------- | --- | --- |
|     | Mathematics | 3,831 | 5,208 4,490    | 5,256  | 4,006         | 59 529    |     |     |
|     | Physics     | 1,344 | 1,906 1,738    | 1,927  | 1,407         | 0 365     |     |     |
|     | Chemistry   | 1,096 | 1,583 1,485    | 1,642  | 1,154         | 43 568    |     |     |
|     | Biology     | 1,117 | 1,506 1,364    | 1,527  | 1,152         | 0 369     |     |     |
|     | Total       | 7,388 | 10,203 9,077   | 10,352 | 7,719         | 102 1,831 |     |     |
Instruction tuning datasets. Supervised fine-tuning (SFT) with high-quality instruction data is critical for
aligning LLMs [23]. General-purpose datasets such as OpenHermes [25], UltraChat [4], WizardLM [20], Tulu-
3 [12], and SmolTalk [1] cover diverse tasks but lack domain-specific educational knowledge. Self-Instruct [27]
and its variants generate synthetic data from LLMs, but do not leverage structured knowledge sources. Our
KG-guided synthesis approach bridges this gap by grounding training data in curriculum structure.
3 K12-KGraph
| 3.1 Schema | Design |     |     |     |     |     |     |     |
| ---------- | ------ | --- | --- | --- | --- | --- | --- | --- |
WedesignaheterogeneouspropertygraphschematailoredtoK–12education,whichincludesbothtextualand
multimodal components. The schema defines nine node types and fourteen directed edge types, summarized
| in Table | 9 (Appendix A.1). |     |     |     |     |     |     |     |
| -------- | ----------------- | --- | --- | --- | --- | --- | --- | --- |
Each node carries typed properties. For example, a Concept node includes name, definition (preferring
textbookwording),importance(understand/master/important),andoptionalfieldssuchasformula,aliases,
and examples. An Experiment node includes instruments, is_student (whether it is a student-performed
| experiment),     | process, phenomena, | and | conclusion. |     |     |     |     |     |
| ---------------- | ------------------- | --- | ----------- | --- | --- | --- | --- | --- |
| 3.2 Construction | Pipeline            |     |             |     |     |     |     |     |
Construction proceeds in five automatic stages, as illustrated in Figure 1. (i) An OCR-based parser
(MinerU [22]) converts textbook PDFs into structured Markdown while preserving heading hierarchy, mathe-
maticalformulas,rawtext,andimageassets. (ii)Atable-of-contentsparserproducesasections_index.json
manifest and splits the Markdown into per-section files, and associates each image with its section text.
(iii) For each section, we prompt GPT-5.2 with a schema-aware instruction (Appendix A.3) to emit nodes and
edges as structured JSON, together with evidence citations (original sentences from textbooks) or confidence
scores (reflecting model’s confidence in the relation) for every edge. (iv) Per-section graphs are merged
bottom-up: a book-level pass assigns globally unique IDs, deduplicates same-name concepts and skills, and

K12-KGraph 6
| K12-KGraph (subgraph) |                     |     | (A) From K12-KGraph to K12-Bench |               |                        |                                                                  |      |                                                 |                                          |
| --------------------- | ------------------- | --- | -------------------------------- | ------------- | ---------------------- | ---------------------------------------------------------------- | ---- | ----------------------------------------------- | ---------------------------------------- |
|                       | Exercise 1          |     | Task Type                        |               | Candidate Construction |                                                                  |      | Benchmark Item                                  |                                          |
|                       | t e s t s  s k i ll |     | G RO U N D                       | Q u es t io n |   Q :  B e f o r       | e   l e a r n i n g   a b o u t   T r a n s p osing Terms, what  |      |                                                 |                                          |
|                       |                     |     |                                  | Te m p la t   | e                      |                                                                  | F il | t e r Q :   B e f o r e   l e a r n i n g   a b | o u t  T r a n s p o s i n g   T e rms,  |
S o lv i n g   P r a c t i c a l  kn o w l e d g e   s h o u l d   w e  l e a r n   f i r s t ? w h a t   k n o w l e d g e   s h o u l d   w e   l e a r n   f i r s t ?
|     |     | L in e a r   | PR ER E Q |     |     |     |     |     |     |
| --- | --- | ------------ | --------- | --- | --- | --- | --- | --- | --- |
Pro b le m s   u s i n g   L i n e a r   Eq u a ti o n s B a s ic   P r o p e r t i e s   o f   E q u a t io n s 3 -g r a m   ( A ) S o l u t i o n   P r o c e d u r e   f o r   L in e a r   E q u a t i on s
|     | E q u a t i o n s |     | NEIGHBOR |     |     |     | similarity |     |     |
| --- | ----------------- | --- | -------- | --- | --- | --- | ---------- | --- | --- |
(B)Basic Properties of Equations
|     |     |     |     |     | i )   L in e | a r   E q u a t io n s i i )  C o m b i n i n g  L i k e  T erms | L L M | - b a s e d   ( C) C o m b in g  L ik e   T e r m | s   |
| --- | --- | --- | --- | --- | ------------ | ---------------------------------------------------------------- | ----- | ------------------------------------------------- | --- |
prerequisites for prerequisites for EVIDENCE i i i )  S o l u t i on   P r o c e dure f o r   L in e a r   E q u a t io n s pe d a g o g i c al (D ) S o lv in g  P ra c t i ca l  P r oblems usingLinear
Solution Procedure for  iv) Solving Practical Problems using Linear Equations Equations
|     | Linear Equations |     | LOCATE |     |     |     |     |     |     |
| --- | ---------------- | --- | ------ | --- | --- | --- | --- | --- | --- |
is a
is a
|     | Transposing  |     | (B) From K12-KGraph to K12-Train |     |     |     |     |     |     |
| --- | ------------ | --- | -------------------------------- | --- | --- | --- | --- | --- | --- |
Combining
|     | Terms Like Terms |     | QA Type |     |     |     | Answer Synthesis |     |     |
| --- | ---------------- | --- | ------- | --- | --- | --- | ---------------- | --- | --- |
Question Generation
prerequisites for NODE-LEVEL Relations  LLM A: Because transposing terms involves performing the same
prerequisites for Q: Whyis it necessary to master the  o p e r a t i o n  o n   b o t h   s i d e s  o f  a n  e q u a t i o n   t o  k e e p  i t  v a li d ,   a n d   t h e
|     |     |     |     | Selection | basic properties of equations before  |     |     |     |     |
| --- | --- | --- | --- | --------- | ------------------------------------- | --- | --- | --- | --- |
Basic Properties of  Like Terms EDGE-LEVEL learning how to transpose terms? b a si c   p r o p e r t ie s   o f   e q u a t io n s  ju s t i f y   t h e s e  o p e r a ti o n s ,   o n e   s h o uld
Equations learn the properties of equality before learning transposition.
Figure2 AconcreteexampleofK12-BenchandK12-TraingenerationfromK12-KGraph. (A) shows benchmark
construction for a Prereq task via neighborhood sampling and filtering. (B) shows QA synthesis grounded in the
| prerequisites_for |     | relation. |     |     |     |     |     |     |     |
| ----------------- | --- | --------- | --- | --- | --- | --- | --- | --- | --- |
remaps edges; a subject-level pass then reconciles entities across books within the same subject (e.g., “velocity”
appearing in both 8th- and 9th-grade physics). (v) We run depth-first cycle detection on the is_a and
prerequisites_for subgraphs and manually resolve any violations, yielding valid DAGs for the taxonomic
| and | prerequisite | relations. |     |     |     |     |     |     |     |
| --- | ------------ | ---------- | --- | --- | --- | --- | --- | --- | --- |
Quality control. Beyond automated DAG validation, the extraction prompt explicitly discourages hallucina-
tion and restricts outputs to “truly important, clearly presented” knowledge; edges are encouraged to carry a
field and an field linking back to the underlying textbook excerpt; all extracted triples
| confidence |     |     | evidence |     |     |     |     |     |     |
| ---------- | --- | --- | -------- | --- | --- | --- | --- | --- | --- |
are manually verified by domain experts; and hierarchical deduplication uses light-normalized name matching
| followed | by expert        | review | to reconcile |     | cross-book | aliases. |     |     |     |
| -------- | ---------------- | ------ | ------------ | --- | ---------- | -------- | --- | --- | --- |
| 3.3      | Graph Statistics |        |              |     |            |          |     |     |     |
Table 1 and Table 2 summarize the core node and edge types of K12-KGraph across subjects. For clarity
and compactness, we focus on pedagogically salient content nodes (Concept, Skill, Experiment, Exercise,
Figure,VisualElement)togetherwithBook,andomitstructuralcontainernodes(Chapter,Section),which
primarily serve organizational roles. We further omit ubiquitous container relations such as appears_in and
is_part_of. By construction, every content node is anchored to a specific textbook location via appears_in,
and all sections and chapters participate in a fixed hierarchy via is_part_of; their presence is guaranteed by
the schema and therefore carries no information for summarizing graph composition.
| 4   | Benchmark | and | Training |     | Data | from K12-KGraph |     |     |     |
| --- | --------- | --- | -------- | --- | ---- | --------------- | --- | --- | --- |
We derive two KG-grounded datasets from K12-KGraph. K12-Bench (§4.1) converts graph textual neighbor-
hoods into multi-select questions for evaluating LLMs’ curriculum cognition, while K12-Train (§4.2) converts
node attributes and edge semantics into structurally grounded QA pairs for training educational LLMs.
Figure 2 illustrates the shared pipeline on a single prerequisites_for subgraph: panel (A) shows how the
subgraph is instantiated into a Prereq benchmark item, while panel (B) shows how the same relation is
reformulated into a KG-guided QA pair for training. Despite serving different purposes, both resources exploit
the same property: every sample can be traced back to a specific subgraph, making difficulty, coverage, and
| factual | correctness | systematically |     | controllable. |     |     |     |     |     |
| ------- | ----------- | -------------- | --- | ------------- | --- | --- | --- | --- | --- |
| 4.1     | K12-Bench:  | Benchmark      |     | Construction  |     |     |     |     |     |
K12-Benchcomprisesfivetaskfamilies(ninesubtasks)thateachprobeadistinctfacetofstructuralcurriculum
understanding. Alltasksareformulatedasmulti-selectquestions: givenaquestionandfourlabeledcandidates,

K12-KGraph 7
the model must output the full set of correct labels. The gold answer cardinality varies per item from 1
to 3 depending on the query and the local graph neighborhood, so even items with a single correct option
must still be produced in the multi-select output format. Questions and distractors are graph-derived rather
than LLM-generated: for each task we define templates instantiated via graph queries, with correct answers
being the true graph neighbors and distractors sampled from a multi-level pool of structurally proximate
but non-answer nodes (e.g., 2-hop neighborhoods or siblings under shared is_a parents). Detailed distractor
pool construction and sampling rules are provided in Appendix B.1. Models receive only the question text
without any graph context, so the benchmark probes parametric curriculum knowledge. Each candidate set
is filtered by a character 3-gram cosine-similarity step that removes surface-form near-duplicates, followed
by a GPT-5.2-based pedagogical filter that discards distractors synonymous with any correct answer (see
Appendix B.1 for details).
We name the five task families Ground, Prereq, Neighbor, Evidence, and Locate after the relation
they probe.
Ground: Knowledge Grounding (tests_concept, tests_skill). Subtask 1: given an exercise stem, select
the core concepts or skills it tests. Subtask 2: given a concept or skill, select which exercises assess it.
Distractors are drawn from structurally related concepts/skills within the same curriculum context.
Prereq: Prerequisite Reasoning (prerequisites_for). Subtask 1: given a concept/skill, select its pre-
requisite closure. Subtask 2: given a concept/skill, select all of its most direct successors. Distractors are
sampled from structurally adjacent nodes, including related concepts and taxonomic siblings.
Neighbor: Neighbor Recommendation (is_a, relates_to). Given a concept, select all directly related
concepts (via is_a or relates_to in either direction). Distractors are drawn from structurally nearby but
non-neighbor concepts, primarily from the 2-hop outer ring.
Evidence: Experiment Evidence Chain (verifies). Subtask 1: given a concept, select which experiments
verify it. Subtask 2: given an experiment, select which concepts it verifies. Distractors are sampled from
structurally related concepts or experiments.
Locate: Cross-Chapter Indexing (appears_in, leads_to). Subtask 1: given a knowledge entity, select
the chapter(s) where it first appears. Subtask 2: given a chapter, select which chapters are its prerequisites.
Distractors are drawn from alternative structural locations within the curriculum.
Benchmark statistics and quality. K12-Bench contains 23,640 multi-select items in total, with per-task
breakdown reported in Appendix B.3 (Table 11). Because every item is derived deterministically from
validated K12-KGraph subgraphs rather than generated by an LLM, its factual correctness reduces to
the correctness of the underlying graph. K12-KGraph itself is fully human-verified by 12 subject-qualified
annotators with strong inter-annotator agreement (Fleiss’ κ=0.84 overall; see Appendix D), and a stratified
spot-check of K12-Bench finds 98.4% of sampled items to be fully correct. This pipeline gives K12-Bench
an unusually tight link between benchmark quality and graph quality: improvements to the KG propagate
directly into the benchmark, while failures are localizable to specific graph edges.
4.2 K12-Train: KG-Guided Data Synthesis
K12-Train converts the knowledge graph into supervised fine-tuning data along three complementary paths,
illustrated in Appendix C.1.
(i) Node-grounded QA (LLM-prompted). For each Concept, Skill, Experiment, or Exercise node, we
prompt Qwen3-235B-A22B [29] to generate a question–answer pair grounded in that node’s typed properties:
definitions, formulas, and worked examples for Concept; procedural steps and application scenarios for Skill;
instruments, phenomena, and conclusions for Experiment; and the stem augmented with concise step-by-step
reasoning for Exercise. This yields supervision that teaches the content of a node.

K12-KGraph 8
(ii) Edge-grounded QA (LLM-prompted). For each semantic relation, the prompt is anchored in a specific
question template that forces the answer to articulate the relation itself: “Why does A belong to category
B?” for is_a, “Why must one learn A before B?” for prerequisites_for, “How are A and B related?” for
relates_to, “How does experiment E verify concept C?” for verifies, “How does figure F explain concept
C?” for illustrates, “How does a local visual element V correspond to concept C?” for refers_to, “What
information does a figure F provide for an exercise?” for requires_figure, and “How does figure F provide
visual evidence for an existing relation?” for supports_edge. This yields supervision that teaches the
structure between nodes.
(iii) Exercise-assessment QA (deterministic templates). For tests_concept and tests_skill edges, which
are factually unambiguous, we bypass the LLM and fill deterministic templates directly from the edge. This
guarantees full factual grounding and eliminates any risk that the LLM fabricates or paraphrases the target
relation for the exercise-to-concept/skill subset.
Quality control. To minimize hallucination, we crop each node’s property set to only those fields relevant for
the target QA type and filter edges with confidence below a specified threshold before prompting, preventing
the LLM from drifting into unrelated attributes. Prompts further instruct the model to produce grade-
appropriate language, strictly grounded in the provided attributes, with a structured answer format that
highlights key conclusions. After generation, every QA pair is validated for JSON structure, non-empty fields,
and language consistency.
The final dataset, , contains 7,335 QA pairs and is partitioned by modality according to whether
K12-Train-Full
answering requires visual input. QA pairs that can be answered from textual information alone constitute
, while those that require an accompanying figure or visual element constitute .
K12-Train-Text K12-Train-MM
contains2,267QApairs,selectedfromasubstantiallylargerKG-derivedcandidatepoolthrough
K12-Train-Text
source-balanced random subsampling. Specifically, it includes 450 Exercise examples (with step-by-step
reasoning), 356 tests_concept/tests_skill examples, 695 node-grounded QA pairs (from Concept, Skill,
and Experiment), and 766 relation-grounded QA pairs (from is_a, prerequisites_for, relates_to, and
verifies).
K12-Train-MM
contains5,068QApairs,allofwhicharerelation-groundedQApairs(illustrates,
refers_to, requires_figure, and supports_edge) selected based on the confidence of corresponding edges
(1.0 for illustrates, refers_to, supports_edge, and 0.8 for requires_figure) to meet the corresponding
target size. This balancing controls data quality while mitigating the natural skew in the raw KG-derived pool
(e.g., relatively fewer textbook exercises), and encourages the model to learn uniformly across content and
relational supervision signals. Despite its modest size, we show in Section 5 that these structurally grounded
samples are highly effective for educational SFT.
5 Experiments and Results
We conduct two complementary experiments: (i) open-source and proprietary LLMs on
benchmarking
K12-Bench to assess structural curriculum understanding (§5.2), and (ii) both LLMs and VLMs
fine-tuning
on K12-Train and on other mainstream instruction-tuning datasets, and comparing their performance on
downstream educational tasks to validate the validity of our data (§5.3).
5.1 Experimental Settings
Modelsunderevaluation. ForK12-Bench,weevaluatefiveopen-sourceLLMs(Meta-LLaMA-3-8B-Instruct[7],
GLM-4.7-Flash [5], Ministral-3-14B-Instruct [18], Qwen3-32B [29], Gemma-4-31B-IT [24]) and five proprietary
APIs (GPT-4o, GPT-5-mini, GPT-5.2, Gemini-2.5-Flash, Gemini-3-Flash) in a zero-shot, answer-only setting:
given a question and four labeled options, the model outputs the correct option label(s). We report per-task
exact match (EM; all predicted labels must equal the gold set) and an instance-level (example-based) macro
F1: for each instance we compute precision, recall, and F1 on the predicted and gold option-label sets, and
then average across instances, so every question contributes equally regardless of how many labels it has. This
choice keeps F1 on the same per-instance footing as EM, avoids letting items with larger gold sets dominate a
micro-pooled F1, and matches the average=‘samples’ convention for multi-label classification. Task-level

K12-KGraph 9
Table3 K12-Benchresults(zero-shot,answer-only),reportedin%. EM=exactmatch(per-instanceall-or-nothing,
averaged across instances). F1 is the instance-level (example-based) macro F1: we compute precision/recall/F1 on
eachinstance’soption-labelset,thenaverageacrossinstances. Withineachmodelfamily(open-sourcevs.proprietary),
| the best | Overall score is highlighted | in     | yellow, and the second-best | in green. |          |        |         |
| -------- | ---------------------------- | ------ | --------------------------- | --------- | -------- | ------ | ------- |
|          |                              | Ground | Prereq                      | Neighbor  | Evidence | Locate | Overall |
Model
|     |     | EM  | F1 EM F1 | EM F1 | EM F1 | EM F1 | EM F1 |
| --- | --- | --- | -------- | ----- | ----- | ----- | ----- |
RandomBaseline
|        |       | 6.7 | 36.2 6.7 37.9 | 6.7 41.3 | 6.7 37.7 | 6.7 32.9 | 6.7 36.4 |
| ------ | ----- | --- | ------------- | -------- | -------- | -------- | -------- |
| Random | guess |     |               |          |          |          |          |
OpenSourceModels
Meta-LLaMA-3-8B-Instruct 6.2 54.9 4.3 47.9 3.8 53.4 5.2 55.4 11.5 53.9 7.2 52.6
|     |     | 36.4 | 70.9 13.4 56.6 | 15.2 59.6 | 39.3 72.8 | 48.9 66.3 | 31.7 63.9 |
| --- | --- | ---- | -------------- | --------- | --------- | --------- | --------- |
GLM-4.7-Flash
|     |     | 43.0 | 75.1 18.4 59.4 | 14.5 59.8 | 38.3 73.2 | 59.3 72.2 | 37.5 67.4 |
| --- | --- | ---- | -------------- | --------- | --------- | --------- | --------- |
Ministral-3-14B-Instruct
Qwen3-32B 46.7 77.2 16.9 60.4 14.6 60.3 41.7 75.1 72.1 75.9 42.6 69.5
Gemma-4-31B-IT 50.6 79.0 28.3 62.6 15.0 60.7 43.3 73.9 73.4 73.5 46.4 69.5
ProprietaryModels
|     |     | 30.3 | 70.6 9.3 57.5 | 10.1 57.9 | 32.4 71.8 | 55.6 72.3 | 31.1 65.9 |
| --- | --- | ---- | ------------- | --------- | --------- | --------- | --------- |
GPT-4o
GPT-5-mini 30.4 70.4 9.9 57.6 12.5 59.0 32.9 72.3 55.5 72.8 31.7 66.4
GPT-5.2 50.8 79.2 17.9 59.5 13.1 60.0 41.6 73.9 70.1 71.5 42.8 68.0
|     |     | 58.0 | 75.7 29.7 56.3 | 15.4 56.0 | 47.1 72.0 | 72.8 74.0 | 48.3 66.7 |
| --- | --- | ---- | -------------- | --------- | --------- | --------- | --------- |
Gemini-2.5-Flash
Gemini-3-Flash 63.4 83.3 34.8 58.2 33.4 63.5 47.4 72.4 81.7 82.6 57.1 73.0
scores are the average over instances within that task, and Overall scores are the instance-count-weighted
| average | across tasks. |     |     |     |     |     |     |
| ------- | ------------- | --- | --- | --- | --- | --- | --- |
Ourfine-tuningexperimentsconsistoftwoevaluationsettings. For evaluation,
| Fine-tuning | settings. |     |     |     |     | text-only |     |
| ----------- | --------- | --- | --- | --- | --- | --------- | --- |
we train Qwen3-4B-Base and Llama3.1-8B-Base on K12-Train-Text and eight general instruction-tuning
datasets, with all datasets matched to a budget of approximately 2,300 samples. For evaluation,
multimodal
we fine-tune Qwen3.5-2B-Base on K12-Train-Full, K12-Train-Text, and K12-Train-MM, together with the full
available DataFlow and WizardLM datasets (10,000 and 142,759 samples, respectively).
Text-only SFT protocol. We perform full-parameter SFT on Qwen3-4B-Base [29] and Llama3.1-8B-Base [6]
using K12-Train-Text and eight general-purpose instruction-tuning datasets: OpenHermes-2.5 [25], Infinity-
Instruct [15], UltraChat [4], WizardLM_evol_instruct_V2_196k [20], DataFlow-10K-Instruct [16], LM-
SYS [34], SmolTalk [1], and Tulu-3-SFT [12]. To ensure a fair comparison, we uniformly sample 2,300
examples from each baseline, approximately matching the 2,267 examples in K12-Train-Text. All configura-
tions use identical hyperparameters: learning rate 5×10−6, cosine scheduler with 10% warmup, 3 epochs,
per-device batch size 1 with gradient accumulation of 4, DeepSpeed ZeRO-3, and bf16 precision, implemented
via LLaMA-Factory [35]. For each backbone, we additionally include two reference points that are not
constrained to 2,300 samples: the untuned base and the corresponding official instruct version.
We perform LoRA SFT on Qwen3.5-2B-Base using K12-Train-Text, K12-Train-
| Multimodal | SFT protocol. |     |     |     |     |     |     |
| ---------- | ------------- | --- | --- | --- | --- | --- | --- |
MM, and K12-Train-Full, as well as the full DataFlow and WizardLM datasets containing 10,000 and 142,759
examples, respectively. All configurations use identical hyperparameters: learning rate 1×10−4, cosine
scheduler with 10% warmup, 3 epochs, per-device batch size 4 with gradient accumulation of 2, and bf16
precision, implemented via LLaMA-Factory [35]. We also additionally report the untuned Qwen3.5-2B-Base
| model and | its official instruction-tuned |     | variant as reference | points. |     |     |     |
| --------- | ------------------------------ | --- | -------------------- | ------- | --- | --- | --- |
Text-only fine-tuned models are evaluated on two open-ended educational benchmarks:
| Evaluation | axes. |     |     |     |     |     |     |
| ---------- | ----- | --- | --- | --- | --- | --- | --- |
GaokaoBench [33] and EduEval [21]. For GaokaoBench, we follow the official evaluation protocol for both
objective and subjective questions, using string-matching against the reference answers. For EduEval, we

K12-KGraph 10
Table4 GaokaoBenchscoresafterSFTonQwen3-4B-BaseandLlama3.1-8B-Basewith2,300samplesfrom
eachdataset. “Total” denotes the sum of per-subject scores; “Obj” / “Sub” are overall score rates across objective /
subjective sub-portions. Within each base-model block, the best Overall score per column is highlighted in yellow, and
the second-best in green.
Sci. Hum. Overall
Model Eng. Chi. Phy. Chem. Bio. His. Geo. Pol.
Math Math Total Obj Sub
TrainedonQwen3-4B-Base
Qwen3-4B-Base 37.88 55.20 65.22 76.59 47.34 30.60 30.72 39.80 17.72 44.35 445.42 61.4% 19.9%
Qwen3-4B-Instruct 119.98 103.22 97.32 106.62 72.60 54.45 73.40 88.75 88.38 90.65 895.37 77.7% 77.3%
+OpenHermes 125.04 114.28 117.87 123.75 69.96 69.85 80.11 87.65 86.18 92.15 966.84 79.9% 85.4%
+Infinity 122.92 103.74 119.55 120.90 73.08 73.45 77.97 82.95 86.42 92.75 953.73 80.1% 82.4%
+UltraChat 120.44 110.19 100.32 104.58 69.17 66.00 77.11 81.00 82.78 91.05 902.64 74.6% 79.8%
+WizardLM 124.28 112.52 102.69 112.26 69.17 65.70 78.94 81.95 83.44 91.80 922.75 77.6% 80.6%
+DataFlow 120.93 116.85 122.49 127.92 77.35 70.70 81.79 87.65 85.78 94.45 985.91 81.3% 87.1%
+LMSYS 86.39 85.16 80.58 89.70 57.40 60.80 73.07 78.55 83.86 86.85 782.36 65.1% 68.9%
+SmolTalk 119.72 111.69 117.93 124.92 77.09 68.75 79.07 85.05 85.18 94.20 963.60 78.9% 85.4%
+Tulu 122.89 93.58 117.60 125.91 74.12 74.15 81.25 84.35 84.50 93.30 951.65 80.7% 81.4%
+K12-Train-Text(ours) 122.04 120.18 128.61 132.00 79.73 79.35 80.74 87.40 85.76 94.15 1009.96 81.8% 89.5%
TrainedonLlama3.1-8B-Base
Llama3.1-8B-Base 26.89 16.83 6.60 6.48 16.19 8.05 8.69 18.50 17.18 5.35 130.76 12.7% 9.0%
Llama3.1-8B-Instruct 14.49 28.52 58.35 57.90 40.94 23.85 33.14 52.05 43.92 51.35 404.50 33.0% 36.2%
+OpenHermes 62.88 79.84 51.54 54.39 38.83 39.45 56.93 65.60 65.92 64.80 580.19 35.7% 62.4%
+Infinity 67.50 79.75 48.57 52.38 37.38 41.40 53.13 67.05 61.12 65.05 573.33 37.1% 60.5%
+UltraChat 72.97 83.17 52.02 56.31 32.54 52.40 56.87 64.20 58.24 63.50 592.23 37.3% 62.7%
+WizardLM 89.76 79.78 51.24 52.26 33.59 46.60 54.36 66.40 55.58 63.50 593.08 39.2% 62.8%
+DataFlow 62.46 86.82 47.97 50.91 33.18 40.45 57.29 70.20 67.60 68.15 585.03 32.6% 66.8%
+LMSYS 60.36 40.16 34.32 43.56 24.20 28.70 36.90 48.25 48.22 37.95 402.62 29.1% 38.5%
+SmolTalk 62.02 80.40 44.67 51.87 31.86 34.90 53.45 67.90 65.02 63.55 555.64 34.7% 60.8%
+Tulu 74.73 74.53 56.58 60.15 36.76 40.05 55.53 63.40 62.68 62.55 586.97 38.8% 61.1%
+K12-Train-Text(ours) 76.17 93.39 52.02 60.45 34.63 48.85 59.61 69.80 67.62 62.95 625.49 41.0% 65.2%
report a subset of 18 tasks covering five capability dimensions (Application, Ethics, Memory, Reasoning, and
Understanding). As EduEval employs heterogeneous evaluation protocols across tasks, we restrict to those
with standardized, officially supported scoring to ensure comparability. Multimodal fine-tuned models are
evaluated on three complementary benchmarks. [37] consists of image-bearing multiple-choice
Gaokao-MM
questions from eight Gaokao subjects; following its official protocol, we apply rule-based answer extraction
and report accuracy. For [36], which covers six disciplines and five question formats, we use
MDK12-Bench
the official judge-assisted evaluation pipeline and aggregate scores across question formats and disciplines.
[13] covers five subjects with multiple-choice, fill-in-the-blank, and open-ended questions; following
K12Vista
its official protocol, we use the K12-PEM judge to assess answer correctness and reasoning quality, and report
per-format mean scores and an overall mean score.
5.2 Benchmarking LLMs on K12-Bench
Table 3 presents per-task and overall results across all five K12-Bench task families. In addition to model
results, we report a simple Random guess baseline, which samples uniformly from the 15 non-empty label
subsets of {A,B,C,D}. This baseline provides a lower reference for purely random guessing on multi-select
items; formal EM/F1 definitions and the expectation formulas are in Appendix B.5.
Findings. (1)EvenstrongLLMsstrugglewithcurriculumstructure. Thebestoverallexactmatchisonly57.1%
(Gemini-3-Flash); a strong open-source model (Gemma-4-31B-IT) reaches just 46.4%. In more than half the
questions, models fail to identify the complete correct answer set. Overall F1 peaks at ∼73%, indicating
systematic errors rather than isolated mistakes. Moreover, LLaMA-3-8B-Instruct (EM =7.2%) is essentially
indistinguishable from pure random guessing (EM =6.7%), showing that smaller open-source models have no

K12-KGraph 11
Table 5 EduEval scores after SFT on Qwen3-4B-Base and Llama3.1-8B-Base, organized by capability
dimension(18sub-tasks). Within each base-model block, the best Avg is highlighted in yellow, and the second-best
in green.
Application Ethics Memory Reasoning Understanding
Model Avg.
CDC ES JPS PPS SPS EEJ JES PM SES JKR PFR SCR JR PR SR JU PU SU
TrainedonQwen3-4B-Base
Qwen3-4B-Base 15.7 25.6 35.2 33.0 32.2 41.0 44.0 42.4 39.4 34.0 35.6 51.4 33.2 29.8 34.4 34.1 28.9 42.9 34.51
Qwen3-4B-Instruct 19.2 90.1 74.0 58.0 63.0 65.8 72.4 67.6 64.6 63.5 73.8 75.8 75.4 54.8 70.0 78.4 78.3 78.6 66.30
+OpenHermes 14.8 89.8 74.6 59.8 61.4 65.0 70.8 68.8 68.2 63.0 70.4 75.8 76.2 56.4 69.8 78.5 77.4 80.1 66.01
+Infinity 15.9 91.3 73.4 56.4 62.6 66.6 72.2 67.2 68.4 62.5 72.0 77.4 79.0 56.4 71.4 76.8 76.1 79.3 66.04
+UltraChat 16.4 92.0 74.4 52.2 59.2 64.8 74.2 70.0 67.6 64.0 71.4 80.4 74.8 52.4 68.4 76.4 76.2 79.6 65.44
+WizardLM 16.4 91.1 74.8 59.6 64.4 69.2 74.8 71.6 71.4 66.8 70.2 78.2 75.0 52.0 70.0 76.6 76.1 80.9 66.70
+DataFlow 13.7 92.1 72.2 57.2 61.0 67.6 74.8 72.0 70.4 66.8 69.6 74.2 76.6 51.4 67.6 77.2 78.1 77.8 65.57
+LMSYS 14.2 50.2 72.0 57.0 64.4 68.8 72.8 70.4 69.0 63.5 71.0 75.4 75.0 53.8 67.4 73.4 76.5 77.0 64.68
+SmolTalk 14.6 92.7 73.4 58.8 65.4 69.0 74.8 70.4 70.6 63.7 71.4 76.0 76.0 52.6 67.6 75.1 77.6 80.0 66.10
+Tulu 15.8 93.2 75.4 59.0 64.2 69.2 74.0 70.8 69.4 63.0 71.0 79.0 75.6 52.8 67.0 76.2 77.2 79.5 66.27
+K12-Train-Text(ours) 16.2 93.1 74.4 59.6 60.2 71.8 77.0 73.6 71.6 69.2 70.6 78.4 72.6 57.8 68.2 74.8 77.8 79.0 66.76
TrainedonLlama3.1-8B-Base
Llama3.1-8B-Base 10.7 55.8 24.6 13.2 21.4 25.4 26.4 26.0 23.4 15.2 25.2 40.0 11.2 12.0 19.6 25.0 10.2 21.9 20.98
Llama3.1-8B-Instruct 10.7 83.4 22.6 26.8 25.8 34.0 32.8 34.0 35.6 33.2 22.2 24.4 27.4 26.6 24.0 28.1 31.5 28.4 27.31
+OpenHermes 12.7 80.7 42.4 27.8 34.4 55.6 58.6 60.0 60.6 34.8 34.4 37.8 40.8 29.0 38.4 39.1 43.7 41.3 40.05
+Infinity 16.0 89.6 38.8 23.0 32.0 49.4 56.2 52.8 57.2 27.3 40.2 41.2 38.4 29.0 38.4 37.1 32.3 41.3 37.33
+UltraChat 12.9 89.1 34.8 36.8 25.6 61.6 34.6 33.2 34.6 25.5 33.4 22.8 24.8 27.6 26.8 39.9 34.0 30.8 31.87
+WizardLM 16.4 88.6 41.8 21.8 33.0 56.6 62.2 61.2 63.8 25.8 36.0 39.6 39.4 26.2 33.0 39.8 32.6 38.7 38.58
+DataFlow 9.6 80.4 33.0 25.8 28.4 49.4 48.4 57.2 53.6 34.0 31.0 29.0 35.6 30.6 29.8 31.9 37.1 33.8 34.53
+LMSYS 21.7 74.2 27.0 29.6 27.0 42.0 42.2 40.8 40.8 24.8 22.8 24.2 24.8 26.0 27.8 28.7 27.9 26.3 29.85
+SmolTalk 12.3 60.7 37.0 28.8 29.6 60.4 66.0 64.8 65.8 35.8 34.2 40.6 29.2 28.8 30.6 33.0 36.6 36.4 37.64
+Tulu 9.6 78.7 36.8 26.4 30.0 53.0 58.8 58.8 56.2 36.0 39.4 31.2 43.8 25.2 38.8 39.3 41.2 39.3 37.68
+K12-Train-Text(ours) 12.3 88.3 40.6 27.8 32.6 60.0 67.2 69.6 68.6 34.8 39.8 35.0 40.8 27.6 35.8 40.7 41.4 41.9 40.90
parametric knowledge of curriculum structure at all.
Prereq and Neighbor yield the lowest EM across almost
(2)Prerequisiteandneighbortasksarehardest.
every model, with EM below 35% even for Gemini-3-Flash on both tasks. These tasks require understanding
directed and structural relationships between concepts, capabilities that current LLMs evidently lack.
Knowledge Grounding (Ground) and Experiment Evidence
(3)GroundandEvidencearerelativelyeasier.
Chain (Evidence) achieve the highest F1 (above 75% on Ground and above 72% on Evidence for top
models), likely because exercise–concept and experiment–concept associations are more explicitly discussed in
pretraining corpora such as textbook solutions and lab handbooks.
5.3 K12-Train for Educational SFT
We first report the text-only fine-tuning results on GaokaoBench and EduEval, followed by the multimodal
results on Gaokao-MM, MDK12-Bench, and K12Vista, and then analyze the sources of K12-Train’s effective-
ness.
5.3.1 Text-OnlyFine-TuningResults
GaokaoBench. Table 4 reports per-subject scores, the summed total across ten subjects, and the objective/-
subjective score rates for both backbones. On Qwen3-4B-Base, K12-Train-Text achieves the highest overall
total (
1009.96
), improving over the strongest baseline DataFlow (985.91) by +24.1, while also reaching the
best objective score rate (81.8%) and subjective score rate (89.5%). On Llama3.1-8B-Base, K12-Train-Text
again obtains the highest total ( ) and the best objective score rate (41.0%), outperforming the strongest
625.49
baseline WizardLM (593.08) by +32.4. Curriculum-structured training thus transfers across distinct model

| K12-KGraph |     |     |     |     |     |     | 12  |
| ---------- | --- | --- | --- | --- | --- | --- | --- |
Table6 Gaokao-MMaccuracy(%)afterSFTonQwen3.5-2B-Basewithfullsamplesfromeachdataset.
Model Math Chinese Physics Chemistry Biology History Geography Politics Overall
TrainedonQwen3.5-2B-Base
| Qwen3.5-2B-Base |     | 23.7 12.5 | 4.6 | 52.2 | 28.6 64.7 | 45.2 51.5 | 32.4 |
| --------------- | --- | --------- | --- | ---- | --------- | --------- | ---- |
Qwen3.5-2B (Instruct) 32.5 12.5 9.8 53.7 52.4 64.7 46.6 48.5 36.1
| +WizardLM(Full) |     | 38.8 28.1 | 16.7 | 38.8 | 42.9 58.8 | 55.2 48.5 | 39.1 |
| --------------- | --- | --------- | ---- | ---- | --------- | --------- | ---- |
| +DataFlow(Full) |     | 37.5 18.8 | 19.0 | 47.8 | 23.8 64.7 | 34.8 39.4 | 33.3 |
| +K12-Train-Text |     | 30.0 31.2 | 20.4 | 44.8 | 38.1 67.6 | 47.5 51.5 | 38.3 |
| +K12-Train-MM   |     | 38.8 28.1 | 16.7 | 49.3 | 42.9 64.7 | 49.3 39.4 | 38.8 |
|                 |     | 28.7 25.0 | 18.1 | 46.3 | 52.4 67.6 | 50.7 51.5 | 39.9 |
+K12-Train-Full
Table7 MDK12-mediumscoresafterSFTonQwen3.5-2B-Basewithfullsamplesfromeachdataset.
Model Math Physics Chemistry Biology Geography InformationScience Overall
TrainedonQwen3.5-2B-Base
| Qwen3.5-2B-Base |     | 45.83 49.56 | 48.52 | 54.75 | 54.86 | 56.63 | 50.77 |
| --------------- | --- | ----------- | ----- | ----- | ----- | ----- | ----- |
Qwen3.5-2B (Instruct) 48.57 47.99 46.69 57.70 55.41 50.67 50.61
| + WizardLM       | (Full) | 45.40 48.42 | 51.27 | 53.11 | 54.24 | 58.65 | 50.76 |
| ---------------- | ------ | ----------- | ----- | ----- | ----- | ----- | ----- |
| + DataFlow       | (Full) | 52.92 47.19 | 50.04 | 53.37 | 59.70 | 44.88 | 51.28 |
| + K12-Train-Text |        | 49.68 51.37 | 52.77 | 53.90 | 53.37 | 50.19 | 51.55 |
| + K12-Train-MM   |        | 47.47 49.57 | 53.59 | 56.65 | 54.48 | 58.60 | 52.33 |
|                  |        | 49.84 53.24 | 51.37 | 57.92 | 54.55 | 53.68 | 52.94 |
+K12-Train-Full
| families rather | than | being confined | to a single backbone. |     |     |     |     |
| --------------- | ---- | -------------- | --------------------- | --- | --- | --- | --- |
Table5presentsthe18sub-taskscoresgroupedintofivecapabilitydimensions(Application,Ethics,
EduEval.
Memory, Reasoning, Understanding) for both backbones. On Qwen3-4B-Base, K12-Train-Text achieves the
best average score ( ) among all 2,300-sample SFT configurations, surpassing the strongest baseline
66.76
WizardLM (66.70) while delivering the strongest Ethics results overall. On Llama3.1-8B-Base, K12-Train-Text
again reaches the best average score ( 40.90 ), ahead of OpenHermes (40.05) by nearly one point, a non-trivial
gapgivenidenticaltrainingbudget. AlthoughtheoverallgainsaresmallerthanonGaokaoBench, theyremain
consistent across both base models under the same 2,300-sample budget, demonstrating robust improvements
across backbones.
5.3.2 MultimodalFine-TuningResults
Gaokao-MM. Table 6 evaluates multimodal educational reasoning across eight high-school subjects. K12-
Train-Full achieves the highest overall accuracy ( ) among all evaluated configurations, exceeding
39.9%
Qwen3.5-2B-Base and Qwen3.5-2B (Instruct) by 7.5% and 3.8%, respectively. Relative to the base model,
K12-Train-Full improves performance in six of the eight subjects and matches it in another, with gains
spanning both STEM and humanities disciplines. Its overall advantage is therefore broadly distributed
rather than being driven by a single subject. Moreover, K12-Train-Full also surpasses K12-Train-Text and
K12-Train-MM, providing initial evidence that textual curriculum supervision and multimodal grounding
| offer complementary |     | benefits. |     |     |     |     |     |
| ------------------- | --- | --------- | --- | --- | --- | --- | --- |
MDK12-Bench. Table 7 further evaluates multimodal educational reasoning across six science-oriented
subjects. K12-Train-Full again achieves the highest overall score ( ), surpassing Qwen3.5-2B-Base and
52.94
Qwen3.5-2B(Instruct)by2.17and2.33points,respectively,andoutperformingthestrongestnon-K12baseline,
DataFlow, by 1.66 points. Compared with the base model, it improves four of the six subject scores and
achieves the best results among all configurations in Physics and Biology. It also exceeds K12-Train-Text and

K12-KGraph 13
Table8 K12VistascoresafterSFTonQwen3.5-2B-Basewithfullsamplesfromeachdataset.
Overall
Model Math Physics Chemistry Biology Geography
Choice Blank QA Average
TrainedonQwen3.5-2B-Base
Qwen3.5-2B-Base 81.18 79.24 80.41 79.48 77.64 83.65 76.19 79.09 79.72
Qwen3.5-2B (Instruct) 82.19 79.11 78.10 76.87 72.64 82.48 75.31 76.54 78.20
+ WizardLM (Full) 72.57 68.38 65.53 63.99 61.90 74.65 60.64 65.41 67.06
+ DataFlow (Full) 71.80 77.12 70.70 76.17 67.75 77.64 66.77 67.21 72.87
+ K12-Train-Text 69.77 76.59 67.70 76.64 65.58 77.32 62.85 64.42 71.13
+ K12-Train-MM 78.19 73.80 74.04 71.97 69.74 80.92 69.12 71.44 73.97
+K12-Train-Full 82.73 79.50 80.31 78.91 76.97 83.84 76.22 79.56 79.95
K12-Train-MM by 1.39 and 0.61 points, respectively, suggesting that the benefit of combining textual and
multimodal supervision is not specific to Gaokao-MM.
K12Vista. Table 8 provides a particularly rigorous test of capability retention, as the untuned Qwen3.5-2B-
Base already achieves a strong average score of 79.72. K12-Train-Full is the only fine-tuned configuration
that improves upon the base model, reaching the best average score of . Moreover, it achieves the best
79.95
results across all three question formats—multiple-choice, fill-in-the-blank, and open-ended QA—showing
that its advantage is not restricted to a particular response type. Its large gains over K12-Train-Text and
K12-Train-MM further indicate that combining the two supervision sources is critical for preserving the base
model’s strong capabilities while improving its multimodal educational reasoning.
5.3.3 Analysis
Why does K12-Train work? We hypothesize that the advantage of K12-Train stems from two properties
of KG-guided synthesis. First, structural grounding: each QA pair encodes not just a fact but an explicit
relationship (prerequisite, taxonomy, association, verification). Second, pedagogical coherence: because
the KG mirrors the official curriculum, the training distribution aligns with what educational benchmarks
implicitly assume. Consistent with this, K12-Train’s largest gains appear on open-ended GaokaoBench
questions, EduEval’s Ethics dimension (both of which demand structured reasoning rather than isolated
recall), and K12Vista’s open-ended QAs.
A further piece of evidence comes from cross-subject transfer. Although K12-Train is synthesized exclusively
from the mathematics, physics, chemistry, and biology subgraphs, SFT on K12-Train also attains the highest
Chinese score (120.18, +3.33 over the strongest baseline DataFlow) and the best Humanities Math score
(132.00, +4.08 over DataFlow), and matches the top tier on History, Geography, and Politics (Table 4). Since
these subjects receive no in-domain supervision from K12-Train, the improvement cannot be attributed to
content memorization and instead reflects the acquisition of a transferable, structurally-grounded answer style,
supporting our claim that K12-Train teaches curriculum cognition itself.
Complementarity of textual and multimodal supervision. K12-Train-Full achieves the best overall result on
all three multimodal benchmarks and consistently outperforms both Text Only and MM Only, indicating
that the two supervision sources are complementary. Text-only QA strengthens curriculum knowledge and
relation-levelreasoning, whilemultimodalQAgroundsthesecapabilitiesinfiguresanddiagrams. Thispattern
isconsistentwithpriorfindingsthattext-onlyinstructiondatacantransferreasoningandinstruction-following
capabilities to vision-language tasks [10, 17, 26].

K12-KGraph 14
6 Conclusion
We introduced K12-KGraph, a curriculum-aligned knowledge graph built from official Chinese K–12 text-
books, together with K12-Bench (for evaluating curriculum cognition) and K12-Train (for KG-guided SFT).
Experiments show that (1) current LLMs lack robust curriculum cognition despite strong factual recall (46%
EM for a strong open-source model on K12-Bench); (2) KG-guided synthesis is remarkably sample-efficient
across both textual and multimodal settings: under a matched budget of approximately 2,300 samples,
K12-Train-Text outperforms equally sized subsets of eight mainstream SFT corpora on GaokaoBench and
EduEval, while K12-Train-Full outperforms substantially larger general-purpose datasets on three multi-
modal educational benchmarks; and (3) textual and visual supervision are complementary: K12-Train-Full
consistently outperforms both K12-Train-Text and K12-Train-MM across the three multimodal educational
benchmarks. Together, these results highlight the potential of curriculum-grounded data for building more
capable educational language and vision-language models.

K12-KGraph 15
References
[1] Loubna Ben Allal, Anton Lozhkov, Elie Bakouch, Gabriel Martín Blázquez, Guilherme Penedo, Lewis Tunstall,
AndrésMarafioti,HynekKydlíček,AgustínPiqueresLajarín,VaibhavSrivastav,etal. Smollm2: Whensmolgoes
big–data-centric training of a small language model. arXiv preprint arXiv:2502.02737, 2025.
[2] Hamed Babaei Giglou, Jennifer D’Souza, and Sören Auer. Llms4ol: Large language models for ontology learning.
| In International |     | semantic | web conference, |     | pages 408–427. | Springer, | 2023. |     |
| ---------------- | --- | -------- | --------------- | --- | -------------- | --------- | ----- | --- |
[3] Penghe Chen, Yu Lu, Vincent W Zheng, and Yang Pian. Prerequisite-driven deep knowledge tracing. In 2018
| IEEE international |     | conference | on  | data mining | (ICDM), | pages 39–48. | IEEE, | 2018. |
| ------------------ | --- | ---------- | --- | ----------- | ------- | ------------ | ----- | ----- |
[4] Ning Ding, Yulin Chen, Bokai Xu, Yujia Qin, Shengding Hu, Zhiyuan Liu, Maosong Sun, and Bowen Zhou.
Enhancing chat language models by scaling high-quality instructional conversations. In Proceedings of the 2023
Conference on Empirical Methods in Natural Language Processing, pages 3029–3051, 2023.
[5] Team Glm, Aohan Zeng, Bin Xu, Bowen Wang, Chenhui Zhang, Da Yin, Dan Zhang, Diego Rojas, Guanyu Feng,
Hanlin Zhao, et al. Chatglm: A family of large language models from glm-130b to glm-4 all tools. arXiv preprint
| arXiv:2406.12793, |     | 2024. |     |     |     |     |     |     |
| ----------------- | --- | ----- | --- | --- | --- | --- | --- | --- |
[6] Aaron Grattafiori, Abhimanyu Dubey, Abhinav Jauhri, Abhinav Pandey, Abhishek Kadian, Ahmad Al-Dahle,
Aiesha Letman, Akhil Mathur, Alan Schelten, Alex Vaughan, et al. The llama 3 herd of models. arXiv preprint
| arXiv:2407.21783, |     | 2024. |     |     |     |     |     |     |
| ----------------- | --- | ----- | --- | --- | --- | --- | --- | --- |
[7] Aaron Grattafiori, Abhimanyu Dubey, Abhinav Jauhri, Abhinav Pandey, Abhishek Kadian, Ahmad Al-Dahle,
Aiesha Letman, Akhil Mathur, Alan Schelten, Alex Vaughan, et al. The llama 3 herd of models. arXiv preprint
| arXiv:2407.21783, |     | 2024. |     |     |     |     |     |     |
| ----------------- | --- | ----- | --- | --- | --- | --- | --- | --- |
[8] Jinchang Hou, Chang Ao, Haihong Wu, Xiangtao Kong, Zhigang Zheng, Daijia Tang, Chengming Li, Xiping Hu,
Ruifeng Xu, Shiwen Ni, et al. E-eval: A comprehensive chinese k-12 education evaluation benchmark for large
language models. In Findings of the Association for Computational Linguistics: ACL 2024, pages 7753–7774,
2024.
[9] Yuzhen Huang, Yuzhuo Bai, Zhihao Zhu, Junlei Zhang, Jinghan Zhang, Tangjun Su, Junteng Liu, Chuancheng
Lv, Yikai Zhang, Yao Fu, et al. C-eval: A multi-level multi-discipline chinese evaluation suite for foundation
| models. Advances |     | in neural | information | processing |     | systems, 36:62991–63010, |     | 2023. |
| ---------------- | --- | --------- | ----------- | ---------- | --- | ------------------------ | --- | ----- |
[10] Yiming Jia, Jiachen Li, Xiang Yue, Bo Li, Ping Nie, Kai Zou, and Wenhu Chen. Visualwebinstruct: Scaling up
multimodal instruction data through web search. In Proceedings of the 2025 Conference on Empirical Methods
| in Natural | Language | Processing, |     | pages 1373–1393, | 2025. |     |     |     |
| ---------- | -------- | ----------- | --- | ---------------- | ----- | --- | --- | --- |
[11] Enkelejda Kasneci, Kathrin Seßler, Stefan Küchemann, Maria Bannert, Daryna Dementieva, Frank Fischer, Urs
Gasser, Georg Groh, Stephan Günnemann, Eyke Hüllermeier, et al. Chatgpt for good? on opportunities and
challenges of large language models for education. Learning and individual differences, 103:102274, 2023.
[12] Nathan Lambert, Jacob Morrison, Valentina Pyatkin, Shengyi Huang, Hamish Ivison, Faeze Brahman, Lester
James V Miranda, Alisa Liu, Nouha Dziri, Shane Lyu, et al. Tulu 3: Pushing frontiers in open language model
| post-training. | arXiv | preprint | arXiv:2411.15124, |     | 2024. |     |     |     |
| -------------- | ----- | -------- | ----------------- | --- | ----- | --- | --- | --- |
[13] ChongLi,ChenglinZhu,TaoZhang,MinganLin,ZenanZhou,andJianXie. K12vista: Exploringtheboundaries
| of mllms in | k-12 | education. | arXiv | preprint | arXiv:2506.01676, | 2025. |     |     |
| ----------- | ---- | ---------- | ----- | -------- | ----------------- | ----- | --- | --- |
[14] Haonan Li, Yixuan Zhang, Fajri Koto, Yifei Yang, Hai Zhao, Yeyun Gong, Nan Duan, and Timothy Baldwin.
Cmmlu: Measuring massive multitask language understanding in chinese. In Findings of the Association for
| Computational | Linguistics: |     | ACL | 2024, pages | 11260–11285, | 2024. |     |     |
| ------------- | ------------ | --- | --- | ----------- | ------------ | ----- | --- | --- |
[15] Jijie Li, Li Du, Hanyu Zhao, Bo-wen Zhang, Liangdong Wang, Boyan Gao, Guang Liu, and Yonghua Lin. Infinity
instruct: Scalinginstructionselectionandsynthesistoenhancelanguagemodels. arXivpreprintarXiv:2506.11116,
2025.
[16] Hao Liang, Xiaochen Ma, Zhou Liu, Zhen Hao Wong, Zhengyang Zhao, Zimo Meng, Runming He, Chengyu Shen,
Qifeng Cai, Zhaoyang Han, et al. Dataflow: An llm-driven framework for unified data preparation and workflow
| automation | in the | era of | data-centric | ai. arXiv | preprint | arXiv:2512.16676, |     | 2025. |
| ---------- | ------ | ------ | ------------ | --------- | -------- | ----------------- | --- | ----- |

K12-KGraph 16
[17] Ji Lin, Hongxu Yin, Wei Ping, Pavlo Molchanov, Mohammad Shoeybi, and Song Han. Vila: On pre-training for
visuallanguagemodels. InProceedingsoftheIEEE/CVFconferenceoncomputervisionandpatternrecognition,
| pages 26689–26699, | 2024. |     |     |     |
| ------------------ | ----- | --- | --- | --- |
[18] AlexanderHLiu,KartikKhandelwal,SandeepSubramanian,VictorJouault,AbhinavRastogi,AdrienSadé,Alan
Jeffares,AlbertJiang,AlexandreCahill,AlexandreGavaudan,etal. Ministral3. arXivpreprintarXiv:2601.08584,
2026.
[19] Qi Liu, Zhenya Huang, Yu Yin, Enhong Chen, Hui Xiong, Yu Su, and Guoping Hu. Ekt: Exercise-aware
knowledge tracing for student performance prediction. IEEE Transactions on Knowledge and Data Engineering,
| 33(1):100–115, | 2019. |     |     |     |
| -------------- | ----- | --- | --- | --- |
[20] Ziyang Luo, Can Xu, Pu Zhao, Qingfeng Sun, Xiubo Geng, Wenxiang Hu, Chongyang Tao, Jing Ma, Qingwei
Lin, and Daxin Jiang. Wizardcoder: Empowering code large language models with evol-instruct. arXiv preprint
| arXiv:2306.08568, | 2023. |     |     |     |
| ----------------- | ----- | --- | --- | --- |
[21] Guoqing Ma, Jia Zhu, Hanghui Guo, Weijie Shi, Yue Cui, Jiawei Shen, Zilong Li, and Yidan Liang. Edueval:
A hierarchical cognitive benchmark for evaluating large language models in chinese education. arXiv preprint
| arXiv:2512.00290, | 2025. |     |     |     |
| ----------------- | ----- | --- | --- | --- |
[22] Junbo Niu, Zheng Liu, Zhuangcheng Gu, Bin Wang, Linke Ouyang, Zhiyuan Zhao, Tao Chu, Tianyao He, Fan
Wu, Qintong Zhang, et al. Mineru2. 5: A decoupled vision-language model for efficient high-resolution document
parsing. In The 64th Annual Meeting of the Association for Computational Linguistics–Industry Track, 2025.
[23] LongOuyang,JeffreyWu,XuJiang,DiogoAlmeida,CarrollWainwright,PamelaMishkin,ChongZhang,Sandhini
Agarwal, Katarina Slama, Alex Ray, et al. Training language models to follow instructions with human feedback.
| Advances | in neural information | processing | systems, 35:27730–27744, | 2022. |
| -------- | --------------------- | ---------- | ------------------------ | ----- |
[24] Gemma Team, Thomas Mesnard, Cassidy Hardin, Robert Dadashi, Surya Bhupatiraju, Shreya Pathak, Laurent
Sifre, Morgane Rivière, Mihir Sanjay Kale, Juliette Love, et al. Gemma: Open models based on gemini research
| and technology. | arXiv preprint | arXiv:2403.08295, | 2024. |     |
| --------------- | -------------- | ----------------- | ----- | --- |
[25] Teknium. Openhermes 2.5: An open dataset of synthetic data for generalist llm assistants, 2023. URL https:
//huggingface.co/datasets/teknium/OpenHermes-2.5.
[26] Jianhong Tu, Zhuohao Ni, Nicholas Crispino, Zihao Yu, Michael Bendersky, Beliz Gunel, Ruoxi Jia, Xin Liu,
Lingjuan Lyu, Dawn Song, et al. Mlan: Language-based instruction tuning preserves and transfers knowledge
in multimodal language models. In Proceedings of the 3rd Workshop on Towards Knowledgeable Foundation
| Models | (KnowFM), pages | 59–74, 2025. |     |     |
| ------ | --------------- | ------------ | --- | --- |
[27] Yizhong Wang, Yeganeh Kordi, Swaroop Mishra, Alisa Liu, Noah A Smith, Daniel Khashabi, and Hannaneh
Hajishirzi. Self-instruct: Aligning language models with self-generated instructions. In Proceedings of the 61st
annualmeetingoftheassociationforcomputationallinguistics(volume1: longpapers),pages13484–13508,2023.
[28] Xiang Wei, Xingyu Cui, Ning Cheng, Xiaobin Wang, Xin Zhang, Shen Huang, Pengjun Xie, Jinan Xu, Yufeng
Chen, Meishan Zhang, et al. Chatie: Zero-shot information extraction via chatting with chatgpt. arXiv preprint
| arXiv:2302.10205, | 2023. |     |     |     |
| ----------------- | ----- | --- | --- | --- |
[29] An Yang, Anfeng Li, Baosong Yang, Beichen Zhang, Binyuan Hui, Bo Zheng, Bowen Yu, Chang Gao, Chengen
Huang, Chenxu Lv, et al. Qwen3 technical report. arXiv preprint arXiv:2505.09388, 2025.
[30] YuqingYe,XuanZhou,ZhifuChen,DandanLi,HengnianGu,JinPengZhou,andDongdaiZhou. K-12edubench:
Abenchmarkforevaluatinglargelanguagemodels’knowledge, problem-solving,andeducationalgoalcognitionin
k-12 education. In Proceedings of the AAAI Conference on Artificial Intelligence, volume 40, pages 34459–34466,
2026.
[31] WeihaoYou,PengchengWang,ChanglongLi,ZhilongJi,andJinfengBai. Ck12: aroundedk12knowledgegraph
based benchmark for chinese holistic cognition evaluation. In Proceedings of the AAAI Conference on Artificial
| Intelligence, | volume 38, pages | 19431–19439, | 2024. |     |
| ------------- | ---------------- | ------------ | ----- | --- |
[32] Peitian Zhang, Shitao Xiao, Zheng Liu, Zhicheng Dou, and Jian-Yun Nie. Retrieve anything to augment large
| language | models. arXiv preprint | arXiv:2310.07554, | 2023. |     |
| -------- | ---------------------- | ----------------- | ----- | --- |
[33] Xiaotian Zhang, Chunyang Li, Yi Zong, Zhengyu Ying, Liang He, and Xipeng Qiu. Evaluating the performance
of large language models on gaokao benchmark. arXiv preprint arXiv:2305.12474, 2023.

K12-KGraph 17
[34] LianminZheng,Wei-LinChiang,YingSheng,TianleLi,SiyuanZhuang,ZhanghaoWu,YonghaoZhuang,Zhuohan
Li, Zi Lin, Eric P Xing, et al. Lmsys-chat-1m: A large-scale real-world llm conversation dataset. arXiv preprint
| arXiv:2309.11998, | 2023. |     |     |
| ----------------- | ----- | --- | --- |
[35] Yaowei Zheng, Richong Zhang, Junhao Zhang, Yanhan Ye, and Zheyan Luo. Llamafactory: Unified efficient fine-
tuningof100+languagemodels. InProceedingsofthe62ndannualmeetingoftheassociationforcomputational
| linguistics (volume | 3: system demonstrations), | pages 400–410, | 2024. |
| ------------------- | -------------------------- | -------------- | ----- |
[36] Pengfei Zhou, Xiaopeng Peng, Fanrui Zhang, Zhaopan Xu, Jiaxin Ai, Yansheng Qiu, Wangbo Zhao, Jiajun Song,
Chuanhao Li, Weidong Tang, et al. Mdk12-bench: a multi-discipline benchmark for evaluating reasoning in
multimodal large language models. In Proceedings of the AAAI Conference on Artificial Intelligence, volume 40,
| pages 28982–28990, | 2026. |     |     |
| ------------------ | ----- | --- | --- |
[37] Yi Zong and Xipeng Qiu. Gaokao-mm: A chinese human-level benchmark for multimodal models evaluation. In
Findings of the Association for Computational Linguistics: ACL 2024, pages 8817–8825, 2024.

K12-KGraph 18
Table9 K12-KGraphschema: nine node types and fourteen relation types with allowed source→target connections.
| Category | Type            |     |     | Description                             |     |     |     |
| -------- | --------------- | --- | --- | --------------------------------------- | --- | --- | --- |
|          | Book            |     |     | Textbookentity(subject,grade,publisher) |     |     |     |
|          | Chapter         |     |     | Chapterwithtitleandordering             |     |     |     |
|          | Section         |     |     | Sectionwithtitleandordering             |     |     |     |
|          | Concept(Cpt)    |     |     | Coreknowledgeconceptwithdefinition      |     |     |     |
| Nodes    | Skill(Skl)      |     |     | Transferablemethodortechnique           |     |     |     |
|          | Experiment(Exp) |     |     | Laboratoryexperimentwithinstruments     |     |     |     |
|          | Exercise(Exe)   |     |     | Practiceproblemwithstemandanswer        |     |     |     |
|          | Figure(Fig)     |     |     | Singlepictureinatextbook                |     |     |     |
VisualElement(Vis_Ele) Localvisualelementsinafigurethathaveeducationalvalue
|     | is_a |     |     | Taxonomicsubsumption(Concept→Concept) |     |     |     |
| --- | ---- | --- | --- | ------------------------------------- | --- | --- | --- |
prerequisites_for(prereq) Learningdependency(Concept/Skill→Concept/Skill/Experiment)
|     | relates_to(rel_to)      |     |     | Semanticassociation(Concept→Concept)       |     |     |     |
| --- | ----------------------- | --- | --- | ------------------------------------------ | --- | --- | --- |
|     | verifies(verif)         |     |     | Experimentalvalidation(Experiment→Concept) |     |     |     |
|     | tests_concept(tes_cpt)  |     |     | Exerciseassessesconcept(Exercise→Concept)  |     |     |     |
|     | tests_skill(tes_skl)    |     |     | Exerciseassessesskill(Exercise→Skill)      |     |     |     |
|     | contains_visual_element |     |     | Figurecomposition(Figure→VisualElement)    |     |     |     |
Edges
illustrates Figure-levelknowledgegrounding(Figure→Concept/Skill/Experiment)
refers_to Element-levelknowledgegrounding(VisualElement→Concept/Skill/Experiment)
|     | requires_figure |     |     | Visualdependency(Exercise→Figure)             |     |     |     |
| --- | --------------- | --- | --- | --------------------------------------------- | --- | --- | --- |
|     | supports_edge   |     |     | Visualevidencefortextualrelation(Figure→Edge) |     |     |     |
appears_in Knowledgelocatedinsection(Concept/Skill/Experiment/Figures→Section)
leads_to(lea_to) Chapter-levelnecessarylearningorder(Chapter→Chapter)
|          | is_part_of     |     |         | Chapterhierarchy(Section→Chapter,Chapter→Book) |     |     |             |
| -------- | -------------- | --- | ------- | ---------------------------------------------- | --- | --- | ----------- |
|          |                |     | Table10 | Node-levelattributeschemainK12-KGraph.         |     |     |             |
| NodeType | RequiredFields |     |         | OptionalFields                                 |     |     | Constraints |
Concept id,name,definition,importance examples,aliases,formula,unit importance∈{understand,master,important}
Skill id,name,description examples mustbegeneralizable(notexercise-specific)
|     | id,name,instruments,is_student |     |     | process,phenomena,conclusion |     |     | is_student∈{0,1} |
| --- | ------------------------------ | --- | --- | ---------------------------- | --- | --- | ---------------- |
Experiment
Exercise id,stem,answer,difficulty,type analysis difficulty∈[1,5],mustlinktoConcept/Skill
Figure id,name,img_path,description,textual_evidence role,role_rationale roleisoneofsixpedagogicalfunctionswhenannotated
id,name,description,source_figure text_on_img,bbox_2d,bbox_conf,bbox_rationale bboxusesnormalized[ymin,xmin,ymax,xmax]∈[0,1000]4
VisualElement
Appendix
| A K12-KGraph |     | Construction |           | Details       |     |     |     |
| ------------ | --- | ------------ | --------- | ------------- | --- | --- | --- |
| A.1 Node     | and | Edge         | Attribute | Specification |     |     |     |
Table9definesthehigh-levelontologyofK12-KGraph(ninenodetypesandfourteenedgetypes),andTable10
| summarizes | the detailed | attribute |     | specifications | for each node | type. |     |
| ---------- | ------------ | --------- | --- | -------------- | ------------- | ----- | --- |
All textual node attributes must be explicitly supported by the source textbook content.
Global Constraints.
Attributes should not introduce information beyond the provided text, and any extracted field must be
verifiable from the corresponding source passage. For visual nodes, description and localization attributes
must be supported by visible image content, while must quote the aligned textbook text
textual_evidence
verbatim. Every model-inferred visual relation includes a rationale and confidence score.
| A.2 Source | Documents |     | and | Preprocessing | Setup |     |     |
| ---------- | --------- | --- | --- | ------------- | ----- | --- | --- |
K12-KGraph is constructed from official textbook PDFs from the People’s Education Press (PEP) curriculum,
covering mathematics, physics, chemistry, and biology across primary, middle, and high school levels. The
| source | files are obtained | from | public | repository1. |     |     |     |
| ------ | ------------------ | ---- | ------ | ------------ | --- | --- | --- |
1https://github.com/TapXWorld/ChinaTextbook

K12-KGraph 19
|     | SINGLE-TURN |     | USER | PROMPT |     | FOR TEXTUAL |     | K12-KGRAPH | EXTRACTION |
| --- | ----------- | --- | ---- | ------ | --- | ----------- | --- | ---------- | ---------- |
You are a knowledge graph expert proficient in K–12 textbook research and development, skilled at
|     | extracting | structured |     | knowledge | from | textbook texts. |     |     |     |
| --- | ---------- | ---------- | --- | --------- | ---- | --------------- | --- | --- | --- |
Your task is to: read the provided , extract nodes and edges according to the
textbooksectiontext
|     | specified |     |     | , and | output | the JSON | result. |     |     |
| --- | --------- | --- | --- | ----- | ------ | -------- | ------- | --- | --- |
SchemaDefinition
Requirements:
• This task primarily focuses on building concepts/skills and the relationships between them .
Exercises are optional or only a few are required; quality over quantity is preferable.
• Extract the truly important and clearly presented concepts/methods from this section of the
|     | textbook. | Do  | not | create content |     | or include trivial | details. |     |     |
| --- | --------- | --- | --- | -------------- | --- | ------------------ | -------- | --- | --- |
• Skills should be generalizableandapplicable within the subject, not specific problem-solving
|     | techniques | used | in  | a particular | question. |     |     |     |     |
| --- | ---------- | ---- | --- | ------------ | --------- | --- | --- | --- | --- |
• For each edge, if there are supporting sentences in the original textbook text, please provide the
|     | original | text. |     |     |     |     |     |     |     |
| --- | -------- | ----- | --- | --- | --- | --- | --- | --- | --- |
OutputFormat:
• Output only a single JSON object. Do not output any explanatory text, comments, or Markdown
|     | code | block markers. |     |     |     |     |     |     |     |
| --- | ---- | -------------- | --- | --- | --- | --- | --- | --- | --- |
InputText:
|     | •   |     | {Section_Markdown_Content} |     |     |     |     |     |     |
| --- | --- | --- | -------------------------- | --- | --- | --- | --- | --- | --- |
Textbooktext:
|     | Now, please | generate |     | the knowledge |     | graph JSON: |     |     |     |
| --- | ----------- | -------- | --- | ------------- | --- | ----------- | --- | --- | --- |
Figure3 SimplifiedprompttemplateforKG(textualcomponent)extraction. The actual extraction prompt
additionally includes the full graph schema definition and JSON output requirements.
For document preprocessing, we directly adopt the official MinerU pipeline and recommended settings to
convert PDFs into structured text. We use the provided CLI interface and default configuration without
| introducing | any    | custom | parsing       | rules | or  | modifications. |     |     |     |
| ----------- | ------ | ------ | ------------- | ----- | --- | -------------- | --- | --- | --- |
| A.3         | Prompt | for    | KG Extraction |       |     |                |     |     |     |
A simplified version of the prompt template used for LLM-based knowledge graph extraction (Stage 3 of the
| pipeline) | is demonstrated |     |     | in Figure | 3.  |     |     |     |     |
| --------- | --------------- | --- | --- | --------- | --- | --- | --- | --- | --- |
In implementation, we construct K12-KGraph in two phases. We first extract the textual component section
by section. The textual extraction template is sent as a single user message without a separate system
prompt, and its full version additionally incorporates the detailed schema definitions in Table 9 and Table 10.
We then construct the multimodal component from the textbook images, their corresponding section text,
and the previously extracted textual graph. This phase proceeds in three steps: (a) image-level analysis
and knowledge-relevance filtering; (b) pedagogical-role classification and visual-element identification; and
(c) visual-element localization and extraction of multimodal relations that link the image to the textual
component.

K12-KGraph 20
| PROMPT | FOR | MULTIMODAL |     | K12-KGRAPH | EXTRACTION | (STEP 1) |
| ------ | --- | ---------- | --- | ---------- | ---------- | -------- |
Systemprompt:
You are a rigorous and conservative multimodal analysis assistant for Chinese textbooks.
You will receive a single image from a textbook and the original textbook text from the section
containing that image. Your task is to combine the visible content of the image with the original
textbook text, extract image-level information, and determine whether the image is worth including in
| the knowledge | graph. |     |     |     |     |     |
| ------------- | ------ | --- | --- | --- | --- | --- |
Outputfields.
1. name: a short Chinese semantic name suitable for this image in the knowledge graph.
2. textual_evidence: the verbatim textbook text most directly related to the image.
3. description: a Chinese description of the overall content directly visible in the image.
4. is_kg_relevant: whether the image is worth including in the knowledge graph; the value must
| be "yes" | or "no". |     |     |     |     |     |
| -------- | -------- | --- | --- | --- | --- | --- |
5. irrelevant_reason: if the image is irrelevant, provide a brief reason in Chinese; otherwise, use
| an empty | string. |     |     |     |     |     |
| -------- | ------- | --- | --- | --- | --- | --- |
Rulesfortextual_evidence.
1. The evidence must come directly from the original textbook text. Rewriting, summarization,
synonym substitution, and independently adding content are strictly prohibited.
2. Prefer the figure caption, excluding a standalone figure number; original body-text sentences
| directly | corresponding |     | to the image | may also | be included. |     |
| -------- | ------------- | --- | ------------ | -------- | ------------ | --- |
3. Oneormorerelatedexcerptsmaybecopiedandconcatenatedintheiroriginalorder. Everyexcerpt
must be verbatim textbook text; do not add words, rewrite content, or reorganize excerpts into a
new sentence that does not occur in the textbook merely to improve coherence.
4. If the textbook contains no text directly related to the image, use an empty string.
Rulesfordescription.
1. Describe only content directly visible in the image. Do not add extracurricular knowledge,
| information | outside |     | the textbook, | or additional | inference. |     |
| ----------- | ------- | --- | ------------- | ------------- | ---------- | --- |
Rulesforis_kg_relevant.
1. Mark the image as if it is merely decoration, a column icon, a layout element, a cover
"no"
background, or has no explicit connection to the instructional content of the section.
2. Mark the image as "yes" if it can be explicitly connected to a concept, skill, experiment, problem
| context, | learning | task, | or textbook | narrative | in the section. |     |
| -------- | -------- | ----- | ----------- | --------- | --------------- | --- |
3. Images that may be marked "yes" include, but are not limited to, conceptual illustrations,
structural diagrams, experiment images, problem-solving aids, real-life context images, problem-
introduction images, observation or discussion materials, positive examples, counterexamples, and
| incorrect | demonstrations. |     |     |     |     |     |
| --------- | --------------- | --- | --- | --- | --- | --- |
4. Mark the image as if it is only broadly related, its specific instructional function cannot be
"no"
determined, and it cannot be stably linked to a knowledge object, problem context, or learning
task.
Output-formatrules.
| 1. Output | JSON | only, | with no additional | explanation. |     |     |
| --------- | ---- | ----- | ------------------ | ------------ | --- | --- |
2. The JSON object must contain the specified fields and no additional fields.
Userprompt:
| Please analyze | this | textbook | image.             |     |     |     |
| -------------- | ---- | -------- | ------------------ | --- | --- | --- |
| •              |      |          | {section_metadata} |     |     |     |
Sectioninformation:

K12-KGraph 21
| •   |     |     | {section_text} |     |     |     |
| --- | --- | --- | -------------- | --- | --- | --- |
Fulloriginaltextofthesection:
| •   |     |     | {figure_hint} |     |     |     |
| --- | --- | --- | ------------- | --- | --- | --- |
Image-structureinformation:
| PROMPT | FOR MULTIMODAL |     | K12-KGRAPH |     | EXTRACTION | (STEP 2) |
| ------ | -------------- | --- | ---------- | --- | ---------- | -------- |
Systemprompt:
You are a rigorous assistant for classifying the instructional functions of Chinese textbook images and
| identifying | visual elements. |     |     |     |     |     |
| ----------- | ---------------- | --- | --- | --- | --- | --- |
You will receive a textbook image that has already been determined to be knowledge-relevant, its
| image-level | analysis, | and six valid |     | values. |     |     |
| ----------- | --------- | ------------- | --- | ------- | --- | --- |
figure_role
| Your tasks | are: |     |     |     |     |     |
| ---------- | ---- | --- | --- | --- | --- | --- |
1. Determine the primary “instructional function” performed by the image in the textbook.
2. Identify visual elements that can genuinely be localized within the image and have instructional
significance.
Rulesforfigure_role.
The valid values are limited to the following six literal labels: explaining a con-
figure_role
cept;introducingareal-lifecontext;demonstratinganexperiment;assistingproblemsolving;summarizing
| and consolidating | knowledge;presenting |     | data. |     |     |     |
| ----------------- | -------------------- | --- | ----- | --- | --- | --- |
Note that is not a classification of the figure’s format, image type, or content topic.
figure_role
If the image is a “structural schematic / knowledge-principle diagram / principle diagram / flowchart
/ schematic,” figure_role should usually be explaining a concept. If it is an “experiment
demonstration / experimental-apparatus diagram / experimental-process diagram,” the role should
usually be demonstrating an experiment. If it is a “statistical chart / table / curve graph / bar
chart,” the role should usually be data. If it is a “problem diagram / geometric diagram
presenting
/ condition diagram,” the role should usually be assisting problem solving.
Rulesforvisual_elements.
Retain only objects, regions, annotations, organs, devices, arrows, curves, text, and other elements
that can genuinely be localized in the image and have instructional significance. Do not name abstract
actions, generalized conclusions, or overall phenomena as visual elements. Each visual element should
| contain | only name, description, |     | and text_on_image; |     | do not output | kind. |
| ------- | ----------------------- | --- | ------------------ | --- | ------------- | ----- |
Outputrequirements.
| 1. Output | JSON only.       |          |                  |        |          |     |
| --------- | ---------------- | -------- | ---------------- | ------ | -------- | --- |
| 2. Do not | output Markdown. |          |                  |        |          |     |
| 3.        | must             | copy one | of the six valid | values | exactly. |     |
figure_role
4. may explain the figure format, but must not use the figure format itself
figure_role_rationale
| as the | figure_role. |     |     |     |     |     |
| ------ | ------------ | --- | --- | --- | --- | --- |
5. The JSON object must contain the specified fields and no additional fields.
Userprompt:
Please analyze the primary instructional figure_role of this textbook image and identify its visual
elements.
| • Sectioninformation: |     | {section_metadata} |                |     |     |     |
| --------------------- | --- | ------------------ | -------------- | --- | --- | --- |
| •                     |     |                    | {section_text} |     |     |     |
Fulloriginaltextofthesection:
| •   |     | {figure_info} |     |     |     |     |
| --- | --- | ------------- | --- | --- | --- | --- |
Imageinformation:

K12-KGraph 22
| PROMPT | FOR | MULTIMODAL |     |     | K12-KGRAPH | EXTRACTION | (STEP 3) |
| ------ | --- | ---------- | --- | --- | ---------- | ---------- | -------- |
Systemprompt:
You are a rigorous and conservative assistant for multimodal knowledge-graph extraction and
| visual-element | localization |     | from | Chinese | textbooks. |     |     |
| -------------- | ------------ | --- | ---- | ------- | ---------- | --- | --- |
You will receive a textbook image already determined to be knowledge-relevant, the original textbook
text from its section, the image-level analysis, the identified visual elements, and candidate nodes and
| edges from  | the existing |     | textual | knowledge | graph         | for that section. |     |
| ----------- | ------------ | --- | ------- | --------- | ------------- | ----------------- | --- |
| Your tasks  | are:         |     |         |           |               |                   |     |
| 1. Generate | a bounding   |     | box     | only for  | each supplied | visual element.   |     |
2. Extract only incremental knowledge-graph relations that are directly supported by the image.
Generalprinciples.
1. Linksmayuseonlythesuppliedcandidate-nodeIDs. DonotinventnewConcept,Skill,Experiment,
| or Exercise | IDs. |     |     |     |     |     |     |
| ----------- | ---- | --- | --- | --- | --- | --- | --- |
2. may select only from the supplied candidate values. Do not invent a
supports_edges edge_ref
new edge_ref.
3. If the image is relevant but cannot be stably linked to any candidate node or edge, return empty
relations.
| 4. When | uncertain, | output | less | rather | than guessing. |     |     |
| ------- | ---------- | ------ | ---- | ------ | -------------- | --- | --- |
Evidencerequirements.
1. Do not add relations using extracurricular common sense, background subject knowledge, comple-
| tion | from textbook |     | context, | or abstract | inference. |     |     |
| ---- | ------------- | --- | -------- | ----------- | ---------- | --- | --- |
2. Only content directly visible in the image, or direct alignment between the image and
textual_-
| evidence, | counts | as  | valid | evidence. |     |     |     |
| --------- | ------ | --- | ----- | --------- | --- | --- | --- |
3. Do not output a relation if it relies primarily on “this is usually true according to common sense”
| rather | than “this | is  | explicitly | shown | in the image.” |     |     |
| ------ | ---------- | --- | ---------- | ----- | -------------- | --- | --- |
Requirementsforillustrates.
Output only when the entire image is directly used to explain a candidate knowledge
illustrates
point. Do not output it when the connection is weak, indirect, or requires a long chain of reasoning.
Requirementsforvisual_elements.
Do not add, delete, or modify any supplied visual element. For each input ve_id, return only its
bounding-boxcoordinates,confidence,briefrationale,andrefers_torelations. Usenormalized0–1000
coordinates in the format ]. If a visual element cannot be stably localized, set
|              |     |         | [y min | ,x min     | ,y max ,x max |     |     |
| ------------ | --- | ------- | ------ | ---------- | ------------- | --- | --- |
| its bounding | box | to null | and    | confidence | to 0.0.       |     |     |
Confidence must be a decimal between 0 and 1 and reflect the strength of the image evidence. A value
of 1.0 means that the evidence in the image is highly direct and explicit and supports the localization
with almost no interpretation; 0.5 means that some supporting evidence exists but a small amount of
alignment or judgment is still required; and 0.0 means that the image provides no valid support. Do
not add visual elements; return results one by one only for the supplied ve_id values.
Requirementsforsupports_edges.
The threshold for is the highest. Output one only when the image can directly
supports_edges
serve as visual evidence for a candidate edge. If the image supports only a node-level concept but
does not directly support the source–target relation expressed by the candidate edge, do not output
supports_edges.
Requirementsforrequired_by_exercises.
The threshold for is extremely high. Output one only when removing the
required_by_exercises
image would make the exercise impossible to understand, make its meaning indeterminate, or prevent

K12-KGraph 23
completion of a key reasoning step. If the image is merely helpful, assists understanding, or makes the
exercise easier, but the exercise can still be completed without it, do not output the relation.
Outputrequirements.
1. Every must explicitly state what visible content in the image supports the relation; do
rationale
| not provide | vague explanations. |     |     |     |     |     |
| ----------- | ------------------- | --- | --- | --- | --- | --- |
2. Relation confidence must be a decimal between 0 and 1 and reflect the strength of the image
evidence. A value of 1.0 means that the evidence is highly direct and explicit and supports the
relation with almost no interpretation; 0.5 means that some supporting evidence exists but a small
amount of alignment or judgment is still required; and 0.0 means that the image provides no valid
support.
| 3. Return | an empty array | for     | any field  | with no      | output content. |     |
| --------- | -------------- | ------- | ---------- | ------------ | --------------- | --- |
| 4. Output | JSON only,     | with no | additional | explanation. |                 |     |
5. The JSON object must contain the specified fields and no additional fields.
Please localize the existing visual elements in this textbook image and extract
| User prompt: |                |                    |           |        |                    |        |
| ------------ | -------------- | ------------------ | --------- | ------ | ------------------ | ------ |
| incremental  | relations that | can                | be linked | to the | existing knowledge | graph. |
| •            |                | {section_metadata} |           |        |                    |        |
Sectioninformation:
| •   |     |     | {section_text} |     |     |     |
| --- | --- | --- | -------------- | --- | --- | --- |
Fulloriginaltextofthesection:
| • Imageinformation: |     | {figure_info} |                        |     |     |     |
| ------------------- | --- | ------------- | ---------------------- | --- | --- | --- |
| •                   |     |               | {visual_elements_json} |     |     |     |
Suppliedvisualelements:
| •   |     | {candidate_nodes} |     |     |     |     |
| --- | --- | ----------------- | --- | --- | --- | --- |
Candidatenodes:
| •   |     | {candidate_edges} |     |     |     |     |
| --- | --- | ----------------- | --- | --- | --- | --- |
Candidateedges:
| • Candidateexercises: |     | {exercise_catalog} |     |     |     |     |
| --------------------- | --- | ------------------ | --- | --- | --- | --- |
Figure4 Simplifiedthree-steppromptsequenceforconstructingthemultimodalcomponentofK12-KGraph.
(a) Step 1 performs image-level analysis and knowledge-relevance filtering. (b) Step 2 identifies the pedagogical role
of each retained figure and extracts its instructional visual elements. (c) Step 3 localizes these visual elements and
| extracts multimodal | relations    | linking    | the figure | to the   | existing textual | component. |
| ------------------- | ------------ | ---------- | ---------- | -------- | ---------------- | ---------- |
| B K12-Bench         | Construction |            | Details    | and      | Evaluation       | Protocol   |
| B.1 Distractor      | Pool and     | Structural |            | Sampling | Rules            |            |
Overview. We construct distractors through a structured, graph-driven pipeline rather than generating them
from an LLM from scratch. For each benchmark instance, the generator first derives the question and gold
answer set from a target relation or graph query, and then samples distractors from a multi-layer pool of
structurally relevant but non-gold nodes. The overall design follows a “near-to-far” principle: candidates are
firstdrawnfromgraph-localneighborhoodsandonlyexpandedtobroadercurriculumcontextswhennecessary,
ensuring both plausibility and difficulty without introducing semantically valid alternatives.
Distractor construction pipeline. For each instance, distractors are constructed in three stages:
1. multi-layer expansion from graph neighborhoods to broader curriculum-based pools;
Candidatepooling:
2. removal of gold answers, surface-form duplicates, and task-invalid candidates;
Rule-basedfiltering:
3. LLM-based filtering to discard weak, trivial, or controversial distractors.
Pedagogicalfiltering:
Candidates are finally deduplicated and stably ordered before option sampling.

K12-KGraph 24
Candidate pool construction. Candidate pools are expanded in layers. Early layers consist of structurally
proximate nodes, while later layers draw from broader curriculum scopes such as the same section, chapter,
book, subject-stage, or subject. Each layer is only used when previous layers are insufficient, and candidates
| already selected | in earlier | layers | are removed. |     |     |     |
| ---------------- | ---------- | ------ | ------------ | --- | --- | --- |
Graph distance is defined over the undirected union of relates_to, is_a, and prerequisites_for. Thus,
references to 1-hop, 2-hop, or 3-hop neighborhoods correspond to distances in this combined structural graph
rather than any single relation type. We also incorporate “sibling” structures induced by shared is_a parents
orsharedprerequisites_fortargets,assuchnodesareoftenpedagogicallyadjacentwhileremainingdistinct
| from the correct | answers. |     |     |     |     |     |
| ---------------- | -------- | --- | --- | --- | --- | --- |
In practice, this layered expansion yields an initial pool of approximately 8–20 raw candidates per instance
prior to filtering, reducing the risk of brittle items with insufficient negative options.
Candidate ranking. Within each layer, candidates are ranked by semantic similarity using BAAI/bge-small-
zh-v1.5 [32]. For each candidate, the final score averages (i) similarity between the candidate text and the
finalized question text, and (ii) the maximum similarity between the candidate text and any gold answer.
Node representations use the name field, while Exercise nodes preferentially use their stem. Candidates are
| sorted within | each layer      | by descending | similarity         | before subsequent | filtering.   |                 |
| ------------- | --------------- | ------------- | ------------------ | ----------------- | ------------ | --------------- |
|               |                 | The           | exact construction | of candidate      | pools varies | by task family: |
| Task-specific | sampling rules. |               |                    |                   |              |                 |
• Ground(exercise→concept/skill): Distractors are seeded from the 2-hop neighborhoods of the correct
answers and expanded to same-section, same-chapter, same-book, subject-stage, and subject-level pools
| with | the same node | type. |     |     |     |     |
| ---- | ------------- | ----- | --- | --- | --- | --- |
• Ground(concept/skill→exercise): The first layer consists of exercises attached to the 2-hop structural
neighborhood of the query node, followed by broader curriculum-based expansions.
• Prereq: Candidate pools are asymmetric by design. For prerequisite queries, early layers emphasize
forward descendants of the query node and the boundary of the gold prerequisite closure. For successor
queries, early layers emphasize the full prerequisite closure and deeper descendants beyond the direct
| gold | successors. |     |     |     |     |     |
| ---- | ----------- | --- | --- | --- | --- | --- |
• Theanswersetconsistsonlyofdirectrelates_toandis_aneighbors. Distractorsaredrawn
Neighbor:
from the immediately outer ring, primarily 2-hop concept nodes and broader same-location concept
pools.
• First-layer distractors are constructed from structurally nearby concepts or experiments
Evidence:
within the 2-hop neighborhood of the query or answer node, and then expanded through the same
| section/chapter/book/stage/subject |     |     | hierarchy. |     |     |     |
| ---------------------------------- | --- | --- | ---------- | --- | --- | --- |
• Locate: For “first appearance” questions, distractors are drawn from alternative locations where the
queried node appears and expanded to nearby sections or chapters. For chapter-level leads_to tasks,
the first layer contains nearby earlier chapters relative to both the query and gold prerequisite chapters,
| with | fallback to broader | chapter | pools when | necessary. |     |     |
| ---- | ------------------- | ------- | ---------- | ---------- | --- | --- |
Final filtering. In addition to removing gold answers and name-level duplicates, task-specific rule filters
exclude candidates that are too closely related to the gold set under the intended task semantics (e.g.,
nodes reachable via short alternative paths or still acceptable under a looser interpretation). The remaining
candidates are then passed to the pedagogical filter described in the next subsection, ensuring that final
| distractors | are both challenging | and | unambiguously | incorrect. |     |     |
| ----------- | -------------------- | --- | ------------- | ---------- | --- | --- |
| B.2 Prompt  | for Pedagogical      |     | Filtering     |            |     |     |
To ensure that distractors are pedagogically valid and unambiguously incorrect, we apply an LLM-based
filtering step after rule-based candidate pruning. The goal of this step is not to improve semantic similarity,
but to remove candidates that are either trivially implausible or potentially acceptable as correct answers
| under a reasonable | educational | interpretation. |     |     |     |     |
| ------------------ | ----------- | --------------- | --- | --- | --- | --- |
Eachcandidateisevaluatedindependently,giventhequestionandthegoldanswerset. Themodelisinstructed
to act as a conservative K–12 teacher and determine whether the candidate is a valid distractor, as shown in
Figure 5.

K12-KGraph 25
| PROMPT |     | FOR FILTERING |     |     | K12-BENCH | CANDIDATE | DISTRACTORS |
| ------ | --- | ------------- | --- | --- | --------- | --------- | ----------- |
SystemPrompt:
| You | are an experienced |     | K–12 | teacher. |     |     |     |
| --- | ------------------ | --- | ---- | -------- | --- | --- | --- |
Your task is to judge whether a candidate option is a for a multiple-choice question.
validdistractor
Criteria.
| A valid | distractor      | must  | satisfy  | all      | of the following: |               |     |
| ------- | --------------- | ----- | -------- | -------- | ----------------- | ------------- | --- |
| •       | It is incorrect | given | the      | question | and the           | gold answers. |     |
| •       | It is           | and   | relevant | (not     | obviously         | unrelated).   |     |
plausible
• It is , not ambiguous, and would not be accepted as correct by a careful
|     | not | partially | correct |     |     |     |     |
| --- | --- | --------- | ------- | --- | --- | --- | --- |
teacher.
Instruction.
• Be conservative: if a candidate could be considered correct under any reasonable interpretation,
|     | mark it as | invalid. |     |     |     |     |     |
| --- | ---------- | -------- | --- | --- | --- | --- | --- |
Outputformat.
| •   | Output exactly | one | label: | VALID | or INVALID. |     |     |
| --- | -------------- | --- | ------ | ----- | ----------- | --- | --- |
UserPrompt:
| •   |     | {question} |     |     |     |     |     |
| --- | --- | ---------- | --- | --- | --- | --- | --- |
Question:
| •   | Goldanswers: | {gold_answers} |             |     |     |     |     |
| --- | ------------ | -------------- | ----------- | --- | --- | --- | --- |
| •   |              |                | {candidate} |     |     |     |     |
Candidateoption:
| Is this | a valid | distractor? |     |     |     |     |     |
| ------- | ------- | ----------- | --- | --- | --- | --- | --- |
Figure5 Promptforjudgingwhetheracandidateoptioncanserveasadistractor. The system prompt defines
the teacher-style judgment criteria, and the user prompt supplies the question, the gold answer set, and the candidate
| option to | be checked. |     |     |     |     |     |     |
| --------- | ----------- | --- | --- | --- | --- | --- | --- |
Candidates labeled as are removed from the pool. Only candidates labeled as are retained for
INVALID VALID
| final option  | sampling. |             |     |     |            |     |     |
| ------------- | --------- | ----------- | --- | --- | ---------- | --- | --- |
| B.3 Benchmark |           | Composition |     |     | Statistics |     |     |
Table11reportstheper-subtasksamplecountsandthegraphrelationprobedbyeachsubtask,complementing
| the high-level | statistics |     | quoted | in the | main text | (§4.1). |     |
| -------------- | ---------- | --- | ------ | ------ | --------- | ------- | --- |
Figure 6 summarizes two additional aspects of K12-Bench: (i) subject distribution across task families, and
(ii) answer cardinality, i.e., the number of correct options per subtask. These properties are important for
interpreting benchmark performance, as exact-match accuracy depends not only on reasoning difficulty but
| also on | the structure | of  | the answer | space. |     |     |     |
| ------- | ------------- | --- | ---------- | ------ | --- | --- | --- |
The left panel shows that subject coverage is broadly balanced across task families. For most tasks, items
are evenly distributed across biology, chemistry, mathematics, and physics, without a clear bias towards any
single subject. Evidence exhibits a different pattern: it draws primarily from chemistry, biology, and physics,
and contains no mathematics items. This is a direct consequence of the graph schema, as mathematics does
not include Experiment nodes and therefore cannot instantiate verifies-based queries. Overall, the subject
distribution reflects the underlying curriculum structure rather than sampling artifacts.
The right panel shows that single-answer items dominate several task families, especially Locate. This
pattern is largely induced by the semantics of the underlying graph queries. Many queries are structurally
single-answer: for example, “first appearance” in Locate typically corresponds to a unique earliest location,
and tightly constrained relation queries often yield a single valid node in the merged graph. More generally, a
substantial portion of K12-Bench is derived from relations whose gold sets are inherently small, leading to a

K12-KGraph 26
Table11 K12-Benchstatistics. All tasks use multi-select format with four options.
Task Subtask #Samples ProbedRelation
Ground (Knowledge Grounding) Subtask 1 1,754 Exercise → Concept/Skill
Subtask 2 2,096 Concept/Skill → Exercise
Prereq (Prerequisite Reasoning) Subtask 1 2,565 Prerequisite closure
Subtask 2 2,852 Direct successors
Neighbor (Neighbor Recommendation) – 4,358 is_a + relates_to
Evidence (Experiment Evidence) Subtask 1 769 Concept → Experiment
Subtask 2 622 Experiment → Concept
Locate (Cross-Chapter Indexing) Subtask 1 8,456 First appearance location
Subtask 2 168 Chapter prerequisites (leads_to)
Total 23,640
  
  
  
     
  
 
 * U R X Q G  3 U H U H T  1 H L J K E R U  ( Y L G H Q F H  / R F D W H
     H J D W Q H F U H 3
 6 X E M H F W  ' L V W U L E X W L R Q  E \  7 D V N  ) D P L O \
      
     
     
          
                                      
    
 
 7     7     7     7     7   7     7     7     7   
 % L R O R J \  & K H P L V W U \  0 D W K H P D W L F V  3 K \ V L F V
     H J D W Q H F U H 3
 & R U U H F W  2 S W L R Q  & D U G L Q D O L W \  E \  6 X E W D V N
   
           
     
  
                 
                           
 * U R X Q G  3 U H U H T  1 H L J K E R U  ( Y L G H Q F H  / R F D W H
   R S W L R Q    R S W L R Q V    R S W L R Q V
Figure6 BenchmarkcompositionstatisticsforK12-Bench. The left panel shows subject distribution across task
families, and the right panel shows distribution of the number of correct options per subtask.
natural skew toward single-answer instances.
At the same time, the final option construction stage explicitly enforces balance over both answer cardinality
and label combinations. The number of retained correct options per item is selected from the feasible set
under a balancing constraint over k ∈{1,2,3}, and the corresponding label combination (e.g., A, A,B, B,C,D)
isassignedthroughaseparatebalancingprocedurebeforepopulatingslotsA–D.Asaresult, whiletaskfamilies
retain their intrinsic structural differences, the benchmark avoids systematic bias toward particular answer
letters or specific label combinations.
B.4 Answering Prompt and Decoding Rules
All K12-Bench evaluations are run through the OpenAI-compatible chat interface. Each sample is formatted
as a two-message conversation consisting of a fixed system prompt and a user prompt instantiated from the
benchmark item. The combined prompt is shown in Figure 7. The system prompt constrains the model to
answer using only option labels, while the user prompt presents the question stem and the four candidate
options.
Across all released model configurations in eval/configs/models/, we use deterministic decoding with
temperature =0.0, top_p =1.0, and max_tokens =32.
Modelresponsesarepost-processedbyalightweightparsertoextractpredictedlabelsets. Boththerawmodel
output and the parsed prediction are retained: the former is stored verbatim, while the latter is normalized
(uppercased, deduplicated, and sorted) and used for evaluation.
The parser performs minimal normalization (e.g., unifying common delimiter variants) and extracts labels
from the model output without attempting semantic repair. For abnormal cases (e.g., empty responses or

K12-KGraph 27
| PROMPT | FOR | ANSWERING |     | K12-BENCH |     | QUESTIONS |     |
| ------ | --- | --------- | --- | --------- | --- | --------- | --- |
SystemPrompt:
| You are | a K–12 | teaching | expert. |     |     |     |     |
| ------- | ------ | -------- | ------- | --- | --- | --- | --- |
Please output the setofcorrectoptionletters according to the requirements of the question, and you
| must strictly | adhere    | to      | the following | format:      |          |              |        |
| ------------- | --------- | ------- | ------------- | ------------ | -------- | ------------ | ------ |
| • Only        | uppercase | letters | A/B/C/D       | are          | allowed; |              |        |
| • Output      | example:  | "A"     | or "A,C";     |              |          |              |        |
| • Multiple    | letters   | must    | be arranged   | in ascending |          | alphabetical | order; |
• Only English commas are allowed for separation; spaces are not permitted;
• .
Noexplanations,analyses,prefixes,suffixes,punctuation,orlinebreaksareallowed
| Each question | may     | have    | one or         | more correct | options. |            |             |
| ------------- | ------- | ------- | -------------- | ------------ | -------- | ---------- | ----------- |
| No points     | will be | awarded | for incorrect, | multiple,    |          | or missing | selections. |
UserPrompt:
| Question: | {question} |     |     |     |     |     |     |
| --------- | ---------- | --- | --- | --- | --- | --- | --- |
A. {A}
B. {B}
C. {C}
D. {D}
| Please provide |     | the set | of letters | for the answer: |     |     |     |
| -------------- | --- | ------- | ---------- | --------------- | --- | --- | --- |
The system prompt enforces
Figure7 PromptthatinstructsthemodelhowtorespondtoK12-Benchquestions.
an answer-only output format, and the user prompt presents the question together with the four labeled candidate
options.
API failures), instances are flagged and re-evaluated via automatic retries until a valid response is obtained.
| B.5 Baseline | EM/F1 | Computation |     | for | the Random | Predictor |     |
| ------------ | ----- | ----------- | --- | --- | ---------- | --------- | --- |
For completeness, we formalize how exact match (EM) and option-label F1 are computed for the simple
random baseline on K12-Bench. Let the gold label set for an instance be G⊆{A,B,C,D} and the predicted
label set be Gˆ. Denote k =|G| and m=|Gˆ|. Per-instance scores are defined as
EM(G,Gˆ)=1[G=Gˆ], (1)
|G∩Gˆ|
P(G,Gˆ)= (2)
,
|Gˆ|
|G∩Gˆ|
R(G,Gˆ)= (3)
,
|G|
2P(G,Gˆ)R(G,Gˆ)
F1(G,Gˆ)= (4)
,
P(G,Gˆ)+R(G,Gˆ)
F1(G,Gˆ)=0
| with | when | both | precision | and recall | are | zero. |     |
| ---- | ---- | ---- | --------- | ---------- | --- | ----- | --- |

| K12-KGraph |     |     |     |     |     |     |     | 28  |
| ---------- | --- | --- | --- | --- | --- | --- | --- | --- |
Aggregation: instance-level (example-based) macro F1. To form a task- or benchmark-level F1, we average
per-instance F1 across instances rather than pooling intersection/union counts:
|     |     |     |     |     |      | 1 N (cid:88)task |     |     |
| --- | --- | --- | --- | --- | ---- | ---------------- | --- | --- |
|     |     |     |     |     |      |                  | ,Gˆ | (5) |
|     |     |     |     |     | F1 = | F1(G             | ),  |     |
|     |     |     |     |     | task | N                | i i |     |
task
i=1
and overall scores are obtained by weighting task-level averages by the task’s instance count. This is the
instance-level (example-based) macro F1, equivalent to scikit-learn’s average=‘samples’ convention for
multi-label classification; every instance contributes equal weight regardless of its gold cardinality. We prefer
this aggregation over a micro (corpus-pooled) F1 for two reasons: (i) it keeps F1 on the same per-instance
footing as EM, so EM and F1 numbers in the same row are directly comparable; and (ii) micro-pooling would
implicitly up-weight items with more correct labels, mixing difficulty with cardinality in an undesirable way
| for an evaluation |     | aimed | at curriculum |     | cognition | rather than | label frequency. |     |
| ----------------- | --- | ----- | ------------- | --- | --------- | ----------- | ---------------- | --- |
For a random predictor, the baseline score is the expected EM or F1 under the corresponding sampling rule.
Equivalently, one may view the baseline as repeatedly sampling predictions and averaging the resulting scores
| over infinitely | many | trials. |     |     |     |     |     |     |
| --------------- | ---- | ------- | --- | --- | --- | --- | --- | --- |
This baseline samples Gˆ uniformly from the non-empty subsets of {A,B,C,D}. For a
| Random     | guess. |              |     |          |     |     | 15  |     |
| ---------- | ------ | ------------ | --- | -------- | --- | --- | --- | --- |
| fixed gold | set G, | the expected |     | score is |     |     |     |     |
1
|     |     |     |     | E[EM|G]= |     | ,   |     | (6) |
| --- | --- | --- | --- | -------- | --- | --- | --- | --- |
15
|     |     |     |     |          |     | 1 (cid:88) |          |     |
| --- | --- | --- | --- | -------- | --- | ---------- | -------- | --- |
|     |     |     |     | E[F1|G]= |     |            | F1(G,S). | (7) |
15
∅̸=S⊆{A,B,C,D}
Becausethelabelpositionsaresymmetricallybalanced,theseexpectationsdependonlyonthegoldcardinality
| k =|G|,          | not on | the specific | letters | in             | G.  |          |            |     |
| ---------------- | ------ | ------------ | ------- | -------------- | --- | -------- | ---------- | --- |
| B.6 Illustrative |        | Example      |         | of KG-Grounded |     | Resource | Derivation |     |
Figure 2 in the main text provides a concrete instantiation of the K12-KGraph-based construction pipeline.
Both K12-Bench and K12-Train are generated by first selecting a target relation and extracting the corre-
sponding local subgraph, followed by task-specific instantiation under structural constraints. The benchmark
version preserves the original graph query form for evaluation, while the training version reformulates the
| same structure | into | instruction–response |           |         | pairs | for supervision. |     |     |
| -------------- | ---- | -------------------- | --------- | ------- | ----- | ---------------- | --- | --- |
| C K12-Train    |      | Construction         |           | Details |       | and SFT Protocol |     |     |
| C.1 Prompt     |      | for QA               | Synthesis |         |       |                  |     |     |
We use separate prompt templates for node-level and edge-level QA generation. As shown in Figure 8 and
Figure 9, node-level prompts instruct the LLM to generate questions targeting the node’s key attributes, while
edge-level prompts instruct the LLM to generate questions that require reasoning about the relationship. For
readability, Figure 9 presents the shared logic of the edge-level prompt with a simplified input schema. In the
implementation, each multimodal relation uses a relation-specific template supplied with the relevant figure
or visual-element description, relation rationale, and, where applicable, the exercise stem or supported-edge
metadata. TheresultingVQAinstanceispairedwiththecompletefigureforillustrates,requires_figure,
and supports_edge, or with a copy of the complete figure in which the target bounding box is highlighted
for refers_to. Each synthesis template is sent as a single user message without a separate system prompt.
All prompts include style constraints: answers should be grade-appropriate in language, logically rigorous, and
strictly grounded in the graph data. Before prompting, each node’s property set is cropped to only the fields
relevant for the target QA type (e.g., importance is removed for Concept QAs to prevent meta-commentary
leakage).

K12-KGraph 29
SINGLE-TURN PROMPT FOR NODE-LEVEL QA SYNTHESIS
You are a top K–12 education expert with 20 years of experience, skilled at transforming complex
STEM textbook knowledge into highly logical and thought-provoking QA materials.
Your task is to synthesize n high-quality SFT training datasets based on the provided Concept/Skill.
InputData
• {name}
name:
• {properties_json}
properties:
GenerationStrategy
1.GeneralConstraints
• Each example must contain exactly .
onequestionandoneanswer
• Allcontentmustbe ; donotintroduceexternalknowledge.
strictlygroundedintheinputproperties
• Use aliases when appropriate to improve naturalness.
2.Concept-OrientedQA
• Questions should focus on:
definition (what it is),
■
key properties or formulas,
■
basic understanding.
■
• Answers must follow the structure:
\box{core definition} + \box{core formula / key rule}(optional)
followed by:
1 2 sentences of explanation (optional),
■
1 illustrative example (optional).
■
3.Skill-OrientedQA
• Questions should focus on:
what the method is,
■
how to apply it (steps or procedure),
■
when to use it (applicable scenarios).
■
• Answers must follow the structure:
\box{method description or steps}
followed by:
brief explanation of usage or advantages (optional),
■
1 illustrative example (optional).
■
StyleRequirements
• Language must be .
clear,concise,andpedagogicallyappropriate
• Maintain a , but avoid unnecessary complexity.
formalandprecisetone
• Explanations should be accessible to K–12 students.
Figure8 Node-levelpromptforK12-TrainQAsynthesis. Given a Concept or Skill and its properties, the model
is asked to generate factually grounded question–answer pairs for K–12 learners.

K12-KGraph 30
| SINGLE-TURN | PROMPT |     | FOR EDGE-LEVEL |     | QA SYNTHESIS |     |
| ----------- | ------ | --- | -------------- | --- | ------------ | --- |
You are a top K–12 education expert with 20 years of experience, skilled at transforming complex
STEM textbook knowledge into highly logical and thought-provoking QA materials.
Yourtaskistosynthesize{n}high-qualitySFTtrainingdatasetsbasedontheprovided
edgerelation
(is_a, prerequisites_for, relates_to, verifies, illustrates, refers_to, requires_figure,
supports_edge).
InputData
| • {source_name} |     |     |     |     |     |     |
| --------------- | --- | --- | --- | --- | --- | --- |
source:
| • target: {target_name} |                   |     |     |     |     |     |
| ----------------------- | ----------------- | --- | --- | --- | --- | --- |
| •                       | {properties_json} |     |     |     |     |     |
properties:
GenerationStrategy
1.GeneralConstraints
| • Each example     | must | contain | exactly | onequestionandoneanswer |                                    | .   |
| ------------------ | ---- | ------- | ------- | ----------------------- | ---------------------------------- | --- |
| • Allcontentmustbe |      |         |         |                         | ; donotintroduceexternalknowledge. |     |
strictlygroundedintheinputproperties
• Questions must focus on explaining , rather than merely restating the two
whytheedgeholds
| endpoint names. |     |     |     |     |     |     |
| --------------- | --- | --- | --- | --- | --- | --- |
2.Relation-SpecificPromptingGoals
• ask why {source_name} belongs to or is part of {target_name}; answers should explain
is_a:
| how the source | satisfies | the | defining | properties | of the target. |     |
| -------------- | --------- | --- | -------- | ---------- | -------------- | --- |
• ask why one should learn {source_name} before{target_name}; answers
prerequisites_for:
should explain what knowledge or ability the source provides that supports later learning of the
target.
• relates_to: ask what relationship holds between {source_name} and {target_name}; answers
| should clarify | their connection, |     | contrast, | or  | shared properties. |     |
| -------------- | ----------------- | --- | --------- | --- | ------------------ | --- |
• verifies: ask what principle is verified by {source_name}, or how {source_name} verifies
{target_name}; answers should trace the path from experiment content and observations to the
| verified concept. |     |     |     |     |     |     |
| ----------------- | --- | --- | --- | --- | --- | --- |
• askwhatconcept,skill,orexperimentisillustratedbytheentirefigure,whythefigure
illustrates:
illustrates{target_name}, orhowthefigurehelpsexplain{target_name}; answersshouldexplain
how the overall visual content represents the definition, characteristics, structure, procedure,
| process, or | phenomenon | associated | with | the | target. |     |
| ----------- | ---------- | ---------- | ---- | --- | ------- | --- |
• ask which concept, skill, or experiment a specific visual element corresponds to, why
refers_to:
the element refers to {target_name}, or what role it plays in understanding the target; answers
should connect the localized element’s visible features to the corresponding properties of the
target.
• ask why an exercise requires the figure, what information the figure provides
requires_figure:
for solving the exercise, or how the figure contributes to understanding the problem; answers
should identify the conditions, data, structures, phenomena, or relations supplied by the figure
and explain why the exercise cannot be fully understood or solved without them.
• supports_edge: ask how the figure supports the relation between {source_name} and {target_-
name}, which visual information provides evidence for that relation, or why the figure can serve
as visual evidence for the edge; answers should state the source–target relation and explain how
| the visible | content directly |     | supports | it. |     |     |
| ----------- | ---------------- | --- | -------- | --- | --- | --- |
3.PreferredAnswerStructures
• is_a: because {source definition}, {target definition}, and {source satisfies target definition},
| therefore {source | belongs | to  | target}. |     |     |     |
| ----------------- | ------- | --- | -------- | --- | --- | --- |
• prerequisites_for: because learning the target requires {specific knowledge/ability}, and the

K12-KGraph 31
source provides this knowledge/ability, therefore the source should be learned first.
• relates_to: first state the concrete relationship between the two concepts, then briefly explain
each side of the relation.
• verifies: from the experiment’s setup, operation, or observed phenomenon, explain what result
is seen and why that result supports the target concept.
• illustrates: because the figure presents {main visual content}, which reflects the {defini-
tion/characteristics/structure/method/steps/process/phenomenon} of {target_name}, the figure
provides a visual illustration of {target_name}.
• refers_to: because the visual element exhibits {visible features}, which correspond to the
{definition/characteristics/structure/method/steps/process/phenomenon} of {target_name}, the
element refers to {target_name}.
• requires_figure: because solving or interpreting the exercise requires {specific information to
be identified/analyzed/calculated}, and this information is provided by {conditions/data/struc-
tures/phenomena/relations visible in the figure}, the figure is necessary for understanding or
answering the exercise.
• supports_edge: first state the concrete {edge_type} relation between {source_name} and
{target_name}; thenexplainwhatvisualinformationthefigurepresentsandhowthatinformation
directly supports the relation; finally conclude that the figure provides visual evidence for the
edge.
StyleRequirements
• Language must be .
clear,concise,andpedagogicallyappropriate
• Maintain a , but avoid unnecessary complexity.
formalandprecisetone
• Explanations should be accessible to K–12 students.
Figure9 Edge-levelpromptforK12-TrainQAsynthesis. Givenatypedrelationanditsendpointnodes,themodel
is asked to generate factually grounded question–answer pairs for K–12 learners.
C.2 Training Configuration
Table 12 provides the full-parameter configuration for the text-only SFT experiments, while Table 13 reports
the LoRA configuration for the multimodal experiments. Within each experiment group, all models share an
identical set of hyperparameters for fair comparison. Hyperparameters not explicitly listed follow the default
settings of the training framework.
C.3 Baseline Subsampling and Fairness Controls
For the text-only experiments, to ensure a fair comparison under a fixed data budget, we subsample 2,300
instances from each baseline dataset, matching the size of K12-Train.
Importantly, when metadata (e.g., source tags, task types, or length categories) is available, we perform
stratified sampling to preserve the original distribution of these attributes. This ensures that the subsampled
data remains representative of the full dataset rather than being biased toward a particular subset.
Our goal is to isolate the effect of data quality and structural grounding under a controlled budget, rather
than total data scale. Using a fixed-size and distribution-preserving sampling strategy allows us to attribute
performance differences to dataset characteristics rather than volume or sampling artifacts.
We further verify that different random samples from the same dataset yield similar performance trends in
pilot experiments, suggesting that our conclusions are not sensitive to a particular subset.
D Validation and Quality Assurance

K12-KGraph 32
|                |     | Table12   | Full-parameterSFTconfigurationforthetext-onlyexperiments. |           |              |             |                 |                  |
| -------------- | --- | --------- | --------------------------------------------------------- | --------- | ------------ | ----------- | --------------- | ---------------- |
|                |     |           | Component                                                 |           |              |             | Setting         |                  |
|                |     |           | Backbones                                                 |           |              |             | Qwen3-4B-Base;  | Llama3.1-8B-Base |
|                |     |           | Framework                                                 |           |              |             | LLaMA-Factory   | (v0.9.5.dev0)    |
|                |     |           | SFT                                                       | Type      |              |             | Full-parameter  | fine-tuning      |
|                |     |           | Max                                                       | Sequence  | Length       |             | 32768           |                  |
|                |     |           | Per-device                                                |           | Batch        | Size        | 1               |                  |
|                |     |           | Gradient                                                  |           | Accumulation |             | 4               |                  |
|                |     |           | Effective                                                 |           | Batch Size   |             | 32 (1 × 4       | × 8 GPUs)        |
|                |     |           | Optimizer                                                 |           |              |             | AdamW           |                  |
|                |     |           | Learning                                                  |           | Rate         |             | 5×10−6          |                  |
|                |     |           | Scheduler                                                 |           |              |             | Cosine decay    |                  |
|                |     |           | Warmup                                                    |           |              |             | 10% steps       |                  |
|                |     |           | Epochs                                                    |           |              |             | 3               |                  |
|                |     |           | Precision                                                 |           |              |             | bf16            |                  |
|                |     |           | Distributed                                               |           | Training     |             | DeepSpeed       | ZeRO-3           |
|                |     |           | Random                                                    |           | Seed         |             | 42              |                  |
|                |     |           | Checkpoint                                                |           | Selection    |             | Last checkpoint |                  |
|                |     |           | Hardware                                                  |           |              |             | 8×A100 (80GB)   |                  |
|                |     |           | Training                                                  |           | Time         |             | ∼0.4–1.7 hours  | per run          |
| D.1 Validation |     | Strategy, |                                                           | Annotator |              | Background, |                 | and Ethics       |
To ensure the reliability of K12-KGraph and its downstream resources, we adopt a tiered validation strategy
centered on the knowledge graph (KG), which serves as the foundation for both K12-Bench and K12-Train.
The KG receives the most intensive validation, combining automatic structural checks with full human
verification. In contrast, K12-Bench and K12-Train are validated via targeted manual spot-checks rather
than full re-annotation. This difference is motivated by how these resources are constructed. K12-Bench
instances (including both answers and distractors) are deterministically derived from graph structure rather
than generated by LLMs, making their correctness largely reducible to the correctness of the underlying KG.
K12-Train, as a supervision dataset, does not require perfect instance-level accuracy: minor imperfections
are tolerable as long as the data remains factually grounded and pedagogically useful. Therefore, verifying
| consistency | with | the | validated | KG  | is sufficient | for | both resources. |     |
| ----------- | ---- | --- | --------- | --- | ------------- | --- | --------------- | --- |
All human validation is conducted by domain-qualified annotators. Since K12-KGraph covers four core
disciplines (mathematics, physics, chemistry, and biology), we recruit subject specialists accordingly, with
threeannotatorspersubject(12intotal). AnnotatorsareexperiencedK–12educationpractitioners,collectively
covering primary, middle, and high school levels, ensuring reliable assessment of both fine-grained concepts
| and cross-stage |     | curriculum | relations. |     |     |     |     |     |
| --------------- | --- | ---------- | ---------- | --- | --- | --- | --- | --- |
Annotators are compensated at rates that meet or exceed the local minimum wage, in accordance with
standard academic annotation practices. All data are derived from public educational materials and do not
| involve | sensitive   | personal | information. |     |        |     |           |              |
| ------- | ----------- | -------- | ------------ | --- | ------ | --- | --------- | ------------ |
| D.2 KG  | Validation: |          | Structural   |     | Checks |     | and Human | Verification |
Wefirstperformautomaticconsistencychecksontheis_aandprerequisites_-
Automaticstructuralchecks.
for subgraphs, both expected to be directed acyclic graphs (DAGs). Cycles and structural inconsistencies are
| detected | after graph |     | construction |     | and merging. |     |     |     |
| -------- | ----------- | --- | ------------ | --- | ------------ | --- | --- | --- |
Detected conflicts are then reviewed by subject annotators, who determine whether to remove, modify, or
retain edges based on curriculum correctness. In cases of ambiguity, decisions are made through discussion
among annotators to ensure consistency with standard curriculum progression.
Human verification. After resolving structural conflicts, we conduct full human validation over the entire
graph. Each node and edge is independently annotated by three annotators within the same subject area.

K12-KGraph 33
|     |     | Table13     | LoRASFTconfigurationforthemultimodalexperiments. |              |                   |                  |
| --- | --- | ----------- | ------------------------------------------------ | ------------ | ----------------- | ---------------- |
|     |     | Component   |                                                  |              | Setting           |                  |
|     |     | Backbone    |                                                  |              | Qwen3.5-2B-Base   |                  |
|     |     | Framework   |                                                  |              | LLaMA-Factory     | (v0.9.5.dev0)    |
|     |     | SFT         | Type                                             |              | LoRA              |                  |
|     |     | Template    |                                                  |              | qwen3_vl_nothink  |                  |
|     |     | LoRA        | Configuration                                    |              | rank 8, alpha     | 16, dropout 0.05 |
|     |     | LoRA        | Target                                           | Modules      | All modules       |                  |
|     |     | Max         | Sequence                                         | Length       | 4096              |                  |
|     |     | Max         | Image                                            | Size         | 262,144 pixels    |                  |
|     |     | Per-device  |                                                  | Batch Size   | 4                 |                  |
|     |     | Gradient    |                                                  | Accumulation | 2                 |                  |
|     |     | Effective   |                                                  | Batch Size   | 64 (4 × 2         | × 8 GPUs)        |
|     |     | Learning    |                                                  | Rate         | 1×10−4            |                  |
|     |     | Scheduler   |                                                  |              | Cosine decay      |                  |
|     |     | Warmup      |                                                  |              | 10% steps         |                  |
|     |     | Epochs      |                                                  |              | 3                 |                  |
|     |     | Precision   |                                                  |              | bf16              |                  |
|     |     | Distributed |                                                  | Training     | 8-GPU distributed | data parallel    |
|     |     | Data        | Workers                                          |              | 16 preprocessing; | 4 dataloader     |
|     |     | Random      |                                                  | Seed         | 42 (framework     | default)         |
|     |     | Checkpoint  |                                                  | Selection    | Last checkpoint   |                  |
|     |     | Hardware    |                                                  |              | 8×A100 (80GB)     |                  |
Disagreements are identified and resolved through joint review, leading to a consensus decision (retain, modify,
| or remove). | The consensus | label | is  | taken as final. |     |     |
| ----------- | ------------- | ----- | --- | --------------- | --- | --- |
Visual relation filtering. Each model-inferred visual relation includes a rationale and confidence score. Based
on confidence-stratified inspection, we retain and relations with confidence at least
|     |     |     |     | refers_to |     | illustrates |
| --- | --- | --- | --- | --------- | --- | ----------- |
0.85,andrequires_figureandsupports_edgerelationswithconfidenceatleast0.95. Apredictedbounding
box is retained only when it is valid and its localization confidence is at least 0.9. After relation filtering, we
remove a if it has no retained illustrates, supports_edge, or incoming relation
Figure requires_figure
and contains no VisualElement with a retained refers_to relation. Visual elements without a retained
relation and unused reified edge references are pruned together with their incident edges.
refers_to
To quantify annotation reliability, we report inter-annotator agreement (IAA) before adjudication (Table 14).
Agreementtendstobehigherforstructurallyexplicitrelations(e.g., is_a)andlowerforsemanticallynuanced
ones (e.g., relates_to). After adjudication, the final graph achieves high precision.
| D.3 Spot-Check |           | Validation |           | of K12-Bench   | and K12-Train |           |
| -------------- | --------- | ---------- | --------- | -------------- | ------------- | --------- |
| We validate    | K12-Bench | and        | K12-Train | via stratified | manual        | sampling. |
For K12-Bench, we perform stratified sampling across task families, subjects, and grade levels, and manually
review 15% instances in total. Each instance is checked for consistency between the question text, gold answer
set, and distractor options with respect to the underlying graph structure. We find that of sampled
98.4%
instancesarefullycorrect, whiletheremainingcasesprimarilyinvolveminorissuessuchasphrasingambiguity
| or borderline | distractor | quality, | rather | than semantic | errors. |     |
| ------------- | ---------- | -------- | ------ | ------------- | ------- | --- |
For K12-Train, we sample QA pairs from different construction categories (e.g., node-grounded and
10%
relation-grounded)andevaluatefactualconsistency,pedagogicalappropriateness,andlinguisticclarity. Among
the sampled instances, are judged to be fully correct, with most errors attributable to surface-level
96.9%
| issues rather | than | factual inconsistencies. |     |     |     |     |
| ------------- | ---- | ------------------------ | --- | --- | --- | --- |
Across both resources, most identified issues are minor (e.g., phrasing or distractor similarity) rather than
semantic errors, confirming that the validated KG provides a reliable basis for both benchmark construction
and QA synthesis.

K12-KGraph 34
Table14 Inter-annotatoragreement(IAA)beforeadjudication,measuredbyFleiss’κ,acrosssubjectsand
node/edgetypes.
|     | Group | Category |     | Math Physics |      | Chemistry | Biology | Overall |
| --- | ----- | -------- | --- | ------------ | ---- | --------- | ------- | ------- |
|     |       | Concept  |     | 0.84         | 0.86 | 0.85      | 0.83    | 0.85    |
|     |       | Skill    |     | 0.81         | 0.83 | 0.82      | 0.80    | 0.82    |
Node
|     |      | Experiment        |     | –    | 0.85 | 0.84 | 0.83 | 0.84 |
| --- | ---- | ----------------- | --- | ---- | ---- | ---- | ---- | ---- |
|     |      | Exercise          |     | 0.78 | 0.80 | 0.79 | 0.77 | 0.79 |
|     |      | is_a              |     | 0.90 | 0.92 | 0.91 | 0.89 | 0.91 |
|     |      | prerequisites_for |     | 0.85 | 0.87 | 0.86 | 0.84 | 0.86 |
|     | Edge | relates_to        |     | 0.68 | 0.70 | 0.69 | 0.67 | 0.69 |
|     |      | verifies          |     | –    | 0.82 | 0.83 | 0.81 | 0.82 |
|     |      |                   |     | 0.79 | 0.81 | 0.80 | 0.78 | 0.80 |
tests_concept/skill
|     | Overall | –   |     | 0.83 | 0.85 | 0.84 | 0.82 | 0.84 |
| --- | ------- | --- | --- | ---- | ---- | ---- | ---- | ---- |
Table15 Per-subtaskK12-Benchresults,reportedin%. EM = exact match; F1 is computed at the option-label
level.
Ground_1 Ground_2 Prereq_1 Prereq_2 Neighbor Evidence_1 Evidence_2 Locate_1 Locate_2
Model
|     |     | EM  | F1 EM F1 | EM F1 EM | F1 EM | F1 EM | F1 EM | F1 EM F1 EM F1 |
| --- | --- | --- | -------- | -------- | ----- | ----- | ----- | -------------- |
OpenSourceModels
Meta-LLaMA-3-8B-Instruct 9.1 58.0 3.8 52.3 6.4 50.5 2.5 45.6 3.8 53.4 4.3 55.7 6.3 54.9 11.5 53.9 6.5 48.8
GLM-4.7-Flash 43.0 74.1 30.8 68.3 12.2 59.1 14.4 54.3 15.2 59.6 46.3 75.9 30.5 68.9 48.9 66.3 13.1 60.3
Ministral-3-14B-Instruct 40.8 74.7 44.9 75.5 17.2 61.0 19.5 57.9 14.5 59.8 47.3 77.6 27.2 67.8 59.3 72.2 19.0 58.1
Qwen3-32B 44.2 76.8 48.9 77.6 17.0 62.3 16.9 58.6 14.6 60.3 49.5 78.6 32.0 70.8 72.1 75.9 18.5 59.0
Gemma-4-31B-IT 45.7 76.8 54.8 80.9 20.3 63.6 35.4 61.7 15.0 60.7 50.1 78.0 34.9 68.8 73.4 73.5 19.0 62.0
ProprietaryModels
GPT-4o 28.9 71.1 31.5 70.1 9.9 60.1 8.7 55.1 10.1 57.9 37.5 74.3 26.2 68.8 56.4 72.6 12.5 58.0
GPT-5-mini 29.0 70.8 31.6 70.0 10.5 60.1 9.4 55.4 12.5 59.0 38.4 74.8 26.2 69.2 56.4 73.1 10.1 58.6
GPT-5.2 43.9 76.4 56.6 81.5 13.5 60.9 21.9 58.3 13.1 60.0 46.9 77.7 34.9 69.1 71.2 71.7 17.3 61.7
Gemini-2.5-Flash 56.1 75.6 59.6 75.8 24.0 55.3 34.8 57.2 15.4 56.0 55.0 75.9 37.3 67.2 73.9 74.4 16.3 52.9
Gemini-3-Flash 42.5 75.5 80.9 89.9 26.6 56.1 42.1 60.1 33.4 63.5 55.9 76.7 36.8 67.1 82.7 82.9 33.9 67.6
| E Extended |           | Results | and Sanity | Checks |     |     |     |     |
| ---------- | --------- | ------- | ---------- | ------ | --- | --- | --- | --- |
| E.1 Full   | Benchmark | Results |            |        |     |     |     |     |
Table 15 and Table 16 provide fine-grained K12-Bench results omitted from the main text. Rather than
repeating the task-family averages in Table 3, we report per-subtask and per-subject breakdowns, highlighting
| the sources   | of variation | behind | the aggregate | results. |     |     |     |     |
| ------------- | ------------ | ------ | ------------- | -------- | --- | --- | --- | --- |
| E.2 Stability | Across       | Random | Seeds         |          |     |     |     |     |
Although we do not conduct a full multi-seed evaluation on the entire benchmarks due to computational cost,
we perform controlled multi-seed validation via stratified subsampling to assess robustness.
Specifically, for both GaokaoBench and EduEval, we randomly sample 20% of instances within each subtask
to preserve the original task distribution. On this fixed subset, we repeat the SFT process with three different
| random | seeds ({42, | 123, 2026}) | and evaluate | the resulting | models. |     |     |     |
| ------ | ----------- | ----------- | ------------ | ------------- | ------- | --- | --- | --- |
Table 17 reports the overall performance on these sampled evaluation sets. We observe only minor variation
across seeds, indicating that the performance gains are stable and not driven by a particular random
initialization.
These results suggest that performance differences between datasets are stable with respect to seed choice.

K12-KGraph 35
Table16 Per-subjectK12-Benchresults,reportedin%. EM = exact match; F1 is instance-level (example-based)
macro F1. This table complements Table 15 by showing how performance varies across curriculum domains.
|     |     |     | Biology | Chemistry | Mathematics | Physics | Overall |
| --- | --- | --- | ------- | --------- | ----------- | ------- | ------- |
Model
|     |     |     | EM F1 | EM F1 | EM F1 | EM F1 | EM F1 |
| --- | --- | --- | ----- | ----- | ----- | ----- | ----- |
OpenSourceModels
Meta-LLaMA-3-8B-Instruct 8.8 53.5 8.1 53.2 5.2 51.3 5.7 52.0 7.2 52.6
|     |     |     | 34.4 64.4 | 28.8 63.2 | 34.0 64.5 | 31.2 64.0 | 31.7 63.9 |
| --- | --- | --- | --------- | --------- | --------- | --------- | --------- |
GLM-4.7-Flash
Ministral-3-14B-Instruct 39.9 68.3 35.2 66.9 38.9 67.5 37.2 67.2 37.5 67.4
| Qwen3-32B |     |     | 45.4 70.8 | 39.8 68.7 | 44.2 69.8 | 42.5 69.1 | 42.6 69.5 |
| --------- | --- | --- | --------- | --------- | --------- | --------- | --------- |
|           |     |     | 48.9 70.2 | 44.1 69.0 | 47.8 69.9 | 46.3 69.0 | 46.4 69.5 |
Gemma-4-31B-IT
ProprietaryModels
|     |     |     | 33.2 67.2 | 29.2 65.2 | 31.9 65.9 | 31.3 65.6 | 31.1 65.9 |
| --- | --- | --- | --------- | --------- | --------- | --------- | --------- |
GPT-4o
| GPT-5-mini |     |     | 33.8 67.7 | 29.8 65.7 | 32.4 66.4 | 31.9 66.1 | 31.7 66.4 |
| ---------- | --- | --- | --------- | --------- | --------- | --------- | --------- |
|            |     |     | 45.5 69.2 | 39.9 67.2 | 44.8 68.5 | 42.7 67.4 | 42.8 68.0 |
GPT-5.2
Gemini-2.5-Flash 51.3 68.0 45.0 65.8 50.8 67.1 48.0 66.3 48.3 66.7
|     |     |     | 60.8 74.5 | 53.6 72.0 | 59.8 73.7 | 56.2 72.3 | 57.1 73.0 |
| --- | --- | --- | --------- | --------- | --------- | --------- | --------- |
Gemini-3-Flash
Table17 Performancevariationacrossrandomseeds({42,123,2026}). Meanandstandarddeviationarecomputed
| over three runs | on a 20% stratified | subset.          |     |             |              |      |     |
| --------------- | ------------------- | ---------------- | --- | ----------- | ------------ | ---- | --- |
|                 |                     | Backbone         |     | GaokaoBench | EduEval      |      |     |
|                 |                     | Qwen3-4B-Base    |     | 1002.94 ±   | 6.37 66.83 ± | 0.11 |     |
|                 |                     | Llama3.1-8B-Base |     | 621.18 ±    | 5.28 40.87 ± | 0.23 |     |
| E.3 Overlap     | and Leakage         | Analysis         |     |             |              |      |     |
We analyze potential data contamination between K12-Train and the external evaluation benchmarks
| (GaokaoBench | and EduEval). |     |     |     |     |     |     |
| ------------ | ------------- | --- | --- | --- | --- | --- | --- |
K12-TrainissynthesizedfromK–12textbookcontent,focusingoncurriculumstructure
Source independence.
and concept relations. In contrast, GaokaoBench consists of standardized high-stakes examination questions,
whileEduEvalisconstructedindependentlywithdiverseevaluationobjectives. Thesesourcesareinstitutionally
| and functionally | distinct. |     |     |     |     |     |     |
| ---------------- | --------- | --- | --- | --- | --- | --- | --- |
Content characteristics. K12-Train emphasizes concept definitions, procedural knowledge, and relation
explanations grounded in textbook structure, whereas GaokaoBench and EduEval primarily assess problem-
solving and applied reasoning. The difference in content form and objective further reduces the likelihood of
overlap.
Empiricalverification. Weperformn-gramoverlapanalysisbetweenK12-Trainandtheevaluationbenchmarks
and observe negligible lexical overlap. Manual inspection of sampled instances also reveals no duplicated or
| near-duplicated | question-answer | pairs. |     |     |     |     |     |
| --------------- | --------------- | ------ | --- | --- | --- | --- | --- |
Taken together, these observations indicate that K12-Train does not introduce measurable leakage into the
| evaluation | benchmarks. |     |     |     |     |     |     |
| ---------- | ----------- | --- | --- | --- | --- | --- | --- |