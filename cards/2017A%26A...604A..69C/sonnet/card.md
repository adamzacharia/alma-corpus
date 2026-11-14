# Herschel survey and modelling of externally-illuminated photoevaporating protoplanetary disks

`2017A&A...604A..69C` | Astronomy and Astrophysics 2017 | first author: Champion, J. | arXiv: 1702.00251 | DOI: 10.1051/0004-6361/201629404

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the physical properties (density, temperature) and heating/cooling processes of the PDR in externally-illuminated photoevaporating disks (proplyds), and what mass-loss rates do they imply?  
  > "What are the physical properties of this PDR (density, temperature)?" (1 Introduction); "What are the key mechanisms driving the thermal balance (heating and cooling processes) and hence the photoevaporation?" (1 Introduction)
- Target **203-506 (Orion)**: coordinates RA 05 35 20.32, Dec -05 25 05.55 (J2000)  
  > "203-506 (Orion) | 05 35 20.32$^{d}$ | $-$ 05 25 05.55$^{d}$" (Table 1); z/distance 414 pc  
  > "203-506 (Orion) | 05 35 20.32$^{d}$ | $-$ 05 25 05.55$^{d}$" (Table 1); distance from _not stated_
- Target **105-600 (Carina)**: coordinates RA 10 46 32.97, Dec -60 03 53.50 (J2000)  
  > "105-600 (Carina) | 10 46 32.97$^{a}$ | $-$ 60 03 53.50$^{a}$" (Table 1); z/distance 2300 pc  
  > "105-600 (Carina) | 10 46 32.97$^{a}$ | $-$ 60 03 53.50$^{a}$" (Table 1); distance from _not stated_
- Target **HST10 (Orion)**: coordinates RA 05 35 18.22, Dec -05 24 13.45 (J2000)  
  > "HST10   (Orion) | 05 35 18.22$^{d}$ | $-$ 05 24 13.45$^{d}$" (Table 1); z/distance 414 pc  
  > "HST10   (Orion) | 05 35 18.22$^{d}$ | $-$ 05 24 13.45$^{d}$" (Table 1); distance from _not stated_
- Target **244-440 (Orion)**: coordinates RA 05 35 24.38, Dec -05 24 39.74 (J2000)  
  > "244-440 (Orion) | 05 35 24.38$^{d}$ | $-$ 05 24 39.74$^{d}$" (Table 1); z/distance 414 pc  
  > "244-440 (Orion) | 05 35 24.38$^{d}$ | $-$ 05 24 39.74$^{d}$" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00352.S
- bands: Band 7  
  > "The observations were conducted in Band 7 with an angular resolution of 1$''$ insufficient to spatially resolve the disk." (2.3 ALMA detection of the 203-506 proplyd)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1''  
  > "The observations were conducted in Band 7 with an angular resolution of 1$''$ insufficient to spatially resolve the disk." (2.3 ALMA detection of the 203-506 proplyd)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 1 Orion Bar project (PI: J. Goicoechea); serendipitous detection  
  > "The 203-506 proplyd was detected as part of the ALMA cycle 1 project dedicated to the observation of the Orion bar (PI: J. Goicoechea)." (2.3 ALMA detection of the 203-506 proplyd)
- Line: HCO+ 4-3 (not stated)
- Other facility **Herschel (PACS, HIFI, SPIRE)**: FIR lines and continuum of proplyds  
  > "We conducted the first and unique far-IR (FIR) survey of proplyds with the *Herschel Space Observatory*." (2.1 Herschel survey)
- Other facility **APEX**: CO, HCO+, HCN lines and continuum for 105-600 from literature  
  > "We also retrieved the data of the Atacama pathfinder experiment (APEX) 12-m telescope from (cite: sahai_are_2012)" (2.1.3 Complementary data)
- External data: Intensity of H2 1-0 S(1) for 203-506 from CFHT/BEAR  
  > "This data is presented in (cite: noel_dynamique_2003) and we use their intensity." (2.3 ALMA detection of the 203-506 proplyd) [from (cite: noel_dynamique_2003)]
- External data: Observed mass-loss rates at ionisation front for HST10 and 244-440  
  > "The observed mass-loss rates derived at the ionisation front are from (cite: henney_keck_1999) for HST10 and 244-440" (Table 4 notes) [from (cite: henney_keck_1999)]

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

- ALMA data analysis and reduction of the Orion Bar project  
  > "The detailed analysis and data reduction are presented in (cite: goicoechea_compression_2016)." (2.3 ALMA detection of the 203-506 proplyd) [from (cite: goicoechea_compression_2016)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging, and CASA version
- How the HCO+ (4-3) integrated intensity was extracted (aperture, beam)
- Chi-square grid spacing and weighting for line fits

## Analysis recipe

1. **Fit dust SED of 105-600**: Two-component modified blackbody plus DustEM PAH; Nelder-Mead chi-square minimisation  
  > "the model numerically converges to the best solution in the space of parameters using a Nelder-Meadwith non-linear minimisation script." (3.4 Fitting strategy)
   - software: DustEM
   - assumption: beta = 1.8, reference 250 um, sigma = 2.32e-25 cm2, mu = 1.4  
  > "we used a spectral index of 1.8 and a reference wavelength of 250 μm (1200 GHz)" (3.2 Dust spectral energy distribution)
   - fitting: chi-square minimisation  
  > "we are looking for the set of values that best fit the observations based on a chi-square minimisation." (3.4 Fitting strategy)
   - validation: _not stated_
2. **Fit line intensities with 1D PDR model grid**: Meudon PDR code run on a grid of n_env and n_disk; best model minimises chi-square vs line intensities  
  > "The best model is the one which minimizes the chi-square between observed and predicted line integrated intensities." (3.4 Fitting strategy)
   - software: Meudon PDR code
   - parameter: A_V^max = 10; minimum grain radius 3 nm; dust-to-gas 0.01  
  > "Finally, the value of $A_\mathrm{V}^\mathrm{max}$ is set to 10." (3.3 Line emission using the Meudon PDR code)
   - assumption: Default ISM cosmic-ray rate, turbulent velocity 2 km/s  
  > "We use the default values for the dust-to-gas mass ratio, dust properties, cosmic ray ionisation rate and turbulent velocity" (3.3 Line emission using the Meudon PDR code)
   - fitting: grid chi-square  
  > "The best model is the one which minimizes the chi-square between observed and predicted line integrated intensities." (3.4 Fitting strategy)
   - validation: Grain parameter tests, shock alternatives checked  
  > "We should thus verify if some of the observed lines could originate in shocks rather than in the PDR." (Appendix: 105-600: the possibility of emissions from shocks)
3. **Estimate mass-loss rates**: Supercritical (Johnstone) and subcritical (Adams) analytic prescriptions using model disk temperature and density  
  > "$$\dot{M}= \mu m_H n_\mathrm{disk} c_\mathrm{S} \times 2\pi (r_\mathrm{disk} - r_\mathrm{g})^2.$$" (6.1 Definitions)
   - assumption: Central star 0.1 Msun (supercritical) or 1 Msun (subcritical); gamma = 7/5  
  > "we used a 0.1 and 1 M$_\odot$ for the *supercritical* and *subcritical* cases respectively." (Table notes (mass-loss rates table))
   - fitting: _not stated_
   - validation: Compared with ionisation-front rates of Henney & O'Dell  
  > "to reconcile the photoevaporation rates derived from our best fit models with those derived from the observations by (cite: henney_keck_1999), one must assume that the flows are in a *supercritical* regime." (6.3 Orion Proplyds)

## Software

- **Meudon PDR code** 1.4.4: 1D PDR modelling of proplyd line emission  
  > "Here, we use the 1.4.4[^3] public version of the code." (3.3 Line emission using the Meudon PDR code)
- **DustEM** : PAH emission in SED model  
  > "This component is included in the model using the PAH emission modelled with the DustEM code" (3.2 Dust spectral energy distribution)
- **HIPE** : Herschel data reduction  
  > "The data reduction and parts of post-processing were done using the *Herschel Interactive Processing Environment*" (2.1.2 Observing strategy and data reduction)
- **RADEX** : Non-LTE check of CO optical depth  
  > "Calculations with the online non-LTE molecular radiative transfer code RADEX" (11.2 Consistency of mass estimates)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 203-506 HCO+ (4-3) integrated intensity | 3.04e-20 | 10% | W m-2 | 0 | / 203-506 / HCO+ (4-3)   / 840.41     / ALMA             /    3.04e-20$^{c}$   / (10%) |
| 203-506 best-fit n_disk | 1e6 | not stated | cm-3 | 2 | the best-fit value is $n_\mathrm{disk} = 1 \times 10^6$ cm$^\mathrm{-3}$ |
| 203-506 disk surface temperature | 1080 | not stated | K | 2 | The temperature at the disk surface (which we consider being at the H/H$_\mathrm{2}$ transition) predicted by the best fit model is 1080 K. |
| 105-600 best-fit n_env | 8.5e3 | not stated | cm-3 | 2 | the best-fit model is the one with $n_\mathrm{env} = 8.5\times10^3 ~\mathrm{cm^{-3}}$ |

## Qualitative findings

- Proplyd disk surfaces are in a transitional regime at ~1000 K, regulated by the H/H2 transition position  
  > "This implies that proplyds appear to be in the **transitional* regime* with temperatures at the disk surface close to 1000 K." (5.3)

## Claim tuples

- H: Can proplyd FIR emission be modelled as a PDR? | E: 1D Meudon PDR model fitted to Herschel, APEX and ALMA lines | R: Most lines reproduced within a factor of a few; HCN (4-3) underpredicted | F: Disk surface densities ~1e6 cm-3, temperatures 1000-1300 K | **supported**
- H: Which regime sets mass loss? | E: Compare model mass-loss rates to ionisation-front rates | R: Supercritical rates agree better | F: Flows are supercritical | **supported**

## Reasoning

- Why this data: HCO+ is a PDR tracer and 203-506 complements the sample as a silhouette proplyd  
  > "Since HCO$^+$ is a PDR tracer, and given that other PDR tracers have been detected towards 203-506 (see below), we have decided to include it in our study." (2.3 ALMA detection of the 203-506 proplyd)
- Why this method: _not stated_
- Alternative: Shock origin for 105-600 lines judged unlikely  
  > "Altogether, we conclude that shocks are unlikely to play a major role in the observed emission." (10)
- How they decided it was enough: _not stated_
- Limitation (authors): 1D model cannot reproduce dense-gas tracers; unresolved observations  
  > "To go further and improve the modelling of the low-$J$ CO and HCN lines would require a detailed disk model not limited to the PDR as here." (4.1.2 Line emission)
- Caveat (inferred, ours): Unresolved ALMA data; HCO+ intensity extraction undocumented
- Caveat (inferred, ours): Few detections constrain Orion proplyd fits
- Caveat (inferred, ours): Mass-loss comparison depends on assumed stellar masses

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgements; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00352.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA reduction details (deferred to Goicoechea et al. 2016)
- Missing: Model grid details and own scripts
- Data volume (inferred): Tens of GB for the ALMA Band 7 dataset; Herschel data small
- Score (inferred): 3/5, Public Meudon code and tabulated inputs, but ALMA processing is inherited and the fitting is not fully specified.
- Rediscovery candidate: no, ALMA role is minor (one line intensity) and processing is deferred to another paper.

## Links

- Method: (cite: goicoechea_compression_2016) (ALMA data reduction and analysis)
- Method: (cite: le_petit_model_2006) (Meudon PDR code)
- Related: Herschel proplyd survey
- Related: ALMA Cycle 1 Orion Bar project (PI J. Goicoechea)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 77,
  "stated": 37,
  "rate": 0.481
 },
 "evidence_ok": true
}
```
