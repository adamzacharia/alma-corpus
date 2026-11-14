# Exploring DCO<SUP>+</SUP> as a tracer of thermal inversion in the disk around the Herbig Ae star HD 163296

`2018A&A...616A..45S` | Astronomy and Astrophysics 2018 | first author: Salinas, V. N. | arXiv: 1806.02950 | DOI: 10.1051/0004-6361/201731745

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can a simple 2D chemical model of cold deuteration plus a parametrized warm deuteration channel reproduce the DCO+ J=3-2 emission in the HD 163296 disk, and what do the fitted parameters imply?  
  > "We aim to reproduce the DCO$^+$ emission in the disk around HD163296 using a simple 2D chemical model for the formation of DCO$^+$ through the cold deuteration channel and a parametric treatment of the warm deuteration channel." (abstract)
- Target **HD 163296**: coordinates RA 17h56m51.21s, Dec -21d57m22.0s (J2000)  
  > "the Herbig Ae star HD163296 ($\rm\alpha_{2000}$ = ${\rm    17^h56^m51{s}21}$, $\delta_{2000}$ = $-21^\circ57'22{\ensuremath{''}}0$)" (2.1 Previous observation of HD 163296); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01268.S
- bands: Band 6  
  > "obtained by the Atacama Large (sub-)Millimeter Array (ALMA) in Band 6 as a part of Cycle 2" (2.1 Previous observation of HD 163296)
- frequencies and spectral setup: DCO+ J=3-2 at 216.112 GHz; spectral resolution 0.7 MHz = 0.085 km/s  
  > "The spectral resolution is 0.7 MHz corresponding to 0.085 km s$^{-1}$ with respect to the rest frequency of the line." (2.1 Previous observation of HD 163296)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: uv-coverage 20 to 630 kλ  
  > "The $uv$-coverage of the data ranges from 20 to 630 k$\lambda$." (2.1 Previous observation of HD 163296)
- angular resolution: 0.53" x 0.42"  
  > "The resulting synthesized beam has dimensions of 0$\ensuremath{''}$53$\times$0$\ensuremath{''}$42" (2.1 Previous observation of HD 163296)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014 July 27-29 (Cycle 2)  
  > "as a part of Cycle 2 on 2014 July 27-29 (project 2013.1.01268.S)" (2.1 Previous observation of HD 163296)
- pi or archival as stated: _not stated_
- Line: DCO+ J=3-2 (216.112 GHz)
- External data: Physical structure of the disk (gas density and dust temperature from RADMC) adopted from the parametric model  
  > "We adopt the gas density and dust temperature from the physical model used by (cite: Mathews2013) as inputs for the simple chemical network describe above." (2.3 Implementation) [from (cite: Mathews2013)]
- External data: Simplified analytic DCO+ cold-deuteration chemical network  
  > "This system can be solved analytically as proposed by (cite: Murillo2015). We use their prescription and simplified chemical network of the CD channel and apply it to HD163296." (2.2 Chemical model) [from (cite: Murillo2015)]
- External data: Thermal inversion temperature structure motivated by dust evolution models  
  > "A thermal inversion is produced by the dust evolution modeling of (cite: Facchini2017) as a direct consequence of grain growth and settling." (3.2 Thermal inversion model (CD+TI)) [from (cite: Facchini2017)]

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
- weighting robust: Briggs 0.5  
  > "imaged using a Briggs weighting of 0.5" (2.1 Previous observation of HD 163296)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: visibility-plane first-order polynomial fit  
  > "The DCO$^+$ $J$=3–2 line was continuum subtracted in the visibility plane using a first-order polynomial fit and imaged using a Briggs weighting of 0.5." (2.1 Previous observation of HD 163296)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.53" x 0.42"  
  > "The resulting synthesized beam has dimensions of 0$\ensuremath{''}$53$\times$0$\ensuremath{''}$42" (2.1 Previous observation of HD 163296)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction  
  > "The data were reduced as described by (cite: Salinas2017) and (cite: Carney2017)." (2.1 Previous observation of HD 163296) [from (cite: Salinas2017); (cite: Carney2017)]
- Keplerian mask for integrated intensity and residual radial profiles  
  > "The residual radial profile is obtained applying a Keplerian mask (cite: Salinas2017) to the residual cube" (3.1 Standard model (CD)) [from (cite: Salinas2017)]
- Column density prescription and excitation temperature profile  
  > "This 1D analysis was previously performed by (cite: Salinas2017) and we use the same prescription and excitation temperature profile for DCO$^+$." (3.1 Standard model (CD)) [from (cite: Salinas2017)]

### Not stated but needed to reproduce (our reading)

- Original calibration details, CASA version and calibrators (deferred to Salinas2017/Carney2017)
- Channel range and line-free channels for continuum fit
- Image size, cell size and cleaning parameters
- Numeric rms of the cube
- Excitation temperature profile values
- Scale heights h_C for gas and dust
- Distance to HD 163296
- Disk inclination and position angle used in LIME and the radial profile
- Model-fitting procedure (by-eye vs. statistical) and parameter uncertainties
- LIME input details such as turbulent linewidth and the exact radial cutoff treatment

## Analysis recipe

1. **Build radial emission profile from the data**: Keplerian mask to make integrated intensity map; average over concentric ellipses centered on the star  
  > "A radial emission profile can be constructed by taking the average value of concentric ellipsoids, centered at the star, in the integrated intensity map." (2.1 Previous observation of HD 163296)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute DCO+ abundance with simplified cold-deuteration network**: Analytic 10-reaction network of Murillo+2015 on adopted Mathews+2013 density and temperature structure  
  > "The DCO$^+$ chemical network involving the CD channel can be boiled down to only ten chemical reactions." (2.2 Chemical model)
   - parameter: Constant ionization rate 1.3e-17 s^-1  
  > "The ionization rate ($\zeta$) is constant throughout the disk and equal to$1.3\times10^{-17}$ s$^{-1}$." (2.2 Chemical model)
   - parameter: Standard model X_high=5e-5, T_CO=19 K, radial cutoff 300 AU  
  > "We chose a standard CO abundance model with a constant abundance $X_{\rm high}$=5.0$\times10^{-5}$ at temperatures above an evaporation temperature of $T_{\rm CO}$=19 K." (3.1 Standard model (CD))
   - assumption: T_dust = T_gas; HD abundance equals the cosmic D/H ~1e-5; X_low = 0.01 X_high  
  > "We assume that the dust temperature ($T_{\rm dust}$) equals the gas temperature ($T_{\rm gas}$), which is a reasonable assumption in the dense regions that we focus on." (2.3 Implementation)
   - fitting: Parameters adjusted to match the observed profile; no sampler stated  
  > "These values are taken to match the inner DCO$^+$ emission at R$\lesssim$ 150 AU." (The CD+WD+TI model)
   - validation: Network compared with full chemical models by Murillo+2015  
  > "They contrasted their results to a full chemical network including gas-grain balance (freeze-out, thermal desorption, and cosmic-ray-induced photodesorption) confirming the general trend found by the simplified network." (2.2 Chemical model)
3. **Non-LTE radiative transfer and comparison with data**: LIME model cube, continuum subtracted with first channel, convolved with the synthesized beam, compared with data radial profile  
  > "Then, each spectral plane of the model is convolved with the synthesized beam of the DCO$^+$ data cube." (2.4 Radiative transfer)
   - software: LIME
   - parameter: 100000 grid points, 20 iterations  
  > "We use a grid of 100000 points that are created applying a weighted random selection in $R$ using a logarithmic scale." (2.4 Radiative transfer)
   - fitting: _not stated_
   - validation: Convergence checked by comparing consecutive iterations  
  > "We manually set the number of iterations to 20 and confirm convergence by comparing consecutive iterations." (2.4 Radiative transfer)
4. **Residual abundance estimate for WD contribution**: Subtract convolved model cube from data channel by channel, Keplerian mask, radial profile, LTE optically thin column density divided by surface density  
  > "We perform a channel by channel subtraction from the data cube and the convolved model cube to calculate a residual cube" (3.1 Standard model (CD))
   - assumption: LTE, optically thin emission  
  > "The radial abundance estimate is calculated assuming LTE and that the emission is optically thin." (3.1 Standard model (CD))
   - fitting: _not stated_
   - validation: _not stated_
5. **Add thermal inversion (CD+TI) and warm deuteration (CD+WD+TI)**: Temperature increased by parametrized term with R1=240 AU, R2=300 AU; X_WD added where T<=T_eff  
  > "where $R_1=240$ AU is the inflection point at which the TI occurs and $R_2=300$ AU a characteristic radius." (3.2 Thermal inversion model (CD+TI))
   - software: LIME
   - parameter: X_high=2.0e-7, T_CO=19 K; X_WD=3.2e-12, T_eff=32 K  
  > "using $X_{\rm WD}=3.2\times10^{-12}$ and $T_{\rm eff}$= 32 K and the parameters from the CD+TI model" (3.3 The CD+WD+TI model)
   - fitting: Values chosen to match the observed profile  
  > "These values are taken to match the inner DCO$^+$ emission at R$\lesssim$ 150 AU." (3.3 The CD+WD+TI model)
   - validation: _not stated_

## Software

- **LIME** v1.5: 3D non-LTE radiative transfer of DCO+ model  
  > "We used LIME (v1.5), a 3D radiative transfer code in non-LTE (cite: Brinch2010)" (2.4 Radiative transfer)
- **RADMC** : dust temperature profile of the adopted physical model  
  > "The dust temperature profile was computed by the 2D radiative transfer code RADMC (cite: Dullemond2004b)" (2.3 Implementation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Maximum CD DCO+ abundance | 1.6e-11 | not stated | relative to H2 | 5 | cold deuteration producing abundances up to $1.6\times 10^{-11}$ |
| Warm deuteration constant abundance X_WD | 3.2e-12 | not stated | dimensionless | 5 | Warm deuteration, at a constant abundance of $3.2\times 10^{-12}$ |
| Effective WD temperature T_eff | 32 | not stated | K | 5 | becomes fully effective below 32 K |
| CO abundance in DCO+ zone (X_high) | 2e-7 | not stated | dimensionless | 5 | a CO abundance of $2\times 10^{-7}$ is found |
| WD/CD DCO+ ratio outside CO snowline | 0.2 | not stated | dimensionless | 5 | ratio between the DCO$^+$ column densities produced by the WD and the CD channel of  0.2 |
| Radius of thermal inversion | ~250-260 | not stated | AU | 5 | attributed to a temperature inversion at 250 AU |

## Qualitative findings

- Thermal inversion or increased photodesorption can explain the DCO+ outer bump and cutoff; the models cannot distinguish them.  
  > "Our modeling cannot distinguish this from thermal desorption." (4.1 DCO$^+$ Outer radius)

## Claim tuples

- H: Simple CD chemistry with a temperature inversion reproduces the outer DCO+ morphology | E: CD+TI model in LIME compared with the observed radial profile | R: Reproduces shape at R>180 AU and the lack of emission at R>300 AU with X_high=2e-7 | F: A thermal inversion near 250 AU can cause the secondary maximum and limit DCO+ extent | **supported**
- H: The WD channel contributes to inner DCO+ emission | E: Add constant X_WD below T_eff to CD+TI | R: X_WD=3.2e-12, T_eff=32 K; WD/CD ratio 0.2 | F: WD contributes up to ~20%, consistent with Favre et al. models | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Drop in gas density, higher o/p H2, and higher electron fraction judged unlikely for the DCO+ outer drop  
  > "It is therefore unlikely that the drop off of DCO$^+$ is due to an overall drop in gas surface density." (4.1 DCO$^+$ Outer radius)
- How they decided it was enough: _not stated_
- Limitation (authors): T_eff cannot be constrained without a gas temperature model, and photodesorption cannot be distinguished from thermal desorption  
  > "The exact value of the parameter $T_{\rm eff}$ cannot be constrained without a gas temperature model and only represents the location of the isothermal surface." (3.3 The CD+WD+TI model)
- Caveat (inferred, ours): Parameters tuned by eye without uncertainties or formal fit
- Caveat (inferred, ours): Degeneracy between CO abundance and T_CO
- Caveat (inferred, ours): Gas temperature assumed equal to dust temperature
- Caveat (inferred, ours): Thermal inversion parametrization is ad hoc

## Reproducibility

- Data public (paper): ALMA project 2013.1.01268.S acknowledged; no explicit statement of public access  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2013.1.01268.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration and imaging details in earlier papers
- Missing: Scale heights and distance of the physical model
- Missing: Exact model fitting procedure
- Missing: LIME input scripts
- Data volume (inferred): ~10-50 GB raw for a single Band 6 project
- Score (inferred): 3/5, Public ALMA data and clear model parameters, but the reduction is inherited, the fit is by eye and key model inputs are in other papers.
- Rediscovery candidate: no, Modelling relies on external physical structure and unstated inputs; results are not from a fully specified recipe.

## Links

- Method: (cite: Murillo2015) (Simplified DCO+ chemical network)
- Method: (cite: Mathews2013) (Physical disk model)
- Companion: (cite: Salinas2017) (Previous observational analysis of the same data)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "facts": 75,
  "stated": 37,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
