# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.525.5831K\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–16 (2022) Preprint 4 September 2023 Compiled using MNRAS L [A] TEX style file v3.0

## Faint [C i](1-0) emission in 𝑧 ∼ 3 . 5 radio galaxies


S. Kolwa, [1] _[,]_ [2] _[★]_ C. De Breuck, [3] J. Vernet, [3] D. Wylezalek, [7] W. Wang, [7] G. Popping, [3]

A.W.S. Man, [4] _[,]_ [5] C.M. Harrison, [6] P. Andreani, [3]

1 _Physics Department, University of Johannesburg, 5 Kingsway Ave, Rossmore, Johannesburg, 2092, South Africa_
2 _Inter-University Institute for Data Intensive Astronomy, Department of Astronomy, University of Cape Town, Rondebosch 7701, South Africa_
3 _European Southern Observatory, Karl-Schwarzschild-Str. 2 85748 Garching bei München, Germany_
4 _Dunlap Institute for Astronomy and Astrophysics, University of Toronto, 50 St George Street, Toronto ON, M5S 3H4, Canada_
5 _Department of Physics & Astronomy, The University of British Columbia, 6224 Agricultural Road, Vancouver, BC V6T 1Z1, Canada_
6 _School of Mathematics, Statistics and Physics, Newcastle University, Newcastle upon Tyne, NE1 7RU, UK_
7 _Astronomisches Rechen-Institut, Zentrum für Astronomie der Universität Heidelberg, Mönchhofstra𝛽e 12-14, 69120 Heidelberg, Germany_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

We present Atacama Large Millimeter/sub-millimeter Array (ALMA) neutral carbon, [C i](1-0), line observations that probe
molecular hydrogen gas (H 2 ) within seven radio galaxies at _𝑧_ = 2 _._ 9 − 4 _._ 5 surrounded by extended (≳100 kpc) Ly _𝛼_ nebulae. We
extract [C i](1-0) emission from the radio-active galactic nuclei (AGN) host galaxies whose positions are set by near-infrared
detections and radio detections of the cores. Additionally, we place constraints on the galaxies’ systemic redshifts via He ii _𝜆_ 1640
lines seen with the Multi-Unit Spectroscopic Explorer (MUSE). We detect faint [C i] emission in four out of seven sources.
In two of these galaxies, we discover narrow line emission of full width at half maximum ≲ 100 km s [−][1] which may trace
emission from bright kpc-scale gas clouds within the ISM. In the other two [C i]-detected galaxies, line dispersions range from
∼ 100 − 600 km s [−][1] and may be tracing the rotational component of the cold gas. Overall, the [C i] line luminosities correspond
to H 2 masses of _𝑀_ H 2 _,_ [C i] ≃(0 _._ 5 − 3) × 10 [10] M ⊙ for the detections and _𝑀_ H 2 _,_ [C i] _<_ 0 _._ 65 × 10 [10] M ⊙ for the [C i] non-detections
in three out of seven galaxies within the sample. The molecular gas masses in our sample are relatively low in comparison to
previously reported measures for similar galaxies which are _𝑀_ H 2 _,_ [C i] ≃(3 − 4) × 10 [10] M ⊙ _._ Our results imply that the observed
faintness in carbon emission is representative of a decline in molecular gas supply from previous star-formation epochs and/or a
displacement of molecular gas from the ISM due to jet-powered outflows.


**Key words:** galaxies: high-redshift – galaxies: active – galaxies: star formation – ISM: molecules – galaxies: kinematics and
dynamics



**1** **INTRODUCTION**


Observations of cold gas in radio galaxies (HzRGs) which host
high-power jetted active galactic nuclei (AGN) are an excellent
tool for studying the impact of radio-mode feedback on baryonic
matter within the interstellar medium and extended halo of a highmass galaxy. The distinguishing features of radio galaxies at highredsift ( _𝑧>_ 1) are their high-luminosity nuclear emission, prominent radio-jets, and high stellar masses which typically range from
_𝑀_ _★_ ≃ 10 [11] − 10 [12] M ⊙ (Seymour et al. 2007; De Breuck et al. 2010).
Such a combination of physical features make HzRGs particularly
important sites for examining the co-evolution of galaxies and their
central supermassive black-holes as well as feedback mechanisms
regulated by the active galactic nucleus (AGN).
Within the past three decades, it has become increasingly apparent that HzRGs are also commonly associated with enormous
Ly _𝛼_ nebulae (ELANe) that can extend out to distances of ≳ 100
pkpc from their nuclei. The combination of powerful radio jets and
enormous haloes of ionised gas surrounding the galaxy mean that


_★_ E-mail: sthabile@idia.ac.za


© 2022 The Authors



HzRGs are also very convenient probes for investigating the interplay
between ionised gas and radio emission (McCarthy 1993; Reuland
et al. 2003; Villar-Martín et al. 2003; Villar-Martín 2007; Humphrey
et al. 2007; Swinbank et al. 2015; Morais et al. 2017; Silva et al.
2018). ELAN surrounding HzRGs represent the warm ionised gas
component (T ∼ 10 [4] − 10 [5] K) of the circumgalactic medium (CGM)
where turbulent gas motions is observed up to tens of kpc from the
AGN while on the outermost envelopes of the halo (≳ 10 pkpc) warm
gas tends to be more kinematically quiet (Villar-Martín et al. 2003).

Generally, the CGM of a galaxy is defined as the gas region through
which baryonic matter is transported (via accretion, and outflows) between the intergalactic medium (IGM) and the interstellar medium
(ISM). With the CGM being multi-phase, consisting of cold molecular, neutral as well as ionised gas, it has become an important
subject for investigation in galaxy evolution, allowing us to determine how multi-phase gas components interact physically with one
another throughout the extent of a galaxy’s halo (Steidel et al. 2010;
Tumlinson et al. 2017).

The ionised component of the CGM surrounding galaxies that host
AGN has been examined in numerous studies involving observations,
photoionisation modelling and theoretical simulations. These studies

2 _S. Kolwa et al._


have made significant use of integral field unit (IFU) spectrographs
to observe the ionised gas, providing a more detailed look into the
kinematics of the Ly _𝛼_ nebulae surrounding galaxies which had been
discovered a decade or two prior to the advent of IFUs. The 3D
imaging capability of IFUs provide a crucial in-depth view of the
gaseous environments of galaxies up to 100s of kpc from their nuclei.
Ly _𝛼_ line emission traced directly from the target galaxy with an IFU
is equally useful in studying the warm gas component of the CGM
(Borisova et al. 2016; Ginolfi et al. 2018; Arrigoni Battaia et al. 2018,
2019; Fossati et al. 2021). When the CGM of a galaxy coincides with
a quasar sight-line, absorption-line measures in the quasar spectrum
become a very useful diagnostic for the chemical composition and
kinematics of the foreground galaxy’s CGM (Bielby et al. 2017;
Péroux et al. 2017; Dutta et al. 2020).
For HzRGs in particular, instruments such as the Spectrograph
for INtegral Field Observations in the INfrared (SINFONI; e.g. Nesvadba et al. 2006, 2017) and the Multi-Unit Spectroscopic Explorer
(MUSE; e.g. Swinbank et al. 2015; Gullberg et al. 2016b; Vernet
et al. 2017; Kolwa et al. 2019; Falkendal et al. 2021; Wang et al.
2021) have illustrated the impact of the powerful radio jets on the
kinematics of emitting gas, in terms of producing outflows and increasing gas turbulence, showing that jets can drive out molecular
gas and effectively shut down the fuel supply for star-formation.
While all of the above observations have been beneficial in providing information on the properties of ionised gas in radio-loud
AGN hosts, a systematic CO survey to trace H 2 in a wide sample of
HzRGs has yet to be performed. This is the case despite the fact that
low- _𝐽_ transitions of CO have minimal excitation requirements (i.e.,
low critical densities and _𝐸_ /k B values). This fact implies that CO
lines can easily trace H 2 clouds irrespective of their thermal states at
low gas densities _𝑛_ ∼ 10 [2] cm [−][3] which are typically seen in optically
thick CO(1-0) gas. While CO has clear advantages as a molecular
gas tracer, solely relying on it comes with drawbacks. For instance, in
jetted AGN, CO within the ISM can be photodissociated by cosmic
rays, effectively destroying CO molecules and reducing the CO/H 2
abundance in giant molecular clouds (GMCs) (Bisbas et al. 2015,
2017).

Within this framework, neutral carbon fine-structure line transitions, [C i] [3] _𝑃_ 1 → [3] _𝑃_ 0 and [C i] [3] _𝑃_ 2 → [3] _𝑃_ 1 _,_ hereinafter [C i](1-0)
and [C i](2-1), have been introduced as an alternative tracer for H 2 in
GMCs. Selecting [C i] as a tracer may be especially wise given that
radio galaxies have jetted AGN that produce high-energy cosmic rays
which are capable of photodissociating CO in molecular gas. As a result, [C i] lines may retain their ability to trace H 2 in clouds irradiated
by cosmic rays (CRs). This situation may change as one shifts away
from the nuclear region and towards the interstellar medium (ISM)
where the number density of ionising photons is relatively lower than
it is in a galaxy’s nuclear region (Papadopoulos et al. 2004)
Previously, a pilot study of molecular gas in ultra-luminous infrared galaxies (ULIRGs) found reasonable agreement between the
H 2 masses inferred from [C i] and low- _𝐽_ CO lines (e.g. Papadopoulos
& Greve 2004). While more recently, observations in Papadopoulos
et al. (2018) have shown that high energy cosmic rays (CRs) produced by star-formation and active galactic nuclei (AGN) can provide the right conditions for creating a [C i]-rich/CO-poor molecular
gas phase. Another advantage to using [C i] line tracers is that they
provide a straightforward interpretation of the molecular clouds allowing us to infer H 2 mass. This is due to [C i] lines having typically
low optical depths in comparison to CO lines. Hence, the [C i] line
surface brightness correlates more directly with the mass of neutral
carbon and also the H 2 mass of a molecular cloud (Nesvadba et al.
2019). Furthermore, both [C i](1-0) and [C i](2-1) transitions have


MNRAS **000**, 1–16 (2022)



sufficiently low critical densities of _𝑛_ 10 = 500 cm [−][3] and _𝑛_ 21 = 10 [3]

cm [−][3] _,_ respectively.
One of the first major high-redshift ( _𝑧>_ 2) [C i] line surveys
was carried out by Walter et al. (2011) and showed emission in
sub-millimetre galaxies and quasar hosts. Since then, several [C i]
surveys have been performed with the goal of tracing H 2 and inferring
molecular gas masses and the dynamics thereof for both lensed and
unlensed galaxies at high- _𝑧_ (Alaghband-Zadeh et al. 2013; Bothwell
et al. 2017; Valentino et al. 2018; Nesvadba et al. 2019). Adding
to these surveys are several single-source studies which reveal the
presence of [C i] emission in star-forming galaxies (Popping et al.
2017; Andreani et al. 2018). For HzRGs, [C i](2-1) has traced H 2 in
PKS 0529-549 at _𝑧_ = 2 _._ 57 (Lelli et al. 2018; Man et al. 2019). Within
the halo of the Spiderweb Galaxy (MRC 1138-262 at _𝑧_ ≃ 2 _._ 16),
Gullberg et al. (2016b) have reported broad [C i](2-1) emission at a
projected distance of _𝑑_ ≃ 4 kpc from the main galaxy’s radio core. In
addition to this, [C i](1-0) emission, within the Spiderweb’s gas halo,
has been detected between _𝑑_ ≃ 17 and 70 kpc from its core (Emonts
et al. 2018). Other recent studies of [C i](1-0) line emission in HzRGs
have been carried out for two sources: 4C+14.17 at _𝑧_ = 3 _._ 8 (Nesvadba
et al. 2020) and 4C+19.71 at _𝑧_ ≃ 3 _._ 6 (Falkendal et al. 2021). With all
these results, it is clear that the drive to use [C i] as a molecular gas
tracer has certainly caught on thus strengthening its case for being
a similarly and perhaps even more reliable H 2 tracer than CO (e.g.
Dunne et al. 2022).
For tracing [C i](1-0) with sub-arcsecond resolution, the Atacama
Large Millimeter-submillimeter Array (ALMA) has frequency bands
3 and 4 which are best suited for probing emission from this atomic
transition at a redshift range of _𝑧_ = 2 _._ 9 − 4 _._ 5 where rest-UV lines
are detectable within the observational window of the Multi-Unit

Spectroscopic Explorer (MUSE). Hence, with a combined ALMA
and MUSE dataset, we can perform a detailed kinematic analysis
of both the ionised and molecular gas. In doing so, we are capable
of assessing the probable effects of shock-induced turbulence from
radio jets as well as photon-heating on the molecular gas within the
ISM (Mahony et al. 2013; Morganti & Oosterloo 2018) and possibly
also the CGM (McNamara et al. 2016).
We have therefore constructed a sample of seven HzRGs with
redshifts spanning _𝑧_ = 2 _._ 9 − 4 _._ 5 _._ This galaxy sample has been observed with both ALMA in [C i](1-0) and MUSE which probes the
Ly _𝛼_ emission. In tandem, the ALMA and MUSE observations pro
∼
vide us with a multi-wavelength view of the cold ( 10 K) and warm
(∼ 10 [4] − 10 [5] K) gas phases of baryonic haloes surrounding radio
galaxies. With such an imaging set, we are capable of gauging the
impact of high-powered radio jets on the multi-phase gas within both
a galaxies’ ISM and its surrounding CGM.
This paper is structured in the following way: Section 2 describes
the sample selection; Section 3 provides an overview of the data
acquisition and analysis procedures; Section 4 explains the method
for the analysis; and in Section 5, we describe the overall results of
this study and explore the implications of our findings. A summary
is provided in Section 6. Throughout, we have made use of ΛCDM
cosmology as defined by Planck Collaboration et al. (2016) where
H 0 = 67 _._ 8 km s [−][1] Mpc [−][1] and Ω m = 0 _._ 308 _._


**2** **GALAXY SAMPLE SELECTION**


The radio galaxies covered in this work are drawn from legacy radio
surveys. Our sample, in particular, comprises seven targets which are
listed sources in the Molongolo Reference Catalogue (MRC; Large
et al. 1981) and Fourth Cambridge Catalogue (4C; Pilkington & Scott

1965). The targets are radio sources with optical counterparts i.e.
radio galaxies with rest-frame 5 GHz luminosities of ≥ 10 [25] W Hz [−][1]

which imply the presence of radio-loud AGN (Miller et al. 1990).
Currently, radio galaxies are known out to redshifts of _𝑧_ =5.72 (Saxena
et al. 2018). Generally speaking, those above a redshift of 2 (i.e.,
_𝑧>_ 2) are referred to as high- _𝑧_ radio galaxies (HzRGs) which are rare
and require a significant amount of optical and infrared spectroscopic
observing time for reliable constraints on their redshifts to be made.
Despite this, several radio selection techniques have already been
applied to pre-select high- _𝑧_ radio galaxy candidates (e.g. Drouart
et al. 2020). As a result of the stringency of pre-selections, however,
the space density of HzRGs is not sufficiently constrained, at the
present time.
Our ALMA+MUSE sample has been selected from a large survey
program designed to study stellar mass build up and star-formation
in distant radio galaxies at 1 _._ 0 _<_ _𝑧<_ 5 _._ 2 with the _Spitzer_ Space Telescope (Seymour et al. 2007; De Breuck et al. 2010). This dedicated
_Spitzer_ HzRGs program consists of 71 HzRGs which have stellar
masses which range from _𝑀_ _★_ ≃ 10 [11] − 10 [11] _[.]_ [5] M ⊙ (details on stellar
mass inferences are given in Section 3.3). The 3 _._ 6 − 850 _𝜇_ m _Spitzer_
and _Herschel_ photometry first reported by Drouart et al. (2014) have
been combined with ALMA continuum observations to obtain SED

fits that provide the star-formation rate measures for the galaxies in
our sample (Falkendal et al. 2019).
With the goal of simultaneously tracing the ionised and molecular
gas components of the extended halos of HzRGs, we have defined
a sub-sample of seven HzRGs that are observable both in Ly _𝛼_ with
MUSE and in [C i] with ALMA. For ALMA, we targeted the neutral
carbon, ground-state transition line [C i] [3] _𝑃_ 1 → [3] _𝑃_ 0 (hereinafter

[C i](1-0) at _𝜈_ rest = 492.161 GHz), with simultaneous coverage of
13 CO(4-3) at _𝜈_ rest = 440.765 GHz. This was done with the aim of
tracing the cold gas component within the host galaxies and their
extended haloes. At the 2 _._ 9 ≲ _𝑧_ ≲ 4 _._ 5 redshift coverage of our subsample, the [C i](1-0) line can be observed in ALMA bands 3 and
4.

On the other hand, the MUSE survey targeted rest-frame UV
emission lines that are observable within the spectral window of
MUSE (in the wide-field mode) which covers a wavelength range of
_𝜆_ obs = 4800 − 9300 Å _._ The MUSE observations are ideal for tracing
warm ionised gas at redshifts of _𝑧_ = 2 _._ 9−6 _._ 6 where the Ly _𝛼𝜆_ 1216 Å
line falls within the MUSE spectral window. The blue edge of MUSE
sets the lower redshift range of our subsample.
To place our sample into the general context of high- _𝑧_ galaxies, we construct a SFR- _𝑀_ _★_ plane (Fig. 1) where our targets are
shown against HzRGs from previous studies and star-forming galaxies (SFGs) at _𝑧>_ 1 _._ 0 _._ The SFRs for the HzRGs represented in the
figure have been adapted from Falkendal et al. (2019) who make
use of _Herschel_, _Spitzer_ and ALMA photometry to perform SEDtemplate fitting and derive the infrared (IR) luminosities required to
estimate SFRs for the galaxies. Additionally, Seymour et al. (2007)
use _Spitzer_ photometry to perform SED-fits that yield _𝑀_ _★_ as upper
limits for the 26 out of 29 HzRGs from our study as well as the literature in Fig. 1. _𝑀_ _★_ constraints are made for 3 out of the 29 HzRGs
shown.


**3** **OBSERVATIONS AND DATA REDUCTION**


**3.1** **ALMA**


The radio galaxies in our sample were observed in ALMA bands
3 (Kerr et al. 2014) and 4 (Asayama et al. 2014) during ALMA



_Faint carbon emission in high-𝑧_ _radio galaxies_ 3


Cycle 3 under the project ID 2015.1.00530.S (PI: De Breuck) on
the dates provided in Table 1. The correlator configurations was set
to observe two contiguous spectral windows covering the [C i](1-0)
line and continuum in one side-band and the remaining two spectral
windows simultaneously covering the [13] CO(4-3) line and continuum
in the other side-band. All four spectral windows were recorded in
Frequency Domain Mode with a bandwidth 1875 MHz and spectral
resolution of 3.904 MHz.

We generated the calibrated measurement sets using the calibration
scripts provided by the ALMA Observatory using casa ( _Common_
_Astronomy_ _Software_ _Applications_ ) versions 4.5.1, 4.5.3, 4.6.0, and
4.7.2 (McMullin et al. 2007). For the imaging, we used the data reduction pipeline (casa-6.2.1.7 and a natural _uv_ -weighting ( `robust`
parameter 2) to optimise the signal-to-noise ratio (S/N) at the expense
of spatial resolution. As the CGM emission can be quite spatially extended (e.g. Emonts et al. 2018), we also made an attempt at tapering
the 12m _uv_ -data with 2 [′′], 3 [′′], and 4 [′′] Gaussian width options. For all
sources, with the exception of MRC 0943-292, an increase in noise
due to the reduced amount of data decreased the S/N data overall.

Hence, we opted to continue forward with the untapered images for
which the spatial resolution is provided in Table 3.1. Continuum subtraction was performed using the _uvcontsub()_ task and spectral-line
cubes were generated with a range of velocity resolutions from 9 to 64
km s [−][1], where we selected the binning that provides the most optimal
line S/N for the observed line width. The images were primary beam
corrected with the casa task _impbcor()_ . For the 1D spectra, pixels
were averaged over 2 [′′] diameter apertures. The moment-0 maps (i.e.
narrow-band images) were created with casa _immoments()_ in which
we images were integrated over frequency ranges shown in Fig. 3.
The 1 _𝜎_ rms levels in the [C i] spectra are two orders of magnitude
smaller than the [C i] contour levels shown in the corresponding images due to the velocity integration performed during the moment-0
map creation.


**3.2** **MUSE**


From the MUSE IFU spectrograph, we acquired rest-UV line and
continuum observations for the sample of radio galaxies. Mounted
on VLT Yepun (UT4), MUSE covers a spectral range of 4800−9300 Å
where the spectral resolution ranges from 2 _._ 82 − 2 _._ 74 Å between the
blue and red wavelength extremities of the MUSE spectral window.
All of the galaxies, excluding for 4C+03.24 and MRC 0943-242,
were observed in WFM-NOAO-N (nominal wide-field mode with
no adapative optics system in place) mostly under the program IDs
096.B-0752 and 097.B-0323 (PI: Vernet) on several nights between
2015 October and 2016 September (see Table 1).
The galaxy, 4C+03.24, was observed under program IDs 060.A9100(G) during the GALACSI/WFM commissioning run in 2017
June. TN J1338-1942 was observed under 60.A-9318(A) and 060.A9100(B) during the science verification and second MUSE commissioning run, from 2014 April to June. For MRC 0943-242 which was
observed in WFM-NOAO-E (extended wide-field mode, no adapative
optics), we also include the data of obtained during first commissioning in 2014 February under 60.A-9100(A).
We processed the raw observations using a standard data reduction
procedure in esorex v.2.8.4 (Weilbacher et al. 2020) which produced
the final data-cube for each galaxy. We then ran a principal component
analysis based procedure called _Zurich Atmosphere Purge_ (zap 2.0)
(Soto et al. 2016) on the reduced data-cubes in order to subtract
telluric sky line emission where it is most present at the red end of
the MUSE spectral window.
To create the Ly _𝛼_ narrow-band images, the MUSE data-cubes


MNRAS **000**, 1–16 (2022)

4 _S. Kolwa et al._


**Figure 1.** The star-formation rate as a function of stellar mass for HzRGs and several classes of SFGs. The HzRGs from the ALMA+MUSE sample (orange)
presented in this work are shown alongside an HzRG sample (Falkendal et al. 2019) in red. Lensed SFGs (lSFGs in navy blue), compact SFGs (blue) and normal
SFGs (sky blue) are shown. The main sequence of star-forming galaxies from Schreiber et al. (2015) at _𝑧_ = 2 _._ 52 _,_ the median redshift across all the galaxies
depicted, is shown in grey with a 0.3 dex region of scatter in SFR which corresponds to a 1 _𝜎_ dispersion in log 10 (SFR/M ⊙ yr [−][1] ) which is based on empirical
results from a flux-limited sample of galaxies with _Spitzer_ MIPS (Noeske et al. 2007; Elbaz et al. 2007). The data point sizes are scaled as 10 _𝑧_ [2] where _𝑧_ is the
redshift of the galaxy. Literature references of the galaxy samples are provided in the text. We include a sample of a _Herschel_ -detected, lensed SFGs using their
magnification-corrected SFR and _𝑀_ _★_ measures (Sharon et al. 2013; Bothwell et al. 2013b; Dessauges-Zavadsky et al. 2015; Nayyeri et al. 2017). The figure
also shows a sample of six compact SFGs (Tadaki et al. 2015; Spilker et al. 2016; Popping et al. 2017; Tadaki et al. 2017; Barro et al. 2017). Additionally, a
sample of normal SFGs have been adapted from Tadaki et al. (2015) and are shown in the figure as well.


**Table 1.** ALMA and MUSE observation details for the 2 _._ 9 ≲ _𝑧_ ≲ 4 _._ 5 radio galaxy sample. Columns (1) and (2) show the galaxy catalogue names and literature
redshifts. Column (3) indicates the start and end dates for the completion of the 12m ALMA observations, column (4) shows the on-source integration time
( _𝑡_ int _._ ). In column (5), we provide the full-width at half maximum (FWHM) of the synthesised beam along its major and minor axes. Column (6) shows the MUSE
observing dates. Column (7) indicates the source exposure time ( _𝑡_ exp _._ ). Column (8) indicates the seeing conditions during observations which are obtained from
the average FWHM of the brightest foreground star in the field.


|Galaxy|ALMA<br>Observing dates (𝑡i mnt (b am rca sj × b )min<br>in) e c2|MUSE<br>Observing Dates 𝑡exp. Seeing<br>(min) (arcsec)|
|---|---|---|
|MRC 0943-242<br>TN J0205+2242<br>TN J0121+1320<br>4C+03.24<br>4C+19.71<br>TN J1338-1942<br>4C+04.11|04/03/2016 - 20/05/2016<br>45<br>2_._09 × 1_._33<br>08/03/2016 - 13/09/2016<br>44<br>2_._28 × 1_._81<br>06/03/2016 - 24/09/2016<br>40<br>1_._98 × 1_._47<br>06/03/2016<br>38<br>2_._23 × 1_._62<br>06/03/2016 - 24/09/2016<br>39<br>1_._98 × 1_._81<br>16/03/2016 - 22/09/2016<br>40<br>1_._98 × 1_._61<br>05/03/2016 - 03/05/2016<br>43<br>2_._24 × 2_._17|21/02/2014 - 18/01/2016<br>312<br>0.65<br>03/12/2015 - 08/12/2015<br>254<br>0.73<br>06/10/2015 - 28/08/2016<br>318<br>0.83<br>17/06/2017 - 18/06/2017<br>75<br>0.63<br>08/06/2016 - 02/09/2016<br>350<br>1.03<br>30/04/2014 - 30/06/2014<br>535<br>0.77<br>03/12/2015 - 15/12/2015<br>254<br>0.88|



were integrated along the spectral axes over 15 Å around the peak in
Ly _𝛼_ emission in each source. The images have a sampling rate of 0 _._ 2×
0 _._ 2 arcsec [2] per pixel which is seeing-limited to an average 1 _._ 0 [′′] in
our observations. We note that some of the MUSE data on individual

sources has already been published in previous papers (Swinbank


MNRAS **000**, 1–16 (2022)



et al. 2015; Gullberg et al. 2016a; Vernet et al. 2017; Falkendal et al.
2019; Kolwa et al. 2019; Wang et al. 2021). Additionally, detailed
tomography of the Ly _𝛼_ nebulae for eight radio-loud AGN (including
the seven galaxies from our sample) are reported in Wang et al.
(2023).

**3.3** **Ancillary data**


Optical, near-infrared (NIR) and radio data are available for the HzRG
sample which we have selected. The multi-wavelength dataset includes _Hubble Space Telescope_ (HST) wide-band imaging obtained
with Wide-field Planetary Camera 2 (WFPC2) with the F702W filter which has a spectral coverage of 5865 _._ 66 − 8433 _._ 19 Å useful for
tracing the continua of O & B-type stars in high- _𝑧_ sources (Pentericci
et al. 1997). The reduced HST images images are accessible via the
[Hubble Legacy Archive (HLA).](https://hla.stsci.edu/hlaview.html)

The _Spitzer_ Space Telescope images of radio galaxies reveal emission from evolved stellar populations (Seymour et al. 2007). We
have obtained rest-frame _𝐾_ −band detections from the Infrared Array
Camera (IRAC; 3 _._ 6 − 8 _._ 0 _𝜇_ m). In addition to those taken by the
other _Spitzer_ instruments: Infrared Spectrograph (IRS; 16 _𝜇_ m) and
Multiband Imaging Photometer for _Spitzer_ (MIPS; 24 − 160 _𝜇_ m),
_Spitzer_ images we use in this study are available and accessible from
a dedicated _Spitzer_ [HzRGs (SHzRGs) archive. The near-IR,](http://www.eso.org/~cdebreuc/shzrg/) _Spitzer_
and _Herschel_ data (De Breuck et al. 2010; Drouart et al. 2014) provide stellar masses and star formation rates (or limits thereof) for our
entire sample, which allows us to derive the evolutionary state of the
galaxies relative to the Main Sequence of star-forming galaxies (see
Fig. 1). We note that the stellar masses reported by Seymour et al.
(2007) and De Breuck et al. (2010) are often upper limits due to
potential contributions from the hot dust torus emission to the restframe 1.6 _𝜇_ m photometry. However, this approach is conservative, as
most of the stellar populations are consistent with the _𝐾_ -band photometry. As a result, the real stellar masses in Fig. 1 are expected to
be sufficiently close to the upper limits, which unlike normaly upper
limits, have been measured from significantly deep photometry. For
the radio imaging of these sources, we obtained archival C-band (4.8
GHz) and X-band (8.3 GHz) images from the Karl G. Jansky Very
Large Array (VLA) that indicate the locations of the radio hotspots
(Carilli et al. 1997; Pentericci et al. 2000).


**4** **DATA ANALYSIS**


**4.1** **Systemic Redshift Estimation**


The galaxies in our combined ALMA+MUSE sample have spectroscopic redshifts from the literature which are based on a variety
of line tracers which we provide references of in table 2. With the
advent of optical 3D data cubes, the complex kinematic structure
of extended ionised gas haloes has become more apparent revealing
outflowing ionised gas from AGN host galaxies (e.g. Molyneux et al.
2019; Couto et al. 2020; Riffel et al. 2023). The presence of such
components can lead to offsets of several hundreds of km s [−][1] when
estimating systemic redshifts, even when non-resonant lines such as
He ii are used (e.g. Kolwa et al. 2019).
The He ii _𝜆_ 1640 recombination line is our benchmark for setting
the systemic redshift of each galaxy. The He ii profiles are extracted
from the galaxy positions in the MUSE data-cubes for all the sources
except 4C+03.24 which does not have detected He ii emission at its
core, and 4C+19.71, where the He ii line coincides with a spectral
region affected by skyline residuals. The 1D spectra are extracted
from aperture diameters of 5 pixels or 1 [′′] at the positions of the host
galaxies which are determined from the radio cores (Carilli et al.
1997; Pentericci et al. 2000) and the _Spitzer_ imaging which indicates
the extent of the evolved stellar distribution (see Fig 3). The size
of the aperture is chosen (i) to match the seeing element (of width
0 _._ 9 [′′] ∼ 1 _._ 0 [′′] ) estimated from stars in the MUSE fields of view;
(ii) to maximise the spectral S/N ratio; (iii) to avoid contamination



_Faint carbon emission in high-𝑧_ _radio galaxies_ 5


(a)


(b)


**Figure 2.** MUSE-detected He ii _𝜆_ 1640 emission in TN J1338-1952 integrated
over 8345 _._ 65 − 8362 _._ 38 Å in panel A and 8376 − 8393 Å in panel B (greyscale with black contours) against the _Spitzer_ IRAC2 continuum (red).


from non-systemic line emission components further away from the
core which may emerge within the line profile as the aperture size is
increased.

We began by applying a Gaussian fit to the He ii profiles of MRC
0943-242, TN J0205+2242, TN J0121+1320 and 4C+04.11 where
the Gaussian peak ( _𝐴_ ), width ( _𝜎_ ) and centre ( _𝜆_ _𝑐_ ) were fit to the
data with _𝐴_ as a free parameter and sigma constrained within the
wavelength range 2 − 15 Å and _𝜆_ _𝑐_ is allowed to deviate ±5 Å from
its initial value. The He ii emission of TN J1338-1942 is spatially
extended and, when extracted to form a 1D spectrum, it is seen to have
two distinct spectral profiles: one at the position of the host galaxy and
the other offset in projected distance from the host galaxy illustrated
in Fig. 2. As a result, a double Gaussian profile, with components that
are independent of one another, is fit to the spectrum. The peak, width
and line centres are constrained by the same boundary conditions as
those used for the single Gaussian fits.
In the case of a single emission component, the Gaussian centre
is used to infer the systemic redshift of the source. For a double
emission component, we needed to carefully select which Gaussian
component represents the systemic redshift. We therefore look for
a spatial overlap between the He ii and _𝐾_ −band continuum from
_Spitzer_ /IRAC2 to confirm which emission component in He ii traces
the host galaxy and should thus represent the systemic redshift.
As a result, we obtain 1D spectral line models which are shown in
Fig. 3, with the results being listed in Table 2. Where [C i] is detected,
the He ii and [C i] redshifts are fully consistent within the margin of
error. Given the low S/N of our [C i] data, the uncertainties of the [C i]


MNRAS **000**, 1–16 (2022)

6 _S. Kolwa et al._


redshifts are higher than on the He ii redshifts (Table 2) hence the
current ALMA data may not be able to improve the overall systemic
redshift accuracy but they do allow for a consistency check. In two
sources, the He ii line cannot be fit due to its low S/N. Here, the [C i]
line is used to constrain the systemic redshift for the 4C+03.24 and
4C+19.71. In 4C+03.24, He ii is not detected and we fix the redshift
to the centre of the [C i] line (bottom panel of Fig. 3). In 4C+19.71,
He ii is strongly affected by skyline residuals (e.g Falkendal et al.
2021), even though some of the line emission is discernible, we
provide as a Gaussian profile that is fixed to the [C i] redshift (top
panel of Fig. 3) and label this _He ii fix_ in the figure.


**4.2** **[C i] narrow-band imaging**


Locating [C i] emission in projection is crucial in determining
whether the traced gas is associated with the host galaxy or extended
CGM. We use the narrow-band images created with the procedure
described in Section 3.1. The maps are spectrally integrated over velocity intervals which display the spatial extent of [C i] emission by
summing the consecutive channels which exceed the zero-flux level.
For the three galaxies where [C i] is not detected, we do not construct
a moment-0 map or continuum-subtract because none of the galaxies
show any significant continuum emission. The [C i] contours in Fig.
3 are rather close to the AGN host galaxies detected with _Spitzer_,
indicating that our faint [C i] detections are likely to be associated
with the host galaxies.


**4.3** **Neutral carbon spectral line fits**


In this study, we trace molecular gas via the [C i] lines which we fit
using single Gaussian models. Our [C i] line spectra are extracted
from primary-beam corrected image cubes in 2 [′′] diameter apertures
(∼15 kpc at _𝑧_ = 3 _._ 5) which have similar dimensions as the synthesised beams for each observation. We select this aperture size to
ensure that (i) the full central part of the host galaxy is included,
and (ii) the extracted 1D spectra have sufficient S/N to provide a
stable convergence of the fitting algorithm. The sky co-ordinates of
the host galaxies are already known from VLA radio continuum detections and (Carilli et al. 1997; Pentericci et al. 2000) and _Spitzer_
near-infrared observations of the host galaxies (Seymour et al. 2007;
De Breuck et al. 2010).
A high degree of certainty in the host galaxy positions is provided
by the sub-arcsecond astrometry in both the MUSE and legacy VLA
observations; hence we can extract spectra of the AGN host galaxies
using the positions of the radio cores. For this procedure, fixing the
locations, however, does not necessarily optimise the S/N as the peak
of the [C i] emission may have a small spatial offset from the AGN
host galaxy. This is still acceptable for our purposes because we only
aim to determine the [C i] content inside the AGN host galaxies which
can provide us with an indication of the molecular gas available for
star-formation. The synthesised beam sizes are 1 [′′] in radius which at
_𝑧_ = 3 _._ 5 corresponds to a projected size of ∼15 kpc which sufficiently
covers the host galaxy sizes represented by the _Spitzer_ IRAC _𝐾_ -band
contours in the narrow-band images.
On the extracted 1D spectra, we fit the lines in a similar manner as
that for the single-peaked He ii lines (see Section 4.1). The extracted
spectra are shown in the bottom left panels of Fig. 3 with the results
of the fit convergence displayed in Table 3. The He ii and [C i] line
fits are completely independently of one another.


MNRAS **000**, 1–16 (2022)



**4.4** **Neutral carbon line luminosity and molecular gas mass**


From the [C i] spectral line fitting, we obtain [C i] line flux density
measures to infer line luminosities and [C i]-derived H 2 masses for
the radio-AGN host galaxies. For non-detections, we estimate 5 _𝜎_
flux density upper limits of _𝑆_ [C i] dV = 5 _𝜎_ rms ~~√~~ _𝛿_ 𝑣Δ𝑣 where _𝜎_ rms

is the root-mean-square (RMS) level in the 1D spectrum estimated
over a velocity range of -50 to 50 km s [−][1] _._ The average channel size
is denoted by _𝛿_ 𝑣 _._ This velocity width, Δ𝑣 ≃ 100 km s [−][1] _,_ is based
on the assumption that emission from the cold gas is traced by line
dispersions of the order ∼100 km s [−][1] _._
We calculate the line luminosity of [C i], _𝐿_ [′] [C i] _[,]_ [(e.g.] [Solomon]
et al. 1992) as,

_𝐿_ [′] [C i] [=][ 3] _[.]_ [25][ ×][ 10] [4] _[𝑆]_ [[][C i][]] [dV] _[ 𝜈]_ obs [−][2] [(][1][ +] _[ 𝑧]_ [)] [−][3] _[𝐷]_ [2] L _[,]_ (1)

to obtain _𝐿_ [′] [C i] [in K km s] [−][1] [ pc] [2] _[.]_ [ Here,] _[ 𝑆]_ [[][C i][]] [dV is the integrated flux]

in mJy km s [−][1], _𝜈_ obs is the observed frequency of [C i] in GHz, _𝐷_ L
is the luminosity distance of the source in Mpc and _𝑧_ is its redshift.
Alternatively, the line luminosity in solar luminosities (L ⊙ ) may be
written as,

_𝐿_ [C i] = 1 _._ 04 × 10 [−][6] _𝑆_ [C i] dV _𝜈_ rest (1 + _𝑧_ ) [−][1] _𝐷_ [2] L (2)


where, as in equation 1, _𝑆_ [C i] dV is the integrated flux in mJy km
s [−][1], _𝜈_ rest = 492 _._ 161 GHz, the rest frequency of the [C i](1-0) line,
and _𝐷_ L is the luminosity distance of the source in Mpc and _𝑧_ is its
redshift.

The [C i] line luminosity provides an inference for molecular gas
mass in solar masses (M ⊙ ) via the equation,



_𝑋_ [C i]
� 10 [−][5]



� −1 � Jy km s _𝑆_ [C i] dV [−][1]



_._
�



−1
A 10
� � 10 [−][7] s [−][1]



_𝑀_ H 2 _,_ [C i] = [1375] _[.]_ [8]

_𝑄_ 10



_𝐷_ [2]
L
(1 + _𝑧_ )



(3)


In equation 3, the luminosity distance, _𝐷_ L _,_ is in Mpc, the Einstein
A-coefficient is A 10 = 7 _._ 93×10 [−][8] s [−][1] _._ We use a [C i](1-0) excitation
factor of _𝑄_ 10 = 0 _._ 48 and a carbon abundance of _𝑋_ [C i] = 3 _._ 0 × 10 [−][5]

(Weiß et al. 2005).
Three galaxies in our sample are not detected in [C i](1-0). For
these sources, the 5 _𝜎_ upper limits yield flux estimates of ≲ 100
mJy km s [−][1] where we assume a line-width of 100 km s [−][1] . To contextualise these non-detections, we recast our sensitivity limits in
terms of molecular gas mass limits, assuming (like for our detections) Q 10 = 0 _._ 48 and X [C i] = 3 × 10 [−][5] _._ This results in upper
limits of _𝑀_ H 2 _,_ [CI] _<_ (0 _._ 5 − 1 _._ 0) × 10 [10] M ⊙ . Unfortunately, no CO
observations have been reported for these three galaxies, hence we
cannot determine whether the [C i] upper limits are consistent with
CO-derived masses in these three sources.


**5** **RESULTS AND DISCUSSION**


**5.1** **Neutral carbon within the host galaxies**


Based on our results, we find that [C i] emission is fainter than expected compared to recent detections of this line in HzRGs such as
the Spiderweb galaxy (Gullberg et al. 2016a; Emonts et al. 2018)
and PKS 0529-54 (Lelli et al. 2018; Man et al. 2019). At least three
HzRGs in our observations are not detected in [C i], while the remaining four have 2 − 3 _𝜎_ level line detections. Nevertheless, we
consider this faint line emission worth reporting because it overlaps both spatially and spectrally with the He ii emission seen by
MUSE which traces the warm ionised gas within the ISM. Additionally, the [C i] detections spatially overlap with the AGN based on

_Faint carbon emission in high-𝑧_ _radio galaxies_ 7


**Table** **2.** Redshifts of galaxies from the ALMA+MUSE HzRG sample, named in column (1), are based on He ii _𝜆_ 1640 and [C i](1-0) line fitting shown in
columns (2) and (3). The literature redshift is shown in column (4) with the cited source provided in column (5).


Galaxy He ii redshift [C i] redshift Literature redshift Reference


MRC 0943-242 2 _._ 9230 ± 0 _._ 0001 2 _._ 9215 ± 0 _._ 003 2 _._ 9230 ± 0 _._ 0020 Roettgering et al. (1997)
TN J0205+2242 3 _._ 5060 ± 0 _._ 0003 _. . ._ 3 _._ 5061 ± 0 _._ 0004 De Breuck et al. (2001)
TN J0121+1320 3 _._ 5190 ± 0 _._ 0002 3 _._ 5230 ± 0 _._ 004 3 _._ 5200 ± 0 _._ 0007 Nesvadba et al. (2007)
4C+03.24 _. . ._ 3 _._ 5828 ± 0 _._ 004 3 _._ 5699 ± 0 _._ 0003 van Ojik et al. (1996)
4C+19.71 _. . ._ 3 _._ 5892 ± 0 _._ 004 3 _._ 5935 ± 0 _._ 0007 Nesvadba et al. (2017)
TN J1338-1942 4 _._ 0959 ± 0 _._ 0005 _. . ._ 4 _._ 1057 ± 0 _._ 0004 Swinbank et al. (2015)
4C+04.11 4 _._ 5080 ± 0 _._ 0002 _. . ._ 4 _._ 5100 ± 0 _._ 0001 Nesvadba et al. (2017)



the VLA-detected synchrotron emission labelled in Fig. 3. Although
deeper [C i] observations are required to accurately constrain the line
widths and the spatial extent of cold gas traced by neutral carbon,
we already observe [C i] faint emission as a necessary motivation for
future searches of [C i] within other samples of AGN host galaxies.


In our results, the galaxy TN J0121+132 is observed with a 2 _𝜎_

[C i] that traces the full velocity dispersion of the galaxy. Its observed
line width of 565 ± 194 km s [−][1] is consistent with that of the CO(3-2)
detection in this galaxy (De Breuck et al. 2003). In the other galaxies
from our sample, we observe narrow [C i] emission up to a minimum
width of 40 km s [−][1] (see Table 3). The four detections include the
previously reported narrow [C i] line in 4C+19.71 (Falkendal et al.
2021). Due to our different extraction aperture, we recover a slightly
different line profile from the same dataset, which has an intermediate
in line width between TN J0121+1320 and two galaxies, 4C+03.24
and MRC 0943-242, which have line-widths with the same order
of magnitude (∼50 km s [−][1] ). [C i] velocity dispersions of this width
are not commonly observed and should be followed up with deeper
observations to trace the full extent of the [C i] emission line. We
note that there is a significant agreement in redshift between [C i]
and He ii, especially in the galaxy MRC 0943-242 (see Fig. 3). This
further justifies the use of [C i] lines as a proxy for the systemic
redshifts of galaxies (see §4.1 for more details). Overall, we obtain
flux density measures of _𝑆_ [C i] dV ≤ 100 mJy km s [−][1] and nondetections being reported with upper-limits in the [C i] flux density.
Both [C i] line constraints and upper limits of as well as the molecular
gas masses inferred are shown in Table 3.


Generally, [C i] line-widths represent gas kinematics of the cold
atomic and molecular gas phase. In our study, the line-widths have
been integrated over the full extent of the galactic disk. In MRC
0943-242 and 4C+03.24, the dispersions range from 40-50 km s [−][1]

and are insufficiently broad to cover the rotational velocity of the host
galaxy and can therefore only trace single molecular clouds within
the galaxy. For these two galaxies in our small sample, we observe
dispersions that are consistent with galaxy kinematics in 4C+19.17 − 1
and TN J0121+1320 which have line-widths of 179 ± 60 km s and

− 1
565 ± 194 km s _,_ respectively. Such dispersions are comparable
to those observed in high- _𝑧_ dusty star-forming galaxies (DSFGs)
and SMGs where FWHM ≃ 200 − 1000 km s [−][1] (Alaghband-Zadeh
et al. 2013; Bothwell et al. 2017; Nesvadba et al. 2019). In DSFGs
and SMGs, X-ray and UV radiation from the AGN and star-forming
regions, respectively, heat up gas sufficiently to sustain the broad line
dispersions observed in cold gas tracers such as [C i].


Broad CO emission lines have also been detected in low- _𝑧_ ULIRGS

which have similar ISM thermodynamic conditions as high- _𝑧_ DSFGs
and SMGs where CO gas can exist in gas regions where cosmic rays



are dominant (Bradford et al. 2003; Papadopoulos & Thi 2013). Two
galaxies from our sample, TN J0121+1320 and 4C+19.71 have similar line widths as the DSFGs and SMGs. The line widths in these two

HzRGs may be tracing the gas kinematics of molecular clouds spread
throughout the galaxy. We note, however, that significantly deeper

[C i] observations would be required to obtain reliable kinematic
inferences as previously demonstrated in De Breuck et al. (2014)
where shallow [C ii] data provided a rotation curve based on the cold
gas tracers. In fact, these results have been recently fine-tuned using
deeper detections in Lelli et al. (2021) as evidence for the importance
in sometimes obtaining follow-up observations of low S/N data.


A more direct comparison of our results to previous observations
is possible via [C i] detections in PKS 0529-54 and MRC 1138-262
( _𝑧_ ≃ 2 _._ 2; Spiderweb Galaxy). In PKS 0529-54 ( _𝑧_ ≃ 2 _._ 6), the shallow

[C i](2-1) profile was interpreted in two ways: Man et al. (2019) associated both velocity components with distinct star-forming regions
within the galaxy, while Lelli et al. (2018) interpreted the observations as evidence for a rotating disk with a circular velocity of 310
km s [−][1] . In an upcoming study of the same source, ALMA Cycle 6
observations provide [C i](2-1) line emission of FWHM = 615 ± 56
km s [−][1] and [C i](1-0) line emission of FWHM = 848 ± 230 km s [−][1]

(Huang et al. 2023). Both emission components are broader than
the values reported in Table 4 of Man et al. (2019). Additionally,
the newly detected broadened line emission has made it possible to
constrain the redshift from the deeper [C i] line observations.


For the Spiderweb galaxy, Gullberg et al. (2016b) report a more
complex [C i](2-1) morphology consisting of two spatial components: one of which contains a broad emission lines of width 1100 km
s [−][1] and one with a width of 270 km s [−][1] . Additionally, Emonts et al.
(2018) report a similar velocity profile for the Spiderweb Galaxy
in [C i](1-0) emission seen in observations that unfortunately lack
the spatial resolution required to resolve the two spatial components
along the spectral axis. In comparison the [C i](1-0) line detections
in 4C+03.24 and MRC 0943-242 from our results have line-widths

which are a factor of 5 − 10 narrower than what is expected based on
the previous studies we have discussed here (Gullberg et al. 2016b;
Emonts et al. 2018; Lelli et al. 2018; Man et al. 2019). In the case of
MRC 0943-242, however, Gullberg et al. (2016b) report a CO(8-7)
FWHM of 43±13 km s [−][1], fully consistent with the 40±14 km s [−][1]

we find in [C i].


In terms of [C i] velocity dispersion, the most anomalous source in
our sample is TN J0121+1320 which has a [C i] line-width of ∼600
km s [−][1] and is located above the Main Sequence of star-forming
galaxies, as seen in Fig. 1. Within our sample, this source also has
the highest SFR measure (see Table 3) which places it at the upper
reach of the Main Sequence in Fig. 5 from Falkendal et al. (2019)


MNRAS **000**, 1–16 (2022)

8 _S. Kolwa et al._



500


400


300


200


100


0


6


4


0.6


0.4


0.2


0.0


0.2


0.4


80


60


40


20


0


20

10

0.8


0.6


0.4


0.2


0.0


0.2


0.4




[CI]


1000 750 500 250 0 250 500 750 1000
v [km s 1 ], HeII


(c)



MRC0943

HeII



Best HeII fit

Best HeII fit sys.

Best HeII fit b.l.



9 [h] 45 [m] 33.2 [s] 33.0 [s] 32.8 [s] 32.6 [s] 32.4 [s]


(J2000)


(b)


2 [h] 05 [m] 11.0 [s] 10.8 [s] 10.6 [s] 10.4 [s] 10.2 [s]


(J2000)


(d)




[CI] Best [CI] fit


800 600 400 200 0 200 400 600 800
v [km s 1 ], HeII



TNJ0205
HeII



(a)



Best HeII fit



-24°28'45"


48"


51"


54"


22°42'54"


51"


48"


45"



**Figure** **3.** **Left:** MUSE He ii and ALMA [C i](1-0) line spectra of the host galaxies of MRC 0943-42 and TN J0205+2242, in the top and bottom panels,
respectively. The 1 _𝜎_ (rms) noise levels in the [C i] spectra for MRC 0943-42 and TN J0205+2242 are 0.335 and 0.260 mJy beam [−][1] respectively. The middle
panel shows the MUSE spectral variance ( _𝜎_ _𝑣_ ). All spectra have been extracted from the data cubes with a 1 [′′] aperture centred at the peak of the _𝐾_ -band
continuum. The ALMA [C i] channel binning is 9 and 11 km s [−][1] for MRC 0943-42 and TN J0205+2242, respectively. When the radio core is not seen, the
He ii is extracted from the peak of the _Spitzer_ /IRAC (4.5 _𝜇_ m) continuum. The yellow vertical bars in the MUSE spectra indicate the locations of skylines with
predicted _𝑓_ _𝜆_ _>_ 10 [−][16] erg s [−][1] Å [−][1] arcsec [−][2] (Hanuschik 2003). The He ii line is decomposed into the emission component at the host galaxy (systemic redshift)
and the blue-shifted emission is represented by the blue line (b.l.). **Right:** 14 × 14 [′′] MUSE narrow-band image centered on the Ly _𝛼_ line (the covered wavelength
range is reported in the image) with _Spitzer_ contours overplotted in pink. The [C i] contours are shown in blue and are in units of mJy beam [−][1] km s [−][1] The
orange crosses represent the hotspots of the radio lobes observed by the VLA in its C-band configuration. The contour levels represented for each data set are
shown directly in the overlay plots.



as well. In this work, we have obtained a tentative 2 _𝜎_ [C i] detection
from which we infer a molecular gas mass of ∼ 2 _._ 60 × 10 [10] M ⊙ .
Furthermore, the [C i] line dispersion and inferred H 2 mass are both
consistent with the galaxy’s position above the Main Sequence which
is evidence that is still has sufficient fuel star-formation at a relatively
high level (∼626 M ⊙ yr [−][1] ) compared to the other HzRGs within our
sample. For the HzRGs with narrow line emission, [C i] may be
tracing sub-kpc star-forming regions within the galaxy.

Another anomalous case from our sample is TN J1338-1942 which


MNRAS **000**, 1–16 (2022)



has a relatively high star-formation rate of ∼461 M ⊙ yr [−][1] but no
traceable [C i] line emission within its host galaxy. Its inferred molecular gas mass is an upper limit of _<_ 1 _._ 08 × 10 [10] M ⊙ . For this source,
Falkendal et al. (2019) reported a 92 GHz ALMA detection which
coincides spatially with the northern radio lobe. The spectral energy
distribution (in Fig. A.52 of Falkendal et al. (2019)) predicts equal
contributions from synchrotron and thermal dust emission at ∼92
GHz. Given the multi-band _Herschel_ detection, we are certain the
the high SFR measure is valid however the continuum data lacks the

_Faint carbon emission in high-𝑧_ _radio galaxies_ 9



200


150


100


50


0


15

10

5


0.3


0.2


0.1


0.0


0.1


0.2


60


40


20


0


50


25


0.4


0.2


0.0



TNJ0121
HeII



Best HeII fit



1 [h] 21 [m] 43.0 [s] 42.8 [s] 42.6 [s] 42.4 [s]


(J2000)


(b)




[CI] Best [CI] fit


1000 750 500 250 0 250 500 750 1000
v [km s 1 ], HeII



13°21'03"


00"


20'57"


54"


3°23'27"


24"


21"


18"


15"



4C03.24

HeII



(a)




[CI] Best [CI] fit



0.2

1000 750 500 250 0 250 500 750 1000
v [km s 1 ], [CI]


(c)



12 [h] 45 [m] 38.8 [s] 38.6 [s] 38.4 [s] 38.2 [s] 38.0 [s]


(J2000)


(d)



**Figure** **3.** continued: Here, we show the He ii and [C i] spectra alongside the multiwavelength narrow-band images for TN J0121+1320 (top) and 4C+03.24
(bottom). The 1 _𝜎_ (rms) noise levels in the [C i] spectra for TN J0121+1320 and 4C+03.24 are 0.311 and 0.189 mJy beam [−][1] respectively. The aperture for

[C i] spectral extraction is centered on the VLA-detected radio core position denoted by the white star. The ALMA [C i] binning are 64 and 43 km s [−][1] for TN
J0121+1320 and 4C+03.24, respectively.



spatial resolution to determine whether such a high SFR is spatially
coincident with the AGN or rather a component within a jet-cloud
interacting region at ∼10 kpc north of the galaxy nuclei. Higher spatial resolution thermal dust continuum detections are thus required
to properly constrain the star-formation properties of this source.


We estimate the strength of atomic line cooling by calculating the
ratio of the [C i] line luminosity to L IR luminosity (8 − 1000 _𝜇_ m).
For the radio galaxies sampled in this work, these line luminosity
ratios range from (2 − 15) × 10 [−][6] _._ A similarly radio-loud AGN host
at _𝑧_ ≃ 2 _._ 2 (MRC 1138-257) has a luminosity ratio of 5 _._ 6 × 10 [−][6]

based on L IR (the starburst component) reported in Seymour et al.
(2012) and _𝐿_ [′] [C i] [from] [Emonts] [et] [al.] [(][2018][).] [Previous] [works] [have]
shown that the _𝐿_ [′] [C i] [/L] [IR] [values] [for] [lensed] [SFGs] [and] [SMGs] [(at]

_𝑧_ = 2 − 4) range from (5 − 20) × 10 [−][6] (Nesvadba et al. 2019). For



lensed, dusty star-forming galaxies, this range is (2 − 18) × 10 [−][6]

(Bothwell et al. 2017). For unlensed SMGs at _𝑧_ ∼ 2 _._ 5 _,_ this value
ranges from (5 − 30) × 10 [−][6] (Alaghband-Zadeh et al. 2013). A
sample of Main Sequence galaxies at _𝑧_ ∼ 1 _._ 2 show line luminosity
ratios of (4 − 187) × 10 [−][6] Valentino et al. (2018). The _𝐿_ [′] [C i] [/L] [IR]
values obtained for the high- _𝑧_ radio galaxies sample in this work, are
comparable to those for other high- _𝑧_ galaxy populations but trace the
lower end of their _𝐿_ [′] [C i] [/L] [IR] [ranges.] [We] [summarise] [all] _[𝐿]_ [′] [C i] [/L] [IR]
ratios for our sample as well as those from the literature in Table 4.


MNRAS **000**, 1–16 (2022)

10 _S. Kolwa et al._



19°29'21"


18"


15"


12"


09"



HeII fix





60


40


20


0


20

10


0.8


0.6


0.4


0.2


0.0


0.2


0.4



4C19.71

HeII




[CI] Best [CI] fit



1500 1000 500 0 500 1000 1500
v [km s 1 ], [CI]



21 [h] 44 [m] 08.0 [s] 07.8 [s] 07.6 [s] 07.4 [s] 07.2 [s]


(J2000)



150


125


100


75


50


25


0


20

10


0.3


0.2


0.1


0.0


0.1


0.2


0.3



TNJ1338
HeII


[CI]



-19°42'27"


30"


33"


36"



(a)



Best HeII fit

Best HeII fit sys.

Best HeII fit redshift





2000 1500 1000 500 0 500 1000 1500 2000
v [km s 1 ], HeII



13 [h] 38 [m] 26.6 [s] 26.4 [s] 26.2 [s] 26.0 [s] 25.8 [s]


(J2000)



150


125


100


75


50


25


0


50
25


1.5


1.0


0.5


0.0


0.5


1.0



4C04.11

HeII


[CI]



Best HeII fit



5°08'09"


06"


03"


00"


07'57"



(c)





1000 750 500 250 0 250 500 750 1000
v [km s 1 ], HeII


(e)



3 [h] 11 [m] 48.4 [s] 48.2 [s] 48.0 [s] 47.8 [s] 47.6 [s]


(J2000)


(f)



**Figure 3.** continued: Here, we show the He ii and [C i] spectra alongside the multiwavelength narrow-band images for 4C+19.71 (top), TN J1338-1934 (middle),
and 4C04+11 (bottom). The 1 _𝜎_ (rms) noise levels in the [C i] spectra for 4C+19.71, TN J1338-1942 and 4C.04+11 are 0.366, 0.208 and 0.352 mJy beam [−][1]

respectively. The ALMA [C i] spectra are extracted from the _𝐾_ -band continuum peak in 4C+19.71 and the VLA-detected radio core TN J1338-1942 and
4C.04+11. The [C i] binnings are 43, 48 and 13 km s [−][1] for 4C+19.71, TN J1338-1942 and 4C.04+11, respectively.


MNRAS **000**, 1–16 (2022)

_Faint carbon emission in high-𝑧_ _radio galaxies_ 11


**Table** **3.** ALMA [C i](1-0) line parameters. In column (1), we provide the catalog name for the galaxy. Columns (2) to (4) list the observed frequency, the
full-width half maximum (FWHM) and integrated flux density of the [C i] lines, respectively. Column (5) gives the [C i]-inferred molecular hydrogen gas mass
and column (6) provides the star-formation rate reported by Falkendal et al. (2019); we have obtained SFR uncertainties by propagating the uncertainties in the
L [SF] _[𝛿]_ [SFR][ =][ SFR][(] _[ 𝛿]_ [L] [SF] _[𝑎]_ [For the 5] _[𝜎]_ [non-detections, a line-width of 100 km s] [−][1] [is assumed.]
IR _[,]_ [ as] IR [/][L] [SF] IR [)][. All uncertainties are reported at the 1] _[𝜎]_ [level.]
Stellar masses ( _𝑀_ _★_ ) are taken from De Breuck et al. (2010) _[𝑏]_ and Drouart et al. (2016) _[𝑐]_ .


Galaxy _𝜈_ obs FWHM _𝑆_ [C i] dV _𝑀_ H 2 SFR log M _★_ _𝐿_ [′] [C i] _𝐿_ [C i] L [SF] IR
(GHz) (km s [−][1] ) (mJy km s [−][1] ) (10 [10] M ⊙ ) (M ⊙ yr [−][1] ) (M ⊙ ) (10 [8] K km s [−][1] pc [2] ) (10 [6] L ⊙ ) (10 [12] L ⊙ )


MRC 0943-242 125.50 40 ± 14 25 ± 14 0 _._ 49 ± 0 _._ 27 41 [+] − [26] 33 11 _._ 22 _[𝑐]_ 5 _._ 45 ± 3 _._ 05 2.08 0 _._ 36 [+] − [0] 0 _[.]_ _._ [23] 29
TN J0205+2242 _[𝑎]_ . . . _. . ._ _<_ 24 _<_ 0 _._ 53 _<_ 84 10 _._ 82 _[𝑏]_ _<_ 28 _._ 7 _<_ 11 _._ 0 _<_ 0 _._ 74
TN J0121+1320 108.81 565 ± 194 98 ± 55 2 _._ 60 ± 1 _._ 46 626 [+] − [267] 243 11 _._ 02 _[𝑏]_ 29 _._ 0 ± 16 _._ 2 11.0 5 _._ 43 [+] − [2] 2 _[.]_ _._ [32] 11
4C+03.24 107.39 47 ± 16 24 ± 8 0 _._ 65 ± 0 _._ 22 142 [+] − [240] 130 11 _._ 27 _[𝑏]_ 7 _._ 28 ± 2 _._ 43 2.78 1 _._ 23 [+] − [2] 1 _[.]_ _._ [08] 13
4C+19.71 107.24 179 ± 60 93 ± 32 2 _._ 54 ± 0 _._ 88 84 [+] − [173] 62 11 _._ 13 _[𝑏]_ 28 _._ 3 ± 9 _._ 74 10.8 0 _._ 74 [+] − [1] 0 _[.]_ _._ [52] 55
TN J1338-1942 _[𝑎]_ . . . _. . ._ _<_ 93 _<_ 1 _._ 08 461 [+] − [298] 187 11 _._ 04 _[𝑏]_ _<_ 36 _._ 8 _<_ 14 4 _._ 02 [+] − [2] 1 _[.]_ _._ [60] 63
4C+04.11 _[𝑎]_ . . . _. . ._ _<_ 25 _<_ 1 _._ 06 _. . ._ 11 _._ 03 _[𝑏]_ _<_ 10 _._ 4 _<_ 3 _._ 98 _. . ._



**Table 4.** The [C i](1-0) to infrared (8 - 1000 _𝜇_ m) luminosity ratios ( _𝐿_ [′] [C i] [/L] [IR] [)]
for the radio-loud AGN hosts in this work compared to dusty star-forming
galaxies and Main Sequence ( _𝑧_ ∼ 1 _._ 2) galaxies.


Source(s) _𝐿_ [′] [C i] [/L] [IR] Reference
(10 [−][6] )


MRC 0943-242 5 _._ 8 This work

TN J0205+2242 _. . ._ " "

TN J0121+1320 2 _._ 0 " "

4C+03.24 2 _._ 3 " "

4C+19.71 15 " "

TN J1338-1942 _<_ 3 _._ 5 " "

MRC 1138-257 8 _._ 2 Emonts et al. (2018)

DSFGs 5 − 20 Nesvadba et al. (2019)
" " 2 − 18 Bothwell et al. (2017)
" " 5 − 30 Alaghband-Zadeh et al. (2013)
MS ( _𝑧_ ∼ 1 _._ 2) 4 − 187 Valentino et al. (2018)


**5.2** **Comparing CO and [C i]-derived molecular gas in high-** _𝑧_
**radio galaxies**


For two sources with both [C i] and CO detections, we can make
a direct comparison between the molecular gas tracers. In MRC
0943-242, Gullberg et al. (2016a) report a CO(8-7) detection and a
CO(1-0) upper limit. Scaling the CO(8-7) detections of 0.33 Jy km
s [−][1] in _Yggdrasil_ (the AGN host galaxy) to the 0.54 Jy km s [−][1] in the
companion galaxy _Loke_ which is detected in both CO(1-0) and CO(87) and implies an inferred mass of _𝑀_ H 2 _,_ CO ∼ 1 _._ 4 × 10 [10] M ⊙ . Such a
mass, however, is less likely to be a proper constraint than an upper
limit as the CO line emission at _Yggdrasil_ will likely have a higher
excitation level due to the presence of the AGN than that seen at the
position of _Loke_ . Our _𝑀_ H 2 _,_ [CI] = (4 _._ 9 ± 2 _._ 7) × 10 [9] M ⊙ is therefore
consistent with these previously reported CO observations. Similarly,
at the host galaxy of TN J0121+1320, the CO(4-3) line flux of 1.2
Jy km s [−][1] from De Breuck et al. (2003) leads to an inferred mass of
_𝑀_ H 2 _,_ CO(4−3) ∼ 7 _._ 0×10 [10] M ⊙, when we assume a CO(4-3)/CO(1-0)
ratio of 0.5 and an _𝛼_ CO = 0 _._ 8 M ⊙ /(K km s [−][1] pc [2] ). This is a factor
of ∼ 3 larger than the [C i] inferred mass of M H 2 _,_ [C i] = (2 _._ 60 ±
1 _._ 46) × 10 [10] M ⊙ . The caveat here is that the CO(4-3) observations
from De Breuck et al. (2003) were obtained over a synthesised beam
of 8 [′′] ×4 [′′] and may therefore include multiple components that are
not included in the [C i] spectrum extracted over the 1 [′′] diameter
aperture, in our results. As expected, the [C i] and CO gas estimates
do not lead to equivalent results due to the assumptions on _𝛼_ CO



and X [C i] and Q 10 _,_ which are more appropriate for populations of
galaxies, but have large uncertainties for individual galaxies. If the
the CO-inferred H 2 mass were to be made equivalent to that of [C i],
we would require a [C i] flux density of _𝑆_ dV [C i] ≥ 264 mJy km s [−][1]

which is inconsistent with the observations presented in this work.
We conclude that the uncertainties on the H 2 masses derived from
the high- _𝐽_ CO lines are too high to provide a detailed prediction
for the detectability of [C i]. We have, however, with the current
depth reached corresponding H 2 masses lower than those previously
reported in HzRGs (e.g. Papadopoulos et al. 2000; De Breuck et al.
2003, 2005; Ivison et al. 2008; Emonts et al. 2014, 2015; Gullberg
et al. 2016b). With sufficiently longer integration times on these
sources, targeting the [C i] line with an interferometer such as ALMA,
there is a probability for detection in the sources where we have
derived upper limits.


**5.3** **Star-formation efficiency**


The star-formation efficiency (SFE) is defined as SFE = SFR/M gas,
where _𝑀_ gas should include all gas phases (H i, H ii, H 2 ). In HzRGs,
the H 2 component was often assumed to be the dominant one (e.g.
De Breuck et al. 2003), though in some cases the neutral H i gas
causing the Ly _𝛼_ can reach masses of order 10 [10] M ⊙ (Gullberg et al.
2016b; Kolwa et al. 2019; Falkendal et al. 2019). Using the lower _𝐻_ 2
masses when concentrating on the AGN host galaxies only from our
ALMA [C i] data, we now compare HzRGs with other high redshift
galaxies in terms of SFE and gas fraction _𝑓_ gas = _𝑀_ gas /( _𝑀_ gas + _𝑀_ _★_ ).
For our HzRG sample, we use the molecular gas mass (or their
limits) as derived from the [C i](1-0) emission. Due to the lack of
systematic measurements, we neglect the H i component, which may
lead to an under-estimate of _𝑀_ gas by a factor up to two. We then use
the SFRs from Falkendal et al. (2019) to derive the SFE. To calculate
the _𝑓_ gas, we consider the radio galaxies’ stellar masses from Seymour
et al. (2007) and De Breuck et al. (2010), where the upper limits of
4C+03.24 (= USS1243+036) and 4C+19.71 (= MG2144+1928) are

considered detections because their observed _𝐾_ −band detections are

fully consistent with the _Spitzer_ 3.6 and 4.5 _𝜇_ m photometry. We
enumerate our HzRGs in Fig. 4 from (6) to (10) where (6) MRC
0943-242, (7) TN J0121+1320, (8) 4C+03.24, (9) 4C+19.71 and (10)

TN J1338-1942. Note TN J0205+2242 is not included as both SFR

and M H 2 are upper limits, while 4C+04.11 does not have an estimate
of the stellar mass. Furthermore, we provide the gas fractions and


MNRAS **000**, 1–16 (2022)

12 _S. Kolwa et al._


**Table** **5.** The gas fractions ( _𝑓_ gas ) and star-formation efficiencies (SFE) of
the high- _𝑧_ radio galaxies where the _𝑓_ gas and SFE can be shown as either a
limit or a constrained value. The host galaxy 4C04.11 does not have a wellconstrained _𝑀_ ∗ and it is, therefore, not shown.


Galaxy (Fig. 4 ID) _𝑓_ gas SFE
(Gyr [−][1] )


MRC 0943-242 (6) 0 _._ 03 ± 0 _._ 02 8 _._ 38 [+] − [8] 7 _[.]_ _._ [22] 09
TN J0121+1320 (7) 0 _._ 20 ± 0 _._ 11 24 _._ 1 [+] − [16] 17 _[.]_ _._ [5] 0
4C+03.24 (8) _>_ 0.03 21.7
4C+19.71 (9) _>_ 0.16 3.30
TN J1338-1942 (10) _<_ 0.09 _>_ 42.6


star-forming efficiency in Table 5 for galaxies within our sample
where these values are either limits or constraints.

We also include SFE and _𝑓_ gas for HzRGs from the literature and
number them (1) to (5). These sources are (1) PKS 0529-549 at
_𝑧_ ≃ 2 _._ 6 from Man et al. (2019) who use [C i] to trace H 2 ; (2) 4C41.17
at _𝑧_ ≃ 3 _._ 8 from De Breuck et al. (2005) who use CO(4-3); (3) MRC
0152-209 at _𝑧_ ≃ 1 _._ 9 from Emonts et al. (2015) who use CO(1-0);
(4) MRC 1138-262 at _𝑧_ ≃ 2 _._ 2 from Gullberg et al. (2016b) who use

[C i](2-1); and (5) 4C60.07 at _𝑧_ ≃ 3 _._ 8 from Greve et al. (2004), who
use CO(1-0). Fig. 4 also includes a sample of a _Herschel_ -detected,
lensed SFGs (lSFGs) based on their magnification-corrected SFR and
_𝑀_ _★_ measures (Sharon et al. 2013; Bothwell et al. 2013b; DessaugesZavadsky et al. 2015; Nayyeri et al. 2017). In the figure, we have also
included six compact SFGs (cSFGs) (Tadaki et al. 2015; Spilker et al.
2016; Popping et al. 2017; Tadaki et al. 2017; Barro et al. 2017). A
sample of normal SFGs have been adapted from Tadaki et al. (2015)
and are shown in the figure as well.
In Fig. 4, we compare the HzRG sample with high-redshift
compact, normal and lensed star-forming galaxies as well as submillimeter galaxies. To derive SFE and _𝑓_ gas, various tracers and
methods have been used. The star-forming galaxies (SFGs) from
Daddi et al. (2010) reside within clusters at _𝑧_ ∼ 1 _._ 4 − 1 _._ 6 and have
molecular masses derived from CO(2-1). In Noble et al. (2017), SFGs
at _𝑧_ ∼ 1 _._ 6 have H 2 gas masses derived from CO(2-1). In Hayashi et al.
(2018), cluster-centric SFGs at _𝑧_ ∼ 1 _._ 46 have molecular gas masses
derived from CO(2-1). The sub-millimeter galaxies (SMGs) in the
diagram have molecular gas masses inferred from CO line emission
in several transitions from _𝐽_ up = 2 − 7 (Bothwell et al. 2013a). Additionally, the lensed SFGs, compact SFGs and SFGs from Fig. 1 are
included in the plot where the gas fractions are derived from [C i],
CO or the dust continuum.

From the SFE- _𝑓_ gas plot (Fig. 4), we find that HzRGs have generally lower _𝑓_ gas and higher SFE than SFGs and SMGs. The HzRGs
with constrained _𝑓_ gas and SFE occupy have SFE ≳ 10 Gyr [−][1] and
_𝑓_ gas ≲ 0 _._ 3. SFGs with _𝑀_ _★_ ≳ 10 [11] M ⊙ close to those of HzRGs also
occupy this high SFE, low _𝑓_ gas region. This result agrees well with
observations of galaxies at _𝑧_ ≃ 2 − 4 where high mass galaxies tend
to have lower molecular gas abundances than their low stellar mass
counterparts of stellar mass below 10 [11] M ⊙ as displayed in Figs 5
and 6 of Tacconi et al. (2018). It is also consistent with the observation that AGN galaxies appear to have lower CO(3-2) gas masses
than non-active galaxies (Circosta et al. 2021).


**5.4** **Why molecular gas may be undetected within the ISM of**
**radio galaxies at high-** _𝑧_


Fig. 4 demonstrates that high- _𝑧_ radio galaxies in this work and others
tend to have significantly lower molecular gas fractions than SMGs


MNRAS **000**, 1–16 (2022)



**Figure** **4.** Star-formation efficiency as a function of molecular gas fraction.
The HzRGs from our sample (magenta) and from the literature (orange) are
numbered as described in the text. We compare our sub-sample of HzRGs
with star-forming galaxies at _𝑧_ ∼ 1 _._ 4 (H18; Hayashi et al. 2018), at _𝑧_ ∼ 1 _._ 6
(N17; Noble et al. 2017), at _𝑧_ ∼ 1 _._ 4 − 1 _._ 6 (D10; Daddi et al. 2010) as well as a
_𝑧_ ∼ 1 _._ 2−4 _._ 1 sub-mm galaxy population (B13a; Bothwell et al. 2013a), lensed
SFGs (lSFGs - navy blue), compact SFGs (cSFGS - blue) and SFGs (faint
blue), see referenced in the text. HzRGs from the literature are numbered as
(1) PKS 0529-549 at _𝑧_ ≃ 2 _._ 6 (Man et al. 2019); (2) 4C41.17 at _𝑧_ ≃ 3 _._ 8 (De
Breuck et al. 2005); (3) MRC 0152-209 at _𝑧_ ≃ 1 _._ 9 from (Emonts et al. 2015);
(4) MRC 1138-262 at _𝑧_ ≃ 2 _._ 2 (Gullberg et al. 2016b); and (5) 4C60.07 at
_𝑧_ ≃ 3 _._ 8 (Greve et al. 2004). The hatched symbols represent galaxies in each
sample with stellar masses of _𝑀_ _★_ ≳ 10 [11] M ⊙ _._ The grey box represents the
high SFE and low _𝑓_ gas region adopted in previous studies (e.g Man et al.
2019). Details on the tracers used to obtain _𝑓_ gas are provided in the text. The
HzRG uncertainties for sources (6) and (8) are propagated from errors in SFR
errors based on the work of (Drouart et al. 2014) and Falkendal et al. (2019),
_𝑀_ _★_ errors from De Breuck et al. (2010) and _𝑀_ H 2 errors reported in Table 3.


and SFGs. Furthermore, [C i] line emission, a molecular gas tracer,
in 4/7 of the galaxies sampled in our work have 2 − 3 _𝜎_ detections
while in 3/7 galaxies, [C i] emission is too faint to be detected in
our ∼45 minute integration times. Additionally, the sampled galaxies
devoid of [C i] emission do not have previous CO detections either
leading us to conclude that molecular gas is almost or fully depleted
within the ISM of the radio-loud AGN host galaxies. In the sections
that follow, we briefly discuss the physical mechanisms that would
lead to such observations.


_5.4.1_ _High-𝑧_ _radio galaxies in a low star-formation rate phase?_


Tentative evidence for a decline in SFR for HzRGs at 1 _._ 3 _<_ _𝑧<_ 4 _._ 0

has been provided (Falkendal et al. 2019). In this study, 25 HzRGs
are shown against the Main Sequence (M.S.) of star-forming galaxies from Schreiber et al. (2015) and Santini et al. (2017). We have
provided a similar plot in Fig. 1 showing the Main Sequence from
Schreiber et al. (2015). In Fig. 1, a reasonable majority of the HzRGs
sampled sit within 0.3 dex region of scatter around the MS average.
Generally, sources located a factor of 10 below the Main Sequence
are considered to be in a low star-forming phase (Rodighiero et al.

2011). Furthermore, two of the sampled galaxies (TN J0121+1320
and TN J1338-1942) are vertically offset by ∼0.15 dex above the
MS while three (MRC 0943-242, 4C+03.24, 4C+19.71) are located
∼0.15 dex below it. TN J0205+2242 has a SFR upper limit of _<_ 84
M ⊙ yr [−][1] such that even if it were to eventually receive a constrained
measure of SFR, this would be low enough to be place it significantly
below the MS average. Due to 4C+04.11 not having a constrained
SFR, we have no indication for its position in the MS diagram. Overall, we find that radio galaxies at 1 _._ 3 _<_ _𝑧<_ 4 _._ 5 are more likely to
exist in a predominantly low star-formation rate phase in their evolution where they may lack sufficient molecular gas to continue fuelling
star-formation in the ISM at the SFR predicted by the Main Sequence
when a constant SFR is assumed from the Kennicutt-Schmidt law

(Kennicutt 1998).
A previous epoch of violent and rapid star-formation may have
removed the supply of molecular gas (e.g. Scholtz et al. 2023), leaving
only trace amounts, explaining the faint line emission in [C i] and
CO observed within the host galaxies. This idea is supported by
the [C i] line-widths in our sample which are predominantly narrow
(FWHM = 40 − 200 km s [−][1] ) with the exception of TN J0121+1320
which has a line-width of ∼600 km s [−][1] which is uncharacteristic of

galaxies undergoing major starbursts.


_5.4.2_ _AGN feedback effects on cold gas_


The molecular gas available to fuel star-formation could also have
been displaced from the ISM, dissociated or heated as radio jets
propagate through the gas medium (McNamara & Nulsen 2012;
Fabian 2012). Previous studies have provided sufficient evidence for
mechanical feedback occurring in radio AGN host galaxies (VillarMartín et al. 1999; Best et al. 2005; Merloni & Heinz 2007; Nesvadba
et al. 2008; Rosario et al. 2010; McNamara & Nulsen 2012; Hardcastle et al. 2012; Ishibashi et al. 2014; Williams & Röttgering 2015;
Mahony et al. 2016; Nesvadba et al. 2017; Santoro et al. 2020). The
notion that radio jets from the AGN cause cold gas removal has also
been examined by theoretical predictions. Cosmological simulations
of AGN feedback have demonstrated that galaxies within the stellar mass range _𝑀_ _★_ ≃ 10 [10] − 10 [11] M ⊙ undergo a higher level of
quenching than their low mass counterparts (Weinberger et al. 2017;
Nelson et al. 2019). In the case of radio AGN specifically, the kinetic
feedback may be associated with powerful jets (Davé et al. 2020;
Hardcastle & Croston 2020; Thomas et al. 2020).
A causal link between starbursts in radio galaxies and gas-rich
mergers has been suggested before (Ivison et al. 2012). In these
sources, which are also luminous in the far-infrared, turbulence in the
cold gas is induced by an energy injection from either X-ray radiation
or mechanical feedback (or both) which result in the subsequent, slow
termination of star-formation within the ISM (Papadopoulos et al.
2008, 2012). This result is similar to the merger-associated starbursts
intheSpiderweb galaxy,a _𝑧_ = 2 _._ 2 radio-loudAGN,whereinturbulent
gas dynamics have been traced via broad [C i] line emission of width
FWHM ≃ 1100 km s [−][1] _._

It is possible that cold molecular gas has been removed from the
galaxy ISM via negative kinetic AGN feedback events within our
sample. The gas would be entrained by propagating radio jets and
accelerated out of the ISM resulting in the decline in cold molecular
gas abundance that would ordinarily be traced via [C i] or CO line
emission. We can briefly approximate the kinetic energy injection
produced by radio jets relativistic speeds 𝑣/c ∼ 0 _._ 1 _._ The kinetic
jet powers typically measured for radio-loud AGN are within the
range _𝑃_ jet ≃ 10 [46] − 10 [48] erg s [−][1] (Carvalho & O’Dea 2002; Bicknell
et al. 2003). Detailed calculations have already demonstrated that



_Faint carbon emission in high-𝑧_ _radio galaxies_ 13


such relativistic jets produce sufficient power to produce outflows of
molecular gas from the ISM of radio galaxies (Nesvadba et al. 2010,
2021).
As stated in Section 2, our sample comprises jetted radio AGN
host galaxies where the kinetic mode of feedback is likely to operate
(Heckman & Best 2014). Given the results from Falkendal et al.
(2019), there is clear supporting evidence that a considerable number
of HzRGs have low star-formation rates compared to common SFGs
and that AGN feedback is responsible for removing molecular gas
and shutting off the star formation. Hence, given the high jet powers,
relatively low SFR, low gas fractions and high SFE’s observed in
our sample, mechanical AGN feedback is a possible cause for the
removal of molecular gas from the ISM of the radio-loud AGN host
galaxies in our sample.
In summary, due to the observed faintness of the molecular gas as
traced via [C i] in the AGN host galaxies galaxies with high stellar masses and powerful radio jets, we tentatively conclude that
AGN feedback may be the cause for the low molecular gas fractions. However, we can not rule out an earlier starburst as the cause
of the depletion. Without a well constrained star-formation history of
radio-AGN out to their first formation redshifts, we are limited from
making strictly conclusive statements.


**6** **CONCLUSIONS**


We have presented ALMA bands 3 and 4 observations of [C i] [3] _𝑃_ 1
→ [3] _𝑃_ 0 for seven radio galaxies (radio-loud AGN hosts) at redshifts
_𝑧_ = 2 _._ 9 − 4 _._ 5 with the goal of tracing molecular hydrogen via neutral
carbon emission. Knowing the locations of the host galaxies, we
searched for [C i] emission at the prescribed co-ordinates.
In our sample, four galaxies are detected with 2 − 3 _𝜎_ level [C i]
line emission. The remaining three galaxies are reported as nondetections with [C i] flux densities given as 5 _𝜎_ upper limits. [C i]
line widths within three out the seven sources in the sample range
from ∼ 40−180 km s [−][1] indicative of emission from bright molecular
gas clouds within the ISM. In one of the galaxies, TN J0121+1320
(SFR ≃ 626 M ⊙ yr [−][1] .), a [C i] line-width of ∼600 km s [−][1] is measured and is indicative of cold gas that is rotationally supported.
Overall, we have obtained [C i] flux densities that provide molecular
gas mass inferences where the upper limits are _𝑀_ H 2 _<_ 0 _._ 65 × 10 [10]

and the constraints are in the range, _𝑀_ H 2 _,_ [CI] ≲ (0 _._ 5 − 3) × 10 [10]

M ⊙ _._
We compare the star-formation efficiencies (SFE) and molecular
gas fractions ( _𝑓_ gas ) of our sample to other high- _𝑧_ radio galaxy populations as well as star-forming and sub-mm galaxies (SFGs and SMGs)
at _𝑧_ ≃ 2 _._ Generally, we find that high- _𝑧_ radio galaxies have _𝑓_ gas _<_ 0 _._ 2
and relatively high SFE’s of 4 − 45 Gyr [−][1] _._ Furthermore, three galaxies in our sample (TN J0121+1320, 4C+03.24, and 4C+19.72) have
gas fractions below 10%.
Based on these results, we consider two physical mechanisms
that may explain the faintness of the [C i](1-0) emission within our
sample. The first being that the galaxies have experienced vigorous
starburst activity at early epochs in their evolution which has caused
a period of star-formation quiescence where molecular gas mass
is close to depletion and cannot be traced by either [C i] or CO.
This would be followed by a second mechanism – the kinetic-mode
of feedback that operates in jetted and high- _𝑧_ radio-loud AGN host
galaxies, such as the sources in our high- _𝑧_ radio galaxy sample which
would eject a significant amount of cold gas from the ISM of the
galaxies resulting in the faintness of [C i] and CO line tracers. While
such outflows have been observed in the ionized gas of a sample of


MNRAS **000**, 1–16 (2022)

14 _S. Kolwa et al._


∼50 HzRGs (Nesvadba et al. 2017), it is unclear if similar outflows
are found in the cold molecular gas. Our current data is too shallow
to allow for a proper conclusion on which mechanism is primarily
responsible for the low molecular gas fractions we have observed in
our sample of radio galaxies.
In future, we aim to conduct a follow-up study of the cold gas
within the extended haloes of this sample as well as other _𝑧>_ 2 radio
galaxies that ties in a greater focus on the mm/sub-mm continuum
as well as the tracers of ionised gas observed within the optical
window of MUSE. Generally, the warm hot ionised component of
the circumgalactic halo gas contributes a higher proportion of a
galaxies’ baryon budget (see Tumlinson et al. (2017)) in the CGM
than cold gas which remains rather elusive in high-redshift galaxies
at _𝑧>_ 2 as has been demonstrated by this study. Hence, a greater
focus should be placed on investigating the warm and hot ionised gas
within the baryonic haloes of jetted radio-AGN host galaxies.


**ACKNOWLEDGEMENTS**


SK acknowledges the financial grants of the National Research Foundation (NRF) and the South African Radio Astronomy Observatory (SARAO; www.sarao.ac.za) whose contribution towards this
research is hereby acknowledged (2020). The Inter-University Institute for Data Intensive Astronomy (IDiA; www.idia.ac.za) is thanked
for their provision of computing resources utilised in this project
(2020-). SK thanks Federico Lelli and Helmut Dannerbauer for providing clarifying remarks on early drafts. Thanks to Ryan Trainor
for essential feedback on later versions of this paper. A tremendous
thanks to the expert on all things related to carbon in galaxies, Padelis
Papadopoulos, who provided invaluable feedback on many iterations
of this paper throughout the grueling editing phase.
This paper made use of calibrated measurement sets provided by the
European ALMA Regional Centre network (Hatziminiaoglou et al.
2015) through the calMS service (Petry et al. 2020).
AWSM acknowledges the support of the Natural Sciences and Engineering Research Council of Canada (NSERC) and the Dunlap
Fellowship at the Dunlap Institute for Astronomy & Astrophysics,
funded through an endowment established by the David Dunlap family and the University of Toronto.
CMH acknowledges funding from a United Kingdom Research and
Innovation grant (code: MR/V022830/1). For the purpose of open
access, the authors have applied a Creative Commons Attribution
(CC-BY) license to any author accepted version arising.
This paper is based on observations collected at the European
Southern Observatory under ESO programmes 097.B-0323(B),
097.B-0323(C), 096.B-0752(A), 096.B-0752(B), 096.B-0752(C)
and 096.B-0752(F).
This paper also makes use of the following ALMA observations:
ADS/JAO.ALMA#2015.1.00530.S. ALMA is a partnership of ESO
(representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO, AUI/NRAO and
NAOJ.


**DATA AVAILABILITY**


The raw Atacama Large Millimeter/submillimeter Array (ALMA)
data underlying this article are available in the _ALMA Science Portal_
at `[https://almascience.eso.org/](https://almascience.eso.org/)`, and can be accessed with


MNRAS **000**, 1–16 (2022)



the project ID: `2015.1.00530.S` . The Multi-unit Spectroscopic Explorer (MUSE) data are available in the _ESO Science Archive Facility_
at `[http://archive.eso.org/cms.html](http://archive.eso.org/cms.html)` . The processed MUSE
data will be shared on reasonable request to the corresponding author. The _Hubble_ _Space_ _Telescope_ (HST) data are available in the
_Hubble Legacy Archive_ at `[https://hla.stsci.edu/](https://hla.stsci.edu/)` . The _Spitzer_
Space Telescope (SST) data are available on the _SHzRGs Archive_ at
`[http://www.eso.org/~cdebreuc/shzrg/](http://www.eso.org/~cdebreuc/shzrg/)` . The Karl G. Jansky
Very Large Array (VLA) data is available from the VLA Legacy
Data Archive at `[https://data.nrao.edu/portal/](https://data.nrao.edu/portal/)` .


**REFERENCES**


[Alaghband-Zadeh S., et al., 2013, MNRAS, 435, 1493](http://dx.doi.org/10.1093/mnras/stt1390)
Andreani P., Retana-Montenegro E., Zhang Z.-Y., Papadopoulos P., Yang C.,
[Vegetti S., 2018, A&A, 615, A142](http://dx.doi.org/10.1051/0004-6361/201732560)
Arrigoni Battaia F., Prochaska J. X., Hennawi J. F., Obreja A., Buck T.,
[Cantalupo S., Dutton A. A., Macciò A. V., 2018, MNRAS, 473, 3907](http://dx.doi.org/10.1093/mnras/stx2465)
Arrigoni Battaia F., Hennawi J. F., Prochaska J. X., Oñorbe J., Farina E. P.,
[Cantalupo S., Lusso E., 2019, MNRAS, 482, 3162](http://dx.doi.org/10.1093/mnras/sty2827)
[Asayama S., et al., 2014, PASJ, 66, 57](http://dx.doi.org/10.1093/pasj/psu026)
[Barro G., et al., 2017, ApJ, 851, L40](http://dx.doi.org/10.3847/2041-8213/aa9f0d)
Best P. N., Kauffmann G., Heckman T. M., Brinchmann J., Charlot S., Ivezić
[Ž., White S. D. M., 2005, MNRAS, 362, 25](http://dx.doi.org/10.1111/j.1365-2966.2005.09192.x)
Bicknell G. V., Saxton C. J., Sutherland R. S., Midgley S., Wagner S. J., 2003,

[New Astron. Rev., 47, 537](http://dx.doi.org/10.1016/S1387-6473(03)00089-7)
Bielby R., Crighton N. H. M., Fumagalli M., Morris S. L., Stott J. P., Tejos
[N., Cantalupo S., 2017, MNRAS, 468, 1373](http://dx.doi.org/10.1093/mnras/stx528)
[Bisbas T. G., Papadopoulos P. P., Viti S., 2015, ApJ, 803, 37](http://dx.doi.org/10.1088/0004-637X/803/1/37)
Bisbas T. G., van Dishoeck E. F., Papadopoulos P. P., Szűcs L., Bialy S.,
[Zhang Z.-Y., 2017, ApJ, 839, 90](http://dx.doi.org/10.3847/1538-4357/aa696d)
[Borisova E., et al., 2016, ApJ, 831, 39](http://dx.doi.org/10.3847/0004-637X/831/1/39)
[Bothwell M. S., et al., 2013a, MNRAS, 429, 3047](http://dx.doi.org/10.1093/mnras/sts562)
[Bothwell M. S., et al., 2013b, ApJ, 779, 67](http://dx.doi.org/10.1088/0004-637X/779/1/67)
[Bothwell M. S., et al., 2017, MNRAS, 466, 2825](http://dx.doi.org/10.1093/mnras/stw3270)
Bradford C. M., Nikola T., Stacey G. J., Bolatto A. D., Jackson J. M., Savage
[M. L., Davidson J. A., Higdon S. J., 2003, ApJ, 586, 891](http://dx.doi.org/10.1086/367854)
Carilli C. L., Röttgering H. J. A., van Ojik R., Miley G. K., van Breugel
[W. J. M., 1997, ApJS, 109, 1](http://dx.doi.org/10.1086/312973)
[Carvalho J. C., O’Dea C. P., 2002, ApJS, 141, 371](http://dx.doi.org/10.1086/340646)
[Circosta C., et al., 2021, A&A, 646, A96](http://dx.doi.org/10.1051/0004-6361/202039270)
Couto G. S., Storchi-Bergmann T., Siemiginowska A., Riffel R. A., Morganti
[R., 2020, MNRAS, 497, 5103](http://dx.doi.org/10.1093/mnras/staa2268)
[Daddi E., et al., 2010, ApJ, 713, 686](http://dx.doi.org/10.1088/0004-637X/713/1/686)
Davé R., Crain R. A., Stevens A. R. H., Narayanan D., Saintonge A., Catinella
[B., Cortese L., 2020, MNRAS, 497, 146](http://dx.doi.org/10.1093/mnras/staa1894)

[De Breuck C., et al., 2001, AJ, 121, 1241](http://dx.doi.org/10.1086/319392)
[De Breuck C., Neri R., Omont A., 2003, New Astronomy Reviews, 47, 285](http://dx.doi.org/10.1016/S1387-6473(03)00040-X)
De Breuck C., Downes D., Neri R., van Breugel W., Reuland M., Omont A.,
[Ivison R., 2005, A&A, 430, L1](http://dx.doi.org/10.1051/0004-6361:200400115)
[De Breuck C., et al., 2010, ApJ, 725, 36](http://dx.doi.org/10.1088/0004-637X/725/1/36)
[De Breuck C., et al., 2014, A&A, 565, A59](http://dx.doi.org/10.1051/0004-6361/201323331)
[Dessauges-Zavadsky M., et al., 2015, A&A, 577, A50](http://dx.doi.org/10.1051/0004-6361/201424661)
[Drouart G., et al., 2014, A&A, 566, A53](http://dx.doi.org/10.1051/0004-6361/201323310)
Drouart G., Rocca-Volmerange B., De Breuck C., Fioc M., Lehnert M., Sey[mour N., Stern D., Vernet J., 2016, A&A, 593, A109](http://dx.doi.org/10.1051/0004-6361/201526880)

[Drouart G., et al., 2020, Publ. Astron. Soc. Australia, 37, e026](http://dx.doi.org/10.1017/pasa.2020.6)
Dunne L., Maddox S. J., Papadopoulos P. P., Ivison R. J., Gomez H. L., 2022,
[arXiv e-prints, p. arXiv:2208.01622](https://ui.adsabs.harvard.edu/abs/2022arXiv220801622D)
[Dutta R., et al., 2020, MNRAS, 499, 5022](http://dx.doi.org/10.1093/mnras/staa3147)

[Elbaz D., et al., 2007, A&A, 468, 33](http://dx.doi.org/10.1051/0004-6361:20077525)

[Emonts B. H. C., et al., 2014, MNRAS, 438, 2898](http://dx.doi.org/10.1093/mnras/stt2398)

[Emonts B. H. C., et al., 2015, MNRAS, 451, 1025](http://dx.doi.org/10.1093/mnras/stv930)

[Emonts B. H. C., et al., 2018, MNRAS, 477, L60](http://dx.doi.org/10.1093/mnrasl/sly034)

[Fabian A. C., 2012, ARA&A, 50, 455](http://dx.doi.org/10.1146/annurev-astro-081811-125521)

[Falkendal T., et al., 2019, A&A, 621, A27](http://dx.doi.org/10.1051/0004-6361/201732485)

[Falkendal T., Lehnert M. D., Vernet J., De Breuck C., Wang W., 2021, A&A,](http://dx.doi.org/10.1051/0004-6361/201935237)

[645, A120](https://ui.adsabs.harvard.edu/abs/2021A&A...645A.120F)

[Fossati M., et al., 2021, MNRAS, 503, 3044](http://dx.doi.org/10.1093/mnras/stab660)
Ginolfi M., Maiolino R., Carniani S., Arrigoni Battaia F., Cantalupo S.,
[Schneider R., 2018, MNRAS, 476, 2421](http://dx.doi.org/10.1093/mnras/sty364)
[Greve T. R., Ivison R. J., Papadopoulos P. P., 2004, A&A, 419, 99](http://dx.doi.org/10.1051/0004-6361:20035788)
[Gullberg B., et al., 2016a, A&A, 586, A124](http://dx.doi.org/10.1051/0004-6361/201526858)
[Gullberg B., et al., 2016b, A&A, 591, A73](http://dx.doi.org/10.1051/0004-6361/201527647)
[Hanuschik R. W., 2003, A&A, 407, 1157](http://dx.doi.org/10.1051/0004-6361:20030885)

[Hardcastle M. J., Croston J. H., 2020, New Astron. Rev., 88, 101539](http://dx.doi.org/10.1016/j.newar.2020.101539)

[Hardcastle M. J., et al., 2012, MNRAS, 424, 1774](http://dx.doi.org/10.1111/j.1365-2966.2012.21247.x)
[Hayashi M., et al., 2018, ApJ, 856, 118](http://dx.doi.org/10.3847/1538-4357/aab3e7)
[Heckman T. M., Best P. N., 2014, ARA&A, 52, 589](http://dx.doi.org/10.1146/annurev-astro-081913-035722)
Huang et al., 2023, in prep.
Humphrey A., Villar-Martín M., Fosbury R., Binette L., Vernet J., De Breuck
[C., di Serego Alighieri S., 2007, MNRAS, 375, 705](http://dx.doi.org/10.1111/j.1365-2966.2006.11344.x)
Ishibashi W., Auger M. W., Zhang D., Fabian A. C., 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stu1236) [443,](https://ui.adsabs.harvard.edu/abs/2014MNRAS.443.1339I)

[1339](https://ui.adsabs.harvard.edu/abs/2014MNRAS.443.1339I)

[Ivison R. J., et al., 2008, MNRAS, 390, 1117](http://dx.doi.org/10.1111/j.1365-2966.2008.13811.x)

[Ivison R. J., et al., 2012, MNRAS, 425, 1320](http://dx.doi.org/10.1111/j.1365-2966.2012.21544.x)
[Kennicutt Robert C. J., 1998, ApJ, 498, 541](http://dx.doi.org/10.1086/305588)
Kerr A. R., Pan S.-K., Claude S. M. X., Dindo P., Lichtenberger A. W., Effland
J. E., Lauria E. F., 2014, IEEE Transactions on Terahertz Science and
[Technology, 4, 201](http://dx.doi.org/10.1109/TTHZ.2014.2302537)
[Kolwa S., et al., 2019, A&A, 625, A102](http://dx.doi.org/10.1051/0004-6361/201935437)
Large M. I., Mills B. Y., Little A. G., Crawford D. F., Sutton J. M., 1981,

[MNRAS, 194, 693](http://dx.doi.org/10.1093/mnras/194.3.693)

Lelli F., De Breuck C., Falkendal T., Fraternali F., Man A. W. S., Nesvadba

[N. P. H., Lehnert M. D., 2018, MNRAS, 479, 5440](http://dx.doi.org/10.1093/mnras/sty1795)
Lelli F., Di Teodoro E. M., Fraternali F., Man A. W. S., Zhang Z.-Y., De
[Breuck C., Davis T. A., Maiolino R., 2021, Science, 371, 713](http://dx.doi.org/10.1126/science.abc1893)
Mahony E. K., Morganti R., Emonts B. H. C., Oosterloo T. A., Tadhunter C.,
[2013, MNRAS, 435, L58](http://dx.doi.org/10.1093/mnrasl/slt094)
Mahony E. K., Oonk J. B. R., Morganti R., Tadhunter C., Bessiere P., Short
[P., Emonts B. H. C., Oosterloo T. A., 2016, MNRAS, 455, 2453](http://dx.doi.org/10.1093/mnras/stv2456)

Man A. W. S., Lehnert M. D., Vernet J. D. R., De Breuck C., Falkendal T.,

[2019, A&A, 624, A81](http://dx.doi.org/10.1051/0004-6361/201834542)
[McCarthy P. J., 1993, ARA&A, 31, 639](http://dx.doi.org/10.1146/annurev.aa.31.090193.003231)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
[McNamara B. R., Nulsen P. E. J., 2012, New Journal of Physics, 14, 055023](http://dx.doi.org/10.1088/1367-2630/14/5/055023)
McNamara B. R., Russell H. R., Nulsen P. E. J., Hogan M. T., Fabian A. C.,
[Pulido F., Edge A. C., 2016, ApJ, 830, 79](http://dx.doi.org/10.3847/0004-637X/830/2/79)
[Merloni A., Heinz S., 2007, MNRAS, 381, 589](http://dx.doi.org/10.1111/j.1365-2966.2007.12253.x)

[Miller L., Peacock J. A., Mead A. R. G., 1990, MNRAS, 244, 207](https://ui.adsabs.harvard.edu/abs/1990MNRAS.244..207M)
[Molyneux S. J., Harrison C. M., Jarvis M. E., 2019, A&A, 631, A132](http://dx.doi.org/10.1051/0004-6361/201936408)
[Morais S. G., et al., 2017, MNRAS, 465, 2698](http://dx.doi.org/10.1093/mnras/stw2926)
[Morganti R., Oosterloo T., 2018, A&ARv, 26, 4](http://dx.doi.org/10.1007/s00159-018-0109-x)
[Nayyeri H., et al., 2017, ApJ, 844, 82](http://dx.doi.org/10.3847/1538-4357/aa7aa0)
[Nelson D., et al., 2019, MNRAS, 490, 3234](http://dx.doi.org/10.1093/mnras/stz2306)

Nesvadba N. P. H., Lehnert M. D., Eisenhauer F., Gilbert A., Tecza M., Abuter
[R., 2006, ApJ, 650, 693](http://dx.doi.org/10.1086/507266)
Nesvadba N. P. H., Lehnert M. D., De Breuck C., Gilbert A., van Breugel W.,
[2007, A&A, 475, 145](http://dx.doi.org/10.1051/0004-6361:20078175)
Nesvadba N. P. H., Lehnert M. D., De Breuck C., Gilbert A. M., van Breugel
[W., 2008, A&A, 491, 407](http://dx.doi.org/10.1051/0004-6361:200810346)

[Nesvadba N. P. H., et al., 2010, A&A, 521, A65](http://dx.doi.org/10.1051/0004-6361/200913333)
Nesvadba N. P. H., Drouart G., De Breuck C., Best P., Seymour N., Vernet J.,
[2017, A&A, 600, A121](http://dx.doi.org/10.1051/0004-6361/201629357)
Nesvadba N. P. H., Cañameras R., Kneissl R., Koenig S., Yang C., Le Floc’h
[E., Omont A., Scott D., 2019, A&A, 624, A23](http://dx.doi.org/10.1051/0004-6361/201833777)
[Nesvadba N. P. H., Bicknell G. V., Mukherjee D., Wagner A. Y., 2020, A&A,](http://dx.doi.org/10.1051/0004-6361/202038269)

[639, L13](https://ui.adsabs.harvard.edu/abs/2020A&A...639L..13N)

[Nesvadba N. P. H., et al., 2021, A&A, 654, A8](http://dx.doi.org/10.1051/0004-6361/202140544)
[Noble A. G., et al., 2017, ApJ, 842, L21](http://dx.doi.org/10.3847/2041-8213/aa77f3)
[Noeske K. G., et al., 2007, ApJ, 660, L43](http://dx.doi.org/10.1086/517926)



_Faint carbon emission in high-𝑧_ _radio galaxies_ 15


[Papadopoulos P. P., Greve T. R., 2004, ApJ, 615, L29](http://dx.doi.org/10.1086/426059)
Papadopoulos P. P., Thi W.-F., 2013, in Torres D. F., Reimer O., eds, Vol. 34,
Cosmic Rays in Star-Forming Environments. p. 41 ( `[arXiv:1207.2048](http://arxiv.org/abs/1207.2048)` ),
[doi:10.1007/978-3-642-35410-6_5](http://dx.doi.org/10.1007/978-3-642-35410-6_5)

Papadopoulos P. P., Röttgering H. J. A., van der Werf P. P., Guilloteau S.,
[Omont A., van Breugel W. J. M., Tilanus R. P. J., 2000, ApJ, 528, 626](http://dx.doi.org/10.1086/308215)
[Papadopoulos P. P., Thi W. F., Viti S., 2004, MNRAS, 351, 147](http://dx.doi.org/10.1111/j.1365-2966.2004.07762.x)
[Papadopoulos P. P., Kovacs A., Evans A. S., Barthel P., 2008, A&A, 491, 483](http://dx.doi.org/10.1051/0004-6361:200810513)
Papadopoulos P. P., van der Werf P. P., Xilouris E. M., Isaak K. G., Gao Y.,
[Mühle S., 2012, MNRAS, 426, 2601](http://dx.doi.org/10.1111/j.1365-2966.2012.21001.x)

[Papadopoulos P. P., Bisbas T. G., Zhang Z.-Y., 2018, MNRAS, 478, 1716](http://dx.doi.org/10.1093/mnras/sty1077)
Pentericci L., Roettgering H. J. A., Miley G. K., Carilli C. L., McCarthy P.,
[1997, A&A, 326, 580](https://ui.adsabs.harvard.edu/abs/1997A&A...326..580P)

Pentericci L., Van Reeven W., Carilli C. L., Röttgering H. J. A., Miley G. K.,
[2000, A&AS, 145, 121](http://dx.doi.org/10.1051/aas:2000104)

[Péroux C., et al., 2017, MNRAS, 464, 2053](http://dx.doi.org/10.1093/mnras/stw2444)

[Pilkington J. D. H., Scott J. F., 1965, Mem. RAS, 69, 183](https://ui.adsabs.harvard.edu/abs/1965MmRAS..69..183P)
[Planck Collaboration et al., 2016, A&A, 594, A13](http://dx.doi.org/10.1051/0004-6361/201525830)

[Popping G., et al., 2017, A&A, 602, A11](http://dx.doi.org/10.1051/0004-6361/201730391)
[Reuland M., et al., 2003, ApJ, 592, 755](http://dx.doi.org/10.1086/375619)
Riffel R. A., Riffel R., Bianchin M., Storchi-Bergmann T., Souza-Oliveira
[G. L., Zakamska N. L., 2023, MNRAS, 521, 3260](http://dx.doi.org/10.1093/mnras/stad776)

[Rodighiero G., et al., 2011, ApJ, 739, L40](http://dx.doi.org/10.1088/2041-8205/739/2/L40)
Roettgering H. J. A., van Ojik R., Miley G. K., Chambers K. C., van Breugel
[W. J. M., de Koff S., 1997, A&A, 326, 505](https://ui.adsabs.harvard.edu/abs/1997A&A...326..505R)

Rosario D. J., Shields G. A., Taylor G. B., Salviand er S., Smith K. L., 2010,

[ApJ, 716, 131](http://dx.doi.org/10.1088/0004-637X/716/1/131)
[Santini P., et al., 2017, ApJ, 847, 76](http://dx.doi.org/10.3847/1538-4357/aa8874)
Santoro F., Tadhunter C., Baron D., Morganti R., Holt J., 2020, arXiv e-prints,

[p. arXiv:2009.11175](https://ui.adsabs.harvard.edu/abs/2020arXiv200911175S)
[Saxena A., et al., 2018, MNRAS, 480, 2733](http://dx.doi.org/10.1093/mnras/sty1996)

[Scholtz J., Maiolino R., Jones G. C., Carniani S., 2023, MNRAS, 519, 5246](http://dx.doi.org/10.1093/mnras/stac3787)

[Schreiber C., et al., 2015, A&A, 575, A74](http://dx.doi.org/10.1051/0004-6361/201425017)

[Seymour N., et al., 2007, ApJS, 171, 353](http://dx.doi.org/10.1086/517887)
[Seymour N., et al., 2012, ApJ, 755, 146](http://dx.doi.org/10.1088/0004-637X/755/2/146)
[Sharon C. E., Baker A. J., Harris A. I., Thomson A. P., 2013, ApJ, 765, 6](http://dx.doi.org/10.1088/0004-637X/765/1/6)
[Silva M., et al., 2018, MNRAS, 474, 3649](http://dx.doi.org/10.1093/mnras/stx3019)

[Solomon P. M., Downes D., Radford S. J. E., 1992, ApJ, 398, L29](http://dx.doi.org/10.1086/186569)
[Soto K. T., Lilly S. J., Bacon R., Richard J., Conseil S., 2016, MNRAS, 458,](http://dx.doi.org/10.1093/mnras/stw474)

[3210](http://adsabs.harvard.edu/abs/2016MNRAS.458.3210S)

Spilker J. S., Bezanson R., Marrone D. P., Weiner B. J., Whitaker K. E.,
[Williams C. C., 2016, ApJ, 832, 19](http://dx.doi.org/10.3847/0004-637X/832/1/19)
Steidel C. C., Erb D. K., Shapley A. E., Pettini M., Reddy N., Bogosavljević
[M., Rudie G. C., Rakic O., 2010, ApJ, 717, 289](http://dx.doi.org/10.1088/0004-637X/717/1/289)
Swinbank A. M., et al., 2015, Monthly Notices of [the](http://dx.doi.org/10.1093/mnras/stv366) Royal Astronomical
[Society, 449, 1298](http://dx.doi.org/10.1093/mnras/stv366)
[Tacconi L. J., et al., 2018, ApJ, 853, 179](http://dx.doi.org/10.3847/1538-4357/aaa4b4)
[Tadaki K.-i., et al., 2015, ApJ, 811, L3](http://dx.doi.org/10.1088/2041-8205/811/1/L3)
[Tadaki K.-i., et al., 2017, ApJ, 841, L25](http://dx.doi.org/10.3847/2041-8213/aa7338)
Thomas N., Dave R., Jarvis M. J., Angles-Alcazar D., 2020, arXiv e-prints,

[p. arXiv:2010.11225](https://ui.adsabs.harvard.edu/abs/2020arXiv201011225T)
[Tumlinson J., Peeples M. S., Werk J. K., 2017, ARA&A, 55, 389](http://dx.doi.org/10.1146/annurev-astro-091916-055240)
[Valentino F., et al., 2018, ApJ, 869, 27](http://dx.doi.org/10.3847/1538-4357/aaeb88)
[Vernet J., et al., 2017, A&A, 602, L6](http://dx.doi.org/10.1051/0004-6361/201730865)

Villar-Martín M., Tadhunter C., Morganti R., Axon D., Koekemoer A., 1999,

[MNRAS, 307, 24](http://dx.doi.org/10.1046/j.1365-8711.1999.02603.x)

Villar-Martín M., Vernet J., di Serego Alighieri S., Fosbury R., Humphrey
[A., Pentericci L., 2003, MNRAS, 346, 273](http://dx.doi.org/10.1046/j.1365-2966.2003.07090.x)

[Villar-Martín M., 2007, New Astronomy Reviews, 51, 194](http://dx.doi.org/https://doi.org/10.1016/j.newar.2006.11.017)
[Walter F., Weiß A., Downes D., Decarli R., Henkel C., 2011, ApJ, 730, 18](http://dx.doi.org/10.1088/0004-637X/730/1/18)
Wang W., Wylezalek D., De Breuck C., Vernet J., Humphrey A., Villar Martín
[M., Lehnert M. D., Kolwa S., 2021, A&A, 654, A88](http://dx.doi.org/10.1051/0004-6361/202141558)

Wang W., Wylzalek D., Vernet J., et al., 2023, submitted
[Weilbacher P. M., et al., 2020, A&A, 641, A28](http://dx.doi.org/10.1051/0004-6361/202037855)

[Weinberger R., et al., 2017, MNRAS, 465, 3291](http://dx.doi.org/10.1093/mnras/stw2944)
[Weiß A., Downes D., Henkel C., Walter F., 2005, A&A, 429, L25](http://dx.doi.org/10.1051/0004-6361:200400085)

[Williams W. L., Röttgering H. J. A., 2015, MNRAS, 450, 1538](http://dx.doi.org/10.1093/mnras/stv692)


MNRAS **000**, 1–16 (2022)

16 _S. Kolwa et al._


van Ojik R., Roettgering H. J. A., Carilli C. L., Miley G. K., Bremer M. N.,
[Macchetto F., 1996, A&A, 313, 25](https://ui.adsabs.harvard.edu/abs/1996A&A...313...25V)


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–16 (2022)


</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "1.98 - 2.28 arcsec x 1.33 - 2.17 arcsec (see Table 1)",
  "failed_quote": "MRC 0943-242 | 04/03/2016 - 20/05/2016 45 2.09 × 1.33"
 },
 {
  "path": "data.angular_resolution.evidence[1]",
  "value": "1.98 - 2.28 arcsec x 1.33 - 2.17 arcsec (see Table 1)",
  "failed_quote": "4C+04.11 | 05/03/2016 - 03/05/2016 43 2.24 × 2.17"
 },
 {
  "path": "data.time_on_source.evidence[0]",
  "value": "38 to 45 min per target",
  "failed_quote": "MRC 0943-242 | 04/03/2016 - 20/05/2016 45 2.09 × 1.33"
 },
 {
  "path": "data.time_on_source.evidence[1]",
  "value": "38 to 45 min per target",
  "failed_quote": "4C+03.24 | 06/03/2016 38 2.23 × 1.62"
 },
 {
  "path": "data.observing_dates.evidence[0]",
  "value": "04/03/2016 to 24/09/2016",
  "failed_quote": "MRC 0943-242 | 04/03/2016 - 20/05/2016 45 2.09 × 1.33"
 },
 {
  "path": "data.observing_dates.evidence[1]",
  "value": "04/03/2016 to 24/09/2016",
  "failed_quote": "TN J0121+1320 | 06/03/2016 - 24/09/2016 40 1.98 × 1.47"
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "2.09 x 1.33 arcsec (MRC 0943-242), 2.28 x 1.81 arcsec (TN J0205+2242), 1.98 x 1.47 arcsec (TN J0121+1320), 2.23 x 1.62 arcsec (4C+03.24), 1.98 x 1.81 arcsec (4C+19.71), 1.98 x 1.61 arcsec (TN J1338-1942), 2.24 x 2.17 arcsec (4C+04.11)",
  "failed_quote": "MRC 0943-242 | 04/03/2016 - 20/05/2016 45 2.09 × 1.33"
 },
 {
  "path": "processing.imaging.final_beam.evidence[1]",
  "value": "2.09 x 1.33 arcsec (MRC 0943-242), 2.28 x 1.81 arcsec (TN J0205+2242), 1.98 x 1.47 arcsec (TN J0121+1320), 2.23 x 1.62 arcsec (4C+03.24), 1.98 x 1.81 arcsec (4C+19.71), 1.98 x 1.61 arcsec (TN J1338-1942), 2.24 x 2.17 arcsec (4C+04.11)",
  "failed_quote": "TN J0205+2242 | 08/03/2016 - 13/09/2016 44 2.28 × 1.81"
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Low S/N (2-3 sigma) of the [C I](1-0) detections leads to large redshift and line width uncertainties and prevents detailed kinematic modelling or distinguishing between starburst depletion and AGN feedback.",
  "failed_quote": "Given the low S/N of our [C i] data, the uncertainties of the [C i] redshifts are higher than on the He ii redshifts (Table 2)"
 }
]
```
