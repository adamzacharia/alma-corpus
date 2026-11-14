# Circular Polarization of Simulated Images of Black Holes

`2024ApJ...972..135J` | The Astrophysical Journal 2024 | first author: Joshi, Abhishek V. | arXiv: 2406.15653 | DOI: 10.3847/1538-4357/ad5b51

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: agn_and_quasars, milky_way_ism
- Question: Which GRMHD/GRRT black hole models produce net circular polarization (v_net) consistent with unresolved ALMA 1.3 mm measurements of Sgr A* and M87*, and how does v_net depend on model parameters?  
  > "We find that ALMA observations of Sgr A\* are inconsistent with all edge-on ($i = 90^\circ$) models." (abstract)
- Target **Sgr A***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **M87***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00764.S, 2016.1.01154.V, 2016.1.01404.V
- bands: 1.3 mm (ALMA) CP measurements  
  > "Measurements of CP fraction at 1.3mm for EHT targets." (Table 6)
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
- Other facility **Submillimeter Array (SMA)**: Unresolved CP of Sgr A* (Muñoz et al. 2012), listed in Table but not used for comparison  
  > "we only use the ALMA epoch $v_\mathrm{net}$ for comparing our simulations with Sgr A\*." (Table 6)
- External data: ALMA Sgr A* v_net measurements (8 data points, -1.5% to -0.92%) used as constraint  
  > "(8 data points, assumed uncorrelated, ranging from $-1.5\%$ to $-0.92\%$)" (6.1 Sgr A*) [from (cite: bower_alma_2018); (cite: wielgus_orbital_2022)]
- External data: M87* limit |v_net|<0.8%  
  > "CP measurements of M87\* given in (cite: Goddi2021) constrain $|v_\mathrm{net}|<0.8\%$." (6.2 M87*) [from (cite: Goddi2021)]
- Simulation/model as data: KHARMA GRMHD library (V3), ray-traced with ipole; 600 images per model over 15000-30000 GM/c^3; spin, MAD/SANE, R_high, inclination, field sign varied  
  > "Each model contains 600 images evenly spaced in the interval $15000 \mbox{--} 30000\; GM/c^3$" (3.3 Image Library Parameters)

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

- Model comparison procedure (KS tests) similar to earlier EHT Sgr A* paper  
  > "To test the models, a procedure similar to that in is used." (6.1 Sgr A*) [from EHT Sgr A* Paper V (reference not given in text)]
- GRMHD library and modeling procedure  
  > "the modeling procedure is described in detail in (cite: wong_patoka_2022)." (1 Introduction) [from (cite: wong_patoka_2022)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA epochs/values for the 8 data points beyond Table 6
- Public availability of the model library and analysis scripts
- ipole image field of view and exact ray-tracing settings
- KS test implementation details

## Analysis recipe

1. **Generate model library**: KHARMA GRMHD simulations ray-traced with ipole over spin, MAD/SANE, R_high, inclination, field sign  
  > "We image the GRMHD simulation snapshots using the general relativistic ray-tracing code `ipole `(cite: ipole18)." (3.2 Radiative Transfer Numerical Model)
   - software: KHARMA, ipole
   - assumption: Thermal Maxwell-Jüttner electrons; flux density scaled to 2.4 Jy (Sgr A*)  
  > "the average flux is within $5\%$ of $0.7$ Jy and $2.4$ Jy, respectively" (3.3 Image Library Parameters)
   - fitting: _not stated_
   - validation: Convergence tests with time, GRMHD and GRRT resolution  
  > "the $v_\mathrm{net}$ distributions appear converged with respect to GRMHD resolution and GRRT image resolution." (5 CP Distributions Across All Models)
2. **Compare model v_net distributions to ALMA data**: Two-sided KS test between model (sampled every 400M) and observations; fail if both aligned and reversed field give p<0.01  
  > "The model is sampled every 400M to obtain an approximately uncorrelated sample." (6.1 Sgr A*)
   - parameter: p<0.01 threshold  
  > "giving 99% confidence in rejecting the null hypothesis that the model and observations arose from the same distribution." (6.1 Sgr A*)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit mean v_net of Sgr A* MAD models**: Symbolic regression  
  > "which we extracted using the `PySR` symbolic regression code" (5.2 Fits)
   - software: PySR
   - fitting: _not stated_
   - validation: Fit within 0.3% for ~80% of models  
  > "The fit accurately measures the mean $v_\mathrm{net}$ of roughly 80% of the models to within 0.3% (absolute difference)." (5.2 Fits)

## Software

- **KHARMA** 2022.3: GRMHD simulations  
  > "The models are run using KHARMA[^1](cite: prather_grmhd_2022; prather_2024_kharma_zenodo)" (3.1 GRMHD Models)
- **ipole** : GR ray tracing / polarized radiative transfer  
  > "We image the GRMHD simulation snapshots using the general relativistic ray-tracing code `ipole `(cite: ipole18)." (3.2 Radiative Transfer Numerical Model)
- **PySR** : Symbolic regression fit of mean v_net  
  > "which we extracted using the `PySR` symbolic regression code" (5.2 Fits)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MAD models passing CP constraint | 27/180 (15%) | not stated | dimensionless | 2 | We have $27/180 = 15\%$ of the MAD models pass and $43/180 = 24\%$ of the SANE models pass the CP constraint. |
| SANE models passing CP constraint | 43/180 (24%) | not stated | dimensionless | 2 | We have $27/180 = 15\%$ of the MAD models pass and $43/180 = 24\%$ of the SANE models pass the CP constraint. |
| One-zone CP fraction Sgr A* | 5.1 | not stated | % | 0 | \mathrm{CP_{SgrA^*}} = 5.1\% |

## Qualitative findings

- Edge-on models produce v_net≈0 and are disfavored; passing MAD models have dipole moment pointing away from observer and clockwise rotation  
  > "We also note that in 26 of the 27 passing MAD models the accretion flow rotates clockwise on the sky." (abstract)

## Claim tuples

- H: Do ALMA unresolved CP data constrain Sgr A* models? | E: KS tests of model v_net distributions against ALMA data | R: All edge-on MAD models fail; passing MADs have field pointing away from observer | F: CP constrains inclination, field direction and flow rotation | **supported**
- H: Best-bet EHT models are consistent with CP | E: KS test | R: All best-bet models fail | F: Prograde high-R_high low inclination MADs do not give sufficient CP | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Models highly variable with frequent v_net sign crossings unlike observations  
  > "The primary caveat is that the models are highly variable in Stokes I and V when compared to Sgr A\*." (7 Discussion)
- Caveat (inferred, ours): Eight ALMA points assumed uncorrelated
- Caveat (inferred, ours): Single GRMHD library with fixed adiabatic index and thermal electrons
- Caveat (inferred, ours): Extended emission assumed negligible

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: KHARMA publicly available at GitHub  
  > "It is publicly available at <https://github.com/AFD-Illinois/kharma>." (footnote)
- Missing: Model library images not stated as released
- Missing: ipole settings
- Data volume (inferred): Negligible ALMA data; large simulation library
- Score (inferred): 3/5, Observational inputs are literature values; theory pipeline described but library and details not fully released.
- Rediscovery candidate: no, Main results depend on a large simulation library not provided; ALMA data not reprocessed.

## Links

- Method: (cite: wong_patoka_2022) (GRMHD library and modeling procedure)
- Method: (cite: ipole18) (Polarized ray-tracing code)
- Companion: (cite: wielgus_orbital_2022) (ALMA Sgr A* CP data)
- Companion: (cite: bower_alma_2018) (ALMA Sgr A* CP data)
- Related: Event Horizon Telescope

## Checks

```json
{
 "quotes": 31,
 "quotes_ok": 31,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 21,
  "rate": 0.304
 },
 "evidence_ok": true
}
```
