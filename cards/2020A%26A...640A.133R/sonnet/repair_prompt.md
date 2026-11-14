# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...640A.133R\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Astronomy & Astrophysics manuscript no. deathstar1 ⃝c ESO 2020
August 19, 2020

## **DEATHSTAR: Nearby AGB stars with the Atacama Compact Array**

### **I. CO envelope sizes and asymmetries: A new hope for accurate mass-loss-rate** **estimates**


S. Ramstedt [1], W. H. T. Vlemmings [2], L. Doan [1], T. Danilovich [3], M. Lindqvist [2], M. Saberi [2], H. Olofsson [2], E. De Beck [2],
M. A. T. Groenewegen [4], S. Höfner [1], J. H. Kastner [5], F. Kerschbaum [6], T. Khouri [2], M. Maercker [2], R. Montez [7],
G. Quintana-Lacaci [8], R. Sahai [9], D. Tafoya [2], and A. Zijlstra [10]


1 Theoretical Astrophysics, Division for Astronomy and Space Physics, Department of Physics and Astronomy, Uppsala University,
Box 516, SE-751 20 Uppsala, Sweden
e-mail: sofia.ramstedt@physics.uu.se
2 Department of Space, Earth and Environment, Chalmers University of Technology, Onsala Space Observatory, 439 92 Onsala,
Sweden
3 Department of Physics and Astronomy, Institute of Astronomy, KU Leuven, Celestijnenlaan 200D, 3001 Leuven, Belgium
4 Koninklijke Sterrenwacht van België, Ringlaan 3, B-1180 Brussels, Belgium
5 Rochester Institute of Technology, Rochester, NY, USA
6 Department of Astrophysics, University of Vienna, Türkenschanzstr. 17, 1180 Vienna, Austria
7 Smithsonian Astrophysical Observatory, 60 Garden Street, Cambridge, MA 02138, USA
8 Instituto de Física Fundamental (IFF-CSIC), Serrano 123, Madrid, CP 28006, Spain
9 Jet Propulsion Laboratory, MS 183-900, California Institute of Technology, Pasadena, CA 91109, USA
10 Jodrell Bank Centre for Astrophysics, Alan Turing Building, University of Manchester, Manchester M13 9PL, UK


**ABSTRACT**


Context. This is the first publication from the DEATHSTAR project. The overall goal of the project is to reduce the uncertainties of
the observational estimates of mass-loss rates from evolved stars on the Asymptotic Giant Branch (AGB).
Aims. The aim in this first publication is to constrain the sizes of the [12] CO emitting region from the circumstellar envelopes around
42 mostly southern AGB stars, of which 21 are M-type and 21 are C-type, using the Atacama Compact Array (ACA) at the Atacama
Large Millimeter/submillimeter Array (ALMA). The symmetry of the outflows is also investigated.
Methods. Line emission from [12] CO J=2→1 and 3→2 from all of the sources were mapped using the ACA. In this initial analysis,
the emission distribution was fit to a Gaussian distribution in the uv-plane. A detailed radiative transfer analysis will be presented in
a future publication. The major and minor axis of the best-fit Gaussian at the line center velocity of the [12] CO J=2→1 emission gives
a first indication of the size of the emitting region. Furthermore, the fitting results, such as the Gaussian major and minor axis, center
position, and the goodness of fit across both lines, constrain the symmetry of the emission distribution. For a subsample of sources,
the measured emission distribution is compared to predictions from previous best-fit radiative transfer modeling results.
Results. We find that the CO envelope sizes are, in general, larger for C-type than for M-type AGB stars, which is as expected if
the CO/H 2 ratio is larger in C-type stars. Furthermore, the measurements show a relation between the measured (Gaussian) [12] CO
J=2→1 size and circumstellar density that, while in broad agreement with photodissociation calculations, reveals large scatter and
some systematic differences between the different stellar types. For lower mass-loss-rate irregular and semi-regular variables of both
M- and C-type AGB stars, the [12] CO J=2→1 size appears to be independent of the ratio of the mass-loss rate to outflow velocity,
which is a measure of circumstellar density. For the higher mass-loss-rate Mira stars, the [12] CO J=2→1 size clearly increases with
circumstellar density, with larger sizes for the higher CO-abundance C-type stars. The M-type stars appear to be consistently smaller
than predicted from photodissociation theory. The majority of the sources have CO envelope sizes that are consistent with a spherically
symmetric, smooth outflow, at least on larger scales. For about a third of the sources, indications of strong asymmetries are detected.
This is consistent with what was found in previous interferometric investigations of northern sources. Smaller scale asymmetries are
found in a larger fraction of sources.
Conclusions. These results for CO envelope radii and shapes can be used to constrain detailed radiative transfer modeling of the
same stars so as to determine mass-loss rates that are independent of photodissociation models. For a large fraction of the sources,
observations at higher spatial resolution will be necessary to deduce the nature and origin of the complex circumstellar dynamics
revealed by our ACA observations.


**Key words.** stars: AGB and post-AGB - stars: mass-loss - stars: winds, outflows - stars: circumstellar material



**1.** **Introduction**


Stars with zero-age-main-sequence masses in the range of ∼0.8–
8 M ⊙ evolve into asymptotic giant branch (AGB) stars during
the late stages of their evolution. The heavy mass loss during



the AGB makes the stars major contributors of newly synthesized elements and dust to their surroundings. Understanding
the mass-loss process is crucial for comprehending the evolution of stars in this mass range, but also for extragalactic pop

Article number, page 1 of 28

A&A proofs: manuscript no. deathstar1


35



90 `[°]`


0


-90 `[°]`


180 `[°]` 0 180 `[°]`


Galactic Longitude


25



30


25


20


15


10


5


0
100 300 500 700 900



10 [-4]


10 [-5]


10 [-6]


10 [-7]


10 [-8]


10 [-9]
0 5 10 15 20 25 30


80


70


60


50


40


30


20


10


0
0 200 400 600 800



20


15


10


5


0
-9 -8 -7 -6 -5



10 [-6]


10 [-7]


10 [-8]



0 200 400 600 800



Fig. 1. Sample statistics of the full ∼180 star DEATHSTAR sample. M-type stars are blue, C-type stars are red, and S-type stars are green. Filled
symbols mark the stars included in this paper. Upper left: Galactic distribution of the full sample. Upper middle: Distance, D, distribution.
These are preliminary distances from previous publications (see text and Table 1). The solid lines show the expected distributions for each spectral
type with Poisson errors (Jura 1990; Jura & Kleinmann 1992; Jura et al. 1993). Upper right: Wind properties (mass-loss rate, M [˙], and terminal
expansionM˙ /v ∞ is a proxy for the wind density.velocity, v ∞ ) from previous Lower middle:publications. See text for references.M˙ /v ∞ as a function of the pulsational Lower left: Theperiod.M [˙] /v ∞ Lower left:distribution for the full sample. We note that [12] CO/ [13] CO ratio for the sample
sources (Ramstedt & Olofsson 2014) is plotted against the pulsational period. Both parameters are expected to increase as the stars evolve. See
text for a further discussion.



ulation studies. Mass-loss rates, M [˙], on the AGB are found to
range from ∼10 [−][8] –10 [−][4] M ⊙ yr [−][1] (e.g., Höfner & Olofsson 2018,
and references therein). It is challenging to find reliable observational methods to measure mass-loss rates covering this
wide range (Ramstedt et al. 2008), but it is crucial since the
measurements will provide key constraints for theoretical models (e.g., Eriksson et al. 2014; Marigo et al. 2016; Bladh et al.
2019). Wind formation is studied using dynamical wind models (e.g., Höfner 2008; Eriksson et al. 2014; Bladh et al. 2015;
Höfner et al. 2016) with the ultimate goal of developing a predictive theory of AGB mass loss. This will permit reliable estimates of dust production and, for example, the intrinsic reddening of distant galaxies (e.g., Conroy 2013). These models
are constrained using observed wind properties, that is, M [˙] and
wind velocities, v ∞ . However, with the derived M [˙] uncertainties
reaching as high as a factor of three (within the adopted spherically symmetric model, Ramstedt et al. 2008), the dynamical
wind models cannot be sufficiently well constrained (e.g., Fig. 7
in the recent paper by Bladh et al. 2019 shows how the wind parameters vary with model input parameters).
Observations of [12] CO radio line emission (originating in the
circumstellar envelope, CSE, which is created by the wind), in
combination with detailed radiative transfer, is considered to be
the most reliable method for determining AGB wind properties (e.g., Höfner & Olofsson 2018, and references therein). The
poorly constrained size of the [12] CO envelope is a remaining, sig

Article number, page 2 of 28



nificant source of uncertainty for the mass-loss rates estimated
using this method. The generally adopted strategy is to use an
envelope-sized estimate based on the photodissociation model
by Mamon et al. (1988). Major uncertainties are that this model
assumed a standard interstellar radiation field (Draine 1978), and
that numerical methods and shielding functions have been updated since then (e.g., Groenewegen 2017; Saberi et al. 2019).
In radiative transfer models that are intended to determine wind
parameters from [12] CO line observations, the [12] CO envelope size
is estimated using a functional fit to the Mamon et al. photodissociation model results. The envelope size is a function of the wind
parameters, including the [12] CO abundance, which increase with
density, that is, M [˙] /v e . A more exact way to determine the [12] CO
envelope size (e.g., independent of our knowledge of shielding
functions) is to constrain it directly using interferometry. Direct
observations will further improve the accuracy, since the radiation environment changes from source to source .
A pioneering interferometric survey of AGB (and post-AGB)
CO CSEs was performed by Neri et al. (1998). Forty-six sources
were mapped in [12] CO J=1 → 0 (from now on CO(1-0), etc.)
emission with three antennas on the Plateau de Bure interferometer combined with the IRAM 30 m telescope. The sample was
selected on evolutionary status, declination, IR color, and CO
line strength. They found a good agreement between measured
CO(1-0) sizes and photodissociation radii based on the model
by Mamon et al. (1988); however, as expected, they observed

Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA



significant scatter. They also concluded that about 30% of the
envelopes show significant asymmetry. This investigation was
later followed up with considerably improved capabilities at the
Plateau de Bure by the COSAS program (Castro-Carrizo et al.
2010). The goal was to investigate the morphologies of the envelopes, in particular during the transition to post-AGB, and this
sample contained several sources at later evolutionary stages
than the AGB. Castro-Carrizo et al. (2010) presented detailed
maps of the CO(1-0) and (2-1) emission from 16 sources and
thoroughly discussed each source. The synthesized beams were
typically of the order 3-5 [′′] and 1-2 [′′] for CO(1-0) and (2-1), respectively. They found that the measured envelope sizes were, on
average, slightly larger than expected from the photodissociation
model by Mamon et al. (1988). They further concluded that the
AGB envelopes generally show round shapes and approximately
isotropic expansion, while most later sources, that is post-AGB,
exhibit axial symmetry and fast bipolar flows.
We have started a new project called DEATHSTAR [1] (DEtermining Accurate mass-loss rates for THermally pulsing AGB
STARs) in which the overall aim is to better constrain the measurements of AGB mass-loss rates. Observations of a large sample of "typical" AGB envelopes (sources with known strong deviations from spherical symmetry have been omitted), covering
the full range of AGB stellar and wind parameters, will be analyzed in detail in future work. The already-available data base of
CO lower-J transitions will be modeled, together with available
and new interferometric observations using updated radiative
transfer models. In this first paper, new interferometric data of
CO(2-1) and (3-2) emission obtained with the Atacama Compact
Array (ACA) at the Atacama Large Millimeter/submillimeter
Array (ALMA) are presented. The sample selection is explained
in Sect. 2. The observations, data reduction, and data analysis are
outlined in Sect. 3. The results with an analysis of the CO line
emission distributions (size and morphology) and an overview
of the detections of emission from other molecular species are
presented in Sect. 4. Finally, the results are discussed and summarized in Sects. 5 and 6.


**2.** **The sample**


The full sample for which the circumstellar CO line emission will be modeled consists of the ∼180 C-, M-, and
S-type AGB stars analyzed in Schöier & Olofsson (2001),
González Delgado et al. (2003), and Ramstedt et al. (2006) together with additional sources presented in Danilovich et al.
(2015). In this initial paper, the new interferometric data for
the southern M- and C-type stars are presented. Some of the
available sample statistics for the full ∼180 star DEATHSTAR
sample are shown in Fig. 1. The distance distribution (Fig. 1,
middle) is compared with the estimated distribution in the solar neighborhood (Jura 1990; Jura & Kleinmann 1992; Jura et al.
1993). The estimated distribution is derived from 2MASS and
ground-based observations (Jura & Kleinmann 1990) and assumes a smooth distribution of 40 C-type stars kpc [−][2], a scale
height of 200 pc, and that there are a third as many S-type as
C-type stars. For the full ∼180 star DEATHSTAR sample, the
C-type stars from Schöier & Olofsson (2001) are all brighter
than K = 2 mag. The M-type sample consists of the non-Mira
stars from the General Catalog of Variable Stars (Samus’ et al.
2017, GCVS;) with quality flag 3 in the IRAS 12, 25, and 60 µm
bands and 60 µm flux ≳ 3 Jy with the addition of the Mira stars
in González Delgado et al. (2003). The S-type sample also con

1 www.astro.uu.se/deathstar



sists of stars that have good quality flux measurements in the
IRAS 12, 25, and 60 µm bands, that are found in the General
Catalog of Galactic S stars, and that are detected in Tc and are
hence intrinsic. The completeness of the S-type sample is discussed in Ramstedt et al. (2009) and it is thought to be complete
out to 600 pc. Furthermore, stars of all three spectral types are
only included in the sample if they are detected in CO radio
line emission, which could be reproduced under the assumption
of spherical symmetry. Sources that show strongly asymmetric
line profiles when observed with single-dish telescopes, or with
known CO-detached shells, are hence not included (e.g., R Scl,
U Ant, EP Aqr, and π [1] Gru). In this paper, we also exclude stars
that have previously been observed with ALMA; however, they
will be included in the future analysis. The lower panel of Fig. 1
shows that the stellar and wind parameters of the full ∼180 star
sample cover the ranges expected for AGB stars. As expected,
fewer stars are found at the high end. The sample is biased to
mass-losing stars since only stars that are previously detected
in CO radio line emission are included. It is also likely that the
full range of AGB masses is not covered simply because higher
mass stars are rare. It is our assessment that the full ∼180 star
DEATHSTAR sample is representative of Galactic mass-losing
AGB stars and covers the relevant ranges of wind and stellar
parameters to provide the necessary constraints for theoretical
models.

The 42 stars (21 M-type, 21 C-type), which were observed
with ALMA ACA in Cycle 4 and for which the data are presented in this paper, are listed in Table 1 with the variability type
(as listed in the GCVS), mass-loss rate, final wind velocity, distance according to the previous analysis in Schöier & Olofsson
(2001), González Delgado et al. (2003), and Danilovich et al.
(2015), and Gaia data release 2 (DR2) (Gaia Collaboration et al.
2016, 2018) distance from Bailer-Jones et al. (2018). The massloss rates and wind velocities were estimated by reproducing
several low-J CO lines for each source using the non-LTE,
nonlocal, spherically symmetric radiative transfer code that was
first presented in Schöier & Olofsson (2001). The CO/H 2 abundance ratio, which is necessary to derive the total gas massloss rate, is assumed to be 2 × 10 [−][4] for the M-type stars and
1 × 10 [−][3] for the C-type stars. The results from the photodissociation model by Mamon et al. (1988) was used in the radiative transfer modeling. In order to give consistent mass-loss
rates and distances, the distances adopted here (and listed in Table 1) are the same as those used in the papers listed above. The
distances will be updated as part of the future radiative transfer analysis planned for the full sample. For the semi-regular
M-type stars, a stellar bolometric luminosity of 4000 L ⊙ was
adopted. For M-type Mira variables and some C-type stars,
the period-luminosity relations from Whitelock et al. (1994) and
Groenewegen & Whitelock (1996) were used to estimate the luminosity, respectively. From the luminosity, the distances were
determined by either using two blackbodies or by using the dust
radiative transfer code DUSTY (Ivezic et al. 1999) to model the
spectral energy distribution (SED). For the remaining C-type
stars, the distance was estimated directly from the original Hipparcos parallax (The HIPPARCOS and TYCHO catalogs 1997)
or adopted from Menzies et al. (2006). The method used for each
C-type star is noted in Table 1. Figure 2 shows the comparison
between the adopted distances from a previous analysis and the
new Gaia DR2 distances for the full sample (Bailer-Jones et al.
2018). The spread is very large and the uncertainties affecting the
Gaia DR2 distances for these types of stars are further discussed
in Appendix A. The Gaia DR2 distances are typically larger than
the adopted distances. The mass-loss rates given in Table 1 scale


Article number, page 3 of 28

A&A proofs: manuscript no. deathstar1



1000


800


600


400


200


0
0 200 400 600 800 1000


Fig. 2. Comparison between distances from Gaia DR2 parallaxes and
the adopted distances from the previous analysis (see text for details)
for the full ∼180 star DEATHSTAR sample. Red symbols are carbon
stars, blue symbols are M-type stars, and green symbols are S-type stars.
Filled symbols are the sources included in this paper. The solid, black
line marks a one-to-one correlation, while the dashed lines show the
range of ±50%.


with distance as D [n] where 1.4 ≲ n ≲ 1.9 (Ramstedt et al. 2008)
and would, in general, be larger than those in Table 1 if Gaia
DR2 distances are used in the analysis.


**3.** **Observations, data reduction, and analysis**


3.1. Observations with the ACA


The 42 sample sources listed in Table 1 were observed with the
ACA in stand-alone mode in Cycle 4 in Bands 6 and 7 (project
codes: 2016.2.00025.S and 2017.1.00595.S). The correlator was
set up with four spectral windows in each band. In Band 6 the
windows were centered on 216.4, 218.3, 230.7, and 232.1 GHz.
In Band 7 they were centered on 330.75, 332.25, 343.52, and
345.6 GHz. Line emission from [12] CO J = 2 → 1, 3 → 2, and
13 CO J = 3 → 2 were covered in this setup, as well as emission
from a large number of other chemically interesting molecules,
including SiO, SiS, and CS, for example. The spectral resolution
of the imaged data was set to 0.75 km s [−][1] in the [12] CO and [13] CO
windows and to 1.0 and 1.5 km s [−][1] in the other spectral windows
in Band 6 and 7, respectively.
All data were calibrated using the standard pipeline scripts
and imaged using the Common Astronomy Software Applications package (CASA; McMullin et al. 2007). Self-calibration
was performed using a small number of channels, typically two,
across the peak [12] CO line emission and applied to all sources in
both bands. This improved the signal-to-noise ratio by 10-15%
on average. All data were cleaned initially using 10000 iterations. For sources brighter than ∼20 Jy, we found that further
cleaning iterations was necessary to recover the signal and finally 20000 iterations were applied to all bright (>20 Jy) sources.
The processed data have improved the quality compared to the
data products provided in the ALMA archive. Each spectral win

Article number, page 4 of 28



dow in both bands were imaged separately and can be accessed
through CDS (see also www.astro.uu.se/deathstar).
The full width at half-maximum (FWHM) beam widths and
root mean square (rms) noise levels at a velocity resolution of
0.75 km s [−][1], which were measured in the emission-free channels
in the [12] CO line window of the final images in both bands, are
given in Table B.1 for all sources. The science goal beam widths
and rms values at 1.5 km s [−][1] were 5.5 [′′] and 40 mJy beam [−][1] as
well as 3-4 [′′] and 50 mJy beam [−][1] in Bands 6 and 7, respectively.
For a significant fraction of the data sets, the beams are larger
than what was aimed for as well as elongated; this is an effect of
the project being partly observed as a filler program with some
of the sources at low elevation. The maximum recoverable scale
will cover a range depending on the exact antenna configuration and frequency, but on average it was 25 [′′] ± 4 [′′] and 18 [′′] ± 2 [′′]
for Band 6 and 7, respectively. The data quality is sufficient for
the DEATHSTAR project goals; however, as is discussed below,
there are compelling reasons to follow up on a majority of the
sources with higher-spatial-resolution observations.


3.2. Fitting the emission distribution in the uv -plane


The first step is to fit the visibility data in the CO(2-1) and (32) measurement sets with Gaussian distributions for all sources
using the CASA task UVMULTIFIT (Martí-Vidal et al. 2014).
The least-square fit gives the center position coordinates, the major axis and the axis ratio of the best-fit Gaussian, and the position angle of the major axis for each channel over which the fit
has been performed. This provides initial estimates for the sizes
of the emitting regions and indications of deviations from symmetry (as described below). The next step will be to perform
detailed radiative transfer modeling that is constrained by the
available multitransition single-dish, including the CO(1-0) line,
and interferometry data for each source to determine the size of
the CO envelope and to fit the emission distributions. This will
be presented in a future publication.


3.3. Emission distributions from 1D radiative transfer models


Emission distributions for the CO(2-1) and (3-2) lines were calculated from our previous best-fit radiative transfer model results
for a subsample of sources. This is a first step toward full radiative transfer modeling in order to reproduce the data available
for each source (planned for a future publication). The subsample consists of six stars: three M-type and three C-type stars of
which there is one low-, one intermediate-, and one high-massloss-rate source for each type. The models were directly adapted
from the previous best-fit models (Danilovich et al. 2015, see
also Table 1) and no attempt has been made to improve the fit to
the ALMA ACA data. Instead, the purpose is to start evaluating
the validity of the photodissociation model used to estimate the
size of the circumstellar CO envelopes in the models. For these
sources, the original radiative transfer used the photodissociation
radius from Mamon et al. (1988). The output from the best-fit radiative transfer models of the six sources was used to create image cubes with an imaging ray-tracing program that is part of the
radiative transfer package developed by Schöier (2000). The image cubes were created with 32×32 pixels with sizes of 0 [′′] . 8 and
0 [′′] . 7 for each channel across the CO(2-1) and (3-2) line, respectively. Once image cubes were created, they were run through
the ALMA simulator in CASA to simulate observations with the
same configuration and under the same conditions as during the
ACA observations of each respective source.

Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA



**4.** **Results**


4.1. Line profiles


The CO J = 2→1 and 3→2 line profiles were generated from the
image cubes across the lines and are presented in Figs D.1–D.6.
A circular aperture of 18 [′′] was used for both transitions because
this covered the emitting region without reaching lower-fidelity
regions that are close to the image edges. Table B.1 gives the
peak flux, the center velocity, and the total velocity width of
each line. The peak value was measured at the maximum point
across the line. The center velocity was measured at the center between the two points where the flux reaches 5% of the
peak value at the extreme velocities. The total width is the velocity width between the two 5%-peak-flux-value points. The line
profiles show an interesting structure that is likely indicative of
circumstellar dynamics and which was revealed due to the very
high signal-to-noise ratio attained. For example, some lines are
distinctly asymmetric (see e.g., R Hya and SS Vir). Furthermore,
some lines seem to show extended wings (see e.g., L [2] Pup and
TW Hor). Indications of circumstellar inhomogeneities and nonisotropic kinematics are further discussed below (Sect. 4.3).


4.2. Emission distribution


4.2.1. Gaussian distribution fits


The results of fitting the data using Gaussian visibility distributions are given in Table 2. The second column gives two
times the predicted photodissociation radius, R p, over the distance, D (from Table 1), as a measure of the expected size
of the CO line emitting region. The photodissociation radius,
which was measured as the radius where the CO abundance has
dropped to half of its initial value, was calculated using Eqns.
10 and 11 from Schöier & Olofsson (2001), which were derived
(Stanek et al. 1995) by fitting the results of the CO photodissociation model by Mamon et al. (1988). The parameter values
given in Table 1 were used for the calculation. Table 2 also lists
the beam-deconvolved FWHM major axis and the axis ratio of
the best-fit Gaussian at the center velocity (from Table B.1). The
error is the average error of the fits in the two channels adjacent
to the center velocity. When the error is large when the center
channels are strongly affected by resolved-out flux, for example
(see discussion in Sect. 4.3 and Figs E.1–E.6), the results are
given without errors and marked by a colon (:).
There are good reasons (from previous radiative transfer
models, e.g., Ramstedt & Olofsson 2014) to expect that the
CO(2-1) line will be excited almost throughout the entire CSE.
However, without detailed models for individual sources, we
cannot estimate how well the fitted Gaussian semi-major axis
will correspond to the photodissociation radius, or by what factor
it may deviate (see Sect. 4.2.2). In Fig. 3, we illustrate the reliability of using the measured Gaussian size as a proxy for the size
of the emitting region and for the photodissociation radius, R p,
based on the recent models by Saberi et al. (2019). These models include a more complete treatment of CO self-shielding and
yield radii that are mostly similar to Mamon et al. (1988), but
they can be up to ∼ 40% smaller for some combinations of massloss rates and initial CO abundances. We used the LIME 1.9.5
radiative transfer code (Brinch & Hogerheijde 2010) to produce
radiative transfer models of the photodissociation models from
Saberi et al. (2019), using the CSE parameters that were adopted
in their chemical models. Subsequently, we fit a Gaussian profile
to the CO(2-1) emission at the systemic velocity using a 1 km s [−][1]
channel width using the same method as in Sect. 3.2. Figure 3



shows the CO(2-1) line intensity distributions for three M-star
models with different mass-loss rates. Each model intensity distribution has been scaled to the fitted Gaussian. For intermediateto high-mass-loss-rate sources in particular, the intensity distribution is significantly non-Gaussian, and the determination of a
Gaussian FWHM is strongly dependent on the exact shape of
the intensity distribution in the inner region. Since low-angularresolution observations lack the uv-coverage to extract this information and as irregular structures are especially common in
these areas, the Gaussian radii determined for the CSEs with
the highest density, M [˙] /v ∞ ≳ 10 [−][7] M ⊙ km s [−][1] yr [−][1], are less
reliable. The figure also shows the calculated photodissociation
radius from Saberi et al. (2019) for each model (vertical lines)
scaled with the Gaussian FWHM radius. For the densest CSEs,
the CO(2-1) line does not extend to the photodissociation radius
and the Gaussian radii are therefore not a measure for R p .


Based on the formula and the distance estimates from
Stanek et al. (1995) in Table 1, the CO(2-1) major axis is a factor
of two smaller than 2×R p /D for the semi- and irregular variables,
and a factor of three smaller for the Mira variables, regardless of
chemical type. This is consistent with the expectations from the
modeling (both chemical and radiative transfer). Furthermore,
for a small majority of the sources (26/42), the CO(2-1) axis ratio deviates ≤10% from one, meaning that slightly more than
half of the sources are close to being circular. For the more aspherical sources, the photodissociation calculations that assume
a standard spherically expanding CSE introduce further uncertainties.


The major axes of the Gaussian fits to the CO(2-1) emission at the center velocity channels (third column of Table 2
multipliedM˙ /v ∞ in Fig. 4. The uncertainty of the major axis is very smallwith the distance from Table 1) are plotted against
in arcseconds (see Figs E.1–E.6). Instead, the error bars in the ydirection are dominated by the distance uncertainty, which cannot be evaluated easily. The figure also shows the photodissociation diameter for the M-type and C-type stars, respectively.
The photodissociation radii were calculated across the range of˙
M/v ∞ for v ∞ = 7.5 km s [−][1] . We used the LIME 1.9.5 radiative
transfer code again (Brinch & Hogerheijde 2010) to produce radiative transfer models of the Saberi et al. (2019) photodissociation model grid, and we used the same Gaussian fitting procedure as mentioned above to measure the predicted CO(2-1)
size. A spline fit to the expected CO(2-1) size is shown by the
solid lines in Fig. 4, which thus indicates the dependence of the
measured size of the CO(2-1) emitting region on the photodissociation radius as well as on the circumstellar density. The different results for higher- and lower-mass-loss-rate sources are apparent in the figure: The measured size of the CO(2-1) emitting
region for lower-mass-loss-rate M-type stars appears to show a
rather weak dependence on the circumstellar density, which is
also seen in the dependence of photodissociation diameter and
the modeled Gaussian diameter on the density. For higher-massloss rate M-type Mira sources, the dependence on the density is
much steeper, with a slope similar to what is expected from the
photodissociation models. In almost all cases, however, the measured diameter is smaller than the expected CO(2-1) diameter
based on the chemical and radiative transfer models. The lowermass-loss-rate C-type stars show no significant dependence on
circumstellar density, or at least a large scatter around the expected relation. Essentially all of the observed low-mass-lossrate C-type stars have CO(2-1)-emitting major axes of 1000–
2000AU. The higher-mass-loss-rate C-type Mira stars, on the
other hand, show a dependence on density that appears to be


Article number, page 5 of 28

A&A proofs: manuscript no. deathstar1


somewhat steeper than for the M-type Miras. For all C-type Miras, the measured diameters are larger than expected.
Although the measured size of the CO(2-1) region is smaller
than the calculated photodissociation diameter for essentially all
sources, it is apparent from Fig. 4 that the correlation between
the two is not straightforward. There are a variety of possible
explanations for the deviations between the observations and
the photodissociation models. The most obvious one is the uncertainty of the distance, which introduces significant scatter in
the size determinations. Furthermore, as shown in Saberi et al.
(2019), changes in initial CO abundance, CSE temperature profiles, and the interstellar radiation field can have significant effects. Finally, different density profiles, dust properties, or dustto-gas ratios from what is assumed in the photodissociation models can all change the estimated radius.
The full results of the fitting of Gaussian emission distributions to the ALMA ACA data across all of the CO line channels are displayed in Figs E.1–E.6. The major and minor axis of
each channel, as well as the RA and Dec offsets of the center of
the best-fit Gaussian relative to the SIMBAD J2000 coordinates
of each source, are plotted against lsr-velocity for each line and
source as denoted in each plot. The interpretation of these plots
is further discussed in Sect. 4.3.


Fig. 4. Full-width half-maximum (FWHM) major axis of the bestfit Gaussian at the center velocity channel of the CO(2-1) emission
(marked by triangles and in astronomical units by multiplying by the
distance from Table 1) as a function of circumstellar density (as measured by M [˙] /v ∞ from Table 1). M-type stars are blue. C-type stars are red.
Mira-type variables are marked with solid symbols and other variables
appear with open symbols. The dashed lines show the photodissociation diameter for M-type (blue) and C-type (red) stars from the model
grid by Saberi et al. (2019) (calculated with v ∞ = 7.5 km s [−][1] ). The dotted
lines are the parametrized fits to the results from Mamon et al. (1988).
The solid lines show a spline-fit to the expected Gaussian FWHM determined from radiative transfer modeling of the models from Saberi et al.
(2019). See text for a further explanation.



Fig. 3. CO(2-1) intensity distribution at the systemic velocity as a function of radius for three M-star models from Saberi et al. (2019). The
models were normalized to the peak of the fitted Gaussian and scaled
to the FWHM radius of that Gaussian for each model separately. The
normalized Gaussian is indicated by the solid red line in the figure. For
each model, the vertical lines indicate the photodissociation radius R p,
which was also scaled to the Gaussian FWHM radius for each model.
See text for a further explanation.


4.2.2. Comparison with results from spherically symmetric
radiative transfer models


Here we present the comparison between the emission distributions from ALMA and those calculated from our previous bestfit radiative transfer model results (Sect. 3.3). The same analysis
was performed on the model results as on the observational data.


Article number, page 6 of 28



Figure 5 shows the results of the Gaussian emission distribution
fitting (Sects 3.2 and 4.2.1) from the models compared with the
observational results for the CO(2-1) emission for each of the
six selected sources. For error bars on the observational results,
see Figs E.1–E.6. The results are affected by the difficulties of
fitting a Gaussian distribution to the weaker and smaller emission distribution close to the edge of the line. It is obvious that
the radiative transfer analysis of the full data set will be necessary before any firm conclusions can be drawn. For the M-type
stars, it seems as if the size of the emission might be smaller
than expected for the low mass-loss-rate source (R Leo) and the
opposite for the high mass-loss-rate source (IRC-10529). The
upcoming analysis will evaluate whether this is a general trend
or specific to the selected sources. This trend would indicate an
even steeper dependence on the circumstellar density than predicted from the photodissociation model by Mamon et al. (1988)
and is contrary to the fit to the M-type Mira stars in Fig. 4. The
results for the C-type stars are less clear, partly because the fitting results to the U Hya data seem strongly affected by resolved
out flux (see Sect. 4.3). It is also possible that the emission from
C-type stars is subject to stronger optical depth effects due to the
higher CO abundance. This will also be evaluated in the upcoming radiative transfer analysis.

Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA



12


10


8


6


4


2


0









-10 -5 0 5 10


12



12


10


8


6


4


2


0


12


10


8


6


4


2


0



30 35 40 45



-30 -20 -10 0





10


8


6


4


2


0


12


10


8


6


4


2


0





10


8


6


4


2


0





-40 -35 -30 -25



-10 0 10 20



30 40 50



Fig. 5. Comparison between the results from fitting a Gaussian emission distribution to the CO(2-1) data (blue) and the model results (orange)
based on previous best-fit models (see text). The solid lines show the major axis and the dashed lines show the minor axis. The red and green
lines show the RA and Dec. offsets for the data, respectively. The top row shows three M-type stars, and the bottom row shows three C-type stars,
with an increasing mass-loss rate (Table 1). The results are affected by the difficulties of fitting a Gaussian distribution to the weaker and smaller
emission distribution close to the edge of the line. For error bars on the results from the measurements, see Figs E.1–E.6.



4.3. Asymmetrical features


Several asymmetrical features can be identified in the observational results presented thus far, that is, the line profiles (Figs D.1–D.6) and the results from the Gaussian fitting
(Figs E.1–E.6). These features can be divided into two classes:
Features that are consistent with a spherically symmetric CSE
and those that are not.


4.3.1. Consistent with a smooth outflow


The features that can be explained with a spherically symmetric
CSE are as follows.


1. An offset between the center position (of the fitted Gaussian)
and the source coordinates is explained the most easily by
uncertainties in the adopted coordinates (taken from SIMBAD pre-Gaia DR2), when seen consistently in both lines.
Examples include V Tel and RT Cap, for instance.
2. The interferometer acts as a spatial filter and since only the
ACA was used (and not the total-power array), large-scale,
smooth emission is resolved out. Resolved-out flux results in
a lower peak flux level than when measured with a (similarsized) single-dish telescope. Furthermore, if a significant
fraction of the flux is resolved out, the visibility distribution
cannot be well-fitted by a simple Gaussian distribution. This



is the most apparent across the center channels where the
emission distribution is expected to be the largest. Therefore,
it is also a more common problem for the CO(3-2) line where
the beam is smaller. Examples of this can be seen in RR Aql
(CO(3-2)), WX Psc (both lines), and R Vol (CO(3-2)).
3. Self-absorption on the blue-shifted side of the line can be
seen as asymmetry in the line profile where it is sometimes
apparent that emission is "missing" on the blue side of the
line. Examples include IRC-10529, NP Pup, and T Ind. It
is even more apparent when looking at how the sizes of
the sources change across the channels. Sources with selfabsorption show a prominent peak in the size distribution at
blue-shifted velocities since these channels probe emission
coming from cooler circumstellar layers (and hence a larger
region).


These features are relatively easy to explain and related to how
the observations were performed for the first and second points.


4.3.2. Indications of circumstellar anisotropic structure


The next class of features is less straight-forward to interpret and
the features are mostly thought to be clearly inconsistent with a
spherically symmetric outflow. Further modeling and/or observations will be necessary to explain exactly how they arise. The
majority of sources that exhibit these features need to be fol

Article number, page 7 of 28

A&A proofs: manuscript no. deathstar1



lowed up with higher-spatial-resolution observations. Features
that cannot be explained by a smoothly expanding, spherically
symmetric CSE are the following.


4. Triangular line profiles are not a newly observed feature;
however, a satisfactory explanation as to how they arise
is lacking. This feature seems to be more common among
high-mass-loss-rate sources. Clear examples are R Hor and
V1259 Ori.
5. High-velocity wings are not a new feature either, but they
can be detected from more sources in this data set due to
the superior sensitivity reached with the ACA observations
compared to previous single-dish observations. The line profiles of TW Hor, for example, are very similar to those of the
known asymmetrical CSE of π [1] Gru (e.g., Doan et al. 2020).
The CO emission from π [1] Gru can be reproduced by a CSE
consisting of an expanding equatorial torus (explaining the
two central peaks) and a bi-polar faster outflow leading to
wide wings (Doan et al. 2017). Other, more tentative examples of line profiles with high-velocity wings include those
of L 2 Pup, R Leo, and BK Vir.
6. The fitting of the visibility distribution gives the center position of the best-fit Gaussian in each channel and the offset relative to the center position is plotted in Figs E.1–E.6.
Several sources show center position gradients. A position
gradient with velocity is either indicative of expansion in
a higher-density layer (e.g., an equatorial torus such as in
the case of π [1] Gru) or of rotation (e.g., Ramstedt et al. 2018;
Vlemmings et al. 2018) depending on the orientation of the
sources. Examples of sources with center position gradients
are BK Vir (in RA), TW Hor (both RA and Dec), SS Vir
(both RA and Dec), and W CMa (in RA).
7. A spherically symmetric CSE with a constant expansion velocity grows monotonically in size from the edge of the
line to the center velocity. The effects of self-absorption
and resolved-out flux on the size distribution are discussed
above. For some sources, the source size changes in an unpredictable way that cannot be easily explained without further modeling and/or observations. Examples include T Mic,
CW Cnc, RT Vir, and W Ori.
8. It is directly apparent from the line profile that the emission
cannot come from a standard CSE for a handful of the sample sources. Instead, these line profiles are anomalous. Some
are previously known to be anomalous, for example, L 2 Pup
(e.g., Kervella et al. 2016) and R Leo (Fonfría et al. 2019),
while others have not been studied with a focus on the detailed structure of the CSE, for example, R Hya and SS Vir.


4.4. Detections of emission from molecules other than [12] CO


A large number of molecules other than [12] CO have transitions
with frequencies within the observed bands. For all sources, the
peak fluxes of the detected lines as measured across a 10 [′′] aperture are listed in Tables C.1-C.4. The spectral resolution across
each spectral window is the same as the one used for imaging
and is given in Sect. 3. The lines listed in Tables C.1-C.4 are
those for which we are confident of detection at the given spectral resolution and aperture. It is possible that further detections
could be confirmed with more optimization of the data analysis.
Lines from SiO, SiS, [13] CO, CS, and H [13] CN are detected in
a majority of the sources. Unsurprisingly, oxides such as SO,
SO 2, and H 2 O are only detected in the M-type stars as are H 2 S
and less common isotopologues of SiS and NaCl. In the C-type
stars, [13] CN and [13] CS are detected, sometimes together with lines


Article number, page 8 of 28



from molecules with several carbon atoms, such as HC 3 N, C 4 H,
and SiC 2 . A further analysis of these lines is beyond the scope of
this paper, but an overview of the firm detections are given here
and follow-up studies are encouraged.


**5.** **Discussion and summary**


The measurements presented in this paper show that, for this
sample, the CO envelope sizes are, in general, larger for C-type
than for M-type stars. As explained both above and below, the
envelope size depends on many different parameters, but this
trend is expected if the CO/H 2 ratio is larger in C-type stars.
Based on chemical equilibrium models, the ratio between the Cand M-type CO-abundance is generally assumed to be equal to
five when deriving total gas mass-loss rates from observations of
CO emission lines. As part of the analysis planned for the full
DEATHSTAR sample, the difference in abundance depending
on chemical type (also S-type stars) can now be observationally
constrained for a large sample of AGB stars.
Furthermore, the measurements show a relation between the
measured (Gaussian) CO(2-1) size and circumstellar density
that, while in broad agreement with photodissociation calculations, reveal large scatter and some systematic differences between the different stellar types. A significant amount of scatter
arises due to significant distance uncertainties. Part of the differences can also be explained by excitation and optical depth
effects that decrease the reliability of the Gaussian size determination for M [˙] /v ∞ ≳ 10 [−][7] M ⊙ km s [−][1] yr [−][1] . For lower-massloss-rate irregular and semi-regular variables of both M- and
C-type stars, the CO(2-1) size seems essentially independent ofM˙ /v ∞ . For the higher-mass-loss-rate Mira stars, the CO(2-1) size
clearly increases with circumstellar density, with larger sizes for
the higher CO-abundance C-type stars. The M-type stars appear
to be consistently smaller than what was predicted from photodissociation theory. The differences between the estimates and
measurements could (as shown in Saberi et al. (2019)) be due
to, for example, a systematically overestimated CO abundance,
differences in the CSE temperature profile, or differences in the
UV-environment. Additionally, a difference in the adopted properties of the dust, which is responsible for much of the shielding
in low density CSEs, and/or the adopted dust-to-gas ratio in the
models would lead to different sizes. Finally, a difference in the
CSE density profile due to changes in velocity and/or the mass
loss rate could significantly alter the photodissociation radius.
With the size measurements that are now available for the large
sample of sources in the DEATHSTAR project, it will be possible to investigate many of these factors in more detail.
In recent years there has been a strong focus on investigating the isotropy of the mass-loss process in low- to intermediate
mass evolved stars, which was partly expedited by the superior
imaging capabilities of ALMA. Several AGB sources with previously known complex circumstellar dynamics and/or binary
companions have been mapped in detail (e.g., Ramstedt et al.
2014; Decin et al. 2015; Maercker et al. 2016; Doan et al. 2017;
Kim et al. 2017; Homan et al. 2018; Fonfría et al. 2019). With
the DEATHSTAR project, the aim is to get an overview of how
widespread and significant the detected asymmetrical features
are, from the perspective of measuring the amount of circumstellar wind material. A goal is to eventually be able to evaluate
the uncertainties that these features will result in when estimating mass-loss rates from more distant, unresolved sources.
The results presented here show that the majority of the
sources have CO CSEs that are consistent with a spherically
symmetric, smooth outflow, at least on larger scales. This is

Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA



based on the line profile shapes and that the emission distribution
across the line channels can be well-fitted with a Gaussian visibility distribution with axis ratios that are close to one for a majority of the sources. For about a third of the sources, indications
of strong asymmetries are detected. This is consistent with what
was found in previous interferometric investigations of northern sources (Neri et al. 1998; Castro-Carrizo et al. 2010). In the
DEATHSTAR sample, some of the known asymmetric sources
have been removed, but the higher sensitivity reached in the
ACA observations allowed us to detect relatively weaker features, such as extended line wings, than what was possible in
previous investigations. This offers an explanation as to why the
same fraction of strong asymmetries is still found. In a large fraction of the sources, some deviation from spherical symmetry is
detected, often on smaller scales. Whether these smaller deviations can have a significant effect on the estimated mass-loss rate
or not cannot be evaluated without further analysis.
The peak fluxes of lines from molecules other than [12] CO detected within the observed bands are listed in Tables C.1-C.4.
In general, lines from molecules that are known to be abundant
in AGB CSEs (e.g., SiO, SiS, CS) are detected in almost all
sources. Some less abundant oxides (e.g., H 2 O and SO) are only
detected in the M-type stars, while emission from molecules
with several carbon atoms (e.g., SiC 2 ) are only detected toward
the C-type stars. No further analysis has been attempted.


**6.** **Outlook**


This paper presents the first observational results from the
DEATHSTAR project. The CO(2-1) and (3-2) ALMA ACA
observations of the southern M- and C-type stars observed in
ALMA Cycle 4 are presented and analyzed. In an upcoming publication, the results on the M-, S-, and C-type sources observed
in Cycle 5 will be presented. The next step is to perform detailed
radiative transfer modeling that is constrained by the presented
ACA data together with the previously attained single-dish observations of the lower-J CO transition lines (up to J=6→5) in
order to determine mass-loss rates that are independent of photodissociation model results. This will also be presented in future
publications. For a large fraction of the sources, observations at
higher spatial resolution will be necessary to deduce the nature
and origin of the complex circumstellar dynamics revealed by
the observations and data analysis presented in this paper.


Acknowledgements. This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2016.2.00025.S and #2017.1.00595.S. ALMA is a
partnership of ESO (representing its member states), NSF (USA) and
NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic
of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO
and NAOJ. This work has made use of data from the European Space
Agency (ESA) mission Gaia [(https://www.cosmos.esa.int/gaia),](https://www.cosmos.esa.int/gaia)
processed by the Gaia Data Processing and Analysis Consortium (DPAC,
[https://www.cosmos.esa.int/web/gaia/dpac/consortium).](https://www.cosmos.esa.int/web/gaia/dpac/consortium) Funding
for the DPAC has been provided by national institutions, in particular the
institutions participating in the Gaia Multilateral Agreement.



Table 1. Forty-two sources observed with the ACA by spectral type and
variability type listed in ascending mass-loss-rate order.


Source Variability M˙ [a] v ∞ [a] D D Gaia
type [M ⊙ yr [−][1] ] [km s [−][1] ] [pc] [pc]


M-type semi-regular and irregular stars:
L 2 Pup SRb 2 × 10 [−][8] 2.3 85 140
W Hya SRa 8 × 10 [−][8] 6.5 65 160
T Mic SRb 8 × 10 [−][8] 4.8 130 190
Y Scl SRb 1.3 × 10 [−][7] 5.2 330 310
V1943 Sgr Lb 1.3 × 10 [−][7] 5.4 150 665
BK Vir SRb 1.5 × 10 [−][7] 4.0 190 235
V Tel SRb 2 × 10 [−][7] 6.8 290 400
SU Vel SRb 2 × 10 [−][7] 5.5 250 290
UY Cet SRb 2.5 × 10 [−][7] 6.0 300 320
SV Aqr Lb 3 × 10 [−][7] 8.0 470 390
SW Vir SRb 4 × 10 [−][7] 7.5 120 300
CW Cnc Lb 5 × 10 [−][7] 8.5 280 210
RT Vir SRb 5 × 10 [−][7] 7.8 170 490
R Crt SRb 8 × 10 [−][7] 10.6 170 240

M-type Mira stars:
R Leo M 2 × 10 [−][7] 6.0 130 70
R Hya M 3 × 10 [−][7] 7.0 150 225
R Hor M 5.9 × 10 [−][7] 4.0 310 310
RR Aql M 2.4 × 10 [−][6] 9.0 530 320
IRC-10529 M 2.5 × 10 [−][6] 12.0 270 WX Psc M 1.1 × 10 [−][5] 19.3 600 IRC+10365 M 3 × 10 [−][5] 16.2 750 360

C-type semi-regular and irregular stars:
TW Oph SRb 5 × 10 [−][8] 7.5 280 [b] 590
NP Pup Lb 6.5 × 10 [−][8] 9.5 420 [b] 470
TW Hor SRb 9 × 10 [−][8] 5.5 400 [b] 420
T Ind SRb 9 × 10 [−][8] 6.0 570 [b] 610
RT Cap SRb 1 × 10 [−][7] 8.0 450 [c] 430
AQ Sgr SRb 2.5 × 10 [−][7] 10.0 420 [d] 560
U Hya SRb 1.2 × 10 [−][7] 7.0 160 [b] 170
W Ori SRb 1.4 × 10 [−][7] 11.0 220 [b] 1010
V Aql SRb 1.5 × 10 [−][7] 8.5 370 [b] 400
Y Pav SRb 1.6 × 10 [−][7] 8.0 360 [c] X Vel SR 1.8 × 10 [−][7] 10.0 310 [c] 640
Y Hya SRb 1.9 × 10 [−][7] 9.0 350 [b] 475
SS Vir SRa 2 × 10 [−][7] 12.5 540 [c] 670
W CMa Lb 3 × 10 [−][7] 10.5 450 [d] 555

C-type Mira stars:
R Lep M 7 × 10 [−][7] 18.0 250 [b] 420
CZ Hya M 9 × 10 [−][7] 12.0 960 [c] 3300
R For M 1.1 × 10 [−][6] 16.5 610 [c] 630
R Vol M 1.7 × 10 [−][6] 18.0 730 [c] 840
RV Aqr M 2 × 10 [−][6] 16.0 670 [c] 860
V688 Mon M 6.1 × 10 [−][6] 13.5 1770 [e] 500
V1259 Ori M 8.8 × 10 [−][6] 16.0 1600 [e] 

Notes. The columns give wind properties (mass-loss rate, M [˙], and final expansion velocity, v ∞ ), and preliminary distance, D, from previous
publications (see text for details). The final column gives the distances
from Gaia data release 2 (Bailer-Jones et al. 2018) for comparison purposes (see also Fig. 2).
(a) From the previous analysis. See text for references. (b) Hipparcos parallax. [(][c][)] Period-Luminosity relation (Groenewegen & Whitelock 1996).
(d) Assuming 4000 L ⊙ . (e) Adopted from Menzies et al. (2006).


Article number, page 9 of 28

A&A proofs: manuscript no. deathstar1


Table 2. Results from the Gaussian visibility distribution fitting.


2R p CO(2-1) CO(3-2) Asym.
Source D Major Ratio Major Ratio Feat.

[ [′′] ] [ [′′] ] [ [′′] ]


M-type semi-regular and irregular stars:

L 2 Pup 10.6 6.04±0.08 0.85±0.02 5.9: 1.0: 2, 5, 8
W Hya 22.6 10.92±0.12 0.75±0.06 5.59±0.06 0.89±0.01
T Mic 12.0 7.04±0.12 0.99±0.02 3.48±0.08 0.97±0.05 6, 7
Y Scl 6.0 3.88±0.20 0.89±0.05 3.02±0.16 0.75±0.05 8
V1943 Sgr 13.0 6.95±0.12 0.94±0.03 7.9: 0.9: 2
BK Vir 12.2 5.84±0.15 0.89±0.04 3.46±0.04 0.90±0.02 5, 6
V Tel 8.0 5.00±0.08 0.95±0.02 3.22±0.07 0.94±0.03 1

SU Vel 9.8 4.85±0.07 0.76±0.01 3.37±0.05 0.75±0.02

UY Cet 9.0 5.48±0.13 0.82±0.03 3.04±0.08 0.86±0.03 4
SV Aqr 5.8 3.83±0.17 0.94±0.06 2.36±0.18 0.98±0.14 6
SW Vir 27.0 8.92±0.13 1.00±0.02 6.7: 1.0: 2, 6
CW Cnc 12.6 8.00±0.15 0.88±0.02 3.92±0.13 0.92±0.04 7

RT Vir 21.2 8.18±0.14 0.89±0.02 5.25±0.06 0.82±0.01 7

R Crt 25.0 7.72±0.08 1.0: 5.5: 0.9: 2

M-type Mira stars:

R Leo 18.2 10.00±0.11 0.88±0.02 4.70±0.08 1.0: 2, 5, 8
R Hya 18.8 4.5: 1.0: 4.5: 0.8: 6, 7, 8
R Hor 16.8 7.28±0.04 0.84±0.01 4.1: 0.8: 2, 4
RR Aql 4.5 6.39±0.07 0.95±0.01 7.2: 0.9: 2, 5
IRC-10529 28.6 7.00±0.06 0.93±0.01 8.2: 0.6: 2, 3
WX Psc 25.4 11.6: 0.9: 8.5: 0.7: 2, 3
IRC+10365 40.8 7.73±0.08 0.93±0.01 4.18±0.05 0.92±0.02 3

C-type semi-regular and irregular stars:

TW Oph 8.0 4.68±0.26 1.00±0.08 2.57±0.09 0.96±0.04
NP Pup 5.8 4.63±0.27 0.93±0.08 3.16±0.32 0.87±0.12 3
TW Hor 8.4 5.77±0.06 0.66±0.01 2.65±0.05 0.94±0.02 5, 6
T Ind 5.6 3.50±0.14 0.83±0.06 2.14±0.28 0.91±0.13 1, 3
RT Cap 7.0 4.42±0.23 0.89±0.05 2.25±0.20 1.00±0.15 1
AQ Sgr 9.0 4.93±0.11 0.90±0.02 1.4: 1.0:
U Hya 17.8 10.8: 0.8: 6.2: 0.7: 2
W Ori 9.2 4.38±0.07 0.98±0.03 3.28±0.07 0.92±0.02 7, 8
V Aql 10.6 5.65±0.09 0.97±0.02 3.22±0.05 0.94±0.02
Y Pav 11.2 4.89±0.10 0.99±0.03 3.04±0.06 0.94±0.03

X Vel 13.0 4.07±0.10 0.99±0.03 2.63±0.09 0.92±0.04 3
Y Hya 12.2 5.39±0.15 1.0: 2.63±0.10 0.89±0.06
SS Vir 7.4 5.88±0.86 0.57±0.13 3.34±0.25 0.70±0.08 5, 6, 8
W CMa 11.6 4.26±0.11 1.00±0.02 3.20±0.08 0.98±0.03 6

C-type Mira stars:

R Lep 17.2 11.7: 0.9: 3.58±0.07 0.99±0.03 2
CZ Hya 9.8 3.98±0.11 0.99±0.04 2.47±0.15 0.88±0.09
R For 15.8 5.69±0.11 0.99±0.02 3.60±0.07 0.93±0.03 3
R Vol 16.6 5.83±0.08 0.97±0.02 4.0: 1.0: 2, 3
RV Aqr 24.6 6.01±0.05 0.99±0.01 4.2: 0.9: 2, 3
V688 Mon 16.3 6: 1: 2.98±0.08 0.97±0.03 3
V1259 Ori 20.9 5.0: 1.0: 3.48±0.06 0.92±0.02 3, 4


Notes. The second column gives the photodissociation radius two times
over the distance as a measure of the expected size of the CO emitting
region. Columns 3-6 give the major axis and the axis ratio with errors
for the best-fit Gaussian at the center velocity of the respective line.
The final column gives the asymmetrical features for each source, as is
explained in Sect. 4.3. See text for a further explanation.


Article number, page 10 of 28

Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA



**Appendix A:** **Parallaxes for AGB stars from Gaia**
**DR2**


Fig. A.1. Gaia DR2 parallaxes for our sample compared to the distances
used in the current mass-loss models. In the bottom panel, the Gaia parallaxes are presented with their formal errors. In the top panel, the astrometric_excess_noise value is added in quadrature to the formal errors
following the empirical results from van Langevelde et al. (2018).


Since the paper presents mass-loss values based on earlier
analysis, we have presented the distances that were used in the
mass-loss determinations. Recently, Gaia DR2 astrometric solutions were released for all but one of the stars in our sample. While the formal errors on the Gaia parallaxes are generally
small, the reliability of the Gaia parallaxes for AGB stars is under debate (e.g., van Langevelde et al. 2018). There are several
reasons why the Gaia parallaxes to AGB stars might be wrong
or have significantly underestimated the assigned errors. Firstly,
AGB stars are often larger than the parallax signature itself (with
sizes of order one to a few astronomical units) and they have
convective surface motions that can cause the photo-center to
shift significantly (Chiavassa et al. 2018). Secondly, AGB pulsations can affect the astrometric measurements. Finally, AGB
stars are so bright that Gaia approaches saturation. The Gaia
DR2 catalog contains a number of parameters that can provide
a measure for the reliability of the astrometry. One of these is
the astrometric_excess_noise, which represents modeling errors
for sources that do not behave according to the adopted astrometric model of Lindegren et al. (2012). In van Langevelde et al.
(2018), an empirical analysis of very long baseline interferometry (VLBI) parallaxes compared to the Gaia results revealed that
adding the astrometric_excess_noise to the formal parallax errors in quadrature was needed to reconcile the two methods. In
Fig. A.1 we show the difference between the formal and excess
noise errors. When we adopted this procedure, only four of the
AGB stars in our sample have a parallax solution that satisfies
π/σ π - 5. Recently, another measure of reliability was introduced, namely the RUWE [2] (renormalized unit weighted error).


2 Lindegren et al. 2018, Gaia memo; GAIA-C3-TN-LU-LL-124-01



This represents the square-root of the reduced χ [2] value, which
was corrected for the strong dependence of the χ [2] value on magnitude and color. For many applications, a RUWE value < 1.4 is
empirically found to represent a good fit. However, as is noted in
Lindegren et al. (2018), the RUWE normalization does not work
optimally for the brightest sources G < 12, which includes all
of our AGB stars. In these cases, Lindegren et al. (2018) stress
that a RUWE threshold should be set based on empirical evidence and not a theoretical distribution. For this, we can use the
northern AGB star BX Cam as an example. Recent VLBI observations have revealed a parallax of π VLBI = 1.73 ± 0.03 mas
(Matsuno et al. 2020). This value is significantly different from
the Gaia value of π Gaia = 4.13 ± 0.25 even when taking the astrometric_excess_noise of 0.67 mas into account. However, the
RUWE of BX Cam is 1.04, which would have qualified as a
good solution in most cases. In comparing the stellar luminosity,
Matsuno et al. (2020) conclude that the larger VLBI distance is
more reliable since the VLBI distance would imply a luminosity
of ∼ 4950 L ⊙, while the Gaia distance would result in a luminosity of only ∼ 870 L ⊙ . This example illustrates that even for
AGB stars with an apparent low RUWE value, we should exercise caution when adopting the current Gaia DR2 parallaxes.


**Appendix B:** **Imaging results**


**Appendix C:** **Detections of emission from**
**molecules other than** [12] **CO**


**Appendix D:** **Line profiles**


**Appendix E:** **Results from fitting to Gaussian**
**emission distributions**


**References**


1997, The HIPPARCOS and TYCHO catalogues. Astrometric and photometric
star catalogues derived from the ESA HIPPARCOS Space Astrometry Mission, Vol. 1200
Bailer-Jones, C. A. L., Rybizki, J., Fouesneau, M., Mantelet, G., & Andrae, R.
2018, AJ, 156, 58
Bladh, S., Höfner, S., Aringer, B., & Eriksson, K. 2015, A&A, 575, A105
Bladh, S., Liljegren, S., Höfner, S., Aringer, B., & Marigo, P. 2019, A&A, 626,
A100
Brinch, C. & Hogerheijde, M. R. 2010, A&A, 523, A25
Castro-Carrizo, A., Quintana-Lacaci, G., Neri, R., et al. 2010, A&A, 523, A59
Chiavassa, A., Freytag, B., & Schultheis, M. 2018, A&A, 617, L1
Conroy, C. 2013, ARA&A, 51, 393
Danilovich, T., Teyssier, D., Justtanont, K., et al. 2015, A&A, 581, A60
Decin, L., Richards, A. M. S., Neufeld, D., et al. 2015, A&A, 574, A5
Doan, L., Ramstedt, S., Vlemmings, W. H. T., et al. 2017, A&A, 605, A28
Doan, L., Ramstedt, S., Vlemmings, W. H. T., et al. 2020, A&A, 633, A13
Draine, B. T. 1978, ApJS, 36, 595
Eriksson, K., Nowotny, W., Höfner, S., Aringer, B., & Wachter, A. 2014, A&A,
566, A95
Fonfría, J. P., Santander-García, M., Cernicharo, J., et al. 2019, A&A, 622, L14
Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1
Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1
González Delgado, D., Olofsson, H., Kerschbaum, F., et al. 2003, A&A, 411,
123
Groenewegen, M. A. T. 2017, A&A, 606, A67
Groenewegen, M. A. T. & Whitelock, P. A. 1996, MNRAS, 281, 1347
Höfner, S. 2008, A&A, 491, L1
Höfner, S., Bladh, S., Aringer, B., & Ahuja, R. 2016, A&A, 594, A108
Höfner, S. & Olofsson, H. 2018, A&A Rev., 26, 1
Homan, W., Richards, A., Decin, L., de Koter, A., & Kervella, P. 2018, A&A,
616, A34
Ivezic, Z., Nenkova, M., & Elitzur, M. 1999, arXiv e-prints

[arXiv:astro-ph/9910475]
Jura, M. 1990, in From Miras to Planetary Nebulae: Which Path for Stellar Evolution?, ed. M. O. Mennessier & A. Omont, 41–63
Jura, M. & Kleinmann, S. G. 1990, ApJ, 364, 663
Jura, M. & Kleinmann, S. G. 1992, ApJS, 79, 105


Article number, page 11 of 28

A&A proofs: manuscript no. deathstar1



Table B.1. Imaging results.



Band 6 Band 7 CO(2-1) CO(3-2)

Source θ P.A. rms θ P.A. rms F peak v c ∆v F peak v c ∆v

[”] [ [◦] ] [ [mJy] []] [”] [ [◦] ] [ [mJy] []] [Jy] [km s [−][1] ] [kms [−][1] ] [Jy] [kms [−][1] ] [km s



beam [mJy] []] [”] [ [◦] ] [ beam [mJy]



beam [mJy] []] [Jy] [km s [−][1] ] [kms [−][1] ] [Jy] [kms [−][1] ] [km s [−][1] ]



M-type semi-regular and irregular stars:

L 2 Pup 6.5 × 5.4 67.0 52 3.9 × 3.5 -70.1 103 19.8 33.3 7.5 47.2 32.7 8.0
W Hya 6.6 × 4.4 -89.1 51 4.5 × 2.9 -89.9 340 36.0 41.0 17.0 68.0 41.0 17.5
T Mic 6.3 × 4.0 -78.2 76 4.9 × 2.7 -79.1 168 17.5 25.3 12.5 20.0 25.0 13.0

Y Scl 6.5 × 4.3 81.8 71 5.1 × 2.7 89.9 138 4.9 28.8 11.5 7.8 29.0 12.0
V1943 Sgr 6.5 × 4.2 -73.1 76 5.2 × 2.7 -73.5 170 14.0 -14.8 12.7 19.0 -15.0 13.0
BK Vir 7.6 × 4.8 -89.0 112 4.9 × 3.1 -67.2 144 12.9 16.8 11.5 25.8 17.0 11.0

V Tel 6.5 × 5.4 74.3 52 4.4 × 3.8 84.9 155 11.9 -32.5 16.0 21.3 -32.8 15.5

SU Vel 6.3 × 4.5 -78.1 48 4.3 × 3.2 85.5 136 13.5 7.5 13.0 25.7 7.5 13.0

UY Cet 6.2 × 4.7 88.1 72 5.2 × 3.0 -69.5 142 9.5 4.7 15.3 18.1 4.8 15.5
SV Aqr 6.4 × 4.5 -82.9 40 4.3 × 2.8 -89.9 158 4.0 5.6 18.8 5.8 6.8 18.5
SW Vir 8.2 × 4.6 -73.2 71 4.6 × 3.3 74.7 141 36.5 -11.5 17.0 66.4 -11.5 17.0

CW Cnc 7.3 × 4.6 -75.8 53 4.2 × 3.4 83.4 161 9.5 15.0 24.0 12.8 15.0 23.3

RT Vir 8.8 × 4.4 -70.8 72 4.7 × 3.3 68.2 145 16.9 17.0 18.0 31.0 17.3 17.5

R Crt 7.1 × 4.4 81.1 52 4.4 × 2.8 -87.1 153 26.3 11.3 23.5 44.3 11.3 23.5

M-type Mira stars:

R Leo 7.0 × 4.7 -85.8 54 4.2 × 3.2 69.5 176 25.3 -0.5 15.0 57.8 -0.5 16.0
R Hya 6.6 × 4.4 -89.7 51 4.4 × 2.8 -87.6 123 26.0 -9.8 21.0 67.9 -9.8 21.5
R Hor 6.1 × 5.4 79.6 45 3.9 × 2.8 -82.9 133 54.7 37.5 13.0 76.3 37.5 13.0
RR Aql 6.2 × 5.4 -73.5 50 4.9 × 3.4 -68.3 97 19.0 27.8 16.5 27.1 27.8 16.5
IRC-10529 6.4 × 5.2 -71.9 52 4.6 × 3.4 -67.1 101 33.3 -17.8 30.5 43.4 -17.5 30.0

WX Psc 7.4 × 5.4 31.1 89 4.4 × 3.2 70.5 129 28.6 9.0 39.0 38.9 9.5 39.0

IRC+10365 6.9 × 5.6 89.0 62 4.1 × 3.4 -74.4 149 24.4 -31.3 34.5 32.4 -31.3 35.5

C-type semi-regular and irregular stars:

TW Oph 10.3 × 4.5 -84.8 72 4.5 × 2.9 -89.3 94 6.3 28.4 17.3 9.5 28.5 17.0
NP Pup 6.3 × 5.2 84.9 52 4.1 × 3.5 -80.6 105 3.0 13.3 21.5 3.4 12.8 21.5
TW Hor 6.1 × 5.7 81.0 41 4.0 × 3.1 -77.2 112 13.9 1.3 14.5 24.1 1.1 13.8

T Ind 6.0 × 5.2 -84.9 47 5.0 × 2.7 -72.7 168 5.3 15.8 12.5 8.6 15.8 11.5
RT Cap 6.8 × 3.9 -74.3 75 5.1 × 2.6 -74.0 181 5.7 -18.0 16.0 6.6 -18.0 15.0
AQ Sgr 6.4 × 4.5 -82.6 47 6.0 × 2.7 -79.7 179 8.2 21.5 22.0 9.7 21.5 23.0
U Hya 6.9 × 4.4 86.7 51 4.3 × 2.9 -86.6 144 43.3 -31.3 14.5 63.1 -31.3 14.5
W Ori 6.3 × 5.4 81.3 49 4.0 × 3.1 85.5 146 11.3 -1.5 23.0 18.0 -1.5 23.0
V Aql 7.7 × 5.0 -68.7 62 4.3 × 3.6 -79.6 123 12.8 53.5 19.0 22.9 53.8 19.5
Y Pav 9.8 × 5.0 28.3 58 4.3 × 3.8 44.1 135 12.7 -3.8 18.5 19.3 -3.5 18.0

X Vel 6.5 × 4.4 -77.5 49 4.3 × 3.2 87.3 136 8.3 -19.3 22.5 14.7 -19.3 22.5
Y Hya 7.5 × 4.3 -74.8 54 4.6 × 2.6 89.3 146 10.7 -8.5 19.0 15.0 -8.5 18.0
SS Vir 7.6 × 4.5 -85.0 112 4.9 × 3.0 -68.6 137 3.9 8.5 28.0 6.8 8.7 30.3

W CMa 7.4 × 4.2 -79.8 44 5.2 × 2.6 69.9 116 8.8 -0.3 21.5 11.4 -0.3 21.5

C-type Mira stars:

R Lep 7.4 × 3.8 -75.2 106 4.2 × 2.7 89.4 125 22.6 11.3 37.5 21.8 11.5 38.0
CZ Hya 6.9 × 4.3 -73.6 52 4.6 × 2.7 84.9 154 6.5 13.5 26.0 9.4 13.3 25.5
R For 7.2 × 4.0 -76.8 68 4.5 × 3.1 78.9 168 11.6 -2.4 34.8 20.0 -2.3 33.5

R Vol 6.3 × 6.0 -48.0 72 5.0 × 3.6 -5.0 152 14.6 -10.8 36.5 24.4 -10.8 36.5
RV Aqr 6.5 × 5.4 -67.9 50 4.5 × 3.0 -73.3 153 26.1 1.0 30.0 37.8 1.3 30.5
V688 Mon 6.4 × 4.6 -87.1 76 4.6 × 2.9 -79.0 224 25.2 3.0 28.0 33.7 3.0 27.0

V1259 Ori 6.2 × 4.6 -79.5 77 5.1 × 2.8 -71.1 229 28.9 43.0 31.0 48.0 43.3 28.5


Notes. Columns 2-7 give the imaging results: Full width at half-maximum beam-widths (major × minor axis), θ, and position angle, P.A., at the
center frequency of [12] CO spectral windows, as well as the rms noise level in both band 6 and 7, respectively, at a velocity resolution of 0.75 km s [−][1] .
Columns 8-13 give the CO line parameters: Peak flux, center velocity, and total velocity width of the line profiles of both CO transitions presented
in Figs D.1–D.6.



Jura, M., Yamamoto, A., & Kleinmann, S. G. 1993, ApJ, 413, 298
Kervella, P., Homan, W., Richards, A. M. S., et al. 2016, A&A, 596, A92

Kim, H., Trejo, A., Liu, S.-Y., et al. 2017, Nature Astronomy, 1, 0060
Lindegren, L., Lammers, U., Hobbs, D., et al. 2012, A&A, 538, A78
Maercker, M., Vlemmings, W. H. T., Brunner, M., et al. 2016, A&A, 586, A5
Mamon, G. A., Glassgold, A. E., & Huggins, P. J. 1988, ApJ, 328, 797


Article number, page 12 of 28



Marigo, P., Ripamonti, E., Nanni, A., Bressan, A., & Girardi, L. 2016, MNRAS,
456, 23


Martí-Vidal, I., Vlemmings, W. H. T., Muller, S., & Casey, S. 2014, A&A, 563,
A136


Matsuno, M., Nakagawa, A., Morita, A., et al. 2020, arXiv e-prints,
arXiv:2003.03038

Table C.1. Peak flux of detected molecular emission measured within a circular 10 [′′] aperture centered on the M-type semi-regular and irregular stars. The spectral resolution for each spectral
window is given in Sect. 3. The peak flux error is on the order of 20%.


Line Frequency Peak flux [Jy]

[GHz] L 2 Pup W Hya T Mic Y Scl V1943 Sgr BK Vir V Tel SU Vel UY Cet SV Aqr SW Vir CW Cnc RT Vir R Crt


Band 6, spectral window 1

SiO (v=1, J=5-4) 215.596 1.5 96 1.6 - 1.2 0.9 0.2 0.1 - - 1.4 0.1 0.5 4.1
34 SO (6 5 -5 4 ) 215.840 0.1 0.2  -  -  -  -  -  -  -  -  -  - 0.1 0.2
SO 2 (22 2,20 -22 1,21 ) 216.643 0.7 0.6 0.1 - - - - - - - - - 0.3 0.2
H 2 S (2 2,0 -2 1,1 ) 216.710 - - - - - - - - - - - - - SiS (v=1, J=12-11) 216.758 0.1 0.2 - - - - - - - - - - - SiO (5-4) 217.105 16.5 45 7.7 2 9.8 6.1 3.2 2.6 4 2.2 18.5 3.6 12 19

Band 6, spectral window 2

SiS (12-11) 217.818 0.2 - - - - - - - - - - - - 
Band 6, spectral window 4

29 SiS (13-12) 231.627  -  -  -  -  -  -  -  -  -  -  -  -  -  SO 2 (v 2 =1, 14 3,11 -14 2,12 ) 231.981 0.1 0.1 - - - - - - - - - - - Si [33] S (13-12) 232.629 - - - - - - - - - - - - - H 2 O (v 2 =1, 5 5,0 -6 4,3 ) 232.687 0.2 0.2 - - - - - - - - - - - 
Band 7, spectral window 1

13 CO (3-2) 330.588 6.4 1.8 0.8 1 0.9 1.8 1.1 1.6 1.6 0.5 5.5 0.7 3.0 4.0
Na [37] Cl (27-26) 330.805 - - - - - - - - - - - - - 
Band 7, spectral window 2

SO 2 (11 6,6 -12 5,7 ) 331.580 0.2 - - - - - - - - - - - - SO 2 (21 2,20 -21 1,21 ) 332.091 1.4 0.7 - - - - - - - - - - 0.5 0.5
SO 30 SiS (19-18) 2 (4 3,1 -3 2,2 ) 332.505332.550 1.4- 0.6- -- -- -- -- -- -- -- -- -- -- 0.8- 0.8
Band 7, spectral window 3

SO 2 (34 3,31 -34 2,32 ) 342.762 0.2 0.5 - - - - - - - - - - 0.3 0.2
CS (7-6) 342.883 - 0.5 - - - - - - - - - - 0.2 29 SiO (8-7) 342.981 1.3 30 6.3 1 4.4 4.7 2.5 2.6 2.8 0.2 10 2.0 7.0 8.0
SiS (v=1, J=19-18) 343.101 0.04 - - - - - - - - - - - - SO ( [3] Σ v=1, 9 8 -8 7 ) 343.829 - 0.5 - - - - - - - - - - - SO (8 8 -7 7 ) 344.311 1.4 6.5 1.9 0.2 1.2 1.4 0.4 0.4 1.2 0.1 1.8 0.5 3.7 3.0

Band 7, spectral window 4
H [13] CN (4-3) 345.340 3.4 8.7 - - 0.4 - - - 0.3 - 0.1 - 2.0 2.2

A&A proofs: manuscript no. deathstar1


Table C.2. Peak flux of detected molecular emission measured within a circular 10 [′′] aperture centered on the M-type Mira stars. The spectral
resolution for each spectral window is given in Sect. 3. The peak flux error is on the order of 20%.


Line Frequency Peak flux [Jy]

[GHz] R Leo R Hya R Hor RR Aql IRC-10529 WX Psc IRC+10365


Band 6, spectral window 1

SiO (v=1, J=5-4) 215.596 36 6.0 0.5 0.3 2.5 17 4.0
34 SO (6 5 -5 4 ) 215.840 0.1  -  - 0.1 0.1  - 0.1
SO 2 (22 2,20 -22 1,21 ) 216.643 5.7 - - 0.2 - - H 2 S (2 2,0 -2 1,1 ) 216.710 - - - - 0.3 0.2 SiS (v=1, J=12-11) 216.758 - - - - - 0.1 SiO (5-4) 217.105 36 22.4 6.7 4.2 5.7 9.6 12

Band 6, spectral window 2

SiS (12-11) 217.818 - - - - 1.8 2.9 0.9

Band 6, spectral window 4

29 SiS (13-12) 231.627  -  -  -  - 0.2 0.4 0.1
SO 2 (v 2 =1, 14 3,11 -14 2,12 ) 231.981 - - - - - - Si [33] S (13-12) 232.629 - - - - 0.1 - H 2 O (v 2 =1, 5 5,0 -6 4,3 ) 232.687 - - - - - 0.3 0.1

Band 7, spectral window 1

13 CO (3-2) 330.588 3.2 2.0 4.0 0.5 7.0 7.0 6.0
Na [37] Cl (27-26) 330.805 - - - - - 0.1 
Band 7, spectral window 2

SO 2 (11 6,6 -12 5,7 ) 331.580 - - - - - - SO 2 (21 2,20 -21 1,21 ) 332.091 0.4 - - 0.3 - - SO 30 SiS (19-18) 2 (4 3,1 -3 2,2 ) 332.505332.550 0.4- -- -- 1.9- 1.20.3 1.20.5 0.80.2

Band 7, spectral window 3

SO 2 (34 3,31 -34 2,32 ) 342.762 0.3 - - - - - CS (7-6) 342.883 0.7 0.2 - - 0.7 1.4 1.0
29 SiO (8-7) 342.981 21.5 12.5 7.0 2.0 1.3 2.7 3.1
SiS (v=1, J=19-18) 343.101 - - - - 0.3 0.4 SO ( [3] Σ v=1, 9 8 -8 7 ) 343.829 - - - - - - SO (8 8 -7 7 ) 344.311 4 1.4 1.4 1.4 0.4 0.4 0.8

Band 7, spectral window 4
H [13] CN (4-3) 345.340 7.7 0.9 - 1.4 0.6 1.7 1.6


McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical
Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J.
Bell, 127
Menzies, J. W., Feast, M. W., & Whitelock, P. A. 2006, MNRAS, 369, 783
Neri, R., Kahane, C., Lucas, R., Bujarrabal, V., & Loup, C. 1998, A&AS, 130, 1
Ramstedt, S., Mohamed, S., Olander, T., et al. 2018, A&A, 616, A61
Ramstedt, S., Mohamed, S., Vlemmings, W. H. T., et al. 2014, A&A, 570, L14
Ramstedt, S. & Olofsson, H. 2014, A&A, 566, A145
Ramstedt, S., Schöier, F. L., & Olofsson, H. 2009, A&A, 499, 515
Ramstedt, S., Schöier, F. L., Olofsson, H., & Lundgren, A. A. 2006, A&A, 454,
L103
Ramstedt, S., Schöier, F. L., Olofsson, H., & Lundgren, A. A. 2008, A&A, 487,
645
Saberi, M., Vlemmings, W. H. T., & De Beck, E. 2019, A&A, 625, A81
Samus’, N. N., Kazarovets, E. V., Durlevich, O. V., Kireeva, N. N., & Pastukhova, E. N. 2017, Astronomy Reports, 61, 80
Schöier, F. L. 2000, PhD thesis, Stockholm Observatory, SE-133 36 Saltsjöbaden, Sweden
Schöier, F. L. & Olofsson, H. 2001, A&A, 368, 969
Stanek, K. Z., Knapp, G. R., Young, K., & Phillips, T. G. 1995, ApJS, 100, 169
van Langevelde, H., Quiroga-Nuñez, L. H., Vlemmings, W. H. T., et al. 2018, in
14th European VLBI Network Symposium & Users Meeting (EVN 2018), 43
Vlemmings, W. H. T., Khouri, T., De Beck, E., et al. 2018, A&A, 613, L4
Whitelock, P., Menzies, J., Feast, M., et al. 1994, MNRAS, 267, 711


Article number, page 14 of 28

Table C.3. Peak flux of detected molecular emission measured within a circular 10 [′′] aperture centered on the C-type semi-regular and irregular stars. The spectral resolution for each spectral window
is given in Sect. 3. The peak flux error is on the order of 20%.


Line Frequency Peak flux [Jy]

[GHz] TW Oph NP Pup TW Hor T Ind RT Cap AQ Sgr U Hya W Ori V Aql Y Pav X Vel Y Hya SS Vir W CMa


Band 6, spectral window 1

SiO (5-4) 217.105 0.3 - - - 0.1 0.1 0.1 3.6 0.4 0.1 0.3 0.4 - 13 CN (N=2-1) a 217.287 0.1
13 CN (N=2-1) b 217.315  -  -  -  -  -  - 0.1  - 0.1  -  -  -  -  
Band 6, spectral window 2

13 CN (N=2-1) c 217.467  -  -  -  -  -  - 0.1  -  -  -  -  -  -  SiS (12-11) 217.818 - - - - - - - - - - - - - HC 3 N (24-23) 218.325 0.1 - - - - - - 0.2 0.1 - 0.1 0.2 - C 4 H (N=23-22) [d] 218.837 - - - - - - - - - - - - - C 4 H (N=23-22) [e] 218.875 - - - - - - - - - - - - - 
Band 6, spectral window 4

13 CS (5-4) 231.221  -  -  -  -  -  -  - 0.1 0.1  - 0.1 0.1  -  29 SiS (13-12) 231.627  -  -  -  -  -  -  -  -  -  -  -  -  -  SiC 2 (10 2,9 -9 2,8 ) 232.534 0.2 - - - - - - 0.3 0.4 - 0.2 0.6 - 
Band 7, spectral window 1

13 CO (3-2) 330.588  -  - 0.8  -  - 0.2 4.5 0.4 0.4 0.7  -  -  - 0.3
SiC 2 (14 6,9 -13 6,8 ) 330.870 0.4 - - - - - - 0.4 0.5 - 0.3 0.7 - 
Band 7, spectral window 3

SiC 2 (15 2,14 -14 2,13 ) 342.805 0.3 - - - - - - 0.1 0.5 - 0.4 0.3 - CS (7-6) 342.883 3.4 - - - 1.6 0.3 1.1 5.0 6.2 - 3.6 4.5 - 29 SiO (8-7) 342.981  -  -  -  -  -  -  -  - 0.1  -  -  -  -  
Band 7, spectral window 4
H [13] CN (4-3) 345.340 0.8 - - - 0.8 0.3 4.0 1.9 1.5 0.5 0.3 1.2 0.1 

Notes. [(][a][)] J=5/2-3/2, F1=2-1, F=2-2 ; [(][b][)] J=5/2-3/2, F1=2-2, F=2-3 ; [(][c][)] J=5/2-3/2, F1=3-2, F=4-3 ; [(][d][)] J=47/2-45/2, F=23-22 ; [(][e][)] J=45/2-43/2, F=23-22

A&A proofs: manuscript no. deathstar1


Table C.4. Peak flux of detected molecular emission measured within a circular 10 [′′] aperture centered on the C-type Mira stars. The spectral
resolution for each spectral window is given in Sect. 3. The peak flux error is on the order of 20%.


Line Frequency Peak flux [Jy]

[GHz] R Lep CZ Hya R For R Vol RV Aqr V688 Mon V1259 Ori


Band 6, spectral window 1

SiO (5-4) 217.105 1.9 0.3 2 1.9 3.2 1.0 0.8
13 CN (N=2-1) a 217.287 0.1  - 0.1  - 0.1  -  13 CN (N=2-1) b 217.315 0.1  - 0.2 0.1 0.2  -  
Band 6, spectral window 2

13 CN (N=2-1) c 217.467 0.1  - 0.1 0.1 0.1  -  SiS (12-11) 217.818 - - 0.2 - 0.7 0.7 1.5
HC 3 N (24-23) 218.325 0.2 - 0.4 0.1 0.1 0.4 0.1
C 4 H (N=23-22) [d] 218.837 - - - - - 0.2 0.4
C 4 H (N=23-22) [e] 218.875 - - - - - 0.2 0.6

Band 6, spectral window 4

13 CS (5-4) 231.221 0.2  - 0.2 0.2 0.3 0.1 0.2
29 SiS (13-12) 231.627  -  -  -  - 0.1 0.1 0.1
SiC 2 (10 2,9 -9 2,8 ) 232.534 0.1 - 0.3 0.2 0.3 0.4 0.4

Band 7, spectral window 1

13 CO (3-2) 330.588 0.9 0.6 0.8 1.4 2.5 1.6  SiC 2 (14 6,9 -13 6,8 ) 330.870 - - 0.3 0.2 0.3 0.5 
Band 7, spectral window 3

SiC 2 (15 2,14 -14 2,13 ) 342.805 - - 0.1 - - - CS (7-6) 342.883 5.6 0.5 6.8 6.5 11 5.6 29 SiO (8-7) 342.981 0.1  - 0.5 0.3 0.5  -  
Band 7, spectral window 4
H [13] CN (4-3) 345.340 3.1 0.4 2.3 2.5 5 4 

Notes. [(][a][)] J=5/2-3/2, F1=2-2, F=2-3 ; [(][b][)] J=5/2-3/2, F1=2-1, F=2-2 ; [(][c][)] J=5/2-3/2, F1=3-2, F=4-3 ; [(][d][)] J=47/2-45/2, F=23-22 ; [(][e][)] J=45/2-43/2,
F=23-22


Article number, page 16 of 28

Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA



20


15


10


5


0


20 25 30 35 40 45


15


10


5


0


10 20 30 40


16


14


12


10


8


6


4


2


0


-2
-25 -20 -15 -10 -5 0


14


12


10


8


6


4


2


0


-2
-45 -40 -35 -30 -25 -20


10


8


6


4


2


0


-10 0 10 20



50


40


30


20


10


0


10 20 30 40 50


20


15


10


5


0


10 20 30 40


20


15


10


5


0


-25 -20 -15 -10 -5 0


20


15


10


5


0


-45 -40 -35 -30 -25 -20


20


15


10


5


0


-10 0 10 20



-2
5 10 15 20 25


15


10


5


0


-5 0 5 10 15 20


4


3


2


1


0


-10 0 10 20



30


25


20


15


10


5


0


5


4


3


2


1


0


14


12


10


8


6


4


2


0



30 40 50 60


20 25 30 35 40



70


60


50


40


30


20


10


0


8


6


4


2


0


25


20


15


10


5


0



30 40 50 60


20 25 30 35 40



5 10 15 20 25


25


20


15


10


5


0


-5 0 5 10 15 20


6


5


4


3


2


1


0


-10 0 10 20



Fig. D.1. CO J = 2→1 and 3→2 line profiles measured toward the M-type AGB stars of the sample discussed in this paper. The source name is
given in the upper left corner and the transition is in the upper right corner of each plot.


Article number, page 17 of 28

40


35


30


25


20


15


10


5


0


15


10


5


0


25


20


15


10


5


0



A&A proofs: manuscript no. deathstar1


10


8


6


4


2


0



0 10 20 30


25


20


15


10


5


0


-10 0 10 20 30


25


20


15


10


5


0


-30 -20 -10 0 10


20


15


10


5


0


15 20 25 30 35 40 45


30


25


20


15


10


5


0


-20 0 20 40



14


12


10


8


6


4


2


0


-2
0 10 20 30


40


30


20


10


0


-10 0 10 20 30


70


60


50


40


30


20


10


0


-30 -20 -10 0 10


30


25


20


15


10


5


0


15 20 25 30 35 40 45


40


35


30


25


20


15


10


5


0


-20 0 20 40



-25 -20 -15 -10 -5 0 5


0 10 20 30



70


60


50


40


30


20


10


0


35


30


25


20


15


10


5


0


60


50


40


30


20


10


0



-25 -20 -15 -10 -5 0 5


0 10 20 30



-15 -10 -5 0 5 10


60


50


40


30


20


10


0


25 30 35 40 45 50


35


30


25


20


15


10


5


0


-40 -30 -20 -10 0 10



-15 -10 -5 0 5 10


80


70


60


50


40


30


20


10


0


25 30 35 40 45 50


45


40


35


30


25


20


15


10


5


0


-40 -30 -20 -10 0 10



Fig. D.2. CO J = 2→1 and 3→2 line profiles measured toward the M-type AGB stars of the sample discussed in this paper. The source name is
given in the upper left corner and the transition is in the upper right corner of each plot.


Article number, page 18 of 28

25


20


15


10


5


0



-60 -40 -20 0



Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA


35


30


25


20


15


10


5


0


-60 -40 -20 0



Fig. D.3. CO J = 2→1 and 3→2 line profiles measured toward the M-type AGB stars of the sample discussed in this paper. The source name is
given in the upper left corner and the transition is in the upper right corner of each plot.


Article number, page 19 of 28

7


6


5


4


3


2


1


0


10 20 30 40


15


10


5


0


-10 -5 0 5 10 15


6


5


4


3


2


1


0


-1
-30 -25 -20 -15 -10 -5


45


40


35


30


25


20


15


10


5


0


-40 -30 -20


14


12


10


8


6


4


2


0


-2
40 50 60 70



10


8


6


4


2


0



A&A proofs: manuscript no. deathstar1


3.5


3


2.5


2


1.5


1


0.5


0



10 20 30 40


25


20


15


10


5


0


-10 -5 0 5 10 15


7


6


5


4


3


2


1


0


-1
-30 -25 -20 -15 -10 -5


60


50


40


30


20


10


0


-40 -30 -20


25


20


15


10


5


0


40 50 60 70



-0.5
-10 0 10 20 30


6


5


4


3


2


1


0


5 10 15 20 25


8


6


4


2


0


0 10 20 30 40


12


10


8


6


4


2


0


-20 -10 0 10 20


15


10


5


0


-20 -10 0 10



8


6


4


2


0



4


3.5


3


2.5


2


1.5


1


0.5


0


-0.5
-10 0 10 20 30


5 10 15 20 25


10


8


6


4


2


0


0 10 20 30 40


20


15


10


5


0


-20 -10 0 10 20


20


15


10


5


0


-20 -10 0 10



Fig. D.4. CO J = 2→1 and 3→2 line profiles measured toward the C-type AGB stars of the sample discussed in this paper. The source name is
given in the upper left corner and the transition is in the upper right corner of each plot.


Article number, page 20 of 28

15


10


5


0


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


-40 -30 -20 -10 0


4


3


2


1


0


-10 0 10 20 30


25


20


15


10


5


0


-20 0 20 40


12


10


8


6


4


2


0


-30 -20 -10 0 10 20


30


25


20


15


10


5


0


-20 -10 0 10 20 30



Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA


12


15


10


8

10


6



5


0


-40 -30 -20 -10 0


7


6


5


4


3


2


1


0


-1
-10 0 10 20 30


25


20


15


10


5


0


-20 0 20 40


20


15


10


5


0


-30 -20 -10 0 10 20


40


35


30


25


20


15


10


5


0


-20 -10 0 10 20 30



4


2


0


10


8


6


4


2


0



-20 -10 0 10



-20 -10 0 10



-20 -10 0 10 20


7


6


5


4


3


2


1


0


-1
-10 0 10 20 30


16


14


12


10


8


6


4


2


0


-40 -20 0 20


25


20


15


10


5


0


-10 0 10 20



-20 -10 0 10 20


10


8


6


4


2


0


-10 0 10 20 30


25


20


15


10


5


0


-40 -20 0 20


35


30


25


20


15


10


5


0


-10 0 10 20



Fig. D.5. CO J = 2→1 and 3→2 line profiles measured toward the C-type AGB stars of the sample discussed in this paper. The source name is
given in the upper left corner and the transition is in the upper right corner of each plot.


Article number, page 21 of 28

A&A proofs: manuscript no. deathstar1


20 30 40 50 60 70



30


25


20


15


10


5


0



50


40


30


20


10


0



20 30 40 50 60 70



Fig. D.6. CO J = 2→1 and 3→2 line profiles measured toward the C-type AGB stars of the sample discussed in this paper. The source name is
given in the upper left corner and the transition is in the upper right corner of each plot.


Article number, page 22 of 28

Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA



10


8


6


4


2


0


35 40 45 50
v lsr [km/s]


4


3


2


1


0


-1


24 26 28 30 32 34
v lsr [km/s]


5


4


3


2


1


0


-1


12 14 16 18 20 22
v lsr [km/s]

5


4


3


2


1


0


-1


2 4 6 8 10 12 14
v lsr [km/s]

5


4


3


2


1


0


-1


0 5 10 15
v lsr [km/s]



6


4


2


0


30 32 34 36 38
v lsr [km/s]


6


4


2


0


20 22 24 26 28 30
v lsr [km/s]


6


4


2


0


-20 -18 -16 -14 -12 -10
v lsr [km/s]


4


3


2


1


0


-1


-40 -35 -30 -25
v lsr [km/s]

6


5


4


3


2


1


0


-1


0 5 10
v lsr [km/s]



10


8


6


4


2


0


35 40 45 50
v lsr [km/s]


4


3


2


1


0


-1


24 26 28 30 32 34
v lsr [km/s]


5


4


3


2


1


0


-1


12 14 16 18 20 22
v lsr [km/s]

5


4


3


2


1


0


-1


2 4 6 8 10 12 14
v lsr [km/s]

5


4


3


2


1


0


-1


0 5 10 15
v lsr [km/s]



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


8


6


4


2


0


5


4


3


2


1


0


-1


6


5


4


3


2


1


0


-1



30 32 34 36 38
v lsr [km/s]


20 22 24 26 28 30
v lsr [km/s]


-20 -18 -16 -14 -12 -10
v lsr [km/s]


-40 -35 -30 -25
v lsr [km/s]


0 5 10
v lsr [km/s]



Fig. E.1. Results from the visibility fitting to the data measured toward the M-type AGB stars of the sample discussed in this paper. The source
name is given in the upper left corner and the transition is in the upper right corner of each plot. The upper blue and orange lines show the major
and minor axis of the best-fit Gaussian in each channel, respectively. The lower red and green lines show the RA and Dec offset relative to the
center position, respectively.


Article number, page 23 of 28

A&A proofs: manuscript no. deathstar1



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


5 10 15 20 25
v lsr [km/s]

12


10


8


6


4


2


0


0 5 10 15 20
v lsr [km/s]


6


4


2


0


-20 -15 -10 -5 0
v lsr [km/s]

10


8


6


4


2


0


20 25 30 35
v lsr [km/s]


10


8


6


4


2


0


-10 0 10 20
v lsr [km/s]





-20 -15 -10 -5
v lsr [km/s]



12


10


8


6


4


2


0


-20 -15 -10 -5
v lsr [km/s]


8


6


4


2


0


10 15 20 25
v lsr [km/s]


8


6


4


2


0


-5 0 5
v lsr [km/s]

12


10


8


6


4


2


0


32 34 36 38 40 42
v lsr [km/s]

10


8


6


4


2


0


-30 -25 -20 -15 -10 -5
v lsr [km/s]



8


6


4


2


0


5 10 15 20 25
v lsr [km/s]

12


10


8


6


4


2


0


0 5 10 15 20
v lsr [km/s]


6


4


2


0


-20 -15 -10 -5 0
v lsr [km/s]

10


8


6


4


2


0


20 25 30 35
v lsr [km/s]


10


8


6


4


2


0


-10 0 10 20
v lsr [km/s]



10


8


6


4


2


0


10


8


6


4


2


0


12


10


8


6


4


2


0


10


8


6


4


2


0



10 15 20 25
v lsr [km/s]


-5 0 5
v lsr [km/s]


32 34 36 38 40 42
v lsr [km/s]


-30 -25 -20 -15 -10 -5
v lsr [km/s]



Fig. E.2. Results from the visibility fitting to the data measured toward the M-type AGB stars of the sample discussed in this paper. The source
name is given in the upper left corner and the transition is in the upper right corner of each plot. The upper blue and orange lines show the major
and minor axis of the best-fit Gaussian in each channel, respectively. The lower red and green lines show the RA and Dec offset relative to the
center position, respectively.


Article number, page 24 of 28

10


8


6


4


2


0



|C+10365|CO(2|
|---|---|
|||
|||


-40 -30 -20
v lsr [km/s]



Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA


10


8


6


4


2


0

|RC+10365|CO(3-|
|---|---|
|||
|||



-40 -30 -20
v lsr [km/s]



Fig. E.3. Results from the visibility fitting to the data measured toward the M-type AGB stars of the sample discussed in this paper. The source
name is given in the upper left corner and the transition is in the upper right corner of each plot. The upper blue and orange lines show the major
and minor axis of the best-fit Gaussian in each channel, respectively. The lower red and green lines show the RA and Dec offset relative to the
center position, respectively.


Article number, page 25 of 28

A&A proofs: manuscript no. deathstar1



5


4


3


2


1


0


-1


5 10 15 20
v lsr [km/s]


4


3


2


1


0


10 12 14 16 18 20 22
v lsr [km/s]

6


5


4


3


2


1


0


-1


10 15 20 25 30
v lsr [km/s]

5


4


3


2


1


0


-1


-10 -5 0 5 10
v lsr [km/s]

6


5


4


3


2


1


0


-1


-10 -5 0
v lsr [km/s]



5


4


3


2


1


0


-1


5 10 15 20
v lsr [km/s]


4


3


2


1


0


10 12 14 16 18 20 22
v lsr [km/s]

6


5


4


3


2


1


0


-1


10 15 20 25 30
v lsr [km/s]

5


4


3


2


1


0


-1


-10 -5 0 5 10
v lsr [km/s]

6


5


4


3


2


1


0


-1


-10 -5 0
v lsr [km/s]



6


5


4


3


2


1


0


-1





20 25 30 35
v lsr [km/s]



5


4


3


2


1


0


-1


20 25 30 35
v lsr [km/s]


5


4


3


2


1


0


-1


-4 -2 0 2 4 6 8
v lsr [km/s]

5


4


3


2


1


0


-1


-24 -22 -20 -18 -16 -14 -12
v lsr [km/s]


10


8


6


4


2


0


-35 -30 -25
v lsr [km/s]


5


4


3


2


1


0


-1


45 50 55 60
v lsr [km/s]



6


5


4


3


2


1


0


-1


5


4


3


2


1


0


-1



-4 -2 0 2 4 6 8
v lsr [km/s]



-24 -22 -20 -18 -16 -14 -12
v lsr [km/s]



12


10


8


6


4


2


0


6


5


4


3


2


1


0


-1



-35 -30 -25
v lsr [km/s]


45 50 55 60
v lsr [km/s]



Fig. E.4. Results from the visibility fitting to the data measured toward the C-type AGB stars of the sample discussed in this paper. The source
name is given in the upper left corner and the transition is in the upper right corner of each plot. The upper blue and orange lines show the major
and minor axis of the best-fit Gaussian in each channel, respectively. The lower red and green lines show the RA and Dec offset relative to the
center position, respectively.


Article number, page 26 of 28

Ramstedt et al.: DEATHSTAR: Nearby AGB stars with ALMA ACA



5


4


3


2


1


0


-1


8


7


6


5


4


3


2


1


0


-1


15


10


5


0


6


5


4


3


2


1


0


-1


7


6


5


4


3


2


1


0


-1



-30 -25 -20 -15 -10
v lsr [km/s]


-5 0 5 10 15 20
v lsr [km/s]


0 10 20 30
v lsr [km/s]


-15 -10 -5 0 5 10 15
v lsr [km/s]


-10 -5 0 5 10 15
v lsr [km/s]



8


7


6


5


4


3


2


1


0


-1


-15 -10 -5 0
v lsr [km/s]

5


4


3


2


1


0


-1


-10 -5 0 5 10
v lsr [km/s]

5


4


3


2


1


0


-1


5 10 15 20 25
v lsr [km/s]


6


5


4


3


2


1


0


-1


-30 -20 -10 0
v lsr [km/s]


6


4


2


0


-10 -5 0 5 10 15
v lsr [km/s]



8


7


6


5


4


3


2


1


0


-1


-15 -10 -5 0
v lsr [km/s]

5


4


3


2


1


0


-1


-10 -5 0 5 10
v lsr [km/s]

5


4


3


2


1


0


-1


5 10 15 20 25
v lsr [km/s]


6


5


4


3


2


1


0


-1


-30 -20 -10 0
v lsr [km/s]


6


4


2


0


-10 -5 0 5 10 15
v lsr [km/s]



5


4


3


2


1


0


-1


-30 -25 -20 -15 -10
v lsr [km/s]

8


7


6


5


4


3


2


1


0


-1


-5 0 5 10 15 20
v lsr [km/s]

15


10


5


0


0 10 20 30
v lsr [km/s]


5


4


3


2


1


0


-1


-15 -10 -5 0 5 10 15
v lsr [km/s]


6


5


4


3


2


1


0


-1


-10 -5 0 5 10 15
v lsr [km/s]



Fig. E.5. Results from the visibility fitting to the data measured toward the C-type AGB stars of the sample discussed in this paper. The source
name is given in the upper left corner and the transition is in the upper right corner of each plot. The upper blue and orange lines show the major
and minor axis of the best-fit Gaussian in each channel, respectively. The lower red and green lines show the RA and Dec offset relative to the
center position, respectively.


Article number, page 27 of 28

10


8


6


4


2


0



|259 Ori|CO(2-1|
|---|---|
|||


30 35 40 45 50 55
v lsr [km/s]



A&A proofs: manuscript no. deathstar1


10


8


6


4


2


0

|V1259 Ori|CO(3-2)|
|---|---|
|||



30 35 40 45 50 55
v lsr [km/s]



Fig. E.6. Results from the visibility fitting to the data measured toward the C-type AGB stars of the sample discussed in this paper. The source
name is given in the upper left corner and the transition is in the upper right corner of each plot. The upper blue and orange lines show the major
and minor axis of the best-fit Gaussian in each channel, respectively. The lower red and green lines show the RA and Dec offset relative to the
center position, respectively.


Article number, page 28 of 28


</paper>

## Items to check

```json
[
 {
  "path": "data.simulations_or_models_as_data[0].evidence[0]",
  "value": "Previous best-fit 1D radiative transfer models of six stars (3 M, 3 C), turned into image cubes and run through the CASA ALMA simulator",
  "failed_quote": "The subsample consists of six stars: three M-type and three C-type stars of which there is one low-, one intermediate-, and one high-mass-loss-rate source for each type."
 },
 {
  "path": "processing.imaging.task.evidence[0]",
  "value": "CASA (clean) imaging; each spectral window imaged separately",
  "failed_quote": "Each spectral win dow in both bands were imaged separately"
 },
 {
  "path": "reproducibility.data_public_as_stated.evidence[0]",
  "value": "Reprocessed images available through CDS and project website; raw data in ALMA archive",
  "failed_quote": "Each spectral win dow in both bands were imaged separately and can be accessed through CDS (see also www.astro.uu.se/deathstar)."
 }
]
```
