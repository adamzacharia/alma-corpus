# A combined multiwavelength VLA/ALMA/Chandra study unveils the complex magnetosphere of the B-type star HR5907

`2018MNRAS.476..562L` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Leto, P. | arXiv: 1801.08738 | DOI: 10.1093/mnras/sty244

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: stellar_physics
- Question: What are the physical conditions and magnetic topology of the magnetosphere of the fast-rotating magnetic B star HR 5907, probed through VLA/ALMA radio light curves, Chandra X-ray spectra and 3D gyro-synchrotron modeling?  
  > "The new radio observations of HR 5907 are combined with archival X-ray data to study the physical condition of its magnetosphere." (abstract)
- Target **HR 5907 (HD 142184)**: coordinates _not stated_; z/distance 131±6 pc  
  > "Distance \[pc\] | $D$ | $131\pm6$ | 2" (Table 1); distance from van Leeuwen 2007  
  > "Distance \[pc\] | $D$ | $131\pm6$ | 2" (Table 1)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 and Band 7 (87–103 and 277–293 GHz)  
  > "observing each source with consecutive scans covering 87–103 and 277–293 GHz (Bands 3 and 7, respectively, using a common photonic LO frequency of 95 GHz for both bands)" (2.2 ALMA)
- frequencies and spectral setup: One baseband (2 GHz), XX only; centres 102.04 and 291.97 GHz  
  > "The centre frequencies of the two basebands were 102.04 and 291.97 GHz in the Band 3 and 7, respectively." (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: ACA correlator, 11 7m and 3 12m antennas  
  > "In this case the observation was made with the ACA correlator using 11 7m and 3 12m antennas." (2.2 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015-Aug-02  
  > "was observed on 2015-Aug-02" (2.2 ALMA)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 6–44 GHz Stokes I and V light curves, two epochs in March 2015, B configuration  
  > "The array was in configuration ‘B’ during the two observing runs of HR 5907." (2.1 VLA)
- Other facility **Chandra ACIS-S**: Archival 25 ks X-ray spectrum (ObsID 13624)  
  > "HR 5907 was observed by *Chandra* on 2012-06-18 for 25 ks (ObsID 13624, (cite: naze_etal14))." (2.3 Chandra)
- External data: Stellar parameters, ephemeris, Be measurements, polar field  
  > "(3) (cite: grunhut_etal12a)" (Table 1) [from (cite: grunhut_etal12a)]
- External data: HR 7355 model parameters (n0 = 2–5e9 cm^-3, low-energy cutoff)  
  > "$n_\mathrm{0}=$2–5$\times 10^9$ \[cm$^{-3}$\] (cite: leto_etal17a)" (6.3 Comparison with the observations) [from (cite: leto_etal17a)]

## Processing

### Calibration

- pipeline or manual: ALMA data re-reduced to produce fluxes per scan; VLA standard pipeline by NRAO staff  
  > "We have re-reduced the data[^4] to produce fluxes per scan." (2.2 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% absolute ALMA flux uncertainty added in quadrature  
  > "An absolute flux calibration uncertainty of 5% has been added in quadrature with the noise-based uncertainty." (2.2 ALMA)
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

- 3D gyro-synchrotron model and simulation approach  
  > "In a previous paper, using the same 3D model and the same simulation approach, we successfully simulated the multi-wavelength radio light curves of HR 7355" (6.3 Comparison with the observations) [from (cite: trigilio_etal04; leto_etal06; leto_etal17a)]

### Not stated but needed to reproduce (our reading)

- ALMA calibrator names and CASA version/reduction details
- flux extraction method for ALMA scans
- non-thermal electron model code not released

## Analysis recipe

1. **measure VLA/ALMA fluxes**: CLEAN images, 2D Gaussian fit in Stokes I and V; uncertainty from fit and map rms in quadrature  
  > "The flux density of the source, for each observing frequency and for each scan, was measured by fitting a two-dimensional gaussian at the source position" (2.1 VLA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **fit X-ray spectrum**: Two-temperature apec and thermal plus power-law fits with tbabs absorption  
  > "we fitted the X-ray spectrum of HR 5907 using a spectral model that combines thermal and non-thermal (power-low) components." (5 X-ray)
   - software: xspec
   - assumption: Solar abundances (Asplund 2009)  
  > "The abundances were set to solar values according to (cite: asplund_etal09)." (2.3 Chandra)
   - fitting: _not stated_
   - validation: reduced chi2 = 0.67  
  > "The quality of fit is similar to the two temperature model (reduced $\chi^2 = 0.67$)." (5 X-ray)
3. **3D radio model comparison**: Grid of >1e6 simulations with fixed delta = 2.6 from X-ray fit; compare light curves; test cold ring, auroral emission, boosted B and flipped dipole  
  > "more than $10^6$ simulations were carried out" (6.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : VLA calibration pipeline and CLEAN imaging  
  > "The calibrated data were imaged using the CASA task CLEAN" (2.1 VLA)
- **xspec** : X-ray spectral fitting  
  > "we used the standard X-ray spectral fitting software xspec (cite: arnaud96)" (2.3 Chandra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 102 GHz flux | 128 and 102 | ±7, ±5 | mJy | 1 | / 237.3487   / 0.6847     / 128 ($\pm7$) / |
| ALMA 292 GHz flux | 32 and 33 | ±3 | mJy | 1 | / 237.3752   / 0.7369     / 33 ($\pm3$) / |
| Hot plasma temperature (2T model) | 6.5 | ±0.9 | keV | 2 | $kT_2$ \[keV\]                                                             / $6.5\pm 0.9$ |
| X-ray power-law index alpha | 1.6 | ±0.1 | dimensionless | 2 | $\alpha$                                                                   / $1.6\pm0.1$ |
| Radio luminosity | 2e18 | not stated | erg/s/Hz | 0 | the absolute radio luminosity of HR 5907 is about $2 \times 10^{18}$ \[erg s$^{-1}$Hz$^{-1}$\] |

## Qualitative findings

- Radio variability amplitude grows with frequency; 292 GHz flux drops steeply (spectral index ≈ -1 between 102 and 292 GHz)  
  > "The spectral index calculated within the two ALMA measurements (102 and 292 GHz) is instead very steep (spectral index $\approx -1$)." (4.2)

## Claim tuples

- H: Can a dipolar gyro-synchrotron model reproduce HR 5907 radio light curves? | E: 3D model simulations with X-ray-constrained parameters | R: Only 6 GHz reproduced; flux at ≥10 GHz about 50% higher than model | F: Simple dipole insufficient; field is likely non-dipolar | **supported**
- H: Non-thermal X-rays are auroral | E: Thermal+power-law fit to Chandra spectrum | R: alpha=1.6, delta=2.6 | F: Tentative auroral non-thermal component | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Cold equatorial ring and coherent auroral radio emission were considered and rejected  
  > "This hypothesis has also been discarded." (8 Summary)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA circular polarization unavailable and only two scans per band  
  > "the circular polarization information of the electromagnetic wave measured by ALMA could not be extracted" (2.2 ALMA)
- Caveat (inferred, ours): ALMA data are only two scans per band
- Caveat (inferred, ours): Non-dipolar field inferred from ad hoc field boosting and flipping

## Reproducibility

- Data public (paper): WSS photometry public in the ALMA Source Catalogue  
  > "The photometry from the survey is available publicly in the ALMA Source Catalogue" (2.2 ALMA)
- Products in archive: _not stated_
- Missing: 3D model code
- Missing: ALMA reduction details
- Data volume (inferred): <5 GB
- Score (inferred): 3/5, ALMA data public, but the reduction is sparse and the modeling code is unreleased.
- Rediscovery candidate: no, The ALMA part is minor and the modeling is not reproducible from the text.

## Links

- Method: (cite: trigilio_etal04; leto_etal06) (3D gyro-synchrotron model)
- Companion: (cite: leto_etal17a) (twin star HR 7355 study)
- Related: ALMA Weak Source Survey

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 25,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
