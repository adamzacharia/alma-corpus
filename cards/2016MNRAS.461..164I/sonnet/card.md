# On the origin of the flux ratio anomaly in quadruple lens systems

`2016MNRAS.461..164I` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Inoue, Kaiki Taro | arXiv: 1601.04414 | DOI: 10.1093/mnras/stw1270

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: cosmology, high_z_galaxies
- Question: Whether flux ratio anomalies in 11 quadruple lens systems are caused mainly by subhaloes or by line-of-sight structures  
  > "We explore the origin of flux ratio anomaly in quadruple lens systems." (abstract)
- Target **SDP.81**: coordinates _not stated_; z/distance z_S = 3.042, z_L = 0.2999  
  > "| SDP.81 | 3.042 | 0.2999 | submm | submm | $4$ | $1.6$ | $0.50$ |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: Band 7 continuum  
  > "we use the processed archival image of the band 7 continuum taken from the ALMA Science Portal" (4 Quadruple lens systems)
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
- Other facility **CASTLES and optical/NIR/radio/MIR literature data**: Astrometry, radio and MIR fluxes for the other 10 lens systems  
  > "For the astrometry of lensed images and the centroids of lensing galaxies, we use optical or NIR data except for SDP.81" (4 Quadruple lens systems)
- External data: Processed ALMA Band 7 continuum image of SDP.81  
  > "see (cite: vlahakis2015) for detail" (4 Quadruple lens systems) [from (cite: vlahakis2015)]
- External data: Best-fit lens model parameters  
  > "The best-fitted model parameters are in (cite: inoue-takahashi2012; takahashi-inoue2014)." (5 Lens model) [from (cite: inoue-takahashi2012; takahashi-inoue2014)]
- Simulation/model as data: N-body based non-linear power spectra (particle mass ~1e5 h^-1 Msun) and semi-analytic subhalo mass function from Han et al. 2015  
  > "we first calculate the non-linear power spectra of matter fluctuations down to mass scales of $\sim 10^5\, h^{-1 } M_{\odot}$ using $N$-body simulations" (3 Line-of-sight lensing)

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

- Line-of-sight perturbation formalism and lens models  
  > "using semi-analytic formulae developed in (cite: inoue-takahashi2012; takahashi-inoue2014)" (3 Line-of-sight lensing) [from (cite: inoue-takahashi2012; takahashi-inoue2014)]
- SDP.81 flux ratio anomaly analysis  
  > "For detail of these 11 lens systems, see (cite: takahashi-inoue2014; inoue-etal2015; inoue-minezaki2015)." (4 Quadruple lens systems) [from (cite: inoue-minezaki2015)]

### Not stated but needed to reproduce (our reading)

- Fitted lens model parameters for each system (only referenced)
- Observational errors on flux ratios and eps_0 per system
- Host halo concentration and mass mapping details
- Data points for the redshift correlation fits

## Analysis recipe

1. **Fit smooth lens models**: Fit SIE plus external shear to fluxes, positions and time delays by chi^2  
  > "simultaneous $\chi^2$ fitting of the fluxes, positions, and time delay of lensed images" (5 Lens model)
   - software: GRAVLENS
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute expected perturbation from subhaloes and line-of-sight structure**: Semi-analytic subhalo mass function in NFW host plus N-body power spectra with constant-shift cut, constrained by astrometric shifts  
  > "we use a statistic $\eta$ defined as" (6 Method)
   - assumption: Statistical isotropy, |dgamma| ~ |dkappa|  
  > "we assume statistical isotropy for the perturbation. Then we have $|\delta \gamma| \sim |\delta \kappa|$" (6 Method)
   - fitting: _not stated_
   - validation: _not stated_
3. **Linear fit of convergence perturbation vs redshift**: Fit |dkappa| = alpha + beta z and test beta=0  
  > "we fit the data with a linear function $|\delta \kappa|=\alpha + \beta z_{\textrm{L}} (z_{\textrm{S}})$" (7 Result)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GRAVLENS** : Lens model chi^2 fitting  
  > "we use a numerical code GRAVLENS developed by Keeton" (5 Lens model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean subhalo convergence perturbation | 0.003 | not stated | dimensionless | 2 | $\langle \delta \kappa_{\textrm{sub}} \rangle  = 0.003$ |
| mean line-of-sight convergence perturbation | 0.008 | not stated | dimensionless | 2 | $\langle /\delta \kappa_{\textrm{los}}/ \rangle = 0.008$ |
| mean observed convergence perturbation | 0.009 | not stated | dimensionless | 2 | for the observed values is $\langle /\delta \kappa _{\textrm{obs}}/ \rangle =0.009$ |
| mean subhalo mass fraction f_sub | 0.006 | not stated | dimensionless | 2 | $\langle f_{\textrm{sub}} \rangle  = 0.006$ |
| beta for z_L>0.6 (with error) | 0.0046 | 0.0009 | dimensionless | 3 | / $z_{\textrm{L}}>0.6$ (with error) / $-0.0007\pm 0.0017$ / $0.72$ / $0.0046 \pm 0.0009$ / $0.014$ / |

## Qualitative findings

- Convergence perturbation correlates with source redshift more strongly than with lens redshift, favouring line-of-sight structures  
  > "This feature also supports an idea that the flux ratio anomaly is caused mainly by line-of-sight structures rather than subhaloes." (abstract)

## Claim tuples

- H: Subhaloes alone explain observed flux ratio anomalies | E: Compare expected eta and delta kappa from subhaloes and LOS structures with observed values for 11 lenses | R: Subhalo <dkappa>=0.003 vs observed 0.009; LOS 0.008 | F: Subhaloes are insufficient; LOS structures dominate | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Primary lenses assumed SIE; multipoles and non-isothermal profiles not included  
  > "This assumption may be too simple." (Conclusion and Discussion)
- Caveat (inferred, ours): Only 11 lenses; small-sample significance
- Caveat (inferred, ours): Results depend on the SIE macromodel
- Caveat (inferred, ours): SDP.81 source size set to the beam size

## Reproducibility

- Data public (paper): SDP.81 image from the ALMA Science Portal  
  > "processed archival image of the band 7 continuum taken from the ALMA Science Portal" (4 Quadruple lens systems)
- Products in archive: _not stated_
- Missing: Per-system lens models and flux errors
- Missing: Semi-analytic LOS code and power spectra
- Data volume (inferred): <1 GB
- Score (inferred): 2/5, ALMA is a minor input and the key models are in companion papers.
- Rediscovery candidate: no, Mostly theory, with the recipe relying on companion papers.

## Links

- Method: (cite: takahashi-inoue2014) (LOS lensing formalism and CS cut)
- Method: (cite: han2015) (Subhalo mass function)
- Companion: (cite: inoue-minezaki2015) (SDP.81 anomaly analysis)
- Related: CASTLES

## Checks

```json
{
 "quotes": 25,
 "quotes_ok": 25,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 17,
  "rate": 0.274
 },
 "evidence_ok": true
}
```
