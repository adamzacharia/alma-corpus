# Observational signatures of circumbinary discs - II. Kinematic signatures in velocity residuals

`2024MNRAS.534.2904C` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Calcino, Josh | arXiv: 2407.21309 | DOI: 10.1093/mnras/stae2233

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: What kinematic signatures do circumbinary discs leave in velocity-map residuals, and do they match observed discs such as HD 142527 and HD 100546?  
  > "In this work we study the kinematic signatures of circumbinary discs in the residuals of their velocity maps." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 100546**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **AB Aurigae, GG Tau, CS Cha, J1604, LkCa 15 and other discs in the sample table**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01353.S, 2018.1.01055.L, 2016.1.00826.S, 2015.1.00490.S, 2016.1.00344.S, 2013.1.00387.S, 2018.A.00021.S, 2018.1.00532.S, 2013.1.00498.S, 2016.A.00026.S, 2017.1.01404.S, 2021.1.00690.S, 2018.1.01255.S, 2018.1.00350.S, 2017.1.00969.S
- bands: Band 6 and Band 7  
  > "We utilised ALMA Band 6 and Band 7 archival $\rm ^{12}CO$ and $\rm ^{13}CO$ line data." (2.2 Observational Data)
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
- Line: 12CO J=3-2 (synthetic) (not stated)
- Line: 12CO/13CO 2-1 and 3-2 (observed) (not stated)
- External data: HD 100546 CO J=2-1 cube from Perez et al. 2020, public via Law et al. 2022  
  > "we obtained the CO J=2–1 from (cite: perez2020), made publicly available from (cite: law2022)." (4.2 HD 100546) [from (cite: perez2020); (cite: law2022)]
- External data: MAPS sample data and emission surfaces for GM Aur, HD 163296, IM Lupi, MWC 480  
  > "where the emission surfaces are taken from (cite: mapsiv)" (4.3 Fast-Flows Inside the Cavities of Transition Discs) [from (cite: mapsiv); (cite: MAPSI2021)]
- External data: Gas surface density estimates for HD 142527 used to scale model mass  
  > "We also scale the total gas mass of our simulation to be consistent with the gas surface density estimates from (cite: garg2021)." (4.1 HD 142527) [from (cite: garg2021)]
- Simulation/model as data: Phantom SPH gas-only circumbinary and planet disc simulations (models P, MP, EP, NOD, OD, EC, HIC, PC) with MCFOST synthetic 12CO(3-2) cubes  
  > "We used the smoothed particle hydrodynamics (SPH; (cite: monaghan1992)) code phantom (cite: phantom2018)." (2.1 SPH Simulations and Synthetic Observations)

## Processing

### Calibration

- pipeline or manual: Mostly self-calibrated products via private communication, or archive data calibrated with CASA pipeline  
  > "The majority of our data was obtained either via private communication as self-calibrated data products, or via the ALMA archive, calibrated using the CASA pipeline for the appropriate ALMA cycle." (2.2 Observational Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA  
  > "We imaged/re-imaged our data using the *tclean* task in CASA" (2.2 Observational Data)
- deconvolver: Multiscale Clean  
  > "with the Multiscale Clean deconvolver (cite: cornwell2008) with Briggs weighting" (2.2 Observational Data)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 5x RMS noise cut for all cubes  
  > "When generating our images we applied noise cuts of $5\times$ the RMS noise for all cubes." (2.2 Observational Data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: JvM and primary beam correction applied  
  > "and applied JvM (cite: JvM1995) and primary beam correction" (2.2 Observational Data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Synthetic observations and simulation details taken from Paper I  
  > "Our synthetic observations are the same as shown in ." (2.1 SPH Simulations and Synthetic Observations) [from Paper I (calcino2023)]
- Viscosity prescription from SPH artificial viscosity  
  > "used to produce a (cite: shakura1973) alpha viscosity $\alpha_\textrm{SS}$ following (cite: lodato2010)" (2.1 SPH Simulations and Synthetic Observations) [from (cite: lodato2010)]
- Model OD originally from Calcino et al. 2019, rescaled for HD 142527  
  > "The length is rescaled by a factor of 3.8 from the original model presented in (cite: calcino2019)" (4.1 HD 142527) [from (cite: calcino2019)]

### Not stated but needed to reproduce (our reading)

- Briggs robust values and per-target tclean parameters (cell, image size, scales, masks)
- Which cubes were self-calibrated and the self-cal settings
- eddy fit settings for observations (inclination, PA, mass, r_min/r_max, emission surface)
- Moment 1 vs quadratic choice per target
- Private-communication data products are not available
- CASA versions and software versions

## Analysis recipe

1. **Run SPH simulations**: Phantom gas-only SPH with sink-particle binary/companion, locally isothermal  
  > "Our gas discs are initialised with $5\times 10^{6}$ SPH particles following a surface density profile $\Sigma (R)\propto R^{-p}$" (2.1 SPH Simulations and Synthetic Observations)
   - software: phantom
   - parameter: p = 1, q_T = 0.25, primary mass 2 Msun  
  > "where we set $p = 1$ in all models." (2.1 SPH Simulations and Synthetic Observations)
   - assumption: Locally isothermal equation of state  
  > "We assume a locally isothermal equation of state with a temperature profile $T(R) \propto R^{-2q_T}$" (2.1 SPH Simulations and Synthetic Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Synthetic CO cubes**: MCFOST radiative transfer, then pymcfost convolution and noise  
  > "The CO cubes from mcfost were then processed to mimic the finite resolution and sensitivity capabilities of ALMA using the Python package pymcfost." (2.1 SPH Simulations and Synthetic Observations)
   - software: mcfost, pymcfost
   - parameter: 0.15'' beam, 250 m/s channels, noise 2.5 mJy, i=30 deg, PA=0, 100 pc  
  > "The final cubes had a spectral resolution of 250 ms$^{-1}$, and were convolved with a 0.15$\ensuremath{''}$ Gaussian beam." (2.1 SPH Simulations and Synthetic Observations)
   - assumption: T_dust=T_gas, LTE, 12CO/H2=1e-4, grain size dist s^-3.5  
  > "We assumed that $T_\textrm{dust} = T_\textrm{gas}$ and all molecules are at local thermodynamical equilibrium." (2.1 SPH Simulations and Synthetic Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Velocity maps and Keplerian residuals**: bettermoments maps with 5 sigma cut; eddy single-star Keplerian fit without flaring; subtract to get residuals  
  > "We fit the velocity maps using eddy (cite: eddy). Since the disc flaring is relatively small in our simulations, we fit Keplerian disc models that do not account for the disc flaring." (2.1 SPH Simulations and Synthetic Observations)
   - software: bettermoments, eddy
   - parameter: r_min varied in eddy fit to test residual dependence  
  > "which were obtained by changing the minimum radius, $r_\textrm{min}$, that is used in the fit with eddy." (3.1 Doppler-Flips)
   - assumption: Single central massive body, circular Keplerian  
  > "The Keplerian disc models assumed a single central massive body." (2.1 SPH Simulations and Synthetic Observations)
   - fitting: _not stated_
   - validation: Tested residuals against r_min and CO isotopologue  
  > "However high amplitude Doppler-flips are less dependent on the Keplerian model that is subtracted, as shown in Figure [4]" (3.1 Doppler-Flips)
4. **Compare to HD 142527 and HD 100546**: Rescale OD model for HD 142527 and new eccentric companion simulation (a=10 au, e=0.4) for HD 100546; compare velocity residuals with ALMA data  
  > "We also reproduced our eccentric companion model with a new simulation with a binary semi-major of 10 au, and eccentricity of 0.4." (4.2 HD 100546)
   - software: phantom, mcfost, eddy, bettermoments
   - parameter: HD 142527: primary 1.8 Msun, length rescale 3.8, i=27 deg, PA=-20 deg  
  > "we rescale our model OD such that the primary star has a mass of 1.8 M$_\odot$" (4.1 HD 142527)
   - fitting: _not stated_
   - validation: Qualitative visual comparison  
  > "Firstly, we see that our model recreates the observed spiral arms in the outer region of the disc found by (cite: christiaens2014) and further studied by (cite: garg2021)." (Applications to Observed Kinematic Features: HD 142527)
5. **Rotation curves near major axis for 16 observed discs**: Fit each velocity map with eddy; compare observed velocity along major axis with best-fit Keplerian, scaled by sin(i)  
  > "We fit each velocity map with eddy and use the resulting best-fit Keplerian model 2D velocity map to obtain the velocities along the same path close to the disc major axis as the observations." (4.3 Fast-Flows Inside the Cavities of Transition Discs)
   - software: eddy
   - assumption: Elevated emission surface for MAPS discs GM Aur, HD 163296, IM Lupi, MWC 480; flat Keplerian otherwise  
  > "or pure Keplerian rotation (all other observations)" (4.3 Fast-Flows Inside the Cavities of Transition Discs)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **phantom** : SPH simulations  
  > "We used the smoothed particle hydrodynamics (SPH; (cite: monaghan1992)) code phantom (cite: phantom2018)." (2.1 SPH Simulations and Synthetic Observations)
- **mcfost** : Monte Carlo radiative transfer  
  > "We used the Monte Carlo radiative transfer code mcfost (cite: pinte2006; pinte2009)." (2.1 SPH Simulations and Synthetic Observations)
- **pymcfost** : Mimic ALMA resolution and noise  
  > "using the Python package pymcfost" (2.1 SPH Simulations and Synthetic Observations)
- **bettermoments** : Integrated intensity and velocity maps  
  > "Integrated intensity and velocity maps were made from the cubes using bettermoments (cite: bettermoments2018)" (2.1 SPH Simulations and Synthetic Observations)
- **eddy** : Keplerian fits and residuals  
  > "We fit the velocity maps using eddy (cite: eddy)." (2.1 SPH Simulations and Synthetic Observations)
- **CASA** : tclean imaging of observed data  
  > "We imaged/re-imaged our data using the *tclean* task in CASA" (2.2 Observational Data)

## Numeric results


## Qualitative findings

- Circumbinary discs commonly show Doppler-flips, spirals, eccentric gas motion, fast flows in the cavity and vortex-like signatures in residuals.  
  > "We show that Doppler-flips, spiral arms, eccentric gas motion, fast flows inside of the cavity, and vortex-like kinematic signatures are commonly observed." (abstract)
- AB Aur and HD 100546 show highly perturbed rotation curves inside their cavities, possibly from massive companions.  
  > "We show that two transition discs, AB Aur and HD 100546, have highly perturbed rotation curves inside of their cavities" (5 Summary)

## Claim tuples

- H: Doppler-flips indicate planets | E: Residuals of circumbinary simulations | R: Doppler-flips appear and are not centred on the companion, linked to spirals | F: Doppler-flips should not be used alone as planet indicators | **supported**
- H: HD 142527 vortex-like kinematics need a vortex | E: Rescaled OD model compared to 13CO data | R: Model reproduces spirals and the Doppler-flip without vortical motion | F: Kinematics are consistent with an over-density lacking vortical motion | **partially**
- H: HD 100546 Doppler-flip arises from an internal massive companion | E: Eccentric companion model compared to CO 2-1 data | R: Flip and cavity perturbations reproduced | F: An eccentric internal companion can explain it | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Residuals are model dependent; Keplerian background assumed  
  > "By their very definition velocity residuals are model dependent, and the appearance of a Doppler-flip is therefore also model dependent." (3.1 Doppler-Flips)
- Caveat (inferred, ours): Comparisons with observations are qualitative with no quantitative fit
- Caveat (inferred, ours): Gas-only simulations without self-gravity or dust
- Caveat (inferred, ours): Single viewing inclination and few models
- Caveat (inferred, ours): No companion detected in HD 100546 yet

## Reproducibility

- Data public (paper): MAPS data public; other data in cited papers or by contacting authors; simulation dumps on Zenodo  
  > "Additional observational data can be found in the citations in the caption of Table 2, or by contacting the authors." (Data Availability Statement)
- Products in archive: _not stated_
- Code: phantom and mcfost publicly available on GitHub  
  > "phantom is publicly available at <https://github.com/danieljprice/phantom>, while mcfost is available at <https://github.com/cpinte/mcfost>." (Data Availability Statement)
- Missing: Full per-target imaging parameters
- Missing: Private self-calibrated products
- Missing: eddy fit configurations
- Data volume (inferred): Hundreds of GB for archival cubes across ~15 projects, plus simulation outputs
- Score (inferred): 3/5, Codes public and parameters largely given, but observational processing details and private data are missing and results are qualitative.
- Rediscovery candidate: no, Results are qualitative and some data are private.

## Links

- Method: (cite: eddy) (Keplerian fitting and residuals)
- Method: (cite: bettermoments2018) (Moment maps)
- Companion: (cite: calcino2023) (Paper I of the series with the same simulations)
- Related: MAPS
- Related: exoALMA

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 15,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 0,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 40,
  "rate": 0.449
 },
 "evidence_ok": true
}
```
