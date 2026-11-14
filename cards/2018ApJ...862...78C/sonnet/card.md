# An Analysis of ALMA Deep Fields and the Perceived Dearth of High-z Galaxies

`2018ApJ...862...78C` | The Astrophysical Journal 2018 | first author: Casey, Caitlin M. | arXiv: 1806.05603 | DOI: 10.3847/1538-4357/aacd11

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: high_z_galaxies
- Question: Are the low numbers of high-z dusty galaxies in ALMA deep fields consistent with a backward-evolution IRLF model constrained by single-dish surveys, and how should future ALMA surveys be designed?  
  > "the measured number counts and redshift distributions from ALMA deep field surveys are fully consistent with constraints of the infrared luminosity function (IRLF) at $z<2.5$" (abstract)
- Target **ASPECS-Pilot, HUDF, GOODS-ALMA, SSA22, SXDF ALMA deep fields (literature)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00173.S, 2012.1.00756.S, 2013.1.00718.S, 2013.1.00162.S, 2015.1.00543.S, 2017.1.00755.S
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
- External data: Published 1.1-1.3 mm ALMA deep field number counts, source lists and redshifts (HUDF, ASPECS-Pilot, GOODS-ALMA, SSA22, SXDF)  
  > "Figure [5](#fig:nc) shows a detailed comparison of measured number counts at 1.2 mm from these literature resources against our three models." (3 Comparison to Existing 1.2 mm Datasets) [from (cite: dunlop16a; aravena16b; franco18a; umehata15a; hatsukade16a)]
- External data: 35 LBGs and ASPECS-Pilot flux limits used for dust-content analysis  
  > "present a sample of 35 Lyman Break Galaxies (LBGs) which they expected to detect in the ASPECS-Pilot map" (3.3 Analysis of UV-bright Population) [from (cite: bouwens16a)]
- External data: 12 z~5.5 UV-selected galaxies with dust continuum observations  
  > "who present 12 rest-frame UV-selected galaxies at $z\approx5.5$ with dust continuum observations" (3.3 Analysis of UV-bright Population) [from (cite: capak15a); (cite: barisic17a)]
- Simulation/model as data: Backward-evolution IRLF model of C18, with Models A, B and a new Model C  
  > "We have built a backward-evolution model to interpret the origins of emission in the submillimeter/millimeter sky from galaxy number counts, redshift distributions and correlations between bands." (2 Model Parameterization)

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

- Model setup, IRLF evolution, SED generation, parameters (Table 3 of C18)  
  > "All other parameters in the models are fixed to the values as given in Table 3 of C18." (3.1 Importance of the Faint-End Slope of the IRLF) [from (cite: casey18a)]
- SEDs transition from optically thick to thin with tau=1 at 100 micron  
  > "As in C18, and informed by the rough luminosity sensitivities of ALMA deep field surveys shown in Figure [2](#fig:lirz), we continue with the assumption" (2 Model Parameterization) [from (cite: casey18a)]

### Not stated but needed to reproduce (our reading)

- Source extraction algorithm and settings used on mock maps
- Exact mapping from flux to LIR SED families and scatter used for the LBG analysis
- Mock map sizes, random seeds, and the exact number of Monte Carlo realizations for all figures
- Model code is not released; full C18 parameter table needed
- Photometric redshift PDFs of the observed deep field sources

## Analysis recipe

1. **Build mock ALMA maps**: Inject IRLF-derived sources with SEDs into mock maps, convolve with beam, add noise, re-extract sources  
  > "Once all sources at all redshifts have been injected into these mock maps, they are convolved with the beamsize of observations specific to a certain instrument at a certain observatory" (2 Model Parameterization)
   - parameter: Pixel size 1/5 of minimum beam FWHM; Band 6 beam 0.6" and RMS 13 uJy  
  > "A mock map consists of a regularly-spaced grid with pixel size equal to 1/5 of the minimum beamsize FWHM simulated" (2 Model Parameterization)
   - assumption: Sources are unresolved point sources  
  > "Since we do not model the galaxies’ sizes directly, and instead input them as point sources" (2 Model Parameterization)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit faint-end slope to HUDF source density**: Vary alpha_LF in -1 to -0.1 for Models A and B; count >3.5 sigma sources at 35 uJy RMS; 100 Monte Carlo runs per value  
  > "we constrain the number of expected sources and its uncertainty by using 100 Monte Carlo simulations for either Model A or Model B." (3.1 Importance of the Faint-End Slope of the IRLF)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate completeness and contamination and compare number counts and redshift distributions**: Run detection on inverted maps and compare injected vs detected catalogues; compare with literature counts and redshift distributions using random subsets of n=5 or 15  
  > "we invert the maps and run our source detection algorithm on the negative image, where we know all detections will be false." (3.1 Completeness, Contamination, and Sample Cleaning)
   - fitting: _not stated_
   - validation: _not stated_
4. **Re-derive IRX for LBGs**: Generate SED family with mid-IR power law, find SEDs matching observed 1.2 mm flux, derive LIR probability density, combine with LUV to get IRX  
  > "We then search for all possible SEDs that have the observed flux density at 1.2 mm and use it to generate a probability density distribution in $L_{\rm IR}$." (3.3 Analysis of UV-bright Population)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit faint-end slope, Model A | -0.69 | +0.06/-0.07 | dimensionless | 2 | $\alpha_{\rm
  LF}=-0.69^{+0.06}_{-0.07}$ for Model A |
| Best-fit faint-end slope, Model B | -0.49 | +0.07/-0.06 | dimensionless | 2 | $\alpha_{\rm
  LF}=-0.49^{+0.07}_{-0.06}$ for Model B |
| False detection rate in inverted maps | 4.6 | 0.6 | sources per arcmin^2 | 3 | we estimate a false rate of 4.6$\pm$0.6 sources per arcmin$^2$ |
| Upper limits consistent with Calzetti law | 29/32 | not stated | count | 4 | the vast majority of these upper limits (29/32) are consistent with the Calzetti dust attenuation law |
| Expected 1.2 mm median redshift | 1.7<z<3.5 | not stated | dimensionless | 3 | the expected redshift distributions for 1.2 mm surveys of this size is between $1.7<\langle z\rangle<3.5$ |

## Qualitative findings

- 1.2 mm deep fields are unconstraining for the high-z IRLF; 2 mm wider, shallower surveys are optimal  
  > "We find 1.2 mm ALMA deep fields completely unconstraining for the high-redshift IRLF." (Conclusions)

## Claim tuples

- H: ALMA deep-field counts and redshifts are consistent with single-dish-constrained IRLF | E: Mock ALMA maps from the extended C18 model compared with literature counts | R: Good agreement in counts; redshift data cannot distinguish models | F: No dearth of high-z dusty galaxies is implied | **supported**
- H: High-z LBGs are dust-poor | E: Re-derived IRX with different SEDs and IRX-beta reference | R: Most limits consistent with Calzetti | F: No evidence for less dust | **supported**
- H: A 2 mm ALMA survey can discriminate models | E: Mock Band 4 survey | R: 20 (Model A) to 120 detections over ~230 arcmin^2 at 0.08 mJy RMS | F: 2 mm survey recommended | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Sources are modelled as point sources, and observed samples are small  
  > "The comparison is a bit unfair, given that we are limited to a handful of galaxies in each sample" (3.2 Redshift Distributions)
- Caveat (inferred, ours): Model is tuned to single-dish data and a single HUDF count; faint-end slope degenerate with cosmic variance
- Caveat (inferred, ours): Contamination estimates depend on the assumed detection algorithm

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Model code and full parameter set
- Missing: Detection algorithm details
- Data volume (inferred): none for model; literature catalogues only
- Score (inferred): 2/5, Model-based paper relying on unreleased C18 model code; ALMA data only enter via literature numbers.
- Rediscovery candidate: no, Main results require the unreleased model, not ALMA data reduction.

## Links

- Method: (cite: casey18a) (Backward-evolution model)
- Companion: (cite: dunlop16a) (HUDF ALMA deep field)
- Companion: (cite: aravena16b) (ASPECS-Pilot)
- Companion: (cite: franco18a) (GOODS-ALMA)
- Related: ASPECS
- Related: GOODS-ALMA
- Related: ALMACAL

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.00755.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 15,
  "rate": 0.231
 },
 "evidence_ok": true
}
```
