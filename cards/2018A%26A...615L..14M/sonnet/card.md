# Revised SED of the triple protostellar system VLA 1623-2417

`2018A&A...615L..14M` | Astronomy and Astrophysics 2018 | first author: Murillo, N. M. | arXiv: 1807.00640 | DOI: 10.1051/0004-6361/201833420

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: How do new ALMA Band 9 data change the SED of each component of VLA 1623-2417 and the inferred nature of VLA 1623 B?  
  > "We explore the consequences of new ALMA Band 9 data on the spectral energy distribution (SED) of VLA 1623$-$2417 and their inferred nature." (abstract)
- Target **VLA 1623-2417 (A, B, W)**: coordinates A: 16:26:26.390 -24:24:30.688; B: 16:26:26.309 -24:24:30.588; W: 16:26:25.636 -24:24:29.488  
  > "Recent observations place L1688 and VLA 1623  at a distance of 137.3 $\pm$ 1.2 pc (cite: ortiz2017)." (Introduction); "16:26:26.390" (Table 2); z/distance 137.3 +/- 1.2 pc  
  > "Recent observations place L1688 and VLA 1623  at a distance of 137.3 $\pm$ 1.2 pc (cite: ortiz2017)." (Introduction); "16:26:26.390" (Table 2); distance from Ortiz-Leon et al. 2017  
  > "Recent observations place L1688 and VLA 1623  at a distance of 137.3 $\pm$ 1.2 pc (cite: ortiz2017)." (Introduction); "16:26:26.390" (Table 2)

## Data provenance

- ALMA projects: 2012.1.00707.S, 2011.0.00902.S, 2013.1.01004.S
- bands: Band 6, 7 and 9  
  > "2012.1.00707.S | 9 | 421 $-$ 429 $\mu$m" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 9: 30-2280 kλ  
  > "30 $\sim$ 2280" (Table 1)
- angular resolution: Band 9 beam 0.25x0.14 arcsec (natural) and 0.17x0.1 arcsec (Briggs)  
  > "0.25$\ensuremath{''}\times$0.14$\ensuremath{''}$$^{a}$" (Table 1)
- max recoverable scale: Band 9: 1.6 arcsec  
  > "1.6 | 9.0" (Table 1)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Band 9 PI D. Salter; Bands 6/7 PI S.-P. Lai; Cycle 0 Band 6 PI N. Murillo  
  > "Cycle 2 observations in Band 9 (Project code: 2012.1.00707.S; PI: D. Salter)" (Observations)
- Other facility **Herschel/PACS**: 70, 100, 160 um unresolved fluxes tracing the SED peak  
  > "PSF photometry of *Herschel* PACS maps provides unresolved fluxes between 70 to 160 $\mu$m, which trace the peak of the SED." (Summary)
- Other facility **Spitzer (IRAC, MIPS, IRS)**: Infrared fluxes and newly reduced IRS spectra  
  > "The Spitzer IRS spectra are new reductions of serendipitous observations of VLA 1623." (Observations)
- External data: SMA 1.3 mm and BIMA 2.7 mm fluxes  
  > "Observations with SMA at 1.3 mm and BIMA at 2.7 mm (cite: looney2000; murillo2013a) detect all three components." (Analysis) [from looney2000; murillo2013a]
- External data: Spitzer IRAC/MIPS, VLA and MERLIN fluxes (Table refs 1,2,6,7)  
  > "the fluxes presented in this work are used, together with those found in literature." (Analysis) [from Table references]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-130 (Band 9); Ceres unreliable  
  > "Flux calibration was done with J1733$-$130." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural and Briggs weighting for Band 9 (robust not given)  
  > "ALMA/Band 9 Briggs weighting" (Table 2)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Flux region defined by the 3 sigma contour; Band 9 uses the Band 6 region  
  > "Fluxes for each component are measured using a region which is defined by the 3$\sigma$ contour of the continuum emission." (Results)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Herschel deblending method  
  > "The method is further detailed in (cite: murillo2016) and (cite: diolaiti2000)." (Analysis) [from (cite: murillo2016); (cite: diolaiti2000)]
- Envelope mass formula  
  > "To calculate the envelope mass, the formula from (cite: jorgensen2009)" (Analysis) [from (cite: jorgensen2009)]

### Not stated but needed to reproduce (our reading)

- Band 9 robust value and cleaning parameters
- CASA version and calibration procedure
- Priors/initial values and bounds for graybody fit, beta values
- Exact flux-measurement regions
- How IR flux was split for the A/B fits
- Herschel aperture-correction details

## Analysis recipe

1. **Measure ALMA continuum fluxes**: Integrated flux in 3 sigma contour region per component; Band 9 uses Band 6 region  
  > "For Band 9 continuum, we use the same region used for Band 6." (Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Herschel PACS photometry**: PSF photometry with aperture correction, deblending at 160 and 100 um  
  > "PSF photometry is performed on the PACS maps to extract fluxes using *StarFinder* (cite: diolaiti2000)." (Analysis)
   - software: StarFinder
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit SEDs**: Single-temperature graybody fit over 7 mm to 22 um; three IR splitting scenarios for A/B  
  > "The fit is done in the wavelength range from 7 mm to 22 $\mu$m." (Analysis)
   - software: SciPy curve_fit
   - assumption: optical depth tau proportional to nu^beta  
  > "with optical depth $\tau\propto\nu^{\beta}$" (Analysis)
   - fitting: curve_fit least squares  
  > "The SEDs are fit using the Scipy method curve$\_$fit" (Analysis)
   - validation: Fits compared with and without Herschel fluxes  
  > "The graybody fits are practically the same with or without the *Herschel* PACS fluxes" (Analysis)
4. **Bolometric luminosity and envelope mass**: Trapezoid integration of fit curves; Jorgensen et al. 2009 mass formula with ALMA 850 um flux  
  > "The bolometric luminosity is calculated based on the curve of the fits to the constructed SEDs using the trapezoid method." (Analysis)
   - assumption: distance 137.3 pc  
  > "for a distance of 137.3 pc" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SciPy curve_fit** : graybody SED fitting  
  > "The SEDs are fit using the Scipy method curve$\_$fit" (Analysis)
- **StarFinder** : PSF photometry on Herschel PACS maps  
  > "using *StarFinder* (cite: diolaiti2000)" (Analysis)
- **SMART/CASSIS AdOpt** CASSIS low-resolution pipeline update version 7: Spitzer IRS extraction  
  > "CASSIS low-resolution pipeline update, version 7 (cite: lebouteiller2010) provided in SMART" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 7 850um flux, VLA 1623 A | 1139.5 | 3.4 | mJy | 1 | / 850        / 1139.5        / 3.4      / 373.0 |
| Dust temperature of B | 38 to 49 | large | K | 3 | the derived dust temperature for VLA 1623 B (38 to 49 K) |
| Dust temperature of W | 66 | not stated | K | 3 | The derived dust temperature for VLA 1623 W (66 K) |
| Lbol of W | 0.13 | 0.01 | Lsun | 4 | 0.13 $\pm$ 0.01 L$_{\odot}$ |
| Envelope mass of W | 0.04 | 0.005 | Msun | 4 | For VLA 1623 W, the mass is 0.04 $\pm$ 0.005 M$_{\odot}$. |

## Qualitative findings

- B's SED does not peak at 850 um but resembles A at wavelengths shorter than 450 um  
  > "does not peak at 850$\mu$m as previously expected" (abstract)

## Claim tuples

- H: VLA 1623 B has a very cold envelope | E: Band 9 plus Herschel SED graybody fits | R: T_dust of 38-49 K | F: B is not very cold; may contribute significantly at lambda<450 um | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): A and B unresolved at lambda<450um, so SED parameters uncertain  
  > "parameters derived from the SED are uncertain, and these bolometric luminosities are rough estimates" (Analysis)
- Caveat (inferred, ours): Graybody fit details and degeneracy with beta not given
- Caveat (inferred, ours): Flux split between A and B arbitrary

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Band 9 imaging parameters
- Missing: Fit parameters and bounds
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Archival ALMA data, but imaging and fit details are sparse.
- Rediscovery candidate: no, Imaging and fit settings are incomplete.

## Links

- Method: Jorgensen et al. 2009 (envelope mass formula)
- Companion: Murillo & Lai 2013 (previous SED and Cycle 0 data)
- Related: Herschel Gould Belt Survey

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
 "codes_printed_but_missing": [
  "2013.0.01004.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 31,
  "rate": 0.456
 },
 "evidence_ok": true
}
```
