# Lupus disks with faint CO isotopologues: low gas/dust or high carbon depletion?

`2017A&A...599A.113M` | Astronomy and Astrophysics 2017 | first author: Miotello, A. | arXiv: 1612.01538 | DOI: 10.1051/0004-6361/201629556

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can CO isotopologue (13CO, C18O 3-2) and continuum data of Lupus disks, compared with DALI physical-chemical models, give gas masses and gas-to-dust ratios, and do low values indicate gas loss or carbon depletion?  
  > "Low CO-based gas masses and gas-to-dust ratios may indicate rapid loss of gas, or alternatively chemical evolution, e.g. via sequestering of carbon from CO to more complex molecules" (abstract)
- Target **Lupus disks (88 objects, Lupus ALMA Disk Survey)**: coordinates _not stated_; z/distance ~150 pc (Lupus I, II, IV); ~200 pc (Lupus III)  
  > "Lupus III is located at a distance of $\sim 200$ pc to the Sun, while Lupus I, II, and IV at $\sim 150$ pc." (2 ALMA observations); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00220.S
- bands: continuum 890 um (Band 7)  
  > "The disks were observed in continuum (890 $\mu$m) and CO isotopologues line emission" (2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 June 14 and 15  
  > "The observations were obtained on 2015 June 14 and 15." (2 ALMA observations)
- pi or archival as stated: Data from Cycle 2 Lupus ALMA Disk Survey, as presented by Ansdell16  
  > "More details on the observational settings and data reduction are presented in (cite: Ansdell16)." (2 ALMA observations)
- Line: 13CO J=3-2 (not stated)
- Line: C18O J=3-2 (not stated)
- Other facility **VLT/X-Shooter**: Stellar properties and mass accretion rates for the Lupus sample  
  > "stellar properties and mass accretion rates have been estimated from VLT/X-Shooter spectra for the same sample" (Introduction)
- External data: ALMA continuum and line fluxes, inclinations, and dust masses of Lupus disks  
  > "the inclination angle $i$ has been derived for many of the Lupus disks from continuum data by (cite: Ansdell16)" (4.1 Dust masses revisited) [from (cite: Ansdell16)]
- External data: Grid of ~800 DALI physical-chemical disk models  
  > "The grid by (cite: Miotello16) is composed of around 800 disk models" (3 Model) [from (cite: Miotello16)]
- External data: Mass accretion rates and stellar masses  
  > "the mass accretion rate onto the central star and the disk mass inferred from the dust, combining ALMA and VLT/X-Shooter data" (5.3 Correlation between disk gas mass and stellar mass) [from (cite: Manara16); (cite: Alcala14)]
- Simulation/model as data: DALI grid with disk masses 1e-5 to 1e-1 Msun, ray-traced at i=10 and 80 deg, plus extra models with Rc=30,60 au varying gas-to-dust ratio and carbon depletion  
  > "Disk masses vary between $10^{-5} M_{\odot}$ and $10^{-1} M_{\odot}$" (3 Model)

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

- Observational settings and data reduction  
  > "More details on the observational settings and data reduction are presented in (cite: Ansdell16)." (2 ALMA observations) [from (cite: Ansdell16)]
- Model grid and isotope-selective treatment  
  > "As in (cite: Miotello14) and in (cite: Miotello16), a complete treatment of CO isotope-selective processes is included." (3 Model) [from (cite: Miotello14); (cite: Miotello16)]

### Not stated but needed to reproduce (our reading)

- Measured continuum and 13CO/C18O line luminosities and uncertainties per source (from Ansdell16)
- Which sources use i=10 vs 80 deg individually
- How the mass uncertainty ranges (Mmax, Mmin) are derived exactly
- Details of the Bayesian regression setup (priors, upper-limit treatment)

## Analysis recipe

1. **Dust masses from continuum**: Fit median simulated 890 um luminosity vs dust mass from DALI grid (piecewise function) and invert for observed luminosities  
  > "The medians of the simulated continuum luminosities at 890 $\mu$m can be calculated for different dust masses" (4.1 Dust masses revisited)
   - software: DALI
   - parameter: Inclination 10 deg for i<70 deg or unknown; 80 deg otherwise  
  > "Lupus disks with $i<70^{\circ}$ or with unknown inclination are compared with models where $i$ = 10$^{\circ}$, elsewhere we employ models with $i$ = 80$^{\circ}$." (4.1 Dust masses revisited)
   - assumption: kappa = 4.3 cm2/g at 340 GHz (DALI standard)  
  > "The assumed dust opacity, $\kappa_{\nu}=4.3$ cm$^2$g$^{-1}$ at 340 GHz, is the standard value in DALI" (4.1 Dust masses revisited)
   - fitting: _not stated_
   - validation: Compared with Ansdell16 dust masses (factor 2.2 higher in Ansdell16)  
  > "dust masses derived by (cite: Ansdell16) are a factor of 2.2 higher than those estimated by this analysis" (4.1 Dust masses revisited)
2. **Gas masses from CO isotopologue luminosities**: Compare 13CO and C18O luminosities with model grid; for 13CO-only detections use fitted linear L-Mgas relation (optically thin); upper limits for non-detections  
  > "Accordingly we can use the fit function presented in Eq. [\[L_13\]](#L_13) to calculate the gas masses of these sources, as $^{13}$CO is optically thin" (4.2 Gas masses)
   - software: DALI
   - assumption: ISM carbon abundance [C]/[H]=1.35e-4  
  > "if the carbon over hydrogen ratio is set to the ISM-level, \[C\]/\[H\] = $1.35 \cdot 10^{-4}$" (5.2.1 Test models)
   - fitting: Piecewise fits of median line luminosity vs gas mass; uncertainty from range of model luminosities per mass bin  
  > "which covers the range of line luminosities simulated by the grid of models for different mass bins" (4.2 Gas masses)
   - validation: Test grid with L*=0.1 Lsun reduced line luminosities only up to 25%  
  > "we found that CO isotopologues line luminosities are reduced only up to 25%" (3 Model)
3. **Gas-to-dust ratios and scenario tests**: Divide gas by dust masses; run extra models with lower gas-to-dust ratio or carbon depletion delta_C=0.1,0.01 and compare with observations  
  > "the loss of gas is simulated by fixing the gas mass and increasing the dust mass, i.e. obtaining lower gas-to-dust ratios." (5.2.1 Test models)
   - software: DALI
   - fitting: _not stated_
   - validation: _not stated_
4. **Mgas-Mstar correlation**: Bayesian linear regression including upper limits  
  > "Using the Bayesian linear regression method (cite: Kelly07) which accounts for the upper limits" (5.3 Correlation between disk gas mass and stellar mass)
   - fitting: Kelly07 linear regression, errors on both axes  
  > "This is shown in Fig. [9](#Mstar) where the red line gives the Bayesian linear regression fit, which considers errors on both axes and is applied to both detected and undetected targets." (5.3 Correlation between disk gas mass and stellar mass)
   - validation: _not stated_

## Software

- **DALI** : Physical-chemical models of continuum and CO isotopologue emission  
  > "These models are computed with the physical-chemical code DALI" (3 Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of disks with gas masses | 34 | not stated | disks | 2 | disk gas masses have been calculated for a total of 34 sources |
| Disks with gas-to-dust ratio below 10 | 23 of 34 | not stated | disks | 3 | Most of the disks, 23 out of 34, present gas-to-dust ratios lower than 10 |
| Mgas-Mstar correlation coefficient | 0.74 | not stated | dimensionless | 4 | we find a correlation with $r = 0.74$ and a two-sided $p$-value of $3\cdot 10^{-2}$ |
| Mgas-Mstar slope | 0.63 | not stated | dimensionless | 4 | The slope of the correlation is 0.63 and the intercept is -3.92. |

## Qualitative findings

- Gas masses often below 1 MJup; CO-based Mdisk/Macc much smaller than region age, suggesting underestimated CO-based masses  
  > "this method suggests that CO-based disk masses are generally under-estimated." (5.3 Correlation between disk gas mass and stellar mass)

## Claim tuples

- H: Lupus disks have low gas masses and gas-to-dust ratios | E: Model-based gas and dust masses for 34 disks | R: Gas masses often <1 MJup; ratios mostly 1-10 | F: Gas-to-dust ratios far below 100 if carbon is not depleted | **supported**
- H: Low CO masses are due to gas loss vs carbon depletion | E: Extra DALI models with lower g/d or reduced carbon | R: Both reproduce the observations | F: Cannot distinguish with current data | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Four of 10 doubly detected disks are not reproduced by the model grid; full-disk models used for transition disks  
  > "Four of them are not reproduced by any of our models" (4.2 Gas masses)
- Caveat (inferred, ours): Gas masses depend on the model grid with fixed L*, Rc etc.
- Caveat (inferred, ours): Carbon depletion vs gas loss unresolved
- Caveat (inferred, ours): Mdisk/Macc argument assumes viscous evolution

## Reproducibility

- Data public (paper): ALMA data 2013.1.00220.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00220.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Model grid outputs (DALI) not given here
- Missing: Observed fluxes from Ansdell16 needed
- Missing: DALI code availability not stated
- Data volume (inferred): small (tens of GB raw; only catalog fluxes needed)
- Score (inferred): 3/5, Fit coefficients are tabulated, but the inputs come from companion papers and the DALI grid.
- Rediscovery candidate: no, Depends on the external DALI model grid and on fluxes from Ansdell16.

## Links

- Method: (cite: Miotello16) (DALI model grid and CO mass determination method)
- Method: (cite: Williams14) (CO isotopologue gas mass method)
- Companion: (cite: Ansdell16) (Lupus ALMA survey data and reduction)
- Companion: (cite: Manara16) (Macc vs dust mass correlation)
- Related: Lupus ALMA Disk Survey

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 27,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
