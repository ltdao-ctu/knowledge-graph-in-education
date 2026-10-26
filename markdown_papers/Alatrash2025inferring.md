---
title: "Alatrash2025inferring"
source: "Alatrash2025inferring.pdf"
source_sha256: "888a1888cd5a087514b11f654b628a4f09c32970ddaa7bc60a3ffca234dd1fec"
converted_at: "2026-10-26T07:04:54.522187+00:00"
markitdown_version: "0.1.9"
---
Inferring Prerequisite Knowledge Concepts in
Educational Knowledge Graphs: A Multi-criteria
Approach
Rawaa Alatrash1[0000−0003−2192−028X], Mohamed Amine
Chatti1[0000−0002−1311−7852], Nasha Wibowo1, and Qurat Ul
Ain1[0000−0003−2691−0267]
Social Computing Group, Faculty of Computer Science, University of
Duisburg-Essen, Duisburg, Germany
Abstract. Educational Knowledge Graphs (EduKGs) organize various
learningentitiesandtheirrelationshipstosupportstructuredandadap-
tive learning. Prerequisite relationships (PRs) are critical in EduKGs
for defining the logical order in which concepts should be learned. How-
ever, the current EduKG in the MOOC platform CourseMapper lacks
explicitPRlinks,andmanuallyannotatingthemistime-consumingand
inconsistent. To address this, we propose an unsupervised method for
automatically inferring concept PRs without relying on labeled data.
We define ten criteria based on document-based, Wikipedia hyperlink-
based, graph-based, and text-based features, and combine them using a
votingalgorithmtorobustlycapturePRsineducationalcontent.Exper-
iments on benchmark datasets show that our approach achieves higher
precisionthanexistingmethodswhilemaintainingscalabilityandadapt-
ability, thus providing reliable support for sequence-aware learning in
CourseMapper.
Keywords: Educational Knowledge Graphs · MOOCs · Prerequisite
concept identification · Relation extraction · Knowledge structure
1 Introduction
Educational Knowledge Graphs (EduKGs) play a vital role in organizing and
representingkeyentitiesandtheirrelationshipsindigitallearningenvironments,
supporting knowledge discovery, concept navigation, and learner modeling [1].
In our MOOC platform CourseMapper, EduKGs provide learners with a struc-
tured overview of the main knowledge concepts covered in learning materials
to enhance understanding and engagement [2,3,1]. However, a major limitation
of current EduKG structures in CourseMapper is the lack of prerequisite rela-
tionships (PRs), which define concept dependencies where understanding one
concept is necessary before learning another. These relationships determine the
logical sequence for mastering topics and support personalized sequence recom-
mendations [15]. Without explicit PRs, learners may struggle to identify which
concepts should be mastered first, which can hinder self-directed learning and
5202
peS
5
]YC.sc[
1v39350.9052:viXra

2 R. Alatrash et al.
adaptiverecommendationsystems.Priorresearchhasexploredend-to-endlearn-
ing,feature-based,andhybridmethodsforPRextraction[6,15,12,5].End-to-end
learning-based methods depend on domain-specific labeled data and static fea-
tures, which limits their scalability. Feature-based methods remain widely used
and rely on graph structures, text content, or Wikipedia data to capture con-
ceptdependencies[12,7].However,thesemethodshaveseverallimitations.They
often overlook how semantic and structural information interact and they of-
ten rely only on concept order. Moreover, most feature-based approaches as-
sess each criterion individually instead of combining their contributions for ef-
fective PR identification. To overcome these limitations, we propose an unsu-
pervised, multi-criteria approach that combines the contributions of document-
based, Wikipedia hyperlink-based, graph-based, and text-based features using a
voting algorithm, aiming to effectively extract PRs and enrich the structure of
EduKGs in CourseMapper.
2 Background and Related Work
2.1 EduKG Generation in CourseMapper
EducationalKnowledgeGraphs(EduKGs)representdiverseentitiesandtheirre-
lationshipswithinalearningcontext,suchasconcepts,instructors,courses,and
institutions[1].InourMOOCplatformCourseMapper[2],instructorscanupload
LearningMaterials(LM),forwhichanEduKGisautomaticallygenerated.This
includesentitiessuchasLM,Slides(S),MainConcepts(MC),RelatedConcepts
(RC), Categories (Cat), and Learners (L), linked by relationships such as CON-
TAINS, CONSISTS_OF, RELATED_TO, HAS_CATEGORY, HAS_READ,
UNDERSTOOD (U), and DID_NOT_UNDERSTAND (DNU). MCs are iden-
tified in each slide using a keyphrase extraction algorithm. These MCs undergo
an expansion process via DBpedia Spotlight, which adds additional knowledge
concepts as RCs and Cats. The RCs and Cats are then filtered to retain only
the most relevant ones using cosine similarity in the EduKG[3]. This structure
provideslearnerswithanorganizedviewofkeyconceptsintheLM.TheEduKG
can be further enhanced by adding prerequisite relationships, which model the
learningsequenceamongconceptsandsupportadaptivelearningpathways[15].
Currently, CourseMapper’s EduKG does not include PRs, limiting its support
for sequence-aware learning.
2.2 Prerequisite Relationship Extraction
PRs describe how concepts depend on each other in learning pathways. Meth-
ods for identifying PRs include end-to-end learning-based, feature-based, and
hybrid approaches. End-to-end learning-based methods rely on deep learning
to detect PRs from large datasets [6,19,17]. Feature-based methods use man-
ually designed features [15,12,7] such as graph-based features [12], which cap-
ture structural characteristics of graphs; text-based features, which use descrip-
tionsandcontent[23,8];andWikipedia-basedfeatures,whichexploithyperlinks,

Title Suppressed Due to Excessive Length 3
clickstreams, and categories [18,5,16]. Hybrid methods combine both end-to-
end learning-based and feature-based methods [12,5]. Many existing end-to-end
learning-basedmethodsforPRinferencedependondomain-specificlabeleddata
and simplistic features, limiting scalability and adaptability. Manual annotation
is time-consuming and inconsistent. Most feature-based methods consider cri-
teria independently, often ignoring the interaction between semantic and struc-
tural information. To overcome these issues, we propose an unsupervised multi-
criteria approach combining ten distinct criteria document-based, Wikipedia
hyperlink-based, graph-based, and text-based features.These criteria integrate
semantic, structural, and contextual information through a voting algorithm
that balances their contributions and mitigates noise from any single criterion.
Our method evaluates all concept pairs in the EduKG, which is crucial for un-
structuredcontentwherestructuralcriteriaalonemaybemisleading.Therefore,
incorporatingadditionalcriteriathatleverageexternalresourcesandcontextual
information can enhance the accuracy of PR inference. Our approach, tested
on two public datasets, achieves a precision of 1.0, demonstrating robustness,
domain independence, and effective PR extraction.
3 Methodology
To define the likelihood of one concept being a prerequisite of another, we de-
veloped and adopted a set of criteria, derived from the literature review and
adapted for our context. These criteria are categorized into document-based
features, Wikipedia hyperlink-based features, graph-based features, hierarchy-
based features, and text-based features. Our multi-criteria approach begins by
examining concept pairs against these criteria, each offering a unique perspec-
tive. Their outputs are then aggregated using a voting algorithm, followed by a
thresholding step to infer whether a PR exists. These criteria are applied to all
concept pairs in EduKG in CourseMapper and examined in both directions to
ensurecomprehensiveidentification.Thisstudyexcludesconceptsynonymsand
automatic redirections, as these are managed during the EduKG construction
on the platform CourseMapper, ensuring only unique nodes without duplicates
are extracted [3]. Before outlining the model structure, we adopt three core as-
PR PR PR
sumptions: Transitivity [5,4], where if A−−→B and B −−→C, then A−−→C;
Asymmetry[5,4],whereifB →A,thenA↛B;andNoSelf-Connection[4],
a concept cannot be a prerequisite of itself. Table 1 lists each criterion with its
name, abbreviation, and description.
3.1 Prerequisite Relationships Extraction Features:
Document-based Features: This category depends on the document struc-
turetoobtainthetemporal order(TemO)ofconceptswithinanarticlewhere
the concept introduced first serves as a prerequisite for the subsequent [19]. For
instance,indiscussingClustering,thetermmachinelearning islikelyintroduced
beforeClustering asunderstandingtheformerisessentialforgraspingthelatter.

4 R. Alatrash et al.
Table1:CategoriesofCriteriawithFullNames,Abbreviations,andDescriptions.
Category Full name Abbreviations Description
Document c precedes c in the learning
1 2
based features Temporal order TemO material or channel
Hyperlinks on c hyperlink is mentioned
1
each other’s articles HL-A within c ’s article
2
Wikipedia Hyperlinks on c hyperlink appears in the
1
Hyperlinks each other’s abstract HL-Ab abstract of c
2
based features Hyperlinks on each
other’s related c hyperlink is given on c ’s
1 2
concepts’ abstracts HL-RCA related concept’s abstract
c hyperlink is mentioned
1
Reference distance RefD in the related concepts of c
2
c has higher ratio of the
1
Inbound links and number of in/outbound links
outbound links ratio IOLR pointing to c
2
One concept is a
category of another c is a category of c in
1 2
Graph concept CatCon DBPedia hierarchy
based features One concept is the
direct super-category c is a super category of c in
1 2
of another concept SuperCatCon DBPedia hierarchy
first occurrence of c in
1
Hierarchy channel precedes first
1
based features CourseMapper Hier- CMH occurrence of c in channel
2 2
archy
Text- c has higher topic entropy
1
based features BERTopic and Shan- BERTropy than c
2
non’s Entropy
TemO(c ,c ) is assigned the value 1 if the position P(c ) of concept c appears
1 2 1 1
before the position P(c ) of concept c ; otherwise, 0.
2 2
(cid:40)
1, if P(c )<P(c )
TemO(c ,c )= 1 2 (1)
1 2
0, otherwise
TemO applies only to MCs, as it relies on their order of appearance in the LM;
related concepts are excluded because they are not explicitly mentioned.
Wikipedia Hyperlinks-based Features: Wikipedia has been exploited to
findpotentialPRsamongconceptsbyanalyzingthehyperlinkstructureoftheir
corresponding Wikipedia articles [20,5].
Hyperlinksoneachother’sarticles(HL-A):Inthiscriteria,weexamine
whether the hyperlinks for each concept appear in the corresponding Wikipedia
articlesofotherconcepts.Forexample,ifthehyperlinkfortheconceptArtificial
Intelligence (c ) is found in the Wikipedia article for Machine Learning (c ),
1 2
it suggests that Artificial Intelligence serves as a prerequisite for understanding

|     |     |     |     |     | Title | Suppressed | Due | to Excessive | Length | 5   |
| --- | --- | --- | --- | --- | ----- | ---------- | --- | ------------ | ------ | --- |
MachineLearning.Thisimpliesthatc 1 isaprerequisitetoc 2 .Theserelationships
| are formalized |     | as  | follows: |     |     |     |     |     |     |     |
| -------------- | --- | --- | -------- | --- | --- | --- | --- | --- | --- | --- |
(cid:40)
|     |     |     |        |     |       | 1,  | if c | ∈H  |     |     |
| --- | --- | --- | ------ | --- | ----- | --- | ---- | --- | --- | --- |
|     |     |     | HL−A(c |     | ,c )= |     | 1    | c2  |     | (2) |
1 2
|     |     |     |     |     |     | 0,  | otherwise |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --------- | --- | --- | --- |
where HL−A(c ,c ) determines whether the hyperlink for concept c exists in
|     |     | 1   | 2   |     |     |     |     |     | 1   |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
the Wikipedia article of concept c , where in this case 1 is assigned, otherwise
2
0. H represents the set of concepts that are hyperlinked within the Wikipedia
c2
article for concept c 2 . Sometimes, hyperlinks in Wikipedia articles do not in-
dicate a PR especially in long articles or hyperlinks at the end of the article.
For example, if Supervised Learning appears at the end of the article Machine
Learning it could misleadingly suggest that Supervised Learning is a prerequi-
site to Machine Learning. Therefore, we need to consider criteria focused on the
| abstracts  | of  | articles | for such | special | cases    | [10]. |          |      |              |         |
| ---------- | --- | -------- | -------- | ------- | -------- | ----- | -------- | ---- | ------------ | ------- |
| Hyperlinks |     | on       | each     | other’s | abstract |       | (HL-Ab): | This | criterion is | to find |
out if c hyperlinks are included in c abstract. The abstract typically provides
|     | 1   |     |     |     | 2   |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
a brief definition, and if hyperlink for concept c is mentioned in the abstract of
1
concept c , it suggests that c is likely a prerequisite for c [10]. For instance,
|     | 2   |     |     | 1   |     |     |     | 2   |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
if Machine Learning is referenced in the abstract of Supervised Learning this
implies that understanding Machine Learning is necessary before learning Su-
| pervised | Learning |     | [10]. The | relationships |     | are | formulated | as follows: |     |     |
| -------- | -------- | --- | --------- | ------------- | --- | --- | ---------- | ----------- | --- | --- |
(cid:40)
|     |     |     |         |     |       | 1,  | if c ∈AH |     |     |     |
| --- | --- | --- | ------- | --- | ----- | --- | -------- | --- | --- | --- |
|     |     |     | HL−Ab(c |     | ,c )= |     | 1        | c2  |     | (3) |
1 2
|     |     |     |     |     |     | 0,  | otherwise |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --------- | --- | --- | --- |
HL−Ab(c ,c ) indicates whether c is a prerequisite to c , where 1 is assigned
|     | 1   | 2   |     |     | 1   |     |     | 2   |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
in case hyperlink for concept c belongs to AH which is the set of concepts
|     |     |     |     |     | 1   |     | c2  |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
hyperlinkedwithintheabstractoftheWikipediaarticleforconceptc ,otherwise
2
0.
| Hyperlinks |     | on  | each | other’s | related | concepts’ |     | abstracts | (HL-RCA): |     |
| ---------- | --- | --- | ---- | ------- | ------- | --------- | --- | --------- | --------- | --- |
Inspired by the idea of analyzing the importance of related concepts to infer
PRs[9]andtheroleofhyperlinksinabstracts,wedevelopedthiscriterion.This
involves analyzing the abstracts of related concepts for each concept pair. For
instance, consider the concepts artificial intelligence and machine learning. A
related concept of machine learning, such as artificial neural network, is likely
to reference a hyperlink for concept artificial intelligence in the abstract of its
Wikipediaarticle.Incontrast,aconceptrelatedtoartificial intelligence,suchas
knowledge representation, does not mention the hyperlink of machine learning
concept within the abstract of its article. This pattern arises because related
concepts often share common prerequisite concepts. In this example, artificial
intelligence serves as a prerequisite for both machine learning and artificial
| neural | network | as  | given | in the | following | formula: |     |     |     |     |
| ------ | ------- | --- | ----- | ------ | --------- | -------- | --- | --- | --- | --- |
(cid:40)
|     |     |     |          |     |     | 1,  | if c | ∈A   |     |     |
| --- | --- | --- | -------- | --- | --- | --- | ---- | ---- | --- | --- |
|     |     |     | HL−RCA(c |     | ,c  | )=  | 1    | RCc2 |     | (4) |
1 2
|     |     |     |     |     |     | 0,  | otherwise |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --------- | --- | --- | --- |

| 6   | R. Alatrash |     | et al. |     |     |     |     |     |     |
| --- | ----------- | --- | ------ | --- | --- | --- | --- | --- | --- |
where A RCc2 is the set of concepts that are hyperlinked within the abstract of
the Wikipedia article of the related concepts of c . HL−RCA(c ,c ) will be 1
|         |              |     |             |     |      |             | 2   | 1   | 2   |
| ------- | ------------ | --- | ----------- | --- | ---- | ----------- | --- | --- | --- |
| in case | c hyperlinks |     | are present | in  | A    | , otherwise | 0.  |     |     |
|         | 1            |     |             |     | RCc2 |             |     |     |     |
Referencedistance(RefD):Itisdefinedasthereferencedistancebetween
conceptpair[9].ThismeasurestheproximityofWikipediaarticlesbasedontheir
reference links and can be an excellent indicator for finding PRs. The idea here
is that for each concept pair, we are comparing the asymmetry of c ’s related
1
concept mentioning c and c ’s related concepts mentioning c . For example,
|     |     |     | 2   | 2   |     |     |     | 1   |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
most of Data Mining related concepts mention Data Science in their articles.
However, none of Data Science related concepts mention Data Mining in their
| articles. | We      | adapted   | this      | equation | to fit    | our system     | as        | follows:    |      |
| --------- | ------- | --------- | --------- | -------- | --------- | -------------- | --------- | ----------- | ---- |
|           |         | (cid:80)k | r(R       | ,c )w(R  |           | ,c ) (cid:80)k | r(R       | ,c )w(R     | ,c ) |
|           |         |           |           | ci 2     | ci        | 1              |           | ci 1        | ci 2 |
| RefD      |         | =         | i=1       |          |           | −              | i=1       |             | (5)  |
|           | (c1,c2) |           | (cid:80)k |          |           |                | (cid:80)k |             |      |
|           |         |           |           | w(R      | ci ,c 1 ) |                |           | w(R ci ,c 2 | )    |
|           |         |           |           | i=1      |           |                | i=1       |             |      |
where C = {c ,...,c } is the concept space, R is a set of related concepts to
|     |     | 1   | k   |     |     | ci  |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
c i , w(R ci ,c 1 ) is cosine similarity between R ci and c 1 , r(R ci ,c 1 ) the relationship
between related concept of c and c , where R refers to c , meaning whether
|     |     |     |     | i   | 1   | ci  |     | 1   |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
the related concept of c includes c . The outcome of RefD is then compared
|     |     |     | i   |     | 1   |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
against a threshold to determine whether a PR is indicated as shown in the
| equation | 6   | below. |     |     |     |     |     |     |     |
| -------- | --- | ------ | --- | --- | --- | --- | --- | --- | --- |
(cid:40)
|     |     |     |     | 1,  | if −1<RefD(c |     | ,c  | )<−θ |     |
| --- | --- | --- | --- | --- | ------------ | --- | --- | ---- | --- |
1 2
|     |     | RefD(c | 1 ,c | 2 )= |           |     |     |     | (6) |
| --- | --- | ------ | ---- | ---- | --------- | --- | --- | --- | --- |
|     |     |        |      | 0,   | otherwise |     |     |     |     |
c is considered a prerequisite of c if the RefD result falls between -1 and −θ.
| 1   |     |     |     |     | 2   |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
Conversely,c 2 isassumedtobeaprerequisiteofc 1 iftheRefDresultisbetween
θand1.Whilebetween−θandθindicatesnoprerequisitecanbeinferred,where
| θ is empirically |     | determined. |     | This | is defined | as the | following: |     |     |
| ---------------- | --- | ----------- | --- | ---- | ---------- | ------ | ---------- | --- | --- |
(cid:40)
|     |     |        |     |       | 1, if        | θ <RefD(c | ,c  | )<1 |     |
| --- | --- | ------ | --- | ----- | ------------ | --------- | --- | --- | --- |
|     |     |        |     |       |              |           | 1   | 2   |     |
|     |     | RefD(c |     | ,c )= |              |           |     |     | (7) |
|     |     |        | 2   | 1     | 0, otherwise |           |     |     |     |
Inbound links and outbound links ratio (IOLR): This criterion evaluates
a concept’s connectivity by comparing its inbound and outbound links [10,5].
Foundational concepts usually receive more inbound links, while advanced ones
tend to have more outbound links. To reduce bias from generally popular con-
cepts,wecomputetheinbound-to-outboundlinkratio(IOL),whereahigherIOL
indicates that a concept is more foundational and likely to be a prerequisite, as
given below:
(cid:80)
inboundlinks
|     |     |     | IOL(c | )=  |          |     |     |     | (8) |
| --- | --- | --- | ----- | --- | -------- | --- | --- | --- | --- |
|     |     |     |       | i   | (cid:80) |     |     |     |     |
outboundlinks
Then, we define the ratio to determine the direction of the relationship, as indi-
| cated | by the | equation | IOLR(c | ,c  | ).  |     |     |     |     |
| ----- | ------ | -------- | ------ | --- | --- | --- | --- | --- | --- |
|       |        |          |        | 1   | 2   |     |     |     |     |
(cid:40)
|     |     |        |     |       | 1,  | if IOL(c | )>IOL(c | )   |     |
| --- | --- | ------ | --- | ----- | --- | -------- | ------- | --- | --- |
|     |     | IOLR(c |     | ,c )= |     |          | 1       | 2   | (9) |
1 2
|     |     |     |     |     | 0,  | otherwise |     |     |     |
| --- | --- | --- | --- | --- | --- | --------- | --- | --- | --- |

|     |     |     |     | Title Suppressed |     | Due | to Excessive | Length |     | 7   |
| --- | --- | --- | --- | ---------------- | --- | --- | ------------ | ------ | --- | --- |
Graph-based Features: This category adopts the hierarchical structure of
DBpedia, where the categories in DBpedia represent the hierarchical relation-
| ships between | concepts. |               |     |            |     |         |           |     |            |     |
| ------------- | --------- | ------------- | --- | ---------- | --- | ------- | --------- | --- | ---------- | --- |
| One concept   |           | is a category |     | of another |     | concept | (CatCon): |     | Categories |     |
outline the essential topics of concepts, and understanding a concept often re-
quires knowledge of its foundational elements defined by its category [20,5].
Based on the DBpedia hierarchy, if c is classified under c , we can infer that c
|     |     |     |     | 2   |     |     | 1   |     |     | 1   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
is a category of c and thus a prerequisite for c . To formulate this, we define
|     | 2   |     |     |     |     | 2   |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
K as the category associated with c and vice versa in case of K . This is
| c2           |          |        |     | 2   |     |     |     |     | c1  |     |
| ------------ | -------- | ------ | --- | --- | --- | --- | --- | --- | --- | --- |
| given in the | equation | below: |     |     |     |     |     |     |     |     |
(cid:40)
|     |     |          |     |       | 1,  | if c ∈K |     |     |     |      |
| --- | --- | -------- | --- | ----- | --- | ------- | --- | --- | --- | ---- |
|     |     | CatCon(c |     | ,c )= |     | 1       | c2  |     |     | (10) |
1 2
|     |     |     |     |     | 0,  | otherwise |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --------- | --- | --- | --- | --- |
CatCon(c 1 ,c 2 ) indicates that c 1 belongs to the category associated with c 2 . In
other words, c is categorized under c . This, strongly implies that c serves as
|                | 2   |     |     | 1   |     |     |     |     | 1   |     |
| -------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| a prerequisite | for | c . |     |     |     |     |     |     |     |     |
2
| One concept |     | is the | direct | super-category |     |     | of another | concept |     | (Su- |
| ----------- | --- | ------ | ------ | -------------- | --- | --- | ---------- | ------- | --- | ---- |
perCatCon): Another useful signal for identifying PRs is the direct super-
category of a concept, defined as the category of its category in DBpedia [20].
This follows a transitive logic: if c (Machine Learning) is a category of c (Un-
|     |     |     |     | 1   |     |     |     |     | 2   |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
supervised Learning), and c is a category of c (K-Means). Thus, c is the
|     |     |     | 2   |     |     | 3   |     |     | 1   |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
super-category of c , which means c is inferred as a prerequisite of c . Let Kup
|     |     | 3   |     | 1   |     |     |     |     | 3   | c1  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
denote the direct super-category of c , PR exists when these intersect with the
1
| categories | of c 2 . |     |            |     |          |     |     |     |     |      |
| ---------- | -------- | --- | ---------- | --- | -------- | --- | --- | --- | --- | ---- |
|            |          |     | SuperCat(c | ,c  | )=|Kup∩K |     | |   |     |     | (11) |
|            |          |     |            | 1 2 |          | c1  | c2  |     |     |      |
This is also repeated to calculate the existence of prerequisite in both directions
super(c ,c ). Then, we compare their asymmetry to avoid intertwining cate-
| 2   | 1   |     |     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
gories. We want to prevent scenarios where some super-categories of c are also
2
categoriesofc forSuperCat(c ,c )orforSuperCat(c ,c ),whichwouldimply
|                       | 1   |     |          | 1 2 |     |     | 2 1 |     |     |     |
| --------------------- | --- | --- | -------- | --- | --- | --- | --- | --- | --- | --- |
| mutual prerequisites, |     | as  | follows: |     |     |     |     |     |     |     |
(cid:40)
|               |     |     | 1,  | if len(SuperCat(c |     | ,c  | ))>len(SuperCat(c |     |     | ,c )) |
| ------------- | --- | --- | --- | ----------------- | --- | --- | ----------------- | --- | --- | ----- |
|               |     |     |     |                   |     | 1 2 |                   |     | 2   | 1     |
| SuperCatCon(c | ,c  | )=  |     |                   |     |     |                   |     |     |       |
|               | 1   | 2   | 0,  | otherwise         |     |     |                   |     |     |       |
(12)
WhenSuperCatCon(c ,c )is1,indicatesthatmoreofc ’ssuper-categoriesare
|                 |     | 1              | 2   |          |                   |     | 1      |     |     |     |
| --------------- | --- | -------------- | --- | -------- | ----------------- | --- | ------ | --- | --- | --- |
| also categories | of  | c 2 suggesting |     | that c 1 | is a prerequisite |     | of c 2 | .   |     |     |
Hierarchy-based Features: This category captures the structural organi-
zation of educational content, reflecting concept relationships based on their
positions within hierarchical formats. This approach can be applied to all ed-
ucational platforms that follow a hierarchy structure. Inspired by Thareja et
al., who modeled conceptual progression using the hierarchical structure of aca-
demictextbookstodetectPRs[17].Weappliedasimilarstrategyinourcontext

| 8 R. Alatrash | et al. |     |     |     |     |
| ------------- | ------ | --- | --- | --- | --- |
by leveraging the course hierarchy in CourseMapper, to define the CourseMap-
perHierarchy(CMH)criterion,whichcapturesPRsamongconceptswithinthe
coursehierarchy.InCourseMapper,coursesarestructuredhierarchically,encom-
passing multiple topics, each of which consists of several channels that, in turn,
contain various LMs. This hierarchical organization can be leveraged to infer
PRs,asthearrangementoftopics,channels,andLMsfollowsasequentialorder.
Specifically,channelsthatneedtobeaccessedearlierarepositionedbeforethose
intended for later stages of learning. By exploiting this structured progression,
we can systematically derive PRs between different concepts within one course.
(cid:40)
|     |          | 1,     | if Top(c 1 )>Top(c | 2 ) |      |
| --- | -------- | ------ | ------------------ | --- | ---- |
|     | ConTop(c | ,c )=  |                    |     | (13) |
|     |          | 1 2 0, | otherwise          |     |      |
In this context, Top(c ) represents the topics or channels within one course in
1
which c 1 appears within a learning material in CourseMapper. ConTop(c 1 ,c 2 )
is assigned a value of 1 if the channel in which c is mentioned precedes the
1
channel that mentions c . In this case, the likelihood of c being a prerequisite
|                 |                | 2   |     | 1   |     |
| --------------- | -------------- | --- | --- | --- | --- |
| for c increases | significantly. |     |     |     |     |
2
Text-based Features: This approach utilizes BERTopic combined with Shan-
non’s entropy (BERTropy) to infer prerequisite connections [5]. In this con-
text, a topic is defined as a theme discussed in the Wikipedia abstract of a
given concept. For example, the abstract of the Machine Learning article may
includetopicssuchasArtificial Intelligence andStatistical Methods.Theunder-
lying intuition of this approach is that more advanced concepts tend to be more
specialized and therefore cover fewer topics, whereas general concepts span a
broader set of topics. To operationalize this, BERTopic is employed to extract
topics from the Wikipedia abstract of a concept c. The model assigns a prob-
ability to each topic, indicating the degree to which the topic is present in the
abstract. Let P(x) denote the probability assigned by BERTopic that topic x
| appears in | the abstract | of concept c:      |     |     |      |
| ---------- | ------------ | ------------------ | --- | --- | ---- |
|            |              | P(x)=BERTopic(x,c) |     |     | (14) |
Given these topic probabilities, Shannon entropy is used to measure the distri-
| bution of topics | within | the abstract: |     |     |     |
| ---------------- | ------ | ------------- | --- | --- | --- |
X
|     |     |             | (cid:88) 1 |     |      |
| --- | --- | ----------- | ---------- | --- | ---- |
|     |     | EntPro(c)=− | P(x)log    |     | (15) |
P(x)
x
whereX denotesthesetofallidentifiedtopicsandP(x)representstheprobabil-
ity of topic x for concept c. A higher entropy score indicates that the concept is
moregeneral,whilealowerentropyscoresuggestsamoreadvancedandfocused
concept. This is applied to infer PRs between all concept pairs using entropy
rule. A PR is assumed to exist only if the difference exceeds this threshold θ. In

|     |     |     |     | Title | Suppressed | Due to Excessive | Length | 9   |
| --- | --- | --- | --- | ----- | ---------- | ---------------- | ------ | --- |
our case, the threshold is empirically selected and set θ = 1.33, meaning that
| between | 0   | and 1.33, | we assume | no PR | exists. |     |     |     |
| ------- | --- | --------- | --------- | ----- | ------- | --- | --- | --- |
(cid:40)
|     |            |           |       | 1, if        | EntPro(c | )−EntPro(c | )>θ |      |
| --- | ---------- | --------- | ----- | ------------ | -------- | ---------- | --- | ---- |
|     | BERTropy(c |           | ,c )= |              |          | 1          | 2   | (16) |
|     |            |           | 1 2   |              |          |            |     |      |
|     |            |           |       | 0, otherwise |          |            |     |      |
| 3.2 | Voting     | Algorithm |       |              |          |            |     |      |
Afterapplyingthecriteriamentionedpreviouslytoeachconceptpairs,avoting
algorithm will take place determine both the presence and direction of the PR
between concept pairs. First, we treat all criteria equally by assigning equal
weight(1)toallofthem.Thisavoidsbiasinginferencetowardanysinglefeature
andensuresnocriteriondominatesthefinaldecision.Afterthat,weconstructed
two binary arrays (one hot encoded) (A ,A ) corresponds to (c1 > c2) and
1 2
(c2 < c1), each of size 10, to examine how well each concept pair satisfies the
set of predefined criteria. Each array element corresponds to a specific criterion
and is assigned a value of 1 if the criterion is met or 0 if not. This means that
only the criteria that are satisfied contribute to the final computation used to
determine the PR, while the criteria that are not met have no influence on the
result. We then separately sum the positive values in each array to quantify the
total contribution of satisfied criteria for each concept pair. Following that, we
compute the difference between the two sums by subtracting the total score of
| A 1 | from that | of A 2 , | as detailed | in the   | following | equation. |     |      |
| --- | --------- | -------- | ----------- | -------- | --------- | --------- | --- | ---- |
|     |           |          |             | (cid:88) | (cid:88)  |           |     |      |
|     |           |          |             | S =      | A −       | A         |     | (17) |
|     |           |          |             | init     | 1         | 2         |     |      |
After that, normalization takes place, which is a common practice in many ap-
plications and simplifies setting thresholds for PR inference. To this end, the
finalscore(S )isrescaledfromtheoriginalrangeof[−10,10]tothestandard-
init
ized range of [−1,1]. This facilitates meaningful aggregation and supporting the
| inference | of  | PRs. |     |          |         |          |     |      |
| --------- | --- | ---- | --- | -------- | ------- | -------- | --- | ---- |
|           |     |      |     | (cid:18) |         | (cid:19) |     |      |
|           |     |      |     | S        | init −S | min      |     |      |
|           |     |      | S   | =2·      |         | −1       |     | (18) |
|           |     |      | new | S        | −S      |          |     |      |
|           |     |      |     |          | max     | min      |     |      |
where S new is the normalized score difference between the two arrays, A 1 and
A . S , in this case, would be the minimum, which is −10 and S is the
| 2   | min |     |     |     |     |     | max |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
maximum,10.S isthecurrentscorebeforenormalizationaconceptpairhas.
init
After normalizing the results, we classify the results into three distinct ranges.
To do this, we define a threshold on both sides, these are θ and −θ. The first
rangeisifS new orthedifferencebetweenthearraysisbetween−1and−θwhich
concludes that c is a prerequisite concept to c . When the result is between −θ
|     |     | 2   |     |     |     | 1   |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
and θ, that means there is no PR between the two concepts. The last range is
when S is between θ and 1 then we conclude that c is a prerequisite of c .
|     | new |     |     |     |     | 1   |     | 2   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
The value of θ =0.28 is determined empirically through a series of experiments
aimed at identifying the optimal parameter setting for our specific application
as mentioned in Section 4. To illustrate this more, an example in Table 2 is

| 10 R. | Alatrash | et al. |     |     |     |     |     |     |     |     |     |
| ----- | -------- | ------ | --- | --- | --- | --- | --- | --- | --- | --- | --- |
given, after examining all criteria for the concept pair Machine Learning (c 1 )
and Supervised Learning (c ), we use two one-hot encoded arrays (A ,A ) to
|     |     |     | 2   |     |     |     |     |     |     | 1 2 |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
representhowwelleachconceptpairsatisfiesasetofpredefinedcriteria,inboth
directions.Afterthat,wecalculatetheoverallsumsofthetwoarrays(A =5.00
1
|     |     | Table |     | 2: Voting | algorithm | example |     |     |     |     |     |
| --- | --- | ----- | --- | --------- | --------- | ------- | --- | --- | --- | --- | --- |
Criteria TemO HL-A HL-Ab HL-RCA RefD IOLR CatCon SuperCatCon CMH BERTropy
| A (c ->c | ) 1 | 1   | 0   | 0   | 0   | 0   | 1   |     | 1   | 0   | 1   |
| -------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 1 2    |     |     |     |     |     |     |     |     |     |     |     |
| (c ->c   | ) 0 | 0   | 1   | 0   | 1   | 0   | 0   |     | 0   | 0   | 0   |
| A 2 2 1  |     |     |     |     |     |     |     |     |     |     |     |
and A 2 = 2.00), then compute the difference between them and normalize it,
as illustrated in Table 3. The final score of 0.3 > 0.28 falls between θ and 1,
| indicating | that c | is prerequisite |            | to c | .      |           |         |     |     |     |     |
| ---------- | ------ | --------------- | ---------- | ---- | ------ | --------- | ------- | --- | --- | --- | --- |
|            |        | 1               |            |      | 2      |           |         |     |     |     |     |
|            |        | Table           | 3: Example | of   | voting | algorithm | results |     |     |     |     |
Mechanism Total A (c ->c ) Total A (c ->c ) A −A Normalized difference
|                  |     |     | 1 1  | 2       | 2    | 2 1 | 1    | 2   |     |     |     |
| ---------------- | --- | --- | ---- | ------- | ---- | --- | ---- | --- | --- | --- | --- |
| Voting algorithm |     |     | 5.00 |         | 2.00 |     | 3.00 |     | 0.3 |     |     |
| 4 Experiments    |     |     | and  | Results |      |     |      |     |     |     |     |
To demonstrate the effectiveness and advantages of our proposed method, we
conducted thorough experiments and a comparative analysis using two public
datasets, namely the AL-CPL [18,11,10] and Biology datasets, which is a spe-
cialized dataset derived from textbook chapters in the Biology curriculum [17].
| Threshold | Optimization: |     |     | The | threshold | is  | essentially | a hyperparameter |     |     |     |
| --------- | ------------- | --- | --- | --- | --------- | --- | ----------- | ---------------- | --- | --- | --- |
to control the sensitivity of the model in determining the PR. The thresholds of
criteria RefD and BERTopic, as well as the proposed voting algorithm were de-
terminedempiricallyusingthesamemethodology,basedontheAL-CPLdataset.
To this end, a range of threshold values have been used to run each approach
separately and compared the results with the ground truth dataset to compute
precision, accuracy, recall, and F1 score. The RefD method identifies PRs by
analyzinghowconceptsreferenceeachotherwithintheWikipedialinkstructure.
Wangetal.[18]originallyproposedathresholdvalueofθ =0.04.Wereplicated
this in the context of our platform, CourseMapper to generate the PRs. We
found out that precision peaks at θ =0.6 with a value close to 0.9. This aligned
with our aim of reliably detecting PRs while minimizing false positives. The
higher threshold compared to previous work is attributed to the more domain-
specificconceptspaceusedinourEduKG.Whilepriorstudiesoperatedoverthe
full Wikipedia concept set, our system limits the scope to concepts and related

Title Suppressed Due to Excessive Length 11
concepts extracted from AL-CPL, leading to a more focused and specialized se-
mantic space. Similarly, BERTropy infers PRs between concepts by analyzing
the distribution of topics covered within their respective abstracts. We calcu-
lated the distribution of topics covered across all concepts. Then, BERTropy is
applied to the entire set of concepts to determine PRs among them. We em-
pirically found that precision peaks at θ = 1.4, reaching approximately 0.9.
This suggests that higher thresholds are more conservative, identifying only the
strongest relationships, whereas lower thresholds connect more topics but may
introduce noise. For the Voting Algorithm, we experimentally observed that
precision reaches its maximum value of 1.0 at θ = 0.28, indicating complete
correctness among positive predictions without false positives at this threshold.
In this study, we prioritize precision because minimizing false positives is more
critical than capturing all possible PRs. Incorrect prerequisite suggestions could
negatively affect learning paths and curriculum design.
Experiment1:PrerequisiteLearningontheAL-CPLDataset: Toeval-
uate the effectiveness of our proposed model, we conducted experiments using
three domains from the AL-CPL dataset: Data Mining, Physics, and Macroeco-
nomics [18,10,11]. It labels concepts with relationships: 1 for "prerequisite," -1
for"reverseprerequisite,"and0fornorelation.Thisdatasetvalidatesallcriteria
except CMH, which requires a content hierarchy that is lost when materials are
uploaded into a single channel, treating all concepts at the same level. There-
fore, hierarchical information was only applied in the Biology dataset, where
such structure was available. The AL-CPL was uploaded in CourseMapper, and
an EduKG was generated including main concepts, related concepts, and cat-
egories. This set of related concepts is utilized to infer the likelihood of a PR
between concept pairs of the learning materials in CourseMapper.
Evaluation of Individual Criteria: To evaluate the contribution of each
criterion,weconductedexperimentsacrossthreedomains—DataMining,Physics,
and Macroeconomics. Results showed that BERTropy achieved (1), HL-Ab ob-
tained(0.84),andRefDaccomplished(0.84)notablyenhancedprecisioninData
Mining, while HL-Ab got (1) and CatCon got (1) performed well in Physics,
and CatCon excelled in Macroeconomics with value (0.86). In terms of recall,
IOLR with value (0.83, 0.84, 0.91) consistently outperformed all other criteria
across three domains (Data Mining, Physics, and Macroeconomics), effectively
capturing a broader set of prerequisite relations. Conversely, SuperCatCon un-
derperformedinbothprecisionandrecall,indicatingtheneedforrefinement.To
assess the balance between precision and recall, F1 scores were analyzed. IOLR
achievedthehighestF1scoreswithvalues(0.67,0.55,0.59)inalldomains(Data
Mining,Physics,andMacroeconomics),confirmingitseffectivenessinmaintain-
ingthistrade-off.Accuracywasalsoconsideredandofferedusefultrends,despite
potential sensitivity to class imbalance. For example, HL-A showed high accu-
racy (0.65) in Data Mining, while CatCon achieved (0.70, 0.63) strong accuracy
in Physics and Macroeconomics but had lower F1 scores, suggesting it may fa-
vor majority classes while poor at finding the minority class. The variation in

12 R. Alatrash et al.
criterionperformanceacrossdomainscanbeattributedtodifferencesinconcept
structure and semantic clarity. For instance, Data Mining and Physics datasets
often contain well-defined, hierarchical, and technically specific concepts, which
alignwellwithcriteriathatleveragestructuralorsemanticfeatures.Incontrast,
the Macroeconomics domain tends to be more abstract and less formally struc-
tured, making it harder for some methods to identify clear PRs. In line with
prior work, we place greater emphasis on precision, as the reliability of inferred
PRs is critical for downstream tasks and system utility.
Comparative Results and Analysis: We compared our proposed model
againstsixbaselinemethods—RefD[9],ActiveLearning[11],AdaBoost[22],Wi-
kiCPRL[21],NeuralNetwork[14],andaLinguistically-DrivenStrategy[13]—to
evaluate its effectiveness in capturing PRs without relying on labeled data. As
shown in Table 4, we assessed our voting algorithm across three domains: Data
Mining,Physics,andMacroeconomics.Comparedtoexistingbaselines,ourpro-
posed Voting Algorithm consistently achieves higher precision but lower recall
andF1scores,reflectingitsfocusonreliablyextractingonlythestrongestedges.
For example, in Data Mining, our method reaches perfect precision (1.0) while
RefD, Active Learning, and AdaBoost achieve lower precision (0.51,0.80, 0.85)
but higher recall (0.76, 0.73, 0.85) and F1 scores (0.61, 0.67, 0.85). Similarly
in Physics, Bagging-based AdaBoost achieves higher precision (0.87) than our
method (0.76), while other baselines such as RefD and WikiCPRL show lower
precision (0.49 and 0.43, respectively) compared to our method, but higher re-
call (0.49, 0.90). The same trend is observed for the Neural Network and the
Linguistically-Driven Strategy, which yield higher F1 scores (0.65 and 0.81 in
Data Mining, respectively, vs. 0.42 for our method) due to their stronger recall.
This pattern shows that while baselines recover more links overall, our method
prioritizes the precision and reliability of inferred PRs—critical for building ro-
bust learning paths—since, in educational settings, misleading a learner with
an incorrect prerequisite (false positive) is more harmful than omitting some
prerequisites.
However, baseline models perform better in recall, which we attribute to our
precision-focused threshold selection in criteria such as RefD and BERTropy.
These thresholds were tuned to prioritize reliability over quantity, resulting in
fewer but more accurate inferred relationships. This can be attributed to differ-
ences between domains in concept structure and semantic clarity as mentioned
earlier. Despite the lower recall, the proposed voting algorithm which integrates
variousfeature-basedmethodsachievescompetitiveperformancewithoutrequir-
ing any labeled training data. This makes it particularly well-suited for real-
world settings where labeled prerequisite data is limited or difficult to obtain.
Although supervised models often outperform unsupervised ones due to access
to labeled data, manual labeling is costly, time-consuming, and prone to incon-
sistency.Mostunsupervisedmethodsevaluatecriteriaindependentlyratherthan
integrating them for more effective PR identification. Our unsupervised multi-
criteriaapproachaddressesthisgapwithascalable,flexiblevotingalgorithmfor
inferring PRs, particularly in diverse educational domains lacking annotations.

|          |       |                | Title      | Suppressed |        | Due     | to Excessive | Length         |      | 13   |
| -------- | ----- | -------------- | ---------- | ---------- | ------ | ------- | ------------ | -------------- | ---- | ---- |
|          | Table | 4: Performance | Comparison |            | Across | AL-CPL  |              | Datasets       |      |      |
|          |       |                | DataMining |            |        | Physics |              | Macroeconomics |      |      |
| Criteria |       |                | P R        | F1         | Acc.   | P R     | F1 Acc.      | P              | R F1 | Acc. |
TemO 0.47 0.31 0.37 0.40 0.36 0.42 0.39 0.47 0.46 0.71 0.56 0.53
HL-A 0.8 0.53 0.64 0.65 0.58 0.34 0.43 0.64 0.58 0.34 0.42 0.62
HL-Ab 0.84 0.22 0.35 0.53 1 0.13 0.23 0.65 0.62 0.08 0.14 0.60
HL-RCA 0.53 0.53 0.53 0.45 0.42 0.67 0.52 0.49 0.39 0.43 0.41 0.48
RefD 0.84 0.22 0.35 0.53 0.72 0.21 0.33 0.65 0.69 0.15 0.24 0.62
| IOLR        |     |     | 0.560.830.67 |      | 0.53 0.41 | 0.840.55 | 0.45          | 0.44 | 0.910.59  | 0.47 |
| ----------- | --- | --- | ------------ | ---- | --------- | -------- | ------------- | ---- | --------- | ---- |
| CatCon      |     |     | 0 0          | 0    | 0.43      | 1 0.25   | 0.40 0.700.86 |      | 0.12 0.21 | 0.63 |
| SuperCatCon |     |     | 0 0          | 0    | 0.43      | 0 0      | 0 0.60        | 0    | 0 0       | 0.59 |
| BERTropy    |     |     | 1 0.09       | 0.16 | 0.48 0.26 | 0.09     | 0.13 0.54     | 0    | 0 0       | 0.59 |
Baselines
| RefD[9]                               |     |     | 0.51 0.76 | 0.61 | - 0.49         | 0.49 | 0.49 -    | -    | - -       | -    |
| ------------------------------------- | --- | --- | --------- | ---- | -------------- | ---- | --------- | ---- | --------- | ---- |
| ActiveLearning[10]                    |     |     | 0.80 0.73 | 0.76 | - 0.8          | 0.6  | 0.7 -     | -    | - -       | -    |
| Bagging-basedAdaBoost[22]             |     |     | 0.85 0.85 | 0.85 | - 0.870.870.86 |      | -         | -    | - -       | -    |
| WikiCPRL[21]                          |     |     | 0.590.90  | 0.68 | - 0.43         | 0.83 | 0.57 -    | -    | - -       | -    |
| NeuralNetwork[14]                     |     |     | 0.62 0.68 | 0.65 | - 0.53         | 0.62 | 0.57 -    | -    | - -       | -    |
| Linguistically-DrivenStrategy[13]0.81 |     |     | 0.81      | 0.81 | - 0.77         | 0.71 | 0.74 -    | -    | - -       | -    |
|                                       |     |     | 0.27      | 0.42 | 0.58 0.76      | 0.13 | 0.22 0.64 | 0.65 | 0.16 0.25 | 0.61 |
| Proposed-VotingAlgorithm              |     |     | 1         |      |                |      |           |      |           |      |
Experiment 2: Prerequisite Learning on the Biology Dataset: To ef-
fectively evaluate the proposed model’s ability to detect PRs and assess TemO
criterion more reliably, as well as to measure the contribution of CMH, we
NCERT1
| utilized | a specialized | dataset | derived | from | textbook |     | chapters | in the |     |     |
| -------- | ------------- | ------- | ------- | ---- | -------- | --- | -------- | ------ | --- | --- |
Biology curriculum [17]. For our experiments, we selected two conceptually re-
lated chapters from NCERT science textbooks: Chapter 7 (Transportation in
Animals and Plants, Class 7) and Chapter 6 (Life Processes, Class 10). These
were chosen for their natural hierarchical relationship, with foundational con-
tent in Class 7 supporting advanced concepts in Class 10. Both chapters were
uploaded into CourseMapper under the same course and same topic, but placed
intwodifferentsequentialchannelstopreservethelearninghierarchydefinedby
theplatform.WegeneratedtheEduKGforeachchapterindividuallybyextract-
ing the main concepts from each and then expanding them using DBpedia to
identifyrelatedconcepts.Thisstructureenabledustoevaluatealltenpredefined
criteria for detecting PRs. It is worth mentioning, when a new learning mate-
rial is added, the system computes the EduKG for this new material, without
needing to reprocess the entire EduKG. In the absence of ground truth in the
original dataset, 186 concept pairs were manually annotated by domain experts
| (PhDs      | and medical | doctors)      | as either | prerequisite |     | or          | not. |                 |     |     |
| ---------- | ----------- | ------------- | --------- | ------------ | --- | ----------- | ---- | --------------- | --- | --- |
| Evaluation |             | of Individual | Criteria  |              | and | Comparative |      | Results:Biology |     |     |
datasetisusedtoevaluateeachindividualcriterionusingfourstandardmetrics:
precision, recall, F1-score, and accuracy (Table 5). HL-Ab and HL-A achieved
thehighestprecision,effectivelyidentifyingthemostreliablePRswhileminimiz-
ing false positives. In contrast, IOLR and CMH attained the highest recall, cap-
turingabroadersetofdependenciesattheexpenseoftoleratingsomefalsepos-
1 https://ncert.nic.in/textbook.php

| 14  | R. Alatrash et al. |     |     |     |
| --- | ------------------ | --- | --- | --- |
itives. Notably, IOLR and CMH also achieved the highest F1-scores, indicating
a strong balance between precision and recall. In terms of accuracy, BERTropy
performed best (0.75), followed closely by IOLR and CMH, reinforcing their ro-
bustness in distinguishing between prerequisite and non-prerequisite pairs. The
success of CMH, in particular, highlights the value of structured educational
contentandhierarchicalinformationininferringPRs.Inthisdataset,theplace-
mentofmaterialsacrosschannelsiswell-defined,enablingCMHtoleveragethis
ordering effectively. By contrast, CatCon and SuperCatCon depend on the cat-
egory hierarchy in DBpedia, and TemO relies on the sequential appearance of
concepts in text, both of which are less consistent in the current dataset. Their
effectiveness may improve by incorporating additional chapters. In comparison,
our proposed voting algorithm achieved competitive results, although it did not
surpass the best-performing individual criteria such as CMH and IOLR. With
moderate precision and recall, it provided a balanced yet limited performance
compared to these criteria when applied independently. The effectiveness of the
votingalgorithmislargelysupportedbystrongindividualcontributorslikeCMH
and IOLR. CMH achieved high F1-scores due to its reliance on hierarchical sig-
nals, while IOLR benefited from the ratio of in-outbound links—both features
being particularly well captured in the Biology dataset. These findings high-
lighttheimportanceofintegratinghierarchicalinformation.Thedefinedcriteria
are deduced from Wikipedia articles, DBpedia hierarchy, textual information,
content order, and platform hierarchy to infer PRs, making it applicable across
| diverse | educational platforms. |            |                |         |
| ------- | ---------------------- | ---------- | -------------- | ------- |
|         | Table 5: Performance   | Comparison | Across Biology | dataset |
Biology
|     | Criteria |     | P R            | F1 Acc.  |
| --- | -------- | --- | -------------- | -------- |
|     | TemO     |     | 0.0 0.0        | 0.0 0.42 |
|     | HL-A     |     | 0.91 0.32 0.48 | 0.58     |
|     | HL-Ab    |     | 1.0 0.06 0.12  | 0.45     |
|     | HL-RCA   |     | 0.87 0.23 0.35 | 0.51     |
|     | RefD     |     | 0.75 0.10 0.17 | 0.45     |
|     | IOLR     |     | 0.58           | 0.58     |
1.0 0.74
|              | CMH               |           | 0.58 1.0 0.74  | 0.58     |
| ------------ | ----------------- | --------- | -------------- | -------- |
|              | CatCon            |           | 0.0 0.0        | 0.0 0.42 |
|              | SuperCatCon       |           | 0.0 0.0        | 0.0 0.42 |
|              | BERTropy          |           | 0.55 0.65 0.70 | 0.75     |
|              | Proposed - Voting | Algorithm | 0.48 0.35 0.41 | 0.40     |
| 5 Conclusion | and Future        | Work      |                |          |
Educational Knowledge Graphs (EduKGs) capture diverse entities and con-
nections in educational systems, providing a structured view of key concepts

Title Suppressed Due to Excessive Length 15
from learning materials. Prerequisite relationships (PRs) are essential for defin-
ing learning sequences but are often missing in EduKGs. However, automatic
methodsforPRidentificationdependondomain-specificlabeleddataandstatic
features, limiting scalability. Existing feature-based methods often ignore how
semantic and structural information interact, rely often on concept order, and
assess criteria individually. To address these gaps, we proposed an unsupervised
method that combines ten criteria using a voting algorithm to infer PRs with-
out using labeled data. Experiments on two benchmark datasets show that our
proposedapproachachieveshigherprecisionthanbaselinesandreliablyextracts
PRs across domains. In future work, we aim to extend our PR identification
framework with more criteria. We will also experiment with hybrid and LLM-
based approaches for more effective PR identification. Additionally, adaptive
thresholding methods, learned per domain and combined with a weighting ap-
proach, could be adopted to further enhance the robustness and accuracy of PR
inference.
Disclosure of Interests. The authors have no competing interests to declare that
are relevant to the content of this article.
References
1. Ain, Q.U., Chatti, M.A., Bakar, K.G.C., Joarder, S., Alatrash, R.: Automatic
constructionofeducationalknowledgegraphs:awordembedding-basedapproach.
Information 14(10), 526 (2023)
2. Ain, Q.U., Chatti, M.A., Joarder, S., Nassif, I., Wobiwo Teda, B.S., Guesmi,
M., Alatrash, R.: Learning channels to support interaction and collaboration in
coursemapper.In:Proceedingsofthe14thInternationalConferenceonEducation
Technology and Computers. pp. 252–260 (2022)
3. Alatrash, R., Chatti, M.A., Ain, Q.U., Fang, Y., Joarder, S., Siepmann,
C.: Conceptgcn: Knowledge concept recommendation in moocs based on
knowledge graph convolutional networks and sbert. Computers and Edu-
cation: Artificial Intelligence 6, 100193 (2024). https://doi.org/https:
//doi.org/10.1016/j.caeai.2023.100193, https://www.sciencedirect.com/
science/article/pii/S2666920X23000723
4. Bai, Y., Liu, Z., Guo, T., Hou, M., Xiao, K.: Prerequisite relation learning: A
survey and outlook. ACM Computing Surveys (2025)
5. Bai,Y.,Zhang,Y.,Xiao,K.,Lou,Y.,Sun,K.:Abert-basedapproachforextract-
ing prerequisite relations among wikipedia concepts. Mathematical Problems in
Engineering 2021(1), 3510402 (2021)
6. Gasparetti,F.,DeMedio,C.,Limongelli,C.,Sciarrone,F.,Temperini,M.:Prereq-
uisitesbetweenlearningobjects:Automaticextractionbasedonamachinelearning
approach. Telematics and Informatics 35(3), 595–610 (2018)
7. Hu,H.,Pan,L.,Ran,Y.,Kan,M.Y.:Modelingandleveragingprerequisitecontext
in recommendation. arXiv preprint arXiv:2209.11471 (2022)
8. Hu, X., He, Y., Sun, G.: Active learning for concept prerequisite learning in
wikipedia. In: Proceedings of the 2021 13th International Conference on Machine
Learning and Computing. pp. 582–587 (2021)

16 R. Alatrash et al.
9. Liang,C.,Wu,Z.,Huang,W.,Giles,C.L.:Measuringprerequisiterelationsamong
concepts. In: Proceedings of the 2015 conference on empirical methods in natural
language processing. pp. 1668–1674 (2015)
10. Liang,C.,Ye,J.,Wang,S.,Pursel,B.,Giles,C.L.:Investigatingactivelearningfor
conceptprerequisitelearning.In:ProceedingsoftheAAAIConferenceonArtificial
Intelligence. vol. 32 (2018)
11. Liang, C., Ye, J., Zhao, H., Pursel, B., Giles, C.L.: Active learning of strict
partial orders: A case study on concept prerequisite relations. arXiv preprint
arXiv:1801.06481 (2018)
12. Manrique,R.,Pereira,B.,Mariño,O.:Exploringknowledgegraphsfortheidenti-
fication of concept prerequisites. Smart Learning Environments 6(1), 21 (2019)
13. Miaschi, A., Alzetta, C., Cardillo, F.A., Dell’Orletta, F.: Linguistically-driven
strategy for concept prerequisites learning on italian. In: Proceedings of the Four-
teenthWorkshoponInnovativeUseofNLPforBuildingEducationalApplications.
pp. 285–295 (2019)
14. Moggio, A., Parizzi, A.: Unige se@ prelearn: Utility for automatic prerequisite
learning from italian wikipedia. EVALITA Evaluation of NLP and Speech Tools
for Italian-December 17th, 2020 p. 376 (2020)
15. Pan,L.,Li,C.,Li,J.,Tang,J.:Prerequisiterelationlearningforconceptsinmoocs.
In:Proceedingsofthe55thAnnualMeetingoftheAssociationforComputational
Linguistics (Volume 1: Long Papers). pp. 1447–1456 (2017)
16. Sayyadiharikandeh,M.,Gordon,J.,Ambite,J.L.,Lerman,K.:Findingprerequisite
relationsusingthewikipediaclickstream.In:CompanionProceedingsofThe2019
World Wide Web Conference. pp. 1240–1247 (2019)
17. Thareja, R., Garg, R., Baghel, S., Dwivedi, D., Mohania, M., Kulshrestha, R.:
Auto-req: Automatic detection of pre-requisite dependencies between academic
videos.In:Proceedingsofthe18thWorkshoponInnovativeUseofNLPforBuild-
ing Educational Applications (BEA 2023). pp. 539–549 (2023)
18. Wang, S., Ororbia, A., Wu, Z., Williams, K., Liang, C., Pursel, B., Giles, C.L.:
Usingprerequisitestoextractconceptmapsfromtextbooks.In:Proceedingsofthe
25thacminternationalonconferenceoninformationandknowledgemanagement.
pp. 317–326 (2016)
19. Xia,J.,Li,M.,Tang,Y.,Yang,S.:Coursemaplearningwithgraphconvolutional
network based on aucm. World Wide Web 26(5), 3483–3502 (2023)
20. Xiao, K., Fu, Y., Zhang, J., Tianji, W.: A hybrid approach for discovering con-
cept prerequisite relations in wikipedia. In: 2022 9th International Conference on
Behavioural and Social Computing (BESC). pp. 1–5. IEEE (2022)
21. Xiao, K., Li, K., Zhang, Y., Chen, X., Lou, Y.: Wikicprl: A weakly supervised
approachforwikipediaconceptprerequisiterelationlearning.In:Asia-PacificWeb
(APWeb) and Web-Age Information Management (WAIM) Joint International
Conference on Web and Big Data. pp. 177–192. Springer (2023)
22. Zhou,Y.,Xiao,K.,Zhang,Y.:Anensemblelearningapproachforextractingcon-
cept prerequisite relations from wikipedia. In: 2020 16th International Conference
on Mobility, Sensing and Networking (MSN). pp. 642–647. IEEE (2020)
23. Zhu, Y., Zamani, H.: Predicting prerequisite relations for unseen concepts. In:
Proceedings of the 2022 Conference on Empirical Methods in Natural Language
Processing (EMNLP 2022) (2022)