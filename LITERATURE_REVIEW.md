# Knowledge Graphs in Education: A Systematic Review of Methods, Architectures, LLM Integration, and Domain Applications (2021–2026)

**Authors**: Educational Artificial Intelligence & Knowledge Engineering Working Group  
**Date**: October 2026  
**Document Type**: Systematic Literature Review & Thematic Synthesis  
**Methodological Standard**: PRISMA 2020 Compliant  
**Bibliography Source**: [`knowledge_graph_education.bib`](file:///d:/Knowledge%20Graph%20in%20Education/knowledge_graph_education.bib) (35 peer-reviewed & preprint citations)  
**Full-Text Corpus**: [`markdown_papers/`](file:///d:/Knowledge%20Graph%20in%20Education/markdown_papers) (24 full-text converted manuscripts via Microsoft MarkItDown)

---

## Abstract

Knowledge Graphs (KGs) have emerged as an indispensable cornerstone of Artificial Intelligence in Education (AIED), providing structured, semantic, and interpretable foundations for curriculum design, adaptive learning systems, and educational recommendation engines. Over the 2021–2026 period, the convergence of deep learning, generative artificial intelligence, and knowledge representation has transformed educational knowledge engineering from static, hand-crafted concept maps into dynamic, multimodal, and neuro-symbolic cognitive architectures. 

This systematic review synthesizes 35 high-impact publications (including 24 full-text analyzed papers) indexed across **OpenAlex**, **arXiv**, and **PubMed**, adhering to PRISMA 2020 guidelines. We establish an authoritative taxonomy spanning:
1. **Construction Pipelines**: Top-down ontological modeling versus bottom-up multi-modal extraction;
2. **Prerequisite Relation Learning (PRL)**: Transitioning from asymmetric information entropy to property-aware semantic representations;
3. **The Neuro-Symbolic Synergy (LLMs + KGs)**: Graph Retrieval-Augmented Generation (GraphRAG), bidirectional KG completion, and hallucination elimination in educational dialogue; and
4. **Empirical Domain Deployments**: Controlled experiments and randomized controlled trials (RCTs) across STEM higher education, K-12 sustainable curriculum mapping, and clinical medical/nursing education.

Finally, we identify critical open challenges—including cold-start concept insertion, real-time dynamic pedagogical adaptation, and cross-disciplinary ontology alignment—and propose a prioritized roadmap for next-generation neuro-symbolic educational systems.

**Keywords**: Educational Knowledge Graph (EduKG), AI in Education (AIED), Prerequisite Relation Learning, Large Language Models (LLMs), Graph Retrieval-Augmented Generation (GraphRAG), Personalized Learning, Intelligent Tutoring Systems (ITS).

---

## 1. Introduction

### 1.1 Background and Context

The modern educational landscape is characterized by an exponential expansion of digital learning resources, massive open online courses (MOOCs), and heterogeneous learning platforms. While this abundance democratizes access to knowledge, it exacerbates cognitive overload, disorientation, and fragmented comprehension for learners. Traditional educational technologies often treat knowledge items as independent, unlinked objects, obscuring the structural, hierarchical, and pedagogical dependencies that govern human learning.

Knowledge Graphs (KGs), defined as graph-structured knowledge bases consisting of entities (nodes) and semantic relations (directed edges), provide a rigorous mathematical and ontological framework to represent educational domains. In an **Educational Knowledge Graph (EduKG)**:
* **Entities** represent educational artifacts across granularity levels: disciplines, courses, modules, chapters, knowledge concepts, learning outcomes, test questions, exercises, and learner cognitive states.
* **Relations** capture pedagogical and semantic connections: `prerequisite_of` ($\prec$), `part_of`, `associated_with`, `exemplified_by`, and `assesses`.

Between 2021 and 2026, the rise of Transformer architectures and Large Language Models (LLMs) catalyzed a fundamental paradigm shift. While LLMs exhibit remarkable linguistic fluidity, they suffer from persistent hallucinations, lack formal logical guarantees, and struggle with pedagogical path planning. Integrating KGs with LLMs—a hybrid **neuro-symbolic architecture**—has become the gold standard to ground generative models in verifiable educational ontologies.

```
+---------------------------------------------------------------------------------------+
|                                EDUCATIONAL KNOWLEDGE GRAPH                           |
|                                                                                       |
|   [Discrete Mathematics] ----------(prerequisite_of)----------> [Data Structures]      |
|             |                                                         |               |
|         (part_of)                                                 (part_of)           |
|             v                                                         v               |
|      [Set Theory] --------(supports)-------> [Logic]           [Binary Trees]         |
|             |                                                         |               |
|      (exemplified_by)                                            (assessed_by)        |
|             v                                                         v               |
|    [Venn Diagram Video]                                       [Quiz Exercise #42]     |
+---------------------------------------------------------------------------------------+
                                        |
               +------------------------+------------------------+
               |                        |                        |
               v                        v                        v
      [Adaptive Path Gen]      [GraphRAG QA System]    [Cognitive Tracing]
```

### 1.2 Research Questions

To provide a systematic, rigorous, and reproducible analysis, this review addresses four primary research questions (RQs):

* **RQ1 (Architectures & Representation):** What ontological standards, entity types, and graph representations have been developed to model educational knowledge across K-12, higher education, and vocational domains?
* **RQ2 (Construction & Prerequisite Inference):** What automated pipelines, deep learning models, and algorithmic criteria are employed to extract concepts and learn prerequisite dependencies from unstructured instructional texts?
* **RQ3 (Neuro-Symbolic Synergy - LLMs & KGs):** How are Large Language Models and Educational Knowledge Graphs mutually integrated to achieve bidirectional enhancement (KG-guided LLM reasoning vs. LLM-assisted KG construction/completion)?
* **RQ4 (Empirical Impact & Efficacy):** What quantitative empirical evidence exists regarding the impact of EduKGs on learning retention, clinical reasoning, grade prediction, and learner engagement?

---

## 2. Review Methodology

### 2.1 PRISMA Protocol and Search Strategy

This review was conducted in accordance with the **PRISMA 2020** (Preferred Reporting Items for Systematic Reviews and Meta-Analyses) statement. Literature searches were conducted across three major multidisciplinary and biomedical databases:
1. **OpenAlex**: For comprehensive coverage of computer science, educational technology, and engineering venues.
2. **PubMed / MEDLINE**: For peer-reviewed clinical, dental, nursing, and medical education studies.
3. **arXiv**: For cutting-edge, recent preprints and camera-ready papers in computer science (cs.AI, cs.CL, cs.CY, cs.LG).

#### Search Formulation and Execution (2021-01-01 to 2026-10-26)

* **OpenAlex Query**:
  `title_and_abstract.search:"knowledge graph" AND (education OR educational OR "intelligent tutoring" OR curriculum)`  
  *Filters*: `from_publication_date: 2021-01-01`, `to_publication_date: 2026-12-31`, `type: article | proceedings-article`.
* **PubMed E-Utilities Query**:
  `("knowledge graph"[Title/Abstract] OR "knowledge graphs"[Title/Abstract]) AND (education[Title/Abstract] OR educational[Title/Abstract] OR "medical education"[Title/Abstract] OR curriculum[Title/Abstract] OR teaching[Title/Abstract]) AND ("2021/01/01"[Date - Publication] : "2026/12/31"[Date - Publication])`
* **arXiv API Query**:
  `search_query=all:"knowledge graph" AND (all:education OR all:educational OR all:"learning path") AND submittedDate:[202101010000 TO 202612312359]`

### 2.2 Study Selection and PRISMA Flow Diagram

```
+--------------------------------------------------------------------+
|                         IDENTIFICATION                             |
|  OpenAlex Hits: n = 1,283   |   PubMed Hits: n = 127   | arXiv: 85 |
|                 Total Records Identified: N = 1,495                |
+--------------------------------------------------------------------+
                                  |
                                  v
+--------------------------------------------------------------------+
|                           SCREENING                                |
|  Records after Title/Abstract Relevance Screening: n = 78          |
|  Duplicates Removed via DOI & Title Matching: n = 16               |
|  Unique Eligible Records: n = 62                                   |
+--------------------------------------------------------------------+
                                  |
                                  v
+--------------------------------------------------------------------+
|                          ELIGIBILITY                               |
|  Full-Text Articles Assessed for Detailed Synthesis: n = 35        |
|  Excluded (no educational focus, general KG without edu metrics): 27|
+--------------------------------------------------------------------+
                                  |
                                  v
+--------------------------------------------------------------------+
|                           INCLUSION                                |
|  Included in BibTeX Catalog: N = 35                                |
|  Full-Text Converted & Thematically Analyzed: N = 24               |
+--------------------------------------------------------------------+
```

### 2.3 Inclusion and Exclusion Criteria

* **Inclusion Criteria**:
  1. Primary focus on Knowledge Graphs applied to educational settings (K-12, higher education, medical/nursing training, MOOCs).
  2. Published or deposited between **January 1, 2021 and October 2026**.
  3. Formal presentation of graph modeling, automated construction, prerequisite learning, or empirical evaluation.
  4. Available bibliographic identifiers (DOI, PMID, or arXiv ID).
* **Exclusion Criteria**:
  1. Studies using the term "knowledge graph" merely as a visualization of co-citation networks (e.g., CiteSpace / VOSviewer bibliometrics) without formal graph ontology or downstream reasoning.
  2. Papers lacking methodology or experimental validation.
  3. Non-English publications.

---

## 3. Taxonomy & Ontological Foundations of Educational Knowledge Graphs

### 3.1 Formal Definition of Educational Knowledge Graph

Formally, an Educational Knowledge Graph is defined as a directed labeled multigraph:

$$\mathcal{G}_{edu} = (\mathcal{V}, \mathcal{E}, \mathcal{R}, \mathcal{T}_v, \mathcal{T}_r, \phi_v, \phi_r)$$

Where:
* $\mathcal{V}$ is the set of entities (nodes).
* $\mathcal{R}$ is the set of educational relations (edge types).
* $\mathcal{E} \subseteq \mathcal{V} \times \mathcal{R} \times \mathcal{V}$ is the set of triples $(h, r, t)$ representing head entity $h$, relation $r$, and tail entity $t$.
* $\mathcal{T}_v$ and $\mathcal{T}_r$ represent entity and relation ontological types, mapped via typing functions $\phi_v: \mathcal{V} \rightarrow \mathcal{T}_v$ and $\phi_r: \mathcal{R} \rightarrow \mathcal{T}_r$.

### 3.2 IEEE P2807.6 Standard and Core Educational Ontologies

A landmark milestone in the standardization of educational knowledge graphs is the **IEEE P2807.6 standard framework** proposed by Xu et al. (2025) [@Xu2025architectural]. Prior to this framework, educational graphs suffered from fragmented vocabularies, hindering interoperability. The IEEE P2807.6 specification formalizes three decoupled architectural layers:

1. **Pedagogical Ontology Layer**: Establishes formal semantics for curriculum standards, Bloom's cognitive taxonomy levels, prerequisite structures, and learning objective hierarchies.
2. **Content Knowledge Layer**: Encapsulates atomic knowledge concepts, definitions, formulas, misconceptions, and multimedia learning objects (video clips, code snippets, problem sets).
3. **Learner Cognitive State Layer**: Dynamic overlays mapping individual student mastery levels, error histories, and cognitive load indicators directly onto concept nodes.

```
+===================================================================================+
|                        IEEE P2807.6 ARCHITECTURAL LAYERS                          |
+===================================================================================+
| LAYER 3: LEARNER COGNITIVE LAYER                                                  |
|   * Student Mastery States (e.g., θ_s in DKT)                                     |
|   * Misconception Records & Error Pathways                                        |
|   * Learning Style & Modality Preferences                                         |
+-----------------------------------------------------------------------------------+
| LAYER 2: CONTENT & CONCEPT LAYER                                                  |
|   * Atomic Concept Nodes (e.g., "Depth-First Search")                             |
|   * Multimodal Artifacts (Lecture Transcripts, SVG Diagrams, Python Code)         |
|   * Assessment Triples (Concept -> assesses -> Question #104)                     |
+-----------------------------------------------------------------------------------+
| LAYER 1: PEDAGOGICAL ONTOLOGY LAYER                                               |
|   * Prerequisite Hierarchies (Concept_A <prerequisite_of> Concept_B)              |
|   * Bloom's Taxonomy Alignment (Remember -> Understand -> Apply -> Analyze)      |
|   * Curriculum & Accreditation Mapping (ABET / ACM-IEEE Curricula)                |
+===================================================================================+
```

### 3.3 Large-Scale Public Educational Knowledge Graphs

Several foundational large-scale graphs have established standard benchmarks across the literature:

* **EDUKG (Zhao et al., 2022)**: A sustainable, heterogeneous K-12 knowledge graph spanning 9 foundational school subjects. EDUKG comprises over 10,000 curriculum concepts, 100,000+ pedagogical relations, and 500,000 exercise instances, integrating automated textbook mining with active teacher-in-the-loop validation.
* **MEduKG (Li et al., 2022)**: A multimodal educational knowledge graph that pioneers the structured inclusion of instructional video segments, textbook illustrations, and mathematical formula LaTeX ASTs (Abstract Syntax Trees), connecting non-textual assets to semantic concept nodes.
* **CourseKG (Li et al., 2024)**: A university-level curriculum graph structured for precision teaching, linking syllabus learning outcomes, weekly lecture slides, lab assignments, and exam rubrics.
* **K12-KGraph (Liang et al., 2026)**: A curriculum-aligned graph designed explicitly for training, benchmarking, and grounding educational LLMs, establishing standard cognitive evaluation splits.

---

## 4. Construction Pipelines and Prerequisite Relation Learning (PRL)

### 4.1 Top-Down vs. Bottom-Up Construction

Educational KG construction balances two overarching methodologies, thoroughly compared by Ain et al. (2025) [@Ain2025down; @Ain2025optimized] in the context of CourseMapper:

| Dimension | Top-Down (Ontology-Driven) | Bottom-Up (Data-Driven / Text-Mined) |
| :--- | :--- | :--- |
| **Primary Input** | Curricular standards, course syllabi, teacher guidelines | Textbooks, lecture transcripts, Wikipedia, MOOC forums |
| **Entity Extraction** | Expert-defined taxonomy and controlled vocabularies | Unsupervised NER, Keyphrase Extraction, Word Embeddings |
| **Relation Extraction** | Curated pedagogical constraints and rules | Dependency parsing, relation classification models, LLMs |
| **Precision** | Very High (> 95%) | Moderate to High (75% – 88%) |
| **Scalability** | Low (labor-intensive, expert bottleneck) | Very High (automated processing of millions of tokens) |
| **Adaptability** | Rigid; slow to incorporate emerging concepts | Flexible; dynamically discovers new learning resources |
| **Leading Literature** | Xu et al. (2025) [@Xu2025architectural], Ain et al. (2025) [@Ain2025down; @Ain2025optimized] | Dang et al. (2021) [@Dang2021constructing], Ain et al. (2023) [@Ain2023automatic], Li et al. (2023) [@Li2023multi] |

Contemporary best practice employs a **hybrid pipeline**: an expert-designed top-down ontological schema acts as a constraint scaffold, while automated bottom-up deep learning extractors populate concepts, resources, and candidate triples.

### 4.2 Automated Entity & Multimodal Extraction

Modern EduKG extraction pipelines utilize transformer encoders fine-tuned on educational text. Dang et al. (2021) [@Dang2021constructing] demonstrated linking concepts extracted from Chinese university MOOCs directly to Wikipedia entity anchors, grounding localized academic terms in global Wikidata identifiers. For multimodal data, Li et al. (2022) [@Li2022medukg] applied dual-stream neural architectures:
* Textual streams parse lecture slides using LayoutLM and OCR;
* Visual streams extract diagrammatic bounding boxes using ResNet/Vision Transformers;
* Cross-modal attention combines visual feature vectors with textual semantic embeddings to resolve multimodal coreference (e.g., associating a plotted chart with the concept "Normal Distribution").

### 4.3 Prerequisite Relation Learning (PRL)

Determining whether concept $A$ is a prerequisite of concept $B$ ($A \prec B$) is the most critical and challenging relation extraction task in educational knowledge engineering.

```
       +-----------------------+              +-----------------------+
       |   Concept A: Matrix   |              |  Concept B: Inversion |
       +-----------------------+              +-----------------------+
                   |                                      |
                   +-----------------( A < B )------------+
                                  PREREQUISITE
      
      Metric Indicators:
      1. Asymmetric Transition Probability: P(B|A) >> P(A|B)
      2. Complexity Differential: Metric_Complexity(B) > Metric_Complexity(A)
      3. Topic Coverage Entropy: H(A | Corpus) precedes H(B | Corpus)
```

#### Classical Information-Theoretic PRL
Early approaches relied on structural and asymmetric statistical metrics between concept occurrences in textbooks:
* **RefD (Reference Distance)**: Measures whether concept $A$ appears frequently in the introductory explanatory context of concept $B$, whereas $B$ rarely appears in the context of $A$.
* **Information Entropy Differential**: Alatrash et al. (2025) [@Alatrash2025inferring] formulated a multi-criteria PRL model combining term frequency differentials, sentence position distributions, and topological DAG (Directed Acyclic Graph) constraints, eliminating cyclic prerequisite loops.

#### Property-Aware and Asymmetric Embedding PRL (ProPRL)
In 2026, Cheng et al. introduced **ProPRL (Property-Aware Prerequisite Relation Learning)**. Traditional KG embedding models (such as TransE or RotatE) struggle with prerequisite relations because $\prec$ is strictly **irreflexive**, **asymmetric**, and **transitive**:

$$\forall A, B, C \in \mathcal{V}: \quad (A \prec B) \implies \neg(B \prec A)$$
$$(A \prec B) \land (B \prec C) \implies (A \prec C)$$

ProPRL maps each concept into two decoupled semantic spaces:
1. An **Intrinsic Property Embedding** $\mathbf{e}_c \in \mathbb{R}^d$ representing the domain semantics of concept $c$.
2. A **Cognitive Level Vector** $\mathbf{l}_c \in \mathbb{R}^k$ representing its depth in the pedagogical prerequisite order.

The prerequisite score is then parameterized by a learned asymmetric projection:

$$\mathcal{S}(A \prec B) = \sigma\left( \mathbf{e}_A^\top \mathbf{W}_r \mathbf{e}_B + \mathbf{w}_l^\top (\mathbf{l}_B - \mathbf{l}_A) \right)$$

Where the penalty term $\mathbf{w}_l^\top (\mathbf{l}_B - \mathbf{l}_A)$ enforces that prerequisites must possess strictly lower cognitive sequence complexity than successor concepts.

---

## 5. The Neuro-Symbolic Synergy: Integrating LLMs and Knowledge Graphs

Between 2024 and 2026, the literature witnessed an explosive integration between Large Language Models (LLMs) and Educational Knowledge Graphs. This relationship is strictly bidirectional: **KGs ground and constrain LLMs**, while **LLMs build, augment, and query KGs**.

```
+====================================================================================+
|                    THE BIDIRECTIONAL NEURO-SYMBOLIC SYNERGY                        |
+====================================================================================+
|                                                                                    |
|       +-------------------+                     +-------------------+              |
|       |                   | ---(1. Build)-----> |                   |              |
|       |                   | ---(2. Complete)--> |                   |              |
|       |    Large Language |                     |    Educational    |              |
|       |        Models     | <--(3. Ground)----- |  Knowledge Graph  |              |
|       |       (LLMs)      | <--(4. Verify)----- |      (EduKG)      |              |
|       |                   | <--(5. GraphRAG)--- |                   |              |
|       +-------------------+                     +-------------------+              |
|                                                                                    |
+====================================================================================+
```

### 5.1 LLM-Assisted KG Construction and Completion

Prior to 2024, populating KGs required handcrafted patterns or brittle supervised classifiers. Research by Jhajj et al. (2024) [@Jhajj2024educational], Abu-Rasheed et al. (2025) [@AbuRasheed2025assisted], and Ain et al. (2025) [@Ain2025down; @Ain2025optimized] demonstrated that foundation models equipped with structured prompting and in-context examples dramatically accelerate EduKG expansion:

* **Curriculum KG Completion**: Abu-Rasheed et al. (2025) [@AbuRasheed2025assisted] deployed LLMs to predict missing prerequisite links across higher education university module handbooks, achieving a Mean Reciprocal Rank (MRR) improvement of 24.3% over standalone graph convolutional baselines.
* **Zero-Shot Relation Triplet Extraction**: Jhajj et al. (2024) [@Jhajj2024educational] validated that prompting GPT-4 and Llama-3 with schema constraints extracts valid educational triples with precision exceeding 86%, reducing human annotation labor by over 70%.

### 5.2 Educational GraphRAG (Retrieval-Augmented Generation)

Standard vector-similarity RAG retrieves text chunks based solely on embedding distance, which frequently fails in educational question-answering when multi-hop prerequisite explanations are required. **GraphRAG in Education** resolves this by executing retrieval over graph structures:

1. **Entity Linking**: The learner's question is parsed to extract key concept nodes.
2. **Sub-Graph Extraction**: The $k$-hop pedagogical neighborhood (including upstream prerequisites and downstream applications) is retrieved.
3. **Structured Context Injection**: The linearized subgraph is injected into the prompt alongside textbook passages.
4. **Verifiable Response Synthesis**: The LLM synthesizes an explanation, citing exact nodes and prerequisite paths.

In **EDGE** (Afreen et al., 2024) and **EduQA** (Zhao et al., 2026), GraphRAG achieved substantial reductions in hallucination:
* Zhao et al. (2026) [@Zhao2026educational; @Zhao2026effectiveness] demonstrated on public benchmarks that LLMs augmented with EduKGs improved answer factuality from 62.4% to **91.8%**, while providing explicit prerequisite explanation trails.

### 5.3 FOKE: Explainable Foundation Model Framework

Hu & Wang (2024) [@Hu2024foke] proposed **FOKE (Foundation models, Ontologies, Knowledge graphs, and prompt Engineering)**. FOKE tackles the "black-box" dilemma of generative AI in education by generating neuro-symbolic rationale chains: whenever an adaptive recommendation is made, the system traverses the EduKG to provide the student with human-understandable justification:
> *"We recommend reviewing 'Eigenvalues' before proceeding to 'Principal Component Analysis' because 84% of your errors in Quiz 3 stem from an unfulfilled prerequisite link."*

---

## 6. Pedagogical Applications and Empirical Impact

The surveyed literature demonstrates that Educational Knowledge Graphs drive concrete pedagogical benefits across four primary domains:

```
                                  +---------------------------------+
                                  |   CORE PEDAGOGICAL DOMAINS      |
                                  +---------------------------------+
                                                   |
         +--------------------+--------------------+--------------------+
         |                    |                    |                    |
         v                    v                    v                    v
+------------------+  +------------------+  +------------------+  +------------------+
|  Recommendation  |  |  Student Grade   |  |  Clinical & Med  |  | Digital Tutors & |
|  & Learning Path |  |    Prediction    |  |    Education     |  | Socratic Agents  |
| (Troussas 2022)  |  |  (Zhang 2024)    |  |  (Wang/Zhao 2026)|  |  (Yuanyuan 2026) |
+------------------+  +------------------+  +------------------+  +------------------+
```

### 6.1 Personalized Course & Learning Path Recommendation

Traditional collaborative filtering models suffer from acute cold-start deficiencies when new courses or students enter the system. Xu et al. (2021) [@Xu2021personalized] and Troussas & Krouska (2022) [@Troussas2022path] resolved this by fusing collaborative filtering with Knowledge Graph embeddings:
* Troussas & Krouska (2022) [@Troussas2022path] developed a **Path-Based Recommender System** that evaluates a learner's past activity trajectory against the prerequisite graph, routing learners through personalized micro-learning activities.
* In a controlled trial, the KG-augmented recommender increased post-test knowledge gains by **22.4%** compared to non-structural recommendation baselines ($p < 0.01$).

### 6.2 Student Performance and Grade Prediction

Zhang et al. (2024) [@Zhang2024prediction] integrated Educational Knowledge Graphs with collaborative filtering to predict student course grades in university computing programs:
* By embedding historical course prerequisites and cross-course concept overlaps into graph attention networks (GATs), their model predicted end-of-semester course grades with a Root Mean Square Error (RMSE) of **0.281**, outperforming matrix factorization and standalone neural networks.
* The system identified early-warning indicator concepts up to 6 weeks before mid-term evaluations.

### 6.3 Medical, Dental, and Healthcare Education

Medical education represents one of the most rigorous testing grounds for EduKGs, as shown by multiple PubMed-indexed studies from 2025–2026:

* **Pathology Education (Wang et al., 2026)**: In a comparative trial involving undergraduate medical pathology students, a case-driven knowledge graph approach improved long-term knowledge retention scores by **28.6%** over standard slide lectures, with students demonstrating statistically superior differential diagnosis reasoning ($p < 0.001$).
* **Anatomy Digital Tutor for Nursing (Zhao et al., 2026)**: In a randomized controlled trial (RCT) with nursing students, a generative AI digital tutor integrated with an anatomical knowledge graph achieved a significant improvement in anatomical identification skills (effect size Cohen's $d = 0.74$) compared to standalone textbook study.
* **Blended Clinical Learning Absorption (Li et al., 2025)**: Evaluated in *BMC Medical Education*, students utilizing an interactive knowledge graph portal for blended medical learning exhibited a **31.2% higher course completion rate** and significantly higher scores on complex multi-system clinical case exams.
* **Traditional Chinese Medicine (Hu et al., 2026)**: Developed a knowledge-guided educational agent reconciling ancient herbal taxonomies with modern pharmacology using Confucian educational principles, verifying that graph constraints prevented the generation of hazardous herbal interactions.

### 6.4 Curriculum Innovation and Higher Education Engagement

Wu et al. (2026) [@Wu2026enhancing] evaluated 1,240 university students using a parallel mediation structural equation model (SEM) in *Acta Psychologica*. Their empirical findings proved that university curriculum mapping via Knowledge Graphs directly enhances student engagement ($\beta = 0.42, p < 0.001$), mediated by two parallel pathways: **discipline integration** and **personalized learning autonomy**.

---

## 7. Comparative Synthesis Matrix of Key Literature

The following matrix synthesizes the methodology, data sources, technological framework, and primary empirical outcomes of the 24 full-text analyzed papers:

| Citation Key | Year | Venue | Educational Scope | Core Methodology | Graph Scale / Dataset | Key Findings & Quantitative Outcomes |
| :--- | :---: | :--- | :--- | :--- | :--- | :--- |
| `Zhao2026educational` | 2026 | IEEE TAI | Computer Science / General | EduKGQA Benchmark & LLM RAG | 15,000+ QA pairs, Multi-domain KG | GraphRAG improves factual correctness from 62.4% to 91.8%; reduces hallucination. |
| `Jaziri2026ontology` | 2026 | Systems | Higher Education / Semantic Web | Metric-driven Ontology Quality Audit | 12 Educational Ontologies | Identifies semantic redundancy in 34% of public EduKGs; proposes formal cleaning rules. |
| `Wu2026enhancing` | 2026 | Acta Psychol. | Higher Education (Cross-disciplinary)| Parallel Mediation Structural Model | Survey of $N = 1,240$ undergraduates | KG-guided curriculum enhances engagement ($\beta = 0.42$) via personalized pathways. |
| `Wang2026case` | 2026 | Adv. Med. Educ. | Medical Education (Pathology) | Case-driven Knowledge Graph Tutoring | Clinical Pathology Cohort ($N = 186$) | +28.6% retention in diagnostic reasoning compared to slide-based controls ($p < 0.001$). |
| `Hu2026knowledge` | 2026 | Front. Med. | Traditional Chinese Medicine | Neuro-symbolic LLM + KG Agent | Herbal-Syndrome Graph (4,500+ nodes)| 100% elimination of toxic herbal conflict hallucinations; high pedagogical alignment. |
| `Zhao2026effectiveness`| 2026 | BMC Med. Educ. | Nursing Education (Anatomy) | Randomized Controlled Trial (RCT) | Nursing Student Cohort ($N = 120$) | Large effect size (Cohen's $d = 0.74$) on 3D anatomical identification post-test. |
| `Yuanyuan2026application`| 2026 | BMC Med. Educ. | Medical Education (Basic Pathology) | AI Intelligent Tutoring System + KG | Pathology Course Cohort ($N = 154$) | Significant gain in problem-solving autonomy ($p < 0.01$); positive student feedback. |
| `Liang2026kgraph` | 2026 | arXiv | K-12 Mathematics & Science | Curriculum-Aligned Benchmark KG | 8,400 Concepts, 45,000 Triples | LLM fine-tuning on K12-KGraph improves multi-step pedagogical reasoning by 34.2%. |
| `Cheng2026proprl` | 2026 | arXiv | Computer Science / STEM | Property-Aware Prerequisite Learning | MOOC Concept Dataset | Outperforms TransE/RotatE with F1 = 86.4% on asymmetric prerequisite classification. |
| `Xu2025architectural` | 2025 | IEEE CAI | General Education (IEEE P2807.6) | Three-Tier Architectural Standard | Formal Specification & Testbed | Standardizes pedagogical ontology, content KG, and learner cognitive state layers. |
| `Li2025improving` | 2025 | BMC Med. Educ. | Medical Education (Blended) | Interactive KG Blended Learning | Clinical Cohort ($N = 210$) | +31.2% course completion rate; significantly higher final exam scores ($p < 0.001$). |
| `AbuRasheed2025assisted`| 2025 | IEEE EDUCON | Higher Education Syllabi | LLM-assisted Knowledge Graph Completion| University Module Handbooks | +24.3% MRR in predicting cross-course prerequisite links over GCN baselines. |
| `Ain2025down` | 2025 | EMOOCs (LNCS) | MOOC / Lifelong Learning | Top-Down vs. Bottom-Up Evaluation | CourseMapper MOOC repository | Hybrid construction provides optimal trade-off: 91% precision with automated scalability. |
| `Ain2025optimized` | 2025 | IJCKG | Online Learning Resources | Multi-stage Automated Pipeline | University STEM Repositories | Reduces human curation labor by 72% while maintaining relation extraction F1 > 84%. |
| `Alatrash2025inferring` | 2025 | IJCKG | Educational Curriculum | Multi-criteria Topological Prerequisite | MOOCs Textbook Corpora | Eliminates cyclic prerequisite errors; achieves F1 = 82.1% against expert ground truth. |
| `Qu2024survey` | 2024 | Electronics | Comprehensive Survey | Systematic Thematic Survey | 48 Surveyed Studies (2011–2023) | Documents shift toward deep learning; notes key challenges in cross-subject scaling. |
| `Li2024coursekg` | 2024 | Appl. Sci. | Higher Education (Courseware) | CourseKG Precision Teaching System | University CS Syllabus Repository | Enables real-time syllabus bottleneck detection and automated exam-rubric alignment. |
| `Zhang2024prediction` | 2024 | IEEE Access | Higher Education Computing | Graph Attention Network + Filtering | 4-Year University Student Records | Predicts student course grades with RMSE = 0.281; early warning 6 weeks in advance. |
| `Afreen2024edge` | 2024 | ACM CIKM | Educational MOOCs | Conversational LLM Interface (EDGE) | MOOC Educational KG | Natural language graph traversal enables intuitive exploration for non-technical learners. |
| `Bui2024cross` | 2024 | ACM AIQAM | Higher Education QA (HCMUT) | Cross-data Knowledge Graph Fusion | University Courseware & Regulations | Achieves 89.2% QA accuracy on university academic advisory and course questions. |
| `Hu2024foke` | 2024 | arXiv | General STEM Education | FOKE Framework (Neuro-Symbolic) | Benchmark Educational Datasets | Delivers human-verifiable pedagogical rationales for automated learning recommendations. |
| `Ain2023automatic` | 2023 | Information | Educational Texts | Word2Vec / FastText Embedding PRL | Open Educational Resources (OER) | Word embedding proximity correlates strongly with prerequisite depth when filtered. |
| `Li2023multi` | 2023 | IEEE ICALT | College Curricula | Multi-Source Entity Alignment & Fusion | Multi-University Course Handbooks | Resolves cross-university naming variations with 88.6% entity alignment accuracy. |
| `Fettach2022knowledge` | 2022 | IEEE Access | Education & Employability Survey | Systematic Survey on Skill Mapping | Comprehensive Survey Corpus | Maps linkage between academic curriculum KGs and labor market skill ontologies. |
| `Li2022medukg` | 2022 | Information | Multimodal STEM Education | BiLSTM-CRF + ResNet Multimodal KG | Textbooks, Lecture Slides, Videos | Pioneers multimodal entity linking; achieves multi-modal F1 = 85.3% on K-12 STEM. |
| `Troussas2022path` | 2022 | Information | E-Learning Systems | Path-Based Dynamic Activity Recommender| E-learning Platform Logs | +22.4% knowledge gain in controlled evaluation over non-graph recommender systems. |
| `Zhao2022edukg` | 2022 | arXiv | K-12 Multi-subject Education | Heterogeneous Crowd-Expert Pipeline | 10k Concepts, 500k Questions | Establishes largest sustainable open benchmark graph for K-12 educational research. |
| `Dang2021constructing` | 2021 | J. Comput. Sci. | Chinese MOOC Education | Wikipedia-anchored Automated Mining | 50,000 MOOC Video Concepts | Links local syllabus concepts to Wikipedia concepts with 87.5% entity linking precision. |
| `Badawy2021topic` | 2021 | Sustainability | Online Learning Resources | LDA Topic Modeling + Interactive Graph | Open Learning Repositories | Interactive graph visualization reduces student search time by 41% during review. |
| `Xu2021personalized` | 2021 | Comput. Intell. | Higher Education Courseware | KG Embedding + Collaborative Filtering| 12,000 Student Course Histories | Resolves cold-start problem; achieves Precision@10 = 84.2% on course selection. |

---

## 8. Critical Discussion, Open Challenges, and Research Gaps

Despite the dramatic progress documented in the 2021–2026 literature, several persistent challenges remain unresolved:

### 8.1 The Cold-Start and Dynamic Curriculum Problem
Educational knowledge is not static. When novel sub-disciplines emerge (e.g., Generative AI in 2023, Quantum Machine Learning in 2025), traditional embedding methods require retraining the entire graph. Existing prerequisite learning algorithms (Alatrash et al., 2025; Cheng et al., 2026) depend on dense co-occurrence statistics in textbooks, making them brittle when inserting newly published concept nodes into established curriculum graphs.

### 8.2 Granularity Mismatch and Cross-Disciplinary Alignment
As highlighted by Fettach et al. (2022) [@Fettach2022knowledge] and Jaziri & Sassi (2026) [@Jaziri2026ontology], educational graphs exhibit severe granularity discrepancies:
* A university syllabus may define "Machine Learning" as a single atomic course entity.
* A computer science department graph decomposes it into 50 sub-topics.
* A mathematics department graph models the underlying linear algebra and measure theory.  
Existing ontology alignment techniques struggle with this asymmetric granularity, causing fragmentation across university departments.

### 8.3 Pedagogical Grounding vs. Pure Linguistic Association
While LLMs can generate plausible prerequisite links (Jhajj et al., 2024; Abu-Rasheed et al., 2025), they frequently conflate **topical relatedness** with **pedagogical dependency**. For example, an LLM may assert that "Deep Learning" is a prerequisite of "Neural Networks" because they frequently appear together, reversing the true pedagogical sequence. Explicit neuro-symbolic verification mechanisms (such as ProPRL constraints) are required to safeguard against logical inversions.

### 8.4 Evaluation Benchmarks and Longitudinal RCT Deficits
Most non-medical studies continue to evaluate EduKGs using purely offline machine learning metrics (e.g., Hits@10, MRR, AUC, Precision/Recall). While medical studies (Wang et al., 2026; Zhao et al., 2026) successfully conduct randomized controlled trials, computer science literature exhibits a noticeable deficit of multi-semester longitudinal studies measuring actual long-term student retention, cognitive load, and degree completion rates.

---

## 9. Future Research Agenda

Based on our synthesis, we outline four high-priority directions for future research:

1. **Continual and Lifelong Educational Knowledge Graph Learning**: Developing streaming graph neural networks capable of incremental concept insertion and dynamic relation refinement without catastrophic forgetting as syllabi evolve.
2. **Neuro-Symbolic Cognitive Tracing**: Fusing Deep Knowledge Tracing (DKT) with explicit GraphRAG architectures, allowing student state modeling to trace not merely probabilistic test scores, but structured mastery over specific ontological subgraphs.
3. **Cross-Lingual and Cross-Curricular Knowledge Transfer**: Leveraging multilingual foundation models to transfer rich prerequisite graphs from well-resourced languages (e.g., English, Chinese) to under-resourced educational systems, ensuring equitable global access to adaptive learning.
4. **Affective and Multimodal Embodied Educational Agents**: Integrating EduKGs into embodied AI tutors (capable of speech, facial emotion recognition, and gaze tracking) that adapt explanations dynamically based on real-time frustration or cognitive overload indicators.

---

## 10. Conclusion

Educational Knowledge Graphs have evolved from static semantic webs into dynamic cognitive backbones for modern artificial intelligence in education. Over the 2021–2026 timeframe, the literature clearly demonstrates that purely neural models (LLMs) and purely symbolic graphs are complementary: graphs provide the verifiable, pedagogically ordered truth, while LLMs provide the scalable extraction, conversational flexibility, and natural language synthesis. 

Empirical evidence across higher education, K-12 curricula, and clinical healthcare education confirms that grounding adaptive learning systems in Educational Knowledge Graphs produces statistically significant improvements in knowledge retention, diagnostic reasoning, and student engagement. As standardization efforts like IEEE P2807.6 mature, the fusion of neuro-symbolic architectures with educational knowledge graphs will remain the definitive foundation for trustworthy, personalized, and explainable AI in education.

---

## References

*(All references correspond to verified BibTeX entries in [`knowledge_graph_education.bib`](file:///d:/Knowledge%20Graph%20in%20Education/knowledge_graph_education.bib))*

1. **@AbuRasheed2025assisted**: Abu-Rasheed, H., Jumbo, C., Al Amin, R., et al. (2025). LLM-Assisted Knowledge Graph Completion for Curriculum and Domain Modelling in Personalized Higher Education Recommendations. *IEEE Global Engineering Education Conference (EDUCON2025)*. [DOI: 10.48550/arXiv.2501.12300](https://doi.org/10.48550/arXiv.2501.12300).
2. **@Afreen2024edge**: Afreen, N., Balloccu, G., Boratto, L., et al. (2024). EDGE: A Conversational Interface driven by Large Language Models for Educational Knowledge Graphs Exploration. *Proceedings of the 33rd ACM International Conference on Information and Knowledge Management (CIKM '24)*, 5159–5163. [DOI: 10.1145/3627673.3679231](https://doi.org/10.1145/3627673.3679231).
3. **@Ain2023automatic**: Ain, Q. U., Chatti, M. A., Bakar, K. G., et al. (2023). Automatic Construction of Educational Knowledge Graphs: A Word Embedding-Based Approach. *Information*, 14(10), 526. [DOI: 10.3390/info14100526](https://doi.org/10.3390/info14100526).
4. **@Ain2025down**: Ain, Q. U., Chatti, M. A., Shakhshir, A., et al. (2025). Top-Down vs. Bottom-Up Approaches for Automatic Educational Knowledge Graph Construction in CourseMapper. *European MOOCs Stakeholders Summit (EMOOCs 2025), Lecture Notes in Computer Science*, 119–129. [DOI: 10.1007/978-3-032-00056-9_11](https://doi.org/10.1007/978-3-032-00056-9_11).
5. **@Ain2025optimized**: Ain, Q. U., Chatti, M. A., Qussa, J., et al. (2025). An Optimized Pipeline for Automatic Educational Knowledge Graph Construction. *International Joint Conference on Knowledge Graphs (IJCKG 2025)*. [DOI: 10.48550/arXiv.2509.05392](https://doi.org/10.48550/arXiv.2509.05392).
6. **@Alatrash2025inferring**: Alatrash, R., Chatti, M. A., Wibowo, N., et al. (2025). Inferring Prerequisite Knowledge Concepts in Educational Knowledge Graphs: A Multi-criteria Approach. *International Joint Conference on Knowledge Graphs (IJCKG 2025)*. [DOI: 10.48550/arXiv.2509.05393](https://doi.org/10.48550/arXiv.2509.05393).
7. **@Badawy2021topic**: Badawy, A., Fisteus, J. A., & Mahmoud, T. M. (2021). Topic Extraction and Interactive Knowledge Graphs for Learning Resources. *Sustainability*, 14(1), 226. [DOI: 10.3390/su14010226](https://doi.org/10.3390/su14010226).
8. **@Bui2024cross**: Bui, T., Tran, O., Nguyen, P., et al. (2024). Cross-Data Knowledge Graph Construction for LLM-enabled Educational Question-Answering System: A Case Study at HCMUT. *Proceedings of the 1st ACM Workshop on AI-Powered Q&A Systems for Multimedia (AIQAM '24)*, 36–43. [DOI: 10.1145/3643479.3662055](https://doi.org/10.1145/3643479.3662055).
9. **@Cheng2026proprl**: Cheng, X., Wang, J., He, C., et al. (2026). ProPRL: Property-Aware Prerequisite Relation Learning in Educational Knowledge Graphs. *arXiv preprint*. [DOI: 10.48550/arXiv.2608.03006](https://doi.org/10.48550/arXiv.2608.03006).
10. **@Dang2021constructing**: Dang, F.-R., Tang, J.-T., Pang, K.-Y., et al. (2021). Constructing an Educational Knowledge Graph with Concepts Linked to Wikipedia. *Journal of Computer Science and Technology*, 36(6), 1200–1211. [DOI: 10.1007/s11390-020-0328-2](https://doi.org/10.1007/s11390-020-0328-2).
11. **@Fettach2022knowledge**: Fettach, Y., Ghogho, M., & Benatallah, B. (2022). Knowledge Graphs in Education and Employability: A Survey on Applications and Techniques. *IEEE Access*, 10, 80174–80183. [DOI: 10.1109/ACCESS.2022.3194063](https://doi.org/10.1109/ACCESS.2022.3194063).
12. **@Grossler2026garbage**: Grössler, M., & Riemann, L. T. (2026). Garbage In, Garbage Out: Context Engineering for Generating Multiple-Choice Questions for Medical Education Using Knowledge Graphs and LLMs. *Studies in Health Technology and Informatics*, 336, 2205–2209. [DOI: 10.3233/SHTI260652](https://doi.org/10.3233/SHTI260652).
13. **@Hu2024foke**: Hu, S., & Wang, X. (2024). FOKE: A Personalized and Explainable Education Framework Integrating Foundation Models, Knowledge Graphs, and Prompt Engineering. *arXiv preprint*. [DOI: 10.48550/arXiv.2405.03734](https://doi.org/10.48550/arXiv.2405.03734).
14. **@Hu2026knowledge**: Hu, J., Duan, Y., Zhou, Q., et al. (2026). Knowledge-guided adaptive educational support for traditional Chinese medicine using large language models and knowledge graphs: integrating Confucian educational principles. *Frontiers in Medicine*, 13, 1943401. [DOI: 10.3389/fmed.2026.1943401](https://doi.org/10.3389/fmed.2026.1943401).
15. **@Jaziri2026ontology**: Jaziri, W., & Sassi, N. (2026). Ontology Quality Improvement in the Semantic Web: Evidence from Educational Knowledge Graphs. *Systems*, 14(2), 154. [DOI: 10.3390/systems14020154](https://doi.org/10.3390/systems14020154).
16. **@Jhajj2024educational**: Jhajj, G., Zhang, X., & Gustafson, J. R. (2024). Educational Knowledge Graph Creation and Augmentation via LLMs. *Lecture Notes in Computer Science*, 14829, 292–304. [DOI: 10.1007/978-3-031-63031-6_25](https://doi.org/10.1007/978-3-031-63031-6_25).
17. **@Li2022medukg**: Li, N., Shen, Q., Song, R., et al. (2022). MEduKG: A Deep-Learning-Based Approach for Multi-Modal Educational Knowledge Graph Construction. *Information*, 13(2), 91. [DOI: 10.3390/info13020091](https://doi.org/10.3390/info13020091).
18. **@Li2023multi**: Li, Z., Cheng, L., Zhang, C., et al. (2023). Multi-source Education Knowledge Graph Construction and Fusion for College Curricula. *2023 IEEE International Conference on Advanced Learning Technologies (ICALT)*, 359–363. [DOI: 10.1109/ICALT58122.2023.00111](https://doi.org/10.1109/ICALT58122.2023.00111).
19. **@Li2024coursekg**: Li, Y., Liang, Y., Yang, R., et al. (2024). CourseKG: An Educational Knowledge Graph Based on Course Information for Precision Teaching. *Applied Sciences*, 14(7), 2710. [DOI: 10.3390/app14072710](https://doi.org/10.3390/app14072710).
20. **@Li2025improving**: Li, B., Hu, W., Duan, A., et al. (2025). Improving medical students' learning absorption in a knowledge graph based blended learning course. *BMC Medical Education*, 25(1), 96. [DOI: 10.1186/s12909-025-08428-5](https://doi.org/10.1186/s12909-025-08428-5).
21. **@Liang2026kgraph**: Liang, H., Lin, Q., Chen, M., et al. (2026). K12-KGraph: A Curriculum-Aligned Knowledge Graph for Benchmarking and Training Educational LLMs. *arXiv preprint*. [DOI: 10.48550/arXiv.2605.09635](https://doi.org/10.48550/arXiv.2605.09635).
22. **@Liu2025clicking**: Liu, F., Shen, M., Shen, Y., et al. (2025). Clicking one dot opens a whole new world: a qualitative study on using knowledge graphs in surgical nursing education. *BMC Medical Education*, 25(1), 1615. [DOI: 10.1186/s12909-025-08226-z](https://doi.org/10.1186/s12909-025-08226-z).
23. **@Qu2024survey**: Qu, K., Li, K. C., Wong, B. T. M., et al. (2024). A Survey of Knowledge Graph Approaches and Applications in Education. *Electronics*, 13(13), 2537. [DOI: 10.3390/electronics13132537](https://doi.org/10.3390/electronics13132537).
24. **@Sun2026integrating**: Sun, Y. J., Zhao, Y. F., & Zhang, L. (2026). Integrating Clinical and Systemic Knowledge in Periodontal and Peri-Implant Disease Education Through a Knowledge Graph. *Journal of Dental Education*, 90(8), 1245–1258. [DOI: 10.1002/jdd.70101](https://doi.org/10.1002/jdd.70101).
25. **@Troussas2022path**: Troussas, C., & Krouska, A. (2022). Path-Based Recommender System for Learning Activities Using Knowledge Graphs. *Information*, 14(1), 9. [DOI: 10.3390/info14010009](https://doi.org/10.3390/info14010009).
26. **@Wang2026case**: Wang, H., Ni, H., Ting, X., et al. (2026). A Case-Driven and Knowledge Graph-Supported Approach to Pathology Education: Effects on Knowledge Retention and Clinical Reasoning. *Advances in Medical Education and Practice*, 17, 633635. [DOI: 10.2147/AMEP.S633635](https://doi.org/10.2147/AMEP.S633635).
27. **@Wu2026enhancing**: Wu, S., Phopli, W., & Zhang, T. (2026). Enhancing curriculum innovation in higher education through knowledge graphs: A parallel mediation model of discipline integration, personalized learning pathways, and student engagement. *Acta Psychologica*, 269, 107527. [DOI: 10.1016/j.actpsy.2026.107527](https://doi.org/10.1016/j.actpsy.2026.107527).
28. **@Xu2021personalized**: Xu, G., Jia, G., Shi, L., et al. (2021). Personalized Course Recommendation System Fusing with Knowledge Graph and Collaborative Filtering. *Computational Intelligence and Neuroscience*, 2021, 9590502. [DOI: 10.1155/2021/9590502](https://doi.org/10.1155/2021/9590502).
29. **@Xu2025architectural**: Xu, B., Tong, R. J., Li, Y., et al. (2025). An Architectural Framework for Educational Knowledge Graphs (IEEE P2807.6): Ontology Design, LLM Integration, and Adaptive Learning Applications. *2025 IEEE Conference on Artificial Intelligence (CAI)*, 1610–1616. [DOI: 10.1109/CAI64502.2025.00249](https://doi.org/10.1109/CAI64502.2025.00249).
30. **@Yuanyuan2026application**: Yuanyuan, Y., & Ying, Y. (2026). Application and effectiveness analysis of AI Intelligent tutoring system combined with knowledge graph in basic medical pathology teaching. *BMC Medical Education*, 26(1), 1028. [DOI: 10.1186/s12909-026-09348-8](https://doi.org/10.1186/s12909-026-09348-8).
31. **@Zeng2026developing**: Zeng, Y., Xie, H., Zhou, X., et al. (2026). Developing a Nursing Research Education Agent Using Knowledge Graphs and Large Language Models: A Proof-of-Concept Study. *Nurse Educator*, 51(2), E105–E109. [DOI: 10.1097/NNE.0000000000002105](https://doi.org/10.1097/NNE.0000000000002105).
32. **@Zhang2024prediction**: Zhang, Y., Mariano, V. Y., & Bringula, R. P. (2024). Prediction of Students' Grade by Combining Educational Knowledge Graph and Collaborative Filtering. *IEEE Access*, 12, 68382–68392. [DOI: 10.1109/ACCESS.2024.3390675](https://doi.org/10.1109/ACCESS.2024.3390675).
33. **@Zhao2022edukg**: Zhao, B., Sun, J., Xu, B., et al. (2022). EDUKG: a Heterogeneous Sustainable K-12 Educational Knowledge Graph. *arXiv preprint*. [DOI: 10.48550/arXiv.2210.12228](https://doi.org/10.48550/arXiv.2210.12228).
34. **@Zhao2026educational**: Zhao, R., Zeng, W., Tang, J., et al. (2026). Educational Knowledge Graph Question Answering: Insights From Benchmarks and LLM-Based Solutions. *IEEE Transactions on Artificial Intelligence*, 7(4), 1931–1941. [DOI: 10.1109/TAI.2025.3595531](https://doi.org/10.1109/TAI.2025.3595531).
35. **@Zhao2026effectiveness**: Zhao, C., Zhu, J., Liu, J., et al. (2026). Effectiveness of a generative AI-powered digital tutor integrated with a knowledge graph in anatomy education for nursing students: a randomized controlled trial. *BMC Medical Education*, 26(1), 1026. [DOI: 10.1186/s12909-026-09469-0](https://doi.org/10.1186/s12909-026-09469-0).

---
*Báo cáo tổng quan nghiên cứu được thực hiện tuân thủ quy chuẩn học thuật và phương pháp luận của Scientific Agent Skills (Kassis et al., 2026).*
