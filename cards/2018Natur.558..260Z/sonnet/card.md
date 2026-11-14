# Stellar populations dominated by massive stars in dusty starburst galaxies across cosmic time

`2018Natur.558..260Z` | Nature 2018 | first author: Zhang, Zhi-Yu | arXiv: 1806.01280 | DOI: 10.1038/s41586-018-0196-x

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, astrochemistry
- Question: Is the stellar initial mass function in dusty starburst galaxies at z~2-3 top-heavy, as probed by 13CO/C18O line ratios?  
  > "find unambiguous evidence for a top-heavy stellar initial mass function in all of them." (abstract)
- Target **SPT 0103-45**: coordinates 01:03:11.50 -45:38:53.9 (J2000)  
  > "SPT 0103−45 SPT-S J010312−4538.8 01:03:11.50 −45:38:53.9 3.0917 5.3" (Extended Data Table. 1); z/distance z = 3.0917  
  > "SPT 0103−45 SPT-S J010312−4538.8 01:03:11.50 −45:38:53.9 3.0917 5.3" (Extended Data Table. 1); distance from _not stated_
- Target **SPT 0125-47**: coordinates 01:25:07.08 -47:23:56.0 (J2000)  
  > "SPT 0125−47 SPT-S J012506−4723.7 01:25:07.08 −47:23:56.0 2.5148 5.5" (Extended Data Table. 1); z/distance z = 2.5148  
  > "SPT 0125−47 SPT-S J012506−4723.7 01:25:07.08 −47:23:56.0 2.5148 5.5" (Extended Data Table. 1); distance from _not stated_
- Target **SDP.17b**: coordinates 09:03:03.02 -01:41:26.9 (J2000)  
  > "SDP.17b HATLAS J090302.9−014127 09:03:03.02 −01:41:26.9 2.3051" (Extended Data Table. 1); z/distance z = 2.3051  
  > "SDP.17b HATLAS J090302.9−014127 09:03:03.02 −01:41:26.9 2.3051" (Extended Data Table. 1); distance from _not stated_
- Target **Cloverleaf (H1413+117)**: coordinates 14:15:46.23 +11:29:44.0 (J2000)  
  > "Cloverleaf H1413+117 14:15:46.23 +11:29:44.0 2.5585" (Extended Data Table. 1); z/distance z = 2.5585  
  > "Cloverleaf H1413+117 14:15:46.23 +11:29:44.0 2.5585" (Extended Data Table. 1); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01309.S, 2013.1.00164.S, 2011.0.00958.S, 2011.0.00747.S
- bands: Bands 3 and 4  
  > "with two 2-GHz-wide spectral windows (SPWs) in bands 3 and 4." (2 Observations and data reduction)
- frequencies and spectral setup: two 2-GHz SPWs for 13CO/C18O, two SPWs for continuum  
  > "We used the remaining two SPWs to cover continuum emission." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-1 and C36-2  
  > "relatively compact array configurations (C36-1 and C36-2)" (2 Observations and data reduction)
- baselines: _not stated_
- angular resolution: ~2.5-3.7 arcsec x 1.6-2.5 arcsec  
  > "Angular Resolution 2.5 ′′ ×1.8 ′′ 2.7 ′′ ×1.6 ′′ 3.6 ′′ ×2.5 ′′ 2.5 ′′ ×1.8 ′′ 3.1 ′′ ×2.3 ′′ 2.7 ′′ ×1.8 ′′ 3.7 ′′ ×2.0 ′′" (Extended Data Table. 2)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 10-30 min per transition  
  > "Between 10 and 30 min were spent on target for each transition." (2 Observations and data reduction)
- observing dates: 16-21 Jan 2016 and 8 Apr 2016  
  > "Observing Date 21-Jan-2016 21-Jan-2016 21-Jan-2016 21-Jan-2016 17-Jan-2016 16-Jan-2016 08-Apr-2016" (Extended Data Table. 2)
- pi or archival as stated: First author is PI of the observing project  
  > "Z.-Y.Z. is the Principal Investigator of the ALMA observing project." (Author Contributions)
- Line: 13CO and C18O J=3-2, 4-3, 5-4 (target dependent) (not stated)
- Line: 12CO J=5-4 (SPT 0103-45), J=4-3 (SPT 0125-47) (not stated)
- Other facility **ALMA archive high-resolution submm continuum**: high-resolution continuum images overlaid as contours  
  > "overlaid with contours of highresolution submm continuum." (2 Observations and data reduction)
- External data: Lensing amplification factors, LIR and M* for targets  
  > "Data for SDP.17b is from ref. [73,74] ." (Extended Data Table. 1) [from refs 71-75]
- External data: Literature 12CO line data  
  > "Literature data are from refs [32,78,79] ." (Extended Data Table. 3) [from refs 32, 78, 79]
- External data: Comparison I(13CO)/I(C18O) ratios for local galaxies and SMM J2135-0102  
  > "three local ULIRGs [11], Arp 220, Mrk 231, and IRAS 13120−5453, and a SMG, SMM J2135−0102 [13] at z ≈ 2.3." (Figure 1 caption) [from refs 11-18]
- Simulation/model as data: Single-zone chemical evolution model with Bottom-heavy, Kroupa, Top-heavy and Ballero IMFs  
  > "We adopt a single-zone chemical evolution model for our analysis, originally developed to describe the evolution of the Milky Way [52]" (5 Chemical evolution model)

## Processing

### Calibration

- pipeline or manual: manual calibration with standard procedures  
  > "All the data were calibrated manually using CASA v4.7.1 [36], using standard procedures." (2 Observations and data reduction)
- casa version: CASA v4.7.1  
  > "All the data were calibrated manually using CASA v4.7.1 [36]" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune, Callisto, or quasars (J2357-5311, J0854+2006)  
  > "Flux Calibrator Neptune J2357−5311 Neptune Neptune J0854+2006 J0854+2006 Callisto" (Extended Data Table. 2)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 1.5  
  > "using a Briggs weighting with robust = 1.5 to optimise sensitivity." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, linear slope fit to line-free channels  
  > "We subtracted the continuum using the CASA task, uvcontsub, by fitting a linear slope to the line-free channels." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: applied to all cleaned data  
  > "We applied a primary beam correction to all the cleaned data." (2 Observations and data reduction)
- array combination: _not stated_
- smoothing: channel width ~20-30 km/s  
  > "We cleaned the visibility data with a channel width of ∼ 20–30 km s [−][1]" (2 Observations and data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Cell size, image size, clean masks and thresholds
- Self-calibration usage
- Aperture centres and exact sizes per source
- Flux calibrator flux scale uncertainty
- Which archive MOUS/EBs map to each target
- Chemical evolution model code and parameters (SFH timescales, inflow, outflow) for the observed targets
- Gaussian-fit procedure details and priors

## Analysis recipe

1. **Image continuum-subtracted cubes**: uvcontsub linear fit, cleaning with Briggs weighting, primary beam correction  
  > "We subtracted the continuum using the CASA task, uvcontsub, by fitting a linear slope to the line-free channels." (2 Observations and data reduction)
   - software: CASA
   - parameter: robust = 1.5; channel width ~20-30 km/s  
  > "using a Briggs weighting with robust = 1.5 to optimise sensitivity." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure velocity-integrated line fluxes**: Three methods: 1D Gaussian fit to spectra from circular apertures with fixed 12CO linewidth; 2D Gaussian fit to moment-0 maps; theoretical noise from ALMA sensitivity calculator  
  > "we first fit one-dimensional Gaussian profiles to the extracted spectra with a fixed linewidth from [12] CO, and fixed the frequency interval between [13] CO and C [18] O" (2 Observations and data reduction)
   - software: ALMA Sensitivity Calculator
   - parameter: apertures ~4-6 arcsec diameter  
  > "We extract spectra of [13] CO and C [18] O using circular apertures ≈ 4–6 [′′] in diameter" (2 Observations and data reduction)
   - assumption: 13CO and C18O linewidths equal those of 12CO  
  > "We assume that line widths of [13] CO and C [18] O are the same as those of [12] CO lines, to minimise uncertainties in the line flux fitting." (2 Observations and data reduction)
   - fitting: Gaussian fits; largest error of the three methods adopted  
  > "To be conservative, in Figs 1 and 2 we adopt the largest error among the results from the three methods in the analysis." (2 Observations and data reduction)
   - validation: Independent cross-check of three methods  
  > "Second, we made moment-0 maps and fitted two-dimensional Gaussian profiles, as an independent check of line flux." (2 Observations and data reduction)
3. **Constrain optical depths with LTE and non-LTE models**: LTE brightness-temperature ratio equations; RADEX non-LTE grids  
  > "we present non-LTE models derived with a non-LTE radiative transfer code, RADEX [40]" (3.2 Non-LTE conditions)
   - software: RADEX
   - parameter: nH2 = 1e3, 1e4, 1e5 cm-3; Tkin = 30 K; FWHM 300 km/s  
  > "The velocity width (full-width at half-maximum, fwhm) is set to 300 km s [−][1]" (3.2 Non-LTE conditions)
   - assumption: 12CO/13CO = 70, 13CO/C18O = 7 (Milky Way disk)  
  > "12 CO/ [13] CO = 70, and [13] CO/C [18] O = 7, which are representative values of the Milky Way disk." (3.2 Non-LTE conditions)
   - fitting: _not stated_
   - validation: LTE results overlaid on non-LTE for comparison  
  > "we overlay the LTE results, for comparison." (3.2 Non-LTE conditions)
4. **Assess HNCO contamination of C18O**: RADEX line ratios of HNCO to C18O with Arp 220 abundances and LAMBDA data  
  > "We assume the same abundances measured in Arp 220 [47], and use molecular data from the Leiden Atomic and Molecular Database [51] (LAMBDA)." (4 Possible HNCO contamination of C18O lines)
   - software: RADEX
   - assumption: Tkin = 30 K  
  > "We assume T kin = 30 K as the representative temperature of the H 2 gas." (4 Possible HNCO contamination of C18O lines)
   - fitting: _not stated_
   - validation: Contamination at most 3% for high-J C18O  
  > "the corresponding contamination for the high- J C18O transitions will be at most 3%" (4 Possible HNCO contamination of C18O lines)
5. **Compare line ratios with chemical evolution models for different IMFs**: Single-zone non-IRA chemical evolution model with metallicity-dependent yields, delayed starburst  
  > "Finite stellar lifetimes for different stars need to be considered (i.e. no instantaneous recycling approximation (non-IRA) is adopted)" (5 Chemical evolution model)
   - parameter: starburst starts ~z~3 (2 Gyr after Big Bang), reaches 1e11 Msun one Gyr later, then ceases  
  > "reached a stellar mass of 10 [11] M ⊙ one Gyr later, ceased forming stars after the burst, then evolved passively to the present day." (Main text)
   - assumption: Kennicutt-Schmidt law; exponentially fading primordial inflow; outflows  
  > "Star formation follows the canonical Kennicutt-Schmidt law [57]" (5 Chemical evolution model)
   - fitting: _not stated_
   - validation: Yields calibrated on Milky Way data  
  > "have been calibrated with the best fit using the Milky Way data" (5 Chemical evolution model)

## Software

- **CASA** 4.7.1: manual calibration, uvcontsub, cleaning  
  > "All the data were calibrated manually using CASA v4.7.1 [36], using standard procedures." (2 Observations and data reduction)
- **RADEX** : non-LTE line ratios, optical depths, HNCO contamination  
  > "are based on the publicly available non-LTE radiative transfer code, RADEX [40]." (Code Availability)
- **ALMA Sensitivity Calculator** : theoretical noise estimate  
  > "we also calculated the theoretical noise using the ALMA sensitivity calculator [37]" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 13CO J=5-4 flux, SPT 0103-45 (Gaussian fit) | 0.37 | 0.07 | Jy km/s | 2 | SPT 0103−45 13 CO J = 5 → 4 134.65 0.37 ± 0.07 0.38 ± 0.05 0.07 1.2 ± 0.4 |
| C18O J=5-4 flux, SPT 0103-45 | 0.35 | 0.09 | Jy km/s | 2 | SPT 0103−45 C [18] O J = 5 → 4 134.13 0.35 ± 0.09 0.39 ± 0.07 0.07 1.2 ± 0.4 |
| 13CO J=3-2 flux, SPT 0125-47 | 0.78 | 0.09 | Jy km/s | 2 | SPT 0125−47 13 CO J = 3 → 2 94.06 0.78 ± 0.09 0.86 ± 0.07 0.1 2.0 ± 0.4 |
| C18O J=3-2 flux, SPT 0125-47 | 0.63 | 0.07 | Jy km/s | 2 | SPT 0125−47 C [18] O J = 3 → 2 93.70 0.63 ± 0.07 0.71 ± 0.1 0.1 1.6 ± 0.4 |
| 13CO J=3-2 flux, Cloverleaf | 0.65 | 0.09 | Jy km/s | 2 | Cloverleaf 13 CO J = 3 → 2 92.90 0.65 ± 0.09 0.61 ± 0.06 0.07 1.4 ± 0.4 |
| C18O J=3-2 flux, Cloverleaf | 0.40 | 0.10 | Jy km/s | 2 | Cloverleaf C [18] O J = 3 → 2 92.55 0.40 ± 0.10 0.43 ± 0.06 0.07 0.8 ± 0.4 |
| 13CO J=4-3 flux, SDP.17b | 0.47 | 0.07 | Jy km/s | 2 | SDP.17b 13 CO J = 4 → 3 133.36 0.47 ± 0.07 0.46 ± 0.08 0.07 1.3 ± 0.4 |
| C18O J=4-3 flux, SDP.17b | 0.34 | 0.06 | Jy km/s | 2 | SDP.17b C [18] O J = 4 → 3 132.85 0.34 ± 0.06 0.50 ± 0.08 0.07 1.0 ± 0.4 |
| Required 13CO optical depth for observed I(12CO)/I(13CO) >= 30 (LTE) | < 0.03 | not stated | dimensionless | 3 | the optical depth for [13] CO needs to be < 0.03 |
| Maximum HNCO contamination of high-J C18O | 3 | not stated | % | 4 | the corresponding contamination for the high- J C18O transitions will be at most 3% |

## Qualitative findings

- I(13CO)/I(C18O) is close to unity in all four SMGs, decreasing with LIR  
  > "For all the galaxies in our observed sample (see Methods), the line ratios of I ( [13] CO)/ I (C [18] O) are close to unity" (Main text)
- Kroupa IMF cannot reproduce the observed ratios; top-heavy IMF required  
  > "It is not possible to reproduce the observed I ( [13] CO)/ I (C [18] O) ratio in SMGs with a Kroupa IMF" (Main text)

## Claim tuples

- H: 13CO and C18O emission is optically thin so line ratios reflect abundance ratios | E: LTE and RADEX non-LTE modelling of line ratios and optical depths | R: Unity ratio needs N_H2 >> 1e26 cm-2, orders above SMG values | F: Emission is optically thin; ratio traces 13C/18O | **supported**
- H: The IMF in z~2-3 dusty starbursts is top-heavy | E: Compare observed ratios to chemical evolution tracks for four IMFs | R: Kroupa cannot reproduce near-unity ratios | F: Top-heavy IMF operates in distant starbursts and local ULIRGs; SFRs must be reduced | **supported**

## Reasoning

- Why this data: 13CO/C18O is immune to dust effects and sensitive to the IMF  
  > "is a very sensitive index of the stellar initial mass function, with its determination immune to the pernicious effects of dust." (abstract)
- Why this method: _not stated_
- Alternative: Differential lensing, HNCO blending and high optical depth rejected as explanations for low ratios  
  > "It is unlikely that differential lensing could skew the measured I ( [13] CO)/ I (C [18] O) line ratio away from the value intrinsic to the galaxy" (Main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Some lines only marginally detected (~4 sigma)  
  > "The J = 3 → 2 line from SDP.17b and the J = 5 → 4 line from SPT 0103−45 are marginally detected at ∼ 4σ levels." (Main text)
- Limitation (authors): Uncertainty on Cloverleaf amplification not reported  
  > "Unfortunately the uncertainty of this amplification factor was not reported" (Extended Data Table. 1)
- Caveat (inferred, ours): Only four lensed sources, some marginal detections
- Caveat (inferred, ours): Model dependence on yields and assumed star formation histories
- Caveat (inferred, ours): Mix of IMFs or young starburst age not fully disentangled
- Caveat (inferred, ours): Aperture photometry on marginally resolved sources with assumed linewidths

## Reproducibility

- Data public (paper): Data in ALMA archive under four project codes  
  > "The dataset that supports the findings of this study is available in the ALMA archive" (Data Availability)
- Products in archive: _not stated_
- Code: Chemical evolution code not released; line analysis based on public RADEX  
  > "We opt not to make the code used for the chemical evolution modeling publicly available" (Code Availability)
- Missing: Chemical evolution code
- Missing: Exact imaging and aperture parameters
- Missing: Model parameters for each target
- Data volume (inferred): ~50-150 GB raw for seven short EBs; tens of GB if products used
- Score (inferred): 5/5, Data public and flux recipe mostly given, but the chemical model is unreleased and imaging details are sparse.
- Rediscovery candidate: no, Line fluxes are reproducible from public data, but the key IMF inference depends on an unreleased chemical evolution code.

## Links

- Method: Romano et al. 2017 (cite: ref 6) (Chemical evolution model of CNO isotopes and IMF)
- Companion: Sliwa et al. 2017 (13CO/C18O ratios in IRAS 13120-5453)
- Related: SPT survey
- Related: Herschel-ATLAS

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 57,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
