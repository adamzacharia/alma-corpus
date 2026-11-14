# Ejection History of the IRAS 04166+2706 Molecular Jet

`2019ApJ...874...31W` | The Astrophysical Journal 2019 | first author: Wang, Liang-Yao | arXiv: 1902.06038 | DOI: 10.3847/1538-4357/ab07b5

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation
- Question: Can the saw-tooth velocity pattern of the IRAS 04166+2706 molecular jet be explained by a spherically expanding wind with axial density concentration, and what does it imply for the ejection history?  
  > "This pattern can be formed by a spherically expanding wind with axial density concentration." (abstract)
- Target **IRAS 04166+2706**: coordinates _not stated_; z/distance 140 pc  
  > "the first highly collimated, extremely high velocity bipolar outflow identified in the nearby Taurus molecular cloud (140 pc)" (Introduction); distance from Taurus molecular cloud distance  
  > "the first highly collimated, extremely high velocity bipolar outflow identified in the nearby Taurus molecular cloud (140 pc)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00304.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C32-2, no Morita Array  
  > "The array was in its C$32-2$ configuration and no observations with the compact Morita Array were made" (Introduction)
- baselines: _not stated_
- angular resolution: CO beam 1.5" x 1.1"  
  > "the beam-size of the CO data is $1.5\ensuremath{''}\times1.1\ensuremath{''}$." (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: December 2014 (ALMA data of Tafalla et al. 2017)  
  > "observed the two knots B6 and R6 of the I04166 outflow at 230.5 GHz using ALMA in December 2014." (Introduction)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.5 GHz)
- Other facility **IRAM PdBI**: CO J=2-1 PV diagram of the whole jet (with single-dish data added), compared with the model  
  > "Single-dish data were added to the visibility to improve the quality of the CO $J=$ 2 – 1 images, and the beam-size of the combined data is $3\ensuremath{''}$." (Introduction)
- Other facility **SMA**: CO J=3-2 data of inner knots (Wang et al. 2014)  
  > "The CO $J=$ 3 – 2 data of (cite: wang2014) taken in 2010 by the SMA covered the inner four pairs of knots" (Introduction)
- External data: ALMA CO J=2-1 observations of knots B6 and R6 and inclination estimate of 38 deg from the plane of the sky  
  > "This is the average angle estimated by (cite: tafalla2017) based on the elliptical shapes of the knots B6 and R6 in their ALMA observations." (2 Analytic View) [from (cite: tafalla2017)]
- External data: PdBI CO J=2-1 PV diagram and data provided by the authors  
  > "We thank M. Tafalla and J. Santiago-García for providing the CO $J=$ 2 – 1 data of the molecular outflows IRAS 04166$+$2706." (Acknowledgments) [from (cite: santiago-garcia2009)]
- Simulation/model as data: 2D axisymmetric unified wind model simulations with two-temperature scheme, synthetic CO J=2-1 PV diagrams and channel maps  
  > "Our simulations build upon the unified wind model framework outlined in (cite: shang2006) with detailed simulation setups following the two-temperature generalization described in (cite: wang2015)." (3 Numerical Simulations)

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

- Simulation setup follows the two-temperature generalization  
  > "detailed simulation setups following the two-temperature generalization described in (cite: wang2015)" (3 Numerical Simulations) [from (cite: wang2015)]

### Not stated but needed to reproduce (our reading)

- Simulation code name, grid and resolution not given
- Exact velocity values per burst not tabulated
- Coordinates of the source and the knot positions/velocities picked from PV diagrams
- ALMA calibration and imaging details (in Tafalla et al. 2017)

## Analysis recipe

1. **Analytic slope model**: Derive the tooth slope on the PV diagram vs. inclination for a spherical wind layer; overlay on observed CO 2-1 PV with 28, 38, 48 deg  
  > "At each knot position, we overlay three sets of velocity pattern computed with different inclination angles on top of the observed CO $J=$ 2 – 1 data." (2 Analytic View)
   - parameter: half-opening angle 7.5 deg displayed  
  > "we display the model pattern up to a half-opening angle of $\alpha=7.5$$^\circ$ from the rough center of each tooth." (2 Analytic View)
   - fitting: _not stated_
   - validation: Same inclination reproduces most knots  
  > "The overall behavior of the whole sawtooth velocity pattern can therefore be generally explained with one same inclination angle" (2 Analytic View)
2. **Estimate inclination from dimensionless slope**: Manually pick two points per tooth, compute eta-hat and theta; error from shifting a point by 140 AU  
  > "we displace the upper selected point in each pattern to the left and right by 140 AU" (2 Analytic View)
   - fitting: _not stated_
   - validation: _not stated_
3. **Numerical simulations with variable velocity history**: Unified wind simulations with burst or low-high cycle velocity history; synthetic PVs convolved with 3" beam  
  > "each having a constant speed and lasts for $20$ years long." (3.2 Modeling the Ejection History)
   - parameter: period ~93 yr; M_A=150; T=100 K; inclination 52 deg from line of sight; inner cone 3 deg  
  > "We adopt a large Alfvén Mach number of $M_A=150$ for purposes of better modeling." (3.1 Unified Wind Model)
   - assumption: Level populations in statistical equilibrium, radiative effects ignored; line width 1 km/s  
  > "For simplicity, effects of radiative excitation and de-excitation on the level populations were ignored so the line emissions can be calculated locally." (3.1 Unified Wind Model)
   - fitting: Velocity histories designed by hand to fit  
  > "The velocities of the ejecta are designed so as to let them travel ballistically to the observed location by the time of $t=0$." (3.2 Modeling the Ejection History)
   - validation: Compare convolved synthetic PV and channel maps with observations  
  > "Although not perfectly, our numerical simulations successfully reproduce the observed velocity pattern." (3.2 Modeling the Ejection History)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean inclination from plane of sky, blue lobe | 38.4 | not stated | deg | 2 | The mean inclination angle values are $38.4$$^\circ$ and $37.6$$^\circ$ for the blue and red shifted lobes |
| Mean inclination from plane of sky, red lobe | 37.6 | not stated | deg | 2 | The mean inclination angle values are $38.4$$^\circ$ and $37.6$$^\circ$ for the blue and red shifted lobes |
| Dimensionless slope range | ~-3 to -1 | not stated | dimensionless | 2 | The value of $\hat{\eta}$ falls in the range of $\sim-3$ to $-1$. |
| Ejection periodicity | ~93 | not stated | yr | 3 | we will try to follow a periodicity of $\sim93$ year, which is estimated from the roughly equal spacing of the first few knots |
| Dynamical age of fitted region | ~1200 | not stated | yr | 3 | The dynamical age of the fitted regions (up to knots B7 and R7) is about 1200 years. |

## Qualitative findings

- Outer knots are well described by thin spherical shells; inner knots retain velocity history and need continuous variation  
  > "the more evolved outer knots are indeed well described by the model of thin spherical shell." (3.2 Modeling the Ejection History)

## Claim tuples

- H: A spherical wind with axial density concentration explains the sawtooth PV pattern | E: Analytic projection model compared with CO 2-1 PV diagram | R: One inclination of ~38 deg fits most knots | F: The pattern is a projection effect of a wind-like velocity field | **supported**
- H: The unified wind model can reproduce the pattern | E: Simulations with bursty or cyclic velocity history, synthetic PVs | R: Observed sawtooth reproduced, though not perfectly | F: Wind geometry is feasible | **supported**
- H: Inner knots follow the same simple slope relation | E: Inclination from eta-hat per knot | R: Inferred theta decreases systematically outward | F: The simple model is incomplete for inner knots | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Jet with internal working surface side-way ejection cannot be ruled out, but it does not naturally explain the coherent slope variation  
  > "although this does not rule out the possibility of a jet shock." (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Axisymmetric model cannot represent asymmetric knot B6; knot B7 not reproduced  
  > "The asymmetric knot is not well represented by the current axisymmetric model." (3.2 Modeling the Ejection History)
- Caveat (inferred, ours): ALMA data are only used indirectly via Tafalla et al. 2017 and PdBI data
- Caveat (inferred, ours): Velocity histories are hand-tuned, so fits are not unique
- Caveat (inferred, ours): Model is qualitative with no quantitative goodness of fit

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Simulation code and parameters
- Missing: Digitized PV data and picked points
- Data volume (inferred): small (published PV diagrams; simulations only)
- Score (inferred): 2/5, Mainly theory and simulation with unreleased code; ALMA data enter only through earlier publications.
- Rediscovery candidate: no, Main results are simulation-based and the recipe is incomplete.

## Links

- Method: (cite: shang2006) (Unified wind model framework)
- Method: (cite: wang2015) (Two-temperature simulation setup)
- Companion: (cite: tafalla2017) (ALMA observations of knots B6 and R6)
- Companion: (cite: santiago-garcia2009) (PdBI CO and SiO maps of the outflow)

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
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
  "facts": 64,
  "stated": 24,
  "rate": 0.375
 },
 "evidence_ok": true
}
```
