# Possible planet formation in the young, low-mass, multiple stellar system GG Tau A

`2014Natur.514..600D` | Nature 2014 | first author: Dutrey, Anne | arXiv: - | DOI: 10.1038/nature13822

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Is cold CO gas present in the GG Tau A inner cavity, can it replenish the inner disc, and what is the dust temperature of the circumbinary ring?  
  > "Here we report imaging of massive CO-emitting gas fragments within the GG Tau-A cavity." (abstract)
- Target **GG Tau A**: coordinates RA 04:32:30.359, Dec +17:31:40.38 (J2000, map reference)  
  > "The 1-5 Million year old [12,13] triple stellar system GGTau-A is located at 140 pc in a hole" (main text); "Positions are relative to R.A. = 04:32:30.359 and Dec. = 17:31:40.38 (J2000)." (Figure 1 caption); z/distance 140 pc  
  > "The 1-5 Million year old [12,13] triple stellar system GGTau-A is located at 140 pc in a hole" (main text); "Positions are relative to R.A. = 04:32:30.359 and Dec. = 17:31:40.38 (J2000)." (Figure 1 caption); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00059.S
- bands: Band 9 (0.45 mm)  
  > "Band 9 on August 13 2012." (Methods)
- frequencies and spectral setup: 4 spectral windows, total width 0.938 GHz, centered at 691.485, 689, 676 and 674 GHz; 244 kHz channels (0.11 km/s)  
  > "The spectral setup was of 4 spectral windows of total width 0.938" (Methods); "yielding a channel spacing of 244 kHz, or 0.11 km/s." (Methods)
- continuum bandwidth: _not stated_
- arrays: 23 antennas, extended configuration  
  > "The array of 23 antennas was in its extended configuration." (Methods)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: about 0.25 arcsec (~35 au)  
  > "with an angular resolution" (main text)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: August 13 2012  
  > "Band 9 on August 13 2012." (Methods)
- pi or archival as stated: _not stated_
- Line: CO J=6-5 (not stated)
- Other facility **IRAM PdBI**: CO J=2-1 and 1.3 mm continuum images; 3 mm data from earlier work  
  > "We complement ALMA data with CO J=2-1 and continuum images from the IRAM" (Methods)
- External data: Proper motions (17, 19) mas/yr used to merge datasets  
  > "we adopted proper motions of (17," (Methods) [from Ducourant et al. 2005 (ref 28)]
- External data: Previous 1.3 and 3.4 mm continuum maps and CO data  
  > "existing 1.3 and 3.4 mm" (main text) [from refs 14, 21]

## Processing

### Calibration

- pipeline or manual: calibrated using CASA, exported via UVFITS  
  > "The ALMA data were calibrated using CASA then exported through" (Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres  
  > "The absolute flux scale" (Methods)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: imaged and analysed with GILDAS  
  > "UVFITS to be imaged and analysed using GILDAS." (Methods)
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
- final beam: 0.29 x 0.25 arcsec at PA 68 deg (CO 6-5)  
  > "The beam size is" (Extended Data Figure 1)
- final rms: _not stated_

### Inherited from earlier work

- Dust model fitting with Diskfit and Levenberg-Marquardt  
  > "We use Diskfit, a radiative transfer code dedicated to the mod" (Methods) [from Boehler et al. 2013 (ref 36); Pietu et al. 2007 (ref 37)]
- Velocity offset corrected using IRAM CO 2-1 data  
  > "We corrected the" (Methods) [from existing IRAM data]

### Not stated but needed to reproduce (our reading)

- Imaging weighting, cell and image size, cleaning parameters
- Continuum channel selection for the ALMA data
- Bandpass and gain calibrators and CASA version
- Diskfit parameter priors and ranges
- Baseline range and flux scale uncertainty of the ALMA data

## Analysis recipe

1. **Calibrate, correct velocity offset and image**: CASA calibration, GILDAS imaging; velocity offset 0.97 km/s corrected against IRAM CO 2-1  
  > "The velocity difference was 0" (Methods)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Flux loss estimated with ALMA simulator  
  > "using the ALMA simulator" (Methods)
2. **CO excitation and clump masses**: RADEX escape probability calculations; CO/H2 = 1e-4  
  > "We performed escape probability calculations using the" (Methods)
   - software: RADEX
   - assumption: standard CO/H2 ratio of 1e-4  
  > "With a standard CO/H2 ratio of 10" (Methods)
   - fitting: _not stated_
   - validation: consistent with pre-shock densities from H2 shock models  
  > "These densities agree with the pre" (Methods)
3. **Fit circumbinary dust ring**: Diskfit in the Fourier plane to 3 mm, 1.3 mm and 0.45 mm data with truncated power-law surface density and temperature  
  > "The analysis is performed in the Fourier plane to avoid non linear effects due to the deconvolution." (Methods)
   - software: Diskfit
   - assumption: gas-to-dust 100, kappa(1.3 mm)=0.02 cm2/g  
  > "Gas-to-Dust Ratio G/D 100" (Extended Data Table 2)
   - fitting: modified Levenberg-Marquardt, 1 sigma errors from covariance matrix  
  > "A modified Levenberg-Marquardt scheme with step adjustment is used to derive the best fit" (Methods)
   - validation: results robust to 20% flux calibration error at 0.45 mm  
  > "we checked that the results remain robust even assuming an absolute" (Methods)

## Software

- **CASA** : calibration  
  > "The ALMA data were calibrated using CASA" (Methods)
- **GILDAS** : imaging and analysis  
  > "imaged and analysed using GILDAS." (Methods)
- **RADEX** : CO excitation  
  > "using the" (Methods)
- **Diskfit** : dust disc modelling  
  > "We use Diskfit, a radiative transfer code" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust temperature T200 | 13.8 | 0.3 | K | 3 | Dust Temperature T 200 13.8 ± 0.3 K |
| Temperature exponent q | 1.1 | 0.1 | dimensionless | 3 | exponent q 1.1 ± 0.1 |
| Dust spectral index beta | 1.0 | 0.1 | dimensionless | 3 | We found a value for the spectral index |
| Mass per CO 6-5 clump | ~5e-5 | not stated | Msun | 2 | The mass of each CO |
| Velocity offset ALMA vs IRAM | 0.97 | 0.01 | km/s | 1 | The velocity difference was 0 |

## Qualitative findings

- CO gas fragments in the cavity feed the Aa disc; a CO hot spot at the ring outer edge may mark a proto-planet  
  > "We suggest that this localized emission" (main text)

## Claim tuples

- H: Gas streamers in the cavity replenish the inner disc | E: ALMA CO 6-5 imaging with kinematics | R: ~5e-5 Msun clumps; about 20 clumps in Aa disc mass | F: Replenishment can sustain the Aa disc beyond accretion lifetime | **supported**
- H: Dust temperature of the ring can be measured directly | E: Multi-wavelength Diskfit including 0.45 mm | R: T=13.8 K (r/200 au)^-1.1 | F: Very cold outer disc | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: GG Tau B perturbation judged unlikely to cause the hot spot  
  > "it is unlikely that GG Tau B would have induced such a sizeable disturbance" (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short baselines cause flux loss, precluding quantitative large-scale CO 6-5 analysis  
  > "uncertainties on the amount of flux loss preclude any quantitative analysis" (Methods)
- Caveat (inferred, ours): Hot spot interpretation as proto-planet is speculative
- Caveat (inferred, ours): Velocity offset origin unknown
- Caveat (inferred, ours): Limited resolution of 35 au

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Diskfit setup details
- Missing: Unpublished IRAM extended-configuration data
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Nature letter with a concise Methods; imaging details are missing, but the Cycle 0 data are archival.
- Rediscovery candidate: no, Imaging recipe incomplete and IRAM data are partly unpublished.

## Links

- Method: Boehler et al. 2013 (ref 36) (Diskfit)
- Companion: Di Folco et al. 2014 (ref 8) (triple nature of GG Tau A)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 33,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
