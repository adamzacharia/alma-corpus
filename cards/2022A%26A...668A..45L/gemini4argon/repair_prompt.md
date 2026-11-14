# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2022A%26A...668A..45L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. PUMA_CO_outflow_paper_arxiv ©ESO 2023
March 21, 2023

## **Physics of ULIRGs with MUSE and ALMA: The PUMA project** **IV. No tight relation between cold molecular outflow rates and AGN** **luminosities**


I. Lamperti [1,][⋆] M. Pereira-Santaella [1], M. Perna [1][,][ 2], L. Colina [1], S. Arribas [1], S. García-Burillo [3], E. González-Alfonso [4], S.
Aalto [5], A. Alonso-Herrero [6], F. Combes [7], A. Labiano [8], J. Piqueras-López [1], D. Rigopoulou [9], and P. van der Werf [10]


1 Centro de Astrobiología (CAB), CSIC-INTA, Ctra. de Ajalvir Km. 4, 28850 Torrejón de Ardoz, Madrid, Spain
2 INAF - Osservatorio Astrofisico di Arcetri, Largo Enrico Fermi 5, I-50125 Firenze, Italy
3 Observatorio Astronómico Nacional (OAN-IGN)-Observatorio de Madrid, Alfonso XII, 3, 28014, Madrid, Spain
4 Universidad de Alcalá, Departamento de Física y Matemáticas, Campus Universitario, 28871 Alcalá de Henares, Madrid, Spain
5 Department of Space, Earth and Environment, Division of Astronomy and Plasma Physics, SE-412 96 Gothenburg, Sweden
6 Centro de Astrobiología (CAB), CSIC-INTA, Camino Bajo del Castillo s/n, 28692, Villanueva de la Cañada, Madrid, Spain
7 LERMA, Obs. de Paris, PSL Univ., Collége de France, CNRS, Sorbonne Univ., Paris, France
8 Telespazio UK for ESA, ESAC, E-28692 Villanueva de la Cañada, Madrid, Spain
9 Department of Physics, University of Oxford, Keble Road, Oxford OX1 3RH, UK
10 Leiden Observatory, Leiden University, PO Box 9513, 2300, RA Leiden, The Netherlands


March 21, 2023


**ABSTRACT**


We study molecular outflows in a sample of 25 nearby ( _z_ < 0.17, _d_ < 750 Mpc) ultra-luminous infrared galaxy (ULIRG) systems (38
individual nuclei) as part of the Physics of ULIRGs with MUSE and ALMA (PUMA) survey, using ∼ 400 pc (0.1-1.0" beam FWHM)
resolution ALMA CO(2-1) observations. We used a spectro-astrometry analysis to identify high-velocity (> 300 km s [−][1] ) molecular gas
disconnected from the galaxy rotation, which we attribute to outflows. In 77% of the 26 nuclei with log _L_ _IR_ / _L_ ⊙    - 11.8, we identified
molecular outflows with an average _v_ _out_ = 490 km s [−][1], outflow masses 1 − 35 × 10 [7] M ⊙, mass outflow rates _M_ [˙] _out_ = 6 − 300 M ⊙ yr [−][1],
mass-loading factors η = _M_ [˙] _out_ / _S FR_ = 0.1−1, and an average outflow mass escape fraction of 45±6%. The majority of these outflows
(18/20) are spatially resolved with radii of 0.2 − 0.9 kpc and have short dynamical times ( _t_ _dyn_ = _R_ _out_ / _v_ _out_ ) in the range 0.5 − 2.8 Myr.
The outflow detection rate is higher in nuclei dominated by starbursts (SBs, 14/15 = 93%) than in active galactic nuclei (AGN,
6/11 = 55%). Outflows perpendicular to the kinematic major axis are mainly found in interacting SBs. We also find that our sample
does not follow the _M_ [˙] _out_ versus AGN luminosity relation reported in previous works. In our analysis, we include a sample of nearby
main-sequence galaxies (SFR = 0.3 − 17 M ⊙ yr [−][1] ) with detected molecular outflows from the PHANGS-ALMA survey to increase
the _L_ _IR_ dynamic range. Using these two samples, we find a correlation between the outflow velocity and the star-formation rate (SFR),
as traced by _L_ _IR_ ( _v_ _out_ ∝ _S FR_ [0][.][25][±][0][.][01] ), which is consistent with what was found for the atomic ionised and neutral phases. Using this
correlation, and the relation between _M_ _out_ / _R_ _out_ and _v_ _out_, we conclude that these outflows are likely momentum-driven. Finally, we
compare the CO outflow velocities with the ones derived from the OH 119µm doublet. In 76% of the targets, the outflow is detected
in both CO and OH, while in three targets (18%) the outflow is only detected in CO, and in one target the outflow is detected in OH
but not in CO. The difference between the OH and CO outflow velocities could be due to the far-IR background source required by
the OH absorption which makes these observations more dependent on the specific outflow geometry.


**Key words.** galaxies: evolution – galaxies: nuclei – galaxies: active – galaxies: starburst



**1.** **Introduction**


Local ultraluminous infrared galaxies (ULIRGs) are extreme objects with infrared (IR, 8-1000 µm) luminosities _L_ _IR_ - 10 [12] _L_ ⊙ .
ULIRGs are mostly gas-rich major mergers (Lonsdale et al.
2006) and represent an important stage in galaxy evolution. The
nuclei of ULIRGs host intense starbursts, and active galactic nuclei (AGN) can also account for a significant fraction of their
IR luminosity (Farrah et al. 2003; Nardini et al. 2010). Nuclear
outflows powered by starbursts and AGN are thought to play a
significant role in the evolution of galaxies. They can influence
star-formation by injecting energy into the interstellar medium
(ISM), heating or expelling gas from the galaxy (e.g. Fabian
2012; Veilleux et al. 2020). In ULIRGs, outflows have been de

⋆ E-mail: isabellalamperti@gmail.com



tected in different gas phases: atomic neutral (e.g. Rupke et al.
2005a; Cazzoli et al. 2016), atomic ionised (e.g. Westmoquette
et al. 2012; Bellocchi et al. 2013; Arribas et al. 2014), hot molecular (e.g. Dasyra & Combes 2011; Dasyra et al. 2014; Emonts
et al. 2017), and cold molecular (e.g. Fischer et al. 2010; Feruglio et al. 2010; Sturm et al. 2011; Cicone et al. 2014; Sakamoto
et al. 2014; García-Burillo et al. 2015; Aalto et al. 2015; Feruglio
et al. 2015; Pereira-Santaella et al. 2018; Fluetsch et al. 2019;
Lutz et al. 2020).


In this work, we focus on the cold molecular phase, which is
thought to account for most of the mass outflow rate (e.g. Rupke
& Veilleux 2013; Carniani et al. 2015; Ramos Almeida et al.
2019; Fluetsch et al. 2021). The most common tracers of the cold
molecular phase are the low-J transitions of CO (Feruglio et al.
2010; Chung et al. 2011; Cicone et al. 2014; Pereira-Santaella


Article number, page 1 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



et al. 2018; Lutz et al. 2020), HCN (Aalto et al. 2012, 2015;
Walter et al. 2017; Barcos-Muñoz et al. 2018), and FIR OH lines
(e.g. Fischer et al. 2010; Sturm et al. 2011; Spoon et al. 2013;
Veilleux et al. 2013; González-Alfonso et al. 2017).
To accurately measure the outflow properties, such as the
mass outflow rate, outflow energy and momentum rate, it is
necessary to know the distribution of the outflowing gas. Spatially resolved studies of molecular outflows in ULIRGs have
only been performed on a few sources (e.g. García-Burillo et al.
2015; Saito et al. 2018; Barcos-Muñoz et al. 2018; PereiraSantaella et al. 2018). In most cases, the targeted objects were
selected based on the presence of an outflow, which was detected through previous low-resolution observations. This could
introduce a bias in the samples, in which only ULIRGs with the
most-extreme outflows are selected.
In this work, we present high spatial resolution (0.1-1.0",
∼ 400 pc) ALMA observations of the CO(2-1) line for an unbiased sample of 25 ULIRGs, selected only based on their IR
luminosity. This paper is part of the Physics of ULIRGs with
MUSE and ALMA (PUMA) project. The main goals of PUMA
are the following: (i) to study the prevalence of outflows in different gas phases (ionised, neutral, and molecular) as a function
of the galaxy properties, (ii) to determine the driving mechanisms of the outflows (e.g. distinguish between starburst- and
AGN-powered outflows), and (iii) to characterise the effects
of outflow feedback on the host galaxies. The PUMA survey
combines VLT/MUSE optical integrated field spectroscopy and
ALMA CO(2-1) and continuum observations to study the multiphase (ionised, neutral, and molecular) properties of outflows in
ULIRGs. Perna et al. (2021) have presented the first results on
the spatial distribution of the ionised gas and the resolved stellar
kinematics derived from the MUSE data. A detailed analysis of
the MUSE data for Arp 220 has been presented in Perna et al.
(2020). Perna et al. (2022) studied the properties and incidence
of the ionised gas disks in the PUMA ULIRGs, the associated
velocity dispersion and its relation with the offset from the main
sequence. Pereira-Santaella et al. (2021) analysed the ALMA
220 GHz continuum and provided evidence for the ubiquitous
presence of deeply obscured AGN in ULIRGs, which could substantially contribute to their IR emission.
This paper is organised as follows. In Section 2, we describe
the sample selection criteria and the general properties of the
PUMA targets. Section 3 describes the ALMA observations and
the data reduction. In Section 4, we present the CO(2-1) moment maps (Sec. 4.1), the spectro-astrometry analysis (Sec. 4.2),
and the method used to derive the properties of the molecular outflows (Sec. 4.4- 4.6), as well as the analysis of the OH
119 µm spectra (Sec. 4.7). The outflow properties, detection
rate, energetics, and launching mechanisms are discussed in Section 5.1-5.3. In Section 5.4, we compare the outflow properties
derived from the CO(2-1) data with the ones derived from the
OH 119 µm doublet. The discussion is presented in Section 6. In
Section 7, we summarise the main results and our conclusions.
Throughout this work, we assume a cosmological model with
Ω λ = 0.7, Ω M = 0.3, and _H_ 0 = 70 km s [−][1] Mpc [−][1] .


**2.** **Sample**


The PUMA sample consists of 25 nearby ( _z_ < 0.165, _d_ <
750 Mpc) ULIRG systems (38 individual nuclei) with IR luminosities (8−1000 µm) in the range log _L_ _IR_ / _L_ ⊙ = 11.9−12.7. The
individual nuclei have luminosities from log _L_ _IR_ / _L_ ⊙ < 10.5 to
log _L_ _IR_ / _L_ ⊙ = 12.7, based on the relative contribution of the nuclei to the total ALMA continuum fluxes (see Pereira-Santaella


Article number, page 2 of 76



13.0


12.5


12.0


11.5


11.0


10.5





10.0

0.00 0.02 0.04 0.06 0.08 0.10 0.12 0.14 0.16 0.18

redshift



Fig. 1: Infrared luminosity (8-1000 µm) and redshift of the individual nuclei in the PUMA sample. AGN are shown in orange, while starburst (SB) dominated nuclei are in lightblue. Circles indicate interacting systems and squares indicate advanced
mergers. The nuclei with log _L_ _IR_ / _L_ ⊙ < 12 are the fainter nuclei
in interacting systems, where the IR luminosity is dominated by
the other nucleus.


et al. 2021). The sample has been selected to cover a range of interacting phases: 12 systems are classified as advanced mergers
(with distance between the nuclei _d_ _nuclei_ < 1 kpc) and 13 systems are classifies as interacting (with _d_ _nuclei_ = 1.8 − 8.3 kpc).
The nuclei of the ULIRGs can be classified as AGN-dominated
or starburst- (SB-) dominated based on the AGN contribution
in the MIR (α _AGN_, see Perna et al. 2021): eight ULIRG systems are dominated by AGN (α _AGN_ ≥ 0.5) and 17 by a SB
(α _AGN_ < 0.5). Based on the optical classification, our sample
includes the following: nine Seyfert galaxies (two Seyfert 1 and
seven Seyfert 2), eight HII and eight low ionisation nuclear emission regions (LINERs, Perna et al. 2021). In this paper we
adopt a combined classification, in which we consider as AGN
all nuclei classified as AGN either based on the MIR criterion
(α _AGN_ ≥ 0.5) or based on the optical classification (Seyfert 1 or
Seyfert 2). According to this combined classification, 11/25 systems (14/38 individual nuclei) are classified as AGN, while the
others are classified as SBs.
An overview of the sample properties is shown in Table 1.
Figure 1 shows the IR luminosities and redshift of the sample.


**3.** **Observations and data reduction**


In this work, we analyse ALMA 12-m array CO(2-1)
230.538 GHz observations of the 25 ULIRGs systems in the
PUMA sample. Most of these observations were carried out
as part of our programmes 2015.1.00263.S, 2016.1.00170.S,
2018.1.00486.S, and 2018.1.00699.S (PI: M. Pereira-Santaella).
Additionally, we use archival data for 13120-5453 and
15327+2340 (Arp 220), from programmes 2016.1.00777.S (PI:
K. Sliwa) and 2015.1.00113.S (PI: N. Scoville), respectively.
The observations were taken between 2015 and 2021. We note
that the analysis of the CO(2-1) observations of three of the
PUMA ULIRGs (12112+0305, 14348-1447, and 22491-1808)
has already been presented in Pereira-Santaella et al. (2018), but
are included in this paper for completeness.
Depending on the redshift of the targets, the CO(2-1) transition falls in Band 5 or Band 6. The synthesised beam full

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs


Table 1: Properties of the sample.


IRAS name other name nucleus RA Dec log _L_ _IR_ morph. _d_ _nuclei_ opt. class. α _AGN_ AGN/SB CON

[deg] [deg] [log _L_ ⊙ ] [kpc]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12)

00091-0738 S 2.930301 -7.368707 12.33 I 2.3 HII 0.46 SB Y

N 2.930424 -7.368383 < 10.82
00188-0856  - 5.360472 -8.657220 12.42 M < 0.3 Sy 2 0.50 AGN N
00509+1225 I Zw 1 - 13.395560 12.693316 11.87 M < 0.2 Sy 1 0.92 AGN N
01572+0009 Mrk 1014 - 29.959380 0.394688 12.65 M < 0.4 Sy 1 0.65 AGN N
05189-2524  - 80.255834 -25.362582 12.20 M < 0.1 Sy 2 0.72 AGN N
07251-0248 E 111.906721 -2.915070 12.41 I 1.8 HII 0.30 SB Y

W 111.906385 -2.915106 11.40

09022-3615  - 136.052940 -36.450537 12.33 M < 0.1 HII 0.54 AGN N

10190+1322 E 155.428143 13.115447 11.98 I 7.2 HII 0.17 SB N

W 155.427056 13.114952 11.12

11095-0238 NE 168.014095 -2.906371 12.16 I 1.1 LINER 0.44 SB Y

SW 168.013994 -2.906468 11.84
12071-0444 N 182.438000 -5.020377 12.41 I 2.3 Sy 2 0.75 AGN N
S 182.437998 -5.020812 < 11.66

12112+0305 NE 183.441903 2.811542 12.28 I 4.2 LINER 0.17 SB N

SW 183.441417 2.810866 11.27
13120-5453 WKK 2031  - 198.776347 -55.156339 12.27 M < 0.1 Sy 2 0.33 AGN N
13451+1232 4C+12.50 W 206.889004 12.290064 12.31 I 4.3 Sy 2 0.82 AGN N
E 206.889583 12.289944 < 10.31
14348-1447 SW 219.409503 -15.006729 12.21 I 5.5 LINER 0.17 AGN [⋆] Y
NE 219.409988 -15.005908 11.98 SB [⋆]
14378-3651  - 220.245888 -37.075537 12.15 M < 0.1 Sy 2 0.21 AGN N
15327+2340 [⋆⋆] Arp220 E 233.738722 23.503135 11.65 M 0.4 LINER 0.06 SB Y
W 233.738431 23.503177 12.04

16090-0139  - 242.918411 -1.785098 12.62 M < 0.7 HII 0.41 SB Y
16156+0146 NW 244.539016 1.656043 12.14 I 8.3 Sy 2 0.70 AGN Y
SE 244.539754 1.655458 < 11.54

17208-0014  - 260.841481 -0.283582 12.43 M < 0.1 LINER 0.00 SB Y

19297-0406 N 293.092955 -4.000286 12.45 I 1.1 HII 0.23 SB Y

S 293.092904 -4.000500 < 10.45

19542+1110 - 299.149103 11.318064 12.09 M < 0.1 LINER 0.26 SB N

20087-0308  - 302.849441 -2.997422 12.47 M < 0.9 LINER 0.20 SB N

20100-4156 SE 303.373149 -41.793113 12.65 I 6.5 LINER 0.26 SB Y

NW 303.372813 -41.792383 < 10.96

20414-1651  - 311.075663 -16.671340 12.24 M < 0.2 HII 0.00 SB N

22491-1808 E 342.955620 -17.873368 12.22 I 2.7 HII 0.15 SB Y

W 342.955158 -17.873239 < 10.53


**Notes.** (1) IRAS name. (2) Alternative name. (3) Name of the nucleus. (4) and (5) Coordinates of the nuclei derived from the ALMA 1.4 mm
continuum. If the continuum is not detected, the coordinates are measured from the NIR or optical HST (see Perna et al. 2021). (6) Infrared
luminosity of the nuclei. For the interacting systems, the proportion of IR luminosity in each nucleus is based on their relative ALMA continuum
fluxes (see Pereira-Santaella et al. (2021)). (7) Morphology of the system. I: interacting system with nuclear separation - 1 kpc; M: advanced
merger with nuclear separation < 1 kpc. (8) Nuclear separation. (9) Nuclear activity classification based on optical spectroscopy (see Perna et al.
2021). (10) Fraction of AGN contribution to _L_ _bol_ derived from the 30µm to 15µm flux ratio (see Perna et al. 2021). (11) Combined nuclear activity
classification used in this paper. Nuclei are classified as AGN either if α _AGN_ ≥ 0.5 or if their optical classification is Seyfert (Sy 1 or Sy 2).
(12) Objects classified as compact obscured nuclei (CONs) using ratios of the equivalent widths of different polycyclic aromatic hydrocarbons
(PAHs) based on the method by García-Bernete et al. (2022). [⋆] : For 14348-1447, there is evidence that the AGN is located in the SW nucleus
based on high-angular resolution mid-IR imaging (Alonso-Herrero et al. 2016). [⋆⋆] : Even though this target (Arp 220) is classified as a merger
( _d_ _nuclei_ = 0.37 kpc), we report the position of the two nuclei that have been identified thanks to the low redshift of this source. For consistency, we
treat this target as a single nucleus in the rest of the paper.



width at half-maximum (FWHM) has been selected for each
target so that it corresponds to a similar physical spatial resolution for all targets (∼ 400 − 500 pc). As a result, the synthesised beam FWHM are in the range 0.13 − 1.05". The maximum
recoverable scales are ∼ 10 times the beam FWHM. Table 2
presents the details of the observations: the beam FWHM, line
sensitivity and total CO(2-1) fluxes. The data-reduction is de


scribed in detail in the PUMA II paper (Pereira-Santaella et al.
2021). We note that two targets (12071-0444 and 13451+1232)
are not presented in that work because the ALMA observations
were not available at the time of publication, but they are included in this work. The ALMA observations of 12071-0444
have been reduced following the same procedure used for the
other sources. The second target, 13451+1232 (4C+12.50), is a


Article number, page 3 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



radio AGN with a strong 230 GHz continuum dominated by synchrotron radiation (Pereira-Santaella et al. 2021). Given that for
this source the continuum is strong enough, we decide to apply
self-calibration to these data in order to increase the signal-tonoise. We apply five rounds of phase self-calibration and one
round of amplitude self-calibration. Due to the steep slope of its
continuum, we use a first-order polynomial to subtract the continuum from the CO(2-1) spectral window in the _uv_ plane. For
the rest of the data-reduction, we follow the same procedure as
presented in Pereira-Santaella et al. (2021).


**4.** **Analysis**


_4.1._ _CO(2-1) moment maps_


We produced the maps of the CO(2-1) intensity (moment 0), velocity (moment 1), and velocity dispersion (moment 2) for our
sample. Before producing the moment maps, we masked pixels with low signal-to-noise ratio (S/N) in each velocity channel,
where the noise was estimated using the median absolute deviation (MAD). Specifically, for each velocity channel, we masked
spaxels with S/N < 3.5 − 5 depending on the overall S/N of the
observations.
Moreover, we masked individual spaxels which show spurious emission applying the following procedure. For each spectral channel, we applied a Gaussian kernel with a size of three
pixels to smooth the channel image and then we masked individual pixels with S/N < 0.4 in the smoothed image. In this way, for
each velocity channel, we remove isolated pixels with spurious
emission, which could bias the calculation of the moment maps.
The moment 0, moment 1, and moment 2 maps were produced
using the cubes obtained with this masking process, while the
CO(2-1) peak map was obtained from the original data cubes.
We define the zero velocity (and consequently the redshift) based
on the moment 1 velocity at the position of the continuum peak.
The CO(2-1) redshifts (reported in Table 2) are in good agreement with previously reported redshifts. Throughout this paper,
we use the radio velocity definition.
Figure 2 shows the CO(2-1) moment 0, 1, and 2 maps, along
with the CO(2-1) peak map and continuum map for four targets as an example. The maps of the full sample are shown
in the Appendix (Fig. D.1). The CO(2-1) emission is detected
with S/N - 3 in all individual nuclei but 16156+0146 SE. In
the majority of the nuclei (32/37), the kinematic major axis is
clearly visible in the moment 1 maps. The moment 1 maps of
five nuclei show a less ordered motion (01572+0009, 051892524, 12112+0305 NE, 14348-1447 SW, 22491-1808 E+W). In
22/37 nuclei the moment 2 map shows an increase in the velocity
dispersion close to the peak continuum position.
In 09022-3615, we detect an increase in velocity dispersion
south of the nucleus (distance ∼ 1", equivalent to ∼ 1 kpc),
which corresponds to the most blue-shifted velocities in the moment 1 map. The spectrum in this location shows two peaks.
This could be due to a blue-shifted outflow (or inflow) in this
location, or a cloud pushed by an outflow. An alternative explanation is the presence of a second very obscured nucleus, which
is not detected in the ALMA millimetre continuum. As we do
not see evidence of rotation at the position of the putative second nucleus, we consider more likely the former explanations.
The CO(2-1) peak maps of 10/38 nuclei show a dip in
the centre, corresponding roughly to the position of the continuum peak (e.g. 00188-0856, 12112+0305 NE, 13120-5453,
13451+1232 N). This drop in the centre is compatible with an
extreme central optical depth. In a future work, we will present


Article number, page 4 of 76



ongoing ALMA observations of the optically thin [13] CO isotopologue to investigate this.
In the appendix F, we also show the maps of the CO(2-1)
emission integrated in 50 km s [−][1] channels for all targets.


_4.2._ _Spectro-astrometry_


We perform a spectro-astrometry analysis to identify highvelocity molecular gas that is decoupled from the main rotation
of the galaxy disk. This analysis consists in determining how the
centroid position of the CO(2-1) emission changes as a function
of velocity. We follow a similar methodology to the one used by
García-Burillo et al. (2015) and Pereira-Santaella et al. (2018).
We binned together the velocity channels in order to achieve
a minimum S/N of five, necessary to reliably determine the position of the peak of the emission. To determine the peak position in each binned channel, we first identify the spaxel with the
highest flux. Then, we consider a region of 5 × 5 spaxels centred
on the maximum spaxel and we perform a 2D Gaussian fit. In
this way, we can determine the position at sub-pixel scales. In
some targets, the CO(2-1) peak map presents a dip in the centre (see previous section) in the central velocity-channels. Thus,
the position determined from the pixel with the maximum flux is
not representative of the centroid of the emission. In these cases
(07251-0248, 10190+1322, 13120-5453, 13451+1232, 192970406, 19542+1110, and 20414-1651), we determine the centroid
emission by fitting a 2D Gaussian. The uncertainties on the centroids are calculated as ∆ _x_ = _FWHM_ _beam_ /(2 × _S_ / _N_ ), where
_FWHM_ _beam_ is the beam size and S/N is the signal-to-noise ratio
of the binned channel (Condon 1997). The spectro-astrometry
analysis of 13120-5453 and 20100-4156 SE are shown in Figure 3 and 4 as examples.
We perform a linear bisector fit of the centroids of the lowvelocity channels, to determine the orientation of the kinematic
major axis (see dashed line in Fig. 3, 4, and E.1). As low-velocity
channels, we consider absolute velocities | _v_ | < 300 km s [−][1] . If
there are channels at | _v_ | < 300 km s [−][1] whose position deviates significantly from the direction described by the other lowvelocity channels (e.g. 00091-0738 N), we do not include them
in the fit of the kinematic major axis. To determine the direction
of the high-velocity gas, we perform a bisector fit to the highvelocity centroids (see dotted line in Fig. 3, 4, and E.1). In general, we consider as high-velocity the channels with | _v_ | > 300 km
s [−][1], and we exclude channels that do not agree with the direction of the highest-velocity centroids or that follow the directions of the kinematic major axis. In some cases, the centroids of
the blue-shifted and red-shifted high-velocity channels occupy a
very similar region (e.g. 13451+1232 W or 14378-3651), which
prevents us from determining the direction of the outflow axis. It
is possible that the emission of the high-velocity gas is compact
and unresolved, or that the outflow is pointing towards our line
of sight, so that the blue- and red-sides overlap. In some cases,
we observe some gas deviating from the kinematic major axis,
however, because of its low relative velocity, ∼ 200 − 300 km
s [−][1], it is more likely due to a tidal tail than to an outflow (e.g.
00091-0738 N, 01572+0009).


_4.3._ _Comparison of position angles of the molecular gas,_
_stellar and ionised gas disks_


From the fit of the spectro-astrometry low-velocity channels, we
derive the position angles (PAs) of the kinematic major axis of
the molecular gas disk (listed in Table 2). We obtain the PA of

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



CO(2-1) moment 0


1.2 0 - 1.2 - 2.3
∆RA [arcsec]



1.2 0  - 1.2  - 2.3
∆RA [arcsec]


-200 -100 0 100 200
km s [−][1]


CO(2-1) moment 1



CO(2-1) moment 1



2.3


- 2.3



continuum







2.3 1.2 0 - 1.2 - 2.3
∆RA [arcsec]



CO(2-1) peak


1.2 0 - 1.2 - 2.3
∆RA [arcsec]



0 6 12 18 24 30 36 42 48
mJy/beam


CO(2-1) peak



0 2 4 6 8 10 12 14 16 18
Jy/beam km s [−][1]


CO(2-1) moment 0





4.8


- 4.8



0.0 0.4 0.8 1.2 1.6 2.0 2.4 2.8 3.2 3.6

mJy/beam


continuum



4.8 2.4 0 - 2.4 - 4.8
∆RA [arcsec]



2.4 0 - 2.4 - 4.8
∆RA [arcsec]



2.4 0 - 2.4 - 4.8
∆RA [arcsec]



2.4 0 - 2.4 - 4.8
∆RA [arcsec]



CO(2-1) moment 2


1.2 0    - 1.2    - 2.3
∆RA [arcsec]


30 45 60 75 90 105 120 135 150
km s [−][1]


CO(2-1) moment 2


2.4 0    - 2.4    - 4.8
∆RA [arcsec]


15 30 45 60 75 90 105 120
km s [−][1]


CO(2-1) moment 2


0.8 0    - 0.8    - 1.5
∆RA [arcsec]


15 30 45 60 75 90 105
km s [−][1]


CO(2-1) moment 2


1.0 0    - 1.0    - 1.9
∆RA [arcsec]


15 30 45 60 75 90 105
km s [−][1]



0 6 12 18 24 30 36 42 48 54
mJy/beam


CO(2-1) peak



0.0 1.5 3.0 4.5 6.0 7.5 9.010.512.013.5

Jy/beam km s [−][1]


CO(2-1) moment 0



-300 -200 -100 0 100 200 300
km s [−][1]


CO(2-1) moment 1





1.5


- 1.5



0 0.25 0.5 0.75 1.0 1.25
mJy/beam


continuum



1.5 0.8 0 - 0.8 - 1.5
∆RA [arcsec]



0.8 0 - 0.8 - 1.5
∆RA [arcsec]



0.8 0 - 0.8 - 1.5
∆RA [arcsec]



0.8 0  - 0.8  - 1.5
∆RA [arcsec]


-100 -50 0 50 100
km s [−][1]


CO(2-1) moment 1



0.0 1.5 3.0 4.5 6.0 7.5 9.0
mJy/beam


CO(2-1) peak



0.0 0.2 0.4 0.6 0.8 1.0 1.2 1.4 1.6 1.8

Jy/beam km s [−][1]


CO(2-1) moment 0





1.9


- 1.9



0 0.2 0.4 0.6
mJy/beam


continuum



1.9 1.0 0 - 1.0 - 1.9
∆RA [arcsec]



1.0 0 - 1.0 - 1.9
∆RA [arcsec]



1.0 0 - 1.0 - 1.9
∆RA [arcsec]



1.0 0  - 1.0  - 1.9
∆RA [arcsec]


-200 -100 0 100 200
km s [−][1]



0 0.2 0.4
mJy/beam



0 5 10 15 20
mJy/beam



0 1 2 3 4 5
Jy/beam km s [−][1]



Fig. 2: Examples of the ALMA ∼ 220 − 250 GHz continuum and CO(2-1) moment maps (from left to right: peak map, moment 0, 1,
and 2) for a merger (20087-0308) and an interacting (10190+1322) starburst dominated system and for a merger (01572+0009) and
an interacting (12071-0444) AGN dominated system. The blue crosses mark the position of the nuclei (see Table 1). The magenta
ellipse shows the FWHM and position angle of the ALMA beam . The contours in the maps are: _continuum map_ : [0.3, 0.4, 0.6, 0. 8,
0.9] of the maximum; _peak map_ : 1.5×σ (where σ is the rms) and [0.1, 0. 2, 0.4, 0.6, 0.8] of the maximum; _moment 0_ : [3, 6, 25, 50,
75]×σ (where σ is the rms), _moment 1:_ every 50 km s [−][1] (every 25 km s [−][1] if the maximum value < 100 km s [−][1] ), _moment 2:_ every
25 km s [−][1] (every 15 km s [−][1] if the maximum value < 150 km s [−][1] ).


Article number, page 5 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv


Table 2: Properties of the ALMA CO(2-1) observations.


IRAS name nucleus synthesised beam sensitivity int. time _z_ _CO_ _S_ CO log _L_ CO [′] log _M_ ( _H_ 2 ) FWHM PA
(arcsec×arcsec) [µJy beam [−][1] ] [min.] [Jy km s [−][1] ] [K km s [−][1] pc [2] ] [ _M_ ⊙ ] [km s [−][1] ] [deg.]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11)

00091-0738 S 0.29×0.24 552 100 0.117984 14.4±0.2 9.33 9.26 294±5 303

N 0.118188 12.1± 0.2 9.25 9.18 203±5 300

00188-0856 0.14×0.12 265 69 0.128500 20.6±0.2 9.55 9.48 274±5 268

00509+1225 0.35×0.31 332 48 0.061112 56.9±0.7 9.29 9.22 376±5 136

01572+0009 0.16×0.13 279 69 0.163271 10.8±0.3 9.47 9.40 183±16 306

05189-2524 0.59×0.49 440 34 0.042731 101.1±0.4 9.33 9.26 183±5 93

07251-0248 E 0.36×0.31 332 41 0.087787 55

W 0.087817 271

tot 68.8± 0.7 9.77 9.70 376±5

09022-3615 0.34×0.30 348 37 0.059577 329.4±0.8 10.14 10.07 376±5 0

10190+1322 E 0.36×0.31 330 49 0.075970 61.2±0.2 9.61 9.54 416±5 250

W 0.076626 53.2± 0.8 9.55 9.48 325±5 113

11095-0238 NE 0.31×0.25 460 121 0.106535 6

SW 0.106302     
tot 40.7± 0.1 9.71 9.64 264±5

12071-0444 N 0.22×0.16 367 62 0.128969 40.8±0.6 9.86 9.79 183±5 79

S 0.128441 4.6± 0.2 8.92 8.85 335±15 172

12112+0305 NE 0.34×0.30 265 74 0.072717 122.3±0.5 9.88 9.81 335±5 80

SW 0.073203 27.8± 0.4 9.23 9.17 274±5 290

13120-5453 0.65×0.65 1065 19 0.031114 650.7±2.1 9.87 9.81 335±5 91

13451+1232 W 0.23×0.17 362 81 0.121680 41.5±0.6 9.82 9.76 386±15 242

E 0.121291 2.8± 0.4 8.65 8.58 223±36       
14348-1447 SW 0.35×0.30 345 79 0.082750 116.1±0.6 9.95 9.89 193±5 231

NE 0.082351 64.9± 1.0 9.70 9.63 213±5 196

14378-3651 0.41×0.28 554 47 0.068097 63.7±0.6 9.52 9.45 183±5 211

15327+2340 1.28×0.81 2145 2 0.018120 1693.7±3.5 9.84 9.77 477±5 41

16090-0139 0.20×0.17 436 49 0.133690 75.5±1.0 10.15 10.09 345±10 181

16156+0146 NW 0.24×0.16 498 76 0.132985 6.2±0.3 9.06 8.99 223±25 323
SE       - < 0.05 [⋆] < 6.96 < 6.89       -       
17208-0014 0.47×0.47 1043 7 0.042800 551.4±2.5 10.06 10.00 427±5 109

19297-0406 N 0.34×0.31 282 89 0.085407 230

S 0.085785       
tot 140.3± 0.5 10.05 9.98 386±5

19542+1110 0.40×0.34 368 44 0.062479 40.9±0.3 9.28 9.21 274±5 229

20087-0308 0.31×0.25 287 192 0.105461 94.6±0.3 10.05 9.98 528±5 250

20100-4156 SE 0.20×0.14 336 49 0.129848 31.3±0.3 9.74 9.68 376±5 228

NW 0.129740 2.2± 0.2 8.59 8.52 111±6 268

20414-1651 0.24×0.18 375 47 0.086874 51.4±0.6 9.62 9.56 427±5 59

22491-1808 E 0.44×0.33 342 58 0.077742 59.4±0.2 9.59 9.52 284±5 348

W 0.077560 4.1± 0.2 8.40 8.34 121±5     

**Notes.** (1) IRAS name. (2) Name of the nucleus. (3) FWHM of the synthesised ALMA beam. (4) 1σ line rms sensitivity per 10 km s [−][1] channel.
(5) Integration time on source. (6) CO(2-1) redshift, calculated based on the velocity of the moment 1 map at the ALMA continuum peak position.
(7) CO(2-1) integrated flux. For the interacting systems for which it is not possible to separate the flux belonging to the two nuclei (07251-0248,
11095-0238, and 19297-0406), we report the total flux of the system, as well as the total CO(2-1) luminosity (column 7) and FWHM (column 8).
⋆ For the undetected nucleus 16156+014546 SE, we provide a 3σ upper limit, calculated based on the rms and a typical line FWHM of 300 km
s [−][1] . (8) CO(2-1) luminosity, calculated as _L_ _CO_ [′] [=] [3][.][25][ ·][ 10] [7] _[S]_ _[ CO]_ [ν] _rest_ [−][2] _[D]_ [2] _L_ [(1][ +] _[ z]_ [)] [−][1] [, where][ ν] _[rest]_ [is the line rest-frequency,] _[D]_ _[L]_ [the luminosity distance]
and _z_ the redshift (Solomon et al. 1997). (9) Molecular gas mass calculated as _M_ ( _H_ 2 ) = 1/ _r_ 21 - α _CO_ - _L_ _CO_ [′] (2−1) [, where] _[ r]_ [21] [=] _[L]_ _CO_ [′] (2−1) [/] _[L]_ _CO_ [′] (1−0) [=][ 0][.][91]
(Bolatto et al. 2013b) and α _CO_ = 0.78 _M_ ⊙ /(K km s [−][1] pc [2] ) is the ULIRGs-like CO-to-H 2 conversion factor. (10) FWHM of the integrated CO(2-1)
line, corrected for instrumental resolution. (11) Position angle (PA) of the kinematic major axis measured from the spectro-astrometry of the
low-velocity CO channels. The PA is measured east of north (anticlockwise) for the receding half of the galaxy.



the major axis on the receding half of the galaxy, measured east
of north (anticlockwise). We compare these PAs with the ones
of the stellar and ionised gas (traced by Hα) disks presented in
Perna et al. (2022). Figure 5 shows the absolute differences between PA(CO) and the PA derived from the stellar and ionised
gas kinematics.


Article number, page 6 of 76



Overall, there is a general agreement between these measurements, with differences within ∼ 20 [◦], hence it is consistent with what observed in non-interacting galaxies (see Perna
et al. 2022). We identify only six outliers with PA differences
≫ 20 [◦] (01572+0009, 07251-0248 E, 09022-3615,14348-1447
SW, 16090-0139, and 17208-0014). The PAs of CO are mea
∼
sured on smaller scales ( 1 kpc), compared to the scales used to

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs





20100-4156 SE



CO(2-1) moment 1



1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]



CO(2-1) moment 2



























100


50


0


50


100

















0.75


0.38


0


- 0.38


- 0.75















0.75 0.38 0 -0.38 -0.75
∆RA [arcsec]



-1200-1000-800 -600 -400 -200 0 200 400 600 800 10001200
v [km/s]



Fig. 3: Example of spectro-astrometry and outflow maps for one target (20100-4156 SE) with outflow direction perpendicular to the
kinematic major axis. _Panel a)_ Spectro-astrometry of the CO(2-1) emission line, i.e. centroid position of the CO(2-1) emission in
the different velocity channels. The points are colour-coded by the channel velocity. The pink diamond indicates the peak ALMA
millimetre continuum position. The dashed line is a linear fit to the low-velocity points (kinematic major axis) and the dotted line
is a fit to the high-velocity points (indicating the outflow direction, if present). _Panel_ _b)_ _and_ _c)_ show the moment 1 and moment
2 maps, where the green square indicate the field of view of panel _(a)_ . The grey ellipse illustrates the ALMA beam FWHM. The
grey contours on the moment 1 maps are every 50 km s [−][1] (every 25 km s [−][1] if the maximum value < 100 km s [−][1] ), and every 25 km
s [−][1] (every 15 km s [−][1] if the maximum value < 150 km s [−][1] ) on the moment 2 map. In black are the CO(2-1) moment 0 contours
([3, 6, 25, 50, 75]×σ). _Panel d)_ Emission of the high-velocity channels, integrated over the velocity ranges indicated on the CO(21) spectrum (shown in panel _e_ ). Blue- and red-shifted channels are shown with blue and red contours, respectively (dashed lines
indicate negative contour levels). The lowest contour corresponds to the 3σ level. The next contour levels are (0.5, 0.7, 0.9) of the
peak of the emission, if these are above the 3σ level. The dashed circle shows the size of the outflow ( _R_ _out_ ). _Panel_ _e)_ CO(2-1)
continuum-subtracted spectrum extracted from a circle with radius equivalent to the outflow size ( _R_ _out_ ). The lower panel shows an
y-axis zoom-in to highlight the emission in the wings. The horizontal dashed line shows the 1σ noise level. The vertical dashed lines
indicated the ‘flux-weighted’ velocity of the blue and red-shifted outflow ( _v_ _out_ ). _Panel_ _f)_ OH 119 µm spectrum (upper) compared
with the nuclear CO(2-1) spectrum (bottom), convolved to the resolution of the OH spectrum (FWHM∼ 270 km s [−][1] ). The total fit to
the OH lines is shown with a magenta line, while the Gaussian components of the fit are shown in lightblue and brown. The orange
lines show the 50 Monte Carlo iterations used to estimate the uncertainties on the fit (see Sec. 4.7). The vertical dotted, dashed and
dot-dashed lines show the _v_ 50, _v_ 84, and _v_ 98 percentile velocities, respectively. The blue-shaded area in the upper panel shows the
wavelength range between _v_ 84 and _v_ 98 . Figures for the rest of the sample are in the appendix.



derive the PAs of the stellar disk and ionised gas (∼5-10 kpc).
Thus, we expect to see some differences between the PAs, especially considering the fact that our targets are mergers or interacting systems, many of which do not show regular rotating
disk (only 27% and < 50% of nuclei in the PUMA sample show
rotating disks in the ionised gas and stars, respectively, Perna
et al. 2022). In summary, we find that in most of the targets the
molecular gas disk has an orientation (PA) similar to the stellar
and ionised gas disk.


_4.4._ _Outflow velocity range definition_


One of the main goals of this work is to identify and characterise high-velocity (> 300 km s [−][1] ) outflows of cold molecular
gas, which produce broad wings in the line profile. Moreover,
outflowing gas does not have to follow the disk rotation, thus it
can be identified as high velocity gas that does not follow the
main rotation pattern of the galaxy. For each nucleus, we define the velocity range where a potential outflow is located, us


ing the spectro-astrometry analysis and the integrated CO(2-1)
spectrum. We define the minimum ( _v_ _min_ ) and maximum ( _v_ _max_ )
velocities of the outflow (separately for the blue and red part of
the outflow) and consider the emitting gas in the [ _v_ _min_, _v_ _max_ ] velocity range as part of the outflow.


To define _v_ _min_ and _v_ _max_ for each nucleus, we perform the following procedure, separately for the blue-shifted and red-shifted
emission. We used the spectro-astrometry plot to select the minimum velocity at which the centroid position of the gas starts to
deviate from the direction of the major axis of rotation. In particular, we look for velocity channels whose centroid position
deviates significantly from the direction of the kinematic major
axis, or that does not follow the rotation pattern (from blue to
red). The _v_ _min_ values are in the range | _v_ _min_ | = 180 − 450 km s [−][1] .
To define _v_ _max_, we started from the channel corresponding to _v_ _min_
and we continued adding velocity channels to create the map of
the high-velocity emission, until the peak S/N of the integrated
map starts to decrease. We checked by looking at the integrated
CO(2-1) spectrum that we are not missing significant emission at


Article number, page 7 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv





20087-0308



CO(2-1) moment 1



|Col1|OH|
|---|---|
|zoom −in<br>0.6<br>0.7<br>0.8<br>0.9<br>norm. spec<br><br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>1.2<br>I [mJy]|v50<br>v84<br>v98<br>nuclear CO|


1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]



CO(2-1) moment 2

















0.0

0.2







200


100


0


100


200





150


135


120


105


90


75


60


45


30









0.75


0.38


0


- 0.38










- 0.750.75 0.38 0 -0.38 -0.75

∆RA [arcsec]





-1200-1000-800 -600 -400 -200 0 200 400 600 800 10001200
v [km/s]



Fig. 4: Same as Figure 3, but for 20087-0308, a target with outflow direction not perpendicular to the kinematic major axis.



180


160


140


120


100


80


60


40


20





180


160


140


120


100


80


60


40


20









0


~~PA(CO) [deg. ]~~



0


~~PA(CO) [deg. ]~~



_4.5._ _Measurements of the outflow properties and energetics_


In this section, we describe the method we use to measure the
main outflow parameters: outflow radius ( _R_ _out_ ), outflow velocity ( _v_ _out_ ), and molecular gas mass in the outflow ( _M_ _out_ ). We use
these parameters to derive the outflow energetics: mass outflow
rate ( _M_ [˙] _out_ ), mass-loading factor (η = _M_ [˙] _out_ / _S FR_ ), outflow momentum rate ( _P_ [˙] _out_ ), and kinetic luminosity ( _L_ _out_ ). In the following, we explain how we measure the ‘projected’ _R_ _out_ and _v_ _out_ .
We discuss the inclination corrections in Sec. 4.5.1.


Different methods have been used in the literature to separate the outflow and rotating disk emission. A possible method
(used for example by Pereira-Santaella et al. 2018) consists in
subtracting the flux belonging to the rotating disk, by fitting the
central velocity channels with one or two Gaussians and then
considering only the flux in the residuals as part of the outflow.
However, this method may underestimate the outflow mass as
outflow flux with low (projected) velocities is generally assigned
to the disk regardless of the actual position of the emission. An
alternative method used in the literature consists in fitting the
line profile using a systemic Gaussian component and a broader
Gaussian component for the outflow (e.g. Fluetsch et al. 2019).
This method may be overestimating the flux of the outflowing
gas, since it considers that a large portion of the outflowing gas
is at low velocities.


Since the resolution of the observations allows us to determine the position of the gas and to identify the gas that is not
following the galaxy rotation, we prefer to consider only the gas
with high velocities as part of the outflow. Moreover, most of
the line profiles of our targets cannot be well fitted using a simple model with only one or two Gaussians (see Fig. 3, 4 and
E.1). The line profiles are asymmetric and show multiple peaks,
which could also include self-absorption (see Sec. 4.1). Thus, to
measure the outflow gas mass, we consider the total flux in the
high-velocity channels, highlighted in the blue and red shaded
regions on the spectra (see Fig. 3, previous section), without
subtracting the low-velocity Gaussian fit.



Fig. 5: Absolute difference between the position angles (PAs) of
the kinematic major axis derived from CO and the PAs derived
from the stellar kinematics ( _left_ ), and the ionised gas kinematics
( _right_ ). The PAs of the stars and ionised gas are taken from Perna
et al. (2022). The dashed lines show a difference of 20 [◦] . The
names of galaxies with large PA differences (≫ 20 [◦] ) are shown
on the figure. The colours and shapes of the symbols are as in
Fig. 1.


_v_ - _v_ _max_ due to a particular low S/N channel. The _v_ _max_ values are
in the range | _v_ _max_ | = 300 − 800 km s [−][1] . Figure 3, 4, and E.1 show
the CO(2-1) spectra with the blue-shifted and red-shifted outflow
velocity ranges highlighted with blue and red shaded areas. The
integrated maps of the blue- and red-shifted outflow channels are
shown as contours in the bottom-left panel of the figures.
One caveat of our analysis is that since we are observing
projected velocities, we are not sensitive to high velocity gas in
the plane of the sky. Additionally, with our method we are not
considering outflowing gas with low projected velocities, that is
with velocities _v_ such that _v_ _min_ ( _blue_ ) < _v_ < _v_ _min_ ( _red_ ), because
it overlaps with the velocities of the rotating disk. In order to
identify this gas, we would need to model the rotation of the
system to identify non-rotating gas (e.g. Brusa et al. 2018; Gao
et al. 2021; Ramos Almeida et al. 2022). We plan to investigate
this in a future work.


Article number, page 8 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



In Section 4.5.2), we discuss the systematic effects affecting
the derived outflow quantities depending on the different
methods. A comparison of our outflow parameters with the
ones reported by Fluetsch et al. (2019) and Lutz et al. (2020) is
shown in Section 4.6.


**Outflow size** : to measure the outflow radius, we fit a 2D Gaussian model to the high-velocity maps, obtained integrating the
flux over the high-velocity channels (see bottom left panel in
Fig. 3), separately for the blue and red part. To take into account
the beam size and obtain the ‘intrinsic radius’, we convolve our
model with a 2D Gaussian with the shape of the ALMA beam,
and we fit this ‘convolved model’ to the maps. The radius of the
blue (red) part of the outflow is defined as:

_R_ _[b]_ _out_ [=] _[ d]_ _c_ _[b]_ [+] _[FWHM]_ 2 _[b]_, (1)


where _d_ _c_ _[b]_ [is the centroid distance from the nucleus and] _[ FWHM]_ _[b]_
is the average size (deconvolved from the beam) of the two axes
of the 2D Gaussian fit.
The outflow radius _R_ _out_ is the mean of the radii of the blueand red-shifted wings:


_R_ _out_ = 0.5 · ( _R_ _[b]_ _out_ [+] _[ R]_ _[r]_ _out_ [)][,] (2)


The outflow radii are shown in Fig. 3 as dashed circles (bottom
left panel). This method is analogous to the method used by Lutz
et al. (2020), although applied here to higher spatial resolution
data (400 pc vs. 700 pc), which is enough to resolve the outflow
structure. Due to the limited S/N of the single channels, it is not
possible to measure the radius in each channel, which would give
a more accurate measurement to derive the mass outflow rate.
We also measure the maximum extent of the outflow, by taking the maximum distance from the continuum position reached
by the 3σ contour. We subtract the beam size in quadrature to obtain the ‘intrinsic’ distance. Then, we take the mean between the
radius of the red- and blue-shifted channels as the representative
maximum radius of the outflow ( _R_ 3σ ).
The outflow radii _R_ _out_ measured from the 2D Gaussian fit are
in the range 0.18 − 0.94 kpc (0.1 − 1.5"). The maximum outflow
radii _R_ 3σ are in the range 0.1 − 2.1 kpc (0.05 − 2.5"). The ratio of
the observed _R_ 3σ / _R_ _out_ is in the range 1-3, with a mean of 1.45.
We note that in some cases the _R_ 3σ values reported in Table 3
are smaller than _R_ _out_ . This is due to the different way used to
deconvolve the beam and to the uncertainty on the Gaussian fit.
We calculate that > 50% of the outflow flux is within _R_ _out_, with
a median of 76%. Given that most of the outflow flux is located
within _R_ _out_, we decide to use _R_ _out_ to compute the mass outflow
rate and the energetics. If we were to use the outflow flux within
_R_ 3σ instead of within _R_ _out_ to calculate the outflow mass, _M_ _out_
would increase on average by a factor of 1.3 (0.11 dex). The
mass outflow rate is proportional to _M_ _out_ / _R_ _out_, thus the larger
molecular mass included within _R_ 3σ is counterbalanced by the
larger radius. If we were to use _R_ 3σ and the outflow flux within
this radius, we would obtain very similar values (less than 8%
smaller, −0.04 dex) compared to the _M_ [˙] _out_ estimated using _R_ _out_ .
We do not attempt to correct the radii of the single targets
for inclination, since information about the inclination is not
available for the full sample (see discussion in Sec. 4.5.1).


**Outflow mass** : To derive the outflow mass, we extract the central spectrum from a radius equal to the observed _R_ _out_ (not deconvolved from the beam) and we integrate the flux in the highvelocity channels between _v_ _min_ and _v_ _max_, separately for the blue



where _R_ _out_ is the outflow radius, _M_ _i_ is the H 2 gas mass in the
channel with velocity _v_ _i_, and the sum is over the velocity channels identified as part of the blue-shifted (or red-shifted) emission (see Fig. 3). The total mass outflow rate is the sum of the
blue and red _M_ [˙] _out_ . We note that this formula corresponds to the
assumption that the outflow has started at a point in the past
(− _t_ = − _R_ _out_ / _v_ _out_ ) and has continued with a constant _M_ [˙] _out_ (Rupke
et al. 2005b; Veilleux et al. 2005; Lutz et al. 2020). Under this


Article number, page 9 of 76



and the red part of the outflow. The central spectra are shown in
Fig. 3, 4 and E.1 (bottom row, middle panel). Then, we sum
the flux of the blue and red part of the outflow to obtain the total
outflow flux ( _F_ _out_ ).
We estimate the uncertainties on _F_ _out_ by extracting a spectrum from a region away from the source and measuring the standard deviation of the flux density in the high-velocity channels
(σ in units of mJy) . The uncertainty on _F_ _out_ is :


_F_ _out_, _err_ = σ · ∆ _v_ _ch_ - � _N_ _ch_, (3)


where ∆ _v_ _ch_ is the width of a velocity channel in km s [−][1], and _N_ _ch_
is the number of velocity channels in the high-velocity windows.
We transform the CO(2-1) flux into luminosity (in units of K km
s [−][1] pc [2] ) using the formula:


_L_ _CO_ [′] [=][ 3][.][25][ ·][ 10] [7] _[S]_ _[ CO]_ [ν] _rest_ [−][2] _[D]_ [2] _L_ [(1][ +] _[ z]_ [)] [−][1] [,] (4)


where _S_ _CO_ is the velocity-integrated CO line flux in Jy km s [−][1],
ν _rest_ is the line rest-frequency in GHz, _D_ _L_ is the luminosity
distance in Mpc, and _z_ is the redshift (Solomon et al. 1997). We
convert the CO(2-1) luminosity to CO(1-0) luminosity using
_r_ 21 = _L_ CO(2-1) [′] [/] _[L]_ CO(1-0) [′] [=] [0][.][91] [(][Bolatto] [et] [al.] [2013b][).] [Then] [we]
multiply it by the ULIRGs-like CO-to-H 2 conversion factor α=
0.78 M ⊙ /(K km s [−][1] pc [2] ), to obtain the outflow molecular (H 2 )
gas mass _M_ _out_ . Although, we note that the cold molecular gas
conditions in the outflow likely differ from those in the disk and,
therefore, the CO-to-H 2 outflow conversion factor is uncertain
(see e.g. Pereira-Santaella et al. 2020).


**Mean** **outflow** **velocity** : We calculate the mean velocity of the
outflow separately for the blue- and red-shifted high-velocity
wings, by taking the flux-weighted mean of the velocity in the
channels identified as part of the blue-shifted (or red-shifted)
emission (see Sec. 4.4, Fig. 3, middle panel of the bottom row):


� _i_ _[v]_ _i_ [·] _[ F]_ _i_
_v_ _out_ =, (5)
� _i_ _[F]_ _i_


where _v_ _i_ is the velocity of channel _i_ and _F_ _i_ is the CO(2-1) flux
density in that channel.
Different methods have been used in the literature to
estimate the outflow velocity (see Sec. 4.5.2). We decide to use
this ‘flux-weighted velocity’ to calculate the mass outflow rate,
because it is independent from the modelling of the emission
line profile and it gives more weight to the velocities at which
most of the emission takes place. We note that the outflow
velocities measured with this method are sensitive to the choice
of the velocity window defined as ‘high-velocity gas’. In
Sections 4.5.2 and 4.6 we explore this possible bias.


**Mass outflow rate** : For the red and blue part of the outflow separately, we calculate the mass outflow rate (in units of [M ⊙ yr [−][1] ])
using the formula:




[| ·] _[ M]_ _[out]_ � _i_ [|] _[v]_ _i_ [| ·] _[ M]_ _i_

=
_R_ _out_ _R_ _out_



˙
_M_ _out_ = [|] _[v]_ _[out]_ [| ·] _[ M]_ _[out]_



, (6)
_R_ _out_

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



assumption, the average volume density of the outflowing gas
decreases with radius (∝ _R_ [−][2] ). Assuming that the outflowing gas
fills a spherical or multi-conical volume with a constant average
volume density, would increase _M_ [˙] _out_ by a factor of three (e.g.
Maiolino et al. 2012; Cicone et al. 2014; Lutz et al. 2020).
In the cases where the outflow is not detected, we estimate
3σ upper limits on _M_ [˙] _out_ as:


˙
_M_ _out_, _UL_ = 3 · [⟨] _[v]_ _[out]_ ⟨ [⟩·] _R_ _[ M]_ _out_ ⟩ _[out]_ [,] _[err]_, (7)

where ⟨ _v_ _out_ ⟩ = 390 km s [−][1] and ⟨ _R_ _out_ ⟩ = 0.52 kpc are the median
outflow velocity and radius of our sample. _M_ _out_, _err_ is calculated
based on _F_ _out_, _err_ (eq. 3), measured from the spectrum extracted
from a radius ⟨ _R_ _out_ ⟩. The mass outflow rates are in the range ∼ 5
to ∼ 300 M ⊙ yr [−][1] .
We compare the outflow properties ( _v_ _out_, _R_ _out_ and _M_ _out_ ) measured from the blue and red-shifted wings. The _v_ _out_, _R_ _out_ and
_M_ _out_ measured from the red and blue parts are similar within a
factor of 1.6, 2.4 and 1.2 respectively. The mean and corresponding standard deviation of the ratio of the red- and blue-shifted
outflow quantities are: 0.97 ± 0.16, 1.05 ± 0.51, 0.99 ± 0.04, respectively.


4.5.1. Inclination corrections


We do not attempt to correct the outflow radii and velocities of
the single targets for the inclination, since this information is
not available for all objects. In order to apply an inclination correction to _v_ _out_ and _R_ _out_, we need to know the inclination of the
outflow with respect to our line of sight. Even if we knew the
inclination of the molecular gas disk, in order to use this information we would need to know the inclination of the outflow
with respect to the disk. In Sec. 5.2 we discuss the projected angles between the outflow axis and the major kinematics axis. For
a handful of targets (6), there is evidence that the outflow may
be perpendicular to the major kinematics axis. However, only for
one of them we have a measurement of the ionised gas (or stellar) disk inclination from Perna et al. (2022). Thus, we decide
not to attempt to correct for inclination _v_ _out_ and _R_ _out_ of the single
targets, and all the quantities reported here are the ‘projected’

ones.
However, we derive an average inclination correction that we
apply to the average outflow properties of the sample. To convert
the observed (projected) mean outflow velocity to intrinsic velocity, we need to divide _v_ _out_ by sin( _i_ ), where _i_ is the inclination.
Analogously, the observed outflow radius needs to be divided by
cos( _i_ ) to recover the intrinsic value. Following Law et al. (2009),
who considered the average for a collection of objects oriented
isotropically in space, the average correction for the velocities
is 1/ ⟨sin( _i_ )⟩ = 1/0.79 = 1.27. Analogously, we calculated the
average correction for the radius: 1/ ⟨cos( _i_ )⟩ = 2. We use these
values to correct the mean outflow velocity and mean outflow
radius reported in table 3.
It is not possible to derive the average inclination correction
for the mass outflow rate _M_ [˙] _out_ in a similar way, since the calculation of the integral over the entire solid angle gives infinity.
However, the average inclination correction for the dynamical
time ( _t_ _dyn_ = _R_ _out_ / _v_ _out_ ∝ _M_ _out_ / _M_ [˙] _out_ ) is unity (see Cicone et al.
2015).


4.5.2. Caveats: Methods to measure outflow parameters


In this section, we discuss how the outflow parameters (in
particular _v_ _out_, _M_ _out_ and _M_ [˙] _out_ ) change depending on the method


Article number, page 10 of 76



adopted for the measurements. Readers who are less interested
in the details about the methodology and the comparison with
previous works may wish to go directly to Section 4.7.


_1)_ _Low_ _projected_ _velocity_ _(v_ < 300 _km_ _s_ [−][1] _)_ _gas_ _in_ _the_ _out-_
_flow_ : since we are not considering low projected velocities (| _v_ | ≲
200 − 300 km s [−][1] ), it is possible that we are missing part of the
outflow flux. If we were to consider also this low velocities, the
outflow mass _M_ _out_ would increase and the flux-weighted outflow velocity _v_ _out_ would decrease. Overall, we expect _M_ [˙] _out_ to
increase, but by a lower factor than _M_ _out_, because the increase in
_M_ _out_ is counterbalanced by the decrease of _v_ _out_ .
To test how much this effect could affect our measurements
of the outflow properties, we consider 3D models of biconical
outflows based on the models presented by Bae & Woo (2016).
The outflow is a bicone with a half opening angle of 40 [◦] . We set
the maximum velocity of the outflow to 750 km s [−][1] . We consider
several outflow radial velocity profiles, motivated by previous
works in the literature (e.g. Förster Schreiber et al. 2014; Venturi
et al. 2018; Meena et al. 2021), and different outflow inclinations
with respect to the line of sight. More details on the simulations
can be found in the appendix A. We measure _v_ _out_, _M_ _out_ and _M_ [˙] _out_
from the total simulated profile (outflow+systemic component)
considering only | _v_ | - 300 km s [−][1], to mimic the method we are
using with our data. Then, we measure the outflow quantities
( _v_ _out_, _M_ _out_, and _M_ [˙] _out_ ) from the simulated outflow emission profile (without the systemic component) considering the full velocity range.
The _M_ _out_ measured from | _v_ | > 300 km s [−][1] are underestimated
compared to the values measured from the entire velocity range
by a factor of 0.2 − 1 (average 0.5), while the _v_ _out_ are overestimated˙ by up to a factor of 2.2 (average of 1.6). Consequently,
_M_ _out_ would be underestimated by up to ∼0.45 dex (65%) for
outflow inclinations close to the plane of the sky (90 [◦] ). For an
inclination of 10 [◦], the measured _M_ [˙] _out_ would be underestimated
by up to 0.1 dex (see Fig. 6).
For targets with a wide CO(2-1) line core (large FWHM), the
flux of the gas in the rotating disk can overlap with the outflow
flux up to larger velocities. Indeed, there is a positive correlation
between the velocity at which we start to consider the flux to
be dominated by the outflow ( _v_ _min_ ) and the FWHM of the line
(Spearmann rank correlation coefficient _r_ = 0.81, _p_ -value< 0.1).
We did a test to estimate how much flux we may be missing in
our measurements of the outflow flux for the targets with large
FWHM CO(2-1) line profiles. In particular, we consider the 13
targets with | _v_ _min_ | - 300 km s [−][1] (either in the blue or red side).
To estimate the amount of possible flux belonging to the outflow
in the velocity range between | _v_ | = 300 km s [−][1] and | _v_ _min_ |, we
assume the outflow flux density in this range to be equal to the
value at _v_ _min_ . Using this assumption, we estimate the outflow
parameters ( _M_ _out_, _v_ _out_, and _M_ [˙] _out_ ) starting from _v_ _min_ = 300 km
s [−][1] . We find that the value of _M_ _out_ increases by 0.28 dex on
average (maximum 0.67 dex), while _v_ _out_ decreases by a factor
of −0.07 dex on average (minimum −0.11 dex). So, the _M_ [˙] _out_
estimates increase by 0.2 dex on average (maximum 0.6 dex).


_2)_ _Possible_ _overestimation_ _of_ _M_ ˙ _out_ _due_ _to_ _the_ _rotating_ _disk_
_contribution at_ | _v_ | = 250 − 300 _km s_ [−][1] : Since we do not model
and subtract the disk rotation, it is possible that at low velocities
(250 − 350 km s [−][1] ) we are including in the outflow flux some
flux emitted by the gas in the rotating galaxy disk. To test how
large this contribution could be, we subtract from the spectra
the flux due to rotation estimated by modelling the core of the
emission profile (with absolute velocities smaller than ∼ 300 km

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs


Table 3: CO(2-1) observed outflow properties.


IRAS name n. [ _v_ _min_, _v_ _max_ ] (b) [ _v_ _min_, _v_ _max_ ] (r) _S_ _CO_ (b) _S_ _CO_ (r) _R_ 3σ _R_ _out_ _v_ _out_ log _M_ _out_ log _M_ [˙] _out_ angle _out_

[km s [−][1] ] [km s [−][1] ] [Jy km s [−][1] ] [Jy km s [−][1] ] [kpc] [kpc] [km s [−][1] ] [M ⊙ ] [M ⊙ yr [−][1] ] [deg.]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12)

00091-0738 S - - - - - - - <7.26 <1.15 
N     -     -     -     -     -     -     - <7.20 <1.08     
00188-0856 - - - - - - - <7.33 <1.22 
00509+1225 - - - - - - - <6.62 <0.50 
01572+0009 - - - - - - - <7.62 <1.51 05189-2524 [-200,-600] [200,350] 1.27±0.05 1.27±0.04 1.39 0.83±0.01 294±16 7.66±0.01 1.22±0.01 07251-0248 E [-320,-500] [300,550] - 0.32±0.01 0.64 0.17±0.01 377±12 7.37±0.01 1.72±0.01 W    -    -    -    -    -    -    - <6.87 <0.75    09022-3615 [-400,-700] [300,500] 6.87±0.05 2.05±0.04 1.68 0.94±0.01 423±8 8.50±0.01 2.17±0.01 12
10190+1322 E [-290,-410] [350,420] 0.06±0.02 0.09±0.02 0.60 0.62±0.02 366±143 6.96±0.08 0.74±0.08 75
W    -    -    -    -    -    -    - <6.78 <0.66    11095-0238 NE [-300,-500] [300,500] 0.25±0.02 0.22±0.02 0.46 0.37±0.01 373±37 7.70±0.02 1.71±0.02 32
SW     -     -     -     -     -     -     - <7.05 <0.94     12071-0444 N [-250,-430] [260,400] 0.22±0.03 0.22±0.03 0.36 0.40±0.01 385±65 7.83±0.04 1.82±0.04 37
S      -      -      -      -      -      -      - <7.37 <1.26      12112+0305 NE [-250,-700] [250,700] 2.43±0.03 4.09±0.03 2.07 0.59±0.01 357±6 8.54±0.01 2.33±0.01 90
SW [-200,-600] [200,400] 0.51±0.04 0.29±0.03 0.73 0.63±0.01 292±32 7.63±0.03 1.31±0.03 84
13120-5453 [-300,-800] [300,600] 5.38±0.15 2.48±0.13 0.70 0.37±0.01 432±25 7.89±0.01 1.96±0.01 29
13451+1232 W - - - - - - - <7.62 <1.50 
E      -      -      -      -      -      -      - <7.22 <1.10      14348-1447 SW [-250,-700] [250,700] 1.46±0.04 1.59±0.04 1.78 0.67±0.01 380±13 8.31±0.01 2.07±0.01 56
NE [-300,-550] [300,600] 0.57±0.03 0.46±0.03 1.36 0.69±0.01 393±35 7.83±0.02 1.60±0.02 82
14378-3651 [-200,-600] [200,300] 1.16±0.05 0.32±0.02 0.69 0.51±0.01 311±24 7.82±0.02 1.61±0.02 15327+2340 [-450,-600] [400,600] 4.06±0.15 2.08±0.18 0.96 0.56±0.01 474±43 7.33±0.02 1.26±0.02 64
16090-0139 [-400,-600] [350,600] 0.33±0.04 0.70±0.04 0.69 0.50±0.01 454±58 8.22±0.02 2.19±0.02 16156+0146 NW - - - - - - - <7.32 <1.21 
SE      -      -      -      -      -      -      - <7.47 <1.35      17208-0014 [-400,-800] [390,450] 3.18±0.17 0.18±0.06 0.49 0.51±0.01 487±148 7.78±0.03 1.77±0.03 3
19297-0406 N [-350,-500] [350,500] 0.28±0.02 0.27±0.02 1.01 0.64±0.01 409±42 7.58±0.02 1.40±0.02 49
S      -      -      -      -      -      -      - <6.76 <0.64      19542+1110 [-250,-400] [300,500] 0.19±0.02 0.16±0.02 0.48 0.38±0.01 346±52 7.14±0.03 1.11±0.03 72
20087-0308 [-350,-450] [380,600] 0.22±0.01 0.39±0.02 1.12 0.67±0.01 425±32 7.79±0.01 1.60±0.01 40
20100-4156 SE [-300,-800] [250,800] 0.90±0.04 1.05±0.04 0.76 0.44±0.01 438±26 8.47±0.01 2.48±0.01 70
NW    -    -    -    -    -    -    - <7.39 <1.28    20414-1651 [-350,-440] [300,400] 0.18±0.03 0.25±0.03 0.44 0.52±0.01 364±84 7.48±0.05 1.33±0.05 25
22491-1808 E [-200,-400] [200,600] 1.69±0.01 0.68±0.01 0.92 0.26±0.01 263±5 8.12±0.01 2.14±0.01 57
W    -    -    -    -    -    -    - <6.60 <0.49    average [∗] 1.84 1.07 485 8.01 1.89


**Notes.** (1) IRAS name. (2) Name of the nucleus. (3) and (4) Velocity range considered to measure the blue- and red-shifted wings of the CO(2-1)
profile with respect to the systemic velocity. (5) and (6) CO(2-1) flux in the blue- and red-shifted wings. (7) Maximum extent of the outflow
estimated from the emission above 3σ (see Sec. 4.5). (8) Outflow radius (of the blue- and red-shifted wings) deconvolved from the beam, but not
corrected for inclination. (9) Flux-weighted outflow velocity (see eq. 5), not corrected for inclination. (10) Outflow molecular gas mass, calculated
assuming a ULIRG-like conversion factor α _CO_ of 0.78 M ⊙ /(Kkm s [−][1] pc [−][2] ) [−][1] and _r_ 21 ratio of 0.91 (Bolatto et al. 2013b). (11) Mass outflow rate
calculated using equation 6. (12) Angle between the outflow axis and the kinematic major axis, derived from the spectro-astrometry, for the cases
where it could be determined. [∗] Average outflow properties, excluding upper limits. The average of _R_ _out_ and _v_ _out_ have been corrected for inclination
assuming the average corrections: _R_ _out_ = _R_ _out_ ( _obs_ )/ ⟨cos( _i_ )⟩ = 2 · _R_ _out_ ( _obs_ ), _v_ _out_ = _v_ _out_ ( _obs_ )/ ⟨sin( _i_ )⟩ = 1.27 · _v_ _out_ ( _obs_ ) (see Section 4.5.1).



s [−][1] ) with one, two or three Gaussians (e.g. Pereira-Santaella
et _v_ _out_ al., _M_ 2018˙ _out_ ) ).fromThen,theweresiduals,computeconsideringthe outflowtheparametersvelocity (range _M_ _out_,
between _v_ _max_ and the velocity ( _v_ _min_ ) at which the residuals
approach zero. The outflow masses vary in the range −1.0 dex
to 0.5 dex (−0.12 dex on average). In some cases, the measured
_M_ _out_ increases because we can extend the outflow velocity
range to smaller velocities, since there is no risk of including
flux from the rotation. The outflow velocities vary by less than
±50 km s [−][1] . The _M_ [˙] _out_ vary between −0.82 dex and +0.45 dex



(−0.11 dex on average).


_3) Di_ ff _erent methods to estimate the outflow velocity_ : In this
work, we adopted the ‘flux-weighted’ outflow velocity definition to compute the mass outflow rate. Other works instead have
used different definitions of ‘maximum outflow velocity’ (e.g.
Fluetsch et al. 2019; Lutz et al. 2020). If we assume a biconical
outflow with constant gas velocity within the outflow, the range
of velocities observed in the broad wings of the CO profile would
be solely due to different orientation angles of the outflow gas
clouds with respect to our line of sight. The part of the outflow


Article number, page 11 of 76

3.5


3.0


2.5


2.0


1.5


1.0


0.5



0.18


0.16


0.14


0.12


0.10


0.08


0.06


0.04


0.02


0.00


0.18


0.16


0.14


0.12


0.10


0.08


0.06


0.04


0.02


0.00



|Col1|Col2|Col3|2.5<br>2.0<br>FWHM/vout<br>1.5<br>1.0 vmax,|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|outflow emission : incl. =<br>vout(|v| > 300 km/s)<br>vout(total)|10◦||||||
||||||||
||||||||


|outflow emission : incl. = 90◦<br>vout(|v| > 300 km/s)<br>vout(total)|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||



1000 500 0 500 1000
velocity [km/s]



_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv







200 250 300 350 400 450 500
v out [km s [−][1] ]



Fig. 6: Simulated outflow profiles for outflow inclinations with
respect to our line of sight of 10 [◦] ( _upper_ ) and 90 [◦] ( _bottom_ ).
The outflow velocity in this particular simulation increases up
to a turnover radius and then decreases. Up to four different velocity fields are considered in Appendix A. The magenta curve
shows the outflow component, the grey curve the systemic component and the black curve the total profile. The vertical dashed
lines show the flux-weighted _v_ _out_ measured from the total profile at | _v_ | ≥ 300 km s [−][1] (coloured in blue and red). The vertical
solid lines show the flux-weighted _v_ _out_ measured from the outflow component over the full velocity range. For high outflow
inclination (close to the plane of the sky), the contribution to the
outflow flux by the gas at low projected velocities (| _v_ | < 300 km
s [−][1] ) increases.


closer to our line of sight would have the highest observed velocity. Thus, one could assume that this maximum velocity is the
closest to the true/intrinsic velocity. We do not know the true radial profile of the velocity or the geometry of the outflowing gas
for our targets. However, we can estimate how much our ‘fluxweighted outflow velocity’ differ from the ‘maximum outflow
velocity’ assumption in our sample. We consider two definition
of the maximum velocity. Both definition require the fit of the
line profile with multiple Gaussian components: a broad component for the outflow, and other components for the systemic
emission. The first definition that we consider is the prescription
from Rupke et al. (2005a), used for example by Fluetsch et al.
(2019):



_v_ _max_, _FWHM_ = |∆ _v_ | + _[FWHM]_ 2 _[broad]_, (8)


where |∆ _v_ | is the shift of the broad Gaussian outflow component
with respect to systemic velocity and _FWHM_ _broad_ its full width
at a half maximum. The second definition, adopted for example
by Lutz et al. (2020), is:



_v_ _max_, _FW_ 10 = |∆ _v_ | + _[FW]_ 2 [10%], (9)


where _FW_ 10% is the full width of the broad component at a
tenth of its peak. We measure _v_ _max_, _FWHM_ and _v_ _max_, _FW_ 10 for
our sample of galaxies with outflow detection. We use up to
three Gaussian components to model the systemic emission. We
stress that in most of the cases, the parameters of the Gaussian
components are highly degenerate. Thus, the derived maximum


Article number, page 12 of 76



Fig. 7: Comparison of different methods for measuring the outflow velocity. _Left:_ Ratio between the maximum outflow velocity
_v_ _max_, _FWHM_ (eq. 8) and the flux-weighted outflow velocity ( _v_ _out_ )
in our sample. _Right:_ Ratio between _v_ _max_, _FW_ 10% (eq. 9) and _v_ _out_ .
The horizontal lines show the 1-to-1 ratio.


velocity can vary depending on the assumptions used in the fit.
In Fig. 7 we compare the flux-weighted _v_ _out_ with the maximum
velocity _v_ _max_, _FWHM_ and _v_ _max_, _FW_ 10 for our sample. The ratio
_v_ _max_, _FWHM_ / _v_ _out_ varies between 0.5 and 2.0, with a median 0.9.
The ratio _v_ _max_, _FW_ 10 / _v_ _out_ instead is almost always larger than
one, with a maximum of 3.2 and a median of 1.6. Assuming
that _v_ _max_ is the closest measure of the ‘true’ outflow velocity, it
does not need to be corrected for inclination, while the observed
(projected) _v_ _out_ would need to be corrected by an average factor
of 1.3 (see Sec. 4.5.1). This factor can account for most of the
average difference between _v_ _max_, _FW_ 10 and _v_ _out_ .


We decide to avoid the methods based on the fit of the emission line profile with multiple Gaussian components, because the
components are degenerate and this will introduce further uncertainties in the measurements.

An additional caveat is related to the definition of _v_ _max_, which
will impact the _v_ _out_ estimates. In selecting _v_ _max_ based on the
S/N of the integrated high-velocity maps, it is possible that we
are excluding diffuse high-velocity flux which is below the 3σ
level. In this way, we may underestimate _v_ _out_, especially for cases
in which the outflow velocity increases radially. Unfortunately,
with our current data it is not possible to estimate the impact of
this possible additional component. Higher sensitivity observations are needed for this purpose.
In Table 4, we summarise the average biases in the outflow
properties ( _v_ _out_, _M_ _out_ and _M_ [˙] _out_ ) due to the effects described in
1), 2) and 3). Since the two effects described in 1) and 2) go in
opposite directions, they tend to compensate each other. Taking
into account the two effects, we may be underestimating _M_ _out_
∼ 0.2 dex and _M_ [˙] _out_ by ∼ 0.04 dex on average.
Based on the variations of outflow quantities from the tests
using different methods, we estimate the typical uncertainties on
the outflow quantities. For the outflow velocity, we estimate a
typical uncertainty of 0.1 dex, while for _M_ _out_ and _M_ [˙] _out_ we adopt
a typical uncertainty of 0.3 dex. For _R_ _out_, we estimate a typical
uncertainty of 0.2 dex, based on the difference between _R_ _out_ and
_R_ 3σ .
The uncertainties on _M_ [˙] _out_ are dominated by the uncertainties
on the α _CO_ conversion factor, which can be up to 0.7 dex (Papadopoulos et al. 2012; Bolatto et al. 2013b; Pereira-Santaella
et al. 2020), and on the outflow geometry. If the α _CO_ is more
similar to the Galactic value (α _CO_ =4.3 M ⊙ /(K km s [−][1] pc [2] )), it
would imply that all our _M_ _out_ and _M_ [˙] _out_ measurements are under

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



Table 4: Possible biases in the outflow properties measured with
our method, due to different issues.


_v_ _out_ biases in outflow properties _M_ _out_ _M_ ˙ _out_

[dex] [dex] [dex]


1) Not considering outflow flux at | _v_ | < 300 km s [−][1] :
average: 0.20 −0.30 −0.15
range: (0, 0.34) (−0.70, 0) (−0.45, 0)


2) Rotating disk contribution at | _v_ | = 250 − 300 km s [−][1] :
average: −0.01 0.12 0.11
range: (−0.08, 0, 08) (−1.0, 0.5) (−0.82, 0.45)


3) Flux-weighted velocity instead of _v_ _max_ :
average: −0.20 − −0.20
range: (−0.50, 0.30) − (−0.50, 0.30)


estimated by a factor of ∼ 5 (0.7 dex), while if the optically thin
case applies (α _CO_ = 0.35 M ⊙ /(K km s [−][1] pc [2] )), our measurements
would be overestimated by a factor of ∼ 2 (Bolatto et al. 2013b).


_4.6._ _Comparison with previous works_


In this Section we compare the derived outflow parameters with
previous works that study properties of molecular outflow in
nearby ULIRGs using CO observations.


4.6.1. Comparison with Lutz et al. (2020)


Lutz et al. (2020) study the outflow properties in a sample of
54 nearby ( _z_ < 0.2) galaxies with CO(1-0), CO(2-1) or CO(32) observations, with a range of spatial resolutions (30 pc to
5 kpc; 0.5 − 5 arcsec beam FWHM). They collect 41 nearby
galaxies with molecular outflow detections or upper limits from
the literature. They also present new NOEMA and ALMA observations, with a spatial resolution of ∼700 pc (0.5-3.7 arcsec
beam FWHM), for 13 compact far-infrared galaxies from the
Lutz et al. (2016) sample. To derive the outflow velocity and flux,
they fitted the line profile with two Gaussian components (systemic and broad (outflow) component). They defined the outflow
velocity using Eq. 9. To derive the outflow flux, they integrated
the broad component only over the velocity ranges for which
it contributes at least 50% of the total flux density of the line
profile. The outflow radius was defined similarly to our method:
_R_ _out_ = |∆ _R_ |+ _FWHM_ /2, where |∆ _R_ | is the distance of the outflow
emission centroid from the continuum position and _FWHM_ was
derived from a Gaussian spatial fit in the _uv_ -plane using a velocity range that is dominated by outflow, although, the spatial
resolution is a factor of ∼ 2 lower than in our work. For the other
41 targets, they collect information about the outflow parameters
( _v_ _out_, _R_ _out_, _M_ _out_ ) from the data published in the literature, trying
to be consistent with their adopted definition of these parameters
and their adopted methodology to separate the flux of the line
core and high velocity wings.
There are 12 objects in common with our sample, with data
published by Cicone et al. (2014) Barcos-Muñoz et al. (2018),
Gowardhan et al. (2018), Pereira-Santaella et al. (2018), and
Lutz et al. (2020). We compare our measurements of the outflow parameters ( _v_ _out_, _R_ _out_, _M_ _out_, _M_ [˙] _out_ ) with these works in Figure 8. There are some discrepancy between our measurements



and the literature values. In particular for two galaxies (172080014 and 20100-4156) the literature _v_ _out_ is larger than 900 km
s [−][1], while we measure _v_ _out_ < 500 km s [−][1] . For 20100-4156, it
is possible that the spectral range of our observations ( _v_ = [1200, 1200] km s [−][1] ) is not wide enough to detect the emission
at very high velocities (| _v_ _out_ | - 1000 km s [−][1] ). Additionally, this
high-velocity outflow is detected in CO(1-0), while in CO(3-2)
no outflow is detected (Gowardhan et al. 2018). Thus, it is possible that this difference also depends on the J-level observed. For
17208-0014, the S/N of the outflow component presented in Lutz
et al. (2020) is not very high, thus the uncertainty on _v_ _out_ should
be large (even though it is not reported in the paper). For four
galaxies, _R_ _out_ values from the literature are considerably higher
than our measurements (∼ 2 − 6 times higher). For three of these
galaxies, the difference is due to the different definition of _R_ _out_ as
the maximum radius at which the outflow is detected (see _R_ _max_
definition in Pereira-Santaella et al. 2018). For the other target
(20100-4156), the difference could be due to the different spatial
resolution (1.5 arcsec vs. 0.2 arcsec). For Arp 220 instead _R_ _out_
from the literature is smaller than our measurement; also in this
case the difference could be due to the different spatial resolution (0.09 arcsec vs. 1.0 arcsec). The _M_ _out_ values agree within
a factor of 2.5, with some of our values being smaller and other
larger than the values from Lutz et al. (2020). Since _M_ [˙] _out_ is proportional to _v_ _out_ and _R_ _out_ [−][1], the differences in _R_ _out_ and _v_ _out_ tend
to balance each other and lead to similar _M_ [˙] _out_ (within a factor of
3).


4.6.2. Comparison with Fluetsch et al. (2019)


We also compared the _M_ _out_ and _M_ [˙] _out_ of our sample with the
values reported by Fluetsch et al. (2019) for a sample of 45 local ( _z_ < 0.2) star-forming galaxies with CO(1-0), CO(2-1), or
CO(3-2) ALMA observations. Fluetsch et al. (2019) used a different method to estimate the outflow mass: they measured the
outflow flux by fitting the line profile with two Gaussians, one
for the core of the line and one broad component for the outflow,
and they considered the total flux of the broad component as the
outflow flux. We expect that the outflow fluxes measured in this
way will be higher than the ones measured with our method,
since in addition to the flux in the wings, they are also considering the low-velocity emission of the broad component as part
of the outflow. They measured the outflow velocity using Eq. 8.
They fitted a 2D-Gaussian profile to the wing maps and used
the beam-deconvolved major axis (FWHM) divided by two as
the radius of the outflow. Compared to our methodology, they
did not include the distance between the centroids of the blueshifted and red-shifted emission in the calculation of _R_ _out_, thus
their _R_ _out_ estimates are expected to be smaller.
Figure 9 shows the comparison of the outflow parameters
derived by Fluetsch et al. (2019) with our results for the five
sources in common between the two samples. Their _v_ _out_ tend to
be higher than ours (maximum by factor of 1.7), while their _R_ _out_
tend to be smaller (maximum by a factor of 1/4) . The largest difference is in the outflow masses, that are larger by up to a factor
of 16 (1.2 dex). This difference can be attributed to the different method used to estimate the flux belonging to the outflowing
gas. This difference in _M_ _out_ propagates to the _M_ [˙] _out_ .
Since the overlap between the two samples is small, we decide to also compare the outflow properties of the two samples
at the same IR luminosity. Figure 10 shows _M_ _out_ and _M_ [˙] _out_ as a
function of IR luminosity for the Fluetsch et al. (2019) sample
and our sample. The diamond symbols with red borders show
the average values of the two samples for different bins of IR lu

Article number, page 13 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



2.5


2.0


1.5


1.0


0.5


0.0


|Col1|Col2|Col3|
|---|---|---|
||||
|||Rout(Lutz)/Rout(this work)|
||||



250 300 350 400 450 500
v out [km s [−][1] ] (this work)



0 1 2 3 4
M out [10 [8] M ⊙ ] (this work)



3.0


2.5


2.0


1.5


1.0


0.5



6


5


4


3


2


1



7


6


5


4


3


2


1


0



0

0.0 0.2 0.4 0.6 0.8
R out [kpc] (this work)



0.0

0 50 100 150 200 250 300
˙M out [M ⊙ yr [−][1] ] (this work)



Fig. 8: Comparison of outflow parameters measured in this work with values reported in Lutz et al. (2020). From left to right:
outflow velocity, outflow radius, outflow mass and mass outflow rate. The dashed line marks the ratio of 1. Even though there are
differences in outflow velocities and radii, the mass outflow rates agree within a factor of 3.



minosity (with bin width of 0.5 dex). For the same IR luminosity
(in the range log˙ _L_ _IR_ / _L_ ⊙ = 12.0 − 12.5), their average _M_ _out_ and
_M_ _out_ are ∼ 0.6 − 0.8 dex higher than our measurements (factor
of ×4 − 6).
Given the different methodology used to measure these parameters, the difference is not surprising. As discussed in Section 4.5.2, this comparison highlights the large effect that the
choice of methodology can have on the measured outflow parameters. The approach used by Fluetsch et al. (2019) assumes
that most of the outflow flux is at low projected velocity. Based
on simulations of biconical outflows (e.g. Bae & Woo 2016), this
scenario is possible when the outflow is oriented in a direction
close to the plane of the sky, or if the outflow has low velocities.
In general, this method would tend to over-estimate the outflow
mass and it suffers from the degeneracy of the fit with multiple
Guassian components. With our method on the other hand, we
could be missing the outflow contribution at the low projected
velocities, thus, we may be underestimating the outflow mass.


_4.7._ _Analysis of the OH 119_ µ _m_ _spectra_


Other lines that are often used as tracer of molecular outflows
are the OH (hydroxyl) FIR lines (e.g. Fischer et al. 2010; Sturm
et al. 2011; Spoon et al. 2013; Veilleux et al. 2013; GonzálezAlfonso et al. 2014; Stone et al. 2016; González-Alfonso et al.
2017). We compare the outflow parameters derived from CO(21) with the ones derived from the OH 119µm doublet, which
is the strongest of the OH ground-state lines (e.g. GonzálezAlfonso et al. 2017). We collect archival _Herschel_ /PACS spectra of the OH 119µm doublet transition (hereafter OH) for
22/25 of our ULIRGs systems (no data available for 000910738, 10190+1322, and 16156+0146). The majority of the spectra (20/22) were published in Veilleux et al. (2013), Spoon et al.
(2013), and González-Alfonso et al. (2017); 11095-0238 and
13451+1232 are not presented in these works but were found
in the _Herschel_ archive.

We extract the spectra from the central 9.4 [′′] × 9.4 [′′] spaxel
and apply the point source aperture correction. We fit the OH
spectra to derive the velocity of the outflow. In particular, we
want to compare the velocity ranges where the OH outflow is
detected with the ones of the CO outflow. Outflow parameters
were derived by Veilleux et al. (2013) for 14 of the ULIRGs in
our sample, but we repeat the analysis in order to obtain consistent parameters for the full sample. We set the zero velocity
of the OH spectra based on the redshift of CO (see Table 1), so
that we can directly compare the outflow velocities of the two

tracers.


Article number, page 14 of 76



We fit the line profile following the method used by Veilleux
et al. (2013), and we check that our derived parameters are consistent with their results. We first perform a linear fit of the continuum around the OH line and normalise the spectra to the continuum level. The OH doublet can appear in absorption (11/22),
emission (4/22) or as P-Cygni profile (7/22). The P-Cygni profile is considered a clear indication of the presence of an outflow
(e.g. Prochaska et al. 2011; Fischer et al. 2010; Sturm et al.
2011; González-Alfonso et al. 2012, 2013; Veilleux et al. 2013).
In our sample, emission and P-Cygni profiles are more common
in AGN (73%) than in SB dominated nuclei, which is consistent
with previous findings (Veilleux et al. 2013; Stone et al. 2016;
Runco et al. 2020).
For the absorption profiles, we fit a model with two Gaussians (one for the systemic and one for the outflow) for each line
of the OH doublet. The separation between the two lines of the
Λ-doublet is fixed to 0.208 µm (in rest-frame) and the amplitude
and width of the two lines were tied to be the same in each component. We convolve our model with the _Herschel_ /PACS instrumental resolution (FWHM∼ 270 km s [−][1], Veilleux et al. 2013),
to recover the intrinsic shape of the line. For profiles in emission,
we fit a model with two Gaussians (one for the systemic and one
for the outflow component) in emission for each OH line. For
the P-Cygni profiles, we consider one component in absorption
and one in emission for each line. Adding more components is
not possible due to parameter degeneracy (Veilleux et al. 2013).
We add as an additional constraint that the model absorption can
not be deeper than the observed absorption (similar to Veilleux
et al. 2013), to avoid a fitting result with unrealistically large amplitude of the emission and absorption components that cancel
each other out.

We use the best-fit model to derive the characteristic velocity of the emission and absorption profiles, separately. For the
absorption components, _v_ 50, _v_ 84 and _v_ 98 are the velocities corresponding to the 50th, 84th and 98th percentile of the absorption line profile, i.e. the velocities above which 50%, 84%, and
98% of the absorption takes place. Similarly, for the emission
components, _v_ 50, _v_ 84 and _v_ 98 are the velocities corresponding to
the 50th, 84th and 98th percentile of the emission line profile.
Veilleux et al. (2013) consider _v_ 84 to be a more robust estimate
of the outflow velocity compared to the ‘maximum outflow velocity’. We use _v_ 98 as an estimate of the maximum outflow velocity, keeping in mind that it may be more susceptible to noise
variation than _v_ 84 .
We apply a Monte Carlo (MC) approach to estimate the uncertainty on the derived parameters. We estimate the noise level
on a region of the continuum away from the line (excluding also
the region of the CH [+] (3-2) and [18] OH 120µm lines), then we add

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs


|Col1|1.6<br>work)<br>1.4<br>1.2 is|Col3|
|---|---|---|
||00<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>Rout(Fl¨utsch)/Rout(th|00<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>Rout(Fl¨utsch)/Rout(th|
||00<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>Rout(Fl¨utsch)/Rout(th||



0.5 1.0 1.5 2.0 2.5 3.0
M out [10 [8] M ⊙ ] (this work)



14


12


10



1.5


1.0


0.5


0.0



250 300 350 400 450 500
v out [km s [−][1] ] (this work)



0.0 0.2 0.4 0.6 0.8
R out [kpc] (this work)



16


14


12


10


8


6


4


2


0



8


6


4


2


0

0 50 100 150 200 250 300
˙M out [M ⊙ yr [−][1] ] (this work)



Fig. 9: Comparison of outflow parameters measured in this work with values reported in Fluetsch et al. (2019).From left to right:
outflow velocity, outflow radius, outflow mass and mass outflow rate. Differences in _M_ _out_ and _M_ [˙] _out_ can be up to a factor of 16.



10.0


9.5


9.0


8.5


8.0


7.5


7.0


6.5


6.0





3.5


3.0


2.5


2.0


1.5


1.0


0.5


0.0


0.5





9.5 10.0 10.5 11.0 11.5 12.0 12.5 13.0
logL IR [L ⊙ ]



9.5 10.0 10.5 11.0 11.5 12.0 12.5 13.0
logL IR [L ⊙ ]



Fig. 10: Comparison of the outflow mass and mass outflow rate as a function of IR luminosity for our sample and the sample from
Fluetsch et al. (2019) (purple triangles). The red symbols show the average values (considering only the detections) in bins of log _L_ _IR_
for the Fluetsch et al. (2019) sample (triangles) and the PUMA sample (circles). The sources in common between the two samples
are highlighted with black contours. Due to the different methods, the _M_ _out_ and _M_ [˙] _out_ values estimated by Fluetsch et al. (2019) are
higher by a factor of ×4 − 6 compared with our measurements at the same infrared luminosity


.



random Gaussian noise, proportional to the noise level, to the
best-fit model and we run the line fitting on this artificial spectrum. We repeat this procedure 50 times and we use the 16th and
84th percentiles of the distribution of best-fit parameters to estimate the 1σ uncertainties on the derived parameters. The 50
MC realisations are shown as orange curves on Figure 11. The
velocities derived from the OH profiles are shown in Table 5.
The properties of molecular outflows derived from OH will be
discussed and compared with those derived from the CO tracer
in Sec. 5.4.


**5.** **Results**


_5.1._ _Mean outflow properties_


Here we summarise the ranges of outflow properties of our sample and their average values, corrected for inclination as described in Sec. 4.5.1. We measure projected outflow velocities
of ∼ 260 − 490 km s [−][1], with a mean outflow velocity (corrected
for inclination) of 485±16 km s [−][1] . Outflow radii are in the range
0.17-0.94 kpc and the mean inclination-corrected outflow radius
is 1.1±0.1 kpc. The outflow masses are between 1−35×10 [7] M ⊙,
with an average of (10±2)×10 [7] M ⊙ . These outflow masses corresponds to 0.2-6.5% of the total molecular gas masses. The mass
outflow rates are in the range 6 − 302 M ⊙ yr [−][1], with an average
outflow rate of 78 ± 16 M ⊙ yr [−][1] . The ranges and averages of



the outflow parameters measured in this work are summarised in
Table 6.

As a comparison, Ramos Almeida et al. (2022) find molecular gas mass outflow rate _M_ [˙] _out_ = 8 − 16 M ⊙ yr [−][1] in a sample of
nearby type 2 quasars (log˙ _L_ _AGN_ /[erg s [−][1] ] = 45.7 − 46.3). Lower
_M_ _out_ = 0.3 − 5 M ⊙ yr [−][1] have been measured in lower luminosity (log _L_ _AGN_ /[erg s [−][1] ] = 43.2 − 44.2) Seyfert galaxies (AlonsoHerrero et al. 2019; Domínguez-Fernández et al. 2020; GarcíaBernete et al. 2021). Higher molecular gas mass outflow rates
( _M_ [˙] _out_ = 60 − 400 M ⊙ yr [−][1] ) have been measured in ULIRGs hosting an AGN (Feruglio et al. 2010; Cicone et al. 2014). We note
that, as discussed in Sec. 4.6, the method used to derive the mass
outflow rates can introduce systematic differences (up to factor
of ∼ 10) between different samples.
We also compare our measurements with the properties of
the ionised outflows measured by Arribas et al. (2014) for a
sample of nearby U/LIRGs. For ULIRGs, they find maximum
outflow velocities in the range 100-1000 km s [−][1], with a mean
393 ± 38 km s [−][1] and mass outflow rates in the range 1 − 100 M ⊙
yr [−][1] (from Fig. 13 in the paper), with an average 38 M ⊙ yr [−][1] .
The average _M_ [˙] _out_ of the ionised gas is about a factor of 2 smaller
than the one of the molecular phase. For U/LIRGs, they find outflow masses in the range 0.14 − 28 × 10 [7] M ⊙, with a average of
6.7 × 10 [7] M ⊙, similar to the masses of the molecular phase.
We find molecular outflow dynamical times ( _t_ _dyn_ = _R_ _out_ / _v_ _out_ )
in the range 0.45 − 2.77 Myr. The mean _t_ _dyn_, based on the
mean observed _R_ _out_ and _v_ _out_, is 1.37 Myr, assuming a aver

Article number, page 15 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv


Table 5: Velocities derived from the OH 119µm profiles.


IRAS name _v_ 50 (abs) _v_ 84 (abs) _v_ 98 (abs) _v_ 50 (em) _v_ 84 (em) _v_ 98 (em)

[km s [−][1] ] [km s [−][1] ] [km s [−][1] ] [km s [−][1] ] [km s [−][1] ] [km s [−][1] ]
(1) (2) (3) (4) (5) (6) (7)

00091-0738 ~~[⋆]~~           -           -           -           -           -           
00188-0856 -330±29 -774±69 -1186±136           -           -           
00509+1225          -          -          - 120±33 262±85 404±194

01572+0009          -          -          - 88±139 155±209 188±318

05189-2524 -306±84 -543±72 -781±105 145±23 316±22 489±33

07251-0248 -127±20 -347±22 -475±126           -           -           
09022-3615 -139±36 -270±28 -398±72 214±11 342±14 472±22
10190+1322 [⋆]          -          -          -          -          -          
11095-0238           -           -           - 206±163 344±40 413±110

12071-0444 -249±17 -454±30 -694±43 194±8 296±12 398±17

12112+0305 21±12 -76±27 -207±48 341±263 503±327 664±405

13120-5453 -253±16 -586±18 -850±35           -           -           
13451+1232          -          -          - -51±35 155±123 360±274

14348-1447 -245±34 -560±40 -917±68 154±11 300±14 446±23

14378-3651 -296±27 -650±39 -1007±58 189±15 319±14 478±20

15327+2340 -28±0 -194±0 -359±13          -          -          
16090-0139 -36±25 -410±43 -683±91           -           -           16156+0146 [⋆]          -          -          -          -          -          
17208-0014 50±10 -99±15 -466±94           -           -           
19297-0406 -121±39 -500±84 -879±199           -           -           
19542+1110 -302±50 -480±96 -622±157 267±72 302±114 373±168

20087-0308 48±19 -160±24 -403±52           -           -           
20100-4156 -393±39 -985±73 -1539±145           -           -           
20414-1651 17±0 -53±16 -88±85           -           -           
22491-1808 88±20 25±55 -8±196           -           -           

**Notes.** (1) IRAS name. (2), (3) and (4): 50th, 84th and 98th percentile velocities derived from the absorption profile (when present). (5), (6) and
(7): 50th, 84th and 98th percentile velocities derived from the emission profile (when present). [⋆] : OH 119µm spectra not available for 00091-0738,
10190+1322, and 16156+0146.



Table 6: Mean cold molecular outflow properties in ULIRGs.


_v_ _out_ _R_ _out_ _M_ _out_ _M_ ˙ _out_

[km s [−][1] ] [kpc] [10 [7] M ⊙ ] [M ⊙ yr [−][1] ]

mean: 485 ± 16 1.07 ± 0.08 10 ± 2 78 ± 16
range: 260 − 490 [⋆] 0.26 − 0.94 [⋆] 1 − 35 6 − 302


**Notes.** [⋆] : Not corrected for inclination.


age inclination correction of unity (Cicone et al. 2015). This
is similar to the outflow dynamical times 0.63-2.51 Myr reported in Pereira-Santaella et al. (2018). The outflow depletion times ( _t_ _dep_ = _M_ ( _H_ 2 ) _tot_ / _M_ [˙] _out_ ) in our sample are in the
range 15 − 644 Myr, with a median of 75 Myr. These are
a bit longer than the values reported for ULIRGs in PereiraSantaella et al. (2018) (15 − 80 Myr) and Cicone et al. (2015)
(1.2 − 50 Myr). For comparison, the star-formation depletion
times ( _t_ _dep_ = _M_ ( _H_ 2 ) _tot_ / _S FR_ ) for targets with detected outflows
in our sample are in the range 9-77 Myr (median 27 Myr).


_5.2._ _Outflow characteristics for AGN/SB and_
_interacting/mergers_


5.2.1. Outflow detection rate and direction


In this Section, we present the statistics of the number of detected molecular outflows in our sample and we investigate
whether there is any dependency of the outflow detection rate


Article number, page 16 of 76



on the nuclear classification (AGN or SB) or on the merger stage
(advanced mergers or interacting systems).
The top panel of Figure 12 shows the percentage of nuclei in
the sample belonging to each category: AGN, SB, merger (M),
interacting (I), and the mixed categories (merger AGN, merger
SB, interacting AGN, and interacting SB). For the interacting
systems, we consider only the nuclei with log _L_ _IR_ / _L_ ⊙ - 11.8
in this statistical analysis. As shown in Pereira-Santaella et al.
(2021), in most of our interacting systems the IR luminosity
is dominated by one nucleus, thus by applying this luminosity threshold, we discard the fainter nuclei (with log _L_ _IR_ / _L_ ⊙ =
10.3 − 11.7) which would not be classified as ULIRGs. In this
way, we avoid that the outflow detection rate in interacting nuclei
is artificially lower only because of the ‘secondary’ faint nuclei.
The second panel of Fig. 12 presents the percentage of outflow detections in each category. We detect an outflow, defined
as high-velocity (| _v_ | - 300 km s [−][1] ) CO(2-1) emission which
deviates from the main rotation, in 20/26 of the nuclei with
log _L_ _IR_ / _L_ ⊙ - 11.8 (77 ± 7% [1] ). The nuclei with outflow detections are equally divided between mergers and interacting systems. The percentage of detections in SB (93 ± 4%, 14/15) is
higher than in AGN (55 ± 14%, 6/11). A possible explanation
for this difference is related to the outflow inclination: if AGN
outflows are in the plane of the disk (contrary to SB outflows
that tend to be perpendicular to the disk), they are more difficult to detect with our method, but by modelling and subtract

1 The uncertainties on the percentages represent the 90% binomial
confidence intervals.

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



00188 − 0856













2000 1000 0 1000 2000 3000
velocity [km s [−][1] ]


13451 + 1232



















velocity [km s [−][1] ]


Fig. 11: Example of the fit of the OH 119µm doublet with absorption ( _upper_ ), emission ( _middle_ ) and P-Cygni ( _bottom_ ) profile. The velocity is relative to the blue component of the doublet
(at 119.233 µm) at the systemic velocity inferred from the CO(21) line. The best-fit model is shown in magenta, while the orange
models are the results of the 50 Monte Carlo realisations that illustrate the uncertainty of the fit. Solid lines show the model
convolved with the instrumental resolution, while dashed lines
indicate the intrinsic (deconvolved) model. Blue and red mark
the two components of the fit. The vertical dotted, dashed and
dot-dashed lines show the _v_ 50, _v_ 84 and _v_ 98 percentile velocities,
respectively, derived from the absorption (blue) and/or emission
(red) profiles. Grey dashed lines at ∼ 2000 km s [−][1] show the position of the [18] OH 120 µm doublet and the CH [+] (3-2) absorption
line.



ing the disk rotation, it may be possible to identify them. Ad
buried nuclei. This is in agreement with an evolutionary scenario
in which in a first merger phase the nuclei are more obscured and
produced outflows, which expel gas and dust from the nuclear

∼

thus it appear very compact and unresolved. This could explain
why we could not determine the outflow direction in many AGN.
We find that in six nuclei the outflow direction is nearly perpendicular (angle 90 ± 20 [◦] ) to the kinematic major axis. These
nuclei are 12112+0305 NE, 12112+0305 SW, 14348-1447 NE
(already presented in Pereira-Santaella et al. 2018), 10190+1322
E, 19542+1110 and 20100-4156 SE. All these nuclei are SB
dominated. This supports the idea that outflow powered by SB
tend to be perpendicular to the disk, while AGN outflow can have
any orientation (e.g. Pjanka et al. 2017). However, there are also
many SB nuclei (50 ± 13%) for which the outflow direction is
not perpendicular. This could be due to a hidden (deeply buried)
AGN that is powering the outflow, even though it is not detected
in the MIR or optical (see Pereira-Santaella et al. 2021). An alternative explanation is that in these SB the molecular gas is still
strongly disturbed and has not yet settled into a galactic plane,
and consequently also the path of least resistance is not well defined. We note that we measure the angle between outflow and
major kinematic axis projected in the plane of the sky. Thus,
there is the possibility that we measured a projected angle of 90 [◦]


Article number, page 17 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



for an outflow that is not perpendicular to the plane if we observe it from a particular orientation. However, for SB it is more
likely that the outflow escape from the path of least resistance
(perpendicular to the disk) than from any other direction, where
the outflow will encounter more material. The majority of the
nuclei with perpendicular outflow (5/6) are interacting systems.
Although the number statistics are small, this could be due to the
poorly defined disk rotation axis in some of the more advanced

mergers.
Our sample was selected to have a similar number of objects
in each category (AGN/SB, interacting/mergers), thus it does not
have the _L_ _IR_ distribution or AGN fraction of the general population of ULIRGs. We estimate the outflow detection fraction that
would be measured in a sample of ULIRGs with the same AGN
fraction as the local ULIRGs population. Veilleux et al. (2009)
study the AGN contribution in a representative sample of 74
ULIRGs from the IRAS 1 Jy Survey (Kim & Sanders 1998) and
find that 24% of their sample has an AGN contribution - 50%
in the MIR. We use this AGN fraction to correct our outflow detection statistics and we find that the expected outflow detection
fraction in local ULIRGs is 84% (compared to 77% measured in
our sample).


5.2.2. Outflow quantities


In this Section, we investigate whether there are differences in
the outflow properties depending on these categories. We calculate the mean outflow parameters ( _v_ _out_, _R_ _out_, _M_ _out_, _M_ [˙] _out_ ) for each
category and we compare it with the mean of the total sample.
We do not include upper limits in this comparison. Even though
there are small differences, the mean quantities in all categories
are consistent (within 2σ) with the sample mean (see Fig. 13).
Additionally, we compare the distribution of outflow properties for AGN vs. SB and mergers vs. interacting systems, taking
into account also the upper limits on the non-detections. Figure 13 shows the cumulative distribution functions (CDF) of the
outflow properties ( _v_ _out_, _R_ _out_, log _M_ _out_, log _M_ [˙] _out_, and log η =
log( _M_ [˙] _out_ / _S FR_ )) for the AGN and SB categories (upper) and
mergers and interacting (bottom) categories. To test whether two
samples have different distributions, we perform a Two Sample
test using the survival analysis package ASURV (Feigelson &
Nelson 1985) which allows us to take into account upper limits.
We find that the distributions of the outflow properties of AGN
and SB are not significantly different according to the Gehan’s,
Logrank and Peto-Prentice’s Two Sample Tests ( _p_ -value=0.20.7). Similarly, we do not find significant differences between
mergers and interacting systems ( _p_ -value=0.2-0.9).
We also consider the mean outflow rate normalised by the
total _L_ _IR_ (see Fig. 14), in order to remove the effect of the
correlation between _M_ [˙] _out_ and _L_ _IR_ (see Sec. 5.3). Also in this
case there are no significant differences in the average _M_ [˙] _out_ / _L_ _IR_
of˙ the different categories. The average for the total sample is
_M_ _out_ / _L_ _IR_ = (3.8 ± 0.6) × 10 [−][11] M ⊙ _yr_ [−][1] _L_ ⊙ [−][1] . In the right
panel, we also plot the average outflow rates normalised by AGN
luminosity˙ _M_ [˙] _out_ / _L_ _IR_, _AGN_ for the AGN categories. The ˙average
_M_ _out_ / _L_ _IR_, _AGN_ for AGN are ∼ 3 − 6 times higher than the _M_ _out_ / _L_ _IR_
for starbursts.


_5.3._ _Outflow properties and energetics_


In this section, we investigate the relation between the outflow
properties and the total infrared luminosity, as well as with the
SFR and AGN luminosity.


Article number, page 18 of 76



70













sample


outflow detection





perpendicular

not perp.

unclear



100


80


60


40


20


0


100


80


60


40


20



0

|AGN SB M I AGN M+SB AGN|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|AGN I+SB|Col16|Col17|Col18|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|M+<br>M<br>I+<br>outflo~~w~~ direction|I|I|I|I|
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|||||||||||||||||||
|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|AGN<br>SB<br>M<br>I<br>+AGN<br>M+SB<br>I+AGN|I+SB|I+SB|I+SB|I+SB|



Fig. 12: Outflow detection statistics for different categories:
AGN, starburst (SB), mergers (M, _d_ _nuclei_ < 1 kpc), interacting systems (I, _d_ _nuclei_ - 1 kpc), and mixed categories (mergers AGN, mergers SB, interacting AGN, interacting SB). _Upper_
_panel:_ fraction of individual galaxy nuclei in each category with
respect to the total sample. The scale on the right axis shows the
number of objects. _Middle_ _panel:_ outflow detections fractions.
The percentages have been calculated with respect to the total
number of nuclei in each category. _Lower panel:_ outflow orientation statistics divided in three groups: outflow projected orientation perpendicular to the kinematic major axis of the disk (angle 90 ± 20 [◦] ), outflow projected orientation non-perpendicular,
or orientation could not be determined. The percentages have
been calculated with respect to the number of outflow detection
in each category. Error bars in middle and lower panel show the
90% binomial confidence interval.


5.3.1. Outflow and AGN properties


In this section, we look at trends between the outflow properties and the AGN luminosity and AGN fraction. We calculate

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs





1


0.5



0

200 250 300 350 400 450 500

v out [km s [−][1] ]



6.5 7.0 7.5 8.0 8.5
logM out [M ⊙ ]


6.5 7.0 7.5 8.0 8.5
logM out [M ⊙ ]



0.0 0.5 1.0 1.5 2.0 2.5
log M [˙] out [M ⊙ yr [−][1] ]


0.0 0.5 1.0 1.5 2.0 2.5
log M [˙] out [M ⊙ yr [−][1] ]



1.6 1.2 0.8 0.4 0.0
log η = log(M [˙] out /SFR)


1.6 1.2 0.8 0.4 0.0
log η = log(M [˙] out /SFR)





1


0.5



0

200 250 300 350 400 450 500

v out [km s [−][1] ]



0.1 0.3 0.5 0.7 0.9
R out [kpc]


0.1 0.3 0.5 0.7 0.9
R out [kpc]



Fig. 13: Cumulative distribution function (CDF) of the outflow properties of AGN and starbursts (SB) ( _top_ ) and mergers (M) and
interacting (I) ( _bottom_ ). The solid lines show the CDFs for the outflow detections only, while the dashed lines show the CDFs
including upper limits (only for _M_ _out_, _M_ [˙] _out_ and η) . The shaded area mark the area between the CDFs with and without upper limits.
The square symbols show the average values for the outflow detections in the two categories, the points with arrows show the upper
limits (with arbitrary values on the y-axis). According to a survival analysis Two Sample test, the differences between AGN and SB
and between interacting and mergers, are not statistically significant.



3.0


2.5


2.0


1.5


1.0


0.5


0.0



3.0


2.5


2.0


1.5


1.0


0.5


0.0






|1e 10|Col2|
|---|---|
|||
|||



Fig. 14: _Left:_ Mean values of the ratio of _M_ [˙] _out_ and total _L_ _IR_ for
different categories: AGN, starbursts (SB), mergers (M), interacting (I), and the mix categories mergers AGN, mergers SB,
interacting AGN and interacting SB. The errorbars show the uncertainty on the mean. The grey diamond and horizontal band
shows the mean of the total sample and the corresponding uncertainty. _Right:_ For the AGN categories, mean ratios of _M_ [˙] _out_
and _L_ _IR_, _AGN_ .


the AGN luminosity ( _L_ _IR_, _AGN_ ) as the fraction of the total infrared luminosity _L_ _IR_ due to AGN, based on the MIR AGN
fraction (α _AGN_, see Perna et al. 2021). For the interacting systems, α _AGN_ is determined only for the IR brightest nucleus,
thus, for the second faint nucleus we cannot estimate _L_ _IR_, _AGN_
and _L_ _IR_, _S F_ . Cicone et al. (2014) reported a trend for the massloading factor (η = _M_ [˙] _out_ /SFR) to increase with AGN fraction
(α _AGN_ = _L_ _AGN_ / _L_ _bol_ ), while we do not find a correlation between
these two quantities in our sample (Spearmann rank correlation
coefficient for the detections _r_ = 0.27, _p_ -value=0.28), as it is
shown in Figure 15. The correlation found in Cicone et al. (2014)
is driven mostly by the objects with high AGN fraction (> 0.8),
which have η - 10 . Fluetsch et al. (2019) expand the Cicone
et al. (2014) sample and find that the correlation between η and
α _AGN_ is only evident for α _AGN_ - 0.7. They propose that the lack



of correlation for α _AGN_ < 0.7 could be due to i) the contribution
from star-formation to the mass outflow rate for small AGN fractions or ii) to the short timescale of AGN variability (10 − 10 [5] yr,
Gilli et al. 2000; Schawinski et al. 2015), compared to the outflow timescales (10 [6] yr). Since Cicone et al. (2014) included in
the study objects with known molecular outflows, it is possible
that they sample the upper end of the distribution of η at large
α _AGN_ . On the other hand, our sample was selected without a prior
knowledge of the presence of outflows. The difference could be
also due to the method used to estimate the AGN fraction. We
use α _AGN_ estimated from the MIR 30 µm to 15 µm flux ratio.
Cicone et al. (2014) estimate the AGN fraction using different
methods: from the 5-8 µ _m_ spectral range using the method from
Nardini et al. (2010), from a combination of MIR and FIR diagnostics as described in Veilleux et al. (2009), by taking the
fraction of _L_ _AGN_ (estimated from [OIII] or from the X-ray luminosity) and _L_ _bol_ . If we were to use the method from Nardini
et al. (2010), the α _AGN_ for our sample would be lower (< 0.7 for
all sources).


Cicone et al. (2014) also find a correlation between the
molecular mass outflow rate and the AGN luminosity. A similar correlation was also reported in Fiore et al. (2017), who expanded the sample used by _M_ ˙ _out_ as a function of _L_ _AGN_ Cicone et al.for our sample, (2014). Figuretogether 16with showsthe
sample from Cicone et al. (2014), Lutz et al. (2020), the nearby
(non-ULIRGs) AGN from Stuber et al. (2021), and the nearby
( _z_ < 0.13) type 2 AGN from Ramos Almeida et al. (2022).
Ramos Almeida et al. (2022) find that their sample has _M_ [˙] _out_
more than one order of magnitude below the relation derived
by Cicone et al. (2014) (dashed line on the Fig. 16). Our sample occupies the parameter space between the Ramos Almeida
et al. (2022) objects and the Cicone et al. (2014) relation. Ramos
Almeida et al. (2022) suggest that this scaling relation represents
the upper boundary of the _M_ [˙] _out_ versus AGN luminosity relation.
Our sample confirms that for the same AGN luminosity, ULIRGs
can have a wide range of _M_ [˙] _out_ . We note that most of the objects
in Cicone et al. (2014) were selected based on the presence of a


Article number, page 19 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



molecular outflow (detected in CO or OH), while for our sample
we do not apply this prior criterion. This may explain the fact
that the sources in their sample have the highest _M_ [˙] _out_ values for
a given AGN luminosity.


2.5



5.3.2. Outflow energetics





2.0


1.5


1.0


0.5


0.0


0.5


1.0


1.5

0.0 0.2 0.4 0.6 0.8 1.0
α AGN = L AGN /L bol


Fig. 15: Mass-loading factor (η = _M_ [˙] _out_ /SFR) versus AGN fraction (α _AGN_ ). Star symbols show the Cicone et al. (2014) sample
(scaled down by a factor of three to match our outflow geometry
definition). Symbols for the PUMA sample are as in Fig. 1.







|Col1|Cicone+14relation|Col3|
|---|---|---|
|0.0<br>0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>.|r: 0.43, p: 0.07<br> <br>Fiore + 17 relation<br>Cicone + 14<br>Ramos Almeida + 22<br>Stuber + 21<br>Lutz + 20||
|0.0<br>0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>.|||


43 44 45 46
logL AGN [erg s [−][1] ]


Fig. 16: Mass outflow rate versus AGN luminosity. Diamonds
symbols _M_ ˙ _out_ have been scaled down by a factor of three to match our out-show the sample from Cicone et al. (2014), for which
flow geometry definition. The sample of Ramos Almeida et al.
(2022) is shown with triangles. Horizontal lines for the Ramos
Almeida et al. (2022) sample indicate the position that they
would occupy if we were to use the _L_ _AGN_ derived from SED
fitting from Jarvis et al. (2019), instead of the one derived from
the [O iii] luminosity (see Ramos Almeida et al. 2022, for details). The Lutz et al. (2020) sample is shown with red pentagons.
For the Stuber et al. (2021) sample (stars), the AGN luminosities have been derived from the 14-195 keV X-ray luminosity.
Symbols for the PUMA sample are as in Fig. 1. The dashed and
dotted lines show the relations presented by Cicone et al. (2014)
and by Fiore et al. (2017), respectively, scaled down by a factor
of three to match our outflow geometry definition).


Article number, page 20 of 76



In Figure˙ 17 we show the outflow rate, momentum rate ( _P_ [˙] _out_ =
_M_ _out_ - _v_ _out_ ), and kinetic luminosity ( _L_ _out_ = [1] 2 _[M]_ [˙] _[out]_ [ ·] _[ v]_ _out_ [2] [) as a func-]

tion of SFR. The SFR has been estimated from the IR luminosity, using the Kennicutt & Evans (2012) relation (with Kroupa &
Weidner (2003) initial mass function (IMF)) after removing the
fraction of luminosity associated with the AGN (α _AGN_ ).
To increase the dynamic range of SFR, we include in this figure also the 20 galaxies with candidate outflows from the Physics
at High Angular resolution in Nearby GalaxieS (PHANGS [2] )
ALMA survey (Leroy et al. 2021a; Stuber et al. 2021).The
PHANGS-ALMA sample consists of 90 nearby ( _d_ < 24 Mpc)
star-forming galaxies (log sSFR/yr [−][1] - −11) with stellar masses
in the range 9.3 ≤ log _M_ ⋆ / _M_ ⊙ ≤ 11.1. Stuber et al. (2021) use
ALMA CO(2-1) observations with a resolution of ∼ 100 pc to
look for molecular outflows in their sample and they find 20
(22%) outflow candidates, of which 16 are classified as ‘secure’
candidates. Half of the candidates are classified as AGN hosts
based on Véron-Cetty & Véron (2010).
The outflow parameters of this sample have been measured
using a method comparable to ours. They integrated the total
flux within the defined outflow velocity range to derive the outflow mass and measure the flux-weighted outflow velocity. They
also measured flux-weighted outflow radii. Because of the limited S/N, we did not attempt to derive flux-weighted _R_ _out_ by
measuring the outflow radii in each channel, but the _R_ _out_ derived from the 2D Gaussian fit should be representative of the
radius where most of the flux is located. To convert the CO(2-1)
outflow flux to outflow mass, Stuber et al. (2021) use the conversion factor α _CO_ = 0.8 M ⊙ /(K km s [−][1] pc [2] ) (Bolatto et al. 2013b),
similar to our assumption of α _CO_ = 0.78 M ⊙ /(K km s [−][1] pc [2] ), and
_r_ 21 = 0.65 (Bolatto et al. 2013a; Leroy et al. 2013; den Brok et al.
2021; Leroy et al. 2021b) while we use the value of _r_ 21 = 0.91
measured in ULIRGs (Papadopoulos et al. 2012). The SFR for
this sample are derived by Leroy et al. (2021a) from the WISE
band 4 photometry, with a calibration consistent with Kennicutt
& Evans (2012), the one used for the PUMA targets. The molecular outflows detected in the PHANGS galaxies have weighted
velocities _v_ _out_ = 65 − 238 km s [−][1], _M_ _out_ = 0.35 − 102 × 10 [6] M ⊙
and _M_ [˙] _out_ = 0.15 − 21 M ⊙ yr [−][1] . These outflow parameters are
lower than the ones we measure for PUMA, as it is expected for
galaxies with lower SFR compared to ULIRGs.
The left panel of Figure 17 shows the relation between mass
outflow rate and SFR. The dashed lines indicate constant massloading factors (η = _M_ [˙] _out_ /SFR). The PUMA objects have η <
0.04 − 1. The PHANGS-ALMA galaxies have slightly higher
η = 0.15 − 4. The dispersion in _M_ [˙] _out_ for a given SFR is quite
high (∼ 1 dex). Mass-loading factors in local starburst galaxies
are typically lower than 2 − 3 (e.g. Bolatto et al. 2013b; Cicone
et al. 2014; Salak et al. 2016), thus, the outflows of the PUMA
sample are consistent with being powered by starburst. We note
that the nuclei classified as AGN through MIR or optical diagnostics (orange symbols) do not show higher mass-loading factors compared with the rest of the sample. For the PUMA sample, the vertical errorbars are probably more extended towards
higher values, given that with our method it is possible that we
are underestimating _M_ [˙] _out_ in some of the objects (see discussion
in Sec. 4.5.2).
In Figure 17 we also show the outflow momentum rate ( _P_ [˙] _out_ )
as a function of SFR. We follow Pereira-Santaella et al. (2018)
to calculate the total momentum injected by supernova explosions. We assume that the momentum per supernova is 1.3 × 10 [5]


2 http://www.phangs.org

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



M ⊙ km s [−][1] ×( _n_ 0 /100 cm [−][3] ) [−][0][.][17] (Kim & Ostriker 2015), where
_n_ 0 = 100 cm [−][3] is the electron density; and that the supernova
rate is 0.012×SFR (M ⊙ yr [−][1] ) for the adopted IMF (Leitherer
et al. 1999). Since all the PUMA galaxies have _P_ [˙] _out_ smaller than
the total momentum injected by supernovae (SNe, see dashed
line in the middle panel of Fig. 17), their outflow momentum
rate could be explained entirely by SNe.
The outflow kinetic luminosity is shown in the right panel
of Figure 17. The dashed lines show fractions of the energy
produced by SNe (1%, 10%, 100%). The kinetic energy injected by supernova explosions is calculated as _L_ _S Ne_ [erg s [−][1] ]=
9 × 10 [41] ×SFR [M ⊙ yr [−][1] ] (Leitherer et al. 1999), adapted for a
Kroupa (2001) IMF. For the PUMA ULIRGs, the outflow kinetic luminosity is 0.2 − 5.9% of the energy produced by SNe,
for the PHANGS-ALMA sample it is slightly lower (0.1−2.4%).
The linear fit to the two samples gives:


log _L_ _out_ [erg s [−][1] ] = (39.4±0.08)+(1.3±0.05) log _S FR_ [M ⊙ yr [−][1] ].

(10)


The slope is larger than one, meaning that, assuming that these
outflows are driven by SNe, the coupling efficiency between
ISM and SNe increases slightly with SFR. This slope is shallower than the value of 2 ± 0.2 found by Pereira-Santaella et al.
(2018) using a smaller sample (15 objects). The difference could
be partly explained by the different method used to derive the
outflow parameters in Pereira-Santaella et al. (2018), which obtained higher mass outflow rates for ULIRGs (12-400 M ⊙ yr [−][1] ).


5.3.3. Outflow launching mechanism


In this section we investigate the outflow launching mechanism.
In particular, we investigate whether the detected molecular outflows are momentum-driven or energy-driven. For momentumdriven outflows, the mass-loading factor (η = _M_ [˙] _out_ / _S FR_ ) is proportional to _v_ [−] _out_ [1] [, while for energy driven outflows][ η] [∝] _[v]_ [−] _out_ [2] [(e.g.]
Murray et al. 2005). It is possible to distinguish between the two
scenarios by looking at the slope of the relation between log η
and log _v_ _out_ :



In Figure 19, we show the SFR as a function of _v_ _out_ . There
is a strong positive correlation between these two quantities ( _r_ =
0.84, _p_ -value< 0.01).The best linear fit gives:


log _v_ _out_ ∝ (0.25 ± 0.01) · log _S FR_ . (12)


The slope of the relation is in agreement with the relation found
for the ionised gas by Arribas et al. (2014) (slope 0.24 ± 0.05)
and for neutral gas by Rupke et al. (2005b) (slope 0.21 ± 0.04). It
is also in agreement with the theoretical prediction from Heckman et al. (2000) of the relation between velocity and starburst
luminosity _v_ _max_ ∝ _L_ _bol_ [0][.][25] [.] [This] [relation] [is] [derived] [under] [the] [as-]
sumption that starbursts have a maximum characteristic surface
brightness (Lehnert & Heckman 1996; Meurer et al. 1997), and
therefore their bolometric luminosity is proportional to their radius squared. We note that these relations consider _v_ _max_, not the
mean outflow velocity. We cannot use _v_ _max_ in our analysis, because it is not available for the PHANGS sample and we consider it less robust than _v_ _out_ . Nonetheless, for the PUMA sample
we find a good correlation between _v_ _max_ and _v_ _out_ ( _r_ = 0.58, _p_ value< 0.01).
Using this relation, we can substitute log _S FR_ with 4·log _v_ _out_
in the expression of the mass-loading factor:



_M_ ˙ _out_
log η = log
� _S FR_



= log _M_ [˙] _out_ − log _S FR_
�



_M_ ˙ _out_
log η = log
� _S FR_



= α · log _v_ _out_ + _b_, (11)
�



= log _[v]_ _[out]_ [ ·] _[ M]_ _[out]_ − 4 · log _v_ _out_

_R_ _out_

= log _[M]_ _[out]_ − 3 · log _v_ _out_ . (13)

_R_ _out_


Substituting this in equation 11 gives:


log η = log _[M]_ _[out]_ − 3 · log _v_ _out_ = α · log _v_ _out_ + _b_ (14)

_R_ _out_


log _[M]_ _[out]_ = (α + 3) · log _v_ _out_ + _b_ . (15)

_R_ _out_


Thus, by looking at the relation between _M_ _out_ / _R_ _out_ and _v_ _out_, we
can derive the value of α. For the fit, we assume a systematic
error of 0.1 dex on log _v_ _out_ and 0.3 dex on log( _M_ _out_ / _R_ _out_ ). Figure 20 shows log( _M_ _out_ / _R_ _out_ ) as a function of log _v_ _out_ .
The best linear bisector fit relation has a slope of 2.61 ± 0.25,
which implies α = −0.39. The α = −1 scenario (momentumdriven) is within the 1σ uncertainty (see shaded area in Fig. 20),
while the α = −2 scenario does not agree with the fit. Therefore,
our analysis favours the momentum-driven scenario as the primary launching mechanism for molecular outflows in ULIRGs.
Previous works investigating the molecular outflows in ULIRGs
also reach this conclusion. Cicone et al. (2014) find α = −1.0 ±
0.5 for a sample of five pure starburst galaxies, in agreement with
the momentum-driven scenario. Pereira-Santaella et al. (2018)
find α = −0.3 ± 0.2 combining a sample U/LIRGs and lower
luminosity starbursts. We note that for this analysis we adopt a
different _r_ 21 value for the Stuber et al. (2021) sample ( _r_ 21 = 0.6)
and for the PUMA sample ( _r_ 21 = 0.91). If we were to use the
same value for both samples, the fit would agree even more with
the momentum-driven scenario.


5.3.4. Escape fractions


We estimate the average fraction of the outflowing gas that can
potentially escape from the gravitation potential of the galaxies.


Article number, page 21 of 76



where α and _b_ are the slope and intercept of the linear relation. In Figure 18 we show log η as a function of log _v_ _out_ for the
PUMA and PHANGS-ALMA samples. We fit a linear relation
between these two quantities using the Monte Carlo MarkovChain (MCMC) implementation PyStan [3] . The lightblue shaded
region shows the 1 σ uncertainty on the fit, obtained by sampling the posterior distribution. We assume a systematic error of
0.1 dex on _v_ _out_ and 0.3 dex on η. We also model the intrinsic
scatter of the relation and we assume that the noise is normal
distributed. We derive the best fit values and the corresponding
1σ uncertainties from the median and the 16th-84th percentiles,
respectively, of the marginalised posterior distributions of the parameters (more details on the fitting procedure can be found in
appendix B).
The best linear bisector fit gives a slope α = −1.43 ± 0.28
(σ _intr_ = 0.35). This slope is between the momentum-driven (α =
−1) and energy-driven (α = −2) value. From Fig. 18, we can see
that both slopes are included within the 1σ fit uncertainty (lightblue shaded area), and therefore we cannot distinguish between
the two options on the basis of this figure.


3
https://mc-stan.org/users/interfaces/pystan

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



44


43


42


41


40


39


38





9 10 logL IR 11, SF [L ⊙ ] 12 13



9 10 logL IR 11, SF [L ⊙ ] 12 13









37


36


35


34











33


32





0.5 0.0 0.5 1.0 1.5 2.0 2.5 3.0
log SFR [M ⊙ yr [−][1] ]





0.5 0.0 0.5 1.0 1.5 2.0 2.5 3.0
log SFR [M ⊙ yr [−][1] ]



Fig. 17: Mass outflow rate ( _left_ ), outflow momentum rate ( _middle_ ), and outflow kinetic luminosity ( _right_ ) as a function of SFR.
Lightblue and orange symbols indicate SB and AGN dominated nuclei, respectively. Circles indicate interacting systems and squares
indicate mergers from the PUMA sample (including nuclei with log _L_ _IR_ / _L_ ⊙ < 11.8). Stars show the PHANGS-ALMA targets from
Stuber et al. (2021). A representative errorbar is shown on the lower right. _Left panel_ : the black dotted-dashed lines show lines of
constant mass-loading factors (η= _M_ [˙] _out_ /SFR) of 0.1, 1 and 10. _Middle panel_ : the dashed line indicates the total momentum injected
by SNe as a function of SFR. The dotted line shows the _L_ _S FR_ / _c_ ratio, where _L_ _S FR_ is the IR luminosity for a given SFR derived
using the (Kennicutt & Evans 2012) relation. _Right panel:_ the lines show the 1%, 10% and 100% of the energy produced by SNe.
The lightblue lines in the three panels are the best linear fit to the data, with the shaded area indicating the 1σ uncertainty.



1.0


0.5


0.0


0.5


1.0





2.8


2.6











1.5


log v out [km s [−][1] ]


Fig. 18: Mass-loading factor versus outflow velocity for our sample (circles and square symbols) and the PHANGS-ALMA sample (stars). The lightblue line is the best linear bisector fit to the
data and the shaded areas indicates the 1σ uncertainty on the
fit with and without including the intrinsic scatter term (lighter
and darker colour, respectively). The blue dashed line shows the
predictions for a energy-driven outflow (α = −2) and the red
dotted-dashed line for a momentum-driven outflow (α = −1).


To estimate the escape fraction, we compare the outflow velocity with the escape velocity derived from a gravitational model
of the host galaxy, which is assumed to be a truncated isothermal sphere (e.g. Veilleux et al. 2005). We use equation (7) in
Arribas et al. (2014) to estimate the average escape velocity for
our sample at the average outflow radius _r_ = 1 kpc. Since estimates of the dynamical masses have been obtained by Perna
et al. (2022) only for a subset of our targets (eight objects), we
use the mean dynamical mass of the PUMA sample for our cal

Article number, page 22 of 76



2.4


2.2


2.0


1.8


1.6


0.5 0.0 0.5 1.0 1.5 2.0 2.5 3.0
log SFR [M ⊙ yr [−][1] ]


Fig. 19: Outflow velocity versus star-formation rate for our sample and the PHANGS-ALMA sample. The lightblue line is the
best linear fit to the data (slope: 0.25 ± 0.01); the 1σ uncertainties on the fit (with and without including the intrinsic scatter
term) are indicated with shaded areas (lighter and darker colour,
respectively). Symbols as in Fig. 17.


culation ⟨ _M_ _dyn_ ⟩ = 3.9 - 10 [10] M ⊙ . The dynamical masses have
been obtained from the modelling of the rotation of the ionised
gas (see Perna et al. 2022, for more details). As truncating radius
we assume two times the average effective radius ⟨ _R_ _e_ ⟩ = 2 kpc
(Perna et al. 2022). We assume that the outflow velocity only
has a radial component.With these assumptions, we estimate an
average escape velocity of _v_ _esc_ = 486 ± 40 km s [−][1] . We apply
an inclination correction to determine the average ‘observed’
_v_ _esc_, _obs_ = _v_ _esc_ /1.27 = 382 km s [−][1] (see Sec. 4.5).
Integrating the CO(2-1) emission at velocities higher than
_v_ _esc_, _obs_, we find that between 4 − 100% of the high-velocity gas

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



9.0


8.5


8.0


7.5


7.0


6.5





6.0

|y = (2 .61 ± 0 .25)x + (1 .45 ± 0 .63)<br>σintr. = 0 .41 ± 0 .06<br>r = 0 .75, p < 0 .01<br>α = −2<br>α = −1|Col2|
|---|---|
|6<br>1.8<br>2.0<br>2.2<br>2.4<br>2.6<br>2<br>log vout [km s−1]<br> Outﬂow mass divided by outﬂow radius (_Mout_/_Rout_) v|6<br>1.8<br>2.0<br>2.2<br>2.4<br>2.6<br>2<br>log vout [km s−1]<br> Outﬂow mass divided by outﬂow radius (_Mout_/_Rout_) v|



sus outflow velocity. The lightblue line is the best linear fit to
the data (slope=2.61 ± 0.25). The shaded area indicates the 1σ
uncertainty with and without including the intrinsic scatter term
(lighter and darker colour, respectively). The blue dashed line
shows the predictions for a energy-driven outflow (α = −2)
and the red dotted-dashed line for a momentum-driven outflow
(α = −1). Symbols as in Fig. 17.


will escape to the circumgalactic medium, with mean escape
fraction ⟨ _f_ _esc_ ⟩ = 45 ± 6%. This calculation depends on the assumption on the truncating radius. If we were to assume a larger
truncating radius, the escape velocity would increase, and the
escape fraction would decrease. For example, assuming a truncating radius larger by a factor of two ( _r_ _max_ = 4 × ⟨ _R_ _e_ ⟩ = 8 kpc),
_v_ _esc_ would increase by 13%. The escape outflow rates are in the
range 1-173 M ⊙ yr [−][1], with an average ⟨ _M_ [˙] _esc_ ⟩ = 40 ± 10 M ⊙
yr [−][1] . We find that interacting systems tend to have lower _f_ _esc_
than mergers (mean _f_ _esc_ = 33 ± 6% vs. _f_ _esc_ = 60 ± 10%).
We also compare the escape molecular gas mass ( _M_ ( _H_ 2 ) _esc_ )
with the total _M_ ( _H_ 2 ) of the galaxy (i.e. systemic and outflow).
The escape _M_ ( _H_ 2 ) _esc_ is < 5% of the total _M_ ( _H_ 2 ), with a mean of
1%. The mean depletion time based on the escape outflow rate
( _t_ _dep_ = _M_ ( _H_ 2 )/ _M_ [˙] _esc_ ) is 158 Myr (range 23 − 3715 Myr).


_5.4._ _OH vs. CO outflow properties_


In this section we compare the molecular outflow properties derived from the CO(2-1) emission line with the ones derived from
the OH 119 µm doublet, which is an alternative tracer used to
identify molecular outflows.
We compare the OH and CO profile of each PUMA target
in Figure 3, 4, and E.1. The OH absorption is produced in front
of the continuum emission, thus, we can assume that it is located in a region of the size of the continuum, which in most
cases is equal or smaller than the beam size (Pereira-Santaella
et al. 2021). Therefore, to have a fair comparison, we extract
the nuclear CO spectrum from a region equal to the beam size.
We also smooth the CO spectrum to the same spectral resolution of the OH spectrum. Qualitatively, it is evident from this
comparison that there are some cases where a clear blue-shifted
outflow is detected in OH but not in CO (e.g. 00188-0856),



and vice-versa (e.g. 09022-3615, 17208-0014). In Figure 21
we show four example cases: i) broad OH absorption reaching
high negative velocities ( _v_ < −1000 km s [−][1] ), but no CO blueshifted emission at _v_ < −300 km s [−][1] (00188-0856); ii) CO outflow, but no sign of outflow in OH (22491-1808); iii) outflow detected in both OH and CO, but OH outflow maximum velocity
( _v_ 98 = −1540 km s [−][1] ) much larger than CO outflow maximum
velocity _v_ _max_ = −800 km s [−][1] (20100-4156); iv) OH outflow maximum velocity ( _v_ 98 = −360 km s [−][1] ) smaller than CO outflow
maximum velocity _v_ _max_ = −600 km s [−][1] (15327+2340).
In Figure 22, we compare the OH and CO outflow velocities.
In the upper row, we compare the OH _v_ 98 velocity of the absorption profile with the ‘weighted’ outflow velocity ( _v_ _out_, _left_ )
and maximum outflow velocity ( _v_ _max_, _right_ ) of the blue-shifted
wing of the CO profile. We show the objects with OH absorption or P-Cygni profile, for a total of 20 nuclei. For 12112+0305
and 14348-1447, we show both nuclei, since a CO outflow is
detected around each nucleus and they have comparable continuum luminosity. For the other interacting systems, we consider
only the nucleus with the brightest continuum, since the second
nucleus does not have a CO outflow detection.
We identify three groups: i) targets with comparable OH
and CO outflow velocity, ii) targets with OH outflow velocity
larger than the ones from CO, and iii) targets with CO outflow velocity larger than the OH outflow velocity. In 13 targets, both | _v_ 98 ( _abs_ )(OH)| and | _v_ _max_ (CO)| are > 300 km s [−][1] . The
| _v_ 98 (abs)(OH)| values tend to be higher (on average by 170 km
s [−][1] ) than the | _v_ _max_ (CO)| values, but this is not surprising given
that _v_ 98 and _v_ _max_ are measured using different methods.
For 3/20 targets, | _v_ 98 ( _abs_ )(OH)| < 300 km s [−][1], thus, there
is no evidence of an outflow in the OH absorption profile, while
a CO outflow is detected. This difference may be due to a collimated outflow in CO. In this case, the associated OH will absorb
only a tiny fraction of the continuum behind the outflow and
thus it will be undetectable. In Figure 23 we compare the velocity difference | _v_ 98 ( _abs_ )(OH) − _v_ _max_ (CO)| with the CO outflow
radius _R_ _out_ . We find a weak anti-correlation between the _R_ _out_ and
the OH-CO velocity difference ( _r_ = −0.4, or _r_ = −0.3 if we exclude the point with _v_ _max_ (CO)=0 km s [−][1] ), meaning that for more
extended CO outflow, the CO velocity tend to be larger than the
OH velocity. This is consistent with the scenario explained before, where for an outflow extending to a larger distance from the
nucleus, a lower fraction of the outflowing gas may overlap with
the background continuum, making the OH absorption weaker
(Veilleux et al. 2020). Additionally, if the velocity of the outflow increases with distance from the nucleus, the part with the
highest velocity is more likely to not overlap with the continuum
and thus, will not be detected in the OH absorption. Indeed, a
radial velocity gradient of ∼ 1 km s [−][1] pc [−][1] has been detected in
the molecular outflows of two galaxies: in the nearby starburst
galaxy NGC 253 by Walter et al. (2017) and in the LIRG ESO
320-G030 by Pereira-Santaella et al. (2020).
For one target (00188-0856), the OH spectrum shows a clear
outflow signature with _v_ 98 ( _abs_ )(OH) ∼−1200 km s [−][1], but there
is no outflow signature in the CO spectrum. The case of 001880856 can potentially be explained with extreme environments:
if the ionisation fraction of the molecular gas is high, the abundance of CO would decrease while the abundance of OH remains
high (González-Alfonso et al. 2018). This could be mostly associated with the highest-velocity gas. Alternatively, this difference
may be explained by the geometry of the outflow.
Another factor that can explain part of the differences in outflow velocities is the difference in sensitivities of the CO and OH
observations. Thus, the observation of one tracer may be more


Article number, page 23 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv





|Col1|OH 188 −0856 1.0 1.1 ectrum 22491 −18|
|---|---|
||v50<br>v84<br>v98<br>0<br>500<br>1000<br>1500<br>ty [km s−1]<br>nuclear CO<br>0.8<br>0.9<br>1.0<br>norm. spe<br>1500<br>1000<br>500<br>0<br>velocity [km<br>0<br>5<br>10<br>15<br>I [mJy]<br>OH<br>00 −4156<br>1.0<br>1.1<br>um<br>15327+ 23|
|0.6<br>0.7<br>0.8<br>0.9<br>1.0<br>norm. spectr<br>0.5<br>1.0<br>1.5<br>2.0<br>2.5<br>3.0<br>I [mJy]|v50<br>v84<br>v98<br>nuclear CO<br>0.5<br>0.6<br>0.7<br>0.8<br>0.9<br>norm. spectr<br><br>2<br>4<br>6<br>8<br>10<br>12<br>I [mJy]|


0.0



1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]



0

2



1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]





nuclear CO





Fig. 21: Comparison of the OH 119 µm and CO(2-1) line profile. The CO(2-1) spectrum is extracted from a nuclear region corresponding to the ALMA beam size and is convolved to the resolution of the OH spectrum (FWHM∼ 270 km s [−][1] ). We identified four
different cases: i) OH absorption reaching high velocity (| _v_ | - 1000 km s [−][1] ), but no CO blue-shifted emission (00188-0856); ii)
CO outflow, but no sign of OH outflow (22491-1808); iii) outflow detected in both OH and CO, but OH outflow maximum velocity
( _v_ 98 ) larger than CO outflow maximum velocity (20100-4156); iv) OH outflow maximum velocity ( _v_ 98 ) smaller than CO outflow
maximum velocity (15327+2340).



sensitive to weak outflow signatures at high velocities than the
other.

We note that the AGN nuclei tend to have faster OH outflows than SB dominated nuclei. Indeed, all AGN nuclei have
| _v_ 98 (OH)| > 300 km s [−][1] . There is a positive correlation ( _r_ = 0.51)
between the outflow velocity difference | _v_ 98 (OH)- _v_ (CO)| and the
AGN fraction (see Fig. 23). Veilleux et al. (2013) find that AGNdominated nuclei (α _AGN_ - 0.5) tend to have more negative OH
outflow velocities than SB-dominated nuclei. Their interpretation of this result is that once a significant fraction of the material
has been pushed away from the nucleus by the outflow, the AGN
is more likely to be identifiable. At the same time, the central
high-velocity part of the outflow can be seen more easily.
To investigate the differences between the OH and CO outflow velocities, we consider the possibility that the presence
of a compact obscured nucleus (CON) could influence the OH
outflow velocities. Falstad et al. (2019) find that CONs with
the most luminous HCN-vib line lack signatures of high velocity outflows in the OH 119 µm absorption lines, even though
some of them have molecular outflows detected in the CO or
HCN emission lines. We apply the method described in GarcíaBernete et al. (2022) to identify CONs in our sample, based on
the ratios of the equivalent widths of different polycyclic aro

Article number, page 24 of 76



matic hydrocarbons (PAHs) features from the literature (see Table 1). We find that CONs do not occupy a specific region of
the _v_ 98 ( _abs_ )(OH) vs. _v_ _max_ (CO) diagram (see black circles in
Fig. 22). We find that 6/7 CONs have | _v_ 98 (abs)(OH)|> 300 km
s [−][1], a sign of molecular outflows.
In Figure 22, we also compared the velocities derived from
the OH emission ( _v_ 98 ( _em_ )) with the velocities of the red-shifted
CO outflow ( _v_ _out_ ( _r_ ) and _v_ _max_ ( _r_ )). Most targets have _v_ 98 ( _em_ ) 300 km s [−][1] . For these targets, _v_ 98 ( _em_ ) generally agree, within the
uncertainties, with the CO outflow velocities. The uncertainties
on OH velocities derived from the emission profiles tend to be
larger than the ones derived from the absorption, because the
emission features are weaker.

One possible caveat of this analysis is the fact that the OH
spectrum includes the nuclear region with a beam size ∼ 20
arcsec [4] . For the interacting systems, these include the two nuclei. To detect the OH absorption, it is necessary to have the
continuum emission in the background. In the majority of interacting cases, the ALMA continuum emission is dominated
by one nucleus ( - 80% of the total emission for all but two
cases, 11095-0238 (65%) and 14348-1447 (60%), see Table 7


4 http://herschel.esac.esa.int/Docs/PACS/html/pacs_om.html

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



1500


1200


900


600


300


0


700


600


500


400


300


200


100


0







1500


1200


900


600


300


0


700


600


500


400


300


200


100


0


|Col1|Col2|Col3|
|---|---|---|
|||CONs|
|300<br>0<br>vou|600<br>t(b) [km|1500<br>1200<br>900<br> /s] (CO)|
||||
||||
|0<br>100<br>200<br>300<br>400<br>500<br>600<br>700<br>vout(r) [km s−1] (CO)|0<br>100<br>200<br>300<br>400<br>500<br>600<br>700<br>vout(r) [km s−1] (CO)|0<br>100<br>200<br>300<br>400<br>500<br>600<br>700<br>vout(r) [km s−1] (CO)|


|ii)|i)|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|**ii)**|||||||
||||||**iii)**|**iii)**|
|9<br>600<br>300<br>0<br>vmax(b) [km|9<br>600<br>300<br>0<br>vmax(b) [km|9<br>600<br>300<br>0<br>vmax(b) [km|9<br>600<br>300<br>0<br>vmax(b) [km|15<br>1200<br>00<br>  s−1] (CO)|15<br>1200<br>00<br>  s−1] (CO)|00|
||||||||
||||||||
|0<br>100<br>200<br>300<br>400<br>500<br>600<br>700<br>vmax(r) [km s−1] (CO)|0<br>100<br>200<br>300<br>400<br>500<br>600<br>700<br>vmax(r) [km s−1] (CO)|0<br>100<br>200<br>300<br>400<br>500<br>600<br>700<br>vmax(r) [km s−1] (CO)|0<br>100<br>200<br>300<br>400<br>500<br>600<br>700<br>vmax(r) [km s−1] (CO)|0<br>100<br>200<br>300<br>400<br>500<br>600<br>700<br>vmax(r) [km s−1] (CO)|0<br>100<br>200<br>300<br>400<br>500<br>600<br>700<br>vmax(r) [km s−1] (CO)|0<br>100<br>200<br>300<br>400<br>500<br>600<br>700<br>vmax(r) [km s−1] (CO)|



Fig. 22: Comparison of the outflow velocities of OH and CO. _Upper row_ : _v_ 98 derived from the OH absorption profile compared with
the mean ( _v_ _out_ ( _b_ ), _left_ ) and maximum ( _v_ _max_ ( _b_ ), _right_ ) velocities of the CO blue-shifted wing. The background colours highlight the
three regions described in section 5.4: i) targets with _v_ 98 similar to _v_ _max_ ( _b_ ), ii) targets with _v_ 98 - _v_ _max_ ( _b_ ), and iii) targets _v_ 84 < _v_ _max_ ( _b_ ).
_Lower row_ : _v_ 98 derived from the OH emission profile compared with the mean ( _v_ _out_ ( _r_ ), _left_ ) and maximum ( _v_ _max_ ( _r_ ), _right_ ) velocities
of the CO red-shifted wing. The blue lines mark the outflow detection threshold of | _v_ | - 300 km s [−][1] . Black circles mark targets
classified as compact obscured nuclei (CONs). Colour-code as in Fig. 1.



1500


1000


500


0


500





1500


1000


500


0


500







1000

0.0 0.2 0.4 0.6 0.8 1.0
R out [kpc] (CO)



1000

0.10.0 0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8


α AGN



Fig. 23: Comparison of the difference between the outflow velocities of OH ( _v_ 98 ) and CO ( _v_ _max_ ) with the CO outflow radius _R_ _out_
( _left_ ) and the AGN fraction α _AGN_ ( _right_ ). Black circles mark targets classified as compact obscured nuclei (CONs). Colour-code
as in Fig. 1.


in Pereira-Santaella et al. 2021), thus we can associate the OH
absorption to the nucleus with the brightest continuum emission.



**6.** **Discussion**


In our sample, we find a lower molecular outflow detection rate
in AGN (55 ± 14%) than in SB (93 ± 4%), for the nuclei with
log _L_ _IR_ - 11.8 _L_ ⊙ (see Sec. 5.2). This finding is in contrast with
the result of Stuber et al. (2021), who find higher molecular outflow detection rate in AGN (53%) compared to non-AGN (17%)
in main-sequence galaxies from the PHANGS sample. A possible explanation is that the situation in ULIRGs is different than
in main-sequence galaxies: in ULIRGs, SB-driven outflows are
stronger and may be easier to detect than AGN-driven outflows.
In main-sequence galaxies on the other hand, outflows driven by
star-formation are weaker, and the AGN-outflows are more important.

Other than the detection rate, we do not find significant differences in the outflow properties ( _v_ _out_, _R_ _out_, _M_ _out_, _M_ [˙] _out_ ) in AGN
and SB in the PUMA sample. Thus, molecular outflow in AGNdominated nuclei seem to be as powerful as SB-driven outflows,
contrary to what was found in previous works (Cicone et al.
2014; Fluetsch et al. 2019). Cicone et al. (2014) and Fiore et al.
(2017) reported a positive correlation between _M_ [˙] _out_ and AGN
luminosity, while in the PUMA sample we do not see this correlation, in agreement with the findings of Ramos Almeida et al.
(2022). The previous relations maybe trace the most efficient
coupling between AGN and molecular gas, so that the objects


Article number, page 25 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



with the most extreme outflows follow those relations. This implies that there are other factors that set the mass outflow rate
other than the AGN luminosity, as for example the geometry
of the outflow and the coupling between the outflow and the
CO disk, the efficiency of the energy/momentum transfer between the AGN and the molecular gas, or the distribution of the
gas around the AGN. Additionally, starbursts could contribute to
powering the molecular outflows even in AGN-dominated nuclei.
In our sample, we find outflow dynamical times 0.5-2.8 Myr
(see Sec. 5.1). These dynamical times are significantly shorter
than the expected age of the star-formation burst in ULIRGs
(∼ 60 − 100 Myr, Rodríguez Zaurín et al. 2010), the deple
−
tion times of star-formation (10 100 Myr for our sample) or the
outflow depletion times (∼ 10 − 700 Myr, Cicone et al. 2015;
Pereira-Santaella et al. 2018). These short dynamical times of
the molecular outflows may be due to the survival time of the
molecular gas in the hot outflow environment (e.g. Decataldo
et al. 2017). An alternative explanation may be related to the
geometry of the outflow. If the outflow has a bi-conical geometry, the area of the outflow increases with the squared of the
radial distance from the nucleus ( _r_ [2] ). Thus, the column density
of the outflow decreases with radius, making the emission fainter
and more difficult to detect at large radii (Pereira-Santaella et al.
2018).
In our sample, we find that between 4-100% of the outflow
gas could escape from the gravitational potential of the galaxies into the circumgalactic medium (see Sec. 5.3.4). However,
this represents only 1-5% of the total molecular gas reservoir of
the galaxies. Thus, it is unlikely that these outflows are able to
impact star-formation by removing gas from the molecular gas
reservoir.


**7.** **Summary and conclusions**


In this work, we present ALMA CO(2-1) observations of 25
nearby ( _z_ < 0.165) ULIRG systems (38 individual nuclei) with a
resolution of ∼ 400 pc. We have used these observations to study
their molecular outflow properties. The main results of this work
are as follows:


1. We detect molecular outflows in 20/26 (77%) nuclei with
log _L_ _IR_ / _L_ ⊙   - 11.8. The molecular outflows have an average outflow velocity 485 ± 16 km s [−][1], outflow masses
1 − 35 × 10 [7] M ⊙, mass outflow rates˙ _M_ [˙] _out_ = 6 − 300 M ⊙ yr [−][1],
and mass-loading factors η = _M_ _out_ / _S FR_ = 0.1 − 1. The
majority of the outflows (18/20) are spatially resolved
with radii of 0.2 − 0.9 kpc and have short dynamical times
( _t_ _dyn_ = _R_ _out_ / _v_ _out_ ) in the range 0.5 − 2.8 Myr. We estimate the
average escape velocity for our sample _v_ _esc_ = 486 ± 40 km
s [−][1] . We find that, on average, 45 ± 6% of the high-velocity
gas will escape to the circumgalactic medium, which
represents less than 5% of the total molecular gas mass of
the systems (see Sec. 4.5.)


2. We find that the outflow detection rate is higher in SBs
(93 ± 4%, 14/15) than in AGN (55 ± 14%, 6/11) (see Sec. 5.2,
Fig. 12). A possible interpretation is that SB outflows tend
to be perpendicular to the disk, and thus they are easier
to detect, while AGN outflow can have any inclination
and/or can be more collimated. Indeed, we find that in 43%
(6/14) of the SB nuclei with outflow detection, the projected
position angle of the outflow is along the kinematic minor
axis, which suggests that these outflows are perpendicular


Article number, page 26 of 76



to the disk. This fraction is higher in early interacting
SBs (50%) than in advanced merger SBs (17%). Outflows
powered by AGN do not have a preferred orientation with
respect to the disk. We do not find any significant difference
in the mean outflow properties depending on the nuclear
engine (AGN versus SBs) or on the merger stage (advanced
mergers versus interacting systems) (see Fig. 14).


3. We find that our sample does not follow a tight _M_ [˙] _out_ versus
AGN luminosity relation, as reported in previous works
(see Fig. 16). For the same AGN luminosity, we find _M_ [˙] _out_
spanning up to 1.2 dex. This suggests that other factors may
contribute in determining _M_ [˙] _out_ in AGN ULIRGs, such as the
efficiency of the energy or momentum transfer between the
AGN and the molecular gas, the outflow geometry, or the
distribution of the gas around the AGN.


4. We investigate whether the molecular outflows are
momentum-driven or energy-driven, using also the
PHANGS-ALMA sample (Stuber et al. 2021) to extend the analysis to galaxies with lower SFR. Based on the
slope (α = −1.43 ± 028) of the mass-loading factor versus
outflow-velocity relation (Fig. 18), we cannot distinguish
between the momentum-driven (α = −1) and energy-driven
(α = −1) scenarios. However, using the relation between the
SFR and the outflow velocity (log _v_ _out_ ∝ 0.25 · log _S FR_ ), we
could derive the value of α by fitting the relation between
_M_ _out_ / _R_ _out_ and _v_ _out_ . From this analysis, we derived a slope
α = −0.39 ± 0.25, which is more consistent with the
momentum-driven than with the energy-driven scenario (see
Sec 5.3.3, Fig. 20).


5. We compare the outflow velocities derived from CO
( _v_ _out_ ) with the ones derived from OH outflow ( _v_ 98 ) (see
Sec. 5.4, Fig. 22). We find that for 13 targets, both the
CO and OH velocities are above 300 km s [−][1], which is a
sign of outflow, while in three targets the OH velocities
are considerably lower than _v_ _out_, and therefore there is no
evidence of outflows. This could be explained if the outflow
is highly collimated, and thus the outflowing OH covers
a small region of the background continuum. In one case
(00188-0856), the OH outflow velocity is very high, but no
outflow is detected in CO. This situation could be explained
by an extreme environment, where the high ionisation would
decrease the CO abundance more than the OH abundance,
by the outflow geometry or by the different sensitivities of
the OH and CO observations.


_Acknowledgements._ We thank the referee for the useful comments and
suggestions which helped improve this manuscript. We thank Cristina Ramos
Almeida for helpful discussion. We thank the staff of the European ALMA
ARC for the support with the self-calibration of the data. This research has been
funded by MDM-2017-0737 Unidad de Excelencia "María de Maeztu"-Centro
de Astrobiología (INTA-CSIC) by the Spanish Ministry of Science and
Innovation/State Agency of Research MCIN/AEI/ 10.13039/501100011033
and by "ERDF A way of making Europe". IL and MPS acknowledge
support from the Comunidad de Madrid through the Atracción de Talento
Investigador Grant 2018-T1/TIC-11035 and PID2019-105423GA-I00 funded
by MCIN/AEI/10.13039/501100011033. MP is supported by the Programa
Atracción de Talento de la Comunidad de Madrid via grant 2018-T2/TIC-11715.
MP and SA acknowledge support from the Spanish Ministerio de Economía y
Competitividad through the grant ESP2017-83197-Py and PID2019-106280GBI00. EG-A is a Research Associate at the Harvard-Smithsonian Center for
Astrophysics, and thanks the Spanish Ministerio de Economía y Competitividad
for support under projects ESP2017-86582-C4-1-R and PID2019-105552RBC41. AAH and SGB acknowledge grant PGC2018-094671-B-I00 funded by
MCIN/AEI/ 10.13039/501100011033 and by ERDF A way of making Europe.

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



SGB acknowledges support from the research project PID2019-106027GA-C44
of the Spanish Ministerio de Ciencia e Innovación. SAa gratefully acknowledges
support from an ERC Advanced Grant 789410, from the Swedish Research
Council and from the Knut and Alice Wallenberg Foundation (KAW). DR
acknowledges support from STFC through grant ST/S000488/1. This paper
makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00113.S,
ADS/JAO.ALMA#2015.1.00263.S, ADS/JAO.ALMA#2016.1.00170.S,
ADS/JAO.ALMA#2016.1.00777.S, ADS/JAO.ALMA#2018.1.00486.S, and
ADS/JAO.ALMA#2018.1.00699.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in
cooperation with the Republic of Chile. The Joint ALMA Observatory is
operated by ESO, AUI/NRAO and NAOJ. This research has made use of
the NASA/IPAC Extragalactic Database (NED) which is operated by the Jet
Propulsion Laboratory, California Institute of Technology, under contract
with the National Aeronautics and Space Administration. This research made
use of Astropy, a community-developed core Python package for Astronomy
(The Astropy Collaboration et al. 2013), `Matplotlib` (Hunter 2007), `NumPy`
(Van Der Walt et al. 2011). This research used the `TOPCAT` tool for catalogue
cross-matching (Taylor 2005) and the `Stan` interface for Python `PyStan` (Stan
Development Team 2018).


**References**


Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2015, A&A, 574, A85
Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2012, A&A, 537, A44
Alonso-Herrero, A., Esquej, P., Roche, P. F., et al. 2016, MNRAS, 455, 563
Alonso-Herrero, A., García-Burillo, S., Pereira-Santaella, M., et al. 2019, A&A,
628, A65
Arribas, S., Colina, L., Bellocchi, E., Maiolino, R., & Villar-Martín, M. 2014,
A&A, 568, A14
Bae, H.-J. & Woo, J.-H. 2016, ApJ, 828, 97
Barcos-Muñoz, L., Aalto, S., Thompson, T. A., et al. 2018, ApJ, 853, L28
Bellocchi, E., Arribas, S., Colina, L., & Miralles-Caballero, D. 2013, A&A, 557,
A59
Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2013a, Nature, 499, 450
Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013b, ARA&A, 51, 207
Brusa, M., Cresci, G., Daddi, E., et al. 2018, A&A, 612, A29
Carniani, S., Marconi, A., Maiolino, R., et al. 2015, A&A, 580, A102
Cazzoli, S., Arribas, S., Maiolino, R., & Colina, L. 2016, A&A, 590, A125
Chung, A., Yun, M. S., Naraynan, G., Heyer, M., & Erickson, N. R. 2011, ApJ,
732, L15
Cicone, C., Maiolino, R., Gallerani, S., et al. 2015, A&A, 574, A14
Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21
Condon, J. J. 1997, Publications of the Astronomical Society of the Pacific, 109,
166
Dasyra, K. M. & Combes, F. 2011, A&A, 533, L10
Dasyra, K. M. & Combes, F. 2012, A&A, 541, L7
Dasyra, K. M., Combes, F., Novak, G. S., et al. 2014, A&A, 565, A46
Decataldo, D., Ferrara, A., Pallottini, A., Gallerani, S., & Vallini, L. 2017, MNRAS, 471, 4476
den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221
Domínguez-Fernández, A. J., Alonso-Herrero, A., García-Burillo, S., et al. 2020,
A&A, 643, A127
Emonts, B. H. C., Colina, L., Piqueras-López, J., et al. 2017, A&A, 607, A116
Fabian, A. C. 2012, Annual Review of Astronomy and Astrophysics, 50, 455
Falstad, N., Hallqvist, F., Aalto, S., et al. 2019, A&A, 623, A29
Farrah, D., Afonso, J., Efstathiou, A., et al. 2003, MNRAS, 343, 585
Feigelson, E. D. & Nelson, P. I. 1985, Astrophysical Journal, 293, 192
Feruglio, C., Fiore, F., Carniani, S., et al. 2015, A&A, 583, A99
Feruglio, C., Maiolino, R., Piconcelli, E., et al. 2010, A&A, 518, L155
Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143
Fischer, J., Sturm, E., González-Alfonso, E., et al. 2010, A&A, 518, L41
Fluetsch, A., Maiolino, R., Carniani, S., et al. 2021, MNRAS, 505, 5753
Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, Monthly Notices of the
Royal Astronomical Society, 483, 4586
Förster Schreiber, N. M., Genzel, R., Newman, S. F., et al. 2014, ApJ, 787, 38
Gao, Y., Egusa, F., Liu, G., et al. 2021, ApJ, 913, 139
García-Bernete, I., Alonso-Herrero, A., García-Burillo, S., et al. 2021, A&A,
645, A21
García-Bernete, I., Rigopoulou, D., Aalto, S., et al. 2022, arXiv e-prints,
arXiv:2203.14795
García-Burillo, S., Combes, F., Usero, A., et al. 2015, A&A, 580, A35
Gelman, A., Carlin, J. B., Ster, H. S., et al. 2004, Chapman and Hall/CRC
Gilli, R., Maiolino, R., Marconi, A., et al. 2000, A&A, 355, 485
González-Alfonso, E., Fischer, J., Bruderer, S., et al. 2018, ApJ, 857, 66
González-Alfonso, E., Fischer, J., Bruderer, S., et al. 2013, A&A, 550, A25
González-Alfonso, E., Fischer, J., Graciá-Carpio, J., et al. 2014, A&A, 561, A27



González-Alfonso, E., Fischer, J., Graciá-Carpio, J., et al. 2012, A&A, 541, A4
González-Alfonso, E., Fischer, J., Spoon, H. W. W., et al. 2017, The Astrophysical Journal, 836, 11
Gowardhan, A., Spoon, H., Riechers, D. A., et al. 2018, ApJ, 859, 35
Heckman, T. M., Lehnert, M. D., Strickland, D. K., & Armus, L. 2000, ApJS,
129, 493
Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008, ApJS, 175, 356
Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90
Jarvis, M. E., Harrison, C. M., Thomson, A. P., et al. 2019, Monthly Notices of
the Royal Astronomical Society, 485, 2710
Kennicutt, R. C. & Evans, N. J. 2012, Annual Review of Astronomy and Astrophysics, 50, 531
Kim, C.-G. & Ostriker, E. C. 2015, ApJ, 802, 99
Kim, D. C. & Sanders, D. B. 1998, ApJS, 119, 41
Kroupa, P. 2001, MNRAS, 322, 231
Kroupa, P. & Weidner, C. 2003, ApJ, 598, 1076
Law, D. R., Steidel, C. C., Erb, D. K., et al. 2009, ApJ, 697, 2057
Lehnert, M. D. & Heckman, T. M. 1996, ApJ, 472, 546
Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, ApJS, 123, 3
Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021a, arXiv e-prints,
arXiv:2104.07739
Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021b, ApJS, 257, 43
Leroy, A. K., Walter, F., Sandstrom, K., et al. 2013, AJ, 146, 19
Lonsdale, C. J., Farrah, D., & Smith, H. E. 2006, in Astrophysics Update 2, ed.
J. W. Mason, 285
Lutz, D., Berta, S., Contursi, A., et al. 2016, A&A, 591, A136
Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134
Maiolino, R., Gallerani, S., Neri, R., et al. 2012, MNRAS, 425, L66
Meena, B., Crenshaw, D. M., Schmitt, H. R., et al. 2021, ApJ, 916, 31
Meurer, G. R., Heckman, T. M., Lehnert, M. D., Leitherer, C., & Lowenthal, J.
1997, AJ, 114, 54
Murray, N., Quataert, E., & Thompson, T. A. 2005, ApJ, 618, 569
Nardini, E., Risaliti, G., Watabe, Y., Salvati, M., & Sani, E. 2010, MNRAS, 405,
2505
Papadopoulos, P. P., van der Werf, P. P., Xilouris, E. M., et al. 2012, Monthly
Notices of the Royal Astronomical Society, 426, 2601
Pereira-Santaella, M., Colina, L., García-Burillo, S., et al. 2018, A&A, 616,
A171
Pereira-Santaella, M., Colina, L., García-Burillo, S., et al. 2020, A&A, 643, A89
Pereira-Santaella, M., Colina, L., García-Burillo, S., et al. 2021, A&A, 651, A42
Perna, M., Arribas, S., Catalan-Torrecilla, C., et al. 2020, A&A, 643, A139
Perna, M., Arribas, S., Colina, L., et al. 2022, A&A, 662, A94
Perna, M., Arribas, S., Pereira Santaella, M., et al. 2021, A&A, 646, A101
Pjanka, P., Greene, J. E., Seth, A. C., et al. 2017, ApJ, 844, 165
Prochaska, J. X., Kasen, D., & Rubin, K. 2011, ApJ, 734, 24
Ramos Almeida, C., Acosta-Pulido, J. A., Tadhunter, C. N., et al. 2019, MNRAS,
487, L18
Ramos Almeida, C., Bischetti, M., García-Burillo, S., et al. 2022, A&A, 658,
A155
Rodríguez Zaurín, J., Tadhunter, C. N., & González Delgado, R. M. 2010, MNRAS, 403, 1317
Runco, J. N., Malkan, M. A., Fernández-Ontiveros, J. A., Spinoglio, L., &
Pereira-Santaella, M. 2020, ApJ, 905, 57
Rupke, D. S., Veilleux, S., & Sanders, D. B. 2005a, ApJ, 632, 751
Rupke, D. S., Veilleux, S., & Sanders, D. B. 2005b, ApJS, 160, 115
Rupke, D. S. N. & Veilleux, S. 2013, ApJ, 768, 75
Saito, T., Iono, D., Ueda, J., et al. 2018, MNRAS, 475, L52
Sakamoto, K., Aalto, S., Combes, F., Evans, A., & Peck, A. 2014, ApJ, 797, 90
Salak, D., Nakai, N., Hatakeyama, T., & Miyamoto, Y. 2016, ApJ, 823, 68
Schawinski, K., Koss, M., Berney, S., & Sartori, L. F. 2015, Monthly Notices of
the Royal Astronomical Society, 451, 2517
Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett, J. W. 1997, The Astrophysical Journal, 478, 144
Spoon, H. W. W., Farrah, D., Lebouteiller, V., et al. 2013, ApJ, 775, 127
Stan Development Team. 2018, PyStan: the Python interface to Stan, Version
2.17.1.0
Stone, M., Veilleux, S., Meléndez, M., et al. 2016, ApJ, 826, 111
Stuber, S. K., Saito, T., Schinnerer, E., et al. 2021, A&A, 653, A172
Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, The Astrophysical
Journal Letters, 733, L16
Taylor, M. B. 2005, Astronomical Data Analysis Software and Systems XIV
ASP Conference Series, 347, 29
The Astropy Collaboration, Robitaille, Thomas P., Tollerud, Erik J., et al. 2013,
A&A, 558, A33
Van Der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science
and Engineering, 13, 22
Veilleux, S., Cecil, G., & Bland-Hawthorn, J. 2005, ARA&A, 43, 769
Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&A Rev., 28, 2
Veilleux, S., Meléndez, M., Sturm, E., et al. 2013, The Astrophysical Journal,
776, 27
Veilleux, S., Rupke, D. S. N., Kim, D. C., et al. 2009, ApJS, 182, 628
Venturi, G., Nardini, E., Marconi, A., et al. 2018, A&A, 619, A74
Véron-Cetty, M. P. & Véron, P. 2010, A&A, 518, A10
Walter, F., Bolatto, A. D., Leroy, A. K., et al. 2017, ApJ, 835, 265
Westmoquette, M. S., Clements, D. L., Bendo, G. J., & Khan, S. A. 2012, MNRAS, 424, 416


Article number, page 27 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



**Appendix A:** **Simulations of biconical outflows**


In this section we provide some additional information about the
simulations used to estimate the biases in the outflow properties measured with our method (see Sec. 4.5.2). We simulate a
biconcal outflow with a half opening angle of 40 [◦] . The maximum velocity of the outflow is 750 km s [−][1] and the maximum
outflow extension is _R_ _out_ = 2 kpc. The outflow flux decreases
with increasing radius (as it is expected in a scenario with constant mass outflow rate). We consider four distributions of the
outflow velocity as a function of radius: 1) constant velocity, 2)
velocity linearly decreasing with radius, 3) linear velocity law
with an increasing velocity going from zero to _v_ _max_ at a given
turnover radius _R_ _to_ = 0.5 × _R_ _out_, followed by a linearly decreasing trend with _v_ ( _R_ _out_ ) = 0 km s [−][1], 4) a radial velocity profile
with turnover radius as in the previous case, but accounting for
an initial velocity _v_ ( _r_ = 0) = 400 km s [−][1] . We consider four values for the inclination of the outflow with respect to our line of
sight: 10 [◦], 40 [◦], 70 [◦], and 90 [◦] (where an inclination _i_ = 90 [◦] corresponds to the plane of the sky). The systemic component has a
FWHM of 360 km s [−][1] and a flux ∼ 10 times the outflow flux. We
measure _v_ _out_, _M_ _out_ and _M_ [˙] _out_ from the total simulated profile (outflow+systemic component) considering only | _v_ | > 300 km s [−][1], to
mimic the method we are using with our data. Then, we measure
the outflow quantities ( _v_ _out_, _M_ _out_ and _M_ [˙] _out_ ) from the simulated
outflow emission profile (without the systemic component) considering the full velocity range.
Figure A.1 shows the ratios of the outflow quantities measured with our method (| _v_ | > 300 km s [−][1] ) and from the total outflow profile. The differences between the two methods increase
with increasing outflow inclination.


**Appendix B:** **Bisector fit methodology**


Here we explain in detail the methodology used for the bisector
fit used in Figures 17, 18, 19, and 20. Considering two generic
quantities _x_ and _y_, we fit a linear relation between them using the
Monte Carlo Markov-Chain (MCMC) implementation PyStan [5] .
We assume that the noise is normal distributed. We fit for the
parameter α and β that minimises the quantity:



σ _intr_, _x_ and σ _intr_, _y_ . The lightblue shaded regions in the Figures
shows the 1 σ uncertainty on the fit, obtained by sampling the
posterior distribution.


**Appendix C:** **CO outflow detection in absorption**


We detect a blue-shifted absorption in the CO(2-1) spectrum
of 07251-0248 E at velocities _v_ = [−320, −500] km s [−][1] (see
Fig. C.1). The absorption is compact, centred at the position of
the continuum peak and nearly coincident with the position of
the red-shifted outflow emission at _v_ = [300, 550] km s [−][1] . This
absorption can be interpreted as an outflow located in front of the
continuum source and moving towards us. Alternatively, it could
be due to an extremely compact outflow. The redshifted part of
the outflow, identified in emission, appears compact and moves
away from us along a direction compatible with our line of sight.
This is the only target for which we could identify an absorption. Dasyra & Combes (2012) detected a blue-shifted absorption at −950 km s [−][1] in the CO(3-2) spectrum of 13451+1232
(4C+12.50), obtained with the IRAM 30m telescope. No absorption was detected in the CO(1-0) data observed with the IRAM
Plateau de Bure Interferometer (PdBI) by Dasyra et al. (2014).
We inspect the ALMA CO(2-1) spectrum of the west nucleus
of 13451+1232 (shown in Fig. C.1), which is the nucleus dominating the FIR continuum emission and therefore, the nucleus
where an absorption could be produced. We do not observe any
significant absorption in the spectral channels on the blue-side
of the CO(2-1) line in this target. Although, we note that the
CO(3-2) absorption feature would be near the edge of the spectral window of our CO(2-1) spectrum.


**Appendix D:** **CO(2-1) moment maps**


**Appendix E:** **CO(2-1) spectra and**
**spectro-astrometry**


**Appendix F:** **Channel maps**



ϵ _y_ = �

_i_



( _f_ ( _x_ _i_, α, β) − _y_ _i_ ) [2]
 _y_ [2] _err_, _i_ [+][ σ] [2] _intr_, _y_



, (B.1)




where _f_ ( _x_ _i_, α, β) = α - _x_ _i_ + β, _y_ _err_, _i_ is the error on the quantity _y_ _i_, σ _intr_ is the intrinsic scatter, and the sum is over the data
points. The analogous expression can be defined with respect to
the quantity _x_ _i_ and the error _x_ _err_, _i_ :



, (B.2)




ϵ _x_ =
�

_i_



( _f_ ( _y_ _i_, γ, δ) − _x_ _i_ ) [2]

_x_ [2]

 _err_, _i_ [+][ σ] [2] _intr_, _x_



We run the fitting algorithm to find the best parameters that minimise ϵ _y_ and ϵ _x_, and then we perform a bisector fit. We run the
algorithm for 2000 steps with 4 chains as ‘burn-in’ phase. We
monitor the convergence by looking at the effective sample size
( _N_ _e f f_ ), which is defined as the number of iterations divided by
the integrated autocorrelation time _N_ _ef f_ = _N_ _iter_ /τ _int_ . We check
that the number of effective samples is > 10, which indicate that
the algorithm has converged (Gelman et al. 2004).
We derive the best fit values and the corresponding 1σ uncertainties from the median and the 16th-84th percentiles, respectively, of the marginalised posterior distributions of the parameters. The intrisic scatter is obtained by adding in quadrature


5
https://mc-stan.org/users/interfaces/pystan


Article number, page 28 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



1.4


1.2


1.0


0.8


0.6


0.4


0.2





2.0


1.5


1.0


0.5



1.4


1.2


1.0


0.8


0.6


0.4


0.2



0.0



0.0

0 20 40 60 80 100
outflow incl. [deg]



0.0

0 20 40 60 80 100
outflow incl. [deg]



Fig. A.1: Ratios of the outflow properties ( _v_ _out_, _M_ _out_ and _M_ [˙] _out_ ) measured with our method from the total profile (systemic+outflow)
considering only the | _v_ | - 300 km s [−][1] range and from only the outflow profile considering the full velocity range. The ratios are
shown as a function of the outflow inclination with respect to our line of sight (where _i_ = 90 [◦] is in the plane of the sky). The points
are colour-coded according to outflow velocity radial distribution used in the simulation. The black lines show the one-to-one ratio.



1.50


0.75


0


- 0.75




- 1.50

1.50 0.75 0 -0.75 -1.50
∆RA [arcsec]





35


30


25


20


15


10


5


5.0


4.5


4.0


3.5


3.0


2.5



CO


zoom − in









Fig. C.1: _Left:_ CO(2-1) spectrum (with continuum) of 07251-0248 E, showing an absorption at velocities _v_ = [−320, −500] km

|Col1|Col2|
|---|---|
|||
|20<br>40<br>60<br>80<br>outflow incl. [deg]<br>  f the outﬂow propert<br>the |_v_| > 300 km s−1<br>  on of the outﬂow inc<br> according to outﬂow<br>07251-0248 E|20<br>40<br>60<br>80<br>outflow incl. [deg]<br>  f the outﬂow propert<br>the |_v_| > 300 km s−1<br>  on of the outﬂow inc<br> according to outﬂow<br>07251-0248 E|
|||
|||
|||
|00<br>-400<br>-200<br>0<br>200<br>400<br>v [km/s]<br>(2-1)sectrum(wit|00<br>-400<br>-200<br>0<br>200<br>400<br>v [km/s]<br>(2-1)sectrum(wit|

s [−][1] . _Middle:_ Emission of the blue- and red-shifted high-velocity channels of 07251-0248 E, shown with blue and red contours,
respectively. The lowest contour corresponds to the 3σ level. The next contour levels are (0.5, 0.7, 0.9) of the peak of the emission.
Dashed lines indicate negative contour levels ([-3, -4, -5, -6, -7]×σ). The dashed black circle shows the size of the outflow ( _R_ _out_ )
and the grey cross the central position of the outflow. The black and green crosses shows the position of the continuum peaks of
the E and W nuclei, respectively. _Right:_ CO(2-1) spectrum (with continuum) of 13451+1232 W. No clear absorption is detected
in this spectrum at the velocities of the an absorption detected in the CO(3-2) spectrum by Dasyra & Combes (2012) at _v_ =

[−700, −1200] km s [−][1] (see orange shaded region).


Article number, page 29 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



CO(2-1) moment 0


1.0 0 - 1.0 - 2.1
∆RA [arcsec]



CO(2-1) moment 1



1.0 0 - 1.0 - 2.1
∆RA [arcsec]



2.1


- 2.1



continuum







2.1 1.0 0 - 1.0 - 2.1
∆RA [arcsec]



CO(2-1) peak


1.0 0 - 1.0 - 2.1
∆RA [arcsec]



CO(2-1) moment 2


1.0 0  - 1.0  - 2.1
∆RA [arcsec]



0 5 10 15 20
mJy/beam


CO(2-1) peak



0 1 2 3 4 5 6 7
Jy/beam km s [−][1]


CO(2-1) moment 0



-200 -100 0 100 200
km s [−][1]


CO(2-1) moment 1





1.9


- 1.9



0.0 0.8 1.6 2.4 3.2 4.0 4.8 5.6
mJy/beam


continuum



15 30 45 60 75 90 105 120
km s [−][1]


CO(2-1) moment 2



1.9 1.0 0 - 1.0 - 1.9
∆RA [arcsec]



1.0 0 - 1.0 - 1.9
∆RA [arcsec]



1.0 0 - 1.0 - 1.9
∆RA [arcsec]



0 2 4 6 8 10 12 14 16
mJy/beam


CO(2-1) peak



0.0 0.4 0.8 1.2 1.6 2.0 2.4 2.8
Jy/beam km s [−][1]


CO(2-1) moment 0



6.0


- 6.0



0 0.2 0.4 0.6 0.8
mJy/beam


continuum



6.0 3.0 0 - 3.0 - 6.0
∆RA [arcsec]



3.0 0 - 3.0 - 6.0
∆RA [arcsec]



3.0 0 - 3.0 - 6.0
∆RA [arcsec]



1.0 0  - 1.0  - 1.9
∆RA [arcsec]


-100 -50 0 50 100
km s [−][1]


CO(2-1) moment 1


3.0 0  - 3.0  - 6.0
∆RA [arcsec]



0 4 8 12 16 20 24 28 32
mJy/beam


CO(2-1) peak



0 1 2 3 4 5 6 7 8
Jy/beam km s [−][1]


CO(2-1) moment 0



-200 -100 0 100 200
km s [−][1]


CO(2-1) moment 1





1.5


- 1.5



0 0.2 0.4 0.6 0.8
mJy/beam


continuum



1.5 0.8 0 - 0.8 - 1.5
∆RA [arcsec]



0.8 0 - 0.8 - 1.5
∆RA [arcsec]



0.8 0 - 0.8 - 1.5
∆RA [arcsec]



0.8 0 - 0.8 - 1.5
∆RA [arcsec]



1.0 0    - 1.0    - 1.9
∆RA [arcsec]


20 30 40 50 60 70 80 90
km s [−][1]


CO(2-1) moment 2


3.0 0    - 3.0    - 6.0
∆RA [arcsec]


15 30 45 60 75 90
km s [−][1]


CO(2-1) moment 2


0.8 0    - 0.8    - 1.5
∆RA [arcsec]



0.0 1.5 3.0 4.5 6.0 7.5 9.0
mJy/beam


CO(2-1) peak



0.0 0.2 0.4 0.6 0.8 1.0 1.2 1.4 1.6 1.8

Jy/beam km s [−][1]


CO(2-1) moment 0



-100 -50 0 50 100
km s [−][1]


CO(2-1) moment 1





5.7


- 5.7



0 0.2 0.4 0.6
mJy/beam


continuum



15 30 45 60 75 90 105
km s [−][1]


CO(2-1) moment 2



5.7 2.8 0 - 2.8 - 5.7
∆RA [arcsec]



2.8 0 - 2.8 - 5.7
∆RA [arcsec]



2.8 0 - 2.8 - 5.7
∆RA [arcsec]



2.8 0 - 2.8 - 5.7
∆RA [arcsec]


-100 -50 0 50 100
km s [−][1]



2.8 0  - 2.8  - 5.7
∆RA [arcsec]


15 30 45 60 75 90 105
km s [−][1]



0.0 0.6 1.2 1.8 2.4 3.0 3.6 4.2 4.8

mJy/beam


Article number, page 30 of 76



0 20 40 60 80 100 120 140 160
mJy/beam



0 4 8 12 16 20 24 28 32
Jy/beam km s [−][1]



Fig. D.1: See caption of Figure 2

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



CO(2-1) moment 0


1.4 0 - 1.4 - 2.8
∆RA [arcsec]



CO(2-1) moment 1



1.4 0 - 1.4 - 2.8
∆RA [arcsec]



2.8


- 2.8



continuum







2.8 1.4 0 - 1.4 - 2.8
∆RA [arcsec]



CO(2-1) peak


1.4 0 - 1.4 - 2.8
∆RA [arcsec]



CO(2-1) moment 2


1.4 0  - 1.4  - 2.8
∆RA [arcsec]



0 6 12 18 24 30 36 42 48
mJy/beam


CO(2-1) peak



0 2 4 6 8 10 12 14 16 18
Jy/beam km s [−][1]


CO(2-1) moment 0



-200 -100 0 100 200
km s [−][1]


CO(2-1) moment 1





4.1


- 4.1



0 1 2 3 4 5 6 7 8
mJy/beam


continuum



15 30 45 60 75 90 105 120 135
km s [−][1]


CO(2-1) moment 2



4.1 2.0 0 - 2.0 - 4.1
∆RA [arcsec]



2.0 0 - 2.0 - 4.1
∆RA [arcsec]



2.0 0 - 2.0 - 4.1
∆RA [arcsec]



2.0 0   - 2.0   - 4.1
∆RA [arcsec]


-300 -200 -100 0 100 200 300
km s [−][1]


CO(2-1) moment 1



0 10 20 30 40 50 60 70 80 90
mJy/beam


CO(2-1) peak



0 4 8 12 16 20 24 28
Jy/beam km s [−][1]


CO(2-1) moment 0





4.8


- 4.8



0 0.5 1.0 1.5 2.0
mJy/beam


continuum



4.8 2.4 0 - 2.4 - 4.8
∆RA [arcsec]



2.4 0 - 2.4 - 4.8
∆RA [arcsec]



2.4 0 - 2.4 - 4.8
∆RA [arcsec]



2.4 0 - 2.4 - 4.8
∆RA [arcsec]



0 6 12 18 24 30 36 42 48 54
mJy/beam


CO(2-1) peak



0.0 1.5 3.0 4.5 6.0 7.5 9.010.512.013.5

Jy/beam km s [−][1]


CO(2-1) moment 0



-300 -200 -100 0 100 200 300
km s [−][1]


CO(2-1) moment 1





2.3


- 2.3



0 0.25 0.5 0.75 1.0 1.25
mJy/beam


continuum



2.3 1.2 0 - 1.2 - 2.3
∆RA [arcsec]



1.2 0 - 1.2 - 2.3
∆RA [arcsec]



1.2 0 - 1.2 - 2.3
∆RA [arcsec]



1.2 0 - 1.2 - 2.3
∆RA [arcsec]



2.0 0   - 2.0   - 4.1
∆RA [arcsec]


25 50 75 100 125 150 175 200
km s [−][1]


CO(2-1) moment 2


2.4 0   - 2.4   - 4.8
∆RA [arcsec]


15 30 45 60 75 90 105 120
km s [−][1]


CO(2-1) moment 2


1.2 0   - 1.2   - 2.3
∆RA [arcsec]



0 4 8 12 16 20 24 28 32
mJy/beam


CO(2-1) peak



0 1 2 3 4 5 6 7 8
Jy/beam km s [−][1]


CO(2-1) moment 0



-100 -50 0 50 100
km s [−][1]


CO(2-1) moment 1





1.9


- 1.9



0 0.25 0.5 0.75 1.0
mJy/beam


continuum



15 30 45 60 75 90 105
km s [−][1]


CO(2-1) moment 2



1.9 1.0 0 - 1.0 - 1.9
∆RA [arcsec]



1.0 0 - 1.0 - 1.9
∆RA [arcsec]



1.0 0 - 1.0 - 1.9
∆RA [arcsec]



1.0 0   - 1.0   - 1.9
∆RA [arcsec]


-200 -100 0 100 200
km s [−][1]



1.0 0   - 1.0   - 1.9
∆RA [arcsec]


15 30 45 60 75 90 105
km s [−][1]


Article number, page 31 of 76



0 0.2 0.4
mJy/beam



0 5 10 15 20
mJy/beam



0 1 2 3 4 5
Jy/beam km s [−][1]


Fig. D.1: continued.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



CO(2-1) moment 0


2.2 0 - 2.2 - 4.4
∆RA [arcsec]



2.2 0  - 2.2  - 4.4
∆RA [arcsec]


-200 -100 0 100 200
km s [−][1]


CO(2-1) moment 1



CO(2-1) moment 1



4.4



continuum







4.4 2.2 0 - 2.2 - 4.4
∆RA [arcsec]



CO(2-1) peak


2.2 0 - 2.2 - 4.4
∆RA [arcsec]



0 8 16 24 32 40 48 56 64
mJy/beam


CO(2-1) peak



0 5 10 15 20
Jy/beam km s [−][1]


CO(2-1) moment 0





7.8


- 7.8



0.0 0.6 1.2 1.8 2.4 3.0 3.6 4.2 4.8

mJy/beam


continuum



7.8 3.9 0 - 3.9 - 7.8
∆RA [arcsec]



3.9 0 - 3.9 - 7.8
∆RA [arcsec]



3.9 0 - 3.9 - 7.8
∆RA [arcsec]



3.9 0 - 3.9 - 7.8
∆RA [arcsec]



CO(2-1) moment 2


2.2 0   - 2.2   - 4.4
∆RA [arcsec]


20 40 60 80 100 120 140 160
km s [−][1]


CO(2-1) moment 2


3.9 0   - 3.9   - 7.8
∆RA [arcsec]



0 50 100 150 200 250 300 350 400

mJy/beam


CO(2-1) peak



0 10 20 30 40 50 60 70 80
Jy/beam km s [−][1]


CO(2-1) moment 0



-200 -100 0 100 200
km s [−][1]


CO(2-1) moment 1





15 30 45 60 75 90 105 120 135
km s [−][1]


CO(2-1) moment 2



2.4


- 2.4



0.0 1.5 3.0 4.5 6.0 7.5 9.0 10.5
mJy/beam


continuum



2.4 1.2 0 - 1.2 - 2.4
∆RA [arcsec]



1.2 0 - 1.2 - 2.4
∆RA [arcsec]



1.2 0 - 1.2 - 2.4
∆RA [arcsec]



1.2 0 - 1.2 - 2.4
∆RA [arcsec]



1.2 0 - 1.2 - 2.4
∆RA [arcsec]



0 2 4 6 8 10 12 14 16
mJy/beam


CO(2-1) peak



0.0 0.5 1.0 1.5 2.0 2.5 3.0 3.5 4.0
Jy/beam km s [−][1]


CO(2-1) moment 0



-300 -200 -100 0 100 200 300
km s [−][1]


CO(2-1) moment 1





15 30 45 60 75 90 105 120
km s [−][1]


CO(2-1) moment 2



4.4


- 4.4



0 40 80 120 160 200 240 280

mJy/beam


continuum



4.4 2.2 0 - 2.2 - 4.4
∆RA [arcsec]



2.2 0 - 2.2 - 4.4
∆RA [arcsec]



2.2 0 - 2.2 - 4.4
∆RA [arcsec]



2.2 0   - 2.2   - 4.4
∆RA [arcsec]


-200 -100 0 100 200
km s [−][1]


CO(2-1) moment 1



0 8 16 24 32 40 48 56
mJy/beam


CO(2-1) peak



0 2 4 6 8 10 12 14 16 18
Jy/beam km s [−][1]


CO(2-1) moment 0





3.6


- 3.6



0 0.25 0.5 0.75 1.0 1.25 1.5
mJy/beam


continuum



3.6 1.8 0 - 1.8 - 3.6
∆RA [arcsec]



1.8 0 - 1.8 - 3.6
∆RA [arcsec]



1.8 0 - 1.8 - 3.6
∆RA [arcsec]



1.8 0  - 1.8  - 3.6
∆RA [arcsec]


-50 -25 0 25 50
km s [−][1]



2.2 0   - 2.2   - 4.4
∆RA [arcsec]


15 30 45 60 75 90 105 120 135
km s [−][1]


CO(2-1) moment 2


1.8 0   - 1.8   - 3.6
∆RA [arcsec]


16 24 32 40 48 56 64 72
km s [−][1]



0 0.2 0.4 0.6 0.8
mJy/beam


Article number, page 32 of 76



0 5 10 15 20 25 30 35 40
mJy/beam



0 1 2 3 4 5 6 7 8
Jy/beam km s [−][1]


Fig. D.1: continued.

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



CO(2-1) peak



CO(2-1) moment 1



5.3 0 - 5.3 - 10.6
∆RA [arcsec]



10.6



continuum












- 10.6

10.6 5.3 0   - 5.3   - 10.6
∆RA [arcsec]



5.3 0 - 5.3 - 10.6
∆RA [arcsec]



CO(2-1) moment 0


5.3 0 - 5.3 - 10.6
∆RA [arcsec]



CO(2-1) moment 2


5.3 0  - 5.3  - 10.6
∆RA [arcsec]



0 100200300400500600700800900

mJy/beam


CO(2-1) peak



0 40 80 120 160 200 240 280
Jy/beam km s [−][1]


CO(2-1) moment 0



-300 -200 -100 0 100 200 300
km s [−][1]


CO(2-1) moment 1





20 40 60 80 100 120 140 160
km s [−][1]


CO(2-1) moment 2



1.9


- 1.9



0 15 30 45 60 75 90 105 120
mJy/beam


continuum



1.9 0.9 0 - 0.9 - 1.9
∆RA [arcsec]



0.9 0 - 0.9 - 1.9
∆RA [arcsec]



0.9 0 - 0.9 - 1.9
∆RA [arcsec]



0.9 0 - 0.9 - 1.9
∆RA [arcsec]



0.9 0 - 0.9 - 1.9
∆RA [arcsec]



0 5 10 15 20 25
mJy/beam



0.0 1.5 3.0 4.5 6.0 7.5 9.0 10.512.0

Jy/beam km s [−][1]



-100 -50 0 50 100
km s [−][1]







0 0.25 0.5 0.75 1.0
mJy/beam


continuum



20 40 60 80 100 120 140 160 180

km s [−][1]










CO(2-1) moment 1



0.0 0.2 0.4 0.6 0.8 1.0 1.2 1.4 1.6

Jy/beam km s [−][1]


CO(2-1) moment 0





5.7


- 5.7



0 0.2 0.4
mJy/beam


continuum





0 1 2 3 4 5 6
mJy/beam


CO(2-1) peak



5.7 2.8 0 - 2.8 - 5.7
∆RA [arcsec]



2.8 0 - 2.8 - 5.7
∆RA [arcsec]



2.8 0 - 2.8 - 5.7
∆RA [arcsec]



2.8 0 - 2.8 - 5.7
∆RA [arcsec]



24 32 40 48 56 64 72 80 88
km s [−][1]


CO(2-1) moment 2


2.8 0   - 2.8   - 5.7
∆RA [arcsec]



0 20 40 60 80 100120140160180

mJy/beam


CO(2-1) peak



0 10 20 30 40 50 60 70 80 90
Jy/beam km s [−][1]


CO(2-1) moment 0



-300 -200 -100 0 100 200 300
km s [−][1]


CO(2-1) moment 1





4.3


- 4.3



0 3 6 9 12 15 18 21 24
mJy/beam


continuum



20 40 60 80 100 120 140 160 180
km s [−][1]


CO(2-1) moment 2



4.3 2.2 0 - 2.2 - 4.3
∆RA [arcsec]



2.2 0 - 2.2 - 4.3
∆RA [arcsec]



2.2 0 - 2.2 - 4.3
∆RA [arcsec]



2.2 0  - 2.2  - 4.3
∆RA [arcsec]


-200 -100 0 100 200
km s [−][1]



2.2 0   - 2.2   - 4.3
∆RA [arcsec]


15 30 45 60 75 90 105 120
km s [−][1]


Article number, page 33 of 76



0 0.5 1.0 1.5 2.0 2.5
mJy/beam



0 10 20 30 40 50 60 70 80
mJy/beam



0 5 10 15 20
Jy/beam km s [−][1]


Fig. D.1: continued.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



CO(2-1) moment 0


2.0 0 - 2.0 - 3.9
∆RA [arcsec]



CO(2-1) moment 1



2.0 0 - 2.0 - 3.9
∆RA [arcsec]



3.9


- 3.9



continuum







3.9 2.0 0 - 2.0 - 3.9
∆RA [arcsec]



CO(2-1) peak


2.0 0 - 2.0 - 3.9
∆RA [arcsec]



CO(2-1) moment 2


2.0 0 - 2.0 - 3.9
∆RA [arcsec]



0 8 16 24 32 40 48 56 64
mJy/beam


CO(2-1) peak



0 2 4 6 8 10 12 14 16
Jy/beam km s [−][1]


CO(2-1) moment 0



-50 -25 0 25 50
km s [−][1]


CO(2-1) moment 1





2.3


- 2.3



0 0.5 1.0 1.5 2.0
mJy/beam


continuum



20 30 40 50 60 70 80 90
km s [−][1]


CO(2-1) moment 2



2.3 1.2 0 - 1.2 - 2.3
∆RA [arcsec]



1.2 0 - 1.2 - 2.3
∆RA [arcsec]



1.2 0 - 1.2 - 2.3
∆RA [arcsec]



1.2 0  - 1.2  - 2.3
∆RA [arcsec]


-200 -100 0 100 200
km s [−][1]


CO(2-1) moment 1



0 6 12 18 24 30 36 42 48
mJy/beam


CO(2-1) peak



0 2 4 6 8 10 12 14 16 18
Jy/beam km s [−][1]


CO(2-1) moment 0





2.3


- 2.3



0.0 0.4 0.8 1.2 1.6 2.0 2.4 2.8 3.2 3.6

mJy/beam


continuum



2.3 1.1 0 - 1.1 - 2.3
∆RA [arcsec]



1.1 0 - 1.1 - 2.3
∆RA [arcsec]



1.1 0 - 1.1 - 2.3
∆RA [arcsec]



1.1 0  - 1.1  - 2.3
∆RA [arcsec]


-100 -50 0 50 100
km s [−][1]


CO(2-1) moment 1



0 5 10 15 20 25
mJy/beam


CO(2-1) peak



0 1 2 3 4 5 6 7 8 9
Jy/beam km s [−][1]


CO(2-1) moment 0





2.8


- 2.8



0 0.5 1.0 1.5 2.0
mJy/beam


continuum



2.8 1.4 0 - 1.4 - 2.8
∆RA [arcsec]



1.4 0 - 1.4 - 2.8
∆RA [arcsec]



1.4 0 - 1.4 - 2.8
∆RA [arcsec]



1.4 0 - 1.4 - 2.8
∆RA [arcsec]



1.2 0  - 1.2  - 2.3
∆RA [arcsec]


30 45 60 75 90 105 120 135 150
km s [−][1]


CO(2-1) moment 2


1.1 0  - 1.1  - 2.3
∆RA [arcsec]


20 40 60 80 100 120 140
km s [−][1]


CO(2-1) moment 2


1.4 0  - 1.4  - 2.8
∆RA [arcsec]



0 5 10 15 20 25
mJy/beam


CO(2-1) peak



0.0 1.5 3.0 4.5 6.0 7.5 9.0 10.5
Jy/beam km s [−][1]


CO(2-1) moment 0



-200 -100 0 100 200
km s [−][1]


CO(2-1) moment 1





5.7


- 5.7



0.0 0.4 0.8 1.2 1.6 2.0 2.4 2.8
mJy/beam


continuum



20 40 60 80 100 120 140 160
km s [−][1]


CO(2-1) moment 2



5.7 2.8 0 - 2.8 - 5.7
∆RA [arcsec]



2.8 0 - 2.8 - 5.7
∆RA [arcsec]



2.8 0 - 2.8 - 5.7
∆RA [arcsec]



2.8 0 - 2.8 - 5.7
∆RA [arcsec]



2.8 0  - 2.8  - 5.7
∆RA [arcsec]


15 30 45 60 75 90 105 120
km s [−][1]



0.0 0.5 1.0 1.5 2.0 2.5 3.0 3.5 4.0
mJy/beam


Article number, page 34 of 76



0 10 20 30 40 50 60 70 80
mJy/beam



0 5 10 15 20
Jy/beam km s [−][1]



-100 -50 0 50 100
km s [−][1]



Fig. D.1: continued.

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



0.2


0.1


0


- 0.1












|00091-0738 S low v|Col2|Col3|
|---|---|---|
|200 pc<br>a)<br>low v||0<br>1<br>2<br>3|
|200 pc<br>a)<br>low v|||
|200 pc<br>a)<br>low v|||
|200 pc<br>a)<br>low v|||



















120


105


90


75


60


45


30


15


120


105


90


75


60


45


30


15




- 0.2

0.2 0.1 0  - 0.1  - 0.2
∆RA [arcsec]







1.20



1.20



-800 -600 -400 -200 0 200 400 600 800
v [km/s]


CO(2-1) moment 1



0.4


0.2


0


- 0.2



00091-0738 N



CO(2-1) moment 2






























- 0.4



300


200


100


100


200


300


200









-800 -600 -400 -200 0 200 400 600 800
v [km/s]


Fig. E.1: Spectro-astrometry and outflow maps for 00091-0738 S and 00091-0738 N. _a)_ Spectro-astrometry of the CO(2-1) emission
line, i.e. centroid position of the CO(2-1) emission in the different velocity channels. The points are colour-coded by the channel
velocity. The dotted line is a linear fit to the low-velocity points (kinematic major axis) and the dashed line is a fit to the high-velocity
points (indicating the outflow direction, if present). Panel _b)_ and _c)_ show the moment 1 and moment 2 maps, where the green square
indicate the field of view of panel _(a)_ . The grey ellipse illustrates the ALMA beam FWHM. The grey contours on the moment 1 maps
are every 50 km s [−][1] (every 25 km s [−][1] if the maximum value < 100 km s [−][1] ), and every 25 km s [−][1] (every 15 km s [−][1] if the maximum
value < 150 km s [−][1] ) on the moment 2 map. In black are the CO(2-1) moment 0 contours ([3, 6, 25, 50, 75]×σ). _d)_ Emission of the
high-velocity channels(if detected), integrated over the velocity ranges indicated on the CO(2-1) spectrum (shown in panel _e_ ). Blueand red-shifted channels are shown with blue and red contours, respectively (dashed lines indicate negative contour levels). The
lowest contour corresponds to the 3σ level. The next contour levels are (0.5, 0.7, 0.9) of the peak of the emission, if these are above
the 3σ level. The dashed circle shows the size of the outflow ( _R_ _out_ ). _e)_ CO(2-1) continuum-subtracted spectrum extracted from a
circle with radius equivalent to the outflow size ( _R_ _out_ ). The lower panel shows an y-axis zoom-in to highlight the emission in the
wings. The horizontal dashed line show the 1σ noise level. The vertical dashed lines indicated the ‘flux-weighted’ velocity of the
blue and red-shifted outflow ( _v_ _out_ ). _f)_ OH 119 µm spectrum ( _upper_, if available) compared with the nuclear CO spectrum ( _bottom_ ),
convolved to the resolution of the OH spectrum (FWHM∼ 270 km s [−][1] ). The total fit to the OH lines is shown with a magenta line,
while the Gaussian components of the fit are shown in lightblue and brown. The orange lines show the 50 Monte Carlo iterations
used to estimate the uncertainties on the fit (see Sec. 4.7). The vertical dotted, dashed and dot-dashed lines show the _v_ 50, _v_ 84, and
_v_ 98 percentile velocities, respectively. The blue-shaded area in the upper panel shows the wavelength range between _v_ 84 and _v_ 98 .


Article number, page 35 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



90


80


70


60


50


40


30


20



0.2


0.1


0


- 0.1



00188-0856



CO(2-1) moment 1



0


50











CO(2-1) moment 2



0.60





100


50



0.60
















- 0.2





1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]







-800 -600 -400 -200 0 200 400 600 800
v [km/s]











0.4


0.2


0


- 0.2










































- 0.4







1500 1000 500 0 500 1000 1500





-800 -600 -400 -200 0 200 400 600 800







0.2


0.1


0


- 0.1





































105


90


75


60


45


30










- 0.2





15



1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]







-800 -600 -400 -200 0 200 400 600 800
v [km/s]





Fig. E.1: continued.



Article number, page 36 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs











































1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]















2.00





















-800 -600 -400 -200 0 200 400 600 800
v [km/s]



























































































































1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]





-800 -600 -400 -200 0 200 400 600 800
v [km/s]



Fig. E.1: continued.



Article number, page 37 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv















































2.00


1.00


0
















- 1.00

























































































































-800 -600 -400 -200 0 200 400 600 800
v [km/s]


Fig. E.1: continued.





Article number, page 38 of 76

[−]





























































































































velocity [km s [−][1] ]


Article number, page 39 of 76





















































v [km/s]









∆RA [arcsec]



Fig. E.1: continued.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



105


90


75


60


45


30









0.40



0.40


0.20







150


100













0.20


0


- 0.20




   - 0.20


100



0





50


0



50











200


100


0


100


200



150























































2.00


1.00













0


- 1.00































































1.50


0.75















0


- 0.75









Fig. E.1: continued.



Article number, page 40 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



0.8


0.4


0


 - 0.4















150


100


50





















50


150





135


120


105


90


75


60


45


30




 - 0.8







3.00


1.50


0


- 1.50























0.2


0.1


0


 - 0.1




























 - 0.2



















-1000 -800 -600 -400 -200 0 200 400 600 800 1000
v [km/s]



1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]





54


48


42


36


30


24


18


12


6



0.2


0.1


0


 - 0.1



13451+1232 E



0.60



CO(2-1) moment 1









CO(2-1) moment 2



0.60








 - 0.2



100



3

2

1

0

1

2

3

4


2


1


0


1


2


3


4







Article number, page 41 of 76



-1000 -800 -600 -400 -200 0 200 400 600 800 1000
v [km/s]


Fig. E.1: continued.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



135


120


105


90


75


60


45


30


15



0.4


0.2


0


 - 0.2



14348-1447 SW



CO(2-1) moment 1



nuclear CO


1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]



1.20


0.60


0


- 0.60



50


0.60 0        - 0.60        - 1.20
∆RA [arcsec]


e) CO


zoom − in


-800 -600 -400 -200 0 200 400 600 800
v [km/s]


Fig. E.1: continued.



100


50


0


50





a)



low v

high v

angle: 56°





CO(2-1) moment 2



nuclear CO


1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]


CO(2-1) moment 2



200 pc


 - 0.4

0.4 0.2 0   - 0.2   - 0.4
∆RA [arcsec]



100


0.60 0        - 0.60        - 1.20
∆RA [arcsec]


e) CO


zoom − in


-800 -600 -400 -200 0 200 400 600 800
v [km/s]



0.60 0  - 0.60  - 1.20
∆RA [arcsec]


v50v84 v50v84 f) OH

v98 v98



1.25


0.62


0


- 0.62


- 1.25



d)



500 pc



1.25 0.62 0 -0.62 -1.25
∆RA [arcsec]



100


50


0


50


100





0.4


0.2


0


 - 0.2



14348-1447 NE



1.20


0.60


0


- 0.60



CO(2-1) moment 1





a)



low v

high v

angle: 82°





120


105


90


75


60


45


30



200 pc


 - 0.4

0.4 0.2 0   - 0.2   - 0.4
∆RA [arcsec]



0.60 0        - 0.60        - 1.20
∆RA [arcsec]


e) CO


zoom − in


-800 -600 -400 -200 0 200 400 600 800
v [km/s]



nuclear CO


1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]


CO(2-1) moment 2



0.60 0  - 0.60  - 1.20
∆RA [arcsec]


v50v84 v50v84 f) OH

v98 v98



1.25


0.62


0


- 0.62


- 1.25



d)



500 pc



1.25 0.62 0 -0.62 -1.25
∆RA [arcsec]



0.4


0.2


0


 - 0.2



14378-3651



CO(2-1) moment 1



1.20


0.60


0


- 0.60





50


25


0


25



a)



low v



1.20


0.60


0


- 0.60


1.2


1.1


1.0


0.9


0.8


0.7


3.5

3.0

2.5

2.0

1.5

1.0

0.5

0.0


1.20


0.60


0


- 0.60


1.2


1.1


1.0


0.9


0.8


0.7


1.5


1.0


0.5


0.0


1.20


0.60


0


 - 0.60


1.2


1.1


1.0


0.9


0.8


0.7


1.5


1.0


0.5


0.0







72


64


56


48


40


32


24


16



200 pc


 - 0.4

0.4 0.2 0   - 0.2   - 0.4
∆RA [arcsec]



600


400


200


0


200


400


600


150


100


50


0


12


10


8


6


4


2


0


400


200


0


200


400


100


80


60


40


20


0

6


4


2


0


2


400


200


0


200


400


100


80


60


40


20


0


6

5

4

3

2

1

0

1



0.60 0   - 0.60   - 1.20
∆RA [arcsec]


v50v84 v50v84 f) OH

v98 v98



1.50


0.75


0


- 0.75



d)



500 pc


- 1.501.50 0.75 0 -0.75 -1.50

∆RA [arcsec]



Article number, page 42 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs























































































































































































Article number, page 43 of 76







-800 -600 -400 -200 0 200 400 600 800
v [km/s]


Fig. E.1: continued.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



200


100


100


200



180


160


140


120


100





0.5


0.2


0


 - 0.2






























 - 0.5







1.50


0.75


0


- 0.75







1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]














- 1.501.50 0.75 0 -0.75 -1.50

∆RA [arcsec]



-800 -600 -400 -200 0 200 400 600 800
v [km/s]




















































|a)|l ao niw lv<br>h g gh v<br>e : 45°|
|---|---|
|200 pc||





1.75


0.88


0


- 0.88



















































































-800 -600 -400 -200 0 200 400 600 800
v [km/s]


Fig. E.1: continued.



Article number, page 44 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



0.2


0.1


0


 - 0.1



19542+1110



CO(2-1) moment 1



1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]


Article number, page 45 of 76



CO(2-1) moment 2



400


200











0



200



0.80


0.40


0


- 0.40





50


25


0


25


50





90


80


70


60


50


40


30


20










 - 0.2

0.2 0.1 0   - 0.1   - 0.2
∆RA [arcsec]



400



0.40 0        - 0.40        - 0.80
∆RA [arcsec]


-800 -600 -400 -200 0 200 400 600 800
v [km/s]



1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]


CO(2-1) moment 2



∆RA [arcsec]



0.75


0.38


0


- 0.38


- 0.75











0.75 0.38 0 -0.38 -0.75
∆RA [arcsec]



0.4


0.2


0


 - 0.2



20087-0308



CO(2-1) moment 1



















200


100


0


100


200





150


135


120


105


90


75


60


45


30




 - 0.4







1500 1000 500 0 500 1000 1500
velocity [km s [−][1] ]


CO(2-1) moment 2



0.75


0.38


0


- 0.38



-800 -600 -400 -200 0 200 400 600 800
v [km/s]










- 0.750.75 0.38 0 -0.38 -0.75

∆RA [arcsec]





20100-4156 SE



CO(2-1) moment 1



100









0.80


0.40


0


 - 0.40











100


50


0


50


100

















0.75


0.38


0


- 0.38


- 0.75

















0.75 0.38 0 -0.38 -0.75
∆RA [arcsec]



-1200-1000-800 -600 -400 -200 0 200 400 600 800 10001200
v [km/s]


Fig. E.1: continued.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



39


36


33


30


27


24


21


18


15



0.2


0.1


0


 - 0.1



20100-4156 NW





0.60



0.60





CO(2-1) moment 1



30


20


10


0


10


20









CO(2-1) moment 2






 - 0.2



100





6


4


2


0


2


3


2


1


0


1


2



30





-1200-1000-800 -600 -400 -200 0 200 400 600 800 10001200
v [km/s]









































































































































Fig. E.1: continued.



Article number, page 46 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs























































-800 -600 -400 -200 0 200 400 600 800
v [km/s]


Fig. E.1: continued.



Article number, page 47 of 76

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv


Fig. F.1: CO channel maps of 00091-0738 S showing the emission in channels of 50 km s [−][1] on the blue and red-shifted side with
respect to the CO redshift ( _z_ CO ). The lowest contour corresponds to 3×σ, where σ is the rms measured in each 50 km s [−][1] channel
(in mJy), and the other contours correspond to 0.1, 0.2, 0.3, 0.5, 0.7, 0.9× maximum flux. Contours are shown only if they are
above the 3×σ level. Dashed contours show negative -3, -4, -5 ...×σ levels. The σ values (in mJy) for the blue and red channels are
indicated in the top-right corner. The dotted line shows the kinematic major axis, the dashed line shows the direction of the outflow
(if present). The black cross shows the peak position of the ALMA continuum. The green cross shows the continuum position of
the second nucleus in interacting systems.



1.25


0.62


0


- 0.62


- 1.25


1.25


0.62


0


- 0.62


- 1.25


1.25






0.62 0 -0.62 -1.25
∆RA [arcsec]




0.62 0 -0.62 -1.25
∆RA [arcsec]



0.62


0


   - 0.62


   - 1.25

0.62 0 -0.62 -1.25
∆RA [arcsec]


Article number, page 48 of 76




0.62 0 -0.62 -1.25
∆RA [arcsec]

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



1.25


0.62


0


- 0.62


- 1.25


1.25


0.62


0


- 0.62


- 1.25


0.50


0.25


0


- 0.25


- 0.50


0.50


0.25


0


- 0.25


- 0.50



0.25 0 -0.25 -0.50
∆RA [arcsec]



0.62 0 -0.62 -1.25
∆RA [arcsec]




0.62 0 -0.62 -1.25
∆RA [arcsec]






0.62 0 -0.62 -1.25
∆RA [arcsec]



Fig. F.2: 00091-0738 N.




0.62 0 -0.62 -1.25
∆RA [arcsec]


0.25 0 -0.25 -0.50
∆RA [arcsec]


Article number, page 49 of 76







0.25 0 -0.25 -0.50
∆RA [arcsec]




0.25 0 -0.25 -0.50
∆RA [arcsec]



Fig. F.3: 00188-0856.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



1.50


0.75


0


- 0.75


- 1.50


1.50


0.75


0


- 0.75


- 1.50


0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38











0.75 0 -0.75 -1.50
∆RA [arcsec]



0.75 0 -0.75 -1.50
∆RA [arcsec]







0.75 0 -0.75 -1.50
∆RA [arcsec]



0.75 0 -0.75 -1.50
∆RA [arcsec]



Fig. F.4: 00509+1225.






























   - 0.75

0.38 0 -0.38 -0.75
∆RA [arcsec]


Article number, page 50 of 76



0.38 0 -0.38 -0.75
∆RA [arcsec]



0.38 0 -0.38 -0.75
∆RA [arcsec]



0.38 0 -0.38 -0.75
∆RA [arcsec]



Fig. F.5: 01572+0009.

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



2.00


1.00


0


- 1.00


- 2.00


2.00


1.00


0


- 1.00


- 2.00


2.00


1.00


0


- 1.00


- 2.00




1.00 0 -1.00 -2.00
∆RA [arcsec]
















1.00 0 -1.00 -2.00
∆RA [arcsec]




1.00 0 -1.00 -2.00
∆RA [arcsec]




1.00 0 -1.00 -2.00
∆RA [arcsec]


Article number, page 51 of 76



Fig. F.6: 05189-2524.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



1.50


0.75


0


- 0.75


- 1.50


1.50


0.75


0


- 0.75


- 1.50


1.50


0.75


0


- 0.75


- 1.50


1.00


0.50


0


- 0.50


- 1.00


1.00


0.50


0


- 0.50


- 1.00




0.75 0 -0.75 -1.50
∆RA [arcsec]


0.50 0 -0.50 -1.00
∆RA [arcsec]
















0.75 0 -0.75 -1.50
∆RA [arcsec]




0.50 0 -0.50 -1.00
∆RA [arcsec]




0.75 0 -0.75 -1.50
∆RA [arcsec]



Fig. F.7: 07251-0248 E.




0.50 0 -0.50 -1.00
∆RA [arcsec]




0.75 0 -0.75 -1.50
∆RA [arcsec]


0.50 0 -0.50 -1.00
∆RA [arcsec]



Fig. F.8: 07251-0248 W.



Article number, page 52 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



2.00


1.00


0


- 1.00


- 2.00


2.00


1.00


0


- 1.00


- 2.00


2.00


1.00


0


- 1.00


- 2.00


2.00


1.00


0


- 1.00


- 2.00

























































Article number, page 53 of 76



Fig. F.9: 09022-3615.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



1.00


0.50


0


- 0.50


- 1.00


1.00


0.50


0


- 0.50


- 1.00


1.00


0.50


0


- 0.50


- 1.00


1.75


0.88


0


- 0.88


- 1.75


1.75


0.88


0


- 0.88


- 1.75




0.88 0 -0.88 -1.75
∆RA [arcsec]





































0.88 0 -0.88 -1.75
∆RA [arcsec]








0.88 0 -0.88 -1.75
∆RA [arcsec]



Fig. F.10: 10190+1322 E.









0.88 0 -0.88 -1.75
∆RA [arcsec]



Fig. F.11: 10190+1322 W.



Article number, page 54 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75















































Article number, page 55 of 76



Fig. F.12: 11095-0238 NE.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75




0.38 0 -0.38 -0.75
∆RA [arcsec]






0.38 0 -0.38 -0.75
∆RA [arcsec]




0.38 0 -0.38 -0.75
∆RA [arcsec]






0.38 0 -0.38 -0.75
∆RA [arcsec]



Fig. F.13: 11095-0238 SW.



Article number, page 56 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs









0.31


0


- 0.31


0.31


0


- 0.31


0.31


0


- 0.31


0.25


0


- 0.25


0.25


0


- 0.25























∆RA [arcsec]





∆RA [arcsec]



∆RA [arcsec]



Fig. F.14: 12071-0444 N.



∆RA [arcsec]



Article number, page 57 of 76













Fig. F.15: 12071-0444 S.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



2.00


1.00


0


- 1.00


- 2.00


2.00


1.00


0


- 1.00


- 2.00


2.00


1.00


0


- 1.00


- 2.00


2.00


1.00


0


- 1.00


- 2.00











































































Fig. F.16: 12112+0305 NE.



Article number, page 58 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs











0.75


0


- 0.75


0.75


0


- 0.75


0.75


0


- 0.75





































Article number, page 59 of 76



Fig. F.17: 12112+0305 SW.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



3.00


1.50


0


- 1.50


- 3.00


3.00


1.50


0


- 1.50


- 3.00


3.00


1.50


0


- 1.50


- 3.00


3.00


1.50


0


- 1.50


- 3.00


3.00


1.50


0


- 1.50


- 3.00




1.50 0 -1.50 -3.00
∆RA [arcsec]




1.50 0 -1.50 -3.00
∆RA [arcsec]




1.50 0 -1.50 -3.00
∆RA [arcsec]




1.50 0 -1.50 -3.00
∆RA [arcsec]



Fig. F.18: 13120-5453.



Article number, page 60 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs









0.25


0


- 0.25


0.25


0


- 0.25


0.25


0


- 0.25


1.00


0


- 1.00


1.00


0


- 1.00





0.25 0 -0.25
∆RA [arcsec]


1.00 0 -1.00
∆RA [arcsec]










0.25 0 -0.25
∆RA [arcsec]






0.25 0 -0.25
∆RA [arcsec]




1.00 0 -1.00
∆RA [arcsec]



Fig. F.19: 13451+1232 W.




1.00 0 -1.00
∆RA [arcsec]




0.25 0 -0.25 -0.50
∆RA [arcsec]


1.00 0 -1.00 -2.00
∆RA [arcsec]


Article number, page 61 of 76



Fig. F.20: 13451+1232 E.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



1.25


0.62


0


- 0.62


- 1.25


1.25


0.62


0


- 0.62


- 1.25


1.25


0.62


0


- 0.62


- 1.25


1.25


0.62


0


- 0.62




































































   - 1.25

0.62 0 -0.62 -1.25
∆RA [arcsec]


Article number, page 62 of 76



0.62 0 -0.62 -1.25
∆RA [arcsec]



0.62 0 -0.62 -1.25
∆RA [arcsec]



0.62 0 -0.62 -1.25
∆RA [arcsec]



Fig. F.21: 14348-1447 SW.

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



1.25


0.62


0


- 0.62


- 1.25


1.25


0.62


0


- 0.62


- 1.25


1.25


0.62


0


- 0.62


- 1.25


1.25


0.62


0


- 0.62


- 1.25



































Article number, page 63 of 76



Fig. F.22: 14348-1447 NE.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



1.50


0.75


0


- 0.75


- 1.50


1.50


0.75


0


- 0.75


- 1.50


1.50


0.75


0


- 0.75


- 1.50







































Fig. F.23: 14378-3651.



Article number, page 64 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



5.00


2.50


0


- 2.50


- 5.00


5.00


2.50


0


- 2.50


- 5.00


5.00


2.50


0


- 2.50


- 5.00















































Article number, page 65 of 76



Fig. F.24: 15327+2340.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



1.00


0.50


0


- 0.50


- 1.00


1.00


0.50


0


- 0.50


- 1.00


1.00


0.50


0


- 0.50


- 1.00


0.25


- 0.25


0.25


- 0.25















Fig. F.25: 16090-0139.

















Fig. F.26: 16156+0146 NW.



Article number, page 66 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



1.50


0.75


0


- 0.75


- 1.50


1.50


0.75


0


- 0.75


- 1.50




0.75 0 -0.75 -1.50
∆RA [arcsec]




0.75 0 -0.75 -1.50
∆RA [arcsec]




0.75 0 -0.75 -1.50
∆RA [arcsec]




0.75 0 -0.75 -1.50
∆RA [arcsec]


Article number, page 67 of 76



Fig. F.27: 16156+0146 SE.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



0.75


0


   - 0.75


0.75


0


   - 0.75


0.75


0


   - 0.75


0.75


0


   - 0.75


0.75 0 -0.75
∆RA [arcsec]


Article number, page 68 of 76




0.75 0 -0.75
∆RA [arcsec]






0.75 0 -0.75
∆RA [arcsec]






0.75 0 -0.75 -1.50
∆RA [arcsec]



Fig. F.28: 17208-0014.

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



1.75


0.88


0


- 0.88


- 1.75


1.75


0.88


0


- 0.88


- 1.75


1.75


0.88


0


- 0.88


- 1.75

























































Article number, page 69 of 76



Fig. F.29: 19297-0406 N.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



1.75


0.88


0


- 0.88


- 1.75


1.75


0.88


0


- 0.88


- 1.75


1.75


0.88


0


- 0.88


- 1.75




0.88 0 -0.88 -1.75
∆RA [arcsec]




0.88 0 -0.88 -1.75
∆RA [arcsec]




0.88 0 -0.88 -1.75
∆RA [arcsec]




0.88 0 -0.88 -1.75
∆RA [arcsec]



Fig. F.30: 19297-0406 S.



Article number, page 70 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75



















































0.38 0 -0.38 -0.75
∆RA [arcsec]



0.38 0 -0.38 -0.75
∆RA [arcsec]



0.38 0 -0.38 -0.75
∆RA [arcsec]



0.38 0 -0.38 -0.75
∆RA [arcsec]


Article number, page 71 of 76



Fig. F.31: 19542+1110.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75




0.38 0 -0.38 -0.75
∆RA [arcsec]
































0.38 0 -0.38 -0.75
∆RA [arcsec]




0.38 0 -0.38 -0.75
∆RA [arcsec]




0.38 0 -0.38 -0.75
∆RA [arcsec]



Fig. F.32: 20087-0308.



Article number, page 72 of 76

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75


0.75


0.38


0


- 0.38


- 0.75



































































0.38 0 -0.38 -0.75
∆RA [arcsec]



0.38 0 -0.38 -0.75
∆RA [arcsec]



0.38 0 -0.38 -0.75
∆RA [arcsec]



0.38 0 -0.38 -0.75
∆RA [arcsec]


Article number, page 73 of 76



Fig. F.33: 20100-4156 SE.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



0.50


0.25


0


- 0.25


- 0.50


0.50


0.25


0


- 0.25


- 0.50


1.00


0.50


0


- 0.50


- 1.00


1.00


0.50


0


- 0.50


- 1.00


1.00




0.25 0 -0.25 -0.50
∆RA [arcsec]




0.25 0 -0.25 -0.50
∆RA [arcsec]




0.50 0 -0.50 -1.00
∆RA [arcsec]




0.25 0 -0.25 -0.50
∆RA [arcsec]



Fig. F.34: 20100-4156 NW.




0.50 0 -0.50 -1.00
∆RA [arcsec]




0.25 0 -0.25 -0.50
∆RA [arcsec]


0.50 0 -0.50 -1.00
∆RA [arcsec]



0.50


0


   - 0.50


   - 1.00

0.50 0 -0.50 -1.00
∆RA [arcsec]


Article number, page 74 of 76



Fig. F.35: 20414-1651.

I. Lamperti et al.: PUMA IV. Spatially resolved cold molecular outflows in ULIRGs



2.50


1.25


0


- 1.25


- 2.50


2.50


1.25


0


- 1.25


- 2.50


2.50


1.25


0


- 1.25


- 2.50

























































Article number, page 75 of 76



Fig. F.36: 22491-1808 E.

_A&A proofs:_ manuscript no. PUMA_CO_outflow_paper_arxiv



2.50


1.25


0


- 1.25


- 2.50


2.50


1.25


0


- 1.25


- 2.50


2.50


1.25


0


- 1.25


- 2.50




1.25 0 -1.25 -2.50
∆RA [arcsec]




1.25 0 -1.25 -2.50
∆RA [arcsec]




1.25 0 -1.25 -2.50
∆RA [arcsec]




1.25 0 -1.25 -2.50
∆RA [arcsec]



Fig. F.37: 22491-1808 W.



Article number, page 76 of 76


</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "0.13-1.05 arcsec (0.14x0.12 to 1.28x0.81 arcsec in Table 2; ~400-500 pc)",
  "failed_quote": "The synthesised beam full width at half-maximum (FWHM) has been selected for each target so that it corresponds to a similar physical spatial resolution for all targets (∼ 400 − 500 pc). As a result, the synthesised beam FWHM are in the range 0.13 − 1.05\"."
 },
 {
  "path": "data.other_facilities[0].provided.evidence[0]",
  "value": "Archival spectra of the OH 119 um doublet transition for 22/25 ULIRG systems",
  "failed_quote": "We collect archival _Herschel_ /PACS spectra of the OH 119µm doublet transition (hereafter OH) for 22/25 of our ULIRGs systems (no data available for 00091-0738, 10190+1322, and 16156+0146)."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "Individual nuclear infrared luminosities and ALMA continuum fluxes",
  "failed_quote": "The individual nuclei have luminosities from log _L_ _IR_ / _L_ ⊙ < 10.5 to log _L_ _IR_ / _L_ ⊙ = 12.7, based on the relative contribution of the nuclei to the total ALMA continuum fluxes (see Pereira-Santaella et al. 2021)."
 },
 {
  "path": "data.external_data_from_literature[2].what.evidence[1]",
  "value": "Position angles of stellar and ionised gas disks, mean dynamical mass, and mean effective radius",
  "failed_quote": "Since estimates of the dynamical masses have been obtained by Perna et al. (2022) only for a subset of our targets (eight objects), we use the mean dynamical mass of the PUMA sample for our calculation ⟨ _M_ _dyn_ ⟩ = 3.9 - 10 [10] M ⊙ ."
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Define [v_min, v_max] for blue and red wings where centroids deviate from rotation and integrated map S/N peaks; fit beam-convolved 2D Gaussian to integrated high-velocity maps to get R_out; extract spectrum within observed R_out and integrate flux in [v_min, v_max] to get F_out, L'_CO, and M_out; compute flux-weighted v_out, mass outflow rate M_dot_out, momentum rate, kinetic luminosity, and esca",
  "failed_quote": "Outflow mass : To derive the outflow mass, we extract the central spectrum from a radius equal to the observed _R_ _out_ (not deconvolved from the beam) and we integrate the flux in the high-velocity channels between _v_ _min_ and _v_ _max_, separately for the blue and the red part of the outflow."
 },
 {
  "path": "analysis_steps[2].assumptions[4].evidence[0]",
  "value": "Truncated isothermal sphere for escape velocity with <M_dyn> = 3.9e10 M_sun, r = 1 kpc, truncation radius = 2 * <R_e> = 4 kpc",
  "failed_quote": "since estimates of the dynamical masses have been obtained by Perna et al. (2022) only for a subset of our targets (eight objects), we use the mean dynamical mass of the PUMA sample for our calculation ⟨ _M_ _dyn_ ⟩ = 3.9 - 10 [10] M ⊙ ."
 },
 {
  "path": "analysis_steps[2].validation.evidence[1]",
  "value": "Tested biases using 3D biconical outflow simulations, subtraction of Gaussian fits to disk rotation, alternative maximum velocity definitions (v_max,FWHM and v_max,FW10), and comparisons with Lutz et al. (2020) and Fluetsch et al. (2019).",
  "failed_quote": "To test how large this contribution could be, we subtract from the spectra the flux due to rotation estimated by modelling the core of the emission profile (with absolute velocities smaller than ∼ 300 km s [−][1] ) with one, two or three Gaussians"
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "Convolved multi-Gaussian fitting with 50 Monte Carlo noise realisations for 16th-84th percentile uncertainties",
  "failed_quote": "then we add random Gaussian noise, proportional to the noise level, to the best-fit model and we run the line fitting on this artificial spectrum. We repeat this procedure 50 times and we use the 16th and 84th percentiles of the distribution of best-fit parameters to estimate the 1σ uncertainties on the derived parameters."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[1]",
  "value": "SFR from L_IR (after removing AGN fraction alpha_AGN) using Kennicutt & Evans (2012) relation with Kroupa & Weidner (2003) IMF; SNe momentum and energy from Kim & Ostriker (2015) and Leitherer et al. (1999)",
  "failed_quote": "We assume that the momentum per supernova is 1.3 × 10 [5] M ⊙ km s [−][1] ×( _n_ 0 /100 cm [−][3] ) [−][0][.][17] (Kim & Ostriker 2015), where _n_ 0 = 100 cm [−][3] is the electron density; and that the supernova rate is 0.012×SFR (M ⊙ yr [−][1] ) for the adopted IMF (Leitherer et al. 1999)."
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Mean outflow mass escape fraction (<f_esc>) = 45 %",
  "failed_quote": "Integrating the CO(2-1) emission at velocities higher than _v_ _esc_, _obs_, we find that between 4 − 100% of the high-velocity gas will escape to the circumgalactic medium, with mean escape fraction ⟨ _f_ _esc_ ⟩ = 45 ± 6%."
 },
 {
  "path": "claims[2].evidence[0]",
  "value": "The molecular outflows are consistent with being momentum-driven and can be powered by supernovae.",
  "failed_quote": "The best linear bisector fit relation has a slope of 2.61 ± 0.25, which implies α = −0.39. The α = −1 scenario (momentum-driven) is within the 1σ uncertainty (see shaded area in Fig. 20), while the α = −2 scenario does not agree with the fit. Therefore, our analysis favours the momentum-driven scenario as the primary launching mechanism for molecular outflows in ULIRGs."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[1]",
  "value": "Subtracting rotating disk emission by fitting central velocity channels with 1-3 Gaussians and measuring outflow in the residuals (tested in Sec. 4.5.2; rejected for main analysis as it underestimates outflow flux at low projected velocities and suffers from complex core profiles).",
  "failed_quote": "To test how large this contribution could be, we subtract from the spectra the flux due to rotation estimated by modelling the core of the emission profile (with absolute velocities smaller than ∼ 300 km s [−][1] ) with one, two or three Gaussians"
 }
]
```
