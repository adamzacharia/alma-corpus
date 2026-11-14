# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.524..923Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–24 (2022) Preprint 16 June 2023 Compiled using MNRAS L [A] TEX style file v3.0

## The large molecular gas fraction of post-starburst galaxies at 𝑧> 1


A. Zanella [1] _[★]_, F. Valentino [2] _[,]_ [3], A. Gallazzi [4], S. Belli [5], G. Magdis [3] _[,]_ [6] _[,]_ [7], A. Bolamperti [2] _[,]_ [8]

1 _Istituto Nazionale di Astrofisica, Osservatorio di Padova, Vicolo dell’Osservatorio 5, 35122 Padova, Italy_
2 _European Southern Observatory, Karl Schwarzschild Strasse 2, 85748 Garching, Germany_
3 _Cosmic Dawn Center (DAWN), Copenhagen, Denmark_
4 _Istituto Nazionale di Astrofisica, Osservatorio Astrofisico di Arcetri, Largo Enrico Fermi 5, I-50125 Firenze, Italy_
5 _Dipartimento di Fisica e Astronomia "Augusto Righi", Università di Bologna, via Gobetti 93/2, 40129 Bologna, Italy_
6 _DTU-Space, Technical University of Denmark, Elektrovej 327, 2800, Kgs. Lyngby, Denmark_
7 _Niels Bohr Institute, University of Copenhagen, Lyngbyvej 2, 2100, Copenhagen Ø, Denmark_
8 _Dipartimento di Fisica ed Astronomia, Università degli Studi di Padova, Vicolo dell’Osservatorio 3, I-35122 Padova, Italy_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

Post-starburst galaxies are sources that had the last major episode of star formation about 1 Gyr before the epoch of the observations
and are on their way to quiescence. It is important to study such galaxies at redshift _𝑧>_ 1, during their main quenching phase,
and estimate their molecular gas content to constrain the processes responsible for the cessation of star formation. We present
CO(3-2) ALMA observations of two massive (M _★_ ∼ 5 × 10 [10] M ⊙ ) post-starburst galaxies at _𝑧>_ 1. We measure their molecular
gas fraction to be _𝑓_ H2 = M H2 /M _★_ ∼ 8% - 16%, consistent with _𝑧<_ 1 post-starburst galaxies from the literature. The star
formation efficiency of our targets is ∼ 10× lower than that of star-forming galaxies at similar redshift, and they are outliers of
the _𝑓_ H2 - specific star formation rate (sSFR) relation of star-forming galaxies, as they have larger _𝑓_ H2 than expected given their
sSFR. The gas fraction of post-starbursts from our sample and the literature correlates with the D _𝑛_ 4000 spectral index, a proxy
of the stellar population age. This suggests that their gas content decreases after the last major burst of star formation. Finally,
one of our targets is undergoing a major merger phase with two highly star-forming companions. This hints at a picture where a
perturber event (e.g., major merger) quenches star formation without completely removing the molecular gas.


**Key** **words:** galaxies: evolution _<_ Galaxies, galaxies: formation _<_ Galaxies, galaxies: high-redshift _<_ Galaxies, (galaxies:)
intergalactic medium _<_ Galaxies, galaxies: ISM _<_ Galaxies



**1** **INTRODUCTION**


The existence of a well defined separation among massive, red, earlytype, quiescent galaxies and blue, late-type, actively star-forming objects is a fundamental instrument for the current modeling of galaxy
formation and evolution. Nowadays, the majority of star-forming
galaxies are thought to assemble their mass through a secular process of star formation in a relatively steady state, forming a "Main
Sequence" up to high redshift (Daddi et al. 2007; Speagle et al. 2014)
and following a tight gas-star formation rate (SFR) density relation
(Kennicutt-Schmidt relation, "KS", Schmidt 1959; Kennicutt 1998).
Deviations from this dynamic equilibrium may occur in short starbursting events (associated with major mergers at least in the local
Universe, Sanders & Mirabel 1996) or due to the cessation of star
formation ("quenching", Davis et al. 2016). Both these deviations
from equilibrium are poorly understood: why do galaxies suddenly
ignite the formation of thousands of stars per year? Why do they stop
forming stars?
The deviations from the Main Sequence, observed across redshift,
and the KS relation might be connected: the merger of gas-rich objects may first result in a burst of star formation, followed by a drop
of star formation rate and the subsequent quenching of the galaxy,


_★_ E-mail: anita.zanella@inaf.it


© 2022 The Authors



possibly connected with feedback from active supermassive black
holes or environmental effects (Hopkins et al. 2008). The results
of this process might be the quiescent galaxies, which have been
observed up to high redshift ( _𝑧_ ∼ 2 − 4, e.g., Cimatti et al. 2008;
Toft et al. 2014; Dudzeviči¯ut˙e et al. 2020, (Glazebrook et al. 2017;
Valentino et al. 2020). However, what the mechanism responsible
for stopping star formation is and how galaxies are maintained quiescent for several Gyrs are still matter of debate. Two alternative
physical conditions might be responsible for galaxy quenching: the
gas may be either removed from galaxies or prevented from cooling into molecular clouds. Several scenarios have been proposed,
which we outline in the following. Outflows driven by supernovae
or Active Galactic Nuclei (AGN) can expel gas out of galaxies –
and are the typical quenching mechanisms in simulations (Hopkins
et al. 2012). Ram pressure and tidal interactions can strip it in cluster
environments (Gunn & Gott 1972; Werle et al. 2022). The gas might
be consumed by continuous star formation and black hole growth,
while the normal replenishment from the cosmic web is cut by the
accumulation of hot plasma, inducing shocks and heating up the
infalling gas (i.e, “strangulation”, “starvation”, Larson et al. 1980;
Peng et al. 2015; "halo quenching", Dekel & Birnboim 2006). The
gas can be prevented from cooling because of dynamical stabilization
("morphological quenching", Martig et al. 2009), gravitational heat

2 _A. Zanella et al._


ing (Johansson et al. 2009), or AGN heating ("radio-mode feedback",
also expelling gas, Croton et al. 2006).


To find a way out of this labyrinth, it is key to capture galaxies during or immediately after their quenching, and investigate their molecular gas content and conditions. Galaxies dubbed "K+A", "E+A", or
"post-starburst" (post-SB) are thought to be objects on their way towards quenching. Their spectra are characterized by deep Balmer absorption lines, typical of A-stars dominating the continuum emission
about 1 Gyr after the last major episode of star formation, and little or
no nebular lines associated with ongoing star formation (Dressler &
Sandage 1983; Couch & Sharples 1987; French 2021, and references
therein). They have prominent bulges, but their disturbed morphologies are highly suggestive of recent merging activity (e.g., Zabludoff
et al. 1996; Yang et al. 2008; Wild et al. 2016). Moreover, many
post-SBs lie in the "green valley" of the color-magnitude diagram of
galaxies, suggesting once more their nature of intermediate objects
between gas rich, blue, star-forming galaxies and red, quiescent systems (Wong et al. 2012). Therefore, this population of galaxies has
been a natural choice for sub-millimeter and radio follow-ups in order to constrain their gas content. In the local Universe, a significant
fraction of post-SB galaxies have been detected in neutral atomic hydrogen H I, with intermediate gas fractions similar to gas-poor spirals
and gas-rich early-type galaxies (Zwaan et al. 2013). However, H I is
not a sensitive tracer of the dense gas from which past and new star
formation may occur. Moreover, H I cannot be observed at high redshift, close to the main quenching episode of local massive quiescent
galaxies. The far-infrared continuum dust emission has been used as a
proxy of the cold gas content of post-starburst and quiescent galaxies
up to _𝑧_ ∼ 2 (e.g., Gobat et al. 2018; Michałowski et al. 2019; Whitaker
et al. 2021; Gobat et al. 2022). However such studies yield contradictory results, mainly depending on the method used to estimate the
dust and in turn gas mass of galaxies. Relatively large gas fractions

∼
( 7%) are found when far-infrared spectral energy distributions averaged over large samples are considered (Gobat et al. 2018; Magdis
et al. 2021), whereas smaller gas fractions (∼ 0 _._ 1 − 1%) are found
when individual lensed sources are observed (Whitaker et al. 2021).
Such discrepancies might be due to uncertainties on the photometric
redshift of galaxies entering the stacking, the coarse resolution of
the observations and hence blending of quiescent and star-forming
sources (which affect the first method), uncertainties on the lensing model and magnification of lensed targets especially in case of
extended emission (which affect the second method). Moreover uncertainties about the dust-to-gas conversion factor, dust temperature,
and compactness of the emission might also be responsible for such
discrepancies (Gobat et al. 2022).


An alternative way to constrain the cold gas content of post-SB
and quiescent galaxies is to target carbon monoxide (CO) line transitions, which are a good proxy for the dense molecular phase. If
post-SBs are effectively on their route to quiescence, the presence of
molecular gas points towards quenching mechanisms preventing gas
from forming stars, rather than removing it completely. Several studies have detected substantial molecular gas reservoirs (gas fractions
∼ 10% − 20%) in post-SB galaxies up to _𝑧_ ≲ 0 _._ 1 and have shown
that they have lower star formation efficiency (SFE) than star-forming
galaxies, lying below the KS relation French et al. 2015; Rowlands
et al. 2015; Alatalo et al. 2016; Yesuf et al. 2017; French et al. 2018;
French 2021). From a spatially-resolved analysis, Brownson et al.
(2020) finds, in the central regions of local green valley galaxies,
lower molecular gas fractions and SFE than in star-forming galaxies
and suggest that AGN preventive feedback might inject thermal energy in the ISM, supporting molecular clouds against gravitational


MNRAS **000**, 1–24 (2022)



**Table 1.** Log of the ALMA observations


ID Date t exp Noise R. M. S. Beam
(min) mJy/beam (arcsec)
(1) (2) (3) (4) (5)


97148 09 Jan 2020 50 0.13 1 _._ 6 × 1 _._ 3

83492 09 Jan 2020 35 0.65 1 _._ 9 × 1 _._ 3

**Columns** : (1) Galaxy ID; (2) Date of observations; (3) Integration time on
source; (4) Noise r. m. s.; (5) FWHM of the beam.


collapse, while the prominent bulge stabilizes the ISM against gravitational instabilities, suppressing the SFE (Martig et al. 2009).
To catch quenching in action and understand what its main drivers
are, it is crucial to study galaxies close to their main quenching epoch
at high redshift. Such studies are challenging though, due to the faint
CO emissions of the targets. A handful quiescent galaxies have been
detected in CO at _𝑧_ ∼ 0 _._ 5 − 2 (Sargent et al. 2015; Rudnick et al.
2017; Spilker et al. 2018; Hayashi et al. 2018; Williams et al. 2021)
and they typically are massive systems (M _★_ ≳ 10 [11] M ⊙ ). Similarly,
small samples of massive (M _★_ ≳ 10 [11] M ⊙ ) post-SB galaxies have
been detected in CO (or have stringent upper limits) at high redshift
_𝑧_ ∼ 0 _._ 5−1 _._ 5 (Suess et al. 2017; Bezanson et al. 2019, 2022; Belli et al.
2021). In this study we expand upon those works, including two postSB galaxies at _𝑧>_ 1, with lower stellar masses (M _★_ ∼ 5 × 10 [10] M ⊙ )
than other high-redshift samples from the literature, allowing us to
start widening the explored parameter space.
This paper is organized as follows: in Section 2 we describe the
sample selection and the data set; in Section 3 we discuss how we
estimated the observables (CO and dust continuum flux) and derived
physical properties (molecular gas mass, stellar mass, star formation
rate, stellar age); in Section 4 we discuss our results and scaling
relations among observables; in Section 5 we discuss the possible
mechanisms halting star formation in our galaxies and report on their
environment; finally in Section 6 we conclude and summarize our
findings. Throughout the paper we adopt a flat ΛCDM cosmology
with Ω m = 0 _._ 3, Ω Λ = 0 _._ 7, and H 0 = 70 km s [−][1] Mpc [−][1] . All magnitudes are AB magnitudes (Oke 1974) and we adopt a Chabrier (2003)
initial mass function, unless differently stated.


**2** **DATA**


In this study we focus on two, post-starburst galaxies at _𝑧>_ 1
(ID83492 and ID97148). We aim, by detecting their CO emission,
to estimate their molecular gas content and constrain possible physical mechanisms responsible for galaxy quenching. In addition, we
include samples from the literature (see Section 2.3).


**2.1** **Sample selection and ancillary data**


Our two target galaxies were initially optically selected by Wild et al.
(2014) with other 921 candidates applying a principal component
analysis (PCA) on the spectral energy distributions (SED) based on
the photometry of the Ultra-Deep Survey that comprises data in the
optical _𝐵𝑉𝑅𝑖𝑧_, near-infrared _𝐽𝐻𝐾_, and mid- to far-infrared from
Subaru, _Hubble_ _Space_ _Telescope_ ( _HST_ /WFC3), Very Large Telescope (VLT/VIRCAM, and FORS2), _Spitzer_ and _Herschel_ . Maltby
et al. (2016) confirmed the post-SB nature of a subsample of 19
objects with rest-frame optical spectroscopy, showing deep Balmer
absorption lines (EW(H _𝛿_ ) _>_ 5Å) and no or little [OII]3727 emission associated with star formation and low-luminosity AGN. For

_Large molecular gas fraction of post-SBs at 𝑧>_ 1 3


**Table 2.** Measurements for our sample galaxies


ID RA DEC _𝑧_ CO _𝑧_ opt F CO Δv F cont
(deg) (deg) ( _𝜇_ Jy) km s [−][1] ( _𝜇_ Jy)
(1) (2) (3) (4) (5) (6) (7) (8)


97148 34.3335000 -5.0840889 1.2728 ± 0.0007 1.273 299 _._ 4 ± 78 _._ 2 166 _<_ 60 _._ 1
97148 corrected [1] 34.3335000 -5.0840889 1.2728 ± 0.0007 1.273 687 _._ 7 ± 78 _._ 2 240 _<_ 60 _._ 1

83492 34.5469167 -5.1470694 1.1393 ± 0.0005 1.138 258 _._ 8 ± 50 _._ 9 568 _<_ 69 _._ 3

Companion1 of 83492 34.5475633 -5.1485586 1 _._ 1375 ± 0 _._ 0002 – 789 _._ 0 ± 55 _._ 5 555 48 _._ 9 ± 13 _._ 9
Companion2 of 83492 34.5501383 -5.1491131 1 _._ 1379 ± 0 _._ 0001 – 1054 _._ 3 ± 63 _._ 9 439 65 _._ 3 ± 13 _._ 9


**Columns** : (1) Galaxy ID; (2) Right ascension of the galaxy center from the _𝐻_ -band; (3) Declination of the galaxy center from the _𝐻_ -band; (4) Redshift estimated
by fitting the CO(3-2) emission line with a Gaussian in our 1D ALMA spectra. The uncertainty that we report is the formal error obtained from the fit; (5) Redshift
estimated from the optical spectra (Maltby et al. 2016); (6) CO(3-2) emission line flux; (7) Line velocity width; (8) 5 _𝜎_ upper limits on the continuum emission

flux.
**Notes** : [1] See Section 3.1 for details.



the present study, we selected two objects with stringent star formation rate limits (SFR ≲ 1 M ⊙ yr [−][1] ) and secure spectroscopic redshift
(i.e., marked with flag “4” as being a highly reliable redshift, estimated to have _>_ 99% probability of being correct, based on a high
signal-to-noise spectrum and supported by obvious and consistent
spectral features, Garilli et al. 2021). They are not detected in _Her-_
_schel_ imaging and neither by the Multi-Band Imaging Photometer for
_Spitzer_ (MIPS) at 24 _𝜇_ m or Submillimeter Common-User Bolometer
Array 2 (SCUBA-2) at 850 _𝜇_ m probing the Rayleigh-Jeans tail of the
dust continuum emission down to an r.m.s. of 0.9 mJy/beam (Geach
et al. 2017).
Both targets have rest-frame optical spectra taken with the VIsible
MultiObject Spectrograph (VIMOS) previously mounted on the Very
Large Telescope UT3 and available in the ESO archive. In particular,
we used the spectrum of ID83492 which is already available among
the phase 3 data products released by the VANDELS team [1] . For
ID97148, we reduced the raw data with the VIPGI pipeline (Scodeggio et al. 2005) used by the VANDELS team and following the same
steps used to reduce the spectrum of ID83492 (Pentericci et al. 2018).


**2.2** **ALMA data**


We carried out ALMA Band 4 observations for our sample during Cycle 7 (PI: A. Zanella, Project ID: 2019.1.00900.S) with the
goal of detecting the CO(3-2) emission line at rest-frame frequency
_𝜈_ rf = 345 _._ 795 GHz and the underlying continuum, redshifted in the
frequency range _𝜈_ obs = 150 − 160 GHz.
We observed ID83492 for 35 minutes and ID97148 for 50 minutes

on source and reached a sensitivity of 0.65 and 0.13 mJy/beam,
respectively, over a bandwidth of 150 km s [−][1] . The native spectral
resolution of the observations is 7.812 MHz (∼ 15 km s [−][1] – later
binned to lower velocity resolutions for our purposes). The imaged
beam sizes are FWHM = 1 [′′] _._ 9 × 1 [′′] _._ 3 for ID83492 and 1 [′′] _._ 6 × 1 [′′] _._ 3

for ID97148 (Table 1).
The data were reduced with the standard ALMA pipeline, based
on the CASA software (McMullin et al. 2007). The calibrated data
cubes were then converted to _uvfits_ format and analyzed with the
software GILDAS (Guilloteau & Lucas 2000).


**2.3** **Literature samples**


To obtain a more comprehensive understanding of how quenching acts and cover a larger parameter space, we complemented our


1 `[https://eso.org/rm/api/v1/public/releaseDescriptions/147](https://eso.org/rm/api/v1/public/releaseDescriptions/147)`



observations with data from the literature. To have a sample with
homogeneously-derived molecular gas masses, we only considered
galaxies with CO observations. We excluded from the literature comparison the galaxies with molecular gas mass estimates based on SED
fitting and/or dust continuum observations. In particular we considered samples of star-forming (Saintonge et al. 2011, Tacconi et al.
2013, Freundlich et al. 2019), post-SB (French et al. 2015, Rowlands
et al. 2015, Suess et al. 2017, Bezanson et al. 2019, Belli et al. 2021,
Bezanson et al. 2022), and quiescent (Sargent et al. 2015, Davis et al.
2016, Rudnick et al. 2017, Hayashi et al. 2018, Spilker et al. 2018,
Williams et al. 2021) galaxies up to redshift _𝑧_ ∼ 2. In Appendix A
we briefly describe these literature samples and comment on how the
key properties that are relevant for our analysis (i.e., molecular gas
mass, SFR) have been derived. We report such properties in Table
A1.


**3** **ANALYSIS**


**3.1** **CO emission**


To create the velocity-integrated CO(3-2) line maps for our galaxies
we had to determine the optimal spectral range over which to integrate the spectra. We carried out the following iterative procedure,
similar to the one described in Zanella et al. (2018). Since our targets are expected to be unresolved at the angular resolution of the
observations, we modelled their emission in the _uv_ plane with pointsource profiles in all four sidebands and channel per channel. In this
process, we fixed the spatial position to that determined from the
optical images (Section 2.1). We extracted one-dimensional spectra
using these models and we looked for positive emission line signal
in the resulting spectra. When a signal was present, we averaged the
data over the channels maximizing the detection signal-to-noise ratio
(S/N) and we fitted the resulting two-dimensional (channel-averaged)
map to obtain the best fitting line spatial position. If this was different
from the spatial position of the initial extraction we proceeded to a
new spectral extraction at the new position, and iterate the procedure
until convergence was reached.
We securely detected the CO(3-2) emission line at 5 _𝜎_ and 4 _𝜎_
significance for ID83492 and ID97148, respectively (Figure 1). As
expected, both sources are spatially unresolved. The optimized spatial
position for the spectral extraction of ID83492 is consistent with that
of the optical peak emission in the astrometrically-calibrated _𝐻_ band


MNRAS **000**, 1–24 (2022)

ID83492 CO ID83492 continuum


ID97148 CO ID97148 continuum


[t!]





**Figure** **1.** ALMA data of our sample galaxies. _First_ _column_ : ALMA 2D maps of the CO(3-2) line. The black and white solid contours indicate respectively
positive and negative levels of (9, 7, 6, 5, 4, 3) rms. The beam is reported as the black dashed ellipse. Each stamp has a size of 16" × 16". The black cross
indicates the center of our post-SB targets as estimated from the CO(3-2) emission. Additional serendipitous detections visible in the map of ID83492 are likely
companions (see Sections 3.1 and 5.1). _Second column_ : 1D spectra of sources extracted using a PSF to maximize the S/N. The grey shaded areas indicate the
1 _𝜎_ velocity range over which we measured the CO(3-2) line flux. For illustrative purposes we also report the Gaussian fit of the emissions: it was not used to
estimate the line fluxes, but only as an alternative estimate of the redshift of the galaxies (Section 3.1). We notice that the continuum of ID97148 is on average
below zero despite the fact that the data were not continuum-subtracted. This is due to the negative noise peak which is also visible in the 2D continuum map
(third column). The red Gaussian is the fit to the spectrum, allowing for a negative continuum. _Third column_ : ALMA 2D maps of the continuum emission. The
black and white solid contours indicate respectively positive and negative levels from 4.5 _𝜎_ to 2.5 _𝜎_, in steps of 0.5 _𝜎_ . The black cross indicates the center of
our post-SB targets as estimated from the CO(3-2) emission. The additional detections visible in both maps are likely companion galaxies (see Sections 3.2 and
5.1). _Fourth column_ : _HST_ /WFC3 F160W rest-frame optical continuum imaging (for ID83492) and VIRCAM/ _𝐻_ band imaging (for ID97148). The red contours
show the CO(3-2) emission, while the cyan ones show the continuum emission. Contour levels are the same as in the first and third panels (solid for positive
levels and dashed for negative levels). The ALMA beam is reported as the red shaded ellipse.

from _HST_ /WFC3, falling within the FWHM of the beam (offset
_<_ 0 _._ 25 [′′] ). The spatial position of CO emission of ID97148 instead
is offset by ∼ 1 _._ 6 [′′] with respect to the optical peak emission in
the astrometrically-calibrated _𝐻_ band from VLT/VIRCAM [2] . Despite this offset is within the FWHM of the beam (1 _._ 6 [′′] × 1 _._ 3 [′′] ) we
notice that the _𝐻_ -band photometry show elongation in the direction
of the CO detection which could be tracing an ongoing interaction
(similarly to the EGS-18045 from Belli et al. 2021). Alternatively the
CO emission might originate from a nearby dust-obscured satellite
which is not detected in the near-infrared imaging (e.g., Schreiber
et al. 2018). In this case the molecular gas mass that we estimate for
ID97148 should be considered as an upper limit. However, the fact
that the redshift of the CO (3-2) emission matches the one estimated
from the optical spectrum (velocity difference _𝑣_ off ∼ 47 km s [−][1], consistent with null velocity offset within the uncertainties) rules out the
possibility of a spurious detection [3] . We also highlight that next to
the CO(3-2) detected line there is a negative noise peak which is
evident in the continuum map (Figure 1) and that could hide part of
the emission and artificially offset its peak. To account for the effects
of the negative noise peak on the line emission flux, we fitted the
1D spectrum (Figure 1) with a Gaussian model, allowing for a negative continuum, and estimated the integrated flux of the emission.
We compared it with the integrated flux obtained when forcing the
Gaussian to have zero continuum. We find that the flux doubles when

we account for the negative continuum. Also the velocity width of
the line increases by ∼ 40%. This translates into a molecular gas
mass and molecular gas fraction that are 3 times larger (Section 3.3).
In the following we report both molecular gas estimates.
We estimated the redshift from the CO (3-2) lines in two ways,
both giving consistent results ( _𝛿𝑧<_ 0 _._ 0004): by computing the
signal-weighted average frequency within the line channels and
by fitting the one-dimensional spectrum with a Gaussian function.
We compared these redshift estimates with those obtained from
optical spectra (Maltby et al. 2016) and found that they agree within
1 _𝜎_, increasing the reliability of the CO detection (Table 2). We
finally estimated their CO (3-2) flux by fitting their average emission
line maps in the _uv_ plane adopting the Fourier Transform of a
two-dimensional PSF model with the GILDAS task `uv_fit` . Fluxes

and uncertainties determined with the `uvmodelfit` task provided
by CASA give consistent results. The obtained CO(3-2) total fluxes
are reported in Table 2.


We also serendipitously detected bright emission lines and continuum from two additional galaxies in the surroundings of ID83492
(Figure B1). The lines are detected at 14 _𝜎_ and 16 _._ 5 _𝜎_ and the continuum at 3 _._ 5 _𝜎_ and 4 _._ 7 _𝜎_ respectively (Table 2). They both have
optical counterparts in _Hubble Space Telescope_ Wide Field Camera
3 ( _HST_ /WFC3) imaging from the 3D-HST program (Skelton et al.
2014, Figure 1). Their photometric redshift is _𝑧_ ∼ 1 _._ 1, implying
that the detected line likely is CO(3-2) at _𝑧_ = 1 _._ 1375 ± 0 _._ 0002 and
_𝑧_ = 1 _._ 1379 ± 0 _._ 0001, consistent with the spectroscopic redshift of
ID83492. Given their velocity difference ( _𝑣_ off ∼ 250 km s [−][1] and 195
km s [−][1] ) and projected distance from ID83492 (5 _._ 8 [′′] ∼ 48 kpc and
13 _._ 7 [′′] ∼ 112 kpc), they might be companions that are merging with


2 We calibrated the astrometry of the VIRCAM data against Gaia DR3 by using 30 non-saturated stars in the field of view. Uncertainties on the calibration
(estimated as the standard deviation of the Δ( _𝑅𝐴_ ) and Δ( _𝐷𝐸𝐶_ ) offsets) are
_𝜎_ RA ∼ 0 _._ 08 [′′] and _𝜎_ DEC ∼ 0 _._ 06 [′′] .
3 If we fit the CO map at the optical position of the galaxy, we retrieve a 3 _𝜎_
CO flux upper limit _𝑓_ CO _<_ 235 _𝜇_ m, and a corresponding molecular gas mass
M H2 _<_ 3 _._ 2 × 10 [9] M ⊙ .



_Large molecular gas fraction of post-SBs at 𝑧>_ 1 5


our target galaxy. In the literature, different criteria about the velocity
difference and physical proximity are adopted when defining mergers. Galaxies with spectroscopic velocity differences _𝑣_ off ≲ 500 km
s [−][1] and projected distances d proj ≲ 50 kpc are typically considered
as close pairs (e.g., Lin et al. 2008; Patton & Atfield 2008; Lotz et al.
2011; Mantha et al. 2018) and simulations predict that they merge
within less than 1 Gyr (e.g., Conselice 2006). Galaxies with larger
separation (up to ∼ 150 kpc) are still considered pairs (de Ravel et al.
2009; Lotz et al. 2011) and are expected to merge on timescales of
∼ 1 _._ 5 − 2 _._ 5 Gyr, depending on their baryonic mass ratio and orbital parameters (Lotz et al. 2008, 2010b,a). Based on these results,
ID83492 might merge with two companion galaxies within _<_ 2 _._ 5
Gyr. We report their observed and measured properties respectively
in Table 2 and Table 3. We show their CO(3-2) spectra and spectral
energy distributions in Figure B1.


**3.2** **Continuum emission**


We created averaged continuum maps by integrating the spectral
range, after excluding the channels where the flux is dominated by
the CO emission line. None of our main targets is detected. In Table
2, we report the total flux density upper limits that we estimated as
the 5 _𝜎_ uncertainty obtained when fitting, in the _uv_ plane, the Fourier
Transform of a two-dimensional PSF model with center fixed at the

position of the CO detection.
We detected the continuum emission of the two serendipitous
companion galaxies of ID83492 at 3.5 _𝜎_ and 4.7 _𝜎_ significance. We
also serendipitously detected at 4 _._ 8 _𝜎_ the continuum of an additional
source nearby ID97148 (Figure 1). However this source is not detected in CO(3-2) and it does not have a counterpart in current catalogs including ground-based optical observations (Tanaka 2015). A
possible counterpart is found in the catalog by Mehta et al. (2018),
but it has a distance of ∼ 0 [′′] _._ 5 from ID97148 and a photometric
redshift _𝑧_ ∼ 1 _._ 1. The SED fit also returns a very low stellar mass and
SFR (log(M _★_ /M ⊙ ) = 7.7, log(SFR/(M ⊙ yr [−][1] )) = 0.33). Given the
angular distance from ID97148, the redshift difference of Δ _𝑧>_ 0 _._ 15
and the highly uncertain values retrieved from the SED fit, we do
not consider such detection as a companion galaxy, but rather as a
spurious detection or lower-redshift and low-mass interloper.


**3.3** **Molecular gas mass**


We estimated the molecular gas mass of our galaxies from their CO
luminosity. We considered a brightness temperature ratio _𝑟_ 32 = 0 _._ 5
(Carilli & Walter 2013) to account for the excitation of the CO(3-2)
transition with respect to the thermalized case. We then converted the
estimated CO(1-0) luminosity into molecular gas mass by adopting
the standard Milky-Way like conversion factor _𝛼_ CO = 4 _._ 4 M ⊙ K km
s [−][1] pc [2] (Bolatto et al. 2013). This is consistent with most literature
studies used to compare with our results (Section 2.3). We corrected
the molecular gas mass from literature samples that adopt a different
_𝛼_ CO conversion factor to make them consistent with our assumptions.
For our sample galaxies, we obtain molecular gas masses M H2 =
(4 _._ 1 ± 1 _._ 1) × 10 [9] M ⊙ for ID97148 and M H2 = (9 _._ 9 ± 1 _._ 9) × 10 [9]

M ⊙ for ID83492 (Table 3). These uncertainties do not account for
systematic differences in the (unconstrained) excitation and CO-toH 2 factors in post-SB galaxies, but allow to directly compare our
results with the literature on star-forming and quiescent galaxies.
We also estimated an upper limit on the gas mass of our galaxies
by using the ALMA continuum which is probing the Rayleigh-Jeans
tail of the far-infrared dust emission. The continuum at 850 _𝜇_ m in


MNRAS **000**, 1–24 (2022)

6 _A. Zanella et al._


**Figure 2.** Optical and near-infrared photometry and VIMOS spectroscopy for our target post-SB galaxies. _Left column:_ spectral energy distribution modelling.
The filled red circles and solid orange line indicate the observed photometry and the optical spectra that we modelled. The black solid line marks the best-fit
models at fixed _𝑧_ spec calculated by including the spectrum. For ID97148 the gray solid line shows the best-fit model at fixed _𝑧_ spec calculated by excluding the
spectrum. For ID83492 excluding the spectrum produces a comparable fit instead. _Right column:_ VLT/VIMOS spectra. The black curve shows the spectrum,
whereas the gray one shows the associated uncertainties. The vertical red dashed lines mark the main absorption or emission lines.



fact probes a wavelength regime where the dust emission is optically
thin, providing direct information on the dust (and thus gas) content
(Magdis et al. 2012; Scoville & Murchikova 2013; Scoville et al.
2015). By considering the continuum flux upper limits estimated as
in Section 3.2 (Table 2), a spectral index _𝛽_ = 1 _._ 8 (Magdis et al. 2021;
Cochrane et al. 2022), and a specific luminosity at 850 GHz restframe (L _𝜈_ 850 ) to gas mass conversion factor _𝛼_ 850 = L _𝜈_ 850 /M gas =
1 × 10 [20] erg s [−][1] Hz [−][1] M [−] ⊙ [1] (Scoville et al. 2015), we obtained
M gas ≲ 1 _._ 3 × 10 [10] M ⊙ for both galaxies at 5 _𝜎_ . We also stacked
the continuum maps of our target galaxies at the position of the CO
detections, reaching a 5 _𝜎_ upper limit on the flux F cont ≲ 9 _._ 1 _𝜇_ Jy. This
implies an upper limit on the average gas mass M gas ≲ 9 _._ 2×10 [9] M ⊙ .
These upper limits are consistent with the molecular gas estimates
obtained from CO within the uncertainties related not only to the
flux measurements, but also to the conversion factors (e.g., _𝑟_ 32, _𝛼_ CO,
_𝛼_ 850 ).


**3.4** **Stellar mass and star formation rate**


We modelled the multi-wavelength photometric catalog in the SXDS
field described in Kubo et al. (2018). The catalog comprises _𝑢_ -band
data obtained with CFHT/Megacam, _𝐵𝑉𝑅𝑖𝑧_ with Subaru/SuprimeCam, _𝐽𝐻𝐾_ from the UKIRT Infrared Deep Sky Survey (UKIDSS,
Lawrence et al. 2007), and _Spitzer_ observations from the UKIDSS
Ultra Deep Survey (SpUDS; PI: J. Dunlop). We fit the SEDs with
Fast++ [4] (Schreiber et al. 2018) using Bruzual & Charlot (2003)
models, the Chabrier (2003) IMF, delayed SFHs (SFR( _𝑡_ ) ∝ _𝑡𝑒_ [−] _[𝑡]_ [/] _[𝜏]_

with log( _𝜏_ /yr [−][1] ) ∈[6 _._ 5 _,_ 10] in log-steps of 0.1), ages in log-steps


4 `[https://github.com/cschreib/fastpp](https://github.com/cschreib/fastpp)`


MNRAS **000**, 1–24 (2022)



of 0.1 from a minimum of 100 Myr and a maximum set by the
age of the Universe, the Calzetti et al. (2000) dust attenuation curve
( _𝐴_ V ∈[0 _,_ 6] mag), and free metallicities including sub- and supersolar estimates ( _𝑍_ = 0 _._ 008 _,_ 0 _._ 02 _,_ 0 _._ 05). We fixed the redshifts to the
spectroscopic values and modelled the photometry and the spectra
simultaneously. In the case of ID83492, the inclusion of the restframe optical spectrum does not appreciably affect the best-fit parameters obtained by modelling the photometry only (Figure 2). On
the contrary, the spectrum of ID97148 drops more steeply than the
photometry at short wavelengths. We ascribed this difference to an
imperfect flux calibration of the spectrum and compensated for it by
boosting its uncertainties by a factor of 3×. This more conservative
value does not hamper our ability to reproduce the main absorption
features in the spectrum and allows us to simultaneously retrieve the
overall SED shape at longer wavelengths (Figure 2). We note that the
photometry adopted here is consistent with an independent extraction
by Mehta et al. (2018), which supports its validity and constraining
power. In the case of ID83492, the photometry is also consistent
with that from 3D-HST (Skelton et al. 2014). The best-fit parameters
and their uncertainties are reported in Table 3. The latter were estimated both analytically following Avni (1976) and via Monte Carlo
bootstrapping (see Schreiber et al. 2018 for details about the exact
implementation in Fast++).


We also checked for consistency with SED fitting results reported
in the literature (Carnall et al. 2019; Wild et al. 2020). Only one
of our targets (ID83492) is included in those samples and its stellar
mass is reported. Both Carnall et al. (2019) and Wild et al. (2020) fit
the SED with the code BAGPIPES, with Bruzual & Charlot (2003)
spectral synthesis models, assuming a Chabrier (2003) IMF. While
Carnall et al. (2019) parametrizes the SFH with a double-power-law
model, Wild et al. (2020) also allows for a secondary burst of star

formation (exponentially declining) not to force all the stellar mass
production to happen in a single burst. The stellar mass estimated for
ID83492 by Wild et al. (2020) is log(M _★_ /M ⊙ ) = 11 _._ 19 ± 0 _._ 2 when
fitting the photometric data only and log(M _★_ /M ⊙ ) = 11 _._ 08 ± 0 _._ 05
when fitting photometric and spectroscopic data, whereas Carnall
et al. (2019) reports log(M _★_ /M ⊙ ) = 11 _._ 29 ± 0 _._ 2. Our stellar mass
estimate is also consistent with that reported by 3D-HST (Skelton
et al. 2014, log(M _★_ /M ⊙ ) = 10 _._ 86 estimated using the code Fast++)
and that reported by (Mehta et al. 2018, log(M _★_ /M ⊙ ) = 10 _._ 91).
Despite the different assumptions, SFH used, and codes adopted for
the SED fit, all these estimates are consistent within them and with
ours, within the uncertainties.
Both our target galaxies have detected [OII] emission in the optical spectra (Section 2.1). We estimate the dust-corrected [OII] luminosity by using the extinction estimated from the best-fit SED and
accounting for the fact that emission lines are more attenuated than
the stellar continuum (E(B − V) star = 0 _._ 58E(B − V) nebular, Calzetti
et al. 2000). We convert the dust-corrected [OII] luminosity into
SFR by using the calibration by Kewley et al. (2004). We find SFR
= 0 _._ 2 ± 0 _._ 1 M ⊙ yr [−][1] for ID97148 and SFR = 0 _._ 3 ± 0 _._ 1 M ⊙ yr [−][1] for
ID83492, which are consistent, within the uncertainties, with those
estimated from the SED fit. In the following we adopt SFR from the
SED fit for consistency with the estimates obtained in the literature.


**3.5** **Stellar age**


Stellar absorption features in the optical spectra, such as the Balmer
lines, together with the 4000-break (D _𝑛_ 4000) are powerful tools to
constrain the mean stellar age and the recent star formation history
of galaxies (Worthey et al. 1994; Kauffmann et al. 2003; Gallazzi
et al. 2005). From the optical spectra of our galaxies we measure
the Lick indices of the high-order Balmer lines H _𝛿_ F, H _𝛾_ F [5], and
the D _𝑛_ 4000 index following Gallazzi et al. (2014). For ID97148 we
obtain H _𝛿_ F = 7 _._ 1±0 _._ 6, H _𝛾_ F = 7 _._ 0±0 _._ 6, andD _𝑛_ 4000 = 1 _._ 166±0 _._ 010,
whereas for ID83492 we estimate H _𝛿_ F = 5 _._ 1 ± 0 _._ 2, H _𝛾_ F = 2 _._ 9 ± 4 _._ 6,
and D _𝑛_ 4000 = 1 _._ 407 ± 0 _._ 007. We add a 10% error to the error
budget of D _𝑛_ 4000 to account for uncertainties in spectrophotometric
calibration (Figure 3).
We estimated the mean age of the stellar populations of our sample galaxies by adopting the Bayesian approach described in Gallazzi
et al. (2005, 2014). Specifically, we compare the observed D _𝑛_ 4000,
H _𝛿_ F, H _𝛾_ F absorption index strengths with those predicted by a large
Monte Carlo library of model spectra. We adopted the model library described in Zibetti et al. (2017), which comprises 500000
synthetic spectra assuming randomly generated star formation histories (Sandage 1986, allowing both rising and declining phases, with
the addition of random bursts) and metal enrichment histories (see
Zibetti et al. 2017; Zibetti & Gallazzi 2022, for more details). The
base models are Bruzual & Charlot (2003) Simple Stellar Populations in the 2016 version (Chevallard & Charlot 2016). Considering
only the models with a formation epoch compatible with the age of
the Universe at the redshift of our sample galaxies, we construct the
posterior probability function (PDF) of the _𝑅_ -band light weighted
mean stellar age and of the mass-weighted mean stellar age. We take
the median of the PDF as our fiducial value and the 16th and 84th

percentile range as the uncertainties accounting for model degeneracies. We estimate the uncertainties related to using different sets of


5 Note that we choose the H _𝛿_ F and H _𝛾_ F definitions instead of the wider H _𝛿_ A,
H _𝛾_ A used in (Gallazzi et al. 2014) because the latter cannot be measured for

ID97148.



_Large molecular gas fraction of post-SBs at 𝑧>_ 1 7


**Figure 3.** H _𝛿_ F absorption index as a function of D _𝑛_ 4000. Our sample galaxies
(dark green filled circles) are reported together with literature samples from
French et al. (2015, light green crosses), Rowlands et al. (2015, light green
squares), Spilker et al. (2018, orange diamonds), Belli et al. (2021, dark
green cross, partially hidden behind the symbol indicating one of our sample
galaxies), Bezanson et al. (2022, dark green diamonds). Of the sample of
Bezanson et al. (2022) we report only the 4 galaxies that have available
measurements for the H _𝛿_ F index (see Appendix A).


indices to measure ages of high-redshift post-SBs to be ∼ 0 _._ 02 dex
(see Appendix A, point _(viii) High-redshift post-SBs_ ).
As a result, for ID97148 we estimate an _𝑅_ -band light-weighted
mean age of log(age/yr) = 8 _._ 6 ± 0 _._ 1 and for ID83492 log(age/yr) =
8 _._ 9 ± 0 _._ 1. The estimated mass-weighted ages are very similar, only
0.03 dex older, but with larger uncertainties of ∼ 0 _._ 2dex. [6] These
results are consistent with the ages obtained from SED fitting,
within the uncertainties: log(age/yr) = 8 _._ 4 [+] − [0] 0 _[.]_ _._ [5] 3 [for] [ID97148] [and]
log(age/yr) = 9 _._ 4 [+] − [0] 0 _[.]_ _._ [3] 9 [for] [ID83492.] [In] [the] [following] [we] [adopt] [the]
ages estimated from the stellar population analysis. However, adopting those derived from SED fitting instead, would make our results
(e.g., anti-correlation between gas fraction and age, Section 5) even

stronger.


**4** **RESULTS AND SCALING RELATIONS: LINKING M** H2 **,**
**M** _★_ **, SFR, AND REDSHIFT**


**4.1** **Molecular gas fraction evolution with redshift**


Based on the CO(3-2) detections, we estimate gas fractions M mol /M _★_
of 8% and 16% for our sample galaxies. These are comparable to
gas fractions of other post-SB galaxies at similar redshift from the


6 The model library adopted here differs from the one adopted in Gallazzi
et al. (2014), which assumed exponential SFHs with random bursts and fixed
metallicity along each SFH and which is based on the original BC03 SSP
models. The new library results in a better coverage of the index-index diagnostic diagrams. As a reference, we note that adopting the Gallazzi et al.
(2014) library we would estimate ages older by 0.2 dex and 0.1 dex for
ID97148 and ID83492, respectively.


MNRAS **000**, 1–24 (2022)

8 _A. Zanella et al._


**Table 3.** Physical properties of our sample galaxies.


ID log(SFR) [1] log(M _★_ ) [1] M H2 SFE t d log(f H2 ) age
(M ⊙ yr [−][1] ) (M ⊙ ) (10 [9] M ⊙ ) (Gyr [−][1] ) (Gyr) Gyr
(1) (2) (3) (4) (5) (6) (7) (8)


97148 _<_ −0 _._ 14 10 _._ 66 ± 0 _._ 13 4 _._ 1 ± 1 _._ 1 _<_ 0 _._ 20 _>_ 5 _._ 7 −1 _._ 0 ± 0 _._ 1 8 _._ 6 [+] − [0] 0 _[.]_ _._ [1] 1
97148 corrected [2] _<_ −0 _._ 14 10 _._ 66 ± 0 _._ 13 13 _._ 8 ± 1 _._ 6 _<_ 0 _._ 05 _>_ 19 −1 _._ 0 ± 0 _._ 1 8 _._ 6 [+] − [0] 0 _[.]_ _._ [1] 1
83492 −0 _._ 28 ± 0 _._ 40 10 _._ 79 ± 0 _._ 20 9 _._ 9 ± 1 _._ 9 0.05 18.9 −0 _._ 8 ± 0 _._ 1 8 _._ 9 [+] − [0] 0 _[.]_ _._ [1] 1
Companion1 of 83492 2 _._ 47 [+] − [0] 0 _[.]_ _._ [24] 63 10 _._ 57 ± 0 _._ 10 29 _._ 5 ± 2 _._ 1 10 _._ 00 0.10 0 _._ 13 ± 0 _._ 1         Companion2 of 83492 2 _._ 93 [+] − [0] 0 _[.]_ _._ [01] 63 10 _._ 80 ± 0 _._ 20 31 _._ 1 ± 1 _._ 9 27 _._ 37 0.04 0 _._ 31 ± 0 _._ 2         

**Columns** : (1) Galaxy ID; (2) For the two post-SBs: SFR averaged over 10 Myr from the SED modelling; for the two companions: SFR averaged over 100 Myr
from the SED modelling; (3) stellar mass from the SED modelling; (4) molecular gas mass estimated from CO (3-2) adopting _𝑟_ 31 = 0 _._ 5 and _𝛼_ CO = 4.4 M ⊙ K
km s [−][1] pc [2] (Section 3.3); (5) star formation efficiency, SFE = SFR/M H2 ; (6) depletion time, t d = M H2 /SFR (7) gas fraction, f H2 =M H2 /M _★_ ; (8) average _𝑅_ -band
light-weighted age from stellar population modelling.
**Notes:** [1] The uncertainties on the quantities derived from the SED modelling (Section 3.4) represent the 95% confidence interval. [2] See Section 3.1 for details.
Stellar masses and SFRs have all been homogenized to Chabrier (2003) IMF, and molecular gas masses have been homogenized to _𝛼_ CO = 4 _._ 4 K km s [−][1] pc [2] .


**Figure 4.** Evolution of the molecular gas fraction with redshift. We show our two post-starburst galaxies (dark green circles, with the filled/empty circle indicating
the measurements for ID97148 obtained without or with the correction for the negative continuum, see Section3.1), as well as the star forming companions
of ID83492 (cyan emtpy circles). We also report star-forming (Saintonge et al. 2011; Tacconi et al. 2013; Freundlich et al. 2019, blue and cyan symbols),
quiescent (Sargent et al. 2015; Davis et al. 2016; Rudnick et al. 2017; Spilker et al. 2018; Hayashi et al. 2018; Williams et al. 2021, red and orange symbols),
and post-starburst (French et al. 2015; Rowlands et al. 2015; Suess et al. 2017; Belli et al. 2021; Bezanson et al. 2019, 2022, green symbols) galaxies from the
literature. The darkness of symbols correlate with their redshift (lighter colors at lower redshift). Upper limits are indicated with arrows. Typical error bars for
the largest statistical samples (Saintonge et al. 2011; Davis et al. 2016; Tacconi et al. 2013; Freundlich et al. 2019) are shown as vertical bars in the top left
corner. The black curve shows the evolution of the main-sequence for galaxies with stellar masses 9 _._ 0 ≲ log(M _★_ /M ⊙ ) ≲ 11 _._ 8 (Tacconi et al. 2018). The gray
shaded area shows a 0.2 dex scatter, corresponding to the 1 _𝜎_ scatter of the main-sequence. The dashed curve corresponds to a factor 10 vertical shift of the
main-sequence.


MNRAS **000**, 1–24 (2022)

literature (Belli et al. 2021; Bezanson et al. 2019; Suess et al. 2017)
which have M mol /M _★_ ∼ 5 – 25%. Such gas fractions are comparable
or larger than those measured in quiescent galaxies at high redshift
(Spilker et al. 2018; Hayashi et al. 2018; Rudnick et al. 2017; Sargent
et al. 2015) which are often not detected and have M mol /M _★_ ≲
15%. In Figure 4 we show the molecular gas fraction of galaxies as
a function of redshift. We compare different populations: post-SB
(our sample, Suess et al. 2017, Bezanson et al. 2019, Belli et al.
2021), quiescent (Sargent et al. 2015; Davis et al. 2016; Rudnick
et al. 2017; Hayashi et al. 2018; Spilker et al. 2018; Williams et al.
2021), and star-forming (Saintonge et al. 2011; Tacconi et al. 2013;
Freundlich et al. 2019) galaxies with spectroscopic redshifts in the
range 0 _<_ _𝑧<_ 2.
The gas fraction of star-forming galaxies increases with redshift,
with _𝑧_ ∼ 1 − 1 _._ 5 sources having one order of magnitude higher
M mol /M _★_ than local ones in agreement with the evolution of the
main-sequence parametrized by Tacconi et al. (2018). In the local
Universe the molecular gas fraction of quiescent galaxies is ≳ 10×
lower than that of star-forming systems at the same redshift (Figure
4). At _𝑧>_ 0 _._ 5 the CO line of most quiescent galaxies is not detected
and therefore _𝑓_ H2 is an upper limit. Deeper observations are needed
to confirm whether high-redshift quiescent galaxies are indeed more
gas-rich than local ones. Post-starburst galaxies at _𝑧>_ 0 _._ 5 on the
contrary have been mostly detected in current CO observations and
have intermediate _𝑓_ H2 between star-forming and quiescent systems.
In particular, our post-SB galaxies double the sample currently available at _𝑧>_ 1 and have intermediate gas fraction between quiescent
and star-forming ones (Figure 4). The other two post-SBs at _𝑧>_ 1
from the literature with CO observations are from Bezanson et al.

(2019) (not detected in CO) and Belli et al. (2021) (CO detected).
The latter study analyzes three massive galaxies at 1 _<_ _𝑧<_ 1 _._ 3,
selected to be detected at 24 _𝜇_ m. We only consider the one which
is classified as post-SB, namely EGS-17533, which has a gas fraction _𝑓_ H2 ∼ 13%. This is consistent with the results obtained for our
post-SB targets ( _𝑓_ H2 ∼ 8% - 16%), which are not detected at 24 _𝜇_ m
instead.

While the decline of gas fraction with redshift is evident for starforming galaxies, such an evolution is less clear (and possibly absent)
for post-SBs . In particular, post-SBs seem to divide in two populations: those with gas fraction f H2 ≳ 5% at all redshifts (from _𝑧_ ∼ 0
up to _𝑧_ ∼ 1 _._ 5), and those which are not CO detected and have
molecular gas fraction upper limits f H2 ≲ 1% − 5%, more similar to
high-redshift quiescent galaxies (Figure 4). The latter are, for example, the 8 post-SBs from the sample of Bezanson et al. (2022) which
are not CO-detected and have _𝑓_ H2 _<_ 1%. They are among the most
massive (M _★_ _>_ 2 _._ 5 × 10 [11] M ⊙ ) and oldest (time since quenching
_>_ 0 _._ 1 Gyr, D _𝑛_ 4000 _>_ 1 _._ 3) post-SBs reported in the literature, suggesting that quenching mechanisms could depend on galaxy mass
(see Section 5).


**4.2** **Star formation efficiency and Kennicutt-Schmidt plane**


By comparing the SFR and the molecular gas mass of galaxies in the
traditional Schmidt-Kennicutt plane (Kennicutt 1998) it is possible
to assess their star formation efficiency and in turn set constraints on
models of galaxy quenching. We show the SFR - M H2 relation of our
sample and literature galaxies in Figure 5 (right panel). Star-forming
galaxies at all redshifts follow a tight relation with a scatter of ∼ 0 _._ 2
dex, mostly independent of redshift (Sargent et al. 2014). Also the
local quiescent galaxies from Davis et al. (2016), which sample the
low-SFR and low-M mol part of the parameter space, appear to follow
such relation. Quiescent and post-SB systems at _𝑧>_ 0 _._ 5 instead



_Large molecular gas fraction of post-SBs at 𝑧>_ 1 9


show a systematic offset from this relation toward lower SFR, but
with a large scatter (∼ 1 dex). In particular our two post-SBs have
one order of magnitude lower molecular gas mass and almost two
orders of magnitude lower SFR than star-forming galaxies at similar
redshift (e.g., Tacconi et al. 2013). Their star formation efficiency,
SFE = SFR/M mol ≲ 0 _._ 1 Gyr [−][1], is comparable to those of quiescent
galaxies at similar redshift.


The molecular gas fraction in different samples has been measured
by using different CO line transitions, namely CO(1-0), CO(2-1),
and CO(3-2), and converting them to M H2 by using the excitation
factors _𝑟_ J1 and _𝛼_ CO conversion factor, as discussed in Section 3.3. We
investigated whether the use of different tracers affects the offset and
scatter of quiescent and post-SB galaxies in the Schmidt-Kennicutt
plane by directly comparing their SFR and CO luminosity ( _𝐿_ CO [′] [,]
Figure 5, left panel). The offset from the relation of star-forming
galaxies remains, as well as the scatter. Our sample galaxies have
CO luminosity comparable to _𝑧_ ∼ 0 star-forming galaxies from the
COLDGASS survey (Saintonge et al. 2011) and ∼ 1 dex lower than
star-forming systems at _𝑧_ ∼ 1 _._ 3 (Tacconi et al. 2013).


Another source of uncertainty is the estimate of the SFR for postSB and quiescent galaxies as detecting low levels of star formation
at high redshift is observationally challenging. In the literature SFR
estimated using different tracers have been compared. In particular, Belli et al. (2021) measured the SFR by using three different
methods: UV+IR emission, UV-to-IR spectral fit, and dust-corrected

[OII] emission. They found that the UV+IR-based SFR estimates
are systematically 2 − 6 times higher than those obtained with the
other tracers. This is in agreement with previous findings by Hayward et al. (2014) and Smercina et al. (2018) who pointed out that
the relatively old stellar population hosted by post-SBs heats the dust
leading to a boost in infrared emission which is unrelated to star
formation, hence resulting in higher UV+IR-based SFR estimates
than those obtained when properly modelling the UV-to-IR SED.
They also pointed out that SFR estimates based on dust-corrected
emission lines (e.g., [OII], H _𝛼_, [NeII]+[NeIII]) might be underestimated due to inadequate dust correction and are possibly contaminated by AGN emission. On the other hand, the SFR measurements from SED fitting depend on degeneracies of the parameters
(e.g., degeneracies between metallicity, age, and extinction of the
stellar population) and on the adopted models themselves. In particular SED fitting results for post-SBs are very sensitive to the
choice of star formation history, which can lead to systematic differences in the estimate of SFR up to 0.5 dex (e.g., French et al.
2018, Wild et al. 2020, Suess et al. 2022a). In addition, different
SFR proxies trace different timescales with the emission lines probing younger stellar populations than the continuum. Due to these
reasons, different SFR values are reported in the literature for the
same galaxies. One striking example is SDSSJ0912+1523: Suess
et al. (2017) report a SFR = 2 _._ 1 ± 0 _._ 8M ⊙ yr [−][1] estimated using
the dust-corrected [OII] luminosity; Bezanson et al. (2022) report
a SFR = 0 _._ 81 [+] − [1] 0 _[.]_ _._ [33] 76 [M][ ⊙] [yr] [−][1] [derived] [from] [the] [spectro-photometric]
fit of UV-to-IR data with a set of non parameteric star formation
histories (Suess et al. 2022b); finally Belli et al. (2021) report
three different SFR estimates, SFR _<_ 257M ⊙ yr [−][1] derived from
the weighted sum of the UV and IR luminosities (Bell et al. 2005;
Wuyts et al. 2008), SFR = 52 [+] − [20] 20 [M][ ⊙] [yr] [−][1] [from] [spectral] [fit,] [and]
SFR = 4 _._ 6 ± 1 _._ 4M ⊙ yr [−][1] from the dust-corrected [OII] luminosity
including extra dust attenuation toward the HII regions. In the following, we adopt SFR obtained through SED fit whenever available
and in Appendix A we report the assumptions underlying the SFR
estimates for the literature comparison samples.


MNRAS **000**, 1–24 (2022)

10 _A. Zanella et al._


**Figure** **5.** Schmidt-Kennicutt plane. _Left_ _panel_ : correlation between SFR and CO luminosity for main-sequence, post-starbursts, and quiescent galaxies both
from our work (dark green circles, with the filled/empty circle indicating the measurements for ID97148 obtained without or with the correction for the negative
continuum, see Section 3.1) and the literature (Saintonge et al. 2011; Tacconi et al. 2013; Sargent et al. 2015; French et al. 2015; Rowlands et al. 2015; Davis et al.
2016; Rudnick et al. 2017; Suess et al. 2017; Spilker et al. 2018; Hayashi et al. 2018; Bezanson et al. 2019; Freundlich et al. 2019; Belli et al. 2021; Williams
et al. 2021; Bezanson et al. 2022, symbols as in Figure 4). The black line indicates the redshift-independent relation SFR - M H2 estimated for main-sequence
galaxies by (Sargent et al. 2014), re-scaled by considering _𝛼_ CO = 4 _._ 4 M ⊙ K km s [−][1] pc [2] and _𝑟_ 21 = 0 _._ 8. The gray shaded area is its scatter. The dashed line
corresponds to a factor 10 vertical shift of the main-sequence curve. _Right panel_ : correlation between SFR and molecular gas mass. The black line indicates the
typical relation for main-sequence galaxies (Sargent et al. 2014) and the gray shaded area its scatter. The dashed line corresponds to a factor 10 vertical shift of
the main-sequence curve. All symbols are used as in the left panel.


**Figure 6.** Molecular gas fraction as a function of galaxies specific star formation rate. _Left panel_ : Main-sequence, post-starbursts, and quiescent galaxies both
from our work (dark green circles, with the filled/empty circle indicating the measurements for ID97148 obtained without or with the correction for the negative
continuum, see Section3.1) and the literature (symbols as in Figure 4, Saintonge et al. 2011; Tacconi et al. 2013; Sargent et al. 2015; French et al. 2015; Rowlands
et al. 2015; Davis et al. 2016; Rudnick et al. 2017; Suess et al. 2017; Spilker et al. 2018; Bezanson et al. 2019; Freundlich et al. 2019; Williams et al. 2021; Belli
et al. 2021; Bezanson et al. 2022) are reported. The black and gray lines indicate the relations from Dou et al. (2021) and Feldmann (2020), and the gray shaded
areas represent their scatter. _Right panel_ : Molecular gas fraction versus galaxies sSFR normalized by the star-forming main-sequence at the redshift and stellar
mass of each galaxy from Sargent et al. (2014). Gray shaded areas indicate the relation from Tacconi et al. (2018), computed at different redshifts ( _𝑧_ ∼ 1 _._ 5 dark
gray, _𝑧_ ∼ 0 _._ 5 intermediate shade of gray, _𝑧_ ∼ 0 light gray) and stellar mass (spanning from M _★_ ∼ 10 [10] − 10 [11] M ⊙ from the upper to the lower envelop of each
shaded area). Other symbols are as in the previous panel.


MNRAS **000**, 1–24 (2022)

_Large molecular gas fraction of post-SBs at 𝑧>_ 1 11



**4.3** **Beyond the KS relation: exploring the full parameter space**


Besides that in the Schmidt-Kennicutt plane, other scaling relations
linking galaxies molecular gas reservoirs and star formation activity
have been proposed (Lilly et al. 2013; Tacconi et al. 2013; Scoville
et al. 2017; Tacconi et al. 2018). In particular, the molecular gas
fraction has been compared with the specific star formation rate, sSFR
= SFR/M _★_ of galaxies, as a function of redshift (Tacconi et al. 2020).
Most of such relations though have been investigated considering
samples of star-forming galaxies. Only recently samples of post-SB
and quiescent galaxies have been adopted to investigate the scatter of
such relations at the low-end of the star formation activity (Williams
et al. 2021; Bezanson et al. 2022). Across all redshifts, star-forming
galaxies follow a similar relation (e.g., Feldmann 2020, Dou et al.
2021), but spanning different sSFR regimes [7] . The post-SB galaxies of
this sample instead lie outside such relation, having higher molecular
gas fraction than expected given their sSFR. The deviation is still
present also when considering the relation between _𝑓_ H2 and the sSFR,
normalized by the sSFR of main-sequencegalaxiesfrom Sargent et al.
(2014) (Figure 6, right panel). Our sample post-SBs show similar
star formation activity (sSFR/sSFR MS ) as local quiescent galaxies
(Davis et al. 2016), but they have two orders of magnitude larger gas
fractions. In general, post-SBs span a large range of sSFR/sSFR MS ∼
0 _._ 01−1. Their star-formation activity does not seem to correlate with
redshift nor with gas fraction (Figure 6). This is at odds with starforming galaxies which instead show, on average, a decrease of their
gas fraction with redshift and with sSFR/sSFR MS (Saintonge et al.
2011; Tacconi et al. 2013; Freundlich et al. 2019).
Other post-SB galaxies from the literature show similar gas fractions as ours, but their sSFR/sSFR MS have a large scatter and can
differ up to one order of magnitude (e.g., those by French et al.
2015). While the gas fraction of star-forming galaxies declines with
sSFR/sSFR MS and redshift (in Figure 6 symbols with lighter colors
indicate lower-redshift galaxies), such a trend seems to be lacking for
post-SBs.
However, one additional parameter that plays an important role in
galaxy evolution is the stellar mass (e.g., Peng et al. 2010). In Figure 7
we show the gas fraction of galaxies as a function of their stellar mass,
divided in two redshfit bins ( _𝑧>_ 0 _._ 5, left panel, and _𝑧<_ 0 _._ 5 right
panel). The gas fraction of all galaxy types (star-forming, post-SB,
quiescent) declines with increasing stellar mass, at all redshifts, with
quiescent galaxies typically sampling the highest mass end (M _★_ _>_
10 [11] M ⊙ ) and having the lowest gas fraction. In particular, current
literature studies of post-SB and quiescent galaxies at high redshift
mostly consider massive sources with M _★_ ≳ 10 [11] M ⊙ . Our sample
galaxies have ∼ 0 _._ 3 − 0 _._ 5 dex lower stellar masses, allowing us to
start exploring the gas fraction of post-SBs in this relatively lowmass regime (Figure 7, left panel). More observations of low-mass
post-SBs at high redshift are needed to understand whether indeed
the gas fraction of post-SBs increases at lower stellar masses (e.g.,
as for the star-forming population).


**5** **DISCUSSION**


Different pathways have been proposed to explain the physical properties of post-SB galaxies and their contribution to the population


7 We note that most of the star-forming galaxies from Saintonge et al. (2011)
that seem to deviate from the Feldmann (2020) and Dou et al. (2021) relations
in Figure 6 have sSFR upper limits and are therefore formally consistent with

those relations.



of quiescent galaxies. They might be massive galaxies that have
rapidly formed the bulk of their stellar content at _𝑧>_ 2, consuming
most of their molecular gas reservoirs and expelling the remaining
gas through outflows, leading them to quiescence; however post-SBs
might also be the result of gas-rich major-mergers and/or environment effects that stripped the gas and heated it up preventing new
star formation (Wild et al. 2016; Pawlik et al. 2019). Both processes
might be at play and effective, however it is important to understand
what mechanisms are dominating at different cosmic times, as well as
possible dependences on the galaxies stellar mass and environment.
Our post-SB galaxies span the lowest stellar mass range probed
by currently available samples (Figure 7) and seem to have retained
a significant fraction of molecular gas ( _𝑓_ H2 ∼ 8% - 16%) detected
in CO(3-2), an emission line tracing modestly excited gas. This disfavours scenarios where the gas is consumed and expelled during
strong bursts of star formation, which could instead be more common for more massive galaxies (M _★_ _>_ 10 [11] M ⊙, e.g., Williams et al.
2000 and part of the sample from Bezanson et al. 2022 which is not
CO-detected). When we complement our sample with literature data,
6 out of 7 (i.e., 85%) post-SB or quiescent galaxies with stellar mass
M _★_ ≲ 10 [11] M ⊙ at _𝑧>_ 0 _._ 5 are detected in CO and have f H2 ≳ 8%
(Figure 7). Higher mass galaxies (M _★_ _>_ 10 [11] M ⊙ ) at these redshifts
instead have a lower CO detection rate: only 8 out of 27 are detected
(i.e., 29%) and have gas fraction consistent with our sample postSBs (f H2 ∼ 5 − 20%), whereas the non-detections have typical upper
limits of f H2 ≲ 5%. The large number of non detections among the
high-mass population suggests that multiple mechanisms might be
at play for more massive galaxies: in these cases, not only the star
formation is suppressed (as for the lower mass galaxies), but also
the gas is expelled (e.g., due to AGN or star formation feedback)
or stripped during the quenching phase. For the majority of lower
mass galaxies instead quenching mechanisms that halt star formation
without removing the gas seem to be favoured. Also the fact that
post-SBs, especially at low mass and high redshift, have higher gas
fraction than expected given their sSFR favours the idea that gas is
not expelled before the star formation is quenched or, in other words,
that gas depletion is not a direct cause of star formation suppression.
This is in agreement with results from Bezanson et al. (2022) probing
more massive and lower redshift post-SBs. Mechanisms, such as major mergers, which remove part of the gas and heat up the remaining
(e.g., through shocks or by increasing the internal turbulent pressure,
Smercina et al. 2022) are favoured. Indeed we find that ID83492 is
possibly undergoing an early merger phase with two gas-rich and
starbursting close companions (Section 5.1). We do not find clear
signatures of mergers for ID97148 instead, but this might simply be
due to the lack of high angular resolution observations that prevent
us from detecting close pairs and/or due to the fact that low-surface
brightness features indicative of past mergers fade quickly ( _<_ 0 _._ 5
Gyr, e.g. Pawlik et al. 2019). Studying the CO spectral line energy
distribution would clarify whether indeed the remaining gas is excited
and high- _𝐽_ CO transitions are favoured in post-SB galaxies.
Relating the properties of the stellar population (e.g., age) with
the gas fraction might further constrain the evolutionary pathways
of post-SB galaxies (Bezanson et al. 2022). We investigated whether
a relation between the gas fraction and the D _𝑛_ 4000 index, a proxy
of the age of the stellar population, is in place by complementing
our results with the literature (Figure 8). When considering galaxies
detected in CO at _𝑧>_ 0 _._ 5 − 1 _._ 5 (our sample and Spilker et al. 2018;
Bezanson et al. 2022; Belli et al. 2021) we find that galaxies with
higher gas fraction preferentially have lower D _𝑛_ 4000 (Figure 8, top
panels) and younger ages (Figure 8, bottom panels). We investigated
if, after a first episode that drives the quenching of star formation (e.g.,


MNRAS **000**, 1–24 (2022)

12 _A. Zanella et al._


**Figure 7.** Molecular gas fraction as a function of stellar mass. _Left panel_ : we show high-redshift galaxies ( _𝑧>_ 0 _._ 5). _Right panel_ : we show low-redshift galaxies
( _𝑧<_ 0 _._ 5). The dashed blue and cyan lines indicate the relation from Liu et al. (2019), computed at different redshifts. Symbols are as in previous figures.



major merger), the little ongoing star formation rate (SFR ∼ 0 _._ 5 − 1
M ⊙ yr [−][1] ) can consume the remaining molecular gas reservoir. Even
assuming a constant SFR equal to the one we estimated at _𝑧_ ∼ 1, the
gas fraction of our sample galaxies would decrease by a factor two
(e.g., for ID83492 it would become f H2 ∼ 8%). This is larger than
the f H2 ∼ 1% − 0 _._ 1% measured in _𝑧_ ∼ 0, massive (M _★_ ≳ 10 [11] _[.]_ [5] M ⊙ )
quiescent galaxies (Davis et al. 2016). Similar arguments hold also
for ID97148. This indicates that either lower-mass quiescent galaxies
have larger molecular gas fractions than massive (M _★_ ≳ 10 [11] _[.]_ [5] M ⊙ )
ones or that additional mechanisms are needed to remove or heat the

gas at low redshift.


At lower redshift ( _𝑧<_ 0 _._ 5, French et al. 2015; Rowlands et al. 2015)
a broad anti-correlation of _𝑓_ H2 with D _𝑛_ 4000 is maintained (Figure
8, bottom right panel), although the picture becomes less clear, especially when considering the age estimates, possibly indicating that
more quenching processes might be at play for local post-SBs. For example at lower redshift some post-SB galaxies might have re-accreted
gas (hence show a relatively large gas fraction), while environmental
processes (e.g., ram pressure stripping) and AGN feedback might
have played an important role in local environments. Larger samples
of post-SB and quiescent galaxies with high signal-to-noise optical spectra will be needed to investigate in the future such relations
between _𝑓_ H2 and stellar populations.


Our sample galaxies are not detected in dust-continuum. However,
assuming a standard dust-to-gas conversion factor (Section 3.3) we
obtain M H2 upper limits consistent with the CO-based moelcular
gas mass estimates. This suggests that exotic gas-to-dust ratios (e.g.,
Whitaker et al. 2021) are not needed to explain the molecular gas
fractions observed in post-SB galaxies. However deeper submillimeter observations are needed to detect the dust-continuum underlying
the CO(3-2) emission and properly measure the gas-to-dust ratio in
post-SBs. Moreover, our results seem to confirm that the less massive
post-SB galaxies retain substantial molecular gas reservoirs, possibly in agreement with studies targeting the dust emission of post-SB


MNRAS **000**, 1–24 (2022)



and quiescent galaxies and stacking statistical samples (e.g., Gobat
et al. 2018; Magdis et al. 2021, Blánquez-Sese et al., submitted).
Having deep observations of post-SBs to detect individually their
dust continuum will be crucial to confirm these results.


**5.1** **The merger scenario**


It has been suggested several times in previous studies that poststarburst galaxies represent a transition phase between gas-rich mergers and gas-poor quiescent galaxies. A large fraction of local postSBs in the field show major merger signatures (e.g., strong tidal
features, disturbed kinematics, nearby companions) in _HST_ imaging
(Zabludoff et al. 1996; Yang et al. 2006; Chandar et al. 2021) and in
high-resolution ALMA observations (Smercina et al. 2022). Wilkinson et al. (2022) find that the merger fraction in local post-SBs ranges
between 19% and 42%, depending on the merger identification criteria, but merger signatures fade quickly ( _<_ 200 Myr) and therefore
such fractions might actually be higher. Indeed, when considering
deep _HST_ and SDSS images, Sazonova et al. (2021) find that 88% of
their local post-SBs show disturbed morphologies. They also point
out that most disturbances are low-surface brightness features which
require high sensitivity and fine spatial resolution to be identified,
and that fade in short timescales, suggesting that all their post-SBs
might have had a merger origin. Similar results are also found by Verrico et al. (2022), who also show that post-SBs are 3 _._ 6 [+] − [2] 1 _[.]_ _._ [9] 3 [(2] _[.]_ [1] [+] 0 _._ [1] 73 _[.]_ [9] [)]
times more likely to show disturbances than quiescent (star-forming)
galaxies. In the cosmological hydrodynamical EAGLE simulations,
between 30% and 50% of post-SBs have undergone a merger just before the onset of their post-starburst episode (Davis et al. 2019; Pawlik
et al. 2019). Similarly, idealised simulations of galaxy mergers have
found that a brief ( _<_ 600 Myr) post-starburst phase can follow a gasrich merger which triggers a central starburst phase, succeeded by
the rapid quenching of star formation (Wild et al. 2009; Bekki et al.
2005; Snyder et al. 2011). Studying the morphology of high-redshift

_Large molecular gas fraction of post-SBs at 𝑧>_ 1 13


**Figure 8.** Linking the molecular gas fraction with the properties of the stellar population. _Top panels_ : molecular gas fraction as a function of D _𝑛_ 4000, a proxy
for the galaxy age, for our sample galaxies and literature samples (French et al. 2015; Rowlands et al. 2015; Spilker et al. 2018; Bezanson et al. 2022; Belli et al.
2021) at high redshift ( _𝑧>_ 0 _._ 5, left panel) and low redshift ( _𝑧<_ 0 _._ 5 right panel). _Bottom panels_ : molecular gas fraction as a function of _𝑅_ -band light-weighted
age of the stellar population for the high-redshift (left panel) and low-redshift (right panel) samples. Symbols are as in previous figures.



post-SBs is still challenging, due to the need of high-resolution and
deep observations. Setton et al. (2022) have studied the morphology
of 145 post-SBs at _𝑧_ ∼ 0 _._ 7 and found no correlation between their
size and time since quenching. This finding disfavours the formation
of post-SBs purely through mergers which would instead ignite a
central burst of star formation, that in turn would make the galaxy
more compact and shut off star formation. On the contrary, other
works found that post-SBs are in general smaller than the average
population of quiescent galaxies (e.g., Whitaker et al. 2012; Yano
et al. 2016; Almaini et al. 2017; Wu et al. 2018). Therefore, evidence for mergers being at the origin of post-SBs, especially at high
redshift, is still inconclusive.


To assess whether our sample galaxies are undergoing a merger
we investigated their environment. In particular, we serendipitously
found two CO(3-2) emitters located respectively at 5 [′′] _._ 8 and 13 [′′] _._ 7
away from ID83492. Their redshift, estimated from the CO emission,
is Δ _𝑧<_ 0 _._ 0018 ( _𝑣_ off _<_ 250 km s [−][1] ) different from that of our postSB target. This suggests that ID83492 might be in an early (multiple)
merger stage. Given the stellar masses of the companions, this is
a major merger (mass ratios 1:1 and 1:1.5). ID83492 and its two
companions might be part of a larger galaxy group or be the parents
of a very massive galaxy to be formed by _𝑧_ ∼ 0 through the merger of
these sources. In the current _HST_ and ALMA data we do not detect



tidal features or morphological asymmetries indicating an ongoing
merger, although deeper and higher resolution observations might be
needed to detect those, especially if the merger is in its early phase.
The two companion galaxies are gas-rich, star-forming sources in a
starburst phase (sSFR _>_ 10, Figure 6), lying above main-sequence
galaxies in the KS plane (Figure 5).


On the contrary ID97148 does not show any clear companion, a
part from a continuum-detected source that might rather be a lower
redshift interloper (Section 3.2). Observations with better angular
resolution are needed to understand whether ID97148 is undergoing
a late merger phase with two nuclei which are not resolved with the
current angular resolution (pair closer than ∼ 1 [′′] _._ 5 ∼ 12 _._ 5 kpc at
_𝑧_ ∼ 1 _._ 2). The fact that at least one of our post-SBs is undergoing
a merger suggests that interactions might be a major cause for the
suppression of star formation. The large molecular gas reservoir
measured for ID83492 might be due to the fact that while the merger
episode halts the star formation it does not remove the galaxy ISM
entirely, but leaves a large (∼ 15%) fraction of the molecular gas.
Possibly due to the high excitation and turbulence, the leftover gas
does not form new stars and hence the galaxy becomes a post-SB with
little or no ongoing star formation and still a considerable reservoir
of gas. Another possible scenario is the fact that the post-SB is a
quiescent galaxy which was replenished with molecular gas, stripped


MNRAS **000**, 1–24 (2022)

14 _A. Zanella et al._


from the star-forming companions, during the merger phase. If the
galaxy rejuvenates (i.e., goes through a new spark of star formation)
the correlation between molecular gas fraction with D _𝑛_ 4000 and age
is still expected, whereas it is not if the accreted gas does not produce
new star formation (i.e., the galaxy does not rejuvenate). This shows
the importance of combining measurements of molecular gas tracers
with excellent optical spectra which allow us to accurately determine
absorption indices and hence stellar population ages. Future studies
with larger samples of post-SBs will confirm whether indeed mergers
at high redshift are key ingredients to undertsand the nature of postSB galaxies.


**6** **SUMMARY AND CONCLUSIONS**


We have investigated the molecular gas content (traced by ALMA
CO(3-2) observations) of two post-starburst galaxies at redshift _𝑧_ =
1 _._ 1 − 1 _._ 3 and stellar masses M _★_ ∼ 5 × 10 [10] M ⊙ and complement our
study with literature samples. We find that:


 - our post-SB galaxies retain a significant fraction of molecular
gas ( _𝑓_ H2 ∼ 8% - 16%), which is modestly excited. Such fractions are
consistent with other samples of post-SB galaxies from the literature
and are less than 10 times lower than the gas fraction of star-forming
galaxies at similar redshift (Figure 4). Such gas fractions however
are larger than those found for local quiescent galaxies (e.g., Davis
et al. 2016);

 - our post-SBs have a 10 times lower star formation efficiency
than star-forming galaxies. This result does not depend on the CO
transition that is probed (up to CO(3-2)), indicating that post-SBs
have in general less CO-emitting gas than star-forming galaxies (Figure 5);

 - post-SBs are outliers of the sSFR - _𝑓_ H2 relation of star-forming
galaxies as they have larger molecular gas fraction than expected
given their sSFR. In particular, their molecular gas fraction seems
to be quite constant with redshift, while that of star-forming and
quiescent galaxies decreases with redshift (Figures 4 and 6);

 - our post-SBs probe the lower mass end of current post-SB and
quiescent samples at high redshift ( _𝑧>_ 0 _._ 5). They retain a significant molecular gas fraction ( _𝑓_ H2 ∼ 8% - 16%, similar to other
post-SB and quiescent galaxies at similar redshift, especially with
M _★_ _<_ 10 [11] M ⊙ ), hinting at major mergers as a possible mechanism
at play at _𝑧>_ 0 _._ 5, which halt star formation by increasing the turbulence and excitation of the molecular gas rather than expelling it.
This scenario is supported by the fact that post-SBs have higher gas
fraction than expected given their sSFR (indicating that gas removal
is not the cause of star formation suppression). Moreover, one of our
targets is undergoing a major merger with two nearby companion
galaxies which are actively star forming;

 - the gas fraction of post-SBs seems to decrease with the age
of their stellar population (Figure 8), as suggested also by previous
literature works studying lower-redshift post-SBs (French et al. 2015;
Bezanson et al. 2022). This is in agreement with the scenario that
a perturber event (e.g., major merger) halts star formation without
completely removing the gas. The leftover cold molecular gas is
then exhausted by the low remaining level of star formation and/or
expelled (or heated up) at a later stage.


Having in the future larger samples of high-redshift post-SBs with
CO observations will allow us to confirm the results reported in
this study. In particular, by targeting lower mass post-SBs we can
investigate whether a trend between the _𝑓_ H2 and stellar mass is indeed in place and in turn constrain the role of different quenching


MNRAS **000**, 1–24 (2022)



mechanisms in different M _★_ regimes. In addition, sampling the CO
spectral line energy distribution of post-SB galaxies will allow us to
understand whether indeed the molecular gas is more excited than
in star-forming galaxies. Also having higher-resolution observations
will help to constrain the size of the CO emitting region, its morphology and deblend possible close pairs to clarify whether indeed
mergers are ubiquitous in the post-SB population and in turn constrain their role in the suppression of star formation at cosmic noon.


**ACKNOWLEDGEMENTS**


We thank the referee whose valuable comments helped to clarify the
text and improve the paper. We warmly thank Paolo Franzetti for
his help with the reduction of the VLT/VIMOS data and Masayuki
Tanaka and David Blánquez-Sese for sharing their multi-wavelength
catalog and literature compilation. We also thank Paolo Cassata for
useful discussions. GEM acknowledges financial support from the
Villum Young Investigator grant 37440 and 13160. The Cosmic
Dawn Center (DAWN) is funded by the Danish National Research
Foundation under grant No. 140. This paper makes use of the following ALMA data: 2019.1.00900.S. ALMA is a partnership of ESO
(representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO, AUI/NRAO and
NAOJ.


**DATA AVAILABILITY**


The data used in this study are publicly available from telescope
archives. Software and derived data generated for this research can
be made available upon reasonable request made to the corresponding
author.


**REFERENCES**


[Alatalo K., et al., 2016, ApJ, 827, 106](http://dx.doi.org/10.3847/0004-637X/827/2/106)
[Almaini O., et al., 2017, MNRAS, 472, 1401](http://dx.doi.org/10.1093/mnras/stx1957)
[Avni Y., 1976, ApJ, 210, 642](http://dx.doi.org/10.1086/154870)
[Bekki K., Couch W. J., Shioya Y., Vazdekis A., 2005, MNRAS, 359, 949](http://dx.doi.org/10.1111/j.1365-2966.2005.08932.x)
[Bell E. F., et al., 2005, ApJ, 625, 23](http://dx.doi.org/10.1086/429552)
[Belli S., et al., 2021, ApJ, 909, L11](http://dx.doi.org/10.3847/2041-8213/abe6a6)
Bezanson R., Spilker J., Williams C. C., Whitaker K. E., Narayanan D.,
[Weiner B., Franx M., 2019, ApJ, 873, L19](http://dx.doi.org/10.3847/2041-8213/ab0c9c)
[Bezanson R., et al., 2022, ApJ, 925, 153](http://dx.doi.org/10.3847/1538-4357/ac3dfa)
[Bolatto A. D., Wolfire M., Leroy A. K., 2013, ARA&A, 51, 207](http://dx.doi.org/10.1146/annurev-astro-082812-140944)
[Brownson S., Belfiore F., Maiolino R., Lin L., Carniani S., 2020, MNRAS,](http://dx.doi.org/10.1093/mnrasl/slaa128)


[498, L66](https://ui.adsabs.harvard.edu/abs/2020MNRAS.498L..66B)

[Bruzual G., Charlot S., 2003, MNRAS, 344, 1000](http://dx.doi.org/10.1046/j.1365-8711.2003.06897.x)
Calzetti D., Armus L., Bohlin R. C., Kinney A. L., Koornneef J., Storchi[Bergmann T., 2000, ApJ, 533, 682](http://dx.doi.org/10.1086/308692)
[Carilli C. L., Walter F., 2013, ARA&A, 51, 105](http://dx.doi.org/10.1146/annurev-astro-082812-140953)

[Carnall A. C., et al., 2019, MNRAS, 490, 417](http://dx.doi.org/10.1093/mnras/stz2544)

[Chabrier G., 2003, PASP, 115, 763](http://dx.doi.org/10.1086/376392)
[Chandar R., Mok A., French K. D., Smercina A., Smith J.-D. T., 2021, ApJ,](http://dx.doi.org/10.3847/1538-4357/ac0c19)

[920, 105](https://ui.adsabs.harvard.edu/abs/2021ApJ...920..105C)

[Chevallard J., Charlot S., 2016, MNRAS, 462, 1415](http://dx.doi.org/10.1093/mnras/stw1756)

[Cimatti A., et al., 2008, A&A, 482, 21](http://dx.doi.org/10.1051/0004-6361:20078739)
[Cochrane R. K., Hayward C. C., Anglés-Alcázar D., 2022, ApJ, 939, L27](http://dx.doi.org/10.3847/2041-8213/ac951d)
[Conselice C. J., 2006, ApJ, 638, 686](http://dx.doi.org/10.1086/499067)
[Couch W. J., Sharples R. M., 1987, MNRAS, 229, 423](http://dx.doi.org/10.1093/mnras/229.3.423)
[Croton D. J., et al., 2006, MNRAS, 365, 11](http://dx.doi.org/10.1111/j.1365-2966.2005.09675.x)

_Large molecular gas fraction of post-SBs at 𝑧>_ 1 15



[Daddi E., et al., 2007, ApJ, 670, 156](http://dx.doi.org/10.1086/521818)
[Davis T. A., et al., 2014, MNRAS, 444, 3427](http://dx.doi.org/10.1093/mnras/stu570)

Davis T. A., Greene J., Ma C.-P., Pandya V., Blakeslee J. P., McConnell N.,
[Thomas J., 2016, MNRAS, 455, 214](http://dx.doi.org/10.1093/mnras/stv2313)

Davis T. A., van de Voort F., Rowlands K., McAlpine S., Wild V., Crain R. A.,
[2019, MNRAS, 484, 2447](http://dx.doi.org/10.1093/mnras/stz180)

[Dekel A., Birnboim Y., 2006, MNRAS, 368, 2](http://dx.doi.org/10.1111/j.1365-2966.2006.10145.x)

[Dou J., et al., 2021, ApJ, 907, 114](http://dx.doi.org/10.3847/1538-4357/abd17c)
[Dressler A., Sandage A., 1983, ApJ, 265, 664](http://dx.doi.org/10.1086/160712)
[Dudzeviči¯ut˙e U., et al., 2020, MNRAS, 494, 3828](http://dx.doi.org/10.1093/mnras/staa769)

[Feldmann R., 2020, Communications Physics, 3, 226](http://dx.doi.org/10.1038/s42005-020-00493-0)
[French K. D., 2021, PASP, 133, 072001](http://dx.doi.org/10.1088/1538-3873/ac0a59)

French K. D., Yang Y., Zabludoff A., Narayanan D., Shirley Y., Walter F.,
[Smith J.-D., Tremonti C. A., 2015, ApJ, 801, 1](http://dx.doi.org/10.1088/0004-637X/801/1/1)
[French K. D., Yang Y., Zabludoff A. I., Tremonti C. A., 2018, ApJ, 862, 2](http://dx.doi.org/10.3847/1538-4357/aacb2d)
[Freundlich J., et al., 2019, A&A, 622, A105](http://dx.doi.org/10.1051/0004-6361/201732223)

Gallazzi A., Charlot S., Brinchmann J., White S. D. M., Tremonti C. A., 2005,


[MNRAS, 362, 41](http://dx.doi.org/10.1111/j.1365-2966.2005.09321.x)

[Gallazzi A., Bell E. F., Zibetti S., Brinchmann J., Kelson D. D., 2014, ApJ,](http://dx.doi.org/10.1088/0004-637X/788/1/72)

[788, 72](https://ui.adsabs.harvard.edu/abs/2014ApJ...788...72G)

Gallazzi A. R., Pasquali A., Zibetti S., Barbera F. L., 2021, [MNRAS,](http://dx.doi.org/10.1093/mnras/stab265) [502,](https://ui.adsabs.harvard.edu/abs/2021MNRAS.502.4457G)
[4457](https://ui.adsabs.harvard.edu/abs/2021MNRAS.502.4457G)

[Garilli B., et al., 2021, A&A, 647, A150](http://dx.doi.org/10.1051/0004-6361/202040059)

[Geach J. E., et al., 2017, MNRAS, 465, 1789](http://dx.doi.org/10.1093/mnras/stw2721)

[Glazebrook K., et al., 2017, Nature, 544, 71](http://dx.doi.org/10.1038/nature21680)

[Gobat R., et al., 2018, Nature Astronomy, 2, 239](http://dx.doi.org/10.1038/s41550-017-0352-5)
Gobat R., D’Eugenio C., Liu D., Caminha G. B., Daddi E., Blánquez D.,
[2022, A&A, 668, L4](http://dx.doi.org/10.1051/0004-6361/202244995)

Guilloteau S., Lucas R., 2000, in Mangum J. G., Radford S. J. E., eds,
Astronomical Society of the Pacific Conference Series Vol. 217, Imaging
at Radio through Submillimeter Wavelengths. p. 299
[Gunn J. E., Gott J. Richard I., 1972, ApJ, 176, 1](http://dx.doi.org/10.1086/151605)
[Hayashi M., et al., 2018, ApJ, 856, 118](http://dx.doi.org/10.3847/1538-4357/aab3e7)
[Hayward C. C., et al., 2014, MNRAS, 445, 1598](http://dx.doi.org/10.1093/mnras/stu1843)
[Hopkins P. F., Cox T. J., Kereš D., Hernquist L., 2008, ApJS, 175, 390](http://dx.doi.org/10.1086/524363)
[Hopkins P. F., Kereš D., Murray N., Quataert E., Hernquist L., 2012, MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2012.21981.x)

[427, 968](http://adsabs.harvard.edu/abs/2012MNRAS.427..968H)

[Johansson P. H., Naab T., Ostriker J. P., 2009, ApJ, 697, L38](http://dx.doi.org/10.1088/0004-637X/697/1/L38)
[Kauffmann G., et al., 2003, MNRAS, 341, 33](http://dx.doi.org/10.1046/j.1365-8711.2003.06291.x)

[Kennicutt Jr. R. C., 1998, ApJ, 498, 541](http://dx.doi.org/10.1086/305588)
[Kewley L. J., Geller M. J., Jansen R. A., 2004, AJ, 127, 2002](http://dx.doi.org/10.1086/382723)
Kubo M., Tanaka M., Yabe K., Toft S., Stockmann M., Gómez-Guĳarro C.,
[2018, ApJ, 867, 1](http://dx.doi.org/10.3847/1538-4357/aae3e8)
[Larson R. B., Tinsley B. M., Caldwell C. N., 1980, ApJ, 237, 692](http://dx.doi.org/10.1086/157917)
[Lawrence A., et al., 2007, MNRAS, 379, 1599](http://dx.doi.org/10.1111/j.1365-2966.2007.12040.x)

Lilly S. J., Carollo C. M., Pipino A., Renzini A., Peng Y., 2013, [ApJ,](http://dx.doi.org/10.1088/0004-637X/772/2/119) [772,](https://ui.adsabs.harvard.edu/abs/2013ApJ...772..119L)

[119](https://ui.adsabs.harvard.edu/abs/2013ApJ...772..119L)

[Lin L., et al., 2008, ApJ, 681, 232](http://dx.doi.org/10.1086/587928)
[Liu D., et al., 2019, ApJ, 887, 235](http://dx.doi.org/10.3847/1538-4357/ab578d)
[Lotz J. M., et al., 2008, ApJ, 672, 177](http://dx.doi.org/10.1086/523659)
[Lotz J. M., Jonsson P., Cox T. J., Primack J. R., 2010a, MNRAS, 404, 575](http://dx.doi.org/10.1111/j.1365-2966.2010.16268.x)

[Lotz J. M., Jonsson P., Cox T. J., Primack J. R., 2010b, MNRAS, 404, 590](http://dx.doi.org/10.1111/j.1365-2966.2010.16269.x)

Lotz J. M., Jonsson P., Cox T. J., Croton D., Primack J. R., Somerville R. S.,
[Stewart K., 2011, ApJ, 742, 103](http://dx.doi.org/10.1088/0004-637X/742/2/103)
[Magdis G. E., et al., 2012, ApJ, 760, 6](http://dx.doi.org/10.1088/0004-637X/760/1/6)
[Magdis G. E., et al., 2021, A&A, 647, A33](http://dx.doi.org/10.1051/0004-6361/202039280)
[Maltby D. T., et al., 2016, MNRAS, 459, L114](http://dx.doi.org/10.1093/mnrasl/slw057)
[Mantha K. B., et al., 2018, MNRAS, 475, 1549](http://dx.doi.org/10.1093/mnras/stx3260)

[Martig M., Bournaud F., Teyssier R., Dekel A., 2009, ApJ, 707, 250](http://dx.doi.org/10.1088/0004-637X/707/1/250)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
[Mehta V., et al., 2018, ApJS, 235, 36](http://dx.doi.org/10.3847/1538-4365/aab60c)
[Michałowski M. J., et al., 2019, A&A, 632, A43](http://dx.doi.org/10.1051/0004-6361/201936055)

[Oke J. B., 1974, ApJ, 189, L47](http://dx.doi.org/10.1086/181461)
[Patton D. R., Atfield J. E., 2008, ApJ, 685, 235](http://dx.doi.org/10.1086/590542)



Pawlik M. M., McAlpine S., Trayford J. W., Wild V., Bower R., Crain R. A.,
[Schaller M., Schaye J., 2019, Nature Astronomy, 3, 440](http://dx.doi.org/10.1038/s41550-019-0725-z)
[Peng Y.-j., et al., 2010, ApJ, 721, 193](http://dx.doi.org/10.1088/0004-637X/721/1/193)
[Peng Y., Maiolino R., Cochrane R., 2015, Nature, 521, 192](http://dx.doi.org/10.1038/nature14439)
[Pentericci L., et al., 2018, A&A, 616, A174](http://dx.doi.org/10.1051/0004-6361/201833047)
Rowlands K., Wild V., Nesvadba N., Sibthorpe B., Mortier A., Lehnert M.,
[da Cunha E., 2015, MNRAS, 448, 258](http://dx.doi.org/10.1093/mnras/stu2714)
[Rudnick G., et al., 2017, ApJ, 849, 27](http://dx.doi.org/10.3847/1538-4357/aa87b2)
[Saintonge A., et al., 2011, MNRAS, 415, 32](http://dx.doi.org/10.1111/j.1365-2966.2011.18677.x)
[Sandage A., 1986, A&A, 161, 89](https://ui.adsabs.harvard.edu/abs/1986A&A...161...89S)
[Sanders D. B., Mirabel I. F., 1996, ARA&A, 34, 749](http://dx.doi.org/10.1146/annurev.astro.34.1.749)
[Sargent M. T., et al., 2014, ApJ, 793, 19](http://dx.doi.org/10.1088/0004-637X/793/1/19)
[Sargent M. T., et al., 2015, ApJ, 806, L20](http://dx.doi.org/10.1088/2041-8205/806/1/L20)
[Sazonova E., et al., 2021, ApJ, 919, 134](http://dx.doi.org/10.3847/1538-4357/ac0f7f)
[Schmidt M., 1959, ApJ, 129, 243](http://dx.doi.org/10.1086/146614)
[Schreiber C., et al., 2018, A&A, 618, A85](http://dx.doi.org/10.1051/0004-6361/201833070)
[Scodeggio M., et al., 2005, PASP, 117, 1284](http://dx.doi.org/10.1086/496937)
[Scoville N., Murchikova L., 2013, ApJ, 779, 75](http://dx.doi.org/10.1088/0004-637X/779/1/75)
[Scoville N., Faisst A., Capak P., Kakazu Y., Li G., Steinhardt C., 2015, ApJ,](http://dx.doi.org/10.1088/0004-637X/800/2/108)

[800, 108](http://adsabs.harvard.edu/abs/2015ApJ...800..108S)
[Scoville N., et al., 2017, ApJ, 837, 150](http://dx.doi.org/10.3847/1538-4357/aa61a0)
[Setton D. J., et al., 2022, ApJ, 931, 51](http://dx.doi.org/10.3847/1538-4357/ac6096)
[Skelton R. E., et al., 2014, ApJS, 214, 24](http://dx.doi.org/10.1088/0067-0049/214/2/24)
[Smercina A., et al., 2018, ApJ, 855, 51](http://dx.doi.org/10.3847/1538-4357/aaafcd)
[Smercina A., et al., 2022, ApJ, 929, 154](http://dx.doi.org/10.3847/1538-4357/ac5d5f)
[Snyder G. F., Cox T. J., Hayward C. C., Hernquist L., Jonsson P., 2011, ApJ,](http://dx.doi.org/10.1088/0004-637X/741/2/77)

[741, 77](https://ui.adsabs.harvard.edu/abs/2011ApJ...741...77S)
[Speagle J. S., Steinhardt C. L., Capak P. L., Silverman J. D., 2014, ApJS, 214,](http://dx.doi.org/10.1088/0067-0049/214/2/15)
[15](https://ui.adsabs.harvard.edu/abs/2014ApJS..214...15S)

[Spilker J., et al., 2018, ApJ, 860, 103](http://dx.doi.org/10.3847/1538-4357/aac438)
Suess K. A., Bezanson R., Spilker J. S., Kriek M., Greene J. E., Feldmann
[R., Hunt Q., Narayanan D., 2017, ApJ, 846, L14](http://dx.doi.org/10.3847/2041-8213/aa85dc)
[Suess K. A., et al., 2022a, ApJ, 926, 89](http://dx.doi.org/10.3847/1538-4357/ac404a)
[Suess K. A., et al., 2022b, ApJ, 935, 146](http://dx.doi.org/10.3847/1538-4357/ac82b0)
[Tacconi L. J., et al., 2013, ApJ, 768, 74](http://dx.doi.org/10.1088/0004-637X/768/1/74)
[Tacconi L. J., et al., 2018, ApJ, 853, 179](http://dx.doi.org/10.3847/1538-4357/aaa4b4)
[Tacconi L. J., Genzel R., Sternberg A., 2020, ARA&A, 58, 157](http://dx.doi.org/10.1146/annurev-astro-082812-141034)
[Tanaka M., 2015, ApJ, 801, 20](http://dx.doi.org/10.1088/0004-637X/801/1/20)
[Toft S., et al., 2014, ApJ, 782, 68](http://dx.doi.org/10.1088/0004-637X/782/2/68)
[Valentino F., et al., 2020, ApJ, 889, 93](http://dx.doi.org/10.3847/1538-4357/ab64dc)
[Verrico M., et al., 2022, arXiv e-prints, p. arXiv:2211.16532](http://dx.doi.org/10.48550/arXiv.2211.16532)
[Werle A., et al., 2022, ApJ, 930, 43](http://dx.doi.org/10.3847/1538-4357/ac5f06)
Whitaker K. E., Kriek M., van Dokkum P. G., Bezanson R., Brammer G.,
[Franx M., Labbé I., 2012, ApJ, 745, 179](http://dx.doi.org/10.1088/0004-637X/745/2/179)
[Whitaker K. E., et al., 2021, ApJ, 922, L30](http://dx.doi.org/10.3847/2041-8213/ac399f)
Wild V., Walcher C. J., Johansson P. H., Tresse L., Charlot S., Pollo A., Le

[Fèvre O., de Ravel L., 2009, MNRAS, 395, 144](http://dx.doi.org/10.1111/j.1365-2966.2009.14537.x)

[Wild V., et al., 2014, MNRAS, 440, 1880](http://dx.doi.org/10.1093/mnras/stu212)
Wild V., Almaini O., Dunlop J., Simpson C., Rowlands K., Bowler R., Maltby
[D., McLure R., 2016, MNRAS, 463, 832](http://dx.doi.org/10.1093/mnras/stw1996)

[Wild V., et al., 2020, MNRAS, 494, 529](http://dx.doi.org/10.1093/mnras/staa674)
Wilkinson S., Ellison S. L., Bottrell C., Bickley R. W., Gwyn S., Cuillandre
[J.-C., Wild V., 2022, MNRAS, 516, 4354](http://dx.doi.org/10.1093/mnras/stac1962)

[Williams R. E., et al., 2000, AJ, 120, 2735](http://dx.doi.org/10.1086/316854)
[Williams C. C., et al., 2021, ApJ, 908, 54](http://dx.doi.org/10.3847/1538-4357/abcbf6)
[Wong O. I., et al., 2012, MNRAS, 420, 1684](http://dx.doi.org/10.1111/j.1365-2966.2011.20159.x)
[Worthey G., Faber S. M., Gonzalez J. J., Burstein D., 1994, ApJS, 94, 687](http://dx.doi.org/10.1086/192087)
[Wu P.-F., et al., 2018, ApJ, 868, 37](http://dx.doi.org/10.3847/1538-4357/aae822)
Wuyts S., Labbé I., Förster Schreiber N. M., Franx M., Rudnick G., Brammer
[G. B., van Dokkum P. G., 2008, ApJ, 682, 985](http://dx.doi.org/10.1086/588749)
[Yang Y., Tremonti C. A., Zabludoff A. I., Zaritsky D., 2006, ApJ, 646, L33](http://dx.doi.org/10.1086/506909)
[Yang Y., Zabludoff A. I., Zaritsky D., Mihos J. C., 2008, ApJ, 688, 945](http://dx.doi.org/10.1086/591656)
[Yano M., Kriek M., van der Wel A., Whitaker K. E., 2016, ApJ, 817, L21](http://dx.doi.org/10.3847/2041-8205/817/2/L21)
Yesuf H. M., French K. D., Faber S. M., Koo D. C., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx1046) [469,](https://ui.adsabs.harvard.edu/abs/2017MNRAS.469.3015Y)

[3015](https://ui.adsabs.harvard.edu/abs/2017MNRAS.469.3015Y)

Zabludoff A. I., Zaritsky D., Lin H., Tucker D., Hashimoto Y., Shectman
[S. A., Oemler A., Kirshner R. P., 1996, ApJ, 466, 104](http://dx.doi.org/10.1086/177495)
[Zanella A., et al., 2018, MNRAS, 481, 1976](http://dx.doi.org/10.1093/mnras/sty2394)


MNRAS **000**, 1–24 (2022)

16 _A. Zanella et al._


[Zibetti S., Gallazzi A. R., 2022, MNRAS, 512, 1415](http://dx.doi.org/10.1093/mnras/stac370)

[Zibetti S., et al., 2017, MNRAS, 468, 1902](http://dx.doi.org/10.1093/mnras/stx251)
[Zwaan M. A., Kuntschner H., Pracy M. B., Couch W. J., 2013, MNRAS, 432,](http://dx.doi.org/10.1093/mnras/stt496)

[492](https://ui.adsabs.harvard.edu/abs/2013MNRAS.432..492Z)

[de Ravel L., et al., 2009, A&A, 498, 379](http://dx.doi.org/10.1051/0004-6361/200810569)


MNRAS **000**, 1–24 (2022)



**APPENDIX A:** **LITERATURE DATA**


We complemented our observations with literature samples. We
describe such ancillary datasets and the methods used to derive
the parameters that are relevant for our analysis (redshift, SFR,
molecular gas mass, stellar mass). To properly compare different samples, we homogenized the IMF to Chabrier 2003 adopting the following conversions: SFR Chabrier =SFR Salpeter /0 _._ 63 and
M ∗ _,_ Chabrier =M ∗ _,_ Salpeter /0 _._ 61.
_(i)_ _Local_ _star-forming_ _galaxies_ (Saintonge et al. 2011). Sample of galaxies from the COLD GASS survey with measurements
of the CO(1-0) emission line from the IRAM 30m telescope.
The galaxies have redshift 0 _._ 025 _<_ _𝑧<_ 0 _._ 05 and stellar masses
10 _._ 0 _<_ log(M _★_ /M ⊙ ) _<_ 11 _._ 5. The molecular gas masses have been
estimated considering an _𝛼_ CO = 3 _._ 2 M ⊙ K km s [−][1] pc [2] conversion
factor (throught the paper and in Table A1 we homogenized this
sample to the other literature ones by converting to _𝛼_ CO = 4 _._ 4 M ⊙ K
km s [−][1] pc [2] ). SFRs have been derived through SED fitting assuming
exponentially declining SFHs without bursts.
_(ii) Intermediate-redshift star-forming galaxies_ (Freundlich et al.
2019). Sample of 61 galaxies from the PHIBSS survey with measurements of the CO(2-1) emission from IRAM NOEMA. The
galaxies have redshift 0 _._ 5 _<_ _𝑧<_ 0 _._ 8 and stellar masses 10 _._ 0 _<_
log(M _★_ /M ⊙ ) _<_ 11 _._ 8. The molecular gas masses have been estimated considering an excitation factor _𝑟_ 21 = 0 _._ 77 and a CO-to-H2
conversion factor that depends on metallicity and has an average
value of _𝛼_ CO = 4 _._ 0 M ⊙ K km s [−][1] pc [2] (in Figures and in Table A1
we homogenized this sample to the other literature ones by converting to _𝛼_ CO = 4 _._ 4 M ⊙ K km s [−][1] pc [2] ). SFRs have been derived by
combining UV and IR luminosities to account for both unobscured
and dust-obscured star formation (Kennicutt 1998).

_(iii)_ _High-redshift_ _star-forming_ _galaxies_ (Tacconi et al. 2013).
Sample of 52 galaxies from the PHIBSS survey with measurements
of the CO(3-2) emission from IRAM NOEMA. The galaxies have
redshift 1 _<_ _𝑧<_ 2 _._ 5 and stellar masses 10 _._ 4 _<_ log(M _★_ /M ⊙ ) _<_ 11 _._ 5.
The molecular gas masses have been estimated considering an excitation factor _𝑟_ 31 = 0 _._ 5 and an _𝛼_ CO = 4 _._ 4 M ⊙ K km s [−][1] pc [2]

conversion factor. SFRs have been derived by combining UV and IR
luminosities (Kennicutt 1998).

_(iv)_ _Local_ _quiescent_ _galaxies_ (Davis et al. 2016). Sample of 15
passive galaxies from the MASSIVE survey with measurement of
the CO(1-0) emission from IRAM 30m telescope. The galaxies have
distances _<_ 108 Mpc and stellar masses log(M _★_ /M ⊙ ) _>_ 11 _._ 5. The
molecular gas masses have been estimated considering a conversion
factor X CO = 3 × 10 [20] . SFRs have been derived from _WISE_ 22 _𝜇_ m
as in Davis et al. (2014).

_(v) Intermediate-redshift quiescent galaxies_ (Spilker et al. 2018).
Sample of 8 passive galaxies with measurements of the CO(21) emission from ALMA, at redshift _𝑧_ ∼ 0 _._ 7 and stellar mass
log(M _★_ /M ⊙ ) ∼ 11. The molecular gas masses have been estimated
considering an excitation factor _𝑟_ 21 = 0 _._ 8 and a conversion factor
_𝛼_ CO = 4 _._ 4. SFRs have been derived by combining UV and IR luminosities (Kennicutt 1998). The D _𝑛_ 4000 and H _𝛾_ F indices are from
the LEGA-C DR3 catalog. We estimated the _𝑅_ -band light-weighted
age adopting the same procedure and model assumptions as for our
sample (Section 3.5).
_(vi) High-redshift quiescent galaxies_ (Sargent et al. 2015; Rudnick
et al. 2017; Hayashi et al. 2018; Williams et al. 2021). The galaxy
by Sargent et al. (2015) and Hayashi et al. (2018) have CO(2-1)
measurements at _𝑧_ = 1 _._ 43 from IRAM NOEMA and _𝑧_ = 1 _._ 46 from
ALMA respectively, and have stellar masses log(M _★_ /M ⊙ ) ∼ 11. The
molecular gas masses have been computed by considering an exci

_Large molecular gas fraction of post-SBs at 𝑧>_ 1 17



tation factor _𝑟_ 21 = 0 _._ 8 − 1 and a conversion factor _𝛼_ CO = 4 _._ 4 M ⊙
K km s [−][1] pc [2] . Sargent et al. (2015) estimated the SFRs from SED
fitting assuming an exponentially declining SFH, whereas Hayashi
et al. (2018) from the dust-corrected [OII] emission line.
The galaxy by Rudnick et al. (2017) instead is detected in CO(10) emission from VLA at redshift _𝑧_ = 1 _._ 62, with stellar mass
log(M _★_ /M ⊙ ) ∼ 11. The molecular gas mass has been computed by
considering a conversion factor _𝛼_ CO = 4 _._ 4 M ⊙ K km s [−][1] pc [2] . The
SFR has been estimated from SED modelling, but the used SFH is
not reported.
The sample by Williams et al. (2021) is made of massive quiescent galaxies (log(M _★_ /M ⊙ ) _>_ 11 _._ 3), with CO(2-1) emission from
ALMA at redshift _𝑧_ ∼ 1 _._ 5. The molecular gas masses have been
computed by considering an excitation factor _𝑟_ 21 = 0 _._ 8 and a conversion factor _𝛼_ CO = 4 _._ 4 M ⊙ K km s [−][1] pc [2] . The SFR is estimated
from UV+IR, as well as from SED fitting assuming an exponentially
declyning SFH.
_(vii)_ _Low-redshift_ _post-SBs_ (French et al. 2015; Rowlands et al.
2015). The galaxies in both samples have CO(1-0) observed with
IRAM. They have redshift _𝑧<_ 0 _._ 1 and stellar masses in the range
log(M _★_ /M ⊙ ) ∼ 9 _._ 5 − 11 _._ 3. The molecular gas masses have been
computed considering a conversion factor _𝛼_ CO = 4 _._ 0 M ⊙ K km
s [−][1] pc [2] (French et al. 2015) and _𝛼_ CO = 4 _._ 4 M ⊙ K km s [−][1] pc [2]

(Rowlands et al. 2015). In Figures and in Table A1 we homogenized
the sample of French et al. (2015) to the other literature ones by
converting to _𝛼_ CO = 4 _._ 4 M ⊙ K km s [−][1] pc [2] . French et al. (2015)
estimates the SFR in two ways, from the H _𝛼_ emission and from
the D _𝑛_ 4000 break. Rowlands et al. (2015) estimates the SFR from
SED fitting assuming exponentially declining SFHs with additional
superimposed random bursts (i.e., stochastic SFHs). We used the
D _𝑛_ 4000, H _𝛿_ F, and H _𝛾_ F indices reported in the MPA/JHU catalog [8] .
We have estimated the _𝑅_ -band light-weighted ages of these galaxies
by using only the spectral features adopted also for the high-redshift
samples (D _𝑛_ 4000, H _𝛿_, H _𝛾_ ), for consistency with our sample galaxies.
For the sample by French et al. (2015) these ages are systematically
0.2 dex younger than those estimated using five spectral indices
(D _𝑛_ 4000, H _𝛽_, H _𝛿_ A +H _𝛾_ A, [MgFe]’, and [Mg 2 Fe]) as in Gallazzi et al.
(2021) and the library of SFHs (exponential + burst) and metallicities
(fixed along the SFH) of Gallazzi et al. (2005, 2014). They are instead
0.17 dex younger than the ages estimated using the new SFH library
and varying metallicities as in Zibetti et al. (2017). For the sample by
Rowlands et al. (2015) the systematic differences are slightly smaller,
although there is a fairly large scatter.
_(viii) Intermediate-redshift post-SBs_ (Suess et al. 2017; Bezanson
et al. 2022). Sample of 2 post-SB galaxies with CO(2-1) emission
observed by ALMA. They have a redshift _𝑧_ ∼ 0 _._ 7 and stellar mass
log(M _★_ /M ⊙ ) ∼ 11. The molecular gas mass has been computed by
considering an excitation factor _𝑟_ 21 = 1 and a conversion factor
_𝛼_ CO = 4 _._ 0 M ⊙ K km s [−][1] pc [2] (in Figures and in Table A1 we
homogenized this sample to the other literature ones by converting
to _𝛼_ CO = 4 _._ 4 M ⊙ K km s [−][1] pc [2] ). The SFR has been estimated from
the dust-corrected [OII] luminosity (Kennicutt 1998).
The sample from Bezanson et al. (2022) is made of galaxies at redshift
_𝑧_ ∼ 1 _._ 5, with CO(2-1) observed with ALMA and stellar masses
log(M _★_ /M ⊙ ) ∼ 11 _._ 3. The molecular gas masses have estimated
considering an excitation factor _𝑟_ 21 = 1 and a _𝛼_ _𝐶𝑂_ = 4 _._ 0 M ⊙
K km s [−][1] pc [2] conversion factor (in Figures and in Table A1 we
homogenized this sample to the other literature ones by converting
to _𝛼_ CO = 4 _._ 4 M ⊙ K km s [−][1] pc [2] ). The SFRs have been estimated


8 [Link to the catalog: link](https://wwwmpa.mpa-garching.mpg.de/SDSS/DR7/raw_data.html)



through the joint photometric and spectroscopic modelling, assuming
a custom set of non parametric SFHs. As mentioned in Bezanson
et al. (2022) (their Section 2.1), when making comparisons to scaling
relations, we set a floor value to the SFR = 1 M ⊙ yr [−][1] and consider
those estimates as upper limits. We estimated the ages of all the
13 sample galaxies by fitting the D _𝑛_ 4000 and H _𝛿_ A indices that are
reported in Suess et al. (2022b, Table 1), adopting the same procedure
described in our manuscript (3.5). In the following we refer to this as
“method 1”. As a check, for the 4 galaxies that are also in the SDSS
DR7 catalogue and have measurements of indices from the MPA/JHU
catalogs, we have also estimated the ages by fitting (2) the D _𝑛_ 4000
and H _𝛿_ A indices (as reported in the MPA/JHU catalogue); (3) the
D _𝑛_ 4000, H _𝛿_ F, and H _𝛾_ F (as reported in the MPA/JHU catalogue).
The comparison of the results obtained from methods 1 and 2 allows
us to estimate the uncertainties related to using indices calculated by
different groups to estimate ages. The comparison of results obtained
using method 2 and 3 instead quantifies the uncertainty related to
estimating ages using the H _𝛿_ A index (as reported by Suess et al.
2022b) instead of the _𝐻𝛿_ F and H _𝛾_ F as for our post-SBs. In all cases
we find very small differences (∼ 0 _._ 02 dex).
_(ix)_ _High-redshift_ _post-SBs_ (Bezanson et al. 2019; Belli et al.
2021). The post-starburst galaxy from Bezanson et al. (2019) has
CO(2-1) observations from ALMA at _𝑧_ ∼ 1 _._ 5 and it has a stellar mass log(M _★_ /M ⊙ ) ∼ 11 _._ 2. The molecular gas mass has been
computed by considering an excitation correction _𝑟_ 21 = 1 and a
_𝛼_ _𝐶𝑂_ = 4 _._ 4 M ⊙ K km s [−][1] pc [2] conversion factor. The SFR has been
estimated by combining UV and IR luminosities (Kennicutt 1998).
The sample from Belli et al. (2021) instead is made of 3 poststarburst galaxies with CO(3-2) and CO(2-1) observations from
IRAM NOEMA. They have a redshift 1 _<_ _𝑧<_ 1 _._ 3 and stellar masses
10 _._ 8 _<_ log(M _★_ /M ⊙ _<_ 11 _._ 3. The molecular gas mass has been computed by considering excitation corrections _𝑟_ 31 = 0 _._ 5 and _𝑟_ 21 = 0 _._ 77
and a conversion factor _𝛼_ CO = 4 _._ 4 M ⊙ K km s [−][1] pc [2] . SFRs have been
estimated through SED modelling assuming a nonparametric SFH
consisting of seven independent age bins logarithmically spaced. In
this work we only consider EGS-17533 that is, among their three
sample galaxies, the only one classified as post-SB, having a spectrum dominated by Balmer absorption lines and a SFR that dropped
by an order of magnitude over the last ∼ 500 Myr (Belli et al. 2021).
We estimated the D _𝑛_ 4000, H _𝛾_ F indices, and _𝑅_ -band light-weighted
age adopting the same procedure as for our sample (Section 3.5).


MNRAS **000**, 1–24 (2022)

18 _A. Zanella et al._


MNRAS **000**, 1–24 (2022)



ID _𝑧_ log(M _★_ ) log(L’CO) log(M H2 ) SFR
(M ⊙ ) (K km s [−][1] pc [2] ) (M ⊙ ) (M ⊙ yr [−][1] )
(1) (2) (3) (4) (5) (6)


Local star-forming galaxies (Saintonge et al. 2011)
1 0.0395 10.0 7.9 8.6 0.4

2 0.0384 10.0 8.3 9.1 2.3

3 0.0375 10.0 8.4 9.1 1.4

4 0.0292 10.1 8.0 8.8 0.2

5 0.0484 10.8 8.7 9.4 1.2

6 0.0427 10.7 8.7 9.4 3.0

7 0.0380 10.1 8.3 9.0 0.7

8 0.0453 10.6 9.3 10.0 10.

9 0.0438 10.7 9.4 10.1 9.6

10 0.0427 10.9 9.5 10.2 6.3

11 0.0258 10.2 8.0 8.8 0.6

12 0.0324 10.2 7.9 8.6 0.4

13 0.0491 11.3 9.1 9.8 1.1

14 0.0417 10.7 8.8 9.5 1.4

15 0.0265 10.4 8.9 9.7 4.5

16 0.0262 10.4 8.4 9.1 0.9

17 0.0414 10.5 8.7 9.4 1.5

18 0.0416 10.5 8.6 9.4 4.3

19 0.0264 10.5 8.1 8.8 0.3

20 0.0296 10.3 8.8 9.5 2.4

21 0.0464 10.8 9.1 9.9 1.2

22 0.0345 10.1 8.1 8.8 0.4

23 0.0293 10.4 8.6 9.3 0.7

24 0.0344 10.1 8.5 9.2 1.1

25 0.0340 10.8 8.5 9.2 1.4

26 0.0462 10.8 8.7 9.5 1.8

27 0.0292 10.0 7.9 8.6 0.3

28 0.0328 10.4 7.9 8.6 0.1

29 0.0289 10.6 8.8 9.5 1.7

30 0.0368 10.5 8.6 9.3 2.3

31 0.0296 10.1 8.6 9.3 1.6

32 0.0334 10.6 8.6 9.4 0.7

33 0.0383 10.5 9.1 9.9 4.2

34 0.0323 10.5 8.4 9.1 0.3

35 0.0318 10.0 8.4 9.2 1.1

36 0.0489 10.8 8.8 9.6 5.3

37 0.0318 11.0 8.5 9.2 1.3

38 0.0285 10.3 8.5 9.3 0.8

39 0.0296 10.1 8.4 9.2 1.7

40 0.0299 10.2 8.4 9.2 0.6

41 0.0385 10.3 8.9 9.6 3.3

42 0.0411 10.5 8.8 9.5 1.9

43 0.0299 10.6 8.4 9.2 0.2

44 0.0346 10.5 8.8 9.5 0.9

45 0.0444 11.2 9.0 9.7 1.1

46 0.0317 10.9 9.5 10.2 3.7

47 0.0329 10.2 8.7 9.5 1.7

48 0.0448 11.1 8.6 9.4 1.3

49 0.0455 10.6 9.1 9.8 4.6

50 0.0468 11.1 9.0 9.8 1.4

51 0.0339 10.0 8.1 8.8 1.2

52 0.0316 10.3 7.9 8.6 0.1

53 0.0266 10.4 8.7 9.5 1.4

54 0.0324 10.6 7.8 8.5 0.1

55 0.0348 10.1 8.2 9.0 1.9

56 0.0394 11.1 9.3 10.0 3.6

_Large molecular gas fraction of post-SBs at 𝑧>_ 1 19


57 0.0340 10.3 8.8 9.5 1.0

58 0.0340 11.0 7.9 8.7 0.1

59 0.0432 10.8 8.7 9.5 2.2

60 0.0496 11.3 8.8 9.6 0.9

61 0.0494 10.9 8.5 9.3 0.3

62 0.0341 10.8 9.3 10.0 2.3

63 0.0470 10.7 9.1 9.8 2.4

64 0.0270 10.2 8.4 9.2 1.2

65 0.0366 11.0 8.7 9.4 1.1

66 0.0260 10.4 8.0 8.8 0.1

67 0.0429 10.7 9.1 9.8 4.3

68 0.0492 10.9 8.9 9.7 4.4

69 0.0434 10.6 8.6 9.4 1.8

70 0.0431 11.0 8.7 9.4 0.8

71 0.0338 10.1 8.4 9.1 1.0

72 0.0305 10.1 8.5 9.2 1.2

73 0.0478 10.1 8.4 9.2 12.

74 0.0487 10.7 9.3 10.0 7.0

75 0.0376 11.0 9.2 9.9 2.7

76 0.0483 11.2 8.8 9.5 1.2

77 0.0350 10.9 9.3 10.0 5.3

78 0.0447 10.6 8.4 9.2 1.8

79 0.0343 10.7 8.1 8.8 0.4

80 0.0411 10.3 8.4 9.2 1.2

81 0.0462 11.3 8.9 9.7 1.3

82 0.0269 10.7 8.1 8.9 1.4

83 0.0258 10.7 8.8 9.6 0.7

84 0.0354 10.7 8.7 9.5 2.2

85 0.0267 10.5 7.9 8.6 0.2

86 0.0269 10.9 9.4 10.1 1.8

87 0.0293 10.8 8.7 9.5 0.5

88 0.0405 10.4 8.6 9.4 4.5

89 0.0308 10.6 8.9 9.7 1.0

90 0.0276 10.1 8.5 9.3 0.6

91 0.0464 10.7 9.1 9.8 3.5

92 0.0345 10.1 8.4 9.2 1.4

93 0.0367 10.8 8.4 9.2 0.6

94 0.0351 10.4 9.1 9.9 4.4

95 0.0368 10.7 9.3 10.0 4.9

96 0.0347 10.4 8.6 9.3 2.4

97 0.0435 10.8 9.0 9.7 3.1

98 0.0312 10.5 8.5 9.3 1.1

99 0.0419 11.2 9.3 10.1 20.

100 0.0318 10.5 8.4 9.2 0.8

101 0.0460 11.0 8.5 9.3 1.2

102 0.0428 11.1 8.3 9.0 0.5

103 0.0273 10.4 8.1 8.8 0.2

104 0.0355 10.2 8.3 9.1 0.3

105 0.0270 10.3 8.3 9.0 0.4

106 0.0275 10.0 8.5 9.3 1.5

107 0.0275 10.2 8.1 8.9 0.3

108 0.0258 10.0 7.9 8.7 0.1

109 0.0262 10.4 8.3 9.0 0.0

110 0.0257 10.5 8.1 8.8 0.7

111 0.0277 10.8 9.3 10.0 2.8

112 0.0271 10.4 8.5 9.2 2.5

113 0.0341 10.9 9.0 9.8 0.5

114 0.0394 10.1 8.5 9.3 0.3

115 0.0398 11.0 9.0 9.8 0.5

116 0.0298 10.7 8.9 9.7 1.3

117 0.0395 10.0 8.1 8.9 0.9

118 0.0256 10.1 8.5 9.2 1.0


MNRAS **000**, 1–24 (2022)

20 _A. Zanella et al._


MNRAS **000**, 1–24 (2022)



119 0.0264 10.5 8.2 9.0 0.4

120 0.0260 10.0 8.4 9.2 1.1

121 0.0411 10.6 8.0 8.8 0.1

122 0.0428 10.2 8.3 9.1 1.8

123 0.0479 10.7 8.7 9.4 4.3

124 0.0363 10.6 8.9 9.7 3.1

125 0.0380 10.2 8.2 8.9 0.9


Intermediate-redshift star-forming galaxies (Freundlich et al. 2019)
1 0.7000 11.4 9.9 10.7 47.0

2 0.6227 10.9 9.0 9.7 47.0

3 0.7028 10.9 9.8 10.6 39.0

4 0.5297 10.3 9.6 10.5 25.0

5 0.5020 11.0 9.7 10.5 18.0

6 0.6223 11.2 9.6 10.4 21.0

7 0.7028 10.7 9.2 10.0 18.0

8 0.7026 11.4 9.3 10.1 20.0

9 0.7506 11.2 9.7 10.5 28.0

10 0.7007 11.6 9.7 10.5 23.0

11 0.6967 11.0 9.5 10.3 24.0

12 0.6077 11.3 9.5 10.2 11.0

13 0.6793 10.9 9.4 10.2 26.0

14 0.5165 11.2 9.2 10.0 14.0

15 0.7021 11.0 9.6 10.3 22.0

16 0.5172 10.2 9.4 10.2 28.0

17 0.6248 10.7 9.8 10.6 23.0

18 0.7503 10.3 9.1 9.9 13.0

19 0.5024 10.1 9.4 10.3 29.0

20 0.6885 10.4 9.1 9.9 8.8

21 0.5015 10.7 9.1 9.9 4.1

22 0.6081 10.9 9.6 10.3 13.0

23 0.6976 10.4 9.4 10.2 21.0

24 0.6985 10.4 9.6 10.4 29.0

25 0.7007 10.5 9.4 10.2 10.0

26 0.6590 11.1 9.8 10.5 51.0

27 0.6702 11.2 9.7 10.5 29.0

28 0.5093 11.2 9.6 10.3 37.0

29 0.7541 10.3 9.5 10.4 28.0

30 0.5090 10.3 9.3 10.1 11.0

31 0.7683 10.7 9.5 10.3 19.0

32 0.6593 11.1 9.6 10.4 14.0

33 0.7560 10.2 8.9 9.7 13.0

34 0.5010 10.4 9.0 9.8 7.4

35 0.7315 10.9 9.9 10.7 79.0

36 0.7359 10.0 9.4 10.3 9.9

37 0.6702 10.7 9.1 9.8 9.3

38 0.5705 10.7 9.5 10.3 25.0

39 0.5447 11.0 9.0 9.8 9.1

40 0.7099 10.9 8.9 9.7 5.9

41 0.7369 10.9 9.0 9.7 13.0

42 0.6445 10.6 9.1 9.9 6.6

43 0.7610 10.4 9.4 10.2 44.0

44 0.6790 10.6 _<_ 9 _._ 3 _<_ 10 _._ 1 23.0

45 0.7800 10.6 9.7 10.5 29.0

46 0.7790 10.4 9.5 10.3 21.0

47 0.7720 10.5 9.3 10.1 14.0

48 0.6382 10.0 9.0 9.9 11.0

49 0.5110 10.5 9.3 10.1 8.5

50 0.7784 10.2 9.3 10.1 13.0

51 0.7880 10.5 9.5 10.3 22.0

52 0.6825 10.3 9.7 10.5 23.0

53 0.5950 10.8 9.5 10.3 8.9

_Large molecular gas fraction of post-SBs at 𝑧>_ 1 21


54 0.5035 10.2 9.1 9.9 5.5

55 0.7837 10.3 9.3 10.2 32.0

56 0.6380 10.7 9.8 10.6 76.0

57 0.5561 10.1 8.5 9.4 6.8

58 0.5320 10.6 8.8 9.6 3.5

59 0.5605 11.1 8.8 9.6 7.6

60 0.5609 10.0 8.8 9.7 6.7

61 0.5200 10.8 9.8 10.6 8.7


High-redshift star-forming galaxies (Tacconi et al. 2013)
1 1.0230 10.6 9.8 10.8 100.0

2 1.0170 10.9 10.2 11.1 150.0

3 1.0260 10.9 9.6 10.6 53.0

4 1.1600 10.7 9.9 10.8 94.0

5 1.2820 10.4 9.5 10.5 6.4

6 1.1190 11.0 10.2 11.1 –

7 1.3740 10.6 9.7 10.7 113.0

8 1.3790 10.6 10.0 11.0 163.0

9 1.3510 10.7 9.5 10.5 115.0

10 1.3980 10.7 9.7 10.7 78.0

11 1.0020 10.3 9.5 10.5 31.0

12 1.1590 10.4 9.2 10.2 89.0

13 1.2300 11.2 10.3 11.3 200.0

14 1.1450 10.9 10.6 11.5 3.9

15 1.1920 10.4 9.5 10.5 60.0

16 1.0140 11.0 9.9 10.9 42.0

17 1.1730 11.0 9.7 10.6 52.0

18 1.0120 11.0 10.1 11.0 201.0

19 1.5290 11.0 10.4 11.4 373.0

20 1.0990 10.9 9.8 10.7 –

21 1.1800 11.1 10.1 11.0 88.0

22 1.0370 10.8 10.0 10.9 351.0

23 1.0520 10.6 9.7 10.7 35.0

24 1.0310 10.6 9.5 10.5 55.0

25 1.2270 11.0 9.0 10.0 –

26 1.1050 10.8 9.8 10.8 –

27 1.2290 10.7 9.5 10.5 –

28 1.1050 10.8 9.7 10.7 47.0

29 1.3500 10.6 9.6 10.6 87.0

30 1.2410 11.1 10.2 11.1 113.0

31 1.3170 10.9 10.0 10.9 148.0

32 1.3170 10.4 9.6 10.6 28.0

33 1.1680 11.0 9.5 10.5 –

34 1.4400 10.8 9.7 10.7 86.0

35 1.4350 10.7 9.2 10.2 –

36 1.1150 11.1 10.0 10.9 87.0

37 1.3930 10.5 9.4 10.4 55.0

38 2.1960 9.97 10.6 10.9 480.0

39 2.1870 10.7 9.6 10.5 80.0

40 – _<_ 10 _._ 0 10.5 _<_ 11 _._ 0 246.0

41 2.1820 10.4 10.0 10.9 246.0

42 2.2680 _<_ 9 _._ 7 10.8 _<_ 10 _._ 6 59.0

43 2.3300 10.7 9.7 10.6 –

44 -99.00 _<_ 9 _._ 9 10.8 _<_ 10 _._ 8 144.0

45 2.3330 11.1 10.5 11.5 271.0

46 2.2890 11.2 10.0 10.9 164.0

47 2.3400 11.3 10.2 11.2 159.0

48 – _<_ 10 _._ 0 10.8 _<_ 11 _._ 0 -0

49 2.4340 11.0 9.5 10.5 17.0

50 2.1890 10.8 9.6 10.6 50.0

51 2.2110 11.0 10.4 11.3 212.0

52 2.1090 10.4 9.5 10.5 –


MNRAS **000**, 1–24 (2022)

22 _A. Zanella et al._


53 2.1750 11.0 9.8 10.7 145.0

54 2.0110 10.8 10.7 10.9 26.0

55 – _<_ 10 _._ 1 10.6 _<_ 11 _._ 0 196.0

56 – _<_ 9 _._ 9 11.1 _<_ 10 _._ 8 62.0

57 2.2640 9.77 9.9 10.9 34.0


Local quiescent galaxies (Davis et al. 2016)
1 0.0183 11.6 8.3 9.0 0.3

2 0.0176 11.6 8.4 9.1 0.2

3 0.0162 11.7 _<_ 8 _._ 1 8.8 _<_ 0 _._ 15

4 0.0213 11.6 8.5 9.2 0.4

5 0.0230 11.7 _<_ 7 _._ 9 _<_ 8 _._ 6 0.1

6 0.0165 11.7 _<_ 7 _._ 8 8.5 0.2

7 0.0207 11.6 8.3 9.1 0.7

8 0.0149 11.6 8.5 9.2 0.3

9 0.0139 11.7 _<_ 8 _._ 1 _<_ 8 _._ 8 0.0

10 0.0211 11.8 _<_ 7 _._ 7 8.4 0.2

11 0.0247 11.7 8.7 9.4 0.5

12 0.0245 11.6 _<_ 8 _._ 1 _<_ 8 _._ 9 2.8

13 0.0145 11.7 _<_ 7 _._ 9 _<_ 8 _._ 6 _<_ 0 _._ 17

14 0.0163 11.7 _<_ 8 _._ 9 9.6 0.2

15 0.0243 11.8 _<_ 7 _._ 8 _<_ 8 _._ 6 0.8


Intermediate-redshift quiescent galaxies (Spilker et al. 2018)
110509 0.6670 11.0 9.1 9.9 0.8

130284 0.6020 10.9 9.2 10.0 2.7

132776 0.7500 10.9 9.3 10.0 3.1

138718 0.6560 11.2 _<_ 9 _._ 0 _<_ 9 _._ 8 2.1

169076 0.6770 11.4 _<_ 9 _._ 1 _<_ 9 _._ 9 0.5

210210 0.6540 11.3 _<_ 9 _._ 0 _<_ 9 _._ 8 _<_ 0 _._ 1

211409 0.7140 11.1 _<_ 8 _._ 9 _<_ 9 _._ 7 _<_ 0 _._ 1


High-redshift quiescent galaxies (Sargent et al. 2015)
pBzK-217431 1.4277 11.8 _<_ 9 _._ 9 _<_ 10 _._ 6 0.03


High-redshift quiescent galaxies (Hayashi et al. 2018)
Stack 1.4600 11.0 -Na _<_ 9 _._ 9 1.0


High-redshift quiescent galaxies (Rudnick et al. 2017)
30169 1.6290 11.2 9.8 10.5 12.0


High-redshift quiescent galaxies (Williams et al. 2021)
22260 1.240 11.5 _<_ 1 _._ 3 _<_ 1 _._ 0 3.6

20866 1.522 11.5 _<_ 0 _._ 9 _<_ 1 _._ 1 12.8

34879 1.322 11.3 _<_ 0 _._ 5 _<_ 0 _._ 7 22.9

34265 1.582 11.5 _<_ 0 _._ 8 _<_ 1 _._ 0 7.4

21434 1.522 11.4 _<_ 0 _._ 9 _<_ 1 _._ 1 19.1

307881 1.429 11.6 _<_ 0 _._ 7 _<_ 0 _._ 9 5.0


Low-redshift post-SBs (French et al. 2015)
EAH01 0.0478 10.5 2.1 2.8 0.06

EAH02 0.0541 10.0 1.9 2.6 5.03

EAH03 0.0449 10.3 2.2 2.8 0.02

EAH04 0.0269 10.2 1.0 1.6 0.07

EAH05 0.0653 10.0 2.0 2.6 0.06

EAH06 0.0441 10.5 _<_ 1 _._ 4 _<_ 2 _._ 0 5.37

EAH07 0.038 10.7 _<_ 1 _._ 0 _<_ 1 _._ 6 0.22

EAH08 0.0604 10.4 1.6 2.2 0.04

EAH09 0.0291 10.2 0.9 1.5 0.06

EAH10 0.1053 10.2 2.3 2.9 0.04

EAH11 0.0542 10.6 _<_ 1 _._ 6 _<_ 2 _._ 2 0.17

EAH12 0.0826 10.6 _<_ 1 _._ 8 _<_ 2 _._ 4 0.18

EAH13 0.1129 11.0 2.3 2.9 0.62

EAH14 0.0622 10.0 _<_ 1 _._ 7 _<_ 2 _._ 3 0.10

EAH15 0.0411 10.4 _<_ 1 _._ 4 _<_ 2 _._ 0 0.06

EAH16 0.1113 10.7 _<_ 2 _._ 2 _<_ 2 _._ 8 0.51


MNRAS **000**, 1–24 (2022)

_Large molecular gas fraction of post-SBs at 𝑧>_ 1 23


EAH17 0.0481 10.1 _<_ 1 _._ 4 _<_ 2 _._ 0 0.05

EAS01 0.0196 10.2 _<_ 0 _._ 8 _<_ 1 _._ 4 0.01

EAS02 0.0231 10.1 1.1 1.8 0.03

EAS03 0.0628 10.9 2.2 2.8 0.17

EAS04 0.0153 10.0 _<_ 0 _._ 1 _<_ 0 _._ 7 8.01

EAS05 0.0467 10.6 1.5 2.1 0.11

EAS06 0.0227 10.1 1.6 2.3 0.06

EAS07 0.0325 10.5 _<_ 1 _._ 0 _<_ 1 _._ 6 0.04

EAS08 0.0408 10.7 _<_ 1 _._ 0 _<_ 1 _._ 6 0.06

EAS09 0.027 10.6 1.5 2.2 0.04

EAS10 0.0381 10.5 _<_ 1 _._ 2 _<_ 1 _._ 8 0.02

EAS11 0.0395 10.7 _<_ 1 _._ 2 _<_ 1 _._ 8 0.08

EAS12 0.0336 10.0 0.9 1.6 0.03

EAS13 0.0462 11.0 _<_ 1 _._ 5 _<_ 2 _._ 1 0.09

EAS14 0.0826 11.3 2.1 2.7 0.41

EAS15 0.0533 10.8 1.5 2.1 0.17


Low-redshift post-SBs (Rowlands et al. 2015)
PSB1 0.039 9.3 _<_ 8 _._ 0 _<_ −0 _._ 5 10.96

PSB2 0.036 10.5 8.9 0.6 1.62

PSB3 0.032 9.5 7.8 -0.5 5.50

PSB4 0.029 9.8 8.7 0.3 5.50

PSB5 0.034 9.5 8.8 0.4 6.31

PSB6 0.043 10.5 9.0 0.6 2.51

PSB7 0.047 10.1 8.8 0.5 0.74

PSB8 0.046 9.9 8.2 -0.1 0.11

PSB9 0.049 10.1 8.9 0.5 0.69

PSB10 0.034 10.0 8.6 0.3 1.70

PSB11 0.048 10.5 8.2 -0.2 0.15


Intermediate-redshift post-SBs (Suess et al. 2017)
SDSSJ0912+1523 0.7470 11.2 9.9 10.7 52.0

SDSSJ2202-0033 0.6570 11.1 9.1 10.0 12.0


Intermediate-redshift post-SBs (Bezanson et al. 2022)
SDSS J1448+1010 0.6462 11.6 9.7 10.3 1.06

SDSS J0753+2403 0.5652 11.3 _<_ 8 _._ 6 _<_ 9 _._ 3 0.10

SDSS J1053+2342 0.6370 11.6 _<_ 8 _._ 9 _<_ 9 _._ 6 0.29

SDSS J0027+0129 0.5851 11.5 _<_ 8 _._ 8 _<_ 9 _._ 4 1.44

SDSS J2202-0033 0.6573 11.7 9.2 9.9 1.99

SDSS J2258+2313 0.7058 11.8 10.1 10.8 0.94

SDSS J0233+0052 0.5918 11.6 _<_ 8 _._ 7 _<_ 9 _._ 4 0.01

SDSS J0046-0147 0.6088 11.6 _<_ 8 _._ 8 _<_ 9 _._ 4 0.14

SDSS J1109-0040 0.5935 11.3 9.6 10.2 2.33

SDSS J1203+1807 0.5946 11.4 _<_ 8 _._ 7 _<_ 9 _._ 3 0.02

SDSS J1007+2330 0.6353 11.6 _<_ 8 _._ 9 _<_ 9 _._ 6 0.89

SDSS J0912+1523 0.7473 11.4 9.9 10.6 0.81

SDSS J1302+1043 0.5921 11.6 9.6 10.2 0.26


High-redshift post-SBs (Bezanson et al. 2019)
C21434 1.5220 11.2 _<_ 9 _._ 3 _<_ 10 _._ 0 _<_ 1 _._ 4


High-redshift post-SBs (Belli et al. 2021)
EGS-17533 1.2640 10.7 9.1 9.8 6.4

Table A1: Compilation of literature data used in this paper. The full table is
available online.


**Columns** : (1) Galaxy ID; (2) Redshift; (3) Stellar mass; (4) CO luminosity; (5) Molecular gas mass; (6) Star formation rate.


MNRAS **000**, 1–24 (2022)

24 _A. Zanella et al._


ID83492: CO(3-2) map



Companion 1


Companion 2



**Figure B1.** Available photometric and spectroscopic data of the galaxies detected in CO(3-2) that are likely companions of our post-starburst target ID83492.
_Left panel:_ CO(3-2) ALMA map showing the target and the two CO-detected companions. _Central panels:_ one-dimensional spectrum extracted at the location
of each companion, showing the CO(3-2) emission. _Right panels:_ SED modelling. The filled red circles indicate the observed photometry. The black line shows

the best-fit model.


**APPENDIX B:** **COMPANION GALAXIES**


We detected the CO(3-2) emission of two galaxies nearby our post-starburst target ID83492 (Section 3.1). In Figure B1 we show their
submillimeter spectra and spectral energy distributions.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–24 (2022)


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Iterative uv-plane point-source modelling per channel across all four sidebands, averaging over channels maximizing S/N to fit spatial position, and fitting average line maps in uv plane with a 2D PSF model; Gaussian fit to 1D spectrum allowing for negative continuum for ID97148",
  "failed_quote": "Since our targets are expected to be unresolved at the angular resolution of the observations, we modelled their emission in the uv plane with point-source profiles in all four sidebands and channel per channel."
 },
 {
  "path": "analysis_steps[0].assumptions[0].evidence[0]",
  "value": "Targets are spatially unresolved point sources at the angular resolution of the observations",
  "failed_quote": "Since our targets are expected to be unresolved at the angular resolution of the observations, we modelled their emission in the uv plane with point-source profiles in all four sidebands and channel per channel."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "log(tau/yr^-1) in [6.5, 10] in log-steps of 0.1; ages in log-steps of 0.1 from 100 Myr to age of Universe; A_V in [0, 6] mag; Z = 0.008, 0.02, 0.05",
  "failed_quote": "delayed SFHs (SFR(𝑡) ∝ 𝑡𝑒−𝑡/𝜏 with log(𝜏/yr−1) ∈[6.5, 10] in log-steps of 0.1), ages in log-steps of 0.1 from a minimum of 100 Myr and a maximum set by the age of the Universe,"
 },
 {
  "path": "reasoning.why_this_data.evidence[1]",
  "value": "Targeting CO(3-2) at z > 1 probes the dense molecular gas phase during the main quenching epoch of lower-mass (M_* ~ 5 x 10^10 M_sun) post-starburst galaxies with secure spectroscopic redshifts and stringent SFR limits.",
  "failed_quote": "For the present study, we selected two objects with stringent star formation rate limits (SFR ≲ 1 M⊙ yr−1) and secure spectroscopic redshift"
 },
 {
  "path": "reasoning.why_this_method.evidence[1]",
  "value": "Since targets are unresolved at ~1.5'' resolution, modelling point sources directly in the uv plane per channel and iterating spatial positions maximizes S/N; excluding dust-based literature gas estimates avoids systematic discrepancies.",
  "failed_quote": "Since our targets are expected to be unresolved at the angular resolution of the observations, we modelled their emission in the uv plane with point-source profiles in all four sidebands and channel per channel."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[2].evidence[0]",
  "value": "Post-SB ID83492 being a quiescent galaxy replenished with molecular gas stripped from its star-forming companions during the merger",
  "failed_quote": "Another possible scenario is the fact that the post-SB is a quiescent galaxy which was replenished with molecular gas, stripped from the star-forming companions, during the merger phase."
 }
]
```
