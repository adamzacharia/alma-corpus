# On the Origin of High-energy Neutrinos from NGC 1068: The Role of Nonthermal Coronal Activity

`2020ApJ...891L..33I` | The Astrophysical Journal Letters 2020 | first author: Inoue, Yoshiyuki | arXiv: 1909.02239 | DOI: 10.3847/2041-8213/ab7661

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Can non-thermal coronal activity in the NGC 1068 nucleus, supported by the mm-excess, explain the IceCube neutrino flux without violating gamma-ray data?  
  > "We check if the reported flux of VHE neutrino is consistent with the revealed properties of the corona non-thermal particles." (1. INTRODUCTION)
- Target **NGC 1068**: coordinates _not stated_; z/distance ~14 Mpc  
  > "It locates at a distance of ∼ 14 Mpc (1′′ ∼ 70 pc, Tully 1988)." (2. OBSERVATIONAL PROPERTIES); distance from Tully 1988  
  > "It locates at a distance of ∼ 14 Mpc (1′′ ∼ 70 pc, Tully 1988)." (2. OBSERVATIONAL PROPERTIES)

## Data provenance

- ALMA projects: 2016.1.00232.S
- bands: Band 6 and 7  
  > "analyzing the latest ALMA band 6 and 7 data" (3. CORONAL SYNCHROTRON EMISSION)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 30 mas beams  
  > "continuum fluxes at 224, 345, and 356 GHz with beam sizes of 30 mas" (3. CORONAL SYNCHROTRON EMISSION)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLBA**: cm-band core fluxes  
  > "based on measurements reported by Gallimore et al. (2004)" (3. CORONAL SYNCHROTRON EMISSION)
- Other facility **IceCube**: neutrino spectrum of NGC 1068  
  > "The data is taken from Fig. 7 of IceCube Collaboration et al. (2019)" (4. CORONAL GAMMA-RAY AND NEUTRINO EMISSION)
- Other facility **Fermi-LAT, MAGIC**: gamma-ray data  
  > "observed gamma-ray data (The Fermi-LAT collaboration 2019; Ajello et al. 2017; MAGIC Collaboration et al. 2019)" (4. CORONAL GAMMA-RAY AND NEUTRINO EMISSION)
- External data: ALMA core fluxes 6.6±0.3 mJy at 256 GHz and 13.8±1.0 mJy at 694 GHz  
  > "detected 6.6 ± 0.3 mJy and 13.8 ± 1.0 mJy flux from the core at 256 GHz and 694 GHz, respectively" (2. OBSERVATIONAL PROPERTIES) [from García-Burillo et al. 2016; Impellizzeri et al. 2019]
- External data: VLBA cm-band flux 5.9±0.5 mJy, spectral index -0.17  
  > "reported the flux of 5.9 ± 0.5 mJy with a spectral index of −0.17 above 5 GHz" (2. OBSERVATIONAL PROPERTIES) [from Gallimore et al. 2004]
- External data: Intrinsic 2-10 keV luminosity 7×10^43 erg/s adopted  
  > "we take the value of L X = 7 × 10 [43] erg s −1" (2. OBSERVATIONAL PROPERTIES) [from Marinucci et al. 2016]

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

- Coronal parameters (f_nth, temperature, optical depth, injection) and the gamma-ray/neutrino model follow the earlier model  
  > "We follow the assumptions on the coronal parameters as in Inoue et al. (2019)" (4. CORONAL GAMMA-RAY AND NEUTRINO EMISSION) [from Inoue et al. 2019]

### Not stated but needed to reproduce (our reading)

- How the 224, 345 and 356 GHz fluxes were measured from the ALMA data (calibration, imaging, flux extraction)
- Flux values and uncertainties for the new points
- Model code and fitting procedure for the synchrotron fit
- Free-free component parameters used in the fit

## Analysis recipe

1. **Build cm-mm spectrum**: Combine literature VLBA/ALMA fluxes with new ALMA continuum fluxes  
  > "we obtain the continuum fluxes at 224, 345, and 356 GHz with beam sizes of 30 mas" (3. CORONAL SYNCHROTRON EMISSION)
   - fitting: _not stated_
   - validation: _not stated_
2. **Model mm-excess with coronal synchrotron plus free-free**: Coronal synchrotron model on top of pc-scale free-free  
  > "The excess of NGC 1068 can be reproduced with the coronal synchrotron emission model" (3. CORONAL SYNCHROTRON EMISSION)
   - parameter: R_c = 10 R_s, B = 100 G, p = 2.7  
  > "the corona size R c = 10 R s, the magnetic field strength B = 100 G, and the spectral index of non-thermal electrons p = 2.7" (3. CORONAL SYNCHROTRON EMISSION)
   - assumption: SMBH mass 5×10^7 Msun; f_nth = 0.03; coronal temperature 100 keV; optical depth 1.1  
  > "We fix the energy fraction of non-thermal electrons as f nth = 0.03" (3. CORONAL SYNCHROTRON EMISSION)
   - fitting: _not stated_
   - validation: A softer index would violate ALMA measurements or the 351 GHz upper limit  
  > "A much softer spectral index would violate either the ALMA measurements or the flux upper limit at 351 GHz" (3. CORONAL SYNCHROTRON EMISSION)
3. **Predict gamma-ray and neutrino spectra**: Inoue et al. 2019 corona model with uniform and screened internal attenuation, EBL attenuation, varying gyrofactor  
  > "we plot the model curve region in the range of 30 ≤ η g ≤ 3 × 10 [4] for each curve" (4. CORONAL GAMMA-RAY AND NEUTRINO EMISSION)
   - assumption: Equal injection power in protons and electrons  
  > "The injection powers both in protons and electrons are set to equal" (4. CORONAL GAMMA-RAY AND NEUTRINO EMISSION)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Corona size | 10 | not stated | R_s | 2 | the corona size R c = 10 R s |
| Magnetic field | 100 | not stated | G | 2 | the magnetic field strength B = 100 G |
| Electron spectral index | 2.7 | not stated | dimensionless | 2 | the spectral index of non-thermal electrons p = 2.7 |
| Allowed gyrofactor range | 30 to 3e4 | not stated | dimensionless | 3 | the gyro factor in the range of 30 ≤ η g ≤ 3 × 10 [4] |

## Qualitative findings

- Only a screened corona avoids violating the low-energy gamma-ray data; MeV gamma-ray missions can test the model  
  > "In order not to violate the observed gamma-ray data, the corona can not be uniform." (5. DISCUSSIONS AND CONCLUSION)

## Claim tuples

- H: Coronal synchrotron emission explains the mm-excess in NGC 1068 | E: Add coronal synchrotron to free-free and compare with the cm-mm spectrum | R: R_c=10 R_s, B=100 G, p=2.7 reproduce the excess | F: Consistent, though no firm detection is claimed | **partially**
- H: The corona can produce the IceCube neutrino flux | E: Predict neutrino and gamma-ray spectra for 30≤η_g≤3e4 | R: Coronal emission can explain the neutrino flux in the screened case | F: Neutrinos can come only from the SMBH vicinity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: X-ray binaries cannot supply the neutrino flux; their number is several orders of magnitude too low  
  > "thus their number is not sufficient at least by several orders of magnitude" (1. INTRODUCTION)
- How they decided it was enough: _not stated_
- Limitation (authors): No firm detection of the mm-excess owing to few flux measurements, mixed beam sizes and complex structure  
  > "because of a paucity of flux measurements, mixture of beam sizes, and the complex source structure" (3. CORONAL SYNCHROTRON EMISSION)
- Caveat (inferred, ours): Fit is not quantitative; no uncertainties on the parameters
- Caveat (inferred, ours): Black hole mass and X-ray luminosity are uncertain
- Caveat (inferred, ours): Free-free contribution is poorly constrained

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: New ALMA flux values and extraction method
- Missing: Model code and fit details
- Data volume (inferred): tens of GB
- Score (inferred): 2/5, Mostly theoretical; the ALMA analysis is described in one sentence.
- Rediscovery candidate: no, The ALMA recipe is not given and the results are model parameters.

## Links

- Method: Inoue & Doi 2018 (coronal synchrotron mm-excess approach)
- Method: Inoue et al. 2019 (gamma-ray and neutrino corona model)
- Companion: García-Burillo et al. 2019 (source of the 2016.1.00232.S data)

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 22,
  "rate": 0.338
 },
 "evidence_ok": true
}
```
