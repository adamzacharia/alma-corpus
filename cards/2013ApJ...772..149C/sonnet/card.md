# Constraining a Model of Turbulent Coronal Heating for AU Microscopii with X-Ray, Radio, and Millimeter Observations

`2013ApJ...772..149C` | The Astrophysical Journal 2013 | first author: Cranmer, Steven R. | arXiv: 1306.4567 | DOI: 10.1088/0004-637X/772/2/149

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: stellar_physics, debris_disks
- Question: Can a turbulence-driven coronal loop heating model for AU Mic reproduce the X-ray luminosity, the ALMA 1.3 mm central emission peak, and radio upper limits?  
  > "We aim to create a single model of these loops that reproduces the available observations at X-ray and millimeter wavelengths." (Introduction)
- Target **AU Microscopii (HD 197481, GJ 803)**: coordinates _not stated_; z/distance 9.91 pc  
  > "| Distance | 9.91 pc | (cite: vL07) |" (Table 1); distance from van Leeuwen 2007 (cite: vL07)  
  > "| Distance | 9.91 pc | (cite: vL07) |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00142.S
- bands: Band 6 (1.3 mm)  
  > "AU Mic was observed by ALMA with its Band 6 receivers over four 2 hr long scheduling blocks" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 April 23 to 2012 June 16  
  > "between 2012 April 23 and 2012 June 16" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **ROSAT PSPC**: X-ray response function used to synthesize L_X; observed L_X from Hünsch et al. 1999  
  > "we chose to use the response function of the *ROSAT* Position Sensitive Proportional Counter (PSPC) given by (cite: Ju03)" (3 Synthesis)
- Other facility **Chandra**: Published X-ray spectral fits and density limits used for comparison  
  > "(cite: SS10) produced a fit of the full *Chandra* spectrum of AU Mic with three plasma components" (4 Results)
- External data: ALMA 1.3 mm central peak flux 320 ± 60 μJy  
  > "| $S_{\nu}$ ($\lambda = 1.3$ mm) | 320 $\pm$ 60 $\mu$Jy | (cite: Mc13)$^{a}$ |" (Table 1) [from (cite: Mc13)]
- External data: Radio upper limits 210 μJy at 2.0 cm and 120 μJy at 3.7 cm  
  > "| $S_{\nu}$ ($\lambda = 2.0$ cm) | $<$ 210 $\mu$Jy | (cite: Wh94) |" (Table 1) [from (cite: Wh94)]
- External data: Observed log L_X = 29.74  
  > "observed value of $\log L_{\rm X} = 29.74$ (cite: Hu99)" (4 Results) [from (cite: Hu99)]

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

- Heating rate formulation and loop-length distribution N(L) ∝ L^-ε  
  > "Following (cite: Cr09), we define the heating rate" (2 Coronal Heating Model) [from (cite: Cr09)]
- Loop energy balance scaling laws  
  > "We use the energy balance model of (cite: Ma10) to solve for the temperature $T$ and electron number density $n_e$" (2 Coronal Heating Model) [from (cite: Ma10)]
- Mean atomic weight parameterization and B* equipartition constant  
  > "We used the proportionality constant found from observations by (cite: CS11)" (2 Coronal Heating Model) [from (cite: CS11)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA data reduction behind the 320 μJy flux (in MacGregor et al. 2013)
- Code implementing the model
- Numerical values of the Martens (2010) proportionality constants
- Details of the stellar wind model used for mass loss

## Analysis recipe

1. **Compute single-length loop models**: Heating rate from turbulent cascade, with the Martens (2010) scaling laws solved iteratively for T_max, P, ρ, α  
  > "we solve for these quantities iteratively by starting with the initial guess that the density is given by $\rho_{\ast}$" (2 Coronal Heating Model)
   - parameter: 50 iterations; 100 loop lengths on a log grid between L_min and L_max  
  > "we run it for a total of 50 iterations to ensure accuracy" (2 Coronal Heating Model)
   - assumption: f* = 1; L_max = R*; T minimum 10^4 K at coronal base  
  > "The minimum value of $T$ at the coronal base was fixed at $10^4$ K." (2 Coronal Heating Model)
   - fitting: _not stated_
   - validation: _not stated_
2. **Synthesize X-ray and radio/mm emission**: L_X from the ROSAT PSPC loss function; free-free radiative transfer for radio/mm; convolve over N(L)  
  > "then we convolved them together using $N(L)$ to produce a result that is weighted properly" (3 Synthesis)
   - parameter: Grid 250 v_perp × 250 ε, 0.2–200 km/s, ε 0–2.5  
  > "The $250 \times 250$ grid encompasses the ranges $0.2 \leq v_{\perp} \leq 200$ km s$^{-1}$ and $0 \leq \varepsilon \leq 2.5$." (Footnote 2)
   - assumption: Vertical loops, no limb effects, S_ν = π R*² I_ν / D²  
  > "Thus, we used $S_{\nu} = \pi R_{\ast}^{2} I_{\nu} / D^{2}$." (3 Synthesis)
   - fitting: Best model is where L_X and 1.3 mm flux contours intersect; no formal fit  
  > "the two empirical constraints intersect one another (roughly perpendicularly) at a single parameter value" (4 Results)
   - validation: Compared with Chandra temperatures, densities, UV pressure and radio upper limits  
  > "Our best-fitting solution sits comfortably in the region that is consistent with all of the observed radio upper limits." (4 Results)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit v_perp | 1.5545 | not stated | km/s | 2 | This best-fitting model has a basal velocity amplitude $v_{\perp} = 1.5545$ km s$^{-1}$ |
| Best-fit loop-length exponent ε | 1.245 | not stated | dimensionless | 2 | a loop distribution power-law exponent $\varepsilon = 1.245$ |
| Loop T_max range | 3.7 to 7.2 | not stated | MK | 2 | peak temperatures between 3.7 MK (for $L_{\rm min}$) and 7.2 MK (for $L_{\rm max}$) |
| Model mass loss rate at v_perp=1.5545 km/s | 9e-12 | not stated | Msun/yr | 2 | the (cite: CS11) mass loss rate increases to $9 \times 10^{-12} \, M_{\odot}$ yr$^{-1}$ |

## Qualitative findings

- The coronal model is an alternative to an inner asteroid belt, but both may contribute to the 1.3 mm peak  
  > "it is also possible that the central 1.3 mm peak is caused by a combination of active coronal emission and a bright inner source of dusty debris." (abstract)

## Claim tuples

- H: Hot coronal loops can explain the ALMA central 1.3 mm peak of AU Mic | E: Grid of loop models compared to L_X and 1.3 mm flux | R: A single model with v_perp=1.5545 km/s and ε=1.245 matches both | F: Corona is a viable alternative explanation | **supported**
- H: The model is consistent with radio non-detections | E: Computed 2 cm and 3.7 cm fluxes | R: Best model lies below the upper limits | F: Consistent with all radio upper limits | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Inner asteroid belt within ~3 AU (MacGregor et al. 2013) cannot be ruled out  
  > "we do not yet have a definitive way to distinguish between this model and the idea of an inner asteroid belt" (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Only time-steady heating modeled; no flares, nonthermal emission, or 3D geometry  
  > "We limited ourselves to just the time-steady component of coronal heating and not the more intermittent flaring" (5 Discussion)
- Caveat (inferred, ours): v_perp and ε are tuned to two constraints, so the fit is degenerate
- Caveat (inferred, ours): Results depend on f* and unconstrained loop geometry
- Caveat (inferred, ours): No uncertainty on best-fit parameters

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Model code
- Missing: Martens (2010) constants
- Data volume (inferred): none (no ALMA data reprocessed)
- Score (inferred): 2/5, Pure theory with a published ALMA flux; equations are given but code and some constants are missing.
- Rediscovery candidate: no, The ALMA data are not reanalyzed; the work is a model calculation.

## Links

- Method: (cite: Cr09) (Source of heating model and loop distribution)
- Method: (cite: Ma10) (Loop energy balance scaling laws)
- Method: (cite: CS11) (Stellar parameter recipes and wind model)
- Companion: (cite: Mc13) (ALMA observation of AU Mic providing the 1.3 mm flux)

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
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
  "facts": 64,
  "stated": 24,
  "rate": 0.375
 },
 "evidence_ok": true
}
```
