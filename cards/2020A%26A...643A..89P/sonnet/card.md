# Excitation and acceleration of molecular outflows in LIRGs: The extended ESO 320-G030 outflow on 200-pc scales

`2020A&A...643A..89P` | Astronomy and Astrophysics 2020 | first author: Pereira-Santaella, M. | arXiv: 2009.08481 | DOI: 10.1051/0004-6361/202038838

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How is the cold molecular outflow of the LIRG ESO 320-G030 excited and accelerated, and how do its physical conditions evolve with distance from the nucleus?  
  > "To investigate this, we obtained high-spatial resolution (70 pc; 0.3$''$) CO multi-transition (1–0, 2–1, 4–3, and 6–5) ALMA observations of the local luminous IR galaxy (LIRG) ESO 320-G030" (Introduction)
- Target **ESO 320-G030**: coordinates _not stated_; z/distance d = 48 Mpc; v_radio = 3049 km/s  
  > "ESO 320-G030 ($d=48$ Mpc; $L_{\rm IR}\slash L_\odot = 10^{11.3}$)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00263.S, 2013.1.00271.S
- bands: Bands 3, 6, 8, 9 (CO 1–0, 2–1, 4–3, 6–5)  
  > "with the ALMA 12-m array (Bands 3, 6, 8, and 9, respectively)" (2 ALMA data reduction)
- frequencies and spectral setup: Four 1.875 GHz spectral windows per band; channels ~1–3 km/s  
  > "Four spectral windows of 1.875 GHz were defined for all the Bands centered on various molecular transitions and continuum." (2 ALMA data reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array; Band 9 extended configuration only  
  > "Two 12-m array configurations, compact and extended, were considered" (2 ALMA data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.30'' (70 pc); matched to 0.37''x0.30''  
  > "the same angular resolution ($\sim$0.30$''$; 70 pc)" (2 ALMA data reduction)
- max recoverable scale: 3'' (700 pc)  
  > "maximum recoverable scale (3$''$; 700 pc)" (2 ALMA data reduction)
- sensitivity: 0.87 (Band 3), 0.98 (B6), 4.2 (B8), 7.6 (B9) mJy/beam  
  > "| 3 | 0.37$''$$\times$0.30$''$ | 5.1 | 0.87 | 1–0 | 2016.1.00263.S |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 1–0 (115.271 GHz)
- Line: CO 2–1 (230.538 GHz)
- Line: CO 4–3 (461.041 GHz)
- Line: CO 6–5 (691.473 GHz)
- Line: HNCO 21(0,21)-20(0,20) (461.450 GHz)
- Other facility **HST/NICMOS**: F110W and F160W images for stellar mass model  
  > "near-IR F110W (J-band) and F160W (H-band) *HST*/NICMOS images of this galaxy" (4.3.1 Gravitational potential model)
- Other facility **Spitzer/IRAC**: 3.6 micron image for stellar mass at larger radii  
  > "we used the *Spitzer*/IRAC 3.6 $\mu$m image" (4.3.1 Gravitational potential model)
- External data: CO(2–1) kinematic model (rotation curve) of the disk  
  > "we used the CO(2–1) kinematic model described in (cite: Pereira2016b)" (3.2 Spatially resolved outflow CO SLED) [from (cite: Pereira2016b)]
- External data: CO collisional coefficients  
  > "We include collisions with ortho- and para-H$_2$ using the (cite: Yang2010) collisional coefficients" (3.4 Non-LTE CO radiative transfer models) [from (cite: Yang2010)]
- External data: Inclination 43±2 deg  
  > "The inclination of ESO 320-G030 is 43$\pm$2$^\circ$ relative to the plane of the sky (cite: Pereira2016b)" (3.2 Spatially resolved outflow CO SLED) [from (cite: Pereira2016b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v5.4  
  > "We calibrated the data using CASA (v5.4)." (2 ALMA data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Nominal Cycle 4: 5% Band 3, 10% Band 6, 20% Bands 8 and 9  
  > "That is, 5% for Band 3, CO(1–0), 10% for Band 6, CO(2–1), and 20% for Bands 8 and 9, CO(4–3) and CO(6–5)." (2 ALMA data reduction)
- self calibration: _not stated_

### Imaging

- task: TCLEAN  
  > "The data were then cleaned using the TCLEAN CASA task" (2 ALMA data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "with a robustness parameter of 0.5" (2 ALMA data reduction)
- uv taper: _not stated_
- cell size: 0.06'' (0.04'' Band 9)  
  > "0.06$''$ (0.04$''$ for Band 9) pixels" (2 ALMA data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane constant fit to line-free channels  
  > "The continuum was subtracted in the *uv* plane by fitting a constant value using the line-free channels." (2 ALMA data reduction)
- line free channels: _not stated_
- primary beam correction: applied  
  > "These cubes were corrected for the primary beam patterns." (2 ALMA data reduction)
- array combination: _not stated_
- smoothing: imsmooth to 0.37''x0.30'' beam  
  > "we used the IMSMOOTH CASA task to obtain cubes with a 0.37$''$$\times$0.30$''$ (85 pc$\times$70 pc) beam" (2.2 Beam matching)
- final beam: 0.37''x0.30''  
  > "0.37$''$$\times$0.30$''$ (85 pc$\times$70 pc) beam" (2.2 Beam matching)
- final rms: _not stated_

### Inherited from earlier work

- CO(2–1) disk kinematic model and rotation curve  
  > "we used the CO(2–1) kinematic model described in (cite: Pereira2016b)" (3.2 Spatially resolved outflow CO SLED) [from (cite: Pereira2016b)]
- Band 6 CO(2–1) data previously analysed  
  > "The Band 6 CO(2–1) data have been already analyzed by (cite: Pereira2016b)" (2 ALMA data reduction) [from (cite: Pereira2016b)]
- Upper-limit treatment in probability  
  > "(see e.g., Appendix B of (cite: Pereira2015not))" (3.5 Bayesian CO SLED parameter inference) [from (cite: Pereira2015not)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Mask/threshold and niter used in tclean
- Number of channels/spectral resolution used in imaging per band and uv ranges
- Detection limit definition for high-velocity range
- Parameters of the 2D Gaussian HNCO fit and scaling
- Pereira2016b kinematic model parameters
- Whether flux comparisons need uv-matched data

## Analysis recipe

1. **Calibrate and image CO cubes, subtract HNCO, match beams**: CASA calibration, uv continuum subtraction, tclean Briggs, primary beam correction, HNCO model subtraction from CO(4–3), imsmooth to common beam  
  > "we degraded the angular resolution of the other CO data cubes to match the resolution of the CO(1–0)" (2.2 Beam matching)
   - software: CASA, tclean, imsmooth
   - parameter: robust 0.5; 5 km/s channels (21 km/s Band 9)  
  > "The final cleaned cubes have 5 km s$^{-1}$ channels (except the Band 9 that has 21 km s$^{-1}$ channels)" (2 ALMA data reduction)
   - fitting: _not stated_
   - validation: Checked amplitudes agree for common baselines between configurations  
  > "we verified that the amplitudes for the baselines in common for both configurations were in good agreement" (2 ALMA data reduction)
2. **Measure high-velocity CO fluxes in outflow sectors**: Define biconical outflow region split into annulus sectors; measure in 0.35'' circular regions; high-velocity range from disk model v±3σ extended to detection limit, defined on CO(2–1)  
  > "This high-velocity range starts at ${\rm v}_{\rm disk} + 3 \sigma_{\rm disk}$, and at ${\rm v}_{\rm disk} - 3 \sigma_{\rm disk}$ for the red- and blue-shifted sides, respectively." (3.2 Spatially resolved outflow CO SLED)
   - parameter: opening angle 65 deg, PA 22 deg, sector width ~1.1''  
  > "The opening angle of the outflow region is 65$^\circ$ and its central PA is 22$^\circ$ (east of north)." (3.2 Spatially resolved outflow CO SLED)
   - assumption: SLED independent of velocity within sector; outflow perpendicular to disk, i=43 deg  
  > "Assuming that the SLED does not depend on the velocity of the gas within a given sector" (3.2 Spatially resolved outflow CO SLED)
   - fitting: Two-Gaussian model for nuclear profiles  
  > "we used a two-Gaussian model to reproduce the nuclear profiles" (3.2 Spatially resolved outflow CO SLED)
   - validation: Inner sector fluxes treated as lower limits  
  > "the high-velocity emission is likely underestimated and should be considered as a lower limit" (3.2 Spatially resolved outflow CO SLED)
3. **Compute normalized CO SLEDs for nucleus, disk GMCs and outflow**: Nucleus r~1'' aperture; 126 disk GMC regions from >3σ CO(2–1) peaks; normalize to CO(2–1) and average  
  > "we defined 126 nonoverlapping regions in the disk, with radius of about 0.3$''$ (70 pc)" (3.3 Nuclear, disk, and outflow CO SLED comparison)
   - fitting: _not stated_
   - validation: _not stated_
4. **Non-LTE RADEX grid and Bayesian inference of gas conditions**: 64000-model RADEX grid; probability ∝ exp(-χ²/2) times erf factor for upper limits; marginalized PDFs  
  > "we calculated the $\chi^2$ for the 64000 models and assigned a probability to each model proportional to $\exp(-\chi^2\slash 2)$" (3.5 Bayesian CO SLED parameter inference)
   - software: RADEX
   - parameter: Tkin 3–400 K, nH2 1e2–1e5 cm-3, NCO/Δv 1e15–1e20, 40 log steps each  
  > "The grid consists of 40 steps for each parameter in log space and, therefore, a total of 64000 models." (3.4 Non-LTE CO radiative transfer models)
   - assumption: Z_CO = 1e-4; LTE H2 ortho-to-para ratio; Yang2010 collision rates  
  > "We assumed a fiducial $Z_{\rm CO}=10^{-4}$." (3.5 Bayesian CO SLED parameter inference)
   - fitting: Grid chi-square likelihood, uniform prior in log parameters, reweighted for derived quantities  
  > "we weighted the probability of the models to obtain a uniform prior for each of these derived quantities" (3.5 Bayesian CO SLED parameter inference)
   - validation: Best-fit SLEDs reproduce observations except CO(4–3) in B130 and R130  
  > "the models properly reproduce the observed SLEDs, except the CO(4–3) transition measured in the innermost outflow annulus sectors (B130 and R130)" (3.5 Bayesian CO SLED parameter inference)
5. **Thermal evolution and cloud stability**: Cooling time estimate with Neufeld1995 rate; K_vir from LVG Δv/R vs virial gradient  
  > "We approximate an upper limit on the cooling time $t_{\rm cool} < \left(3/2 k \Delta T\right)$/$\Lambda_{\rm 10\,K}\sim 100$ kyr" (4.1 Thermal evolution)
   - assumption: alpha 0.6–2.4  
  > "where $\alpha$ is between 0.6 and 2.4" (4.2 Outflowing clouds stability)
   - fitting: _not stated_
   - validation: _not stated_
6. **Dynamical evolution with gravitational potential and ram pressure**: Stellar potential from NICMOS and IRAC masses along z-axis; compare observed velocities vs distance; ram pressure vs gravity discussion  
  > "The final potential is the sum of potentials produced by all these mass distributions" (4.3.1 Gravitational potential model)
   - parameter: M/L 0.75 (F160W, Bell2001), 0.47 (3.6 um, McGaugh2014); no dark matter halo  
  > "we do not include a dark matter halo potential" (4.3.1 Gravitational potential model)
   - assumption: Outflow perpendicular to disk, i=43 deg  
  > "We assume a perpendicular to the disk outflow and a galaxy inclination of 43$^\circ$" (4.3 Dynamical evolution)
   - fitting: _not stated_
   - validation: Potential reproduces Halpha rotation ~200 km/s at ~5 kpc  
  > "This mass distribution reproduces relatively well the observed H$\alpha$ rotation velocity" (4.3.1 Gravitational potential model)

## Software

- **CASA** 5.4: Calibration, tclean imaging, imsmooth  
  > "We calibrated the data using CASA (v5.4)." (2 ALMA data reduction)
- **RADEX** : Non-LTE radiative transfer grid  
  > "we generated a grid of non-LTE radiative transfer models using the RADEX software" (3.4 Non-LTE CO radiative transfer models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Nuclear CO(6–5)/CO(2–1) ratio | 2.7 | 0.6 | dimensionless | 3 | / Nucleus / 0.24 $\pm$ 0.03 / 1.0 $\pm$ 0.1 / 2.9 $\pm$ 0.7 / 2.7 $\pm$ 0.6 / |
| Disk GMC CO(4–3)/CO(2–1) | 1.8 | 0.5 | dimensionless | 3 | / Disk GMC / 0.26 $\pm$ 0.05 / 1.0 $\pm$ 0.1 / 1.8 $\pm$ 0.5 / $<1.4$ / |
| Outer outflow (d>250 pc) CO(4–3)/CO(2–1) | <0.6 | not stated | dimensionless | 3 | / Outflow ($d>250$ pc) / 0.30 $\pm$ 0.10 / 1.0 $\pm$ 0.1 / $<0.6$ / $<0.8$ / |
| Nuclear Tkin | 37.6 | +119/-21.4 | K | 4 | / Nucleus / $37.6^{+119}_{-21.4}$ / |
| Disk GMC Tkin | 15.4 | +60/-6.8 | K | 4 | / Disk GMC / $15.4^{+60}_{-6.8}$ / |
| Mean outflow Tkin (d>250 pc) | 9.4 | 1.2 | K | 4 | / $\langle$Outflow$\rangle$$^{a}$ / $9.4\pm1.2$ / |
| Outflow (Δv/R)_LVG | 60 | +250/-45 | km/s/pc | 5 | For the outflow, $(\Delta$v$\slash R)_{\rm LVG}$=60$^{+250}_{-45}$ km s$^{-1}$ pc$^{-1}$. |
| Outflow K_vir range | 2–6000 | not stated | dimensionless | 5 | This corresponds to $K_{\rm vir}$=2–6000 |
| Cooling time upper limit | ~100 | not stated | kyr | 5 | $t_{\rm cool} < \left(3/2 k \Delta T\right)$/$\Lambda_{\rm 10\,K}\sim 100$ kyr |
| Launching velocity gradient 190–560 pc | ~0.8 | not stated | km/s/pc | 6 | This yields a velocity gradient of $\sim$0.8 km s$^{-1}$ pc$^{-1}$. |
| Stellar mass in central 3.4 kpc | 10^10.4 | not stated | Msun | 6 | we find a total stellar mass in the central 3.4 kpc of 10$^{10.4}$ $M_{\rm \odot}$ |

## Qualitative findings

- Outflowing molecular gas is less excited than nuclear and disk gas, opposite to most AGN-driven outflows  
  > "The outflowing molecular gas is less excited than the molecular gas in the nucleus (i.e., outflow launching site) and the disk GMCs." (5 Conclusions)

## Claim tuples

- H: Is the outflowing molecular gas less excited than nuclear and disk gas? | E: Multi-transition CO SLEDs in nucleus, disk GMCs and outflow sectors | R: CO(4–3)/CO(2–1) <0.6 in outer outflow vs 1.8±0.5 in disk and 2.9±0.7 in nucleus | F: Outflow is less excited, unlike most AGN-driven outflows | **supported**
- H: Are the outflowing clouds colder and unbound? | E: RADEX Bayesian modelling of SLEDs and virial comparison | R: Tkin ~9 K; K_vir 2–6000 | F: Outflow clouds are cold, low column density and not gravitationally bound unless CO abundance is >2 times lower | **supported**
- H: Can the gas have been entrained and cooled? | E: Cooling time estimate vs flow time | R: ~0.1 Myr cooling vs ~1.5 Myr flow time | F: Compatible with entrained gas, but condensation not rejected | **partially**
- H: What explains the outflow kinematics? | E: Gravitational potential model and ram pressure discussion | R: Constant max velocity 700–800 km/s to 1.7 kpc; pure gravity needs short timescale variation | F: Favored: ram pressure with inefficient cloud evaporation | **partially**

## Reasoning

- Why this data: Most outflow studies observe a single CO transition and do not fully resolve the outflow  
  > "However, most of these studies only observe one CO transition, and the molecular outflow is not always fully spatially resolved." (Introduction)
- Why this method: _not stated_
- Alternative: Radiation pressure rejected as negligible beyond 250 pc  
  > "the effect of the radiation pressure is negligible compared with the gravitational attraction" (4.3.3 Ram pressure acceleration and cloud destruction)
- How they decided it was enough: _not stated_
- Limitation (authors): Inner outflow fluxes uncertain due to broad nuclear profile; CO(4–3) excess unexplained  
  > "To investigate these options higher spatial resolution data would be required." (3.5 Bayesian CO SLED parameter inference)
- Caveat (inferred, ours): Single-zone RADEX with uniform priors gives weakly constrained density and opacity
- Caveat (inferred, ours): Outflow flux depends on disk-model velocity cuts defined from CO(2–1)
- Caveat (inferred, ours): Perpendicular-outflow assumption affects deprojection
- Caveat (inferred, ours): Mostly upper limits for CO(4–3) and CO(6–5) in outflow

## Reproducibility

- Data public (paper): Data from ALMA programs listed in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00263.S, ADS/JAO.ALMA#2013.1.00271.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Tclean mask, niter, line-free channels
- Missing: Pereira2016b disk kinematic model parameters
- Missing: Detection-limit definition for velocity range
- Missing: No code released
- Data volume (inferred): ~100–300 GB raw for four bands
- Score (inferred): 3/5, Data public and recipe moderately described, but many imaging and flux-extraction details are missing and the disk model is inherited.
- Rediscovery candidate: no, Key flux extraction details and the inherited kinematic model are incomplete, so reproduction is hard to do precisely.

## Links

- Method: (cite: vanderTak2007) (RADEX code)
- Method: (cite: Yang2010) (CO collisional coefficients)
- Companion: (cite: Pereira2016b) (Earlier CO(2–1) study with kinematic model of the same galaxy)
- Companion: (cite: Pereira2017Water) (Band 8 H2O detection from the same data)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 52,
  "rate": 0.634
 },
 "evidence_ok": true
}
```
