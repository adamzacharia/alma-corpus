# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...644A.102J\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
A&A 644, A102 (2020)
[https://doi.org/10.1051/0004-6361/202038200](https://doi.org/10.1051/0004-6361/202038200)
© A. Jabri et al. 2020


# **Astronom** **y**
### &
# **Astrophysics**


## **Rotational spectroscopic study of S-methyl thioformate**

#### **A global laboratory analysis of ground and excited torsional states** up to 660 GHz [⋆]

A. Jabri [1], B. Tercero [2,3], L. Margulès [4], R. A. Motiyenko [4], E. A. Alekseev [5], I. Kleiner [1],
J. Cernicharo [6], and J.-C. Guillemin [7]


1 Laboratoire Interuniversitaire des Systèmes Atmosphériques (LISA), UMR CNRS 7583, Université Paris-Est-Créteil,
Université de Paris, Institut Pierre Simon Laplace (IPSL), 61 av. du Général de Gaulle, 94010 Créteil, France
e-mail: `[kleiner@lisa.ipsl.fr](mailto:kleiner@lisa.ipsl.fr)`
2 Observatorio Astronómico Nacional (OAN-IGN). Calle Alfonso XII, 3, 28014 Madrid, Spain
3 Observatorio de Yebes (IGN). Cerro de la Palera s/n, 19141 Yebes, Guadalajara, Spain
4 Univ. Lille, CNRS, UMR 8523 - PhLAM - Physique des Lasers Atomes et Molécules, 59000 Lille, France
5 Radiospectrometry Department, Institute of Radio Astronomy of NASU, Kharkov, Ukraine
6 Instituto de Física Fundamental (IFF-CSIC). Calle Serrano 123, 28006 Madrid, Spain
7 Univ. Rennes, Ecole Nationale Supérieure de Chimie de Rennes, CNRS, ISCR-UMR 6226, 35000 Rennes, France


Received 19 April 2020 / Accepted 13 October 2020


**ABSTRACT**


_Context._ S-methyl thioformate CH 3 SC(O)H is a monosulfur derivative of methyl formate, a relatively abundant component of the
interstellar medium (ISM). S-methyl thioformate being, thermodynamically, the most stable isomer, it can be reasonably proposed for
detection in the ISM.
_Aims._ This work aims to experimentally study and theoretically analyze the ground and first torsional excited states for CH 3 SC(O)H
in a large spectral range for astrophysical use.
_Methods._ S-methyl thioformate was synthesized as a result of a reaction of methyl mercaptan with acetic-formic anhydride. The
millimeter-wave spectrum was then recorded for the first time from 150 to 660 GHz with the solid-state spectrometer located at Lille.
_Results._ A set of 3545 lines is determined and combined with 54 previously measured lines in the microwave region, belonging to
ground state ν t = 0 as well as 1391 transitions in the first excited state of torsion ν 18 = 1. Some 164 lines were also assigned to ν 18 = 2
for the A-species. A global fit was performed using the BELGI-C _s_ code taking into account the large splitting of A and E lines due to
methyl internal rotation motion with a relatively low barrier, _V_ 3 = 127.4846(15) cm [−][1] .
_Conclusions._ Using our spectroscopy work, a deep search of S-methyl thioformate was carried out in the IRAM 30 m and ALMA data
of different high-mass star-forming regions (Orion KL and Sgr B2). We derived an upper limit to the CH 3 SC(O)H column density in
these regions.


**Key words.** line: identification – catalogs – ISM: abundances – submillimeter: ISM – methods: laboratory: molecular



**1. Introduction**


In recent years, the detection of many complex organic
molecules (COMs) in the interstellar medium (ISM) and circumstellar envelopes has been made possible by substantial progress
accomplished in astrophysical observation. According to the
Cologne Database for Molecular Spectroscopy (CDMS, Endres
et al. 2016) and to the recent review of McGuire (2018), around
204 different molecules have been detected, and almost a third
of them contain more than five atoms (Herbst & Van Dishoeck
2009). Most of the molecular identifications were accomplished
by recording their spectra in the laboratory and comparing them
to the interstellar surveys by means of microwave, millimeter- or
submillimeter-wave telescopes.
The detection of molecular species in space by microwave,
millimeter- and submillimeter-wave telescopes would have been


⋆ Full Table A.1 is only available at the CDS via anonymous ftp
to `[cdsarc.u-strasbg.fr](http://cdsarc.u-strasbg.fr)` ( `[130.79.128.5](ftp://130.79.128.5)` ) or via `[http://cdsarc.](http://cdsarc.u-strasbg.fr/viz-bin/cat/J/A+A/644/A102)`
```
u-strasbg.fr/viz-bin/cat/J/A+A/644/A102

```


impossible without dedicated studies in the laboratory addressing the high-resolution rotational and rovibrational spectroscopy,
both in theory and experimentally, of relevant species. Precise
knowledge of the rotational spectra was the key point for the
detections of many complex molecules compiled and updated
in the existing international databases such as CDMS (Endres
et al. 2016), Splatalogue, `JPL` `[catalog](http://spec.jpl.nasa.gov)` (Pickett et al. 1998),
`NIST` `[catalog](http://physics.nist.gov/restfreq/)` (Lovas 2004), and Toyama Microwave Atlas for
spectroscopists and astronomers. To gain this knowledge, a common strategy is to combine experimental microwave, millimeterand submillimeter-wave spectroscopy, followed by the analysis
of these spectra using appropriate effective quantum mechanical
Hamiltonians and ab initio calculations, if no information on the
rotational constants is available from previous studies.
In the last decades, several molecules exhibiting internal
rotations of the methyl CH 3 group have been detected in the
interstellar and circumstellar media; for example, methanol
(CH 3 OH, Ball et al. 1970), methyl formate and its isotopologues
(HCOOCH 3, Churchwell & Winnewisser 1975; Demyk et al.
2008; Favre et al. 2014; Carvajal et al. 2009; Haykal et al. 2014;


A102, page 1 of 9



[Open Access article, published by EDP Sciences, under the terms of the Creative Commons Attribution License (](https://www.edpsciences.org) `[https://creativecommons.org/licenses/by/4.0](https://creativecommons.org/licenses/by/4.0)` ),
which permits unrestricted use, distribution, and reproduction in any medium, provided the original work is properly cited.

A&A 644, A102 (2020)



Kobayashi et al. 2013), acetaldehyde (CH 3 CHO, Fourikis et al.
1974), acetic acid (CH 3 COOH, Mehringer et al. 1997; Remijan
et al. 2003), and acetamide (CH 3 CONH 2, Hollis et al. 2006).
Sulfur-bearing molecules are important species when it
comes to understanding the chemical evolution of hot cores,
and their molecular ratios have previously been used as chemical clocks to obtain information about the age of those hot
cores (Wakelam et al. 2004; Charnley 1997). However, the
chemistry of interstellar sulfur is still not well understood. The
observed abundance of sulfur-bearing species in dense clouds
only represents about 0.1% of the abundance of sulfur in diffuse clouds (where it corresponds almost to its solar abundance).
There is still some mystery surrounding this missing sulfur and
what its reservoir would be (Anderson et al. 2013). About 20
different molecules containing sulfur have been identified in
space so far, and among them, only methyl mercaptan (CH 3 SH)

−
exhibits observable internal rotation splitting (called A E splitting) (Linke et al. 1979; Xu et al. 2012; Kolesniková et al. 2014;
Zakharenko et al. 2019).
S-methyl thioformate CH 3 SC(O)H is the sulfur analog of
methyl formate CH 3 OC(O)H, a relatively abundant and ubiquitous molecule in the ISM (Brown et al. 1975; Churchwell &
Winnewisser 1975). It is also detected in the comet Hale-Bopp
(Bockelée-Morvan et al. 2000) and in low-mass star-forming
regions (hot corinos) such as NGC 1333-IRAS4B and IRAS2A
(Bottinelli et al. 2007). Methyl thioformate can be thus considered as a potentially detectable species in this medium because
most of the abundant oxygen derivatives have the corresponding
sulfur derivative detected in the ISM (Cernicharo et al. 1987).
Relatively few laboratory spectroscopic studies exist on internal rotors containing sulfur, and in the case of methyl thioformate those studies mainly concern transitions in the ground
torsional state ν t = 0. Two isomers exist for methyl thioformate where either the sp [3] oxygen atom of methyl formate
HCOOCH 3 is substituted by a sulfur atom (S-methyl thioformate
CH 3 SC(O)H) or the sp [2] oxygen is substituted (O-methyl thioformate CH 3 OC(S)H). In 2014 Senent et al. (2014) performed highlevel quantum chemical calculations to determine the spectroscopic parameters (rotational and centrifugal distortion constants
as well as the potential barrier hindering the internal rotation of
the methyl group). They also characterized the relative energies
for the two isomers, CH 3 SC(O)H and CH 3 OC(S)H. Figure 2 of
Senent et al. (2014) shows the two isomers with their possible
conformers, cis- and trans-, depending on the position of the
methyl group relative to that of the C = O or C = S bonds for
CH 3 SC(O)H and CH 3 OC(S)H, respectively. The cis- S-methyl
thioformate CH 3 SC(O)H is determined as the most stable structure at 1134 cm [−][1] below the trans- CH 3 SC(O)H, and at 4372.2
and 6335.8 cm [−][1] below the cis- and trans- configurations of
O-methyl thioformate CH 3 OC(S)H, respectively. In the present
paper, we focus on the spectroscopy of the cis- S-methyl thioformate CH 3 SC(O)H as it corresponds to the most stable species.
To our knowledge, only two spectroscopic studies are available for CH 3 SC(O)H: Jones et al. (1976) recorded the microwave
spectrum between 10 and 41 GHz, as well as an infrared spectrum recorded at low resolution between 50 and 4000 cm [−][1] .
Although they measured about 40 lines of the torsional
A-species in the R-branch (corresponding to the a-type selection
rule) and in the R- and Q-branches (corresponding to the b-type

−
selection rule), their search for the A E splitting due to internal
rotation was unsuccessful because of the poor information about
the barrier height to internal rotation _V_ 3 . Self consistent field
(SCF) ab initio calculations allowed them to conclude that their
measured lines correspond to the cis- CH 3 SC(O)H isomer. Using


A102, page 2 of 9



Stark-effect measurements, they were able to determine the electric dipole moment values µ _a_ and µ _b_ in the principal axis system
to be 1.52 and 0.43 Debye, respectively. Later on, Caminati
et al. (1981) recorded the microwave spectrum of CH 3 SC(O)H
between 10 and 40 GHz with a cold cell at 235 K. They also performed double resonance microwave measurements that allowed
them to confirm the identification of the E-species lines. In total,
they measured 22 and 15 lines belonging to the internal A- and
E-rotation states, respectively, up to _J_ = 20. They fit the 37 lines
using 11 parameters. However, their study shows discrepancies
up to 5.7 MHz when comparing the observed line positions to
the calculated values (see Tables I and II of the ref. Caminati
et al. 1981).
In this context, the goal of the present work is to extend, for
the first time, the spectroscopic measurements of CH 3 SC(O)H
in the millimeter- and submillimeter-wave spectral ranges in
order to produce a reliable line list of frequencies and intensities
to be used for searching the molecule in space. Section 2
presents the experimental details, including the synthesis of the
S-methyl thioformate. Section 3 contains a presentation of the
theoretical model used for data analysis. The second part of
this section is dedicated to assignments and fits of the spectral
data. Section 4 presents the intensity calculation and the line
lists for astronomers. Section 5 corresponds to the astronomical
search for CH 3 SC(O)H in the ISM. Section 6 is dedicated to the
discussion of our results.


**2. Experimental details**


_2.1. Chemical synthesis_


To prepare S-methyl thioformate CH 3 SC(O)H, we modified the
synthesis of Hershfield & Schmir (1972). In a Schlenk flask,
methanethiol (methyl mercaptan, CH 3 SH; 0.1 mol) was slowly
added to acetic-formic anhydride (0.1 mol) at a temperature ranging from 5 to 10 [◦] C. The flask was immersed in a liquid nitrogen
bath, degassed, and then closed with the stopcock. The mixture was stirred for 36 h at 35 [◦] C. Then, a distillation with a
short Vigreux Column (20 cm) gave a first fraction containing
the S-methyl thioformate and about 30% of formic and acetic
acids. Purification was performed in a vacuum line (0.1 mbar)
with a first trap cooled at −50 [◦] C to remove both carboxylic
acids, and a second trap cooled at −90 [◦] C to selectively condense the S-methyl thioformate, which was thus obtained in a
37% yield.


_2.2. Spectra measurements_


The measurements in the frequency range under investigation
(150−660 GHz) were performed using the Lille spectrometer
(Zakharenko et al. 2015). The absorption cell was a stainlesssteel tube (6 cm in diameter, 220 cm in length). The sample
pressure during measurements was about 10 Pa and at room
temperature, the line width was limited by Doppler broadening. The frequency ranges, 150−330 and 400−660 GHz, were
covered with various active and passive frequency multipliers
from Virginia Diodes, Inc.(VDI Inc) and an Agilent synthe
−
sizer (12.5 18.25 GHz) was used as the source of radiation. As
a detector, we used an InSb liquid He-cooled bolometer from
QMC Instruments Ltd to improve the sensitivity of the spectrometer. The sources were frequency modulated at 30 kHz.
Estimated uncertainties for measured line frequencies are 30 and
50 kHz depending on the observed signal-to-noise (S/N) and
the frequency range. Uncertainties of 100 kHz are also given to
relatively broad transitions or presenting a weak S/N.

A. Jabri et al.: Rotational spectroscopic study of S-methyl thioformate



**3. Results**


_3.1. Theoretical model_


The S-methyl thioformate contains one methyl group internal
rotor with a rather low torsional barrier hindering this motion,
which was estimated by Caminati et al. (1981) to be _V_ 3 =
147.96 cm [−][1] . Therefore, the rotational analysis of its spectra
requires a suitable theoretical model and Hamiltonian to treat
the internal rotation splitting between the A- and E-species.
In the present work, we used the BELGI-C _s_ [1] program
(Hougen et al. 1994) using the rho-axis method (RAM) with a
two-step procedure initially described by Herbst et al. (1984).
The BELGI-C _s_ code was previously applied successfully to a
number of interstellar molecules containing an internal methyl
rotor and was used in particular for the parent species of the
cis- methyl formate (Carvajal et al. 2007) as well as for its
13 C isotopic species H 13 COOCH 3 and HCOO 13 CH 3 (Carvajal
et al. 2009), [18] O isotopologues HC [18] OOCH 3 and HCO [18] OCH 3
(Tercero et al. 2012), and deuterated species DCOOCH 3 (Duan
et al. 2015). The method takes its name from the choice of the
axis system, which allows us to minimize the coupling between
internal rotation and global rotation in the Hamiltonian, at least
in the zeroth order. As it has been described in the literature (Lin
& Swalen 1959; Hougen et al. 1994; Kleiner 2010) and applied
extensively, we do not repeat it here.
The BELGI-C _s_ program uses a global approach since it takes
into account the A- and E-symmetry states simultaneously, as
well as all the ν t torsional levels originating from a given vibrational state, up to a truncation level. The interactions between
rotation-torsion energy levels are treated explicitly within the
Hamiltonian matrix elements. In our approach, only one set of
rotational constants and parameters that describe the potential
are fit for all the torsional states for a given vibrational state.
In the so-called RAM used in the BELGI-Cs code, we do
not use the Principal Axis System (PAS). To simplify the calculations and to get rid at the zeroth order of the torsion-rotation
interaction terms, we use a non-principal axis system (called the
rho-axis system (RAS); Kleiner 2010). As a consequence, we
fit the _D_ _ab_ parameter, which multiplies the _P_ _a_ _P_ _b_ + _P_ _b_ _P_ _a_ offdiagonal operator, where _P_ _a_ and _P_ _b_ designate the projection
of the total rotational angular momentum on the _a_ and _b_ axes,
respectively. The _D_ _ab_ parameter is related to the θ RAM angle
between the _z_ axis of the PAS and RAS, as described by Kleiner
(2010):



2 _D_ _ab_

θ RAM = [1]

2 [arctan] � _A_ RAM − _B_ RAM



. (1)
�



The torsional frequency mode v 18 for the cis- S-methyl thioformate is predicted to lie between 80 and 111 cm [−][1] depending
on the level of theory used (see Tables III and VII of the ref.
Senent et al. 2014). Other low-frequency vibrational modes can
also be responsible for rotational transitions observed in the
spectrum, such as the v 17 mode (torsion of the CO group) calculated to be around 250 cm [−][1], the v 12 mode (bending of the CSC
bond) observed at 245 cm [−][1] and the v 11 mode (bending of the
OCS bond) observed at 320 cm [−][1] (Senent et al. 2014). However,
our present model does not take into account the interactions
between the ground state and v 17, v 12 or v 11 .


_3.2. Millimeter- and submillimeter-wave spectral analysis_


First, we performed a preliminary fit using the microwave data
measured by Jones et al. (1976) and Caminati et al. (1981)
between 10 and 41 GHz in order to obtain the overall rotation
and the internal rotation constants in the RAS using the BELGIC _s_ program. These preliminary parameters allowed us to obtain
a starting prediction of the millimeter-wave spectrum between
150 and 330 GHz in the ground torsional state ν t = 0. Eventually,
we pursued our assignments up to 660 GHz.
Following Jones et al. (1976), the electric dipole moment is
maximal along the a principal axis (µ _a_ = 1.52 D; µ _b_ = 0.43 D).
Therefore, rotational structures of a-type R-branch series were
identified with a shift between 2 and 10 MHz for lines with
_K_ _a_ ⩽ 5. Then, lines belonging to higher _J_ and _K_ _a_ values were
progressively assigned and added to the fit. After the a-type
transitions were analyzed, we also succeeded in assigning some
b-type transitions, even though they are approximatively 12 times
less intense [( [µ] µ _[a]_ _b_ [)] [2] [≈] [12][.][5].] [In] [this] [process,] [we] [simultaneously]

assigned A- and E-type transitions, for _J_ values up to 75. The
same assignment process was pursued in the first and second
excited torsional states ν t = 1 and 2.
The spectrum was recorded at room temperature close to
300 K. For this reason, it was very dense (as shown in Fig. 1)
since it contains not only rotational transitions of the ground
state but also those belonging to the low-lying excited states, as
mentioned earlier in Sect. 3.1.
In total, 5154 rotational transitions were assigned in our
model and fit with experimental accuracy for _J_ and _K_ _a_ values
up to 75 and 24, respectively. We weighted all lines into four
sets corresponding to differences in measurement accuracy. The
first set corresponds to isolated lines with a weight corresponding to (∆1ν) [2] [, where][ ∆][ν][ is the measurement uncertainty of 30 kHz.]
The second set is weighted corresponding to the measurement
accuracy of 50 kHz since they are blended lines and their energy
levels are degenerated. The third given set weighted to 100 kHz
corresponds to relatively broad transitions or those with a weak
(S/N) ratio. Finally, we weighted the microwave transitions measured in earlier studies by Jones et al. (1976) and Caminati et al.
(1981) to 150 kHz. Indeed, in our fit those lines seem to fit with
larger residuals than the measurement accuracy of 100 kHz estimated by those authors. The quality of our fit is presented in
Table 1, with the unitless standard deviations for each torsional

state.
A global unitless standard deviation of 1.01 was obtained
by floating 61 parameters for 3599 transitions belonging to
the ground state ν t = 0, 1391 transitions for ν 18 = 1, and 164
transitions for ν 18 = 2. Table 2 shows the values of the 61 molecular parameters obtained by the fit using the BELGI-C _s_ code
together with the operators that those parameters multiply. The
three rotational constants _A_, _B_, and _C_ as well as the quartic
centrifugal distortion (∆ _J_, ∆ _JK_, ∆ _K_, δ _J_ and δ _K_ ) and three sextic


A102, page 3 of 9



Morever, in the BELGI-C _s_ code, a two-step diagonalisation
procedure is used to calculate the energy levels. First, a set of
calculations are carried out to diagonalize the torsion part of the
Hamiltonian for each _K_ = _K_ _a_ value. Then in the second step, the
rest of the Hamiltonian terms (rotational, centrifugal distortion,
and interaction terms between rotation and torsion) are diagonalized. The RAM method has been sucessfully applied to a
number of astrophysical internal rotors, such as methyl formate
(Carvajal et al. 2007, 2009). As described further in Sect. 4, the
BELGI-C _s_ program also has an option allowing us to calculate
the line strengths (using the RAM values for the electric dipole
moments).


1 The source code BELGI for the fit, an example of input data file
and a readme file are available at the web site `[PROSPE,](http://www.ifpan.edu.pl/~kisiel/prospe.htm)` managed by
Dr. Zbigniew Kisiel. Extended versions of code are also available by
contacting the author I. Kleiner.

A&A 644, A102 (2020)


**[Fig. 1.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/202038200&pdf_id=0)** _Upper panel_ : section of experimental spectrum between 264 and 282 GHz (in black) compared to calculated spectra obtained from our fit
parameters described in Table 2. _Lower panel_ : expanded view of the 271.96−273.96 GHz region showing the assignments (A-species of the GS in
red, E-species of the GS in blue, A-species of the ν 18 = 1 mode in green, E-species of the ν 18 = 1 mode in orange, and A-species of the ν 18 = 2 mode
in magenta).



constants ( _H_ _J_, _H_ _KJ_ and _H_ _K_ ) were determined. As explained in
Sect. 3.1, in the RAM we also need to fit a parameter ( _D_ _ab_ )
that corresponds to the fact that the inertial tensor is not diagonal. The height of the potential barrier _V_ 3 was determined as
127.4846(15) cm [−][1] . We note that as we globally fit the data from
ν t = 0, 1 and 2, we were also able to determine the value of the


A102, page 4 of 9



internal rotation constant _F_ = 5.332339(21) cm [−][1], and the second and the third terms in the cosine expansion of the potential
( _V_ 6 = 24.3418(94) cm [−][1], _V_ 9 = 6.567(21) cm [−][1] ). Forty-five interaction parameters between rotation and torsion (such as ρ, _c_ 2,
_c_ 4, _k_ 5, _k_ 2, _k_ 1, etc.), as defined in Table 2, were also necessary to
reproduce the observed transitions.

A. Jabri et al.: Rotational spectroscopic study of S-methyl thioformate


**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/202038200&pdf_id=0)** **2.** _Left_ _plot_ : variation of A−E splittings with _J_ values for R-type branches of CH 3 SC(O)H in the ground state (upper trace) and in the first
torsional state ν 18 = 1 (lower trace). _Right plot_ : obtained energy levels from our BELGI-C _s_ analysis compared to those determined by Senent et al.
(2014) with quantum chemical calculations.



**Table** **1.** Overview on the quality of measured lines included in the
BELGI-C _s_ fit, for the ground state (GS) and the two first excited states
ν 18 = 1 and ν 18 = 2.


Mm-wave and submm-wave data Mw data [(] _[a]_ [)]


G.S ν 18 = 1 ν 18 = 2 G.S


_J_ max 75 75 75 20
_K_ max 24 13 3 6
_N_ _A_ / _N_ _E_ [(] _[b]_ [)] 1831/1714 720/671 164/0 43/11
Std. dev. [(] _[c]_ [)] 0.89 1.20 1.43 0.66


**Notes.** ( _a_ ) These 54 lines were measured by Jones et al. (1976) and
Caminati et al. (1981) in the microwave domain between 10 and 41 GHz,
and they were added to our new measured 3545 rotational transitions
in the final fit. The total number of ground-state ν t = 0 transitions is
thus 3599. [(] _[b]_ [)] Number of A- and E-transitions included in our BELGI-C _s_
global fit. [(] _[c]_ [)] Unitless standard deviation of the fit.


Using the set of parameters of Table 2, the millimeter- and
submillimeter-wave spectra measured between 150 and 660 GHz
are very well reproduced to experimental accuracies, and the
main strong rotational lines are assigned as shown in Fig. 1,
where a section of 18 GHz (upper part) is presented with a
zoomed portion of 2 GHz (lower part).
The internal rotation effect for the CH 3 SC(O)H molecule
is quite large in comparison with methyl formate. Its barrier
height _V_ 3 is determined to be relatively low in comparison
with its oxygenated analog methyl formate, CH 3 OC(O)H, for
which _V_ 3 = 372.6720(42) cm [−][1] (Ilyushin et al. 2009). As a result,
the A−E splittings are larger in our case where, for _K_ _a_ ⩽ 3,
differences between A- and E-frequencies vary from −150 to
250 MHz instead of only few MHz for methyl formate for the
ground torsional ν _t_ = 0 state. Moreover, this splitting between Aand E-levels becomes larger for excited torsional states (ν 18 = 1
and ν 18 = 2), going up to some GHz. The left panel of Fig. 2
shows the variation of those A−E splittings with increasing _J_ for
ground state (upper trace) and for the first excited state (lower
trace). Therefore, the use of a suitable theoretical model based
on the RAM is needed to predict these rotational lines correctly.
Indeed, the global approach used in the BELGI-C _s_ code allows



us to treat all the torsional states together in the fit and to deal
with the torsion-rotation interaction terms.
In the right panel of Fig. 2, we also compare the torsional
energy levels determined by ab initio calculations (Senent et al.
2014) with those determined using our parameters from the fit.
The agreement between our observations and those calculations
is quite good.


**4. Intensity calculation**


For calculations of the line strengths, we used the same procedure as the one described in detail in Sect. 3.2 of Kleiner 2010.
This method had been used for different molecules with C _s_ symmetry containing one methyl rotor such as methyl formate and
its isotopologues (Favre et al. 2014; Carvajal et al. 2009, 2007;
Haykal et al. 2014; Tercero et al. 2012; Duan et al. 2015) or vinyl
acetate (Kolesnikova et al. 2015). We used the BELGI-C _s_ code
to calculate the line strengths, using the energy parameters determined in Table 2. In the same way that the Hamiltonian was used
in the calculation and fit of the line positions in the RAM, the
calculation of the line strengths also has to be carried out in this
same axis system. For this purpose, the components of the dipole
moment µ _a_ and µ _b_ obtained by Stark measurements (Jones et al.
1976) were thus transformed in the RAM system using Eq. (20)
of Kleiner (2010) and determined to be 1.527 Debye and −0.404
Debye, respectively. The value of the angle between the PAS and
the RAS was calculated using Eq. (1) to be 30.6 [◦] .
The line frequencies, line strengths ( _S_ .µ [2] ), and lower state
energies, as well as the assignments for the observed transitions
of CH 3 SC(O)H in the millimeter-wave and submillimeter-wave
ranges are shown in Table A.1. Using a method and a code
developed by Favre et al. (2014); Carvajal et al. (2019), we calculated the partition function for an internal rotor, including the
torsional contribution. The values of the partition function are
presented in Table A.2 for temperatures allowing the search of
this molecule in different regions in warm molecular clouds of
the ISM.


**5. Search for methyl thioformate in space**


Using the rotational constants of Table 2 and the MADEX code
(Cernicharo 2012), we searched for methyl thioformate in warm


A102, page 5 of 9

A&A 644, A102 (2020)


**Table 2.** Spectroscopic parameters of CH 3 SC(O)H in the RAM obtained with the BELGI-C _s_ program.


_nlm_ [(] _[a]_ [)] Operator [(] _[b]_ [)] Par. [(] _[c]_ [)] Value [(] _[d]_ [)] _nlm_ [(] _[a]_ [)] Operator [(] _[b]_ [)] Par. [(] _[c]_ [)] Value [(] _[d]_ [)]

220 12 [(1][ −] [cos 3][α][)] _V_ 3 127.4846(15)
_P_ [2] α _F_ 5.332339(21) (1 − cos 6α)( _P_ _a_ _P_ _b_ + _P_ _b_ _P_ _a_ ) _dd_ _ab_ −3.4755(32) × 10 [−][4]

211 _P_ α _P_ _a_ ρ 0.03644877(22) (1 − cos 6α)( _P_ [2] _b_ [−] _[P]_ _c_ [2] [)] _c_ 11 −4.376(19) × 10 [−][5]

202 _P_ [2] _a_ _A_ 0.22208287(97) _P_ [4] α _[P]_ _a_ [2] _K_ 1 −3.546(18) × 10 [−][7]

_P_ [2] _b_ _B_ 0.3162569(10) _P_ [4] α _[P]_ [2] _M_ v 2.519(39) × 10 [−][8]

_P_ [2] _c_ _C_ 0.119194004(55) (1 − cos 6α) _P_ [2] _a_ _K_ 2 2.2583(42) × 10 [−][4]

( _P_ _a_ _P_ _b_ + _P_ _b_ _P_ _a_ ) _D_ _ab_ −0.08605178(54) 624 (1 − cos 3α) _P_ [2] _P_ [2] _a_ _k_ 5 _J_ 7.098(84) × 10 [−][8]

440 12 [(1][ −] [cos 6][α][)] _V_ 6 24.3418(94) (1 − cos 3α) _P_ [4] _a_ _k_ 5 _K_ −7.145(86) × 10 [−][8]

_P_ [4] α _k_ 4 −9.832(68) × 10 [−][4] (1 − cos 3α) _P_ [4] _f_ v 8.330(78) × 10 [−][9]

431 _P_ [3] α _[P]_ _[a]_ _k_ 3 1.2310(35) × 10 [−][4] (1 − cos 3α)( _P_ [2] _b_ [−] _[P]_ _c_ [2] [)] _[P]_ [2] _c_ 2 _J_ 4.613(78) × 10 [−][9]

_P_ [3] α _[P]_ _[b]_ _ESPOIR_ −5.134(32) × 10 [−][5] (1 − cos 3α){ _P_ [2] _a_ [,][ (] _[P]_ [2] _b_ [−] _[P]_ _c_ [2] [)][}] _c_ 2 _K_ 5.023(27) × 10 [−][8]

422 _P_ [2] α _[P]_ [2] _G_ v −9.521(32) × 10 [−][6] (1 − cos 3α)( _P_ _a_ _P_ _b_ + _P_ _b_ _P_ _a_ ) _P_ [2] _d_ _abJ_ 2.639(40) × 10 [−][8]

2 _P_ [2] α [(] _[P]_ [2] _b_ [−] _[P]_ _c_ [2] [)] _c_ 1 −5.088(17) × 10 [−][6] (1 − cos 3α)( _P_ [3] _a_ _[P]_ _[b]_ [+] _[ P]_ _[b]_ _[P]_ [3] _a_ [)] _d_ _abK_ −5.188(44) × 10 [−][8]

(1 − cos 3α) _P_ [2] _F_ v −8.7206(42) × 10 [−][4] _P_ [2] α _[P]_ _a_ [2] _[P]_ [2] _k_ 2 _J_ −9.19(45) × 10 [−][11]

(1 − cos 3α) _P_ [2] _a_ _k_ 5 1.4439(14) × 10 [−][3] sin 3α _P_ [2] { _P_ _a_, _P_ _c_ } _D_ _acJ_ −4.98(26) × 10 [−][9]

(1 − cos 3α)( _P_ [2] _b_ [−] _[P]_ _c_ [2] [)] _c_ 2 2.3162(44) × 10 [−][4] sin 3α _P_ [2] { _P_ _b_, _P_ _c_ } _D_ _bcJ_ −3.028(26) × 10 [−][9]

(1 − cos 3α)( _P_ _a_ _P_ _b_ + _P_ _b_ _P_ _a_ ) _d_ _ab_ −3.47891(53) × 10 [−][3] 633 _P_ [3] α _[P]_ [2] _[P]_ _[a]_ _k_ 3 _J_ −3.18(17) × 10 [−][9]

_P_ [2] α _[P]_ _a_ [2] _k_ 2 7.797(87) × 10 [−][6] _P_ [3] α _[P]_ _a_ [3] _k_ 3 _K_ 1.731(29) × 10 [−][8]

_P_ [2] α [(] _[P]_ _[a]_ _[P]_ _[b]_ [+] _[ P]_ _[b]_ _[P]_ _[a]_ [)] ∆ _ab_ 5.640(27) × 10 [−][6] _P_ _a_ _P_ [3] α [(] _[P]_ [2] _b_ [−] _[P]_ _c_ [2] [)] _c_ 12 1.287(84) × 10 [−][9]

sin 3α( _P_ _a_ _P_ _c_ + _P_ _c_ _P_ _a_ ) _D_ _ac_ 5.47(15) × 10 [−][5] 606 _P_ [6] _H_ _J_ −0.02220(10) × 10 [−][12]

sin 3α( _P_ _b_ _P_ _c_ + _P_ _c_ _P_ _b_ ) _D_ _bc_ 1.320(12) × 10 [−][4] _P_ [2] _P_ [4] _a_ _H_ _KJ_ −2.112(16) × 10 [−][12]

413 _P_ α _P_ _a_ _P_ [2] _L_ v 3.4869(48) × 10 [−][6] _P_ [6] _a_ _H_ _K_ 2.854(27) × 10 [−][12]

_P_ α _P_ [3] _a_ _k_ 1 −3.0770(63) × 10 [−][6] 660 12 [(1][ −] [cos 9][α][)] _V_ 9 6.567(21)
_P_ α { _P_ _a_, ( _P_ [2] _b_ [−] _[P]_ _c_ [2] [)][}] _c_ 4 1.8914(18) × 10 [−][6] _P_ [6] α _k_ 4 _B_ −1.946(26) × 10 [−][5]

_P_ _a_ _P_ α ( _P_ _a_ _P_ _b_ + _P_ _b_ _P_ _a_ ) δ _ab_ −1.7256(37) × 10 [−][6] 651 _P_ [5] α _[P]_ _[a]_ _k_ 3 _B_ 4.450(17) × 10 [−][6]

404 − _P_ [4] ∆ _J_ 1.9298(55) × 10 [−][7] 615 _P_ _a_ _P_ α _P_ [2] _P_ [2] _a_ _k_ 1 _J_ 3.776(69) × 10 [−][11]

− _P_ [2] _P_ [2] _a_ ∆ _JK_ 3.590(18) × 10 [−][7] _P_ _a_ _P_ α _P_ [4] _a_ _k_ 1 _K_ −5.12(11) × 10 [−][11]

− _P_ [4] _a_ ∆ _K_ −5.3604(43) × 10 [−][7] _P_ _a_ _P_ α { _P_ [2] _a_ [,][ (] _[P]_ [2] _b_ [−] _[P]_ _c_ [2] [)][}] _c_ 4 _K_ 6.54(25) × 10 [−][12]

−2 _P_ [2] ( _P_ [2] _b_ [−] _[P]_ _c_ [2] [)] δ _J_ 0.7803(27) × 10 [−][7] 844 (1 − cos 6α) _P_ [4] _N_ v _J_ 6.710(16) × 10 [−][10]

−{ _P_ [2] _a_ [,][ (] _[P]_ [2] _b_ [−] _[P]_ _c_ [2] [)][}] δ _K_ 2.6080(13) × 10 [−][7] (1 − cos 6α) _P_ [2] _P_ [2] _a_ _K_ 2 _J_ 2.445(63) × 10 [−][9]

( _P_ _a_ _P_ _b_ + _P_ _b_ _P_ _a_ ) _P_ [2] _D_ _abJ_ 9.768(58) × 10 [−][8]

642 (1 − cos 6α) _P_ [2] _N_ v −1.6163(20) × 10 [−][4]


**Notes.** All values of these rotational constants are in cm [−][1], except for ρ, which is unitless. [(] _[a]_ [)] _n_ = _l_ + _m_, where _n_ is the total order of the operator,
_l_ is the order of the torsional part, and _m_ is the order of the rotational part. [(] _[b]_ [)] _P_ _a_, _P_ _b_ and _P_ _c_ are the components of the overall rotational angular
momentum. _P_ α is the angular momentum of the internal rotor. {u,v} is the anticommutator _uv_ +vu. [(] _[c]_ [)] The product of the parameter and operator
from a given row yields the term actually used in the vibration-rotation-torsion Hamiltonian, except for _F_, ρ and _A_, which occur in the Hamiltonian
in the form _F_ ( _P_ α − ρ _P_ _a_ ) [2] + _AP_ _a_ [(] _[d]_ [)] Values of the parameters from the present fit for ν _t_ = 0, 1, and 2. Statistical uncertainties are given in parentheses
in units of the last quoted digits.



**Table 3.** S-methyl thioformate column densities.


Orion KL [(] _[a]_ [)] Orion KL [(] _[a]_ [)] Sgr B2 [(] _[b]_ [)]

(MF peak) (ET peak) (IRAM 30m)


Coordinates α = 05 [h] 35 [m] 14.1 [s] α = 05 [h] 35 [m] 14.4 [s] α = 17 [h] 47 [m] 20.0 [s]


(J2000.0) δ = −05 [◦] 22 [′] 36.8 [′′] δ = −05 [◦] 22 [′] 34.74 [′′] δ = −28 [◦] 22 [′] 19.0 [′′]


_HPBW_ [(] _[c]_ [)] ( [′′] ) ∼2.0 × 1.5 ∼2.0 × 1.5 30−21
Freq. [(] _[d]_ [)] (GHz) 213.7−246.6 213.7−246.6 80−115.5
v LSR (km s [−][1] ) 7.5 8.0 63.5 / 73.5
∆v FWHM (km s [−][1] ) 2.0 3.0 7.0 / 7.0
_d_ sou ( [′′] ) 3.0 3.0 4.0 / 4.0
_T_ rot (K) 150 150 80 / 80


_N_ (CH 3 SCOH) ≤1.0 × 10 [14] ≤1.0 × 10 [14] ≤2.0 / 1.0 × 10 [16]

(cm [−][2] )


**Notes.** ( _a_ ) Physical parameters derived for the main spectral component
of HCOOCH 3 by Tercero et al. (2018). [(] _[b]_ [)] Physical parameters derived for
two spectral components of HCOOCH 3 by Belloche et al. (2013). [(] _[c]_ [)] Half
power beam width (HPBW) for observations with a single-dish telescope (IRAM 30m) and synthetic beam for the ALMA SV observations.
( _d_ ) Range of frequencies considered in the analysis.


A102, page 6 of 9



molecular clouds. High-mass star-forming regions are the best
candidates for this search. On one hand, it is well known that
methyl formate is one of the most abundant species in hot
cores. In addition, these regions are associated with molecular
outflows in which large abundances of sulfur-bearing species
arise (see e.g., Esplugues et al. 2013; Crockett et al. 2014;
Luo et al. 2019; Belloche et al. 2013). On the other hand, one
of the HCOOCH 3 derivatives, ethyl formate (HCOOCH 2 CH 3 ),
has only been unambiguously detected in this kind of region
(Belloche et al. 2009, 2013; Tercero et al. 2013, 2015, 2018;
Rivilla et al. 2017; Marcelino et al. 2018). Therefore, we mainly
focused on the available astronomical data of Orion KL and
Sgr B2. Our frequency predictions are sufficiently reliable for
_a_ -type transitions up to 300 GHz, which is the range of the
astronomical search. Nevertheless, owing to the high line density of the data and in order to ensure the line identification,
we restricted our search to transitions with uncertainties in the
predicted frequency of less than 0.1 MHz.
We used the ALMA science verification (SV) data of Orion
KL between 213.7 and 246.6 GHz (for observations and data
reduction, see e.g., Tercero et al. 2018) and the IRAM 30 m,

A. Jabri et al.: Rotational spectroscopic study of S-methyl thioformate


**Table 4.** Comparison of spectroscopic constants of CH 3 SC(O)H, obtained by BELGI-C _s_, fit with those determined in previous experimental and
theoretical investigations.


Parameter Unit Present work Previous Mw Ab initio study [(] _[b]_ [)]

work [(] _[a]_ [)] Ground state ν 18 = 1


_A_ MHz 11 010.242(32) 11 035.13(19) 11 043.16 11 117.07
_B_ MHz 5128.785(88) 5099.99(13) 5113.37 5061.61
_C_ MHz 3573.3379(28) 3561.570(30) 3570.06 3552.91
∆ _J_ kHz 5.785301(16) 3.10(50) 3.482
_V_ 3 cm [−][1] 127.4846(15) 150.47(1.67) 139.7
_V_ 6 cm [−][1] 24.3418(94) 25.4
_N_ [(] _[c]_ [)] 5154 37

Std. dev. unitless 1.01


**Notes.** Overall rotational constants _A_, _B_, and _C_ are transformed into the PAS, as explained in the text. [(] _[a]_ [)] Constants taken from the previous
microwave study (ν _t_ = 0) of Caminati et al. (1981). [(] _[b]_ [)] Values obtained by Senent et al. (2014) using ab initio calculations at the CCSD(T)/VTZ level
of theory. [(] _[c]_ [)] Total number of measured lines used in the fit.



3 mm survey of Sgr B2 provided by Belloche et al. (2013). In the
ALMA data, we concentrated the search in the emission peaks of
methyl (MF and ET peaks of Tercero et al. 2018). These positions
also seem to be associated with the molecular outflow driven by
source _I_ (see Tercero et al. 2018 and references therein).
We did not find this species above the detection limit of both
sets of data. To provide upper limits to its column density, we
used MADEX to derive the synthetic spectrum of CH 3 SC(O)H
for both sources assuming local thermodynamic equilibrium
(LTE) and the same physical parameters as those derived for
methyl formate by Tercero et al. (2018) and Belloche et al.
(2013) in Orion KL and Sgr B2, respectively. The results are
summarized in Table 3.
These results provide an abundance ratio of [CH [[][HCOOCH] 3 SC(O)H] [3] []] [>][ 10] [3]

in the emission peaks of methyl formate within Orion KL
(Tercero et al. 2018) and a value >14−20 for the different methyl
formate components of Sgr B2 (Belloche et al. 2013). It is worth
noting that the latter value may be greatly underestimated due to
the high level of line confusion in the IRAM 30m data of Sgr B2,
which leads to a less constrained upper limit for the CH 3 SC(O)H
column density in this region.


**6. Discussion**


The values for the rotational constants _A_, _B_, and _C_ with the
BELGI-C _s_ code are obtained via the RAM. To compare them
directly with the values derived from the previous microwave
study (Caminati et al. 1981) or with the values calculated by ab
initio methods (Senent et al. 2014), we need to transform them
from the RAS to the PAS. This transformation is done with a
rotation by an angle θ RAM between the _z_ axis of both systems, as
described in Sect. 3.1 using Eq. (1) (Kleiner 2010).
Table 4 shows the values of the rotational constants after
transforming back to the PAS and comparing with those determined in the literature. The spectroscopic parameters _A_, _B_, and
_C_ carried out in the present study are more accurate, but they are
slightly different from those determined in the previous experimental microwave investigations (Caminati et al. 1981). They
also differ from the values determined by previous theoretical
calculations (Senent et al. 2014) by 0.5–1%. This could mainly
be explained by the fact that we used a different Hamiltonian
based on a “global approach”, taking into account both ground
state and excited torsional states with a determination of higher
order interaction terms between overall and internal rotations
(shown in Table 2).



In Fig. 3, we show the torsion-rotation interaction diagrams,
which represent the reduced energy levels ( _E_ − _BJ_ ( _J_ + 1)) in
terms of the rotational quantum number _J_ . As shown in Figs. 3a
and b for A- and E-species, respectively, the torsional levels in
ground state with _J_ ⩾ 16 begin to be mixed, though rotationtorsional interactions or resonances, with those of ν 18 = 1 and 2
excited states. Figure 3c presents a zoomed section of Fig. 3a to
highlight the complexity of the interaction scheme for _J_ ⩾ 56.
As shown in Fig. 3d, the interactions often correspond to the
rotation-torsion states’ avoided crossings (with large differences
in the _K_ values between the interacting energy levels), such as
between ν t = 0, for values of _K_ _a_ = 7 and ν 18 = 1 for 2 ⩽ _K_ _a_ ⩽ 4,
and ν 18 = 2, _K_ _a_ ≤ 1.
Our global fit represents a clear improvement on previous work, especially for the ground torsional state and the
first excited state, which are fit with 54 and 120 kHz standard
deviations, respectively. However our analysis only contains a
limited number of rotational transitions within ν 18 = 2, with 164
transitions belonging to the A-species. No E-species could be
assigned without ambiguity for this state. Presumably the rotational excited torsional states of S-methyl thioformate interact
with the levels from other low-frequency vibrational modes, such
as the bending of the CSC bond ν 12 (a [′] ) observed at 245 cm [−][1]
(Jones et al. 1976) and the torsional mode ν 17 of the CO calculated at 253 cm [−][1] (Senent et al. 2014). A natural next step in
the understanding of the rotation-vibrational-torsional spectrum
of S-methyl thioformate will be the recording of the far-infrared
spectrum at high resolution, in order to measure the torsional
fundamental bands at low frequencies. As in the case of methyl
formate, the assignment and fit of the higher excited torsional
states of S-methyl thioformate will also depend on the global
treatment of the various vibrations (Ilyushin et al. 2009). It is
possible that the ν 18 = 2 and ν 18 = 3 analysis will require significant extension of the current model to include suspicious
perturbations from the ν 12 bending mode at 245 cm [−][1], or ν 17
torsion mode at 253 cm [−][1] .


**7. Conclusion**


This work presents a global fit consisting of pure rotational transitions and rotation-torsion transitions using the BELGI-C _s_ code
for an internal rotor. The present fit makes it possible to reproduce, from microwave to submillimeter-wave domains, data up
to 660 GHz with root mean square deviations close to experimental accuracies. Using our spectroscopy work, a deep search


A102, page 7 of 9

A&A 644, A102 (2020)


**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/202038200&pdf_id=0)** **3.** ( _a_, _b_ ) Torsion-rotation diagrams (reduced energy) [ _E_ − _BJ_ ( _J_ + 1)] in the ground state, the ν 18 = 1 and ν 18 = 2 states of torsion for both
A-species ( _left_ _plot_ ) and E-species ( _right_ _plot_ ). ( _c_ ) An enlargement of the torsion-rotation diagram for _J_ values between 56 and 70 in order to
highlight how energy levels become close to each other. ( _d_ ) Examples of perturbations between different torsional states (avoided crossings are
shown around _J_ = 61 and 62, as well as around _J_ = 66).



of S-methyl thioformate was carried out in the IRAM 30 m and
ALMA data of different high-mass star-forming regions (Orion
KL and Sgr B2). We derive an upper limit to the CH 3 SC(O)H
column density in these regions.


_Acknowledgements._ This paper makes use of the following ALMA data:
ADS/JAO.ALMA #2011.0.00009.SV. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC
(Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated
by ESO, AUI/NRAO, and NAOJ. The results are also based on observations
obtained with the IRAM 30 m telescope supported by INSU/CNRS (France),
MPG (Germany), and IGN (Spain). We would like to thank Dr. Carvajal for
kindly providing us values for the partition functions. A.J. and I.K. also thank the
French Groupe de Recherche GDR SPECMO for travel fundings. This work was
supported by the Programme National Physique et Chimie du Milieu Intestellaire (PCMI) of CNRS/INSU with INC/INP co-funded by CEA and CNES.
B.T. and J.C. thank the ERC for support under grant ERC-2013-Syg-610 256NANOCOSMOS and the Spanish MINECO for funding support under grants
AYA2012-32032 and FIS2014-52172-C2, and the CONSOLIDER-Ingenio program “ASTROMOL” CSD 2009-00038. J.-C.G. thanks the Centre National
d’Etudes Spatiales (CNES) for a grant.


**References**


[Anderson, D. E., Bergin, E. A., Maret, S., & Wakelam, V. 2013, ApJ, 779, 141](http://linker.aanda.org/10.1051/0004-6361/202038200/1)
[Ball, J. A., Gottlieb, C. A., Lilley, A., & Radford, H. 1970, ApJ, 162, L203](http://linker.aanda.org/10.1051/0004-6361/202038200/2)
[Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2009, A&A, 499, 215](http://linker.aanda.org/10.1051/0004-6361/202038200/3)
Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito, C. 2013,

[A&A, 559, A47](http://linker.aanda.org/10.1051/0004-6361/202038200/4)
[Bockelée-Morvan, D., Lis, D. C., Wink, J. E., et al. 2000, A&A, 353, 1101](http://linker.aanda.org/10.1051/0004-6361/202038200/5)
[Bottinelli, S., Ceccarelli, C., Williams, J. P., & Lefloch, B. 2007, A&A, 463, 601](http://linker.aanda.org/10.1051/0004-6361/202038200/6)
[Brown, R., Crofts, J., Gardner, F., et al. 1975, ApJ, 197, L29](http://linker.aanda.org/10.1051/0004-6361/202038200/7)
[Caminati, W., van Eijck, B. P., & Lister, D. G. 1981, J. Mol. Spectr., 90, 15](http://linker.aanda.org/10.1051/0004-6361/202038200/8)
[Carvajal, M., Willaert, F., Demaison, J., & Kleiner, I. 2007, J. Mol. Spectr., 246,](http://linker.aanda.org/10.1051/0004-6361/202038200/9)
[158](http://linker.aanda.org/10.1051/0004-6361/202038200/9)
[Carvajal, M., Margulès, L., Tercero, B., et al. 2009, A&A, 500, 1109](http://linker.aanda.org/10.1051/0004-6361/202038200/10)
[Carvajal, M., Favre, C., Kleiner, I., et al. 2019, A&A 627, A65](http://linker.aanda.org/10.1051/0004-6361/202038200/11)
[Cernicharo, J. 2012, EAS Pub. Ser., 58, 251](http://linker.aanda.org/10.1051/0004-6361/202038200/12)
[Cernicharo, J., Guelin, M., Hein, H., & Kahane, C. 1987, A&A, 181, L9](http://linker.aanda.org/10.1051/0004-6361/202038200/13)
[Charnley, S. 1997, ApJ, 481, 396](http://linker.aanda.org/10.1051/0004-6361/202038200/14)
[Churchwell, E., & Winnewisser, G. 1975, A&A, 45, 229](http://linker.aanda.org/10.1051/0004-6361/202038200/15)
[Crockett, N. R., Bergin, E. A., Neill, J. L., et al. 2014, ApJ, 787, 112](http://linker.aanda.org/10.1051/0004-6361/202038200/16)


A102, page 8 of 9



[Demyk, K., Wlodarczak, G., & Carvajal, M. 2008, A&A, 489, 589](http://linker.aanda.org/10.1051/0004-6361/202038200/17)
[Duan, C., Carvajal, M., Yu, S., et al. 2015, A&A, 576, A39](http://linker.aanda.org/10.1051/0004-6361/202038200/18)
Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. 2016, [J.](http://linker.aanda.org/10.1051/0004-6361/202038200/19)
[Mol. Spectr., 327, 95](http://linker.aanda.org/10.1051/0004-6361/202038200/19)
[Esplugues, G. B., Tercero, B., Cernicharo, J., et al. 2013, A&A, 556, A143](http://linker.aanda.org/10.1051/0004-6361/202038200/20)
[Favre, C., Carvajal, M., Field, D., et al. 2014, ApJS, 215, 25](http://linker.aanda.org/10.1051/0004-6361/202038200/21)
[Fourikis, N., Sinclair, M., Robinson, B., Godfrey, P., & Brown, R. 1974, Aust. J.](http://linker.aanda.org/10.1051/0004-6361/202038200/22)
[Phys., 27, 425](http://linker.aanda.org/10.1051/0004-6361/202038200/22)
[Haykal, I., Carvajal, M., Tercero, B., et al. 2014, A&A, 568, A58](http://linker.aanda.org/10.1051/0004-6361/202038200/23)
[Herbst, E., & Van Dishoeck, E. F. 2009, ARA&A, 47, 427](http://linker.aanda.org/10.1051/0004-6361/202038200/24)
Herbst, E., Messer, J., De Lucia, F. C., & Helminger, P. 1984, J. Mol. Spectr.,
[108, 42](http://linker.aanda.org/10.1051/0004-6361/202038200/25)
[Hershfield, R., & Schmir, G. L. 1972, J. Am. Chem. Soc., 94, 1263](http://linker.aanda.org/10.1051/0004-6361/202038200/26)
[Hollis, J., Lovas, F. J., Remijan, A. J., et al. 2006, ApJ, 643, L25](http://linker.aanda.org/10.1051/0004-6361/202038200/27)
[Hougen, J. T., Kleiner, I., & Godefroid, M. 1994, J. Mol. Spectr., 163, 559](http://linker.aanda.org/10.1051/0004-6361/202038200/28)
[Ilyushin, V., Kryvda, A., & Alekseev, E. 2009, J. Mol. Spectr., 255, 32](http://linker.aanda.org/10.1051/0004-6361/202038200/29)
Jones, G. I., Lister, D. G., Owen, N. L., Gerry, M. C., & Palmieri, P. 1976, [J.](http://linker.aanda.org/10.1051/0004-6361/202038200/30)
[Mol. Spectr., 60, 348](http://linker.aanda.org/10.1051/0004-6361/202038200/30)
[Kleiner, I. 2010, J. Mol. Spectr., 260, 1](http://linker.aanda.org/10.1051/0004-6361/202038200/31)
[Kobayashi, K., Takamura, K., Sakai, Y., et al. 2013, ApJS, 205, 9](http://linker.aanda.org/10.1051/0004-6361/202038200/32)
[Kolesniková, L., Tercero, B., Cernicharo, J., et al. 2014, ApJ, 784, L7](http://linker.aanda.org/10.1051/0004-6361/202038200/33)
[Kolesnikova, L., Peña, I., Alonso, J., et al. 2015, A&A, 577, A91](http://linker.aanda.org/10.1051/0004-6361/202038200/34)
[Lin, C. C., & Swalen, J. D. 1959, Rev. Mod. Phys., 31, 841](http://linker.aanda.org/10.1051/0004-6361/202038200/35)
[Linke, R., Frerking, M., & Thaddeus, P. 1979, ApJ, 234, L139](http://linker.aanda.org/10.1051/0004-6361/202038200/36)
[Lovas, F. J. 2004, J. Phys. Chem. Ref. Data, 33, 177](http://linker.aanda.org/10.1051/0004-6361/202038200/37)
[Luo, G., Feng, S., Li, D., et al. 2019, ApJ, 885, 82](http://linker.aanda.org/10.1051/0004-6361/202038200/38)
[Marcelino, N., Gerin, M., Cernicharo, J., et al. 2018, A&A, 620, A80](http://linker.aanda.org/10.1051/0004-6361/202038200/39)
[McGuire, B. A. 2018, ApJS, 239, 17](http://linker.aanda.org/10.1051/0004-6361/202038200/40)
[Mehringer, D. M., Snyder, L. E., Miao, Y., & Lovas, F. J. 1997, ApJ, 480, L71](http://linker.aanda.org/10.1051/0004-6361/202038200/41)
[Pickett, H., Poynter, R., Cohen, E., et al. 1998, J. Quant. Spectr. Rad. Transf., 60,](http://linker.aanda.org/10.1051/0004-6361/202038200/42)
[883](http://linker.aanda.org/10.1051/0004-6361/202038200/42)
Remijan, A., Snyder, L., Friedel, D., Liu, S.-Y., & Shah, R. 2003, ApJ, 590,
[314](http://linker.aanda.org/10.1051/0004-6361/202038200/43)

[Rivilla, V. M., Beltrán, M. T., Martín-Pintado, J., et al. 2017, A&A, 599, A26](http://linker.aanda.org/10.1051/0004-6361/202038200/44)
Senent, M., Puzzarini, C., Hochlaf, M., Domínguez-Gómez, R., & Carvajal, M.
[2014, J. Chem. Phys., 141, 104303](http://linker.aanda.org/10.1051/0004-6361/202038200/45)
[Tercero, B., Margulès, L., Carvajal, M., et al. 2012, A&A, 538, A119](http://linker.aanda.org/10.1051/0004-6361/202038200/46)
[Tercero, B., Kleiner, I., Cernicharo, J., et al. 2013, ApJ, 770, L13](http://linker.aanda.org/10.1051/0004-6361/202038200/47)
[Tercero, B., Cernicharo, J., López, A., et al. 2015, A&A, 582, L1](http://linker.aanda.org/10.1051/0004-6361/202038200/48)
[Tercero, B., Cuadrado, S., López, A., et al. 2018, A&A, 620, L6](http://linker.aanda.org/10.1051/0004-6361/202038200/49)
Wakelam, V., Caselli, P., Ceccarelli, C., Herbst, E., & Castets, A. 2004, [A&A,](http://linker.aanda.org/10.1051/0004-6361/202038200/50)
[422, 159](http://linker.aanda.org/10.1051/0004-6361/202038200/50)
[Xu, L.-H., Lees, R. M., Crabbe, G. T., et al. 2012, J. Chem. Phys., 137, 104313](http://linker.aanda.org/10.1051/0004-6361/202038200/51)
Zakharenko, O., Motiyenko, R. A., Margulès, L., & Huet, T. R. 2015, J. [Mol.](http://linker.aanda.org/10.1051/0004-6361/202038200/52)
[Spectr., 317, 41](http://linker.aanda.org/10.1051/0004-6361/202038200/52)
[Zakharenko, O., Ilyushin, V. V., Lewen, F., et al. 2019, A&A, 629, A73](http://linker.aanda.org/10.1051/0004-6361/202038200/53)

A. Jabri et al.: Rotational spectroscopic study of S-methyl thioformate


**Appendix A: Additional tables**


**Table A.1.** Excerpt of the line list for CH 3 SC(O)H in the microwave and millimeter-wave range.


Upper state Lower state
v _t_ _J_ _K_ _a_ _K_ _c_ v _t_ _J_ _K_ _a_ _K_ _c_ Sym. Obs. Calc. Obs. − Calc. _E_ up _E_ low S*µ [2]

MHz MHz MHz cm [−][1] cm [−][1] Debye [2]


0 2 1 2 0 1 1 1 A 15 804.360(150) 15 804.262 0.098 48.2813 47.7541 0.192588E+01
0 2 1 2 0 1 1 1 E 15 807.960(150) 15 808.067 −0.107 48.7485 48.2212 0.189151E+01
0 2 0 2 0 1 0 1 E 17 003.290(150) 17 003.268 0.022 48.5911 48.0239 0.250867E+01
0 2 0 2 0 1 0 1 A 17 092.040(150) 17 092.095 −0.055 48.1266 47.5565 0.254265E+01
0 16 5 11 0 15 5 10 E 150 541.933( 30) 150 541.964 −0.031 94.3548 89.3333 0.186967E+02
0 16 5 11 0 15 5 10 A 151 336.356( 30) 151 336.343 0.013 94.0586 89.0106 0.187751E+02
1 21 0 21 1 20 0 20 A 151 567.769(100) 151 567.960 −0.191 182.6137 177.5580 0.230444E+02
1 21 1 21 1 20 1 20 A 151 567.769(100) 151 567.483 0.286 182.6137 177.5580 0.230444E+02
1 21 1 21 1 20 1 20 E 152 072.790(100) 152 072.771 0.019 172.0147 166.9421 0.285556E+02
1 21 0 21 1 20 0 20 E 152 072.790(100) 152 072.789 0.001 172.0147 166.9421 0.285556E+02
2 24 1 23 2 23 1 22 A 183 932.733( 50) 183 932.639 0.094 226.8075 220.6722 0.327233E+02
0 21 20 1 0 20 20 0 A 183 952.286( 50) 183 952.242 0.044 203.5658 197.4298 0.250842E+01
0 21 20 2 0 20 20 1 A 183 952.286( 50) 183 952.242 0.044 203.5658 197.4298 0.250842E+01
2 25 0 25 2 24 0 24 A 184 013.640( 50) 184 013.698 −0.058 225.8189 219.6808 0.319334E+02
1 28 0 28 1 27 0 27 A 201 218.098(100) 201 218.032 0.066 224.6298 217.9179 0.369771E+02
1 28 1 28 1 27 1 27 A 201 218.098(100) 201 218.032 0.066 224.6298 217.9179 0.369771E+02
0 23 6 18 0 22 6 17 E 201 240.369( 30) 201 240.379 −0.010 137.3375 130.6249 0.270077E+02
0 23 22 2 0 22 22 1 E 201 325.474( 30) 201 325.440 0.034 235.4292 228.7137 0.250758E+01
0 23 22 1 0 22 22 0 A 201 389.321( 50) 201 389.268 0.053 235.3366 228.6190 0.248480E+01
0 23 22 2 0 22 22 1 A 201 389.321( 50) 201 389.268 0.053 235.3366 228.6190 0.248480E+01
1 28 1 28 1 27 1 27 E 201 487.949(100) 201 487.963 −0.014 214.1165 207.3955 0.663354E+02
1 28 0 28 1 27 0 27 E 201 487.949(100) 201 487.963 −0.014 214.1165 207.3955 0.663354E+02
0 39 2 37 0 38 2 36 E 294 442.233( 50) 294 442.247 −0.014 254.2485 244.4269 0.815427E+02
0 39 3 37 0 38 3 36 E 294 442.233( 50) 294 442.247 −0.014 254.2485 244.4269 0.815427E+02
0 40 2 38 0 39 2 37 A 301 662.222( 50) 301 662.212 0.010 264.0225 253.9602 0.589426E+02
0 40 3 38 0 39 3 37 A 301 662.222( 50) 301 662.212 0.010 264.0225 253.9602 0.589426E+02
1 65 1 65 1 64 1 64 E 461 957.557(100) 461 957.616 −0.059 628.0309 612.6216 0.150728E+03
1 65 0 65 1 64 0 64 E 461 957.557(100) 461 957.616 −0.059 628.0309 612.6216 0.150728E+03
0 75 1 74 0 74 1 73 A 542 497.712( 50) 542 497.777 −0.065 748.5724 730.4766 0.182046E+03
0 75 2 74 0 74 2 73 A 542 497.712( 50) 542 497.777 −0.065 748.5724 730.4766 0.182046E+03
2 75 1 74 2 74 1 73 A 544 005.163( 50) 544 004.966 0.197 849.2223 831.0762 0.174155E+03
0 75 5 70 0 74 5 69 E 568 540.980( 50) 568 540.717 0.263 812.0658 793.1013 0.152061E+03
0 75 6 70 0 74 6 69 E 568 540.980( 50) 568 540.718 0.262 812.0658 793.1013 0.152061E+03
0 74 6 68 0 73 6 67 A 568 684.774(100) 568 684.805 −0.031 808.1602 789.1909 0.156142E+03
0 74 7 68 0 73 7 67 A 568 684.774(100) 568 684.806 −0.032 808.1602 789.1909 0.156142E+03
0 75 5 70 0 74 5 69 A 569 084.432( 50) 569 084.411 0.021 812.2936 793.3110 0.162207E+03
0 75 6 70 0 74 6 69 A 569 084.432( 50) 569 084.411 0.021 812.2936 793.3110 0.162207E+03


**Notes.** The table includes assignments, observed frequencies, calculated frequencies from the _BELGI_ − _C_ _s_ fit, residuals, upper- and lower-state
energy levels, and line strengths S*µ [2] . The complete table is available at the CDS.


**Table** **A.2.** Partition functions of S-methyl thioformate, calculated at
different temperatures.


_T_ (K) _Q_ rot [(] _[a]_ [)] _Q_ tor [(] _[b]_ [)] _Q_ vib [(] _[c]_ [)] _Q_ RTV [(] _[d]_ [)]


80.0 8501.8 2.83 1.03 24 781.9

150.0 21 828.0 3.62 1.27 100 352.0

225.0 40 100.6 4.18 1.85 310 097.9

300.0 61 738.9 4.53 2.86 799 876.8


**Notes.** The partition function is calculated using the method described
in Carvajal et al. (2019). The experimental vibrational energies are taken
from Jones et al. (1976), and the torsional band ν 17 (CO-torsion) is
calculated with CCSD(T) by Senent et al. (2014). The nuclear spin
degeneracy is assumed as 1. [(] _[a]_ [)] Classical rotational partition function,
calculated for the A-species (the same value is expected for the Especies within this approximation) using rotational constants from Jones
et al. (1976). [(] _[b]_ [)] The torsional partition function, calculated using v t =
0, 1, and 2. [(] _[c]_ [)] The vibrational partition function, calculated using all
the fundamental energy levels except the CH 3 torsional mode. [(] _[d]_ [)] The
rotation-torsion-vibration partition function.


A102, page 9 of 9


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].fitting.evidence[0]",
  "value": "61 parameters floated for 5154 transitions",
  "failed_quote": "A global unitless standard deviation of the fit of 1.01 was obtained by floating 61 parameters"
 }
]
```
