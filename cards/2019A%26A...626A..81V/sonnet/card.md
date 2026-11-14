# Resolving the extended stellar atmospheres of asymptotic giant branch stars at (sub)millimetre wavelengths

`2019A&A...626A..81V` | Astronomy and Astrophysics 2019 | first author: Vlemmings, W. H. T. | arXiv: 1904.06374 | DOI: 10.1051/0004-6361/201935329

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What are the brightness temperature structure, hotspots, variability and opacity structure of the extended atmospheres of four nearby AGB stars at (sub)mm wavelengths?  
  > "We resolve all four AGB stars and determine the brightness temperature structure between $1$ and $2$ stellar radii." (abstract)
- Target **Mira A**: coordinates _not stated_; z/distance 100 pc  
  > "| Mira A | 100 | 15 | 332 |" (Table 1); "We adopt $100$ pc." (2.1 Mira A); distance from adopted between Hipparcos 92±10 pc and period-luminosity 110±9 pc  
  > "| Mira A | 100 | 15 | 332 |" (Table 1); "We adopt $100$ pc." (2.1 Mira A)
- Target **R Dor**: coordinates _not stated_; z/distance 60 pc  
  > "A distance of $\sim60$ pc is obtained from observations using *Hipparcos* (cite: Knapp2003)" (2.2 R Dor); distance from Hipparcos (cite: Knapp2003) and near-IR aperture masking (cite: Bedding1997)  
  > "A distance of $\sim60$ pc is obtained from observations using *Hipparcos* (cite: Knapp2003)" (2.2 R Dor)
- Target **W Hya**: coordinates _not stated_; z/distance 98 pc (Table 1)  
  > "The distance to W Hydrae is found to be $\approx 100$ pc, from VLBI astrometry of maser spots (cite: Vlemmings2003)" (2.3 W Hya); distance from VLBI maser astrometry and Hipparcos  
  > "The distance to W Hydrae is found to be $\approx 100$ pc, from VLBI astrometry of maser spots (cite: Vlemmings2003)" (2.3 W Hya)
- Target **R Leo**: coordinates _not stated_; z/distance 71 pc  
  > "Still, we used $71$ pc in our analysis." (2.4 R Leo); distance from Gaia (cite: vL19), flagged as low quality  
  > "Still, we used $71$ pc in our analysis." (2.4 R Leo)

## Data provenance

- ALMA projects: 2016.1.00004.S, 2016.A.00029.S, 2017.1.00075.S, 2017.1.00191.S, 2017.1.00862.S
- bands: Bands 4, 6 and 7  
  > "| 2017-09-21 | 2016.1.00004.S | 4 | $131.28$ |" (Table 1)
- frequencies and spectral setup: four spws of 1.95 GHz bandwidth each, spectral line mode  
  > "All observations were taken in spectral line mode, with four spectral windows (spws) with a bandwidth of $1.95$ GHz each." (3 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: maximum baselines 10 to 16.2 km  
  > "in some of the longest baseline ALMA configurations with maximum baselines between 10 and 16.2 km" (3 Observations and data reduction)
- angular resolution: beam sizes ~19 to 74 mas (Table 1)  
  > "| 2017-10-03 | 2017.1.00862.S | 6 | $215.19$ | $19\times19$, $73$ | $40$ |" (Table 1)
- max recoverable scale: ~0.4'' at longest wavelengths to ~0.2'' at shortest  
  > "ranges from $\sim0.4\ensuremath{''}$ at the longest wavelengths to $\sim0.2\ensuremath{''}$ at the shortest wavelengths" (3 Observations and data reduction)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 21 September to 25 November 2017  
  > "The observations presented in this paper were taken between 21 September and 25 November 2017" (3 Observations and data reduction)
- pi or archival as stated: Projects with PIs Vlemmings, Khouri; R Leo data from project of PI Kaminski retrieved from archive  
  > "we retrieved archive data of R Leo taken between our observations as part of project 2017.1.00862.S (PI: Kaminski)." (3 Observations and data reduction)
- External data: Stellar radii R_* adopted from near-IR measurements (Mira A, R Leo) and others  
  > "We used $R_*=15$ mas, which is the smallest measurement of (cite: Woodruff2009) in the analysis." (2.1 Mira A) [from (cite: Woodruff2009)]
- External data: Absorption coefficients for electron-neutral free-free opacity (third-order polynomial fits)  
  > "To calculate the opacity, we use the RM97 third-order polynomial fits to the absorption coefficients calculated by (cite: DL66)." (5.1 Parameterised model atmospheres) [from (cite: RM97); (cite: DL66)]
- External data: Mira B subtracted from Mira A data  
  > "For Mira A, we performed the fits after its companion Mira B was subtracted from the data." (4 Results) [from not stated]

## Processing

### Calibration

- pipeline or manual: CASA pipeline for several datasets, manual calibration by observatory staff for others  
  > "was done using the Common Astronomy Software Applications (CASA) package pipeline (cite: McMullin07), while others were manually calibrated by observatory staff using different version of CASA." (3 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasars per Table 1; R Leo Band 4 recalibrated with J1002+1216 renormalised to 136 mJy at 135 GHz  
  > "the flux densities in these observations were recalibrated using a renormalised flux density for the gain calibrator (J1002+1216) of $136$ mJy at $135$ GHz." (3 Observations and data reduction)
- flux scale uncertainty: ~5% for R Leo Band 4; 10% assumed otherwise  
  > "For the other sources only a single epoch was available at each observing band and we assume a $10\%$ uncertainty for all bands." (3 Observations and data reduction)
- self calibration: Phase-only self-cal; SiO maser spw used for first two steps where present, then 1-2 continuum phase steps; no amplitude self-cal  
  > "No amplitude self-calibration was performed and for the data sets without SiO masers, only continuum self-calibration was done." (3 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust +0.5 for Table 1 rms/beam; uniform weighting for illustration images  
  > "The images were produced using uniform weighting in order to reach the highest resolution." (4 Results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: spectral smoothing to 20 channels and time smoothing to 10 s before continuum self-cal  
  > "performed spectral (20 channels) and time smoothing (10 sec) to reduce the data size." (3 Observations and data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- uv-fitting approach with uvmultifit as in earlier W Hya work  
  > "Most of our analysis is performed using the *uv*-fitting code *uvmultifit* (cite: MartiVidal14) in a similar manner as described in (cite: Vlemmings17)." (4 Results) [from (cite: Vlemmings17)]
- Residual phase-error size uncertainty approach  
  > "Adopting the approach described in (cite: Matthews15), we conservatively find that a relative error term, with respect to the measured size" (4 Results) [from (cite: Matthews15)]
- Model atmosphere based on radio-photosphere model  
  > "We constructed a simple parameterised model atmosphere based on the radio-photosphere model of RM97" (5.1 Parameterised model atmospheres) [from (cite: RM97)]
- R_* for W Hya adopted for consistency  
  > "For consistency with (cite: Vlemmings17) we adopt $R_*=20$ mas $\approx1.96$ au." (2.3 W Hya) [from (cite: Vlemmings17)]

### Not stated but needed to reproduce (our reading)

- uvmultifit settings (initial guesses, weights, per-spw handling)
- CASA versions used
- line-free channel selection and self-cal solution intervals
- how Mira B was subtracted
- image sizes, cell sizes and clean parameters
- model fitting procedure for atmosphere parameters (done by eye or fit?)
- uv-range cutoffs per spw for all sources

## Analysis recipe

1. **Recalibrate and self-calibrate**: Inspect calibration, extra flagging, recalibrate R Leo Band 4 fluxes, phase-only self-calibration  
  > "After the initial calibration, we performed self-calibration." (3 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: S/N improved from ~100 to ~1000 or better  
  > "The self-calibration generally improved the S/N from $\sim100$ to $\sim1000$ or better." (3 Observations and data reduction)
2. **Fit uniform elliptical disc in uv plane per spw**: Fit flux density, major axis, axis ratio and position angle per spw  
  > "We fit a uniform elliptical stellar disc for each of the spws in our observations." (4 Results)
   - software: uvmultifit
   - parameter: uv range restricted to >2 Mlambda (Band 4) or >3 Mlambda (Bands 6,7) for spws with short-baseline excess  
  > "we restricted our fits to *uv* distances $>2$, or $>3$ M$\lambda$ for Band 4 and for Bands 6 and 7, respectively." (4 Results)
   - fitting: _not stated_
   - validation: Residual images after subtracting best-fit disc  
  > "The figures also show the residuals after subtracting the best-fit stellar disc model from the data in each spw." (4 Results)
3. **Derive brightness temperature and spectral index**: T_b from flux, size, axis ratio, frequency; spectral index via Monte Carlo with flux uncertainties  
  > "the spectral index and its associated error are determined by a Monte Carlo scheme." (4 Results)
   - assumption: 10% absolute flux uncertainty per band (5% for R Leo Band 4)  
  > "we include a $10\%$ absolute flux density uncertainty for the different bands (except for R Leo where we adopt a $5\%$ uncertainty in Band 4)." (4 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Parameterised atmosphere radiative transfer models**: Power-law density and grey/power-law temperature, ionisation power law, electron-neutral free-free opacity, Rayleigh-Jeans radiative transfer; compare size-frequency and T_b-size relations; add layer with 10x tau_ff increase at R_s  
  > "We thus produce a model, which we describe as a “layer” model that has a ten times increase in $\tau_{\rm ff}$ at a single “shock” radius ($R_s$)" (5.1 Parameterised model atmospheres)
   - parameter: alpha=6 reference; X_i,3000=7e-6; gamma=8  
  > "We adopt $\alpha=6$ for our reference model." (5.1 Parameterised model atmospheres)
   - assumption: Only atomic hydrogen interacts with electrons (no molecular H2 equilibrium)  
  > "We only consider interactions of the electrons with purely atomic hydrogen in our calculations." (5.1 Parameterised model atmospheres)
   - fitting: No formal fit stated; small parameter study  
  > "a number of conclusions can still be drawn from a small parameter study." (5.1 Parameterised model atmospheres)
   - validation: _not stated_
5. **Measure R Leo expansion**: Scale sizes to common frequencies and fit linear size growth over time  
  > "We can fit a linear expansion of $0.17\pm0.02$ mas day$^{-1}$ to the Band 4 data" (5.2 Expansion of R Leo)
   - assumption: distance 71 pc  
  > "when assuming a distance to R Leo of 71 pc" (5.2 Expansion of R Leo)
   - fitting: _not stated_
   - validation: Consistent with Band 6 sizes; uv comparison of first and last epoch  
  > "The fit indicates that the size change is robustly determined." (5.2 Expansion of R Leo)

## Software

- **CASA** : Pipeline/manual calibration and self-calibration  
  > "Common Astronomy Software Applications (CASA) package pipeline (cite: McMullin07)" (3 Observations and data reduction)
- **uvmultifit** : uv-plane fitting of uniform elliptical disc  
  > "uv-fitting code *uvmultifit* (cite: MartiVidal14)" (4 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| R Leo expansion velocity of mm surface | 10.6 | ±1.4 | km/s | 5 | for R Leo we directly measure an outward motion of the millimetre wavelength surface with a velocity of at least $10.6\pm1.4$ km s$^{-1}$ |
| R Leo linear size expansion (Band 4) | 0.17 | ±0.02 | mas/day | 5 | We can fit a linear expansion of $0.17\pm0.02$ mas day$^{-1}$ to the Band 4 data |
| Mira A size-frequency slope eta (Band 4-6) | -0.087 | ±0.006 | dimensionless | 4 | $\eta=-0.087\pm0.006$ is determined from the Band 4 and 6 observations |
| W Hya eta (Band 4) | -0.160 | ±0.007 | dimensionless | 4 | $\eta=-0.160\pm0.007$ in Band 4 |
| R Dor hotspot brightness above disc (Band 7) | >3300 | lower limit | K | 2 | we can determine a lower limit to $T_{\rm b}$ for both brightest hotspot of $>3300$ K above the average stellar disc temperature |
| W Hya Band 7 hotspots T_b | >10000 | lower limit | K | 2 | In Band 7, the two spots are very compact ($<2.6\times2.6$ mas) with $T_{\rm b}>10000$ K. |
| Mira A opacity layer radius | 1.4 | not stated | R_* | 4 | requires a sudden increase (moving inwards) in opacity by at least a factor of 10 at $R_s=1.4~R_*$ |

## Qualitative findings

- Mira A excess short-baseline emission extends over almost 5 R_*; origin uncertain (free-free, stacked lines, or dust)  
  > "the extended emission peaks towards the east of the star and extends over almost $5~R_*$" (5.4 Extended emission surrounding Mira A)

## Claim tuples

- H: Do the extended atmospheres show hotspots and deviations from sphericity? | E: uv fits and residual images of four stars | R: All stars show asymmetries; hotspots in W Hya and R Dor | F: Inhomogeneous atmospheres with convective cells/shocks | **supported**
- H: Is the mm surface of R Leo moving? | E: Six epochs of size measurements | R: Linear expansion 10.6±1.4 km/s | F: Outward motion of an opacity layer, below escape velocity | **supported**
- H: Can a smooth free-free atmosphere explain size-frequency relations? | E: Parameterised models vs observations | R: Shallow slopes need an opacity layer for all but W Hya | F: Enhanced-opacity layer needed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Mira A extended emission from dust judged unlikely  
  > "At the moment we cannot rule out any of the possible origins with certainty, although dust emission appears unlikely." (5.4 Extended emission surrounding Mira A)
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute flux calibration is the main temperature uncertainty; non-simultaneous observations  
  > "The main source of uncertainty on the temperature determination has been shown to be the absolute flux calibration accuracy of ALMA." (7 Conclusions)
- Caveat (inferred, ours): Atmosphere models are hand-tuned with degenerate parameters and no formal fit or uncertainties
- Caveat (inferred, ours): Stellar radii R_* are adopted from varied literature and affect the interpretation
- Caveat (inferred, ours): R Leo distance relies on a poor-quality Gaia solution, so the velocity scales with it
- Caveat (inferred, ours): Epochs for other stars treated as simultaneous though variability is days to weeks

## Reproducibility

- Data public (paper): Archive data with listed project codes; R Leo data retrieved from archive  
  > "we retrieved archive data of R Leo taken between our observations as part of project 2017.1.00862.S (PI: Kaminski)." (3 Observations and data reduction)
- Products in archive: _not stated_
- Missing: uvmultifit configuration
- Missing: self-calibration parameters
- Missing: model parameter-selection procedure
- Data volume (inferred): Several hundred GB to ~1 TB raw across ~15 long-baseline datasets
- Score (inferred): 5/5, Public data and clear uv-fit approach, but calibration details and model-tuning procedure are loosely specified.
- Rediscovery candidate: yes, Public data, uv-disc fits give numeric sizes, fluxes and T_b in Table 2 that can be re-derived, though the model step is less specified.

## Links

- Method: (cite: MartiVidal14) (uvmultifit uv-fitting code)
- Method: (cite: RM97) (radio-photosphere model basis)
- Companion: (cite: Vlemmings17) (previous ALMA W Hya observation and method)
- Companion: (cite: Vlemmings18) (line results from same data)
- Companion: (cite: Khouri19) (line results from same data)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 49,
  "rate": 0.583
 },
 "evidence_ok": true
}
```
