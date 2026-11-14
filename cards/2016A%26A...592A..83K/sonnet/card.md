# Volatile-carbon locking and release in protoplanetary disks. A study of TW Hya and HD 100546

`2016A&A...592A..83K` | Astronomy and Astrophysics 2016 | first author: Kama, M. | arXiv: 1605.05093 | DOI: 10.1051/0004-6361/201526991

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the gas-phase carbon abundance in the warm Herbig disk HD 100546 and the cold T Tauri disk TW Hya, and how are volatile carbon locking and release governed?  
  > "we carry out a comparative analysis of the gas-phase carbon abundance in two systems with a similar age and disk mass, but different central stars: HD 100546 and TW Hya." (abstract)
- Target **HD 100546**: coordinates _not stated_; z/distance 97 ± 4 pc  
  > "The distance, measured with Hipparcos, is 97 ± 4 pc (van Leeuwen 2007)." (3. The sources); distance from Hipparcos (van Leeuwen 2007)  
  > "The distance, measured with Hipparcos, is 97 ± 4 pc (van Leeuwen 2007)." (3. The sources)
- Target **TW Hya**: coordinates _not stated_; z/distance 55 ± 9 pc  
  > "The distance is (55 ± 9) pc (van Leeuwen 2007)" (3. The sources); distance from van Leeuwen 2007  
  > "The distance is (55 ± 9) pc (van Leeuwen 2007)" (3. The sources)

## Data provenance

- ALMA projects: 2011.0.00863.S, 2011.0.00001.SV
- bands: _not stated_
- frequencies and spectral setup: _not stated_
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
- Line: CO 3-2 (ALMA, spatially resolved radial cut) (not stated)
- Other facility **APEX (FLASH, CHAMP+)**: New [CI] 1-0, CO 6-5, C2H and HCO+ detections  
  > "were obtained with the single-pixel FLASH (Heyminck et al. 2006) and 7-pixel CHAMP+ ([C i] 2–1, CO 6–5) receivers" (2. Observations)
- Other facility **ESO FEROS archive**: Optical spectra for HD 100546 photospheric abundances  
  > "Spectra from FEROS (Kaufer et al. 1999) were extracted from the ESO Science Archive." (2. Observations)
- External data: TW Hya spatially resolved CO 3-2 ALMA data  
  > "Constrained by the spatially resolved CO 3–2 data (Rosenfeld et al. 2012)" (5.2 TW Hya: carbon and oxygen are underabundant) [from Rosenfeld et al. 2012]
- External data: HD 100546 ALMA CO 3-2 and continuum measurements  
  > "supplemented with ALMA measurements from Walsh et al. (2014a)" (Appendix C: Summary of observational data) [from Walsh et al. 2014a]
- External data: SED of TW Hya  
  > "The SED of TW Hya was adopted from Andrews et al. (2012, and references therein)." (Appendix C: Summary of observational data) [from Andrews et al. 2012]

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

- Use of DALI for deriving [C]/[H]gas  
  > "The use of DALI for deriving [C]/[H] gas is described in more detail in Kama et al. (2016)." (5. Analysis) [from Kama et al. (2016)]
- Stellar abundance fitting identical to earlier method  
  > "This fitting process is identical to that used by Folsom et al. (2012)." (Appendix A) [from Folsom et al. (2012)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and CO 3-2 radial-profile extraction (done in Walsh et al. 2014a and Rosenfeld et al. 2012; not described)
- How model fits were compared with data (chi2 or other; fit chosen by eye)
- DALI chemical network and parameter grid details
- Which ALMA project corresponds to which source

## Analysis recipe

1. **Fit physical-chemical disk models with DALI**: Source-specific DALI model grids fitted to SED, resolved CO 3-2 radial profile, CO ladder, [OI], [CI], [CII], HD and C2H data  
  > "we have run source-specific model grids using the 2D physical-chemical code, DALI" (5. Analysis)
   - software: DALI
   - parameter: Chemistry evolved to 10 Myr  
  > "We let the chemistry evolve to 10 Myr to match the ages of the two disks." (5. Analysis)
   - assumption: Disk gaps in mm opacity not included in the models  
  > "We do not presently include these in our modelling" (5. Analysis)
   - fitting: Range of well-fitting models chosen by eye, about 100 models per source  
  > "The range of well-fitting models was chosen by eye through con" (5. Analysis)
   - validation: APEX CO 3-2 flux checked against ALMA flux from Walsh et al. 2014a  
  > "We have also checked that the total CO 3–2 line flux in our APEX data is the same as that recovered from the ALMA observation of Walsh et al. (2014a)." (Appendix B)
2. **Analytical model of volatile locking**: Depletion X1 = X0(1-ΔX)^N with mixing time from alpha viscosity and grain size distribution  
  > "X 1 = X 0 × (1 − ∆ X ) N" (6.2 An analytical model of volatile locking)
   - parameter: alpha = 0.01, h = 30 au, c_s = 300 m/s, t_tot = 10 Myr  
  > "further set α = 0.01" (6.2 An analytical model of volatile locking)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DALI** : 2D physical-chemical disk modelling  
  > "the 2D physical-chemical code, DALI (Bruderer et al. 2009, 2012; Bruderer 2013)" (5. Analysis)
- **GILDAS/CLASS** : APEX spectra inspection, baseline subtraction, averaging  
  > "Inspection, baseline subtraction and averaging were done with GILDAS/CLASS" (2. Observations)
- **APECS** : Initial APEX processing  
  > "Initial processing was done using the APECS software (Muders et al. 2006)." (2. Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C]/[H]gas HD 100546 | (0.1-1.5)e-4 | range of well-fitting models | dimensionless | 1 | [C]/[H] gas = (0.1−1.5)×10 [−][4] |
| [C]/[H]gas TW Hya | (0.2-5.0)e-6 | range of well-fitting models | dimensionless | 1 | ratio of (0.2 − 5.0) × 10 [−][6] |
| HD 100546 total disk mass upper limit | ≤0.1 | not stated | Msun | 1 | place an upper limit on the total disk mass of ≤ 0.1 M ⊙ |
| TW Hya best-fit disk gas mass | 2.3e-2 | not stated | Msun | 1 | Our best-fit disk mass, M disk = 2.3 × 10 [−][2] M ⊙ |
| Fractional loss per mixing cycle ΔX | 2e-2 | not stated | dimensionless | 2 | per mixing cycle of ∆ X = 2 × 10 [−][2] |

## Qualitative findings

- HD 100546 gas-phase carbon is at most moderately depleted; TW Hya is strongly depleted in C and O  
  > "is at most moderately depleted compared to the interstellar medium" (abstract)

## Claim tuples

- H: Is gas-phase carbon depleted in both disks? | E: DALI modelling of SED, resolved CO and line fluxes | R: [C]/[H]gas (0.1-1.5)e-4 for HD 100546 and (0.2-5.0)e-6 for TW Hya | F: Warm disk near-interstellar; cold disk depleted by about two orders of magnitude | **supported**
- H: Can vertical mixing plus freeze-out onto settled grains explain the depletion? | E: Analytical model with mixing time and dust size distribution | R: Mixing gives N=200 and ΔX=2e-2, consistent with a settled grain population | F: Model reproduces the TW Hya depletion | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas-to-dust ratio and radial gas extent dominate uncertainty; mm-opacity gaps not modelled  
  > "The two main sources of uncertainty are the radial extent of the gas disk and the gas to dust ratio." (5. Analysis)
- Caveat (inferred, ours): Fits chosen by eye, no formal uncertainties
- Caveat (inferred, ours): ALMA data enter only as literature radial profiles
- Caveat (inferred, ours): Model degeneracy between gas-to-dust ratio and carbon abundance

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: DALI setup and full parameter grid
- Missing: ALMA reduced data or profiles
- Missing: Stellar UV spectra processing
- Data volume (inferred): small; ALMA data used only as literature profiles (<10 GB if reprocessed)
- Score (inferred): 2/5, ALMA data are secondary, taken from other papers, and the models are fitted by eye with an unreleased code setup.
- Rediscovery candidate: no, ALMA part is not reprocessed and the main results depend on DALI modelling chosen by eye.

## Links

- Method: Bruderer et al. 2012; Bruderer 2013 (DALI code)
- Method: Folsom et al. 2012 (Stellar abundance method)
- Companion: Kama et al. (2016) (Large survey with [CI] and CO 6-5 detections; DALI use for [C]/[H]gas)
- Companion: Miotello et al. in preparation (TW Hya companion)
- Related: DISCO (Disk Carbon and Oxygen)

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 24,
  "rate": 0.358
 },
 "evidence_ok": true
}
```
