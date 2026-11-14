# On the Commonality of 10-30 AU Sized Axisymmetric Dust Structures in Protoplanetary Disks

`2016ApJ...818L..16Z` | The Astrophysical Journal Letters 2016 | first author: Zhang, Ke | arXiv: 1601.05182 | DOI: 10.3847/2041-8205/818/1/L16

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Do the highest-resolution ALMA (sub)mm continuum observations of four disks show common 10-30 AU axisymmetric dust structures, and do they relate to CO snowlines?  
  > "Here we investigate the commonality of 10-30 AU-sized dust structures in a modest sample of four protoplanetary disks with the highest spatial resolution (sub)mm continuum observations to date." (1 Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance 54 pc  
  > "TW Hya | 54 | 0.55 | 0.23 | 4$\times$10$^{-10}$ | 7 | 355 | 17-23 | 1,2,3,4" (Table 1); distance from _not stated_
- Target **DM Tau**: coordinates _not stated_; z/distance 145 pc  
  > "DM Tau | 145 | 0.5 | 0.25 | 2$\times$10$^{-9}$ | 35 | 155 | 70$\pm$10 | 5,6" (Table 1); distance from _not stated_
- Target **HD 163296**: coordinates _not stated_; z/distance 122 pc  
  > "HD 163296 | 122 | 2.3 | 27.2 | 7.6$\times$10$^{-8}$ | 224 | 312 | 90$^{+8}_{-6}$ | 7,8" (Table 1); distance from _not stated_
- Target **HL Tau**: coordinates _not stated_; z/distance 145 pc  
  > "HL Tau | 145 | 1.3 | — | 1$\times$10$^{-6}$ | 46.7 | 138 | 63$\pm$10 | 9" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00198.S, 2013.1.01268.S, 2011.0.00015.SV
- bands: _not stated_
- frequencies and spectral setup: TW Hya 349 and 661 GHz; DM Tau 329 GHz; HD 163296 233 GHz; HL Tau 233 GHz  
  > "| TW Hya | 349 | 2.938 | 29.0 | 0.28$\times$0.28 (-10) | 25-913 | 1415 | 0.096 | 6/15/2015 |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 12-11843 kλ for HL Tau; others about 700 kλ max  
  > "The baselines are generally $\sim$700 k$\lambda$, except that those for HL Tau extend to $\sim$12,000 k$\lambda$." (2 Observations and Results)
- angular resolution: HL Tau 0.035x0.022 arcsec; TW Hya 0.28 arcsec (349 GHz)  
  > "| HL Tau | 233 | 8 | 280.2 | 0.035$\times$0.022(11) | 12-11843 | 744 | 0.01 | 10/24-31/2014 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: TW Hya 29.0 and 39.9 min; DM Tau 7.7; HD 163296 154.5; HL Tau 280.2 min  
  > "| DM Tau | 329 | 2.234 | 7.7 | 0.41$\times$0.33(24.9) | 24-861 | 191 | 0.191 | 6/14/2015 |" (Table 1)
- observing dates: _not stated_
- pi or archival as stated: HL Tau is public data (ALMA Partnership 2015) used as test case  
  > "Here we mainly use the public data on HL Tau (cite: Partnership15) as a test case for our data analysis methodology." (2 Observations and Results)
- External data: CO snowline radii for TW Hya and HD 163296 from N2H+/C18O  
  > "where R$_{\rm CO}$=90$^{+8}_{-6}$ AU ((cite: Qi15))" (3.3 Correlation between CO snowlines and enhanced continuum emission) [from Qi13; Qi15; Schwarz et al. submitted]
- External data: CO snowline radii for HL Tau (63±10 AU) and DM Tau (70±10 AU) from radiative transfer models  
  > "R$_{\rm CO\ clatherate}$ = 63$\pm$10 AU for HL Tau (cite: Menshchikov99; Zhang15) and R$_{\rm CO }$ = 70$\pm$10 AU for DM Tau (Bergin, in prep)." (3.3 Correlation between CO snowlines and enhanced continuum emission) [from Menshchikov99; Zhang15; Bergin in prep]

## Processing

### Calibration

- pipeline or manual: CASA scripts provided by ALMA staff  
  > "All visibility data were calibrated in CASA (version 4.2) using scripts provided by the ALMA staff." (2 Observations and Results)
- casa version: CASA 4.2  
  > "All visibility data were calibrated in CASA (version 4.2)" (2 Observations and Results)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "The absolute uncertainty of the flux calibration is $\sim$10%." (2 Observations and Results)
- self calibration: iterative phase and amplitude self-calibration on continuum  
  > "We performed iterative self-calibration on both the continuum emission phase and amplitude to reduce the atmospheric decoherence." (2 Observations and Results)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "deconvolved through the CLEAN algorithm using uniform weighting, and restored with a synthesized Gaussian beam" (3.3 Image approach)
- uv taper: _not stated_
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
- final rms: _not stated_

### Inherited from earlier work

- HL Tau data and calibration from ALMA Partnership  
  > "Here we mainly use the public data on HL Tau (cite: Partnership15) as a test case" (2 Observations and Results) [from Partnership15]
- HD 163296 data described elsewhere  
  > "those on HD 163296 were obtained in project 2013.1.01268.S (Salinas et al., in prep)" (2 Observations and Results) [from Salinas et al., in prep]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (cell, image size, masks, iterations, threshold)
- self-calibration solution intervals and number of iterations
- number of Gaussian components and best-fit parameter values per disk
- fit uncertainty estimation method
- how inclination/PA values were chosen for deprojection (HD 163296 incl listed as 224)
- visibility binning in deprojected annuli
- calibrator details

## Analysis recipe

1. **Calibrate and self-calibrate**: CASA 4.2 ALMA scripts plus iterative phase and amplitude self-cal  
  > "We performed iterative self-calibration on both the continuum emission phase and amplitude to reduce the atmospheric decoherence." (2 Observations and Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Deprojected visibility profiles**: Deproject uv with inclination and PA and plot against deprojected baseline; check imaginary part is flat for axisymmetry  
  > "as also suggested by the flat distribution of their imaginary visibility components as a function of deprojected $uv$-distance." (2 Observations and Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit radial brightness with Gaussians modulated by cosines**: Hankel transform of I(theta) = central Gaussian + sum of cosine-modulated Gaussians fit to visibilities; number of Gaussians set by number of visibility peaks; optional inner cavity with R_cav and depletion delta for HD 163296 and DM Tau  
  > "The number of Gaussians is decided by the number of distinctive peaks in the visibility profile" (3.2 Model fitting approach)
   - parameter: _not stated_
   - assumption: flat intensity inside the cavity  
  > "We assume the source intensity is flat inside the cavity since fine structures inside 20 AU are unresolved." (3.2 Model fitting approach)
   - fitting: Levenberg-Marquardt chi2 minimization; initial rho_i at visibility peak centers  
  > "We use the Levenberg-Marquardt $\chi^2$ minimization algorithm to search for the optimal value of free parameters." (3.2 Model fitting approach)
   - validation: HL Tau fit with truncated uv range compared with CLEAN image of full baselines  
  > "the three major gaps (13, 32 and 63 AU) are reproduced nicely by the model fitting approach using the $\rho\le 2000$ k$\lambda$ data" (3.3 Image approach)
4. **CLEAN image radial profiles**: Deproject visibilities, CLEAN with uniform weighting, azimuthally average  
  > "We then derive an azimuthally averaged $I(\theta)$ from the images." (3.3 Image approach)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with model-fit profiles  
  > "Consistent results are found over larger scales" (3.4 Results)
5. **Compare structures with CO snowlines**: Overplot literature midplane CO snowline radii on brightness profiles  
  > "Figure 3 presents the mid-plane CO snowline locations on top of the surface brightness distributions in the four disks." (3.3 Correlation between CO snowlines and enhanced continuum emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2: Calibration, self-calibration and CLEAN imaging  
  > "All visibility data were calibrated in CASA (version 4.2) using scripts provided by the ALMA staff." (2 Observations and Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HL Tau gap radii | 13, 32, 63 | not stated | AU | 3 | For HL Tau, its known major gaps at 13, 32 and 63 AU are well recovered. |
| HD 163296 depressed zones | 55 and 100 | not stated | AU | 3 | HD 163296 has two depressed zones centered near 55 and 100 AU |
| DM Tau depressed zone | 70 | not stated | AU | 3 | DM Tau has a shallowly depressed emission zone around 70 AU |
| TW Hya slope turning point | 25 | not stated | AU | 3 | has a turning point in the slope around 25 AU, followed by a plateau |

## Qualitative findings

- All four disks are approximately axisymmetric with 10-30 AU radial structures  
  > "the continuum emission of the four disks is $\sim$axi-symmetric but rich in 10-30 AU-sized radial structures" (abstract)

## Claim tuples

- H: Small-scale axisymmetric dust structures are common in disks | E: Visibility fitting and CLEAN profiles of four high-resolution disks | R: All four show 10-30 AU structures | F: Such structures are likely common | **supported**
- H: Continuum enhancements relate to CO snowlines | E: Overplot snowline radii on brightness profiles | R: Enhanced emission just beyond snowlines in all four | F: Possible causal link between snowlines and dust growth/trapping | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: No physical model for mm-dust surface density, so empirical approach  
  > "Due to these uncertainties, we employ an empirical approach to characterize spatial structures in the surface brightness distributions" (3 Modeling)
- Alternative: Tapered edge, sharp edge, and sharp cavity models fail to reproduce visibility features  
  > "These discrepancies suggest that a sharp truncation alone cannot fit the data" (2 Observations and Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Deconvolution solution is not unique  
  > "our proposed solutions are consistent with the data but other disk structures may also be possible." (3.4 Results)
- Caveat (inferred, ours): Only four disks, so commonality is weakly supported
- Caveat (inferred, ours): No uncertainties on fitted structures
- Caveat (inferred, ours): Snowline correlation is qualitative with two model-based snowline radii
- Caveat (inferred, ours): Number of Gaussians subjectively chosen

## Reproducibility

- Data public (paper): HL Tau public; others cited by project code  
  > "Here we mainly use the public data on HL Tau (cite: Partnership15) as a test case" (2 Observations and Results)
- Products in archive: _not stated_
- Missing: fitted parameter values
- Missing: CLEAN settings
- Missing: self-cal parameters
- Data volume (inferred): ~hundreds of GB (HL Tau long baseline dominates)
- Score (inferred): 4/5, Method equations given and data are archival, but fit parameters and imaging settings are missing.
- Rediscovery candidate: no, Recipe incomplete; results mostly radii read from profiles, not tabulated.

## Links

- Method: Pearson99 (Hankel transform and model fitting of visibilities)
- Companion: Partnership15 (HL Tau ALMA data)
- Companion: Zhang15 (snowline origin of HL Tau rings)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 34,
  "rate": 0.442
 },
 "evidence_ok": true
}
```
