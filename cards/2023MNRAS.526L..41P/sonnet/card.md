# Kinematic and thermal signatures of the directly imaged protoplanet candidate around Elias 2-24

`2023MNRAS.526L..41P` | Monthly Notices of the Royal Astronomical Society 2023 | first author: Pinte, C. | arXiv: 2301.08759 | DOI: 10.1093/mnrasl/slad010

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Does the directly imaged protoplanet candidate in the Elias 2-24 disc have kinematic and thermal counterparts in the DSHARP 12CO data, and what planet mass or accretion do they imply?  
  > "We report kinematic and thermal signatures associated with the directly imaged protoplanet candidate in the Elias 2-24 disc." (abstract)
- Target **Elias 2-24**: coordinates _not stated_; z/distance 140 pc  
  > "We assumed a distance of 140 pc (cite: GaiaDR3)" (Models and disccussion); distance from Gaia DR3  
  > "We assumed a distance of 140 pc (cite: GaiaDR3)" (Models and disccussion)

## Data provenance

- ALMA projects: 2016.1.00484.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 0.09"x0.06" at PA=90 deg (fiducial DSHARP cube)  
  > "beam size 0.09"$\times$0.06" at PA=90$^\mathrm{o}$ with a rms of 1.4mJy/beam per channel" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 1.4 mJy/beam per channel  
  > "beam size 0.09"$\times$0.06" at PA=90$^\mathrm{o}$ with a rms of 1.4mJy/beam per channel" (Observations and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Publicly available DSHARP 12CO cube and measurement set  
  > "We used the publicly available $^{12}$CO data cube and measurement set from the Disc Substructures at High Angular Resolution Project" (Observations and data reduction)
- Line: 12CO J=2-1 (not stated)
- Other facility **VLT/NaCo**: L'-band ADI imaging of the planet candidate, re-reduced  
  > "We re-analysed the NaCo Elias2-24 observations in $L'$-band from July 15, 2018" (Observations and data reduction)
- External data: Original NaCo planet-candidate detection (separation 0.411", PA 302.10 deg, delta L' 8.81 mag)  
  > "The location is consistent within 1-$\sigma$ with ’s reported separation of 0.411$\pm$0.008 ", PA=302.10$\pm$1.14 deg, and $\Delta L'=8.81\pm0.12$ mag." (Results) [from Jorquera2021]
- Simulation/model as data: 3D SPH phantom gas+dust simulations with planets of 1-10 MJup at 65 au, post-processed with mcfost  
  > "we performed a series of 3D multigrain gas+dust simulations with the Smoothed Particle Hydrodynamics (SPH) code phantom (cite: Price2018), using $10^6$ particles" (Models and disccussion)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Publicly available DSHARP calibrated cube and measurement set used  
  > "Calibrated ALMA data sets are available at [alma-dl.mtk.nao.ac.jp/ftp/alma/lp/DSHARP]" (Data and software avaibility)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean with auto-masking, multiple robust/taper values  
  > "For all imaging attempts, we used the auto-masking function of tclean." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: tested with and without continuum subtraction  
  > "with and without continuum subtraction and the “JvM” correction" (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Imaging test strategy (robust, taper, continuum subtraction, JvM)  
  > "we followed (cite: Pinte2020) and imaged the data for a set of imaging parameters" (Observations and data reduction) [from Pinte2020]
- CO abundance prescription (freeze-out, photodissociation, photodesorption)  
  > "We set the CO abundance following the prescription in Appendix B of (cite: Pinte2018)" (Models and disccussion) [from Pinte2018]
- NaCo ADI cube, PSF, parallactic angles, platescale and true north calibrations  
  > "using the same pre-processed Angular Differential Imaging (ADI) cube, stellar point spread function and parallactic angles" (Observations and data reduction) [from Jorquera2021]

### Not stated but needed to reproduce (our reading)

- robust and taper values of the imaging grid
- fiducial cube robust value
- continuum-subtraction channels
- mcfost grid and photon settings
- how the CO spot Gaussian fit was done
- the exact mcfost accretion rates for each model

## Analysis recipe

1. **Re-reduce NaCo L' data**: median ADI, PCA-ADI and annular PCA-ADI; NEGFC with Nelder-Mead then MCMC for flux and position  
  > "We estimated the flux and position of the source by minimizing the residuals after injecting a negative fake companion (NEGFC) using a simplex Nelder-Mead minimization function." (Results)
   - software: vip, NaCo pipeline
   - parameter: ~4,500 MCMC steps, 120 walkers  
  > "with $\sim$4,500 steps and 120 walkers" (Results)
   - fitting: MCMC with Christiaens2021 log-probability  
  > "We used the new log-probability function introduced by (cite: Christiaens2021) to take into account the effect of stellar speckles." (Results)
   - validation: Contrast curves with Student statistics; detection 4 sigma in wedge, ~2 sigma in full frame  
  > "placing our detection at 4$\sigma$ in the wedge, or $\approx$ 2$\sigma$ in the full frame." (Results)
2. **Image CO and find the kinematic spot**: Image the DSHARP data with several imaging parameters; identify the detached CO spot, fit a Gaussian, make a partial moment 1 map  
  > "The planet signal we report below was detected in all resulting images." (Observations and data reduction)
   - software: CASA tclean
   - fitting: Gaussian fit to the CO spot  
  > "We measure a separation of 0.36$\pm$0.04" and PA = 290$\pm$3$^{\circ}$ by fitting a Gaussian to the CO spot." (Results)
   - validation: Spot recovered for all imaging choices  
  > "The planet signal we report below was detected in all resulting images." (Observations and data reduction)
3. **Model the planet-disc interaction**: phantom SPH simulations with planets of 1-10 MJup at 65 au, run for 100 orbits, post-processed with mcfost for dust temperature and CO channel maps  
  > "We evolved the simulations for 100 planet orbits" (Models and disccussion)
   - software: phantom, mcfost
   - parameter: 10^6 particles, 11 grain sizes 1 um-1 mm, M*=1.5 Msun, disc 0.01 Msun, H/R=0.1 at 50 au  
  > "We adopted a vertically isothermal equation of state with $H/R=0.1$ at $r=50$ au" (Models and disccussion)
   - assumption: distance 140 pc, gas-to-dust 100, astrosilicate grains, Tgas=Tdust, CO LTE, turbulent velocity zero  
  > "a gas-to-dust ratio of 100" (Models and disccussion)
   - fitting: _not stated_
   - validation: Qualitative comparison of model channel maps with the observations  
  > "None of our models reproduce all the observations." (Models and disccussion)

## Software

- **CASA tclean** : imaging the CO data  
  > "we used the auto-masking function of tclean" (Observations and data reduction)
- **vip** : NaCo ADI post-processing  
  > "based on the Vortex Image Processing package (vip, (cite: GomezGonzalez2017))" (Observations and data reduction)
- **phantom** : SPH simulations  
  > "the Smoothed Particle Hydrodynamics (SPH) code phantom (cite: Price2018)" (Models and disccussion)
- **mcfost** : radiative transfer for dust temperature and CO maps  
  > "We post-processed the models with the radiative transfer code mcfost" (Models and disccussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NaCo candidate separation | 0.37 | 0.04 | arcsec | 1 | We obtained a separation of 0.37$\pm$0.04" ($\sim$51.8 au) and a PA of 298.4$\pm$4.6$^{\circ}$. |
| NaCo candidate PA | 298.4 | 4.6 | deg | 1 | We obtained a separation of 0.37$\pm$0.04" ($\sim$51.8 au) and a PA of 298.4$\pm$4.6$^{\circ}$. |
| L' contrast | 8.78 | +0.98/-0.48 | mag | 1 | we derived an $L'$ contrast of 8.78$^{+0.98}_{-0.48}$ mag. |
| CO spot separation | 0.36 | 0.04 | arcsec | 2 | We measure a separation of 0.36$\pm$0.04" and PA = 290$\pm$3$^{\circ}$ |
| CO spot PA | 290 | 3 | deg | 2 | We measure a separation of 0.36$\pm$0.04" and PA = 290$\pm$3$^{\circ}$ |
| dynamical stellar mass | close to 1.5 | not stated | Msun | 3 | we find a dynamical stellar mass close to $1.5$M$_\odot$ |

## Qualitative findings

- The CO spot is detected in 6 channels, from -0.20 to 1.55 km/s, with 4 to 10 times the rms significance.  
  > "with a significance of 4 to 10 times the rms" (Results)

## Claim tuples

- H: Is there a CO kinematic counterpart to the NaCo planet candidate? | E: Imaged the DSHARP 12CO cube with several imaging choices | R: Detached CO spot near the candidate in all images | F: CO counterpart detected | **supported**
- H: What planet properties explain the CO spot? | E: phantom and mcfost model grid | R: A ~8 MJup planet, or a 3 MJup planet accreting at high rate, reproduces the spot | F: A warm embedded giant planet is implied; the mass is not robustly constrained | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cloud contamination hides the channels where a velocity kink is expected, so no robust kinematic mass is possible.  
  > "Hence it is not possible to estimate a robust planet mass from kinematics." (Models and disccussion)
- Caveat (inferred, ours): NaCo detection is only ~2 sigma in the full frame
- Caveat (inferred, ours): Models are not fitted; the mass range is qualitative
- Caveat (inferred, ours): Cloud contamination could mimic or shift the CO spot

## Reproducibility

- Data public (paper): Raw data public in ALMA and ESO archives; calibrated data and models on figshare  
  > "Raw data sets are publicly available on the ALMA and ESO archives." (Data and software avaibility)
- Products in archive: _not stated_
- Code: NaCo pipeline, phantom, mcfost and figure scripts on GitHub  
  > "The scripts used to make the figures are available at <https://github.com/cpinte/elias2-24>." (Data and software avaibility)
- Missing: exact imaging parameters
- Missing: full mcfost and phantom input files
- Data volume (inferred): ~10 GB for the DSHARP CO cube plus measurement set; simulations are the heavier part
- Score (inferred): 3/5, Public data and released code, but imaging settings are partly unspecified and the modelling is qualitative.
- Rediscovery candidate: no, The main results are qualitative model comparisons rather than a numeric recipe.

## Links

- Method: Pinte2020 (imaging tests for kinematic deviations in DSHARP CO)
- Method: Hammond2022 (NaCo reduction pipeline)
- Companion: Jorquera2021 (original NaCo planet candidate detection)
- Companion: Andrews2018 (DSHARP data release)
- Related: DSHARP

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 34,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
