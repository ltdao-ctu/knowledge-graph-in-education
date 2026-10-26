---
title: "AbuRasheed2025assisted"
source: "AbuRasheed2025assisted.pdf"
source_sha256: "0db8c0a307800d871258774eaf10e62243f027a3205abc9f9c74e2140c373feb"
converted_at: "2026-10-26T07:04:52.635104+00:00"
markitdown_version: "0.1.9"
---
LLM-Assisted Knowledge Graph Completion for
Curriculum and Domain Modelling in Personalized Higher
Education Recommendations
HasanAbu-Rasheed1,*, ConstanceJumbo2, RashedAlAmin2, ChristianWeber1,3,
VeitWiese2, RomanObermaisser2 and MadjidFathi1
1InstituteforKnowledge-BasedSystemsandKnowledgeManagement,UniversityofSiegen,Siegen,Germany
2InstituteforEmbeddedSystems,UniversityofSiegen,Siegen,Germany
3DepartmentofDigitalHealthSciencesandBiomedicine,UniversityofSiegen,Siegen,Germany
Abstract
Whilelearningpersonalizationoffersgreatpotentialforlearners,modernpracticesinhighereducationrequirea
deeperconsiderationofdomainmodelsandlearningcontexts,todevelopeffectivepersonalizationalgorithms.This
paperintroducesaninnovativeapproachtohighereducationcurriculummodellingthatutilizeslargelanguage
models(LLMs)forknowledgegraph(KG)completion, withthegoalofcreatingpersonalizedlearning-path
recommendations.Ourresearchfocusesonmodellinguniversitysubjectsandlinkingtheirtopicstocorresponding
domainmodels,enablingtheintegrationoflearningmodulesfromdifferentfacultiesandinstitutionsinthe
student’slearningpath.Centraltoourapproachisacollaborativeprocess,whereLLMsassisthumanexpertsin
extractinghigh-quality,fine-grainedtopicsfromlecturematerials.Wedevelopadomain,curriculum,anduser
modelsforuniversitymodulesandstakeholders. WeimplementthismodeltocreatetheKGfromtwostudy
modules:EmbeddedSystemsandDevelopmentofEmbeddedSystemsUsingFPGA.TheresultingKGstructures
thecurriculumandlinksittothedomainmodels.Weevaluateourapproachthroughqualitativeexpertfeedback
andquantitativegraphqualitymetrics.Domainexpertsvalidatedtherelevanceandaccuracyofthemodel,while
thegraphqualitymetricsmeasuredthestructuralpropertiesofourKG.OurresultsshowthattheLLM-assisted
graphcompletionapproachenhancestheabilitytoconnectrelatedcoursesacrossdisciplinestopersonalizethe
learningexperience.Expertfeedbackalsoshowedhighacceptanceoftheproposedcollaborativeapproachfor
conceptextractionandclassification.
Keywords
Highereducation,Knowledgegraph(KG),Largelanguagemodels(LLM),curriculummodel,domainmodel,
Recommendersystems
1. Introduction
Highereducationisastructuredlearningsetting,wherecurriculumsaredesignedtomeetpredefined
learning goals for each study program. This leaves a small margin to meet the individual goals of
differentstudentsinthesameprogram,especiallyinprogramswherestudentshavedifferentstudy
backgrounds,orcomefromvariouscountries,suchasinternationalstudyprograms. Inthesescenarios,
thelikelihoodofastudentrepeatingacourseoratopictheyalreadystudiedbeforebecomeshigher. In
ordertoincreasetheefficiencyofthefulllearningpaththatastudenttakeswithintheirstudy,itis
essentialtoconsidertheirlevelofknowledge,thecoursesandmodulestheyalreadystudied,aswellas
theircareerandprofessionalgoals,totailortheirlearningpathtothoseindividualneeds,goals,and
requirements.
However,thelearningsettinginhighereducationposesseveralchallengestoaccomplishingthis
personalization. Ontheonehand,teachersareoccupiedwithmanytasks[1]andlacksufficienttimeto
analyzethebackgroundknowledgeofindividualstudents,aswellastoanalyzethecontentofother
coursesintheuniversity,whichmightbeusedtoconstructapersonalizedlearningpath. Ontheother
hand,thereisalackofstandardrepresentationofthecoursesandstudymodulesindifferentstudy
AcceptedintheIEEEGlobalEngineeringEducationConference(EDUCON2025),London,UK,22-25April,2025
*Correspondingauthor.
$hasan.abu.rasheed@uni-siegen.de(H.Abu-Rasheed)
©2025Copyrightforthispaperbyitsauthors.UsepermittedunderCreativeCommonsLicenseAttribution4.0International(CCBY4.0).
5202
naJ
12
]CH.sc[
1v00321.1052:viXra

programs, sometimes even inside the same university. To enhance the interoperability of different
studyprograms,andthusthepotentialtocreateanefficientlearning-pathrecommendation,weaimin
thisresearchtoprovideafoundationforcreatingacomprehensiveandhomogenicpooloflearning
materials,throughaflexibleandsufficiently-detailedrepresentationofcurriculumsinhighereducation.
Weproposeahuman-AIcollaborationapproachtosupportteacherswithintelligent,LLM-assisted
algorithmsthatextractandanalyzetheireducationalmaterials. Automaticextractionisthenevaluated
and controlled by the human teacher to ensure its high-quality. To ensure the comparability of the
learningmaterialsamongstdifferentstudyprogramsanddifferentuniversities,weproposeanonto-
logicalfoundationthatisdesignedspecificallyforhighereducation,coveringthecurriculummodel,
domainmodel,andstudentmodel. Ourmainresearchquestionsinthispaperaretherefore:
1. How to develop a higher-education ecosystem, where LLM supports teachers in creating a
knowledgegraphforhighereducation?
2. Whatarethesufficientclassesofahighereducationontology,tointegratedomain,curriculum,
andusermodels?
To answer those questions, we developed the collaboration process based on a KG, which serves
as the network data structure that represents the three models and their educational content. The
KGalsoformsthehomogeneousdatabasethatallowsarecommendersystemtofindandrecommend
personalizelearningpaths.
2. Background
The recent developments of LLMs opened several doors to support teachers and experts in a faster
extractionandanalysisofthewiderangeofeducationalcontent,whetheronlineorwithinuniversities
andhighereducationinstitutions. Inthefollowing,wehighlightsomeofthesystemsandapproaches
thathavesimilargoalstoourresearch.
2.1. LLMsSupportinCreatingKGs
LLMs are powerful tools for generating and enhancing KGs [2]. They are designed to understand
andgeneratenaturallanguageandarecapableofawiderangeofnaturallanguageprocessingtasks
[3]. In the context of KGs, LLMs enhance KG embedding, completion, and construction, as well as
supportingtextgenerationandquestion-answeringtasks[4]. KGsarevaluablemeansforrepresenting
theinterconnectednatureofinformation,especiallyineducationalsettings[5]. Theyserveasasolid
datastructurefororganizingandstoringknowledge[6]. Kommineni’sstudyshowsthatintegrating
LLMsintoKGcreationcanenhanceentityrecognitionandrelationshipextractionstreamliningKG
creation[7]. Thisisanessentialtoolinhighereducationwherevastinformationmustbeorganized
cohesively.
2.2. LLM-EnhancedKGCreationforHigherEducation
EnhancingKGcreationusingLLMsinhighereducationintroducesarobustmethodformodellingcourse
contentandstructure[8]. ThetraditionalprocessofconstructingKGsislargelydependentonhuman
expertsandthishasproventobemorecomplexwhenconstructinglarge-scaleandhigh-qualityKGsin
domainsthatevolveconstantly[1]. Jhajj[8]investigatedtheuseofLLMincreatingandenhancing
educationalknowledgegraphsbyanalyzingthreeKGs. Thehumanevaluatorsratedthegraphcreated
fromLLMandcontextualdata(coursesyllabus)higherregardingitsrelevanceandeducationalvalue.
Togetherwithcourse-specificinformation,LLMcanextractinformationandgeneratenodesthathave
highsemanticsimilaritywithcoursematerialsenablingamoreefficientsemi-automatedKGcreation
processinhighereducation. ThefusionofKGandLLMsissynergistic,particularlyinhighereducation.
KGscanbeusedasfactualcontextsourcesforLLMpromptstoenhancelearningrecommendations
[9]. Evaluating the approach both qualitatively and quantitatively, results showed improvement in

the quality of the generated text. Despite these use cases, LLM support for KG creation in higher
educationremainsunder-explored,particularlyincomprehensivemulti-dimensionalmodels,linking
users,curriculums,anddomainelements.
2.3. AComprehensiveOntologyforHigherEducation
Ontologiesareformalrepresentationsofdata,whichinourusecaseprovideaholisticviewofhigher
education requirements, incorporating curriculum, user, and domain models. Recently, ontologies
havebeencommonlyusedinhighereducation[10]. However,traditionalontologiesfocusonuserand
educationalmodels[11],whichrepresentthesubjectmatterwithintheeducationalenvironment. This
underscorestheneedforprovidingadetailedandcomprehensiverepresentationofrelevantknowledge
andconceptsinreal-worlddomains. Includingadomainmodelprovidescontextualdepth,whichis
importantforrecommendingcoursesthatalignwithuserbackgrounds,goals,andcareerorientations.
LLM-supportforcurriculumanddomainmodellingoffersasolidfoundationforpersonalizedlearning
recommendationsinhighereducation.
3. Methodology
Toaccomplishcreatingagraphdatastructureformodellingcontentinhighereducationandsupporting
teacherstorepresenttheirexistingmaterialsinthismodel,weproposeafour-stepimplementation
strategy: Graphontologydefinition,automatedtopicextraction,human-AIcollaborationforvalidation
task,andKGconstruction.
3.1. DefiningaHigherEducationOntology
To develop a graph structure that accommodates learning content from different study programs
anduniversities,wedevelopedthecontentrepresentationmodelsasinteroperableones. Thismeant
selecting ontological classes that apply to a wider range of course structures, enabling teachers to
adapttheirlearningcontenttothatmodeleasily. Tothatend,weselecttheclass“Topic”asthecore
taxonomicalelementthatisusedtobreakdownthecontentofeachsessionwithinthestudymodule,
seeFigure1Astopicsinthelearningcontentdifferintheirlevelofdetail,weadda“Sub-Topic”classto
accountformoregranularityintheeducationalcontent. Inthissense,aTopicisdefinedasanabstract
concept,whichisbeingtaughtinthelearningsession,whileaSub-Topicisdefinedasthefine-grained
content, which is described through a tangible means, such as lecture slides. A Session is then the
iterativeinstanceofaLecture, whichtakesplace, e.g., onaweeklybasis. Theproposedontologyis
composedofthreemodels:
1. Thecurriculummodel: whichincludestheclassesrepresentingeducationalcontentasdefinedby
theuniversity.
2. Thedomainmodel: whichisusedtomodelahigherabstractionlevelofthedomainofknowledge.
Thedomainmodelincludesdomainstowhichthelearningcontentbelongs,suchasAutomotive,
EmbeddedSystems,orCommunicationdomains. Ineachdomain,moregranularconceptsare
representedasSub-Domains,suchasSelf-DrivingCarsbeingasub-domainoftheAutomotive
domain.
3. Theusermodel: whichismeanttorepresentthestakeholdersintheeducationalsetting,focusing
on students and the factors that can be used for learning personalization. These include the
backgroundknowledge,learninggoals,preferences,aswellasacademicparameters,asadopted
from[12],whichrepresentallotheracademicaspectsrelatedtothestudent’slearningprocess,
suchastheirexamperformance.

Figure1:Proposedontologicalstructureoftheknowledgegraph,withdomain,curriculum,andusermodels.
3.2. AutomaticContentExtractionandClassification
Inorderforteacherstoclassifythecontentoftheirlecturesintotopicsandsub-topics,agreatamount
oftimeandeffortneedstobeinvested,whichisrarelyavailableforteachersduetotheirbusyschedules.
Therefore,wedevelopedanautomatedextractionandclassificationpipeline,tosupportteacherswith
thistaskandconsiderablyreducethetimeandeffortrequirementsontheirside.
Thepipeline,seeFigure2,beginswiththeextractionoftextualcontentfromthelearningmaterials,
includinglectureslides,manuscripts,andlecturevideorecordings. Whiletheextractionofthetextual
datafromlectureslidesandmanuscriptsisrelativelystraightforward,theextractionofthetextfrom
lecturevideosrequirestranscribingthesevideos.Here,weassumethatthefigures,images,andequations
intheslidesareannotatedordescribedtextually. Weconductthistranscriptionautomaticallyutilizing
theadvancedcapabilitiesofOpenAI’sWhispermodel[13],whichisaspeechrecognitionmodelwith
highaccuracyinzero-shotrecognitiontasks. Videotranscriptsarethenfed,alongsidetheothertextual
contentmaterialstoanLLMforthetopicextractionandclassificationtasks.
Inthetopicextractionstep,weutilizeOpenAI’sGPT-4omodel. TheLLMispromptedtoextractthe
mainconceptsthateachsessionincludes. Aconceptrepresentshereakeytopicthatisbeingtaughtin
thesession. Extractedconceptsarethenclassifiedintotopicsandsub-topicsbasedonthedefinitionsof
thesetwoclassesinourontology. AtopicisdefinedintheLLMpromptasanabstractconcept,which
is taught within the session. A sub-topic is defined as the concept that is being explained, in detail,
throughlearningmaterials(e.g. lectureslides). TheLLMisalsoinstructedtoconsiderthehierarchical
structure of the two classes, where each topic includes one or more sub-topics. A topic is then an
overarchingconcept,whosesub-topicsaretheactualcontentofthelecture. Itisimportanttopointout

Figure2:Pipelinecomponentsforthetranscription,extraction,classification,andKGconstruction,basedona
human-AIcollaborativeapproach.
herethatthisontology-basedcontextualizationoftheLLMpromptisimperativetoextractanaccurate
representationofthelearningcontent,ensureasufficientlevelofinteroperability,andenablefinding
meaningfulsimilaritiesbetweenthetopicsandsub-topicsamonglecturesfromdifferentprogramsor
universities.
Inadditiontothetopicsandsub-topics,thedetailedcontentoflectureslidesandvideosprovidesa
solidsourceforgeneratinghigh-qualitydescriptions,especiallyonthesub-topiclevel,sinceitisthe
conceptexplainedindetailinthesession. Weusethosedescriptions, inadditiontothetitlesofthe
topicsandsub-topics,tosearchforsemanticsimilaritiesbetweendifferentstudyprograms.
3.3. HumanValidationoftheAutomatedExtraction
TherisksofLLMsinautomaticextraction,classification,andgenerationtasks,arehighinasensitive
fieldlikeeducation. Therefore,weensurethehigh-qualityoftopicextractionandclassificationthrough
ahuman-in-the-loopapproach,inwhichteachersvalidatethepredictionsoftheintelligentalgorithm,
andmakethefinaldecisiononextractedconceptsandtheirclassificationastopicsorsub-topics. The
preliminaryextractionandclassificationbytheLLMserveshereasanadvancedstartingpointforthe
teachersandhumanevaluators,whichsavesthemaconsiderableamountoftimewhenanalyzingthe
educationalcontent. Thisalsoappliestotheautomateddescriptionsoftopicsandsub-topics,sincethe
phrasingofthedescriptionisbasedonthesessioncontentitselfandnotthegeneralknowledgeofthe
model,i.e.,initstrainingdata. Thefinaldecisiononthetopics,sub-topics,andtheirdescriptionsismade
bytheteachersthemselves,toensureahigh-qualitycontentcurationoftheKG,whichisnecessary
to enable generating high-quality learning-path recommendations for the students. The role of the

teachersinoursystemisnotlimitedtovalidatingthelastpredictionoftheintelligentmodels. Teachers
arealsointegratedinthecontextualizationoftheLLMpromptsbyprovidinginputonthedefinitions,
limitations,andrulesthatthemodelshouldconsiderwhenanalyzing,extracting,andclassifyingthe
topicsoftheirlearningmaterials. Anexampleofthosedefinitionsisthespecificmeaningofterminology
thatisusedinthelecture,whichmaydiffer,slightlyorconsiderably,amongdifferentdomains.
3.4. KnowledgeGraphConstruction
Based on the validated content from the teachers, the KG construction process is then conducted
throughtwosteps:
1. Creatinggraphnodes: accordingtothebaseontology,andpopulatingthemwiththedatafrom
thelearningcontent,domain,andusers.
2. Creatinggraphrelations: whichisconductedontwolevels: thehierarchicalstructurefromthe
baseontology,andthesemanticsimilaritybetweenthetopicsandsub-topicsofdifferentlectures.
Tocalculatethesemanticsimilarities,wefirstbuildonthenaturallanguageprocessingpipelinein[5],
wherethetitleanddescriptionpropertiesofthelearningcontentareutilizedtofindsimilarcontent.
Thisapproachfitsourextractionprocessofthetopics,sub-topics,andtheirdescriptions. Secondly,we
utilizetheLLMitselftoanalyzetheextractedcontentandsearchforsimilarcontentfromotherlectures.
We use a semi-supervised approach for the validation of semantic similarities, where the human
teacher validates a random sample of the predicted relations in the KG. This approach is adopted
due to the large amount of semantic relations that can be identified when the KG grows to include
large-scaleeducationalcontent. Throughteachervalidation,hintsarecollectedtoadjusttheparameters
andpromptsoftherelationextractionpipelineandtheLLM,respectively,sustainingthecollaborative
approachinouroverallsolution.
Once the KG is constructed, it also becomes a source of data that is fed to the LLM, to provide
contextualinformationfortheextractionandclassificationtasks. Wefoundthismethodparticularly
effectivewhenthetopicextractionandclassificationaredonetoalecturethatiscontextuallysimilarto
theexistingcontentoftheKG,suchastopicsfromthesamedomain,orthesamefieldofapplication.
4. Evaluation and Results
Toevaluatetheproposedpipeline,weconstructtheknowledgegraphfromthecontentoftwouniversity
modules,namelyEmbeddedSystemsandDevelopmentofEmbeddedSystemsUsingFPGA.Thetwo
coursesaretaughtintheUniversityofSiegen,Germany,formaster-andbachelor-levelstudents. These
courseswerechosenbecausetheyaretaughtseparately,despitethepotentialoverlapbetweenthem.
Eachcourseiscomposedof9sessions,spanningthelectureperiodofoneacademicsemester. Each
weeklysessioncoversadiversenumberoftopics,whichdifferintheirlevelofdetail.
4.1. ExpertEvaluationoftheOntologyandPipeline
We conduct the evaluation with module lecturers, to ensure high-quality feedback based on their
experiencewiththemodule’scontentandlearninggoals. Evaluatorsincludedoneprofessorandtwo
PhDassistants,workingintheEmbeddedSystemsInstituteinthesameuniversity.Wecollectqualitative
feedbackfromthelecturersaboutthebaseontology,andtheoverallacceptanceofourapproachfor
human-AIcollaboration. Feedbackiscollectedthroughgroupmeetingswiththelecturers,inwhichthe
ontologywaspresentedandevaluatedfromtheperspectiveofusecasestheyfaceintheirteaching.
Moreover,wecollectquantitativeinputfromthelecturersregardingtheaccuracyofextractionand
classificationoftopics,sub-topics,anddescriptionsthroughthepipeline. Toachievethisquantitative
feedback, each lecturer checked a comprehensive list of extracted topics, their sub-topics, and the
sub-topicdescriptions,andevaluatedthefollowingforeachsample:
1. Thecorrectnessofextraction.

Table1
TABLEI.PRECISION(P),RECALL(R),ANDF1MEASUREVALUESFORTOPICSANDSUB-TOPICSOFTHE
EVALUATIONMODULES.
Topic Sub-Topic Description
P R F1 P R F1 P
ESa 0,99 0,94 0,96 1 0,97 0,98 1
FPGA 0,97 1 0,98 0,89 0,99 0,94 0,89
2. Thehierarchicalallocationofsub-topicswithinthetopic.
Lecturersalsoevaluatedthestructuralextractionandverifiedwhethertheextractedsub-topicswere
correctlypositionedwithinthecorrespondingtopics. Atotalof1197extractionsampleswereevaluated
by the experts (173 Topics, 512 Sub-Topics, and 512 Descriptions). Table 1 shows the results of the
Precision,Recall,andF1measureforTopicandSub-Topicclassesinbothevaluationmodules. Forthe
Descriptionclass,wecalculatethePrecisionvaluetoverifywhetherthelongdescriptiontextthatwas
generatedautomaticallyfitsthecorrespondingsub-topic.
The proposed pipeline and LLM-supported extraction of topics and sub-topics has shown a high
capability of detecting the topics and their corresponding sub-topics from the lecture materials. A
slightdifferencecanbenoticedbetweenthetwomodules,whichwetracebacktothelevelandstyleof
structuringthateachlecturerusestoorganizetheirlecturerecordings. Whilesomerecordingsonly
includedthelecturer’sexplanationofthesession’scontent,otherrecordingsweresimplymadeofthe
live,onlinesession,includingthediscussionswithstudents,theirquestions,andthelecturer’sanswers.
Thedifferencebetweenthesetwoapproacheshadaconsiderableinfluenceontheconceptextraction
fromtranscribedvideosinthefirstiterationofLLMextractionandclassification. Themodelextracted
conceptsfromthesidediscussions,questions,andanswers,aswellasfromthelecturer’shighlights
abouttopicsthatwillbecoveredinthecourse. Thosetopics,however,werenotinfactdiscussedinthe
correspondingsession. Toaccountforthiseffect,wefollowedapromptengineeringapproachtoset
explicitrulesandlimitationsforthewayeachvideotranscriptishandled. Thepromptengineering
processalsodefinedtheontologyclassestotheLLM,toclarifythecontextualmeaningoftheTopicand
Sub-Topicclasses.
Itisimportanttohighlightherethatthedifferencesamonglecturersinthewaystheyrecordtheir
lecturesarevast,andthereforecannotbeonlyaccountedforinthepromptengineeringsteps. Tothat
end,diversifyingtheinputofthemodel,e.g.,bysupportingthevideotranscriptionswithstructured
lectureslidesorreferences,willbeimportanttoensureagoodqualityextraction. Moreover,theKG
itself can play the role of a supporting data source, e.g., in a retrieval augmented generation (RAG)
approach,toextendthecontextoftheLLM’spromptandincreasetherelevanceandaccuracyofthe
extractionandclassificationtasks.
4.2. KG-StructuralEvaluation
Toevaluatetheresultingknowledgegraphstructure,weusethegraphqualitymeasures:AverageDegree
Centrality(ADC),andGraphModularity. Thesemeasuresvalidateourresearchgoalofdiscovering
connectionsbetweenlearningcontentsfrommultiplemodules. Averagedegreecentralityevaluates
theconnectednessofagraphnodethroughitsincomingandoutgoingrelations. Inourusecase,ADC
highlightstherolethatthesemanticsimilarityalgorithmplaysinincreasingthedensityofrelations
amonggraphnodes. Graphmodularity,ontheotherhand,evaluatesthepotentialtoseparatelearning
contentsinthegraphfromeachother. Therefore,alowermodularityscoreispreferredinourcase,
sinceitreflectsstrongerconnectionsbetweensimilarcontents.
In the resulting KG, see Figure 3, we calculate an increase of the ADC value from 0.9 to 1.03, as
wellasaslightmodularitydecreasefrom0.769to0.767. Thisslightchangecanbetracedbacktothe
smallnumberofsemanticrelationsaddedbetweenthetwomodules,duetotherelativelysmallsizeof
thesampledata. Moreover,thisisalsoaresultofthehighsimilaritythresholdsthatwehavesetfor

Figure3:ThestructureoftheKGbefore(left)andafter(right)connectingbothevaluationmodulesthrough
semanticTopicandSub-Topicrelations.
the semantic relation extraction algorithm, to ensure high-quality relations between the topics and
sub-topics.
DespitethisrelativelysmallimprovementontheKGstructurally,qualitativeexpertfeedbackpointed
outthattheautomatictopicextractionandthepossibilitytosemanticallyconnecttopicsfromdifferent
coursesisaconsiderablehelpforthelecturersinre-structuringtheircoursecontents. Thisisaccom-
plishedbybeingawareofsimilarcontentinothercoursesandmodules,whichmightbeoverlapping,
orcanbere-used. Theevaluatorspointedoutthattheinsightstheyreceivedfromthepipeline’soutput
didnotonlysupportabetterstructuringoftheircoursesandmodules,butalsothepersonalization
ofthelearningexperienceforindividualstudents,whohavedifferentlevelsofknowledge,scientific
backgrounds,andcareergoals.
5. Conclusion
Inthispaper,weproposedanapproachformodellinghighereducationcurriculumsandlinkingthem
todomainandusermodels. WeuseanLLM-assistedpipelinetoconductaKGcompletiontask,whichis
accomplishedthroughacollaborationbetweentheintelligentmodelanddomainexperts. Ourgoalwas
toenableaseamlessintegrationoftheexistinglearningcontentintothecurriculummodel,tosupport
learningpersonalizationbasedontheKG.
Weimplementedourpipelineonasampleoftwouniversitymoduleswithinembeddedsystemsand
FPGAcourses. Theproposedbaseontology,pipeline,andtheextractionandclassificationmodelswere
evaluatedwiththelecturersoftheselectedevaluationmodules. Ourevaluationresultsshowedthe
effectivenessoftheproposedapproachforthecollaborationbetweenhumanexpertsandtheAIsystem.
Itservedasanassistant,providingthehumanexpertwithanadvancedstartingpointforthestructuring
ofthelearningcontent,andforenablingbetterpersonalizationofthelearningexperience,considering
thesimilaritiesbetweenmodulecontentsandtheirconnectiontothedomainandusermodels.

References
[1] R.Meissner,L.Köbis, AnnotatedKnowledgeGraphsforTeachinginHigherEducation:Supporting
MentorsandMenteesbyDigitalSystems, in: M.Bielikova,T.Mikkonen,C.Pautasso(Eds.),Web
Engineering,volume12128,SpringerInternationalPublishing,Cham,2020,pp.551–555.URL:http:
| //link.springer.com/10.1007/978-3-030-50578-3_43.doi: |     |     |     |     | ,se- |
| ----------------------------------------------------- | --- | --- | --- | --- | ---- |
10.1007/978-3-030-50578-3_43
| riesTitle: LectureNotesinComputerScience. |     |     |     |     |     |
| ----------------------------------------- | --- | --- | --- | --- | --- |
[2] N.Ibrahim,S.Aboulela,A.Ibrahim,R.Kashef, Asurveyonaugmentingknowledgegraphs(KGs)
withlargelanguagemodels(LLMs): models,evaluationmetrics,benchmarks,andchallenges, Dis-
coverArtificialIntelligence4(2024)76.URL:https://link.springer.com/10.1007/s44163-024-00175-8.
| doi: 10.1007/s44163-024-00175-8 |     | .   |     |     |     |
| ------------------------------- | --- | --- | --- | --- | --- |
[3] H.Naveed,A.U.Khan,S.Qiu,M.Saqib,S.Anwar,M.Usman,N.Akhtar,N.Barnes,A.Mian,A
ComprehensiveOverviewofLargeLanguageModels,2023.URL:https://arxiv.org/abs/2307.06435.
| doi: |     | ,versionNumber: | 10. |     |     |
| ---- | --- | --------------- | --- | --- | --- |
10.48550/ARXIV.2307.06435
[4] S.Pan,L.Luo,Y.Wang,C.Chen,J.Wang,X.Wu, UnifyingLargeLanguageModelsandKnowledge
Graphs: ARoadmap(2023).URL:https://arxiv.org/abs/2306.08302.doi:
10.48550/ARXIV.2306.
| ,publisher: | arXivVersionNumber: | 3.  |     |     |     |
| ----------- | ------------------- | --- | --- | --- | --- |
08302
[5] H.Abu-Rasheed,M.Dornhöfer,C.Weber,G.Kismihók,U.Buchmann,M.Fathi, BuildingCon-
textualKnowledgeGraphsforPersonalizedLearningRecommendationsUsingTextMiningand
Semantic Graph Completion, in: 2023 IEEE International Conference on Advanced Learning
Technologies(ICALT),IEEE,Orem,UT,USA,2023,pp.36–40.URL:https://ieeexplore.ieee.org/
| document/10260850/.doi: |     |     | .   |     |     |
| ----------------------- | --- | --- | --- | --- | --- |
10.1109/ICALT58122.2023.00016
[6] M.Kejriwal, KnowledgeGraphs: APracticalReviewoftheResearchLandscape, Information13
| (2022)161.URL:https://www.mdpi.com/2078-2489/13/4/161.doi: |     |     |     |     | .   |
| ---------------------------------------------------------- | --- | --- | --- | --- | --- |
10.3390/info13040161
[7] V.K.Kommineni,B.König-Ries,S.Samuel,Fromhumanexpertstomachines: AnLLMsupported
approachtoontologyandknowledgegraphconstruction,2024.URL:https://arxiv.org/abs/2403.
| 08345.doi: |     | ,versionNumber: | 1.  |     |     |
| ---------- | --- | --------------- | --- | --- | --- |
10.48550/ARXIV.2403.08345
[8] G.Jhajj,X.Zhang,J.R.Gustafson,F.Lin,M.P.-C.Lin, EducationalKnowledgeGraphCreation
andAugmentationviaLLMs, in: A.Sifaleras,F.Lin(Eds.),GenerativeIntelligenceandIntelligent
TutoringSystems, volume14799, SpringerNatureSwitzerland, Cham, 2024, pp.292–304.URL:
https://link.springer.com/10.1007/978-3-031-63031-6_25.doi:
10.1007/978-3-031-63031-6_
| 25 ,seriesTitle: | LectureNotesinComputerScience. |     |     |     |     |
| ---------------- | ------------------------------ | --- | --- | --- | --- |
[9] H.Abu-Rasheed,C.Weber,M.Fathi, KnowledgeGraphsasContextSourcesforLLM-BasedExpla-
nationsofLearningRecommendations, in: 2024IEEEGlobalEngineeringEducationConference
(EDUCON),IEEE,KosIsland,Greece,2024,pp.1–5.URL:https://ieeexplore.ieee.org/document/
| 10578654/.doi: |     |     | .   |     |     |
| -------------- | --- | --- | --- | --- | --- |
10.1109/EDUCON60312.2024.10578654
[10] K.Stancin,P.Poscic,D.Jaksic,Ontologiesineducation–stateoftheart,EducationandInformation
Technologies 25 (2020) 5301–5320. URL: https://link.springer.com/10.1007/s10639-020-10226-z.
| doi: 10.1007/s10639-020-10226-z |     | .   |     |     |     |
| ------------------------------- | --- | --- | --- | --- | --- |
[11] E.Katis,H.Kondylakis,G.Agathangelos,K.Vassilakis, DevelopinganOntologyforCurriculum
andSyllabus, in: A.Gangemi,A.L.Gentile,A.G.Nuzzolese,S.Rudolph,M.Maleshkova,H.Paul-
heim,J.Z.Pan,M.Alam(Eds.),TheSemanticWeb: ESWC2018SatelliteEvents,volume11155,
SpringerInternationalPublishing,Cham,2018,pp.55–59.URL:https://link.springer.com/10.1007/
| 978-3-319-98192-5_11. | doi: |     | , series Title: | Lecture Notes | in  |
| --------------------- | ---- | --- | --------------- | ------------- | --- |
10.1007/978-3-319-98192-5_11
ComputerScience.
[12] E. Ilkou, H. Abu-Rasheed, M. Tavakoli, S. Hakimov, G. Kismihók, S. Auer, W. Nejdl, EduCOR:
An Educational and Career-Oriented Recommendation Ontology, in: A. Hotho, E. Blomqvist,
S.Dietze,A.Fokoue,Y.Ding,P.Barnaghi,A.Haller,M.Dragoni,H.Alani(Eds.),TheSemantic
Web–ISWC2021,volume12922,SpringerInternationalPublishing,Cham,2021,pp.546–562.URL:
https://link.springer.com/10.1007/978-3-030-88361-4_32.doi:
10.1007/978-3-030-88361-4_
| ,seriesTitle: | LectureNotesinComputerScience. |     |     |     |     |
| ------------- | ------------------------------ | --- | --- | --- | --- |
32
[13] A.Radford,J.W.Kim,T.Xu,G.Brockman,C.McLeavey,I.Sutskever,RobustSpeechRecognition

viaLarge-ScaleWeakSupervision,2022.URL:https://arxiv.org/abs/2212.04356.doi:
10.48550/
,versionNumber: 1.
ARXIV.2212.04356