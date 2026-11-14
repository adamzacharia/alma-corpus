# ALMA Detection of Extended Millimeter Halos in the HD 32297 and HD 61005 Debris Disks

`2018ApJ...869...75M` | The Astrophysical Journal 2018 | first author: MacGregor, Meredith A. | arXiv: 1812.05610 | DOI: 10.3847/1538-4357/aaec71

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Do the HD 32297 and HD 61005 edge-on debris disks, known for swept-back wings in scattered light, show extended millimeter-grain halos, and what is their radial structure?  
  > "Thus, high resolution observations at millimeter wavelengths are especially critical to our understanding of the physical mechanisms shaping the structure of these asymmetric debris disks." (1 Introduction)
- Target **HD 32297**: coordinates _not stated_; z/distance 133 pc  
  > "the HD 32297 (A5V, $<30$ Myr, $133\pm1$ pc)" (1 Introduction); distance from Gaia DR2  
  > "the HD 32297 (A5V, $<30$ Myr, $133\pm1$ pc)" (1 Introduction)
- Target **HD 61005**: coordinates _not stated_; z/distance 36.56 pc (36.6 pc adopted)  
  > "HD 61005 (G8V, 40 Myr, $36.56^{+0.03}_{-0.06}$ pc, nicknamed ‘The Moth’)" (1 Introduction); distance from Gaia DR2  
  > "HD 61005 (G8V, 40 Myr, $36.56^{+0.03}_{-0.06}$ pc, nicknamed ‘The Moth’)" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00633.S, 2012.1.00437.S
- bands: Band 6 (1.3 mm, 230 GHz)  
  > "ALMA in Band 6 (1.3 mm, 230 GHz, #2015.1.00633.S, PI: Alycia Weinberger)" (2 Observations)
- frequencies and spectral setup: New data: four basebands at 215.5, 217.5, 230.538, 232.538 GHz (HD 32297; CO baseband 3840 channels, 1.875 GHz); HD 61005 new data continuum-only at 224, 226, 240, 242 GHz, 2 GHz each  
  > "We used four basebands centered at 215.5, 217.5, 230.538, and 232.538 GHz, and two polarizations (XX and YY)." (2 Observations); "included only four continuum basebands with a bandwidth of 2 GHz each centered at 224, 226, 240, and 242 GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 36 antennas (Cycle 3); 27 and 31 antennas for Cycle 1 HD 61005  
  > "ALMA executed two scheduling blocks (SBs) in Cycle 3 with 36 antennas in two configurations" (2 Observations)
- configurations: _not stated_
- baselines: HD 32297: 15-310 m and 15-704 m; HD 61005: 12-335 m (Cycle 1) and 15-650 m  
  > "2016 Jun 21 | 36 | $15-704$ | 1.15 | 44.4" (Table 1)
- angular resolution: 0.76"x0.51" (HD 32297); 0.49"x0.43" (HD 61005), robust 0.5  
  > "the synthesized beam size is $0.76\ensuremath{''}\times0.51\ensuremath{''}$" (3.1 Continuum Emission)
- max recoverable scale: _not stated_
- sensitivity: rms 14 and 13 μJy/beam (HD 32297, HD 61005); CO rms 1.0 mJy/beam  
  > "These observations achieve sensitivities of 14 and 13 $\mu$Jy beam$^{-1}$ for HD 32297 and HD 61005, respectively" (abstract)
- time on source: HD 32297: 22.2 + 44.4 min; HD 61005: 49.0 + 26.6 (archival) + 44.4 min  
  > "2016 Jun 18 | 36 | $15-650$ | 0.73 | 44.4" (Table 1)
- observing dates: HD 32297: 2016 Jan 1, 2016 Jun 21; HD 61005: 2013 Dec 4, 2014 Mar 20, 2016 Jun 18  
  > "2016 Jan 1 | 36 | $15-310$ | 1.26 | 22.2" (Table 1)
- pi or archival as stated: New Cycle 3 data (PI Weinberger); archival Cycle 1 HD 61005 data (PI Rodriguez)  
  > "Archival observations from ALMA project 2012.1.00437.S (PI: David Rodriguez)" (Table 1)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **HST STIS**: Scattered light images used for comparison and overlay  
  > "previous *Hubble Space Telescope* (HST) STIS coronagraphic images of optical scattered light from (cite: sch14)" (3.1 Continuum Emission)
- Other facility **Gaia DR2**: Updated distances  
  > "gives an updated distance for the HD 32297 system of 133 pc compared with the *Hipparcos* result of 112 pc" (1 Introduction)
- External data: Scattered light images (HST STIS) shown with ALMA contours  
  > "previous *Hubble Space Telescope* (HST) STIS coronagraphic images of optical scattered light from (cite: sch14)" (3.1 Continuum Emission) [from (cite: sch14)]
- External data: CO Einstein A coefficient 6.91e-7 s^-1  
  > "$A_{21}=6.91\times10^{-7}$ s$^{-1}$ is the Einstein A coefficient (cite: hol05)" (3.3 12CO Emission) [from (cite: hol05)]
- External data: Dust opacity 2.3 cm2/g at 1.3 mm  
  > "a commonly used value in the literature is $\kappa_\nu = 2.3$ cm$^2$ g$^{-1}$ at 1.3 mm (cite: beck90)" (4.2) [from (cite: beck90)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline; statwt reweighting  
  > "All of the raw data sets were calibrated with the ALMA pipeline using the `CASA` package (version 4.7.2)." (2 Observations)
- casa version: CASA 4.7.2  
  > "All of the raw data sets were calibrated with the ALMA pipeline using the `CASA` package (version 4.7.2)." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: HD 32297: J0510+1800; HD 61005: J0538-4405  
  > "For HD 32297, observations of J0510+1800 were used for both bandpass and flux calibration." (2 Observations)
- flux scale uncertainty: <10%  
  > "The systematic uncertainty for absolute flux calibration is estimated to be $<10\%$." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN (multi-frequency synthesis) in CASA  
  > "Both continuum and line images were generated using the multi-frequency synthesis `CLEAN` algorithm in the `CASA` package." (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "With robust $=0.5$ weighting, the synthesized beam size is" (3.1 Continuum Emission)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum level subtracted from line spectral window  
  > "the continuum level was subtracted from the spectral window containing the line" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.76"x0.51" PA -65 deg (HD 32297); 0.49"x0.43" PA -71 deg (HD 61005)  
  > "the synthesized beam size is $0.49\ensuremath{''}\times0.43\ensuremath{''}$" (3.1 Continuum Emission)
- final rms: 14 and 13 μJy/beam  
  > "the rms is comparable, 13 $\mu$Jy beam$^{-1}$" (3.1 Continuum Emission)

### Inherited from earlier work

- MCMC visibility-fitting approach  
  > "we adopt our previously described approach (cite: mac13) and fit directly to the millimeter visibilities" (3.2) [from (cite: mac13)]
- Cycle 1 HD 61005 data analysed earlier  
  > "Analysis of these lower resolution observations was presented in (cite: olof16)." (2 Observations) [from (cite: olof16)]
- Optical depth estimate method  
  > "We can estimate the optical depth of the $J=2-1$ line from the 3-D data cube following (cite: mat17a)" (3.3) [from (cite: mat17a)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method details for CO
- CLEAN mask, cell size, image size, iteration threshold
- Initial walker positions and burn-in length
- Stellar flux/ photospheric contribution handling
- Channel binning/velocity range for CO moment maps
- Whether combined datasets were rescaled/phase-aligned between epochs

## Analysis recipe

1. **Calibrate and prepare visibilities**: ALMA pipeline calibration, statwt reweighting, 30 s averaging  
  > "The calibrated visibilities were averaged in 30 second intervals to reduce the total size of the measurement sets" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and CO**: CLEAN MFS with robust 0.5  
  > "With robust $=0.5$ weighting" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit two-component broken power-law belt+halo model to visibilities**: Optically thin, flat, axisymmetric model, T∝r^-0.5, broken power-law Σ; synthetic visibilities compared with data  
  > "we adopt a parametric model with a radial temperature profile, $T\propto r^{-0.5}$, and a surface density profile described by a broken power law" (3.2)
   - software: emcee, vis_sample
   - parameter: 100 walkers, 10,000 steps  
  > "we use $10^6$ iterations (100 walkers and 10,000 steps each)" (3.2)
   - assumption: Continuous surface density at R_halo; no vertical structure  
  > "We assume that the surface density profile of both components is continuous such that $\Sigma_\text{belt}=\Sigma_\text{halo}$ at $R_\text{halo}$." (3.2)
   - fitting: emcee MCMC, chi2 likelihood lnL=-chi2/2, uniform priors with F>0 and 0<Rin<Rhalo<Rout  
  > "We assume uniform priors, with limits that ensure each model is physical: $F_\text{belt}$, $F_\text{halo}$, $F_\text{tot}>0$ and $0<R_\text{in}<R_\text{halo}<R_\text{out}$." (3.2)
   - validation: Gelman-Rubin R-hat<1.1; reduced chi2 1.32 and 1.61; deprojected visibilities; Gaussian comparison  
  > "we compute the Gelman-Rubin statistic (cite: gel92) and ensure that $\hat{R}<1.1$ for all model parameters" (3.2)
4. **Derive CO line properties and gas mass**: Moment maps, integrated flux over 3σ region, optically thin LTE mass at 30 K, optical depth estimate  
  > "For HD 32297, we can calculate the total mass of CO probed by the $J=2-1$ line transition (noted by the subscript 21 in the following equation) for optically thin line emission in LTE:" (Results and Analysis, 12CO Emission)
   - software: CASA
   - assumption: LTE, optically thin, T=30 K, CO/H2=1e-4  
  > "evaluated at a characteristic temperature of 30 K" (3.3)
   - fitting: _not stated_
   - validation: Peak optical depth 0.3 check  
  > "we obtain a peak optical depth of $0.3$, reasonably consistent with optically thin emission" (3.3)
5. **Estimate halo and belt dust masses**: Optically thin M=F D^2/(κ B(T)), dust temperature from radiative equilibrium with emission efficiency β=0.7  
  > "For optically thin dust emission, the dust mass is $M_\text{dust}=F_\nu D^2/(\kappa_\nu B_\nu(T_\text{dust}))$" (4.2)
   - assumption: κ=2.3 cm2/g for belt, 1.3 cm2/g for halo micron grains  
  > "we adopt the typical value of $2.3$ cm$^2$ g$^{-1}$ in our calculations for millimeter-sized grains in the planetesimal belt, and $1.3$ cm$^2$ g$^{-1}$ for micron-sized grains in the halo" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: Calibration, statwt, CLEAN imaging  
  > "we used the `statwt` task in CASA to recalculate the data weights" (2 Observations)
- **emcee** : MCMC fitting  
  > "within a Markov Chain Monte Carlo (MCMC) framework making use of the `emcee` package" (3.2)
- **vis_sample** : Synthetic visibilities for models  
  > "We compute synthetic visibilities for each model using the python package `vis_sample`" (3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD 32297 belt inner edge | 78.5 | ±8.1 | AU | 3 | $R_\text{in}$ / Planetesimal belt inner edge \[AU\] / $78.5\pm8.1$ / $41.9\pm0.9$ |
| HD 32297 belt outer edge | 122 | ±3 | AU | 3 | / $122\pm3$ / $67.0\pm0.5$ / |
| HD 32297 halo outer edge | 440 | ±32 | AU | 3 | / $440\pm32$ / $188\pm8$ / |
| HD 61005 belt inner edge | 41.9 | ±0.9 | AU | 3 | $41.9\pm0.9$ AU and $67.0\pm0.5$ AU for HD 61005 |
| HD 61005 belt outer edge | 67.0 | ±0.5 | AU | 3 | $41.9\pm0.9$ AU and $67.0\pm0.5$ AU for HD 61005 |
| HD 61005 halo outer edge | 188 | ±8 | AU | 3 | The halos extend to $440\pm32$ AU and $188\pm8$ AU, respectively. |
| Belt surface density index x1 (HD 32297, HD 61005) | 2.23, 2.87 | ±0.61, ±0.19 | dimensionless | 3 | $x_1=2.23\pm0.61$ and $2.87\pm0.19$ |
| Halo surface density index x2 (HD 32297, HD 61005) | -6.20, -5.52 | ±0.30, ±0.14 | dimensionless | 3 | $x_2=-6.20\pm0.30$ for HD 32297 and $-5.52\pm0.14$ for HD 61005 |
| 12CO J=2-1 integrated intensity (HD 32297) | 7.91e-21 | ±0.08e-21 | W m^-2 | 4 | $1.02\pm0.01$ Jy km s$^{-1}=7.91\pm0.08\times10^{-21}$ W m$^{-2}$ |
| CO mass HD 32297 | 4.32e-4 | not stated | Earth masses | 4 | This approach yields a total CO mass of $M_\text{CO} = 4.32\times10^{-4}~M_\oplus$. |
| HD 32297 belt dust mass | 0.57 | ±0.07 | Earth masses | 5 | yields a total mass of millimeter-sized grains of $0.57\pm0.07$ $M_\oplus$ |
| HD 32297 inclination | 83.6 | +4.6/-0.4 | deg | 3 | $83.6 (+4.6, -0.4)^\text{a}$ |

## Qualitative findings

- Both disks have a broad planetesimal belt with rising surface density plus a steeply falling halo co-aligned with the scattered light disk.  
  > "a broad ($\Delta R/R> 0.4$) planetesimal belt with a rising surface density gradient, and a steeply falling outer halo aligned with the scattered light disk" (abstract)
- CO gas in HD 32297 shows marginal sub-Keplerian rotation.  
  > "the CO gas appears to exhibit sub-Keplerian rotation, although the significance of this result is unclear" (5 Conclusions)

## Claim tuples

- H: Do mm-sized grains populate the extended halos seen in scattered light? | E: MCMC visibility fits of two-component model to 1.3 mm ALMA data | R: Two-component model with halo out to 440 AU and 188 AU fits better than single power law or Gaussian | F: Millimeter-sized grains likely populate the halos, favoring planetary sculpting | **supported**
- H: Does the surface density gradient constrain stirring? | E: Fit belt power-law index | R: x1 = 2.23±0.61 and 2.87±0.19 | F: Consistent with self-stirred models | **partially**
- H: Is CO gas present in HD 32297 and co-located with dust? | E: Imaged 12CO 2-1 and computed LTE mass | R: Detected, 4.32e-4 Earth masses | F: CO-rich disk, co-located with dust, possible variability vs JCMT | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Broken power law chosen as simplest model justified by sensitivity and resolution  
  > "We choose a broken power law as the simplest model justified by the sensitivity and resolution of our current dataset." (3.2)
- Alternative: Single power law/Gaussian models left significant residuals; more complex models gave no substantially different results  
  > "Although we explored more complicated models that allowed for different surface density profiles, gaps between the belt and halo components, or multiple rings, they did not yield substantially different results." (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Residuals of 4-8σ likely make uncertainties underestimates; vertical structure not fitted  
  > "significant residuals at the $4-8\sigma$ level that could indicate additional asymmetric substructure not resolved by our current observations and likely make our quoted uncertainties underestimates" (5 Conclusions)
- Caveat (inferred, ours): Halo detection depends on model form and unmodelled vertical structure
- Caveat (inferred, ours): LTE CO mass assumption is uncertain
- Caveat (inferred, ours): Halo grain-size inference depends on assumed opacities
- Caveat (inferred, ours): Temperature profile fixed at r^-0.5

## Reproducibility

- Data public (paper): ALMA data identified by project code; acknowledged as ADS/JAO.ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00633.S and #2012.1.00437.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: vis_sample publicly available on GitHub  
  > "`vis_sample` is publicly available at <https://github.com/AstroChem/vis_sample>" (footnote 1)
- Missing: CLEAN parameters
- Missing: Model code and priors implementation details beyond description
- Missing: Line-free channels
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 7/5, Data and software are public and fitting recipe is well described, but imaging details are sparse.
- Rediscovery candidate: yes, Public data, clear model, numeric results in Table 2.

## Links

- Method: (cite: mac13) (MCMC visibility-fitting approach)
- Method: (cite: for13) (emcee)
- Companion: (cite: olof16) (Earlier analysis of Cycle 1 HD 61005 ALMA data)

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 53,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
