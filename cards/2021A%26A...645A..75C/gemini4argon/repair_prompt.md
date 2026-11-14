# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...645A..75C\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
A&A 645, A75 (2021)
[https://doi.org/10.1051/0004-6361/202039924](https://doi.org/10.1051/0004-6361/202039924)
© ESO 2021


# **Astronom** **y**
### &
# **Astrophysics**


## **Comprehensive rotational study and astronomical search** for cyclopropanecarboxaldehyde [⋆]

C. Cabezas [1], E. M. Neeman [2], B. Tercero [3,4], C. Bermúdez [1], and J. Cernicharo [1]


1 Instituto de Física Fundamental (IFF-CSIC), Group of Molecular Astrophysics, C/ Serrano 121, 28006 Madrid, Spain
e-mail: `[carlos.cabezas@csic.es](mailto:carlos.cabezas@csic.es)`
2 Departamento de Química Física, Facultad de Ciencias y Tecnologías Químicas, Universidad de Castilla-La Mancha Avda,
Camilo José Cela 1B. 13071, Ciudad Real, Spain
3 Observatorio de Yebes (IGN), Cerro de la Palera s/n, 19141 Yebes, Guadalajara, Spain
4 Observatorio Astronómico Nacional (OAN-IGN), C/ Alfonso XII 3, 28014 Madrid, Spain


Received 17 November 2020 / Accepted 2 December 2020


**ABSTRACT**


_Context._ At least a dozen molecules with a formyl group (HCO) have been observed to date in the interstellar medium (ISM), suggesting that other such species exist and remain to be discovered. However, there is still a lack of high-resolution spectroscopic data for
simple molecular species of this type that could provide a basis for their detection.
_Aims._ Cyclopropanecarboxaldehyde, c-C 3 H 5 CHO, is a small molecule containing a formyl group and is therefore an interesting candidate for astrophysical detection. The rotational spectrum of cyclopropanecarboxaldehyde has been observed before, but its experimental
rotational parameters are not precise enough to allow its detection in the millimetre-wave domain.
_Methods._ We measured the rotational spectrum of cyclopropanecarboxaldehyde in the frequency ranges 31.5–50 GHz and 72–
116.5 GHz using the GACELA (GAS CEll for Laboratory Astrophysics) broadband high-resolution rotational spectrometer constructed
at the Yebes Observatory. The spectroscopic study was supported by high-level theoretical calculations which were used in the identification of the vibrational excited states of cyclopropanecarboxaldehyde.
_Results._ Our analysis of the rotational spectrum of cyclopropanecarboxaldehyde allowed us to obtain accurate rotational parameters
for the ground state of both cis and trans isomers, which were used to derive sufficiently reliable predictions up to 300 GHz. In addition
to the ground states, we identified 12 and 6 vibrationally excited states for the trans and cis isomers, respectively, including fundamental modes, multiple excitation quanta, and combination states. We find that the gas phase concentration of the trans isomer is almost
1.2 times larger than that of the cis one. These new experimental rotational parameters were employed to search for cyclopropanecarboxaldehyde in the warm molecular clouds Orion KL and Sgr B2(N) using the spectral surveys captured by ALMA (Orion) and IRAM
30 m (Sgr) at 1 and 3 mm, respectively.


**Key words.** ISM: molecules – methods: laboratory: molecular – molecular data – line: identification



**1. Introduction**


Among the more than 200 molecular species detected so far in
the interstellar medium (ISM) or circumstellar shells [1], 12 species
share a common structural unit, the formyl moiety, HCO. This
group of molecules contains seven aldehydes (-CHO), the simplest carboxylic acid, formic acid (HOCHO; Zuckerman et al.
1971), two amides (-NCHO), formamide (Rubin et al. 1971) and
N-methyl formamide (Belloche et al. 2019), and two formates
(-OCHO), methyl formate (Brown et al. 1975) and ethyl formate (Belloche et al. 2009; Tercero et al. 2013). The interstellar
aldehydes discovered so far are formaldehyde (HCHO; Snyder
et al. 1969), acetaldehyde (CH 3 CHO; Gottlieb et al. 1973),
cyanoformaldehyde (NCCHO; Remijan et al. 2008), propynal
(HC 2 CHO; Irvine et al. 1988), propenal (H 2 CHCHO; Hollis
et al. 2004), propanal (CH 3 CH 2 CHO; Hollis et al. 2004), and


⋆ Data are only available at the CDS via anonymous ftp to
`[cdsarc.u-strasbg.fr](http://cdsarc.u-strasbg.fr)` ( `[130.79.128.5](ftp://130.79.128.5)` ) or via `[http://cdsarc.](http://cdsarc.u-strasbg.fr/viz-bin/cat/J/A+A/645/A75)`
```
u-strasbg.fr/viz-bin/cat/J/A+A/645/A75
```

1 CDMS 2020, The Cologne Database for Molecular Spectroscopy:
Molecules in the Interstellar Medium or Circumstellar Shells
(as of 08/2020), `[https://cdms.astro.uni-koeln.de/classic/](https://cdms.astro.uni-koeln.de/classic/molecules)`
```
molecules

```


glycolaldehyde (HOCH 2 CHO; Hollis et al. 2000). The relative
abundances of some aldehydes are not accurately reproduced
by current theoretical chemistry models, and so there are no
accepted formation routes in interstellar environments for these
molecules. It is therefore not straightforward to make predictions as to which yet-undiscovered species could be abundant in
the interstellar medium (ISM). However, given the many HCOcontaining molecules detected in space, it is fair to anticipate that
others of this type could be present as well.
Five of the seven aldehydes detected in the ISM are alkyl
derivatives of the simplest aldehyde, formaldehyde. Hence, one
candidate yet to be observed consists of an aldehyde containing
a cyclic functional group, either an aliphatic or aromatic ring.
While the astrochemical literature on aromatic rings is extensive,
less information is available related to aliphatic rings. Cyclopropane, c-C 3 H 6, is the smallest saturated carbon ring; it lacks
a dipole moment and therefore cannot be detected by its rotational spectrum. This is not the case with its derived aldehyde,
cyclopropanecarboxyaldehyde (c-C 3 H 5 CHO, CPCA hereinafter)
which is a good candidate for observation by way of its rotational
spectrum. The microwave spectrum of CPCA was observed
by Volltrauer & Schwendeman (1971) in the centimeter wave
range up to 32 GHz and two different isomers, cis and trans



[Article published by EDP Sciences](http://www.edpsciences.org) A75, page 1 of 8

A&A 645, A75 (2021)


**Table** **1.** Calculated relative energies (in cm [−][1] ) for the cis and trans
isomers of CPCA at different levels of theory.


Level of theory ∆ _E_ cis [(] _[a]_ [)] ∆ _E_ trans [(] _[a]_ [)]


B3LYP/6-311++G(d,p) 80.7 0.0
B3LYP/cc-pVTZ 12.5 0.0
B3LYP/aug-cc-pVTZ 99.7 0.0
B97D/6-311++G(d,p) 107.9 0.0
B97D/cc-pVTZ 45.6 0.0
B97D/aug-cc-pVTZ 128.0 0.0
MP2/6-311++G(d,p) 0.0 84.7
MP2/cc-pVTZ 0.0 131.7
MP2/aug-cc-pVTZ 0.0 69.2
CCSD/6-311++G(d,p) 0.0 21.6
CCSD/cc-pVTZ 0.0 52.1
CCSD/aug-cc-pVTZ 0.0 6.8


**Notes.** [(] _[a]_ [)] Relative energy to that of the most stable isomer.



**[Fig. 1.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/202039924&pdf_id=0)** Molecular structures and principal inertial axes for the trans and
cis conformers of CPCA.


(see Fig. 1), were identified. These measurements included rotational transitions with _J_ ≤ 10 and _K_ a ≤ 2 and only the rotational
constants were determined with large uncertainties. The astronomical search for CPCA at the observational frequency ranges
of sensitive radio telescopes becomes difficult using the predictions obtained with these rotational parameters. A more accurate
spectral modelling of CPCA with measurements extending into
the millimetre-wave region therefore constitutes the first scenario
for a robust astronomical detection.
In addition, CPCA was investigated by infrared (IR) and
Raman spectroscopy (Durig & Little 1988; Durig et al. 1992;
Durig & Shen 2000; Hudson & Coleman 2019) and electron
diffraction (Bartell & Guillory 1965). In these works the abundance ratios for both cis and trans isomers were derived and it
was found that the cis isomer is more stable in the gas phase
while the trans is the only species present in liquid phase, which
is in contrast with the rotational spectroscopy study, where the
trans species were found to be the most abundant one (Volltrauer
& Schwendeman 1971). Quantum chemical calculations (De
Mare & Peterson 1983; Durig & Shen 2000) point out some
uncertainties in terms of the relative stability of CPCA isomers
due to the relative energies of cis and trans species which fluctuate with the calculation method employed. This raises important
questions as to the relative abundances of CPCA isomers in the
gas phase, which have considerable astrochemical implications.
In this work, we report new rotational spectroscopy measurements for CPCA in the 31.5–50 GHz and 72–116.5 GHz
frequency ranges using a high-resolution broadband millimetrewave spectrometer. The first aim of this investigation is to
contribute to the astronomical search for CPCA by providing a
better spectral modelling of CPCA isomers, extending the measurements into the millimetre-wave region. This comprehensive
study involves the analysis of the rotational spectra in the lowlying vibrational states of CPCA isomers, motivated by the fact
that these are found to be considerably populated in the warm
environments of the ISM. The analysis of our new data allowed
us to very accurately determine the rotational parameters needed
to provide reliable predictions to support astronomical observations of CPCA in the warm molecular clouds Orion KL and
Sgr B2(N) using the spectral surveys captured by ALMA (Orion)
and IRAM 30 m (Sgr) at 1 and 3 mm, respectively. Secondly,


A75, page 2 of 8



this work is also devoted to obtaining insights into the relative
stabilities of cis and trans CPCA isomers. To this end, we directly
measured the abundance ratio of CPCA isomers in order to
ascertain which of the two species, cis or trans, is energetically
favoured in the gas phase, and we provide new high-level quantum chemical calculations to predict the theoretical stabilities.


**2. Quantum chemical calculations**


Existing quantum chemical calculations available in the literature include very cheap Hartree Fock (HF; Hartree 1928)
methods, small basis sets (Durig et al. 1992), and Møller-Plesset
perturbation theory calculations (MP2; Møller & Plesset 1934)
combined with Pople’s basis sets (Frisch et al. 1984), with
MP2/6-311++G(d,p) being the highest level of theory employed
(Durig & Shen 2000). In order to evaluate the conformational
stability of the CPCA isomers, we extended the quantum chemical calculations using two density-functional theory methods,
namely Becke 3-parameter Lee-Yang-Parr (B3LYP; Lee et al.
1988) and Grimme’s functional including dispersion (B97D;
Grimme 2006), and two post-Hartree Fock methods, namely
MP2 and coupled-cluster with single and double excitations
(CCSD; Cížek 1969). We combine all these methods with the
6-311++G(d,p) Pople’s basis set (Frisch et al. 1984) and the
Dunning’s basis set cc-pVTZ (Dunning 1989) and aug-cc-pVTZ
(Woon & Dunning 1995). In addition to the structural optimisation calculations, we carried out harmonic and anharmonic
frequency calculations in order to estimate the energy and the
rotational constants of the individual vibrationally excited states,
facilitating the assignment of the experimental spectrum. These
calculations were carried out at the MP2/6-311++G(d,p) level
of theory because this method reproduce the experimental rotational constants very well (see below). The energy calculations
for the cis and trans isomers at different levels of theory are
shown in Table 1 while a complete list of the vibrational frequencies is given in Table 2. All calculations were carried out
using the Gaussian16 (Frisch et al. 2016) program package.
We compared the theoretical constants obtained for each of
the levels of theory employed to those determined experimentally in this work. In general, all the methods nicely reproduce
the rotational constants for both isomers, with the MP2/6311++G(d,p) level of theory providing the best agreement with
the experiment. The discrepancies for this method are 0.14

C. Cabezas et al.: CPCA



**Table** **2.** The MP2/6-311++G(d,p) anharmonic vibrational frequencies
(in cm [−][1] ) of cis and trans isomers of CPCA.


Mode Symmetry cis trans


1 _A_ [′] 3151.20 3145.01

2 _A_ [′] 3093.76 3099.70

3 _A_ [′] 3063.01 3064.97

4 _A_ [′] 2760.82 2761.57

5 _A_ [′] 1713.99 1726.74

6 _A_ [′] 1468.38 1472.44

7 _A_ [′] 1405.60 1409.03

8 _A_ [′] 1372.12 1328.22

9 _A_ [′] 1206.92 1205.11

10 _A_ [′] 1110.92 1188.50

11 _A_ [′] 1060.63 1050.07

12 _A_ [′] 975.63 937.64

13 _A_ [′] 845.99 884.08

14 _A_ [′] 789.91 781.27

15 _A_ [′] 670.71 503.01

16 _A_ [′] 261.17 291.83

17 _A_ [′′] 3137.81 3131.83

18 _A_ [′′] 3063.79 3063.40

19 _A_ [′′] 1437.12 1448.33

20 _A_ [′′] 1197.58 1189.28

21 _A_ [′′] 1092.27 1107.45

22 _A_ [′′] 1072.78 1063.72

23 _A_ [′′] 1024.21 1016.76

24 _A_ [′′] 818.36 845.64

25 _A_ [′′] 817.48 828.91

26 _A_ [′′] 305.46 339.88

27 _A_ [′′] 123.01 126.92


and 0.28% for cis and trans isomers, respectively, taking into
account the sum of the relative errors for _A_, _B_, and _C_ constants.
B3LYP/cc-pVTZ, with relative errors of 0.21 and 0.32% for cis
and trans, respectively, and CCSD/cc-pVTZ, 0.42 and 0.40%,
provide good results as well. The least satisfactory results were
found for B97D methods, with relative discrepancies larger than
1.5%.


**3. Experimental setup**


The emission rotational spectrum of CPCA was recorded using
the GACELA (GAS CEll for Laboratory Astrophysics) broadband high-resolution rotational spectrometer constructed at
the Yebes Observatory (Spanish National Geographic Institute
(IGN)) in the frame of the ERC synergy project Nanocosmos.
The GACELA spectrometer is equipped with radio receivers
similar to those used in radio astronomy to search for molecular emission in space. The receivers are equipped with
16 × 2.5 GHz FFT spectrometers with a spectral resolution of
38.14 kHz allowing the observation of the rotational transitions
in the _Q_ (31.5–50 GHz) and _W_ bands (72–116.5 GHz). The spectrometer performance has been described at length in previous
works (Tanarro et al. 2018; Cernicharo et al. 2019; Cabezas et al.
2019, 2020a,b).
The CPCA sample (purity >98%), purchased from Apollo
Scientific, was placed into a Pyrex [TM] vacuum Schlenk which
was connected directly to the cell of the spectrometer. This
latter consists of a stainless steel cylinder of 890 mm length
and 490 mm diameter. In order to avoid sample condensation



during the experiment, which was carried out in continuous flow
mode, the temperature of the sample container, the injection line,
and the cell were kept at 350 K using a dry heating tape and
a proportional integral derivative (PID) temperature controller.
Prior to introduction of the sample, the pressure inside the vacuum chamber was 2.0 × 10 [−][4] mbar and during the experiment
the pressure was kept at 6.0 × 10 [−][3] mbar because higher pressures produce undesirable line broadenings. With the selected
working pressure, the rotational lines of CPCA have a HWHM
of 0.2−0.35 MHz which is well adapted to measuring frequencies with high accuracy. The total observing time to obtain the
whole CPCA spectrum in the _Q_ (31.5–50 GHz) and _W_ bands
(72–116.5 GHz) was six days. In all these experiments, a frequency switching with a throw of 50 MHz was selected as the
observing procedure. This has previously been confirmed as the
most suitable mode, as the lines are observed twice and the noise
is improved by a factor √2, allowing us to derive accurate line

profiles and intensities for lines of up to 2 MHz full width at half
maximum (Cernicharo et al. 2019). With this observing procedure the baseline shows several ripples which can be easily eliminated by applying a FFT filter and removing the corresponding
time domain, or by a polynomial baseline removal.


**4. Rotational spectrum and analysis**


The two CPCA isomers are near symmetric tops with moderate
dipole moments that have been experimentally determined by
Volltrauer & Schwendeman (1971). For the trans isomer, |µ _a_ | and
|µ _c_ | were found to be 3.221 D and 0.493 D, respectively, while the
dipole moment components for the cis species are |µ _a_ | = 2.019 D
and |µ _b_ | = 1.856 D. A very rich rotational spectrum is therefore
observed for CPCA, which is governed by strong _a_ -type rotational transitions for the trans isomer. Figure 2 shows the typical
pattern of _a_ -type _R_ -branch rotational transitions for the ground
state of the trans isomer together with weaker _b_ -type _Q_ -branch
rotational transitions for the ground state of the cis isomer. For
the trans isomer, we measured a total of 208 _a_ -type _R_ -branch
transitions with maximum values of _J_ and _K_ a quantum numbers
of 18 and 17, respectively, which were fitted using the SPFIT
(Pickett 1991) program with the _S_ -reduction of the Watson’s
Hamiltonian in _I_ _[r]_ representation (Watson 1977). A list of all the
measured transitions is available at CDS. In spite of the fact that
the trans isomer also presents a _c_ -type dipole moment different
from zero, no _c_ -type rotational transitions could be measured
in our spectrum. This can be explained taking into account the
fact that the intensity of the rotational transitions is proportional
to the square of the dipole moment components, and therefore
_c_ -type transitions for the trans species are expected to be about
43 times weaker than the _a_ -type ones. The fit for the trans isomer
provided a set of experimental constants, including rotational
constants, and four quartic and two sextic centrifugal distortion
constants, which are listed in the first column of Table 3.
For the cis isomer, we first measured _a_ -type _R_ -branch transitions and the initial fit of these lines provided a set of refined
experimental constants, which were used for new spectral predictions that in turn allowed the identification of _b_ -type _R_ - and
_Q_ -branch transitions. The best fit for all these lines was obtained
using the _S_ -reduction of Watson’s Hamiltonian in _III_ _[r]_ representation (Watson 1977). This fit was done using the Kisiel’s ASFIT
program (Kisiel & Bialkowska-Jaworska 2019) which is best
suited when the _S_ -reduction in _III_ _[r]_ representation is required.
A total of 819 rotational transitions with maximum values of
_J_ and _K_ a quantum numbers of 79 and 21, respectively, were
assigned for the ground vibrational state of the cis isomer. A list


A75, page 3 of 8

A&A 645, A75 (2021)



17 12 8 7 6 5 4 3 3



_K_ _a_



_Trans_ G.S.

−
_J_ =18 17















_K_ _a_







**112200** **112400** **112600**


Frequency /MHz



**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/202039924&pdf_id=0)** **2.** Section of the rotational spectrum of CPCA
showing _a_ -type _R_ -branch rotational transitions for the
ground state, and ν 27 and ν 16 vibrationally excited states
of the trans conformer, and _b_ -type _Q_ -branch transitions
for the ground state of the cis species. The negative
spectral features are produced by the folding of the
frequency-switched data and appear at ±50 MHz of each
rotational transition.



of all the measured transitions is available at CDS. The analysis
provided a list of experimental constants, shown in Table 4,
which includes the rotational constants, and all the quartic and
six sextic centrifugal distortion constants.
The spectrum in Fig. 2 shows that each ground-state line of
CPCA was accompanied by many satellite lines attributable to
rotational transitions in vibrationally excited states, as no other
coupling interaction is expected for this closed-shell molecule.
As can be seen in Table 2, four vibrational modes are predicted
below 500 cm [−][1], which originate many low-energy vibrationally
excited states from overtones and combination states. For the
assignment of these satellite lines, the rotational spectra of the
lower-energy excited states were modelled on the basis of calculated first-order vibration–rotation constants α _i_ that define the
vibrational dependence of rotational constants _B_ ν = _B_ e - [�] _i_ [α] _i_
(ν _i_ + 1/2), where _B_ ν and _B_ e substitute all three rotational constants in a given excited state and in equilibrium, respectively,
and ν _i_ is the vibrational quantum number. The calculations were
carried out with the Gaussian16 program package at the MP2/6311++G(d,p) level of theory. Our frequency calculations are in
agreement with those reported before and with the experimental vibrational assignments (Durig & Little 1988; Durig et al.
1992; Durig & Shen 2000) which point out that the lowest
energy vibrational modes are ν 27, ν 16, ν 26 and ν 15 . These four
modes correspond to the asymmetric torsion, the ring CHO inplane bend, the ring CHO bend, and the CCO bend, respectively.
According to this, we searched for the rotational transitions
coming from these modes and were able to identify up to 12
and 6 vibrationally excited states for the trans and cis isomers,
respectively.
For the trans isomer, in addition to the three fundamental
modes ν 27, ν 16, and ν 26, we identified, between the 12 states,
the second quanta of ν 27, ν 16, and ν 26 (2ν 27, 2ν 16 and 2ν 26 ),
and the third quanta of ν 27 (3ν 27 ), together with some combination states, namely ν 27 +ν 16, ν 27 +ν 26, 2ν 27 +ν 16, 2ν 27 +ν 26, and
3ν 27 +ν 16 . We note the non-detection of ν 15 in spite of it being
predicted to lie below other identified modes, such as 2ν 16 .


A75, page 4 of 8



We scrutinised the rotational spectrum searching for transitions
attributable to ν 15 but all attempts were fruitless. All the measured rotational transitions for the vibrationally excited states of
the trans isomer available at the CDS were analysed using the
SPFIT program (Pickett 1991) in the same manner as that used
for the ground state, and the derived spectroscopic constants are
shown in Table 3. As for the trans ground state, four quartic
and two sextic centrifugal distortion constants were determined
for all the vibrationally excited states except for 2ν 27 +ν 26, with
Φ _JK_ fixed to the ground state value, and 3ν 27, whose transitions
were very weak and for which only a few parameters could be
determined.
The six vibrationally excited states identified for the cis isomer arise from the three lowest energy modes ν 27, ν 16, and ν 26 .
These three fundamental modes were observed together with the
second and third quanta of ν 27, 2ν 27, and 3ν 27, and the combination state ν 27 +ν 16 . The analysis of the rotational lines for all
these states was carried out in the same manner as that for the cis
ground state, and the spectroscopic constants obtained are collected in Table 4. For ν 27, the rotational parameters included the
rotational constants and all the centrifugal distortion constants
derived for the ground state of the cis isomer, except the _h_ 2 constant. For the other five vibrationally excited states, in addition
to the rotational constants, only the quartic centrifugal distortion
constants could be fitted.
As shown before by Cernicharo et al. (2019), our GACELA
spectrometer allows us to determine the concentrations of the
different molecular species from the observed line intensities
with high accuracy; these concentrations are proportional to the
line strength, the partition function, the square of a corresponding component of the electric dipole moment, and the molecular
concentration. Therefore, the abundance of each CPCA isomer
in the gas phase can be directly determined by relative intensity measurements of their ground-state rotational transitions.
In these measurements, we compared the intensities of tens of
_a_ -type rotational transitions and we find that the transitions for
the trans isomer are 1.1985(37) times more intense than those

C. Cabezas et al.: CPCA


**Table 3.** Spectroscopic constants for the ground- and vibrationally excited states of the trans conformer of CPCA.


Constants/units Ground state ν 27 2ν 27 ν 16 ν 26 3ν 27 ν 27 + ν 16


_A_ /MHz 15 885.549(45) 15 778.423(62) 15 676.048(88) 15 980.713(47) 15 888.49(11) 15 577.886(79) 15 863.51(13)
_B_ /MHz 3195.10235(26) 3207.76840(41) 3219.76650(60) 3192.87144(33) 3190.93426(74) 3231.18571(60) 3206.19178(89)
_C_ /MHz 3040.93992(25) 3045.99119(36) 3050.78930(64) 3038.13243(28) 3035.87075(64) 3055.33570(58) 3042.89403(84)
_D_ _J_ /kHz 0.50922(15) 0.53049(23) 0.55487(22) 0.50253(23) 0.50187(43) 0.57944(35) 0.51843(52)
_D_ _JK_ /kHz 12.5700(11) 11.7320(14) 10.8774(22) 12.8823(25) 12.7997(39) 10.0613(28) 12.1590(50)
_d_ 1 /kHz −0.019406(24) −0.02509(36) −0.03146(60) −0.01630(28) −0.02138(65) −0.03913(55) −0.01959(80)
_d_ 2 /kHz −0.00581(13) −0.00620(16) −0.00731(17) −0.00608(10) −0.00535(19) −0.00867(20) −0.00648(30)
_H_ _JK_ /Hz 0.0837(24) 0.0537(30) 0.0523(44) 0.0600(50) 0.0802(79) 0.0495(57) 0.061(10)
_H_ _KJ_ /Hz −0.8448(33) −0.7034(44) −0.6184(55) −0.8395(65) −0.940(12) −0.566(10) −0.695(22)

σ rms /kHz 9.65 9.32 8.79 9.53 11.57 9.21 13.15

_N_ lines 208 196 164 142 150 168 138

_J_ min / _J_ max 5/18 11/18 10/18 11/18 11/18 11/18 11/18
_K_ _a_,min / _K_ _a_,max 0/17 0/17 0/16 0/16 0/16 0/15 0/14


Constants/units ν 27 + ν 26 2ν 27 + ν 16 2ν 16 2ν 27 + ν 26 2ν 26 3ν 27 + ν 16


_A_ /MHz 15 790.59(11) 15 753.84(17) 16 075.714(99) 15 692.61(17) 15 882.6(12) 15 597.86(27)
_B_ /MHz 3203.52896(82) 3218.6359(13) 3190.77722(98) 3216.0069(13) 3187.4267(38) 3227.8800(22)
_C_ /MHz 3041.59709(72) 3047.2257(13) 3035.57590(53) 3047.2385(12) 3031.3270(26) 3052.7581(19)
_D_ _J_ /kHz 0.52627(48) 0.54322(69) 0.49676(71) 0.55387(60) 0.4397(58) 0.5668(15)
_D_ _JK_ /kHz 11.8662(50) 11.4110(67) 13.2328(77) 10.8954(44) 13.4(24) 9.840(21)
_d_ 1 /kHz −0.02846(74) −0.0248(12) −0.01287(67) −0.0375(12) −0.0505(30) −0.0410(19)
_d_ 2 /kHz −0.00606(41) −0.00787(41) −0.00630(39) −0.00685(44) −0.00535 [(] _[b]_ [)] −0.00938(72)
_H_ _JK_ /Hz 0.063(10) 0.079(13) 0.075(15) 0.0837 [(] _[a]_ [)] 0.0802 [(] _[b]_ [)] 0.115(43)
_H_ _KJ_ /Hz −0.749(19) −0.691(25) −0.628(37) −0.629(31) −0.940 [(] _[b]_ [)] −0.73(16)

σ rms /kHz 11.41 15.39 15.61 20.98 27.20 25.30

_N_ lines 141 134 104 130 18 76

_J_ min / _J_ max 11/18 11/18 11/18 11/18 11/18 11/18
_K_ _a_,min / _K_ _a_,max 0/13 0/13 0/12 0/14 0/1 0/10


**Notes.** Numbers in parentheses represent the derived uncertainty (1 σ) of the parameter in units of the last digit. [(] _[a]_ [)] Fixed to the ground-state value.
( _b_ ) Fixed to the ν 26 state value.


**Table 4.** Spectroscopic constants for the ground and vibrationally excited states of cis conformer of CPCA.


Constants/units Ground state ν 27 2ν 27 ν 16 ν 26 3ν 27 ν 27 + ν 16


_A_ /MHz 11 417.32304(39) 11 454.85634(69) 11485.3120(23) 11 444.8779(39) 11 452.2176(21) 11 522.0344(19) 11 482.1682(18)
_B_ /MHz 3994.186538(85) 3967.16406(24) 3950.3361(12) 3975.58760(64) 3981.7448(15) 3928.67737(90) 3945.6599(11)
_C_ /MHz 3849.930881(87) 3842.87981(23) 3836.8000(11) 3837.08702(58) 3844.5882(12) 3830.59473(82) 3829.9139(11)
_D_ _J_ /kHz 3.7355(11) 4.0405(17) 4.4152(67) 4.065(12) 3.8166(58) 4.4654(51) 4.2188(52)
_D_ _JK_ /kHz 1.24912(24) 0.89498(43) 0.5717(10) 1.347(14) 1.16303(84) 0.5214(16) 0.7408(40)
_D_ _K_ /kHz −3.30818(76) −3.2752(17) −3.3254(54) −3.784(17) −3.3080(36) −3.3402(44) −3.3230(55)
_d_ 1 /kHz −1.33950(88) −1.4677(18) −1.7152(58) −1.792(12) −1.4089(39) −1.7766(45) −1.5892(41)
_d_ 2 /kHz −0.76937(41) −0.74076(90) −0.9201(29) −0.9135(59) −0.7784(20) −0.9256(22) −0.6459(20)

_H_ _J_ /Hz 0.00713(92) −0.02318(33)

_H_ _JK_ /Hz −0.013204(89) −0.00749(10)
_H_ _KJ_ /Hz 0.02195(73) 0.03481(14)
_H_ _K_ /Hz −0.016015(15) −0.01646(14)
_h_ 1 /Hz 0.01140(81) −0.005664(36)

_h_ 2 /Hz 0.00796(40)

σ rms /kHz 37.90 32.22 47.51 46.23 39.54 47.07 49.05

_N_ lines 819 471 230 157 252 315 241

_J_ min / _J_ max 3/76 3/69 7/52 9/62 8/50 7/62 9/53
_K_ _a_,min / _K_ _a_,max 0/21 0/13 0/13 0/10 0/11 0/14 0/13


**Notes.** Numbers in parentheses represent the derived uncertainty (1 σ) of the parameter in units of the last digit.



for the cis isomer. Assuming a temperature for our experiment
of 350K, this implies an energy difference between both isomers



of 44.05(75) cm [−][1], with the trans species being the most stable. This result can be compared to those previously reported


A75, page 5 of 8

A&A 645, A75 (2021)


**Table 5.** Rotational, vibrational, and conformational partition functions for both cis and trans isomers of CPCA at different temperatures.


Temperature/K _Q_ r (c) [(] _[a]_ [,] _[b]_ [)] _Q_ r (t) _Q_ v (c) _Q_ v (t) _Q_ c _X_ (t/c)


350.000 82 331.3 86 128.5 7.3 6.8 0.83 1.83

300.000 65 822.4 69 359.9 4.8 4.5 0.81 1.81

225.000 42 979.0 45 656.3 2.8 2.6 0.75 1.75

150.000 23 411.5 24 951.4 1.7 1.6 0.66 1.66

75.000 8275.4 8823.1 1.1 1.1 0.43 1.43

37.500 2927.1 3120.7 1.0 1.0 0.18 1.18

18.750 1036.3 1104.6 1.0 1.0 0.03 1.03

9.375 367.5 391.5 1.0 1.0 0.00 1.00


**Notes.** ( _a_ ) _Q_ r, _Q_ v, and _Q_ c are the rotational, vibrational, and conformational partition functions, respectively. _X_ (t/c) is the trans/cis isomer ratio at
different temperatures. [(] _[b]_ [)] c and t refer to cis and trans isomers, respectively.



for the relative stability of CPCA isomers, which seem fairly
ambiguous. Durig & Little (1988), Durig et al. (1992) and Bartell
& Guillory (1965) in their respective experiments found that
the cis isomer was the most stable species in the gas phase,
with an energy difference of around 40–60 cm [−][1], while Hudson
& Coleman (2019) showed that the cis/trans ratio was 1:1. On
the other hand, Volltrauer & Schwendeman (1971) proposed
that in the gas phase the trans species was slightly more stable
(10 ± 20 cm [−][1] ) than the cis one, but with large uncertainties. In
liquid phase, the panorama is completely distinct because the
trans isomer was found by Durig & Little (1988) to be the only
species present, with an energy gap of 405 cm [−][1] over the cis
isomer. In addition, large discrepancies are encountered when
quantum chemical calculations at different levels of theory are
used to evaluate the isomer energies. De Mare & Peterson (1983)
and Durig & Shen (2000) used HF and MP2 methods combined with modest basis sets and their results indicated that the
cis species was the most stable. We carried out additional calculations at different levels of theory and the results, collected
in Table 1, show discrepancies as well. Density functional levels of theory, B3LYP and B97D, predict the trans isomer to
be more stable than the cis isomer with relative energies of
between 12 and 128 cm [−][1] . In contrast, more sophisticated calculation methods, such as MP2 and CCSD, provide totally different
results, with the cis isomer being found to be the most stable.
In this case, the relative energies also oscillate between 7 and
132 cm [−][1] . In light of this, we can conclude that the small energy
difference between cis and trans isomers makes experimental
determination of the isomer energies more difficult. However,
we find that the trans isomer is moderately more stable than
the cis one and therefore both species should be taken into
consideration for astronomical implications. Secondly, the use
of quantum chemical calculations to estimate the relative energies of CPCA isomers should be handled with caution because
these relative energies are near to the level of accuracy of the
calculations.
We used the rotational parameters obtained in this work for
both cis and trans isomers of CPCA to obtain accurate frequency predictions up to 300 GHz, providing a means for their
astronomical detection. These frequency predictions for both
CPCA isomers, calculated at _T_ = 300 K, are provided at the
CDS. The rotational and vibrational partition functions used in
these predictions, at different temperatures, are listed in Table 5.
The rotational partition function was calculated considering a
maximum value of _J_ = 90, while the vibrational partition function was calculated using the method described by Gordy &
Cook (1984) and the anharmonic frequencies from Table 2.


A75, page 6 of 8



The conformational partition function and the conformational
abundances were calculated using the energy difference between
isomers determined in this work.


**5. Search for cyclopropanecarboxaldehyde in**

**space**


Thanks to the improved frequency predictions provided by the
present work, we were able to carry out a rigorous search
for trans and cis isomers of CPCA in space. For this search,
we rely on our line surveys and public data towards different
astronomical sources at frequencies above 80 GHz (Cernicharo
et al. 2012; Belloche et al. 2013; Tercero et al. 2018, 2015). For
these frequencies, the energies of the rotational levels of the
CPCA _a_ -type transitions are above 30 K, preventing the detection of CPCA in our IRAM 30 m data of cold clouds at 3 mm
(Cernicharo et al. 2012). Therefore, we focused the search on
high-mass star-forming regions which show high abundances of
acetaldehyde (CH 3 CHO) such as Orion KL and Sgr B2 (see,
e.g. Belloche et al. 2013; Cernicharo et al. 2016). We used the
MADEX code (Cernicharo 2012) to exploit the spectroscopic
parameters presented in this work and to derive the synthetic
spectrum of this species (assuming local thermodynamic equilibrium) according to the physical parameters of the sources (see
below) collected in Table 6. The column density was the only
free parameter for these models. Corrections for beam dilution
were applied to each line depending on its frequency.


_Orion_ _KL._ Science Verification (SV) data from the Atacama Large millimetre/submillimetre Array (ALMA) interferometer towards Orion KL (Tercero et al. 2015, 2018) were
explored to search for CPCA. The ALMA SV data allow us to
obtain the spectrum between 213.7 and 246.7 GHz for different
positions within the source characterised by different chemistry
and physical parameters. We distinguished three positions, two
of them presenting high abundances of CH 3 CHO, namely the
south hot core and the MM4 source (Cernicharo et al. 2016). The
other location is the compact ridge which shows emission peaks
of several complex O-bearing species such as methyl formate,
dimethyl ether, and methyl acetate (Favre et al. 2011; Brouillet
et al. 2013; Tercero et al. 2018). To model the CPCA emission
in these components, we adopted physical parameters according to those derived by Cernicharo et al. (2016) and Tercero
et al. (2018). Figure 3 shows selected frequencies and positions
within these data together with the model derived by MADEX
that demonstrates the lack of CPCA lines above the confusion

limit of the data.

C. Cabezas et al.: CPCA


**Table 6.** Physical parameters of the considered cloud cores.


Source Coordinates _HPBW_ [(] _[a]_ [)] Frequencies [(] _[b]_ [)] v LSR [(] _[c]_ [)] ∆v FWHM [(] _[d]_ [)] _d_ sou [(] _[e]_ [)] _T_ rot [(] _[f]_ [)] _N_ (trans) [(][g][)] _N_ (cis) [(] _[h]_ [)]

(J2000.0) ( [′′] ) (GHz) (km s [−][1] ) (km s [−][1] ) ( [′′] ) (K) ×10 [14] (cm [−][2] ) ×10 [14] (cm [−][2] )


Orion KL
α = 05 [h] 35 [m] 14.5 [s]
(ALMA SV) ∼1.9 × 1.4 213.7–246.7 8.0 3.0 3 150 ≤(2.5 ± 1.2) ≤(6.0 ± 3.0)
δ = −05 [◦] 22 [′] 32.5 [′′]
Hot core


Orion KL
α = 05 [h] 35 [m] 14.1 [s]
(ALMA SV) ∼1.9 × 1.4 213.7–246.7 7.5 2.0 3 150 ≤(2.0 ± 1.0) ≤(5.0 ± 2.5)
δ = −05 [◦] 22 [′] 36.9 [′′]
Compact ridge


Orion KL
α = 05 [h] 35 [m] 14.2 [s]
(ALMA SV) ∼1.9 × 1.4 213.7–246.7 5.0 3.0 3 150 ≤(2.0 ± 1.0) ≤(5.0 ± 2.5)
δ = −05 [◦] 22 [′] 31.1 [′′]
MM4



Sgr B2(N)



(IRAM 30m)
α = 17 [h] 47 [m] 20.0 [s] 30–21 80–115.5


δ = −28 [◦] 22 [′] 19.0 [′′] 63 8.0 3 100 ≤(100 ± 50) ≤(200 ± 100)

(GBT 100m) 73 8.0 3 100 ≤(100 ± 50) ≤(200 ± 100)
α = 17 [h] 47 [m] 19.8 [s] 80–15 7–50



δ = −28 [◦] 22 [′] 17.0 [′′]


**Notes.** [(] _[a]_ [)] HPBW for observations with single dish telescope (IRAM 30 m and GBT 100 m) and synthetic beam for the ALMA SV observations.
( _b_ ) Range of frequencies considered in the analysis. ( _c_ ) Radial velocity with respect the Local Standard of Rest. ( _d_ ) FWHM. ( _e_ ) Source diameter assuming
a uniform disc-type model. [(] _[f]_ [)] Rotational temperature. [(][g][)] Column density for trans isomer of CPCA in the ground state. [(] _[h]_ [)] Column density for cis
isomer of CPCA in the ground state.



**Table 7.** Column density ratios.


Source _N_ (CH 3 CHO) _N_ (CH 3 CHO)/
(cm [−][2] ) _N_ (CPCA) [(] _[a]_ [)]


Orion KL (HC) 1.6 × 10 [15] [(] _[b]_ [)] ≥2
Orion KL (MM4) 1.4 × 10 [15] [(] _[b]_ [)] ≥2
Sgr B2 [(] _[c]_ [)] 2.2 × 10 [17] [(] _[d]_ [)] ≥4


**Notes.** ( _a_ ) trans+cis. ( _b_ ) Cernicharo et al. (2016). ( _c_ ) Sum of the different
spectral components. [(] _[d]_ [)] Belloche et al. (2013).


_Sgr_ _B2._ we also searched for CPCA in public data available for Sgr B2. We did not find this species above the detection
limit of the data either in the PRIMOS survey [2] (Neill et al. 2012)
or in the IRAM 30m data at 3 mm provided by Belloche et al.
(2013). To estimate upper limits to the CPCA column density
in the region, we adopted the physical parameters derived by
Belloche et al. (2013) for CH 3 CHO (see Table 6). Figure 3
shows the model provided by MADEX together with the IRAM
30 m data of Sgr B2(N). This model is also consistent with the
lack of CPCA lines above the detection limit of the PRIMOS

data.
Table 7 shows the CH 3 CHO/CPCA density ratios in Orion
KL and Sgr B2. It is worth noting that the lower limit ratios
derived agree for the considered Orion cores and for Sgr B2,

∼
and they are extremely low ( 2–4). As we discuss previously for
other species (Bermúdez et al. 2018; Cabezas et al. 2019, 2020b),
the CPCA partition function is approximately four times larger
than that of CH 3 CHO at ∼100 K. As a result, the CPCA lines


2 The 100 m Green Bank Telescope (GBT) PRebiotic Interstellar
MOlecule Survey covers a frequency band between 7 and 50 GHz.
Access to the entire PRIMOS data set, specifics on the observing
strategy, and overall frequency coverage information is available at
```
http://www.cv.nrao.edu/ aremijan/PRIMOS/

```


appear weaker than those of CH 3 CHO assuming similar abundances. Therefore, it is reasonable to suggest that the derived
lower limit ratio is far from the real abundance ratio between
these species in the considered regions.


**6. Conclusions**


This paper presents an extensive laboratory study of the rotational spectrum of CPCA in its ground- and vibrationally
excited states, extending the earlier limited knowledge on the
spectroscopic properties of this molecule. Measurements were
performed in the 31.5–50 and 72–116.5 GHz frequency regions
using a high-resolution broadband spectrometer. From the analysis we obtained accurate rotational parameters for the ground
state of both cis and trans isomers of CPCA which allowed us to
obtain sufficiently reliable frequency predictions up to 300 GHz.
In addition to the ground states, we identified 12 and 6 vibrationally excited states for the trans and cis isomers, respectively,
comprising fundamental modes, multiple excitation quanta, and
combination states. By comparison of the observed line intensities, we determined the concentration of both cis and trans
isomers in the gas phase with high accuracy. We find that the
trans isomer is almost 1.2 times more abundant than the cis isomer, which means that the former is 44.05(75) cm [−][1] more stable
than the latter. Finally, these new laboratory data were employed
to search for CPCA in the warm molecular clouds Orion KL
and Sgr B2(N) using the spectral surveys captured by ALMA
(Orion) and IRAM 30 m (Sgr) at 1 and 3 mm, respectively. We
did not find any CPCA above the detection limit of these data and
provide upper limits to the column density for the two isomers
of CPCA.


_Acknowledgements._ We thank the European Research Council for funding support under Synergy Grant ERC-2013-SyG, G.A. 610256 (NANOCOSMOS). We
also thank Ministerio de Ciencia e Innovación for funding support through
projects AYA2016-75066-C2-1-P and PID2019-107115GB-C21. B.T. also thanks


A75, page 7 of 8

A&A 645, A75 (2021)


observations carried out with the IRAM 30-meter telescope. IRAM is supported
by INSU/CNRS (France), MPG (Germany), and IGN (Spain).


**References**


[Bartell, L. S., Guillory, J. P. 1965, J. Chem. Phys., 43, 647](http://linker.aanda.org/10.1051/0004-6361/202039924/1)
[Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2009, A&A, 499, 218](http://linker.aanda.org/10.1051/0004-6361/202039924/2)
Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito, C. 2013,



**[Fig. 3.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/202039924&pdf_id=0)** Observed data of Orion KL and Sgr B2 taken with the ALMA
interferometer and the IRAM 30 m telescope, respectively (histogram
black spectrum), together with the synthetic spectra obtained using the
column densities given as upper limits in Table 6 (red and blue thin
curves). The synthetic total model for the 30 m data of Sgr B2(N) (see
Belloche et al. 2013) is overlaid in green. A v LSR of +9.0 km s [−][1] and
+64.0 km s [−][1] is assumed for Orion KL and Sgr B2, respectively.


the Spanish MICIU for funding support from grant PID2019-106235GB-I00.
C.B. thanks to Ministerio de Ciencia, Innovación y Universidades for a Juan
de la Cierva postdoctoral fellowship (FJCI-2016-27983). This paper makes use
of the following ALMA data: ADS/JAO.ALMA#2011.0.00009.SV. ALMA is a
partnership of ESO (representing its member states), NSF (USA), and NINS
(Japan) with NRC (Canada), NSC, and ASIAA (Taiwan), and KASI (Republic
of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. This work was also based on


A75, page 8 of 8



[A&A, 559, A47](http://linker.aanda.org/10.1051/0004-6361/202039924/3)
[Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2019, A&A, 628, A10](http://linker.aanda.org/10.1051/0004-6361/202039924/4)
[Bermúdez, C., Tercero, B., Motiyenko, R. A., et al. 2018, A&A, 619, A92](http://linker.aanda.org/10.1051/0004-6361/202039924/5)
[Brouillet, N., Despois, D., Baudry, A., et al. 2013, A&A, 550, A46](http://linker.aanda.org/10.1051/0004-6361/202039924/6)
[Brown, R. D., Crofts, J. G., Gardner, F. F., et al. 1975, ApJ, 197, L29](http://linker.aanda.org/10.1051/0004-6361/202039924/7)
[Cabezas, C., Bermúdez, C., Gallego, J. D., et al. 2019, A&A, 629, A35](http://linker.aanda.org/10.1051/0004-6361/202039924/8)
[Cabezas, C., Bermúdez, C., Endo, Y., et al. 2020a, A&A, 636, A33](http://linker.aanda.org/10.1051/0004-6361/202039924/9)
Cabezas, C., Bermúdez, C., Tercero, B., &, Cernicharo, J. 2020b, [A&A,](http://linker.aanda.org/10.1051/0004-6361/202039924/10) 639,
[A129](http://linker.aanda.org/10.1051/0004-6361/202039924/10)
Cernicharo, J. 2012, EAS Pub. [Ser.,](http://linker.aanda.org/10.1051/0004-6361/202039924/11) 2012, 251, `[https://nanocosmos.iff.](https://nanocosmos.iff.csic.es/?pageid=1619)`
```
 csic.es/?pageid=1619
```

[Cernicharo, J., Marcelino, N., Roueff, E., et al. 2012, ApJ, 759, L43](http://linker.aanda.org/10.1051/0004-6361/202039924/12)
[Cernicharo, J., Kisiel, Z., Tercero, B., et al. 2016, A&A, 587, L4](http://linker.aanda.org/10.1051/0004-6361/202039924/13)
[Cernicharo, J., Gallego, J. D., López-Pérez, J. A., et al. 2019, A&A, 626, A34](http://linker.aanda.org/10.1051/0004-6361/202039924/14)
[Cížek, J., Advances in Chemical Physics, ed. P. C. Hariharan (New York: Wiley](http://linker.aanda.org/10.1051/0004-6361/202039924/15)
Interscience), 14, 35
Collins, J. B., Schleyer, P. v. R., Binkley, J. S., & Pople, J. A. 1976, J. [Chem.](http://linker.aanda.org/10.1051/0004-6361/202039924/16)
[Phys., 64, 5142](http://linker.aanda.org/10.1051/0004-6361/202039924/16)
[De Mare, G., & Peterson, M. R. 1983, J. Mol. Strct. Theochem., 104, 115](http://linker.aanda.org/10.1051/0004-6361/202039924/17)
[Dunning Jr., T. H. 1989, J. Chem. Phys., 90, 1007](http://linker.aanda.org/10.1051/0004-6361/202039924/18)
[Durig, J. R., & Little, T. S. 1988, Croat. Chem. Acta, 61, 529](http://linker.aanda.org/10.1051/0004-6361/202039924/19)
[Durig, J. R., & Shen, S. 2000, Spectrochim. Acta, Part A, 56A, 2545](http://linker.aanda.org/10.1051/0004-6361/202039924/20)
[Durig, J. R., Feng, F., Little, T. S., & Wang, A.-Y. 1992, Struct. Chem., 3, 417](http://linker.aanda.org/10.1051/0004-6361/202039924/21)
[Favre, C., Despois, D., Brouillet, N., et al. 2011, A&A, 532, A32](http://linker.aanda.org/10.1051/0004-6361/202039924/22)
[Frisch, M. J., Pople, J. A., & Binkley, J. S. 1984, J. Chem. Phys., 80, 3265](http://linker.aanda.org/10.1051/0004-6361/202039924/23)
Frisch, M. J., Trucks, G. W., Schlegel, H. B., et al. 2016, Gaussian [16,](http://linker.aanda.org/10.1051/0004-6361/202039924/24) revision
[A.03](http://linker.aanda.org/10.1051/0004-6361/202039924/24)
[Grimme, S. 2006, J. Comput. Chem., 27, 1787](http://linker.aanda.org/10.1051/0004-6361/202039924/25)
Gordy, W., & Cook, R. 1984, Microwave Molecular [Spectra,](http://linker.aanda.org/10.1051/0004-6361/202039924/26) Techniques of
[Chemistry (New York: Wiley)](http://linker.aanda.org/10.1051/0004-6361/202039924/26)
[Gottlieb, C. A. 1973, Molecules in the Galactic Environment (New York: Wiley)](http://linker.aanda.org/10.1051/0004-6361/202039924/27)
[Hartree, D.R. 1928, Math. Proc. Cambridge Philos. Soc., 24, 89](http://linker.aanda.org/10.1051/0004-6361/202039924/28)
[Hollis, J. M., Lovas, F. J., & Jewell, P. R. 2000, ApJ, 540, L107](http://linker.aanda.org/10.1051/0004-6361/202039924/29)
[Hollis, J. M., Jewell, P. R., Lovas, F. J., et al. 2004, ApJ, 610, L21](http://linker.aanda.org/10.1051/0004-6361/202039924/30)
[Hudson, R. L., & Coleman F. M. 2019, ACS Earth Space Chem., 3, 1182](http://linker.aanda.org/10.1051/0004-6361/202039924/31)
[Irvine, W. M., Brown, R. D., Cragg, D. M., et al. 1988, ApJ, 335, L89](http://linker.aanda.org/10.1051/0004-6361/202039924/32)
[Kisiel, Z., & Bialkowska-Jaworska, E. 2019, J. Mol. Spectr., 359, 16.](http://linker.aanda.org/10.1051/0004-6361/202039924/33)
[Lee, C., Yang, W., & Parr, R. G. 1988, Phys. Rev. B, 37, 785](http://linker.aanda.org/10.1051/0004-6361/202039924/34)
[Møller, C., & Plesset, M. S. 1934, Phys. Rev., 46, 618](http://linker.aanda.org/10.1051/0004-6361/202039924/35)
[Neill, J. L., Muckle, M. T., Zaleski, D. P., et al. 2012, ApJ, 755, 153](http://linker.aanda.org/10.1051/0004-6361/202039924/36)
[Pickett, H. M. 1991, J. Mol. Spectr., 148, 371](http://linker.aanda.org/10.1051/0004-6361/202039924/37)
[Remijan, A. J., Hollis, J. M., Lovas, F. J., et al. 2008, ApJ, 675, L85](http://linker.aanda.org/10.1051/0004-6361/202039924/38)
[Rubin, R. H., Swenson, G. W., Jr., Benson, R. C., et al. 1971, ApJ, 169, L39](http://linker.aanda.org/10.1051/0004-6361/202039924/39)
[Snyder, L. E., Buhl, D., Zuckerman, B., & Palmer, P. 1969, Phys. Rev. Lett., 22,](http://linker.aanda.org/10.1051/0004-6361/202039924/40)
[679](http://linker.aanda.org/10.1051/0004-6361/202039924/40)

[Tanarro, I., Alemán, B., de Vicente, P., et al. 2018, A&A, 609, A15](http://linker.aanda.org/10.1051/0004-6361/202039924/41)
[Tercero, B., Kleiner, I., Cernicharo, J., et al. 2013, A&A, 770, L13](http://linker.aanda.org/10.1051/0004-6361/202039924/42)
[Tercero, B., Cernicharo, J., López, A., et al. 2015, A&A, 582, L1](http://linker.aanda.org/10.1051/0004-6361/202039924/43)
[Tercero, B., Cuadrado, S., López, A., et al. 2018, A&A, 620, L6](http://linker.aanda.org/10.1051/0004-6361/202039924/44)
[Volltrauer, H. N., & Schwendeman, R. H. 1971, J. Chem. Phys., 54, 260](http://linker.aanda.org/10.1051/0004-6361/202039924/45)
Watson, J.K.G., Vibration [Spectra](http://linker.aanda.org/10.1051/0004-6361/202039924/46) and Structure, ed. J. Durig (Amsterdam:
Elsevier), 6, 1
[Woon, D. E., & Dunning Jr., T. H. 1995, J. Chem. Phys., 98, 1358](http://linker.aanda.org/10.1051/0004-6361/202039924/47)
[Zuckerman, B., Ball, J. A., & Gottlieb, C. A. 1971, ApJ, 163, L41](http://linker.aanda.org/10.1051/0004-6361/202039924/48)


</paper>

## Items to check

```json
[
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Gas-phase trans/cis relative intensity ratio at 350 K = 1.1985 dimensionless",
  "failed_quote": "we find that the transitions for the trans isomer are 1.1985(37) times more intense than those for the cis isomer."
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "The trans isomer of CPCA is moderately more stable than the cis isomer in the gas phase, though both should be considered for astronomical searches.",
  "failed_quote": "we find that the transitions for the trans isomer are 1.1985(37) times more intense than those for the cis isomer. Assuming a temperature for our experiment of 350K, this implies an energy difference between both isomers of 44.05(75) cm −1 , with the trans species being the most stable."
 }
]
```
