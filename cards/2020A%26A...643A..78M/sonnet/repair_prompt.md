# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...643A..78M\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. manuscript ⃝c ESO 2020
September 18, 2020

### **VALES VII: Molecular and ionized gas properties in pressure**
## balanced interstellar medium of starburst galaxies at z ∼ 0 . 15 .


Juan Molina [1][,][ 2], Edo Ibar [3], Nicolás Godoy [3][,][ 4], Andrés Escala [2], Tomonari Michiyama [1], Cheng Cheng [5][,][ 6][,][ 3], Thomas M.
Hughes [3][,][ 5][,][ 7][,][ 8], Maarten Baes [9], Yongquan Xue [7], Michał J. Michałowski [10], Paul van der Werf [11], and Xue-Jian Jiang [12]


1 Kavli Institute for Astronomy and Astrophysics, Peking University, 5 Yiheyuan Road, Haidian District, Beijing 100871, P.R. China
2 Departamento de Astronomía (DAS), Universidad de Chile, Casilla 36-D, Santiago, Chile
e-mail: `jumolina@pku.edu.cn`
3 Instituto de Física y Astronomía, Universidad de Valparaíso, Avda. Gran Bretaña 1111, Valparaíso, Chile
4 Núcleo Milenio de Formación Planetaria – NPF, Universidad de Valparaíso, Av. Gran Bretaña 1111, Valparaíso, Chile
5 Chinese Academy of Sciences South America Center for Astronomy, National Astronomical Observatories, CAS, Beijing 100101,
China.
6 CAS Key Laboratory of Optical Astronomy, National Astronomical Observatories, CAS, Beijing 100101, China.
7 CAS Key Laboratory for Research in Galaxies and Cosmology, Department of Astronomy, University of Science and Technology of
China, Hefei 230026, China
8 School of Astronomy and Space Science, University of Science and Technology of China, Hefei 230026, China
9 Sterrenkundig Observatorium, Universiteit Gent, Krijgslaan 281 S9, B-9000 Gent, Belgium
10 Astronomical Observatory Institute, Faculty of Physics, Adam Mickiewicz University, ul. Słoneczna 36, 60-286 Pozna´n, Poland
11 Leiden Observatory, Leiden University, P.O. Box 9513, NL-2300 RA Leiden, The Netherlands
12 East Asian Observatory, 660 North A’ohoku Place, Hilo, Hawaii 96720, USA


**ABSTRACT**


_Context._ Spatially resolved observations of the ionized and molecular gas are critical for understanding the physical processes that
govern the interstellar medium (ISM) in galaxies. The observation of starburst systems is also important as these present extreme gas
conditions that may help to test different ISM models. However, matched resolution imaging at ∼kpc scales for both ISM gas phases
are usually scarce and the ISM properties of starbursts still remain poorly understood.
_Aims._ We aim to study the morpho-kinematic properties of the ionized and molecular gas in three dusty starburst galaxies at _z_ =
0.12 − 0.17 to explore the relation between molecular ISM gas phase dynamics and the star-formation activity.
_Methods._ We employ two-dimensional dynamical modelling to analyse Atacama Large Millimeter/submillimiter Array (ALMA)
CO(1–0) and seeing limited Spectrograph for INtegral Field Observations in the Near Infrared (SINFONI) Paschen-α (Paα) observations tracing the molecular and ionized gas morpho-kinematics at ∼ kpc-scales. We use a dynamical mass model, which accounts for
beam-smearing effects, to constrain the CO-to-H 2 conversion factor and estimate the molecular gas mass content.
_Results._ One starburst galaxy shows irregular morphology which may indicate a major merger, while the other two systems show
disc-like morpho-kinematics. The two disc-like starbursts show molecular gas velocity dispersion values comparable with that seen
in local Luminous and Ultra Luminous Infrared Galaxies, but in an ISM with molecular gas fraction and surface density values in
the range of the estimates reported for local star-forming galaxies. We find that these molecular gas velocity dispersion values can be
explained by assuming vertical pressure equilibrium. We also find that the star-formation activity, traced by the Paα emission line, is
well correlated with the molecular gas content suggesting an enhanced star formation efficiency and depletion times of the order of
∼ 0.1 − 1 Gyr. We find that the star formation rate surface density (Σ SFR ) correlates with the ISM pressure set by self-gravity ( _P_ grav )
following a power law with an exponent close to 0.8.
_Conclusions._ In dusty disc-like starburst galaxies, our data support the scenario in which the molecular gas velocity dispersion values
are driven by the ISM pressure set by self-gravity, responsible to maintain the vertical pressure balance. The correlation between Σ SFR
and _P_ grav suggests that, in these dusty starbursts galaxies, the star formation activity arises as a consequence of the ISM pressure
balance.


**Key words.** galaxies: star formation – galaxies: starburst – ISM: kinematics and dynamics



**1.** **Introduction**


Understanding how galaxies build up their stellar mass content
within dark matter haloes is a key goal in modern extragalactic
astrophysics. One of the best constraints comes from studying
the evolution of the star formation rate density (SFRD) across
cosmic time (Madau et al. 1996; Madau & Dickinson 2014). The
overall decline of the SFRD in the last ∼10 Gyr coincides with
the decrease of the average fraction of molecular gas mass in
galaxies (Tacconi et al. 2010; Geach et al. 2012; Carilli & Wal


ter 2013). A straightforward interpretation is that the molecular
gas is the fuel that maintains the star formation activity (Bigiel
et al. 2008; Leroy et al. 2008). If the gas supply into galaxies is
continuously smooth, then the formation of stars may be driven
by internal dynamical processes within the interstellar medium
(ISM; Kereš et al. 2005; Bournaud et al. 2007; Dekel et al. 2009;
Spring & Michałowski 2017). It is therefore essential to identify
the physical processes that govern the ISM properties to tackle
galaxy evolution.


Article number, page 1 of 22

_A&A proofs:_ manuscript no. manuscript



A complete characterization of the ISM involves the understanding of many complex processes that are driven and evolve
on different spatial and time scales. ISM models often assume a
dynamic equilibrium (e.g. Thompson et al. 2005; Ostriker et al.
2010; Faucher-Giguère et al. 2013; Krumholz et al. 2018). In this
‘quasi steady-state’, the ISM gas pressure is set to maintain the
vertical pull from galaxy self-gravity. The star formation activity,
parametrized by the Kennicutt-Schmidt law (Kennicutt 1998a),
arises as a result of the pressure balance (e.g. Ostriker & Shetty
2011; Hayward & Hopkins 2017).
It is still unclear which mechanism is the main responsible
for setting the pressure support to stabilize the ISM gas against
self-gravity. One possibility is stellar feedback (e.g. Ostriker
& Shetty 2011; Kim et al. 2011). Another possibility comes
from the energy released by gravitational instabilities and mass
transport within galactic discs (Krumholz & Burkhart 2016;
Krumholz et al. 2018). Local galaxy spatially-resolved observations show trends in favour of the stellar-feedback regulated
model (Sun et al. 2020). Unresolved observations for starbursts
also agree with this model (Fisher et al. 2019). However, there
is also evidence that additional sources of energy beyond stellar feedback may help support system self-gravity (Zhou et al.
2017; Molina et al. 2019b), especially for systems with high star
formation rates (e.g. Varidel et al. 2020). Luminous and Ultra
Luminous Infrared Galaxies (LIRG/ULIRGs) seem also to be in
vertical pressure equilibrium set by the release of gravitational
energy (Wilson et al. 2019). In any case, to test the pressure
balance-based ISM models, galaxy spatially-resolved observations that trace the ISM gas phases, star-formation activity and
the stellar component are needed.
Obtaining such a dataset for large galaxy samples is generally time-consuming. While integral field unit (IFU) observations targeting the star formation activity in galaxies are common (e.g. Sánchez et al. 2012; Bryant et al. 2015), molecular gas spatially-resolved observations are relatively scarce. Observing the spatial distribution of the molecular gas content in
star-forming galaxies is still, relative to the optical/near-IR observations, highly time-consuming. This is true even for the
present times of Atacama Large Millimeter/submillimeter Array (ALMA) and the NOrthem Ex-tended Millimetre Array
(NOEMA). The hydrogen molecule (H 2 ) is not easily detectable
at low temperatures in the range of the few hundreds of Kelvin
(e.g. Papadopoulos & Seaquist 1999; Bothwell et al. 2013),
and use of molecular gas tracers, such as the carbon monoxide
molecule ( [12] C [16] O, hereafter CO) emission of rotational low− _J_
transitions (e.g. _J_ = 1 − 0), is strictly necessary to indirectly
observe this cold gaseous ISM phase (Solomon & Vanden Bout
2005; Bolatto et al. 2013).
In this work, we introduce new detailed ∼ kpc-scale morphokinematics observations toward three starburst galaxies taken
from the Valparaíso ALMA/APEX Emission Line Survey
(VALES; Villanueva et al. 2017; Cheng et al. 2018) at _z_ ∼
0.12 − 0.18. The VALES survey is designed to target low- _J_
CO emission line transitions in dusty galaxies extracted from
the _Herschel_ Astrophysical Terahertz Large Area Survey ( _H_ ATLAS; Eales et al. 2010). VALES extracts sources from the
equatorial Galaxy And Mass Assembly (GAMA) fields (Driver
et al. 2016), which present wide broad-band imaging and photometry in multiple bands sampling the galaxy Spectral Energy Distribution (SED) from far-ultraviolet (far-UV) to IR. The
VALES survey covers the redshift range of 0.02< _z_ <0.35, stellar masses ( _M_ ⋆ ) from ≈ 6 to 11 × 10 [10] _M_ ⊙ and IR-luminosity
range of _L_ 8−1000µm ≈ 10 [10][−][12] _L_ ⊙ (see Villanueva et al. 2017 for
more details).


Article number, page 2 of 22



We characterize the molecular gas morpho-kinematics by
observing the CO( _J_ = 1 − 0, ν rest = 115.271 GHz) molecule
by ALMA. These sub-mm observations are complemented by
spatially-resolved seeing-limited ionized gas phase measurements taken by the Spectrograph for INtegral Field Observations in the Near Infrared (SINFONI) IFU located at the European Southern Observatory Very Large Telescope (ESO-VLT).
The ionized gas ISM phase is traced by observing the nebular
Paschen alpha (Paα) emission line (λ rest = 1.8751 µm). Our observations are one of the few that use the CO and Paα emission
lines to study the ISM dynamics in dusty starbursts.
We assume a ΛCDM cosmology with Ω Λ = 0.73, Ω m =
0.27, and _H_ 0 =70 km s [−][1] Mpc [−][1] . Thus, at a redshift range of _z_ =
0.1 − 0.2, a spatial resolution of 0 [′′] . 6 corresponds to a physical
scale between 1.0 − 1.8 kpc.


**2.** **Observations & Data Reduction**


_2.1._ _The three targeted galaxies_


We select three galaxies taken from the VALES survey at _z_ ≈
0.12 − 0.18. These systems were selected based on their likelihood to be molecular gas-rich systems, i.e., with expected
molecular gas fractions _f_ H 2 ≡ _M_ H 2 /( _M_ H 2 + _M_ ⋆ ) - 0.3 after assuming a Milky-way like CO-to-H 2 conversion factor α CO,MW =
4.6 _M_ ⊙ (K km s [−][1] pc [2] ) [−][1] (Bolatto et al. 2013). Our ‘gas-rich’ criterion takes into account two observational facts: (1) the negligible cosmic evolution of _f_ H 2 in the redshift range _z_ = 0 − 0.2
(Villanueva et al. 2017; Tacconi et al. 2018); and (2) local galaxies have average molecular gas fractions of ∼ 0.1 (Leroy et al.
2009; Saintonge et al. 2017) with only a few of these presenting
_f_ H 2 - 0.3 (≈ 1 % based on XCOLD GASS survey _M_ H 2 measurements re-scaled by assuming α CO,MW ; Saintonge et al. 2017).
In Fig 1, we present the global properties for these three
galaxies compared to full VALES and GAMA surveys. We adopt
the star-forming galaxy (SFG) ‘main-sequence’ parametrization
suggested by Whitaker et al. (2012). The main-sequence corresponds to the tight correlation between the galaxy stellar masses
and star formation rates (SFRs). Our three targets are representative of the starburst galaxy population.
Using the Baldwin-Phillips-Terlevich (BPT) diagram (Baldwin et al. 1981), we show that two systems lie just below the
limit of the pure star-forming region (Kauffmann et al. 2003).
The remaining target (HATLAS114625−014511) is located in
the low ionization nuclear emission line region (LINER). The
Hβ, [Oiii], Hα and [Nii] flux measurements are presented in
Appendix A. By using the _Wide-field_ _Infrared_ _Survey_ _Ex-_
_plorer_ (WISE; Wright et al. 2010) mid-IR colour diagram
(right panel in Fig. 1; Stern et al. 2012; Mateos et al. 2012),
HATLAS114625−014511 would be classified as an AGN host
galaxy, while the other two targets are classified as SFGs in
agreement with the BPT-diagram analysis.


_2.2._ _ALMA observations_


In this work, we describe an ALMA follow up campaign (taken
from project 2015.1.01012.S; P.I.: E. Ibar) for imaging three
VALES galaxies for which we obtained previous bright CO(10) detections presented in Villanueva et al. (2017). Observations
were taken on Band-3 with the extended 12 m array to obtain
higher spatial and spectral resolution imaging than previous observations.
The spectral setup was designed to target the redshifted
CO(1-0) emission line (between 97 GHz and 103 GHz, depend

Juan Molina et al.: Molecular and ionized gas properties in pressure balanced ISM of starburst galaxies


Fig. 1: Characterization of the three galaxies presented in this work in terms of stellar mass, SFRs, and AGN activity. _Left:_ The
SFR- _M_ ⋆ plane. The solid and dashed lines represent the main-sequence (MS) parametrization suggested by Whitaker et al. (2012)
and the 4× SFR(MS) starburst threshold, respectively. _Middle:_ The BPT-diagram (Baldwin et al. 1981). The dashed curve shows the
empirical star-forming threshold (Kauffmann et al. 2003), whereas the solid curve corresponds to the theoretical maximum starburst
model (Kewley et al. 2001). These two lines encompass the SFGs-AGN ‘composite’ zone. The dotted-dashed line indicates the
division between AGNs and LINERs (Schawinski et al. 2007). _Right:_ WISE mid-IR colour-colour diagram. The solid lines delimit
the AGN-zone suggested by Mateos et al. (2012), whereas the dashed line represents the AGN threshold adopted by Stern et al.
(2012). The WISE data 1-σ errorbars are smaller than the plotted symbol sizes. The GAMA data are taken from their data-release
3 (GAMA-DR3; Baldry et al. 2018) encompassing galaxies at _z_ < 0.35 (the upper redshift limit for the VALES survey) and with
5-σ or higher flux estimates. These three panels indicate that the three galaxies presented in this work can be classified as starbursts,

−
with one target (HATLAS114625 014511) likely to be classified as an obscured AGN host galaxy.


Table 1: ALMA observational setup for project 2015.1.01012.S.


Source List Observation Flux Bandpass Phase P.W.V. Number of Time on θ BMAJ
Date Calibrator Calibrator Calibrator (mm) antennas Target (min) (arcsec.)
HATLASJ114625.0−014511 & 9 Aug. 2016 J1229+0203 J1229+0203 J1150−0023 0.80 36 35 0 [′′] . 52
HATLASJ121446.4−011155 11 Aug. 2016 J1229+0203 J1229+0203 J1150−0023 0.80 38 35 0 [′′] . 50
HATLASJ090750.0+010141 13 Aug. 2016 J0854+2006 J0854+2006 J0909+0121 0.63 36 35 0 [′′] . 45



ing on the source) using a spectral window in Frequency Division Mode to cover 1.875 GHz of bandwidth at a native
3906.250 kHz resolution. The other three spectral windows were
used in Time Division Mode and were positioned to measure
the continuum emission around the redshifted line. Observations
were taken under relatively good weather conditions with precipitable water vapour (P.W.V.) ranging from 0.6 mm to 0.8 mm,
and using 36 to 38 antennas with a maximum baseline of 1.5 km.
The phase, bandpass and flux calibrations are listed in Table 1.
Data reduction was carried out using the Common Astronomy Software Applications (CASA) and using the provided
ALMA pipeline up to calibrated _uv_ products. Data taken in
different days were concatenated together after running the
pipeline and before imaging. After exploring different imaging
approaches using task tclean, and guided by our scientific objectives, we decided to use a Briggs weighting (robust=0.4) to
reach a major axis full width half maximum for the synthesized
beam (θ BMAJ ) in a range between 0 [′′] . 45–0 [′′] . 52. For each source,
we apply a slight convolution (within tclean) to obtain a circular beam. The pixel size is set to 0 [′′] . 1. All three sources are
clearly detected at high significance, and the signal was interactively cleaned down to 2–3-σ in spectral channels with confident
source emission.
Final images reach r.m.s. noises of ∼ 400–500µJy beam [−][1] at
≈ 12 km s [−][1] channel width. The channel width is set to minimize spectral resolution effects (Molina et al. 2019b). The continuum emission image, obtained over 6 GHz bandwidth reaches
noise levels of 13µJy beam [−][1] . Two targets are detected as point



sources with peak flux densities of ∼ 110µJy beam [−][1], while
HATLASJ121446.4−011155 remains undetected.


_2.3._ _SINFONI observations_


We observe the Paα emission line by using the SINFONI IFU
(Eisenhauer et al. 2003) on the ESO-VLT in its seeing-limited
mode (Project 099.B-0479(A); P.I. J.Molina). The SINFONI
field-of-view (FOV) is 8 [′′] ×8 [′′] with a pixel angular size of 0 [′′] . 125.
The spectral resolution is λ/∆λ ∼ 3800, and OH sky-lines have
∼ 5 Å full width at half maximum – FWHM (≈ 30km s [−][1] at
2.1µm). The observations were carried out in service mode between 2017 March 15 and 2017 December 11 in seeing and photometric conditions (point spread function – PSF FWHM ≈ 0 [′′] . 4–
0 [′′] . 8 in _K_ -band). In addition, two different jittering patterns were
used during the observing runs in order to boost the observation
signal-to-noise ratio (S/N) in one galaxy.


2.3.1. ‘OSSO’ Jittering


To observe the HATLASJ1146251−014511 and
HATLASJ121446.4−011155 galaxies (hereafter, HATLAS114625 and HATLAS121446, respectively), we used
the traditional ABBA chop sequences, nodding 16 [′′] . 0 across
the IFU. That means that the traditional jittering OBJECTSKY-SKY-OBJECT (‘OSSO’) pattern was implemented. We
used one observing block (OB) per target, implying a total


Article number, page 3 of 22

_A&A proofs:_ manuscript no. manuscript


Table 2: Spatially-integrated measurements for the three starbursts. The far-IR luminosities are calculated across the rest-frame
8–1000 µm wavelength range. _E_ ( _B_ − _V_ ) Neb is the colour excess estimated by using the observed Hα-to-Paα flux ratio. SFR Paα
and SFR Paα,corr correspond to the observed and attenuation-corrected Paα-based SFR estimates, respectively. _S_ CO ∆ _v_ is the velocity
integrated flux density. _L_ CO [′] [is the CO(1-0) line luminosity taken from Villanueva et al. (2017).]


HATLASJ090750.0+010141 HATLASJ114625.4−014511 HATLASJ121446.0−011155
RA (J2000) 09:07:50.07 11:46:25.01 12:14:46.47
Dec (J2000) +01:01:41.47 −01:45:12.81 −01:11:55.55
_z_ spec 0.12834 0.16553 0.17981
_M_ ⋆ (× 10 [10] _M_ ⊙ ) 1.4±0.4 5.1±1.2 6.6±1.7
_L_ IR (× 10 [10] _L_ ⊙ ) 50±1 53±1 35±1
SFR IR 50±1 53±1 35±1
f Paα (× 10 [−][17] erg s [−][1] cm [−][2] ) – 1069±111 644±96
_E_ ( _B_ − _V_ ) Neb – 1.35±0.05 0.91±0.06
SFR Paα – 32±4 25±4
SFR Paα,corr – 67±8 40±6
_S_ CO ∆ _v_ (Jy km s [−][1] ) 6.8±0.6 6.6±0.6 4.6±0.6
_L_ CO [′] [(][×][ 10] [9] [ K km s] [−][1] [p][c] [2] [)] 5.4±0.5 8.6±0.8 7.3±0.9



observing time of ≈3.2 ks per source. The raw datasets for
these two sources were reduced by using the standard SINFONI
ESOREX [1] data reduction pipeline.


2.3.2. ‘OOOO’ Jittering


We perform an on-source experimental jittering pattern increase the S/N of the Paα emission line in one galaxy. In this
experimental observation, the pointing was kept fixed at the
galaxy location. Thus, an OBJECT-OBJECT-OBJECT-OBJECT
(‘OOOO’) jitter sequence was used. Based on previous analyses by Godoy et al. (in prep), this observing approach provides
reliable results for emission line with S/N≳ 15.
To reduce the data, first, we use the SINFONI esoreflex and
esorex pipelines. Then, sky emission lines are subtracted using SkyCor (Noll et al. 2014), while Molecfit (Kausch et al.
2015) is implemented to remove telluric absorption bandpass
lines (Godoy et al. in prep.). This is necessary as we do not have
‘sky’ observations.
To test this experimental jitter pattern, we choose the brightest galaxy in our small sample, HATLASJ090750.0+010141
(hereafter, HATLAS090750). By using this method, the observed emission line S/N is expected to increase by ∼ √2 com
pared to the use of an ‘OSSO’ jitter pattern due to the extra onsource time. For this observation, the exposure time was also set
to ≈ 3.2 ks. More details about this experimental observation are
reported in Appendix B.


2.3.3. Flux calibration


The standard star observation is used to perform the flux calibration. First, the galaxy spectrum is corrected in each pixel
by atmospheric telluric absorptions and by the SINFONI _K_ band transmission curve. We do this by collapsing the standard
star datacube in the spectral axis using a wavelength range free
from significant telluric absorptions. A two-dimensional Gaussian function is fitted to this spectrally-collapsed image. Then,
we extract the spectrum from the standard star by using an aperture size of 2× FWHM in diameter. We use this standard star
spectrum to normalize the galaxy spectrum observed in each
pixel. We take into account the different total exposure times.


1 http://www.eso.org/sci/software/pipelines/


Article number, page 4 of 22



Then, in each pixel, we multiply the normalized spectrum by
a representative stellar black-body profile. To obtain this blackbody curve, we fit a black-body function to the standard star
magnitudes collated in the Visual Observatory SED Analyser
(VOSA, Bayo et al. 2008). This allows us to estimate the stellar
surface temperature – thus the black-body function shape – and
the normalization constant to construct the representative standard stellar black-body profile as seen in the SINFONI _K_ -band.
We note that the typical relative uncertainty for the conversion
factor is ∼5% (e.g. Piqueras López et al. 2012).
Even though we can provide reliable flux calibrations for
HATLAS114625 and HATLAS121446, the different on-source
(’OOOO’) observing mode for HATLAS090750 impeded a
proper calibration from its standard star observation. The flux
calibration for this observation requires us to carefully model
the sky for the standard star observation and, hence the stellar
spectrum. However, we were unable to obtain an accurate stellar
atmospheric model for the standard star (HD 56006) due to its
uncertain stellar parameters. More details about these uncertainties are presented in Appendix B.


2.3.4. Spatial resolution


We also use the spectrally-collapsed standard star image to determine the PSF FWHM (θ PSF ) for each _K_ -band observation. By fitting a two-dimensional Gaussian function, we determine θ PSF ≈
0 [′′] . 62, 0 [′′] . 39 and 0 [′′] . 81 for HATLAS090750, HATLAS114625 and
HATLAS121446, respectively.


_2.4._ _Stellar Mass and IR-based SFR estimates_


The stellar masses for the three galaxies were estimated in Villanueva et al. (2017) by using the photometry provided by the
GAMA survey (extending from the far-UV to FIR – ∼ 0.1 −
500 µm) and by using the Bayesian SED fitting code magphys
(Da Cunha et al. 2008). We assume a Chabrier (2003) initial
mass function (IMF). The _M_ ⋆ values are presented in Table 2.
The IR-based SFRs (SFR FIR ) are estimated by using the restframe far-IR 8–1000 µm luminosity ( _L_ IR ) estimates taken from
Ibar et al. (2015). By assuming a Chabrier (2003) IMF, the SFR IR
values are calculated following SFR IR ( _M_ ⊙ yr [−][1] ) = 10 [−][10] × _L_ IR
( _L_ ⊙ ; Kennicutt 1998b) and correspond to the obscured starformation activity. The IR-based SFRs are consistent with the

Juan Molina et al.: Molecular and ionized gas properties in pressure balanced ISM of starburst galaxies



SFR estimates suggested by magphys but tend to be offset by a
factor of ∼ 2 toward higher values (see Villanueva et al. 2017 for
more details).


_2.5._ _CO(1-0) Luminosities_


The total galaxy CO(1-0) velocity-integrated flux densities
( _S_ CO(1−0) ∆ _v_ ) are taken from Villanueva et al. (2017). Briefly,
these were estimated by implementing a two-step procedure.
First, the CO(1-0) line is spectrally fitted by a Gaussian profile to determine its FWHM and spectrally-collapse the datacube
within ±1× FWHM. Then, _S_ CO(1−0) ∆ _v_ values are estimated by
fitting a two-dimensional Gaussian function to the spectrallyintegrated datacube (moment 0) using the task gaussfit within
casa. Finally, the CO(1-0) luminosities ( _L_ CO(1 [′] −0) [) are calculated]
by following Solomon & Vanden Bout (2005);


_L_ CO(1 [′] −0) [=][ 3][.][25] [×] [10] [7] _[ S]_ [ CO(1][−][0)] [∆] _[v]_ [ ν] obs [−][2] _[D]_ L [2] [(1] [+] _[z]_ [)] [−][3] [ [K km s] [−][1] [ pc] [2] []][,]
(1)


where _S_ CO(1−0) ∆ _v_ is in Jy km s [−][1], ν obs is the observed frequency
of the emission line in GHz, _D_ L is the luminosity distance in
Mpc, and _z_ is the redshift. Both estimates are presented in Table 2.


**3.** **ANALYSIS and RESULTS**


_3.1._ _Average ISM properties_


To analyse the spatially-integrated emission line fluxes for our
three galaxies, first, we collapse the new ALMA and SINFONI
datacubes into one-dimensional spectra (Fig 2). These spectra
were built by stacking the spectrum seen in the individual pixels from which we detected an emission line (see § 3.2). Before
stacking, we manually shifted the individual emission lines to
rest-frame accounting for redshift and the respective pixel lineof-sight (LOS) velocity value (see Fig, 3). Thus, we try to minimize any line broadening produced by rotational motions and
we focus on intrinsic individual emission line widths.
In all the three starbursts, the spatially-integrated Paα emission line seems broader than the CO(1-0) emission line. By convolving the ALMA spatially-integrated spectrum by the SINFONI line spread function (LSF; green curves in Fig. 2), we find
that the spectral resolution difference is not producing this trend.
The difference between the spatially-integrated Paα and CO(10) line widths seems to be caused by broader nuclear Paα emission lines in the individual pixels in each galaxy (see § 3.2.2).
The broad nuclear Paα emission lines indicate that the ionized
gas ISM phase is more affected by turbulent supersonic motions
than the molecular gas [2] . We do not detect any broad-line component (> 500 km s [−][1] ) in the spatially-collapsed SINFONI spectra,
suggesting the absence of signatures from a broad line region
produced by an active galactic nucleus (AGN).
We use the Paα emission line fluxes to derive SFR estimates (less affected by attenuation compared to Hα) using the
Kennicutt (1998b)’s conversion for the Chabrier (2003) IMF.
By assuming an intrinsic Hα-to-Paα ratio equal to 0.116 (Case
B recombination, Osterbrock & Ferland 2006), the Paα-based


2 4
For a typical Hii region with a temperature of 10 K, we expect a Paα
thermal broadening of ∼ 20km s [−][1] . For the molecular gas ISM phase
with a temperature of ≲ 200 K, we expect thermally-broadened CO line
widths ≲ 0.5km s [−][1] .



**0.0**


1.8720 1.8757 1.8795 1.8832 1.8870 1.8907
λ Rest−frame [µm]


Fig. 2: Spatially-integrated rest-frame spectra around the emission lines of interest. The bottom and top x-axes show the
rest-frame wavelength and frequency ranges for the Paα and
CO(1-0) emission lines, respectively. For each galaxy, the solid
green curve shows the CO(1-0) spectrum convoluted by the SINFONI LSF. From HATLAS090750, we also detect the Br δ, H 2 (10)S(3), H 2 (1-0)S(2), H 2 (1-0)S(1) and He i near-IR emission lines
using as an aperture an encircled zone given by the PSF FWHM
and centred at the Paα luminosity peak. In the case of the HATLAS114625 galaxy observation, we also detect the H 2 (1-0)S(3)
emission. These detections are shown in the sub-plots (blueshaded area) in each panel (see also Appendix C). The CO(1-0)
and Paα emission lines are clearly detected.


Article number, page 5 of 22



ν Rest−frame [GHz]
115.46 115.23 115.00 114.77 114.54 114.31













**1.0**


**0.5**


**0.0**

























1.8720 1.8757 1.8795 1.8832 1.8870 1.8907
λ Rest−frame [µm]


ν Rest−frame [GHz]
115.46 115.23 115.00 114.77 114.54 114.31









**1.0**


**0.5**


**0.0**





1.8720 1.8757 1.8795 1.8832 1.8870 1.8907
λ Rest−frame [µm]


ν Rest−frame [GHz]
115.46 115.23 115.00 114.77 114.54 114.31





**1.0**


**0.5**

_A&A proofs:_ manuscript no. manuscript



SFRs (SFR Paα ) are calculated following SFR Paα ( _M_ ⊙ yr [−][1] ) =
4.0 × 10 [−][41] × _L_ Paα (erg s [−][1] ). The SFR Paα values are presented in
Table 2. We do not present an SFR Paα estimate for the HATLAS090750 galaxy as we were unable to obtain a reliable flux
calibration for its SINFONI observation.

We compute the nebular _E_ ( _B_ − _V_ ) colour excess ( _E_ ( _B_ − _V_ ) Neb )
by using the observed Hα-to-Paα flux ratio [3] and assuming a
Calzetti et al. (2000) attenuation law. We list the _E_ ( _B_ − _V_ ) Neb values in Table 2. We note that these _E_ ( _B_ − _V_ ) Neb values are ∼ 4.7
and ∼ 2.3 times higher than the colour excess estimates given by
magphys for the stellar component ( _E_ ( _B_ − _V_ ) ⋆ ≈0.29 and ≈0.39
for HATLAS114625 and HATLAS121446, respectively). This is
expected from local galaxy studies, where the higher _E_ ( _B_ − _V_ ) Neb
values suggest a differential attenuation model in which stars experience attenuation from a diffuse ISM dust component, but the
massive young stars experience an additional attenuation as they
are embedded in their dusty birth clouds (Calzetti et al. 2000).
However, we note that the HATLAS114625’s nebular-to-stellar
colour excess ratio is twice than the average value found in local
galaxies (∼ 2.3, Calzetti et al. 2000), indicating its highly dusty
nature and more in line with the findings of an extreme obscured
starburst galaxy population at _z_ ∼ 0.5 − 0.9 (Calabrò et al. 2018).
By considering the derived _E_ ( _B_ − _V_ ) Neb values, we estimate
attenuation-corrected SFR Paα (SFR Paα,corr ) values of 67 ± 8 and
40 ± 6 _M_ ⊙ yr [−][1] for HATLAS114625 and HATLAS121446, respectively. These estimates are slightly higher than the SFR FIR
values (Table 2), but still consistent with the 2-σ uncertainties
for both starbursts.


_3.2._ _Galaxy Dynamics_


We construct the two-dimensional moment maps by following
Swinbank et al. (2012). Briefly, the spectrum associated with
each pixel corresponds to the average spectrum calculated from
the pixels inside a square area that contains the spatial resolution element – the synthesized beam or PSF. The noise per spectral channel is estimated from a region that does not contain any
source emission. We use the lmfit Python package (Newville
et al. 2014) to fit a Gaussian profile to the emission lines. In the
case of the SINFONI observations, we mask the spectrum at the
wavelength ranges where OH sky-line features are present and
the Paα line widths are corrected by spectral resolution effects.
We apply an S/N = 5 threshold to determine whether we have
detected an emission line or not. If this criterion is not achieved,
then we increase the square binned area by one pixel per side and
repeat the Gaussian fit again. We iterate up to two more times in
order to avoid large binned regions. After the third iteration, if
the S/N criterion has not been achieved, we mask that pixel and
skip to the next one.
The pixel-by-pixel intensity, velocity and velocity dispersion
1-σ uncertainties are estimated by re-sampling via Monte Carlo
simulations the flux density uncertainties in the data. The maps
from both emission lines are presented in Fig. 3.
The CO(1-0) and Paα intensity maps present smooth distributions with no clear level of clumpiness, at ∼ kpc-scales, in
the three starbursts. These also agree with the stellar morphology seen in _K_ -band image. However, we note that OH sky-line
features present in the SINFONI observations may add noise to
the Paα two-dimensional maps and this may partly explain the
smoother CO(1-0) maps as the ALMA spectra are free from skyline residuals.


3 The Hα flux estimates are taken from the GAMA survey DR3 (see
Table A.1).


Article number, page 6 of 22



Table 3: _K_ -band surface brightness Sérsic best-fit model parameters taken from the GAMA-DR3 for our sample (Kelvin et al.
2012). µ 0, _K_ is the central surface brightness value. _R_ 1/2, _K_ corresponds to the half-light radius. _n_ _S_ is the Sérsic photometric
index. PA _K_ indicates the position angle of the photometric major
axis. The ellipticity ‘ _e_ ’ is derived from the projected major-tominor axis ratio on the sky ( _e_ ≡ 1 − _b_ / _a_ ). The final column
denotes the reduced chi-square (χ [2] ν [) value of the best-fit model.]


Name µ 0, _K_ _R_ 1/2, _K_ _n_ _S_ PA _K_ _e_ χ [2] ν
(mag/arcsec [2] ) (kpc) (deg)
HATLAS090750 9.36 3.66 4.92 62.1 0.26 2.19

HATLAS114625 3.78 2.76 6.80 −82.2 0.60 1.29

HATLAS121446 15.31 2.55 1.26 −3.5 0.67 1.12


In the particular case of the HATLAS090750 system, the _K_   band and Paα intensity images show two asymmetric features
that may be related to gas inflow/outflow or tidal interaction.
These features suggest an on-going merging process. Both features account for ∼18% of the total Paα flux suggesting on-going
star formation activity. One of the asymmetric features has a projected velocity blueshift of ∼−300 km s [−][1] compared to the system centre, while the other feature presents a velocity redshift of
∼ 80 km s [−][1] suggesting that this system has a complex 3D shape.
The ALMA observation just traces the CO(1-0) emission coming
from the central part of this system, probably due to sensitivity
limitations. Interestingly, the central part of this system shows a
rotational pattern in the CO(1-0) and Paα velocity maps, with a
peak-to-peak rotational velocity of _V_ max sin( _i_ ) ∼ 90 km s [−][1] .
In contrast, HATLAS114625 and HATLAS121446 show
clear disc-like rotational patterns in their CO(1-0) and Paα velocity maps. The ionized and molecular gas kinematics broadly
agree in both starbursts with peak-to-peak rotational velocities
of _V_ max sin( _i_ ) ∼ 360 − 460 km s [−][1], respectively.


3.2.1. Kinematic Modelling


We model the ionized and molecular gas ISM kinematics by fitting the two-dimensional LOS velocity fields. The model velocity maps are constructed by assuming an input arctan rotation

curve:


_V_ ( _R_ ) = _V_ 0 + [2] (2)

π _[V]_ [asym] [ arctan(] _[R]_ [/] _[R]_ [t] [)][,]


where _R_ t is the radius at which the rotation curve turns over, _V_ 0
is the systemic velocity (i.e. redshift) and _V_ asym is the asymptotic
rotational velocity (Courteau 1997).
For each observation, the kinematic model considers seven
free parameters ( _V_ 0, _V_ asym, _R_ t, PA, [ _x_ / _y_ ], and inclination angle).
We convolve the velocity model map with the PSF or synthesized beam, and we use the emcee Python package (ForemanMackey et al. 2013) to find the best-fit model.
We use the _K_ -band Sérsic photometric models (Sérsic 1963)
to constrain the inclination angle values. We use the _K_ -band
best-fit minor-to-major axis ratio ( _b_ / _a_ ; Table 3) as initial guess
input to the kinematic modelling and we allow to search the bestfit inclination value within a 3-σ range. To better account for the
_K_ -band model _b_ / _a_ uncertainty, we adopt a _b_ / _a_ ratio 1-σ relative error equal to 10% as suggested by Epinat et al. (2012). The

Juan Molina et al.: Molecular and ionized gas properties in pressure balanced ISM of starburst galaxies














|Col1|ity|Col3|
|---|---|---|
|2 kpc|0<br>21<br>42<br>||
|2 kpc|−360 km/|−360 km/|



Fig. 3: _K_ -band, intensity, velocity, velocity dispersion and residual maps (1st to 5th columns) for HATLAS090750 ( _Top_ ), HATLAS114625 ( _Middle_ ) and HATLAS121446 ( _Bottom_ ). For each galaxy, from the 2nd column to the last column, we show the Paα
and CO(1-0) two-dimensional maps, one above the other, respectively. The spatial scale for each observation is shown in each map.
The _K_ -band map has over-plotted the CO(1-0) and Paα emissions in green and pink colour contours, respectively. The CO(1-0)
intensity map shows the synthesized beam size. In the velocity and velocity dispersion maps, the white cross indicates the location
of the best-fitted dynamical centre. The velocity maps have over-plotted the velocity contours from their best-fit disc models, and
the green- and pink-dashed lines represent the molecular and ionized gas major kinematic axes, respectively. In each velocity dispersion map, the white circumference represents the boundary of the region masked during the estimation of the global velocity
dispersion value. The residual fields are constructed by subtracting the velocity disc models from the velocity maps. The r.m.s. of
these residuals are given in each panel. In the case of HATLAS090750 Paα observation, we only show the modelled central zone in
the residual map.



inclination angle is derived from _b_ / _a_ by considering an oblate
spheroid geometry (Holmberg 1958):


0
cos [2] ( _i_ ) = [(] _[b]_ [/] _[a]_ [)] [2] [ −] [q] [2], (3)
1 − q [2] 0



where ‘ _i_ ’ is the galaxy inclination angle and q 0 is the intrinsic
minor-to-major axis ratio (i.e. disc thickness) of the galaxy. For
edge-on systems ( _i_ = 90 deg), q 0 = _b_ / _a_ . We use q 0 = 0.14 mean


Article number, page 7 of 22

_A&A proofs:_ manuscript no. manuscript


Table 4: Best-fit kinematic parameters for the galaxies in our sample. PA is the kinematic major-axis position angle. _R_ 1/2 is the
half-light radius corrected by beam smearing effects. σ _v_ is the global velocity dispersion value (see §3.2.2). _V_ rot is the rotational
velocity measured across the major kinematic axis. _i_ is the inclination angle (for a face-on galaxy, _i_ = 0 deg.). We do not give
uncertainty estimates for _i_ as it is constrained by the _K_ -band image model. The ‘CO’ and ‘Paα’ sub-indexes indicate the emission
line from which the kinematic parameters were estimated.


HATLAS090750 HATLAS114625 HATLAS121446
_i_ CO (deg) 65 70 80
PA CO (deg) −132 ± 1 −76 ± 1 −10 ± 1
_R_ 1/2,CO (kpc) 1.44 ± 0.01 2.09 ± 0.01 2.74 ± 0.01
_V_ rot,CO (km s [−][1] ) 67 ± 2 198 ± 22 245 ± 5
σ _v_,CO (km s [−][1] ) 35 ± 12 26 ± 10 34 ± 11
χ [2] ν,CO 11.2 10.4 7.0
_i_ Paα (deg) 65 70 80
PA Paα (deg) −123 ± 1 −81 ± 1 −9 ± 1
_R_ 1/2,Paα (kpc) 2.10 ± 0.05 1.72 ± 0.01 2.52 ± 0.03
_V_ rot,Paα (km s [−][1] ) 68 ± 4 190 ± 7 246 ± 9
σ _v_,Paα (km s [−][1] ) 66 ± 18 51 ± 30 51 ± 31
χ [2] ν,Paα 7.1 5.0 7.8



value reported for edge-on galaxies at low-redshift ( _z_ < 0.05,
Mosenkov et al. 2015).
The model best-fit parameters and χ [2] ν [values] [are] [given] [in]
Table 4 and the r.m.s. values are shown in each residual map
(Fig. 3). The kinematic position angles roughly agree with each
other (∆PA = PA Paα - PA CO ≲ 10 deg). For HATLAS114625 and
HATLAS121446 galaxies, these also roughly agree with the position angles derived from the _K_ -band image modelling.
The best-fit disc model gives a reasonable fit to the inner
ionized and molecular gas kinematics of the HATLAS090750
galaxy as suggested by the low reported r.m.s. value. This may
indicate a fast relaxation process of the ISM molecular gaseous
phase into a disc-like galaxy in the central zone of this system
(e.g. Kronberger et al. 2007). For the other two galaxies, the
r.m.s. values presented in the Paα velocity residual maps tend to
be larger than the values derived from the CO(1-0) observations,
suggesting that the ionized gas ISM phase may be a more sensitive tracer of non-circular motions compared to the molecular
gas ISM phase. However, these high r.m.s values also are a consequence of the coarser SINFONI spectral resolution compared
to the ALMA observations plus additional noise induced by the
OH sky-line features present in some pixels at the wavelengths
where the Paα emission line is found.


3.2.2. Kinematic Parameters


We use the best-fit dynamical models to simulate a slit observation along the major kinematic axis and we extract the onedimensional rotation velocity and velocity dispersion curves for
both ISM phases (Fig. 4). We consider a slit width equal to the
synthesized beam or PSF FWHM. The half-light radii for the
ionized and molecular gas ISM phases ( _R_ 1/2,Paα, _R_ 1/2,CO ) are calculated by using a tilted ring approach. From the rotation curve,
we define the rotational velocity for the Paα and CO observations
( _V_ rot,Paα, _V_ rot,CO ) as the inclination corrected values observed at
two times the Paα and CO half-light radii, respectively.
To correct the velocity dispersion values for beam-smearing
effects, we apply the correction suggested by Stott et al. (2016).
This corresponds to a linear subtraction of the local velocity gradient ∆ _V_ /∆ _R_ from the beam-smeared line widths. However, to
further consider beam-smearing residual effects from this correction, we define the global velocity dispersion for each gas phase


Article number, page 8 of 22



(σ _v_,CO, σ _v_,Paα ) as the median value taken from the pixels located
beyond three times the synthesized beam or PSF FWHM from
the dynamical centre (white circumferences in velocity dispersion maps in Fig. 3).
For HATLAS090750, we find a very compact CO light
distribution as suggested by its half-light radius. In its central zone, this system shows a low rotational velocity value
( _V_ rot,CO ∼ 70 km s [−][1] ) and a high median velocity dispersion
σ _v_,CO ∼ 35 km s [−][1], suggesting a molecular gas ISM phase with
highly supersonic turbulent motions and a CO-traced kinematic
ratio _V_ rot,CO /σ _v_,CO ∼ 2. The CO- and Paα-based rotation curves
clearly agree at the radius at which CO(1-0) is detected (Fig 4),
implying that the _V_ rot,CO and _V_ rot,Paα values also agree.
In contrast, the Paα emission tends to show broader line
widths compared to the CO emission line (σ _v_,Paα ∼ 66 km s [−][1] ).
This is unlikely to be produced by beam-smeared flux coming
from the asymmetric features as the broader Paα line widths are
seen across all the major kinematic axis. Assuming that the line
widths trace the turbulent kinematic state of the respective ISM
gas phase, this result suggests that the molecular gas phase may
be able to dissipate the turbulent kinetic energy faster than the
ionized gas phase. Another possibility could be an additional energy injection in the ionized gas from stellar feedback such as
stellar winds, supernovae feedback and/or Wolf-Rayet episodes
(e.g. Thornton et al. 1998; Crowther 2007; Kim & Ostriker 2015;
Martizzi et al. 2015; Kim et al. 2017). The expansion of overpressured Hii regions is also a possibility (Elmegreen & Scalo
2004). We remind that we have corrected the SINFONI observations by instrumental line broadening effects.
For HATLAS114625 and HATLAS121446, the molecular and ionized gas ISM phases show similar scale sizes
_R_ 1/2,Paα / _R_ 1/2,CO ≈ 0.85 ± 0.01 and 0.96 ± 0.01, respectively. For
HATLAS121446, these half-light radii estimates also agree with
_R_ 1/2, _K_ (see Table 3). However, for HATLAS114625, we find that
_R_ 1/2, _K_ / _R_ 1/2,CO/Paα ≈ 1.3 − 1.6 kpc, suggesting that the ionized
and molecular gas ISM phases are distributed in a more compact
disc-like structure in this galaxy.
For both starbursts, the velocity curves agree and we derive
ionized to molecular gas rotation velocity ratios _V_ rot,Paα / _V_ rot,CO ≈
1.04 ± 0.04 and 0.94 ± 0.14, for HATLAS121446 and HATLAS114625, respectively. The consistency between the CO- and
Hα-based velocity curves tend to be found in local galaxies

Juan Molina et al.: Molecular and ionized gas properties in pressure balanced ISM of starburst galaxies



**100**





|Paα<br>CO(1 0)<br>−|Col2|
|---|---|
|||
|||


−4 −2 0 2 4
Radius [kpc]



**50**


**0**


**−50**


**−100**

**−4** **−2** **0** **2** **4**

Radius [kpc]



120


100


80


60


40


20


250


200


150


100


50





200


100


0


−100


−200





−6 −4 −2 0 2 4 6
Radius [kpc]



−6 −4 −2 0 2 4 6
Radius [kpc]



300


200


100


0


−100


−200


−300





200


150


100


50




|Paα<br>CO(1 0)<br>−|Col2|
|---|---|
|||



−6 −4 −2 0 2 4 6
Radius [kpc]



−6 −4 −2 0 2 4 6
Radius [kpc]



Fig. 4: Rotation velocity ( _Left_ ) and velocity dispersion ( _Right_ )
profiles across the major kinematic axis for HATLAS090750
( _Top_ ), HATLAS114625 ( _Middle_ ) and HATLAS121446 ( _Bottom_ )
galaxies. The error bars show the 1-σ uncertainties. The vertical black-dashed line represents the best-fit dynamical centre.
The light grey shaded area represents the 3× synthesized beam
size region centred at the best-fit molecular gas dynamical centre, whereas the dark grey dashed area represents the 3× PSF
FWHM zone centred at the best-fit ionized gas dynamical centre. In the rotation velocity profile panels, the dashed-magenta
and solid-green curves show the rotation curves extracted from
the beam-smeared Paα and CO(1-0) two-dimensional best-fit
models, respectively. In the velocity dispersion profile panels,
the green- and magenta-dashed lines show the median galactic
value estimated from the outskirts of the galactic disc (Table 4)
for the CO(1-0) and Paα observations, respectively. We find a
good agreement between the rotation curves derived from the
ionized and molecular gas ISM phases in the three starbursts.


where the ionized gas emission seems to come from recent star
formation activity episodes (Levy et al. 2018).
In both systems, the median σ _v_,CO values are lower than the
corresponding σ _v_,Paα estimates (σ _v_,Paα /σ _v_,CO ∼ 1.5−2), however,
those still agree within 1-σ uncertainties. The CO and Paα ve


locity dispersion values seen in both galaxies suggest a dominant
common nature. The CO and Paα velocity dispersion profiles
(Fig. 4) suggests even closer σ _v_,Paα and σ _v_,CO values. Nevertheless, we note that our measured σ _v_,CO values tend to be higher
than the estimates reported from local systems (≈ 9 − 19 km s [−][1],
Levy et al. 2018). Indeed, these median σ _v_,CO values are consistent with the lower end of the velocity dispersion estimates
measured from ULIRGs (∼ 30–140 km s [−][1], Downes & Solomon
1998; Wilson et al. 2019).
We derive an average CO-based rotational velocity to dispersion velocity ratio ( _V_ rot,CO /σ _v_,CO ) of 8 ± 3 and 7 ± 2 for
HATLAS114625 and HATLAS121446, respectively. If we consider the Paα observations, we derive _V_ rot,Paα /σ _v_,Paα ∼ 4 ± 2 and
∼ 5 ± 3, respectively. Independent of the emission line considered, the _V_ rot /σ _v_ ratios measured for HATLAS114625 and HATLAS121446 suggest that the rotational motions are the main support against self-gravity in both starburst galaxies.


3.2.3. Comparison with previous VALES works


Using our kpc-scale resolution data (∼ 0 [′′] . 5), we try to test if
the previous kinematic analysis done for the VALES galaxies
(Molina et al. 2019b) may be biased due to beam-smearing effects. These previous CO(1-0) observations were performed by
using a more compact ALMA array configuration, thereby delivering a coarser spatial resolution (∼ 3 − 4” ≈ 5 − 7 kpc).
Beam-smearing could hide galaxy morpho-kinematic properties,
making it hard to recover unbiased intrinsic parameters when the
spatial resolution is of the order of several kpc.
Even though the galaxies presented in this work, HATLAS114625 and HATLAS121446, were not described in Molina
et al. (2019b) as they were not extended enough for a dynamical interpretation, we can still make a brief comparison with the
VALES systems that share similar global properties.
We concentrate in VALES sources with similar specific
SFR values (sSFR≡SFR/ _M_ ⋆ ; ∆ log(sSFR) < 0.3 dex) than the
estimated for HATLAS114625 and HATLAS121446 (sSFR =
10–100 Gyr, respectively). For these sources, we find that the
kinematic maps present marginally resolved rotation ( _V_ rot,CO ≈
40 − 200km s [−][1] ) and high velocity dispersion values (σ _v_,CO ≈
40−70 km s [−][1] ), implying _V_ rot,CO /σ _v_,CO ratios in the range of 1−3.
These values are lower than the ones presented in this work, suggesting that the kinematic parameters presented in Molina et al.
(2019b) might be systematically biased due to beam smearing.
This comparison is not straightforward as the resolution presented in this work is five to seven times higher than in Molina
et al. (2019b), however, it highlights the importance of highresolution imaging for extracting more precise dynamical information.


_3.3._ _The CO-to-H_ 2 _conversion factor from dynamics_


A CO-to-H 2 conversion factor must be used to estimate molecular gas masses from the CO luminosities ( _M_ H 2 = α CO _L_ CO [′] [,]
e.g. Bolatto et al. 2013). Traditionally, two different α CO values have been considered to calculate _M_ H 2 for galaxies as
a whole (Solomon & Vanden Bout 2005). An α CO,MW ≈
4.6 _M_ ⊙ (K km s [−][1] pc [2] ) [−][1] value seems to be more appropriate
for disc-like galaxies (e.g. Solomon et al. 1987), whereas an
α CO,ULIRG ≈ 0.8 _M_ ⊙ (K km s [−][1] pc [2] ) [−][1] value has been estimated
for ULIRGs and assumed to be representative for merger-like
systems (e.g. Downes & Solomon 1998). However, it is unlikely that α CO follows a bi-modal distribution. Models suggest


Article number, page 9 of 22

_A&A proofs:_ manuscript no. manuscript



a smooth transition that depends on the ISM physical properties
(e.g. Narayanan et al. 2012).

We exploit the dynamical mass estimate [ _M_ dyn ( _R_ ) = _V_ circ [2] _G_ _[R]_ []]

to constrain the α CO value. In this procedure, we assume that the
dynamical mass estimate corresponds to the sum of the stellar,
molecular and dark matter masses (e.g. Motta et al. 2018; Molina
et al. 2019a). This is true when looking at the central regions of
galaxies. The Hi component at larger scales dominates the gas
mass, while the ionized gas might have a role as well. Additionally, for the sake of simplicity, we also assume a constant α CO
value across each galactic disc. Therefore, by quantifying the
dark matter content in terms of the dark matter fraction ( _f_ DM ) at
each galactocentric radius, we obtain the following constraint;


CO [(] _[R]_ [)]
_f_ DM ( _R_ ) = 1 − _[M]_ [⋆] [(] _[R]_ [)][ +][ α] [CO] _[L]_ [′], (4)
_M_ dyn ( _R_ )


where the CO luminosities inside each radius are calculated
directly from the ALMA observations and the stellar masses
are truncated using the _K_ -band Sérsic model profile following
Molina et al. (2019a).
To estimate the dynamical mass values and use Eq. 4, first
we need to calculate the circular velocity _V_ circ at each galactocentric radius. To do this, we consider two cases, the thin- and
thick-disc hydrostatic equilibrium approximations. In the first
case, the galaxy support against self-gravity is assumed to be
purely rotational and _V_ circ corresponds to the observed rotational
velocity ( _V_ circ = _V_ rot,CO, Genzel et al. 2015). In the second case,
the galaxy scale height can not be neglected, and the self-gravity
is balanced by the joint support between the rotational motions
and the pressure gradient across the galactic disc (Burkert et al.
2010).
In this ‘thick-disc’ approximation, an analytic expression for
_V_ circ can be derived by parametrizing the pressure gradients in
terms of σ _v_ (which is assumed to be constant across the galactic
height and radius) and the mass distribution, which we assume to
follow the best-fit Sérsic model of the _K_ -band surface brightness
distribution;



Table 5: CO-to-H 2 conversion factor, molecular gas masses and
gas fractions for HATLAS114625 and HATLAS121446 starbursts


HATLAS114625 HATLAS121446


α CO _M_ ⊙ (K km s [−][1] pc [2] ) [−][1] 0.7 − [+] 0 [0] . [.] 3 [5] 1.2 [+] − [1] 0 [.] . [0] 6
_M_ H 2 (× 10 [9] _M_ ⊙ ) 6.0 [+] − [4] 2 [.] . [3] 6 10.3 − [+] 5 [8] . [.] 3 [7]
_f_ H 2 0.11 [+] − [0] 0 [.] . [07] 05 0.14 [+] − [0] 0 [.] . [10] 07


We estimate the posterior probability density function (PDF) for
the CO-to-H 2 conversion factor and the dark matter fraction parameters by sampling the α CO – _f_ DM ( _R_ ) phase-space defined in
Eq. 4 and by considering the likelihood of the estimated _L_ CO [′] [,]
_M_ dyn and _M_ ⋆ values.
Additional to the thin- and thick-disc dynamical model assumptions, we explore the effect of the chosen underlying mass
distribution by assuming that the galaxies follow an exponential
total-mass surface density distribution (Freeman 1970). We note
that this assumption produces a variation in our thick-disc _M_ dyn
and truncated _M_ ⋆ estimates. Thus, we employ a total of four different dynamical models per galaxy.
We do not derive an α CO value for the HATLAS090750 system as this on-going merger may not fulfil the virial assumption
necessary to obtain a dynamical mass estimate.
In Fig 5 we show the α CO posterior PDFs for HATLAS114750 and HATLAS121664 starbursts. We note that the
thick-disc Sérsic mass-profile model suggests slightly higher
α CO values than the other three models for both galaxies. This
is produced by two effects; (1) the additional pressure gradient
support against self-gravity, which is low for our galaxies as suggested by the _V_ rot,CO /σ _v_,CO ∼ 7 ratios; and (2) surface density
profiles steeper than the ones derived from an exponential model
profile as indicated by the Sérsic indexes _n_ _S_ ≳ 1. This tends
to increase the _M_ dyn values by a larger amount compared to the
truncated _M_ ⋆ values at smaller galactocentric radii.
We note that a possible systematic overestimation of _M_ ⋆
by magphys may bias the α CO estimates toward lower values
than the reported ones. This scenario is unlikely as we have
input a large wavelength SED coverage (∼ 0.1 − 500 µm) to
obtain accurate _M_ ⋆ values (see also Michałowski et al. 2014).
However, to be conservative, we assume α CO upper limit values
(α CO,uplim ) given by the PDFs 3-σ range. We obtain α CO,uplim =
2.7 and 5.1 _M_ ⊙ (K km s [−][1] pc [2] ) [−][1] for HATLAS114625 and HATLAS121446, respectively.
In the remaining of this work, we estimate the molecular
gas masses by adopting the median CO-to-H 2 conversion factor
value derived from the thick-disc Sérsic mass-profile dynamical
model, i.e., by considering the model that suggests the higher
median α CO value. This election does not affect our results as
the differences between the four dynamical models are marginal
compared to the uncertainties behind the galaxy estimates as
seen by the broad α CO PDFs. Our analysis suggests low α CO
values that are consistent with the ULIRG-like value for both
starbursts. We present this value along with the molecular gas
estimates in Table 5.

A direct result of adopting that α CO value is that our early
expectation about observing ‘gas-rich’ systems was wrong. Indeed, the measured _f_ H 2 values are consistent with the average
estimate for local star-forming galaxies ( _f_ H 2 ∼ 0.1, Leroy et al.
2009; Saintonge et al. 2017). This suggests that these starburst



_V_ circ [2] [(] _[R]_ [)][ =] _[ V]_ rot [2],CO [(] _[R]_ [)][ +][ 2] [σ] _n_ _v_ [2] _[b]_ _S_ _[n]_ _S_



_R_
� _R_ 1/2, _K_



(1/ _n_ _s_ )
, (5)
�



where, _V_ rot,CO ( _R_ ) is the rotation velocity profile (Fig. 4), _b_ _n_ _S_ is
the Sérsic coefficient that sets _R_ 1/2, _K_ as the _K_ -band half-light radius (e.g. Burkert et al. 2016; Lang et al. 2017; Molina et al.
2019b).
The disc radial coordinates are determined by the bestfit two-dimensional model. Additionally, to minimize beamsmearing effects, we only consider the _V_ rot,CO values extracted
from a zone beyond three times the synthesized beam FWHM
from the dynamical centre (see ‘σ _v_ ’ panels in Fig. 3). However,
as we still expect some residual beam-smearing effect at these
radii, we also apply a correction factor (≲ 10 %) to the rotation velocity values based on the ratio between the intrinsic-tosmoothed best-fit arctan velocity models across the galaxy major
kinematic axis (Appendix D).
We note that this method suffers from a degeneracy between
the α CO and _f_ DM ( _R_ ) parameters, along with it there is a strong
dependence on the accuracy of the _M_ dyn and _M_ ⋆ values. To try
to overcome these issues, we use a Markov Chain Monte Carlo
(MCMC) technique (Calistro Rivera et al. 2018; Molina et al.
2019b) implemented in emcee (Foreman-Mackey et al. 2013).


Article number, page 10 of 22

Juan Molina et al.: Molecular and ionized gas properties in pressure balanced ISM of starburst galaxies



**1.0**


**0.8**


**0.6**


**0.4**


**0.2**


**0.0**













**1.0**


**0.8**


**0.6**


**0.4**


**0.2**


**0.0**





**0.5** **1.0** **1.5** **2.0** **2.5** **3.0**
**α** **CO** **[ M** **O** **•** **[pc]** **[-2]** **[ (K km s]** **[-1]** **[)]** **[-1]** **[]]**



**1** **2** **3** **4** **5** **6**
**α** **CO** **[ M** **O** **•** **[pc]** **[-2]** **[ (K km s]** **[-1]** **[)]** **[-1]** **[]]**



Fig. 5: Posterior α CO PDFs for HATLAS114625 ( _Left_ ) and HATLAS121446 ( _Right_ ) starbursts. For each galaxy, we consider
four dynamical mass models encompassing different underlying surface density mass distributions and hydrostatic equilibrium
approximations. We also show the cumulative probability distribution in each panel with our α CO upper limit defined as _P_ ( _x_ <
α CO,uplim ) ≈ 0.997 (i.e. 3-σ) and estimated by using the ‘thick-disc + Sérsic’ dynamical mass model. The coloured arrows indicate
the median α CO value for each PDF. We find median α CO estimates consistent with the ULIRG-like value for both starburst galaxies.



galaxies may not be ‘gas-rich’ as originally expected, implying
that without a robust molecular gas estimate, it is not straightforward to catalogue these systems as possible analogues of the
high- _z_ SFG population.


**4.** **Discussion**



The upward pressure is parametrized as a function of the average mid-plane density ρ mid and the thermal plus turbulent velocity dispersions;



_4.1._ _What sets the molecular gas velocity dispersions?_


HATLAS114625 and HATLAS121446 present σ _v_,CO values
that are comparable with the lower end estimates observed in
ULIRGs (σ _v_,CO ≈30–140 km s [−][1], Downes & Solomon 1998;
Wilson et al. 2019). However, both galaxies show regular disclike kinematics with little evidence of interactions that may enhance the internal σ _v_,CO values, suggesting that the high molecular gas velocity dispersion values may be produced by internal
secular processes.
Wilson et al. (2019) found that, in ULIRGs, the σ _v_,CO values roughly increase with the molecular surface density (Σ H 2 ),
following a power-law relationship with a tentative exponent of
∼ 0.5. Wilson et al. (2019) suggested that this correlation can
be explained if ULIRGs are in vertical pressure balance. In this
section, we explore if their model is able to explain the σ _v_,CO
values measured for the HATLAS114625 and HATLAS121446
galaxies. We choose Wilson et al. (2019)’s ISM pressure balance model because we lack of stellar velocity dispersion measurement for our sources. This quantity is required to calculate
the pressure set by self-gravity in other ISM models such as, for
example, in the traditional Elmegreen (1989)’s ISM model.
In Wilson et al. (2019)’s model, a downward pressure on the
molecular gas (modelled as a gas layer) is produced by the disc
self-gravity, plus an additional contribution from the dark matter
halo. This pressure can be calculated as;



Σ H 2 σ [2] _v_,H 2 [(1][ +][ ψ][)]
_P_ ISM = ρ mid σ [2] _v_,H 2 [(1][ +][ ψ][)][ =], (7)

2 _h_ H 2


where ρ mid = Σ H 2 /2 _h_ H 2, _h_ H 2 is the molecular gas disc scale
height, σ _v_,H 2 is the molecular gas velocity dispersion (hereafter
we assume σ _v_,H 2 ≈ σ _v_,CO ) and ψ is a factor which accounts principally for the magnetic-to-thermal support ratio (∼ 0.3, Kim
& Ostriker 2015) as the cosmic ray to turbulent support ratio is
negligible (see Wilson et al. 2019, for more details).
The vertical equilibrium condition requires _P_ grav,W+19 =
_P_ ISM and allows us to write the Wilson et al. (2019)’s Eq. 6 in a
more compact form;



_h_ H 2 = πσ _G_ [2] _v_ Σ,COTot × � 11 + + γψ



. (8)
�



_P_ grav,W+19 = 0.5π _G_ Σ H 2 Σ Tot (1 + γ), (6)


where Σ Tot is the disc total mass surface density and γ is a factor that accounts for the vertical pull toward the galaxy midplane produced by dark matter. This factor depends inversely on
_V_ rot /σ _v_ squared, thus, it contributes a small correction for both
galaxies (γ ∼ 0.05).



From this equation, if galaxies have similar Σ H 2 /Σ Tot ratio, then
σ _v_,CO ∝ Σ [0] H [.] 2 [5] [, and] _[ h]_ [H] [2] [is constant across the galactic radius, i.e.,]
the correlation found by Wilson et al. (2019) for local ULIRGs.
In the left panel of Fig. 6, we plot the pixel-by-pixel σ _v_,CO
values as a function of Σ H 2 (corrected by projection effects) for
HATLAS114625 and HATLAS121446. All the values associated with the pixels that reside inside the central galactic region [4]
are shown in grey colour, highlighting that these σ _v_,CO values are
likely to be overestimated due to beam-smearing residual effects.
We also show the values presented by Wilson et al. (2019)
for the local ULIRG sample (measured at 450 − 650 pc scales)
and the average galactic values for a sub-sample of 17 SFGs
taken from the EDGE-CALIFA survey (Bolatto et al. 2017). For
these SFGs, the σ _v_,CO values are taken from Levy et al. (2018),
whereas the average Σ H 2 values are calculated by using the _M_ H 2
and _R_ 1/2,CO estimates presented in Bolatto et al. (2017) and assuming a radial spatial extension of 2 × _R_ 1/2,CO . The ‘ _z_ ∼ 1.5’


4 It is defined as the region within three times the synthesized beam
size from the best-fit galactic dynamical centre (see Fig. 3).



Article number, page 11 of 22

_A&A proofs:_ manuscript no. manuscript





1.5 2.0 2.5 3.0 3.5 4.0 4.5
log 10 ( Σ Tot ) [M      - O [ pc] [-2] []]



**100**


**10**













**0** **1** **2** **3** **4**

log 10 ( Σ H 2 ) [M     - O [ pc] [-2] []]



1.5 2.0 2.5 3.0 3.5 4.0 4.5
log 10 ( Σ tot ) [M       - O [ pc] [-2] []]



Fig. 6: _Left:_ Pixel-by-pixel molecular gas velocity dispersion estimates as a function of molecular gas surface density. For each
starburst galaxy, in grey colour, we show the σ _v_,CO values that may be overestimated due to beam-smearing residual effects. The
error bar in the lower-right corner indicates the typical 1-σ uncertainty, whereas the arrow represents the systematic uncertainty
given by the use of our α CO upper limit instead of the adopted value. The ‘ _z_ ∼ 0 ULIRG’ sample is taken from Wilson et al. (2019).
The ‘ _z_ ∼ 0 SFGs’ sample estimates are galactic average values measured for a sub-sample of galaxies taken from the CARMAEDGE survey (Bolatto et al. 2017; Levy et al. 2018). The ‘ _z_ ∼ 1.5 SFG’ data correspond to the ∼kpc-scale measurements for a
main-sequence galaxy presented in Molina et al. (2019a). The solid line represents the empirical relationship suggested by Wilson
et al. (2019). The dashed line shows the empirical relationship corrected by the average Σ H 2 /Σ Tot and _V_ rot,CO /σ _v_,CO ratios measured
for both systems. _Middle:_ Pixel-by-pixel σ _v_,CO values as a function of the total surface density. _Right:_ Molecular gas scale height as
a function of the total gas surface density. The last two panels are colour-coded in the way as the _left_ panel. The vertical pressure
equilibrium model gives a reasonable representation of our data.



SFG data correspond to ∼kpc-scale measurements for a mainsequence galaxy presented in Molina et al. (2019a).
Despite of comparing with data observed at different spatial
resolutions, both starbursts exhibit σ _v_,CO values mainly in the
range between the local SFGs and ULIRGs, but their ∼kpc-scale
Σ H 2 values are comparable to the average estimates measured for
the local SFGs and much lower than the estimates reported for
the ULIRG sample. However, similar to the ULIRGs, the starburst data seem to follow a roughly σ _v_,CO ∝ Σ [0] H [.] 2 [5] [power-law rela-]
tionship. This is shown by the dashed line which represents the
pressure balance model suggested by Wilson et al. (2019), but
scaled to the average Σ H 2 /Σ Tot and _V_ rot,CO /σ _v_,CO ratios measured
for both systems. Additionally, the solid line shows Wilson et al.
(2019)’s model for the local ULIRGs.
We now consider the total surface density Σ Tot (Fig. 6). We
approximate Σ Tot by the sum of Σ H 2 and the stellar surface density Σ ⋆ (Σ Tot ≡ Σ H 2 + Σ ⋆ ). For each starburst, the pixel-by-pixel
Σ ⋆ values are calculated by scaling the SINFONI _K_ -band continuum image surface brightness distribution (Fig. E.1) to the
global _M_ ⋆ value derived by magphys.
HATLAS114625 and HATLAS121446 starbursts tend to be
located in the lower Σ Tot limit covered by the ULIRG sample.
Despite of the large scatter (≈0.22 dex, for non-masked values),
the vertical pressure balance model (solid line) gives a reasonable representation of the data. We note that the systematic uncertainty added by the adopted α CO conversion factor is low
as the Σ Tot values are mainly dictated by Σ ⋆ in both starbursts
(sources have low integrated molecular gas fractions; see Table 5). The scatter is probably increased by the use of a constant
mass-to-light ratio to estimate Σ ⋆ .
By using Eq. 8 we estimate roughly _h_ H 2 for both starbursts.
We plot the _h_ H 2 pixel-by-pixel distribution in the right panel of
Fig. 6. From the non-masked pixels, we obtain _h_ H 2 ∼ 200 [+] − [250] 130
and 160 [+] − [570] 80 [pc] [median] [values] [for] [HATLAS114625] [and] [HAT-]
LAS121446, respectively. Those values are consistent with the


Article number, page 12 of 22



average estimate reported for the ULIRG systems (∼ 150 pc;
Wilson et al. 2019).


Our data support the scenario in which the molecular gas
velocity dispersion on large scales (∼kpc-scales) is set by the
local gravitational potential of the galaxy through the reaching
of the vertical pressure balance as suggested by Wilson et al.
(2019).


We note that, the main difference between the two starbursts
analysed in this work and the ULIRGs presented by Wilson et al.
(2019) is that, in the former, the vertical gravitational pressure is
mainly dictated by the stellar component ( _f_ H 2 ∼ 0.1) and not
by a nearly equal gravitational contribution from stars and gas.
Indeed, if in Eq 6 we take the approximation Σ Tot ∼ Σ ⋆ and
we assume vertical pressure equilibrium, then we obtain σ _v_,CO ∝
Σ [0] ⋆ [.][5] [, suggesting that, even in starburst systems, the molecular gas]
dynamical properties can be set by the stellar gravity.


Momentum injected by stellar feedback may be insufficient
to produce the observed σ _v_,CO −Σ Tot trend. Hydrodynamical simulations suggest that stellar feedback can just account for σ _v_ values up to ∼6–10 km s [−][1] for the diffuse gas component and with
a moderate increase with gas surface density (Ostriker & Shetty
2011; Shetty & Ostriker 2012). However, our data sample the
σ _v_,CO ≳ 15 km s [−][1] range and additional pressure sources, such as
stellar feedback, may still set the σ _v_,CO values below this limit.


Resolution effects should be present as our ∼kpc-scale measurements may underestimate the ambient pressure at smaller
scales. This effect has been recently measured by high-resolution
(∼ 60 pc) molecular gas observations in nearby galaxies (Sun
et al. 2020). Indeed, Sun et al. (2020) suggest a correction
for the ∼kpc-scale pressure estimates. However, their observations cover a considerable lower galactic pressure range (∼
10 [4][−][6] / _k_ _B_ K cm [−][3], see Fig 8) and, thus, extrapolating such a correction and applying it to our measurements is uncertain. Nevertheless, these high-resolution observations also suggest that the

**3**


**2**


**1**


**0**


**-1**


**-2**



Juan Molina et al.: Molecular and ionized gas properties in pressure balanced ISM of starburst galaxies


**3**











**2**


**1**


**0**


**-1**


**-2**



**-3**

**1** **2** **3** **4**

log 10 Σ H 2 [M        - O [ pc] [-2] []]



**-3**

**1** **2** **3** **4**

log 10 Σ H 2 [M        - O [ pc] [-2] []]



Fig. 7: Σ SFR against Σ H 2 for HATLAS114625 ( _Left_ ) and HATLAS121446 ( _Right_ ) starbursts. In each panel, the error bar in the
bottom-right corner represents the typical 1-σ uncertainty. The arrow indicates the horizontal shift of the data produced if we
assume the α CO,uplim value instead of the median α CO estimate to calculate Σ H 2 . This is also highlighted by the lightly-coloured data
showed in the background. The dotted lines indicate fixed τ dep values. We show ∼kpc-scale spatially-resolved observations of two
_z_ ∼ 0 LIRGs (orange diamonds, Espada et al. 2018) and the median trend observed for the HERACLES nearby galaxy survey (open
circles, Leroy et al. 2013). The dot-dashed line represents the best-fit for the HERACLES ∼kpc-scale median values. We also present
spatially-resolved estimates for local ULIRGs measured at ∼350-650 pc scales (Wilson et al. 2019). In solid and dashed lines we
show the double and single power-law best fits reported by Wilson et al. (2019) for the ULIRG data, respectively. Independent of
the α CO value assumed, we find lower τ dep values than that measured from local normal star-forming galaxies.



molecular gas is in pressure balance with its weight and the local
ISM self-gravity (see also Schruba et al. 2019).
Another major caveat in our analysis comes from the assumption behind Eq. 6. This equation corresponds to a corrected
form of the Spitzer (1942) formula for an isothermal layer embedded in a spherical mass component. It does not consider a
multi-component composition of the ISM and may not be appropriate to describe the vertical pressure produced by a gaseous
plus stellar ISM. For example, in the traditional Elmegreen
(1989)’s ISM pressure formula, the Σ ⋆ term is weighted by
the ratio between the molecular-to-stellar velocity dispersions
( _s_ ≡ σ _v_,CO /σ _v_,⋆ ) [5] . In this case, the additional vertical pressure
set by Σ ⋆ can be neglected in the limit _s_ << 1. Only if _s_ ∼ 1,
then Eq. 6 is recovered. Thus, Eq. 6 should be considered as an
upper limit case of the Elmegreen (1989)’s formula.


_4.2._ _The star-formation activity traced at_ ∼ _kpc-scales_


Our CO(1-0) and Paα observations are ideal for studying the star
formation activity in dusty starburst galaxies. The CO(1-0) emission provides a direct estimate to the molecular gas mass (albeit an α CO ), and Paα does not suffer from significant extinction
(compared to Hα), facilitating a direct view to the star formation
activity in dustier environments.
The star formation activity can be described as a power-law
relationship between the SFR surface density (Σ SFR ) and total
gas surface density (Σ gas ) or Σ H 2, the well-known Kennicutt

5 Compared to Eq. 6, Σ Tot is replaced by [Σ H 2 + _s_ Σ ⋆ ] and γ = 0.



Schmidt relationship (Kennicutt 1998a). For typical local starforming galaxies, when Σ H 2 is used, it is well-characterized by a
linear relation with an observed average molecular gas depletion
time τ dep ≡ Σ H 2 /Σ SFR = 2.2 ± 0.3 Gyr (Leroy et al. 2013). However, this linear trend seems not to be followed by galaxies with
enhanced SFRs as those tend to exhibit shorter molecular gas
depletion times or higher star formation efficiencies (SFE≡ τ [−] dep [1] [,]
e.g. Daddi et al. 2010).
In Fig 7, we show the pixel-by-pixel distribution in the Σ SFR –
Σ H 2 plane for HATLAS114625 and HATLAS121446. The Σ SFR
and Σ H 2 quantities are directly estimated from the spatiallyresolved SINFONI and ALMA observations assuming the median α CO value (Table 5) and employing the dynamical modelling to correct by projection effects.
We use the hastrom task written in the Interactive Data Language (IDL) to register the images on the same pixel scales and
orientation. While implementing this routine, we consider that
the total flux is conserved in each map. We prefer not to include
the HATLAS090750 system in our analysis due to its complex
geometry and uncertain α CO value.
We compare our Σ SFR –Σ H 2 estimates with ∼kpc-scale local galaxy measurements and the ∼sub-kpc data from local
ULIRGs. Briefly, the ∼kpc-scale data are represented by the median trend reported from the HERA CO-Line Extragalactic Survey (HERACLES, Leroy et al. 2008) for normal star-forming
systems and measurements from two LIRGs (NGC3110 and
NGC232; Espada et al. 2018). The local ULIRG data correspond
to CO(1-0)-based ∼350-650 pc-scale estimates presented in Wilson et al. (2019).


Article number, page 13 of 22

_A&A proofs:_ manuscript no. manuscript



The two galaxies presented in this work exhibit τ dep values in
the range of ∼0.1–1 Gyr, i.e., τ dep values comparable to that derived for ULIRGs (τ dep ≲ 0.1 Gyr), but in a low Σ H 2 environment.
τ dep internal galactic trends are not clear due to the considerable
data scatter.

If we assume our α CO,uplim estimates, we obtain τ dep median values of ∼0.5 and 0.6 Gyr for HATLAS114625 and HATLAS121446, respectively. In this case, both starbursts mainly
present τ dep values within 0.2 −−2.2 Gyr, a range similar to
that reported for the two local LIRGs (0.2–1.6 Gyr; Espada et al.
2018). In any case, the depletion times estimated for both galaxies are lower than the τ dep median values reported for local SFGs
with similar Σ H 2 and _f_ H 2 values (Leroy et al. 2013). It suggests
that the enhancement of the SFE seen in starburst galaxies may
not be only related to high Σ H 2 estimates.


_4.3._ _Pressure regulated star-formation activity_


If the star-formation activity also depends on the dynamics of
the molecular gas, then Σ SFR should also correlate with the physical variables that regulate these properties. Thus, if the vertical
pressure equilibrium sets the molecular gas properties on larger
scales (∼ kpc-scales, § 4.1), then Σ SFR should correlate with the
ISM pressure set by self-gravity _P_ grav . The correlation between
Σ SFR and ISM pressure has been suggested and observed previously by many authors (e.g. Genzel et al. 2010; Ostriker et al.
2010; Ostriker & Shetty 2011; Bolatto et al. 2017; HerreraCamus et al. 2017; Fisher et al. 2019) and also used to explain
the so-called ‘extended’ Kennicutt-Schmidt relation (Shi et al.
2011). Indeed, the mid-plane hydrostatic pressure seems to predict the star formation efficiency better than gas surface density
in atomic-dominated regimes (Leroy et al. 2008).
In Fig. 8, we show Σ SFR as a function _P_ grav . The Physics at
High Angular resolution in Nearby Galaxies (PHANGS; Leroy
et al. in prep.) data correspond to measurements from 28 nearby
galaxies presented in Sun et al. (2020) and artificially convolved
to kpc-scale by them. We also consider the spatially-resolved
ULIRG data presented in Wilson et al. (2019) and The Hi Nearby
Galaxy Survey (THINGS; Walter et al. 2008; de Blok et al. 2008)
and DYNAMO (Green et al. 2014) galactic averages presented
in Fisher et al. (2019). We caution, however, that the DYNAMO
pressure data are based on ionized gas velocity dispersions and
unresolved CO emission line measurements, while we are using spatially-resolved molecular gas estimates. We also show the
∼kpc-scale data measured for a typical star-forming galaxy at
_z_ ∼ 1.5 (Molina et al. 2019a).
Our data clearly fill the gap between the ULIRG the
PHANGS data in terms of pressure set by self-gravity. We find
that Σ SFR is correlated with _P_ grav across nearly seven and six orders of magnitude in terms of _P_ grav and Σ SFR, respectively.
By performing a linear fit in the log-log parameter space
(log 10 (Σ SFR ) = _N_ × log 10 ( _P_ grav / _P_ 0 )) using emcee (ForemanMackey et al. 2013), we find a best-fit slope _N_ = 0.78 ± 0.01
with an interceptor value log 10 ( _P_ 0 / _k_ _B_ [cm [−][3] K]) = 5.38 ± 0.04.
This is represented by the red solid line in Fig. 8. In this fitting
procedure, we have adopted conservative 0.2 dex uncertainties
for the PHANGS data estimates (Sun et al. 2020) and we have
not included the THINGS sample as we lack of measured uncertainties for those data. Nevertheless, the THINGS data are in
rough agreement with the best-fit trend. We note that we have included the _z_ ∼ 1.5 star-forming galaxy data, but the exclusion of
these data only produced a slight variation of the best-fit results
( _N_ = 0.80 ± 0.01, log 10 ( _P_ 0 / _k_ _B_ [cm [−][3] K]) = 5.57 ± 0.02).


Article number, page 14 of 22



**3**


**2**


**1**


**0**


**-1**


**-2**


**-3**







**10** **[2]** **10** **[4]** **10** **[6]** **10** **[8]** **10** **[10]**

P grav / k B [cm [-3] K]


Fig. 8: Σ SFR against the ISM pressure set by self-gravity. The
PHANGS data correspond to the manually convolved kpc-scale
measurements reported by Sun et al. (2020) for 28 nearbygalaxies. The ULIRG data correspond to the values measured at

∼
350-650 pc scales by Wilson et al. (2019). The DYNAMO data
are based on galactic ionized gas velocity dispersion measurements along with spatially-unresolved molecular gas observations (Fisher et al. 2019). We also present the ∼kpc-scale values
measured for a typical star-forming galaxy at _z_ ∼ 1.5 (SHiZELS19; Molina et al. 2019a). The dashed line corresponds to the
best-fit presented by Fisher et al. (2019) for the DYNAMO and
THINGS data, while the solid black line corresponds to the bestfit given by Sun et al. (2020) to the PHANGS data. The dotdashed line corresponds to the parametrization given by Kim
et al. (2013) for their set of hydrodynamical simulations. The
solid red line represents our best-fit. The starburst and ULIRG
data are consistent with the trend reported from the nearby galaxies. The _z_ ∼ 1.5 star-forming galaxy data are in clear offset.


Our best-fit estimates agree within 1-σ uncertainty with the
values reported for the DYNAMO (Fisher et al. 2019), and
THINGS data ( _N_ = 0.76 ± 0.06, log 10 ( _P_ 0 / _k_ _B_ [cm [−][3] K]) = 5.89 ±
0.35). However, we find that Fisher et al. (2019)’s best-fit is offset from the kpc-scale data by ∼ 0.5 dex, suggesting that their
result was probably affected by the assumptions behind using
unresolved CO data.

Sun et al. (2020) report _N_ = 0.84 ± 0.01 and
log 10 ( _P_ 0 / _k_ _B_ [cm [−][3] K]) = 5.85 ± 0.01 best-fit estimates for the
PHANGS data, but they caution that their best-fit uncertainties
may be underestimated due to not considering systematic errors.
This problem may be affecting our uncertainty estimates as well.

To compare with their result, we estimate the r.m.s. of the
best-fit residuals. We measure r.m.s. ≈ 0.34 and ≈ 0.36 dex from
our and Sun et al. (2020) best-fits, respectively. We note that
these values are considerably increased by considering the _z_ ∼
1.5 SFG data. However, these data seem to be an outlier compared to the other kpc-scale measurements and, perhaps, it is
produced by an underestimated dust extinction correction applied to the observed SFR for this system. If we do not consider

Juan Molina et al.: Molecular and ionized gas properties in pressure balanced ISM of starburst galaxies



the _z_ ∼ 1.5 SFG data, we find r.m.s. ≈ 0.25 dex from both bestfit residuals. Thus, in both cases, we obtain a good agreement
between our and Sun et al. (2020) results.
The stellar feedback regulated model predicts a Σ SFR and
ISM pressure correlation with the slope close to unity (Ostriker & Shetty 2011). In this model, stellar feedback (e.g. photoionization, radiation, supernovae, winds) heats the ISM gas
while the energy and pressure losses occur via turbulent dissipation and cooling. The star formation activity gives pressure support against self-gravity (hence, _P_ ISM = _P_ grav ). Σ SFR
and _P_ ISM are closely related due to a nearly constant injected
feedback momentum per stellar mass formed _p_ ⋆ / _m_ ⋆ (Σ SFR =
4( _p_ ⋆ / _m_ ⋆ ) [−][1] _P_ ISM ; e.g. Ostriker et al. 2010; Ostriker & Shetty
2011; Shetty & Ostriker 2012).
This is highlighted by the dot-dashed line in Fig. 8 which
represents the best-fit power-law ( _N_ ≈ 1.1) for the hydrodynamical simulations presented in Kim et al. (2013). This power-law
overestimates the ISM pressure for the ULIRG systems. However, those systems display larger Σ SFR values than that covered by the simulations (Σ [sim] SFR [≲] [10] [−][2] _[ M]_ [⊙] [yr] [−][1] [ kpc] [−][2] [; Kim et al.]
2013).
To further test the plausibility of a Σ SFR ∝ _P_ grav trend, we fit a
linear function to our data. We obtain a best-fit interceptor value
log 10 ( _P_ 0 / _k_ _B_ [cm [−][3] K]) = 6.74 ± 0.01 (we caution that the uncertainty may be underestimated due to systematic errors) and a
residual r.m.s. of ≈0.47 and ≈0.31 dex depending on whether we
include the _z_ ∼ 1.5 SFG data or not. The r.m.s. values are slightly
higher than the reported estimates from our previous best-fit. The
interceptor value translates to _p_ ⋆ / _m_ ⋆ ∼ 4600 km s [−][1], a value
that is ∼ 1.5 times higher than the estimate typically adopted
for single supernovae feedback (∼ 3000 km s [−][1] ; e.g. Thornton
et al. 1998; Martizzi et al. 2015; Ostriker & Shetty 2011; Kim &
Ostriker 2015). Enhanced feedback from clustered supernovae
may be needed to explain such a _p_ ⋆ / _m_ ⋆ value (e.g. Sharma et al.
2014; Gentry et al. 2017; Kim et al. 2017). However its effectiveness is still under debate (Gentry et al. 2019).
Additional energy sources that regulate the star formation
activity should also be considered. Mass transport through the
galactic disc could be one of these (e.g. Krumholz et al. 2018).
Nevertheless, this may require understanding how the gas dissipates the gravitational energy from larger scales toward smaller
scales (e.g. Bournaud et al. 2010; Combes et al. 2012).
Our observations suggest that, in our dusty starburst galaxies,
the molecular gas properties seem to be regulated by the pressure set by self-gravity (§ 4.1). Therefore, a possibility is that
the gravitational instabilities may induce large scale gas motions
that then are dissipated through energy cascades toward small
scales (e.g. Bournaud et al. 2010; Combes et al. 2012) until the
range where stellar feedback operates and stops the local gravitational collapse through momentum/energy injection. In this
picture, the observed star formation activity occurs as a response
to the ISM pressure balance.
It is also worth mentioning that Sun et al. (2020) calculated
_P_ grav by using the ‘dynamical equilibrium pressure’ ( _P_ DE e.g.
Elmegreen 1989; Wong & Blitz 2002; Ostriker et al. 2010; Ostriker & Shetty 2011; Fisher et al. 2019) which accounts for the
gas and stellar galaxy self-gravity in the limit in which the gas
disc scale height ( _h_ gas ) is much smaller than the stellar disc scale
height ( _h_ ⋆ ; Benincasa et al. 2016). They neglect the gravitational
pressure set by the dark matter component as this pressure source
is small in galaxies analysed by them. It is also the case of our
galaxies and the ULIRGs presented in Wilson et al. (2019). We
determine _P_ grav by using Eq. 6. This equation corresponds to a
_P_ DE upper limit case when _h_ gas ≈ _h_ ⋆ (see Appendix A of Ben


incasa et al. 2016). Thus, a possible correction to our _P_ grav estimates may lead to a stepper Σ SFR − _P_ grav correlation.
Another possible source of uncertainty comes from the limited spatial resolution from our observations. Beam-smearing
effect produces that Σ SFR and Σ H 2 (hence, _P_ grav ) are average
∼kpc-scale estimates of the patchy underlying surface density
distributions. This artificial dilution effect is quantified for the
PHANGS molecular gas data (see Sun et al. 2020 for more details), however, it is unknown for the starburst galaxy population
where the ISM is denser. Higher spatial resolution observations
(∼ 10 − 100 pc) may further be needed to quantify this.


_4.4._ _Limitations of our dynamical mass approach_


One of the stronger constraints for the dynamical modelling is
given by the assumption of a constant CO-to-H 2 conversion factor across the galactic disc. This may not be an ideal assumption
due to possible α CO variation with galactocentric radius (e.g.
Sandstrom et al. 2013). Indeed, lower α CO values are likely to
be measured towards the Galactic centre (Bolatto et al. 2013).
Based on the dynamical mass modelling, it is highly uncertain to
determine an α CO radial variation due to the unconstrained dark
matter fraction values. We need to assume a halo model. However, we can not accurately constrain the halo properties as the
observed rotation curves do not extend more than ∼6 kpc away
from the galactic centre (Fig. 4). A constant α CO assumption is
reasonable given our data limitations.
The dynamical interpretation is mainly limited by the degeneracy between α CO and _f_ DM values constrained at the inner
galactocentric radius considered in each galaxy ( _R_ ≈ 2.3 kpc,
Fig. 4). The over/under-estimation of _f_ DM at this radius will bias
our result towards lower/higher α CO estimates. In the case that
we are underestimating _f_ DM, then the median α CO values should
be considered as an upper limit of the true values, implying that
both starburst galaxies might have lower molecular gas masses
and α CO values even lower than that reported for ULIRGs.
On the other hand, a possible overestimation of the _f_ DM does
not affect our results. If we assume the limit case that there is
no dark matter, then the median α CO values increase by ≲14 %
compared to these estimated values when the dark matter content is considered. This variation is smaller than the α CO PDF’s
1-σ range and it is independent of the dynamical mass model
assumed (see Fig. 5).
Another limitation comes from the adopted dynamical mass
formula. We have not considered any geometrical factor that
should multiply the _V_ rot,CO values in Eq. 5. This is equivalent to
the assumption of spherical geometry when calculating enclosed
mass estimates from rotational motions. However, this source
of uncertainty is expected to not affect our conclusions. For example, the _V_ circ difference between an exponential disk and the
equivalent spherical mass distribution is ≲ 15% and it highly depends on the disc radius (see Fig. 2.17 in Binney & Tremaine
2008). By adopting this _V_ circ difference value (translated into the
enclosed mass difference), then the median α CO values would
increase by ∼30 %. Again, this variation is smaller than the estimated α CO PDF’s 1-σ range.
The CO(1-0) emission source is also a concern. From our

∼
kpc-scale observations, we can not separate between the CO(10) emission originated in GMCs and any significant molecular
gas diffuse emission. This diffuse component may not be negligible in galaxies (e.g Goldsmith et al. 2008; Schinnerer et al.
2010) and it is enhanced in dense and high ISM pressure galactic environments (Sandstrom et al. 2013). If the diffuse molecular gas phase dominates the CO(1-0) emission, then low α CO


Article number, page 15 of 22

_A&A proofs:_ manuscript no. manuscript



**100.0**


**10.0**


**1.0**







**0.1**
**10** **[1]** **10** **[2]** **10** **[3]** **10** **[4]** **10** **[5]**

Σ Tot [M            - O [pc] [-2] []]


Fig. 9: Median CO-to-H 2 conversion factor estimates as a
function of the total surface density. The grey circles correspond to the α CO values based on dust emission for nearby
disc galaxies (Sandstrom et al. 2013). The ULIRG data correspond to the estimates presented in Downes & Solomon (1998)
and Papadopoulos et al. (2012). In the latter case, we show
the α CO values reported from their ‘one-’ and ‘two-component’
multi-transition models. The color bands indicate the traditional
CO-to-H 2 conversion factors and their uncertainties for Milky
Way- and ULIRG-like systems (Bolatto et al. 2013). The green
line corresponds to the α CO parametrization suggested by Bolatto et al. (2013) for galaxies with solar metallicity. For HATLAS114625, we find a lower α CO estimate than the expected
value from Bolatto et al. (2013)’s parametrization. In the case of
HATLAS121446, we find an agreement within 1-σ uncertainty.
Figure adapted from Bolatto et al. (2013).


values may underestimate the high density molecular gas mass
content for both starbursts (Papadopoulos et al. 2012). This effect is highlighted by the difference in the estimated α CO values
between the ‘one-’ and ‘two-component’ models for ULIRGs
(Fig. 9, see Papadopoulos et al. 2012).
However, it should be noted that molecular gas diffuse emission and its contribution to the estimated α CO values are uncertain. The CO-to-H 2 conversion factor may vary significantly for
this gas component depending on local environment properties
(e.g. Liszt & Pety 2012). Additional observations tracing the
dense molecular gas phase may help to determine whether our
α CO estimations are biased toward low values or not.

We note that we have not considered the Hi content in our
dynamical mass approach as we expect a negligible amount of
Hi mass within the inner radius ( _R_ ≈ 2.3 kpc) at which _M_ dyn was
calculated. We remind that the _M_ dyn values calculated at these
radii are the ones that strongly constrain the α CO estimates in
our procedure. In local spirals, the transition between an H 2 - to
Hi-dominated ISM (Σ H 2 ≈ Σ HI ) occurs at Σ gas ∼ 12 ± 6 _M_ ⊙ pc [−][2]
(Leroy et al. 2008). From the spatially-resolved CO(1-0) observations and the adopted α CO values, we estimate Σ H 2 ∼ 146 ± 93
and 127 ± 50 _M_ ⊙ pc [−][2] at _R_ ≈ 2.3 kpc for HATLAS114625 and
HATLAS121446 galaxies, supporting our assumption.
Finally, we check if our α CO estimates are reasonable given
by the theoretical expectation (Bolatto et al. 2013). From theories, it is expected that α CO mainly varies with the system metallicity and total surface density. However, before making any
comparison, we note that HATLAS114625 and HATLAS121446
present supra-solar metallicity values in terms of the gas phase


Article number, page 16 of 22



oxygen abundance (12 + log(O/H) = 8.99 and 8.72, respectively) [6] . We note that above the solar metallicity, we do not expected any significant variation of α CO due to the high metal
content (Bolatto et al. 2013). Thus, we simply assume a solar
metallicity when comparing with Bolatto et al. (2013)’s theoretical prediction. We show this comparison in Fig. 9. We find that
the reported median CO-to-H 2 values are somewhat lower than
the theoretical expectation, but still consistent within the scatter.
Our α CO estimates are, therefore, reasonable given the measured
12 + log(O/H) and Σ Tot values for both starbursts.


**5.** **Conclusions**


We present new ALMA Cycle-3 and VLT-SINFONI observations tracing the CO(1-0) and Paα emission lines from three
starburst galaxies at _z_ ∼ 0.12–0.18 taken from the VALES survey. The ALMA observations were designed to deliver spatiallyresolved observations of the molecular gas content at ∼ 0 [′′] . 5, i.e.,
approximately the resolution of the seeing-limited SINFONI observations (∼ 0 [′′] . 4 − 0 [′′] . 8). Combining near-IR and sub-mm observations, we study the ionized and molecular gas dynamics at

∼
kpc-scales.
One target, HATLAS090750, presents highly asymmetric
morpho-kinematics, suggesting an on-going merger. From its
SINFONI observation, we also detected fainter ro-vibrational
warm molecular gas transitions along with an ionized Helium
line in its central galactic zone. The H 2 emission lines were used
to determine a warm molecular gas temperature of ∼ 1700 ±
500 K (Fig C.1), probably produced by supernovae remnant
shocks. However, we could not discard non-thermal gas excitation sources due to the lack of H 2 emission line intensity measurements with different vibrational energy levels (e.g. Davies
et al. 2003).
The other two starburst galaxies, HATLAS114625 and HATLAS121446, show disc-like morpho-kinematics, with rotation
as the dominant component supporting self-gravity ( _V_ rot /σ _v_ ∼
7 − 8). For both systems, we model the CO and Paα galactic
dynamics and we aid the kinematic modelling by using _K_ -band
photometric models to constrain the inclination angle parameter. From those analyses, we find that the CO and Paα dynamics
present a good agreement in both galaxies (Fig. 3), as suggested
by similar kinematic position angles (∆PA∼ 4 deg.) and emission
line spatial extensions ( _R_ 1/2,Paα / _R_ 1/2,CO ∼ 1). Our observations
suggest that the ionized and molecular gas components display
roughly the same galaxy morpho-kinematics.
We estimate the total mass budget for both, HATLAS114625
and HATLAS121446 galaxies, by calculating the dynamical
masses assuming the ‘thin-’ and ‘thick-disc’ hydrostatic equilibrium approximations (Burkert et al. 2010) along with two
different surface density profile models. We obtain α CO values
in the range of 0.7–1.2 _M_ ⊙ (K km s [−][1] pc [2] ) [−][1] for both galaxies
(Fig 5), i.e., similar values to that reported for ULIRGs (Downes
& Solomon 1998). These values do not depend strongly on the
hydrostatic equilibrium and total surface density assumptions.
Our conversion factor estimates are somewhat lower but still
consistent with the α CO ∝ Σ [−] Tot [0][.][5] trend suggested from theoretical expectations (Fig. 9, Bolatto et al. 2013).
By adopting the dynamically based α CO values, we obtain
molecular gas fractions of the order of ∼ 0.1 for both starbursts,


6 We base our metallicity estimates on the Pettini & Pagel (2004) calibration scale and the [Nii] and Hα line intensities reported in Table A.1.
We also adopt a solar abundance of 12 + log(O/H) = 8.69 (Asplund
et al. 2009).

Juan Molina et al.: Molecular and ionized gas properties in pressure balanced ISM of starburst galaxies



far below our initial expectations and consistent with values
measured in local star-forming galaxies. Therefore, the sources
are not ‘gas-rich’ as initially thought, highlighting the difficulties to estimate molecular gas masses due to the uncertainty of
the CO-to-H 2 conversion factor.
We find that the HATLAS114625 and HATLAS121446
molecular gas velocity dispersion values are reasonably represented by a σ _v_,CO ∝ Σ [0] tot [.][5] [trend,] [where] [Σ] [tot] [is] [the] [total] [galaxy]
surface density (Fig. 6). This suggests that the molecular gas
velocity dispersion values are consistent with being set by the
galaxy self-gravity to maintain the vertical pressure balance.
We study the star formation activity traced at ∼kpc-scales in
HATLAS114625 and HATLAS121446 starbursts. Both galaxies exhibit τ dep values in the range of ∼0.1–1 Gyr (Fig. 7),
i.e., values consistent with the reported estimates for ULIRGs
(τ dep ∼ 0.1 Gyr). However, both systems present Σ H 2 values that
are comparable to those seen in local star-forming disc galaxies (Leroy et al. 2013). This suggests that the decrease of τ dep
(or enhancement of SFE) is also produced by additional physical
processes that may not only be related to high Σ H 2 environments.
To further explore this, we study the correlation between
Σ SFR and the gravitational pressure _P_ grav . HATLAS114625
and HATLAS121446 fill the gap between the normal galaxies and the ULIRG systems in terms of pressure set by
self-gravity. We find a linear relation in the log-log space,
log 10 (Σ SFR ) = _N_ × log 10 ( _P_ grav / _P_ 0 ), where _N_ = 0.78 ± 0.01 and
log 10 ( _P_ 0 / _k_ _B_ [cm [−][3] K]) = 5.38 ± 0.04 (Fig. 8). It is in agreement
with the trend reported for local galaxies Sun et al. (2020), suggesting that, in these _z_ ∼ 0.12 − 0.17 dusty starburst galaxies, the
star formation activity can be a consequence of the ISM pressure
balance.


_Acknowledgements._ We thank the anonymous referee for her/his careful reading of our manuscript as well as helpful comments and suggestions. This
work was supported by the National Science Foundation of China (11421303,
11721303, 11890693, 11991052) and the National Key R&D Program of
China (2016YFA0400702, 2016YFA0400703). We acknowledge Prof. Fisher for
kindly sharing his data. J. M. and A. E. acknowledge support from CONICYT
project Basal AFB-170002 and Proyecto Regular FONDECYT (grant 1181663).
E. I. acknowledges partial support from FONDECYT through grant N [◦] 1171710.
N. G. acknowledges financial support from ICM Núcleo Milenio de Formación
Planetaria, NPF and grant support from project CONICYT-PFCHA/Doctorado
Nacional/2017 folio 21170650. C. C. is supported by the National Natural Science Foundation of China, No. 11803044, 11933003, 11673028 and by the National Key R&D Program of China grant 2017YFA0402704. M. J. M. acknowledges the support of the National Science Centre, Poland through the SONATA
BIS grant 2018/30/E/ST9/00208. This work is sponsored (in part) by the Chinese
Academy of Sciences (CAS), through a grant to the CAS South America Center for Astronomy (CASSACA). This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2015.1.01012.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated
by ESO, AUI/NRAO and NAOJ. This work is also based on observations collected at the European Organization for Astronomical Research in the Southern
Hemisphere under ESO programme ID 099.B-0479(A).


**References**


Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, Annual Review of
Astronomy and Astrophysics, 47, 481
Baldry, I. K., Liske, J., Brown, M. J. I., et al. 2018, MNRAS, 474, 3875
Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5
Bayo, A., Rodrigo, C., Barrado Y Navascués, D., et al. 2008, A&A, 492, 277
Bedregal, A. G., Colina, L., Alonso-Herrero, A., & Arribas, S. 2009, ApJ, 698,
1852
Benincasa, S. M., Wadsley, J., Couchman, H. M. P., & Keller, B. W. 2016, MNRAS, 462, 3053
Benjamin, R. A., Skillman, E. D., & Smits, D. P. 1999, ApJ, 514, 307
Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846



Binney, J. & Tremaine, S. 2008, Galactic Dynamics: Second Edition
Black, J. H. & van Dishoeck, E. F. 1987, ApJ, 322, 412
Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, Annual Review of Astronomy
and Astrophysics, 51, 207
Bolatto, A. D., Wong, T., Utomo, D., et al. 2017, ApJ, 846, 159
Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047
Bournaud, F., Elmegreen, B. G., & Elmegreen, D. M. 2007, ApJ, 670, 237
Bournaud, F., Elmegreen, B. G., Teyssier, R., Block, D. L., & Puerari, I. 2010,
MNRAS, 409, 1088
Brand, P. W. J. L., Toner, M. P., Geballe, T. R., & Webster, A. S. 1989, MNRAS,
237, 1009
Bryant, J. J., Owers, M. S., Robotham, A. S. G., et al. 2015, MNRAS, 447, 2857
Burkert, A., Förster Schreiber, N. M., Genzel, R., et al. 2016, ApJ, 826, 214
Burkert, A., Genzel, R., Bouché, N., et al. 2010, ApJ, 725, 2324
Calabrò, A., Daddi, E., Cassata, P., et al. 2018, ApJ, 862, L22
Calistro Rivera, G., Hodge, J. A., Smail, I., et al. 2018, ApJ, 863, 56
Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682
Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105
Chabrier, G. 2003, PASP, 115, 763
Cheng, C., Ibar, E., Hughes, T. M., et al. 2018, MNRAS, 475, 248
Cluver, M. E., Jarrett, T. H., Hopkins, A. M., et al. 2014, ApJ, 782, 90
Colina, L., Piqueras López, J., Arribas, S., et al. 2015, A&A, 578, A48
Combes, F., Boquien, M., Kramer, C., et al. 2012, A&A, 539, A67
Courteau, S. 1997, AJ, 114, 2402
Crowther, P. A. 2007, ARA&A, 45, 177
Da Cunha, E., Charlot, S., & Elbaz, D. 2008, MNRAS, 388, 1595
Daddi, E., Bournaud, F., Walter, F., et al. 2010, ApJ, 713, 686
Davies, R. I., Sternberg, A., Lehnert, M., & Tacconi-Garman, L. E. 2003, ApJ,
597, 907
de Blok, W. J. G., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2648
Dekel, A., Sari, R., & Ceverino, D. 2009, ApJ, 703, 785
Downes, D. & Solomon, P. M. 1998, ApJ, 507, 615
Draine, B. T. & Woods, D. T. 1990, ApJ, 363, 464
Driver, S. P., Wright, A. H., Andrews, S. K., et al. 2016, MNRAS, 455, 3911
Eales, S., Dunne, L., Clements, D., et al. 2010, PASP, 122, 499
Eisenhauer, F., Abuter, R., Bickert, K., et al. 2003, in Proc. SPIE, Vol. 4841,
Instrument Design and Performance for Optical/Infrared Ground-based Telescopes, ed. M. Iye & A. F. M. Moorwood, 1548–1561
Elmegreen, B. G. 1989, ApJ, 338, 178
Elmegreen, B. G. & Scalo, J. 2004, ARA&A, 42, 211
Epinat, B., Tasca, L., Amram, P., et al. 2012, A&A, 539, A92
Espada, D., Martin, S., Verley, S., et al. 2018, ApJ, 866, 77
Faucher-Giguère, C.-A., Quataert, E., & Hopkins, P. F. 2013, MNRAS, 433, 1970
Fazeli, N., Busch, G., Valencia-S., M., et al. 2019, A&A, 622, A128
Fisher, D. B., Bolatto, A. D., White, H., et al. 2019, ApJ, 870, 46
Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125,
306
Freeman, K. C. 1970, ApJ, 160, 811
Geach, J. E., Sobral, D., Hickox, R. C., et al. 2012, MNRAS, 426, 679
Gentry, E. S., Krumholz, M. R., Dekel, A., & Madau, P. 2017, MNRAS, 465,
2471
Gentry, E. S., Krumholz, M. R., Madau, P., & Lupi, A. 2019, MNRAS, 483,
3647
Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091
Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20
Goldsmith, P. F., Heyer, M., Narayanan, G., et al. 2008, ApJ, 680, 428
Green, A. W., Glazebrook, K., McGregor, P. J., et al. 2014, MNRAS, 437, 1070
Hayward, C. C. & Hopkins, P. F. 2017, MNRAS, 465, 1682
Herrera-Camus, R., Bolatto, A., Wolfire, M., et al. 2017, ApJ, 835, 201
Holmberg, E. 1958, Meddelanden fran Lunds Astronomiska Observatorium Serie II, 136, 1
Ibar, E., Lara-López, M. A., Herrera-Camus, R., et al. 2015, MNRAS, 449, 2498
Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, MNRAS, 346, 1055
Kausch, W., Noll, S., Smette, A., et al. 2015, A&A, 576, A78
Kelvin, L. S., Driver, S. P., Robotham, A. S. G., et al. 2012, MNRAS, 421, 1007
Kennicutt, Robert C., J. 1998a, ApJ, 498, 541
Kennicutt, Jr., R. C. 1998b, ARA&A, 36, 189
Kereš, D., Katz, N., Weinberg, D. H., & Davé, R. 2005, MNRAS, 363, 2
Kewley, L. J., Dopita, M. A., Sutherland, R. S., Heisler, C. A., & Trevena, J.
2001, ApJ, 556, 121
Kim, C.-G., Kim, W.-T., & Ostriker, E. C. 2011, ApJ, 743, 25
Kim, C.-G. & Ostriker, E. C. 2015, ApJ, 802, 99
Kim, C.-G., Ostriker, E. C., & Kim, W.-T. 2013, ApJ, 776, 1
Kim, C.-G., Ostriker, E. C., & Raileanu, R. 2017, ApJ, 834, 25
Kronberger, T., Kapferer, W., Schindler, S., & Ziegler, B. L. 2007, A&A, 473,
761
Krumholz, M. R. & Burkhart, B. 2016, MNRAS, 458, 1671
Krumholz, M. R., Burkhart, B., Forbes, J. C., & Crocker, R. M. 2018, MNRAS,
477, 2716
Lang, P., Förster Schreiber, N. M., Genzel, R., et al. 2017, ApJ, 840, 92


Article number, page 17 of 22

_A&A proofs:_ manuscript no. manuscript


Larkin, J. E., Armus, L., Knop, R. A., Soifer, B. T., & Matthews, K. 1998, ApJS,
114, 59
Lefever, K., Puls, J., Morel, T., et al. 2010, A&A, 515, A74
Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670
Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782
Leroy, A. K., Walter, F., Sandstrom, K., et al. 2013, AJ, 146, 19
Levy, R. C., Bolatto, A. D., Teuben, P., et al. 2018, ApJ, 860, 92
Liszt, H. S. & Pety, J. 2012, A&A, 541, A58
Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415
Madau, P., Ferguson, H. C., Dickinson, M. E., et al. 1996, MNRAS, 283, 1388
Martizzi, D., Faucher-Giguère, C.-A., & Quataert, E. 2015, MNRAS, 450, 504
Mateos, S., Alonso-Herrero, A., Carrera, F. J., et al. 2012, MNRAS, 426, 3271
Michałowski, M. J., Hayward, C. C., Dunlop, J. S., et al. 2014, A&A, 571, A75
Molina, J., Ibar, E., Smail, I., et al. 2019a, MNRAS, 487, 4856
Molina, J., Ibar, E., Villanueva, V., et al. 2019b, MNRAS, 482, 1499
Mosenkov, A. V., Sotnikova, N. Y., Reshetnikov, V. P., Bizyaev, D. V., &
Kautsch, S. J. 2015, MNRAS, 451, 2376
Motta, V., Ibar, E., Verdugo, T., et al. 2018, ApJ, 863, L16
Narayanan, D., Krumholz, M. R., Ostriker, E. C., & Hernquist, L. 2012, MNRAS, 421, 3127
Newville, M., Stensitzki, T., Allen, D. B., & Ingargiola, A. 2014, LMFIT: NonLinear Least-Square Minimization and Curve-Fitting for Python
Niemczura, E., Morel, T., & Aerts, C. 2009, A&A, 506, 213
Noll, S., Kausch, W., Kimeswenger, S., et al. 2014, A&A, 567, A25
Oliva, E., Moorwood, A. F. M., & Danziger, I. J. 1990, A&A, 240, 453
Osterbrock, D. E. & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and
active galactic nuclei
Ostriker, E. C. & Shetty, R. 2011, ApJ, 731, 41
Ostriker, J. P., Choi, E., Ciotti, L., Novak, G. S., & Proga, D. 2010, ApJ, 722,
642
Papadopoulos, P. P. & Seaquist, E. R. 1999, ApJ, 516, 114
Papadopoulos, P. P., van der Werf, P., Xilouris, E., Isaak, K. G., & Gao, Y. 2012,
ApJ, 751, 10
Pettini, M. & Pagel, B. E. J. 2004, MNRAS, 348, L59
Piqueras López, J., Colina, L., Arribas, S., Alonso-Herrero, A., & Bedregal,
A. G. 2012, A&A, 546, A64
Riffel, R., Rodríguez-Ardila, A., Aleman, I., et al. 2013, MNRAS, 430, 2002
Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22
Sánchez, S. F., Kennicutt, R. C., Gil de Paz, A., et al. 2012, A&A, 538, A8
Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5
Schawinski, K., Thomas, D., Sarzi, M., et al. 2007, MNRAS, 382, 1415
Schinnerer, E., Weiß, A., Aalto, S., & Scoville, N. Z. 2010, ApJ, 719, 1588
Schruba, A., Kruijssen, J. M. D., & Leroy, A. K. 2019, ApJ, 883, 2
Sérsic, J. L. 1963, Boletin de la Asociacion Argentina de Astronomia La Plata
Argentina, 6, 41
Sharma, P., Roy, A., Nath, B. B., & Shchekinov, Y. 2014, MNRAS, 443, 3463
Shetty, R. & Ostriker, E. C. 2012, ApJ, 754, 2
Shi, Y., Helou, G., Yan, L., et al. 2011, ApJ, 733, 87
Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, ApJ, 319, 730
Solomon, P. M. & Vanden Bout, P. A. 2005, Annual Review of Astronomy and
Astrophysics, 43, 677
Spitzer, Lyman, J. 1942, ApJ, 95, 329
Spring, E. F. & Michałowski, M. J. 2017, MNRAS, 471, L101
Stern, D., Assef, R. J., Benford, D. J., et al. 2012, ApJ, 753, 30
Sternberg, A. 1989, ApJ, 347, 863
Stott, J. P., Swinbank, A. M., Johnson, H. L., et al. 2016, MNRAS, 457, 1888
Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020, arXiv e-prints,
arXiv:2002.08964

Swinbank, A. M., Sobral, D., Smail, I., et al. 2012, MNRAS, 426, 935
Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781
Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179
Thompson, T. A., Quataert, E., & Murray, N. 2005, ApJ, 630, 167
Thornton, K., Gaudlitz, M., Janka, H. T., & Steinmetz, M. 1998, ApJ, 500, 95
U, V., Medling, A. M., Inami, H., et al. 2019, ApJ, 871, 166
Varidel, M. R., Croom, S. M., Lewis, G. F., et al. 2020, MNRAS, 495, 2265
Villanueva, V., Ibar, E., Hughes, T. M., et al. 2017, MNRAS, 470, 3775
Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, AJ, 136, 2563
Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012, ApJ, 754,
L29
Wilson, C. D., Elmegreen, B. G., Bemis, A., & Brunetti, N. 2019, ApJ, 882, 5
Wolniewicz, L., Simbotin, I., & Dalgarno, A. 1998, ApJS, 115, 293
Wong, T. & Blitz, L. 2002, ApJ, 569, 157
Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868
Zhou, L., Federrath, C., Yuan, T., et al. 2017, MNRAS, 470, 4573


Article number, page 18 of 22

Juan Molina et al.: Molecular and ionized gas properties in pressure balanced ISM of starburst galaxies



**Appendix A:** **Emission line and WISE colour fluxes**


Table A.1: Summary of the emission line and WISE colour
fluxes used in this work and taken from the GAMA DR3 (Baldry
et al. 2018). _W_ 1, _W_ 2, and _W_ 3 correspond to the ‘profile-fit photometry’ WISE filter fluxes measured at 3.4, 4.6 and 12µm (Cluver et al. 2014). The uncertainties indicate 1-σ errors. Our three
galaxies are catalogued as unresolved by WISE.


Model HATLAS090750 HATLAS114625 HATLAS121446


f Hβ (× 10 [−][17] erg/s/cm [2] ) 552±16 76±23 29±11

f [O III] (× 10 [−][17] erg/s/cm [2] ) 402±14 196±34 11±8


f Hα (× 10 [−][17] erg/s/cm [2] ) 2680±33 307±18 588±25


f [N II] (× 10 [−][17] erg/s/cm [2] ) 1016±17 444±17 286±17


_W_ 1 (mJy) 1.15±0.03 1.57±0.03 0.59±0.02


_W_ 2 (mJy) 1.04±0.03 2.40±0.05 0.66±0.02


_W_ 3 (mJy) 16.89±0.41 11.99±0.34 8.65±0.35


**Appendix B:** **Experimental observation results**


We performed an on-source experimental jittering pattern to optimise the S/N of the Paα emission line for HATLAS090750. In
this experimental observation, the pointing was kept fixed at the
galaxy location. Hence, an ‘OOOO’ jitter sequence was used.
As we do not observe the sky during this observation, then the
emission and telluric absorption bandpass lines need to be subtracted using sky models. We specifically used the SkyCor and
Molecfit pipelines. It implies that the performance of this experimental observation is mainly limited by the accuracy of the sky
emission modelling and the ability to detect the line emission
(S/N≳ 15; Godoy et al. in prep.).

Fig. 2 clearly shows that we were able to detect the targeted
emission line (Paα) for this galaxy (S/N = 80). We were also able
to observe many other fainter near-IR emission lines (Table C.1)
that allowed us to study the conditions of the host molecular gas
ISM (Appendix C). Faint tidal features were also detected for
this system, demonstrating the ability of this observation to recover the galaxy spatial distribution when compared, for example, to the CO(1-0) observation (Fig. 3). Thus, this experimental observation delivered more information than that initially expected and allowed us to study HATLAS090750 in great detail.

Even though we have not provided a reliable flux calibration
for HATLAS090750, we note that this was because we were unable to accurately model the telluric standard star (HD 56006)
observation. For most of the observed telluric standards, the effective temperature agrees well in the literature with very low
dispersion, allowing an appropriate calibration using a black
body. However, HD 56006 has very uncertain stellar parameters
(e.g. Niemczura et al. 2009; Lefever et al. 2010), making a reliable calibration impossible even in the case when more sophisticated approaches were attempted. We highlight that this problem
is only related to this standard star observation. If a flux standard star had been observed, then the ‘OOOO’ observation flux
calibration would have been straightforward. Thus, we conclude
that our observational experiment was a success. We recommend
adopting this experimental ‘OOOO’ observational setup when
the expected line emission S/N is ∼15 or greater.



Table C.1: Spatially-integrated Br δ λ1.944µm, ro-vibrational
H 2 (1-0)S(3)λ1.957µm, H 2 (1-0)S(2)λ2.033µm, H 2 (10)S(1)λ2.122µm and Heiλ2.058µm fluxes relative to the
Paα emission line flux. We note that the H 2 (1-0)S(1) emission
is redshifted out of the SINFONI _K_ -band wavelength range
for the later two galaxies. The upper emission line flux limits
are calculated as r.m.s. × σ Paα,ch, where the r.m.s. values are
estimated within a 30 channel spectral window width centred at
the expected emission line location in the spectra, and σ Paα,ch is
the Paα emission line width.


HATLAS090750 HATLAS114625 HATLAS121446

Br δ /Paα 0.055±0.002 < 0.12 < 0.08
H 2 (1-0)S(3)/Paα 0.063±0.005 0.107±0.006 < 0.08
H 2 (1-0)S(2)/Paα 0.028±0.006 < 0.17 < 0.33
H 2 (1-0)S(1)/Paα 0.072±0.016 — —
Hei/Paα 0.051±0.006 < 0.27 <0.29


**Appendix C:** **Near-IR emission lines**


Near-IR emission lines are useful to determine the excitation mechanism of the gaseous line-emitting ISM. Similar to
the well-established optical diagnostic diagrams (e.g. BPT diagram), the ratio between star-formation line tracers (e.g. Paα,
Paβ) and shock tracers such as ro-vibrational molecular hydrogen emission lines (e.g. H 2 (1-0)S(1)λ2.122µm) or forbidden iron
lines ([Feii]λ1.64µm) can be used to determine the dominant excitation mechanism (e.g. Larkin et al. 1998; Riffel et al. 2013;
Fazeli et al. 2019).
From the central brightest pixels from our SINFONI _K_ -band
observations, we detected more near-IR emission lines than only
Paα (Fig. 2). By considering a circular aperture with a radius
equal to the PSF FWHM and centred at the galaxy Paα luminosity peak, we measure several other emission lines fluxes (see
Table C.1). These values are estimated by fitting a Gaussian
function to each emission line in the spatially-collapsed spectrum and the 1-σ uncertainties are derived by bootstrapping via
Monte-Carlo simulations the flux-density errors. These ratio values are corrected by assuming a Calzetti et al. (2000) attenuation law ( _A_ Paα = 0.145 _A_ _V_, _A_ Br δ = 0.132 _A_ _V_, _A_ HeI = 0.113 _A_ _V_,
_A_ H 2 (1−0)S(3) = 0.130 _A_ _V_, _A_ H 2 (1−0)S(2) = 0.117 _A_ _V_, _A_ H 2 (1−0)S(1) =
0.103 _A_ _V_ ). We note that this correction is determined by the
shape of the assumed attenuation law.
We can only apply the near-IR emission line analysis to the
HATLAS090750 galaxy as we lack of enough H 2 emission line
flux measurements for the other two systems. For this galaxy,
we use the Paα flux intensity to differentiate between the possible excitation mechanisms. The other option, the use of the
Br γ emission line, is impeded given that this emission line is
redshifted out of the SINFONI _K_ -band wavelength range. This
means that the H 2 (1-0)S(1)/Br γ ≈ 0.8 ratio that differentiates between star-forming regions and SNR shocks and compact AGN
activity is translated to H 2 (1-0)S(1)/Paα ≈ 0.07 (assuming a
Br γ -to-Paα intrinsic ratio of 12.19 (Case B recombination, Osterbrock & Ferland 2006).
HATLAS090750 shows a central H 2 (1-0)S(1)/Paα ratio consistent with the median value measured for local LIRGs ( _z_ ≲
0.02; Colina et al. 2015). This ratio suggests that there is no clear
dominant gas excitation mechanism in this galaxy, likely with a
combined effect between UV photons produced by young O-B
stars, SNR shocks and weak AGN activity (Colina et al. 2015).
The detection of Heiλ2.058µm suggests that we are witnessing a young central starburst probably induced by the ongoing
merger. Unfortunately, we can not constrain the ISM physical


Article number, page 19 of 22

_A&A proofs:_ manuscript no. manuscript



**2**


**1**







**7000** **7500** **8000** **8500**

Energy of upper level [K]


Fig. C.1: Gas excitation diagram for the H 2 emission coming from the central part of the HATLAS090750 galaxy. The
_N_ ν, _J_ / _g_ ν, _J_ ratios are normalized to the value inferred from the
H 2 (1-0)S(3) emission line transition. The population levels are
well-characterized by a Boltzmann distribution suggesting that
the warm H 2 gas is in LTE.


properties from this emission line as we lack of the detection of
additional Hei emission lines (e.g. Benjamin et al. 1999).
We further characterize the HATLAS090750’s ISM warm
molecular gas phase by using the log _N_ ν, _J_ / _g_ ν, _J_ − _E_ excitation diagram (Davies et al. 2003). In this diagram, _N_ ν, _J_ is the molecular column density, _g_ ν, _J_ is the statistical weight and _E_ is the
upper energy level of the ro-vibrational transition. From the H 2
emission line fluxes _f_ ν, _J_, the column densities in the upper rovibrational levels are computed as:



H 2 emission line observations with different vibrational energy
levels (Bedregal et al. 2009).
Nevertheless, our _T_ rot estimate is slightly higher but still consistent with the average value (< _T_ rot >∼ 1360 ± 390 K) reported
for local ( _z_ < 0.08) LIRGs (U et al. 2019).


**Appendix D:** **Beam smearing effect on the rotation**
**velocity values**


Accurate rotation velocities can not be derived toward the centre of galaxies due to beam-smearing effects. Rotation velocities
tend to be underestimated due to the flux-weighted nature of the
data convolution with the PSF and/or synthesized beam. Thus, a
beam-smearing correction needs to be applied.
Based on our best-fit two-dimensional models, we quantify the beam-smearing effect on rotation velocities by computing the beam-smeared to intrinsic arctan best-fit velocity
model ratio and measured across the galaxy major kinematic
axis. We show the estimation of this ratio in Fig. D.1 for the
ALMA and VLT-SINFONI observations of the HATLAS114625
and HATLAS121446 galaxies. We find that a moderate beamsmearing correction (≲10 %) needs to be applied to the rotation
velocity values measured at a galactocentric radius longer than
1.5× projected synthesized beam/PSF FWHM. At smaller radii,
the beam-smearing effect tends to increase dramatically.



HATLAS114625



HATLAS121446







1.00


0.95


0.90


−6 −4 −2 0 2 4
Radius [kpc]



4π _f_ ν, _J_
_N_ ν, _J_ ≡ � _A_ _ul_ Ω



λ
�� _hc_



, (C.1)
�



**1.00**


**0.95**


**0.90**


**−6** **−4** **−2** **0** **2** **4** **6**

Radius [kpc]



where Ω is the spectrum extraction aperture size, _A_ _ul_ is the
Einstein coefficient computed by Wolniewicz et al. (1998) and
λ/ _hc_ is the photon energy. Additionally, the _N_ ν, _J_ / _g_ ν, _J_ ratios
need to be normalized to a specific population distribution value
_N_ ν 0, _J_ 0 / _g_ ν 0, _J_ 0 given from a determined H 2 transition. We normalize them to the inferred value from the H 2 (1-0)S(3) emission line
transition (e.g. Bedregal et al. 2009). We note that, if the warm
molecular gas phase is in LTE, then the data are well described
by a simple linear function that represents a Boltzmann distribution characterized by a single excitation temperature.
In Fig. C.1 we show the excitation diagram. As we lack of H 2
emission line intensity measurements with different vibrational
energy levels, we can only measure rotational temperature _T_ rot
for the vibrational H 2 (ν = 1 − 0) transition. We find that the data
are well-fitted by a linear fit with _T_ rot ≈ 1600±400 K, suggesting
that the warm H 2 ISM phase in the central brightest zone of this
galaxy is in LTE.
This temperature value also suggests that the warm H 2 gas
may be mainly heated by SNR shocks (Brand et al. 1989; Oliva
et al. 1990), with perhaps some contribution from thermal Xray heating from SNRs ( _T_ rot ≳ 2000 K, e.g. Draine & Woods
1990). Thermal UV heating is unlikely as models suggest lower
temperature values ( _T_ rot ≲ 1000 K, Sternberg 1989). However,
we stress that we can not rule out non-thermal UV excitation
(e.g. fluorescence; Black & van Dishoeck 1987) as we lack of


Article number, page 20 of 22



Fig. D.1: Beam-smearing effect on the recovered rotation velocity values across the major kinematic axis for HATLAS114625
( _Left_ ) and HATLAS121446 ( _Right_ ) galaxies. We mask the values
at _R_ ≤ 0.5× synthesized beam/PSF FWHM due to the highly uncertain estimates and to improve visualization. We colour-code
in the same way as Fig. 4. At a radius _R_ ≳ 1.5× synthesized
beam/PSF FWHM from the dynamical centre, we estimate that a
moderate correction (≲10 %) needs to be applied to the observed
rotation velocity values.


**Appendix E:** **SINFONI** _**K**_ **-band continuum maps**


In Fig E.1 we show the continuum maps used to calculate the
pixel-by-pixel Σ ⋆ values. These maps are scaled to the respective
galaxy _M_ ⋆ value, i.e., by assuming a constant mass-to-light ratio
across the galactic disc.


**Appendix F:** **Full** α **CO** **and Dark Matter PDFs**


Our dynamical mass approach is limited by the degeneracy between α CO and the dark matter fraction _f_ DM variables. Due to our
assumption of a constant α CO value across the galactic disc, then

Juan Molina et al.: Molecular and ionized gas properties in pressure balanced ISM of starburst galaxies







Fig. E.1: SINFONI _K_ -band continuum maps for HATLAS114625 ( _Left_ ) and HATLAS121446 ( _Right_ ) targets.


the dynamical mass value estimated at the innermost galactocentric radius limits the maximum α CO value that can be obtained.
At this radius, _f_ DM is consistent with zero, but it does not necessarily hold at longer radii.
In Fig. F.1, we show the α CO and _f_ DM ( _R_ ) PDFs derived from
the ‘thick-disc plus Sérsic’ dynamical mass model, i.e. the model
that determines the adopted median α CO value in our work.
There is no major difference between the α CO PDF obtained
from this model and those derived from other dynamical models as the broad α CO PDF shapes probe (Fig. 5).
HATLAS114625 galaxy shows a higher increase of _f_ DM
as a function of galactocentric radius compared to the HATLAS121446, suggesting that baryonic matter is distributed more
compactly in this system. It is consistent with the reported _K_ band Sérsic index value (Table 3) and the steeper velocity gradient that is seen in HATLAS114625 (Fig. 4).



Article number, page 21 of 22

_A&A proofs:_ manuscript no. manuscript



CO [ = 0.7] [+0.5] 0.3


CO


CO [ = 1.2] [+1.0] 0.6


CO



f DM (R = 2.7 kpc)



f DM (R = 2.6 kpc) = 0.1 [+0.1] 0.1


f DM (R = 2.6 kpc)


f DM (R = 2.7 kpc) = 0.1 [+0.2] 0.1



f DM (R = 3.2 kpc) = 0.2 [+0.1] 0.1


f DM (R = 3.2 kpc)



f DM (R = 4.3 kpc) = 0.2 [+0.1] 0.1


f DM (R = 4.3 kpc)



f DM (R = 5.6 kpc) = 0.4 [+0.1] 0.1


f DM (R = 5.6 kpc)



f DM (R = 4.2 kpc) = 0.2 [+0.2] 0.1


f DM (R = 4.2 kpc)



f DM (R = 4.9 kpc) = 0.2 [+0.2] 0.1


f DM (R = 4.9 kpc)



f DM (R = 5.6 kpc) = 0.2 [+0.2] 0.1


f DM (R = 5.6 kpc)



f DM (R = 3.5 kpc) = 0.2 [+0.2] 0.1


f DM (R = 3.5 kpc)



Fig. F.1: Corner plot for α CO and _f_ DM ( _R_ ) variables for HATLAS114625 ( _Top_ ) and HATLAS121446 ( _Bottom_ ) starbursts.


Article number, page 22 of 22


</paper>

## Items to check

```json
[
 {
  "path": "software[4].used_for.evidence[0]",
  "value": "SINFONI reduction",
  "failed_quote": "standard SINFONI ESOREX data reduction pipeline"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "emcee MCMC; priors not stated",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[6].fitting.evidence[0]",
  "value": "emcee linear fit in log-log; priors not stated",
  "failed_quote": "(no quote given)"
 }
]
```
