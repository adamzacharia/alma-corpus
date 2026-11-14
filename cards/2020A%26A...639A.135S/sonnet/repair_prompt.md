# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...639A.135S\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# **Interstellar glycolamide: A comprehensive rotational study** **and an astronomical search in Sgr B2(N)**

M. Sanz-Novo [1], A. Belloche [2], J. L. Alonso [1], L. Kolesniková [1][, ][3], R. T. Garrod [4], S. Mata [1],


H. S. P. Müller [5], K. M. Menten [2], Y. Gong [2]


1 Grupo de Espectroscopía Molecular (GEM), Edificio Quifima, Área de Química-Física, Lab

oratorios de Espectroscopía y Bioespectroscopía, Parque Científico UVa, Unidad Asociada


[CSIC, E-47011 Valladolid, Spain. jlalonso@qf.uva.es](mailto:jlalonso@qf.uva.es)


2 Max-Planck-Institut für Radioastronomie, Auf dem Hügel 69, 53121 Bonn, Germany


3 Department of Analytical Chemistry, University of Chemistry and Technology, Technická 5,


166 28 Prague 6, Czech Republic


4 Departments of Chemistry and Astronomy, University of Virginia, Charlottesville, VA 22904,


USA


5 I. Physikalisches Institut, Universität zu Köln, Zülpicher Str. 77, 50937 Köln, Germany


June 24, 2020


**ABSTRACT**


_Context._ Glycolamide is a glycine isomer and also one of the simplest derivatives of acetamide


(e.g., one hydrogen atom is replaced with a hydroxyl group), which is a known interstellar


molecule.


_Aims._ In this context, the aim of our work is to provide direct experimental frequencies of   the


ground vibrational state of glycolamide in the centimeter-, millimeter- and submillimeter

wavelength regions in order to enable its identification in the interstellar medium.


_Methods._ We employed a battery of state-of-the-art rotational spectroscopic techniques in the


frequency and time domain to measure the frequencies of glycolamide. We used the spectral line


survey named Exploring Molecular Complexity with ALMA (EMoCA), which was performed


toward the star forming region Sgr B2(N) with ALMA to search for glycolamide in space. We


also searched for glycolamide toward Sgr B2(N) with the Effelsberg radio telescope. The astro

nomical spectra were analyzed under the local thermodynamic equilibrium approximation. We


used the gas-grain chemical kinetics model MAGICKAL to interpret the results of the astronom

ical observations.


, page 1 of 42

_Results._ About 1500 transitions have been newly assigned up to 460 GHz to the most stable


conformer, and a precise set of spectroscopic constants was determined. Spectral features of


glycolamide were then searched for in the prominent hot molecular core Sgr B2(N2). We report


the nondetection of glycolamide toward this source with an abundance at least six and five times


lower than that of acetamide and glycolaldehyde, respectively. Our astrochemical model suggests


that glycolamide may be present in this source at a level just below the upper limit, which was


derived from the EMoCA survey. We could also not detect the molecule in the region’s extended


molecular envelope, which was probed with the Effelsberg telescope. We find an upper limit  to


its column density that is similar to the column densities obtained earlier for acetamide and


glycolaldehyde with the Green Bank Telescope.


**1.** **Introduction**


N-bearing molecules have attracted the attention of much theoretical and experimental research in


the last half-century. Only a few molecules containing the NH 2 group have been confidently


detected in the interstellar medium (ISM). However, chemical models predict the formation of com

plex interstellar amines, such as methoxyamine (CH 3 ONH 2 ) and N-methylhydroxylamine (CH 3 NHOH).


Recently, we have chemically liberated both amines (Kolesniková et al. 2018, 2017) from their


corresponding hydrochloride salts; additionally, precise sets of spectroscopic constants were ob

tained and used to search for spectral features of both molecules in the molecular clouds Orion KL,


Sgr B2, B1-b, and TMC-1.


Moreover, it is interesting to study molecules that contain a peptide bond given that this type of


bond plays an essential role as a building block of proteins, which are fundamental components of


living systems (Belloche et al. 2017). The simplest molecule containing a peptide bond, formamide


(NH 2 CHO), was detected in the interstellar medium (ISM) in the 1970s in Sagittarius B2 (Rubin et


al. 1971) and later in Orion KL (Turner 1989, 1991). One of the simplest derivatives of formamide


that also contains a peptide bond, acetamide (CH 3 C(O)NH 2 ), has already been detected in the ISM


(Hollis et al. 2006; Halfen et al. 2011). Following this, we propose the study of glycolamide, an


amide derivative (CH 2 (OH)C(O)NH 2 ), as a candidate for interstellar detection.


Glycolamide is an interesting compound for various reasons. On the one hand, it was detected


experimentally by Nuevo et al. (2010) when they simulated the relevant conditions to the interstel

lar medium and Solar System icy bodies such as comets. In their experimental setup, a condensed


CH 3 OH : NH 3 = 11 : 1 ice mixture was UV irradiated at about 80 K and urea, glycolic acid, glyc

erol, glycerolic acid, and glycerol amide were also found as products. Also, reactions involving


glycolamide are relevant, since it can participate in polycondensation reactions, leading to the for

, page 2 of 42

mation of N-(2-amino-2-oxoethyl)-2-hydroxyacetamide, a derivative of glycine dipeptide (Szo˝ri et


al. 2011), which was already investigated by high-resolution rotational spectroscopy (Cabezas et


al. 2017).


Of paramount importance is the fact that glycolamide is also an isomer of glycine, the small

est amino acid. Attempts to observe glycine in the ISM have been reported but its detection has


never been confirmed (Snyder et al. 2005; Cunningham et al. 2007; Jones et al. 2007; Hollis et al.


2003). Nevertheless, several amino acids have already been found in some chondritic meteorites


(Pizzarello 2006; Pizzarello et al. 2010; Burton et al 2012). Recently, Altwegg et al. (2016) have


reported the presence of volatile glycine together with the precursor molecules methylamine and


ethylamine in the coma of comet 67P/Churyumov-Gerasimenko. Furthermore, the observation of


not only amino acids but also their most essential isomers as plausible precursors, in the ISM and


in solar system bodies, would be of crucial importance for revealing the chemistry that may have


led to life’s origin (Ehrenfreund et al. 2001). It is known that total dipole-moment values can be


used as a discrimination element for the detection of rotational transitions. An inspection of the


most essential glycine isomers shows that the dipole moment of glycolamide is double that the one


of methylcarbamate and N-methyl carbamic acid, and even a factor four higher than that of glycine


conformer I (Sanz-Novo et al. 2019; Lattelais et al. 2011). Thus, glycolamide should be a good


candidate to search for in the ISM. Among all the isomers studied up to now, methylcarbamate has


been the only one searched for in the hot molecular cloud W51e2, associated with high-mass


protostar, and the intermediate-mass protostar IRAS21391+58502 (Demyk et al. 2004). Groner et


al. (2007) studied the millimeter and submillimeter-wave spectrum of methyl carbamate, provid

ing rotational data in wide frequency ranges. Finally, glycolamide has been characterized by Stark


modulation spectroscopy between 60 and 78.3 GHz (Maris 2004).


In this work, we use a battery of state of the art rotational spectroscopic techniques in the fre

quency and time domain to derive a precise set of spectroscopic constants for glycolamide. The


14 N nuclear quadrupole coupling constants need to be determined together with the rotational con

stants in order to correctly reproduce the spectrum, which is a prerequisite for its identification in


astronomical spectra. This is especially true for observations in low-frequency regions accessible


with the Green Bank Telescope (GBT) or the Effelsberg 100 m telescope, for which the hyperfine


components of transitions with low angular momentum number J are generally spread over sev

eral MHz. Moreover, glycolamide stands as a challenging problem for gas-phase millimeter-wave


rotational studies due to its high melting point (122–126 [◦] CC), which is related to condensation


problems. Therefore, its spectrum so far has remained unexplored in these high-frequency regions.


High-quality data at mm and submm wavelengths are also necessary for the eventual astronomical


detection of glycolamide with observational facilities such as the radio telescopes of the Institut de


RadioAstronomie Millimétrique (IRAM) or the Atacama Large Millimeter-submillimeter Array


(ALMA). This motivated us to record the millimeter and submillimeter-wave spectrum of glyco

page 3 of 42

lamide up to 460 GHz using the heated-cell millimeter-wave spectrometer at the University of


Valladolid.


One of the best astronomical sources to search for complex organic molecules in the interstellar


medium is the giant molecular cloud complex Sagittarius B2 (Sgr B2) that is located in the galactic


center region at a distance of 8.2 kpc (Reid et al. 2019). This star forming region contains the pro

tocluster Sgr B2(N) in which several hot molecular cores are embedded (e.g., Bonfand et al. 2019).


Many complex organic molecules were first detected toward Sgr B2(N) (see, e.g., McGuire 2018,


for a census). Several spectral line surveys were done toward Sgr B2(N) over the past four decades.


We use one of the most recent ones, the imaging spectral line survey EMoCA, which stands for


Exploring Molecular Complexity with ALMA (Belloche et al. 2016), performed with ALMA, to


search for glycolamide and compare its abundance to other related organic molecules. We also


targeted the whole Sgr B2(N) region with the Effelsberg telescope to search for glycolamide in its


extended molecular envelope.


We describe in Sect. 2 the experimental setup that was used to measure the spectrum of gly

colamide. Section 3 presents the results of our analysis of the experimental data. The results of  a


search for glycolamide toward the hot molecular core Sgr B2(N2) are reported in Sect. 4 along


with a comparison to other related molecules. Section 5 reports on our search for glycolamide to

ward Sgr B2(N) with the Effelsberg telescope. The astronomical results are then put into a broader


astrochemical context by comparing them to predictions of numerical simulations in Sect. 6. The


conclusions of this work are given in Sect. 7.


**2.** **Experimental details**


A commercial sample of glycolamide was purchased from Aldrich and used without further purifi

cation (98%). It is a white crystalline substance melting at 122–126 [◦] C. Rotational spectra mea

surements were carried out with three different spectroscopic techniques.


_2.1._ _CP-FTMW spectroscopy_


The supersonic-jet rotational spectrum in the 9.2–17.1 GHz frequency range was investigated using


a broadband CP-FTMW spectrometer (Mata et al. 2012; Kolesniková et al. 2017). A pulsed heated


nozzle was used to expand a gas mixture containing the gaseous glycolamide (heated from the solid


at 130 [◦] CC) seeded in neon (backing pressure of 1 bar). Up to 60,000 individual free induction


decays (four FIDs on each valve cycle) were averaged in the time domain, and Fourier-transformed


using a Kaiser–Bessel window function to obtain the frequency-domain spectrum. The uncertainty


of the frequency measurements was estimated to be smaller than 10 kHz.


_2.2._ _MB-FTMW and DR-MB-FTMW spectroscopy_


In an attempt to fully resolve the [14] N hyperfine structure of glycolamide, we took advantage of the


higher sensitivity and resolution of our molecular beam Fourier transform microwave (MB

page 4 of 42

FTMW) spectrometer, which operates in the frequency range from 4 to 14 GHz and is described


elsewhere (Balle & Flygare 1981; Alonso et al. 1997). Glycolamide was conventionally heated at


130 [◦] C and then seeded in Ne (stagnation pressure 1 bar) and expanded adiabatically to form  a


supersonic jet into a Fabry–Pérot resonator. A microwave radiation pulse sequence that allows


for multiple FID collection was recently implemented (León et al. 2017). The microwave transient


FID was again registered in the time domain and Fourier transformed into the frequency domain.


The pulsed molecular beam was introduced parallel to the axis of the resonator, so each observed


transition appears as a Doppler doublet. The resonance frequency is determined by the arithmetic


mean of the two Doppler components.


In a next step, we configured a double-resonance (DR-MB-FTMW) technique in our laboratory


to extend the coverage of the microwave spectrum of the most stable conformer of glycolamide up


to 40 GHz. In this technique (Mori et al. 2009), millimeter-wave radiation was sent into the Fabry

Pérot cavity of the FTMW spectrometer while monitoring a microwave transition by the FTMW


system, and transitions induced by the millimeter-wave radiation, even with the hyperfine structure


resolved, were observed as a change in the intensity of the monitored transition. This new


configuration is of great importance because it allows us to measure in the same frequency region


covered by astronomical surveys conducted at cm wavelengths with the GBT, and also serves as a


straightforward connection between the microwave and the millimeter-wave data.


_2.3._ _MMW spectroscopy_


Afterwards, the rotational spectrum was measured from 80 to 460 GHz using the millimeter-wave


absorption spectrometer at the University of Valladolid coupled with a new heating cell. A small


amount of solid (0.8 g) was introduced in a single neck round bottom flask connected directly to


the newly built free space cell of the spectrometer (a 140 cm-long Pyrex cell with an inner diameter


of 10 cm and Teflon Windows covered by a heating aluminum blanket) (Alonso et al. 2019). The


flask was evacuated (1 × 10 [−][2 ] mbar) and then was slowly heated using a heating tape controlled by


a thermocouple to a temperature of 70 [◦] C. The optical path length of the spectrometer was doubled


using a rooftop mirror and a polarization grid. The sample was continuously flowed through the cell


(which was heated at 100 [◦] C during the whole experiment), and an optimum gas pressure of about


15 µbar was maintained that allowed us to record the spectra in the millimeter and submillimeter

wave region from 80 to 460 GHz. This spectrometer is based on cascaded multiplication of the


output of an Agilent E8257D microwave synthesizer (up to 20 GHz) by a set of active and passive


multipliers. In this experiment, to cover the recorded spectral range, amplifier-multiplier chains


WR10.0, and WR9.0 (VDI, Inc) in combination with an additional frequency doubler and tripler


(WR2.2, WR4.3, WR2.8, VDI, Inc.) were employed. The output of the synthesizer was frequency


modulated at _f_ = 10.2 kHz with modulation depth between 20 and 40 kHz. After the second pass


through the cell, the signal was detected using solid-state zero-bias detectors and was then sent to a


phase-sensitive lock-in amplifier with 2f demodulation (time constant 30 ms), resulting in a second


page 5 of 42

derivative line shape. A detailed description of the experimental setup has been given elsewhere


(Daly et al. 2014; Alonso et al. 2016). Rotational transitions were measured using an average of


two scans: one recorded in increasing and the other in decreasing frequency, and also employing a


Gaussian profile function with the AABS package (Kisiel et al. 2005). The experimental un

certainty of the isolated symmetric lines is estimated to be around 50 kHz (higher than the usual


30 kHz due to the corresponding temperature broadening).


**3.** **Experimental results and discussion**


_3.1._ _Jet-cooled rotational spectrum_


The CP-FTMW rotational spectrum of glycolamide is shown in Fig. 1a. It appears dominated by


intense water dimer (H 2 O) 2 signals and other lines belonging to known decomposition products


that were identified and discarded from the analysis. At the first stage of the line assignment, pre

dictions based on the spectroscopic constants from Maris (2004) were used. Initial inspection of


the broadband spectrum was directed to search for a set of intense R-branch µ _a_ -type rotational


transitions (with _J_ ’ ← _J_ ” = 2 ← 1) arising from _syn_ -glycolamide predicted with significant µ _a_


electric dipole-moment component. The initial assignment was extended to other intense _b_ -type


transitions. After an iterative procedure of fittings and predictions, a total of six rotational transi

tions were measured. They were least-squares fitted to a rigid rotor Hamiltonian (Pickett 1991).


After excluding these lines from the spectral analysis, another weaker progression of _[a]_ _R_ -branch


transitions was discovered and assigned to _anti_ -glycolamide.


Rotational transitions exhibit the typical hyperfine structure arising from the interaction of the


electric quadrupole moment of the [14] N ( _I_ = 1) nucleus with the electric field gradient created at the


site of the quadrupolar nucleus by the rest of the electronic and nuclear charges of the molecule.


As shown in Fig. 1b, the resolution attained with our broadband CP-FTMW technique was not


sufficient to fully resolve the hyperfine patterns. At this point, we took advantage of the high reso

lution of our narrowband MB-FTMW spectrometer. The analysis began with the measurement of


a total of 5 hyperfine components by interpreting the quadrupole coupling pattern for the 2 02 ←


1 01 rotational transition (see Fig. 1c) and then extended to other _a_ - and _b_ - type _R_ -branch transi

tions. Once the analysis of _syn_ -glycolamide was completed, new _[b]_ _R_ -type transitions belonging to


_anti_ -glycolamide were identified.


Contrary to _syn_ -glycolamide, _anti_ -glycolamide exhibits a weak _b_ -type rotational spectrum and


we were only able to measure _b_ -type lines during the MB-FTMW experiment. After iterative fit

tings and predictions, a set of low- _J_ rotational transitions along with a selection of well-resolved


nuclear hyperfine components from the previous Stark study (Maris 2004) was adequately weighted


and fitted (Pickett 1991) to a semirigid-rotor Hamiltonian in the _A_ -reduction and the _I_ _[r ]_ representa

tion H _R_ [(] _[A]_ [) ] (Watson 1977), supplemented with a term to take into account the quadrupole interaction


_H_ _Q_ (Foley 1947; Robinson & Cornwell 1953), namely _H_ = _H_ _R_ [(] _[A]_ [) ] + _H_ _Q_ . The Hamiltonian was set


up in the coupled basis set _I_ + _J_ = _F_, so the energy levels involved in each transition are labeled


page 6 of 42

**Fig. 1.** (a) Broadband CP-FTMW spectrum of glycolamide from 9.2 to 17.1 GHz. We depict strong _a_ - and _b_ type _R_ -branch transitions of _syn_ -glycolamide (in blue) as well as some transitions of _anti_ -glycolamide (in red).
(b) Zoom-in section of the broadband spectrum showing the rotational transition 2 02 ← 1 01 of both _syn_ glycolamide and _anti_ -glycolamide. (c) The same rotational transition measured in the MB-FTMW experiment,
displaying the high resolution of our spectrometer. The resonance frequency is determined by the arithmetic
mean of two Doppler components. The MB-FTMW spectrum was obtained by averaging 200 experimental
cycles (four free induction decay signals per cycle).


with the quantum numbers _J_, _K_ _a_, _K_ _c_, and _F_ . The final set of rotational constants and nuclear


quadrupole coupling constants are listed in the second column of Table 1. In a quest to extend the


measurements to higher frequencies and allow for an eventual direct comparison with our Effels

berg observations or the GBT line surveys, we used a double-resonance technique with which also


hyperfine components can be resolved. An example of the double resonance spectrum is shown in


Fig. 2, where the _b_ -type transition, 2 12 ← 2 02 is monitored and five hyperfine components of the _a_ 

type transition 3 03 ← 2 02, which is connected to the lower level of the millimeter-wave transition,


page 7 of 42

**Fig. 2.** (a) Double-resonance spectrum of the 3 03 2 02 ← rotational transition of _syn_ -glycolamide showing  five
different hyperfine components. The 2 2 and 3 2 lines were observed monitoring the hyperfine component ← ← _F_
= 2 of the rotational transition 2 12 2 02, while the 2 1 was observed monitoring the hyperfine component ← ← _F_ = 1
component, and both 4 3 and 3 3 were observed monitoring the ← ← _F_ = 3 component of the same rotational
transition; (b) Schematic energy level diagram (in GHz) relative to the 2 02 energy level of _syn_ - glycolamide
from the determined molecular constants. The hyperfine splittings are shown. Arrows indicate an example of
the observed (dashed arrows in garnet) and monitored (dotted arrows in blue) transitions.


have been observed. Subsequently, we performed a fit (Pickett 1991) including our microwave and


double resonance (DR) lines as well as a selection of transitions from Maris (2004). We used the


same Hamiltonian mentioned above. The derived spectroscopic parameters for _syn_ -glycolamide are


listed in the first column of Table 1. Also, in Table A.1 of the Appendix we provide a comparison


between the experimental and **ab initio** predicted quadrupole coupling constants.


**Table 1.** Experimental spectroscopic parameters for _syn_ - and _anti_ - glycolamide.


Parameters _syn (DR)_ _anti_
A ~~_[(a) ]_~~ (MHz) 10454.2640 (15) ~~_[(e)]_~~ 9852.6242 (22)
B (MHz) 4041.15663 (54) 4125.1664 (15)
C (MHz) 2972.07394 (59) 2967.57976 (75)
∆ _J_ (kHz) 0.7723 (59) 0.700 (38)
∆ _K_ (kHz) 2.224 (74) 3.45 (28)
∆ _JK_ (kHz) 6.98 (46) 3.3 (8)
δ _J_ (kHz) 0.2061 (21) 0.27 (2)
δ _K_ (kHz) 2.082 (65)        χ _aa_ _[(b) ]_ (MHz) 2.050 (4) 1.618 (5)
χ _bb_ (MHz) 1.930 (6) 2.020 (10)
χ _cc_ (MHz) -3.981 (6) -3.638 (10)
N _[(c) ]_ 97 46
σ _[(d)]_ (kHz) 21.3 15.6


**Notes.** _[(a) ]_ A, B, and C represent the rotational constants. _[(b) ]_ χ _aa_, χ _bb_, χ _cc_ are the diagonal elements of the [14] N
nuclear quadrupole coupling tensor. _[(c) ]_ N is the number of measured hyperfine components. _[(d) ]_ σ is the root
mean square (rms) deviation of the fit. _[(e) ]_ Standard error in parentheses in units of the last digit.


page 8 of 42

**Fig. 3.** Pairs of _a_ - and _b_ -type transitions of _syn_ -glycolamide with K _a_ = 4,5 at _J_ ”=37 (left panel) that coa- lesce into a
quadruply degenerate line at _J_ ”=41 (right panel) during the mmW experiment while going up in frequency ( _b_ -type
transitions colored in green and _a_ -type transitions in red, respectively). The broadening is higher than that of
conventional room-temperature experiments due to the effect of the temperature of the cell. The _x_ axis is labeled in MHz.


_3.2._ _Millimeter and submillimeter wave spectra_


Afterwards, predictions based on the spectroscopic constants from the high-resolution data of the previous


section were used. Groups of _a_ -type _R_ -branch transitions dominate the millimeter-wave spectrum and can


be easily identified due to their typical ( _B_ + _C_ ) periodicity. These groups are inter- spersed by _b_ -type _R_ -branch


transitions that do not cluster into any characteristic pattern. However, as _J_ increases, the rotational energy


levels with the lowest K _a_ quantum numbers become nearly degenerate, and pairs of _b_ -type with


corresponding _a_ -type transitions involving these energy lev- els form one quadruply degenerate line. For


instance, in Fig. 3 we depict the coalescence for the quartets corresponding to K _a_ = 4 and 5. Taking this


into account, intense _[a]_ _R_ -branch transitions in- volving K _a_ = 0, 1 energy levels were searched for at first.


Subsequently, higher K _a_ R-branch _a_ - and _b_ - type transitions together with several _Q_ -branch transitions were


assigned. However, it is worth noticing that discrepancies up to 60 MHz were found at first between the


experimental _Q_ -branch and also the high _K_ _a_ rotational transitions compared to initial predictions,


emphasizing once more the primary interest of this study.


Finally, 1480 new transition lines were measured (together with the previous MW and DR-MW


measurements correctly weighted) and the ranges of _J_ and K _a_ quantum numbers were extended up to 51


and 33, respectively. The fits and predictions were made in terms of Watson’s _A_ -reduced Hamiltonian in _I_ _[r ]_


-representation with the Pickett’s SPFIT/SPCAT program suite (Pickett 1991). The presently available data


allowed the determination of accurate rotational constants, the full set of quartic and almost all the sextic


centrifugal distortion constants. What is more, despite the broadening due to the temperature effect of the


cell, the RMS deviation of the fit is considerably small (around 50 kHz). The spectroscopic constants are


presented in Table 2, and the measured transitions are reported in Table 4. The final spectroscopic set


decisively improves the previous free-jet Stark modulated experimental data by up to three orders of


magnitude (Maris 2004). In conclusion, the millimeter and submillimeter-wave spectrum of the most stable


conformer of gly

page 9 of 42

**Table 2.** Ground-state spectroscopic parameters of _**syn**_ **-** glycolamide ( _A_ -Reduction, I _[r ]_ -Representation).


Parameters This study Stark experiment ~~_[(a)]_~~
A ~~_[(b) ]_~~ (MHz) 10454.26296 (48) ~~_[(f)]_~~ 10454.260 (6)
B (MHz) 4041.15605 (24) 4041.163 (4)
C (MHz) 2972.07260 (20) 2972.083 (5)
∆ _J_ (kHz) 0.77546 (14) 0.80 (2)
∆ _K_ (kHz) 2.35393 (55) 2.36 (6)
∆ _JK_ (kHz) 6.47368 (90) 6.3 (2)
δ _J_ (kHz) 0.204628 (23) 0.202 (5)
δ _K_ (kHz) 2.0742 (21) 1.8 (2)
Φ _J_ (mHz) -0.492 (36)      Φ _JK_ (Hz) -0.02302 (28)      Φ _K_ (Hz) 0.04078 (77)      φ _JK_ (Hz) -0.01456 (71)      φ _K_ (Hz) -0.1638 (21)      χ _aa_ _[(c) ]_ (MHz) 2.051 (4) 2.3 (2)
χ _bb_ (MHz) 1.930 (6) 2.2 (1)
χ _cc_ (MHz) -3.982 (6) -3.5 (1)
N _[(d) ]_ 1480 121
σ _[(e)]_ (kHz) 50 34


**Notes.** _[(a) ]_ The parameters for the previous Stark experiment were published in Maris (2004). _[(b) ]_ _A_, _B_, and _C_
represent the rotational constants. _[(c) ]_ χ _aa_, χ _bb_, χ _cc_ are the diagonal elements of the [14] N nuclear quadrupole
coupling tensor. _[(d) ]_ _N_ is the number of measured transitions. _[(e) ]_ σ is the root mean square (rms) deviation of the
fit. _[(f) ]_ Standard error in parentheses in units of the last digit.


**Table 3.** Rotational and vibrational partition functions of glycolamide.


Temperature (K) Q _r_ _[(a) ]_ Q _v_ _[(b)]_
2.72 68.8745 1.0000

8.00 342.4694 1.0000

9.38 434.0770 1.0000

18.75 1224.6939 1.0024

37.50 3459.8737 1.0529

75.00 9781.5471 1.3302

100.00 15059.0883 1.6225

150.00 27667.5424 2.5317

225.00 50841.4225 5.2978

300.00 78299.5551 11.5094


**Notes.** _[(a) ]_ Q _r_ is the rotational partition function. It does not take the hyperfine splitting into account. _[(b) ]_ Q _v_ is the
vibrational partition function. The total partition function of the molecule (without hyperfine splitting) is Q _r_
× Q _v_ .


colamide has been studied up to 460 GHz to provide accurate laboratory reference spectra that are


needed to compare directly against the observational data in different regions of the ISM.


We provide the rotational (Q _r_ ) and vibrational (Q _v_ ) partition functions of glycolamide in Ta

ble 3. The values of Q _r_ were calculated from first principles at different temperatures, using the


Picket program Pickett (1991). The maximum value of the _J_ quantum number of the energy levels


taken into account to calculate the partition function is 200. The vibrational part, Q _v_, was estimated


using a harmonic approximation and a simple formula that corresponds to Eq. 3.60 of Gordy &


Cook (1970). The frequencies of the normal modes were obtained from double-hybrid calculations


of the harmonic force field using the B2PLYPD3 method and the aug-cc-pVTZ basis set (see Ta

ble A.2 of the Apendix). The values of Q _v_ were calculated by taking the ten lowest vibrational


modes into account. The full partition function, Q _tot_, is thus the product of Q _r_ and Q _v_ .


page 10 of 42

**Table 4.** Sample list of the measured transition frequencies for the ground-state of glycolamide.


Technique J’ K _a_ ’ K _c_ ’ F’ J” K _a_ ” K _c_ ” F” υ _obs_ ~~_[a]_~~ (MHz) υ _calc_ ~~_[b]_~~ (MHz) υ _obs_ -υ _calc_ ~~_[c]_~~ (MHz)
~~1~~ ~~0~~ ~~1~~ ~~1~~ ~~0~~ ~~0~~ ~~0~~ ~~1~~ ~~7013.7350~~ ~~7013.7398~~ ~~0.0048~~

1 0 1 2 0 0 0 1 7013.1250 7013.1240 0.0009

1 0 1 0 0 0 0 1 7012.2000 7012.2005 0.0005

2 0 2 1 1 0 1 1 13902.4690 13902.4652 0.0038

MB-FTMW 2 0 2 3 1 0 1 2 13903.5250 13903.5242 0.0007

2 0 2 1 1 0 1 0 13904.0050 13904.0038 0.0012

2 0 2 2 1 0 1 1 13903.7090 13903.7073 0.0002

2 0 2 2 1 0 1 2 13904.3250 13904.3228 0.0022

~~3~~ ~~0~~ ~~3~~ ~~2~~ ~~2~~ ~~0~~ ~~2~~ ~~2~~ ~~20557.4200~~ ~~20557.4348~~ ~~-0.0148~~

3 0 3 4 2 0 2 3 20558.6000 20558.5948 0.0052

DR-MB-FTMW 3 0 3 2 2 0 2 1 20558.6900 20558.6769 0.0131

3 0 3 3 2 0 2 2 20558.8291 20558.8291 -0.0091

3 0 3 3 2 0 2 3 20559.6400 20559.6276 0.0123

17 0 17          - 16 1 16          - 103873.6006 103873.5786 0.0220

17 1 17          - 16 1 16          - 103874.6090 103874.6102 -0.0013

17 0 17          - 16 0 16          - 103875.6817 103875.6598 0.0218

17 1 17          - 16 0 16          - 103876.7134 103876.6915 0.0219

38 5 34          - 37 4 33          - 251427.5135 251427.5373 -0.0239

38 4 34          - 37 4 33          - 251426.4797 251426.4907 -0.0109

mmW 38 5 34 - 37 5 33 - 251425.4969 251425.4909 0.0060

38 4 34          - 37 5 33          - 251424.3507 251424.3287 0.0219

48 31 17          - 48 30 18          - 419757.5597 419757.5203 0.0394

48 31 18          - 48 30 19          - 419757.5597 419757.5203 0.0394

49 31 18          - 49 30 19          - 419568.2608 419568.2301 0.0307

49 31 19          - 49 30 20          - 419568.2608 419568.2301 0.0307

32 17 15          - 31 16 16          - 453552.8166 453552.8010 0.0155

32 17 16          - 31 16 15          - 453552.8166 453552.8010 0.0156


**Notes.** Upper and lower state quantum numbers are indicated by ’ and ”, respectively. _[(a) ]_ Observed frequency. _[(b) ]_

Calculated frequency. _[(c) ]_ Observed minus calculated frequency. Table A3 containing the com- plete list of
measured transitions is only available in electronic form at the CDS via anonymous ftp to cdsarc.u-strasbg.fr
(130.79.128.5) or via http://cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/ .


**4.** **Search for glycolamide toward Sgr B2(N2) with ALMA**


_4.1._ _Observations_


We used the spectroscopic predictions derived in Sect. 3 to search for glycolamide toward the hot


molecular core Sgr B2(N2) located in the giant molecular cloud Sgr B2. We used the EMoCA


imaging spectral line survey performed toward the protocluster Sgr B2(N) with ALMA. As men

tioned in Sect. 1, Sgr B2(N) is a high-mass star forming region with a very rich chemistry that is


part of the Sagittarius B2 Giant Molecular Cloud in which many complex organic molecules were


discovered for the first time in the interstellar medium (see, e.g., Menten 2004, and Sect. 5.3). A de

tailed account of the observational setup and data reduction of the EMoCA survey can be found in


Belloche et al. (2016). In short, the survey covers the frequency range from 84.1 GHz to 114.4 GHz


with a spectral resolution of 488 kHz (1.7 to 1.3 km s [−] [1] ) and a median angular resolution of 1.6 [JJ] .


The field was centered at ( α, δ ) J2000 = (17 [h] 47 [m] 19 [s] . 87, − 28 [◦] 22 [J] 16 [J] . [J] 0). Here we analyze the spectrum


at the peak position of Sgr B2(N2) located at ( α, δ ) J2000 = (17 [h] 47 [m] 19 [s] . 86, − 28 [◦] 22 [J] 13 [J] . [J] 4).


As described in Belloche et al. (2016), the spectrum was modeled with the software Weeds


(Maret et al. 2011) under the assumption of local thermodynamical equilibrium (LTE), which is an


appropriate assumption given the high densities characterizing the region where the hot-core


page 11 of 42

emission is detected (> 1 × 10 [7 ] cm [−][3], see Bonfand et al. 2019). A best-fit synthetic spectrum of


each molecule was derived separately, and the contributions of all identified molecules were then


added together. Each species was modeled with a set of five parameters: size of the emitting region,


column density, temperature, linewidth, and velocity offset with respect to the assumed systemic


velocity of the source (74 km s [−][1] ).


_4.2._ _Nondetection of glycolamide_


We did not find a clear evidence for the presence of glycolamide in Sgr B2(N2). Figure 4 shows


in red the synthetic spectrum that we computed to obtain the upper limit on the glycolamide col

umn density. In order to model the emission of glycolamide, we assumed the same parameters as


those derived by Belloche et al. (2017) for acetamide (CH 3 C(O)NH 2 ): an emission size of 0.9 [JJ], a


temperature of 180 K, a linewidth of 5 km s [−] [1], and no velocity o ff set with respect to the systemic


velocity. The red spectrum shown in Fig. 4 was computed with a glycolamide column density of


2.4 × 10 [16 ] cm [−][2 ] (see Table 5).


**Table 5.** Parameters of our best-fit LTE model of acetaldehyde, glycolaldehyde, and acetamide, and column
density upper limit for glycolamide, toward Sgr B2(N2).



Molecule Status _[a ]_ _N_ det _[b ]_ Size _[c ]_ _T_ rot _[d ]_ _N_ _[e ]_ _F_ vib _[f ]_ ∆ _V_ _[g ]_ _V_ off _[h ]_ _N_ _N_ ref _i_
( [JJ] ) (K) (cm [−][2] ) (km s [−][1] ) (km s [−][1] )
Acetaldehyde
CH 3 CHO, r = 0 [Y] d 19 1.1 160 5.3 (17) 1.08 5.6 0.0 1
r t = 1 d 13 1.1 160 5.3 (17) 1.08 5.6 0.0 1
r t = 2 d 2 1.1 160 5.3 (17) 1.08 5.6 0.0 1
13 CH 3 CHO, r = 0 t 2 1.1 160 2.4 (16) 1.01 5.6 0.0 22
r t = 1 n 0 1.1 160 2.4 (16) 1.01 5.6 0.0 22
CH 3 [13] CHO, r = 0 n 0 1.1 160 2.4 (16) 1.01 5.6 0.0 22
r t = 1 n 0 1.1 160 2.4 (16) 1.01 5.6 0.0 22
Glycolaldehyde
CH 2 (OH)CHO, r = 0 [Y] d 21 1.0 170 1.1 (17) 0.92 5.4 1.0 1
r 1 = 1 t 2 1.0 170 1.1 (17) 0.92 5.4 1.0 1
r 2 = 1 t 1 1.0 170 1.1 (17) 0.92 5.4 1.0 1
13 CH 2 (OH)CHO, r = 0 n 0 1.0 170 < 1.6 (16) 1.37 5.4 1.0 - 6.7
CH 2 (OH) [13] CHO, r = 0 n 0 1.0 170 < 2.1 (16) 1.37 5.4 1.0 - 5.4
Acetamide

CH 3 C(O)NH 2, r = 0 [Y] d 10 0.9 180 1.4 (17) 1.23 5.0 1.5 1
r t = 1 d 8 0.9 180 1.4 (17) 1.23 5.0 1.5 1
r t = 2 d 5 0.9 180 1.4 (17) 1.23 5.0 1.5 1
∆ r t Ç 0 t 0 0.9 180 1.4 (17) 1.23 5.0 1.5 1
Glycolamide


CH 2 (OH)C(O)NH 2, r = 0 n 0 0.9 180 < 2.4 (16) 3.38 5.0 0.0 –



_N_



t 0 0.9 180 1.4 (17) 1.23 5.0 1.5 1



**Notes.** The parameters for acetamide were published in Belloche et al. (2017). [(] _[a]_ [) ] d: detection, t: tentative
detection, n: non-detection. [(] _[b]_ [) ] Number of detected lines (conservative estimate, see Sect. 3 of Belloche et al.
2016). One line of a given species may mean a group of transitions of that species that are blended together.
( _c_ ) Source diameter ( _FWHM_ ). ( _d_ ) Rotational temperature. ( _e_ ) Total column density of the molecule. _x_ ( _y_ ) means
_x_ × 10 _[y]_ . An identical value for all listed vibrational and torsional states of a molecule means that LTE is
an adequate description of the vibrational and torsional excitation. [(] _[f]_ [)] Correction factor that was applied to
the column density to account for the contribution of vibrationally excited states, in the cases where this
contribution was not included in the partition function of the spectroscopic predictions. For glycolaldehyde,
see explanation in Sect. 4.3. [(] _[g]_ [)] Linewidth ( _FWHM_ ). [(] _[h]_ [)] Velocity o ff set with respect to the assumed systemic
velocity of Sgr B2(N2), _V_ sys = 74 km s [−] [1] . [(] _[i]_ [)] Column density ratio, with _N_ ref the column density of the previous
reference species marked with a Y .


page 12 of 42

**Fig. 4.** Synthetic LTE spectrum of glycolamide (in red) used to derive the upper limit to its column density,
overlaid on the ALMA spectrum of Sgr B2(N2) (in black) and the synthetic spectrum that contains the contributions of all the species (but not glycolamide) that we have identified so far in this source (in green). The
dotted line in each panel indicates the 3σ noise level. For clarity purposes, the _x_ -axis of each panel is only
labeled with its central frequency followed by the value of the displayed frequency range in parentheses, both
in MHz. The transitions of glycolamide that are weaker than 3σ and the ones which are heavily contaminated
by other species are not shown.


The ALMA spectrum displayed in Fig. 4 shows a ∼5σ line matching one line of the synthetic


∼
spectrum of glycolamide at 109070 MHz, but several issues at other frequencies suggest that this


is likely fortuitous. One major problem is indeed that the glycolamide synthetic spectrum at


∼
103875 MHz, if added to the contribution of all identified species, would significantly overes

timate the signal detected with ALMA at this frequency, which is already accounted for (even


slightly overestimated) by the contributions of ethanol and CH 2 [13] CHCN. The latter species both


have many lines detected in the survey and well reproduced by our best-fit LTE model (see Bel

loche et al. 2016; Müller et al. 2016). There is thus no room left for glycolamide emission at this


frequency.


∼
Another problem occurs at 109817 MHz where the red spectrum overestimates the detected


signal. However, as can be seen in the green spectrum, there are several absorption components


tracing diffuse and translucent clouds along the line of sight that are expected from C [18] O _J_ =1–0


in this frequency range (see, e.g., Thiel et al. 2019), in particular two of them very close to the


glycolamide transition frequency. The strength of these C [18] O absorption components is difficult to


constrain. Therefore, the inconsistency of the glycolamide spectrum at this frequency may not be


significant.


page 13 of 42

All in all, the fact that only one line of glycolamide matches a detected line and the fact that


∼
there is no room left for glycolamide emission at 103875 MHz lead us to conclude that glyco

lamide is not detected in Sgr B2(N2). We thus consider the red spectrum shown in Fig. 4 as an


upper limit to the emission of glycolamide in Sgr B2(N2).


_4.3._ _Comparison to other molecules_


In order to put the column density upper limit derived for glycolamide into a broader astrochemical


context, we use the EMoCA survey to determine the column densities of other species detected


toward Sgr B2(N2) that can be compared to glycolamide. We selected acetaldehyde (CH 3 CHO),


glycolaldehyde (CH 2 (OH)CHO), and acetamide (CH 3 C(O)NH 2 ) because acetamide and glyco

lamide are structurally related in the same way as acetaldehyde and glycolaldehyde: in both cases,


the substitution of an hydrogen atom in the methyl group of the former species with an hydroxyl


group gives the latter species. The column density derived for acetamide in Sgr B2(N2) was already


reported in Belloche et al. (2017).


For both acetaldehyde and glycolaldehyde, we use the spectroscopic predictions (entries 44003


version 3 and 60006 version 2, respectively) available in the Jet Propulsion Laboratory spectro

scopic catalog (Pickett et al. 1998). The acetaldehyde entry is based on Kleiner et al. (1996) with


data in the range of our survey from Kleiner et al. (1991, 1992). The ground state data of gly

colaldehyde are based on Butler et al. (2001), those of the excited data on Widicus Weaver et al.


(2005). Recently, we became aware of an extensive study of the vibrational spectrum of glyco

laldehyde by Johnson et al. (2013). The vibrational energies are higher than those used for the JPL


catalog which were based on relative intensities of vibrational states in the rotational spectrum of


glycolaldehyde. As a result, the vibrational correction factor to the partition function at 170 K is


only 1.38 instead of 1.50. We made the appropriate correction to the column density derived be

low. For the [13] C isotoplogs of acetaldehyde, we use spectroscopic predictions from Margulès et al.


(2015). For the [13] C isotopologs of glycolaldehyde, we use predictions (entries 61513 and 61514,


both version 1) available in the Cologne Database for Molecular Spectroscopy (Endres et al. 2016).


The [13] C entries of glycolaldehyde are based on Haykal et al. (2013). The acetamide entry is based


on Ilyushin et al. (2004).


Many transitions of acetaldehyde and glycolaldehyde in their vibrational ground state are de

tected toward Sgr B2(N2) (see Figs. B.1 and B.8). We also detect transitions from within the first


two torsionally excited states of acetaldehyde (Figs. B.2 and B.3) and transitions from within the


first two vibrationally excited states of glycolaldehyde (Figs. B.9 and B.10). There is an issue with


the transition of CH 3 CHO r t = 2 at ∼90910 MHz, and we suspect that this results from an inacur

rate rest frequency. The frequency computed for this transition by Kleiner et al. (1996) is indeed


somewhat higher than the frequency listed in the JPL catalog: 90910.914 ± 0.204 MHz versus


90910.330 ± 0.101 MHz. The former would better match the EMoCA spectrum.


page 14 of 42

**Table 6.** Rotational temperatures derived from population diagrams toward Sgr B2(N2).


Molecule States _[a ]_ _T_ fit _[b]_

(K)
~~CH~~ 3 ~~CHO~~ ~~r~~ ~~= 0,~~ ~~r~~ t ~~= 1,~~ ~~r~~ t ~~= 2~~ ~~166 (17)~~
CH 2 (OH)CHO r = 0, r 1 = 1, r 2 = 1 163.8 (6.1)


**Notes.** [(] _[a]_ [) ] Vibrational states that were taken into account to fit the population diagram. [(] _[b]_ [) ] The standard deviation of the fit is given in parentheses. As explained in Sect. 3 of Belloche et al. (2016), this uncertainty is
purely statistical and should be viewed with caution. It may be underestimated.


On the basis of a first-guess LTE synthetic spectrum for each molecule, we selected the transi

tions that are not significantly contaminated by other species to measure the size of the emission


of acetaldehyde and glycolaldehyde. The emission is compact around Sgr B2(N2) and we obtained


median sizes (HPBW) of 1.1 [JJ] and 1.0 [JJ], respectively. The transitions that are not much contami

nated were then used to produce population diagrams (Figs. C.1a and C.2a). Following the method


described in Belloche et al. (2016), we corrected the diagrams for optical depth and for the con

tamination due to the other species using our synthetic spectrum that includes the contribution of


all species identified so far (Figs. C.1b and C.2b). A fit to the corrected population diagrams yields


temperatures of 166 ± 17 K and 164 ± 6 K for acetaldehyde and glycolaldehyde, respectively (see


Table 6). As explained in Sect. 3 of Belloche et al. (2016), the uncertainties on the rotational tem

peratures are purely statistical and do not take into account the residual contamination by species


that have not been identified so far. The best-fit spectra shown in Figs. B.1–B.3 and Figs. B.8–


B.10 were computed with temperatures of 160 K and 170 K, respectively, consistent within the


uncertainties with the values derived from the fits to the population diagrams.


On the basis of the parameters obtained for acetaldehyde and glycolaldehyde, we also searched


for emission of their [13] C isotopologs, assuming a [12] C/ [13] C isotopic ratio in the range 20–25 as usu

ally found for complex organic molecules in Sgr B2(N2) (see, e.g., Belloche et al. 2016; Müller et


al. 2016). We tentatively detect [13] CH 3 CHO in its vibrational ground state (Fig. B.4), with an


isotopic ratio of 22. Assuming the same isotopic ratio for both [13] C isotopologs, which is com

monly the case in Sgr B2(N2) for complex organic molecules (COMs) that contain several carbon


atoms (Belloche et al. 2016; Margulès et al. 2016; Müller et al. 2016), yields a synthetic spectrum


of CH 3 [13] CHO that is consistent with the observed spectrum (Fig. B.6). However, no transition is


sufficiently free of contamination from emission of other species to claim a detection of this iso

topolog. Still, we include it in our complete model because its emission contributes significantly to


the signal detected at several frequencies. Transitions from the first torsionally excited state of both


isotopologs contribute to the observed spectra at the ∼3σ level at most (see Figs. B.5 and B.7).


The [13] C isotopologs of glycolaldehyde are not detected. We report upper limits to their column


densities in Table 5. Their non-detection is consistent with the [12] C/ [13] C typical ratio obtained for


other COMs in Sgr B2(N2).


From Table 5 we derive the following column density ratios in Sgr B2(N2): [CH 3 CHO]/[CH 2 (OH)CHO]


= 4.8 and [CH 3 C(O)NH 2 ]/[CH 2 (OH)C(O)NH 2 ] > 5.8. The lower limit on the latter ratio is only


page 15 of 42

slightly higher than the former ratio. We also find that glycolamide ist at least five times less abun

dant than glycolaldehyde ([CH 2 (OH)CHO]/[CH 2 (OH)C(O)NH 2 ] > 4.6).


**5.** **Search for glycolamide toward Sgr B2(N) with Effelsberg**


At low radio frequencies, in the cm-wavelength range, transitions of many molecules including


complex organic species are often seen in absorption against the strong nonthermal (synchrotron)


radiation (Hollis et al. 2007) of the Sgr B2 comples and also the greater Galactic center region,


while others appear in emission depending on the excitation process (e.g., Menten 2004; Hollis et


al. 2004b, 2006, and see Sect. 5.3 below) . In the following we describe our search for several low

_J_ transitions of glycolamide within in the 4–8 and 12–17 GHz frequency ranges.


_5.1._ _Observations_


We performed measurements (project id: 08-20) toward Sgr B2(N) with the S45mm and S20mm


receivers of the 100 m radio telescope at E ff elsberg, Germany [1] on 28 March and 3 April 2020.


The targeted position was α J2000 = 17 [h] 47 [m] 19.8 [s], δ J2000 = − 28 [◦] 22 [J] 17 [JJ] . This is identical to the position


used by Hollis et al. (2006) for their acetamide observations and within a few arc seconds of the


position of Sgr B2(N2) hot core for which the ALMA spectra discussed in Sect. 4 were extracted.


We used the position-switching mode with an o ff -source position located 60 [J] east of Sgr B2(N).


The S45 mm receiver is a broad-band receiver with two orthogonal linear polarizations operating


in the frequency range between 4 and 9.3 GHz. The S20 mm receiver is a dual-beam receiver with


two orthogonal linear polarizations covering the frequency range 12–18 GHz.


The focus was adjusted using observations of 3C286 at the beginning of each observing ses

sion. 3C286 was also used as flux calibrator, and the flux calibration accuracy is estimated to be


within ∼10%. NRAO530 was used as pointing source close to Sgr B2(N). The pointing accuracy


was found to be better than 5 [JJ], small compared to the half-power beam width (HPBW) of 99 [JJ] at


7.2 GHz and 57 [JJ] at 13 GHz. The main beam e ffi ciency is about 69% at 7.2 GHz and 66% at 13 GHz,


and the typical system temperature was about 33 K at 7.2 GHz and 41 K at 13 GHz.


The spectroscopic backends were Fast Fourier Transform spectrometers (FFTSs, e.g., Klein et


al. 2012). The FFTSs cover, in two bands, the frequency ranges 4–8 GHz and 12–17 GHz with  a


channel width of 38.1 kHz, corresponding to a velocity spacing of 1.6 km s [−][1 ] at 7 GHz and


0.9 km s [−][1 ] at 13 GHz. This is adequate, given the expected line widths of ∼10 km s [−][1 ] (see below).


The data reduction was performed using the GILDAS/CLASS software [2] .


_5.2._ _Nondetection of glycolamide_


We used the spectroscopic predictions (with hyperfine structure) derived in Sect. 3 to search for


glycolamide in the Effelsberg spectra of Sgr B2(N). None of the glycolamide transitions covered


page 16 of 42

by our observations were detected either in absorption or in emission. Figures 5 and B.11 illustrate


these non-detections with several portions of the spectra that cover some of the lowest-energy


transitions of glycolamide included in our observations. The spectra of Figs. 5a-b and B.11a-d were


obtained after averaging both polarizations. We then measured the average continuum level in each


panel and removed a fifth-order baseline to produce the spectra shown in Figs. 5c-d and B.11e-h.


We used the software Weeds to produce synthetic spectra assuming a beam-filling factor of 1.


We made the same assumptions as Hollis et al. (2006) made to analyze their detection of acetamide


with the GBT: a systemic velocity of 64 km s [−][1 ] and a rotational temperature of 8 K. We assumed a


linewidth (FWHM) of 10 km s [−][1], which is similar to the linewidth of glycolaldehyde detected with


the GBT (Hollis et al. 2004b). We assumed a background temperature equal to the average con

tinuum level determined in Figs. 5a-b and B.11a-d. With these parameters, we obtained a column


density upper limit of 1.2 × 10 [14 ] cm [−][2 ] for glycolamide at the 4–5σ level for extended emission


from this molecule. This value is similar to the column densities derived by Hollis et al. (2004b,


2006) for acetamide and glycolaldehyde with the GBT.


For completeness, Table A.0 lists all glycolamide transitions with a lower level energy in tem

perature units lower than 10 K covered by the Effelsberg observations. None of these transitions


are detected, and the table indicates the noise level and the average continuum level.


_5.3._ _Discussion of the Effelsberg nondetection_


Our astronomical search for centimeter wavelength transitions from glycolamide was motivated by


the fact that in the early days of molecular radio astronomy, the early 1970s, radiation from many


large molecules was first detected toward Sgr B2 with single dish telescopes (for a sum- mary and


a list of early detections, see Menten 2004). These identifications were made via de- tections of


cm-wavelength of low- _J_ rotational ground-state or near ground state transitions. More recent


observations with the GBT added a significant number of species to this list, namely glyco

laldehyde (CH 2 (OH)CHO), ethylene glycol (HOCH 2 CH 2 OH), propenal (CH 2 CHCHO), propanal


(CH 3 CH 2 CHO) and acetamide (CH 3 C(O)NH 2 ) (Hollis et al. 2002, 2004a,b, 2006).


In many cases, these low- _J_ transitions were exclusively found toward Sgr B2 and its larger


environment, the central molecular zone (CMZ) of our Galaxy (Morris & Serabyn 1996). The CMZ


is a ∼ 200 pc long region stretched around the Galactic center that contains molecular gas that has


much higher temperatures and densities than Giant Molecular Clouds (GMCs) in the Galactic disk


as well as a peculiar chemistry. The latter two facts cause a variety of molecules to be observable


over the whole CMZ, via mm wavelength rotational lines (e.g., Jones et al. 2012; Requena-Torres


et al. 2006), but also in the 834.3 MHz 1 1 − 1 1 _A_ [∓ ] line of CH 3 OH and low-J lines from various


COMs (Gottlieb et al. 1979; Requena-Torres et al. 2008).


The star formation/GMC complex Sagittarius B2 is a prominent part of the CMZ and the men

tioned low- _J_ lines were first (and many of them only) detected toward the extended molecular


page 17 of 42

**Fig. 5. a, b** Examples of spectra obtained with Effelsberg between 4 and 8 GHz toward Sgr B2(N) resulting
from averaging both polarizations. In each panel, the vertical dashed line marks a velocity of 64 km s [−][1] . The
red curve shows the baseline fitted with a 5 [th] -order polynomial function. The boxes at the bottom show the
windows avoided to perform the baseline fit. The average continuum level used to compute the synthetic
spectrum is indicated in the top left corner. **c, d** Synthetic spectra (orange) used to derive the upper limit to
the column density of glycolamide, overlaid on observed spectra after baseline subtraction (black). The rms
noise level is indicated in the top left corner. The horizontal dotted lines show the 4σ and 4 − σ levels. The
components of each hyperfine multiplet are labeled and marked with vertical dotted lines. The velocity axis
shown at the top was computed relative to the strongest component of each hyperfine multiplet.


envelope of this source, which is a prominent source of mm-wavelength emission from very many


molecules (e.g., Jones et al. 2007). Important here is the imaging of the 1065 MHz 1 11 − 1 10 ro

tational transition of acetaldehyde (CH 3 CHO), which shows its emission to be extended over the


whole complex, is, a 3 × 10 pc [2] sized region (Chengalur & Kanekar 2003) that appears to be part of


the several times larger extended envelope of the Sgr B2 complex (Comito et al. 2010; Schmiedeke


et al. 2016). The even (much) more extreme conditions in its embedded dense molecular cores, for


example, Sgr B2(N2), allow the detection of many rare species in these very compact regions that


have sizes of order 1 [JJ] (or ≈ 0 . 04 pc), for instance, with the EMoCA survey (see Table 5). For the


column densities and sizes reported in Table 5, any thermal (LTE) signal in the cm lines for the


listed species would be undetectable because of the lines’ low transition probabilities and the large


beams they are observed with. In fact, the Weeds LTE model of Sgr B2(N2) (Sect. 4) produces


a peak temperature of a few µ _K_ for the 7013 MHz lines of glycolamide when computed at the


resolution of the E ff elsberg telescope.


For various reasons, it is clear that the low frequency, low- _J_, emission or absorption lines ob

served from some molecules in the CMZ are only observable because their observed intensities are


page 18 of 42

the result of a population inversion causing weak maser emission in some lines or _anti_ -inversion


causing enhanced absorption (over-cooling) in others. The weak ( _anti_ -)inversion results in gener

ally small (absolute) optical depths. Nevertheless, the prominent background continuum emission


causes the weak maser emission or absorption to be detectable, since the line signal is proportional


to the optical depth times the (very strong) continuum flux. To give an example: that non-thermal


excitation produces the observed intensities of the formamide and acetamide lines reported by


Hollis et al. (2006) follows directly from the facts that, first, some of them show absorption, while


others show emission. Second the total column densities calculated from the upper level column


densities determined for individual lines vary by a factor of six for the acetamide lines and a factor


of ten for the formamide lines, indicating non-LTE conditions. To calculate these column densities,


Hollis et al. (2006) assume a rotation temperature of 8 K, which suggests a widespread “cold enve

lope” as the origin of these molecules, which is also implied by GBT observations of other COMs


(see references in Hollis et al. 2006). Also Requena-Torres et al. (2006) find mm-wavelength emis

sion from many COMs to be widespread over the CMZ and characterized by a rotation temperature


of 8 K, while the same group of authors (Requena-Torres et al. 2008) derive 8–16 K from the cm


lines of assorted COMs. They invoke subthermal excitation to explain these low numbers, which


are much lower than the gas kinetic temperatures of >60 K found throughout the CMZ by Ginsburg


et al. (2016), who find the extended Sgr B2 cloud to have some of the highest values (>100 K). For


consistency with other studies of cm lines, We have adopted 8 K to calculate our column density


upper limits.


Whether inversion or _anti_ -inversion (over-cooling) of a line can be attained, depends on the


interplay of the molecule’s energy level structure and its radiative and collisional (de)excitation


rates. Since for most species the latter are unknown, it is in general impossible to predict or explain


observed maser (or anti-maser) action. Recently, collisional rate coefficients were calculated for


methyl formate (CH 3 OCHO) and methanimine (CH 2 NH) by Faure et al. (2014) and Faure et al.


(2018), respectively. Using their results, these authors’ excitation calculations indeed confirm non

LTE excitation and reproduce the inversion observed in several low-J lines of these molecules.


While some low-J lines from the above-mentioned COMs and assorted others show extended


non-thermal weak maser emission or enhanced absorption, others do not. Obviously, glycolamide


does not and neither does amino acetonitrile, according to Brown et al. (1977) and Belloche et al.


(2008), who unsuccessfully searched for this molecule’s 1 01 − 0 00 multiplet at 9071.28 MHz (but


did detect its mm-wavelength spectrum in the Sgr B2(N) hot core).


The upper limit we obtained from the cm-wavelength data in Sect. 5.2, 1.2 × 10 [14 ] cm [−][2], is two


orders of magnitude lower than the upper limit we calculated for the glycolamide column density


in the Sgr B2(N2) hot core, 2.4 × 10 [16 ] cm [−][2 ] (Table 5). These two values cannot be compared


directly because the H 2 column densities of the hot core and Sgr B2(N)’s envelope probed with


ALMA and Effelsberg, respectively, are widely different. We note that the value for Sgr B2(N2) is


calculated from a well-constrained measurement, while the value for the envelope depends on


page 19 of 42

the questionable assumption of LTE with a rotation temperature of 8 K. Would we assume a value


of 100 K similar to the kinetic temperature of the envelope (Ginsburg et al. 2016), the upper limit


based on the cm data would increase by a factor of 43 to 5.3 × 10 [15 ] cm [−][2] . The acetamide column


density presented by Hollis et al. (2006) would increase by a similar factor. Assuming 100 K for


the rotation temperature is taking the opposite extreme to 8 K and is also an unrealistic assumption.


The density in the molecular envelope is estimated to be of order a few times 10 [3 ] cm [−][3 ] (Comito et


al. 2010). At such moderate densities, the level population of any molecule with a substantial dipole


moment will not be in LTE. Column density and abundance determinations for this environment


are very difficult to make on the basis of a limited number of observed transitions, and impossible


if their excitation is affected by inversion or _anti_ -inversion.


**6.** **Astrochemical modeling**


In order to interpret the observational findings of Sect. 4, here we present results from the astro

chemical kinetics model _MAGICKAL_ relating to the cold collapse and gradual warm up (8–400 K)


of a hot core with physical conditions appropriate to Sgr B2(N2). Selected model results were


originally published by Garrod et al. (2017), who extended their chemical network to simulate the


production of butyl cyanide and related species. The results presented here for other molecules are


produced by the medium-timescale warm-up model described in detail by those authors. In brief,


the physical model involves a freefall collapse from _n_ H = 3 × 10 [3 ] to 2 × 10 [8 ] cm [−][3 ] over a period of


∼1 Myr. The warm-up stage then proceeds over a period 2.85 × 10 [5 ] yr, reaching a temperature of


200 K after 2 × 10 [5 ] yr. The chemical model includes gas-phase, grain-surface, and ice-mantle


chemistry. In the latter two phases in particular, the addition of functional-group radicals produced


by cosmic ray-induced UV photolysis can result in a range of complex organic molecules, prior to


the thermal desorption of the ice mantles into the gas phase.


Figure 6 shows the simulated time-dependent fractional abundances (with respect to H 2 ) of the


same molecules whose observational parameters are shown in Table 5; both the gas-phase and


grain-surface abundances are indicated for each species. Table 7 shows the peak gas-phase


fractional abundances and the associated gas and dust temperatures obtained from the model for


each of these species and some related molecules. In order to compare with the observational data,


the ratios between the peak fractional abundances of key molecules are considered.


The ratio of glycolamide to glycolaldehyde found in the models (0.21) is consistent with the


upper limit of the observational ratio (0.22). In the models, the main precursor to glycolamide is


indeed glycolaldehyde; the latter is produced on the grains at around 30 K through the addition of


the HCO and CH 2 OH radicals, which are methanol photo-products. The abstraction of a hydrogen


atom from the aldehyde end of the glycolaldehyde molecule, by various species including the


radicals NH 2 and OH, produces a radical that may combine with NH 2 in the ice, or with NH


followed by atomic hydrogen, resulting in glycolamide.


page 20 of 42

**Table 7.** Peak fractional abundances for selected molecules with respect to H 2 obtained from the chemical
kinetics model. The associated temperature at which the peak value is achieved is also indicated.


~~Molecule~~ ~~n(i) / n(H~~ 2 ~~)~~ ~~T~~
(K)

CH 3 OH 2.1(-5) 130
CH 3 CHO 3.3(-7) 58
CH 2 (OH)CHO 7.4(-7) 148
CH 3 C(O)NH 2 3.4(-8) 138
CH 2 (OH)C(O)NH 2 1.5(-7) 226

NH 2 CHO 4.8(-7) 158

CH 3 OCHO 7.8(-8) 125


**Notes.** x (y) means _x_ × 10 _[y]_ .


In the models, the main precursor to acetamide is its smaller homologue, formamide. Similarly


to the grain-surface mechanism described above for glycolamide, hydrogen abstraction from the


aldehyde end of formamide results in a radical that, with the addition of the methyl radical (CH 3 ),


produces acetamide. The model ratio of acetamide to formamide (0.071) is comparable to the


observational ratio (0.054), based on data from Table 5 and from Belloche et al. (2019, their Table


6).


While the ratios between each molecule and its precursor appear to agree fairly well with the


observational values for glycolamide and acetamide, the direct ratio between these two species


themselves does not; the models suggest a ratio of glycolamide to acetamide of 4.4, compared with


∼
an observational upper limit of 0.17, discrepant by a factor 26. The modeled ratios of the pre

∼
cursors of these molecules show similar behavior, being too large by a factor 33. This suggests


that, while the chemistry of glycolamide and acetamide are well treated within the model, the rela

tive abundances of their precursors require attention. It may be noted that the model abundance of


methyl formate (CH 3 OCHO), also shown in Table 7, is around one order of magnitude lower than


that of glycolaldehyde. This also defies the observational expectation for Sgr B2(N2) and various


other star-forming regions that typically show the inverse relationship; Belloche et al. (2016) found


a column density of methyl formate of 1.2 × 10 [18 ] cm [−][2], ten times larger than the glycolaldehyde


abundance shown in Table 5. The inversion of this ratio in the models was noted by Garrod (2013),


and could be related to the choice of dissociation branching ratios of methanol, or to the branching


ratios of the radical-addition reaction (HCO + CH 2 OH) leading to glycolaldehyde on the grains.


Whatever the cause, a reduction in the overall production of glycolaldehyde (and, by consequence,


of glycolamide) in the models of around 30 times would appear to make the model ratios consistent


with the observations for each of the molecules discussed here. Even with this adjustment, the mod

eled ratio of glycolamide to glycolaldehyde remains unchanged, suggesting that the observational


upper limit obtained for glycolamide may be close to the true column density.


**7.** **Conclusions**


∼
The rotational spectrum of glycolamide has been recorded up to 460 GHz. Precise ground state


spectroscopic constants up to sextic centrifugal distortion constants are provided for the most stable

page 21 of 42

**Fig. 6.** Chemical model results for the molecules whose observational data are shown in Table 5; methanol is
included for reference. Solid lines indicate gas-phase abundances with respect to H 2 . Dashed lines of the same
color indicate the solid-phase abundance of the same species, also with respect to gas-phase H 2 . Data shown
correspond to the warm-up period following free-fall collapse.


conformer obtained from the fit of more than 1480 transition lines. In this work, using the heated

cell millimeter-wave spectrometer at the University of Valladolid, we were able not only to transfer


this organic molecule from the solid state to the gas phase but to avoid condensation problems in


the walls of the free-space cell. We used this precise set of spectroscopic parameters to search for


glycolamide toward the hot core Sgr B2(N2) and the envelope of Sgr B2(N). The main conclusions


of this astronomical search are the following:


1. We report a non-detection of glycolamide toward Sgr B2(N2) with ALMA with a column den

sity upper limit of 2.4 × 10 [16 ] cm [−][2] . This implies that glycolamide is at least six and five times


less abundant than acetamide and glycolaldehyde, respectively, in this source. The former lower


limit is only slightly higher than the column density ratio of acetaldehyde to glycolaldehyde,


suggesting that the actual column density of glycolamide in Sgr B2(N2) may not be far from


the derived upper limit.


2. We also report a non-detection of glycolamide toward Sgr B2(N) with the Effelsberg 100 me

ter radio telescope. We derive an upper limit to its beam-averaged column density of 1.2 × 10 [14 ]


cm [−][2 ] that is similar to the column densities of glycolaldehyde and acetamide reported earlier


toward the same source with the Green Bank Telescope.


3. Our astrochemical models suggest that glycolamide is a product of atomic-H abstraction from


glycolaldehyde, followed by radical addition. Relative fractional abundances are close to the


page 22 of 42

observed upper limit for glycolamide in Sgr B2(N2), suggesting that a slightly more sensitive


search in this source could indeed yield a detection.


_Acknowledgements._ This research was supported by the Ministerio de Ciencia e Innovación (CTQ2013- 40717-P and
CTQ2016-76393-P), Junta de Castilla y León (Grants VA175U13 and VA077U16), and the European Research Council under the European Union’s Seventh Framework Programme (FP/2007–2013)/ERC-2013-SyG, Grant Agreement no. 610256
NANOCOSMOS, is gratefully acknowledged. M.S.N. acknowledges funding from the Spanish “Ministerio de Ciencia,
Innovación y Universidades” under predoctoral FPU Grant (FPU17/02987). L.K. thanks The Czech Science Foundation
(GACR) for financial support (grant 19-25116Y). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00017.S,
ADS/JAO.ALMA#2012.1.00012.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS
(Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the
Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The interferometric data are
available in the ALMA archive at https://almascience.eso.org/aq/. Part of this work has been carried out within the
Collaborative Research Centre 956, sub-project B3, funded by the Deutsche Forschungsgemeinschaft (DFG) – project ID
184018867. We would like to thank Dr. A. Kraus, the station manager of the MPIfR Effelsberg observatory, for scheduling
our observations with the 100 meter telescope on very short notice.


**References**


Alonso, J.L., Lorenzo, F. J., López, J. C., et al. 1997, Chemical Physics, 218, 267.


Alonso, E. R., Kolesniková, L., Tercero, B., et al. 2016, ApJ, 832, 42.


Alonso, E. R., McGuire, B. A., Kolesniková, L., et al. 2019, ApJ, 883, 18.


Altwegg, K., Balsiger, H., Bar-Nun, A., et al. 2016, Science Advances, 2, e1600285.


Balle, T. J., & Flygare, W. H. 1981, Review of Scientific Instruments, 52, 33.


Belloche, A., Menten, K. M., Comito, C., et al. 2008, A&A, 482, 179.


Belloche, A., Müller, H. S. P., Garrod, R. T., & Menten, K. M. 2016, A&A, 587, A91.


Belloche, A., Meshcheryakov, A. A., Garrod, R. T., et al. 2017, A&A, 601, A49 and references therein.


Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2019, A&A, 628, A10.


Brown, R. D., Godfrey, P. D., Ottrey, A. L., et al. 1977, Journal of Molecular Spectroscopy, 68, 359.


Bonfand, M., Belloche, A., Garrod, R. T., et al. 2019, A&A, 628, A27.


Burton, A. S., Stern, J. C., Elsila, J. E. et al. 2012, Chem. Soc. Rev., 41, 5459-5472.


Butler R. A. H., De Lucia F. C., Petkie D. T., Møllendal H., Horn A., Herbst E., 2001, ApJS, 134, 319.


Cabezas, C., Varela, M., Alonso, J. L. 2017, Angew. Chem. Int. Ed, 56, 6420.


Chengalur, J. N., & Kanekar, N. 2003, A&A, 403, L43.


Comito, C., Schilke, P., Rolffs, R., et al. 2010, A&A, 521, L38.


Cunningham, M. R., Jones, P. A., Godfrey, P. D., et al. 2007, MNRAS, 376, 1201.


Daly, A., Kolesniková, L. Mata, S., J. Alonso, J. L. 2014, Journal of Molecular Spectroscopy, 306, 11.


Ehrenfreund, P., Bernstein, M. P., Dworkin, J. P., et al. 2001, ApJ, 550, L95.


Endres, C. P., Schlemmer, S., Schilke, P., et al. 2016, J. Mol. Spectrosc., 327, 95.


Faure, A., Remijan, A. J., Szalewicz, K., et al. 2014, ApJ, 783, 72.


Faure, A., Lique, F., & Remijan, A. J. 2018, The Journal of Physical Chemistry Letters, 9, 3199


Foley, H. M. 1947, Physical Review, 71, 747.


Garrod, R. T. 2013, ApJ, 765, 60.


Garrod, R. T., Belloche, A., Müller, H. S. P., et al. 2017, A&A, 601, A48.


Gordy, W., Cook, R. L. Microwave Molecular spectra, Interscience Pub, 1970, New York, Chap. III, 58-70.


Gottlieb, C. A., Ball, J. A., Gottlieb, E. W., et al. 1979, ApJ, 227, 422.


Groner, P., Winnewisser, M., Medvedev, I. R., et al. 2007, ApJS, 169, 28.


Demyk, K., Wlodarczak, G., & Dartois, E. 2004, SF2A-2004: Semaine De L’astrophysique Francaise, 493.


Ginsburg, A., Henkel, C., Ao, Y., et al. 2016, A&A, 586, A50.


Halfen, D. T., Ilyushin, V., Ziurys, L. L., 2011, ApJ, 743, 60.


Haykal, I., Motiyenko, R. A., Margulès, L., et al. 2013, A&A, 549, A96.


Hollis, J. M., Lovas, F. J., Jewell, P. R., et al. 2002, ApJ, 571, L59.


Hollis, J. M., Pedelty, J. A., Snyder, L. E., et al. 2003, ApJ, 588, 353.


page 23 of 42

Hollis, J. M., Jewell, P. R., Lovas, F. J., et al. 2004a, ApJ, 610, L21


Hollis, J. M., Jewell, P. R., Lovas, F. J., et al. 2004b, ApJ, 613, L45


Hollis, J. M., Lovas, F. J., Remijan, A. J., et al. 2006, ApJ, 643, L25.


Hollis, J. M., Jewell, P. R., Remijan, A. J., et al. 2007, ApJ, 660, L125.


Ilyushin, V. V., Alekseev, E. A., Dyubko, S. F., et al. 2004, Journal of Molecular Spectroscopy, 227, 115.


Johnson, T. J., Sams, R. L., Profeta, L. T. M., et al. 2013, J. Phys. Chem. A, 117, 4096.


Jones, P. A., Cunningham, M. R., Godfrey, P. D., et al. 2007, MNRAS, 374, 579.


Jones, P. A., Burton, M. G., Cunningham, M. R., et al. 2008, MNRAS, 386, 117.


Jones, P. A., Burton, M. G., Cunningham, M. R., et al. 2012, MNRAS, 419, 2961.


Kisiel, Z., Pszczółkowski, L., Medvedev, I. R., et al. 2005, Journal of Molecular Spectroscopy, 233, 231.


Klein, B., Hochgürtel, S., Krämer, I., et al. 2012, A&A, 542, L3.


Kleiner, I., Hougen, J. T., Suenram, R. D., et al. 1991, Journal of Molecular Spectroscopy, 148, 38.


Kleiner, I., Hougen, J. T., Suenram, R. D., et al. 1992, Journal of Molecular Spectroscopy, 153, 578.


Kleiner, I., Lovas, F. J., & Godefroid, M. 1996, Journal of Physical and Chemical Reference Data, 25, 1113.


Kolesniková, L., Alonso, E. R., Mata, S., et al. 2017, ApJS, 233, 24.


Kolesniková, L., Alonso, E. R., Mata, S., J. Alonso, J. L. 2017, Journal of Molecular Spectroscopy, 335, 54.


Kolesniková, L., Tercero, B., Alonso, E. R., Guillemin, J. C., Cernicharo, J. Alonso, J. L. 2018, A&A, 609, A24.


Lattelais, M., Pauzat, F., Pilmé, J., et al. 2011, A&A, 532, A39.


León, I., Alonso, E. R., Mata, S., et al. 2017, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions),


19, 24985.


Maris, A. 2004, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 6, 2611.


Maret, S., Hily-Blant, P., Pety, J., Bardeau, S., & Reynier, E. 2011, A&A, 526, A47.


Mata, S., Pena, I., Cabezas, C., J. Alonso, J. L. 2012, Journal of Molecular Spectroscopy, 280, 91.


McGuire, B. A. 2018, ApJS, 239, 17.


Menten, K. M. 2004, The Dense Interstellar Medium in Galaxies, 69.


Mori, T., Suma, K. Sumiyoshi, Y. Endo, J. 2009, Journal of Chemical Physics, 130, 204308 and references therein.


Margulès, L., Motiyenko, R. A., Ilyushin, V. V., et al. 2015, A&A, 579, A46.


Margulès, L., Belloche, A., Müller, H. S. P., et al. 2016, A&A, 590, A93.


Morris, M., & Serabyn, E. 1996, ARA&A, 34, 645


Motiyenko, R. A., Tercero, B., Cernicharo, J., et al. 2012, A&A, 548, A71 and references therein.


Müller, H. S. P., Belloche, A., Xu, L.-H., et al. 2016, A&A, 587, A92.


Nuevo, M., Bredehöft, U. J., Meierhenrich, U. J., D’Hendecourt, L., et al. 2011, Astrobiology, 10, 245.


Pickett, H. M., Poynter, R. L., Cohen, E. A., Delitsky, M. L., Pearson, J. C., & Müller, H. S. P. 1998,


J. Quant. Spectr. Rad. Transf., 60, 883


Pizzarello, S. 2006, Acc. Chem. Res, 39, 321.


Pizzarello, S., Shock, E. 2010, Cold Spinrg Harb. Perspect. Biol., 2, 1-20.


Requena-Torres, M. A., Martín-Pintado, J., Rodríguez-Franco, A., et al. 2006, A&A, 455, 971.


Requena-Torres, M. A., Martín-Pintado, J., Martín, S., et al. 2008, ApJ, 672, 352.


Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2019, ApJ, 885, 131.


Robinson, G. W., & Cornwell, C. D. 1953, J. Chem. Phys., 21, 1436.


Rubin, R., Swenson, G., Benson, R., Tigelaar, H., Flygare, W. 1971, ApJ, 169, L39.


Sanz-Novo, M., Largo, A., Redondo, P., et al. 2019, ACS Earth and Space Chemistry, 3, 1170.


Snyder, L. E., Lovas, F. J., Hollis, J. M., et al. 2005, ApJ, 619, 914.


Schmiedeke, A., Schilke, P., Möller, T., et al. 2016, A&A, 588, A143.


Szo˝ri, M., Jójárt, B., Izsák, R., et al. 2011, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 13,


7449.


Thiel, V., Belloche, A., Menten, K. M., et al. 2019, A&A, 623, A68.


Turner, B. E. 1989, ApJS, 70, 539.


Turner, B. E. 1991, ApJS, 76, 617.


Pickett, H. M. 1991, Journal of Molecular Spectroscopy, 148, 371.


Watson, J. K. G. 1977, Journal of Molecular Spectroscopy, 66, 500.


Widicus Weaver, S. L., Butler, R. A. H., Drouin, B. J., et al. 2005, ApJS, 158, 188.


page 24 of 42

**Appendix A: Complementary tables**


Table A.1 shows a comparison between experimental and theoretical spectroscopic constants for


glycolamide and Table A.2 lists the theoretical frequencies of the lowest vibrational modes. Ta- ble


A.0 lists the noise levels and continuum levels measured around all glycolamide transitions with a


lower level energy in temperature units below 10 K covered by the Effelsberg observations between


4 and 8 GHz and between 12 and 17 GHz.


**Table A.1.** Experimental (exp) and theoretical (theory) spectroscopic parameters for _syn_ - and _anti_ - glycolamide.


Parameters _syn_ (exp) _anti_ (exp) _syn_ (theory) _anti_ (theory)
A ~~_[(a) ]_~~ (MHz) 10454.2591 (20) ~~_[(f)]_~~ 9852.6098 (20) 10448.9 9932.8
B (MHz) 4041.14440 (88) 4125.1538 (12) 4077.1 4149.0
C (MHz) 2972.08215 (78) 2967.57875 (70) 2987.5 2981.2
∆ _J_ (kHz) 0.678 (74)   -   -   ∆ _JK_ (kHz) 9.87 (90)   -   -   χ _aa_ _[(b) ]_ (MHz) 2.050 (4) 1.615 (5) 2.1 1.6
χ _bb_ (MHz) 1.926 (6) 2.005 (10) 1.9 2.0
χ _cc_ (MHz) -3.976 (6) -3.621 (10) -4.0 -3.6
N _[(c) ]_ 55 21   -   σ _[(d)]_ (kHz) 10.8 6.9   -   ∆E _[(e) ]_ (cm [−][1] )   -   - 0 218


**Notes.** Theoretical calculations at MP2/aug-cc-pVTZ level of theory. _[(a) ]_ A, B, and C represent the rotational
constants. _[(b) ]_ χ _aa_, χ _bb_, χ _cc_ are the diagonal elements of the [14] N nuclear quadrupole coupling tensor. _[(c) ]_ N is the
number of measured **hyperfine components** . _[(d) ]_ σ is the root mean square (rms) deviation of the fit. _[(e) ]_ ∆E is
the electronic energy relative to the global minimum, taking into account the zero-point vibrational energy
(ZPE) calculated at the same level. _[(f) ]_ Standard error in parentheses in units of the last digit.


**Table A.2.** Theoretical frequencies of the lowest vibrational modes.


Vibrational mode Frequency ~~_[(a)]_~~
1 78.4

2 183.6

3 293.0

4 444.5

5 447.7

6 500.9

7 634.3

8 645.3

9 827.5

10 1042.7


**Notes.** _[(a) ]_ Frequencies (in cm [−][1] ) calculated at the B2PLYPD3/aug-cc-pVTZ level of theory. They are necessary
to estimate the vibrational contribution to the partition function in order to get a proper estimate of the total
column density (upper limit) of the molecule.


page 25 of 42

**Appendix B: Complementary figures: Spectra**


Figures B.1–B.10 show the transitions of CH 3 CHO, CH 2 (OH)CHO, and some of their isotopologs


or vibrationally excited states that are covered by the EMoCA survey and contribute significantly


to the signal detected toward Sgr B2(N2). Figure B.11 shows examples of spectra obtained with Ef

felsberg toward Sgr B2(N) between 12 and 17 GHz. It illustrates the non-detection of glycolamide


at these low frequencies.


page 26 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.1.** Transitions of CH 3 CHO, r = 0 covered by our ALMA survey. The best-fit LTE synthetic spectrum of
CH 3 CHO, r = 0 is displayed in red and overlaid on the observed spectrum of Sgr B2(N2) shown in black. The
green synthetic spectrum contains the contributions of all molecules identified in our survey so far, including
the species shown in red. The central frequency and width are indicated in MHz below each panel. The y-axis
is labeled in brightness temperature units (K). The dotted line indicates the 3σ noise level.


page 27 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.1.** continued.


page 28 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.2.** Same as Fig. B.1, but for CH 3 CHO, r t = 1.


page 29 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.3.** Same as Fig. B.1, but for CH 3 CHO, r t = 2.


page 30 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.4.** Same as Fig. B.1, but for [13] CH 3 CHO, r = 0.


**Fig. B.5.** Same as Fig. B.1, but for [13] CH 3 CHO, r t = 1.


page 31 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.6.** Same as Fig. B.1, but for CH 3 [13] CHO, r = 0.


**Fig. B.7.** Same as Fig. B.1, but for CH 3 [13] CHO, r t = 1.


page 32 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.8.** Same as Fig. B.1, but for CH 2 (OH)CHO, r = 0.


page 33 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.8.** continued.


page 34 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.8.** continued.


page 35 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.9.** Same as Fig. B.1 for CH 2 (OH)CHO, r 1 = 1.


page 36 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.9.** continued.


page 37 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.10.** Same as Fig. B.1, but for CH 2 (OH)CHO, r 2 = 1.


page 38 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Fig. B.11.** Same as Fig. 5, but for spectra obtained with Effelsberg between 12 and 17 GHz.


page 39 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Appendix C: Complementary figures: Population diagrams**


Figures C.1 and C.2 show the population diagrams of CH 3 CHO and CH 2 (OH)CHO toward Sgr B2(N2).


**Fig. C.1.** Population diagram of CH 3 CHO toward Sgr B2(N2). The observed datapoints are shown in various
colors (but not red) as indicated in the upper right corner of panel a while the synthetic populations are shown
in red. No correction is applied in panel a. In panel b, the optical depth correction has been applied to both the
observed and synthetic populations and the contamination by all other species included in the full model has
been removed from the observed datapoints. The purple line is a linear fit to the observed populations (in
linear-logarithmic space).


**Fig. C.2.** Same as Fig. C.1, but for CH 2 (OH)CHO.


page 40 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Table A.0.** Spectral noise levels and continuum levels for glycolamide transitions with _E_ low < 10 K observed


with Effelsberg toward Sgr B2(N).


Frequency Transition _E_ l / _k_ _[a ]_ _A_ ul _[b ]_ _g_ u _[c ]_ rms _[d ]_ _T_ cont _[e]_


(MHz) _J_ [u] _K_ a [u ] _K_ c [u ] _F_ [u ] _J_ [l ] _K_ a [l ] _K_ c [l ] _F_ [l ] (K) ( 10 [−] [8 ] s [−] [1] ) (mK) (K)


4538.854 7 1 7 8 – 6 2 4 7 8.694 0.012 17 13.4 55.7


5043.746 6 1 6 5 – 5 2 3 4 6.548 0.024 11 13.2 51.0


5044.140 6 1 6 7 – 5 2 3 6 6.548 0.024 15


5046.409 6 1 6 6 – 5 2 3 5 6.548 0.024 13


5108.735 3 3 1 4 – 4 2 2 5 4.779 0.026 9 11.3 50.8


5550.175 6 2 5 5 – 5 3 2 4 8.092 0.062 11 6.0 46.5


5550.320 6 2 5 7 – 5 3 2 6 8.092 0.064 15


5551.151 6 2 5 6 – 5 3 2 5 8.092 0.062 13


6404.012 3 1 2 3 – 3 1 3 3 2.196 0.220 7 8.8 44.2


6405.972 3 1 2 4 – 3 1 3 4 2.195 0.246 9


6406.658 3 1 2 2 – 3 1 3 2 2.195 0.233 5


6861.504 3 3 0 3 – 4 2 3 4 4.695 0.060 7 8.3 38.3


6862.721 3 3 0 4 – 4 2 3 5 4.695 0.060 9


6863.118 3 3 0 2 – 4 2 3 3 4.695 0.064 5


7001.013 6 2 4 6 – 6 2 5 6 8.358 0.315 13 7.4 36.0


7002.061 6 2 4 7 – 6 2 5 7 8.358 0.324 15


7002.238 6 2 4 5 – 6 2 5 5 8.358 0.321 11


7012.199 1 0 1 0 – 0 0 0 1 0.000 1.370 1 6.8 36.3


7013.121 1 0 1 2 – 0 0 0 1 0.000 1.371 5


7013.736 1 0 1 1 – 0 0 0 1 0.000 1.371 3


7480.660 1 1 0 1 – 1 0 1 1 0.337 0.548 3 9.8 37.9


7481.275 1 1 0 1 – 1 0 1 2 0.337 0.914 3


7481.853 1 1 0 2 – 1 0 1 1 0.337 0.548 5


7482.198 1 1 0 1 – 1 0 1 0 0.337 0.731 3


7482.468 1 1 0 2 – 1 0 1 2 0.337 1.646 5


7483.643 1 1 0 0 – 1 0 1 1 0.337 2.195 1


7489.391 2 0 2 1 – 1 1 1 1 0.644 0.227 3 9.6 37.6


7490.412 2 0 2 3 – 1 1 1 2 0.644 0.545 7


7490.632 2 0 2 2 – 1 1 1 1 0.644 0.409 5


7490.836 2 0 2 1 – 1 1 1 0 0.644 0.303 3


7491.210 2 0 2 2 – 1 1 1 2 0.644 0.136 5


12199.244 4 1 3 4 – 3 2 2 3 3.353 1.102 9 20.4 24.5


12199.244 4 1 3 4 – 3 2 2 4 3.353 0.074 9


page 41 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Table A.0.** continued.


Frequency Transition _E_ l / _k_ _[a ]_ _A_ ul _[b ]_ _g_ u _[c ]_ rms _[d ]_ _T_ cont _[e]_


12199.522 4 1 3 5 – 3 2 2 4 3.353 1.175 11


12199.593 4 1 3 3 – 3 2 2 3 3.353 0.094 7


12199.593 4 1 3 3 – 3 2 2 2 3.353 1.079 7


12786.796 4 4 1 4 – 5 3 2 5 8.092 0.252 9 8.1 23.6


12787.652 4 4 1 5 – 5 3 2 6 8.092 0.254 11


12787.880 4 4 1 3 – 5 3 2 4 8.092 0.263 7


12795.512 6 2 4 6 – 5 3 3 5 8.080 0.940 13 9.8 23.3


12795.816 6 2 4 7 – 5 3 3 6 8.080 0.967 15


12795.865 6 2 4 5 – 5 3 3 4 8.080 0.935 11


12955.894 2 1 2 1 – 1 1 1 1 0.644 3.241 3 10.9 22.3


12956.471 2 1 2 1 – 1 1 1 2 0.644 0.216 3


12957.182 2 1 2 3 – 1 1 1 2 0.644 7.779 7


12957.338 2 1 2 1 – 1 1 1 0 0.644 4.321 3


12957.882 2 1 2 2 – 1 1 1 1 0.644 5.834 5


12958.460 2 1 2 2 – 1 1 1 2 0.644 1.945 5


13030.677 4 4 0 4 – 5 3 3 5 8.080 0.266 9 12.2 23.3


13031.620 4 4 0 5 – 5 3 3 6 8.080 0.268 11


13031.866 4 4 0 3 – 5 3 3 4 8.080 0.278 7


13425.365 1 1 1 0 – 0 0 0 1 0.000 8.450 1 10.7 21.7


13426.232 1 1 1 2 – 0 0 0 1 0.000 8.453 5


13426.810 1 1 1 1 – 0 0 0 1 0.000 8.452 3


13681.452 4 1 3 4 – 4 0 4 4 3.282 8.173 9 8.3 20.0


13681.730 4 1 3 5 – 4 0 4 4 3.282 0.363 11


13681.801 4 1 3 3 – 4 0 4 4 3.282 0.566 7


13682.749 4 1 3 4 – 4 0 4 5 3.282 0.443 9


13683.027 4 1 3 5 – 4 0 4 5 3.282 8.697 11


13683.083 4 1 3 4 – 4 0 4 3 3.282 0.440 9


13683.432 4 1 3 3 – 4 0 4 3 3.282 8.493 7


13902.465 2 0 2 1 – 1 0 1 1 0.337 5.315 3 10.1 19.0


13903.080 2 0 2 1 – 1 0 1 2 0.337 0.354 3


13903.523 2 0 2 3 – 1 0 1 2 0.337 12.760 7


13903.706 2 0 2 2 – 1 0 1 1 0.337 9.569 5


13904.002 2 0 2 1 – 1 0 1 0 0.337 7.088 3


13904.321 2 0 2 2 – 1 0 1 2 0.337 3.190 5


15090.186 3 0 3 2 – 2 1 2 2 1.266 1.107 5 30.5 18.5


page 42 of 42

Sanz-Novo et al.: Interstellar glycolamide: A comprehensive rotational study and an astronomical search in

Sgr B2(N)


**Table A.0.** continued.


Frequency Transition _E_ l / _k_ _[a ]_ _A_ ul _[b ]_ _g_ u _[c ]_ rms _[d ]_ _T_ cont _[e]_


15091.579 3 0 3 3 – 2 1 2 2 1.266 6.322 7


15091.825 3 0 3 4 – 2 1 2 3 1.266 7.112 9


15092.174 3 0 3 2 – 2 1 2 1 1.266 5.974 5


15092.857 3 0 3 3 – 2 1 2 3 1.266 0.790 7


15093.987 2 1 1 1 – 1 1 0 0 0.696 6.834 3 30.5 18.5


15094.813 2 1 1 2 – 1 1 0 2 0.696 3.075 5


15095.432 2 1 1 3 – 1 1 0 2 0.696 12.301 7


15095.777 2 1 1 1 – 1 1 0 2 0.696 0.342 3


15096.006 2 1 1 2 – 1 1 0 1 0.696 9.225 5


15096.969 2 1 1 1 – 1 1 0 1 0.696 5.126 3


15791.081 5 1 4 5 – 5 1 5 5 4.961 1.550 11 12.6 14.9


15793.038 5 1 4 6 – 5 1 5 6 4.961 1.614 13


15793.436 5 1 4 4 – 5 1 5 4 4.961 1.593 9


**Notes.** [(] _[a]_ [) ] Energy of lower level in temperature units. [(] _[b]_ [) ] Einstein coefficient for spontaneous emission. [(] _[c]_ [) ] De

generacy of upper energy level. [(] _[d]_ [) ] Noise level measured in baseline-removed spectrum at 38.1 kHz resolution.


( _e_ ) Average continuum level measured around the transition or hyperfine multiplet.


page 43 of 42


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "size 0.9\", T 180 K, linewidth 5 km/s, Voff 0",
  "failed_quote": "an emission size of 0.9 , a temperature of 180 K, a linewidth of 5 km s −1, and no velocity o ff set with respect to the systemic velocity."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Envelope limit depends on questionable LTE assumption at 8 K",
  "failed_quote": "the value for the envelope depends on the questionable assumption of LTE with a rotation temperature of 8 K"
 }
]
```
