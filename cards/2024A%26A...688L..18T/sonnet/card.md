# Detection of maser emission at 183 and 380 GHz with ALMA in the gigamaser galaxy TXS 2226-184

`2024A&A...688L..18T` | Astronomy and Astrophysics 2024 | first author: Tarchi, A. | arXiv: 2407.13373 | DOI: 10.1051/0004-6361/202451245

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Is there 183 and 380 GHz water maser emission in the 22 GHz gigamaser galaxy TXS 2226-184, and what is its nature (disk vs jet/outflow)?  
  > "To date, the nature of this maser is still being debated, in particular, whether it is associated with a nuclear accretion disk or with an ejection component" (abstract)
- Target **TXS 2226-184**: coordinates RA 22h29m12.4942s, Dec -18d10m47.235s (J2000), from maser centroid  
  > "TXS 2226-184 (hereafter TXS 2226) is located at a distance of 107 Mpc ($z$ = 0.025; (cite: Kuo2018))" (Introduction); "RA$_{J2000}$=$\rm{22^{h}:29^{m}:12.4942^{s}}$ and Dec.$_{J2000}$=$\rm{-18^{\circ}:10':47.235''}$" (4.2 The possible nature of the maser emission); z/distance 107 Mpc (z = 0.025)  
  > "TXS 2226-184 (hereafter TXS 2226) is located at a distance of 107 Mpc ($z$ = 0.025; (cite: Kuo2018))" (Introduction); "RA$_{J2000}$=$\rm{22^{h}:29^{m}:12.4942^{s}}$ and Dec.$_{J2000}$=$\rm{-18^{\circ}:10':47.235''}$" (4.2 The possible nature of the maser emission); distance from Kuo et al. 2018  
  > "TXS 2226-184 (hereafter TXS 2226) is located at a distance of 107 Mpc ($z$ = 0.025; (cite: Kuo2018))" (Introduction); "RA$_{J2000}$=$\rm{22^{h}:29^{m}:12.4942^{s}}$ and Dec.$_{J2000}$=$\rm{-18^{\circ}:10':47.235''}$" (4.2 The possible nature of the maser emission)

## Data provenance

- ALMA projects: 2022.1.01591.S
- bands: Band 5 and Band 7 used (Band 6 observed but not included)  
  > "On April 28, 2023, Band 6 was also observed, but it is not included in this work." (2 Observations and data reduction)
- frequencies and spectral setup: four spectral windows per band, ~1.13 MHz resolution, ~2 GHz wide; one centered on maser lines  
  > "The spectral setup for each band consisted of four spectral windows." (2 Observations and data reduction); "one spectral window was centered around the expected locations of the maser lines." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.13 arcsec (183 GHz), 0.06 arcsec (380 GHz)  
  > "The restoring beam size of the images is 0.13 and 0.06 arcsec, for the 183 and 380 GHZ cubes, respectively." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 5 on May 24, Band 7 on June 9, 2023  
  > "dual polarization at Band 5 on May 24, and Band 7 on June 9, 2023" (2 Observations and data reduction)
- pi or archival as stated: Own project, PI Tarchi  
  > "performed as part of the ALMA project 2022.1.01591.S (PI: Tarchi)" (2 Observations and data reduction)
- Line: H2O 3(1,3)-2(2,0) (183.310087 GHz)
- Line: H2O 4(1,4)-3(2,1) (380.1973598 GHz)
- Other facility **GBT (AGBT10C_013)**: 22 GHz archival spectrum observed Dec 9, 2010  
  > "we retrieved a data set from the Green Bank Telescope (GBT) archive. This was observed on December 9, 2010, under the project name AGBT10C_013." (2 Observations and data reduction)
- External data: 22 GHz GBT observation details and VLBI maser positions  
  > "The details of this observation are thoroughly reported in (cite: Surcis2020), and will not be replicated here." (2 Observations and data reduction) [from (cite: Surcis2020)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 6.5.4.9  
  > "version 6.5.4.9" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: QA2 processed data exist for all project data  
  > "All data from this ALMA project have a corresponding quality assurance 2 (QA2) data processing." (2 Observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean on continuum-subtracted line data  
  > "We carried out the imaging of the spectral line continuum-subtracted data sets using the task ‘tclean’" (2 Observations and data reduction)
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
- final beam: 0.13 arcsec (183 GHz), 0.06 arcsec (380 GHz)  
  > "The restoring beam size of the images is 0.13 and 0.06 arcsec, for the 183 and 380 GHZ cubes, respectively." (2 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- GBT 22 GHz observation and reduction details  
  > "The details of this observation are thoroughly reported in (cite: Surcis2020), and will not be replicated here." (2 Observations and data reduction) [from (cite: Surcis2020)]
- Isotropic luminosity from the standard equation  
  > "By using the standard equation (see, e.g., (cite: Humphreys2016); their Eq. 1) to derive the isotropic luminosity" (3 Results) [from (cite: Humphreys2016) Eq. 1]

### Not stated but needed to reproduce (our reading)

- Weighting/robust, cell and image size, deconvolver, niter/threshold
- Continuum subtraction method and line-free channels
- Spectral extraction region and flux measurement aperture
- Channel width of the imaged cubes and velocity definition/reference
- Details of Gaussian fit (components a+b) and how centroid positions were measured
- Array configurations and baselines, on-source times, calibrators

## Analysis recipe

1. **Image line cubes**: tclean on QA2-calibrated, continuum-subtracted data for Band 5 and 7  
  > "We carried out the imaging of the spectral line continuum-subtracted data sets using the task ‘tclean’" (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and fit Gaussians**: Spectra from cubes with spectral profile tool; Gaussian fits of features with CLASS  
  > "We extracted the spectra from the image cubes using the spectral profile tool." (2 Observations and data reduction); "for follow-up investigation (e.g., Gaussian fitting, comparison)" (2 Observations and data reduction)
   - software: CASA, CLASS/GILDAS
   - fitting: Gaussian fits of individual features  
  > "The results for a Gaussian fit of the individual spectral line features are reported in Table" (3 Results)
   - validation: _not stated_
3. **Derive isotropic luminosity**: Standard maser L_iso equation of Humphreys et al. 2016  
  > "By using the standard equation (see, e.g., (cite: Humphreys2016); their Eq. 1) to derive the isotropic luminosity" (3 Results)
   - assumption: Distance 107 Mpc  
  > "located at a distance of 107 Mpc ($z$ = 0.025; (cite: Kuo2018))" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Brightness temperature limits and positions**: Lower limit Tb from beam size; centroid positions of both masers compared with 22 GHz positions  
  > "The lower limit to the brightness temperature of our spectral line emission is then of order 130 K" (4 Discussion)
   - assumption: Thermal emission limited to Tb <= 2000 K  
  > "for the emission to be thermal, but with a brightness temperature $\le$ 2000 K, such that the water molecules are not dissociated" (4 Discussion)
   - fitting: _not stated_
   - validation: Compared with 22 GHz VLBI positions within ~10 mas ALMA astrometric precision  
  > "the absolute astrometric precision for our ALMA observations is on the order of 10 mas" (4.2 The possible nature of the maser emission)

## Software

- **CASA** 6.5.4.9: tclean imaging and spectral profile extraction  
  > "using the task ‘tclean’ of the Common Astronomy Software Applications (CASA) software" (2 Observations and data reduction)
- **CLASS (GILDAS)** : Gaussian fitting and comparison of spectra  
  > "imported in the Continuum and Line Analysis Single-dish Software (CLASS) package" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 183 GHz feature A1 peak flux density | 0.125 | not stated | Jy | 2 | / A1$(a+b)$ / 0.125 / 94.2 ( 0.2) / 12.48 ( 0.03) / 7368.7 ( 0.2) / 25589 / |
| 183 GHz feature B1 peak flux density | 0.043 | not stated | Jy | 2 | / B1 / 0.043 / 110.2 ( 0.8) / 5.01 ( 0.03) / 7217.9 ( 0.4) / 10281 / |
| 380 GHz feature A2 peak flux density | 0.217 | not stated | Jy | 2 | / A2(a$+$b) / 0.217 / 103.6 ( 0.5) / 24.0 ( 0.1) / 7366.2 ( 0.2) / 101893 / |
| 380 GHz feature B2 peak flux density | 0.119 | not stated | Jy | 2 | / B2 / 0.119 / 106 ( 1) / 13.5 ( 0.1) / 7215.8 ( 0.4) / 57465 / |
| L_iso of A1 | 25589 | not stated | L_sun | 3 | / A1$(a+b)$ / 0.125 / 94.2 ( 0.2) / 12.48 ( 0.03) / 7368.7 ( 0.2) / 25589 / |
| Tb lower limit at 183 GHz | 130 | not stated | K | 4 | The lower limit to the brightness temperature of our spectral line emission is then of order 130 K |
| Tb lower limit at 380 GHz | ~400 | not stated | K | 4 | the lower limit to the brightness temperature of our spectral line emission ($\sim$ 400 K) |

## Qualitative findings

- Both lines show two-peaked profiles like the 22 GHz maser and are co-spatial within errors; the 183 and 380 GHz masers have centroid positions coincident within 1 mas.  
  > "the position derived from centroid measurements of both the 183 and 380 GHz masers is coincident, within the statistical uncertainty of 1 mas" (4.2 The possible nature of the maser emission)

## Claim tuples

- H: TXS 2226 hosts 183 and 380 GHz maser emission | E: ALMA Band 5 and 7 spectral cubes | R: Two-peaked broad lines at both frequencies, S/N >= 100, L_iso ~1e4-1e5 Lsun | F: First 380 GHz maser detection in a known 22 GHz maser galaxy; all three transitions in one object | **supported**
- H: The masers arise from the same nuclear structure as the 22 GHz maser | E: Compared profiles and centroid positions with 22 GHz data | R: Similar profiles; positions coincident within errors | F: Same gas likely; nature favors amplification of nuclear continuum from jet or outflow, but more analysis needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Thermal origin cannot be ruled out by Tb alone; would require emitting region >0.03 arcsec (15 pc) at 183 GHz, judged unlikely  
  > "the emitting region has to be $>$ 0.03 arcsec (corresponding to 15 pc)" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Preliminary reduction; GBT and ALMA epochs differ by over ten years, so only qualitative comparison; resolution too coarse for maser spot positions  
  > "we note that only a qualitative comparison is performed here" (4.1 Comparison of the (maser) features); "Unfortunately, the spatial resolution is too coarse to yield detailed position estimates of the different maser emitting regions." (4.1 Comparison of the (maser) features)
- Caveat (inferred, ours): Maser nature rests on indirect arguments (profile and position), as Tb limits are low
- Caveat (inferred, ours): Flux calibration uncertainty and fit uncertainties not discussed
- Caveat (inferred, ours): Comparison with 22 GHz is across epochs

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: QA2 products exist for the project  
  > "All data from this ALMA project have a corresponding quality assurance 2 (QA2) data processing." (2 Observations and data reduction)
- Missing: Imaging parameters
- Missing: Spectral extraction region
- Missing: Fit setup
- Missing: Luminosity equation inputs
- Data volume (inferred): ~50-100 GB for the two bands (raw), less for QA2 products
- Score (inferred): 3/5, Short Letter; ALMA data and QA2 are available, but imaging and extraction parameters are not given.
- Rediscovery candidate: no, Imaging and extraction recipe is incomplete, and the data may still be under proprietary period or require own reduction.

## Links

- Method: (cite: Humphreys2016) (L_iso equation)
- Companion: (cite: Surcis2020) (22 GHz VLBI and GBT data of the same maser)
- Companion: (cite: Tarchi2023) (EVN multi-band continuum campaign)
- Related: Megamaser Cosmology Project

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 66,
  "stated": 31,
  "rate": 0.47
 },
 "evidence_ok": true
}
```
