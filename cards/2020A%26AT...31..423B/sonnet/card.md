# Interpretation of ALMA velocity map for the obscuring torus in NGC1068

`2020A&AT...31..423B` | Astronomical and Astrophysical Transactions 2020 | first author: Bannikova, E. Yu. | arXiv: 2001.00421 | DOI: 10.48550/arXiv.2001.00421

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: agn_and_quasars
- Question: Can an N-body dynamical model of a self-gravitating clumpy torus reproduce the ALMA velocity map of the NGC1068 torus and give the SMBH mass?  
  > "The self-gravity of the torus induces the velocity distribution of clouds with a global orbital motion which mimics the ALMA data for NGC1068." (abstract)
- Target **NGC1068**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00052.S
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
- Line: HCN and HCO+ not stated (not stated)
- External data: ALMA mean velocity map of the NGC1068 torus (observed, compared to model)  
  > "The mean velocity distribution of the ALMA data (Fig.[3](#fig:vel_map); left) clearly shows the global rotation of the matter" (Dynamics of the clouds in the torus and interpretation of ALMA results) [from Imanishi et al. 2018; Garcia-Burillo et al. 2016]
- External data: Observed velocity 20 km/s at 3 pc, inclination 34 deg  
  > "The observational velocity is 20km/s at the distance 3pc (Imanishi et al. 2018)" (Introduction) [from Imanishi et al. 2018]
- Simulation/model as data: N-body simulation of clouds, N=8192, M_torus=0.01 M_BH, wind half-opening angle 45 deg  
  > "Here we use $N=8192$ to demonstrate the distribution of the clouds and to analyze their dynamics." (Dynamical model of a dusty torus)

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

- Dynamical torus model and its stability  
  > "Such a model was suggested in (Bannikova et al. 2012) and further developed in (Bannikova 2015, Bannikova & Sergeev 2017)." (Introduction) [from Bannikova et al. 2012; Bannikova 2015; Bannikova & Sergeev 2017]

### Not stated but needed to reproduce (our reading)

- The actual ALMA velocity map data and which moment-1 product was used
- N-body code, integrator and simulation duration
- Values of the Euler angles beyond the ~35 deg inclination
- Quantitative goodness-of-fit between model and observed map
- How the SMBH mass of 5e6 Msun was derived

## Analysis recipe

1. **Set up N-body torus**: Clouds on orbits with random orbital elements, inclinations in [0, pi/4], evolved with mutual gravity until equilibrium  
  > "It means that inclinations ($i$) of all clouds are in the range \[$0,\pi/4$\]." (Dynamical model of a dusty torus)
   - parameter: N=8192, M_torus=0.01 M_BH  
  > "demonstrate the result for $M_{torus}=0.01 M_{BH}$" (Dynamical model of a dusty torus)
   - assumption: M_BH ~ 1e7 Msun initially; M_gas ~ 1e5 Msun  
  > "with the suggestion that SMBH mass is $M_{BH} \approx 10^7 M_\odot$" (Dynamical model of a dusty torus)
   - fitting: _not stated_
   - validation: Gaussian cross-section distribution compared with IR SED requirement  
  > "This distribution obeys the Gaussian law and satisfies the obscuration condition" (Dynamical model of a dusty torus)
2. **Build model velocity maps**: Rotate torus by two Euler angles, 30x30 cells, mean velocity of first 10 clouds along line of sight per cell  
  > "Find the mean velocity of the clouds which are located in the cylinder along the line of sight with the cross-section corresponding to the cell but taking into account only the first 10 clouds" (Dynamics of the clouds in the torus and interpretation of ALMA results)
   - fitting: _not stated_
   - validation: Visual comparison with ALMA map  
  > "Fig.[3](#fig:vel_map) *middle* demonstrates good agreement with the observations" (Dynamics of the clouds in the torus and interpretation of ALMA results)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMBH mass in NGC1068 from model | 5e6 | not stated | Msun | 2 | The SMBH mass in NGC1068 is about $5 \times 10^6 M_\odot$. |
| Best-match torus inclination from edge-on | 35 | not stated | deg | 2 | The best match of the model velocity map with the observed one occurs for an inclination of the torus of $35^\circ$ from edge-on position. |

## Qualitative findings

- Self-gravity with eccentric orbits explains low ALMA velocities with a higher SMBH mass than Keplerian estimate  
  > "Such low velocity for more high value of the SMBH mass is related to the fact that clouds move in eccentric orbits due to self-gravity of the torus" (Dynamics of the clouds in the torus and interpretation of ALMA results)

## Claim tuples

- H: A self-gravitating clumpy torus model reproduces the ALMA velocity map of NGC1068 | E: N-body simulation projected into 30x30 velocity maps at various orientations | R: Orientation about 35 deg from edge-on matches the observed map | F: Orientation effects and clumpy structure explain the map | **supported**
- H: The SMBH mass is reconciled between megamaser and ALMA estimates | E: Compare model velocity at 3 pc with 20 km/s | R: M_BH about 5e6 Msun | F: Keplerian estimate of 9e5 Msun is too low | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Keplerian disk interpretation gives SMBH mass inconsistent with megamaser value  
  > "which may suggest that the approach of a Keplerian disk does not work" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Work in progress  
  > "Here we present the work in progress using the dynamical model of the torus for an explanation of the ALMA observations" (Introduction)
- Caveat (inferred, ours): Comparison with the ALMA map is qualitative only
- Caveat (inferred, ours): No uncertainty on mass or inclination
- Caveat (inferred, ours): Only 8192 clouds, with mass scaling argued rather than tested
- Caveat (inferred, ours): Degeneracy between orientation and M_BH not explored

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: N-body code and integration details
- Missing: Initial orbital element distributions
- Missing: ALMA velocity map product
- Missing: Fit procedure
- Data volume (inferred): small; ALMA map is a moment product, from a few GB
- Score (inferred): 2/5, Qualitative comparison, code and model details missing.
- Rediscovery candidate: no, Recipe is incomplete and the main results are not quantitatively defined.

## Links

- Method: Bannikova et al. 2012, MNRAS 424, 820 (Original dynamical torus model)
- Companion: Imanishi et al. 2018, ApJL 853, L25 (Source of the ALMA velocity map)

## Checks

```json
{
 "quotes": 21,
 "quotes_ok": 21,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 58,
  "stated": 14,
  "rate": 0.241
 },
 "evidence_ok": true
}
```
