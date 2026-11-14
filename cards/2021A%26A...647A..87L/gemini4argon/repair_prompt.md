# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...647A..87L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. SMM1_C2H3NO_isomers ©ESO 2021
January 1, 2021

## **The prebiotic molecular inventory of Serpens SMM1**

### **I. An investigation of the isomers CH 3 NCO and HOCH 2 CN**


N.F.W. Ligterink [1], A. Ahmadi [2], A. Coutens [3], Ł. Tychoniec [2] H. Calcutt [4][,][ 5], E.F. van Dishoeck [2][,][ 6], H. Linnartz [7], J.K.
Jørgensen [8], R.T. Garrod [9], and J. Bouwman [7]


1 Physics Institute, University of Bern, Sidlerstrasse 5, 3012 Bern, Switzerland
e-mail: `niels.ligterink@csh.unibe.ch`
2 Leiden Observatory, Leiden University, PO Box 9513, 2300 RA Leiden, The Netherlands
3 Laboratoire d’Astrophysique de Bordeaux, Univ. Bordeaux, CNRS, B18N, allée Geoffroy Saint-Hilaire, 33615 Pessac, France
4 Department of Space, Earth and Environment, Chalmers University of Technology, 41296, Gothenburg, Sweden
5 Institute of Astronomy, Faculty of Physics, Astronomy and Informatics, Nicolaus Copernicus University, Grudziadzka 5, 87-100
Torun, Poland
6 Max-Planck Institut für Extraterrestrische Physik (MPE), Giessenbachstr. 1, 85748 Garching, Germany
7 Laboratory for Astrophysics, Leiden Observatory, Leiden University, PO Box 9513, 2300 RA Leiden, The Netherlands
8 Centre for Star and Planet Formation, Niels Bohr Institute & Natural History Museum of Denmark, University of Copenhagen,
Øster Voldgade 5–7, 1350 Copenhagen K., Denmark
9 Departments of Chemistry and Astronomy, University of Virginia, Charlottesville, VA 22904, USA


Received October 8, 2020; accepted December 22, 2020


**ABSTRACT**


_Aims._ Methyl isocyanate (CH 3 NCO) and glycolonitrile (HOCH 2 CN) are isomers and prebiotic molecules that are involved in the
formation of peptide structures and the nucleobase adenine, respectively. These two species are investigated to study the interstellar
chemistry of cyanides (CN) and isocyanates (NCO) and to gain insight into the reservoir of interstellar prebiotic molecules.
_Methods._ ALMA observations of the intermediate-mass Class 0 protostar Serpens SMM1-a and ALMA-PILS data of the low-mass
Class 0 protostar IRAS 16293B are used. Spectra are analysed with the CASSIS line analysis software package in order to identify
and characterise molecules.
_Results._ CH 3 NCO, HOCH 2 CN, and various other molecules are detected towards SMM1-a. HOCH 2 CN is identified in the PILS data
towards IRAS 16293B in a spectrum extracted at a half-beam offset position from the peak continuum. CH 3 NCO and HOCH 2 CN
are equally abundant in SMM1-a at [X]/[CH 3 OH] of 5.3×10 [−][4] and 6.2×10 [−][4], respectively. A comparison between SMM1-a and
IRAS 16293B shows that HOCH 2 CN and HNCO are more abundant in the former source, but CH 3 NCO abundances do not differ
significantly. Data from other sources are used to show that the [CH 3 NCO]/[HNCO] ratio is similar in all these sources within ∼10%.
_Conclusions._ The new detections of CH 3 NCO and HOCH 2 CN are additional evidence for a large interstellar reservoir of prebiotic
molecules that can contribute to the formation of biomolecules on terrestrial planets. The equal abundances of these molecules in
SMM1-a indicate that their formation is driven by kinetic processes instead of thermodynamic equilibrium, which would drive the
chemistry to one product. HOCH 2 CN is found to be much more abundant in SMM1-a than in IRAS 16293B. From the observational
data, it is difficult to indicate a formation pathway for HOCH 2 CN, but the thermal Strecker-like reaction of CN [−] with H 2 CO is a
possibility. The similar [CH 3 NCO]/[HNCO] ratios found in the available sample of studied interstellar sources indicate that these
two species either are chemically related or their formation is affected by physical conditions in the same way. Both species likely
form early during star-formation, presumably via ice mantle reactions taking place in the dark cloud or when ice mantles are being
heated in the hot core. The relatively high abundances of HOCH 2 CN and HNCO in SMM1-a may be explained by a prolonged stage
of relatively warm ice mantles, where thermal and energetic processing of HCN in the ice results in the efficient formation of both
species.


**Key words.** Astrochemistry – Astrobiology – Individual Objects: Serpens SMM1 – ISM: abundances – Submillimeter: ISM



**1.** **Introduction**


Observations of molecules towards star-forming regions give insight into the kind of species that end up in planet-forming discs.
These molecules not only aid planet formation but can also seed
newly formed planets with a cocktail of molecules from which
larger organic molecules can be formed. Prebiotic molecules are
of particular interest, as they are involved in the formation of
biomolecules, such as amino acids, nucleobases, proteins, and
lipids (Sandford et al. 2020). In the interstellar medium (ISM)



and on planets, prebiotic molecules are the building blocks from
which biomolecules are made.

In the ISM, several prebiotic molecules have been detected. Examples are formamide (NH 2 CHO, Rubin et al.
1971) a precursor to nucleobases and amino acids (Saladino
et al. 2012), the simplest sugar-like molecule glycolaldehyde
(HOCH 2 CHO, Hollis et al. 2000; Jørgensen et al. 2012), methylamine (CH 3 NH 2, Kaifu et al. 1974; Bøgelund et al. 2019) and
aminoacetonitrile (NH 2 CH 2 CN, Belloche et al. 2008), building
blocks of the amino acid glycine (Holtom et al. 2005; Lee et al.
2009), the peptide building blocks acetamide (CH 3 C(O)NH 2 )


Article number, page 1 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers



Methyl isocyanate Glycolonitrile


Fig. (1) Structures of the C 2 H 3 NO isomers methyl isocyanate
(CH 3 NCO, left) and glycolonitrile (HOCH 2 CN, right).


and N-methylformamide (CH 3 NHCHO, Hollis et al. 2006;
Halfen et al. 2011; Belloche et al. 2017, 2019; Ligterink et al.
2020), the chiral molecule propylene oxide (CH 3 CHCH 2 O,
McGuire et al. 2016), cyanomethanimine (NHCHCN), which
can oligomerise to form adenine (Zaleski et al. 2013; Rivilla et al. 2019), and the nucleobase precursors cyanamide
(NH 2 CN, Turner et al. 1975; Coutens et al. 2018), hydroxylamine (NH 2 OH, Rivilla et al. 2020) and carbamide (also known
as urea, NH 2 C(O)NH 2, Belloche et al. 2019). Over the past
years, methyl isocyanate (CH 3 NCO, Halfen et al. 2015; Cernicharo et al. 2016; Ligterink et al. 2017) has been detected
in several interstellar sources and recently its isomer glycolonitrile (also known as hydroxy acetonitrile, HOCH 2 CN, Zeng
et al. 2019) was identified for the first time in the ISM towards the low-mass protostar IRAS 16293–2422B (hereafter
IRAS 16293B). Both these isomers are prebiotic molecules.
CH 3 NCO can engage in reactions that form peptide-like structures, while HOCH 2 CN is known to accelerate the oligomerisation of HCN in liquids and ice under terrestrial conditions,
forming the nucleobase adenine (Schwartz & Goverde 1982;
Schwartz et al. 1982).

Besides their relevance to prebiotic chemistry, CH 3 NCO and
HOCH 2 CN are also interesting molecules to gain insight into interstellar nitrogen chemistry. While these molecules, being isomers, have the same elemental composition (C 2 H 3 NO), their
chemical structures differ significantly, see Fig. 1. Recent quantum chemical calculations of the stability of C 2 H 3 NO isomers
in general, also reveal that CH 3 NCO is the most stable species
of those, followed by HOCH 2 CN (Fourré et al. 2020). Therefore, observations of this isomer couple provide information on
interstellar reactions involving cyanides (-CN) and isocyanates
(-NCO), two important nitrogen-bearing chemical groups, and
the physical conditions that steer or prohibit this chemistry.
After the first detection of CH 3 NCO (Halfen et al. 2015; Cernicharo et al. 2016), HNCO was suggested to be involved in its
formation due to their structural similarity and the large HNCO
abundances in interstellar gas and ice (in the form of OCN [−]
Boogert et al. 2015). Various gas-phase and solid-state methylation (the addition of a CH 3 functional group to a molecule)
reactions of HNCO, the OCN radical, and the OCN [−] anion have
been proposed as possible reaction pathways. Experimental investigations (Ligterink et al. 2017; Maté et al. 2018) and modeling studies (Martín-Doménech et al. 2017; Quénard et al. 2018;
Majumdar et al. 2018) indicate solid-state methylation in the ice
mantle as the main pathway to form CH 3 NCO:


CH 3 + NCO −−−→ CH 3 NCO · (1)


Article number, page 2 of 32



Variations of this pathway, such as the methylation of HNCO
or OCN [−] may be possible as well, while completely different
reactions, such as the hydrogenation of HCN. . .CO may form
CH 3 NCO as well.
No gas-phase formation pathways are known for glycolonitrile, but solid-state production routes have been studied theoretically (Woon 2001) and experimentally (Danger et al. 2012,
2014). Laboratory work indicates that the thermally activated
reaction between a cyanide anion (CN [−] ) and formaldehyde
(H 2 CO) forms HOCH 2 CN:


[XH [+] CN [−] ] + H 2 CO −−−→ HOCH 2 CN + X, (2)


where X is a molecule that can act as a base, such as ammonia (NH 3 ) or water (H 2 O). This reaction is the solid-state
equivalent of the Strecker synthesis, which is a sequence of
chemical reactions that produce amino acids. The Streckerlike formation of HOCH 2 CN is linked to the formation of
aminomethanol (HOCH 2 NH 2, Bossa et al. 2009) and aminoacetonitrile (NH 2 CH 2 CN, Danger et al. 2011). The latter of these
species is detected in the ISM and known as a possible intermediate in the formation of the amino acid glycine (Belloche
et al. 2008). Irradiation of HOCH 2 CN results in the photoproducts formylcyanide (HC(O)CN) and ketenimine (CH 2 CNH). Although not investigated, hydrogenation and oxygen additions of
these two species may provide pathways to form HOCH 2 CN in
the ISM. The solid-state radical-radical reactions HO + CH 2 CN
and HOCH 2 + CN can also form glycolonitrile, but neither of
these reactions has been investigated (Margulès et al. 2017).
However, precursor species to these reactions can be present in
ice mantles, in particular when methanol (CH 3 OH) or acetonitrile (CH 3 CN) are energetically processed (Allamandola et al.
1988; Hudson & Moore 2004; Bulak et al. 2020).
Methyl isocyanate and glycolonitrile can thus be used as
tracers of reactions involving CN and NCO and investigating
their interstellar abundances reveals information about the chemical and physical processes that drive these reactions and interstellar nitrogen chemistry as a whole. CH 3 NCO and HOCH 2 CN
have only been detected simultaneously in the low-mass protostar IRAS 16293B (Ligterink et al. 2017; Martín-Doménech
et al. 2017; Zeng et al. 2019), albeit in different observational
data sets. Due to this limited sample size, it is difficult to derive correlations or variations in the C 2 H 3 NO isomer chemistry
and therefore simultaneous identifications in other sources are
required. Here, deep ALMA observations of the intermediatemass Class 0 protostar Serpens SMM1-a (hereafter SMM1-a)
are presented to derive additional constraints on CH 3 NCO and
HOCH 2 CN chemistry.
The Serpens star-forming region contains multiple deeply
embedded sources, of which SMM1 is the brightest (Casali et al.
1993). The Serpens region contains multiple outflows and jets,
some of which originate from SMM1 (Dionatos et al. 2013; Hull
et al. 2016). The chemistry of the SMM1 hot corino, its outflows, and the Serpens core have been characterised in various
studies (e.g., White et al. 1995; Hogerheijde et al. 1999; Kristensen et al. 2010; Öberg et al. 2011; Goicoechea et al. 2012; Tychoniec et al. 2019). High-resolution continuum jet observations
have shown that SMM1 consists of multiple sources, of which
SMM1-a is the main one (Choi 2009; Dionatos et al. 2014; Hull
et al. 2017). SMM1-a has SMM1-b as a close neighbor at ∼500
au, while two other sources, SMM1-c and -d, are located further away to its north. Recent distance measurements place the
Serpens core, and therefore SMM1, at a distance of 436.0±10
pc (Ortiz-León et al. 2017), resulting in a luminosity estimate of
the entire SMM1 source of ∼100 _L_ ⊙ . SMM1-a is considered to

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1



be an intermediate-mass protostar (Hull et al. 2017; Tychoniec
et al. 2019).
In this work, the detection and analysis of the isomers
HOCH 2 CN and CH 3 NCO towards SMM1-a are presented and
compared with literature results of IRAS 16293B and those of
other sources. In section 2 the observations towards SMM1 and
the analysis method are presented. The detections of HOCH 2 CN,
CH 3 NCO, and various other molecules are presented in section
3. Section 4 discusses these detections and their likely formation
pathways. The conclusions of this work are presented in section
5.


**2.** **Data & Methods**


_2.1._ _Observations and spectra of Serpens SMM1_


SMM1 was observed on 27-March-2019 during ALMA cycle 6,
as part of project #2018.1.00836.S (PI: N.F.W. Ligterink). The
region was observed using a total of 42 antennae with baselines
spanning 15 – 332 meters in configuration C43-5. The on-source
integration time was 50 minutes, towards the phase centre α J2000
= 18:29:49.80 δ J2000 = +01:15:20.6. Spectra were recorded in
select frequency windows between 217.59 and 235.93 GHz, at
resolutions of 488.21 kHz (0.33 km s [−][2] ) and 1952.84 kHz (1.25
km s [−][2] ) for the continuum window, see Table 1. The data were
calibrated and imaged with version 5.4.0-70 of the Common
Astronomy Software Applications (CASA). Bandpass and flux
calibration was conducted on J2000–1748, while phase calibration was performed on J1851+0035. The flux uncertainty was
≤20%. To reach the desired sensitivity, the measurement sets
were cleaned using the Hogbom algorithm (Högbom 1974) and
Briggs weighting with a robust parameter of 0.5. This resulted
in an angular resolution of 1 [′′] . 32×1 [′′] . 04 and an rms noise of 2.6
mJy beam [−][1] km s [−][1] in the final spectral data cubes. The primary
beam of the observations was 26 [′′] .


Table (1) Frequency settings of ALMA SMM1 observations


Frequency range Bandwidth Resolution
(GHz) (GHz) (kHz) (km s [−][1] )
217.59 – 217.70 0.117 488.21 0.33

217.97 – 218.09 0.117 488.21 0.33

218.43 – 218.55 0.117 488.21 0.33

218.92 – 219.03 0.117 488.21 0.33

219.71 – 219.82 0.117 488.21 0.33

221.30 – 221.42 0.117 488.21 0.33

221.42 – 221.53 0.117 488.21 0.33

221.53 – 221.65 0.117 488.21 0.33

231.74 – 231.97 0.234 488.21 0.33

233.41 – 233.65 0.234 488.21 0.33

234.06 – 235.93 1.875 1952.84 1.25


Due to the line-richness of the source, the following procedure was followed to properly subtract the continuum from
the line observations. We imaged all spectral windows without
the continuum removed and used the corrected sigma-clipping
method of the STATCONT package [1] (Sánchez-Monge et al.
2018) to extract a continuum-subtracted line cube. STATCONT
can only subtract zeroth-order polynomials, while in this dataset
non-zeroth-order baselines are visible. Furthermore, continuum
subtraction in the uv-plane is more desirable since the deconvolution of the line emission is more robust when it is not subjected


1 `[https://hera.ph1.uni-koeln.de/~sanchez/statcont](https://hera.ph1.uni-koeln.de/~sanchez/statcont)`



to the deconvolution errors of the brighter continuum. Therefore, the STATCONT outputs were used to identify the line-free
channels in the spectra and the continuum was subtracted in the
uv-plane with the _uvcontsub_ task in CASA. Line-free channels
are sparse, but for most spectral windows, at least 20% of the
bandwidth was given as input to the _uvcontsub_ task, with the exception of two spectral windows, where only 10% of the bandwidth was line-free. From the resulting datacube, the SMM1a hot core spectrum was extracted towards the peak continuum
position α J2000 = 18:29:49.793, δ J2000 = +1.15.20.200. From the
average continuum flux density (0.41 mJy beam [−][1] ), the background temperature was determined to be ∼5.2 K.


_2.2._ _PILS observations and spectra of IRAS 16293B_


In this work, the column density of HOCH 2 CN is determined independently from the detection presented by (Zeng et al. 2019)
by analysing data from the Protostellar Interferometric Line Survey (PILS). Other species relevant to this work are also searched
for in the PILS data set. The observational details of the PILS
survey have been presented in various other publications (e.g.,
Jørgensen et al. 2016) and here only the most relevant information is presented. In short, the PILS survey makes use of ALMA
band 7 observations, covering a frequency range from 329 to
363 GHz at a spatial resolution of 0 [′′] . 5. To investigate the chemical inventory of IRAS 16293B, spectra are extracted at several
positions. These positions are on the peak continuum, a halfbeam offset from the peak continuum, and a full-beam offset
from the peak continuum. Most PILS analyses of IRAS 16293B
make use of the spectrum at the full-beam offset position Jørgensen et al. (e.g., 2016); Coutens et al. (e.g., 2016); Ligterink
et al. (e.g., 2017); Coutens et al. (e.g., 2018); Persson et al. (e.g.,
2018); Calcutt et al. (e.g., 2018); Jørgensen et al. (e.g., 2018). In
this work, this is the main position for which molecular ratios
with HOCH 2 CN are determined, but the spectra of other positions are also analysed. The systemic velocity towards these positions is _V_ LSR = 2.7 km s [−][1] and the line width is approximately
∆ _V_ = 1.0 km s [−][1] . Due to the dense dust around IRAS 16293B,
the background temperatures ( _T_ BG ) at these positions are higher
than the cosmic microwave background radiation temperature of
2.7 K and couple with the molecular line emission (see Ligterink
et al. 2018). At the full-beam offset position _T_ BG = 21 K, while
at the half-beam offset position it is _T_ BG = 52 K.


_2.3._ _Analysis method_


The spectra were analyzed with the CASSIS [2] line analysis software. Spectral line lists were obtained from the JPL database
for molecular spectroscopy (Pickett et al. 1998), the Cologne
Database for Molecular Spectroscopy (CDMS, Müller et al.
2001, 2005), and from literature. An overview of the spectroscopic line lists used in this work and the laboratory works they
are based on is given in Appendix A. Given a spectroscopic
line list as input, CASSIS can produce synthetic spectra of a
molecule based on parameters such as column density ( _N_ T ), excitation temperature ( _T_ ex ), peak gas velocity ( _V_ LSR ), line width at
half maximum (∆ _V_ ), and source size (θ source ). These parameters
were given as free parameters to a Monte-Carlo Markov Chain
(MCMC) algorithm and χ [2] minimisation routine. This routine
finds the best-fit of a synthetic spectrum to an observed spectrum over a specified parameter space, thereby determining the


2 CASSIS has been developed by IRAP-UPS/CNRS
(http://cassis.irap.omp.eu)


Article number, page 3 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers



HOCH 2 CN - 24 8, 17, 0 -23 8, 16, 0 - E up = 222K


0.08



CH 3 NCO - 25 0, 0, 2 -24 0, 0, 2 - E up = 188K


0.08







0.07


0.06


0.05


0.04


0.03


0.02


0.01







0.07


0.06


0.05


0.04


0.03


0.02


0.01



















Right ascension (J2000)



Right ascension (J2000)



Fig. (2) Moment 0 maps of the HOCH 2 CN 24 8,17/16 –23 8,16/15, E up = 222 K line and the CH 3 NCO ν=0 25 0,0 –24 0,0, E up = 188 K
line towards SMM1. Both lines are integrated over 8 velocity bins, centered on the peak frequency of each line as determined
towards SMM1-a. Positions of protostars in the SMM1 region are indicated and the beam size (1 [′′] . 32×1 [′′] . 04) is visualised in the
bottom left corner. Dust continuum contours are given by the black dotted line at the levels of 0.02, 0.05, 0.1, 0.2, 0.5 Jy Beam [−][1] .


Table (2) Best-fit parameters for molecules detected towards SMM1-a in a 1 [′′] . 2 beam.


Molecule Lines _N_ T _T_ ex _V_ LSR ∆ _V_ [X] / [CH 3 OH] [X] / [HNCO]
# (cm [−][2] ) (K) km s [−][1] km s [−][1]

HOCH 2 CN 18 (7.4±0.9)×10 [14] 260±45 6.8±0.2 2.5±0.3 6.2×10 [−][4] 7.4×10 [−][2]

CH 3 NCO 12 (6.4±1.9)×10 [14] 240±60 7.0±0.4 3.0±0.6 5.3×10 [−][4] 6.4×10 [−][2]

D 2 CO 3 (5.4±2.5)×10 [14] [200] 7.4±0.4 3.9±0.2 4.5×10 [−][4] 5.4×10 [−][2]

CH [18] 3 [OH] 4 (2.0±1.1)×10 [15] 250±60 7.1±0.2 2.8±0.3 – –
12 CH 3 OH _a_ 5 _[b]_ 1.1×10 [18] – – – 1.0 110
CH 3 CN _[c]_ 6 (1.3±0.3)×10 [15] 190±25 7.5±0.2 3.4±0.3 1.1×10 [−][3] 0.1
NH 2 CN 3 (5.1±1.3)×10 [13] 190±40 7.1±0.2 3.2±0.4 4.3×10 [−][5] 5.1×10 [−][3]

HN [13] CO 3 (1.9±0.3)×10 [14] 190±30 7.6±0.2 3.5±0.3 – –
HN [12] CO _[a]_ 5 _[b]_ 1.0×10 [16] – – – 1.1×10 [−][2] 1.0
CH 3 CH 2 OH 14 (4.1±0.9)×10 [15] 210±25 7.3±0.2 2.8±0.6 4.1×10 [−][3] 0.3
CH 3 OCHO 24 (7.4±0.7)×10 [15] 215±20 7.3±0.2 3.1±0.3 7.4×10 [−][3] 0.6
a-(CH 2 OH) 2 14 (1.7±0.5)×10 [15] 195±70 7.2±0.2 2.7±0.3 1.7×10 [−][3] 0.1
CH 3 CNO 0 ≤1.0×10 [13] [200] [7.0] [3.5] ≤9.1×10 [−][6] ≤1.0×10 [−][3]

CH 3 OCN 0 ≤5.0×10 [13] [200] [7.0] [3.5] ≤4.6×10 [−][6] ≤5.0×10 [−][3]

CH 2 CNH 0 ≤1.0×10 [15] [200] [7.0] [3.5] ≤8.3×10 [−][4] 0.1
CH(O)CN 0 ≤2.0×10 [14] [200] [7.0] [3.5] ≤1.7×10 [−][4] ≤2.0×10 [−][2]

NH 2 CH 2 CN 0 ≤1.0×10 [14] [200] [7.0] [3.5] ≤8.3×10 [−][5] ≤1.0×10 [−][2]


**Notes.** Values in brackets are assumed. _[a]_ Main isotopologue column densities are determined by applying the ratios [16] O/ [18] O = 560 and [12] C/ [13] C =
52.5 to the minor isotopologue column densities. _[b]_ The number of lines identified of the main isotopologue in this data set. _[c]_ The CH 3 CN best-fit
parameters are determined from its vibrationally excited state ν 8 =1.



best-fit parameters and thus column density and excitation temperature of a molecule. For the analysis, optically thin lines (τ ≪
1.0) were used. The τ-value was approximated from the by-eye
synthetic fit (see below) of the observed rotational lines with the
CASSIS software. The molecules were assumed to be in local
thermodynamic equilibrium (LTE). Errors on physical parameters take the uncertainty of the fit and the flux uncertainty as
input and are calculated from the spread in χ [2] values around the
minimum to a 3σ confidence level.

In this work, spectral lines of a molecule were identified in
the observed spectra and a by-eye synthetic fit of the lines was
made. For the by-eye fit, line width and peak velocity are determined from prominent spectral lines of molecules such as


Article number, page 4 of 32



HNCO and CH 3 OH and used as a first approximation for other
molecules. An excitation temperature of 200 K is taken as an
initial guess and followed by a round of adjusting column density and rotational temperature until a reasonable by-eye fit was
found. The by-eye fit results were given as starting parameters
for the MCMC χ [2] minimisation routine. The χ [2] minimisation
was performed on lines that are not blended and have minimal contributions from the wings of neighboring lines. Blending
species were identified by checking the line position for other
lines of known hot core / corino species with A ij - 1×10 [−][6] and
E up of 0–1000 K. The column density was given as a free parameter over two orders of magnitude centered on the by-eye fit column density and the excitation temperature was a free parameter

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1


Table (3) Best-fit parameters of HOCH 2 CN and related species towards IRAS 16923B in the PILS data set in a 0 [′′] . 5 beam


Molecule _N_ T _T_ ex [X] / [CH 3 OH] _[a]_ [X] / [HNCO] _[a]_

(cm [−][2] ) (K)
HOCH 2 CN ≤1.0×10 [15] [150] ≤1.0×10 [−][4] ≤3.3×10 [−][2]

HOCH 2 CN ≤1.0×10 [15] [300] ≤1.0×10 [−][4] ≤3.3×10 [−][2]

CH 2 CNH ≤1.0×10 [15] [100] ≤1.0×10 [−][4] ≤3.3×10 [−][2]

CH 2 CNH ≤2.0×10 [15] [300] ≤2.0×10 [−][4] ≤6.7×10 [−][2]

CH(O)CN ≤5.0×10 [14] [100] ≤5.0×10 [−][5] ≤1.7×10 [−][2]

CH(O)CN ≤5.0×10 [14] [300] ≤5.0×10 [−][5] ≤1.7×10 [−][2]

NH 2 CH 2 CN ≤1.0×10 [15] [100] ≤1.0×10 [−][4] ≤3.3×10 [−][2]

NH 2 CH 2 CN ≤5.0×10 [14] [300] ≤5.0×10 [−][5] ≤1.7×10 [−][2]


**Notes.** Values in brackets are assumed. _V_ LSR = 2.7 km s [−][1] and ∆ _V_ = 1.0 km s [−][1] . Note that some upper limit column densities are similar because
the upper state energies of the lines cover only a narrow range of energies. _[a]_ CH 3 OH and HNCO column densities were adopted from Jørgensen
et al. (2018) and Coutens et al. (2016), respectively.



HOCH 2 CN - 36 4, 32 -35 4, 31 - E up = 324K


0.040







0.035


0.030


0.025


0.020


0.015



|-24°28'31<br>Declination(J2000)<br>32<br>33<br>34<br>35|"<br>" half beam<br>" full beam<br>"<br>1 =141AU<br>"<br>16h32m22.7s 22.6s 22.5s<br>Rightascension(J2000)|Col3|
|---|---|---|
|-24°28'31<br>32<br>33<br>34<br>35<br>Declination (J2000)|16h32m22.7s<br>22.6s<br>22.5s<br>"<br>"<br>"<br>"<br>"<br>Right ascension (J2000)<br>half<br>beam<br>full<br>beam<br>1 = 141 AU|16h32m22.7s<br>22.6s<br>22.5s<br>Right ascension (J2000)|


Fig. (3) Moment 0 map of the HOCH 2 CN 36 4,32 –35 4,31, E up =
324 K line towards IRAS 16293B. The line is integrated over
8 velocity bins, centered on the peak frequency of the line. The
positions of the half-beam and full-beam offset positions around
IRAS 16293B are indicated and the beam size (0 [′′] . 5×0 [′′] . 5) is visualised in the bottom left corner. Dust continuum contours are
given by the black dotted line at the levels of 0.02, 0.05, 0.1, 0.2,
0.5 Jy Beam [−][1] .


from 50 – 350 K. For SMM1-a, ∆ _V_ was a free parameter from
1.0 – 4.0 km s [−][1], and the source velocity was a free parameter
between 6.0 – 9.0 km s [−][1] . The source size was assumed to be
equal to the beam size and taken to be 1 [′′] . 2, resulting in a beam
filling factor of 0.5. A background continuum temperature ( _T_ bg )
of 5.2 K was used.
For the analysis of IRAS 16293B, ∆ _V_ and _V_ LSR were fixed
to 1.0 km s [−][1] and 2.7 km s [−][1], respectively. The source size was
assumed to be equal to the beam size at 0 [′′] . 5, while a background
continuum temperature of _T_ bg = 21 K was used.


**3.** **Results**


_3.1._ _SMM1_


In the spectra of SMM1-a, multiple unblended rotational lines
of the isomers HOCH 2 CN and CH 3 NCO ν=0 are found. Moment 0 maps (the spatial mapping of the integrated line intensity of a single rotational line) of both species show that



most emission originates from SMM1-a, see Fig. 2. The identified lines towards SMM1-a are presented in Figs. 4 and 5. For
HOCH 2 CN, this is the second independent interstellar detection
of this molecule (the first detection of HOCH 2 CN was presented
towards IRAS 16293B by Zeng et al. 2019), while the first detection of CH 3 NCO towards SMM1-a is part of only a handful
of detections of this species towards other interstellar sources.
Several other species are identified in the SMM1-a spectra as well. Rotational lines of acetonitrile (CH 3 CN ν 8 =1),
cyanamide (NH 2 CN), ethanol (CH 3 CH 2 OH), the anti-conformer
of ethylene glycol (a-(CH 2 OH) 2 ), deuterated formaldehyde
(D 2 CO), isocyanic acid (HN [12] CO and HN [13] CO), methylformate
(CH 3 OCHO), and methanol ( [12] CH 3 OH and CH [18] 3 [OH)] [are] [de-]
tected. Rotational lines of the C 2 H 3 NO isomers methyl fulmiate
(CH 3 CNO) and methyl cyanate (CH 3 OCN) were not identified
in the spectra. The molecules aminoacetonitrile (NH 2 CH 2 CN),
ketenimine (CH 2 CNH), and formylcyanide (HC(O)CN) are
searched for, but not identified. Spectra are presented in Appendix B and spectroscopic parameters of transitions are provided in Table 5. Following the procedure detailed in Sect. 2.3,
the best-fit parameters of these species are determined. For undetected species, upper limit column densities are determined by
assuming _T_ ex = 200 K, which is chosen as a representative excitation temperature from the molecules that are detected. The fit
parameters are presented in Table 2. The main isotopologues of
CH 3 OH and HNCO are optically thick and their column densities are therefore determined from minor isotopologues. This is
done by multiplying with the local interstellar [12] C/ [13] C ratio of
52.5±15.4 (Yan et al. 2019) and [16] O/ [18] O ratio of 560 (Wilson
1999).


_3.2._ _IRAS 16293B_


Because the chemical inventory of IRAS 16293B is well characterised with results from the PILS survey, this data set is used
to search for HOCH 2 CN and related species to make an unbiased chemical comparison with SMM1-a. While HOCH 2 CN
was identified towards IRAS 16293B by Zeng et al. (2019), this
detection cannot be confirmed in the PILS spectrum at the fullbeam offset position (the position commonly used for the molecular analysis of IRAS 16293B with PILS data, see Fig.3). Figthisure 6positionshows thecoveredHOCHby 2 CNthea-typePILS spectraltransitionsrange( _J_ 0 [′], _J_ with [′] [–] _[J]_ 0 [′′] a, _J_ [′′] syn- [)] [at]
thetic glycolonitrile spectrum at _N_ T = 1.0×10 [15] cm [−][2] and _T_ ex

=
150 and 300 K. A synthetic spectrum of the previously identified molecules towards IRAS 16293B at the full-beam offset


Article number, page 5 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers


HOCH 2 CN - Serpens SMM1-a





0.6


0.4


0.2


0.0



























218980 218990 219000



221320 221330 221340



221330 221340 221350



221360 221370 221380





0.6


0.4


0.2


0.0


0.6


0.4


0.2


0.0



0.6



0.6


0.4


0.2


0.0



24 6, 19/18, 1 23 6, 18/17, 1



221400 221410 221420


24 8, 17/16, 0 23 8, 16/15, 0



24 12, 13/12, 1 23 12, 12/11, 1



24 3, 22, 1 23 3, 21, 1







0.4


0.2


0.0


221460 221470 221480





0.2


0.0


221400 221410 221420



0.6


0.4


0.2


0.0



24 7, 18/17, 0 23 7, 17/16, 0



24 9, 16/15, 0 23 9, 15/14, 0



221460 221470 221480


24 10, 15/14, 0 23 10, 14/13, 0



0.2









0.0


0.6


0.4


0.2


0.0


0.6


0.4


0.2


0.0



221470 221480 221490



221490 221500 221510



0.6


0.4


0.2


0.0



221510 221520 221530



24 13, 12/11, 1 23 13, 11/10, 1





24 6, 19/18, 0 23 6, 18/17, 0



221480 221490 221500


24 5, 20, 1 23 5, 19, 1


0.2


0.0


0.2


0.0






|1490 221500 221490 221500 221510 221510 221520 221530 235, 19, 1 245, 19, 1 235, 18, 1 0.6 2411, 14/13, 0 2311, 13/12, 0|Col2|
|---|---|
|0 221540<br>221530 221540 221550<br>0.0<br>0.2<br>0.4<br>173 K<br>221550 221560 221570<br>0.0<br>0.2<br>0.4<br>0.6<br>301 K<br>2312, 12/11, 0<br>0.0<br>0.2<br>0.4<br>157 K<br>252, 23, 1<br>242, 22, 1<br>0.2<br>0.0<br>0.2<br>0.4<br>152 K<br>252, 23, 0<br>242, 22, 0|0 221540<br>221530 221540 221550<br>0.0<br>0.2<br>0.4<br>173 K<br>221550 221560 221570<br>0.0<br>0.2<br>0.4<br>0.6<br>301 K<br>2312, 12/11, 0<br>0.0<br>0.2<br>0.4<br>157 K<br>252, 23, 1<br>242, 22, 1<br>0.2<br>0.0<br>0.2<br>0.4<br>152 K<br>252, 23, 0<br>242, 22, 0|
|0.0|0.2<br>0.0|



221550 221560 221570 221600 221610 221620 234570 234580 234590 235100 235110 235120

Frequency (MHz)



221550 221560 221570



221600 221610 221620



234570 234580 234590



235100 235110 235120



Fig. (4) Identified lines of HOCH 2 CN towards SMM1. The observed spectrum is plotted in black, with the best-fit synthetic
spectrum overplotted in blue ( _N_ T = (7.4±0.9)×10 [14] cm [−][2], _T_ ex = 260±45 K). The transition is indicated at the top of each panel and
the upper state energy is given in the top left of each panel.



position is added in green. Note that this synthetic spectrum
only includes molecules listed in previous publications and does
not include HOCH 2 CN. The molecules and parameters used in
this fit are listed in Table 5. When a rotational spectrum is experimentally measured, a-type transitions are usually the first
and most accurately determined transitions. The assignment of
these a-type transitions, therefore, is key to claim an unambiguous identification. However, of the seven a-type transitions covered by the PILS survey, only the 39 0,39,1 – 38 0,38,1 transition
at 344625 MHz is possibly detected, although this feature has
a contribution of a HONO and CH 2 DOH transition (Jørgensen
et al. 2016, 2018; Coutens et al. 2019), which also can fully reproduce this line. Appendix C presents all the HOCH 2 CN transitions at the full-beam offset position that are largely unblended


Article number, page 6 of 32



and have _A_ ij ≥ 1×10 [−][3] s [−][1] . At the full-beam offset position, a

∼
large number ( 40) of glycolonitrile transitions that are present
in the synthetic spectrum are not seen in the observed spectrum.
We note that due to the line-richness of the source the baseline
subtraction is challenging and in some cases, it can be oversubtracted. This can explain why certain HOCH 2 CN lines are not
clearly observed, as the baseline at these positions dips. Furthermore, some transitions seem to be better reproduced with low
excitation temperatures, whereas others require warmer temperatures. This could indicate that two gas components are traced,
as also shown by Zeng et al. (2019), but at this position these
components are hard to distinguish. Therefore, HOCH 2 CN can
only tentatively be identified towards the full-beam offset posi

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1





























235650 235660 235670















234080 234090 234100





234920 234930 234940







231780 231790 231800


|CH 3NCO Serpens SMM<br>-<br>25 24 25 24 25<br>102 102 002 002 201<br>0140,,,, 04,,,, 03,,<br>.. . .<br>194K 188K 171K<br>02<br>02 02 .<br>. .<br>01<br>.|Col2|1 -a<br>24 24 23<br>201 301 301<br>,, 03,,,,<br>.<br>191K<br>02<br>.<br>01<br>.|
|---|---|---|
|217590 217600 217610<br>0.0<br>217590 <br>0.0<br>0.1<br>0.2<br>0.3<br>258 K<br>251, 0,<br>3<br>241, 0,<br>3<br>0.1<br>0.2<br>0.3<br>251 K<br>250, 0,<br>3<br>0.6<br>0.8|217590 217600 217610<br>0.0<br>217590 <br>0.0<br>0.1<br>0.2<br>0.3<br>258 K<br>251, 0,<br>3<br>241, 0,<br>3<br>0.1<br>0.2<br>0.3<br>251 K<br>250, 0,<br>3<br>0.6<br>0.8|217590 217600 217610<br>0.0<br>217590 <br>0.0<br>0.1<br>0.2<br>0.3<br>258 K<br>251, 0,<br>3<br>241, 0,<br>3<br>0.1<br>0.2<br>0.3<br>251 K<br>250, 0,<br>3<br>0.6<br>0.8|
|217990 218000 218010<br>0.0<br>218000 218010 218020<br>0.0<br>218060 218<br>0.0<br>0.2<br>0.4<br>175 K<br>27<br>1, 0, 1<br>26<br>1, 0, 1<br><br>0.2<br>181 K<br>272, 26, 0<br>262, 25, 0<br>0.2<br>0.4<br>210 K<br>270, 0, 2<br>0.4<br>TB (K)|217990 218000 218010<br>0.0<br>218000 218010 218020<br>0.0<br>218060 218<br>0.0<br>0.2<br>0.4<br>175 K<br>27<br>1, 0, 1<br>26<br>1, 0, 1<br><br>0.2<br>181 K<br>272, 26, 0<br>262, 25, 0<br>0.2<br>0.4<br>210 K<br>270, 0, 2<br>0.4<br>TB (K)|217990 218000 218010<br>0.0<br>218000 218010 218020<br>0.0<br>218060 218<br>0.0<br>0.2<br>0.4<br>175 K<br>27<br>1, 0, 1<br>26<br>1, 0, 1<br><br>0.2<br>181 K<br>272, 26, 0<br>262, 25, 0<br>0.2<br>0.4<br>210 K<br>270, 0, 2<br>0.4<br>TB (K)|
|22<br>0.0|2<br>222<br>0.0<br>2222<br>0.0<br>222<br>0.0|2<br>222<br>0.0<br>2222<br>0.0<br>222<br>0.0|





0.3


0.2


0.1


0.0



27 2, 0, 3 26 2, 0, 3






|231800 234080 23 262, 0, 3 0.3 272, 0, 3|34090 234100 234920 234930 234940 235650 235660 235670 262, 0, 3|
|---|---|
|0.1<br>0.2<br>0.3<br>297 K||
|0.0||



235790 235800 235810 235790 235800 235810

Frequency (MHz)



235790 235800 235810



235790 235800 235810



Fig. (5) Identified lines of CH 3 NCO, ν=0 towards SMM1. The observed spectrum is plotted in black, with the best-fit synthetic
spectrum overplotted in blue ( _N_ T = (6.4±1.9)×10 [14] cm [−][2], _T_ ex = 240±60 K). The transition is indicated at the top of each panel and
the upper state energy is given in the top left of each panel.



tion, with a column density of ∼1.0×10 [15] cm [−][2] at _T_ ex = 150 and
300 K.


At the half-beam offset position (see Fig. 3), which is closer
to the continuum peak of IRAS 16293B, HOCH 2 CN can be identified. At this position, at least four a-type transitions are clearly
detected, while the three other lines suffer from line blending or
absorption features, see Fig. 7. These lines can approximately
be fitted with synthetic spectra of _N_ T = 3.0×10 [15] cm [−][2] for _T_ ex =
150 and 300 K. In appendix C the remaining HOCH 2 CN transitions at the half-beam offset position are shown, with the same
selection criteria for the full-beam offset position.


In Fig. 3 the moment 0 map of the HOCH 2 CN 36 4,32 –
35 4,31 transition towards IRAS 16293B is shown. This map
shows that HOCH 2 CN emission towards IRAS 16293B is compact. This explains the non-detection of glycolonitrile towards
the full-beam offset position, as this position misses most of
the HOCH 2 CN emission. At the same time, this map demonstrates why Zeng et al. (2019) could detect HOCH 2 CN towards
IRAS 16293B, since these authors use a larger observational
beam of 1 [′′] . 6 beam (with an assumed source size of 0 [′′] . 5), which
covers the entire emitting area.



Because the chemical inventory at the full-beam offset position of the PILS data is best characterised, the tentative detection of HOCH 2 CN towards this position, with a column density
of ∼1.0×10 [15] cm [−][2] ), is used for further analysis in this paper.
However, the identification of HOCH 2 CN towards the half-beam
offset position in combination with the moment 0 map support
the detection of HOCH 2 CN towards IRAS 16923B by Zeng et al.
(2019).
The related species CH 2 CNH, CH(O)CN, and NH 2 CH 2 CN
are also searched for in the PILS dataset, but clear and unblended
lines are not identified. For these species upper limit column densities are determined at the full-beam offset position at excitation
temperatures of 100 and 300 K. The upper limit column densities
and abundances of all species are presented in Table 3.


**4.** **Discussion**


In this work, several molecules are detected towards SMM1-a
and analysed. Most notable are the detection of the C 2 H 3 NO isomers CH 3 NCO (methyl isocyanate) and HOCH 2 CN (glycolonitrile). For HOCH 2 CN, this is only its second interstellar detec

Article number, page 7 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers


HOCH 2 CN - IRAS 16293 2422B - full-beam offset position















0







0


|2 0.8|2|2|2|Col5|
|---|---|---|---|---|
|0|0|0|0||
|0|5910 335920<br>335980 <br><br>390, 39, 0<br>2<br>4<br>374 K<br>410, 41, 1|335990 336000<br>344620 <br><br>400, 40, 1<br>2<br>368 K<br>410, 41, 0|335990 336000<br>344620 <br><br>400, 40, 1<br>2<br>368 K<br>410, 41, 0|335990 336000<br>344620 <br><br>400, 40, 1<br>2<br>368 K<br>410, 41, 0|
|0.2||0|||



353410 353420 353430 362040 362050 362060 362130 362140 362150

Frequency (MHz)



353410 353420 353430



362040 362050 362060



362130 362140 362150



Fig.position of IRAS 16293B, illustrating the non-detection of these lines in this spectrum. The observed spectrum is plotted in black and(6) Overview of a-type ( _J_ 0 [′], _J_ [′] [–] _[J]_ 0 [′′], _J_ [′′] [)] [HOCH] [2] [CN] [transitions] [covered] [by] [the] [PILS] [spectrum] [towards] [the] [full-beam] [o][ff][set]
synthetic spectra for a column density of 1.0×10 [15] cm [−][2] and excitation temperatures of 150 (blue) and 300 K (red) are overplotted.
The synthetic spectrum of the entire molecular inventory determined with PILS data towards this position is plotted in green. The
quantum numbers of the transition are indicated at the top of each panel and the upper state energy is given in the top left of each
panel.




















































|38<br>0381<br>160,,<br>.<br>323K<br>4<br>02.8<br>0<br>0 .26 (K)<br>335900 33<br>40 B<br>0400 6,, T<br>04<br>. 351K<br>4<br>022<br>.<br>0<br>020<br>.03053410 353<br>.|HOCH 2CN IRAS 16293 2422B half -be<br>- -<br>37 38 37 39<br>0371 0380 0370 0391<br>,, 6,,,, 6,,<br>318K 339K<br>4 4<br>2 2<br>0 0<br>2 2<br>5910 335920 335980 335990 336000 344620<br>39 41 40 41<br>0390 0411 0401 0410<br>,, 6,,,, 6,,<br>374K 368K<br>4 4<br>2 2<br>0 0<br>2 2<br>420 35343002 362040 362050 36024060 36210360 3<br>. F. (MHz).<br>requency|6293 2422B half -be<br>-<br>37 39<br>0370 0391<br>,, 6,,<br>339K<br>4<br>2<br>0<br>2<br>335990 336000 344620<br>40 41<br>0401 0410<br>,, 6,,<br>368K<br>4<br>2|am offset position<br>38 40 39<br>0381 0401 0391<br>,, 6,,,,<br>356K<br>4<br>2|
|---|---|---|---|
|335900 33<br>2<br>0<br>2<br>4<br>6<br>323 K<br>380, 38, 1<br>353410 353<br>2<br>0<br>2<br>4<br>6<br>351 K<br>400, 40, 0<br>0.0<br>~~0~~.0<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>TB (K)|5910 335920<br>370, 37, 1<br>335980 335990 336000<br>2<br>0<br>2<br>4<br>6<br>318 K<br>380, 38, 0<br>370, 37, 0<br>344620 <br>2<br>0<br>2<br>4<br>6<br>339 K<br>390, 39, 1<br>420 353430<br>390, 39, 0<br>362040 362050 362060<br>2<br>0<br>2<br>4<br>6<br>374 K<br>410, 41, 1<br>400, 40, 1<br>362130 3<br>2<br>0<br>2<br>4<br>6<br>368 K<br>410, 41, 0<br>0.2<br>0.4<br>0.6<br>Frequency (MHz)<br>HOCH2CN - IRAS 16293<br>2422B - half-be|335990 336000<br>370, 37, 0<br>344620 <br>2<br>0<br>2<br>4<br>6<br>339 K<br>390, 39, 1<br>400, 40, 1<br><br>2<br>4<br>6<br>368 K<br>410, 41, 0<br>   6293<br>2422B - half-be|344630 344640<br>353330 353340 353350<br>2<br>0<br>400, 40, 0|
|335900 33<br>2<br>0<br>2<br>4<br>6<br>323 K<br>380, 38, 1<br>353410 353<br>2<br>0<br>2<br>4<br>6<br>351 K<br>400, 40, 0<br>0.0<br>~~0~~.0<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>TB (K)|5910 335920<br>370, 37, 1<br>335980 335990 336000<br>2<br>0<br>2<br>4<br>6<br>318 K<br>380, 38, 0<br>370, 37, 0<br>344620 <br>2<br>0<br>2<br>4<br>6<br>339 K<br>390, 39, 1<br>420 353430<br>390, 39, 0<br>362040 362050 362060<br>2<br>0<br>2<br>4<br>6<br>374 K<br>410, 41, 1<br>400, 40, 1<br>362130 3<br>2<br>0<br>2<br>4<br>6<br>368 K<br>410, 41, 0<br>0.2<br>0.4<br>0.6<br>Frequency (MHz)<br>HOCH2CN - IRAS 16293<br>2422B - half-be|335990 336000<br>370, 37, 0<br>344620 <br>2<br>0<br>2<br>4<br>6<br>339 K<br>390, 39, 1<br>400, 40, 1<br><br>2<br>4<br>6<br>368 K<br>410, 41, 0<br>   6293<br>2422B - half-be|62140 362150<br>0.8<br>1.0|



Fig.position(7) ofOverviewIRAS 16293B,of a-typeillustrating( _J_ 0 [′], _J_ [′] [–] _[J]_ the 0 [′′], _J_ [′′] detection [)] [HOCH] [2] [CN] of a [transitions] number of [covered] these lines. [by] [the] The [PILS] observed [spectrum] spectrum [towards] is plotted [the] [half-beam] in black [o][ff] and [set]
synthetic spectra for a column density of 3.0×10 [15] cm [−][2] and excitation temperatures of 150 (blue) and 300 K (red) are overplotted.
The quantum numbers of the transition are indicated at the top of each panel and the upper state energy is given in the top left of
each panel.



tion. CH 3 NCO has been detected in multiple interstellar sources,
but this is the first detection towards SMM1 and therefore also
the first detection towards an intermediate-mass source. These
new detections serve as additional evidence for a large and diverse reservoir of prebiotic molecules in star- and planet-forming
regions, which can contribute to the emergence of biomolecules
on planetary bodies. Of the C 2 H 3 NO isomers, CH 3 NCO is en

Article number, page 8 of 32



ergetically the most favorable, followed by HOCH 2 CN, which
has a higher relative energy of 12.1 – 18.6 kcal mol [−][1] (0.5 – 0.8
eV molecule [−][1] or 5800 – 9300 K molecule [−][1] ), depending on the
level of theory used (Fourré et al. 2020). In a thermodynamic
equilibrium, lower energy or more stable products are favored
and in such a scenario, CH 3 NCO is expected to be more abundant than HOCH 2 CN by a factor of at least 1×10 [9] (assuming a

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1



temperature of 300 K). The fact that CH 3 NCO and HOCH 2 CN
are found to be equally abundant is, therefore, evidence that the
formation of these molecules is rather driven by kinetics.
To better understand the interstellar chemistry of HOCH 2 CN
and CH 3 NCO, their abundances and those of several other
species are compared for SMM1-a, IRAS 16293B, and several
other sources for which at least some of these species are detected. For this comparison, it is important to emphasise observational differences. For example, SMM1 (D ≈436 pc) is located further away than IRAS 16293 (D ≈141 pc, Dzib et al.
2018) and the beam size used in this work (1 [′′] . 2) is larger than
that of the PILS survey (0 [′′] . 5). Therefore, the chemical inventory of SMM1-a and the involved chemical processes are investigated on a much larger spatial scale of roughly 500 au, compared to about 70 au for IRAS 16293B. The SMM1-a observations can cover a larger range of physical environments (e.g.
also the envelope or outflow), and potentially a larger temperature gradient. At the same time, the higher luminosity of SMM1
results in a larger area where hot core conditions are present, thus
compensating for the lower spatial resolution. Furthermore, the
SMM1-a spectrum is extracted towards the continuum peak, but
for IRAS 16293B a full-beam offset position from the continuum peak is used. Therefore, when comparing molecular ratios
between the two sources, they may not only be affected by different physical conditions but also due to the way the sources were
observed. Observational parameters of SMM1-a, IRAS 16293B,
and other sources used for comparisons are listed in Table D.1.
HOCH 2 CN is thus far only detected in two sources, SMM1a and IRAS 16293B (Zeng et al. 2019), and therefore a chemical comparison is limited to these two objects. To use molecular ratios that are unbiased by observational parameters, only
data of the chemical inventory of IRAS 16293B obtained with
PILS survey data at the full-beam offset position is used for the
source comparison. This means that the tentative column density of HOCH 2 CN in IRAS 16293B is used. Figure 8 shows the
abundances of molecules detected in this work to CH 3 OH and
HNCO in SMM1-a and IRAS 16293B. For IRAS 16293B, the
analysis performed in this work is combined with results from
Jørgensen et al. (2016); Coutens et al. (2016); Ligterink et al.
(2017); Coutens et al. (2018); Persson et al. (2018); Calcutt et al.
(2018); Jørgensen et al. (2018). For both the [X]/[CH 3 OH] and

[X]/[HNCO] ratios, all the oxygen-bearing molecules, CH 3 CN,
and NH 2 CN are found to be more abundant in IRAS 16293B
than in SMM1-a. For [X]/[CH 3 OH] its ratios are generally a factor of a few lower in SMM1-a, while for the [X]/[HNCO] ratios
the difference is usually more than a factor of ten.


_4.1._ _SMM1-a: A HOCH_ 2 _CN-rich source_


While general trends are found in the [X]/[CH 3 OH] and

[X]/[HNCO] ratios displayed in Fig. 8, three molecules deviate from the general trend. The abundance of CH 3 NCO
is found to be approximately equal in both sources, while
HOCH 2 CN and HNCO are more abundant in SMM1-a compared to IRAS 16293B. In particular, for HOCH 2 CN a large difference is seen in its ratios to CH 3 OH, which can be more than
an order of magnitude different between the two sources.
To gain further insight in how the chemical compositions
of SMM1-a and IRAS 16293B differ, the statistical distance of
molecular ratios are plotted in Fig. 9. The statistical distance indicates how significant the difference in a molecular ratio between SMM1-a and IRAS 16293B is (see Manigand et al. 2020,
and Appendix E). Greater values indicate a greater difference
in the molecular ratios between the two sources. A positive



value indicates that the ratio of SMM1-a is greater than that of
IRAS 16293B and vice versa. Fig. 9 highlights that HOCH 2 CN
and HNCO are more abundant in SMM1-a (σ ranging from 3 –
6) and CH 3 NCO is moderately more abundant in SMM1-a (σ ≥
2).
The statistical distance results have several implications.
Since the abundances of both HOCH 2 CN and HNCO are enhanced in SMM1-a, this may indicate a relationship between
these two species. For CH 3 NCO a much less significant enhancement is seen, which can imply that both C 2 H 3 NO isomers
form via different chemical reactions or under different physical
conditions. However, it is important to stress that an abundance
correlation does not always imply a formational link between
species (Belloche et al. 2020).
The statistical distances of ratios involving CH 3 CN, NH 2 CN,
a-(CH 2 OH), and CH 3 CH 2 OH show that there is almost no variation in these molecules between SMM1-a and IRAS 16293B.
This is interesting because some of these molecules can form in
reactions involving radicals from which HOCH 2 CN also can be
formed, such as CN, CH 2 OH, and CH 2 CN. This hints that either
HOCH 2 CN is not formed from these radicals, is not linked to
the reaction networks that form the four aforementioned species,
or HOCH 2 CN forms from the same radicals, but under different
physical conditions.
Finally, it is interesting to note that ratios of D 2 CO and
CH 3 OCHO to NH 2 CN, CH 3 CH 2 OH, and a-(CH 2 OH) 2 seem to
be a bit more abundant in SMM1-a than in IRAS 16293B. This
is particularly significant for the case of D 2 CO since H 2 CO is
involved in the Strecker-like formation of HOCH 2 CN, see reaction 2. A higher abundance of H 2 CO may indicate that the
Strecker-like reaction can more efficiently take place. However,
care needs to be taken with this interpretation, since the D 2 CO
spectral lines in the SMM1-a spectrum are blended and thus
there is a large uncertainty on its column density. At the same
time, the D/H ratio of H 2 CO is not known in SMM1-a, which
introduces another source of uncertainty. To investigate if there
is a correlation between HOCH 2 CN and H 2 CO, both species
should be identified towards more sources and H 2 CO should be
observed through its minor [13] C and [18] O isotopes instead of the
deuterated species. For now, however, the Strecker-like synthesis of HOCH 2 CN in the ISM can neither be confirmed nor ruled

out.


_4.2._ _Interstellar formation of CH_ 3 _NCO_


Since its first detection in the ISM, the formation of CH 3 NCO
has been hypothesised to be linked to that of HNCO, see
Eq. 1. To investigate the interstellar chemical relationship between these two species, their gas-phase ratios towards interstellar sources are plotted in Fig. 10. The result of the SMM1a analysis is complemented by data from the low-mass protostar IRAS 16239B (Ligterink et al. 2017), the quiescent giant
molecular cloud G+0.693 (Zeng et al. 2018), the high-mass starforming region Orion KL (Cernicharo et al. 2016), the high-mass
hot molecular core G10.47+0.03 (Gorai et al. 2020), and the
galactic center source Sagittarius B2(N) (Sgr B2(N), Belloche
et al. 2013; Cernicharo et al. 2016; Belloche et al. 2017). The
majority of these sources is categorised as hot cores or corinos.
In these sources, thermal desorption of molecules from ice mantles plays an important role to chemically enrich the gas surrounding the protostar, in particular around the desorption temperature of water ice (∼100 K). The exception is the source
G+0.693, which is a molecular cloud. Molecules observed in
the gas of this cloud are assumed to be the result of gas-phase


Article number, page 9 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers


[ X ] / [ C 3 [O] [H] [] (] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )                            - 2



3 [O] [H] [ X ] / [ H N C O ] (


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O ) - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E      - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O]   - 2


a  - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )                                        - 2



3 [O] [H] N C O


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )                                    - 2



3 [O] [H] N C O


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )                   - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )             - 2



3 [O] [H] N C O


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )         - 2



3 [O] [H] N C O


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O ) - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 . 0 0 . 1 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )                                     - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 . 1 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )         - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a  - ( C 2 [O] [H] [)] a  - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E      - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


Fig. (8) Ratios of [X]/[CH 3 OH] towards SMM1-a (red) and IRAS 16293B (blue) in decreasing order of SMM1-a abundance.
The “∼” symbol indicates that these HOCH 2 CN ratios have been determined with the column density of the tentative HOCH 2 CN
detection towards the IRAS 16293B full-beam offset position. For IRAS 16293B, column densities derived towards the full-beam
offset position from the following PILS publications are used: _[a]_ This work, _[b]_ Ligterink et al. (2017), _[c]_ Coutens et al. (2016), _[d]_ Jørgensen
et al. (2016, 2018), _[e]_ Calcutt et al. (2018), _[f]_ Persson et al. (2018), _[g]_ Coutens et al. (2018).


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O]    - 2


a   - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )                                         - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )          - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E    - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )                                        - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6 . 0


H O C H N 2 C [C] 54 . 2. 4 1 E 1 S g r 2 ( N )


3 . 6


C 3 [N] [C] 2 . 8 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 . 0 1 E 1 S g r 2 ( N 2


1 . 2


C 3 [C] 0 . 4


N 2 [C] -- 01 . 4. 2 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2 . 0


a - ( C 2 [O] [H] [)] -- 23 . 8. 6 1 E 1 O r n L


2 [C] - 4 . 4 S 1 

C 3 [O] [C] [H] -- 56 . 2. 0


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )                  - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6


3


1


C 3 [C] 0


C 3 [C] 2 [O] - 2


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )       - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )   - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O ) - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O ) - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )       - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )    - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )                   - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )                                    - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a  - ( C 2 [O] [H] [)] a  - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E      - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O]    - 2


a   - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o i n a t o


Fig. (9) Statistical distance between molecular ratios in SMM1 N ( H N C O ) - 2
and IRAS 16293B, given in σ. Larger σ values indicate a larger
difference between the two sources for a given ratio. Positive
values indicate that a ratio is higher in SMM1-a, while negative
values indicate that a ratio is lower in SMM1-a. In particular, all
ratios of HOCH 2 CN are found to be higher in SMM1-a than in
IRAS 16239B.


formation reactions or non-thermal desorption from ice mantles
of dust grains.

The ratios of CH 3 NCO and HNCO are generally similar at

[CH 3 NCO] / [HNCO] = ∼10% and vary only by a factor of a
few, in particular when the lowest and highest ratio are omitted.
The lowest ratio, found towards G+0.693, arises in a source with
a very different physical structure and can therefore not directly
be compared with the hot core and corino sources. The highest
ratio is found towards G10.47+0.03, but the analysis of HNCO
in this source is likely performed on optically thick HNCO lines
and the analysis seems to underestimate the HNCO column density in this source (see Fig. 4 in Gorai et al. 2020). Removing
these results from the analysis, a correlation between CH 3 NCO


Article number, page 10 of 32



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O ) [ c - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O ) - 2



3 [O] [H] N C O


H O C 2 [C] H O C 2 [C]


H N C C 3 [O]


C 3 [O] [C] [H] C 3 [O] [C] [H]


C 3 [C] 2 [O] C 3 [C] 2 [O]


a - ( C 2 [O] [H] [)] a - ( C 2 [O] [H] [)]


C 3 [C] C 3 [C]


2 [C] 2 [C]


N 2 [C] N 2 [C]


1 E - 0 0 1 0 1 1 0 1 0 0 1 0 0 0


( (


6

H O C H N 2 C [C] 54 1 E 1 S g r 2 ( N )


3

C 3 [N] [C] 2 G 1 0 7 + 0 S g r 2 ( N )


C 3 [O] 2 1 E 1 S g r 2 ( N 2


1


C 3 [C] 0


N 2 [C] -- 01 1 E 1 A S 6 2 9 3 O r n L


C 3 [C] 2 [O] - 2


a - ( C 2 [O] [H] [)] -- 23 1 E 1 O r n L


C 3 [O] [C] [H] -- 56


1 E 1 1 E 1 1 E 1

D e n o a


N ( H N C O )             - 2


Fig. (10) Ratios of [CH 3 NCO]/[HNCO] ratios towards
SMM1-a and various other sources. Column densities from the
following publications are used: Belloche et al. (2013), Cernicharo et al. (2016), Ligterink et al. (2017), Belloche et al.
(2017), Zeng et al. (2018), Gorai et al. (2020), and this work.


and HNCO is found, which may indicate a chemical link between CH 3 NCO and HNCO. Furthermore, this correlation spans
a variety of sources of different masses and over four order of
magnitude in luminosities. This results in different physical conditions, such as gas and dust temperature and radiation fields
for each source. Therefore, the lack of source-to-source variation in [CH 3 NCO]/[HNCO] ratio hints that the abundances of
these species are set at an early stage of star formation. Formation of CH 3 NCO via reaction 1 in the ice mantles of dust grains
during the dark cloud stage or while the ice mantles are warmed
up in the hot core/corino stage are a plausible scenario.

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1



_4.3._ _On the formation of -CN and -NCO molecules_


Figure 9 shows that HOCH 2 CN and HNCO abundances are enhanced in SMM1-a compared to IRAS 16293B. At the same
time, CH 3 NCO is only marginally enhanced and CH 3 CN and
NH 2 CN abundances show little difference between the two
sources. Why the abundances of HOCH 2 CN and HNCO are enhanced in SMM1-a and those of CH 3 NCO, CH 3 CN, and NH 2 CN
are not is not straightforward to explain. However, it is likely that
the various -CN and -NCO molecules form in different chemical
reactions and physical conditions.
As this work shows, CH 3 NCO probably forms at an early
stage of star-formation, as do CH 3 CN and NH 2 CN. All three
species are suggested to form in radical-radical addition reactions in ice mantles. These reactions take place during the
dark cloud stage in cold (∼10 K) ice mantles and significantly
speed up when the ice mantle temperature increases to ∼30 K
and radicals become mobile (Garrod et al. 2008; Coutens et al.
2018). Some reactions can compete for the same radical, such as
CH 3 CN and NH 2 CN, which both compete for the -CN radical.
The fact that HOCH 2 CN and HNCO are enhanced in abundance in SMM1-a, can indicate a link between these species.
Both molecules can be formed from HCN in ice mantles of interstellar dust grains. HOCH 2 CN can be formed in the Strecker-like
reaction when HCN is converted to CN [−] . HNCO and the related
anion OCN [−] are formed when HCN:H 2 O mixtures are processed
with energetic UV photons or protons (Gerakines et al. 2004).
These reactions are aided by high grain temperatures (≫30 K,
but below the water sublimation temperature) for a prolonged
time and high fluxes of photons and energetic particles. If these
conditions are met in SMM1, they can explain the higher abundances of HOCH 2 CN and HNCO compared to IRAS 16239B
and present a formational link between some -CN and -NCO
molecules. However, only circumstantial evidence can be presented for such conditions in SMM1, which is based on the
fact that SMM1 hosts multiple protostellar sources and outflows,
which can warm and irradiate the cloud (e.g. Choi 2009; Dionatos et al. 2014; Hull et al. 2017; Tychoniec et al. 2019).
To gain further insight into the reactions that form -CN and NCO molecules, unbiased observations of these species towards
a multitude of sources spanning different physical conditions are
needed. Not only the isomers HOCH 2 CN and CH 3 NCO should
be targeted for these observations, but also species like CH 3 CN,
HNCO, NH 2 CN, C 2 H 3 CN, and C 2 H 5 CN. Laboratory, theoretical and modeling efforts should be focused on understanding
the formation of these species. In particular, the formation of
HOCH 2 CN via pathways other than the thermal Strecker-like
synthesis needs to be studied and a better understanding of the
formation of CH 3 CN is required.


**5.** **Conclusions**


This publication presents the simultaneous detection of the
C 2 H 3 NO isomers methyl isocyanate (CH 3 NCO) and glycolonitrile (HOCH 2 CN). Both species are identified towards the
intermediate-mass Class 0 protostar Serpens SMM1-a. This
is only the second interstellar detection of glycolonitrile,
while for methyl isocyanate it is the first detection towards
an intermediate-mass protostar. Additionally, CH 3 OH, HNCO,
CH 3 OCHO, CH 3 CH 2 OH, a-(CH 2 OH) 2, D 2 CO, and NH 2 CN are
detected. CH 2 CNH, CH(O)CN, and NH 2 CH 2 CN, molecules that
are related to HOCH 2 CN, are searched for but not identified.
Data from the PILS survey towards IRAS 16293B are analysed
in search for HOCH 2 CN and this molecule is identified in a spec


trum extracted at a half-beam offset position from the continuum
peak of IRAS 16239B. The molecules CH 2 CNH, CH(O)CN, and
NH 2 CH 2 CN are not identified towards this source.
The detection of CH 3 NCO and HOCH 2 CN towards SMM1a is additional evidence of a large interstellar reservoir of prebiotic molecules. Delivery of these molecules to planetary surfaces may contribute to the formation of biomolecules on these
objects. The column densities and abundances of CH 3 NCO ( _N_ T
= 6.4×10 [14] cm [−][2] and [CH 3 NCO]/[CH 3 OH] = 5.3×10 [−][4] ) and
HOCH 2 CN ( _N_ T = 7.4×10 [14] cm [−][2] and [HOCH 2 CN]/[CH 3 OH]
= 6.2×10 [−][4] ) are found to be equal within their error bars. Since
HOCH 2 CN is the least energetically favorable of the two isomers, thermodynamics predicts that CH 3 NCO should be more
abundant. The equal ratio between both molecules is therefore
evidence that the formation of these molecules is driven by kinetics.

The comparison of molecular ratios between SMM1-a and
IRAS 16293B show that HOCH 2 CN and HNCO are significantly more abundant in the former source. The molecular ratios
of HOCH 2 CN hint that the formation of this molecule does not
heavily depend on solid-state radical-radical addition reactions,
such as HOCH 2 + CN and HO + CH 2 CN. Formation via the
thermal Strecker-like reaction [X [+] CN [−] ] + H 2 CO in ice mantles
cannot be confirmed nor ruled out based on the current data but
may be a prominent formation pathway.
To investigate the possibility that CH 3 NCO formation is related to HNCO, the ratios of these molecules in SMM1-a and
other sources are analysed. These ratios are found to be uniform throughout all sources at [CH 3 NCO]/[HNCO] = ∼10 %.
This indicates that there is a chemical link between both species,
but also that its ratios is already set at an early stage of starformation. Presumably CH 3 NCO forms via the radical-radical
reaction CH 3 + NCO in ice mantles during the dark cloud stage.
It is difficult to establish a chemical link between -CN and
-NCO molecules. Some may be related, such as HOCH 2 CN and
HNCO, which can both form from HCN at elevated (≫30 K)
grain temperatures and in relatively high radiation fields. Continued observational, laboratory, and theoretical studies of -CN and
-NCO molecules are required to gain further insight into their
formation and links in their chemistry.


_Acknowledgements._ We thank E.G. Bøgelund, S.F. Wampfler, M.N. Drozdovskaya, B. Kulterer, and B.A. McGuire for helpful discussions on the observations, spectroscopy, and the chemistry of the C 2 H 3 NO isomers. The authors acknowledge assistance from Allegro, the European ALMA Regional
Center node in the Netherlands. We thank the anonymous referee for their
thorough review of this manuscript and helpful comments. This paper makes
use of the following ALMA data: ADS/JAO.ALMA#2018.1.00836.S and
ADS/JAO.ALMA#2013.1.00278.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by
ESO, AUI/NRAO and NAOJ. NFWL is supported by the Swiss National Science
Foundation (SNSF) Ambizione grant 193453. JKJ is supported by the European
Research Council (ERC) under the European Union’s Horizon 2020 research and
innovation programme through ERC Consolidator Grant “S4F” (grant agreement
No 646908). AC acknowledges financial support from the Agence Nationale de
la Recherche (grant ANR-19-ERC7-0001-01).


**References**


Allamandola, L., Sandford, S., & Valero, G. 1988, Icarus, 76, 225

Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2019, A&A, 628, A10
Belloche, A., Maury, A., Maret, S., et al. 2020, Astronomy & Astrophysics
Belloche, A., Menten, K., Comito, C., et al. 2008, Astronomy & Astrophysics,
482, 179
Belloche, A., Meshcheryakov, A. A., Garrod, R. T., et al. 2017, A&A, 601, A49


Article number, page 11 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers



Belloche, A., Müller, H. S., Menten, K. M., Schilke, P., & Comito, C. 2013,
Astronomy & Astrophysics, 559, A47
Bocquet, R., Demaison, J., Cosléou, J., et al. 1999, Journal of molecular spectroscopy, 195, 345
Bøgelund, E. G., McGuire, B. A., Hogerheijde, M. R., van Dishoeck, E. F., &
Ligterink, N. F. W. 2019, A&A, 624, A82
Boogert, A. A., Gerakines, P. A., & Whittet, D. C. 2015, Annual Review of
Astronomy and Astrophysics, 53
Bossa, J., Theule, P., Duvernay, F., & Chiavassa, T. 2009, The Astrophysical
Journal, 707, 1524
Bulak, M., Paardekooper, D., Fedoseev, G., & Linnartz, H. 2020, Astronomy &
Astrophysics, 636, A32
Calcutt, H., Jørgensen, J. K., Müller, H., et al. 2018, Astronomy & Astrophysics,
616, A90
Casali, M., Eiroa, C., & Duncan, W. 1993, Astronomy and Astrophysics, 275,
195
Cernicharo, J., Kisiel, Z., Tercero, B., et al. 2016, Astronomy & Astrophysics,
587, L4
Choi, M. 2009, The Astrophysical Journal, 705, 1730
Christen, D., Coudert, L., Suenram, R. D., & Lovas, F. J. 1995, Journal of Molecular Spectroscopy, 172, 57
Christen, D. & Müller, H. S. 2003, Physical Chemistry Chemical Physics, 5,
3600
Coutens, A., Jørgensen, J. K., Van der Wiel, M. H. D., et al. 2016, Astronomy &
Astrophysics, 590, L6
Coutens, A., Ligterink, N. F. W., Loison, J.-C., et al. 2019, Astronomy & Astrophysics, 623, L13
Coutens, A., Willis, E., Garrod, R., et al. 2018, Astronomy & Astrophysics, 612,
A107
Danger, G., Borget, F., Chomat, M., et al. 2011, Astronomy & Astrophysics, 535,
A47
Danger, G., Duvernay, F., Theulé, P., Borget, F., & Chiavassa, T. 2012, The Astrophysical Journal, 756, 11
Danger, G., Rimola, A., Mrad, N. A., et al. 2014, Physical Chemistry Chemical
Physics, 16, 3360
Dionatos, O., Jørgensen, J. K., Green, J. D., et al. 2013, Astronomy & Astrophysics, 558, A88
Dionatos, O., Jørgensen, J. K., Teixeira, P., Güdel, M., & Bergin, E. 2014, Astronomy & Astrophysics, 563, A28
Dzib, S., Ortiz-León, G., Hernández-Gómez, A., et al. 2018, Astronomy & Astrophysics, 614, A20
Fisher, J., Paciga, G., Xu, L.-H., et al. 2007, Journal of Molecular Spectroscopy,
245, 7
Fourré, I., Matz, O., Ellinger, Y., & Guillemin, J. 2020, Astronomy & Astrophysics, 639, A16
Garrod, R. T., Weaver, S. L. W., & Herbst, E. 2008, The Astrophysical Journal,
682, 283
Gerakines, P., Moore, M., & Hudson, R. 2004, Icarus, 170, 202
Goicoechea, J. R., Cernicharo, J., Karska, A., et al. 2012, Astronomy & Astrophysics, 548, A77
Gorai, P., Bhat, B., Sil, M., et al. 2020, The Astrophysical Journal, 895, 86
Halfen, D., Ilyushin, V. V., & Ziurys, L. M. 2015, The Astrophysical Journal
Letters, 812, L5
Halfen, D. T., Ilyushin, V., & Ziurys, L. M. 2011, ApJ, 743, 60
Hocking, W., Gerry, M., & Winnewisser, G. 1975, Canadian Journal of Physics,
53, 1869
Högbom, J. A. 1974, A&AS, 15, 417
Hogerheijde, M. R., Van Dishoeck, E. F., Salverda, J. M., & Blake, G. A. 1999,
The Astrophysical Journal, 513, 350
Hollis, J. M., Lovas, F. J., & Jewell, P. R. 2000, The Astrophysical Journal Letters, 540, L107
Hollis, J. M., Lovas, F. J., Remijan, A. J., et al. 2006, ApJ, 643, L25
Holtom, P. D., Bennett, C. J., Osamura, Y., Mason, N. J., & Kaiser, R. I. 2005,
ApJ, 626, 940
Hudson, R. & Moore, M. 2004, Icarus, 172, 466
Hull, C. L., Girart, J. M., Kristensen, L. E., et al. 2016, The Astrophysical Journal
Letters, 823, L27
Hull, C. L., Girart, J. M., Tychoniec, Ł., et al. 2017, The Astrophysical Journal,
847, 92
Ilyushin, V., Kryvda, A., & Alekseev, E. 2009, Journal of Molecular Spectroscopy, 255, 32
Jacobsen, S., Jørgensen, J., Van der Wiel, M., et al. 2018, Astronomy & Astrophysics, 612, A72
Jørgensen, J., Müller, H., Calcutt, H., et al. 2018, Astronomy & Astrophysics,
620, A170
Jørgensen, J. K., Favre, C., Bisschop, S. E., et al. 2012, The Astrophysical Journal Letters, 757, L4
Jørgensen, J. K., Van der Wiel, M. H. D., Coutens, A., et al. 2016, Astronomy &
Astrophysics, 595, A117


Article number, page 12 of 32



Kaifu, N., Morimoto, M., Nagane, K., et al. 1974, ApJ, 191, L135
Koivusaari, M., Horneman, V., & Anttila, R. 1992, Journal of Molecular Spectroscopy, 152, 377
Kristensen, L., Van Dishoeck, E., Van Kempen, T., et al. 2010, Astronomy &
Astrophysics, 516, A57
Kukolich, S. G., Nelson, A., & Yamanashi, B. 1971, Journal of the American
Chemical Society, 93, 6769
Lapinov, A., Golubiatnikov, G. Y., Markov, V., & Guarnieri, A. 2007, Astronomy
Letters, 33, 121
Lee, C.-W., Kim, J.-K., Moon, E.-S., Minh, Y. C., & Kang, H. 2009, ApJ, 697,
428
Ligterink, N., Coutens, A., Kofman, V., et al. 2017, Monthly Notices of the Royal
Astronomical Society, 469, 2219
Ligterink, N. F., El-Abd, S. J., Brogan, C. L., et al. 2020, The Astrophysical
Journal, 901, 37
Ligterink, N. F. W., Calcutt, H., Coutens, A., et al. 2018, Astronomy & Astrophysics, 619, A28
Majumdar, L., Loison, J.-C., Ruaud, M., et al. 2018, Monthly Notices of the
Royal Astronomical Society: Letters, 473, L59
Manigand, S., Jørgensen, J., Calcutt, H., et al. 2020, Astronomy & Astrophysics,
635, A48
Margulès, L., McGuire, B., Senent, M. L., et al. 2017, Astronomy & Astrophysics, 601, A50
Martín-Doménech, R., Rivilla, V., Jiménez-Serra, I., et al. 2017, Monthly Notices
of the Royal Astronomical Society, 469, 2230
Maté, B., Molpeceres, G., Tanarro, I., et al. 2018, The Astrophysical Journal,
861, 61
McGuire, B. A., Carroll, P. B., Loomis, R. A., et al. 2016, Science, 352, 1449
Müller, H. S., Belloche, A., Xu, L.-H., et al. 2016, Astronomy & Astrophysics,
587, A92
Müller, H. S., Brown, L. R., Drouin, B. J., et al. 2015, Journal of Molecular
Spectroscopy, 312, 22
Müller, H. S., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of
Molecular Structure, 742, 215
Müller, H. S., Thorwirth, S., Roth, D., & Winnewisser, G. 2001, Astronomy &
Astrophysics, 370, L49
Niedenhoff, M., Yamada, K., Belov, S., & Winnewisser, G. 1995, Journal of
Molecular Spectroscopy, 174, 151
Öberg, K. I., Van der Marel, N., Kristensen, L. E., & Van Dishoeck, E. F. 2011,
The Astrophysical Journal, 740, 14
Ortiz-León, G. N., Dzib, S. A., Kounkel, M. A., et al. 2017, The Astrophysical
Journal, 834, 143
Pearson, J. C., Brauer, C. S., & Drouin, B. J. 2008, Journal of Molecular Spectroscopy, 251, 394
Persson, M. V., Jørgensen, J. K., Müller, H., et al. 2018, Astronomy & Astrophysics, 610, A54
Pickett, H., Poynter, R., Cohen, E., et al. 1998, Journal of Quantitative Spectroscopy and Radiative Transfer, 60, 883
Quénard, D., Jiménez-Serra, I., Viti, S., Holdship, J., & Coutens, A. 2018,
Monthly Notices of the Royal Astronomical Society, 474, 2796
Read, W. G., Cohen, E. A., & Pickett, H. M. 1986, Journal of Molecular Spectroscopy, 115, 316
Rivilla, V., Martín-Pintado, J., Jiménez-Serra, I., et al. 2019, Monthly Notices of
the Royal Astronomical Society: Letters, 483, L114
Rivilla, V. M., Martín-Pintado, J., Jiménez-Serra, I., et al. 2020, The Astrophysical Journal Letters, 899, L28
Rubin, R. H., Swenson, G. W., J., Benson, R. C., Tigelaar, H. L., & Flygare,
W. H. 1971, ApJ, 169, L39
Saladino, R., Crestini, C., Pino, S., Costanzo, G., & Di Mauro, E. 2012, Physics
of Life Reviews, 9, 84
Sánchez-Monge, Á., Schilke, P., Ginsburg, A., Cesaroni, R., & Schmiedeke, A.
2018, Astronomy & Astrophysics, 609, A101
Sandford, S. A., Nuevo, M., Bera, P. P., & Lee, T. J. 2020, Chemical Reviews
Schwartz, A. W. & Goverde, M. 1982, Journal of molecular evolution, 18, 351
Schwartz, A. W., Joosten, H., & Voet, A. 1982, Biosystems, 15, 191
Turner, B. E., Liszt, H. S., Kaifu, N., & Kisliakov, A. G. 1975, ApJ, 201, L149
Tychoniec, Ł., Hull, C. L. H., Kristensen, L. E., et al. 2019, A&A, 632, A101
White, G. J., Casali, M. M., & Eiroa, C. 1995, Astronomy & Astrophysics, 298,
594
Wilson, T. 1999, Reports on Progress in Physics, 62, 143
Woon, D. E. 2001, Icarus, 149, 277
Xu, L.-H., Fisher, J., Lees, R., et al. 2008, Journal of Molecular Spectroscopy,
251, 305
Yan, Y., Zhang, J., Henkel, C., et al. 2019, The Astrophysical Journal, 877, 154
Zakharenko, O., Motiyenko, R. A., Margulès, L., & Huet, T. R. 2015, Journal of
Molecular Spectroscopy, 317, 41
Zaleski, D. P., Seifert, N. A., Steber, A. L., et al. 2013, The Astrophysical Journal
Letters, 765, L10
Zeng, S., Jiménez-Serra, I., Rivilla, V., et al. 2018, Monthly Notices of the Royal
Astronomical Society, 478, 2962
Zeng, S., Quénard, D., Jiménez-Serra, I., et al. 2019, Monthly Notices of the
Royal Astronomical Society: Letters, 484, L43

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1


**Appendix A:** **Spectroscopic data**


In this paper, the CDMS and JPL spectroscopic databases are the
primary sources of molecular line lists. In the following table, an
overview of the analysed molecules, their identifier and catalog,
and the most important publications in literature on which these
entries are based is given.


**Appendix B:** **Supporting information for the**
**SMM1-a analysis**


**Appendix C:** **Analysis of PILS data**


**Appendix D:** **Source parameters**


**Appendix E:** **Statistical distance**


The statistical distance of molecular ratios between SMM1-a and
IRAS 16293B is calculated according to the following equation:



, (E.1)



_S_ X/Y =



_N_ X
� _N_ Y �



Y SMM1−a Y IRAS 16293B

~~�~~ σ [2] SMM1−a [+][ σ] [2] IRAS 16293B



_N_ X
SMM1−a [−] � _N_ Y �



where _N_ x and _N_ y are the column densities of two different
molecules and σ is the uncertainty on the column density ratio
� _NN_ XY �. The value of _S_ X/Y is given in σ and indicates the significance of the difference, with greater values implying that there
is a more significant difference between the two sources. In this
equation, positive values indicate that � _NN_ XY � is more abundant in
SMM1-a than in IRAS 16293B, while negative values indicate
the opposite.



Article number, page 13 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers


Table (A.1)


Molecule ID catalog entry date reference
D 2 CO 32502 CDMS Jan 2016 Bocquet et al. (1999)
Zakharenko et al. (2015)
12 CH 3 OH 32504 CDMS May 2016 Xu et al. (2008)
CH [18] 3 [OH] 34504 CDMS Sep 2020 Fisher et al. (2007)
CH 3 CN, ν 8 =1 41509 CDMS Nov 2016 Müller et al. (2015)
Koivusaari et al. (1992)
NH 2 CN 42003 JPL Jan 1991 Read et al. (1986)
HN [12] CO 43511 CDMS May 2009 Kukolich et al. (1971)

Hocking et al. (1975)
Niedenhoff et al. (1995)

Lapinov et al. (2007)
HN [13] CO 44008 JPL Jul 1987 Hocking et al. (1975)
CH 3 CH 2 OH 46524 CDMS Nov 2016 Pearson et al. (2008)

Müller et al. (2016)
CH 3 NCO, ν=0 57505 CDMS Mar 2016 Cernicharo et al. (2016)
CH 3 NCO, ν=1 57506 CDMS Mar 2016 Cernicharo et al. (2016)
HOCH 2 CN 57512 CDMS Mar 2017 Margulès et al. (2017)
CH 3 OCHO 60003 JPL Apr 2009 Ilyushin et al. (2009)
a-(CH 2 OH) 2 62503 CDMS Sep 2003 Christen et al. (1995)
Christen & Müller (2003)


CH 3 CN 8 [=1 - Serpens SMM1-a]











12 2, 2/ 2 11 2, 2/2































221400 221410 221620 221630 221640

Frequency (MHz)



221390 221400 221410



221620 221630 221640



Fig. (B.1) Identified lines of CH 3 CN ν 8 =1 towards SMM1. The observed spectrum is plotted in black, with the best-fit synthetic
spectrum overplotted in blue ( _N_ T = (1.3±0.3)×10 [15] cm [−][2], _T_ ex = 190±25 K). The transition is indicated at the top of each panel and
the upper state energy is given in the top left of each panel.


Table (D.1) Physical parameters of interstellar sources used for abundance comparison.


Source Telescope Distance Luminosity Beam size physical size Reference
(pc) _L_ ⊙ ( [′′] × [′′] ) au
IRAS 16293–2422B ALMA 141 3 _[a]_ 0.5×0.5 70 Jørgensen et al. (2016)
Serpens SMM1-a ALMA 436 100 _[b]_ 1.3×1.0 500 this work
Orion KL ALMA 414 1×10 [5] 1.8×1.8 750 Cernicharo et al. (2016)
Sgr B2(N2) ALMA 8300 4.7×10 [6] 1.6×1.2 – 2.9×1.5 1.3×10 [4] Belloche et al. (2017)
G10.47+0.03 ALMA 8550 5×10 [5] 2.0×1.4 – 2.4×1.6 1.6×10 [4] Gorai et al. (2020)
Sgr B2(N) IRAM 30m 8300 4.7×10 [6] 3.2×2.8 – 12.2×4.4 3.0×10 [4] Cernicharo et al. (2016)
G+0.693 IRAM 30m & GBT 8300 _[c]_ – 9×9 – 55×55 ≥7.5×10 [4] Zeng et al. (2019)


**Notes.** _[a]_ Luminosity determined from a modeling investigation by Jacobsen et al. (2018). _[b]_ Luminosity for the entire SMM1 source. _[c]_ The distance
to G+0.693 is assumed to be the same as Sgr B2.


Article number, page 14 of 32

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1




























|11<br>1110<br>10100,,<br>. .<br>77K<br>0 .705.8<br>(K)<br>0500.6<br>.<br>04 B<br>025. T<br>.<br>02<br>.|NH 2CN - Serpens SMM1 -a<br>10 11 10 11 10<br>1100 0111 0101 1100 190<br>,, 08,,,, 08,,,,<br>. .<br>135K 78K<br>06 06<br>. .<br>04 04<br>. .<br>02 02<br>. .<br>00 00<br>. .<br>460 21847002 219710 21972004219730 221350 02621360 221370 08 10<br>. F. z). . .<br>requency (MH|
|---|---|
|218450 218<br>0.00<br>0.0<br>0.0|218450 218<br>0.00<br>0.0<br>0.0|



Fig. (B.2) Identified lines of NH 2 CN towards SMM1. The observed spectrum is plotted in black, with the best-fit synthetic spectrum overplotted in blue ( _N_ T = (5.1±1.3)×10 [13] cm [−][2], _T_ ex = 190±40 K). The transition is indicated at the top of each panel and the
upper state energy is given in the top left of each panel.









0.50


0.25


0.00


0.2


0.1


0.0


0.1


















|a-(CH 2OH) 2 - Serpens SMM1 -a<br>21 20 19 22 218131 28 28<br>148/71 4161 4150 8140 1217/160 1118/170<br>,,,,,, 06,,,, 02,,,,<br>. .<br>114K 156K 270K<br>0 .50 0 .4<br>01<br>.<br>025 02<br>. .<br>000 00 00<br>. . .<br>18470 218480 219750 219760 219770 219800 219810 219820 233420 233430 2334<br>28 22 21 22 21 22 216160<br>1118/171 5181 5170 7161 7150 6171<br>,, 06,,,, 06,,,, 06,,,,<br>. . .<br>138K 149K 143K<br>04 04 04<br>. . .<br>02 02 02<br>. . .<br>00 00 00<br>. . .|Col2|Col3|
|---|---|---|
|18470 218480<br>2114, 8/7, 1<br>219750 219760 219770<br>0.00<br>0.25<br>0.50<br>114 K<br>204, 16, 1<br>194, 15, 0<br>219800 219810 219820<br>0.0<br>0.2<br>0.4<br>0.6<br>156 K<br>228, 14, 0<br>218, 13, 1<br>233420 233430 2334<br>0.0<br>0.1<br>0.2<br>270 K<br>2812, 17/16, 0<br>2811, 18/17, 0<br>2811, 18/17, 1<br>0.0<br>0.2<br>0.4<br>0.6<br>138 K<br>225, 18, 1<br>215, 17, 0<br>0.0<br>0.2<br>0.4<br>0.6<br>149 K<br>227, 16, 1<br>217, 15, 0<br>0.0<br>0.2<br>0.4<br>0.6<br>143 K<br>226, 17, 1<br>216, 16, 0<br>a-(CH2OH)2 - Serpens SMM1-a|143 K|143 K|
|18470 218480<br>2114, 8/7, 1<br>219750 219760 219770<br>0.00<br>0.25<br>0.50<br>114 K<br>204, 16, 1<br>194, 15, 0<br>219800 219810 219820<br>0.0<br>0.2<br>0.4<br>0.6<br>156 K<br>228, 14, 0<br>218, 13, 1<br>233420 233430 2334<br>0.0<br>0.1<br>0.2<br>270 K<br>2812, 17/16, 0<br>2811, 18/17, 0<br>2811, 18/17, 1<br>0.0<br>0.2<br>0.4<br>0.6<br>138 K<br>225, 18, 1<br>215, 17, 0<br>0.0<br>0.2<br>0.4<br>0.6<br>149 K<br>227, 16, 1<br>217, 15, 0<br>0.0<br>0.2<br>0.4<br>0.6<br>143 K<br>226, 17, 1<br>216, 16, 0<br>a-(CH2OH)2 - Serpens SMM1-a|143 K||



233440 233450 233460



233530 233540 233550



233550 233560 233570



234250 234260 234270



0.3


0.2


0.1


0.0







0.50


0.25


0.00

|450 233460 233530 23 5112, 40, 1 233, 21, 1|33540 233550 233550 23356 223, 20, 0 226, 16, 1|
|---|---|
|0.25<br>0.50<br>139 K|0.25<br>0.50<br>143 K|
|0.00|0.00|



235160 235170 235180


|145, 9, 1 1|134, 10, 1|
|---|---|
|64 K||
|||



235160 235170 235180


23 2, 21, 1 22 2, 20, 0

0.75


0.50


0.25


0.00



235320 235330 235340


26 1/0, 26, 0 25 1/0, 25, 1

1.5


1.0


0.5


0.0



235290 235300 235310


24 4, 21, 0 23 4, 20, 1

0.75


0.50


0.25


0.00



0.3


0.2


0.1


0.0



21 4, 18, 0 20 3, 17, 0





235320 235330 235340 235590 235600 235610 235610 235620 235630 235820 235830 235840

Frequency (MHz)



235320 235330 235340



235590 235600 235610



235610 235620 235630



235820 235830 235840



Fig. (B.3) Identified lines of a-(CH 2 OH) 2 towards SMM1. The observed spectrum is plotted in black, with the best-fit synthetic
spectrum overplotted in blue ( _N_ T = (1.7±0.5)×10 [15] cm [−][2], _T_ ex = 195±70 K). The transition is indicated at the top of each panel and
the upper state energy is given in the top left of each panel.


Article number, page 15 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers

























































































































Fig. (B.4) Identified lines of CH 3 CH 2 OH towards SMM1. The observed spectrum is plotted in black, with the best-fit synthetic
spectrum overplotted in blue ( _N_ T = (4.1±0.9)×10 [15] cm [−][2], _T_ ex = 210±25 K). The transition is indicated at the top of each panel and
the upper state energy is given in the top left of each panel.


Article number, page 16 of 32

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1



0.0

|CH 3OCHO Serpens SMM<br>-<br>18 109/83 17 108/73 18 118/70 17 117/60 18 1082<br>1 .0,,,, 075,,,, 0 .6,,<br>0 .4 355 K . 181 K 167 K<br>04<br>050 .<br>.<br>02 02<br>. 025 .<br>.<br>00<br>0 .0 0 .00 .<br>219810 219820 219830 221420 221430 221440 221640 22<br>19 18 19 18 19<br>8124 8114 1010/90 109/80 10101<br>06,,,,,,,, 06,,<br>. 341K 1 .0 179K . 178K<br>004.8 04<br>. .<br>0 .2 0 .5 0 .2|1 -a<br>17 1072 19 4164 18 4154<br>,, 06,,,,<br>.<br>310K<br>04<br>.<br>02<br>.<br>00<br>.|Col3|
|---|---|---|
|219810 219820 219830<br>0.0<br>0.2<br>0.4<br>355 K<br>1810, 9/8, 3<br>1710, 8/7, 3<br>221420 221430 221440<br>0.00<br>0.25<br>0.50<br>0.75<br>181 K<br>1811, 8/7, 0<br>1711, 7/6, 0<br>221640 22<br>0.0<br>0.2<br>0.4<br>0.6<br>167 K<br>1810, 8, 2<br><br>0.2<br>0.4<br>0.6<br>341 K<br>198, 12, 4<br>188, 11, 4<br>0.5<br>1.0<br>179 K<br>1910, 10/9, 0<br>1810, 9/8, 0<br><br>0.2<br>0.4<br>0.6<br>178 K<br>1910, 10, 1<br>0.8<br>1.0<br>CH3OCHO - Serpens SMM|1710, 7, 2<br>0.0<br>0.2<br>0.4<br>0.6<br>310 K<br>194, 16, 4<br>184, 15, 4<br>  1-a||
|219810 219820 219830<br>0.0<br>0.2<br>0.4<br>355 K<br>1810, 9/8, 3<br>1710, 8/7, 3<br>221420 221430 221440<br>0.00<br>0.25<br>0.50<br>0.75<br>181 K<br>1811, 8/7, 0<br>1711, 7/6, 0<br>221640 22<br>0.0<br>0.2<br>0.4<br>0.6<br>167 K<br>1810, 8, 2<br><br>0.2<br>0.4<br>0.6<br>341 K<br>198, 12, 4<br>188, 11, 4<br>0.5<br>1.0<br>179 K<br>1910, 10/9, 0<br>1810, 9/8, 0<br><br>0.2<br>0.4<br>0.6<br>178 K<br>1910, 10, 1<br>0.8<br>1.0<br>CH3OCHO - Serpens SMM|1650 221660<br>231890 231900 231910<br>1810, 9, 1<br>0.2<br>0.4<br>324 K<br>196, 14, 3<br>186, 13, 3|1650 221660<br>231890 231900 231910<br>1810, 9, 1<br>0.2<br>0.4<br>324 K<br>196, 14, 3<br>186, 13, 3|



234120 234130 234140


19 9, 10, 2 18 9, 9, 2



0.0


234330 234340 234350


19 9, 11/10, 0 18 9, 10/9, 0















0.0







1.0


0.5


0.0



0.0





233620 233630 233640


19 5, 15, 3 18 5, 14, 3



234110 234120 234130


19 7, 13, 4 18 7, 12, 4








|19 9111 B<br>,, T<br>075<br>. 166K<br>050<br>.<br>025<br>.0 .4|18 19<br>9101 8112<br>,,,,<br>075<br>. 155K<br>050<br>.<br>025<br>.|
|---|---|
|0.00|0.00|



19 5, 15, 4 18 5, 14, 4


0.2


0.0


235620 235630 235640





234370 234380 234390



1.0


0.5


0.0



234480 234490 234500


19 8, 12, 0 18 8, 11, 0



234490 234500 234510


19 8, 12/11, 1/0 18 8, 11/10, 1/0











234500 234510 234520


19 6, 13, 5 18 6, 12, 5



0.2


0.0


234430 234440 234450


19 8, 11, 2 18 8, 10, 2


235020 235030 235040


20 3, 18, 4 19 3, 17, 4


0.2


0.0


235190 235200 235210



235040 235050 235060



235040 235050 235060



19 7, 13, 0 18 7, 12, 0



235830 235840 235850


19 7, 12, 0 18 7, 11, 0

0.75


0.50


0.25


0.00











235070 235080 235090





0.6


0.4


0.2


0.0



0.6


0.4


0.2


0.0



20 2, 18, 3 19 2, 17, 3



21 2, 20, 3 20 2, 19, 3



0.75


0.50


0.25


0.00







235860 235870 235880235890 235900 235910 235910 235920 235930 235920 235930 235940

Frequency (MHz)



235860 235870 235880



235890 235900 235910



235910 235920 235930



235920 235930 235940



Fig. (B.5) Identified lines of CH 3 OCHO towards SMM1. The observed spectrum is plotted in black, with the best-fit synthetic
spectrum overplotted in blue ( _N_ T = (7.4±0.7)×10 [15] cm [−][2], _T_ ex = 215±20 K). The transition is indicated at the top of each panel and
the upper state energy is given in the top left of each panel.


Article number, page 17 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers


D 2 CO - Serpens SMM1-a






















|42, 3 1.0|32, 2 0.6 43, 2 D|33, 1 0.6 43, 1 D2CO - Serpens SMM1-|33, 0 -a|
|---|---|---|---|
|0.0<br>0.5<br>1.0<br>50 K<br>00<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>TB (K)|0.0<br>0.2<br>0.4<br>0.6<br>77 K|0.2<br>0.4<br>0.6<br>77 K||
|0.0<br>0.5<br>1.0<br>50 K<br>00<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>TB (K)|0.0<br>0.2<br>0.4<br>0.6<br>77 K|0.0||



233640 233650 233660 234280 234290 234300 234320 234330 234340

Frequency (MHz)



233640 233650 233660



234280 234290 234300



234320 234330 234340



Fig. (B.6) Identified lines of D 2 CO towards SMM1. The observed spectrum is plotted in black, with the best-fit synthetic spectrum
overplotted in blue ( _N_ T = (5.4±0.5)×10 [14] cm [−][2], _T_ ex = [200] K). The transition is indicated at the top of each panel and the upper
state energy is given in the top left of each panel.


HN [12] CO - Serpens SMM1-a



1.5


1.0


0.5


0.0



3


2


1



10 0, 10 9 0, 9



10 2, 9 9 2, 8



10 2, 8 9 2, 7





10 1, 10 9 1, 9



2


1









0

218970 218980 218990



1.5


1.0


0.5


0.0



219720 219730 219740



219730 219740 219750



0

219790 219800 219810



28 1, 28 29 0, 29

0.75


0.50



0.25


0.00



231860 231870 231880

Frequency (MHz)



Fig. (B.7) Identified lines of HN [12] CO towards SMM1. The observed spectrum is plotted in black and the line position is indicated
by the red dotted line. Because these lines are optically thick, not synthetic fit is given. The transition is indicated at the top of each
panel and the upper state energy is given in the top left of each panel.




















|10<br>11011/10/<br>10,,<br>.<br>06 101K<br>0.<br>8<br>.<br>04 (K)<br>0.6<br>.<br>00.2 .4 B<br>T<br>00 .0.2<br>00|HN<br>9 10<br>9 1910/9/8 2811/10/9<br>,,,,<br>04 231K<br>.<br>02<br>.<br>00<br>.|13CO Serpens SMM<br>-<br>9 10<br>2710/9/8 01011/10/<br>,, 08,,<br>.<br>58K<br>06<br>.<br>04<br>.<br>02<br>.|1 -a<br>9<br>9 0910/9/8<br>,,|
|---|---|---|---|
|0.0<br>0.2<br>0.4<br>0.6<br>101 K<br>101, 10, 11/10/<br>00<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>TB (K)|9<br>91, 9, 10/9/8<br>0.0<br>0.2<br>0.4<br>231 K<br>102, 8, 11/10/9<br>HN|0.0||



218980 218990 219000219730 219740 219750 219790 219800 219810

Frequency (MHz)



218980 218990 219000



219730 219740 219750



219790 219800 219810



Fig. (B.8) Identified lines of HN [13] CO towards SMM1. The observed spectrum is plotted in black, with the best-fit synthetic
spectrum overplotted in blue ( _N_ T = (1.9±0.3)×10 [14] cm [−][2], _T_ ex = 190±30 K). The transition is indicated at the top of each panel and
the upper state energy is given in the top left of each panel.


Article number, page 18 of 32

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1


12 CH 3 OH - Serpens SMM1-a



4 2, 3, 1 3 1, 2, 1





32 2, 30, 2 32 1, 31, 1





15 6, 10/9, 3 16 5, 12/11, 3





4 2, 3, 0 5 1, 4, 0


2


0


234670 234680 234690







217630 217640 217650



218430 218440 218450



0.50


0.25


0.00


234510 234520 234530





3


2



5 4, 2, 2 6 3, 3, 2





1


0



234690 234700 234710

Frequency (MHz)



Fig. (B.9) Identified lines of [12] CH 3 OH towards SMM1. The observed spectrum is plotted in black and the line position is indicated
by the red dotted line. Because these lines are optically thick, not synthetic fit is given. The transition is indicated at the top of each
panel and the upper state energy is given in the top left of each panel.


CH [18] 3 [OH - Serpens SMM1-a]



5 3, 3/2, 0 4 3, 2/1, 0


0.4


0.2


0.0



5 3, 2, 2 4 3, 2/1, 2

















5 2, 4, 0 4 2, 3, 0





0.3


0.2


0.1


0.0











231820 231830 231840 231850 231860 231870



231820 231830 231840





Fig. (B.10) Identified lines of CH [18] 3 [OH] [towards] [SMM1.] [The] [observed] [spectrum] [is] [plotted] [in] [black,] [with] [the] [best-fit] [synthetic]
spectrum overplotted in blue ( _N_ T = (2.0±0.7)×10 [15] cm [−][2], _T_ ex = 250±60 K). The transition is indicated at the top of each panel and
the upper state energy is given in the top left of each panel.


Article number, page 19 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers































|36<br>1125/26<br>10,<br>4. 468K<br>2|HOCH CN IRAS 1<br>2 -<br>35 36<br>1124/25 1224/25<br>,,<br>4 500K<br>2|6293 2422B full -be<br>-<br>35 36<br>1223/24 829/28<br>,,<br>4 389K<br>2|am offset position<br>35828/27 36<br>730/29<br>,,<br>4 363K<br>2|35<br>729/28<br>,|
|---|---|---|---|---|
|331980 331<br>0<br>332670 33<br>0<br>2<br>4<br>345 K<br>366, 31<br><br>2<br>4<br>318 K<br>372, 36<br>0.6<br>0.8|990 332000<br>332030 33<br>0<br>356, 30<br><br>2<br>4<br>345 K<br>366, 30|2040 332050<br>332030 332040<br>0<br>356, 29<br><br>2<br>4<br>323 K<br>364, 33|332050<br>332400 33<br>0<br>354, 32<br>0<br>2<br>4<br>335 K<br>365, 31|2410 332420<br>355, 30|
|331980 331<br>0<br>332670 33<br>0<br>2<br>4<br>345 K<br>366, 31<br><br>2<br>4<br>318 K<br>372, 36<br>0.6<br>0.8|2680 332690<br>332690 332<br>0<br>362, 35<br><br>2<br>4<br>318 K<br>371, 36, 1|700 332710<br>332790 3<br>0<br>361, 35, 1<br><br>2<br>4<br>312 K<br>371, 36, 0|32800 332810<br>333140 3<br>361, 35, 0<br><br>2<br>4<br>324 K<br>364, 32|33150 333160<br>354, 31|
|334170 3<br>0<br><br>2<br>4<br>310 K<br>362, 34<br>0.4<br>TB (K)|34180 334190<br>335130 <br>0<br>352, 33<br><br>2<br>4<br>318 K<br>364, 32|335140 335150<br>335180 3<br>0<br>354, 31<br><br>2<br>4<br>323 K<br>381, 38|35190 335200<br>335440 <br>0<br>70 335880<br>371, 37<br>335900 33<br>0<br>2<br>4<br>323 K<br>380, 38<br>363, 34, 1<br><br>2<br>4<br>324 K<br>373, 35, 0|335450 335460<br>5910 335920<br>370, 37<br>363, 34, 0|
|335750 3<br>0<br><br>2<br>4<br>318 K<br>380, 38|35760 335770<br>335820 <br>0<br>370, 37<br><br>2<br>4<br>311 K<br>363, 33|335830 335840<br>335860 3358<br>0<br>353, 32<br><br>2<br>4<br>329 K<br>373, 35, 1|335830 335840<br>335860 3358<br>0<br>353, 32<br><br>2<br>4<br>329 K<br>373, 35, 1|335830 335840<br>335860 3358<br>0<br>353, 32<br><br>2<br>4<br>329 K<br>373, 35, 1|
|335980 335990 336000<br>0<br>338250 338260 338270<br>0<br>339700 339710 339720<br>0<br>339760 339<br>0<br>341190 341200 341210<br>0<br>2<br>4<br>485 K<br>3711, 26/27<br>3611, 25/26<br>341190 341200 341210<br>0<br>2<br>4<br>429 K<br>379, 29/28<br>369, 28/27<br>341260 341270 341280<br>0<br>2<br>4<br>405 K<br>378, 30/29<br>368, 29/28<br>341420 3<br>0<br>2<br>4<br>385 K<br>377, 31<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>0.0<br>0.2|335980 335990 336000<br>0<br>338250 338260 338270<br>0<br>339700 339710 339720<br>0<br>339760 339<br>0<br>341190 341200 341210<br>0<br>2<br>4<br>485 K<br>3711, 26/27<br>3611, 25/26<br>341190 341200 341210<br>0<br>2<br>4<br>429 K<br>379, 29/28<br>369, 28/27<br>341260 341270 341280<br>0<br>2<br>4<br>405 K<br>378, 30/29<br>368, 29/28<br>341420 3<br>0<br>2<br>4<br>385 K<br>377, 31<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>0.0<br>0.2|338270<br>339700 33971<br>0<br>369, 28/27<br><br>2<br>4<br>405 K<br>378, 30/29|0 339720<br>339760 339<br>0<br>368, 29/28<br><br>2<br>4<br>385 K<br>377, 31|770 339780<br>41430 341440<br>367, 30<br>1.0|


Frequency (MHz)











Fig. (C.1) Spectral lines of HOCH 2 CN in the PILS spectrum towards IRAS 16293B at the full-beam offset position. The observed
spectrum is plotted in black, with synthetic spectra overplotted ( _N_ T = [1.0×10 [15] ] cm [−][2], _T_ ex = 150, blue, and 300 K, red). The
synthetic spectrum of the entire molecular inventory determined with PILS data towards this position is plotted in green. All
covered transitions with _A_ ij ≥ 1.0×10 [−][3] s [−][1] that are not blended are shown. The transition is indicated at the top of each panel and
the upper state energy is given in the top left of each panel. HOCH 2 CN is not detected in the full-beam offset position spectrum
towards IRAS 16293B.


Article number, page 20 of 32

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1


























|37830/29<br>10,<br>4. 400K<br>2<br>0<br>341490 34<br>37<br>434<br>,<br>4 339K<br>08<br>.<br>2|HOCH CN IRAS 1<br>2 -<br>36 37<br>829/28 1324/25<br>,,<br>4 545K<br>2<br>0<br>1500 341510 341520 341<br>36 37<br>433 533<br>,,<br>4 352K<br>2|6293 2422B full -be<br>-<br>36 37<br>1323/24 731/30<br>,,<br>4 379K<br>2|am offset position<br>36 37631<br>730/29<br>,,<br>4 362K<br>2|36<br>630<br>,<br>80 341990<br>372361<br>,,|
|---|---|---|---|---|
|341490 34<br>0<br>2<br>4<br>400 K<br>378, 30/29<br><br>2<br>4<br>339 K<br>374, 34<br>0.8<br>1.0|1500 341510<br>368, 29/28<br>341520 341<br>0<br>2<br>4<br>545 K<br>3713, 24/25<br>364, 33<br><br>2<br>4<br>352 K<br>375, 33<br>HOCH2CN - IRAS 1|530 341540<br>341650 341<br>0<br>365, 32<br><br>2<br>4<br>352 K<br>375, 32|660 341670<br>341970 3419<br>0<br>365, 31<br><br>2<br>4<br>335 K<br>382, 37, 1|660 341670<br>341970 3419<br>0<br>365, 31<br><br>2<br>4<br>335 K<br>382, 37, 1|
|341990 3420<br>0<br><br>2<br>4<br>330 K<br>382, 37, 0<br>0.6|00 342010<br>342110 34<br>0<br>372, 36, 0<br><br>2<br>4<br>339 K<br>390, 39|2120 342130<br>342500 342510<br>0<br>380, 38<br><br>2<br>4<br>340 K<br>374, 33, 1|342520<br>342930 342940<br>0<br>364, 32, 1<br><br>2<br>4<br>335 K<br>374, 33, 0|342950<br>364, 32, 0|
|343040 343050 343060<br>0<br>344620 <br>0<br>348720 348730 348740<br>0<br>2<br>4<br>340 K<br>383, 36<br>373, 35<br>350410 3<br>0<br>2<br>4<br>446 K<br>389, 30/29<br>350970 350980 350990<br>0<br>2<br>4<br>384 K<br>386, 33<br>376, 32<br>351010 35<br>0<br>2<br>4<br>384 K<br>386, 32<br><br>2<br>4<br>352 K<br>392, 38, 1<br>382, 37, 1<br><br>2<br>4<br>347 K<br>392, 38, 0<br>0.2<br>0.4<br>TB (K)|343040 343050 343060<br>0<br>344620 <br>0<br>348720 348730 348740<br>0<br>2<br>4<br>340 K<br>383, 36<br>373, 35<br>350410 3<br>0<br>2<br>4<br>446 K<br>389, 30/29<br>350970 350980 350990<br>0<br>2<br>4<br>384 K<br>386, 33<br>376, 32<br>351010 35<br>0<br>2<br>4<br>384 K<br>386, 32<br><br>2<br>4<br>352 K<br>392, 38, 1<br>382, 37, 1<br><br>2<br>4<br>347 K<br>392, 38, 0<br>0.2<br>0.4<br>TB (K)|344630 344640<br>345060 345<br>0<br>379, 29/28<br><br>2<br>4<br>568 K<br>3813, 25/26|070 345080<br>345460 3454<br>0<br>50520 350530<br>3713, 24/25<br>350610 3<br>0<br>2<br>4<br>467 K<br>3810, 28/29<br>376, 31<br><br>2<br>4<br>369 K<br>385, 34|70 345480<br>3710, 27/28|
|343040 343050 343060<br>0<br>344620 <br>0<br>348720 348730 348740<br>0<br>2<br>4<br>340 K<br>383, 36<br>373, 35<br>350410 3<br>0<br>2<br>4<br>446 K<br>389, 30/29<br>350970 350980 350990<br>0<br>2<br>4<br>384 K<br>386, 33<br>376, 32<br>351010 35<br>0<br>2<br>4<br>384 K<br>386, 32<br><br>2<br>4<br>352 K<br>392, 38, 1<br>382, 37, 1<br><br>2<br>4<br>347 K<br>392, 38, 0<br>0.2<br>0.4<br>TB (K)|343040 343050 343060<br>0<br>344620 <br>0<br>348720 348730 348740<br>0<br>2<br>4<br>340 K<br>383, 36<br>373, 35<br>350410 3<br>0<br>2<br>4<br>446 K<br>389, 30/29<br>350970 350980 350990<br>0<br>2<br>4<br>384 K<br>386, 33<br>376, 32<br>351010 35<br>0<br>2<br>4<br>384 K<br>386, 32<br><br>2<br>4<br>352 K<br>392, 38, 1<br>382, 37, 1<br><br>2<br>4<br>347 K<br>392, 38, 0<br>0.2<br>0.4<br>TB (K)|50420 350430<br>350510 3<br>0<br>376, 31<br><br>2<br>4<br>378 K<br>386, 32|50420 350430<br>350510 3<br>0<br>376, 31<br><br>2<br>4<br>378 K<br>386, 32|50620 350630<br>375, 33|
|343040 343050 343060<br>0<br>344620 <br>0<br>348720 348730 348740<br>0<br>2<br>4<br>340 K<br>383, 36<br>373, 35<br>350410 3<br>0<br>2<br>4<br>446 K<br>389, 30/29<br>350970 350980 350990<br>0<br>2<br>4<br>384 K<br>386, 33<br>376, 32<br>351010 35<br>0<br>2<br>4<br>384 K<br>386, 32<br><br>2<br>4<br>352 K<br>392, 38, 1<br>382, 37, 1<br><br>2<br>4<br>347 K<br>392, 38, 0<br>0.2<br>0.4<br>TB (K)|343040 343050 343060<br>0<br>344620 <br>0<br>348720 348730 348740<br>0<br>2<br>4<br>340 K<br>383, 36<br>373, 35<br>350410 3<br>0<br>2<br>4<br>446 K<br>389, 30/29<br>350970 350980 350990<br>0<br>2<br>4<br>384 K<br>386, 33<br>376, 32<br>351010 35<br>0<br>2<br>4<br>384 K<br>386, 32<br><br>2<br>4<br>352 K<br>392, 38, 1<br>382, 37, 1<br><br>2<br>4<br>347 K<br>392, 38, 0<br>0.2<br>0.4<br>TB (K)|1020 351030<br>351260 35<br>0<br>382, 37, 0<br><br>2<br>4<br>369 K<br>385, 33, 1|1270 351280<br>351390 351400 351410<br>0<br>375, 32, 1<br><br>2<br>4<br>363 K<br>385, 33, 0<br>375, 32, 0|1270 351280<br>351390 351400 351410<br>0<br>375, 32, 1<br><br>2<br>4<br>363 K<br>385, 33, 0<br>375, 32, 0|
|0<br>00|0|0|0||



351700 351710 351800 351810 351820 351890 351900 351910 352170 352180 352190

Frequency (MHz)



351690 351700 351710



351800 351810 351820



351890 351900 351910



352170 352180 352190



Fig. (C.2) Same as Fig. C.1



Article number, page 21 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers


























|39<br>138<br>10,<br>4. 346K<br>2|HOCH CN IRAS 1<br>2 -<br>38 38<br>137 236<br>,,<br>4 344K<br>2|6293 2422B full -be<br>-<br>37235 40<br>040<br>,,<br>4 356K<br>2|am offset position<br>39 40<br>039 140<br>,,<br>4 351K<br>2|39<br>139<br>,|
|---|---|---|---|---|
|352480 35<br>0<br><br>2<br>4<br>351 K<br>400, 40<br>0.8|2490 352500<br>353150 35316<br>0<br>390, 39<br><br>2<br>4<br>352 K<br>384, 34|0 353170<br>353330 353<br>0<br>374, 33<br><br>2<br>4<br>363 K<br>393, 37|340 353350<br>353390 <br>0<br>383, 36<br><br>2<br>4<br>463 K<br>399, 31/30|353400 353410<br>389, 30/29|
|353410 353<br>0<br>359870 3598<br>0<br>2<br>4<br>544 K<br>3912, 27/28<br><br>2<br>4<br>705 K<br>3916, 23/24<br>0.4<br>0.6<br>TB (K)|420 353430<br>355120 35513<br>0<br>80 359890<br>3812, 26/27<br>359910 35<br>0<br>2<br>4<br>419 K<br>397, 33<br>3816, 22/23<br><br>2<br>4<br>617 K<br>3914, 25/26|0 355140<br>358280 358290<br>0<br>9920 359930<br>387, 32<br>359940 3<br>0<br>2<br>4<br>579 K<br>3913, 26/27<br>3814, 24/25<br><br>2<br>4<br>401 K<br>396, 33|358300<br>359620 359630<br>0<br>59950 359960<br>3813, 25/26<br>359960 35<br>0<br>2<br>4<br>434 K<br>398, 32/31<br>386, 32<br><br>2<br>4<br>373 K<br>394, 36|359640<br>9970 359980<br>388, 31/30<br>384, 35|
|360020 360030 360040<br>0<br>360020 360030 360040<br>0<br>360290 36030<br>0<br><br>2<br>4<br>364 K<br>402, 39<br>392, 38<br><br>2<br>4<br>386 K<br>395, 35<br>385, 34<br><br>2<br>4<br>369 K<br>401, 39|360020 360030 360040<br>0<br>360020 360030 360040<br>0<br>360290 36030<br>0<br><br>2<br>4<br>364 K<br>402, 39<br>392, 38<br><br>2<br>4<br>386 K<br>395, 35<br>385, 34<br><br>2<br>4<br>369 K<br>401, 39|360020 360030 360040<br>0<br>360020 360030 360040<br>0<br>360290 36030<br>0<br><br>2<br>4<br>364 K<br>402, 39<br>392, 38<br><br>2<br>4<br>386 K<br>395, 35<br>385, 34<br><br>2<br>4<br>369 K<br>401, 39|0 360310<br>360360 360<br>0<br>391, 38<br><br>2<br>4<br>386 K<br>395, 34, 1|370 360380<br>385, 33, 1|
|360560 <br>0<br><br>2<br>4<br>381 K<br>395, 34, 0<br>0.2|360570 360580<br>360670 360680<br>0<br>385, 33, 0<br><br>2<br>4<br>361 K<br>392, 37|360690<br>361050 36106<br>0<br>382, 36<br><br>2<br>4<br>374 K<br>410, 41, 1|0 361070<br>361290 3<br>0<br>400, 40, 1<br><br>2<br>4<br>368 K<br>410, 41, 0|61300 361310<br>400, 40, 0|
|0<br>00|0|0|0||



361590 361600 361800 361810 361820 362040 362050 362060 362130 362140

Frequency (MHz)



361580 361590 361600



361800 361810 361820



362040 362050 362060



362130 362140 362150



Fig. (C.3) Same as Fig. C.1



Article number, page 22 of 32

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1










































































































































|36<br>1125/26<br>160,<br>. 468K<br>4<br>2|HOCH CN IRAS 1<br>2 -<br>35 36<br>1124/25 1224/25<br>, 6,<br>500K<br>4<br>2|6293 2422B half -b<br>-<br>35 36<br>1223/24 829/28<br>, 6,<br>389K<br>4<br>2|eam offset position<br>35828/27 36<br>730/29<br>, 6,<br>363K<br>4<br>2|35<br>729/28<br>,|
|---|---|---|---|---|
|331980 331990 332000<br>2<br>0<br>332030 33<br>2<br>0<br>332670 332680 332690<br>2<br>0<br>2<br>4<br>6<br>345 K<br>366, 31<br>356, 30<br>332690 332<br>0<br>2<br>4<br>345 K<br>366, 30<br><br>2<br>4<br>6<br>318 K<br>372, 36<br>362, 35<br><br>2<br>4<br>6<br>318 K<br>371, 36, 1<br>0.6<br>0.8|990 332000<br>332030 33<br>2<br>0<br>356, 30<br><br>2<br>4<br>345 K<br>366, 30|2040 332050<br>332030 332040<br>2<br>0<br>356, 29<br><br>2<br>4<br>323 K<br>364, 33|332050<br>332400 33<br>2<br>0<br>354, 32<br>0<br>2<br>4<br>6<br>335 K<br>365, 31|2410 332420<br>355, 30|
|331980 331990 332000<br>2<br>0<br>332030 33<br>2<br>0<br>332670 332680 332690<br>2<br>0<br>2<br>4<br>6<br>345 K<br>366, 31<br>356, 30<br>332690 332<br>0<br>2<br>4<br>345 K<br>366, 30<br><br>2<br>4<br>6<br>318 K<br>372, 36<br>362, 35<br><br>2<br>4<br>6<br>318 K<br>371, 36, 1<br>0.6<br>0.8|990 332000<br>332030 33<br>2<br>0<br>356, 30<br><br>2<br>4<br>345 K<br>366, 30|700 332710<br>332790 3<br>0<br>361, 35, 1<br><br>2<br>4<br>6<br>312 K<br>371, 36, 0|32800 332810<br>333140 3<br>2<br>361, 35, 0<br><br>2<br>4<br>6<br>324 K<br>364, 32|33150 333160<br>354, 31|
|334170 3<br>2<br>0<br><br>2<br>4<br>6<br>310 K<br>362, 34<br>0.4<br>TB (K)|34180 334190<br>335130 <br>2<br>0<br>352, 33<br><br>2<br>4<br>6<br>318 K<br>364, 32|335140 335150<br>335180 3<br>2<br>0<br>354, 31<br><br>2<br>4<br>6<br>323 K<br>381, 38|335140 335150<br>335180 3<br>2<br>0<br>354, 31<br><br>2<br>4<br>6<br>323 K<br>381, 38|335450 335460<br>5910 335920<br>370, 37<br>363, 34, 0|
|335750 3<br>2<br>0<br><br>2<br>4<br>6<br>318 K<br>380, 38|35760 335770<br>335820 <br>2<br>0<br>370, 37<br><br>2<br>4<br>6<br>311 K<br>363, 33|35760 335770<br>335820 <br>2<br>0<br>370, 37<br><br>2<br>4<br>6<br>311 K<br>363, 33|35760 335770<br>335820 <br>2<br>0<br>370, 37<br><br>2<br>4<br>6<br>311 K<br>363, 33|35760 335770<br>335820 <br>2<br>0<br>370, 37<br><br>2<br>4<br>6<br>311 K<br>363, 33|
|335980 335990 336000<br>2<br>0<br>338250 338260 338270<br>2<br>0<br>339700 339710 339720<br>2<br>0<br>339760 3397<br>2<br>0<br>341190 341200 341210<br>2<br>0<br>2<br>4<br>6<br>485 K<br>3711, 26/27<br>3611, 25/26<br>341190 341200 341210<br>2<br>0<br>2<br>4<br>6<br>429 K<br>379, 29/28<br>369, 28/27<br>341260 341270 341280<br>2<br>0<br>2<br>4<br>6<br>405 K<br>378, 30/29<br>368, 29/28<br>341420 3<br>2<br>0<br>2<br>4<br>6<br>385 K<br>377, 31<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>Frequency (MHz)<br>~~0~~.0<br>0.2|335980 335990 336000<br>2<br>0<br>338250 338260 338270<br>2<br>0<br>339700 339710 339720<br>2<br>0<br>339760 3397<br>2<br>0<br>341190 341200 341210<br>2<br>0<br>2<br>4<br>6<br>485 K<br>3711, 26/27<br>3611, 25/26<br>341190 341200 341210<br>2<br>0<br>2<br>4<br>6<br>429 K<br>379, 29/28<br>369, 28/27<br>341260 341270 341280<br>2<br>0<br>2<br>4<br>6<br>405 K<br>378, 30/29<br>368, 29/28<br>341420 3<br>2<br>0<br>2<br>4<br>6<br>385 K<br>377, 31<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>Frequency (MHz)<br>~~0~~.0<br>0.2|335980 335990 336000<br>2<br>0<br>338250 338260 338270<br>2<br>0<br>339700 339710 339720<br>2<br>0<br>339760 3397<br>2<br>0<br>341190 341200 341210<br>2<br>0<br>2<br>4<br>6<br>485 K<br>3711, 26/27<br>3611, 25/26<br>341190 341200 341210<br>2<br>0<br>2<br>4<br>6<br>429 K<br>379, 29/28<br>369, 28/27<br>341260 341270 341280<br>2<br>0<br>2<br>4<br>6<br>405 K<br>378, 30/29<br>368, 29/28<br>341420 3<br>2<br>0<br>2<br>4<br>6<br>385 K<br>377, 31<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>Frequency (MHz)<br>~~0~~.0<br>0.2|0 339720<br>339760 3397<br>2<br>0<br>368, 29/28<br><br>2<br>4<br>6<br>385 K<br>377, 31|70 339780<br>41430 341440<br>367, 30<br>1.0|



Fig. (C.4) Spectral lines of HOCH 2 CN in the PILS spectrum towards IRAS 16293B at the half-beam offset position. The observed
spectrum is plotted in black, with synthetic spectra overplotted ( _N_ T = [3.0×10 [15] ] cm [−][2], _T_ ex = 150, blue, and 300 K, red). All covered
transitions with _A_ ij ≥ 1.0×10 [−][3] s [−][1] that are not blended are shown. The transition is indicated at the top of each panel and the
upper state energy is given in the top left of each panel. HOCH 2 CN is detected in the half-beam offset position spectrum towards
IRAS 16293B.


Article number, page 23 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers















































































































































Frequency (MHz)






|HOCH CN IRAS 1<br>2 -<br>37830/29 36 37<br>829/28 1324/25<br>160,, 6,<br>. 400K 545K<br>4 4<br>2 2<br>0 0<br>2 2<br>341490 341500 341510 341520 341<br>37 36 37<br>434 433 533<br>6,, 6,<br>339K 352K<br>04.8 4<br>2 2|Col2|6293 2422B half -b<br>-<br>36 37<br>1323/24 731/30<br>, 6,<br>379K<br>4<br>2<br>0<br>2<br>530 341540 341650 341<br>36 37<br>532 532<br>, 6,<br>352K<br>4<br>2|eam offset position<br>36 37631<br>730/29<br>, 6,<br>362K<br>4<br>2|36<br>630<br>,<br>0 341990<br>372361<br>,,|
|---|---|---|---|---|
|341490 341500 341510<br>2<br>0<br>2<br>4<br>6<br>400 K<br>378, 30/29<br>368, 29/28<br>341520 341<br>2<br>0<br>2<br>4<br>6<br>545 K<br>3713, 24/25<br><br>2<br>4<br>6<br>339 K<br>374, 34<br>364, 33<br><br>2<br>4<br>6<br>352 K<br>375, 33<br>0.8<br>1.0<br>HOCH2CN - IRAS 1|341490 341500 341510<br>2<br>0<br>2<br>4<br>6<br>400 K<br>378, 30/29<br>368, 29/28<br>341520 341<br>2<br>0<br>2<br>4<br>6<br>545 K<br>3713, 24/25<br><br>2<br>4<br>6<br>339 K<br>374, 34<br>364, 33<br><br>2<br>4<br>6<br>352 K<br>375, 33<br>0.8<br>1.0<br>HOCH2CN - IRAS 1|530 341540<br>3613, 23/24<br>341650 341<br>2<br>0<br>2<br>4<br>6<br>379 K<br>377, 31/30<br>365, 32<br><br>2<br>4<br>6<br>352 K<br>375, 32<br>   6293<br>2422B - half-b|660 341670<br>341970 34198<br>2<br>0<br>365, 31<br><br>2<br>4<br>6<br>335 K<br>382, 37, 1|660 341670<br>341970 34198<br>2<br>0<br>365, 31<br><br>2<br>4<br>6<br>335 K<br>382, 37, 1|
|341990 3420<br>2<br>0<br><br>2<br>4<br>6<br>330 K<br>382, 37, 0<br>0.6|00 342010<br>342110 34<br>2<br>0<br>372, 36, 0<br><br>2<br>4<br>6<br>339 K<br>390, 39|2120 342130<br>342500 342510<br>2<br>0<br>380, 38<br><br>2<br>4<br>6<br>340 K<br>374, 33, 1|342520<br>342930 342940<br>2<br>0<br>364, 32, 1<br><br>2<br>4<br>6<br>335 K<br>374, 33, 0|342950<br>364, 32, 0|
|343040 <br>2<br>0<br>348720 3<br>2<br>0<br>2<br>4<br>6<br>340 K<br>383, 36<br>350970 350980<br>2<br>0<br>2<br>4<br>6<br>384 K<br>386, 33<br><br>2<br>4<br>6<br>352 K<br>392, 38, 1<br>0.2<br>0.4<br>TB (K)|343050 343060<br>344620 <br>2<br>0<br>48730 348740<br>373, 35<br>350410 3<br>2<br>0<br>2<br>4<br>6<br>446 K<br>389, 30/29<br> 350990<br>376, 32<br>351010 35<br>2<br>0<br>2<br>4<br>6<br>384 K<br>386, 32<br>382, 37, 1<br><br>2<br>4<br>6<br>347 K<br>392, 38, 0|344630 344640<br>345060 345<br>2<br>0<br>379, 29/28<br><br>2<br>4<br>6<br>568 K<br>3813, 25/26|070 345080<br>345460 3454<br>2<br>0<br>50520 350530<br>3713, 24/25<br>350610 3<br>2<br>0<br>2<br>4<br>6<br>467 K<br>3810, 28/29<br>1270 351280<br>376, 31<br>351390 35140<br>2<br>0<br>2<br>4<br>6<br>369 K<br>385, 34<br>375, 32, 1<br><br>2<br>4<br>6<br>363 K<br>385, 33, 0|70 345480<br>3710, 27/28|
|343040 <br>2<br>0<br>348720 3<br>2<br>0<br>2<br>4<br>6<br>340 K<br>383, 36<br>350970 350980<br>2<br>0<br>2<br>4<br>6<br>384 K<br>386, 33<br><br>2<br>4<br>6<br>352 K<br>392, 38, 1<br>0.2<br>0.4<br>TB (K)|343050 343060<br>344620 <br>2<br>0<br>48730 348740<br>373, 35<br>350410 3<br>2<br>0<br>2<br>4<br>6<br>446 K<br>389, 30/29<br> 350990<br>376, 32<br>351010 35<br>2<br>0<br>2<br>4<br>6<br>384 K<br>386, 32<br>382, 37, 1<br><br>2<br>4<br>6<br>347 K<br>392, 38, 0|50420 350430<br>350510 3<br>2<br>0<br>376, 31<br><br>2<br>4<br>6<br>378 K<br>386, 32|50420 350430<br>350510 3<br>2<br>0<br>376, 31<br><br>2<br>4<br>6<br>378 K<br>386, 32|50620 350630<br>0 351410<br>375, 33<br>375, 32, 0|
|343040 <br>2<br>0<br>348720 3<br>2<br>0<br>2<br>4<br>6<br>340 K<br>383, 36<br>350970 350980<br>2<br>0<br>2<br>4<br>6<br>384 K<br>386, 33<br><br>2<br>4<br>6<br>352 K<br>392, 38, 1<br>0.2<br>0.4<br>TB (K)|343050 343060<br>344620 <br>2<br>0<br>48730 348740<br>373, 35<br>350410 3<br>2<br>0<br>2<br>4<br>6<br>446 K<br>389, 30/29<br> 350990<br>376, 32<br>351010 35<br>2<br>0<br>2<br>4<br>6<br>384 K<br>386, 32<br>382, 37, 1<br><br>2<br>4<br>6<br>347 K<br>392, 38, 0|1020 351030<br>351260 35<br>2<br>0<br>382, 37, 0<br><br>2<br>4<br>6<br>369 K<br>385, 33, 1|1020 351030<br>351260 35<br>2<br>0<br>382, 37, 0<br><br>2<br>4<br>6<br>369 K<br>385, 33, 1|1020 351030<br>351260 35<br>2<br>0<br>382, 37, 0<br><br>2<br>4<br>6<br>369 K<br>385, 33, 1|
|351690 351700 351710<br>2<br>0<br>351800 351<br>2<br>0<br>0.0<br>0.2<br>~~0~~.0|351690 351700 351710<br>2<br>0<br>351800 351<br>2<br>0<br>0.0<br>0.2<br>~~0~~.0|810 351820<br>351890 351900 351910<br>2<br>0<br>352170 352180 352190<br>2<br>0<br>0.4<br>0.6<br>0.8<br>1.0<br>F (MH)|810 351820<br>351890 351900 351910<br>2<br>0<br>352170 352180 352190<br>2<br>0<br>0.4<br>0.6<br>0.8<br>1.0<br>F (MH)|810 351820<br>351890 351900 351910<br>2<br>0<br>352170 352180 352190<br>2<br>0<br>0.4<br>0.6<br>0.8<br>1.0<br>F (MH)|



Fig. (C.5) Same as Fig. C.4



Article number, page 24 of 32

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1




















































































































































|39<br>138<br>160,<br>. 346K<br>4<br>2|HOCH CN IRAS 1<br>2 -<br>38 38<br>137 236<br>, 6,<br>344K<br>4<br>2|6293 2422B half -beam offset position<br>-<br>37235 40 39 40<br>040 039 140<br>, 6,, 6,<br>356K 351K<br>4 4<br>2 2|Col4|39<br>139<br>,|
|---|---|---|---|---|
|353150 35316<br>2<br>0<br><br>2<br>4<br>6<br>351 K<br>400, 40<br>0.8|0 353170<br>353150 353160 353170<br>2<br>0<br>353330 353<br>2<br>0<br>390, 39<br><br>2<br>4<br>6<br>352 K<br>384, 34<br>374, 33<br><br>2<br>4<br>6<br>363 K<br>393, 37|0 353170<br>353150 353160 353170<br>2<br>0<br>353330 353<br>2<br>0<br>390, 39<br><br>2<br>4<br>6<br>352 K<br>384, 34<br>374, 33<br><br>2<br>4<br>6<br>363 K<br>393, 37|340 353350<br>353390 <br>2<br>0<br>383, 36<br><br>2<br>4<br>6<br>463 K<br>399, 31/30|353400 353410<br>389, 30/29|
|353410 353420 353430<br>2<br>0<br>355120 355130 355140<br>2<br>0<br>358280 358290<br>2<br>0<br>359870 359880 359890<br>2<br>0<br>2<br>4<br>6<br>544 K<br>3912, 27/28<br>3812, 26/27<br>359910 359920 359930<br>2<br>0<br>2<br>4<br>6<br>419 K<br>397, 33<br>387, 32<br>359940 3<br>2<br>0<br>2<br>4<br>6<br>579 K<br>3913, 26/27<br><br>2<br>4<br>6<br>705 K<br>3916, 23/24<br>3816, 22/23<br><br>2<br>4<br>6<br>617 K<br>3914, 25/26<br>3814, 24/25<br><br>2<br>4<br>6<br>401 K<br>396, 33<br>0.4<br>0.6<br>TB (K)|353410 353420 353430<br>2<br>0<br>355120 355130 355140<br>2<br>0<br>358280 358290<br>2<br>0<br>359870 359880 359890<br>2<br>0<br>2<br>4<br>6<br>544 K<br>3912, 27/28<br>3812, 26/27<br>359910 359920 359930<br>2<br>0<br>2<br>4<br>6<br>419 K<br>397, 33<br>387, 32<br>359940 3<br>2<br>0<br>2<br>4<br>6<br>579 K<br>3913, 26/27<br><br>2<br>4<br>6<br>705 K<br>3916, 23/24<br>3816, 22/23<br><br>2<br>4<br>6<br>617 K<br>3914, 25/26<br>3814, 24/25<br><br>2<br>4<br>6<br>401 K<br>396, 33<br>0.4<br>0.6<br>TB (K)|353410 353420 353430<br>2<br>0<br>355120 355130 355140<br>2<br>0<br>358280 358290<br>2<br>0<br>359870 359880 359890<br>2<br>0<br>2<br>4<br>6<br>544 K<br>3912, 27/28<br>3812, 26/27<br>359910 359920 359930<br>2<br>0<br>2<br>4<br>6<br>419 K<br>397, 33<br>387, 32<br>359940 3<br>2<br>0<br>2<br>4<br>6<br>579 K<br>3913, 26/27<br><br>2<br>4<br>6<br>705 K<br>3916, 23/24<br>3816, 22/23<br><br>2<br>4<br>6<br>617 K<br>3914, 25/26<br>3814, 24/25<br><br>2<br>4<br>6<br>401 K<br>396, 33<br>0.4<br>0.6<br>TB (K)|358300<br>359620 359630<br>2<br>0<br>59950 359960<br>3813, 25/26<br>359960 35<br>2<br>0<br>2<br>4<br>6<br>434 K<br>398, 32/31<br>386, 32<br><br>2<br>4<br>6<br>373 K<br>394, 36|359640<br>9970 359980<br>388, 31/30<br>384, 35|
|360020 36003<br>2<br>0<br><br>2<br>4<br>6<br>364 K<br>402, 39|0 360040<br>360020 360030<br>2<br>0<br>392, 38<br><br>2<br>4<br>6<br>386 K<br>395, 35|360040<br>360290 36030<br>2<br>0<br>385, 34<br><br>2<br>4<br>6<br>369 K<br>401, 39|0 360310<br>360360 360<br>2<br>0<br>0 361070<br>391, 38<br>361290 3<br>2<br>0<br>2<br>4<br>6<br>386 K<br>395, 34, 1<br>400, 40, 1<br><br>2<br>4<br>6<br>368 K<br>410, 41, 0|370 360380<br>61300 361310<br>385, 33, 1<br>400, 40, 0|
|360560 360570 360580<br>2<br>0<br>360670 360680<br>2<br>0<br><br>2<br>4<br>6<br>381 K<br>395, 34, 0<br>385, 33, 0<br><br>2<br>4<br>6<br>361 K<br>392, 37<br>0.2|360560 360570 360580<br>2<br>0<br>360670 360680<br>2<br>0<br><br>2<br>4<br>6<br>381 K<br>395, 34, 0<br>385, 33, 0<br><br>2<br>4<br>6<br>361 K<br>392, 37<br>0.2|360690<br>361050 36106<br>2<br>0<br>382, 36<br><br>2<br>4<br>6<br>374 K<br>410, 41, 1|360690<br>361050 36106<br>2<br>0<br>382, 36<br><br>2<br>4<br>6<br>374 K<br>410, 41, 1|360690<br>361050 36106<br>2<br>0<br>382, 36<br><br>2<br>4<br>6<br>374 K<br>410, 41, 1|
|361580 361590 361600<br>2<br>0<br>361800 3<br>2<br>0<br>0.0<br>0.2<br>~~0~~.0|361580 361590 361600<br>2<br>0<br>361800 3<br>2<br>0<br>0.0<br>0.2<br>~~0~~.0|61810 361820<br>362040 362050 362060<br>2<br>0<br>362130 <br>2<br>0<br>0.4<br>0.6<br>0.8<br>Frequency (MHz)|61810 361820<br>362040 362050 362060<br>2<br>0<br>362130 <br>2<br>0<br>0.4<br>0.6<br>0.8<br>Frequency (MHz)|362140 362150<br>1.0|



Fig. (C.6) Same as Fig. C.4



Article number, page 25 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers


Table (B.1) Spectral information of molecules detected towards SMM1-a


Molecule Database entry Transition Frequency _E_ up _A_ ij
_J_, _K_ a, _K_ c, ( _F_ ) (MHz) (K) s [−][1]

D 2 CO 32502 4 2 3 - 3 2 2 233 650.441 (0.0500) 49.63 2.69×10 [−][4]

CDMS 4 3 2 - 3 3 1 234 293.361 (0.0500) 76.62 1.58×10 [−][4]

4 3 1 - 3 3 0 234 331.062 (0.0500) 76.63 1.58×10 [−][4]

12
CH 3 OH 32504 15 6 9 3 - 16 5 11 3 217 642.677 (0.0220) 746 1.89×10 [−][5]

CDMS 15 6 10 3 - 16 5 12 3 217 642.678 (0.0220) 746 1.89×10 [−][5]

4 2 3 1 - 3 1 2 1 218 440.063 (0.0130) 45 5.69×10 [−][5]

32 2 30 2 - 32 1 31 1 234 523.365 (0.1070) 1256 8.95×10 [−][5]

4 2 3 0 - 5 1 4 0 234 683.370 (0.0120) 61 1.87×10 [−][5]

5 4 2 2 - 6 3 3 2 234 698.519 (0.0150) 123 6.34×10 [−][6]

CH [18] 3 [OH] 34504 5 0 5 0 - 4 0 4 0 231 758.446 (0.0300) 33 5.33×10 [−][5]

CDMS 5 3 3 0 - 4 3 2 0 231 796.218 (0.0300) 83 3.41×10 [−][5]

5 3 2 0 - 4 3 1 0 231 796.521 (0.0300) 83 3.41×10 [−][5]

5 3 2 2 - 4 3 1 2 231 801.304 (0.0300) 81 3.42×10 [−][5]

5 2 4 0 - 4 2 3 0 231 801.466 (0.0300) 71 4.53×10 [−][5]

5 1 4 2 - 4 1 3 2 231 826.744 (0.0300) 54 5.33×10 [−][5]

5 2 3 2 - 4 2 2 2 231 864.501 (0.0300) 56 4.41×10 [−][5]

CH 3 CN, ν 8 =1 41509 12 2 2 - 11 -2 2 221 367.450 (0.0011) 649 8.98×10 [−][4]

CDMS 12 -2 2 - 11 2 2 221 367.450 (0.0011) 649 8.98×10 [−][4]

12 4 3 - 11 -4 3 221 380.608 (0.0011) 655 8.21×10 [−][4]

12 -4 3 - 11 4 3 221 380.608 (0.0011) 655 8.21×10 [−][4]

12 1 2 - 11 1 2 221 387.271 (0.0011) 615 9.17×10 [−][4]

12 0 2 - 11 0 2 221 394.085 (0.0011) 594 9.24×10 [−][4]

12 3 3 - 11 3 3 221 403.521 (0.0011) 619 8.66×10 [−][4]

12 1 3 - 11 -1 3 221 625.840 (0.0011) 588 9.20×10 [−][4]

NH 2 CN 42003 11 1 11 0 - 10 1 10 0 218 461.795 (0.0200) 77 1.08×10 [−][3]

JPL 11 0 11 1 - 10 0 10 1 219 719.651 (0.0200) 135 1.08×10 [−][3]

11 1 10 0 - 10 1 9 0 221 361.160 (0.0200) 78 1.12×10 [−][3]

HN [12] CO 43511 10 1 10 - 9 1 9 218 985.696 (0.0192) 101 1.48×10 [−][4]

CDMS 10 2 9 - 9 2 8 219 733.850 (0.0300) 228 1.35×10 [−][4]

10 2 8 - 9 2 7 219 737.193 (0.0300) 228 1.35×10 [−][4]

10 0 10 - 9 0 9 219 798.274 (0.0040) 58 1.47×10 [−][4]

28 1 28 - 29 0 29 231 873.255 (0.0064) 470 6.68×10 [−][5]

HN [13] CO 44008 10 1 10 9 - 9 1 9 9 218 984.716 (0.1053) 101 1.63×10 [−][6]

10 1 10 11 - 9 1 9 10 218 985.697 (0.0192) 101 1.48×10 [−][4]

10 1 10 10 - 9 1 9 9 218 985.705 (0.0191) 101 1.46×10 [−][4]

10 1 10 9 - 9 1 9 8 218 985.706 (0.0191) 101 1.46×10 [−][4]

10 1 10 10 - 9 1 9 10 218 986.596 (0.0191) 101 1.48×10 [−][6]

10 1 10 10 - 9 1 9 10 218 986.596 (0.0191) 101 1.48×10 [−][6]

10 2 9 9 - 9 2 8 9 219 739.762 (0.0962) 231 1.60×10 [−][6]

10 2 9 11 - 9 2 8 10 219 740.451 (0.0274) 231 1.45×10 [−][4]

10 2 9 9 - 9 2 8 8 219 740.456 (0.0274) 231 1.43×10 [−][4]

10 2 9 10 - 9 2 8 9 219 740.471 (0.0274) 231 1.43×10 [−][4]

10 2 9 10 - 9 2 8 10 219 741.095 (0.0885) 231 1.45×10 [−][6]

10 2 8 9 - 9 2 7 9 219 743.054 (0.0966) 231 1.60×10 [−][6]

10 2 8 11 - 9 2 7 10 219 743.742 (0.0288) 231 1.45×10 [−][4]

10 2 8 9 - 9 2 7 8 219 743.747 (0.0288) 231 1.43×10 [−][4]

10 2 8 10 - 9 2 7 9 219 743.762 (0.0288) 231 1.43×10 [−][4]

10 2 8 10 - 9 2 7 10 219 744.386 (0.0890) 231 1.45×10 [−][6]

10 0 10 9 - 9 0 9 9 219 803.645 (0.1070) 58 1.67×10 [−][6]

10 0 10 11 - 9 0 9 10 21 9804.439 (0.0171) 58 1.51×10 [−][4]

10 0 10 10 - 9 0 9 9 219 804.442 (0.0171) 58 1.50×10 [−][4]

10 0 10 9 - 9 0 9 8 219 804.446 (0.0171) 58 1.49×10 [−][4]

10 0 10 10 - 9 0 9 10 219 805.163 (0.0965) 58 1.51×10 [−][6]

CH 3 CH 2 OH 46524 35 4 31 2 - 35 3 32 2 218 943.289 (0.0068) 560 7.38×10 [−][5]

CDMS 34 6 28 2 - 34 5 29 2 221 612.904 (0.0080) 548 8.84×10 [−][5]

31 5 27 1 - 31 4 27 0 231 789.850 (0.0120) 506 2.24×10 [−][5]


Article number, page 26 of 32

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1


Table (B.1) Continued.

Molecule Database entry Transition Frequency _E_ up _A_ ij
_J_, _K_ a, _K_ c, ( _F_ ) (MHz) (K) s [−][1]

22 5 18 2 - 22 4 19 2 231 790.056 (0.0035) 245 8.46×10 [−][5]

13 5 8 2 - 13 4 9 2 233 571.051 (0.0032) 108 7.54×10 [−][5]

14 5 10 2 - 14 4 11 2 233 601.554 (0.0032) 120 7.71×10 [−][5]

12 5 8 2 - 12 4 9 2 234 255.240 (0.0032) 97 7.39×10 [−][5]

11 5 6 2 - 11 4 7 2 234 406.433 (0.0033) 87 7.17×10 [−][5]

10 5 5 2 - 10 4 6 2 234 666.142 (0.0035) 78 6.89×10 [−][5]

10 5 6 2 - 10 4 7 2 234 714.782 (0.0035) 78 6.90×10 [−][5]

23 1 22 2 - 23 0 23 2 234 725.620 (0.0090) 233 3.17×10 [−][5]

9 5 4 2 - 9 4 5 2 234 852.862 (0.0038) 69 6.53×10 [−][5]

36 4 32 2 - 36 3 33 2 234 855.010 (0.0073) 591 8.70×10 [−][5]

9 5 5 2 - 9 4 6 2 234 873.873 (0.0038) 69 6.54×10 [−][5]

14 2 12 1 - 13 3 10 0 234 882.537 (0.0105) 155 3.64×10 [−][5]

14 0 14 1 - 13 1 12 0 235 158.494 (0.0058) 146 1.12×10 [−][4]

CH 3 NCO, ν=0 57505 25 -1 0 2 - 24 -1 0 2 217 595.174 (0.0500) 194 4.84×10 [−][4]

CDMS 25 0 0 2 - 24 0 0 2 217 595.174 (0.0500) 188 4.85×10 [−][4]

25 2 0 1 - 24 2 0 1 217 652.088 (0.0500) 171 4.82×10 [−][4]

24 3 0 1 - 23 3 0 1 217 701.086 (0.0500) 191 4.40×10 [−][4]

25 1 0 -3 - 24 1 0 -3 218 002.461 (0.0500) 258 4.93×10 [−][4]

25 0 0 -3 - 24 0 0 -3 218 014.630 (0.0500) 251 4.84×10 [−][4]

25 1 0 3 - 24 1 0 3 218 069.900 (0.0500) 257 4.93×10 [−][4]

25 1 24 0 - 24 1 23 0 218 541.803 (0.0500) 142 4.94×10 [−][4]

27 -1 0 1 - 26 -1 0 1 231 793.783 (0.0500) 175 6.02×10 [−][4]

27 2 26 0 - 26 2 25 0 234 088.125 (0.0500) 181 6.05×10 [−][4]

27 0 0 2 - 26 0 0 2 234 932.492 (0.0500) 210 6.11×10 [−][4]

27 -3 0 2 - 26 -3 0 2 235 663.096 (0.0500) 264 6.06×10 [−][4]

27 2 0 3 - 26 2 0 3 235 801.163 (0.0500) 296 6.12×10 [−][4]

27 2 0 -3 - 26 2 0 -3 235 803.211 (0.0500) 297 6.12×10 [−][4]

HOCH 2 CN 57512 24 2 23 1 - 23 2 22 1 218 994.156 (0.0009) 143 3.23×10 [−][4]

CDMS 24 8 17 1 - 23 8 16 1 221 334.546 (0.0009) 227 2.98×10 [−][4]

24 8 16 1 - 23 8 15 1 221 334.546 (0.0009) 227 2.98×10 [−][4]

24 9 15 1 - 23 9 14 1 221 344.331 (0.0010) 251 2.88×10 [−][4]

24 9 16 1 - 23 9 15 1 221 344.331 (0.0010) 251 2.88×10 [−][4]

24 10 14 1 - 23 10 13 1 221 372.125 (0.0010) 277 2.77×10 [−][4]

24 10 15 1 - 23 10 14 1 221 372.125 (0.0010) 277 2.77×10 [−][4]

24 6 19 1 - 23 6 18 1 221 406.933 (0.0009) 188 3.15×10 [−][4]

24 6 18 1 - 23 6 17 1 221 407.170 (0.0009) 188 3.15×10 [−][4]

24 11 13 1 - 23 11 12 1 221 413.638 (0.0010) 306 2.65×10 [−][4]

24 11 14 1 - 23 11 13 1 221 413.638 (0.0010) 306 2.65×10 [−][4]

24 12 12 1 - 23 12 11 1 221 466.304 (0.0011) 338 2.52×10 [−][4]

24 12 13 1 - 23 12 12 1 221 466.304 (0.0011) 338 2.52×10 [−][4]

24 3 22 1 - 23 3 21 1 221 466.604 (0.0009) 151 3.32×10 [−][4]

24 8 17 0 - 23 8 16 0 221 480.199 (0.0009) 222 2.95×10 [−][4]

24 8 16 0 - 23 8 15 0 221 480.199 (0.0009) 222 2.95×10 [−][4]

24 9 15 0 - 23 9 14 0 221 488.785 (0.0010) 245 2.86×10 [−][4]

24 9 16 0 - 23 9 15 0 221 488.785 (0.0010) 245 2.86×10 [−][4]

24 7 18 0 - 23 7 17 0 221 497.997 (0.0009) 201 3.04×10 [−][4]

24 7 17 0 - 23 7 16 0 221 498.002 (0.0009) 201 3.04×10 [−][4]

24 10 14 0 - 23 10 13 0 221 515.800 (0.0010) 272 2.75×10 [−][4]

24 10 15 0 - 23 10 14 0 221 515.800 (0.0010) 272 2.75×10 [−][4]

24 13 11 1 - 23 13 10 1 221 528.501 (0.0011) 372 2.38×10 [−][4]

24 13 12 1 - 23 13 11 1 221 528.501 (0.0011) 372 2.38×10 [−][4]

24 5 20 1 - 23 5 19 1 221 533.058 (0.0009) 173 3.22×10 [−][4]

24 5 19 1 - 23 5 18 1 221 542.097 (0.0009) 173 3.22×10 [−][4]

24 11 13 0 - 23 11 12 0 221 556.802 (0.0010) 301 2.63×10 [−][4]

24 11 14 0 - 23 11 13 0 221 556.802 (0.0010) 301 2.63×10 [−][4]

24 6 19 0 - 23 6 18 0 221 557.660 (0.0009) 183 3.12×10 [−][4]

24 6 18 0 - 23 6 17 0 221 557.911 (0.0009) 183 3.12×10 [−][4]


Article number, page 27 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers


Table (B.1) Continued.

Molecule Database entry Transition Frequency _E_ up _A_ ij
_J_, _K_ a, _K_ c, ( _F_ ) (MHz) (K) s [−][1]

24 12 12 0 - 23 12 11 0 221 609.140 (0.0010) 332 2.50×10 [−][4]

24 12 13 0 - 23 12 12 0 221 609.140 (0.0010) 332 2.50×10 [−][4]

25 2 23 1 - 24 2 22 1 234 584.932 (0.0300) 157 4.36×10 [−][4]

25 2 23 0 - 24 2 22 0 235 112.110 (0.0300) 152 3.94×10 [−][4]

CH 3 OCHO 60003 18 10 9 3 - 17 10 8 3 219 822.126 (0.1000) 355 1.11×10 [−][4]

JPL 18 10 8 3 - 17 10 7 3 219 822.126 (0.1000) 355 1.11×10 [−][4]

18 11 7 0 - 17 11 6 0 221 433.019 (0.1000) 181 1.03×10 [−][4]

18 11 8 0 - 17 11 7 0 221 433.019 (0.1000) 181 1.03×10 [−][4]

18 10 8 2 - 17 10 7 2 221 649.411 (0.1000) 167 1.14×10 [−][4]

19 4 16 4 - 18 4 15 4 231 896.060 (0.1000) 310 1.79×10 [−][4]

19 8 12 4 - 18 8 11 4 233 627.478 (0.1000) 341 1.59×10 [−][4]

19 10 10 0 - 18 10 9 0 234 124.883 (0.1000) 179 1.40×10 [−][4]

19 10 9 0 - 18 10 8 0 234 124.883 (0.1000) 179 1.40×10 [−][4]

19 10 10 1 - 18 10 9 1 234 134.600 (0.0500) 178 1.40×10 [−][4]

19 6 14 3 - 18 6 13 3 234 336.107 (0.1000) 324 1.75×10 [−][4]

19 5 15 3 - 18 5 14 3 234 381.269 (0.1000) 316 1.80×10 [−][4]

19 7 13 4 - 18 7 12 4 234 441.264 (0.1000) 332 1.68×10 [−][4]

19 9 10 2 - 18 9 9 2 234 486.395 (0.1000) 166 1.51×10 [−][4]

19 9 11 0 - 18 9 10 0 234 502.241 (0.0009) 166 1.51×10 [−][4]

19 9 10 0 - 18 9 9 0 234 502.432 (0.0009) 166 1.51×10 [−][4]

19 9 11 1 - 18 9 10 1 234 508.614 (0.1000) 166 1.51×10 [−][4]

19 8 11 2 - 18 8 10 2 235 029.952 (0.1000) 155 1.61×10 [−][4]

19 8 12 0 - 18 8 11 0 235 046.493 (0.1000) 155 1.61×10 [−][4]

19 8 11 0 - 18 8 10 0 235 051.378 (0.1000) 155 1.61×10 [−][4]

19 8 12 1 - 18 8 11 1 235 051.378 (0.1000) 155 1.61×10 [−][4]

19 6 13 5 - 18 6 12 5 235 084.738 (0.1000) 324 1.76×10 [−][4]

20 3 18 4 - 19 3 17 4 235 200.422 (0.1000) 314 1.90×10 [−][4]

19 5 15 4 - 18 5 14 4 235 633.058 (0.1000) 316 1.81×10 [−][4]

19 7 13 0 - 18 7 12 0 235 844.544 (0.1000) 145 1.71×10 [−][4]

19 7 13 1 - 18 7 12 1 235 865.969 (0.1000) 145 1.67×10 [−][4]

20 2 18 3 - 19 2 17 3 235 904.655 (0.1000) 315 1.91×10 [−][4]

21 2 20 3 - 20 2 19 3 235 919.352 (0.1000) 319 1.94×10 [−][4]

19 7 12 0 - 18 7 11 0 235 932.379 (0.1000) 145 1.72×10 [−][4]

a-(CH 2 OH) 2 62503 22 14 8 0 - 21 14 7 1 218 468.381 (0.0044) 221 1.51×10 [−][4]

CDMS 22 14 9 0 - 21 14 8 1 218 468.381 (0.0044) 221 1.51×10 [−][4]

20 4 16 1 - 19 4 15 0 219 764.925 (0.0040) 114 2.45×10 [−][4]

22 8 14 0 - 21 8 13 1 219 809.406 (0.0026) 156 2.24×10 [−][4]

28 12 16 0 - 28 11 17 0 233 426.949 (0.0036) 270 3.11×10 [−][5]

28 12 17 0 - 28 11 18 0 233 427.018 (0.0036) 270 3.10×10 [−][5]

28 12 16 1 - 28 11 17 1 233 451.651 (0.0036) 271 3.32×10 [−][5]

28 12 17 1 - 28 11 18 1 233 451.723 (0.0036) 271 3.32×10 [−][5]

22 5 18 1 - 21 5 17 0 233 536.696 (0.0025) 138 2.93×10 [−][4]

22 7 16 1 - 21 7 15 0 233 561.784 (0.0024) 149 2.79×10 [−][4]

22 6 17 1 - 21 6 16 0 234 264.446 (0.0026) 143 2.84×10 [−][4]

51 13 39 1 - 51 12 40 1 235 170.476 (0.0288) 737 4.73×10 [−][5]

23 3 21 1 - 22 3 20 0 235 170.573 (0.0023) 139 2.91×10 [−][4]

22 6 16 1 - 21 6 15 0 235 304.050 (0.0026) 143 2.90×10 [−][4]

14 5 9 1 - 13 4 10 1 235 326.413 (0.0021) 64 2.39×10 [−][5]

21 4 18 0 - 20 3 17 0 235 327.161 (0.0027) 122 6.30×10 [−][5]

23 2 21 1 - 22 2 20 0 235 600.178 (0.0022) 139 3.28×10 [−][4]

24 4 21 0 - 23 4 20 1 235 620.372 (0.0027) 155 2.88×10 [−][4]

26 1 26 0 - 25 1 25 1 235 834.239 (0.0040) 159 3.22×10 [−][4]

26 0 26 0 - 25 0 25 1 235 834.327 (0.0040) 159 3.22×10 [−][4]


Article number, page 28 of 32

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1


Table (C.1) Molecules and parameters used for the IRAS 16293B synthetic spectrum


Molecule Name Tag Database _N_ T _T_ ex
(cm [−][2] ) (K)
CCH Ethynyl radical 25501 CDMS 3.00×10 [13] 120
HCN Hydrogen cyanide 27501 CDMS 5.00×10 [16] 120
HNC Hydrogen isocyanide 27502 CDMS 5.00×10 [16] 120
H [13] CN Hydrogen cyanide 28501 CDMS 2.00×10 [14] 300
CO Carbon monoxide 28503 CDMS 1.00×10 [20] 100
HC [15] N Hydrogen cyanide 28506 CDMS 2.00×10 [14] 300
DNC Hydrogen cyanide 28508 CDMS 7.00×10 [14] 300
13
CO Carbon monoxide 29501 CDMS 3.10×10 [19] 100
C [17] O Carbon monoxide 29503 CDMS 8.00×10 [16] 100
H [13] C [15] Hydrogen cyanide 29512 CDMS 2.00×10 [14] 300
HNCH 2 Methanimine 29518 CDMS 8.00×10 [14] 100
NO Nitrogen oxide 30008 JPL 2.00×10 [16] 100
H 2 CO Formaldehyde 30501 CDMS 1.80×10 [18] 105
C [18] O Carbon monoxide 30502 CDMS 1.00×10 [17] 100
DCO [+] Formyl radical 30510 CDMS 3.00×10 [12] 29
CH 3 NH 2 Methylamine 31008 JPL 5.30×10 [14] 100
HDCO Formaldehyde 31501 CDMS 1.30×10 [17] 105
H [13] 2 [CO] Formaldehyde 31503 CDMS 3.60×10 [16] 105
D 2 CO Formaldehyde 32502 CDMS 1.60×10 [16] 105
H 2 C [18] O Formaldehyde 32503 CDMS 2.50×10 [15] 105
CH 3 OH Methanol 32504 CDMS 2.00×10 [19] 300
CH 2 DOH Methanol 33004 JPL 7.10×10 [17] 300
13
CH 3 OH Methanol 33502 CDMS 4.00×10 [16] 300
NH 2 OH Hydroxylamine 33503 CDMS 3.70×10 [14] 100
D [13] 2 [CO] Formaldehyde 33506 CDMS 2.20×10 [14] 105
HDC [18] O Formaldehyde 33510 CDMS 1.40×10 [14] 105
H 2 S Hydrogen sulfide 34502 CDMS 1.00×10 [18] 125
CH [18] 3 [OH] Methanol 34504 CDMS 2.00×10 [16] 300
HDS Hydrogen sulfide 35502 CDMS 2.00×10 [16] 125
HD [34] S Hydrogen sulfide 37503 CDMS 1.00×10 [15] 125
c-C 3 H 2 Cyclopropenylidene 38508 CDMS 2.00×10 [14] 100
CH 3 CCH Propyne 40502 CDMS 6.80×10 [15] 100
CH 3 CN Acetonitrile 41505 CDMS 4.00×10 [16] 120
CH 3 CN ν 8 =1 Acetonitrile 41509 CDMS 4.00×10 [16] 120
CH 3 NC Methyl isocyanide 41514 CDMS 2.00×10 [14] 150
H 2 CCO Ketene 42501 CDMS 4.80×10 [16] 125
HNCNH Carbodiimide 42506 CDMS 2.40×10 [16] 300

13
CH 3 CN Acetonitrile 42508 CDMS 3.30×10 [14] 130
CH [13] 3 [CN] Acetonitrile 42509 CDMS 3.00×10 [14] 130
CH 3 C [15] N Acetonitrile 42510 CDMS 8.70×10 [13] 130
CH 2 DCN Acetonitrile 42511 CDMS 5.60×10 [14] 130
H 2 C [13] CO Ketene 43505 CDMS 7.10×10 [14] 125
H [13] Ketene 43506 CDMS 7.10×10 [14] 125
2 [CCO]
HDC 2 O Ketene 43507 CDMS 2.00×10 [15] 125
HNCO Isocyanic acid 43511 CDMS 3.70×10 [16] 300
CHD 2 CN Acetonitrile 43514 CDMS 1.20×10 [14] 130
H 2 N [13] CN Cyanamide 43515 CDMS 3.00×10 [13] 300
N 2 O Nitrous oxide 44004 JPL 5.00×10 [16] 100
DNCO Isocyanic acid 44006 JPL 3.00×10 [14] 300
HN [13] CO Isocyanic acid 44008 JPL 4.00×10 [14] 300
CS Carbon monosulfide 44501 CDMS 1.00×10 [16] 125
c-C 2 H 4 O Ethylene oxide 44504 CDMS 4.10×10 [15] 125
SiO Silicon monoxide 44505 CDMS 7.00×10 [13] 300
s-H 2 CCHOH Vinylalcohol 44506 CDMS 1.20×10 [17] 125
a-H 2 CCHOH Vinylalcohol 44507 CDMS 1.20×10 [17] 125
C [33] S Carbon monosulfide 45502 CDMS 1.00×10 [14] 125


Article number, page 29 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers


Table (C.1) Continued.

Molecule Name Tag Database _N_ T _T_ ex
(cm [−][2] ) (K)
NH 2 CHO Formamide 45512 CDMS 1.00×10 [16] 300
CH 3 CDO Acetaldehyde 45524 CDMS 7.40×10 [15] 125
CH 2 DCHO Acetaldehyde 45525 CDMS 6.20×10 [15] 125
C [34] S Carbon monosulfide 46501 CDMS 3.00×10 [14] 125
t-HCOOH Formic acid 46506 CDMS 5.08×10 [16] 300
H 2 CS Thioformaldehyde 46509 CDMS 1.50×10 [15] 125
NH [13] Formamide 46512 CDMS 1.00×10 [14] 300
2 [CHO]
CH 3 OCH 3 Dimethyl ether 46514 CDMS 3.00×10 [17] 125
NH 2 CDO Formamide 46520 CDMS 1.40×10 [14] 300
cis-NHDCHO Formamide 46521 CDMS 1.40×10 [14] 300
trans-NHDCHO Formamide 46522 CDMS 1.20×10 [14] 300
C 2 H 5 OH Ethanol 46524 CDMS 2.30×10 [17] 300
HONO Nitrous acid 47007 JPL 9.00×10 [14] 100
t-H [13] COOH Formic acid 47503 CDMS 8.30×10 [14] 300
HDCS Thioformaldehyde 47504 CDMS 1.50×10 [14] 125
CH [13] 3 [CH] [2] [OH] Ethanol 47511 CDMS 4.60×10 [14] 300
13
CH 3 CH 2 OH Ethanol 47512 CDMS 4.60×10 [14] 300
CH 3 CH 2 OD Ethanol 47515 CDMS 5.75×10 [14] 300
CH 3 CHDOH Ethanol 47516 CDMS 1.15×10 [15] 300
a-CH 2 DCH 2 OH Ethanol 47517 CDMS 1.34×10 [15] 300
s-CH 2 DCH 2 OH Ethanol 47518 CDMS 6.51×10 [14] 300
SO Sulfur monoxide 48501 CDMS 5.00×10 [14] 125
C [36] S Carbon monosulfide 48503 CDMS 2.00×10 [13] 125
CH 3 SH Methyl mercaptan 48510 CDMS 5.50×10 [15] 125
CH [35] 3 [Cl] Chloromethane 50007 JPL 3.10×10 [13] 125
HC 3 N Cyanoacetylene 51501 CDMS 1.40×10 [14] 100
CH [37] 3 [Cl] Chloromethane 52009 JPL 2.20×10 [14] 125
C 2 H 3 CN Vinyl cyanide 53515 CDMS 4.80×10 [14] 110
C 2 H 5 CN Ethyl cyanide 55502 CDMS 1.50×10 [15] 160
CH 3 NCO Methyl isocyanate 57505 CDMS 3.00×10 [15] 300
CH 3 C(O)CH 3 Acetone 58003 JPL 3.40×10 [16] 125
CH 3 CH 2 CHO Propanal 58505 CDMS 1.48×10 [15] 125
CH 3 OCHO Methylformate 60003 JPL 2.60×10 [17] 300
HOCH 2 CHO Glycolaldehyde 60501 CDMS 3.40×10 [16] 300
OCS Carbonyl sulfide 60503 CDMS 2.00×10 [16] 125
OCS ν 2 =1 Carbonyl sulfide 60504 CDMS 2.00×10 [17] 125
CH 3 COOH Acetic acid 60523 CDMS 3.00×10 [15] 300
O [13] CS Carbonyl sulfide 61502 CDMS 5.00×10 [15] 125
OC [33] S Carbonyl sulfide 61503 CDMS 3.00×10 [15] 100
HOCH [13] 2 [CHO] Glycolaldehyde 61513 CDMS 4.46×10 [14] 300
HO [13] CH 2 CHO Glycolaldehyde 61514 CDMS 4.46×10 [14] 300
CH 3 O [13] CHO Glycolaldehyde 61515 CDMS 6.30×10 [15] 300
DOCH 2 CHO Glycolaldehyde 61516 CDMS 4.86×10 [14] 300
HOCHDCHO Glycolaldehyde 61517 CDMS 1.27×10 [15] 300
HOCH 2 CDO Glycolaldehyde 61518 CDMS 6.25×10 [14] 300
a-(CH 2 OH) 2 Ethylene glycol 62503 CDMS 1.37×10 [16] 300
s-(CH 2 OH) 2 Ethylene glycol 62504 CDMS 3.62×10 [16] 300
OC [34] S Carbonyl sulfide 62505 CDMS 1.50×10 [16] 125
18
OCS Carbonyl sulfide 62506 CDMS 7.00×10 [14] 125
SO 2 Sulfur dioxide 64502 CDMS 1.50×10 [15] 125
34
O 2 Sulfur dioxide 66501 CDMS 4.00×10 [14] 125


Article number, page 30 of 32

N.F.W. Ligterink et al.: The prebiotic molecular inventory of Serpens SMM1


Table (C.1) HOCH 2 CN lines in the PILS data towards IRAS 16293B


Transition Frequency _E_ up _A_ ij Blending species
_J_, _K_ a, _K_ c, _F_ (MHz) (K) s [−][1]

36 11 25 1 - 35 11 24 1 331 990.003 468 1.03×10 [−][3] g-(CH 2 OH) 2
36 11 26 1 - 35 11 25 1 331 990.003 468 1.03×10 [−][3] g-(CH 2 OH) 2
36 12 24 1 - 35 12 23 1 332 038.123 500 1.01×10 [−][3] CH 3 OCHO
36 12 25 1 - 35 12 24 1 332 038.123 500 1.01×10 [−][3] CH 3 OCHO
36 8 29 1 - 35 8 28 1 332 045.021 389 1.08×10 [−][3] g-(CH 2 OH) 2
36 8 28 1 - 35 8 27 1 332 045.044 389 1.08×10 [−][3] g-(CH 2 OH) 2
36 7 30 0 - 35 7 29 0 332 409.418 363 1.09×10 [−][3] –
36 7 29 0 - 35 7 28 0 332 410.281 363 1.09×10 [−][3] –
36 6 31 0 - 35 6 30 0 332 678.904 345 1.10×10 [−][3] –
36 6 30 0 - 35 6 29 0 332 699.957 345 1.10×10 [−][3] –
36 4 33 1 - 35 4 32 1 332 797.489 323 1.14×10 [−][3] –
36 5 31 1 - 35 5 30 1 333 147.976 335 1.13×10 [−][3] –
37 2 36 1 - 36 2 35 1 334 177.762 318 1.15×10 [−][3] CH 3 OCHO, CH 3 O [13] CHO, C 2 H 5 CN, HO [13] CH 2 CHO
37 1 36 1 - 36 1 35 1 335 135.448 318 1.16×10 [−][3] CH 3 OH
37 1 36 0 - 36 1 35 0 335 187.943 313 1.16×10 [−][3] –
36 4 32 1 - 35 4 31 1 335 446.009 324 1.17×10 [−][3] –
36 2 34 1 - 35 2 33 1 335 757.704 310 1.15×10 [−][3] g-(CH 2 OH) 2
36 4 32 0 - 35 4 31 0 335 825.850 318 1.15×10 [−][3] g-(CH 2 OH) 2, CH 3 C(O)CH 3, CH 3 OCHO
38 1 38 1 - 37 1 37 1 335 871.388 323 1.17×10 [−][3] –
38 0 38 1 - 37 0 37 1 335 909.319 323 1.17×10 [−][3] –
38 0 38 0 - 37 0 37 0 335 985.342 318 1.17×10 [−][3] CH 3 CH 2 OH, g-(CH 2 OH) 2
36 3 33 0 - 35 3 32 0 338 263.867 311 1.07×10 [−][3] CH 3 OCHO
37 3 35 1 - 36 3 34 1 339 712.712 329 1.21×10 [−][3] NH 2 CHO
37 3 35 0 - 36 3 34 0 339 771.178 324 1.20×10 [−][3] –
37 11 26 1 - 36 11 25 1 341 198.194 484 1.13×10 [−][3] –
37 11 27 1 - 36 11 26 1 341 198.194 484 1.13×10 [−][3] –
37 9 29 1 - 36 9 28 1 341 199.695 429 1.16×10 [−][3] g-(CH 2 OH) 2
37 9 28 1 - 36 9 27 1 341 199.696 429 1.16×10 [−][3] g-(CH 2 OH) 2
37 8 30 1 - 36 8 29 1 341 272.746 405 1.18×10 [−][3] HOCH 2 CHO, CH 3 CDO
37 8 29 1 - 36 8 28 1 341 272.781 405 1.18×10 [−][3] HOCH 2 CHO, CH 3 CDO
37 7 31 1 - 36 7 30 1 341 427.962 385 1.20×10 [−][3] CH 3 CHO
37 8 30 0 - 36 8 29 0 341 498.917 400 1.17×10 [−][3] CH 3 OCHO
37 8 29 0 - 36 8 28 0 341 498.954 400 1.17×10 [−][3] CH 3 OCHO
37 13 24 0 - 36 13 23 0 341 529.626 545 1.08×10 [−][3] a-(CH 2 OH) 2
37 13 25 0 - 36 13 24 0 341 529.626 545 1.08×10 [−][3] a-(CH 2 OH) 2
37 7 31 0 - 36 7 30 0 341 659.715 379 1.18×10 [−][3] –
37 7 30 0 - 36 7 29 0 341 660.941 379 1.18×10 [−][3] –
37 6 31 0 - 36 6 30 0 341 982.421 362 1.20×10 [−][3] CH 3 O [13] CHO
37 4 34 1 - 36 4 33 1 342 001.917 339 1.23×10 [−][3] –
37 5 33 1 - 36 5 32 1 342 118.267 352 1.23×10 [−][3] HOCH 2 CHO
37 5 32 1 - 36 5 31 1 342 514.548 352 1.23×10 [−][3] CH 3 CDO
38 2 37 1 - 37 2 36 1 342 945.040 335 1.25×10 [−][3] H 2 CS, CH 3 O [13] CHO
38 2 37 0 - 37 2 36 0 343 045.762 330 1.24×10 [−][3] CH 3 CDO
39 0 39 1 - 38 0 38 1 344 625.126 339 1.27×10 [−][3] HONO, CH 2 DOH, CH 3 CHO
37 4 33 1 - 36 4 32 1 345 070.674 340 1.27×10 [−][3] CH 3 OCHO
37 4 33 0 - 36 4 32 0 345 471.229 335 1.25×10 [−][3] CH 3 OCHO
38 3 36 0 - 37 3 35 0 348 727.094 340 1.30×10 [−][3] –
38 9 30 1 - 37 9 29 1 350 417.202 446 1.27×10 [−][3] a-(CH 2 OH) 2
38 9 29 1 - 37 9 28 1 350 417.203 446 1.27×10 [−][3] a-(CH 2 OH) 2
38 13 25 1 - 37 13 24 1 350 517.318 568 1.19×10 [−][3] –
38 13 26 1 - 37 13 25 1 350 517.318 568 1.19×10 [−][3] –
38 10 28 0 - 37 10 27 0 350 617.089 467 1.24×10 [−][3] CH 3 O [13] CHO
38 10 29 0 - 37 10 28 0 350 617.089 467 1.24×10 [−][3] CH 3 O [13] CHO
38 6 33 1 - 37 6 32 1 350 983.970 384 1.32×10 [−][3] CH 3 OCHO, CH 3 CDO
38 6 32 1 - 37 6 31 1 351 019.318 384 1.32×10 [−][3] H 2 C [13] CO, CH 3 OCHO
38 6 32 0 - 37 6 31 0 351 269.282 378 1.30×10 [−][3] –
38 5 34 1 - 37 5 33 1 351 402.459 369 1.33×10 [−][3] –


Article number, page 31 of 32

_A&A proofs:_ manuscript no. SMM1_C2H3NO_isomers


Table (C.1) Continued.

Transition Frequency _E_ up _A_ ij Blending species
_J_, _K_ a, _K_ c, _F_ (MHz) (K) s [−][1]

39 2 38 1 - 38 2 37 1 351 704.972 352 1.35×10 [−][3] –
39 2 38 0 - 38 2 37 0 351 809.704 346 1.34×10 [−][3] –
38 5 33 1 - 37 5 32 1 351 897.151 369 1.34×10 [−][3] –
38 5 33 0 - 37 5 32 0 352 181.763 363 1.32×10 [−][3] CH 3 O [13] CHO
39 1 38 0 - 38 1 37 0 352 488.531 346 1.35×10 [−][3] CH [18] 3 [OH]
38 2 36 1 - 37 2 35 1 353 163.191 344 1.35×10 [−][3] –
40 0 40 1 - 39 0 39 1 353 340.026 356 1.37×10 [−][3] CH 3 OCHO
40 1 40 0 - 39 1 39 0 353 395.992 351 1.37×10 [−][3] –
40 0 40 0 - 39 0 39 0 353 420.250 351 1.37×10 [−][3] –
38 4 34 0 - 37 4 33 0 355 133.419 352 1.36×10 [−][3] –
39 3 37 1 - 38 3 36 1 358 294.680 363 1.33×10 [−][3] –
39 9 31 1 - 38 9 30 1 359 634.337 463 1.37×10 [−][3] –
39 9 30 1 - 38 9 29 1 359 634.339 463 1.37×10 [−][3] –
39 12 27 0 - 38 12 26 0 359 881.373 545 1.30×10 [−][3] –
39 12 28 0 - 38 12 27 0 359 881.373 545 1.30×10 [−][3] –
39 7 33 1 - 38 7 32 1 359 919.218 419 1.41×10 [−][3] –
39 13 26 0 - 38 13 25 0 359 947.354 579 1.28×10 [−][3] –
39 13 27 0 - 38 13 26 0 359 947.354 579 1.28×10 [−][3] –
39 8 32 0 - 38 8 31 0 359 967.849 434 1.38×10 [−][3] –
39 8 31 0 - 38 8 30 0 359 967.931 434 1.38×10 [−][3] –
39 16 23 1 - 38 16 22 1 360 033.494 705 1.21×10 [−][3] t-HCOOH
39 16 24 1 - 38 16 23 1 360 033.494 705 1.21×10 [−][3] t-HCOOH
39 14 25 0 - 38 14 24 0 360 034.284 617 1.25×10 [−][3] t-HCOOH
39 14 26 0 - 38 14 25 0 360 034.284 617 1.25×10 [−][3] t-HCOOH
39 6 33 1 - 38 6 32 1 360 303.101 401 1.43×10 [−][3] –
39 4 36 1 - 38 4 35 1 360 369.224 373 1.45×10 [−][3] –
40 2 39 0 - 39 2 38 0 360 565.572 364 1.44×10 [−][3] –
39 5 35 1 - 38 5 34 1 360 684.867 386 1.44×10 [−][3] –
40 1 39 1 - 39 1 38 1 361 063.161 369 1.46×10 [−][3] –
39 5 34 1 - 38 5 33 1 361 297.474 386 1.45×10 [−][3] CH 3 CH 2 OH
39 5 34 0 - 38 5 33 0 361 594.894 381 1.43×10 [−][3] –
39 2 37 1 - 38 2 36 1 361 805.086 361 1.46×10 [−][3] CH 3 OCHO
41 0 41 1 - 40 0 40 1 362 053.851 374 1.47×10 [−][3] CH 3 C(O)CH 3
41 0 41 0 - 40 0 40 0 362 136.053 368 1.47×10 [−][3] –


**Notes.** List of identified and unidentified HOCH 2 CN transitions with A ij ≥ 1.0×10 [−][3] s [−][1] towards IRAS 16293B in the PILS data set.


Article number, page 32 of 32


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "T_ex free range: 50 – 350 K; N_T free range: two orders of magnitude centered on by-eye fit",
  "failed_quote": "The column density was given as a free parameter over two orders of magnitude centered on the by-eye fit column density and the excitation temperature was a free parameter from 50 – 350 K."
 },
 {
  "path": "analysis_steps[1].validation.evidence[1]",
  "value": "Check line positions for blending species with A_ij > 1×10^-6 and E_up of 0–1000 K; compare against full-inventory synthetic spectrum in IRAS 16293B.",
  "failed_quote": "A synthetic spectrum of the previously identified molecules towards IRAS 16293B at the full-beam offset position is added in green."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "HOCH2CN is identified in IRAS 16293B PILS data at the half-beam offset position (compact emission), but only tentatively at the full-beam offset position.",
  "failed_quote": "Therefore, HOCH 2 CN can only tentatively be identified towards the full-beam offset position, with a column density of ∼1.0×10 15 cm −2 at T ex = 150 and 300 K."
 },
 {
  "path": "findings_qualitative[3].evidence[0]",
  "value": "The [CH3NCO]/[HNCO] ratio is uniform at ~10% across low-, intermediate-, and high-mass star-forming regions, suggesting a chemical link and early formation in ice mantles.",
  "failed_quote": "These ratios are found to be uniform throughout all sources at [CH 3 NCO]/[HNCO] = ∼10 %. This indicates that there is a chemical link between both species, but also that its ratios is already set at an early stage of star-formation."
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "The formation of CH3NCO and HOCH2CN is driven by kinetic processes rather than thermodynamic equilibrium.",
  "failed_quote": "In a thermodynamic equilibrium, lower energy or more stable products are favored and in such a scenario, CH 3 NCO is expected to be more abundant than HOCH 2 CN by a factor of at least 1×10 9 (assuming a temperature of 300 K)."
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "STATCONT followed by CASA uvcontsub in the uv-plane was chosen because STATCONT only subtracts zeroth-order polynomials while non-zeroth-order baselines are present, and uv-plane subtraction avoids deconvolution errors from the brighter continuum.",
  "failed_quote": "STATCONT can only subtract zeroth-order polynomials, while in this dataset non-zeroth-order baselines are visible. Furthermore, continuum subtraction in the uv-plane is more desirable since the deconvolution of the line emission is more robust when it is not subjected to the deconvolution errors of the brighter continuum."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Thermodynamic equilibrium formation of C2H3NO isomers was rejected because CH3NCO and HOCH2CN are equally abundant rather than showing the >10^9 CH3NCO excess predicted by thermodynamics.",
  "failed_quote": "In a thermodynamic equilibrium, lower energy or more stable products are favored and in such a scenario, CH 3 NCO is expected to be more abundant than HOCH 2 CN by a factor of at least 1×10 9 (assuming a temperature of 300 K). The fact that CH 3 NCO and HOCH 2 CN are found to be equally abundant is, therefore, evidence that the formation of these molecules is rather driven by kinetics."
 }
]
```
