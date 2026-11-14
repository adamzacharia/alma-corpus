# Dust Polarization toward Embedded Protostars in Ophiuchus with ALMA. I. VLA 1623

`2018ApJ...859..165S` | The Astrophysical Journal 2018 | first author: Sadavoy, Sarah I. | arXiv: 1804.05968 | DOI: 10.3847/1538-4357/aac21a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the dust polarization morphologies and mechanisms (scattering, magnetic or radiative grain alignment) in the inner disks and extended ring of the Class 0 system VLA 1623?  
  > "We detect highly structured dust polarization toward the inner disks and the extended ring with typical polarization fractions $\approx 1.7$% and $\approx 2.4$%, respectively." (abstract)
- Target **VLA 1623 (A and B)**: coordinates 16:26:26.351 -24:24:30.57 (J2000, phase center)  
  > "The phase center is $\alpha$ $=$ 16:26:26.351 and $\delta =-$24:24:30.57 (J2000)." (3 Results); "At a distance of 120 pc, this maximum recoverable scale spans only 310 au." (4.2 The Extended Dust Ring); z/distance 120 pc  
  > "The phase center is $\alpha$ $=$ 16:26:26.351 and $\delta =-$24:24:30.57 (J2000)." (3 Results); "At a distance of 120 pc, this maximum recoverable scale spans only 310 au." (4.2 The Extended Dust Ring); distance from Ophiuchus distance (Loinard08 cited for the nearby Ophiuchus cloud)  
  > "The phase center is $\alpha$ $=$ 16:26:26.351 and $\delta =-$24:24:30.57 (J2000)." (3 Results); "At a distance of 120 pc, this maximum recoverable scale spans only 310 au." (4.2 The Extended Dust Ring)

## Data provenance

- ALMA projects: 2015.1.01112.S, 2013.1.01004.S
- bands: Band 6 (1.3 mm, 233 GHz), full polarization  
  > "VLA 1623 was observed in full polarization with ALMA in Band 6 (1.3 mm, 233 GHz)" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5, 36 antennas  
  > "using 28 pointings in the C40-5 configuration with 36 antenna" (2 Observations)
- baselines: max baseline 1.12 km (May) or 2.65 km (July)  
  > "a maximum baseline of 1.12 km (May observations) or 2.65 km (July observations)" (2 Observations)
- angular resolution: 0.27'' x 0.21'' (~30 au)  
  > "Our map resolution is $0.27\ensuremath{''} \times 0.21\ensuremath{''}$ or $\sim 30$ au at the distance of Ophiuchus." (2 Observations)
- max recoverable scale: 2.6'' (310 au) from 5th percentile baseline 102.275 m, elevation 80 deg  
  > "We estimate a maximum recoverable scale of $2.6$$''$ using the fifth percentile[^3] baseline (102.275 m)" (4.2 The Extended Dust Ring)
- sensitivity: rms 0.071 (I), 0.027 (Q), 0.027 (U), 0.026 (V) mJy/beam  
  > "The final map sensitivities are 0.071 mJy beam$^{-1}$, 0.027 mJy beam$^{-1}$, 0.027 mJy beam$^{-1}$, and 0.026 mJy beam$^{-1}$ for the Stokes I, Q, U, and V maps" (2 Observations)
- time on source: 7.2 minutes per target field  
  > "The total time on each target field is 7.2 minutes." (2 Observations)
- observing dates: 20 May, 11 July, 13 July 2017  
  > "on 20 May, 11 July, and 13 July 2017" (2 Observations)
- pi or archival as stated: _not stated_
- Line: DCO+ 3-2 (absorption, Cycle 2 data, comparison only) (not stated)
- Other facility **Literature mm observations (ALMA Cycle 0, SMA, BIMA, CARMA)**: Archival positions of VLA 1623-B for proper motion fit; CARMA polarization comparison  
  > "we collect the positions of VLA 1623-B from four sub-arcscecond millimeter observations in the literature" (5.5 Proper Motion of VLA 1623)
- External data: Positions, epochs, peak fluxes of VLA 1623-B from earlier mm observations  
  > "We find four studies in the literature that meet these criteria: (cite: Murillo13), (cite: Maury12), (cite: Chen13), (cite: Looney00)." (Appendix Proper Motion) [from Murillo13, Maury12, Chen13, Looney00]
- External data: Dust opacity 0.024 cm2/g at 1.3 mm  
  > "We assume $T = 20$ K and $\kappa = 0.024$ cm$^2$ g$^{-1}$ at 1.3 mm (cite: Andrews09)." (5.1 Model Results) [from Andrews09]
- External data: Proper motion of S1 used for comparison  
  > "$\mu_{\alpha,S1}\cos\delta = -3.88$ mas yr$^{-1}$ and $\mu_{\delta, S1} = -31.55$ mas yr$^{-1}$" (5.5 Proper Motion of VLA 1623) [from Loinard08]
- Simulation/model as data: Analytic flux-frozen oblate Plummer spheroid hourglass magnetic field model (A=10, inclination 54 deg, nu0=60, r0=40 au) compared by eye to b-vectors  
  > "we incline the spheroid and its associated field lines through a polar angle of $\theta=54\degree$ from the plane of the sky toward the line of sight." (5.1 Model Description)

## Processing

### Calibration

- pipeline or manual: manual calibration  
  > "The data are calibrated manually using CASA 4.7.2." (2 Observations)
- casa version: CASA 4.7.2  
  > "The data are calibrated manually using CASA 4.7.2." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 (20 May, 13 July); J1733-1304 (11 July); bandpass J1517-2422, phase J1625-2527, leakage J1549+0237  
  > "For flux calibration, we use J1517-2422 for the 20 May and 13 July observations and J1733-1304 for the 11 July observations." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: three rounds of phase-only self-calibration, successively smaller intervals; amplitude self-cal rejected  
  > "Thus, for our final maps, we use three rounds of phase-only self calibration." (2 Observations)

### Imaging

- task: clean, interactive for Stokes I; non-interactive for Q, U, V  
  > "For the Stokes Q, U, and V observations, we run *clean* non-interactively and without multi-scale." (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manual interactive regions for bright emission in Stokes I  
  > "we use *clean* in interactive mode to manually identify regions with bright emission" (2 Observations)
- multiscale scales: multi-scale used for Stokes I (scales not stated)  
  > "We also use the multi-scale option to recover the extended emission better." (2 Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to each Stokes map  
  > "We perform one final, deep iteration of clean and a primary beam correction on each of the four Stokes maps" (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.27'' x 0.21''  
  > "Our map resolution is $0.27\ensuremath{''} \times 0.21\ensuremath{''}$" (2 Observations)
- final rms: 0.071/0.027/0.027/0.026 mJy/beam (I/Q/U/V); I dynamic range limited  
  > "The sensitivity of the Stokes I map is dynamic range limited, resulting in its higher rms value." (2 Observations)

### Inherited from earlier work

- Full survey details and calibration to be given in a future paper  
  > "Full details on the entire survey will be provided in a future paper." (2 Observations) [from future survey paper]
- Polarization debiasing and P/sigma>4 cut  
  > "The most common approach to debias dust polarization observations follows a basic maximum likelihood characterization (cite: SimmonsStewart85; Vaillancourt06):" (3 Results) [from SimmonsStewart85; Vaillancourt06]
- Model details to be published separately  
  > "Further details of this procedure and these models are described in a forthcoming publication (Myers et al. 2018, in preparation)." (5.1 Model Description) [from Myers et al. 2018, in preparation]

### Not stated but needed to reproduce (our reading)

- Robust/weighting, cell size, image size, niter and threshold for clean
- Multiscale scales used
- Self-calibration solution intervals and reference antenna/spw
- Spectral setup and continuum bandwidth
- Line-free/continuum channel selection
- Pixel-level masks for ring and disk region definitions beyond the 4 sigma contours with 'slight modification'
- Flux of the calibrators and flux scale uncertainty
- Model matching is by eye; no fit parameters or objective criteria

## Analysis recipe

1. **Calibrate and self-calibrate**: Manual CASA calibration, then three rounds of phase-only self-calibration  
  > "Thus, for our final maps, we use three rounds of phase-only self calibration." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Visual check of amplitude profile and comparison of signal/sensitivity after each round  
  > "visually check the amplitude profile of VLA 1623 after applying the solutions" (2 Observations)
2. **Image Stokes I, Q, U, V**: clean with primary beam correction; multi-scale interactive for I  
  > "We perform one final, deep iteration of clean and a primary beam correction on each of the four Stokes maps" (2 Observations)
   - software: CASA clean
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive polarization maps**: Debiased polarized intensity sqrt(Q^2+U^2-sigma^2), angle 0.5 atan(U/Q), fraction PI/I  
  > "we limit our analysis to only those data with $\mbox{$\mathcal{P}_I$}/\mbox{$\sigma_{\mathcal{P}I}$}>4$" (3 Results)
   - parameter: P/sigma>4; sigma_PI ~ sigma_Q ~ sigma_U; 0.1% fraction uncertainty  
  > "We assume a 1 $\sigma$ polarization fraction uncertainty of 0.1%" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit Gaussians to inner disks**: imfit Gaussian fits to Stokes I, deconvolved with beam; no background subtraction  
  > "We fit the disks using the *imfit* task in MIRIAD (cite: Sault95)." (4.1 The Inner Protostellar Disks)
   - software: MIRIAD
   - assumption: inclination from cos i = b/a  
  > "assuming $\cos{i} = b/a$ (see Table [1](#disk_prop))" (4.1 The Inner Protostellar Disks)
   - fitting: imfit; errors from range of deconvolved parameters  
  > "with errors estimated by the largest absolute difference between the best-fit deconvolved parameters and the range of deconvolved parameters when considering the errors in the observed Gaussian fit from *imfit*." (Polarization Morphology: The Inner Protostellar Disks)
   - validation: _not stated_
5. **Compare polarization to mechanisms**: Compare e-vector angles to disk minor axes, spectral index (nterms=2) for optical depth, Stokes I gradient vs polarization angle for ring  
  > "Figure [11](#ang_diff) shows these relative angles for the ring only." (5.2 Radiation Field Alignment)
   - software: CASA clean
   - fitting: _not stated_
   - validation: Smoothing ALMA data to CARMA resolution reproduces CARMA position angle  
  > "From our smoothed data, we find a typical position angle of -57, which matches (cite: Hull14)." (4.3 Comparison to Previous Polarization Observations)
6. **Model hourglass magnetic field**: Analytic flux-frozen oblate Plummer spheroid model, matched by eye to ring b-vectors; ring mass from 1.3 mm flux  
  > "We qualitatively match our model by eye to the observations." (5.1 Model Results)
   - software: MIRIAD
   - parameter: A=10, theta=54 deg, nu0=60, r0=40 au, peak density ~6e10 cm-3  
  > "We also adopt a ratio of peak density to background density of $\nu_0 = 60$" (5.1 Model Results)
   - assumption: T = 20 K, kappa = 0.024 cm2/g at 1.3 mm, d = Ophiuchus distance  
  > "We assume $T = 20$ K and $\kappa = 0.024$ cm$^2$ g$^{-1}$ at 1.3 mm (cite: Andrews09)." (5.1 Model Results)
   - fitting: by eye, no formal fit  
  > "We qualitatively match our model by eye to the observations." (Discussion: Model Results)
   - validation: Good by-eye agreement in NW and SE quadrants; departures in NE and SW  
  > "There are noticeable departures in the north-east and south-west quadrants, however." (5.1 Model Results)
7. **Measure proper motion**: chi^2 linear regression of VLA 1623-B positions across epochs 1997-2017  
  > "We fit the positions of VLA 1623-B with a $\chi^2$ linear regression" (5.5 Proper Motion of VLA 1623)
   - parameter: position errors sigma = FWHM/(I/sigma_I)  
  > "we assume $\sigma_{\alpha} = \sigma_{\delta} = \mbox{FWHM}/(I/\sigma_I)$" (Appendix Proper Motion)
   - fitting: chi^2 linear regression  
  > "We fit the positions of VLA 1623-B with a $\chi^2$ linear regression" (Discussion: Proper Motion of VLA 1623)
   - validation: Orbital motion and atmospheric noise considered and rejected; compared with S1 proper motion  
  > "We find that orbital motions are an unlikely cause." (Appendix Proper Motion)

## Software

- **CASA** 4.7.2: manual calibration and clean imaging  
  > "The data are calibrated manually using CASA 4.7.2." (2 Observations)
- **MIRIAD** : imfit Gaussian fits and source subtraction  
  > "We fit the disks using the *imfit* task in MIRIAD (cite: Sault95)." (4.1 The Inner Protostellar Disks)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stokes I flux VLA 1623-A | 141.8 | 5.9 | mJy | 4 | / flux (mJy)             / $141.8 \pm 5.9$   / $127.3 \pm 1.9$   / |
| Stokes I flux VLA 1623-B | 127.3 | 1.9 | mJy | 4 | / flux (mJy)             / $141.8 \pm 5.9$   / $127.3 \pm 1.9$   / |
| Median polarization fraction of inner disks | 1.7 | not stated | % | 3 | median polarization fractions of 1.7% |
| Typical polarization fraction of ring | 2.4 | not stated | % | 3 | with a typical polarization fraction of 2.4% |
| Ring 1.3 mm flux | 0.6 | not stated | Jy | 6 | we use this source-subtracted image to measure the 1.3 mm flux of the ring, $S_{1.3} = 0.6$ Jy |
| Ring mass | 0.1 | not stated | Msun | 6 | we calculate a total mass for the ring $M = S_{1.3}d^2/B(T)\kappa = 0.1\ \mbox{M$_{\odot}$}$ |
| Proper motion mu_alpha cos delta | -7.8 | 1.6 | mas/yr | 7 | \mu_\alpha\cos\delta &=& (-7.8 \pm 1.6)\ \mbox{mas}\ \mbox{yr}^{-1} |
| Proper motion mu_delta | -27 | 1.6 | mas/yr | 7 | \mu_\delta &=& (-27 \pm 1.6)\ \mbox{mas}\ \mbox{yr}^{-1} |
| Column density at polarization transition | 5e24 | not stated (lower limit) | cm-2 | 5 | the transition point corresponds to a column density of $\mbox{N(H$_2$)}\approx 5 \times 10^{24}$ cm$^{-2}$ |

## Qualitative findings

- Inner disks show uniform polarization aligned with minor axes consistent with self-scattering; ring shows azimuthal polarization  
  > "The disks shown uniform polarization morphologies aligned with their short axes, whereas the ring shows azimuthal polarization." (6 Summary and Conclusions)

## Claim tuples

- H: What mechanism produces polarization in the inner disks of VLA 1623-A and B? | E: Compare polarization angles, fractions and optical depth (spectral index ~2) with scattering models | R: Uniform angles near minor axes, median 1.7%, optically thick | F: Inner disk polarization is most consistent with dust self-scattering | **supported**
- H: Is the ring polarization due to a flux-frozen magnetic field? | E: By-eye comparison of b-vectors with an analytic oblate spheroid hourglass model | R: Good agreement apart from NE and SW quadrants | F: Ring consistent with magnetized hourglass field, though radiative alignment is an alternative | **partially**
- H: Does VLA 1623 show detectable proper motion? | E: Linear fit to VLA 1623-B positions from 1997-2017 | R: mu = (-7.8, -27) mas/yr, offset of ~0.14'' vs Cycle 2 | F: Proper motion must be corrected when combining epochs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Maximum likelihood debiasing used because it is the common approach, valid only for well-detected polarization  
  > "Since the maximum likelihood method is reliable only for well-detected dust polarization" (3 Results)
- Alternative: Pure self-scattering rejected for ring; mechanical alignment judged unlikely; orbital motion and atmospheric noise rejected as cause of offsets  
  > "Thus, mechanical grain alignment from the outflow is unlikely to impact our observations." (5.4 Mechanical Grain Alignment)
- How they decided it was enough: _not stated_
- Limitation (authors): Model is simple, axisymmetric, excludes rotation, matched by eye; short spacings missing to trace hourglass  
  > "The model is only a first step toward a full description, which should include both disk rotation and the dense core environment." (5.1 Magnetic Field Alignment)
- Caveat (inferred, ours): By-eye model match gives no quantitative goodness of fit; degeneracy with radiative alignment unresolved
- Caveat (inferred, ours): Ring defined with ad hoc modifications to 4 sigma contours
- Caveat (inferred, ours): Only 7.2 min on source; Stokes I dynamic range limited
- Caveat (inferred, ours): Proper motion fit uses heterogeneous literature positions with ad hoc error estimates

## Reproducibility

- Data public (paper): Acknowledgements cite ALMA project data; public status not stated explicitly  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01112.S and ADS/JAO.ALMA#2013.1.01004." (Acknowledgements)
- Products in archive: _not stated_
- Missing: clean parameters (robust, scales, cell, imsize, thresholds)
- Missing: self-cal solution intervals
- Missing: spectral setup
- Missing: region masks
- Missing: model code (Myers et al. in prep)
- Data volume (inferred): ~10-50 GB (three short execution blocks of a polarization survey)
- Score (inferred): 3/5, Data identified and polarization derivation clear, but imaging/self-cal parameters missing and the model comparison is by eye.
- Rediscovery candidate: no, Key imaging parameters are missing and the main interpretation is qualitative, though polarization fractions and proper motion are numeric.

## Links

- Method: Vaillancourt06 (polarization debiasing and threshold)
- Method: Hull14 (polarization angle uncertainty and CARMA comparison)
- Companion: Harris et al. (submitted) (gap between VLA 1623-A and the ring)
- Companion: Myers et al. 2018, in preparation (magnetic field model details)
- Related: ALMA Cycle 3 Ophiuchus embedded protostar polarization survey (2015.1.01112.S)
- Related: ALMA Cycle 2 project 2013.1.01004.S

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 56,
  "rate": 0.683
 },
 "evidence_ok": true
}
```
