# Dynamical Inference from Polarized Light Curves of Sagittarius A<SUP>*</SUP>

`2025ApJ...987..152R` | The Astrophysical Journal 2025 | first author: Ricarte, Angelo | arXiv: 2504.01114 | DOI: 10.3847/1538-4357/add729

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: agn_and_quasars, milky_way_ism
- Question: Can the average rotation rate and handedness of Q-U loops in Sgr A* polarized light curves be measured and used to constrain accretion flow dynamics via GRMHD models?  
  > "we apply the differential geometry of planar curves to develop a new technique for estimating polarimetric rotation rates." (abstract)
- Target **Sagittarius A***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01404.V, 2016.1.00413.V
- bands: _not stated_
- frequencies and spectral setup: 212.1-216.1 and 226.1-230.1 GHz sub-bands; analysis focuses on 228.1-230.1 GHz  
  > "These data were obtained at 212.1-216.1 GHz and 226.1-230.1 GHz as part of the EHT+ALMA observations of Sgr A$^*$" (3 Light Curve Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017 April 6, 7, 11 (EHT+ALMA); 86-100 GHz on 2017 April 3  
  > "On April 3rd, 2017, polarized light curves in 85.3-89.3 GHz and 97.3-101.3 GHz were also recorded as a part of GMVA+ALMA observations" (6 Discussion)
- pi or archival as stated: _not stated_
- Other facility **EHT**: 2017 campaign context; ALMA phased array light curves  
  > "as part of the EHT+ALMA observations of Sgr A$^*$" (3 Light Curve Analysis)
- External data: 230 GHz polarized Sgr A* light curves (Stokes Q, U) from ALMA 2017  
  > "millimeter light curves presented in (cite: Wielgus2022QU)" (3 Light Curve Analysis) [from (cite: Wielgus2022QU)]
- External data: 86-100 GHz GMVA+ALMA light curves, reduced and published  
  > "The light curves were reduced and published in (cite: Wielgus+2024)." (6 Discussion) [from (cite: Wielgus+2024)]
- Simulation/model as data: KHARMA GRMHD library ray-traced with ipole: MAD/SANE, 5 spins, 9 inclinations, 4 Rhigh, aligned fields; analysed 15000-30000 tg  
  > "we consider the library run using the General Relativistic Magnetohydrodynamics (GRMHD) code KHARMA (cite: Prather2024), subsequently ray-traced using the General Relativistic Ray-tracing (GRRT) code ipole" (2.1 Images from GRMHD)

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

- Simulation library and polarized images  
  > "We use as our starting point a library of polarized model images of Sgr A$^*$ presented in (cite: EHTC+2022e; EHTC+2024c)" (2.1 Images from GRMHD) [from (cite: EHTC+2022e; EHTC+2024c), Patoka pipeline (cite: Wong+2022)]
- Windowed estimation across 10 windows of simulations  
  > "This is consistent with the methodology of (cite: EHTC+2024c)." (4 Model Comparison) [from (cite: EHTC+2024c)]

### Not stated but needed to reproduce (our reading)

- Calibrated Stokes Q,U light curve files (taken from Wielgus et al. 2022)
- GRMHD library images (not public in paper)
- Exact numerical differentiation and segmentation details beyond three-point scheme
- Smoothing spline handling of gaps/weights

## Analysis recipe

1. **Pre-process light curves**: Split into segments at gaps >=1.8 min, fit smoothing splines to Q and U, trim edge points  
  > "we fit a smoothing spline of polynomial order $\kappa \in \{3,4,5\}$ with smoothing factor $\sigma \in \{0.1,0.5\}$ using the Python function `scipy.interpolate.UnivariateSpline`." (3 Light Curve Analysis)
   - software: scipy
   - parameter: kappa in {3,4,5}, sigma in {0.1,0.5}, n_T in {0,1,2,3}  
  > "$\kappa \in \{3,4,5\}$, $\sigma \in \{0.1,0.5\}$, and $n_T \in \{0,1,2,3\}$" (3 Light Curve Analysis)
   - fitting: _not stated_
   - validation: Splines visually characterize Q and U without obvious over-fitting  
  > "We find that these splines are generally able to characterize the $Q$ and $U$ behavior well, without obvious over-fitting." (3 Light Curve Analysis)
2. **Compute Q-U rotation rate and clockwise fraction**: Signed curvature from three-point derivatives, integrated to total curvature; Omega_QU = slope; f_CW from sign per scan; mean and std over meta-parameter grid as systematic error  
  > "We report the mean and use the standard deviation of these values as a systematic error bar" (3 Light Curve Analysis)
   - parameter: speed limit 2pi/5 rad per tg; curvature zeroed above it  
  > "we place a “speed limit” of $2\pi / 5 \ \mathrm{rad}\,\mathrm{t_g}^{-1}$." (2.2 Differential Geometry of Loops)
   - fitting: _not stated_
   - validation: Applied to GRMHD example; 5 tg boxcar smoothed data compared  
  > "we also compute an all-day fit on light curves first smoothed with a boxcar filter with duration 5$t_g$, resulting in $\Omega_{QU} = -2.8 \pm 1.0 \ \mathrm{deg} \, t_g^{-1}$" (Light Curve Analysis)
3. **Compare with GRMHD library**: Compute Omega_QU and f_CW in 10 windows of 1500 tg per model; models pass if 1 sigma regions overlap observations  
  > "Models pass if their 1$\sigma$ confidence region overlaps with the 1$\sigma$ confidence region of observations." (4 Model Comparison)
   - parameter: 25 tg segments within 1500 tg windows  
  > "we consider the fraction of $25 \ t_g$ segments within each $1500 \ t_g$ window which are clockwise." (4 Model Comparison)
   - fitting: _not stated_
   - validation: 90 percent overlap test as robustness check  
  > "In previous EHT studies, a more permissive 90 percent confidence region overlap was used" (Scoring Consistent with Previous EHT Studies)

## Software

- **scipy.interpolate.UnivariateSpline** : Smoothing splines of Q and U  
  > "using the Python function `scipy.interpolate.UnivariateSpline`" (3 Light Curve Analysis)
- **KerrBAM** : Hotspot Q-U loop toy model  
  > "generated using the code `KerrBAM` (cite: Palumbo_2022)" (6 Discussion)
- **KHARMA** : GRMHD simulations  
  > "General Relativistic Magnetohydrodynamics (GRMHD) code KHARMA (cite: Prather2024)" (2.1 Images from GRMHD)
- **ipole** : GRRT ray tracing  
  > "General Relativistic Ray-tracing (GRRT) code ipole (cite: Moscibrodzka&Gammie2018)" (2.1 Images from GRMHD)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| All-days Q-U rotation rate | -2.6 | 0.6 | deg tg^-1 | 2 | All Days / $-2.6 \pm 0.6$ / $0.65 \pm 0.09$ |
| All-days clockwise fraction | 0.65 | 0.09 | dimensionless | 2 | All Days / $-2.6 \pm 0.6$ / $0.65 \pm 0.09$ |
| April 11th T0-T7 rotation rate | -4.0 | 0.7 | deg tg^-1 | 2 | April 11th ($T_0$-$T_7$) / $-4.0 \pm 0.7$ / $0.82 \pm 0.09$ |
| All days 5tg pre-smoothed rate | -2.8 | 1.0 | deg tg^-1 | 2 | All Days (5$t_g$ pre-smoothed) / $-2.8 \pm 1.0$ / $0.67 \pm 0.11$ |
| 100 GHz rotation rate | 1.4 | 0.7 | deg tg^-1 | 2 | $\Omega_{QU} = 1.4 \pm 0.7 \ \mathrm{deg}\,\mathrm{t_g}^{-1}$ at 100 GHz |

## Qualitative findings

- Face-on clockwise MAD models are most likely to match; SANE models too depolarized  
  > "face-on and clockwise ($i>90^\circ$) MAD models are most likely to match observational constraints." (4 Model Comparison)

## Claim tuples

- H: Clockwise Q-U motion exists on quiescent days, not only post-flare | E: Curvature-based rotation rate on 2017 ALMA light curves | R: Omega_QU=-2.6±0.6 deg/tg, f_CW=0.65±0.09 | F: Clockwise motion on all three days | **supported**
- H: GRMHD models can be constrained by Omega_QU and f_CW | E: Compare 1 sigma overlap for model library | R: Face-on clockwise MAD models pass | F: Favors clockwise-rotating strongly magnetized flows, supporting external Faraday screen | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Antonopoulou+2025 model of counter-clockwise disk with clockwise hotspots appears disfavored  
  > "Our analysis appears to disfavor this model" (6 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): 86-100 GHz results inconclusive  
  > "We therefore report inconclusive results at this band." (6 Discussion)
- Caveat (inferred, ours): Systematic error from spline meta-parameter grid is not a true statistical uncertainty
- Caveat (inferred, ours): Only three days of data; correlated segments
- Caveat (inferred, ours): Method insensitive to Faraday screen so inference is indirect
- Caveat (inferred, ours): Model library limited to thermal electrons, aligned fields

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: GRMHD image library access
- Missing: Light curve data tables
- Missing: Analysis code
- Data volume (inferred): small (light curves only); GRMHD library large
- Score (inferred): 3/5, Method is well specified and light curves are public via prior paper, but simulation library and code not stated as released.
- Rediscovery candidate: no, Needs the GRMHD library and published light curves; recipe depends on external data.

## Links

- Method: (cite: Wielgus2022QU) (Source of light curves and loop analysis)
- Companion: (cite: EHTC+2024c) (Simulation library and best-bet model)
- Related: EHT 2017 campaign
- Related: GMVA+ALMA

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 25,
  "rate": 0.368
 },
 "evidence_ok": true
}
```
