# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.524.1211M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# **Rotational spectroscopy and astronomical search for the** **2-hydroxyacetonitrile isotopologues (HOCH2CN)-C-13,** **(HOCH2CN)-C-13, and DOCH2CN**

### L. Margulès, A. Coutens, N. F. W. Ligterink, A Ahmadi, R.A. Motiyenko, E.A. Alekseev, C. Vastel, E. Caux, J-C Guillemin **To cite this version:**

L. Margulès, A. Coutens, N. F. W. Ligterink, A Ahmadi, R.A. Motiyenko, et al.. Rotational spectroscopy and
astronomical search for the 2-hydroxyacetonitrile isotopologues (HOCH2CN)-C-13, (HOCH2CN)-C-13, and
DOCH2CN. Monthly Notices of the Royal Astronomical Society, 2023, 524 (1), pp.1211-1218. ⟨10.1093/mnras/stad1834⟩. ⟨hal-04193322⟩

### **HAL Id: hal-04193322** **https://hal.science/hal-04193322v1**


Submitted on 3 Oct 2023



**HAL** is a multi-disciplinary open access archive
for the deposit and dissemination of scientific research documents, whether they are published or not.
The documents may come from teaching and research
institutions in France or abroad, or from public or private research centers.



L’archive ouverte pluridisciplinaire **HAL**, est destinée au dépôt et à la diffusion de documents scientifiques de niveau recherche, publiés ou non, émanant
des établissements d’enseignement et de recherche
français ou étrangers, des laboratoires publics ou
privés.



[Distributed under a Creative Commons CC BY-NC 4.0 - Attribution - Non-commercial use - International](https://creativecommons.org/licenses/by-nc/4.0/)

[License](https://creativecommons.org/licenses/by-nc/4.0/)

MNRAS **000**, 1–8 (2023) Preprint 15 June 2023 Compiled using MNRAS L [A] TEX style file v3.0

## **Rotational spectroscopy and astronomical search for the** 2-hydroxyacetonitrile isotopologues HO [13] CH 2 CN, HOCH [13] 2 [CN and] DOCH 2 CN


L. Margulès, [1] [⋆] A. Coutens, [2] N. F.W. Ligterink, [3] A. Ahmadi, [4] R. A. Motiyenko, [1] E. A. Alekseev, [1][,][5]

C. Vastel, [2] E. Caux, [2] and J.-C. Guillemin [6]

1 _Univ. Lille, CNRS, UMR 8523 - PhLAM - Physique des Lasers Atomes et Molécules, F-59000 Lille, France_
2 _Institut de Recherche en Astrophysique et Planétologie (IRAP), Université de Toulouse, UPS-OMP, CNRS, CNES, 9 av. du Colonel Roche,_
_31028 Toulouse Cedex 4, France_
3 _Physics Institute, University of Bern, Sidlerstrasse 5, 3012 Bern, Switzerland_
4 _Leiden Observatory, Leiden University, PO Box 9513, 2300 RA Leiden, The Netherlands_
5 _Radiospectrometry Department, Institute of Radio Astronomy of NASU, Kharkiv, Ukraine_
6 _Univ Rennes, Ecole Nationale Supérieure de Chimie de Rennes, CNRS, ISCR UMR6226, F-35000 Rennes, France_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

The main isotopologue of 2-hydroxyacetonitrile (glycolonitrile; HOCH 2 CN) has recently been detected in the interstellar
medium (ISM). To date, no rotational spectroscopy of 2-hydroxyacetonitrile [13] C-isotopologues studies has been carried out
and only few centimeter-wave measurements of one deuterated isotopologue (DOCH 2 CN) exist. The rotational spectrum of the
2-hydroxyacetonitrile 13C-isotopologues and DOCH 2 CN was investigated from 150 to 530 GHz. As the parent isotopic species,
the other 2-hydroxyacetonitrile isotopologues exhibit large amplitude motion due to the torsion of the hydroxyl group. The
analysis of the spectra were carried out using the RAS formalism and Watson’s S-reduction Hamiltonian implemented in the
SPFIT code. More than 3000 lines were fitted for the three studied isotopologues, with quantum number values reaching 60 to
67 for _J_ and 21 to 25 for _K_ _a_ depending on the species. Accurate line lists up to 600 GHz and partition functions are provided.
A search for these isotopologues in SMM1-a and IRAS16293 B surveys resulted in non-detections; upper limits to the column
density were determined. The accurate spectroscopic prediction of their spectra provided in this work will allow astronomers to
continue the search for 2-hydroxyacetonitrile isotopologues in the ISM.


**Key words:** ISM: molecules – methods: laboratory: molecular – submillimetre: ISM – molecular data – line: identification –
astrochemistry



**1** **INTRODUCTION**


The astrochemical study of the isotopologues (or isotopomers) of
a molecule detected in the interstellar medium (ISM) is an essential tool for improving the understanding of the formation of these
compounds by searching for similar isotopic ratios in possible precursors. This approach thus allows to eliminate a number of potential reactants and the reactions associated with them. The remaining
precursor(s) allows considering possible chemical reactions which
can also lead to other compounds which become target compounds.
On Earth, the [13] C/ [12] C ratio is about 1%. This ratio can vary considerably depending on the studied area of the universe. It is of
the order of 4 to 5% in the region of the Galactic Center, and 1–
2% in the Solar neighborhood (Halfen et al. 2017; Müller et al.
2008; Jacob et al. 2020; Wilson & Rood 1994). Similarly, deuterated
compounds were observed. Even trideuterated compounds, ND 3 and
CD 3 OH, were detected, this implies a huge enhancement factor compared to the deuterium/hydrogen cosmic value (Roueff et al. 2005;


⋆ E-mail: laurent.margules@univ-lille.fr



Parise et al. 2004). In order to quantify the ratio between isotopologues, laboratory recording of the spectrum of each isotopologue
is necessary before detecting them and determining the ratio between each and the main isotopomer if they are sufficiently abundant
to perform such studies. We recently reported the millimeter spectrum of 2-hydroxyacetonitrile (HOCH 2 CN, glycolonitrile, hereafter
hydroxyacetonitrile) (Margulès et al. 2017) and this compound was
detected a few months later in both the inner hot corino and the

outer cold envelope of IRAS16293 B (Zeng et al. 2019). Later, a second detection of hydroxyacetonitrile was reported towards Serpens
SMM1-a (Ligterink et al. 2021). These two detections are thus far
the only observations of this molecule. Hydroxyacetonitrile is considered a prebiotic molecule because it is a catalyst for the formation
of the nucleobase adenine (Schwartz & Goverde 1982) and is often
a byproduct in the synthesis by a Strecker reaction of aminoacetonitrile (NH 2 CH 2 CN). It can be formed in the ISM through the reaction
of the CN anion or radical with formaldehyde (Danger et al. 2012).
Thus, a link can be established between the ratios of the [13] C and
12 C isotopologues of hydroxyacetonitrile if they are detected, and
those of formaldehyde and hydrogen cyanide in the event that such


# ACCEPTED MANUSCRIPT / CLEAN COPY

2 _L. Margulès et al._


ratios can be measured for these compounds in the same area. We
report here the synthesis, measurements, and analysis of the two [13] C
isotopomers of (HO [13] CH 2 CN and HOCH [13] 2 [CN) and one deuterated]
isotopologue (DOCH 2 CN) spectra in the range 150–530 GHz.


**2** **EXPERIMENTAL SECTION**


**2.1** **Synthesis**


Paraformaldehyde- [13] _C_ and potassium cyanide- [13] _C_ were purchased
from Eurisotop and used without further purification. Formaldehyde
(37 wt % in water), potassium cyanide and methanol- _d_ (CH 3 OD)
were purchased from Sigma-Aldrich. 2-hydroxyacetonitrile- _1-_ [13] _C_
and 2-hydroxyacetonitrile- _2-_ [13] _C_ were prepared as previously reported for the main isotopologue (Gaudry 1947, 1955) but using
paraformaldehyde- [13] _C_ or potassium cyanide- [13] _C_, respectively.
**Hydroxyacetonitrile-** _**1-**_ [13] _**C.**_ To obtain 6 g of a 20 wt % aqueous
solution of [13] _C_ -formaldehyde, paraformaldehyde- [13] _C_ (1.20 g) was
diluted in water (4.8 g) under stirring, heating to 50 [◦] C and then
cooled at room temperature. In a 50 mL flask cooled to 0 [◦] C, potassium cyanide (2.6 g, 40 mmol) was dissolved in water (5 mL) and
formaldehyde- [13] _C_ (20% in water, 6 g) was added dropwise. After
10 min standing, 4.6 mL of dilute sulfuric acid (1.14 mL, 1.84 g/ml,
in 3.5 ml of water) was added dropwise to the cold solution (0 [◦] C).
A copious precipitate of potassium sulfate was formed. The pH of
the solution was about 1.9. A 10% potassium hydroxide solution was
then added, dropwise, and with cooling, until the pH was about 3.0.
The flask was then removed from the cooling bath, 10 mL of diethyl
ether have been added, and the mixture was well shaken. The salt
was removed by filtration, and washed with 5 mL of diethyl ether. 2hydroxyacetonitrile- _1-_ [13] _C_ was then extracted (10 x10 mL of diethyl
ether), dried and distilled in vacuo. Yield: 65%. [1] H NMR (CD 3 CN,
400 MHz) δ 3.83 (m brd, 1H, OH); 4.29 (dd, 2H, [1] J _CH_ = 152.6 Hz,
3 J _HH_ = 6.4 Hz, CH 2 ). 13 C NMR (CD 3 CN, 100 MHz) δ 48.1 ( 1 J _CH_
= 152.6 Hz (t), CH 2 ); 118.7 (d, [1] J _CC_ = 59.5 Hz (d), CN).
**Hydroxyacetonitrile-** _**2-**_ [13] _**C.**_ The same procedure was used with
potassium cyanide- [13] _C_ (2.7 g, 40 mmol), water (5 mL) and formaldehyde (3.4 mL, 37 wt % in water and 2.6 mL of water). Yield: 65%.
1 H NMR (CD 3 CN, 400 MHz) δ 3.83 (m brd, 1H, OH); 4.29 (dd, 2H,
2 J _CH_ = 3 J _HH_ = 6.4 Hz, CH 2 ). 13 C NMR (CD 3 CN, 100 MHz) δ 48.1
( [1] J _CC_ = 59.5 Hz (d), [1] J _CH_ = 152.6 Hz (t), CH 2 ); 118.7 ( [2] J _CH_ = 6.4
Hz (t), CN).
**Deuteroxyacetonitrile.** Methanol- _d_ CH 3 OD (3.2 g, 0.1 mol) was
added to hydroxyacetonitrile (1.14 g, 20 mmol) and the mixture was
stirred for 10 min at room temperature. Low boiling compounds were
removed in vacuo and the reaction repeated twice.


**2.2** **Lille: Submillimeter wave spectra**


The measurements in the frequency range under investigation (150–
530 GHz) were performed using the Lille spectrometer (Zakharenko
et al. 2015). The absorption cell was a stainless-steel tube (6 cm in
diameter, 220 cm in length). The sample pressure and temperature
during measurements were about 10 Pa and room temperature, and
the line width was limited by Doppler broadening. The frequency
range 150–530 GHz was covered with various active and passive frequency multipliers from VDI Inc. and an Agilent synthesizer (12.5–
18.25 GHz) was used as the source of radiation. Absorption signals
were detected by an InSb liquid He-cooled bolometer (QMC Instruments Ltd.). Estimated uncertainties for measured line frequencies


MNRAS **000**, 1–8 (2023)



are 30 kHz and 50 kHz depending on the observed S/N and the
frequency range.


**3** **ANALYSIS OF THE ROTATIONAL SPECTRA**


As for the parent isotopic species, we only analyzed the spectra of
the _gauche_ rotamer, which is the most stable one. The _trans_ rotamer of hydroxyacetonitrile is calculated to be 1.41 kcal.mol [−][1]

(493 cm [−][1] /710 K) higher in energy (Dalbouha et al. 2017). The
analysis was complicated by a large amplitude motion (LAM) with
a symmetric two minima potential due to the two equivalent _gauche_
rotamers. As a result of the tunneling through the barrier to OHgroup torsion, each energy level of 2-hydroxyacetonitrile is split into
two substates labeled here as 0 (the lowest energy level) and 1. The
corresponding labeling used by Dalbouha et al. (2017) is A1 and
A2. The structure of _gauche_ rotamer is very close to a symmetric
prolate rotor with an asymmetry parameter κ = -0.968. Many nitriles
are characterized by large dipole moment. It is also the case of 2hydroxyacetonitrile: µ _a_ = 2.32 D, µ _b_ = 1.31 D, µ _c_ = 1.23 D. These ab
initio values are from Dalbouha et al. (2017). It should be noted that
the component of the dipole moment along _c_ -axis is linked to torsion
motion, and allows transitions between the two torsional substates.
For the global fit, a model based on the reduced axis system (RAS)
approach proposed by Pickett (1972) was implemented in the widely
used SPFIT/SPCAT programs for fitting and predicting molecular
spectra. Is has been shown by Christen & Müller (2003) that the RAS
formalism is equivalent to the internal-axis-method (IAM) approches
developed by Hougen and coworkers for molecules with several large
amplitude motions (Hougen 1985; Coudert & Hougen 1988). This
method is particulary suitable for double minimum LAM cases, we
employed it successfully in previous studies (Motiyenko et al. 2010;
Smirnov et al. 2013; Motiyenko et al. 2015) and in particular with
the hydroxyacetonitrile normal species (Margulès et al. 2017). More
details about the model can be found in this paper.


**3.1** [13] **C isotopologues**


The analysis of the [13] C isotopologues was rather straightforward.
Even if no spectroscopic studies existed up to now, we could take
benefit of the main isotopologue study. Substituting the [12] C with [13] C
does not affect significantly kinetic and potential energy of LAM as
it can be verified in the final parameters set table (Table 1). With
this assumption, for both [13] C isotopologues, we used as starting parameters the _ab_ _initio_ ground vibrational state rotational constants
of Table 2 in Dalbouha et al. (2017) while all the other parameters (centrifugal distortion, tunneling splitting, and Coriolis coupling
constants) were taken from Margulès et al. (2017). The initial predictions obtained using these parameters allowed, for example, easy
assignment of HO [13] CH 2 CN _[a]_ _R_ -branch _J_ = 17 − 16 band heads at
156 GHz that were shifted by 260 MHz in the experimental spectrum.
The _[a]_ _R_ branch transitions are the most intense in the spectra, due to
the large µ _a_ value. Their assignment and improvement of the set of
Hamiltonian parameters permitted the search for _b_ -type transitions.
Finally, we were also able to assign _c_ -type transitions connecting two
torsional substates. Going step by step with the different ranges (150220, 225-330, 400-530 GHz) permitted to determine almost all the
rotational and tunneling parameters we could fit in the main isotopologue study (Margulès et al. 2017). The same procedure was used for
the second [13] C isotopologue: HOCH [13] 2 [CN. Some of the octic distor-]
sion constants which could not be determined better than 10 times


# ACCEPTED MANUSCRIPT / CLEAN COPY

their standard deviation were kept fixed at the main isotopologue
values.
In total, 3403 distinct lines of the HO [13] CH 2 CN isotopologue were
assigned with maximum values for _J_ and _K_ _a_ of 67 and 25, respectively. The standard deviation of the fit is 26.3 kHz and 45 parameters
were determined. For HOCH [13]
2 [CN isotopologue, the dataset is com-]
posed of 3235 lines with maximum values for _J_ and _K_ _a_ of 63 and
26, respectively. The standard deviation of the fit is 28.7 kHz and 44
parameters were determined. The number of parameters needed to
reproduce experimental accuracy seems important, but this is generally the case when dealing with large amplitude motion.
The final set of parameters that we obtained are listed in Table 1.
The first column of the table shows the parameters of the main
isotopologue from Margulès et al. (2017). This permits to check the
good agreement of the [13] C parameters from this new study with
the [12] C ones. From the analysis of Table 1, it can be clearly seen
that [12] C to [13] C isotopic substitution has a very limited influence
on tunneling Hamiltonian parameters. We also compare in Table 2
the rotational constants _A_, _B_, and _C_, and energy difference between
tunneling sublevels _E_ from our study with the _ab initio_ calculations.
The difference between theoretical and experimental values for [13] C
isotopologues have the same order of magnitude as for the main
isotopologue (see Table 2 of Margulès et al. (2017)). This confirms
the quality of the results obtained in this work.


**3.2** **Deuterated isotopologue: DOCH** 2 **CN**


Despite the existence of centimeter-wave measurements (Cazzoli
et al. 1973), the analysis of the DOCH 2 CN spectra was more complicated. The deuteration of the hydroxyl group hydrogen implies a
significant variation of the mass of the tunneling atom which has a direct influence on the tunneling probability and hence on the splitting
between 0 and 1 substates, and in general, on the tunneling dynamics.
Therefore, for DOCH 2 CN isotopic species, as starting set of tunneling and Coriolis coupling parameters, we could not use the ones
determined for the parent or [13] C species. The initial assignment and
analysis were performed separately for the two tunneling substates.
The initial spectral predictions were calculated with Watson’s Hamiltonian in the _I_ _[r]_ representation, the rotational parameters from Cazzoli
et al. (1973), and the _ab initio_ quartic centrifugal distortion constants
(Dalbouha et al. 2017). In such manner we assigned _[a]_ _R_ -branch transitions for both substates up to _K_ ” _a_ = 4 in the 150–300 GHz range
corresponding to _J_ ” between 18 and 30. The assignment of higher _K_ _a_
transitions was not possible without taking Coriolis-type interaction
between tunneling substates into account. However, the least-squares
fitting using the global model is not straightforward due to the strong
correlation between tunneling and Coriolis-coupling parameters. In
this case, the initial fit strategy is to fix one of the two parameters,
the energy difference _E_ or the Coriolis coupling parameter _F_ _bc_, to
a series of reasonable values, to vary the second one, and to search
for a minimum rms deviation solution as a function of fixed parameter Motiyenko et al. (2018). We used _E_ as fixed parameter in
the range between 15 and 18 GHz that comprises the corresponding
values from _ab_ _initio_ calculations, 15.3 GHz, and from an estimation by Cazzoli et al. (1973), 16.7 GHz. Using this strategy, the
minimum rms deviation fit was obtained for _E_ = 17.5 GHz. New predictions calculated using optimized value of _E_ allowed us to locate
and assign in the spectra _c_ -type transitions that connect two tunneling
substates, and thus, to remove the correlation between tunneling and
Coriolis-coupling parameters. One should note that without accurate
estimation of _E_, it is almost impossible to assign correctly _c_ -type
transitions. For example, the _c_ -type transition frequencies calculated



_Spectroscopy for HOCH_ 2 _CN isotopologues_ 3


using _E_ values from Dalbouha et al. (2017) or Cazzoli et al. (1973)
are shifted by few GHz compared to experimental positions. Finally,
after removing the correlations, we switched to a model that uses a
single set of rotational and centrifugal distortion parameters for both
substates, as in the case of the parent or [13] C isotopic species.
A total of 3190 distinct lines of the DOCH 2 CN were assigned with
maximum values for _J_ and _K_ _a_ of 60 and 21, respectively. Among the
assigned lines 393 lines are transitions between tunneling substates.
44 parameters were determined and the standard deviation of the fit
is 26.6 kHz. We can observe in the Table 2 a good agreement of the
rotational constants and energy difference of the sublevels from our
study with the _ab initio_ calculations. As mentioned for [13] C species,
the difference observed have the same order of magnitude as the
main isotopologue (Margulès et al. 2017). For example, the energy
difference we obtained 17567.061(10) MHz is in good agreement
with 15289.4 MHz, regarding the 15% accuracy for the main and
13 C isotopologues.
Part of the new measurements with the fit residuals for
HO [13] CH 2 CN, HOCH [13] 2 [CN and DOCH] [2] [CN are given in Tables][ 3][,][ 4]
and 5. Owing to their large size, the complete versions of the global fit
(Tables S1, S2 and S3) for the three isotopologues are supplied at the
CDS [1] . The predicted spectra are available in different formats including standard .cat format (Pickett 1972) from the new database of the
Lille spectroscopy group called the Lille Spectroscopic Database [2] .
The predictions can be generated using various options (e.g., intensity units, temperature, and frequency range) that provide additional
flexibility in the data access.


**3.3** **Partition function**


The tabulated values for the partition function are given in Table 6,
with _Q_ tot (T) = _Q_ vib (T) ×Q rot (T). The rotational partition function
was obtained directly at various temperatures from SPCAT (Pickett
1991) with J up to 90, and K _a_ up to 40. The vibrational contribution
was calculated in the harmonic approximation (Gordy et al. 1984),
as we proceeded in our previous studies (see, e.g., Margulès et al.
2020). The four lowest vibrational excited states levels were considered. The remaining ones above 870 cm [−][1] (1252 K) were found to
have no influence on the partition function calculations especially at
temperatures below 200 K. The band centers values were taken from
Table 3 in Dalbouha et al. (2017).


**4** **ASTRONOMICAL OBSERVATIONS: SEARCH FOR**

**HYDROXYACETONITRILE ISOTOPOLOGUES IN**

**SMM1-A AND IRAS16293 B**


**4.1** **SMM1-a**


The main isotopologue of hydroxyacetonitrile has been detected towards Serpens SMM1-a (hereafter SMM1-a) at high abundance (Ligterink et al. 2021), making this a suitable target to search for its isotopologues DOCH 2 CN, HO [13] CH 2 CN and HOCH [13] 2 [CN. The source,]
observations, and methods are described in Ligterink et al. (2021)
and therefore be covered briefly here. SMM1 is a well characterized and chemically rich source, located at a distance of 436±10 pc
(Ortiz-León et al. 2017), and consists of multiple protostars. The
brightest, SMM1-a, is an intermediate-mass Class 0 protostar. Recently, this source was targeted with ALMA towards a phase centre


1 https://cds.unistra.fr
2 https://lsd.univ-lille.fr



MNRAS **000**, 1–8 (2023)
# ACCEPTED MANUSCRIPT / CLEAN COPY

4 _L. Margulès et al._


**Table 1.** Spectroscopic parameters of the [13] C and deuterated gauche conformer of 2-hydroxyacetonitrile species


Parameters in MHz HOCH 2 CN _[a]_ HO [13] CH 2 CN HOCH [13] 2 [CN] DOCH 2 CN


Rotational and centrifugal distortion constants


_A_ 33609.53194(27) _[b]_ 32787.31228(29) 33569.30468(40) 30653.94661(70)

_B_ 4838.014347(41) 4820.980595(68) 4810.878790(83) 4725.725505(99)
_C_ 4377.304462(40) 4349.083437(65) 4354.399428(80) 4262.86028(24)
_D_ _J_ ∗ 10 [3] 3.093051(44) 3.008971(76) 3.049000(80) 3.280413(94)
_D_ _JK_ ∗ 10 [3] -63.89803(34) -59.85131(51) -64.23275(47) -54.586(17)
_D_ _K_ ∗ 10 [3] 969.2208(61) 917.8160(52) 982.3170(80) 753.258(32)
_d_ 1 ∗ 10 [3] -0.695725(10) -0.692148(22) -0.685525(26) -0.788049(46)
_d_ 2 ∗ 10 [3] -0.041757(18) -0.043740(23) -0.040349(15) -0.055228(45)
_H_ _J_ ∗ 10 [6] 0.0107392(81) 0.010232(23) 0.010513(28) 0.011381(31)
_H_ _JK_ ∗ 10 [6] -0.16090(71) -0.1265(13) -0.17990(54) 0.2101(91)
_H_ _KJ_ ∗ 10 [6] -3.6005(17) -3.4904(44) -3.4713(15) -5.399(33)
_H_ _K_ ∗ 10 [6] 82.883(56) 77.670(30) 83.883(55) 60.75(11)
_h_ 1 ∗ 10 [6] 0.0044035(40) 0.004285(11) 0.004305(13) 0.004613(22)
_h_ 2 ∗ 10 [6] 0.0005288(27) 0.0005242(20) 0.0005086(18) 0.000368(11)
_h_ 3 ∗ 10 [6] 0.00007335(95) 0.0000622(12) 0.00008221(61)
_L_ _K_ ∗ 10 [9] -3.14(17) -3.14 _[c]_ -3.14 _[c]_

_L_ _KKJ_ ∗ 10 [9] 0.3292(25) 0.3028(20) 0.3435(15) 0.751(18)
_L_ _JK_ ∗ 10 [9] -0.04864(29) -0.04450(42) -0.04609(63) 0.000169(33)
_L_ _JJK_ ∗ 10 [9] 0.001496(12) 0.001417(24) 0.001485(27) -0.1871(34)
_L_ _J_ ∗ 10 [9] -0.00005190(75) -0.0000553(28) -0.0000624(36) -0.0000840(34)
_l_ 1 ∗ 10 [9] -0.00002619(46) -0.0000298(16) -0.0000265(19) -0.0000208(26)
_l_ 2 ∗ 10 [9] -0.00000544(39) -0.00000544 _[c]_ -0.00000544 _[c]_

_l_ 3 ∗ 10 [9] -0.00000236(17) -0.00000236 _[c]_ -0.00000236 _[c]_


Tunneling splitting constants


_E_ 112672.5526(30) 112016.5779(41) 112716.4480(55) 17567.0493(89)
_E_ _J_ 1.0954348(39) 1.0751770(59) 1.0883325(56) 0.380161(59)
_E_ _K_ -13.606157(53) -13.273996(71) -13.78242(11) -3.71749(19)
_E_ _JJ_ ∗ 10 [3] -0.00749(11) -0.00487(24) -0.01055(13) -0.007934(35)
_E_ _JK_ ∗ 10 [3] -0.19132(72) -0.2154(14) -0.16000(80) -0.1601(30)
_E_ _KK_ ∗ 10 [3] 0.44739(78) 0.4516(14) 0.3688(14) 0.1017(35)
_E_ 2 0.331606(22) 0.329474(47) 0.329718(27) 0.119585(35)
_E_ 2 _J_ ∗ 10 [3] -0.0073918(30) -0.0072687(69) -0.0073022(88) -0.005092(24)
_E_ 2 _K_ ∗ 10 [3] 1.339(22) 1.589(46) 0.664(26) 0.3930(43)
_E_ 2 _JJ_ ∗ 10 [9] 0.07826(71) 0.0935(16) 0.0928(19) 0.1222(28)
_E_ 2 _JK_ ∗ 10 [9] -21.80(20) -19.53(34) -29.19(32) -18.93(28)
_E_ 4 ∗ 10 [6] -5.215(60) -6.29(12) -3.533(63) -1.8968(74)
_E_ 4 _J_ ∗ 10 [9] 0.1756(13) 0.1959(27) 0.2005(28) 0.2708(34)


Coriolis coupling constants


_F_ _bc_ -5.7926(14) -5.9589(18) -5.77100(11) -3.32962(35)
_F_ _bcK_ ∗ 10 [3] 43.41(74) 56.41(92) 31.77(59) -112.97(28)
_F_ _bcJ_ ∗ 10 [3] -0.113411(86) -0.115675(85) -0.11216(10) -0.46075(94)
_F_ _bcKK_ ∗ 10 [6] -19.08(43) -12.27(24) -25.60(32) 38.69(80)
_F_ _bcJK_ ∗ 10 [6] 0.4789(72) 0.3470(77) 0.517(11)
_F_ _bcJJ_ ∗ 10 [6] 0.014149(81)
_F_ 2 _bc_ ∗ 10 [6] 86.5(14) 116.7(19) 62.3(11) -22.135(52)
_F_ _ac_ 75.52596(18) 73.71299(25) 75.01253(25) 136.707(18)
_F_ _acJ_ ∗ 10 [3] -0.05771(28) -0.07313(36) -0.05196(44)
_F_ _acK_ ∗ 10 [3] 9.943(25) 10.099(30) 9.835(36) 19.91(91)
_F_ _acJK_ ∗ 10 [6] 0.485(16) 0.185(16) 0.193(16)
_F_ _acKK_ ∗ 10 [6] -9.229(30) -8.740(29) -8.798(37) -34.37(42)


Number of distincts lines 5128 3403 3235 3190

Number of parameters 47 45 44 44
Standard deviation (in kHz) _J_ _max_ [′′], _K_ _a_ [′′], _max_ 75, 2529.2 67, 2526.3 63,2628.7 60,2126.3

Weighted deviation 0.931 0.855 0.916 0.875


_a_ Margulès et al. (2017); _b_ Number in parentheses is one standard deviation in unit of the last digit; _c_ Fixed to main isotopologue value



of α _J_ 2000 = 18:29:49.80, δ _J_ 2000 = +01:15:20.6. Selected frequency
windows in Band 6 between 217 and 235 GHz were targeted. A
synthetic beam of approximately 1.2” was employed, which is insufficient to resolve the hot corino. Analysis of an extracted spectrum
towards the SMM1-a continuum peak in a single beam with the


MNRAS **000**, 1–8 (2023)



CASSIS [3] line analysis software resulted in the detection of sev

3 Based on analysis carried out with the CASSIS software
(http://cassis.irap.omp.eu; (Vastel et al. 2015) and JPL database for
molecular spectroscopy (Pickett et al. 1998) and the Cologne Database for


# ACCEPTED MANUSCRIPT / CLEAN COPY

_Spectroscopy for HOCH_ 2 _CN isotopologues_ 5


**Table 2.** Comparison of experimental and ab initio parameters in MHz


Parameters HO [13] CH 2 CN HOCH [13] 2 [CN] DOCH 2 CN


this work ab initio _[a]_ this work ab initio this work ab initio Cazzoli et al. _[c]_


_A_ 32787.31523(44) _[b]_ 32800.04 33569.30468(40) 33579.15 30653.94661(70) 30666.47 30651.04(22)

_B_ 4820.980561(79) 4811.81 4810.878790(83) 4801.98 4725.725505(99) 4716.15 4726.75(22)
_C_ 4349.083413(75) 4342.59 4354.399428(80) 4348.01 4262.86028(24) 4255.64 4262.36(22)

_E_ 112016.5659(48) 95334.00 112716.4480(55) 96533.17 17567.061(10) 15.289.42 16749.57


_a_ Dalbouha et al. (2017); _b_ Number in parentheses is one standard deviation in unit of the last digit; _c_ Cazzoli et al. (1973)


**Table 3.** Measured frequencies of the HO [13] CH 2 CN isotopologue and residuals from the fit (full fit is available at the CDS: S1)


Upper level Lower level Frequency(Unc.) o.-c.
_J_ ” _K_ _a_ ” _K_ _c_ ” _v_ _t_ ” a _J_ [′] _K_ _a_ [′] _K_ _c_ [′] _v_ [′] _t_ _[a]_ (in MHz) (in MHz)


61 1 60 1 60 1 59 1 539819.787(0.030) -0.000

61 2 60 1 60 1 59 1 539863.767(0.030) 0.004

60 3 58 1 59 2 57 1 539875.463(0.030) -0.031

61 1 60 0 60 2 59 0 539908.910(0.030) -0.009

19 7 12 0 18 6 13 0 539943.488(0.030) 0.002

19 7 13 0 18 6 12 0 539943.488(0.030) 0.030

61 2 60 0 60 2 59 0 539950.533(0.030) -0.042

61 1 60 0 60 1 59 0 539959.986(0.030) -0.002

58 4 54 1 57 4 53 1 539974.592(0.030) 0.040

60 3 58 0 59 2 57 0 539977.449(0.030) -0.030


_a_ following SPFIT format the torsional substates _A_ 1 and _A_ 2 are labeled 0 and 1, respectively


**Table 4.** Measured frequencies of the HOCH [13] 2 [CN isotopologue and residuals from the fit (full fit is available at the CDS: S2)]


Upper level Lower level Frequency(Unc.) o.-c.
_J_ ” _K_ _a_ ” _K_ _c_ ” _v_ _t_ ” a _J_ [′] _K_ _a_ [′] _K_ _c_ [′] _v_ [′] _t_ _[a]_ (in MHz) (in MHz)


45 5 40 0 44 4 40 1 527413.846(0.03000) -0.032

33 3 30 1 32 2 30 0 527665.846(0.03000) 0.079

52 4 49 1 51 3 48 1 527765.891(0.03000) 0.036

58 4 55 1 57 4 54 1 528239.640(0.03000) -0.001

58 4 55 0 57 4 54 0 528436.677(0.03000) 0.042

56 8 49 1 56 7 49 0 528606.153(0.03000) -0.063

17 5 12 1 16 4 12 0 528611.553(0.03000) -0.023

17 5 13 1 16 4 13 0 528642.147(0.03000) -0.056

23 6 17 0 22 5 18 0 528776.749(0.03000) 0.047

23 6 17 1 22 5 18 1 528984.733(0.03000) 0.057


_a_ following SPFIT format the torsional substates _A_ 1 and _A_ 2 are labeled 0 and 1, respectively


**Table 5.** Measured frequencies of the DOCH 2 CN isotopologue and residuals from the fit (full fit is available at the CDS: S3)


Upper level Lower level Frequency(Unc.) o.-c.
_J_ ” _K_ _a_ ” _K_ _c_ ” _v_ _t_ ” a _J_ [′] _K_ _a_ [′] _K_ _c_ [′] _v_ [′] _t_ _[a]_ (in MHz) (in MHz)


20 7 13 0 19 6 14 0 519153.053(0.03000) -0.021

20 7 14 0 19 6 13 0 519153.053(0.03000) 0.044

20 7 13 1 19 6 14 1 519208.530(0.03000) -0.064

20 7 14 1 19 6 13 1 519208.530(0.03000) 0.000

30 5 26 1 29 4 26 0 519570.812(0.03000) -0.001

24 6 18 1 23 5 18 0 519677.999(0.03000) 0.033

24 6 19 1 23 5 19 0 519704.748(0.03000) 0.066

57 4 53 1 56 4 52 1 519765.867(0.03000) 0.024

57 4 53 0 56 4 52 0 519853.924(0.03000) -0.079

56 4 53 1 55 3 52 1 519863.089(0.03000) 0.012

59 3 57 0 58 2 56 0 519888.201(0.03000) 0.026


_a_ following SPFIT format the torsional substates _A_ 1 and _A_ 2 are labeled 0 and 1, respectively


MNRAS **000**, 1–8 (2023)
# ACCEPTED MANUSCRIPT / CLEAN COPY

6 _L. Margulès et al._


**Table 6.** Rotational, vibrational, and total partition functions of 2-hydroxyacetonitrile isotopologues at various temperatures.


HO [13] CH 2 CN HOCH [13] 2 [CN] DOCH 2 CN
_T_ (K) _Q_ rot (T) _Q_ vib (T) _Q_ tot (T) _[a]_ _Q_ rot (T) _Q_ vib (T) _Q_ tot (T) _[a]_ _Q_ rot (T) _Q_ vib (T) _Q_ tot (T) _[a]_


300 66349.366 2.945 195427.600 65599.953 2.983 195705.692 70508.718 3.448 243084.660

225 43025.987 1.938 83402.987 42538.671 1.955 83169.251 45852.122 2.201 100939.594

150 23269.950 1.316 30624.476 23005.366 1.321 30395.412 24923.049 1.428 35588.472

75 8080.026 1.028 8303.656 7987.232 1.028 8212.221 8781.574 1.047 9198.324

37.5 2762.515 1.000 2763.682 2730.231 1.000 2731.423 3088.620 1.001 3092.371

18.75 917.588 1.000 917.588 906.545 1.000 906.545 1081.656 1.000 1081.657

9.375 290.775 1.000 290.775 287.126 1.000 287.126 375.515 1.000 375.515


_a_ _Q_ tot (T) values are calculated without truncation of _Q_ rot (T) and _Q_ vib (T) at the third digit



eral prebiotic molecules, including HOCH 2 CN. Hydroxyacetonitrile
was detected at _N_ _Tot_ = (7.4±0.9)×10 [14] cm [−][2], _T_ ex = 260±45 K,
∆ _V_ 2.5±0.3 km.s [−][1], and _V_ LSR = 6.8±0.2 km.s [−][1] (Ligterink et al.
2021). To identify the isotopologues, their lines are searched within
a 3 S/N detection. Upon identification, a synthetic spectrum is fitted
to these lines, assuming Local Thermodynamic Equilibrium (LTE)
conditions. If no lines are detected, the upper limit column density
of an isotopologue is determined in line-free spectral regions where
a transition of said isotopologue is located. The parameters _T_ ex, ∆ _V_,
and _V_ LSR are adopted from the main isotopologue. In the SMM1-a
spectra, the three hydroxyacetonitrile isotopologues are not detected.
Several of their undetected transitions are presented in Figures 1, 2,
3, for DOCH 2 CN, HO [13] CH 2 CN and HOCH [13] 2 [CN, respectively. Due]
to the line-richness of the spectrum, it is difficult to find completely
line free spectral regions. For HO [13] CH 2 CN, blended line features
seem to be present in the observed spectrum, but these can both be
attributed to CH 3 COOH. The 26 2,25 ← 25 2,24 transition of the synthetic HOCH [13]
2 [CN spectrum blends in the wing with a CH] [3] [CDO line]
in the observed spectrum. Due to the issues in determining line free
spectral regions, a conservative estimate of the upper limit column
density is given. For DOCH 2 CN _N_ _tot_ ≤ 1 × 10 [14] cm [−][2], while for
both [13] C isotopologues it is set a _N_ _tot_ ≤ 2 × 10 [14] cm [−][2] . This
results in [isotopologue]/[HOCH 2 CN] ratios of ≤ 0.14 and ≤ 0.27
for the deuterated and [13] C hydroxyacetonitrile isotopologues, respectively. Part of the reason that the isotopologues of HOCH 2 CN
are not detected lies in the fact that the spectral windows of the
SMM1-a observations miss the most of the strongest transitions of
these species. Figure 4 shows the normalized synthetic spectra of
DOCH 2 CN, HO [13] CH 2 CN and HOCH [13] 2 [CN at] _[ T]_ [ex] [ = 260 K, with the]
location of the spectral windows indicated. Only several DOCH 2 CN
lines are covered in the low resolution continuum band between

234.06 and 235.93 GHz. Follow-up observations with ALMA that
target the strongest isotopologue transition at higher sensitivity will
presumably be more successful in detecting these species.


**4.2** **IRAS16293 B**


HOCH 2 CN has also been detected towards the low-mass protostar
IRAS16293 B (Zeng et al. 2019; Ligterink et al. 2021). Contrary
to SMM1-a, a large spectral range (329–363 GHz) has been covered for this source in the framework of the ALMA-PILS survey,
which is fully described in Jørgensen et al. (2016). Faint lines of
hydroxyacetonitrile lines were identified at the so-called half-beam
offset position (Ligterink et al. 2021). We consequently searched
for the [13] C isotopologues at the same position. No lines of the [13] C


Molecular Spectroscopy (Müller et al. 2001, 2005; Endres et al. 2016).
CASSIS has been developed by IRAP-UPS/CNRS.


MNRAS **000**, 1–8 (2023)



**Table 7.** Derived isotopic ratios towards IRAS16293B and SMM1-a.


Source SMM1-a IRAS16293B


13 C/ 12 C ≲ 0.27 ≲ 0.5

D/H ≲ 0.14 ≲ 0.5


isotopologues are detected. Assuming an excitation temperature of
150 K (similar to the one obtained by Zeng et al. 2019), a source
size of 0.5 [′′], a linewidth ∆ _V_ = 1 km s [−][1], and a _V_ LSR = 2.7 km.s [−][1],
we derive an upper limit of 1.5×10 [15] cm [−][2] for both HO [13] CH 2 CN
and HOCH [13] [The] [upper] [limit] [would] [be] [lower] [if] [the] [excitation]
2 [CN.]
temperature is higher. Using the column density of 3×10 [15] cm [−][2]

derived for the main isotopologue by Ligterink et al. (2021), we
obtain a [13] C/ [12] C ≤ 0.5. DOCH 2 CN was also searched for in the
PILS survey but is undetected with a column density lower than
1.5×10 [15] cm [−][2] for _T_ ex = 150 K. This leads to an upper limit for
the D/H ratio of 50%, which is well above the values derived for the
mono-deuterated isotopologues of other complex organic molecules
in this source with the same survey: 1-8% (Coutens et al. 2016, 2018;
Jørgensen et al. 2018; Persson et al. 2018; Müller et al. 2023). Given
the lower constraints obtained for IRAS16293 B and the small spectral range covered by the observations of SMM1-a so far, it appears
that SMM1-a would be a better target for follow-up observations.
As Zeng et al. (2019) identified clearer lines of HOCH 2 CN towards
IRAS16293 B with larger angular resolution observations, we also
checked the ALMA archive data with angular sizes between 1 and
2 [′′] . We used the ATOMIS [4] web application to search for the three
isotopologues in the archival ALMA data with the following request:
an angular resolution between 1 and 2 [′′], a spectral resolution better
than 0.5 km s [−][1], and a sensitivity better than 6 mJy beam [−][1] for a
bin width of 1 km s [−][1] . We restricted the search to the Bands 3, 4,
5, and 6 similarly to Zeng et al. (2019) and we only looked at the
transitions with an _A_ ij higher than 5 × 10 [−][5] s [−][1] . We found that one
transition of HOCH [13] [and] [two] [transitions] [of] [HO] [13] [CH] [2] [CN] [at]
2 [CN]
139.5831, 139.6833, and 139.8175 GHz, respectively, are covered in
the project 2013.1.00352.S. Multiple transitions of DOCH 2 CN are
covered in the project 2018.1.01496.S. We visualize the fits cubes
provided on the ALMA archive with Aladin [5] and CASSIS. The
HOCH [13] [line] [at] [139.5831] [GHz] [is] [blended] [with] [a] [CH] [3] [COCH] [3]
2 [CN]
line. The two transitions of HO [13] CH 2 CN are within the noise. No


4 ATOMIS (ALMA archive Tool for Molecular Investigations in Space) is
developed at IRAP-UPS/CNRS in the framework of the ERC starting grant
Chemtrip (grant agreement No 949278)
5 `[https://aladin.u-strasbg.fr/AladinDesktop/](https://aladin.u-strasbg.fr/AladinDesktop/)`


# ACCEPTED MANUSCRIPT / CLEAN COPY

DOCH 2 CN - Serpens SMM1-a


2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



_Spectroscopy for HOCH_ 2 _CN isotopologues_ 7


HO [13] CH 2 CN - Serpens SMM1-a


2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



26 2, 25, 0 25 2, 24, 0

|Col1|255, 20, 0 264, 23, 0<br>020<br>.<br>172K<br>015<br>.<br>010<br>.<br>005<br>.|254, 22, 0<br>04 1<br>.<br>(K)<br>02<br>.<br>B<br>T<br>00<br>.|262, 25, 1 2<br>64K|Col5|
|---|---|---|---|---|
|005<br>0.00<br>_T_|005<br>0.00|005<br>0.00||0.0|


2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0

F r e q u e n c y H z



235600 235610 235620


2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



234330 234340 234350 234530 234540 234550
Frequency (MHz)


2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



235540 235550 235560


2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



**Figure** **1.** ALMA spectrum of SMM1-a (black) and a synthetic spectrum
of DOCH 2 CN (blue). Two undetected and largely unblended transitions are
shown from which the upper limit column density of ≤ 1×10 [14] cm [−][2] is determined. Other synthetic spectrum parameters are adopted from the main isotopologue HOCH 2 CN detection towards SMM1-a and are fixed at _T_ ex = 260
K, ∆ _V_ = 2.5 km.s [−][1], and _V_ LSR = 6.8 km.s [−][1] . The upper state energy of each
transition is indicated in the top left corner.


2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



Frequency (MHz)


**Figure** **3.** ALMA spectrum of SMM1-a (black) and a synthetic spectrum
of HO [13] CH 2 CN (blue). Two undetected and largely unblended transitions
are shown from which the upper limit column density of ≤ 2 × 10 [14] cm [−][2]

is determined. Other synthetic spectrum parameters are adopted from the
main isotopologue HOCH 2 CN detection towards SMM1-a and are fixed at
_T_ ex = 260 K, ∆ _V_ = 2.5 km.s [−][1], and _V_ LSR = 6.8 km.s [−][1] . The upper state
energy of each transition is indicated in the top left corner. Both transitions
are blended with CH 3 COOH lines.


2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



|Col1|CH13CN S<br>2 -<br>243211|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|0.05<br>0.10<br>0.15<br>0.20<br>162 K<br>,,<br>_TB_ (K)|,,|0.05<br>0.10<br>0.15<br>0.20<br>164 K<br>,,|<br>,,<br> <br> <br> <br>||<br>  <br> <br>  <br>|
|231870 231880 231890<br>0.05<br>0.00<br>235620 235630 235640<br>0.05<br>0.00<br>Frequency (MHz)<br>**re 2.** ALMA spectrum of SMM1-a (black) and a synthetic spectrum<br>OCH13<br>CN(blue).Twoundetectedandlargelyunblendedtransitions<br> <br> <br> <br> <br>|||||<br>|
|231870 231880 231890<br>0.05<br>0.00<br>235620 235630 235640<br>0.05<br>0.00<br>Frequency (MHz)<br>**re 2.** ALMA spectrum of SMM1-a (black) and a synthetic spectrum<br>OCH13<br>CN(blue).Twoundetectedandlargelyunblendedtransitions<br> <br> <br> <br> <br>||||||
|231870 231880 231890<br>0.05<br>0.00<br>235620 235630 235640<br>0.05<br>0.00<br>Frequency (MHz)<br>**re 2.** ALMA spectrum of SMM1-a (black) and a synthetic spectrum<br>OCH13<br>CN(blue).Twoundetectedandlargelyunblendedtransitions<br> <br> <br> <br> <br>||||||


are shown from which the upper limit column density of ≤ 2×10 [14] cm [−][2] 2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0

is determined. Other synthetic spectrum parameters are adopted from the F r e q u e n c y H z
main isotopologue HOCH 2 CN detection towards SMM1-a and are fixed at
_T_ ex = 260 K, ∆ _V_ = 2.5 km.s [−][1], and _V_ LSR = 6.8 km.s [−][1] . The upper state
energy of each transition is indicated in the top left corner. The 26 2,25 â 25 2,24
transition is blended in the wing with a CH 3 CDO transition.


DOCH 2 CN line is detected either. This confirms that SMM1-a could
be a better target for future studies.


**5** **CONCLUSION**


Millimeter and submillimeter wave spectra of three 2hydroxyacetonitrile isotopologues, HO [13] CH 2 CN, HOCH [13] 2 [CN] [and]
DOCH 2 CN, were assigned up to 530 GHz. This has allowed us
to produce accurate predictions of the spectra and made possible
a search for these isotopologues in the ISM. Only non-detections
could be reported in this work toward SMM1-a and IRAS16293 B
with no significant constraints on the [13] C/ [12] C and D/H ratios of
this molecule. The spectroscopic predictions are now available to
the astrophysical community, enabling future searches for these 2hydroxyacetonitrile isotopologues as more sensitive surveys become
available.



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y ( H z


**Figure 4.** Normalized synthetic spectra of HOCH [13] 2 [CN (blue), HO] [13] [CH] [2] [CN]
(red), and DOCH 2 CN (black) for _T_ ex = 260 K, ∆V = 2.5 km.s [−][1], and
V _LS R_ = 6.8 km.s [−][1] together with the locations of the spectral windows of the
SMM1-a observations (grey). With the exception of a number of DOCH 2 CN
lines covered by the continuum window, the strongest and most prominent
transitions of these hydroxyacetonitrile isotopologues are not covered by the

observations.


**ACKNOWLEDGEMENTS**


This work was supported by the CNRS through the MITI interdisciplinary programs. A.C. received financial support from the
European Research Council (ERC) under the European Unions
Horizon 2020 research and innovation programme (ERC Starting
Grant Chemtrip, grant agreement No 949278). J.C.G. thanks
the Centre National d’Etudes Spatiales (CNES) for a grant.
N.F.W.L. acknowledges funding by the Swiss National Science
Foundation Ambizione grant 193453. This paper makes use of
the following ALMA data: ADS/JAO.ALMA2013.1.00278.S,
ADS/JAO.ALMA2018.1.00836.S and

ADS/JAO.ALMA2013.1.00352.S. ALMA is a partnership of
ESO (representing its member states), NSF (USA) and NINS
(Japan), together with NRC (Canada), NSC and ASIAA (Taiwan),
and KASI (Republic of Korea), in cooperation with the Republic



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z



2 1 5 0 0 2 2 0 0 0 2 2 5 0 0 2 3 0 0 0 2 3 5 0 0 2 4 0 0 0


F r e q u e n c y H z


MNRAS **000**, 1–8 (2023)
# ACCEPTED MANUSCRIPT / CLEAN COPY

8 _L. Margulès et al._


of Chile. The Joint ALMA Observatory is operated by ESO,
AUI/NRAO and NAOJ


**DATA AVAILABILITY**


Owing to their large size, the complete versions of the global fit (Tables S1, S2 and S3) for the three isotopologues are supplied at the
CDS [6] . The predicted spectra are available in different formats including standard .cat format (Pickett 1972) from the new database of the
Lille spectroscopy group called the Lille Spectroscopic Database [7] .


**REFERENCES**


Cazzoli G., Lister D., Mirri A., 1973, Journal of the Chemical Society, Faraday
Transactions 2: Molecular and Chemical Physics, 69, 569
Christen D., Müller H. S., 2003, Physical Chemistry Chemical Physics, 5,
3600

Coudert L., Hougen J., 1988, Journal of Molecular Spectroscopy, 130, 86
[Coutens A., et al., 2016, A&A, 590, L6](http://dx.doi.org/10.1051/0004-6361/201628612)

[Coutens A., et al., 2018, A&A, 612, A107](http://dx.doi.org/10.1051/0004-6361/201732346)
[Dalbouha S., Domínguez-Gómez R. M., Senent M. L., 2017, The European](http://dx.doi.org/10.1140/epjd/e2017-70748-y)
[Physical Journal D, 71](http://dx.doi.org/10.1140/epjd/e2017-70748-y)
[Danger G., Duvernay F., Theulé P., Borget F., Chiavassa T., 2012, ApJ, 756,](http://dx.doi.org/10.1088/0004-637x/756/1/11)

11

[Endres C. P., Schlemmer S., Schilke P., Stutzki J., Müller H. S., 2016, Journal](http://dx.doi.org/https://doi.org/10.1016/j.jms.2016.03.005)
[of Molecular Spectroscopy, 327, 95](http://dx.doi.org/https://doi.org/10.1016/j.jms.2016.03.005)
Gaudry R., 1947, Organic Syntheses, 27, 41
Gaudry R., 1955, Organic Syntheses, 3, 436
Gordy W., Cook R. L., Weissberger A., 1984, Microwave molecular spectra.
Vol. 18, Wiley New York
[Halfen D. T., Woolf N. J., Ziurys L. M., 2017, ApJ, 845, 158](http://dx.doi.org/10.3847/1538-4357/aa816b)
Hougen J. T., 1985, Journal of Molecular Spectroscopy, 114, 395
Jacob A. M., Menten K. M., Wiesemeyer H., Güsten R., Wyrowski F., Klein
[B., 2020, A&A, 640, A125](http://dx.doi.org/10.1051/0004-6361/201937385)
[Jørgensen J. K., et al., 2016, A&A, 595, A117](http://dx.doi.org/10.1051/0004-6361/201628648)
[Jørgensen J. K., et al., 2018, A&A, 620, A170](http://dx.doi.org/10.1051/0004-6361/201731667)
[Ligterink N. F. W., et al., 2021, A&A, 647, A87](http://dx.doi.org/10.1051/0004-6361/202039619)
Margulès L., McGuire B. A., Senent M. L., Motiyenko R. A., Remĳan A.,
[Guillemin J. C., 2017, A&A, 601, A50](http://dx.doi.org/10.1051/0004-6361/201628551)
Margulès L., McGuire B. A., Evans C. J., Motiyenko R. A., Remĳan A.,
[Guillemin J. C., Wong A., McNaughton D., 2020, A&A, 642, A206](http://dx.doi.org/10.1051/0004-6361/202038230)
Motiyenko R. A., Margulès L., Goubet M., Møllendal H., Konovalov A.,
[Guillemin J.-C., 2010, The Journal of Physical Chemistry A, 114, 2794](http://dx.doi.org/10.1021/jp912082b)
Motiyenko R. A., Margulès L., Alekseev E. A., Guillemin J.-C., 2015, [The](http://dx.doi.org/10.1021/jp512625s)
[Journal of Physical Chemistry A, 119, 1048](http://dx.doi.org/10.1021/jp512625s)
Motiyenko R. A., Margulès L., Senent M. L., Guillemin J.-C., 2018, The
Journal of Physical Chemistry A, 122, 3163
[Müller H. S. P., Thorwirth S., Roth D. A., Winnewisser G., 2001, A&A, 370,](http://dx.doi.org/10.1051/0004-6361:20010367)

L49

[Müller H. S., Schlöder F., Stutzki J., Winnewisser G., 2005, Journal of Molec-](http://dx.doi.org/https://doi.org/10.1016/j.molstruc.2005.01.027)

[ular Structure, 742, 215](http://dx.doi.org/https://doi.org/10.1016/j.molstruc.2005.01.027)

[Müller H. S., Belloche A., Menten K. M., Comito C., Schilke P., 2008, Journal](http://dx.doi.org/https://doi.org/10.1016/j.jms.2008.03.016)
[of Molecular Spectroscopy, 251, 319](http://dx.doi.org/https://doi.org/10.1016/j.jms.2008.03.016)
Müller H. S. P., Jørgensen J. K., Guillemin J.-C., Lewen F., Schlemmer S.,
[2023, MNRAS, 518, 185](http://dx.doi.org/10.1093/mnras/stac2525)
[Ortiz-León G. N., et al., 2017, ApJ, 834, 143](http://dx.doi.org/10.3847/1538-4357/834/2/143)
Parise B., Castets A., Herbst E., Caux E., Ceccarelli C., Mukhopadhyay I.,
[Tielens A. G. G. M., 2004, A&A, 416, 159](http://dx.doi.org/10.1051/0004-6361:20034490)

[Persson M. V., et al., 2018, A&A, 610, A54](http://dx.doi.org/10.1051/0004-6361/201731684)
Pickett H. M., 1972, J. Chem. Phys., 56, 1715
Pickett H. M., 1991, Journal of Molecular Spectroscopy, 148, 371


6 https://cds.unistra.fr
7 https://lsd.univ-lille.fr


MNRAS **000**, 1–8 (2023)



Pickett H., Poynter R., Cohen E., Delitsky M., Pearson J., Müller H., 1998,

[J. Quant. Spectrosc. Radiative Transfer, 60, 883](http://dx.doi.org/https://doi.org/10.1016/S0022-4073(98)00091-0)
Roueff E., Lis D. C., van der Tak F. F. S., Gerin M., Goldsmith P. F., 2005,

[A&A, 438, 585](http://dx.doi.org/10.1051/0004-6361:20052724)

Schwartz A. W., Goverde M., 1982, Journal of molecular evolution, 18, 351
Smirnov I., Alekseev E., Piddyachiy V., Ilyushin V., Motiyenko R., 2013,

[Journal of Molecular Spectroscopy, 293–294, 33](http://dx.doi.org/http://dx.doi.org/10.1016/j.jms.2013.10.001)
Vastel C., Bottinelli S., Caux E., Glorian J., Boiziot M., 2015, in SF2A-2015:
Proceedings of the Annual meeting of the French Society of Astronomy
and Astrophysics. pp 313–316
[Wilson T. L., Rood R. T., 1994, ARA&A, 32, 191](http://dx.doi.org/10.1146/annurev.aa.32.090194.001203)
[Zakharenko O., Motiyenko R. A., Margulès L., Huet T. R., 2015, Journal of](http://dx.doi.org/https://doi.org/10.1016/j.jms.2015.09.005)
[Molecular Spectroscopy, 317, 41](http://dx.doi.org/https://doi.org/10.1016/j.jms.2015.09.005)
Zeng S., Quénard D., Jiménez-Serra I., Martí n Pintado J., Rivilla V. M., Testi
[L andMartí n-Domé nech R., 2019, MNRAS, 484, L43](http://dx.doi.org/10.1093/mnrasl/slz002)


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


# ACCEPTED MANUSCRIPT / CLEAN COPY


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].coordinates.evidence[1]",
  "value": "18:29:49.80 +01:15:20.6 (J2000)",
  "failed_quote": "Recently, this source was targeted with ALMA towards a phase centre of α J 2000 = 18:29:49.80, δ J 2000 = +01:15:20.6."
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[1]",
  "value": "436±10 pc",
  "failed_quote": "Recently, this source was targeted with ALMA towards a phase centre of α J 2000 = 18:29:49.80, δ J 2000 = +01:15:20.6."
 },
 {
  "path": "science.targets[0].distance_source.evidence[1]",
  "value": "Ortiz-León et al. 2017",
  "failed_quote": "Recently, this source was targeted with ALMA towards a phase centre of α J 2000 = 18:29:49.80, δ J 2000 = +01:15:20.6."
 },
 {
  "path": "analysis_steps[0].assumptions[0].evidence[0]",
  "value": "Some octic distortion constants (L_K, l_2, l_3) for 13C isotopologues fixed to main isotopologue values; dipole moments taken from ab initio calculations (µ_a = 2.32 D, µ_b = 1.31 D, µ_c = 1.23 D)",
  "failed_quote": "Some of the octic distortion constants which could not be determined better than 10 times their standard deviation were kept fixed at the main isotopologue values."
 },
 {
  "path": "software[2].used_for.evidence[0]",
  "value": "Line analysis, LTE synthetic spectrum modeling, and visualizing ALMA archival FITS cubes",
  "failed_quote": "Analysis of an extracted spectrum towards the SMM1-a continuum peak in a single beam with the CASSIS 3 line analysis software resulted in the detection of several prebiotic molecules, including HOCH 2 CN."
 }
]
```
