# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.530.4887W\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–15 (2023) Preprint 9 February 2024 Compiled using MNRAS L [A] TEX style file v3.0

## **Little evolution of dust emissivity in bright infrared galaxies** **from 2 < z < 6**


B. A. Ward, [1] _[⋆]_ S. A. Eales, [1] R. J. Ivison [2] _[,]_ [3] _[,]_ [4] _[,]_ [5] and V. Arumugam [6]


1 _Cardiff_ _Hub_ _for_ _Astrophysics_ _Research_ _and_ _Technology_ _(CHART),_ _School_ _of_ _Physics_ _and_ _Astronomy,_ _Cardiff_ _University,_ _The_ _Parade,_ _Cardiff_ _CF2_
2 _European_ _Southern_ _Observatory_ _(ESO),_ _Karl-Schwarzschild-Strasse_ _2,_ _D-85748_ _Garching,_ _Germany_
3 _ARC_ _Centre_ _of_ _Excellence_ _for_ _All_ _Sky_ _Astrophysics_ _in_ _3_ _Dimensions_ _(ASTRO_ _3D)_
4 _School_ _of_ _Cosmic_ _Physics,_ _Dublin_ _Institute_ _for_ _Advanced_ _Studies,_ _31_ _Fitzwilliam_ _Place,_ _Dublin_ _D02_ _XF86,_ _Ireland_
5 _Institute_ _for_ _Astronomy,_ _University_ _of_ _Edinburgh,_ _Royal_ _Observatory,_ _Blackford_ _Hill,_ _Edinburgh_ _EH9_ _3HJ_
6 _Institut_ _de_ _Radioastronomie_ _Millimétrique,_ _300_ _rue_ _de_ _la_ _Piscine,_ _Domaine_ _Universitaire,_ _38406_ _Saint_ _Martin_ _d’Hères,_ _France_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

Variations in the dust emissivity index, _β_, within and between galaxies, are evidence that the chemistry and physics
of dust must vary on large scales, although the nature of the physical and/or chemical variations is still unknown. In
this paper we estimate values of _β_ and dust temperature for a sample of 109 dusty star-forming galaxies (DSFGs)
over the range, 2 _< z_ _<_ 6. We compare the results obtained with both an optically-thin model and a general opacity
model, finding that our estimates of _β_ are similar between the models but our estimates of dust temperature are not.
We find no evidence of a change in _β_ with redshift, with a median value of _β_ = 1 _._ 96 for the optically-thin model with
a confidence interval (16–84%) of 1.67 to 2.35 for the population. Using simulations, we estimate the measurement
errors from our procedure and show that the variation of _β_ in the population results from intrinsic variations in
the properties of the dust in DSFGs. At a fixed far-infrared luminosity, we find no evidence for a change in dust
temperature, _T_ dust, with redshift. After allowing for the effects of correlated measurement errors, we find an inverse
correlation between _β_ and _T_ dust in DSFGs, for which there is also evidence in low-redshift galaxies.


**Key** **words:** submillimetre: galaxies – galaxies: evolution



**1** **INTRODUCTION**


Despite contributing only a small percentage (≲ 1 per cent)
of the mass of the interstellar medium (Galliano et al. 2018),
interstellar dust plays a pivotal role in the star-formation processes of galaxies. Dust efficiently absorbs optical and ultraviolet (UV) light from young OB-type stars and active galactic nuclei (AGN) and re-emits this radiation at longer wavelengths, in the far-infrared (FIR) to millimetre-wave (mm)
regimes (e.g. Puget et al. 1996; Dwek et al. 1998; Fixsen et al.
1998; Dole et al. 2006; Driver et al. 2008). This dust obscuration hides star-formation activity in the most massive, dustenshrouded galaxies in the early Universe. The most intense
star formation occurs in dusty star-forming galaxies (DSFGs)
at high redshifts ( _z_ _>_ 1) where stars were produced at rates
of ≳ 100–1000 _M_ _⊙_ yr _[−]_ [1], causing high infrared luminosities
( _L_ IR ), often in excess of _∼_ 10 [12] L _⊙_ (Blain et al. 2002; Casey
et al. 2014; Swinbank et al. 2014; da Cunha et al. 2015, 2021;
Dudzeviči¯ut˙e et al. 2020).
The first high-redshift DSFGs were discovered using the
Sub-millimetre Common User Bolometer Array (SCUBA;


_⋆_ E-mail: WardB2@cardiff.ac.uk


© 2023 The Authors



Holland et al. 1999) on the 15-m James Clerk Maxwell Telescope (JCMT) at 850 _µ_ m (Smail et al. 1997; Barger et al.
1998; Hughes et al. 1998; Eales et al. 1999). Since their discovery, many samples have been selected at wavelengths between 450 _µ_ m – 2 mm using SCUBA’s successor, SCUBA-2
(Holland et al. 2013), e.g. by Wang et al. (2017) and Dudzeviči¯ut˙e et al. (2020), and by other single-dish FIR–mm facilities such as the _Herschel_ _Space_ _Observatory_ (e.g. Eales
et al. 2010; Oliver et al. 2012), AzTEC (e.g. Montaña et al.
2021) and the South Pole Telescope (SPT; e.g. Vieira et al.
2010; Everett et al. 2020), aided by the negative _K_ correction, which means that flux densities decline very slowly for
a fixed _L_ IR at _z_ _>_ 1 (e.g. Blain & Longair 1993).

The very large star-formation rates in these galaxies suggest they contain very large masses of molecular gas. Since it
is impossible to observe the molecular hydrogen directly, the
mass of molecular gas in the DSFGs has been estimated by
the standard method of making observations of a ‘tracer’ of
the hidden gas, then estimating the gas mass from the luminosity of the tracer and a calibration factor linking the two.
The tracers that have been used are the CO molecule, dust
grains and carbon atoms (e.g. Dunne et al. 2022). The dust
method (e.g. Magdis et al. 2012; Eales et al. 2012; Scoville
et al. 2014) is particularly useful for DSFGs because they are

2 _B. A._ _Ward_ _et_ _al._


powerful sources of thermal continuum emission. Studies of
the DSFGs and other high-redshift galaxies have shown that
they contain a higher fraction of gas than observed in galaxies
today (e.g. Tacconi et al. 2010; Scoville et al. 2016; Scoville
et al. 2017; Millard et al. 2020).
In considering this result, however, it should be remembered that the calibration factors are ultimately based on
observations in our own Galaxy, and therefore the method is
based on the implicit assumption that the physics and other
properties of the tracer do not evolve with redshift. In the case
of the dust method, this boils down to the assumptions that
the gas-to-dust ratio and the physical and chemical properties of the dust do not change with redshift. Recent observational (e.g. Shapley et al. 2020; Popping & Péroux 2022) and
theoretical (e.g. Popping et al. 2017; Li et al. 2019) studies
have concluded that the dust-to-gas ratio does not appear to
evolve with redshift.

One useful observational indicator of the physical and
chemical properties of the dust grains is the dust emissivity spectral index, _β_, which describes the frequency dependence of the emissivity of the dust grains, with the optical
depth of the dust being approximated as a power-law, _τ_ _∝_ _ν_ _[β]_ .
Theoretical models of dust (e.g. Draine & Lee 1984) predict
that _β_ should range between 1–2 depending on the chemical composition of the dust grains. The value for dust in the
Galaxy is remarkably uniform over the sky, with a value of
_β_ = 1 _._ 51 _±_ 0 _._ 01 (Planck Collaboration et al. 2015). Although
the assumption necessary to use dust as a tracer of the hidden molecular hydrogen is that the properties of dust are the
same in every galaxy, there is now plenty of evidence that this
is not true. For example, Lamperti et al. (2019) modelled the
FIR SEDs of 192 nearby galaxies from JINGLES (the JCMT
dust and gas In Nearby Galaxies Legacy Exploration Survey)
and found _β_ values between 0.6 and 2.2. Also, there is now
evidence for radial variation of _β_ within galaxies (e.g. Smith
et al. 2012; Draine et al. 2014; Tabatabaei et al. 2014; Hunt
et al. 2015; Whitworth et al. 2019; Clark et al. 2023).
In this study, we test the assumption that the properties
of dust are the same at all cosmic epochs by investigating
whether there is evidence for evolution in the value of the

dust emissivity index. We study bright FIR sources detected
by _Herschel_ and SPT with spectroscopically determined redshifts between 2 ≲ _z_ spec ≲ 6, and model their FIR dust emission to determine the value of _β_ for each galaxy. We investigate whether there is any difference between these values and
those in galaxies today, and also whether there is any change
over this redshift range, corresponding to the period between
about a billion years after the Big Bang and the epoch at
which cosmic star formation was at its peak (e.g. Lilly et al.
1996).
The paper is organised as follows. In Section 2 we describe
the sample used during this analysis. In Section 3 we derive
the dust properties of our sources by fitting their SEDs with
modified blackbodies. In Section 4 we consider the impact
of the well-studied _β_ –dust temperature degeneracy and the
extent to which this biases our results. We also discuss the

robustness of our estimated dust parameters by presenting
simple simulations that imitate the SED fitting routine on
mock _Herschel_ and SPT sources. Section 5 describes the re
sults of our analysis and the suite of simulations used to predict the accuracy of our estimated dust properties. We also
discuss the implications of our findings in the context of the


MNRAS **000**, 1–15 (2023)



existing literature for low redshift galaxies. Finally, we provide a summary of our results in Section 6. Throughout this
paper we assume a ΛCDM cosmology with _H_ 0 = 67.7 km s _[−]_ [1]

Mpc _[−]_ [1] and Ω _m_ = 0.31 (Planck Collaboration et al. 2020).


**2** **THE** **SAMPLE**


The sample studied here is a combination of DSFGs from
_Herschel_, specifically from HerBS ( _Herschel_ Bright Sources;
Bakx et al. 2018), and from the SPT (Reuter et al. 2020).


**2.1** **HerBS** **sub-sample**


The first sub-sample used in this study comes from the HerBS
catalogue, a selection of the brightest high-redshift sources
detected during the _Herschel_ -Astrophysical Terahertz Large
Area Survey (H-ATLAS; Eales et al. 2010). The sample contains 209 galaxies with 500 _µ_ m flux densities above 80 mJy
and photometric redshift estimates in excess of 2.
Spectroscopic redshifts have been obtained for a selection
of HerBS sources within the South Galactic Pole field of _H_ ATLAS, as part of the Bright Extragalactic ALMA Redshift Survey (BEARS; Urquhart et al. 2022, Bendo et al.
2023; Hagimoto et al. 2023). These redshifts were measured
from CO spectral lines detected with the band-3 receivers of
the Atacama Compact Array (ACA), which is part of the
Atacama Large Millimetre Array (ALMA), and also from
spectral lines detected with the band-3 and -4 receivers of
ALMA’s 12-m array. The high spatial resolution of the ALMA
band 4 images ( _∼_ 2”) revealed that many HerBS sources are
composed of more than one source; only half of the HerBS
sources comprise a single source at ALMA’s spatial resolution. In total, Urquhart et al. (2022) measured 71 spectroscopic redshifts for 62 entries in the HerBS catalogue. Several HerBS sources comprise two or more ALMA sources with
spectroscopic redshifts that agree well, suggesting either that
the sources are physically associated galaxies or are multiple images caused by gravitational lensing. For this study,
we have retained the HerBS sources which are multiples in
the ALMA images, if the redshifts of the sources are within
0.1 of each other (we have taken the average redshift as that
of the system). If there are multiple sources in the ALMA
image within the _Herschel_ beam but a spectroscopic redshift
for only one source, we have assumed the sources are physical connected and used the redshift of the one source as the

redshift of the system.
In our study we have used all HerBS sources with spectroscopic redshifts and photometry at 250, 350 and 500 _µ_ m
( _Herschel_ -SPIRE), at 850 _µ_ m (Bakx et al. 2018) and at 2
and 3 mm from ALMA (Bendo et al. 2023. We have also
used photometry in ALMA band 6 (1.1–1.4 mm) from the
ALMARED survey (Jianhang Chen et al., in preparation)
of potentially ‘ultrared’ (see Ivison et al. 2016) sources in
_H_ -ATLAS (project code 2018.1.00526.S). The minimum and
maximum redshifts are _z_ min = 1.569 and _z_ max = 4.509.


**2.2** **SPT** **sub-sample**


Our second sub-sample comprises the 81 DSFGs selected using the SPT (Weiß et al. 2013; Strandet et al. 2016; Reuter
et al. 2020). For a source to be included in this sub-sample, it

_Evolution_ _of_ _dust_ 3



must have a flux density above 25 mJy at 870 _µ_ m. Redshifts
for all SPT sources were obtained via blind searches targeting CO line emission (Weiß et al. 2013; Strandet et al. 2016;
Reuter et al. 2020). There are robust spectroscopic redshifts
(from two or more CO lines) for all except two sources. We
have retained the two because their spectroscopic redshifts
are consistent with the redshifts estimated from photometry.
The sub-sample has redshifts over the range 1.867 < _z_ spec <
6.901 and a median redshift of 3 _._ 9 _±_ 0 _._ 2 (Reuter et al. 2020).
The SPT redshift distribution extends to higher redshifts
than that of HerBS because the longer selection wavelength
modifies the effect of the negative _K_ correction. The extreme
apparent luminosities of the SPT sources implies that most
of them are gravitationally lensed, with lensing models based
on ALMA observations giving a median lensing magnification
factor of 5 _._ 5 _×_ (Spilker et al. 2016).
The SPT sources have photometry between 250 _µ_ m and
3 mm, corresponding to a rest-frame range of 86 _µ_ m ≲ _λ_ rest ≲
380 _µ_ m, meaning that the peak of the dust emission ( _∼_
100 _µ_ m) and Rayleigh-Jeans (R-J) tail are well sampled. The
photometry includes flux densities measured at 250, 350 and
500 _µ_ m ( _Herschel_ -SPIRE), at 870 _µ_ m (APEX-LABOCA), at
1.4 and 2 mm (SPT) and at 3 mm (ALMA). For 65 sources
there are additional constraints at 100 and 160 _µ_ m from _Her-_
_schel_ -PACS.


**2.3** **Restrictions** **on** **sample** **for** **this** **study**


The two sub-samples contain 143 galaxies with spectroscopic
redshifts. However, as we are interested in estimating the
galaxy-integrated _β_ of each source, which is characterised
by the slope of the dust emission on the R-J side of the
Planck function, we restrict our final sample to those galaxies that have at least two photometric measurements at observed wavelengths beyond 1 mm. This reduces our sample
to a total of 109 galaxies (79 SPT DSFGs, plus 30 from
HerBS/BEARS). While the fitting methods used in this work
are the same for both sub-samples, we treat the two separately to look for effects that might have been caused by
their different selection wavelengths and flux density limits.
In Fig. 1 we show the redshift distributions of the two subsamples. The photometry and redshifts of the HerBS-BEARS
sources are tabulated in Appendix A1; the corresponding
data used in this work for the SPT sources can be found
in Reuter et al. (2020).


**3** **SED** **FITTING**


We model the FIR-to-millimetre spectra of our galaxies with
a single modified blackbody (MBB) model combined with
a mid-IR power-law, where the MBB represents the emission from the reservoir of cold dust, which represents most of
the dust in the ISM, and the power-law represents emission
from any dust in the vicinity of star-forming regions, young
OB stars, or active galactic nuclei (AGN). The observed flux
density can be expressed in the following form:



16


14


12


10


8


6


4


2



0

0 2 4 6 8

_z_ spec



**Figure** **1.** Spectroscopic redshift distributions for the SPT DSFGs
(grey) and those from HerBS/BEARS (red).


_τ_ _ν_ is the dust optical depth, _B_ _ν_ ( _T_ dust ) is the Planck function
assuming a characteristic dust temperature of the dust grains,
_T_ dust, _N_ is a normalisation for the power-law which is tied
to the normalisation of the blackbody, and _α_ is the mid-IR
power-law index. The value of _ν_ c is the frequency at which
the gradient of the MBB is equal to the value of _α_ .
We define the solid angle, Ω, as _[A]_ [(][1] _D_ [+] L [2] _[z]_ [)] [4], where _A_ is the area

of the source and _D_ L represents the luminosity distance. The
optical depth, _τ_ _ν_, is defined as the product of dust surface
mass density, Σ dust = _M_ dust _/A_, and the dust opacity, _κ_ _ν_, but
is often assumed to take the form of a power-law, ( _ν/ν_ 1 ) _[β]_,
where _ν_ 1 represents the frequency at which the optical depth
equals unity, marking the frequency of the transition between
optically thin and optically thick dust. This parameter can
be reformulated in terms of intrinsic properties by equating
the two forms of _τ_ such that _ν_ 1 = _ν_ 0 ( _κ_ 0 Σ dust ) _[β]_ . In a similar fashion, _κ_ _ν_ may be assumed to take a power-law form:
_κ_ _ν_ = _κ_ 0 ( _ν/ν_ 0 ) _[β]_, where _κ_ 0 is the emissivity of the dust grains
per unit mass at a given reference frequency, _ν_ 0 . In the following, we assume _κ_ 0 = 0.077 m [2] kg _[−]_ [1] at _ν_ 0 = 353 GHz (Dunne
et al. 2000; James et al. 2002). Combining these, we find the
following equation for the observed flux density of a galaxy:



_µA_ (1+ _z_ )



�1 _−_ _e_ _[−]_ _[M]_ [dust] _A_ _[κ][ν]_




_[κ][ν]_

_A_ _B_ _ν_ ( _T_ dust ) _,_ _ν_ _≤_ _ν_ c
�



_S_ _ν,_ obs =










_D_ L (2)

_µNν_ _[−][α]_ _,_ _ν_ _> ν_ c



_D_ L [2]



where we have included a term, _µ_, to account for the possibility of magnification due to gravitational lensing. For sources
where there is no evidence of gravitational lensing, we assume
_µ_ = 1.
As demonstrated by da Cunha et al. (2013), the heating
of dust by the cosmic microwave background (CMB) has a
non-negligible effect on the shape of the FIR SED when the
temperature of the CMB is a significant fraction of the dust
temperature of a galaxy (see also Zhang et al. 2016 for the
influence of the CMB on the measurement of structural and
dynamical properties). Including the effects of the CMB on
the observed dust continuum using the procedure outlined


MNRAS **000**, 1–15 (2023)



_S_ _ν,_ obs =



Ω
(1+ _z_ ) [3] [(1] _[ −]_ _[e]_ _[−][τ]_ _[ν]_ [ )] _[B]_ _[ν]_ [(] _[T]_ [dust] [)] _[,]_ _ν_ _≤_ _ν_ c (1)
� _Nν_ _[−][α]_ _,_ _ν_ _> ν_ c



where Ω represents the solid angle subtended by the galaxy,

4 _B. A._ _Ward_ _et_ _al._


in da Cunha et al. (2013), the CMB-adjusted MBB model is
now given by:



**Table** **1.** Median and 1 _σ_ errors, estimated from the 16th, 50th
and 84th percentiles of the stacked posterior distribution, for the
parameters presented in Fig. 2.


Parameter Optically _λ_ 1 = _λ_ 1 =
thin 100 _µ_ m 200 _µ_ m

SPT
log( _µM_ dust [M _⊙_ ]) 9 _._ 92 [+0] _−_ 0 _[.]_ _._ [30] 31 9 _._ 77 [+0] _−_ 0 _[.]_ _._ [31] 34 9 _._ 49 [+0] _−_ 0 _[.]_ _._ [37] 41
_T_ dust [K] 32 _._ 07 [+8] _−_ 8 _[.]_ _._ [43] 44 40 _._ 77 [+10] _−_ 11 _[.]_ _._ [90] 77 55 _._ 63 [+11] _−_ 9 _._ 28 _[.]_ [20]
_β_ 1 _._ 98 [+0] _−_ 0 _[.]_ _._ [54] 39 1 _._ 91 [+0] _−_ 0 _[.]_ _._ [50] 32 2 _._ 18 _−_ [+0] 0 _[.]_ _._ [38] 30
log( _µL_ IR [L _⊙_ ]) 13 _._ 98 [+0] _−_ 0 _[.]_ _._ [19] 31 13 _._ 99 [+0] _−_ 0 _[.]_ _._ [19] 30 13 _._ 89 _−_ [+0] 0 _[.]_ _._ [23] 27
_λ_ peak [ _µ_ m] 90 _._ 70 [+17] _−_ 12 _[.]_ _._ [33] 72 90 _._ 70 [+18] _−_ 13 _[.]_ _._ [36] 02 89 _._ 28 [+15] _−_ 13 _[.]_ _._ [21] 39
HerBS
log( _µM_ dust [M _⊙_ ]) 9 _._ 62 [+0] _−_ 0 _[.]_ _._ [30] 22 9 _._ 49 [+0] _−_ 0 _[.]_ _._ [31] 22 9 _._ 30 [+0] _−_ 0 _[.]_ _._ [33] 26
_T_ dust [K] 32 _._ 73 [+5] _−_ 5 _[.]_ _._ [85] 92 41 _._ 16 [+7] _−_ 8 _[.]_ _._ [48] 20 55 _._ 18 _−_ [+7] 9 _[.]_ _._ [25] 23
_β_ 1 _._ 92 [+0] _−_ 0 _[.]_ _._ [39] 32 1 _._ 85 [+0] _−_ 0 _[.]_ _._ [34] 25 2 _._ 08 _−_ [+0] 0 _[.]_ _._ [26] 25
log( _µL_ IR [L _⊙_ ]) 13 _._ 55 [+0] _−_ 0 _[.]_ _._ [27] 37 13 _._ 57 [+0] _−_ 0 _[.]_ _._ [26] 37 13 _._ 57 _−_ [+0] 0 _[.]_ _._ [25] 34
_λ_ peak [ _µ_ m] 90 _._ 03 [+12] _−_ 9 _._ 28 _[.]_ [70] 90 _._ 36 [+13] _−_ 9 _._ 46 _[.]_ [42] 89 _._ 96 [+14] _−_ 9 _._ 46 _[.]_ [92]


flux density uncertainties assuming absolute calibrations of 7
per cent ( _Herschel_ -PACS), 5.5 per cent ( _Herschel_ -SPIRE), 5
per cent (SCUBA-2), 12 per cent (APEX-LABOCA), 7 per
cent (SPT) and 10 per cent (ALMA).


**4** **RESULTS**


**4.1** **Comparison** **between** **the** **optically** **thin** **and**
**general** **opacity** **models**


Fig. 2 shows the stacked posterior probability distributions
for the dust parameters derived for the two samples. The
median values and the 16th and 84th percentiles of the probability distributions are listed in Table 1. The median value
of the main parameter of interest, the dust emissivity spectral
index, covers only a range of 0.2 for the three models, showing
that it doesn’t make much difference what one assumes about
the opacity, a conclusion also reached in a study of a different
sample of DSFGs by Ismail et al. (2023). We note, however,
that the general opacity model with the highest value of _λ_ 1
does give the highest value of _β_, as observed previously by
McKay et al. (2023). Using a sample of 870 _µ_ m-selected galaxies in GOODS-S, McKay et al. (2023) found good agreement
in the median _β_ between an optically thin model (1.78) and
an MBB model with _λ_ 1 = 100 _µ_ m (1.80), but this increased
to 2.02 for a model with _λ_ 1 = 200 _µ_ m. Some recent studies
have suggested that _β_ _>_ 2 is common among high-redshift
galaxies (Casey et al. 2019; Casey et al. 2021; Cooper et al.
2022), but this may be due to these studies using a higher
value for the wavelength at which the dust becomes optically
thick.

The assumption that the dust is optically thin does, however, have a much larger effect for some of the other parameters. There is a clear trend to higher median dust temperatures with increasing _λ_ 1, with increases of _∼_ 10 K and
_∼_ 20 K from the optically-thin model to the _λ_ 1 = 100 _µ_ m
and to the _λ_ 1 = 200 _µ_ m general opacity models, respectively.
The dust masses decrease by approximately 0.1 log( _µ_ M _⊙_ )
and 0.4 log( _µ_ M _⊙_ ) from the optically-thin model to the _λ_ 1 =
100 _µ_ m and the _λ_ 1 = 200 _µ_ m general opacity models, respectively, though we note that these decreases are smaller than
the 1 _σ_ widths of the probability distributions. There is no



1 _−_ _e_ _[−]_ _[M]_ [dust] _A_ _[κ][ν]_ _B_ _ν_ ( _T_ dust ( _z_ )) _,_ _ν_ _≤_ _ν_ c
� �



_S_ _ν,_ obs =








_µA_ (1+ _z_ )
_f_ CMB _D_ L [2]



_f_ CMB _µNν_ _[−][α]_





_D_ L [2]



_f_ CMB _µNν_ _[−][α]_ _,_ _ν_ _> ν_ c



(3)


where we have made the following two changes: i) the prefactor, _f_ CMB, denotes the fraction of the total dust emission that
is observed against the background caused by the hotter CMB
at higher redshifts, given by Equation 18 of da Cunha et al.

(2013), i.e. _f_ CMB = _SS_ _ν_ [observed] _ν_ [intrinsic] = 1 _−_ _[B]_ _B_ _[ν]_ _ν_ [[] [ _[T]_ _T_ [CMB] dust ( [(] _z_ _[z]_ )] [)]] [;] [and] [ii)] [we]

have re-defined the dust temperature to be a function of redshift due to the influence on dust grains of the warmer CMB
at higher redshifts. The derived dust temperature is corrected
for CMB effects using Equation 12 of da Cunha et al. (2013),
1
i.e. _T_ dust ( _z_ ) = [ _T_ dust [4+] _[β]_ _,_ 0 [+] _[ T]_ CMB [ 4+] _[β]_ _,_ 0 [((1 +] _[ z]_ [)] [4+] _[β]_ _[−]_ [1)]] 4+ _β_, where
_T_ dust _,_ 0 is the dust temperature as observed at _z_ = 0 and
_T_ CMB _,_ 0 = 2.73 K is the CMB temperature at _z_ = 0. Note
that all further mention of the dust temperature refers to
the CMB-corrected, luminosity-weighted dust temperature as
given by the model described above, unless otherwise stated.
Using this general form of the MBB, there are up to four free
parameters: the dust mass, the dust temperature, _T_ dust, the
dust emissivity index, _β_, and the frequency at which the dust
opacity reaches unity. If the physical area of the region emitting the submillimetre emission is known, the opacity can be
calculated from the surface density of the dust.
We estimated the parameters of the dust using three different models. In the first model, we assume the dust is optically
thin at all wavelengths ( _τ_ _ν_ _≪_ 1), which eliminates the fourth
of the free parameters in the list above and modifies Eqn 3

to:



_S_ _ν,_ obs =



_µ_ (1+ _z_ )
_f_ CMB _D_ L [2]
� _f_ CMB _µNν_ _[−]_



L (4)

_f_ CMB _µNν_ _[−][α]_ _,_ _ν_ _> ν_ c



_D_ L [2] _z_ _M_ dust _κ_ _ν_ _B_ _ν_ ( _T_ dust ( _z_ )) _,_ _ν_ _≤_ _ν_ c



However, since in DSFGs a large amount of dust is packed
into a small region (e.g. Ikarashi et al. 2017), it is possible
that the dust is optically thick at one or more of the wavelengths covered by our photometry (e.g. Conley et al. 2011;
Casey et al. 2019; Cortzen et al. 2020). We therefore also
used two models in which the dust becomes optically thick
at wavelengths below _λ_ 1 = 100 _µ_ m or 200 _µ_ m.
Some of the SPT sources have measurements of the sizes of
the submillimetre-emitting region, typically _∼_ 1 kpc (Spilker
et al. 2016). For this subset of sources, we also fitted a modified MBB using the size of the emitting region to calculate
the opacity directly.
To estimate the mass and luminosity of the dust we require an estimate of the lensing magnifications, which we have
taken to be those quoted in the lens modelling of Spilker et al.
(2016) for the SPT sources and from the correlation between
CO luminosity and line width as determined by Urquhart
et al. (2022) for HerBS, building on the work of Harris et al.
(2012). During SED fitting we assume flat priors on all free
parameters and take the best-fitting SED to be the median
value of the posterior distribution for each parameter. The
(1- _σ_ ) uncertainties are quoted at the 16th and 84th percentiles. Calibration errors are added in quadrature with the


MNRAS **000**, 1–15 (2023)

|Evol ution of d ust<br>Optically Thin<br>λ1 = 100µm<br>λ1 = 200µm<br>Fixed r<br>Steps<br>MCMC<br>9O λ1p t =ic a 1l 0ly T m1hi0 n 11 25 50 75 1 2 3 4 13 .0 13 .5 14 .0 14 .5<br>0µ<br>λ1 = 200µm|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|_Evolution of dust_<br>9<br>10<br>11<br>Optically Thin<br>_λ_1 = 100_µ_m<br>_λ_1 = 200_µ_m<br>Fixed r<br>25<br>50<br>75<br>1<br>2<br>3<br>4 13_._0 13_._5 14_._0 14_._5<br>Optically Thin<br>_λ_1 = 100_µ_m<br>_λ_1 = 200_µ_m<br>MCMC Steps|Optically Thin<br>_λ_1 = 100_µ_m<br>_λ_1 = 200_µ_m<br>Fixed r|||||
|_Evolution of dust_<br>9<br>10<br>11<br>Optically Thin<br>_λ_1 = 100_µ_m<br>_λ_1 = 200_µ_m<br>Fixed r<br>25<br>50<br>75<br>1<br>2<br>3<br>4 13_._0 13_._5 14_._0 14_._5<br>Optically Thin<br>_λ_1 = 100_µ_m<br>_λ_1 = 200_µ_m<br>MCMC Steps|9<br>10<br>11<br>Optically Thin<br>_λ_1 = 100_µ_m<br>_λ_1 = 200_µ_m|25<br>50<br>75|1<br>2<br>3<br>4|13_._0 13_._5 14_._0 14_._|5|



13 _._ 0 13 _._ 5 14 _._ 0 14 _._ 5

log( _µL_ IR[ _L_ _⊙_ ])



50 100 150
_λ_ [ _µ_ m]
peak



9 10 11
log( _µM_ dust[ _M_ _⊙_ ])



25 50 75
_T_ dust [K]



1 2 3 4
_β_



**Figure** **2.** Stacked posterior distributions of log( _µM_ dust ), _T_ dust, _β_, log( _µL_ IR ) (rest-frame 8–1000 _µ_ m) and _λ_ peak for SPT (top panels)
and HerBS galaxies (bottom panels). The posterior distribution for each MBB model is illustrated as follows: optically thin (shaded);
_λ_ 1 = 100 _µ_ m (solid line); _λ_ 1 = 200 _µ_ m (dashed line); fixed continuum size (hatched).



significant difference in IR luminosities or peak wavelengths
between the models.

Fig. 2 also shows the posterior probability distributions for
the subset of SPT galaxies for which we are able to estimate
the area of the dust region (hatched histograms). This distribution agrees well with the probability distributions for the
optically-thin model and for the general-opacity model with
_λ_ 1 = 100 _µ_ m, but not for the one with _λ_ 1 = 200 _µ_ m. For this
subset of galaxies we find a median value of _λ_ 1 = 88 _µ_ m (16th
and 84th percentile range 44–224 _µ_ m). However, we note that
this value is inversely proportional to the value assumed for
the dust opacity ( _κ_ _ν_ ) and since the opacity of interstellar
dust is still very uncertain (Clark et al. 2016), the frequency
at which the opacity is unity is also uncertain.
Fig. 3 shows the median values of the parameters estimated
from the optically-thin model versus those estimated from
the general-opacity models. As we discussed above, the estimates from the two types of model agree well for _β_, _λ_ peak
and far-infrared luminosity, but there are systematic difference for _T_ dust and _M_ dust . The probability distributions for the
optically-thin model are a good match to those for the subset
of galaxies for which we know the size of the dust region, and
therefore the parameter estimates we discuss in the rest of
this paper have been derived using the optically-thin model.
The panels in Fig. 3 show the size of the systematic errors on
these estimates if the dust is actually optically thick.


**4.2** **The** _β_ **–dust** **temperature** **relationship**


Where an MBB is fitted to an empirical SED it is well
known that an artificial anti-correlation can be produced



between dust temperature and _β_ because of correlated errors in the two parameters (Shetty et al. 2009; Kelly et al.
2012; Juvela & Ysard 2012). Fig. 4 shows that there is a
negative correlation between the measured values of _β_ and
dust temperature for both sub-samples when assuming that
the dust is optically thin. The strength of these correlations
were tested with the Pearson correlation coefficient, _r_ Pearson,
and Spearman’s rank correlation coefficient, _ρ_ Spearman . The
values ( _r_ Pearson = _−_ 0 _._ 83 and _ρ_ Spearman = _−_ 0 _._ 87 for SPT;
_r_ Pearson = _−_ 0 _._ 89 and _ρ_ Spearman = _−_ 0 _._ 89 for HerBS) show
that the SPT and HerBS galaxies exhibit a strong negative
_β_ – _T_ dust correlation and the similarity between the two metrics suggests that few galaxies deviate from the trend. In
the following section, we address the extent to which the observed _β_ – _T_ dust anti-correlation is a true relationship between
dust properties, reflecting an intrinsic change in the emissivity properties of dust grains with temperature, and how much
is due to the fitting method.


**4.3** **Simulations**


In order to assess how accurately our fitting routine derives a
galaxy’s dust parameters, we ran a suite of mock SEDs with
known input parameters and measured how precisely we recover the dust properties from our fits. We generated these
mock SEDs in the following way. We assumed that the dust
emission is described by the optically-thin model (Eqn 4). A
catalogue of models were produced with dust parameters randomly drawn from a uniform distribution between the lower
and upper bounds in Table 2, chosen to reflect the width of
the posterior distributions for the parameters derived for the


MNRAS **000**, 1–15 (2023)

6 _B. A._ _Ward_ _et_ _al._



11 _._ 0


10 _._ 5


10 _._ 0


**9** _**.**_ **5**


9 _._ 0


8 _._ 5



_λ_ 1 = 100 _µ_ m

_λ_ 1 = 200 _µ_ m



10 _._ 25


10 _._ 00


9 _._ 75


9 _._ 50


9 _._ 25


9 _._ 00



_λ_ 1 = 100 _µ_ m

_λ_ 1 = 200 _µ_ m



8 _._ 5 9 _._ 0 **9** _**.**_ **5** 10 _._ 0 10 _._ 5 11 _._ 0
log( _µM_ dust[ _M_ _⊙_ ]) - Optically Thin



9 _._ 00 9 _._ 25 9 _._ 50 9 _._ 75 10 _._ 00 10 _._ 25
log( _µM_ dust[ _M_ _⊙_ ]) - Optically Thin



80


70


60


50


40


30


20


4 _._ 0


3 _._ 5


3 _._ 0


2 _._ 5


2 _._ 0


1 _._ 5


1 _._ 0


14 _._ 50


14 _._ 25


14 _._ 00


13 _._ 75


13 _._ 50


13 _._ 25


150


130


110


90


70



20 30 40 50 60 70 80
_T_ dust [K]  - Optically Thin


1 _._ 0 1 _._ 5 2 _._ 0 2 _._ 5 3 _._ 0 3 _._ 5 4 _._ 0
_β_   - Optically Thin


~~1~~ 3 _._ 25 13 _._ 50 13 _._ 75 14 _._ 00 14 _._ 25 14 _._ 50
lo ~~g~~ ( _µL_ IR[ _L_ _⊙_ ]) - Optically Thin


70 90 110 130 150
_λ_ peak [ _µ_ m] - Optically Thin



70


60


50


40


30


3 _._ 0


2 _._ 5


2 _._ 0


1 _._ 5



30 40 50 60 70
_T_ dust [K] - Optically Thin



1 _._ 0

1 _._ 0 1 _._ 5 2 _._ 0 2 _._ 5 3 _._ 0
_β_     - Optically Thin



14 _._ 00


13 _._ 75


13 _._ 50


13 _._ 25


13 _._ 00


12 _._ 75


140


130


120


110


100


90


80



12 _._ 75 13 _._ 00 13 _._ 25 13 _._ 50 13 _._ 75 14 _._ 00
log( _µL_ IR[ _L_ _⊙_ ]) - Optically Thin


80 90 100 110 120 130 140
_λ_ peak [ _µ_ m] - Optically Thin



**Figure** **3.** Comparison between the parameters derived from the optically-thin and general-opacity models for the galaxies in the SPT
(left column) and HerBS (right column) sub-samples. The general opacity models are shown as filled and open circles for _λ_ 1 = 100 _µ_ m
and 200 _µ_ m, respectively.


MNRAS **000**, 1–15 (2023)

3 _._ 00


2 _._ 75


2 _._ 50


2 _._ 25


2 _._ 00


1 _._ 75


1 _._ 50


1 _._ 25


1 _._ 00


15 20 25 30 35 40 45 50
T [K]


**Figure** **4.** Relationship between the dust temperature and the
emissivity index for the SPT (black) and HerBS (red) galaxies in
the optically thin case.


**Table** **2.** Upper and lower bounds assumed on the flat priors during the simulations described in Section 4.3.


Parameter Bounds

log( _µL_ IR [L _⊙_ ]) 13–14 (HerBS)
13–14.5 (SPT)
_T_ dust [K] 20–50
_β_ 0.5–4

_α_ 1–5


real sources. We created two samples of mock galaxies with
similar properties to the real sub-samples. To create the first
sample, we placed each galaxy at a random redshift between
2 and 4 and gave the galaxy the same photometric coverage as for the HerBS sub-sample, omitting photometry at
1.2 mm as only a few of the HerBS sources have photometry
at this wavelength. To create the second sample, we placed
each galaxy at a random redshift between 2 and 6 and gave
the galaxy the same photometric coverage as the SPT sample. We created observed SEDs of each mock galaxy by adding
flux errors to the model SED, drawing randomly from a normal distribution with a standard deviation equal to the real
observational error at that wavelength. We assumed a lensing magnification of 5 _._ 5 _×_ for all SPT galaxies and 5 _._ 3 _×_ for
all HerBS galaxies, equal to the median lensing magnification
for the two sub-samples. Once we had calculated an observed
SED for each mock galaxy, we removed it from the sample
if it fell below the detection limits of the real samples (Section 2). For the sources that remained, we then derived the
dust parameters using the same modelling procedure we had
applied to the real sample.
Fig. 5 shows the paramaters derived for the two artificial
samples plotted against the input values of these parameters.
There is good agreement between the input and output parameters. The r.m.s. error (RMSE) is calculated for each dust
parameter, showing the intrinsic scatter around the ‘true’ input values. The RMSE indicate that our fitting recovers the
input dust masses to 0.05 dex and 0.03 dex, the dust temperatures to 1.63 K and 1.61 K and _β_ to 0.13 and 0.09 of the



_Evolution_ _of_ _dust_ 7


input values for SPT and HerBS galaxies, respectively. The
accuracy of the output _T_ dust decreases for higher temperatures as a result of the SED shifting to shorter wavelengths,
meaning the peak is then less constrained by the _Herschel_
photometry than at lower temperatures.
The right-most panel of the two simulations in Fig. 5 shows
the difference between the input and output in the _T_ dust – _β_
plane. Since there is no intrinsic correlation between _β_ and
dust temperature in the model, the anti-correlation in this
panel must have been introduced by correlated errors in the
two parameters. The r.m.s. variations in _β_ and _T_ dust in the
artificial dataset are 0.1 and 1.6 K, respectively. The r.m.s.
variations in _β_ and _T_ dust in the real data (Fig. 4) are 0.5 and
8 K, respectively, for the SPT galaxies, and 0.3 and 5 K, respectively, for the HerBS galaxies. The large differences between the r.m.s. values for the simulation and for the real

samples imply there is a genuine inverse correlation between
_β_ and _T_ dust which is not caused by correlated measurement

errors.


**5** **DISCUSSION**


**5.1** **Evolution** **of** _β_ **with** **redshift**


Fig. 6 shows the distribution of galaxies in the _β_ – _z_ plane.
The average value of the emissivity spectral index of SPT and
HerBS galaxies ( _β_ = 1 _._ 98 and 1 _._ 91) are slightly higher than
the values typically assumed for galaxies in the local Universe.
It is significantly higher than the value in our Galaxy, which
is remarkably uniform over the sky: _β_ = 1 _._ 51 _±_ 0 _._ 01 (Planck
Collaboration et al. 2015). It is also significantly higher than
the average value of _β_ for a large sample of nearby galaxies
(Lamperti et al. 2019), although it is close to the values measured for the most massive galaxies in this sample, which may
be the descendants of the DSFGs (Eales et al. 2023). Considering the samples themselves, there is little evidence of any
evolution in _β_ over the redshift range 2 _<_ _z_ _<_ 6. The apparent negative redshift evolution within the HerBS sample
is mostly the effect of the five sources at _z_ _∼_ 4. At this redshift, the selection wavelength of HerBS, 500 _µ_ m, is close to
the peak of the MBB, thus biasing us towards higher temperatures. The intrinsic anti-correlation between dust temperature and _β_ (Section 4.2) would then explain the low values of
_β_ for these galaxies.
Similar conclusions have been reached in two other recent

studies. For an independent sample of DSFGs selected from
HerBS, Ismail et al. (2023) found no evolution in _β_ over 2 _<_
_z_ _<_ 3. For a sample of 17 galaxies, Witstok et al. (2023)
found no evolution across 4 _< z_ _<_ 8.


**5.2** **Variation** **in** _β_


To assess whether the variation of _β_ in Fig. 6 is due to genuine differences in the properties of dust between DSFGs,
or whether it is simply due to measurement errors, we repeated the simulations of the previous section. This time we
used values of _β_ drawn from a uniform distribution covering
the _±_ 1 _σ_ range of the observed values in Fig. 6, generating –
as before – two samples of mock galaxies with observational
data similar to that of the SPT and HerBS sub-samples.
Fig. 7 shows a comparison of the input and output values


MNRAS **000**, 1–15 (2023)

8 _B. A._ _Ward_ _et_ _al._


10 _._ 5

~~RMSE~~ ~~=~~ ~~0.05 dex~~


10 _._ 0


9 _._ 5


9 _._ 0



50


45


40


35


30


25



~~RMSE~~ ~~=~~ ~~0.13~~


1 2 3 4

       _β_ Input


~~RMSE~~ ~~=~~ ~~0.09~~


1 2 3 4

       _β_ Input



0 _._ 2


0 _._ 1


0 _._ 0


_−_ 0 _._ 1


_−_ 0 _._ 2


0 _._ 2


0 _._ 1


0 _._ 0


_−_ 0 _._ 1


_−_ 0 _._ 2



~~RMSE~~ ~~=~~ ~~1.63~~ ~~K~~



_−_ 2 0 2
∆ _T_


_−_ 2 0 2
∆ _T_



8 _._ 5

8 _._ 5 9 _._ 0 9 _._ 5 10 _._ 0 10 _._ 5
log( _M_ dust [ _M_ _⊙_ ])   - Input



20

20 30 40 50
T [K]    - Input


50

~~RMSE~~ ~~=~~ ~~1.61~~ ~~K~~


45


40


35


30


25



4


3


2


1


4


3


2


1



10 _._ 5


10 _._ 0


9 _._ 5


9 _._ 0



~~RMSE~~ ~~=~~ ~~0.03 dex~~



8 _._ 5

8 _._ 5 9 _._ 0 9 _._ 5 10 _._ 0 10 _._ 5
log( _M_ dust [ _M_ _⊙_ ])   - Input



20

20 30 40 50
T [K]    - Input



**Figure** **5.** Comparison of the input and output (measured) values of dust mass, dust temperature and dust emissivity index for the
simulations described in Section 4.3. The right-most panel shows the difference between the input and output (measured) values of dust
temperature against the difference between the input and output (measured) values of _β_ . The top row (black) shows the results for the
mock SPT galaxies and the bottom row (red) shows the results for the mock HerBS galaxies.



of _β_ as a function of redshift for both samples. There is no
tendency for our fitting method to over- or under-predict the
true value of _β_ at any redshift. The r.m.s. scatter in Fig. 7
is _≃_ 0.1, which is much less than the r.m.s. scatter in _β_ in
Fig. 6 ( _≃_ 0.3–0.5), which shows that the measurement errors
are much smaller than the scatter in Fig. 6. Fig. 6 therefore
shows that there are real differences in the properties of dust
between DSFGs, a phenomenon also seen in the low-redshift
galaxy population (Lamperti et al. 2019).


In their study of an independent sample of DSFGs drawn
from HerBS, Ismail et al. (2023) reached similar conclusions.
Across 2 _< z_ _<_ 4, they found an average value of _β_ = 2 _._ 2 _±_ 0 _._ 2
with a range of _β_ from 1.5 to 3.0, very similar to our results for
the combined HerBS/SPT sample. They, too, concluded that
the variation in _β_ is caused by intrinsic differences between
the dust in different DSFGs rather than by measurement errors. In their sample of 17 galaxies in the range 4 _<_ _z_ _<_ 8,
Witstok et al. (2023) found a mean value of _β_ = 1 _._ 8 _±_ 0 _._ 3, in
agreement with our estimates, with a similar wide range of
_β_ from _≃_ 1 _._ 5 to _≃_ 2 _._ 7. Other recent studies of high-redshift
galaxies find similar values of _β_ (da Cunha et al. 2021; Cooper
et al. 2022).


Some of the SPT galaxies in Fig. 6 have values of _β_ _≃_ 3, as
do galaxies in other high-redshift samples (Ismail et al. 2023;
Witstok et al. 2023). Such values are higher than the global
values seen in local galaxies (Lamperti et al. 2019), although
such high values have been seen within Andromeda (Smith
et al. 2012) and the Galaxy (Bracco et al. 2011). Are there any
methodological limitations which might explain these results?


For our sample, one possible explanation might be the 3mm photometry for the SPT sources. These flux densities
were measured from ALMA images, so it is possible that they


MNRAS **000**, 1–15 (2023)



are too low because of the possibility – as with all interferometers – that some extended flux has been missed (the ‘zero
baseline problem’). We assessed how much would need to be
lost by repeating the SED fitting without the 3-mm photometry, with _β_ = 2. We did this for five sources: SPT0112 _−_ 55
( _β_ = 3 _._ 62), SPT0611 _−_ 55 ( _β_ = 3 _._ 44), SPT2203 _−_ 41 ( _β_ =
2 _._ 84), SPT2349 _−_ 52 ( _β_ = 3 _._ 62) and SPT2357 _−_ 51 ( _β_ = 2 _._ 80).
Comparing the flux density at 3 mm predicted by the model
with the observed flux density, we find that the observed flux
density would need to be between 60–80 per cent lower than
the true flux density to explain the very high values of _β_ .
Although this is possible, given the structures seen for highredshift galaxies it seems unlikely, and it seems more likely to
us that some of these extreme values found by us and others
are genuine.


**5.3** **The** **inverse** _β_ **–** _T_ **dust** **relationship**


Our simulations imply that the inverse relationship seen between _β_ and _T_ dust is not the result of measurement errors.
Another study of an independent sample of HerBS sources
reached a similar conclusion (Ismail et al. 2023). A similar
conclusion was also reached by a hierarchical Bayesian study
of nearby galaxies (Lamperti et al. 2019).


**5.4** **Evolution** **of** _T_ **dust** **with** **redshift**


Does the temperature of dust increase with redshift? This has
been a matter of intense debate in the literature. Some groups
find evidence for an increase, e.g. Magdis et al. (2012); Magnelli et al. (2014); Swinbank et al. (2014); Béthermin et al.
(2015); Ivison et al. (2016); Faisst et al. (2017); Schreiber

# 4 . 0 3 . 5 3 . 0 2 . 5 2 . 0 1 . 5 1 . 0



_Evolution_ _of_ _dust_ 9


# 0 . 5 0 1 2 3 4 5 6 7 z spec



**Figure** **6.** Distribution of _β_ for the HerBS (red) and SPT (black) galaxies versus redshift, with the canonical values from JINGLES
(green) and the Milky Way (blue). The median value of the stacked posterior distributions are shown as red and black lines for the HerBS
and SPT sub-samples, respectively, with the shaded regions showing the 16th to 84th percentiles.



et al. (2018); Zavala et al. (2018); Liang et al. (2019); Ma et al.
(2019); Faisst et al. (2020); Bakx et al. (2021); Witstok et al.
(2023), which might not be surprising since both high specific
star-formation rates and lower dust abundances at high redshift might lead to higher dust temperatures. Others report
a fall, e.g. Symeonidis et al. (2013). An important caveat,
noted by many of those studies, is the correlation between
dust temperature and luminosity (Dunne et al. 2000) which
– since galaxies at high redshift tend to have high luminosities – might lead to a correlation between dust temperature
and redshift. In contrast, the works of Casey et al. (2018); Jin
et al. (2019); Lim et al. (2020); Dudzeviči¯ut˙e et al. (2020);
Reuter et al. (2020); Barger et al. (2022); Drew & Casey
(2022) and Witstok et al. (2023), among others, report little
or no evolution of temperature with redshift at a given fixed
IR luminosity.


The dust temperature derived from SED fitting depends
on the model assumed for the dust opacity, whereas _λ_ peak
is the same for every model. To avoid this dependence, we
have derived _λ_ peak for each source and then calculated _T_ dust



from Wien’s displacement law. Although this will not be the
same as the true temperature of the dust, it allows us to
see whether there is any evidence for a change in _T_ dust with
redshift.


The top panel of Fig. 8 shows the distribution of IR luminosity for the full sample of galaxies as obtained from the
fitting of Equation 4, as well as the detection limits. In calculating the detection limits, we have assumed an SED with
a dust temperature of 32 K, the median temperature of the
sample, and _β_ = 2. To avoid the selection effect caused by
the luminosity–temperature relationship, we only consider
sources selected in a small range of IR luminosity, as illustrated by the boxed regions. The bottom panel of Fig. 8 shows
the peak dust temperature ( _T_ peak = 2 _._ 898 _×_ 10 [3] [ _µ_ mK]/ _λ_ peak

[ _µ_ m]) versus redshift. We have plotted the observational relationships inferred by Schreiber et al. (2018), Bouwens et al.
(2020) and Viero et al. (2022). Bootstrap fitting with a linear
model gives an evolution rate of 5 _._ 20 _±_ 0 _._ 92 and _−_ 0 _._ 25 _±_ 0 _._ 52
_T_ peak _/z_ for the HerBS and SPT galaxies, respectively. In a
study of an independent sample of HerBS galaxies, Ismail


MNRAS **000**, 1–15 (2023)

10 _B. A._ _Ward_ _et_ _al._


0 _._ 4


0 _._ 2


0 _._ 0


_−_ 0 _._ 2



14


13


12


60


40


20



_−_ 0 _._ 4


0 _._ 4


0 _._ 2


0 _._ 0


_−_ 0 _._ 2


_−_ 0 _._ 4






|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|1_._68_ < β_inpu|1_._68_ < β_inpu|t _<_ 2_._41|t _<_ 2_._41||
||||||
|1_._61_ < β_in|put _<_ 2_._26|put _<_ 2_._26|||


|Col1|Col2|
|---|---|
|Below CMB Temperature<br>chreiber+2018<br>ouwens+2020<br>iero+2022<br>amperti+2019|Below CMB Temperature<br>chreiber+2018<br>ouwens+2020<br>iero+2022<br>amperti+2019|



0 2 4 6
_z_ input


**Figure** **7.** Difference between the input and output _β_ values,
∆ _β_ = _β_ output _−_ _β_ input, as a function of the input redshift for
mock SPT galaxies (top panel) and mock _Herschel_ galaxies (bottom panel). Filled circles represent mock galaxies with SEDs that
would have been observed according to their respective survey limits. Dotted vertical lines represent the minimum and maximum
redshift observed in each sub-sample. The thick solid lines represent the median in ∆ _β_ .


et al. (2023) found a rate of evolution of 6 _._ 5 _±_ 0 _._ 5 _K/z_, similar to our value.

While there is statistical evidence within the HerBS subsample – both ours and that of Ismail et al. (2023) – for the
evolution of temperature with redshift, there seems little evidence for any such evolution over the redshift range covered
by the combined HerBS and SPT sample.
We suggest there is a simple selection effect that explains
the temperature evolution seen in the HerBS sample. For the
highest redshift sources in the HerBS sub-sample, the selection wavelength in the rest frame is close to the peak of the
MBB, which leads to a selection bias towards sources with
higher temperatures. Given the lack of any obvious correlation when both sub-samples are considered together, we
conclude that there is no strong evidence for temperature
evolution. A plausible suggestion for the disagreement in the
literature was suggested by Drew & Casey (2022): the studies
that have found no evolution are those that looked for evolu
tion at a fixed infrared luminosity, as in this paper, whereas
those that found evolution were generally looking for evolution at a fixed stellar mass. The latter would be expected to
see evolution because of the gradual increase in specific starformation rate – and thus the increase in the intensity of the
interstellar radiation field – with redshift.


MNRAS **000**, 1–15 (2023)



0

0 2 4 6

_z_ spec



**Figure 8.** Top: distribution of HerBS (red) and SPT (black) galaxies in the _µL_ IR – _z_ plane. Red and black lines represent the detection limit of a source detected at _>_ 80 mJy (500 _µ_ m) and _>_ 25 mJy
(870 _µ_ m) with _β_ = 2 and _T_ dust = 32 K. Boxed regions show the
limits of the unbiased, luminosity-limited set of sources from which
we test evolutionary trends in the dust temperature. Bottom: distribution of dust temperature with redshift for the sources selected
in our luminosity-limited subset. Observed trends from Schreiber
et al. (2018); Bouwens et al. (2020) and Viero et al. (2022) are
illustrated as cyan, orange and purple lines, respectively. The median dust temperature of local sources from JINGLES is shown in

green.


**6** **CONCLUSIONS**


In this paper we estimate values of _β_ and dust temperature
for a sample of 109 dusty star-forming galaxies spanning 2 _<_
_z_ _<_ 6. We have obtained the following results:


_•_ We have compared the results from fitting the emission
from the galaxies with an optically-thin model and with two
general-opacity models, one in which the dust becomes optically thick at a wavelength of 100 _µ_ m, the other where the
dust becomes optically thick at 200 _µ_ m. We find that our estimates of _β_, the peak of the galaxy SED, and the far-infrared
luminosity, are similar between the models, although there is
a change in _β_ of 0.2 between the most extreme models. In
contrast, our estimates of dust mass and dust temperature
depend strongly on the opacity assumptions.

_•_ For a sub-sample of 37 galaxies, we have measurements of
the sizes of the sources, which allows us to estimate the opacity directly. We find very similar estimates of the galaxy parameters with this model to the optically-thin model, which
we use for the rest of the paper.

_•_ We find no evidence of any change in _β_ with redshift
across 2 _<_ _z_ _<_ 6, with a median value of _β_ = 1 _._ 96 for the
optically-thin model and a 14–86% confidence interval for the
population of 1.65 to 2.38. Using simulations, we estimate the

measurement errors from our procedure and show that the
variation of _β_ in the population is the result of intrinsic variations in the properties of the dust in DSFGs, the same found
between galaxies in the low-redshift Universe (Lamperti et al.
2019).

_•_ After allowing for the effect of correlated errors, we find
an inverse correlation between our estimates of _β_ and dust

temperature.

_•_ We find no evidence at a fixed far-infrared luminosity for
any change in dust temperature with redshift.


The results in this and other recent papers show that the
properties of dust appear to differ between galaxies, both at
high and low redshift. Ours and other recent papers show that
there appears to be intrinsic anti-correlation between dust
emissivity index and dust temperature. As far as we know,
there is no chemical/physical model of dust that explains
either of these results.


**ACKNOWLEDGEMENTS**


BW thanks the Engineering and Physical Sciences Research Council for a PhD studentship. SAE thanks the Science and Technology Facilities Council (consolidated grant
ST/K000926/1) for the funds that supported this research.


**DATA** **AVAILABILITY**


The photometry for each galaxy and the results of fitting our
models to the photometry are listed in the appendix.


**REFERENCES**


Bakx T. J. L. C., et al., 2018, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx2267) 473, 1751
Bakx T. J. L. C., et al., 2021, [MNRAS,](http://dx.doi.org/10.1093/mnrasl/slab104) 508, L58
Barger A. J., Cowie L. L., Sanders D. B., Fulton E., Taniguchi Y.,
Sato Y., Kawara K., Okuda H., 1998, [Nature,](http://dx.doi.org/10.1038/28338) 394, 248
Barger A. J., Cowie L. L., Blair A. H., Jones L. H., 2022, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ac67e7)

[934,](https://ui.adsabs.harvard.edu/abs/2022ApJ...934...56B) 56
Bendo G. J., et al., 2023, [MNRAS,](http://dx.doi.org/10.1093/mnras/stac3771) 522, 2995
Béthermin M., et al., 2015, [A&A,](http://dx.doi.org/10.1051/0004-6361/201425031) 573, [A113](https://ui.adsabs.harvard.edu/abs/2015A&A...573A.113B)
Blain A. W., Longair M. S., 1993, [MNRAS,](http://dx.doi.org/10.1093/mnras/264.2.509) 264, 509
Blain A. W., Smail I., Ivison R. J., Kneib J. P., Frayer D. T., 2002,

[Phys.](http://dx.doi.org/10.1016/S0370-1573(02)00134-5) Rep., 369, 111
Bouwens R., et al., 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/abb830) 902, 112
Bracco A., et al., 2011, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2010.17971.x) 412, 1151
Casey C. M., Narayanan D., Cooray A., 2014, [Phys.](http://dx.doi.org/10.1016/j.physrep.2014.02.009) Rep., [541,](https://ui.adsabs.harvard.edu/abs/2014PhR...541...45C) 45
Casey C. M., et al., 2018, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aac82d) [862,](https://ui.adsabs.harvard.edu/abs/2018ApJ...862...77C) 77
Casey C. M., et al., 2019, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab52ff) [887,](https://ui.adsabs.harvard.edu/abs/2019ApJ...887...55C) 55
Casey C. M., et al., 2021, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ac2eb4) 923, 215
Clark C. J. R., Schofield S. P., Gomez H. L., Davies J. I., 2016,

[MNRAS,](http://dx.doi.org/10.1093/mnras/stw647) 459, 1646
Clark C. J. R., Roman-Duval J. C., Gordon K. D., Bot C., Smith
M. W. L., Hagen L. M. Z., 2023, [ApJ,](http://dx.doi.org/10.3847/1538-4357/acbb66) [946,](https://ui.adsabs.harvard.edu/abs/2023ApJ...946...42C) 42
Conley A., et al., 2011, [ApJ,](http://dx.doi.org/10.1088/2041-8205/732/2/L35) 732, L35
Cooper O. R., Casey C. M., Zavala J. A., Champagne J. B., da
Cunha E., Long A. S., Spilker J. S., Staguhn J., 2022, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ac616d)
[930,](https://ui.adsabs.harvard.edu/abs/2022ApJ...930...32C) 32
Cortzen I., et al., 2020, [A&A,](http://dx.doi.org/10.1051/0004-6361/201937217) 634, L14
Dole H., et al., 2006, [A&A,](http://dx.doi.org/10.1051/0004-6361:20054446) 451, 417
Draine B. T., Lee H. M., 1984, [ApJ,](http://dx.doi.org/10.1086/162480) [285,](https://ui.adsabs.harvard.edu/abs/1984ApJ...285...89D) 89
Draine B. T., et al., 2014, [ApJ,](http://dx.doi.org/10.1088/0004-637X/780/2/172) 780, 172
Drew P. M., Casey C. M., 2022, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ac6270) 930, 142



_Evolution_ _of_ _dust_ 11


Driver S. P., Popescu C. C., Tuffs R. J., Graham A. W., Liske J.,
Baldry I., 2008, [ApJ,](http://dx.doi.org/10.1086/588582) 678, [L101](https://ui.adsabs.harvard.edu/abs/2008ApJ...678L.101D)
Dudzeviči¯ut˙e U., et al., 2020, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa769) 494, 3828
Dunne L., Eales S., Edmunds M., Ivison R., Alexander P.,
Clements D. L., 2000, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.2000.03386.x) 315, 115
Dunne L., Maddox S. J., Papadopoulos P. P., Ivison R. J., Gomez
H. L., 2022, [MNRAS,](http://dx.doi.org/10.1093/mnras/stac2098) 517, 962
Dwek E., et al., 1998, [ApJ,](http://dx.doi.org/10.1086/306382) 508, 106
Eales S., Lilly S., Gear W., Dunne L., Bond J. R., Hammer F., Le
Fèvre O., Crampton D., 1999, [ApJ,](http://dx.doi.org/10.1086/307069) 515, 518
Eales S., et al., 2010, [PASP,](http://dx.doi.org/10.1086/653086) 122, 499
Eales S., et al., 2012, [ApJ,](http://dx.doi.org/10.1088/0004-637X/761/2/168) 761, 168
Eales S., Gomez H., Dunne L., Dye S., Smith M. W. L., 2023,

arXiv [e-prints,](http://dx.doi.org/10.48550/arXiv.2303.07376) p. [arXiv:2303.07376](https://ui.adsabs.harvard.edu/abs/2023arXiv230307376E)
Everett W. B., et al., 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab9df7) [900,](https://ui.adsabs.harvard.edu/abs/2020ApJ...900...55E) 55
Faisst A. L., et al., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa886c) [847,](https://ui.adsabs.harvard.edu/abs/2017ApJ...847...21F) 21
Faisst A. L., Fudamoto Y., Oesch P. A., Scoville N., Riechers D. A.,
Pavesi R., Capak P., 2020, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa2545) 498, 4192
Fixsen D. J., Dwek E., Mather J. C., Bennett C. L., Shafer R. A.,
1998, [ApJ,](http://dx.doi.org/10.1086/306383) 508, 123
Galliano F., Galametz M., Jones A. P., 2018, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-081817-051900) 56, 673
Hagimoto M., et al., 2023, [MNRAS,](http://dx.doi.org/10.1093/mnras/stad784) 521, 5508
Harris A. I., et al., 2012, [ApJ,](http://dx.doi.org/10.1088/0004-637X/752/2/152) 752, 152
Holland W. S., et al., 1999, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.1999.02111.x) 303, 659
Holland W. S., et al., 2013, [MNRAS,](http://dx.doi.org/10.1093/mnras/sts612) 430, 2513
Hughes D. H., et al., 1998, [Nature,](http://dx.doi.org/10.1038/28328) 394, 241
Hunt L. K., et al., 2015, [A&A,](http://dx.doi.org/10.1051/0004-6361/201424734) 576, A33
Ikarashi S., et al., 2017, [ApJ,](http://dx.doi.org/10.3847/2041-8213/aa9572) 849, L36
Ismail D., et al., 2023, arXiv [e-prints,](http://dx.doi.org/10.48550/arXiv.2307.15747) p. [arXiv:2307.15747](https://ui.adsabs.harvard.edu/abs/2023arXiv230715747I)
Ivison R. J., et al., 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/832/1/78) [832,](https://ui.adsabs.harvard.edu/abs/2016ApJ...832...78I) 78
James A., Dunne L., Eales S., Edmunds M. G., 2002, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.2002.05660.x)

335, 753
Jin S., et al., 2019, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab55d6) 887, 144
Juvela M., Ysard N., 2012, [A&A,](http://dx.doi.org/10.1051/0004-6361/201118596) 541, A33
Kelly B. C., Shetty R., Stutz A. M., Kauffmann J., Goodman
A. A., Launhardt R., 2012, [ApJ,](http://dx.doi.org/10.1088/0004-637X/752/1/55) [752,](https://ui.adsabs.harvard.edu/abs/2012ApJ...752...55K) 55
Lamperti I., et al., 2019, [MNRAS,](http://dx.doi.org/10.1093/mnras/stz2311) 489, 4389
Li Q., Narayanan D., Davé R., 2019, [MNRAS,](http://dx.doi.org/10.1093/mnras/stz2684) 490, 1425
Liang L., et al., 2019, [MNRAS,](http://dx.doi.org/10.1093/mnras/stz2134) 489, 1397
[Lilly S. J., Le Fevre O., Hammer F., Crampton D., 1996, ApJ, 460,](http://dx.doi.org/10.1086/309975)

[L1](https://ui.adsabs.harvard.edu/abs/1996ApJ...460L...1L)

Lim C.-F., et al., 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ab607f) [889,](https://ui.adsabs.harvard.edu/abs/2020ApJ...889...80L) 80
Ma X., et al., 2019, [MNRAS,](http://dx.doi.org/10.1093/mnras/stz1324) 487, 1844
Magdis G. E., et al., 2012, [ApJ,](http://dx.doi.org/10.1088/0004-637X/760/1/6) [760,](https://ui.adsabs.harvard.edu/abs/2012ApJ...760....6M) 6
Magnelli B., et al., 2014, [A&A,](http://dx.doi.org/10.1051/0004-6361/201322217) 561, A86
McKay S. J., Barger A. J., Cowie L. L., Bauer F. E., Rosenthal
M. J. N., 2023, [ApJ,](http://dx.doi.org/10.3847/1538-4357/acd1e5) [951,](https://ui.adsabs.harvard.edu/abs/2023ApJ...951...48M) 48
Millard J. S., et al., 2020, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa609) 494, 293
Montaña A., et al., 2021, [MNRAS,](http://dx.doi.org/10.1093/mnras/stab1649) 505, 5260
Oliver S. J., et al., 2012, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2012.20912.x) 424, 1614
Planck Collaboration et al., 2015, [A&A,](http://dx.doi.org/10.1051/0004-6361/201424088) 576, [A107](https://ui.adsabs.harvard.edu/abs/2015A&A...576A.107P)
Planck Collaboration et al., 2020, [A&A,](http://dx.doi.org/10.1051/0004-6361/201833910) [641,](https://ui.adsabs.harvard.edu/abs/2020A&A...641A...6P) A6
Popping G., Péroux C., 2022, [MNRAS,](http://dx.doi.org/10.1093/mnras/stac695) 513, 1531
Popping G., Somerville R. S., Galametz M., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx1545) [471,](https://ui.adsabs.harvard.edu/abs/2017MNRAS.471.3152P)

[3152](https://ui.adsabs.harvard.edu/abs/2017MNRAS.471.3152P)

Puget J. L., Abergel A., Bernard J. P., Boulanger F., Burton W. B.,
Desert F. X., Hartmann D., 1996, A&A, [308,](https://ui.adsabs.harvard.edu/abs/1996A&A...308L...5P) L5
Reuter C., et al., 2020, [ApJ,](http://dx.doi.org/10.3847/1538-4357/abb599) [902,](https://ui.adsabs.harvard.edu/abs/2020ApJ...902...78R) 78
Schreiber C., Elbaz D., Pannella M., Ciesla L., Wang T., Franco
M., 2018, [A&A,](http://dx.doi.org/10.1051/0004-6361/201731506) 609, A30
Scoville N., et al., 2014, [ApJ,](http://dx.doi.org/10.1088/0004-637X/783/2/84) [783,](https://ui.adsabs.harvard.edu/abs/2014ApJ...783...84S) 84
Scoville N., et al., 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/820/2/83) [820,](https://ui.adsabs.harvard.edu/abs/2016ApJ...820...83S) 83
Scoville N., et al., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa61a0) 837, 150
Shapley A. E., Cullen F., Dunlop J. S., McLure R. J., Kriek M.,
Reddy N. A., Sanders R. L., 2020, [ApJ,](http://dx.doi.org/10.3847/2041-8213/abc006) 903, L16
Shetty R., Kauffmann J., Schnee S., Goodman A. A., 2009, [ApJ,](http://dx.doi.org/10.1088/0004-637X/696/1/676)

696, 676
Smail I., Ivison R. J., Blain A. W., 1997, [ApJ,](http://dx.doi.org/10.1086/311017) [490,](https://ui.adsabs.harvard.edu/abs/1997ApJ...490L...5S) L5


MNRAS **000**, 1–15 (2023)

12 _B. A._ _Ward_ _et_ _al._


Smith M. W. L., et al., 2012, [ApJ,](http://dx.doi.org/10.1088/0004-637X/756/1/40) [756,](https://ui.adsabs.harvard.edu/abs/2012ApJ...756...40S) 40
Spilker J. S., et al., 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/826/2/112) 826, 112
Strandet M. L., et al., 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/822/2/80) [822,](https://ui.adsabs.harvard.edu/abs/2016ApJ...822...80S) 80
Swinbank A. M., et al., 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stt2273) 438, 1267
Symeonidis M., et al., 2013, [MNRAS,](http://dx.doi.org/10.1093/mnras/stt330) 431, 2317
Tabatabaei F. S., et al., 2014, [A&A,](http://dx.doi.org/10.1051/0004-6361/201321441) 561, A95
Tacconi L. J., et al., 2010, [Nature,](http://dx.doi.org/10.1038/nature08773) 463, 781
Urquhart S. A., et al., 2022, [MNRAS,](http://dx.doi.org/10.1093/mnras/stac150) 511, 3017
Vieira J. D., et al., 2010, [ApJ,](http://dx.doi.org/10.1088/0004-637X/719/1/763) 719, 763
Viero M. P., Sun G., Chung D. T., Moncelsi L., Condon S. S.,
2022, [MNRAS,](http://dx.doi.org/10.1093/mnrasl/slac075) 516, L30
Wang W.-H., et al., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa911b) [850,](https://ui.adsabs.harvard.edu/abs/2017ApJ...850...37W) 37
Weiß A., et al., 2013, [ApJ,](http://dx.doi.org/10.1088/0004-637X/767/1/88) [767,](https://ui.adsabs.harvard.edu/abs/2013ApJ...767...88W) 88
Whitworth A. P., et al., 2019, [MNRAS,](http://dx.doi.org/10.1093/mnras/stz2166) 489, 5436
Witstok J., Jones G. C., Maiolino R., Smit R., Schneider R., 2023,

[MNRAS,](http://dx.doi.org/10.1093/mnras/stad1470) 523, 3119
Zavala J. A., et al., 2018, [MNRAS,](http://dx.doi.org/10.1093/mnras/sty217) 475, 5585
Zhang Z.-Y., Papadopoulos P. P., Ivison R. J., Galametz M., Smith
M. W. L., Xilouris E. M., 2016, Royal Society Open Science,
3, [160025](https://ui.adsabs.harvard.edu/abs/2016RSOS....360025Z)
da Cunha E., et al., 2013, [ApJ,](http://dx.doi.org/10.1088/0004-637X/766/1/13) [766,](https://ui.adsabs.harvard.edu/abs/2013ApJ...766...13D) 13
da Cunha E., et al., 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/806/1/110) 806, 110
da Cunha E., et al., 2021, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ac0ae0) [919,](https://ui.adsabs.harvard.edu/abs/2021ApJ...919...30D) 30


This paper has been typeset from a TEX/L [A] TEX file prepared by
the author.


MNRAS **000**, 1–15 (2023)

_Evolution_ _of_ _dust_ 13


**APPENDIX** **A:** **HERBS** **PHOTOMETRY**


Table A1: Spectroscopic redshifts, lensing magnifications and photometry for
HerBS sources.


Source Spec-z _µ_ _S_ 250 _µ_ m _S_ 350 _µ_ m _S_ 500 _µ_ m _S_ 850 _µ_ m _S_ 1 _._ 2 mm _S_ 2 mm _S_ 3 mm
(mJy) (mJy) (mJy) (mJy) (mJy) (mJy) (mJy)
HerBS-11 2.631 18.4 257.5 _±_ 6.4 271.1 _±_ 6.3 204.0 _±_ 7.2 67.3 _±_ 6.3 – 3.59 _±_ 0.03 0.93 _±_ 0.02

HerBS-14 3.782 36.4 116.3 _±_ 6.1 177.0 _±_ 6.3 179.3 _±_ 7.5 77.9 _±_ 6.4 28.9 _±_ 0.6 7.31 _±_ 0.04 1.50 _±_ 0.02

HerBS-18 2.182 27.9 212.9 _±_ 4.7 244.2 _±_ 5.0 169.4 _±_ 6.2 52.9 _±_ 6.1 – 2.73 _±_ 0.03 0.74 _±_ 0.06

HerBS-21 3.323 6.1 125.8 _±_ 5.5 185.5 _±_ 5.8 155.1 _±_ 7.4 51.3 _±_ 6.3 – 3.92 _±_ 0.03 0.94 _±_ 0.10

HerBS-24 2.198 4.6 170.9 _±_ 5.7 197.1 _±_ 6.3 145.6 _±_ 7.4 64.8 _±_ 7.8 – 2.68 _±_ 0.03 0.74 _±_ 0.03

HerBS-25 2.912 49.8 112.5 _±_ 5.0 148.0 _±_ 5.4 143.4 _±_ 6.5 49.2 _±_ 5.7 – 3.52 _±_ 0.03 0.81 _±_ 0.11

HerBS-27 4.509 14.6 72.2 _±_ 5.3 129.8 _±_ 5.6 138.6 _±_ 7.0 90.5 _±_ 6.3 28.9 _±_ 1.0 8.70 _±_ 0.03 1.97 _±_ 0.02

HerBS-28 3.925 5.7 79.4 _±_ 5.8 135.4 _±_ 6.0 140.0 _±_ 7.4 79.4 _±_ 7.8 25.5 _±_ 1.2 5.56 _±_ 0.03 1.66 _±_ 0.10

HerBS-36 3.095 5.4 121.5 _±_ 6.1 161.0 _±_ 6.7 125.5 _±_ 7.7 64.0 _±_ 8.8 – 4.81 _±_ 0.03 1.11 _±_ 0.02

HerBS-39 3.229 5.1 118.3 _±_ 5.1 141.2 _±_ 5.5 119.7 _±_ 6.8 36.5 _±_ 7.0 – 3.01 _±_ 0.03 0.64 _±_ 0.03

HerBS-41 4.098 2.1 63.3 _±_ 6.2 91.1 _±_ 6.1 121.7 _±_ 7.4 31.8 _±_ 5.9 15.2 _±_ 0.5 4.85 _±_ 0.07 –

HerBS-42 3.307 3.9 130.3 _±_ 5.8 160.0 _±_ 6.1 116.2 _±_ 6.8 50.4 _±_ 6.1 – 2.95 _±_ 0.06 0.58 _±_ 0.05

HerBS-49 2.727 15.3 76.8 _±_ 6.0 110.9 _±_ 6.2 110.4 _±_ 7.3 31.9 _±_ 8.5 – 1.69 _±_ 0.04 1.13 _±_ 0.09

HerBS-55 2.656 13.7 109.0 _±_ 5.3 116.5 _±_ 5.5 107.1 _±_ 6.6 29.9 _±_ 7.1 – 1.05 _±_ 0.03 0.33 _±_ 0.02

HerBS-57 3.265 15.0 118.1 _±_ 4.9 147.3 _±_ 5.2 105.4 _±_ 6.4 60.7 _±_ 8.5 – 3.05 _±_ 0.02 0.50 _±_ 0.02

HerBS-60 3.261 9.5 73.3 _±_ 5.8 101.2 _±_ 6.1 103.6 _±_ 7.5 39.8 _±_ 5.7 13.2 _±_ 0.8 2.54 _±_ 0.03 0.53 _±_ 0.02

HerBS-68 2.719 10.5 139.1 _±_ 5.3 144.8 _±_ 5.4 100.5 _±_ 6.6 46.7 _±_ 7.7 – 1.62 _±_ 0.04 0.32 _±_ 0.05

HerBS-73 3.026 3.1 117.1 _±_ 6.0 129.0 _±_ 6.2 99.6 _±_ 7.4 49.4 _±_ 6.8 – 2.09 _±_ 0.03 0.43 _±_ 0.02

HerBS-86 2.564 4.8 77.4 _±_ 5.6 90.7 _±_ 5.8 96.0 _±_ 7.4 33.8 _±_ 6.1 8.1 _±_ 0.6 1.56 _±_ 0.02 0.25 _±_ 0.02

HerBS-93 2.400 2.4 77.3 _±_ 5.4 87.3 _±_ 5.7 94.8 _±_ 7.0 22.8 _±_ 5.7 6.2 _±_ 0.4 1.39 _±_ 0.02 0.16 _±_ 0.01

HerBS-103 2.942 4.3 126.1 _±_ 5.3 131.2 _±_ 5.7 93.5 _±_ 7.0 33.7 _±_ 7.6 – 1.40 _±_ 0.03 0.42 _±_ 0.02

HerBS-111 2.371 4.3 105.9 _±_ 6.5 115.6 _±_ 6.2 92.7 _±_ 7.4 13.3 _±_ 6.9 – 1.13 _±_ 0.02 0.21 _±_ 0.02

HerBS-132 2.473 4.8 86.7 _±_ 5.8 102.6 _±_ 6.0 90.6 _±_ 7.8 16.6 _±_ 7.4 – 0.86 _±_ 0.02 0.16 _±_ 0.02

HerBS-145 2.730 1.9 54.7 _±_ 6.0 67.4 _±_ 6.2 86.8 _±_ 7.7 13.4 _±_ 7.0 5.1 _±_ 0.6 1.06 _±_ 0.04 –

HerBS-160 3.955 8.1 48.6 _±_ 5.6 84.2 _±_ 6.0 84.8 _±_ 7.1 36.6 _±_ 6.4 15.0 _±_ 0.6 3.94 _±_ 0.02 0.91 _±_ 0.02

HerBS-182 2.227 1.1 89.0 _±_ 5.7 109.1 _±_ 6.2 82.3 _±_ 7.9 – – 1.04 _±_ 0.03 0.21 _±_ 0.02

HerBS-184 2.507 6.0 91.9 _±_ 5.9 107.6 _±_ 6.0 82.3 _±_ 7.1 – – 1.49 _±_ 0.02 0.48 _±_ 0.02

HerBS-200 2.151 0.4 107.1 _±_ 6.1 109.7 _±_ 6.0 80.5 _±_ 7.5 11.3 _±_ 6.6 – 0.78 _±_ 0.02 0.25 _±_ 0.01

HerBS-207 1.569 5.2 96.9 _±_ 5.9 121.7 _±_ 6.1 80.2 _±_ 7.5 33.1 _±_ 6.3 – 0.89 _±_ 0.02 0.25 _±_ 0.03

HerBS-208 2.481 1.4 69.4 _±_ 5.1 91.9 _±_ 5.5 80.1 _±_ 6.6 – – 1.40 _±_ 0.05 0.32 _±_ 0.04


MNRAS **000**, 1–15 (2023)

14 _B. A._ _Ward_ _et_ _al._


**APPENDIX** **B:** **BEST-FITTING** **SED** **PARAMETERS**


Table B1: Best-fitting SED parameters for all SPT sources.


Source Spec-z log( _M_ dust [ _M_ _⊙_ ]) _T_ dust [K] _β_ _χ_ [2] _ν_
SPT0002-52 2.351 8 _._ 95 _−_ [+0] 0 _[.]_ _._ [05] 05 33 _._ 23 _−_ [+2] 1 _[.]_ _._ [19] 80 2 _._ 08 _−_ [+0] 0 _[.]_ _._ [11] 12 2.05
SPT0020-51 4.123 9 _._ 16 _−_ [+0] 0 _[.]_ _._ [06] 06 33 _._ 49 _−_ [+3] 3 _[.]_ _._ [02] 04 1 _._ 90 _−_ [+0] 0 _[.]_ _._ [18] 17 0.57
SPT0027-50 3.444 9 _._ 29 _−_ [+0] 0 _[.]_ _._ [04] 04 33 _._ 48 _−_ [+1] 1 _[.]_ _._ [35] 25 2 _._ 03 _−_ [+0] 0 _[.]_ _._ [10] 09 3.02
SPT0054-41 4.877 9 _._ 26 _−_ [+0] 0 _[.]_ _._ [08] 06 31 _._ 67 _−_ [+3] 3 _[.]_ _._ [54] 99 2 _._ 12 _−_ [+0] 0 _[.]_ _._ [25] 22 0.84
SPT0103-45 3.090 9 _._ 57 _−_ [+0] 0 _[.]_ _._ [08] 07 25 _._ 37 _−_ [+2] 2 _[.]_ _._ [84] 88 2 _._ 14 _−_ [+0] 0 _[.]_ _._ [29] 22 1.10
SPT0106-64 4.910 9 _._ 21 _−_ [+0] 0 _[.]_ _._ [05] 05 41 _._ 39 _−_ [+3] 2 _[.]_ _._ [65] 93 1 _._ 78 _−_ [+0] 0 _[.]_ _._ [14] 15 3.65
SPT0109-47 3.614 8 _._ 78 _−_ [+0] 0 _[.]_ _._ [05] 05 35 _._ 33 _−_ [+2] 3 _[.]_ _._ [12] 32 1 _._ 96 _−_ [+0] 0 _[.]_ _._ [18] 13 2.85
SPT0112-55 3.443 9 _._ 18 _−_ [+0] 0 _[.]_ _._ [24] 35 14 _._ 35 _−_ [+4] 1 _[.]_ _._ [40] 59 3 _._ 62 _−_ [+0] 0 _[.]_ _._ [25] 50 6.53
SPT0113-46 4.233 8 _._ 84 _−_ [+0] 0 _[.]_ _._ [13] 12 22 _._ 52 _−_ [+5] 3 _[.]_ _._ [08] 33 2 _._ 35 _−_ [+0] 0 _[.]_ _._ [38] 43 1.40
SPT0125-47 2.515 9 _._ 47 _−_ [+0] 0 _[.]_ _._ [05] 05 38 _._ 81 _−_ [+2] 2 _[.]_ _._ [07] 88 1 _._ 67 _−_ [+0] 0 _[.]_ _._ [14] 11 2.69
SPT0125-50 3.957 8 _._ 77 _−_ [+0] 0 _[.]_ _._ [06] 06 46 _._ 69 _−_ [+3] 2 _[.]_ _._ [35] 78 1 _._ 32 _−_ [+0] 0 _[.]_ _._ [13] 13 3.83
SPT0136-63 4.299 9 _._ 18 _−_ [+0] 0 _[.]_ _._ [07] 06 28 _._ 24 _−_ [+2] 2 _[.]_ _._ [68] 68 2 _._ 21 _−_ [+0] 0 _[.]_ _._ [22] 20 0.42
SPT0147-64 4.803 9 _._ 30 _−_ [+0] 0 _[.]_ _._ [07] 06 35 _._ 28 _−_ [+3] 5 _[.]_ _._ [98] 08 1 _._ 70 _−_ [+0] 0 _[.]_ _._ [27] 19 2.39
SPT0150-59 2.788 9 _._ 26 _−_ [+0] 0 _[.]_ _._ [05] 05 33 _._ 29 _−_ [+1] 2 _[.]_ _._ [88] 26 1 _._ 70 _−_ [+0] 0 _[.]_ _._ [13] 11 2.63
SPT0155-62 4.349 10 _._ 01 _−_ [+0] 0 _[.]_ _._ [07] 07 22 _._ 43 _−_ [+2] 1 _[.]_ _._ [40] 78 2 _._ 21 _−_ [+0] 0 _[.]_ _._ [20] 23 3.32
SPT0202-61 5.018 9 _._ 12 _−_ [+0] 0 _[.]_ _._ [04] 04 57 _._ 61 _−_ [+4] 3 _[.]_ _._ [19] 64 0 _._ 96 _−_ [+0] 0 _[.]_ _._ [11] 11 6.46
SPT0226-45 3.233 9 _._ 01 _−_ [+0] 0 _[.]_ _._ [07] 08 28 _._ 51 _−_ [+4] 2 _[.]_ _._ [58] 15 2 _._ 38 _−_ [+0] 0 _[.]_ _._ [18] 26 4.29
SPT0243-49 5.702 9 _._ 67 _−_ [+0] 0 _[.]_ _._ [11] 09 26 _._ 80 _−_ [+4] 4 _[.]_ _._ [61] 30 1 _._ 87 _−_ [+0] 0 _[.]_ _._ [39] 38 0.71
SPT0245-63 5.626 9 _._ 84 _−_ [+0] 0 _[.]_ _._ [08] 08 30 _._ 30 _−_ [+4] 3 _[.]_ _._ [99] 47 2 _._ 09 _−_ [+0] 0 _[.]_ _._ [28] 31 1.07
SPT0300-46 3.595 9 _._ 35 _−_ [+0] 0 _[.]_ _._ [07] 07 31 _._ 26 _−_ [+2] 3 _[.]_ _._ [94] 23 1 _._ 96 _−_ [+0] 0 _[.]_ _._ [26] 20 0.96
SPT0311-58 6.901 9 _._ 28 _−_ [+0] 0 _[.]_ _._ [09] 08 42 _._ 17 [+10] _−_ 7 _._ _[.]_ 33 [20] 1 _._ 66 _−_ [+0] 0 _[.]_ _._ [35] 37 1.37
SPT0314-44 2.935 9 _._ 44 _−_ [+0] 0 _[.]_ _._ [04] 04 31 _._ 57 _−_ [+1] 1 _[.]_ _._ [35] 22 2 _._ 01 _−_ [+0] 0 _[.]_ _._ [10] 09 2.96
SPT0319-47 4.510 9 _._ 38 _−_ [+0] 0 _[.]_ _._ [09] 08 37 _._ 93 _−_ [+5] 5 _[.]_ _._ [07] 60 1 _._ 66 _−_ [+0] 0 _[.]_ _._ [33] 24 1.63
SPT0345-47 4.296 8 _._ 85 _−_ [+0] 0 _[.]_ _._ [06] 06 52 _._ 45 _−_ [+2] 2 _[.]_ _._ [45] 60 1 _._ 47 _−_ [+0] 0 _[.]_ _._ [12] 11 1.22
SPT0346-52 5.655 9 _._ 24 _−_ [+0] 0 _[.]_ _._ [05] 06 52 _._ 76 _−_ [+4] 7 _[.]_ _._ [10] 17 1 _._ 31 _−_ [+0] 0 _[.]_ _._ [26] 16 2.94
SPT0348-62 5.654 9 _._ 59 _−_ [+0] 0 _[.]_ _._ [14] 12 26 _._ 19 _−_ [+4] 3 _[.]_ _._ [35] 48 2 _._ 60 _−_ [+0] 0 _[.]_ _._ [30] 33 0.21
SPT0402-45 2.683 9 _._ 46 _−_ [+0] 0 _[.]_ _._ [04] 04 33 _._ 16 _−_ [+1] 1 _[.]_ _._ [60] 62 2 _._ 07 _−_ [+0] 0 _[.]_ _._ [10] 09 8.22
SPT0403-58 4.056 9 _._ 40 _−_ [+0] 0 _[.]_ _._ [07] 07 36 _._ 14 _−_ [+3] 4 _[.]_ _._ [77] 35 1 _._ 81 _−_ [+0] 0 _[.]_ _._ [23] 19 2.28
SPT0418-47 4.225 8 _._ 30 _−_ [+0] 0 _[.]_ _._ [19] 09 29 _._ 92 _−_ [+2] 9 _[.]_ _._ [89] 65 2 _._ 43 _−_ [+0] 0 _[.]_ _._ [83] 23 7.44
SPT0425-40 5.135 8 _._ 78 _−_ [+0] 0 _[.]_ _._ [05] 05 44 _._ 68 _−_ [+2] 3 _[.]_ _._ [69] 05 1 _._ 78 _−_ [+0] 0 _[.]_ _._ [15] 12 4.65
SPT0436-40 3.852 9 _._ 20 _−_ [+0] 0 _[.]_ _._ [16] 16 23 _._ 42 _−_ [+7] 3 _[.]_ _._ [81] 87 2 _._ 59 _−_ [+0] 0 _[.]_ _._ [38] 51 2.63
SPT0441-46 4.480 8 _._ 89 _−_ [+0] 0 _[.]_ _._ [13] 13 28 _._ 48 [+11] _−_ 5 _._ _[.]_ 46 [44] 2 _._ 07 _−_ [+0] 0 _[.]_ _._ [50] 55 3.66
SPT0452-50 2.011 10 _._ 07 _−_ [+0] 0 _[.]_ _._ [13] 10 19 _._ 02 _−_ [+2] 2 _[.]_ _._ [76] 34 2 _._ 02 _−_ [+0] 0 _[.]_ _._ [30] 27 1.63
SPT0459-58 4.856 9 _._ 06 _−_ [+0] 0 _[.]_ _._ [11] 09 31 _._ 52 _−_ [+6] 5 _[.]_ _._ [78] 52 2 _._ 03 _−_ [+0] 0 _[.]_ _._ [42] 37 0.68
SPT0459-59 4.799 9 _._ 48 _−_ [+0] 0 _[.]_ _._ [09] 09 25 _._ 24 _−_ [+3] 2 _[.]_ _._ [93] 83 2 _._ 29 _−_ [+0] 0 _[.]_ _._ [30] 33 0.80
SPT0512-59 2.233 9 _._ 39 _−_ [+0] 0 _[.]_ _._ [04] 05 29 _._ 06 _−_ [+1] 1 _[.]_ _._ [69] 46 1 _._ 92 _−_ [+0] 0 _[.]_ _._ [14] 13 0.83
SPT0516-59 3.404 8 _._ 68 _−_ [+0] 0 _[.]_ _._ [05] 05 36 _._ 36 _−_ [+2] 2 _[.]_ _._ [21] 30 1 _._ 97 _−_ [+0] 0 _[.]_ _._ [15] 13 2.31
SPT0520-53 3.779 9 _._ 09 _−_ [+0] 0 _[.]_ _._ [08] 07 32 _._ 54 _−_ [+3] 4 _[.]_ _._ [22] 43 1 _._ 83 _−_ [+0] 0 _[.]_ _._ [27] 18 1.54
SPT0528-53 4.737 8 _._ 69 _−_ [+0] 0 _[.]_ _._ [12] 08 36 _._ 91 _−_ [+6] 7 _[.]_ _._ [77] 38 1 _._ 76 _−_ [+0] 0 _[.]_ _._ [36] 30 1.14
SPT0529-54 3.368 9 _._ 38 _−_ [+0] 0 _[.]_ _._ [09] 11 19 _._ 07 _−_ [+3] 2 _[.]_ _._ [29] 03 2 _._ 62 _−_ [+0] 0 _[.]_ _._ [29] 36 0.80
SPT0532-50 3.399 9 _._ 33 _−_ [+0] 0 _[.]_ _._ [04] 04 38 _._ 56 _−_ [+2] 1 _[.]_ _._ [15] 94 1 _._ 38 _−_ [+0] 0 _[.]_ _._ [13] 12 0.86
SPT0538-50 2.786 8 _._ 98 _−_ [+0] 0 _[.]_ _._ [05] 06 33 _._ 59 _−_ [+1] 1 _[.]_ _._ [98] 75 1 _._ 71 _−_ [+0] 0 _[.]_ _._ [15] 16 1.36
SPT0544-40 4.269 9 _._ 14 _−_ [+0] 0 _[.]_ _._ [05] 05 38 _._ 11 _−_ [+2] 2 _[.]_ _._ [45] 89 1 _._ 65 _−_ [+0] 0 _[.]_ _._ [15] 14 2.75
SPT0550-53 3.128 9 _._ 20 _−_ [+0] 0 _[.]_ _._ [08] 09 25 _._ 27 _−_ [+3] 2 _[.]_ _._ [60] 46 2 _._ 17 _−_ [+0] 0 _[.]_ _._ [26] 28 1.92
SPT0551-48 2.583 9 _._ 54 _−_ [+0] 0 _[.]_ _._ [06] 06 39 _._ 01 _−_ [+2] 2 _[.]_ _._ [94] 66 1 _._ 52 _−_ [+0] 0 _[.]_ _._ [18] 16 2.27
SPT0551-50 3.164 9 _._ 24 _−_ [+0] 0 _[.]_ _._ [05] 05 32 _._ 99 _−_ [+1] 1 _[.]_ _._ [71] 58 1 _._ 83 _−_ [+0] 0 _[.]_ _._ [13] 12 2.83
SPT0552-42 4.438 9 _._ 25 _−_ [+0] 0 _[.]_ _._ [10] 09 27 _._ 06 _−_ [+3] 3 _[.]_ _._ [98] 29 2 _._ 03 _−_ [+0] 0 _[.]_ _._ [25] 25 0.88
SPT0553-50 5.323 8 _._ 89 _−_ [+0] 0 _[.]_ _._ [07] 07 39 _._ 50 _−_ [+5] 4 _[.]_ _._ [27] 90 1 _._ 65 _−_ [+0] 0 _[.]_ _._ [28] 25 0.90
SPT0555-62 4.815 9 _._ 01 _−_ [+0] 0 _[.]_ _._ [10] 10 30 _._ 00 _−_ [+8] 3 _[.]_ _._ [01] 66 2 _._ 22 _−_ [+0] 0 _[.]_ _._ [27] 40 4.84
SPT0604-64 2.481 9 _._ 52 _−_ [+0] 0 _[.]_ _._ [04] 04 28 _._ 98 _−_ [+1] 1 _[.]_ _._ [14] 11 2 _._ 13 _−_ [+0] 0 _[.]_ _._ [09] 08 4.53
SPT0611-55 2.026 8 _._ 92 _−_ [+0] 0 _[.]_ _._ [07] 07 19 _._ 45 _−_ [+1] 2 _[.]_ _._ [33] 26 3 _._ 44 _−_ [+0] 0 _[.]_ _._ [34] 22 4.45
SPT0625-58 2.727 9 _._ 48 _−_ [+0] 0 _[.]_ _._ [04] 04 32 _._ 41 _−_ [+1] 1 _[.]_ _._ [44] 32 1 _._ 80 _−_ [+0] 0 _[.]_ _._ [09] 09 2.85
SPT0652-55 3.347 9 _._ 65 _−_ [+0] 0 _[.]_ _._ [14] 08 24 _._ 80 _−_ [+2] 4 _[.]_ _._ [77] 72 2 _._ 35 _−_ [+0] 0 _[.]_ _._ [39] 24 4.53
SPT2031-51 2.452 9 _._ 40 _−_ [+0] 0 _[.]_ _._ [04] 04 29 _._ 27 _−_ [+1] 1 _[.]_ _._ [37] 26 2 _._ 00 _−_ [+0] 0 _[.]_ _._ [10] 10 2.18
SPT2037-65 3.998 9 _._ 89 _−_ [+0] 0 _[.]_ _._ [04] 04 46 _._ 72 _−_ [+3] 3 _[.]_ _._ [06] 15 0 _._ 70 _−_ [+0] 0 _[.]_ _._ [13] 11 2.16
SPT2048-55 4.090 9 _._ 24 _−_ [+0] 0 _[.]_ _._ [05] 06 42 _._ 17 _−_ [+3] 3 _[.]_ _._ [71] 35 1 _._ 11 _−_ [+0] 0 _[.]_ _._ [15] 14 1.07
SPT2101-60 3.155 9 _._ 11 _−_ [+0] 0 _[.]_ _._ [04] 04 33 _._ 91 _−_ [+1] 1 _[.]_ _._ [73] 70 1 _._ 93 _−_ [+0] 0 _[.]_ _._ [12] 11 1.76
SPT2103-60 4.436 8 _._ 65 _−_ [+0] 0 _[.]_ _._ [10] 09 22 _._ 20 _−_ [+2] 2 _[.]_ _._ [88] 33 2 _._ 68 _−_ [+0] 0 _[.]_ _._ [28] 29 2.44
SPT2129-57 3.260 9 _._ 04 _−_ [+0] 0 _[.]_ _._ [05] 05 37 _._ 26 _−_ [+2] 1 _[.]_ _._ [08] 88 1 _._ 75 _−_ [+0] 0 _[.]_ _._ [11] 11 3.51
SPT2132-58 4.768 9 _._ 24 _−_ [+0] 0 _[.]_ _._ [09] 10 29 _._ 82 _−_ [+9] 4 _[.]_ _._ [38] 40 1 _._ 91 _−_ [+0] 0 _[.]_ _._ [36] 48 1.90


MNRAS **000**, 1–15 (2023)

_Evolution_ _of_ _dust_ 15


Table B1: Best-fitting SED parameters for all SPT sources.


Source Spec-z log( _M_ dust [ _M_ _⊙_ ]) _T_ dust [K] _β_ _χ_ [2] _ν_
SPT2134-50 2.780 8 _._ 67 _−_ [+0] 0 _[.]_ _._ [05] 06 37 _._ 39 _−_ [+3] 2 _[.]_ _._ [60] 13 1 _._ 70 _−_ [+0] 0 _[.]_ _._ [14] 15 3.51
SPT2146-55 4.567 9 _._ 03 _−_ [+0] 0 _[.]_ _._ [10] 10 33 _._ 32 _−_ [+8] 5 _[.]_ _._ [78] 89 1 _._ 80 _−_ [+0] 0 _[.]_ _._ [39] 39 1.01
SPT2147-50 3.760 9 _._ 01 _−_ [+0] 0 _[.]_ _._ [07] 07 30 _._ 72 _−_ [+3] 2 _[.]_ _._ [25] 49 2 _._ 05 _−_ [+0] 0 _[.]_ _._ [21] 20 2.62
SPT2152-40 3.851 9 _._ 29 _−_ [+0] 0 _[.]_ _._ [22] 11 30 _._ 11 _−_ [+6] 9 _[.]_ _._ [51] 32 1 _._ 92 _−_ [+0] 0 _[.]_ _._ [69] 38 4.47
SPT2203-41 5.194 9 _._ 23 _−_ [+0] 0 _[.]_ _._ [15] 12 21 _._ 94 _−_ [+2] 2 _[.]_ _._ [92] 43 2 _._ 84 _−_ [+0] 0 _[.]_ _._ [24] 27 1.89
SPT2232-61 2.894 9 _._ 18 _−_ [+0] 0 _[.]_ _._ [06] 06 27 _._ 91 _−_ [+2] 2 _[.]_ _._ [27] 59 2 _._ 24 _−_ [+0] 0 _[.]_ _._ [19] 15 2.93
SPT2311-45 2.507 9 _._ 18 _−_ [+0] 0 _[.]_ _._ [05] 05 31 _._ 51 _−_ [+2] 1 _[.]_ _._ [45] 74 1 _._ 78 _−_ [+0] 0 _[.]_ _._ [12] 14 2.71
SPT2311-54 4.280 9 _._ 18 _−_ [+0] 0 _[.]_ _._ [06] 06 40 _._ 77 _−_ [+3] 4 _[.]_ _._ [49] 39 1 _._ 83 _−_ [+0] 0 _[.]_ _._ [20] 16 4.16
SPT2316-50 3.141 8 _._ 71 _−_ [+0] 0 _[.]_ _._ [13] 11 23 _._ 11 _−_ [+3] 3 _[.]_ _._ [44] 33 2 _._ 75 _−_ [+0] 0 _[.]_ _._ [38] 31 1.04
SPT2319-55 5.293 8 _._ 74 _−_ [+0] 0 _[.]_ _._ [10] 10 29 _._ 34 _−_ [+6] 3 _[.]_ _._ [12] 78 2 _._ 21 _−_ [+0] 0 _[.]_ _._ [29] 33 1.10
SPT2332-53 2.726 9 _._ 18 _−_ [+0] 0 _[.]_ _._ [04] 05 39 _._ 12 _−_ [+1] 1 _[.]_ _._ [82] 68 1 _._ 86 _−_ [+0] 0 _[.]_ _._ [11] 11 6.82
SPT2335-53 4.756 8 _._ 46 _−_ [+0] 0 _[.]_ _._ [11] 09 30 _._ 55 _−_ [+4] 5 _[.]_ _._ [68] 40 2 _._ 68 _−_ [+0] 0 _[.]_ _._ [38] 31 1.93
SPT2340-59 3.862 8 _._ 84 _−_ [+0] 0 _[.]_ _._ [14] 11 26 _._ 28 _−_ [+3] 4 _[.]_ _._ [79] 89 2 _._ 71 _−_ [+0] 0 _[.]_ _._ [41] 29 3.62
SPT2349-50 2.876 9 _._ 37 _−_ [+0] 0 _[.]_ _._ [07] 07 30 _._ 69 _−_ [+3] 4 _[.]_ _._ [06] 05 2 _._ 06 _−_ [+0] 0 _[.]_ _._ [24] 18 3.26
SPT2349-52 3.900 8 _._ 58 _−_ [+0] 0 _[.]_ _._ [22] 17 19 _._ 49 _−_ [+4] 2 _[.]_ _._ [23] 99 3 _._ 62 _−_ [+0] 0 _[.]_ _._ [37] 34 2.62
SPT2351-57 5.811 8 _._ 65 _−_ [+0] 0 _[.]_ _._ [07] 06 39 _._ 58 _−_ [+4] 4 _[.]_ _._ [69] 72 1 _._ 98 _−_ [+0] 0 _[.]_ _._ [23] 21 3.76
SPT2353-50 5.578 8 _._ 83 _−_ [+0] 0 _[.]_ _._ [11] 10 35 _._ 44 _−_ [+8] 6 _[.]_ _._ [18] 36 1 _._ 94 _−_ [+0] 0 _[.]_ _._ [37] 34 1.85
SPT2354-58 1.867 9 _._ 09 _−_ [+0] 0 _[.]_ _._ [05] 07 31 _._ 95 _−_ [+3] 2 _[.]_ _._ [77] 00 2 _._ 05 _−_ [+0] 0 _[.]_ _._ [12] 16 1.73
SPT2357-51 3.070 9 _._ 39 _−_ [+0] 0 _[.]_ _._ [16] 09 21 _._ 63 _−_ [+2] 3 _[.]_ _._ [26] 65 2 _._ 80 _−_ [+0] 0 _[.]_ _._ [36] 24 3.82


Table B2: Best-fitting SED parameters for all HerBS sources.


Source Spec-z log( _M_ dust [ _M_ _⊙_ ]) _T_ dust [K] _β_ _χ_ [2] _ν_
HerBS-11 2.631 8 _._ 63 _−_ [+0] 0 _[.]_ _._ [03] 04 34 _._ 01 _−_ [+1] 1 _[.]_ _._ [78] 58 1 _._ 84 _−_ [+0] 0 _[.]_ _._ [10] 10 1.63
HerBS-14 3.782 8 _._ 42 _−_ [+0] 0 _[.]_ _._ [04] 03 37 _._ 51 _−_ [+1] 2 _[.]_ _._ [77] 08 1 _._ 64 _−_ [+0] 0 _[.]_ _._ [12] 10 1.45
HerBS-18 2.182 8 _._ 47 _−_ [+0] 0 _[.]_ _._ [03] 04 29 _._ 05 _−_ [+1] 1 _[.]_ _._ [45] 29 1 _._ 95 _−_ [+0] 0 _[.]_ _._ [11] 11 0.94
HerBS-21 3.323 9 _._ 01 _−_ [+0] 0 _[.]_ _._ [04] 04 35 _._ 63 _−_ [+1] 1 _[.]_ _._ [73] 70 1 _._ 81 _−_ [+0] 0 _[.]_ _._ [12] 11 0.18
HerBS-24 2.198 9 _._ 27 _−_ [+0] 0 _[.]_ _._ [04] 04 28 _._ 70 _−_ [+1] 1 _[.]_ _._ [65] 43 1 _._ 87 _−_ [+0] 0 _[.]_ _._ [11] 11 3.60
HerBS-25 2.912 8 _._ 18 _−_ [+0] 0 _[.]_ _._ [05] 05 31 _._ 53 _−_ [+1] 2 _[.]_ _._ [91] 51 1 _._ 84 _−_ [+0] 0 _[.]_ _._ [17] 14 1.56
HerBS-27 4.509 8 _._ 84 _−_ [+0] 0 _[.]_ _._ [04] 04 40 _._ 87 _−_ [+2] 2 _[.]_ _._ [16] 49 1 _._ 46 _−_ [+0] 0 _[.]_ _._ [13] 12 3.56
HerBS-28 3.925 9 _._ 20 _−_ [+0] 0 _[.]_ _._ [04] 04 37 _._ 69 _−_ [+2] 1 _[.]_ _._ [01] 99 1 _._ 57 _−_ [+0] 0 _[.]_ _._ [13] 12 1.70
HerBS-36 3.095 9 _._ 20 _−_ [+0] 0 _[.]_ _._ [04] 04 36 _._ 81 _−_ [+2] 2 _[.]_ _._ [29] 13 1 _._ 50 _−_ [+0] 0 _[.]_ _._ [12] 11 1.80
HerBS-39 3.229 8 _._ 93 _−_ [+0] 0 _[.]_ _._ [04] 04 37 _._ 62 _−_ [+2] 2 _[.]_ _._ [30] 29 1 _._ 75 _−_ [+0] 0 _[.]_ _._ [13] 12 1.06
HerBS-41 4.098 9 _._ 44 _−_ [+0] 0 _[.]_ _._ [06] 07 44 _._ 29 _−_ [+3] 3 _[.]_ _._ [95] 40 1 _._ 31 _−_ [+0] 0 _[.]_ _._ [20] 20 8.36
HerBS-42 3.307 9 _._ 01 _−_ [+0] 0 _[.]_ _._ [04] 04 37 _._ 83 _−_ [+2] 2 _[.]_ _._ [24] 00 1 _._ 82 _−_ [+0] 0 _[.]_ _._ [11] 11 1.99
HerBS-49 2.727 8 _._ 48 _−_ [+0] 0 _[.]_ _._ [05] 05 28 _._ 93 _−_ [+2] 2 _[.]_ _._ [14] 08 2 _._ 06 _−_ [+0] 0 _[.]_ _._ [19] 18 14.77
HerBS-55 2.656 8 _._ 26 _−_ [+0] 0 _[.]_ _._ [04] 04 30 _._ 86 _−_ [+2] 2 _[.]_ _._ [17] 09 2 _._ 22 _−_ [+0] 0 _[.]_ _._ [16] 15 7.48
HerBS-57 3.265 8 _._ 40 _−_ [+0] 0 _[.]_ _._ [05] 04 36 _._ 51 _−_ [+2] 2 _[.]_ _._ [04] 33 1 _._ 89 _−_ [+0] 0 _[.]_ _._ [13] 11 6.40
HerBS-60 3.261 8 _._ 66 _−_ [+0] 0 _[.]_ _._ [04] 04 32 _._ 10 _−_ [+2] 2 _[.]_ _._ [16] 58 1 _._ 97 _−_ [+0] 0 _[.]_ _._ [17] 14 1.09
HerBS-68 2.719 8 _._ 44 _−_ [+0] 0 _[.]_ _._ [04] 04 34 _._ 16 _−_ [+2] 1 _[.]_ _._ [22] 99 2 _._ 01 _−_ [+0] 0 _[.]_ _._ [14] 13 2.97
HerBS-73 3.026 9 _._ 04 _−_ [+0] 0 _[.]_ _._ [05] 04 34 _._ 99 _−_ [+2] 3 _[.]_ _._ [41] 22 1 _._ 93 _−_ [+0] 0 _[.]_ _._ [18] 13 3.95
HerBS-86 2.564 8 _._ 88 _−_ [+0] 0 _[.]_ _._ [06] 05 26 _._ 11 _−_ [+2] 2 _[.]_ _._ [13] 72 2 _._ 32 _−_ [+0] 0 _[.]_ _._ [22] 17 3.73
HerBS-93 2.400 9 _._ 07 _−_ [+0] 0 _[.]_ _._ [06] 05 24 _._ 88 _−_ [+1] 2 _[.]_ _._ [79] 12 2 _._ 50 _−_ [+0] 0 _[.]_ _._ [18] 15 6.77
HerBS-103 2.942 8 _._ 75 _−_ [+0] 0 _[.]_ _._ [04] 04 38 _._ 66 _−_ [+2] 2 _[.]_ _._ [67] 46 1 _._ 85 _−_ [+0] 0 _[.]_ _._ [13] 13 2.53
HerBS-111 2.371 8 _._ 79 _−_ [+0] 0 _[.]_ _._ [05] 05 28 _._ 77 _−_ [+1] 1 _[.]_ _._ [92] 75 2 _._ 24 _−_ [+0] 0 _[.]_ _._ [14] 14 2.00
HerBS-132 2.473 8 _._ 64 _−_ [+0] 0 _[.]_ _._ [05] 05 26 _._ 67 _−_ [+2] 2 _[.]_ _._ [04] 06 2 _._ 52 _−_ [+0] 0 _[.]_ _._ [19] 17 1.69
HerBS-145 2.730 9 _._ 04 _−_ [+0] 0 _[.]_ _._ [05] 06 28 _._ 69 _−_ [+2] 2 _[.]_ _._ [79] 87 2 _._ 24 _−_ [+0] 0 _[.]_ _._ [29] 24 7.24
HerBS-160 3.955 8 _._ 81 _−_ [+0] 0 _[.]_ _._ [04] 04 39 _._ 28 _−_ [+2] 2 _[.]_ _._ [46] 36 1 _._ 50 _−_ [+0] 0 _[.]_ _._ [13] 13 0.52
HerBS-182 2.227 9 _._ 44 _−_ [+0] 0 _[.]_ _._ [05] 05 26 _._ 41 _−_ [+1] 1 _[.]_ _._ [84] 77 2 _._ 29 _−_ [+0] 0 _[.]_ _._ [16] 15 0.39
HerBS-184 2.507 8 _._ 80 _−_ [+0] 0 _[.]_ _._ [04] 05 33 _._ 57 _−_ [+2] 2 _[.]_ _._ [73] 37 1 _._ 71 _−_ [+0] 0 _[.]_ _._ [15] 14 4.62
HerBS-200 2.151 9 _._ 76 _−_ [+0] 0 _[.]_ _._ [05] 05 30 _._ 84 _−_ [+2] 2 _[.]_ _._ [68] 21 2 _._ 04 _−_ [+0] 0 _[.]_ _._ [15] 15 5.58
HerBS-207 1.569 8 _._ 99 _−_ [+0] 0 _[.]_ _._ [05] 05 21 _._ 10 _−_ [+1] 1 _[.]_ _._ [39] 30 2 _._ 36 _−_ [+0] 0 _[.]_ _._ [15] 15 3.43
HerBS-208 2.481 9 _._ 45 _−_ [+0] 0 _[.]_ _._ [06] 05 27 _._ 87 _−_ [+2] 2 _[.]_ _._ [11] 08 2 _._ 07 _−_ [+0] 0 _[.]_ _._ [18] 16 0.96


MNRAS **000**, 1–15 (2023)

16 _B. A._ _Ward_ _et_ _al._





log( _L_ IR [ _L_ _⊙_ ])


log( _L_ IR [ _L_ _⊙_ ])



log( _M_ dust [ _M_ _⊙_ ])


log( _M_ dust [ _M_ _⊙_ ])



_T_ dust [K]


_T_ dust [K]



_β_


_β_



_λ_ peak [ _µ_ m]


_λ_ peak [ _µ_ m]



**Figure** **C1.** The posterior distributions for SPT 0002-52 and HerBS-11 obtained from FIR SED fitting with an optically thin dust model
(shaded contours), and two general opacity models, one with _λ_ 1 = 100 _µ_ m (solid contours), the other with _λ_ 1 = 200 _µ_ m (dashed contours).
Parameters shown are the dust mass _M_ dust, the dust temperature _T_ dust, the dust emissivity index _β_, IR luminosity _L_ IR and the peak
wavelength _λ_ peak .


**APPENDIX** **C:** **EXAMPLE** **POSTERIOR** **DISTRIBUTIONS**


MNRAS **000**, 1–15 (2023)


</paper>

## Items to check

```json
[
 {
  "path": "data.other_facilities[0].provided.evidence[1]",
  "value": "Photometry at 100, 160, 250, 350, and 500 um",
  "failed_quote": "For 65 sources there are additional constraints at 100 and 160 \\mu m from Herschel-PACS."
 },
 {
  "path": "data.other_facilities[1].provided.evidence[1]",
  "value": "850 um photometry for HerBS sources",
  "failed_quote": "Calibration errors are added in quadrature with the flux density uncertainties assuming absolute calibrations of 7 per cent (Herschel-PACS), 5.5 per cent (Herschel-SPIRE), 5 per cent (SCUBA-2), 12 per cent (APEX-LABOCA), 7 per cent (SPT) and 10 per cent (ALMA)."
 },
 {
  "path": "processing.calibration.flux_scale_uncertainty.evidence[0]",
  "value": "10% (ALMA), 7% (Herschel-PACS), 5.5% (Herschel-SPIRE), 5% (SCUBA-2), 12% (APEX-LABOCA), 7% (SPT)",
  "failed_quote": "Calibration errors are added in quadrature with the flux density uncertainties assuming absolute calibrations of 7 per cent (Herschel-PACS), 5.5 per cent (Herschel-SPIRE), 5 per cent (SCUBA-2), 12 per cent (APEX-LABOCA), 7 per cent (SPT) and 10 per cent (ALMA)."
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "CMB dust heating and background contrast correction formalism",
  "failed_quote": "Including the effects of the CMB on the observed dust continuum using the procedure outlined in da Cunha et al. (2013), the CMB-adjusted MBB model is now given by:"
 },
 {
  "path": "analysis_steps[1].assumptions[2].evidence[0]",
  "value": "Calibration errors added in quadrature: 7% (PACS), 5.5% (SPIRE), 5% (SCUBA-2), 12% (LABOCA), 7% (SPT), 10% (ALMA)",
  "failed_quote": "Calibration errors are added in quadrature with the flux density uncertainties assuming absolute calibrations of 7 per cent (Herschel-PACS), 5.5 per cent (Herschel-SPIRE), 5 per cent (SCUBA-2), 12 per cent (APEX-LABOCA), 7 per cent (SPT) and 10 per cent (ALMA)."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Generate mock SEDs from the optically-thin model with parameters drawn from uniform distributions, add normal observational errors, apply survey flux detection limits (>80 mJy at 500 \\mu m for HerBS; >25 mJy at 870 \\mu m for SPT), and refit with the same SED fitting routine.",
  "failed_quote": "A catalogue of models were produced with dust parameters randomly drawn from a uniform distribution between the lower and upper bounds in Table 2, chosen to reflect the width of the posterior distributions for the parameters derived for the real sources."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "SPT stacked median T_{dust} (optically thin) = 32.07 K",
  "failed_quote": "T_{dust} [K] 32.07^{+8.43}_{-8.44} 40.77^{+10.90}_{-11.77} 55.63^{+11.28}_{-9.20}"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "SPT stacked median T_{dust} (\\lambda_1 = 100 um) = 40.77 K",
  "failed_quote": "T_{dust} [K] 32.07^{+8.43}_{-8.44} 40.77^{+10.90}_{-11.77} 55.63^{+11.28}_{-9.20}"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "SPT stacked median T_{dust} (\\lambda_1 = 200 um) = 55.63 K",
  "failed_quote": "T_{dust} [K] 32.07^{+8.43}_{-8.44} 40.77^{+10.90}_{-11.77} 55.63^{+11.28}_{-9.20}"
 },
 {
  "path": "results_numeric[14].evidence[0]",
  "value": "HerBS stacked median \\lambda_{peak} (optically thin) = 90.03 um",
  "failed_quote": "\\lambda_{peak} [\\mu m] 90.03^{+12.28}_{-9.70} 90.36^{+13.46}_{-9.42} 89.96^{+14.46}_{-9.92}"
 },
 {
  "path": "results_numeric[23].evidence[0]",
  "value": "Simulation parameter recovery RMSE for \\beta (SPT and HerBS) = 0.13 (SPT), 0.09 (HerBS) dimensionless",
  "failed_quote": "The RMSE indicate that our fitting recovers the input dust masses to 0.05 dex and 0.03 dex, the dust temperatures to 1.63 K and 1.61 K and \\beta to 0.13 and 0.09 of the input values for SPT and HerBS galaxies, respectively."
 },
 {
  "path": "results_numeric[24].evidence[0]",
  "value": "Simulation parameter recovery RMSE for T_{dust} (SPT and HerBS) = 1.63 (SPT), 1.61 (HerBS) K",
  "failed_quote": "The RMSE indicate that our fitting recovers the input dust masses to 0.05 dex and 0.03 dex, the dust temperatures to 1.63 K and 1.61 K and \\beta to 0.13 and 0.09 of the input values for SPT and HerBS galaxies, respectively."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Interferometric flux loss at 3 mm ('zero baseline problem') was considered and rejected as the primary explanation for extreme \\beta \\simeq 3 values in SPT galaxies because 60-80% of the 3-mm flux would need to be missed.",
  "failed_quote": "These flux densities were measured from ALMA images, so it is possible that they are too low because of the possibility – as with all interferometers – that some extended flux has been missed (the ‘zero baseline problem’)."
 }
]
```
