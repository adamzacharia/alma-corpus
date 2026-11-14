# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.496..138B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–15 (2020) Preprint 8 September 2020 Compiled using MNRAS L [A] TEX style file v3.0

## **VLA and ALMA observations of the lensed radio-quiet** quasar SDSS J0924+0219: a molecular structure in a 3 µ Jy **radio source**


### Shruti Badole [1][⋆], Neal Jackson [1], Philippa Hartley [1][,][2], Dominique Sluse [3], Hannah Stacey [4][,][5][,][6], H´ector Vives-Arias [7][,][8]

1 _Jodrell_ _Bank_ _Centre_ _for_ _Astrophysics,_ _Department_ _of_ _Physics_ _&_ _Astronomy,_ _University_ _of_ _Manchester,_ _Alan_ _Turing_ _Building,_
_Oxford_ _Road,_ _Manchester_ _M13_ _9PL,_ _UK_
2 _Square_ _Kilometre_ _Array_ _Organisation,_ _Macclesfield,_ _Cheshire_ _SK11_ _9DL,_ _UK_
3 _STAR_ _Institute,_ _Quartier_ _Agora_ _-_ _All´ee_ _du_ _six_ _Aoˆut,_ _19c_ _B-4000_ _Li`ege,_ _Belgium_
4 _ASTRON,_ _Netherlands_ _Institute_ _for_ _Radio_ _Astronomy,_ _Oude_ _Hoogeveensedijk_ _4,_ _7991_ _PD,_ _Dwingeloo,_ _The_ _Netherlands_
5 _Kapteyn_ _Astronomical_ _Institute,_ _PO_ _Box_ _800,_ _9700_ _AV_ _Groningen,_ _The_ _Netherlands_
6 _Max_ _Planck_ _Institute_ _for_ _Astrophysics,_ _Karl-Schwarzschild_ _Str._ _1,_ _D-85748_ _Garching_ _bei_ _M¨unchen,_ _Germany_
7 _Instituto_ _de_ _Astrof´ısica_ _de_ _Canarias,_ _V´ıa_ _L´actea,_ _s/n,_ _E-38205_ _La_ _Laguna,_ _Tenerife,_ _Spain_
8 _Departmento_ _de_ _Astrof´ısica,_ _Universidad_ _de_ _La_ _Laguna,_ _E-38205,_ _La_ _Laguna,_ _Tenerife,_ _Spain_


Accepted 2020 May 21. Received 2020 May 21; in original form 2019 October 23


**ABSTRACT**
We present Karl G. Jansky Very Large Array (VLA) and Atacama Large Millimetre
Array (ALMA) observations of SDSS J0924+0219, a _z_ =1.524 radio-quiet lensed quasar
with an intrinsic radio flux density of about 3 µJy. The four lensed images are clearly
detected in the radio continuum and the CO(5-4) line, whose centroid is at _z_ = 1.5254±
0.0001, with a marginal detection in the submillimetre continuum. The molecular gas
displays ordered motion, in a structure approximately 1–2.5 kpc in physical extent,
with typical velocities of 50-100 km s [−][1] . Our results are consistent with the radio
emission being emitted from the same region, but not with a point source of radio
emission. SDSS J0924+0219 shows an extreme anomaly in the flux ratios of the two
merging images in the optical continuum and broad emission lines, suggesting the
influence of microlensing by stars in the lensing galaxy. We find the flux ratio in the
radio, submillimetre continuum and CO lines to be slightly greater than 1 but much less
than that in the optical, which can be reproduced with a smooth galaxy mass model
and an extended source. Our results, supported by a microlensing simulation, suggest
that the most likely explanation for the optical flux anomaly is indeed microlensing.


**Key** **words:** gravitational lensing: strong – galaxies:individual:SDSS J0924+0219 –
galaxies:star formation



**1** **INTRODUCTION**


In a strong gravitational lensing system, the light from a background source is deflected due to the gravitational potential of
a foreground galaxy or galaxy cluster, resulting in multiple images of the background source. The position and brightness of
the lensed images contain information about the structure of the
source, together with the mass distribution of the lensing galaxy
(Treu 2010). Lensing galaxies or galaxy clusters also magnify the
sources by factors of typically 10–20, allowing us to study lensed


⋆ E-mail: shruti.badole@postgrad.manchester.ac.uk


© 2020 The Authors



sources which would otherwise be unobservably faint (Zheng et al.
2012; Yuan et al. 2012; Atek et al. 2015).


The use of effective increases in resolution and/or sensitivity is particularly interesting in sources which contain a quasar.
About 10% of quasars are radio loud, with the radio synchrotron
emission being generated by jets ejected from close to the central
black hole. The remainder generally have weak radio emission,
which may be a result of jet activity similar to that in radio loud
quasars but on a smaller scale (Zakamska et al. 2016; Herrera Ruiz
et al. 2016; White et al. 2017; Hartley et al. 2019; Jarvis et al.
2019), or due to processes associated with star-formation (Condon
et al. 2013; Bonzini et al. 2015; Padovani et al. 2017; Stacey et al.
2019). One way to investigate this question is to study the molecular gas component associated with star-formation processes; this

2 _Badole_ _et_ _al._


can be detected using molecular lines in the sub-millimetre part of
the spectrum, and its morphology and extent compared with the
radio continuum. The question of the interaction between AGN
and star-forming components is important because it has been
suggested for some time (e.g. Croton et al. 2006) that AGN are
responsible for regulating star-formation in galaxies, periodically
clearing out gas in order to stop star formation. More complex
regulatory interactions have also been proposed (Maiolino et al.
2017).
The study of molecular gas in lensed submillimetre galaxies
has a long history (for recent examples see e.g. Hezaveh et al.
2013b; Rybak et al. 2015; Aravena et al. 2016; Yang et al. 2017;
Geach et al. 2018). Molecular gas reservoirs have also been found
in quasars (Riechers et al. 2009a; Tuan-Anh et al. 2017; Paraficz
et al. 2018). We can use lens models to correct for the lensing
magnification and derive the intrinsic CO luminosity in these objects, and also estimate the molecular gas mass if we assume the
quantity α CO, which relates CO to overall molecular gas mass, is
similar to more directly accessible objects ( Venturini & Solomon
2003; Riechers et al. 2009a; Riechers et al. 2011; Deane et al. 2013;
Tuan-Anh et al. 2017). More recently, detailed imaging together
with lens inversion has been used to calculate values for α CO and
reconstruct lensed sources in more detail (Paraficz et al. 2018;
Spingola et al. 2019).
Imaging of radio structures in lensed radio-quiet quasars has
also been recently developed, with a number of detections of
spatially-resolved radio emission (Wucknitz & Volino 2008; Jackson 2011; Jackson et al. 2015; Hartley et al. 2019). In cases such as
RXJ 1131−1231, high resolution radio observations resolve out the
emission, suggesting emission from an extended disk (Wucknitz
& Volino 2008); in others, variability or directly imaged core-jet
structures with VLBI suggest AGN origin as in HS 0810+2554
(Hartley et al. 2019). The latter is a surprising result because
the object lies within the scatter of the far-infrared (FIR) – radio
correlation resulting from the comparison of lensed radio and _Her-_
_schel_ far-infrared luminosities in a large sample of lensed quasars
(Stacey et al. 2018), where both radio and FIR emission are expected to be produced by the same, star-formation, mechanism.
There is thus a strong motivation to investigate in detail both
radio and sub-millimetre emission in the same objects, to derive
clues on the relation between radio-emitting components and the
molecular gas.
For smooth lens potentials, a point source near a fold or
cusp caustic should yield well-defined flux ratios. For fold systems such as SDSS J0924+0219, the two close images of a point
source should have the same brightness; deviations from this may
indicate millilensing by clumped matter distributions in the lensing galaxy close to the line of sight to one or both of the images
(Mao & Schneider 1998; Fassnacht et al. 1998; Metcalf & Madau
2001; Metcalf & Zhao 2002; Chiba 2002; Saha et al. 2007; Kratzer
et al. 2011; Dalal & Kochanek 2002). The mass scale to which
these flux anomalies are sensitive can be as small as 10 [6] M ⊙,
sufficient to distinguish between CDM and WDM (Miranda &
Macci`o 2007; Gilman et al. 2019). At larger scales, gravitational
imaging of optically-bright lens systems with extended sources
has been used to more directly detect the influence of ∼ 10 [9] M ⊙
substructure (Vegetti & Koopmans 2009; Vegetti et al. 2010a,b;
Hezaveh et al. 2016).
Studies (eg. Xu et al. 2012) also attribute the flux anomaly
to structures present along the line of sight to the primary lens
and other factors such as propagation effects (Xu et al. 2015). It
has been found that anomalies could also be caused by extended
sources (Amara et al. 2006; Jackson et al. 2015), or edge-on disc
components in the lensing galaxy (M¨oller et al. 2003; Hsueh et al.
2016).
In addition to millilensing effects, optical sources can also be
prone to producing measurable flux variation in the lensed images
due to microlensing by stars in the lensing galaxy (Chang & Refs


dal 1979). Anomalous flux ratios due to microlensing by stars in
the lensing galaxy have been found in many systems (e.g. Irwin
et al. 1989; Witt et al. 1995; Burud et al. 2002; Vuissoz et al.
2007; Poindexter et al. 2008; Vuissoz et al. 2008); typically, monitoring of lensed quasars over the timerange of years is essential
to identify the effects of microlensing.
The sample of strong lenses is currently dominated by those
lenses where the source is an optically selected quasar, so only
a small (≃10%) subset of these samples have been used for substructure studies. Measurements at longer wavelengths, where the
continuum source size is ≫ 1µas and not subject to microlensing,
are important (Chiba et al. 2005; Fadely & Keeton 2011, 2012
;Hezaveh et al. 2013a; Jackson et al. 2015; Hartley et al. 2019) as
are studies of the extended optical narrow emission lines (Moustakas & Metcalf 2003; Sugai et al. 2007; Nierenberg et al. 2017,
2020).


**1.1** **The** **quasar** **SDSS** **J0924+0219**


SDSS J0924+0219 was discovered by Inada et al. (2003) as part
of the Sloan Digital Sky Survey Quasar Lens Search (SQLS) and
consists of a radio-quiet quasar at z = 1.524 quadruply imaged by
an early-type galaxy at z = 0.394 (Eigenbrod et al. 2006). It was
selected for observation due to an unusually large flux anomaly: it
is a fold-configuration lens, but the pair of merging images, A and
D in Fig. 1, has a brightness ratio in the optical waveband of 12:1
(Inada et al. 2003). Spectroscopy using the Hubble Space Telescope (Keeton et al. 2006) revealed the presence of flux anomaly
in the broad emission line flux ratios, with the continuum and
broad line emission flux ratios in the merging images being 19
and 10, respectively. This analysis also suggested the presence of
microlensing in the lens system (see also Morgan et al. 2006). The
microlensing duration expected for the lens in this system is 0.39
years and the duration averaged over a sample of 87 lenses is 7.3
months (Mosquera & Kochanek 2011). However, the anomaly in
SDSS J0924+0219 has persisted for 15 years now (Faure et al.
2011; MacLeod et al. 2015), which is an unusual timescale for
microlensing to occur (Peeples et al. 2004 and Morgan et al. 2006
predicted brightening of the demagnified image over the timescale
of roughly a decade). Such an extreme flux anomaly over such
a long period of time [1] suggests the possibility that it could be
driven by not only microlensing but also other factors such as
millilensing by substructure.
We observed SDSS J0924+0219 in order to investigate the
properties of the radio and molecular gas reservoirs in the source,
and investigate the causes of the flux anomaly further. This paper is divided into four sections. Section 2 discusses the Karl G.
Jansky Very Large Array (VLA) and Atacama Large Millimetre Array (ALMA) observations in the radio and submillimetre
wavebands, and the initial data reduction carried out using the
calibration pipelines of the observatories. Section 3 discusses the
data analysis in the image plane and the u − v plane, followed by
Section 4 which discusses the nature of the radio source and the

flux anomaly in SDSS J0924+0219. Where necessary we assume
a flat Universe with H 0 = 68.3 km s [−][1] Mpc [−][1] and Ω m = 0.3; for
the source this gives a luminosity distance D L = 11400 Mpc and
an angular size distance D A = 1790 Mpc. 1 mas corresponds to
8.6 pc at the redshift of this source.


1 The more recent photometry by Gaia Data Release 2 (Gaia
Collaboration 2018) shows persistence of the flux ratio anomaly.


MNRAS **000**, 1–15 (2020)

_SDSS_ _J0924+0219:_ _VLA_ _and_ _ALMA_ _observations_ 3


**Table** **1.** Summary of observations of SDSS J0924+0219 on the
VLA


**Parameter** **Values**


Proposal code AJ413
Observation dates 2018 Apr. 4, 6-8
Configuration A
Central Frequency 5.5 GHz
Bandwidth 2 GHz

Flux Density 90 ± 9.1 µJy


**2** **OBSERVATIONS** **AND** **DATA** **PROCESSING**


**2.1** **VLA** **observations**



SDSS J0924+0219 was observed using the VLA in the A configuration, providing a maximum baseline of 36 km and resolution
of 350 mas at 5 GHz. The observation was made under proposal
code AJ413 (PI Jackson) in the C-band (4.488–6.512 GHz) with a
total bandwidth of 2 GHz using 16 IFs of 128 MHz each. 12 hours
of observations were divided into four blocks of three hours each,
which were observed on 2018 April 4, 6, 7 and 8. The observation
log is summarised in Table 1.
J0914+0245 and J1331+3030 (3C286) were used as the phase
and the flux calibrators respectively. Each of the 3-hour blocks
contained 2h 10m of on-source observation and 32 minutes on the

phase calibrator; the phase calibrator was observed for 2 minutes in each 10-minute cycle, followed by 8 minutes of the target
observation.

The VLA Calibration Pipeline, using the software package casa (Common Astronomy Software Application [2] ; Mcmullin
et al. 2007) was run on each of the four measurement sets. The
pipeline applies basic radio frequency interference (RFI) flagging
to the data, derives the initial and final delay, bandpass, and
gain/phase calibrations, determines the overall flux scale of the
data using the flux calibrator (J1331+3030 in this case) and
also creates images of the calibrators. We combined the calibrated measurement sets generated by the pipeline and imaged
the lensed source using the clean algorithm (H¨ogbom 1974)
implemented in casa with natural weighting. The final map is
shown in Fig. 1. The overall off-source noise level in the map is
1.3µJy/beam, which is in agreement with the expected noise level
of 1.1-1.3µJy/beam with natural weighting. The peak signal level
of the map is about eight times the noise level.


**2.2** **ALMA** **observations**


ALMA observations (Table 2) were performed on 2018 December 19 (project code 2018.1.01447, PI Jackson) using 45 antennas
of the 12-m array, centred on the source SDSS J0924+0219. 5
minutes of on-source integration time were obtained, with observations being performed on the nearby sources J0854+2006
and J0930+0034 for amplitude and phase calibration, respectively. The observations were reduced by the standard ALMA
pipeline system using the casa data analysis package. Observations were performed in four spectral windows close to frequencies
of 226, 228, 242 and 244 GHz; the second window was expected
to contain the redshifted CO(5-4) line which has a rest frequency
of 576.36 GHz and therefore an expected observed frequency of
228.35 GHz given the published redshift of 1.524. Each spectral
window was divided into 128 15.6-MHz channels. The array configuration used gave a resolution of approximately 0 [′′] . 8 with natu

2 Distributed by the National Radio Astronomy Observatory;
`[http://casa.nrao.edu](http://casa.nrao.edu)` .


MNRAS **000**, 1–15 (2020)



**Figure** **1.** Map of SDSS J0924+0219 from the Very Large Array. The map is the coadded version of all four 3-hours observing
chunks. All four images of the lensed source are clearly detected,
with a measured map noise level of 1.3 µJy/beam. The flux density of the lensing system in the map is 90 ± 9.1 µJy, assuming a
10% flux calibration accuracy. The beam size is 0 [′′] . 489 × 0 [′′] . 395
with position angle of -28.43 [◦] .


**Table** **2.** Summary of observations of SDSS J0924+0219 on
ALMA


**Parameter** **Values**


Project code 2018.1.01447.S
Observation date 2018 Dec. 19

Maximum Baseline Length 500 m
Spectral Windows Frequencies 226, 228, 242, 244 GHz
Total Bandwidth 8 GHz
CO(5-4) Peak Flux Density 3.9 mJy/beam
CO(5-4) FWHM 200.02 ± 6.57 km/s
CO(5-4) Luminosity, µL CO [′] 3.16 × 10 [10] K km s [−][1] pc [2]


ral weighting; the calibrated data were also re-imaged with Briggs
weighting (with a default robustness parameter of 0.0), giving a
higher resolution of 0 [′′] . 68 × 0 [′′] . 56 with PA = 69.77 [◦], with only
marginal increase in noise level. A VLA image was also created,
for comparison purposes, with a beam convolved to match the
Briggs-weighted ALMA image.
In this very short observation, we achieve noise levels of
0.2 mJy/beam in each spectral window, or 0.1 mJy/beam overall. We detect the submillimetre continuum at a level of approximately 2 mJy within an area encompassing all four lensed images,
but with the signal-to-noise available it is not possible to make
sensible measurements of the individual component fluxes. Fig. 2
shows the map of the continuum obtained by cleaning the line-free
spectral windows in the ALMA data. The CO(5-4) line is clearly
detected in all four components, and the integrated line flux density, with the continuum subtracted, is also shown in Fig. 2 (left).
The peak signal to noise ratio of the CO(5-4) line map is 19.5.
Fig. 3 shows the same map in greyscale with the radio contours
overlaid on top; there is a clear similarity between the two maps.
A more quantitative comparison of the two maps can be seen in
Fig. 4, which shows the CO line emission map divided by the
radio map (convolved down to the ALMA beam). The radio and

4 _Badole_ _et_ _al._


CO emission in the A and D regions appear indistinguishable,
suggesting that the CO and the radio emission originate at least
in part from the same region. Velocity-resolved maps of the CO
line are shown in Fig. 5, and show clear velocity structure across
the source, with parts of the source moving at different velocities
being in different places in the source plane and thus producing
different image configurations (also see Figure 6 for the integrated
CO(5-4) line spectrum). The first-moment map (with the continuum subtracted from the CO line emission) showing the velocity
structure across the lensed source and the second-moment map
showing the velocity dispersion can be seen in Fig. 7.


**3** **ANALYSIS** **AND** **RESULTS**


In the following sections we describe the analysis of the ALMA
CO(5-4) line image, the submillimetre continuum, and the VLA
image. Our normal procedure is to obtain an initial model in the
image plane, directly by fitting to the components of the image or
using a lens model to fit a lensed source. This analysis is then used
as a starting point for analysis of the data in the u − v (Fourier)
plane. This analysis is done either by fitting the image as separate
components using uvmultifit (Mart´ı-Vidal et al. 2014) or using a
lens model and the visilens package (Hezaveh et al. 2013b; Spilker
et al. 2016) with a parametrised lensed source. We describe both
phases of this process, firstly because the initial starting model
is typically necessary to get good convergence in the u − v fitting
part of the process, and because it allows easy visual assessment
of the fits.


**3.1** **ALMA** **observations:** **the** **molecular** **disk** **and**

**submillimetre** **continuum**


_3.1.1_ _The_ _integrated_ _line_ _emission_


In the image plane, we began by fitting four elliptical Gaussians at
the positions of the images in the CO(5-4) line map, an approach
that makes no assumption about the detail of the lens model, in
particular, its substructure content. The fit used 10 image parameters, namely the peak flux densities of the four components, the
FWHMs and the axis ratios of images A and B and two overall
positional offsets in the x and y directions respectively to allow
for astrometric differences in the radio and optical images. The
FWHMs and axis ratios of the merging images (A and D) are assumed equal, as are the FWHMs and axis ratios for images B and
C, and the fitted components were constrained to have the major axes tangential to the centre of the lensing galaxy (100.87 [◦],
77.21 [◦], 12.99 [◦] and 151.07 [◦] for A, B, C and D respectively; derived from positions of the images in Inada et al. (2003). Since
the lensed images are spatially resolved, the FWHMs of the images were constrained to be greater than the major axis of the
dirty beam. The 10-parameter optimization yielded a minimum
χ red [2] [=] [1][.][5][.] [The] [resulting] [lensed] [image] [and] [residual] [for] [this] [best]
fit is shown in Fig. 8 (bottom right, Fig. (b)). Table 3 (values in
brackets) shows the parameters of the best fit model. The A/D
flux ratio for this model was found to be 1.07. The modelled images B and C are clearly wider than would be expected in any
plausible gravitational lens model.

In addition, we performed a gravitational lens modelling [3]

using the Singular Isothermal Ellipsoid (SIE) model developed
by Eigenbrod et al. (2006) for the lensing galaxy. Allowing the
source to have a Gaussian profile, the galaxy position and the
source parameters were optimized using the difference between
the data and the lensed images convolved with the point spread


3 Throughout this study, we have used the lens modelling code
developed by Neal Jackson.



function. An extra parameter, f AD, was introduced, that can vary
between 0 and 1 and which multiplies the flux of the component
D, while keeping the flux of A the same. This parameter quantifies
the anomaly in the flux ratio of A and D due to substructure effects, with a value of 1 indicating the situation of no flux anomaly
present due to CDM substructure. Due to the relatively low signal
to noise ratio of the data, we did not attempt to pixelize the source
and use semi-linear source reconstruction (Warren & Dye 2003).
The best-fit lensed image, source structure and the corresponding
residual map obtained from the optimization are shown in Figure
8 (top). The fit has a χ red [2] [=][ 1][.][85][ and is generally satisfactory apart]
from some difference in the structure of image B. The parameters for this model are shown in Table 4 (values in brackets). The
best fit position of the lensing galaxy from the optimization corresponds to RA = 09h 24m 55.813s and Dec = 02 [◦] 19 [′] 24 [′′] . 454 and
has been used for all subsequent image-plane analysis, wherever
required. The value of f AD for the best fit is 1. We also attempted
to fit a lens model assuming a point source, giving unresolved
point images [4] ; the resultant residual shows an over-subtraction of
flux in the image positions and under-subtraction in the nearby
areas (see Fig. 8, bottom left), demonstrating incompatibility of
a point source with our observation. The observation that f AD = 1
implies that the SIE model we used clearly reproduces the main
features of the data and is compatible with an extended source,
together with no requirement for additional perturbations due to
millilensing by substructure.

Given a starting model derived from the image plane, we now
derived quantities directly from the u − v data. We first fitted four
elliptical gaussians for the integrated CO line using uvmultifit
(Mart´ı-Vidal et al. 2014), on the continuum subtracted visibility
data of the CO line. We used the positions of the four images
from Inada et al. (2003) and kept them fixed, optimising for the
flux densities, widths and axes ratios of the images. We kept the
axes ratios of A and D (and likewise B and C) equal, as well
as their FWHMs. The parameters corresponding to the best fit
from the optimization can be found in Table 3. The flux ratio
A/D obtained from this fitting was found to be 1.58 ± 0.15, which
is slightly bigger than the corresponding flux ratio from the image
plane analysis.
We also fitted the u−v data with a lens model using visilens.
All the lens galaxy parameters, except the position and mass of
the lens galaxy, were fixed assuming the SIE lens model by Eigenbrod et al. (2006). We optimised for all the source parameters
and the lens galaxy mass and position. Figure 9 shows the best
fit model and the residual map. The parameters for the best fit
can be found in Table 4. The source FWHM using the u − v plane
analysis is 0 [′′] . 081±0 [′′] . 008, slightly larger than the FWHM found in
the image plane analysis. Figure 10 shows the distribution of the
different parameters resulting from this lens model fitting.

We now proceed to calculate the luminosity of the CO(5-4)
emission. Following Solomon & Vanden Bout (2005), we get a
CO line (lensed) luminosity of µL [′] CO [=][ 3][.][16] [×] [10] [10] [K km s] [−][1] [pc] [2] [. The]
lens model fitting of the u − v data using visilens demonstrates a
source magnification of 23.5, making the intrinsic CO line luminosity equal to L [′] CO [≃] [1][.][34][ ×][ 10] [9] [K km s] [−][1] [pc] [2] [.] [Solomon] [&] [Vanden]
Bout (2005) use the formula M dyn sin [2] (i) = 233.5R∆V [2] to calculate
the dynamical mass, where R is the radius of the molecular disk
and ∆V is the FWHM of the CO line. Using our value of size
of the integrated CO line emission source of 81 ± 8 mas (Table
4), we get R = 348 ± 34 pc, approximating R to be equal to half
of size of the disk. The FWHM of the line is 200 ± 7 km/s, thus
giving a dynamical mass M dyn = 3.25 × 10 [9] cosec [2] (i)M ⊙ where i is
the inclination angle of the disk.


4 The fit was performed using jmfit, part of the Astronomical
Image Processing System, aips, which is distributed by the US
National Radio observatory, `[http://www.aips.nrao.edu](http://www.aips.nrao.edu)` .


MNRAS **000**, 1–15 (2020)

_SDSS_ _J0924+0219:_ _VLA_ _and_ _ALMA_ _observations_ 5


**Figure** **2.** Left: The CO(5-4) integrated line emission with the continuum subtracted. This image was obtained using CLEAN in CASA
with Briggs weighting, giving a resolution of 0 [′′] . 68×0 [′′] . 56 in PA 69.77 [◦] . The noise level in this map is 0.2 mJy/beam. The flux density is
21.99 ± 2.21 mJy, assuming a 10% flux calibration accuracy. Right: Map of the submillimetre continuum obtained by cleaning the line-free
spectral windows of the ALMA data with Briggs weighting. The flux density is 2.3 ± 0.2 mJy, assuming a 10% flux calibration accuracy.


**Figure** **3.** ALMA image (greyscale) of the integrated CO(5-4) emission with VLA radio contours overplotted. The greyscale runs from
−1.0 to 4 mJy/beam, and the radio contours are given at (2, 4, 6, 8, 16, 32, 64, 128) times the rms noise level. The radio image has been
convolved down to the ALMA beam.


MNRAS **000**, 1–15 (2020)

6 _Badole_ _et_ _al._


**Figure** **4.** Left: Map of the CO line emission divided by the VLA map convolved down to the ALMA beam. The x and y values are in
arcseconds. Right: Map showing the ALMA image (normalised) subtracted by the VLA image (normalised). The ALMA and the VLA
images (convolved to the ALMA beam) were, each, normalised by dividing each of them by the total flux density in the images, as the
order of the flux densities in the two images are different.


**Table** **3.** Parameters corresponding to the best fit model to image components obtained by fitting elliptical gaussians to the observed
lensed images, in the integrated CO(5-4) line and the radio. Refer to the text for the priors on the model. The reduced chi squared value
before the re-scaling of the visibility weights in the algorithm are 4.68 and 11.24 for the CO line and the radio, respectively. The flux
densities for the CO line and the radio data are in mJy and µJy, respectively. FWHMs are in arcseconds. Quantities derived from the
initial image-plane fitting are given in brackets, in the case of the radio data for the radio image convolved to the ALMA resolution;
other data are from uvmultifit fitting to the u − v data. The bottom table shows the positions of the four images with respect to the
lensing galaxy. For the u − v fit, the positions from Inada et al. (2003) were used and kept fixed. Positions in square brackets correspond
to the best fit model in the image plane fits.


**Flux** **Density** **FWHM** **Axis** **ratio**
CO line Radio CO line Radio CO line Radio
**A** 5.39 ± 0.30 (4.5) 16.71 ± 3.41 (16.8) 0.48 ± 0.07 (0.8) 0.32 ± 0.12 (0.80) 0.75 ± 0.19 (0.83) 0.69 ± 0.26 (0.9)
**B** 6.71 ± 0.36 (7.1) 12.18 ± 3.16 (13.2) 1.32 ± 0.07 (1.25) 0.32 ± 0.12 (0.79) 0.35 ± 0.04 (0.58) 0.69 ± 0.26 (1.0)
**C** 7.41 ± 0.41 (5.7) 13.55 ± 3.14 (14.1) 1.32 ± 0.07 (1.25) 0.32 ± 0.12 (0.80) 0.35 ± 0.04 (0.58) 0.69 ± 0.26 (1.0)
**D** 3.41 ± 0.26 (4.2) 13.06 ± 3.25 (13.5) 0.48 ± 0.07 (0.8) 0.32 ± 0.12 (0.79) 0.75 ± 0.19 (0.83) 0.69 ± 0.26 (0.9)
**Relative** **Positions** **(to** **lensing** **galaxy)** **(x,** **y)/** [′′]

CO line Radio
**A** (-0.162, 0.847) [(-0.06, 0.8)] (-0.162, 0.847) [(-0.09, 0.77)]
**B** (-0.213, -0.944) [(-0.11, -0.98)] (-0.213, -0.944) [(-0.15, -1.02)]
**C** (0.789, 0.182) [(0.89, 0.14)] (0.789, 0.182) [(0.85, 0.1)]
**D** (-0.702, 0.388) [(-0.60, 0.35)] (-0.702, 0.388) [(-0.63, 0.30)]



_3.1.2_ _ALMA_ _observations:_ _velocity-resolved_ _structure_ _in_
_the_ _CO(5-4)_ _line_


The ALMA CO(5-4) line observations (Fig. 5) clearly show that
the line originates in a structure with ordered spatial differentiation in velocity, such as rotation or possibly outflow. We can use
a simple lens model to project the frequency planes of the ALMA
data back into the source plane and thus determine simple parameters, such as size and rotation velocity of the emitting structure.
The relatively low resolution of the ALMA observations do not
allow us to ask more than simple questions of the data. In particular, we cannot derive the structure of the source in detail, nor
do we have the sensitivity at high resolution needed for investigation of detailed structure within the mass model. Observations
of another CO line which do allow this are presented in Stacey et
al. (in preparation).


The relatively low resolution, and the complexity of the information about the source that we seek, motivate a simple anal


ysis in which we project each of the frequency-sliced images back
to the source plane, without modelling the u − v data explicitly. This was the approach taken using simple VLA information
on the source HS 0810+2554 (Jackson et al. 2015) which proved
to yield roughly correct values for the source size when higher
quality observations became available (Hartley et al. 2019). We
use the previous SIE lens model (Section 3.1.1) which allows us
to fix the galaxy mass parameters, and we represent the source
structure in each frequency plane as a single elliptical Gaussian,
whose position, flux, width, axis ratio and position angle we allow to vary in order to fit the data. The resulting source positions
occupy a roughly linear configuration, with a clear sequence from
red to blue across the frequency band. These assumptions about
the source effectively constitute a regularisation, which prevents
the source structure from varying catastrophically as the model
attempts to fit noise in the image.


The resulting source model, with the astroid caustic of the
galaxy overlaid on top, is shown in Fig. 11. This caustic sep

MNRAS **000**, 1–15 (2020)

_SDSS_ _J0924+0219:_ _VLA_ _and_ _ALMA_ _observations_ 7


**Table** **4.** Parameters of source structures inferred from fits assuming a lens model, corresponding to the best fit for the integrated CO
line, submm continuum and radio map (convolved to ALMA resolution) of SDSS J0924+0219. These were fitted in the u − v plane with
a S´ersic profile source using visilens, and (figures in brackets) with a Gaussian profile source in the image plane. ∆x S0 and ∆y S0 are the
positions of the source with respect to the lens, in arcseconds. All angles are east of north. A standard galaxy model (critical radius 0 [′′] . 87,
ellipticity 0.13 at PA −73.1 [◦], shear magnitude 0.042 at PA 65.4 [◦] ) is used for the image plane fitting. For the u − v plane fitting, the lens
parameters are the same as for the image plane, except for the Einstein radius (0 [′′] . 92) which was obtained by optimising for it in case of
the CO line visibility data and subsequently kept fixed for the submillimeter continuum and radio u − v fits. The image plane fit for the
submillimeter continuum did not involve the f AD parameter.


**Parameters** **CO** **line** **submm** **continuum** **Radio**


_f_ AD 1 NA 0.97
∆ _x_ S0 / [′′] −0.037 ± 0.009 (−0.020) −0.050 ± 0.019 (−0.026) −0.037 ± 0.010 (−0.025)
∆y S0 / [′′] −0.036 ± 0.010 (−0.022) −0.017 ± 0.026 (0.005) −0.044 ± 0.009 (−0.019)
Source Flux Density/mJy 0.954 ± 0.057 (0.8) 0.225 ± 0.048 (0.1) 0.003 ± 0.002 (0.0023)
Source FWHM/ [′′] 0.081 ± 0.008 (0.045) 0.260 ± 0.071 (0.21) 0.120 ± 0.089 (0.052)
Source axis ratio 0.41 ± 0.10 (0.36) 0.866 ± 0.122 (0.92) 0.79 ± 0.17 (0.43)
Source PA/ [◦] 223.85 ± 7.55 (136.0) 171.50 ± 131.07 (0.0) 162.16 ± 117.79 (125)
S´ersic index 0.5 ± 0.3 1.029 ± 0.489 1.784 ± 0.324


_3.1.3_ _The_ _submillimetre_ _continuum_



**Figure** **5.** Slices through the ALMA CO(5-4) image cube at different frequencies; velocities on each plot are given in km s [−][1] with
respect to a redshift of 1.5254, the centroid of the CO emission.
The colourbar is in unit of Jy/beam.


arates regions in which the source is doubly and quadruply imaged, and is a locus of infinite magnification. The source model in
Fig. 11 is compatible with the images of the different CO planes
in Fig. 5, and its position angle and ellipticity are compatible
with the source structure inferred by modelling the integrated
CO image. However, the interpretation of details in Figure 11 has
to be done with caution: while we may be tempted to interpret
the source to be a warped disk, it should be noted that there
could be a large error bar on the fit to the velocity planes towards the red end because of their low signal to noise, as can
be seen from Figure 5. Given the limited angular resolution, the
structure could be consistent with a rotating molecular disk (eg
Smit et al. 2018), which has a size of between 0 [′′] . 1 and 0 [′′] . 3 depending on the exact centroids inferred for the lower-frequency parts
of the source, corresponding to ∼ 850–2500 pc at the redshift of
this quasar. However, observations at higher angular resolution
and sensitivity are required to confirm this hypothesis. The size
of the structure, and the overall distribution of velocities, is robust to different assumptions about the source structure, such as
allowing the source components corresponding to each frequency
plane to be circular Gaussians.


MNRAS **000**, 1–15 (2020)



Fig. 2 shows that the lensed submillimetre continuum displays a
ring structure, but which appears subtly different in the distribution of bright features to the CO line image. A simple lens model
of this structure, using the same SIE galaxy lens model as before,
gives a best fit in which the continuum source is somewhat offset
from the line; the best-fit source position is indicated in Fig. 11.
It appears closer to the northeastern fold caustic, in agreement
with the appearance of the lensed continuum map which suggests a different position for the merging image in the continuum
and line maps. This result requires confirmation, however, with
a longer observation. The source structure, lensed image configuration and the residual map obtained using the SIE galaxy lens
model are shown in Fig. 12; the width of the continuum source
from the model is about 0 [′′] . 21 (≈1.8 kpc at the redshift of this
source). This is found to be more compact compared to the dust
emission from a sample of dusty star-forming galaxies studied by
Hodge et al. (2016, 2019).

The source parameters from this image-plane fit were used as
initial parameters to perform a u − v plane fitting using visilens,
incorporating the SIE model of Eigenbrod et al. (2006). For the
optimization, we kept the parameters of the lensing galaxy fixed
(using the lensing galaxy position and mass derived from the optimisation of the CO line visibility data using visilens previously)
and let the source parameters vary. We assumed the source to
have a S´ersic profile (Fig. 12). The size of the submillimetre continuum found using u − v plane fitting (0 [′′] . 26±0 [′′] . 07, Table 4) is
consistent with the size of 0 [′′] . 21 found using the image plane fitting.


**3.2** **Radio**


In the VLA map of SDSS J0924+0219 (Fig. 1) we detect all four
lensed images in the system, and it is clear that the ratio of the
fluxes in the A and D images is less than the value of 12 which
is measured in the optical waveband, but that the flux densities
of the two images do not look equal. We again began by fitting
Gaussian components in the image plane. A preliminary fit of the
four lensed images with point-like gaussian components, using
aips jmfit, gave obviously unsatisfactory results, similar to what
is seen for the CO line map (Fig. 8). This shows that the radio
source is also extended.


The flux ratio of components A and D was determined using the radio map, convolved to the ALMA beam size, using the
Gaussian fitting method described earlier for the CO line, with

8 _Badole_ _et_ _al._


**Figure** **6.** Integrated CO(5-4) line spectrum, with the velocity centre at z=1.5254. The blue curve is the actual spectrum and the green
dashed curve the gaussian fit. The shaded light blue region represents the 1σ uncertainty on the spectrum.


**Figure** **7.** Left: ALMA first-moment map showing the velocity structure across the lensed images, with the velocities being with respect
to the centroid of the line emission (found to be at 228.22 GHz, thus corresponding to a redshift of z = 1.5254). Right: Moment two map
(velocity dispersion) of the continuum-free CO line emission. To obtain both these maps, we included only the pixels that have a signal
to noise (off-source noise in the channel maps) ratio greater than 4.



the same 10 image parameters. The best fit, of χ red [2] [=][ 1][.][8][,] [yielded]
an A/D flux ratio of 1.25; on the original map we obtained 1.28.
The best fit model and its parameters are shown in Fig. 13 and
Table 3 (values in brackets). For illustration, Fig. 13 shows what
the lensed image and the corresponding residual would look like
if we constrained the A/D flux ratio for this lens model to be
12, the ratio observed in the optical waveband. It confirms our
previous result that the radio data does not demonstrate an A/D
flux ratio of 12 and is more consistent with a lower flux ratio.
We carried out the lens modelling of the radio image, convolved
to the ALMA beam and incorporating the same SIE model for
the lensing galaxy as we did for the ALMA data (Section 3.1.1)
and assuming a Gaussian function for the source structure. We
kept the lensing galaxy parameters fixed and optimized only for
the source and the f AD parameter. The source structure, the best
fit lensed image and the residual map corresponding to the lens



model (χ red [2] [=][ 2][.][05][)] [are] [shown] [in] [Figure] [13] [and] [the] [corresponding]
parameters in Table 4 (values in brackets). Similar to the CO line
image, the f AD parameter in this case is also close to 1, implying that any flux anomaly in the radio can be attributed to the
extended source structure.


These image-plane fits were used to start the fitting in the
u − v plane. As for the integrated CO line, we fitted four elliptical Gaussians to the visibility data using uvmultifit, with image
positions from Inada et al. (2003) and fixing the component position angles. The four image flux densities, FWHMs and axis
ratios were optimized, keeping the FWHMs and axis ratios of the
four images equal, because using any more parameters than these
six (four flux densities, one width and one axis ratio) resulted in
the program failing to find a fit. The parameters for the best fit
model are tabulated in Table 3. The flux ratio A/D obtained from


MNRAS **000**, 1–15 (2020)

_SDSS_ _J0924+0219:_ _VLA_ _and_ _ALMA_ _observations_ 9


(a) (b)


**Figure** **8.** Image-plane fitting to ALMA CO line and radio images. Top: The best fit lensed image for the SIE lens model by Eigenbrod
et al. (2006). The first image from the left is the source structure, the second the CO line image from the data, the third the lensed image
and the fourth the corresponding residual map. The bars in the first and the second figures from the left represent 0 [′′] . 1 in the source
figure and 1 [′′] in the lensed image, respectively. The flux density is in unit of µJy/beam. χ red [2] [=] [1][.][85][.] [Bottom] [left] [((a)):] [Residual] [maps]
corresponding to the best fit lens model for a point source, projecting to four PSF-sized lensed images (inside the oval region). From the
left: residual for 1) CO line map 2) radio map convolved to ALMA beam and 3) radio map at its original resolution. It can be clearly
seen that there is an over-subtraction of flux at the position of the images and under-subtraction in the nearby areas. The flux density
units are in µJy/beam. Bottom right ((b)): Best fit CO-line lensed image and the corresponding residual map obtained by fitting four
elliptical Gaussian components at the image positions (χ red [2] [=][ 1][.][5][).] [The] [A/D] [flux] [ratio] [for] [this] [best] [fit] [model] [was] [found] [to] [be] [1.07.] [The]
unit of flux density in the image is µJy/beam and the x and y values are in arcseconds.


**Figure** **9.** Best fit model obtained by fitting the Eigenbrod et al. (2006) SIE model to the visibility data of the CO(5-4) emission line,
obtained using visilens.



this fitting was found to be 1.28 ± 0.41, once again consistent with
the flux ratio found from the image-plane analysis.


Following the same approach as for the CO(5-4) line, we
fixed the lens galaxy parameters and optimised for the source
parameters in visilens. Figure 13 shows the best fit model and the
residual map and Table 4 shows the corresponding parameters.
Even though the median size of the radio source inferred from the
u − v fit is seen to be only 1.3σ away from zero, it can be seen from
Figure 8 that the radio data is inconsistent with a point source.
We also find that the radio source size is sensitive to the starting
parameters of the u − v fit optimisation.


MNRAS **000**, 1–15 (2020)



**4** **DISCUSSION** **AND** **CONCLUSIONS**


There are two interesting questions we can attempt to answer
with these data, the answer to the second of which is related to
the first:


 - What is the size of the radio-emitting region, what physical
processes produce it, and is it co-spatial with the molecular line
gas?


 - Is the optical flux anomaly due to microlensing?

We discuss these two points in the following sections.


**4.1** **The** **radio** **source** **and** **the** **CO(5-4)** **line**


Although we do not have the resolution to study the structure of
the molecular disk in detail, it appears from the ALMA CO(5

10 _Badole_ _et_ _al._


**Figure** **10.** Corner plot showing the distribution for different parameters, obtained by fitting a lens model to the CO(5-4) visibility data
using visilens, described in Section 3.1.1. For this optimisation, all lens galaxy parameters were kept fixed, except the lens galaxy mass
and position. We also optimised for all source parameters. The parameters (with their units) are shown in the upper right corner for
clarity. They refer to: position of lensing galaxy, mass of the lensing galaxy, position of source with respect to the lensing galaxy, flux of
the CO source, width of the source, Sersic index, source axis ratio, phase angle and magnification.


MNRAS **000**, 1–15 (2020)

_SDSS_ _J0924+0219:_ _VLA_ _and_ _ALMA_ _observations_ 11


**Figure** **11.** Reconstructed source based on the ALMA observations, coloured according to frequency of the source (see text). The astroid
caustic of the model galaxy is overlaid. The white crosses are the positions of the sources for the individual CO planes. The black contours
are the sum of contours of the sources in all the planes. The circles in yellow and magenta correspond to the position of the optical and
the radio source, respectively. The circle in cyan corresponds to the submillimeter continuum source (refer to Fig. 12).


**Figure** **12.** Top, left to right: The best fit source structure, data, lensed image configuration and residual map obtained from the
image-plane lens modelling of the submillimetre continuum using the SIE galaxy lens model (Eigenbrod et al. 2006) used in Section 3.1.1
(χ red [2] [=] [1][.][19][).] [The] [bars] [in] [the] [first] [and] [the] [second] [figures] [from] [the] [left] [represent] [0] [′′] [.] [1] [in] [the] [source] [figure] [and] [1] [′′] [in] [the] [lensed] [image,]
respectively. The flux density is in units of µJy/beam. The curves in the source and the model panels show the astroid caustic and the
critical curve. Bottom: Fit to the u − v data of the submm continuum, starting with the image-plane fit.


MNRAS **000**, 1–15 (2020)

12 _Badole_ _et_ _al._


**Figure** **13.** Top: The best fit image-plane lens model for the radio map (convolved to the ALMA beam) assuming the SIE lens model
by Eigenbrod et al. (2006) (χ red [2] [=][ 2][.][05][).] [The] [bars] [in] [the] [first] [and] [second] [figures] [from] [the] [left] [represent] [0] [′′] [.] [1] [in] [the] [source] [figure] [and] [1] [′′] [in]
the lensed image, respectively. The flux density is in units of µJy/beam. The curves in the source and the model panels show the astroid
caustic and the critical curve. Middle: (Left) Image plane fit with elliptical Gaussian components, with residual: (Right) the same, but
enforcing a 12:1 ratio between components A and D. Bottom: Image, model, residual and high-resolution model from the u − v plane fit.



4) observation that we could be seeing a structure in ordered
motion, the natural explanation of which is the presence of a
rotating molecular disk. The structure is of physical dimension
approximately 100–300 mas (∼ 850–2500 pc), consistent with a
compact star-forming disk in the centre of the host galaxy of
SDSS 0924+0219. We have performed simple modelling of the
radio data (which is all that is warranted given the signal-tonoise and resolution of the data) and derive inconsistency with
a point source, and a preferred size of about 100 mas, consistent
with the size of the CO-line source. From Fig. 3 we see that the
lensed structures in the radio and CO lines are consistent with

each other. Although not conclusive, the most natural explanation is therefore that the two components of the source originate
from a region which is of the same size and physical origin. Combining the radio flux density from this work with the previously
determined far-IR flux densities of Stacey et al. (2018), it appears
that SDSS J0924+0219 lies on the standard radio-FIR correlation
(Ivison et al. 2010); the corresponding q IR parameter is found to
be 2.35, well within the range of q IR = 2.40 ± 0.24 found by Ivison et al. (2010). Thus the conclusion of radio emission produced
in a star-forming region appears natural. The physical size of the
disk, of order of a kiloparsec, is similar to, or slightly smaller than
that found in other high redshift lensed quasars with mid-J CO



transition (Alloin et al. 1997; Downes et al. 1999; Venturini &
Solomon 2003; Anh et al. 2013; Rybak et al. 2015; Geach et al.
2018). It is also found to be similar or more compact in size to
mid-J transition CO emission regions in high redshift, unlensed
quasars (Beelen et al. 2004; Riechers et al. 2009b; Polletta et al.
2011; Feruglio et al. 2018; Brusa et al. 2018). The unlensed flux
density of the CO line, as well as the molecular gas mass, are
both about a factor of 10 smaller than those of the radio-loud
quasars JVAS B1938+666 and MG 0751+2716 (Spingola et al.
2019), although the observations are not strictly comparable as
the higher-order CO line in this investigation preferentially traces
warmer gas, which tends to be more compact than the cold molecular gas. Figure 14 shows the spectral energy distribution (SED)
of SDSS J0924+0219, based on this work and previous studies
carried out by Stacey et al. (2018) and Jackson et al. (2015).
The SED was found to correspond to a dust temperature of T =
30.8 ± 0.8 K and emissivity index β = 1.6 ± 0.08.


Our ALMA observations detect the submillimetre contin
uum source, although at a relatively low signal-to-noise level.
Modelling of these observations gives a preliminary indication
that the submillimetre continuum source, which traces the illuminated dust, may be spatially displaced from the region emitting the molecular line and radio emission, although this requires


MNRAS **000**, 1–15 (2020)

_SDSS_ _J0924+0219:_ _VLA_ _and_ _ALMA_ _observations_ 13



**Figure** **14.** The spectral energy distribution of SDSS
J0924+0219, corresponding to a dust temperature of T = 30.8±0.8
K and β=1.6 ± 0.08. The SED was fit to the modified blackbody
curve defined by S ν ∝ ν h [3][+] ν [β], where h is the Planck constant, k

e kT −1

the Boltzmann constant, β the emissivity index and T the dust

temperature.


confirmation from deeper observations. Whether the radio emission contains partial contribution from an AGN-type source, as in
HS 0810+2554 (Hartley et al. 2019) will be interesting to determine from future VLBI observations. The submillimeter source is

also more extended than the CO emitting region; it may be that
star formation is taking place in only part of the overall structure
of dust and gas at the centre of the object.


**4.2** **Is** **microlensing** **the** **reason** **behind** **the** **optical**
**flux** **ratio** **anomaly?**


We now turn to the second question concerning the optical flux
ratio anomaly. In the case of SDSS J0924+0219, the flux ratio
between the brightest image and its merging counterpart in the
radio, was robustly determined as 1.28±0.41, consistent with all
methods of analysis. Similar results are obtained from the CO line
images, and at this resolution the observations are consistent with
a combination of a smooth lens model and an extended source.

Fig. 15 shows the variation in flux ratio in SDSS J0924+0219 with
wavelength.

These results are consistent with the theory that the optical flux anomaly can be attributed to microlensing, a conclusion
which is also consistent with previous studies of this object (Keeton et al. 2006; Morgan et al. 2006). As mentioned earlier, 15 years
seems to be a long time for microlensing to persist. To test that
such a long period of demagnification is plausible, we simulated
a microlensing magnification map corresponding to image D using the ray-tracing tree code developed by Wambsganss (2001).
We built a map with 100 microlensing Einstein radius η 0 sidelength and 0.005 η 0 / pixel resolution. For SDSS J0924+0219,
Mosquera & Kochanek (2011) calculate η 0 ∼ 3.2 × 10 [16] cm for an
average microlens mass < M/M ⊙ >= 0.3, and a transverse velocity of v trans =0.049 η 0 /year. We use convergence and shear values
at the position of image D as derived by Keeton et al. (2006) (i.e.
(κ, γ) = (0.48, 0.57)), a fraction of surface density in form of stars
of α = 0.07. This value of dark matter fraction is at the low side


MNRAS **000**, 1–15 (2020)



**Figure** **15.** Flux ratios in SDSS J0924+0219 over different wavelengths. The data for this plot has been taken from Table 2 in
Floyd et al. (2009), Keeton et al. (2006), Morgan et al. (2006),
Faure et al. (2011) and MacLeod et al. (2015). The logarithm in
the x-axis is in base 10.


of values derived from microlensing at a projected distance of ∼ 1
Einstein radius from the lens center (Jim´enez-Vicente et al. 2015).
To account for the optical-source size, we convolve the map by a
gaussian profile with half-light radius R 1/2 = 0.02η 0, correponding
to the I −band magnitude accretion disc source size expected in
the framework of the standard accretion disc model (Mosquera
& Kochanek 2011). Figure 16 shows a fraction of this map where
multiple regions demagnified by at least a factor 12 are observed.
Those regions extend over several η 0, which translates to periods
of demagnification that can last over 20 to 60 years. This result
remains qualitatively unchanged if we increase the source size by
a factor of 3, to account for the fact the the optical continuum
emission may be larger than expected by the standard model of
accretion (Morgan et al. 2010; Edelson et al. 2015; Hutsem´ekers
et al. 2020).

The overall importance of observing systems like
SDSS J0924+0219 is that such observations contribute to
the slow increase in the number of four-image strong lenses with
available fluxes at optical wavelengths as well as wavelengths
where the sources are large enough to be immune to microlensing.
Xu et al. (2015) considered the then best available sample of
radio lenses and studied the effect of CDM substructure on
each lens of the sample by adding substructure using Aquarius
and Phoenix simulations to the macro models of the lens and

examining the resulting flux ratio distributions, but like their
predecessors was limited to the then available sample of ∼10
systems. The joint analysis of radio studies of radio quiet quasars
and submillimetre/extended emission line studies is likely to
be useful in investigating the physics of the radio emission
and its relation to the molecular gas component (and possibly
also substructure, with availability of the higher resolution
submillimetre data).

14 _Badole_ _et_ _al._


**Figure** **16.** Microlensing magnification map associated with image D. We zoom over a region of 50×50 η 0 . The colour scale corresponds to the the micro(de)magnification of a gaussian source of
half-light radius R 1/2 = 0.06 η 0 (=1.8×10 [15] cm = 5.8×10 [−][4] pc). By
convention, micro-magnification ∆m > 0 correspond to the bright
regions, and demagnification correspond to ∆m < 0 as indicated
by the colorbar. Several regions with demagnification stronger
than |∆m| = 2.7 mag (i.e. corresponding to a flux ratio 1:12 as
observed in image D over the last decade) are detected. Those
regions sometimes extend over several microlensing Einstein radii

η 0 .


**ACKNOWLEDGEMENTS**


The Karl G. Jansky Very Large Array is operated by the US National Radio Astronomy Observatory. NRAO is a facility of the
National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This paper makes use of the
following ALMA data: ADS/JAO.ALMA2018.1.01447.S. ALMA
is a partnership of ESO (representing its member states), NSF
(USA) and NINS (Japan), together with NRC (Canada), MOST
and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory
is operated by ESO, AUI/NRAO and NAOJ. The authors would
like to thank Ian Browne and an anonymous referee for their comments on the paper, Justin Spilker for his help with visilens and
George Bendo for his assistance with the ALMA data analysis.


**REFERENCES**


Alloin D., Guilloteau S., Barvainis R., Antonucci R., Tacconi L.,
1997, Astronomy and Astrophysics, 321, 24
[Amara A., Metcalf R. B., Cox T. J., Ostriker J. P., 2006, Monthly](http://dx.doi.org/10.1111/j.1365-2966.2006.10053.x)
Notices of the Royal [Astronomical](http://dx.doi.org/10.1111/j.1365-2966.2006.10053.x) Society, 367, 1367
Anh P. T., Boone F., Hoai D. T., Nhung P. T., Weiß A., Kneib
J.-P., Beelen A., Salom´e P., 2013, Astronomy [&](http://dx.doi.org/10.1051/0004-6361/201321363) Astrophysics,
552, L12
Aravena M., et al., 2016, Monthly Notices [of](http://dx.doi.org/10.1093/mnras/stw275) the Royal Astronomical Society, 457, 4406
Atek H., et al., 2015, The [Astrophysical](http://dx.doi.org/10.1088/0004-637X/800/1/18) Journal, 800, 18
Beelen A., et al., 2004, Astronomy [&](http://dx.doi.org/10.1051/0004-6361:20040318) Astrophysics, 423, 441
[Bonzini M., et al., 2015, Monthly Notices of the Royal Astronom-](http://dx.doi.org/10.1093/mnras/stv1675)
ical [Society,](http://dx.doi.org/10.1093/mnras/stv1675) 453, 1079
Brusa M., et al., 2018, Astronomy [&](http://dx.doi.org/10.1051/0004-6361/201731641) Astrophysics, 612, A29



Burud I., et al., 2002, Astronomy [&](http://dx.doi.org/10.1051/0004-6361:20011731) Astrophysics, 383, 71
Chang K., Refsdal S., 1979, [Nature,](http://dx.doi.org/10.1038/282561a0) 282, 561
Chiba M., 2002, The [Astrophysical](http://dx.doi.org/10.1086/324493) Journal, 565, 17
Chiba M., Minezaki T., Kashikawa N., Kataza H., Inoue K. T.,
2005, The [Astrophysical](http://dx.doi.org/10.1086/430403) Journal, 627, 53
Condon J. J., Kellermann K. I., Kimball A. E., Ivezi´c Z., [ˇ] Perley
R. A., 2013, The [Astrophysical](http://dx.doi.org/10.1088/0004-637X/768/1/37) Journal, [768,](https://ui.adsabs.harvard.edu/abs/2013ApJ...768...37C) 37
Croton D. J., et al., 2006, Monthly Notices [of](http://dx.doi.org/10.1111/j.1365-2966.2005.09675.x) the Royal Astronomical Society, [365,](https://ui.adsabs.harvard.edu/abs/2006MNRAS.365...11C) 11
Dalal N., Kochanek C. S., 2002, The [Astrophysical](http://dx.doi.org/10.1086/340303) Journal, 572,

25

Deane R. P., Heywood I., Rawlings S., Marshall P. J., 2013,

Monthly Notices of the [Royal](http://dx.doi.org/10.1093/mnras/stt957) Astronomical Society, [434,](https://ui.adsabs.harvard.edu/abs/2013MNRAS.434...23D) 23
Downes D., Neri R., Wiklind T., Wilner D. J., Shaver P. A., 1999,

The [Astrophysical](http://dx.doi.org/10.1086/311896) Journal, 513, L1
Edelson R., et al., 2015, The [Astrophysical](http://dx.doi.org/10.1088/0004-637X/806/1/129) Journal, 806, 129
Eigenbrod A., Courbin F., Dye S., Meylan G., Sluse D., Vuissoz
C., Magain P., 2006, Astronomy [&](http://dx.doi.org/10.1051/0004-6361:20054423) Astrophysics, 451, 747
Fadely R., Keeton C. R., 2011, The [Astronomical](http://dx.doi.org/10.1088/0004-6256/141/3/101) Journal, 141,

101

Fadely R., Keeton C. R., 2012, Monthly [Notices](http://dx.doi.org/10.1111/j.1365-2966.2011.19729.x) of the Royal
[Astronomical](http://dx.doi.org/10.1111/j.1365-2966.2011.19729.x) Society, 419, 936
Fassnacht C. D., et al., 1998, The [Astronomical](http://dx.doi.org/10.1086/300724) Journal, 117, 658
Faure C., Sluse D., Cantale N., Tewes M., Courbin F., Durrer P.,
Meylan G., 2011, Astronomy [&](http://dx.doi.org/10.1051/0004-6361/201117787) Astrophysics, 536, A29
Feruglio C., et al., 2018, Astronomy [&](http://dx.doi.org/10.1051/0004-6361/201833174) Astrophysics, 619, A39
Floyd D. J., Bate N. F., Webster R. L., 2009, Monthly [Notices](http://dx.doi.org/10.1111/j.1365-2966.2009.15045.x) of
the Royal [Astronomical](http://dx.doi.org/10.1111/j.1365-2966.2009.15045.x) Society, 398, 233
Gaia Collaboration e. a., 2018, astro-ph/1804.09365
Geach J. E., Ivison R. J., Dye S., Oteo I., 2018, [ApJ,](http://dx.doi.org/10.3847/2041-8213/aae375) 866, L12
Gilman D., Birrer S., Treu T., Nierenberg A., Benson A., 2019,

[Monthly Notices of the Royal Astronomical Society, 487, 5721](http://dx.doi.org/10.1093/mnras/stz1593)
Hartley P., Jackson N., Sluse D., Stacey H. R., Vives-Arias H.,
[2019, Monthly Notices of the Royal Astronomical Society, 485,](http://dx.doi.org/10.1093/mnras/stz510)

[3009](https://ui.adsabs.harvard.edu/abs/2019MNRAS.485.3009H)

Herrera Ruiz N., Middelberg E., Norris R. P., Maini A., 2016,

Astronomy [&](http://dx.doi.org/10.1051/0004-6361/201628302) Astrophysics, [589,](https://ui.adsabs.harvard.edu/abs/2016A&A...589L...2H) L2
Hezaveh Y., Dalal N., Holder G., Kuhlen M., Marrone D., Murray
N., Vieira J., 2013a, The [Astrophysical](http://dx.doi.org/10.1088/0004-637X/767/1/9) Journal, 767, 9
[Hezaveh Y. D., et al., 2013b, The Astrophysical Journal, 767, 132](http://dx.doi.org/10.1088/0004-637X/767/2/132)
Hezaveh Y. D., et al., 2016, The [Astrophysical](http://dx.doi.org/10.3847/0004-637x/823/1/37) Journal, 823, 37
Hodge J. A., et al., 2016, The [Astrophysical](http://dx.doi.org/10.3847/1538-4357/833/1/103) Journal, 833, 103
Hodge J. A., et al., 2019, The [Astrophysical](http://dx.doi.org/10.3847/1538-4357/ab1846) Journal, 876, 130
H¨ogbom J. A., 1974, Astronomy and Astrophysics Supplement
Series, 15, 417
Hsueh J. W., Fassnacht C. D., Vegetti S., McKean J. P., Spingola
C., Auger M. W., Koopmans L. V., Lagattuta D. J., 2016,
Monthly Notices of the Royal Astronomical Society: Letters,
463, L51
Hutsem´ekers D., Sluse D., Kumar P., 2020, [Astronomy](http://dx.doi.org/10.1051/0004-6361/201936973) & Astro[physics,](http://dx.doi.org/10.1051/0004-6361/201936973) 633, A101
Inada N., et al., 2003, The [Astronomical](http://dx.doi.org/10.1086/375906) Journal, 126, 666
Irwin M. J., Webster R. L., Hewett P. C., Corrigan R. T., Jedrzejewski R. I., 1989, The [Astronomical](http://dx.doi.org/10.1086/115272) Journal, 98
Ivison R. J., et al., 2010, Astronomy [&](http://dx.doi.org/10.1051/0004-6361/201014552) Astrophysics, 518, 1
Jackson N., 2011, The [Astrophysical](http://dx.doi.org/10.1088/2041-8205/739/1/L28) Journal Letters, 739, L28
Jackson N., Tagore A. S., Roberts C., Sluse D., Stacey H., VivesArias H., Wucknitz O., Volino F., 2015, Monthly [Notices](http://dx.doi.org/10.1093/mnras/stv1982) of
the Royal [Astronomical](http://dx.doi.org/10.1093/mnras/stv1982) Society, 454, 287
Jarvis M. E., et al., 2019, Monthly Notices [of](http://dx.doi.org/10.1093/mnras/stz556) the Royal Astronomical Society, 485, 2710
Jim´enez-Vicente J., Mediavilla E., Kochanek C. S., Mu˜noz J. A.,
2015, The [Astrophysical](http://dx.doi.org/10.1088/0004-637X/799/2/149) Journal, 799, 149
Keeton C. R., Burles S., Schechter P. L., Wambsganss J., 2006,

The [Astrophysical](http://dx.doi.org/10.1086/499264) Journal, 639, 1
Kratzer R. M., Richards G. T., Goldberg D. M., Oguri M.,
Kochanek C. S., Hodge J. A., Becker R. H., Inada N., 2011,
The [Astrophysical](http://dx.doi.org/10.1088/2041-8205/728/1/L18) Journal, 728, L18


MNRAS **000**, 1–15 (2020)

_SDSS_ _J0924+0219:_ _VLA_ _and_ _ALMA_ _observations_ 15



MacLeod C. L., et al., 2015, The [Astrophysical](http://dx.doi.org/10.1088/0004-637X/806/2/258) Journal, 806, 258
Maiolino R., et al., 2017, [Nature,](http://dx.doi.org/10.1038/nature21677) 544, 202
Mao S., Schneider P., 1998, Monthly Notices [of](http://dx.doi.org/10.1046/j.1365-8711.1998.01319.x) the Royal Astronomical Society, 295, 587
Mart´ı-Vidal I., Vlemmings W. H., Muller S., Casey S., 2014, [As-](http://dx.doi.org/10.1051/0004-6361/201322633)
tronomy & [Astrophysics,](http://dx.doi.org/10.1051/0004-6361/201322633) 563, A136
Mcmullin J. P., Waters B., Schiebel D., Young W., Golap K.,
2007, in Astronomical Data Analysis Software and Systems
XVI ASP Conference Series. p. 127
Metcalf R. B., Madau P., 2001, The [Astrophysical](http://dx.doi.org/10.1086/323695) Journal, 563,

9

Metcalf R. B., Zhao H., 2002, The [Astrophysical](http://dx.doi.org/10.1086/339798) Journal, 567, L5
Miranda M., Macci`o A. V., 2007, Monthly [Notices](http://dx.doi.org/10.1111/j.1365-2966.2007.12440.x) of the Royal
[Astronomical](http://dx.doi.org/10.1111/j.1365-2966.2007.12440.x) Society, 382, 1225
M¨oller O., Hewett P., Blain A. W., 2003, Monthly [Notices](http://dx.doi.org/10.1046/j.1365-8711.2003.06758.x) of the
Royal [Astronomical](http://dx.doi.org/10.1046/j.1365-8711.2003.06758.x) Society, 345, 1
Morgan C. W., Kochanek C. S., Morgan N. D., Falco E. E., 2006,

The [Astrophysical](http://dx.doi.org/10.1086/505569) Journal, 647, 874
Morgan C. W., Kochanek C. S., Morgan N. D., Falco E. E., 2010,

The [Astrophysical](http://dx.doi.org/10.1088/0004-637X/712/2/1129) Journal, 712, 1129
Mosquera A. M., Kochanek C. S., 2011, The [Astrophysical](http://dx.doi.org/10.1088/0004-637X/738/1/96) Jour[nal,](http://dx.doi.org/10.1088/0004-637X/738/1/96) 738, 96
Moustakas L. A., Metcalf R. B., 2003, Monthly [Notices](http://dx.doi.org/10.1046/j.1365-8711.2003.06055.x) of the
Royal [Astronomical](http://dx.doi.org/10.1046/j.1365-8711.2003.06055.x) Society, 339, 607
Nierenberg A. M., et al., 2017, Monthly [Notices](http://dx.doi.org/10.1093/mnras/stx1400) of the Royal
[Astronomical](http://dx.doi.org/10.1093/mnras/stx1400) Society, 471, 2224
Nierenberg A. M., et al., 2020, Monthly [Notices](http://dx.doi.org/https://doi.org/10.1093/mnras/stz3588) of the Royal
[Astronomical](http://dx.doi.org/https://doi.org/10.1093/mnras/stz3588) Society, 492, 5314
Padovani P., et al., 2017, The Astronomy [and](http://dx.doi.org/10.1007/s00159-017-0102-9) Astrophysics Re[view,](http://dx.doi.org/10.1007/s00159-017-0102-9) [25,](https://ui.adsabs.harvard.edu/abs/2017A&ARv..25....2P) 2
Paraficz D., et al., 2018, Astronomy [&](http://dx.doi.org/10.1051/0004-6361/201731250) Astrophysics, 613, A34
Peeples M. S., Schechter P. L., Wambsganss J. K., 2004, in BAAS.
p. 1392
Poindexter S., Morgan N., Kochanek C. S., 2008, The [Astrophys-](http://dx.doi.org/10.1086/524190)
ical [Journal,](http://dx.doi.org/10.1086/524190) 673, 34
Polletta M., Nesvadba N. P., Neri R., Omont A., Berta S., Bergeron J., 2011, Astronomy [&](http://dx.doi.org/10.1051/0004-6361/201116446) Astrophysics, 533, A20
Riechers D. A., Walter F., Carilli C. L., Lewis G. F., 2009a, [The](http://dx.doi.org/10.1088/0004-637X/690/1/463)
[Astrophysical](http://dx.doi.org/10.1088/0004-637X/690/1/463) Journal, 690, 463
Riechers D. A., et al., 2009b, The [Astrophysical](http://dx.doi.org/10.1088/0004-637X/703/2/1338) Journal, 703,

1338

Riechers D. A., et al., 2011, The [Astrophysical](http://dx.doi.org/10.1088/2041-8205/739/1/L32) Journal Letters,

739, L32
Rybak M., Vegetti S., McKean J. P., Andreani P., White S. D. M.,
[2015, Monthly Notices of the Royal Astronomical Society, 453,](http://dx.doi.org/10.1093/mnrasl/slv092)

[L26](https://ui.adsabs.harvard.edu/abs/2015MNRAS.453L..26R)

Saha P., Williams L. L. R., Ferreras I., 2007, The [Astrophysical](http://dx.doi.org/10.1086/518083)
[Journal,](http://dx.doi.org/10.1086/518083) 663, 29
Smit R., et al., 2018, [Nature,](http://dx.doi.org/10.1038/nature24631) 553, 178
Solomon P. M., Vanden Bout P. A., 2005, Annual [Review](http://dx.doi.org/10.1146/annurev.astro.43.051804.102221) of Astronomy and Astrophysics, 43, 677
Spilker J. S., et al., 2016, The [Astrophysical](http://dx.doi.org/10.3847/0004-637x/826/2/112) Journal, 826, 112
Spingola C., et al., 2019, arXiv e-prints, p. [arXiv:1905.06363](https://ui.adsabs.harvard.edu/abs/2019arXiv190506363S)
Stacey H. R., et al., 2018, Monthly Notices [of](http://dx.doi.org/10.1093/mnras/sty458) the Royal Astronomical Society, 476, 5075
Stacey H. R., et al., 2019, Astronomy [&](http://dx.doi.org/10.1051/0004-6361/201833967) Astrophysics, 622, A18
Sugai H., Kawai A., Shimono A., Hattori T., Kosugi G.,
Kashikawa N., Inoue K. T., Chiba M., 2007, The [Astrophysi-](http://dx.doi.org/10.1086/513731)
cal [Journal,](http://dx.doi.org/10.1086/513731) 660, 1016
Treu T., 2010, Annual Review of [Astronomy](http://dx.doi.org/10.1146/annurev-astro-081309-130924) and Astrophysics,
48, 87
Tuan-Anh P., Hoai D. T., Nhung P. T., Diep P. N., Phuong N. T.,
Thao N. T., Darriulat P., 2017, Monthly [Notices](http://dx.doi.org/10.1093/mnras/stx212) of the Royal
[Astronomical](http://dx.doi.org/10.1093/mnras/stx212) Society, 467, 3513
Vegetti S., Koopmans L. V., 2009, Monthly [Notices](http://dx.doi.org/10.1111/j.1365-2966.2008.14005.x) of the Royal
[Astronomical](http://dx.doi.org/10.1111/j.1365-2966.2008.14005.x) Society, 392, 945
Vegetti S., Czoske O., Koopmans L. V., 2010a, [Monthly](http://dx.doi.org/10.1111/j.1365-2966.2010.16952.x) Notices
of the Royal [Astronomical](http://dx.doi.org/10.1111/j.1365-2966.2010.16952.x) Society, 407, 225


MNRAS **000**, 1–15 (2020)



Vegetti S., Koopmans L. V., Bolton A., Treu T., Gavazzi R.,
2010b, Monthly Notices of the [Royal](http://dx.doi.org/10.1111/j.1365-2966.2010.16865.x) Astronomical Society,
408, 1969
Venturini S., Solomon P. M., 2003, The [Astrophysical](http://dx.doi.org/10.1086/375050) Journal,

590, 740
Vuissoz C., et al., 2007, Astronomy [&](http://dx.doi.org/10.1051/0004-6361:20065823) Astrophysics, 464, 845
Vuissoz C., et al., 2008, Astronomy [&](http://dx.doi.org/10.1051/0004-6361:200809866) Astrophysics, 488, 481
Wambsganss J., 2001, Publications of the [Astronomical](http://dx.doi.org/10.1071/AS01016) Society
of [Australia,](http://dx.doi.org/10.1071/AS01016) 18, 207
Warren S. J., Dye S., 2003, The [Astrophysical](http://dx.doi.org/10.1086/375132) Journal, 590, 673
White S. V., Jarvis M. J., Kalfountzou E., Hardcastle M. J.,
Verma A., Cao Orjales J. M., Stevens J., 2017, [Monthly](http://dx.doi.org/10.1093/mnras/stx284) Notices of the Royal [Astronomical](http://dx.doi.org/10.1093/mnras/stx284) Society, 468, 217
Witt H., Mao S., Schechter P., 1995, The [Astrophysical](http://dx.doi.org/10.1086/175499) Journal,
443, 18
Wucknitz O., Volino F., 2008, arXiv e-prints, p. [arXiv:0811.3421](https://ui.adsabs.harvard.edu/abs/2008arXiv0811.3421W)
Xu D. D., Mao S., Cooper A. P., Gao L., Frenk C. S., Angulo
R. E., Helly J., 2012, Monthly Notices [of](http://dx.doi.org/10.1111/j.1365-2966.2012.20484.x) the Royal Astronomical Society, 421, 2553
Xu D., Sluse D., Gao L., Wang J., Frenk C., Mao S., Schneider P.,
[Springel V., 2015, Monthly Notices of the Royal Astronomical](http://dx.doi.org/10.1093/mnras/stu2673)
[Society,](http://dx.doi.org/10.1093/mnras/stu2673) 447, 3189
Yang C., et al., 2017, Astronomy [&](http://dx.doi.org/10.1051/0004-6361/201731391) Astrophysics, 608, [A144](https://ui.adsabs.harvard.edu/abs/2017A&A...608A.144Y)
[Yuan T. T., Kewley L. J., Swinbank A. M., Richard J., 2012, The](http://dx.doi.org/10.1088/0004-637X/759/1/66)
[Astrophysical](http://dx.doi.org/10.1088/0004-637X/759/1/66) Journal, 759, 66
Zakamska N. L., et al., 2016, Monthly Notices of the Royal As[tronomical](http://dx.doi.org/10.1093/mnras/stv2571) Society, 455, 4191
Zheng W., et al., 2012, [Nature,](http://dx.doi.org/10.1038/nature11446) 489, 406


This paper has been typeset from a TEX/L [A] TEX file prepared by
the author.


</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "~0.8 arcsec (natural weighting); 0.68 x 0.56 arcsec with PA = 69.77 deg (Briggs weighting, robust = 0.0)",
  "failed_quote": "The array configuration used gave a resolution of approximately 0 [′′] . 8 with natural weighting; the calibrated data were also re-imaged with Briggs weighting (with a default robustness parameter of 0.0), giving a higher resolution of 0 [′′] . 68 × 0 [′′] . 56 with PA = 69.77 [◦]"
 },
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "Singular Isothermal Ellipsoid (SIE) lens galaxy mass model parameters (critical radius 0.87 arcsec, ellipticity 0.13 at PA -73.1 deg, shear magnitude 0.042 at PA 65.4 deg)",
  "failed_quote": "In addition, we performed a gravitational lens modelling using the Singular Isothermal Ellipsoid (SIE) model developed by Eigenbrod et al. (2006) for the lensing galaxy."
 },
 {
  "path": "processing.calibration.pipeline_or_manual.evidence[0]",
  "value": "standard ALMA pipeline and VLA Calibration Pipeline",
  "failed_quote": "The VLA Calibration Pipeline, using the software package casa (Common Astronomy Software Application ; Mcmullin et al. 2007) was run on each of the four measurement sets."
 },
 {
  "path": "processing.imaging.weighting_robust.evidence[0]",
  "value": "natural weighting and Briggs weighting with robust = 0.0 (ALMA); natural weighting (VLA)",
  "failed_quote": "The array configuration used gave a resolution of approximately 0 [′′] . 8 with natural weighting; the calibrated data were also re-imaged with Briggs weighting (with a default robustness parameter of 0.0), giving a higher resolution of 0 [′′] . 68 × 0 [′′] . 56 with PA = 69.77 [◦]"
 },
 {
  "path": "processing.imaging.final_beam.evidence[1]",
  "value": "0.68 x 0.56 arcsec with PA = 69.77 deg (ALMA Briggs weighting); ~0.8 arcsec (ALMA natural weighting); 0.489 x 0.395 arcsec with PA = -28.43 deg (VLA natural weighting)",
  "failed_quote": "The array configuration used gave a resolution of approximately 0 [′′] . 8 with natural weighting; the calibrated data were also re-imaged with Briggs weighting (with a default robustness parameter of 0.0), giving a higher resolution of 0 [′′] . 68 × 0 [′′] . 56 with PA = 69.77 [◦]"
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "Singular Isothermal Ellipsoid (SIE) lens model for the lensing galaxy",
  "failed_quote": "In addition, we performed a gravitational lens modelling using the Singular Isothermal Ellipsoid (SIE) model developed by Eigenbrod et al. (2006) for the lensing galaxy."
 },
 {
  "path": "analysis_steps[1].method.evidence[2]",
  "value": "Fit four elliptical Gaussians at the image positions in the CO(5-4) and radio maps using a 10-parameter optimization, and test point-source Gaussian fits with AIPS JMFIT.",
  "failed_quote": "The flux ratio of components A and D was determined using the radio map, convolved to the ALMA beam size, using the Gaussian fitting method described earlier for the CO line, with the same 10 image parameters."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Optimize a Gaussian source profile and flux anomaly parameter f_AD through an SIE lens galaxy mass model against the CO(5-4), submm continuum, and radio images.",
  "failed_quote": "In addition, we performed a gravitational lens modelling using the Singular Isothermal Ellipsoid (SIE) model developed by Eigenbrod et al. (2006) for the lensing galaxy."
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Optimize a Gaussian source profile and flux anomaly parameter f_AD through an SIE lens galaxy mass model against the CO(5-4), submm continuum, and radio images.",
  "failed_quote": "Allowing the source to have a Gaussian profile, the galaxy position and the source parameters were optimized using the difference between the data and the lensed images convolved with the point spread function."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Singular Isothermal Ellipsoid (SIE) lens mass profile and Gaussian source profile",
  "failed_quote": "Allowing the source to have a Gaussian profile, the galaxy position and the source parameters were optimized using the difference between the data and the lensed images convolved with the point spread function."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "Optimization of difference between data and PSF-convolved lensed model images",
  "failed_quote": "the galaxy position and the source parameters were optimized using the difference between the data and the lensed images convolved with the point spread function."
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Comparison of u-v A/D flux ratios with image-plane results",
  "failed_quote": "The flux ratio A/D obtained from this fitting was found to be 1.28 ± 0.41, once again consistent with the flux ratio found from the image-plane analysis."
 },
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "VLA and ALMA calibration pipelines and CLEAN imaging",
  "failed_quote": "The VLA Calibration Pipeline, using the software package casa (Common Astronomy Software Application ; Mcmullin et al. 2007) was run on each of the four measurement sets."
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Radio A/D flux ratio (u-v plane fit) = 1.28 dimensionless",
  "failed_quote": "The flux ratio A/D obtained from this fitting was found to be 1.28 ± 0.41, once again consistent with the flux ratio found from the image-plane analysis."
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "The CO(5-4) emission shows ordered velocity structure consistent with a rotating molecular disk of ~850-2500 pc physical size.",
  "failed_quote": "it appears from the ALMA CO(5-4) observation that we could be seeing a structure in ordered motion, the natural explanation of which is the presence of a rotating molecular disk. The structure is of physical dimension approximately 100–300 mas (∼ 850–2500 pc)"
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "The submillimetre continuum source may be spatially offset from the CO(5-4) and radio emission and is more extended than the CO emitting region, though deeper observations are needed to confirm this.",
  "failed_quote": "Modelling of these observations gives a preliminary indication that the submillimetre continuum source, which traces the illuminated dust, may be spatially displaced from the region emitting the molecular line and radio emission, although this requires confirmation from deeper observations."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Point-source model for the CO(5-4) and radio emission (rejected because residuals show clear over-subtraction at image positions and under-subtraction in nearby areas)",
  "failed_quote": "We also attempted to fit a lens model assuming a point source, giving unresolved point images ; the resultant residual shows an over-subtraction of flux in the image positions and under-subtraction in the nearby areas (see Fig. 8, bottom left), demonstrating incompatibility of a point source with our observation."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[1]",
  "value": "Low signal-to-noise ratio of the ALMA submillimetre continuum prevents measuring individual component fluxes and requires deeper observations to confirm the spatial offset from the CO line.",
  "failed_quote": "Modelling of these observations gives a preliminary indication that the submillimetre continuum source, which traces the illuminated dust, may be spatially displaced from the region emitting the molecular line and radio emission, although this requires confirmation from deeper observations."
 }
]
```
