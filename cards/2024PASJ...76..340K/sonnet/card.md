# Sub-parsec-scale jet-driven water maser with possible gravitational acceleration in the radio galaxy NGC 1052

`2024PASJ...76..340K` | Publications of the Astronomical Society of Japan 2024 | first author: Kameno, Seiji | arXiv: 2402.06166 | DOI: 10.1093/pasj/psae015

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Is the 321-GHz H2O emission in NGC 1052 a maser (brightness temperature, size, variability), and what do its velocity structure, drift and spatial distribution say about the jet-torus region?  
  > "New ALMA long-baseline observations were deemed necessary to confirm that the emission was of masers, and also allows us to clarify the spatial distribution of population-inverted molecular gas." (Introduction)
- Target **NGC 1052**: coordinates _not stated_; z/distance D_L = 17.6 Mpc, D_A = 17.5 Mpc, 85 pc/arcsec, V_sys,LSR = 1492 km/s  
  > "We employ the systemic velocity of $V_{\rm sys, LSR} = 1492$ km s$^{-1}$, the luminosity distance of $D_L = 17.6$ Mpc, the angular distance of $D_A = 17.5$ Mpc" (Introduction); distance from Kameno et al. 2020 (cite: 2020ApJ...895...73K)  
  > "We employ the systemic velocity of $V_{\rm sys, LSR} = 1492$ km s$^{-1}$, the luminosity distance of $D_L = 17.6$ Mpc, the angular distance of $D_A = 17.5$ Mpc" (Introduction)

## Data provenance

- ALMA projects: 2023.A.00023.S, 2021.1.00341.S
- bands: _not stated_
- frequencies and spectral setup: 4 SPWs in 2-GHz basebands; BB4 (USB) FDM on H2O line, 976.562 kHz channels (0.914 km/s); other three TDM  
  > "BB4 in USB was tuned to cover the H$_2$O $J_{Ka, Kc} = 10_{2,9} - 9_{3,6}$ emission and the SPW was set in the frequency division mode (FDM) with a channel separation of 976.562 kHz corresponding to 0.914 km s$^{-1}$." (2.1 Observations)
- continuum bandwidth: 5.4 GHz effective  
  > "to maximize the sensitivity in continuum emission with a effective bandwidth of 5.4 GHz." (2.1 Observations)
- arrays: C-10 configuration, two executions  
  > "ALMA observations under C-10 (the most extended) array configuration with the maximum baseline length of 15.2 km have been carried out twice on 2023-07-10 and 2023-07-24" (2.1 Observations)
- configurations: _not stated_
- baselines: max 15.2 km  
  > "the maximum baseline length of 15.2 km" (2.1 Observations)
- angular resolution: continuum beams 0.017x0.011 arcsec and 0.012x0.010 arcsec (uniform)  
  > "We employed uniform weighting that yielded the synthesized beams of $0^{\prime \prime}.017 \times 0^{\prime \prime}.011$ and $0^{\prime \prime}.012 \times 0^{\prime \prime}.010$" (2.2 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 1108 s on target per execution  
  > "Integration times on the target (NGC 1052) and on a bandpass calibrator were 1108 s and 912 s, respectively, for each execution." (2.1 Observations)
- observing dates: 2023-07-10 and 2023-07-24  
  > "have been carried out twice on 2023-07-10 and 2023-07-24" (2.1 Observations)
- pi or archival as stated: _not stated_
- Line: H2O 10(2,9)-9(3,6) (321.225677 GHz)
- External data: Earlier 2022-05-12 ALMA detection spectrum/components (1333 and 1467 km/s) used for drift comparison  
  > "If B1 is identified as the 1333 km s$^{-1}$ component (cite: 2023PASJ...75L...1K) on 2022-05-12" (4.2 Velocity drift) [from (cite: 2023PASJ...75L...1K)]
- External data: Black hole mass 1.5e8 Msun  
  > "SMBH that weighs $M_{\rm BH} = 1.5 \times 10^8$ M$_{\Sol}$ (cite: 2002ApJ...579..530W)" (4.2 Velocity drift) [from (cite: 2002ApJ...579..530W)]
- External data: Maser excitation density n_H2 >~ 3.3e8 cm-3  
  > "$n_{\rm H2} > 3.3 \times 10^8$ cm$^{-3}$ (cite: 2016MNRAS.456..374G)" (4.4 Torus structure) [from (cite: 2016MNRAS.456..374G)]

## Processing

### Calibration

- pipeline or manual: standard phase and amplitude calibration  
  > "Phase and amplitude calibrations were applied following the standard way, using CASA (cite: 2022PASP..134k4501C) 6.4.1." (2.2 Data Reduction)
- casa version: CASA 6.4.1  
  > "using CASA (cite: 2022PASP..134k4501C) 6.4.1." (2.2 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: bandpass calibrators as flux calibrators: J0423-0120 2.104 Jy, J0238+1636 1.304 Jy  
  > "assuming 2.104 Jy for J$0423-0120$ and 1.304 Jy for J$0238+1636$." (2.2 Data Reduction)
- flux scale uncertainty: ~3%  
  > "This amplitude calibration yields $\sim 3$% uncertainty." (2.2 Data Reduction)
- self calibration: target self-calibrated (phase); Difmap self-cal with CLEAN components  
  > "The target, NGC 1052, was bright and compact enough to allow phase calibration by itself." (2.2 Data Reduction)

### Imaging

- task: tclean for line cubes; Difmap for continuum  
  > "Then, we used the task `tclean` with the natural weighting to produce image cubes." (2.2 Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural (line); uniform (continuum)  
  > "We employed uniform weighting that yielded the synthesized beams" (2.2 Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum-subtracted cross power spectra in BB4  
  > "We produced continuum-subtracted cross power spectra in BB4." (2.2 Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: smoothed bandpass with 9-channel width  
  > "We applied smoothed bandpass calibration (cite: 2012PASJ...64..118Y) with a 9-channel smoothing width" (2.2 Data Reduction)
- final beam: super-resolution images with 1.5 mas circular restoring beam  
  > "we produced super-resolution images with a 1.5-milliarcsec (mas) circular restoring beam." (2.2 Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Physical parameters of jet-torus interaction following earlier discussion  
  > "Here we argue about physical parameters following discussion in (cite: 2023ApJ...944..156K)." (4.3 Jet-torus interaction) [from (cite: 2023ApJ...944..156K)]
- Systemic velocity, distances and linear scale  
  > "the linear scale of $85$ pc arcsec$^{-1}$ (cite: 2020ApJ...895...73K)" (Introduction) [from (cite: 2020ApJ...895...73K)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum definition for BB4 continuum subtraction
- tclean cell size, image size, niter, threshold, mask
- Self-calibration solution intervals
- Initial values and ranges for Gaussian/Lorentzian nls decomposition
- Table of observation log contents (rms values) not in text
- Details of the uv-distance Gaussian fitting method and 99% confidence band
- 2022-05-12 spectrum from earlier paper needed for the 424-day comparison

## Analysis recipe

1. **Calibrate and form line/continuum data**: Standard CASA calibration, smoothed bandpass, continuum subtraction in BB4, self-calibration on target  
  > "Phase and amplitude calibrations were applied following the standard way, using CASA (cite: 2022PASP..134k4501C) 6.4.1." (2.2 Data Reduction)
   - software: CASA
   - parameter: 9-channel bandpass smoothing; flux 2.104 Jy J0423-0120, 1.304 Jy J0238+1636  
  > "We applied smoothed bandpass calibration (cite: 2012PASJ...64..118Y) with a 9-channel smoothing width" (2.2 Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract line spectra and decompose**: Spectra at phase-centre pixel of tclean cubes; nls fit of 7 Gaussian/Lorentzian components  
  > "we used the non-linear least squares function, `nls`, in the R statistical language (cite: 2023R) for spectral decomposition with 7 velocity components with either Gaussian or Lorentzian profile" (3.1 Line profiles)
   - software: CASA, R
   - fitting: nls least squares; profile type chosen to minimize residuals  
  > "We chose Gaussian or Lorentzian profile for each component to minimize the residuals." (3.1 Line profiles)
   - validation: chi2/d.o.f. of residuals  
  > "Residuals of the fittings results are characterized by $\chi^2$ over the degree of freedoms (d.o.f.)" (3.1 Line profiles)
3. **Measure emission sizes and brightness temperature**: Gaussian fit to visibility amplitude vs uv distance for continuum and blue (1360-1500 km/s) and red (1500-1625 km/s) line components  
  > "We measured sizes of the continuum and line-emitting components by fitting a Gaussian function to visibilities as a function of spatial frequency" (3.2 Size of emission regions)
   - fitting: Most-likelihood best fit with 99% confidence band  
  > "Best and max sizes are derived by the most likelihood and 99% confidence band shown in figure [4](#fig:uvplot)." (3.2 Size of emission regions)
   - validation: _not stated_
4. **Continuum imaging and structure**: Difmap CLEAN with uniform weighting on BB1-3; compare self-cal agreement factors with single vs aligned components  
  > "Significant improvements in agreement factors justify the reality of the elongated structure." (2.2 Data Reduction)
   - software: Difmap
   - fitting: _not stated_
   - validation: agreement factors sigma 3.94/4.93 vs 3.57/1.81  
  > "those with the aligned CLEAN components result in $\sigma = 3.57$ and $1.81$." (2.2 Data Reduction)
5. **Position line components and velocity gradient**: uvmodelfit point-source fits on continuum-subtracted visibilities binned by 5 channels (4.57 km/s); linear regression V_LSR ~ jJ + dD  
  > "We performed `uvmodelfit` task in CASA to estimate the positions of line emission source using continuum-subtracted visibilities binned by 5 spectral channels (4.57 km s$^{-1}$)." (3.4 Positioning line emitting components)
   - software: CASA
   - parameter: detection threshold 3x line image rms; J axis PA=68.35 deg  
  > "Threshold for the maser flux density was set to $3\times$ the line image rms" (3.4 Positioning line emitting components)
   - fitting: linear regression  
  > "We applied linear regression of $V_{\rm LSR} \sim j J + d D$, where $J$ and $D$ are offset along PA=$68^{\circ}.35$ and $-21^{\circ}.65$, respectively, to estimate the velocity gradients" (Results, Positioning line emitting components)
   - validation: _not stated_
6. **Derive drift, acceleration and maser distance**: Velocity change of B1 over 14 days gives g; r = sqrt(GM/g)  
  > "$r = \sqrt{GM_{\rm BH}/g} = 0.072$ pc or $5000 \ R_{\rm s}$" (4.2 Velocity drift)
   - assumption: M_BH = 1.5e8 Msun; drift due to gravitational acceleration  
  > "If the velocity drift is ascribed to gravitational acceleration of the SMBH that weighs $M_{\rm BH} = 1.5 \times 10^8$ M$_{\Sol}$" (4.2 Velocity drift)
   - fitting: _not stated_
   - validation: Compared with drift over 424 days vs earlier epoch and with NGC 4258  
  > "Since the drift rate in 424 days is significantly smaller than that in 14 days, it is unlikely to identify the 1333 km s$^{-1}$ component as B1." (4.2 Velocity drift)

## Software

- **CASA** 6.4.1: calibration, tclean imaging, uvmodelfit  
  > "using CASA (cite: 2022PASP..134k4501C) 6.4.1." (2.2 Data Reduction)
- **Difmap** : continuum imaging and self-calibration  
  > "We performed continuum imaging with Difmap (cite: 1994BAAS...26..987S)" (2.2 Data Reduction)
- **R (nls)** : spectral component decomposition  
  > "we used the non-linear least squares function, `nls`, in the R statistical language (cite: 2023R)" (3.1 Line profiles)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated line flux 2023-07-10 | 10.79 | 0.33 | Jy km/s | 2 | The integrated flux densities of $10.79 \pm 0.33$ Jy km s$^{-1}$ and $14.32 \pm 0.43$ Jy km s$^{-1}$ |
| Integrated line flux 2023-07-24 | 14.32 | 0.43 | Jy km/s | 2 | The integrated flux densities of $10.79 \pm 0.33$ Jy km s$^{-1}$ and $14.32 \pm 0.43$ Jy km s$^{-1}$ |
| Isotropic luminosity (07-10, 07-24) | 1120 and 1486 | 34 and 45 | Lsun | 2 | isotropic luminosities of $1120 \pm 34$ L$_{\Sol}$ and $1486 \pm 45$ L$_{\Sol}$ |
| Blue component peak flux increase in 14 d | 34.5 | 4.2 | % | 2 | the peak flux density increased by $34.5 \pm 4.2$% and the center velocity shifted by $4.85 \pm 0.5$ km s$^{-1}$ in 14 days |
| Continuum flux density (07-10, 07-24) | 0.624 and 0.704 | 0.019 and 0.021 | Jy | 3 | increased from $0.624 \pm 0.019$ Jy to $0.704 \pm 0.021$ Jy by $12.8 \pm 4.2$% |
| Maser emitter size | <0.6 | not stated | mas | 3 | allowed us to constrain the size of emission region in $<0.6$ milliarcsec (mas) and the brightness temperature of $T_{\rm B} > 10^6$ K. |
| Blue component velocity drift | 127 | 13 | km/s/yr | 6 | B1 maser component showed the velocity drift of $127 \pm 13$ km s$^{-1}$ yr$^{-1}$ or acceleration of $g = 4.0 \times 10^{-3}$ m s$^{-2}$. |
| Maser distance from SMBH | 0.072 pc (5000 Rs) | not stated | pc | 6 | $r = \sqrt{GM_{\rm BH}/g} = 0.072$ pc or $5000 \ R_{\rm s}$ |
| Velocity gradient along jet | -174 | 19 | km/s/mas | 5 | We identified velocity gradient of $-174 \pm 19$ km s$^{-1}$ mas$^{-1}$ along the jet. |
| Red component drift (weighted mean velocity) | 164 | 37 | km/s/yr | 6 | The change of weighted mean velocity corresponds to $164 \pm 37$ km s$^{-1}$ yr$^{-1}$ |

## Qualitative findings

- Redshifted and blueshifted components span ~400 km/s separated by a local minimum near systemic velocity.  
  > "The maser spectrum consists of redshifted and blueshifted velocity components spanning $\sim 400$ km s$^{-1}$, separated by a local minimum around the systemic velocity of the galaxy." (abstract)

## Claim tuples

- H: The 321-GHz H2O emission is maser, not thermal | E: Long-baseline C-10 observations; size by uv-fit; variability over 14 days | R: size <0.6 mas, T_B >1e6 K, flux change in 14 d | F: Emission is definitely a maser | **supported**
- H: Maser velocity drift reflects gravitational acceleration by the SMBH | E: Compare B1 centre velocities between two epochs 14 days apart | R: 127±13 km/s/yr drift | F: Implies maser at ~5000 Rs; possible but may be misidentified components | **partially**
- H: Maser gas is driven by jet-torus interaction | E: Position of line components via uvmodelfit and velocity gradient regression | R: gradient -174±19 km/s/mas along jet, none perpendicular | F: Population-inverted gas is driven by the jet | **supported**

## Reasoning

- Why this data: Longer baselines needed to measure brightness temperature and confirm maser  
  > "A higher angular resolution was required to confirm for maser emission by brightness temperature" (Introduction)
- Why this method: _not stated_
- Alternative: Rotating disk model for the velocity gradient rejected: expected gradient inconsistent with observed and orientation along jet  
  > "The observed velocity gradient is not consistent with the expectation for the rotating disk model." (4.3 Velocity gradient)
- How they decided it was enough: _not stated_
- Limitation (authors): Red component decomposition not unique; drift versus growth ambiguous; first epoch had poorer uv coverage  
  > "The decompositions are not unique, especially in the red component consisting of complex sub-components." (3.1 Line profiles)
- Caveat (inferred, ours): Drift based on only two epochs 14 days apart with non-unique component identification
- Caveat (inferred, ours): Drift and distance depend on assumed M_BH
- Caveat (inferred, ours): No absolute astrometry; positions relative to continuum core only

## Reproducibility

- Data public (paper): Reduction scripts and reduced data in GitHub repository  
  > "Reduction scripts and reduced data are available in the GitHub repository." (2.2 Data Reduction)
- Products in archive: _not stated_
- Code: GitHub repository kamenoseiji/ALMA-2022.A.00023.S including plotMaserSpec.R  
  > "See the source code `plotMaserSpec.R` in the repository for detail." (3.1 Line profiles)
- Missing: Imaging parameters (cell, size, niter, mask)
- Missing: Line-free channels
- Missing: Self-cal solints
- Data volume (inferred): ~50-200 GB for two C-10 executions
- Score (inferred): 4/5, Public data, scripts released, numeric results; some imaging settings omitted.
- Rediscovery candidate: yes, Public data, code in repository, recipe mostly complete and results numeric.

## Links

- Method: (cite: 2012PASJ...64..118Y) (smoothed bandpass calibration)
- Companion: (cite: 2023PASJ...75L...1K) (first detection of 321-GHz H2O maser in NGC 1052 (earlier epoch))

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2023.A.00023.S",
  "2021.1.00341.S"
 ],
 "obscore_codes_not_in_card": [
  "2022.A.00023.S"
 ],
 "codes_printed_but_missing": [
  "2022.A.00023.S"
 ],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 49,
  "rate": 0.645
 },
 "evidence_ok": true
}
```
