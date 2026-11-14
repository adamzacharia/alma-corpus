# Detection of CI line emission towards the oxygen-rich AGB star omi Ceti

`2018A&A...612L..11S` | Astronomy and Astrophysics 2018 | first author: Saberi, M. | arXiv: 1804.09958 | DOI: 10.1051/0004-6361/201833080

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: evolved_stars, astrochemistry
- Question: Is CI emission present in the envelope of the O-rich AGB star omi Cet, and does it trace external ISRF dissociation or internal UV from the binary companion?  
  > "CI can be used to trace sources of ultraviolet (UV) radiation in CSEs." (abstract)
- Target **omi Cet (Mira AB)**: coordinates _not stated_; z/distance 92 pc  
  > "which is reported to be at a distance of 92 pc (cite: vanLeeuwen07)" (2.1 omi Cet); distance from van Leeuwen 2007  
  > "which is reported to be at a distance of 92 pc (cite: vanLeeuwen07)" (2.1 omi Cet)
- Target **V Hya**: coordinates _not stated_; z/distance 380 pc  
  > "It is located at a distance of 380 pc (cite: Perryman97)" (2.2 V Hya); distance from Perryman et al. 1997  
  > "It is located at a distance of 380 pc (cite: Perryman97)" (2.2 V Hya)

## Data provenance

- ALMA projects: 2012.1.00524.S, 2013.1.00047.S
- bands: CO(3-2) (Band 7)  
  > "We combined the CO(3-2) ALMA observations" (4.1.2 Constraining the CI emitting region)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.28 arcsec (combined CO(3-2))  
  > "to reach an angular resolution of 0.28$''$" (4.1.2 Constraining the CI emitting region)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PIs Ramstedt and Planesas  
  > "2012.1.00524.S (PI: Ramstedt) and 2013.1.00047.S (PI: Planesas)" (4.1.2 Constraining the CI emitting region)
- Line: CI 3P1-3P0 (492.16 GHz)
- Line: CO J=3-2 (ALMA) (not stated)
- Other facility **APEX/SHeFI**: CI(1-0) spectra of omi Cet and V Hya  
  > "on the APEX[^1] 12-meter telescope (cite: Gusten06) located on Llano Chajnantor in northern Chile in Aug 2017" (Observations)
- Other facility **JCMT**: CO(2-1,3-2,4-3) lines modelled  
  > "we could reasonably model the CO($J$=2-1,3-2,4-3) emission lines observed by JCMT" (4.1.1 The circumstellar model)
- External data: CSE physical properties from CO RT modelling (Table 3)  
  > "We adopt the physical properties of the CSE from CO RT modelling results obtained by RS01; see Table 3 in that paper." (4.1.1 The circumstellar model) [from Ryde & Schöier 2001 (cite: Ryde01)]
- External data: CI collisional data with H2  
  > "The collisional data are taken from (cite: Schroder91)." (4.1.1 The circumstellar model) [from (cite: Schroder91)]
- External data: Stellar velocity V_LSR  
  > "The stellar velocity $V_{\rm LSR}$ was taken from (cite: Khouri16)." (Table 2) [from (cite: Khouri16)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 20% (APEX)  
  > "The uncertainty on the absolute intensity scale is estimated to be 20 $\%$." (Observations)
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

- CSE properties, temperature profile, CO/H2 from RS01 model  
  > "We assumed the temperature profile T(r) = 150 (10$^{15}$/r) as given by RS01." (4.1.3 The CI abundance in the postulated emitting region) [from Ryde & Schöier 2001 (cite: Ryde01)]
- H2 density from constant mass loss and expansion velocity  
  > "The H$_2$ number density is calculated assuming a constant mass-loss rate and constant expansion velocity as in (cite: Schier00)." (4.1.3 The CI abundance in the postulated emitting region) [from (cite: Schier00)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version and imaging parameters for the CO(3-2) data
- How the two ALMA projects were combined
- Channel width and rms of the ALMA map
- Source coordinates
- Chemical network details (Saberi et al. in prep)
- How the 0.2 arcsec emitting radius was measured from the map
- Baseline polynomial fitting windows and spectral resolution of APEX data

## Analysis recipe

1. **Reduce APEX CI spectra and fit line**: Convert T_A* to T_mb, subtract first-order baseline, fit Gaussian  
  > "A first-order polynomial baseline was subtracted from the averaged spectra." (Observations)
   - software: GILDAS/CLASS
   - parameter: eta_mb = 0.60  
  > "| CI(1-0) | APEX | 492.16 | 0.60 | 12.67 | 23.62 |" (Table 1)
   - fitting: Gaussian line profile  
  > "were found by fitting a Gaussian line profile to the data." (Table 2)
   - validation: _not stated_
2. **Shell chemistry plus non-LTE RT model**: Chemical model gives 12C and 13C abundance profiles used as input to Monte Carlo non-LTE RT  
  > "We used the $^{12}$C and $^{13}$C abundance distributions that are shown in Fig. [3](#Chemi) as input files in the mcp." (4.1.1 The circumstellar model)
   - software: mcp, UCL_CHEM-type CSE chemical model (McElroy13)
   - parameter: mass-loss 2.5e-7 Msun/yr, v_exp 2.5 km/s, 12CO/H2=5e-4, 13CO/H2=5e-5  
  > "We assumed the initial fractional abundances of $^{12}$CO/H$_2$=5$\times$10$^{-4}$ reported for omi Cet (RS01)" (Chemical modelling results)
   - assumption: Spherical uniformly expanding envelope, ISRF only external UV  
  > "we assume a uniformly expanding spherical envelope which is formed due to a constant mass-loss" (4.1.1 The circumstellar model)
   - fitting: _not stated_
   - validation: CO(2-1,3-2,4-3) JCMT lines reasonably reproduced  
  > "Although the model reasonably reproduces the CO observations" (4.1.1 The circumstellar model)
3. **Locate emitting region in ALMA CO(3-2)**: Inspect combined ALMA CO(3-2) channel map at v_LSR=43.3 km/s  
  > "there are three components that peak around Mira A, Mira B, and the north part of the Mira AB system in the CO(3-2) emission." (4.1.2 Constraining the CI emitting region)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive CI column density near Mira B**: RADEX with dilution correction; column density is the only free parameter  
  > "The only free parameter in this modelling is the CI column density." (4.1.3 The CI abundance in the postulated emitting region)
   - software: RADEX
   - parameter: T_kin 170 K, n(H2) 1.9e6 cm-3, line width 9.5 km/s, T_bg 2.73 K  
  > "| 2.73 | 170 | 1.9E6 | 9.5 | 1.1E19 |" (Table 3)
   - assumption: Emission region 0.4 arcsec; dilution factor ~0.001; position r=60 AU  
  > "With a telescope beam size of $\sim$13$''$ and assuming an emission region of 0.4$''$, we get a dilution factor of $(0.4/13)^2\sim 0.001$." (4.1.3 The CI abundance in the postulated emitting region)
   - fitting: Match corrected T_mb of 54 K  
  > "This leads to a corrected main beam temperature of 0.054 / 0.001 = 54 K." (4.1.3 The CI abundance in the postulated emitting region)
   - validation: T_R changes <10% over n_H2 1e6-1e12 and T_kin 100-500 K  
  > "T$_{\rm R}$ does not change more than 10 $\%$ over ranges of $1\times10^6<n_{\rm H_2}<1\times10^{12}$ cm$^{-3}$ and $100 <T_{\rm kin}<500$ K." (4.1.3 The CI abundance in the postulated emitting region)

## Software

- **GILDAS/CLASS** : APEX data reduction  
  > "We used the GILDAS/CLASS[^2] package to reduce the data." (Observations)
- **RADEX** : CI column density  
  > "The publicly available non-LTE RT code RADEX[^4] is used to model the CI emission." (4.1.3 The CI abundance in the postulated emitting region)
- **mcp** : non-LTE Monte Carlo RT of CI  
  > "A non-local thermodynamic equilibrium (non-LTE) RT code based on the Monte Carlo program (mcp) (cite: Bernes79; Schier01) was used" (4.1.1 The circumstellar model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CI integrated intensity omi Cet | 0.55 | 0.07 | K km/s | 1 | / omi Cet / 47.2 / 43.4$\pm$0.6 / 0.55$\pm$0.07 / 0.054 / 9.5$\pm$1.3 / |
| CI central velocity | 43.4 | 0.6 | km/s | 1 | / omi Cet / 47.2 / 43.4$\pm$0.6 / 0.55$\pm$0.07 / 0.054 / 9.5$\pm$1.3 / |
| CI FWHM | 9.5 | 1.3 | km/s | 1 | / omi Cet / 47.2 / 43.4$\pm$0.6 / 0.55$\pm$0.07 / 0.054 / 9.5$\pm$1.3 / |
| CI column density near Mira B | 1.1e19 | not stated | cm-2 | 4 | a CI column density of $1.1\times10^{19}$ cm$^{-2}$ is needed for the component near to Mira B |
| CI/H2 with 100x overdensity | ~1.1e-4 | not stated | dimensionless | 4 | then our measurement implies a fractional abundance CI/H$_2$ $\sim1.1\times 10^{-4}$ in this location. |
| CI/CO with 100x H2 enhancement | ~0.2 | not stated | dimensionless | 4 | we find a ratio CI/CO $\sim$ 0.2 |
| Peak CI abundance in shell model | 2.4e-5 | not stated | dimensionless | 2 | a peak atomic fractional abundance of 2.4 $\times$ 10$^{-5}$ |

## Qualitative findings

- First CI detection in an O-rich AGB star; CI tentative detection in V Hya confirmed  
  > "This is the first time that CI is detected in the envelope around an oxygen-rich M-type asymptotic giant branch (AGB) star." (abstract)

## Claim tuples

- H: CI in omi Cet arises from a shell dissociated by the ISRF | E: Chemical plus non-LTE RT shell model compared with APEX spectrum | R: Flux reproduced but line is narrower and ~4 km/s shifted | F: ISRF shell cannot explain velocity shift or width, but not ruled out | **partially**
- H: CI arises near Mira B | E: ALMA CO(3-2) map plus RADEX | R: N(CI)=1.1e19 cm-2, CI/CO~0.2 with overdensity | F: Companion UV and/or accretion likely enhances CI; needs high-resolution confirmation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CI from Mira A shell or the north clump rejected as less likely: velocity shift unexplained, no UV source near clump  
  > "There are no known sources of UV- or shock-dissociation near the clump in the north part that cause the enhancement of the CI emission." (4.1.2 Constraining the CI emitting region)
- How they decided it was enough: _not stated_
- Limitation (authors): Single-dish data cannot constrain the complex outflow; the CSE model is crude  
  > "it is not possible to constrain the complex outflow around omi Cet based on the single-dish observations" (4.1.1 The circumstellar model)
- Caveat (inferred, ours): Emitting region size and H2 overdensity are assumed, so CI/H2 and CI/CO are weakly constrained
- Caveat (inferred, ours): ALMA data used only qualitatively with no processing described
- Caveat (inferred, ours): Shell model velocity mismatch may reflect wrong kinematics rather than a companion origin

## Reproducibility

- Data public (paper): ALMA projects cited by code; APEX project ID given  
  > "(project ID: O-0100.F-9317A-2017)" (Observations)
- Products in archive: _not stated_
- Missing: ALMA reduction and imaging details
- Missing: Extended chemical network (in prep)
- Missing: Fitted spectra and baseline details
- Data volume (inferred): ~10-100 GB for the ALMA CO(3-2) data; APEX spectra are small
- Score (inferred): 3/5, The APEX part is simple with a stated RADEX setup, but the ALMA part is undocumented and the chemical model is unpublished.
- Rediscovery candidate: no, ALMA processing is not described and the key numbers depend on the APEX data and an in-prep chemical model.

## Links

- Method: McElroy et al. 2013 (cite: McElroy13) (CSE chemical model code)
- Method: Schöier & Olofsson 2001 (cite: Schier01) (Monte Carlo RT code)
- Companion: Ramstedt et al. 2014 (cite: Ramstedt14) (CO(3-2) observations of the Mira AB bubble)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
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
  "facts": 76,
  "stated": 36,
  "rate": 0.474
 },
 "evidence_ok": true
}
```
