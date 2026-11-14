# Rings and Gaps in Protoplanetary Disks: Planets or Snowlines?

`2018ApJ...867L..14V` | The Astrophysical Journal Letters 2018 | first author: van der Marel, Nienke | arXiv: 1810.05614 | DOI: 10.3847/2041-8213/aae88e

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Do gaps in CO emission in the HD 163296 disk imply gas density drops from planets, or can a snowline-like grain growth model explain the dust rings without planets?  
  > "We use the physical-chemical code DALI to show that the gas temperature increases inside dust density gaps, implying that any gaps in the gas, if present, would have to be much deeper" (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 101.5±1.2 pc  
  > "The most recent parallax of HD 163296 is 9.85$\pm$0.11 mas using *Gaia* DR2, corresponding to a distance of 101.5$\pm1.2$ pc (cite: Gaia2018)." (Model); distance from Gaia DR2 parallax  
  > "The most recent parallax of HD 163296 is 9.85$\pm$0.11 mas using *Gaia* DR2, corresponding to a distance of 101.5$\pm1.2$ pc (cite: Gaia2018)." (Model)

## Data provenance

- ALMA projects: 2013.1.00601.S
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
- Line: 12CO 2-1 (not stated)
- Line: 13CO 2-1 (not stated)
- Line: C18O 2-1 (not stated)
- Other facility **Gaia DR2**: Parallax and distance of HD 163296  
  > "The most recent parallax of HD 163296 is 9.85$\pm$0.11 mas using *Gaia* DR2" (Model)
- External data: Reduced ALMA continuum and CO isotopologue images of HD 163296  
  > "We use the same data images as presented in (cite: Isella2016) for our comparison." (Model) [from (cite: Isella2016)]
- External data: Stellar parameters  
  > "Stellar parameters are taken from (cite: Mendigutia2013)." (Model) [from (cite: Mendigutia2013)]
- External data: Condensation temperatures: 23-28 K CO, 26-32 K CH4, 60-72 K CO2  
  > "based on the condensation temperatures derived in Table 2 in (cite: Zhang2015): 23-28 K for CO, 26-32 K for CH$_4$ and 60-72 K for CO$_2$ respectively." (Discussion and conclusions) [from (cite: Zhang2015)]
- External data: CO snowline at 75±6 AU from N2H+ and DCO+  
  > "we overlay the snowline as derived from N$_2$H$^+$ and DCO$^+$ observations (cite: Qi2011) in HD 163296, located at 75$\pm$6 AU." (Discussion and conclusions) [from (cite: Qi2011)]
- Simulation/model as data: DALI models: Model 0 (no gaps), A (gap), B (snowline), C (deeper gaps)  
  > "we have run Model 0 without any radial changes in the surface density or grain size distribution, and a variation of Model A with much deeper gaps (Model C)." (Model)

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

- Gap depths in dust and gas for Model A  
  > "following the dust and gas model of (cite: Isella2016)" (Model) [from (cite: Isella2016)]
- DALI parameters and assumptions  
  > "Further details on the parameters and assumptions in DALI are given in (cite: Bruderer2013)." (Model) [from (cite: Bruderer2013)]
- Dust settling parametrization  
  > "Settling is parametrized following (cite: Bruderer2013)" (Model) [from (cite: Bruderer2013)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (taken from Isella et al. 2016)
- DALI input files and full parameter set (gas-to-dust ratio, settling fraction, cosmic-ray rate)
- Exact smoothing/normalisation for the EIR
- Gap widths and depths for models with different delta_gas
- Line-ratio/flux scaling used to compare model and data (model fluxes differ strongly from data)

## Analysis recipe

1. **Build parametrized HD 163296 disk with rings**: Lynden-Bell & Pringle power-law with exponential cutoff surface density; gaps at Isella 2016 radii scaled to 101.5 pc  
  > "we assume a surface density profile $\Sigma(r)$ as a radial power-law with exponential cut-off following (cite: LyndenPringle1974)" (Model)
   - software: DALI
   - parameter: gamma = 1; gap factors for dust 0.010, 0.014, 0.17 and gas 0.4, 0.29, 0.56 (Model A)  
  > "the dust surface density is decreased by a factor 0.010, 0.014 and 0.17 for gap $r_1$, $r_2$ and $r_3$ respectively" (Model)
   - assumption: Distance 101.5 pc  
  > "corresponding to a distance of 101.5$\pm1.2$ pc (cite: Gaia2018)" (Model)
   - fitting: _not stated_
   - validation: _not stated_
2. **Run gap and snowline models**: Model A varies surface density in gaps; Model B keeps density but sets large-grain fraction f_ls=0.01 in gaps, 0.99 elsewhere  
  > "the fraction of large grains in the midplane $f_{ls}$ is set to 0.01 inside the three gaps, and otherwise $f_{ls}$=0.99" (Model)
   - software: DALI
   - parameter: 190 radial x 60 vertical cells, time-dependent chemistry up to 1 Myr  
  > "DALI was run using a grid with 190 cells in radial and 60 cells in vertical direction, using time-dependent chemistry up to 1 Myr." (Model)
   - fitting: No formal fit  
  > "We do not aim to provide a perfect fit to the observations, but use the structure to illustrate how the CO emission changes due to changes in the dust structure" (Model)
   - validation: f_ls tested over a range; 0.01 or lower needed to reproduce ring contrast  
  > "a value of 0.01 or lower is required to reproduce the dust continuum contrast seen in the rings of the observations" (Model)
3. **Compare model with data using enhanced image representation**: Ratio of image to smoothed version (FWHM twice the beam), normalized; azimuthally averaged cuts  
  > "for each image we compute the ratio between the original and a smoothed version (smoothing FWHM is twice the beam size of the observations) and normalize the result." (Model)
   - fitting: _not stated_
   - validation: _not stated_
4. **Explore gas gap depth and midplane snowline temperatures**: Run models with delta_gas from 1 to 1e-2; compare Model B midplane temperature with condensation temperatures  
  > "The values of $\delta_{\rm gas}$ range between 1 and 10$^{-2}$." (Discussion and conclusions)
   - software: DALI
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DALI** : Physical-chemical modeling of gas temperature, CO abundance and emission  
  > "We use the physical-chemical code DALI to show that the gas temperature increases inside dust density gaps" (abstract)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gaia DR2 distance of HD 163296 | 101.5 | ±1.2 | pc | 1 | corresponding to a distance of 101.5$\pm1.2$ pc (cite: Gaia2018) |
| Minimum planet mass implied by gaps | >=1 | not stated | M_Jup | 4 | our models suggest that the gaps, if caused by planets, must contain planets which are at least a Jupiter mass. |
| Total 12CO 2-1 flux, data | 41.05 | not stated | Jy km/s | 0 | $^{12}$CO 2–1 / 41.05 |

## Qualitative findings

- Gas temperature and CO abundance rise inside dust gaps, so CO emission can brighten despite lower gas density  
  > "Remarkably, even though the gas surface density has been *decreased* inside the dust gaps, the CO emission (in particular the C$^{18}$O) is *brighter*." (Model)
- Snowline model reproduces dust rings with no change in CO emission  
  > "The snow model can thus reproduce dust rings without changing the CO emission itself." (Model)

## Claim tuples

- H: Gas gaps in CO imply Saturn-mass planets | E: DALI gap model with Isella 2016 depths compared with CO images | R: Model predicts brighter CO in gaps, unlike the data | F: Gas gaps must be deeper, planets at least Jupiter mass | **supported**
- H: Grain growth at snowlines can produce the rings without planets | E: Model B with varied large-grain fraction | R: Reproduces dust ring morphology without CO changes | F: Snowline scenario remains possible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Models not fitted precisely; inner region affected by continuum oversubtraction; combined hydro and chemistry not feasible  
  > "We do not aim to provide a perfect fit to the observations" (Model)
- Caveat (inferred, ours): Model fluxes differ substantially from observed fluxes
- Caveat (inferred, ours): Model A and B compared qualitatively only
- Caveat (inferred, ours): Snowline gap locations opposite to Model B assumption
- Caveat (inferred, ours): Single object and only dust-ring structure from prior reduction

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: DALI input files
- Missing: Reduced Isella et al. cubes (provided privately)
- Missing: Full chemistry settings
- Data volume (inferred): ~10-50 GB if reprocessing archival ALMA data; models need DALI
- Score (inferred): 2/5, Modeling-based, qualitative, DALI inputs and data reduction not given.
- Rediscovery candidate: no, Main results are qualitative model comparisons, not derived from a stated reduction recipe.

## Links

- Method: (cite: Bruderer2013) (DALI code details)
- Method: (cite: Isella2016) (Source of ALMA data and gap model)
- Companion: (cite: Facchini2017gaps) (Gas temperature in planet-carved gaps using DALI)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 25,
  "rate": 0.352
 },
 "evidence_ok": true
}
```
