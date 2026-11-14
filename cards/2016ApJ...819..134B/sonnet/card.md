# Planetary Signatures in the SAO 206462 (HD 135344B) Disk: A Spiral Arm Passing through Vortex?

`2016ApJ...819..134B` | The Astrophysical Journal 2016 | first author: Bae, Jaehan | arXiv: 1601.04976 | DOI: 10.3847/0004-637X/819/2/134

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can a planetary-mass companion in the outer disk of SAO 206462 produce the observed spiral arms, asymmetric sub-mm continuum and dust-depleted inner cavity?  
  > "In this work, we test whether a planetary-mass companion is able to generate various structures observed in the SAO 206462 disk." (INTRODUCTION)
- Target **SAO 206462 (HD 135344B)**: coordinates _not stated_; z/distance 140 pc  
  > "The distance of 140 pc (cite: muller11), PA and inclination of $63^\circ$ and $16^\circ$ (cite: vandermarel15b) were used." (4 DISCUSSION); distance from Müller et al. 2011 (cite: muller11)  
  > "The distance of 140 pc (cite: muller11), PA and inclination of $63^\circ$ and $16^\circ$ (cite: vandermarel15b) were used." (4 DISCUSSION)

## Data provenance

- ALMA projects: 2011.0.00724.S
- bands: _not stated_
- frequencies and spectral setup: 690 GHz continuum  
  > "the dust continuum emission at 690 GHz (cite: perez14)" (4 DISCUSSION)
- continuum bandwidth: _not stated_
- arrays: ALMA cycle 0 extended configuration (simulated, to match Perez et al. 2014 data)  
  > "We use the ALMA cycle 0 extended configuration to compare our models to the data presented in (cite: perez14)." (4 DISCUSSION)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLT/NACO Ks-band polarimetric imaging**: Scattered light image used for qualitative comparison  
  > "we display the scattered light image at the K$_s$ band (cite: garufi13)" (4 DISCUSSION)
- External data: ALMA 690 GHz dust continuum observations  
  > "the dust continuum emission at 690 GHz (cite: perez14)" (4 DISCUSSION) [from Pérez et al. 2014 (cite: perez14)]
- External data: Ks-band scattered light image  
  > "we display the scattered light image at the K$_s$ band (cite: garufi13)" (4 DISCUSSION) [from Garufi et al. 2013 (cite: garufi13)]
- Simulation/model as data: 2D two-fluid FARGO hydrodynamic runs with planet masses 5-20 MJ at 80-140 au, five dust sizes, alpha=1e-4, 288x688 grid  
  > "We use 288 logarithmically spaced radial grid-cells and 688 linearly spaced azimuthal grid-cells" (2.1 Disk Model)

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

- Two-fluid FARGO dust implementation  
  > "The dust response to planet-generated gas structures is calculated with the two-fluid FARGO code introduced in (cite: zhu12)" (2.2 Dust Component) [from Zhu et al. 2012 (cite: zhu12)]
- Stellar mass 1.7 Msun and distance 140 pc  
  > "Stellar mass ($M_*$) | $1.7~M_\odot$$^{a}$" (Table 1) [from Müller et al. 2011 (cite: muller11)]
- Disk mass 0.026 Msun  
  > "We choose $\Sigma_p$ such that the initial total gas mass is $0.026~M_{\odot}$ (cite: andrews11)." (2.1 Disk Model) [from Andrews et al. 2011 (cite: andrews11)]
- PA 63 deg and inclination 16 deg  
  > "PA and inclination of $63^\circ$ and $16^\circ$ (cite: vandermarel15b) were used." (4 DISCUSSION) [from van der Marel et al. 2016 (cite: vandermarel15b)]

### Not stated but needed to reproduce (our reading)

- Observation duration and integration time passed to simobserve
- Antenna configuration file and exact simobserve/cleaning parameters (weighting, robust)
- Which simulation snapshot time was used for each synthetic image
- Dust opacity composition/optical constants for Mie calculation
- Code release of modified FARGO

## Analysis recipe

1. **Run 2D gas+dust hydrodynamic simulations**: Two-fluid FARGO with planet; 100 orbits; planet mass and semi-major axis varied  
  > "All the calculations were run for $100~T_p$ where $T_p$ refers to the orbital time at the planet’s location." (3 RESULTS)
   - software: FARGO
   - parameter: alpha = 1e-4; (H/R)_p = 0.1; Sigma ∝ R^-1; dust-to-gas 1%  
  > "For the gas component a uniform viscosity parameter $\alpha=10^{-4}$ is implemented." (2.1 Disk Model)
   - assumption: Dust size distribution dn ∝ a^-3.5 da between 0.1 um and 5.3 mm; grain density 3 g cm^-3  
  > "We assume that the dust density is $3~{\rm g~cm^{-3}}$." (2.2 Dust Component)
   - fitting: _not stated_
   - validation: Resolution doubled for 10 MJ planet at 100 au; consistent morphology and radial profiles  
  > "While the high-resolution run shows more small-scale structures, the overall morphology is in good agreement with the low-resolution run" (Resolution Test)
2. **Build synthetic 690 GHz emission and observe with simobserve**: Mie opacities, tau scaled by S, F = B_nu(T) exp(1-tau), then CASA simobserve with tsys-atm noise  
  > "Finally, the flux is synthesized with the ALMA beam using CASA" (4 DISCUSSION)
   - software: CASA, simobserve
   - parameter: S ~ 2; inner 35 au dust density reduced by factor 100  
  > "we decrease the dust density at the inner 35 au by a factor of 100 when we produce synthetic ALMA observations." (4 DISCUSSION)
   - assumption: Opacities 12.0, 12.9, 7.6, 2.3, 0.6 cm2/g for 30-3000 um; blackbody at the fixed temperature profile  
  > "the dust opacities are 12.0, 12.9, 7.6, 2.3, 0.6 ${\rm cm}^2 {\rm g}^{-1}$, respectively." (4 DISCUSSION)
   - fitting: Qualitative comparison with observed map by eye; two scenarios (S1 primary or secondary)  
  > "Given the difficulties discriminating the primary and secondary, we test two scenarios: (1) S1 being the primary and (2) S1 being the secondary." (DISCUSSION)
   - validation: _not stated_

## Software

- **FARGO (two-fluid)** : hydrodynamic gas and dust simulations  
  > "in which the dust component is added to the standard FARGO code (cite: masset00)" (2.2 Dust Component)
- **CASA simobserve** : synthetic ALMA observations with thermal noise  
  > "Thermal noise from the atmosphere and from the ALMA receivers is added by setting the *thermalnoise* option in the *simobserve* task to *tsys-atm*." (4 DISCUSSION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Planet mass preferred | 10-15 | not stated | MJ | 1 | We suggest that a planetary companion with a mass of 10–15 $M_J$ is orbiting SAO 206462 at 100–120 au. |
| Planet orbital radius | 100-120 | not stated | au | 1 | We suggest that a planetary companion with a mass of 10–15 $M_J$ is orbiting SAO 206462 at 100–120 au. |
| Peak dust-to-gas ratio in vortex | ~1:25 | not stated | mass ratio | 1 | the dust-to-gas mass ratio inside the vortex becomes as large as $\sim1:25$ |
| Vortex total mass at 50 Tp | about 3 | not stated | MJ | 1 | it is about $3~M_J$ at $50~T_p$ |
| Horseshoe width | about 25 | not stated | au | 1 | The width of the horseshoe region ($x_{\rm hs}$) is about 25 au |
| Predicted vortex peak rotation | about 1.1 | not stated | deg per year | 2 | the peak will rotate about $1.^\circ1$ per year |

## Qualitative findings

- A spiral arm may pass through the vortex, boosting the scattered light, though the vortex alone may suffice  
  > "it is possible that the scattered light is boosted as one of the spiral arms passes through the high density vortex region" (abstract)

## Claim tuples

- H: A planet in the outer disk can produce spirals, asymmetric continuum and inner cavity in SAO 206462 | E: 2D two-fluid hydrodynamic simulations plus synthetic ALMA observations | R: A 10-15 MJ planet at 100-120 au yields spirals, an inner-edge vortex and dust-depleted cavity resembling observations | F: A planetary companion could explain the observed structures | **partially**
- H: Spiral-vortex interaction explains the abrupt brightness change in the western arm | E: Scenario with S1 as primary arm, 10 MJ at 100 au | R: Primary arm passes through the inner-edge vortex | F: Plausible, but vortex alone may also explain it; 2D models cannot discriminate | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Two-fluid calculations are needed to simulate dust as well as gas structures  
  > "we perform two-fluid calculations where we can simulate dust as well as gas structures." (INTRODUCTION)
- Alternative: S2 as primary arm requires 15 MJ at 120 au and no spiral-vortex boost  
  > "a larger planetary mass of $M_p = 15~M_J$ is assumed so that the planet generates a stronger pressure bump at the gap edge." (4 DISCUSSION)
- How they decided it was enough: _not stated_
- Limitation (authors): 2D only; scattered light compared only qualitatively  
  > "Thus, we compare the morphology of the arms and density distribution in a qualitative manner, rather than in a quantitative manner." (4 DISCUSSION)
- Caveat (inferred, ours): Dust density arbitrarily reduced in inner 35 au and scaling S tuned to match data
- Caveat (inferred, ours): Parameter grid is coarse and no quantitative fit
- Caveat (inferred, ours): Surface density compared to scattered light only qualitatively
- Caveat (inferred, ours): Outer vortex predicted but not observed

## Reproducibility

- Data public (paper): ALMA data acknowledged as ADS/JAO.ALMA 2011.0.00724.S; Garufi et al. data publicly available  
  > "Antonio Garufi et al. for making their data publicly available." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Modified FARGO code
- Missing: simobserve parameters
- Missing: Dust opacity inputs
- Missing: Exact observed images/ measurements for comparison
- Data volume (inferred): Small; simulations only (~GB); ALMA data are not reduced here
- Score (inferred): 3/5, Simulation setup well described, but the code and synthetic observation settings are incomplete and comparison is qualitative.
- Rediscovery candidate: no, Main results are simulations compared qualitatively, with a modified code not released.

## Links

- Method: Zhu et al. 2012 (cite: zhu12) (two-fluid FARGO code)
- Companion: Pérez et al. 2014 (cite: perez14) (ALMA data compared)
- Companion: Garufi et al. 2013 (cite: garufi13) (scattered light data compared)

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 28,
  "rate": 0.424
 },
 "evidence_ok": true
}
```
