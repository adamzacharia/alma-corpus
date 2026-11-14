# Probing the gas fuelling and outflows in nearby AGN with ALMA

`2017FrASS...4...58A` | Frontiers in Astronomy and Space Sciences 2017 | first author: Audibert, Anelise | arXiv: - | DOI: 10.3389/fspas.2017.00058

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Do the molecular gas kinematics and morphology in the central kpc of nearby AGN (NGC 7213, NGC 1808) show signs of inflows or outflows?  
  > "Out goal is to probe these phenomena through the kinematic and morphology of the gas inside the central kpc in nearby AGN." (abstract)
- Target **NGC 7213**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC 1808**: coordinates _not stated_; z/distance 9.1 Mpc  
  > "NGC 1808 is a Starburst/Seyfert 2 galaxy located at 9.1 Mpc and it is classified as a SAB(s)a." (3.2. NGC 1808); "Accordingly to Reif et al. (1982), it has an inclination of 57 [◦] ." (3.2. NGC 1808); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00474.S, 2015.1.00404.S
- bands: Band 7 (NGC 1808); NGC 7213 Cycle 1 CO(2-1) at 229.2 GHz  
  > "We report ALMA Cycle 1 observations of CO(2-1) at 229.2 GHz" (3.1. NGC 7213)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.27'' for NGC 1808 (Cycle 3, Band 7)  
  > "in band 7 with a resolution of 0.27 [′′] ." (3.2. NGC 1808)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 2-1 (229.2 GHz)
- Line: CO, CS, HCN, HCO+ CO(3-2), CS(7-6), HCN(4-3), HCO+(4-3) (not stated)
- Other facility **HST**: F606W and WFC/F658N images for comparison with CO maps  
  > "a WFC/F658N HST image followed by the 26 [′′] diameter imaged area of CO(3-2) observations" (Figure 3 caption)
- External data: NGC 1808 inclination of 57 deg  
  > "Accordingly to Reif et al. (1982), it has an inclination of 57 [◦] ." (3.2. NGC 1808) [from Reif et al. (1982)]

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

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (CASA version, weighting, beam, rms, channel width)
- Moment map clipping and masking procedure
- Fitting procedure and best-fit Bertola parameters (A, c, p) for each galaxy
- Inclination and centre used for NGC 7213
- Observing configurations and dates

## Analysis recipe

1. **Fit rotation model to velocity field and inspect residuals**: Fit a 2-D Bertola et al. (1991) rotation-curve model to the CO velocity map and subtract it to look for blue/redshifted residual patterns  
  > "we can compare the CO rotation curve with a rotational velocity model based on the Hα kinematics and then subtract the model to analyse the velocity residuals" (2. Methodology)
   - parameter: 1 ≤ p ≤ 3/2  
  > "therefore we expect 1 ≤ p ≤ 3/2" (2. Methodology)
   - assumption: Gas on circular orbits in a plane  
  > "assuming the gas is on circular orbits in a plane" (2. Methodology)
   - fitting: Model minimizing residuals; algorithm not stated  
  > "to generate a 2-D velocity model that minimizes the residuals" (3.1. NGC 7213)
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NGC 7213 best-fit position angle | -18 | not stated | deg | 1 | we find that the position angle is −18 [◦] and the systemic velocity |
| NGC 7213 systemic velocity correction | 30 | not stated | km/s | 1 | the systemic velocity should be corrected in 30 km/s |

## Qualitative findings

- No significant residuals in NGC 7213, so probably no molecular outflow  
  > "this result indicates that probably there is no molecular outflow in NGC 7213." (3.1. NGC 7213)
- NGC 1808 CO(3-2) kinematics show no strong outflows at this scale  
  > "do not show strong outflows at this scale." (3.2. NGC 1808)

## Claim tuples

- H: Is there a molecular outflow in NGC 7213? | E: Bertola model subtracted from CO(2-1) velocity field | R: No significant blue/red residuals | F: Probably no molecular outflow | **supported**
- H: Is there an outflow in the NGC 1808 nucleus in CO(3-2)? | E: Bertola model subtraction on first moment map | R: No significant residual patterns | F: Outflow, if present, is hard to disentangle from circular motion in moment 1; PV diagrams needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow in NGC 1808 may only be seen in position-velocity diagrams; moment-1 analysis insufficient  
  > "We need to explore in details the position-velocity diagrams along the dust lanes observed in the HST images." (3.2. NGC 1808)
- Caveat (inferred, ours): Perspective piece with no data reduction details or uncertainties
- Caveat (inferred, ours): Moment-1 residual analysis is insensitive to outflows
- Caveat (inferred, ours): Qualitative conclusions without quantitative limits

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: All calibration and imaging parameters
- Missing: Fit parameters and uncertainties
- Missing: Software names
- Data volume (inferred): ~50-200 GB for two ALMA projects
- Score (inferred): 2/5, Short perspective article with minimal methodological detail; data codes given but recipe incomplete.
- Rediscovery candidate: no, Recipe incomplete and results mostly qualitative.

## Links

- Method: Bertola et al. (1991) (Rotation curve model used for velocity field fits)
- Companion: Audibert et al., in preparation (Further analysis of molecular gas and outflow in NGC 1808)
- Companion: Salak et al. (2016) (Earlier CO(1-0) outflow evidence in NGC 1808)
- Related: NUGA (NUclei of GAlaxies)

## Checks

```json
{
 "quotes": 23,
 "quotes_ok": 23,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 56,
  "stated": 13,
  "rate": 0.232
 },
 "evidence_ok": true
}
```
