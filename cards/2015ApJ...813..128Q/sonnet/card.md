# Chemical Imaging of the CO Snow Line in the HD 163296 Disk

`2015ApJ...813..128Q` | The Astrophysical Journal 2015 | first author: Qi, Chunhua | arXiv: 1510.00968 | DOI: 10.1088/0004-637X/813/2/128

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Where is the CO snow line in the HD 163296 disk, and how well do N2H+, DCO+ and C18O trace it?  
  > "The aim is to determine the CO snow line location using observations of N 2 H [+] emission." (1. Introduction)
- Target **HD 163296**: coordinates _not stated_; z/distance ~122 pc  
  > "the disk around HD 163296 at a distance of ∼122 pc, the target of this study" (1. Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00681.S, 2011.0.00010.SV
- bands: _not stated_
- frequencies and spectral setup: Four SPWs: N2H+ 3-2, DCO+ 4-3, one with an H2CO line, one continuum-only  
  > "The correlator was configured to observe four spectral windows (SPWs)" (2. Observations)
- continuum bandwidth: _not stated_
- arrays: 32 12 m antennas  
  > "with 32 12 m antennas" (2. Observations)
- configurations: _not stated_
- baselines: 18–650 m (17–605 kλ)  
  > "Baselines ranged from 18–650 m (17–605 kλ)." (2. Observations)
- angular resolution: ~0.5'' (60 AU); N2H+ beam 0.75''×0.60'', DCO+ 0.58''×0.37''  
  > "at ∼ 0.5 [′′] (60 AU) resolution" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 45 minutes  
  > "The total integration time on HD 163296 was 45 minutes." (2. Observations)
- observing dates: 21 May 2014  
  > "carried out with the Atacama Large Millimeter/submillimeter Array (ALMA) on 21 May 2014" (2. Observations)
- pi or archival as stated: _not stated_
- Line: N2H+ J=3-2 (279.512 GHz)
- Line: DCO+ J=4-3 (288.144 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- External data: Disk density and temperature structure model of HD 163296  
  > "We adopt the density and temperature disk structure from Qi et al. (2011)" (3.1) [from Qi et al. 2011]
- External data: Collisional rates based on HCO+ with H2  
  > "The collisional rates are adopted from Flower (1999) based on HCO [+]" (3.1) [from Flower (1999)]
- External data: ALMA SV 13CO and C18O J=2-1 data  
  > "See the observations and data reduction details in Rosenfeld et al. (2013)." (2. Observations) [from Rosenfeld et al. (2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2  
  > "The visibility data were reduced and calibrated in CASA 4.2." (2. Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Continuum self-cal following HD 163296 SV Band 7 CASA Guides, applied to line data  
  > "We carried out self-calibration procedures on the continuum as demonstrated in the HD 163296 Science Verification Band 7 CASA Guides" (2. Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "a All quoted values assume natural weighting." (Table 1)
- uv taper: Gaussian taper of 0.5'' FWHM for N2H+  
  > "we applied a Gaussian taper to the visibilities that corresponds to 0.5 [′′] FWHM in the image domain." (2. Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Subtracted in the visibility domain after averaging line-free channels  
  > "subtracted the continuum emission in the visibility domain" (2. Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- N2H+ abundance modeling methodology  
  > "We extract the N 2 H [+] abundance profile in the HD 163296 disk following the methodology of" (3.1) [from Qi et al. (2011, 2013b)]
- Vertical boundaries from chemical models  
  > "based on the chemical models of Aikawa & Nomura (2006, Fig. 8)" (3.1) [from Aikawa & Nomura (2006)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Imaging task parameters (cell, image size, masking)
- Fit optimizer and grid details for chi2 minimization
- Details of the 13CO/C18O SV data reduction
- Calibrator names other than J1733-1304

## Analysis recipe

1. **Calibrate, self-calibrate, subtract continuum**: CASA reduction, continuum self-cal from CASA guide, continuum subtraction in uv  
  > "We applied the continuum self-calibration" (2. Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit N2H+ and DCO+ abundance profiles**: Parametric column density power law with R_in, R_out, N100, p; chi2 on complex visibilities with RATRAN  
  > "The best-fit parameter estimates are obtained by minimizing χ [2], the weighted residual of the complex visibilities" (3.1)
   - software: RATRAN
   - parameter: Vertical boundaries σs,σm fixed to 1, 32; R_out fixed at 500 AU for N2H+  
  > "We fix the vertical boundary values σ s, σ m to 1, 32, respectively" (3.1)
   - assumption: Disk inclination ~44 deg; Qi et al. 2011 disk structure  
  > "disk inclination at around 44 [◦], see Qi et al. 2011" (3. Results)
   - fitting: chi2 minimization, errors within 3σ  
  > "Errors within 3σ." (Table 2)
   - validation: Residual images show no emission above 3σ  
  > "the residual image shows no significant emission above the 3σ level" (3.1)
3. **Fit C18O with freeze-out temperature and depletion**: Same framework with T_CO and F_CO free, σs fixed at 0.79  
  > "with both the CO freeze-out temperature (T CO ) and the CO freeze-out fraction (depletion factor; F CO ) as free parameters" (3.2)
   - software: RATRAN
   - assumption: CO/C18O = 550; 13CO/C18O ~8  
  > "assuming an abundance ratio of CO/C [18] O=550" (3.2)
   - fitting: _not stated_
   - validation: Compared with original Qi et al. 2011 model; fit imperfect in inner disk  
  > "The fit is not perfect, however" (3.2)

## Software

- **CASA** 4.2: Reduction and calibration  
  > "The visibility data were reduced and calibrated in CASA 4.2." (2. Observations)
- **RATRAN** : Radiative transfer and excitation  
  > "We use the two-dimensional Monte Carlo software RATRAN" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N2H+ ring inner radius | 90 | +8/-6 | AU | 2 | We find R in =90 [+8] −6 [AU.] |
| N2H+ N100 | 2.6e11 | 0.1e11 | cm^-2 | 2 | the N 2 H [+] column density is 2.6±0.1 ×10 [11] cm [−][2] at 100 AU |
| DCO+ inner radius | 40 | +6/-3 | AU | 2 | inner abundance boundary at 40 [+6] −3 [AU] |
| DCO+ outer radius | 290 | +6/-8 | AU | 2 | 290 [+6] −8 |
| CO freeze-out temperature | 25-26 | not stated | K | 3 | We find a best-fit T CO = 25 − 26 K, which occurs at a radius of 85–90 AU |
| CO depletion factor | about 5 | not stated | dimensionless | 3 | the depletion factor is about 5 |

## Qualitative findings

- 13CO-based 155 AU snow line reflects opacity transition, not a CO drop  
  > "rapid changes in line opacities can masquerade as snow lines" (3.2)

## Claim tuples

- H: N2H+ inner ring edge traces the CO snow line | E: Visibility-domain model fit of N2H+ and C18O | R: R_in=90 AU; C18O gives 85-90 AU | F: N2H+ is a robust CO snow line tracer | **supported**
- H: DCO+ edges coincide with the CO snow line | E: Fit DCO+ ring | R: Edges at 40 and 290 AU | F: Relationship is complex | **refuted**
- H: CO freeze-out temperature is the same across disks | E: Compare 25 K to TW Hya 17 K | R: 25 vs 17 K | F: Freeze-out temperature varies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Data give no N2H+ constraints beyond a few hundred AU; C18O fit imperfect in inner disk  
  > "the data provides no constraints on the N 2 H [+] beyond a few hundred AU due to a lack of sensitivity" (3.1)
- Caveat (inferred, ours): Results depend on the adopted Qi et al. 2011 temperature structure
- Caveat (inferred, ours): Parametric abundance profile and fixed vertical boundaries
- Caveat (inferred, ours): Conversion of radius to temperature is model-dependent

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Disk model parameters (in Qi et al. 2011)
- Missing: Fit grid/optimizer details
- Missing: Imaging parameters
- Data volume (inferred): ~20-50 GB for the two projects
- Score (inferred): 3/5, Public data and clear model parameterization, but imaging and fitting details and the disk model are external.
- Rediscovery candidate: no, Requires RATRAN fitting using external disk model; recipe incomplete.

## Links

- Method: Qi et al. (2011) (Disk model and fitting framework)
- Method: Qi et al. (2013b) (N2H+ methodology)
- Companion: Mathews et al. (2013) (Earlier DCO+ imaging of HD 163296)
- Companion: Rosenfeld et al. (2013) (SV data reduction)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.1.00010.SV"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 31,
  "rate": 0.484
 },
 "evidence_ok": true
}
```
