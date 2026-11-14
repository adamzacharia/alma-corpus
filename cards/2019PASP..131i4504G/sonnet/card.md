# Stochastic Modeling of the Time Variability of ALMA Calibrators

`2019PASP..131i4504G` | Publications of the Astronomical Society of the Pacific 2019 | first author: Guzmán, A. E. | arXiv: 1907.03528 | DOI: 10.1088/1538-3873/ab2d38

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, agn_and_quasars
- Question: Can mixtures of Ornstein-Uhlenbeck processes describe the multi-frequency flux and spectral index variability of ALMA grid calibrators, and provide forecasts, interpolations and uncertainties?  
  > "We find that simple mixtures of Ornstein-Uhlenbeck processes can describe well the flux and spectral index variability of these sources for Bands 3 and 7" (abstract)
- Target **39 ALMA grid calibrator quasars (e.g. J0635-7516)**: coordinates given per source in Table 1  
  > "J0635$-$7516 | 06:35:46.508 | $-$75:16:16.82 | 2012-06-30 | 2018-07-07 | 758" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 and 7 (mostly 91.5, 103.5 and 343.5 GHz), some Band 6  
  > "mostly at 91.5 and 103.5 GHz, and at 343.5 GHz, respectively." (2 ALMA grid calibrator data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Morita ACA from Cycle 5 on  
  > "from Cycle 5 on, observations for the calibrator survey are performed using the Morita ALMA compact array (ACA) and the ACA correlators." (2 ALMA grid calibrator data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 2-4 minutes per grid calibrator  
  > "On-source time spent on each grid calibrator varies between 2–4 minutes." (2 ALMA grid calibrator data)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **ALMACAL**: Additional calibrator measurements, including Bands 8-10, used for J2253+1608  
  > "Additional measurements for many calibrators are provided by the ALMACAL survey" (Combining calibrator survey with additional data)
- External data: Grid calibrator list (Table 10.1 of the ALMA Technical Handbook) and public calibrator source catalogue flux densities  
  > "The list of secondary flux calibrators known as the grid sources is given by Table 10.1 from ." (2 ALMA grid calibrator data) [from ALMA Technical Handbook (Warmels et al. 2018)]
- Simulation/model as data: 100 simulated OU-1F1a light-curves (400 measurements each, 1080 d) used to test MLE recovery  
  > "we generate 100 OU-1F1a simulated light-curves at 91.5, 103.5, and 343.5 GHz" (Performance in simulated data)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Flux densities taken from the public ALMA calibrator source catalogue  
  > "The flux densities used in the light-curves analyzed in this work come from data taken by the calibration survey and reported in the source catalog." (Combining calibrator survey with additional data)
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

- Data reduction of grid calibrator survey and OU mixture formalism follow earlier works  
  > "More details about the design, observational strategy, and data reduction procedure of the grid calibrator survey can be found in ." (2 ALMA grid calibrator data) [from not stated (citation lost in text)]

### Not stated but needed to reproduce (our reading)

- Exact catalogue download date and version, and the 20 masked outlier points (only in supplementary text file)
- Minuit starting values and bounds
- Metropolis-Hastings chain length and step size
- Selection criteria for the best model per source beyond heuristic judgement

## Analysis recipe

1. **Fit simple spectral model and compute variability index**: Least-squares fit of power law to all data per source at nu0=100 GHz; vix computed  
  > "we obtain least squared fitted parameters to all the data available for each calibrator, disregarding its variability." (2 ALMA grid calibrator data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit OU-mixture models by maximum likelihood**: State space representation with Kalman recursions to compute likelihood; MLE of OU-rFsa models with optional curvature and nu-lag  
  > "To calculate the likelihood function we use the state space representation of each process together with the Kalman recursions" (Determination of the best-fit stochastic model)
   - software: Minuit, PDL
   - parameter: r<=2, s<=1; sigma_N proportional to nu^1/2  
  > "In practice, for this work we use $r\le2$ and $s\le1$ models." (OU-rFsa plus noise process)
   - assumption: _not stated_
   - fitting: Likelihood maximization with Minuit; parabolic uncertainties from Hessian  
  > "We use the `Minuit` (cite: JAMES1975343) package implemented within `PDL`[^2] to obtain the MLE and their uncertainties." (Determination of the best-fit stochastic model)
   - validation: AIC, normalized residuals, Anderson-Darling test, ACF, Ljung-Box; recovery on 100 simulated light-curves  
  > "We test the normality of the residuals running the Anderson-Darling test" (Quality of the best-fit model)
3. **Forecasts, interpolation and uncertainties**: Kalman forecasts with stochastic plus parametric uncertainty added in quadrature; compared against next measurements, a Metropolis-Hastings posterior and the P0 interpolation  
  > "we calculate the total uncertainty on the forecast as the sum in quadrature of the parametric and stochastic uncertainties." (Uncertainty of the predictions)
   - software: R, PDL
   - fitting: Metropolis-Hastings MCMC with constant prior starting from MLE  
  > "We sample the posterior using a Metropolis-Hastings Markov chain (cite: gregory2005bayesian) starting from the MLE" (Forecasts and uncertainty intervals)
   - validation: Standardized forecast differences against subsequent measurements (56 Band 3, 41 Band 7)  
  > "For the full grid sample, there are 56 and 41 of these measurements in total for Bands 3 and 7, respectively." (Forecasts and uncertainty intervals)

## Software

- **R** v. 3.5.0: Lomb-Scargle periodogram, ACF, simulation scripts  
  > "R (v. 3.5.0) computer programs to generate the simulated datasets" (Supplementary material)
- **Minuit** : Maximum likelihood estimation within PDL  
  > "We use the `Minuit` (cite: JAMES1975343) package implemented within `PDL`[^2] to obtain the MLE and their uncertainties." (Determination of the best-fit stochastic model)
- **PDL** : Kalman recursion implementation  
  > "PDL code implementing the Kalman recursions (Appendix A) is given in the supplementary material" (Supplementary material)
- **goftest** : Anderson-Darling test  
  > "using the `ad.test` task from package `goftest`" (Quality of the best-fit model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stochastic model interpolation scatter vs P0 for J0635-7516, Band 3 | 3% (OU-1F1a) vs 7% (P0) | not stated | percent | 3 | For P0, the standard deviation of the differences at Bands 3 and 7 are 7% and 11%, respectively |
| Spectral indices of 32 of 39 sources range | -0.35 to -0.80 | not stated | dimensionless | 1 | with 32 out of 39 spectral indices between $-0.35$ and $-0.80$ |
| Sources with significant nu-lag | 5 | not stated | sources | 2 | Five sources are apparently characterized by a significant frequency dependent lag between their Band 3 and 7 light-curves. |

## Qualitative findings

- Spectral-index OU term and concavity substantially improve fits over single OU with constant index  
  > "We see that the addition of stochastic time-variability to the spectral index (a $\beta$ term) accounts for a significant diminishing in the AIC ($\sim420$)." (Results)

## Claim tuples

- H: Can OU mixtures model calibrator multi-frequency variability? | E: MLE fits to 39 grid calibrators in Bands 3 and 7 with residual diagnostics | R: Selected models include spectral-index variation for 38 sources; residuals near white noise | F: OU mixtures describe the variability well | **supported**
- H: Does stochastic interpolation beat the pipeline-like P0 method? | E: Leave-one-day-out interpolation for J0635-7516 and phase calibrators | R: Lower scatter for stochastic model (3%/5% vs 7%/11%); lower median in 26 of 40 cases | F: Stochastic interpolation is better | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Decorrelation time poorly constrained because monitoring baseline is short  
  > "Specifically, the decorrelation time — which is defining of the OU-process — cannot be recovered." (Drawbacks and future refinements)
- Caveat (inferred, ours): Gaussian and stationarity assumptions
- Caveat (inferred, ours): Calibrator fluxes depend on SSO calibration, correlated errors not modelled
- Caveat (inferred, ours): Model selection per source is heuristic

## Reproducibility

- Data public (paper): Public ALMA calibrator source catalogue  
  > "Flux densities, positions, and calibrator type can be obtained from the online source catalogue." (2 ALMA grid calibrator data)
- Products in archive: _not stated_
- Code: PDL Kalman code in supplementary material and ASCL; R scripts for simulations  
  > "can also be obtained from the Astrophysics Source Code Library" (Supplementary material)
- Missing: Snapshot of catalogue used
- Missing: Outlier list only in supplement
- Data volume (inferred): Tiny (catalogue light-curves, under 1 MB)
- Score (inferred): 4/5, Public catalogue, code released, clear equations; some details only in supplement.
- Rediscovery candidate: yes, Public catalogue data, complete recipe, numeric tables of fit parameters.

## Links

- Method: Kelly et al. 2011 (cite: Kelly2011ApJ) (OU mixture models formalism)
- Companion: Bonato et al. 2018 (cite: Bonato2018MNRAS) (ALMACAL calibrator variability comparison)
- Related: ALMA calibrator grid survey
- Related: ALMACAL

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 26,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
