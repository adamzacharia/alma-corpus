# Robustness of N<SUB>2</SUB>H<SUP>+</SUP> as tracer of the CO snowline

`2017A&A...599A.101V` | Astronomy and Astrophysics 2017 | first author: van 't Hoff, M. L. R. | arXiv: 1610.06788 | DOI: 10.1051/0004-6361/201629452

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is N2H+ emission a robust tracer of the CO snowline in the TW Hya disk, given variations in CO/N2 abundances, binding energies, cosmic ray ionization rate and grain settling?  
  > "In this work, the robustness of N$_2$H$^+$ as a tracer of the CO snowline is investigated." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 54 pc  
  > "assuming a distance, inclination and position angle appropriate for TW Hya; 54 pc, 6$\ensuremath{^\circ}$ and 155$\ensuremath{^\circ}$, respectively" (2.3 Line radiative transfer); distance from Hughes2011; Andrews2012  
  > "assuming a distance, inclination and position angle appropriate for TW Hya; 54 pc, 6$\ensuremath{^\circ}$ and 155$\ensuremath{^\circ}$, respectively" (2.3 Line radiative transfer)

## Data provenance

- ALMA projects: 2011.0.00340.S
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
- Line: N2H+ J=4-3 (372 GHz)
- External data: Reduced ALMA N2H+ J=4-3 observations of TW Hya (image cube, integrated intensity profile, line profile) from Q13  
  > "For the $J$ = 4–3 transition, the line profiles and the integrated line intensity profiles were compared to the observational data reduced by Q13." (2.3 Line radiative transfer) [from (cite: Qi2013)]
- External data: TW Hya physical disk structure from DALI model  
  > "For the physical structure we adopt the model for TW Hya from (cite: Kama2016)." (2.1 Physical model) [from (cite: Kama2016)]
- External data: CO and N2 binding energies of 855 and 800 K  
  > "for CO and N$_2$ values of 855 and 800 K (cite: Bisschop2006) are adopted, respectively." (2.2 Chemical model) [from (cite: Bisschop2006)]
- Simulation/model as data: DALI physical model of TW Hya used as the input disk structure for the simple chemical network and LIME  
  > "The 2D physical-chemical code DALI (cite: Bruderer2009; Bruderer2012; Bruderer2013) was used to create the model" (2.1 Physical model)

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
- final beam: Simulated images convolved with 0.63'' x 0.59'' and 0.2'' x 0.2'' beams  
  > "The simulated images were convolved with a 0.63$''$ $\times$ 0.59$''$ beam, similar to the reconstructed beam of Q13, and a 0.2$''$ $\times$ 0.2$''$ beam" (2.3 Line radiative transfer)
- final rms: _not stated_

### Inherited from earlier work

- Distance, inclination and position angle of TW Hya same as adopted by Q13  
  > "These are the same values as adopted by Q13." (2.3 Line radiative transfer) [from (cite: Qi2013)]
- Physical structure of TW Hya adopted from earlier DALI model  
  > "For the physical structure we adopt the model for TW Hya from (cite: Kama2016)." (2.1 Physical model) [from (cite: Kama2016)]
- Stellar UV spectrum and low cosmic ray rate taken from earlier work  
  > "The stellar UV spectrum from (cite: Cleeves2015) is used" (2.1 Physical model) [from (cite: Cleeves2015)]

### Not stated but needed to reproduce (our reading)

- Original ALMA observation reduction details (calibration, imaging, robust, continuum subtraction), only via Q13 and a shared cube
- LIME settings: number of grid points, channel width, N2H+ collisional data, hyperfine treatment
- Velocity field / turbulence and temperature structure files from the Kama et al. DALI model
- How emission-peak radius and column-density peak were located (smoothing, fitting)
- Treatment of the N2H+ hyperfine structure in simulated lines

## Analysis recipe

1. **Adopt disk physical structure**: Use DALI-based TW Hya model with gas surface density power law with exponential cutoff, gas-to-dust 200, large grain settling chi=0.2  
  > "To match the observations, the gas-to-dust mass ratio is set to 200." (2.1 Physical model)
   - software: DALI
   - parameter: M* = 0.74 Msun, R* = 1.05 Rsun  
  > "assuming a stellar mass and radius of $M_*$ = 0.74 $\mathrm{M}_{\ensuremath{\odot}}$ and $R_*$ = 1.05 $\mathrm{R}_{\ensuremath{\odot}}$, respectively" (2.1 Physical model)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute CO and N2 freeze-out/desorption balance and snowlines**: Steady-state balance of freeze-out and thermal desorption; snow surface where 50% in gas  
  > "The snow surface is defined as the position in the disk where 50% of a species is present in the gas phase and 50% is frozen onto the grains." (2.2 Chemical model)
   - parameter: E_b(CO)=855 K, E_b(N2)=800 K; sticking 0.9 and 0.85  
  > "The sticking coefficients for CO and N$_2$ are taken to be 0.9 and 0.85, respectively" (Chemical model)
   - fitting: _not stated_
   - validation: Compared with Q13 and Zhang2016 CO snowline  
  > "in good agreement with recent results from (cite: Zhang2016) who directly detect the CO snowline around 17 AU using CO observations." (3.1 N2H+ distribution and emission)
3. **Solve reduced chemical network for N2H+ abundance**: ODE system integrated to 1e6 yr with all CO and N2 initially frozen; total CO and N2 abundances varied 1e-7 to 1e-4; model variants for binding energy, cosmic ray rate, photodesorption and settling  
  > "As an initial condition, all CO and N$_2$ is considered to be frozen out, while all other abundances (except H$_2$) are set to zero." (2.2 Chemical model)
   - software: SciPy odeint
   - parameter: zeta = 1.2e-17 s-1 fiducial; 1e-19 and 5e-17 variants  
  > "adopting values of $\zeta = 1 \times 10^{-19}$ s$^{-1}$ (CH-CR1) and $\zeta = 5 \times 10^{-17}$ s$^{-1}$ (CH-CR2)" (2.2 Chemical model)
   - fitting: _not stated_
   - validation: Steady state checked time-dependently  
  > "Solving the gas and ice abundances time dependently shows that equilibrium is reached within $10^5$ years" (2.2 Chemical model)
4. **Simulate N2H+ line emission and compare with ALMA data**: LIME in LTE for J=4-3, 3-2, 1-0, convolved with beams; compare peak position and integrated intensity with Q13 ALMA data  
  > "so to reduce CPU time, models were run in LTE." (2.3 Line radiative transfer)
   - software: LIME
   - parameter: d=54 pc, i=6 deg, PA=155 deg  
  > "54 pc, 6$\ensuremath{^\circ}$ and 155$\ensuremath{^\circ}$, respectively" (2.3 Line radiative transfer)
   - fitting: _not stated_
   - validation: Best fit total CO and N2 abundance chosen by matching observed emission peak position  
  > "model CH can reproduce the position of the emission peak for a CO and N$_2$ abundance of $3 \times 10^{-6}$" (3.1 N2H+ distribution and emission)

## Software

- **LIME** : Line radiative transfer of N2H+  
  > "were simulated with the radiative transfer code LIME (cite: Brinch2010)" (2.3 Line radiative transfer)
- **DALI** : Physical-chemical disk model (physical structure)  
  > "The 2D physical-chemical code DALI (cite: Bruderer2009; Bruderer2012; Bruderer2013) was used to create the model" (2.1 Physical model)
- **SciPy odeint** : Solving reduced chemical network ODEs  
  > "was solved using the python function `odeint`[^1] up to a typical disk lifetime of $10^{6}$ yr." (2.2 Chemical model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO snowline radius (fiducial) | 19 | not stated | AU | 2 | the balance between freeze-out and thermal desorption predicts a CO snowline at 19 AU, corresponding to a CO midplane freeze-out temperature of 20 K. |
| Best-fit total CO and N2 abundance wrt H2 | 3e-6 | not stated | dimensionless | 4 | A model with a total, i.e. gas plus ice, CO abundance of $3 \times 10^{-6}$ with respect to H$_2$ fits the position of the emission peak |
| N2H+ column density peak offset outside CO snowline | 5–30 | not stated | AU | 3 | The N$_2$H$^+$ column density, however, peaks 5–30 AU outside the snowline for all conditions tested. |
| Emission peak offset beyond snowline (max) | ~50 | not stated | AU | 4 | the N$_2$H$^+$ emission can peak much further out, as far as $\sim$50 AU beyond the snowline. |

## Qualitative findings

- A N2H+ surface layer arises for N2/CO >~ 0.2 owing to lower N2 photodissociation rate, shifting emission outward  
  > "models with an N$_2$/CO ratio $\gtrsim$ 0.2 predict an N$_2$H$^+$ layer higher up in the disk due to a slightly lower photodissociation rate for N$_2$ as compared to CO." (abstract)

## Claim tuples

- H: N2H+ column density peaks at the CO snowline | E: Simple chemical network over varied abundances, binding energies, zeta, settling | R: Column density peaks 5–30 AU outside the 19 AU snowline in all models | F: N2H+ column density does not trace the snowline directly | **supported**
- H: N2H+ emission peak traces the column density peak | E: LIME emission with and without surface layer | R: Emission peak offset up to ~50 AU due to surface layer | F: Chemical modeling is needed to infer snowline from emission | **supported**
- H: Observed TW Hya N2H+ peak can be reproduced with the model | E: Compare simulated J=4-3 to Q13 data | R: CO abundance 3e-6 reproduces peak position | F: Consistent with CO depletion in TW Hya | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Reduced network chosen to avoid uncertainties of full chemical networks  
  > "To avoid uncertainties associated with full chemical network models, a reduced chemical network, incorporating the key processes affecting the N$_2$H$^+$ abundance" (2.2 Chemical model)
- Alternative: Photodesorption cannot explain the underpredicted outer-disk emission  
  > "so photodesorption alone can not explain the N$_2$H$^+$ emission originating in the outer disk." (3.8 Outer edge)
- How they decided it was enough: _not stated_
- Limitation (authors): Model underpredicts emission beyond ~60 AU; gas-phase formation of CO and N2 ignored  
  > "underestimates the emission coming from the outer disk (further out than $\sim$60 AU)" (3.8 Outer edge)
- Caveat (inferred, ours): Results rely on one fixed TW Hya physical model; temperature not recomputed with abundance changes
- Caveat (inferred, ours): LTE assumption and the simple network ignore full chemistry and CO conversion
- Caveat (inferred, ours): Best-fit abundance judged only by peak position, no formal fit

## Reproducibility

- Data public (paper): ALMA data cited as project 2011.0.00340.S; reduced cube shared by a colleague  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00340.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Kama et al. DALI disk model files
- Missing: LIME configuration details
- Missing: Reduced ALMA N2H+ cube (Q13)
- Data volume (inferred): small (<10 GB) for the model; ALMA cube optional
- Score (inferred): 3/5, Chemical network equations and parameters are well given, but the DALI structure and LIME setup are inherited or missing; ALMA data only used as comparison.
- Rediscovery candidate: no, Main work is modeling with external disk structure; the ALMA data are used only via a previously reduced cube.

## Links

- Method: (cite: Brinch2010) (LIME radiative transfer code)
- Method: (cite: Kama2016) (TW Hya physical model)
- Method: (cite: Aikawa2015) (analytical N2H+ abundance approach)
- Companion: (cite: Qi2013) (ALMA N2H+ J=4-3 observations of TW Hya compared here)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
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
  "facts": 72,
  "stated": 30,
  "rate": 0.417
 },
 "evidence_ok": true
}
```
