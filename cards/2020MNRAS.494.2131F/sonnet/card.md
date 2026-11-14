# Fast cloud-cloud collisions in a strongly barred galaxy: suppression of massive star formation

`2020MNRAS.494.2131F` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Fujimoto, Yusuke | arXiv: 2003.12074 | DOI: 10.1093/mnras/staa840

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: nearby_galaxies, star_formation
- Question: Why do bars of strongly barred galaxies lack massive star formation? Tested with a hydrodynamical simulation of NGC1300 comparing cloud properties and cloud-cloud collisions in bar, bar-end and arm regions.  
  > "We find that the collision speed in the bar is faster than those in the other regions." (abstract)
- Target **NGC1300**: coordinates _not stated_; z/distance 20.7 Mpc  
  > "the distance to NGC1300 of $d = 20.7\ \mathrm{Mpc}$" (2.2.2 Stellar potential); distance from Hubble parameter H = 73 km/s/Mpc, following England 1989b  
  > "the distance to NGC1300 of $d = 20.7\ \mathrm{Mpc}$" (2.2.2 Stellar potential)

## Data provenance

- ALMA projects: 2015.1.00925.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Atacama Compact Array (7m + total power)  
  > "observed with Atacama Compact Array (7m + total power) under project 2015.1.00925.S" (2.2.3 Gas mass)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 7.6'' x 4.1'' (760 pc x 410 pc)  
  > "The spatial resolution is $7.6^{\prime\prime} \times 4.1^{\prime\prime}$, corresponding to $760~{\rm pc} \times 410~{\rm pc}$" (2.2.3 Gas mass)
- max recoverable scale: _not stated_
- sensitivity: rms 11.0 mJy/beam per 10.0 km/s bin  
  > "The rms noise of the data cube is $11.0~\rm mJy~beam^{-1}$ per 10.0 $\rm km~s^{-1}$ bin." (2.2.3 Gas mass)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival data, proposed by B. Guillermo et al.  
  > "from the archival $^{12}$CO($2-1)$ data" (2.2.3 Gas mass)
- Line: 12CO J=2-1 (not stated)
- Other facility **HST**: V-band image of NGC1300  
  > "V-band image taken with Hubble Space Telescope (HST)" (2.2 The structure of the galactic disc)
- External data: HI gas mass (3.72 +/- 0.60)e9 Msun  
  > "HI gas mass of $(3.72 \pm 0.60 ) \times 10^9\ \mathrm{M_\odot}$ taken from the observations by (cite: England1989a)" (2.2.3 Gas mass) [from (cite: England1989a)]
- External data: Galactic CO-to-H2 conversion factor 4.4  
  > "Galactic CO-to-H$_2$ conversion factor of 4.4 $M_\odot~(\rm K~km~s^{-1}~pc^2)^{-1}$ (cite: BolattoWolfireLeroy2013)" (2.2.3 Gas mass) [from (cite: BolattoWolfireLeroy2013)]
- External data: CO(2-1)/CO(1-0) line ratio 0.8  
  > "the line ratio ($I_{\rm CO(2-1)}/I_{\rm CO(1-0)}$) of 0.8 (cite: LeroyEtAl2009)" (2.2.3 Gas mass) [from (cite: LeroyEtAl2009)]
- External data: Observed GMC properties in NGC1300 from ALMA CO(1-0), used for comparison  
  > "They had done $^{12}$CO($1-0$) observations toward the western bar, arm and bar-end regions with ALMA 12-m array with a beam size of $\sim$ 40 pc." (Appendix: Cloud properties comparison) [from (cite: MaedaEtAl2020)]
- Simulation/model as data: ENZO AMR hydrodynamic simulation of NGC1300 with fixed star-particle stellar potential and NFW halo, 1.95 pc min cell size, no star formation or feedback  
  > "producing a minimum cell size of $\Delta x =$ 1.953125 pc" (2.1 The code)

## Processing

### Calibration

- pipeline or manual: observatory-provided calibration script in CASA  
  > "We calibrated raw visibility data using the Common Astronomy Software Applications (CASA) and the observatory-provided calibration script." (2.2.3 Gas mass)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "We imaged the interferometric map using the CLEAN algorithm in CASA" (2.2.3 Gas mass)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "by adopting Briggs weighting with robust $=$ 0.5" (2.2.3 Gas mass)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: feathered with total power image  
  > "The resulting image is feathered with the total power image to recover the extended emission." (2.2.3 Gas mass)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Cloud tracking algorithm  
  > "The algorithm of this cloud tracking is described in (cite: TaskerTan2009)." (3.4 Cloud-cloud collisions) [from (cite: TaskerTan2009)]
- Collision-triggered SFR model with default epsilon=0.2, f_sf=0.5  
  > "we use the default values of $\epsilon = 0.2$ and $f_{\mathrm{sf}} = 0.5$ in (cite: Tan2000)" (3.4 Cloud-cloud collisions) [from (cite: Tan2000)]
- Stellar potential model  
  > "This model is based on the work of (cite: England1989b)" (2.2.1 Stellar potential) [from (cite: England1989b)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum/cube imaging details (cell, image size, masking, clean threshold) for the ACA CO(2-1) cube
- Flux calibrator and CASA version
- Total power data handling and feathering parameters
- Initial conditions random seeds and ENZO parameter files
- Observed SFR values (Maeda et al. in preparation)

## Analysis recipe

1. **Estimate gas mass from ACA CO(2-1)**: Calibrate, CLEAN, feather with TP; compute CO luminosity and convert to H2 mass; add HI mass  
  > "The total molecular gas mass is estimated to be $(1.70 \pm 0.78) \times 10^9~M_\odot$" (2.2.3 Gas mass)
   - software: CASA
   - parameter: alpha_CO = 4.4, R21 = 0.8  
  > "conversion factor of 4.4 $M_\odot~(\rm K~km~s^{-1}~pc^2)^{-1}$ (cite: BolattoWolfireLeroy2013)" (2.2.3 Gas mass)
   - fitting: _not stated_
   - validation: Simulated dense gas mass 1.69e9 Msun consistent with observed H2 mass  
  > "which is consistent with the observed molecular gas mass of $1.7 \times 10^9\ \mathrm{M_{\odot}}$" (3.1 Global structure)
2. **Run the hydrodynamic simulation**: ENZO AMR with ZEUS solver, cooling/heating from t=560 Myr, fixed stellar potential, NFW halo  
  > "we include the cooling and heating of the gas and additional two levels of refinement" (2.1 The code)
   - software: ENZO
   - parameter: pattern speed 20 km/s/kpc  
  > "We select $\Omega =$ 20 $\mathrm{km\ s^{-1}\ kpc^{-1}}$ for the production run" (2.2.1 Stellar potential)
   - fitting: _not stated_
   - validation: Bar size and rotation curve compared with observations  
  > "We also compare and roughly match the rotation curve from the simulation with the observational results" (2.2.2 Dark matter potential)
3. **Identify clouds and compare properties by region**: Threshold contour at n_H=400 cm^-3, minimum 3^3 cells; cumulative distributions of mass, radius, velocity dispersion, virial parameter in Bar, Bar-end, Arm  
  > "we use a slightly higher threshold density of $n_{\mathrm{H, c}} = 400\ \mathrm{cm}^{-3}$" (3.2 Cloud definition)
   - software: yt
   - fitting: _not stated_
   - validation: Compared with Maeda et al. 2020 observed GMCs  
  > "We compare the cloud properties with the observational results of the same galaxy of NGC1300 done by (cite: MaedaEtAl2020)." (Cloud properties: comparison with observations)
4. **Track clouds and measure collisions**: Tracking at 0.2 Myr intervals over 590-610 Myr; collision speed, frequency, estimated SFR  
  > "analysing simulation outputs at intervals of 0.2 Myr between $t =$ 590 and 610 Myr" (3.4 Cloud-cloud collisions)
   - fitting: _not stated_
   - validation: Kinetic-theory collision frequency compared with tracked frequency  
  > "the median is $\sim 16\ \mathrm{Gyr}^{-1}$, which is almost consistent with the actual collision frequency of $\sim 14.1\ \mathrm{Gyr}^{-1}$" (4.1)

## Software

- **CASA** : calibration and imaging of ACA CO(2-1) data  
  > "We imaged the interferometric map using the CLEAN algorithm in CASA" (2.2.3 Gas mass)
- **ENZO** : hydrodynamic simulation  
  > "adaptive mesh refinement (AMR) hydrodynamics code ENZO" (2.1 The code)
- **yt** : analysis of simulation  
  > "We acknowledge extensive use of the YT package" (Acknowledgements)
- **CLOUDY** : cooling table for metals  
  > "created from the CLOUDY package’s cooling table for metals" (2.1 The code)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) luminosity | 3.0e8 | 0.3e8 | K km/s pc^2 | 1 | is $(3.0 \pm 0.3) \times 10^8~\rm K~km~s^{-1}~pc^2$ |
| Total molecular gas mass | 1.70e9 | 0.78e9 | Msun | 1 | $(1.70 \pm 0.78) \times 10^9~M_\odot$ |
| Total gas mass | 5.42e9 | 0.98e9 | Msun | 1 | $(5.42 \pm 0.98) \times 10^9\ \mathrm{M_{\odot}}$ |
| Collision frequency Bar/Bar-end/Arm | 14.1 / 17.6 / 13.8 | not stated | Gyr^-1 | 4 | / Collision frequency: $f_{\mathrm{ccc}}$ / 14.1 / 17.6 / 13.8 / |
| Median collision speed Bar vs others | ~15 vs ~10 | not stated | km/s | 4 | Collisions in the *Bar* have the median of $\sim 15\ \mathrm{km\ s^{-1}}$ while collisions in the *Bar-end* and *Arm* have $\sim 10\ \mathrm{km\ s^{-1}}$ |

## Qualitative findings

- Cloud virial parameter ~1 with no environmental dependence  
  > "the median values are around $\alpha_{\mathrm{vir}} \sim 1$" (3.3)

## Claim tuples

- H: Cloud gravitational boundness explains the lack of massive stars in the bar | E: Compare virial parameters of simulated clouds across regions | R: alpha_vir ~1 in all regions | F: Virial state is not the cause | **supported**
- H: Fast cloud-cloud collisions in the bar suppress massive star formation | E: Track cloud collisions and compare speeds | R: Bar median ~15 km/s versus ~10 km/s elsewhere | F: Fast collisions are the likely cause | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Virial parameter and collision frequency rejected as causes (no environmental dependence)  
  > "a frequency of the cloud-cloud collisions does not seem to be the cause of the lack of the massive stars in strong bars" (3.4)
- How they decided it was enough: _not stated_
- Limitation (authors): No star formation or stellar feedback; simulated clouds smaller than observed; no beam convolution or CO radiative transfer  
  > "we need to convolve the simulation with the beam size of the observation and fine-tune the threshold density" (Appendix)
- Caveat (inferred, ours): Single snapshot and short 20 Myr window gives small collision samples
- Caveat (inferred, ours): Fixed epsilon and f_sf overpredict bar SFR
- Caveat (inferred, ours): ALMA data only set the gas mass normalisation

## Reproducibility

- Data public (paper): archival ALMA data  
  > "from the archival $^{12}$CO($2-1)$ data" (2.2.3 Gas mass)
- Products in archive: _not stated_
- Code: ENZO is public; analysis scripts not stated  
  > "the publicly available ENZO code" (Acknowledgements)
- Missing: ENZO parameter files and initial conditions
- Missing: Cloud tracking code
- Missing: Observed SFR values (in preparation)
- Data volume (inferred): ACA CO(2-1) cube, a few GB; the simulation needs HPC
- Score (inferred): 3/5, The simulation is described in detail but needs HPC and unreleased inputs; the ALMA part is minor.
- Rediscovery candidate: no, Main results come from a large simulation, not from the ALMA data.

## Links

- Method: (cite: TaskerTan2009) (cloud tracking algorithm)
- Method: (cite: Tan2000) (collision-triggered SFR model)
- Companion: (cite: MaedaEtAl2020) (ALMA CO(1-0) GMC observations of NGC1300 used for comparison)
- Companion: (cite: FujimotoTaskerHabe2014) (earlier simulation of weakly barred M83)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "facts": 74,
  "stated": 39,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
