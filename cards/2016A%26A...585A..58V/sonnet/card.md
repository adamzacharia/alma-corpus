# Resolved gas cavities in transitional disks inferred from CO isotopologs with ALMA

`2016A&A...585A..58V` | Astronomy and Astrophysics 2016 | first author: van der Marel, N. | arXiv: 1511.07149 | DOI: 10.1051/0004-6361/201526988

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the size, depth and shape of the gas cavity inside the dust cavities of four transition disks, and what do they imply for embedded planets and disk viscosity?  
  > "The goals of this study are to determine the gas surface density profile, specificially the size, depth, and shape of the gas density structure inside the dust cavity, to constrain the properties of potential embedded planets." (Introduction)
- Target **HD135344B**: coordinates 15:15:48.42 -37:09:16.36 (J2000, derived)  
  > "| HD135344B | F4 | 7.8 | 1.6 | 2.2 | 6590 | $6\cdot10^{-9}$ | 140 | 0.3 | 1,2,3 |" (Table 1); z/distance 140 pc  
  > "| HD135344B | F4 | 7.8 | 1.6 | 2.2 | 6590 | $6\cdot10^{-9}$ | 140 | 0.3 | 1,2,3 |" (Table 1); distance from _not stated_
- Target **SR21**: coordinates 16:27:10.27 -24:19:13.04 (J2000, derived)  
  > "| SR21 | G3 | 10 | 1.0 | 3.2 | 5830 | $<1\cdot10^{-9}$ | 120 | 6.3 | 4,5,6 |" (Table 1); z/distance 120 pc  
  > "| SR21 | G3 | 10 | 1.0 | 3.2 | 5830 | $<1\cdot10^{-9}$ | 120 | 6.3 | 4,5,6 |" (Table 1); distance from _not stated_
- Target **DoAr44**: coordinates 16:31:33.46 -24:27:37.53 (J2000, derived)  
  > "| DoAr44 | K3 | 1.4 | 1.3 | 1.75 | 4730 | $9\cdot10^{-9}$ | 120 | 2.2 | 5,6 |" (Table 1); z/distance 120 pc  
  > "| DoAr44 | K3 | 1.4 | 1.3 | 1.75 | 4730 | $9\cdot10^{-9}$ | 120 | 2.2 | 5,6 |" (Table 1); distance from _not stated_
- Target **IRS48**: coordinates 16:27:37.18 -24:30:35.39 (J2000, derived)  
  > "| IRS48 | A0 | 14.3 | 2.0 | 1.3 | 10000 | $4\cdot10^{-9}$ | 120 | 11.5 | 7,8 |" (Table 1); z/distance 120 pc  
  > "| IRS48 | A0 | 14.3 | 2.0 | 1.3 | 10000 | $4\cdot10^{-9}$ | 120 | 11.5 | 7,8 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00158.S, 2013.1.00100.S
- bands: Band 7 (~335 GHz) for SR21, HD135344B, DoAr44; Band 9 (~680 GHz) for IRS48  
  > "IRS 48 was observed in ALMA Cycle 2 program 2013.1.00100.S (PI van der Marel) in Band 9 ($\sim$680 GHz or 440 $\mu$m)" (2.1 Observational details)
- frequencies and spectral setup: Band 7: three 469 MHz windows (0.1 km/s channels) on 13CO, C18O, CN 3-2 plus 1875 MHz continuum window; Band 9: three 937.5 MHz windows on 13CO 6-5, C18O 6-5, H2CO 9-8 plus 1875 MHz continuum window  
  > "three windows have a bandwidth of 469 MHz (channel width 122 kHz, equivalent to 0.1 km s$^{-1}$), centered on the $^{13}$CO 3–2, C$^{18}$O 3–2, and CN 3–2 transitions" (2.1 Observational details)
- continuum bandwidth: ~3.2 GHz (Band 7); ~4.7 GHz (Band 9)  
  > "The total continuum bandwidth was $\sim$4.7 GHz." (2.1 Observational details)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20 to 1100 m, scales 0.15 to 8 arcsec  
  > "with baselines ranging from 20 to 1100 m, probing scales from 0.15 to 8 arcseconds" (2 Data)
- angular resolution: 0.2-0.25" (Band 7); 0.15-0.2" (Band 9)  
  > "with a resulting spatial resolution of 0.15–0.2"." (2.1 Observational details)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 30 min each SR21 and DoAr44; 54 min HD135344B; 52 min IRS48  
  > "The total on-source integration time was 30 minutes each for SR 21 and DoAr 44, and 54 minutes for HD 135344B." (2.1 Observational details)
- observing dates: June and July 2014  
  > "The observations were obtained during ALMA Cycle 1 and 2 in June and July 2014" (2 Data)
- pi or archival as stated: _not stated_
- Line: 13CO 3-2 (330.58796 GHz)
- Line: C18O 3-2 (329.33056 GHz)
- Line: 13CO 6-5 (661.067276 GHz)
- Line: C18O 6-5 (658.553278 GHz)
- Other facility **VISIR**: 18 micron image used to constrain IRS48 dust  
  > "the total submillimeter flux, the VISIR 18$\mu$m image and the SED are again used to constrain the dust density and dust cavity radius" (4.1 Results for individual targets)
- External data: Best-fit dust/vertical structure models for SR21 and HD135344B (SED, 690 GHz continuum, 12CO 6-5)  
  > "The best-fit models from Table 4 in (cite: vanderMarel2015-12co) were used as initial model for the vertical structure and dust density structure for SR21 and HD135344B" (3.2 Model-fitting approach) [from (cite: vanderMarel2015-12co)]
- External data: IRS48 model  
  > "For IRS48, we used the model derived by (cite: Bruderer2014)" (3.2 Model-fitting approach) [from (cite: Bruderer2014)]
- External data: SR21 7 AU gas cavity from CO rovibrational spectroastrometry  
  > "we adopt the value from CO rovibrational spectroastrometry by (cite: Pontoppidan2008)" (Table 2 notes) [from (cite: Pontoppidan2008)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.1  
  > "The data were calibrated and imaged in CASA version 4.2.1." (2.1 Observational details)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (HD135344B), Titan (SR21, DoAr44), J1517-243 (IRS48)  
  > "The flux was calibrated using J1517-243, the bandpass with J1427-4206 and the gain with J1626-2951." (2.1 Observational details)
- flux scale uncertainty: _not stated_
- self calibration: amplitude and phase self-calibration after standard phase referencing  
  > "amplitude and phase self-calibration was performed after standard phase referencing" (2.1 Observational details)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The data were cleaned using Briggs weighting with a robust factor of 0.5" (2.1 Observational details)
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
- final beam: ~0.25"x0.20" (Cycle 1), ~0.19"x0.15" (Cycle 2)  
  > "resulting in a beam size of $\sim0.25"\times0.20"$ (Cycle 1 data) and $\sim0.19"\times0.15"$ (Cycle 2 data)" (2.1 Observational details)
- final rms: _not stated_

### Inherited from earlier work

- Physical disk model structure and dust/stellar details  
  > "As a starting point for our models we adopted the physical structure suggested by (cite: Andrews2011), as implemented by (cite: Bruderer2013) and fully described in (cite: vanderMarel2015-12co)." (3.1 Physical model) [from (cite: Andrews2011); (cite: Bruderer2013); (cite: vanderMarel2015-12co)]
- DoAr44 dust modeling approach  
  > "Using the same approach as in (cite: vanderMarel2015-12co), a model was found by fitting the SED, the 345 GHz continuum visibility curve, and the 345 GHz continuum intensity cuts." (Dust model DoAr44) [from (cite: vanderMarel2015-12co)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and reference antenna
- Clean masks, thresholds, line-free channels and continuum subtraction method
- Full DALI input parameters (stellar UV, dust composition, abundances, isotope ratios)
- Model grids tried and how fit quality was judged
- Model fits not released

## Analysis recipe

1. **Make moment maps and derive source geometry**: Zero-moment and first-moment maps of 13CO and C18O; channel maps used to derive stellar position, PA, inclination, v_LSR  
  > "The $^{13}$CO channel maps and velocity maps are used to derive the stellar position, the position angle, inclination, and source velocity" (2.2 Continuum and line maps)
   - software: CASA
   - fitting: _not stated_
   - validation: Consistent with 12CO-derived values  
  > "which are within errors consistent with the values derived from the $^{12}$CO data" (2.2 Continuum and line maps)
2. **Fit physical-chemical model to CO isotopologs by eye**: Adopt prior dust structure; vary surface density, gas-to-dust ratio, outer radius, cavity radius and delta parameters in DALI to match spectra, intensity maps and cuts, including isotope-selective photodissociation  
  > "we used the initial dust structure model and only varied a small number of parameters to fit the CO emission by eye by subsequent adjustments of the surface density, gas-to-dust ratio, outer radius, and the $\delta$ parameters" (3.2 Model-fitting approach)
   - software: DALI
   - parameter: Sigma(r) power law with exponential cutoff, gamma=1  
  > "The surface density $\Sigma(r)$ is assumed to be a radial power-law with an exponential cut-off following the time-dependent viscosity disk model $\nu \sim r^{\gamma}$ with $\gamma=1$" (3.1 Physical model)
   - assumption: Gas and dust follow same density profile with varying gas-to-dust ratio  
  > "The gas and dust follow the same density profile, but the gas-to-dust ratio is varied throughout the disk" (3.1 Physical model)
   - fitting: By eye; no chi2 or MCMC  
  > "We did not use a $\chi^2$ or Markov chain Monte Carlo (MCMC) method because the computational time of the models is too long and the number of parameters too large." (3.2 Model-fitting approach)
   - validation: Small model grid with different cavity radii and delta values; uncertainty within 5 AU and an order of magnitude  
  > "the density and $\delta$ parameters are estimated to be within an order of magnitude and the radial parameters to within 5 AU based on a small model grid" (3.2 Model-fitting approach)
3. **Test gradual-drop surface density profile**: Replace the two-drop profile with an increasing exponential between r_cavdust and r_cavgas and refit delta_gas2  
  > "we ran additional models and replaced the exponential power-law $\Sigma(r)$ by an increasing exponential law between $r_{\rm cavdust}$ and $r_{\rm cavgas}$" (4.2 Gradual drop)
   - software: DALI
   - fitting: _not stated_
   - validation: _not stated_
4. **Infer planet mass and viscosity**: Apply de Juan Ovelar et al. cavity radius ratio relation and Fung et al. (2014) gap depth relation using delta_gas2 and h/r from model midplane temperatures  
  > "Using these values for $h/r$ in combination with the $\delta_{\rm gas2}$ values derived for the gradual drop models for our disks, planet masses can be derived for $\alpha$ between 10$^{-2}$ and 10$^{-4}$." (6 Discussion)
   - assumption: Gas follows small dust; isothermal disk in Fung relation; q valid 1e-4 to 1e-2  
  > "The equation is only valid for $q=10^{-4}-10^{-2}$." (6 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1: calibration and imaging  
  > "The data were calibrated and imaged in CASA version 4.2.1." (2.1 Observational details)
- **DALI** : physical-chemical modeling of gas and dust  
  > "We make use of physical-chemical modeling with DALI (cite: Bruderer2012; Bruderer2013)" (Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD135344B gas cavity radius | 30 | ≲5 AU | AU | 2 | The modeling constrains the gas cavity radius to 30 AU (dust cavity radius is 40 AU), and the drop is $2\cdot10^{-4}$ |
| DoAr44 gas cavity radius | 16 | ≲5 AU | AU | 2 | still show a gas cavity that is only half the size of the dust cavity: 16 AU |
| IRS48 gas cavity radius | 25 | ≲5 AU | AU | 2 | The gas cavity radius is found to be 25 instead of the 20 AU found by (cite: Bruderer2014) |
| HD135344B delta_gas2 | 2e-4 | within an order of magnitude | dimensionless | 2 | / density / $\Sigma_c$ (g cm$^{-2}$) / 120 / 400 / 60 / 0.5 / |
| Derived planet masses (HD135344B, DoAr44, IRS48) | 2, 11, 25 | not stated | M_Jup | 4 | planet masses are predicted to be 2, 11, and 25 $M_{\rm Jup}$ for HD135344B, DoAr44, and IRS48 |
| Gradual-drop delta_gas2 (HD135344B, SR21, DoAr44, IRS48) | 2e-4, 1e-3, 2e-4, 5e-2 | not stated | dimensionless | 3 | we find 2$\cdot10^{-4}$, 10$^{-3}$, 2$\cdot10^{-4}$ , and 5$\cdot10^{-2}$ for HD135344B, SR21, DoAr44, and IRS48 respectively |

## Qualitative findings

- No disk shows gas following the dust; gas cavities are smaller than dust cavities  
  > "To date, no counterexample has been found for which the gas follows the same distribution as the dust." (6 Discussion)

## Claim tuples

- H: Gas cavities are smaller than dust cavities | E: 13CO and C18O imaging plus DALI modeling | R: Gas cavity radii 30, 7 (adopted), 16, 25 AU vs dust 40, 25, 32, 60 AU | F: Gas cavities are smaller than dust cavities | **supported**
- H: Gas density drops strongly inside the cavity | E: DALI fits of isotopolog emission | R: Drops of 1e2 to 1e4 | F: Gas depleted but not empty | **supported**
- H: Disk viscosity is low if planets carve the cavities | E: Fung et al. gap-depth relation with measured drops | R: alpha between 1e-3 and 1e-4 for planets up to 10 M_Jup | F: Low viscosity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Isotopologs are less optically thick than 12CO and better constrain density  
  > "The CO isotopologs provide better constraints on the density than the $^{12}$CO because they are less optically thick ($^{13}$CO) or even optically thin (C$^{18}$O)." (3.2 Model-fitting approach)
- Alternative: Gradual increasing profile as alternative to double drop  
  > "An alternative explanation is a gradual drop or increasing surface density profile inside the cavity." (4.2 Gradual drop)
- How they decided it was enough: _not stated_
- Limitation (authors): No formal uncertainties or uniqueness from fitting; parameter correlations not computed  
  > "Formal uncertainties of model parameters, the uniqueness of the fit and correlation between parameters cannot be computed directly" (3.2 Model-fitting approach)
- Caveat (inferred, ours): By-eye fits with no formal uncertainties
- Caveat (inferred, ours): Planet masses depend on isothermal Fung relation and assumed h/r
- Caveat (inferred, ours): Gas cavity in SR21 is unresolved and adopted from literature

## Reproducibility

- Data public (paper): ALMA data identified by project codes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA/2012.1.00158.S and ADS/JAO.ALMA/2013.1.00100.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: DALI model input files
- Missing: Self-calibration and cleaning details
- Missing: Fit procedure is manual
- Data volume (inferred): ~100-300 GB raw for two projects
- Score (inferred): 3/5, Public data and tabulated best-fit parameters, but by-eye fitting with DALI and missing imaging details.
- Rediscovery candidate: no, Main results come from by-eye radiative transfer fits that are not reproducible algorithmically.

## Links

- Method: (cite: Bruderer2012; Bruderer2013) (DALI code)
- Method: (cite: vanderMarel2015-12co) (Model framework and starting models)
- Companion: (cite: Pinilla2015beta) (Band 9 and Band 7 continuum comparison)
- Companion: (cite: vanderMarel2015vla) (IRS48 continuum)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 44,
  "rate": 0.564
 },
 "evidence_ok": true
}
```
