# exoALMA. XXIV. Formaldehyde Emission in Protoplanetary Disks of exoALMA Compared with Their Properties and Dynamical State

`2026ApJ..1000L..32A` | The Astrophysical Journal Letters 2026 | first author: Alarcón, Felipe | arXiv: 2603.13081 | DOI: 10.3847/2041-8213/ae4de0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Do H2CO excitation conditions and emission asymmetry correlate with stellar/disk properties and with the dust continuum non-axisymmetric index (dynamical state) in exoALMA disks?  
  > "search for correlations of the observed emission with stellar and disk properties; (2) shed light on the origin of gas-phase H$_2$CO" (Introduction)
- Target **AA Tau, CQ Tau, HD 34282, HD 135344B, HD 143006, MWC 758, PDS 66, RX J1615, RX J1842, RX J1852, Elias 2-27**: coordinates _not stated_; z/distance 98-309 pc (e.g. AA Tau 135 pc, HD 34282 309 pc, PDS 66 98 pc)  
  > "| AA Tau | 273 | -59 | 135 | 6.50 | 0.79 |" (Table 1 (disk properties)); distance from not stated (table references only)  
  > "| AA Tau | 273 | -59 | 135 | 6.50 | 0.79 |" (Table 1 (disk properties))

## Data provenance

- ALMA projects: 2022.1.00485.S, 2023.1.00334.S, 2016.1.00484.L, 2021.1.01123.L, 2022.1.00875.L
- bands: _not stated_
- frequencies and spectral setup: four H2CO 4-3 transitions (290.62-291.38 GHz) in a single spectral window  
  > "in a single spectral window (see Table [1](#Table: Lines))" (2.1 Sample and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.3''-0.4'' (natural weighting)  
  > "a spatial resolution ranging between 0.3$''$ and 0.4$''$" (2.1 Sample and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI: L. Trapman programs  
  > "programs (PI: L. Trapman)" (2.1 Sample and Data Reduction)
- Line: H2CO 4(0,4)-3(0,3) (290.623405 GHz)
- Line: H2CO 4(2,3)-3(2,2) (291.237766 GHz)
- Line: H2CO 4(3,2)-3(3,1) and 4(3,1)-3(3,0) (blended) (291.380442 / 291.384362 GHz)
- External data: Continuum NAI values for the exoALMA disks  
  > "the NAI values from the continuum data reported in (cite: exoALMAIV_Curone)" (3.2 NAI) [from (cite: exoALMAIV_Curone)]
- External data: Spectroscopic constants and partition function from CDMS  
  > "obtained from the Cologne Database for Molecular Spectroscopy (cite: CDMS)" (Table 1 caption) [from (cite: CDMS)]
- External data: Elias 2-27 continuum data from DSHARP  
  > "The analyzed data are from the DSHARP Large Program (cite: DSHARP; DSHARP..X)." (NAI of Elias 2-27) [from (cite: DSHARP; DSHARP..X)]

## Processing

### Calibration

- pipeline or manual: same calibration as Trapman et al.  
  > "The calibration of the dataset is the same as that performed by (cite: ExoALMAXIII_Trapman)." (2.1 Sample and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA, natural weighting  
  > "We imaged the cubes using the CASA software (cite: CASA) with *natural* weighting to maximize the signal-to-noise ratio (SNR) for the H$_2$CO emission" (2.1 Sample and Data Reduction)
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
- smoothing: native spectral resolution ~1.2 km/s  
  > "native spectral resolution of $\sim$ 1.2 km s$^{-1}$" (2.1 Sample and Data Reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration of the dataset  
  > "The calibration of the dataset is the same as that performed by (cite: ExoALMAXIII_Trapman)." (2.1 Sample and Data Reduction) [from (cite: ExoALMAXIII_Trapman)]
- Bootstrap flux uncertainty and MCMC fitting method  
  > "We recover the physical parameters and their respective uncertainties by employing a Markov Chain Monte Carlo (MCMC) fitting as described in (cite: Luna..24) using the `emcee` package (cite: emcee)." (Flux extraction and retrieval of physical parameters) [from (cite: Luna..24)]
- Continuum NAI procedure for Elias 2-27  
  > "applied the same procedure as outlined by (cite: exoALMAIV_Curone) to retrieve the NAI from the continuum observations" (NAI of Elias 2-27) [from (cite: exoALMAIV_Curone)]

### Not stated but needed to reproduce (our reading)

- Imaging details (tclean parameters, cell/image size, masks, continuum subtraction, line-free channels)
- CASA version and calibration specifics
- Whether primary-beam correction was applied to fluxes
- Sigma (rms) definition used for the 3σ/4σ thresholds
- Aperture geometry parameters (centre, PA, inclination adopted)
- Origin of the stellar/disk parameters (only reference numbers given)
- Handling of upper limits in rotation diagrams and correlations

## Analysis recipe

1. **Image cubes and make moment maps**: Natural-weighted CASA cubes; moment 0 integrated over 3.6-6 km/s (3-5 channels) chosen from >3σ emission of brightest line; moment 8 peak maps  
  > "integrating the data cubes over spectral ranges varying between 3.6 and 6 km s$^{-1}$ (three to five spectral channels)" (2.2 Flux extraction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract line fluxes and uncertainties**: Fluxes in whole disk, inner 0-100 au and 100-200 au elliptical apertures; blended 4(3,2) and 4(3,1) lines averaged; errors by bootstrap in >=15 emission-free apertures  
  > "we extract the flux in multiple nonoverlapping elliptical apertures ($\geq$15) in emission-free regions of the integrated intensity maps" (2.2 Flux extraction)
   - fitting: _not stated_
   - validation: Bootstrapped errors conservative given correlated noise  
  > "it ends up overestimating the uncertainties of our measurements given the spatial correlation of the noise" (2.2 Flux extraction)
3. **Rotation diagram retrieval of Texc and N**: LTE, optically thin rotation diagram with partition function interpolated from CDMS  
  > "we employ rotation diagrams to recover the physical conditions of the formaldehyde gas (cite: Goldsmith..Langer..1999), where we assume local thermodynamic equilibrium" (2.2 Flux extraction)
   - software: emcee
   - parameter: 256 walkers, 5000 steps after 1000 burn-in  
  > "256 walkers, and 5000 steps after a burn-in of 1000 steps" (2.2 Flux extraction)
   - assumption: OPR = 3  
  > "the combined partition function intrinsically assumes a gas-phase ortho-to-para ratio (OPR) scaling of 3.0" (2.2 Flux extraction)
   - fitting: MCMC; uniform prior on Texc 10-200 K, log-uniform prior on N 1e10-1e14 cm-2  
  > "We apply a uniform prior for the excitation temperature ranging between 10 and 200 K" (2.2 Flux extraction)
   - validation: Optical depth check, max tau <= 0.15  
  > "the maximum optical depth measured is $\leq$0.15" (3 Results)
4. **Compute H2CO asymmetry index**: NAI_H2CO from peak-intensity map of 4(0,4)-3(0,3) folded about the minor axis within 200 au, 4σ threshold on pixel pairs  
  > "we calculate the molecular non-axisymmetric index on the intensity peak maps after folding them against the minor axis of the disk" (2.4 Calculation of the NAI)
   - parameter: 4σ threshold  
  > "We employ a 4$\sigma$ threshold on pixel pairs from the opposite sides of the disk" (2.4 Calculation of the NAI)
   - fitting: _not stated_
   - validation: Tested on CO cubes of PDS 66; compared point and axial metrics vs thresholds  
  > "This choice was also tested over the CO line emission cubes of PDS 66 using the exoALMA data" (2.4 Calculation of the NAI)
5. **Correlation analysis**: Weighted Kendall-tau between H2CO properties, NAIs and stellar/disk parameters; z-scores for significance  
  > "We opted to use the nonparametric Kendall-$\tau$ correlation given the size of our disk sample" (2.3 Correlation Analysis)
   - software: statsmodels, scikit-learn
   - parameter: weights w_i = (1+(sigma_i/X_i))^-1  
  > "$w_i = (1 + (\sigma_i/X_i))^{-1}$" (2.3 Correlation Analysis)
   - fitting: _not stated_
   - validation: 2σ significance threshold on z-scores  
  > "The correlation values exceeding the 2$\sigma$ level of significance are highlighted in white in the $z$-score matrix." (3.1)

## Software

- **CASA** : imaging cubes  
  > "We imaged the cubes using the CASA software (cite: CASA)" (2.1 Sample and Data Reduction)
- **emcee** : MCMC fit of rotation diagrams  
  > "using the `emcee` package (cite: emcee)" (2.2 Flux extraction)
- **frank** : Elias 2-27 continuum radial profile for NAI  
  > "the radial profile extracted with the `frank` fit (cite: Jennings..2020)" (NAI of Elias 2-27)
- **statsmodels** : listed in software section  
  > "`statsmodels` (cite: statsmodels)" (Software)
- **scikit-learn** : listed in software section  
  > "`scikit-learn` (cite: scikit-learn)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2CO Texc inner 100 au, CQ Tau | 99.1 | +13.3/-10.7 | K | 3 | 99.1^{+13.3}_{-10.7} & 13.83^{+0.04}_{-0.04} |
| H2CO Texc outer, Elias 2-27 | 16.7 | +3.1/-3.9 | K | 3 | 16.7^{+3.1}_{-3.9} |
| Kendall tau Teff vs Texc,in | 0.5 (2.1σ) | not stated | dimensionless | 5 | showing a Kendall-$\tau$ value 0.5 |
| Mean NAI_H2CO vs continuum NAI | 0.39 vs 0.15 | std 0.14 vs 0.15 | dimensionless | 4 | average value of 0.39, which is significantly higher than the NAI continuum average, which is 0.15 |
| Max optical depth | <=0.15 | not stated | dimensionless | 3 | the maximum optical depth measured is $\leq$0.15 |

## Qualitative findings

- Column density drops by a factor of almost three from inner 100 au to 100-200 au; Texc differences insignificant  
  > "the column densities decrease by a factor of almost three" (4.1)

## Claim tuples

- H: H2CO excitation correlates with stellar/disk properties | E: Weighted Kendall-tau on 11 disks | R: No correlation reaches significance; tentative Teff-Texc,in at 2.1σ | F: Central star likely dominates H2CO excitation; needs larger samples | **partially**
- H: H2CO asymmetry traces dust-traced dynamical state | E: Compare NAI_H2CO with continuum NAI | R: No clear correlation | F: No clear link between dynamics and chemistry in this subsample | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting trades resolution for SNR; 100 au bins chosen to be at least one beam for the most distant target  
  > "it secures us at least one spatial beam for the most distant target" (2.1)
- Alternative: Point-symmetry and major-axis reflection NAI rejected as affected by elevated emission and ray-tracing  
  > "this metric is severely affected by the elevated surface of the gas emission" (Appendix: Asymmetry Metrics)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample; single-component fit; OPR fixed at 3  
  > "In our fit, we assume a single-component formaldehyde reservoir" (4.1)
- Caveat (inferred, ours): Only 11 disks; 2.1σ is not significant, and many tests are made without trial correction
- Caveat (inferred, ours): Upper limits and low-SNR high-Eu points constrain Texc weakly
- Caveat (inferred, ours): Fixed OPR=3 and LTE/optically thin assumption bias Texc
- Caveat (inferred, ours): NAI_H2CO depends on sensitivity and flux normalisation, and correlates with line flux
- Caveat (inferred, ours): Beam dilution differs among disks at fixed 100 au bins (distances 98-309 pc)

## Reproducibility

- Data public (paper): ALMA project codes cited  
  > "ADS/JAO.ALMA#2022.1.00485.S\" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration/imaging scripts and parameters
- Missing: Exact aperture geometry and stellar parameter sources
- Missing: Continuum NAI values are from another paper
- Data volume (inferred): ~50-200 GB raw for 11 disks
- Score (inferred): 3/5, Public data and a clear rotation-diagram and MCMC recipe, but imaging parameters are inherited or unstated.
- Rediscovery candidate: no, Imaging recipe incomplete and the main results are tentative correlations.

## Links

- Method: (cite: Luna..24) (bootstrap flux errors and MCMC rotation diagram method)
- Method: (cite: exoALMAIV_Curone) (continuum NAI definition)
- Companion: (cite: ExoALMAXIII_Trapman) (observations and calibration of the same dataset)
- Companion: (cite: exoALMAI_Teague) (exoALMA survey overview)
- Related: exoALMA Large Program
- Related: DSHARP
- Related: DECO (2022.1.00875.L)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2022.1.00875.L"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 39,
  "rate": 0.513
 },
 "evidence_ok": true
}
```
