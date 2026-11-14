# On the Accuracy of the ALMA Flux Calibration in the Time Domain and across Spectral Windows

`2020AJ....160..270F` | The Astronomical Journal 2020 | first author: Francis, Logan | arXiv: 2010.02186 | DOI: 10.3847/1538-3881/abbe1a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, star_formation
- Question: How accurate is the ALMA pipeline flux calibration between epochs and across spectral windows, tested with stable YSO calibrators in Band 7 ACA data?  
  > "to independently assess the accuracy of the ALMA flux calibration and to refine the relative calibration across epochs." (abstract)
- Target **Serpens SMM 9 (CAL 1)**: coordinates 18:29:48.07 +01:16:43.7 (ICRS)  
  > "| Serpens SMM 9 (CAL 1) | Serpens_Main_850_01 | Ser-emb 8, SH2-68N | 18:29:48.07 +01:16:43.7 |" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **Serpens SMM 4 (CAL 2)**: coordinates 18:29:56.72 +01:13:15.6 (ICRS)  
  > "| Serpens SMM 4 (CAL 2) | Serpens_Main_850_08 | \- | 18:29:56.72 +01:13:15.6 |" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **Serpens SMM 3 (CAL 3)**: coordinates 18:29:59.32 +01:14:00.5 (ICRS)  
  > "| Serpens SMM 3 (CAL 3) | Serpens_Main_850_09 | \- | 18:29:59.32 +01:14:00.5 |" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **Serpens SMM 11 (CAL 4)**: coordinates 18:30:00.38 +01:11:44.6 (ICRS)  
  > "| Serpens SMM 11 (CAL 4) | Serpens_Main_850_11 | \- | 18:30:00.38 +01:11:44.6 |" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00917.S, 2019.1.00475.S
- bands: Band 7 (343.5 GHz)  
  > "343.5 GHz (Band 7) ALMA Atacama Compact Array observations" (abstract)
- frequencies and spectral setup: 4 low-resolution spws, 1.875 GHz each, 128 channels  
  > "to provide 4 low-resolution spectral windows with 1.875GHz of bandwidth across 128 channels, for a total bandwidth of 7.5GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: ACA stand-alone, twelve 7m antennas  
  > "All observations are taken with the stand-alone mode of the Atacama Compact Array (ACA), a sub-array of ALMA consisting of twelve closely-spaced 7m diameter antennas." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~4 arcsec (~1750 au)  
  > "We have obtained 7 epochs of our targets with a typical resolution of 4$''$ ($\sim 1750$ au)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 7 epochs, 14-Oct-2018 to 29-Oct-2019  
  > "| 1 | 14-Oct-2018 | J1924-2914 | J1851+0035 |" (Table 2); "| 7 | 29-Oct-2019 | J1924-2914 | J1851+0035 |" (Table 2)
- pi or archival as stated: PI Logan Francis  
  > "Two ALMA projects (PI: Logan Francis, project IDs 2018.1.00917.S, 2019.1.00475.S)" (Introduction)
- Other facility **JCMT Transient Survey**: Monitoring showing YSO calibrators stable to <3% over 4 years  
  > "The brightness of all YSO calibrators at the JCMT has remained stable over the first 4 years of the Transient Survey to $<3\%$." (Observations)
- External data: ALMA calibrator catalog fluxes and spectral indices (queried April 2020)  
  > "We thus queried the flux of each grid calibrator in April 2020 and compared its flux and spectral index with the values used by the pipeline" (3.2 Grid Calibrator Flux updates) [from ALMA calibrator catalog (not cited as a paper)]

## Processing

### Calibration

- pipeline or manual: Original ALMA pipeline-calibrated visibilities as delivered, then rescaled  
  > "We start our relative calibration process from the original pipeline-calibrated ALMA visibilities processed using CASA 5.6.1." (3.1 Continuum Calibration)
- casa version: CASA 5.6.1  
  > "processed using CASA 5.6.1" (3.1 Continuum Calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Grid quasars J1924-2914, J1751+0939, J1517-2422 by epoch  
  > "| 2 | 06-Mar-2019 | J1751+0939 | J1743-0350 |" (Table 2)
- flux scale uncertainty: nominal Band 7 10%  
  > "the expected nominal band 7 flux calibration accuracy of 10%" (3.1 Continuum Calibration)
- self calibration: _not stated_

### Imaging

- task: Analysis in the uv-plane (point-source fit); dirty cubes only used to extract continuum  
  > "we perform our analysis in the $uv$-plane, where careful error analysis is more tractable." (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Spectra measured in 3 arcsec diameter aperture centred on brightest source  
  > "extract the continuum by sigma-clipping of the spectra measured in a 3$''$ diameter aperture centered on the brightest source" (3.1 Continuum Calibration)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Mean correction factor relative-calibration technique  
  > "This technique follows that used for the JCMT Transient Survey (cite: mairs2017) and its application to interferometric data in (cite: francis2019)." (3.1 Continuum Calibration) [from Mairs et al. 2017 (cite: mairs2017); Francis et al. 2019 (cite: francis2019)]

### Not stated but needed to reproduce (our reading)

- Sigma-clipping threshold for continuum extraction
- Point-source fit software/task and error treatment
- Weighting of the Monte Carlo and Gaussian fits (binning of histograms)
- Whether self-calibration was applied to YSO calibrators (section text empty)
- Exact updated flux.csv values used for rescaling
- Which flux scale details were used for spw-by-spw analysis

## Analysis recipe

1. **Extract continuum per calibrator and epoch**: Dirty cubes, sigma-clipped spectra in 3 arcsec aperture, uv-plane point-source fit with flat spectral index  
  > "We then perform a $uv$-plane fit of a point source to the extracted continuum for each YSO calibrator and epoch assuming a zero (flat) spectral index" (3.1 Continuum Calibration)
   - software: CASA
   - assumption: YSO calibrators stable in flux and spectral index  
  > "we assume our YSO calibrators to be stable in spectral index" (3.1 Continuum Calibration)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute relative flux calibration factors**: MCF = mean flux over 7 epochs divided by epoch flux; rFCF = average of 4 MCFs  
  > "we take the average of the four MCFs for calibrators in that epoch" (3.1 Continuum Calibration)
   - assumption: YSO calibrators stable to ~3-5% from JCMT monitoring  
  > "the brightness of the YSO calibrators is stable over 4 years to a level of $\sim$ 3-5%" (3 Relative Calibration)
   - fitting: _not stated_
   - validation: MCF scatter across calibrators within an epoch <3%  
  > "For any epoch, the MCFs have a range $<7\%$ and standard deviation $<3\%$." (3.1 Continuum Calibration)
3. **Test grid calibrator catalog update**: Compare original pipeline vs April 2020 catalog fluxes, rescale visibilities, recompute MCFs and rFCFs  
  > "With the updated pipeline values for the grid calibrator fluxes, we rescale the pipeline calibrated visibilities and compute the MCFs and rFCFs again" (3.2 Grid Calibrator Flux updates)
   - software: CASA
   - fitting: _not stated_
   - validation: rFCF spread reduced  
  > "the rFCFs overall now have a standard deviation of 9% and range of 26%" (3.2 Grid Calibrator Flux updates)
4. **Measure spectral-window relative calibration error**: Per-spw normalized MCFs; Gaussian fits to scatter histograms; power-law fit vs frequency; Monte Carlo of 16 normalized MCFs repeated 10000 times  
  > "We then measure the power law index $\alpha$ for each simulated set of normalized MCFs and repeat this process 10000 times." (3.4 Calibration across spectral windows)
   - assumption: Width of distribution is sum of two uncorrelated random errors; systematic frequency-dependent terms negligible  
  > "systematic frequency dependent contributions are assumed to be negligible" (3.4 Calibration across spectral windows)
   - fitting: _not stated_
   - validation: Epoch 2 slope plausibly due to spw relative calibration error  
  > "the slope in the second epoch is plausibly explained as the result of a relative calibration error" (3.4 Calibration across spectral windows)

## Software

- **CASA** 5.6.1: Pipeline processing, rescaling of visibilities  
  > "Common Astronomy Software Application (CASA) 5.6.1" (Software)
- **astropy** : Listed software  
  > "astropy (cite: astropy), matplotlib (cite: matplotlib2007)" (Software)
- **matplotlib** : Listed software (plotting)  
  > "astropy (cite: astropy), matplotlib (cite: matplotlib2007)" (Software)
- **analysisUtils** : getALMAFlux to compute grid calibrator flux; catalog delay statistics  
  > "function `getALMAFlux` in the `analysisutils`[^1] python package" (4.2 Best Practices)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Std dev of rFCFs (original pipeline) | 14 | not stated | % | 2 | We find the YSO rFCFs have a standard deviation of $14\%$ and range of $45\%$ |
| Range of rFCFs (original) | 45 | not stated | % | 2 | We find the YSO rFCFs have a standard deviation of $14\%$ and range of $45\%$ |
| Std dev of rFCFs after catalog update | 9 | not stated | % | 3 | the rFCFs overall now have a standard deviation of 9% and range of 26% |
| Range of rFCFs after update | 26 | not stated | % | 3 | the rFCFs overall now have a standard deviation of 9% and range of 26% |
| Relative calibration accuracy using YSO calibrators | ~3 | not stated | % | 2 | This strategy allows us to reach a relative flux calibration accuracy of $\sim 3\%$ |
| Relative flux calibration error between spectral windows | 0.8 | not stated | % | 4 | A Gaussian fit to the red histogram has a width of $\sigma=0.8\%$ |
| Probability of epoch-2 slope from random errors across seven epochs | ~16 | not stated | % | 4 | or $\sim16\%$ for seven |

## Qualitative findings

- Out-of-date calibrator catalog can degrade Band 7 flux calibration beyond the nominal 10%  
  > "the ALMA flux calibration accuracy in Band 7 may be poorer than the nominal 10%" (Conclusions)

## Claim tuples

- H: Pipeline flux calibration meets nominal 10% in Band 7 across epochs | E: Relative calibration with four stable YSO calibrators over 7 ACA epochs | R: rFCF std 14%, range 45%; improves to 9% and 26% after catalog update | F: Out-of-date catalog worsens calibration | **supported**
- H: Flux calibration differs between spectral windows within a band | E: Per-spw normalized MCFs and Monte Carlo | R: 0.8% relative error between spws | F: In-band spectral indices are highly uncertain | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Incorrect grid calibrator spectral index as cause of epoch 2 slope ruled out  
  > "A large systematic error introduced by an incorrect quasar spectral index is therefore ruled out for epoch 2." (3.4 Calibration across spectral windows)
- How they decided it was enough: _not stated_
- Limitation (authors): Point-source model only; structure not modeled  
  > "Future work will model the structure of each source in more detail." (3.1 Continuum Calibration)
- Caveat (inferred, ours): Only 7 epochs and one band/array; generality uncertain
- Caveat (inferred, ours): Assumes YSO calibrators stable, based on JCMT 3-5%
- Caveat (inferred, ours): Several text passages (self-calibration section) missing in the text

## Reproducibility

- Data public (paper): Data from ALMA projects acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00917.S, ADS/JAO.ALMA#2019.1.00475.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: Example CASA rescaling script in appendix  
  > "The below python script shows an example of increasing the visibility amplitudes by 10% which has been tested for CASA 5.6.1." (Measurement Set Re-scaling in CASA)
- Missing: Sigma-clipping parameters
- Missing: Point-source fitting details
- Missing: Self-calibration description
- Data volume (inferred): ~10-50 GB (7 ACA Band 7 execution blocks)
- Score (inferred): 3/5, Simple recipe with tables of numbers but missing fit and clipping details.
- Rediscovery candidate: yes, Data likely public, recipe simple, numeric results in tables.

## Links

- Method: Francis et al. 2019 (cite: francis2019) (Relative calibration with interferometric data)
- Related: JCMT Transient Survey
- Related: ALMACAL

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 39,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
