# Characterizing the Gamma-Ray Variability of the Brightest Flat Spectrum Radio Quasars Observed with the Fermi LAT

`2019ApJ...877...39M` | The Astrophysical Journal 2019 | first author: Meyer, Manuel | arXiv: 1902.02291 | DOI: 10.3847/1538-4357/ab1651

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Characterize long-term gamma-ray variability and brightest flares of six bright FSRQs with Fermi LAT, and constrain the gamma-ray emission location, including via cross-correlation with radio/mm (OVRO, SMA, ALMA calibrator) light curves  
  > "We characterize long-term $\gamma$-ray variability and the brightest $\gamma$-ray flares of six FSRQs." (abstract)
- Target **3C 279**: coordinates R.A. 194.045 deg, Dec -5.786 deg  
  > "| 3C 279 | 3FGL J1256.1-0547 | 194.045 | $-5.786$ | 0.5362 |" (Table 1); z/distance z = 0.5362  
  > "| 3C 279 | 3FGL J1256.1-0547 | 194.045 | $-5.786$ | 0.5362 |" (Table 1); distance from _not stated_
- Target **CTA 102**: coordinates R.A. 338.158 deg, Dec 11.728 deg  
  > "| CTA 102 | 3FGL J2232.5+1143 | 338.158 | 11.728 | 1.037 |" (Table 1); z/distance z = 1.037  
  > "| CTA 102 | 3FGL J2232.5+1143 | 338.158 | 11.728 | 1.037 |" (Table 1); distance from _not stated_
- Target **3C 454.3**: coordinates R.A. 343.493 deg, Dec 16.149 deg  
  > "| 3C 454.3 | 3FGL J2254.0+1608 | 343.493 | 16.149 | 0.859 |" (Table 1); z/distance z = 0.859  
  > "| 3C 454.3 | 3FGL J2254.0+1608 | 343.493 | 16.149 | 0.859 |" (Table 1); distance from _not stated_
- Target **3C 273**: coordinates R.A. 187.266 deg, Dec 2.051 deg  
  > "| 3C 273 | 3FGL J1229.1+0202 | 187.266 | 2.051 | 0.158 |" (Table 1); z/distance z = 0.158  
  > "| 3C 273 | 3FGL J1229.1+0202 | 187.266 | 2.051 | 0.158 |" (Table 1); distance from _not stated_
- Target **PKS 1510-089**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **PKS B1222+216**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: ALMA Band 3, 84-116 GHz (3.6-2.6 mm), calibrator light curves  
  > "the Atacama Large submillimeter/millimeter Array (ALMA) between 84 and 116 GHz (Band 3, 3.6-2.6 mm)" (Results from Radio-$\gamma$-Ray correlation analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Fermi LAT**: Gamma-ray data 2008 Aug 4 to 2018 Jan 30, 100 MeV-316 GeV  
  > "we select $\gamma$-rays that were measured with the *Fermi* LAT between 2008 August 4 and 2018 January 30" (Data selection)
- Other facility **OVRO 40-m**: 15 GHz radio light curves  
  > "All of the studied FSRQs are included in an ongoing blazar monitoring program at OVRO" (Results from Radio-$\gamma$-Ray correlation analysis)
- Other facility **SMA**: 230 GHz (1.3 mm) light curves  
  > "the Submillimeter Array (SMA) at 230 GHz (1.3 mm)" (Results from Radio-$\gamma$-Ray correlation analysis)
- External data: ALMA calibrator-catalogue light curves (Band 3) used as radio data  
  > "also serve as calibrators for SMA and ALMA (cite: 2018MNRAS.478.1512B) at millimeter wavelengths." (Results from Radio-$\gamma$-Ray correlation analysis) [from (cite: 2018MNRAS.478.1512B)]
- External data: Jet Doppler factor, Lorentz factor, viewing angle from VLBA monitoring  
  > "$^{b}$ Average jet values taken from (cite: 2017ApJ...846...98J)." (Table 1) [from (cite: 2017ApJ...846...98J)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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

- Cross-correlation (LCCF) and PSD fitting methodology  
  > "To quantify the correlations, we again closely follow the methodology laid out by (cite: 2014MNRAS.445..437M)." (Results from Radio-$\gamma$-Ray correlation analysis) [from (cite: 2014MNRAS.445..437M)]

### Not stated but needed to reproduce (our reading)

- How ALMA Band 3 flux densities were extracted from the calibrator catalogue (dates, selection)
- Exact ALMA light curve data tables used
- Radio uncertainty handling details

## Analysis recipe

1. **Build radio/gamma light curves and PSDs**: Fit PSD of ALMA/SMA/OVRO light curves with simulated light curves and variance matching  
  > "we use variance matching (cite: 2014MNRAS.445..437M)." (Results from Radio-$\gamma$-Ray correlation analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Cross-correlate gamma and radio light curves**: LCCF with significance from 5000 simulated uncorrelated pairs  
  > "We then calculate the LCCF between 5000 pairs of uncorrelated simulated light curves and derive confidence bands on the LCCF." (Results from Radio-$\gamma$-Ray correlation analysis)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Fermipy** 0.16.0+188: Fermi LAT analysis  
  > "FERMIPY, version 0.16.0+188" (ROI optimization)
- **Fermi Science Tools** 11-05-03: Fermi LAT analysis  
  > "*Fermi Science Tools* version 11-05-03" (ROI optimization)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gamma-ray/ALMA Band 3 time lag, CTA 102 | -216.0 | +209.0/-11.0 | days | 2 | / CTA 102  / $1.94^{+0.42}_{-1.33}$ / 0.45      / $-216.0^{+209.0}_{-11.0}$     / 0.0092   / |
| Gamma-ray/ALMA Band 3 time lag, 3C 454.3 | -27.0 | +30.0/-30.0 | days | 2 | / 3C 454.3 / $1.73^{+0.36}_{-0.30}$ / 0.25      / $-27.0^{+30.0}_{-30.0}$       / 0.0164   / |

## Qualitative findings

- Time lags between gamma-ray and ALMA/SMA mm light curves are consistent with zero, suggesting cospatial production  
  > "The time lags between the $\gamma$-ray and millimeter light curves of ALMA and SMA are consistent with zero, which could indicate a cospatial production." (Summary and Conclusion)

## Claim tuples

- H: Gamma rays are produced near the millimeter core | E: LCCF between Fermi LAT and OVRO/ALMA/SMA light curves | R: Significant correlations for 3C 273, CTA 102 (ALMA), 3C 454.3; mm lags consistent with zero | F: Gamma-ray production consistent with mm core | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Time-lag uncertainties are large so smaller r cannot be ruled out  
  > "One has to keep in mind, however, that the inferred uncertainties on the time lags are large." (Summary and Conclusion)
- Caveat (inferred, ours): ALMA is only a supporting calibrator data set; sparse sampling excluded some sources
- Caveat (inferred, ours): Peak lag does not necessarily equal intrinsic lag

## Reproducibility

- Data public (paper): ALMA calibrator catalogue public; light curves provided online  
  > "Light curves and fit results for the different time intervals and binnings are provided online." (Data selection)
- Products in archive: _not stated_
- Missing: Exact ALMA calibrator light-curve extraction
- Data volume (inferred): Small for ALMA (catalogue flux densities); Fermi data tens of GB
- Score (inferred): 3/5, Fermi analysis is well specified; ALMA part uses catalogue flux densities with few details.
- Rediscovery candidate: no, ALMA role is minor and main results are gamma-ray based.

## Links

- Method: (cite: 2014MNRAS.445..437M) (LCCF and PSD methodology)
- Related: ALMA calibrator catalogue
- Related: MOJAVE

## Checks

```json
{
 "quotes": 27,
 "quotes_ok": 27,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00001.CAL"
 ],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 23,
  "rate": 0.311
 },
 "evidence_ok": true
}
```
