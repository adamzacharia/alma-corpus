# Core Emergence in a Massive Infrared Dark Cloud: A Comparison between Mid-IR Extinction and 1.3 mm Emission

`2018ApJ...855L..25K` | The Astrophysical Journal Letters 2018 | first author: Kong, Shuo | arXiv: 1802.07376 | DOI: 10.3847/2041-8213/aab151

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How does the presence of 1.3 mm continuum emitting dense structures (cores) depend on the local mass surface density from MIR extinction in IRDC G28.37+0.07, and what dense gas fraction and star formation efficiency per free-fall time follow?  
  > "we study the relationship between mm continuum emitting dense gas structures and the local mass surface density of their hosting cloud to better understand the conditions of core formation." (Introduction)
- Target **IRDC G28.37+0.07 (IRDC C)**: coordinates _not stated_; z/distance 5 kpc  
  > "Our target cloud is IRDC G28.37+0.07 (also referred to as IRDC C) from the sample of (cite: 2009ApJ...696..484B; 2012ApJ...754....5B) at an estimated kinematic distance of 5 kpc." (Introduction); distance from kinematic distance  
  > "Our target cloud is IRDC G28.37+0.07 (also referred to as IRDC C) from the sample of (cite: 2009ApJ...696..484B; 2012ApJ...754....5B) at an estimated kinematic distance of 5 kpc." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00183.S
- bands: Band 6 (~231 GHz)  
  > "The observations were in band 6 ($\sim$ 231 GHz)." (2.1 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 1.8 GHz baseband; effective ~1.4 GHz after excluding 12CO(2-1)  
  > "the effective bandwidth for continuum imaging is $\sim1.4\:$GHz due to the exclusion of the $^{12}$CO(2-1) molecular line" (2.1 ALMA Observations)
- arrays: 12-m array, 46 antennas, 86-pointing mosaic  
  > "Forty-six 12-m antennas were used during the observation in C40-4 configuration." (2.1 ALMA Observations)
- configurations: C40-4  
  > "Forty-six 12-m antennas were used during the observation in C40-4 configuration." (2.1 ALMA Observations)
- baselines: _not stated_
- angular resolution: 2'' after uv-taper (matched to MIREX)  
  > "we applied an outer uv-taper to match the ALMA synthesized beam to the MIREX beam (2$''$)" (2.1 ALMA Observations)
- max recoverable scale: ~20'' (shortest baseline 10 kλ)  
  > "The maximum recoverable scale of the ALMA continuum image is $\sim$20$''$" (2.1 ALMA Observations)
- sensitivity: 0.2 mJy per 2'' beam at map center  
  > "The resulting sensitivity at map center is $\sigma_{\rm center}=$ 0.2 mJy per 2$''$ beam." (2.1 ALMA Observations)
- time on source: 6 scheduling blocks, ~50 min on-source each  
  > "The observations consist of 6 scheduling blocks, each having roughly 50 minutes on-source integration time." (2.1 ALMA Observations)
- observing dates: 24-Jun-2016 to 30-Jun-2016 (Cycle 3)  
  > "The observations were carried out between 24-Jun-2016 and 30-Jun-2016 (UTC)" (2.1 ALMA Observations)
- pi or archival as stated: PI: Kong, project 2015.1.00183.S  
  > "under the project 2015.1.00183.S (PI: Kong)" (2.1 ALMA Observations)
- Other facility **Spitzer IRAC/GLIMPSE**: 8 micron imaging used to build the MIREX mass surface density map  
  > "using Spitzer 8 $\rm \mu m$ GLIMPSE imaging data" (2.2 The MIREX image)
- External data: MIREX mass surface density map of the IRDC (NIR-merged, refined with deeper Spitzer-IRAC)  
  > "Finally, the map was refined by (cite: 2014ApJ...782L..30B) by using an analysis of deeper archival *Spitzer*-IRAC imaging" (2.2 The MIREX image) [from (cite: 2014ApJ...782L..30B)]
- External data: Sigma-PDF log-normal parameters (sigma_lnSigma=1.15, mean ln Sigma=-3.93)  
  > "with $\sigma_{\rm ln\Sigma}$ = 1.15, $\overline{\rm \Sigma}$ = 0.038 $\rm g~cm^{-2}$, and $\overline{\rm
  ln\Sigma}$ = -3.93" (3.3 Dense Gas Fraction) [from (cite: 2014ApJ...782L..30B; 2016ApJ...829L..19L)]
- External data: Dust opacity kappa = 5.95e-3 cm2/g at 1.3 mm  
  > "$\kappa_\nu = 5.95\times 10^{-3}\:{\rm cm^2\:g^{-1}}$ (cite: 1994A&A...291..943O)" (3.1 Comparison) [from (cite: 1994A&A...291..943O)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+0939, J1924-2914, Titan  
  > "J1751+0939, J1924-2914, and Titan were used as flux calibrators." (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: No self-calibration  
  > "No self-calibration was done." (2.1 ALMA Observations)

### Imaging

- task: CASA clean  
  > "The mosaic image was cleaned using the standard *clean* task in CASA." (2.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust number of 0.5 was applied." (2.1 ALMA Observations)
- uv taper: outer uv-taper to give 2'' beam  
  > "we applied an outer uv-taper to match the ALMA synthesized beam to the MIREX beam (2$''$)" (2.1 ALMA Observations)
- cell size: 0.4'' in clean, rebinned to 1.2'' pixels  
  > "A pixel scale of 0.4$''$ was adopted in the *clean* task. Then we re-binned the images to have 1.2$''$ pixels" (2.1 ALMA Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied; analysis restricted to PB response >= 0.5  
  > "The continuum image is primary-beam corrected, so the map boundary regions have higher noise levels." (3.1 Comparison)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.2 mJy per 2'' beam at center  
  > "The resulting sensitivity at map center is $\sigma_{\rm center}=$ 0.2 mJy per 2$''$ beam." (2.1 ALMA Observations)

### Inherited from earlier work

- MIREX map construction and dust opacity/dust-to-gas assumptions  
  > "The MIR extinction (MIREX) map of IRDC G28.37+0.07 was first developed by BT09 and BT12" (2.2 The MIREX image) [from BT09, BT12 (cite: 2009ApJ...696..484B; 2012ApJ...754....5B); BTK14 (cite: 2014ApJ...782L..30B)]
- Mass conversion of continuum noise to Sigma_mm = 0.044 g/cm2  
  > "$\Sigma_{\rm
  mm}$ = 0.044 g cm$^{-2}$ (cite: 2017arXiv170105953K), assuming a dust temperature of 20 K" (3.1 Comparison) [from (cite: 2017arXiv170105953K)]
- Star formation timescale from Turbulent Core Model  
  > "(cf. equation 44 in MT03)" (4.2 Star Formation Rates) [from MT03 (cite: 2003ApJ...585..850M)]

### Not stated but needed to reproduce (our reading)

- Clean threshold, number of iterations and masks
- Exact uv-taper parameters
- Calibration pipeline/CASA version
- Which pixels were flagged as MIR-bright sources (visual list)
- Rebinning and regridding procedure to MIREX grid
- Mosaic phase centers/coordinates

## Analysis recipe

1. **Image the 1.3 mm continuum mosaic matched to MIREX**: CASA clean, Briggs weighting, outer uv-taper to 2'' beam, rebin to 1.2'' pixels  
  > "Briggs weighting with a robust number of 0.5 was applied." (2.1 ALMA Observations)
   - software: CASA
   - parameter: robust 0.5; 0.4'' pixels rebinned to 1.2''  
  > "A pixel scale of 0.4$''$ was adopted in the *clean* task." (2.1 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Pixel-by-pixel comparison of continuum with MIREX Sigma**: Compare SNR and flux density versus Sigma where PB response >= 0.5; remove MIR-bright source pixels  
  > "Both comparisons are restricted to regions where the ALMA primary-beam response $\geq$0.5." (3.1 Comparison)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive detection probability function**: P = N_detection/N_total per Sigma bin (0.02 g/cm2), Bernoulli errors, power-law fit a*Sigma^b over 0.15-0.65 g/cm2  
  > "We fit the function $P_{\rm 1.3mm}=a(\Sigma / 1\:\rm g~cm^{-2})^b$ by minimizing $\chi^2$ (normalized by the errors)" (3.2 Dense Gas Detection Probability Function)
   - parameter: thresholds SNR 2,3,4 and flux 2,3,4 sigma_center; P=1 points excluded from fit  
  > "We adopt a fiducial threshold of SNR = 3, and show the effects from using SNR = 2 and SNR = 4." (3.2 Dense Gas Detection Probability Function)
   - fitting: chi-square minimization, errors sqrt(p(1-p)/n)  
  > "The standard deviation of $\sum_{i=1}^{n}X_i/n$ is $[p(1-p)/n]^{0.5}$, which is adopted as the error bar for each bin." (3.2 Dense Gas Detection Probability Function)
   - validation: _not stated_
4. **Estimate dense gas mass fractions**: Direct mm mass, MIREX mass of detected pixels, and DPF integrated with lognormal Sigma-PDF (inner IRDC and GMC)  
  > "Then the mass of dense, i.e., 1.3mm-emitting, gas is" (3.3 Dense Gas Fraction)
   - assumption: T=20 K (15-30 K range), kappa=5.95e-3 cm2/g, dust-to-gas 1:141, mean particle mass 2.33 mH  
  > "assuming a dust temperature of 20 K, $\kappa_\nu = 5.95\times 10^{-3}\:{\rm cm^2\:g^{-1}}$" (3.1 Comparison)
   - fitting: _not stated_
   - validation: f_dg,DPF,0.15-0.65 compared with f_dg,MIREX  
  > "very similar to the values of $f_{\rm dg,MIREX}$ (also compare other values in columns 6 and 7), which indicates that the analytic approximations for the DPF are quite accurate." (4.1 Core/Star Formation Efficiency)
5. **Estimate star formation efficiency per free-fall time**: Turbulent Core Model: t_*f/t_ff = 0.42 for Mc=5 Msun, M_cl=1e4 Msun; eps_ff from f_dg and eps_core  
  > "Under these two conditions, $t_{*f}/\bar{t}_{\rm
  ff,cl}\rightarrow0.42$." (4.2 Star Formation Rates)
   - assumption: eps_core = 0.5; steady SFR; Salpeter CMF 1-240 Msun; mm continuum is complete protostellar core census  
  > "Assuming the SFR is steady and the CMF is evenly populated" (4.2 Star Formation Rates)
   - fitting: _not stated_
   - validation: compared with Orion Nebula Cluster eps_ff  
  > "about a factor of two larger than the value estimate inside the half-mass radius of the Orion Nebula Cluster" (4.2 Star Formation Rates)

## Software

- **CASA** : cleaning the mosaic continuum image with clean  
  > "The mosaic image was cleaned using the standard *clean* task in CASA." (2.1 ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| continuum sensitivity at map center | 0.2 | not stated | mJy per 2'' beam | 1 | $\sigma_{\rm center}=$ 0.2 mJy per 2$''$ beam |
| DPF power-law index b (SNR>=3) | 3.3 | not stated | dimensionless | 3 | SNR$\geq$3 / 0.044 / 4.6 / 3.3 |
| DPF power-law index b (F>=3 sigma_center) | 2.6 | not stated | dimensionless | 3 | $F_{\rm 1.3mm}\geq3\sigma_{\rm center}$ / 0.044 / 3.1 / 2.6 |
| total mm flux in analyzed region (>3 sigma_center) | 1.42 | not stated | Jy | 4 | is 1.42 Jy (based on detections above $3\sigma_{\rm center}$) |
| mm-derived dense gas mass | 1.16e3 | not stated | Msun | 4 | which translates into a total mass of $1.16\times10^3\:M_\odot$ |
| total MIREX mass in mapped region | 1.21e4 | ~30% | Msun | 4 | this mass is $1.21\times10^4\:M_\odot$, with uncertainties at the level of about 30% |
| f_dg,mm (F>=3 sigma_center) | 9.5% | +4.5/-3.7 % (14% at 30 K, 5.8% at 15 K as quoted) | percent | 4 | Thus the direct measure of dense gas mass fraction (expressed as percentages) is $f_{\rm dg,mm}= 9.5\%$ for this case. |
| f_dg,DPF,GMC (fiducial) | 6.5% to 8.2% | not stated | percent | 4 | SNR$\geq$3 / 0.044 / 4.6 / 3.3 / 8.7%$_{5.3\%}^{13\%}$ / 13% / 12% / 6.5% |
| total GMC-scale cloud mass | 170000 | not stated | Msun | 4 | which has a value of 170,000$\:M_\odot$ |
| star formation efficiency per free-fall time | 0.11 | +0.06/-0.041 (0.17 and 0.069 quoted) | dimensionless | 5 | $\epsilon_{\rm
  ff}=0.11^{0.17}_{0.069}$ |

## Qualitative findings

- Being in a high-Sigma region is a necessary but not sufficient condition for strong mm continuum cores; detection is near 100% for Sigma >~ 0.65 g/cm2.  
  > "Being in a high-$\Sigma$ region is a necessary, but not sufficient, condition for the presence of strong mm continuum cores." (3.1 Comparison)

## Claim tuples

- H: Does 1.3 mm core detection depend on local cloud mass surface density? | E: Pixel-by-pixel comparison of ALMA continuum with MIREX Sigma; fit detection probability function | R: P rises as a power law with b~3 between 0.15 and 0.65 g/cm2, reaching ~1 above | F: Core formation is more likely in high-Sigma regions | **supported**
- H: What fraction of the IRDC mass is dense gas? | E: Direct mm mass, MIREX mass of detections, and DPF integration | R: f_dg ~5-15% in IRDC, ~7-8% extrapolated to GMC | F: Dense gas fraction is ~10% in the central IRDC region | **supported**
- H: What is the star formation efficiency per free-fall time in the IRDC? | E: Combine f_dg with Turbulent Core Model and eps_core = 0.5 | R: eps_ff ~ 0.11 | F: eps_ff ~10% with factor-of-two systematics | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Interferometers resolve out extended emission, so mm continuum pinpoints dense cores; continuum is independent of chemical abundance variations.  
  > "mm continuum emission can potentially pinpoint dense, star-forming cores embedded in a molecular cloud because the extended emission is resolved out by interferometers." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust temperature assumption is the largest uncertainty (up to factor ~2); MIREX has zero-point offsets, saturation and MIR-source contamination.  
  > "Systematic variations arising from the choice of dust temperature are up to a factor of almost two and are the most significant source of uncertainty" (3.3 Dense Gas Fraction)
- Caveat (inferred, ours): Mm continuum assumed to be a complete census of protostellar cores without outflow confirmation
- Caveat (inferred, ours): Single uniform dust temperature applied across all structures
- Caveat (inferred, ours): Extrapolation of the inner-IRDC DPF to the 30 pc GMC is untested
- Caveat (inferred, ours): Visual identification of MIR-bright sources is subjective

## Reproducibility

- Data public (paper): ALMA data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00183.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: MIREX map file
- Missing: list of masked MIR-bright pixels
- Missing: clean parameters beyond robust and taper
- Data volume (inferred): ~100-300 GB raw for 6 SBs of an 86-pointing mosaic
- Score (inferred): 3/5, Recipe is clear and results are numeric, but the MIREX map and masks are external and some imaging details are missing.
- Rediscovery candidate: no, The MIREX map and the MIR-source pixel mask are not provided, and key imaging parameters are not stated.

## Links

- Method: (cite: 2014ApJ...782L..30B) (MIREX map with deep Spitzer-IRAC data)
- Companion: (cite: 2017arXiv170105953K) (C1 region continuum cores and mass conversion)
- Related: Spitzer GLIMPSE

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 45,
  "rate": 0.625
 },
 "evidence_ok": true
}
```
