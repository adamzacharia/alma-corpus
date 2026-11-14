# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...693A.237I\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. draft ©ESO 2025
January 23, 2025

### **The ALMA-CRISTAL Survey**

##### Spatial extent of [C ii ] line emission in star-forming galaxies at z = 4 − 6


Ryota Ikeda [1][,][ 2], Ken-ichi Tadaki [3], Ikki Mitsuhashi [2][,][ 4], Manuel Aravena [5], Ilse De Looze [6],
Natascha M. Förster Schreiber [7], Jorge González-López [5][,][ 8][,][ 9], Rodrigo Herrera-Camus [10], Justin Spilker [11],
Loreto Barcos-Muñoz [12][,][ 13], Rebecca A. A. Bowler [14], Gabriela Calistro Rivera [15], Elisabete da Cunha [16][,][ 17],
Rebecca Davies [17][,][ 18], Tanio Díaz-Santos [19][,][ 20], Andrea Ferrara [21], Meghana Killi [5], Lilian L. Lee [7], Juno Li [16],
Dieter Lutz [7], Ana Posses [5][,][ 11], Renske Smit [22], Manuel Solimano [5], Kseniia Telikova [5], Hannah Übler [23][,][ 24],
Sylvain Veilleux [25][,][ 26], and Vicente Villanueva [10]


_(A_ ffi _liations can be found after the references)_


Received ; accepted;


**ABSTRACT**


We investigate the spatial extent and structure of the [C ii] line emission in a sample of 34 galaxies at _z_ = 4 − 6 from the [C ii] Resolved
ISM in STar-forming galaxies with ALMA (CRISTAL) Survey. By modeling the distribution of the [C ii] line emission in the interferometric
visibility data directly, we derive the effective radius of [C ii] line emission assuming an exponential profile. These measurements comprise not
only isolated galaxies but also interacting systems that were identified thanks to the high spatial resolution of the data. The [C ii] line radius
ranges from 0.5 to 3.5 kpc with an average value of ⟨ _R_ _e_,[CII] ⟩ = 1.90 kpc. We compare the [C ii] sizes with the sizes of rest-frame ultraviolet (UV)
and far-infrared (FIR) continua, which were measured from the HST F160W images and ALMA Band-7 continuum images, respectively. We
confirm that the [C ii] line emission is more spatially extended than the continuum emission, with average size ratios of ⟨ _R_ _e_,[CII] / _R_ _e_,UV ⟩ = 2.90
and ⟨ _R_ _e_,[CII] / _R_ _e_,FIR ⟩ = 1.54, although about half of the FIR-detected sample shows a comparable spatial extent between the [C ii] line and the FIR
continuum emission ( _R_ _e_,[CII] ≈ _R_ _e_,FIR ). The residual visibility data of the best-fit model do not show statistical evidence of flux excess, indicating
that the [C ii] line emission in star-forming galaxies can be characterized by an extended exponential disk profile. Overall, our results suggest that
the spatial extent of [C ii] line emission can primarily be explained by photodissociation regions associated with star formation activity, while the
contribution from diffuse neutral medium (atomic gas) and the effects of past merger events may further expand the [C ii] line distributions, causing
their variations among our sample. Finally, we report the negative correlation between the [C ii] surface density (Σ [CII] ) and the Lyα equivalent
width (EW Lyα ), and a possible negative correlation between _R_ _e_,[CII] / _R_ _e_,UV and EW Lyα, which may be in line with the scenario that atomic gas
component largely contributes to the extended [C ii] line emission. Future three-dimensional analysis of Lyα and Hα lines will shed light on the
association of the extended [C ii] line emission with atomic gas and outflows.


**Key words.** galaxies:evolution – galaxies:formation – galaxies:high redshift – galaxies:ISM



**1.** **Introduction**


Understanding the interplay between gas, dust, and stars in
galaxies in the early Universe is one of the biggest topics in
modern extragalactic astronomy. In particular, the cold interstellar medium (ISM), which can be interpreted as a direct fuel for
forming stars, is essential as it becomes the dominant contributor
to the baryonic mass toward high redshift (Tacconi et al. 2020).
In this context, far-infrared (FIR) fine-structure lines have been
known as an effective probe for star formation and the ISM of
galaxies.
The [C ii] [2] _P_ 3/2 − [2] _P_ 1/2 fine-structure line emission (ν rest =
1900.537 GHz, hereafter [C ii] line), emitted from ionized carbon (C [+] ), is one of the main coolants of the ISM among the
FIR emission lines and has been the most popular tracer with
which to study the cool gas component in high-redshift galaxies ( _z_ ≳ 4; Carilli & Walter 2013), as its redshifted millimeter
wavelength is accessible through the atmospheric windows. Ionized carbon is excited by photoelectric heating of gas, whereby
electrons are emitted from small dust grains or polycyclic aromatic hydrocarbons (PAHs) that absorb far-ultraviolet (FUV)
photons from star-forming regions. Therefore, it has been suggested that [C ii] line emission can be used as a good tracer of



photodissociation regions (PDRs; Hollenbach & Tielens 1999;
Wolfire et al. 2022), as well as a star formation rate (SFR) indicator from nearby star-forming galaxies (SFGs; e.g., Stacey et al.
1991; Pineda et al. 2014; Kapala et al. 2015; De Looze et al.
2014; Herrera-Camus et al. 2015; Lapham et al. 2017; Bigiel
et al. 2020; but see Díaz-Santos et al. 2013 for starburst galaxies) to high-redshift galaxies (e.g., Vallini et al. 2015; Carniani
et al. 2018; Schaerer et al. 2020; Liang et al. 2024). At the same
time, [C ii] line emission is also used as a tracer of molecular gas
(e.g., Madden et al. 1997; Langer et al. 2014; Zanella et al. 2018;
Dessauges-Zavadsky et al. 2020; Madden et al. 2020; Vizgan
et al. 2022a; Aravena et al. 2024) and atomic gas (e.g., Heintz
et al. 2021; Heintz et al. 2022; Vizgan et al. 2022b), which may
be compatible with the SFR tracer if the Kennicutt-Schmidt relation (Kennicutt 1998) holds. However, it has been known that the

[C ii] line emission can originate from multiple phases of ISM
beyond PDRs, such as ionized gas, making the interpretation
of [C ii] line emission less straightforward. With these potential
capabilities, a large number of recent studies focusing on ISM
conditions in high-redshift galaxies ( _z_ ≳ 4) rely on observations
of [C ii] line emission, thanks to the capability of the Atacama


Article number, page 1 of 23

_A&A proofs:_ manuscript no. draft



Large Millimeter/submillimeter Array (ALMA) and the Northern Extended Millimeter Array (NOEMA) interferometer.
If the majority of [C ii] line emission indeed originates from
PDRs, one would expect its spatial extent in galaxies to also
trace the region where active star formation takes place, which is
bright in rest-frame ultraviolet (UV) continuum emission from
young stellar populations. In contrast to this expectation, one
remarkable feature of the [C ii] line emission in high-redshift
galaxies is that they are more spatially extended than what is
observable through optical/near-infrared wavelengths.
Several studies have reported comparisons of spatial extent
between [C ii] line emission and the rest-frame UV continuum
observed by the Hubble Space Telescope (HST) for galaxies at
_z_ - 4, both for individual galaxies (e.g., Carniani et al. 2018;
Fujimoto et al. 2020) and for stacked images (e.g., Fudamoto
et al. 2022), providing the general picture that at high redshift
the [C ii] sizes are larger than the UV sizes by a factor of more
than two. Furthermore, Fujimoto et al. (2019) report the detection of a 10 kpc scale “[C ii] halo” with a beam-convolved radius
of 10 kpc ( _R_ _e_,[CII] = 5.6±0.1 kpc), which can be characterized by
a two-component structure in the radial profile, by stacking 18
SFGs at _z_ = 5 − 7. With the detection of 75 [C ii] line emission
from the ALPINE Survey (Le Fèvre et al. 2020; Béthermin et al.
2020; Faisst et al. 2020), Ginolfi et al. (2020b) found evidence
of the “[C ii] halo” through the stacking analysis and the broad
spectral feature for a subsample of galaxies with higher SFRs,
indicative of ongoing star-formation-driven outflows. Although
a visual classification based on morphology and kinematics was
conducted (Le Fèvre et al. 2020), the studies referred to above
cannot rule out the possibility that [C ii] line emission from close
pairs or mergers is blended due to low spatial resolution (∼ 1 [′′] ).
A handful of studies have also compared [C ii] line emission with the underlying FIR continuum emitted from dust
grains heated by star formation or active galactic nuclei (AGNs;
e.g., Gullberg et al. 2018; Venemans et al. 2020; Díaz-Santos
et al. 2021; Izumi et al. 2021a,b; Umehata et al. 2021; Pozzi
et al. 2024; Bischetti et al. 2024; Wang et al. 2024), although
these sources tend to be biased toward submillimeter galaxies or
quasars due to their brightness in the FIR continuum. These studies show that the [C ii] line emission is comparable to or more
extended than the FIR continuum emission, but the differences
are not as significant as those for the rest-frame UV emission.
Through the stacking analysis of 27 quasars at _z_ ≳ 6, Novak
et al. (2020) found a comparable spatial extent between [C ii]
line and FIR continuum emission extending up to ∼ 10 kpc with
no sign of broad line wings in stacked [C ii] line spectra.
Extended [C ii] line emission beyond the rest-frame UV
and/or FIR continua directly implies the presence of metalenriched gas up to a circumgalactic medium (CGM) scale even
in the early Universe, and has been a matter of debate in recent years, given that cosmological zoom-in simulations could
not reproduce such extended [C ii] line emission (Fujimoto et al.
2019; Arata et al. 2020). Multiple scenarios have been proposed,
such as satellite galaxies, extended star formation activity, cold
streams, and outflows. Recent semi-analytical models support
that the two-component halo structure in [C ii] line emission can
be explained by cold outflows (Pizzati et al. 2020, 2023), but
none of the above scenarios are observationally conclusive yet.
There are two reasons why it is difficult to elucidate the origin of
such extended [C ii] line emission. First, [C ii] line emission can
originate from multiple gas phases (ionized or neutral, atomic
or molecular, PDR or H ii regions, and shocked gas); thus, integrated [C ii] line emission is likely to trace a mixture of them.
Second, previous [C ii] line observations were mostly performed


Article number, page 2 of 23



with a spatial resolution of ∼ 1 [′′] (∼ 6 kpc in a physical scale at
_z_ = 5), hampering the measurements of accurate sizes and the
study of morphology below this scale.
Therefore, to narrow down the origin of [C ii] line emission
at high redshift, it is necessary to study galaxies at high resolution and compare them with other tracers. In fact, several studies
have attempted to follow up the [C ii] line at high resolution with
improved sensitivity, and have demonstrated that ALMA is capable of characterizing the [C ii] line in typical SFGs at _z_ = 4 − 7
down to a kiloparsec scale (Herrera-Camus et al. 2021; Akins
et al. 2022; Lambert et al. 2023; Posses et al. 2023). Spatially resolved studies of [C ii] line emission have recently been reported
for two systems (Solimano et al. 2024; Posses et al. 2024) as
a part of the [C ii] Resolved ISM in STar-forming galaxies with
ALma (CRISTAL) Survey (Herrera-Camus et al. in prep) [1] . Solimano et al. (2024) discovered an elongated [C ii] line feature
associated with the J1000+0234 system, composed of a dusty
star-forming galaxy and a Lyman-break galaxy (CRISTAL-01a),
while several scenarios (e.g., a conical outflow, a cold accretion
stream) are possible for its origin. Posses et al. (2024) analyzed
CRISTAL-05, which was previously claimed as a “[C ii] halo”
(Fujimoto et al. 2020), and found a complex kinematical structure, implying that CRISTAL-05 is likely to be a merging system. Both studies exemplify the diverse characteristics of [C ii]
line emission after the Epoch of Reionization and the necessity
of high-resolution ALMA observations to understand their intrinsic morphology and structure. Nonetheless, each study stated
above remains a case study, and it is difficult to draw general conclusions even by compiling these samples. A systemic census of
deep and high-resolution [C ii] line observations with a larger
and homogeneous sample is needed to provide a more general
picture.
In this paper, we report on the size measurement and search
for an extended halo component of the [C ii] line emission in
SFGs at _z_ = 4 − 6. To analyze pure signals obtained from the
interferometer without any processes of Fourier transform – that
is, synthesis imaging – we focus on the analysis of interferometric visibility data throughout this paper. We first describe the
CRISTAL Survey, the galaxy sample, and the archival data that
we used in this study in Section 2. Section 3 presents the analysis
of visibility modeling, including the classification based on multiplicity in either [C ii] line or rest-frame UV emission. We report
the main results and discussions on the extended [C ii] line emission and correlation with other galaxy properties in Section 4 and
summarize this study in Section 5.
Throughout this paper, we assume a standard ΛCDM cosmology with _H_ 0 = 70 km s [−][1] Mpc [−][1], Ω M = 0.3, and Ω Λ = 0.7.
We refer to the term “[C ii] halo” as a secondary structure which
is more extended than the primary [C ii] line emission in the central regions. We use the notation of _R_ _e_,X as a _circularized_ effective radius of a tracer X, a product of the major-axis effective
radius, and a square root of the minor-to-major axis ratio (denotated as _q_ ), unless otherwise noted.


**2.** **Data**


_2.1._ _The CRISTAL Survey_


In this study, we use the data taken from the CRISTAL
Survey, an ALMA Cycle 8 Large Program (Project ID:
#2021.1.00280.L, PI: R. Herrera-Camus). The observations
were carried out during ALMA Cycle 8 and 9, and were com

1 `[https://sites.google.com/view/alma-cristal](https://sites.google.com/view/alma-cristal)`

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6



pleted in April 2023. The primary aim of the survey is to spatially resolve both [C ii] line and FIR continuum emission on
∼ 1 kpc scales with ALMA Band 7 observations for 19 starforming main sequence galaxies at _z_ = 4 − 6. The targets were
drawn from the ALPINE Survey (Le Fèvre et al. 2020). Targets
were mass-selected with the selection of log( _M_ ⋆ / _M_ ⊙ ) ≥ 9.5
and were also required to have observations in the HST/Wide
Field Camera 3 (WFC3) F160W filter. These HST images were
primarily obtained through observations of the CANDELS Survey (Grogin et al. 2011) as well as the COSMOS-DASH Survey
(Momcheva et al. 2017; see more details in Faisst et al. 2020 and
Herrera-Camus et al. in prep). Here, we summarize aspects of
the ALMA observations that are relevant to the analysis of this
study.
The combination of multi-configuration observations is essential to achieve both sufficiently large maximum recoverable
scale (MRS) and high spatial resolution. Therefore, each target was observed using multiple configurations of the ALMA
12m array, one with compact (C43-1/2/3) and another with extended (C43-4/5/6) array configuration. The former covers low
spatial frequencies ( _uv_ distance ≲ 150 - 300 kλ) [2] in the visibility
plane that are sensitive to large-scale structure (θ beam = 0 [′′] . 29 1 [′′] . 00, θ MRS = 5 [′′] . 28 - 9 [′′] . 79), while the latter covers high spatial
frequencies ( _uv_ distance ≳ 350 - 1500 kλ, depending on the target) that are sensitive to small-scale structure (θ beam = 0 [′′] . 07 0 [′′] . 35, θ MRS = 1 [′′] . 15 - 5 [′′] . 15).
We used the ALMA correlators of the 1.875 GHz width spectral windows (SPWs) with the frequency division mode (FDM).
The observing [C ii] frequency for each object was adjusted in
the middle of two adjacent SPWs in the upper sideband unless
the [C ii] line emission was not detected in the ALPINE Survey
(Béthermin et al. 2020).


_2.2._ _ALMA archive_


2.2.1. The ALPINE Survey


To search for faint extended emission, deep integration in the
more compact array configuration, covering short spatial frequencies, is particularly important. Therefore, we combined
the data from the ALPINE Survey (#2017.1.00428.L) with the
CRISTAL data to achieve better sensitivity to the extended struc
ture.

Contrary to the CRISTAL Survey, the ALPINE Survey
adopts the Time Division Mode for the SPW setup, in which
the edges of 2 GHz bandwidth are severely affected by low
power. We find that in three sources the [C ii] lines spread across
the two adjacent SPWs with insufficient overlapping frequencies
(CRISTAL-06, CRISTAL-08, and CRISTAL-23c), and therefore
for these fields we decided not to combine the ALPINE data
in our analysis. Also, we did not include the ALPINE data of
CRISTAL-07c, a serendipitously detected galaxy at _z_ = 5.16, as
it is located at the edge of the Band-7 field of view (FoV) with
the primary beam gain level of ∼ 0.3, while in the CRISTAL Survey, the FoV is adjusted to have comparable sensitivity in both
CRISTAL-07a/07b and CRISTAL-07c.


2.2.2. The CRISTAL+ Sample


In addition to the main targets of the CRISTAL survey, there
exist several programs that used ALMA to observe [C ii] line


2 We use a term of ‘ _uv_ distance’ as a radial distance of visibility data
in the ( _u_, _v_ ) plane in units of kλ, defined as _uv_ distance = √ _u_ [2] + _v_ [2] .



**Fig. 1.** Classification of the galaxies based on a multiplicity of [C ii] line
(with contours) and rest-frame UV (background, HST/WFC3 F160W)
emission. A 5 [′′] × 5 [′′] region is shown in each panel. The contours start at
2σ and increase in steps of 3σ until 20σ. The Gaussian FWHM fit from
the synthesized dirty beam is shown as a white ellipse in the lower-left
corner of each panel. [3] Two arrows shown in a panel of multiple-[C ii]
(CRISTAL-06a) correspond to two [C ii] line components (denoted as
‘W’ and ‘E’) that are visually identified.


emission with similar resolutions and sensitivities. This includes
six galaxies: HZ4, HZ7, HZ10, DEIMOS_COSMOS_818760,
DEIMOS_COSMOS_873756, and vuds_cosmos_8326. We
have included these archival data as the supplementary sample of the CRISTAL Survey and hereafter refer to these six
targets as CRISTAL-20 to CRISTAL-25 (Herrera-Camus et al.
in prep). The [C ii] line emission of the first three was initially reported by Capak et al. (2015) and followed up by
individual projects for high-resolution data (#2018.1.01605.S;
Herrera-Camus et al. 2021, #2018.1.01359.S; Lambert et al.
2023, #2019.1.01075.S; Villanueva et al. 2024 and Telikova et al.
2024). CRISTAL-20 was also observed in the ALPINE Survey as DEIMOS_COSMOS_494057. The latter three are the
three brightest objects in [C ii] line emission among the sample of the ALPINE Survey (Béthermin et al. 2020) and followed up at higher resolution under the ALMA Cycle 7 program
(#2019.1.00226.S; Devereaux et al. 2024). We combine the data
taken by the ALPINE Survey with these follow-up observations,
similar to the CRISTAL main targets.
In summary, the data set of this study comprises 24 ALMA
Band-7 fields, containing 35 main-sequence SFGs and two dusty
star-forming galaxies (DSFGs) detected in [C ii] line at _z_ = 4 −
6. We excluded CRISTAL-18 from the analysis because we do
not detect [C ii] line emission from this source. We present the
list of our sample cross-matched to the other names presented in
previous studies in Table A.1.


3 However, we note that a synthesized dirty beam created using multiple array configurations frequently deviates from a single Gaussian
profile and exhibits an elongated feature toward larger scales. Thus, we
caution the reader that most of the dirty images presented in this paper are convolved with a point spread function (PSF) elongated than a
single Gaussian.


Article number, page 3 of 23

_A&A proofs:_ manuscript no. draft



**3.** **Analysis**


_3.1._ _Classification based on multiplicity_


By virtue of a kiloparsec-scale resolution in [C ii] line emission
and ancillary multi-wavelength data of our sample, we can compare the spatial extent between [C ii] line and UV continuum
emission including complex systems such as interacting galaxies. One possible origin of extended [C ii] line emission is the
presence of tidal features or gas removal caused by mergers
(Solimano et al. 2024; Posses et al. 2024). Therefore, we first
classified the sample based on whether each galaxy is likely to
be physically associated with other galaxies. Mitsuhashi et al.
(2024) classified the CRISTAL sample into single and multiple
sources solely based on the multiplicity in HST/WFC3 F160W
images. In this study, we take a step forward to add information
from the [C ii] line distribution to visually classify the CRISTAL
sample into four categories:


(a) single - an isolated galaxy with a single component of the

[C ii] line emission. We classify 17 sources (∼ 50 %) of the
CRISTAL sample as single.

(b) pair - a pair of [C ii] line detections with a projected angular
separation of less than ∼ 3 arcsec. The velocity offset among
the pair is confirmed to be small (<300 km/s) so that there is
an overlap of [C ii] line frequencies. We classify nine sources

∼
( 30 %) as pair.

(c) multiple-UV - a system comprising of multiple compact
blobs in the UV continuum with overlapping extended [C ii]
line emission. Such systems are likely to be complex merging systems instead of unevenly dust-obscured systems,
since their FIR continuum emission is either faint (S/N<
5) or entirely overlapping the UV blobs (Mitsuhashi et al.
2024). The difference from the pair systems is that the

[C ii] line emission cannot be resolved into each UV counterpart with the existing data. We classified five sources
(CRISTAL-01a, CRISTAL-01b, CRISTAL-02, CRISTAL10, and CRISTAL-13) into this category.

(d) multiple-[C ii] - a system in which multiple peaks in [C ii]
line emission can be found around a single UV component.
Only CRISTAL-06a exhibits this feature.


Figure 1 summarizes our classification, showcasing examples of the [C ii] line and rest-frame UV distributions for each
class. We note, however, that this is still a crude classification, as
we do not consider the dynamical state of each galaxy obtained
from kinematical analysis. For example, we classify CRISTAL05 as single from its appearance. A detailed kinematical analysis
of the [C ii] line revealed that it is actually a complex galaxy pair
projected along the line of sight (Posses et al. 2024).
We also find that three galaxies (CRISTAL-11, CRISTAL15, and CRISTAL-17) classified as single have pair-like morphology when looked with sharper images taken by James Webb
Space Telescope (JWST; Lines et al. 2024). However, the resolution of the [C ii] line emission is coarser than the separation of
two clumps identified by JWST, and thus it would be difficult to
characterize their sizes and perform the one-to-one comparison.
We thus decide to rely on the classification based on rest-frame
UV morphology primarily due to the data homogeneity, and we
note that the discussions and conclusions we present in the following would not significantly be affected by the choice of our
classification, because the sizes of the continuum emission are
not constrained for two out of these three galaxies (Table 2).


Article number, page 4 of 23



v [km/s]
+750 +500 +250 0 -250 -500 -750











283.6 284.0 284.4 284.8

obs [ [GHz]]


**Fig.** **2.** [C ii] line spectrum of CRISTAL-03 extracted from a 1-arcsec
aperture. The best-fit Gaussian is shown as a solid red curve. We bin
the frequency range of the filled region for the [C ii] size measurements,
which corresponds to ±2σ from the central frequency.


_3.2._ _Size measurements_


3.2.1. [C ii ] line emission


The data from the CRISTAL Survey with a kiloparsec-scale resolution allows us to robustly quantify the sizes of [C ii] line emission. While the majority of the sample has a sufficient signal-tonoise ratio (S/N) to perform size measurements in the image
domain, several sources have a moderate S/N of 5 ≲ S/N ≲ 10.
In such cases, the measured sizes in the image domain could be
overestimated, because either the best-fit model takes noise into
account, or the smearing effect of the clean beam affects the fittings (Tadaki et al. 2020; Mitsuhashi et al. 2024). In addition, the
images created through the CLEAN algorithm may overestimate
the flux densities outside the CLEAN masks due to the deviation of the synthesized dirty beam from a single Gaussian. To
avoid these issues, we consistently perform our [C ii] size measurements by modeling interferometric visibility data. The visibility analysis is also favorable assessing faint extended features
in [C ii] line emission, as the imaging procedure requires several
parameters to be considered (e.g., weighting of visibility data,
threshold, size of the masked region for the CLEAN algorithm)
and therefore complicates the optimization of the best parameter
sets (Jones et al. 2023).
As a first step of the [C ii] size measurements, we define the
velocity range (∆ _v_ ) of [C ii] line emission. To perform a quantitatively fair comparison of [C ii] sizes among our sample in terms
of velocity width range, we took the following steps to define the
line width of the [C ii] line emission and create a form of visibility data optimized for size measurements: (1) extract spectrum
with a 1-arcsec aperture from the data cube (20 km/s width per
channel). Here, we used the data cube of the [C ii] line emission,
produced by the `CASA/tclean` task (CASA Team et al. 2022).
The `tclean` task was performed with `auto-multithresh` algorithm and cleaned down to 1σ (Herrera-Camus et al. in prep).
We adopted the robust parameter of either Briggs ( _R_ = 0.5) or
Natural ( _R_ = 2.0) weighting that creates the synthesized beam
size of θ beam = 0 [′′] . 3 – 0 [′′] . 5, (2) fit the extracted spectrum with a
single Gaussian _f_ (ν) ∝ exp[(ν − ν 0 ) [2] /2σ [2] ] using the `curve_fit`
function within the `scipy` package (Virtanen et al. 2020). From
the best-fit Gaussian function, we adopted the spectral range that

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6


**Fig. 3.** Visualization of the visibility modeling of the [C ii] line emission (white contours) in four systems that we showed in Figure 1. The left panel
shows the dirty image of a single cube used for the visibility modeling (Section 3.2). The Gaussian FWHM fit from the dirty beam is shown as a
white ellipse in the lower-left corner. The middle and right panel show the best-fit exponential disk model and the residual created by subtracting
the model from the data, respectively. The contours start at 2σ and increase in steps of 3σ until 20σ. The residual maps do not show any peaks
above the 2σ level around the rest-frame UV counterpart, which indicates that the observed emission is characterized by the best-fit model well.
The rest of the sample is shown in Figure A.1 and A.2.



contains 95 % (= [2.5 %, 97.5 %]) of the total [C ii] line flux, corresponding to 4σ (±2σ from the central frequency ν 0 ) width
of Gaussian (≈ 1.7 Gaussian FWHM). We show a spectrum of
CRISTAL-03 as an example in Figure 2. The ±2σ velocity range
includes almost all of the [C ii] line emission, which assures that
the [C ii] size measurements will be performed by fitting the representative velocity range of the emission. (3) Finally, we created a visibility measurement set that contains only information
on the spectral range calculated above. Here, we used the visibility data where the FIR continuum emission was subtracted
by using `CASA/uvcontsub` task. The fitting of continuum slope
was performed in the spectral range avoiding the [C ii] frequency
of each object. We then binned the visibilities into a single channel by specifying `nchan` `=` `1` in the `CASA/mstransform` task.
As an exceptional case, we fit the [C ii] spectrum of CRISTAL22a, which shows a clear double-peaked line profile, with a double Gaussian. This exceptionally broad and complex [C ii] spectrum of CRISTAL-22a is likely due to a combination of merger
and complex kinematical structure of the central component of
CRISTAL-22a, which are verified from both [O iii] 5007Å line
emission map (Jones et al. 2024) and detailed kinematical analysis of the [C ii] line emission (Telikova et al. 2024).
We used the `UVMULTIFIT` (Martí-Vidal et al. 2014) to model
the visibilities of the [C ii] line emission in the CRISTAL sample. The `UVMULTIFIT` implements simultaneous fitting of multiple components, which is useful for characterizing pair galaxies.
We assumed a two-dimensional (2-D) exponential disk model
( _n_ = 1) for all of the [C ii] components and first allow six parameters (R.A., Decl., total flux density, major-axis FWHM, minorto-major axis ratio, and position angle of major axis) free. Some
of the fittings fail to converge when the peak S/N of the [C ii] line
emission is not high enough (typically S/N < 8). In this case, we
fixed the projected minor-to-major axis ratio to unity.
The fit components were determined based on the classification described in Section 3.1. For single and multiple-UV
classes, we adopt one-component modeling, and otherwise, we
adopt two-component modeling. We show the images of the visibility data, the best-fit model, and the residual in Figure 3 for four
systems that we showed in Figure 1. We show the rest of the sam


**Fig. 4.** [C ii] luminosity-size relation of the CRISTAL sample. Symbols
are based on the classification defined in Section 3.1. Each component
of the pair/multiple-[C ii] systems are shown separately. The right panel
shows the histogram of [C ii] sizes among categories with matched colors. We omit a histogram of multiple-[C ii] because of the small sample size ( _N_ = 2). A histogram with a solid black line shows the size
distribution of the entire CRISTAL sample. The [C ii] sizes show the
diversity at fixed [C ii] luminosity, in which relatively compact sizes
( _R_ _e_,[CII] ≲ 1 kpc) were challenging to be measured in the previous lowresolution data.


ple in Figure A.1 and A.2. As can be seen in Figure 3, the best-fit
model characterizes the observed [C ii] line emission well and
no signal greater than 2σ significance level is present in the central 2 [′′] -region, securing the validity of the fitting. Our analysis
yielded structural parameters of a total number of 34 [C ii] line
components, including J1000+0234 (Capak et al. 2008), a mas

Article number, page 5 of 23



single

pair



multi. UV

multi. [CII]



4


2


1


0.5


0.25



8 9 10
###### log 10 L [CII] [L ]



0 10

###### N

_A&A proofs:_ manuscript no. draft



sive submillimeter galaxy ( _S_ 870µm = 8.03 mJy; Solimano et al.
2024) located in the proximity to CRISTAL-01a.

Finally, we convert the fitting outputs of the total flux density
and major-axis FWHM into the total [C ii] luminosity ( _L_ [CII] ) and
the effective radius ( _R_ _e_,[CII] ), respectively. For a 2-D exponential
disk model, the major axis FWHM and major axis effective radius can be related as _R_ _e_,major = 1.21 × FWHM, therefore we
obtained a circularized effective radius by calculating _R_ _e_,[CII] =
1.21 × FWHM [√] _q_, where _q_ is the minor-to-major axis ratio. We
estimate the uncertainty by using error propagation. For the uncertainty of each parameter (FWHM and _q_ ), we adopt the output from the `UVMULTIFIT`, which is estimated from the post-fit
covariance matrix (Martí-Vidal et al. 2014). We summarize our
fitting results in Table 1. We calculate an average value and standard deviation of the [C ii] sizes of ⟨ _R_ _e_,[CII] ⟩ = 1.90 ± 0.77 kpc.
To fairly compare with the fitting results from the low-resolution
archival data alone, we iterate the above procedure by only using the data taken in the ALPINE Survey. We present the results
and discussion in Appendix B. In brief, we find a good agreement between two measurements for the [C ii] fluxes and sizes
( _R_ _e_,[CII] ≳ 1 kpc). On the other hand, we find that the axis ratios tend to be poorly constrained when only the ALPINE data
is used.

In Figure 4, we show a [C ii] luminosity-size relation of the
CRISTAL sample. To see the dependence of multiplicity, symbols are distinguished based on the classification presented in
Section 3.1. Although we expect to find larger [C ii] sizes in pair
and multiple-UV systems compared to single systems, we were
unable to statistically distinguish their size distributions by performing the Kolmogorov-Smirnov test (with _p_ values of 0.23 and
0.12 for the pair and multiple-UV, respectively), largely due to
our limited sample size. Overall, Figure 4 showcases the diversity of [C ii] sizes at fixed [C ii] luminosity, and we find that lowresolution data used in previous studies were unable to measure
relatively compact sizes ( _R_ _e_,[CII] ≲ 1 kpc).


3.2.2. Rest-frame UV and FIR continuum emission


To evaluate the spatial extent of [C ii] line emission, we refer
to two continuum size measurements (observing wavelengths of
1.6 µm and 870 µm), which were both performed in Mitsuhashi
et al. (2024). The rest-frame UV sizes ( _R_ _e_,UV ) are measured with
`GALFIT` (Peng et al. 2002) using the HST/WFC3 F160W images. A single Sérsic model with an index of _n_ = 1 is assumed
(except for CRISTAL-13), and nearby objects seen in the HST
images are masked by using `SExtractor` (Bertin & Arnouts
1996). The rest-frame FIR sizes ( _R_ _e_,FIR ) are measured from the
ALMA Band-7 continuum visibilities with the same method using `UVMULTIFIT` described in Section 3.2.1.


Mitsuhashi et al. (2024) classify the CRISTAL galaxies into
either single or multiple systems based on the multiplicity in the
HST/WFC3 F160W images. The multiple systems correspond
to either pair, multiple-UV, or multiple-[C ii] classified in Section 3.1 of this study. Unlike [C ii] line emission, all of the FIR
continuum emission was fit in a single exponential disk component due to the lower S/N detection compared to the [C ii] line
emission. While this hampers the fair comparison between FIR
and [C ii] line sizes for multiple-UV, or multiple-[C ii] systems,
we find that the FIR continuum is detected in either one of the
pair systems (e.g., CRISTAL-04a, CRISTAL-07a), and hence we
adopt the FIR sizes of these galaxies in this study.


Article number, page 6 of 23



**4.** **Results and discussion**


_4.1._ _Size comparison_


We start by comparing the measured effective radii among different tracers (rest-frame UV and FIR continua) to characterize
the spatial extent of the [C ii] line emission in the context of star
formation activity. In Table 2, we list the sizes and size ratios
discussed below.

The left panel of Figure 5 shows a comparison between the

[C ii] line and rest-frame UV continuum radii. From Figure 5
(left), we find that the [C ii] line emission is systematically more
extended than the rest-frame UV emission, which is well consistent with the previous findings (Carniani et al. 2018; Fujimoto
et al. 2020; Fudamoto et al. 2022). The size ratio ( _R_ _e_,[CII] / _R_ _e_,UV )
ranges from 0.94 (CRISTAL-16) to 5.03 (CRISTAL-20) with
the average value and standard deviation of ⟨ _R_ _e_,[CII] / _R_ _e_,UV ⟩ =
2.90 ± 1.40. We note that the median (average) positional offset
between the [C ii] line and rest-frame UV continuum emission
is 0.11 (0.14) arcsec (∼ 0.5 kpc in a physical scale), which is
smaller than the typical synthesized beam size of the CRISTAL
data. We interpret this as them having consistent peak positions.
We exclude multiple-UV and multiple-[C ii] systems in this
diagram, because each [C ii] line or UV component may arise
from multiple galaxies for these classes, making the interpretation difficult. Among the multiple-UV systems, the central UV
component in CRISTAL-01a and CRISTAL-01b was successfully modeled by GALFIT, whereas the remaining multiple-UV
systems failed to converge due to contamination from nearby UV
sources. We determine [C ii]-to-UV size ratios of 3.0 and 3.8 for
CRISTAL-01a and CRISTAL-01b, respectively, which are both
slightly larger than the average value. Bowler et al. (2017) report larger UV sizes in bright UV galaxies with clumpy structures ( _M_ UV ≲ −21.5 mag), suggesting a similar effect may influence the [C ii] line emission in these multiple-UV systems (Figure A.1).
In the right panel of Figure 5, we show the size comparison between the [C ii] line and FIR continuum emission. The
latter was measured in visibility modeling with a circular exponential disk model (Mitsuhashi et al. 2024; Section 3.2.2). The
best-fit central positions of the [C ii] line and FIR continuum

                                      emission are in good agreement, with the median (average) off
set of 0.09 (0.12) arcsec, again smaller than the beam size of the
CRISTAL data. Similarly to the comparison with the UV continuum emission, we find that the [C ii] line emission is comparable to, or more extended than the FIR continuum emission.
One galaxy that is well below the one-to-one line is CRISTAL21, which has an unreliable FIR size measurement due to the
insufficient S/N of the visibility data, particularly at short _uv_
distances. Therefore, hereafter, we do not include the results of
CRISTAL-21 when the FIR radius is related to the discussions.
We calculate the average size ratio and standard deviation of
⟨ _R_ _e_,[CII] / _R_ _e_,FIR ⟩ = 1.54 ± 0.63. Within the uncertainty, this size
ratio suggests that the [C ii] line radius is consistent with the FIR
continuum radius. In fact, we find that two-thirds of the sample
(eight out of 12) shown in Figure 5 have comparable FIR continuum radius with [C ii] line radius ( _R_ _e_,[CII] / _R_ _e_,FIR < 1.5).
Three recent studies have independently reported similar
results. Romano et al. (2024) performed a stacking analysis
of [C ii] line, FIR continuum (160 µm), and near-UV (NUV;
2300 Å) continuum emission in local dwarf galaxies considered
as analogs of high-redshift galaxies. They discovered that the

[C ii] line and FIR emission is more extended than the NUV
emission. The single Sérsic fittings of [C ii] line and FIR con

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6


**Table 1.** Structural parameters of [C ii] line emission in the CRISTAL galaxies.


ID R.A. Decl. _I_ [CII] ∆ _v_ [(] _[a]_ [)] _R_ _e_,[CII] _q_ [CII] PA [CII] log 10 ( _L_ [CII] / _L_ ⊙ )


(Jy km/s) (km/s) (kpc) (deg)

CRISTAL-01a 10:00:54.508 2:34:34.46 0.68 ± 0.16 789 3.05 ± 1.19 0.59 ± 0.27 21 ± 24 8.62 [+] − [0] 0 [.] . [09] 12
CRISTAL-01b 10:00:54.778 2:34:28.27 0.67 ± 0.13 376 2.40 ± 0.92 0.44 ± 0.22 67 ± 15 8.62 [+] − [0] 0 [.] . [08] 09
CRISTAL-02 10:00:21.499 2:35:11.01 2.63 ± 0.16 533 2.58 ± 0.28 0.52 ± 0.07 153 ± 5 9.31 [+] − [0] 0 [.] . [03] 03
CRISTAL-03 9:59:53.254 2:07:05.40 0.44 ± 0.05 490 1.33 ± 0.47 0.81 ± 0.34 90 ± 54 8.59 [+] − [0] 0 [.] . [04] 05
CRISTAL-04a 9:58:57.907 2:04:51.36 0.94 ± 0.07 308 1.76 ± 0.36 0.90 ± 0.21 50 ± 66 8.76 [+] − [0] 0 [.] . [03] 04
CRISTAL-04b 9:58:57.928 2:04:52.85 0.32 ± 0.07 129 3.37 ± 1.27 0.74 ± 0.31 57 ± 42 8.30 [+] − [0] 0 [.] . [09] 12
CRISTAL-05 10:00:09.422 2:20:13.84 0.94 ± 0.08 523 1.57 ± 0.28 0.31 ± 0.08 160 ± 5 8.90 [+] − [0] 0 [.] . [03] 04
CRISTAL-06a W 10:01:00.894 1:48:33.66 0.89 ± 0.07 298 1.49 ± 0.22 0.50 ± 0.08 94 ± 6 8.74 [+] − [0] 0 [.] . [03] 03
CRISTAL-06a E 10:01:00.940 1:48:33.81 0.44 ± 0.06 298 1.23 ± 0.22 – – 8.44 [+] − [0] 0 [.] . [06] 07
CRISTAL-06b 10:01:00.999 1:48:34.85 0.52 ± 0.07 332 2.63 ± 0.66 0.71 ± 0.20 123 ± 23 8.51 [+] − [0] 0 [.] . [06] 06
CRISTAL-07a 10:00:04.058 2:37:35.84 0.49 ± 0.09 325 1.84 ± 0.64 0.89 ± 0.39 0 ± 13 8.57 [+] − [0] 0 [.] . [07] 09
CRISTAL-07b 10:00:03.974 2:37:36.36 0.50 ± 0.08 351 1.95 ± 0.71 0.73 ± 0.31 67 ± 40 8.58 [+] − [0] 0 [.] . [07] 08
CRISTAL-07c 10:00:03.223 2:37:37.75 1.56 ± 0.15 413 2.51 ± 0.45 0.74 ± 0.15 70 ± 19 9.07 [+] − [0] 0 [.] . [04] 04
CRISTAL-08 3:32:19.044 -27:52:38.21 1.35 ± 0.12 320 3.47 ± 0.47 0.74 ± 0.12 8 ± 15 8.91 [+] − [0] 0 [.] . [04] 04
CRISTAL-09 9:59:00.893 2:05:27.57 0.56 ± 0.07 518 0.87 ± 0.41 0.78 ± 0.46 13 ± 66 8.67 [+] − [0] 0 [.] . [05] 06
CRISTAL-10 10:02:04.134 1:55:44.30 0.51 ± 0.07 386 2.49 ± 0.71 0.73 ± 0.23 122 ± 29 8.65 [+] − [0] 0 [.] . [06] 07
CRISTAL-11 10:00:32.598 2:15:28.44 1.05 ± 0.11 529 1.44 ± 0.43 0.65 ± 0.23 105 ± 23 8.80 [+] − [0] 0 [.] . [04] 05
CRISTAL-12 3:32:11.943 -27:41:57.44 0.10 ± 0.03 224 1.19 ± 0.89 0.53 ± 0.54 18 ± 44 7.93 [+] − [0] 0 [.] . [10] 14
CRISTAL-13 10:00:41.171 2:17:14.24 0.95 ± 0.09 382 1.61 ± 0.39 0.47 ± 0.15 63 ± 11 8.78 [+] − [0] 0 [.] . [04] 04
CRISTAL-14 9:59:47.068 2:22:32.92 0.35 ± 0.07 534 0.75 ± 0.24 – – 8.31 [+] − [0] 0 [.] . [08] 10
CRISTAL-15 10:00:47.657 2:18:02.09 0.44 ± 0.08 540 1.43 ± 0.87 0.47 ± 0.27 116 ± 20 8.44 [+] − [0] 0 [.] . [07] 09
CRISTAL-16 3:32:15.899 -27:41:24.36 0.33 ± 0.06 445 1.39 ± 0.83 0.17 ± 0.13 68 ± 7 8.44 [+] − [0] 0 [.] . [07] 08
CRISTAL-17 10:00:39.132 2:25:32.66 0.10 ± 0.04 312 2.13 ± 1.33 – – 7.95 [+] − [0] 0 [.] . [15] 24
CRISTAL-19 10:00:05.105 2:03:12.10 0.64 ± 0.05 497 1.48 ± 0.48 0.86 ± 0.24 158 ± 50 8.69 [+] − [0] 0 [.] . [03] 04
CRISTAL-20 9:58:28.503 2:03:06.56 0.94 ± 0.04 330 1.80 ± 0.21 0.57 ± 0.07 25 ± 6 8.89 [+] − [0] 0 [.] . [02] 02
CRISTAL-21 9:59:30.466 2:08:02.62 0.77 ± 0.12 422 1.62 ± 0.61 0.46 ± 0.17 76 ± 12 8.77 [+] − [0] 0 [.] . [06] 07
CRISTAL-22a 10:00:59.291 1:33:19.43 4.91 ± 0.87 1032 0.91 ± 0.58 0.40 ± 0.22 107 ± 14 9.63 [+] − [0] 0 [.] . [07] 08
CRISTAL-22b 10:00:59.250 1:33:19.42 1.66 ± 0.25 924 0.93 ± 0.25 0.49 ± 0.15 80 ± 11 9.16 [+] − [0] 0 [.] . [06] 07
CRISTAL-23a 10:01:54.863 2:32:31.52 4.66 ± 0.27 462 2.87 ± 0.31 0.76 ± 0.08 113 ± 11 9.46 [+] − [0] 0 [.] . [02] 03
CRISTAL-23b 10:01:54.970 2:32:31.51 2.77 ± 0.27 442 2.45 ± 0.43 0.82 ± 0.15 123 ± 28 9.24 [+] − [0] 0 [.] . [04] 04
CRISTAL-23c 10:01:54.682 2:32:31.42 0.66 ± 0.11 465 0.52 ± 0.18 – – 8.62 [+] − [0] 0 [.] . [07] 08
CRISTAL-24 10:00:02.715 2:37:39.99 14.76 ± 2.50 1291 3.00 ± 1.03 0.74 ± 0.25 92 ± 31 9.96 [+] − [0] 0 [.] . [07] 08
CRISTAL-25 10:01:12.502 2:18:52.55 3.35 ± 0.19 477 2.45 ± 0.35 0.65 ± 0.10 35 ± 10 9.32 [+] − [0] 0 [.] . [02] 03


**Notes.** ( _a_ ) Velocity range containing 95 % (= [2.5 %, 97.5 %]) of the total [C ii] line flux. To convert to the 80 % (= [10 %, 90 %]) velocity range,
it is necessary to apply a multiplication factor of 0.654.



tinuum show an excellent agreement in effective radius with a
Gaussian-like profile (Sérsic index _n_ ∼ 0.5). Pozzi et al. (2024)
reported the same comparison for four galaxies drawn from the
ALPINE Survey resulting in a median (average) size ratio of
_R_ _e_,[CII] / _R_ _e_,FIR = 1.29 ± 0.14 (1.24 ± 0.19), which is slightly
smaller than our measurements. Two out of four galaxies are
CRISTAL-24 and CRISTAL-25, and we confirm that the measurements are consistent with ours within uncertainties. Given



that both the average size ratio and its standard deviation derived
from the CRISTAL sample are larger than the values reported by
Pozzi et al. (2024), we are probing more diverse populations in
terms of spatial relation between [C ii] line and FIR continuum
emission, likely due to the improved spatial resolution and sensitivity of the CRISTAL data. Finally, Díaz-Santos et al. (2021)
reported an average size ratio of ⟨ _R_ _e_,[CII] / _R_ _e_,FIR ⟩ = 1.61 ± 0.10
for four dust-obscured quasars at _z_ ≃ 3.0 − 4.6, which are a few


Article number, page 7 of 23

_A&A proofs:_ manuscript no. draft


**Table 2.** Effective radii and size ratios in continuum emission.


ID _R_ _e_,UV _R_ _e_,FIR _R_ _e_,[CII] / _R_ _e_,UV _R_ _e_,[CII] / _R_ _e_,FIR Class.


(kpc) (kpc)


CRISTAL-01a 1.02 ± 0.06 – 3.0 ± 1.2 – multi-UV


CRISTAL-01b 0.63 ± 0.05 2.18 ± 1.01 3.8 ± 1.5 1.1 ± 0.7 multi-UV


CRISTAL-02 – 1.99 ± 0.46 – 1.3 ± 0.3 multi-UV


CRISTAL-03 1.02 ± 0.05 – 1.3 ± 0.5 – single


CRISTAL-04a 1.01 ± 0.05 0.86 ± 0.47 1.7 ± 0.4 2.1 ± 1.2 pair


CRISTAL-04b 0.96 ± 0.14 – 3.5 ± 1.4 – pair


CRISTAL-05 0.36 ± 0.04 1.45 ± 0.63 4.3 ± 0.9 1.1 ± 0.5 single


CRISTAL-06a W – 2.03 ± 0.47 – 0.7 ± 0.2 multi-[C ii]


CRISTAL-06a E – – – – multi-[C ii]


CRISTAL-06b 1.25 ± 0.07 – 2.1 ± 0.5 – pair


CRISTAL-07a 0.90 ± 0.06 1.24 ± 0.95 2.0 ± 0.7 1.5 ± 1.2 pair


CRISTAL-07b 1.51 ± 0.13 – 1.3 ± 0.5 – pair


CRISTAL-07c 0.88 ± 0.11 0.86 ± 0.48 2.8 ± 0.6 2.9 ± 1.7 single


CRISTAL-08 2.53 ± 0.09 – 1.4 ± 0.2 – single


CRISTAL-09 0.17 ± 0.05 0.62 ± 0.47 5.2 ± 3.0 1.4 ± 1.3 single


CRISTAL-10 – 2.38 ± 1.33 – 1.0 ± 0.7 multi-UV


CRISTAL-11 0.44 ± 0.16 0.77 ± 0.60 3.3 ± 1.5 1.9 ± 1.6 single


CRISTAL-12 – – – – single


CRISTAL-13 – 0.60 ± 0.46 – 2.7 ± 2.1 multi-UV


CRISTAL-14 – – – – single


CRISTAL-15 – – – – single


CRISTAL-16 1.49 ± 0.14 – 0.9 ± 0.6 – single


CRISTAL-17 – – – – single


CRISTAL-19 0.60 ± 0.11 1.61 ± 0.94 2.5 ± 0.9 0.9 ± 0.6 single


CRISTAL-20 0.36 ± 0.06 1.50 ± 0.32 5.0 ± 1.0 1.2 ± 0.3 single


CRISTAL-21 0.38 ± 0.06 7.11 ± 3.06 4.3 ± 1.7 0.2 ± 0.1 single


CRISTAL-22a 0.76 ± 0.07 0.88 ± 0.06 1.2 ± 0.8 1.0 ± 0.7 pair


CRISTAL-22b – – – – pair


CRISTAL-23a 0.60 ± 0.04 3.19 ± 0.61 4.8 ± 0.6 0.9 ± 0.2 pair


CRISTAL-23b – – – – pair


CRISTAL-23c – – – – single


CRISTAL-24 0.69 ± 0.26 1.34 ± 0.18 4.4 ± 2.2 2.2 ± 0.8 single


CRISTAL-25 0.86 ± 0.03 2.10 ± 0.76 2.9 ± 0.4 1.2 ± 0.5 single



orders of magnitude brighter in the IR luminosity compared to
our sample (see also Venemans et al. 2020). All these studies
imply that the range of [C ii]-to-FIR size ratios at high redshift
is relatively narrow (1 ≲ _R_ _e_,[CII] / _R_ _e_,FIR ≲ 2), compared to that of

[C ii]-to-UV size ratios which can be affected by dust obscuration.


One possible origin of extended [C ii] line emission is ongoing merging activity. When diffuse carbon-rich gas is morphologically disturbed, or taken away from the stellar component,
the [C ii] line emission can become more extended compared to
the rest-frame UV continuum. Such a phenomenon has been ex

Article number, page 8 of 23



emplified in the case of vuds_cosmos_5101209780 (Ginolfi et al.
2020a) and CRISTAL-05 (Posses et al. 2024) as well as a larger
sample of merging galaxies in the ALPINE sample (Di Cesare
et al. 2024). Ginolfi et al. (2020a) and Di Cesare et al. (2024)
report that ∼ 25–50 % of the total [C ii] line emission is coming from a diffuse gas envelope. The fraction of [C ii] line emission originating from the envelope is defined by subtracting the

[C ii] line flux of the “‘galaxy”’ component from the total [C ii]
line flux, characterized by spectra extracted from regions above
1σ or 2σ significance level in the moment-0 maps. These studies highlight the impact of early metal-enrichment at large radii,

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6



















**Fig. 5.** Comparisons of the effective radii of the [C ii] line and the continuum emission. (Left) Effective radius of [C ii] line emission compared to
the rest-frame UV continuum emission (HST/WFC3 F160W). Symbols are the same as in Figure 4. The dashed black line indicates the one-to-one
relation between _R_ _e_,[CII] and _R_ _e_,UV, and three dashed gray lines above this line represent _R_ _e_,[CII] / _R_ _e_,UV = 2, 4, 8. (Right) Same as the left panel, but

[C ii] line radius is compared to the rest-frame FIR emission, measured from the ALMA Band-7 continuum images (Mitsuhashi et al. 2024). On
average, the [C ii] sizes are larger than the rest-frame UV sizes by a factor of 2.90; compared to the rest-frame FIR sizes, they tend to be larger by
a factor of 1.54 although with large uncertainties.



though the definition depends on the sensitivity of the observations. In particular, extended line flux with low S/N may not
be CLEANed if the stopping threshold of `tclean` is higher than
this flux, potentially leading to an overestimation of the extended
and diffuse flux. For galaxies classified as single, we derive
⟨ _R_ _e_,[CII] / _R_ _e_,UV ⟩ = 3.21 ± 1.42 and ⟨ _R_ _e_,[CII] / _R_ _e_,FIR ⟩ = 1.62 ± 0.69,
while for pair systems we find ⟨ _R_ _e_,[CII] / _R_ _e_,UV ⟩ = 2.38 ± 1.22 and
⟨ _R_ _e_,[CII] / _R_ _e_,FIR ⟩ = 1.36 ± 0.45. Given the large uncertainties of
these size ratios, we refrain from claiming an ongoing physical
effect from galaxy interactions. Thus, we tentatively conclude
that we do not find differences in size ratios between isolated
galaxies classified as single and mergers classified as pair sys
tems.


Since there is a tight correlation between [C ii] luminosity
and SFR, [C ii] line emission has been used as an indicator of star
formation activity. However, the size differences between [C ii]
line and continuum (rest-frame UV and FIR) emission suggests
that the [C ii] line emission is not completely spatially coupled
to star formation activity, which might be at odds with studies of
nearby galaxies (Pineda et al. 2014; Kapala et al. 2015; HerreraCamus et al. 2015). Given the average size ratios of 2.9 and 1.5,
we infer that the [C ii] line emission is approximately two times
more extended than the star formation activity traced by continuum emission. We shall further discuss this point in Section 4.3.


_4.2._ _Constituent of [C_ ii _] line emission_


In this section, we assess whether [C ii] line emission in the SFGs
has a halo structure as a secondary component. If such a halo
structure is confirmed, the physical origin would be different
from the central [C ii] component associated with star-forming
ISM (e.g., star-formation-driven outflow, cold stream). Therefore, the identification of [C ii] halo gives us an important insight
into the origin of the extended [C ii] line emission.



Because [C ii] halo is expected to have low-surface density
at large radii, most of the previous studies needed to rely on the
stacking analysis to confirm such structure (Fujimoto et al. 2019;
Ginolfi et al. 2020b; Novak et al. 2020). To date, the only case
in an individual [C ii] halo has been confirmed as an extended
secondary component structure is A1689-zD1, a strongly lensed
galaxy at _z_ = 7.13 (Akins et al. 2022). As observations of the
CRISTAL Survey are deeper than the previous observations, we
can now assess whether such structure can be confirmed individually. To eliminate the possibility that [C ii] line emission from
satellite galaxies contaminates the halo component, we focus on
16 single galaxies, which we classified in Section 3.1. We do not
include CRISTAL-23c since the galaxy might be in a phase of
triple-merger (Jones et al. 2020).


Figure 6 visualizes the data, best-fit model, and residual as
a form of visibility data for 16 single objects that we created in
Section 3.2. The average velocity range of 16 single galaxies is
485.0 km/s. The data is extracted by the `getdata` function of a
casatool `ms` . In Figure 6, average values and standard deviations
of the real part of visibility data per 100 kλ bin are shown. The
residual data is created by subtracting the best-fit model from
the data. For all galaxies, the data and the best-fit model show a
good agreement, and we do not find an excess at the residual data
in the shortest _uv_ distance bin (∼ 50 kλ). This indicates that the
visibility profile can be well fit by an exponential disk model and
an extended secondary component is not necessary to explain the
data.


To further confirm this, we stack the visibility data of 16 single galaxies and again perform the visibility modeling in the
same manner. We perform both single component and double
component fittings. The result of the single component fitting is
shown in the left panel of Figure 7. As well as the visibility data
of the individual galaxies, the stacked visibility data is fit well
by a single exponential disk profile. The model is characterized
by an effective radius of _R_ _e_,[CII] = 1.97 ± 0.10 kpc, assuming an


Article number, page 9 of 23

_A&A proofs:_ manuscript no. draft



1.0


0.5


0.0


1


0

|Col1|CRISTAL-03|
|---|---|
|||
|250<br>500|250<br>500|
|CRISTAL-09|CRISTAL-09|



0 250 500


0.5


0.0


0.5

0 250 500


2


0


0 250 500



0 250 500


1


0



2


1


0



5.0


2.5


0.0


0 250 500


0.5


0.0


0 250 500


1


0


0 250 500


5


0


0 250 500



0


0.5


0.0



0 250 500



2


0


0.50


0.25


0.00


0.4


0.2


0.0


10


0

|0 250 500|Col2|
|---|---|
|CRISTAL-12|CRISTAL-12|
|0<br>250<br>500|0<br>250<br>500|
|CRISTAL-17~~*~~|CRISTAL-17~~*~~|
|0<br>250<br>500||
|CRISTAL-24|CRISTAL-24|



0 250 500



best-fit model

data

residual


###### uv distance [k ]

**Fig. 6.** Flux density in the form of the real part of the visibility, as a function of _uv_ distances along the minor axis. Each data point represents the
mean value per 100 kλ bin. The galaxies that were fit in a circular exponential disk model are marked in an asterisk. The uncertainties represent
the standard deviation. Both the data (circle) and the residual (diamond) visibilities are shown. The residuals are created by subtracting the best-fit
model (solid black line) from the data.



average redshift of _z_ = 5.22, which is consistent with the average
radius (⟨ _R_ _e_,[CII] ⟩ = 1.90 kpc) of the entire CRISTAL galaxies. At
the smallest 20 kλ bin of the residual visibility, we find a flux
excess of 0.15 mJy (1.2σ significance level). The result of the
double component fitting is shown in the right panel of Figure 7.
Here, we assume two concentric exponential disk components.
The brighter component (1.68 ± 0.23 mJy; hereafter “galaxy”
component) has a radius of _R_ _e_,gal = 1.91 ± 0.20 kpc, which is
similar to the best-fit single component. The other component
(0.16 ± 0.27 mJy; hereafter “halo” component) has an extended
radius of _R_ _e_,halo = 9.17 ± 28.2 kpc. Since the fittings converge
to the same reduced χ [2] value, we cannot statistically favor either the single or double component model. However, the existence of an extended, diffuse component remains uncertain due
to its faintness and large uncertainties. The flux of the “halo”
component constitutes 8.7 ± 13.4 % of the total flux, and this is
smaller than what has been suggested in previous [C ii] line observations (e.g., ∼ 30 % for A1689-zD1 reported in Akins et al.
2022, but see Jones et al. 2023 for faint gaseous halo detected
in CO _J_ = 3 − 2 line emission). The flux becomes negative
within the range of the uncertainty, and the standard deviation of
± 0.13 mJy at the smallest 20 kλ bin gives the detection of 1.2σ
level, which both point out that the detection is not significant.
As we have identified various axis ratios ( _q_ = 0.31 − 0.90) in our
sample (Table 1), it is possible that the extended [C ii] line emission along the major axis is diluted by the stacking and create
the “halo” component artificially.


Article number, page 10 of 23



Alternatively, we now focus on the stacked residual of the
visibility data where the main disk component obtained from
a single exponential disk fitting is subtracted. Figure 8 shows
the stacked residual visibility as a function of _uv_ -distances. In
order to avoid the stacked visibility data being skewed by the
bright objects in which the amplitude of residual visibility is
also bright, we normalize the residual visibility by the total [C ii]
flux obtained from the best-fit model before the stacking. We
show the average values per both 20 kλ and 100 kλ bins, but
no clear excess can be found in either case. By adopting standard deviations of visibility data within each bin as uncertainties, the small deviations from the horizontal axis at shorter- _uv_
distances (≲ 200 kλ) are below the 1σ level. If the fitting results
are dragged by data from the shorter _uv_ distances, we would find
an excess at larger _uv_ -distances as a remnant of the fitting, but
no such feature can be found.


To summarize, from the double component fitting in the
stacked visibility data (Figure 7 right), we do not find a statistically significant evidence of [C ii] halo as a secondary component. The modeled secondary component consists of 8.7±13.4 %
of the total flux, which is smaller by several times than what has
been suggested in the previous [C ii] line observations at high
redshift. Based on Figure 6, 7, and 8, we conclude that the [C ii]
line emission of the CRISTAL galaxies can be adequately explained by a single exponential disk component.

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6


## double component fit
### = /|uv| [arcsec] 5 2 1 0.5


### 2.0 1.0 0.0


## single component fit
### = /|uv| [arcsec] 5 2 1 0.5








### 0 250 500 uv distance [k ]


### 0 250 500 uv distance [k ]



**Fig. 7.** Real part of the stacked visibility (circles) and the residual visibility (diamonds) as a function of _uv_ distances for single component (left)
and double component (“galaxy” + “halo”; right) fittings. Average values of two types of binning (20 kλ and 100 kλ) are shown. Uncertainties
represent a standard deviation of binned visibility data. The best-fit models are shown as a solid black line (total) and solid purple lines (each
component). The flux and effective radius of the best-fit models are summarized at the upper right corners. At the smallest 20 kλ bin, the residual
show an excess at 1.2σ and 0.7σ significance levels, which corresponds to 8.8 % and 5.5 % of the total flux density for single and double component
fittings, respectively.


#### 1.00 0.75 0.50 0.25 0.00 0.25


#### = /|uv| [arcsec] 5 2 1 0.5



**Fig.** **8.** Real part of the stacked residual visibility as a function of _uv_
distances. Average values of two types of binning (20 kλ and 100 kλ) are
shown. Uncertainties represent a standard deviation of binned visibility
data.


_4.3._ _What determines the spatial extent of the [C_ ii _] line?_


In this section, we discuss the origin of extended [C ii] line emission. The correlation between [C ii] luminosity and SFR, which



holds true for several orders of magnitude, suggests that the [C ii]
line emission can be considered a good tracer of PDRs on molecular cloud surface ( _n_ ≃ 10 [3] –10 [5] cm [−][3], _T_ ≃ 10 [2] K) surrounding young massive stars. However, [C ii] line emission can arise
from more diffuse gaseous components ( _n_ ≲ 10 [3] cm [−][3] ) than
PDRs. Following the description of the ISM conditions in Madden et al. (1997), these are cold neutral medium ( _n_ ≃ 10 [2] cm [−][3],
_T_ ≃ 10 [2] K), warm neutral medium ( _n_ ≃ 1 cm [−][3], _T_ ≃ 5 × 10 [3] K),
and ionized medium ( _n_ ≲ 1 cm [−][3], _T_ ≃ 10 [4] K; Section 4.3.2). In
neutral ISM conditions, atomic hydrogen would be the dominant
collision partner, while in PDRs either atomic or molecular hydrogen can be effective in the [C ii] excitation (Goldsmith et al.
2012).


As FIR continuum emission traces a dust re-emission, the
spatial extent of FIR continuum emission can be regarded as regions where PDRs are dominant. Hence, the comparable spatial extent between the [C ii] line and FIR continuum emission
( _R_ _e_,[CII] / _R_ _e_,FIR ≈ 1) indicates that the [C ii] line emission coincides with star formation activity traced by the PDRs. Umehata et al. (2021) report the [C ii] line and FIR continuum observations of galaxies in the SSA22 protocluster at _z_ = 3.1
and discuss that [C ii] line emission is mainly associated with
star formation activity, although other origins and potential effects from the overdense environment are not ruled out. Novak
et al. (2020) also draw a similar conclusion for _z_ - 6 quasars.
However, as those samples are limited to IR-bright galaxies
with _L_ IR ≳ 10 [12] _L_ ⊙, the results may not apply to typical SFGs
( _L_ IR ≲ 10 [12] _L_ ⊙ ) at corresponding redshifts. Previous studies have
reported few galaxies showing _R_ _e_,[CII] / _R_ _e_,FIR ≈ 1 (Fujimoto et al.
2020; Pozzi et al. 2024), and thanks to the sensitivity of ALMA
observations taken by the CRISTAL Survey, we can now postu

Article number, page 11 of 23

_A&A proofs:_ manuscript no. draft



late whether such galaxies comprise of the majority of the SFGs
at _z_ ∼ 4 − 6, which is consistent with the general picture that the

[C ii] line emission is coming from the PDRs.


From the size comparisons that we presented in Section 4.1,
we find that the sizes of the [C ii] line emission in our sample are
on average 2.90 and 1.54 times larger compared to the rest-frame
UV and FIR continuum emission, respectively (Figure 5), suggesting that [C ii] line emission is approximately twice more extended than the main star-forming regions. This indicates that the
contribution from the PDRs is not sufficient to explain the [C ii]
line emission beyond the radius of star-forming regions. For simplicity, if we assume that the [C ii] radius is exactly twice more
larger than the radius that encloses half of the SFR, and the contribution from PDRs is dominant (100 %) within the [C ii] radius
( _r_ < _R_ _e_,[CII] ), the average contribution from PDRs at _r_ - _R_ _e_,[CII]
is roughly estimated to be ≈ 20 %. When spatially integrated, the
PDR fraction is then ≈ 60 %. Low contribution from PDRs at the
outskirts of the galaxies is qualitatively consistent with Li et al.
(2024), who find that the spatially resolved Σ [CII] − Σ SFR has a
steeper slope in about half of the CRISTAL galaxies that are examined than the ones found in nearby star-forming galaxies (e.g.,
De Looze et al. 2014; Herrera-Camus et al. 2015). While this
could be caused by the [C ii] deficit in the central regions, since
we do not find such evidence as we show later (see Figure 10
in Section 4.3.3; see also Herrera-Camus et al. 2021 and Posses
et al. 2024 for individual cases), we suggest that the Σ [CII] − Σ SFR
does not hold at large radii as the central region tends to deviate
toward brighter [C ii] surface densities.


In the Milky Way, Pineda et al. (2013) report that about 20 %
of the [C ii] line emission arises from the cold neutral medium.
In M 33, Kramer et al. (2013) discover an increasing contributions from a cold neutral medium to the [C ii] line emission
with radius. For Haro 11, a nearby dwarf galaxy that has similar [C ii] and IR luminosities to the CRISTAL galaxies, Cormier
et al. (2012) report a contribution from PDRs to the [C ii] line
emission of 10 %, while the rest of the [C ii] line emission is
coming from diffuse low-ionization gas. de Blok et al. (2016)
compare the spectra of [C ii], CO _J_ = 1–0, and H i lines of a sample of 10 nearby galaxies. They find that the radial profile of
the [C ii] line emission is taking an intermediate slope between
CO _J_ = 1–0 and H i lines (see also Tarantino et al. 2021). These
studies motivate us to think that by measuring the spatial extent
of [C ii] line emission at a kiloparsec-scale resolution, we are
looking at the intermediate spatial extent between molecular and
atomic gas distributions. Considering that the average H i gas
fraction ( _M_ HI /( _M_ HI + _M_ ⋆ )) monotonically increases with redshift, from 25 % at _z_ = 0 to 70 % at _z_ ∼ 4–6 (Walter et al. 2020;
Heintz et al. 2021), and that H i gas is thought to be extended
up to a circumgalactic scale along the filaments of the cosmic
web (e.g., Katz et al. 2017), the extended [C ii] line emission
in the CRISTAL galaxies is likely to be a combination of that
coming from PDRs and cold/warm neutral medium, where most
of the mass can be traced by molecular and atomic hydrogen,
respectively. In nearby galaxies, the dust mass surface density
correlates with the total gas mass surface density better than the
molecular or atomic surface densities at a kiloparsec scale (e.g.,
Casasola et al. 2022). Since the atomic gas distribution is generally more extended than that of the molecular gas, the strong
correlation between dust and total gas mass suggests that at large
radii, dust can be a good tracer of atomic gas rather than molecular gas. While we cannot assume the same correlation to the
CRISTAL galaxies due to the differences in gas fraction and
metallicity, this correlation in nearby galaxies supplements our


Article number, page 12 of 23



argument that the contribution from atomic gas to the [C ii] line
emission becomes increasingly dominant with radius.
Numerous theoretical works have been presented to constrain the properties of FIR fine-structure lines at high redshift
(e.g., Nagamine et al. 2006; Vallini et al. 2013, 2015; Katz et al.
2017; Pallottini et al. 2017; Olsen et al. 2018; Lagache et al.
2018; Popping et al. 2019; Arata et al. 2020; Ramos Padilla et al.
2023; Gurman et al. 2024; Casavecchia et al. 2024a,b; MuñozElgueta et al. 2024). Some of the studies that align with the discussion above include Ramos Padilla et al. (2023) who simulated
the dominant fraction (up to ≈70–90 %) of [C ii] line emission
coming from the atomic gas phase in high-redshift galaxies (see
also Casavecchia et al. 2024a). Similarly, Gurman et al. (2024)
report that the contribution from warm neutral medium (not necessarily molecular gas) is dominant (≈ 30 − 40 %) particularly
at sub-solar metallicity while H ii region may be comparably important, based on high-resolution hydrodynamical simulations of
a self-regulated ISM. In contrast, Vallini et al. (2015) discuss
that the [C ii] line emission from cold gas may be attenuated by
cosmic microwave background (CMB) by a factor of 0.1–0.2,
because the CMB temperature approaches the spin temperature
of the [C ii] line transition in the cold neutral medium (∼ 20 K).
This results in a minor contribution of cold neutral gas (≲ 10 %)
to the [C ii] line emission (see also Olsen et al. 2018; Lagache
et al. 2018). It should be noted that these simulated galaxies are
affected by slightly higher CMB temperatures since they are at
higher redshifts ( _z_ ≳ 6) than our sample.
The cause of variations in _R_ _e_,[CII] / _R_ _e_,FIR among individual
galaxies is still not clear. If extended [C ii] line emission originates from a diffuse neutral medium, then it is possible that
the [C ii] line emission can be taken away from the host galaxies during merger events, as has been demonstrated in simulated
galaxies (Pallottini et al. 2022). While we fail to statistically confirm that pair systems have more extended [C ii] sizes than others (Section 3.2), JWST images reveal that some single galaxies
identified by HST images are actually composed of multiple stellar components (Lines et al. 2024). This includes two galaxies,
CRISTAL-07c and CRISTAL-11, which have _R_ _e_,[CII] / _R_ _e_,FIR - 2.
Future assessments of how the _R_ _e_,[CII] / _R_ _e_,FIR (and _R_ _e_,[CII] / _R_ _e_,UV )
varies during past merger events using zoom-in cosmological
simulations will give an insight into our results. Alternatively,
the variations in _R_ _e_,[CII] / _R_ _e_,FIR in our sample may reflect the presence of extraplanar gas and dust, as is demonstrated by the observations of NGC 891, a nearby edge-on galaxy. Reach et al.
(2020) report that the [C ii] line emission in a thick disk of
NGC 891 has larger scale height (2.8 kpc) compared to mid-IR
emission tracing PAHs, as well as FIR emission (1.4 kpc; Bocchio et al. 2016). Nonetheless, the data with deeper sensitivity
and higher spatial resolution are required to verify this scenario
in our sample.
In the following, we discuss four alternative mechanisms that
could be the cause of extended [C ii] line emission in addition to
diffuse neutral gas: outflows (Section 4.3.1), ionized gas (Section 4.3.2), radial variation in the [C ii] deficit (Section 4.3.3),
and shock heating (Section 4.3.4).


4.3.1. Outflows


One of the supporting scenarios for the extended [C ii] line emission is ongoing outflows driven by star formation activity. Semianalytical models predict that cold-mode outflows could reproduce the extended [C ii] line emission (Pizzati et al. 2020, 2023),
and this has been observationally supported by the spectra stacking analysis of [C ii] line emission for both star-forming galaxies

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6



1.0


0.5


0.0


0.5



1 0 1 2
##### log 10 SFR IR [[][M] [/][yr][/kpc] [2] []]







1 0 1 2
##### log 10 SFR IR [[][M] [/][yr][/kpc] [2] []]





1.0


0.5


0.0


0.5



**Fig.** **9.** Dependence of the spatial extent of [C ii] line emission on the SFR IR surface density. (Left) [C ii] line radius as a function of the SFR IR
surface density. The solid blue and purple lines show a best-fit linear regression for single and single+pair sources, respectively. The shaded region
shows a 95 % confidence level of the fit for single galaxies. The _p_ values of a Spearman’s rank correlation test for both single and single+pair
parent samples are shown in the lower-left corner. We also highlight CRISTAL-02 (multiple-UV), a galaxy which shows an evidence of broad

[C ii] wing component in multiple spatially resolved elements of the galaxy (Davies et al. in prep). (Right) Same as the left panel, but taking the

[C ii]-to-UV size ratio as the vertical axis. Given the _p_ values, we cannot rule out the null hypothesis that there is no correlation between these
parameters.



at 4 < _z_ < 6 (Gallerani et al. 2018; Ginolfi et al. 2020b) and
local low-metallicity dwarf galaxies (Romano et al. 2023). On
the other hand, Akins et al. (2022) do not find an outflow signature in [C ii] line from a strongly lensed galaxy A1689-zD1 at
_z_ = 7.13, but detect a broad component in [O iii] 88µm line emission, indicating the presence of ionized outflowing gas that will
subsequently cool and emit the [C ii] line emission at larger radius (see also Wong et al. 2022). For _z_ - 6 quasars, Novak et al.
(2020) report null detection of broad spectral feature from [C ii]
line based on spectral stacking (see also Decarli et al. 2018).

As such, it is still not clear whether there is a physical association between outflows and the extended [C ii] line emission seen
in projected sky distribution at _z_ - 4. The situation has become
more puzzling, since recent ALMA observations (Spilker et al.
2020; Salak et al. 2024; Nianias et al. 2024) report the detection of a blueshifted OH 119µm absorption feature as evidence
of molecular outflows, while a broad [C ii] line feature is not detected for the same sources. These results indicate that the [C ii]
line emission is not always a robust tracer of molecular outflows.
Levy et al. (2023) present a [C ii] line observation of the outflow
region of a nearby starburst galaxy M 82. The authors find that
the fraction of [C ii] line flux associated with the outflow region
is about one-quarter of the total [C ii] line emission, and the majority (> 55 %) of the [C ii] line flux in the outflow region arises
from the atomic component. If the composition of the [C ii] line
in high-redshift galaxies is similar to M 82, it is not surprising to
have a weak or no detection of the broad [C ii] line feature.

It has also been suggested that AGN outflows can enhance

[C ii] line emission due to an additional contribution from either X-ray-dominated or ionized regions (Smirnova-Pinchukova
et al. 2019, but also see Stacey et al. 2010). Since the original
sample selection in the ALPINE Survey excluded Type I AGN
with broad optical spectral line (Le Fèvre et al. 2020), our sample similarly does not include bright Type I AGN. However, Li
et al. (2024) discuss that CRISTAL-25 may be an AGN, be


cause the spatially resolved SED fitting analysis shows poor
fit at the central region, possibly due to the contamination of
broad emission lines from AGN to the broad band photometry.
Nonetheless, we confirm that [C ii] line emission in CRISTAL25 is not particularly bright compared to the FIR continuum
( _L_ [CII] / _L_ FIR = 3.7 × 10 [−][3] ), and so the possible effect of AGN
on the enhancement of [C ii] line emission is not likely playing a
role in this galaxy.
In this study, we are likely measuring the sizes of [C ii] line
emission arising from both galactic ISM and outflows, if they
exist. The median velocity width we use to measure the spatial extent of the [C ii] line emission is 440 km/s, which is broad
enough that star-formation-driven outflows can contribute to the
observed structure of the [C ii] line emission. Sugahara et al.
(2019) report a positive correlation between SFR and outflow
velocity up to _z_ ∼ 6. A similar correlation between SFR (or its
surface density Σ SFR ) and mass outflow rate is also reported for
nearby galaxies (e.g., Fluetsch et al. 2019; see also Veilleux et al.
2020; Förster Schreiber & Wuyts 2020 and references therein).
Among the CRISTAL galaxies, CRISTAL-02 only shows a
strong broad wing component in the [C ii] line spectrum (Davies
et al. in prep) and weak evidence of broad wing component is detected when the [C ii] spectra are stacked among the CRISTAL
galaxies (Birkin et al. in prep). Based on these findings, if outflows contribute to the extended [C ii] line emission, we might
see a correlation between [C ii] sizes and galactic properties.
Figure 9 shows the [C ii] size and [C ii]-to-UV size ratio as a
offunction of the SFRthe CRISTAL galaxies. IR surface density (We use theΣ SFR values IR = SFRof SFR IR /2 IR π _R_ mea- [2] _e_,FIR [)]
sured in Mitsuhashi et al. (2024) who convert FIR continuum
flux ( _S_ 158 µm ) into IR luminosity ( _L_ IR ) and then into obscured
SFR (SFR IR ) following the same method as Béthermin et al.
(2020). According to a linear regression fitting, we find a positive
trend for single galaxies in both panels in Figure 9, but a negative
trend when pair galaxies are included. Nonetheless, the Spear

Article number, page 13 of 23

_A&A proofs:_ manuscript no. draft



man’s rank correlation tests give the _p_ values of 0.546 (single fit)
and 0.831 (single+pair fit) for log 10 Σ SFR IR − log 10 _R_ _e_,[CII] relation
(Figure 9 left), and 0.381 (single fit) and 0.859 (single+pair fit)
for log 10 Σ SFR IR − log 10 ( _R_ _e_,[CII] / _R_ _e_,UV ) relation (Figure 9 right).
We similarly investigated the [C ii] size and [C ii]-to-UV size ratio as a function of SFR, but none of the correlations were significant ( _p_ value > 0.05). Therefore, regardless of the merging
events, we fail to rule out the null hypothesis that there is no association between star-formation-driven (atomic) outflows and the
extended [C ii] line emission. In addition, we find that CRISTAL02 does not have particularly large [C ii] size nor SFR IR surface
density among the CRISTAL galaxies. These results may imply
that there is no strong association between (atomic) outflows and
the extended [C ii] line emission.


4.3.2. Contribution from ionized gas


Due to the low-ionization potential of carbon, [C ii] line could
originate from ionized regions. Because nitrogen has a higher
ionization potential than hydrogen, the [N ii] 205µm line, which
has a similar critical density as the [C ii] line when collisionally excited by electrons, has been widely used to discern the
contribution of the [C ii] line from ionized gas. Alternatively,

[O iii] 88µm can also be used as a tracer of ionized gas (e.g.,
Herrera-Camus et al. 2018a; Harikane et al. 2020), but unfortunately the [O iii] 88µm line from the redshifts of our sample is
hardly accessible through the atmospheric windows.


Studies of nearby galaxies with measurements of both [C ii]
and [N ii] 205µm lines suggest that ionized gas, either diffuse
ionized gas or H ii regions, is not the main contributor of [C ii]
line emission (e.g., Croxall et al. 2017; Herrera-Camus et al.
2018a; Sutter et al. 2019; Tarantino et al. 2021). Nearby luminous infrared galaxies (LIRGs) are reported to have a PDR
fraction of [C ii] line larger than 60 %, up to 95 % (Díaz-Santos
et al. 2017). For high-redshift galaxies, Pavesi et al. (2016) study

[N ii] 205µm line for two Lyman-break galaxies, CRISTAL-02
(LBG-1) and CRISTAL-22 (HZ10), and report higher [C ii]-to
[N ii] luminosity ratio for CRISTAL-02, which is less dusty than
CRISTAL-22 (see also Umehata et al. 2017; Cunningham et al.
2020). The estimated contributions from ionized gas are ∼ 5 %
and 10–25 % for CRISTAL-02 and CRISTAL-22, respectively.


Croxall et al. (2017) find a trend of decreasing [C ii]-to-[N ii]
luminosity ratio with decreasing gas-phase metallicity in the local SFGs; that is, a low contribution to the [C ii] line emission
from the ionized gas at high metallicity (see also Cormier et al.
2019). Assuming that the mass-metallicity relations (Nakajima
et al. 2023) hold true in the CRISTAL galaxies, the empirical
relation presented in Croxall et al. (2017) provides an ionized
fraction of 13 –27 % in a stellar mass range of log( _M_ ⋆ / _M_ ⊙ ) =

[9.5, 11.0]. This agrees with the estimated ionized fraction of
CRISTAL-22 with log( _M_ ⋆ / _M_ ⊙ ) = 10.35±0.37 (Mitsuhashi et al.
2024). Since the majority of the CRISTAL galaxies have lower
stellar masses than this, we infer that the [C ii] line flux contributed from the ionized medium is not as significant as ∼ 25 %,
indicating that the contribution from ionized gas has little impact
on the spatial extent of [C ii] line emission.


However, some theoretical studies show mixed results regarding the impact of diffuse ionized gas on [C ii] line emission
(e.g., Olsen et al. 2018; Ramos Padilla et al. 2023). Future highresolution [N ii] 205µm observations will be crucial to elucidate
the spatial distribution of [C ii] line emission associated with ionized gas at high redshift.


Article number, page 14 of 23



4.3.3. [C ii ] deficit in the central region of galaxies


It is known that the [C ii]-to-(F)IR luminosity ratio varies depending on the ISM conditions; for instance the ratio is particularly low in regions where (F)IR surface density is high. Several
physical explanations have been made, such as low photoelectric heating efficiency due to small grain destruction or charging,
high ionization parameter, and thermal saturation of the [C ii]
line emission (e.g., Malhotra et al. 2001; Muñoz & Oh 2016;
Díaz-Santos et al. 2017; Herrera-Camus et al. 2018b). Because
this so-called [C ii] deficit is prominent in the central region of
galaxies (e.g., Smith et al. 2017; Litke et al. 2019; Venemans
et al. 2020), it is possible that the larger sizes measured in [C ii]
line emission compared to FIR continuum emission accompany
the radial dependence on the [C ii] deficit.


To inspect this, we stacked ten single galaxies, in which both

[C ii] line and FIR continuum emission is detected. The stacking
was performed in visibility using the `CASA/concat` task. The
phase centers of individual visibility data are shifted to match
the coordinates at which the [C ii] line emission peaks. We image both stacked [C ii] line and FIR continuum emission using
the `CASA/tclean` task with natural weighting, and clean down
to 1.5σ noise level by applying 3 [′′] aperture mask, where σ is
the rms noise level of the dirty image. We show the normalized
surface density profiles of the stacked clean image in the left
panel of Figure 10. Both [C ii] line and FIR continuum emission
exhibit an extended structure beyond the PSF Gaussian profile
with an effective radius of 1.97 ± 0.17 kpc and 1.53 ± 0.22 kpc,
respectively. Beyond a beam-convolved radius of 1 [′′], the surface densities of [C ii] line and FIR continuum emission become
comparable to the surface densities derived from setting random
apertures, and the emission is likely not genuine. The IR surface density profile shows a small bump at 1 [′′] . By inspecting
the stacked image, we confirm that this bump results from the
elongated structure at the 2-3σ significance level of the FIR continuum emission. We therefore do not attribute the bump at 1 [′′] to
mergers or halo structure.


In the right panel of Figure 10, we show the absolute surface density profiles (left axis) and their ratio (right axis).
The Σ [CII] /Σ IR profile fluctuates around the global value of
8 × 10 [−][4], with a gradual increase until 0 [′′] . 5 (3 kpc) and subsequent decrease at least up to ∼ 0 [′′] . 8 (5 kpc). The global value
of Σ [CII] /Σ IR = 8 × 10 [−][4] is in fact smaller than the expected
value of Σ [CII] /Σ IR = (1 − 4) × 10 [−][3] (e.g., Herrera-Camus et al.
2018a; Zanella et al. 2018) for the CRISTAL galaxies with
Σ IR ∼ 10 [10] − 10 [11] _L_ ⊙ /kpc [2] (Mitsuhashi et al. 2024). We attribute
this lower ratio in the stacked image to the IR-bright galaxies
in our sample (CRISTAL-21 and CRISTAL-24), which are an
order of magnitude brighter in IR luminosity than the rest of
the CRISTAL galaxies. However, our interest here is the radial
variation in Σ [CII] /Σ IR, and so we have confirmed that the overall trend is unchanged when such exceptionally IR-bright galaxies are excluded from the stacking. Because the radial variations
in Σ [CII] /Σ IR are not monotonically decreasing toward the center
and instead are relatively flat, the [C ii] deficit is not particularly
strong in the central region. This may be at odds with nearby
galaxies (Smith et al. 2017), but consistent with some of the
quasar-host galaxies at _z_ ≳ 6 (Venemans et al. 2020) and the individual CRISTAL galaxies (Herrera-Camus et al. 2021; Posses
et al. 2023; Li et al. 2024). In summary, we suggest that radial
variation in the [C ii] deficit is not the primary cause of the extended [C ii] line emission.

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6


###### radius [kpc]

0 2 4 6 8


###### radius [kpc]

0 2 4 6 8



2



0
10


1
10


2
10



10 [11]



















**Fig. 10.** Radial profiles of the stacked [C ii] line and FIR continuum emission. (Left) Normalized radial surface density profile of the _uv_ -stacked
image in [C ii] line ( _R_ _e_,[CII] = 1.97 ± 0.17 kpc) and FIR continuum ( _R_ _e_,FIR = 1.53 ± 0.22 kpc) emission. The dotted lines show average surface
density derived by setting random apertures on blank regions, which are also shown in color-shaded regions as uncertainties. The dashed black
curve represents the clean PSF. The top axis is converted to a physical scale assuming an average redshift of _z_ = 5.22 among the stacked sample.
(Right) Absolute radial surface density profiles of the [C ii] line and FIR continuum emission, in which the unit is converted to _L_ ⊙ /kpc [2] . The solid
black line shows the ratio between the [C ii] line and IR emission (axis shown on the right hand side). As we do not see a strong radial variation in
the [C ii]-to-IR luminosity ratio, we suggest that the [C ii] deficit is not responsible for the extended [C ii] line emission.



4.3.4. Shocked gas


The alternative mechanism that can enhance the [C ii] line emission without star formation activity is shock heating produced in
a merging system or in a galaxy group (Appleton et al. 2013; Peterson et al. 2018; Fadda et al. 2023): kinetic energy from shocks
and turbulence is injected into the gas and excite the ionized carbon by collisions. We refer the readers to Posses et al. (2024) for
detailed discussion on the argument that the [C ii] line emission
in CRISTAL-05 is likely to be enhanced by shock heating. In
short, the enhanced [C ii] line emission due to shock heating is
suggested from evidence of merging activity and a high [C ii]to-IR luminosity ratio ( _L_ [CII] / _L_ IR ≳ 10 [−][2] ). The latter can also
be tested by comparing the [C ii] surface density to SFR surface
density.

Among the CRISTAL galaxies except for CRISTAL-05
(Posses et al. 2024), the pair and multiple-UV systems are the
likely candidates that may emit [C ii] line emission induced
by shock heating. However, as we show in Table 2 and discuss at the beginning of Section 4.3, most of these systems
have a moderate size ratio between the [C ii] line and FIR continuum ( _R_ _e_,[CII] / _R_ _e_,FIR ∼ 0.7 − 1.5), so their [C ii] line emission can mostly be explained by PDRs. Two exceptions are
CRISTAL-04a ( _R_ _e_,[CII] / _R_ _e_,FIR = 2.1 ± 1.2) and CRISTAL-13
( _R_ _e_,[CII] / _R_ _e_,FIR = 2.7±2.1), but neither of them shows high [C ii]to-IR luminosity ratio ( _L_ [CII] / _L_ IR ≃ 3 × 10 [−][3] ). Shocked gas heating is not likely the driver of extended [C ii] line emission.


_4.4._ _Connection to Ly_ α _and H_ α _emission_


Harikane et al. (2018) find an anti-correlation between [C ii] luminosity and Lyman-α line (Lyα line, λ = 1216 Å) equivalent
width (EW) for Lyα emitters at _z_ = 4 − 7. This anti-correlation is
likely to exist for each galaxy population, such as Lyman-α emit


**Table 3.** Summary of the best-fit parameters in Figure 11.


_y_ _m_ _b_


log 10 Σ [CII] −0.633 8.27


log 10 (Σ [CII] /Σ IR ) 0.274 −2.93


_R_ _e_,[CII] / _R_ _e_,UV −1.02 4.39


**Notes.** Slope ( _m_ ) and intercept ( _b_ ) of the linear regression fittings
performed in Figure 11. Parameters are determined from the form of
_y_ = _m_ log 10 EW Lyα + _b_ .


ters and star-forming main sequence galaxies, since typical [C ii]
luminosity at fixed Lyα EW differs across galaxy populations
(Díaz-Santos et al. 2021). However, Endsley et al. (2022) do not
find such anti-correlation for UV-bright galaxies at _z_ ≃ 7, possibly due to either a limited dynamic range of Lyα EW (< 20Å) or
insufficient statistics.

To study how the [C ii] line properties of our sample correlate with Lyα emission, we plot the [C ii] line surface density
(Σ [CII] = _L_ [CII] /2π _R_ [2] _e_,[CII] [),] [the] [[C][ ii][]-to-IR] [surface] [density] [ratio]
(Σ [CII] /Σ IR ) within the [C ii] effective radius, and the [C ii]-to-UV
size ratio ( _R_ _e_,[CII] / _R_ _e_,UV ) as a function of the Lyα EW (EW Lyα ) in
Figure 11. We estimate the IR luminosity within the [C ii] radius
based on the best-fit model in the visibility modeling. The values
of EW Lyα are presented in the catalogs of both Faisst et al. (2020)
and Cassata et al. (2020). Since Cassata et al. (2020) report the
EW Lyα value only for the galaxies with [C ii] line detection in the
ALPINE Survey, we adopt the values from Faisst et al. (2020) to
increase the sample size. Here, we convert the EW Lyα reported
in the observed-frame to the rest-frame by applying a correction
factor of (1+ _z_ ) [−][1] . In agreement with previous findings, we find a
decreasing trend of the [C ii] line surface density with increasing


Article number, page 15 of 23

2.2









_A&A proofs:_ manuscript no. draft


10.0


7.5


5.0


2.5





2.4


2.6


2.8


3.0







0.0



0.5 1.0 1.5 2.0
##### log 10 EW Ly [Å]



0.5 1.0 1.5 2.0
##### log 10 EW Ly [Å]



**Fig. 11.** [C ii] surface density (top left), [C ii]-to-IR surface density ratio (bottom left), and [C ii]-to-UV size ratio (bottom right) of the CRISTAL
galaxies as a function of the rest-frame EW of Lyα emission. The Lyα properties are taken from Faisst et al. (2020). The galaxies without dust
continuum detection are denoted by open symbols. Small purple circles shown in the top left and bottom right panels are the ALPINE galaxies
in which [C ii] surface density, [C ii]-to-UV size ratio (Fujimoto et al. 2020), and Lyα EW (Faisst et al. 2020) are available. We show the linear
regression fitting (Table 3) in the solid black line, with the shaded region representing the 95 % confidence interval. The _p_ value of a Spearman’s
rank correlation test is shown in the lower-left corner of each panel.



EW Lyα, with a Spearman’s rank correlation coefficient of −0.51
and a _p_ value of 0.039. Moreover, we find the [C ii]-to-IR surface
density ratio positively correlates with EW Lyα with a correlation
coefficient of 0.56 and a _p_ value of 0.090. The size ratio of [C ii]
line and UV radii appears to decrease with EW Lyα, which aligns
with the results from Fujimoto et al. (2020), although a Spearman’s rank correlation test give a _p_ value of 0.516. We perform
a linear regression fitting for each correlation and present the fitting results in Table 3. As a side note, we do not find a correlation
between [C ii] line radius and EW Lyα .


The correlations we present in Figure 11 imply that there
is physical interplay between [C ii] line, dust, and Lyα emission. Noticeably, we find that three galaxies (CRISTAL-01a,
12, and 17) with the lowest [C ii] surface density with Σ [CII] <
10 [7] _L_ ⊙ /kpc [2] have large Lyα EW (EW Lyα ≳ 10 [1][.][5] Å) and are not
detected in FIR continuum emission (Mitsuhashi et al. 2024). On
the other hand, galaxies with small Lyα EW (EW Lyα ≲ 10 [1][.][5] Å)
exhibit a high [C ii] surface density (Σ [CII] - 10 [7] _L_ ⊙ /kpc [2] ) and
a low [C ii]-to-IR surface density ratio (Σ [CII] /Σ IR ≲ 10 [−][2][.][5] ); in
other words, a [C ii] deficit. These ratios indicate that the low
dust content in the ISM of these galaxies facilitates the escape of
Lyα photons and vice versa. In such ISM conditions, the ionization parameter is expected to be higher compared to the galaxies
with strong FIR continuum detection. Simultaneously, the limited amount of dust likely leads to low [C ii] surface density by
reducing the efficiency of photoelectric heating.


Article number, page 16 of 23



It is known that the velocity offsets between the systemic velocity (measured from [C ii] line or optical emission lines) and
the velocity of the peak of Lyα line anti-correlate with EW Lyα
(Hashimoto et al. 2013, 2019; Erb et al. 2014; Valentino et al.
2022), which has also been confirmed for the ALPINE sample
(Cassata et al. 2020). As large velocity offsets indicate high H i
column density, the galaxies with small EW Lyα have higher H i
column densities than the ones with large EW Lyα, which may explain extended [C ii] line emission if it arises from the atomic gas
(Section 4.3). Therefore, although it is not conclusive whether
the weak anti-correlation between _R_ _e_,[CII] / _R_ _e_,UV and Lyα EW is
real, the large Lyα EW, low H i column density, small amount
of dust, and small _R_ _e_,[CII] / _R_ _e_,UV are consistent with each other,
and larger fraction of the [C ii] line emission may arise from the
ionized gas in such galaxies (Section 4.3.2).

However, we note that the Lyα properties currently available
are taken by slit spectroscopy (Cassata et al. 2020), and only
global properties without spatial information can be inferred. We
thus expect that future Lyα observations by integral field spectroscopy (IFS) would be crucial to compare the spatial extent and
morphology between [C ii] line and Lyα emission.

Another fundamental tracer emitted from hydrogen atoms is
the Balmer-α line (Hα line, λ = 6563Å). Hα line traces an instantaneous star formation activity (∼ 10 − 100 Myr), so if the
Hα line is more extended than continuum emission tracing starformation activity over ∼ 100 Myr, this would support the idea
that these galaxies are in a phase of “inside-out” growth and neu

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6



tral gas at larger radii is heated by recent star formation activity. Herrera-Camus et al. (2015) show that [C ii] line emission
can arise and hold the [C ii]-SFR relation with a short duration
(2 Myr) of star formation activity with high heating efficiency
from FUV to [C ii] line emission (ϵ h ≃ 1 − 3 %), suggesting
the possibility that recent star formation activity causing the extended [C ii] line emission may be traced by Hα line emission.
As JWST has recently enabled us to study the spatial distribution of the Hα line at comparable redshifts to our sample (e.g.,
Birkin et al. 2023; Übler et al. 2024; Matharu et al. 2024; Nelson
et al. 2024), it is of great interest to compare the morphological
and kinematical properties of Hα and [C ii] lines (Kohandel et al.
2024). Two of the galaxies among our sample (CRISTAL-20 and
CRISTAL-22) have been observed in JWST/NIRSpec IFU mode
(Parlanti et al. 2024; Jones et al. 2024), offering new insights
into the ionized gas properties of typical star-forming galaxies at
high redshift. In CRISTAL-20, Parlanti et al. (2024) reveal ionized outflows traced by the [O iii]5007Å and Hα lines, which are
co-spatial to the neutral outflows traced by [C ii] line. Jones et al.
(2024) discover brighter Hα line emission in CRISTAL-22b than
CRISTAL-22a, whereas dust continuum is weaker, suggesting
different evolutionary phases among the complex merging system. A future systematic census of ionized gas properties in the
CRISTAL galaxies with JWST will provide unprecedented insights into the spatial correlation between neutral and ionized

gas.


**5.** **Conclusions**


We have presented the [C ii] size measurements and size comparisons with other tracers for typical SFGs at _z_ = 4 − 6 taken
by the CRISTAL Survey. The data of the survey benefits from
the deep sensitivity (1σ ∼ 0.1 − 0.2 mJy per 20 km/s channel
bin) to search faint extended emission and high spatial resolution (θ beam ∼ 0 [′′] . 3), which enables us to identify and characterize
multiple galaxies in proximity. Our main findings are as follows:


1. _[C_ ii _]_ _sizes_ _are_ _similar_ _among_ _various_ _merger_ _states._ We
performed size measurements of [C ii] line emission via
visibility modeling analysis. The structural parameters of
33 components are reported in Table 1, including pairs
(e.g., CRISTAL-07ab) and complex UV systems (e.g.,
CRISTAL-02, CRISTAL-10). In spite of a variety of merger
states, we do not statistically confirm the difference in [C ii]
sizes between single and pair ( _p_ value = 0.23)/multiple-UV
( _p_ value = 0.12) systems.


2. _Extended_ _[C_ ii _]_ _line_ _emission_ _revealed_ _by_ _size_ _comparison._
Based on the comparisons between [C ii] line radius and
rest-frame UV, and FIR radii, we find average size ratios
and standard deviations of ⟨ _R_ _e_,[CII] / _R_ _e_,UV ⟩ = 2.90 ± 1.40
and ⟨ _R_ _e_,[CII] / _R_ _e_,FIR ⟩ = 1.54 ± 0.63, respectively. This
indicates that [C ii] line emission is approximately twice
more extended than the main star-forming regions traced by
rest-frame UV and FIR continuum emission.


3. _[C_ ii _]_ _line_ _emission_ _as_ _a_ _single_ _extended_ _disk_ _component._
We assessed whether the [C ii] line emission can be characterized by a disk with a secondary halo structure by
performing both single and double component fittings in
visibility. While we have obtained the two-component model
( _R_ _e_,gal = 1.91 ± 0.20 kpc, _R_ _e_,halo = 9.17 ± 28.2 kpc), the flux
density of “[C ii] halo” is weaker than the typical uncertainty
of the visibility data in short _uv_ distances (∼ 20 kλ), and



the single extended disk component ( _R_ _e_ = 1.97 ± 0.10 kpc)
characterizes the observed [C ii] line emission with an
equal level of statistical support. In the stacked residual
visibility, we did not detect any significant flux excess, thus
we conclude that the [C ii] line emission in our sample can
be adequately characterized by a single disk component.


4. _Origin of [C_ ii _] line emission._ While the [C ii] line emission
in about half of our sample can be explained by PDRs
associated with the star formation activity, the extent of

[C ii] line emission in the rest of the sample appears to
require an additional source of excitation. The most likely is

[C ii] line emission coming from the diffuse medium, either
neutral atomic gas or ionized gas, although the effect of such
components at high redshift is unsettled from a theoretical
perspective. We argue that the diversity in [C ii] sizes may be
further caused by different merger history and the existence
of extraplanar gas and dust. In contrast, the [C ii] deficit in
the central region of the galaxies, and shocked gas heating
induced by mergers are not likely to be responsible for the
extended [C ii] line emission.


5. _Correlations_ _with_ _the_ _Ly_ α _properties._ We find a negative
correlation between [C ii] surface density (Σ [CII] ) and Lyα
EW ( _p_ value = 0.039), and a tentative positive correlation
between [C ii]-to-IR surface density ratio (Σ [CII] /Σ IR ) and
Lyα EW ( _p_ value = 0.090). These correlations between [C ii]
and Lyα properties can be understood by the amount of gas
and dust content, which is essential for producing the [C ii]
line emission via photoelectric heating. High [C ii] surface
density suggests high neutral gas column density, leading to
strong attenuation of Lyα emission (low Lyα EW). We also
find a possible negative correlation between [C ii]-to-UV
size ratio ( _R_ _e_,[CII] / _R_ _e_,UV ) and Lyα EW. If the correlation is
real, this would support the scenario that extended [C ii]
line emission at large radii is arising from the atomic gas
component. Future IFS studies of both Lyα and Hα lines are
expected to explain the variations in the [C ii] line and dust
properties among the typical SFGs at this epoch.


_Acknowledgements._
We thank the anonymous referee for valuable comments that improved the content of this paper. R.I. would like to thank Seiji Fujimoto, Mahsa Kohandel, Rebecca C. Levy, Zongnan Li, Yuichi Matsuda, Marcel Neeleman, and Andrea Pallottini for illuminating discussions and suggestions. R.I. is supported by Grantsin-Aid for Japan Society for the Promotion of Science (JSPS) Fellows (KAKENHI Grant Number 23KJ1006). K.-i.T. is supported by JSPS KAKENHI grant
No. 23K03466. M.A. acknowledges support from the ANID BASAL project
FB210003. I.D.L. has received funding from the European Research Council
(ERC) under the European Union’s Horizon 2020 research and innovation programme DustOrigin (ERC-2019-StG-851622) and from the Flemish Fund for
Scientific Research (FWO-Vlaanderen) through the research projects G023821N
and G0A1523N. R.H.-C. thanks the Max Planck Society for support under
the Partner Group project "The Baryon Cycle in Galaxies" between the Max
Planck for Extraterrestrial Physics and the Universidad de Concepción. R.HC. also gratefully acknowledge financial support from ANID BASAL projects
FB210003. R.A.A.B. acknowledges support from an STFC Ernest Rutherford
Fellowship [grant number ST/T003596/1]. E.d.C acknowledges support from
the Australian Research Council (projects DP240100589 and CE170100013).
R.L.D. is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship DE240100136 funded
by the Australian Government. T.D.S. was supported by the Hellenic Foundation for Research and Innovation (HFRI) under the “2nd Call for HFRI Research Projects to support Faculty Members & Researchers” (Project Number: 3382). A.F. acknowledges support from the ERC Advanced Grant INTERSTELLAR H2020/740120. M.K. was supported by the ANID BASAL
project FB210003. M.S. was financially supported by Becas-ANID scholarship
#21221511, and also acknowledges ANID BASAL project FB210003. K.T. was
supported by ALMA ANID grant number 31220026 and by the ANID BASAL


Article number, page 17 of 23

_A&A proofs:_ manuscript no. draft



project FB210003. H.Ü. gratefully acknowledges support by the Isaac Newton
Trust and by the Kavli Foundation through a Newton-Kavli Junior Fellowship.
V.V. acknowledges support from the ALMA-ANID Postdoctoral Fellowship under the award ASTRO21-0062. This paper makes use of the following ALMA
data: ADS/JAO.ALMA#2017.1.00428.L, #2018.1.01359.S, #2018.1.01605.S,
#2019.1.00226.S, #2019.1.01075.S, and #2021.1.00280.L. ALMA is a partnership of ESO (represent- ing its member states), NSF (USA), and NINS (Japan),
together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic
of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. We thank the ALMA staff and,
in particular, the EA-ARC staff for their support. Data analyses were carried out
in part on the Multiwavelength Data Analysis System operated by the Astronomy
Data Center (ADC) at the National Astronomical Observatory of Japan.


**References**


Akins, H. B., Fujimoto, S., Finlator, K., et al. 2022, ApJ, 934, 64
Appleton, P. N., Guillard, P., Boulanger, F., et al. 2013, ApJ, 777, 66
Arata, S., Yajima, H., Nagamine, K., Abe, M., & Khochfar, S. 2020, MNRAS,
498, 5541
Aravena, M., Heintz, K., Dessauges-Zavadsky, M., et al. 2024, A&A, 682, A24
Bertin, E. & Arnouts, S. 1996, A&AS, 117, 393
Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2
Bigiel, F., de Looze, I., Krabbe, A., et al. 2020, ApJ, 903, 30
Birkin, J. E., Hutchison, T. A., Welch, B., et al. 2023, ApJ, 958, 64
Bischetti, M., Choi, H., Fiore, F., et al. 2024, ApJ, 970, 9
Bocchio, M., Bianchi, S., Hunt, L. K., & Schneider, R. 2016, A&A, 586, A8
Bowler, R. A. A., Dunlop, J. S., McLure, R. J., & McLeod, D. J. 2017, MNRAS,
466, 3612
Capak, P., Carilli, C. L., Lee, N., et al. 2008, ApJ, 681, L53
Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455
Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105
Carniani, S., Maiolino, R., Amorin, R., et al. 2018, MNRAS, 478, 1170
CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501
Casasola, V., Bianchi, S., Magrini, L., et al. 2022, A&A, 668, A130
Casavecchia, B., Maio, U., Péroux, C., & Ciardi, B. 2024a, arXiv e-prints,
arXiv:2410.14284
Casavecchia, B., Maio, U., Péroux, C., & Ciardi, B. 2024b, A&A, 689, A106
Cassata, P., Morselli, L., Faisst, A., et al. 2020, A&A, 643, A6
Cormier, D., Abel, N. P., Hony, S., et al. 2019, A&A, 626, A23
Cormier, D., Lebouteiller, V., Madden, S. C., et al. 2012, A&A, 548, A20
Croxall, K. V., Smith, J. D., Pellegrini, E., et al. 2017, ApJ, 845, 96
Cunningham, D. J. M., Chapman, S. C., Aravena, M., et al. 2020, MNRAS, 494,
4090
de Blok, W. J. G., Walter, F., Smith, J. D. T., et al. 2016, AJ, 152, 51
De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62
Decarli, R., Walter, F., Venemans, B. P., et al. 2018, ApJ, 854, 97
Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5
Devereaux, T., Cassata, P., Ibar, E., et al. 2024, A&A, 686, A156
Di Cesare, C., Ginolfi, M., Graziani, L., et al. 2024, A&A, 690, A255
Díaz-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32
Díaz-Santos, T., Armus, L., Charmandaris, V., et al. 2013, ApJ, 774, 68
Díaz-Santos, T., Assef, R. J., Eisenhardt, P. R. M., et al. 2021, A&A, 654, A37
Endsley, R., Stark, D. P., Bouwens, R. J., et al. 2022, MNRAS, 517, 5642
Erb, D. K., Steidel, C. C., Trainor, R. F., et al. 2014, ApJ, 795, 33
Fadda, D., Sutter, J. S., Minchin, R., & Polles, F. 2023, ApJ, 957, 83
Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61
Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586
Förster Schreiber, N. M. & Wuyts, S. 2020, ARA&A, 58, 661
Fudamoto, Y., Smit, R., Bowler, R. A. A., et al. 2022, ApJ, 934, 144
Fujimoto, S., Ouchi, M., Ferrara, A., et al. 2019, ApJ, 887, 107
Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900, 1
Gallerani, S., Pallottini, A., Feruglio, C., et al. 2018, MNRAS, 473, 1909
Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020a, A&A, 643, A7
Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020b, A&A, 633, A90
Goldsmith, P. F., Langer, W. D., Pineda, J. L., & Velusamy, T. 2012, ApJS, 203,
13
Grogin, N. A., Kocevski, D. D., Faber, S. M., et al. 2011, ApJS, 197, 35
Gullberg, B., Swinbank, A. M., Smail, I., et al. 2018, ApJ, 859, 12
Gurman, A., Hu, C.-Y., Sternberg, A., & van Dishoeck, E. F. 2024, ApJ, 965,
179
Harikane, Y., Ouchi, M., Inoue, A. K., et al. 2020, ApJ, 896, 93
Harikane, Y., Ouchi, M., Shibuya, T., et al. 2018, ApJ, 859, 84
Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71
Hashimoto, T., Ouchi, M., Shimasaku, K., et al. 2013, ApJ, 765, 70
Heintz, K. E., Oesch, P. A., Aravena, M., et al. 2022, ApJ, 934, L27
Heintz, K. E., Watson, D., Oesch, P. A., Narayanan, D., & Madden, S. C. 2021,
ApJ, 922, 147


Article number, page 18 of 23



Herrera-Camus, R., Bolatto, A. D., Wolfire, M. G., et al. 2015, ApJ, 800, 1
Herrera-Camus, R., Förster Schreiber, N., Genzel, R., et al. 2021, A&A, 649,
A31
Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018a, ApJ, 861, 94
Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018b, ApJ, 861, 95
Hollenbach, D. J. & Tielens, A. G. G. M. 1999, Reviews of Modern Physics, 71,
173
Izumi, T., Matsuoka, Y., Fujimoto, S., et al. 2021a, ApJ, 914, 36
Izumi, T., Onoue, M., Matsuoka, Y., et al. 2021b, ApJ, 908, 235
Jones, G. C., Béthermin, M., Fudamoto, Y., et al. 2020, MNRAS, 491, L18
Jones, G. C., Bunker, A. J., Telikova, K., et al. 2024, arXiv e-prints,
arXiv:2405.12955
Jones, G. C., Maiolino, R., Circosta, C., et al. 2023, MNRAS, 518, 691
Kapala, M. J., Sandstrom, K., Groves, B., et al. 2015, ApJ, 798, 24
Katz, H., Kimm, T., Sijacki, D., & Haehnelt, M. G. 2017, MNRAS, 468, 4831
Kennicutt, Robert C., J. 1998, ApJ, 498, 541
Kohandel, M., Pallottini, A., Ferrara, A., et al. 2024, A&A, 685, A72
Kramer, C., Abreu-Vicente, J., García-Burillo, S., et al. 2013, A&A, 553, A114
Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130
Lambert, T. S., Posses, A., Aravena, M., et al. 2023, MNRAS, 518, 3183
Langer, W. D., Velusamy, T., Pineda, J. L., Willacy, K., & Goldsmith, P. F. 2014,
A&A, 561, A122
Lapham, R. C., Young, L. M., & Crocker, A. 2017, ApJ, 840, 51
Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1
Levy, R. C., Bolatto, A. D., Tarantino, E., et al. 2023, ApJ, 958, 109
Li, J., Da Cunha, E., González-López, J., et al. 2024, ApJ, 976, 70
Liang, L., Feldmann, R., Murray, N., et al. 2024, MNRAS, 528, 499
Lines, N. E. P., Bowler, R. A. A., Adams, N. J., et al. 2024, arXiv e-prints,
arXiv:2409.10963
Litke, K. C., Marrone, D. P., Spilker, J. S., et al. 2019, ApJ, 870, 80
Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141
Madden, S. C., Poglitsch, A., Geis, N., Stacey, G. J., & Townes, C. H. 1997, ApJ,
483, 200
Malhotra, S., Kaufman, M. J., Hollenbach, D., et al. 2001, ApJ, 561, 766
Martí-Vidal, I., Vlemmings, W. H. T., Muller, S., & Casey, S. 2014, A&A, 563,
A136
Matharu, J., Nelson, E. J., Brammer, G., et al. 2024, A&A, 690, A64
Mitsuhashi, I., Tadaki, K.-i., Ikeda, R., et al. 2024, A&A, 690, A197
Momcheva, I. G., van Dokkum, P. G., van der Wel, A., et al. 2017, PASP, 129,
015004
Muñoz, J. A. & Oh, S. P. 2016, MNRAS, 463, 2085
Muñoz-Elgueta, N., Arrigoni Battaia, F., Kauffmann, G., et al. 2024, A&A, 690,
A392
Nagamine, K., Wolfe, A. M., & Hernquist, L. 2006, ApJ, 647, 60
Nakajima, K., Ouchi, M., Isobe, Y., et al. 2023, ApJS, 269, 33
Nelson, E., Brammer, G., Giménez-Arteaga, C., et al. 2024, ApJ, 976, L27
Nianias, J., Lim, J., & Yeung, M. 2024, ApJ, 963, 19
Novak, M., Venemans, B. P., Walter, F., et al. 2020, ApJ, 904, 131
Olsen, K., Greve, T. R., Narayanan, D., et al. 2018, ApJ, 857, 148
Pallottini, A., Ferrara, A., Bovino, S., et al. 2017, MNRAS, 471, 4128
Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621
Parlanti, E., Carniani, S., Venturi, G., et al. 2024, arXiv e-prints,
arXiv:2407.19008
Pavesi, R., Riechers, D. A., Capak, P. L., et al. 2016, ApJ, 832, 151
Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266
Peterson, B. W., Appleton, P. N., Bitsakis, T., et al. 2018, ApJ, 855, 141
Pineda, J. L., Langer, W. D., & Goldsmith, P. F. 2014, A&A, 570, A121
Pineda, J. L., Langer, W. D., Velusamy, T., & Goldsmith, P. F. 2013, A&A, 554,
A103
Pizzati, E., Ferrara, A., Pallottini, A., et al. 2020, MNRAS, 495, 160
Pizzati, E., Ferrara, A., Pallottini, A., et al. 2023, MNRAS, 519, 4608
Popping, G., Narayanan, D., Somerville, R. S., Faisst, A. L., & Krumholz, M. R.
2019, MNRAS, 482, 4906
Posses, A., Aravena, M., González-López, J., et al. 2024, arXiv e-prints,
arXiv:2403.03379
Posses, A. C., Aravena, M., González-López, J., et al. 2023, A&A, 669, A46
Pozzi, F., Calura, F., D’Amato, Q., et al. 2024, A&A, 686, A187
Ramos Padilla, A. F., Wang, L., van der Tak, F. F. S., & Trager, S. C. 2023, A&A,
679, A131
Reach, W. T., Fadda, D., Rand, R. J., & Stacey, G. J. 2020, ApJ, 902, 28
Riechers, D. A., Carilli, C. L., Capak, P. L., et al. 2014, ApJ, 796, 84
Romano, M., Donevski, D., Junais, et al. 2024, A&A, 683, L9
Romano, M., Nanni, A., Donevski, D., et al. 2023, A&A, 677, A44
Salak, D., Hashimoto, T., Inoue, A. K., et al. 2024, ApJ, 962, 1
Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3
Smirnova-Pinchukova, I., Husemann, B., Busch, G., et al. 2019, A&A, 626, L3
Smith, J. D. T., Croxall, K., Draine, B., et al. 2017, ApJ, 834, 5
Solimano, M., González-López, J., Aravena, M., et al. 2024, A&A, 689, A145
Spilker, J. S., Phadke, K. A., Aravena, M., et al. 2020, ApJ, 905, 85
Stacey, G. J., Geis, N., Genzel, R., et al. 1991, ApJ, 373, 423

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6



Stacey, G. J., Hailey-Dunsheath, S., Ferkinhoff, C., et al. 2010, ApJ, 724, 957
Sugahara, Y., Ouchi, M., Harikane, Y., et al. 2019, ApJ, 886, 29
Sutter, J., Dale, D. A., Croxall, K. V., et al. 2019, ApJ, 886, 60
Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157
Tadaki, K.-i., Belli, S., Burkert, A., et al. 2020, ApJ, 901, 74
Tarantino, E., Bolatto, A. D., Herrera-Camus, R., et al. 2021, ApJ, 915, 92
Telikova, K., González-López, J., Aravena, M., et al. 2024, arXiv e-prints,
arXiv:2411.09033
Übler, H., D’Eugenio, F., Perna, M., et al. 2024, MNRAS, 533, 4287
Umehata, H., Matsuda, Y., Tamura, Y., et al. 2017, ApJ, 834, L16
Umehata, H., Smail, I., Steidel, C. C., et al. 2021, ApJ, 918, 69
Valentino, F., Brammer, G., Fujimoto, S., et al. 2022, ApJ, 929, L9
Vallini, L., Gallerani, S., Ferrara, A., & Baek, S. 2013, MNRAS, 433, 1567
Vallini, L., Gallerani, S., Ferrara, A., Pallottini, A., & Yue, B. 2015, ApJ, 813, 36
Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&A Rev., 28, 2
Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130
Villanueva, V., Herrera-Camus, R., González-López, J., et al. 2024, A&A, 691,
A133

Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261
Vizgan, D., Greve, T. R., Olsen, K. P., et al. 2022a, ApJ, 929, 92
Vizgan, D., Heintz, K. E., Greve, T. R., et al. 2022b, ApJ, 939, L1
Walter, F., Carilli, C., Neeleman, M., et al. 2020, ApJ, 902, 111
Wang, F., Yang, J., Fan, X., et al. 2024, ApJ, 968, 9
Wolfire, M. G., Vallini, L., & Chevance, M. 2022, ARA&A, 60, 247
Wong, Y. H. V., Wang, P., Hashimoto, T., et al. 2022, ApJ, 929, 161
Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976


1 Department of Astronomy, School of Science, SOKENDAI (The
Graduate University for Advanced Studies), 2-21-1 Osawa, Mitaka,
Tokyo 181-8588, Japan e-mail: `ryota195ikeda@gmail.com`
2 National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan
3 Faculty of Engineering, Hokkai-Gakuen University, Toyohira-ku,
Sapporo 062-8605, Japan
4 Department of Astronomy, The University of Tokyo, 7-3-1 Hongo,
Bunkyo, Tokyo 113-0033, Japan
5 Instituto de Estudios Astrofísicos, Facultad de Ingeniería y Ciencias, Universidad Diego Portales, Avenida Ejercito Libertador 441,
Santiago, Chile
6 Sterrenkundig Observatorium, Ghent University, Krijgslaan 281  S9, B-9000 Ghent, Belgium
7 Max-Planck-Institut für extraterrestrische Physik, Gießenbachstraße
1, 85748 Garching
8 Instituto de Astrofísica, Facultad de Física, Pontificia Universidad
Católica de Chile, Santiago 7820436, Chile
9 Las Campanas Observatory, Carnegie Institution of Washington,
Raúl Bitrán 1200, La Serena, Chile
10 Departamento de Astronomía, Universidad de Concepción, Barrio
Universitario, Concepción, Chile
11 Department of Physics and Astronomy and George P. and Cynthia
Woods Mitchell Institute for Fundamental Physics and Astronomy,
Texas A&M University, 4242 TAMU, College Station, TX 778434242, US
12 National Radio Astronomy Observatory, 520 Edgemont Road, Charlottesville, VA 22903, USA
13 Department of Astronomy, University of Virginia, 530 McCormick
Road, Charlottesville, VA 22903, USA
14 Jodrell Bank Centre for Astrophysics, Department of Physics and
Astronomy, School of Natural Sciences, The University of Manchester, Manchester, M13 9PL, UK
15 German Aerospace Center (DLR), Institute of Communications and
Navigation, Wessling, Germany
16 International Centre for Radio Astronomy Research (ICRAR), The
University of Western Australia, M468, 35 Stirling Highway, Crawley, WA 6009, Australia
17 ARC Center of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), Australia
18 Centre for Astrophysics and Supercomputing, Swinburne University
of Technology, Hawthorn, Victoria 3122, Australia
19 Institute of Astrophysics, Foundation for Research and TechnologyHellas (FORTH), Heraklion 70013, Greece



20 School of Sciences, European University Cyprus, Diogenes Street,
Engomi 1516, Nicosia, Cyprus
21 Scuola Normale Superiore, Piazza dei Cavalieri 7, 56126 Pisa, Italy
22 Astrophysics Research Institute, Liverpool John Moores University,
146 Brownlow Hill, Liverpool L3 5RF, UK
23 Kavli Institute for Cosmology, University of Cambridge, Madingley
Road, Cambridge, CB3 0HA, UK
24 Cavendish Laboratory, University of Cambridge, 19 JJ Thomson
Avenue, Cambridge, CB3 0HE, UK
25 Department of Astronomy, University of Maryland, College Park,
Maryland, 20742 USA
26 Joint Space-Science Institute, University of Maryland, College Park,
Maryland, 20742 USA


Article number, page 19 of 23

_A&A proofs:_ manuscript no. draft



**Appendix A:** **The sample name and postage stamps**
**of the fit images**


**Table A.1.** Other names and references of the CRISTAL galaxies.


ID Other names Ref.


CRISTAL-01a DC842313 1


CRISTAL-01b – –


CRISTAL-02 DC848185, HZ6, LBG-1 1, 2, 3


CRISTAL-03 DC536534, HZ1 1, 2


CRISTAL-04a vc5100822662, DC514583 1


CRISTAL-04b vc5100822662, DC514583 1


CRISTAL-05 DC683613, HZ3 1, 2


CRISTAL-06a vc5100541407 1


CRISTAL-06b vc5100541407 1


CRISTAL-07a DC873321, HZ8 1,2


CRISTAL-07b DC873321, HZ8W 1,2


CRISTAL-07c – –


CRISTAL-08 ve530029038, CG15 1


CRISTAL-09 DC519281 1


CRISTAL-10 DC417567, HZ2 1, 2


CRISTAL-11 DC630594 1


CRISTAL-12 CG21 1


CRISTAL-13 vc5100994794 1


CRISTAL-14 DC709575 1


CRISTAL-15 vc5101244930 1


CRISTAL-16 CG38 1


CRISTAL-17 DC742174 1


CRISTAL-18 vc5101288969, DC679410 1


CRISTAL-19 DC494763 1


CRISTAL-20 DC494057, HZ4 1, 2


CRISTAL-21 HZ7 1


CRISTAL-22a HZ10, HZ10-C 2, 4


CRISTAL-22b HZ10, HZ10-W 2, 4


CRISTAL-23a DC818760 1


CRISTAL-23b DC818760 1


CRISTAL-23c – –


CRISTAL-24 DC873756 1


CRISTAL-25 vc5101218326 1


**References.** 1. Béthermin et al. (2020); 2. Capak et al. (2015); 3. Riechers et al. (2014); 4. Villanueva et al. (2024).


**Appendix B:** **Visibility modeling with the ALPINE**
**data**


In this section, we briefly discuss how our visibility modeling
improved by adding the data taken from the CRISTAL survey.
In Table B.1, we show the results of visibility modeling using the


Article number, page 20 of 23



ALPINE data alone. We followed the same procedure described
in Section 3.2. Out of the 33 [C ii] components reported in this
work, the ALPINE data was used for 24 components, and we
have successfully modeled 21 components. The fittings did not
converge for the rest of the three components, either due to the
compactness or faintness of the [C ii] line emission. Some of the
merging systems (e.g., CRISTAL-04a and CRISTAL-04b pair)
were able to be modeled as two distinct galaxies if we allow a
circular exponential model.
Figure B.1 compares the fit values between two different
datasets. A slope and _p_ value based on a linear regression fitting
are shown. For the linear regression fitting of the minor-to-major
axis ratios, we exclude the galaxies for which the minor-to-major
axis ratio is unconstrained by the ALPINE data ( _q_ ALPINE = 1).
We find that all three correlations (total flux, effective radius,
and minor-to-major axis ratio) show a good agreement with the
_p_ value smaller than 0.05, demonstrating that the ALPINE data
alone could constrain three parameters well. However, the uncertainties of flux and radius become on average 2.1 and 1.8
times smaller, respectively, when the CRISTAL data is included.
One major improvement is that we have successfully constrained
the minor-to-major axis ratio for more than 90 % of the sample,
while less than half cannot be modeled when only low-resolution
data is used. This could be either due to the difference in the sensitivities or the spatial resolutions of the data.

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6


CRISTAL-01a CRISTAL-01b


CRISTAL-02 CRISTAL-04a


CRISTAL-04b CRISTAL-05


CRISTAL-06b CRISTAL-07a


CRISTAL-07c CRISTAL-08


CRISTAL-09 CRISTAL-11


CRISTAL-12 CRISTAL-13


**Fig.** **A.1.** Visualization of the visibility modeling of the [C ii] line emission in images. The [C ii] line contours are overlaid on the HST/WFC3
F160W image. The left panel shows the dirty image of a single cube used for the visibility modeling (Section 3.2). The FWHM of the dirty beam
is shown as a white ellipse in the lower-left corner. The middle and right panel show the best-fit model and the residual created by subtracting the
model from the data, respectively. A 5 [′′] × 5 [′′] region is shown. The contours start at 2σ and increase in steps of 3σ until 20σ.


Article number, page 21 of 23

_A&A proofs:_ manuscript no. draft


CRISTAL-14 CRISTAL-15


CRISTAL-16 CRISTAL-17


CRISTAL-19 CRISTAL-20


CRISTAL-21 CRISTAL-22a


CRISTAL-22b CRISTAL-23a


CRISTAL-23b CRISTAL-23c


CRISTAL-24 CRISTAL-25


**Fig. A.2.** continued.


Article number, page 22 of 23

R. Ikeda et al.: Spatial extent of [C ii] line emission in SFGs at _z_ = 4 − 6




















|08<br>10 10 0 .. 6 s pl o vp ae lu= e 0 =.7 13 .9×10 4 01 .. 80 s pl o vp ae lu= e=0 .6 06 .026 [kpc]<br>0 .4 0 .6<br>e,ALPINE qALPINE<br>02<br>. 04<br>. log10R<br>00<br>.<br>02<br>.<br>02<br>00 05 10 02 00 02 04 06 08 .02 04 06 08 10<br>. . . . . . . . . . . . . .<br>bined [mJy] log10R e,combined [kpc] qcombined|Col2|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
|0.0<br>0.5<br>1.0<br>bined [mJy]<br>10 10<br>0.2<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>log10Re,combined [kpc]<br>0.2<br>0.0<br>~~0.2~~<br>0.4<br>0.6<br>0.8<br>log10Re,ALPINE [kpc]<br>slope~~=0.73~~<br>p value=1.9×10 4<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>qcombined<br>0.2<br>0.4<br>0.6<br>0.8<br>~~1.0~~<br>qALPINE<br>slope=0.66<br>p value~~=~~0.026|||||||
|0.0<br>0.5<br>1.0<br>bined [mJy]<br>10 10<br>0.2<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>log10Re,combined [kpc]<br>0.2<br>0.0<br>~~0.2~~<br>0.4<br>0.6<br>0.8<br>log10Re,ALPINE [kpc]<br>slope~~=0.73~~<br>p value=1.9×10 4<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>qcombined<br>0.2<br>0.4<br>0.6<br>0.8<br>~~1.0~~<br>qALPINE<br>slope=0.66<br>p value~~=~~0.026|slope=0.66<br>p value~~=~~0.026|slope=0.66<br>p value~~=~~0.026|slope=0.66<br>p value~~=~~0.026|slope=0.66<br>p value~~=~~0.026|slope=0.66<br>p value~~=~~0.026||
|0.0<br>0.5<br>1.0<br>bined [mJy]<br>10 10<br>0.2<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>log10Re,combined [kpc]<br>0.2<br>0.0<br>~~0.2~~<br>0.4<br>0.6<br>0.8<br>log10Re,ALPINE [kpc]<br>slope~~=0.73~~<br>p value=1.9×10 4<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>qcombined<br>0.2<br>0.4<br>0.6<br>0.8<br>~~1.0~~<br>qALPINE<br>slope=0.66<br>p value~~=~~0.026|slope=0.66<br>p value~~=~~0.026||||||
|0.0<br>0.5<br>1.0<br>bined [mJy]<br>10 10<br>0.2<br>0.0<br>0.2<br>0.4<br>0.6<br>0.8<br>log10Re,combined [kpc]<br>0.2<br>0.0<br>~~0.2~~<br>0.4<br>0.6<br>0.8<br>log10Re,ALPINE [kpc]<br>slope~~=0.73~~<br>p value=1.9×10 4<br>0.2<br>0.4<br>0.6<br>0.8<br>1.0<br>qcombined<br>0.2<br>0.4<br>0.6<br>0.8<br>~~1.0~~<br>qALPINE<br>slope=0.66<br>p value~~=~~0.026|slope=0.66<br>p value~~=~~0.026|0.4<br>0.6<br>qcombined|0.4<br>0.6<br>qcombined||||


|slope=0 .73<br>p value =1 .9×10 4|Col2|
|---|---|
|||
||0.2<br><br>,combine|



**Fig.** **B.1.** Comparison of total flux (left), effective radius (middle), and axis ratio (right) measured from the visibility modeling ~~u~~ sing different
datasets. A slope and _p_ value based on a linear regression fitting are sh ~~o~~ wn in the top-left corner of each panel. We exclude the galaxies with
_q_ ALPINE = 1 for the fitting of minor-to-major axis ratio.


**Table B.1.** Structural parameters of the [C ii] line emission measured from the ALPINE data alone.


ID _I_ [CII] _R_ _e_,[CII] _q_ [CII] PA [CII]

(Jy km/s) (kpc) (deg)


CRISTAL-01a 0.72 ± 0.37 2.52 ± 1.94 – –


CRISTAL-01b 0.57 ± 0.32 1.92 ± 2.00 – –


CRISTAL-02 2.70 ± 0.24 2.62 ± 0.46 0.54 ± 0.12 156 ± 9


CRISTAL-03 0.54 ± 0.12 1.50 ± 0.68 – –


CRISTAL-04a 1.25 ± 0.23 2.70 ± 1.02 0.94 ± 0.43 51 ± 226


CRISTAL-04b 0.35 ± 0.12 2.22 ± 1.28 – –


CRISTAL-05 1.01 ± 0.18 1.54 ± 0.89 0.44 ± 0.37 146 ± 25


CRISTAL-07a 0.59 ± 0.19 2.48 ± 1.06 – –


CRISTAL-07b 0.51 ± 0.16 1.58 ± 0.96 – –


CRISTAL-09a – – – –


CRISTAL-10 0.55 ± 0.16 2.61 ± 1.47 0.45 ± 0.34 163 ± 23


CRISTAL-11 1.23 ± 0.21 1.38 ± 0.88 0.42 ± 0.42 83 ± 24


CRISTAL-12 0.14 ± 0.07 1.54 ± 1.69 – –


CRISTAL-13 1.12 ± 0.17 1.70 ± 0.69 0.49 ± 0.27 63 ± 19


CRISTAL-14 – – – –


CRISTAL-15 0.91 ± 0.31 1.76 ± 1.12 – –


CRISTAL-16 0.31 ± 0.14 1.76 ± 1.59 – –


CRISTAL-17 – – – –


CRISTAL-19 0.63 ± 0.11 1.01 ± 0.61 – –


CRISTAL-20 0.97 ± 0.10 2.06 ± 0.63 0.63 ± 0.20 37 ± 18


CRISTAL-23a 5.21 ± 0.42 3.20 ± 0.47 0.71 ± 0.10 115 ± 13


CRISTAL-23b 2.44 ± 0.36 1.89 ± 0.55 0.68 ± 0.26 149 ± 27


CRISTAL-24 13.62 ± 2.08 2.38 ± 0.92 0.59 ± 0.24 108 ± 20


CRISTAL-25 3.29 ± 0.23 1.95 ± 0.51 0.51 ± 0.15 33 ± 10


Article number, page 23 of 23


</paper>

## Items to check

```json
[
 {
  "path": "data.bands.evidence[0]",
  "value": "Band 7",
  "failed_quote": "The primary aim of the survey is to spatially resolve both [C ii] line and FIR continuum emission on ∼ 1 kpc scales with ALMA Band 7 observations for 19 star-forming main sequence galaxies at _z_ = 4 − 6."
 },
 {
  "path": "data.baselines.evidence[0]",
  "value": "compact: uv distance <= 150-300 klambda; extended: uv distance >= 350-1500 klambda",
  "failed_quote": "The former covers low spatial frequencies (_uv_ distance ≲ 150 - 300 kλ) in the visibility plane that are sensitive to large-scale structure (θ beam = 0′′. 29 1′′. 00, θ MRS = 5′′. 28 - 9′′. 79), while the latter covers high spatial frequencies (_uv_ distance ≳ 350 - 1500 kλ, depending on the target)"
 },
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "compact: 0.29\" - 1.00\"; extended: 0.07\" - 0.35\"; synthesized cube: 0.3\" - 0.5\"",
  "failed_quote": "The former covers low spatial frequencies (_uv_ distance ≲ 150 - 300 kλ) in the visibility plane that are sensitive to large-scale structure (θ beam = 0′′. 29 1′′. 00, θ MRS = 5′′. 28 - 9′′. 79), while the latter covers high spatial frequencies (_uv_ distance ≳ 350 - 1500 kλ, depending on the target) that are sensitive to small-scale structure (θ beam = 0′′. 07 0′′. 35, θ MRS = 1′′. 15 - 5′′. 15)."
 },
 {
  "path": "data.max_recoverable_scale.evidence[0]",
  "value": "compact: 5.28\" - 9.79\"; extended: 1.15\" - 5.15\"",
  "failed_quote": "The former covers low spatial frequencies (_uv_ distance ≲ 150 - 300 kλ) in the visibility plane that are sensitive to large-scale structure (θ beam = 0′′. 29 1′′. 00, θ MRS = 5′′. 28 - 9′′. 79), while the latter covers high spatial frequencies (_uv_ distance ≳ 350 - 1500 kλ, depending on the target) that are sensitive to small-scale structure (θ beam = 0′′. 07 0′′. 35, θ MRS = 1′′. 15 - 5′′. 15)."
 },
 {
  "path": "data.observing_dates.evidence[0]",
  "value": "ALMA Cycle 8 and 9, completed in April 2023",
  "failed_quote": "The observations were carried out during ALMA Cycle 8 and 9, and were completed in April 2023."
 },
 {
  "path": "data.other_facilities[1].provided.evidence[0]",
  "value": "High-resolution imaging used to check multiplicity in CRISTAL-11, CRISTAL-15, and CRISTAL-17",
  "failed_quote": "We also find that three galaxies (CRISTAL-11, CRISTAL-15, and CRISTAL-17) classified as single have pair-like morphology when looked with sharper images taken by James Webb Space Telescope (JWST; Lines et al. 2024)."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "Rest-frame UV sizes (Re,UV), FIR continuum sizes (Re,FIR), and obscured star formation rates (SFR_IR)",
  "failed_quote": "We use the values of SFR IR measured in Mitsuhashi et al. (2024) who convert FIR continuum flux (_S_ 158 µm) into IR luminosity (_L_ IR) and then into obscured SFR (SFR IR) following the same method as Béthermin et al. (2020)."
 },
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "Conversion of FIR continuum flux to IR luminosity and obscured SFR",
  "failed_quote": "We use the values of SFR IR measured in Mitsuhashi et al. (2024) who convert FIR continuum flux (_S_ 158 µm) into IR luminosity (_L_ IR) and then into obscured SFR (SFR IR) following the same method as Béthermin et al. (2020)."
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Checked against higher-resolution JWST images (Lines et al. 2024) and kinematical analyses (Posses et al. 2024).",
  "failed_quote": "We also find that three galaxies (CRISTAL-11, CRISTAL-15, and CRISTAL-17) classified as single have pair-like morphology when looked with sharper images taken by James Webb Space Telescope (JWST; Lines et al. 2024)."
 },
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Extract 1D spectrum in a 1-arcsec aperture from the 20 km/s data cube, fit a 1D Gaussian (double Gaussian for CRISTAL-22a) to define the +-2 sigma (95% flux) velocity range, subtract continuum in uv-plane, and bin visibilities over this velocity range into a single channel.",
  "failed_quote": "From the best-fit Gaussian function, we adopted the spectral range that contains 95 % (= [2.5 %, 97.5 %]) of the total [C ii] line flux, corresponding to 4σ (±2σ from the central frequency ν 0) width of Gaussian (≈ 1.7 Gaussian FWHM)."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Single Gaussian line profile (double Gaussian for CRISTAL-22a)",
  "failed_quote": "As an exceptional case, we fit the [C ii] spectrum of CRISTAL-22a, which shows a clear double-peaked line profile, with a double Gaussian."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "Sérsic index n = 1 (exponential disk); 6 free parameters (R.A., Decl., total flux density, major-axis FWHM, minor-to-major axis ratio q, position angle); q fixed to 1 when peak S/N < 8",
  "failed_quote": "We assumed a two-dimensional (2-D) exponential disk model (_n_ = 1) for all of the [C ii] components and first allow six parameters (R.A., Decl., total flux density, major-axis FWHM, minor-to-major axis ratio, and position angle of major axis) free. Some of the fittings fail to converge when the peak S/N of the [C ii] line emission is not high enough (typically S/N < 8). In this case, we fixed the projected minor-to-major axis ratio to unity."
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[0]",
  "value": "16 single galaxies; 20 klambda and 100 klambda uv-distance bins; average redshift z = 5.22",
  "failed_quote": "The model is characterized by an effective radius of _R_ _e_,[CII] = 1.97 ± 0.10 kpc, assuming an average redshift of _z_ = 5.22"
 },
 {
  "path": "analysis_steps[6].validation.evidence[0]",
  "value": "Evaluated p-values of Spearman's rank correlation tests.",
  "failed_quote": "In agreement with previous findings, we find a decreasing trend of the [C ii] line surface density with increasing EW Lyα, with a Spearman’s rank correlation coefficient of −0.51 and a _p_ value of 0.039."
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Stacked visibility single-component [C II] effective radius Re,[CII] = 1.97 kpc",
  "failed_quote": "The model is characterized by an effective radius of _R_ _e_,[CII] = 1.97 ± 0.10 kpc, assuming an average redshift of _z_ = 5.22"
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "Spearman correlation coefficient (log10 Sigma_[CII] vs log10 EW_Lya) = -0.51 dimensionless",
  "failed_quote": "In agreement with previous findings, we find a decreasing trend of the [C ii] line surface density with increasing EW Lyα, with a Spearman’s rank correlation coefficient of −0.51 and a _p_ value of 0.039."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[1]",
  "value": "Multiplicity classification is morphological and does not incorporate kinematical state (e.g., CRISTAL-05 appears single in UV/[C II] morphology but is a line-of-sight pair kinematically), and some HST-single sources are pairs in sharper JWST images.",
  "failed_quote": "We also find that three galaxies (CRISTAL-11, CRISTAL-15, and CRISTAL-17) classified as single have pair-like morphology when looked with sharper images taken by James Webb Space Telescope (JWST; Lines et al. 2024)."
 }
]
```
