# Shadows and cavities in protoplanetary disks: HD 163296, HD 141569A, and HD 150193A in polarized light

`2014A&A...568A..40G` | Astronomy and Astrophysics 2014 | first author: Garufi, A. | arXiv: 1406.7387 | DOI: 10.1051/0004-6361/201424262

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What is the morphology of the disks around HD163296, HD141569A and HD150193A in near-IR polarized light, and what causes the observed shadows and cavities?  
  > "We enlarge the sample of protoplanetary disks imaged in polarized light with high-resolution imaging ($\lesssim 0.2\ensuremath{''}$) by observing the Herbig Ae/Be stars HD163296, HD141569A, and HD150193A." (abstract)
- Target **HD163296**: coordinates _not stated_; z/distance d = 122 pc  
  > "HD163296 is an A1 star at $d=122$ pc (cite: vandenAncker1998)" (Introduction); distance from van den Ancker et al. 1998  
  > "HD163296 is an A1 star at $d=122$ pc (cite: vandenAncker1998)" (Introduction)
- Target **HD141569A**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD150193A**: coordinates _not stated_; z/distance d = 150 pc  
  > "HD150193A is an A2 star at $d=150$ pc (cite: vandenAncker1997)" (Introduction); distance from van den Ancker et al. 1997  
  > "HD150193A is an A2 star at $d=150$ pc (cite: vandenAncker1997)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00010.SV
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA DCO+ data: 0.65'' x 0.44''  
  > "the low angular resolution of the ALMA data ($0.65\ensuremath{''} \times 0.44\ensuremath{''}$)" (4.2.4 Dust properties)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: DCO+ not stated (not stated)
- Other facility **VLT/NACO**: H and Ks band polarimetric differential imaging of the three targets  
  > "observed between 2012 July 23 and 25 with VLT/NACO in PDI mode" (Observations and data reduction)
- Other facility **2MASS**: stellar magnitudes for photometric calibration and stellar colour  
  > "using the 2MASS magnitudes (cite: Cutri2003)" (Observations and data reduction)
- External data: DCO+ ALMA emission map of HD163296 (shared ALMA data)  
  > "we show a comparison of the DCO+ emission map from HD163296 (cite: Mathews2013) with our PDI image." (4.2.4 Dust properties) [from Mathews et al. 2013 (cite: Mathews2013)]
- External data: Mid-IR photometry used for flaring-angle correlation  
  > "we used the mid-IR photometry from (cite: Acke2010)" (4.3 Polarized light vs flaring angle) [from Acke et al. 2010 (cite: Acke2010)]

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

- NACO PDI data reduction procedure  
  > "The data were reduced with the procedure described in (cite: Avenhaus2014)." (Observations and data reduction) [from (cite: Avenhaus2014)]
- Photometric calibration method  
  > "The photometric calibration (only accurate to $\sim40\%$) was performed as described by (cite: Quanz2011)." (Observations and data reduction) [from (cite: Quanz2011)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and moment-map details for the DCO+ data (taken from Mathews et al. 2013)
- How the DCO+ map was aligned and the radial profile extracted for Fig. 3
- Exact stellar flux values used in the contrast definition

## Analysis recipe

1. **Compare polarized-light contrast with DCO+ emission**: Compute disk-to-star polarized contrast along the major axis and compare its radial rise with the DCO+ ALMA map  
  > "We use the disk-to-star contrast at a certain radius $r$ defined as" (4.2.4 Dust properties)
   - parameter: Contrast drop factor >~6 between 0.65'' and 0.3''  
  > "we obtain a factor $\Delta \phi_{\rm pol}\gtrsim 6$ difference between $0.65\ensuremath{''}$" (4.2.4 Dust properties)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inclination of HD163296 from PDI | 43 | +9/-14 | deg | 0 | this translates into an inclination $i=43^{\circ \,+9^\circ}_{-14^\circ}$ |
| Polarized contrast drop inside ring | >~6 | not stated | dimensionless | 1 | we obtain a factor $\Delta \phi_{\rm pol}\gtrsim 6$ difference |

## Qualitative findings

- Disk of HD163296 is weakly detected as a broken ring with a surface brightness drop inward of 0.6''; no polarized emission from HD141569A and HD150193A  
  > "The disk is resolved as a broken ring structure with a significant surface brightness drop inward of $0.6\ensuremath{''}$." (abstract)

## Claim tuples

- H: The inner light drop in HD163296 is caused by self-shadowing versus alternatives such as CO ice | E: Compare PDI contrast with DCO+ ALMA map and geometric arguments | R: Contrast rises by >~6 over the same interval where DCO+ rises, but ALMA resolution is low | F: Self-shadowing is favored; CO freeze-out is only tantalizing | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low ALMA angular resolution prevents strong conclusions from spatial coincidence  
  > "prevents us from drawing strong conclusions from the possible spatial coincidence of the two datasets" (4.2.4 Dust properties)
- Caveat (inferred, ours): ALMA used only qualitatively, no quantitative comparison
- Caveat (inferred, ours): Photometric calibration only ~40% accurate

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA DCO+ reduction details
- Missing: NACO reduction code
- Data volume (inferred): small (ALMA part ~ <50 GB)
- Score (inferred): 2/5, ALMA is a minor supporting dataset taken from another paper with no processing details.
- Rediscovery candidate: no, The ALMA role is minor and qualitative; the main data are VLT/NACO.

## Links

- Method: Avenhaus et al. 2014 (cite: Avenhaus2014) (NACO PDI data reduction)
- Companion: Mathews et al. 2013 (cite: Mathews2013) (source of the ALMA DCO+ data)

## Checks

```json
{
 "quotes": 23,
 "quotes_ok": 23,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 16,
  "rate": 0.262
 },
 "evidence_ok": true
}
```
