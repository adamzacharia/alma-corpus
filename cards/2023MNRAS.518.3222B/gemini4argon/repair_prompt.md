# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.518.3222B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–23 (2022) Preprint 25 October 2022 Compiled using MNRAS L [A] TEX style file v3.0

## **_A Multi-Wavelength Study of Multiple Spectral Component Jets in AGN:_** **_Testing the IC/CMB Model for the Large-Scale-Jet X-ray Emission_**


Peter Breiding, [1] _[★]_ Eileen T. Meyer, [2] Markos Georganopoulos, [2] _[,]_ [3] Karthik Reddy, [2] Kassidy E. Kollmann, [2] _[,]_ [4]

and Agniva Roychowdhury [2]

1 _Department of Physics and Astronomy, Bloomberg Center, Johns Hopkins University, Baltimore, MD 21218, USA_
2 _Department of Physics, University of Maryland Baltimore County, Baltimore, MD 21250, USA_
3 _NASA Goddard Space Flight Center, Code 663, Greenbelt, MD 20771, USA_
4 _Department of Physics, Princeton University, Princeton, NJ 08544, USA_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

Over ∼150 resolved, kpc-scale X-ray jets hosted by active galactic nuclei have been discovered with the _Chandra_ X-ray
Observatory. A significant fraction of these jets have an X-ray spectrum either too high in flux or too hard to be consistent with
the high-energy extension of the radio-to-optical synchrotron spectrum, a subtype we identify as Multiple Spectral Component
(MSC) X-ray jets. A leading hypothesis for the origin of the X-rays is the inverse-Compton scattering of the cosmic microwave
background by the same electron population producing the radio-to-optical synchrotron spectrum (known as the IC/CMB model).
In this work, we test the IC/CMB model in 45 extragalactic X-ray jets using observations from the _Fermi_ Large Area Telescope to
look for the expected high level of gamma-ray emission, utilizing observations from the Atacama Large Millimeter/submillimeter
Array (ALMA) and the _Hubble Space Telescope (HST)_ when possible to best constrain the predicted gamma-ray flux. Including
this and previous works, we now find the IC/CMB model to be ruled out in a total of 24/45 MSC X-ray jets due to its overprediction for the observed MeV-to-GeV gamma-ray flux. We present additional evidence against the IC/CMB model, including
the relative X-ray-to-radio relativistic beaming in these sources, and the general mismatch between radio and X-ray spectral
indexes. Finally, we present upper limits on the large-scale bulk-flow Lorentz factors for all jets based on the Fermi upper limits,
which suggest that these jets are at most mildly relativistic.


**Key words:** galaxies: jets, galaxies: active



**1** **INTRODUCTION**


The launch of the _Chandra_ X-ray observatory in 1999 ushered in a
new era of high-resolution, sensitive X-ray imaging of extragalactic jets in active galactic nuclei (AGN). Prior to its launch, it was
not clear that high levels of X-ray emission would be a common
occurrence in the large-scale (i.e., kpc-scale) AGN jets. However,
there are now over ∼150 known, resolved X-ray jets, most of which
were discovered by _Chandra_ [1] . The X-ray emission in many of the
lower-power jets is usually ascribed to synchrotron radiation from the
high-energy extrapolation of the electron population producing the
radio-to-optical synchrotron spectrum (e.g., Wilson & Yang 2002,
although see Meyer et al. 2018 for a counter-example). Conversely,
a single synchrotron spectrum extending from radio to X-ray wavelengths is precluded in many of the more powerful quasar-hosted
jets (e.g., Sambruna et al. 2004b; Jorstad & Marscher 2006; Tavecchio et al. 2007a; Kharb et al. 2012; Stanley et al. 2015), where
the observed X-ray spectrum is either too high in flux or hard to be
consistent with the high-energy extrapolation of the electron energy


_★_ E-mail: pbreiding@gmail.com
1 see e.g. the XJET database http://hea-www.harvard.edu/XJET/ and the
ATLASX catalog


© 2022 The Authors



distribution (EED) producing the radio-to-optical synchrotron spectrum. In some cases there appear to be at least _three_ distinct emission
components (e.g., the jet in M84; Meyer et al. 2018), and a second
component can be seen emerging in the optical/UV in some cases
(Cara et al. 2013; Breiding et al. 2017). In Breiding et al. (2017) we
began referring to jets with one or more additional high-energy emission components beyond the radio synchrotron emission as “Multiple
Spectral Component” (MSC) jets, and we will continue using this
naming convention for the present study.


The first kpc-scale MSC jet to be detected in X-rays by _Chan-_
_dra_ was hosted by the quasar PKS 0637-752 (Chartas et al. 2000;
Schwartz et al. 2000). Soon after, Tavecchio et al. (2000) and Celotti
et al. (2001) independently proposed that the high level of X-ray
emission could be explained as inverse-Compton (IC) scattering of
the cosmic microwave background (CMB) by the same electron population producing the radio-to-optical synchrotron spectrum (i.e.,
IC/CMB). Subsequently, IC/CMB has become the dominant explanation for the anomalously bright and/or hard X-rays seen in MSC
X-ray jets (e.g., Sambruna et al. 2004b, 2006; Perlman et al. 2011;
Marshall et al. 2018; Schwartz et al. 2020a). However, due to the
very high level of X-ray emission, the IC/CMB model requires high
Doppler factors, which in turn requires jets that remain highly relativistic on kpc scales (with bulk-flow Lorentz factors of Γ ∼ 10) and

2 _P. Breiding et al._


closely aligned to the line of sight (leading to Mpc-scale deprojected
jet lengths in several cases, Dermer & Atoyan 2004). The IC/CMB
model also requires an extension of the (assumed) power-law electron distribution to very low energies, resulting in high total power,
exceeding the Eddington limit in many cases (Dermer & Atoyan
2004).
One strong line of evidence against the IC/CMB model arises
from the morphological comparison of the associated X-ray, radio, and optical jet emission components. In particular, the IC/CMB
model requires cospatial emission in these different bands, since the
radio-to-optical synchrotron spectrum is produced by the same EED
upscattering the CMB to X-ray energies. However, many MSC Xray jets contain anomalous X-ray-jet emission components spatially
offset from the associated synchrotron radio knots by ∼1 kpc in projection; where in most cases the X-ray centroids are located upstream
(i.e., closer to the black hole) from the radio centroids (e.g., Reddy
et al. 2021, 2022). This is in clear conflict with the expectations from
the IC/CMB model, where we would expect if any offset to occur,
for the X-ray emission to persist downstream (i.e., further from the
black hole) of the peak radio emission due to the longer cooling times
of the low-energy portion of the EED responsible for the IC/CMB
X-rays.
These long cooling times would also seem to predict X-ray emission which is continuous along the length of the jet, but in most
cases the observed X-ray emission is confined to compact knots of
order ∼1 kpc in size (see Harris & Krawczynski 2006 for a thorough
review of these issues). This problem can be avoided by requiring the
plasma to be contained within discrete blobs (though see Meyer et al.
2016, where this scenario has been ruled out in 3C 273 by the lack
of expected proper motions). The radio synchrotron emission from

∼
the low-energy electrons (i.e., _𝛾_ 100) have been searched for with
the high angular-resolution Low Frequency Array (LOFAR) observations at 150 MHz presented in Harris et al. (2019) for the MSC
X-ray jet hosted by the quasar 4C +19.44. However, it was found
that the number density of these low-energy electrons was much less
than the implied value from the low-energy extrapolation of the GHzemitting electrons due to the very faint detections of the jet features at
150 MHz (suggesting significant spectral curvature in this jet). This
result is even more problematic for applying the IC/CMB model in
this source, since it necessarily implies a unrealistically high level of
relativistic beaming in order to account for the anomalous X-rays.
Other observations which are challenging for the IC/CMB model
include the high degree of polarization measured in the rising UV
component (clearly part of the second spectral component) in the jet
hosted by quasar PKS 1136-135 (Cara et al. 2013, where the IC/CMB
radiation is expected to be unpolarized), a detected X-ray counter-jet
in Pictor A (Hardcastle et al. 2016, where the resulting jet-to-counter
jet flux ratio implies a non-relativistic jet oriented at large angles to
the line of sight), flux variability on the order of a few years in the
X-ray knots of Pictor A (Hardcastle et al. 2016), rising UV spectral
components that have an implied spectral index inconsistent with the
IC/CMB model in PKS 2209+080 (Breiding et al. 2017), and a lack
of correlation between the ratio of X-ray-to-radio jet luminosity with
redshift in large samples of X-ray jets (e.g., Marshall et al. 2018). This
latter result is especially challenging, since the CMB energy density
is directly proportional to (1 + z) [4], so the naive expectation is that
we would expect more luminous X-ray jets and a higher proportion
of X-ray jets with increasing redshift (Schwartz 2002).
Despite all of the weight of evidence above, it is still possible that
the IC/CMB mechanism is the dominant emission process at work
in some resolved, kpc-scale X-ray jets. This may in particular be the
case for jets at very high redshift due to the strong CMB enhancement


MNRAS **000**, 1–23 (2022)



(e.g. Worrall et al. 2020a; Schwartz et al. 2020b; Ighina et al. 2021)
or at low redshift, in rare cases of fast kpc-scale jets with favorable
alignment (Meyer et al. 2019). In order to evaluate the viability of the
IC/CMB model as the dominant X-ray emission mechanism in any
individual jet we must test the various predictions it makes for the
physical properties of these jets and the resulting multi-wavelength
radiation they produce.
One such prediction of an IC/CMB origin for the X-ray emission
in resolved X-ray jets is the requirement of a high level of MeV-toGeV gamma-ray flux (Georganopoulos et al. 2006). This requirement
results from the fact that the IC/CMB spectrum is essentially an
exact copy of the radio-to-optical synchrotron spectrum, shifted in
frequency and luminosity by an amount necessary to reproduce the
observed X-ray flux. This shift is parametrized by B/ _𝛿_, where B is the
magnetic field strength of the emission region and _𝛿_ is the Doppler
factor [2] . There are no other free parameters in the model, although
we must extrapolate from the observed ∼ GHz radio frequencies to
the much lower unobserved tens-to-hundreds of MHz frequencies.
In several previous studies we have tested the prediction of a
high GeV flux using observations from the _Fermi_ /LAT gamma-ray
space telescope. Flux upper limits resuling from the analyis of this
_Fermi_ /LAT data have ruled out the IC/CMB model in the quasars
3C 273 (Meyer & Georganopoulos 2014), PKS 0637-752 (Meyer
et al. 2015, 2017), and four MSC X-ray jets hosted by quasars not
detected by _Fermi_ (Breiding et al. 2017): PKS 1136-135, PKS 1129021, PKS 1354+195, and PKS 2209+080. In this paper, we present
results from the analysis of over 10 years of _Fermi_ /LAT observational
data for an additional 45 extragalactic X-ray jets. Of these, 36 are
clearly MSC jets based on the X-ray flux and/or spectral index. The
remaining nine jets do not have enough constraints to rule out a
single-synchrotron spectrum from radio to X-rays but have been
modeled as IC/CMB in the literature previously. Importantly, in this
work we utilize multi-wavelength data obtained from a number of
archival and proprietary observations in order to better constrain the
radio-to-optical synchrotron spectrum for our sample − leading to
a better characterization of the predicted IC/CMB spectrum in the
_Fermi_ /LAT band.

In section 2 we further describe the multi-wavelength data used
along with the analysis methodologies utilized. In section 3, we
present the results of these analyses, with their interpretations and
implications discussed in section 4. Finally, in section 5 we summarize the main findings of our work. Throughout this paper we adopt a
ΛCDM cosmology, with H 0 = 67 _._ 74 km s [−][1] Mpc [−][1], Ω _𝜆_ = 0 _._ 69, and
Ω _𝑚_ = 0 _._ 31 (Planck Collaboration et al. 2016). Additionally, we use
the following spectral index convention: F _𝜈_ ∝ _𝜈_ [−] _[𝛼]_, where F _𝜈_ is the
flux density and _𝜈_ is the observer-frame frequency of the radiation.


2 The Doppler factor, _𝛿_, is given by _𝛿_ = Γ(1− _𝛽_ 1cos _𝜃_ ) [. Here,][ Γ][ is the bulk-flow]
Lorentz factor, _𝛽_ is the bulk flow speed scaled by c, and _𝜃_ is the jet angle to
the line of sight.

_Testing IC/CMB in Resolved Quasar X-ray Jets_ 3


**Table 1.** Sample Properties


Source Common IC/CMB
Name Name z kpc/ [′′] log [M] M [BH] ⊙ log L kin log R CE log L ext B eq log R x Ruled

(J2000) (erg s [−][1] ) (erg s [−][1] ) (10 [−][4] G) Out?


J0038−0207 [†] 3C 17 0.220 3.7 ... 45.4 -1.55 42.9 0.716 -0.337 Y
J0108+0135 [†] PKS B0106+013 2.11 8.5 ... 46.4 -0.42 44.4 2.16 0.522 N

J0209+3547 4C 35.03 0.037 0.76 ... 43.9 -1.55 40.6 0.782 0.846 Y
J0210−5101 [†] PKS 0208−512 1.0 8.2 ... 46.0 -0.52 43.8 0.422 0.826 Y
J0237+2848 [†] 4C 28.07 1.21 8.5 ... 45.7 0.42 43.4 1.12 0.649 Y

J0416−2056 PKS 0413−210 0.808 7.7 8.2 [c] 45.9 -0.29 43.7 1.51 -0.40 N
J0418+3801 [†] 3C 111 0.05 1.0 ... 44.7 -0.52 41.8 0.423 1.77 Y
J0433+0521 [†] 3C 120 0.034 0.70 7.8 [e] 43.9 0.43 40.6 0.322 1.64 Y
J0519−4546 [†] Pictor A 0.034 0.70 7.6 [b] 44.9 -1.98 42.1 0.239 1.28 Y
J0607−0834 [†] PKS 0605−085 0.870 7.9 ... 45.2 1.04 42.6 0.680 0.907 Y

J0728+6748 3C 179 0.844 7.9 8.6 [c] 45.9 -1.15 43.7 0.740 0.543 Y

J0741+3112 B2 0738+31 0.631 7.0 9.3 [c] 45.0 0.56 42.4 0.138 1.64 N
J0830+2410 [†] B2 0827+24 0.941 8.1 8.4 [h] 45.3 0.42 42.8 0.309 1.37 Y
J0840+1312 [†] 4C 13.38 0.680 7.3 8.5 [e] 45.9 -1.06 43.6 1.67 0.531 Y
J0922−3959 [†] PKS 0920−397 0.590 6.8 ... 45.6 -0.26 43.4 0.813 0.199 Y

J0947+0725 3C 227 0.086 1.7 ... 44.9 -2.75 42.1 0.185 0.052 N

J1001+5553 QSO 0957+561 1.41 8.7 9.4 [a] 45.9 -1.84 43.7 1.66 -0.244 N
J1007+1248 4C 13.41 0.241 3.9 9.3 [e] 45.0 -2.21 42.3 0.103 -0.315 N

J1033−3601 PKS 1030−357 1.46 8.7 ... 46.1 -0.41 44.0 1.02 0.628 N

J1048−1909 PKS 1045−188 0.590 6.8 6.8 [e] 45.5 -0.52 43.0 0.90 0.138 N

J1048−4114 PKS 1046−409 0.620 7.0 ... 45.7 -1.52 43.4 0.834 0.180 Y

J1058+1951 4C 20.24 1.11 8.4 ... 46.1 -0.39 44.0 0.469 0.302 Y
J1130−1449 [†] PKS 1127−145 1.19 8.5 ... 45.6 1.28 43.3 0.150 0.794 N
J1153+4931 [†] PKS 1150+497 0.334 4.9 8.6 [c] 45.1 0.19 42.5 0.742 1.27 Y
J1205−2634 [†] PKS 1202−262 0.786 7.7 8.8 [c] 45.8 -0.61 43.5 1.13 1.03 Y
J1224+2122 [†] 4C 21.35 0.434 5.8 8.5 [d] 45.4 -0.79 42.9 0.974 0.802 N
J1319+5148 4C 52.27 1.06 8.3 9.5 [d] 45.9 -0.54 43.6 1.03 0.662 N

J1325+6515 4C 65.15 1.63 8.7 9.6 [a] 46.1 -1.30 44.0 4.0 -0.265 N

J1421−0643 PKS 1418−064 3.69 7.4 ... 46.0 -0.63 43.8 1.26 1.92 N
J1510+5702 [†] QSO B1508+572 4.31 6.9 ... 45.8 -0.15 43.6 0.526 1.38 Y
J1632+8232 [†] NGC 6251 0.020 0.42 8.8 [g] 43.9 -0.83 40.5 0.148 -0.575 N
J1642+3948 [†] 3C 345 0.595 6.9 9.1 [h] 45.8 0.33 43.5 1.50 0.075 N

J1642+6856 4C 69.21 0.750 7.6 7.3 [c] 45.5 0.03 43.1 0.709 0.051 Y

J1720−0058 3C 353 0.030 0.63 ... 44.8 -2.59 42.0 0.348 0.365 Y

J1746+6226 4C 62.29 3.89 7.2 ... 46.5 -0.51 44.7 3.19 1.33 N
J1829+4844 [†] 3C 380 0.692 7.3 9.8 46.4 -0.64 44.4 2.44 0.089 Y
J1849+6705 [†] 8C 1849+670 0.660 7.2 9.1 [e] 45.0 0.51 42.3 0.226 1.70 N

J1927+7358 4C 73.18 0.30 4.6 8.7 [e] 45.0 0.50 42.2 0.520 2.20 N
J2005+7752 [†] S5 2007+777 0.342 5.0 7.4 [f] 44.4 1.18 41.4 0.337 1.03 N

J2105−4848 PKS 2101−490 1.04 8.3 ... 45.8 -0.06 43.5 0.589 0.105 N
J2158−1501 [†] PKS 2155−152 0.670 7.2 7.4 [c] 45.4 0.30 43.0 0.975 0.066 N

J2203+3145 4C 31.63 0.295 4.5 8.9 [e] 44.9 0.03 42.2 0.199 0.919 N

J2218−0335 PKS 2216−038 0.901 8.0 9.2 [c] 45.6 -0.47 43.3 0.572 0.028 N
J2253+1608 [†] 3C 454.3 0.859 7.9 8.9 [c] 45.8 0.79 43.6 1.38 0.877 N

J2338+2701 3C 465 0.030 0.62 ... 44.3 -1.63 41.1 0.864 0.620 Y


Black hole mass measurements are obtained from the following literature sources (corresponding to the superscripts in the M BH column): (a)
Kozłowski (2017), (b) Lewis & Eracleous (2006), (c) Liu et al. (2006), (d) Wang et al. (2004), (e) Woo & Urry (2002), (f) Wu et al. (2002),
(g) van den Bosch (2016), (h) Xie et al. (2005).

     - These sources are members of the 4FGL catalog; for these sources we used the re-combined light curve analysis described in section 2.6 to
determine the upper limits/minimum flux levels appropriate for the steady-state large-scale-jet gamma-ray flux.



**2** **DATA ANALYSIS**


**Radio Interferometric Data**


New and archival data from the Very Large Array (VLA), Australia
Telescope Compact Array (ATCA), and the Atacama Large Millimeter/submillimeter Array (ALMA) were reduced for this study. All
radio interferometric data were reduced using the Common Astron


omy Software Applications ( _CASA_ ) package (McMullin et al. 2007).
Below we describe the observations used from each telescope array,
and the procedures utilized to calibrate and image the visibility data.
We describe all of the radio interferometric data used in this paper in
Table 2, where we list the target source name, central frequency and
band of the observation, project code, observation date, telescope array, root mean square (RMS) intensity noise level of the final image,
and the beam width/position angle (P.A) of the synthesized beams.


MNRAS **000**, 1–23 (2022)

4 _P. Breiding et al._


**Table 2.** Radio Observations


Source Telescope Observing Observing
Name Array Band Frequency Project Code Observation Date RMS Beam Size P.A
(J2000) (GHz) YYYY-MM-DD (mJy beam [−][1] ) ( [′′] × [′′] ) ( [◦] )


J0038−0207 VLA C 4.86 AS0179 1985−03−08 [†] 0.870 0.49 × 0.39 23.4
J0108+0135 VLA C 4.86 AR197 1989−01−07 [† † †] 0.234 0.47 × 0.40 19.7
J0108+0135 VLA X 8.44 AR197 1989−01−08 [††] 0.123 0.27 × 0.23 10.5
J0108+0135 VLA Ku 15 AR223 1990−04−29 [††] 0.520 0.20 × 0.15 57.9


This table is published in its entirety online in machine-readable format, where we show a sample portion here for guidance regarding its

form and content.

      - These observations were used for making the images displayed in Figures A3-A5.

      - † These observations were used for flux density measurements.

       - † † These observations were used for both the images displayed in Figures A3-A5 and flux density measurements.



For any flux densities measured for jet components, we assume very
conservative 35% errors on these measured flux densities. These errors assume a level of ∼20% error on absolute flux calibration and

∼
15% error associated with comparing literature flux densities with
our own measured flux densities at different frequencies in the same
SED. These conservative error estimates also allow us to account

for potential minor differences in flux extraction regions at different
bands and for loss of flux associated with spatial frequency filtering
inherent in radio interferometric data with different array configurations and observing frequencies.


**2.1** **Very Large Array**


We reduced 77 archival observations taken with the VLA for the

present study. We also analyzed six new VLA observations taken for
this project under the program 15A-357. For historical VLA observations before the upgrade to the Karl G. Jansky Very Large Array
(JVLA) in 2011, we followed a standard data reduction procedure for
continuum data. For most observations, 3C 286, 3C 48, or 3C 147
served as the flux calibrator and in most cases the source itself served
as the phase calibrator. For more recent JVLA observations, we used
the _CASA_ pipeline for initial calibration. Post calibration, any excess radio frequency interference (RFI) was removed and visibility
data was imaged using the CLEAN deconvolution algorithm, via the
_CASA_ task `tclean` . Typically, the images were made with Briggs
weighting and robust parameter of 0.5 (although sometimes a natural
weighting was utilized). When appropriate or essential to our science
goals for the wide bandwidth JVLA data, we used a multi-term, multifrequency synthesis (mtmfs) deconvolution and imaging procedure
(with `nterms=2` ) defined in the `tclean` task in _CASA_ . This type of
analysis relies on modeling the sky intensity distribution as a Taylor
polynomial, expanded about some reference frequency for the subsequent deconvolution and image reconstruction (Rau & Cornwell
2011). In all cases, we applied several rounds of (non-cumulative)
phase-only self calibration, followed by a single round of amplitude
and phase self-calibration to the data to improve the final image.


**2.2** **Atacama Large Millimeter/submillimeter Array (ALMA)**


We analyzed 11 archival observations from ALMA for this
project, and 17 new observations from our projects 2015.1.00932.S,
2016.1.01481.S, and 2017.1.01572.S. The details of the observations are given in Table 2. The continuum visibility data were calibrated with the _CASA_ pipeline via the NRAO-provided python script


MNRAS **000**, 1–23 (2022)



`scriptForPI.py`, which gives a science-ready measurement set.
Similar to the VLA data, we then imaged the visibility data via the
_CASA_ task `tclean` (with Briggs weighting and robust parameter of
0.5). MTMFS imaging was employed with `nterms=2`, and typically
several rounds of phase-only self calibration and a single round of
amplitude and phase self-calibration were applied to further reduce
the RMS of the final image.


**2.3** **Australia Telescope Compact Array (ATCA)**


For this project, we analyzed six observations from ATCA. _MIRIAD_
was used to initially load the visibility data and then export into a form
to be read by _CASA_ for further calibration and imaging. Standard calibration suitable for continuum observations was applied to the data
after flagging any potential RFI in _CASA_ . For all ATCA observations
used in this project, 1934-638 served as the flux calibrator, and bright
sources served as their own phase calibrator. Imaging deconvolution
was accomplished using the _CASA_ task `clean` with Briggs weighting and a robust parameter of 0.5. In all cases at least one round of
phase-only and a final round of amplitude and phase self-calibration
was used to improve the images.


**2.4** _**Hubble Space Telescope (HST)**_


We analyzed _Hubble_ _Space_ _Telescope_ (HST) archival observations
for the quasars 4C 31.63, QSO 0234+285, PKS 0920-397, PKS 1045188, and PKS 2155-152. For all of these galaxies, the flat-fieldcorrected images were first downloaded from the Mikulski Archive
for Space Telescopes (MAST) after having first been processed
through the _calwf3_ data reduction pipeline. For 4C 31.63, we obtained
a 1.1 ks WFPC2/PC1 (F555W: 544 nm) observation from project
U2CY0 which contained only a single frame. For PKS 1045-188,
we analyzed two 2.7 ks dithered observations taken with the WFC3
detector in the IR and UV channels (filters F160W/F475W and poject code IC6701). For the remaining quasars, we analyzed dithered
observations taken with the ACS/WFC1 detector and F814W filter (805 nm) and ranging from 2 to 2.3 ks in length (project codes:
JC0R02, JC0R02, and J9740). As all observations show a bright point
source at the jet ‘core’, we performed a point spread function (PSF)
subtraction to obtain a measurement of the extended jet. For this
purpose, we used the publicly available _GALFIT_ (GALaxy-FITting;
Peng et al. 2010) software package. All model-fitting was done in the
non-distortion-corrected image frames, where we first masked pixels corresponding to other sources, cosmic ray pollution, and other

image artifacts prior to the fitting. The host galaxies were each fit
with single Sérsic components and we used nearby stars, _TinyTim_,
or a dedicated PSF star observation for the PSF models depending
on which model best-fit the observed quasar point source response.
Finally, we subtracted the best-fit PSF and Sérsic models from the
images and combined the dithered PSF-subtracted image files together with _Astrodrizzle_ (Gonzaga et al. 2012), which also subtracts
the sky background and makes corrections for cosmic ray artifacts
and geometric distortion. All of the jet components for these quasars
remained undetected in the _HST_ imaging except for PKS 0920-397
and PKS 1045-188. We determined jet component flux density upper limits for the non-detections based upon average count rate RMS
deviations in regions the same distance from the core as the jet knots
(identified from radio imaging). For the detected jet components, we
also used this method to determine the background RMS deviations
to be combined with the Poisson count noise when determing our
photometric errors. We used the inverse flux sensitivities and pivot
wavelengths provided in the FITS file headers in order to determine
the conversion from count rate to flux densities. Appropriate extinction corrections were applied (Schlafly & Finkbeiner 2011), along
with the relevant aperture corrections (Bohlin 2016).


**2.5** **Chandra**


We re-analyzed a number of archival _Chandra_ imaging observations
in order to compare radio and X-ray morphologies for our sample, and
to obtain X-ray spectral index measurements for the relevant emission regions. We reduced the X-ray data using the standard methods
described in the Chandra Interactive Analysis of Observations (CIAO
Fruscione et al. 2006) threads. Briefly, we performed the initial reprocessing with the `chandra_repro` task in CIAO using calibration
data from CALDB v4.9.4 and discarded events outside the range of
0.4-8 keV. We examined each light curve and excluded events observed during periods with count rates above 2 _𝜎_ above the mean
level. For sources with multiple observations, each remaining observation was aligned to the one with maximum exposure by matching
the centroids of their cores and were merged using the `merge_obs`
task. Finally, we binned the final events file by a factor of 0.2 (1/5th
native ACIS-S pixel) to produce a sub-pixel image for each source.
We extracted the spectra for each source using the `spectract` task
in CIAO and fit an absorbed power-law model in SHERPA (Freeman
et al. 2001) for events falling in the 0.4-8 keV range; the hydrogen
absorption column density was fixed to the reference value based
on sky location [3] . We binned the spectra to 1 ct/bin and used NelderMead optimization method with WStat statistic to perform the fitting.
Further details concerning the X-ray data analysis and measurements
for each jet will be given in an upcoming publication (Reddy et al.
2022).


**2.6** **Fermi**


For all of our sources, we used all of the available _Fermi_ /LAT data
at the time of analysis, ranging from ∼ 11.7 to 12.1 years (mission
elapse end times for the extracted data can be found in Table 3).
_Fermi_ /LAT event and spacecraft data were extracted using a 10 [◦]

region of interest (ROI), an energy cut of 100 MeV−100 GeV, a
zenith angle cut of 90 [◦], and the recommended event class and type
for point source analysis (128 and 3, respectively). Following the


3 Retrieved using WebPIMMS service ( `[https://heasarc.gsfc.nasa.](https://heasarc.gsfc.nasa.gov/cgi-bin/Tools/w3nh/w3nh.pl)`
`[gov/cgi-bin/Tools/w3nh/w3nh.pl](https://heasarc.gsfc.nasa.gov/cgi-bin/Tools/w3nh/w3nh.pl)` )



_Testing IC/CMB in Resolved Quasar X-ray Jets_ 5


**Figure 1.** Top: _Fermi_ /LAT light curve (upper panel) for PKS 1150+497 with
corresponding TS values for each bin shown in the lower panel. The time bins
correspond to three weeks in good time interval, and the flux from the source
is the integrated photon flux from 100 MeV−100 GeV. The blue arrows in the
light curve represent upper limits for bins in which the source TS was less
than ten. Black data points represent fluxes measured when the TS was greater
than ten, with 1 _𝜎_ error bars. In the TS plot, blue arrows represent TV values
less than zero, while the black points represent positive TS values. Bottom:
Combined-bin flux density upper limits for PKS 1150+497 are shown as lines
without error bars, where upper limits are measured when the source TS was
less than 10. Flux densities are shown with gray 1 _𝜎_ error bars on top of the
lines when the source TS was greater than ten. The flux densities/upper limits
are given in the five Fermi energy bands described in section 2.6.


standard methodology for _Fermi_ /LAT binned likelihood analysis, a
binned counts map was made with 30 logarithmically-spaced energy
bins and 0.2 degree spatial bins. An initial spatial and spectral
model file was constructed with sources up to 10 [◦] outside the
ROI using the publicly available `make4FGLxml.py` script, which
populates the model file with point and extended sources from
the _Fermi_ /LAT 4FGL catalog and an extended source catalog,


MNRAS **000**, 1–23 (2022)

6 _P. Breiding et al._


**Figure 2.** Here we show two example SEDs for the X-ray-jet features analyzed in this study, hosted by the quasars PKS 1150+497 (left) and QSO 0957+561
(right). These SEDs are illustrative of the two possible outcomes of applying our test of the IC/CMB model using _Fermi_ /LAT observations: namely whether
it is ruled out or not based upon the predicted level of MeV-to-GeV gama-ray flux. Observed flux densities are shown with blue circles (plus 1 _𝜎_ error bars),
and bowties represent uncertainties in the measured X-ray spectral indexes. Downward-facing arrows represent upper limits based upon non-detections, where
we show the gamma-ray upper limits determined by _Fermi_ /LAT observations in red. We show the phenomenological synchrotron fits as thin black lines and
the IC/CMB model fits as thick black lines. Gray points mark where the measured radio-to-optical synchrotron flux densities would lie on the shifted IC/CMB
spectra, and thus represent anchor points for the IC/CMB spectra where there is no uncertainty in the predicted flux densities. For QSO 0957+561 we show
two possible synchrotron models which are consistent with the observed radio-to-optical observations as a thin black line and dotted line with corresponding
IC/CMB model curves as a thick black line and dashed line, respectively – see text. The SEDs for the remaining sample can be found in Figures A6 & A7.



respectively. Additionally, the galactic diffuse emission model,
`gll_iem_v07.fits`, and recommended isotropic diffuse emission
model for point sources, `iso_P8R3_SOURCE_V3_v1.txt`, were
used for the analyses. The livetime cubes were computed using
0.025 steps in cos( _𝜃_ ) (where _𝜃_ is the inclination with respect to
the LAT’s z-axis) and 1 [◦] spatial binning. Then all-sky exposure
maps were computed using the same energy binning as the counts
map. After obtaining converged fits with the maximum likelihood
optimizations, we determined upper limits (or lowest flux states)
for the large-scale-jet gamma-ray fluxes from our sources in
the five energy bands: 100 MeV−300 MeV, 300 MeV−1 GeV,
1 GeV−3 GeV, 3 GeV−10 GeV, and 10 GeV−100 GeV. This
procedure is straightforward for sources which are not detected by
_Fermi_, and are not members of the 4FGL point source catalog. In
this case, we forced all of the model parameters fixed and added
a point source with power-law spectral model at the sky position
of our source of interest with normalization of the power law
set free and a fixed photon index of 2 (corresponding to a flat
spectrum in _𝜈_ F _𝜈_ ). The 95% flux density upper limits calculated
with the _Fermi_ tools then apply to the entire source and not
just the large-scale jet. For sources detected by _Fermi_ which
are members of the 4FGL catalog, we use the procedure outlined
below to determine constraints on the large-scale-jet gamma-ray flux.


**Recombined Lightcurves with the** _**Fermi**_ **/LAT**


We now describe a method for detecting the level of a steady flux,
or deriving an upper limit on such a steady flux, when the signal
coincides (or is contaminated by) an unrelated variable component
(as first implemented and described by Meyer & Georganopoulos
2014). We utilize this method for the particular case of determining
(or placing limits on) the level of steady gamma-ray flux coming
from a kpc-scale AGN jet, where the base of the jet (or ’core’, on


MNRAS **000**, 1–23 (2022)



sub-pc scales near the black hole) is known to be a highly variable
and strong gamma-ray emitter (although it should be more widely
applicable in principle). The spatial separation of the two emitting
regions is on the order of thousands of light-years and thus they
are completely (causally) disconnected. Observationally, the angular
separation between the variable core and the steady jet is generally
on the order of arcseconds (or arcminutes at most), which means that
for a telescope like the _Fermi_ /LAT, with at best 0.1 degree resolution,
these two gamma-ray sources appear co-spatial. The general principle
behind this method is to utilize data from periods when the bright
and variable component is in its most quiescent states, allowing for
the longest integration times when the core is not producing a high
level of gamma-ray emission and one has a better chance of detecting
the steady and low level of IC/CMB gamma-ray flux.
In the present study, we implemented this procedure by first producing a light curve, with data subdivided into three week time bins [4]

and executing the pre-likelihood analysis tools on each time bin separately. Then maximum likelihood optimizations were computed for
the data from each time bin to obtain best-fit normalizations for all
sources in the model file, with the other spectral parameters fixed.
Subsequently, the Test Statistic [5] (TS, roughly equivalent to _𝜎_ [2] ) of
our sources were computed for each time bin, and we recombined the
data from lowest to highest TS (one time bin at a time). Next, we re

4 The time bins were defined in terms of good time interval (GTI) time,
corresponding to roughly eight weeks in real time. The time bins are large
enough to avoid being in the photon starved regime, so as to steer clear from
any potential biases in the time bin recombination analysis (defined in this
case as containing at least two photons in any given time bin of the analysis
assuming Poisson statistics).
5 The Test Statistic is formally defined as −2 × the natural logarithm of the

ratio of the maximum likelihood of a model without an additional source to

a model with an additional source at the specified sky position.

ran the pre-likelihood analysis tools on the data from each contiguous
time bin addition, and obtained converged maximum likelihood fits.
After this, we force all of the parameters in the model file fixed except
those of the source of interest before computing flux upper limits (or
fluxes if the TS of the source was greater than 10) for each energy
band. The resulting upper limits (or fluxes) apply to the entire source
including the IC/CMB gamma-ray flux produced by the large-scale
jet. Thus, the gamma-ray limits (or minimum fluxes) obtained from
this analysis apply to the gamma-ray emission from the entire jet, not
just any individual knot or jet component.
In Figure 1, we show an example _Fermi_ /LAT light curve and
corresponding plot of the upper limits/flux densities with each time
bin addition for the source PKS 1150+497 (light curves and combined
bin plots are available as online-only figures). As is readily apparent,
the upper limits decrease with added integration time, until time bins
corresponding to increased flux levels are added into the analysis and
the upper limits begin to increase, eventually becoming increasingly
bright detections. One key feature we would expect to see for any
IC/CMB detection in gamma-rays using this method is a plateau in
flux with decreasing error bars, before photons from the bright and
variable core dominate the flux and the observed fluxes begin to
increase again (see, e.g., Meyer et al. 2019). For any recombined
light curve analysis where we present a flux density instead of an
upper limit in any given band for the minimum flux level consistent
with the steady-state gamma-ray flux, and the recombined light curve
does not have the above-mentioned properties, this flux density likely
represents the minimum _core flux_ over the length of the _Fermi_ /LAT
observations. The IC/CMB gamma-ray flux must be at or below this
level, so any use of these flux minima would represent conservative
estimates when considering whether or not the IC/CMB model for
the large-scale-jet X-ray emission is consistent with the _Fermi_ /LAT
observations.

This methodology relies on the assumption of a bright and variable
core superposed with a weaker, steady state IC/CMB jet component.
We discuss the robustness of the constraints on any potential IC/CMB
component derived from this approach in Appendix A1 with supporting simulations using the _Fermi_ science tools.


**3** **RESULTS**


The primary goal of this study is to assess the viability of the IC/CMB
model accounting for the anomalous X-ray emission in resolved (kpcscale), MSC X-ray jets hosted by AGN. To this end, we analyzed data
from _Fermi_ /LAT observations to search for the predicted high levels
of IC/CMB gamma-ray flux. The expected gamma-ray signature from
the IC/CMB model is a non-variable and (usually) hard spectral state,
which can be isolated from the soft and highly variable bright quasar
core during times when the core is in a quiescent state. Following the
methodology presented in section 2.6, we searched for the plateau
signature in all 23 of the _Fermi_ -detected MSC jets which are members
of the 4FGL catalog. We did not find evidence for such a gammaray signature in any of the _Fermi_ /LAT observations of the AGN
presented here. Thus, we utilize all of the data during times when the
variable core is quiescent in order to obtain the deepest constraints
on the large-scale-jet gamma-ray flux. For the 22 sources not in the
4FGL catalog, we utilize all available _Fermi_ /LAT data for the entire
time _Fermi_ is observing our source of interest in order to obtain the
deepest flux density upper limits. The viability of the IC/CMB model
is then assessed on the basis of whether or not the _Fermi_ /LAT flux
density upper limits (or minimum flux densities) are consistent with
predictions from the IC/CMB model. For cases in which the IC/CMB



_Testing IC/CMB in Resolved Quasar X-ray Jets_ 7


model over-predicts the level of gamma-ray flux consistent with the
_Fermi_ /LAT data, we can rule out the IC/CMB model. Conversely,
if the IC/CMB model curve lies below the minimum _Fermi_ /LAT

flux density upper limits (or flux densities in the case of source
detections), the IC/CMB model can not be ruled out; in the absence
of a clear plateau signature we remain agnostic about its validity as
the correct model.

In Figure 2 we show two representative example SEDs from our
sample to compare the cases in which we can confidently rule out the
IC/CMB model to those in which we can not (the remaining jet SEDs
can be found in Appendix A3). In these SEDs we show observed flux
densities as blue circles with 1 _𝜎_ error bars, and uncertainties of
measured spectral indexes as bowties. For any jet component nondetections, we show flux density upper limits as arrows. Red arrows
specifically denote _Fermi_ /LAT 95% flux density upper limits which
are key to assessing the viability of the IC/CMB model. Phenomenological synchrotron spectral models are fit by eye to the observed
radio-to-optical flux densities using single power laws with highfrequency exponential cut-offs. As described further in Appendix A3,
the synchrotron spectral models have slopes chosen to best-match the
observed X-ray spectral indexes (within the constraints of the radio
flux densities and their associated errors), as this is a requirement of
the IC/CMB model.

As described in Georganopoulos et al. (2006) and Meyer et al.
(2017), the IC/CMB spectral models have the same shape as the synchrotron spectral models but are shifted in frequency and luminosity
by the amount necessary to match the observed X-ray flux densities.
We give the equations parametrizing these shifts in section A (along
with all of the other relevant details for our spectral models), but the
pertinent feature of the IC/CMB model fits is that the IC/CMB spectral shape and associated predicted level of MeV-to-GeV gamma-ray
flux is completely determined by the shape of the radio-to-optical
synchrotron spectrum and the requirement of matching the observed
X-ray flux densities.
In Figure 2, the left-panel SED of knot B from the jet hosted by
the quasar PKS 1150+497 is a clear example of a case in which
we can confidently rule out the IC/CMB model on the basis of its
over-prediction of the large-scale-jet gamma-ray flux. As is clearly
shown in this SED, the red _Fermi_ /LAT flux density upper limits are
well below the IC/CMB model predictions. However, the right-panel
SED for QSO 0957+561 in Figure 2 is a clear example where we
can not rule out the IC/CMB model. This is illustrated by the dotted
synchrotron spectral model curve and corresponding dashed IC/CMB
model curve which remains well below the _Fermi_ /LAT upper limits
in the MeV-to-GeV bands.

The gray circles in the SEDs of Figure 2 show where the observed radio-to-optical synchrotron flux densities would appear in
the shifted IC/CMB spectra. Since these portions of the IC/CMB
spectra correspond to observed portions of the synchrotron spectra,
there is no uncertainty in the IC/CMB model predictions in these regions of the SEDs. Thus, we consider these gray points to be “anchor
points” for the IC/CMB spectra. The case of QSO 0957+561 is an example of how uncertainty in the extrapolation from the observed GHz
synchrotron flux densities to higher energies leads to uncertainty in
the IC/CMB model predictions for the MeV-to-GeV spectrum. If future high-frequency radio or optical/IR/UV observations are able to
detect some portion of this undersampled synchrotron spectrum (especially the peak), this could change to a case in which the IC/CMB
model is ruled out.

Applying the criteria for assessing the viability of the IC/CMB
model described above, we find the IC/CMB model to be ruled out
in 21/45 of the X-ray jets analyzed in this study on the basis of


MNRAS **000**, 1–23 (2022)

8 _P. Breiding et al._


**Table 3.** _Fermi_ Analysis Results


Source Observing Observing Log Predicted Observed Observed
Name End Time Band E1 E2 Freq _𝜈_ F _𝜈,_ IC/CMB _𝜈_ F _𝜈_ _𝜈_ F _𝜈_ Error _𝛿_
(J2000) (MET in s) (GeV) (GeV) (Hz) erg s [−][1] cm [−][2] erg s [−][1] cm [−][2] erg s [−][1] cm [−][2] limit


J1153+4931 617349822 1 0.1 0.3 22.6 4 _._ 06 × 10 [−][13] < 1 _._ 08 × 10 [−][12] < 6.3
2 0.3 1 23.1 5 _._ 09 × 10 [−][13] < 4 _._ 67 × 10 [−][13]

3 1 3 23.6 6 _._ 07 × 10 [−][13] < 2 _._ 01 × 10 [−][13]

4 3 10 24.1 6 _._ 49 × 10 [−][13] < 9 _._ 16 × 10 [−][14]

5 10 100 24.7 5 _._ 32 × 10 [−][13] < 7 _._ 24 × 10 [−][14]


This table is published in its entirety online in machine-readable format, where we show a sample portion here for guidance regarding

its form and content.



over-predicting the large-scale-jet MeV-to-GeV gamma-ray flux consistent with our _Fermi_ /LAT analysis. Furthermore, we have ruled
out the IC/CMB model in 18/36 of the jets from this sample which
are unquestionably MSC X-ray jets and a single radio-to-X-ray synchrotron component is not viable. In total, the IC/CMB model is now
ruled out in 27/54 X-ray jets in which we have used the _Fermi_ /LAT to
search for the required levels of gamma-ray flux under the IC/CMB
model [6] . It is important to note that we use the most conservative
spectral models (given the data), with the lowest predicted MeV-toGeV gamma-ray flux in assessing the viability of the IC/CMB model.
For the remainder of the paper, we will refer to the subset of sources
for which the IC/CMB model is incompatible with the gamma-ray
limits as the "ruled-out" sample, and the remainder as the "unconfirmed" sample. When comparing the “unconfirmed” sample to the
“ruled out” sample, it is important to stress that the “unconfirmed”
sample may still contain X-ray jets which are not truly IC/CMB Xray jets but for which we do not have sufficient data to rule out the
IC/CMB hypothesis. This has the potential to partially wash out sample differences, but it is still important to compare the two samples to
assess any major correlations which still survive the potential sample
contamination.

The particular sources from this study in which we have ruled
out the IC/CMB model are designated in the last column of Table 1. In Table 1 we also give key properties describing our sample,
including the source name, redshift, black hole mass, and angular-tophysical scale conversion factors. Following the methodology outlined in Meyer et al. (2011) and Keenan et al. (2021) and using
data obtained from the NASA/IPAC Extragalactic Database (NED),
we also decomposed the radio spectra into the extended (isotropic)
“lobe” components and beamed “core” components, allowing us to
determine the radio core dominance, R CE . We define R CE for our
sample as the ratio of the modeled core-to-lobe luminosity at 1.4 GHz
(in _𝜈_ L _𝜈_ ), where these values can be found in Table 1. Using these
radio spectral decompositions, we also determined the isotropic lobe
luminosities at 300 MHZ (in _𝜈_ L _𝜈_ ), defined as L ext . We also estimate
kinetic jet powers, L kin, using the scaling relation from Cavagnolo
et al. (2010). Both L ext and L kin are also given in Table 1.
In Table 3 we give the minimum 95% flux density upper limits (or
minimum flux densities) obtained from our _Fermi_ /LAT data analysis, along with the predicted flux densities from the IC/CMB model
and the upper limit on the Doppler factor, _𝛿_, for the jet feature ana

6 This includes the addition of nine X-ray jets for which we have already
published the _Fermi_ /LAT analysis (Meyer & Georganopoulos 2014; Meyer
et al. 2015; Breiding et al. 2017; Meyer et al. 2019; Roychowdhury et al.
2022)


MNRAS **000**, 1–23 (2022)



lyzed as a consequence of our _Fermi_ /LAT flux density upper limits
(or minimum flux densities). These _𝛿_ limits are determined by the
requirement that the IC/CMB spectra not violate the _Fermi_ flux density limits, and assume equipartition magnetic fields for the emission
regions (given in Table 1, and measured [7] using the radio images presented in Figures A3-A4). The equipartition magnetic field strength
assumes an equal energy density between particles and field, and is
the minimum energy state for the system (Burbidge 1959).
In Figures A3-A5 we show X-ray images with radio contours for
each jet from this study in order to highlight the particular radio/X-ray
morphologies for each jet and show the emission regions analyzed
for our SEDs. In Figures A6-A9 we show the jet SEDs complied
with the multi-wavelength data described in section 2, in addition to
the SED data taken from the literature, for each jet analyzed in this
study. We describe precisely where each flux density and spectral
index measurement originates in section A2, where we also discuss
other relevant properties of each source.


**4** **DISCUSSION**


As described in section 3, we consider the IC/CMB model to be
ruled out for a source if the 95% _Fermi_ flux density upper limits (or
minimum flux densities) are below the level required by the IC/CMB
model (for some sources it is clearly ruled out at a greater confidence
than 95%). For the sources in which the _Fermi_ /LAT flux density
upper limits (or minimum flux densities) appear above the IC/CMB
model prediction, we consider the IC/CMB model consistent with the
_Fermi_ /LAT data, and classify the source as ‘unconfirmed’. However,
it is possible future _Fermi_ /LAT observations will yield deeper upper
limits as integration time on-source accumulates, allowing for the
possibility of ruling out the IC/CMB model in any of these jets in the
future. Alternatively, it is possible enough accumulated on-source
integration time may allow for us to detect the IC/CMB gamma-rays
in the future from the unconfirmed sample jets, as demonstrated in
Meyer et al. (2019). The IC/CMB mechanism must still be operating at some level, even if it is not the primary emission process
responsible for the anomalous X-rays observed in these jets.


**4.1** **Alternative Models for the X-ray Emission**


The primary alternative model for the anomalously bright and/or hard
X-ray production in MSC X-ray jets is synchrotron radiation originat

7 For these measurements we assume the EED _𝛾_ min = 10 and estimate radio
jet volumes and flux densities from our images.

**Figure** **3.** _Top:_ Histogram of kinetic jet powers, L kin, for the full sample of
X-ray jets in which we have used _Fermi_ to search for IC/CMB gamma-rays.
The orange shaded region corresponds to the “IC/CMB not ruled out jets”,
and the purple shaded region corresponds to the “IC/CMB ruled out jets”.
_Bottom:_ Histogram of the orientation indicator, OI, where 0 corresponds to
misaligned jets and 1 the aligned jets. The orange shaded region corresponds
to the “IC/CMB not ruled out jets”, and the purple shaded region corresponds
to the “IC/CMB ruled out jets”.


ing from a second, higher-energy EED. If this is the correct physical
description for any of the jets presented here, this implies highly efficient, _in situ_ particle acceleration many kpc from the central engine.
These electrons would be much more energetic than the ones producing the observed radio-to-optical synchrotron spectrum (multi-TeV
versus MeV-to-GeV energies). This high-energy EED would in some
cases need a low-energy cutoff such that it does not overproduce
the observed, and often very faint or non-detected, optical/UV flux
densities in many jets. Furthermore, this distinct, high-energy EED
will inverse-Compton scatter the CMB to TeV gamma-rays, potentially presenting a promising source class for observations with the
upcoming Cherenkov Telescope Array (CTA, Meyer et al. 2015;
Georganopoulos et al. 2006).
Alternatively, it is possible the anomalous X-rays originate
via hadronic emission processes, where the X-rays result either
from direct (relativistic) proton synchrotron radiation, or from
the synchrotron radiation produced by secondary electrons (e.g.,
Petropoulou et al. 2017; Kusunose & Takahara 2017). Hadronic models have a large number of free parameters, and thus it is difficult to



_Testing IC/CMB in Resolved Quasar X-ray Jets_ 9


test such models with e.g., SED-fitting. However, one unique prediction from hadronic models is significant levels of neutrino flux
(Mannheim & Biermann 1989), where spatio-temporal correlations
with blazar gamma-ray flares observed by IceCube over the past few
years offer some support for this scenario (e.g., Kadler et al. 2016).
Additionally, similar to the IC/CMB model, hadronic models imply
highly super-Eddington jets, which offers challenges to the current
accretion paradigm in AGN (e.g., Zdziarski & Bottcher 2015). However, Tchekhovskoy et al. (2010) argue that highly super-Eddington
jets might be accommodated if the jets extract a significant fraction of their energy from black hole spin via the Blandaford-Znajek
mechanism (Blandford & Znajek 1977).
In theory, observations from a high-angular resolution X-ray polarimeter such as the _Imaging_ _X-ray_ _Polarimetry_ _Explorer_ ( _IXPE_,
Weisskopf et al. 2016) could potentially provide another independant line of evidence against the IC/CMB model, since the X-rays
resulting from the IC/CMB mechanism are predicted to have very
low polarization (in contrast to the X-rays from both leptonic synchrotron and hadronic models). However, the relatively large PSF
(∼6.4 arcsec full width half maximum at 2 keV) of _IXPE_ will likely
limit this technique to only the largest jets in angular size (e.g., the
hotspot of Pictor A). Future observations with the Square Kilometer
Array (SKA, Dewdney et al. 2009) will have the requisite frequency
coverage, sensitivity, and angular resolution to search for the verylow-frequency radio light (i.e., tens-to-hundreds of MHz) produced
by the synchrotron radiation of the putative electrons directly upscattering the IC/CMB X-rays (i.e., the low-energy extension of the
GHz-emitting electrons with individual Lorentz factors of _𝛾_ ∼ 100
in the rest frame of the bulk-plasma flow). Determining the correct
physical model which accounts for the anomalously bright and/or
hard X-ray production in MSC X-ray jets is crucial in determining
the physical nature of these jets and the SMBHs which give rise
to them, in addition to what role they play in interacting with their
environments.

For all of the X-ray jets in which the IC/CMB has now been ruled
out by _Fermi_ observations, we can infer that these jets are not as
closely aligned to the line of sight, are not as powerful, and are not
as relativistic on kpc scales as would be required under the IC/CMB
model. Next we discuss some additional properties of the combined
sample of 54 jets for which we have now applied the _Fermi_ test, and
how they relate to the possible physical processes responsible for the
observed X-ray emission.


**4.2** **Jet Alignment & Kinetic Powers**


One requirement of the IC/CMB model is very small jet angles to
the line of sight in order to reproduce the observed, bright X-ray
flux densities via relativistic beaming (Tavecchio et al. 2000; Celotti
et al. 2001). The radio core dominance, R CE, is typically used as a
rough measure of relative jet misalignment in radio-loud AGN (e.g.,
Marin & Antonucci 2016). Qualitatively, this correlation between jet
viewing angle and R CE is expected to result from the fact that the
extended lobe contribution is isotropic while the radio core emission
is highly relativistically beamed. Therefore, if any given jet were
viewed at progressively larger angles to the observers line of sight,
the core should show a commensurate drop in luminosity due to the
radiation being increasingly beamed away from the observer while
the lobe luminosity should remain fixed. However, it was shown in
Keenan et al. (2021) that the distribution of R CE is dependant on
kinetic jet power, where the highest-power jets at log (L ext ) _>_ 43 _._ 5
have a maximum log (R CE ) of ∼1 (L ext being a proxy for jet power).
Additionally, the peak of the distribution of log (R CE ) for low-power


MNRAS **000**, 1–23 (2022)

10 _P. Breiding et al._


**Table 4.** Spectral Index Correlation Tests


Correlation P-Value % Tests

Subset _𝜌_ ¯ s _𝜎_ s 68% Conf. N Failed


All -0.07 0.17 [0.28,0.91] 32 98


All Well-Measured -0.05 0.25 [0.23,0.87] 16 97


Well-Measured -0.26 0.30 [0.45,0.96] 6 99

ruled-out


Well-Measured 0.13 0.44 [0.12,0.73] 10 97
unconfirmed


jets at log (L ext ) _<_ 41 _._ 5 is ∼ 0 _._ 5−1 decades below that of high-power
jets. Therefore, we use the orientation indicator, OI, introduced in
Keenan et al. (2021) as our measure of relative jet misalignment in
our sample of jets, which accounts for this discrepancy in jet power
by also including the core luminosity in the parametrization. The
equation for the OI is


OI = 0 _._ 077 log (L core ) + 0 _._ 021 log (R CE ) − 2 _._ 615 (1)


where L core is the _𝜈_ L _𝜈_ core luminosity. Values of 0 correspond to
the most misaligned jets (i.e., radio galaxies with jets aligned in the
plane of the sky) and 1 the most aligned (i.e., highly aligned blazars
viewed jet-on), where we truncate any values below or above these
boundaries as described in Keenan et al. (2021).
In Figure 3 we show histograms of the kinetic jet power, L kin,
and OI, for our full sample of 54 jets. We discern no significant
difference in the ruled-out versus unconfirmed jets in terms of L kin .
The IC/CMB model generally predicts more powerful jets, so this is
already at odds with the idea that the unconfirmed sources are dominated by IC/CMB X-ray jets. Interestingly, we do find support for
the unconfirmed sources showing some skew towards more aligned
jets than the ruled-out jets when comparing the OI histograms. This
may be indicating that IC/CMB X-ray jets are hidden in our unconfirmed sample, as a high degree of jet alignment is a key feature
of the IC/CMB model. Alternatively, it may be the case that more
aligned jets are brighter _Fermi_ /LAT gamma-ray sources. Thus, the
_Fermi_ /LAT observations will be less constraining in the more aligned
jets than the misaligned jets, making it harder to rule out the IC/CMB
model in the aligned jets. This scenario is partially supported by the
fact the _Fermi_ /LAT 4FGL source catalog is overwhelmingly dominated by blazars (Abdollahi et al. 2020, although there are certainly
some nearby misaligned jets in the catalog). Future _Fermi_ /LAT observations will help address which of these scenarios is correct. As
_Fermi_ continues to monitor the whole sky, it is likely that more
sources will either join the ranks of the ruled-out sample, or finally
show the expected plateau signature from the large-scale jet.


**4.3** **X-ray & Radio Spectral Indexes**


In Figure 4, we show the X-ray and radio spectral index ( _𝛼_ x and
_𝛼_ r, respectively) histograms for the X-ray jet regions analyzed in the
SEDs for this study. In this Figure we also plot the radio spectral
index against the X-ray spectral index for each jet region analyzed.
The expectation from the IC/CMB model is that the radio spectral
index should be the same as the X-ray spectral index, assuming the
observed GHz-frequency radio spectral index is the same as the much


MNRAS **000**, 1–23 (2022)



**Figure** **4.** _Top:_ The X-ray spectral index plotted against the radio spectral
index for each jet analyzed in this study. The jet regions analyzed are given
in Table 3 and denoted in the SEDs in Figures A6-A9. We plot in gray the
least-well-measured indexes, where at least the radio or X-ray spectral index
error exceeds 0.4. The colored indexes correspond to those in which both the
radio and X-ray spectral index errors are less than 0.4. The orange indexes
corresponds to the “IC/CMB not ruled out jets”, and the purple indexes
correspond to the “IC/CMB ruled out jets”. _Bottom:_ Histograms of the X-ray
and radio spectral indexes ( _𝛼_ x and _𝛼_ r, respectively) for all of the jet regions
analyzed in this study — _𝛼_ r is shown in purple and _𝛼_ x in green.


lower and unobserved tens-to-hundreds of MHz-frequency spectral
index probing the portion of the EED directly responsible for the
IC/CMB X-rays. In gray we plot the indexes with errors _>_ 0 _._ 4, where
the colored indexes have both radio and X-ray spectral index errors
_<_ 0 _._ 4 and we consider these the well-measured indexes. In purple are
the well-measured indexes for the ruled-out cases and orange denote
the IC/CMB unconfirmed subsample.
While it does not appear that _𝛼_ x tends to be either harder or
softer than _𝛼_ r, the question remains whether there is any degree
of correlation. The simplest form of the IC/CMB model predicts a
linear correlation between _𝛼_ r and _𝛼_ x . To test this we used the nonparametric Spearman’s rank-order correlation coefficient (Spearman
1904), _𝜌_ s, which assesses the presence of any monotonic dependence
of one variable on another and is in general a more robust indicator
of correlation than the Pearson correlation coefficient which assesses
the degree of linear correlation and can be overly sensitive to outliers
(e.g., Wilcox 2004).
We also looked for any positive dependence between the two quan

**Table 5.** log (R x ) vs log (R CE ) Correlation Tests


Correlation P-Value % Tests

Subset _𝜌_ ¯ s _𝜎_ s 68% Conf. N Failed


All 0.39 0.11 [0.00007,0.02] 54 8
ruled-out 0.36 0.16 [0.002,0.15] 28 36
unconfirmed 0.45 0.16 [0.0006,0.08] 26 22


**Table 6.** Model Parameters for Misalignment Curves in Figure 5


Curve X-ray Radio
Name Panel Zone Zone Γ C Γ X Γ R _𝛼_ X


IC/CMB I ... ... 10 10 10 0.7

100 10 10 0.7

2nd Synch. II Sheath Spine 10 1.5 2.5 0.7
10 2 2.5 0.7

2nd Synch. III Spine Sheath 10 2.5 1.5 0.7
10 1.9 1.5 0.7

Two-Zone IV Spine Sheath 10 3.5 2.5 0
IC/CMB 10 1.9 1.5 0


tities at all. _𝜌_ s values of +1 correspond to high-degrees of positive
correlation, 0 corresponds to uncorrelated data, and -1 to highly negatively correlated data. We determined the significance for _𝜌_ s using
Student’s t-test (Zar 1972). Following the methodology outlined in
Curran (2014), we determine empirical distributions of _𝜌_ s by performing 10,000 trials of bootsrapping with perturbation on the ( _𝛼_ r,
_𝛼_ x ) data pairs. Similar to conventional bootstrapping, this methodology relies on Monte Carlo random sampling with replacement of
each ( _𝛼_ r, _𝛼_ x ) data pair, but also adds some perturbation to the value
of each ( _𝛼_ r, _𝛼_ x ). In this case, we used a perturbative term randomly
chosen from a normal distribution with a mean of zero and standard

deviation corresponding to our index error, but this method does not
in general rely on normally distributed errors for the data. We ran
these bootstrap trials for all indexes, all well-measured indexes, the
well-measured indexes belonging to the ruled-out subsample, and
the well-measured indexes belonging to the unconfirmed subsample.
In Table 4 we give the results of these correlation tests, including
the mean and standard deviation of _𝜌_ s ( _𝜌_ ¯ s and _𝜎_ s, respectively), 68%
confidence limits for the corresponding p-values, the number of data
pairs for each correlation test (N), and percent of bootstrapped trials
showing no degree of positive correlation. In this case, failing the significance test is defined as having a p-value _>_ 0 _._ 05 for a one-tailed
Student’s t-test, meaning we can not reject the null hypothesis at
_>_ 95% confidence that _𝛼_ r is uncorrelated with _𝛼_ x . Interestingly, the
correlation tests between _𝛼_ r and _𝛼_ x for all subsets considered overwhelmingly fail to find a significant correlation. This result suggests
that distinct particle populations are responsible for the observed
radio and X-ray emission in these jets, arising from either different
physical processes, different physical conditions, or some combination thereof. This is clearly in conflict with the expectations from the
IC/CMB model, but a larger sample size of precise spectral index
measurements would be desirable for confirming this result.


**4.4** **X-ray & Radio Beaming Patterns**


X-rays from the IC/CMB mechanism are expected to be highly relativstically beamed, meaning highly focused along the axis of the



_Testing IC/CMB in Resolved Quasar X-ray Jets_ 11


bulk-plasma flow in these jets. The equation governing the relativistic beaming pattern for IC/CMB radiation is


L = L [′] _𝛿_ [p][+][1][+][2] _[𝛼]_ [r] (2)


with p=2 for a continuous flow and p=3 for discrete moving blobs
(Dermer 1995; Georganopoulos et al. 2001). Here, L is the luminosity
in the galaxy rest frame assuming isotropy, L [′] is the solid-angleintegrated luminosity in the jet frame, _𝛼_ r is the radio spectral index,
and _𝛿_ is the Doppler factor. In the case of synchrotron emission, the
expected beaming pattern is given by (Dermer 1995)


L = L [′] _𝛿_ [p][+] _[𝛼]_ [r] _._ (3)


Increasing the angle of the jet to the line of sight decreases the value
of _𝛿_ . Therefore, the observed IC/CMB X-ray flux should decrease
faster than the synchrotron radio flux if viewed at progressively larger
angles to the line of sight due to the stronger dependence on _𝛿_ for
IC/CMB. We define a parameter known as the X-ray dominance, R x,
which is the ratio of the 1 keV X-ray flux density to the 8.6 GHz
radio flux density for the extended jet regions analyzed in our SEDs
(in _𝜈_ F _𝜈_, where the values of R x for our sample can be found in
Table 1). In the four panels of Figure 5, we show log-space plots of
R x against R CE for the full sample of 54 X-ray-jet features analyzed
in this and other recent publications. We binned the jets into three
different groups corresponding to their relative alignment to the line
of sight, assigning different colors to each bin: 0 _<_ OI _<_ 0 _._ 33 (most
misaligned, green), 0 _._ 33 _<_ OI _<_ 0 _._ 66 (medium alignment, sky blue),
and 0 _._ 66 _<_ OI _<_ 1 (most aligned, royal blue). We also placed black
circles around the jets in which we have ruled out the IC/CMB model
with _Fermi_ /LAT results in order to compare any potential correlations
between the ruled-out and the unconfirmed groups. Following the
same methodology as in section 4.3, we tested for any monotonic
correlations between log (R x ) and log (R CE ) by computing empirical
distributions of _𝜌_ s based upon 10,000 boostrapped trials (in this case
we did not add perturbation to the bootstrapping since errors on
log R x and log R CE are negligible). We performed correlation tests
for subsets consisting of all of the jets, the ruled-out subsample, and
the unconfirmed subsample; the results of these correlation tests are
given in Table 5.
The majority of bootstrap trials in all of these subsamples,
and mean _𝜌_ s values for each subsample, indicated significant (pvalue _<_ 0 _._ 05) positive correlations. Not surprisingly the most significant results were for the full sample of jets, likely due to the
larger sample size. Accordingly, and since we have no expectation
for the functional form of the monotonic dependence of log (R x )
on log (R CE ), we fit ordinary least squares (OLS) linear regression
lines to both the ruled-out and unconfirmed subsamples in the 10,000
bootstrapped trials. We plot in all panels of Figure 5 the resulting
mean best-fit regression lines with corresponding shaded 68% confidence intervals constructed from the bootstrapped statistics. As is
evident, the 68% confidence regions of the OLS regression lines are
largely overlapping, indicating no significant difference in the best-fit
slope between the ruled-out and unconfirmed groups.
To demonstrate in Figure 5 how a single hypothetical jet would
move through the plane when misaligned, we plot as connected black
points the ‘de-beaming path’ for different assumed models of Xray emission, using equation 2 (for IC/CMB) and equation 3 (for
synchrotron). This fiducial jet is assumed to be at an initial alignment
of 5 degrees to the line of sight and connected points are spaced by
5 degrees. We show two curves corresponding to different jet model
parameters for each panel of Figure 5, as given in Table 6. We shown


MNRAS **000**, 1–23 (2022)

12 _P. Breiding et al._































**Figure** **5.** The X-ray dominance, R x, for the jet features analyzed in Figures A6-A9, plotted against the core dominance, R CE, for our full sample of 54 jets
we have now used _Fermi_ /LAT observations to test the IC/CMB model (in log-log space). We binned the jets according to their alignment to the line of sight,
assigning different colors to each bin: 0 _<_ OI _<_ 0 _._ 33 (most misaligned, green), 0 _._ 33 _<_ OI _<_ 0 _._ 66 (medium alignment, sky blue), and 0 _._ 66 _<_ OI _<_ 1 (most
aligned, royal blue). As expected, R CE reasonably tracks jet orientation as parametrized by OI. We also placed black circles around the jets in which we have
ruled out the IC/CMB model with _Fermi_ /LAT results. Error bars are not shown as they are on the order of the size of the plotted points. We plot in each panel
the mean OLS linear regression lines (plus 68% confidence regions) for the ruled-out and unconfirmed subsamples, in purple and orange, respectively. Each
different panel corresponds to the misalignment of a fiducial jet under different jet models as described in section 4.4, where the data for each panel is the
same. The jet parameters describing each black misalignment curve are given in Table 5. The black circles on the misalignment curves mark incremental 5
degree misalignments to the line of sight, starting at an initial alignment of five degrees. The gray zones between the misalignment curves show the expected
misalignment for parameter values varying between those given in Table 5.



in gray the expected misalignment zone corresponding to a range of
jet model parameter values between those which delineate the two
curves. These misalignment curves assume a flat radio core spectral
index of 0, a radio spectral index for the observed large-scale-jet
radio emission of 0.7, and a value of p equal to 0 for the core and 1
for the large-scale-jet component. Additionally, this analysis assumes
the angle of the (kpc-scale) large-scale-jet to the line of sight to be
the same as that for the pc-scale core.
In panel I of Figure 5 we show the expected misalignment of the
fiducial jet under the standard single zone IC/CMB model we have
been testing in this study [8] . For this case, the misalignment zone is


8 Using equations 2 & 3, it can be shown that R CE ∝ _𝛿_ core [p][+] _[𝛼]_ core and


MNRAS **000**, 1–23 (2022)



entirely determined by a range of core bulk-flow Lorentz factors,
Γ C, between 10 and 100. It is clear that the observed correlation
between log (R x ) and log (R CE ) is much less steep than the IC/CMB
model predictions — albeit with a large degree of scatter which can
be accounted for by individual jet-to-jet variations. This suggests
that the X-rays in these jet regions are only moderately stronger
beamed than the radio synchrotron radiation. While we can not rule
out the possibility that a few (single-zone) IC/CMB X-ray jets are


R x ∝ _𝛿_ knot [1][+] _[𝛼]_ [knot] under the IC/CMB model. Here, _𝛿_ knot is the Doppler factor of the large-scale-jet component, _𝛿_ core is the Doppler factor of the core,
_𝛼_ knot is the radio spectral index for the large-scale-jet component, and _𝛼_ core
is the core spectral index.

hidden in Figure 5, they are manifestly not the dominant type of
X-ray jet in our sample. Furthermore, the existence of a correlation
for the ruled-out subsample already necessitates another physical
model, and the similarity in regression slope to the unconfirmed
subsample suggests they may be of similar physical origin. However,
larger sample sizes are needed to confirm these correlations and
help tease apart the physical mechanism(s) responsible. Below we
discuss different multi-zone emission models which can account for
the observed log (R x )−log (R CE ) correlation through the adjustment
of an increased number of tuneable model parameters.
In panels II-IV of Figure 5, we consider two-zone models for the
large-scale jet in which there is a fast-flowing jet spine surrounded by
a slower-moving jet sheath (e.g., Sol et al. 1989; Celotti et al. 2001).
In all of these two-zone models, we only consider “mildly relativstic” large-scale jets with Γ ranging between 1.5 and 3.5, and more
relativistic cores with Γ C = 10. We differentiate the Lorentz factors
between the X-ray-emitting zones and radio-synchrotron emitting
zones by Γ X and Γ R, respectively, which are given in Table 5. We
also give the spectral index for the particles responsible for the X-rays
in Table 5, _𝛼_ X . In the context of 2nd synchrotron models, _𝛼_ X corresponds to the observed X-ray spectral index for the jet region which
is assumed to be synchrotron in origin. In the standard IC/CMB or
“two-zone” IC/CMB models, _𝛼_ X corresponds to the radio spectral
index of the low-energy electrons upscattering the CMB to X-ray energies. For the standard IC/CMB model, we assume _𝛼_ X is the same as
the observed GHz radio spectral index for the large-scale jets. However, for the “two-zone” IC/CMB model in panel IV, _𝛼_ X corresponds
to an electron population in the jet spine while the observed radio
synchrotron emanates from the jet sheath.
As is evident from Figure 5, both the 2nd synchrotron and “twozone” IC/CMB models of panels III and IV can account for the
more mildly beamed X-rays in a manner which is consistent with
the observed correlation. What these models have in common is

that the X-rays originate from particles in a faster-moving spine,
while the radio synchrotron emission originates from particles in a
slower-moving surrounding sheath layer. In panel II, we show a twozone 2nd synchrotron model in which the X-rays originate from the
slower-moving sheath and the radio originates from a faster-moving
spine. In this case, we would expect a negative correlation in the
log (R x ) − log (R CE ) plane, as opposed to the positive correlation we
observe.

These results imply that these X-ray jet regions should be narrower than the corresponding radio-jet regions in these systems, and
should be resolvable for very nearby jets. In fact, X-ray jets which are
narrower than their radio counterparts have been observed in several
cases, one noteable example being the MSC X-ray jet in 3C 353
(Kataoka et al. 2008). Interestingly, the X-ray emission in 3C 353
is modeled as a 2nd synchrotron component by the authors, where
the IC/CMB model is ruled out on the basis of an X-ray counter-jet
detection. Also of note in the context of 2nd synchrotron models is
the observation of optical jets which are narrower than their radio-jet
counterparts (e.g., Sparks et al. 1994). Together, these results suggest
that if we are observing a 2nd, higher-energy synchrotron component
in these jets, the high-energy particles are accelerated in the fastermoving inner spine and not the sheath boundary layers as suggested
in shear-layer acceleration models (e.g., Tavecchio 2021). However,
as shown in panel IV, we can not rule out the possibility that a “two
zone” IC/CMB model is operating in some of these jets. This is different from the (single-zone) IC/CMB model we have been testing in
this paper which requires the same electron population that is emitting
the radio-to-optical synchrotron radiation to be responsible for upscattering the CMB to X-rays. In the type of two-zone IC/CMB model



_Testing IC/CMB in Resolved Quasar X-ray Jets_ 13


shown in panel IV, the electrons up-scattering the CMB to X-rays are
in the spine and distinct from the electron population in the sheath
responsible for producing the observed radio synchrotron spectrum.
However, even though this type of two-zone IC/CMB model is more
consistent with the observed log (R x ) − log (R CE ) correlation and
has not been ruled out by our _Fermi_ test, it suffers from many of the
same problems as the single-zone IC/CMB model (e.g., knotty X-ray
jets, X-ray flux variability, etc.) and may only be applicable to the
most aligned jets which remain highly relativistic on kpc scales.


**4.5** **Evidence For Jet Deceleration**


The IC/CMB model requires large bulk-flow Lorentz factors, Γ, on
kpc scales (i.e. highly relativistic, Γ ∼ 10) in addition to being
oriented at small angles to the line of sight. Very Long Baseline
Interferometry (VLBI) observations of apparent superluminal motion
for features at the base of AGN jets provide direct evidence for highly
relativistic bulk-flow speeds on pc scales (e.g., Lister et al. 2013).
Measurement of the maximum apparent speed ( _𝛽_ app, the apparent
speed of the jet feature in units of the speed of light, c) for these
features, gives the most stringent lower limit on Γ and upper limit on
the angle of the jet to the line of sight on the pc scale. The _Fermi_
limits presented in this work allow us to place upper limits on _𝛿_ /B
for the kpc-scale jet such that the IC/CMB model curves fall below
these limits. If we further assume that the magnetic field is at its
equipartition value (these values are given in Table 1), then these
observations give limits on the Doppler factor, _𝛿_ (these limits can be
found in Table 3).
In Table 7, we show the maximum _𝛽_ app values obtained with
VLBI (which we label as _𝛽_ max ) for the sources in which we could
find measurements in the literature, as noted in Table 7. In Table 7
we also give the maximum angle of the jet to the line of sight, _𝜃_ max,
and minimum bulk-flow Lorentz factor, Γ min _,_ pc, which are consistent
with the measured values of _𝛽_ max [9] (where _𝜃_ max and Γ min _,_ pc apply to
the pc-scale portion of the base of the jet). Finally, in the last column
of Table 7 we give the upper limit to the bulk-flow Lorentz factor,
Γ max _,_ kpc, for the kpc-scale jet feature analyzed in our jet SEDs.
Γ max _,_ kpc is determined by our upper limits on the Doppler factor,
assuming an equipartition magnetic field. We additionally give error
bars on Γ max _,_ kpc representing the Γ max _,_ kpc limits corresponding
to a magnetic field strength a factor of two out of equipartition.
Furthermore, we assume the jet angle to the line of sight for the kpcscale jet is less than _𝜃_ max . This assumption is reasonable allowing
that the jet does not significantly bend in the plane of observation.
In Figure 4.5, we plot the maximum Lorentz factor for the kpcscale jet against the minimum Lorentz factor for the pc-scale jet for
the sources listed in Table 7. The straight dashed line shows the case
where the Lorentz factor limits of the pc-scale and kpc-scale jets are
equal. The Γ limits plotted all fall well below this line, indicating
that the jets are at most mildly relativistic on the kpc scale and are
experiencing significant deceleration from pc to kpc scales. These
sources could only remain highly relativistic if they are very far from
equipartition, which would greatly increase the energy content in
these jets. Thus, these results suggest FR II quasar jets decelerate at or
before kpc scales, similar to what has previously been shown for FR I
radio galaxies on the basis of the jet and counter-jet intensity profiles


9 It is a straightforward exercise to show that Γ min _,_ pc = _[𝛽]_ max _𝛽_ ≊ _𝛽_ max

(where _𝛽_ is the true physical speed of the jet flow in units of c) and



_𝜃<_ cos [−][1] _𝛽_ max [2] −1
� _𝛽_ max [2] +1



≡ _𝜃_ max .
�



MNRAS **000**, 1–23 (2022)

14 _P. Breiding et al._


**Table 7.** Jet Deceleration Parameters


Source Common

Name Name _𝛽_ max _𝜃_ max Γ max _,_ kpc
(J2000) ( [◦] )


J0108+0135 [†] PKS B0106+013 26.8 [c] 4.27 4.35 [+] − [2] 1 _[.]_ _._ [77] 40

J0237+2848 4C 28.07 27.3 [e] 4.20 8.41 [+] − 3 _._ 53

J0418+3801 3C 111 8.42 [a] 13.5 ...


J0433+0521 3C 120 9.09 [f] 12.6 ...


J0607−0834 [†] PKS 0605−085 32.8 [a] 3.49 6.42 [+] − [5] 2 _[.]_ _._ [98] 16
J0728+6748 [†] 3C 179 8.99 [i] 12.7 1.54 [+] − [0] 0 _[.]_ _._ [768] 350

J0741+3112 B2 0738+31 11.1 [e] 10.3 ...


J0830+2410 B2 0827+24 24.7 [k] 4.64 5.74 [+] − 2 _._ 08

J0840+1312 [†] 4C 13.38 13.3 [e] 8.60 2.27 [+] − [1] 0 _[.]_ _._ [28] 659
J0922−3959 [†] PKS 0920−397 30.8 [d] 3.72 2.23 [+] − [0] 0 _[.]_ _._ [893] 584

J1048−1909 PKS 1045−188 10.9 [b] 10.5 ...


J1058+1951 [†] 4C 20.24 10.5 [l] 10.9 1.48 [+] − [0] 0 _[.]_ _._ [589] 315
J1130−1449 [†] PKS 1127-145 31.6 [k] 3.63 2.33 [+] − [0] 0 _[.]_ _._ [937] 619
J1153+4931 [†] PKS 1150+497 18.2 [a] 6.29 3.71 [+] − [3] 1 _[.]_ _._ [24] 27

J1205−2634 PKS 1202−262 11.0 [a] 10.4 ...


J1224+2122 4C 21.35 28.0 [a] 4.09 9.98 [+] − 4 _._ 47


J1632+8232 NGC 6251 0.156 [b] 162 ...


J1642+3948 3C 345 24.6 [h] 4.66 ...


J1642+6856 [†] 4C 69.21 24.9 [c] 4.60 2.17 [+] − [0] 0 _[.]_ _._ [864] 557

J1746+6226 4C 62.29 15.2 [c] 7.53 ...


J1829+4844 3C 380 15.4 [l] 7.43 4.46 [+] − 1 _._ 76

J1849+6705 8C 1849+670 31.6 [e] 3.63 ...


J1927+7358 4C 73.18 22.4 [d] 5.11 ...


J2005+7752 S5 2007+777 4.40 [g] 25.6 ...


J2158−1501 PKS 2155−152 21.5 [j] 5.33 ...


J2203+3145 4C 31.63 8.81 [j] 13.0 ...


J2218−0335 PKS 2216−038 6.91 [a] 16.5 ...


J2253+1608 3C 454.3 25.4 [i] 4.51 ..


_𝛽_ max measurements are obtained from the following literature sources
(corresponding to the superscripts in the _𝛽_ max column): (a) Frey et al.
(2015), (b) Homan et al. (2001), (c) Jiang et al. (2002), (d) Jorstad et al.
(2005), (e) Jorstad et al. (2017), (f) Kellermann et al. (2004), (g) Lister
et al. (2009), (h) Lister et al. (2013), (i) Lu et al. (2012), (j) Piner et al.
(2001), (k) Piner et al. (2012), (l) Sudou & Iguchi (2011).

 - These sources are the ones which make the plot of Γ max _,_ kpc vs Γ min _,_ pc
shown in Figure 6, where they all show evidence of pc-to-kpc scale
jet deceleration. The sources in which an ellipses is given for Γ max _,_ kpc
have Doppler factor limits not constraining enough to be translated
into Lortentz factor limits for the given _𝛽_ max measurements. The errors
on Γ max _,_ kpc represent magnetic field strengths a factor of two out of
equipartition. For cases in which the upper bound on Γ max _,_ kpc could
not be determined due to the implied _𝛿_ limit for this magnetic field
value, we leave this error value empty.


MNRAS **000**, 1–23 (2022)



33


29


25


21


17


13


9


5


1


1 5 9 13 17 21 25 29 33


Γ min, pc


**Figure** **6.** Plot of the maximum bulk flow Lorentz factor for the kpc-scale
jet against the minimum bulk flow Lorentz factor for the pc-scale jet for the
sources shown in Table 7. The black circles have error bars showing the result
assuming the magnetic field can be out of equipartition by a factor of two.
The dashed line shows the case where Γ min _,_ pc =Γ max _,_ kpc . We consider points
below this line evidence for deceleration.


(e.g., Laing & Bridle 2014). Common mechanisms invoked to expain
this jet-deceleration in FR I radio galaxies are the entrainment of
ambient cold gas by a shear boundary layer (e.g., Bicknell 1984;
De Young 1986, 1993), various MHD instabilities (e.g., Perucho &
Martí 2007; Rossi et al. 2008; Gourgouliatos & Komissarov 2018),
and mass-loading by stars/stellar winds (e.g., Perucho et al. 2014;
Torres-Albà 2020; Anglés-Castillo et al. 2021).
Another interpretation of this result is again motivated by a spinesheath jet structure, as discusses in section 4.4. If the observed radioto-optical synchrotron radiation originates from a slower-moving
sheath surrounding a faster-moving inner spine, then our _𝛿_ and Γ
upper limits for the large-scale-jet regions apply to the sheath and not
the inner spine. Thus, regardless of the X-ray emission mechanism,
it is still possible the inner jet spines of the FR IIs in Figure 6 may
remain highly relativistic on kpc scales while slower boundary sheath
layers dominate the observed radiative output at ∼GHz frequencies.


**5** **SUMMARY & CONCLUSIONS**


In this study, we used _Fermi_ /LAT observations to search for MeV-toGeV gamma-rays predicted to result from the IC/CMB mechanism
in extragalactic kpc-scale X-ray jets. We did not find evidence for
IC/CMB gamma-rays in any of the observed X-ray jets, and we
subsequently ruled out the IC/CMB model in 21/45 of the X-ray jets
from this study on the basis of over-predicting the observed gammaray flux or limits. In the sources for which the IC/CMB model is not
ruled out by our _Fermi_ /LAT analysis, it is possible future _Fermi_ /LAT
observations will yield deeper limits that do rule out the IC/CMB
model. Alternatively, it is possible we will detect IC/CMB gammarays from some subset of these jets in the future. Additionally, for
many of these jets in which we could not rule out the IC/CMB
model, we identify how future sub-mm imaging with ALMA or
the SMA, or optical/IR/UV imaging with the _HST_ or _James_ _Webb_
_Space Telescope (JWST)_ can help determine the shape of the radioto-optical synchrotron spectrum for better-applying our _Fermi_ test
and measuring the limits on _𝛿_ .

We have also presented additional lines of evidence against the
IC/CMB model relating to the lack of correlation observed between
radio and X-ray spectral indexes for the jet regions analyzed, and significant positive correlation between X-ray and radio-core dominance
which has a much lower slope than required under the conventional
single-zone IC/CMB model addressed in this study. This softer correlation can be accounted for by various multi-zone emission models,
where we in particular consider a two-zone synchrotron and IC/CMB
model motivated by a spine-sheath jet structure. Finally, we present
evidence for pc-to-kpc-scale deceleration of a subset of our jets based
upon superluminal motion measured for the pc-scale VLBI jets combined with the upper limits on the Doppler factors for the kpc-scale
emitting regions analyzed in our SEDs. The corresponding upper
limits we present on the bulk-flow Lorentz factors for the kpc-scale
jet regions represent a new method of constraining jet speed in kpcscale AGN jets, and suggest kpc-scale deceleration in FR II quasar
jets.


**DATA AVAILABILITY**


The data used in this article are all publicly available. The
_Fermi_ /LAT data can be found here: https://fermi.gsfc.nasa.gov/cgibin/ssc/LAT/LATDataQuery.cgi. The _Chandra_ data can be found
here: https://cda.harvard.edu/chaser/. The _HST_ data can be found
here: https://mast.stsci.edu/search/ui/#/hst. The radio interferometric
data can be found here: https://data.nrao.edu/portal/#/.


**REFERENCES**


[Abdollahi S., et al., 2020, ApJS, 247, 33](http://dx.doi.org/10.3847/1538-4365/ab6bcb)
Anglés-Castillo A., Perucho M., Martí J. M., Laing R. A., 2021, [MNRAS,](http://dx.doi.org/10.1093/mnras/staa3291)

[500, 1512](https://ui.adsabs.harvard.edu/abs/2021MNRAS.500.1512A)
[Begelman M. C., Blandford R. D., Rees M. J., 1980, Nature, 287, 307](http://dx.doi.org/10.1038/287307a0)
[Benford G., 1978, MNRAS, 183, 29](http://dx.doi.org/10.1093/mnras/183.1.29)
[Bicknell G. V., 1984, ApJ, 286, 68](http://dx.doi.org/10.1086/162577)
[Blandford R. D., Znajek R. L., 1977, MNRAS, 179, 433](http://dx.doi.org/10.1093/mnras/179.3.433)
[Bohlin R. C., 2016, AJ, 152, 60](http://dx.doi.org/10.3847/0004-6256/152/3/60)
Breiding P., Meyer E. T., Georganopoulos M., Keenan M. E., DeNigris N. S.,
[Hewitt J., 2017, ApJ, 849, 95](http://dx.doi.org/10.3847/1538-4357/aa907a)
[Burbidge G. R., 1959, ApJ, 129, 849](http://dx.doi.org/10.1086/146680)
[Cara M., et al., 2013, ApJ, 773, 186](http://dx.doi.org/10.1088/0004-637X/773/2/186)
Cavagnolo K. W., McNamara B. R., Nulsen P. E. J., Carilli C. L., Jones C.,
[Bîrzan L., 2010, ApJ, 720, 1066](http://dx.doi.org/10.1088/0004-637X/720/2/1066)
[Celotti A., Ghisellini G., Chiaberge M., 2001, MNRAS, 321, L1](http://dx.doi.org/10.1046/j.1365-8711.2001.04160.x)
[Chartas G., et al., 2000, ApJ, 542, 655](http://dx.doi.org/10.1086/317049)
Chartas G., Gupta V., Garmire G., Jones C., Falco E. E., Shapiro I. I., Tavec[chio F., 2002, ApJ, 565, 96](http://dx.doi.org/10.1086/324485)
[Cheung C. C., 2004, ApJ, 600, L23](http://dx.doi.org/10.1086/381366)
[Cheung C. C., Stawarz Ł., Siemiginowska A., 2006, ApJ, 650, 679](http://dx.doi.org/10.1086/506908)
[Chiaberge M., Gilli R., Lotz J. M., Norman C., 2015, ApJ, 806, 147](http://dx.doi.org/10.1088/0004-637X/806/2/147)
[Clarke D. A., Norman M. L., Burns J. O., 1986, ApJ, 311, L63](http://dx.doi.org/10.1086/184799)
[Clautice D., et al., 2016, ApJ, 826, 109](http://dx.doi.org/10.3847/0004-637X/826/2/109)
[Curran P. A., 2014, arXiv e-prints, p. arXiv:1411.3816](https://ui.adsabs.harvard.edu/abs/2014arXiv1411.3816C)
[De Young D. S., 1986, ApJ, 307, 62](http://dx.doi.org/10.1086/164393)
[De Young D. S., 1993, ApJ, 405, L13](http://dx.doi.org/10.1086/186754)
[Dermer C. D., 1995, ApJ, 446, L63](http://dx.doi.org/10.1086/187931)
[Dermer C. D., Atoyan A., 2004, ApJ, 611, L9](http://dx.doi.org/10.1086/423667)
Dewdney P. E., Hall P. J., Schilizzi R. T., Lazio T. J. L. W., 2009, [IEEE](http://dx.doi.org/10.1109/JPROC.2009.2021005)
[Proceedings, 97, 1482](http://dx.doi.org/10.1109/JPROC.2009.2021005)
Evans D. A., Hardcastle M. J., Croston J. H., Worrall D. M., Birkinshaw M.,

[2005, MNRAS, 359, 363](http://dx.doi.org/10.1111/j.1365-2966.2005.08900.x)
Freeman P., Doe S., Siemiginowska A., 2001, in Starck J.-L., Murtagh
F. D., eds, Society of Photo-Optical Instrumentation Engineers (SPIE)



_Testing IC/CMB in Resolved Quasar X-ray Jets_ 15


Conference Series Vol. 4477, Astronomical Data Analysis. pp 76–87
( `[arXiv:astro-ph/0108426](http://arxiv.org/abs/astro-ph/0108426)` [), doi:10.1117/12.447161](http://dx.doi.org/10.1117/12.447161)
[Frey S., Paragi Z., Fogasy J. O., Gurvits L. I., 2015, MNRAS, 446, 2921](http://dx.doi.org/10.1093/mnras/stu2294)
Fruscione A., et al., 2006, in Silva D. R., Doxsey R. E., eds, Society of PhotoOptical Instrumentation Engineers (SPIE) Conference Series Vol. 6270,
Society of Photo-Optical Instrumentation Engineers (SPIE) Conference
[Series. p. 62701V, doi:10.1117/12.671760](http://dx.doi.org/10.1117/12.671760)
[Gentry E. S., et al., 2015, ApJ, 808, 92](http://dx.doi.org/10.1088/0004-637X/808/1/92)
[Georganopoulos M., Kirk J. G., Mastichiadis A., 2001, ApJ, 561, 111](http://dx.doi.org/10.1086/323225)
[Georganopoulos M., Perlman E. S., Kazanas D., McEnery J., 2006, ApJ, 653,](http://dx.doi.org/10.1086/510452)
[L5](http://adsabs.harvard.edu/abs/2006ApJ...653L...5G)

[Godfrey L. E. H., et al., 2012a, ApJ, 755, 174](http://dx.doi.org/10.1088/0004-637X/755/2/174)
[Godfrey L. E. H., et al., 2012b, ApJ, 758, L27](http://dx.doi.org/10.1088/2041-8205/758/2/L27)
Gonzaga S., Hack W., Fruchter A., Mack J., 2012, The DrizzlePac Handbook
[Gopal-Krishna Wiita P. J., 2000, A&A, 363, 507](https://ui.adsabs.harvard.edu/abs/2000A&A...363..507G)
[Gourgouliatos K. N., Komissarov S. S., 2018, Nature Astronomy, 2, 167](http://dx.doi.org/10.1038/s41550-017-0338-3)
[Hardcastle M. J., Sakelliou I., Worrall D. M., 2005, MNRAS, 359, 1007](http://dx.doi.org/10.1111/j.1365-2966.2005.08966.x)

[Hardcastle M. J., Croston J. H., Kraft R. P., 2007, ApJ, 669, 893](http://dx.doi.org/10.1086/521696)
[Hardcastle M. J., et al., 2016, MNRAS, 455, 3526](http://dx.doi.org/10.1093/mnras/stv2553)

[Harris D. E., Krawczynski H., 2006, ARA&A, 44, 463](http://dx.doi.org/10.1146/annurev.astro.44.051905.092446)
Harris D. E., Hjorth J., Sadun A. C., Silverman J. D., Vestergaard M., 1999,

[ApJ, 518, 213](http://dx.doi.org/10.1086/307284)
[Harris D. E., Mossman A. E., Walker R. C., 2004, ApJ, 615, 161](http://dx.doi.org/10.1086/424442)
[Harris D. E., et al., 2019, ApJ, 873, 21](http://dx.doi.org/10.3847/1538-4357/ab01ff)
[Hogan B. S., Lister M. L., Kharb P., Marshall H. L., Cooper N. J., 2011, ApJ,](http://dx.doi.org/10.1088/0004-637X/730/2/92)

[730, 92](https://ui.adsabs.harvard.edu/abs/2011ApJ...730...92H)

Homan D. C., Ojha R., Wardle J. F. C., Roberts D. H., Aller M. F., Aller
[H. D., Hughes P. A., 2001, ApJ, 549, 840](http://dx.doi.org/10.1086/319466)
[Ighina L., et al., 2021, arXiv e-prints, p. arXiv:2111.08632](https://ui.adsabs.harvard.edu/abs/2021arXiv211108632I)
Jiang D. R., Zhou J. F., Hong X. Y., Gurvits L. I., Shen Z. Q., Chen Y. J.,
[2002, ApJ, 577, 69](http://dx.doi.org/10.1086/342145)
[Jones T. W., Owen F. N., 1979, ApJ, 234, 818](http://dx.doi.org/10.1086/157561)
Jones T. W., Nolting C., O’Neill B. J., Mendygral P. J., 2017, [Physics](http://dx.doi.org/10.1063/1.4978620) of
[Plasmas, 24, 041402](http://dx.doi.org/10.1063/1.4978620)

[Jorstad S. G., Marscher A. P., 2004, ApJ, 614, 615](http://dx.doi.org/10.1086/423800)
[Jorstad S. G., Marscher A. P., 2006, Astronomische Nachrichten, 327, 227](http://dx.doi.org/10.1002/asna.200510512)

[Jorstad S. G., et al., 2005, AJ, 130, 1418](http://dx.doi.org/10.1086/444593)

[Jorstad S. G., et al., 2017, ApJ, 846, 98](http://dx.doi.org/10.3847/1538-4357/aa8407)
[Kadler M., et al., 2016, Nature Physics, 12, 807](http://dx.doi.org/10.1038/nphys3715)
[Kataoka J., et al., 2008, ApJ, 685, 839](http://dx.doi.org/10.1086/591024)
Keenan M., Meyer E. T., Georganopoulos M., Reddy K., French O. J., 2021,

[MNRAS, 505, 4726](http://dx.doi.org/10.1093/mnras/stab1182)

[Kellermann K. I., et al., 2004, ApJ, 609, 539](http://dx.doi.org/10.1086/421289)
[Kharb P., Lister M. L., Marshall H. L., Hogan B. S., 2012, ApJ, 748, 81](http://dx.doi.org/10.1088/0004-637X/748/2/81)
[Kozłowski S., 2017, ApJS, 228, 9](http://dx.doi.org/10.3847/1538-4365/228/1/9)
[Kusunose M., Takahara F., 2017, ApJ, 835, 20](http://dx.doi.org/10.3847/1538-4357/835/1/20)
[Laing R. A., Bridle A. H., 2014, MNRAS, 437, 3405](http://dx.doi.org/10.1093/mnras/stt2138)
Lara L., Cotton W. D., Feretti L., Giovannini G., Marcaide J. M., Márquez I.,
[Venturi T., 2001, A&A, 370, 409](http://dx.doi.org/10.1051/0004-6361:20010254)

[Leahy J. P., Williams A. G., 1984, MNRAS, 210, 929](http://dx.doi.org/10.1093/mnras/210.4.929)
[Lewis K. T., Eracleous M., 2006, ApJ, 642, 711](http://dx.doi.org/10.1086/501419)
[Lister M. L., et al., 2009, AJ, 138, 1874](http://dx.doi.org/10.1088/0004-6256/138/6/1874)

[Lister M. L., et al., 2013, AJ, 146, 120](http://dx.doi.org/10.1088/0004-6256/146/5/120)

[Liu Y., Jiang D. R., Gu M. F., 2006, ApJ, 637, 669](http://dx.doi.org/10.1086/498639)
Lu R. S., Shen Z. Q., Krichbaum T. P., Iguchi S., Lee S. S., Zensus J. A.,
[2012, A&A, 544, A89](http://dx.doi.org/10.1051/0004-6361/201218852)

Madrid J. P., Donzelli C. J., Rodríguez-Ardila A., Paggi A., Massaro F.,
[Schirmer M., 2018, ApJS, 238, 31](http://dx.doi.org/10.3847/1538-4365/aade8f)
[Mannheim K., Biermann P. L., 1989, A&A, 221, 211](http://adsabs.harvard.edu/abs/1989A%26A...221..211M)

[Marecki A., 2012, A&A, 544, L2](http://dx.doi.org/10.1051/0004-6361/201219638)

[Marin F., Antonucci R., 2016, ApJ, 830, 82](http://dx.doi.org/10.3847/0004-637X/830/2/82)
[Marshall H. L., et al., 2005, ApJS, 156, 13](http://dx.doi.org/10.1086/425578)
[Marshall H. L., et al., 2011, ApJS, 193, 15](http://dx.doi.org/10.1088/0067-0049/193/1/15)
[Marshall H. L., et al., 2018, ApJ, 856, 66](http://dx.doi.org/10.3847/1538-4357/aaaf66)
Massaro F., Harris D. E., Chiaberge M., Grandi P., Macchetto F. D., Baum
[S. A., O’Dea C. P., Capetti A., 2009, ApJ, 696, 980](http://dx.doi.org/10.1088/0004-637X/696/1/980)
[McKeough K., et al., 2016, ApJ, 833, 123](http://dx.doi.org/10.3847/1538-4357/833/1/123)


MNRAS **000**, 1–23 (2022)

16 _P. Breiding et al._


McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, Astronomical Society of the Pacific Conference Series Vol. 376, Astronomical Data Analysis Software and Systems
XVI. p. 127
[Meliani Z., Keppens R., Giacomazzo B., 2008, A&A, 491, 321](http://dx.doi.org/10.1051/0004-6361:20079185)
[Meyer E. T., Georganopoulos M., 2014, ApJ, 780, L27](http://dx.doi.org/10.1088/2041-8205/780/2/L27)
Meyer E. T., Fossati G., Georganopoulos M., Lister M. L., 2011, [ApJ,](http://dx.doi.org/10.1088/0004-637X/740/2/98) [740,](http://adsabs.harvard.edu/abs/2011ApJ...740...98M)

[98](http://adsabs.harvard.edu/abs/2011ApJ...740...98M)

Meyer E. T., Georganopoulos M., Sparks W. B., Godfrey L., Lovell J. E. J.,
[Perlman E., 2015, ApJ, 805, 154](http://dx.doi.org/10.1088/0004-637X/805/2/154)
[Meyer E. T., et al., 2016, ApJ, 818, 195](http://dx.doi.org/10.3847/0004-637X/818/2/195)
Meyer E. T., Breiding P., Georganopoulos M., Oteo I., Zwaan M. A., Laing
[R., Godfrey L., Ivison R. J., 2017, ApJ, 835, L35](http://dx.doi.org/10.3847/2041-8213/835/2/L35)
Meyer E. T., Petropoulou M., Georganopoulos M., Chiaberge M., Breiding
[P., Sparks W. B., 2018, ApJ, 860, 9](http://dx.doi.org/10.3847/1538-4357/aabf39)
Meyer E. T., Iyer A. R., Reddy K., Georganopoulos M., Breiding P., Keenan
[M., 2019, ApJ, 883, L2](http://dx.doi.org/10.3847/2041-8213/ab3db3)
[Miley G. K., Perola G. C., van der Kruit P. C., van der Laan H., 1972, Nature,](http://dx.doi.org/10.1038/237269a0)

[237, 269](https://ui.adsabs.harvard.edu/abs/1972Natur.237..269M)
[Miller B. P., Brandt W. N., 2009, ApJ, 695, 755](http://dx.doi.org/10.1088/0004-637X/695/1/755)
Miller B. P., Brandt W. N., Gallagher S. C., Laor A., Wills B. J., Garmire
[G. P., Schneider D. P., 2006, ApJ, 652, 163](http://dx.doi.org/10.1086/507509)
[Nakamura M., Li H., Li S., 2007, ApJ, 656, 721](http://dx.doi.org/10.1086/510361)
[O’Dea C. P., de Vries W., Biretta J. A., Baum S. A., 1999, AJ, 117, 1143](http://dx.doi.org/10.1086/300758)
[Owen F. N., Rudnick L., 1976, ApJ, 205, L1](http://dx.doi.org/10.1086/182077)
[Peng C. Y., Ho L. C., Impey C. D., Rix H.-W., 2010, AJ, 139, 2097](http://dx.doi.org/10.1088/0004-6256/139/6/2097)
[Perlman E. S., et al., 2011, ApJ, 739, 65](http://dx.doi.org/10.1088/0004-637X/739/2/65)
[Perucho M., Martí J. M., 2007, MNRAS, 382, 526](http://dx.doi.org/10.1111/j.1365-2966.2007.12454.x)
Perucho M., Martí J. M., Laing R. A., Hardee P. E., 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stu676) [441,](https://ui.adsabs.harvard.edu/abs/2014MNRAS.441.1488P)

[1488](https://ui.adsabs.harvard.edu/abs/2014MNRAS.441.1488P)

[Petropoulou M., Vasilopoulos G., Giannios D., 2017, MNRAS, 464, 2213](http://dx.doi.org/10.1093/mnras/stw2453)
[Piner B. G., Jones D. L., Wehrle A. E., 2001, AJ, 122, 2954](http://dx.doi.org/10.1086/323927)
[Piner B. G., et al., 2012, ApJ, 758, 84](http://dx.doi.org/10.1088/0004-637X/758/2/84)
[Planck Collaboration et al., 2016, A&A, 594, A13](http://dx.doi.org/10.1051/0004-6361/201525830)
[Pringle J. E., 1996, MNRAS, 281, 357](http://dx.doi.org/10.1093/mnras/281.1.357)
[Rau U., Cornwell T. J., 2011, A&A, 532, A71](http://dx.doi.org/10.1051/0004-6361/201117104)
[Reddy K., Georganopoulos M., Meyer E. T., 2021, ApJS, 253, 37](http://dx.doi.org/10.3847/1538-4365/abd8d7)
[Reddy K., Georganopoulos M., Meyer E. T., 2022, ApJS](http://dx.doi.org/in prep)
[Rossi P., Mignone A., Bodo G., Massaglia S., Ferrari A., 2008, A&A, 488,](http://dx.doi.org/10.1051/0004-6361:200809687)
[795](https://ui.adsabs.harvard.edu/abs/2008A&A...488..795R)

Roychowdhury A., Meyer E. T., Georganopoulos M., Breiding P., Petropoulou
[M., 2022, ApJ, 924, 57](http://dx.doi.org/10.3847/1538-4357/ac34f1)
[Sakelliou I., Merrifield M. R., 2000, MNRAS, 311, 649](http://dx.doi.org/10.1046/j.1365-8711.2000.03079.x)
Sambruna R. M., Maraschi L., Tavecchio F., Urry C. M., Cheung C. C.,
[Chartas G., Scarpa R., Gambill J. K., 2002, ApJ, 571, 206](http://dx.doi.org/10.1086/339859)
Sambruna R. M., Gliozzi M., Donato D., Tavecchio F., Cheung C. C.,
[Mushotzky R. F., 2004a, A&A, 414, 885](http://dx.doi.org/10.1051/0004-6361:20031657)
Sambruna R. M., Gambill J. K., Maraschi L., Tavecchio F., Cerutti R., Cheung
[C. C., Urry C. M., Chartas G., 2004b, ApJ, 608, 698](http://dx.doi.org/10.1086/383124)
Sambruna R. M., Gliozzi M., Donato D., Maraschi L., Tavecchio F., Cheung
[C. C., Urry C. M., Wardle J. F. C., 2006, ApJ, 641, 717](http://dx.doi.org/10.1086/500526)
Sambruna R. M., Donato D., Cheung C. C., Tavecchio F., Maraschi L., 2008,

[ApJ, 684, 862](http://dx.doi.org/10.1086/589918)
[Schlafly E. F., Finkbeiner D. P., 2011, ApJ, 737, 103](http://dx.doi.org/10.1088/0004-637X/737/2/103)
Schoenmakers A. P., de Bruyn A. G., Röttgering H. J. A., van der Laan H.,
[2001, A&A, 374, 861](http://dx.doi.org/10.1051/0004-6361:20010746)
[Schwartz D. A., 2002, ApJ, 569, L23](http://dx.doi.org/10.1086/340482)
[Schwartz D. A., et al., 2000, ApJ, 540, 69](http://dx.doi.org/10.1086/312875)
[Schwartz D. A., et al., 2006a, ApJ, 640, 592](http://dx.doi.org/10.1086/500102)
[Schwartz D. A., et al., 2006b, ApJ, 647, L107](http://dx.doi.org/10.1086/507529)
[Schwartz D. A., et al., 2020a, ApJ, 904, 57](http://dx.doi.org/10.3847/1538-4357/abbd99)
[Schwartz D. A., et al., 2020b, ApJ, 904, 57](http://dx.doi.org/10.3847/1538-4357/abbd99)
[Shen Y., et al., 2009, ApJ, 697, 1656](http://dx.doi.org/10.1088/0004-637X/697/2/1656)
Siemiginowska A., Bechtold J., Aldcroft T. L., Elvis M., Harris D. E., Do[brzycki A., 2002, ApJ, 570, 543](http://dx.doi.org/10.1086/339629)
[Siemiginowska A., et al., 2003a, ApJ, 595, 643](http://dx.doi.org/10.1086/377369)
Siemiginowska A., Smith R. K., Aldcroft T. L., Schwartz D. A., Paerels F.,
[Petric A. O., 2003b, ApJ, 598, L15](http://dx.doi.org/10.1086/380497)


MNRAS **000**, 1–23 (2022)



Siemiginowska A., Stawarz Ł., Cheung C. C., Harris D. E., Sikora M., Ald[croft T. L., Bechtold J., 2007, ApJ, 657, 145](http://dx.doi.org/10.1086/510898)
[Sol H., Pelletier G., Asseo E., 1989, MNRAS, 237, 411](http://dx.doi.org/10.1093/mnras/237.2.411)
[Sparks W. B., Biretta J. A., Macchetto F., 1994, ApJS, 90, 909](http://dx.doi.org/10.1086/191924)
[Spearman C., 1904, AJP, 15, 72](http://dx.doi.org/https://doi.org/1412159)
Stanley E. C., Kharb P., Lister M. L., Marshall H. L., O’Dea C., Baum S.,
[2015, ApJ, 807, 48](http://dx.doi.org/10.1088/0004-637X/807/1/48)
[Sudou H., Iguchi S., 2011, AJ, 142, 49](http://dx.doi.org/10.1088/0004-6256/142/2/49)
[Tavecchio F., 2021, MNRAS, 501, 6199](http://dx.doi.org/10.1093/mnras/staa4009)
[Tavecchio F., Maraschi L., Sambruna R. M., Urry C. M., 2000, ApJ, 544, L23](http://dx.doi.org/10.1086/317292)
Tavecchio F., Maraschi L., Wolter A., Cheung C. C., Sambruna R. M., Urry
[C. M., 2007a, ApJ, 662, 900](http://dx.doi.org/10.1086/518085)
Tavecchio F., Maraschi L., Wolter A., Cheung C. C., Sambruna R. M., Urry
[C. M., 2007b, ApJ, 662, 900](http://dx.doi.org/10.1086/518085)
[Tchekhovskoy A., Narayan R., McKinney J. C., 2010, ApJ, 711, 50](http://dx.doi.org/10.1088/0004-637X/711/1/50)
[Torres-Albà N., 2020, Nature Astronomy, 4, 448](http://dx.doi.org/10.1038/s41550-020-1096-1)
[Wang J.-M., Luo B., Ho L. C., 2004, ApJ, 615, L9](http://dx.doi.org/10.1086/426060)
Weisskopf M. C., et al., 2016, in den Herder J.-W. A., Takahashi T., Bautz M.,
eds, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series Vol. 9905, Space Telescopes and Instrumentation 2016:
[Ultraviolet to Gamma Ray. p. 990517, doi:10.1117/12.2235240](http://dx.doi.org/10.1117/12.2235240)
[Wilcox R., 2004, Journal of Applied Statistics, 31, 131](http://dx.doi.org/10.1080/0266476032000148821)
[Wilson A. S., Yang Y., 2002, ApJ, 568, 133](http://dx.doi.org/10.1086/338887)
[Wilson A. S., Young A. J., Shopbell P. L., 2001, ApJ, 547, 740](http://dx.doi.org/10.1086/318412)
[Woo J.-H., Urry C. M., 2002, ApJ, 579, 530](http://dx.doi.org/10.1086/342878)
[Worrall D. M., Birkinshaw M., Hardcastle M. J., 2001, MNRAS, 326, L7](http://dx.doi.org/10.1046/j.1365-8711.2001.04752.x)
Worrall D. M., Birkinshaw M., Marshall H. L., Schwartz D. A., Siemigi[nowska A., Wardle J. F. C., 2020a, MNRAS, 497, 988](http://dx.doi.org/10.1093/mnras/staa1975)
Worrall D. M., Birkinshaw M., Marshall H. L., Schwartz D. A., Siemigi[nowska A., Wardle J. F. C., 2020b, MNRAS, 497, 988](http://dx.doi.org/10.1093/mnras/staa1975)
[Wu X.-B., Liu F. K., Zhang T. Z., 2002, A&A, 389, 742](http://dx.doi.org/10.1051/0004-6361:20020577)
Xie G. Z., Liu H. T., Cha G. W., Zhou S. B., Ma L., Xie Z. H., Chen L. E.,

[2005, AJ, 130, 2506](http://dx.doi.org/10.1086/497163)

[Yuan W., Fabian A. C., Celotti A., Jonker P. G., 2003, MNRAS, 346, L7](http://dx.doi.org/10.1046/j.1365-2966.2003.07234.x)

[Zar J. H., 1972, JASA, 67, 578](http://dx.doi.org/https://doi.org/2284441)

[Zdziarski A. A., Bottcher M., 2015, MNRAS, 450, L21](http://dx.doi.org/10.1093/mnrasl/slv039)
[de Gasperin F., 2017, MNRAS, 467, 2234](http://dx.doi.org/10.1093/mnras/stx210)
[van den Bosch R. C. E., 2016, ApJ, 831, 134](http://dx.doi.org/10.3847/0004-637X/831/2/134)


**APPENDIX A:** **SPECTRAL MODELS**


**Synchrotron Fits**


The empirical synchrotron fits to the radio-to-optical data are
simple power laws with scaled exponential cutoffs, corresponding
to a simple power-law electron energy distribution with maximum
Lorentz factor. They have the following form:



�



� _𝛽_ [�]



_𝜈_
_𝜈_ f _𝜈_ = N � 10 [10] Hz



_𝛾_

exp
�



_𝜈_

−
� _𝜈_ 1



(A1)



In this equation _𝜈_ is the observed frequency of the radiation, _𝛾_ the
power-law index, _𝜈_ 1 the frequency at which the exponential turnover
begins, _𝛽_ the steepness of the cutoff, and N is the normalization of
the spectrum which has the units erg s [−][1] cm [−][2] .


**IC/CMB shifting equations**


The IC/CMB model we use has the following form for the shifting in luminosity and frequency of the lower-energy synchrotron
spectrum, as first described in Georganopoulos et al. (2006):


_𝜈_ c _𝜈_ CMB
= (A2)
_𝜈_ s e(B/ _𝛿_ )/[2 _𝜋_ m e c(1 + z)]

L c
= [32U] [CMB] [ (][1][ +][ z][)] [4] (A3)
L s 3(B/ _𝛿_ ) [2]


B is the magnetic field strength in the emission region, e is the
elementary charge, U CMB is the CMB energy density at the current
epoch, _𝜈_ CMB the CMB peak frequency at the current epoch, z is the
redshift, m e is the electron mass, c is the speed of light, and _𝛿_ is
the Doppler factor. Note the only free parameter in this shift is _𝐵_ / _𝛿_
which becomes fixed upon fitting the X-ray component of the SED.
If one assumes an equipartition magnetic field, this shift is only
parametrized by _𝛿_ . Also note that these shifts should preserve the
same spectral index for both the synchrotron and inverse-Compton
components, assuming the extrapolation of the radio spectral index
from the observed GHz frequencies to the unobserved hundreds of
MHz range.


**A1** **Robustness of Recombined Light Curve Constraints**


Our methodology for recombining _Fermi_ /LAT light curves in order to obtain the deepest constraints on the IC/CMB flux is based
on determining the source detection significance, parametrized by
the TS, in each light curve time bin and contiguously recombining
the lowest significance bins until reaching flux density/upper limit
minima. In this scheme, these minima correspond to the most core
quiescent time we can use in order to obtain our deepest IC/CMB
constraints. This methodology relies on the assumption that our light
curves consist of a superposition of a bright, and intrisically variable,
core component with a weaker and completely steady IC/CMB component. In this setup, the source detection significance is dominated
by the core component. This allows us to use the “core quiescent”
states when the source TS is lowest to obtain the deepest constraints
on the steady IC/CMB component. If the source consisted of only a
completely steady flux component, this method of TS ordering and
recombining only the lowest significance bins would lead to a biased
estimate of the flux, or upper limits in the case of non-detections,
since one would essentially only be using the low Poisson count
deviates from random measurement error.

Cursory inspection of our light curves given as online-only figures will show that they are dominated by intrinsically variabile flux
likely produced by the jet cores, with complex stochastic and correlated variability patterns, flaring periods, etc. The variability indexes
published by the _Fermi_ team further confirm the intrinsically variable nature of the flux output from our sources (Abdollahi et al.
2020). However, in order to demonstrate that measurement bias does
not significantly affect our results, we perform a simulation using
the `gtobssim` tool within the _Fermi_ science tools software package.
This tool can simulate _Fermi_ /LAT events data for an assumed set of

source model parameters, sky observing position, acceptance cone
for your region of interest, and spacecraft pointing history.
For our light curve model, we simulate a steady flux component
corresponding to IC/CMB, a variable component corresponding to
the core, and an isotropic extragalactic background using the most
recent template file, `iso_P8R3_SOURCE_V3_v1.txt` . For our core
and IC/CMB spectra we use a power-law model with photon index
fixed at 2 (horizontal in _𝜈_ F _𝜈_ ) for simplicity and ease of interpretation. We base our simulation on the results for our _Fermi_ analysis
of PKS 1150+497, using a putative source at the same sky position.
Thus, we use an isotropic background model with normalization fixed
in all time bins by that found in the whole time range analysis for
PKS 1150+497. We use the actual spacecraft pointing history for our
light curve time range. We simulate core flux levels corresponding to



_Testing IC/CMB in Resolved Quasar X-ray Jets_ 17


the observed light curve fluxes for PKS 1150+497 shown in Figure 1.
For time bins in which we report source non-detections in Figure 1,
we simulate a flux level corresponding to the flux upper limit subtracted by 0.75 dex. These core states are fairly representative of
many of our light curves, and represent a bright quasar core with intrinsic stochastic and complex variability patterns, with enough core
quiescent states to provide meaningful constraints on any weak and
steady flux component. Our simulated, steady, IC/CMB flux level is
indicated by the horizontal red dashed line in Figure A1. The steady
flux level simulated for our IC/CMB component corresponds to a
level ∼1 dex below the mean flux simulated of the core quiescent
states (here we take those time bins with source non-detections in the
original PKS 1150+497 light curve as the “core quiescent states”) .
The IC/CMB simulated flux level is ∼ three standard deviations below the combined fluctuations of the intrinsic variability of the core
quiescent states and Poisson random-error variation from a steady
source with similar mean flux (with the latter being obtained from a
separate simulation and both being ∼0.2 dex). Thus, this still allows
for time-bin-ordering by TS to be dominated by intrinsic core flux
variability, even among the core quiescent states.
The results from our light curve simulation shown in Figure A1
clearly show that, in general, the combined bin flux density/upper
limit minima do not violate the steady state IC/CMB flux simulation
level. The upper limits from band 3 (3−10 GeV) are the only ones
which just reach the simulation level, but this is consistent with
statistical fluctuations from a 95% upper limit and this does not
indicate appreciable bias from our approach.


**A2** **Notes on Individual Sources**


Next we discuss some notes on individual sources in order to highlight any features of their X-ray/radio jet morphologies, peculiararities associated with their SEDs, or other interesting source properties.
We also note the original discovery papers for each X-ray jet, any
literature sources we used for constructing our SEDs, and any SED
data resulting from our own analysis.


**J0038** − **0207** **(3C** **17):** This jet is highly curved, showing a
greater than 90 [◦] position angle change roughly two-thirds into its
(projected) length, and commensurate with the “bent-tail” class of
radio galaxies. A recent study by Madrid et al. (2018) shows this
jet bend likely originates from the jet moving through the dense
intracluster medium in which it resides, where this is a common explanation for the origin of this type of jet distortion (e.g. Miley et al.
1972; Jones & Owen 1979; Jones et al. 2017). The X-ray emission
corresponds to two knots with associated radio and optical/IR emission. One of the X-ray knots appears in the jet bend, while the other
X-ray knot is a few arcseconds downstream of the core before the
abrupt position angle change. We use the radio-to-X-ray flux densities presented in the X-ray jet discovery paper (Massaro et al. 2009) in
order to construct our SED, where we add together the flux densities
for both of the observed X-ray knots. The radio and X-ray spectral
indexes are similar in value, which is consistent with the IC/CMB
model. However, the IC/CMB model is ruled out at a fairly high level
of significance by our _Fermi_ limits, where the highest-energy _Fermi_
limit is closest in frequency to a region of the IC/CMB spectrum
anchored by an observed portion of the synchrotron spectrum (these
portions of the IC/CMB spectra correspond to where observed synchrotron flux densities would lie on the shifted IC/CMB spectra − as
marked by the gray circles in our SEDs).

**J0108+0135** **(PKS** **B0106+013):** This jet shows semicontinuous X-ray emission along the length of the radio emission,


MNRAS **000**, 1–23 (2022)

18 _P. Breiding et al._


**Figure** **A1.** Top: Simulated _Fermi_ /LAT light curve with corresponding TS
values for each bin shown in the lower panel. The time bins correspond
to three weeks in good time interval, and the flux from the source is the

−
integrated photon flux from 100 MeV 100 GeV. The blue arrows in the light
curve represent upper limits for bins in which the source TS was less than
ten. Black data points represent fluxes measured when the TS was greater
than ten, with 1 _𝜎_ error bars. In the TS plot, blue arrows represent TS values
less than zero, while the black points represent positive TS values. The red
horizontal dashed line corresponds to the simualted steady IC/CMB flux
level. Bottom: Combined-bin flux density upper limits for the simulated light
curve are shown as lines without error bars, where upper limits are measured
when the source TS was less than 10. Flux densities are shown with gray 1 _𝜎_
error bars on top of the lines when the source TS was greater than ten. The
flux densities/upper limits are given in the five Fermi energy bands described
in section 2.6. The horizontal black lines corresponds to the simulated flux
density level for the steady IC/CMB component (the red dashed line from the
top panel).


with the bright X-ray knot B midway along its several arcsecond-long
jet. The jet morphology at both X-ray and radio wavelegnths also appears consistent with a very slight helical or S/Z shape (this S/Z
shape is much more pronounced in several other of the jets presented
in this study). S/Z-shaped helical kpc-scale jets can originate from a
number of processes, including: jet precession induced by a binary
supermassive black hole (SMBH) (Begelman et al. 1980) or warped
accretion disk (Pringle 1996), various magnetohydronamic (MHD)


MNRAS **000**, 1–23 (2022)



instabilities (e.g. Nakamura et al. 2007), or backflowing lobe plasma
(Leahy & Williams 1984). The X-ray jet discovery was presented by
Hogan et al. (2011), but we utilize the X-ray spectral index and flux
density measurement presented by Kharb et al. (2012) in our SED.
Kharb et al. (2012) also note that the radio jet appears to end in a “nose
cone” structure, believed to originate from magnetically confined jets
where the plasma collects between the Mach disk and leading bow
shock at the end of the jet instead of forming a reverse-shock (Clarke
et al. 1986). Additionally, it is suggested S/Z-shaped jet morphologies may be easier to accomodate in magnetically-dominated jets as
they are easier to deflect (e.g. Benford 1978). Our SED also makes
use of archival VLA data which we imaged at L,C, and X bands,
where the radio spectral index is consistent with the X-ray spectral
index. However, even after adding flux densities for all jet regions
(minus the hot spot) together, the IC/CMB model is still not ruled
out by the quiescent-state _Fermi_ flux densities (or upper limit in the
case of the lowest energy band).

**J0209+3547 (4C 35.03):** The radio jet for this source clearly has
a FR I morphology, where the X-ray emission is associated with the
brighter inner region in the first few arcseconds downstream from the
core. The X-ray jet discovery was presented in Worrall et al. (2001),
where we used their measured X-ray flux density combined with
radio flux densities resulting from our own multi-band VLA imaging
in our SED. This is one jet where the MSC-nature of the SED can
be debated, and a single synchrotron power-law model could still
be conceivably connected from radio to X-ray wavelengths without
violating any of the measurement errors. Thus, deep sub-mm-tooptical imaging is essential in order to confirm (or rule out) the MSC
nature of this jet.

**J0210** − **5101 (PKS 0208** − **512):** Marshall et al. (2005) present
the discovery of this X-ray jet,where we use the radio-to-X-ray flux
densities presented in Perlman et al. (2011) for our SED. The X-ray
spectral index for the jet appears harder than the radio spectral index.
Accordingly, the synchrotron and IC/CMB model fits just barely
respect the associated errors. We analyzed archival ALMA band 3
and 7 data, but could not detect the jet and thus give 95% upper
limits in our SED. However, deeper sub-mm imaging with ALMA
would be critical in order to establish the shape of the synchrotron
spectrum between the measured radio flux densities and the NIR _HST_
jet detection. Depending on the outcome of these observations, it is
possible the IC/CMB model would remain ruled out in the event of a
bright ALMA detection, or potentially lead to a SED which is broadly
consistent with the IC/CMB model in the event of a non-detection or

faint detection.


**J0237+2848 (4C 28.07):** The X-ray jet discovery is reported in
Marshall et al. (2011), where we use archival VLA and _HST_ data
we reduced in our composite SED. The radio spectral index for this
source is very hard, leading to a very high level of predicted IC/CMB
gamma-ray flux not observed by _Fermi_ .

**J0416** − **2056** **(PKS** **0413** − **210):** This jet exhibits a C-shaped
morphology indicative of the “wide-angle tailed” class of radio
galaxies (Owen & Rudnick 1976), where this shape may result from
ram pressure experienced by the jet moving through the intergalactic/intracluster medium (similar to the bent-tail class), and potentially
originating from cluster mergers (Sakelliou & Merrifield 2000). The
X-ray jet discovery was reported by Marshall et al. (2005), where we
use the X-ray flux density from Marshall et al. (2011) in our SED
(and our own radio imaging).

**J0418+3801** **(3C** **111):** This well-collimated quasar X-ray jet
was first reported in Hogan et al. (2011), but we used the optical and
X-ray flux densities presented in Clautice et al. (2016) for our SED.
The radio flux densities in our SED came from our own analysis. This

jet is one case where the X-ray spectrum is very soft, and at odds with
the steeply rising radio spectral index. This is suggestive that the Xrays and GHz radio emission do not originate from the same electron
population as is required by the IC/CMB model. Additionally, as is
apparent from our radio/X-ray imaging, the radio and X-ray knots
are not cospatial in this jet as would be expected under the IC/CMB
model, but rather the X-ray knots peak upstream from the radio knots
(i.e., closer to the black hole). A careful analysis of the radio/X-ray
morphology of this jet is given in Clautice et al. (2016).

**J0433+0521** **(3C** **120):** This quasar was not a member of the
_Fermi_ /LAT 3FGL 4-year point source catalog, but subsequently became detected and is a member of the _Fermi_ /LAT 4FGL 8-year point
source catalog. The X-ray jet discovery paper is Harris et al. (1999),
where we used the optical upper limits from this paper in our SED.
We also use the radio flux densities and the X-ray flux density/index
from Harris et al. (2004) in our SED. Knot k25 is the only X-ray knot
which precludes a single synchrotron spectrum from radio-to-X-ray
wavelengths.

**J0519** − **4546** **(Pictor** **A):** This is another highly collimated
quasar jet, where the X-ray jet discovery was reported in Wilson
et al. (2001). The X-ray jet appears very knotty, and the radio jet is
accompanied by expansive radio lobes which surround the source.
The optical jet detection was reported in Gentry et al. (2015). We
use the flux densities/upper limits and X-ray spectral index from
Gentry et al. (2015) for our SED. Follow-up deep _Chandra_ observations were presented in Hardcastle et al. (2016), where they report
the detection of jet knot flux variability and a faint X-ray counter-jet
which are both at odds with the IC/CMB model (due to the fact that
IC/CMB X-rays are expected to be non-variable and highly beamed).
Our SED assumes the optical emission is the high-energy portion of a
single radio-to-optical synchrotron spectrum. It is conceiveable that
IC/CMB could be rescued by instead having the optical flux density
correspond to the low-energy extrapolation of the IC/CMB spectrum
and appopriately softening the radio spectral index. However, this
would imply an extremely soft radio spectrum which could be easily
tested with high-frequency radio observations using either ATCA or
ALMA.


**J0607** − **0834** **(PKS** **0605** − **085):** The X-ray jet discovery was
reported in Sambruna et al. (2004b), where we used their X-ray flux
density and optical upper limit in our SED. We use our own _Chandra_
analysis for the X-ray spectral index. Additionally, we used our own
VLA and ALMA band 3 data reduction for the SED, where the
synchrotron spectrum appears to be turning over around the ALMA
band 3 data point. This turnover could be confirmed with another
higher-frequency ALMA observation.

**J0728+6748** **(3C** **179):** This is a knotty jet, where the X-ray
detection was first reported in Sambruna et al. (2004b). We use
our own archival VLA C and X-band imaging in our SED, and the
X-ray/optical flux densities reported by Sambruna et al. (2004b).
However, a X-ray spectral index could not be determined for the jet
features analyzed, and the radio spectral index is poorly constrained
by the two close-in-frequency radio flux densities. Thus, this very
northern source would make a good target for high-frequency VLA
observations (i.e., K-band or above) or Submillimeter Array (SMA)
observations. Additionally, deeper _Chandra_ observations may provide enough photon counts to contrain the X-ray spectral index for
these emission components.

**J0741+3112** **(B2** **0738+31):** The X-ray jet discovery was reported in Siemiginowska et al. (2003a). The bright X-ray knot A
appears part-way along this jet and we use our own VLA images for
the L/C-band flux density points in our SED. The X-ray flux density
and index used in the SED comes from Sambruna et al. (2004b).



_Testing IC/CMB in Resolved Quasar X-ray Jets_ 19


This jet is interesting because it is not necessarily a MSC jet; deep
ALMA and _HST/JWST_ imaging could help establish the shape of the
radio-to-optical synchrotron spectrum in order to confirm (or rule
out) the MSC nature of this jet, and provide a more stringent test of
the IC/CMB model utilizing our _Fermi_ limits.

**J0830+2410** **(B2** **0827+24):** This is another bent-jet source,
where the radio emission appears to be stronger downstream from
the jet bend, and the X-ray emission peaks upstream from the bend.
The X-ray jet discovery was reported in Jorstad & Marscher (2004).

**J0840+1312 (4C 13.38):** The X-ray jet discovery was reported
in Sambruna et al. (2004b), where use knot A for the SED since
this knot has an associated optical detection. The X-ray spectral
index appears significantly harder than the radio spectral index for
this source, where our radio spectrum is very well-constrained by
our own multi-band VLA and ALMA imaging (we use the C-band
flux density from Sambruna et al. (2004b)). The optical/X-ray flux
densities and X-ray spectral index are taken from Sambruna et al.
(2004b).

**J0922** − **3959** **(PKS** **0920** − **397):** The X-ray jet discovery is reported in Marshall et al. (2005), where we use the X-ray flux density
from Schwartz et al. (2006a) and our own _Chandra_ analysis for
the X-ray spectral index measurement. We also use our own ATCA
and ALMA data reduction in order to fill out the radio synchrotron
spectrum. This is one case where we used our own archival _HST_
analysis and were able to detect the entire optical jet. The SED is
constructed using all of the emission components in the jet without
including the hot spot. One obvious feature of this jet’s morphology
is its quasi-periodic “cannonball” knots, where one interpretation for
this morphology is that it results from the periodic modulation of the
accretion rate due to the dynamics of a binary SMBH (i.e. Godfrey
et al. 2012b).

**J0947+0725 (3C 227):** This X-ray jet was first reported in Hardcastle et al. (2007), where only one X-ray feature was reported as
potentially corresponding to a jet knot versus just a hot spot: P4.
Thus, our SED analyzes this feature, but our _Fermi_ limits are not
constraining enough to rule out the IC/CMB model. We use the Xband flux density from Hardcastle et al. (2007) combined with our
own measured L/C-band flux densities in our SED.

**J1001+5553 (QSO 0957+561):** This quasar system is gravitationally lensed, where the lensing results in a double image of the
quasar. The lensing and X-ray jet discovery are presented in Chartas
et al. (2002), where we also use the X-ray spectral index and flux
density from this paper in our SED. We use our own data reduction
for the radio flux densities. This is a case where the jet X-ray spectral
index is significantly softer than the radio spectral index. However,
in this case the X-ray index is measured for the entire jet while our
SED is constructed just for knot B. Therefore, it is possible the Xspectrum of just knot B is more in line with the IC/CMB model.
Higher-frequnecy radio observations are critical for this jet in order
to appropriately test the IC/CMB model.

**J1007+1248** **(4C** **13.41):** This X-ray jet was first reported in
Miller et al. (2006), where they also discuss the observed broad
absoption lines in the optical/UV spectra originating from a fast
gaseous outflow in this system (and indicative of jet-driven feedback
with its host galaxy). The radio jet hosted by this quasar is enormous
in size, falling just shy of the 0.7 Mpc cutoff for the “giant radio
galaxy” class (e.g. Lara et al. 2001; Schoenmakers et al. 2001),
coming in at ∼0.57 Mpc in linear projected size. The twin radio
jets hosted by 4C +13.41 have a hybrid morphology (Gopal-Krishna
& Wiita 2000), where the southeastern component has a FR I-type
plumey jet, and the northwestern jet exhibits conventional edgebrightened FR II-type features. Interestingly, the anomalousl X-ray


MNRAS **000**, 1–23 (2022)

20 _P. Breiding et al._


**Figure A2.** Here we present the VLA X-band (8.46 GHz) image for 4C 13.41
(with RA/DEC given in the FK4/B1950 coordinate system), showing the
serendipitous radio source discovered at the edge of our field in the bottom
right corner of the image. The serendipitously discovered source appears
consistent with a conventional FR II radio galaxy viewed with its jets oriented
perpendicular to the line of sight and inflating diffuse lobes on either side of
the black hole. The radio contours start at a base level of 3 _𝜎_, and increase
by factors of two thereafter. The image intensity color map ranges from 0 to
5.6 mJy beam [−][1] . The synthesized beam is shown in the bottom left as a solid
gray ellipse with a cross.


emission in this MSC jet is from the FR I side and not the FR II
side, where anomalous X-ray emission is usually observed in FR II
and not FR I jets. The origin of hybrid morphology radio galaxies is
widely debated, with possible explanations including an assymetric
environment surrounding the AGN (i.e., the FR I jet was FR II-type jet
disrupted by propagating into a relatively dense IGM) (Meliani et al.
2008), projection/Doppler-boosting effects leading to the illusion of
hybrid morphology (de Gasperin 2017), or an illusion caused by a
combination of light-travel time effects and retriggered AGN activity
(e.g., Marecki 2012).
We use our own C/X-band VLA imaging for the SED (in addition to
ALMA upper limits based upon non-detections), combined with the
X-ray index and flux density presented in the discovery paper. For this
jet, higher-frequency and deep VLA or ALMA imaging is essential
to better constrain the radio-to-optical synchrotron spectrum. In our
deep X-band radio photometry we also serendipitously detected an
unknown radio source which we could not find a match for in existing
AGN and galaxy catalogs. We present the X-band image showing this
radio source in Figure A2. This very nearby radio galaxy is suggestive
that the two systems may reside in a dense galaxy cluster, where radioloud AGN are generally found to have a preference for residing in
cluster envrionments (e.g., Shen et al. 2009). This picture supports
the scenario that frequent galaxy mergers might be necessary to help
ignite radio-jet activity in AGN (e.g, Chiaberge et al. 2015).

**J1033** − **3601 (PKS 1030** − **357):** The X-ray jet discovery for this
quasar was first presented in Marshall et al. (2005), where we use
the measurements presented in Schwartz et al. (2006a) for the X-ray
flux density and optical upper limit. The radio flux densities and
X-ray spectral index come from our own analysis. This is one case
where deep ALMA imaging would help establish the shape of the
radio-to-optical synchrotron spectrum for our _Fermi_ test.

**J1048** − **1909** **(PKS** **1045** − **188):** This jet is an example of a
slightly bent jet, where the X-ray detection was first reported by
Hogan et al. (2011). We use the X-ray flux density/spectral index
presented in Stanley et al. (2015) for our SED, where the radio-tooptical flux densities result from our own archival data analysis.


MNRAS **000**, 1–23 (2022)



**J1048** − **4114 (PKS 1046** − **409):** This X-ray jet was first reported
in Marshall et al. (2005). This jet shows a strong bend, with a majority
of the X-ray flux emanating from the jet upstream to this bend and
downstream of the core. There is also a very bright feature northwest
of the core which is itself associated with a lobe-type structure. This
feature has a two-point 8.64 GHz−19 GHz spectral index of _𝛼_ ∼ 0 _._ 6,
which is more consistent with a jet knot than a core. For this reason we
don’t believe it is a dual AGN, or an unrelated background/foreground
AGN. We use the X-ray flux density given in Marshall et al. (2005) for
our SED, but our own imaging for the radio flux densities. However,
this SED is poorly constrained; deep _Chandra_ observations would
be beneficial to nail down the X-ray spectral index along with radio
follow-up to better constrain the radio spectral index and shape of
radio-to-optical synchrotron spectrum. In this vain, deep optical/IR
imaging with the _HST/JWST_ would help anchor the radio-to-optical
synchrotron spectrum.

**J1058+1951** **(4C** **20.24):** The discovery of this X-ray jet was
first presented in Schwartz et al. (2006b), where we use the X-ray
spectral index and flux density in this paper for our SED. We use
our own L/C/X-band VLA and ALMA band 3/6 imaging to fill out
the radio synchrotron spectrum, which is very well constrained. The
X-ray spectrum is very soft, and highly discrepent with the radio
spectral index. Interestingly, the X-ray emission is very continuous
and not knotty like some of the other X-ray jets presented in this
study. A very slight jet bend is apparent in this source.

**J1130** − **1449 (PKS 1127** − **145):** The X-ray jet discovery for this
source was first reported in Siemiginowska et al. (2002). We use the
X-ray flux density/spectral index presented in Siemiginowska et al.
(2007) in our SED. Our radio flux densities come from our own
analysis. This is a case where a single synchrotron spectrum can
not be definiteively ruled out from radio-to-X-ray frequencies. Thus,
deep ALMA and/or _HST/JWST_ imaging could help to confirm (or
refute) the MSC nature of this jet and also better-constrain the shape
of the radio-to-optical synchrotron spectrum.

**J1153+4931 (PKS 1150+497):** This X-ray jet was first reported
in Sambruna et al. (2002), where we use the radio-to-X-ray flux
densities and X-ray spectral index presented in Sambruna et al. (2006)
for our SED. This jet is another case of a helical jet with quasiperiodic cannonball knot structure − both potential indicators of a
binary SMBH system. We show the SED for the brightest X-ray knot
(knot B), where we rule out the IC/CMB model at a high level of
significance and the radio-to-optical synchrotron spectrum is verywell constrined.


**J1205** − **2634 (PKS 1202** − **262):** This is another case of a curved
jet, where the X-ray jet discovery is reported by Marshall et al. (2005)
and we use the X-ray flux density and _HST_ upper limits reported in
Perlman et al. (2011) for our SED. We use our own analysis for
the X-ray spectral index measurement. The X-ray emission in this
case seems to be continuous along the length of the jet. We use our
own radio imaging for the radio flux densities, where there is an
apparent synchrotron spectral turnover by the ALMA band 3 and 6
data points. Additionally, there is a definite tension between the radio
spectral index and X-ray spectral index, with the X-ray spectral index
being softer than the radio.

**J1224+2122** **(4C** **21.35):** This X-ray jet was first reported by
Jorstad & Marscher (2006), where we use their X-ray flux density
in our SED. This jet is a clear example of a S/Z-shaped jet, with
quasi-periodic knot structure suggestive of a binary SMBH. The first
two jet knots have associated X-ray emission (where we combine
the flux densities of these knots for our SED), while the rest of
the jet appears undetected in X-rays. We have an extensive amount
of radio imaging we used to fill out the radio-to-optical synchrotron

spectrum. However, this is still a source where even higher-frequency
(i.e., greater than ALMA band 6) ALMA imaging would be helpful
to determine if IC/CMB is ruled out or if it is consistent with the

broadband SED. We show an ALMA band 3 in-band spectral index
which appears consistent with the broadband radio spectral index,
and predicts a rising flux density for future high-frequency ALMA
observations. Another way to anchor the radio-to-optical synchrotron
spectrum would be to pursue deep _HST/JWST_ imaging in the hopes
of an optical jet detection.

**J1319+5148 (4C 52.27):** The X-ray jet discovery was reported
in Jorstad & Marscher (2006), where we use their measured X-ray
flux density in our SED. The radio jet has a knotty morphology
and appears to end in a nose-cone structure. Interestingly, the Xray emission in this jet originates from the knot (knot E) upstrem
of the nose cone, consistent with the idea that high-energy particle acceleration is not occuring in the nose cone due to a lack of
shocks in this region. We used our own C/Ku-band VLA imaging for
our SED, but higher-frequency radio observations and _HST/JWST_
observations are essential to better-test the IC/CMB model in this

source. Furthermore, this jet is another case where the MSC nature
has not been definitively established; deep SMA and/or _HST/JWST_
observations could help in this regard.

**J1325+6515 (4C 65.15):** The X-ray jet discovery for this quasar
was reported in Miller & Brandt (2009), where we use the X-ray flux
density/index and _HST_ upper limit presented in this paper for our
SED. Our VLA L/X/Ku-band imaging appears to just detect the syncrhotron spectrum as it starts to turn over. Thus, low frequency (i.e.,
lower than L-band) VLA observations, high-frequency observations
with the SMA, and deep _HST/JWST_ imaging would be beneficial to
better characterize the radio-to-optical synchrotron spectrum. This
radio jet is classified as a hybrid morphology jet, with one side
displaying a FR I morphology and the other a FR II morphology.
Interestingly, the anomalous X-ray emission for this jet appears spatially cocincident with the (drastic) jet bend in this source, and like
4C 13.41 occurrs on the FR I jet side.

**J1421** − **0643** **(PKS** **1418** − **064):** This X-ray jet is hosted by a
very high redshift quasar (z = 3.7), and its discovery was reported
in McKeough et al. (2016). We use the X-ray flux density/spectral
index and _HST_ upper limits presented in Worrall et al. (2020b) for
our SED. We use our own VLA L/C-band images for the radio flux
densities presented (along with upperlimits from twoarchival ALMA
non-detections). Deeper ALMA and _HST/JWST_ observations are
essential for establishing the MSC nature of this jet and the shape of
the radio-to-optical synchrotron spectrum for our _Fermi_ test. This Xray jet is an especially important test for the IC/CMB model owing to
its extremely high redshift, and the fact that the IC/CMB mechanism
is supposed to be much more efficient with increasing redshift due
to (1 + z) [4] dependance of the CMB energy density on redshift (e.g.,
Schwartz 2002; Marshall et al. 2018).

**J1510+5702** **(QSO** **B1508+572):** This is the highest-redshift
quasar in our sample (z = 4.3), and the discovery of its X-ray jet was
reported by Yuan et al. (2003) and Siemiginowska et al. (2003b).
We use the L-band radio flux density reported by Cheung (2004)
combined with a Ku-band flux density resulting from our own VLA
analysis (including a core subtraction) in order to constrain the radio
synchrotron spectrum. We also use the _HST_ upper limit and X-ray
flux density/spectral index presented in Yuan et al. (2003) in our
SED. Significantly, the IC/CMB model is ruled out in this very high
redshift X-ray jet where one would expect the IC/CMB mechanism to
be much more efficient. This quasar is also another source which was
not detected in the _Fermi_ /LAT 3FGL 4-year point source catalog, but
became a detection in the 4FGL 8-year point source catalog.



_Testing IC/CMB in Resolved Quasar X-ray Jets_ 21


**J1632+8232** **(NGC** **6251):** This X-ray jet discovery was reported by Sambruna et al. (2004a) and Evans et al. (2005), and the
jet is hosted by a very nearby massive elliptical galaxy. The discovery papers also note a detection of a diffuse X-ray-emitting gaseous
halo (of unknown origin) and cavities excavated in said halo by
the radio-luminous jet, indicative of jet-mode feedback operating in
this system (on the scale of the cluster). The X-ray emission associated with the outer jet region in this source is anomalous, and is
the region for which we constructed a SED. We use the X-ray flux
density/spectral index from Evans et al. (2005) in our SED, along
with our own X/L-band VLA imaging. Critically, deep SMA and/or
_HST/JWST_ imaging would help to establish the shape of the radioto-optical synchrotron spectrum in this jet for a more suitable test of
the IC/CMB model with _Fermi_ .


**J1642+3948 (3C 345):** This X-ray jet discovery was reported by
Sambruna et al. (2004b), where we use the X-ray flux density/spectral
index and _HST_ upper limit from Kharb et al. (2012) in our SED.
We use our own analysis for the radio flux densities. Deep ALMA
observations could help determine the shape of the radio-to-optical
synchrotron spectrum for best-applying our _Fermi_ test.

**J1642+6856** **(4C** **69.21):** This X-ray jet was first published in
Sambruna et al. (2004b), where we used their measured X-ray/optical
flux densities in our SED. We used our own _Chandra_ analysis to
determine the X-ray spectral index for the jet, and used our own
VLA C/X/Ku-band imaging for the radio flux densities. We combine
the flux densities from all of the jet knots together for our SED, but
the brightest X-ray knot is roughly two-thirds down the length of the
slightly curved radio jet (knot C).

**J1720** − **0058** **(3C** **353):** The discovery of this X-ray jet was
reported in Kataoka et al. (2008), where we use their X-ray flux
density/X-ray spectral index in our SED. We also use the three lowestfrequency radio flux densities from Kataoka et al. (2008) combined
with our own analysis of X and K-band VLA data for the two highestfrequency radio points. Our SED focuses on the brightest X-ray knot
in the jet, and this SED is a clear example where the radio spectral
index is significantly harder than the X-ray spectral index. As noted
in the discovery paper, this source also has a X-ray counter jet,
inconsistent with a highly aligned jet as is required under the IC/CMB
model (where we would not expect to detect a counter jet due to the
X-rays being relativstically beamed out of our line of sight).

**J1746+6226 (4C 62.29):** This is another case of a high-redshift
quasar (z = 3.9). The radio jet morphology resembles the knotty
quasi-periodic cannonball jets, with a nose-cone-like jet termination.
The X-ray emission appears continuous along the length of the jet,
ending just before the jet termination feature. The X-ray jet discovery
was first reported in Cheung et al. (2006), where we use their X-ray
spectral index/flux density and _HST_ upper limit in our SED. We use
our own VLA imaging for the SED, including an in-band spectral
index bowtie on top of the Ku band flux density. It appears our VLA
flux densities are probing the synchrtron spectrum just at its turnover
for this source. It seems unlikely future _Fermi_ observations will be
able to rule out the IC/CMB model in this jet.

**J1829+4844 (3C 380):** This jet is only ∼10 kpc in linear (projected) extent, where the X-ray and radio emission seem roughly
coincident along the length of this small jet. The X-ray jet discovery
was reported in Marshall et al. (2005), where we use the X-ray flux
density from this paper combined with the radio/optical flux densities presented in O’Dea et al. (1999). The IC/CMB model is only
marginally ruled out in this jet from our highest energy _Fermi_ limit,
but future _Fermi_ observations may be able to increase the significance
of this gamma-ray non-detection.

**J1849+6705** **(8C** **1849+670):** The X-ray jet discovery for this


MNRAS **000**, 1–23 (2022)

22 _P. Breiding et al._


source is reported by Hogan et al. (2011), but we used the X-ray
flux density/spectral index and _HST_ upper limits from Stanley et al.
(2015) in our SED. We used our own VLA L/X-band data reduction
for the radio flux densities. This appears to be another S/Z-shaped
jet, where the X-ray emission is associated with the inner jet before it
starts to bend. Sub-mm imaging with the SMA could help determine
the synchrotron spectrum at a frequency which would better test the
IC/CMB model with our _Fermi_ analysis.

**J1927+7358 (4C 73.18):** The X-ray jet discovery was reported
in Sambruna et al. (2004b), where we use their _HST_ flux density in
our SED. We use our own radio/X-ray analyses for our other flux
densities and X-ray spectral index measurement. The X-ray emission
is associated with the first inner knot (knot A). This is also another
example of a bent-tail radio galaxy. The X-ray emission is very
soft, but not inconsistent with the measured radio flux densities.
The X-ray emission is only marginally anomalous, where the optical
emission appears likely to belong to the same spectral component
as the X-rays. A single synchrotron model from radio to X-rays
might be able to fit the data, all be it at a slight tension with the
measurement uncertainties. Deep SMA imaging would help give us
a better understanding of the radio-to-optical synchrotron spectrum
in this jet.

**J2005+7752** **(S5** **2007+777):** This is a very knotty and hard,
resolved X-ray jet hosted by a BL Lac object − first published in
Sambruna et al. (2008). We use all of the flux densities, _HST_ flux
density upper limits, and the X-ray spectral index presented in Sambruna et al. (2008) for our SED. As is apparent from the SED,
higher-frequency radio observations would be helpful in establishing the shape of the radio-to-optical synchrotron spectrum (where
the highest-frequency point in our SED is at 4.86 GHz). This jet is
another case of a hybrid morphology jet, with the X-ray emission
corresponding to the FR I side.

**J2105** − **4848 (PKS 2101** − **490):** This X-ray jet was first reported
in Marshall et al. (2005), where we use the multi-wavelength flux
densities and X-ray spectral index presented in Godfrey et al. (2012a)
for our SED. We also analyzed ALMA band 3 and 6 data for our SED,
where these flux densities suggest we may be seeing a radio spectral
turnover around ALMA band 3. The radio morphology for this jet is
very knotty, and displays a slight curve.

**J2158** − **1501** **(PKS** **2155** − **152):** The X-ray jet discovery was
reported in Hogan et al. (2011), where we used the X-ray flux density
from this paper in our SED. We used our own _Chandra_ analysis for
the X-ray spectral index, and our own radio/optical analysis for the
radio flux densities (including the upper limits from the ALMA nondetections) and _HST_ flux density upper limit. Due to the deep ALMA
band 6 upper limit, it’s unlikely _Fermi_ will ever be able to rule out
the IC/CMB model in this jet.

**J2203+3145 (4C 31.63):** This quasar is interesting since it was
in the 3FGL catalog, but then was not detected in the 4FGL catalog.
Additionally, we find no evidence for a kpc-scale, resolved X-ray jet
in our _Chandra_ analysis of this source. However, the X-ray jet was
first reported in Hogan et al. (2011). The IC/CMB model is not ruled
out by our _Fermi_ limits. We used the L-band flux density and X-ray
flux density from Hogan et al. (2011) in our SED. We used our own
X-band analysis for the higher-frequency radio flux density.

**J2218** − **0335** **(PKS** **2216-038):** The X-ray jet discovery was
published in Hogan et al. (2011). The radio flux densities and X-ray
spectral index measurement used in our SED come from our own
analysis. Additionally, we used the X-ray flux density and _HST_ upper
limits from Stanley et al. (2015) in our SED. The X-ray and radio
jets are very knotty, and also show a helical pattern. We show an
ALMA non-detection flux density upper limit from our own analysis


MNRAS **000**, 1–23 (2022)



which is not constraining at all. Deeper ALMA imaging would help
constrain the radio-to-optical synchrotron spectrum in this case.

**J2253+1608 (3C 454.3):** This source is another blazar feautring
resolved, kpc-scale X-ray emission (X-ray jet discovery paper: Marshall et al. 2005). We use the optical flux densities from Tavecchio
et al. (2007b) and X-ray flux density/index from Marshall et al.
(2005) in our SED. We use our own radio imaging for the SED,
where we appear to be detecting the radio spectrum just past the
spectral turnover. For this reason, it is not surprising that our ALMA
analysis was unable to detect the jet, and we therefore show flux
density upper limits in the sub-mm/mm bands. This is another case
of a very knotty, cannonball jet.

**J2338+2701 (3C 465):** This X-ray jet discovery was reported in
Hardcastle et al. (2005), and the radio jets resemble the morphology
of the wide-angle tail radio galaxy class. The X-ray emission occurs
in the inner portion of the radio jet upstream of one of the flaring
tails. We use the X-ray flux density reported in Hardcastle et al.
(2005) in our SED and our own VLA/ALMA imaging for the radio
flux densities. We constrcuted a SED for Knot D (the brightest X-ray
knot in the jet).


**A3** **Jet X-ray/Radio Images & Broadband SEDs**


Here we show the radio/X-ray morphologies for our sample, with
false-color X-ray images overlaid with radio contours. The radio
data used to make these images is designated in Table 2. The radio
contours start at a base level of 5 _𝜎_ and increase by factors of two
thereafter (RMS values are given in Table 2). Our _Chandra_ images
are also smoothed with a Gaussian of varying radii in order to better
illustrate the jet morphology. All jet regions analyzed for our SEDs
are labeled in the images, in addition to other regions of interest (the
regions analyzed for our SEDs are noted in the SED figures and in
Table 3).
Our SEDs shown are for the jet regions analyzed in order to test
the IC/CMB model. In most cases these SEDs correspond to the
brightest (anomalous) X-ray knots, but in some cases we used the
entire X-ray jet or combined data from several knots. It’s important
to note that data from several knots can be added together for this
analysis since the _Fermi_ limits (or minimum flux densities) apply to
the entire large-scale jet.
The flux densities used in these SEDs were often taken from the
literature, except for cases in which we used our own analysis (as
described on a source-by-source basis in section A2). Bowties are
shown to illustrate the spectral indexes with associated uncertainties,
and are also taken from the literature when possible. When X-ray
spectral indexes were not available in the literature, we used our own
_Chandra_ analysis when possible to measure the X-ray spectral indexes. In a few cases we also show in-band radio spectral indexes as
bowties in order to better constrain any potential spectral turnovers
of the synchrotron spectrum. We show the phenomenological synchrotron fits as thin black lines, and the IC/CMB model fits as thick
black lines (details concerning these spectral models can be found
in section A). We used radio spectral indexes which best-matched
the measured X-ray spectral indexes, as the radio and X-ray spectral index should match under the IC/CMB model. We also used

synchrotron spectral turnovers which either matched the optical flux
for optical detections or were the most conservative in the case of
optical non-detections. Gray points mark where the measured radioto-optical synchrotron flux densities would appear on the shifted
IC/CMB spectra. The minimum flux densities (or flux density upper limits) for the large-scale jet gamma-rays observed by _Fermi_ /LAT
are given in red, following the methodology presented in Section 2.6.

The naming convention for our jet components analyzed may differ
from other works, so it is important to reference the radio/X-ray images (Figures A3-A5) in interpreting these SEDs. The dotted lines
illustrate our lack of knowledge for the high-energy radio-to-optical
synchrotron spectrum in cases where this information is critical in
the determination of whether the IC/CMB model is ruled out. The

dashed lines correspond to the IC/CMB model fits corresponding to
the dotted synchrotron spectra. It’s important to note that for the purposes of determinining the status on whether or not IC/CMB is ruled
out and the value of the _𝛿_ limits, we use the conservative dashed-line
IC/CMB model predictions.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.



_Testing IC/CMB in Resolved Quasar X-ray Jets_ 23


MNRAS **000**, 1–23 (2022)

24 _P. Breiding et al._


**Figure A3.** _Chandra_ X-ray images of our jet sample are shown as false-color images on a linear scale with the “b” color map of SAOImageDS9. The color map
used ranges from black to white, with warmer colors correpsonding to higher pixel values. The X-ray images are smoothed with Gaussian kernals of various
radii. Overlaid on these X-ray images are radio contours, where the archival data used to make these images is described in Table 2. The radio contours are at a
base level of 5 _𝜎_, spaced by factors of two thereafter (with RMS and synthesized beam properties also given in Table 2). The jet regions analyzed for the SEDs
are delineated in the images, though in some cases we also label other jet components (see the SEDs or Table 3 for clarity on which region was analyzed for the
IC/CMB _Fermi_ test).


MNRAS **000**, 1–23 (2022)

_Testing IC/CMB in Resolved Quasar X-ray Jets_ 25


**Figure A4.** This is a continuation of Figure A3


MNRAS **000**, 1–23 (2022)

26 _P. Breiding et al._


MNRAS **000**, 1–23 (2022)



**Figure A5.** This is a continuation of Figures A3 and A4.

_Testing IC/CMB in Resolved Quasar X-ray Jets_ 27


**Figure A6.** SEDs are shown for each jet from our sample, with blue data points corresponding to measured flux densities with associated 1 _𝜎_ error bars. These
flux densities were taken from the literature, except in a few cases in which we use our own analysis (this is described on a source-by-source basis in section A2).
Bowties are shown to illustrate spectral indexes with associated uncertainties, which are also taken from the literature except for a few sources in which we
used our own analysis (all radio spectral index bowties result from our own data analysis). We show the phenomenological synchrotron fits as thin black lines,
and the IC/CMB model fits as thick black lines. Gray points mark where the measured radio-to-optical synchrotron flux densities would appear on the shifted
IC/CMB spectra and can be considered anchor points for the IC/CMB spectra. The minimum flux densities (or flux density upper limits) for the large-scale jet
gamma-rays observed by _Fermi_ are given in red, following the methodology presented in Section 2.6. The dashed lines are IC/CMB model fits corresponding to
the dotted synchrotron spectra.


MNRAS **000**, 1–23 (2022)

28 _P. Breiding et al._


MNRAS **000**, 1–23 (2022)



**Figure A7.** This is a continuation of Figure A6.

_Testing IC/CMB in Resolved Quasar X-ray Jets_ 29


**Figure A8.** This is a continuation of Figure A6.


MNRAS **000**, 1–23 (2022)

30 _P. Breiding et al._


MNRAS **000**, 1–23 (2022)



**Figure A9.** This is a continuation of Figure A6.


</paper>

## Items to check

```json
[
 {
  "path": "processing.calibration.pipeline_or_manual.evidence[0]",
  "value": "CASA pipeline via scriptForPI.py for ALMA and recent JVLA; manual standard calibration in CASA/MIRIAD for historical VLA and ATCA",
  "failed_quote": "The continuum visibility data were calibrated with the CASA pipeline via the NRAO-provided python script scriptForPI.py, which gives a science-ready measurement set."
 },
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Calibrate visibilities via CASA pipeline (scriptForPI.py for ALMA) or manual calibration, image with tclean/clean using Briggs robust=0.5 and MTMFS (nterms=2), apply phase and amplitude self-calibration, and extract flux densities or 95% upper limits.",
  "failed_quote": "The continuum visibility data were calibrated with the CASA pipeline via the NRAO-provided python script scriptForPI.py, which gives a science-ready measurement set. Similar to the VLA data, we then imaged the visibility data via the CASA task tclean (with Briggs weighting and robust parameter of 0.5)."
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "Binned maximum likelihood optimization",
  "failed_quote": "Following the standard methodology for Fermi/LAT binned likelihood analysis, a binned counts map was made with 30 logarithmically-spaced energy bins and 0.2 degree spatial bins."
 },
 {
  "path": "analysis_steps[4].method.evidence[0]",
  "value": "Fit phenomenological power-law with exponential cutoff models by eye to radio-to-optical synchrotron SEDs, shift in frequency and luminosity via IC/CMB equations to match X-ray flux, compare predicted GeV flux against Fermi limits, and calculate equipartition magnetic fields B_eq, Doppler factor limits delta, and kpc-scale Lorentz factor limits Gamma_max,kpc.",
  "failed_quote": "Phenomenological synchrotron spectral models are fit by eye to the observed radio-to-optical flux densities using single power laws with high-frequency exponential cut-offs."
 },
 {
  "path": "analysis_steps[4].fitting.evidence[0]",
  "value": "By-eye phenomenological fitting of Eq. A1 and analytical IC/CMB shifting via Eqs. A2 and A3",
  "failed_quote": "Phenomenological synchrotron spectral models are fit by eye to the observed radio-to-optical flux densities using single power laws with high-frequency exponential cut-offs."
 },
 {
  "path": "software[0].used_for.evidence[1]",
  "value": "Calibration and imaging of VLA, ALMA, and ATCA radio interferometric data (including tasks tclean and clean, and pipeline scriptForPI.py)",
  "failed_quote": "The continuum visibility data were calibrated with the CASA pipeline via the NRAO-provided python script scriptForPI.py, which gives a science-ready measurement set. Similar to the VLA data, we then imaged the visibility data via the CASA task tclean"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Synchrotron radiation from a second, higher-energy (multi-TeV) electron energy distribution accelerated in situ",
  "failed_quote": "The primary alternative model for the anomalously bright and/or hard X-ray production in MSC X-ray jets is synchrotron radiation originating from a second, higher-energy EED."
 }
]
```
