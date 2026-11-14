# PDS 70: A Transition Disk Sculpted by a Single Planet

`2019ApJ...879L...2M` | The Astrophysical Journal Letters 2019 | first author: Muley, Dhruv | arXiv: 1902.07191 | DOI: 10.3847/2041-8213/ab24d0

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Can a single accreting super-Jupiter (PDS 70b) carve the observed ~30 au gas and ~60 au dust cavity of the PDS 70 transition disk?  
  > "Could PDS 70b be the cause of this cavity? If so, what can we tell about its properties and evolutionary history from its interaction with the disk?" (Introduction)
- Target **PDS 70**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00888.S
- bands: Band 7 (350 GHz continuum and 12CO 3-2)  
  > "We have reduced the ALMA Band 7 observations of (cite: Long18) of the 350 GHz continuum and $^{12}$CO 3–2 emission" (Radiative transfer modeling)
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
- pi or archival as stated: Data from Long et al. 2018, reduced by the authors  
  > "We have reduced the ALMA Band 7 observations of (cite: Long18)" (Radiative transfer modeling)
- Line: 12CO J=3-2 (not stated)
- External data: Stellar mass M* = 0.76 Msun  
  > "Per (cite: Keppler18), we set $M_* = 0.76 \ M_\odot$." (HYDRODYNAMICS SIMULATIONS) [from (cite: Keppler18)]
- External data: Planet mass range 2-17 MJ and age ~4.6 Myr  
  > "Evolutionary models place the planet’s mass between 2 and 17 $M_{\rm J}$ (cite: Muller18)" (Introduction) [from (cite: Muller18)]
- Simulation/model as data: 2D PEnGUIn hydrodynamic fiducial run (accreting, migrating planet, 4.6 Myr) plus control runs with fixed 2, 4, 8 MJ planets, post-processed with DALI  
  > "We compare the results to three “control” runs, in which non-accreting planets of 2, 4, and 8 $M_{\rm J}$ are fixed on circular, 22 au orbits." (HYDRODYNAMICS SIMULATIONS)

## Processing

### Calibration

- pipeline or manual: Default pipeline scripts  
  > "reduced the ALMA Band 7 observations of (cite: Long18) of the 350 GHz continuum and $^{12}$CO 3–2 emission using the default pipeline scripts" (Radiative transfer modeling)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "cleaned the data using natural weighting, resulting in a beam size of 0.22”$\times$0.18”" (Radiative transfer modeling)
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
- final beam: 0.22” x 0.18”  
  > "resulting in a beam size of 0.22”$\times$0.18”" (Radiative transfer modeling)
- final rms: _not stated_

### Inherited from earlier work

- Gas/dust profile extrapolation procedure details  
  > "More details on this procedure are provided in (cite: vanderMarel16)." (Radiative transfer modeling) [from (cite: vanderMarel16)]
- PEnGUIn code identical to earlier work apart from accretion  
  > "the code is identical to that used for (cite: Fung18)" (HYDRODYNAMICS SIMULATIONS) [from (cite: Fung18)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA/pipeline version and tclean parameters (cell, image size, masking, continuum subtraction)
- Disk gas surface density profile and temperature/aspect ratio profile of initial condition
- DALI stellar spectrum, luminosity, CO abundance, grain properties, inclination, PA
- How model images were convolved/compared quantitatively to ALMA data
- Simulation code availability

## Analysis recipe

1. **Run 2D hydrodynamic simulations**: PEnGUIn with accretion prescription, planet migrating and accreting from 10 Earth masses at 23 au, run to 4.6 Myr; alpha0=0.001, Sigma0=3.86 g/cm2, domain 5-100 au  
  > "best-fit fiducial model, in which the planet is free to both migrate and accrete, with $\alpha_0 = 0.001$ and $\Sigma_0 = \SI{3.86}{\gram\per\cm\squared}$" (Results)
   - software: PEnGUIn
   - parameter: 960 x 1944 cells, 20 cells per scale height at 22 au  
  > "960 ($r$) $\times$ 1944 ($\phi$) cells" (Resolution)
   - assumption: M* = 0.76 Msun, 2D, fixed boundaries  
  > "Radial boundaries are fixed to their initial values" (HYDRODYNAMICS SIMULATIONS)
   - fitting: _not stated_
   - validation: Resolution tests +-50% give planet position within 8%  
  > "we find that the position of the planet agrees to within 8%" (Resolution)
2. **Radiative transfer post-processing and comparison with ALMA**: DALI models of 12CO 3-2 and 350 GHz continuum using simulated gas surface density and assumed dust profile, compared with ALMA Band 7 data  
  > "For the gas surface density, we use the output of the fiducial run." (Radiative transfer modeling)
   - software: DALI
   - parameter: Sigma_d,c=0.8 g/cm2, r_c=15 au, gamma=1, reduced 1e6 inside r_cav=60 au and 1e4 inside 10 au  
  > "with the surface density reduced by a factor of 10$^6$ for $r < r_{\rm cav}$, and 10$^4$ for $r<$ 10 au" (Radiative transfer modeling)
   - assumption: overall gas-to-dust ratio of 73  
  > "this yields an overall gas-to-dust ratio of 73" (Radiative transfer modeling)
   - fitting: _not stated_
   - validation: Qualitative comparison of SED, continuum ring and CO morphology  
  > "Figure [2](#fig:dalimodel) shows that the SED and continuum ring closely match the data." (Radiative transfer modeling)

## Software

- **PEnGUIn** : 2D GPU hydrodynamics of disk-planet interaction  
  > "We use the graphics processing unit (GPU)-accelerated code `PEnGUIn` (cite: FungThesis15) to simulate disk-planet interaction in 2D." (HYDRODYNAMICS SIMULATIONS)
- **DALI** : Radiative transfer / thermochemical post-processing  
  > "`DALI` is a physical-chemical modeling code (cite: Bruderer13)" (Radiative transfer modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Planet eccentricity saturation | 0.25 | not stated | dimensionless | 1 | which eventually saturates at $e_{\rm p} \approx 0.25$ |
| Planet mass for eccentricity onset | 2.7 | not stated | MJ | 1 | 960 $\times$ 1944 & 5–100 & 1 & 100 & 4600000 & 23 & 21 & 2.7 & Fiducial |
| Gas depleted below 0.01 g/cm2 out to | 30 | not stated | au | 1 | the planet has depleted the gas below $\Sigma = \SI{0.01}{\gram\per\cm\squared}$ out to 30 au, and produced a pressure peak at 62 au |
| Gas-to-dust ratio | 73 | not stated | dimensionless | 2 | this yields an overall gas-to-dust ratio of 73 |

## Qualitative findings


## Claim tuples

- H: A single accreting super-Jupiter at 22 au can carve the PDS 70 cavity | E: 2D hydro simulation plus DALI post-processing compared with ALMA | R: Gas cleared to ~30 au, pressure peak at 62 au, continuum ring and SED match | F: PDS 70b alone can carve the cavity; the planet grows eccentric (e~0.25) | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Fixed circular non-accreting planets (2, 4, 8 MJ) do not reproduce the wide gap  
  > "likewise, do not reproduce the wide, observed gap" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Model 12CO shows a central peak far stronger than observed, likely from the inner boundary  
  > "it also exhibits a bright central peak, significantly stronger than that found by ALMA" (Radiative transfer modeling)
- Caveat (inferred, ours): Comparison with ALMA is qualitative with no fit statistic
- Caveat (inferred, ours): 2D, simplistic accretion and fixed boundaries
- Caveat (inferred, ours): Dust profile tuned to the data

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Simulation code and DALI setup not provided
- Missing: ALMA imaging parameters
- Data volume (inferred): tens of GB
- Score (inferred): 2/5, Theory paper with a minor ALMA component and incomplete setup details.
- Rediscovery candidate: no, The main results come from simulations with unreleased code and are not ALMA measurements.

## Links

- Method: (cite: Bruderer13) (DALI code)
- Method: (cite: Fung18) (PEnGUIn setup)
- Companion: (cite: Long18) (Source of the ALMA data)

## Checks

```json
{
 "quotes": 31,
 "quotes_ok": 31,
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
  "facts": 62,
  "stated": 23,
  "rate": 0.371
 },
 "evidence_ok": true
}
```
