# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025MNRAS.538.2358S\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–16 (2025) Preprint 26 March 2025 Compiled using MNRAS L [A] TEX style file v3.3

### **High angular resolution evidence of dust traps from deep ALMA Band 3** **observations of LkCa15**


Anibal Sierra, [1] _[,]_ [2] _[★]_ Paola Pinilla, [1] Laura M. Pérez, [2] Myriam Benisty, [3] Carolina Agurto-Gangas, [2]

Carlos Carrasco-González, [4] Pietro Curone, [2] Feng Long [5] _[,]_ [6]

1 _Mullard Space Science Laboratory, University College London, Holmbury St Mary, Dorking, Surrey RH5 6NT, UK_
2 _Departamento de Astronomía, Universidad de Chile, Camino El Observatorio 1515, Las Condes, Santiago, Chile_
3 _Max-Planck Institute for Astronomy (MPIA), Königstuhl 17, 69117 Heidelberg, Germany_
4 _Instituto de Radioastronomía y Astrofísica (IRyA), Universidad Nacional Autónoma de México (UNAM), Campus Morelia, Michoacán, Mexico_
5 _Lunar and Planetary Laboratory, University of Arizona, Tucson, AZ 85721, USA_
6 _NASA Hubble Fellowship Program Sagan Fellow_


Accepted 2025 March 4. Received 2025 March 3; in original form 2024 December 17


**ABSTRACT**

Dust traps are the most promising mechanisms to explain the observed substructures in protoplanetary discs. In this work, we

∼
present high-angular resolution ( 60 mas, 9.4 au) and high-sensitivity Atacama Large Millimetre/submillimetre Array (ALMA)
observations at 3 mm of the transitional disc around LkCa15. The new data, combined with previous high-resolution observations
at _𝜆_ = 0 _._ 87 _,_ 1 _._ 3 mm, make LkCa15 an ideal laboratory for testing the dust trapping mechanism. We found that the width of the
three rings decreases linearly with frequency, and the spectral indices show local minima at the locations of the rings, consistent
with dust trap models. Multi-wavelength modelling confirms that the dust surface density and maximum grain size peak at 69 and
101 au, and suggestive peak at 42 au. The estimated total dust mass is between 13-250 M ⊕, depending on the chosen opacity. The
inner disc shows bright and unresolved emission at 3 mm, exhibiting a spectral index of _𝛼_ 1 _._ 3−3mm = 0 _._ 3 ± 0 _._ 37, and _𝛼_ 3mm−3cm
ranging from −0 _._ 1 to 0 _._ 0. These properties are consistent with free-free emission from an ionised jet or disc wind. Dust evolution
models and radiative transfer calculations suggest that a viscosity coefficient of _𝛼_ = 10 [−][3], a fragmentation velocity of 10 m s [−][1],
and DSHARP opacities provide the best match to the observed properties.


**Key words:** Techniques: Interferometric – Protoplanetary discs



**1** **INTRODUCTION**


Our understanding of planet formation has significantly advanced
over the past decade, mainly thanks to high angular resolution and
sensitive observations of protoplanetary disc at millimetre and infrared wavelengths (Andrews et al. 2018; Benisty et al. 2023), along
with state-of-the-art models capable of reproducing and explaining
the physics behind the diverse substructures observed in the dust and
gas distribution.
One key discovery has been the prediction (e.g., Birnstiel et al.
2012; Pinilla et al. 2012) and observational detection (e.g., van der
Marel et al. 2013; Pérez et al. 2014; Casassus et al. 2015) of dust traps,
which is proposed as an efficient mechanism to halt or slow down
the inward migration of dust grains toward the central star, offering
a solution to the fast radial drift problem in planet formation theory
(Whipple 1972; Weidenschilling 1977). To date, evidence of dust
traps has been observed in several discs at high angular resolution,
either through dust continuum millimetre observations (e.g., Dullemond et al. 2018; Macías et al. 2021; Sierra et al. 2021; Carvalho
et al. 2024), or gas kinematics (e.g., Rosotti et al. 2020; Izquierdo
et al. 2023). This observational evidence suggests the presence of


_★_ E-mail: anibalsierram@gmail.com


© 2025 The Authors



forming planets (Pinilla et al. 2012), dead zones (e.g., Regály et al.
2012; Flock et al. 2015; Gárate et al. 2021; Delage et al. 2023), or
zonal flows (e.g., Johansen et al. 2009; Uribe et al. 2011; Simon &
Armitage 2014).
Examples of discs in which dust traps have been proposed to
explain their morphology are those with large inner cavities, also
known as “transitional discs” (e.g., Calvet et al. 2002; Andrews et al.
2011; van der Marel 2023). One notable example is the disc around
LkCa15, a K5 star with a mass of 1.2 M ⊙, located in the Taurus
star-forming region at 157.2 pc (Gaia Collaboration 2020; Manara
et al. 2014). Its inner dust cavity was resolved over a decade ago
(Piétu et al. 2006; Andrews et al. 2011), a gas surface density drop,
which has been shown to be shallow except in the inner 10 au, has
been inferred from CO isotopologue observations (van der Marel
et al. 2015; Leemker et al. 2022, see Figure 14 by Leemker.). The
constraints on the gas density drop are fundamental to discerning the
origin of the ring structure in transitional discs (Bruderer 2013; van
der Marel et al. 2016; Huang et al. 2024). In particular, the origin of
the ring at 69 au in LkCa15 is consistent with a carving Jovian planet
(Huang et al. 2024).
Millimetre observations (angular resolution between 55-150 mas)
have revealed the presence of three rings at 42, 69, and 101 au
(Isella et al. 2014; Facchini et al. 2020). Additionally, suggestive

2 _A. Sierra et al._


evidence of a potential planet at 42 au has been proposed based on
dust accumulation at Lagrangian points, as observed in the continuum
emission of Bands 6 (1.3 mm) and 7 (0.87 mm) (Long et al. 2022).
The disc around LkCa15 appears to be a strong candidate where dust
traps may accumulate dust particles in its rings, potentially triggering
the streaming instability (e.g., Youdin & Goodman 2005; Stammler
et al. 2019; Flock & Mignone 2021), as suggested by Facchini et al.
(2020), and promoting the formation of planetesimals.
Recent modelling of the dust continuum emission at ALMA Bands
7 and 6, and VLA Band Q (7 mm) by Sierra et al. (2024) shows that
the dust surface density and maximum grain sizes peak around the
rings at 69 and 101 au in LkCa15, which is consistent with dust
trap models. However, the 150 mas (23.6 au) angular resolution,
limited by the 7 mm observations, made it challenging to resolve the
three rings, and analyse the radial profiles with high contrast between
rings and gaps. Long-wavelength observations ( _𝜆_ ≳ 1 _._ 3 mm), where
optically thin emission is detected, are essential for disentangling
degeneracies in radiative transfer modelling (Viscardi et al., in prep.)
and should not be excluded from the analysis.
In this work, we present deep observations of the dust continuum
emission of the disc around LkCa15 at ALMA Band 3 (97.5 GHz,
Section 2), at an angular resolution of 60 mas (9.4 au) when imaging
with traditional techniques, or 35 mas (5.5 au) when modelling the
visibilities. The Band 3 dust continuum observations are compared
with the observations at Band 7 and Band 6 in Long et al. (2022),
allowing us to study the morphology of the dust continuum emission
at optically thin wavelengths at high resolution (Section 3), analyse
its azimuthal asymmetries, and look for observational evidence of
Lagrangian structures (Section 3.3). The multi-wavelength data also
allows us to infer physical dust properties by fitting the spectral energy
distribution (Section 3.4), and put constraints on the amount of dust
and non-dust emission in the inner disc of Band 3 (Section 3.5). Dust
evolution models tailored for LkCa15 are presented in Section 4, and
the results are discussed in Section 5. Finally, the conclusions are
summarized in Section 6.


**2** **OBSERVATIONS**


ALMA observed the disc around LkCa15in Band 3 (Program project:
2022.1.01216.S, PI: Anibal Sierra) from January 2023 to August
2023. The spectral setup was configured to four dedicated dust continuum spectral windows, covering frequencies between 89.54-91.52
GHz, 91.43-93.42 GHz, 101.54-103.52 GHz, 103.50-105.48 GHz,
and at a spectral resolution of 31.25 MHz.
The data consist of one short baseline (SB), 2 medium baselines
(MB), and 4 long baselines (LB) executions. Table 1 shows the details
of each execution. The data were calibrated using the standard calibration provided by the observatory, where problematic antennas for
each execution were flagged. The calibrated data were self-calibrated
using CASA version 6.4.3.27 (McMullin et al. 2007). We checked
the astrometric alignment between different executions by creating
low angular resolution images of each execution and fitting a 2D
Gaussian to each dust continuum map. However, the inferred offsets
were within 5% of the final beam size. Alternatively, we also verify that the main substructures (ring-like features) observed in each
individual execution spatially align.
During each self-calibration iteration, we choose a Briggs robust
parameter of 0.5 to image the new dataset and assume that the brightness distribution consists of emission at different angular scales.
Therefore, we use the `multi-scale` algorithm with angular scales
corresponding to point sources, 1 beam size, and 2 beam sizes, and


MNRAS **000**, 1–16 (2025)



a threshold of 2 _𝜎_ . The signal-to-noise ratio (SNR) is measured after
each self-calibration iteration, and we proceed to apply additional
iterations if the SNR improves by at least a factor of 5%. In each iteration, we use the task `applymode=‘calonly’` within the `applycal`
task to calibrate data only and do not apply flags from solutions.
We first self calibrate the SB execution only. We combine spectral windows and scans using `combine=‘spws,scans’` within the
`gaincal` task. After three rounds of phase self calibrations with solution time intervals equals to `solint` `=` `‘inf’,` `‘360s’,` `‘120s’`,
the SNR increased 164%, 10%, and 8% with respect to the previous iteration, respectively. No amplitude self calibration was applied
because the SNR did not significantly improve.
Before concatenating the MB and LB data, we check for flux-scale
alignment and found that the flux of the SB and LB are consistent within the expected uncertainties (less than 1.5% of difference).
However, the flux from the MB disagree by 20% compared with that
from SB and LB data. The SB and LB executions were observed

closer in time to the amplitude measurements of the flux calibrator
from the ALMA calibrator monitoring [1] . Therefore, the visibilities
of the MB datasets are re-scaled to match the SB and LB flux. Then

we concatenate the self calibrated SB to the re-scaled MB executions

and apply one phase self-calibration iteration with a solution time
interval equal to `solint` `=` `‘inf’` . The SNR of the self calibrated
data increased by 5%. Finally, we concatenated the LB executions
and tried to apply phase and amplitude self-calibration iterations with
different solution time intervals, but the SNR did not significantly
improve. We create a final Band 3 dust continuum map by cleaning
the self calibrated data with a Briggs robust parameter of 0 and a
Gaussian uvtaper of 27 mas × 42 mas; 0 deg, resulting in a beam
size of 59 mas × 55 mas. Then, a convolution was applied using the
task `imsmooth` in CASA to get a circular beam of 60 mas.
In this paper, we compare the Band 3 dust continuum observations
of LkCa15 with previous Band 6 (224 GHz) and 7 (340 GHz) observations of the disc. We use the self-calibrated measurement sets

from Long et al. (2022) and re-image the Band 6/Band 7 data using
a Briggs robust value of 0.0/0.5 and a uvtaper of 12 mas × 39 mas;
0 deg/10 mas × 30 mas; 0 deg. We then apply convolution with the
`imsmooth` task to match the circular 60 mas beam of the Band 3

map. The total fluxes in our Band 6 and 7 images are 145 _._ 6 ± 4 _._ 3 mJy
and 418 _._ 1 ± 4 _._ 7 mJy, respectively (Section 3.5). These values are
consistent within the 10% flux calibration uncertainties when com
pared with the fluxes of 140 ± 3 mJy at 214 GHz reported by Piétu
et al. (2006) using the IRAM PdBI array, 128 ± 5 mJy at 224 GHz
by Isella et al. (2012) with CARMA, and 167 ± 6 mJy at 230 GHz
and 430 ± 30 mJy at 340 GHz by Andrews & Williams (2005) using
the Sub-millimetre Common-User Bolometer Array (SCUBA).


**3** **RESULTS**


**3.1** **Dust continuum images**


Figure 1 shows the dust continuum maps in this work. The left panel
shows the new Band 3 observations, while the middle panels show
the re-imaging data at Band 6 and 7 presented in Long et al. (2022).
The right panel is the brightness temperature radial profile (without
assuming Rayleigh-Jeans approximation) for each map, computed
with Gofish (Teague 2019). The bright three rings at 42, 69, and 101
au (Long et al. 2022) are distinguishable in the three wavelengths
(we follow the nomenclature B42, B69, and B101 for Bright rings).


1 `[https://almascience.eso.org/sc/](https://almascience.eso.org/sc/)`

_High angular resolution evidence of dust traps from deep ALMA Band 3 observations of LkCa15_ 3


**Table 1.** Summary of the ALMA Band 3 execution observations.


UIDs Config UTC Time N ant Baselines On-source Time
(m-km) (min)
(1) (2) (3) (4) (5) (6)


uid://A002/X1026621/X41c8 C43-4 2023-01-20 03:33:39 44 15.3-0.8 16.63

uid://A002/X107abb1/X148e0 C43-7 2023-05-27 16:35:59 43 27.5-3.7 26.17

uid://A002/X107abb1/X13f33 C43-7 2023-05-27 15:04:05 42 27.5-3.7 26.21

uid://A002/X10b0d7d/X808b C43-10 2023-08-07 12:58:41 48 230.2-16.2 22.11

uid://A002/X10b0d7d/X3c87 C43-10 2023-08-06 11:57:31 44 230.2-16.2 41.90

uid://A002/X10b0d7d/X34bd C43-10 2023-08-06 13:55:42 46 230.2-16.2 41.93

uid://A002/X10a67b8/X439b C43-10 2023-07-21 14:52:37 46 230.2-15.2 41.90


(1) Execution block ID. (2): ALMA configuration. (3) UTC time at the end of the observation. (4) Number of non-flagged antennas. (5) Baseline coverage. (6)

Effective on-source time.



The contrast between the rings and gaps clearly increases with wavelength, suggesting a dust trap origin (Pinilla et al. 2012; Long et al.
2020). In addition, the Band 3 data shows a bright inner point source,
with a size similar to that of the beam. In the three cases, there is
a tentative faint ring in the outer ring, but a different radius: 1.00,
1.05, and 1.10 arcsec at Band 3, 6, and 7, respectively. This faint
ring was also identified in the radial profile of the dust continuum
observations of LkCa15 at 7 mm (VLA Band Q), located at a radius
of 0.99 arcsec (Sierra et al. 2024).


The adopted geometry of the disc at all wavelengths is fixed to
inc = 50 _._ 1 deg, and PA = 61 _._ 4 deg. These values were inferred from
two independently methodologies using the Band 3 dataset. Firstly,
they were estimated by minimizing the spread of the de-projected
visibilities for circular annuli in the visibility space (e.g., Isella et al.
2019). This method constrained a inclination and position angle of
50 _._ 1 [+] − [0] 0 _[.]_ _._ [4] 2 [deg, 61] _[.]_ [4] [+] − [0] 0 _[.]_ _._ [3] 4 [deg, respectively. Secondly, we fit an ellipse in]
the image plane to a 10 _𝜎_ iso-contour, which follows the brightest ring
at 69 au. This methodology constrained an inclination and position
angle of 49 _._ 1 [+] − [0] 0 _[.]_ _._ [3] 2 [deg, 62] _[.]_ [0] [+] − [0] 0 _[.]_ _._ [3] 3 [deg, respectively. Previous estimates]
of the disc geometry using the Band 6 and 7 data in Long et al.
(2022) and Sierra et al. (2024) have found similar results: 50.2 deg,
61.9 deg and 49.7 deg, 62.1 deg for the inclination and position
angle, respectively. However, we chose to use our Band 3 estimations
because the higher contrast between rings and gaps allows for better
visualization and resolution of the disc geometry, and enables us to
trace emission closer to the midplane.


The offset of the disc centre with respect to the phase centre in the
Band 3 observations is set to ΔRA = 0 mas, ΔDec = 0 mas. However,
we also infer the disc offset by minimizing the imaginary part of the
visibilities (e.g., Isella et al. 2019), obtaining ΔRA = 15 _._ 3 mas and
ΔDec = 12 _._ 9 mas. Alternatively, by fitting the iso-contour ellipse
to the morphology of the main ring, we obtain ΔRA = 15 _._ 7mas
and ΔDec = −6 _._ 9 mas. These offsets are only a factor of 4 and
10 times smaller than the beam size (∼ one pixel size), and do not
provide robust evidence of eccentricity. We decided to fix offset to 0
because this particular value minimize the azimuthal residuals after
subtracting an axi-symmetric model (Section 3.3 and Appendix A),
and double-check that this choice does not affect the conclusions

about the residuals around the 42 au orbit, where the Lagrangian
structures were observed in Band 6 and 7. For the Band 6 and 7 data,
we use the offsets reported in Long et al. (2022).


Table 2 shows a summary of the imaging properties for the three
wavelengths. Note that compared with the maps presented in Long
et al. (2022) at an angular resolution of 50 mas, the maps in this work
are presented at an angular resolution of 60 mas.



**3.2** **Frankenstein fit**


In order to exploit the highest angular resolution from the data, we
extract the disc visibilities at Band 3 using the self-calibrated measurement set and a modified version of the _export_uvtable_ function
in Tazzari (2017), where the baselines are now normalized using the
wavelength of each spectral window and channel. Then we model
the de-projected visibilities using the non-parametric visibility fit in
the Python package Frankenstein (Jennings et al. 2020). The Band
6 and 7 visibilities in Long et al. (2022) are also modelled using the
new geometry constraints, but found negligible differences compared
with the Frankenstein fit in that work.

Figure 2 shows the results from the Frankenstein fit. The left
panel shows the Band 3 data (binned to 3k _𝜆_ and 30k _𝜆_ ) and the
Frankenstein model, which clearly follows the morphology of the
data. The inset panel shows that the Frankenstein fit is sensitive
to the visibility morphology beyond 1M _𝜆_ . The hyper-parameters
used in the Frankenstein fits are _𝛼_ = 1 _._ 3 and _𝑤_ smooth = 10 [−][1],
which are conservative when inferring substructures from the data
Jennings et al. (2020). _𝛼_ mimics a SNR threshold when modelling
the visibilities, and _𝑤_ smooth controls the smoothness to the power
spectrum. Similar to the Frankenstein fit in Long et al. (2022), the
Frankenstein fit is a good representation of the morphology of the
data.

The right panel of Figure 2 shows the brightness temperature
radial profile computed from the Frankenstein fit. The B42, B69,
B101 rings are clearly distinguishable in all cases. In addition, we
determined the gap location based on the Band 3 data with the
best contrast, which are located at 51, and 83 au (we follow the
nomenclature D51, D83 for dark gaps). The brightness temperature
in the inner most region of the Band 3 data is higher than that from
the Band 6 and 7. The emission from this bright region at Band 3 is
consistent with both dust thermal emission and free-free emission,
as explored in Section 3.5. The tentative faint ring identified from
the radial profiles (Figure 1) is also observed in the radial profiles
derived from the Frankenstein fit, with its radial position appearing
to decrease with wavelength.

The inset panel zooms in the radial extent around the rings, and
shows the normalized intensity for the three analysed wavelengths.
It is evident from this plot that the FWHM of the central ring decreases with wavelength, as already suggested from the intensity
profile in the image plane (Figure 1). However, due to differences in
the uv-coverage of each observation, we anticipated differences in
the intrinsic angular resolution from the Frankenstein fit.

The angular resolution from the Frankenstein fits is computed
following the methodology in Sierra et al. (2024), where the reso

MNRAS **000**, 1–16 (2025)

4 _A. Sierra et al._


**Table 2.** Properties of the millimetre continuum images.


ALMA _𝜈_ Baselines robust uv-tapering rms Noise Peak ALMA
Band (GHz) (m-km) (mas × mas; deg) ( _𝜇_ Jy beam [−][1] ) SNR Project Code


3 97.5 15 - 16.2 0.0 27 × 42; 0 5.4 21.3 2022.1.01216.S
6 224.0 15 - 13.9 0.0 12 × 39; 0 9.5 101 Table 1 in Long et al. (2022)
7 340.0 33 - 8.5 0.5 10 × 30; 0 20.1 105 Table 1 in Long et al. (2022)


The robust and uv-tapering for each data set result in a beam size close to 60 mas. A final convolution using the task `imsmooth` in CASA is used to circularize
the beam at 60 mas for all maps.





12


10


8


6


4


2


0





1 _._ 0


0 _._ 5


0 _._ 0


_−_ 0 _._ 5


_−_ 1 _._ 0




|Col1|0 50|100 150 200 Radius [au]|
|---|---|---|
|Band 3<br>50 au<br>0_._0<br>0_._1<br>Intensity [mJy beam_−_1]|Band 7<br>0<br>1<br>2<br>mJy beam_−_1<br>Band 6<br>0_._0<br>0_._5<br>1_._0<br>mJy beam_−_1<br>60 mas<br>B42|Ring?<br>Band 7<br>Band 6<br>Band 3<br>B69<br>B101|
|1_._0<br>0_._5<br>0_._0<br>_−_0_._5<br>_−_1_._0<br>∆RA [arcsec]<br>0_._2<br>0_._4<br>0_._6<br>0_._8<br>1_._0<br>1_._2<br>1_._4<br>Radius [arcsec]|1_._0<br>0_._5<br>0_._0<br>_−_0_._5<br>_−_1_._0<br>∆RA [arcsec]<br>0_._2<br>0_._4<br>0_._6<br>0_._8<br>1_._0<br>1_._2<br>1_._4<br>Radius [arcsec]|1_._0<br>0_._5<br>0_._0<br>_−_0_._5<br>_−_1_._0<br>∆RA [arcsec]<br>0_._2<br>0_._4<br>0_._6<br>0_._8<br>1_._0<br>1_._2<br>1_._4<br>Radius [arcsec]|



**Figure 1.** Left: CLEAN image of the dust continuum data at ALMA Band 3. Middle: CLEAN image of the dust continuum data at ALMA Band 7 (Top) and
Band 6 (Bottom). Right: Brightness temperature radial profile of the dust continuum data. The circular beam of 60 mas for all maps is shown in the bottom left
corner of each panel. The vertical grey dashed lines indicate the positions of the three bright rings (B). The vertical coloured dashed lines indicate the position
of a tentative faint ring.



lution is quantified by fitting the visibilities of an input delta ring at
the same uv-coverage of each observation, and then measuring the
FWHM of the Frankenstein output profile. The angular resolution
from each Frankenstein fit is shown in the bottom of the right panel
of Figure 2. The difference in angular resolution is a combination of
the longest baselines of each dataset and their SNR. Before comparing the morphology inferred at each wavelength, the radial profiles
are convolved using to the lowest angular resolution: 35 mas (5.5 au).
Figure 3 shows the normalized intensity radial profiles from the
clean image (top row) and from the Frankenstein fit (bottom row)
at Band 7, 6 and 3 (from left to right). The angular resolution of the
top panels is 60 mas (9.4 au), while the common angular resolution
of the bottom panels is 35 mas (5.5 au).
The morphology of the radial profiles in each panel is fitted [2] using
five symmetric Gaussian rings (grey lines). This model is chosen to
account for the three main rings, the inner disc, and the extended
emission beyond the outer ring. The free parameters of each Gaussian
ring are the intensity amplitude ( _𝐴_ _𝑖_ ), the width (FWHM _𝑖_ ), and the
radial location of the peak ( _𝑟_ _𝑖_ ). The only exception is the Gaussian


2 This fit is performed directly on the intensity radial profiles, rather than on
the visibilities or the two-dimensional image.


MNRAS **000**, 1–16 (2025)



ring representing the inner disc, where the radial location if fixed
at 0. The fit is performed using _curve_fit_, a non-linear least squares
minimisation method based on minimising the chi-squared statistic,
implemented in the scipy.optimize module (Virtanen et al. 2020).
Initial guess values were introduced based on the known locations of
the rings, their relative flux amplitudes, and an initial FWHM guess
of 0.15 arcsec for all rings. The lower boundary for each parameter
was set to 0, while no upper boundaries were applied. The best fit
from simple model is able to reproduce the intensity radial profiles
for all wavelengths, as shown by the dashed black line of each panel,
which is the sum of the individual Gaussian rings.


Table 3 shows the best fit parameters and their uncertainties for
the Gaussian functions describing the intensity radial profiles, and
the FWHM is plotted in the right panels of Figure 3. The best fit
parameters are similar to those reported in Table 2 of Long et al.
(2022). The FWHM decreases with wavelength for B42, B69, B101,
and seem to follow a linear relation. The slopes of the linear functions
(fitted using _curve_fit_ without any initial guess values or parameter
space boundaries) for the rings B42, B69, B101 in the bottom right
panel (radial profiles from the Frankenstein fit), are 0 _._ 32 ± 0 _._ 02
mas GHz [−][1], 0 _._ 23 ± 0 _._ 03 mas GHz [−][1], and 0 _._ 42 ± 0 _._ 02 mas GHz [−][1],

_High angular resolution evidence of dust traps from deep ALMA Band 3 observations of LkCa15_ 5


Radius [au]
0 50 100 150 200


15 _._ 0



0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8


35 mas 18 mas 18 mas


0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8 1 _._ 0 1 _._ 2 1 _._ 4

Radius [arcsec]



400 Band 7


200


0


150 Band 6


100


50


0


~~_−_~~ 50


0 _._ 01 0 _._ 10 1 _._ 00 10 _._ 00


Baseline [M _λ_ ]



12 _._ 5


10 _._ 0


7 _._ 5


5 _._ 0


2 _._ 5


0 _._ 0


_−_ 2 _._ 5


_−_ 5 _._ 0


## Band 3

1 2 3 4


Model

Binned data (3k _λ_ )
Binned data (30k _λ_ )


0 _._ 01 0 _._ 10 1 _._ 00

Baseline [M _λ_ ]



14


12


10


8


6


4


2


0



**Figure 2.** Left: Real part of the continuum visibilities at ALMA Band 3. The plotted data is binned to 3k _𝜆_ (blue) and 30k _𝜆_ (pink) to best visualize the visibility
morphology. The Frankenstein model is shown as a solid black line. The inset panel shows a zoom in between 1 and 4 M _𝜆_ in linear scale. Middle: Real
part of the dust continuum visibilities at Band 7 (Top) and Band 6 (Bottom). The data is shown as coloured dots, and the Frankenstein model is shown as a
continuum black line. Right: Brightness temperature radial profile computed from Frankenstein fit. The vertical dashed lines show the position of the three
bright rings (B) and dark rings (D). The vertical coloured dashed lines indicate the position of a tentative faint ring. The inset panel shows the intensity radial
profiles normalized to their peak.



respectively. These slopes will be interpreted in the context of dust
trapping efficiency in Section 5.1.


**3.3** **Band 3 azimuthal structures**


Recently, Long et al. (2022) reported azimuthal structures in the
Band 6 and Band 7 dust continuum emission inside the disc cavity
of LkCa15. These azimuthal structures, separated by ∼ 120 deg, are
consistent with the Lagrangian Points of a forming ∼Neptune-mass
planet located at 42 au from the central star, and may be tracing local
dust traps.
We search for similar azimuthal residuals in the Band 3 dust contin
uum data by creating a measurement set of the Band 3 Frankenstein
model, along with a measurement set for the residuals (observed visibilities minus model visibilities). These datasets are generated from
the original measurement sets by replacing the observed visibilities
with either the Frankenstein model or the visibility residuals. They
are then imaged in CASA using the same parameters as in Table 2.
It is known that the residuals can be strongly affected by the
adopted disc geometry parameters (Andrews et al. 2021). As mentioned in Section 3.1, the offset of the disc centre with respect to the
phase centre for the Band 3 data is fixed to ΔRA = ΔDec = 0. This
is because the structures in the residual map are minimized for these
values (Appendix A). Figure 4 shows the clean image map of the
Frankenstein Model and Residual. The model is a good representation of the axi-symmetric structure of LkCa15 at Band 3, as shown
by the low residuals ( _<_ 3 SNR). However, there are some azimuthal
residuals with a SNR above 3 or below -3, specially within the disc
cavity, as shown in the zoom-in residual maps in the middle-right
panel.
We detected a point source at the 42 au orbit with an SNR of 3.5,



which persists independently of the disc offset (Appendix A). This
point source lies near the border of the Northern arc identified in
Long et al. (2022) (Right panel of Figure 4). This point source is
not detected at Band 6 or 7, therefore, its upper limit flux at Band
6 and 7 are the rms values of 9 _._ 5 and 20 _._ 1 _𝜇_ Jy, respectively. For
reference, the circumplanetary disc around PDS70c (scaled to the
LkCa15 distance) is 44 ± 8 _𝜇_ Jy at Band 7 (Benisty et al. 2021), only
∼ 2 the rms of the LkCa15 Band 7 observations. The absence of

Lagrangian structures in Band 3 is discussed in Section 5.
Two planet candidates at orbital distances of 16.5 au and 20.9
au were proposed based on infrared and H _𝛼_ observations (February 7, 2015) reported by Sallum et al. (2015). However, these were
later explained as scattered light (at the same orbital radii) from the
forward-scattering side of the disc, rather than the presence of orbiting companions (Sallum et al. 2023). The apparent position angle of
these structures changes in the opposite direction to the disc rotation.
In our data, we only detect positive residuals with low SNR of 3.0
in the 16.5 au orbit, and SNR of 2.5 in the 20.9 orbit (blue and grey
iso-contours in the middle-right and right panels of Figure 4). When
estimating the Keplerian rotation around the 1.2 M ⊙ star for each
orbit (opposite to the disc rotation), only the outer point source partially matches the expected position. However, given the low SNR,
these detected residuals cannot be considered evidence of continuum

emission associated with these planet candidates.


**3.4** **Dust properties**


The multi-wavelength observations of LkCa15 can be used to constrain the radial profiles of the dust temperature ( _𝑇_ d ), dust surface
density (Σ d ), and maximum grain size ( _𝑎_ max ), as those inferred in
several resolved discs (e.g., Carrasco-González et al. 2019; Macías


MNRAS **000**, 1–16 (2025)

6 _A. Sierra et al._


Band 7


9 _._ 4 au


5 _._ 5 au

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
||9_._4 au||9_._4 au||B42<br>B69<br>B101|B42<br>B69<br>B101|B42<br>B69<br>B101|
|||||||||
||5_._5 au||5_._5 au||100<br>200<br>300|100<br>200<br>300|100<br>200<br>300|
||5_._5 au|||||||
|||||||||



42 69 101

Radius [au]



Band 6


42 69 101

Radius [au]



Band 3


42 69 101

Radius [au]



Band 3 Band 6 Band 7


97 224 340

_ν_ [GHz]



250


200


150


100


200


150


100


50



**Figure 3.** Ring morphology of LkCa15 at ALMA Band 7 (first column), Band 6 (second column), and Band 3 (third column) computed from the azimutally
averaged radial profile in the image plane (first row) and Frankenstein fit (second row). The angular resolution of the top and bottom panels is 60 mas (9.4 au)
and 35 mas (5.5 au), respectively, and it is shown as a horizontal black line in the top left of each panel. The grey lines are the best fit for individual Gaussian
profiles (fitted to the intensity radial profiles), and the thin black line shows their sum. Three vertical dashed lines are included as reference at the ring locations
of 42, 69, and 101 au. The last column shows the Full-Width-Half-Maximum of the three main rings (see marker code in the top right panel) at different
wavelengths.


**Table 3.** Best fit parameters of the Gaussian rings reproducing the intensity radial profiles computed from the image plane (Clean columns) and from Frankenstein
fit (Frankenstein columns)


Clean Frankenstein
Parameter
B7 B6 B3 B7 B6 B3


_𝑟_ [∗] 0 0 0 0 0 0
0
FWHM 0 [au] 12 _._ 6 ± 1 _._ 0 10 _._ 1 ± 0 _._ 7 11 _._ 8 ± 0 _._ 3 21 _._ 2 ± 2 _._ 2 13 _._ 1 ± 1 _._ 3 8 _._ 6 ± 0 _._ 1
log 10 ( _𝐴_ 0 ) −0 _._ 8 ± −2 _._ 1 −1 _._ 2 ± −2 _._ 4 −1 _._ 5 ± −3 _._ 2 9 _._ 2 ± 1 _._ 0 8 _._ 7 ± 1 _._ 0 9 _._ 0 ± 1 _._ 0



.



_𝑟_ 42 [au] 42 _._ 9 ± 0 _._ 4 43 _._ 5 ± 0 _._ 3 44 _._ 4 ± 1 _._ 0 42 _._ 1 ± 0 _._ 2 42 _._ 6 ± 0 _._ 2 40 _._ 2 ± 0 _._ 3
FWHM 42 [au] 24 _._ 1 ± 1 _._ 1 22 _._ 5 ± 0 _._ 9 14 _._ 6 ± 2 _._ 8 22 _._ 2 ± 0 _._ 9 17 _._ 0 ± 0 _._ 6 10 _._ 0 ± 0 _._ 8
log 10 ( _𝐴_ 42 ) −0 _._ 4 ± −1 _._ 9 −0 _._ 8 ± −2 _._ 2 −2 _._ 5 ± −3 _._ 3 9 _._ 7 ± 8 _._ 3 9 _._ 2 ± 7 _._ 7 7 _._ 8 ± 6 _._ 6


_𝑟_ 69 [au] 67 _._ 5 ± 0 _._ 1 68 _._ 0 ± 0 _._ 1 67 _._ 6 ± 0 _._ 1 67 _._ 8 ± 0 _._ 1 68 _._ 2 ± 0 _._ 1 67 _._ 6 ± 0 _._ 1
FWHM 69 [au] 21 _._ 1 ± 0 _._ 2 19 _._ 1 ± 0 _._ 1 17 _._ 1 ± 0 _._ 1 18 _._ 7 ± 0 _._ 1 15 _._ 5 ± 0 _._ 1 10 _._ 1 ± 0 _._ 1
log 10 ( _𝐴_ 69 ) 0 _._ 1 ± −2 _._ 0 −0 _._ 1 ± −2 _._ 2 −1 _._ 1 ± −3 _._ 3 10 _._ 2 ± 8 _._ 2 10 _._ 0 ± 7 _._ 8 9 _._ 1 ± 6 _._ 7


_𝑟_ 101 [au] 97 _._ 9 ± 0 _._ 2 99 _._ 3 ± 0 _._ 1 100 _._ 8 ± 0 _._ 1 98 _._ 6 ± 0 _._ 1 100 _._ 0 ± 0 _._ 1 101 _._ 5 ± 0 _._ 1
FWHM 101 [au] 35 _._ 4 ± 0 _._ 5 29 _._ 9 ± 0 _._ 4 24 _._ 8 ± 0 _._ 5 31 _._ 8 ± 0 _._ 4 24 _._ 8 ± 0 _._ 3 15 _._ 8 ± 0 _._ 2
log 10 ( _𝐴_ 101 ) −0 _._ 1 ± −2 _._ 0 −0 _._ 4 ± −2 _._ 2 −1 _._ 6 ± −3 _._ 3 9 _._ 9 ± 8 _._ 1 9 _._ 6 ± 7 _._ 7 8 _._ 5 ± 6 _._ 6


_𝑟_ ext [au] 92 _._ 5 ± 1 _._ 0 113 _._ 9 ± 3 _._ 2 77 _._ 1 ± 1 _._ 5 97 _._ 3 ± 2 _._ 3 101 _._ 5 ± 1 _._ 4 87 _._ 0 ± 0 _._ 6
FWHM ext [au] 124 _._ 8 ± 1 _._ 6 97 _._ 0 ± 3 _._ 3 150 _._ 0 ± 4 _._ 6 122 _._ 6 ± 2 _._ 1 96 _._ 0 ± 1 _._ 7 109 _._ 8 ± 1 _._ 5
log 10 ( _𝐴_ ext ) −0 _._ 4 ± −2 _._ 0 −1 _._ 0 ± −2 _._ 3 −1 _._ 9 ± −3 _._ 3 9 _._ 6 ± 8 _._ 1 9 _._ 1 ± 7 _._ 7 8 _._ 2 ± 6 _._ 4


(∗) : fixed value. Amplitude units: [ _𝐴_ _𝑖_ from Clean] = mJy beam −1, [ _𝐴_ _𝑖_ from visibilities] = Jy sr −1 .



MNRAS **000**, 1–16 (2025)

0 _._ 5


0 _._ 0


_−_ 0 _._ 5













(July 2023).



et al. 2021; Sierra et al. 2021; Zhang et al. 2023; Carvalho et al.
2024, among others).

The spectral indices between Bands 6 and 7 ( _𝛼_ B6−B7 ) and between
Bands 3 and 6 ( _𝛼_ B3−B6 ), shown in Figure 5, provide an initial insight
into the dust properties around the rings and gaps of LkCa15. The
spectral index _𝛼_ B6−B7 coincides with that computed in Long et al.
(2022). Both radial profiles show three local minima at the location
of the main rings, which might be explained by the emission of
large grain sizes. In addition, the low spectral index ( _𝛼_ B6−B7 ∼ 2)
in B69 and B101 also suggests that emission at the two bands are
likely optically thick. The radial profiles of the spectral indices vary
significantly in the region within the B42 ring, while _𝛼_ B6−B7 tends
to large values (possibly indicating small grain sizes), _𝛼_ B3−B6 tends
to very low values, close to or below 0.

It is known that dust scattering is able to reproduce spectral indices
between ∼ 1 _._ 5 and 2.0 using optically thick emission and high albedo
grain sizes (Liu 2019; Zhu et al. 2019; Sierra & Lizano 2020). Furthermore, the inclusion of vertical temperature structures, scattering,
and high albedo grain sizes can reproduce spectral indices as low as
0.5 using only dust thermal emission (Sierra & Lizano 2020). This
may help explain the physical conditions within the innermost region of LkCa15. However, other non-dust radiative processes, such
as compact free-free emission, could also explain spectral indices
below 2. The region within 0.1 arcsec (approximately three times the
angular resolution), where the spectral index is below 1.5, is shown
as a grey shaded area in Figure 5. We note that the innermost region
(within 1–2 beam sizes) may have larger uncertainties due to angular
resolution limitations or uncertainties in the Frankenstein fitting
process (see Jennings et al. 2022). Consequently, conclusions drawn
for this region should be interpreted with caution. In Section 3.5,
we study the integrated dust continuum fluxes and spectral indices
in the inner disc of LkCa15, and compare them with those of other
transitional discs.

The dust property constraints are computed using the solution for
the radiative transfer equation in Sierra et al. (2019); Sierra & Lizano
(2020), where the contribution of the scattering opacity is taken into



**Figure** **5.** Spectral index radial profile between ALMA Band 6 and 7 (magenta), and ALMA Band 3 and 6 (yellow). The shaded grey within 0.1 arcsec
show the region with possible free-free emission at Band 3. The vertical
dashed lines show the position of the B42, B69, and B101 rings. The beam
size (35 mas, 5.5 au) is shown in the bottom left corner as a horizontal black
line. The shaded magenta and yellow regions indicate 1 _𝜎_ uncertainties. The
vertical bars in the bottom right corner show the error bars from the ALMA
absolute flux calibration uncertainty.


MNRAS **000**, 1–16 (2025)



Radius [au]

0 20 40 60 80 100 120



6


5


4


3





2


1


0


_−_ 1



0 _._ 0 0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8


Radius [arcsec]

8 _A. Sierra et al._


account. We explore the space parameter between 1 K _<_ _𝑇_ d _<_ 300
K, 10 [−][6] g cm [−][2] _<_ Σ d _<_ 10 g cm [−][2], and 10 _𝜇_ m _<_ _𝑎_ max _<_ 30 cm,
and use the Markov chain Monte Carlo (MCMC) implemented in
the Python library emcee (Foreman-Mackey et al. 2013). The _𝜒_ [2] is
defined as in Equation 5 of Sierra et al. (2024), and we also consider
the absolute flux uncertainty for each ALMA Band according to the
ALMA proposer’s guide: 10% for Band 6 and 7, and 5% for Band 3.
The prior for the maximum grain size and dust temperature are
given by a log-uniform distribution, while for the dust temperature we include a prior temperature radial profile given by the
expected temperature from a passively irradiated disc: _𝑇_ prior =
(0 _._ 02 _𝐿_ ∗ /8 _𝜋𝜎_ B _𝑟_ [2] ) [1][/][4], where _𝜎_ B is the Stefan-Boltzmann constant.
We follow the Equation 6 in Sierra et al. (2024) to describe the
prior probability distribution, and use a wide temperature uncertainty around the prior temperature (50 K) to ensure that the prior is
not dominating the posterior probability distribution.
The dust opacities are estimated by two models: the DSHARP
opacities (Birnstiel et al. 2018), and Ricci’s opacities (Ricci et al.
2010). In both cases, we consider sphere grains and use the DSHARP
opacity tools [3] . The DSHARP composition consists on water ice, astronomical silicates, troilite, and refractory organic, with volume
fractions of 36.42%, 16.70%, 2.58%, 44.30% respectively. Meanwhile, the Ricci’s opacity composition consists on water ice, astronomical silicates, carbon grains, and vacuum, with volume fractions
of 42%, 7%, 21%, and 30%, respectively. A full comparison between
these dust opacity models is discussed in Birnstiel et al. (2018). We
assume the particle size distribution follows _𝑛_ ( _𝑎_ ) _𝑑𝑎_ = _𝑎_ [−] _[𝑝]_ _𝑑𝑎_, with
_𝑝_ = 3. This power law lies between the expected values when the
maximum grain size is dominated by fragmentation ( _𝑝_ ∼ 3 _._ 5) and
drift ( _𝑝_ ∼ 2 _._ 5), as shown by the dust evolution models in Birnstiel
et al. (2012).
Finally, the parameter space at each radius is explored using 24
walkers and 10,000 steps. The best fits at each radius are then used to
sample the radial profile of dust properties, taking the median value
at every 1/3 of a resolution element [4] .
The results are shown in Figure 6 for the radial extent where no
free-free contamination is expected ( _>_ 0 _._ 1 arcsec). Local maxima
for the dust surface density and maximum grain size are inferred
at the ring locations in both models; however, their absolute values
differ significantly. For DSHARP opacities, grain sizes on the order
of millimetres are inferred in the gaps, and centimetre-sized grain
sizes in the rings. In contrast, using Ricci’s opacities, grain sizes
below 1 mm are inferred in both the rings and gaps, with oscillations
of tenths of a millimetre between them. This grain size difference has
an important impact on the order of magnitude of the dust surface
density and total dust mass. While the dust mass inferred from the
DSHARP opacities is around 7 _._ 5 × 10 [−][4] M ⊙ (250 M ⊕ ), for Ricci’s
opacities it is an order of magnitude lower: 0 _._ 4 × 10 [−][4] M ⊙ (13 M ⊕ ).
Additional observational constraints from the properties inferred in
both opacity models are discussed in Section 5.3.
The optical depths for both models are estimated and presented
in Figure 7. We remark that the multi-wavelength analysis includes
both absorption and scattering opacities. The contribution of the
absorption-only optical depth is shown as a blue curve, while the
contribution from both absorption and scattering is shown as an
orange curve. The latter is higher for the DSHARP opacity model
because the albedo of mm-cm grain sizes is higher than that of


3 DSHARP opacity tools available at github.com/birnstiel/dsharp_opac
4 A public version of the code is available at
[github.com/anibalsierram/DustProperties](https://github.com/anibalsierram/DustProperties)


MNRAS **000**, 1–16 (2025)



sub-mm grain sizes at millimetre wavelengths. For both models, the
absorption-only optical depth is below 1 everywhere (it is only close
to 1 in the brightest ring at Band 7 for the DSHARP opacity model).
This indicates that the inclusion of scattering opacities has a small
effect on the radiative transfer equation (Sierra & Lizano 2020), and
the results should be similar if the formal solution to the radiative

transfer equation with no scattering is used. The optical depth at
Band 6 from both the DSHARP and Ricci’s opacity model is similar
to that in Facchini et al. (2020), where no-scattering effects and the
temperature of a passively irradiated disc are assumed.


**3.5** **Non-dust emission**


As discussed in the previous Section, free-free emission is expected
in the inner region ( _<_ 0 _._ 1 arcsec) of LkCa15, where the spectral index
between Band 6 and 3 is below ∼ 1 _._ 5 (the minimum spectral index
that can be explained by dust thermal emission and scattering, Sierra
& Lizano 2020). Previous studies of the compact emission in the
centre of the disc around LkCa15 at 7 mm suggest that this emission
is not consistent with the radiation from the stellar photosphere,
but from ionized gas (Isella et al. 2014). This was confirmed by
the analysis of Zapata et al. (2017), where the SED at millimetre
and centimetre wavelengths is described by a two-power law fit,
accounting for two emission processes: dust continuum emission
and free-free emission.

We study the SED of LkCa15 using the integrated fluxes reported
in Zapata et al. (2017), and including the resolved flux constraints in
this work at ALMA Band 7, 6 and 3. The previous flux estimations at
ALMA Band 7 and 6 in Andrews & Williams (2005) were updated
using our data, but they are consistent within the error bars. Additionally, we include the flux constraints from the ALMA Band 9 and
VLA Band Q observations presented in Sierra et al. (2024). In a few
cases (ALMA Band 3, 6, and 7, and VLA Band Q), we also analyse
the fluxes in the inner disc, where most of the free-free emission is
expected.
The total fluxes were computed using the flux curve of growth,
extracting the asymptotic flux at large radii where the integrated
flux oscillates only around the RMS value. In all cases, we use the
intensity radial profiles computed from the image plane to create the
flux curve of growth. We did not use the intensity profiles derived
from the Frankenstein fits, as constraints on the inner region can
have substantial uncertainties (Jennings et al. 2020, 2022). The fluxes
in the inner disc are taken from Isella et al. (2014) and Long et al.
(2022), while the Band 3 flux is estimated from the peak value in
the compact inner disc region, which is consistent with the result
obtained using the `imfit` task in CASA. Table 4 shows a summary
of the fluxes at different bands, and Figure 8 shows the SED computed
from the total fluxes and the inner disc.

The total fluxes clearly follow different power laws below and
above Band Q. The spectral indices increase with wavelength, from
1.7 between Band 9 and Band 7 to 3.5 between Band 3 and Band

Q, as expected for dust continuum emission. However, the spectral
index decreases to 1.8 between Band X and Band Q, suggesting
contributions from sources other than dust thermal emission, such as
free-free or synchrotron emission. The upper-limit detection at Band
C provides a lower limit for the spectral index of 1.3 between Band C
and Band X, suggesting that the free-free emission could be partially
optically thick between such wavelengths.
On the other hand, the spectral indices in the inner disc appear
to follow a different behaviour. The spectral index between Bands 6
and 7 is 2 _._ 4 ± 0 _._ 3 (Long et al. 2022), decreasing to _𝛼_ = 0 _._ 30 ± 0 _._ 37
between Bands 3 and 6. The latter is similar to what is expected

_High angular resolution evidence of dust traps from deep ALMA Band 3 observations of LkCa15_ 9



Radius [au]



|20 40 60|80|
|---|---|
|_M_d = 7_._6|_ ×_ 10_−_4 _M_|
|_M_d = 0_._3|_ ×_ 10_−_4 _M_|


0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8

Radius [arcsec]

























Radius [au]
20 40 60 80 100 120


0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8

Radius [arcsec]



**Figure 6.** Dust properties constraints from the multi-wavelength dust continuum observations of LkCa15 using the DSHARP opacities (Top panels) and Ricci’s
opacities (Bottom panels). The shaded regions show 1 _𝜎_ and 2 _𝜎_ uncertainties. The vertical dashed lines show the position of the ring locations at 42, 69, and

101 au.



Radius [au]



Radius [au]















|Col1|100 120 ]|
|---|---|
|||
|0_._2<br>0_._4<br>Radius [arcs<br><br><br><br><br>       the DSHARP opacities (To<br>   the position of the ring loc<br>50<br>100<br>Radius [au]||
|Band|Band|
|||
|Band|Band|
|||


0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8
Radius [arcsec]



10 _[−]_ [3]





0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8
Radius [arcsec]



0 _._ 2 0 _._ 4 0 _._ 6 0 _._ 8
Radius [arcsec]



**Figure** **7.** Optical depths at ALMA Band 7, 6 and 3 (from left to right) of LkCa15 using the DSHARP opacities (Top panels) and Ricci’s opacities (Bottom
panels). The blue line is the absorption only optical depth, while the orange line is the absorption + scattering optical depth. The shaded region shows 2 _𝜎_
uncertainties. The vertical dashed lines show the position of the ring locations at 42, 69, and 101 au.



**Table 4.** Flux densities at millimetre and centimetre wavelengths of LkCa15.


Frequency ALMA/VLA Total Flux Inner disc

[GHz] Band [mJy] [ _𝜇_ Jy]


689 9 1436.9 ± 72.4     
341 7 418.1 ± 4.7 155.8 ± 7.9

228 6 145.6 ± 4.3 58.6 ± 4.1

107 3 17.0 ± 0.8     
97.5 3 13.2 ± 1.9 45.4 ± 14.0

44.0 Q 0.82 ± 0.18 16.6 ± 3.6

9.10 X 0.045 ± 0.017      
5.00 C ≤ 2 _._ 1E-2      

References: Zapata et al. (2017) for Band X and C. Piétu et al. (2006) for
Band 3 at 107 GHz. Long et al. (2020) for the inner disc at Band 7 and 6, and
Isella et al. (2014) for Band Q. All other fluxes were computed in this work.



from free-free emission, which typically ranges from −0 _._ 1 (at high
frequencies) to 2 _._ 0 (at low frequencies), depending on the optical
depth regime (Rybicki & Lightman 1986).


Recently, Rota et al. (2024) studied the spectral index between
millimetre and centimetre wavelengths in the inner discs of 11 transitional discs, demonstrating that this value is lower ( _<_ 2) compared
to the spectral indices in the outer discs ( _>_ 2). In several discs, the
low spectral indices in the inner disc extend up to Band 6, as also
observed in the case of LkCa15. Rota et al. (2024) suggest that the
difference in spectral indices between the inner and outer discs arises
because the emission in the former includes a significant contribution
from free-free emission associated with ionised jets or disc winds.


We follow the methodology of Rota et al. (2024) to constrain the
upper and lower limits of the spectral index between Band 3 and
the centimetre observations in Band X in the inner disc. Assuming
that the emission in Bands 6 and 7 originates from dust continuum


MNRAS **000**, 1–16 (2025)

10 _A. Sierra et al._


BC BX BQ B3 B6 B7 B9



the evolution of the dust. The initial gas to dust mass ratio is 100
everywhere, and the initial grain sizes follow a Minimum Mass Solar
Nebulae (MMSN) distribution with grain sizes between 0.1 and 1
micrometers. For the inclusion of the rings, we add three Gaussian
rings to the unperturbed gas surface density, this means


Σ g [′] [(] _[𝑟]_ [)] [= Σ] [g] [(] _[𝑟]_ [) × [][1][ +] _[ 𝐺]_ 1 [+] _[ 𝐺]_ 2 [+] _[ 𝐺]_ 3 []] _[,]_ (1)


where



10 [3]


10 [2]


10 [1]


10 [0]


10 _[−]_ [1]











�



_,_ (2)



_𝐺_ _𝑖_ ( _𝑟_ ) = _𝐴_ _𝑖_ exp



�



− [(] _[𝑟]_ [−] _[𝑟]_ _[𝑖,]_ _[𝑝]_ [)] [2]



2 _𝑤_ [2]
_𝑖_



� 2− _𝛾_ [�]



_𝑟_

�− � _𝑅_ _𝑐_



_𝑟_ − _𝛾_

exp

� _𝑅_ _𝑐_ �



10 _[−]_ [2]

|Col1|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
||_α_ = 1_._7<br>_α_ = 2_._5<br>_α_ = 2_._9<br>_α_ = 3_._5<br>_α_ = 1_._8<br>_α >_ 1_._3<br>_α_ = 2_._4<br>_α_ = 0_._0<br>_α_ = 0_._3<br>Total Flux<br>Inner Disc|_α_ = 1_._7<br>_α_ = 2_._5<br>_α_ = 2_._9<br>_α_ = 3_._5<br>_α_ = 1_._8<br>_α >_ 1_._3<br>_α_ = 2_._4<br>_α_ = 0_._0<br>_α_ = 0_._3<br>Total Flux<br>Inner Disc|_α_ = 1_._7<br>_α_ = 2_._5<br>_α_ = 2_._9<br>_α_ = 3_._5<br>_α_ = 1_._8<br>_α >_ 1_._3<br>_α_ = 2_._4<br>_α_ = 0_._0<br>_α_ = 0_._3<br>Total Flux<br>Inner Disc|_α_ = 1_._7<br>_α_ = 2_._5<br>_α_ = 2_._9<br>_α_ = 3_._5<br>_α_ = 1_._8<br>_α >_ 1_._3<br>_α_ = 2_._4<br>_α_ = 0_._0<br>_α_ = 0_._3<br>Total Flux<br>Inner Disc|_α_ = 1_._7<br>_α_ = 2_._5<br>_α_ = 2_._9<br>_α_ = 3_._5<br>_α_ = 1_._8<br>_α >_ 1_._3<br>_α_ = 2_._4<br>_α_ = 0_._0<br>_α_ = 0_._3<br>Total Flux<br>Inner Disc|_α_ = 1_._7<br>_α_ = 2_._5<br>_α_ = 2_._9<br>_α_ = 3_._5<br>_α_ = 1_._8<br>_α >_ 1_._3<br>_α_ = 2_._4<br>_α_ = 0_._0<br>_α_ = 0_._3<br>Total Flux<br>Inner Disc|_α_ = 1_._7<br>_α_ = 2_._5<br>_α_ = 2_._9<br>_α_ = 3_._5<br>_α_ = 1_._8<br>_α >_ 1_._3<br>_α_ = 2_._4<br>_α_ = 0_._0<br>_α_ = 0_._3<br>Total Flux<br>Inner Disc|_α_ = 1_._7<br>_α_ = 2_._5<br>_α_ = 2_._9<br>_α_ = 3_._5<br>_α_ = 1_._8<br>_α >_ 1_._3<br>_α_ = 2_._4<br>_α_ = 0_._0<br>_α_ = 0_._3<br>Total Flux<br>Inner Disc|_α_ = 1_._7<br>_α_ = 2_._5<br>_α_ = 2_._9<br>_α_ = 3_._5<br>_α_ = 1_._8<br>_α >_ 1_._3<br>_α_ = 2_._4<br>_α_ = 0_._0<br>_α_ = 0_._3<br>Total Flux<br>Inner Disc|
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||



10 [1] 10 [2] 10 [3]


Frequency [GHz]


**Figure 8.** Spectral Energy Distribution (SED) of LkCa15 at millimetre and
centimetre wavelengths computed from the total flux (blue), and inner disc
(orange). The triangle at Band C represents the upper limit detection at that
frequency. The faint orange line between Bands 6 and 3 in the inner disc
represents the extrapolated flux using the spectral index between Bands 6 and
7. The spectral indices between consecutive bands are indicated in each case.


emission, the extrapolated dust continuum flux in Band 3 is approximately 8 _._ 6 _𝜇_ Jy, which represents ∼ 19% of the inner disc flux in
Band 3. Consequently, the estimated free-free emission in the inner
disc at Band 3 is ∼ 36 _._ 8 _𝜇_ Jy, and the lower limit for the spectral index
between Band 3 and Band X (where the total flux is presumably
dominated by the inner disc) is _𝛼_ extrap = −0 _._ 1. The upper limit is
calculated by determining the spectral index without subtracting the
dust continuum contribution in Band 3, yielding an upper limit of
_𝛼_ 3mm−3cm = 0 _._ 0
These spectral indices constraints are similar as those found for
other transitional discs analysed in Rota et al. (2024). In particular,
they are similar to the constraints in GG Tau, HD 100546, and HD
142527, where the emission from the inner disc is also detected in
both Bands 6 and 7. Rota et al. (2024) also found that the ionised

mass loss rate and accretion rate onto the central star of LkCa15

follow the same relation as those of the other discs in their sample,
establishing LkCa15 as another source where the origin of free-free
emission can be attributed to an ionised jet. Suggestive evidence of
unresolved free-free emission in the inner disc at Band 3 has also

been recently reported for the disc around PDS 70 (Doi et al. 2024),
where the spectral index between Bands 7 and 3 is low ( _𝛼<_ 2).


**4** **DUST EVOLUTION MODELS FOR LKCA15**


Thanks to the wealth of (sub-) millimetre data available for LkCa15,
this target is ideal to test dust evolution models, in order to potentially
constrain key parameters of disc evolution, such as disc turbulence.
For this aim, we perform tailored models for the LkCa15 disc,
using `Dustpy` version 1.0.5 (Stammler & Birnstiel 2022). `Dustpy`
simultaneously calculates the dust growth processes (dust coagulation, fragmentation, erosion) with the dynamics of the particles,
including drag (that leads to radial drift) and diffusion. For these
models, we assume a stellar mass of 1 _𝑀_ ⊙ and we do not model the
evolution of the gas, meaning that the gas remains constant during


MNRAS **000**, 1–16 (2025)



Σ g ( _𝑟_ ) = Σ 0



_,_ (3)



_𝛾_ = 1, _𝑅_ _𝑐_ = 160 au, and Σ 0 is taken such that the disc mass is 0 _._ 1 _𝑀_ ⊙
(Jin et al. 2019). The radial grid ranges from 1 to 300 au, and it is
logarithmically spaced in 300 cells. The rings are centred at _𝑟_ _𝑝,_ 1 =
42 au, _𝑟_ _𝑝,_ 2 = 69 au, _𝑟_ _𝑝,_ 3 = 101 au; as constrained from observations.
The width of the Gaussian perturbation _𝑤_ _𝑖_ is the local scale height at
each of the peak locations. Based on the contrast between the three
rings, the amplitudes of the perturbations are assumed to be _𝐴_ 1 = 1,
_𝐴_ 2 = 5, and _𝐴_ 3 = 3.
As rings are perturbations of the gas surface density, this translates
to pressure bumps (Pinilla et al. 2012). Inside pressure bumps, the
radial drift is reduced and particles get trap. As a consequence, the
maximum grain size within the rings is set by the fragmentation
barrier (Birnstiel et al. 2012), which is given by



_𝑎_ frag = 3 [2] _𝜋_ _𝜌_ Σ _𝑠𝑔_ _𝛼_



_𝑣_ [2]
frag
_,_ (4)
_𝑐_ [2] _𝑠_



where _𝜌_ _𝑠_ is the volume density of the particles, which we take either to be 1.6 or 0.85 g cm [−][3] depending on the opacities that are
assumed afterwards for the radiative transfer models (DSHARP or
Ricci’s opacities, respectively), _𝛼_ is the disc viscosity (Shakura &
Sunyaev 1973) that controls the dust diffusion, turbulence, and dust
settling in the dust evolution models (Pinilla et al. 2021), and _𝑣_ frag
is the velocity threshold for which particles fragment (fragmentation velocity). The last two parameters, _𝛼_ and _𝑣_ frag are still highly
unconstrained from observations. Detailed analysis of dust distribution of a handful of highly-inclined discs suggest that the degree of
dust settling is high, implying low values of _𝛼_ ≲ 10 [−][4] (Villenave
et al. 2022; Rosotti 2023). The maximum grain size obtained from
the multi-wavelength analysis presented in Section 3.4 is around
1-2 cm and 0.04-0.06 cm within the rings using the DSHARP or
Ricci opacities, respectively. Base on these constraints, we assume
two values of _𝑣_ frag = 1 _,_ 10 m s [−][1] and two values of _𝛼_ = 10 [−][4] _,_ 10 [−][3],
which gives values of _𝑎_ frag similar to those computed from the multiwavelength analysis. We discard the combination of _𝑣_ frag = 10 m s [−][1]

and _𝛼_ = 10 [−][4], as this leads to _𝑎_ frag within in the rings higher than
100 cm, contradicting the observations. Previous dust evolution models have demonstrated that in such cases, grains grow very efficient to
boulders within the rings, decreasing the observed millimetre fluxes
and underestimating values of typical millimetre fluxes of protoplanetary discs (Pinilla et al. 2020).
Figure 9 shows the dust density distributions after 1 Myr of evolution, as a function of grain size, and distance from the star, for the
three cases considered in this work (see model number in the top of
each panel). This figure shows how different values of _𝑣_ frag and _𝛼_
lead to different maximum grain size across the disc, and hence on
different levels of dust trapping. For example, _𝑣_ frag = 1 m s [−][1] and

_High angular resolution evidence of dust traps from deep ALMA Band 3 observations of LkCa15_ 11


log 10 (Surface density [g cm _[−]_ [2] ])

_−_ 9 _._ 5 _−_ 8 _._ 5 _−_ 7 _._ 5 _−_ 6 _._ 5 _−_ 5 _._ 5 _−_ 4 _._ 5 _−_ 3 _._ 5 _−_ 2 _._ 5 _−_ 1 _._ 5 _−_ 0 _._ 5



10 [0] 10 [1] 10 [2]


Radius [au]



10 [1] 10 [2]


Radius [au]





10 [1]


10 [0]


10 _[−]_ [1]


10 _[−]_ [2]


10 _[−]_ [3]


10 _[−]_ [4]


10 _[−]_ [5]





10 [0] 10 [1] 10 [2]


Radius [au]



**Figure** **9.** Dust evolution models for the disc around LkCa15. The left, middle, and right panel show the dust surface density after 1 Myrs of evolution for
different velocity fragmentation and viscosity (top legend in each panel).



_𝛼_ = 10 [−][3] is the case where _𝑎_ frag is the lowest, implying less trapping
within the rings and more dust diffusion across the gaps. This implies
less contrast in the dust density between rings and gaps. When _𝑎_ frag
is higher, the trapping is more efficient and the contrast between rings
and gaps increases.

To test whether the observations favour any of the explored values
of _𝑎_ frag and _𝑣_ frag, we combine the results from dust evolution models
with radiative transfer calculations to create synthetic images using
`RADMC3D` (Dullemond et al. 2012), as has been done in several previous studies (e.g., Pohl et al. 2017; Pinilla et al. 2021, 2024). The
dust volume density input into `RADMC3D` accounts for the degree of
settling for different values of _𝛼_ . In these models, the stellar temperature is assumed to be 5772 K. For our calculations, we assume
the same radial grid than the dust evolution models and a grid in the
vertical direction that has 64 cells. The number of photons is set to
1 × 10 [7], with an additional 5 × 10 [6] scattering photons. From these
simulations, we create synthetic images at the same wavelengths as
the observations of LkCa15 and convolve them to match the same an
gular resolution (60 mas). For each of the three models, the DSHARP
and Ricci’s dust opacities are explored.

Left images in Figure 10 show the synthetic images for the
DSHARP opacities, which match the observations more closely
compared to Ricci’s (shown in Appendix B). The disc within 25
au is removed in all cases to better visualize the disc morphology
around the rings. The right panels compare the radial profiles of the
brightness temperature and spectral index for each model with the
observations. Model 2 ( _𝛼_ = 10 [−][4], _𝑣_ frag = 1 m s [−][1] ) and 3 ( _𝛼_ = 10 [−][3],
_𝑣_ frag = 10 m s [−][1] ) seem to best match the brightness radial profiles
and spectral indices, while Model 1 ( _𝛼_ = 10 [−][3], _𝑣_ frag = 1 m s [−][1] ) is
not able to reproduce the high contrasts between rings and gaps.

As an additional test, we compute the intensity ratio between
the ring at 69 au and the gaps at 51 au and 83 au (I(B69)/I(D51),
I(B69)/I(D83)), and between the ring at 101 au and the gap at 83
au (I(B101)/I(D83)) for all models, and they are compared with the
observations. These values are summarized in Table 5. This table

also includes the fit to the FWHM of each ring between 25 au and
125 au, following the same methodology as in Figure 3. Additionally,



we include the constraints to the integrated spectral index for each
model, and the total flux in Band Q and Band 9 estimated from the
`RADMC3D` maps at these wavelengths. We highlight in bold the model
that is closest to the observed value for each parameter, which, in
most cases, corresponds to Model 3 ( _𝛼_ = 10 [−][3], _𝑣_ _𝑓_ = 10 m s [−][1] ).
We remark that the maximum grain size in our modelling is set
by the fragmentation limit (Birnstiel et al. 2012), which is directly
proportional to the assumed gas surface density. Therefore, if the
gas mass would be one order of magnitude lower (as estimated by
Sturm et al. 2023), the maximum grain size would be one order of
magnitude lower, favouring models with lower turbulence and higher
fragmentation velocities. Recently, as part of the exoALMA project,
the gas disc mass of LkCa15 was modelled by simultaneously fitting
the [12] CO and [13] CO rotation curves (Longarini et al. submitted), and
it is found to be in agreement with the estimate in Jin et al. (2019),
supporting our specific choice of the gas disc mass.


**5** **DISCUSSION**


**5.1** **No Lagrangian structures in Band 3**


No azimuthal asymmetries above 3 _𝜎_ were detected in the Band
3 dust continuum observations at the locations of the Lagrangian
structures observed in Band 6 and 7 (Section 3.3). These structures
(a clump and an arc) were detected at a 10 _𝜎_ significance level in
both Band 6 and 7 (Long et al. 2022). Extrapolating the clump and
arc fluxes to 97.5 GHz using a spectral index of 3.0 (computed at
the asymmetry locations), results in an expected intensity of ∼ 5 _𝜇_ Jy
beam [−][1] . This value is approximately equal to the rms noise of the
Band 3 observations (Table 1), making it difficult to distinguish them
from thermal noise.

The non-detection of structures around the Lagrangian points in
Band 3 provides insights into dust trapping at the Lagrangian points.
In Band 3, it is expected that observations are more sensitive to larger
particles than in Band 6. If dust trapping is happening in the Lagragian points, those large grains would be bright in Band 3, as predicted
by numerical simulations (Drażkowska et al. 2019; Montesinos et al.


MNRAS **000**, 1–16 (2025)

12 _A. Sierra et al._


Band 3



Band 6



Band 7



Brightness Temperature [K]



Spectral Index










|Col1|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|Model 1<br>0_._00<br>0_._02<br>0_._04|Model 1<br>0_._0<br>0_._5|Model 1<br>0<br>2|2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5|Band 3<br>Band 6<br>Band 7<br>2_._0<br>2_._5<br>3_._0<br>3_._5<br>4_._0<br>4_._5|
|Model 2<br>0_._000<br>0_._025<br>0_._050|Model 2<br>0_._0<br>0_._5|Model 2<br>0<br>1|2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5<br>S<br>|imulations<br>Observations<br>2_._0<br>2_._5<br>3_._0<br>3_._5<br>4_._0<br>4_._5<br>Sim<br>Obs|
||||||
|Model 3<br>0_._00<br>0_._05|Model 3<br>0_._0<br>0_._5<br>1_._0|Model 3<br>0<br>1<br>2|2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5|2_._0<br>2_._5<br>3_._0<br>3_._5<br>4_._0<br>4_._5|
||||||



25 50 75 100 125


Radius [au]



1 _._ 0


0 _._ 5


0 _._ 0


_−_ 0 _._ 5


_−_ 1 _._ 0



1 _._ 0 0 _._ 5 0 _._ 0 _−_ 0 _._ 5 _−_ 1 _._ 0


∆RA [arcsec]



25 50 75 100 125


Radius [au]



**Figure 10.** Simulated dust continuum emission emission for the dust evolution model 1, 2 and 3 (from top to bottom). The images on the left show the `RADMC3D`
emission maps at Band 3, 6, and 7 (from left to right). The units of the colour bars in all cases are mJy beam [−][1], and the ellipses show the radial position of the
three bright rings at 42, 69, and 101 au for reference. The right panels show the radial profile of the brightness temperature and spectral index for each simulation
(solid lines) and those from the observations (shared areas and dashed lines). The angular resolution in all cases is 60 mas, the same as the observational data in
Figure 1.


**Table 5.** disc morphology properties of the `RADMC3D` simulations in Figure 10.


Observed Model 1 Model 2 Model 3
Parameter
B7 B6 B3 B7 B6 B3 B7 B6 B3 B7 B6 B3


I(B69)/I(D51) 2.2 3.7 4.4 0.6 0.4 0.4 **2.3** **3.4** 6.5 1.6 2.2 **4.5**
I(B69)/I(D83) 1.6 2.1 2.9 **1.4** 1.2 **0.9** 3.4 5.0 9.4 2.0 **2.5** 5.3
I(B101)/I(D83) 1.0 1.3 1.4 0.5 0.5 0.5 1.7 2.1 2.2 **1.0** **1.2** **2.1**
FWHM 42 [au] 24.1 ± 1.1 22.5 ± 0.9 14.6 ± 2.8    -    -    - 10.8 10.9 10.8 **23.3** **16.8** **14.9**
FWHM 69 [au] 21.1 ± 0.2 19.1 ± 0.1 17.1 ± 0.1    -    -    - 16.4 15.5 14.4 **25.3** **18.9** **15.5**
FWHM 101 [au] 35.4 ± 0.5 29.9 ± 0.4 24.8 ± 0.5    -    -    - **23.9** 21.5 **19.9** 18.1 **23.4** 18.6


_𝛼_ B3−B6 (25-125 au) 3 _._ 0 ± 0 _._ 9 3.7 3.7 **3.6**
_𝛼_ B6−B7 (25-125 au) 2 _._ 5 ± 0 _._ 4 3.2 **2.7** **2.7**


Flux BQ (25-125 au) [mJy] 0.72 ± 0.07 0.08 0.12 **0.43**
Flux B9 (25-125 au) [Jy] 1.22 ± 0.24 **1.13** 1.04 1.45


Model 1: _𝛼_ = 10 [−][3], _𝑣_ frag = 1 m s [−][1] . Model 2: _𝛼_ = 10 [−][4], _𝑣_ frag = 1 m s [−][1] . Model 3: _𝛼_ = 10 [−][3], _𝑣_ frag = 10 m s [−][1] . Bold text is used to highlight the model that is
closest to the observed parameters. The FWHMs are not reported for Model 1 because a clear ring-like morphology is not present in the intensity profiles.



2020). However, since this is not observed with the current sensitivity, it is likely that only smaller grains (sub-millimetre-sized), which
are bright in ALMA Bands 6 and 7 (Draine 2006), are dominating the
emission of the potential Lagrangian points. A possible explanation
for the absence of large grain sizes at the Lagrangian structures could


MNRAS **000**, 1–16 (2025)



be the filtering of the large dust grains by the dust trap at 69 au or the
influence of the potential dust trap at 42 au, which might be stopping
the reservoir of large grains moving to the Lagrangian points.

_High angular resolution evidence of dust traps from deep ALMA Band 3 observations of LkCa15_ 13



**5.2** **Dust trap efficiency**


The efficiency of dust trapping in ringed protoplanetary discs has
been studied by Rosotti et al. (2020) and Dullemond et al. (2018).
In the former, gas dynamics information is needed to constrain dust
parameters as the Stokes parameter or the _𝛼_ turbulent parameter.
In the latter, only dust continuum emission, as that in this work, is
needed to study the dust trap mechanism.
As mentioned in Dullemond et al. (2018), the width of the radial
pressure bump ( _𝑤_ _𝑝_ ) originating the dust traps cannot be smaller
than the width of the dust ring ( _𝑤_ d ) or the local thermal pressure scale height ( _ℎ_ _𝑝_ ), i.e., _𝑤_ _𝑝,_ min = max( _𝑤_ d _, ℎ_ _𝑝_ ). For this reason, we use the Band 3 radial profiles inferred from the Frankenstein fit as reference, as they exhibit the narrowest dust continuum distribution among the observations in this work (Figure 3).
The widths _𝑤_ d for each ring are the FWHM in Table 3, and they
are deconvolved using their angular resolution (5.5 au) as follows:



_𝑤_ _𝑑_ = ~~√~~



FWHM [2] −(5 _._ 5au) [2] /(2 ~~√~~



_𝑤_ _𝑑_ = FWHM −(5 _._ 5au) /(2 ~~√~~ 2 ln(2)). The factor in the denom
inator consistently converts the FWHM to the standard deviation, as
originally derived in Dullemond et al. (2018). On the other hand, the
width of the radial pressure bump cannot exceed the radial separation
of the rings (as defined in Dullemond et al. 2018). The local pressure
scale height is estimated from the temperature of a passively irradiated disc and assuming hydrostatic equilibrium (Equations 5 and 6
in Dullemond et al. 2018).
Constraints on the gas surface density at the location of the rings
are also necessary to study the dust trap mechanism. Unfortunately, a
constant gas-to-dust ratio cannot be used, as the dust trapping mechanism is expected to concentrate dust grains in the rings and decrease
the local gas-to-dust ratio. Low gas-to-dust ratios in the rings of
LkCa15 have been inferred by Sturm et al. (2023) using observations of several CO isotopologues and continuum data. Additionally,
Sturm et al. (2023) found gas mass estimates that are one order of
magnitude lower than the results in Jin et al. (2019). Therefore, different gas mass estimates may influence the conclusions regarding
the dust trap mechanism.
Fortunately, Dullemond et al. (2018) was able to study the dust trap
mechanism by estimating upper and lower limits to the gas surface
density using only physical constraints, independently of a specific
gas surface density measurement. The upper limit for the gas surface
density is given requiring gravitationally stability (Toomre parameter
_>_ 2), while the lower limit is given by the local dust surface density
(i.e. it requires a gas-to-dust ratio larger than one). The results in
both Jin et al. (2019) and Sturm et al. (2023) fall within these limits.
The dust surface density constraints are taken from those computed
in Section 3.4.

These constraints are summarized in Table 6. where we also in
clude the constraints to the maximum grain size in Figure 6, and to
the minimum and maximum Stokes number in the Epstein regime
(Epstein 1924). The minimum and maximum value for the latter is
estimated using the maximum and minimum gas surface density,
respectively. The bulk densities for the DSHARP and Ricci’s dust
grain compositions are 1.6 and 0.85 g cm [−][3], respectively.
The local thermal scale heights (estimated from the temperature
of a passively irradiated disc) at B42, B69 and B101 are _ℎ_ _𝑝_ = 2.2,
4.0, 6.5 au, respectively, while the dust widths at Band 3 are _𝑤_ _𝑑_ =
3.5, 3.6, 6.3 au, respectively. Except for B42, the width of the dust
rings are narrower than the scale heights, which can be interpreted as
evidence that dust trapping must have taken place in B69 and B101
(Dullemond et al. 2018). The B42 ring does not show a peak in dust
surface density or maximum grain size either (Figure 6), leaving its
origin still unclear.



**Table 6.** Constraints on dust traps in the rings of LkCa15.


DSHARP Opacities Ricci’s Opacities
Parameter
B42 B69 B101 B42 B69 B101


_𝑤_ _𝑝,_ min [au] 3.5 4.0 6.5 3.5 4.0 6.5
_𝑤_ _𝑝,_ max [au] 18 36 36 18 36 36
Σ g _,_ min [g cm [−][2] ] 3.0E-2 6.8E-1 1.7E-1 1.7E-3 1.9E-2 8.2E-3
Σ g _,_ max [g cm [−][2] ] 5.4E1 2.3E1 1.2E1 5.4E1 2.3E1 1.2E1
_𝑎_ max [cm] 4.5E-1 5.9E-1 8.3E-1 3.7E-2 5.8E-2 4.0E-2
St min 2.2E-2 6.7E-2 1.8E-1 9.2E-4 3.4E-3 4.4E-3
St max 3.9E1 2.3E0 1.3E1 2.9E1 4.1E0 6.5E0
( _𝛼_ turb /St) min 3.9E-2 1.0E-2 3.2E-2 1.1E-1 2.9E-2 9.4E-2
_𝛼_ turb _,_ min 8.6E-4 6.7E-4 5.7E-3 1.0E-4 9.9E-5 4.1E-4


The upper and lower limit of the ratio _𝛼_ turb /St can now be estimated using the Equation 21 in Dullemond et al. (2018) and the
lower and upper limit for _𝑤_ _𝑝_, with a Schmidt number = 1 (Johansen
& Klahr 2005). Finally, lower limits for _𝛼_ turb can also be estimated
using the lower limit on the the Stokes number. All the parameters are
reported in Table 6. The lower limits for _𝛼_ turb are within the typical
values found in Pinte et al. (2016); Flaherty et al. (2018); Dullemond
et al. (2018), which lies around _𝛼_ turb ∼ 10 [−][4] _,_ 10 [−][3] .
Note that the possible Stokes number values at B101 tend to be
higher than those at B69, which mainly occurs due to the lower gas
surface densities in the outer ring. However, although higher Stokes
numbers are allowed in the outer ring, both the dust surface density
and maximum grain size inferred from the multi-wavelength analysis
(Figure 6) in B69 are higher than those at B101. Furthermore, similar
results are obtained from the three dust evolution models, as shown
in Figure 9.
All the observational and model constraints indicate that higher
dust surface densities and grain sizes are present in B69 compared
with those in B101. The fact that the slope of the FWHM of the
B101 ring decreases faster than in B69 (Figure 3) can be associated
to an optically depth effect. We remark that interpreting a higher
slope as evidence of higher dust trapping efficiency is only valid
in the optically thin regime, where the dust rings directly trace the
mass distribution of solids. Optical depth effects may contribute to
broadening the observed dust ring width, as in the case of the B69
ring (Figure 7).
The radial position of the B101 ring differs slightly between Bands
7, 6, and 3 (Figures 1, 2). Although the peak position appears to
increase with wavelength, the difference between the radial position
of B101 at Bands 7 and 3 is only about 3 au (Table 3). This difference
is smaller than the angular resolution and limits robust conclusions
about the origin of the apparent shift, which could be attributed to
radial drift and/or optical depth effects.
The hydrodynamical simulations by Facchini et al. (2020) suggest
that the rings in LkCa15 can be attributed to the presence of an
embedded planet, though their specific appearance and the number
of rings are highly sensitive to the disc’s thermodynamics. This
potentially can also explain the tentative faint ring observed beyond
1 arcsec (157.2 au) in Band 3, 6, 7 (Figures 1, 2), and Band Q (Sierra
et al. 2024).


**5.3** **Dust opacities**


Dust opacity significantly influences the derived properties of protoplanetary discs. Variations in assumptions about their composition
(e.g., Birnstiel et al. 2018), grain sizes (e.g., Draine 2006), porosity
(e.g., Kirchschlager et al. 2019; Zhang et al. 2023; Liu et al. 2024),


MNRAS **000**, 1–16 (2025)

14 _A. Sierra et al._



_λ_ = 1 _._ 3 mm





0 _._ 8


0 _._ 6


0 _._ 4


0 _._ 2


0 _._ 0



10 _[−]_ [1]


10 _[−]_ [2]









**Figure** **11.** Dust opacity and albedo at _𝜆_ = 1 _._ 3 mm for the DSHARP (red)
and Ricci (blue) composition. The solid, dashed, and dotted lines show the
absorption, scattering, and albedo coefficients, respectively.


shape (e.g., Tazaki & Tanaka 2018; Kirchschlager & Bertrang 2020),
among other factors, can result in absorption and scattering opacities that differ by orders of magnitude, as well as varied spectral
properties, which directly impact the estimation of dust mass.
In this work we tested the DSHARP and Ricci’s opacities (Figure
11), two of the most widely used dust opacities in protoplanetary disc
studies. Although both compositions contain water ices and astronomical silicates, the inclusion of carbon grains in Ricci’s opacities
(instead of refractory organics in DSHARP) increases absorption
opacity by an order of magnitude at millimetre wavelengths and reduces the albedo. This leads to less massive discs when inferring dust
surface density from multi-wavelength observations (Figure 6), or increases total intensity for a fixed dust surface density in simulations
(Figure 10 and B1).
The gas-to-dust ratio for the DSHARP and Ricci’s opacity models
is approximately 132 and 2500, respectively, (assuming a gas mass
of 0.1 M ⊙, Jin et al. 2019). This ratio is particularly high for Ricci’s
opacities, while it falls within the typical expected values for the
Interstellar Medium (ISM) and protoplanetary discs (Ansdell et al.
2016; Zhang et al. 2021) for the DSHARP opacities. On the other
hand, the small grain sizes and dust surface densities derived from
Ricci’s opacities have significant implications for the expected emission at very long wavelengths. Specifically, the flux of LkCa15 at
VLA Band Q (44 GHz) [5] between 25 au and 125 au is approximately
0.72 mJy. The expected flux at Band Q (within the same radial extent)
based on the inferred dust properties shown in Figure 6 is ∼ 0.70 mJy
and 0.13 mJy for the DSHARP and Ricci’s opacity models, respectively. The latter value is particularly low compared to the observed
flux, likely due to a combination of low dust surface densities and the
reduced opacity of sub-mm grain sizes at _𝜆_ = 7 mm (Draine 2006).


**6** **CONCLUSIONS**


The new Band 3 dust continuum observations ( _𝜆_ = 3 mm) of the disc
around LkCa15 offer unprecedented insights into the distribution of


5 The disc was observed as part of the Disks@EVLA Collaboration,
[https://safe.nrao.edu/evla/disks](https://safe.nrao.edu/evla/disks)


MNRAS **000**, 1–16 (2025)



solids within its ring structures. The Band 3 data were observed at
the highest angular resolution of ALMA’s capabilities, achieving a
resolution of 60 mas (9.4 au) when imaging with CASA, or 35 mas
(5.5 au) when modelling the visibilities.
The bright rings B42, B69, and B101, previously resolved at
shorter wavelengths, are confirmed, revealing deeper gaps and narrower ring structures compared to the dust continuum observations
at Band 6 ( _𝜆_ = 1 _._ 3 mm) and Band 7 ( _𝜆_ = 0 _._ 88 mm). The width of
the B42, B69, and B101 rings increases with frequency at rates of
0.31, 0.22, and 0.41 mas GHz [−][1], respectively, consistent with signatures predicted by dust trap models. Additionally, the Band 3 data
reveals a bright compact emission in the inner disc, which given its
low spectral indices between 1.3 and 3 mm, and 3 mm and 3 cm
( _𝛼_ 1 _._ 3−3mm = 0 _._ 30 ± 0 _._ 37, _𝛼_ 3mm−3m = [−0 _._ 1 _,_ 0 _._ 0]), may be tracing
a combination of dust and free-free emission. The origin of the latter
is consistent with an ionised jet, as reported by Rota et al. (2024)
in the inner discs of 10 transitional discs with similar spectral index
properties.
Although most of the dust continuum data at Band 3 looks axisymmetric, there are some azimuthal residuals around the ∼ 3 _𝜎_ level.

One of these residuals is detected with an SNR of 3.5 in the 42 au

orbit, near the boundary of the Northern arc identified in Bands 7 and
6 by Long et al. (2022). However, no Band 3 azimuthal asymmetries
are detected at the Lagrangian structures observed in Bands 7 and
6. On the other hand, two point sources were also identified with an
SNR of 2.5 in the orbits at 16.5 and 20.9 au, where two possible planets were proposed based on H _𝛼_ observations in Sallum et al. (2015),
although these were later explained by scattered light (Sallum et al.
2023). The position of the outer point source at 20.9 au aligns with
the expected orbital motion of these structures around a 1.2 M ⊙ star.
The resolved multi-wavelength modelling of the dust continuum
emission at Bands 3, 6, and 7 is used to constrain the radial profiles of
dust temperature, dust surface density, and maximum grain size. The
B69 and B101 rings show peak values for dust surface density and
maximum grain size when using DSHARP or Ricci’s opacities, confirming the signatures predicted by dust trapping models. Although
the width of the B42 ring increases with frequency, there is not a
robust evidence of a dust trap when modelling the multi-wavelength
data, and its origin remains unclear. These dust trap signatures at
B69 and B101 are confirmed using the analytical prescription tests
in Dullemond et al. (2018).
The dust surface density and maximum grain size computed using DSHARP opacities are an order of magnitude larger than those
obtained from Ricci’s opacities. This directly impacts the total dust
mass, which is estimated at 7 _._ 6 × 10 [−][4] M ⊙ for DSHARP opacities
and 0 _._ 3 × 10 [−][4] M ⊙ for Ricci’s opacities. These dust masses are factors of 132 and 2500 smaller than previous estimates of the total gas
mass (0.1 M ⊙, Jin et al. 2019), suggesting that properties inferred
from the DSHARP opacities are more consistent with previous constraints on the gas-to-dust mass ratio in several protoplanetary discs
(Ansdell et al. 2016; Zhang et al. 2021).

The dust evolution models of LkCa15 in this work show that a

0.1 M ⊙ gaseous disc with Gaussian rings at B42, B69, and B101,
a viscosity _𝛼_ = 10 [−][3], a fragmentation velocity of _𝑣_ _𝑓_ = 10 m s [−][1],
and DSHARP opacities, is the best model to reproduce the contrast
between rings and gaps of the intensity radial profiles at Bands 3,
6, and 7, as well as the integrated fluxes at Bands Q and 9, and
the spectral indices. In both the dust evolution models and the dust
properties inferred from observations, the efficiency of dust trapping
in the B69 ring appears to be the highest, due to the larger dust mass
and greater maximum grain sizes reached in this ring compared to
B101.

_High angular resolution evidence of dust traps from deep ALMA Band 3 observations of LkCa15_ 15



After computing the dust continuum maps of the dust evolution
models using the DSHARP and Ricci’s opacities, we found that the
former do a better work in reproducing the observations, also suggesting that the DSHARP composition works better when modelling
the millimetre dust continuum emission of LkCa15.


**ACKNOWLEDGMENTS**


We are very thankful for the thoughtful suggestions of the anonymous referee that helped to improve our manuscript significantly.
A.S. and P.P. acknowledge funding from the UK Research and Innovation (UKRI) under the UK government’s Horizon Europe funding
guarantee from ERC (under grant agreement No 101076489). MB
has received funding from the European Research Council (ERC)
under the European Union’s Horizon 2020 research and innovation
programme (PROTOPLANETS, grant agreement No. 101002188).
PC acknowledges support by the ANID BASAL project FB210003.
Support for F.L. was provided by NASA through the NASA Hubble Fellowship grant #HST-HF2-51512.001-A awarded by the Space
Telescope Science Institute, which is operated by the Association of
Universities for Research in Astronomy, Incorporated, under NASA
contract NAS5-26555. C.C.-G. acknowledges support from UNAM
DGAPA-PAPIIT grant IG101224 and from CONAHCyT Ciencia
de Frontera project ID 86372. This paper makes use of the following ALMA data: 2012.1.00870.S, 2015.1.00118.S, 2018.1.00945.S,
2018.1.01255.S, 2018.1.00350.S, and 2022.1.01216.S. ALMA is a
partnership of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada), MOST and ASIAA
(Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO,
AUI/NRAO and NAOJ.


**SOFTWARE**


This work made use of the following software: Astropy (Astropy
Collaboration et al. 2013, 2018), CASA (McMullin et al. 2007),
Dustpy (Stammler & Birnstiel 2022), Emcee (Foreman-Mackey et al.
2013), Frankenstein (Jennings et al. 2020), Gofish (Teague 2019),
Matplotlib (Hunter 2007), Numpy (Harris et al. 2020), RADMC3D
(Dullemond et al. 2012), Scipy (Virtanen et al. 2020).


**DATA AVAILABILITY**


The self-calibrated data underlying this article will be shared on
reasonable request to the corresponding author. The non-calibrated
data is publicly available at [https://almascience.nrao.edu/aq/](https://almascience.nrao.edu/aq/) using
the project code 2022.1.01216.S.


**REFERENCES**


[Andrews S. M., Williams J. P., 2005, ApJ, 631, 1134](http://dx.doi.org/10.1086/432712)
Andrews S. M., Wilner D. J., Espaillat C., Hughes A. M., Dullemond C. P.,
[McClure M. K., Qi C., Brown J. M., 2011, ApJ, 732, 42](http://dx.doi.org/10.1088/0004-637X/732/1/42)
[Andrews S. M., et al., 2018, ApJ, 869, L41](http://dx.doi.org/10.3847/2041-8213/aaf741)
[Andrews S. M., et al., 2021, ApJ, 916, 51](http://dx.doi.org/10.3847/1538-4357/ac00b9)
[Ansdell M., et al., 2016, ApJ, 828, 46](http://dx.doi.org/10.3847/0004-637X/828/1/46)
[Astropy Collaboration et al., 2013, A&A, 558, A33](http://dx.doi.org/10.1051/0004-6361/201322068)
[Astropy Collaboration et al., 2018, AJ, 156, 123](http://dx.doi.org/10.3847/1538-3881/aabc4f)
[Benisty M., et al., 2021, ApJ, 916, L2](http://dx.doi.org/10.3847/2041-8213/ac0f83)



Benisty M., et al., 2023, in Inutsuka S., Aikawa Y., Muto T., Tomida K.,
Tamura M., eds, Astronomical Society of the Pacific Conference Series Vol. 534, Protostars and Planets VII. p. 605 ( `[arXiv:2203.09991](http://arxiv.org/abs/2203.09991)` ),
[doi:10.48550/arXiv.2203.09991](http://dx.doi.org/10.48550/arXiv.2203.09991)

[Birnstiel T., Klahr H., Ercolano B., 2012, A&A, 539, A148](http://dx.doi.org/10.1051/0004-6361/201118136)
[Birnstiel T., et al., 2018, ApJ, 869, L45](http://dx.doi.org/10.3847/2041-8213/aaf743)
[Bruderer S., 2013, A&A, 559, A46](http://dx.doi.org/10.1051/0004-6361/201321171)

Calvet N., D’Alessio P., Hartmann L., Wilner D., Walsh A., Sitko M., 2002,

[ApJ, 568, 1008](http://dx.doi.org/10.1086/339061)
[Carrasco-González C., et al., 2019, ApJ, 883, 71](http://dx.doi.org/10.3847/1538-4357/ab3d33)
[Carvalho A. S., et al., 2024, ApJ, 971, 129](http://dx.doi.org/10.3847/1538-4357/ad5a07)
[Casassus S., et al., 2015, ApJ, 812, 126](http://dx.doi.org/10.1088/0004-637X/812/2/126)
Delage T. N., Gárate M., Okuzumi S., Yang C.-C., Pinilla P., Flock M.,
[Stammler S. M., Birnstiel T., 2023, A&A, 674, A190](http://dx.doi.org/10.1051/0004-6361/202244731)
Doi K., Kataoka A., Liu H. B., Yoshida T. C., Benisty M., Dong R., Yamato
[Y., Hashimoto J., 2024, ApJ, 974, L25](http://dx.doi.org/10.3847/2041-8213/ad7f51)
[Draine B. T., 2006, ApJ, 636, 1114](http://dx.doi.org/10.1086/498130)
[Drażkowska J., Li S., Birnstiel T., Stammler S. M., Li H., 2019, ApJ, 885, 91](http://dx.doi.org/10.3847/1538-4357/ab46b7)
Dullemond C. P., Juhasz A., Pohl A., Sereshti F., Shetty R., Peters T., Commercon B., Flock M., 2012, RADMC-3D: A multi-purpose radiative
transfer tool (ascl:1202.015)
[Dullemond C. P., et al., 2018, ApJ, 869, L46](http://dx.doi.org/10.3847/2041-8213/aaf742)
[Epstein P. S., 1924, Phys. Rev., 23, 710](http://dx.doi.org/10.1103/PhysRev.23.710)
[Facchini S., et al., 2020, A&A, 639, A121](http://dx.doi.org/10.1051/0004-6361/202038027)
Flaherty K. M., Hughes A. M., Teague R., Simon J. B., Andrews S. M.,
[Wilner D. J., 2018, ApJ, 856, 117](http://dx.doi.org/10.3847/1538-4357/aab615)
[Flock M., Mignone A., 2021, A&A, 650, A119](http://dx.doi.org/10.1051/0004-6361/202040104)
Flock M., Ruge J. P., Dzyurkevich N., Henning T., Klahr H., Wolf S., 2015,

[A&A, 574, A68](http://dx.doi.org/10.1051/0004-6361/201424693)
[Foreman-Mackey D., Hogg D. W., Lang D., Goodman J., 2013, PASP, 125,](http://dx.doi.org/10.1086/670067)
[306](https://ui.adsabs.harvard.edu/abs/2013PASP..125..306F)

[Gaia Collaboration 2020, VizieR Online Data Catalog, p. I/350](https://ui.adsabs.harvard.edu/abs/2020yCat.1350....0G)
[Gárate M., et al., 2021, A&A, 655, A18](http://dx.doi.org/10.1051/0004-6361/202141444)

[Harris C. R., et al., 2020, Nature, 585, 357](http://dx.doi.org/10.1038/s41586-020-2649-2)
[Huang S., van der Marel N., Portegies Zwart S., 2024, A&A, 691, A155](http://dx.doi.org/10.1051/0004-6361/202451511)
[Hunter J. D., 2007, Computing in Science & Engineering, 9, 90](http://dx.doi.org/10.1109/MCSE.2007.55)
[Isella A., Pérez L. M., Carpenter J. M., 2012, ApJ, 747, 136](http://dx.doi.org/10.1088/0004-637X/747/2/136)
[Isella A., Chandler C. J., Carpenter J. M., Pérez L. M., Ricci L., 2014, ApJ,](http://dx.doi.org/10.1088/0004-637X/788/2/129)

[788, 129](https://ui.adsabs.harvard.edu/abs/2014ApJ...788..129I)
Isella A., Benisty M., Teague R., Bae J., Keppler M., Facchini S., Pérez L.,
[2019, ApJ, 879, L25](http://dx.doi.org/10.3847/2041-8213/ab2a12)
Izquierdo A. F., Testi L., Facchini S., Rosotti G. P., van Dishoeck E. F., Wölfer
[L., Paneque-Carreño T., 2023, A&A, 674, A113](http://dx.doi.org/10.1051/0004-6361/202245425)
Jennings J., Booth R. A., Tazzari M., Rosotti G. P., Clarke C. J., 2020,

[MNRAS, 495, 3209](http://dx.doi.org/10.1093/mnras/staa1365)
Jennings J., Booth R. A., Tazzari M., Clarke C. J., Rosotti G. P., 2022,

[MNRAS, 509, 2780](http://dx.doi.org/10.1093/mnras/stab3185)
[Jin S., Isella A., Huang P., Li S., Li H., Ji J., 2019, ApJ, 881, 108](http://dx.doi.org/10.3847/1538-4357/ab2dfe)
[Johansen A., Klahr H., 2005, ApJ, 634, 1353](http://dx.doi.org/10.1086/497118)
[Johansen A., Youdin A., Klahr H., 2009, ApJ, 697, 1269](http://dx.doi.org/10.1088/0004-637X/697/2/1269)
[Kirchschlager F., Bertrang G. H. M., 2020, A&A, 638, A116](http://dx.doi.org/10.1051/0004-6361/202037943)
[Kirchschlager F., Bertrang G. H. M., Flock M., 2019, MNRAS, 488, 1211](http://dx.doi.org/10.1093/mnras/stz1763)
[Leemker M., et al., 2022, A&A, 663, A23](http://dx.doi.org/10.1051/0004-6361/202243229)
[Liu H. B., 2019, ApJ, 877, L22](http://dx.doi.org/10.3847/2041-8213/ab1f8e)
[Liu Y., et al., 2024, arXiv e-prints, p. arXiv:2411.00277](http://dx.doi.org/10.48550/arXiv.2411.00277)
[Long F., et al., 2020, ApJ, 898, 36](http://dx.doi.org/10.3847/1538-4357/ab9a54)
[Long F., et al., 2022, ApJ, 937, L1](http://dx.doi.org/10.3847/2041-8213/ac8b10)
Macías E., Guerra-Alvarado O., Carrasco-González C., Ribas Á., Espaillat
[C. C., Huang J., Andrews S. M., 2021, A&A, 648, A33](http://dx.doi.org/10.1051/0004-6361/202039812)
Manara C. F., Testi L., Natta A., Rosotti G., Benisty M., Ercolano B., Ricci
[L., 2014, A&A, 568, A18](http://dx.doi.org/10.1051/0004-6361/201323318)
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
Montesinos M., Garrido-Deutelmoser J., Olofsson J., Giuppone C. A., Cuadra
[J., Bayo A., Sucerquia M., Cuello N., 2020, A&A, 642, A224](http://dx.doi.org/10.1051/0004-6361/202038758)
[Pérez L. M., Isella A., Carpenter J. M., Chandler C. J., 2014, ApJ, 783, L13](http://dx.doi.org/10.1088/2041-8205/783/1/L13)


MNRAS **000**, 1–16 (2025)

16 _A. Sierra et al._


Piétu V., Dutrey A., Guilloteau S., Chapillon E., Pety J., 2006, [A&A,](http://dx.doi.org/10.1051/0004-6361:20065968) [460,](https://ui.adsabs.harvard.edu/abs/2006A&A...460L..43P)

[L43](https://ui.adsabs.harvard.edu/abs/2006A&A...460L..43P)

[Pinilla P., Benisty M., Birnstiel T., 2012, A&A, 545, A81](http://dx.doi.org/10.1051/0004-6361/201219315)
[Pinilla P., Pascucci I., Marino S., 2020, A&A, 635, A105](http://dx.doi.org/10.1051/0004-6361/201937003)

[Pinilla P., Lenz C. T., Stammler S. M., 2021, A&A, 645, A70](http://dx.doi.org/10.1051/0004-6361/202038920)
[Pinilla P., Benisty M., Waters R., Bae J., Facchini S., 2024, A&A, 686, A135](http://dx.doi.org/10.1051/0004-6361/202348707)
Pinte C., Dent W. R. F., Ménard F., Hales A., Hill T., Cortes P., de Gregorio[Monsalvo I., 2016, ApJ, 816, 25](http://dx.doi.org/10.3847/0004-637X/816/1/25)
[Pohl A., et al., 2017, ApJ, 850, 52](http://dx.doi.org/10.3847/1538-4357/aa94c2)
[Regály Z., Juhász A., Sándor Z., Dullemond C. P., 2012, MNRAS, 419, 1701](http://dx.doi.org/10.1111/j.1365-2966.2011.19834.x)
Ricci L., Testi L., Natta A., Neri R., Cabrit S., Herczeg G. J., 2010, [A&A,](http://dx.doi.org/10.1051/0004-6361/200913403)

[512, A15](https://ui.adsabs.harvard.edu/abs/2010A&A...512A..15R)

[Rosotti G. P., 2023, New Astron. Rev., 96, 101674](http://dx.doi.org/10.1016/j.newar.2023.101674)
Rosotti G. P., Teague R., Dullemond C., Booth R. A., Clarke C. J., 2020,

[MNRAS, 495, 173](http://dx.doi.org/10.1093/mnras/staa1170)
Rota A. A., Meĳerhof J. D., van der Marel N., Francis L., van der Tak F. F. S.,
[Sellek A. D., 2024, A&A, 684, A134](http://dx.doi.org/10.1051/0004-6361/202348387)
Rybicki G. B., Lightman A. P., 1986, Radiative Processes in Astrophysics.
Wiley-VCH
[Sallum S., et al., 2015, Nature, 527, 342](http://dx.doi.org/10.1038/nature15761)
[Sallum S., Eisner J., Skemer A., Murray-Clay R., 2023, ApJ, 953, 55](http://dx.doi.org/10.3847/1538-4357/ace16c)
[Shakura N. I., Sunyaev R. A., 1973, A&A, 500, 33](https://ui.adsabs.harvard.edu/abs/1973A&A....24..337S)
[Sierra A., Lizano S., 2020, ApJ, 892, 136](http://dx.doi.org/10.3847/1538-4357/ab7d32)
Sierra A., Lizano S., Macías E., Carrasco-González C., Osorio M., Flock M.,
[2019, ApJ, 876, 7](http://dx.doi.org/10.3847/1538-4357/ab1265)
[Sierra A., et al., 2021, ApJS, 257, 14](http://dx.doi.org/10.3847/1538-4365/ac1431)
[Sierra A., et al., 2024, ApJ, 974, 306](http://dx.doi.org/10.3847/1538-4357/ad7460)
[Simon J. B., Armitage P. J., 2014, ApJ, 784, 15](http://dx.doi.org/10.1088/0004-637X/784/1/15)
[Stammler S. M., Birnstiel T., 2022, ApJ, 935, 35](http://dx.doi.org/10.3847/1538-4357/ac7d58)
Stammler S. M., Drążkowska J., Birnstiel T., Klahr H., Dullemond C. P.,
[Andrews S. M., 2019, ApJ, 884, L5](http://dx.doi.org/10.3847/2041-8213/ab4423)
Sturm J. A., Booth A. S., McClure M. K., Leemker M., van Dishoeck E. F.,

[2023, A&A, 670, A12](http://dx.doi.org/10.1051/0004-6361/202244227)
[Tazaki R., Tanaka H., 2018, ApJ, 860, 79](http://dx.doi.org/10.3847/1538-4357/aac32d)
Tazzari M., 2017, mtazzari/uvplot, [doi:10.5281/zenodo.1003113,](http://dx.doi.org/10.5281/zenodo.1003113) `[https:](https://doi.org/10.5281/zenodo.1003113)`
```
  //doi.org/10.5281/zenodo.1003113
```

[Teague R., 2019, The Journal of Open Source Software, 4, 1632](http://dx.doi.org/10.21105/joss.01632)
[Uribe A. L., Klahr H., Flock M., Henning T., 2011, ApJ, 736, 85](http://dx.doi.org/10.1088/0004-637X/736/2/85)
[Villenave M., et al., 2022, ApJ, 930, 11](http://dx.doi.org/10.3847/1538-4357/ac5fae)
[Virtanen P., et al., 2020, Nature Methods, 17, 261](http://dx.doi.org/10.1038/s41592-019-0686-2)
[Weidenschilling S. J., 1977, MNRAS, 180, 57](http://dx.doi.org/10.1093/mnras/180.2.57)
Whipple F. L., 1972, in Elvius A., ed., From Plasma to Planet. p. 211
[Youdin A. N., Goodman J., 2005, ApJ, 620, 459](http://dx.doi.org/10.1086/426895)
[Zapata L. A., Rodríguez L. F., Palau A., 2017, ApJ, 834, 138](http://dx.doi.org/10.3847/1538-4357/834/2/138)
Zhang K., et al., 2021, ApJS, in press
Zhang S., Zhu Z., Ueda T., Kataoka A., Sierra A., Carrasco-González C.,
[Macías E., 2023, ApJ, 953, 96](http://dx.doi.org/10.3847/1538-4357/acdb4e)
[Zhu Z., et al., 2019, ApJ, 877, L18](http://dx.doi.org/10.3847/2041-8213/ab1f8c)
[van der Marel N., 2023, European Physical Journal Plus, 138, 225](http://dx.doi.org/10.1140/epjp/s13360-022-03628-0)
[van der Marel N., et al., 2013, Science, 340, 1199](http://dx.doi.org/10.1126/science.1236770)

van der Marel N., van Dishoeck E. F., Bruderer S., Pérez L., Isella A., 2015,


[A&A, 579, A106](http://dx.doi.org/10.1051/0004-6361/201525658)
van der Marel N., van Dishoeck E. F., Bruderer S., Andrews S. M., Pontoppidan K. M., Herczeg G. J., van Kempen T., Miotello A., 2016, [A&A,](http://dx.doi.org/10.1051/0004-6361/201526988)
[585, A58](https://ui.adsabs.harvard.edu/abs/2016A&A...585A..58V)


**APPENDIX A:** **DISC CENTRING**


Errors in the disc geometry and offset with respect to the Phase Center
can create non-axi-symmetric structures in the residual maps of the
dust continuum modelling (Andrews et al. 2021). As mentioned in
Section 3, we estimated the offset of the disc by fitting the iso-contour
ellipse that follows the main ring B69 and obtain ΔRA = 15 _._ 7 mas,
ΔDec = −6 _._ 9 mas. On other side, the offset was also estimated by
minimizing the imaginary part of the visibilities (Isella et al. 2019),
obtaining ΔRA = 15 _._ 3 mas, ΔDec = 12 _._ 9 mas. All these values are


MNRAS **000**, 1–16 (2025)



on the order of one pixel size. A Frankenstein model was calculated
in both cases, and the residual maps were computed using the same
imaging parameters as in Figure 4. The residual maps are shown in
Figure A1, where it is clear that the residual structures are minimized
at the disc phase centre. Therefore, we assume ΔRA = ΔDec = 0
when fitting the Band 3 data.


**APPENDIX B:** **RADIATIVE TRANSFER MODELS FOR**

**RICCI’S OPACITIES**


The radiative transfer models computed with `RADMC3D` using the
Ricci’s opacities for the three dust evolution models in Figure 9 are
shown in Figure B1. The brightness temperatures for all bands are
significantly higher compared to those from the DSHARP opacities (Figure 10) and the observations. The main difference between
Ricci’s and DSHARP opacities comes from their composition, as the
carbonaceous grains in the former have a higher absorption opacity
than the refractory organic grains in the DSHARP mixture (Birnstiel
et al. 2018).


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.

_High angular resolution evidence of dust traps from deep ALMA Band 3 observations of LkCa15_ 17



0 _._ 5 _[′′]_


##### Phase Center Ellipse Min Vis



0 _._ 0 _[′′]_

|′′<br>′′|B42<br>B69<br>B101|Col3|Col4|
|---|---|---|---|
|_′′_<br>_′′_<br>||||



0 _._ 5 _[′′]_ 0 _._ 0 _[′′]_ _−_ 0 _._ 5 _[′′]_



5


4


3


_−_ 3


_−_ 4


_−_ 5



**Figure A1.** Residual map of the Band 3 dust continuum observations of LkCa15 after subtracting an axi-symmetric model centred at the Phase Center (left), in
the centre computed from an ellipse fit (middle), and the centre computed from minimizing the imaginary part of the visibilities (right). The colour bar is the
same for all panels. The ellipses show the radial position of the three bright rings at 42, 69, and 101 au. The beam size is shown in the bottom left corner of each
panel.




















|Band3 Band6 Band7 BrightnessTem|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|Model 1<br>0_._0<br>0_._2<br>0_._4|Model 1<br>0<br>2|Model 1<br>0<br>5|2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5|Band 3<br>Band 6<br>Band 7<br>2_._0<br>2_._5<br>3_._0<br>3_._5<br>4_._0<br>4_._5|
|Model 2<br>0_._0<br>0_._2|Model 2<br>0<br>1<br>2|Model 2<br>0<br>2<br>4|2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5<br>S<br>O|imulations<br>bservations<br>2_._0<br>2_._5<br>3_._0<br>3_._5<br>4_._0<br>4_._5<br>Sim<br>Obs|
||||||
|Model 3<br>0_._0<br>0_._2<br>0_._4|Model 3<br>0<br>1<br>2|Model 3<br>0<br>2<br>4|2_._5<br>5_._0<br>7_._5<br>10_._0<br>12_._5|2_._0<br>2_._5<br>3_._0<br>3_._5<br>4_._0<br>4_._5|
||||||



Radius [au]



1 _._ 0


0 _._ 5


0 _._ 0


_−_ 0 _._ 5


_−_ 1 _._ 0



∆RA [arcsec]



Radius [au]


MNRAS **000**, 1–16 (2025)



**Figure B1.** Same as Figure 10, but using the Ricci’s opacities.


</paper>

## Items to check

```json
[
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "Radiative transfer equation solution including scattering opacity",
  "failed_quote": "The dust property constraints are computed using the solution for the radiative transfer equation in Sierra et al. (2019); Sierra & Lizano (2020), where the contribution of the scattering opacity is taken into account."
 },
 {
  "path": "analysis_steps[1].method.evidence[2]",
  "value": "Extract normalized visibilities, fit de-projected visibilities with Frankenstein, convolve radial profiles to a common 35 mas resolution, fit 5 symmetric Gaussian rings to both image-plane and Frankenstein radial profiles, and image visibility residuals (data minus Frankenstein model) in CASA",
  "failed_quote": "The morphology of the radial profiles in each panel is fitted using five symmetric Gaussian rings (grey lines)."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Axi-symmetric disc emission for Frankenstein fit; five symmetric Gaussian components (inner disc fixed at r_0 = 0, three main rings, and extended emission)",
  "failed_quote": "This model is chosen to account for the three main rings, the inner disc, and the extended emission beyond the outer ring. The free parameters of each Gaussian ring are the intensity amplitude (A_i), the width (FWHM_i), and the radial location of the peak (r_i). The only exception is the Gaussian ring representing the inner disc, where the radial location if fixed at 0."
 },
 {
  "path": "analysis_steps[1].validation.evidence[0]",
  "value": "Quantified Frankenstein resolution by fitting input delta rings at the same uv-coverage; tested sensitivity of residual maps to disc centre offsets in Appendix A",
  "failed_quote": "where the resolution is quantified by fitting the visibilities of an input delta ring at the same uv-coverage of each observation, and then measuring the FWHM of the Frankenstein output profile."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "MCMC fitting of multi-wavelength continuum intensities (Bands 3, 6, 7) at each radius (> 0.1 arcsec) using the radiative transfer equation including dust scattering for DSHARP and Ricci opacities",
  "failed_quote": "The dust property constraints are computed using the solution for the radiative transfer equation in Sierra et al. (2019); Sierra & Lizano (2020), where the contribution of the scattering opacity is taken into account."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[1]",
  "value": "Parameter space: 1 K < T_d < 300 K, 10^-6 g cm^-2 < Sigma_d < 10 g cm^-2, 10 um < a_max < 30 cm; 24 walkers, 10,000 steps; sampled every 1/3 resolution element",
  "failed_quote": "Finally, the parameter space at each radius is explored using 24 walkers and 10,000 steps. The best fits at each radius are then used to sample the radial profile of dust properties, taking the median value at every 1/3 of a resolution element."
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[2]",
  "value": "Spherical grains, grain size distribution n(a) da = a^-p da with p = 3, bulk density 1.6 g cm^-3 (DSHARP) or 0.85 g cm^-3 (Ricci), absolute flux uncertainties of 10% (Band 6, 7) and 5% (Band 3)",
  "failed_quote": "The bulk densities for the DSHARP and Ricci's dust grain compositions are 1.6 and 0.85 g cm^-3, respectively."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "MCMC with emcee (24 walkers, 10,000 steps); log-uniform priors on a_max and Sigma_d; prior on T_d from passively irradiated disc T_prior = (0.02 L_* / 8 pi sigma_B r^2)^(1/4) with 50 K uncertainty",
  "failed_quote": "The prior for the maximum grain size and dust temperature are given by a log-uniform distribution, while for the dust temperature we include a prior temperature radial profile given by the expected temperature from a passively irradiated disc: T_prior = (0.02L_* /8πσ_B r^2)^1/4"
 },
 {
  "path": "analysis_steps[2].validation.evidence[0]",
  "value": "Checked optical depths (absorption vs scattering) and compared predicted VLA Band Q (44 GHz) flux between 25 and 125 au against observed flux (0.72 mJy)",
  "failed_quote": "Specifically, the flux of LkCa15 at VLA Band Q (44 GHz) between 25 au and 125 au is approximately 0.72 mJy. The expected flux at Band Q (within the same radial extent) based on the inferred dust properties shown in Figure 6 is ∼ 0.70 mJy and 0.13 mJy for the DSHARP and Ricci's opacity models, respectively."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Inner disc emission in Bands 6 and 7 originates purely from dust continuum emission, and total flux at Band X is dominated by the inner disc",
  "failed_quote": "Assuming that the emission in Bands 6 and 7 originates from dust continuum emission, the extrapolated dust continuum flux in Band 3 is approximately 8.6 μJy, which represents ∼ 19% of the inner disc flux in Band 3."
 },
 {
  "path": "software[6].used_for.evidence[0]",
  "value": "Computing DSHARP and Ricci dust opacities for spherical grains",
  "failed_quote": "In both cases, we consider sphere grains and use the DSHARP opacity tools."
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "FWHM vs frequency slope for B42 (Frankenstein fit) = 0.32 mas GHz^-1",
  "failed_quote": "for the rings B42, B69, B101 in the bottom right panel (radial profiles from the Frankenstein fit), are 0.32 ± 0.02 mas GHz^-1, 0.23 ± 0.03 mas GHz^-1, and 0.42 ± 0.02 mas GHz^-1, respectively."
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "FWHM vs frequency slope for B69 (Frankenstein fit) = 0.23 mas GHz^-1",
  "failed_quote": "for the rings B42, B69, B101 in the bottom right panel (radial profiles from the Frankenstein fit), are 0.32 ± 0.02 mas GHz^-1, 0.23 ± 0.03 mas GHz^-1, and 0.42 ± 0.02 mas GHz^-1, respectively."
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "FWHM vs frequency slope for B101 (Frankenstein fit) = 0.42 mas GHz^-1",
  "failed_quote": "for the rings B42, B69, B101 in the bottom right panel (radial profiles from the Frankenstein fit), are 0.32 ± 0.02 mas GHz^-1, 0.23 ± 0.03 mas GHz^-1, and 0.42 ± 0.02 mas GHz^-1, respectively."
 },
 {
  "path": "results_numeric[20].evidence[0]",
  "value": "Total dust mass (DSHARP opacities) = 7.5e-4 (250 M_Earth) M_sun",
  "failed_quote": "While the dust mass inferred from the DSHARP opacities is around 7.5 × 10^-4 M_⊙ (250 M_⊕), for Ricci's opacities it is an order of magnitude lower: 0.4 × 10^-4 M_⊙ (13 M_⊕)."
 },
 {
  "path": "results_numeric[21].evidence[0]",
  "value": "Total dust mass (Ricci opacities) = 0.4e-4 (13 M_Earth) M_sun",
  "failed_quote": "While the dust mass inferred from the DSHARP opacities is around 7.5 × 10^-4 M_⊙ (250 M_⊕), for Ricci's opacities it is an order of magnitude lower: 0.4 × 10^-4 M_⊙ (13 M_⊕)."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "The inner disc emission at 3 mm is dominated by free-free radiation consistent with an ionised jet or disc wind.",
  "failed_quote": "Assuming that the emission in Bands 6 and 7 originates from dust continuum emission, the extrapolated dust continuum flux in Band 3 is approximately 8.6 μJy, which represents ∼ 19% of the inner disc flux in Band 3. Consequently, the estimated free-free emission in the inner disc at Band 3 is ∼ 36.8 μJy"
 }
]
```
