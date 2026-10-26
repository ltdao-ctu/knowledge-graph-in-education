---
title: "electronics-13-02537"
source: "electronics-13-02537.pdf"
source_sha256: "e63f6c42253fea2416ca30a4d95289910b200058c17d92dcbef04f7286fce82f"
converted_at: "2026-10-26T07:05:08.051731+00:00"
markitdown_version: "0.1.9"
---
electronics
Review
A Survey of Knowledge Graph Approaches and Applications
in Education
KechenQu1,KamCheongLi2,BillyT.M.Wong2,* ,ManfredM.F.Wu2andMengjinLiu2
1 CreditBankDepartment,TheOpenUniversityofChina,75FuxingRoad,Beijing100039,China;
qukch@ouchn.edu.cn
2 InstituteforResearchinOpenandInnovativeEducation,HongKongMetropolitanUniversity,Homantin,
Kowloon,HongKong,China;kcli@hkmu.edu.hk(K.C.L.);mmfwu@hkmu.edu.hk(M.M.F.W.);
mjliu@hkmu.edu.hk(M.L.)
* Correspondence:tamiwong@hkmu.edu.hk
Abstract:Thispaperpresentsacomprehensivesurveyofknowledgegraphsineducation.Itcovers
the patterns and prospects of research in this area. A total of 48 relevant publications between
2011and2023werecollectedfromtheWebofScience,Scopus,andProQuestforreview.Thefindings
revealasharpincreaseinrecentyearsinthebodyofresearchintoeducationalknowledgegraphs
whichwasmainlyconductedfrominstitutionsinChina.Mostoftherelevantresearchworkadopted
aquantitativemethod,suchasperformanceevaluation,usersurveys,andcontrolledexperiments,to
assesstheeffectivenessofknowledgegraphapproaches.Thefindingsalsosuggestthatknowledge
graphapproacheswereprimarilyresearchedandimplementedinhighereducationinstitutions,with
afocusoncomputerscience,mathematics,andengineering.Themostfrequentlyaddressedobjectives
includedenhancingknowledgerepresentationandprovidingpersonallearningrecommendations,
andthemostcommonapplicationswereconceptinstructionandeducationalrecommendations.Di-
versedataresources,suchascoursematerials,studentlearningbehaviours,andonlineencyclopaedia,
wereprocessedtoimplementknowledgegraphapproachesindifferentscenarios.Relevanttechnical
meansemployedfortheimplementationofknowledgegraphsdealtwiththepurposesofbuilding
knowledgeontology,achievingrecommendations,andcreatingknowledgegraphs.Variouspedago-
giessuchaspersonalisedlearningandcollaborativelearningaresupportedbytheknowledgegraph
approaches.Thefindingsalsoidentifiedkeylimitationsintherelevantwork,includinginsufficient
Citation:Qu,K.;Li,K.C.;Wong,
informationforknowledgegraphconstruction,difficultyinextendingapplicationsacrosssubject
B.T.M.;Wu,M.M.F.;Liu,M.ASurvey
areas,therestrictedscaleandscopeofdataresources,andthelackofcomprehensiveuserfeedback
ofKnowledgeGraphApproachesand
andevaluationprocesses.
ApplicationsinEducation.Electronics
2024,13,2537. https://doi.org/
Keywords:knowledgegraph;learningrecommendation;technology-mediatedlearning;educational
10.3390/electronics13132537
technology
AcademicEditor:George
AngelosPapadopoulos
Received:31May2024
Revised:26June2024 1. Introduction
Accepted:26June2024 Advances in technologies have facilitated the development of innovative ways to
Published:28June2024 representandorganisevastamountsofinformationandknowledgeinastructuredformat.
Aknowledgegraphisoneofsuchinnovationswhichhasbeenincreasinglyusedinboth
industryandacademia[1]. Aknowledgegraphreferstoagraphofdatawithnodesrepre-
sentingentitiessuchasobjectsandabstractconceptsandwithedgesshowingrelationships
Copyright: © 2024 by the authors.
betweentheentities[2,3]. Asanartificialintelligencetechnology,knowledgegraphshave
Licensee MDPI, Basel, Switzerland.
beenadoptedinawiderangeofapplications,frominformationretrieval,integration,and
Thisarticleisanopenaccessarticle
managementtorecommendationsandquestionanswering[4]. Sincetheirintroductionin
distributed under the terms and
the2010s,knowledgegraphshavebecomeaneffectiveandefficientapproachtoknowledge
conditionsoftheCreativeCommons
Attribution(CCBY)license(https:// organisation,visualisation,andmanagement[5–7].
creativecommons.org/licenses/by/ Intheeducationdomain,knowledgegraphshavebeenincorporatedintovarioustools
4.0/). toenhanceteachingandlearning,suchasrecommendingpersonalisedlearningresources
Electronics2024,13,2537.https://doi.org/10.3390/electronics13132537 https://www.mdpi.com/journal/electronics

Electronics2024,13,2537 2of18
basedonlearningstylesandpreferences[8],predictinglearningperformance[9],facilitating
question generation process [10], and reducing time to retrieve teaching materials [11].
Theyhavealsobeenusedtosupportcoursemanagementandcurriculumimprovement
byenhancingcourse–teachermatching,courseofferings,andcurriculumcoherence[12].
Theapplicationofknowledgegraphscanbeseeninvariousacademicdisciplines,suchas
computerscience[13,14],mathematics[15,16],andmedicine[17].
Despitethebroadrangeofstudiesonknowledgegraphsineducation,thereareonlya
handfulofreviewstudiesreportingrelatedworks[18–20]. Thesereviewshavefocusedon
somespecificareasofknowledgegraphsorcoveredlimitedworksintheliteratureonly.
Toobtainaholisticviewofthestatusofdevelopmentinthisarea,thispaperpresentsa
comprehensivesurveyofknowledgegraphapproachesandapplicationsineducation. It
systematicallysummarisesthefeatures,patterns,andprospectsofresearchandpracticein
thisarea. Specifically,thissurveyfocusedonthefollowingresearchquestions:
1. Whatarethepatternsofpublicationsonknowledgegraphsineducation?
2. Whataretheeducationalcontextsofknowledgegraphapplications?
3. Whataretheobjectives,applicationcategories,datasources,technicalmeans,and
pedagogicalissuesforknowledgegraphapproachesandapplicationsineducation?
2. RelatedWork
Arangeofreviewstudieswithrespecttoknowledgegraphshavebeenperformedover
theyears. Someofthereviewsfocusedontheoveralldevelopmentofknowledgegraphs.
For example, Chen et al. [21] explored the status and trends of research in knowledge
graphs. Theirresultsshowthattherehasbeenatremendousincreaseintheamountof
relevantresearch, particularlyinChina. Themainresearchfocusescoverareassuchas
knowledgegraphembedding,knowledgegraph-basedsearchandquery,andtheuseof
knowledgegraphsforintangibleculturalheritage. Similarly,WangandHe[22]performed
abibliometricanalysisofknowledgegraphresearchbetween2013and2022andfound
six frequently explored dimensions, including ontology modelling, knowledge extrac-
tion,multi-modalknowledgegraphs,knowledge-awareapplications,knowledgegraph
embedding,andrepresentation.
There have been reviews which focused on specific knowledge graph techniques.
Wangetal.[23],forexample,investigatedpublicationsonknowledgegraphembeddingin
termsofitsmodeldesignsandtrainingproceduresinordertoprovideinsightsintohow
relevanttechniquescontributedtoknowledgegraphcompletion,relationextraction,and
question answering. Rajabi and Etminani [24] surveyed the ways in which knowledge
graphswereappliedinexplainableartificialintelligencesystems. Theyfoundthatknowl-
edgegraphshavebeenwidelyusedforpre-modellingforthesystemstoextractfeatures,
entities,andrelationsforinferencingandreasoningpurposes,withneutral-network-based
machinelearningtechniquesbeingthemostcommonlyused. Tianetal.[25]identified
threetypesofknowledgereasoningmethods,whicharebasedonlogicrules,representa-
tionlearning,andneuralnetworks,respectively. Moreover,theyconductedacomparison
of knowledge hypergraph representation methods, taking into account factors such as
problems,solutions,andcategories.
Reviews on knowledge graphs also addressed its application in specific domains.
Abu-Salih[26]presentedananalysisofknowledgegraphconstructionresearchinseven
domains—includinghealthcare,education,informationandcommunicationtechnology,sci-
enceandengineering,finance,societyandpolitics,andtravel—withrespecttoknowledge
graphusage,constructionalgorithms,knowledgegraphresources,embeddingtechniques,
evaluationmeasures,andlimitations. Chiuetal.[27]summarisedhowknowledgegraphs
were constructed and applied in e-retailing, in terms of its design methods, coverage
ofstructuredandunstructureddata,andapplicationareassuchasquestionanswering,
customerserviceoptimisation,inventorymanagement,andsupplychainvisibility. The
studybyWangetal.[28]reviewedtheuseofknowledgegraphsformedicalimagingand
identifiedthemajorapplicationareas,withdiseaseclassificationbeingthemostwidely

Electronics2024,13,2537 3of18
examinedfollowedbyreportgeneration,diseaselocalisationandsegmentation,andim-
age retrieval. In a similar vein, Abu-Salih et al. [29] analysed how knowledge graphs
wereusedinthehealthcarearea,intermsofthetypesofmethods,knowledgebases,and
evaluationprotocols.
Regarding the use of knowledge graphs in education, however, there have been
verylimitedreviewsonrelevantwork. Amongthefewrelatedreviews,Abu-Salihand
Alotaibi[18]examinedknowledgegraphapplicationsacrossfivedomainsineducation,
suchaspersonalisedlearning,curriculumdesign,conceptmapping,semanticsearchand
questioninganswering, andotherrelevantapplications(e.g., educationalmanagement,
knowledgeintegration,andlinkprediction). Ineachdomain,theysummarisedtheknowl-
edgegraphfunctionalities,types,resourcerequirements,constructionmethods,evaluation
criteria,andlimitations.Elkaimbillahetal.[19]providedacomparativestudyofknowledge
graphmodelsintheeducationdomainbasedonrelatedstudies,highlightingthepurposes,
techniques,datasources,evaluationmeasures,andlimitations. Fettachetal.[20]reviewed
theknowledgegraphapplicationsineducationandforemployability. Theyidentifiedthe
maincategoriesofapplicationsineducation,namelyinstructionalconception,knowledge
management,personalisedlearning,questioninganswering,andeducationalassessment.
Foremployability,relevantapplicationsrangebroadlyfromjobrecommendationtojob-skill
matchingandtalentintelligence.
Nevertheless, these reviews on knowledge graphs in education are limited by the
focuses(e.g.,specificallyonanalysingtherelationshipsamongknowledgegraph,educa-
tion,andemployabilityasinFettachetal.[20])andsourcesofdata(e.g.,coveringonly
sevenpublicationsasinElkaimbillahetal.[19]). Relatedreviewshaveyettoprovidea
comprehensiveoverviewofrelevantworkonknowledgegraphsineducation,suchastheir
researchscopes, researchmethods, pedagogyissues, andresearchtrends. Theselimita-
tionsareaddressedinthepresentpaper,whichpresentsasystematicsurveyofrelevant
researchpublications.
3. Methodology
3.1. DataCollection
Forthisstudy,researcharticlesonknowledgegraphsineducationwerecollectedfrom
theWebofScience,Scopus,andProQuest. Thesethreepublicationdatabaseswerechosen
fortheircomprehensivecoverageoftheliteratureandtheirpopularityasdatasourcesfor
reviewsofvarioustopics[30–32]. Thekeywords[“knowledgegraph”and“education”]
wereusedforsearchingtherelevantliteraturefromthedatabases. Onlyjournalarticles
werecovered. Thepublicationperiodwassetfor2011–2023tocopewiththeintroduction
ofknowledgegraphsinthe2010s[5].
Figure1illustratestheproceduresforthesearchandselectionofrelevantarticlesfor
review based on the PRISMA framework. The initial search across the three databases
yielded 289 results, which were reduced to 181 records after removing duplicates. The
abstract of each paper was scrutinised and any records that did not meet the inclusion
criteriawereexcluded,includingthosewhichwerenotempiricalstudies,notrelatedto
education,ornotclearlyrelevanttotheapplicationofknowledgegraphs. Thisscreening
processresultedin88records.
Afterremovingthearticlesforwhichtheirfulltextcouldnotbeaccessed,71records
remained. Thenextphaseinvolvedthoroughlyexaminingthefulltextsofthesearticlesto
assesstheireligibility. Thisprocessledtotheexclusionof23recordswhichdidnotmeet
thedefinedcriteria,suchasnotbeingwritteninEnglish,notbeingjournalarticles,ornot
illustratingthedesignandimplementationofaneducationalsystemorprogrammebased
onknowledgegraphs.Additionally,articleswhichdidnotreporttheimpactsofknowledge
graphsonpedagogy,learningenvironments,and/orlearningoutcomeswereexcluded.
Finally,atotalof48articleswereselectedforreviewandanalysis,representingthe
most relevant research on knowledge graph construction and application in the educa-
tionaldomain.

Electronics 2024, 13, x FOR PEER REVIEW 4 of 19
knowledge graphs on pedagogy, learning environments, and/or learning outcomes were
excluded.
Finally, a total of 48 articles were selected for review and analysis, representing the
Electronics2024,13,2537 4of18
most relevant research on knowledge graph construction and application in the educa-
tional domain.
Figure 1. Procedures for search and selection of relevant publications.
Figure1.Proceduresforsearchandselectionofrelevantpublications.
3.2. Data Analy3si.s2 . DataAnalysis
Content analysCiso wntaesn ptearnfaolrymsiesdw faosr ptheer fsoerlmecetdedf oarrttihcelesse. lIencftoerdmaarttiioclne sr.elIenvfoarnmt taot itohne relevanttothe
research questiroenses awrcahs qidueensttiifioneds wfraosmi deeanchti fioef dthfero amrtiecalecsh aonfdth ceataergtiocrliessedan, dinccalutedginogri stehde ,includingthe
research methoredsse, aerdchucmateitohnoadls l,eevdeulsc,a stiuobnjaelctl edvieslcsi,psluinbejesc, todbijseccitpivliense,s a,pobpjleiccatitvioesn, acaptpelgicoa-tioncategories,
ries, knowledgken gorwaplehd rgeesgoruarpcehsr, etseocuhrnciecsa,l tmecehannicsa, lpmedeaagnos,gpieesd, aagnodg liiems,iatantdiolnims. iTtahtieo cnosd. T-hecodingand
ing and categocraistaetgioorni soaft itohne oinfftohreminatfioornm wateioren fiwrsetr epefirrfsotrpmeerdfo rbmy ead rebsyeaarrcehseera racnhde rthaennd thenchecked
checked by anobtyhearn roetsheearrcrheesre.a Drcihffeerr.eDncieffse breentwceesenb etthwe ejuedngtehmeejundtsg oefm thene ttswoof rtehseeatwrcoherress earcherswere
were discussedd uisnctuils asend augrneteilmaennatg wreaesm reeancthweda.s Braesaecdh eodn. tBhaes pedroocnestsheed pdraotcae, stsheed fedaattuar,etsh efeaturesand
and patterns ofp raetsteeranrcsho fanreds eparracchtiacne donp rkancotiwceleodngke ngorwaplehds gine gedraupchastioinne wdeurcea tainoanlywseerde. analysed.
4. Results
4.1. OverviewofthePublications
4.1.1. YearofPublication
Figure2showsthedistributionofthepublicationsbetweentheyears2011and2023.
Theresultssuggestthatknowledgegraphswerenotusedforeducationpurposesinthe
firstfewyearsafteritwasintroducedinthe2010s[5]. Relevantpublicationsonknowledge
graphs in education have been published starting from 2018. Then, there has been an
increasingtrendofpublications,andthenumberofpublicationsincreasedrapidlyfrom
2in2018to22in2023. TheseresultsechothoseofChenetal.[21],namelythattherehas
beenagrowinginterestinresearchintoknowledgegraphsineducationinrecentyears.

Electronics 2024, 13, x FOR PEER REVIEW 5 of 19
Electronics 2024, 13, x FOR PEER REVIEW 5 of 19
4. Results
4. Results
4.1. Overview of the Publications
4.1. Overview of the Publications
4.1.1. Year of Publication
4.1.1. Year of Publication
Figure 2 shows the distribution of the publications between the years 2011 and 2023.
Figure 2 shoTwhes trheseu dltisst sriubgugteiosnt tohfa tth ken pouwblleicdagteio gnrsa bpehtsw weeenre t hneo ty euasresd 2 f0o1r1 e adnudc a2t0i2o3n. purposes in the
The results suggfiersstt tfheawt kyenaorws laefdtegre i tg wraapsh ins twroedreu cneodt iuns tehde f2o0r1 e0ds u[5c]a. tRioenle vpaunrpt pousebsl iicna ttihoen s on knowledge
first few years afgterra pith ws aisn i endtruocdauticoend hina vthe eb 2e0e1n0 ps u[5b]l.i Rsheeledv satnatr tpiungb lficroatmio n20s 1o8n. kTnhoenw,l tehdegree has been an in-
graphs in educactiroena shinavge t rbeenedn opfu pbulibshliecdat isotanrst,i nagn dfr tohme n20u1m8.b Terh eonf ,p tuhbelriec ahtaios nbse einnc raena sine-d rapidly from 2
creasing trend oifn p 2u0b1l8ic atoti o2n2 si,n a 2n0d2 3th. eT hneusme breers uolft sp eucbhloic athtioosnes oinf cCrehaesne det raalp. i[d2l1y] ,f rnoamm e2l y that there has
Electronics2024,13,2537 in 2018 to 22 in b2e0e2n3. aT ghreoswe irnegsu inlttse reecshto i nth roessee aorfc hC ihnetno ektn aolw. [le2d1]g, en garmapelhys tihna et dtuhecareti 5 oh o na f s 1 i n 8 recent years.
been a growing interest in research into knowledge graphs in education in recent years.
Figure 2. Distribution of the publications between 2011 and 2023.
Figure2.Distributionofthepublicationsbetween2011and2023.
Figure 2. Distribution of the publications between 2011 and 2023.
4.1.2. Country/Region of Authors(cid:31) Affiliations
4.1.2. Country/RegionofAuthors’Affiliations
4.1.2. Country/Region of Authors(cid:31) Affiliations
Figure3presenFtsigtuhreec 3o upnretrsieenst/sr ethgeio cnosuonftraiuetsh/roergsi’oanfsfi loiaf taiounthsoirns(cid:31)t haeffipluiabtiloicnast iionn tsh.eA publications. A
larg F e i p g r u o r p e o 3 r t p io re nlasro egn fet p spu trb hol e ipc oc a ortitu oion nnt s r oi ( e 4fs 2p/ % rue )bg wliioce narts ei oo gnf e sn a (u e4r t2a h%t o e r)d s w(cid:31) f r aeo ffirmel gi a aef tnfi ioel n iraas tt i ieo ndn t sfhrioe n mp C u ah bffiin lila cia ,at fti oiool n lno ssw . iAned China, followed
la b r y ge th p e r U op n o it r e t d io S nbt a oyt f e ptshu web iUl t i h cna 1itt1 ieo %dn . sST (t4ah 2tee% rse )ww wie etrhr e e 15 g1% e%n o.e f rTt a hht e eedrpe u f rwb o lem icrae a t ffi i5o%n li s aot ffi r o otn mhse i K npo uC rbe h alii, ncaaa nt,i d foon4 lsl % o fwrfroe omd m Korea, and 4%
b G y r t e h e e c e U , n V i i t e e t d n a S mftaro, temS s p wGairi n teh ,e Ic1 tea 1,l %Vy,i. ea Ttnnh daemr I e n, d wSipa ea. rie En 5,a %Ictha oloyf f, tat h hne ed p oIunth bde lii rac.a c Et o iau ocn nhs t r oi f efr o sth, mes u oK cto hhrea era s c, Moaun and lat ry 4ise% isa , ,such as Malay-
fr G o e m rm G a r n e y e , c S e, w V it i z ese tinarl a,a mGnde, rS ,ma p n aad innyR , ,I u tSa sws ly iai,tz , a cen ord nla t Inr n idb d,u i aate .n d Eda aRc b huo su osf ti at 2 h,% ec oo onf thttrh eir eb uc p otueu bdn l i tac rba ie toi suo , nts u s2. c%T h h oa efs s tM ehrea e l spa u yul -btslications. These
si r a e , v G ea e l r t m ha a t n k y n , o S w wrel ise tzud elgtrse l arg ner dva ,ep aa hln s dthh a Ravtu eks b sni eoa e ,w n clo set ndu tgd rei i b egu drtaa epd nhd asb a phoap uvl t i ee 2 d %bei neonf e d tsh uteuc da p tiu ieo bdn l iai c nnatda io wanpi s dp. elTier h ade n sig en e education in a
re o s f u c l o ts u n re tr v i e e a s/ l r t e hwg a i tio dk nen s . oraT wnh lge eed s e gor efe cg sou rua lt pns htarsil es h os/a rrv eee sg eibom ene bsn l.e Ts tht h ueo dssei e e rd oef sa Cunlh dtes n aaplesp tol a irl e .ed [s2 ei 1mn ] ,be ild neu wtcha hot i isc oeh n oC ifh n Ci n aha en et al. [21], in
w is id t e h e ra p n r g im e a o r f y c r owe u ghn iio tcr nhie fCs o /hr reikng nai o o iw ns stl .he T de h gpe ersig emr a rae prsyh u rl r tee sgs e aioa lsnr o c fh or . ers kenmobwlele tdhgoes eg roafp Chh reens eeatr cahl.. [2 1], in
which China is the primary region for knowledge graph research.
Figure3.DistribuFtiigounreo f3t.h Deicstoruibnutrtiieosn/ oref gthioen csooufnaturitehso/rresg’aioffinlsi aotfi oanust.hors(cid:31) affiliations.
Figure 3. Distribution of the countries/regions of authors(cid:31) affiliations.
4.1.3. ResearchMethods
Figure 4 shows the research methods used in the studies on knowledge graphs in
education. Mostofthestudies(78%)adoptedquantitativemethods. AsshowninFigure5,
thestudiesinvolvedatotaloffivetypesofquantitativemethods,includingassessingthe
model/systemperformancethroughevaluationmetrics(e.g.,Hits@N,Accuracy,Precision,
Recall,andF-measure);comparisonexperiments;questionnairesurveysonuserexperience,
perception, or satisfaction; tests on student learning performance; and social network
analysis, among which evaluation metrics were the most frequently used quantitative
measures. A small proportion (2%) of the studies used qualitative methods, such as
interviewsandfocusgroups,toconductin-depthanalysesofparticipants’responses. The
remaining (20%) refers to the use of mixed methods, combining both quantitative and
qualitativewaysofcollectingandanalysingthedata.

Electronics 2024, 13, x FOR PEER REVIEW 6 of 19
Electronics 2024, 13, x FOR PEER REVIEW 6 of 19
4.1.3. Research Methods
4.1.3. Research Methods
Figure 4 shows the research methods used in the studies on knowledge graphs in
Figure 4 shows the research methods used in the studies on knowledge graphs in
education. Most of the studies (78%) adopted quantitative methods. As shown in Figure
education. Most of the studies (78%) adopted quantitative methods. As shown in Figure
5, the studies involved a total of five types of quantitative methods, including assessing
5, the studies involved a total of five types of quantitative methods, including assessing
the model/system performance through evaluation metrics (e.g., Hits@N, Accuracy, Pre-
the model/system performance through evaluation metrics (e.g., Hits@N, Accuracy, Pre-
cision, Recall, and F-measure); comparison experiments; questionnaire surveys on user
cision, Recall, and F-measure); comparison experiments; questionnaire surveys on user
experience, perception, or satisfaction; tests on student learning performance; and social
experience, perception, or satisfaction; tests on student learning performance; and social
network analysis, among which evaluation metrics were the most frequently used quan-
network analysis, among which evaluation metrics were the most frequently used quan-
titative measures. A small proportion (2%) of the studies used qualitative methods, such
titative measures. A small proportion (2%) of the studies used qualitative methods, such
as interviews and focus groups, to conduct in-depth analyses of participants(cid:31) responses.
as interviews and focus groups, to conduct in-depth analyses of participants(cid:31) responses.
The remaining (20%) refers to the use of mixed methods, combining both quantitative and
The remaining (20%) refers to the use of mixed methods, combining both quantitative and
Electronics2024,13,2537 qualitative ways of collecting and analysing the data. 6of18
qualitative ways of collecting and analysing the data.
Figure 4. Research methods adopted in the studies.
FiguFrieg 4u.r Ree4s.eRaercshea mrcehthmoedtsh oaddospatdeodp itne dthien stthuedsiteusd. ies.
Figure5.Typesofquantitativemethods.
Figure 5. Types of quantitative methods.
Figure 5. Types of quantitative methods.
4.2. ContextsofKnowledgeGraphApproaches
4.2. Contexts of Knowledge Graph Approaches
4.2. 4C.2on.1t.exLtesv oefl KonfoEwdluedcgaet iGonraph Approaches
4.2.1. Level of Education
4.2.1. LevFeilg oufr eEd6uschaotiwons the levels of education involved in the applications of knowledge
graphs. AmajorityFiogfupreu b6l ischaotiwons sthwee rleevfeolcsu osfe dedounctahtieotne ritniavroylvleedv eilno ftheed uapcaptliiocnat(io86n%s )o.f knowledge
Figure 6 shows the levels of education involved in the applications of knowledge
Thesecondargyraanpdhsp. rAim maaryjorleitvye losf opfuebdliuccaatitoionns hwaevree mfoucuchsesdm oanll ethrep eterrcteinartayg leesv,eil. eo.,f 1e0d%ucation (86%).
graphs. A majority of publications were focused on the tertiary level of education (86%).
and 4%, respTehctei vseelcyo.nTdhareyd ainstdr ipbruitmioanryo lfepvuelbsl iocfa etidouncsatsiuogng heasvtse tmhautckhn somwalleledrg peegrcraenpthages, i.e., 10%
Electronics 2024, 13, x FOR PEER RETVhIEeW s econdary and primary levels of education have much smaller percentages, i.e.,7 1 0of% 1 9
approacheswaenrde p4r%im, raersiplyecbteivineglyi.m Tphlee mdiesntrtiebduatinodn roefs peaurbclhiceadtiionnhsi gsuhgergeesdtus ctahtaiot nkninoswtilteud-ge graph ap-
and 4%, respectively. The distribution of publications suggests that knowledge graph ap-
tions,withalpersosearchfoecsu wseorne sperciomnadrailryy baenidngp rimimpalreymeednutecdat iaonnd. researched in higher education institu-
proaches were primarily being implemented and researched in higher education institu-
tions, with a lesser focus on secondary and primary education.
tions, with a lesser focus on secondary and primary education.
Figure6.Levelsofeducationforthestudies.
Figure 6. Levels of education for the studies.
4.2.2. SubjectDisciplines
4.2.2. Subject Disciplines
Figure7presentsthesubjectdisciplinescoveredinthepublications. Atotalofnine
subFjiegcutrde i7sc piprelisneenstsw tehree siudbenjetcitfi dedis.cOipvlienreasl lc,ocvoemrepdu tienr tshcei epnucbelwicaatsiothnes. sAu btjoetcatl doifs cniipnlein e
suwbjeitcht tdhiescliaprlginesets pwroepreo ritdioennt(i4fi9e%d.) ,Ofovlelorawlle, dcobmypmuattehr esmciaetniccse (w15a%s )thaen dsuebnjgeicnt edeirsicnigpl(i1n2e% ).
wiSthu bthjeec tladrigsecsipt lpinroespsourtcihonas (4la9n%g)u, afogleloawswede lblya smcoatmhmemeracteicasn (d15m%a)n aangde menegnitnheaevrienagr (e1l2a%tiv).e ly
Susbmjeactll edrispcriopplionretsio snucohf paus blalincagtuioangse (a6s% w).eTllh aess cmoamllmesetrpceer acenndt amgaenoafgpeumbelincta thioanvse (a3 %re)law-as
tivfeolyu nsdmianllseur bpjercotpdoirstcioipnl ionfe spiunbclliucdatiinognsp o(6li%tic).a lTshceie snmcea,llmesetd piceirncee,netdaugec aotifo pnu,abnlidcatthioenasr ts.
(3%) was found in subject disciplines including political science, medicine, education, and
the arts. These results indicate that knowledge graphs have been applied in a broadening
spectrum of subject disciplines in recent years.
Figure 7. Distribution of subject disciplines in the publications.
4.3. Implementation of Knowledge Graph Approaches
Table 1 provides a summary of the implementation of knowledge graph approaches
reported in the reviewed articles. It includes details on the objectives, application catego-
ries, data resources used to construct knowledge graphs, technical methods employed,
pedagogical approaches, and key limitations identified.

Electronics 2024, 13, x FOR PEER REVIEW  7 of 19

Figure 6. Levels of education for the studies.
4.2.2. Subject Disciplines
Figure 7 presents the subject disciplines covered in the publications. A total of nine
subject disciplines were identified. Overall, computer science was the subject discipline
with the largest proportion (49%), followed by mathematics (15%) and engineering (12%).
Subject disciplines such as language as well as commerce and management have a rela-
Electronics2024,13,2537
7of18
tively smaller proportion of publications (6%). The smallest percentage of publications
(3%) was found in subject disciplines including political science, medicine, education, and
the arts. These results indicate that knowledge graphs have been applied in a broadening
Theseresultsindicatethatknowledgegraphshavebeenappliedinabroadeningspectrum
spectrum of subject disciplines in recent years.
ofsubjectdisciplinesinrecentyears.

Figure7.Distributionofsubjectdisciplinesinthepublications.
Figure 7. Distribution of subject disciplines in the publications.
|     | 4.3. ImplementationofKnowledgeGraphApproaches |     |     |     |     |
| --- | --------------------------------------------- | --- | --- | --- | --- |
4.3. Implementation of Knowledge Graph Approaches
Table1providesasummaryoftheimplementationofknowledgegraphapproaches
reTpaobrtlee d1 ipnrothveidreesv aie swuemdmaarrtiyc loefs .thIet iimncpluledmesendteattaioilns oofn ktnhoewolbejdegctei vgersa,pahp applipcraotiaocnhecsa te-
repgoorrteieds ,ind athtae rreesvoiuewrceeds uasretidclteos.c Iotn instcrluucdteksn doewtaleilds goeng trhaep ohbsj,etcetcivhensi,c aalpmpleicthatoidons ecmatpeglooy-ed,
riesp, eddaatgao rgeiscoaluarcpepsr ouascehde sto, acnodnskteryuclitm kintaotwiolnedsgidee gnrtaifipehds., technical methods employed,
pedagogical approaches, and key limitations identified.
  T able1.Summaryofarticlesbasedonobjectives,applicationcategories,knowledgegraphresources,
technicalmeans,pedagogies,andlimitations.
|                 | Application | KnowledgeGraph |                |            |             |
| --------------- | ----------- | -------------- | -------------- | ---------- | ----------- |
| Ref. Objectives |             |                | TechnicalMeans | Pedagogies | Limitations |
|                 | Categories  | Resources      |                |            |             |
Enhance •
| personalised |     | Learningresources, |     |     | Theneedforconsistent |
| ------------ | --- | ------------------ | --- | --- | -------------------- |
[8] Educational learnerattributes, Cosinesimilarity Personalised updatesandupkeepofthe
| educationalcontent | recommendation |                |     | learning |                 |
| ------------------ | -------------- | -------------- | --- | -------- | --------------- |
| recommendation.    |                | andpreferences |     |          | knowledgegraph. |

• Evaluationcoveredlimited
learningtopics.
• Unclearinfluenceof
| Facilitatequestion |     |     |     |     | machine-generatedcontent |
| ------------------ | --- | --- | --- | --- | ------------------------ |
[10] generationfor Questiongeneration Textbooks Semanticnetworks N/A onratings.
| instructors. |     |     |     |     | • Smallsamplesizeof |
| ------------ | --- | --- | --- | --- | ------------------- |
instructors.
•
Lackofstandardquestion
generationmodeldatasets.
| Findameaningful |     |     | Featureselection |              | •                 |
| --------------- | --- | --- | ---------------- | ------------ | ----------------- |
|                 |     |     | usingElasticNet  | Personalised | Thefinalknowledge |
[15] knowledge-concept Conceptinstruction Studentlogdata componentsetsizewas
|                     |                   |              | (LASSO)+RF | learning |                              |
| ------------------- | ----------------- | ------------ | ---------- | -------- | ---------------------------- |
| path.               |                   |              | algorithm  |          | arbitrarilyselected.         |
| Empowera            |                   |              |            |          | • Inconsistentperformancedue |
| question-answering  |                   |              | TheWit.ai  |          | toTF-IDFdocumentcontent      |
| [14]                | Questionanswering | Wikipedia    |            | N/A      |                              |
| Chabottorespond     |                   |              | NLPmodel   |          | limitationsorneedfor         |
| toqueries.          |                   |              |            |          | fine-tuning.                 |
| Enablesemantic      |                   |              |            |          | •                            |
| querying,predictive |                   |              |            |          | Thereisaneedtoalignwith      |
|                     | Predictionof      | LMSs(Moodle, |            |          | ontologiesfromdifferent      |
modelling,and
[33] reasoningfor e d u c a t ion al C O C O U d e m y , OWL2ontology N/A d o m a in s li k e s o c i a l n e tworks,
o u t c o m es O p en U n iv e r sit y ) he a lt h b eh a v i o u r s , a n d
studentbehaviour
analysis. demographics.

Electronics2024,13,2537
8of18
Table1.Cont.
|      |            | Application     | KnowledgeGraph |     |                |            |     |                    |
| ---- | ---------- | --------------- | -------------- | --- | -------------- | ---------- | --- | ------------------ |
| Ref. | Objectives |                 |                |     | TechnicalMeans | Pedagogies |     | Limitations        |
|      |            | Categories      | Resources      |     |                |            |     |                    |
|      |            | Educational     |                |     |                |            | •   | Limitedsamplesize. |
|      | Support    | recommendations |                |     |                |            |     |                    |
collaborative Onlinediscussion Collaborative • Focusedononlyone
| [34] |           | andeducational |             |     | BERT-BiLSTM-CRF |          |     |                               |
| ---- | --------- | -------------- | ----------- | --- | --------------- | -------- | --- | ----------------------------- |
|      | knowledge | assessmentand  | transcripts |     |                 | learning |     | learningdomain.               |
|      | building. |                |             |     |                 |          | •   | Investigatedlimitedvariables. |
feedback
|     | Improve | Educational     |     |     |                 |     | •   | Limitedsamplefroma |
| --- | ------- | --------------- | --- | --- | --------------- | --- | --- | ------------------ |
|     |         | recommendations |     |     | BERT-BiLSTM-CRF |     |     |                    |
collaborative Onlinediscussion Collaborative singleuniversity.
[35] learning andeducational transcripts andBERT-Random learning •
|     |              | assessmentand |     |     | Forest |     |     | Focusedononelearning |
| --- | ------------ | ------------- | --- | --- | ------ | --- | --- | -------------------- |
|     | performance. |               |     |     |        |     |     | taskonly.            |
feedback
• Smallsamplesizeandshort
|     |     | E d u c a ti o n a l |     |     |     |     |     | s t u d y d u r at io n . |
| --- | --- | -------------------- | --- | --- | --- | --- | --- | ------------------------- |
[36] Promoteknowledge as se s s m e n t a n d Onlinediscussion BERT-BiLSTM-CRF Collaborative • S i n gl e ta s k e n v ironmentand
|     | elaboration. |          | transcripts |     |     | learning |     |                        |
| --- | ------------ | -------- | ----------- | --- | --- | -------- | --- | ---------------------- |
|     |              | feedback |             |     |     |          |     | text-onlyinteractions. |
•
Limitedtopost-testdata.
• Didnotutiliserelationships
amongknowledge
|     | Predictstudents’ |              | English         |     |     |     |     | componentslikeprerequisites |
| --- | ---------------- | ------------ | --------------- | --- | --- | --- | --- | --------------------------- |
|     |                  |              |                 |     |     |     |     | o r s i m ila ri t ie s .   |
|     | masteryof        | Predictionof | problem-solving |     |     |     | •   |                             |
[37] kno w le d g e b a s e don e d u c a t ion al Graphneural Personalised U n a b le to l e v e rage
reco r d d a t a f rom network learning relationshipsbetweenstudents
|     | t he ir l e ar n i n g | o u t c o m es | E d N e    | t a n d |     |     |     |                 |
| --- | ---------------------- | -------------- | ---------- | ------- | --- | --- | --- | --------------- |
|     | activity.              |                | ASSIST2017 |         |     |     |     | forsocial-based |
recommendations.
•
Limitedusageoftextual
exercisedata.
|     | Improvethe |             |                   |     |     |              | •   | Onlyexploredonemethod |
| --- | ---------- | ----------- | ----------------- | --- | --- | ------------ | --- | --------------------- |
|     |            | Educational | Textbooks,student |     |     | Personalised |     |                       |
[38] recommendationof recommendations learningactivities Similaritymeasures learning (path-based)forknowledge
|     | learningactivities. |     |     |     |     |     |     | graphrecommendersystems. |
| --- | ------------------- | --- | --- | --- | --- | --- | --- | ------------------------ |
Helpstudentsfind
|      | o u tc o u rs e s a n d     |                   | S y ll a bi , t | e a c h e rs ’ | O n t o lo g y            |              |     |                      |
| ---- | --------------------------- | ----------------- | --------------- | -------------- | ------------------------- | ------------ | --- | -------------------- |
|      |                             | Learningresources |                 |                |                           | Personalised | •   | Thereisaneedtobuilda |
| [39] | kn o w l ed g e r e la t ed |                   | l e ss o n p l  | a n s , a n d  | const ru c t io n , Large |              |     |                      |
tograduation searching webpages LanguageModels learning searchengine.
requirements.
|     | Offe r le a rn e rsa |     |                    |     |                  |     |     |     |
| --- | -------------------- | --- | ------------------ | --- | ---------------- | --- | --- | --- |
|     |                      |     | Learningmaterials, |     | SqueezeBERT,word |     | •   |     |
[40] se m a n ti c Conceptinstruction Wikipedia,and Personalised Limitedevaluationof
representationof andsentence learning knowledgegraphaccuracy.
|     |     |     | Dbpedia |     | embeddings |     |     |     |
| --- | --- | --- | ------- | --- | ---------- | --- | --- | --- |
domainconcepts.
Visualisethe
|     |                  |     | Lectureslides, |     |     | Immersivelearning, | •   | Lackofdiscussiononthe |
| --- | ---------------- | --- | -------------- | --- | --- | ------------------ | --- | --------------------- |
|     | k n o w le d g e |     | Wikipedia,and  |     |     |                    |     |                       |
[41] c o n s tru c ti o n Conceptinstruction N/A collaborative processandtechniquesof
|     |     |     | videos |     |     | learning |     | knowledgegraphconstruction. |
| --- | --- | --- | ------ | --- | --- | -------- | --- | --------------------------- |
process.
|     |                    |              | C o u r s e i n fo | r m a t i o n,  |     |     |     |                 |
| --- | ------------------ | ------------ | ------------------ | --------------- | --- | --- | --- | --------------- |
|     | Identifystudentsat | Predictionof |                    |                 |     |     |     |                 |
|     |                    |              | s t u d e n t h    | is t or i c a l |     |     | •   | Limiteddataset. |
[9] risk o f f a i li nga e d u c a t ion al fe a t u r e s a n d Ontologymapping N/A • Lackofuserfeedback.
|      | c o u r s e .                   | o u t c o m es       |                   |                    |                        |              |     |                         |
| ---- | ------------------------------- | -------------------- | ----------------- | ------------------ | ---------------------- | ------------ | --- | ----------------------- |
|      |                                 |                      | p e r f o r m     | a n c e            |                        |              |     |                         |
|      |                                 |                      | Textbooks,        |                    |                        |              | •   |                         |
|      | Helplearners                    |                      | Baidupedia,and    |                    |                        |              |     | Unclearstandardsfor     |
|      |                                 |                      |                   |                    | Graphconvolutional     | Personalised |     | knowledgepoints         |
| [16] | e f fi cie n t ly m e m o r i s | e Conceptinstruction | s tu d e n ts ’ c | l a s s r o o m    | ne t w o rk ( G C N ), |              |     |                         |
|      |                                 |                      | r e sp o n s e s  | ( c o l l e c te d |                        | learning     |     | relationships,division, |
a n d le a r n co n ce p t s . B i LS T M - C R F andvisualisation.
usingsensors)
|     |     |     |     |     | Embedding-based |     | •   | Lackofdemonstrationonhow |
| --- | --- | --- | --- | --- | --------------- | --- | --- | ------------------------ |
Supportknowledge DBp e d ia , W ik i data, Co l la b o r a tive t h e g r o u p kn o w l ed g egraphis
| [42] | sharin g a n d l e a rning | Conceptinstruction |           |       | k n o w le d g e m a p |                |     |                                 |
| ---- | -------------------------- | ------------------ | --------- | ----- | ---------------------- | -------------- | --- | ------------------------------- |
|      |                            |                    | a n d Y A | G O 3 |                        | l e a rn i n g |     | c o ns t r u c ted b a se d o n |
in g r o u p s . f u s io n a lg o r ith m individualknowledgegraphs.
TheLinkedDatafor
Educationdataset
Predictandanalyse Predictionof (learningresources), Featureselection • Lackofdiscussionon
theOpenAcademic
[43] studenteducational educational usingLSTM_GOA N/A knowledgegraphconstruction
outcomes. outcomes Graphdataset, algorithm basedondatacollected.
DBpedia,and
MOOCplatforms
|     |              |     | Individually |     |     | Project-based |     |                    |
| --- | ------------ | --- | ------------ | --- | --- | ------------- | --- | ------------------ |
|     |              |     | constructed  |     |     |               | •   | Lackofdiscussionon |
|     | Showthelogic |     |              |     |     | learning,     |     |                    |
[44] Conceptinstruction knowledgegraphs Knowledgefusion knowledgegraphconstruction
|     | betweenknowledge. |     | byteachersand |     |     | collaborative |     | algorithm. |
| --- | ----------------- | --- | ------------- | --- | --- | ------------- | --- | ---------- |
learning
students
Assiststudentsin
• Thereisaneedtodevelop
[45] reviewinglectures Learningresources Textbooks OntologyRela-Ops N/A
|     | andcomprehending | searching |     |     | model |     |     | morefunctionstosupport |
| --- | ---------------- | --------- | --- | --- | ----- | --- | --- | ---------------------- |
manykindsofqueries.
coursematerial.
|     | Representrelations |     |     |     |     |     | •   | Thesystemlacksintegration |
| --- | ------------------ | --- | --- | --- | --- | --- | --- | ------------------------- |
|     | ofknowledge        |     |     |     |     |     |     | withfunctionalitieslike   |
[46] Learningresources Textbooksand OntologyRela-Ops N/A studentevaluationor
|     | componentsand    | searching | workbooks |     | model |     |     |                      |
| --- | ---------------- | --------- | --------- | --- | ----- | --- | --- | -------------------- |
|     | retrievecontents |           |           |     |       |     |     | personalisedlearning |
|     | ofqueries.       |           |           |     |       |     |     | recommendations.     |

Electronics2024,13,2537
9of18
Table1.Cont.
|      |            |     | Application | KnowledgeGraph |     |                |     |            |     |             |     |
| ---- | ---------- | --- | ----------- | -------------- | --- | -------------- | --- | ---------- | --- | ----------- | --- |
| Ref. | Objectives |     |             |                |     | TechnicalMeans |     | Pedagogies |     | Limitations |     |
|      |            |     | Categories  | Resources      |     |                |     |            |     |             |     |
Enableslearnersto
|     | performnon-linear |     |     |     |     |     | Speech-to-text |     | •   |     |     |
| --- | ----------------- | --- | --- | --- | --- | --- | -------------- | --- | --- | --- | --- |
[47] Conceptinstruction Videolectures techniquesand N/A Lackofadaptiveand
|     | navigationof |     |     |     |     |     |     |     |     | personalisedfeatures. |     |
| --- | ------------ | --- | --- | --- | --- | --- | --- | --- | --- | --------------------- | --- |
semanticanalysis
learningcontents.
Helpstudents
• Omissionofkeyimagesand
|     | quicklyand          |     |     |     |     | BERT,nameentity |     |     |     |                       |     |
| --- | ------------------- | --- | --- | --- | --- | --------------- | --- | --- | --- | --------------------- | --- |
|     | systematicallygrasp |     |     |     |     |                 |     |     |     | handwritinginthevideo |     |
[17] Conceptinstruction Videolectures recognition,and N/A lectures.
|     | theframeworkand   |     |     |     |     |     | YOLOv3 |     | •   |                           |     |
| --- | ----------------- | --- | --- | --- | --- | --- | ------ | --- | --- | ------------------------- | --- |
|     | keycontentofvideo |     |     |     |     |     |        |     |     | Lackofrelationshipweights |     |
betweennodes.
lectures.
|     | Es ti m at e s | tu de nts’ |              |                |     |     |     |     |     |     |     |
| --- | -------------- | ---------- | ------------ | -------------- | --- | --- | --- | --- | --- | --- | --- |
|     |                |            | Predictionof | Onlinetutoring |     |     |     |     | •   |     |     |
[48] p r ofi c ie n cy in educational systemand Recurrentneural N/A Exploredfactorslimitedto
|     | k n o w le | d g e  |          |                    |     |     | network |     |     | finalgradeanddiscussion. |     |
| --- | ---------- | ------ | -------- | ------------------ | --- | --- | ------- | --- | --- | ------------------------ | --- |
|     |            |        | outcomes | E-learningplatform |     |     |         |     |     |                          |     |
|     | c o n ce   | p ts . |          |                    |     |     |         |     |     |                          |     |
Coursesyllabiinthe
|     | Improvethe |     |     | currentuniversity |     |     |     |     |     |     |     |
| --- | ---------- | --- | --- | ----------------- | --- | --- | --- | --- | --- | --- | --- |
• Lackofintelligentalgorithms
|     | curriculumsystem |     | Curriculumdesign | andthe |     | LatentDirichlet |     |     |     |     |     |
| --- | ---------------- | --- | ---------------- | ------ | --- | --------------- | --- | --- | --- | --- | --- |
[12] andmanagement benchmarkingtop Allocation N/A anddatabasesforautomated
|     | inhighereducation |     |     |                      |     |     |     |     |     | curriculumimprovement. |     |
| --- | ----------------- | --- | --- | -------------------- | --- | --- | --- | --- | --- | ---------------------- | --- |
|     | institutions.     |     |     | universities,teacher |     |     |     |     |     |                        |     |
information
• Biasedbysinglecourse
domainandstudent
background.
|     | Construct |     |     |     |     |     |     |     | •   | Lackofprofessors’ |     |
| --- | --------- | --- | --- | --- | --- | --- | --- | --- | --- | ----------------- | --- |
perspectivesonknowledge
|      | meaningful  |     |                  | Courseinformation, |     |                   |     |               |     |             |     |
| ---- | ----------- | --- | ---------------- | ------------------ | --- | ----------------- | --- | ------------- | --- | ----------- | --- |
|      | connections |     | Curriculumdesign |                    |     |                   |     | Collaborative |     | graphtools. |     |
| [13] |             |     |                  | socialmedia        |     | Semanticmediawiki |     |               | •   |             |     |
betweensocial andmanagement (Facebook,Twitter) learning Studentsunderutilisedsocial
|     | mediaandformal |     |     |     |     |     |     |     |     | featurescomparedtoonline |     |
| --- | -------------- | --- | --- | --- | --- | --- | --- | --- | --- | ------------------------ | --- |
learning.
platforms.
• Lackofanalysisofthe
implicationsofcrowdsourcing
ontologyconcepts.
•
|     | Provideconcept |     |     |     |     |     | Named-entity |     |     | Thereisaneedtodevelop |     |
| --- | -------------- | --- | --- | --- | --- | --- | ------------ | --- | --- | --------------------- | --- |
v i s ua li s a t io n a n d Pro b l e m - b ased d o w n st r e am a p p l ic a ti onslike
| [49] |     |     | Conceptinstruction | Coursematerials |     | recogn | it io nand |     |     |     |     |
| ---- | --- | --- | ------------------ | --------------- | --- | ------ | ---------- | --- | --- | --- | --- |
p r o m o t e c o g ni t iv e N L P l e a r ni n g cu r ri cu l u m d es i g n a n d
|     | engagement. |     |     |     |     |     |          |     |     | learningrecommendations. |     |
| --- | ----------- | --- | --- | --- | --- | --- | -------- | --- | --- | ------------------------ | --- |
|     |             |     |     |     |     |     | Resource |     | •   | Lackofapprenticeship     |     |
Providesemantic
searchforreskilling Educational Educationproviders’ Description providersandcost–benefit
| [50] |               |     | recommendations |          |     | Framework,slot |         | N/A |     |                      |     |
| ---- | ------------- | --- | --------------- | -------- | --- | -------------- | ------- | --- | --- | -------------------- | --- |
|      | andupskilling |     |                 | Webpages |     |                |         |     |     | analysisforeducation |     |
|      | options.      |     |                 |          |     |                | filling |     |     | recommendation.      |     |
Onlineeducation
resources(e.g.,
|      | Manageandpresent |     |           |                  |     |                 |     |     | •   | Limitededucationalresource |     |
| ---- | ---------------- | --- | --------- | ---------------- | --- | --------------- | --- | --- | --- | -------------------------- | --- |
|      | variousmodesof   |     | Knowledge | Baiduentries),   |     |                 |     |     |     |                            |     |
| [51] |                  |     |           | offlineeducation |     | BERT-BiLSTM-CRF |     | N/A |     | integration.               |     |
educational management resources(e.g., • Small-scaleknowledgegraphs.
resources.
PowerPointsand
classaudios)
|     | Minimisethetime   |     |     | DBpedia          |     |     |     |     | •   |                        |     |
| --- | ----------------- | --- | --- | ---------------- | --- | --- | --- | --- | --- | ---------------------- | --- |
|     | instructorshaveto |     |     | KnowledgeGraphs, |     |     |     |     |     | Semanticdataextraction |     |
[11] Educational Semanticsimilarity N/A challengesfeasibilityand
|     | spendlookingfor   |     | recommendations | instructor’steaching |     |     |     |     |     |              |     |
| --- | ----------------- | --- | --------------- | -------------------- | --- | --- | --- | --- | --- | ------------ | --- |
|     | teachingmaterial. |     |                 |                      |     |     |     |     |     | scalability. |     |
plans
NationalScience
Foundation,Survey
|     | Providea |     |     |          |     |                 |     |     | •   | Incompletedatasource |     |
| --- | -------- | --- | --- | -------- | --- | --------------- | --- | --- | --- | -------------------- | --- |
|     |          |     |     | ofEarned |     | SemanticExtract |     |     |     |                      |     |
[52] comprehensive Learningresources D o c t o r at es Tran s f o rm and N/A coverage.
|     | resourcefor |     | searching |                 |           |     |             |     | •   | Insufficientcoverageof |     |
| --- | ----------- | --- | --------- | --------------- | --------- | --- | ----------- | --- | --- | ---------------------- | --- |
|     |             |     |           | Re st ri c t    | e d D ata |     | L o a d -er |     |     |                        |     |
|     | students.   |     |           | AnalysisSystem, |           |     |             |     |     | diversegroups.         |     |
andWikidata
|     |            |         |             |                   |     |                    |          |              | •   | S t a t i c u s e r | m o d e l l in g i g n o res |
| --- | ---------- | ------- | ----------- | ----------------- | --- | ------------------ | -------- | ------------ | --- | ------------------- | ---------------------------- |
|     | Enha n c e | o nline |             | Twopublicdatasets |     | Graphconvolutional |          |              |     |                     |                              |
|     | c o u rs   | e       |             |                   |     |                    |          |              |     | at t r i b u t e c  | o rr e la t i o n s( a g e , |
|     |            |         | Educational | (Movielens-20M,   |     |                    | network, | Personalised |     |                     |                              |
[53] recommendationsto recommendations B oo k -C ro s s i n g ) a n d C o ll ab o ra t i v e learning knowledgelevel).
|     | ad d r e s s  | u s e r      |     |                |                  |         |                         |     | •   | A n e ed t o  | i m p r o ve t h e      |
| --- | ------------- | ------------ | --- | -------------- | ---------------- | ------- | ----------------------- | --- | --- | ------------- | ----------------------- |
|     | ch ar a c t e | ri s ti c s. |     | a n in d us tr | i a l d a t a se | t filte | r in g a lg o r i th ms |     |     |               |                         |
|     |               |              |     |                |                  |         |                         |     |     | rec o m m e n | d a ti o n ac c u racy. |
Predictappropriate
E-content(e.g.,
|     | resourceswiththe |     |     |     |     |     |     |     | •   | Potentialtoimprove |     |
| --- | ---------------- | --- | --- | --- | --- | --- | --- | --- | --- | ------------------ | --- |
[54] highestranking Educational E-Library,Coursera), NLP Personalised predictionsusingdeep
|     |                     |                | recommendations | userselectionsout |            |     |     | learning |     |                     |     |
| --- | ------------------- | -------------- | --------------- | ----------------- | ---------- | --- | --- | -------- | --- | ------------------- | --- |
|     | linkedtothe         |                |                 |                   |            |     |     |          |     | learningtechniques. |     |
|     | learner’sinterests. |                |                 | ofthesematerials  |            |     |     |          |     |                     |     |
|     | H e lp s t ud e     | n t s b u i ld |                 | E d u c a         | ti o n a l |     |     |          | •   |                     |     |
[55] c o m pl e x k n o w l e d g e Conceptinstruction reso u r ce s , l ea r n ing N o d e fe atu r e N/A L a c k o f e v al u a t io n ofthe
|     |             |     |     |           |     | ext | ra c ti on m et h od |     |     | p r o p o s e d | m e t h o d . |
| --- | ----------- | --- | --- | --------- | --- | --- | -------------------- | --- | --- | --------------- | ------------- |
|     | structures. |     |     | behaviour |     |     |                      |     |     |                 |               |
Helpstudentsaccess
|     |     |     |     | L e a r | n i n g |     | C o ll ab o r a ti v e |     |     |     |     |
| --- | --- | --- | --- | ------- | ------- | --- | ---------------------- | --- | --- | --- | --- |
learningresources Educational Personalised • Limitedanalysisof
[56] accuratelyand recommendations behav i o u r s , c ourse filte r in g a lg o r i th ms, learning userfactors.
|     |     |     |     | information |     | similaritymeasures |     |     |     |     |     |
| --- | --- | --- | --- | ----------- | --- | ------------------ | --- | --- | --- | --- | --- |
efficiently.

Electronics2024,13,2537
10of18
Table1.Cont.
|      |            | Application | KnowledgeGraph |     |                |            |     |             |
| ---- | ---------- | ----------- | -------------- | --- | -------------- | ---------- | --- | ----------- |
| Ref. | Objectives |             |                |     | TechnicalMeans | Pedagogies |     | Limitations |
|      |            | Categories  | Resources      |     |                |            |     |             |
• Itusesagenerallexical
|     | Presentknowledge |     |     |     |     |     |     | database(WordNet)which |
| --- | ---------------- | --- | --- | --- | --- | --- | --- | ---------------------- |
couldbeimprovedwith
unitsina
[57] semantically Conceptinstruction Textbooks NLP N/A domain-specificontologies.
•
|     | well-organised |     |     |     |     |     |     | Themodelhasonlybeen      |
| --- | -------------- | --- | --- | --- | --- | --- | --- | ------------------------ |
|     | manner.        |     |     |     |     |     |     | appliedtoComputerScience |
textbookssofar.
• Insufficientinformation
Entityextraction,
|      | Communicate        |                    |     |     |                     |     |     | providedaboutthedata |
| ---- | ------------------ | ------------------ | --- | --- | ------------------- | --- | --- | -------------------- |
|      | knowledgelogically |                    |     |     | relationextraction, |     |     | sourcesandtechnical  |
| [58] |                    | Conceptinstruction | N/A |     | andattribute        | N/A |     |                      |
|      | andcoherently.     |                    |     |     |                     |     |     | implementationofthe  |
|      |                    |                    |     |     | extraction          |     |     | knowledgegraph       |
constructionprocess.
Improvethecourse
|     |     |     | Aud i o , sh e | e t m usic, | R e s o u r c e |     | •   |     |
| --- | --- | --- | -------------- | ----------- | --------------- | --- | --- | --- |
[59] recommendation Educational c h a n ts , a n d D e sc r i p t io n Personalised Aneedtoimprovethe
accuracyformusic recommendations learning recommendationaccuracy.
|     |     |     | metadata |     | Framework |     |     |     |
| --- | --- | --- | -------- | --- | --------- | --- | --- | --- |
education
Enablestudentsto
seekoutand
Learningresources WikipediaMiner, • Onlytext-baseddataresources
| [60] | examineeducational |           | Textbooks |     |     | Networkedlearning |     |           |
| ---- | ------------------ | --------- | --------- | --- | --- | ----------------- | --- | --------- |
|      | resourcesthatalign | searching |           |     | NLP |                   |     | included. |
withtheirinterests.
Provide
|     | p e r s o na l is e d |     | L ea r n | i n g |     |     | •   |     |
| --- | --------------------- | --- | -------- | ----- | --- | --- | --- | --- |
[61] lea r n i n g c o n t ent Educational asses sm e n t , c ourse Named-entity Personalised Lackofevaluationofthe
|     |                | recommendations |           |     | recognition | learning |     | proposedmethod. |
| --- | -------------- | --------------- | --------- | --- | ----------- | -------- | --- | --------------- |
|     | accordingtothe |                 | materials |     |             |          |     |                 |
skillsetoflearners.
Predictstudents’
learningbehaviour Conditional Problem-based • Deeplearningisneededto
Subjectmaterials
[62] inordertoprovide Questionanswering RandomFields, learning,cognitive improveproblem
feedbackonthe andsyllabi TF-IDF learning understandingaccuracy.
teachingeffect.
|     | Effectivelyprovide |     |     |     |     |     | •   | Lackofin-depthsystem |
| --- | ------------------ | --- | --- | --- | --- | --- | --- | -------------------- |
|     | informationin      |     |     |     |     |     |     | evaluation.          |
[63] responsetosearches Learningresources Webpages Bi-LSTMmodel N/A • Noalgorithmperformance
searching
|     | forcontentthatis  |     |     |     |     |     |     | comparisonortechnical     |
| --- | ----------------- | --- | --- | --- | --- | --- | --- | ------------------------- |
|     | usefultolearners. |     |     |     |     |     |     | support.                  |
|     | Recommend         |     |     |     |     |     | •   | Prerequisiterelationships |
Textbook,
|     | personalised |     | Wikipedia,and |     |     |     |     | betweenknowledgepointsare |
| --- | ------------ | --- | ------------- | --- | --- | --- | --- | ------------------------- |
[64] exercisestostudents Educational Collaborative Personalised recognisedmanually.
|     |                 | recommendations | testingbehaviourof |     | filtering | learning |     |                             |
| --- | --------------- | --------------- | ------------------ | --- | --------- | -------- | --- | --------------------------- |
|     | inanappropriate |                 |                    |     |           |          | •   | Limitedtestingbehaviourdata |
|     | order.          |                 | students           |     |           |          |     | types.                      |
P r o v i de
person a li s e d content Educational Collaborative Personalised • Failstoadequatelydiscussor
[65] recommendations N/A filtering learning describethedatasources.
forlearners.
Effectively
recommend Educational Collaborative Personalised • Aneedtoimprovethe
[66] learningresources recommendations Webpages filtering learning
recommendationaccuracy.
tolearners.
Supportstudentsin
|     | constructingand |     |                   |     |     |               | •   | Lackofdiscussionon |
| --- | --------------- | --- | ----------------- | --- | --- | ------------- | --- | ------------------ |
|     |                 |     | Student-generated |     |     | Collaborative |     |                    |
[67] expandingtheir Conceptinstruction knowledgegraphs N/A learning knowledgegraphconstruction
|     | knowledge |     |     |     |     |     |     | methodandprocess. |
| --- | --------- | --- | --- | --- | --- | --- | --- | ----------------- |
structure.
Providea
|     | well-structured |     |     |     | SemanticSimilarity |     |     |     |
| --- | --------------- | --- | --- | --- | ------------------ | --- | --- | --- |
|     | overviewof      |     |     |     | Measure,Resource   |     | •   |     |
[68] knowledgein Conceptinstruction DBpedia Description N/A Limiteddatasources.
|     | nuclearpower |     |     |     | Framework |     |     |     |
| --- | ------------ | --- | --- | --- | --------- | --- | --- | --- |
engineering.
• Thescaleoftheknowledge
Threescientific
Enhancescientific Knowledge databases:Webof Machine-learning Problem-based graphshouldbeexpandedto
| [69] |     |     |     |     |     |     |     | covermoredomains. |
| ---- | --- | --- | --- | --- | --- | --- | --- | ----------------- |
retrievalefficiency. management Science,Engineering algorithms learning •
|     |     |     | Village,andEBSCO |     |     |     |     | Moreadvancedalgorithmsare |
| --- | --- | --- | ---------------- | --- | --- | --- | --- | ------------------------- |
required.
|     | Support |     |     |     | Gatedrecurrentunit |     | •   | Limitedscopeofrelations |
| --- | ------- | --- | --- | --- | ------------------ | --- | --- | ----------------------- |
Standard
personalised c u r r ic u l u m d a ta a n d network, Pe r s o n a li sed identified.
[70] teachingservices Conceptinstruction probabilistic • Lackofsemi-supervised
|     |                    |     | le a r n i n g a ss | e ss m e n | t               | l e a r n in g |     |                   |
| --- | ------------------ | --- | ------------------- | ---------- | --------------- | -------------- | --- | ----------------- |
|     | andadaptive        |     | data                |            | associationrule |                |     | learningtoutilise |
|     | learningsolutions. |     |                     |            | miningalgorithm |                |     | unlabelleddata.   |

Electronics2024,13,2537 11of18
4.3.1. TypesofObjectives
Figure8illustratestheobjectivesofknowledgegraphapproachesinthestudies. The
Electronics 2024, 13, x FOR PEER REVIEWm ostfrequentobjectivewasenhancingknowledgerepresentation,suchasdemo1n2s torf a1t9in g
therelationshipbetweenknowledgetoaidcomprehensionandmemorisation. Another
Electronics 2024, 13, x FOR PEER REVIEW 12 of 19
commonobjectivewasprovidingpersonallearningrecommendations,wherecoursere-
sources,learningpaths,orlearningactivitieswererecommendedaccordingtostudents’
improving learning efficiency, predicting learning behaviours or outcomes, promoting
interestsorcharacteristics. Otherobjectivesarerelatedtothelearningprocess, suchas
collaborative learning, and offering accurate responses to learning queries. Some objec-
improving learimnipnrgoevfifincgi elenacryn,ipnrge deffiictciinegnclye,a rpnriendgicbtienhga lveiaorunrisngo rboehuatcvoiomuerss, oprr oomutocotimnges, promoting
tives aimed to support staff, such as facilitating instructors(cid:31) organisation of learning re-
collaborativelecaornllianbgo,raantidveo flfeearrinnignagc, caunrda toeffreesrpinogn saecscutoraletea rrneisnpgonquseesr iteos .leSaormnienogb qjeucetirvieess. Some objec-
sources and assisting with knowledge/course management.
aimedtosuppotirvtesst aafifm,seudc htoa ssufpapciolirtta stitnaffg,i nsustcrhu catso frasc’iolirtgaatinnigs aitnisotnruocftoleras(cid:31)r noirngganreissaotuiornce osf learning re-
andassistingwsiothurkcneso wanlded agses/isctoinugr sweimtha knnaogwemleedngte./course management.
Figure 8. Types of objectives of knowledge graph approaches.
Figure8.Typesofobjectivesofknowledgegraphapproaches.
Figure 8. Types of objectives of knowledge graph approaches.
4.3.2. Types of Application Categories
4.3.2. TypesofApplicationCategories
Figure 9 sum4m.3a.2r.i sTeysp tehse oafp Applipcalitciaotnio cna tCeagtoergieosr ioefs knowledge graph approaches. The
Figure9summarisestheapplicationcategoriesofknowledgegraphapproaches. The
most common approaFcihg uwraes 9 c sounmcempat riinssetsr uthcet iaopnp, lfioclaltoiwone dca bteyg eodriuecsa otfi oknnaolw relecdogmem greanpdha -approaches. The
most common approach was concept instruction, followed by educational recommen-
tions. Other commmoonst tcyopmesm oofn a apppplircoaatciohn ws ains ccloundcee pleta irnnsitnrugc rteiosno,u froclelo sweaerdc hbiyn ged, uthcea tpiorne-al recommenda-
dations. Other common types of applications include learning resource searching, the
diction of educatitoionnasl. oOutthceorm ceosm, amnodn e tdyupceast oiofn aapl palsicsaetsisomnse nint calnudd ef eleeadrbnaicnkg. rIens oaudrdcieti osena, rching, the pre-
predictionofeducationaloutcomes,andeducationalassessmentandfeedback. Inaddition,
knowledge graphdsi chtiaovne oafl seod ubceaetnio enmalp oluotyceodm teos ,a aidn di ne dcuucraritciounluaml a sdseessisgmne nant dan md afneeadgbea-ck. In addition,
knowledgegraphshavealsobeenemployedtoaidincurriculumdesignandmanagement,
ment, knowledgek mnoawnalegdegmee gnrta, pqhuse shtiaovne aanlssow bereienng ,e amnpdl oqyueeds ttioo na gide niner cautirornic.u lum design and manage-
knowledgemanagement,questionanswering,andquestiongeneration.
ment, knowledge management, question answering, and question generation.
Fig F u i r g e u 9 re . A 9. pAplpicpalitcioanti ocnatceagtoergioesri oesf konfokwnolewdlgeed ggeragprhap ahppaproparcohaecsh.e s.
Figure 9. Application categories of knowledge graph approaches.
4.3.3. TypesofKnowledgeGraphResources
4.3.3. Types of Knowledge Graph Resources
Figure 104p.3re.3s.e Tnytspeths eoft yKpneoswolfedkgneo Gwrlaepdhg eRgesroauprhcerse sources utilised in the studies.
Figure 10 presents the types of knowledge graph resources utilised in the studies.
Themostcommonlyusedresourceswerecoursematerials,suchastextbooks,PowerPoint
Figure 10 presents the types of knowledge graph resources utilised in the studies.
The most commonly used resources were course materials, such as textbooks, PowerPoint
slides,syllabi,coursevideos,lecturenotes,labmanuals,andexamquestions. Otherfre-
The most commonly used resources were course materials, such as textbooks, PowerPoint
slides, syllabi, course videos, lecture notes, lab manuals, and exam questions. Other fre-
quentlyutilisedresourcesincludespecificdatasets(e.g.,Wikidata,DBpedia,andscientific
slides, syllabi, course videos, lecture notes, lab manuals, and exam questions. Other fre-
quently utilised resources include specific datasets (e.g., Wikidata, DBpedia, and scientific
databases)anddatarelatedtostudentlearningbehaviours(e.g.,logintolearningplatforms,
quently utilised resources include specific datasets (e.g., Wikidata, DBpedia, and scientific
databases) and data related to student learning behaviours (e.g., login to learning plat-
theselectionoforaccesstomaterials,andtestingbehaviourdataduringtheprocessof
databases) and data related to student learning behaviours (e.g., login to learning plat-
forms, the selection of or access to materials, and testing behaviour data during the pro-
answering questions). These were followed by online encyclopaedias (e.g., Wikipedia
forms, the selection of or access to materials, and testing behaviour data during the pro-
cess of answering questions). These were followed by online encyclopaedias (e.g., Wik-
andBaidupedia),studentperformance(e.g.,scoresofhomeworkassignments,quizzes,
cess of answering questions). These were followed by online encyclopaedias (e.g., Wik-
ipedia and Baidupedia), student performance (e.g., scores of homework assignments,
ipedia and Baidupedia), student performance (e.g., scores of homework assignments,
quizzes, midterm exams, and final exams), learning management systems or learning plat-
quizzes, midterm exams, and final exams), learning management systems or learning plat-
forms, webpages (e.g., education providers(cid:31) webpages), and online discussion transcripts.
forms, webpages (e.g., education providers(cid:31) webpages), and online discussion transcripts.
Some types of resources were used relatively infrequently, including course information,
Some types of resources were used relatively infrequently, including course information,
MOOC platforms, learner attributes, teacher information, and social media.
MOOC platforms, learner attributes, teacher information, and social media.

Electronics2024,13,2537 12of18
midtermexams,andfinalexams),learningmanagementsystemsorlearningplatforms,
Electronics 2024, 13, x FOR PEER REVwIEeWbp ages(e.g.,educationproviders’webpages),andonlinediscussiontranscripts.13S oomf 1e9
Electronics 2024, 13, x FOR PEER REVIEW 13 of 19
typesofresourceswereusedrelativelyinfrequently,includingcourseinformation,MOOC
platforms,learnerattributes,teacherinformation,andsocialmedia.
Figure 10. Types of knowledge graph resources.
FigFuigreu r1e0.1 T0.yTpyeps eosf okfnkonwolwedlegdeg geragprahp rhesroesuorucersc.e s.
4.3.4. Types of Technical Means
4.3.4. TypesofTechnicalMeans
4.3.4. Types of Technical Means
Figure 11 depicts the technical means employed to implement knowledge graph ap-
Figure11depictsthetechnicalmeansemployedtoimplementknowledgegraphap-
proFaigcuhrees 1f1o dr epedicutsc atthieo nte. chFnoric abl umiledainngs emknpolwoyleeddg teo iomnptolelomgeyn t aksn othwel eddgatea g rmapohd ealp -for
proachesforeducation. Forbuildingknowledgeontologyasthedatamodelforknowledge
prokancohwesle dfogre gerdaupcha, tmioanc. hFinoer lebaurnilidnign gte ckhnnoiqwuleeds gsue cho natso Glorgayp ha Ns etuhrea l dNaettaw omrkods e(Gl NfoNr s),
graph,machinelearningtechniquessuchasGraphNeuralNetworks(GNNs),Bidirectional
knBowidlierdecgteio gnraalp Ehn, mcoadcehri nRee lperaersneinntga ttieocnhsn fiqroumes Tsuracnhs afos rGmrearpsh ( NBEeRuTrasl) ,N aentdw oLraktes n(Gt DNiNrisc)h, let
EncoderRepresentationsfromTransformers(BERTs),andLatentDirichletAllocation(LDA)
BidAirlleocctiaotnioanl E(LnDcoAd)e wr eRreep trhees emntoastti ofnresq furoenmtl yT ruasnesdfo mrmeaenrss .( BTEhRisT ws)a, sa nfodl lLowateedn tb Dy isriecmhlaent tic
werethemostfrequentlyusedmeans. Thiswasfollowedbysemanticwebtechnologies
Allwoceabt itoench (nLoDloAg) iewse srue cthh ea sm Roesst ofurerqceu eDnetlsyc ruipsetido nm Feraanms.e Twhoisrk w RaDs Ffo allnodw eOdW bLy s2e omnatnoltoicg y,
suchasResourceDescriptionFrameworkRDFandOWL2ontology,andnaturallanguage
weabn tde cnhantuorlaolg liaens gsuuacghe apsr oRceessosuinrgce t eDchesncirqiupetiso snu cFhra ams newamorekd -RenDtFit ya nredc oOgWniLti o2n o. Fnotor laocghyie, v-
processingtechniquessuchasnamed-entityrecognition. Forachievingrecommendations
andin nga rteucroaml lamnegnudaagteio pnrso cbeassseidng o tne cthhnei qkuneosw sluecdhg aes g nraamphe,d c-oenlltaibtyo rraetciovgen fiitlitoenri.n Fgo ra algcohriietvh-ms
basedontheknowledgegraph,collaborativefilteringalgorithmssuchasmatrixfactorisa-
ing tsi uo r ncehc w o am esr m emm eantord siaxt t ffi r oaecn qtsou rb ein assatl etyidou no s n ewd te, hrf eeo lmk lo now oswte dflreeb dqy gue se i g mnrtila lyp a r hui , ts yecdo m,l l efaoa bls oluor rwa e t seivds e u b c fiyh l tsa eis rmi c niolgas ri a nilte gyo smr im itehail msaur s ir teys,
su g csh rua ca phs h am as l acg too rsi r xiin t f hea m cstis omr s iiu slaa crh tiito ayn s, gS w PreaA rpe Rh m Q aL olgs ,ot a rn firtd ehqmc u ose r r nse tul l acyht i u oas nse d cSo ,P e fAo ffiRll c oQi w eLn e, t das nb sdu y c cs hoimrars iellS aar ptiie toy an r m mcoe a aenffis ’ u scr rieea snn tks
su c cso hur ca rhe s l aa cso ti s oSi npn . eea F sro imm rat i h lna e(cid:31)rsi c trr yae ,na g tki r o acn pohror f aekllag nto oior w inth l. e mFdos gr e stu ghc reh a c p arhes saS ,tPigoA rna R poQ hf Lkd ,n a aot n awd bla ec sdo egr m ree a lga nrtaa iopg nhe msc,o ege nrffi taps c y ihe s n tde tas mt as-
su s cbu hac sa hes amS s paN enaaE rgO me4ma J new (cid:31)ns e tr r aseyn tsk ht ee cmo m rsr o ess lut act c iho o m nas. m FNo oEr n Ol t y h4e uJ s cwe reed arem ti otehn ae n o ms f . koO nstt o hcw eor lme m dmg eoe a nn gls rya i n puc hsles ud, d g me ra kepan hno sw d. a lOe ta dth- geer
ba e smm e em baena dsn d aiing nce glmutode oen l t kk i snt y sosws t u elm cehdsga ses u Oecmh p eba nes Kd NdE EianO ngd 4 tJob woiblekli rio etsm t sh eue trc i mhc o vass is tOu c apo l m iesna mKti o oEn n al a ynn du d sba eibn dla im loyme ti a cen strs ti. oc O o vl t sihssue u rac lhi-
me asa santCisoi
t
inn
e S
cap lnu add
c
eae .nkanlyowticlse dtogoel se msubcehd adsi nCgi tteoSoplakcites. s uch as OpenKE and bibliometric visuali-
sation and analytics tools such as CiteSpace.
FFiigguurree 1111.. TTyyppeess ooff tteecchhnniiccaallm meeaannssu usseeddf foorri mimpplelemmeennttaattioionno offk knnoowwleleddggeeg grraapphh..
Figure 11. Types of technical means used for implementation of knowledge graph.
4.3.5. Types of Pedagogies
4.3.5. Types of Pedagogies
Figure 12 shows the pedagogies supported by knowledge graph approaches. The
moFsigt ufrreeq u12e nsth poewdsa gthoeg yp ewdaasg poegriseos nsaulipspedor lteeadr nbiyn gk,n aocwhileevdegde tghrraopuhg ha pthper oraecchoems.m Tehned a-
motsiot nfr eoqf uaednetq pueadtea gleoagryn iwnga sa pcteirvsiotineasl iosre da pleparronpirniga,t ea clehaiernveindg t hrersoouugrhc etsh efo rre csotumdmenetnsd. aT-his
tion of adequate learning activities or appropriate learning resources for students. This

Electronics2024,13,2537 13of18
Electronics 2024, 13, x FOR PEER REVIEW 14 of 19
4.3.5. TypesofPedagogies
Figure 12 shows the pedagogies supported by knowledge graph approaches. The
mostfrequentpedagogywaspersonalisedlearning,achievedthroughtherecommendation
waso ffoaldloewqueda tbeyl ecaorllnaibnograatcitvive ilteiaersnoinrga,p wphroeprer ikanteowlelaerdngineg grraepsohu arpcpesrofoacrhsetus dweenrtes a.pTphliisedw as
to ifmolplorwoveed gbryoucopl lakbnoorwatleivdeglee abruniilndgin,gw. hPerroebklenmow-blaesdegde lgeraarpnhinagp pwraosa cahdeospwteedr eina ptphlrieeed to
studimiepsr. oTvheegrero wuperke naolswol ead fgeewb tuyipldeisn go.f Ppreodbalgemog-yb awsehdiclhea wrneirneg uwseads aodnolyp tiend oinnet hprreaecstitcued, ies.
sucThh aesr enwetewreoraklesod alefaerwnitnygp, epsroofjepcet-dbaagseodg ylewarhniicnhgw, iemremuesresdivoe nlleyarinninong,e apnrdac ctiocgen,istuivceh as
learnneitnwgo. r kedlearning,project-basedlearning,immersivelearning,andcognitivelearning.
FiguFrige u1r2e. T12y.pTeysp oefs poefdpaegdoaggieosg sieuspspuoprpteodr tbeyd kbnyokwnloewdgleed ggreagprha paphparpoparcohaecsh. es.
5. Discussion
5. Discussion
The findings of this study illustrate the features of research and the application of
The findings of this study illustrate the features of research and the application of
knowledge graphs in education. They contribute to supplementing relevant work on
knowledge graphs in education. They contribute to supplementing relevant work on
knowledgegraphsandrevealingthecurrentstateofdevelopmentinthisareaandfuture
knowledge graphs and revealing the current state of development in this area and future
researchneeds.
research needs.
Theoverallpatternsofthepublicationscoveredinthisstudyareconsistentwiththose
The overall patterns of the publications covered in this study are consistent with
ofrelatedreviews[21,22,71]. Theyshowasharpincreaseintheamountofrelevantworkin
those of related reviews [21,22,71]. They show a sharp increase in the amount of relevant
recentyears,andmostoftheworkwascontributedbyinstitutionsinChina. Theresults
work in recent years, and most of the work was contributed by institutions in China. The
revealtherapiddevelopmentinthisarea,particularlyinChinawhereknowledgegraphs
results reveal the rapid development in this area, particularly in China where knowledge
havebeenhighlightedinitsdevelopmentplan[72]. Theresultsalsosuggestaneedfor
graphs have been highlighted in its development plan [72]. The results also suggest a need
promotinginter-regionalcollaborationsforexchangesrelevanttotheuseofknowledge
for promoting inter-regional collaborations for exchanges relevant to the use of
graphsineducationamonginstitutionsacrosscountries.
knowledge graphs in education among institutions across countries.
Intermsoftheresearchmethodsusedinthestudies,theresultsshowthepopularityof
In terms of the research methods used in the studies, the results show the popularity
quantitativemethodsfortestingtheapplicability,stability,andeffectivenessofknowledge
of quantitative methods for testing the applicability, stability, and effectiveness of
graphapplications.Commonlyusedmethodsforevaluatingtheeffectivenessofknowledge
knowledge graph applications. Commonly used methods for evaluating the effectiveness
graphapproachesineducationincludeperformanceevaluationsbasedonmetrics,user
of knowledge graph approaches in education include performance evaluations based on
experience surveys using questionnaires, and controlled experiments comparing tradi-
metrics, user experience surveys using questionnaires, and controlled experiments com-
tionalandproposedapproaches. Qualitativedatamainlyincludeperceptionsofstudents,
paring traditional and proposed approaches. Qualitative data mainly include perceptions
teachers,andexpertstowardstheknowledgegraphapproachescollectedfrominterviews,
of students, teachers, and experts towards the knowledge graph approaches collected
focusgroups,andopen-endedquestionnaires. Boththestandardisedevaluationmetrics
from interviews, focus groups, and open-ended questionnaires. Both the standardised
anduserfeedbackserveasimportantdatasourcesforassessingtheeffectsofknowledge
evaluation metrics and user feedback serve as important data sources for assessing the
graphapproachesoneducationaloutcomes.
effects oTf hkenofiwndleindggse rgergaaprdh ianpgpthroeaecdhuecsa otino nedleuvcealtsioannadl souubtjceocmtdeiss.c iplinessuggestthatknowl-
edTgheeg firanpdhinagpsp rroeagcahredsinhga vteheb eeednupcraitmioanr illyevimelps leamnde nstuedbjeacntd driessceiaprlcinheesd isnughgigehste rthedatu ca-
knotwiolnedingset igturatipohn sa,pwpirtohaachfeosc uhsavoen bceoemn ppuritmerasrciileyn icme,pmleamthenemteadt iacnsd,a rnedseeanrcghineede irnin hgi.gThheris is
educcoantsioisnte inntswtitiuthtiopnresv, iwouitshr eas feoacruchs tohna tcohmasphuigtehrl isgchietendcet,h meaadthveamntaatgicess, oafnkdn oenwgleindegeerignrga.p hs
Thiisn tihs esceonfiseilsdtesn[t2 6w].iOthv eprarlelv,itohuesr esreusletsarinchd ictahtaett hhaatsk nhoigwhlelidgghetegdr atphhes haadvveanbteaegneas ppofli ed
knoinwlaebdrgoea gdreanpihnsg isnp tehcetsreu mfieoldfss [u2b6j]e.c Otvdeisrcailpl,l tinhee sreinsurletcse inntdyiceaatres t,haantd ktnhoewreleidsgpeo gternaptihals for
havfeu rbteheenr eaxppplloireadt iionn ao fbtrhoeaidreunsienign svpaerciotruusme douf csautibojnecatl cdoisnctiepxltisn.es in recent years, and
there is pTohteenotbiajelc ftoivr efusrothfekrn eoxwplleodragteiognr oapf htheaiprp ursoea icnh evsaraiodudsr eesdsuedcaitnionthael cpounbtelixctast.i ons are
inTtihmea otebljyecltinivkeesd otfo ktnhoewirlreedsgpee cgtirvaephap applpicraotaiocnhecsa taedgdorreiesss.eFdo irne txhaem ppuleb,litchaetimonoss tacroe minm-on
timoabtejelyct liivnekoefde tnoh tahneciirn rgeskpneocwtilveed agpeprelipcaretisoenn tcaattioegnoirsieclso. sFeolyr etixeadmtoplteh, ethaep pmliocsatt icoonmcmatoegno ry
objeocftcivoen coef petnihnasntrcuinctgi oknn,owwhleicdhgew raesptrheesemntoasttiofrne qisu celnostealpyp tileicda ttioo tnh.eB aypsptlriucacttuiornin cgataengdoriyn ter-
of ccoonncneepctt iinnsgtreudcuticoanti,o wnahliccho nwcaesp tths,er melaotsito fnrsehqiupesn,ta anpdprleicsaotuiorcne. sBiyn tsotraucctouhreinregn atnkdn oinwteler-dge
congnreacptihn,gt heedsuecaaptipornoaalc choenscaeipmts,t oreplarotivoindsehaipcso, manpdr erheseonusirvceesa inndtoi nat ucoithivereernetp krnesoewnlteadtigoen of
graph, these approaches aim to provide a comprehensive and intuitive representation of
the subject matter, facilitating better understanding and learning for students. Similarly,
the objective of providing personal learning recommendations is closely associated with

Electronics2024,13,2537 14of18
thesubjectmatter,facilitatingbetterunderstandingandlearningforstudents. Similarly,the
objectiveofprovidingpersonallearningrecommendationsiscloselyassociatedwiththe
applicationcategoryofeducationalrecommendations,whichwasthesecondmostcommon
applicationcategory. Educationalrecommendationinvolvestheuseofknowledgegraphs
tosuggestcourseresources, learningpaths, oractivitiesbasedonstudents’interestsor
characteristics,whichcanhelppersonalisethelearningexperienceandimprovestudenten-
gagement. Fromtheinstructor’sperspective,theobjectiveofsupportingstaffinorganising
learningresourcesandassistingwithknowledge/coursemanagementiscloselyrelatedto
theapplicationcategoriesofknowledgemanagementandcurriculumdesignandmanage-
ment,whichutiliseknowledgegraphstoorganiseandmanageeducationalresourcesand
facilitatecoursemanagement.Overall,thefindingsregardingtheobjectivesandapplication
categoriesdemonstratethatknowledgegraphapproacheshavebeenprimarilyusedto
facilitatelearners’cognitiveprocessesandstreamlineeducationalmanagement.
Thediverserangeofresourcesutilisedinthestudieshighlightstheadaptabilityof
knowledgegraphsinaccommodatingvarioustypesofdata. Asevidencedbytheextensive
coverage of online resources, the majority of relevant work was conducted within the
contextofonlinelearning.Thismaybeduetoseveralfactors.Firstly,onlinelearningisoften
self-directedandpersonalised,withlearnerspossessingdistinctbackgrounds,interests,
and learning styles that require them to navigate and explore content independently.
Knowledge graphs can provide a visual and interactive interface that enables learners
to explore the relationships between concepts, uncover new information, and generate
customisedlearningpathsandrecommendationsbasedonlearners’interactionswiththe
system. Secondly,knowledgegraphsarescalableandcapableofhandlingvastamounts
ofdataandintricaterelationships,renderingthemwellsuitedforonlinelearning,which
frequentlyencompassesabroadrangeofsubjectsanddomains.
Awidearrayoftechnicalmeanswereidentifiedfortheimplementationofknowledge
graph applications in education. The selection of these methods was based on various
purposescoveringbuildingknowledgeontology,achievinglearningrecommendations,
and creating knowledge graphs. Consistent with previous studies, machine learning
algorithmshavebecomeincreasinglypopularforentityrecognition,relationextraction,
and concept linking [18], and collaborative filtering is a widely recognised method for
providingrecommendations[73]. Giventhemostfrequentlyidentifiedresearchprospect
ontheincorporationofnoveltechniques,approaches,andtoolstoenhancetheeffectiveness
andfunctionalityoftheproposedmodel/system,itisexpectedthatagreatervarietyof
technicalmeanswillbeemployedinfuturework.
Thefindingsalsohighlightthepotentialofknowledgegraphapproachestosupport
variouspedagogiesineducation. Personalisedlearning, whichprioritisesstudents’au-
tonomyandresponsibilityindirectingtheirownlearning,waseffectivelyfacilitatedvia
knowledge graph applications, which served to meet the diverse needs of learners by
providingthemwithtailoredinformationsuchaslearningresourcesandrecommended
courses. Knowledgegraphapproachescanalsobecommonlyemployedtosupportcollab-
orativelearningactivities,suchasgroupdiscussions,peerreview,andknowledgesharing,
byprovidingastructuredandinterconnectedrepresentationofcoursecontent.
BasedontheresultssummarisedinTable1,fourresearchlimitationsarecommonly
shownintherelevantstudiesonknowledgegraphsineducation. Firstly,thereisinsuf-
ficientinformationontheknowledgegraphconstructionprocessandmethods,making
it challenging to replicate or adapt proposed solutions to specific contexts or domains.
Secondly,thereisdifficultyinapplyingtheknowledgegraphapproachestoothersubject
areas. Aseducationaldomainsvaryintermsofaspectssuchascontent,structure,peda-
gogicalapproaches,andlearningobjectives,thetechniquesandstrategiesemployedin
constructingknowledgegraphsandextractingrelevantinformationmaybeinfluencedby
theuniquecharacteristicsandrequirementsofaspecificdomain. Additionally,thereisa
restrictedscaleandscopeoftheresourcesutilisedforknowledgegraphs. Thedatasources
areoftenconfinedtoparticularsubjectareas,educationallevels,orinstitutions,limiting

Electronics2024,13,2537 15of18
the generalisability of the resulting knowledge graphs. Moreover, many studies focus
primarilyonfactualknowledge,overlookingotheressentialaspectsofeducationsuchas
pedagogical strategies or learner profiles. Lastly, there is a lack of comprehensive user
feedbackandevaluationprocesses. Userfeedbackiscrucialforassessingtheactualimpact
andusefulnessofknowledgegraph-basedsolutionsfromtheperspectivesofeducators,
learners, and other stakeholders. Conducting iterative feedback cycles is essential for
refiningandimprovingthesolutions,ensuringtheyeffectivelyaddressdiverseeducational
requirements. These limitations should be addressed in future research to enhance the
developmentandapplicationofknowledgegraphsineducation.
6. Conclusions
Thisstudysurveyedthepublicationsonknowledgegraphineducationandsynthe-
sisedthefeaturesofrelevantresearchandpractice. Itcontributestoprovidinganoverview
ofthedevelopmentinthisareaandofferinginsightsintothepotentialofknowledgegraph
approachestosupportvariouspedagogiesineducation,aswellastheprospectsforfuture
researchinthisfield. Thefindingsaddresstheresearchquestionsofthisstudy:
RQ1: Whatarethepatternsofpublicationsonknowledgegraphsineducation? The
publicationpatternsshowarapidincreaseinrecentyears,indicatingagrowinginterestin
thisarea. Chinaistheprimarycontributor,followedbytheUnitedStates. Quantitative
methods,particularlyperformanceevaluationmetrics,aremostcommonlyused,while
qualitativeandmixedmethodsarelessprevalent.Thissuggeststhatmoreinter-institutional
andinter-regionalstudies,aswellasqualitativeapproaches,couldbeexplored.
RQ2:Whataretheeducationalcontextsofknowledgegraphapplications? Knowledge
graphapplicationsareprimarilyfocusedontertiaryeducation,withlessemphasisonthe
secondaryandprimarylevels. Theyhavebeenappliedacrossvariousdisciplines,with
computerscience,mathematics,andengineeringbeingthemostcommon.Thereispotential
forfurtherexplorationoftheuseofknowledgegraphinvariouseducationalcontexts.
RQ3: Whataretheobjectives,applicationcategories,datasources,technicalmeans,
andpedagogicalissuesforknowledgegraphapproachesandapplicationsineducation?
Themostfrequentlyaddressedobjectivesincludeenhancingknowledgerepresentation
andprovidingpersonallearningrecommendations. Thecommonapplicationsareconcept
instructionandeducationalrecommendations. Diversedatasources,suchascoursemateri-
als,studentlearningbehaviours,andonlineencyclopaedia,areusedindifferentscenarios.
Technical means are employed to deal with the purposes of building knowledge ontol-
ogy, achievingrecommendations, andcreatingknowledgegraphs. Variouspedagogies
suchaspersonalisedlearningandcollaborativelearningaresupportedbytheknowledge
graphapproaches.
The findings of this study also highlight the prospects for future work, including
incorporatingnoveltechniquesandtools,applyingknowledgegraphstootherdomains,
andexpandingdatasourcestoenhancecoverage. Addressingthelimitationsofthepresent
study, such as the small sample size and strict inclusion criteria, is essential. Future
reviewscouldexpandthesearchtocaptureabroaderrangeofpublications. Moreover,
asthissurveyonlyexaminedtheuseofknowledgegraphsineducation,futureresearch
couldalsocovertheworkonnon-educationalknowledgegraphsinordertoexaminethe
similaritiesanddifferencesbetweentheknowledgegraphinthetwoaspects,aswellas
themethodologiesandtechniquesfromnon-educationalknowledgegraphwhichcouldbe
usedintheeducationalaspect.
AuthorContributions:Conceptualization,K.Q.andK.C.L.;methodology,K.Q.,B.T.M.W.,M.M.F.W.
and M.L.; formal analysis, K.Q., B.T.M.W. and M.L.; writing—original draft preparation, K.Q.,
B.T.M.W. and M.L.; writing—review and editing, B.T.M.W. and M.L.; supervision, K.C.L. and
B.T.M.W.;projectadministration,K.Q.andM.M.F.W.;fundingacquisition,B.T.M.W.Allauthorshave
readandagreedtothepublishedversionofthemanuscript.

Electronics2024,13,2537 16of18
Funding:ThisresearchwaspartiallysupportedbyagrantfromHongKongMetropolitanUniversity
(CP/2022/04).
ConflictsofInterest:Theauthorsdeclarenoconflictofinterest.
References
1. Kejriwal,M.Knowledgegraphs:Apracticalreviewoftheresearchlandscape.Information2022,13,161.[CrossRef]
2. Hogan,A.;Blomqvist,E.;Cochez,M.;d’Amato,C.;Melo,G.D.;Gutierrez,C.;Kirrane,S.;Gayo,J.E.L.;Navigli,R.;Neumaier,S.;
etal.Knowledgegraphs.ACMComput.Surv.2021,54,71.
3. Ji,S.;Pan,S.;Cambria,E.;Marttinen,P.;Philip,S.Y.Asurveyonknowledgegraphs:Representation,acquisition,andapplications.
IEEETrans.NeuralNetw.Learn.Syst.2021,33,494–514.[CrossRef]
4. Tiddi,I.;Lécué,F.;Hitzler,P.(Eds.)KnowledgeGraphsforExplainableArtificialIntelligence:Foundations,ApplicationsandChallenges;
IOSPress:Amsterdam,TheNetherlands,2020.
5. Singhal, A. Introducing the Knowledge Graph: Things, Not Strings. Official Google Blog. 2012. Available online: https:
//blog.google/products/search/introducing-knowledge-graph-things-not/(accessedon25May2024).
6. Tiwari,S.;Al-Aswadi,F.N.;Gaurav,D.Recenttrendsinknowledgegraphs:Theoryandpractice.SoftComput.2021,25,8337–8355.
[CrossRef]
7. Wu,T.; Qi, G.; Li,C.; Wang, M.AsurveyoftechniquesforconstructingChineseknowledgegraphsandtheirapplications.
Sustainability2018,10,3245.[CrossRef]
8. Troussas,C.;Krouska,A.;Tselenti,P.;Kardaras,D.K.;Barbounaki,S.Enhancingpersonalizededucationalcontentrecommendation
throughcosinesimilarity-basedknowledgegraphsandcontextualsignals.Information2023,14,505.[CrossRef]
9. Albreiki,B.;Habuza,T.;Palakkal,N.;Zaki,N.Clustering-basedknowledgegraphsandentity-relationrepresentationimproves
thedetectionofatriskstudents.Educ.Inf.Technol.2023,29,6791–6820.[CrossRef]
10. Chung,C.Y.;Hsiao,I.H.;Lin,Y.L.AI-assistedprogrammingquestiongeneration:Constructingsemanticnetworksofprogramming
knowledgebylocalknowledgegraphandabstractsyntaxtree.J.Res.Technol.Educ.2023,55,94–110.[CrossRef]
11. Limongelli,C.;Lombardi,M.;Marani,A.;Taibi,D.Asemanticapproachtorankingtechniques:Improvingwebpagesearchesfor
educationalpurposes.IEEEAccess2022,10,68885–68896.[CrossRef]
12. Shang,S.;Lyv,W.;Luo,L.Applyingleansixsigmaincorporatedwithbigdataanalysistocurriculumsystemimprovementin
highereducationinstitutions.Int.J.Syst.Assur.Eng.Manag.2022,13,641–656.
13. Zablith,F.Constructingsocialmedialinkstoformallearning:Aknowledgegraphapproach.Educ.Technol.Res.Dev.2022,70,
559–584.[CrossRef]
14. Mzwri,K.;Turcsányi-Szabo,M.Internetwizardforenhancingopen-domainquestion-answeringchatbotknowledgebasein
education.Appl.Sci.2023,13,8114.[CrossRef]
15. Choi,H.;Lee,H.;Lee,M.Optimalknowledgecomponentextractingmodelforknowledge-conceptgraphcompletionineducation.
IEEEAccess2023,11,15002–15013.[CrossRef]
16. Yuan,R.;Li,H.;Sun,Z.;Zhang,H.Applicationofgraphconvolutionalnetworkintheconstructionofknowledgegraphfor
highermathematicsteaching.Sens.Mater.2023,35,4269–4290.[CrossRef]
17. Xiao,X.;Fang,Z.;Zou,S.;Zhang,C.;Chen,X.Effectsofanintelligentcuesrecognition-basedmultilevelknowledgegraphs
generationmethodonstudentsinonlinelearningenvironments.Interact.Learn.Environ.2023.[CrossRef]
18. Abu-Salih,B.;Alotaibi,S.Asystematicliteraturereviewofknowledgegraphconstructionandapplicationineducation.Heliyon
2024,10,e25383.[CrossRef][PubMed]
19. Elkaimbillah, Z.; Rhanoui, M.; Mikram, M.; El Asri, B. Comparative study of knowledge graph models in education do-
main.InProceedingsoftheInternationalConferenceonBigdata,ModellingandMachineLearning,Cox’sBazar,Bangladesh,
23–25September2021.
20. Fettach, Y.; Ghogho, M.; Benatallah, B. Knowledge graphs in education and employability: A survey on applications and
techniques.IEEEAccess2022,10,80174–80183.[CrossRef]
21. Chen,X.;Xie,H.;Li,Z.;Cheng,G.Topicanalysisanddevelopmentinknowledgegraphresearch:Abibliometricreviewonthree
decades.Neurocomputing2021,461,497–515.[CrossRef]
22. Wang,G.;He,J.Abibliometricanalysisofrecentdevelopmentsandtrendsinknowledgegraphresearch(2013–2022).IEEEAccess
2024,12,32005–32013.[CrossRef]
23. Wang,Q.;Mao,Z.;Wang,B.;Guo,L.Knowledgegraphembedding:Asurveyofapproachesandapplications.IEEETrans.Knowl.
DataEng.2017,29,2724–2743.[CrossRef]
24. Rajabi,E.;Etminani,K.Knowledge-graph-basedexplainableAI:Asystematicreview.J.Inf.Sci.2022.[CrossRef]
25. Tian,L.;Zhou,X.;Wu,Y.P.;Zhou,W.T.;Zhang,J.H.;Zhang,T.S.Knowledgegraphandknowledgereasoning: Asystematic
review.J.Electron.Sci.Technol.2022,20,100159.[CrossRef]
26. Abu-Salih,B.Domain-specificknowledgegraphs:Asurvey.J.Netw.Comput.Appl.2021,185,103076.[CrossRef]
27. Chiu,B.;See-To,W.K.E.;Ngai,E.W.T.Knowledgegraphconstructionandapplicationsine-retailing:Areviewofliterature.In
ProceedingsofthePacificAsianConferenceonInformationSystems,Virtual,12July2021;p.244.

Electronics2024,13,2537 17of18
28. Wang,S.;Lin,M.;Ghosal,T.;Ding,Y.;Peng,Y.Knowledgegraphapplicationsinmedicalimaginganalysis:Ascopingreview.
HealthDataSci.2022,2022,9841548.[CrossRef][PubMed]
29. Abu-Salih,B.;Al-Qurishi,M.;Alweshah,M.;AL-Smadi,M.Healthcareknowledgegraphconstruction:State-of-the-art,open
issues,andopportunities.arXiv2022,arXiv:2207.03771.
30. Li,K.C.;Wong,B.T.M.Reviewofsmartlearning:Patternsandtrendsinresearchandpractice.Australas.J.Educ.Technol.2021,37,
189–204.[CrossRef]
31. Jardim,J.;Bártolo,A.;Pinho,A.Towardsaglobalentrepreneurialculture:Asystematicreviewoftheeffectivenessofentrepreneur-
shipeducationprograms.Educ.Sci.2021,11,398.[CrossRef]
32. Alonso,R.K.;Vélez,A.;Martínez-Monteagudo,M.C.;Rico-González,M.Flippedlearninginhighereducationforthedevelopment
ofintrinsicmotivation:Asystematicreview.Educ.Sci.2023,13,1226.[CrossRef]
33. Paneque,M.;delMarRoldán-García,M.;García-Nieto,J.e-LION:Dataintegrationsemanticmodeltoenhancepredictiveanalytics
ine-Learning.ExpertSyst.Appl.2023,213,118892.[CrossRef]
34. Zheng,L.;Kinshuk;Fan,Y.;Long,M.Theimpactsofthecomprehensivelearninganalyticsapproachonlearningperformancein
onlinecollaborativelearning.Educ.Inf.Technol.2023,28,16863–16886.[CrossRef]
35. Zheng,L.;Niu,J.;Long,M.;Fan,Y.Anautomaticknowledgegraphconstructionapproachtopromotingcollaborativeknowledge
building,groupperformance,socialinteractionandsociallysharedregulationinCSCL.Br.J.Educ.Technol.2023,54,686–711.
[CrossRef]
36. Zheng,L.;Long,M.;Chen,B.;Fan,Y.Promotingknowledgeelaboration,sociallysharedregulation,andgroupperformancein
collaborativelearning:Anautomatedassessmentandfeedbackapproachbasedonknowledgegraphs.Int.J.Educ.Technol.High.
Educ.2023,20,46.[CrossRef]
37. Han,D.;Kim,D.;Kim,M.;Han,K.;Yi,M.Y.Temporalenhancedinductivegraphknowledgetracing. Appl. Intell. 2023,53,
29282–29299.[CrossRef]
38. Troussas,C.;Krouska,A.Path-basedrecommendersystemforlearningactivitiesusingknowledgegraphs.Information2023,14,9.
[CrossRef]
39. Yang, Y.; Chen, S.; Zhu, Y.; Zhu, H.; Chen, Z. Knowledge graph empowerment from knowledge learning to graduation
requirementsachievement.PLoSONE2023,18,e0292903.[CrossRef][PubMed]
40. Ain,Q.U.;Chatti,M.A.;Bakar,K.G.C.;Joarder,S.;Alatrash,R.AutomaticConstructionofEducationalKnowledgeGraphs:A
WordEmbedding-BasedApproach.Information2023,14,526.[CrossRef]
41. Sin,Z.P.; Jia,Y.; Wu,A.C.; Zhao,I.D.; Li,R.C.; Ng,P.H.; Baciu,G.; Cao,J.; Li,Q.Towardsanedu-metaverseofknowledge:
Immersiveexplorationofuniversitycourses.IEEETrans.Learn.Technol.2023,16,1096–1110.[CrossRef]
42. Hu,Y.;Xu,B.AnalysisofthedilemmaofhighervocationalthinkingeducationinChinaunderthebackgroundof“Internet+”.
Appl.Math.NonlinearSci.2024,9,1–15.[CrossRef]
43. Zhang,W.;ChungEe,J.Y.AnIntelligentKnowledgeGraph-BasedDirectionalDataClusteringandFeatureSelectionforImproved
Education.Int.J.RecentInnov.TrendsComput.Commun.2023,11,22–33.[CrossRef]
44. Liu,C.;Zhang,J.;Zhang,H.;Li,X.;Zhang,E.GroupCooperativeTeachingDesignwithKnowledgeGraphsinProject-Driven
Learning.Int.J.Inf.Commun.Technol.Educ.2023,19,1–11.[CrossRef]
45. Nguyen,H.D.;Truong,D.;Vu,S.;Nguyen,D.;Nguyen,H.;Tran,N.T.Knowledgemanagementforinformationqueryingsystem
ineducationviathecombinationofrela-opsmodelandknowledgegraph.J.CasesInf.Technol.2023,25,1–17.[CrossRef]
46. Nguyen,H.D.;Huynh,H.;Mai,T.DesignanOntology-basedmodelforIntelligentQueryingsysteminMathematicsEducation.J.
Interdiscip.Math.2023,26,449–473.[CrossRef]
47. Coccoli,M.;Torre,I.;Galluccio,I.UserexperienceevaluationofEdurellinterfaceforvideoaugmentation.Multimed.ToolsAppl.
2024,83,36695–36717.[CrossRef]
48. Liu,J.Y.;Wang,F.;Ma,H.P.;Huang,Z.Y.;Liu,Q.;Chen,E.H.;Su,Y.AProbabilisticFrameworkforTemporalCognitiveDiagnosis
inOnlineLearningSystems.J.Comput.Sci.Technol.2023,38,1203–1222.[CrossRef]
49. Agrawal,G.;Deng,Y.;Park,J.;Liu,H.;Chen,Y.C.Buildingknowledgegraphsfromunstructuredtexts:Applicationsandimpact
analysesincybersecurityeducation.Information2022,13,526.[CrossRef]
50. Weichselbraun,A.; Waldvogel,R.; Fraefel,A.; vanSchie,A.; Kuntschik,P.BuildingKnowledgeGraphsandRecommender
SystemsforSuggestingReskillingandUpskillingOptionsfromtheWeb.Information2022,13,510.[CrossRef]
51. Li,N.;Shen,Q.;Song,R.;Chi,Y.;Xu,H.MEduKG:Adeep-learning-basedapproachformulti-modaleducationalknowledge
graphconstruction.Information2022,13,91.[CrossRef]
52. Keshan,N.;Fontaine,K.;Hendler,J.A.Semiautomatedprocessforgeneratingknowledgegraphsformarginalizedcommunity
doctoral-recipients.Int.J.WebInf.Syst.2022,18,413–431.[CrossRef]
53. Yang,S.;Cai,X.Bilateralknowledgegraphenhancedonlinecourserecommendation.Inf.Syst.2022,107,102000.[CrossRef]
54. Ezaldeen,H.;Bisoy,S.K.;Misra,R.;Alatrash,R.Semantics-awarecontext-basedlearnermodellingusingnormalizedPSOfor
personalizedE-learning.J.WebEng.2022,21,1187–1224.[CrossRef]
55. Wu,Z.;Jia,F.ConstructionandApplicationofaMajor-SpecificKnowledgeGraphBasedonBigDatainEducation.Int.J.Emerg.
Technol.Learn.2022,17,64–79.[CrossRef]
56. Zhong,M.;Ding,R.Designofapersonalizedrecommendationsystemforlearningresourcesbasedoncollaborativefiltering.Int.
J.CircuitsSyst.SignalProcess.2022,16,122–131.[CrossRef]

Electronics2024,13,2537 18of18
57. Nafa,F.;Babour,A.;Melton,A.Prerequisiterelationsamongknowledgeunits:Acasestudyofcomputersciencedomain.Comput.
Model.Eng.Sci.2022,133,639–652.[CrossRef]
58. Hou,Q.DesignofaVisualTrainingSystemforSoftwareEngineeringEducationBasedonKnowledgeGraphs. Int. J.Emerg.
Technol.Learn.2022,17,114–130.[CrossRef]
59. Liu,P.;Cao,Y.;Wang,L.AMultimodalFusionOnlineMusicEducationSystemforUniversities.Comput.Intell.Neurosci.2022,
2022,6529110.[CrossRef]
60. Badawy,A.;Fisteus,J.A.;Mahmoud,T.M.;AbdEl-Hafeez,T.Topicextractionandinteractiveknowledgegraphsforlearning
resources.Sustainability2021,14,226.[CrossRef]
61. Martin,A.J.;Dominic,M.M.Personalizationoflearningobjectsaccordingtotheskillsetofthelearnerusingknowledgegraph.
Turk.J.Comput.Math.Educ.2021,12,3974–3987.
62. Yang,Z.;Wang,Y.;Gan,J.;Li,H.;Lei,N.Designandresearchofintelligentquestion-answering(Q&A)systembasedonhigh
schoolcourseknowledgegraph.Mob.Netw.Appl.2021,26,1884–1890.
63. Hur,Y.;Jo,J.DevelopmentofIntelligentInformationSystemforDigitalCulturalContents.Mathematics2021,9,238.[CrossRef]
64. Lv,P.;Wang,X.;Xu,J.;Wang,J.Intelligentpersonalisedexerciserecommendation:Aweightedknowledgegraph-basedapproach.
Comput.Appl.Eng.Educ.2021,29,1403–1419.[CrossRef]
65. Xu,G.;Jia,G.;Shi,L.;Zhang,Z.Personalizedcourserecommendationsystemfusingwithknowledgegraphandcollaborative
filtering.Comput.Intell.Neurosci.2021,2021,9590502.[CrossRef]
66. Zhang,Z.Amethodofrecommendingphysicaleducationnetworkcourseresourcesbasedoncollaborativefilteringtechnology.
Sci.Program.2021,2021,9531111.[CrossRef]
67. Cui,J.;Yu,S.Fosteringdeeperlearninginaflippedclassroom:Effectsofknowledgegraphsversusconceptmaps.Br.J.Educ.
Technol.2019,50,2308–2328.[CrossRef]
68. Telnov,V.;Korovin,Y.Semanticwebandknowledgegraphsasaneducationaltechnologyofpersonneltrainingfornuclearpower
engineering.Nucl.EnergyTechnol.2019,5,273–280.[CrossRef]
69. Chi,Y.;Qin,Y.;Song,R.;Xu,H.Knowledgegraphinsmarteducation:Acasestudyofentrepreneurshipscientificpublication
management.Sustainability2018,10,995.[CrossRef]
70. Chen,P.;Lu,Y.;Zheng,V.W.;Chen,X.;Yang,B.Knowedu:Asystemtoconstructknowledgegraphforeducation.IEEEAccess
2018,6,31553–31563.[CrossRef]
71. Shen,T.;Nagai,Y.;Zhao,J.;Shen,T.Hotspotsandtrendsinknowledgegraphandconceptgenerationbasedonbibliometric
analysis.InProceedingsofthe2020InternationalConferenceonIntelligentDesign(ICID),Xi’an,China,11–13December2020;
IEEE:Piscataway,NJ,USA,2020;pp.124–127.
72. StateCouncil.NewGenerationofArtificialIntelligenceDevelopmentPlan.2017.Availableonline:https://flia.org/wp-content/
uploads/2017/07/A-New-Generation-of-Artificial-Intelligence-Development-Plan-1.pdf(accessedon25May2024).
73. Grad-Gyenge,L.; Kiss,A.; Filzmoser,P.Graphembeddingbasedrecommendationtechniquesontheknowledgegraph. In
ProceedingsoftheAdjunctPublicationofthe25thConferenceonUserModeling,AdaptationandPersonalization,Bratislava,
Slovakia,9–12July2017;pp.354–359.
Disclaimer/Publisher’sNote: Thestatements, opinionsanddatacontainedinallpublicationsaresolelythoseoftheindividual
author(s)andcontributor(s)andnotofMDPIand/ortheeditor(s).MDPIand/ortheeditor(s)disclaimresponsibilityforanyinjuryto
peopleorpropertyresultingfromanyideas,methods,instructionsorproductsreferredtointhecontent.