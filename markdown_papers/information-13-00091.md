---
title: "information-13-00091"
source: "information-13-00091.pdf"
source_sha256: "268e4b28885244dc7e435051724965d55963c515660130260a2bf26de9a33111"
converted_at: "2026-10-26T07:05:09.114318+00:00"
markitdown_version: "0.1.9"
---
informatio n
Article
MEduKG: A Deep-Learning-Based Approach for Multi-Modal
Educational Knowledge Graph Construction
NanLi1 ,QiangShen1,RuiSong2,YangChi2andHaoXu1,2,*
1 CollegeofComputerScienceandTechnology,JilinUniversity,Changchun130012,China;
linan19@mails.jlu.edu.cn(N.L.);shenqiang19@mails.jlu.edu.cn(Q.S.)
2 SchoolofArtificialIntelligence,JilinUniversity,Changchun130012,China;songrui20@mails.jlu.edu.cn(R.S.);
yangchi19@mails.jlu.edu.cn(Y.C.)
* Correspondence:xuhao@jlu.edu.cn
Abstract:Thepopularityofinformationtechnologyhasgivenrisetoagrowinginterestinsmartedu-
cationandhasprovidedthepossibilityofcombiningonlineandofflineeducation.Knowledgegraphs,
aneffectivetechnologyforknowledgerepresentationandmanagement,havebeensuccessfullyuti-
lizedtomanagemassiveeducationalresources. However, theexistingresearchonconstructing
educationalknowledgegraphsignoresmultiplemodalitiesandtheirrelationships,suchasteacher
speechesandtheirrelationshipwithknowledge.Totacklethisproblem,weproposeanautomatic
approachtoconstructmulti-modaleducationalknowledgegraphsthatintegratespeechasamodal
resourcetofacilitatethereuseofeducationalresources. Specifically,wefirstproposeafine-tuned
BidirectionalEncoderRepresentationfromTransformers(BERT)modelbasedoneducationlexicon,
calledEduBERT,whichcanadaptivelycaptureeffectiveinformationintheeducationfield.Wealso
addaBidirectionalLongShort-TermMemory-ConditionalRandomField(BiLSTM-CRF)toeffectively
identifyeducationalentities.Then,thelocationalinformationoftheentityisincorporatedintoBERT
toextracttheeducationalrelationship. Inaddition,tocovertheshortageoftraditionaltext-based
(cid:1)(cid:2)(cid:3)(cid:1)(cid:4)(cid:5)(cid:6)(cid:7)(cid:8)(cid:1)
(cid:1)(cid:2)(cid:3)(cid:4)(cid:5)(cid:6)(cid:7) knowledgegraphs,wefocusoncollectingteacherspeechtoconstructamulti-modalknowledge
Citation:Li,N.;Shen,Q.;Song,R.; graph.Weproposeaspeech-fusionmethodthatlinksthesedataintothegraphasaclassofentities.
Chi,Y.;Xu,H.MEduKG:A Thenumericresultsshowthatourproposedapproachcanmanageandpresentvariousmodesof
Deep-Learning-BasedApproachfor educationalresourcesandthatitcanprovidebettereducationservices.
Multi-ModalEducationalKnowledge
GraphConstruction.Information2022, Keywords:educationalknowledgegraph;multi-modaldata;conceptrecognition;relationextraction;
13,91. https://doi.org/10.3390/ teachingspeechfusion
info13020091
AcademicEditor:PaulBuitelaar
Received:16December2021 1. Introduction
Accepted:11February2022
Withthedevelopmentofartificialintelligenceandpeople’sincreasingemphasison
Published:15February2022
education, smart education has been drawing more attention in recent decades [1]. In
Publisher’sNote:MDPIstaysneutral recent years, various novel teaching manners have been utilized in college classrooms
withregardtojurisdictionalclaimsin thatleveragemultimediatechniques,includingtextbooks,courseware,video,andvoice,
publishedmapsandinstitutionalaffil- amongotherforms,ratherthantraditionalmethodssuchasblackboardwriting. Inthese
iations.
innovated educational methodologies, text is no longer the main form of knowledge
dissemination, and multi-modal data such as pictures and audio are more conducive
to students’ understanding of knowledge [2–4]. Therefore, we need more intelligent
methods/systems,throughwhichtostore,manage,andapplythesemulti-modaldata.
Copyright: © 2022 by the authors.
Knowledgegraphsserveasanimportantmethod,throughwhichdatacanbeorga-
Licensee MDPI, Basel, Switzerland.
nizedandmanagedthatinterlinksheterogeneousdatafromdifferentdomains[5]. Inthe
This article is an open access article
education field, knowledge graphs are often used for teaching and learning in schools.
distributed under the terms and
However,theseknowledgegraphsarefrequentlyconstructedmanually,consumingalot
conditionsoftheCreativeCommons
Attribution(CCBY)license(https:// ofresources,andtheycannotbeextendedtootherentitiesandrelationships. Researchers
creativecommons.org/licenses/by/ havebeguntofocusontheautomaticconstructionofeducationalknowledgegraphs. Re-
4.0/). centresearch[6–8]usedknowledgegraphsforontologyconstructionandachievedsome
Information2022,13,91.https://doi.org/10.3390/info13020091 https://www.mdpi.com/journal/information

Information2022,13,91 2of18
success. Liuetal. predictedthepotentialrelationshipbetweentheconceptandthecourse
bymappinganonlinecoursetothegeneralspaceoftheconcept[9]. Chenetal. proposeda
systemtoconstructeducationalknowledgegraphsforstudents[10].
Ingeneral,mostofthepreviousresearchdatacomefromonlineeducationresources
thatarenotintegratedwithrealclassrooms. Traditionaleducationalknowledgegraphs
onlyutilizetextastheonlyorganizationalform,whichismonotonousandincompletefor
thepresentationofconceptsorentityinformation.Comparedtotext,theuseofpictures,the
teacher’svoice,andothermodesofinformationmakeiteasierforstudentstobeinterested
inandunderstandtheinformationbeinggiventotheminclass. Therefore,theconstruction
ofmulti-modaleducationknowledgegraphsisparticularlynecessaryandmeaningful.
To tackle the challenges above, we propose a method that is able to automatically
constructknowledgegraphsthatintegratemulti-modalteachingresources,suchasteacher
speech. Takingadatastructurecourseasanexample,weusedourmethodtorealizetheau-
tomaticintegrationofmulti-modaleducationalresources. Toimprovetheprofessionalism
anddomainoftheeducationalknowledgegraph,weproposeanewmodelforeducational
entityrecognitioncalledEduBERT-BiLSTM-CRF.First,webuildaneducationallexicon
andfeedthisintothefine-tunedBERT,whichallowstheBERTmodeltoadaptivelylearn
specificknowledgefromtheeducationfield. Then,weuseBiLSTMtoextractthecontextual
featuresofeachwordintheinputsentences. ACRFlayerisaddedtoobtaintheoptimal
predictionsequenceneededtocompleteeducationconceptrecognition. Inaddition,we
usethelocationinformationoftheentitytoconstructmoreaccuratesemanticrelationships
fortheseeducationalconcepts. Finally,asentitiesinthegraphoccurinspeechdata,we
convertclassroomspeechintotextthroughspeechrecognitiontechnologyandlinkitto
theknowledgegraphasanentity. Wealsoconductextensiveexperiments,andtheresults
showtheeffectivenessofourmethod. Insummary,themaincontributionsofthisresearch
areasfollows:
1. Weproposeamodeltoautomaticallyconstructamulti-modaleducationalknowl-
edgegraph,andweprovideawayforspeechfusiontoincorporateandrefinethe
knowledgegraphbytreatingspeechasanentity;
2. We propose a lexicon-based BERT model for educational concept recognition by
combiningtheBiLSTM-CRFmodelthatcanbetteridentifyeducationalconcepts. For
relationextraction,inordertobettercombinethedomaininformation,wecombine
thelocationinformationoftheentitywithBERTtodigouttheimplicitrelationships
betweentheseentities;
3. Wetakecomputercoursesasanexampletoverifythescalabilityandfeasibilityofour
work. Inaddition,theempiricalresultsshowthatourproposedapproachperforms
competitively better than the state-of-the-art models in entity recognition and in
relationextraction.
Therestofthispaperisorganizedasfollows: Section2introducesrelatedworkon
knowledgegraph. Section3brieflyshowsthedetails,whichdescribeshowthemulti-nodal
knowledgegraphwasbuilt. Section4presentstheexperimentalresults. Wesummarize
thisresearchanddiscusstheprospectsforfutureresearchinSection5.
2. RelatedWork
Thissectionintroducesrecentresearchonknowledgegraphsandbrieflydescribes
namedentityrecognitionandrelationextractiontechnologies.
2.1. EducationalKnowledgeGraphConstruction
In essence, a knowledge graph is a semantic network and a graphic set of related
knowledgethatgenerallyreferstoalarge-scaleknowledgebase. Atpresent,knowledge
graphs are generally divided into general domain knowledge graphs and vertical do-
mainknowledgegraphs. Examplesofclassicgeneraldomainknowledgegraphsinclude
YAGO [11], DBpedia [12], Wikidata [13], etc. These general domain graphs have great
advantagesinsemanticsearch,questionansweringsystemsandotherscenarios,however

Information2022,13,91 3of18
theyalsohavedisadvantages. Theycannotsupporttheorganizationandmanagement
of entities in specific fields well, as they require deep domain knowledge. Vertical do-
mainknowledgegraphsplayanimportantroleinthisrespect,howeververticaldomain
knowledge graphs are often manually constructed, requiring a lot of time and human
resources[14].
Recently,knowledgegraphtechnologyhasplayedanimportantroleintheeducation
field [15]. Yang et al. used the correlation between specific courses to establish a di-
recteduniversalconceptgraphandtoexploretheimpliedcorrelationbetweencourses[16].
Senthilkumarintroducedaconceptmapconstructedbysoftwareintoteachingandlearn-
ing[17]. Liangetal. exploredtheprerequisiterelationshipsofconceptsbyminingdepen-
denciesbetweencourses[18]. Thesestudieshaveprovedthatitisveryimportanttodigout
educationalconceptsandrelationships. Manyresearchershavebeguntotrytoconstruct
knowledgegraphsbyintegratingalargeamountofeducationaldata. Suetal. constructed
asubjectknowledgegraphthatevaluatesthestrengthofthesemanticassociationsbetween
knowledge points [15]. Sun et al. used sub-string matching for entity recognition and
theclusteringmethodforsemanticrelationextractiontobuildavisualanalysisplatform
calledEduVis[19]. Zhengetal. constructedacurriculumknowledgegraphbyusingVector
SpaceModel(VSM)andrulesprocessingtolearneasily[20]. Dangetal. usedWikipedia
forentityextractionandconstructedanMOOCknowledgegraph[21]Yaoetal. proposed
anovelmodelforembeddingthelearningofeducationalknowledgegraphstopromote
knowledgegraphconstruction[22].
These studies have proved the urgency for the construction of knowledge graphs
intheeducationfield. However,existingworkshaveonlyusededucationaldatafroma
singlemode,suchascourseoutlinesandothertextresources. Theyignoreothermodal
educational data from offline real classrooms, such as teacher audio, meaning that it is
possible that these knowledge graphs lack integral information. In addition, previous
studiesdidnotfullyrealizeautomaticknowledgegraphconstruction. Theyrequireda
lotofmanualannotationsandtemplates. Therefore,thegoalofthepresentresearchisto
designamulti-modaleducationalknowledgegraphmodelthatautomaticallycombines
onlineandofflinerealresources,whichcaneffectivelyservesmarteducation.
2.2. NamedEntityRecognition
Namedentityrecognition(NER),akeystepintheconstructionofknowledgegraphs,
aims to extract entities from structured or unstructured data according to predefined
tags[23]. Researchonentityrecognitionintheverticaldomainhasbeendrawingmore
attentioninrecentdecades.
Previously published work on named entity recognition is mainly divided into
rule-based and dictionary-based methods, machine learning-based methods, and neu-
ralnetwork-basedmethods[24]. Therule-basedanddictionary-basedapproachwasfirst
appliedtoNER,whichinvolvesrulesbeingmanuallywritteninordertoidentifyentities
bymatchingtexttorules[25]. Manualwritingrequiresalotoftime,lowaccuracy,andpoor
portability.Machinelearningmodelscansolvetheaboveproblemswell.Commonmachine
learningmodelsincludeHiddenMarkovModel(HMM)[26],MaximumSupportVector
Machine(SVM)[27],ConditionalRandomField(CRF)[28],etc. Thesemethodsrequire
manual feature extraction. Model training requires a large number of manual labeling
samples,andtheresultsarenotideal.Atpresent,entityrecognitiontasksusuallyuseneural
networkmodelstobuildsequencelabelingmodelsandtoautomaticallyextractfeatures.
ClassicalencodersincludeConvolutionNeuralNetworks(CNN)[29],BidirectionalLong
Short-TermMemory(BiLSTM)[30],andtheirvariants[31–34].
Recently,pre-trainedlanguagemodels(PLMs)havemadehistoricbreakthroughsin
many natural language processing tasks, such as Embeddings from Language Models
(ELMO)[35],GenerativePre-training(GPT)[36],andBidirectionalEncoderRepresentation
fromTransformer(BERT)[37].Itisundeniablethatapre-trainedBERTmodelperformswell
ingeneraldomains,howeverisinefficientinspecificdomains. Consideringtheshortage

Information2022,13,91 4of18
ofdataresourcesintheeducationfield,fine-tuningcanhelpthemodellearnthedomain-
relatedknowledgebetter. Inaddition,anadaptiveembeddingisconstructedbylexical
enhancement. WeaddedaBiLSTMmodeltocapturetwo-waysemanticdependency. The
CRFmodelcanautomaticallylearnconstraintinformationthroughthetrainingcorpusand
canavoidillegalsequencesinthepredictionresults. Inourpaper,wechoseCRFasthe
decodertoobtaineducationalentities.
2.3. RelationExtraction
Relationextractionisanotherkeystepingraphconstructionthataimstoidentifythe
semanticrelationshipsbetweenentities. Currently,thereareseveralmaintypesofmethods:
template-basedmethods,supervisedlearningmethods,andsemi-supervised/unsupervised
methods[38]. Amongthese,thesupervisedrelationextractionmethodhasdemonstrated
thebestperformance.
Neuralnetworkshavebeenwidelyusedinrelationextraction,suchasinCNNs[29],
andinRecurrentNeuralNetworks(RNN)[39]. Heetal. constructedasystemwithanovel
deepneuralnetwork(DNN)toautomaticallyinferassociationsinthebiomedical-related
literature[40]. Zengetal. proposedanovelmodeldubbedPiecewiseConvolutionalNeural
Networks (PCNNs) with multi-instance learning [41]. Zhang et al. used BiLSTM and
thefeaturesderivedfromlexicalresources[42]. AGraphNeuralNetwork(GNN)[43]is
a kind of neural network that can capture the topological characteristics of graph data.
GNN-basedmodels[44–46]usuallyusethetextdependencytreesastheinputtoana-priori
graphstructureinordertoobtainricherinformationexpression. Usinglanguagemodels
tobetterexpresstherelationship,someworkregardsrelationextractionasadownstream
taskPLM.Wuetal. proposedamodelthatbothleveragestheBERTmodelandincorporates
entityinformationtotacklerelationclassificationtasks[47]. Chengetal. designedanew
networkarchitecturewithaspeciallossfunctionasadownstreamPLMmodel[48]. These
language models have achieved good results in terms of relation extraction. Generally
speaking,relationextractiondependsontheinformationinthesentenceandthetarget
entity.BasedontheideaoftheR-BERTmodel[47],inthispaper,weuseaneducation-based
lexicontopre-processthecorpusandintroduceentitylocationinformationintotheBERT
modelthatcanbetterfusesentenceandlexicalfeaturestoachieverelationextractiontasks.
3. Methods
Inthissection,thedetailedmethodisintroduced. First,weintroducehowtoconstruct
amulti-modaleducationalknowledgegraph. Second,wedescribetheentityrecognition
andrelationextractionmethodsindetail. Finally,wedemonstratehowtoutilizeteacher
speechtobuildtheknowledgegraph.
3.1. FrameworkOverview
In order to better construct a knowledge graph for a specific educational field, we
dividedoursystemframeworkintothefollowingthreemodules: aneducationalconcept
recognitionmodule,aneducationalrelationextractionmodule,andateacherspeech-fusion
module. AdiagramoftheframeworkisshowninFigure1. Themodulescanbedescribed
asfollows:
• EducationalConceptRecognitionModule: Themaingoalofthismoduleistoextract
teaching concepts or educational entities in a specified course. Online education
resources include Baidu entries and Jianshu articles. Offline education resources
usually include course outlines, PowerPoints, and teaching courses. The lexicon
enhancementmethodisusedtopre-processthedata,andthencombineafine-tuned
BERTmodeltoextracttheeducationalconcepts. Thefinaloutputsofthismoduleare
theextractedconcepts,whicharethebasisfortheconstructionoftheknowledgegraph;
• EducationalRelationExtractionModule: Themaingoalofthismoduleistoassociate
theextractededucationalconceptstohelplearnersclarifytherelationshipbetween
knowledgeconcepts. Vocabularyinformationisstillimportantforrelationclassifica-

Information 2022, 13, x FOR PEER REVIEW 5 of 19
include course outlines, PowerPoints, and teaching courses. The lexicon enhancement
method is used to pre-process the data, and then combine a fine-tuned BERT model to
extract the educational concepts. The final outputs of this module are the extracted
concepts, which are the basis for the construction of the knowledge graph;
• Educational Relation Extraction Module: The main goal of this module is to associ-
Information2022,13,91 ate the extracted educational concepts to help learners clarify the relations5hoifp1 8be-
tween knowledge concepts. Vocabulary information is still important for relation
classification. This module uses the acquired entities for vocabulary labeling and
ctioomn.biTnheiss imtsoedlfu wleituhs etsheth BeEaRcqTu mireoddeenl ttioti edsisftoirngvuocisahb uthlaer ypolatbeneltiinagl raenldaticoonmshbiinpess be-
tiwtseelefnw eidthutchaetiBonEaRlT comnocdeeplttso; distinguishthepotentialrelationshipsbetweeneduca-
• T ti e o a n c a h l e c r o n S c p e e p e t c s h ; Fusion Module: The teacher’s voice is also an important resource in
• TeacherSpeechFusionModule: Theteacher’svoiceisalsoanimportantresourcein
the field of education. The main goal of this module is to fuse real classroom teacher
thefieldofeducation. Themaingoalofthismoduleistofuserealclassroomteacher
speech as a kind of entity into the text-based education knowledge graph. The
speechasakindofentityintothetext-basededucationknowledgegraph. Themodule
module mainly uses Mel Frequency Cepstral Coefficients (MFCC) to extract speech
mainlyusesMelFrequencyCepstralCoefficients(MFCC)toextractspeechfeature
feature variables and performs the Fourier transform. HMM is used to obtain speech
variablesandperformstheFouriertransform. HMMisusedtoobtainspeechtextand
text and calculate similarity. Teacher speech is matched with text entities.
calculatesimilarity. Teacherspeechismatchedwithtextentities.
Figure 1. Construction framework of our multi-modal educational knowledge graph.
Figure1.Constructionframeworkofourmulti-modaleducationalknowledgegraph.
33..22.. EEdduuccaattiioonnaall CCoonncceeppttss RReeccooggnnitiitoionn
TThhee ddoommaaiinn iinnffoorrmmaattiioonn ccoonnttaainineeddi ninv ovcoacbaubulalrayryc acnanh ehlpelpw iwthitehn teintytitryec oregcnoigtinointion
ppeerrffoorrmmaannccee.. DDuuee ttoo tthhee sshhoorrttaaggeeo offl alabbeleilninggd adtaatare rseosuorucrecse,sp, rpe-rter-atirnaiinnginmg omdoeldseslus cshucahs as
BBEERRTT uussee tthheemm ddiirreeccttllyy ffoorr eennttiittyy rreeccooggnniittiioonn iinn tthhee vveerrttiiccaall ddoommaaiinn,, wwhhiicchh mmaayy nnoott bbee ef-
feefcfteicvteiv. eF.irFsitr, swt,ew cerecareteadte adna endeudcuactaiotino nvovcoacbaublualrayr.y T. hTrheree eddoommaianin eexxppeertrst saannnnootatatetedd ththee en-
teitnietist ieins itnheth ceocuorusres eououtltinline.e .WWhheenn ttwwoo oorr mmoorree eexxppeerrttssm maarkrkededt htehes asmameeen etintytittyy ptey,pwe,e we
regardeditasthefinaltypeoftheentity. Thevocabularyconsistedoftheseentities. Then,
regarded it as the final type of the entity. The vocabulary consisted of these entities. Then,
weproposedamodelcalledEduBERT-BiLSTM-CRFtoimprovetheaccuracyofeducational
we proposed a model called EduBERT-BiLSTM-CRF to improve the accuracy of educa-
conceptrecognitionbycombiningtheeducationallexicontoencodethecharactersaswell
tional concept recognition by combining the educational lexicon to encode the characters
asafine-tunedBERTmodel. Figure2showsthearchitectureofourmodel,whichconsists
as well as a fine-tuned BERT model. Figure 2 shows the architecture of our model, which
offourparts. Thefirstpartisthecharacterrepresentationmodule;thesecondpartisthe
consists of four parts. The first part is the character representation module; the second part
fine-tuned BERT module; the third part is BiLSTM module; and the fourth part is CRF
is the fine-tuned BERT module; the third part is BiLSTM module; and the fourth part is
module. First,eachcharacterinasentencecorrespondstoadensevector. Accordingto
CRF module. First, each character in a sentence corresponds to a dense vector. According
thedomainlexiconthatwebuilt,allofthevocabularyinformationcorrespondingtoeach
characterisaddedtotherepresentationofeachcharacter. Then,theseenhancedcharacters
areintroducedintofine-tunedBERT,andwordembeddingscanbelearnedbyBiLSTM.
Finally,theoutputoftheBiLSTMmodelisdecodedtoobtaintheoptimallabelsequence.

InInfofromrmataitoinon 2 2002222, ,1 133, ,x x F FOORR P PEEEERR R REEVVIEIEWW 66 oof f 1199
toto t hthee d doommaainin l elexxicicoonn t hthaat tw wee b buuilitl,t ,a alll lo of ft hthee v vooccaabbuulalaryry i ninfoformrmaatitoionn c coorrreressppoonnddiningg t oto
eeaacchh cchhaararaccteter r isis aaddddeedd toto ththee rereppreresseenntatatitoionn oof f eeaacchh cchhaararaccteter.r . TThheenn, , ththeessee eennhhaanncceedd
cchhaararacctetersrs a arere i nintrtorodduucceedd i nintoto f ifninee-t-utunneedd B BEERRTT, ,a anndd w woordrd e emmbbeeddddininggss c caann b bee l eleaarnrneedd b byy
Information2022,13,91 6of18
BBiLiLSSTTMM. .F Fininaalllyly, ,t hthee o ouutptpuut to of ft hthee B BiLiLSSTTMM m mooddeel li sis d deeccooddeedd t oto o obbtatainin t hthee o opptitmimaal ll alabbeel l
sseeqquueennccee. .
FFigiguurere 2 2. .T Thhee a arcrchhitietecctuturere o of ft hthee E EdduuBBEERRTT-B-BiLiLSSTTMM-C-CRRFF m mooddeel lf ofor re edduuccaatitoionnaal lc coonncceeppt tr ereccooggnni-i-
Figure2.ThearchitectureoftheEduBERT-BiLSTM-CRFmodelforeducationalconceptrecognition.
titoionn. .T Thhee i ninppuut ts esenntetennccees sa arere a abblele t oto o obbtatainin f ofouur rt ytyppees so of ft atagg s esetst sa accccoordrdiningg t oto t hthee i ninfoformrmaatitoionn i nin t hthee
Theinputsentencesareabletoobtainfourtypesoftagsetsaccordingtotheinformationinthe
vvooccaabbuulalaryry. .T Thheesese v veecctotorsr sa arere u usesedd a as st hthee f ifninee-t-utunneedd B BEERRTT i ninppuut,t ,a anndd t htheeyy a arere t htheenn e ennccooddeedd a anndd
vocabulary. Thesevectorsareusedasthefine-tunedBERTinput,andtheyarethenencodedand
ddeeccooddeedd b byy B BiLiLSSTTMM a anndd C CRRFF t oto c coommppleletete s eseqquueennccee a annnnootatatitoionn. .T Thhee C Chhinineesese i ninppuut ti si s“ “排排序序是是算算法法””
decodedbyBiLSTMandCRFtocompletesequenceannotation.TheChineseinputis“排序是算法”
(s(osortritningg i si sa ann a alglgoorirtihthmm).) .
(sortingisanalgorithm).
33.2.2.1.1. .C Chhaararaccteterr R Reepprreesseenntatatitoionn
3.2.1. CharacterRepresentation
GGiviveenn t hthee c coonnvveerrtetedd e edduuccaatitoionnaal ld daatata, ,t hthisis c coonncceeppt te exxtrtraacctitoionn t atasskk c caann b bee v vieiewweedd a ass
Giventheconvertededucationaldata,thisconceptextractiontaskcanbeviewedasa
aa w woorrdd s seeqquueennccee l alabbeelilningg p prroobblelemm. .T Too p prreesseerrvvee a ass m muucchh v vooccaabbuulalaryry a ass p poossssibiblele f oforr a alll lo of f
wordsequencelabelingproblem. Topreserveasmuchvocabularyaspossibleforallofthe
ththee c chhaarraacctetersrs, ,w wee d deefifnineedd f ofouurr w woorrdd l alabbeel ls seetsts: :( 1(1) ) 𝐵𝐵: :“ “ccoonntataininss a alll lw woorrddss s statarrtitningg w witihth
characters,wedefinedfourwordlabelsets: (1)B: “containsallwordsstartingwiththis
ththisis cchhaarraaccteterr””; ; (2(2) ) 𝐼𝐼: : ““ccoonntataininss aalll l wwoorrddss wwitihth ththisis cchhaararaccteterr inin ththee mmididddlele””; ; (3(3) ) 𝐸𝐸: :
character”;(2) I: “containsallwordswiththischaracterinthemiddle”;(3)E: “containsall
““ccoonntataininss a alll lw woorrddss e ennddiningg w witihth t hthisis c chhaararaccteterr””; ;a anndd ( 4(4) )S S: :“ “vvooccaabbuulalarryy c coonnssisistitningg o of fo onn--
wordsendingwiththischaracter”;and(4)S:“vocabularyconsistingofonlythischaracter”.
lyly t hthisis c chhaararaccteterr””. .F Figiguurree 3 3 s shhoowwss a ann e exxaammpplele. .
Figure3showsanexample.
FFFiigigguuurreree 3 33.. .A AAnnn e eexxxaaammmppplelle et otto oi lililulllusutssrttarrataette et atatgag gc occolollellecletcitcoitonion. n.T .ThhTee hc ehchacarharaacrcteaterc rt“ e“泡r泡“”泡” o oc”ccuocucrscr sui nrins t witnwoto ww wooorwdrdso,s r,ad ansnd,d ai nti tdo oci-ct-
couccurcsru si rnisn t ihtnhee tm hmeididmddlielde od ofl fe“ “冒o冒f泡泡“排冒排序泡序”排” a an序ndd” a aat tnt htdhee ae tenntdhd oe of ef“ n“冒d冒泡o泡f””.“ .T冒 Thhe泡erer”ef.oforTerhe, ,te htrheee fIo -Ilr-aleab,betelh lse esetI t-i lsia s“b “冒e冒l泡s泡e排t排i序s序”“” 冒a an泡ndd
t排hthe序e E E-”l-alaabnbedel ls teshet eti siE s“ -“冒 l 冒 ab 泡泡 e”l”.s .Te Ththeise C C“h冒hinin泡ees”ese .i niTnphpueut tiC si sh“ i“冒 n 冒 e 泡 s 泡 e 排排 in 序序 p 是 u 是 t 一 i 一 s 种种 “ 算冒算法泡法”排” ( b(序buub是bbbl一ele s种 osor算tr ti s法i sa a”nn (a balgulgoborbirtlihethmsmo).r) .t is
analgorithm).
TThhee ininppuut t sseeqquueennccee isis sseeeenn aass aa cchhaararaccteterr sseeqquueennccee 𝑆𝑆== (cid:4668) 𝑥(cid:4668)𝑥,𝑥,𝑥,…,…,𝑥,𝑥(cid:4669),(cid:4669) , aanndd eeaacchh
(cid:2869)(cid:2869) (cid:2870)(cid:2870) (cid:3041)(cid:3041)
cchhaararTacctheteerr i 𝑥n𝑥
(cid:3036)
p
(cid:3036)
u (1(t1s(cid:3409)e(cid:3409)q𝑖𝑖u(cid:3409)(cid:3409)en𝑛𝑛c)e )i siis sa a sf eofeounurr-aw-swoaordrcdh s asereta.t .cT tToeo ru usteitliqilziuzeee nt htcheee l Selex=xicico{onxn
1
i ni,nfxof
2
orrm,m.a.a.tit,oixon nn }e ,efffaefneccdtitvieveaelcylhy, ,
tchthheae cr caooclltleelecrctxetedd( 1v vo≤occaiabb≤uulanlar)yriy si sias c fcooomumrp-pwrreoesrssdseedsd eu tu.ssiTnionggu w twioliorzrded wt hweeeiglieghxhtiitcniongng. .iI ntIstfs oe reqmquuaaattiitooionnn ei sifs fe ctively,the
i
collectedvocabularyiscompressedusingwordweighting. Itsequationis
11
𝑣𝑣(cid:3046)(cid:3046)((𝑆𝑆))== (cid:3533)(cid:3533)((𝑧𝑧((𝑤𝑤))++𝑐𝑐))𝑒𝑒(cid:3050)(cid:3050)((𝑤𝑤))
(1(1) )
vs(S) =
1𝑍𝑍
∑ (cid:3050)(cid:3050)∈∈(cid:3020)((cid:3020)z(w)+c)ew(w) (1)
Z
w∈S
∑
Z = z(w)+c (2)
w∈B∪I∪E∪S
Here,Sdenotesawordset,ew denotesthewordembedding,z(w)denotestheword
frequency,Zisthefour-classlabelweightnormalization,andcdenotesthenumberofthe
wordsets.

Information2022,13,91 7of18
Thedatasetconsistsofatrainingsetandatestset. Thefrequencyofthecharacter
willnotincreaseifashortwordcomposedof x iscoveredbyalongword. Thisavoids
i
theproblemwherethefrequencyofashortwordisalwayslessthanthefrequencyofthe
long word covering it. We use “链表” (linked list) and “双向链表” (double-linked list)
as examples. When calculating the word frequency of the double-linked list, the word
frequencyofthelinkedlistdoesnotincreaseasthelinkedlistanddouble-linkedlistoverlap.
Byembeddingvocabularycollectionsintocharacters,themodelcanmakebetteruseof
characterinformationandvocabularyinformation.
3.2.2. Fine-TunedBERT
To make better use of contextual semantic features, we use BERT as the generator
togeneratewordembeddingasinputtothenextmodule. Unlikepreviouspre-trained
models,suchasWord2vec[49],theBERTmodelcombinestheadvantagesoftheELMO[35]
andGPT[36]models. Insteadofusingthetraditionalone-waylanguagemodelorshallow
splicingoftwoone-waylanguagemodelsforpre-training,itusesamulti-layerbidirectional
transformernetworkstructuretogeneratebidirectionalsemanticfeatures. ABidirectional
transformerencoderisthekeystructureofBERT,anditsmainroleistheself-attention
mechanism. Itcomputestheattentionfunctionforasetofqueriesandpacksitintomatrix
Q. ThekeysandvaluesarestoredintomatricesKandV.Self-attentionadjuststheweight
factor matrix to obtain the representation of words based on the degree of correlation
betweenwordsinthesamesentence:
(cid:18) QKT(cid:19)
Attention(Q,K,V) =Softmax √ V (3)
d
k
whereQ = K =V andd istheembeddingdimension.
k
Themulti-headattentionmechanismprojectsQ,K,andVthroughseveraldifferentlin-
eartransformations,andfinally,itstitchestogetherdifferentattentionresults. Itsequations
areasfollows:
MultiHead(Q,K,V) =Concat(head ,··· , head )WO (4)
1 n
head =Attention(QW Q ,KWK,VWV) (5)
i i i i
whereW Q ,WK,WV,andWO areparametermatrices.
i i i
TheChineseBERTmodelproposedbyGooglewastrainedusingChinesecharacters.
These characters are randomly blocked when the model generates training samples. It
does not consider traditional Chinese word segmentation, so this paper introduces a
newmechanism: thewholewordmask;thatis,ifapartofthewordthatbelongstothe
samewordisblocked,thentheotherpartsofthewordarealsoblocked. Table1shows
anexample.
Table1. Anillustrationofthecurrentmaskmechanism. TheChineseinputis“排序是一种算法”
(sortingisanalgorithm).Theresultoftheinputsentenceafterwordsegmentationisseveralwords:
“排序”(sort),”是”(is),”一种”(a),and“算法”(algorithm).UsingtheoriginalMASKmechanism,only
partofthewordscanbemasked,suchas“排[M]”and“[M]法”.UsingthecurrentMASKmechanism,
thewholewordcanbemasked.Forexample,“排序”canbemaskedbythetoken[M].
排序是一种算法
Input
(SortingIsanAlgorithm)
WordSegmentation 排序是一种算法
OriginalMask 排[M]是一种[M]法
CurrentMask [M][M]是一种[M][M]

Information2022,13,91 8of18
For the education field, there is a general lack of corpus, and the existing corpus
cannotprovideenoughdataforBERTpre-training. Therefore,weusedfine-tunedBERT
toimproverecognitionaccuracy. AfullyconnectednetworkwasusedatthetopofBERT,
obtaining768-dimensionalcontextrepresentation. TheBERTmodelinthispaperconsists
of12layers,eachofwhichfusesthesemanticinformationofthecontext. Wefine-tuned
thelastfourlayers. Wemaskedpartofthewordsequenceasawholeword,andmarked
thebeginningofthesentencewitha[CLS],separatingthesentencefromthesentencewith
a[SEP].Theoutputembeddingofeachwordconsistsofthreeparts: tokenembedding,
segmentembedding,andpositionembedding. Theseembeddingscanmakebetteruseof
lexicalfeaturesandsentencefeatures. Sequencevectorsareinputtedintothebidirectional
transformerforfeatureextraction,andthensequencevectorswithrichsemanticfeatures
areobtained.
3.2.3. BiLSTMEncoder
BiLSTMisusedtoextractfeaturesfromthesesentencesthroughtwoLSTMs,andfor
learning,eachtokeninthesequenceisbasedonboththefutureandthepastcontextofthe
token. Bothforwardandbackwardinformationisavailableforeachmoment.
TheBERToutputwordvectorisusedastheinputforeachBiLSTMtimestep. Ateach
timestept,ahiddenforwardlayermanagesthesequencefromstep1tostept,obtaininga
|     |     | → → → | →   |     |     |     |
| --- | --- | ----- | --- | --- | --- | --- |
forwardhiddensequence(h , h , h ,... h ),andahiddenbackwardlayerwiththesame
|     |     | 1 2 | 3 t |     |                            |          |
| --- | --- | --- | --- | --- | -------------------------- | -------- |
|     |     |     |     |     | (cid:40) (cid:40) (cid:40) | (cid:40) |
sequenceasstepttostep1,obtainingabackwardhiddensequence(h 1 , h 2 , h 3 ,..., h t ).
→ (cid:40)
Hidden layer state sequence stitching is generated, that is, h = [h : h ]. By matrix
t t t
changingtheoutputsequence,thehiddenstatesequenceismappedintothekdimension
(kisthenumberofcategoriesoflabels)viathelinearoutputlayer. Themappingmatrix
Q= (q ,q ,...,q ) ∈ Rn∗k arethecombinedoutputs,whereq andkarethescoresofthe
| 1   | 2 n |     |     | n   |     |     |
| --- | --- | --- | --- | --- | --- | --- |
k-thlabelrelativetothen-thcategory.
3.2.4. CRFDecoder
The BiLSTM model is good at handling long-distance text information. The CRF
modelcanusetherelationshipbetweenadjacententitylabelstoobtaintheoptimalpre-
dictionsequence. ThebiggestadvantageofCRFistoreducetheprobabilityofirrational
sequencesinthepredictionsequencebyautomaticallylearningrestrictiverules. Inthe
paper, we use different tokens to represent three types of entities: “a” for algorithms,
“s”forstructures,and“c”forbasicterminology. Eachtypeofentityisusedforitsown
BIEOtags,suchasB-a,I-a,I-s,etc. AccordingtoBIEOtags,B-aisusuallyfollowedbyI-a
howevercannotbefollowedbyB-sorI-s. TheinputsentenceisX = (x , x ,..., x ) and,
|      |                                  |          |        |                         | 1 2 n |     |
| ---- | -------------------------------- | -------- | ------ | ----------------------- | ----- | --- |
| = (y | )representsthepredictionresults. |          |        |                         |       |     |
| Y 1  | , y 2 ,..., y n                  |          |        | ThepredictionresultYis: |       |     |
|      |                                  |          | n      | n                       |       |     |
|      |                                  | Score(X, | Y) = ∑ | + ∑                     |       |     |
|      |                                  |          | P      | i,yi A yi,yi+1          |       | (6) |
|      |                                  |          | i=1    | i=0                     |       |     |
wherePisthematrixofthescoresoutputbythelastlayer,andAisamatrixofthetransition
scores;P isthescoreoftheyth tagofthei-thwordinasentence; A representsthe
|     | i,yi | i   |     |     | yi,yi+1 |     |
| --- | ---- | --- | --- | --- | ------- | --- |
scoreofatransitionfromthetagy i toy i+1 ;nisthelengthofasentence. TheCRFmodel
predicts labels for each word as mentioned above. All of the scores can be calculated
accordingtothefollowingformula:
eS(X,y)
|     |     | P(y|X) | =   |                |     | (7) |
| --- | --- | ------ | --- | -------------- | --- | --- |
|     |     |        | ∑   | S(X,y(cid:48)) |     |     |
y∈YX
Inthefinaldecoding,theoptimalsequencelabelingiscomputedasfollows:
|     |     | y ∗ = | argmaxS | (X, y )                  |     | (8) |
| --- | --- | ----- | ------- | ------------------------ | --- | --- |
|     |     |       |         | y(cid:101) ∈YX (cid:101) |     |     |

Information2022,13,91 9of18
3.3. EducationalRelationExtraction
Asmentionedabove,themaingoalofthismoduleistoidentifythelogicalrelation-
shipsthatexistineducationalentitiesandthatfacilitatelearnerslearningmoreeffectively.
Theaboveresearch[8–10,16,22]pointsoutthattheserelationshipsareveryimportantfor
learners: inclusionrelationship,precursorrelationship,identityrelationship,sisterrela-
tionshipandcorrelationrelationship. Table2showstherelationshipcategoriesandtheir
definitions. Thelocationoftheentitiesisveryimportantindeterminingtherelationship.
WelearnedfromtheR-BERTmodeltofusethefeaturesofthesentenceandeducational
entities,whichareidentifiedinthepreviousmodule.
Table2.Educationalrelationshipsandtheirdescriptions.
RelationType RelationDefinition
KnowledgepointAcontainsknowledgepointB,and
InclusionRelationship
knowledgepointBistherefinementofknowledgepointA
KnowledgepointAmustbelearnedbeforelearning
PrecursorRelationship
knowledgepointB
KnowledgepointAandknowledgepointBaredifferent
IdentityRelationship
descriptionsofthesameknowledge
KnowledgepointAandknowledgepointBhavethesame
SisterRelationship
parentknowledgepointC,andthereisnolearningsequence
KnowledgepointAandknowledgepointBdonotconformto
CorrelationRelationship
thepreviousrelationships,althoughtheyarestillrelevant
ForagivensentenceS = {c ,c ,...,c }withtwotargetentitiese ande ,weadda
1 2 n 1 2
specialtoken“#”attheboundaryoftheentitytolocatetheentity. Wealsoinsert“[CLS]”
tothebeginningoftheinputsentence. Theoutputofthe“[CLS]”canbeusedasavector
representationofthesentence. SupposethefinalhiddenstateofBERTis M;forthefinal
hiddenstatevector M ofthetoken“[CLS]”,weaddedanactivationoperationandafully
0
connectedlayer. Itsequationis:
M (cid:48) =W [tanh(M )]+b (9)
0 0 0 0
whereW ∈ Rd∗d,anddisthehiddenstatesizefromBERT.
0
Inadditiontothesentencevector,wealsoneedtocombinethevectorsoftwoentities.
Theentityvectorisobtainedbycalculatingtheaveragevalueofeachwordvector. This
processcanbeexpressedas:
j
1 ∑
E = M (10)
j−i+1 t
t=i
whereiandj denotethebeginningandendofthetargetentity.
Foreachentityvector,theprocessdescribedinFormula(9)needstobeconducted. We
concatenatedtwoentityvectorsandthevectorofthetoken“[CLS]”,thenaddedafully
connectedlayer,whichcanbedescribedasfollows:
M(cid:48)(cid:48) =W (cid:2) concat (cid:0) M (cid:48) ,M (cid:48) ,M (cid:48)(cid:1)(cid:3) +b (11)
1 0 1 2 1
whereW ∈ RL∗3d, L is the total number of relationship types. In this work, we used
1
L =5. M andM denotethefinalhiddenstatevectorsofentity1andentity2,respectively.
1 2
InEquations(9)and(11), b , b arebiasvectors. Finally, weaddedaSoftMaxlayerfor
0 1
classificationprediction.
3.4. TeacherSpeechFusionModule
Teacher speech is also a key resource in the educational knowledge graph, which
isdifferentfromtextandbelongstoanothermodalresource. Thismoduleusesspeech
recognitiontechnologytoprocessaudiosignalsandtointegratetheteacher’sspeechinto

Information 2022, 13, x FOR PEER REVIEW 10 of 19
tively. In Equations (9) and (11), 𝑏 ,𝑏 are bias vectors. Finally, we added a SoftMax
(cid:2868) (cid:2869)
layer for classification prediction.
3.4. Teacher Speech Fusion Module
Teacher speech is also a key resource in the educational knowledge graph, which is
Information2022,13,91 different from text and belongs to another modal resource. This module uses sp10eoefc1h8
recognition technology to process audio signals and to integrate the teacher’s speech in-
to the text knowledge graph. The main speech recognition process includes acoustic
feature extraction, the conversion of the features into pronunciation of a phoneme se-
thetextknowledgegraph. Themainspeechrecognitionprocessincludesacousticfeature
quence/pinyin sequence through the acoustic model, and the speech model transforms
extraction,theconversionofthefeaturesintopronunciationofaphonemesequence/pinyin
tsheeq upehnocneetmhero suegqhuethnecea cinotuos ttiecxmt othdaetl ,aa nhdumthaens pcaene cuhnmdeordsetalntrda. nTsfhoer mmsaitnh epprohcoensesm ise
ssheoqwuenn icne Finigtourtee x4t. thatahumancanunderstand. ThemainprocessisshowninFigure4.
FFiigguurree 44.. TThhee mmaaiinn pprroocceessss ooff ssppeeeecchh rreeccooggnniittiioonn..
WWee ccoonnvveerrtteedd tthhee aauuddiioo ddaattaa iinnttoo WWAAVV ssppeeeecchh ffrraaggmmeennttss tthhaatt wweerree aabbllee ttoo bbee pprroo--
cceesssseedd,, oobbttaainineedd ththee frfarammee nnuummbebre ranadn dsosuonudn dchcahnannenl eolf otfheth seousonudn, dan, dan udseuds eMdFMCCFC tCo
etxotreaxcttr atchtet hspeesepcehe cfehaftuearetu vreecvtoerc tomramtriaxt rtiox ctooncsotnrustcrtu tchtet hinepiuntp utetntseonrs. oTr.heTnh, etnh,et hteentseonr-
nseoerdneede dtoe dbeto frbaemferadm aendd awndindwoiwndeodw, aendd, atnhde vtheectvore cmtoartrmixa twriaxs wgaesnegreanteedra tthedrotuhgrho uthgeh
FthouerFieoru rtirearntsrfaonrmsf.o rTmh.e Tahceouasctoicu smticodmeol duelseuds edtheth ededeepe pleleaarnrnining gffrraammeewwoorrkk KKeerraass
((hhttttppss::///k/ekraesr.aios./i)o (/a)cc(eascsceedss oend 8o nFe8brFueabrryu 2a0r2y22) 0to2 2d)etfoinde eafinn 1e1a-lnay1e1r- lnaeyuerranl neuetrwalonrke tCwNoNrk
CNNstructure,andthelossfunctionusedConnectionistTemporalClassification(CTC)
structure, and the loss function used Connectionist Temporal Classification (CTC) algo-
algorithm. CTCalgorithmcanrealizeend-to-endnetworktrainingwithouttheaudiodata
rithm. CTC algorithm can realize end-to-end network training without the audio data be-
beingpre-alignedandrequiresonlyoneinputsequenceandoneoutputsequence. CTC
ing pre-aligned and requires only one input sequence and one output sequence. CTC al-
algorithmcandirectlyoutputtheprobabilityofthesequencepredictionwithoutexternal
gorithm can directly output the probability of the sequence prediction without external
post-processing. Therefore,CTCalgorithmisalsousedtodecodetherecognitionresults
post-processing. Therefore, CTC algorithm is also used to decode the recognition results
and to generate phoneme sequences. These phoneme sequences are used as the input
and to generate phoneme sequences. These phoneme sequences are used as the input of
ofHMMlanguagemodel,andthedecodingprocessfromphonemesequencestotextis
HMM language model, and the decoding process from phoneme sequences to text is real-
realizedthroughthelanguagedictionary.
ized through the language dictionary.
Aftercompletingspeechrecognition,welinkedthespeechentitieswithtext-based
After completing speech recognition, we linked the speech entities with text-based
educationentities. Todistinguishtherelationshipbetweenthesetextentities,weredefined
education entities. To distinguish the relationship between these text entities, we rede-
therelationshipbetweenspeechandtextentitiesasan“associationrelationship”. First,the
fined the relationship between speech and text entities as an “association relationship”.
extractedsetofeducationalentitieswasconstructedasadomainlexicon. Eacheducational
First, the extracted set of educational entities was constructed as a domain lexicon. Each
conceptintheentitysethasauniqueid. Second,thespeechentityisnumbered. Then,the
educational concept in the entity set has a unique id. Second, the speech entity is num-
speechandtheentitiesinthegrapharelinkedbytextmatchingtechnologytoformanew
bered. Then, the speech and the entities in the graph are linked by text matching tech-
triplegrouping.
nology to form a new triple grouping.
4. ResultsandDiscussion
4. Results and Discussion
Toevaluateourproposedconstructionsystem,weconstructedanexemplaryknowl-
To evaluate our proposed construction system, we constructed an exemplary
edgegraphfortheprofessionalcomputercurriculumdatastructure. Theperformanceof
kthneowsylsetdegme wgraaspehv afolur attheed pcoromfepsrseihoennasl icvoemly.puter curriculum data structure. The perfor-
mance of the system was evaluated comprehensively.
4.1. ExperimentSettings
44..11.. 1E.xDpeartiamseentt Settings
4.1.1. TDoamtaaskete ourknowledgegraphricherandmorecomprehensive,wecreatedadataset
baseTdoo mnatkhee oduart akncoowllelecdtegde fgrroamphc ruicrhriecru alunmd mteoarceh cionmgprerseohuenrcseivsea, nwde ocrnelainteede ad udcaatatisoent
breassoedu rocens .thTeh deaotan licnoelledcattead mfraoimnl ycuinrrcilcuudleudmc oteuarcsheinogu trleinsoe,uBrcaeisd uanedn torinelsi,nea nedduJicaantsiohnu
articles,theofflineclassroomdataincludedcourseware,textbooks,andteacheraudio.
First,thedomainexpertsmarkedtheentitiesofthecourseoutline(https://wenku.
baidu.com/view/9ac023c85901020207409ce8.html)(accessedon8February2022),resulting
inatotalof233entities. Basedonthecourseoutline,wetrawledthroughunstructured
educationaltextresourcesfromtheBaiduEncyclopediaandJianshubooks(eachkeyword
gets the first 30 pages of articles). The beautifulSoup4 library (https://www.crummy.
com/software/BeautifulSoup/)(accessedon8February2022)andtheSeleniumlibrary
(https://www.selenium.dev/)(accessedon8February2022)wereusedtocrawlfromthe
website. TheBaiduEncyclopediadatasetcomprisedatotalof15,674sentences,andthere
were6690theJianshuarticleintotal. Forthecourseware, textdatawereextractedand

Information2022,13,91 11of18
savedbasedontexttype,obtaining8793sentences. Tominimizethenoiseoftheoriginal
data,datacleaningwasrequiredtoremoveirrelevantsymbolsfromthetext. Inaddition,
wealsodownloadedandsavedtheentiretyoftheclassroomaudio. Thecollectedaudio
resourceswereuniformlyconvertedintoWAVformatforpost-processing.
4.1.2. DataPreprocessing
To evaluate the entity recognition task, 8793 courseware sentences were obtained
as labeled datasets. The educational concepts were labeled according to the BIES label
set proposed above. The main objects are three types of educational entities: “/a” for
algorithm, “/s” for structure, and “/c” for basic terminology. The labeled datasets are
dividedintotrainingandtestsetsataratioof7:3.
For the relation extraction task, the data that were extracted from the relationship
camefromcourseware,Baiduentries,andJianshuarticles,anddatasuchasgraphsthat
werenotrelevantforourresearchwereremoved. InordertoenableBERTtocapturethe
locationinformationofthetwoentities,aspecialtag[CLS]wasaddedtothefrontofeach
sentence, and the sentences were separated by [SEP]. At the beginning and end of the
twoentities, thetag“#”wasusedtodistinguishtheentitiesinthesentence. Whenthe
modelrecognizesthefirsttwo“#”,thenittakesthedatabetweenthetwotagsasthefirst
entity,andthedatabetweenthetwotagsasthesecondentitywhenitidentifiesthethird
andfourth”#”. Aftertheentitiesaremarked,therelationshipbetweenthetwoentitiesin
thesentencemustalsobemarkedafterthesentence. Forthecourseware,ifthesentence
containstwoentities,thenitshouldbemarkedaccordingtotheabovemethod. Whenthe
sentencecontainsmorethanoneentity,thenthesentenceisdiscardeddirectly. Inthispaper,
we manually labeled 1452 sentences in the courseware. For Baidu entries and Jianshu
articles,onlysentencescontainingtwoentitieswereretained,andsentenceslessthanfive
words after word division were discarded. Jianshu articles were automatically labeled
withthedatalabeledbythreedomainexpertstoexpandtheexperimentaltrainingset. A
totalof30,000sentenceswereautomaticallylabeled,andtheyweremanuallyreviewedby
domainexperts. Thesentencesweredividedintoatrainingsetandtestsetaccordingly,
ata7:3ratio.
4.1.3. EvaluationMetrics
Accuracy(Acc),Precision(P),Recall(R),andF1-Score(F1)weretheevaluationcriteria
usedforourexperiments.
TP+TN
Acc = ×100% (12)
TP+TN+FP+FN
TP
P = ×100% (13)
TP+FP
TP
R = ×100% (14)
TP+FN
2PR
F1_score = ×100% (15)
P+R
whereTPrepresentsthenumberoflabelsthatarepositiveandpredictedtobepositive.
TN represents the number of labels that are negative and predicted to be negative. FP
representsthenumberoflabelsthatarenegativeandpredictedtobepositive. FNrepresents
thenumberoflabelsthatarepositiveandpredictedtobenegative.
4.2. ExperimentResultsonEntityRecognition
4.2.1. ModelComparison
Fortheproposedentityrecognitionmodel,themodelparameterswerefirstsetduring
training. Batch size is the sample size used in each iteration, which can determine the

Information2022,13,91 12of18
directionofthegradientdescent. Forthesizeofthedatasetinthispaper,thebatchsizewas
setto64. Thelearningrateaffectstheconvergencespeedandfittingeffectofthemodel.
Thelearningratewassetto0.0001withtheAdamoptimizer,andthedropoutratewas0.5.
Wetrainedthemodelfor100epochsusinganearlystoppingstrategy. Forbaselinemodels,
we used the same parameters as those outlined in their original papers or during their
originalimplementation.
Toverifytherecognitioneffectofthemethodinthispaper,wecomparedourmethod
againsttheresultsbybaselinemethods,includingBiLSTM-CRFandBERT-BiLSTM-CRF.
Table3showsalloftheresultsofthebaselinesandourmodel.
Table3.ComparisonofexperimentalresultsoftheBiLSTM-CRFmodel,BERT-BiLSTM-CRFmodel
andourmodel. Weranallmodels20timesandtooktheaverage. Theresultsindicatedstatistical
significancebaseonStudent’st-test(p<0.05).
Method P R F1
BiLSTM-CRF 80.04% 82.07% 81.06%
BERT-BiLSTM-CRF 80.34% 85.49% 82.83%
EduBERT-BiLSTM-CRF 85.32% 85.72% 85.52%
Theexperimentalresultsshowthateachmodelworkswellwhenusingourdataset.
BiLSTMcombinesaforwardLSTMandabackwardLSTMtomodeltheinformationbefore
andafterthesentenceinordertomakebetteruseofcontextinformation. TheCRFlayer
canautomaticallylearntheconstraintsinthesentenceandcanaddconstraintlabelstothe
BiLSTMoutput,improvingentityrecognitionperformance. TheprecisionandF1values
forBiLSTM-CRFare80.04%and81.06%,respectively. OnthebasisofBiLSTM-CRF,adding
aBERTmodelcanmakebetteruseoflocalandglobalinformation. Accordingtotheresults,
themodelwithBERTimprovedtheF1by1.77%,indicatingthatBERThelpstoimprovethe
namedentityrecognitionperformance.
Duetothelackofdatabasesintheeducationfield,thetraditionalBERTmodelcannot
extractthefeaturesinthesequencewell. Educationaldatahavetheirowncharacteristics
thatcannotbeignored. Theresultsshowthatourmodelperformsbetterandthatboth
the precision and the F1 increased by 4.98% and 2.69%. One reason for this is that we
usedafine-tunedBERTmodel. Thefine-tunedBERTmodelprovidesdomainawareness
andenrichesthecontextsemanticsoftheverticaldomain,whichisparticularlyimportant
for the vertical domain NER. Another main reason for this is that we used the lexicon
method. Byusingapredefineddomaindictionarytoconstructanadaptiveembedding,
moredomaininformationisbroughtintothesequencelabeling.
Basedontheanalysisoftheexperimentalresults,themethodusedinthispaperhas
achievedgoodresults. Thispaperalsousedthismodeltocompletetheentitypredictionof
unlabeledtextdatatoensurethequalityoftheentitydataandoftheknowledgegraph.
4.2.2. ParameterSensitivityAnalysis
Whiletrainingthemodel,therearetwoimportantparametersthatneedtobecon-
sidered: thelearningrateandthedropoutvalue. Ifthelearningrateistoolarge,thenthe
modelwillconvergetoofastandmayexceedtheoptimalvalue. Ifthelearningrateistoo
small,thenthemodelwillconvergetooslowlyanditmayevencausethemodeltofailto
converge. Thedropoutmethodcanbeusedtoavoidover-fittingduringmodeltraining.
Basedontheaboveconsiderations,thispaperaddscomparativelearningrateanddropout
valueexperimentstoexplorethemodelwhilealsoobtainingthebestresults.
First,byadjustingthelearningratecontinuously,themodeleffectswerecompared
whenthelearningratewas0.01,0.001and0.0001. Table4showstheexperimentalresults
fordifferentlearningrates. Foramodelwithalearningrateof0.0001,thevalueofF1was
higherthanthatofthemodelwithotherlearningrates,sothelearningratewaschosenas
0.0001basedontheperspectiveofmodelperformance. Thedropoutparametersforthe
experimentalsoneedtobetakenintoconsideration. Intheforwardpropagationprocess,

Information2022,13,91 13of18
thedropoutmethodcausesacertainneurontostopworkingtemporarilyaccordingtoa
certainprobability,P,whichmakesthegeneralizationabilityofthemodelstronger. Models
canberegularizedtosomeextentbynotrelyingonlocalcharacteristicstoomuch. The
resultsofourmodelwithdifferentdropoutsareshowninTable5. Theexperimentalresults
show that the model with dropout equal to 0.5 has better performance, so the dropout
valueof0.5wasselected.
Table4.Comparisonofexperimentalresultsofourmodelwithdifferentlearningrates.Weranall
models20timesandtooktheaverage.TheresultsindicatedstatisticalsignificancebasedonStudent’s
t-test(p<0.05).
LearningRate F1
0.01 82.43%
0.001 83.97%
0.0001 85.61%
Table5.Comparisonofexperimentalresultsofourmodelwithdifferentdropoutvalues.Weranall
models20timesandtooktheaverage.TheresultsindicatedstatisticalsignificancebasedonStudent’s
t-test(p<0.05).
Dropout F1
0.1 84.92%
0.3 85.31%
0.5 85.78%
0.7 85.12%
0.9 84.72%
Figure 5a shows that the loss value decreases gradually as the number of epochs
increases,anditthendecreasestoasmallerandmorestablevalueafter10iterations. By
Information 2022, 13, x FOR PEER REVIEW 14 of 19
comparingtheaboveparameters,weselectedthemodelwithalearningrateof0.0001and
adropoutvalueof0.5. AsshowninFigure5b,thismodelhadthebestperformance.
(a) (b)
Figure 5. (a) The loss value changes with the epoch; (b) model results with learning rate and
Figure5.(a)Thelossvaluechangeswiththeepoch;(b)modelresultswithlearningrateanddropout
dropout value of 0.0001 and 0.5, respectively.
valueof0.0001and0.5,respectively.
4.43..3E. EmmpipriirciaclaRl Reseuslutsltso nonR RelealtaiotinonE xEtxrtarcatciotinon
ThTehere rseuslutsltosf oafl lamll omdeoldsealrse asrheo swhnowinnT ianb lTea6b.lBe i6L.S BTiMLS[T4M2], [C4N2]N, C[N29N], a[2n9d],P aCnNdN PC[4N1]N
w[e4r1e] swetearec csoertd ainccgotroditnhge itroo trhigeiinr aolrpigaipnearl sp.aTpheerse. xTpheer iemxepnetraimlreensutallt sresshuolwts tshhaotwth tehfaot uthre
mfooduer lmshoaddelsso hmaed esfofemcet oenffethcte oend uthcea teidonuaclatrieolnatailo rnelcalatisosnifi cclaatsisoinfi.caIttisohno. uItl dshboeunldo tbeed nthoatetd
thtehaBti LthSeT BMiLmSTodMe lmpoedrfeolr pmeerdfotrhmeewd othrset wonorosut rodna otuasre dtsa.taTsheetsr.e Tahsoen refoasrotnh ifsocro tuhlids cboeutlhda bte
that although the BiLSTM uses two LSTMs to extract forward and reverse semantic fea-
tures, as a result of the limited data, it cannot learn vocabulary features well. A vocabu-
lary feature is an important factor in relation to extraction. CNN automatically extracts
local features without complex data preprocessing. Using a single maximum pooling for
convolution layer output can extract text feature representations to some extent, however
it is difficult to capture the structural information between two entities. PCNN can divide
the output of the convolutional layer into three parts based on the position information of
the two entities, which could also be the reason why PCNN demonstrated better per-
formance. Similarly, our model also incorporates entity location information. The dif-
ference is that our method uses the powerful coding capabilities of the BERT model and
extracts both the semantic and grammatical features of the text. Our model achieved the
highest accuracy with F1, achieving 75.26% and 80.39%, respectively.

Information2022,13,91 14of18
althoughtheBiLSTMusestwoLSTMstoextractforwardandreversesemanticfeatures,as
aresultofthelimiteddata,itcannotlearnvocabularyfeatureswell. Avocabularyfeature
isanimportantfactorinrelationtoextraction. CNNautomaticallyextractslocalfeatures
withoutcomplexdatapreprocessing. Usingasinglemaximumpoolingforconvolution
layeroutputcanextracttextfeaturerepresentationstosomeextent,howeveritisdifficultto
capturethestructuralinformationbetweentwoentities. PCNNcandividetheoutputofthe
convolutionallayerintothreepartsbasedonthepositioninformationofthetwoentities,
whichcouldalsobethereasonwhyPCNNdemonstratedbetterperformance. Similarly,
ourmodelalsoincorporatesentitylocationinformation. Thedifferenceisthatourmethod
usesthepowerfulcodingcapabilitiesoftheBERTmodelandextractsboththesemantic
andgrammaticalfeaturesofthetext. OurmodelachievedthehighestaccuracywithF1,
achieving75.26%and80.39%,respectively.
Table6.Comparisonofexperimentalresultsofdifferentmethods.Weranallmodels20timesand
tooktheaverage.TheresultsindicatedstatisticalsignificancebasedonStudent’st-test(p<0.05).
| Method         | Acc    | P      | R      | F1     |
| -------------- | ------ | ------ | ------ | ------ |
| BiLSTM         | 64.94% | 67.49% | 81.68% | 73.91% |
| CNN            | 70.92% | 76.25% | 79.81% | 77.99% |
| PCNN           | 73.80% | 76.33% | 81.45% | 78.80% |
| Lexicon+R-BERT | 75.26% | 76.38% | 84.85% | 80.39% |
In order to avoid over-fitting during model training, we considered the dropout
parameters. Table 7 shows all the results of our model using different dropout values.
Finally,wechosethedropoutvalueof0.5.Theaboveexperimentsalsoprovetheimportance
ofentityinformationfortherelationextraction. Theyalsoshowthatusingspecialtags
tomarkentitiescaneffectivelyinputentitylocationinformationintotheBERTmodelfor
training. BERTcanobtainthegrammaticalandsemanticfeaturesofsentencestoclassify
relationsmoreaccurately. Toensurethequalityoftheknowledgegraphbuiltinthispaper,
thetrainedmodelisusedtoidentifytherelationshipintheunlabeleddata.
Table7. ComparisonofexperimentalresultsofLexicon+R-BERTmodelwithdifferentdropout
values.Weranallmodels20timesandtooktheaverage.Theresultsindicatedstatisticalsignificance
basedonStudent’st-test(p<0.05).
Dropout F1
| 0.1 |     |     | 79.14% |     |
| --- | --- | --- | ------ | --- |
| 0.3 |     |     | 79.87% |     |
| 0.5 |     |     | 80.39% |     |
| 0.7 |     |     | 79.92% |     |
| 0.9 |     |     | 78.67% |     |
4.4. VisualDisplayofKnowledgeGraph
The above experiments can be used to obtain the entities and relationships in the
multi-modaleducationalknowledgegraph.Inthepaper,theacquirededucationalconcepts
andrelationshipswerestoredintheNeo4jgraphdatabase(https://neo4j.com/)(accessed
on8February2022). UsingD3.js(https://d3js.org/)(accessedon8February2022)andthe
Vueframework(https://vuejs.org/)(accessedon8February2022),acoursemulti-modal
search system based on the knowledge graph was developed. The platform provides
retrievalservicesbasedonmulti-modalcurriculumknowledgegraphs,suchasknowledge
structure,learningsequence,andvoiceexplanations. Therearetwomainsystemfunctions:
acourseknowledgeconceptquerymoduleandamulti-modalconceptdisplaymodule.
4.4.1. CourseKnowledgeConceptQueryModule
The search results obtained when using the “双向链表” (double-linked list) as an
exampleareshowninFigure6. Thedouble-linkedlistwasusedasanentitytoexpand

Information2022,13,91 15of18
and display the attribute information and the entity nodes related to it. With the help
of the knowledge graph, the search no longer comprises of ordinary string matching,
however,insteaditconsistsofasemanticsearchthatisbasedontherelationshipinthe
graph. Thereturnedknowledgegraphcanbegenerateddynamicallybasedonthereturned
results,withnodesofdifferentcolorsrepresentingdifferententities. Thearrowsbetween
theentitiesrepresentwhethertherelationshipbetweenentitiesisaone-wayortwo-way
relationship. Learners can clearly understand the relationship between the knowledge
Information 2022, 13, x FOR PEER REVIEW 16 of 19
points. The“链表”(linkedlist)and“双向链表”(double-linkedlist)inthefigurerepresenta
Information 2022, 13, x FOR PEER REVIEW 16 of 19
one-waypredecessorrelationship,whichmeansthatthedouble-linkedlistmustbelearned
beforethelinkedlistknowledgepoints.
Figure 6. Course knowledge concept query module. Different colors represent different entity type.
Figure 6. Course knowledge concept query module. Different colors represent different entity type.
Figu T r h e e 6 a . r C ro o w u s r s b e et Tk w hn e eo e w n a rl e reo n dw ti g t s i e e s bc eo r t e nw p ce r e e ep s n e t n eq t n u t t h iet e riey s re m l r a eo t p i d o r n eus s le h en i . p tD t b ih e fef t e w rr e ee e lna n tt i t co h on e ls m ohr . i sp W rbe e ep t u rw s e e es ee t nn h e tt hd “ ei 双 fmf 向 e. rW链 en 表et eu ” n seti ttyhet y“p双e.向链表”
The(adroruobwles-lbinektwede (el d ins o t) ue anb s lte iat-il n ie nse k xre aed mp rl p ies lest . )e Anast ptaho n re t e iro xen al am otfip ot l hne. es Aheid pp u o cba ret t iti o own ne k oen fn o tth whe le e emd d g.u eWc g aer ti a oup nsh e k istnh o seh w o“l w 双ed n g向 o e n 链g t r h 表a e p ”h (ids osuhobwlen- on the
linkleedft,l aisntd) eanstiatyn pl e erx fot a ,p m aenrptdiel e es n .atrA iet ydp piosrpr oltap iyo eer ndti o eos fn a t th rhe ee d re iid sgphu lta c. y a e ti d o o n n k t n h o e w rig le h d t. g egraphisshownontheleft,and
entitypropertiesaredisplayedontheright.
4.4.2. Multi-M4o.d4.a2l. CMounlcteip-Mt Dodisapll aCyo Mncoedput lDe isplay Module
4.4.2. MFuilgtui-rMe 7o dshaolwCFsoig ntuhcreee p r7et sDsuhlitosspw flrsao ymthM ew orhedesnuu ll“tes广 f度ro优m先 w遍he历n” “ (广br度ea优dth先-f遍irs历t s”e a(brcrhe)a dwthas-f irst search) was
us
F
e
i
d
g u
a
r
s
e
a
7
n
s
e
h
xu
o
as
w
medp
s
l
t
ea
h
.s
e
Wa
r
nh
e
e
s
en
u
x
l
as
t
m
s
ea
f
pr
r
cl
o
eh
m
.i nWg
w
hf
h
oe
e
rn
n
tsh
“
eisa广 rcc度ohnin优cegp先 tf,o 遍rth t历eh is
”
se a
(
cr
b
oc
r
nh
e
c
a
er
d
eps
t
tu
h
, l
-
tt
f
hs
i
e
r
n
s
os
t
te
s
ao
e
rn
a
cl
r
hy
c h
rien
)
s-
w
ul
a
ts
s u
no
se
t
d
only in-
cluded text incflourdmedat itoenx,t biuntf oarlmsoa tvioonic,e beuxtp laalnsoat ivoonisc. eL eexarpnlaernsa tciaonn sh. eLaer atrhnee rtse accahne r’hse ar the teacher’s
as an example. When searching for this concept, the search results not only included
voice in the vcloaiscser oionm t,h we hcilcahs scroonofmor, mws htioc ht hceo nlefaorrnminsg t om othdee ltehaartn icnogll emgeo dsteu dthenatts college students
textinformation,butalsovoiceexplanations. Learnerscanheartheteacher’svoiceinthe
commonly encgoamgem ino.n ly engage in.
classroom,whichconformstothelearningmodethatcollegestudentscommonlyengagein.
Figure 7. Multi-modal concept display module. When learners query breadth first traversal, they
Figu c r a e n 7 n . oMt ounlltyi -smeFeo i tg dhu aer l etce ox7t. n eM cne utpiltt tiied -sm i sroepld laa atey l dc m oton o c diet,u p bl t e ud .t i W sthpeh laye y nc am lne o aad rlsu nol e e sr .e s Weq th uhe eenirr y lve boa rirce nea e d rms t oh qdu fiaelr r sky tn t bor rwa e vlaee ddr tgs hea ,f l i , r t s h t e tr y av ca e n rsal, they
notothnalty iss, etheetihr eteatcecaxhnet ren’sno vtti otoiinceelsy. r seelea ttehde ttoexitt ,ebnutittieths eryelactaend atols iot, sbeuet tthheeiyr cvaoni caelsmo osedea tlhkeniro vwoliceed gmeo,dtahla ktniso,wledge,
theirteacher’svotihcaet. is, their teacher’s voice.
5. Conclusions
In this w5o.r Ck,o wncel uprsoiopnosse d a method for automatically constructing a multi-modal
educational knowlIend gteh igsr awpohr.k I,t wexet rparcotsp tohsee dim ap lmieedt hteoadc hfionrg a cuotnocmepattsic aanlldy ecdouncsattriuocntainl g a multi-modal
relationships efrdoumc ahtieotneraolg kennoewoules ddgaet ag rsaopuhrc.e Ist, emxtorsatc otsf twheh iicmh pwlieerde toenalcihnein agn cdo nofcfelipntes and educational
relationships from heterogeneous data sources, most of which were online and offline

Information2022,13,91 16of18
5. Conclusions
Inthiswork,weproposedamethodforautomaticallyconstructingamulti-modal
educationalknowledgegraph. Itextractstheimpliedteachingconceptsandeducational
relationships from heterogeneous data sources, most of which were online and offline
real classroom teaching resources. While extracting the educational concepts, we also
proposetheintroductionofdomainknowledgeintoafine-tunedBERTmodelbymeansof
lexicalenhancement. Theeducationalrelationextractionmodulecombinesthelocation
informationoftheentitiesandBERTmodeltoexplorepotentialsemanticrelationships.
We utilized speech recognition and text matching technology to embed teacher audio
intotheconstructedtextknowledgegraph. Theexperimentalresultsshowthattheentity
recognition and relationship extraction precision have significant effects on our model.
Finally,themulti-modalknowledgegraphisconstructedandstoredintheneo4jdatabase,
whichcanbevisualizedbywebprogramming.
Inthefuture,wewillexplorewhethersuchamulti-modalgraphincorporatingspeech
ismoreeffectivethanonethatdoesnotincludeteacherspeech.Wewilltrytointegratemore
educationalresources,suchascourseexercisesandclassroomvideos,intotheknowledge
graph. Moreover,challengesrelatedtomulti-modalknowledgegraphs,includingnamed
entityrecognitiontask,willbelookedatinmoredetail. Finally,wewillfocusonlarge-scale
andhigh-qualitymulti-modaleducationknowledgegraphstoprovidebettereducational
servicesforbothteachersandlearners.
AuthorContributions:N.L.:Conceptualization,Methodology,Software,Datacuration,Writing—
Originaldraftpreparation,Writing—ReviewingandEditing;Q.S.:Visualization,Writing—Reviewing
andEditing;R.S.:Software,Validation;Y.C.:Investigation,Software;H.X.:Supervision.Allauthors
havereadandagreedtothepublishedversionofthemanuscript.
Funding:ThisresearchwasfundedbytheNationalNaturalScienceFoundationofChina(62077027),
theMinistryofScienceandTechnologyofthePeople’sRepublicofChina(2018YFC2002500),theJilin
ProvinceDevelopmentandReformCommission,China(2019C053-1),theEducationDepartmentof
JilinProvince,China(JJKH20200993K),theDepartmentofScienceandTechnologyofJilinProvince,
China(20200801002GH),andtheEuropeanUnion’sHorizon2020FETProactiveproject“WeNet-The
Internetofus”(No.823783).
InstitutionalReviewBoardStatement:Notapplicable.
InformedConsentStatement:Notapplicable.
DataAvailabilityStatement:Thedataunderlyingthisarticleareavailableinthearticle.
Acknowledgments: Theauthorswouldliketothankallofanonymousreviewersandeditorsfor
theirhelpfulsuggestionsfortheimprovementofthispaper.
ConflictsofInterest:Theauthorsdeclarenoconflictofinterest.
References
1. Martín,A.C.;Alario-Hoyos,C.;Kloos,C.D.SmartEducation:AReviewandFutureResearchDirections.Proceedings2019,31,57.
[CrossRef]
2. D’Mello, S.K.; Olney, A.M.; Blanchard, N.; Samei, B.; Sun, X.; Ward, B.; Kelly, S. Multimodal Capture of Teacher-Student
InteractionsforAutomatedDialogicAnalysisinLiveClassrooms. InICMI’15, Proceedingsofthe2015ACMonInternational
ConferenceonMultimodalInteraction;AssociationforComputingMachinery:NewYork,NY,USA,2015;pp.557–566.
3. Suresh, A.; Sumner, T.; Jacobs, J.; Foland, B.; Ward, W. Automating Analysis and Feedback to Improve Mathematics
Teachers’ Classroom Discourse. In Proceedings of the AAAI Conference on Artificial Intelligence, Honolulu, HI, USA,
27January–1February2019;2019;Volume33,pp.9721–9728.
4. Anand,R.;Ottmar,E.;Crouch,J.L.;Whitehill,J.TowardAutomatedClassroomObservation:PredictingPositiveandNegative
Climate.InProceedingsofthe201914thIEEEInternationalConferenceonAutomaticFace&GestureRecognition(FG2019),
Lille,France,14–18May2019;pp.1–8.
5. Heiko,P.TowardsProfilingKnowledgeGraphs.InProceedingsofthePROFILES@ISWC,Vienna,Austria,22October2017.
6. Wang,S.;Liang,C.;Wu,Z.;Williams,K.;Pursel,B.;Brautigam,B.;Saul,S.;Williams,H.;Bowen,K.;Giles,C.L.ConceptHierarchy
ExtractionfromTextbooks. InProceedingsoftheDocEng’15—ACMSymposiumonDocumentEngineering2015,Lusanne,
Switzerland,8–11September2015.

Information2022,13,91 17of18
7. Lu,W.;Zhou,Y.;Yu,J.;Jia,C.ConceptExtractionandPrerequisiteRelationLearningfromEducationalData.Proc.Conf.AAAI
Artif.Intell.2019,33,9678–9685.[CrossRef]
8. Hu, J.; Zheng, L.; Xu, B. An Approach of Ontology Based Knowledge Base Construction for Chinese K12 Education. In
Proceedingsofthe2016FirstInternationalConferenceonMultimediaandImageProcessing(ICMIP),BandarSeriBegawan,
Brunei,1–3June2016;pp.83–88.
9. Liu,H.;Ma,W.;Yang,Y.;Carbonell,J.G.LearningConceptGraphsfromOnlineEducationalData.J.Artif.Intell.Res.2016,55,
1059–1090.[CrossRef]
10. Chen,P.;Yu,L.;Zheng,V.W.;Chen,X.;Li,X.AnAutomaticKnowledgeGraphConstructionSystemforK-12Education. In
ProceedingsoftheFifthAnnualACMConferenceonLearningatScale2018,London,UK,26–28June2018.
11. Biega,J.A.;Kuzey,E.;Suchanek,F.M.InsideYAGO2s:ATransparentInformationExtractionArchitecture.InProceedingsofthe
22ndInternationalConferenceonWorldWideWeb—WWW’13Companion,RiodeJaneiro,Brazil,13–17May2013;pp.325–328.
12. Bizer,C.;Lehmann,J.;Kobilarov,G.;Auer,S.;Becker,C.;Cyganiak,R.;Hellmann,S.DBpedia—Acrystallizationpointforthe
WebofData.J.WebSemant.2009,7,154–165.[CrossRef]
13. Fredo, E.; Günther, M.; Krötzsch, M.; Mendez, J.; Vrandecˇic´, D. Introducing Wikidata to the Linked Data Web; Springer:
Berlin/Heidelberg,Germany,2014.
14. Liu,S.;Yang,H.;Li,J.;Kolmanicˇ,S.PreliminaryStudyontheKnowledgeGraphConstructionofChineseAncientHistoryand
Culture.Information2020,11,186.[CrossRef]
15. Su,Y.;Zhang,Y.AutomaticConstructionofSubjectKnowledgeGraphbasedonEducationalBigData. InProceedingsofthe
ICBDE’20—3rdInternationalConferenceonBigDataandEducation,London,UK,1–3April2020.
16. Yang,Y.;Liu,H.;Carbonell,J.G.;Ma,W.ConceptGraphLearningfromEducationalData.InProceedingsoftheEighthACM
InternationalConferenceonWebSearchandDataMining,Shanghai,China,2–6February2015.
17. Senthilkumar,R.D.ConceptMapsinTeachingPhysicsConceptsAppliedtoEngineeringEducation:AnExplorativeStudyatThe
MiddleEastCollege,SultanateofOman.InProceedingsofthe2017IEEEGlobalEngineeringEducationConference,EDUCON
2017,Athens,Greece,25–28April2017;pp.107–110.
18. Chen,L.;Ye,L.;Wu,Z.;Pursel,B.;Lee,C.G.RecoveringConceptPrerequisiteRelationsfromUniversityCourseDependencies.
Proc.AAAIConf.Artif.Intell.2017,31,10550.
19. Kai,S.;Liu,Y.;Guo,Z.;Wang,C.VisualizationforKnowledgeGraphBasedonEducationData.Int.J.Softw.Inform.2017,10,3.
20. Zheng,Y.;Liu,R.;Hou,J.TheConstructionofHighEducationalKnowledgeGraphBasedonMOOC.InProceedingsofthe2017
IEEE2ndInformationTechnology,Networking,ElectronicandAutomationControlConference,ITNEC,Chengdu,China,15–17
December2017;pp.260–263.
21. Dang,F.;Tang,J.-T.;Pang,K.;Wang,T.;Li,S.;Li,X.ConstructinganEducationalKnowledgeGraphwithConceptsLinkedto
Wikipedia.J.Comput.Sci.Technol.2021,36,1200–1211.[CrossRef]
22. Yao, S.; Wang, R.; Sun, S.; Bu, D.; Liu, J. Joint Embedding Learning of Educational Knowledge Graphs. arXiv 2019,
arXiv:1911.08776.
23. Lample, G.; Ballesteros, M.; Subramanian, S.; Kawakami, K.; Dyer, C.NeuralArchitecturesforNamedEntityRecognition.
NAACL.arXiv2016,arXiv:1603.01360.
24. Yadav,V.;Bethard,S.ASurveyonRecentAdvancesinNamedEntityRecognitionfromDeepLearningmodels. arXiv2018,
arXiv:1910.11470.
25. Nadeau,D.;Sekine,S.ASurveyofNamedEntityRecognitionandClassification.Lingvist.Investig.2007,30,3–26.[CrossRef]
26. Fu,G.;Kit,C.;Webster,J.J.AMorpheme-basedLexicalChunkingSystemforChinese.Int.Conf.Mach.Learn.Cybern.2008,5,
2455–2460.
27. Wang,Y.;Wang,L.;Rastegar-Mojarad,M.;Moon,S.;Shen,F.;Afzal,N.;Liu,S.;Zeng,Y.;Mehrabi,S.;Sohn,S.;etal. Clinical
informationextractionapplications:Aliteraturereview.J.Biomed.Inform.2018,77,34–49.[CrossRef]
28. Sutton,C.;McCallum,A.AnIntroductiontoConditionalRandomFields.Found.TrendsMach.Learn.2012,4,267–373.[CrossRef]
29. Collobert,R.;Weston,J.;Bottou,L.;Karlen,M.;Kavukcuoglu,K.;Kuksa,P.P.NaturalLanguageProcessing(Almost)fromScratch.
J.Mach.Learn.Res.2011,12,2493–2537.
30. Zhiheng,H.;Xu,W.;Yu,K.BidirectionalLSTM-CRFModelsforSequenceTagging.arXiv2015,arXiv:1508.01991.
31. Yann,D.;Fan,A.;Auli,M.;Grangier,D.LanguageModelingwithGatedConvolutionalNetworks.Proc.Mach.Learn.Res.2017,
70,933–941.
32. Hang, Y.; Deng, B.; Li, X.; Qiu, X. TENER: Adapting Transformer Encoder for Named Entity Recognition. arXiv 2019,
arXiv:1911.04474.
33. Hui,C.;Lin,Z.;Ding,G.;Lou,J.-G.;Zhang,Y.;Börje,F.K.GRN:GatedRelationNetworktoEnhanceConvolutionalNeural
NetworkforNamedEntityRecognition.arXiv2019,arXiv:1907.05611.
34. Zhu,Y.;Wang,G.;Börje,F.K.CAN-NER:ConvolutionalAttentionNetworkforChineseNamedEntityRecognition.arXiv2019,
arXiv:1904.02141.
35. Peters,M.E.;Neumann,M.;Iyyer,M.;Gardner,M.;Clark,C.;Lee,K.;Zettlemoyer,L.DeepContextualizedWordRepresentations.
NAACL.arXiv2018,arXiv:1802.05365.
36. Radford,A.;Karthik,N.ImprovingLanguageUnderstandingbyGenerativePre-Training;OpenAI:SanFrancisco,CA,USA,2018.

Information2022,13,91 18of18
37. Devlin,J.;Chang,M.-W.;Lee,K.;Toutanova,K.BERT:Pre-trainingofDeepBidirectionalTransformersforLanguageUnderstand-
ing.arXiv2019,arXiv:1810.04805.
38. Aydar,M.;Ozge,B.;Özbay,F.NeuralRelationExtraction:ASurvey.arXiv2020,arXiv:2007.04247.
39. Vu,N.T.;Adel,H.;Gupta,P.;Schütze,H.CombiningRecurrentandConvolutionalNeuralNetworksforRelationClassification.
InProceedingsofthe2016ConferenceoftheNorthAmericanChapteroftheAssociationforComputationalLinguistics:HumanLanguage
Technologies;AssociationforComputationalLinguistics:SanDiego,CA,USA,2016.[CrossRef]
40. He,H.;Ganjam,K.;Jain,N.;Lundin,J.;White,R.;Lin,J.AnInsightExtractionSystemonBioMedicalLiteraturewithDeepNeural
Networks.InProceedingsofthe2017ConferenceonEmpiricalMethodsinNaturalLanguageProcessing;AssociationforComputational
Linguistics:Copenhagen,Denmark,2017.[CrossRef]
41. Zeng,D.;Liu,K.;Chen,Y.;Zhao,J.DistantSupervisionforRelationExtractionviaPiecewiseConvolutionalNeuralNetworks;EMNLP:
Lisbon,Portugal,2015.
42. Zhang,S.;Zheng,D.;Hu,X.;Yang,M.BidirectionalLongShort-TermMemoryNetworksforRelationClassification;FujitsuResearch
andDevelopmentCenter:Beijing,China,2015.
43. Scarselli,F.;Gori,M.;Tsoi,A.C.;Hagenbuchner,M.;Monfardini,G.TheGraphNeuralNetworkModel.IEEETrans.NeuralNetw.
2009,20,61–80.[CrossRef]
44. Zhang,Y.;Qi,P.;Manning,C.D.GraphConvolutionoverPrunedDependencyTreesImprovesRelationExtraction.arXiv2018,
arXiv:1809.10185.
45. Guo, Z.; Zhang, Y.; Lu, W. Attention Guided Graph Convolutional Networks for Relation Extraction. arXiv 2019,
arXiv:abs/1906.07510.
46. Fu,T.-J.;Li,P.-H.;Ma,W.-Y.GraphRel:ModelingTextasRelationalGraphsforJointEntityandRelationExtraction;Associationfor
ComputationalLinguistics:Florence,Italy,2019.
47. Wu, S.; He, Y. Enriching Pre-trained Language Model with Entity Information for Relation Classification. arXiv 2019,
arXiv:1905.08284.
48. Li,C.;Ye,T.DownstreamModelDesignofPre-trainedLanguageModelforRelationExtractionTask.arXiv2020,arXiv:2004.03786.
49. Mikolov, T.; Chen, K.; Corrado, G.S.; Dean, J. Efficient Estimation of Word Representations in Vector Space. arXiv 2013,
arXiv:1301.3781.