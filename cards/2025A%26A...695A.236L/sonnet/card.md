# Erosion of a dense molecular core by a strong outflow from a massive protostar

`2025A&A...695A.236L` | Astronomy and Astrophysics 2025 | first author: López-Vázquez, J. A. | arXiv: 2502.17786 | DOI: 10.1051/0004-6361/202453196

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: How strongly does the outflow from the high-mass protostar GGD 27-MM2(E) impact its parent envelope and surroundings, including a collision with the molecular core MC?  
  > "We aim to quantify the impact of the outflow associated with the high-mass protostar GGD 27-MM2(E) on its parent envelope and how this outflow affects its environment." (abstract)
- Target **GGD 27-MM2(E)**: coordinates _not stated_; z/distance 1.4 kpc  
  > "The high-mass star forming region GGD 27 is located in the dark molecular cloud L291 in Sagittarius arm at a distance of 1.4 kpc (cite: Anez2020)." (1 Introduction); distance from Añez-López et al. 2020  
  > "The high-mass star forming region GGD 27 is located in the dark molecular cloud L291 in Sagittarius arm at a distance of 1.4 kpc (cite: Anez2020)." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00441.S, 2015.1.00480.S
- bands: Band 3 (N2H+, CH3CN) and Band 7 (H2CO)  
  > "We present Atacama Large Millimeter/submillimeter Array Band 3 observations of N$_2$H$^+$ (1-0) and CH$_3$CN (5-4), as well as Band 7 observations of the H$_2$CO molecular line emissions" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3: 1.3"x1.2"; Band 7 H2CO: 0.18"x0.13"  
  > "$0.^{\prime\prime}18\times0.^{\prime\prime}13$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 1.2 mJy/beam (Band 3, 0.8 km/s channels); 2.1 mJy/beam (H2CO, 0.5 km/s)  
  > "H$_2$CO ($4_{1,3}-3_{1,2}$) | 300.836635 | 47.9" (Table 1)
- time on source: _not stated_
- observing dates: Band 3: 2014 June 27; Band 7: 2016 September 6 and 7  
  > "in Band 3 on 2014 June 27" (2.1 3 mm Observations); "ALMA observations were obtained in Band 7 on 2016 September 6 and 7" (2.2 1 mm Observations)
- pi or archival as stated: _not stated_
- Line: N2H+ 1-0 (93.173398 GHz)
- Line: CH3CN 5-4 K=0-3 (91.971153-91.987088 GHz)
- Line: H2CO 4(1,3)-3(1,2) (300.836635 GHz)
- External data: NH3 cloud temperature ~150 K and H2 mass 16 Msun, used for comparison  
  > "with a gas temperature of $\sim$ 150 K and a mass of H$_2$ of 16 $M_{\ensuremath{\odot}}$" (3.2 Morphology) [from Gomez2003]
- External data: H2CO abundance 1e-10 relative to H2  
  > "We adopt an H$_2$CO abundance with respect to H$_2$ of $10^{-10}$" (4.1 Outflow mass and energy) [from Gerner2014; Tang2018; Gieser2021; Zhao2024]
- External data: N2H+ abundance 1-2e-10  
  > "adopting an N$_2$H$^+$ abundance ranging between 1-2$\times10^{-10}$" (4.1 Outflow mass and energy) [from Shirley2005; AlvarezGutierrez2024]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: Band 3: CASA 6.4.0-16; Band 7: CASA 4.7  
  > "version 6.4.0-16" (2.1 3 mm Observations); "The data were calibrated using the CASA package version 4.7." (2.2 1 mm Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Band 3 self-calibrated; Band 7 standard calibration and continuum self-calibration  
  > "Standard calibration and self-calibration using the continuum emission were applied to the spectral data." (2.2 1 mm Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5 for both  
  > "A robust factor of 0.5 was applied to balance sensitivity and angular resolution" (2.1 3 mm Observations)
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
- final beam: 1.3"x1.2" (Band 3); 0.18"x0.13" (Band 7)  
  > "$1^{\prime\prime}.3\times 1^{\prime\prime}.2$" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Band 7 observations reported in detail elsewhere  
  > "The observations were reported in detail in (cite: FernandezLopez2023)." (2.2 1 mm Observations) [from FernandezLopez2023]
- Outflow mass, momentum, energy procedure  
  > "following an analogous procedure as, e.g., in (cite: Vazzano2021)" (4.1 Outflow mass and energy) [from Vazzano2021]
- Turbulence/energy comparison  
  > "Following an analogous pathway as (cite: Plunkett2015) based on the ‘‘outflow-regulated star formation’’  model by (cite: Nakamura2014)" (4.1 Outflow mass and energy) [from Plunkett2015; Nakamura2014]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and parameters
- Line-free channels / continuum subtraction
- Image size, cell size, masks, clean threshold
- Exact 3 mm spectral setup and cube channel widths
- Details of H2CO outflow mass calculation (velocity range, mask, inclination)
- Initial guesses/priors for CH3CN LTE fits and source size
- Outflow axis and PV cut widths

## Analysis recipe

1. **Make moment maps and PV diagrams**: Moments 0-2 of H2CO, CH3CN, N2H+ cubes; PV cuts along and perpendicular to outflow axis  
  > "The vertical dashed lines (C1–C9) in Figure [3](#fig:vertical_pv_diagram) indicate the positional offsets used to generate a series of PV diagrams perpendicular to the outflow axis" (3.4 Shocked region)
   - software: CASA
   - parameter: H2CO moments over 4-21 km/s; N2H+ hyperfine line moments over -0.05-7.02 km/s  
  > "The maps are integrated over a velocity range of 4-21 km s$^{-1}$" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit CH3CN K-ladder spectra**: LTE synthetic spectra with one or two layers fitted at several positions  
  > "we fitted synthetic spectra derived by solving the radiative transfer equation for an isothermal object in LTE (cite: Moller2017), using one or two independent layers" (4.2)
   - software: lmfit
   - assumption: Isothermal LTE  
  > "for an isothermal object in LTE" (4.2)
   - fitting: nonlinear least squares (lmfit)  
  > "uses a nonlinear least-squares minimization algorithm to search for the best fit of the observed data (cite: Newville2020)" (4.2)
   - validation: Second component judged to reduce residuals  
  > "Incorporating these components into positions S4 through S7 improves the model and reduces the residuals." (4.2)
3. **Outflow mass, momentum, energy**: Optically thin column density from H2CO using Mangum & Shirley eq. 86, Tex 30-70 K from CH3CN  
  > "so we use the simplified expression of equation 86 in (cite: Mangum2015)" (4.1)
   - parameter: Tex 30-70 K  
  > "a range of values between 30 K and 70 K" (4.1)
   - assumption: H2CO abundance 1e-10; no inclination correction  
  > "We adopt an H$_2$CO abundance with respect to H$_2$ of $10^{-10}$" (4.1)
   - fitting: _not stated_
   - validation: Compared with other massive-star outflows  
  > "These values are consistent with the previously reported of outflows driven by massive stars" (4.1)
4. **Cloud mass from N2H+**: HfS hyperfine fit of N2H+ (1-0) spectrum over 73 arcsec^2, optically thin column density  
  > "we use the HfS fitting tool on the hyperfine structure of the N$_2$H$^+$ (1-0) transition" (4.1)
   - software: HfS
   - parameter: N2H+ abundance 1-2e-10  
  > "adopting an N$_2$H$^+$ abundance ranging between 1-2$\times10^{-10}$" (4.1)
   - fitting: HfS  
  > "For this we use the HfS fitting tool on the hyperfine structure of the N$_2$H$^+$ (1-0) transition" (4 Analysis and Discussion, Outflow mass and energy)
   - validation: Tex and mass consistent with Gómez et al. 2003  
  > "This mass is, again, consistent with that estimated by (cite: Gomez2003)." (4.1)
5. **Energy budget of cloud vs outflow**: Compute turbulent energy, free-fall time, dissipation time, binding energy W and eta_out  
  > "(cite: Nakamura2014) defined the non-dimensional parameter $\eta_{out}=-2E_{outflow}/W$" (4.1)
   - assumption: Spherical cloud, radius 5" (~7000 au)  
  > "has an approximate radius of $5\ensuremath{''}$ ($\sim7000$ au)" (4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.0-16 (Band 3); 4.7 (Band 7): calibration, self-calibration, imaging  
  > "further self-calibrated and cleaned using Common Astronomy Software Application (CASA) package" (2.1)
- **HfS** : N2H+ hyperfine structure fitting  
  > "we use the HfS fitting tool on the hyperfine structure of the N$_2$H$^+$ (1-0) transition" (4.1)
- **lmfit** 1.0.1: CH3CN spectral fitting  
  > "Python code which uses a nonlinear least-squares minimization algorithm" (4.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N2H+ cloud mass | 13.3–26.5 | not stated | Msun | 4 | The total mass of the whole clump of gas is therefore 13.3–26.5 $M_{\ensuremath{\odot}}$ |
| Outflow mass | 1.7–2.1 | not stated | Msun | 3 | which produces an outflow mass between 1.7 $M_{\ensuremath{\odot}}$ and 2.1 $M_{\ensuremath{\odot}}$ |
| Outflow mass-loss rate | 4.9–6.0e-4 | not stated | Msun/yr | 3 | 4.9–6.0$\times10^{-4}$ $M_{\ensuremath{\odot}}$ yr$^{-1}$ |
| N2H+ excitation temperature | 23 | 4 | K | 4 | We also found an excitation temperature of 23$\pm4$ K |
| eta_out | 0.55–2.64 | not stated | dimensionless | 5 | $\eta_{out}$ ranges between 0.55 and 2.64 |
| Outflow dynamical time | 3500 | not stated | yr | 3 | $\tau_{dyn}=z/V_z\simeq 3500$ yr |

## Qualitative findings

- N2H+ shows a cavity coincident with the H2CO outflow; CH3CN is enhanced around MC with anti-correlation to N2H+  
  > "This spatial anti-correlation between N$_2$H$^+$ and CH$_3$CN emissions closely follows the MM2(E) outflow path." (4.2)

## Claim tuples

- H: The outflow collides with the MC cloudlet | E: H2CO PV diagrams and CH3CN LTE fits along the outflow | R: X-shape, wider spray downstream, higher Tex, column density, line width and velocity near MC | F: Outflow is colliding with and ablating MC | **supported**
- H: The outflow can erode its parent cloud and sustain turbulence | E: Compare outflow energy and momentum with cloud turbulent and binding energy | R: eta_out 0.55–2.64; momentum rate 7–9 times dissipation rate | F: Outflow is powerful enough to erode the cloud | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Outflow escaping the cloud rear as alternative to collision; multiple streamlines vs episodic ejections not confirmed  
  > "we cannot confirm this scenario" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Momentum and energy not corrected for unknown inclination  
  > "note that we give the momentum and energy without correcting by the unknown outflow inclination with respect to the line of sight" (4.1)
- Caveat (inferred, ours): Abundances of H2CO and N2H+ are uncertain by large factors, dominating mass and energy estimates
- Caveat (inferred, ours): Tex range from CH3CN applied to H2CO
- Caveat (inferred, ours): Collision vs escape-from-cloud interpretation not decisively separated

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Clean parameters and self-cal details
- Missing: Fit initial conditions and region definitions
- Missing: Exact velocity ranges for mass calculation
- Data volume (inferred): ~50-100 GB raw for two archival datasets
- Score (inferred): 3/5, Public archival data and clear analysis chain, but imaging and fitting details are missing.
- Rediscovery candidate: no, Imaging and mass-calculation details are insufficient for an exact redo.

## Links

- Method: Mangum2015 (column density formulae)
- Method: Moller2017 (LTE spectral model)
- Method: 2017Estalella (HfS tool)
- Companion: FernandezLopez2023 (Band 7 observations reported in detail)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 76,
  "stated": 39,
  "rate": 0.513
 },
 "evidence_ok": true
}
```
