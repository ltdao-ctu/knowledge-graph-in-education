---
title: "Cheng2026proprl"
source: "Cheng2026proprl.pdf"
source_sha256: "d0468a5f46bdab12051f714a1f01de7df968d5191423dc0a792c55652ccfe4c8"
converted_at: "2026-10-26T07:04:55.732974+00:00"
markitdown_version: "0.1.9"
---
ProPRL: Property-Aware Prerequisite Relation Learning in Educational
|     |     |     |     | Knowledge | Graphs |     |     |     |
| --- | --- | --- | --- | --------- | ------ | --- | --- | --- |
XingheCheng1,JiapuWang2,ChaoboHe3,RuihaiDong4,QuanlongGuan1
1JinanUniversity
2NanjingUniversityofScienceandTechnology
3SouthChinaNormalUniversity
3UniversityCollegeDublin
chengxh@stu2023.jnu.edu.cn,jiapuwang9@gmail.com,hechaobo@m.scnu.edu.cn
gql@jnu.edu.cn,ruihai.dong@ucd.ie
Abstract
| Prerequisite | relation learning | is  | central to adaptive | instruc- |     |     |     |     |
| ------------ | ----------------- | --- | ------------------- | -------- | --- | --- | --- | --- |
tion,yetexistingmethodsoftenformulateitasconventional
| link prediction, | limiting    | their ability | to adaptively  | integrate |     |     |     |     |
| ---------------- | ----------- | ------------- | -------------- | --------- | --- | --- | --- | --- |
| complementary    | educational | evidence      | for individual | candi-    |     |     |     |     |
datepairsandtodiscouragecontradictoryreversepredictions.
6202 guA 4  ]IA.sc[  1v60030.8062:viXra
WeproposeProPRL,aProperty-awarePrerequisiteRelation
| Learning framework. | ProPRL |     | first learns complementary |     |     |     |     |     |
| ------------------- | ------ | --- | -------------------------- | --- | --- | --- | --- | --- |
conceptrepresentationsfromaconcept-resourcehypergraph
| and a directed | learning-behavior |     | graph, where | direction- |     |     |     |     |
| -------------- | ----------------- | --- | ------------ | ---------- | --- | --- | --- | --- |
Figure1:Representationhomogenizationofknowledgecon-
preservingpersonalizedpropagationaggregatesmulti-hopbe-
cepts.Left:Conceptsexhibithighsimilarityinthepretrained
havioralevidence.ItthenemploysaPair-conditionedGateto
adaptivelyweightandfusethetwoviewsforeachcandidate semanticspace.Right:DuringDGCPL(Zhangetal.2025a)
orderedconceptpair.Finally,anIrreversibilityConstraintin- training, 62.7% of prerequisite pairs become increasingly
| troducesananti-symmetryregularizerthatpenalizessimulta- |     |     |     |     | similar. |     |     |     |
| ------------------------------------------------------- | --- | --- | --- | --- | -------- | --- | --- | --- |
neouslyhighconfidenceinbothdirectionsofthesameconcept
pair.Experimentsonmultiplereal-worldeducationaldatasets
| show that ProPRL | achieves | state-of-the-art | performance | on  |     |     |     |     |
| ---------------- | -------- | ---------------- | ----------- | --- | --- | --- | --- | --- |
MOOCresources(Huetal.2021).Tocapturemoreintricate
prerequisiterelationlearning.
dependencies,currentmodelsshifttowardscomplextopolo-
gies,utilizingheterogeneousgraphneuralnetworkstomap
Introduction
|     |     |     |     |     | relations | across concepts | and resources. These | frameworks |
| --- | --- | --- | --- | --- | --------- | --------------- | -------------------- | ---------- |
As a core pillar of smart education, personalized learn- increasingly integrate multi-view structures and learning
ing fundamentally relies on accurate domain knowledge paths to characterize dependencies from broader data
structures to facilitate adaptive instructional decision- dimensions(Sun,Li,andZhang2022;Zhangetal.2025b).
making (Cheng et al. 2025; Abdelrahman, Wang, and Despitetheseadvances,mostexistingmethodsreducepre-
Nunes2023).Withinthesestructures,prerequisiterelations requisite relation prediction to conventional link prediction
serveasfoundationalcomponentsthatmapthehierarchical
andinferrelationsprimarilyfromembeddingproximity.As
dependencies between knowledge concepts (Zhang et al. shown in Figure 1(a), prerequisite pairs, labeled negative
2025a). However, modeling these relations in real-world pairs, and random non-edges exhibit similarly high initial
educational settings is often hindered by the scarcity of semantic similarities, making them difficult to distinguish.
reliable expert annotations and the inherent noise in auto- Figure 1(b) further shows that GNN training significantly
mated extraction methods (Cheng et al. 2026). Prerequisite increasesthesimilarityofmanyconceptpairs,progressively
relation learning aims to mitigate these challenges by homogenizingtheirrepresentations.Theseobservationsmo-
inferring implicit dependencies from diverse educational tivate the explicit modeling of three important characteris-
data,therebyestablishingamorerobuststructuralbasisfor tics:directionalasymmetry,multi-hopbehavioralevidence,
| effective,adaptiveinstruction. |     |     |     |     | andpair-specificrelevance. |     |     |     |
| ------------------------------ | --- | --- | --- | --- | -------------------------- | --- | --- | --- |
The methodological paradigm of prerequisite relation First, prerequisite relations are intrinsically asymmetric
learning has undergone a definitive transition from feature- anddirectionallyirreversible(Alzettaetal.2018;Yangetal.
centricheuristicstoexpressivegraphrepresentations(Liang 2024).Whenconceptc isaprerequisiteofc ,assigninghigh
|     |     |     |     |     |     |     | i   | j   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
et al. 2015; Mazumder, Paik, and Basu 2023). Historically, confidencetothereverserelationc →c wouldintroducea
|     |     |     |     |     |     |     | j i |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
early studies mainly relied on manually designed features, directional contradiction. Yet, conventional link prediction
textual links, or course dependency structures, applying models evaluate these directed pairs independently, failing
thesemetricswidelytoWikipedia,universitycurricula,and
|     |     |     |     |     | to explicitly | penalize     | such inverse combinations. | This fun-     |
| --- | --- | --- | --- | --- | ------------- | ------------ | -------------------------- | ------------- |
|     |     |     |     |     | damental      | misalignment | frequently produces        | contradictory |

bidirectional predictions, thereby degrading the directional RelatedWork
consistencyofthegraphandinherentlylimitingthetaskof Feature-Based Concept Prerequisite Relation Learning.
accuratelyresolvingasymmetricconceptualdependencies.
Concept prerequisite relation learning aims to identify di-
Second, prerequisite relations often manifest as latent recteddependenciesbetweenknowledgeconcepts,whichis
multi-hop dependencies rather than explicit one-step fundamental to curriculum planning, learning path recom-
transitions in learner behaviors (Talukdar and Cohen 2012; mendation, and intelligent tutoring (Liang et al. 2015; Roy
Xiao, Bai, and Zhang 2022). Even when concepts c and et al. 2019). Early studies mainly formulated this task as a
i
c are not studied consecutively, intermediate interactions feature-based prediction problem. For example, RefD mea-
j
(e.g., c → c → c ) provide vital indirect prerequisite sures prerequisite relations by exploiting asymmetric ref-
i k j
evidence. Yet, conventional behavior modeling frameworks erence patterns between Wikipedia concepts (Liang et al.
are largely tethered to local transition heuristics. This 2015),whilecoursedependencyinformationhasbeenused
shortsightednesspreventsthemfromeffectivelypropagating to recover concept-level prerequisite relations from univer-
structural signals across the behavioral graph, thereby sitycurricula(Liangetal.2017).Withthegrowthofonline
losing the long-range dependencies required to accurately educationalresources,subsequentstudieslearnedprerequi-
reconstructtheunderlyingknowledgetopology. siterelationsfromMOOCs,lecturematerials,textbooks,and
onlineresources(Lietal.2019;Royetal.2019).Thesemeth-
Third, prerequisite relations are inherently defined
odsimprovescalabilitybylearningconceptrepresentations
over specific concept pairs rather than isolated concepts.
orconcept-pairfeaturesfromeducationalcontent.However,
Existing graph-based methods typically model concepts
they mainly rely on static content, course structures, or re-
independently, learning global node representations before
source dependencies, and thus provide limited modeling of
applying a generic scoring function (Zhang et al. 2025a).
prerequisiteevidenceemergingfromlearners’actuallearn-
Under this node-centric paradigm, the representation of c
i ingprocesses(Zhangetal.2025a).
remainsfixedacrossitspairingswithc andc .Ittherefore
j k
cannot adapt to the distinct relational context provided by Graph-based Concept Prerequisite Relation Learning.
each candidate concept. Prerequisite relation learning thus Recentstudiesincreasinglymodelprerequisiterelationlearn-
requires pair-conditioned relation reasoning that constructs ingasagraph-basedrelationpredictionproblem(Zhangetal.
dependencyevidencetailoredtoeachspecificconceptpair. 2022;Mazumder,Paik,andBasu2023).R-VGAEintroduces
To address these limitations, we propose ProPRL, a arelationalvariationalgraphautoencodertolearnprerequi-
property-awareframeworkforprerequisiterelationlearning. site chains without labeled concept pairs (Li et al. 2020).
ProPRL jointly exploits complementary structural and Heterogeneous graph models further incorporate concept-
behavioral evidence, adapts the contribution of these resourceorlearning-objectdependenciestoimproveconcept
evidencesourcestoeachcandidaterelation,anddiscourages representation learning (Mazumder, Paik, and Basu 2023).
mutually contradictory predictions in opposite directions. MHA-VGAE models interactions between resource graphs
Specifically, it integrates concept representations from andconceptgraphswithmulti-headattentionandvariational
concept-resource and learning-behavior views, employs a graph autoencoders (Zhang et al. 2022). More recent work
pair-conditionedgatetoassignrelation-specificimportance incorporates learning paths, global knowledge relations, or
to the two views, and incorporates an anti-symmetry reg- multi-view graph structures to capture richer dependency
ularizer into the training objective. Extensive experiments signals (Sun et al. 2024; Zhang et al. 2025a). LCPRE (Sun
on multiple educational datasets demonstrate that ProPRL etal.2024)useslearning-pathsupervisiontoextractprereq-
outperformsexistingbaselines. uisiterelationsfromeducationaldata,GKROM(Zhangetal.
2025b)optimizesmultipletypesofknowledgerelationsfor
Themaincontributionsofthisworkareasfollows:
prerequisiterelationlearning,andDGCPLconstructsbotha
concept-resourcehypergraphandalearnerbehaviorgraphto
• We introduceProPRL, aproperty-aware framework for
integrateknowledgeandbehaviorperspectives(Zhangetal.
prerequisiterelationlearningthatexplicitlycapturescom-
2025a). Nevertheless, most graph-based methods still learn
plementarymulti-viewevidence,pair-specificrelevance,
concept-levelrepresentationsandpredictcandidateedgesin-
anddirectionalirreversibility.
dependently,leavingorderedconcept-pairreasoninganddi-
rectionalirreversibilityinsufficientlyexplored.
• To the best of our knowledge, we are the first to intro-
ducedirection-preservingpersonalizedpropagationover
ProblemDefinition
directed learning-behavior graphs for prerequisite rela-
tionlearning. LetDdenoteaneducationaldatasetcomprisingaconceptset
C ={c ,c ,...,c },aresourcesetR={r ,r ,...,r },a
1 2 n 1 2 m
• WedevelopaPair-conditionedGatethatconstructsview- learnersetU,learnerinteractionsequencesS,andobserved
specific representations for each candidate ordered con- prerequisite labels Y. Specifically, S = {s | u ∈ U},
u
cept pair and adaptively weights and fuses the two evi- where s = (c ,c ,...,c ) denotes the interaction
u u,1 u,2 u,Tu
denceviewsaccordingtotheirpair-specificrelevance.We sequence of learner u, with c ∈ C representing the
u,t
further introduce an irreversibility-aware anti-symmetry conceptinvolvedinthet-thinteraction.Eachconceptc ∈C
i
regularizer that discourages simultaneously high confi- is associatedwith aninitial featurevector x ∈ Rd,and all
i
denceinbothdirectionsofthesameconceptpair. conceptfeaturesareorganizedasamatrixX∈Rn×d.

Figure2:OverviewoftheProPRLframework.ProPRLcomprisesfourstages.(a)Graphconstructionorganizesconcept–resource
associations and learner interactions into two complementary graph views. (b) Concept representation captures high-order
structuraldependenciesandmulti-hopbehavioralinformation.(c)Pair-conditionedfusiondynamicallyintegratesthetwoviews
to generate a pair-specific embedding for each candidate concept pair. (d) Constraint-aware optimization learns prerequisite
relationswhilesuppressingcontradictoryreversepredictions.
Foreachlabeledorderedconceptpair(c ,c ),wherei ̸= highpredictionsfor(c ,c )and(c ,c ),therebyencouraging
|     |     |     |     |     | i   | j   |     |     |     | i   | j   | j i |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
j, let y ij ∈ {0,1} denote its observed label. Specifically, directionalconsistencyinprerequisitepredictions.
| y = 1ifc | isaprerequisiteofc |     |     | ,andy | =   | 0otherwise. |     |     |     |     |     |     |     |     |
| -------- | ------------------ | --- | --- | ----- | --- | ----------- | --- | --- | --- | --- | --- | --- | --- | --- |
ij i j ij Multi-view Concept Representation. We first construct
ThecollectionofallobservedlabelsisdenotedbyY.Given
|                                                        |     |     |     |     |     |     |     | a directed | learning | behavior | graph | G from | learner | inter- |
| ------------------------------------------------------ | --- | --- | --- | --- | --- | --- | --- | ---------- | -------- | -------- | ----- | ------ | ------- | ------ |
| D,ourgoalistolearnaproperty-awareprerequisitepredictor |     |     |     |     |     |     |     |            |          |          |       | B      |         |        |
F suchthat: actionsequencesS tocapturethetransitionaldynamicsbe-
|     |     |     |              |     |      |     |     | tweenconcepts.Ifasequentialtransitionfromconceptc |     |            |      |                       |     | to  |
| --- | --- | --- | ------------ | --- | ---- | --- | --- | ------------------------------------------------- | --- | ---------- | ---- | --------------------- | --- | --- |
|     |     | F(c | i ,c j |D)=p |     | ij , |     | (1) |                                                   |     |            |      |                       |     | i   |
|     |     |     |              |     |      |     |     | c is observed,                                    |     | a directed | edge | c → c is established. |     | Let |
|     |     |     |              |     |      |     |     | j                                                 |     |            |      | i j                   |     |     |
wherep ij ∈[0,1]denotesthepredictedprobabilitythatc i is Bout ∈ Rn×n denotetheweightedoutgoingadjacencyma-
aprerequisiteofc . trix,whereBo utquantifiesthetransitionstrengthfromc to
|     |     | j   |     |     |     |     |     |                                                       | ij  |     |     |     |     | i   |
| --- | --- | --- | --- | --- | --- | --- | --- | ----------------------------------------------------- | --- | --- | --- | --- | --- | --- |
|     |     |     |     |     |     |     |     | c j .Conversely,theincomingadjacencymatrixisdefinedas |     |     |     |     |     |     |
Method
|            |         |     |                  |     |           |     |     | Bin = (Bout)⊤,explicitlycapturingthereversebehavioral |     |     |     |     |     |     |
| ---------- | ------- | --- | ---------------- | --- | --------- | --- | --- | ----------------------------------------------------- | --- | --- | --- | --- | --- | --- |
| We propose | ProPRL, |     | a Property-aware |     | framework |     | for | flow.                                                 |     |     |     |     |     |     |
Prerequisite Relation Learning. ProPRL is built around To mitigate numerical instability during graph propaga-
three principal components: Multi-view Concept Represen- tion, we incorporate self-loops prior to normalization. For
tation,Pair-conditionedGate,andIrreversibilityConstraint. each direction d ∈ {out,in}, we define B(cid:101)d = Bd +I and
Multi-view Concept Representation learns complementary itscorrespondingdiagonaldegreematrixDd,where
| concept | embeddings |     | from | a directed | learning-behavior |     |     |     |     |     |     |     |     |     |
| ------- | ---------- | --- | ---- | ---------- | ----------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
n
graph and a concept-resource hypergraph. The behavior (cid:88)
|     |     |     |     |     |     |     |     |     |     | Dd  | =   | B(cid:101) d . |     | (2) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | -------------- | --- | --- |
view employs direction-preserving personalized multi-hop ii ij
| propagation | to  | aggregate        | multi-hop |      | behavioral | evidence, |     |                |     |          | j=1       |          |              |     |
| ----------- | --- | ---------------- | --------- | ---- | ---------- | --------- | --- | -------------- | --- | -------- | --------- | -------- | ------------ | --- |
| whereas     | the | concept-resource |           | view | captures   | resource- |     |                |     |          |           |          |              |     |
|             |     |                  |           |      |            |           |     | The normalized |     | behavior | adjacency | matrices | are computed |     |
mediatedhigh-orderconceptassociations.Buildingonthese
as:
| representations, |     | Pair-conditioned |     | Gate | constructs |     | view- |     |     |     |                   |     |     |     |
| ---------------- | --- | ---------------- | --- | ---- | ---------- | --- | ----- | --- | --- | --- | ----------------- | --- | --- | --- |
|                  |     |                  |     |      |            |     |       |     |     | Ad  | =(Dd)−1B(cid:101) | d.  |     |     |
(3)
| specific | representations |     | for each | candidate | ordered |     | concept |     |     |     |     |     |     |     |
| -------- | --------------- | --- | -------- | --------- | ------- | --- | ------- | --- | --- | --- | --- | --- | --- | --- |
pairandlearnsapair-specificgatetoadaptivelyweightand Thus, Aout and Ain serve as the fundamental topologies
fuse evidence from the two views. This pair-conditioned foraggregatingforwardandbackwardtransitionalevidence,
| fusion allows | the | contribution |     | of each | view | to vary | across | respectively. |     |     |     |     |     |     |
| ------------- | --- | ------------ | --- | ------- | ---- | ------- | ------ | ------------- | --- | --- | --- | --- | --- | --- |
candidate pairs, rather than relying on a fixed node-level To encode localized structural contexts, we de-
fusion. Finally, Irreversibility Constraint introduces an ploy direction-specific graph convolutional networks
anti-symmetry regularizer that penalizes simultaneously (GCNs) (Kipf and Welling 2016a) equipped with shortcut

transformations.TheL-layermessagepassingisformulated StartingfromU(0) =X,theresource-awareencoderup-
as: datesconceptrepresentationsby:
(cid:16) (cid:17)
H(ℓ+1) =ϕ AdH(ℓ)W(ℓ) +H(ℓ)W(ℓ), (4) (cid:16) (cid:17)
d d g,d d 0,d U(ℓ+1) =ϕ PU(ℓ)W(ℓ) +U(ℓ)W(ℓ), (10)
h 0
H(0) =X, (5)
d
where U(ℓ) is the concept representation matrix at layer ℓ,
where W(ℓ) and W(ℓ) are trainable weight matrices, ϕ(·)
g,d 0,d W(ℓ)isthetrainableweightmatrixofthehypergraphaggre-
isanonlinearactivationfunction.AfterLlayers,theoutgo- h
ingandincomingbehavioralrepresentationsareextractedas gationbranchandW 0 (ℓ)isthetrainableweightmatrixofthe
Qout =H(L)andQin =H(L). shortcuttransformationbranch.
out in
Asprerequisiterelationshipsfrequentlymanifestaslatent Pair-conditioned Gate. Prerequisite completion is de-
multi-hop dependencies rather than strictly adjacent transi- finedoverorderedconceptpairsratherthanindividualcon-
tions, motivated by the success of APPNP (Gasteiger, Bo- cepts. Although the resource-aware representation u and
i
jchevski,andGünnemann2018)inglobaltopologicalexplo- the behavior-aware representation v encode concept-level
i
ration,wedeviseaspecializedpropagationschemetodistill evidence, they do not by themselves specify the role of a
long-range structural signals. The iterative propagation is conceptinacandidaterelation.Thesameconceptmayserve
definedas: asaprerequisiteinonepairbutasatargetconceptinanother
Zd,(t+1) =(1−α)AdZd,(t)+αQd, Zd,(0) =Qd, (6) pair. Therefore, ProPRL constructs pair-conditioned repre-
sentationstomodelthecandidaterelationfromc toc .
i j
wheret=0,1,...,k−1indexesthepropagationstep,and Fortheresource-awareview,wecomposetherepresenta-
α ∈ (0,1] acts as a teleport probability that gracefully bal- tionsofthesourceconceptc andthetargetconceptc as:
i j
anceshigher-orderneighborhoodexplorationwiththepreser-
ru =[u ;u ;u −u ;u ⊙u ], (11)
vationoflocalizedconceptsemantics.Afterksteps,thefully ij i j i j i j
propagated representations are denoted as Zout = Zout,(k)
where [·;·] denotes vector concatenation and ⊙ denotes
andZin =Zin,(k).
the Hadamard product. The first two terms preserve the
Finally,toholisticallyrepresenttheasymmetricinteraction role-specific information of the source and target concepts.
profile of each concept, we fuse the directional representa- The signed difference u − u introduces order-sensitive
i j
tions: evidence, since reversing the pair changes this term. The
V=LN (cid:0) ϕ (cid:0) ZoutW +ZinW (cid:1)(cid:1) , (7) producttermu i ⊙u j capturesdimension-wisecompatibility
out in
betweenthetwoconcepts.
where W and W are trainable projection matrices, Following a parallel logic, the behavior-aware pair
out in
andLN(·)denoteslayernormalization.Thisyieldsthefinal representationisdefinedas:
behavior-aware representation matrix V, with v denoting
i rv =[v ;v ;v −v ;v ⊙v ]. (12)
thebehavior-awarerepresentationforconceptc i . ij i j i j i j
Weconstructaconcept-resourcehypergraphandemploy
Thisrepresentationdescribesthecandidatepairfromtheper-
a HypergraphConvolutional Network (HGCN)(Feng etal.
spective of learner behavior, including both directional be-
2019) to capture high-order associations between concepts
havioraldiscrepancyandpairwisebehavioralcompatibility.
andlearningresources.LetM∈Rn×mdenotetheconcept-
The resource-aware and behavior-aware views may con-
resource incidence matrix, where M indicates whether
ij tributedifferentlytodifferentcandidatepairs.Forexample,
concept c is associated with resource r . Each resource is
i j some prerequisite relations can be supported mainly by
treatedasahyperedgeconnectingitsrelatedconcepts.
shared learning resources, whereas others may be more
BasedonM,wedefinetheconceptdegreematrixD ∈
c clearly reflected in sequential learning behavior. A fixed
Rn×n and the resource degree matrix D ∈ Rm×m. Their
r view-level fusion strategy would ignore such candidate-
diagonalentriesarecomputedas:
specific differences. To address this issue, ProPRL learns a
m n pair-conditionedgate:
(cid:88) (cid:88)
(D c ) ii = M ij ω j , (D r ) jj = M ij , (8) g =σ (cid:0) MLP (cid:0) [ru;rv ;|ru −rv |;ru ⊙rv ] (cid:1)(cid:1) , (13)
j=1 i=1 ij g ij ij ij ij ij ij
where ω j is the weight of resource hyperedge r j . In our where σ(·) denotes the sigmoid function and g ij has the
implementation,allresourcehyperedgesareassignedequal same dimension as ru and rv . The absolute difference
ij ij
weights, i.e., ω = 1. Let Ω = diag(ω ,ω ,...,ω ). The term measures the discrepancy between the two views,
j 1 2 m
normalized hypergraph propagation matrix is then defined whiletheHadamardproductcapturestheirdimension-wise
as: agreement.Thegatethereforedetermines,foreachcandidate
P=D − c 1 2MΩD− r 1M⊤D c − 2 1 . (9) p sh a o ir ul a d nd be eac ta h ke f n eat f u r r o e m di t m he ens r i e o s n o , ur h c o e w -aw m ar u e ch vi i e n w form or ati t o h n e
This normalization first propagates information from con-
behavior-awareview.
ceptstoresourcehyperedgesandthenbacktoconcepts,while
Thefinalpairrepresentationisobtainedbygatedfusion:
accountingforbothconceptdegreesandresourcehyperedge
sizes. r =g ⊙ru +(1−g )⊙rv . (14)
ij ij ij ij ij

Based on r , the prerequisite score and probability are Theclassificationlossisappliedtoallthreebranches:
ij
computedas:
1 (cid:88) (cid:88) (cid:104)
L =− y logpa
sp ij =MLP p (r ij ), pp ij =σ(sp ij ), (15) cls |T| ij ij
(i,j)∈T a∈{u,v,p}
w is h a e p re re p re p ij qu d i e s n it o e te o s f t c he . fused prerequisite probability that c i +(1−y ij )log(1−pa ij ) (cid:105) .
j
(21)
Irreversibility Constraint. Prerequisite relations are Toencouragethetwosingle-viewbranchestoagreewith
directional and generally irreversible. If concept c i is a thestrongerfusedpredictionwhileavoidingunstablemutual
prerequisiteofconceptc j ,thereverserelationfromc j toc i updates, ProPRL further adopts a teacher-detached multi-
shouldnotbeassignedahighprobabilityatthesametime. viewconsistencyloss.Thefusedbranchservesastheteacher,
However, when ordered pairs are optimized independently, anditslogitisstoppedfromgradientback-propagation:
a model may still produce contradictory bidirectional pre-
d in ic tr t o io d n u s c . es To an re o d rd u e c r e -s s e u n c s h iti s v t e ru ir c r t e u v r e a r l s i i n b c il o it n y si c s o te n n s c tr y a , in P t r . oPRL L con = |T 1 | (cid:88) (cid:16)(cid:12) (cid:12)σ(su ij /t)−σ(sg(sp ij )/t) (cid:12) (cid:12)
(i,j)∈T (22)
Foreachpositivetrainingpair(c ,c ),ProPRLaddition-
ally evaluates its reverse pair (c j ,c i i ) j using the same pair + (cid:12) (cid:12)σ(sv ij /t)−σ(sg(sp ij )/t) (cid:12) (cid:12) (cid:17) ,
scoring function. Let pp and pp denote the fused prereq-
ij ji
uisite probabilities of the forward and reverse directions, wheretisthetemperaturecoefficientandsg(·)denotesthe
respectively.Theirreversibilitylossisdefinedas: stop-gradientoperation.
The final objective combines classification supervision,
L = 1 (cid:88) max (cid:0) 0,pp +pp −µ (cid:1) , (16) multi-viewconsistency,andtheirreversibilityconstraint:
irr |T+| ij ji
(i,j)∈T+
L=L +βL +λL , (23)
cls con irr
whereT+ ={(i,j)∈T |y =1}denotesthesetofposi-
ij whereβ andλcontrolthestrengthsofconsistencylearning
tivetrainingpairs,andµisaco-activationmarginthatcon-
andirreversibilityregularization,respectively.
trolstheallowedupperboundofthetwoopposite-direction
During inference, ProPRL combines the three branch
probabilities.
probabilitiesbyaweightedsum:
Thisconstraintpenalizescasesinwhichbothdirectionsre-
ceivehighprobabilities.Therefore,itencouragesthemodel p =w pu +w pv +w pp, w +w +w =1. (24)
ij u ij v ij p ij u v p
topreservetheforwardprerequisiteevidencewhilesuppress-
ingthereverseprediction,leadingtomoredirectionallycon- Theweightsareselectedonthevalidationsetandthenfixed
sistentprerequisitecompletion. fortestevaluation.
OverallOptimization. ProPRLoptimizesthreeprediction
Experiments
branchesjointly:aresource-awarebranch,abehavior-aware
branch, and a pair-aware fused branch. The resource-aware Datasets. We evaluate ProPRL on three benchmark
and behavior-aware branches are supervised not only to datasets for prerequisite relation learning: MOOC1 (Liang
provide auxiliary predictions, but also to preserve view- et al. 2017), LectureBank2 (Li et al. 2019), and University
specific prerequisite evidence. For each view a ∈ {u,v}, Course3(UCD)(Liangetal.2017).
weuseaSiameserelationclassifiertoscoreanorderedpair.
Evaluation Metrics. We use accuracy (ACC), F1-score
Specifically, the two concepts in a pair are first mapped by
(F1), and area under the ROC curve (AUC) as the main
asharedview-specifictransformation:
evaluationmetrics,followingpreviousstudiesonprerequisite
x˜a =ρ (xa), x˜a =ρ (xa), (17) relationlearning(Zhangetal.2025a).Forallmetrics,higher
i a i j a j
valuesindicatebetterperformance.
where xu = u and xv = v . The same transformation
i i i i
ρ (·) is shared by the two sides of the ordered pair, BaselineMethods. WecompareProPRLwithtwogroups
a
formingaSiamesescoringstructure.Theview-specificpair ofbaselines:general-purposemethodsandtask-specificpre-
representationisthenconstructedas: requisite relation learning models. The first group includes
NB, SVM, RF, RefD (Liang et al. 2015), GAE (Kipf and
˜ra =[x˜a;x˜a;x˜a−x˜a;x˜a⊙x˜a], (18) Welling 2016b), and VGAE (Kipf and Welling 2016b).
ij i j i j i j
The second group includes HGAPNet (Mazumder, Paik,
andthecorrespondinglogitandprobabilityarecomputedby:
and Basu 2023), MHAVGAE (Zhang et al. 2022), Con-
Learn(Sun,Li,andZhang2022),LCPRE(Sunetal.2024),
sa =w⊤˜ra +b , pa =σ(sa), a∈{u,v}. (19)
ij a ij a ij ij andDGCPL(Zhangetal.2025a).
The fused branch uses the pair-conditioned representation
r definedintheprevioussubsectiontoproduce
1https://github.com/suderoy/PREREQ-IAAI-19
ij
2https://github.com/Yale-LILY/LectureBank
sp
ij
=MLP
p
(r
ij
), pp
ij
=σ(sp
ij
). (20) 3https://github.com/suderoy/PREREQ-IAAI-19

|     |     |     |     |     | UCD |     | LectureBank |     |     | MOOC |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | ----------- | --- | --- | ---- | --- | --- | --- | --- |
Method
|     |     |     |     | ACC | F1  | AUC ACC | F1  | AUC | ACC |     | F1  | AUC |     |     |
| --- | --- | --- | --- | --- | --- | ------- | --- | --- | --- | --- | --- | --- | --- | --- |
General-purposeMethods
NB 0.5396 0.5939 0.5039 0.5537 0.5781 0.5156 0.5423 0.5446 0.5511
SVM 0.4851 0.6090 0.4841 0.4545 0.4310 0.5068 0.5274 0.5662 0.5625
RF 0.6436 0.6364 0.7284 0.6777 0.6667 0.7820 0.7214 0.7053 0.8100
RefD 0.6386 0.6840 0.7668 0.5041 0.6629 0.6415 0.5821 0.6693 0.6861
GAE 0.6634 0.7094 0.7763 0.7438 0.7669 0.8563 0.7910 0.7692 0.8385
VGAE 0.6881 0.6834 0.7714 0.7686 0.7778 0.8525 0.7015 0.7368 0.8312
PrerequisiteLearningMethods
ConLearn 0.6275 0.7697 0.5931 0.4771 0.4571 0.6667 0.7961 0.8513 0.7963
MHAVGAE 0.6485 0.6844 0.7667 0.7190 0.7344 0.7978 0.7363 0.7135 0.8052
HGAPNet 0.8069 0.7914 0.8871 0.7934 0.7899 0.8757 0.8358 0.8325 0.9024
LCPRE 0.7723 0.7356 0.8655 0.7934 0.8062 0.8730 0.8308 0.8211 0.9000
DGCPL 0.8366 0.8374 0.8934 0.8099 0.8099 0.8699 0.8856 0.8832 0.9211
ProPRL(Ours) 0.8812 0.8788 0.9480 0.8264 0.8346 0.8929 0.9254 0.9231 0.9605
RelativeImprov. 5.33%↑ 4.94%↑ 6.11%↑ 2.04%↑ 3.05%↑ 1.96%↑ 4.49%↑ 4.52%↑ 4.28%↑
Table1:Overallperformancecomparisononthreebenchmarkdatasets.Thebestresultsarehighlightedinbold.
independentlyofaspecificdecisionthreshold.Notably,Pro-
| Variant |     | UCD |     | LectureBank | MOOC |     |     |     |     |     |     |     |     |     |
| ------- | --- | --- | --- | ----------- | ---- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
PRLimprovesAUCoverthestrongestbaselineonallthree
| w/oPairGate |     | 0.8528 |     | 0.8254 | 0.8763 |     |     |     |     |     |     |     |     |     |
| ----------- | --- | ------ | --- | ------ | ------ | --- | --- | --- | --- | --- | --- | --- | --- | --- |
datasets,withthelargestrelativegainof6.11%observedon
| w/oMulti-hopProp. |     | 0.7831 |     | 0.8000 | 0.8808 |     |     |     |     |     |     |     |     |     |
| ----------------- | --- | ------ | --- | ------ | ------ | --- | --- | --- | --- | --- | --- | --- | --- | --- |
UCD.Overall,therelativeimprovementsrangefrom1.96%
| w/oIrreversibility |     | 0.8670 |     | 0.7969 | 0.9109 |     |          |        |          |              |     |               |     |     |
| ------------------ | --- | ------ | --- | ------ | ------ | --- | -------- | ------ | -------- | ------------ | --- | ------------- | --- | --- |
|                    |     |        |     |        |        |     | to 6.11% | across | the nine | comparisons, |     | demonstrating |     | the |
ProPRL 0.8788 0.8346 0.9231 effectivenessandcross-datasetconsistencyofProPRL.
|     |     |     |     |     |     |     | AblationStudy. |     | Table2evaluatesthecontributionofthe |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | -------------- | --- | ----------------------------------- | --- | --- | --- | --- | --- |
Table2:AblationstudyofProPRLintermsofF1-score.
threeprincipalcomponentsofProPRL.Removinganycom-
|                |          |     |        |     |             |      | ponent    | consistently | reduces |      | the F1-score |     | across all  | three |
| -------------- | -------- | --- | ------ | --- | ----------- | ---- | --------- | ------------ | ------- | ---- | ------------ | --- | ----------- | ----- |
|                |          |     |        |     |             |      | datasets, | confirming   | that    | each | component    |     | contributes | pos-  |
| Implementation | Details. |     | ProPRL | is  | implemented | with |           |              |         |      |              |     |             |       |
itivelytothecompletemodel.Amongthem,multi-hopprop-
PyTorch.Thedatasetsaresplitintotraining,validation,and
|           |               |        |         |           |            |     | agation  | has the    | largest     | overall | impact: | its  | removal    | causes |
| --------- | ------------- | ------ | ------- | --------- | ---------- | --- | -------- | ---------- | ----------- | ------- | ------- | ---- | ---------- | ------ |
| test sets | at a ratio of | 8:1:1. | For all | datasets, | the number | of  |          |            |             |         |         |      |            |        |
|           |               |        |         |           |            |     | the most | pronounced | degradation |         | on      | UCD, | decreasing | the    |
trainingepochs,batchsize,learningrate,µ,t,βandseedare F1-score from 0.8788 to 0.7831. This result highlights the
fixedat50,16,1×10−4,0.8,0.5,1×10−5and42,respec-
|     |     |     |     |     |     |     | importance | of propagating |     | behavioral |     | evidence | beyond | im- |
| --- | --- | --- | --- | --- | --- | --- | ---------- | -------------- | --- | ---------- | --- | -------- | ------ | --- |
tively.Wesetαto0.05forLectureBankandMOOCandto
mediateneighborsforprerequisiterelationlearning.
| 0.2 for UCD. | Moreover, | λ   | is set | to 1×10−3 | for UCD | and |     |     |     |     |     |     |     |     |
| ------------ | --------- | --- | ------ | --------- | ------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
Theeffectsoftheothercomponentsvaryacrossdatasets.
| MOOC | and to 5×10−3 | for | LectureBank. |     | All experiments |     |          |     |            |      |          |     |         |        |
| ---- | ------------- | --- | ------------ | --- | --------------- | --- | -------- | --- | ---------- | ---- | -------- | --- | ------- | ------ |
|      |               |     |              |     |                 |     | Removing | the | pair-aware | gate | produces | the | largest | degra- |
areconductedusinganNVIDIAGeForceRTX3070TiGPU dation on MOOC, while removing anti-symmetry regular-
andanAMDRyzen5800xCPU. ization affects LectureBank most strongly. These dataset-
|             |             |     |       |            |     |         | dependent | patterns | indicate |     | that relation-specific |     | evidence |     |
| ----------- | ----------- | --- | ----- | ---------- | --- | ------- | --------- | -------- | -------- | --- | ---------------------- | --- | -------- | --- |
| Performance | Comparison. |     | Table | 1 presents | the | overall |           |          |          |     |                        |     |          |     |
fusionanddirectionalconstraintsaddressdistinctaspectsof
| performance | comparison |     | on the | three benchmark |     | datasets. |     |     |     |     |     |     |     |     |
| ----------- | ---------- | --- | ------ | --------------- | --- | --------- | --- | --- | --- | --- | --- | --- | --- | --- |
prerequisiterelationlearning.Takentogether,theconsistent
ThemostnotableobservationistheconsistencyofProPRL,
degradationofallablatedvariantsvalidatesthenecessityof
whichranksfirstacrossallninedataset–metriccombinations,
thethreecomponentsinthecompleteProPRLframework.
althoughtheidentityofthestrongestbaselinevariesacross
datasetsandmetrics. CaseStudy. Toexaminewhetherthemodelsdistinguisha
Specifically,DGCPLconstitutesthestrongestbaselinein prerequisiterelationfromitsreversedcounterpart,weeval-
eightoftheninecomparisons,whereasHGAPNetachieves uated each positive MOOC test relation in both orders. As
the highest baseline AUC on LectureBank. ProPRL nev- showninFigure3,bothmodelsplacemostrelationsbelow
ertheless outperforms the strongest baseline in every com- thediagonal,indicatingthattheygenerallyassignhighercon-
parison, demonstrating a consistent performance advantage fidencetotheannotatedprerequisitedirection.ProPRL,how-
across different evaluation settings. The improvements are ever,producesaclearerconcentrationtowardthelower-right
observed jointly in ACC and F1, which characterize over- region, where the annotated direction receives high confi-
allclassificationaccuracyandthebalancebetweenprecision dencewhilethereverseddirectionisstronglysuppressed.
andrecall,aswellasinAUC,whichevaluatesrankingquality Quantitatively, ProPRL increases the proportion of cor-

|     |     |     |     |     |     |     | Data | Method |     | Params | Train  | Infer. | Mem.  |
| --- | --- | --- | --- | --- | --- | --- | ---- | ------ | --- | ------ | ------ | ------ | ----- |
|     |     |     |     |     |     |     |      |        |     | (M)    | (s)    | (s)    | (MB)  |
|     |     |     |     |     |     |     |      | DGCPL  |     | 1.89   | 122.44 | 0.0707 | 28.50 |
MOOC
|     |     |     |     |     |     |     |     | ProPRL |     | 2.68 | 211.59 | 0.0316 | 37.35 |
| --- | --- | --- | --- | --- | --- | --- | --- | ------ | --- | ---- | ------ | ------ | ----- |
|     |     |     |     |     |     |     |     | DGCPL  |     | 1.89 | 73.69  | 0.0427 | 26.48 |
LectureBank
|     |     |     |     |     |     |     |     | ProPRL |     | 2.68 | 96.95  | 0.1754 | 34.11 |
| --- | --- | --- | --- | --- | --- | --- | --- | ------ | --- | ---- | ------ | ------ | ----- |
|     |     |     |     |     |     |     |     | DGCPL  |     | 1.89 | 127.39 | 0.0735 | 28.73 |
UCD
|     |     |     |     |     |     |     |     | ProPRL |     | 2.68 | 212.01 | 0.0351 | 37.82 |
| --- | --- | --- | --- | --- | --- | --- | --- | ------ | --- | ---- | ------ | ------ | ----- |
Figure3:TheleftpanelshowstheresultsofDGCPL,while Table3:Efficiencycomparison.
| the right | panel shows | the | results | of ProPRL. | Each | point |     |     |     |     |     |     |     |
| --------- | ----------- | --- | ------- | ---------- | ---- | ----- | --- | --- | --- | --- | --- | --- | --- |
denotesapositivetestrelation,withtheannotated-direction
confidenceS andreversed-directionconfidenceS . iscomparativelyinsensitivetoλ overtheevaluatedrange:
|     | ij  |     |     |     |     | ji  |     |     |     | asy |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
nonzeroregularizationusuallyimprovesormaintainsperfor-
mance,buttheoptimalstrengthvariesacrossdatasets.This
|     |     |     |     |     |     |     | shows that | directional | regularization |     | is  | beneficial | without |
| --- | --- | --- | --- | --- | --- | --- | ---------- | ----------- | -------------- | --- | --- | ---------- | ------- |
requiringanarrowlytunedcoefficient.
|     |     |     |     |     |     |     | In contrast, | the learning |     | rate has | a substantially |     | stronger |
| --- | --- | --- | --- | --- | --- | --- | ------------ | ------------ | --- | -------- | --------------- | --- | -------- |
effectonmodelperformance.Thebestoverallperformanceis
obtainedaround10−4.Takentogether,theseresultsindicate
thatProPRLisreasonablystablewithrespecttoitsstructural
hyperparametersbutrequiresanappropriatelysmalllearning
rateforreliableoptimization.
|     |     |     |     |     |     |     | Efficiency | Study. | Table | 3 reports | the | computational | ef- |
| --- | --- | --- | --- | --- | --- | --- | ---------- | ------ | ----- | --------- | --- | ------------- | --- |
ficiencyofProPRLandDGCPLontheoriginaldatasplits.
ComparedwithDGCPL,ProPRLincursamoderateincrease
inmodelsizeandtrainingtimebecauseitlearnscomplemen-
taryrepresentationsfromtheconcept-resourceandlearning-
behaviorviewsandperformspair-conditionedgatedfusion.
|     |     |     |     |     |     |     | The direction-preserving |     |     | personalized | propagation |     | and the |
| --- | --- | --- | --- | --- | --- | --- | ------------------------ | --- | --- | ------------ | ----------- | --- | ------- |
irreversibilityconstraintfurtherintroduceadditionaltraining
Figure4:HyperparameterStudy.
overhead.Nevertheless,ProPRLremainslightweight,using
lessthan40MBofGPUmemoryonalldatasetsandrequir-
rectly ordered relations from 88.0% to 90.0% and enlarges inglessthan0.18secondsfortest-timeinference.ProPRLis
fasterthanDGCPLonMOOCandUCD,althoughitrequires
| the mean   | forward-reverse |           | confidence | margin    | from        | 0.605 to |                |        |                 |          |              |       |          |
| ---------- | --------------- | --------- | ---------- | --------- | ----------- | -------- | -------------- | ------ | --------------- | -------- | ------------ | ----- | -------- |
|            |                 |           |            |           |             |          | more inference | time   | on LectureBank. |          | Overall,     | these | results  |
| 0.695. The | wider           | margin    | results    | from both | a higher    | mean     |                |        |                 |          |              |       |          |
|            |                 |           |            |           |             |          | show that      | ProPRL | achieves        | improved | prerequisite |       | relation |
| confidence | for the         | annotated |            | direction | and a lower | mean     |                |        |                 |          |              |       |          |
modelingwithacceptablecomputationaloverhead.
confidenceforitsreversal.Therefore,themainimprovement
| is not merely | the | correction | of  | a small number | of  | reversed |     |     |     |     |     |     |     |
| ------------- | --- | ---------- | --- | -------------- | --- | -------- | --- | --- | --- | --- | --- | --- | --- |
Conclusion
rankings,butastrongerseparationbetweenthetwopossible
directionsacrossthetestrelations. Inthispaper,wepresentedProPRL,aproperty-awareframe-
workforprerequisiterelationlearningineducationalknowl-
| Hyperparameter |     | Study. | Figure | 4 investigates |     | the sensi- |     |     |     |     |     |     |     |
| -------------- | --- | ------ | ------ | -------------- | --- | ---------- | --- | --- | --- | --- | --- | --- | --- |
edgegraphs.ProPRLlearnscomplementaryconceptrepre-
tivityofProPRLtothepropagationcoefficientα,propagation
depthk,anti-symmetryweightλ sentationsfromaconcept-resourcehypergraphandadirected
asy ,andlearningrate.The
learning-behaviorgraph,employsaPair-conditionedGateto
effectofαisdataset-dependent,althoughProPRLmaintains
|            |             |             |     |        |            |        | adaptively | fuse evidence    |     | for each         | candidate | ordered     | con- |
| ---------- | ----------- | ----------- | --- | ------ | ---------- | ------ | ---------- | ---------------- | --- | ---------------- | --------- | ----------- | ---- |
| relatively | competitive | performance |     | across | the tested | range. |            |                  |     |                  |           |             |      |
|            |             |             |     |        |            |        | cept pair, | and incorporates |     | an anti-symmetry |           | regularizer | to   |
MOOCfavorsasmallerα,whereasUCDperformsbestata
discouragesimultaneouslyhighconfidenceinreversedirec-
| moderate | value, indicating |     | that | the appropriate | balance | be- |     |     |     |     |     |     |     |
| -------- | ----------------- | --- | ---- | --------------- | ------- | --- | --- | --- | --- | --- | --- | --- | --- |
tweenpropagatedinformationandtheinitialrepresentation tions.Experimentsonthreebenchmarkdatasetsshowedthat
ProPRLconsistentlyoutperformedrepresentativebaselines,
dependsontheunderlyinggraphstructure.
whileablationstudiesfurthersupportedtheeffectivenessof
| Increasing | k from | zero | generally | improves | performance, |     |     |     |     |     |     |     |     |
| ---------- | ------ | ---- | --------- | -------- | ------------ | --- | --- | --- | --- | --- | --- | --- | --- |
itsprincipalcomponents.
| with particularly | pronounced |     | gains | on UCD. | The | improve- |     |     |     |     |     |     |     |
| ----------------- | ---------- | --- | ----- | ------- | --- | -------- | --- | --- | --- | --- | --- | --- | --- |
mentsbecomelimitedoncekreachesapproximately5,sug-
References
gestingthatamoderatepropagationdepthcapturesmostof
the useful multi-hop behavioral dependencies, while fur- Abdelrahman,G.;Wang,Q.;andNunes,B.2023.Knowledge
ther propagation provides little additional benefit. ProPRL tracing:Asurvey. ACMComputingSurveys,55(11):1–37.

Alzetta,C.;Koceva,F.;Passalacqua,S.;Torre,I.;andAdorni, Roy,S.;Madhyastha,M.;Lawrence,S.;andRajan,V.2019.
G.2018.PRET:Prerequisite-EnrichedTerminology.ACase Inferring concept prerequisite relations from online educa-
Study on Educational Texts. In Proceedings of the Fifth tional resources. In Proceedings of the 33rd AAAI con-
Italian Conference on Computational Linguistics (CLiC-it ference on artificial intelligence (AAAI 2019), volume 33,
| 2018),15–21. |     |     |     |     |     |     |     | 9589–9594. |     |     |     |     |     |     |
| ------------ | --- | --- | --- | --- | --- | --- | --- | ---------- | --- | --- | --- | --- | --- | --- |
Cheng, X.; Zhang, Z.; Wang, J.; Fang, L.; He, C.; Guan, Sun,H.;Li,Y.;andZhang,Y.2022. Conlearn:Contextual-
Q.; Pan, S.; and Luo, W. 2026. GraphRAG-induced dual knowledge-awareconceptprerequisiterelationlearningwith
knowledge structure graphs for personalized learning path graph neural network. In Proceedings of the 2022 SIAM
recommendation. In Proceedings of the 40th AAAI Con- InternationalConferenceonDataMining(SDM2022),118–
126.
| ference on | Artificial | Intelligence |     | (AAAI | 2026), | volume | 40, |     |     |     |     |     |     |     |
| ---------- | ---------- | ------------ | --- | ----- | ------ | ------ | --- | --- | --- | --- | --- | --- | --- | --- |
14610–14620. Sun,J.;He,Y.;Xu,Y.;Sun,J.;andSun,G.2024.Alearning-
|            |       |     |           |     |           |     |          | path based | supervised | method | for | concept | prerequisite | re- |
| ---------- | ----- | --- | --------- | --- | --------- | --- | -------- | ---------- | ---------- | ------ | --- | ------- | ------------ | --- |
| Cheng, X.; | Zhou, | X.; | Fang, L.; | He, | C.; Zhou, | Y.; | Luo, W.; |            |            |        |     |         |              |     |
Gong,Z.;andGuan,Q.2025. NR4DER:Neuralre-ranking lations extraction in educational data. In Proceedings of
for diversified exercise recommendation. In Proceedings the33rdACMInternationalConferenceonInformationand
of the 48th International ACM SIGIR Conference on Re- KnowledgeManagement(CIKM2024),2168–2177.
| search and | Development |     | in  | Information | Retrieval |     | (SIGIR- |           |         |        |          |              |     |         |
| ---------- | ----------- | --- | --- | ----------- | --------- | --- | ------- | --------- | ------- | ------ | -------- | ------------ | --- | ------- |
|            |             |     |     |             |           |     |         | Talukdar, | P.; and | Cohen, | W. 2012. | Crowdsourced |     | compre- |
2025),1738––1747.
|     |     |     |     |     |     |     |     | hension: | predicting | prerequisite |     | structure | in wikipedia. | In  |
| --- | --- | --- | --- | --- | --- | --- | --- | -------- | ---------- | ------------ | --- | --------- | ------------- | --- |
Feng,Y.;You,H.;Zhang,Z.;Ji,R.;andGao,Y.2019. Hy- Proceedings of the Seventh Workshop on Building Educa-
pergraphneuralnetworks. InProceedingsofthe33rdAAAI tionalApplicationsUsingNLP,307–315.
conferenceonartificialintelligence(AAAI2019),volume33, Xiao,K.;Bai,Y.;andZhang,Y.2022.Extractingprecedence
3558–3565. relationsbetweenvideolecturesinmoocs.InProceedingsof
the2022InternationalConferenceonMultimediaRetrieval,
Gasteiger,J.;Bojchevski,A.;andGünnemann,S.2018.Pre-
608–614.
| dict then | propagate: | Graph | neural | networks |     | meet | personal- |     |     |     |     |     |     |     |
| --------- | ---------- | ----- | ------ | -------- | --- | ---- | --------- | --- | --- | --- | --- | --- | --- | --- |
izedpagerank. arXivpreprintarXiv:1810.05997. Yang, B.; Gharebhaygloo, M.; Rondi, H. R.; Hortis, E.;
|               |     |       |     |       |         |     |          | Lostalo,E.Z.;Huang,X.;andErcal,G.2024. |     |     |     |     |     | Comparative |
| ------------- | --- | ----- | --- | ----- | ------- | --- | -------- | -------------------------------------- | --- | --- | --- | --- | --- | ----------- |
| Hu, C.; Xiao, | K.; | Wang, | Z.; | Wang, | S.; and | Li, | Q. 2021. |                                        |     |     |     |     |     |             |
Extractingprerequisiterelationsamongwikipediaconcepts analysisofcourseprerequisitenetworksforfiveMidwestern
using the clickstream data. In International Conference on publicinstitutions. AppliedNetworkScience,9(1):25.
KnowledgeScience,EngineeringandManagement,13–26. Zhang,J.;Lin,N.;Zhang,X.;Song,W.;Yang,X.;andPeng,
Kipf,T.N.;andWelling,M.2016a. Semi-supervisedclas- Z.2022. Learningconceptprerequisiterelationsfromedu-
sificationwithgraphconvolutionalnetworks. arXivpreprint cationaldataviamulti-headattentionvariationalgraphauto-
arXiv:1609.02907. encoders. In Proceedings of the 15th ACM International
ConferenceonWebSearchandDataMining(WSDM2022),
| Kipf,T.N.;andWelling,M.2016b. |     |     |     |     | Variationalgraphauto- |     |     |     |     |     |     |     |     |     |
| ----------------------------- | --- | --- | --- | --- | --------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
1377–1385.
| encoders.       | arXivpreprintarXiv:1611.07308. |     |           |     |     |        |          |            |       |          |           |     |         |            |
| --------------- | ------------------------------ | --- | --------- | --- | --- | ------ | -------- | ---------- | ----- | -------- | --------- | --- | ------- | ---------- |
|                 |                                |     |           |     |     |        |          | Zhang, M.; | Wang, | J.; Han, | J.; Xiao, | K.; | Li, Z.; | Zhang, Y.; |
| Li, I.; Fabbri, | A.                             | R.; | Hingmire, | S.; | and | Radev, | D. 2020. |            |       |          |           |     |         |            |
Chen,H.;andWang,S.2025a.DGCPL:DualGraphDistilla-
R-VGAE:relational-variationalgraphautoencoderforunsu-
tionforConceptPrerequisiteRelationLearning.InProceed-
| pervised | prerequisite | chain | learning. |     | In Proceedings |     | of the |     |     |     |     |     |     |     |
| -------- | ------------ | ----- | --------- | --- | -------------- | --- | ------ | --- | --- | --- | --- | --- | --- | --- |
ingsofthe34thInternationalJointConferenceonArtificial
| 28th International |     | Conference |     | on Computational |     |     | Linguis- |     |     |     |     |     |     |     |
| ------------------ | --- | ---------- | --- | ---------------- | --- | --- | -------- | --- | --- | --- | --- | --- | --- | --- |
Intelligence(IJCAI2025),8366–8374.
tics,1147–1157.
Zhang,M.;Wang,J.;Xiao,K.;Wang,S.;Zhang,Y.;Chen,
| Li, I.; Fabbri, | A.               | R.; Tung, | R.          | R.; and   | Radev,      | D.             | R. 2019. |                                         |     |                                     |     |     |               |     |
| --------------- | ---------------- | --------- | ----------- | --------- | ----------- | -------------- | -------- | --------------------------------------- | --- | ----------------------------------- | --- | --- | ------------- | --- |
|                 |                  |           |             |           |             |                |          | H.;andLi,Z.2025b.                       |     | Learningconceptprerequisiterelation |     |     |               |     |
| What should     | i learn          | first:    | Introducing |           | lecturebank |                | for nlp  |                                         |     |                                     |     |     |               |     |
|                 |                  |           |             |           |             |                |          | viaglobalknowledgerelationoptimization. |     |                                     |     |     | InProceedings |     |
| education       | and prerequisite |           | chain       | learning. |             | In Proceedings |          |                                         |     |                                     |     |     |               |     |
ofthe39thAAAIConferenceonArtificialIntelligence(AAAI
ofthe33rdAAAIconferenceonartificialintelligence(AAAI
2025),volume39,1638–1646.
2019),volume33,6674–6681.
Liang,C.;Wu,Z.;Huang,W.;andGiles,C.L.2015.Measur-
| ing prerequisite |     | relations | among | concepts. |     | In Proceedings |     |     |     |     |     |     |     |     |
| ---------------- | --- | --------- | ----- | --------- | --- | -------------- | --- | --- | --- | --- | --- | --- | --- | --- |
ofthe2015conferenceonempiricalmethodsinnaturallan-
guageprocessing(EMNLP2015),1668–1674.
| Liang, C.;          | Ye, J.; | Wu,                            | Z.; Pursel, | B.;       | and | Giles, | C. 2017.   |     |     |     |     |     |     |     |
| ------------------- | ------- | ------------------------------ | ----------- | --------- | --- | ------ | ---------- | --- | --- | --- | --- | --- | --- | --- |
| Recovering          | concept | prerequisite                   |             | relations |     | from   | university |     |     |     |     |     |     |     |
| coursedependencies. |         | InProceedingsofthe31stAAAICon- |             |           |     |        |            |     |     |     |     |     |     |     |
ferenceonArtificialIntelligence,volume31.
Mazumder,D.;Paik,J.H.;andBasu,A.2023.Agraphneural
| network model  |     | for concept | prerequisite |               | relation |            | extraction. |     |     |     |     |     |     |     |
| -------------- | --- | ----------- | ------------ | ------------- | -------- | ---------- | ----------- | --- | --- | --- | --- | --- | --- | --- |
| In Proceedings |     | of the      | 32nd ACM     | International |          | Conference |             |     |     |     |     |     |     |     |
onInformationandKnowledgeManagement(CIKM2023),
1787–1796.