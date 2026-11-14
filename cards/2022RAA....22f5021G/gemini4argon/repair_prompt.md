# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2022RAA....22f5021G\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Research in Astronomy and Astrophysics


**RESEARCH PAPER**

# Phenol in High-mass Star-forming Regions


To cite this article: Rana Ghosh et al 2022 Res. Astron. Astrophys. 22 065021


View the [article online](https://doi.org/10.1088/1674-4527/ac6aa9) for updates and enhancements.



You may also like










[Laser-Induced Hydrogen Evolution Using](https://iopscience.iop.org/article/10.1149/MA2015-01/8/832)
[Metal-Free Single-Walled Carbon](https://iopscience.iop.org/article/10.1149/MA2015-01/8/832)
[Nanotubes](https://iopscience.iop.org/article/10.1149/MA2015-01/8/832)
Kei Ohkubo, Naoki Kohno, Yusuke
Yamada et al.


[Very low energy electron scattering in](https://iopscience.iop.org/article/10.1088/0953-4075/32/11/317)
[C](https://iopscience.iop.org/article/10.1088/0953-4075/32/11/317) ~~6~~ [H](https://iopscience.iop.org/article/10.1088/0953-4075/32/11/317) ~~5~~ [F, C](https://iopscience.iop.org/article/10.1088/0953-4075/32/11/317) ~~6~~ [H](https://iopscience.iop.org/article/10.1088/0953-4075/32/11/317) ~~5~~ [Cl, C](https://iopscience.iop.org/article/10.1088/0953-4075/32/11/317) ~~6~~ [H](https://iopscience.iop.org/article/10.1088/0953-4075/32/11/317) ~~5~~ [Br and C](https://iopscience.iop.org/article/10.1088/0953-4075/32/11/317) ~~6~~ [H](https://iopscience.iop.org/article/10.1088/0953-4075/32/11/317) ~~5~~ [I](https://iopscience.iop.org/article/10.1088/0953-4075/32/11/317)
S L Lunt, D Field, S V Hoffmann et al.


[Detection of C](https://iopscience.iop.org/article/10.1086/521979) ~~6~~ [H](https://iopscience.iop.org/article/10.1086/521979) [–] [toward the Low-Mass](https://iopscience.iop.org/article/10.1086/521979)
[Protostar IRAS 04368+2557 in L1527](https://iopscience.iop.org/article/10.1086/521979)
Nami Sakai, Takeshi Sakai, Yoshihiro
Osamura et al.



This content was downloaded from IP address 176.227.240.31 on 28/10/2026 at 11:50

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June [https://doi.org/10.1088/1674-4527/ac6aa9](https://doi.org/10.1088/1674-4527/ac6aa9)


© 2022. National Astronomical Observatories, CAS and IOP Publishing Ltd. Printed in China and the U.K.

All rights, including for text and data mining, AI training, and similar technologies, are reserved.

# Phenol in High-mass Star-forming Regions


Rana Ghosh [1], Milan Sil [2][,][1], Suman Kumar Mondal [1], Prasanta Gorai [3], Dipen Sahu [4], Rahul Kumar Kushwaha [5],

1 Indian Centre for Space Physics, Bhalamurugan 43 Chalantika, Sivaraman Garia Station [6], Road, and Kolkata Ankan 700084, Das [1] India; [ankan.das@gmail.com](mailto:ankan.das@gmail.com)
2 S. N. Bose National Centre for Basic Sciences, Salt Lake, Kolkata 700106, India
3 Department of Space, Earth & Environment, Chalmers University of Technology, SE-412 96 Gothenburg, Sweden
4 Institute of Astronomy and Astrophysics Academia Sinica Taipei, Taipei 10617, China
5 Atomic and Molecular Physics Laboratory, Institute for Nuclear Research (Atomki), Debrecen H-4026, Hungary
6 Physical Research Laboratory, Navrangpura, Ahmedabad 380009, India
Received 2022 March 13; accepted 2022 April 11; published 2022 June 6


Abstract


Phenol, which belongs to the C 6 H 6 O isomeric group, is the simplest molecule in the family of alcohol of the aromatic
series. Although phenol has yet to be detected in the interstellar medium, a tentative identification was reported toward
the Orion KL hot core using the IRAM-30 m line survey. To explore some more species of this isomeric group, we
consider ten species to study the fate of their astronomical detection. It is noticed that phenol is the most energetically
favorable isomer of this group. In contrast, propargyl ether is the least favorable (having relative energy ∼103
kcal mol [−][1] compared to phenol) species of this group. So far, the studies associated with the formation of phenol are
heavily concentrated on combustion chemistry. Here, we suggest a few key reactions (C 6 H 6 + OH → C 6 H 5 + H 2 O,
C 6 H 6 + O → C 6 H 5 OH, C 6 H 6 + H → C 6 H 5 + H 2, and C 6 H 5 + OH → C 6 H 5 OH + hν) for the formation of phenol. All
these pathways are included in a large gas-grain chemical network to study its formation in high mass star-forming
regions and dark cloud environments. It is noticed that the phenyl (−C 6 H 5 ) formation by the ice-phase hydrogen
abstraction reaction of benzene (i.e., C 6 H 6 + OH → C 6 H 5 + H 2 O if allowed at ∼10 K) could serve as the starting point
for the formation of phenol in the gas phase by radiative association reaction C 6 H 5 + OH → C 6 H 5 OH + hν. The gasphase reaction C 6 H 6 + O → C 6 H 5 OH significantly contributes to the formation of phenol, when the ice-phase reaction
C 6 H 6 + OH → C 6 H 5 + H 2 O is not considered at low temperature. Band 4 ALMA archival data of a hot molecular
core, G10.47+0.03, are analyzed. It yields an upper limit on phenol abundance of 5.19 × 10 [−][9] . Our astrochemical
model delivers an upper limit on phenol abundance of ∼2.20 × 10 [−][9] in the hot molecular core, whereas its production
in the dark cloud is not satisfactory.


Key words: astrochemistry – ISM: abundances – ISM: molecules – (ISM:) evolution



1. Introduction


Theoretically, the presence of aromatic molecules in the
interstellar medium (ISM) has yet to be fully understood.
However, the recent discovery of benzonitrile ( c - C 6 H 5 CN ) in
a nearby molecular cloud (TMC-1) marks the first radio detection
of an aromatic species in the ISM (McGuire et al. 2018). It is
suggested that c - C 6 H 5 CN can be a proxy of benzene
(c − C 6 H 6 ) at a low-temperature (Cooke et al. 2020), which is
the simplest aromatic molecule and plays a significant role in
interstellar chemistry. Furthermore, the phenyl radical (−C 6 H 5 )
derived from the benzene by a hydrogen abstraction could be a
possible progenitor of the formation of other new aromatic
species. Various cyclic hydrocarbons, such as ethynyl cyclopropenylidene (c − C 3 HCCH), cyclopentadiene (c − C 5 H 6 ), and
indene (c − C 9 H 8 ), in the cold dark cloud TMC-1 were recently
discovered (Burkhardt et al. 2021; Cernicharo et al. 2021a). Later
on, two isomers of ethynyl cyclopentadiene (c − C 5 H 5 CCH)
were detected and a tentative detection of ethynyl benzene



(C 6 H 5 CCH) was reported by Cernicharo et al. (2021b). Various
other cyclic cyano derivatives were observed by Lee et al. (2021),
McCarthy et al. (2021), McGuire et al. (2021). It is astonishing to
see the presence of such cyclic hydrocarbons in a cold starless
region like TMC-1. It imposes a new challenge to reconstruct a
chemical model to explain their observed abundances.
Phenol (C 6 H 5 OH) belongs to the alcohol family in aromatic
series. It contains the hydroxyl (−OH) group directly to the sp [2]

hybridized carbon atom of the aromatic phenyl ring. Due to the
internal rotation of the −OH group, it becomes an exciting
candidate to explore from an astrochemist’s point of view. The
microwave spectrum of phenol was initially measured by
Kojima (1960) in the frequency range of 15–30 GHz. Later on,
Forest & Dailey (1966) determined the equilibrium structure of
phenol by analyzing the rotational spectra of C 6 H 185 OH,
C 6 D 5 OH, and C 6 D 5 OD within the frequency range of
20–30 GHz. The behavior of phenol and its isomers in the
gas phase was examined by Neutralization—Reionization mass



1

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.



spectrometry (Turecek et al. 1989). Ravi et al. (1998) obtained
information about the anomalous temperature dependency of
adsorption of phenol. They also concluded that phenol’s
adsorption and desorption behavior in lower concentrations is
quite different from the higher concentration region. Parker &
Davis (1999) studied the photochemical reaction between
benzene and an oxygen atom ( [3] P) in a solid argon matrix at
12 K. The ultraviolet (UV) light with wavelength 280 nm was
used for this study. They obtained phenol, cyclohexadienone,
benzene oxide, and butadienylketene as products. Isomerization of phenol is considered an important step in the
metabolism of aromatic compounds. Phenol can isomerize to
cyclohexadienone by isodesmic reaction with a relative
enthalpy of the transition state (TS, 18.6 kcal mol [−][1], which is
determined by ΔH rxn of the isodesmic reaction) over a 69.4
kcal mol [−][1] barrier. This is lower than the energy needed
(86 kcal mol [−][1] ) for phenoxy-H bond cleavage (Zhu &
Bozzelli 2003). The millimeter-wave spectra of phenol in the
vibrational ground state and the first excited states of the
bending and torsion vibrational modes have been studied by
Kolesniková et al. (2013). They reported a tentative detection
for phenol in the IRAM 30 m line survey of Orion KL. A recent
experiment by Rahul et al. (2020) found infrared attenuation
due to phase change from amorphous to crystalline in the
propargyl ether ices which belong to the same C 6 H 6 O isomeric

group.
In this paper, we study ten molecules belonging to the
C 6 H 6 O isomeric group. The formation of phenol in high-mass
star-forming regions and starless dark cloud regions is studied.
Atacama Large Millimeter/submillimeter Array (ALMA)
archival data of a hot molecular core, G10.47+0.03 (hereafter
G10), are analyzed to identify the possible transitions of phenol
in this source. Based on the local thermodynamic equilibrium
(LTE) analysis, an upper limit on the abundance of phenol is
predicted in G10. Upper limit calculations are vital for
predicting future detections of complex organic molecules
(COMs), including prebiotic molecules (Sahu et al. 2020), and
inferring reaction pathways and reaction rates. The paper is
organized as follows. In Section 2, for the search of phenol, we
explore the band 4 ALMA archival data of G10. How phenol
could form is addressed in Section 3. Section 4 discusses the
astrochemical model and finally, in Section 5, we conclude. An
appendix section (Appendix) is presented to show the
thermodynamical parameters of the C 6 H 6 O isomeric group.


2. Astronomical Search for Phenol


Phenol has yet to be detected in the ISM, however, a
tentative detection was reported by Kolesniková et al. (2013) in
Orion KL. The tentative detection was based on the IRAM

30 m line survey, in the spectral range of 140–170 and
280–360 GHz toward Orion KL. They estimated a column
density of (8 ± 4) × 10 [14] cm [−][2] (abundance ∼8.0 × 10 [−][9],



considering N(H 2 ) = 1.0 × 10 [23] cm [−][2] in Orion KL; Tercero
et al. 2011). G10 is another hot core source where many COMs
are already reported (Rolffs et al. 2011; Gorai et al. 2020;
Mondal et al. 2021). The Orion KL and G10 are both Galactic
high-mass star-forming regions. Based on the recent identifications of various alcohols (Mondal et al. 2021) in G10, we
search for the simplest alcohol of the aromatic family, phenol in
G10. More specifically, we search for the transitions of phenol
in ALMA cycle 4 archival data of the hot molecular core G10
(project code #2016.1.00929.S). A detailed description of the
data can be found in Gorai et al. (2020), Mondal et al. (2021).
To check the detectability of phenol in G10, we generate
synthetic spectra of phenol utilizing the CASSIS spectrum
analyzer (Vastel et al. 2015). Here, we use the ALMA
telescope to generate the synthetic spectra with a hydrogen
column density ∼1.35 × 10 [25] cm [−][2] (Gorai et al. 2020), full
width at half maximum (FWHM) of 6 km s [−][1], source size of
2″, systematic velocity of 68 km s [−][1], and excitation temperature of 150 K. Mondal et al. (2021) estimated an average
rotational temperature of 177 K for various COMs in G10,
Olmi et al. (1996) estimated a temperature of about 160 K, and
Rolffs et al. (2011) considered 200 K in obtaining the column
density of the species identified in G10. Generated LTE
synthetic spectra along with the observed spectra are depicted
in Figures 1 and 2.
Data presented in Figure 8 of Kolesniková et al. (2013)
demonstrate that the transition at 148.489 GHz (E up = 151.02
K) has a tentative match with the observed data. A green
vertical line in the topmost panel of Figure 1 represents this
transition. We notice that this transition is blended with some

other transitions of phenol along with a transition of
glycolonitrile (HOCH 2 CN). We vary the abundance of phenol
to match this transition. We find that an abundance
∼5.19 × 10 [−][9] is needed to match the observed intensity. Some
transitions (148.6068, 148.9386, 149.2565, and 159.3413
GHz) are marked with blue vertical lines which might have
appeared due to phenol, but no conclusive transitions are
obtained.


3. Kinetics of Phenol


In the Appendix, we present some thermodynamic parameters of the species belonging to the C 6 H 6 O isomeric group.


3.1. At High-temperatures


Benzene and phenol are two fundamental species in the field
of combustion chemistry. Zhu & Bozzelli (2003) studied the
addition of a hydroxyl radical to benzene. They noticed that it
could initially form hydroxyl-cyclohexadienyl, further dissociating to either (i) C 6 H 5 OH + H or back to (ii) C 6 H 6 + OH.
They considered the overall reaction to phenol to be
thermoneutral. Thus, it is at equilibrium under the combustion/high-temperature condition, and hence the thermal



2

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.


Figure 1. Black lines represent the observed spectra toward G10. LTE spectra are shown in red considering N(H 2 ) = 1.35 × 10 [25] cm [−][2], excitation
temperature = 150 K, source size of 2″, FWHM = 6.0 km s [−][1], and abundance of 5.19 × 10 [−][9] (column density = 7.0 × 10 [16] cm [−][2] ). The green dashed lines indicate
the tentatively detected phenol transitions in Orion KL (Kolesniková et al. 2013). The blue dashed lines signify the possible phenol transitions in G10. Solid colored
arrows point out enlarged views of the lines.



reaction rate would depend on the concentration of reactant
species. Madronich & Felder (1985) applied the AeroChem
high-temperature photochemistry technique to study the
reaction between C 6 H 6 and OH over a temperature range of
790–1410 K. Their mechanistic studies around 1300 K showed

the following abstraction reactions as a dominant channel


C 6 H 6 + OH  C 6 H 5 + H 2 O. (1)



The rate constant for the reaction of an OH radical with

benzene and toluene was measured by Seta et al. (2006). They
applied a shock tube/pulsed laser-induced fluorescence
imaging method at high temperatures (∼700–1900 K).
Seta et al. (2006) carried out Quantum chemical calculations
with G3(MP2)/B3LYP and CBS-QB3 models to resolve the
disagreement of the rate constants above a temperature of 500
K between the TS calculations and experiments. They found



3

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.


Figure 2. Same as Figure 1.



that the discrepancy possibly arises due to the overestimated
partition function of the TS. This overestimation happens
because of the improper harmonic oscillator approximation of
C–H–O wagging, C–H–O rocking, and −OH torsion. Finally,
they noted that the anharmonicity of the C–H–O bending
vibration plays an important role in reproducing the experimental rate constant by TS theory. They concluded that the H
atom abstraction channel (reaction (2)) dominates their
temperature range. However, Tokmakov & Lin (2002)
indicated that the direct formation of phenol with an H atom
abstraction from reaction (2) is negligible over the temperature



region 200−2500 K


C 6 H 6 + OH  C 6 H 5 OH + H. (2)


3.2. At Interstellar Conditions


The formation pathways discussed above are mostly relevant
for combustion chemistry. However, reaction (1), considered
by Baulch et al. (2005), could be possible in the temperature
range of 298−1500 K. The rate constants α, β, and γ of this
reaction are considered as 2.8 × 10 [−][11], 0, and 2300,
respectively.



4

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.



In the dark cloud region, benzene abundance could reach
∼10 [−][10] (Jones et al. 2011). It plays a vital role in the formation
of aromatic molecules. Parker & Davis (1999) carried out
photolysis of benzene and ozone mixture in an argon matrix at
12 K. They found that phenol is the major product of their
experiment. It would form by the following reaction,


C 6 H 6 + O( 3 P)  C 6 H 5 OH. (3)


The O( [3] P) in the experiment appears from the photolysis of
ozone. They used UV light of 280 nm for the irradiation.
Taatjes et al. (2010) examined the reaction between benzene
and O( [3] P) over a temperature range of 300−1000 K and a
pressure range of 1−10 Torr. They also did quantum chemical
calculations to study the fate of this gas-phase reaction. With
the TS calculation, they estimated an activation barrier of
3356 K with α = 9.23 × 10 [−][10], β = −2.6, and γ = 0 in the
temperature range of 500−1000 K.
Wang & Frenklach (1997) considered the formation of a
phenyl radical by the hydrogen abstraction reaction of benzene,


C 6 H 6 + H  C 6 H 5 + H 2 . (4)


They considered α = 4.15 × 10 [−][10], β = 0, and γ = 8050 for
this gas phase reaction within the temperature limit of 50−200
K. If a modified Arrhenius equation (Wakelam et al. 2010) is
used to find out the rate coefficient of this reaction, at 200 K, it
has a rate around ∼1.4 × 10 [−][27] cm [3] s [−][1] . So, it is quite unlikely
to form −C 6 H 5 by reaction (4) in the gas phase. Instead, if this
reaction is considered in the ice phase with an activation barrier
of 8050 K, it is possible to produce some −C 6 H 5 at low
temperature. However, this type of reaction can occur at a
temperature below 20 K, which is falling outside the
temperature limit prescribed by Wang & Frenklach (1997).
To check the effect of this ice-phase reaction (4), we study the
abundance of phenol in the absence and presence of this
reaction.

Once a phenyl radical is produced by reactions (1) and (4),
we consider the following radiative association reaction to form
phenol


C 6 H 5 + OH  C 6 H 5 OH + _h_ _n_ . (5)


We did not find any study which used reaction (5) for the
formation of phenol. Vasyunin & Herbst (2013) discussed the
radiative association reaction between two radicals (CH 3 O and
CH 3 ). They proposed a temperature-dependent rate coefficient
for such reaction with α = 10 [−][15], β = −3.0, and γ = 0.0. Sil
et al. (2018) also consider similar rate constants for the
chemical modeling in predicting the abundances of certain
aldimines and amines in hot cores. However, looking at the
large uncertainty in the prescribed rate constant, we use
α = 10 [−][10] for most of the cases to see the upper limit of
forming phenol with reaction (5). For some specific cases, we
apply the rate constants used in Vasyunin & Herbst (2013).



4. Astrochemical Model


Here, Chemical Model of Molecular Cloud is implemented
(Das et al. 2019, 2021; Gorai et al. 2020; Mondal et al. 2021;
Sil et al. 2021; Bhat et al. 2022) to study the chemical evolution
of phenol in high-mass star-forming regions and dark cloud
environments.


4.1. Hot Core Model


For the high-mass star-forming regions, Gorai et al. (2020), Sil
et al. (2021), Mondal et al. (2021) considered three distinct
stages, (a) isothermal collapse (n H = 3.0 × 10 [3] –10 [7] cm [−][3],
T gas = T ice = 10 K, A V = 2 − 200, time = 10 [5] yr), (b) warm-up
(n H = 10 [7] cm [−][3], T gas = T ice = 10–200 K, A V = 200, time =
5.0 × 10 [4] yr), and (c) post-warm-up (n H = 10 [7] cm [−][3],
T gas = T ice = 200 K, A V = 200, time = 1.0 × 10 [5] yr). Here,
following Garrod et al. (2017), for the isothermal collapse phase,
we consider minimum density (n H0 ) = 3 × 10 [3] cm [−][3] and
maximum density ( _n_ Hmax ) = 2 ´ 10 8 cm [−][3] . A shorter collapsing time ( ∼ 10 [5] yr) is considered. Visual extinction parameter is
allowed to vary from a minimum value (A V = 2) to _A_ _V_ =
_A_ _V_ 0 ( _n_ H _n_ H0 ) [2] [3] (Garrod 2008). Dust temperature is allowed to
vary depending on the A V (Garrod 2008), whereas the gas
temperature is kept constant at 10 K. During the initial warm-up
phase, the cloud is allowed to warm up (gas and grain both) to
200 K in 10 [5] yr. Then another 2.12 × 10 [4] yr is used to warm up
to 400 K. Finally, another 10 [5] yr is used for the post-warm-up
phase, where temperature, density, and visual extinction are kept
constant at their respective highest values. So, in total, our
simulation continues up to 3.212 × 10 [5] yr.
Ice-phase pathways are crucial for the chemical complexity
of the ISM. Even the abundances of the most abundant species,
H 2, could not be explained without considering ice-phase
chemistry (Biham et al. 2001; Chakrabarti et al. 2006a, 2006b;
Sahu et al. 2015). Hydrogenation reactions at the ice phase play
a crucial role for the formation of COMs (Hasegawa et al.
1992; Das et al. 2008, 2010, 2016; Das & Chakrabarti 2011).
Ice-phase reactions are included following Hasegawa et al.
(1992), Ruaud et al. (2015), Das et al. (2015a, 2015b), Gorai
et al. (2017a, 2017b). The binding energies of most of the ice
phase species are considered following Garrod et al. (2017).
For phenyl radical and phenol, we calculate the binding
energies by the method prescribed in Sil et al. (2017), Das et al.
(2018, 2021). As a result, we obtain binding energy (scaled by
1.416, because we use water monomer as a substrate here) of
C 6 H 5 and C 6 H 5 OH as 2056 K and 5476 K, respectively.
Since the formation/destruction of nine other species of
C 6 H 6 O except phenol are poorly constrained, their formation/
destruction are not considered here. We prepare various models
to study the fate of the phenol production in such environments. Models are prepared based on the reactions (1), (3), (4),
and (5) (see Table 1). For the destruction of phenol in the gas
phase, photodissociation (α = 2.9 × 10 [−][9], β = 0, and γ = 1.7 is



5

Table 1
Models Considered in this Study


Reactions C1 C2 C3 C4 C5 C6 C7 C8 C9 C10 DC


C 6 H 6 + OH → C 6 H 5 + H 2 O (1) gas gas gas gas gas gas+ice gas+ice gas+ice [a] gas+ice
C 6 H 6 + O → C 6 H 5 OH (3) gas gas gas+ice gas+ice gas+ice gas+ice gas+ice gas+ice gas+ice
C 6 H 6 + H → C 6 H 5 + H 2 (4) gas gas gas gas+ice gas+ice gas+ice gas+ice gas+ice [a] gas+ice
C 6 H 5 + OH → C 6 H 5 OH + h ν (5) gas gas gas gas gas gas+ice gas+ice gas [b] +ice gas [b] +ice gas+ice


Peak abundance 1.67 × 10 [−][12] 1.72 × 10 [−][21] 4.16 × 10 [−][15] 1.67 × 10 [−][12] 1.67 × 10 [−][12] 1.67 × 10 [−][12] 1.67 × 10 [−][12] 2.20 × 10 [−][9] 1.09 × 10 [−][11] 1.67 × 10 [−][12] 9.93 × 10 [−][16]


Notes.
a Temperature limit considered in gas and ice phase.
b −15
used α = 10 and β = −3.0 for C 6 H 5 + OH → C 6 H 5 OH + hν (reaction (5)).

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.


Figure 3. The left panel shows the time evolution (during the warm-up and post-warm-up phase) of phenol for some selected models noted in Table 1. Solid lines
represent the gas-phase abundance, whereas the ice phase abundance is depicted with dashed curves. The right panel displays the time evolution of gas-phase phenol

in a starless dark cloud model.



used) and cosmic ray dissociation (α = 1.3 × 10 [−][17], β = 0, and
γ = 263.5) are considered. Furthermore, its destruction by the
major ions (C [+], He [+], HCO [+], and H 3 O [+] ) is also considered.
In Table 1, models C1–C4 are classified based on the gasphase reactions (1), (3), (4), and (5). Models C1–C4 do not
consider any of these four reactions in the ice phase. Following
Baulch et al. (2005) and the KIDA database [7], in models C3 and
C4, reaction (1) is considered to be valid within a temperature
limit of 298−1500 K. For reaction (3), Taatjes et al. (2010)
proposed γ = 3356 K and a temperature window of 500−1000
K. However, Parker & Davis (1999) carried out photolysis at
12 K and found that phenol was produced. Based on the
experiment of Parker & Davis (1999), our models C1 and C4
consider reaction (3) at a low temperature (∼10 K) with the gas
phase rate constants found by Taatjes et al. (2010). Following
Wang & Frenklach (1997), for reaction (4), a temperature
window of 50−200 K is considered with γ = 8050 K in models
C2 and C4. Reaction (5) is considered as barrier-less in models
C2 and C3 with α = 10 [−][10] . The abundances noted in Table 1

clearly indicate that the gas-phase reaction (3) is the key if it is
considered at low temperature ∼10 K. We have obtained a
peak gas-phase abundance of 1.67 × 10 [−][12] for phenol among
models C1–C4. The left panel of Figure 3 shows the time
evolution of phenol beyond the collapsing time. Observed
upper limit of phenol abundance is highlighted with the brown
horizontal line.

From model C5 onward, these four reactions are sequentially
considered in the ice phase with the activation barriers similar

–
to the gas-phase rate constant, γ. However, for models C5 C9,
no temperature restriction of ice-phase reactions is considered.


7 [http://kida.astrophy.u-bordeaux](http://kida.astrophy.u-bordeaux)



Ice-phase rate constants are calculated by the method described
in Hasegawa et al. (1992). From Table 1, it is clear that
consideration of the ice-phase reactions (3), (4), and (5) does
not increase the formation of phenol. Instead, ice-phase
reaction between C 6 H 6 and −OH (reaction (1)) is contributing
(see abundance obtained from model C8). This is a hydrogen
abstraction reaction. Following Belloche et al. (2016), Garrod
et al. (2017), here also, we consider the hydrogen mass instead
of the reduced mass to calculate the tunneling rate of this
reaction. The other hydrogen abstraction reactions of Belloche
et al. (2016), Garrod et al. (2017) are also considered in our
model. With the consideration of the ice-phase reaction (1), we
have obtained a peak gas-phase abundance of phenol as
2.20 × 10 [−][9] . The models C8 and C9 are the same, except for
the gas-phase rate constants considered for reaction (5). In
model C9, we have considered α = 10 [−][15] and β = −3.0
instead of α = 10 [−][10] and β = 0 applied in model C8. With the
consideration of the lower leading rate constant, phenol
abundance drops to 1.09 × 10 [−][11] . The left panel of Figure 3
plots the time evolution of phenol with models C8 and C9.
A separate model C10 is constructed by implementing the
temperature limit of the reactions (1) and (4) in both the gas and
ice phases. For the gas-phase reaction (5), the rate constant
(α = 10 [−][15], β = −3.0, and γ = 0) mentioned in the context of
model C9 is utilized. Reaction (3) is considered to be valid ∼10
K. The orange line of the left panel of Figure 3 shows the time
evolution of gas-phase phenol obtained with model C10. The
peak abundance obtained with this model is 1.67 × 10 [−][12] for
this. So, if the ice-phase hydrogen abstraction reaction (1) is not
considered at low temperature, then the gas-phase reaction (3)
controls the formation of phenol.



7

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.



4.2. Dark Cloud Model


Benzonitrile was observed in a starless dark cloud, TMC-1
(McGuire et al. 2018). This might have formed by the reaction
between the benzene and cyanide ( - CN ) radical. A similar
pathway for the formation of phenol is considered here
(reaction (5)). For the dark cloud model DC, some standard
parameters are implemented (n H = 2.0 × 10 [4] cm [−][3], T gas =
T ice = 20 K, A V = 10, time = 1.0 × 10 [7] yr). The right panel of
Figure 3 represents the time evolution of phenol for the dark
cloud condition. It is clear from the figure that even with the
highest rate constant and avoiding the temperature restriction,
we can have a maximum gas-phase abundance of 9.93 × 10 [−][16]

for phenol.


5. Conclusions


Interstellar chemistry is far from equilibrium, and the
reaction pathways mainly control it. However, based on the
reaction energy, dipole moment, and enthalpy of formation, it
shows that phenol, 2,5-cyclohexadienone, and cyclohexadienone are the probable candidates and propargyl ether (the only
non-cyclic structure among all the isomers considered here) is
the least probable candidate for future astronomical detection in
the C 6 H 6 O isomeric group. Therefore, we prepare a chemical
model to check the fate of the formation of phenol in the high
mass star-forming regions (models C1–C10) and dark cloud
(model DC) environments. We notice that even with the upper
limit of the rate constant and no temperature limitation for the
ice-phase reactions, the formation of phenol is inadequate in
the dark cloud condition. In contrast, we ascertained the
chances of forming phenol in the hot core from our
astrochemical model. We found that the ice-phase hydrogen
abstraction reaction (if allowed at ∼10 K) of benzene with
−OH radical can produce −C 6 H 5 radical and H 2 O on the grain.
The −C 6 H 5 radical eventually transferred to the gas phase to
form phenol by the radiative association reaction with −OH
radical. With the upper limit of the rate constant of radiative
association reaction between −C 6 H 5 and −OH radicals
(α = 10 [−][10] ) along with the hydrogen abstraction reaction of
benzene allowed at the low temperature, our model predicts a
peak gas-phase abundance of ∼ 2.20 × 10 [−][9] for phenol. When
a temperature restriction (reaction (1) is considered in gas and
ice phase beyond 298 K) is applied and a conservative rate
constant for the radiative association reaction is used, reaction
(1) becomes obsolete and obtains a peak gas-phase
abundance ∼ 1.67 × 10 [−][12] for phenol, which occurs due to
the other gas-phase reaction C 6 H 6 + O → C 6 H 5 OH (reaction
(3)). All these obtained peak abundances are consistent (below)
with the upper limit (5.19 × 10 [−][9] ) set by the data analysis of a
Galactic high-mass star-forming region, G10.



Acknowledgments


R.G. wants to acknowledge the SVMCM scholarship,
Government of West Bengal. M.S. [IF160109] gratefully
acknowledges the DST-INSPIRE Fellowship scheme for
financial assistance. S.K.M. (09/904(0014)/2018-EMR-I)
acknowledges the CSIR fellowship. This paper makes
use of the following ALMA archival data: ADS/JAO.
ALMA#2016.1.00929.S. (ALMA is a partnership of ESO
(representing its member states), NSF (USA) and NINS
(Japan), together with NRC (Canada), MOST and ASIAA
(Taiwan), and KASI (Republic of Korea), in cooperation with
the Republic of Chile. The Joint ALMA Observatory is
operated by ESO, AUI/NRAO and NAOJ).


Appendix
Thermodynamic Data of C 6 H 6 O Isomeric Group


To carry out a comprehensive study of thermodynamic data
among the ten considered species from C 6 H 6 O isomeric group,
we perform quantum chemical calculations using the Gaussian
09 suite of programs (Frisch et al. 2013). Out of the ten
considered isomers of phenol, nine are cyclic. Only propargyl
ether is not a cyclic member. The optimized structures (see
Figure A1) are subsequently characterized by the harmonic
vibrational analysis.


A.1. Electronic Energy with Zero-point Vibrational
Energy Correction


The electronic energy values with zero-point vibrational
energy correction (E 0 +ZPVE) for all the species are calculated.
The G4 composite method (Curtiss et al. 2007) is utilized for
these computations. These values are arranged in descending
order in Table A1. The relative energy value of a species is
calculated by subtracting their E 0 +ZPVE from that of the
phenol (see the bracketed term of column 3 in Table A1). The
equilibrium geometry of all the optimized structures is verified
based on the non-negative frequencies of vibration. This allows
all the species to locate them at the valley on the potential
energy surface. According to our calculations, phenol is
energetically most favorable, and propargyl ether is the least
favorable candidate of the C 6 H 6 O isomeric group. We notice
that the relative energy of 2,5-cyclohexadienone is greater than
that of phenol by ∼17 kcal mol [−][1] . Cyclohexadienone is the
third in this series, having relative energy ∼18 kcal mol [−][1]

compared to phenol. Le et al. (2001) carried out the quantum
chemical calculations with B3LYP/6-311++G(d,p) + ZPVE.
They found that cyclohexadienone and 2,5-cyclohexadienone
have the relative energies of 17.4 kcal mol [−][1] and
16.5 kcal mol [−][1], respectively compared to phenol. The gasphase tautomerism process of phenol has been attempted by
Gómez et al. (2006) theoretically by using Gaussian 03 suite of
quantum-chemical programs. They showed that phenol is more



8

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.


Figure A1. The optimized structures of C 6 H 6 O isomeric group. Except propargyl ether, all the isomers are cyclic.



stable than its tautomers (cyclohexadienone and 2,5-cyclohexadienone). It is noticed that phenol is more stable by
19.1 kcal mol [−][1] and 17.2 kcal mol [−][1] than cyclohexadienone
and 2,5-cyclohexadienone, respectively. Moreover, Gómez
et al. (2006) predicted that 2,5-cyclohexadienone is energetically lower (by 1.9 kcal mol [−][1] ) than cyclohexadienone. They
used the CASPT2(8,8)/cc-pVDZ level of theory for energy
calculation and CASSCF(8,8)/6-31G(d) level of theory for
geometry optimization. Our calculations noted in Table A1
report a ∼1 kcal mol [−][1] energy difference between these two.


A.2. Enthalpy of Formation


We include the calculated enthalpy of formation (Δ f H [0] ) of
these species by using Density Functional Theory (DFT) with
the popular hybrid B3LYP functional and 6-31G(d,p) basis set.
The obtained Δ f H [0] are compared with the experimental values



(if available). The enthalpy of formation denotes the enthalpy
changes, accompanied by the formation of a species from its
constituents. Table A1 shows a negative value for the first three
species, and the rest are positive. The negative value refers to
the exothermicity, where energy is usually released to form a
stronger bond. On the contrary, the positive value refers to the
thermodynamically least favorable endothermicity under the
interstellar condition. However, it is essential to note that
interstellar chemistry is far from equilibrium, and kinetics
dominate the chemical composition rather than thermodynamics. Our calculations demonstrate that phenol releases ∼22
kcal mol [−][1], whereas 2,5-cyclohexadineone and cyclohexadineone release ∼5 kcal mol [−][1] and 4 kcal mol [−][1], respectively to
form the bond. Zhu & Bozzelli (2003) calculated the standard
enthalpy of formation value of cyclohexadienone and 2,5cyclohexadienone by applying CBS-QB3 level of theory. Their
finding is similar to our values (−4.4 ± 2.4 kcal mol [−][1] and



9

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.


Table A1
The Enthalpy of Formation at 298 K, Electronic Energy (E 0 ) with Zero-point Vibrational Energy (ZPVE), and Relative Energy with the G4 Composite Method for ten
Species of the C 6 H 6 O Isomeric Group


Serial Species E 0 +ZPVE Calculated Δ f H [0] at T = 298 K Experimental
No. in Hartree/Particle Using G4 Composite Method Δ f H [0] at T = 298 K
(Relative Energy (Using B3LYP/6-31G(d,p) Method) (in kcal mol [−][1] )
in kcal mol [−][1] ) (in kcal mol [−][1] )


1 Phenol −307.387662 (0.000000) −22.047392 (−17.587071) −23.03 [a]

2 2,5-cyclohexadienone −307.360965 (16.751369) −5.182519 (−1.506103) −11.95 [a], −6.0 ± 2.4 [b]

3 cyclohexadienone −307.359278 (17.810605) −4.010040 (−0.623054) −4.4 ± 2.4 [b]

4 Vinylfuran −307.348834 (24.364315) 2.561879 (7.520718) 6.6444 [c]

5 3-Vinylfuran −307.341343 (29.06499) 7.461043 (12.307825)
6 Oxepin −307.317155 (44.243192) 22.318538 (27.000497)
7 Arene Oxide −307.313922 (46.271931) 24.015868 (28.049861)
8 3-Oxabicyclo[3.2.0]hepta-1, 4-diene −307.299106 (55.569113) 33.377396 (37.848077)
9 Oxanorbornadiene −307.281912 (66.358513) 43.830,071 (48.037668)
10 Propargyl Ether −307.223585 (102.959266) 82.496958 (90.075299)


Notes.
a [https://cccbdb.nist.gov](https://cccbdb.nist.gov)
b Zhu & Bozzelli (2003).
c Lide (2004).



−6.0 ± 2.4 kcal mol [−][1] for cyclohexadienone and 2,5-cyclohexadienone, respectively). Table A1 affirms that the calculated
Δ f H [0] for phenol with the G4 composite method
(−22.04 kcal mol [−][1] ) is in good agreement with the experiment
(−23.03 kcal mol [−][1] ). With the DFT-B3LYP/6-31G(d,p) level
of theory, we obtain a large deviation from the experimental
values. Zhu & Bozzelli (2003) also showed that their results in
obtaining the value of Δ f H [0] at 298 K are significantly higher
than the experimentally determined Δ f,298 H [0] values of Shiner
et al. (1986) for cyclohexadineone and 2,5-cyclohexadienone.
But, the trend we are getting in our calculation is the same as that of
Le et al. (2001), Gadosy & McClelland (1996), Zhu et al. (2000),
Santoro & Louw (2001), i.e., Δ f,298 H [0] (phenol) = Δ f,298 H [0]

(2,5-cyclohexadienone) < Δ f,298 H [0] (cyclohexadienone). A graphical representation of enthalpy of formation is displayed in
Figure A2. It depicts that the relative energy of propargyl ether is
the highest in between this isomeric group (∼103 kcal mol [−][1] ).


A.3. Dipole Moment Components


Radio astronomy is the most powerful tool to identify
interstellar species. It already bears ∼200 species (including
radicals and ions) in the ISM. The intensity of a rotational
transition between two rotational energy levels may change due
to the relative sign of the dipole moment components (a-type,
b-type, and c-type) that are small in magnitude (Müller et al.
2016). The expected intensities are directly proportional to the
square of the total dipole moment (μ total ) of that species and
inversely proportional to the rotational partition function (Q rot )
at a particular temperature. So, at a fixed temperature, the
higher the value of the total dipole moment is, higher the



Figure A2. Enthalpy of Formation for different species in C 6 H 6 O isomeric

group.


intensities. Dipole moments in the unit of debye of each species
along the fixed a-, b- and c-axis (μ a, μ b, and μ c ) and the total
dipole moment (μ total ) are noted in Table A2. To calculate the
dipole moment of this isomeric group, we use the DFTB3LYP/6-31G(d,p) level of quantum chemical theory. The
experimental values (if available) are also noted in parentheses.
They show that our calculated values can successfully explain
the experimentally obtained values. The size and direction of a
species could characterize the dipole moment. Here, from our
calculations, we obtain a total dipole moment of phenol as
1.3359 D, which is in good agreement with the available
literature values (McClellan 1963; Johnson 1999; Reese et al.
2004). In the case of Vinylfuran, “c” type transition is absent,



10

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.


Table A2
Calculated Dipole Moment Components for Ten Species of the C 6 H 6 O Isomeric Group with DFT/B3LYP 6-31G(d,p) Method


Serial No. Species μ a (D) μ b (D) μ c (D) μ total (D)


1 Phenol 0.0946 (−0.133 ± 0.003) [a] 1.3326 (1.217 ± 0.008) [a] 0.0000 (0.000) [a] 1.3359 (1.224 ± 0.008) [a], 1.45 [b]

2 2,5 -cyclohexadienone 4.4575 0.0005 0.0001 4.4575
3 cyclohexadienone −3.4890 0.4296 −0.0011 3.5154
4 Vinylfuran −0.6237 0.4933 0.0000 0.7952 (0.69 ± 0.07) [c]

5 3-Vinylfuran 0.1191 0.5266 −0.0090 0.5400
6 Oxepin 0.5949 0.0000 −1.2178 1.3554

7 Arene Oxide −0.9200 −0.0006 −1.7205 1.9510

8 3-Oxabicyclo[3.2.0]hepta-1,4-diene −1.3382 0.0001 −0.0033 1.3382

9 Oxanorbornadiene 0.0000 0.0000 −1.8709 1.8709

10 Propargyl Ether −0.0003 1.5289 0.0005 1.5289


Notes. Experimental values are noted in parentheses (if available).

a
Johnson (1999).
b
McClellan (1963).
c Lide (2004).


Table A3
Calculated Rotational Constant and Rotational Partition Function (Q rot ) at 150 K for Ten Species of the C 6 H 6 O Isomeric Groups with the MP2/6-311G++(d,p)
Method


Serial Species A (in MHz) B (in MHz) C (in MHz) Rotational Partition

No. Function at 150 K


1 Phenol 5627.92 (5650.52) [a] 2605.76 (2619.24) [a] 1781.25 (1789.85) [a] 0.605,968(+05)
2 2,5-cyclohexadienone 5226.05 (5228) [b] 2652.04 (2653) [b] 1778.26 (1779) [b] 0.623,848(+05)
3 cyclohexadienone 5127.57 2693.12 1805.09 0.620,327(+05)
4 Vinylfuran 7811.41 2103.65 1657.32 0.593,470(+05)
5 3-Vinylfuran 7785.52 1955.09 1599.18 0.627,738(+05)
6 Oxepin 4030.06 3817.33 2145.01 0.539,143(+05)
7 Arene oxide 4552.69 3588.31 2304.04 0.504,812(+05)
8 3-Oxabicyclo[3.2.0]hepta-1,4-diene 6714.63 2711.64 1980.23 0.515,786(+05)
9 Oxanorbornadiene 4527.55 3722.71 3301.26 0.207,598(+05)
10 Propargyl ether 11,416.16 1056.99 979.71 0.900,761(+05)


Notes.
a Larsen (1979).
b
Johnson (1999).



and the total calculated electric dipole moment (0.7952 D)
shows good agreement with the available value (0.69 D;
Lide 2004). In oxanorbornadiene, the “a” and “b” type
rotational transition is absent, whereas the “c” type transition
is available.


A.4. Rotational Constants


No microwave spectra of a species are observed unless it has
a permanent electric dipole moment. The intensity of spectra
depends on the shape of a species. Quantum chemical studies
can provide a reliable spectroscopic constant (comparable to
experimental value) to aid laboratory microwave studies. These
studies are essential as these could ultimately lead to the
identification of new species in the ISM. So, a high level of



quantum chemical theory is needed for a precise calculation
of rotational spectroscopic parameters. Here, Møller–Plesset
of second order perturbation (MP2) method (Møller &
Plesset 1934), with the 6-311G++(d,p) including a diffuse
function are used to calculate the rotational constants (A, B, and
C) of the species of C 6 H 6 O isomeric group (see Table A3). The
obtained values are compared with the experimentally obtained
parameters (if available). The comparison between these two
data shows that calculated values are matched well with the

experimentally obtained values.

_m_ 2 _b_ _Q_ rot [would] [indicate] [the] [expected] [antenna] [temperature] [of]
some large molecules (Charnley et al. 1995). They used b-type
electric dipole moment because it was much more extensive
for all types of molecules considered in their study. For our



11

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.


top molecules, one can reference the approximate ground
vibrational state rotational partition function for the asymmetric
top molecules (Cernicharo et al. 2016; Sil et al. 2018) using the
following relation


_Q_ rot = 5.3311 ´ 10 6 ( _T_ 3 _ABC_ ) _s_ . (A1)


Here σ is the rotational symmetry number having the value 1
for all species, A, B, and C are the rotational constants for the
molecule (in MHz) and T is the temperature (in K).


ORCID iDs



Figure A3. Expected intensity ratio of the C 6 H 6 O isomeric groups.


molecules (belonging to the C 6 H 6 O isomeric group), we did
not see any such trend for any specific type of dipole moment.
Therefore, we use the total dipole moment (μ total ) for our case
rather than relying on a particular kind of dipole moment.
Figure A3 features a comparative study on the expected
antenna temperature of the C 6 H 6 O isomeric group. Only the
_m_ total2 _Q_ rot [is] [considered] [for] [this] [comparison.] [In] [reality,] [the]
intensity would also depend on the abundance, which is not
considered here. It is the reaction pathways that control their
abundance. Figure A3 shows that this probability is maximum
for 2,5-cyclohexadienone. Rotational constants and rotational
partition function for the C 6 H 6 O isomeric group are listed in
Table A3. Rotational constants along the three principal axes
(a, b and c) are given in the unit of MHz. In the case of phenol,
the calculated values of rotational constants A, B, and C are
5627.92 MHz, 2605.76 MHz, and 1781.25 MHz, respectively,
and all are approximately well matched with experimental
values and have the deviation of 0.4%, 0.5%, and 0.5%,
respectively, from the experimental values. We obtain a
variation of 0.04%, 0.04%, and 0.02% in the calculated A, B,
and C from the experimental values for 2,5-cyclohexadienone
respectively. For the rest of the species, no experimental values
are available. So, our calculation would be an essential
guideline for the rotational constants of these species. Based
on the values obtained for phenol and 2,5-cyclohexadienone, it
is expected that our calculated value would have a minor
deviation from the experimentally obtained values. Table A3
reports the rotational partition functions for all the isomers at a
150 K temperature relevant for the hot core condition. These
values play a significant role to derive the molecular column
densities and help to calculate line intensities. These partition
functions are calculated quantum chemically applying the
“freqchk” utility, which is used to retrieve frequency and
thermochemistry data from a checkpoint file, with the optional
specification of alternate temperature, pressure, scale factor,
and/or isotope substitutions. As all the isomers are asymmetric



Rana Ghosh [https://orcid.org/0000-0003-1745-9718](https://orcid.org/0000-0003-1745-9718)
Milan Sil [https://orcid.org/0000-0001-5720-6294](https://orcid.org/0000-0001-5720-6294)
Suman Kumar Mondal [https://orcid.org/0000-0002-](https://orcid.org/0000-0002-7657-1243)
[7657-1243](https://orcid.org/0000-0002-7657-1243)
Prasanta Gorai [https://orcid.org/0000-0003-1602-6849](https://orcid.org/0000-0003-1602-6849)
Dipen Sahu [https://orcid.org/0000-0002-4393-3463](https://orcid.org/0000-0002-4393-3463)
Rahul Kumar Kushwaha [https://orcid.org/0000-0002-](https://orcid.org/0000-0002-5914-7061)
[5914-7061](https://orcid.org/0000-0002-5914-7061)
Bhalamurugan Sivaraman [https://orcid.org/0000-0002-](https://orcid.org/0000-0002-2833-0357)
[2833-0357](https://orcid.org/0000-0002-2833-0357)
Ankan Das [https://orcid.org/0000-0003-4615-602X](https://orcid.org/0000-0003-4615-602X)


References


Baulch, D., Bowman, C., Cobos, C. J., et al. 2005, [JPCRD,](https://doi.org/10.1063/1.1748524) [34,](https://ui.adsabs.harvard.edu/abs/2005JPCRD..34..757B/abstract) 757
Belloche, A., Müller, H. S. P., Garrod, R. T., & Menten, K. M. 2016, [A&A,](https://doi.org/10.1051/0004-6361/201527268)

587, A91
[Bhat, B., Gorai, P., Mondal, S. K., Chakrabarti, S. K., & Das, A. 2022, AdSpR,](https://doi.org/10.1016/j.asr.2021.07.011)

69, 415
Biham, O., Furman, I., Pirronello, V., & Vidali, G. 2001, [ApJ,](https://doi.org/10.1086/320975) [553,](https://ui.adsabs.harvard.edu/abs/2001ApJ...553..595B/abstract) 595
[Burkhardt, A. M., Lee, K. L. K., Changala, P. B., et al. 2021, ApJL, 913, L18](https://doi.org/10.3847/2041-8213/abfd3a)
Cernicharo, J., Agúndez, M., Cabezas, C., et al. 2021a, [A&A,](https://doi.org/10.1051/0004-6361/202141156) [649,](https://ui.adsabs.harvard.edu/abs/2021A&A...649L..15C/abstract) L15
Cernicharo, J., Agúndez, M., Kaiser, R. I., et al. 2021b, [A&A,](https://doi.org/10.1051/0004-6361/202142226) [655,](https://ui.adsabs.harvard.edu/abs/2021A&A...655L...1C/abstract) L1
Cernicharo, J., Kisiel, Z., Tercero, B., et al. 2016, [A&A,](https://doi.org/10.1051/0004-6361/201527531) [587,](https://ui.adsabs.harvard.edu/abs/2016A&A...587L...4C/abstract) L4
Chakrabarti, S. K., Das, A., Acharyya, K., & Chakrabarti, S. 2006a, [A&A,](https://doi.org/10.1051/0004-6361:20065335)

457, 167
Chakrabarti, S. K., Das, A., Acharyya, K., & Chakrabarti, S. 2006b, [BASI,](https://ui.adsabs.harvard.edu/abs/2006BASI...34..299C/abstract)

34, 299
[Charnley, S. B., Kress, M. E., Tielens, A. G. G. M., & Millar, T. J. 1995, ApJ,](https://doi.org/10.1086/175955)

448, 232
[Cooke, I. R., Gupta, D., Messinger, J. P., & Sims, I. R. 2020, ApJL, 891, L41](https://doi.org/10.3847/2041-8213/ab7a9c)
Curtiss, L. A., Redfern, P. C., & Raghavachari, K. 2007, [JChPh,](https://doi.org/10.1063/1.2436888) 126, [084108](https://ui.adsabs.harvard.edu/abs/2007JChPh.126h4108C/abstract)
Das, A., Acharyya, K., Chakrabarti, S., & Chakrabarti, S. K. 2008, [A&A,](https://doi.org/10.1051/0004-6361:20078422)

486, 209
Das, A., Acharyya, K., & Chakrabarti, S. K. 2010, [MNRAS,](https://doi.org/10.1111/j.1365-2966.2010.17343.x) [409,](https://ui.adsabs.harvard.edu/abs/2010MNRAS.409..789D/abstract) 789
Das, A., & Chakrabarti, S. K. 2011, [MNRAS,](https://doi.org/10.1111/j.1365-2966.2011.19503.x) [418,](https://ui.adsabs.harvard.edu/abs/2011MNRAS.418..545D/abstract) 545
Das, A., Gorai, P., & Chakrabarti, S. K. 2019, [A&A,](https://doi.org/10.1051/0004-6361/201834923) [628,](https://ui.adsabs.harvard.edu/abs/2019A&A...628A..73D/abstract) A73
Das, A., Majumdar, L., Chakrabarti, S. K., & Sahu, D. 2015a, [NewA,](https://doi.org/10.1016/j.newast.2014.07.006) [35,](https://ui.adsabs.harvard.edu/abs/2015NewA...35...53D/abstract) 53
Das, A., Majumdar, L., Sahu, D., et al. 2015b, [ApJ,](https://doi.org/10.1088/0004-637X/808/1/21) [808,](https://ui.adsabs.harvard.edu/abs/2015ApJ...808...21D/abstract) 21
Das, A., Sahu, D., Majumdar, L., & Chakrabarti, S. K. 2016, [MNRAS,](https://doi.org/10.1093/mnras/stv2264)

455, 540
Das, A., Sil, M., Ghosh, R., et al. 2021, [FrASS,](https://doi.org/10.3389/fspas.2021.671622) 8, 78
Das, A., Sil, M., Gorai, P., Chakrabarti, S. I. K., & Loison, J. C. [2018, ApJS,](https://doi.org/10.3847/1538-4365/aac886)

[237,](https://ui.adsabs.harvard.edu/abs/2018ApJS..237....9D/abstract) 9
Forest, H., & Dailey, B. 1966, [JChPh,](https://doi.org/10.1063/1.1727823) 45, 1736
Frisch, M. J., Trucks, G. W., Schlegel, H. B., et al. 2013, Gaussian 09 Revision
D.01 (Wallingford CT: Gaussian Inc)
Gadosy, T. A., & McClelland, R. A. 1996, JMoSt, 369, 1
Garrod, R. T. 2008, [A&A,](https://doi.org/10.1051/0004-6361:200810518) [491,](https://ui.adsabs.harvard.edu/abs/2008A&A...491..239G/abstract) 239
Garrod, R. T., Belloche, A., Müller, H. S. P., & Menten, K. M. 2017, [A&A,](https://doi.org/10.1051/0004-6361/201630254)

601, A48



12

Research in Astronomy and Astrophysics, 22:065021 (13pp), 2022 June Ghosh et al.



Gómez, I., Rodríguez, E., & Reguero, M. 2006, [JMoSt,](https://doi.org/10.1016/j.theochem.2006.03.034) 767, 11
Gorai, P., Bhat, B., Sil, M., et al. 2020, [ApJ,](https://doi.org/10.3847/1538-4357/ab8871) [895,](https://ui.adsabs.harvard.edu/abs/2020ApJ...895...86G/abstract) 86
Gorai, P., Das, A., Das, A., et al. 2017a, [ApJ,](https://doi.org/10.3847/1538-4357/836/1/70) [836,](https://ui.adsabs.harvard.edu/abs/2017ApJ...836...70G/abstract) 70
Gorai, P., Das, A., Majumdar, L., et al. 2017b, [MolAs,](https://doi.org/10.1016/j.molap.2017.01.004) 6, 36
Hasegawa, T. I., Herbst, E., & Leung, C. M. 1992, [ApJS,](https://doi.org/10.1086/191713) 82, 167
Johnson, R. D., III 1999, NIST 101. Computational Chemistry Comparison and
Benchmark Database, Tech. Rep.
Jones, B. M., Zhang, F., Kaiser, R. I., et al. 2011, [PNAS,](https://doi.org/10.1073/pnas.1012468108) [108,](https://ui.adsabs.harvard.edu/abs/2011PNAS..108..452J/abstract) 452
Kojima, T. 1960, [JPSJ,](https://doi.org/10.1143/JPSJ.15.284) 15, 284
Kolesniková, L., Daly, A. M., Alonso, J. L., Tercero, B., & Cernicharo, J.
2013, [JMoSp,](https://doi.org/10.1016/j.jms.2013.05.006) [289,](https://ui.adsabs.harvard.edu/abs/2013JMoSp.289...13K/abstract) 13
Larsen, N. W. 1979, [JMoSt,](https://doi.org/10.1016/0022-2860(79)80292-6) [51,](https://ui.adsabs.harvard.edu/abs/1979JMoSt..51..175L/abstract) 175
Le, H. T., Flammang, R., Gerbaux, P., Bouchoux, G., & Nguyen, M. T. 2001,

[JPCA,](https://doi.org/10.1021/jp012679e) 105, 11582
Lee, K. L. K., Changala, P. B., Loomis, R. A., et al. 2021, [ApJL,](https://doi.org/10.3847/2041-8213/abe764) [910,](https://ui.adsabs.harvard.edu/abs/2021ApJ...910L...2L/abstract) L2
Lide, D. 2004, CRC Handbook of Chemistry and Physics, Vol. 85 (Boca
Raton, FL: CRC Press)
Madronich, S., & Felder, W. 1985, [JPhCh,](https://doi.org/10.1021/j100262a026) 89, 3556
McCarthy, M. C., Lee, K. L. K., Loomis, R. A., et al. 2021, [NatAs,](https://doi.org/10.1038/s41550-020-01213-y) 5, 176
McClellan, A. L. 1963, Tables of Experimental Dipole Moments, Vol. 3 (San
Francisco, CA: Freeman)
McGuire, B. A., Burkhardt, A. M., Kalenskii, S., et al. 2018, [Sci,](https://doi.org/10.1126/science.aao4890) [359,](https://ui.adsabs.harvard.edu/abs/2018Sci...359..202M/abstract) 202
McGuire, B. A., Loomis, R. A., Burkhardt, A. M., et al. 2021, [Sci,](https://doi.org/10.1126/science.abb7535) 371, 1265
Møller, C., & Plesset, M. S. 1934, [PhRv,](https://doi.org/10.1103/PhysRev.46.618) [46,](https://ui.adsabs.harvard.edu/abs/1934PhRv...46..618M/abstract) 618
Mondal, S. K., Gorai, P., Sil, M., et al. 2021, [ApJ,](https://doi.org/10.3847/1538-4357/ac1f31) [922,](https://ui.adsabs.harvard.edu/abs/2021ApJ...922..194M/abstract) 194
Müller, H. S. P., Belloche, A., Xu, L.-H., et al. 2016, [A&A,](https://doi.org/10.1051/0004-6361/201527470) [587,](https://ui.adsabs.harvard.edu/abs/2016A&A...587A..92M/abstract) A92
Olmi, L., Cesaroni, R., & Walmsley, C. M. 1996, A&A, [307,](https://ui.adsabs.harvard.edu/abs/1996A&A...307..599O/abstract) 599
Parker, J. K., & Davis, S. R. 1999, [JACS,](https://doi.org/10.1021/ja984380o) 121, 4271



Rahul, K. K., Meka, J. K., Pavithraa, S., et al. 2020, [AcSpA,](https://doi.org/10.1016/j.saa.2019.117393) 224, [117393](https://ui.adsabs.harvard.edu/abs/2020AcSpA.22417393R/abstract)
Ravi, V. P., Jasra, R. V., & Bhat, T. S. 1998, [JChemTechBiotech,](https://doi.org/10.1002/(SICI)1097-4660(199802)71:23.0.CO;2-N) 71, 173
Reese, J. A., Nguyen, T. V., Korter, T. M., & Pratt, D. W. 2004, [JACS,](https://doi.org/10.1021/ja0469683) 126,
11387
Rolffs, R., Schilke, P., Zhang, Q., & Zapata, L. 2011, [A&A,](https://doi.org/10.1051/0004-6361/201117112) [536,](https://ui.adsabs.harvard.edu/abs/2011A&A...536A..33R/abstract) A33
Ruaud, M., Loison, J. C., Hickson, K. M., et al. 2015, [MNRAS,](https://doi.org/10.1093/mnras/stu2709) [447,](https://ui.adsabs.harvard.edu/abs/2015MNRAS.447.4004R/abstract) 4004
Sahu, D., Das, A., Majumdar, L., & Chakrabarti, S. K. 2015, [NewA,](https://doi.org/10.1016/j.newast.2014.12.011) [38,](https://ui.adsabs.harvard.edu/abs/2015NewA...38...23S/abstract) 23
Sahu, D., Liu, S.-Y., Das, A., Garai, P., & Wakelam, V. 2020, [ApJ,](https://doi.org/10.3847/1538-4357/aba0a5) [899,](https://ui.adsabs.harvard.edu/abs/2020ApJ...899...65S/abstract) 65
Santoro, D., & Louw, R. 2001, JChemSoc [Perkin](https://doi.org/10.1039/b004990p) Transactions, 2, 645
Seta, T., Nakajima, M., & Miyoshi, A. 2006, [JPCA,](https://doi.org/10.1021/jp0575456) 110, 5081
Shiner, C. S., Vorndam, P. E., & Kass, S. R. 1986, [JACS,](https://doi.org/10.1021/ja00279a006) 108, 5699
[Sil, M., Gorai, P., Das, A., Sahu, D., & Chakrabarti, S. K. 2017, EPJD, 71, 45](https://doi.org/10.1140/epjd/e2017-70610-4)
Sil, M., Gorai, P., Das, A., et al. 2018, [ApJ,](https://doi.org/10.3847/1538-4357/aa984d) [853,](https://ui.adsabs.harvard.edu/abs/2018ApJ...853..139S/abstract) 139
Sil, M., Srivastav, S., Bhat, B., et al. 2021, [AJ,](https://doi.org/10.3847/1538-3881/ac09f9) [162,](https://ui.adsabs.harvard.edu/abs/2021AJ....162..119S/abstract) 119
Taatjes, C. A., Osborn, D. L., Selby, T. M., et al. 2010, [JPCA,](https://doi.org/10.1021/jp9114145) [114,](https://ui.adsabs.harvard.edu/abs/2010JPCA..114.3355T/abstract) 3355
[Tercero, B., Vincent, L., Cernicharo, J., Viti, S., & Marcelino, N. 2011, A&A,](https://doi.org/10.1051/0004-6361/201015837)

528, A26
Tokmakov, I., & Lin, M.-C. 2002, [JPCA,](https://doi.org/10.1021/jp0211842) 106, 11309
Turecek, F., Drinkwater, D. E., Maquestiau, A., & McLafferty, F. W. 1989,

Organic Mass Spectrometry, 24, 669
Vastel, C., Bottinelli, S., Caux, E., Glorian, J. M., & Boiziot, M. 2015, in
SF2A-2015: Proc. Annual Meeting of the French Society of Astronomy and
Astrophysics, [313](https://ui.adsabs.harvard.edu/abs/2015sf2a.conf..313V/abstract)
Vasyunin, A. I., & Herbst, E. 2013, [ApJ,](https://doi.org/10.1088/0004-637X/769/1/34) [769,](https://ui.adsabs.harvard.edu/abs/2013ApJ...769...34V/abstract) 34
Wakelam, V., Smith, I. W. M., Herbst, E., et al. 2010, [SSRv,](https://doi.org/10.1007/s11214-010-9712-5) [156,](https://ui.adsabs.harvard.edu/abs/2010SSRv..156...13W/abstract) 13
Wang, H., & Frenklach, M. 1997, [CoFl,](https://doi.org/10.1016/S0010-2180(97)00068-0) 110, 173
Zhu, L., & Bozzelli, J. W. 2003, [JPCA,](https://doi.org/10.1021/jp0212545) [107,](https://ui.adsabs.harvard.edu/abs/2003JPCA..107.3696Z/abstract) 3696
Zhu, L., Chen, C.-J., & Bozzelli, J. W. 2000, [JPCA,](https://doi.org/10.1021/jp001531c) [104,](https://ui.adsabs.harvard.edu/abs/2000JPCA..104.9197Z/abstract) 9197



13


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Destruction of phenol in gas phase via photodissociation (alpha = 2.9 x 10^-9, beta = 0, gamma = 1.7), cosmic ray dissociation (alpha = 1.3 x 10^-17, beta = 0, gamma = 263.5), and major ions (C+, He+, HCO+, H3O+)",
  "failed_quote": "For the destruction of phenol in the gas phase, photodissociation (α = 2.9 × 10 [−][9], β = 0, and γ = 1.7 is used) and cosmic ray dissociation (α = 1.3 × 10 [−][17], β = 0, and γ = 263.5) are considered. Furthermore, its destruction by the major ions (C [+], He [+], HCO [+], and H 3 O [+] ) is also considered."
 }
]
```
