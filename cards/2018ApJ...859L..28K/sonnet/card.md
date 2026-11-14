# Probing Signatures of a Distant Planet around the Young T-Tauri Star CI Tau Hosting a Possible Hot Jupiter

`2018ApJ...859L..28K` | The Astrophysical Journal Letters 2018 | first author: Konishi, Mihoko | arXiv: 1805.07498 | DOI: 10.3847/2041-8213/aac6d2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Does the disk of CI Tau, which hosts a hot Jupiter candidate, show a gap that could be created by a distant planet?  
  > "We search for signatures of a distant planet around the two-million-year-old classical T-Tauri star CI Tau hosting a hot Jupiter candidate" (abstract)
- Target **CI Tau**: coordinates _not stated_; z/distance 158.7±1.2 pc  
  > "We employ recent astrometic measurements from the $Gaia$ data release 2 which revealed the distance of 158.7$\pm$1.2 pc (cite: bailer-jones+18)." (Introduction); distance from Gaia DR2 (Bailer-Jones et al. 2018)  
  > "We employ recent astrometic measurements from the $Gaia$ data release 2 which revealed the distance of 158.7$\pm$1.2 pc (cite: bailer-jones+18)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.01207.S
- bands: Band 6 (1.3 mm)  
  > "CI Tau was observed by ALMA band 6 (1.3 mm) as part of the Cycle 3 program 2015.1.01207.S" (2.1 Observations)
- frequencies and spectral setup: Four spectral windows centered on 216.7, 231.2, 234.4 GHz (937.5 MHz bandwidth each) and 219.9 GHz (234.375 MHz)  
  > "three spectral windows (937.500 MHz bandwidth) centered on 216.7, 231.2, 234.4 GHz and the other one (234.375 MHz bandwidth) centered on 219.9 GHz" (2.1 Observations)
- continuum bandwidth: 1875.0 MHz total  
  > "The dust continuum image (with a total bandwidth of 1875.0 MHz) was generated from line-free spectral windows" (2.2 Data Reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 1.6 km, 44 antennas of the 12-m array  
  > "44 antennas in the 12-m array were used with a baseline length ranging from 15.1 m to 1.6 km." (2.1 Observations)
- angular resolution: 0.25" x 0.17" (superuniform); 0.29" x 0.28" after taper  
  > "The beaming size of the `CLEAN`ed image is 0.25$''$ $\times$ 0.17$''$ (40 $\times$ 27 au) with a position angle of 0.6$^{\circ}$" (2.2 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma ~0.17 mJy/beam  
  > "its 1$\sigma$ noise is $\sim$0.17 mJy beam$^{-1}$" (2.2 Data Reduction)
- time on source: 18.4 min  
  > "The total on-source integration time was 18.4 min." (2.1 Observations)
- observing dates: August 27, 2016 UT  
  > "on August 27, 2016 UT" (2.1 Observations)
- pi or archival as stated: Archival data from program of PI H. Nomura  
  > "which are publicly available from the ALMA data archive" (Introduction)
- External data: Dust midplane temperature profile T_d(R)=178±3 (R/1 au)^-0.57±0.02, q=1/2  
  > "the dust temperature at the disk midplane given in (cite: andr07), $T_d(R) = 178\pm3\ (R/1\ {\rm au})^{-0.57\pm0.02}$" (3 Disk modeling) [from Andrews & Williams 2007 (cite: andr07)]
- External data: Distance 158.7±1.2 pc  
  > "the distance of 158.7$\pm$1.2 pc (cite: bailer-jones+18)" (Introduction) [from (cite: bailer-jones+18)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline following ALMA calibration scripts  
  > "Data calibration was performed using the Common Astronomy Software Applications (CASA) pipeline version 4.7.0 (cite: mcmu07) according to the steps shown in the calibration scripts provided by ALMA." (2.2 Data Reduction)
- casa version: 4.7.0  
  > "CASA) pipeline version 4.7.0" (2.2 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (also bandpass)  
  > "The quasar J0510$+$1800 was observed for bandpass and flux calibration" (2.1 Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-calibration; amplitude not used  
  > "We used only phase self-calibration because the signal-to-noise (S/N) ratio remained nearly unchanged by the amplitude calibration." (2.2 Data Reduction)

### Imaging

- task: CLEAN algorithm  
  > "generated from line-free spectral windows by using the `CLEAN` algorithm (cite: rau11)" (2.2 Data Reduction)
- deconvolver: _not stated_
- weighting robust: superuniform weighting  
  > "The left panel of Figure [1](#fig_finimg) shows the `CLEAN`ed image with “superuniform” weighting." (2.2 Data Reduction)
- uv taper: uvtaper to circular 0.29" x 0.28" beam  
  > "we generated the `CLEAN`ed image with a circular beam size of 0.29$''$ $\times$ 0.28$''$ using `uvtaper` in the CASA tools" (2.2 Data Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: ~0.17 mJy/beam (superuniform image)  
  > "its 1$\sigma$ noise is $\sim$0.17 mJy beam$^{-1}$" (2.2 Data Reduction)

### Inherited from earlier work

- Visibility deprojection in the uv plane using equations of Zhang et al.  
  > "using the following equations (cite: zhan16)" (2.2 Data Reduction) [from (cite: zhan16)]
- Dust temperature exponent q = 1/2  
  > "we adopted $q = 1/2$, as suggested by (cite: andr07)" (3 Disk modeling) [from (cite: andr07)]
- Calibration steps from ALMA-provided scripts  
  > "according to the steps shown in the calibration scripts provided by ALMA" (2.2 Data Reduction) [from ALMA calibration scripts]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters (cell, image size, mask, threshold, niter, uvtaper value)
- Which spectral windows were line-free and any channel flagging
- Self-calibration solution intervals
- MCMC initial walker positions and likelihood form/uncertainties
- Dust opacity and aspect-ratio derivation (h/r=0.122) details
- Number of azimuthal bins/radial bins in the visibility profile

## Analysis recipe

1. **Image continuum and measure geometry**: CLEAN continuum image, tapered to a circular beam; fit ellipse to 20σ contour with orthogonal distance regression  
  > "We fitted the 20$\sigma$-contour level of the `CLEAN`ed image with an elliptical shape using orthogonal distance regression, obtaining values of $i=$44.6$^{\circ}$ and $PA=$11.8$^{\circ}$" (2.2 Data Reduction)
   - software: CASA
   - parameter: i=44.6 deg, PA=11.8 deg  
  > "obtaining values of $i=$44.6$^{\circ}$ and $PA=$11.8$^{\circ}$" (2.2 Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Radial surface brightness and brightness temperature profile**: Deproject visibilities in uv plane, image, average azimuthally; Planck function for brightness temperature  
  > "we calculated the surface brightness profile by averaging the deprojected image azimuthally" (2.2 Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit gapped disk model to visibilities**: Exponentially tapered power-law brightness profile with gap; model image converted to visibilities with vis_sample; MCMC fit to azimuthally averaged deprojected visibilities  
  > "we used the Markov Chain Monte Carlo (MCMC) method to fit our disk model to the radial profile of observed complex visibilities, using the emcee package" (3 Disk modeling)
   - software: vis_sample, emcee
   - parameter: 6 free parameters: gamma, R_gap_in, R_gap_out, delta, R_c, F_total; 100 walkers, 1000 iterations, 500 burn-in  
  > "we excluded 500 steps as the burn-in phase and then, ran 1000 iterations with 100 walkers for convergence" (3 Disk modeling)
   - assumption: Optically thin emission, I ∝ T_d τ; q=1/2; fixed i and PA from the image  
  > "thermal emissions from dust grains in the CI Tau disk are optically thin" (3 Disk modeling)
   - fitting: emcee with flat priors; reduced chi2 ~4.7  
  > "We used flat prior distributions for each parameter." (3 Disk modeling)
   - validation: Corner map showed no locally concentrated regions  
  > "We confirmed that there are no locally concentrated regions for our MCMC sampling" (3 Disk modeling)
4. **Estimate planet mass from gap**: Empirical gap-opening formulas with aspect ratio 0.122 and alpha=1e-3 or 1e-4  
  > "Using the estimated aspect ratio of 0.122 and empirical formulas for gap-opening induced by a planet (cite: kanagawa+2015; kanagawa+2016)" (4 Discussion)
   - assumption: alpha = 1e-3 and 1e-4  
  > "where we consider $\alpha = 10^{-3}$ and $10^{-4}$ as the strength of turbulent viscosity" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: Calibration pipeline, CLEAN imaging, uvtaper  
  > "CASA) pipeline version 4.7.0" (2.2 Data Reduction)
- **vis_sample** : Convert model image to complex visibilities  
  > "The modeled image was converted to complex visibilities using the public Python code vis_sample" (3 Disk modeling)
- **emcee** : MCMC fitting  
  > "using the emcee package (cite: foreman-mackey+2013)" (3 Disk modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gap location (deprojected radius) | 104.5 | ±1.6 | au | 3 | the gap is located at a deprojected radius of 104.5$\pm$1.6 au |
| Gap width | 36.9 | ±2.9 | au | 3 | has a width of 36.9$\pm$2.9 au |
| Gap depth | 0.41 | +0.04/-0.06 | dimensionless | 3 | gap width and depth (0.41$^{+0.04}_{-0.06}$) |
| Brightness temperature drop at gap | ~2.3 | not stated | K | 3 | The brightness temperature around the gap was calculated to be $\sim$2.3 K lower than that of the ambient disk. |
| Total flux density F_total | 140.6 | ±0.6 | mJy | 3 | 140.6$^{+0.6}_{-0.6}$ |
| Inclination | 44.6 | not stated | deg | 1 | obtaining values of $i=$44.6$^{\circ}$ |
| Planet mass from gap | 0.25–0.8 | not stated | M_Jupiter | 4 | we find the mass of a planet to be 0.8 $M_{\rm Jupiter}$ and 0.25 $M_{\rm Jupiter}$ |

## Qualitative findings

- Gap eccentricity of ~0.46 was found but considered likely overestimated due to low S/N; gap treated as circular  
  > "However, the low S/N ratio of 1.3 mm dust continuum observations may overestimate the gap eccentricity." (2.2 Data Reduction)

## Claim tuples

- H: CI Tau's disk contains a gap | E: Visibility fitting of an axisymmetric gapped model to ALMA 1.3 mm data | R: Gap at 104.5±1.6 au, width 36.9±2.9 au, depth 0.41 | F: A gap exists in the CI Tau disk | **supported**
- H: A distant planet could have opened the gap | E: Gap-opening formulas for alpha 1e-3 and 1e-4 | R: Planet mass 0.25–0.8 MJ, below direct imaging limits | F: A planet cannot be ruled out, though coexistence with the eccentric hot Jupiter challenges scattering scenarios | **partially**
- H: Non-planetary mechanisms explain the gap | E: Qualitative comparison with snow-line, thermal wave, MRI and secular GI | R: Snow-line and thermal waves disfavored; MRI/GI/dust trapping possible | F: Dust trapping and secular GI can explain the gap | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Snow-line dust pile-up rejected because the gap lies beyond the CO, CH4, N2 snow lines  
  > "Thus, the growth and concentration of dust aggregates near the snow line could not explain formation of the observed gap in the disk around CI Tau." (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Planet mass from gas formulas applied to dust surface density needs caution  
  > "we should take some cautions to interpret the derived planet mass when such gas surface density formulas are applied to dust surface density" (4 Discussion)
- Caveat (inferred, ours): Reduced chi2 ~4.7 indicates poor fit; uncertainties likely underestimated
- Caveat (inferred, ours): Beam comparable to gap size; model-dependent gap parameters
- Caveat (inferred, ours): Short 18 min integration, low S/N
- Caveat (inferred, ours): Optically thin and fixed q assumptions
- Caveat (inferred, ours): Gap in the profile is not independently confirmed with a higher-resolution observation

## Reproducibility

- Data public (paper): Data publicly available in the ALMA archive  
  > "which are publicly available from the ALMA data archive" (Introduction)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Exact clean parameters
- Missing: MCMC likelihood details and initial conditions
- Missing: Radial binning of visibilities
- Data volume (inferred): ~10-30 GB raw single execution block
- Score (inferred): 3/5, Public data and a clear model/MCMC setup, but imaging parameters and likelihood details are missing.
- Rediscovery candidate: yes, Public data, a clear modelling recipe and numeric results (gap radius, width, depth) allow reproduction.

## Links

- Method: Zhang et al. 2016 (cite: zhan16) (visibility deprojection)
- Method: Foreman-Mackey et al. 2013 (cite: foreman-mackey+2013) (emcee)
- Companion: Andrews & Williams 2007 (cite: andr07) (previous submillimeter continuum and SED, temperature profile)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 42,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
