# Space reconstruction of the morphology and kinematics of axisymmetric radio sources

`2016MNRAS.461.4276D` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Diep, P. N. | arXiv: 1603.02405 | DOI: 10.1093/mnras/stw1630

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: evolved_stars, star_formation
- Question: How can the morphology and kinematics of axisymmetric circumstellar envelopes be reconstructed in space from radio data cubes, telling expansion from rotation and finding the star axis orientation?  
  > "Reconstructing in space the morphology and kinematics of radio sources is an underdetermined problem that requires imposing additional constraints for its solution." (abstract)
- Target **RS Cnc**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **EP Aqr**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Red Rectangle**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **L1527 IRS**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Mira Ceti**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00223.S, 2012.1.00524.S, 2013.1.00047.S, 2012.1.00647.S
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
- Line: C18O 2-1 (not stated)
- Other facility **IRAM Plateau de Bure Interferometer**: CO(1-0) data of RS Cnc  
  > "in particular from observations of CO(1-0) emission using the Plateau de Bure Interferometer" (3.1 A typical AGB star: RS Cnc)
- Simulation/model as data: Simulated P-V diagrams for star axis inclinations 15-90 deg, pure expansion/rotation/mixed, velocity cases A and B, emissivity r^-2  
  > "The effective emissivity is taken isotropic with dependence in $r^{-2}$ on the distance $r$ from the star." (2.3 Velocity spectra and P-V diagrams)

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

- Model used to fit RS Cnc rotation  
  > "we use the model described in (cite: Hoai2014) and (cite: Nhung2015a)." (3.1 A typical AGB star: RS Cnc) [from (cite: Hoai2014); (cite: Nhung2015a)]
- Detailed analysis of Red Rectangle ALMA data  
  > "We refer the reader to (cite: TuanAnh2015) for details and limit our comments to a brief summary of the main results." (3.3 The Red Rectangle) [from (cite: TuanAnh2015)]
- Detailed analysis of L1527 data  
  > "We refer the reader to a detailed analysis by (cite: TuanAnh2016)." (3.4 Protostar L1527 IRS) [from (cite: TuanAnh2016)]

### Not stated but needed to reproduce (our reading)

- Data reduction and imaging details for all ALMA datasets
- Which project code corresponds to EP Aqr, Red Rectangle and Mira
- Distances to targets
- Fitting code and error treatment
- Line-free channels, beam and rms

## Analysis recipe

1. **Fit RS Cnc radial dependence**: Power-law fit of R-weighted flux vs R, giving emissivity index  
  > "The $R$-dependence is well described by a power law of the form $R^{-0.63}$ implying a $r$-dependence of the effective emissivity of the approximate form $r^{-1.6}$." (3.1 A typical AGB star: RS Cnc)
   - fitting: _not stated_
   - validation: _not stated_
2. **Deproject EP Aqr emissivity and radial velocity**: Solve the Abel-type integral equation per position-angle bin assuming power-law emissivity, then derive V_rad from flux per velocity bin  
  > "Assuming in each $\varphi$ bin a form ($r$ measured in arcseconds)." (3.2 The theta=0 case: EP Aquarii)
   - assumption: Radial wind, CO dissociated at 13 arcsec  
  > "As rotation cannot be detected, we assume a radial wind of velocity $V_{rad}$." (3.2 The theta=0 case: EP Aquarii)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| RS Cnc flux R-dependence index | -0.63 | not stated | dimensionless | 1 | The $R$-dependence is well described by a power law of the form $R^{-0.63}$ |
| RS Cnc best-fit equatorial rotation velocity at r=1" | 0.4 | not stated | km/s | 0 | we obtain a best fit for $V_{rot}=0.4$ km s$^{-1}$, $\sigma_{rot} =0.3''$ and $n_{rot}=-1.0$. |
| EP Aqr R-dependence indices CO(2-1), CO(1-0) | -1.2, -0.9 | not stated | dimensionless | 2 | with respective power indices $-1.2$ and $-0.9$ |

## Qualitative findings

- EP Aqr results favour a bipolar outflow with V_rad depending on latitude rather than radius  
  > "Evidence has been given in favour of the latter." (Summary and conclusion)

## Claim tuples

- H: Does RS Cnc show rotation and a stationary wind? | E: Fit with rotation component and compare stationary vs non-stationary fits | R: Rotation up to ~1 km/s allowed; chi2 only 12% larger for non-stationary fit | F: Data cannot establish rotation or stationarity | **partially**
- H: Can EP Aqr models be unified? | E: Deprojection of CO emission | R: Strong polar enhancement with weak radial dependence up to r~8" | F: Latitude-dependent outflow preferred | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination and elongation are degenerate; psi hard to find when rotation and expansion mix  
  > "this implies strong correlations relating the inclination angle to the elongation of the outflow on the star axis" (2.5 Inclination theta)
- Caveat (inferred, ours): Methods demonstrated qualitatively without ALMA reduction details
- Caveat (inferred, ours): Uncertainties largely subjective

## Reproducibility

- Data public (paper): ALMA data public after one year  
  > "who are making their data available to the public after a one year period of exclusive property" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reduction and imaging details
- Missing: Analysis code
- Missing: Mapping of data to targets
- Data volume (inferred): tens of GB across four projects
- Score (inferred): 2/5, Method paper; applications are brief and defer details to other papers.
- Rediscovery candidate: no, Recipe incomplete and results mostly qualitative.

## Links

- Method: (cite: Hoai2014); (cite: Nhung2015a) (Model used for RS Cnc fit)
- Companion: (cite: TuanAnh2015) (Red Rectangle ALMA analysis)
- Companion: (cite: TuanAnh2016) (L1527 detailed analysis)
- Companion: (cite: Nhung2015b) (EP Aqr bipolar model)

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 12,
  "rate": 0.174
 },
 "evidence_ok": true
}
```
