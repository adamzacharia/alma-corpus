# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...654A..90L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. SUPER_paper ©ESO 2023
August 4, 2023

## ∼
### **SUPER V. ALMA continuum observations of z 2 AGN and the** **elusive evidence of outflows influencing star formation**


I. Lamperti [1][,][ 2][,][ 3][⋆], C. M. Harrison [4][⋆⋆], V. Mainieri [1], D. Kakkad [5][,][ 6], M. Perna [3][,][ 7], C. Circosta [2], J. Scholtz [8], S. Carniani [9],
C. Cicone [10], D. M. Alexander [11], M. Bischetti [12], G. Calistro Rivera [1], C.-C. Chen [13], G. Cresci [7], C. Feruglio [12], F. Fiore [12],
F. Mannucci [7], A. Marconi [14][,][ 7], L. N. Martínez-Ramírez [1][,][ 15], H. Netzer [16], E. Piconcelli [17], A. Puglisi [11], D. J. Rosario [11],
M. Schramm [18], G. Vietri [19], C. Vignali [20][,][ 21], L. Zappacosta [17]


1 European Southern Observatory, Karl-Schwarzschild-Str. 2, 85748 Garching bei München, Germany
2 Department of Physics & Astronomy, University College London, Gower Street, London WC1E 6BT, UK
3 Centro de Astrobiología (CAB, CSIC–INTA), Departamento de Astrofísica, Ctra. de Ajalvir Km. 4, 28850 Torrejón de Ardoz,
Madrid, Spain
4 School of Mathematics, Statistics and Physics, Herschel Building, Newcastle University, Newcastle upon Tyne NE1 7RU, UK
5 European Southern Observatory, Alonso de Cordova 3107, Casilla 19, Santiago 19001, Chile
6 Department of Physics, University of Oxford, Denys Wilkinson Building, Keble Road, Oxford, OX1 3RH, UK
7 INAF - Osservatorio Astrofisico di Arcetri, Largo E. Fermi 5, 50125 Firenze, Italy
8 Chalmers University of Technology, Department of Earth and Space Sciences, Onsala Space Observatory, 43992, Onsala, Sweden
9 Scuola Normale Superiore, Piazza dei Cavalieri 7, I-56126 Pisa, Italy
10 Institute of Theoretical Astrophysics, University of Oslo, P.O. Box 1029, Blindern, 0315 Oslo, Norway
11 Centre for Extragalactic Astronomy, Department of Physics, Durham University, South Road, Durham DH1 3LE, UK
12 INAF - Osservatorio Astronomico di Trieste, via G.B. Tiepolo 11, 34143 Trieste, Italy
13 Academia Sinica Institute of Astronomy and Astrophysics (ASIAA), No. 1, Sec. 4, Roosevelt Rd., Taipei 10617, Taiwan
14 Dipartimento di Fisica e Astronomia, Università di Firenze, Via G. Sansone 1, 50019 Sesto Fiorentino (Firenze), Italy
15 Escuela de Física - Universidad Industrial de Santander, 680002 Bucaramanga, Colombia
16 School of Physics and Astronomy, Tel-Aviv University, Tel-Aviv 69978, Israel
17 INAF – Osservatorio Astronomico di Roma, via di Frascati 33, 00078 Monte Porzio Catone, Italy
18 Graduate school of Science and Engineering, Saitama Univ. 255 Shimo-Okubo, Sakura-ku, Saitama City, Saitama 338-8570, Japan
19 INAF IASF-Milano, Via Alfonso Corti 12, 20133 Milano, Italy
20 Dipartimento di Fisica e Astronomia, Alma Mater Studiorum, Università degli Studi di Bologna, Via Gobetti 93/2, I-40129
Bologna, Italy
21 INAF – Osservatorio di Astrofisica e Scienza dello Spazio di Bologna, Via Gobetti 93/3, I-40129 Bologna, Italy


August 4, 2023


**ABSTRACT**


We study the impact of active galactic nuclei (AGN) ionised outflows on star formation in high-redshift AGN host galaxies, by
combining near-infrared integral field spectroscopic (IFS) observations, mapping the Hα emission and [O iii]λ5007 outflows, with
matched-resolution observations of the rest-frame far-infrared (FIR) emission. We present high-resolution ALMA Band 7 observations
of eight X-ray selected AGN ( _L_ 2−10 _keV_ = 10 [43][.][8] − 10 [45][.][2] erg s [−][1] ) at _z_ ∼ 2 from the SUPER (SINFONI Survey for Unveiling the Physics
and Effect of Radiative feedback) sample, targeting the observed-frame 870 µm (rest-frame ∼ 260 µm) continuum at ∼ 2 kpc (0.2”)
spatial resolution. The targets were selected among the SUPER AGN with an [O iii] detection in the IFS maps and with a detection
in the FIR photometry. We detected six out of eight targets with signal-to-noise ratio S/N≳ 10 in the ALMA maps, from which we
measured continuum flux densities in the range 0.27 − 2.58 mJy and FIR half-light radii ( _R_ _e_ ) in the range 0.8 − 2.1 kpc. The other
two targets were detected with S/N of 3.6 and 5.9, which are insufficient for spatially resolved analysis. The FIR _R_ _e_ of our sample
are comparable to other AGN and star-forming galaxies at a similar redshift from the literature. However, combining our sample with
the literature samples, we find that the mean FIR size in X-ray AGN ( _R_ _e_ = 1.16 ± 0.11 kpc) is slightly smaller than in non-AGN
( _R_ _e_ = 1.69 ± 0.13 kpc). From spectral energy distribution (SED) fitting, we find that the main contribution to the 260 µm flux density
is dust heated by star formation, with ≤ 4% contribution from AGN-heated dust and ≤ 1% from synchrotron emission. The majority
of our sample show different morphologies for the FIR (mostly due to reprocessed stellar emission) and the ionised gas emission (Hα
and [O iii], mostly due to AGN emission). This could be due to the different locations of dust and ionised gas, the different sources
of the emission (stars and AGN), or the effect of dust obscuration. We are unable to identify any residual Hα emission, above that
dominated by AGN, that could be attributed to star formation. Under the assumption that the FIR emission is a reliable tracer of
obscured star formation, we find that the obscured star formation activity in these AGN host galaxies is not clearly affected by the
ionised outflows. However, we cannot rule out that star formation suppression is happening on smaller spatial scales than the ones we
probe with our observations (< 2 kpc) or on different timescales.


**Key words.** galaxies: star formation – galaxies: Seyfert – galaxies: active – galaxies: ISM


Article number, page 1 of 32

_A&A proofs:_ manuscript no. SUPER_paper



**1.** **Introduction**


Super-massive black holes (SMBHs) in the centre of galaxies
have phases of intense accretion of material, during which they
become very luminous and are identified as active galactic nuclei (AGN). AGN release large amounts of energy into the host
galaxies (∼ 10% of the rest-mass energy of the accreted material, Shapiro et al. 1983; Marconi et al. 2004) and therefore
have the potential to influence the properties of the interstellar
medium (ISM) and ultimately its star formation rate (SFR). This
phenomenon is called AGN feedback (e.g. Fabian 2012; King
& Pounds 2015; Harrison 2017). Simulations of galaxy formation require AGN feedback in massive galaxies (stellar masses

- 10 [10] M ⊙ ) in order to match many observables, such as the evolution of galaxy sizes (e.g, Choi et al. 2018), the galaxy colour
bi-modality (Trayford et al. 2016), and the lack of very massive
galaxies in the most massive galaxy haloes (Somerville et al.
2008; Behroozi et al. 2013).
A viable AGN feedback mechanism is represented by fast
winds (> 1000 km s [−][1] ) originating from the AGN accretion disk,
or by collimated radio jets, both of which can impact the surrounding gas, generating outflows which propagate to large distances into the host galaxy (e.g. King 2003; Mukherjee et al.
2018; Costa et al. 2020). These outflows can potentially heat the
ISM and also expel gas from the host galaxy (Ishibashi & Fabian
2016; Zubovas 2018).
AGN outflows have been detected at different scales, extending from a few parsecs to kiloparsecs (e.g Storchi-Bergmann
et al. 2010; Veilleux et al. 2013; Cresci et al. 2015a; Feruglio
et al. 2015; Kakkad et al. 2016; McElroy et al. 2016; Rupke
et al. 2017; Jarvis et al. 2019; Marasco et al. 2020; Kakkad et al.
2020; Vietri et al. 2018, 2020). In addition, outflows have been
observed in multiple gas phases: neutral and ionised as well as
atomic and molecular (Cicone et al. 2018).
Understanding whether these outflows are able to have an
impact on star formation is crucial for testing and refining the
aforementioned simulations, which include a variety of different
models of ‘AGN feedback’. This impact can be particularly important for galaxies at redshift _z_ ∼ 2, which corresponds to the
peak of star formation and AGN activity in the Universe (e.g.
Shankar et al. 2009; Madau & Dickinson 2014; Tacconi et al.
2020).
To study the impact of AGN outflows on star formation, one
possibility is to use spatially resolved observations to map the
distribution of both the outflows and the star-forming regions and
look for spatial correlations or anti-correlations, which can indicate signatures of star formation enhancement (‘positive feedback’) or suppression (‘negative feedback’) (Cresci & Maiolino
2018, and references therein). Using integral field spectroscopy
(IFS) at rest-frame optical wavelengths, several studies investigate the impact of ionised outflows, traced by [O iii]λ5007 ([O iii]
hereafter), on star formation in AGN host galaxies and found evidence of both positive and negative feedback (e.g. Cano-Díaz
et al. 2012; Cresci et al. 2015a; Carniani et al. 2016; Maiolino
et al. 2017; Gallagher et al. 2019; Perna et al. 2020). However,
the interpretation of some of these observations may not be trivial (see Scholtz et al. 2020; Scholtz et al. 2021). For example,
assessing the impact of outflows on star formation can be complicated by the fact that common SFR tracers (e.g. the Hα emission line) are affected by dust extinction (Madau et al. 1996;
Casey et al. 2014; Whitaker et al. 2014). In some objects, the UV
and Hα emission could be completely hidden by the dust (e.g.


⋆ E-mail: isabellalamperti@gmail.com
⋆⋆ E-mail: christopher.harrison@newcastle.ac.uk


Article number, page 2 of 32



Hodge et al. 2016; Chen et al. 2017; Puglisi et al. 2017). Thus, to
have a complete view of the star formation in the host galaxy, it is
crucial to also have information about the dust-obscured star formation traced by the far-infrared (FIR) emission (e.g. Whitaker
et al. 2014; Brusa et al. 2018; Scholtz et al. 2020; Bouwens et al.
2020).
High-resolution observations from the Atacama Large Millimeter/submillimeter Array (ALMA) have been used to measure the FIR sizes of high-redshift star-forming galaxies (e.g.
Ikarashi et al. 2015; Simpson et al. 2015; Hodge et al. 2016;
Gullberg et al. 2019; Puglisi et al. 2019; Cheng et al. 2020).
Several studies found the rest-frame FIR sizes of star-forming
galaxies at _z_ - 1 to be smaller than the rest-frame optical sizes
(e.g. Chen et al. 2015; Barro et al. 2016; Tadaki et al. 2017;
Fujimoto et al. 2017, 2018; Elbaz et al. 2018; Calistro Rivera
et al. 2018; Lang et al. 2019). A possible interpretation is that the
central compact dusty star-forming component is related to the
formation of the bulge (Fujimoto et al. 2017). Alternatively, Popping et al. (2021) suggested, based on simulations, that the larger
rest-frame optical sizes could be due to higher dust-obscuration
in the central region of galaxies, which artificially increases the
ratio between the derived optical and FIR sizes. It is still unclear
whether the presence of an AGN can affect (or is related to) the
FIR size of the host galaxy. For example, Chang et al. (2020)
studied a sample of seven AGN and 20 non-AGN at _z_ ∼ 1 and
found that obscured IR-selected AGN have smaller FIR sizes
(median size _R_ _e_ = 0.76 ± 0.48 kpc) than non-AGN (median size
_R_ _e_ = 1.62 ± 0.50 kpc) at the same redshift and stellar mass. On
the other hand, Harrison et al. (2016b) measured the FIR sizes of
a sample of five X-ray selected AGN at _z_ ∼ 1.5 − 4.5 and found
that their FIR sizes (FWHM size 1 − 3 kpc, median 1.8 kpc) are
comparable to the sizes of sub-millimetre galaxies (SMGs) at the
same redshift (median FWHM size 2.4 ± 0.2 kpc).
This paper is part of a series of papers from SUPER [1] (SINFONI Survey for Unveiling the Physics and Effects of Radiative feedback, Circosta et al. 2018), an ESO large programme
which aims to investigate the outflows properties of _z_ ∼ 2 Xray AGN. The high resolution (∼ 0.2 − 0.3 [′′], corresponding to

∼
2 kpc) of the IFS SINFONI observations is critical to resolve
the morphology of the ionised outflow (Kakkad et al. 2020) and
connect it with the star formation properties of the host galaxy.
In this work, we study the impact of AGN ionised outflows on
both obscured and unobscured star formation in a sub-sample of
eight SUPER AGN. We combine SINFONI IFS observations,
to map the Hα emission and [O iii] outflows, with matchedresolution ALMA observations of the continuum FIR emission
at λ _obs_ ∼ 870 µm (λ _rest_ ∼ 260 µm).
The paper is organised as follows. In Section 2, we describe
the selection criteria and the general properties of the sample.
In Section 3, we present the ALMA data and the analysis to extract the information about the FIR sizes and flux densities. Section 4 describes the SINFONI Hα and [O iii] data. In Section 5
we present our results. First, we investigate the origin of the FIR
emission in our targets (Sec. 5.1). Then, we compare the FIR
sizes with other samples from the literature (Sec. 5.2). Finally,
we compare the spatial distribution of the FIR continuum with
the Hα and [O iii] emission, as well as with the ionised outflows
(Sec. 5.3 and 5.4). In Section 6, we summarise the main results
and our conclusions.

Throughout this work, we assume wavelength in vacuum and
a cosmological model with Ω λ = 0.7, Ω M = 0.3, and _H_ 0 = 70
km s [−][1] Mpc [−][1] .


1 http://www.super-survey.org

I. Lamperti et al.: SUPER V: obscured star formation and outflows



**2.** **Sample**


The sample studied in this paper consists of eight AGN with
ALMA Band 7 continuum observations, which have been selected from the SUPER parent sample. The sample selection
of SUPER is described in detail in Circosta et al. (2018). In
brief, the 39 SUPER AGN were selected in the X-rays from various surveys, by adopting as a threshold an absorption-corrected
X-ray luminosity of _L_ _X_ ≥ 10 [42] erg s [−][1], to exclude sources
where the X-ray emission may come from star formation (Aird
et al. 2017). The SUPER sample covers the redshift range _z_ =
2 − 2.5 and spans a wide range of AGN bolometric luminosities [2] (∼ 10 [44] − 10 [48] erg s [−][1] ) and X-ray luminosities ( _L_ 2−10 _keV_ ∼
10 [43] −10 [46] erg s [−][1] ). To select the sub-sample to be observed with
ALMA, we considered all the SUPER objects with at least one
photometric detection, based on the photometry we had in hand
(i.e. a signal-to-noise S/N - 3 in the catalogue from Circosta
et al. 2018) in the FIR (i.e. observed wavelength in the range
70 − 870 µm), to be able to properly assess the emission process
at 870 µm (observed wavelength), and with [O iii] detections in
the completed IFS data at the time of the proposal (April 2018),
to be able to investigate the impact of [O iii] outflows on the dustobscured star formation. The eight SUPER targets that satisfied
these criteria were selected for the ALMA observations.
Our sample includes five AGN from the COSMOS-Legacy
survey (Civano et al. 2016; Marchesi et al. 2016), two from the
_Chandra_ Deep Field South (CDF-S, Luo et al. 2017), and one
from the wide-area XMM-Newton XXL survey (Pierre et al.
2016). A summary of the sample characteristics is provided in
Table 1.
Given the selection criteria based on the FIR and [O iii] properties described above, it is important to consider how this subsample is representative of the parent population of the SUPER
survey. Figure 1 shows the AGN bolometric luminosities ( _L_ _bol_ )
and hydrogen column densities ( _N_ _H_ ) for the total SUPER sample, with the ALMA targets highlighted in orange. Bolometric
luminosities are derived from SED fitting and _N_ _H_ from the analysis of the X-ray spectra (for more details see Circosta et al.
2018). The ALMA targets have bolometric luminosities in the
range log( _L_ _bol_ /[erg s [−][1] ]) = 44.9−46.8, with median log( _L_ _bol_ /[erg
s [−][1] ]) = 45.8. They are therefore representative in terms of
bolometric luminosities of the parent SUPER sample (median
log _L_ _bol_ /(erg s [−][1] ) = 46.0 and interquartile range log( _L_ _bol_ /[erg
s [−][1] ]) = 45.4 − 46.5).
Most of the ALMA targets have relatively high hydrogen
column densities (log( _N_ _H_ /cm [−][2] ) = 23.1 − 24.3), with the exception of X_N_81_44, which has an upper limit (log( _N_ _H_ /cm [−][2] ) <
21.9). The three ALMA targets with the lowest _N_ _H_ are classified
as optical broad line (Type 1) AGN. Our ALMA sample includes
7/8 (88%) obscured sources (based on log( _N_ _H_ /cm [−][2] ) - 22;
Mainieri et al. 2002; Szokoly et al. 2004), compared to 54% in
the parent sample, and 5/8 (63%) optical Type 2 (narrow line)
AGN, compared to 41% in the parent sample. However, if we
consider only SUPER targets with photometric coverage in the
FIR, 18/26 (70%) have log _N_ _H_ /cm [−][2] - 22 and 15/26 (58%) are
classified as optical Type 2 AGN. The targets with FIR observations are biased against unobscured (Type 1) AGN. This is
due to the fact that Type 1 targets in SUPER are mostly located
in the XMM-XXL, WISSH and Stripe82X fields, which do not
have a good FIR coverage: WISSH and Stripe82X do not have
FIR photometric observations available and XMM-XXL has FIR


2 AGN bolometric luminosities are derived from the fit of the multiwavelength spectral energy distributions (SEDs) (for details, see Circosta et al. 2018).



coverage for only some of the targets. On the contrary, the CDFS and COSMOS fields have good FIR coverage, and the SUPER
targets in those fields are biased towards Type 2 objects (73% of
the objects, compared to 41% in the total SUPER sample) which
is expected given that these two fields have the deepest X-ray observations (e.g. Mainieri et al. 2002). We conclude that the high
_N_ _H_ values of our sample are likely due to the fact that obscured
targets are preferentially located in the two fields (COSMOS and
CDF-S) with good FIR photometry.
In summary, although the ALMA sample presented in this
paper has bolometric luminosities which are representative of
the parent sample, we are biased towards heavily obscured (high
_N_ _H_ ) and Type 2 targets. We discuss how representative our
ALMA sample is in terms of SFRs and stellar masses in section 3.4.


**3.** **ALMA observations and analyses**


We use FIR continuum observations from ALMA with the goal
of tracing the dust obscured star formation at the same resolution (∼2 kpc) as the [O iii] and Hα emission line maps extracted
from our SINFONI IFS data. The ALMA Band 7 continuum observations used in this work belong to the Cycle 6 observing
programme ID 2018.1.00992.S (P.I: C. M. Harrison).
Observations were taken between 18 October and 5 November 2018. The on-source integration time for each target is between 14 and 70 minutes. The observations were performed with
45 − 49 antennas, with baselines in the range 15.1 − 2500 m.
The Band 7 870µm continuum observations correspond to restframe 250-277 µm for our sources. The requested angular resolution was 0.15-0.30”, to match the resolution of the SINFONI
observations. The maximum recoverable scales are in the range
1.9 − 2.8”. The field of view is ∼ 17”.


_3.1._ _Data reduction and imaging_


We reduced the data using the Common Astronomy Software
Application ( `CASA` ) version 5.4.0. The calibrated measurement
sets were created using the standard ALMA pipeline provided
with the raw data in the ALMA archive. We used the `CASA` task
`fixvis` to phase-centre the calibrated measurement set on the
central position of the source, determined by fitting a 2D Gaussian profile on the reduced image provided by the ALMA datareduction pipeline.
We produced an image of the calibrated measurement set using the `CASA` task `tclean` . We measured the RMS (root mean
square) noise from the dirty image (obtained without applying
the primary-beam correction), excluding the emission from the
sources. We set the cleaning threshold of `tclean` to 2×RMS
and the pixel size to be one fifth of the beam size. In three cases
(cid_451, cid_1205 and cid_1143), there is a secondary source
in the field of view. The secondary sources are at a distance of
∼ 2.5", 8" and 9" from the primary target for cid_1205, cid_451
and cid_1143, respectively. We modelled the secondary source
with a 2D Gaussian and then we removed it from the _uv_ -data
using the `CASA` task `uvsub` . We note that in all cases the presence of the secondary source does not affect significantly our
size measurements. We also tested that fitting the two sources
simultaneously in the _uv_ -plane gives consistent results.
One of our aims is to compare location, sizes and morphologies between the FIR emission, measured from the ALMA maps,
and the ionised gas emission, measured with SINFONI. Thus,
we want to create ALMA maps with a similar resolution to


Article number, page 3 of 32

_A&A proofs:_ manuscript no. SUPER_paper


Table 1: Properties of the sample. All quantities are taken from Circosta et al. (2018), except for the SFRs and stellar masses which
have been derived from the SED fitting including the Band 7 fluxes presented in this paper (see Section 3.4). (1) Field where the
targets are located; (2) Source identification number from the catalogues corresponding to each field; (3) RA and (4) Dec of the
optical counterpart; (5) Spectroscopic redshift; (6) AGN classification as broad line (BL) or narrow line (NL) objects according to
the optical spectra; (7) Host galaxy stellar mass and 1σ error; (8) SFR from the 8-1000µm FIR luminosity and 1σ error; (9) AGN
bolometric luminosity and 1σ error, derived from SED fitting; (10) Absorption-corrected X-ray luminosity in the hard band (2-10
keV) and 90% confidence level error; (11) Absorbing hydrogen column density and 90% confidence level error, derived from either
X-ray spectral fitting or hardness-ratio (see Circosta et al. 2018).


Field ID RA Dec z AGN log M ∗ SFR log L bol log L 2-10keV log N H

[deg] [deg] type [log M ⊙ ] [ M ⊙ yr [−][1] ] [erg s [−][1] ] [erg s [−][1] ] [cm [−][2] ]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11)
XMM-XXL X_N_81_44 34.378942 -4.306572 2.311 BL 10.89±0.25 173±92 46.80±0.03 44.77 [+] − [0] 0 [.] . [07] 09 < 21.86
CDF-S XID36 52.961556 -27.784281 2.259 NL 10.72±0.08 186±9 45.70±0.06 43.84 [+] − [0] 0 [.] . [31] 63 - 24.10
CDF-S XID419 53.097649 -27.715270 2.145 NL 10.89±0.02 44±2 45.54±0.05 43.84 [+] − [0] 0 [.] . [29] 44 24.28 [+] − [0] 0 [.] . [19] 31
COSMOS cid_1057 149.812485 2.111014 2.214 NL 10.99±0.08 64±7 45.91±0.06 44.53 [+] − [0] 0 [.] . [26] 30 23.98 [+] − [0] 0 [.] . [24] 28
COSMOS cid_346 149.930878 2.118734 2.219 BL 10.67±0.37 380±29 46.66±0.02 44.47 [+] − [0] 0 [.] . [08] 09 23.05 [+] − [0] 0 [.] . [17] 19
COSMOS cid_451 150.002533 2.258629 2.450 NL 11.21±0.05 48±19 46.44±0.07 45.18 [+] − [0] 0 [.] . [23] 19 23.87 [+] − [0] 0 [.] . [19] 15
COSMOS cid_1205 150.010696 2.332968 2.255 BL _[a]_ 11.16±0.22 88±16 45.75±0.17 44.25 [+] − [0] 0 [.] . [21] 23 23.50 [+] − [0] 0 [.] . [27] 27
COSMOS cid_1143 150.036819 2.257776 2.492 NL 10.82±0.04 8±2 44.85±0.12 44.83 [+] − [0] 0 [.] . [43] 36 24.01 [+] − [0] 0 [.] . [77] 29
( _a_ ) cid_1205 was previously reported as a NL target in Circosta et al. (2018), but it is now classified as a BL target based on the
presence of BLR emission in the Hα line in the K-band SINFONI spectrum (Kakkad et al. 2020).



48.0


47.5


47.0


46.5


46.0


45.5


45.0


44.5


44.0


|Col1|Col2|
|---|---|
|||



20 21 22 23 24 25
log (N H /cm [−][2] )



3.0











log M ∗ [M ⊙ ]





Fig. 1: _Left:_ AGN bolometric luminosity versus hydrogen column density ( _N_ _H_ ) for the SUPER sample. ALMA targets from this
work are marked with orange squares. Targets classified as broad line AGN in the optical are marked with black contours. The
dashed line at log( _N_ _H_ /cm [−][2] ) = 22 marks the separation between X-ray unobscured and obscured AGN. _Right:_ SUPER sample in
the star formation rate (SFR) vs. stellar mass ( _M_ ∗ ) plane. Only the 24/39 objects with SFR and stellar mass constraints are shown.
The size of the systematic uncertainties is shown on the top left corner. The black dashed curve shows the main sequence (MS)

∼
of star-forming galaxies from Schreiber et al. (2015) at the average redshift of our target sample (z 2.3), the 0.3 dex dispersion is
showed by dotted lines. Most of the ALMA targets are consistent with being on the MS, with the exception of cid_1143, which lies
below.



∼
the SINFONI IFS maps (FWHM PSF 0.3"). We generated the
maps using the Briggs weighting scheme with robust parameter
= 2 (corresponding to natural weighting). The beam sizes obtained using natural weighting are in the range 0.17-0.25” and
closely match the resolution of the SINFONI maps. We also created maps using the Briggs weighting scheme with robust = 0.5
(higher resolution, beam size 0.16-0.20”) and we found no appreciable difference in the morphology and size of the FIR emission that would affect our conclusions. Therefore we decided to
use the maps obtained with natural weighting for the rest of the
analysis. We show these final ALMA maps in Figure 2.


We re-measured the RMS from the ‘clean’ maps produced
with natural weighting. The RMS are in the range 15-31 µJy


Article number, page 4 of 32



beam [−][1] . We measured the peak signal-to-noise ratio (S/N) of the
sources by dividing the peak flux density by the RMS. The S/N
values vary between 3.6 and 29. Two of the targets (cid_1057
and cid_451) have low S/N (<< 10), and therefore we cannot derive reliable size measurements for these objects (Simpson et al.
2015). We highlight these two targets with low S/N in all the relevant figures. The beam size, RMS, and peak signal-to-noise of
the ALMA images are summarised in Table 2.

I. Lamperti et al.: SUPER V: obscured star formation and outflows



2


1


0


1


2


3


2

0


-2



0.5


0


-0.5


0.5


0


-0.5


0.5


0


-0.5


0.5


0


-0.5



1 0.5 0 -0.5 -1
∆R. A. [arcsec]


1 0.5 0 -0.5 -1
∆R. A. [arcsec]


1 0.5 0 -0.5 -1
∆R. A. [arcsec]


1 0.5 0 -0.5 -1
∆R. A. [arcsec]



0.4


0.6


0.5
0

-0.5



best model : point
low S/N



best model : exponential
R e = 0.10 ± 0.01" = 0.85 ± 0.10 kpc

point


Gaussian

Gaussian + point



0 500 1000 1500
UV − distance [kλ]



2.0


1.5


1.0


0.5


0.0


0.5


1.0


1.5


2

0


-2



best model : exponential
R e = 0.12 ± 0.01" = 1.03 ± 0.11 kpc



0 500 1000 1500
UV − distance [kλ]


1.0


0.5


0.0


0.5


1.0



1.5


2

0


-2



best model : Gaussian
R e = 0.10 ± 0.01" = 0.80 ± 0.12 kpc



0 500 1000 1500
UV − distance [kλ]


0.6


0.4


0.2


0.0


0.2



0 500 1000 1500 2000
UV − distance [kλ]



Fig. 2: _Left column:_ Maps of the ALMA continuum. The white ellipse represents the ALMA beam. The peak S/N is also shown. Contours start at
2σ and increase at intervals of 2σ. Dashed contours are negative contours at -2σ. The lightblue line indicates the position angle along the major
axis of the FIR emission, when it can be reliably determined (see Section 3.3.1). _Right column:_ Real part of the visibilities versus _uv_ -distance. The
overlaid straight and curved lines show the fit using different models: point source (dotted lightblue line), exponential (dashed red curve), Gaussian
(dashed-dotted blue curve), and Gaussian profile plus point source (solid magenta curve). The best model according the Bayesian Information
Criterion (BIC) is labelled in each case. The shaded area shows the 1σ uncertainties on the best fit model. The lower panel shows the residuals
with respect to the best-fit model.


Article number, page 5 of 32

_A&A proofs:_ manuscript no. SUPER_paper


4



best model : Gaussian + point
R e (tot) = 0.19 ± 0.01" = 1.60 ± 0.10 kpc
R e (Gauss. ) = 0.22 ± 0.01" = 1.81 ± 0.10 kpc



0.5


0


-0.5


0.5


0


-0.5


0.5


0


-0.5


0.5


0


-0.5



1 0.5 0 -0.5 -1
∆R. A. [arcsec]


1 0.5 0 -0.5 -1
∆R. A. [arcsec]


1 0.5 0 -0.5 -1
∆R. A. [arcsec]


1 0.5 0 -0.5 -1
∆R. A. [arcsec]



3


2


1


0


2

0


-2



0 200 400 600 800 1000 1200 1400
UV − distance [kλ]


0.5


0.0


0.5

best model : exponential
R e = 0.26 ± 0.05" = 2.14 ± 0.41 kpc


1

0


-1


0 200 400 600 800 1000 1200 1400
UV − distance [kλ]



0 200 400 600 800 1000 1200
UV − distance [kλ]



0.6


0.4


0.2


0.0


0.2


0.4


0.6


0.8


1

0


-1



best model : exponential
R e = 0.27 ± 0.07" = 2.22 ± 0.56 kpc
low S/N



0 200 400 600 800 1000 1200 1400
UV − distance [kλ]



0.6


0.4


0.2


0.0


0.2


0.4


1


0


-1



best model : point



Fig. 2: Continued.



_3.2._ _Modelling the ALMA continuum data: sizes and flux_
_densities_


In this section, we describe how we measure the sizes and
flux densities of the 260 µm (rest-frame) emission. In particular, we are interested in comparing the 260 µm sizes with FIR


Article number, page 6 of 32



sizes of literature samples, to test whether AGN show different sizes compared to non-AGN. We also want to compare the
FIR sizes with the sizes of the optical emission-line regions (Hα
and [O iii]), to investigate whether they are tracing similar spatial
scales.

I. Lamperti et al.: SUPER V: obscured star formation and outflows


Table 2: Properties of the ALMA maps and measurement of FIR sizes and flux densities at rest-frame ∼ 260 µm. (1) Synthesized
beam size (FWHM) of the ALMA maps created with Briggs weighting with robust=2. (2) RMS noise (measured from the ‘clean’
maps). (3) Peak signal-to-noise in the ALMA map. (4) Best fit model to the _uv_ -visibility data, according to the Bayesian Information
Criterion (BIC). ( [⋆] ) If the peak _S_ / _N_ < 8 in the ALMA maps, we do not consider the size measurements to be reliable. (5) Flux
density at rest-frame ∼ 260 µm, measured from the _uv_ -visibilities using the best model. (6) Half-light radius (deconvolved from the
beam) in arcsec measured from the _uv_ -visibilities using the best model. For cid_1057 the radius is not reported due to the low S/N.
(7) Half-light radius in kpc. (8) Axial ratio measured using `uvmodelfit` (excluding point sources). Axial ratios consistent with
one are marked with [∗] . (9) Position angle (P.A.) measured using `uvmodelfit` for the objects with axial ratios significantly different
from one. The P.A. measures the angle of the major axis with respect to the north in anti-clockwise direction. (10) AGN contribution
to the rest-frame 260 µm ALMA flux, estimated from the SED fit. (11) Contribution from synchrotron emission to the rest-frame
260 µm ALMA flux. We model the synchrotron emission as a power law with a spectral index α _r_ . (12) Spectral index α _r_ used to
estimate the synchrotron contribution, calculated from the 1.4, 3 and 5.5 GHz data (when available). In the cases where we could
not constrain α _r_ with the available data, we assume α _r_ = −0.7 (see Sec. 5.1).


ID Beam size RMS S/N best model F(260 µm) R _e_ R _e_ axial ratio P.A. _f_ _AGN_ _f_ _sync_ α _r_

[arcsec [2] ] [µJy beam [−][1] ] [mJy] [arcsec] [kpc] [deg.] % %
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12)

X_N_81_44 0.23×0.22 31.44 22.7 exponential 1.13±0.16 0.10±0.01 0.83±0.10 1.00±0.11 [∗]  - < 1 < 1 -0.70
XID36 0.22×0.21 26.62 21.5 exponential 1.05±0.13 0.12±0.01 1.00±0.10 1.22±0.12 [∗]  - 3 < 1 -1.25
XID419 0.22×0.21 23.49 9.8 Gaussian 0.43±0.05 0.10±0.01 0.79±0.12 2.9±0.8 88±5 4 < 1 -0.70
cid_1057 0.18×0.16 16.34 3.6 [⋆] point 0.06±0.02  -  -  -  - 3 < 1 -0.70
cid_346 0.27×0.22 31.40 29.0 Gauss.+point 2.58±0.14 0.19±0.01 1.61±0.09 1.3±0.1 2±5 < 1 < 1 -0.98
cid_451 0.26×0.23 16.25 5.9 [⋆] exponential 0.29±0.09 0.24±0.07 1.98±0.55 3.1±0.8 -58±5 6 21 -0.99
cid_1205 0.25×0.25 16.20 16.6 point 0.27±0.02 < 0.12 < 2.06  -  - < 1 < 1 -0.70
cid_1143 0.25×0.23 14.76 12.1 exponential 0.46±0.11 0.25±0.05 2.01±0.41 4.6±0.7 23±2 < 1 < 1 -0.70



We tested models describing different morphologies (e.g.
point source, exponential disk profile) to extract reliable size and
flux density measurements. We measured the sizes both from the
visibilities and in the image plane. Measuring the sizes directly
from the _uv_ -visibilities has the advantage that it is not dependent on the choices made to create the images (e.g. weighting
scheme, cleaning threshold, ...). For completeness, all of the size
measurements using the different methods are shown in the appendix in tables B.1 and B.2.


First we used the `CASA` routine `uvmodelfit` to fit a model directly to the visibilities. The models available with `uvmodelfit`
are a point source, a 2D Gaussian and an elliptical disk. We ran
`uvmodelfit` on the phase-centred calibrated measurement sets
assuming a 2D Gaussian model and using 20 iterations, which
are enough to reach convergence. We note that `uvmodelfit`
measures the intrinsic sizes, deconvolved from the beam. The
results from `uvmodelfit` also provide the information on the
ratio of the major and minor axis (see Table 2).


We also performed a fit on the collapsed visibilities using
python outside of `CASA`, which gives us more freedom in the
choice of models. We extracted the visibility amplitudes from the
phase-centred calibrated measurements sets. Then, we binned
the data in _uv_ -distance intervals of 50 kλ. We measured the average of the visibilities at each _uv_ -distance, weighted by the corresponding uncertainties. The uncertainty on each mean visibility is given by the standard deviation of the mean divided by
the square root of the number of visibility points in that bin. In
Figure 2 we show the visibility amplitudes as a function of _uv_ distance for our sample.


For simplicity, we only considered symmetrical models, that
is an axial ratio of one. We note that the radii derived with symmetrical Gaussian models are consistent with the mean radii
measured with `uvmodelfit` . We tested the following models:
point source, 2D Gaussian, 2D Gaussian plus a point source,
and exponential profile (equivalent to a Sérsic profile with index
_n_ = 1).



To fit the visibilities versus _uv_ -distances, we used the Markov
chain Monte Carlo (MCMC) program `Stan` [3] (Carpenter et al.
2017), which allows us to accurately estimate the uncertainties
on the derived parameters. Specifically, we employed `PyStan` [4],
the python interface to `Stan` . We assumed a Gaussian likelihood
and use uniform priors, allowing the free parameters to vary in a
large parameter range (the prior ranges are tabulated in Table A.1
in the appendix).
We derived the best fit parameters by taking the median values from the marginal posterior distributions. The uncertainties are given as the 16th and 84th percentiles of the posterior distributions. We express all sizes in terms of half-light
radius (also known as effective radius) _R_ _e_ . For a 2D Gaussian, _R_ _e_ is equivalent to 0.5×FWHM. For the exponential profile
_I_ ( _R_ ) = exp (− _R_ / _a_ ), where _a_ is the scale parameter, _R_ _e_ is given
by 1.6783 × _a_ . For the model with Gaussian plus point source,
we calculate the radius that contains half of the light based on
the total profile derived from the fit, _R_ _e_ (tot). We also report the
value of _R_ _e_ for the Gaussian component only, _R_ _e_ (Gauss.).
The results from our fit on the visibilities using a Gaussian model are consistent within the uncertainties with the results from `uvmodelfit` both in terms of sizes and flux densities.
Therefore, for the rest of this work we use the flux densities and
size measurements from our analysis of the collapsed visibility
amplitude versus _uv_ -distance performed in python.
To assess the preferred model to fit our data, we use the
Bayesian Information Criterion (BIC; Schwarz 1978):


_BIC_ = −2 · ln _L_ + _q_ - ln( _m_ ), (1)


where _L_ is the likelihood (i.e. the probability of the data given
the parameters), _q_ is the number of free parameters of the model,
and _m_ is the number of data points. The BIC considers the likelihood of the model and penalises models with a larger number
of parameters. The model with the smallest BIC is the preferred


3 http://mc-stan.org/
4
http://pystan.readthedocs.io/en/latest/http://mc- stan.org


Article number, page 7 of 32

_A&A proofs:_ manuscript no. SUPER_paper



model [5] . Figure 2 shows the visibilities versus _uv_ -distances data
with the curves showing the different models fitted. The preferred model is highlighted with a thicker line.
At least a S/N≳ 10 on the flux is required to obtain reliable
size measurements (Simpson et al. 2015). XID419 has S/N= 9.8
and is therefore a borderline case. Given the good agreement in
the size measured with different methods for this source, we consider the size measurements to be reliable. cid_1057 and cid_451
have very low S/N (3.6 and 5.9, respectively), therefore we do
not consider the size measurements of these two targets to be reliable. However, for completeness we show their values throughout the figures, and we highlight them as unreliable. For these
two sources, the flux densities measured from the _uv_ -visibilities
are more uncertain. Thus, we also check the flux densities derived from the ALMA images created by applying tapering (with
tapering size = 0.5") using `CASA` . The peak flux densities measured in the tapered images are in agreement (within the uncertainties) with the ones measured from the fit of the _uv_ -visibilities.
We verify that we obtain consistent results by performing the
analysis also in the image plane, using the 2D Gaussian fitting
routine available in the `CASA` `viewer` . The sizes and flux densities measured in the image plane are in agreement with the
measurements done in the _uv_ -plane using the Gaussian model.
For more details on the comparison between different methods,
see Section B of the appendix.
The sizes and flux densities measured with the different
methods are reported in tables B.1 and B.2 in the appendix.The
measurements done in the image plane, with `uvmodelfit`, and
fitting the _uv_ -visibilities with the ‘preferred model’ are in general agreement (see Figure B.1 in the appendix). We consider
as our ‘best measurements’ the FIR sizes and flux densities derived from the fit of the _uv_ -visibilities with the ‘preferred model’
(reported in Table 2). Given the general agreement between the
different methods, the choice of the method does not affect our
results. Nevertheless, we provide the information on the sizes
measured with the different methods to ease the comparison with
literature values (see Section 5.2).


_3.3._ _FIR sizes, morphologies, and flux densities_


3.3.1. FIR sizes and morphologies


The effective radii derived from the ‘best fit’ models for our sample are in the range 0.80-2.13 kpc, with a median of 1.31 ± 0.23
kpc [6] . The sizes measured from the fit with an exponential profile
are larger than the sizes derived assuming a Gaussian profile by
a factor of 1.38 on average (for the extended sources). This is by
construction, since the exponential profile decreases less rapidly
toward zero at larger radii than the Gaussian profile and therefore there is a larger fraction of flux at large distances. However,
we note that our conclusions do not change if we choose one
of these models for all sources. To facilitate comparison with
literature values (where both these models are considered), we
provide the results from both models in Appendix B.
Half of the sources with reliable size measurements (3/6) are
best described by an exponential profile according to the BIC.
One source (cid_1205) is better described by a point source and
one source (XID419) by a Gaussian. The preferred model for
cid_346 is a Gaussian plus a point source. The point source ac

5 We note that using the Akaike Information Criterion (AIC) or the
Akaike Information Criterion corrected for sample size (Akaike 1973,
1974) will give the same qualitative results.
6 The error on the median is calculated as the standard deviation of the
measurements divided by the square root of the number of objects.


Article number, page 8 of 32



counts for 13.5% of the total flux density, according to the results of our fit. For this source, we also test a model consisting
of an exponential profile plus a point source. This model gives
a point source contribution to the total flux of 4.1%, but it is
not preferred over the ‘Gaussian plus point source’ or the ‘exponential profile’ model, according to the BIC. The point source
component could be either due to the emission from a compact
starburst or from the AGN. From our SED fitting decomposition,
the AGN component contributes only 0.15% to the total 260 µm
flux density, thus it cannot account for all the flux of the observed
point source. Therefore, a compact star-forming region may be
a more likely scenario. Since we have only two objects which
require a point source in the model, and in the case of cid_346
its contribution to the total flux is marginal, we consider this as
an indication that on average point source emission from AGN
heated dust at this wavelength is not prominent (see Section 5.1
for further discussion on the origin of the FIR emission).
The ratios between the major and minor axis derived using
`uvmodelfit` for the 6/8 sources with high S/N are in the range
1−4.6. For two sources (X_N_81_44 and cid_1205) the axial ratio is consistent with one. For XID_419, cid_346, and cid_1143
the difference in the sizes of the major and minor axes show that
the emission is significantly elongated in one direction (axial ratio - 1.3). For these three sources, we report also the position
angle measured with `uvmodelfit` (see Table 2).


3.3.2. Flux densities


The flux densities measured with the different methods are in
agreement within the uncertainties (see Figure B.1). The only
exception is cid_346, for which the `uvmodelfit` Gaussian fit
gives a slightly smaller flux (8%) than the other methods. This is
probably because the Gaussian model cannot well describe the
point source emission in the centre, and therefore misses part of
the flux.
Our high-resolution ALMA images are potentially missing
some of the more diffuse emission, and therefore the measured
flux densities cannot be considered as ‘total’ flux densities. For
example, Harrison et al. (2016b) found a drop in peak flux of
18 − 44% between a resolution of 0.8” and 0.3”. To assess how
much flux we are potentially missing in our ALMA data, we
compare these flux measurements with other 260 µm flux measurements from lower resolution data from the ALMA Archive
(compiled by Circosta et al. 2018) and from Scholtz et al.
(2020). Three sources have 260 µm fluxes from lower resolution
data. XID419 has an upper limit from Scholtz et al. (2020), that
is consistent with our measurement. For cid_451 and cid_1205,
our flux density measurements are consistent within the uncertainties with the 260 µm flux densities from the low-resolution
data. Therefore, there is no evidence that the ALMA images are
resolving out a large portion of the flux.


_3.4._ _SED fits including the ALMA flux densities_


In this section, we fit the spectral energy distributions (SEDs) of
our targets to estimate the stellar masses and SFRs of their host
galaxies. We used the UV-FIR photometric catalogue from Circosta et al. (2018) and we added the ALMA band-7 flux densities. Given the large number of upper limits and the large PSF of
the _Herschel_ images, including the ALMA fluxes helps to place
better constraints on the properties of the host galaxies. Moreover, in section 5.1 we use these best-fit SED models to estimate
the AGN contribution to the ∼ 260 µm flux densities.

I. Lamperti et al.: SUPER V: obscured star formation and outflows



In addition to including the ALMA photometry, we took a
conservative approach for the weakly detected or possibly contaminated _Herschel_ sources; specifically, we considered the Herschel fluxes as upper limits for X_N_81_44, cid_1057, cid_1205
and cid_1143. However, if we use the full photometry catalogue
used in Circosta et al. (2018), even excluding the ALMA Band
7 photometry, we reach the same conclusions in terms of AGN
contributions (see Section 5.1).
We use the same SED fitting approach used by Circosta et al.
(2018) for the full SUPER sample, with the only difference that
we include the ALMA band 7 photometry. Circosta et al. (2018)
performed the panchromatic (UV-to-FIR) SED fitting using the
Code Investigating GALaxy Emission ( `CIGALE` ; Burgarella et al.
2005; Noll et al. 2009; Boquien et al. 2019). This code takes into
account the energy balance between the absorption by dust in
the UV-optical and the corresponding re-emission in the FIR.
The SED model includes three emission components: i) stellar
emission; ii) emission by cold dust heated by star formation; iii)
AGN emission, consisting in direct emission from the accretion
disk in the UV-optical range and emission from the dusty torus
peaking in the mid-infrared (MIR). For more details on the SED
fitting method we refer the reader to Circosta et al. (2018).
The SFRs are estimated from the infra-red (IR) luminosity,
obtained by integrating the best-fit template SED in the restframe wavelength range 8-1000 µm, after removing the AGN
contribution. The IR luminosity is converted to SFR using the
Kennicutt (1998) calibration, converted from a Salpeter IMF to
a Chabrier (2003) IMF by subtracting 0.23 dex (Bolzonella et al.
2010) [7] . Figure E.1 in the appendix shows the SEDs with the results from the SED fitting and the measured ALMA 260 µm flux
densities. The SFR and stellar masses derived from these SED
fits are reported in Table 1.
We compare the SFR and stellar masses derived from the
SED including the ALMA data with the values reported in Circosta et al. (2018). The SFRs vary by less than 0.13 dex for all
targets except for cid_1205 (-0.6 dex) and cid_1143 (-1.2 dex).
The large difference for cid_1143 can be explained by the fact
that the _Herschel_ fluxes are all upper limits, thus the previous
SFR needs to be considered as an upper limit. For cid_1205,
the _Herschel_ fluxes used to calculate the previous SFR value included also the flux from the companion galaxy, thus the previous SFR was an upper limit. For cid_451, only an upper limit
on the SFR (< 125 M ⊙ yr [−][1] ) was reported in Circosta et al.
(2018) due to the possible high contamination from synchrotron
emission to the FIR fluxes. This target is classified as a radioloud source based on the comparison between infrared and radio luminosity. We take advantage of the ALMA Band 3 flux
measurement at rest-frame 1 mm recently presented in Circosta
et al. (2021) to better constrain the contribution from the AGN
synchrotron emission to the FIR fluxes (see Sec. 5.1). We remeasure the SFR after subtracting the synchrotron contribution
from the FIR fluxes and obtain SFR = 48 ± 19 M ⊙ yr [−][1] . The stellar masses differences with respect to the previous measurements
are ≤ 0.42 dex (mean 0.14 dex). cid_1143 shows the largest difference in stellar mass.

The right panel of Figure 1 shows the parent SUPER sample and the subset targeted for ALMA observations in this work
on the SFR versus stellar mass ( _M_ ∗ ) plane. The ALMA targets


7 Systematic uncertainties on the stellar masses are around 0.3 dex and
can be larger for SFRs (e.g. Mancini et al. 2011; Santini et al. 2015).
These uncertainties are due to the models used, degeneracies between
parameters, a priori assumptions and the discrete coverage of the parameter space.



have stellar masses in the range log( _M_ ∗ / _M_ ⊙ ) = 10.7 − 11.2, with
a median log( _M_ ∗ / _M_ ⊙ ) = 10.9. The SUPER parent sample has
the same median log _M_ ∗ / _M_ ⊙ = 10.9, and an interquartile range
log( _M_ ∗ / _M_ ⊙ ) = 10.6 − 11.0. The SFRs of the ALMA sample are
in the range SFR= 8 − 380 M ⊙ yr [−][1], with a median SFR = 76
M ⊙ yr [−][1] . The SUPER parent sample has a median SFR = 144
M ⊙ yr [−][1] and interquartile range SFR = 63 − 242 M ⊙ yr [−][1] . The
ALMA targets have similar stellar masses and (slightly lower)
SFRs to the objects with SFR and stellar mass measurements
in the parent SUPER sample. However, we note that only 24/39
of the SUPER targets have SFR and stellar mass measurements,
and ten of these have only upper limits on the SFR, which are not
taken into account in the above median and interquartile ranges.
Given the presence of many SFR upper limits in the parent sample, our targets are likely to represent the upper end of the SFR
distribution of the SUPER sample.
On the SFR- _M_ ∗ plane (see Figure 1), we show also the
main-sequence definition by Schreiber et al. (2015) at the average redshift of our sample ( _z_ ∼ 2.3). Most of the ALMA targets lie on the main-sequence or slightly below [8] . The exception is cid_1143, which lies clearly below the main-sequence.
Despite the pre-selection of FIR detections, our ALMA targets are mainly main-sequence galaxies. However, SUPER primarily consists of moderate luminosity X-ray AGN which, as
a population, tend to have SFR distributions slightly below
the main-sequence (e.g. Mullaney et al. 2015; Scholtz et al.
2018; Grimmett et al. 2020). Scholtz et al. (2018) study the
specific SFR (SSFR=SFR/ _M_ ∗ ) distribution of a sample of 81
AGN at _z_ = 1.5 − 3.2 and for AGN with X-ray luminosities
_L_ 2−10 _keV_ - 10 [44] erg s [−][1], they measure the mode of the SSFR
distribution log(SSFR/Gyr [−][1] ) = −0.32 ± 0.16. For the SUPER
targets with SFR and stellar mass measurements, the mean is
log(SSFR/Gyr [−][1] ) = 0.19 ± 0.09. Thus, the SUPER sample is
likely to have a distribution of SFRs skewed to higher values
compared with the parent population of X-ray AGN.


**4.** **H** α **and [OIII] observations and analysis**


_4.1._ _SINFONI observations and data reduction_


The SINFONI Adaptive Optics (AO) assisted observations and
data reduction are described in detail in Kakkad et al. (2020),
for the Type 1s, and in M. Perna et al. (in prep.), for the Type
2s. Here we summarise the main information. The SINFONI observations took place between November 2015 and December
2018 (ESO large program 196.A-0377). We observe the H-band
(1.45 − 1.85 µm), which includes the rest frame optical lines Hβ
and [O iii]λλ4959, 5007, and the K-band (1.95−2.45 µm), which
includes the [N ii]λλ6584,6548, Hα and [S ii]λλ6716, 6731 lines.
The average spectral resolution in the H-band and K-band is
∼3000 and ∼4000 respectively, corresponding to a channel width
of ∼ 2 Å and ∼ 2.5 Å, respectively. The PSF sizes of the H-band
and K-band are in the range 0.27 − 0.52” and 0.15 − 0.46”, respectively (the PSF sizes for each target are listed in Table 3).
We note that cid_1057 is not detected in Hα, thus for this target
we only show the [O iii] (i.e. H-band) data.


8 We note that the main-sequence from Schreiber et al. (2015) is derived assuming a Salpeter IMF (Salpeter 1955), while we assume a
Chabrier IMF (Chabrier 2003). However, assuming a different IMF
would systematically shift both _M_ ∗ and SFRs by approximately the
same amount (Brinchmann et al. 2004; Elbaz et al. 2007), and therefore would not affect the shape of the main-sequence.


Article number, page 9 of 32

_A&A proofs:_ manuscript no. SUPER_paper


Table 3: Information about the SINFONI maps. PSF of the H and K-band SINFONI images and line fluxes measured from the
integrated spectra. If the S/N of a line is smaller than 3, we report a 5σ upper limit. For cid_1057, the S/N of the K-band image is
too low to derive any information about the Hα and [N ii] emission. (4) redshift derived from the narrow component of the [O iii]
line. (5) Ratio of the fluxes of [O iii]λ5007 and Hβ narrow emission lines. For Type 1 AGN, this is the flux of the narrow component,
i.e. the BLR component is not included. (6) Ratio of the fluxes of [N ii]λ6548 and Hα narrow emission lines. For Type 1 AGN, this is
the flux of the narrow component, i.e. the BLR component is not included. (7) Half-light radius (R _e_ ) of the [O iii] systemic emission
([-300,300] km s [−][1] range), deconvolved from the PSF. If R _e_ is smaller than the PSF, we give the size of the PSF as an upper limit.
(8) Half-light radius (R _e_ ) of the Hα systemic emission ([-300,300] km s [−][1] range), deconvolved from the PSF. (9) Components used
to fit the emission lines. ‘n’: narrow component, ‘b’: broad component (for the outflow), ‘BLR’: broad line region component.


ID H-band PSF K-band PSF z [O iii] F([O iii])/F(Hβ) F([N ii])/F(Hα) _R_ _e_ ([O iii]) _R_ _e_ (Hα) line

[arcsec [2] ] [arcsec [2] ] [kpc] [kpc] components
(1) (2) (3) (4) (5) (6) (7) (8) (9)

X_N_81_44 0.27×0.27 0.24×0.24 2.3180 - 8.00 < 0.10 < 1.11 3.48±0.08 n, b, BLR
XID36 0.35×0.35 0.15×0.15 2.2578 10.15±0.63 0.69±0.12 1.06±0.01 1.57±0.01 n, b
XID419 0.52×0.47 0.24×0.22 2.1430 - 2.15 0.91±0.05 < 2.07 1.42±0.02 n
cid_1057 0.32×0.30 0.46×0.43 2.2099 2.51±0.17  - 1.36±0.01  - n, b
cid_346 0.30×0.30 0.30×0.30 2.2170 1.58±0.20 0.43±0.11 1.99±0.03 2.28±0.05 n, b, BLR
cid_451 0.30×0.28 0.28×0.27 2.4434  - 10.59 0.61±0.03 0.78±0.00 0.67±0.01 n, b
cid_1205 0.30×0.30 0.30×0.30 2.2555  - 1.66  - 0.99±0.02 1.33±0.09 n, BLR
cid_1143 0.41×0.38 0.30×0.30 2.4418 6.91±1.97 0.75±0.09 < 1.62 0.92±0.02 n, b



_4.2._ _Astrometry registration_


Since one of our main goals is to compare the spatial distribution of the FIR continuum and ionised gas emission, we need
to have reliable astrometry for both ALMA and the SINFONI
maps. The absolute position of the SINFONI cubes, as derived
from the SINFONI pipeline, is not sufficiently accurate for our
purposes. Given the small field of view of the SINFONI images
(3 × 3 arcsec [2] ), we cannot correct the astrometry using nearby
stars, since usually the target is the only visible source in the
field of view. Thus, we need to rely on coordinates derived from
other images.
We aligned our SINFONI data-cubes to broadband Hand K-band images of the same field. We used images from
VLT/VISTA taken as part of the UltraVISTA survey for COSMOS (McCracken et al. 2012) and as part of the VHS (VISTA
Hemisphere Survey) for XMM-XXL (McMahon et al. 2013),
and from VLT/ISAAC for CDF-S (Retzlaff et al. 2010). We first
aligned the H/K-band images to _Gaia_ astrometry (Gaia Collaboration et al. 2016, 2018) using several stars across the fields.
We then made broad-band images from the SINFONI datacubes by collapsing them over the same wavelength range as
the archival H/K-band images. We found the centroids of the
images from the data-cubes and aligned these to the positions
of the corresponding source in the near-infrared VLT/VISTA or
VLT/ISAAC (H/K-band) images [9] . For the uncertainties on these
positions, we combined in quadrature the uncertainties from:
(1) the _Gaia_ coordinates (< 4 mas), (2) the alignment of the
H/K-band images with _Gaia_ (75 − 130 mas), (3) the PSF of the
VLT/VISTA or VLT/ISAAC K-band images (3-40 mas), (4) the
2D Gaussian fit to determine the position of sources in the VLT
images (1-49 mas), and (5) the centroid position of the collapsed
data-cubes (∼25 mas). This results in uncertainties on the astrometry in our SINFONI cubes of 0.03 − 0.14”, corresponding
to 1-3 pixels [10] . More details about the coordinate registration are
provided in the appendix C. The ALMA astrometry has an ab

9 For two of the Type 1 sources (X_N_81_44 and cid_346) we use
the more accurate _Gaia_ position and for XID419 we use more accurate
coordinates from _HST_ /WFC3, see appendix C.
10 The largest uncertainties are due to the lower resolution of the
VLT/ISAAC K-band images for the CDF-S field.


Article number, page 10 of 32



solute accuracy of 2% of the synthesized beam (ALMA Cycle 6
Technical Handbook [11] ), which corresponds to ∼ 3 − 6 mas for
our observations and it is small enough compared to the other
uncertainties.


_4.3._ _Spectral line fitting_


We use the integrated spectra to derive emission line flux ratios and investigate the main source of ionisation in our objects. For this purpose, we measure the fluxes of the Hβ,

[O iii]λλ4959,5007, Hα and the [N ii]λλ6548,6583 emission
lines. The integrated SINFONI spectra of the Hα+[N ii] and
Hβ+[O iii] spectral regions for our targets are shown in Figure 3.
The spectra are extracted from a circular aperture centred on the
targets. The diameter of the aperture was defined to include at
least ∼ 95% of the emission.
Up to three Gaussian components were used to fit each emission line. These are a narrow (systemic) component, a broad
(outflow) component and a broad line region (BLR) component
(only for the Hydrogen lines). The components used for each
target are summarised in Table 3.
For the Type 1 AGN, the Hβ+[O iii] and Hα+[N ii] spectral
regions are fitted separately. The modelling of the Hβ+[O iii]
spectral region is described in details in Kakkad et al. (2020).
The width and relative position of the systemic and outflow components of Hβ and [O iii] are tied together. The broad outflow
component is used in the fit only if its addition decreases the reduced χ [2] value of the overall model. Specifically, for the three
Type 1 in our sample: this is not required for cid_1205 but is
required for X_N_81_44 and cid_346 [12] . An additional Gaussian
component is used to model the broad line region (BLR) component of Hβ for all Type 1 sources. For the Hα+[N ii] spectral region, we use the same number of Gaussian components


11 https://almascience.eso.org/documents-and-tools/cycle6/almatechnical-handbook
12 We note that in Kakkad et al. (2020) the Hβ+[O iii] emission lines
were fitted with one component, while two components are required
for the fit of the Hα+[N ii] emission lines (based on the reduced χ [2] ).
In order to have consistent measurements for the four emission lines,
we decide to use the fit with two components also for the Hβ+[O iii]
emission lines.

I. Lamperti et al.: SUPER V: obscured star formation and outflows



as for [O iii], and an additional Gaussian component to model
the BLR component of Hα. Additionally, we apply the following constraints (following Vietri et al. 2020): i) the widths of the
broad components of Hα and [N ii] are tied to the width of the
broad component of [O iii], allowing variation in the parameters
within the measurement errors; ii) the relative centroid locations
of the narrow and broad components of Hα and [N ii] are tied to
the ones measured with [O iii]; iii) the maximum width allowed
for the narrow Hα component is set by the width of the narrow [O iii] component plus its measurement error. Finally, empirical FeII templates from the literature are used to model the
FeII emission (Boroson & Green 1992; Veron-Cetty et al. 2004;
Tsuzuki et al. 2006).
For the Type 2 sources, the fitting procedure is similar to the
one used for the Type 1 AGN. The results of the emission line fits
for all the Type 2 objects in the SUPER sample will be presented
in M. Perna et al. (2021, in prep.). The Hα and Hβ lines, and
the [O iii], [N ii] and [S ii] doublets were modelled using Gaussian profiles. The wavelength separation between emission lines
was tied according to atomic physics, and the FWHM was constrained to be the same for all the emission lines. The relative flux
of the two [N ii] and [O iii] lines was fixed to 2.99 (Osterbrock
& Ferland 2006). Each spectral fit was performed with one and
two Gaussian components (each centred at a given velocity and
with a given FWHM). The Bayesian information criterion (BIC,
Schwarz 1978) was used to decide whether a second component
was needed for the fit (see e.g. Perna et al. 2019). All targets require a second component except for XID419. We note that we
use our emission-line profile fits to characterise the integrated
emission-line profiles; however, in this study we do not attempt
to map individual Hα components associated with star formation, AGN narrow line regions and/or outflows (see Section 4.4).
The H and K-band (continuum- and BLR-subtracted) spectra
with the corresponding emission line fits are shown in Figure 3.
The total spectra of the Type 1 targets (before subtracting the
continuum and BLR components) are shown in Appendix D. A
summary of the line components used for each target is provided
in Table 3.
For both Type 1 and Type 2 sources, the uncertainties on the
line fluxes were estimated using a Monte Carlo approach (for
details, see Kakkad et al. 2020). We define a line as detected if
it has a S/N= _F_ / _F_ _err_ ≥ 3. If a line is not detected, we calculate
a conservative upper limit equal to the flux of a Gaussian emission line with amplitude five times the noise level (measured in a
line-free region of the spectrum) and with the same width as the
other detected emission lines. The 5σ upper limit corresponds
to a ‘false negative’ fraction of 2%, which is the probability that
a source with ‘true’ flux higher than this upper limit is not detected.
We note that we did not correct the line fluxes for obscuration. In most of the cases we are not able to calculate the Balmer
decrement, because the Hβ line is not detected. Nevertheless, we
do not consider this a major limitation since we are mainly interested in the ratio of emission lines close in wavelength, which
therefore are negligibly affected by differential obscuration.


_4.4._ _H_ α _and [OIII] maps_


In this section we describe the methods used to derive the maps
of the narrow Hα (i.e. without Broad Line Region) and [O iii]
emission. In this paper, we consider a w 80 (i.e. the width containing 80% of the line emission) value - 600 km s [−][1] as a signature of an AGN-driven outflow (Kakkad et al. 2020). Following this definition, we consider as non-outflowing emission a ve


locity range of 600 km s [−][1], centred on the peak of the [O iii]
(or Hα) emission line. For the two targets with a two component fit to the [O iii] emission line, this definition covers the
bulk of the narrower component and excludes the broader, blueshifted component. We note that it is possible that the outflow
component is contributing also in the central velocity channel
( _v_ = [−300, 300] km s [−][1] ), especially in the sources with a strong
outflow component. We chose this definition because we prefer
to adopt a consistent definition across all targets and for both
emission lines (Hα and [O iii]). Moreover, a definition which is
as independent as possible from the modelling of the emission
line profile is highly preferred. However, it is inevitable that the
resulting Hα maps of the Type 1s will depend on the method
used to subtract the BLR component.
To create the maps, we use the continuum-subtracted datacubes. For the Hα maps, we also subtract the BLR component
(for the Type 1) and the [N ii] components. For X_N_81_44, we
note that the broad component of Hβ is much more prominent
than the broad component detected in [O iii] (see Figure D.1 in
the appendix). We suspect that this component is a residual component belonging to the BLR. This argument is supported by the
fact that the spatial distribution of the Hβ broad component is
similar to the spatial location of the BLR. Therefore, for this object we consider the broad Hβ and Hα components as part of the
BLR and we subtract them from the data-cube. We use the peak
of the modelled [O iii]λ5007 line profile to derive the systemic
redshift and set the zero velocity (see Sec. 4.3). We create the

[O iii] and Hα maps by collapsing the spectra over the selected
velocity channels for each spaxel.
We note that our approach to map the Hα emission line is different from the method applied in other resolved studies of the
Hα emission of Type 1 AGN (e.g. Carniani et al. 2016), where
the residuals of the fit (of their AGN-dominated components)
were used to trace Hα emission due to star formation. After subtracting the emission line fitting model from our data, we do not
find any significant residual at the position of Hα, both in the
maps and in the integrated spectra (see residual panels in Figure 3). Thus, we cannot use this method to map the Hα emission
from star formation. We defer to a future work a detailed investigation of the spatially-resolved narrow Hα emission distribution
and kinematics for the few Type 1 sources where the S/N are sufficiently high for such analyses. In Section 5.3.1 we use emission
line diagnostics to investigate the main mechanism responsible
for the ionisation of Hα (star formation or AGN) in our objects.
However, due to the limited S/N of our observations, we cannot
perform a BPT analysis in a spatially resolved manner.
Figure 3 shows the contours of the Hα and [O iii] emission in the central 600 km s [−][1] channels. For every map, we
measure the size and the centroid (‘peak position’) of the
emission by fitting a 2D Gaussian using the python package
`scipy.optimize.curve_fit` . The Hα and [O iii] sizes are reported in Table 3. We use these measurements in Sec. 5.3.2,
where we compare the sizes and positions of the Hα and [O iii]
emissions with the location of the FIR emission. The uncertainties on the positions are calculated by adding in quadrature the
uncertainties on the coordinates registration (see Section 4.2)
and the uncertainties due to the 2D Gaussian fit (mean uncertainty ∼ 2 mas). The uncertainties on the position are in the range
0.04-0.15”.


**5.** **Results and discussion**


In this section, we first investigate the origin of the (rest-frame)
260 µm emission in our targets, to assess the relative importance


Article number, page 11 of 32

_A&A proofs:_ manuscript no. SUPER_paper


X_N_81_44





0.75 0.38 0 -0.38 -0.75
∆R. A. [arcsec]









0.3


0


-0.3









X_N_81_44







XID36



∆R. A. [arcsec]


XID36



rest _−_ frame wavelength [A] [˚]





0.25


0


-0.25



0.25


0


-0.25











∆R. A. [arcsec]


XID419



∆R. A. [arcsec]



_−_ 0 _._ 256450 6475 6500 6525 6550 6575 6600 6625 6650

rest _−_ frame wavelength [ [˚] A]



0.25


-0.25



0.25


-0.25



















0.25


0


-0.25







0.5 0.25 0 -0.25 -0.5
∆R. A. [arcsec]


cid_346



2 _._ 0


1 _._ 5


1 _._ 0


0 _._ 5


0 _._ 0


_−_ 0 _._ 5


2

1

0

_−_ 47001 4750 4800 4850 4900 4950 5000 5050

rest _−_ frame wavelength [A] [˚]


4800 4850 4900 4950 5000 5050
rest _−_ frame wavelength [ [˚] A]


4800 4850 4900 4950 5000 5050
rest _−_ frame wavelength [ [˚] A]


1 _._ 25


1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00


_−_ 0 _._ 25


2


0


4700 4750 4800 4850 4900 4950 5000 5050
rest _−_ frame wavelength [ [˚] A]



cid_346

















0.75 0.38 0 -0.38 -0.75
∆R. A. [arcsec]



6450 6475 6500 6525 6550 6575 6600 6625 6650
rest _−_ frame wavelength [ [˚] A]



Fig. 3: [O iii] and Hα continuum-subtracted maps (where available), with the corresponding spectra. For the Type 1 AGN
(X_N_81_44, cid_346 and cid_1205),the broad line region component is also subtracted. The [O iii] and Hα maps were created
by integrating the spectrum over the [-300, 300] km s [−][1] velocity range, with respect to the centre of the line (see shaded regions
on spectra). The FIR (black), [O iii] (lightblue), and Hα (red) emission contours are shown at the 2, 3, 4, 6, 8, 12, and 16σ levels.
Dashed lines indicate the negative -2σ contours. The crosses show the position of the centroid of the FIR (black), [O iii] (blue)
and Hα (red) emission with the respective uncertainties (circles). The lightblue point shows the centroid position of the optical
continuum (i.e. K-band observed-frame). In all maps, the grey ellipses show the size of the ALMA beam, while the scale-bars give
the size of the PSF of the line emission maps. The grey bar shows the position angle along the major axis of the FIR emission,
when it can be reliably determined (see Section 3.3.1). _Column 1:_ Contours of the [O iii] emission (lightblue) and FIR (rest-frame)
260 µm continuum emission (black). _Column_ _2:_ Continuum-subtracted (integrated) [O iii]+Hβ spectra. The blue curve shows the
total fit to the Hβ, [O iii]λ4959 and [O iii]λ5007 lines. The magenta and orange curves show the narrow and broad components.
_Column_ _3:_ Contours of the narrow Hα flux map (red) FIR (rest-frame) 260 µm continuum emission (black). _Column_ _4:_ Same as
column 2, but for the continuum-subtracted (integrated) Hα+[N ii] spectra. The blue curve shows the total fit to the Hα, [N ii]λ6548
and [N ii]λ6584 lines.


Article number, page 12 of 32

I. Lamperti et al.: SUPER V: obscured star formation and outflows



cid_451























0.5 0.25 0 -0.25 -0.5
∆R. A. [arcsec]


cid_1205







6450 6475 6500 6525 6550 6575 6600 6625 6650
rest _−_ frame wavelength [ [˚] A]























0.5 0.25 0 -0.25 -0.5
∆R. A. [arcsec]







6450 6475 6500 6525 6550 6575 6600 6625 6650
rest _−_ frame wavelength [ [˚] A]













0.25


-0.25









0.5 0.25 0 -0.25 -0.5
∆R. A. [arcsec]








rest _−_ frame wavelength [ [˚] A]



Fig. 3: Continued.



of the physical processes responsible for the FIR emission (Section 5.1). Then, we compare the FIR size of our sample with
other AGN hosts and non-AGN galaxies at similar redshift from
the literature, to test whether our sample has similar sizes to the
general population of _z_ ∼ 2 galaxies (Section 5.2). Finally, we
compare the spatial distribution of the FIR emission with the
ionised gas distribution (Section 5.3), as well as with the position of the ionised outflows (Section 5.4).


_5.1._ _Origin of the FIR ALMA Band 7 emission_


We compare the distribution of dust-obscured star formation
with the distribution of ionised gas and corresponding ionised
outflows in our targets. For this goal, we use the rest-frame FIR
images from our ALMA 260 µm maps. However, it is important
to first assess the physical processes that are responsible for the
260 µm emission in our sample, to test whether this emission can
be used as a reliable tracer of dust obscured star formation.
The rest-frame ∼ 260 µm emission (corresponding to the
observed 870 µm emission) can have different origins. The three
main sources of emission in the FIR are: 1) dust heated by star
formation, 2) dust heated by the AGN, and 3) AGN synchrotron
emission (e.g. Falkendal et al. 2019). The observed emission is
likely a combination of the three processes above, nevertheless
in this section we attempt to estimate their fractional contribution, and to determine the dominant source of emission in our
eight ALMA targets.


_Dust_ _heated_ _by_ _the_ _AGN_ : We consider first a diagnostic to estimate the AGN contribution in the FIR that does not rely directly on our specific SED fits. Following Stanley et al. (2018),



this method focuses on the ratio of the (observed-frame) FIR
(870µm) to MIR (24µm) flux. AGN can have a stronger MIR
emission compared to star-forming galaxies, due to emission
from hot dust in the torus (e.g. Pier & Krolik 1992; Lacy et al.
2004; Donley et al. 2012; Stern et al. 2012). Therefore, looking
at the (observed-frame) flux ratio _F_ 870µ _m_ / _F_ 24µ _m_, it is possible to
assess whether the SED is dominated by AGN emission in the
24 − 870 µm regime.


Figure 4 shows the _F_ 870µ _m_ / _F_ 24µ _m_ flux ratios as a function of
redshift for our sample. To compute the flux ratios, we use the
24 µm _Spitzer_ /MIPS flux densities from the photometric catalogue compiled by Circosta et al. (2018) and our measurements
of the 870 µm ALMA flux densities. On Figure 4, we show the
range of flux ratios obtained from the SED fit of our objects by
Circosta et al. (2018) using AGN models from Fritz et al. (2006)
and star-forming galaxies (SF) templates from Dale et al. (2014).
We also show the curves corresponding to the average pure SF
template and the average AGN only template from Stanley et al.
(2018). They use AGN templates from Mullaney et al. (2011)
and SF templates from Mullaney et al. (2011) and Silva et al.
(1998).


All our targets are in the region between the SF and AGN
templates, suggesting that the (observed-frame) 24 − 870 µm
emission is produced by a mixture of SF and AGN. The only
two targets which are close to the AGN-dominated region of this
diagram are cid_1057 and cid_451. These two targets are those
with low S/N in the 870 µm data (S/N< 8). This is probably
reflecting the uncertainty in the measured _F_ 870µ _m_ fluxes and the
higher fraction of flux that may be resolved out in the ALMA
observations, rather than suggesting a higher AGN contribution.


Article number, page 13 of 32

_A&A proofs:_ manuscript no. SUPER_paper



To provide a more quantitative estimate of the contribution
of the different physical processes to the rest-frame 260 µm
(observed-frame 870 µm) flux density of our targets, we also
analyse the results of the UV-to-FIR SED fitting performed with
`CIGALE` including our ALMA Band 7 photometric points (see
Section 3.4). The MIR to FIR spectral range is modelled with
two main components: emission by cold dust heated by SF and
AGN emission due to the dusty torus peaking in the MIR. To
estimate the AGN contribution to the 260 µm flux density, we
consider the ratio between the flux density of the AGN component at 260 µm derived from the SED best-fit model and that
measured from our ALMA data.
In Figure 5, we show as an example the SED of one target (cid_346). The SEDs of the other targets are shown in Figure E.1 in the appendix. The AGN contribution to the total flux
at 260 µm ranges from < 1% to 6.3% (for cid_451), with a mean
of 2.1%. Therefore, the results of the SED fitting decomposition
suggest that the 260 µm emission is dominated by star formation
rather than heating from the AGN in all our targets. For the two
targets with low S/N in the 870 µm data (cid_1057 and cid_451),
which are close to the AGN-dominated region of the diagnostic
diagram from Stanley et al. (2018), the SED fitting would imply that the AGN only contributes 2.8% and 6.3%, respectively,
to the 260 µm flux. The `CIGALE` SED fitting code does not provide the uncertainties on the best-model SED. We therefore consider the uncertainties on the AGN fraction in the FIR range (81000 µm), derived from the posterior distribution of the `CIGALE`
SED fit. These uncertainties are in the range 3-10%. Thus, even
adding these uncertainties, the AGN contribution remains small
(< 16%). We note that the SED fit was performed including our
ALMA high-resolution flux densities. We test that excluding the
ALMA points from the SED fit, the inferred AGN contributions
vary by less than 3%. Additionally, we test that using a difference SED fitting code (AGNfitter, Calistro Rivera et al. 2016),
the AGN contributions remain small (< 7%).
We also consider a third method to estimate the AGN contribution in the FIR. The AGN re-processed emission depends on
the model assumed to describe the torus, thus different models
could potentially lead to different estimates. For the SED fitting,
Circosta et al. (2018) use the models from Fritz et al. (2006).
As an alternative approach, we model the torus emission using
a modified black-body (MBB) following the methodology described by Lani et al. (2017). Using the AGN bolometric luminosity ( _L_ _bol_ ) and the measured dust sizes ( _R_ _e_ ), we apply Eq. 2
from Lani et al. (2017) to estimate the temperature that the dust
heated by the AGN would have at a distance _R_ _e_ from the AGN:



_L_ _bol_ [ _erg_ / _s_ ]
� 10 [46]



consider more accurate the results from the `CIGALE` SED fitting,
since this method uses a larger wavelength range to constrain the
contribution from the AGN, including the near-infrared (NIR)
photometry. Nevertheless, it is re-assuring that also using a different model to reproduce the torus emission returns consistent
results.

Although we are limited by photometric coverage at long
wavelengths in most of the SEDs, which makes the exact
percentage of the AGN contribution uncertain, all our analyses
indicate that the contribution from dust heated by the AGN to
the 260 µm emission, and hence to our maps produced from the
ALMA data, is negligible. We note that some studies based on
radiative transfer models have highlighted the possibility that
AGN could contribute significantly to the heating of diffuse
warm dust on host-galaxy scales (Schneider et al. 2015; Duras
et al. 2017; Viaene et al. 2020; Di Mascia et al. 2021; McKinney
et al. 2021). This emission is not related to the torus emission
and therefore it is not taken into account in our SED fitting
decomposition. This AGN contribution is more important in
the central region (≲ 100 pc, Viaene et al. 2020), but in more
luminous AGN it could also affect larger scales. This effect
on large scales is more likely to appear on extremely dusty
and infrared-luminous objects, such as in infrared and submm
selected galaxies (McKinney et al. 2021), or in very luminous
quasars ( _L_ _bol_ - 10 [47] erg s [−][1], Duras et al. 2017), which is not the
case of our sample. Detailed radiative transfer modelling would
be required to test this effect on our sample, but this is beyond
the scope of this work.


_Synchrotron_ _emission_ : In AGN, synchrotron emission can also
contribute to the FIR flux, in particular in sources classified as
‘radio loud’ (e.g. Dicken et al. 2008; Falkendal et al. 2019).
All our targets have flux measurements or 3σ upper limits at
1.4 GHz and/or 3 GHz obtained with the Very Large Array
(VLA). The radio fluxes are reported in Circosta et al. (2018).
Briefly, the two sources from E-CDF-S (XID36 and XID419)
have 1.4 GHz fluxes from Miller et al. (2013). XID36 has an additional flux measurement at 5.5 GHz taken with the Australia
Telescope Compact Array (ATCA) from Huynh et al. (2012).
X_N_81_44 has a 1.4 GHz flux upper limit from the VLA’s
FIRST survey (Becker et al. 1995). The sources from COSMOS
have flux measurements from the 3 GHz VLA-COSMOS project
(Smolˇci´c et al. 2017). Two targets (cid_346 and cid_451) have
also a measurement at 1.4 GHz from Schinnerer et al. (2007).
To estimate the contribution from synchrotron emission to
the ALMA Band 7 flux (rest-frame ∼260 µm), we extrapolate
from the radio fluxes using a power-law model (Dicken et al.
2008). For the two sources that have two flux measurements in
the radio (XID36 and cid_346), we use the slope between the
two points to determine the spectral index α _r_ ( _F_ ν ∝ ν [α] _[r]_ ), assuming no significant variability in the radio at the two frequencies.
For cid_346, we measure a spectral index α _r_ = −0.98 and the
contribution from synchrotron emission is 0.03%. For XID36
we measure a spectral index α _r_ = −1.25 and a contribution of
0.06%. For cid_451, which is classified as a radio loud AGN, the
3 GHz flux is higher than the 1.4 GHz flux. Using the ALMA
Band 3 flux at ∼ 100 GHz from Circosta et al. (2021) and the
3 GHz flux, we estimate α _r_ = −0.99 and a contribution of 21%.
We note that since this source has low S/N, it is not included
in our spatially resolved analyses. For the targets with only one
flux measurement in the radio, we assume α _r_ = −0.7, which is
the median value measured for AGN from Smolˇci´c et al. (2017).
For these targets, the contribution from synchrotron emission is
small (< 1%). We note that even assuming a conservative value



_T_ [ _K_ ]
� 1500



2 1

=
� [4][+][β] _R_ _e_ [ _pc_ ]



2
. (2)
� [1]



We note that this equation assumes optically thin dust and we
assume a dust emissivity index β = 1.8 for this test. For our
sample, the temperatures of the AGN component (estimated using equation 2) are in the range 68 − 153 K. Then, for each target
we create a MBB with the estimated temperature and we scale
this model to match the photometric data. In this way, we can
estimate the maximum AGN contribution at rest-frame 260 µm
assuming a MBB model. Since this model is constrained only
in the MIR range (∼ 5 − 50 µm), we can apply it only to the
six targets with enough photometric coverage in the MIR (i.e.
excluding cid_1057 and cid_1143). The AGN contributions to
the ALMA band 7 photometry estimated with this method are in
the range 0.5 − 20%. These percentages are consistent within the
uncertainties with the results from the `CIGALE` SED fitting. We


Article number, page 14 of 32

I. Lamperti et al.: SUPER V: obscured star formation and outflows



















10 [4]


10 [3]


10 [2]


10 [1]


10 [0]


10 [-1]


10 [-2]











2.1 2.2 2.3 2.4 2.5

redshift



10 [-3]


|cid_346|Col2|Col3|
|---|---|---|
|AGN heated dust: < 1% ofF(870µm)<br>synchr. (αr= - 0.98): < 1% ofF(870µm)<br>best fit<br>stellar emission<br>SF heated dust<br>Fitted UV-IR photometry<br>ALMA Band 7<br>3 GHz<br>1.4 GHz|AGN heated dust: < 1% ofF(870µm)<br>synchr. (αr= - 0.98): < 1% ofF(870µm)<br>best fit<br>stellar emission<br>SF heated dust<br>Fitted UV-IR photometry<br>ALMA Band 7<br>3 GHz<br>1.4 GHz|AGN heated dust: < 1% ofF(870µm)<br>synchr. (αr= - 0.98): < 1% ofF(870µm)<br>best fit<br>stellar emission<br>SF heated dust<br>Fitted UV-IR photometry<br>ALMA Band 7<br>3 GHz<br>1.4 GHz|
|-1<br>100<br>re|101<br>102<br>st −frame wavelen|103<br>104<br>1<br> gth [µm]|



Fig. 4: Ratio of (observed-frame) 870µm to 24µm flux as a
function of redshift for our targets calculated using the measured F(870µm) from the ALMA maps. The two sources with
peak S/N< 8 in the ALMA maps are marked with empty symbols (cid_1057 and cid_451). The numbers show the percentage
AGN contribution at 870 µm (observed-frame) estimated from
the modelled SEDs (see Section 5.1). The dashed lines show the
median flux ratio as a function of redshift for star-forming (SF)
galaxies templates (magenta) and AGN templates (green) from
Stanley et al. (2018). The shaded areas show the range of flux ratios obtained from the SF (magenta) and AGN (green) templates
used to fit our ALMA targets.


of α _r_ = 0, which is towards the most extreme value measured for
AGN (Dicken et al. 2008; Smolˇci´c et al. 2017), the synchrotron
contribution is small (< 34% for cid_1057 (a source with low
S/N in the ALMA map) and < 14% for the other targets).
We conclude that in our ALMA sample most of the emission
at rest-frame 260 µm is due to dust heated by star formation,
with contribution from dust heated by the AGN ≤ 6% and synchrotron contribution ≤ 21%. If we consider only the six targets
with high S/N in the 260 µm maps, the contribution from AGNheated dust is ≤ 4% and the synchrotron contribution is < 1%.
The estimated contributions for each target are tabulated in Table 2.


_5.2._ _FIR size comparison with other samples from the_
_literature_


In this section, we compare the FIR sizes of our sample with
other samples of galaxies at similar redshift from the literature.
We also investigate if there is any difference in the size of galaxies with and without an AGN.
From our analysis, we find that the FIR effective radii derived
from the fit with the ‘preferred models’ for our sample are in the
range 0.80 − 2.01 kpc, with a mean of 1.36 ± 0.21 kpc. These
sizes are comparable to previous measurements presented from
ALMA data for _z_ ∼ 1 − 3 AGN and star-forming galaxies (Barro
et al. 2016; Hodge et al. 2016; Fujimoto et al. 2017; Gullberg
et al. 2019; Scholtz et al. 2020; Chen et al. 2020).
We investigate in more detail how our sizes compare to
other samples in Figure 6, where we plot size as a function of
observed-frame 870 µm flux density. We show the 6/8 sources
with high S/N in our sample. For the sake of a more direct comparison to literature, we show the sizes from our exponential and



Fig. 5: Example rest-frame spectral energy distribution (SED)
of one of our targets (cid_346). The light blue data points represent the UV-IR photometry used for the SED fit. The arrows
indicate 3σ upper limits. The red point shows our ALMA Band
7 flux measurement (included in the fit). The blue and orange
points show the radio fluxes at 1.4 and 3 GHz, respectively. The
solid curves show the different components of the SED modelling performed with `CIGALE` . To estimate the maximum contribution of synchrotron emission to the rest-frame 260 µm flux
density, we parametrised this emission as a power law with spectral index α _r_ = −1.25 (dashed red line), derived based on the 1.4
and 5.5 GHz data. The estimated contributions to the 260 µm
flux from dust heated by the AGN and from synchrotron emission are also shown.


Gaussian fits (see Section 3.3.1; Appendix B), noting that these
are consistent with the sizes derived from our ‘preferred’ models.

For this comparison, we identify five samples of star-forming
galaxies (SFGs) and AGN with i) similar redshifts to our sample
( _z_ ∼ 1.5 − 2.5) and ii) FIR sizes measured from high-resolution
(< 0.5”) ALMA Band 7 continuum data: Hodge et al. (2016),
Gullberg et al. (2019), Scholtz et al. (2020), Chen et al. (2020),
and Tadaki et al. (2020). We consider only the sources detected
with S/N> 8, for which it is possible to derive reliable sizes.
In Table 4 we summarise the main properties of the literature
samples (sample size, redshift, resolution and RMS sensitivity
of the ALMA maps, and the model used to derive the FIR sizes).
The first sample consists of 16 sub-millimetre galaxies
(SMGs) from the ALESS survey (Hodge et al. 2013; Karim et al.
2013), whose FIR sizes are reported in Hodge et al. (2016). We
consider only the SMGs in the redshift range _z_ = 1.5 − 2.5 (six
objects). Based on X-ray data (Wang et al. 2013), one object
(ALESS17.1) is confirmed as AGN. We note that two of the targets have X-ray luminosities _L_ _X_ (0.5 − 8 _keV_ ) - 10 [42][.][2] erg/s, for
which it is ambiguous if the emission is due to an AGN or to star
formation.

The second sample is presented by Gullberg et al. (2019).
They measure the FIR sizes from exponential fits for 153 SMGs
from the ALMA SCUBA-2 UDS survey (AS2UDS; Stach et al.
2019). Using MIR diagnostics, Stach et al. (2019) identified one
third of the sample as AGN, one third as non-AGN, with the
final third having insufficient MIR photometry for this classification. Using stacking analyses, Gullberg et al. (2019) show that
their measured individual sizes underestimate the true sizes by


Article number, page 15 of 32

_A&A proofs:_ manuscript no. SUPER_paper


Table 4: Properties of the literature samples used to compare the FIR sizes (see Section 5.2). (1) Number of objects considered in
our comparison. (2) Redshift of the sources. (3) RMS sensitivity of the ALMA observed-frame 870 µm maps. (4) Resolution of the
ALMA observed-frame 870 µm maps. (5) Model used to measure the FIR sizes: exponential (exp.) or Gaussian. (6) Mean FIR size
(half-light radius) derived from the 870 µm data.


Reference N z RMS resolution model < _R_ _e_  
[mJy beam [−][1] ] [arcsec] [kpc]
(1) (2) (3) (4) (5)

This work 6 2.1-2.5 0.02-0.04 0.16-0.27 exp. (Gaussian) 1.31±0.23 (0.93±0.23) _[a]_

Hodge et al. (2016) 6 1.5-2.5 ∼0.064 ∼0.16 exp./Gaussian _[b]_ 1.48±0.08
Gullberg et al. (2019) 153 1.5-5.8 (median 2.9) 0.09-0.34 ∼0.18 exponential 1.20±0.4
Scholtz et al. (2020) 4 1.4-2.6 0.02-0.69 0.16-0.28 Gaussian 0.97±0.24
Chen et al. (2020) 4 1.5-2.5 0.03-0.07 0.17-0.25 Gaussian 1.67±0.22
Tadaki et al. (2020) 62 1.9-2.6 ∼0.06 0.20-0.30 exponential 1.56±0.12
( _a_ ) For our work, we report the mean _R_ _e_ obtained using both the exponential (exp.) and the Gaussian model. ( _b_ ) Hodge et al. (2016)
fit the sample assuming a Sérsic profile with index _n_ free. The six SMGs with _z_ = 1.5 − 2.5 have FIR profiles between Gaussian
and exponential (Sérsic index _n_ = 0.5 − 1).



∼ 50% due to the relatively low RMS (median of 0.3 mJy/beam
compared to our mean 0.02 mJy/beam). Therefore, in Figure 6,
we just show their derived median size which accounts for this
effect.
The third sample is presented in Scholtz et al. (2020) and
consists of eight X-ray AGN at _z_ = 1.4 − 2.6 from the KMOS
AGN Survey at High-redshift (KASHz) [13] . We exclude from the
comparison two targets with low-resolution ALMA data (beam
size > 0.5”) and two targets with S/N< 8.
Moreover, we consider the sample of six SMGs in the redshift range _z_ = 1.5 − 2.5 presented by Chen et al. (2020). Three
objects are classified as X-ray AGN, one as infrared AGN, and
two as non-AGN. Two targets are also present in the sample from
Hodge et al. (2016) and have consistent size measurements, thus
we consider them only once in our comparison.
Finally, we consider the sample of 62 massive ( _M_ ⋆   - 10 [11]
M ⊙ ) star-forming galaxies at redshift _z_ = 1.9 − 2.6 from Tadaki
et al. (2020). X-ray data for this sample are available from Luo
et al. (2017) and Kocevski et al. (2018). Based on a threshold
of intrinsic X-ray luminosity _L_ _X_ - 10 [42] erg s [−][1], 13 objects
are classified as AGN. We note that this sample combines highresolution ALMA observations (0.2”) with a compact array configuration (maximum recoverable scale ∼ 6.7”). Therefore, their
observations are more sensitive to large scales than the other
samples, which only use the high-resolution configuration.
The mean effective radius obtained with the exponential fit
for our sample (1.30 ± 0.22 kpc) is consistent with the mean
sizes from Hodge et al. (2016) (1.48 ± 0.08 kpc), Gullberg et al.
(2019) (1.2 ± 0.4 kpc), and Tadaki et al. (2020) (1.56 ± 0.12 kpc),
that also used the exponential fit. Using the Gaussian fit, we obtained a mean radius of 0.91 ± 0.11 kpc, which is consistent with
Scholtz et al. (2020) (1.14±0.29 kpc) and smaller (by > 3σ) than
the mean size from Chen et al. (2020) (1.67 ± 0.22 kpc), both obtained assuming a Gaussian profile. However, we note that our
sample has a smaller range of flux densities ( _F_ 870µ _m_ = 0.3 − 2.6
mJy) compared to these other samples ( _F_ 870µ _m_ = 0.7 − 9.0 mJy),
which include also SMGs, that is galaxies selected because of
their high submm flux. If we limit the comparison to objects
with _F_ 870µ _m_ < 2.6 mJy, the mean size derived, 1.44 ± 0.11 kpc, is
consistent with the mean size of our sample (measured with the
exponential fit).


13 We note that Scholtz et al. (2020) reported the effective radii as
_R_ _e_ =σ=FWHM/2.355. For our comparison, we convert their size measurements to _R_ _e_ =FWHM/2, to be consistent with our definition.


Article number, page 16 of 32



We also separate the sample in AGN and non-AGN (see open
and filled symbols in Figure 6), to investigate whether there is a
difference in their FIR sizes. We consider the sizes measured
assuming a Gaussian profile, when possible, in order to have a
consistent method for all samples. We note that for the Tadaki
et al. (2020) sample this is not possible, since the sizes have
been measured only with the exponential profile. However, we
note that if we were to use the sizes measured with the exponential profile fit, we would obtain the same qualitative results.
We exclude from this analysis the sample from Gullberg et al.
(2019), for which we only have the ‘median’ size of the sample
that includes both AGN and non-AGN.

The mean size for AGN is 1.16 ± 0.11 kpc, while the mean
size for non-AGN is 1.69 ± 0.13 kpc (4σ difference). Applying the two-samples Kolmogorov-Smirnov (KS) test, we find a
_p_ −value= 0.03, meaning that the distributions of sizes for the
AGN and non-AGN are significantly different ( _p_ −value< 0.05).
We note that if we consider the sizes measured only with exponential or only with Gaussian profiles, the KS test finds a significant difference between the sizes of AGN and non-AGN with
_p_ −values of 0.02 and 0.01, respectively. The AGN sample has
a low mean flux density ( _F_ 870µ _m_ = 2.0 ± 0.3 mJy) compared
with the non-AGN sample ( _F_ 870µ _m_ = 2.8 ± 0.2 mJy). Therefore,
it is possible that the difference in FIR sizes is partly related
to the difference in flux density, and not to the presence of an
AGN. To test this, we limit the samples to objects with flux densities < 4 mJy, and we find that the difference between AGN
and non-AGN becomes even larger: the mean size for AGN is
1.18 ± 0.12 kpc and for non-AGN is 1.80 ± 0.16 kpc ( _p_ −value of
the KS test is 0.03). The AGN sample has a stellar mass distribution slightly skewed to lower stellar masses (30% of objects have
_M_ ⋆ < 10 [10] M ⊙, median _M_ ⋆ = 10 [11][.][07] M ⊙ ), compared with the
non-AGN sample (3% of objects have _M_ ⋆ < 10 [10] M ⊙, median
_M_ ⋆ = 10 [11][.][21] M ⊙ ). If we consider only objects with _M_ ⋆ - 10 [11]
M ⊙, we still find a significant difference in the mean size of AGN
(1.06 ± 0.14 kpc) and non-AGN (1.70 ± 0.10 kpc).
As mentioned before, the observations of Tadaki et al. (2020)
are more sensitive to large scales than the other samples, and
therefore they may be more effective in recovering larger and
more diffuse dust emission. This could introduce a bias in our
comparison. To avoid it, we compare the sizes of AGN and nonAGN within the Tadaki et al. (2020) sample. We note that there
is no significant difference in the stellar mass or SFR distribution
of the AGN and non-AGN within this sample. Using the KS test,
we find that the FIR sizes of AGN are significantly smaller than

I. Lamperti et al.: SUPER V: obscured star formation and outflows







6


5


4


3


2


1









0

0 2 4 6 8 10
Flux density (870µm) [mJy]



0 2 4 6 8 10 12

N



Fig. 6: FIR effective radii versus observed-frame 870 µm flux density for our targets and other samples from the literature at similar
redshift ( _z_ ∼ 2), derived from ALMA observations at similar resolution (∼ 0.2”). The effective radii are measured assuming a
Gaussian profile for the Scholtz et al. (2020) and Chen et al. (2020) samples; an exponential profile for the Gullberg et al. (2019)
and Tadaki et al. (2020) sample; and a Sérsic profile with index _n_ between Gaussian and exponential for the Hodge et al. (2016)
sample. For the Gullberg et al. (2019) sample, we show the median value of the sample. For SUPER, we show the radii measured
from the fit of the visibilities assuming both a Gaussian and an exponential profile. Filled symbols are used for AGN and empty
symbols for galaxies with no AGN signature. The Gullberg et al. (2019) sample is a mixture of AGN and non-AGN. The histograms
on the right show the distributions of FIR effective radii for AGN (filled histogram) and star-forming galaxies with no AGN (empty
histogram), with the corresponding medians.



the ones of non-AGN ( _p_ −value = 0.03). To take into account the
uncertainties in the size measurements, we apply a Monte Carlo
approach. For each source, we draw 100 samples from a Gaussian distribution centred on the measured size and with standard
deviation equal to the uncertainty on the size. Then we perform
the KS test on the drawn samples. In 79% of the samples, the
KS test gives a _p_ −value< 0.05, meaning that the difference is
significant at the 79% level.
Some previous studies have also found smaller FIR sizes in
galaxies hosting AGN. For example, Chang et al. (2020) also
find smaller sizes in obscured IR-selected AGN compared to
non-AGN at _z_ ∼ 1. Furthermore, Lutz et al. (2018) find smaller
FIR sizes in nearby ( _z_ < 0.06) X-ray selected AGN than in nonAGN at the same FIR luminosity. Under the assumption that the
dust is spatially coincident with the gas reservoir, their interpretation is that a compact configuration of dust and gas favours
the accretion to the central SMBH. However, another interpretation is that the AGN are contributing significantly to the heating
of the diffuse dust in the central region of the galaxy, resulting
in more concentrated FIR emission in AGN host galaxies (e.g.
Schneider et al. 2015; Viaene et al. 2020; Di Mascia et al. 2021;
McKinney et al. 2021). On the other hand, Ni et al. (2021) recently reported a relation between the black hole accretion rate
and the compactness of the host galaxy using optical/NIR imaging. They also interpret this relation as a link between the black
hole growth and the central gas density.
The significance of the difference in dust size between AGN
and non-AGN presented in this paper is still limited by the sample size and by the lack of homogeneity in the samples (although
we have tried to minimise these as much as possible). In order to



confirm our result, it would be important to have a larger AGN
and control samples well matched in SFR, stellar mass, redshift
and with similar FIR sensitivity and resolution.


_5.3._ _ionised gas and FIR emission_


5.3.1. Origin of the H α emission


The Hα emission is sometimes used to trace the spatial distribution of unobscured star formation in AGN host galaxies. Previous studies have performed a variety of analyses to try to minimise the challenges in using Hα maps to investigate the impact of AGN outflows on star formation (Cano-Díaz et al. 2012;
Cresci et al. 2015a; Carniani et al. 2016). These challenges include the fact that part of the Hα flux could be due to the ionising
radiation of the AGN itself, and therefore special care should be
taken if we want to use it as a star formation rate tracer (e.g.
Scholtz et al. 2020). In addition, Hα can suffer from significant obscuration (see also Kewley et al. 2013a; D’Agostino et al.
2019). Therefore, if we want to use Hα as a SFR tracer we need
to determine what is the dominant contributor to the line emission and whether we can identify a component of the Hα emission that can be used to trace star formation in our sample.
Unlike Carniani et al. (2016), we were unable to identify
any residual emission beyond the components associated with
the AGN (i.e. the broad-line regions, AGN narrow line regions
and outflows, see Section 4.4). Therefore, we may expect the
Hα emission we have mapped to be dominated by AGN-related
processes. To verify this, in Figure 7 we use a BPT-like diagram (Baldwin et al. 1981) which uses the optical line ratios



Article number, page 17 of 32

_A&A proofs:_ manuscript no. SUPER_paper




[O iii]/Hβ and [N ii]/Hα to separate galaxies depending on the
different source of ionisation (HII region or AGN).
The black dashed curve is the separation between star formation and ‘composite’ (AGN/star-forming) at the mean redshift
of our sample ( _z_ = 2.3) from Kewley et al. (2013b). As a reference, we also show as a grey dashed curve the separation at
_z_ = 0 (Kauffmann et al. 2003). The upper panel shows the line
ratios measured from the total line profiles (narrow and broad
component), while the lower panel shows the line ratios of only
the narrow components. In the cases where Hβ is not detected,
based on a detection threshold of S/N> 3, we derive a 5σ lower
limit for the [O iii]/Hβ line ratio (see Sec. 4.3). Similarly, for the
cases where [N ii] is not detected, we show the 5σ upper limit for
the [N ii]/Hα line ratio. In some targets, both the Hα and [N ii]
lines are not detected, therefore the [N ii]/Hα line ratio is unconstrained (see box on the right).
Most of our objects lie above the division line when we consider the line ratios measured from the total profile (see upper
panel of Figure 7). This means that the emission is not dominated by star formation. This is not surprising, since these are
X-ray selected AGN. For two objects, the [N ii]/Hα line ratio is
unconstrained. If we assume that they have a similar [N ii]/Hα
line ratio as the other objects, they would be in the AGN region.
The only target which lies in the HII region is cid_346.
The targets remain in the same region of the BPT diagram
also when considering only the narrow component (see lower
panel of Figure 7). This again is not surprising given the fact
that our targets are bright AGN. Therefore, even if we were to
consider the narrow component separately, it would still be dominated by AGN emission in most of our galaxies. The only exception is cid_346, which lies in the HII part of the diagram both
when considering the total profile and when considering only the
narrow component. For this target, we do not see a large difference in the spatial distribution of the ‘narrow’ map and the map
that contains both the narrow and broad components. Thus, our
main conclusions would not change if we were to consider only
the narrow Hα component for cid_346.
In summary, the BPT analysis suggests that Hα emission is
dominated by AGN ionisation in most of our sample. As discussed in the next section, the central position of Hα and [O iii]
are in in agreement for most targets (see Figure 8). Our sources
lie within the scatter of the [O iii]-X-ray luminosity relation derived by Kakkad et al. (2020) using data from SUPER and from
X-ray selected AGN at _z_ ∼ 1.1 − 2.5 from the KASHz survey
(Harrison et al. 2016a). This suggests that the [O iii] emission
is mainly ionised by the AGN, as traced by the X-rays. Consequently, the similar spatial distribution of Hα and [O iii] supports
the idea that also the Hα emission is predominantly ionised by
the AGN.
For this analysis, we have considered spatially integrated
spectra, but there may be spatial variations in the line ratios and
some of the emission is probably more AGN dominated (e.g. towards the centre). Unfortunately, with the current resolution we
are not able to investigate spatial variations or de-couple AGN
and star formation contributions as done in Cano-Díaz et al.
(2012), Cresci et al. (2015a) and Carniani et al. (2016). Additionally, PSF-smearing could spread the AGN emission from the
central spaxels to the other spaxels, contaminating the Hα emission at larger scales, which may be originally dominated by star
formation.
Summarising, we are not able to use the Hα emission as a
good indicator of short term (∼ 10 Myr) star formation in our
sample. The FIR emission can provide information on the spatial location of the dust-obscured star formation, but in general


Article number, page 18 of 32



2.5



total emission − line profile

















2.5



only narrow components

















Fig. 7: Emission lines diagnostic diagrams. The curves show the
separation between star-forming galaxies and AGN at redshift
_z_ = 0 (grey) and _z_ = 2.3 (black) from Kewley et al. (2013a).
In the cases where one line is not detected (S/N< 3), the line
ratio is shown with an arrow indicating a 5σ upper (or lower)
limit. In the cases where both the Hα and [N ii] lines are not
detected, the [N ii]/Hα line ratio is unconstrained (see box on the
right). _Upper panel:_ The line ratios are measured from the total
emission line profile. _Lower panel:_ The line ratios are calculated
using the fluxes of only the narrow Gaussian component. For the
three targets for which the emission lines were fitted with only
one Gaussian component (marked with black crosses), the line
ratios are the same as in the upper panel.


it can trace SFR up to longer timescales (up to 100 Myr, Kennicutt & Evans 2012). As an alternative to Hα, star formation
on short timescales can be traced using rest-frame UV observations, which however could suffer from AGN contamination and
dust-obscuration as well.

I. Lamperti et al.: SUPER V: obscured star formation and outflows



5.3.2. Comparison of spatial distribution of FIR, optical, H α,
and [OIII] emission


In this section we compare the spatial distribution of the FIR,
optical, Hα and [O iii] emission. In Figure 3, we show the FIR
continuum contours, with the [O iii] and Hα contours overlaid,
created using the ‘central’ 600 km s [−][1] wide maps. We measure the positions of the FIR, Hα and [O iii] emission by fitting a 2D Gaussian to the images using the python routine
`scipy.optimize.curve_fit` (see Sec. 4.4). The positions of
the centroids are plotted as crosses on the images, with circles
indicating the corresponding 1σ uncertainties. The position of
the rest-frame optical continuum (see Section 4.2) is also shown
in lightblue.
In Figure 8 we directly compare the difference in position
between the FIR continuum, optical continuum, Hα and [O iii]
emission. The two targets with low S/N in the ALMA maps are
marked with empty symbols.
The rest-frame optical continuum emission is in general
agreement with the position of the FIR continuum (see left panel
of Figure 8). The offset between optical and FIR continuum is
smaller than the uncertainties for all targets, with the exception of cid_1057 and X_N_81_44. cid_1057 has low S/N in the
ALMA maps (S/N= 3.6), therefore, the FIR position is not well
constrained. X_N_81_44 shows an offset larger than the uncertainties, but still small (< 0.05”). In the Type 1s, the optical continuum is dominated by the AGN emission, while in the Type
2s it is probably tracing the stellar disk, since the central AGN is
obscured. The good alignment between the FIR continuum emission and the optical continuum suggests that the FIR is aligned
with the host galaxy position. Unfortunately, we do not have
other information about the host galaxy morphology. For three
sources, there are HST/WFC3 images available, but the images
show only strong point sources, so we cannot derive any information about the host galaxy morphology.
For the majority of the sources with reliable FIR positions
(4/6), the Hα and [O iii] centroid positions are not consistent
with the FIR position (difference larger than 1σ, see Figure 8).
The offsets between the FIR and Hα position are in the range
0.3 − 1.9 kpc, with a mean offset of 0.8 ± 0.2 kpc. The offsets
between the FIR and [O iii] are in the range 0.2 − 1.8 kpc, with a
mean offset of 1.0 ± 0.2 kpc. Two objects have an offset > 1 kpc,
both for Hα and [O iii]: XID419 and cid_1143. We compare our
results with the work by Scholtz et al. (2020), who measured
the offset between the FIR emission and the Hα emission in a
sample of eight AGN at redshift 1.4 − 2.6. They found projected
offsets between Hα and FIR in the range 0.8 − 2.8 kpc, with a
mean offset of 1.4 ± 0.6 kpc. The offsets found by Scholtz et al.
(2020) are a bit larger but consistent with our findings. However,
we note that their rest-frame optical observations have a lower
spatial resolution (FWHM PSF ∼ 0.6 − 1”) compared to the AO
observations presented here.
To summarise, we find that the centroid of the FIR emission
is on average offset (> 1σ, see star symbols in Fig. 8) from the

[O iii] and Hα centroids. However, we note that there can still be
significant overlap between the emissions even if the centroids
are offset. One possible explanation of the offset is that the dust
and the ionised gas have different locations. Another possibility
is that the outflow component is contributing substantially also in
the central velocity channel ( _v_ = [−300, 300] km s [−][1] ). In the next
Section 5.4, we compare the position of the [O iii] emission in the
central velocity channel with the emission in the blue-shifted and
red-shifted channels ( _v_ < −300 km s [−][1] and _v_ - 300 km s [−][1] ). For
XID36 and cid_451, the morphology and position of the [O iii]



emission is similar in the three velocity channels, which suggests
that the outflow component may contribute significantly also in
the central velocity channels. For the other targets, the morphology and position of the emission in the three channels are different, suggesting that the central [O iii] channel is not strongly
contaminated by the outflow component.
It is also possible that the dust is obscuring part of the Hα
and [O iii] emission, especially where the peak of the dust emission is located. Unfortunately, in most of our objects, we do not
have a measurement of the Balmer decrement, because of the
low S/N of the Hα and Hβ emission lines. However, even the
Balmer decrement could underestimate the level of obscuration,
because in the most obscured regions the ionised gas emission
may be totally obscured by dust (see Chen et al. 2020). The fact
that the Hα and FIR emission are not co-spatial has implications
if we want to use the Hα emission to trace the total star formation in the host galaxies. First, the assumption that Hα emission
is dominated by star formation is likely not to be true in most
of our cases (see Section 5.3.1). Second, even if we could derive
the extinction correction for the Hα emission, we would still not
be able to recover the total SFR of the galaxy since we would not
be sampling the same region as that covered by the FIR emission
(e.g. Brusa et al. 2018).
In Figure 3, which presents the Hα and [O iii] maps, we also
show the position angle along the major axis of the FIR emission for the three targets where it can be reliably determined
(XID419, cid_346, and cid_1143). The Hα and [O iii] emission
are offset from the FIR emission in a direction roughly perpendicular to the FIR major axis. This could be indicative of AGN
ionisation cones, extending perpendicular to the plane of the
galaxy (e.g. Crenshaw et al. 2010; Venturi et al. 2017, 2018).
This would favour a scenario where a significant fraction of the
ionised gas has a different locations with respect to the FIR emission. However, we cannot rule out that dust is obscuring part of
the ionised gas emission.
The Hα and [O iii] positions are in general in agreement with
each other, with offsets in the range 0.3 − 1.5 kpc and mean offset 0.6 ± 0.1 kpc (see fourth panel in Figure 8). Only two objects (X_N_81_44 and cid_346) show a Hα-[O iii] offset larger
than the uncertainties. In X_N_81_44 the morphologies of Hα
and [O iii] emission are also different, extending in two almost
perpendicular directions. In cid_346 instead the Hα distribution
is similar to the FIR distribution, while [O iii] is more extended
in the S-E direction. We note that cid_346 is the only object in
our sample which is classified in the HII region according to the
emission line diagnostic diagram (see Section 5.3.1). The offset
between Hα and [O iii] could be a result of the fact that they are
ionised by different mechanisms (AGN for [O iii] and star formation for Hα).
Following Chen et al. (2020) and Scholtz et al. (2020), we
also compare the sizes of the FIR, Hα, and [O iii] emission in
Figure 9. We use the FIR sizes derived with the best model fit
of the _uv_ -visibilities. In general, the Hα and [O iii] sizes are
comparable or larger than the FIR sizes. The only exception
is cid_1143, for which the upper limits on the Hα and [O iii]
sizes are smaller that the FIR sizes. We note that the FIR emission of this object is significantly elongated (axis ratio = 4.6).
A possible interpretation is that the dust emission is tracing
the stellar disk of this galaxy (seen edge-on), and the ionised
gas is more extended out of the galaxy plane. The mean ratios are _R_ _e_ (Hα)/ _R_ _e_ (FIR) = 1.87 ± 0.45 and _R_ _e_ ([O iii])/ _R_ _e_ (FIR)
= 1.50 ± 0.23. Larger Hα sizes compared to FIR sizes have also
been observed by Scholtz et al. (2020), Chen et al. (2020) and
Tadaki et al. (2020), who find mean ratio _R_ _e_ (Hα)/ _R_ _e_ (FIR) of


Article number, page 19 of 32

_A&A proofs:_ manuscript no. SUPER_paper





0.4


0.3


0.2


0.1


0.0


0.1


0.2


0.3



|XN8144<br>X_ ID3_6 _<br>XID419<br>cid1057<br>_|cid346<br>cid_<br>451<br>cid_ 1205<br>cid_ 1143<br>_<br>2kpc<br>1kpc|
|---|---|
||FIR −opt.|


0.3 0.2 0.1 0.0 0.1 0.2 0.3

∆R. A. [arcsec]





|Col1|2kpc<br>1kpc|
|---|---|
||FIR −Hα|


0.3 0.2 0.1 0.0 0.1 0.2 0.3

∆R. A. [arcsec]



|Col1|2kpc<br>1kpc|
|---|---|
||FIR −[OIII]|


0.3 0.2 0.1 0.0 0.1 0.2 0.3

∆R. A. [arcsec]



|Col1|2kpc<br>1kpc|
|---|---|
||Hα −[OIII]|


0.3 0.2 0.1 0.0 0.1 0.2 0.3

∆R. A. [arcsec]



Fig. 8: Comparison of the centroid positions of the 2D Gaussian fit to the images of (from left to right): FIR and optical continuum,
FIR and Hα emission, FIR and [O iii] emission, and Hα and [O iii] emission. The coordinates are derived from the centroid of a 2D
Gaussian fit to the images. The Hα and [O iii] images were created by integrating the spectra over the [-300,300] km s [−][1] velocity
range. The uncertainties on the position combine the uncertainties on the coordinate registration, on the Gaussian fit and the pixel
size. The objects with a significant offset (i.e. difference in R.A. or Dec. larger than the 1σ uncertainty) are shown as star symbols in
each plot, while the ones with no significant offset are shown as circles. The dashed circles show the offset corresponding to 1 kpc
and 2 kpc at the median redshift of the sample. The two objects with ALMA low S/N< 8 are shown as empty symbols (cid_1057
and cid_451). The position of the Hα and [O iii] centroids are in fairly good agreement, while the FIR centroids show larger offset
to the centroid positions of the ionised gas (both Hα and [O iii]).



3.1 ± 0.6, 2.1 ± 0.3, and 2.3 respectively. These studies find on
average larger Hα sizes (and larger _R_ _e_ (Hα)/ _R_ _e_ (FIR) ratios) compared to our observations. The difference could be due to the
fact that our AO observations are missing part of the more extended flux (Förster Schreiber et al. 2018). Additionally, in our
case we cannot exclude that the FIR sizes are underestimated because the high-resolution ALMA observations are not sensitive
to more diffuse emission.
The larger sizes of the ionised gas emission compared to the
FIR sizes could be due to different reasons. One possibility is
that the ionised gas is more extended because of the AGN, that
ionises the gas to larger distances (e.g. Scholtz et al. 2020).
However, larger Hα sizes compared to the FIR have been observed also in star-forming galaxies not hosting AGN (Chen
et al. 2020; Tadaki et al. 2020). In _z_ ∼ 2 star-forming galaxies,
the optical continuum is found to be systematically larger than
the FIR sizes by a factor of 2 − 3, suggesting that the FIR emission is tracing a compact star-burst region (e.g. Barro et al. 2016;
Tadaki et al. 2017; Fujimoto et al. 2017, 2018; Elbaz et al. 2018;
Calistro Rivera et al. 2018; Lang et al. 2019; Puglisi et al. 2019).
It is interesting to note that Popping et al. (2021) use simulations
to show that the larger rest-frame optical sizes are due to higher
dust-obscuration in the centre of galaxies which artificially increases the derived sizes in this band, and that the FIR emission
is not intrinsically more compact than the stellar distribution.


_5.4._ _ionised outflows and star formation_


In this section, we qualitatively compare the spatial distribution
of the [O iii] outflows and star formation. As we have shown in
Section 5.1, the rest-frame 260 µm emission in our targets is
mostly due to star formation, while we cannot rely on the Hα
emission as a star formation indicator. Thus, here we focus on
the spatial comparison of the outflows and FIR emission.
Following Kakkad et al. (2020), we define as outflow the

[O iii] emission with absolute velocities - 300 km s [−][1] with respect to the zero velocity (see Section 4.4). In Figure 10 we show
the [O iii] maps in three velocity channels: blue-shifted emission


Article number, page 20 of 32



< -300 km s [−][1], central emission [-300, 300] km s [−][1], and redshifted emission > 300 km s [−][1] . We create the maps by collapsing the continuum subtracted spectra over the selected velocity
channels for each spaxel. We check that our conclusions are not
sensitive to the choice of the threshold adopted to select the blueor red-shifted emission (i.e. absolute velocities - 300 km s [−][1] ).
By selecting only the extreme velocity wings (e.g. - 600 km
s [−][1] ), the qualitative conclusions remain the same.

All our targets apart from cid_1205 show blue-shifted emission (above 4σ), in agreement with the analyses of Kakkad et al.
(2020) on the Type 1 targets. We note that the [O iii] data-cube
of cid_1205 presents an artefact (horizontal stripe) south of the
target. After removing the artefact, we do not see significant
emission in the blue-shifted map, but we cannot exclude that
a faint outflow could be undetected. However, since the [O iii]
spectrum of this target shows only a weak emission at velocities
< −300 km s [−][1], we do not expect a strong [O iii] outflow in this
target.

From the [O iii] line profiles, we can see that the blue-wing is
generally more prominent than the red-wing. This effect can be
due to dust that is obscuring the receding side of the outflow (e.g.
Bae & Woo 2016). The more extended blue-shifted emissions
(> 4.5 kpc) are detected in cid_1143, and cid_1057. The redshifted emission is fainter and detected above 5σ in only 5/8
objects (X_N_81_44, XID36, cid_1057, cid_451 and cid_1205).
These objects show a significantly extended (∼ 2.5 kpc) redshifted emission.

The shape of the outflow is certainly also a function of the
viewing angle. In XID36 and cid_451, the blue-shifted emission
is symmetric (not elongated) and the shape is similar to the emission in the central velocity channel. A possible interpretation is
that the outflow is aligned in the direction of our line-of-sight.
On the contrary, in cid_1143 and cid_1057 the outflow has an
extended and biconical shape which is suggesting that our line
of sight is almost perpendicular to it. In particular, in cid_1143,
the direction of the outflow is perpendicular to the major axis of
the FIR emission. If the stellar disk is oriented as the dust emission, this may suggest that the outflow is moving along the path

I. Lamperti et al.: SUPER V: obscured star formation and outflows



5


4


3


2


1







1 2 3 4 5
R e (FIR) [kpc]


Fig. 9: Comparison of the size of the FIR emission with the
sizes of the Hα (red) and [O iii] (blue) emission. The effective
radii of the FIR emission are measured from the best fit on the
visibilities. The Hα and [O iii] sizes are measured by fitting a
2D Gaussian to the images. If the measured size is smaller than
the beam, we show the point as an upper limit. The two objects
with low S/N (< 8) in the ALMA data are not shown (cid_1057
and cid_451). The FIR and Hα sizes of the sample of _z_ ∼ 2
AGN from Scholtz et al. (2020) and from Chen et al. (2020) are
shown with violet circles and magenta diamonds, respectively.
The white diamonds are non-AGN from Chen et al. (2020). On
average, the FIR sizes are smaller than the Hα and [O iii] sizes
by a factor of ∼ 2.


of least resistance, which is perpendicular to the disk (Gabor &
Bournaud 2014).
Under the assumption that the FIR emission is a reliable
tracer of the SFR, we do not see evidence that the obscured star
formation is suppressed or disturbed in the location of the outflow. We discuss this result further in the next section.


_5.5._ _Implications of our results_


The main goal of this study is to trace with high spatial resolution
the star formation in the host galaxies of AGN with powerful
outflows, to assess the impact that these may have on the mass
build-up of the galaxies.
Since our targets are powerful AGN, we expected the Hα
maps to be contaminated by AGN emission. Our BPT analysis
confirms that for all but one target (cid_346) the Hα emission
is AGN dominated. Thus, we cannot use Hα as a star formation
tracer in our sample and we have to rely only on the FIR, which
traces obscured star formation.
In this study, we use the monochromatic FIR emission at
∼ 260 µm to trace obscured star formation. This relies on the
assumption that spatial variations of the shape of the FIR SED
(due to changes in the dust properties, as for example the dust
temperature and emissivity index β) are negligible. Under this
assumption, the single FIR image can be translated into a map
of the FIR luminosity and, consequently, of the obscured SFR. In
order to test how spatial variations in the dust temperature may



affect our results, we would need spatially resolved FIR observations at other wavelengths.

As described Section 5.4, we do not find any evidence of the
ionised outflows instantaneously regulating the star formation in
their host galaxies, for example, through cavities or ‘holes’ in
the FIR emission. Similar results are reported by Balmaverde
et al. (2016), who study a sample of quasars at _z_ < 1 and find
that quasars with strong outflows do not show lower SFR than
those with weaker outflows. Other spatially-resolved studies of
AGN at _z_ ∼ 1.4 − 2.6 also find no evidence of instantaneous star
formation suppression due to the ionised outflows (Scholtz et al.
2020; Scholtz et al. 2021).

When looking for evidence of AGN feedback on star formation, we need to consider the timescales of the star formation
tracer we are using. If the impact of the AGN on the level of
star formation is on short timescales, then a star formation rate
tracer too sensitive to the past star formation history of the galaxy
may dilute the feedback signature. The FIR is commonly believed to trace star formation on timescales of ∼ 100 Myr. However, some studies find no significant difference in the SFR measured from the FIR and from Hα in star-forming galaxies (e.g.
Lam et al. 2013; Dominguez-Sanchez et al. 2014; Rosario et al.
2016), which is believed to measure SFR on shorter timescales
(∼ 10 Myr). This would suggest that the FIR traces similar
star formation timescales as the Hα emission. However, this result may depend on the star formation history of the individual galaxies. In this context, it would then be very interesting
to have an alternative and reliable tracer of the star formation
on short timescales. Standing the limitations of using Hα or the
UV emission for AGN hosts, an alternative could be to use the
mid-infrared PAHs features which would be accessible at these

redshifts with JWST.

On the other hand, it is also possible that the outflow needs
some time to produce an effect on the star formation. Thus, there
is a delay between the moment the outflow is visible and when
the star formation decreases. Episodes of AGN activity happen
on shorter timescales compared to timescales of star formation
variations (Gabor & Bournaud 2014; Hickox et al. 2014). The
outflow may need more time to remove a substantial quantity of
gas from the host galaxy and cause a suppression of star formation. Simulations by Gabor & Bournaud (2014) show that
AGN-driven outflows do not cause instantaneous quenching, but
they may remove a substantial amount of gas on long timescales
(≳ Gyr). Recently, Costa et al. (2020) found that AGN feedback
acts in two modes in their simulations: a rapid mode that removes dense gas from the nucleus, and a slower mode that prevents halo gas accretion. The first mode alone will not cause a
decrease in the star formation, but the combination of the two
modes will suppress star formation in the long-term. Some observations show that high-redshift AGN host galaxies may have
lower molecular gas fractions, the fuel for star formation, compared to mass-matched star-forming galaxies at high redshift
(e.g. Kakkad et al. 2017; Circosta et al. 2021). Over time, this
should be visible as an impact on the star formation itself.

Moreover, we need to consider also the physical scales that
we are sampling in this study. We do not see signs of star formation suppression at the scales probed by our observations
(≥ 2 kpc), but it is possible that the impact of the outflows is
only visible at smaller scales. Outflows may influence star formation only in a small region of the galaxy, on scale < 1 kpc (e.g.
Croft et al. 2006; Alatalo et al. 2015; Cresci et al. 2015b; Querejeta et al. 2016; Rosario et al. 2019; Shin et al. 2019; Husemann
et al. 2019).


Article number, page 21 of 32

_A&A proofs:_ manuscript no. SUPER_paper







v = [−300, 300] km s [−][1]









0.25


-0.25






v      - 300 km s [−][1]



0.5 0.25 0 -0.25 -0.5
∆R. A. [arcsec]



0.5 0.25 0 -0.25 -0.5
∆R. A. [arcsec]



v < −300 km s [−][1]



v = [−300, 300] km s [−][1]







0.25


0


-0.25





∆R. A. [arcsec]



∆R. A. [arcsec]



∆R. A. [arcsec]





v [km s [−][1] ]





















v      - 300 km s [−][1]



0.75 0.38 0 -0.38 -0.75
∆R. A. [arcsec]





v < −300 km s [−][1]









0.25


0







v < −300 km s [−][1]















0.75 0.38 0 -0.38 -0.75
∆R. A. [arcsec]



v = [−300, 300] km s [−][1]


0.5 0.25 0 -0.25 -0.5
∆R. A. [arcsec]


v = [−300, 300] km s [−][1]


0.75 0.38 0 -0.38 -0.75
∆R. A. [arcsec]



v      - 300 km s [−][1]



2000 1500 1000 500 0 500 1000 1500 2000
v [km s [−][1] ]



Fig. 10: Maps of [O iii] emission in three different velocity channels: blue-shifted emission (< -300 km s [−][1], _first_ _column_ ), central
channel ([-300, 300] km s [−][1], _second_ _column_ ), red-shifted emission (> 300 km s [−][1], _third_ _column_ ). The interval over which the
spectrum has been integrated is indicated on the right plot. In black are the [O iii] emission contours starting from 2σ and increasing in intervals of 1σ (and in intervals of 2σ for XID36, cid_451 and cid_1143, to improve presentation). In white are the FIR
emission contours, starting from 2σ and increasing in intervals of 2σ (or intervals of 4σ for X_N_81_44 and cid_346, to improve
presentation). Negative -2σ contours are shown with dashed curves. The grey ellipse shows the size of the ALMA beam, while the
white scale-bar shows the size of the PSF of the [O iii] image in kpc. The blue cross and circle show the position and uncertainty
of the optical continuum. The lightblue bar indicates the position angle along the major axis of the FIR emission, when it can be
reliably determined (see Section 3.3.1). _Fourth column:_ spectrum around the [O iii]λ5007 emission line. The coloured areas show
the spectral regions over which the emission was integrated to create the three images on the left.


Article number, page 22 of 32

I. Lamperti et al.: SUPER V: obscured star formation and outflows



v      - 300 km s [−][1]



v < −300 km s [−][1]



























v = [−300, 300] km s [−][1]





























0.5 0.25 0 -0.25 -0.5
∆R. A. [arcsec]



0.5 0.25 0 -0.25 -0.5
∆R. A. [arcsec]



0.5 0.25 0 -0.25 -0.5
∆R. A. [arcsec]



2000 1500 1000 500 0 500 1000 1500 2000
v [km s [−][1] ]



Fig. 10: Continued.



There is also the possibility that the interaction between the
outflow and the ISM is limited. We observe that, at least in two
targets (cid_346 and cid_1143), the ionised gas is located preferentially perpendicular to the dust. This may indicate that the outflow is propagating following the path of least resistance. Simulations have shown that AGN-driven outflows propagate preferably away from the plane of the galaxy, avoiding dense gas regions in the galactic disk (Gabor & Bournaud 2014; Costa et al.
2014; Mukherjee et al. 2016).
To interpret our results, we also need to consider how representative of the parent population our sample is. Due to the requirement to have FIR detections, our targets tend to have higher
SFRs compared to the average of the parent SUPER sample, in
which there are many SFR upper limits (see Figure 1). Additionally, our sample has a higher SSFR compared to the average
of the parent population of X-ray AGN at _z_ ∼ 2 (Scholtz et al.
2018). It is possible that if we were to target AGN with lower
SFRs, we would be more likely to observe localised suppression
of star formation, since the total star formation level is lower. To
test this hypothesis, it would require deep ALMA continuum observations to get spatially resolved maps of the dust continuum
emission for the whole SUPER sample.


**6.** **Summary and conclusions**


We present ALMA Band 7 observed-frame 870 µm (rest-frame
∼ 260 µm) continuum high-resolution (∼0.2”, corresponding to
∼2 kpc) observations of eight X-ray AGN at redshift _z_ ∼2 from



the SUPER sample. The ALMA targets were selected from the
parent SUPER sample based on photometric detections in the
FIR (i.e. observed wavelength 24 − 870 µm) and [O iii] detections in the SINFONI IFS maps. The selected sample has a range
of bolometric luminosities which is representative of the parent
sample ( _L_ _bol_ = 10 [44][.][9] − 10 [46][.][8] erg s [−][1] ). They have SFRs in the
range 8−380 _M_ ⊙ yr [−][1] and most of the targets lie near the star formation main-sequence, with the exception of cid_1143 that lies
below (see Figure 1). The main conclusions of this work are:


**–** We detect 6/8 of our targets with S/N> 8 in the ALMA
rest-frame 260 µm continuum maps. The rest of the conclusions are based on these six high S/N targets. We model
the 260 µm data in the visibilities versus _uv_ -distance space
using different models (point source, Gaussian, exponential
profile, Gaussian+point source). From the ‘best fit’ models,
we measure flux densities in the range 0.27 − 2.58 mJy and
half-light radii in the range _R_ _e_ = 0.83 − 2.01 kpc (median
1.31 ± 0.23 kpc) (Section 3.3).


**–**
From the SED decomposition, we find that the contribution
of AGN-heated dust to the total rest-frame 260 µm emission
is ≤ 4% in our sample. The contribution from synchrotron
emission from AGN is small in most of the targets (< 1%).
We conclude that the main contribution to the 260 µm flux
is due to dust heated by star formation (see Section 5.1).


**–**
We compare the FIR sizes of our sample with other samples
of SFGs and AGN at similar redshift, for which the FIR


Article number, page 23 of 32

_A&A proofs:_ manuscript no. SUPER_paper



sizes are measured from ALMA (observed-frame) 870 µm
observations of similar resolution and sensitivity (see
Section 5.2, Figure 6). Our sample is in agreement with
literature samples of redshift-matched star-forming and
AGN host galaxies. Across these samples, we find that the
mean FIR size of AGN ( _R_ _e_ = 1.16 ± 0.11 kpc) is smaller
than the mean FIR size of non-AGN ( _R_ _e_ = 1.69 ± 0.13 kpc).
A possible interpretation is that a compact dust/gas configuration favours the accretion to the central SMBH.


**–** We use the redshift-dependent BPT diagnostic diagram
from Kewley et al. (2013a,b) to identify the main process
responsible for gas ionisation in our sample (Figure 7). Most
of our objects lie in the AGN region, with the exception
of cid_346 (see Section 5.3.1). We find a good agreement
between the spatial distribution of Hα and [O iii] in most of
the targets (see Section 5.3.2, Figure 3). This suggests that
the same mechanism responsible for the [O iii] emission,
that is the AGN, is also partly responsible for the Hα
emission. Only two objects (X_N_81_44 and cid_346)
show a significant offset between the peak of Hα and [O iii]
emission, which could be a sign that there are different
contributions from the ionisation sources or it could be due
to differential obscuration. In summary, across our sample
we do not identify any Hα emission that we can confidently
use to trace star formation.


**–** We observe different spatial distributions of ionised gas and
FIR emission (Figure 3, Figure 8). Specifically, in most of
our targets (4/6) there is a significant offset between the
central position of the ionised gas emission and the FIR
emission (0.4 − 1.9 kpc). We also find that the ionised gas
emission tends to be larger than the FIR emission by a
factor of ∼ 1.7 (Figure 9). Most strikingly, in two sources
(cid_1143 and cid_346) we observe that the ionised gas is
perpendicular to the dust emission. All of these observations
provides further evidence that dust and ionised gas emission
are not directly associated in our sample, with the dust most
likely to be tracing the host galaxy and the ionised gas most
likely to be tracing the AGN emission-line regions.


**–** Comparing the position of the [O iii] blue-shifted emission
with the FIR emission (Figure 10), we find that the FIR emission is unaffected by the ionised outflow. Assuming that the
FIR is tracing the obscured star formation, we see no evidence for star formation suppression due to the ionised outflows at the scale probed by our observations (∼ 2 kpc).
However, we do not have a resolved map of an alternative
and reliable tracer of only recent star formation. Additionally, the outflow may need longer timescales to significantly
affect star formation. In at least two objects (cid_346 and
cid_1143), the outflow is almost perpendicular to the direction of the major axis of the FIR emission, which can be an
indication that the outflow propagates following the path of
least resistance.


We do not observe any evidence in this study for ionised outflows directly influencing star formation. However, one limitation is that our sample may be biased to relatively high SFRs.
To confirm that the ionised outflows do not have an impact on
star formation, we need to obtain spatially-resolved FIR maps
also for the SUPER targets with lower SFRs. Furthermore, future IFS observations with higher spatial resolution (e.g. with
ELT/HARMONI) will help to get spatially-resolved emission

Article number, page 24 of 32



line ratio diagnostics that will allow us to map and identify the
ionisation sources of Hα in a spatially-resolved way.


_Acknowledgements._ We thank the anonymous referee for carefully reading the
paper and providing constructive comments. We thank Ian Smail and Bitten
Gullberg for helping us to understand the data of the AS2UDS sample. I.L. acknowledges support from the Comunidad de Madrid through the Atracción de
Talento Investigador Grant 2018-T1/TIC-11035. M.P. is supported by the Programa Atracción de Talento de la Comunidad de Madrid via grant 2018-T2/TIC11715. C.C.C. acknowledges support from the Ministry of Science and Technology of Taiwan (MOST 109-2112-M-001-016-MY3). D.M.A. and D.J.R. acknowledge support from STFC (ST/T000244/1). A.P. gratefully acknowledges
financial support from STFC through grants ST/T000244/1 and ST/P000541/1.
G.V. acknowledges financial support from Premiale 2015 MITic (PI B. Garilli). This paper is based on observations collected at the European organisation for Astronomical Research in the Southern Hemisphere under ESO programme 196.A- 0377. This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2018.1.00992.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in
cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Based in part on data products produced by TERAPIX and the Cambridge Astronomy Survey Unit on behalf
of the UltraVISTA consortium. Based on observations obtained as part of the
VISTA Hemisphere Survey, ESO Progam, 179.A-2010 (PI: McMahon). This
work has made use of data from the European Space Agency (ESA) mission _Gaia_
( `[https://www.cosmos.esa.int/gaia](https://www.cosmos.esa.int/gaia)` ), processed by the _Gaia_ Data Processing and Analysis Consortium (DPAC, `[https://www.cosmos.esa.int/web/](https://www.cosmos.esa.int/web/gaia/dpac/consortium)`
`[gaia/dpac/consortium](https://www.cosmos.esa.int/web/gaia/dpac/consortium)` ). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the _Gaia_ Multilateral Agreement. The `Starlink` software (Currie et al. 2014) is currently
supported by the East Asian Observatory. This research has made use of the
NASA/IPAC Extragalactic Database (NED) which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration. This research made use of Astropy,
a community-developed core Python package for Astronomy (The Astropy Collaboration et al. 2013), `Matplotlib` (Hunter 2007) and `NumPy` (Van Der Walt
et al. 2011). This research used the `TOPCAT` tool for catalogue cross-matching
(Taylor 2005), the `Stan` interface for Python `PyStan` (Stan Development Team
2018), and `APLpy`, an open-source plotting package for Python (Robitaille &
Bressert 2012).


**References**


Aird, J., Coil, A. L., & Georgakakis, A. 2017, Monthly Notices of the Royal
Astronomical Society, 465, 3390
Akaike, H. 1973, Information theory and an extension of the maximum likelihood principle, in: B.N. Petrov and F. Csaki, eds., 2nd international symposium on information theory (Akademiai Kiado, Budapest), 267–281
Akaike, H. 1974, IEEE Transactions on Automatic Control, 19, 716
Alatalo, K., Lacy, M., Lanz, L., et al. 2015, The Astrophysical Journal, 798, 31
Bae, H.-J. & Woo, J.-H. 2016, The Astrophysical Journal, 828, 97
Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, Astronomical Society of
the Pacific, 93, 5
Balmaverde, B., Marconi, A., Brusa, M., et al. 2016, A&A, 585, A148
Barro, G., Kriek, M., Pérez-González, P. G., et al. 2016, The Astrophysical Journal Letters, 827, L32
Becker, R. H., White, R. L., & Helfand, D. J. 1995, Astrophysical Journal v.450,
450, 559
Behroozi, P. S., Wechsler, R. H., & Conroy, C. 2013, The Astrophysical Journal,
770, 57
Bolzonella, M., Kovac, K., Pozzetti, L., et al. 2010, A&A, 524, A76
Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103
Boroson, T. A. & Green, R. F. 1992, Astrophysical Journal Supplement Series
(ISSN 0067-0049), 80, 109
Bouwens, R., Gónzalez-López, J., Aravena, M., et al. 2020, The Astrophysical
Journal, 902, 112
Brinchmann, J., Charlot, S., White, S. D. M., et al. 2004, Monthly Notices of the
Royal Astronomical Society, 351, 1151
Brusa, M., Cresci, G., Daddi, E., et al. 2018, A&A, 612, A29
Burgarella, D., Buat, V., & Iglesias-Páramo, J. 2005, Monthly Notices of the
Royal Astronomical Society, 360, 1413
Calistro Rivera, G., Hodge, J. A., Smail, I., et al. 2018, The Astrophysical Journal, 863, 56
Calistro Rivera, G., Lusso, E., Hennawi, J. F., & Hogg, D. W. 2016, The Astrophysical Journal, 833, 98
Cano-Díaz, M., Maiolino, R., Marconi, A., et al. 2012, A&A, 537, L8

I. Lamperti et al.: SUPER V: obscured star formation and outflows



Carniani, S., Marconi, A., Maiolino, R., et al. 2016, A&A, 591, A28
Carpenter, B.,, Gelman, A., et al. 2017, Journal of Statistical Software, Articles,
76, 1
Casey, C. M., Narayanan, D., & Cooray, A. 2014, Physics Reports, 541, 45
Chabrier, G. 2003, The Publications of the Astronomical Society of the Pacific,
115, 763
Chang, Y.-Y., Le Floch, E., Juneau, S., et al. 2020, The Astrophysical Journal,
888, 44
Chen, C.-C., Harrison, C. M., Smail, I., et al. 2020, A&A, 635, A119
Chen, C.-C., Hodge, J. A., Smail, I., et al. 2017, The Astrophysical Journal, 846,
108
Chen, C.-C., Smail, I., Swinbank, A. M., et al. 2015, The Astrophysical Journal,
799, 194
Cheng, C., Ibar, E., Smail, I., et al. 2020, Monthly Notices of the Royal Astronomical Society, 499, 5241
Choi, E., Somerville, R. S., Ostriker, J. P., Naab, T., & Hirschmann, M. 2018,
The Astrophysical Journal, 866, 91
Cicone, C., Brusa, M., Ramos Almeida, C., et al. 2018, Nature Astronomy, 2,
176
Circosta, C., Mainieri, V., Lamperti, I., et al. 2021, A&A, 646, A96
Circosta, C., Mainieri, V., Padovani, P., et al. 2018, A&A, 620, A82
Civano, F., Marchesi, S., Comastri, A., et al. 2016, The Astrophysical Journal,
819, 62
Condon, J. J. 1997, Publications of the Astronomical Society of the Pacific, 109,
166
Costa, T., Pakmor, R., & Springel, V. 2020, Monthly Notices of the Royal Astronomical Society, 497, 5229
Costa, T., Sijacki, D., & Haehnelt, M. G. 2014, Monthly Notices of the Royal
Astronomical Society, 444, 2355
Crenshaw, D. M., Schmitt, H. R., Kraemer, S. B., Mushotzky, R. F., & Dunn,
J. P. 2010, The Astrophysical Journal, 708, 419
Cresci, G., Mainieri, V., Brusa, M., et al. 2015a, The Astrophysical Journal, 799,
82
Cresci, G. & Maiolino, R. 2018, Nature Astronomy, 2, 179
Cresci, G., Marconi, A., Zibetti, S., et al. 2015b, A&A, 582, A63
Croft, S., van Breugel, W., de Vries, W., et al. 2006, The Astrophysical Journal,
647, 1040
Currie, M. J., Berry, D. S., Jenness, T., et al. 2014, in Astronomical Data Analysis
Software and Systems XXIII. Proceedings of a meeting held 29 September 3 October 2013 at Waikoloa Beach Marriott, 391–
D’Agostino, J. J., Kewley, L. J., Groves, B. A., et al. 2019, Monthly Notices of
the Royal Astronomical Society: Letters, 485, L38
Dale, D. A., Helou, G., Magdis, G. E., et al. 2014, The Astrophysical Journal,
784, 83
Di Mascia, F., Gallerani, S., Behrens, C., et al. 2021, Monthly Notices of the
Royal Astronomical Society
Dicken, D., Tadhunter, C., Morganti, R., et al. 2008, The Astrophysical Journal,
678, 712
Dominguez-Sanchez, H., Bongiovanni, A., Lara-López, M. A., et al. 2014,
Monthly Notices of the Royal Astronomical Society, 441, 2
Donley, J. L., Koekemoer, A. M., Brusa, M., et al. 2012, The Astrophysical Journal, 748, 142
Duras, F., Bongiorno, A., Piconcelli, E., et al. 2017, A&A, 604, A67
Elbaz, D., Daddi, E., Le Borgne, D., et al. 2007, A&A, 468, 33
Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616, A110
Fabian, A. C. 2012, Annual Review of Astronomy and Astrophysics, 50, 455
Falkendal, T., De Breuck, C., Lehnert, M. D., et al. 2019, A&A, 621, A27
Feruglio, C., Fiore, F., Carniani, S., et al. 2015, A&A, 583, A99
Förster Schreiber, N. M., Renzini, A., Mancini, C., et al. 2018, The Astrophysical
Journal Supplement Series, 238, 21
Fritz, J., Franceschini, A., & Hatziminaoglou, E. 2006, Monthly Notices of the
Royal Astronomical Society, 366, 767
Fujimoto, S., Ouchi, M., Kohno, K., et al. 2018, The Astrophysical Journal, 861,
7
Fujimoto, S., Ouchi, M., Shibuya, T., & Nagai, H. 2017, The Astrophysical Journal, 850, 83
Gabor, J. M. & Bournaud, F. 2014, Monthly Notices of the Royal Astronomical
Society, 441, 1615
Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1
Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1
Gallagher, R., Maiolino, R., Belfiore, F., et al. 2019, Monthly Notices of the
Royal Astronomical Society, 485, 3409
Grimmett, L. P., Mullaney, J. R., Bernhard, E. P., et al. 2020, Monthly Notices of
the Royal Astronomical Society, 495, 1392
Gullberg, B., Smail, I., Swinbank, A. M., et al. 2019, Monthly Notices of the
Royal Astronomical Society, 490, 4956
Harrison, C. M. 2017, Nature Astronomy, 1, 0165
Harrison, C. M., Alexander, D. M., Mullaney, J. R., et al. 2016a, Monthly Notices
of the Royal Astronomical Society, 456, 1195



Harrison, C. M., Simpson, J. M., Stanley, F., et al. 2016b, Monthly Notices of
the Royal Astronomical Society: Letters, 457, L122
Hickox, R. C., Mullaney, J. R., Alexander, D. M., et al. 2014, The Astrophysical
Journal, 782, 9
Hodge, J. A., Karim, A., Smail, I., et al. 2013, The Astrophysical Journal, 768,
91
Hodge, J. A., Swinbank, A. M., Simpson, J. M., et al. 2016, The Astrophysical
Journal, 833, 103
Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90
Husemann, B., Scharwächter, J., Davis, T. A., et al. 2019, A&A, 627, A53
Huynh, M. T., Hopkins, A. M., Lenc, E., et al. 2012, Monthly Notices of the
Royal Astronomical Society, 426, 2342
Ikarashi, S., Ivison, R. J., Caputi, K. I., et al. 2015, The Astrophysical Journal,
810, 133
Ishibashi, W. & Fabian, A. C. 2016, Monthly Notices of the Royal Astronomical
Society, 457, 2864
Jarvis, M. E., Harrison, C. M., Thomson, A. P., et al. 2019, Monthly Notices of
the Royal Astronomical Society, 485, 2710
Kakkad, D., Mainieri, V., Brusa, M., et al. 2017, Monthly Notices of the Royal
Astronomical Society, 468, 4205
Kakkad, D., Mainieri, V., Padovani, P., et al. 2016, A&A, 592, A148
Kakkad, D., Mainieri, V., Vietri, G., et al. 2020, A&A, 642, A147
Karim, A., Swinbank, A. M., Hodge, J. A., et al. 2013, Monthly Notices of the
Royal Astronomical Society, 432, 2
Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, Monthly Notices of
the Royal Astronomical Society, 346, 1055
Kennicutt, R. C. & Evans, N. J. 2012, Annual Review of Astronomy and Astrophysics, 50, 531
Kennicutt, R. C. J. 1998, The Astrophysical Journal, 498, 541
Kewley, L. J., Dopita, M. A., Leitherer, C., et al. 2013a, The Astrophysical Journal, 774, 100
Kewley, L. J., Maier, C., Yabe, K., et al. 2013b, The Astrophysical Journal Letters, 774, L10
King, A. 2003, The Astrophysical Journal, 596, L27
King, A. & Pounds, K. 2015, Annual Review of Astronomy and Astrophysics,
53, 115
Kocevski, D. D., Hasinger, G., Brightman, M., et al. 2018, The Astrophysical
Journal Supplement Series, 236, 48
Lacy, M., Storrie-Lombardi, L. J., Sajina, A., et al. 2004, The Astrophysical Journal Supplement Series, 154, 166
Lam, M. I., Wu, H., Zhu, Y.-N., & Zhou, Z.-M. 2013, Research in Astronomy
and Astrophysics, 13, 179
Lang, P., Schinnerer, E., Smail, I., et al. 2019, The Astrophysical Journal, 879,
54
Lani, C., Netzer, H., & Lutz, D. 2017, Monthly Notices of the Royal Astronomical Society, 471, 59
Luo, B., Brandt, W. N., Xue, Y. Q., et al. 2017, The Astrophysical Journal Supplement Series, 228, 2
Lutz, D., Shimizu, T., Davies, R. I., et al. 2018, A&A, 609, A9
Madau, P. & Dickinson, M. 2014, Annual Review of Astronomy and Astrophysics, 52, 415
Madau, P., Ferguson, H. C., Dickinson, M. E., et al. 1996, Monthly Notices of
the Royal Astronomical Society, 283, 1388
Mainieri, V., Bergeron, J., Hasinger, G., et al. 2002, A&A, 393, 425
Maiolino, R., Russell, H. R., Fabian, A. C., et al. 2017, Nature, 544, 202
Mancini, C., Förster Schreiber, N. M., Renzini, A., et al. 2011, The Astrophysical
Journal, 743, 86
Marasco, A., Cresci, G., Nardini, E., et al. 2020, A&A, 644, A15
Marchesi, S., Civano, F., Elvis, M., et al. 2016, The Astrophysical Journal, 817,
34
Marconi, A., Risaliti, G., Gilli, R., et al. 2004, Monthly Notices of the Royal
Astronomical Society, 351, 169
McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156
McElroy, R. E., Husemann, B., Croom, S. M., et al. 2016, A&A, 593, L8
McKinney, J., Hayward, C. C., Rosenthal, L. J., et al. 2021, arXiv,
arXiv:2103.12747
McMahon, R. G., Banerji, M., Gonzalez, E., et al. 2013, The Messenger, 154, 35
Miller, N. A., Bonzini, M., Fomalont, E. B., et al. 2013, The Astrophysical Journal Supplement, 205, 13
Mukherjee, D., Bicknell, G. V., Sutherland, R., & Wagner, A. 2016, Monthly
Notices of the Royal Astronomical Society, 461, 967
Mukherjee, D., Bicknell, G. V., Wagner, A. Y., Sutherland, R. S., & Silk, J. 2018,
Monthly Notices of the Royal Astronomical Society, 479, 5544
Mullaney, J. R., Alexander, D. M., Aird, J., et al. 2015, Monthly Notices of the
Royal Astronomical Society: Letters, 453, L83
Mullaney, J. R., Alexander, D. M., Goulding, A. D., & Hickox, R. C. 2011,
Monthly Notices of the Royal Astronomical Society, 414, 1082
Ni, Q., Brandt, W. N., Yang, G., et al. 2021, Monthly Notices of the Royal Astronomical Society, 500, 4989


Article number, page 25 of 32

_A&A proofs:_ manuscript no. SUPER_paper



Noll, S., Burgarella, D., Giovannoli, E., et al. 2009, A&A, 507, 1793
Osterbrock, D. E. & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and
active galactic nuclei
Perna, M., Arribas, S., Catalan-Torrecilla, C., et al. 2020, A&A, 643, A139
Perna, M., Cresci, G., Brusa, M., et al. 2019, A&A, 623, A171
Pier, E. A. & Krolik, J. H. 1992, Astrophysical Journal, 401, 99
Pierre, M., Pacaud, F., Adami, C., et al. 2016, A&A, 592, A1
Popping, G., Pillepich, A., Calistro Rivera, G., et al. 2021, arXiv,
arXiv:2101.12218
Puglisi, A., Daddi, E., Liu, D., et al. 2019, The Astrophysical Journal Letters,
877, L23
Puglisi, A., Daddi, E., Renzini, A., et al. 2017, The Astrophysical Journal Letters,
838, L18
Querejeta, M., Schinnerer, E., García-Burillo, S., et al. 2016, A&A, 593, A118
Retzlaff, J., Rosati, P., Dickinson, M., et al. 2010, A&A, 511, A50
Robitaille, T. & Bressert, E. 2012, Astrophysics Source Code Library,
ascl:1208.017
Rosario, D. J., Mendel, J. T., Ellison, S. L., Lutz, D., & Trump, J. R. 2016,
Monthly Notices of the Royal Astronomical Society, 457, 2703
Rosario, D. J., Togi, A., Burtscher, L., et al. 2019, The Astrophysical Journal
Letters, 875, L8
Rupke, D. S. N., Gültekin, K., & Veilleux, S. 2017, The Astrophysical Journal,
850, 40
Salpeter, E. E. 1955, Astrophysical Journal, 121, 161
Santini, P., Ferguson, H. C., Fontana, A., et al. 2015, The Astrophysical Journal,
801, 97
Schinnerer, E., Smolˇci´c, V., Carilli, C. L., et al. 2007, The Astrophysical Journal
Supplement Series, 172, 46
Schneider, R., Bianchi, S., Valiante, R., Risaliti, G., & Salvadori, S. 2015, A&A,
579, A60
Scholtz, J., Alexander, D. M., Harrison, C. M., et al. 2018, Monthly Notices of
the Royal Astronomical Society, 475, 1288
Scholtz, J., Harrison, C. M., Rosario, D. J., et al. 2020, Monthly Notices of the
Royal Astronomical Society, 492, 3194
Scholtz, J., Harrison, C. M., Rosario, D. J., et al. 2021, Monthly Notices of the
Royal Astronomical Society, 505, 5469
Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74
Schwarz, G. 1978, Ann. Statist., 6(2), 461
Shankar, F., Weinberg, D. H., & Miralda-Escudé, J. 2009, The Astrophysical
Journal, 690, 20
Shapiro, S. L., Teukolsky, S. A., & Lightman, A. P. 1983, Physics Today, 36, 89
Shin, J., Woo, J.-H., Chung, A., et al. 2019, The Astrophysical Journal, 881, 147
Silva, L., Granato, G. L., Bressan, A., & Danese, L. 1998, The Astrophysical
Journal, 509, 103
Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2015, The Astrophysical Journal, 799, 81
Smolˇci´c, V., Novak, M., Bondi, M., et al. 2017, A&A, 602, A1
Somerville, R. S., Hopkins, P. F., Cox, T. J., Robertson, B. E., & Hernquist, L.
2008, Monthly Notices of the Royal Astronomical Society, 391, 481
Stach, S. M., Dudzeviˇci¯ut˙e, U., Smail, I., et al. 2019, Monthly Notices of the
Royal Astronomical Society, 487, 4648
Stan Development Team. 2018, PyStan: the Python interface to Stan, Version
2.17.1.0
Stanley, F., Harrison, C. M., Alexander, D. M., et al. 2018, Monthly Notices of
the Royal Astronomical Society, 478, 3721
Stern, D., Assef, R. J., Benford, D. J., et al. 2012, The Astrophysical Journal,
753, 30
Storchi-Bergmann, T., Lopes, R. D. S., McGregor, P. J., et al. 2010, Monthly
Notices of the Royal Astronomical Society, 402, 819
Szokoly, G. P., Bergeron, J., Hasinger, G., et al. 2004, The Astrophysical Journal
Supplement Series, 155, 271
Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, Annual Review of Astronomy
and Astrophysics, 58, 157
Tadaki, K.-i., Belli, S., Burkert, A., et al. 2020, The Astrophysical Journal, 901,
74
Tadaki, K.-i., Genzel, R., Kodama, T., et al. 2017, The Astrophysical Journal,
834, 135
Taylor, M. B. 2005, Astronomical Data Analysis Software and Systems XIV
ASP Conference Series, 347, 29
The Astropy Collaboration, Robitaille, Thomas P., Tollerud, Erik J., et al. 2013,
A&A, 558, A33
Trayford, J. W., Theuns, T., Bower, R. G., et al. 2016, Monthly Notices of the
Royal Astronomical Society, 460, 3925
Tsuzuki, Y., Kawara, K., Yoshii, Y., et al. 2006, The Astrophysical Journal, 650,
57
Van Der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science
and Engineering, 13, 22
Veilleux, S., Meléndez, M., Sturm, E., et al. 2013, The Astrophysical Journal,
776, 27


Article number, page 26 of 32



Venturi, G., Marconi, A., Mingozzi, M., et al. 2017, Frontiers in Astronomy and
Space Sciences, 4, 46
Venturi, G., Nardini, E., Marconi, A., et al. 2018, A&A, 619, A74
Veron-Cetty, M. P., Joly, M., & Veron, P. 2004, A&A, 417, 515
Viaene, S., Nersesian, A., Fritz, J., et al. 2020, A&A, 638, A150
Vietri, G., Mainieri, V., Kakkad, D., et al. 2020, A&A, 644, A175
Vietri, G., Piconcelli, E., Bischetti, M., et al. 2018, A&A, 617, A81
Wang, S. X., Brandt, W. N., Luo, B., et al. 2013, The Astrophysical Journal, 778,
179
Whitaker, K. E., Rigby, J. R., Brammer, G. B., et al. 2014, The Astrophysical
Journal, 790, 143
Zubovas, K. 2018, Monthly Notices of the Royal Astronomical Society, 479,
3189

I. Lamperti et al.: SUPER V: obscured star formation and outflows



**Appendix A:** **Models used to fit the FIR profile**


To assess the morphology of the FIR emission, we fit the visibilities versus _uv_ -distances using the following models: point
source, Gaussian, Gaussian+point source, and exponential profile. We Fourier-transformed the models to perform the fit in the
visibilities versys _uv_ -distance plane. The models in the visibilities versus _uv_ -distance plane are defined as:


**–** _Point_ _source_ : a point source is represented as a constant
model as a function of _uv_ -distance:


_f_ ( _x_, _F_ ) = _F_, (A.1)


where _F_ is the flux density in mJy and _x_ is the _uv_ -distance
in units of kλ, where λ is the wavelength of the observation.


**–** _Gaussian profile_ : the Fourier transform of a Gaussian model
is also a Gaussian defined as:



Table A.1: Range of priors used for the fit of the visibilities vs.
_uv_ -distances. _F_ is the flux density and σ _uv_ is the scale parameter.


Model parameter priors
point _F_ 0 − 1000 mJy
Gaussian _F_ 0 − 1000 mJy
σ _uv_ 0 − 10000 kλ
Gaussian+point _F_ (Gauss) 0 − 5 mJy
σ _uv_ 0 − 10000 kλ
_F_ (point) 0 − 5 mJy
exponential _F_ 0 − 1000 mJy
σ _uv_ 0 − 20000 kλ


_uv_ -visibilities with the ‘preferred’ model according to the BIC
(point, Gaussian, exponential or Gaussian+point model, see Section 3.2). For the 2D Gaussian fit on the image plane, we show
two points representing the sizes of the major and minor axis
(in violet) and the mean value in magenta. For `uvmodelfit`,
we show the mean value between the major and minor axis. For
cid_1057 and cid_451, the S/N is very low (3.6 and 5.9, respectively), therefore we do not consider their size measurements to
be reliable. These two sources are highlighted with a grey band
in Figure B.1.
In general, the sizes measured with different methods are
in agreement within the uncertainties. We note that the sizes
measured with the exponential profile are larger than the sizes
measured with the Gaussian profile (factor of 1.38 on average)
by construction, since the exponential profile does not decrease
rapidly towards zero at larger radii and thus considers a larger
amount of flux at large radii.
The flux densities are mostly insensitive to the method used.
The only notable differences are for cid_1057 and cid_346.
cid_1057 has a very low S/N, thus the flux measurements are not
very reliable. For cid_346, the Gaussian fit with `uvmodelfit`
measures a lower flux than the other methods. The rest-frame
260 µm emission of this galaxy is better described by a Gaussian+point source or by an exponential profile, therefore the
Gaussian model cannot fit well the central flux peak and underestimates the total flux.
In Tables B.1 and B.2, we provide all the measurements obtained with the different methods. We note that when we compare our measurements to literature values in Section 5.2, we
used the sizes obtained with the same method used in the litera
ture.


**Appendix C:** **Astrometry of the SINFONI data**


In this Section, we explain the details of the registration of the
astrometry of the SINFONI data-cubes. As explained in Section 4.2, the absolute position of the SINFONI cubes, as derived
from the SINFONI pipeline, is not sufficiently accurate for our
purposes. The small field of view of the SINFONI images (3×3
arcsec [2] ) does not allow us to correct the astrometry using nearby
stars, since usually the target is the only visible source in the
field of view. Therefore, we have to derive the absolute coordinates from other images.
**Reference** **coordinates:** We use H-band and K-band images
with a large field of view (3×3 arcmin [2] ) to determine the reference coordinates of our targets that we later use to register the
astrometry of the SINFONI data-cubes. We use K-band and Hband images from the VLT/VISTA and VLT/ISAAC.
To determine the coordinates from the H/K-band images, we
apply the following procedure. First, we align the H/K-band im

Article number, page 27 of 32



2 []

, (A.2)
� 



_f_ ( _x_, _F_, σ _uv_ ) = _F_ - exp



1
− 2




_x_
� σ _uv_



where _F_ is the flux density in mJy and σ _uv_ is the scale parameter. σ _uv_ is related to the effective radius _R_ _e_ (in radians)

as:



= [2][.][355]
2 2



_R_ _e_ [rad] = _[FWHM]_




[355] 1

  - σ = [2][.][355]  - [(A.3)]
2 2 2πσ _uv_ - 10 [3] [,]



where the factor 10 [3] is necessary to convert from
kλ to λ. The effective radius in arcsec is obtained as
_R_ _e_ [arcsec] = _R_ _e_ [rad] [180][·] π [3600] .



**–** _Gaussian_ + _point_ _source_ : this model combines the previous
two models:


_f_ ( _x_, _F_ _Gauss_ ., σ _uv_, _F_ _point_ ) = _f_ _Gauss_ ( _x_, _F_ _Gauss_, σ _uv_ ) + _F_ _point_,

(A.4)


where _F_ _Gauss_ . and _F_ _point_ are the flux densities of the Gaussian
and point source components, respectively. The total flux
density is given by _F_ ( _tot_ ) = _F_ _Gauss_ . + _F_ _point_ .


**–**
_Exponential profile_ : the exponential profile is modelled as :

_f_ ( _x_, _F_, σ _uv_ ) = _F_    - σ [2] _uv_ σ + _uv_ _x_ [2] [,] (A.5)


where σ _uv_ is related to the effective radius _R_ _e_ (in radians) as:


1
_R_ _e_ [rad] = 1.6783 · σ = 1.6783 · 2πσ _uv_  - 10 [3] [.] (A.6)


The priors used for the Bayesian fitting are reported in Table A.1.


**Appendix B:** **Comparison of FIR sizes and flux**
**densities derived using different methods**


In Figure B.1, we compare the FIR sizes and and flux densities of the rest-frame 260 µm ALMA emission, measured using
four different methods: 1) fit on the image assuming a 2D Gaussian profile, 2) fit with `uvmodelfit` assuming a 2D Gaussian
profile, 3) fit of the _uv_ -visibilities assuming an exponential profile (equivalent to a Sérsic profile with _n_ = 1), and 4) fit of the

_A&A proofs:_ manuscript no. SUPER_paper



1.0


0.8


0.6


0.4


0.2


0.0


3.0


2.5


2.0


1.5


1.0







0.5


0.0

|S/N:228 211 94<br>. . .|35<br>.|285<br>.|55<br>.|Col5|162 120<br>. .<br>imagefit(Gaussian)<br>uvmodelfit(Gaussian)<br>exp visibilityfit<br>.<br>bestvisibilityfit|
|---|---|---|---|---|---|
|S/N : 22.8<br>21.1<br>9.4|3.5|28.5|5.5||image fit (Gaussian)<br>uvmodelfit (Gaussian)<br>exp. visibility fit<br>best visibility fit|
|S/N : 22.8<br>21.1<br>9.4|3.5|28.5|5.5|||

X_N_81_44 XID36 XID419 cid_1057 cid_346 cid_451 cid_1205 cid_1143


Fig. B.1: Comparison of the FIR sizes and flux densities derived using different methods: fit of a 2D Gaussian on the image plane
(circles), fit of a 2D Gaussian using `uvmultifit` (stars), fit of the visibilities assuming an exponential profile (squares), and fit of
the visibilities with the ‘preferred model’ according to the BIC (diamonds). The preferred model for each object is written on the
top part of the figure. _Upper panel_ : Size measurements expressed as two times the effective radius ( _R_ _e_ ). The grey horizontal lines
represent the size of the ALMA beam for each object. For the 2D Gaussian fit on the image plane, the two magenta crosses represent
the sizes of the major and minor axis. For point sources, we show the upper limit corresponding to the beam size. _Bottom_ _panel:_
integrated flux densities measured with different methods. The peak signal-to-noise (S/N) of the ALMA images is written on the
top part of the panel. The results for the two objects with S/N too low to obtain reliable measurements (cid_1057 and cid_451) are
highlighted with background grey shading.



ages to the _Gaia_ DR2 catalogue, using the Graphical Astronomy
and Image Analysis Tool (GAIA) that is part of the `Starlink`
software (Currie et al. 2014). There are at least five objects in
common between the _Gaia_ DR2 catalogue and each image that
allow us to accurately align the images to the _Gaia_ astrometry [14] .
Then, we determine the centroid position of our target in the ‘astrometry corrected’ image by fitting a 2D Gaussian to the source.
We apply this procedure to both the H-band and K-band images. The offsets between the coordinates derived from the Hband and K-band are smaller than one pixel (< 0.07”), therefore
we can assume that the H-band and K-band emission peak at the
same position. We decide to use the coordinates derived from


14 There is an exception: cid_1205 that has only 3 sources in common
between the GAIA catalogue and the H/K-band image. For this object
the H/K-band position is in perfect agreement with the FIR position
measured from the ALMA map, therefore we consider the H/K-band
coordinates to be reliable.


Article number, page 28 of 32



the K-band corrected images to register the astrometry of both
the H-band and K-band SINFONI images.
We compare the K-band coordinates with the _Gaia_ coordinates for the two objects detected in _Gaia_ . For cid_346, the
K-band coordinates agree very well with the _Gaia_ coordinates
(offset 7.3 mas). For X_N_81_44, the K-band coordinates are
shifted by 0.05” to the west with respect to the coordinates from
_Gaia_ . Given the low resolution of the K-band image for this target (FWHM PSF 1.04”), we decide to use the coordinates from
_Gaia_ for this source. We note that these two targets are Type
1 AGN, and are dominated by the point source emission of the
AGN across the optical and near-infrared bands. Finally, we note
that XID419 is only marginally detected in the K-band image
(peak S/N< 6) and thus it is difficult to determine its position.
Therefore for this target we rely on the coordinates derived from
the _HST_ /WFC3 images reported in Scholtz et al. (2020).
**Registration** **of** **the** **SINFONI** **images:** We use these coordinates to register the position of the peak of the emission in the

I. Lamperti et al.: SUPER V: obscured star formation and outflows


|ft uvmodelfit image i F R F R axial ratio axial ratio e e [mas] [mas] [mJy] [mJy]|. . . . . . . . 118±010 123±032 105±003 70±5 100±011 98±18 . . . . . . . . 101±008 130±025 122±012 99±13 095±003 79±5 112±22 . . . . . . . . 045±006 160±046 044±003 288±080 96±14 - - - - 0 .13 0 .21±0 .04 .29±0 . . . . . . . . 261±017 186±17 127±016 241±004 171±5 131±006 . . . . . . . . 035±008 244±66 027±002 315±083 191±076 190±36 - - - - 0 .02 0 .28±0 .01 .29±0 . . . . . . . . 056±007 222±36 045±002 174±18 460±070 249±060|
|---|---|
|Method:<br>ID<br>S/N|X_N_81_44<br>22.7<br>XID36<br>21.5<br>XID419<br>9.8<br>cid_1057⋆<br>3.6<br>cid_346<br>29.0<br>cid_451⋆<br>5.9<br>cid_1205<br>16.6<br>cid_1143<br>12.1|



Article number, page 29 of 32

_A&A proofs:_ manuscript no. SUPER_paper


SINFONI data cubes. The emission of the H/K-band filters is
dominated by the continuum, but there is also some contribution
from the emission lines.
For the Type 1 AGN, we check that the position of the continuum and the position derived by collapsing the total SINFONI
data-cubes are in agreement, both in the H- and K-band (offset
< 0.02 [′′] ).
For the Type 2, the continuum is significantly detected in
the SINFONI maps only in one object (XID36). For this target,
we test that the position of the continuum and the position derived by collapsing the total data-cube are in agreement (offset
< 0.007 [′′] ), both in the H- and K-band. For the other targets, we
use the SINFONI spectra to estimate the relative contribution of
continuum and emission lines to the total emission in the H/K
band VISTA and ISAAC filters. The continuum contribution is

- 70% for all targets.
**Uncertainties on the coordinate registration:** The typical uncertainty on the _Gaia_ coordinates is ≤ 4 mas. The precision of
the alignment of the K-band images with the _Gaia_ images is
about half pixel (75 mas for COSMOS and 130 mas for CDFS). The uncertainties from the 2D Gaussian fit of the VISTA
or ISAAC K-band images are in the range 1-49 mas (median
4 mas). We also consider the uncertainties due to the size of
the VISTA or ISAAC K-band PSF (0.78-1.04”), calculated as
PSF/(2×S/N) following Condon (1997), which are in the range
3-40 mas. The uncertainties on the position of the emission of
the SINFONI cubes is ∼ half pixel (25 mas).
To estimate the total uncertainties of the derived K-band coordinates, we added in quadrature all the above uncertainties.
These uncertainties are dominated by the pixel size of the Kband images. In summary, the uncertainties on the derived SINFONI astrometry for our sample are in the range 0.03-0.14”.


**Appendix D:** **SINFONI spectra of Type 1 AGN**


Figure 3 in Section 4 shows the BLR-subtracted spectra that we
used in the analysis. In this Section, we show the total SINFONI emission line spectra (including the BLR component) of
the three Type 1 AGN in our sample (X_N_81_44, cid_346,
cid_1205).


**Appendix E:** **Spectral energy distributions (SEDs)**


In Figure E.1, we show the spectral energy distributions of our
targets (rest-frame wavelength range 0.1 µm−10 cm), together
with the best fit model from Circosta et al. (2018) (see description in Section 2). We use these models to predict the percentage
contribution due to dust heated by the AGN at 260 µm (restframe). We also show the synchrotron emission contribution at
260 µm, predicted based on the available radio photometry. The
different sources that can contribute to the 260 µm flux are discussed in Section 5.1.


Article number, page 30 of 32

I. Lamperti et al.: SUPER V: obscured star formation and outflows



14



X ~~N~~ ~~8~~ 1 ~~4~~ 4





X ~~N~~ ~~8~~ 1 ~~4~~ 4





4700 4750 4800 4850 4900 4950 5000 5050
rest _−_ frame wavelength [A] [˚]



6450 6500 6550 6600 6650
rest _−_ frame wavelength [A] [˚]


cid ~~3~~ 46



4


3



cid ~~3~~ 46





2


1


0


2 _._ 0
1 _._ 5
1 _._ 0
0 _._ 5
_−−−_ 0011 _...._ 0505







4700 4750 4800 4850 4900 4950 5000 5050
rest _−_ frame wavelength [A] [˚]


cid ~~1~~ 205



6450 6500 6550 6600 6650
rest _−_ frame wavelength [A] [˚]


cid ~~1~~ 205

















_−_ 1


_−_ 1







4700 4750 4800 4850 4900 4950 5000 5050
rest _−_ frame wavelength [A] [˚]



6450 6500 6550 6600 6650
rest _−_ frame wavelength [A] [˚]



Fig. D.1: Integrated spectra of Type 1 AGN in our sample: [O iii]+Hβ spectra (left) and Hα+[N ii] spectra (right). The continuumand BLR-subtracted spectra are shown in light-grey. The total spectra, before subtracting the continuum and broad line region
(BLR) emission, are shown in dark grey. The blue curves show the total fit to the Hβ, [O iii]λ4959 and [O iii]λ5007 lines (left panel)
and to the Hα, [N ii]λ6548 and [N ii]λ6584 lines (right panel). The red and orange curves show the narrow and broad components,
respectively. For X_N_81_44, the broad components of the Hβ and Hα are considered as part of the BLR.


Article number, page 31 of 32

_A&A proofs:_ manuscript no. SUPER_paper


10 [4]



10 [4]


10 [3]


10 [2]


10 [1]


10 [0]


10 [-1]


10 [-2]



X_N_81_44


AGN heated dust: < 1% of F(870µm)


synchr. (α r =-0.7): < 1% of F(870µm)


best fit

stellar emission



XID36



SF heated dust

Fitted UV-IR photometry

ALMA Band 7

1.4 GHz



10 [3]


10 [2]


10 [1]


10 [0]


10 [-1]


10 [-2]



AGN heated dust: 2.1% of F(870µm)


synchr. (α r = − 1.3): < 1% of F(870µm)


best fit

stellar emission

SF heated dust



Fitted UV-IR photometry

ALMA Band 7

1.4 GHz

5.5 GHz



10 [-3]

10 [-1] 10 [0] 10 [1] 10 [2] 10 [3] 10 [4] 10 [5]

rest − frame wavelength [µm]



10 [-3]

10 ~~[-]~~ [1] 10 [0] 10 [1] 10 [2] 10 [3] 10 [4] 10 [5]

rest − frame wavelength [µm]



10 [4]


10 [3]


10 [2]


10 [1]


10 [0]


10 [-1]


10 [-2]



XID419


AGN heated dust: 5.4% of F(870µm)


synchr. (α r =-0.7): < 1% of F(870µm)


best fit

stellar emission



cid_1057


AGN heated dust: < 1% of F(870µm)


synchr. (α r =-0.7): < 1% of F(870µm)


best fit

stellar emission



SF heated dust

Fitted UV-IR photometry

ALMA Band 7

1.4 GHz



SF heated dust

Fitted UV-IR photometry

ALMA Band 7

1.4 GHz



10 [-3]

10 [-1] 10 [0] 10 [1] 10 [2] 10 [3] 10 [4] 10 [5]

rest − frame wavelength [µm]



10 [4]


10 [3]


10 [2]


10 [1]


10 [0]


10 [-1]


10 [-2]


10 [-3]


10 [-4]



rest − frame wavelength [µm]



10 [-1] 10 [0] 10 [1] 10 [2] 10 [3] 10 [4] 10 [5]



10 [4]


10 [3]


10 [2]


10 [1]


10 [0]


10 [-1]


10 [-2]



cid_346


AGN heated dust: < 1% of F(870µm)


synchr. (α r = - 0.98): < 1% of F(870µm)


best fit

stellar emission

SF heated dust



cid_451


AGN heated dust: 6.4% of F(870µm)


synchr.( α r = − 0.99): 21.8% of F(870µm)


best fit

stellar emission

SF heated dust



Fitted UV-IR photometry

ALMA Band 7

3 GHz

1.4 GHz



Fitted UV-IR photometry

ALMA Band 7

ALMA Band 3

3 GHz

1.4 GHz



10 [-3]

10 [-1] 10 [0] 10 [1] 10 [2] 10 [3] 10 [4] 10 [5]

rest − frame wavelength [µm]



10 [4]


10 [3]


10 [2]


10 [1]


10 [0]


10 [-1]


10 [-2]


10 [-3]


10 [-4]



rest − frame wavelength [µm]



10 [-1] 10 [0] 10 [1] 10 [2] 10 [3] 10 [4] 10 [5]



10 [4]


10 [3]


10 [2]


10 [1]


10 [0]


10 [-1]


10 [-2]


10 [-3]


10 [-4]



cid_1205


AGN heated dust: < 1% of F(870µm)


synchr. (α r =-0.7): < 1% of F(870µm)


best fit

stellar emission



cid_1143


AGN heated dust: < 1% of F(870µm)


synchr. (α r =-0.7): < 1% of F(870µm)


best fit

stellar emission



SF heated dust

Fitted UV-IR photometry

ALMA Band 7

3 GHz



SF heated dust

Fitted UV-IR photometry

ALMA Band 7

3 GHz



10 [-1] 10 [0] 10 [1] 10 [2] 10 [3] 10 [4] 10 [5]



10 [4]


10 [3]


10 [2]


10 [1]


10 [0]


10 [-1]


10 [-2]


10 [-3]


10 [-4]



10 [-1] 10 [0] 10 [1] 10 [2] 10 [3] 10 [4] 10 [5]



rest − frame wavelength [µm]



rest − frame wavelength [µm]



Fig. E.1: Rest-frame spectral energy distribution (SED) of our sample. The light blue data points represent the UV-IR photometry that was used
for the SED fitting (Circosta et al. 2018). The red point shows our ALMA Band 7 flux measurements, which was also included in the fit. The
violet point in cid_451 shows the ALMA Band 3 flux from Circosta et al. (2021). The blue, orange, and pink points show the radio fluxes at 1.4,
3, and 5 GHz, respectively. The arrows indicate 3σ upper limits. The solid curves show the results of the SED fitting with `CIGALE` : in black is the
total best-fit model (including the contribution the from nebular emission component), in orange the dust-attenuated stellar emission, in magenta
the emission from dust heated by star formation and in green the emission from dust heated by the AGN. To estimate the maximum contribution
of synchrotron emission to the rest-frame 260 µm flux density we parameterized this emission as a power law with spectral index α _r_ (dashed red
line), normalised at 3 GHz (10cm) or 1.4 GHz (21cm), depending on the available radio data. For the galaxies with radio fluxes in two bands,
we derived α _r_ based on the two fluxes. On the plot we show the estimated contribution (in percentage) from dust heated by the AGN and from
synchrotron emission to the rest-frame 260 µm ALMA Band 7 flux, estimated from the total SED template.


Article number, page 32 of 32


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[3].provided.evidence[1]",
  "value": "Astrometric reference catalogue (Gaia DR2) for aligning H/K-band images and direct positions for two Type 1 AGN",
  "failed_quote": "First, we align the H/K-band images to the Gaia DR2 catalogue, using the Graphical Astronomy and Image Analysis Tool (GAIA) that is part of the Starlink software (Currie et al. 2014)."
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Run standard ALMA pipeline in CASA 5.4.0, phase-centre the calibrated measurement set on the 2D Gaussian centroid using fixvis, model and subtract secondary sources in three fields (cid_451, cid_1205, cid_1143) with a 2D Gaussian and uvsub, and image with tclean using natural weighting (Briggs robust = 2).",
  "failed_quote": "We used the CASA task fixvis to phase-centre the calibrated measurement set on the central position of the source, determined by fitting a 2D Gaussian profile on the reduced image provided by the ALMA data-reduction pipeline."
 },
 {
  "path": "analysis_steps[0].fitting.evidence[0]",
  "value": "2D Gaussian fit on pipeline image for phase centre and on secondary sources for uvsub",
  "failed_quote": "We used the CASA task fixvis to phase-centre the calibrated measurement set on the central position of the source, determined by fitting a 2D Gaussian profile on the reduced image provided by the ALMA data-reduction pipeline."
 },
 {
  "path": "analysis_steps[2].validation.evidence[1]",
  "value": "Tested excluding ALMA Band 7 from CIGALE fit (<3% change in AGN contribution), fitting with AGNfitter (<7% AGN contribution), MBB torus model, and extreme synchrotron slope alpha_r = 0.",
  "failed_quote": "We note that even assuming a conservative value of α r = 0, which is towards the most extreme value measured for AGN (Dicken et al. 2008; Smolˇci´c et al. 2017), the synchrotron contribution is small"
 },
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Align VLT/VISTA and VLT/ISAAC H/K-band images to Gaia DR2 using Starlink GAIA, align collapsed SINFONI cubes to broadband centroids, fit Hbeta+[O III] and Halpha+[N II] spectra with multi-Gaussian components, create narrow [-300, 300] km s^-1 and outflow (< -300 and > 300 km s^-1) velocity maps, and fit 2D Gaussians with scipy.optimize.curve_fit to compare centroids and sizes with ALMA FIR maps.",
  "failed_quote": "We first aligned the H/K-band images to Gaia astrometry (Gaia Collaboration et al. 2016, 2018) using several stars across the fields. We then made broad-band images from the SINFONI data-cubes by collapsing them over the same wavelength range as the archival H/K-band images."
 },
 {
  "path": "software[10].used_for.evidence[0]",
  "value": "Aligning H/K-band images to the Gaia DR2 catalogue using the GAIA tool",
  "failed_quote": "First, we align the H/K-band images to the Gaia DR2 catalogue, using the Graphical Astronomy and Image Analysis Tool (GAIA) that is part of the Starlink software (Currie et al. 2014)."
 }
]
```
