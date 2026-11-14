# ALMA observations of the vibrationally excited rotational CO transition v = 1, J = 3 - 2 towards five AGB stars

`2016MNRAS.463L..74K` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Khouri, T. | arXiv: 1608.03271 | DOI: 10.1093/mnrasl/slw161

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the extents, densities and kinematics of the warm molecular layer of AGB stars, probed by the CO v=1 J=3-2 line detected serendipitously with ALMA?  
  > "We constrain the extents, densities, and kinematics of the region where the lines are produced." (abstract)
- Target **o Cet**: coordinates _not stated_; z/distance 107 pc  
  > "| $o$ Cet | 107 | 331 | 8.1 | $2.5\times10^{-7}$ |" (Table 1); distance from van Leeuwen 2007, Whitelock 2008, Min 2014 or Mayer 2014 (per-source assignment not stated)  
  > "| $o$ Cet | 107 | 331 | 8.1 | $2.5\times10^{-7}$ |" (Table 1)
- Target **R Aqr**: coordinates _not stated_; z/distance 218 pc  
  > "| R Aqr | 218 | 387 | 20.0 | $9\times 10^{-6}$ |" (Table 1); distance from van Leeuwen 2007, Whitelock 2008, Min 2014 or Mayer 2014 (per-source assignment not stated)  
  > "| R Aqr | 218 | 387 | 20.0 | $9\times 10^{-6}$ |" (Table 1)
- Target **R Scl**: coordinates _not stated_; z/distance 370 pc  
  > "| R Scl | 370 | 370 | 17.0 | $1 \times 10^{-6}$ |" (Table 1); distance from van Leeuwen 2007, Whitelock 2008, Min 2014 or Mayer 2014 (per-source assignment not stated)  
  > "| R Scl | 370 | 370 | 17.0 | $1 \times 10^{-6}$ |" (Table 1)
- Target **W Aql**: coordinates _not stated_; z/distance 395 pc  
  > "| W Aql | 395 | 490 | 20.0 | $4\times 10^{-6}$ |" (Table 1); distance from van Leeuwen 2007, Whitelock 2008, Min 2014 or Mayer 2014 (per-source assignment not stated)  
  > "| W Aql | 395 | 490 | 20.0 | $4\times 10^{-6}$ |" (Table 1)
- Target **pi1 Gru**: coordinates _not stated_; z/distance 163 pc  
  > "| $\pi^1$ Gru | 163 | 195 | 30.0 | $8.5\times 10^{-7}$ |" (Table 1); distance from van Leeuwen 2007, Whitelock 2008, Min 2014 or Mayer 2014 (per-source assignment not stated)  
  > "| $\pi^1$ Gru | 163 | 195 | 30.0 | $8.5\times 10^{-7}$ |" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00524.S, 2012.1.00097.S
- bands: _not stated_
- frequencies and spectral setup: Spectral windows 0.937 GHz wide centred at 342.883 GHz for R Scl; 1.875 GHz wide centred at 343.30 GHz for the other four  
  > "observed spectral windows 0.937 GHZ wide and centred at 342.883 GHz for R Scl and 1.875 GHz wide and centred at 343.30 GHz for the other four sources" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: o Cet 2014-02-25 and 2014-05-03; R Aqr 2015-05-21; R Scl 2013-12-14, 2014-12-25, 2015-07-24; W Aql 2014-03-20, 2014-04-14; pi1 Gru 2013-10-08, 2014-03-25  
  > "on 2014-03-20 and 2014-04-14 for W Aql, and on 2013-10-08 and 2014-03-25 for $\pi^1$ Gru." (Table 1)
- pi or archival as stated: _not stated_
- Line: CO v=1, J=3-2 (342.647 GHz)
- Other facility **AAVSO**: Pulsation phases of the observations  
  > "obtained from data from the American association of variable stars observers" (Table 1)
- External data: Mass-loss rates and terminal expansion velocities, periods  
  > "The $\dot{M}_{\rm gas}$ are those given by (cite: DeBeck2010)" (Table 1) [from DeBeck2010; Maercker2016; Danilovich2014; Bujarrabal2010]
- External data: Stellar distances  
  > "The distances were retrieved from (cite: vanLeeuwen2007)" (Table 1) [from vanLeeuwen2007; Whitelock2008; Min2014; Mayer2014]

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

- o Cet observations were presented earlier  
  > "The observations of $o$ Cet were presented by (cite: Ramstedt2014a)." (2 Observations) [from (cite: Ramstedt2014a)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- Imaging parameters (weighting, cell, continuum subtraction, line-free channels)
- How line profiles and continuum fluxes were extracted
- Fitting procedure details for chi2 mapping and grid steps
- Source coordinates and per-source distance references
- Velocity resolution

## Analysis recipe

1. **Estimate outflow contribution**: Non-LTE spherically symmetric radiative transfer of outflows to compare predicted line strength with observed  
  > "we used GASTRoNOoM (cite: Decin2006) to calculate non-LTE spherically-symmetric radiative transfer models for the outflows of the five sources." (3 Modelling)
   - software: GASTRoNOoM
   - parameter: initial expansion velocity 2 km/s; stellar temperature 3000 K  
  > "We adopt an initial expansion velocity, $\upsilon(R_\circ) = \upsilon_\circ$, of 2 km/s." (3 Modelling)
   - assumption: Outflow emission neglected in fits  
  > "we have not considered emission from the outflow when fitting the observations." (3 Modelling)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit WML line profiles**: Spherical WML radiative transfer with constant density and vibrational temperature; stellar radius from ALMA continuum; line-of-sight intensity integration  
  > "We opt for a simple model in which the density, $n_{\rm WML}$, and excitation temperature of CO, $T^{\rm Vib}_{\rm WML}$, are constant throughout the WML." (3 Modelling)
   - parameter: T_vib = 1000, 1500, 2000 K; free: R_o, n_WML, velocity dispersion, global radial velocity  
  > "We calculated models with $T^{\rm Vib}_{\rm WML}$ equal to 1000 K, 1500 K, and 2000 K." (3 Modelling)
   - assumption: Stellar temperature 3000 K blackbody; companion ignored  
  > "We have not considered the presence of a companion star in our calculations." (3 Modelling)
   - fitting: 1 sigma uncertainties from mapping chi2 around best model for inverse P-Cygni profiles; from line flux uncertainty for o Cet and W Aql  
  > "we obtained the $1\sigma$ uncertainties from mapping the $\chi^{2}$ around the best model" (4 Discussion)
   - validation: _not stated_

## Software

- **GASTRoNOoM** : Non-LTE radiative transfer for outflows  
  > "we used GASTRoNOoM (cite: Decin2006) to calculate non-LTE spherically-symmetric radiative transfer models" (3 Modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| o Cet peak flux density, 2014-02-25 to 2014-05-03 | 0.15 to 0.40 | not stated | Jy | 0 | the peak flux density increases from 0.15 Jy close to minimum-light phase to 0.40 Jy close to maximum-light phase |
| R Aqr R_o (T_vib=1500 K) | 3.63 | 0.03 | AU | 2 | /  /  /  /  /  $3.63\pm0.03$ / $2.3 \times 10^{10}$ /  $1.0\pm{0.1} \times 10^{11}$ / 12.6 / 1500 / |
| Max fraction of WML mass lost per pulsation cycle, o Cet | ≲1.0 | not stated | % | 2 | $\lesssim 1.0\%$ for $o$ Cet and $\lesssim 7.5\%$ for W Aql |

## Qualitative findings

- R Aqr and R Scl show inverse P-Cygni profiles indicating infall; o Cet and R Scl show line variability  
  > "R Aqr and R Scl show inverse P-Cygni line profiles which indicate infall of material onto the stars." (abstract)

## Claim tuples

- H: Vibrationally excited CO rotational lines are detectable with ALMA towards AGB stars and trace the WML | E: Serendipitous detection in five stars and simple WML radiative transfer fits | R: Line detected in 5 of 5 sources; fitted with constant-density WML models | F: Such lines can be observed towards many nearby AGB stars | **supported**
- H: Lines indicate infall in some stars | E: Inverse P-Cygni profile modelling | R: Models require infalling gas for R Aqr and R Scl | F: Material falls back onto the stars | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties reflect only the fitting; systematic errors from model assumptions can be larger  
  > "the systematic errors from our model assumptions can be larger than those." (4 Discussion)
- Caveat (inferred, ours): Simple constant-density spherical model with strong parameter degeneracy
- Caveat (inferred, ours): Mass-loss rates highly uncertain for R Aqr and R Scl
- Caveat (inferred, ours): No data reduction details given

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduction and imaging details
- Missing: Model code
- Missing: Exact fitting grid
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Data archival and model described, but reduction and fitting details missing.
- Rediscovery candidate: no, Processing steps and model code not specified.

## Links

- Method: Decin2006 (GASTRoNOoM code)
- Companion: Ramstedt2014a (Earlier presentation of o Cet data)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 27,
  "rate": 0.375
 },
 "evidence_ok": true
}
```
