# Consistent Dust and Gas Models for Protoplanetary Disks. III. Models for Selected Objects from the FP7 DIANA Project

`2019PASP..131f4301W` | Publications of the Astronomical Society of the Pacific 2019 | first author: Woitke, P. | arXiv: 1812.02741 | DOI: 10.1088/1538-3873/aaf4e5

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can a standardized thermo-chemical modelling approach fit all available multi-wavelength continuum and line observations of protoplanetary disks simultaneously, and what disk shapes, masses and dust properties result?  
  > "Can we fit all available observational data with a standardized modeling approach, using 2D thermo-chemical disk models, only by varying the disk mass and shape parameters, the gas/dust ratio and the dust size and opacity parameters?" (Summary and Outlook)
- Target **RECX 15**: coordinates _not stated_; z/distance 94.3 pc  
  > "| RECX 15 | M3 | 94.3 | 0.65 | 3400 | 0.091 | 0.28 | 6.5 |" (Table 1); distance from literature distances (Table 1)  
  > "| RECX 15 | M3 | 94.3 | 0.65 | 3400 | 0.091 | 0.28 | 6.5 |" (Table 1)
- Target **DM Tau**: coordinates _not stated_; z/distance 140 pc  
  > "| DM Tau | M0 | 140 | 0.55 | 3780 | 0.232 | 0.53 | 6.0 |" (Table 1); distance from literature distances (Table 1)  
  > "| DM Tau | M0 | 140 | 0.55 | 3780 | 0.232 | 0.53 | 6.0 |" (Table 1)
- Target **MWC 480**: coordinates _not stated_; z/distance 137 pc  
  > "| MWC 480 | A5 | 137 | 0.16 | 8250 | 13.7 | 1.97 | 11 |" (Table 1); distance from literature distances (Table 1)  
  > "| MWC 480 | A5 | 137 | 0.16 | 8250 | 13.7 | 1.97 | 11 |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00133.S, 2011.0.00629.S, 2015.1.00657.S
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
- pi or archival as stated: mostly archival multi-instrument data; RECX 15 ALMA cycle-0 data are the authors' own  
  > "We used multi-wavelength, multi-instrument, mostly archival data comprising photometry, low-resolution IR to far-IR spectra, continuum images and line observations" (Summary and Outlook); "Our ALMA cycle-0 data shows a faint, very broad CO $J\!=$3-2 line (FWHM $\approx\!15\,$km/s)" (4.5 DIANA Standard Models)
- Line: CO J=3-2 (not stated)
- Other facility **Herschel, Spitzer, ISO, SMA, VLT, IUE/FUSE/HST, XMM-Newton, Chandra**: photometry, spectra, images, line fluxes and profiles, UV and X-ray spectra  
  > "A large collection of UV low- and high-resolution archival data was collected from different instruments (IUE, FUSE, STIS, COS, ACS)" (3.1 Modeling step 1); "X-ray data was collected from XMM-Newton and Chandra." (3.1 Modeling step 1)
- External data: Stellar distances and effective temperatures  
  > "we used distance $d$ and effective temperatures $T_{\rm eff}$-values from the literature" (3.1 Modeling step 1) [from literature, not specified]
- External data: UV and X-ray spectral analysis of the stars  
  > "The details are described in (cite: Dionatos2018)." (3.1 Modeling step 1) [from (cite: Dionatos2018)]

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

- Physical and chemical assumptions of the models, and the stellar-parameter method  
  > "The method we have used for all objects is explained in (cite: Woitke2016)" (3.1 Modeling step 1); "Our physical assumptions about the gas, dust particles and PAHs in the protoplanetary disk are detailed in (cite: Woitke2016)." (3.2 Modeling step 2) [from (cite: Woitke2016)]
- Standard chemical networks and element abundances  
  > "The details of our thermo-chemical models are explained in (cite: Woitke2016; Kamp2017), which we summarize here as follows" (3.3 Modeling step 3) [from (cite: Kamp2017)]
- DIANA standard dust opacities  
  > "we apply the DIANA standard dust opacities for disks" (3.2 Modeling step 2) [from (cite: Min2016)]

### Not stated but needed to reproduce (our reading)

- Details of ALMA calibration and imaging for RECX 15, DM Tau and MWC 480 (how line fluxes and radial profiles were extracted)
- Final chi2 weights per object (only in downloadable files)
- Random seeds and initial parameters for the genetic algorithm

## Analysis recipe

1. **fit stellar parameters and irradiation**: Fit PHOENIX photospheres to photometry and UV with a (1,12) evolutionary strategy; add UV and X-ray spectra  
  > "We have used the $(1,12)$-evolutionary strategy of (cite: Rechenberg1994) to fit our model parameters $P_j$" (3.1 Modeling step 1)
   - software: PHOENIX
   - assumption: R_V = 3.1  
  > "A standard value of $R_V\!=\!3.1$ is applied to all stars if not stated otherwise." (3.1 Modeling step 1)
   - fitting: _not stated_
   - validation: _not stated_
2. **SED fitting**: Monte Carlo radiative transfer of up to two-zone passive disks fitted with the same genetic algorithm  
  > "These disk models are run by means of our fast Monte Carlo radiative transfer tools MCFOST and/or MCMax." (3.2 Modeling step 2)
   - software: MCFOST, MCMax
   - fitting: _not stated_
   - validation: _not stated_
3. **thermo-chemical DIANA standard models**: ProDiMo models fitted jointly to SED, images, line fluxes, profiles and maps; radial profiles from ALMA maps are compared to model  
  > "The final step of our data analysis is therefore to run full radiation thermo-chemical models with an enlarged set of continuum and line observations." (3.3 Modeling step 3)
   - software: ProDiMo, FLiTs
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ProDiMo** : thermo-chemical disk models  
  > "(ProDiMo, MCFOST, MCMax)" (abstract)
- **MCFOST** : Monte Carlo continuum radiative transfer  
  > "These disk models are run by means of our fast Monte Carlo radiative transfer tools MCFOST and/or MCMax." (3.2 Modeling step 2)
- **MCMax** : Monte Carlo continuum radiative transfer  
  > "These disk models are run by means of our fast Monte Carlo radiative transfer tools MCFOST and/or MCMax." (3.2 Modeling step 2)
- **FLiTs** : 3D line radiative transfer prediction of spectra  
  > "3D diagnostic radiative transfer tools (e.g. FLiTs) are eventually used to predict all available observations" (abstract)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean disk mass to stellar mass ratio | 0.72 | not stated | % | 2 | / mean value$^\star$ /  /  /  / 27.7 / 6.32 /  /  /  / 0.72 % / |
| log10 alpha_settle | -2.9 | 0.9 | dimensionless | 3 | $\log_{10}\alpha_{\rm set}=-2.9\pm0.9$ |
| outer-disk gas/dust ratio (8 free models) | 120 | +170/-70 | dimensionless | 3 | the remaining 8 models have $\rm gas/dust=120^{+170}_{-70}$. |
| HD 163296 outer disk gas mass | 0.58 | not stated | Msun | 3 | The outer disk is found to be very massive in this model (0.58 M$_\odot$) |

## Qualitative findings

- Many disks have cold massive outer disks partly shadowed by a tall, gas-rich inner disk; classical dust masses can be wrong.  
  > "Our analysis shows a number of Herbig Ae and T Tauri stars with very cold and massive outer disks which are situated at least partly in the shadow of a tall and gas-rich inner disk." (abstract)

## Claim tuples

- H: A standardized 2D thermo-chemical model can fit all data per object | E: three-step fitting for 27 SED and 14 full models | R: most line fluxes within a factor 3, some data unfittable | F: yes, but solutions are not unique | **supported**
- H: Classical Rayleigh-Jeans dust mass is reliable | E: compare model masses to classical estimates | R: offsets up to a factor 15 | F: classical method biased for cold and warm disks | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: MCMC for error bars rejected as too costly  
  > "Running MCMC models to determine errorbars was not feasible." (3.3 Modeling step 3)
- How they decided it was enough: _not stated_
- Limitation (authors): Results probably not unique, only a local chi2 minimum near the SED fit  
  > "our computational resources only allowed us to find a $\chi^2$ minimum in the neighborhood of the SED-fitting model in parameter space." (3.3 Modeling step 3)
- Caveat (inferred, ours): ALMA data are a small fraction of the data and are not reprocessed
- Caveat (inferred, ours): chi2 weighting is subjective and unvalidated

## Reproducibility

- Data public (paper): data collection and model outputs available online  
  > "Our data collection, the fitted physical disk parameters as well as the full model output are available to the community through an online database" (abstract)
- Products in archive: _not stated_
- Code: Model setup files released; the codes themselves are not stated as released  
  > "all users of MCFOST, MCMax or ProDiMo can download setup files to re-run our disk models." (Summary and Outlook)
- Missing: Access to ProDiMo/MCFOST/MCMax
- Missing: ALMA reduction details
- Missing: Heavy compute (tens of thousands CPU hours per object)
- Data volume (inferred): small for ALMA (3 targets); models heavy in compute
- Score (inferred): 2/5, ALMA minor and theory-heavy; large compute needed, but model files are public.
- Rediscovery candidate: no, Requires huge compute and ALMA processing is not described.

## Links

- Method: (cite: Woitke2016) (models and assumptions)
- Method: (cite: Kamp2017) (chemical networks)
- Method: (cite: Dionatos2018) (UV and X-ray data)
- Related: FP7 DIANA project

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.00657.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 27,
  "rate": 0.37
 },
 "evidence_ok": true
}
```
