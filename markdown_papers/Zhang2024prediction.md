---
title: "Zhang2024prediction"
source: "Zhang2024prediction.pdf"
source_sha256: "8016c3ff2efeebb996c263027a25c5436f6f7c2378d8d90c73a39532f5e8ed98"
converted_at: "2026-10-26T07:05:04.849148+00:00"
markitdown_version: "0.1.9"
---
This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
,Date of publication xxxx 00, 0000, date of current version xxxx 00, 0000.
Digital Object Identifier 10.1109/ACCESS.2022.Doi Number
Prediction of Students’ Grade by Combining
Educational Knowledge Graph and
Collaborative Filtering
Yiwen ZHANG 1,2 ,Vladimir Y.Mariano 1,Rex. P. Bringula 3
1 College of Computing and Information Technologies,National University, Manila, Philippines
2 Big Data and Artificial Intelligence College, Anhui Xinhua University, Hefei, China
3 University of the East,Manila,Philippines
Corresponding author:Zhang Ywen(yiwenzh@ustc.edu.cn)
ABSTRACT Traditional collaborative filtering-based grade prediction methods overly rely on students' historical grades and
overlook the content correlation between courses, resulting in lower accuracy in predicting student grades. This paper proposes
a grade prediction method that combines the educational domain knowledge graph with collaborative filtering, gathering
course semantic information and constructing a course knowledge graph as auxiliary information for grade prediction. Through
experimentation, it has been demonstrated that the integration of the educational knowledge graph and collaborative filtering
in the grade prediction method uncovers more semantic relationships between courses, thereby improving the accuracy of
predicting grades for related courses. The Root Mean Square Error (RMSE) and Mean Absolute Error (MAE) metrics show a
decrease when compared to collaborative filtering and K-means algorithms.The method in this paper allows for more
personalized learning and recommendation in the knowledge-rich field of education with semantic richness.
INDEX TERMS Grade predicted; Knowledge graph; Collaborative filtering; Recommended algorithm
I. INTRODUCTION online resources and provide better personalized resource
In recent years, with the rapid growth of data and information services for learners, the content of online resources and
across various industries, the focus of research has been on learners' learning progress are analyzed.Resource
how to quickly find suitable information for users from a vast recommendations [6] is to provide learners with high-quality
amount of data. To address the problem of information personalized resource recommendations through data analysis
overload, recommendation algorithms have been widely and modeling. Therefore, grade prediction plays an important
applied in scenarios dealing with information overload. role in improving teaching quality and holds significant
Recommendation systems have shown excellent performance research significance and practical value.
in various fields, including telecommunications, finance, Currently, there has been substantial research on student grade
agriculture, e-commerce, medicine, and education [1-2]. In the prediction. Burman et al. [7] collected students' psychological
education sector, recommendation systems have been used to characteristic data and classified student grades into three
provide personalized teaching for students and teachers, categories (high, medium, and low). They used multi-class
making it a current research focus. Support Vector Machines (SVM) for grade prediction. Deho
Among these efforts, predicting student grades is a key aspect et al. [8] used causal tree methods to analyze the factors
of educational data mining. By using prediction methods to influencing student grades during online teaching at a certain
forecast student grades, teachers can identify factors that Australian university in 2020 during the pandemic. Zhang et
influence student performance promptly, reduce the risk of al. [9] predicted student grades by analyzing Massive Open
failing and dropping out, and adjust teaching plans and Online Course(MOOC) learners' behavioral data using neural
methods to implement personalized teaching. Additionally, network algorithms and clustering algorithms. Ma et al. [10]
grade prediction can also be applied to knowledge tracking [3], used a multi-instance multi-label approach to predict students'
we can track students' mastery of learned knowledge points performance in new courses, helping teachers grasp the
based on their learning time series。student profiling [4], The learning progress of each student. Bujang et al. [11] proposed
author analyzes students' historical grades and related the Synthetic Minority Oversampling Technique(SMOTE) to
knowledge points to gain insights into their mastery of the address the issue of class imbalance and overfitting in student
knowledge points.Online assessments [5], In order to optimize grade prediction. Xue Mengting [12] introduced a domain-
VOLUME XX, 2017 1
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/

This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
  Author Name: Preparation of Papers for IEEE Access (February 2017)
based collaborative filtering method for predicting college  graphs and behavior paths based on the historical behavior
student grades. In general, existing student grade prediction  sequences of learners, calculating the similarity between paths,
methods can be categorized into two main types: one that  using  path-based  collaborative  filtering  to  predict  user
|           |             |     |                 |     |          |      |        | behavior  | and  make  | recommendations.Hongwei,  |     |     |     | et  al.  |
| --------- | ----------- | --- | --------------- | --- | -------- | ---- | ------ | --------- | ---------- | ------------------------- | --- | --- | --- | -------- |
| utilizes  | regression  | or  | classification  |     | methods  | for  | grade  |           |            |                           |     |     |     |          |
prediction and another that treats the prediction of student  [18]Established  a  movie  knowledge  graph,  utilizing  the
grades as a rating prediction problem in recommendation  information in the knowledge graph for convolution to predict
user interests and recommend movies. Knowledge Graph
systems.
As  student  learning  behavior  exhibits  time-series  Convolutional Networks (KGCN) is an end-to-end framework
that effectively captures the inter-item relatedness by mining
| characteristics,  |     | and  recommendation  |     |     | systems'  | prediction  |     |     |     |     |     |     |     |     |
| ----------------- | --- | -------------------- | --- | --- | --------- | ----------- | --- | --- | --- | --- | --- | --- | --- | --- |
their associated attributes on the knowledge graph, thereby
methods rely on users' historical behavioral data, using an
analogy to recommendation systems [13-14] to predict student  alleviating data sparsity and cold-start issues. Due to the
abundance of knowledge information in the field of education,
| grades  | yields  | higher  | prediction  | accuracy  |     | and  stronger  |     |     |     |     |     |     |     |     |
| ------- | ------- | ------- | ----------- | --------- | --- | -------------- | --- | --- | --- | --- | --- | --- | --- | --- |
some researchers have also introduced knowledge graphs into
| interpretability  |     | compared  | to  | other  | statistical  | methods.  |     |     |     |     |     |     |     |     |
| ----------------- | --- | --------- | --- | ------ | ------------ | --------- | --- | --- | --- | --- | --- | --- | --- | --- |
educational recommendations, such as, Lu X , Zhu Y, Xu ,et
| However,  | when  | using  | recommendation  |     |     | system-based  |     |                 |        |        |                |              |     |          |
| --------- | ----- | ------ | --------------- | --- | --- | ------------- | --- | --------------- | ------ | ------ | -------------- | ------------ | --- | -------- |
|           |       |        |                 |     |     |               |     | al.[19]created  | three  | types  | of  bipartite  | interaction  |     | graphs:  |
approaches for grade prediction, there is an excessive reliance
|     |     |     |     |     |     |     |     | student-course  | graph,  | student-student  |     | graph,  | and  | course- |
| --- | --- | --- | --- | --- | --- | --- | --- | --------------- | ------- | ---------------- | --- | ------- | ---- | ------- |
on students' historical grades, and the accuracy of grade
course graph. Utilizing these three graph relationships to
prediction can be affected by courses with low relevance in
represent students and courses, calculating student similarities
the historical data.
|     |     |     |     |     |     |     |     | and  course  | similarities,  | and  | conducting  |     | grade  | prediction.  |
| --- | --- | --- | --- | --- | --- | --- | --- | ------------ | -------------- | ---- | ----------- | --- | ------ | ------------ |
Education data has more knowledge relations, and knowledge
|     |     |     |     |     |     |     |     | Wang  | Q,Cao  X,Wang  | J,et  | al.[20]established  |     |     | user-item  |
| --- | --- | --- | --- | --- | --- | --- | --- | ----- | -------------- | ----- | ------------------- | --- | --- | ---------- |
graph can be used to learn more knowledge relations and have
|     |     |     |     |     |     |     |     | knowledge  | interaction  | relationships  |     | and  | inputted  | these  |
| --- | --- | --- | --- | --- | --- | --- | --- | ---------- | ------------ | -------------- | --- | ---- | --------- | ------ |
better interpretability，knowledge graph is currently widely
knowledge relationships into a Transformer model to predict
applied  in  the  field  of  artificial  intelligence,  such  as  ratings based on user reviews. Both of the above methods
| recommendation  |     | systems,  | information  |     | retrieval,  |     | natural  |     |     |     |     |     |     |     |
| --------------- | --- | --------- | ------------ | --- | ----------- | --- | -------- | --- | --- | --- | --- | --- | --- | --- |
utilized the representation of bipartite graph models, but did
language processing, etc. [15]. It is a large-scale semantic  not establish a knowledge graph with ternary relationships.
network that effectively integrates various information and  [21]combined  collaborative  filtering  algorithms  with
| adds  it  | to  a  | knowledge  | base,  | revealing  |     | the  semantic  |     |     |     |     |     |     |     |     |
| --------- | ------ | ---------- | ------ | ---------- | --- | -------------- | --- | --- | --- | --- | --- | --- | --- | --- |
reinforcement learning's reward and punishment mechanism,
information between entities and entity-property relationships.  a time-series-based student rating optimization model was
KGs  are  typically  described  and  stored  using  triplets  of  constructed. The rating results are used as a measure of
"entity-relation-entity."  Embedding  models  are  commonly  students'  preference  for  courses  and  for  recommending
used to map the triplets in the knowledge graph to a low- courses to students. Xu G,Jia G, Shi L, et al.[22]By established
dimensional vector space [16], where each vector represents  a  course-based  knowledge  graph  and  integrating  the
information from the knowledge graph into collaborative
the latent semantic relationship in the knowledge graph.
To  address  these  issues,  this  paper  proposes  a  grade  filtering  recommendation  algorithms,  recommending
resources to learners, the accuracy of collaborative filtering
| prediction  | method  | that  | combines  | educational  |     | knowledge  |     |                  |      |       |            |     |               |       |
| ----------- | ------- | ----- | --------- | ------------ | --- | ---------- | --- | ---------------- | ---- | ----- | ---------- | --- | ------------- | ----- |
|             |         |       |           |              |     |            |     | recommendations  | has  | been  | improved.  |     | The  authors  | used  |
graph with collaborative filtering (KN-CF), which has the
following contributions:  knowledge graph embeddings as inputs for the similarity
|                |     |         |            |     |           |      |         | calculation  | in  collaborative  |     | filtering,  |     | which  | improved  |
| -------------- | --- | ------- | ---------- | --- | --------- | ---- | ------- | ------------ | ------------------ | --- | ----------- | --- | ------ | --------- |
| 1. Extracting  |     | course  | knowledge  |     | entities  | and  | course  |              |                    |     |             |     |        |           |
recommendation effectiveness. However, they overlooked the
relationships to construct a knowledge graph, mapping the
importance of the collaborative filtering algorithm for learning
knowledge graph to a low-dimensional vector space.  from users' historical behaviors.
2. Calculate the similarity between course knowledge graph
|     |     |     |     |     |     |     |     | In  summary,  | there  | is  currently  | more  | research  |     | on  course  |
| --- | --- | --- | --- | --- | --- | --- | --- | ------------- | ------ | -------------- | ----- | --------- | --- | ----------- |
vectors.
recommendation, while research on grade prediction mainly
| 3. Integrating  |     | collaborative  |     | filtering-based  |     |     | course  |     |     |     |     |     |     |     |
| --------------- | --- | -------------- | --- | ---------------- | --- | --- | ------- | --- | --- | --- | --- | --- | --- | --- |
employs bipartite graph models and deep learning methods.
similarity and course knowledge graph similarity for student
Therefore, this paper proposes "Prediction of Students’Grade
grade prediction.  by  Combining  Educational  Knowledge  Graph  and
Experiments are conducted using a dataset collected from
|     |     |     |     |     |     |     |     | Collaborative  | Filtering"  | which  | utilizes  |     | the  rich  | semantic  |
| --- | --- | --- | --- | --- | --- | --- | --- | -------------- | ----------- | ------ | --------- | --- | ---------- | --------- |
users and compared with course-based collaborative filtering
relationships in knowledge graphs to learn user preferences,
(C-CF),  course-based  clustering  (C-KM),  and  user-based  and simultaneously utilizes collaborative filtering to learn
collaborative filtering (U-CF).
historical user preferences, train optimal parameters, linearly
combine the two, and complement each other.
II. RELATED WORK
| The  method  | proposed  |     | in  this  | paper  | is  inspired  |     | by  the  |     |     |     |     |     |     |     |
| ------------ | --------- | --- | --------- | ------ | ------------- | --- | -------- | --- | --- | --- | --- | --- | --- | --- |
III. A GRADE PREDICTION METHOD COMBINING
application of knowledge graphs in recommendation systems,
EDUCATIONAL KNOWLEDGE GRAPH AND
generally speaking, the use of knowledge graphs in prediction  COLLABORATIVE
and  recommendation  methods  is  to  expand  semantic  A. COLLABORATIVE FILTERING RECOMMENDATION
information.For  example,  Geng  L[17]created  behavior  ALGORITHM
| 2   |     |     |     |     |     |     |     |     |     |     |     |     | VOLUME XX, 2017  |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ---------------- | --- |
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/

Author Name: Preparation of Papers for IEEE Access (February 2017)
Collaborative Filtering Recommendation Algorithm includes
User-Based Collaborative Filtering [23] and Item-Based
Collaborative Filtering [24], which are widely used in various
fields such as video, e-commerce websites, music, and
education recommendations. The main idea of this algorithm
is to calculate the similarity between users or items based on
users' historical rating records for items. Then, it recommends
items that users might be interested in or predicts users' ratings
for future items. The implementation of this algorithm can be
divided into three parts, as follows:
1) CONSTRUCTING THE RATING MATRIX
Constructing the user-item rating matrix is the foundation of
collaborative filtering algorithms.Let
2 VOLUME XX, 2017
U = { u
1
,u
2
, u
3
,  , u
m
}
be the set of m users,
I ={i ,i ,i ,,i } R
1 2 3 n be the set of n items, and mn
represent the rating matrix for users' ratings on items, as
shown in formula (1):
R =
m×n
R R R ⋯ R R
11 12 13 1n−1 1n
R R R ⋯ R R
21 22 23 2n−1 2n
R R R ⋯ R R
31 32 33 3n−1 3n （1）
⋮ ⋮ ⋮ ⋮ ⋮
R R R R R
m−11 m−12 m−13 m−1n−1 m−1n
[ R R R R R ]
m1 m2 m3 mn−1 mn
In formula (1), the rating of user u on item I is represented
i j
by R
ij
, where i takes values in the range of [1, m] and j
takes values in the range of [1, n]. A higher rating value
indicates a higher level of preference that user u
i
has for item
I
j
.
2) CALCULATING ITEM SIMILARITY
If two items have a higher similarity, it indicates that the user
has a higher interest in similar items that similar to the
historical items can be recommended to the target user.
Usually, cosine [25], Jaccard, or Pearson algorithms are used
to calculate the similarity between items. Taking cosine
similarity as an example, considering all users’ ratings for a
certain item as an m×1 one-dimensional vector, the rating
vector of item i is represented as F =i { r
1 i
, r
2 i
, r
3 i
, , r
m i
} ,
and the rating vector of item j
values in descending order and selecting the top
is represented as
F ={r ,r ,r ,,r } . Then, calculate the similarity
i 1j 2j 3j mj
between item i and item j is shown in formula (2):
𝐴(𝑖,𝑗) = 𝐹 𝑖 ⋅𝐹 𝑗 = ∑𝑚 𝑢=1 𝑟𝑢𝑖 ⋅𝑟 𝑢𝑗
‖𝐹 𝑖 ‖⋅‖𝐹 𝑗 ‖ √∑𝑚 𝑢=1 𝑟𝑢𝑖 2⋅√∑𝑚 𝑢=1 𝑟𝑢𝑗 2
（2）
In formula (2), A(i,j) represents the cosine similarity value
between item i and item jwith a range of [-1, 1].
3) SELECTING NEIGHBORS
There are typically two methods for selecting neighbors. The
first method involves sorting the computed item similarity
N items as
neighbors, also known as TOP-N. The second method
involves directly setting a threshold value Y and selecting
all items with similarity values greater than Y as neighbor
recommendations. In this paper, the TOP-N method is used
to select neighbors.
B. KNOWLEDGE GRAPH AND METHOD OF
REPRESENTION
The commonly used knowledge graph embedding models
include matrix factorization model, bilinear model, distance-
based model, single-layer neural network model, and
translation model, etc.[26]. Among them, the translation
model, characterized by simple parameters and low algorithm
complexity, is widely applied in knowledge graphs, for
example, the TransE model [27]. For each given triplet
( h , r , t ) in the set S, where h represents the head entity, t
represents the tail entity, and r represents the relationship
between entities, we use E to represent the set of entities h , t ,
i.e., h , t  E , and R to represent the set of entity
relationships, i.e., R r  . The TransE model represents the
embedding vectors of head entity h and tail entity t as h , t ,
respectively, and the embedding vector of relationship entity
r as r , where r is also known as the translation between
vectors h and t . Through continuous training and
adjustment, the model aims to makeh+ r infinitely close to
t , i.e., h + r  t
This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
. The TransE model is illustrated in Figure
1.
FIGURE 1. TransE Model
The loss function of the TransE model is represented by
formula (3):
2
𝑑(ℎ,𝑡,𝑟)=‖ℎ+𝑟−𝑡‖ （3） 2 In the formula(3),d represents the loss function, which is also
the Euclidean distance, and H denotes the L2 norm of the
vectors. For all triplets in the set S, the loss function can be
defined as shown in formula (4):
′ ′
𝐷 =∑ ∑ 𝑚𝑎𝑥(0,𝑑(ℎ,𝑟,𝑡)−𝑑(ℎ,𝑟,𝑡)+ (ℎ,𝑟,𝑡)∈𝑆 (ℎ′,𝑟,𝑡′)∈𝑆′
𝛾)（4）
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/

This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
  Author Name: Preparation of Papers for IEEE Access (February 2017)
| In the formula(4),  | S  represents the set of positive triplets,  |     |     | S    |     |     |     |     |
| ------------------- | -------------------------------------------- | --- | --- | ----- | --- | --- | --- | --- |
Vec
denotes the set of negative triplets obtained by randomly  t C C
|     |     |     |     |     | o r | o u o u |     |     |
| --- | --- | --- | --- | --- | --- | ------- | --- | --- |
replacing the head or tail entity of positive triplets, and  γ     R r s s i m r s
|     |     |     |     |     | e p | e   i e       |     |     |
| --- | --- | --- | --- | --- | --- | ------------- | --- | --- |
|     |     |     |     |     | r e | S e l a r s e |     |     |
represents the distance between positive and negative triplets.  s e m a it m a
|     |     |     |     |     | n t | n y n |     |     |
| --- | --- | --- | --- | --- | --- | ----- | --- | --- |
During the training process of the TransE model, minimizing  a ti t i c t i c
|     |     |     |     |               | on     |     |     |     |
| --- | --- | --- | --- | ------------- | ------ | --- | --- | --- |
|     |     |     |     | C ourse K now | ledge  |     |     |     |
the value of L will make the distance  d ( h ,r ,t )  for positive  G raph Fusion similarity Student Grade
|     |     |     |     |     |     | C urriculu m   |     | Prediction |
| --- | --- | --- | --- | --- | --- | -------------- | --- | ---------- |
|     |     |     |     |     | Sem | antics M odule |     |            |
|     |     |     |     |   |     |                |     |            |
samples approach 0 infinitely, and the distance  d ( h ,r ,t )   S C
|                                |     |      |     |     |     | t u o          |     |     |
| ------------------------------ | --- | ---- | --- | --- | --- | -------------- | --- | --- |
|                                |     |      |     |     |     | d i t l l a    |     |     |
| for negative samples approach  |     |  .  |     |     |     | e n e m b o    |     |     |
|                                |     |      |     |     | M   | t   C   si r a |     |     |
|                                |     |      |     |     | a t | o u m t i      |     |     |
|                                |     |      |     |     | r i | r i l v e      |     |     |
|                                |     |      |     |     | x   | s e   a r  f i |     |     |
| C. TEXTRANK                    |     |      |     |     |     | G i t y l t e  |     |     |
|                                |     |      |     |     |     | r a r in       |     |     |
TextRank is an unsupervised graph-based algorithm that can  d e  g

be used not only for text keyword extraction[28] but also for
|                      |                        |     |                |     |     | C ollaborative     |     |     |
| -------------------- | ---------------------- | --- | -------------- | --- | --- | ------------------ | --- | --- |
|                      |                        |     |                |     |     | F iltering M odule |     |     |
| text  summarization  | generation[29].First,  |     | the  TextRank  |     |     |                    |     |     |
algorithm is used to divide the text into several parts, where  FIGURE 2. Collaborative filtering recommendation algorithm integrated
each part represents a vertex, i.e., a text unit, containing words  with knowledge graph
and sentences. Next, the similarity between each pair of
D. SEMANTIC SIMILARITY OF COURSE KNOWLEDGE
vertices is computed, and the similarity values are assigned to
GRAPH
the related vertex pairs. This process is iteratively performed
The entities and relationships of the course knowledge graph
to calculate the similarity scores between the vertices. Finally,  are embedded into a P-dimensional semantic space using the
the computed scores are stored in a matrix, and the vertex
TransE model, resulting in a semantic vector representation
values are sorted in descending order. The keywords are then
|     |     |     |     | denoted as  | C = ( c | , c , , c | , c ) T ,In the equation,  |     |
| --- | --- | --- | --- | ----------- | ------- | ---------- | -------------------------- | --- |
extracted from the vertices with higher values.  i 1 i 2 i n i p i
In this paper, the TextRank algorithm is employed for text  C  represents  the  semantic  vector  of  course  i  and
i
keyword extraction, which not only takes into account the
|     |     |     |     | 1  n  | p   |     |     |     |
| --- | --- | --- | --- | ------- | --- | --- | --- | --- |
 denotes the semantic value of course i on the n-
contextual context of keyword occurrences but also better
reflects the semantic information of the text. As a result, the  th dimension. Since the TransE model is trained using the
extracted keywords are more specific and highly accurate.  Euclidean distance to compute errors, the semantic similarity
value between two courses is also calculated using the
Traditional collaborative filtering algorithms only consider
the historical rating information of users on items, without  Euclidean distance. The calculation method is illustrated in
Formula (5):
considering the relationship between item semantics, and
cannot deeply explore the correlation between items.This  𝐿(𝐶,𝐶)=√∑𝑝 2
|     |     |     |     |     | 𝑖 𝑗 | (𝑐 𝑛𝑖 | −𝑐 𝑛𝑗 ) |     |
| --- | --- | --- | --- | --- | --- | ----- | ------- | --- |
leads to a limitation in effectively uncovering the correlations  𝑘=1
          (5)

| among  items.  | In  this  paper,  | we  propose  | a  method  | for  |     |     |     |     |
| -------------- | ----------------- | ------------ | ---------- | ---- | --- | --- | --- | --- |
Where  L  represents the semantic distance between any
predicting academic performance by integrating educational
|     |     |     |     | two courses  | C  and  C | . In order to avoid singular values in  |     |     |
| --- | --- | --- | --- | ------------ | --------- | --------------------------------------- | --- | --- |
knowledge graphs with collaborative filtering. We incorporate  i j
the semantic content of course knowledge graphs into the  the calculation results, the distances are normalized using the
collaborative filtering recommendation algorithm, addressing  specific formula shown in Equation (6):
the  deficiency  of  semantic  information  in  the  traditional                          𝐺(𝐶,𝐶)= 1             (6)
𝑖 𝑗
collaborative filtering approach. This integration enhances the  1+𝐿(𝐶𝑖,𝐶𝑗)
|     |     |     |     | In the equation, the range of values for G(C |     |     |     | ,C ) is (0,1].  |
| --- | --- | --- | --- | -------------------------------------------- | --- | --- | --- | --------------- |
accuracy of performance prediction. The algorithmic process  i j
is illustrated in Figure 2.  When the value of G  approaches 1, it indicates that the

|     |     |     |     | semantic similarity between courses C |     |     |  and C |  is higher.  |
| --- | --- | --- | --- | ------------------------------------- | --- | --- | ------ | ------------ |
i j
E. FUSION SIMILARITY
The course-based collaborative filtering algorithm calculates
course similarity based on a matrix of students' historical
course grades. The accuracy of calculating course similarity is
|     |     |     |     | influenced  | by  subjective  | factors.  | For  instance,  | different  |
| --- | --- | --- | --- | ----------- | --------------- | --------- | --------------- | ---------- |
instructors assessing the same questions differently can affect
course grades and subsequently impact the accuracy of course
similarity. Moreover, the algorithm's accuracy is also affected
by data sparsity. High data sparsity, characterized by a lack of
|     |     |     |     | historical  | student-course  | grade  data,  | can  result  | in  lower        |
| --- | --- | --- | --- | ----------- | --------------- | ------------- | ------------ | ---------------- |
| 2   |     |     |     |             |                 |               |              | VOLUME XX, 2017  |
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/

This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
  Author Name: Preparation of Papers for IEEE Access (February 2017)
prediction accuracy.On the other hand, semantic similarity  encompasses comparative experiments, including: course-
between courses is calculated from the perspective of course  based collaborative filtering prediction method (referred to
features.  The  more  comprehensive  the  course  semantic  as  C-CF),  course  clustering-based  prediction  method
(referred to as C-KM), and user-based collaborative filtering
features are, the more accurate the computation of course
similarity becomes. This, in turn, leads to higher accuracy in  prediction method (referred to as U-CF). The experimental
| predicting student grades.  |     |     |     |     |     | steps are outlined as follows:  |     |     |     |     |     |
| --------------------------- | --- | --- | --- | --- | --- | ------------------------------- | --- | --- | --- | --- | --- |
Step 1: Obtain online and offline course content and store
The course semantic similarity obtained from the course
it in TXT format, and organize student course grade data.
knowledge graph and the similarity calculated using the
course-based collaborative filtering algorithm are combined  Step  2:  Extract  entities  and  relationships  from  the
knowledge graph, and construct the course knowledge graph.
through a linear weighted fusion to derive the final similarity.
Step  3: Calculate semantic similarity within the course
The fusion process is represented by Formula (7):
knowledge graph.
𝑊(𝐶,𝐶)=𝛽⋅𝐺(𝐶,𝐶)+(1−𝛽)⋅𝐴(𝑖,𝑗)    (7)
|     | 𝑖 𝑗 | 𝑖 𝑗 |     |     |     | Step  4:  | Compute  |     | similarity  | using  | course-based  |
| --- | --- | --- | --- | --- | --- | --------- | -------- | --- | ----------- | ------ | ------------- |
In  the  Formula(7),  W ( C , C )  represents  the  fused  collaborative filtering.
|             |          | i        | j      |       |            |           |       |           |             |       |              |
| ----------- | -------- | -------- | ------ | ----- | ---------- | --------- | ----- | --------- | ----------- | ----- | ------------ |
|             |          |          |        |       |            | Step  5:  | Fuse  | semantic  | similarity  | from  | the  course  |
| similarity  | between  | courses  | C and  | C , G | ( C ,C )   |           |       |           |             |       |              |
i j i j knowledge graph and course-based collaborative filtering
similarity (KN-CF).
| signifies  | the  semantic  | similarity  | based  | on  | the  course  |     |     |     |     |     |     |
| ---------- | -------------- | ----------- | ------ | --- | ------------ | --- | --- | --- | --- | --- | --- |
Step  6: Utilize the fused similarity for predicting student
| knowledge  | graph,  | and  A ( i | , j )  denotes  | the  | similarity  |     |     |     |     |     |     |
| ---------- | ------- | ---------- | --------------- | ---- | ----------- | --- | --- | --- | --- | --- | --- |
grades.
calculated through the course-based collaborative filtering.
Step  7: Compare KN-CF with C-CF, C-KM, and U-CF
| β is the weighting factor, with a range of values between  |                                                   |     |     |     |     | methods.  |     |     |     |     |     |
| ---------------------------------------------------------- | ------------------------------------------------- | --- | --- | --- | --- | --------- | --- | --- | --- | --- | --- |
| [0,1]. When                                                | β  lies within the range of (0,1), it represents  |     |     |     |     |           |     |     |     |     |     |
A. DATASET AND PREPROCESSING
β
the fused similarity. When   is equal to 1, it corresponds to  The experimental data for this study was sourced from the
the similarity derived from the course knowledge graph.  School of Big Data and Artificial Intelligence, Software
When  β  is equal to 0, it corresponds to the similarity  Engineering program, Anhui Xinhua University. The dataset
comprises two main components: student grades and course
obtained from collaborative filtering.
|     |     |     |     |     |     | semantic  information.  |     | The  | course  | semantic  | information  |
| --- | --- | --- | --- | --- | --- | ----------------------- | --- | ---- | ------- | --------- | ------------ |
includes details about MOOC[30] courses and attributes of
F. COURSE GRADE PREDICTION
course materials ,such as textbook name, author, publisher,
Predicting the course a certain student is about to study,
publication year.
based on Formula (7), the calculation formula for grade
1) PROCESSING STUDENT GRADE DATA
prediction is given by Formula (8):
|     |     |     |     |     |     | These  records  | contain  |     | the  course  | scores  | of  software  |
| --- | --- | --- | --- | --- | --- | --------------- | -------- | --- | ------------ | ------- | ------------- |
∑𝑗∈𝑌(𝑖,𝑁)𝑊(𝐶𝑖,𝐶𝑗)⋅𝑟𝑢𝑗  (8)  engineering  students  enrolled  in  2015,  2016  and  2017
|                                𝑍 |     | =   |     |     |     |     |     |     |     |     |     |
| -------------------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
𝑢𝑖 𝑊(𝐶𝑖,𝐶𝑗) cohorts over a period of four years, spanning 8 semesters.
However, the 8th semester includes internships and thesis
In  the  equation,  Z  represents  the  predicted  course  defense without examinable courses. Therefore, only grades
u
i from  the  1st  to  7th  semesters  are  selected  for  the
|     |     | u   | i Y ( i,N | )   |     |     |     |     |     |     |     |
| --- | --- | --- | --------- | --- | --- | --- | --- | --- | --- | --- | --- |
grade for student   in course  .   signifies the N  experimental dataset. Furthermore, various subjects adhere
courses most similar to course  i .  r  denotes the historical  to  distinct  assessment  standards,  with  some  employing
u
j percentage grading and others using a letter-grade system. In
|     |     | u   |     | j   |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
grades of student   in their past courses  .  W ( C , C )   order to standardize data types, a normalization process will
|     |     |     |     |     | i j |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
be performed to convert scores into a range of 1 to 5 at our
stands for the fused similarity.
A  parenthetical  statement  at  the  end  of  a  sentence  is  school, as shown in Table I.

punctuated outside of the closing parenthesis (like this). (A
TABLE I
parenthetical sentence is punctuated within the parentheses.)
GRADE LEVEL REPRESENTATION
In  American  English,  periods  and  commas  are  within
quotation marks, like “this period.” Other punctuation is  Original Data(grade)  Transformed(grade)
“outside”! Avoid contractions; for example, write “do not”
|     |     |     |     |     |     | 9 0  g r a d | e  1 0 | 0   ；Excellent  |     |     | 5   |
| --- | --- | --- | --- | --- | --- | ------------- | ------- | --------------- | --- | --- | --- |
instead of “don’t.” The serial comma is preferred: “A, B, and
C” instead of “A, B and C.”
|     |     |     |     |     |     | 80  grade | 90  ；Good  |     |     |     | 4   |
| --- | --- | --- | --- | --- | --- | ---------- | ----------- | --- | --- | --- | --- |
IV. EXPERIMENTAL METHODOLOGY
|     |     |     |     |     |     | 70 grade80  ；Average  |     |     |     |     | 3   |
| --- | --- | --- | --- | --- | --- | ----------------------- | --- | --- | --- | --- | --- |
The experimental design for this study consists of two main
parts. The first part involves the integration of educational
|             |            |                     |            |              |             | 60  grade70 |     |   ；Pass  |     |     | 2                |
| ----------- | ---------- | ------------------- | ---------- | ------------ | ----------- | ------------- | --- | -------- | --- | --- | ---------------- |
| knowledge   | graphs     | and  collaborative  | filtering  |              | for  grade  |               |     |          |     |     |                  |
| prediction  | (referred  | to  as  KN-CF).     |            | The  second  | part        |               |     |          |     |     |                  |
| 2           |            |                     |            |              |             |               |     |          |     |     | VOLUME XX, 2017  |
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/

Author Name: Preparation of Papers for IEEE Access (February 2017)
2 VOLUME XX, 2017
0  g r a d e  6 0
This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
；Fail 1 acquisition is divided into two parts: offline course
knowledge data and online course knowledge data. For
offline course knowledge data, information is extracted from
The processed dataset consists of a total of 14,898 grade physical textbooks and supplementary materials. Due to the
records. limitations or singular nature of offline resources, web
scraping techniques are employed to extract course textbook
outline information from the internet, serving as a
2) PROCESSING COURSE SEMANTIC DATA
complement to online course knowledge data.
The course semantic information primarily involves the
collection of course knowledge point data, including course
names, course descriptions, and course outlines. Some B. CONSTRUCTION OF KNOWLEDGE GRAPH
knowledge points come from offline teaching material In this paper, knowledge units are extracted from online and
information, but since the content of the offline teaching offline educational and teaching resources of different courses
material is less or not comprehensive enough, more online to form a course knowledge graph. Choose Python language
information related to the course is crawled by web crawler programming design course and build knowledge graph as
to supplement the knowledge content.This knowledge shown in Figure 3:
FIGURE 3. The knowledge graph of Python programming course
The steps to construct the knowledge graph are as follows: entities in the course knowledge graph, to mitigate
Step 1: Utilizing the TextRank algorithm, extract construction costs, only the top 20 most significant entities are
knowledge points from all corresponding online and offline extracted from each course. The extraction results are depicted
content for each course, representing them as entities in the in Table II.
knowledge graph. Given the potentially high number of Step 2: Define relationships between entities in the
knowledge graph and create triples, as illustrated in Table III.
TABLE Ⅱ
EXTRACTION OF COURSE ENTITIES
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/

This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
  Author Name: Preparation of Papers for IEEE Access (February 2017)
Course name  Entity
Control Form Statement File Data Type Menu
.NET Programming
Array Instance Dialog Box Control Structure
|     |     | Function  | Array  | Pointer  |     | C++  Programming  |
| --- | --- | --------- | ------ | -------- | --- | ----------------- |
C++language programming  Operator  Statement  Structure  Definition
Constructor
Statement Implementation Data Type Object
| J2EE framework  |     | Mapping  | Form  | Application  |     | Form  Dynamic  |
| --------------- | --- | -------- | ----- | ------------ | --- | -------------- |
Configuration
|     |     | network  | security  |     | computer  | virus  encryption  |
| --- | --- | -------- | --------- | --- | --------- | ------------------ |
encryption algorithm

Computer technology algorithm authentication
Information Security
cryptography information security

TABLE Ⅲ
|              |                   | CONSTRUCTION OF COURSE TRIPLETS |     |                            |                     |        |
| ------------ | ----------------- | ------------------------------- | --- | -------------------------- | ------------------- | ------ |
| Entity       |                   | Relation                        |     |                            | Entity              |        |
| Student      | Course Name       |                                 |     |                            |                     | Score  |
| course name  |                   | Include                         |     |                            | Keyword Entity      |        |
| course name  |                   | Textbook                        |     |                            | Textbook Name       |        |
| course name  |                   | Author                          |     |                            | Author Name         |        |
| course name  | publishing house  |                                 |     |                            | Concrete publisher  |        |
| course name  |                   | Time                            |     | Specific publication time  |                     |        |
| course name  |                   | Course type                     |     |                            | Elective            |        |
| course name  |                   | Belong                          |     |                            | Specific Category   |        |
2  VOLUME XX, 2017
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/

Author Name: Preparation of Papers for IEEE Access (February 2017)
Table III shows the 8 triplet relationships established in this
experiment, and the knowledge graph is created according to
these 8 triplet relationships.
Based on the aforementioned rules, the dataset used in this
study eventually forms 15,957 triples in the course knowledge
graph. Among these triples, 80% are allocated for the training
set, 10% for the validation set, and the remaining 10% for the
test set.
C. EVALUATION METRICS
In this experiment, the commonly used evaluation metrics in
recommendation systems,Evaluation methods in
recommendation systems are divided into two types: TOP-N
recommendation and rating prediction. TOP-N
recommendation mainly measures the hit rate, commonly
using metrics such as F1, recall, precision[31][32][33],etc.
Rating prediction mainly measures the error range and
commonly uses the Root Mean Square Error (
2 VOLUME XX, 2017
R M S E ) ,
(Mean Absolute Error ( M A E ) [34][4], are employed as
evaluation criteria. These metrics have a range of [ 0 , +  ] ,
with values approaching 0 indicating a closer alignment
between actual and predicted values, thereby making R M S E
and M A E closer to 0. Conversely, larger values indicate
greater errors, approaching + 
∧
𝑅𝑀𝑆𝐸
=√∑𝑥
𝑖=1
(𝑃𝑖−𝑃𝑖)2
(9)
𝑥
In the equation:
. The calculation formulas
are illustrated in Equations (9) and (10).
R M S E represents the Root Mean Square
Error (RMSE) of predicted student grades. i denotes the
current prediction of course grade.P represents the predicted
i

grade for the i-th course. P signifies the actual grade for
i
the i-th course. x represents the total number of courses.
The specific formula for MAE, as shown in Equation (10),
is as follows:
∑𝑥 𝑖=1|𝑃𝑖−𝑃 ∧ 𝑖|
𝑀𝐴𝐸 = (10)
𝑥
In the equation, M A E represents the Mean Absolute
Error of predicted student grades. i denotes the current
prediction of course grade. P i represents the predicted grade
for the i -th course.
P
i
signifies the actual grade for the i -th
course. x
This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
represents the total number of courses.
The main contributions of this paper are summarized in Table
IV.
TABLE Ⅳ
CONTRIBUTION OF PAPER
Method Contribution
Build a knowledge graph Learn more knowledge and expand the modle’s
information
Computing KG similarity Conputing course similarity from a semantic perspective
Fused KG-CF Enhancing collaborative filtering recommendation
methods
experimental results for different weight values of  are
V. EXPERIMENTAL RESULTS ANALYSIS depicted in Figures 3 and 4.
A. EXPERIMENTAL PROCEDURE
First, the construction of the course knowledge graph is
performed according to the methods described in Section 3.2.
Then, the similarity of the knowledge graph is calculated
using the Euclidean formula as shown in equation (3). Finally,
the results of the knowledge graph and collaborative filtering
similarity are combined, and the recommendation list is
computed.
B. PARAMETER TRAINING
In accordance with Equation (7), for the fusion experiment,
Figure 3. RMSE Results under Different Weight Values
the weight of  is varied within the range of 0 to 1 with a
step size of 0.1. The average values of the evaluation metrics
for semesters 1 to 7 for RMSEand MAE are computed. The
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/

This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
Author Name: Preparation of Papers for IEEE Access (February 2017)
FIGURE 4. MAE Results under Different Weight Values
From Figures 3 and 4, it can be observed that when  is
set to 0.4, the values of RMSE and MAE for the grade
prediction method that combines educational knowledge FIGURE 5. RMSE Comparison Results
graph and collaborative filtering are minimized. Therefore, in
this experiment, the value of  is chosen as 0.4.
C. EXPERIMENTAL RESULTS AND ANALYSIS
The experiments are conducted in four groups, comparing
course-based collaborative filtering (C-CF), course
clustering-based (C-KM), user-based collaborative filtering
(U-CF), and the proposed grade prediction method that
combines educational knowledge graph and collaborative
filtering (KN-CF).
1)C-CF This is a course-based collaborative filtering
prediction method. This method calculates the similarity
between courses based on a user's historical courses and
ratings, and predicts grades.
FIGURE 6. MAE Comparison Results
2)C-KM Rating prediction method based on course clustering. From Figures 5 and 6, it can be observed that, except for the
This method establishes a course knowledge graph, clusters 2nd semester, the fused method of course knowledge graph
courses, and predicts grades based on the similarity of and collaborative filtering generally outperforms course-
courses within the same cluster. based collaborative filtering, user-based collaborative filtering,
3)U-CF User-based collaborative filtering prediction method. and K-means-based methods in terms of RMSE and MAE
This method calculates similar users to the target user and metrics. This indicates that the course knowledge content
predicts course exam grades based on the similarity between learned by the knowledge graph contributes to the discovery
users. of knowledge relevance, enhancing the accuracy of similarity
computation and reducing prediction errors. The relatively
4)KN-CF The method proposed in this paper, based on
higher errors in the 2nd semester are likely due to the fact that
combining educational knowledge graph and collaborative
the courses undertaken by students during that period are
filtering, is compared with the methods mentioned above.
primarily common courses. As specialized courses increase in
In the experiment,with β set to 0.4, the comparative results
subsequent semesters, the content becomes more interrelated,
of the four groups in terms of RMSE and MAE metrics are
and the knowledge learned by the graph becomes more
illustrated in Figures 5 and 6, respectively.
accurate in describing the courses. Thus, overall, the fused
approach of course knowledge graph and collaborative
filtering exhibits lower RMSE and MAE errors compared to
other methods.
The results of grade prediction for four groups from the 2nd
semester to the 7th semester in terms of RMSE and MAE
metrics are shown in Table V,VI：
TABLE V
COMPARISON RESULT OF RMSE
Term-2 Term-3 Term-4 Term-5 Term-6 Term-7
RMSE RMSE RMSE RMSE RMSE RMSE
VOLUME XX, 2017 7
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/

This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
  Author Name: Preparation of Papers for IEEE Access (February 2017)
|     | C-CF   |     | 1.3615  |     | 1.4439  | 1.1539  |     | 1.1310  |     |     | 1.0885  | 1.0376  |     |     |
| --- | ------ | --- | ------- | --- | ------- | ------- | --- | ------- | --- | --- | ------- | ------- | --- | --- |
|     | C-KM   |     | 1.1239  |     | 1.0725  | 1.0396  |     | 1.0611  |     |     | 0.9720  | 0.9980  |     |     |
|     | U-CF   |     | 1.1602  |     | 1.1686  | 1.1775  |     | 1.2133  |     |     | 1.0276  | 1.0923  |     |     |
|     | KN-CF  |     | 1.2068  |     | 0.9516  | 0.9802  |     | 0.9823  |     |     | 0.8929  | 0.9408  |     |     |

TABLE VI
COMPARISON RESULT OF MAE
|     |     | Term-2  |     | Term-3  |     | Term-4  |     | Term-5  |     | Term-6  |     | Term-7  |     |     |
| --- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | --- |
|     |     | MAE     |     | MAE     |     | MAE     |     | MAE     |     | MAE     |     | MAE     |     |     |
|     | C-  | 1.0702  |     | 1.1684  |     | 0.8435  |     | 0.8414  |     | 0.7962  |     | 0.7670  |     |     |
CF
|     | C-  | 0.8464  |     | 0.8124  |     | 0.8052  |     | 0.8068  |     | 0.7238  |     | 0.7435  |     |     |
| --- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | --- |
KM
|     | U-  | 0.8521  |     | 0.8774  |     | 0.8545  |     | 0.9068  |     | 0.7264  |     | 0.8246  |     |     |
| --- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | --- |
CF
|     | KN- | 0.9280  |     | 0.7046  |     | 0.7298  |     | 0.7382  |     | 0.6418  |     | 0.7035  |     |     |
| --- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | ------- | --- | --- |
CF
From TABLE V and TABLE VI it can be shown that the  course customization, course recommendations, and other
| method proposed in this paper performs poorly in terms of  |     |     |     |     |     |     | related areas.  |     |     |     |     |     |     |     |
| ---------------------------------------------------------- | --- | --- | --- | --- | --- | --- | --------------- | --- | --- | --- | --- | --- | --- | --- |
MAE and RMSE metrics in the second semester. The reason  Therefore, in future research, the next step would involve
for this is that the first two semesters mainly consist of general  applying  the  grade  prediction  method  that  combines
education courses such as English and mathematics. It is only  educational knowledge graph and collaborative filtering to
after the second semester that more professional courses are
|     |     |     |     |     |     |     | larger  | public  | online  | education  |     | datasets  | for  experimental  |     |
| --- | --- | --- | --- | --- | --- | --- | ------- | ------- | ------- | ---------- | --- | --------- | ------------------ | --- |
offered, where the semantic relationships in the knowledge
verification.
graph can be better manifested. Therefore, starting from the
second semester, the effectiveness of the model proposed in
ACKNOWLEDGMENT
this paper is optimal. This is because through the knowledge
This research is supported by the Natural Science Foundation
graph, a large number of semantic relationships between
|     |     |     |     |     |     |     | of  | Anhui  |     | Provincial  |     | Education  | Department  |     |
| --- | --- | --- | --- | --- | --- | --- | --- | ------ | --- | ----------- | --- | ---------- | ----------- | --- |
courses are learned, improving the accuracy of similarity
(KJ2020A0784,KJ2021A1159), Anhui Province teaching and
| calculation  | between  | courses.  | Additionally,  |     | by  integrating  |     |     |     |     |     |     |     |     |     |
| ------------ | -------- | --------- | -------------- | --- | ---------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
research project(2021jyxm0616).
| collaborative  | filtering  | methods,  |     | the  model  | learns  | from  |     |     |     |     |     |     |     |     |
| -------------- | ---------- | --------- | --- | ----------- | ------- | ----- | --- | --- | --- | --- | --- | --- | --- | --- |
students' historical learning behaviors, thus enhancing the
| accuracy of the model's predictions.         |     |     |     |     |     |     |             |     |     |     |     |     |     |     |
| -------------------------------------------- | --- | --- | --- | --- | --- | --- | ----------- | --- | --- | --- | --- | --- | --- | --- |
| VI. CONCLUSION,RECOMMENDATIONS,IMPLICATIONS, |     |     |     |     |     |     | REFERENCES  |     |     |     |     |     |     |     |
AND FUTURE WORK  [1]  Chen  K.  Research  on  prediction  model  of  College  Students'
This study addresses the limitations of collaborative filtering  Academic Achievement based on Time Series Analysis[D]. Wuhan:
methods, which heavily rely on historical student grades and  Central China Normal University, 2021. (in Chinese)
[2]  Yang Z, Zeng Z, Wang K, et al. Modified SEIR and AI prediction of
often overlook semantic information of courses as well as the  the epidemics trend of COVID-19 in China under public health
influence of subjective factors on course grades. A novel  interventions[J]. Journal of thoracic disease, 2020, 12(3): 165.
approach  is  proposed  for  grade  prediction,  combining  [3]  Sun X, Zhao X, Ma Y, et al. Muti-behavior features based knowledge
tracking using decision tree improved DKVMN[C]//Proceedings of
| educational  | knowledge  | graphs  | and  | collaborative  |     | filtering.  |     |     |     |     |     |     |     |     |
| ------------ | ---------- | ------- | ---- | -------------- | --- | ----------- | --- | --- | --- | --- | --- | --- | --- | --- |
the ACM Turing Celebration Conference-China. 2019: 1-6.
This approach bridges the gap in computing course similarity
[4]  Ren C L, Wang X L. Research on Students’ Performance Portrait
within  collaborative  filtering  algorithms  by  incorporating  Method Based on Multidimensional Data[C]//Journal of Physics:
knowledge semantics. Experimental results demonstrate that  Conference Series. IOP Publishing, 2019, 1237(3): 032－043.
[5]  Zhu C, Sun W, Liu Q, et al. HomoTR: online test recommendation
the proposed method achieves better results in terms of RMSE
|     |     |     |     |     |     |     |     | system  | based  | on  homologous  |     | code  matching[C]//2020  |     | 35th  |
| --- | --- | --- | --- | --- | --- | --- | --- | ------- | ------ | --------------- | --- | ------------------------ | --- | ----- |
and MAE metrics compared to other methods.However, the
|     |     |     |     |     |     |     |     | IEEE/ACM  | International  |     | Conference  | on  | Automated  | Software  |
| --- | --- | --- | --- | --- | --- | --- | --- | --------- | -------------- | --- | ----------- | --- | ---------- | --------- |
dataset used in this experiment is relatively small, potentially
Engineering (ASE). IEEE, 2020: 1302-1306.
introducing  some  errors.  The  algorithm  that  combines  [6]  Li H, Li H, Zhang S, et al. Intelligent learning system based on
knowledge graph and collaborative filtering can learn more  personalized recommendation technology[J]. Neural Computing and
  Applications, 2019, 31(9): 4455-4462.
knowledge relationships from
[7]  Burman I, Som S. Predicting students academic performance using
  support vector machine[C]//2019 Amity international conference on
knowledge-rich educational datasets, leading to improved  artificial intelligence (AICAI). IEEE, 2019: 756-759.
prediction accuracy.   [8]  Deho O B, Liu L, Joksimovic S, et al. Assessing the Causal Impact
The research findings can provide a basis for relevant  of Online Instruction due to COVID-19 on Students’ Grades and its
aftermath on Grade Prediction Models[C]//Proceedings of the 2022
studies in the knowledge-rich field of education. For example,  ACM Conference on Information Technology for Social Good. 2022:
| they can contribute to student grade prediction, personalized  |     |     |     |     |     |     |     | 32-38.  |     |     |     |     |     |     |
| -------------------------------------------------------------- | --- | --- | --- | --- | --- | --- | --- | ------- | --- | --- | --- | --- | --- | --- |
| VOLUME XX, 2017                                                |     |     |     |     |     |     |     |         |     |     |     |     |     | 7   |
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/

This article has been accepted for publication in IEEE Access. This is the author's version which has not been fully edited and
content may change prior to final publication. Citation information: DOI 10.1109/ACCESS.2024.3390675
Author Name: Preparation of Papers for IEEE Access (February 2017)
[9] Zhang Y, Jiang W. Score Prediction Model of MOOCs Learners [23] Lavanya R, Bharathi B. Movie Recommendation System to Solve
Based on Neural Network[J]. International Journal of Emerging Data Sparsity Using Collaborative Filtering Approach[J].
Technologies in Learning (iJET), 2018, 13(10): 171-182. Transactions on Asian and Low-Resource Language Information
[10] Ma Y, Cui C, Nie X, et al. Pre-course student performance prediction Processing, 2021, 20(5): 1-14
with multi-instance multi-label learning[J]. Science China [24] Truong Q T, Salah A, Lauw H W. Bilateral variational autoencoder
Information Sciences, 2019, 62(2): 1-3. for collaborative filtering[C]//Proceedings of the 14th ACM
[11] Bujang S D A, Selamat A, Ibrahim R, et al. Multiclass prediction International Conferenceon Web Search and Data Mining.2021: 292-
model for student grade prediction using machine learning[J]. IEEE 300.
Access, 2021, 9: 95608-95621. [25] Xiao W Q,Yao S J,Wu S M.An improved Top-N collaborative
[12] Xue M T. Research on Prediction of College Students' Achievement filtering recommendation algorithm[J].Computer Application
based on Neighborhood Collaborative Filtering[J]. Modern computer, research, 2018, 35(01): 105-108+112.(in Chinese)
2020(05): 26-29. (in Chinese) [26] Rossi A, Barbosa D, Firmani D, et al. Knowledge graph embedding
[13] Huang L, Wang C D, Chao H Y, et al. A score prediction approach for link prediction: A comparative analysis[J]. ACM Transactions on
for optional course recommendation via cross-user-domain Knowledge Discovery from Data (TKDD), 2021, 15(2): 31-49.
collaborative filtering[J]. IEEE Access, 2019, 7: 19550-19563. [27] Bordes A, Usunier N, Garcia-Duran A, et al. Translating embeddings
[14] Ceyhan M, Okyay S, Kartal Y, et al. The Prediction of Student for modeling multi-relational data[J].Advances in neural information
Grades Using Collaborative Filtering in a Course Recommender processing systems, 2013, 26.
System[C]//2021 5th International Symposium on Multidisciplinary [28] Tian X. Study on keyword extraction using word position weighted
Studies and Innovative Technologies (ISMSIT). IEEE, 2021: 177- TextRank[J]. Data Analysis and Knowledge Discovery, 2013, 29(9):
181. 30-34.
[15] Wang M, Qiu L, Wang X. A Survey on Knowledge Graph [29] Huynh H T, Duong-Trung N, Truong D Q, et al.Vietnamese text
Embeddings for Link Prediction[J]. Symmetry, 2021, 13(3): 485. classification with textrank and jaccard similarity coefficient[J]. Adv.
[16] Wang Q, Mao Z, Wang B, et al. Knowledge graph embedding: A Sci. Technol. Eng. Syst, 2020, 5(6): 363-369.
survey of approaches and applications[J]. IEEE Transactions on [30] Luo Y ,Zhou G ,Li J , et al.Study on MOOC scoring algorithm based
Knowledge and Data Engineering, 2017, 29(12): 2724- 2743. on Chinese University MOOC learning behavior
[17] Geng L. The recommendation system of innovation and data[J].Heliyon,2018,4(11): 960-972.
entrepreneurship education resources in universities based on [31] Ray B, Garain A, Sarkar R. An ensemble-based hotel recommender
improved collaborative filtering model[J]. Computational system using sentiment analysis and aspect categorization of hotel
Intelligence and Neuroscience, 2022, 2022:1-9. reviews[J]. Applied Soft Computing, 2021, 98: 106935.
[18] Wang H, Zhao M, et al. Knowledge graph convolutional networks [32] Wang H, Zhao M, Xie X, et al.Knowledge graph convolutional
for recommender systems[C].The world wide web conference. networks for recommender systems[C].The world wide web
2019,3307-3313. conference, 2019: 3307-3313.
[19] Lu X, Zhu Y, Xu Y,et al.Learning from multiple dynamic graphs of [33] Darban Z,Z,Valipour M H.GHRS: Graph-based hybrid
student and course interactions for student grade recommendation system with application to movie
predictions[J].Neurocomputing,2021, 431:23-33. recommendation[J]. Expert Systems with Applications, 2022, 200:
[20] Wang Q, Cao X, Wang J, et al. Knowledge-aware collaborative 116850.
filtering with pre-trained language model for personalized review- [34] Choudhury S S, Mohanty S N, Jagadev A K. Multimodal trust based
based rating prediction[J]. IEEE Transactions on Knowledge and recommender system with machine learning approaches for movie
Data Engineering, 2023,36(3):1170-1182. recommendation[J].International Journal of Information Technology,
[21] Scientific Programming and Artificial Intelligence for Sensor Data 2021, 13: 475-482.
Stream Analysis
[22] Xu G, Jia G, Shi L,et al. Personalized course recommendation system
fusing with knowledge graph and collaborative filtering[J].
Computational Intelligence and Neuroscience, 2021, 2021: 1-8
environmental issues, human-computer interaction, IT education, Internet
studies, mobile learning, and web usability.
YIWEN ZHANG was born in FuYang
ANHUI,CHINA in 1980. She received the B.S. and M.S. degrees in
Universityof Science and Technologe of China, in 2009.
Since 2019, she has been an Professor with the Big Data and artificial
intelligence Department, Texas A&M University, College Station. she is
the author of two books, more than 30 articles, and more than 10 inventions.
Her research interests include recommendation algorithm and
recommendation system, educational recommendation method ,application
of prediction method in weather environment.
Vladimir Y.Mariano is a full professor at the College of Computing
and Information Technologies,National University, Manila, Philippine.His
research interests include image processing and pattern
recognition,iIntelligent information processing.
Rex P. Bringula is a full professor at the University of the East (UE)
College of Computer Studies and Systems. He has published more than 100
papers. His research interests are in affective computing, cyber-behavior,
VOLUME XX, 2017 7
This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 License. For more information, see https://creativecommons.org/licenses/by-nc-nd/4.0/