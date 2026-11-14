# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019Natur.575..459M\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
## **Observation of inverse Compton emission from a long** γ -ray burst

V. A. Acciari [1], S. Ansoldi [2] _[,]_ [3], L. A. Antonelli [4], A. Arbet Engels [5], D. Baack [6], A. Babi´c [7],


B. Banerjee [8], U. Barres de Almeida [9], J. A. Barrio [10], J. Becerra Gonz´alez [1], W. Bednarek [11],


L. Bellizzi [12], E. Bernardini [13] _[,]_ [14], A. Berti [15], J. Besenrieder [16], W. Bhattacharyya [13], C. Bigongiari [4],


A. Biland [5], O. Blanch [17], G. Bonnoli [12], Z. Boˇsnjak [ˇ] [7], G. Busetto [14], R. Carosi [18], G. Ceribella [16],


Y. Chai [16], A. Chilingaryan [19], S. Cikota [7], S. M. Colak [17], U. Colin [16], E. Colombo [1], J. L. Contreras [10],


J. Cortina [20], S. Covino [4], V. D’Elia [4], P. Da Vela [18], F. Dazzi [4], A. De Angelis [14], B. De Lotto [2],


M. Delfino [17] _[,]_ [21], J. Delgado [17] _[,]_ [21], D. Depaoli [15], F. Di Pierro [15], L. Di Venere [15], E. Do Souto


Espi˜neira [17], D. Dominis Prester [22], A. Donini [2], D. Dorner [23], M. Doro [14], D. Elsaesser [6], V. Fallah


Ramazani [24], A. Fattorini [6], G. Ferrara [4], D. Fidalgo [10], L. Foffano [14], M. V. Fonseca [10], L. Font [25],


C. Fruck [16], S. Fukami [26], R. J. Garc´ıa L´opez [1], M. Garczarczyk [13], S. Gasparyan [27], M. Gaug [25],


N. Giglietto [15], F. Giordano [15], N. Godinovi´c [28], D. Green [16], D. Guberman [17], D. Hadasch [26],


A. Hahn [16], J. Herrera [1], J. Hoang [10], D. Hrupec [29], M. H¨utten [16], T. Inada [26], S. Inoue [30], K. Ishio [16],


Y. Iwamura [26], L. Jouvin [17], D. Kerszberg [17], H. Kubo [3], J. Kushida [31], A. Lamastra [4], D. Lelas [28],


F. Leone [4], E. Lindfors [24], S. Lombardi [4], F. Longo [2] _[,]_ [32] _[,]_ [33], M. L´opez [10], R. L´opez-Coto [14],


A. L´opez-Oramas [1], S. Loporchio [15], B. Machado de Oliveira Fraga [9], C. Maggio [25], P. Majumdar [8],


M. Makariev [34], M. Mallamaci [14], G. Maneva [34], M. Manganaro [22], K. Mannheim [23], L. Maraschi [4],


M. Mariotti [14], M. Mart´ınez [17], D. Mazin [16] _[,]_ [26], S. Mi´canovi´c [22], D. Miceli [2], M. Minev [34],


J. M. Miranda [12], R. Mirzoyan [16], E. Molina [35], A. Moralejo [17], D. Morcuende [10], V. Moreno [25],


E. Moretti [17], P. Munar-Adrover [25], V. Neustroev [36], C. Nigro [13], K. Nilsson [24], D. Ninci [17],


1

K. Nishijima [31], K. Noda [26], L. Nogu´es [17], S. Nozaki [3], S. Paiano [14], M. Palatiello [2], D. Paneque [16],


R. Paoletti [12], J. M. Paredes [35], P. Pe˜nil [10], M. Peresano [2], M. Persic [2], P. G. Prada Moroni [18],


E. Prandini [14], I. Puljak [28], W. Rhode [6], M. Rib´o [35], J. Rico [17], C. Righi [4], A. Rugliancich [18], L. Saha [10],


N. Sahakyan [27], T. Saito [26], S. Sakurai [26], K. Satalecka [13], K. Schmidt [6], T. Schweizer [16], J. Sitarek [11],


I. Snidari´c [ˇ] [37], D. Sobczynska [11], A. Somero [1], A. Stamerra [4], D. Strom [16], M. Strzys [16], Y. Suda [16],


T. Suri´c [37], M. Takahashi [26], F. Tavecchio [4], P. Temnikov [34], T. Terzi´c [22] _[,]_ [37], M. Teshima [16] _[,]_ [26],


N. Torres-Alb`a [35], L. Tosti [15], V. Vagelli [15], J. van Scherpenberg [16], G. Vanzo [1], M. Vazquez Acosta [1],


C. F. Vigorito [15], V. Vitale [15], I. Vovk [16], M. Will [16], D. Zari´c [28]


L. Nava [4] _[,]_ [32] _[,]_ [38],


P. Veres [39], P. N. Bhat [39], M. S. Briggs [39] _[,]_ [40], W. H. Cleveland [41], R. Hamburg [39] _[,]_ [40], C. M. Hui [42],


B. Mailyan [39], R. D. Preece [39] _[,]_ [40], O. Roberts [41], A. von Kienlin [43], C. A. Wilson-Hodge [42],


D. Kocevski [42], M. Arimoto [44], D. Tak [45] _[,]_ [46], K. Asano [47], M. Axelsson [48] _[,]_ [49], G. Barbiellini [32],


E. Bissaldi [50] _[,]_ [51], F. Fana Dirirsa [52], R. Gill [53], J. Granot [53], J. McEnery [45] _[,]_ [46], N. Omodei [54] _[,]_ [55],


S. Razzaque [52], F. Piron [56], J. L. Racusin [46], D. J. Thompson [46],


S. Campana [57], M. G. Bernardini [57], N. P. M. Kuin [58], M. H. Siegel [59], S. Bradley Cenko [46] _[,]_ [60], P.


OBrien [61], M. Capalbi [62], A. DA`ı [62], M. De Pasquale [63], J. Gropp [59], N. Klingler [59], J. P. Osborne [61],


M. Perri [64] _[,]_ [65], R. Starling [61], G. Tagliaferri [57] _[,]_ [62], A. Tohuvavohu [59],


A. Ursi [66], M. Tavani [66] _[,]_ [67] _[,]_ [68], M. Cardillo [66], C. Casentini [66], G. Piano [66], Y. Evangelista [66],


F. Verrecchia [64] _[,]_ [65], C. Pittori [64] _[,]_ [65], F. Lucarelli [64] _[,]_ [65], A. Bulgarelli [65], N. Parmiggiani [65],


2

G. E. Anderson [69], J. P. Anderson [70], G. Bernardi [71] _[,]_ [72] _[,]_ [73], J. Bolmer [43], M. D. Caballero-Garc´ıa [74],


I. M. Carrasco [75], A. Castell´on [76], N. Castro Segura [77], A. J. Castro-Tirado [78] _[,]_ [79], S. V. Cherukuri [80],


A. M. Cockeram [81], P. D’Avanzo [57], A. Di Dato [82] _[,]_ [83], R. Diretse [84], R.P. Fender [85],


E. Fern´andez-Garc´ıa [79], J. P. U. Fynbo [86] _[,]_ [87], A.S. Fruchter [88] J. Greiner [43], M. Gromadzki [89], K.E.


Heintz [90] I. Heywood [72] _[,]_ [85], A.J. van der Horst [91] _[,]_ [92], Y.-D. Hu [79] _[,]_ [93], C. Inserra [94], L. Izzo [79] _[,]_ [95],


V. Jaiswal [80], P. Jakobsson [90], J. Japelj [96], E. Kankare [97], D. A. Kann [79], C. Kouveliotou [91] _[,]_ [92],


S. Klose [98], A. J. Levan [99], X. Y. Li [100] _[,]_ [101], S. Lotti [66], K. Maguire [102], D. B. Malesani [86] _[,]_ [87] _[,]_ [95] _[,]_ [103],


I. Manulis [104], M. Marongiu [105] _[,]_ [106], S. Martin [70] _[,]_ [107], A. Melandri [57], M. Michałowski [108],


J.C.A. Miller-Jones [69], K. Misra [109] _[,]_ [110], A. Moin [111], K.P. Mooley [112] _[,]_ [113], S. Nasri [111],


M. Nicholl [114] _[,]_ [115], A. Noschese [82], G. Novara [116] _[,]_ [117], S. B. Pandey [109], E. Peretti [68] _[,]_ [118], C. J. P´erez del


Pulgar [78], M.A. P´erez-Torres [79] _[,]_ [119], D. A. Perley [81], L. Piro [66], F. Ragosta [83] _[,]_ [120] _[,]_ [121], L. Resmi [80],


R. Ricci [71] A. Rossi [122], R. S´anchez-Ram´ırez [66], J. Selsing [87] S. Schulze [123], S. J. Smartt [124],


I. A. Smith [125], V. V. Sokolov [126], J. Stevens [127], N. R. Tanvir [61], C. C. Th´one [79], A. Tiengo [116] _[,]_ [117] _[,]_ [128],


E. Tremou [129], E. Troja [46] _[,]_ [130], A. de Ugarte Postigo [79] _[,]_ [95], A. F. Valeev [126], S. D. Vergani [131],


M. Wieringa [132], P.A. Woudt [84], D. Xu [133], O. Yaron [104], D. R. Young [124]


1 _Inst._ _de_ _Astrof´ısica_ _de_ _Canarias,_ _E-38200_ _La_ _Laguna,_ _and_ _Universidad_ _de_ _La_ _Laguna,_ _Dpto._


_Astrof´ısica, E-38206 La Laguna, Tenerife, Spain_


2 _Universit`a di Udine, and INFN Trieste, I-33100 Udine, Italy_


3 _Japanese MAGIC Consortium, Department of Physics, Kyoto University, Kyoto, Japan._


4 _National Institute for Astrophysics (INAF), I-00136 Rome, Italy_


5 _ETH Zurich, CH-8093 Zurich, Switzerland_


3

6 _Technische Universit¨at Dortmund, 44221 Dortmund, Germany_


7 _Croatian Consortium, University of Zagreb, FER, Zagreb, Croatia._


8 _Saha Institute of Nuclear Physics, HBNI, 1/AF Bidhannagar, Salt Lake, Sector-1, Kolkata 700064,_


_India_


9 _Centro Brasileiro de Pesquisas F´ısicas (CBPF), 22290-180 URCA, Rio de Janeiro (RJ), Brasil_


10 _Unidad_ _de_ _Part´ıculas_ _y_ _Cosmolog´ıa_ _(UPARCOS),_ _Universidad_ _Complutense,_ _E-28040_ _Madrid,_


_Spain_


11 _University_ _of_ _Lodz,_ _Faculty_ _of_ _Physics_ _and_ _Applied_ _Informatics,_ _Department_ _of_ _Astrophysics,_


_90-236 Lodz, Poland_


12 _Universit`a di Siena and INFN Pisa, I-53100 Siena, Italy_


13 _Deutsches Elektronen-Synchrotron (DESY), 15738 Zeuthen, Germany_


14 _Universit`a di Padova and INFN, I-35131 Padova, Italy_


15 _Istituto Nazionale Fisica Nucleare (INFN), 00044 Frascati (Roma) Italy_


16 _Max-Planck-Institut f¨ur Physik, 80805 M¨unchen, Germany_


17 _Institut_ _de_ _F´ısica_ _d’Altes_ _Energies_ _(IFAE),_ _The_ _Barcelona_ _Institute_ _of_ _Science_ _and_ _Technology_


_(BIST), E-08193 Bellaterra (Barcelona), Spain_


18 _Universit`a di Pisa, and INFN Pisa, I-56126 Pisa, Italy_


19 _The Armenian Consortium, A. Alikhanyan National Laboratory, Yerevan, Armenia._


20 _Centro_ _de_ _Investigaciones_ _Energ´eticas,_ _Medioambientales_ _y_ _Tecnol´ogicas,_ _E-28040_ _Madrid,_


_Spain_


21 _also at Port d’Informaci´o Cient´ıfica (PIC) E-08193 Bellaterra (Barcelona) Spain_


4

22 _Croatian Consortium, Department of Physics, University of Rijeka, Rijeka, Croatia._


23 _Universit¨at W¨urzburg, 97074 W¨urzburg, Germany_


24 _Finnish_ _MAGIC_ _Consortium,_ _Finnish_ _Centre_ _of_ _Astronomy_ _with_ _ESO_ _(FINCA),_ _University_ _of_


_Turku, Turku, Finland._


25 _Departament_ _de_ _F´ısica,_ _and_ _CERES-IEEC,_ _Universitat_ _Aut`onoma_ _de_ _Barcelona,_ _E-08193_ _Bel-_


_laterra, Spain_


26 _Japanese MAGIC Consortium, ICRR, The University of Tokyo, Kashiwa, Japan._


27 _The Armenian Consortium, ICRANet-Armenia at NAS RA, Yerevan, Armenia._


28 _Croatian Consortium, University of Split, FESB, Split, Croatia._


29 _Croatian Consortium, Josip Juraj Strossmayer University of Osijek, Osijek, Croatia._


30 _Japanese MAGIC Consortium, RIKEN, Wako, Japan._


31 _Japanese MAGIC Consortium, Tokai University, Hiratsuka, Japan_


32 _Istituto Nazionale di Fisica Nucleare, Sezione di Trieste, 34149 Trieste, Italy_


33 _also at Dipartimento di Fisica, Universit`a di Trieste, 34127 Trieste, Italy_


34 _Inst._ _for_ _Nucl._ _Research_ _and_ _Nucl._ _Energy,_ _Bulgarian_ _Academy_ _of_ _Sciences,_ _BG-1784_ _Sofia,_


_Bulgaria_


35 _Universitat de Barcelona, ICCUB, IEEC-UB, E-08028 Barcelona, Spain_


36 _Finnish MAGIC Consortium, Astronomy Research Unit, University of Oulu, Oulu, Finland._


37 _Croatian Consortium, Rudjer Boskovic Institute, Zagreb, Croatia._


38 _Institute for Fundamental Physics of the Universe (IFPU), 34151 Trieste, Italy_


39 _Center_ _for_ _Space_ _Plasma_ _and_ _Aeronomic_ _Research,_ _University_ _of_ _Alabama_ _in_ _Huntsville,_ _320_


5

_Sparkman Drive, Huntsville, AL 35899, USA_


40 _Space_ _Science_ _Department,_ _University_ _of_ _Alabama_ _in_ _Huntsville,_ _320_ _Sparkman_ _Drive,_


_Huntsville, AL 35899, USA_


41 _Science_ _and_ _Technology_ _Institute,_ _Universities_ _Space_ _Research_ _Association,_ _Huntsville,_ _AL_


_35805, USA_


42 _Astrophysics Office, ST12, NASA/Marshall Space Flight Center, Huntsville, AL 35812, USA_


43 _Max-Planck_ _Institut_ _f¨ur_ _extraterrestrische_ _Physik,_ _Giessenbachstraße_ _1,_ _85748_ _Garching,_ _Ger-_


_many_


44 _Faculty of Mathematics and Physics, Institute of Science and Engineering, Kanazawa University,_


_Kakuma, Kanazawa, Ishikawa 920-1192_


45 _Department of Physics, University of Maryland, College Park, MD 20742-4111, USA_


46 _Astrophysics Science Division, NASA Goddard Space Flight Center, 8800 Greenbelt Rd, Green-_


_belt, MD 20771, USA_


47 _Institute for Cosmic-Ray Research,_ _University of Tokyo,_ _5-1-5 Kashiwanoha,_ _Kashiwa,_ _Chiba,_


_277-8582, Japan_


48 _Department of Physics, Stockholm University, AlbaNova, SE-106 91 Stockholm, Sweden_


49 _Department of Physics, KTH Royal Institute of Technology, AlbaNova, SE-106 91 Stockholm,_


_Sweden_


50 _Dipartimento di Fisica “M. Merlin” dell’Universit`a e del Politecnico di Bari, 70126 Bari, Italy_


51 _Istituto Nazionale di Fisica Nucleare, Sezione di Bari, 70126 Bari, Italy_


52 _Department_ _of_ _Physics,_ _University_ _of_ _Johannesburg,_ _PO_ _Box_ _524,_ _Auckland_ _Park_ _2006,_ _South_


6

_Africa_


53 _Department_ _of_ _Natural_ _Sciences,_ _Open_ _University_ _of_ _Israel,_ _1_ _University_ _Road,_ _POB_ _808,_


_Ra’anana 43537, Israel_


54 _W._ _W._ _Hansen_ _Experimental_ _Physics_ _Laboratory,_ _Kavli_ _Institute_ _for_ _Particle_ _Astrophysics_ _and_


_Cosmology._


55 _Department_ _of_ _Physics_ _and_ _SLAC_ _National_ _Accelerator_ _Laboratory,_ _Stanford_ _University,_ _Stan-_


_ford, CA 94305, USA_


56 _Laboratoire Univers et Particules de Montpellier, Universit´e Montpellier, CNRS/IN2P3, F-34095_


_Montpellier, France_


57 _INAF - Astronomical Observatory of Brera, I-23807 Merate (LC), Italy_


58 _Mullard_ _Space_ _Science_ _Laboratory,_ _University_ _College_ _London,_ _Holmbury_ _St._ _Mary,_ _Dorking,_


_RH5 6NT, United Kingdom_


59 _Department of Astronomy and Astrophysics, Pennsylvania State University._ _525 Davey Labora-_


_tory, University Park, PA 16802, USA_


60 _Joint Space-Science Institute, University of Maryland, College Park, Maryland 20742, USA_


61 _Department of Physics and Astronomy, University of Leicester, University Road, Leicester LE1_


_7RH, UK_


62 _INAF_ _Istituto_ _di_ _Astrofisica_ _Spaziale_ _e_ _Fisica_ _Cosmica_ _di_ _Palermo,_ _via_ _Ugo_ _La_ _Malfa_ _153,_ _I-_


_90146 Palermo, Italia_


63 _Department_ _of_ _Astronomy_ _and_ _Space_ _Sciences,_ _Istanbul_ _University,_ _Fatih,_ _34119,_ _Istanbul,_


_Turkey_


7

64 _INAF-Osservatorio Astronomico di Roma, Via Frascati 33, I-00078 Monteporzio Catone, Italy_


65 _Space Science Data Center (SSDC), Agenzia Spaziale Italiana (ASI), via del Politecnico s.n.c.,_


_I-00133, Roma, Italy_


66 _INAF-IAPS, via del Fosso del Cavaliere 100, I-00133 Roma, Italy_


67 _Univ._ _“Tor Vergata”, Via della Ricerca Scientifica 1, I-00133 Roma, Italy_


68 _Gran Sasso Science Institute, viale Francesco Crispi 7, I-67100 L’Aquila, Italy_


69 _International Centre for Radio Astronomy Research, Curtin University, GPO Box U1987, Perth,_


_WA 6845, Australia_


70 _European Southern Observatory, Alonso de C`ordova, 3107, Vitacura, Santiago 763-0355, Chile_


71 _INAF-Istituto di Radioastronomia, via Gobetti 101, I-40129, Bologna, Italy_


72 _Department_ _of_ _Physics_ _and_ _Electronics,_ _Rhodes_ _University,_ _PO_ _Box_ _94,_ _Grahamstown,_ _6140,_


_South Africa_


73 _South African Radio Astronomy Observatory, Black River Park, 2 Fir Street, Observatory, Cape_


_Town, 7925, South Africa_


74 _Astronomical_ _Institute_ _of_ _the_ _Academy_ _of_ _Sciences,_ _Boˇcn´ı_ _II_ _1401,_ _CZ-14100_ _Praha_ _4,_ _Czech_


_Republic_


75 _Departamento de F´ısica Aplicada, Facultad de Ciencias, Universidad de M´alaga, Bulevar Louis_


_Pasteur 31, E-29071 M´alaga, Spain_


76 _Departamento de_ _´Algebra, Geometr´ıa y Topolog´ıa, Facultad de Ciencias, Bulevar Louis Pasteur_


_31, Universidad de M´alaga, E-29071 M´alaga, Spain_


77 _Physics and Astronomy Department, University of Southampton, Southampton, UK_


8

78 _Unidad_ _Asociada_ _Departamento_ _de_ _Ingenier´ıa_ _de_ _Sistemas_ _y_ _Autom´atica,_ _E.T.S._ _de_ _Ingenieros_


_Industriales, Universidad de M´alaga, Arquitecto Francisco Pe˜nalosa 6, E-29071 M´alaga, Spain_


79 _Instituto_ _de_ _Astrof´ısica_ _de_ _Andaluc´ıa_ _(IAA-CSIC),_ _Glorieta_ _de_ _la_ _Astronom´ıa,_ _s/n,_ _E-18008,_


_Granada, Spain_


80 _Indian Institute of Space Science & Technology, Trivandrum 695547, India_


81 _Astrophysics Research Institute, Liverpool John Moores University, 146 Brownlow Hill, Liver-_


_pool L3 5RF, UK_


82 _Osservatorio Astronomico ’S. Di Giacomo’ - AstroCampania, I-80051, Agerola (NA), Italy_


83 _INAF - Astronomical Observatory of Naples, I-23807 Naples (NA), Italy_


84 _Inter-University_ _Institute_ _for_ _Data-Intensive_ _Astronomy,_ _Department_ _of_ _Astronomy,_ _University_


_of Cape Town, Private Bag X3, Rondebosch 7701, South Africa_


85 _Astrophysics, Department of Physics, University of Oxford, Keble Road, Oxford OX1 3RH, UK_


86 _Cosmic Dawn Center (DAWN)_


87 _Niels Bohr Institute, Copenhagen University, Vibenshuset, Lyngbyvej 2, DK-2100, Copenhagen_


88 _Space Telescope Science Institute, 3700 San Martin Drive, Baltimore, MD 21218, USA_


89 _Astronomical_ _Observatory,_ _University_ _of_ _Warsaw,_ _Al._ _Ujazdowskie_ _4,_ _PL-00-_ _478_ _Warszawa,_


_Poland_


90 _Centre for Astrophysics and Cosmology, Science Institute, University of Iceland, Dunhagi 5, 107_


_Reykjav´ık, Iceland_


91 _Department_ _of_ _Physics,_ _The_ _George_ _Washington_ _University,_ _725_ _21st_ _Street_ _NW,_ _Washington,_


_DC 20052, USA_


9

92 _Astronomy, Physics, and Statistics Institute of Sciences (APSIS), The George Washington Uni-_


_versity, Washington, DC 20052, USA_


93 _Universidad_ _de_ _Granada,_ _Facultad_ _de_ _Ciencias_ _Campus_ _Fuentenueva_ _S/N_ _CP_ _18071_ _Granada,_


_Spain_


94 _School of Physics & Astronomy, Cardiff University, Queens Buildings, The Parade, 25 Cardiff,_


_CF24 3AA, UK_


95 _DARK, Niels Bohr Institute, University of Copenhagen, Lyngbyvej 2, DK-2100 Copenhagen Ø,_


_Denmark_


96 _Anton_ _Pannekoek_ _Institute_ _for_ _Astronomy,_ _University_ _of_ _Amsterdam,_ _Science_ _Park_ _904,_ _1098_


_XH Amsterdam, The Netherlands_


97 _Tuorla Observatory, Department of Physics and Astronomy, University of Turku, 20014 Turku,_


_Finland_


98 _Th¨uringer Landessternwarte Tautenburg, Sternwarte 5, 07778 Tautenburg, Germany_


99 _Department of Astrophysics/IMAPP, Radboud University Nijmegen, The Netherlands_


100 _Instituto de Hortofruticultura Subtropical y Mediterr´anea La Mayora (IHSM/UMA-CSIC), Al-_


_garrobo Costa s/n, E-29750 M´alaga, Spain_


101 _Nanjing_ _Institute_ _for_ _Astronomical_ _Optics_ _and_ _Technology,_ _National_ _Observatories,_ _Chinese_


_Academy of Sciences, 188 Bancang St, Xuanwu Qu, Nanjing Shi, Jiangsu Sheng, China_


102 _School of Physics, Trinity College Dublin, Dublin 2, Ireland_


103 _DTU Space,_ _National Space Institute,_ _Technical University of Denmark,_ _Elektrovej 327,_ _2800_


_Kongens Lyngby, Denmark_


10

104 _Benoziyo Center for Astrophysics, Weizmann Institute of Science, 76100 Rehovot, Israel_


105 _Department of Physics and Earth Science, University of Ferrara, via Saragat 1, I-44122, Ferrara,_


_Italy_


106 _International_ _Center_ _for_ _Relativistic_ _Astrophysics_ _Network_ _(ICRANet),_ _Piazzale_ _della_ _Repub-_


_blica 10, I-65122, Pescara, Italy_


107 _Joint ALMA Observatory, Alonso de C`ordova, 3107, Vitacura, Santiago 763-0355, Chile_


108 _Astronomical_ _Observatory_ _Institute,_ _Faculty_ _of_ _Physics,_ _Adam_ _Mickiewicz_ _University,_


_ul. Słoneczna 36, 60-286 Pozna´n, Poland_


109 _Aryabhatta Research Institute of Observational Sciences, Manora Peak, Nainital 263 001, India_


110 _Department of Physics, University of California, 1 Shields Ave, Davis, CA 95616-5270, USA_


111 _Physics_ _Department,_ _United_ _Arab_ _Emirates_ _University,_ _P.O._ _Box_ _15551,_ _Al-Ain,_ _United_ _Arab_


_Emirates_


112 _National Radio Astronomy Observatory, 1003 Lopezville Road, Socorro, NM 87801, USA_


113 _Caltech, 1200 California Blvd., Pasadena, CA 91106, USA_


114 _Institute for Astronomy, University of Edinburgh, Royal Observatory, Blackford Hill, EH9 3HJ,_


_UK_


115 _Birmingham Institute for Gravitational Wave Astronomy and School of Physics and Astronomy,_


_University of Birmingham, Birmingham B15 2TT, UK_


116 _Scuola Universitaria Superiore IUSS Pavia, Piazza della Vittoria 15, 27100 Pavia, Italy_


117 _INAF - IASF Milano, Via E. Bassini 15, 20133 Milano, Italy_


118 _INFN / Laboratori Nazionali del Gran Sasso, Via G. Acitelli 22, 67100, Assergi (AQ), Italy_


11

119 _Depto._ _de F´ısica Te´orica, Universidad de Zaragoza, E-50019, Zaragoza, Spain_


120 _Dipartimento di Scienze Fisiche, Universit degli studi di Napoli Federico II, Via Cinthia, Edifi-_


_cio N, 80126 Napoli, Italy_


121 _INFN,_ _Sezione_ _di_ _Napoli,_ _Complesso_ _Universitario_ _di_ _Monte_ _S._ _Angelo,_ _Via_ _Cinthia,_ _Edificio_


_N, 80126 Napoli, Italy_


122 _INAF_ _-_ _Osservatorio_ _di_ _Astrofisica_ _e_ _Scienza_ _dello_ _Spazio,_ _via_ _Piero_ _Gobetti_ _93/3,_ _40129_


_Bologna, Italy_


123 _Department_ _of_ _Particle_ _Physics_ _and_ _Astrophysics,_ _Weizmann_ _Institute_ _of_ _Science,_ _Rehovot_


_76100, Israel_


124 _Astrophysics Research Centre, School of Mathematics and Physics, Queen?s University Belfast,_


_Belfast BT7 1NN, UK_


125 _Department of Physics and Astronomy,_ _Rice University,_ _6100 South Main,_ _MS-108,_ _Houston,_


_TX 77251-1892, USA_


126 _Special_ _Astrophysical_ _Observatory,_ _Nizhniy_ _Arkhyz,_ _Zelenchukskiy_ _region,_ _Karachai-_


_Cherkessian Republic, 369167, Russia_


127 _CSIRO Australia Telescope National Facility, Paul Wild Observatory, Narrabri NSW 2390, Aus-_


_tralia_


128 _Istituto Nazionale di Fisica Nucleare, Sezione di Pavia, Via Bassi 6, 27100 Pavia, Italy_


129 _AIM,_ _CEA,_ _CNRS,_ _Universit´e_ _Paris_ _Diderot,_ _Sorbonne_ _Paris_ _Cit´e,_ _Universit´e_ _Paris-Saclay,_ _F-_


_91191 Gif-sur-Yvette, France_


130 _Department of Astronomy, University of Maryland, College Park, MD 20742-4111, USA_


12

131 _GEPI,_ _Observatoire_ _de_ _Paris,_ _PSL_ _University,_ _CNRS,_ _5_ _Place_ _Jules_ _Janssen,_ _92190_ _Meudon,_


_France_


132 _Australia Telescope National Facility, CSIRO Astronomy and Space Science, PO Box 76, Ep-_


_ping, NSW 1710, Australia_


133 _CAS Key Laboratory of Space Astronomy and Technology, National Astronomical Observato-_


_ries, Chinese Academy of Sciences, Beijing 100012, China_


**Long-duration gamma-ray bursts (GRBs) originate from ultra-relativistic jets launched from**


**the** **collapsing** **cores** **of** **dying** **massive** **stars.** **They** **are** **characterised** **by** **an** **initial** **phase** **of**


**bright and highly variable radiation in the keV-MeV band that is likely produced within the**


**jet and lasts from milliseconds to minutes,** **known as the prompt emission** **[1,2]** **.** **Subsequently,**


**the interaction of the jet with the external medium generates external shock waves, respon-**


**sible** **for** **the** **afterglow** **emission,** **which** **lasts** **from** **days** **to** **months,** **and** **occurs** **over** **a** **broad**


**energy range,** **from the radio to the GeV bands** **[1–6]** **.** **The afterglow emission is generally well**


**explained** **as** **synchrotron** **radiation** **by** **electrons** **accelerated** **at** **the** **external** **shock** **[7–9]** **.** **Re-**


**cently, an intense, long-lasting emission between 0.2 and 1 TeV was observed from the GRB**


**190114C** **[10]** **.** **Here** **we** **present** **the** **results** **of** **our** **multi-frequency** **observational** **campaign** **of**


**GRB 190114C, and study the evolution in time of the GRB emission across 17 orders of mag-**


**nitude** **in** **energy,** **from** 5 _×_ 10 _[−]_ [6] **up** **to** 10 [12] **eV.** **We** **find** **that** **the** **broadband** **spectral** **energy**


**distribution is double-peaked, with the TeV emission constituting a distinct spectral compo-**


**nent** **that** **has** **power** **comparable** **to** **the** **synchrotron** **component.** **This** **component** **is** **associ-**


**ated** **with** **the** **afterglow,** **and** **is** **satisfactorily** **explained** **by** **inverse** **Compton** **upscattering** **of**


13

**synchrotron photons by high-energy electrons.**


**We** **find** **that** **the** **conditions** **required** **to** **account** **for** **the** **observed** **TeV** **component** **are** **not**


**atypical, supporting the possibility that inverse Compton emission is commonly produced in**


**GRBs.**


On 14 January 2019, following an alert from the Neil Gehrels Swift Observatory (here

after _Swift_ ) and the _Fermi_ satellite, the Major Atmospheric Gamma Imaging Cherenkov (MAGIC)


telescopes observed and detected radiation up to at least 1 TeV from GRB 190114C. Before the


MAGIC detection, GRB emission has only been reported at much lower energies, ≲ 100 GeV, first


by _CGRO_ /EGRET in a handful of cases, and more recently by _AGILE_ /GRID and _Fermi_ /LAT (see


11 for a recent review).


Detection of TeV radiation opens a new window in the electromagnetic spectrum for the


study of GRBs [10] . Its announcement [12] triggered an extensive campaign of follow-up observations.


Owing to the relatively low redshift _z_ = 0 _._ 4245 _±_ 0 _._ 0005 (see Methods) of the GRB (corresponding


to a luminosity distance of _∼_ 2 _._ 3 Gpc) a comprehensive set of multi-wavelength data could be


collected. We present observations gathered from instruments onboard six satellites and 15 ground


telescopes (radio, submm and NIR/optical/UV and very high energy gamma-rays; see Methods)


for the first ten days after the burst. The frequency range covered by these observations spans more


than 17 orders of magnitude, from 1 to _∼_ 2 _×_ 10 [17] GHz, the most extensive to date for a GRB. The


light curves of GRB 190114C at different frequencies are shown in Fig. 1.


The prompt emission of GRB 190114C was simultaneously observed by several space mis

14

Figure 1: **Multi-wavelength light curves of GRB 190114C.** Energy flux at different wavelengths,


from radio to gamma-rays, versus time since the BAT trigger time _T_ 0 = 20:57:03.19 UT on 14


January 2019. The light curve for the energy range 0.3-1 TeV (green circles) is compared with


light curves at lower frequencies. Those for VLA (yellow square), ATCA (yellow stars), ALMA


(orange circles), GMRT (purple filled triangle), and MeerKAT (purple empty triangles) have been


multiplied by 10 [9] for clarity. The vertical dashed line marks approximately the end of the prompt


emission phase, identified with the end of the last flaring episode. For the data points, vertical bars


show the 1- _σ_ errors on the flux, while horizontal bars represent the duration of the observation.


15

sions (see Methods), covering the spectral range from 8 keV to _∼_ 100 GeV. The prompt light curve


shows a complex temporal structure, with several emission peaks (Methods; Extended Data Fig. 1),


with total duration _∼_ 25 s (see dashed line in Fig. 1) and total radiated energy _E_ _γ,_ iso = (2.5 _±_ 0.1)


_×_ 10 [53] ergs (isotropic equivalent, in the energy range 1 _−_ 10 [4] keV [13] ). During the time of inter-burst


quiescence at _t_ _∼_ [5 _−_ 15] seconds and after the end of the last prompt pulse at _t_ ≳ 25 s, the flux


decays smoothly, following a power law in time _F_ _∝_ _t_ _[α]_, with _α_ 10 _−_ 1000keV = _−_ 1 _._ 10 _±_ 0 _._ 01 [13] . The


temporal and spectral characteristics of this smoothly varying component support an interpretation


in terms of afterglow synchrotron radiation, making this one of the few clear cases of afterglow


emission detected in the band 10 _−_ 10 [4] keV during the prompt emission phase. The onset of the


afterglow component is then estimated to occur around _t ∼_ 5 _−_ 10 s [13,14], implying an initial bulk


Lorentz factor between 300 and 700 (Methods).


After about one minute from the start of the prompt emission, two additional high-energy


telescopes began observations: MAGIC and _Swift_ /XRT. The XRT and MAGIC light curves (1

10 keV, blue data points in Fig. 1, and 0.3-1 TeV, green data points, respectively) decay with time as


a power law, and display the following decay rates: _α_ X _∼−_ 1 _._ 36 _±_ 0 _._ 02 and _α_ TeV _∼−_ 1 _._ 51 _±_ 0 _._ 04.


The 0.3-1 TeV light curve shown in Fig. 1 was obtained after correcting for attenuation by the


extragalactic background light (EBL) [10] . The TeV-band emission is observable until _∼_ 40 minutes,


which is much longer than the nominal duration of the prompt emission phase. The NIR-optical


light curves (square symbols) show a more complex behaviour. Initially, a fast decay is seen,


where the emission is most likely dominated by the reverse shock component [15] . This is followed


by a shallower decay, and subsequently a faster decay at _t_ ≳ 10 [5] s. The latter behaviour might


16

indicate that the characteristic synchrotron frequency _ν_ m is crossing the optical band (Extended


Data Fig. 6), which is not atypical, but usually occurs at earlier times. The relatively late time at


which the break appears in GRB 190114C would then imply a very large value of _ν_ m, placing it in


the X-ray band at _∼_ 10 [2] s. The millimeter light curves (orange symbols) also show an initial fast


decay where the emission is dominated by the reverse shock, followed by emission at late times


with nearly constant flux (Extended Data Fig. 3).


The spectral energy distributions (SEDs) of the radiation detected by MAGIC are shown in


Fig. 2, where the whole duration of the emission detected by MAGIC is divided into five time in

tervals. For the first two time intervals, observations in the GeV and X-ray bands are also available.


During the first time interval (68-110 s, blue data points and blue confidence regions), _Swift_ /XRT

BAT and _Fermi_ /GBM data show that the afterglow synchrotron component is peaking in the X-ray


band. At higher energies, up to ≲1 GeV, the SED is a decreasing function of energy, as supported


by the _Fermi_ /LAT flux between 0.1 and 0.4 GeV (see Methods). On the other hand, at even higher


energies, the MAGIC flux above 0.2 TeV implies a spectral hardening. This evidence is indepen

dent of the EBL model adopted to correct for the attenuation (Methods). This demonstrates that


the newly discovered TeV radiation is not a simple extension of the known afterglow synchrotron


emission, but rather a separate spectral component that has never been clearly seen before.


The extended duration and the smooth, power-law temporal decay of the radiation detected


by MAGIC (see green data points in Fig. 1) suggest an intimate connection between the TeV


emission and the broadband afterglow emission. The most natural candidate is synchrotron self

17

Compton (SSC) radiation in the external forward shock: the same population of relativistic elec

trons responsible for the afterglow synchrotron emission Compton upscatters the synchrotron pho

tons, leading to a second spectral component that peaks at higher energies. TeV afterglow emission


can also be produced by hadronic processes such as synchrotron radiation by protons accelerated


to ultra-high energies in the forward shock [16–18] . However, due to their typically low efficiency


of radiation [6], reproducing the luminous TeV emission as observed here by such processes would


imply unrealistically large power in accelerated protons [10] . TeV photons can also be produced via


the SSC mechanism in internal shock synchrotron models of the prompt emission. However, nu

merical modeling (Methods) shows that prompt SSC radiation can account at most for a limited


fraction ( _[<]_ _∼_ [20][%][)] [of] [the] [observed] [TeV] [flux,] [and] [only] [at] [early] [times] [(] _[t]_ [≲] [100][ s).] [Henceforth,] [we]


focus on the SSC process in the afterglow.


SSC emission has been predicted for GRB afterglows [9,11,17,19–26] . However, its quantitative


significance was uncertain, as the SSC luminosity and spectral properties depend strongly on the


poorly constrained physical conditions in the emission region (e.g., the magnetic field strength).


The detection of the TeV component in GRB 190114C and the availability of multi-band obser

vations offer the opportunity to investigate the relevant physics at a deeper level. SSC radiation


might have been already detected in very bright GRBs, such as GRB 130427A. Photons with ener

gies 10-100 GeV, as those detected in GRB 130427A are challenging to explain by the synchrotron


processes, suggesting a different origin [27–29] .


We model the full data set (from radio band to TeV energies, for the first week after the


18

Figure 2: **Multi-band** **spectra** **in** **the** **time** **interval** **68-2400 s** . Five time intervals are consid

ered: 68-110 s (blue), 110-180 s (yellow), 180-360 s (red), 360-625 s (green), 625-2400 s (purple).


MAGIC data points have been corrected for attenuation caused by the extragalactic background


light. Data from other instruments are shown for the first two time-intervals: _Swift_ /XRT, _Swift_ /BAT,


_Fermi_ /GBM, and _Fermi_ /LAT. For each time interval, LAT contour regions are shown limiting the


energy range to the range where photons are detected. MAGIC and LAT contour regions are drawn


from the 1- _σ_ error of their best-fit power law functions. For _Swift_ data, the regions show the 90%


confidence contours for the joint fit XRT-BAT obtained fitting to the data a smoothly broken power


law. Filled regions are used for the first time interval (68-110 s, blue color).


19

Figure 3: **Modeling** **of** **the** **broadband** **spectra** **in** **the** **time** **intervals** **68-110 s** **and** **110-180 s.**


Thick blue curve: modeling of the multi-band data in the synchrotron and SSC afterglow scenario.


Thin solid lines: synchrotron and SSC (observed spectrum) components; dashed lines: SSC if


internal _γ_ - _γ_ opacity is neglected. The adopted parameters are: _s_ = 0, _ϵ_ e = 0 _._ 07, _ϵ_ B = 8 _×_ 10 _[−]_ [5],


_p_ = 2 _._ 6, _n_ 0 = 0 _._ 5, and _E_ k = 8 _×_ 10 [53] erg, see the Text. Empty circles show the observed MAGIC


spectrum, i.e. not corrected by attenuation caused by the extragalactic background light. Contour


regions and data points as in Fig. 2.


20

explosion) as synchrotron plus SSC radiation, within the framework of the theory of afterglow


emission from external forward shocks. The detailed modeling of the broadband emission and


its evolution with time is presented in Section Methods. We discuss here the implications for the


emission at _t <_ 2400 s and energies above _>_ 1 keV.


The soft spectra in the 0.2-1 TeV energy range (photon index Γ TeV _< −_ 2; see Extended Data


Table 1) constrain the peak of the SSC component to be below this energy range. The relatively


small ratio between the spectral peak energies of the SSC ( _E_ p [SSC] ≲ 200 GeV) and synchrotron


( _E_ p [syn] _∼_ 10 keV) components implies a relatively low value for the Lorentz factor of the electrons


( _γ_ _∼_ 2 _×_ 10 [3] ). This value is hard to reconcile with the observation of the synchrotron peak


at ≳ keV energies. In order to explain the soft spectrum detected by MAGIC, it is necessary to


invoke the Klein-Nishina (KN) regime scattering for the electrons radiating at the spectral peak as


well as internal _γ_ - _γ_ absorption [30] . While both effects tend to become less important with time, the


spectral index in the 0.2-1 TeV band remains constant in time (or possibly evolves to softer values;


Extended Data Table 1). This implies that the SSC peak energy is moving to lower energies and


crossing the MAGIC energy band. The energy at which attenuation by internal pair production


becomes important indicates that the bulk Lorentz factor is _∼_ 140-160 at 100 s.


An example of the theoretical modeling in this scenario is shown in Fig. 3 (blue solid curve,


see Methods for details). The dashed line shows the SSC spectrum when internal absorption is


neglected. The thin solid line shows the model spectrum including EBL attenuation, in comparison


to the MAGIC observations (empty circles).


21

We find that acceptable models of the broadband SED can be obtained if the conditions at


the source are the following. The initial kinetic energy of the blastwave is _E_ k ≳ 3 _×_ 10 [53] erg


(isotropic-equivalent). The electrons swept up from the external medium are efficiently injected


into the acceleration process, and carry a fraction _ϵ_ e _∼_ 0 _._ 05 _−_ 0 _._ 15 of the energy dissipated at


the shock. The acceleration mechanism produces an electron population characterized by a non

thermal energy distribution, described by a power law with index _p ∼_ 2 _._ 4 _−_ 2 _._ 6, injection Lorentz


factor _γ_ m = (0 _._ 8 _−_ 2) _×_ 10 [4] and maximum Lorentz factor _γ_ max _∼_ 10 [8] (at _∼_ 100 s). The magnetic


field behind the shock conveys a fraction _ϵ_ B _∼_ (0 _._ 05 _−_ 1) _×_ 10 _[−]_ [3] of the dissipated energy. At


_t_ _∼_ 100 s, corresponding to _R_ _∼_ (8 _−_ 20) _×_ 10 [16] cm, the density of the external medium is


_n_ _∼_ 0 _._ 5 _−_ 5 cm _[−]_ [3], and the magnetic field strength is _B_ _∼_ 0 _._ 5 _−_ 5 Gauss. The latter implies that


the magnetic field was efficiently amplified from values of a few _µ_ Gauss that are typical of the


unshocked ambient medium, due to plasma instabilities or other mechanisms [6] . Not surprisingly,


we find that _ϵ_ e _≫_ _ϵ_ B, that is a necessary condition for the efficient production of SSC radiation [17,19] .


The blastwave energy inferred from the modeling is comparable to the amount of energy


released in the form of radiation during the prompt phase. The prompt emission mechanism must


then have dissipated and radiated no more than half of the initial jet energy, leaving the other half


available for the afterglow phase. The modeling of the multi-band data also allows us to infer how


the total energy is shared between the synchrotron and the SSC components. The resultant power


in the two components are comparable. We estimate that the energy in the synchrotron and SSC


component are _∼_ 1 _._ 5 _×_ 10 [52] erg and _∼_ 6 _._ 0 _×_ 10 [51] erg respectively in the time interval 68-110 s, and


_∼_ 1 _._ 3 _×_ 10 [52] erg and _∼_ 5 _._ 4 _×_ 10 [51] erg respectively in the time interval 110-180 s. Thus, previous


22

studies of GRBs may have been missing a significant fraction of the energy emitted during the


afterglow phase that is essential to its understanding.


Finally, we note that the values of the afterglow parameters inferred from the modeling fall


within the range of values typically inferred from broadband (radio-to-GeV) studies of GRB af

terglow emission. This points to the possibility that SSC emission in GRBs may be a relatively


common process that does not require special conditions to be produced with power similar to


synchrotron radiation.


The SSC component may then be detectable at TeV energies in other relatively energetic


GRBs, as long as the redshift is low enough to avoid severe attenuation by the EBL. This also


provides support to earlier indications for SSC emission at GeV energies [27–29] .


23

**Methods**


**Prompt** **emission** **observations** On 14 January 2019, the prompt emission from GRB 190114C


triggered several space instruments, including _Fermi_ /GBM [31], _Fermi_ /LAT [32], _Swift_ /BAT [33], Super

AGILE [34], _AGILE_ /MCAL [34], _KONUS_ /Wind [35], _INTEGRAL_ /SPI-ACS [36], and _Insight_ /HXMT [37] . The


prompt emission light curves from _AGILE_, _Fermi_, and _Swift_ are shown in Fig. 1 and in Ex

tended Data Fig. 1, where the trigger time _T_ 0 (here and elsewhere) refers to the BAT trigger time


(20:57:03.19 UT). The prompt emission lasts approximately for 25 s, where the last flaring emis

sion episode ends. Nominally, the _T_ 90, i.e. the time interval during which a fraction between


5% and 95% of the total emission is observed, is much longer ( _>_ 100 s, depending on the instru

ment [13] ), but is clearly contaminated by the afterglow component (Fig. 1) and does not provide a


good measure of the actual duration of the prompt emission. A more detailed study of the prompt


emission phase is reported in [13] .


**AGILE** (The Astrorivelatore Gamma ad Immagini LEggero [38] ) could observe GRB 190114C until


_T_ 0 +330 s, before it became occulted by the Earth. GRB 190114C triggered the Mini-CALorimeter


(MCAL) from T0 _−_ 0.95 s to T0+10.95 s. The MCAL light flux curve in Fig. 1 has been pro

duced using two different spectral models. From _T_ 0 _−_ 0.95 s to _T_ 0 +1.8 s, the spectrum is fit

ted by a power law with photon index Γ ph = -1.97 [+0] _−_ 0 _[.]_ _._ [47] 70 [(] _[dN/dE]_ _[∝]_ _[E]_ [Γ] [ph] [).] [From] _[T]_ [0] [+][1.8 s] [to]


_T_ 0 + 5 _._ 5 s the best fit model is a broken power law with Γ ph _,_ 1 = _−_ 1 _._ 87 [+0] _−_ 0 _[.]_ _._ [54] 19 [,][ Γ] [ph] _[,]_ [2] [=] _[−]_ [2] _[.]_ [63] [+0] _−_ 0 _[.]_ _._ [07] 07 [,]


and break energy _E_ b =756 [+137] _−_ 159 [keV.] [The] [total] [fluence] [in] [the] [0.4] _[−]_ [100 MeV] [energy] [range] [is] _[F]_ [=]


1 _._ 75 _×_ 10 _[−]_ [4] erg cm _[−]_ [2] . The Super-AGILE detector also detected the burst, but the large off-axis


angle prevented any X-ray imaging of the burst, as well as spectral analysis. Panels **a**, **d**, and **e**


24

Extended Data Figure 1: **Prompt** **emission** **light** **curves** **for** **different** **detectors.** The differ

ent panels show light curves for: **a**, SuperAGILE (20-60 keV); **b**, _Swift_ /BAT (15-150 keV); **c**,


_Fermi_ /GBM (10-1000 keV); **d**, _AGILE_ /MCAL (0.4-1.4 MeV); **e**, _AGILE_ /MCAL (1.4-100 MeV);


**f**, _Fermi_ /LAT (0.1-10 GeV). The light curve of _AGILE_ /MCAL is split into two bands to show the


energy dependence of the first peak. Error bars show the 1- _σ_ statistical errors.


25

in Extended Data Fig. 1 show the GRB 190114C light curves acquired by the Super-AGILE de

tector (20 _−_ 60 keV) and by the MCAL detector in the low- (0 _._ 4 _−_ 1 _._ 4 MeV) and high-energy


(1 _._ 4 _−_ 100 MeV) bands.


_**Fermi**_ **/GBM** At the time of the MAGIC observations there are indications that some of the de

tectors are partially blocked by structure on the _Fermi_ Spacecraft that is not modeled in the GBM


detectors’ response. This affects the low-energy part of the spectrum [39] . For this reason, out of cau

tion we elected to exclude the energy channels below 50 keV. The spectra detected by the _Fermi_ 

Gamma-ray Burst Monitor (GBM) [40] during the _T_ 0 +68 s to _T_ 0 +110 s and _T_ 0 +110 s to _T_ 0 +180 s


intervals are best described by a power law model with photon index Γ ph = _−_ 2 _._ 10 _±_ 0 _._ 08 and


Γ ph = _−_ 2 _._ 05 _±_ 0 _._ 10 respectively (Fig. 2 and Fig. 3). The 10-1000 keV light curve in Extended


Data Fig. 1 (panel **c** ) was constructed by summing photon counts for the bright NaI detectors.


_**Swift**_ **/BAT** The 15 _−_ 350 keV mask-weighted light curve of the Burst Alert Telescope (BAT [41] )


shows a multi-peaked structure that starts at _T_ 0 _−_ 7 s (Extended Data Fig. 1, panel **b** ). The 68 _−_ 110 s


and 110 _−_ 180 s spectra shown in Figs. 2 and 3 were derived from joint XRT-BAT fit. The best

fitting parameters for the whole interval (68 _−_ 180 s) are: column density _N_ H = (7 _._ 53 [+0] _−_ 1 _._ _[.]_ [74] 74 [)] _[ ×]_


10 [22] cm _[−]_ [2] at _z_ = 0 _._ 42, in addition to the galactic value of 7 _._ 5 _×_ 10 [19] cm _[−]_ [2], low-energy photon index


Γ ph _,_ 1 = _−_ 1 _._ 21 [+0] _−_ 1 _[.]_ _._ [40] 26 [, high-energy spectral index][ Γ] [ph] _[,]_ [2] [=] _[−]_ [2] _[.]_ [19] [+0] _−_ 0 _[.]_ _._ [39] 19 [, peak energy] _[ E]_ [pk] _[>]_ [14] _[.]_ [5][ keV.]


Errors are given at 90% confidence level.


_**Fermi**_ **/LAT** The _Fermi_ Large Area Telescope (LAT) [42] detected a gamma-ray counterpart since


the prompt phase [43] . The burst left the LAT field of view (FoV) at _T_ 0 +150 s and remained outside


26

the LAT FoV until _T_ 0 +8600 s. The count light curve in the energy range 0.1-10 GeV is shown


in Extended Data Fig. 1 (panel **f** ). The LAT spectra in the time bins 68–110 s and 110–180 s


(Figs. 2 and 3) are described by a power law with pivot energies of, respectively, 200 MeV and


500 MeV, photon indices Γ ph (68 _−_ 110) = _−_ 2 _._ 02 _±_ 0 _._ 95 and Γ ph (110 _−_ 180) = _−_ 1 _._ 69 _±_ 0 _._ 42,


and corresponding normalisations of _N_ 0 _,_ 68 _−_ 110 = (2 _._ 02 _±_ 1 _._ 31) _×_ 10 _[−]_ [7] ph MeV _[−]_ [1] cm _[−]_ [2] s and


_N_ 0 _,_ 110 _−_ 180 = (4 _._ 48 _±_ 2 _._ 10) _×_ 10 _[−]_ [8] ph MeV _[−]_ [1] cm _[−]_ [2] s. In each time-interval, the analysis has been


performed limited to the energy range where photons have been detected. The LAT light curve


integrated in the energy range 0.1-1 GeV is shown in Fig. 1.


**MAGIC** We used the Major Atmospheric Gamma Imaging Cherenkov (MAGIC) standard soft

ware [44] and followed the steps optimised for the data taking under moderate moon illumination [45]


to analyse the data. The spectral fitting is performed by a forward-folding method assuming a


simple power law for the intrinsic spectrum and taking into account the extragalactic background


light (EBL) effect using the model of Dom´ınguez et al. [46] . Extended Data Table 1 shows the fitting


results for various time bins (the pivot energy is chosen to minimise the correlation between nor

malisation and photon index parameters). The data points shown in both Fig. 2 and 3 are obtained


from the observed excess rates in estimated energy whose fluxes are evaluated in true energy using


effective time and a spill-over corrected effective area obtained as a resultant of the best fit.


The time resolved analysis hints to a possible spectral evolution to softer values. Although


we can not exclude that the photon indices are compatible with a constant value of _∼−_ 2 _._ 5 up to


2400 s. The signal and background in the considered time bins are both in the low-count Poisson


regime. Therefore, the correct treatment of the MAGIC data provided here includes along with the


27

Time bin Normalisation Photon index Pivot energy


[ seconds after _T_ 0 ] [ TeV _[−]_ [1] cm _[−]_ [2] s _[−]_ [1] ] [GeV]


62 - 90 1 _._ 95 [+0] _−_ 0 _[.]_ _._ [21] 20 _[·]_ [ 10] _[−]_ [7] _−_ 2 _._ 17 [+0] _−_ 0 _[.]_ _._ [34] 36 395 _._ 5


68 - 180 1 _._ 10 [+0] _−_ 0 _[.]_ _._ [09] 08 _[·]_ [ 10] _[−]_ [7] _−_ 2 _._ 27 [+0] _−_ 0 _[.]_ _._ [24] 25 404 _._ 7


180 - 625 2 _._ 26 [+0] _−_ 0 _[.]_ _._ [21] 20 _[·]_ [ 10] _[−]_ [8] _−_ 2 _._ 56 [+0] _−_ 0 _[.]_ _._ [27] 29 395 _._ 5


68 - 110 1 _._ 74 [+0] _−_ 0 _[.]_ _._ [16] 15 _[·]_ [ 10] _[−]_ [7] _−_ 2 _._ 16 [+0] _−_ 0 _[.]_ _._ [29] 31 386 _._ 5


110 - 180 8 _._ 59 [+0] _−_ 0 _[.]_ _._ [95] 91 _[·]_ [ 10] _[−]_ [8] _−_ 2 _._ 51 [+0] _−_ 0 _[.]_ _._ [37] 41 395 _._ 5


180 - 360 3 _._ 50 [+0] _−_ 0 _[.]_ _._ [38] 36 _[·]_ [ 10] _[−]_ [8] _−_ 2 _._ 36 [+0] _−_ 0 _[.]_ _._ [34] 37 395 _._ 5


360 - 625 1 _._ 65 [+0] _−_ 0 _[.]_ _._ [23] 23 _[·]_ [ 10] _[−]_ [8] _−_ 3 _._ 16 [+0] _−_ 0 _[.]_ _._ [48] 54 369 _._ 1


625 - 2400 3 _._ 52 [+0] _−_ 0 _[.]_ _._ [47] 47 _[·]_ [ 10] _[−]_ [9] _−_ 2 _._ 80 [+0] _−_ 0 _[.]_ _._ [48] 54 369 _._ 1


62 - 2400 (Nominal MC) 1 _._ 07 [+0] _−_ 0 _[.]_ _._ [08] 07 _[·]_ [ 10] _[−]_ [8] _−_ 2 _._ 51 [+0] _−_ 0 _[.]_ _._ [20] 21 423 _._ 8


62 - 2400 (Light scale +15% MC) 7 _._ 95 [+0] _−_ 0 _[.]_ _._ [58] 56 _[·]_ [ 10] _[−]_ [9] _−_ 2 _._ 91 [+0] _−_ 0 _[.]_ _._ [23] 25 369 _._ 1


62 - 2400 (Light scale -15% MC) 1 _._ 34 [+0] _−_ 0 _[.]_ _._ [09] 09 _[·]_ [ 10] _[−]_ [8] _−_ 2 _._ 07 [+0] _−_ 0 _[.]_ _._ [18] 19 509 _._ 5


Extended Data Table 1: **MAGIC spectral fit parameters for GRB 190114C.** For each time


bin, columns represent a) start time and end time of the bin; b) normalisation of the EBL

corrected differential flux at the pivot energy with statistical errors; c) photon indices with


statistical errors; d) pivot energy of the fit (fixed).


28

use of the Poisson statistic also the systematic errors. To estimate the main source of systematic


error caused by our imperfect knowledge of the absolute instrument calibration and the total at

mospheric transmission we vary the light-scale in our Monte Carlo (MC) simulation as suggested


in previous studies [44] . The result is reported in the last two lines of Extended Data Table 1 and in


Extended Data Fig. 2.


The systematic effects deriving from the choice of one particular EBL model were also stud

ied. The analysis performed to obtain the time integrated spectrum was repeated employing other


three models [47–49] . The contribution to the systematic error on the photon index caused by the un

certainty on the EBL model is _σ_ _α_ = [+0] _−_ 0 _[.]_ _._ [10] 13 [which is smaller than the statistical error only (1 standard]


deviation) as already seen in a previous work [10] . On the other hand, the contribution to the system

atic error on the normalisation, due to choice of the EBL model, is only partially at the same level


of the statistical error (1 standard deviation) _σ_ _N_ = [+0] _−_ 0 _[.]_ _._ [30] 08 _[×]_ [10] _[−]_ [8] [.] [The chosen EBL model returns a]


lower normalisation with respect to two of the other models and very close to the third one [47] .


The MAGIC energy flux light curve that is presented in Fig. 1 was obtained by integrating


the best fit spectral model of each time bin from 0.3 to 1 TeV, in the same manner as a previous


publication [10] . The value of the fitted time constant reported here differs less than two standard


deviation from the one previously reported [10] . The difference is due to the poor constraints on the


spectral fit parameters of the last time bin, which influences the light curve fit.


29

Extended Data Figure 2: **MAGIC** **time** **integrated** **spectral** **energy** **distributions** **in** **the** **time**


**interval** **62-2400 s** **after** _T_ 0 **.** The green (yellow, blue) points and band show the result with the


nominal (+15%, -15%) light scale MC, defining the limits of the systematic uncertainties. The


contour regions are drawn from the 1- _σ_ error of their best-fit power law functions. The vertical


bars of the data points show the 1- _σ_ errors on the flux.


30

**X-ray afterglow observations**


_**Swift**_ **/XRT** The _Swift_ X-Ray Telescope (XRT) started observing 68 s after _T_ 0 . The source light


curve [50] was taken from the _Swift_ /XRT light curve repository [51] and converted into 1-10 keV flux


(Fig. 1) through dedicated spectral fits. The combined spectral fit XRT+BAT in Figs. 2 and 3 has


been described above.


_**XMM-Newton**_ **and** _**NuSTAR**_ The _XMM-Newton_ X-ray Observatory and **the** Nuclear Spectro

scopic Telescope Array ( _NuSTAR_ ) started observing GRB 190114C under DDT ToOs 7.5 hours


and 22.5 hrs (respectively) after the burst. The _XMM-Newton_ and NuSTAR absorption-corrected


fluxes (see Fig. 1) were derived by fitting the spectrum with XSPEC adopting the same power law


model, with absorption in our Galaxy and at the redshift of the burst.


**NIR,** **Optical** **and** **UV** **afterglow** **observations** Light curves from the different instruments pre

sented in this section are shown in Extended Data Fig. 3.


**GROND** The Gamma-ray Burst Optical/Near-infrared Detector (GROND [52] ) started observations


3.8 hours after the GRB trigger, and the follow-up continued until January 29, 2019. Image re

duction and photometry were carried out with standard IRAF tasks [53], as described in [54,55] . _JHK_ s


photometry was converted to AB magnitudes to have a common flux system. Final photometry is


given in Extended Data Table 2.


**GTC** The BOOTES-2 ultra-wide field camera [56], took an image at the GRB 190114C location,


starting at 20:57:18 UT (30 s exposure time) (see Extended Data Fig. 4). The Gran Canarias


31

Extended Data Figure 3: **Afterglow** **light** **curves** **of** **GRB** **190114C.** Flux density at differ

ent frequencies, as a function of the time since the initial burst _T_ 0 . Panel **a** : observations in


the NIR/Optical/UV bands. The flux has been corrected for extinction in the host and in our


Galaxy. The contribution of the host galaxy and its companion has been subtracted. Fluxes have


been rescaled (except for the _r_ filter). Panel **b** : Radio and sub-mm observations from 1.3 GHz to


670 GHz.


_T_ GROND AB magnitude


(s) _g_ _[′]_ _r_ _[′]_ _i_ _[′]_ _z_ _[′]_ _J_ _H_ _K_ _s_


14029 _._ 94 _±_ 335 _._ 28 19 _._ 21 _±_ 0 _._ 03 18 _._ 46 _±_ 0 _._ 03 17 _._ 78 _±_ 0 _._ 03 17 _._ 33 _±_ 0 _._ 03 16 _._ 78 _±_ 0 _._ 05 16 _._ 30 _±_ 0 _._ 05 16 _._ 03 _±_ 0 _._ 07


24402 _._ 00 _±_ 345 _._ 66 19 _._ 50 _±_ 0 _._ 04 18 _._ 72 _±_ 0 _._ 03 18 _._ 05 _±_ 0 _._ 03 17 _._ 61 _±_ 0 _._ 03 17 _._ 02 _±_ 0 _._ 05 16 _._ 53 _±_ 0 _._ 05 16 _._ 26 _±_ 0 _._ 08


102697 _._ 17 _±_ 524 _._ 01 20 _._ 83 _±_ 0 _._ 06 20 _._ 00 _±_ 0 _._ 04 19 _._ 30 _±_ 0 _._ 04 18 _._ 87 _±_ 0 _._ 03 18 _._ 15 _±_ 0 _._ 05 17 _._ 75 _±_ 0 _._ 06 17 _._ 40 _±_ 0 _._ 09


106405 _._ 63 _±_ 519 _._ 87 20 _._ 86 _±_ 0 _._ 05 19 _._ 98 _±_ 0 _._ 03 19 _._ 34 _±_ 0 _._ 03 18 _._ 88 _±_ 0 _._ 03 18 _._ 17 _±_ 0 _._ 06 17 _._ 75 _±_ 0 _._ 06 17 _._ 34 _±_ 0 _._ 09


191466 _._ 77 _±_ 751 _._ 37 21 _._ 43 _±_ 0 _._ 07 20 _._ 61 _±_ 0 _._ 03 19 _._ 97 _±_ 0 _._ 03 19 _._ 52 _±_ 0 _._ 03 18 _._ 77 _±_ 0 _._ 06 18 _._ 28 _±_ 0 _._ 06 17 _._ 92 _±_ 0 _._ 14


275594 _._ 19 _±_ 747 _._ 59 21 _._ 57 _±_ 0 _._ 07 20 _._ 88 _±_ 0 _._ 04 20 _._ 31 _±_ 0 _._ 04 19 _._ 87 _±_ 0 _._ 04 19 _._ 14 _±_ 0 _._ 07 18 _._ 57 _±_ 0 _._ 06 18 _._ 26 _±_ 0 _._ 21


366390 _._ 74 _±_ 1105 _._ 79 21 _._ 87 _±_ 0 _._ 07 21 _._ 17 _±_ 0 _._ 04 20 _._ 62 _±_ 0 _._ 03 20 _._ 15 _±_ 0 _._ 03 19 _._ 43 _±_ 0 _._ 06 18 _._ 89 _±_ 0 _._ 06 18 _._ 46 _±_ 0 _._ 15


448791 _._ 55 _±_ 1201 _._ 33 21 _._ 90 _±_ 0 _._ 08 21 _._ 27 _±_ 0 _._ 04 20 _._ 79 _±_ 0 _._ 04 20 _._ 33 _±_ 0 _._ 03 19 _._ 66 _±_ 0 _._ 07 18 _._ 97 _±_ 0 _._ 07 18 _._ 55 _±_ 0 _._ 18


537481 _._ 41 _±_ 1132 _._ 16 22 _._ 02 _±_ 0 _._ 09 21 _._ 52 _±_ 0 _._ 05 21 _._ 00 _±_ 0 _._ 04 20 _._ 55 _±_ 0 _._ 03 19 _._ 87 _±_ 0 _._ 07 19 _._ 20 _±_ 0 _._ 07 18 _._ 83 _±_ 0 _._ 17


794992 _._ 63 _±_ 1200 _._ 69 22 _._ 14 _±_ 0 _._ 04 21 _._ 51 _±_ 0 _._ 03 21 _._ 05 _±_ 0 _._ 04 20 _._ 71 _±_ 0 _._ 05 20 _._ 31 _±_ 0 _._ 13 19 _._ 79 _±_ 0 _._ 14 19 _._ 59 _±_ 0 _._ 41


1226716 _._ 84 _±_ 1050 _._ 15 22 _._ 17 _±_ 0 _._ 04 21 _._ 59 _±_ 0 _._ 04 21 _._ 26 _±_ 0 _._ 04 20 _._ 97 _±_ 0 _._ 04 20 _._ 34 _±_ 0 _._ 12 19 _._ 95 _±_ 0 _._ 11 19 _._ 40 _±_ 0 _._ 34


Extended Data Table 2: **GROND** **photometry.** _T_ GROND in seconds after the BAT trigger.


The AB magnitudes are not corrected for the Galactic foreground reddening.


32

Telescope (GTC) equipped with the OSIRIS spectrograph [57] started observations 2.6 hr post-burst.


The grisms R1000B and R2500I were used covering the wavelength range 3,700-10,000 A (600 s [˚]


exposure times for each grism). The GTC detects a highly extinguished continuum, as well as CaII


H and K lines in absorption, and [OII], H _β_, and [OIII] in emission (see Extended Data Fig. 5), all


roughly at the same redshift _z_ = 0.4245 _±_ 0.0005 [58] . Comparing the derived rest-frame equivalent


widths (EWs) with the work by [59], GRB 190114C clearly shows higher than average, but not


unprecedented, values.


**HST** The _Hubble Space Telescope_ ( _HST_ ) imaged the afterglow and host galaxy of GRB 190114C


on 11 February and 12 March 2019. HST observations clearly reveal that the host galaxy is spiral


(Extended Data Fig. 4). A direct subtraction of the epochs of F850LP observations yields a faint


residual close to the nucleus of the host (Extended Data Fig. 4). From the position of the residual


we estimate that the burst originated within 250 pc of the host galaxy nucleus.


**LT** The robotic 2-m Liverpool Telescope (LT [60] ) slewed to the afterglow location at UTC 2019

01-14.974 and on the second night, from UTC 2019-01-15.814 and acquired images in _B_, _g_, _V_,


_r_, _i_ and _z_ bands (45 s exposure each in the first night and 60 s in the second, see Extended Data


Table 3). Aperture photometry of the afterglow was performed using a custom IDL script with


a fixed aperture radius of 1.5 _[′′]_ . Photometric calibration was performed relative to stars from the


Pan-STARRS1 catalogue [61] .


**NTT** The ESO New Technology Telescope (NTT) observed the optical counterpart of GRB 190114C


under the extended Public ESO Spectroscopic Survey for Transient Objects (ePESSTO) using the


33

Extended Data Figure 4: **Images** **of** **the** **localisation** **region** **of** **GRB** **190114C.** Panel **a** : The


CASANDRA-2 at the BOOTES-2 station all-sky image. The image (30 s exposure, unfiltered) was


taken at T0+14.8 s. At the GRB 190114C location (circle) no prompt optical emission is detected.


Panel **b** : Three-colour image of the host of GRB 190114C with the HST. The host galaxy is a


spiral galaxy, and the green circle indicates the location of the transient close to its host nucleus.


The image is 8 _[′′]_ across, north is up and east to the left. Panels **c,** **d** and **e** : F850LP imaging of


GRB 190114C taken with the HST. Two epochs are shown (images are 4 _[′′]_ across), as well as the


result of the difference image. A faint transient is visible close to the nucleus of the galaxy, and we


identify this as the late time afterglow of the burst.


34

UTC Filter Exposure (s) Magnitude

LT/IO:O

2019-01-14.975 _g_ 45 19.08 _±_ 0.06

2019-01-14.976 _r_ 45 18.22 _±_ 0.02

2019-01-14.977 _i_ 45 17.49 _±_ 0.02

2019-01-14.978 _z_ 45 17.12 _±_ 0.02

2019-01-14.979 _B_ 45 19.55 _±_ 0.15

2019-01-14.980 _V_ 45 18.81 _±_ 0.08

2019-01-15.814 _r_ 60 19.61 _±_ 0.05

2019-01-15.818 _z_ 60 18.70 _±_ 0.06

2019-01-15.820 _i_ 60 19.04 _±_ 0.04

2019-01-15.823 _g_ 60 20.96 _±_ 0.17


NOT/AlFOSC

2019-01-14.89127 _g_ 1 _×_ 300 17.72 _±_ 0.03

2019-01-14.89512 _r_ 1 _×_ 300 16.93 _±_ 0.02

2019-01-14.89899 _i_ 1 _×_ 300 16.42 _±_ 0.04

2019-01-14.90286 _z_ 1 _×_ 300 16.17 _±_ 0.04

2019-01-23.8896 _i_ 6 _×_ 300 21.02 _±_ 0.05


UVOT


_T_ start _T_ stop Filter Magnitude _T_ start _T_ stop Filter Magnitude


56.63 57.63 _V_ 12.17 _±_ 0.14 130958 142524 _UV M_ 2 20.37

57.63 58.63 _V_ 12.34 _±_ 0.14 217406 222752 _UV M_ 2 20.48

58.63 59.63 _V_ 12.44 _±_ 0.13 107573 125233 _U_ 20.29

59.63 60.63 _V_ 12.29 _±_ 0.14 205500 210750 _U_ 20.25

60.63 61.63 _V_ 12.44 _±_ 0.14 291188 302718 _U_ 20.49

61.63 62.63 _V_ 12.16 _±_ 0.13 400429 412385 _U_ 20.82

62.63 63.63 _V_ 12.51 _±_ 0.13 616 627 _V_ 16.25 _±_ 0.20

615.95 625.95 _V_ 16.32 _±_ 0.20 16295 17136 _V_ 19.03 _±_ 0.14

73.34 83.34 _white_ 13.86 26775 27682 _V_ 19.50 _±_ 0.27

83.34 93.34 _white_ 14.10 _±_ 0.06 39149 57221 _V_ 20.09 _±_ 0.23

93.34 103.34 _white_ 14.19 _±_ 0.06 108064 125736 _V_ 20.02

103.34 113.34 _white_ 14.36 _±_ 0.06 206689 211356 _V_ 20.02

113.34 123.34 _white_ 14.64 _±_ 0.06 292383 303996 _V_ 20.42

123.34 133.34 _white_ 14.65 _±_ 0.06 401305 413316 _V_ 20.17

133.34 143.34 _white_ 14.91 _±_ 0.06 4044 51522 _UV W_ 1 21.17

143.34 153.34 _white_ 14.99 _±_ 0.06 131216 142656 _UV W_ 1 20.47

153.34 163.34 _white_ 15.05 _±_ 0.06 217984 223056 _UV W_ 1 20.57

163.34 173.34 _white_ 15.32 _±_ 0.06 592 612 _UV W_ 2 17.65

173.34 183.34 _white_ 15.38 _±_ 0.06 6056 56384 _UV W_ 2 21.30

183.34 193.34 _white_ 15.38 _±_ 0.06 130699 142346 _UV W_ 2 20.52

193.34 203.34 _white_ 15.59 _±_ 0.06 216828 222404 _UV W_ 2 20.55

562.0 572.0 _white_ 16.96 _±_ 0.10 566 586 _white_ 16.90 _±_ 0.07

572.0 582.0 _white_ 16.90 _±_ 0.10 607389 613956 _white_ 22.16

535.5 555.5 _B_ 17.56 _±_ 0.21 624452 682416 _white_ 21.99 _±_ 0.18

545.5 565.5 _B_ 17.25 _±_ 0.18 745033 769296 _white_ 21.64 _±_ 0.16

285.9 305.9 _U_ 17.35 _±_ 0.19 818840 837216 _white_ 22.50

305.9 325.9 _U_ 17.50 _±_ 0.20 893522 907116 _white_ 22.57

325.9 345.9 _U_ 17.24 _±_ 0.18 991065 1004196 _white_ 22.49 _±_ 0.35

345.9 365.9 _U_ 17.26 _±_ 0.18 1077542 1094616 _white_ 22.41 _±_ 0.31

365.9 385.9 _U_ 17.80 _±_ 0.24 1140343 1170336 _white_ 22.50

385.9 405.9 _U_ 17.64 _±_ 0.22 1220661 1274376 _white_ 22.36 _±_ 0.29

405.9 425.9 _U_ 17.82 _±_ 0.24 5851 6050 _white_ 19.25 _±_ 0.09

425.9 445.9 _U_ 17.84 _±_ 0.25 21950 22857 _white_ 20.25 _±_ 0.09

445.9 465.9 _U_ 17.87 _±_ 0.25 1353459 1359284 _white_ 21.70

465.9 485.9 _U_ 17.79 _±_ 0.24 1502211 1548336 _white_ 21.98 _±_ 0.24

485.9 505.9 _U_ 17.81 _±_ 0.24 1692292 1703935 _white_ 22.07

505.9 525.9 _U_ 17.65 _±_ 0.22 2132978 2146056 _white_ 22.58

542 561 _B_ 17.38 _±_ 0.14 2299521 2317956 _white_ 22.41 _±_ 0.31

5646 5845 _B_ 19.54 _±_ 0.19 63686 80942 _white_ 21.07 _±_ 0.24

21038 46521 _B_ 21.14 _±_ 0.35 107900 125591 _white_ 21.40 _±_ 0.28

62774 96486 _B_ 21.33 _±_ 0.29 206292 211137 _white_ 21.52

107737 125412 _B_ 21.00 291984 303556 _white_ 21.48 _±_ 0.23

205896 210944 _B_ 20.78 401012 413029 _white_ 21.84

291586 303137 _B_ 21.29 491973 505356 _white_ 22.21 _±_ 0.24

400721 412707 _B_ 21.22 74 224 _white_ 14.90 _±_ 0.02

3839 50615 _UV M_ 2 20.88 _±_ 0.28


Extended Data Table 3: **Liverpool Telescope, Nordic Optical Telescope, and UVOT observa-**


**tions.** Magnitudes are SDSS AB-”like” for ugriz, Vega-”like” for all the other filters and are


35

not corrected for Galactic extinction. For UVOT data, magnitudes without uncertainties


are upper limits.

NTT/EFOSC2 instrument in imaging mode [62] . Observations started at 04:36:53 UT on 2019 Jan

uary 16 with the _g_, _r_, _i_, _z_ Gunn filters. Image reduction was carried out by following the standard


procedures [63] .


**OASDG** The 0.5 m remote telescope of the Osservatorio Astronomico “S. Di Giacomo” (OASDG),


located in Agerola (Italy) started observations in the optical _Rc_ -band 0.54 hours after the burst. The


afterglow of GRB 190114C was clearly detected in all the images.


**NOT** The Nordic Optical Telescope (NOT) observed the optical afterglow of GRB 190114C with


the Alhambra Faint Object Spectrograph and Camera (AlFOSC) instrument. Imaging was obtained


in the _griz_ filters with 300 s exposures, starting at Jan 14 21:20:56 UT, 24 minutes after the BAT


trigger. The normalised spectrum (Extended Data Fig. 5) reveals strong host interstellar absorption


lines due to Ca H & K and Na I D, which provided a redshift of _z_ = 0 _._ 425.


**REM** The Rapid Eye Mount telescope (REM) performed optical and NIR observations with


the REM 60 cm robotic telescope equipped with the ROS2 optical imager and the REMIR NIR


camera [64] . Observations were performed starting about 3.8 hours after the burst in the _r,_ and _J_


bands and lasted about one hour.


_**S**_ **wift/UVOT** The _Swift_ UltraViolet and Optical Telescope (UVOT [65] ) began observations at _T_ 0 +54


seconds in the UVOT _v_ band. The first observation after settling started 74 s after the trigger for


150 s in the UVOT _white_ band [66] . A 50 s exposure with the UV grism was taken thereafter, followed


by multiple exposures rotating through all seven broad and intermediate-band filters until switching


to only UVOT’s clear white filter on 2019-01-20. Standard photometric calibration and methods


36

Extended Data Figure 5: **Optical/NIR** **spectra** **of** **GRB** **190114C.** Panel **a** : The NOT/AlFOSC


spectrum obtained at a mid-time 1 hr post-burst. The continuum is afterglow dominated at this


time, and shows strong absorption features of Ca II and Na I (in addition to telluric absorption).


Panel **b** : the normalised GTC (+OSIRIS) spectrum on Jan 14, 23:32:03 UT, with the R1000B and


R2500I grisms. The emission lines of the underlying host galaxy are noticeable, besides the Ca


II absorption lines in the afterglow spectrum. Panel **c** : The visible light region of the VLT/X

shooter spectrum obtained approximately 3.2 d post-burst, showing strong emission lines from the


star-forming host galaxy.


37

were used for deriving the aperture photometry [67,68] . The grism zeroth order the data were reduced


manually [69] to derive the _b_ -magnitude and error.


**VLT** The STARGATE collaboration used the Very Large Telescope (VLT) and observed GRB 190114C


using the X-shooter spectrograph. Detailed analysis will be presented in forthcoming papers. A


portion of the second spectrum is shown in Extended Data Fig. 5, illustrating the strong emission


lines characteristic of a strongly star-forming galaxy, whose light is largely dominating over the


afterglow at this epoch.


**Magnitudes of the underlying galaxies** The _HST_ images show a spiral or tidally disrupted galaxy


whose bulge is coincident with the coordinates of GRB 190114C. A second galaxy is detected at an


angular distance of 1.3 _[′′]_, towards the North East. The SED analysis was performed with LePhare


70,71
using an iterative method that combined both the resolved photometry of the two galaxies


found in the _HST_ and _VLT_ /HAWK-I data and the blended photometry from _GALEX_ and WISE,


where the spatial resolution was much lower. Further details will be given in a paper in preparation


(de Ugate Postigo et al.). The estimated photometry, for each object and their combination, is given


in Extended Data Table 4.


**Optical Extinction** The optical extinction toward the line of sight of a GRB is derived assuming


**a** power law as intrinsic spectral shape [72] . Once the Galactic extinction ( _E_ B _−_ V = 0 _._ 01 [73] ) is taken


into account and the fairly bright host galaxy contribution is properly subtracted, a good fit to the


data is obtained with the LMC recipe and _A_ _V_ = 1 _._ 83 _±_ 0 _._ 15. The spectral index _β_ ( _F_ _ν_ _∝_ _ν_ _[β]_ [o] )


evolves from hard to soft across the temporal break in the optical light-curve at about 0.5 days,


38

Filter Host Companion Combined


Sloan _u_ 23.54 25.74 23.40


Sloan _g_ 22.51 23.81 22.21


Sloan _r_ 22.13 22.81 21.66


Sloan _i_ 21.70 22.27 21.19


Sloan _z_ 21.51 21.74 20.87


2MASS _J_ 20.98 21.08 20.28


2MASS _H_ 20.68 20.82 20.00


2MASS _Ks_ 20.45 20.61 19.77


Extended Data Table 4: **Observations** **of** **the** **host** **galaxy.** For each filter, the estimated


magnitudes are given for the host galaxy of GRB 190114C, the companion and the com

bination of the two objects.


39

moving from _β_ o _,_ 1 = _−_ 0 _._ 10 _±_ 0 _._ 12 to _β_ o _,_ 2 = _−_ 0 _._ 48 _±_ 0 _._ 15.


**Radio and Sub-mm afterglow observations** The light curves from the different instruments are


shown in Extended Data Fig. 3.


**ALMA** The Atacama Large Millimetre/Submillimetre Array (ALMA) observations are reported


in Band 3 (central observed frequency of 97.500 GHz) and Band 6 (235.0487 GHz), between 2019


January 15 and 2019 January 19. Data were calibrated within CASA (Common Astronomy Soft

ware Applications, version 5.4.0 [74] ) using the pipeline calibration. Photometric measurements were


also performed within CASA. ALMA early observations at 97.5 GHz are taken from [15] .


**ATCA** The Australia Telescope Compact Array (ATCA) observations were made with the ATCA


4 cm receivers (band centres 5.5 and 9 GHz), 15 mm receivers (band centres 17 and 19 GHz), and


7 mm receivers (band centres 43 and 45 GHz). ATCA data were obtained using the CABB con

tinuum mode [75] and reduced with the software packages M IRIAD [76] and CASA [74] using standard


techniques. The quoted errors are 1 _σ_, which include the RMS and Gaussian 1 _σ_ errors.


**GMRT** The upgraded Giant Metre-wave Radio Telescope [77] (UGMRT) observed on 17th January


2019 13.44 UT (2.8 days after the burst) in band 5 (1000-1450 MHz) with 2048 channels spread


over 400 MHz. GMRT detected a weak source with a flux density of 73 _±_ 17 _µ_ Jy at the GRB


position [78] . The flux should be considered as an upper limit, as the contribution from the host [79] has


not been subtracted.


40

ATCA


Start Date and Time End Date and Time Frequency Flux
GHz mJy


1/16/2019 6:47:00 1/16/2019 10:53:00 5.5 1.92 _±_ 0.06


9 1.78 _±_ 0.06


18 2.62 _±_ 0.26


1/18/2019 1:45:00 1/18/2019 11:18:00 5.5 1.13 _±_ 0.04


9 1.65 _±_ 0.05


18 2.52 _±_ 0.27


44 1.52 _±_ 0.15


1/20/2019 3:38 1/20/2019 10:25:00 5.5 1.78 _±_ 0.06


9 2.26 _±_ 0.07


18 2.30 _±_ 0.23


JCMT SCUBA-2


UT Date Time since Time on Typical Typical 850 _µ_ m RMS 450 _µ_ m RMS
trigger source 225 GHz CSO elevation density density
(days) (hours) Opacity (degrees) (mJy/beam) (mJy/beam)


2019-01-15 0.338 1.03 0.026 39 1.7 9.2


2019-01-16 1.338 1.03 0.024 39 1.6 8.4


2019-01-18 3.318 0.95 0.031 37 1.7 11.4


Extended Data Table 5: **Observations of GRB 190114C by ATCA and JCMT SCUBA-2** . For


ATCA data, start and end date and times (UTC) of the observations, frequency, and flux


(1 _σ_ error) are reported. For JCMT SCUBA-2 data, the CSO 225 GHz opacity measures


the zenith atmospheric attenuation.


41

**MeerKAT** The new MeerKAT radio observatory [80,81] observed on 15 and 18 January 2019, with


DDT requested by the ThunderKAT Large Survey Project [82] . Both epochs used 63 antennas and


were done at L-band spanning 856 MHz and centered at 1284 MHz. MeerKAT flux estimation


was done by finding and fitting the source with the software PyBDSF v.1.8.15 [83] . Adding the RMS


noise in quadrature to the flux uncertainty leads to final flux measurements of 125 _±_ 14 _µ_ Jy/beam


on 15 January and 97 _±_ 16 _µ_ Jy/beam on 18 January. The contribution from the host galaxy [79] has


not been subtracted. Therefore, these measurements provide a maximum flux of the GRB.


**JCMT** **SCUBA-2** **Sub-millimeter** Sub-millimeter observations were performed simultaneously


at 850 _µ_ m and 450 _µ_ m on three nights using the SCUBA-2 continuum camera [84] . GRB 190114C


was not detected on any of the individual nights. Combining all the SCUBA-2 continuum camera [84]


observations, the RMS background noise is 0.95 mJy/beam at 850 _µ_ m and 5.4 mJy/beam at 450 _µ_ m


at 1.67 days after the burst trigger.


**Prompt emission model for the early time MAGIC emission** In the standard picture the prompt


sub-MeV spectrum is explained as a synchrotron radiation from relativistic accelerated electrons


in the energy dissipation region. The associated inverse Compton component is sensitive to the


details of the dynamics: e.g. in the internal shock model if the peak energy is initially very high


and the IC component is suppressed due to Klein-Nishina (KN) effects, the peak of the IC com

ponent may be delayed and become bright only at late times when scatterings occur in Thomson


regime. Simulations showed that magnetic fields required to produce the GeV/TeV component are


rather low [85], _ϵ_ _B_ _∼_ 10 _[−]_ [3] . In this framework the contribution of the IC component to the observed


flux at early times (62-90 s, see Extended Data Table 1) does not exceed _∼_ 20%. Alternatively, if


42

Extended Data Figure 6: **Radio to X-rays SED at different epochs** . The synchrotron frequency


_ν_ m crosses the optical band, moving from higher to lower frequencies. The break between 10 [8] and


10 [10] Hz is caused by the self-absorption synchrotron frequency _ν_ sa . Optical (X-ray) data have been


corrected for extinction (absorption).


43

the prompt emission originates in reprocessed photospheric emission, the early TeV flux may arise


from IC scatterings of thermal photons by freshly heated electrons below the photosphere at low


optical depths. Another possibility for the generation of TeV photons might be the inverse Comp

ton scattering of prompt MeV photons by electrons in the external forward shock region where


electrons are heated to an average Lorentz factor of order 10 [4] at early times.


**Afterglow model** Synchrotron and SSC radiation from electrons accelerated at the forward shock


has been modelled within the external shock scenario [7,8,19,24,86] . The results of the modeling are


overlaid to the data in Fig. 3, and Extended Data Figs. 6 and 7.


We consider two types of power law radial profiles _n_ ( _R_ ) = _n_ 0 _R_ _[−][s]_ for the external environ

ment: _s_ = 0 (homogeneous medium) and _s_ = 2 (wind-like medium, typical of an environment


shaped by the stellar wind of the progenitor). In the last case, we define _n_ 0 = 3 _×_ 10 [35] _A_ _⋆_ cm _[−]_ [1] .


We assume that electrons swept up by the shock are accelerated into a power law distribution de

scribed by spectral index _p_ : _dN/dγ_ _∝_ _γ_ _[−][p]_, where _γ_ is the electron Lorentz factor. We call _ν_ m the


characteristic synchrotron frequency of electrons with Lorentz factor _γ_ m, _ν_ c the cooling frequency,


and _ν_ sa the synchrotron self-absorption frequency.


The early time optical emission (up to _∼_ 1000 s) and radio emission (up to _∼_ 10 [5] s) are


most likely dominated by reverse shock radiation [15] . Detailed modeling of this component is not


discussed in this work, where we focus on forward shock radiation.


The XRT flux (Fig. 1, blue data points) decays as _F_ X _∝_ _t_ _[α]_ [X] with _α_ X = _−_ 1 _._ 36 _±_ 0 _._ 02. If


_ν_ X _>_ _max_ ( _ν_ m _, ν_ c ), the X-ray light curve is predicted to decay as _t_ [(2] _[−]_ [3] _[p]_ [)] _[/]_ [4], that implies _p_ _∼_ 2 _._ 5.


44

Extended Data Figure 7: **Modeling of the broadband light curves.** Modeling of forward shock


emission is compared to observations at different frequencies (see legend). The model shown with


solid and dashed lines is optimised to describe the high-energy radiation (TeV, GeV and X-ray).


It has been obtained with the following parameters: _s_ = 0, _ϵ_ e = 0 _._ 07, _ϵ_ B = 8 _×_ 10 _[−]_ [5], _p_ = 2 _._ 6,


_n_ 0 = 0 _._ 5, and _E_ k = 8 _×_ 10 [53] erg. Solid lines show the total flux (synchrotron and SSC), while the


dashed line refers to the SSC contribution only. Dotted curves are derived to test a better modeling


of observations at lower frequencies, but fail to explain the behaviour of the TeV light curve. These


are obtained with the following model parameters: _s_ = 2, _ϵ_ e = 0 _._ 6, _ϵ_ B = 10 _[−]_ [4], _p_ = 2 _._ 4, _A_ _⋆_ = 0 _._ 1,


and _E_ k = 4 _×_ 10 [53] erg.


45

Another possibility is to assume _ν_ m _<_ _ν_ X _<_ _ν_ c, which implies _p_ = 2 _._ 1 _−_ 2 _._ 2 for _s_ = 2 and


_p_ _∼_ 2 _._ 8 for _s_ = 0. A broken power law fit provides a better fit (5 _._ 3 _×_ 10 _[−]_ [5] probability of chance


improvement), with a break occurring around 4 _×_ 10 [4] s and decay indices _α_ X _,_ 1 _∼−_ 1 _._ 32 _±_ 0 _._ 03


and _α_ X _,_ 2 _∼−_ 1 _._ 55 _±_ 0 _._ 04. This behaviour can be explained by the passage of _ν_ c in the XRT band


and assuming again _p_ = 2 _._ 4 _−_ 2 _._ 5 for _s_ = 2 and _p ∼_ 2 _._ 8 for _s_ = 0.


The optical light curve starts displaying a shallow decay in time (with temporal index poorly


constrained, between -0.5 and -0.25) starting from _∼_ 2 _×_ 10 [3] s, followed by a steepening around


8 _×_ 10 [4] s, when the temporal decay becomes similar to the decay in X-ray band, suggesting that after


this time the X-ray and optical band lie in the same part of the synchrotron spectrum. If the break


is interpreted as the synchrotron characteristic frequency _ν_ m crossing the optical band, after the


break the observed temporal decay requires a steep value of _p_ _∼_ 3 for _s_ = 0 and a value between


_p_ = 2 _._ 4 and _p_ = 2 _._ 5 for _s_ = 2. Independently of the density profile of the external medium and on


the cooling regime of the electrons, _ν_ m _∝_ _t_ _[−]_ [3] _[/]_ [2], placing it the soft X-ray band at 10 [2] s. The SED at


_∼_
100 s is indeed characterised by a peak in between 5-30 keV (Fig. 3). Information on the location


of the self-absorption frequency are provided by observations at 1 GHz, showing that _ν_ sa _∼_ 1 GHz


at 10 [5] s (Extended Data Fig. 6).


Summarizing, in a wind-like scenario X-ray and optical emission and their evolution in time


can be explained if _p_ = 2 _._ 4 _−_ 2 _._ 5, the emission is initially in fast cooling regime and transitions to


a slow cooling regime around 3 _×_ 10 [3] s. The optical spectral index at late times is predicted to be


(1 _−_ _p_ ) _/_ 2 _∼−_ 0 _._ 72, in agreement with observations. _ν_ m crosses the optical band at _t ∼_ 8 _×_ 10 [4] s,


explaining the steepening of the optical light curve and the flattening of the optical spectrum.


46

The X-ray band initially lies above (or close to) _ν_ m, and the break frequency _ν_ c starts crossing


the X-ray band around 2 _−_ 4 _×_ 10 [4] s, producing the steepening in the decay rate (the cooling


frequency increases with time for _s_ = 2). In this case, before the temporal break, the decay rate


is related to the spectral index of the electron energy distribution by _α_ X _,_ 1 = (2 _−_ 3 _p_ ) _/_ 4 _∼−_ 1 _._ 3,


for _p_ _∼_ 2 _._ 4 _−_ 2 _._ 5. Well after the break, this value of _p_ predicts a decay rate _α_ X _,_ 1 = (1 _−_ 3 _p_ ) _/_ 4 =


_−_ 1 _._ 55 _−_ 1 _._ 62. Overall, this interpretation is also consistent with the fact that the late time ( _t >_ 10 [5] s)


X-ray and optical light curves display similar temporal decays (Fig.1), as they lie in the same part


of the synchrotron spectrum ( _ν_ m _<_ _ν_ opt _<_ _ν_ X _<_ _ν_ c ). A similar picture can be invoked to explain


the emission also assuming a homogeneous density medium, but a steeper value of _p_ is required.


In this case, however, no break is predicted in the X-ray light curve.


We now add to the picture the information brought by the TeV detection. The modeling is


built with reference to the MAGIC flux and spectral indices derived considering statistical errors


only (see Extended Data Table 1 and green data points in Extended Data Fig. 2). The light curve


decays in time as _t_ _[−]_ [1] _[.]_ [51] and the photon index is consistent within _∼_ 1 _σ_ with Γ ph _,_ TeV _∼−_ 2 _._ 5 for


the entire duration of the emission, although there is evidence for an evolution from harder ( _∼−_ 2)


to softer ( _∼−_ 2 _._ 8) values. In the first broadband SED (Fig. 3, 68-110 s), LAT observations provide


strong evidence for the presence of two separated spectral peaks.


Assuming Thomson scattering, the SSC peak is given by:


_ν_ peak [SSC] _[≃]_ [2] _[ γ]_ e [2] _[ν]_ peak [syn] (1)


47

while in KN regime, the SSC peak should be located at:


_hν_ peak [SSC] _[≃]_ [2] _[ γ]_ [e] [Γ] _[ m]_ [e] _[c]_ [2] _[/]_ [(1 +] _[ z]_ [)] (2)


where _γ_ e = min( _γ_ c _, γ_ m ). The synchrotron spectral peak is located at _E_ peak [syn] _[∼]_ [10][ keV,] [while]


the peak of the SSC component must be below _E_ peak [ssc] [≲] [100][ GeV to explain the MAGIC photon]


index. Both the KN and Thomson scattering regimes imply _γ_ e ≲ 10 [3] . This small value faces


two problems: i) if the bulk Lorentz factor Γ is larger than 150 (that is a necessary condition to


avoid strong _γ_ - _γ_ opacity, see below), a small _γ_ m translates into a small efficiency of the electron


acceleration, with _ϵ_ e _<_ 0 _._ 05, ii) the synchrotron peak energy can be located at _E_ peak [syn] _[∼]_ [10][ keV]


only for _B_ Γ ≳ 10 [5] G. Large _B_ and small _ϵ_ e would make difficult to explain the presence of a


strong SSC emission. These calculations show that _γ_ - _γ_ opacity likely plays a role in shaping and


softening the observed spectra of the SSC spectrum [30,87] .


For a gamma-ray photon with energy _E_ _γ_, the _τ_ _γγ_ opacity is:


_τ_ _γγ_ ( _E_ _γ_ ) = _σ_ _γγ_ ( _R/_ Γ) _n_ t ( _E_ _γ_ ) _,_ (3)


where _n_ t = _L_ t _/_ (4 _π R_ [2] _c_ Γ _E_ t ) is the density of target photons in the comoving frame, _L_ t is the


luminosity and _E_ t = ( _m_ e _c_ [2] ) [2] Γ [2] _/E_ _γ_ _/_ (1+ _z_ ) [2] is the energy of target photons in the observer frame.


Target photons for photons with energy _E_ _γ_ = 0 _._ 2 _−_ 1 TeV and for Γ _∼_ 120 _−_ 150 have energies


in the range 4 _−_ 30 keV. When _γ_ _−_ _γ_ absorption is relevant, the emission from pairs can give a


non-negligible contribution to the radiative output.


To properly model all the physical processes that are shaping the broadband radiation, we


use a numerical code that solves the evolution of the electron distributions and derives the radiative


48

output taking into account the following processes: synchrotron and SSC losses, adiabatic losses,


_γ_ _−_ _γ_ absorption, emission from pairs, and synchrotron self-absorption [88–91] . We find that for


the parameters assumed in the proposed modeling (see below), the contribution from pairs to the


emission is negligible.


The MAGIC photon index (Extended Data Table 1) and its evolution with time constrain the


SSC peak energy to be at ≲ 1 TeV at the beginning of observations (Extended Data Table 1). In


general the internal opacity decreases with time and KN effects become less relevant. A possible


softening of the spectrum with time, as the one suggested by the observations, requires that the


spectral peak decreases with time and moves below the MAGIC energy range. In the slow cooling


regime, the SSC peak evolves to higher frequencies for a wind-like medium and decreases very


slowly ( _ν_ peak [SSC] _[∝]_ _[t]_ _[−]_ [1] _[/]_ [4] [) for a constant-density medium (both in KN and Thomson regimes).] [In fast]


cooling regime the evolution is faster ( _ν_ peak [SSC] _[∝]_ _[t]_ _[−]_ [1] _[/]_ [2] _[ −]_ _[t]_ _[−]_ [9] _[/]_ [4] [ depending on medium and regime).]


We model the multi-band observations considering both _s_ = 0 and _s_ = 2. The results are


shown in Fig. 3, Extended Data Figs. 6 and 7 where model curves are overlaid to observations.


The model curves shown in these figures have been derived using the following parameters. The


model in Fig. 3 and in 7 (solid and dashed curves) we have used _s_ = 0, _ϵ_ e = 0 _._ 07, _ϵ_ B = 8 _×_ 10 _[−]_ [5],


_p_ = 2 _._ 6, _n_ 0 = 0 _._ 5, and _E_ k = 8 _×_ 10 [53] erg. For the dotted curves in Extended Data Fig. 7 and the


SEDs in Extended Data Figs. 6 we have used _s_ = 2, _ϵ_ e = 0 _._ 6, _ϵ_ B = 10 _[−]_ [4], _p_ = 2 _._ 4, _A_ _⋆_ = 0 _._ 1, and


_E_ k = 4 _×_ 10 [53] erg.


Using the constraints on the afterglow onset time ( _t_ [aft] peak _[∼]_ [5] _[ −]_ [10][ s from the smooth compo-]


49

nent detected during the prompt emission) the initial bulk Lorentz factor is constrained to assume


values Γ 0 _∼_ 300 and Γ 0 _∼_ 700 for _s_ = 2 and _s_ = 0, respectively.


Consistently with the qualitative description above, we find that late time optical observa

tions can indeed be explained with _ν_ m crossing the band (see the SED modeling in Extended Data


Fig. 6 and dotted curves in Extended Data Fig. 7). However a large _ν_ m is required in this case


and consequently also the peak of the SSC component would be large and lie above the MAGIC


energy range. The resulting MAGIC light curve (green dotted curve in Extended Data Fig. 7) does


not agree with observations. Relaxing the requirement on _ν_ m, the TeV spectra (Fig. 3) and light


curve (green solid curve in Extended Data Fig. 7) can be explained. As noted before, a wind-like


medium can explain the steepening of the X-ray light curve at 8 _×_ 10 [4] s, while in a homogeneous


medium no steepening is expected (blue dotted and solid lines in Extended Data Fig. 7). We find


that the GeV flux detected by LAT at late time ( _t_ _∼_ 10 [4] s) is dominated by the SSC component


(dashed line in Extended Data Fig. 7).


1. M´esz´aros, P. Theories of Gamma-Ray Bursts. ARA&A **40**, 137–169 (2002).


2. Piran, T. The physics of gamma-ray bursts. _Reviews of Modern Physics_ **76**, 1143–1210 (2004).


3. van Paradijs, J., Kouveliotou, C. & Wijers, R. A. M. J. Gamma-Ray Burst Afterglows.


ARA&A **38**, 379–425 (2000).


4. Gehrels, N., Ramirez-Ruiz, E. & Fox, D. B. Gamma-Ray Bursts in the Swift Era. ARA&A


50

**47**, 567–617 (2009).


5. Gehrels, N. & M´esz´aros, P. Gamma-Ray Bursts. _Science_ **337**, 932 (2012).


6. Kumar, P. & Zhang, B. The physics of gamma-ray bursts & relativistic jets. Phys. Rep. **561**,


1–109 (2015).


7. Sari, R., Piran, T. & Narayan, R. Spectra and Light Curves of Gamma-Ray Burst Afterglows.


ApJ **497**, L17–L20 (1998).


8. Granot, J. & Sari, R. The Shape of Spectral Breaks in Gamma-Ray Burst Afterglows. ApJ


**568**, 820–829 (2002).


9. Meszaros, P. & Rees, M. J. Delayed GEV Emission from Cosmological Gamma-Ray Bursts 

Impact of a Relativistic Wind on External Matter. MNRAS **269**, L41 (1994).


10. MAGIC Collaboration. Teraelectronvolt emission from the _γ_ -ray burst GRB 190114C. _Nature_


**575**, 455–458 (2019).


11. Nava, L. High-energy emission from gamma-ray bursts. _International_ _Journal_ _of_ _Modern_


_Physics D_ **27**, 1842003 (2018).


12. Mirzoyan, R. First time detection of a GRB at sub-TeV energies; MAGIC detects the GRB


190114C. _The Astronomer’s Telegram_ **12390** (2019).


13. Ajello, M. _et_ _al._ Fermi and Swift Observations of GRB 190114C: Tracing the Evolution of


High-Energy Emission from Prompt to Afterglow. _arXiv e-prints_ arXiv:1909.10605 (2019).


51

14. Ravasio, M. E. _et al._ GRB 190114C: from prompt to afterglow? A&A **626**, A12 (2019).


15. Laskar, T. _et al._ ALMA Detection of a Linearly Polarized Reverse Shock in GRB 190114C.


ApJ **878**, L26 (2019).


16. Vietri, M. GeV Photons from Ultrahigh Energy Cosmic Rays Accelerated in Gamma Ray


Bursts. _Physical Review Letters_ **78**, 4328–4331 (1997).


17. Zhang, B. & M´esz´aros, P. High-Energy Spectral Components in Gamma-Ray Burst After

glows. ApJ **559**, 110–122 (2001).


18. Razzaque, S. A Leptonic-Hadronic Model for the Afterglow of Gamma-ray Burst 090510.


ApJ **724**, L109–L112 (2010).


19. Sari, R. & Esin, A. A. On the Synchrotron Self-Compton Emission from Relativistic Shocks


and Its Implications for Gamma-Ray Burst Afterglows. ApJ **548**, 787–799 (2001).


20. M´esz´aros, P., Razzaque, S. & Zhang, B. GeV-TeV emission from _γ_ -ray bursts. New A Rev.


**48**, 445–451 (2004).


21. Lemoine, M. The synchrotron self-Compton spectrum of relativistic blast waves at large Y.


MNRAS **453**, 3772–3784 (2015).


22. Fan, Y.-Z. & Piran, T. High-energy _γ_ -ray emission from gamma-ray bursts — before GLAST.


_Frontiers of Physics in China_ **3**, 306–330 (2008).


23. Galli, A. & Piro, L. Prospects for detection of very high-energy emission from GRB in the


context of the external shock model. A&A **489**, 1073–1077 (2008).


52

24. Nakar, E., Ando, S. & Sari, R. Klein-Nishina Effects on Optically Thin Synchrotron and


Synchrotron Self-Compton Spectrum. ApJ **703**, 675–691 (2009).


25. Xue, R. R. _et al._ Very High Energy _γ_ -Ray Afterglow Emission of Nearby Gamma-Ray Bursts.


ApJ **703**, 60–67 (2009).


26. Piran, T. & Nakar, E. On the External Shock Synchrotron Model for Gamma-ray Bursts’ GeV


Emission. ApJ **718**, L63–L67 (2010).


27. Tam, P.-H. T., Tang, Q.-W., Hou, S.-J., Liu, R.-Y. & Wang, X.-Y. Discovery of an Extra Hard


Spectral Component in the High-energy Afterglow Emission of GRB 130427A. ApJ **771**, L13


(2013).


28. Liu, R.-Y., Wang, X.-Y. & Wu, X.-F. Interpretation of the Unprecedentedly Long-lived High

energy Emission of GRB 130427A. ApJ **773**, L20 (2013).


29. Ackermann, M. _et_ _al._ Fermi-LAT Observations of the Gamma-Ray Burst GRB 130427A.


_Science_ **343**, 42–47 (2014).


30. Wang, X.-Y., Liu, R.-Y., Zhang, H.-M., Xi, S.-Q. & Zhang, B. Synchrotron self-Compton


emission from afterglow shocks as the origin of the sub-TeV emission in GRB 180720B and


GRB 190114C. _arXiv e-prints_ arXiv:1905.11312 (2019).


31. Hamburg, R. GRB 190114C: Fermi GBM detection. _GRB Coordinates Network_ **23707** (2019).


32. Kocevski, D. _et al._ GRB 190114C: Fermi-LAT detection. _GRB Coordinates Network_ **23709**


(2019).


53

33. Gropp, J. D. GRB 190114C: Swift detection of a very bright burst with a bright optical


counterpart. _GRB Coordinates Network_ **23688** (2019).


34. Ursi, A. _et_ _al._ GRB 190114C: AGILE/MCAL detection. _GRB_ _Coordinates_ _Network_ **23712**


(2019).


35. Frederiks, D. _et_ _al._ Konus-Wind observation of GRB 190114C. _GRB_ _Coordinates_ _Network_


**23737** (2019).


36. Minaev, P. & Pozanenko, A. GRB 190114C: SPI-ACS/INTEGRAL extended emission detec

tion. _GRB Coordinates Network_ **23714** (2019).


37. Xiao, S. _et al._ GRB 190114C:Insight-HXMT/HE detection. _GRB Coordinates Network_ **23716**


(2019).


38. Tavani, M. _et al._ The AGILE Mission. _Astron. Astrophys._ **502**, 995–1013 (2009).


39. Goldstein, A. _et_ _al._ The Fermi GBM Gamma-Ray Burst Spectral Catalog: The First Two


Years. ApJS **199**, 19 (2012).


40. Meegan, C. _et al._ The Fermi Gamma-ray Burst Monitor. ApJ **702**, 791–804 (2009).


41. Barthelmy, S. D. _et_ _al._ The Burst Alert Telescope (BAT) on the SWIFT Midex Mission.


Space Sci. Rev. **120**, 143–164 (2005).


42. Atwood, A. A., W. B.Abdo _et al._ The Large Area Telescope on the Fermi Gamma-Ray Space


Telescope Mission. ApJ **697**, 1071–1102 (2009).


54

43. Kocevski, D. _et al._ GRB 190114C: Fermi-LAT detection. _GRB Coordinates Network_ **23709**


(2019).


44. Aleksi´c, J. _et al._ The major upgrade of the MAGIC telescopes, Part II: A performance study


using observations of the Crab Nebula. _Astroparticle Physics_ **72**, 76–94 (2016).


45. Ahnen, M. L. _et_ _al._ Performance of the MAGIC telescopes under moonlight. _Astroparticle_


_Physics_ **94**, 29–41 (2017).


46. Dom´ınguez, A. _et al._ Extragalactic background light inferred from AEGIS galaxy-SED-type


fractions. MNRAS **410**, 2556–2578 (2011).


47. Franceschini, A., Rodighiero, G. & Vaccari, M. Extragalactic optical-infrared background ra

diation, its time evolution and the cosmic photon-photon opacity. A&A **487**, 837–852 (2008).


48. Finke, J. D., Razzaque, S. & Dermer, C. D. Modeling the Extragalactic Background Light


from Stars and Dust. ApJ **712**, 238–249 (2010).


49. Gilmore, R. C., Somerville, R. S., Primack, J. R. & Dom´ınguez, A. Semi-analytic modelling


of the extragalactic background light and consequences for extragalactic gamma-ray spectra.


MNRAS **422**, 3189–3207 (2012).


50. UK _Swift_ Science Data Centre. GRB 190114C _Swift_ /XRT Light Curve. [https://www.](https://www.swift.ac.uk/xrt_curves/00883832/)


[swift.ac.uk/xrt_curves/00883832/.](https://www.swift.ac.uk/xrt_curves/00883832/)


51. Evans, P. A. _et_ _al._ Methods and results of an automatic analysis of a complete sample of


Swift-XRT observations of GRBs. MNRAS **397**, 1177–1201 (2009).


55

52. Greiner, J. _et al._ GROND—a 7-Channel Imager. _Publications of the Astronomical Society of_


_the Pacific_ **120**, 405 (2008).


53. Tody, D. IRAF in the Nineties. In Hanisch, R. J., Brissenden, R. J. V. & Barnes, J. (eds.)


_Astronomical_ _Data_ _Analysis_ _Software_ _and_ _Systems_ _II_, vol. 52 of _Astronomical_ _Society_ _of_ _the_


_Pacific Conference Series_, 173 (1993).


54. Kr¨uhler, T. _et al._ The 2175 A Dust Feature in a Gamma-Ray Burst Afterglow at Redshift 2.45. [˚]


ApJ **685**, 376–383 (2008).


55. Bolmer, J. _et_ _al._ Dust reddening and extinction curves toward gamma-ray bursts at _z_ _>_ 4.


A&A **609**, A62 (2018).


56. Castro-Tirado, A. J. _et al._ A very sensitive all-sky CCD camera for continuous recording of


the night sky. In Proc. SPIE, vol. 7019 of _Society of Photo-Optical Instrumentation Engineers_


_(SPIE) Conference Series_, 70191V (2008).


57. Cepa, J. _et al._ OSIRIS tunable imager and spectrograph. In Iye, M. & Moorwood, A. F. (eds.)


_Optical_ _and_ _IR_ _Telescope_ _Instrumentation_ _and_ _Detectors_, vol. 4008 of Proc. SPIE, 623–631


(2000).


58. Castro-Tirado, A. GRB 190114C: refined redshift by the 10.4m GTC. _GRB_ _Coordinates_


_Network_ **23708** (2019).


59. de Ugarte Postigo, A. _et_ _al._ The distribution of equivalent widths in long GRB afterglow


spectra. A&A **548**, A11 (2012).


56

60. Steele, I. A. _et al._ The Liverpool Telescope: performance and first results. In Oschmann, J. M.,


Jr. (ed.) _Ground-based Telescopes_, vol. 5489 of Proc. SPIE, 679–692 (2004).


61. Chambers, K. C. _et al._ The Pan-STARRS1 Surveys. _arXiv e-prints_ (2016).


62. Tarenghi, M. & Wilson, R. N. The ESO NTT (New Technology Telescope): The first active


optics telescope. In Roddier, F. J. (ed.) _Active telescope systems_, vol. 1114 of _Society of Photo-_


_Optical Instrumentation Engineers (SPIE) Conference Series_, 302–313 (1989).


63. Smartt, S. J. _et al._ PESSTO: survey description and products from the first data release by the


Public ESO Spectroscopic Survey of Transient Objects. A&A **579**, A40 (2015).


64. Covino, S. _et_ _al._ REM: a fully robotic telescope for GRB observations. In Moorwood, A.


F. M. & Iye, M. (eds.) _Ground-based Instrumentation for Astronomy_, vol. 5492 of _Society of_


_Photo-Optical Instrumentation Engineers (SPIE) Conference Series_, 1613–1622 (2004).


65. Roming, P. W. A. _et al._ The Swift Ultra-Violet/Optical Telescope. Space Sci. Rev. **120**, 95–142


(2005).


66. Siegel, M. H. & Gropp, J. D. GRB 190114C: Swift/UVOT Detection. _GRB_ _Coordinates_


_Network_ **23725** (2019).


67. Poole, T. S. _et al._ Photometric calibration of the Swift ultraviolet/optical telescope. MNRAS


**383**, 627–645 (2008).


68. Breeveld, A. A. _et al._ An Updated Ultraviolet Calibration for the Swift/UVOT. In _American_


_Institute of Physics Conference Series_, vol. 1358, 373–376 (2011).


57

69. Kuin, N. P. M. _et al._ Calibration of the Swift-UVOT ultraviolet and visible grisms. MNRAS


**449**, 2514–2538 (2015).


70. Arnouts, S. _et_ _al._ Measuring and modelling the redshift evolution of clustering: the Hubble


Deep Field North. MNRAS **310**, 540–556 (1999).


71. Ilbert, O. _et al._ Accurate photometric redshifts for the CFHT legacy survey calibrated using


the VIMOS VLT deep survey. A&A **457**, 841–856 (2006).


72. Covino, S. _et_ _al._ Dust extinctions for an unbiased sample of gamma-ray burst afterglows.


MNRAS **432**, 1231–1244 (2013).


73. Schlafly, E. F. & Finkbeiner, D. P. Measuring Reddening with Sloan Digital Sky Survey Stellar


Spectra and Recalibrating SFD. ApJ **737**, 103 (2011).


74. McMullin, J. P., Waters, B., Schiebel, D., Young, W. & Golap, K. CASA Architecture and


Applications. In Shaw, R. A., Hill, F. & Bell, D. J. (eds.) _Astronomical_ _Data_ _Analysis_ _Soft-_


_ware and Systems XVI_, vol. 376 of _Astronomical Society of the Pacific Conference Series_, 127


(2007).


75. Wilson, W. E. _et al._ The Australia Telescope Compact Array Broad-band Backend: description


and first results. MNRAS **416**, 832–856 (2011).


76. Sault, R. J., Teuben, P. J. & Wright, M. C. H. A Retrospective View of MIRIAD. In Shaw,


R. A., Payne, H. E. & Hayes, J. J. E. (eds.) _Astronomical Data Analysis Software and Systems_


_IV_, vol. 77 of _Astronomical Society of the Pacific Conference Series_, 433 (1995).


58

77. Swarup, G. _et_ _al._ The Giant Metre-Wave Radio Telescope. _Current_ _Science,_ _Vol._ _60,_


_NO.2/JAN25, P. 95, 1991_ **60**, 95 (1991).


78. Cherukuri, S. V. _et al._ GRB 190114C: GMRT detection at 1.26GHz. _GRB Coordinates Net-_


_work_ **23762** (2019).


79. Tremou, L. _et_ _al._ GRB 190114C: MeerKAT radio observation. _GRB_ _Coordinates_ _Network_


**23760** (2019).


80. Camilo, F. _et_ _al._ Revival of the Magnetar PSR J1622-4950: Observations with MeerKAT,


Parkes, XMM-Newton, Swift, Chandra, and NuSTAR. ApJ **856**, 180 (2018).


81. Jonas, J. & MeerKAT Team. The MeerKAT Radio Telescope. In _Proceedings_ _of_ _MeerKAT_


_Science:_ _On the Pathway to the SKA. 25-27 May_, 1 (2016).


82. Fender, R. _et_ _al._ ThunderKAT: The MeerKAT Large Survey Project for Image-Plane Radio


Transients. _arXiv e-prints_ arXiv:1711.04132 (2017).


83. Mohan, N. & Rafferty, D. PyBDSF: Python Blob Detection and Source Finder (2015).


84. Holland, W. S. _et_ _al._ SCUBA-2: the 10 000 pixel bolometer camera on the James Clerk


Maxwell Telescope. MNRAS **430**, 2513–2533 (2013).


85. Boˇsnjak, Z., Daigne, F. & Dubus, G. [ˇ] Prompt high-energy emission from gamma-ray bursts in


the internal shock model. A&A **498**, 677–703 (2009).


86. Panaitescu, A. & Kumar, P. Analytic Light Curves of Gamma-Ray Burst Afterglows: Homo

geneous versus Wind External Media. ApJ **543**, 66–76 (2000).


59

87. Derishev, E. & Piran, T. The Physical Conditions of the Afterglow Implied by MAGIC’s


Sub-TeV Observations of GRB 190114C. ApJ **880**, L27 (2019).


88. Mastichiadis, A. & Kirk, J. G. Self-consistent particle acceleration in active galactic nuclei.


A&A **295**, 613 (1995).


89. Vurm, I. & Poutanen, J. Time-Dependent Modeling of Radiative Processes in Hot Magnetized


Plasmas. ApJ **698**, 293–316 (2009).


90. Petropoulou, M. & Mastichiadis, A. On the multiwavelength emission from gamma ray burst


afterglows. A&A **507**, 599–610 (2009).


91. Pennanen, T., Vurm, I. & Poutanen, J. Simulations of gamma-ray burst afterglows with a


relativistic kinetic code. A&A **564**, A77 (2014).


**Author Information** The authors declare no competing interests. Correspondence and requests for mate

rials should be addressed to Razmik Mirzoyan (email: razmik.mirzoyan@mpp.mpg.de) or MAGIC (email:


contact.magic@mpp.mpg.de).


**Acknowledgements** The MAGIC Collaboration would like to thank the Instituto de Astrof´ısica de Ca

narias for the excellent working conditions at the Observatorio del Roque de los Muchachos in La Palma.


The financial support of the German BMBF and MPG, the Italian INFN and INAF, the Swiss National


Fund SNF, the ERDF under the Spanish MINECO (FPA2017-87859-P, FPA2017-85668-P, FPA2017-82729

C6-2-R, FPA2017-82729-C6-6-R, FPA2017-82729-C6-5-R, AYA2015-71042-P, AYA2016-76012-C3-1-P,


ESP2017-87055-C2-2-P, FPA201790566REDC), the Indian Department of Atomic Energy, the Japanese


60

JSPS and MEXT, the Bulgarian Ministry of Education and Science, National RI Roadmap Project DO1

153/28.08.2018 and the Academy of Finland grant nr. 320045 is gratefully acknowledged. This work


was also supported by the Spanish Centro de Excelencia “Severo Ochoa” SEV-2016-0588 and SEV-2015

0548, and Unidad de Excelencia “Mar´ıa de Maeztu” MDM-2014-0369, by the Croatian Science Foun

dation (HrZZ) Project IP-2016-06-9782 and the University of Rijeka Project 13.12.1.3.02, by the DFG


Collaborative Research Centers SFB823/C4 and SFB876/C3, the Polish National Research Centre grant


UMO-2016/22/M/ST9/00382 and by the Brazilian MCTIC, CNPq and FAPERJ. L. Nava acknowledges


funding from the European Union’s Horizon 2020 Research and Innovation programme under the Marie


Skłodowska-Curie grant agreement n. 664931. E. Moretti acknowledges funding from the European Union’s


Horizon 2020 research and innovation programme under Marie Skłodowska-Curie grant agreement No


665919. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.A.00020.T,


ADS/JAO.ALMA#2018.1.01410.T. ALMA is a partnership of ESO (representing its member states), NSF


(USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Repub

lic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by


ESO, AUI/NRAO and NAOJ. CT, AdUP, and DAK acknowledge support from the Spanish research project


AYA2017-89384-P. C. Thoene and A. de Ugarte Postigo acknowledge support from funding associated to


Ram´on y Cajal fellowships (RyC-2012-09984 and RyC-2012-09975). D. A. Kann acknowledges support


from funding associated to Juan de la Cierva Incorporaci´on fellowships (IJCI-2015-26153). The James Clerk


Maxwell Telescope is operated by the East Asian Observatory on behalf of The National Astronomical Ob

servatory of Japan; Academia Sinica Institute of Astronomy and Astrophysics; the Korea Astronomy and


Space Science Institute; Center for Astronomical Mega-Science (as well as the National Key R&D Program


of China with No. 2017YFA0402700). Additional funding support is provided by the Science and Tech

nology Facilities Council of the United Kingdom and participating universities in the United Kingdom and


61

Canada. The JCMT data reported here were obtained under project M18BP040 (P.I. D. Perley). We thank


Mark Rawlings, Kevin Silva, Sheona Urquart, and the JCMT staff for the prompt support of these observa

tions. The Liverpool Telescope, located on the island of La Palma in the Spanish Observatorio del Roque de


los Muchachos of the Instituto de Astrofisica de Canarias, is operated by Liverpool John Moores University


with financial support from the UK Science and Technology Facilities Council. The Australia Telescope


Compact Array is part of the Australia Telescope National Facility which is funded by the Australian Gov

ernment for operation as a National Facility managed by CSIRO. GEA is the recipient of an Australian


Research Council Discovery Early Career Researcher Award (project number DE180100346) and JCAM-J


is the recipient of Australian Research Council Future Fellowship (project number FT140101082) funded by


the Australian Government. Support for the German contribution to GBM was provided by the Bundesmin

isterium f¨ur Bildung und Forschung (BMBF) via the Deutsches Zentrum f¨ur Luft und Raumfahrt (DLR)


under grant number 50 QV 0301. The UAH coauthors gratefully acknowledge NASA funding from coop

erative agreement NNM11AA01A. C.A.W.H., and C.M.H. gratefully acknowledge NASA funding through


the _Fermi_ -GBM project.


The _Fermi_ LAT Collaboration acknowledges generous ongoing support from a number of agencies and in

stitutes that have supported both the development and the operation of the LAT as well as scientific data


analysis. These include the National Aeronautics and Space Administration and the Department of Energy


in the United States, the Commissariat `a l’Energie Atomique and the Centre National de la Recherche Sci

entifique / Institut National de Physique Nucl´eaire et de Physique des Particules in France, the Agenzia


Spaziale Italiana and the Istituto Nazionale di Fisica Nucleare in Italy, the Ministry of Education, Cul

ture, Sports, Science and Technology (MEXT), High Energy Accelerator Research Organization (KEK) and


Japan Aerospace Exploration Agency (JAXA) in Japan, and the K. A. Wallenberg Foundation, the Swedish


Research Council and the Swedish National Space Board in Sweden.


62

Additional support for science analysis during the operations phase is gratefully acknowledged from the


Istituto Nazionale di Astrofisica in Italy and the Centre National d’Etudes [´] Spatiales in France. This work


performed in part under DOE Contract DE-AC02-76SF00515.


Part of the funding for GROND (both hardware as well as personnel) was generously granted from the


Leibniz-Prize to Prof. G. Hasinger (DFG grant HA 1850/28-1). Swift data were retrieved from the Swift


archive at HEASARC/NASA-GSFC, and from the UK Swift Science Data Centre. Support for Swift in the


UK is provided by the UK Space Agency


This work is based on observations obtained with XMM-Newton, an ESA science mission with instruments


and contributions directly funded by ESA Member States and NASA.


This work is partially based on observations collected at the European Organisation for Astronomical Re

search in the Southern Hemisphere under ESO programme 199.D-0143. The work is partly based on ob

servations made with the Gran Telescopio Canarias (GTC), installed in the Spanish Observatorio del Roque


de los Muchachos of the Instituto de Astrof´ısica de Canarias, in the island of La Palma. This work is par

tially based on observations made with the Nordic Optical Telescope (programme 58-502), operated by the


Nordic Optical Telescope Scientific Association at the Observatorio del Roque de los Muchachos, La Palma,


Spain, of the Instituto de Astrof´ısica de Canarias. This work is partially based on observations collected at


the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programme


102.D-0662. This work is partially based on observations collected through the ESO programme 199.D

0143 ePESSTO. M. Gromadzki is supported by the Polish NCN MAESTRO grant 2014/14/A/ST9/00121.


M. Nicholl is supported by a Royal Astronomical Society Research Fellowship M. G. Bernardini, S. Cam

pana, A. Melandri and P. D’Avanzo acknowledge ASI grant I/004/11/3. S. Campana thanks for support the


implementing agreement ASI-INAF n.2017-14-H.0. S. J. Smartt acknowledges funding from STFC Grant


63

Ref: ST/P000312/1. NPMK acknowledges support by the UK Space Agency under grant ST/P002323/1


and the UK Science and Technology Facilities Council under grant ST/N00811/1. L. Piro, S. Lotti acknowl

edge partial support from the agreement ASI-INAF n.2017-14-H.0. VAF acknowledges RFBR 18-29-21030


for support. AJCT acknowledges support from the Junta de Andaluc´ıa (Project P07-TIC-03094) and sup

port from the Spanish Ministry Projects AYA2012-39727-C03-01 and 2015-71718R. KM acknowledges the


support from Department of Science and Technology (DST), Govt. of India and Indo-US Science and Tech

nology Forum (IUSSTF) for the WISTEMM fellowship and Dept. of Physics, UC Davis where a part of this


work was carried out. M.J.M. acknowledges the support of the National Science Centre, Poland through


the grant 2018/30/E/ST9/00208. VJ and RL acknowledges support from the grant EMR/2016/007127 from


Dept. of Science and Technology, India. K. Maguire acknowledges support from H2020 through an ERC


Starting Grant (758638). L. Izzo would like to acknowledge Massimo Della Valle for invaluable support in


the operation of the telescope.


**Author Contributions** The MAGIC telescope system was designed and constructed by the MAGIC Col

laboration. Operation, data processing, calibration, Monte Carlo simulations of the detector, and of theo

retical models, and data analyses were performed by the members of the MAGIC Collaboration, who also


discussed and approved the scientific results. L. Nava coordinated the gathering of the data, developed the


theoretical interpretation, and wrote the main section and the section on Afterglow Modeling. E. Moretti


coordinated the analysis of the MAGIC data, wrote the relevant sections, and, together with F. Longo, co

ordinated the collaboration with the Fermi team. D. Miceli, Y. Suda and S. Fukami performed the analysis


of the MAGIC data. S. Covino provided support with the analysis of the optical data and the writing of


the corresponding sections. Z. Bosnjak performed calculations for the contribution from prompt emission


to TeV radiation and wrote the corresponding section. A. Stamerra, D. Paneque and S. Inoue contributed in


64

structuring and editing the paper. A. Berti contributed to editing and finalising the manuscript. R. Mirzoyan


coordinated and supervised the paper. All MAGIC collaborators contributed to the editing and comments to


the final version of the manuscript.


S. Campana and M. G. Bernardini extracted the spectra and performed the spectral analysis of _Swift_ /BAT


and _Swift_ /XRT data. N. P. M. Kuin derived the photometry for the _Swift_ /UVOT event mode data, and the uv


grism exposure. M. H. Siegel derived the image mode Swift UVOT photometry. A. de Ugarte Postigo was


principal investigator of ALMA program 2018.1A.00020.T, triggered these observations and performed


photometry. S. Martin reduced the ALMA Band 6 data. C. C. Th¨one, S. Schulze, D. A. Kann, and M.


Michałowski participated in the ALMA DDT proposal preparation, observations, and scientific analysis of


the data. D. A. Perley was principal investigator of ALMA program 2018.1.01410.T and triggered these


observations, and was also principal investigator of the LT programme and the JCMT programme. A. M.


Cockeram analyzed the ALMA Band 3 and LT data, and wrote the LT text. S. Schulze contributed to the


development of the ALMA Band 3 observing programme. I. A. Smith triggered the JCMT programme,


analyzed the data, and wrote the associated text. N. R. Tanvir contributed to the development of the JCMT


programme. D. A. Kann and C. C. Th¨one triggered and coordinated the X-shooter observations. D. A. Kann


independently checked the optical light curve analysis. K. Misra was the principal investigator of the GMRT


programme 35 ~~0~~ 18. S. V. Cherukuri and V. Jaiswal analyzed the data. L. Resmi contributed to the observa

tion plan and data analysis. E.T., I.H. and R.D. have performed the MeerKAT data analysis. G. Anderson,


A. Moin, S. Schulze and E. Troja were principal investigator of ATCA program CX424. G. Anderson, M.


Wieringa and J. Stevens carried out the observations. G. Anderson, G. Bernardi, S. Klose, M. Marongiu, A.


Moin, R. Ricci and M. Wieringa analysed these data. M. Bell, J. Miller-Jones and L. Piro participated to the


ATCA proposal preparation and scientific analysis of the data. The ePESSTO project was delivered by the


following who have contributed to managing, executing, reducing, analysing ESO/NTT data and provided


65

comments to the manuscript: J. P. Anderson, N. Castro Segura, P. D’Avanzo, M. Gromadzki, C. Inserra,


E. Kankare, K. Maguire, M. Nicholl, F. Ragosta, S. J. Smartt. A. Melandri and A. Rossi reduced and an

alyzed REM data and provided comments to the manuscript. J. Bolmer was responsible for observing the


GRB with GROND as well as for the data reduction and calibration. J. Bolmer and J. Greiner contributed to


the analysis of the data and writing of the text. E. Troja triggered the _NuSTAR_ TOO observations performed


under DDT program, L. Piro requested the XMM-Newton data carried out under DDT program and carried


out the scientific analysis of XMM-Newton and _NuSTAR_ . S. Lotti analyzed the _NuSTAR_ data and wrote the


associated text. A. Tiengo and G. Novara analysed the XMM-Newton data and wrote the associated text.


AJCT led the observing BOOTES and GTC programs. AC, CJPP, EFG, IMC, SBP and XYL analyzed the


BOOTES data whereas AFV, MDCG, RSR, YDH and VVS analyzed the GTC data and interpreted them


accordingly. N. Tanvir created the X-shooter and AlFOSC figures. J. Fynbo, J. Japelj performed the analy

sis of X-shooter and AlFOSC spectra. D. Xu, P. Jakobsson contributed to NOT programme and triggering.


D. Malesani performed photometric analysis of NOT data. E. Peretti contributed to developing the code for


modeling of afterglow radiation. L. Izzo triggered and analysed the OASDG data, while A. Di Dato and A.


Noschese executed the observations at the telescope.


**Data Availability Statement** Data are available from the corresponding authors upon request.


**Code Availability Statement** Proprietary data reconstruction codes were generated at the MAGIC tele

scopes large-scale facility. Information supporting the findings of this study are available from the corre

sponding authors upon request.


66


</paper>

## Items to check

```json
[
 {
  "path": "paper_type_evidence[0]",
  "value": "paper type: multi_facility_alma_minor",
  "failed_quote": "Here we present the results of our multi-frequency observational campaign of GRB 190114C, and study the evolution in time of the GRB emission across 17 orders of magnitude in energy"
 },
 {
  "path": "science.question.evidence[0]",
  "value": "What is the broadband emission of GRB 190114C from radio to TeV, and is the TeV emission a distinct inverse Compton (SSC) component of the afterglow?",
  "failed_quote": "We find that the broadband spectral energy distribution is double-peaked, with the TeV emission constituting a distinct spectral component that has power comparable to the synchrotron component."
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Numerical code solving electron distribution evolution with synchrotron, SSC, adiabatic losses, gamma-gamma absorption, pairs, self-absorption",
  "failed_quote": "we use a numerical code that solves the evolution of the electron distributions and derives the radiative output"
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "The TeV emission is a distinct spectral component, explained by SSC in the afterglow forward shock.",
  "failed_quote": "This component is associated with the afterglow, and is satisfactorily explained by inverse Compton upscattering of synchrotron photons by high-energy electrons."
 }
]
```
