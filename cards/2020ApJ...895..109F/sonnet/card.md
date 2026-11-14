# Measuring Turbulent Motion in Planet-forming Disks with ALMA: A Detection around DM Tau and Nondetections around MWC 480 and V4046 Sgr

`2020ApJ...895..109F` | The Astrophysical Journal 2020 | first author: Flaherty, Kevin | arXiv: 2004.12176 | DOI: 10.3847/1538-4357/ab8cc5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How strong is non-thermal (turbulent) gas motion in the DM Tau, MWC 480 and V4046 Sgr disks, measured from CO(2-1) with parametric disk models, and is weak turbulence common?  
  > "Using parametric models of disk structure, we robustly detect non-thermal gas motions around DM Tau of between 0.25 c$_s$ and 0.33 c$_s$" (abstract)
- Target **DM Tau**: coordinates phase center 04:33:48.73 +18:10:09.7  
  > "04:33:48.732781 +18:10:09.67744" (Table 1); "144.5 $\pm$ 1.1 (4)" (Table 2); z/distance 144.5 ± 1.1 pc  
  > "04:33:48.732781 +18:10:09.67744" (Table 1); "144.5 $\pm$ 1.1 (4)" (Table 2); distance from GAIA DR2 parallax  
  > "04:33:48.732781 +18:10:09.67744" (Table 1); "144.5 $\pm$ 1.1 (4)" (Table 2)
- Target **MWC 480**: coordinates phase center 04:58:46.27 +29:50:36.5  
  > "04:58:46.271217 +29:50:36.52973" (Table 1); "161.1 $\pm$ 2.0 (4)" (Table 2); z/distance 161.1 ± 2.0 pc  
  > "04:58:46.271217 +29:50:36.52973" (Table 1); "161.1 $\pm$ 2.0 (4)" (Table 2); distance from GAIA DR2 parallax  
  > "04:58:46.271217 +29:50:36.52973" (Table 1); "161.1 $\pm$ 2.0 (4)" (Table 2)
- Target **V4046 Sgr**: coordinates phase center 18:14:10.47 -32:47:35.4  
  > "18:14:10.468875 -32:47:35.43708" (Table 1); "72.26 $\pm$ 0.34 (4)" (Table 2); z/distance 72.26 ± 0.34 pc  
  > "18:14:10.468875 -32:47:35.43708" (Table 1); "72.26 $\pm$ 0.34 (4)" (Table 2); distance from GAIA DR2 parallax  
  > "18:14:10.468875 -32:47:35.43708" (Table 1); "72.26 $\pm$ 0.34 (4)" (Table 2)

## Data provenance

- ALMA projects: 2016.1.00724.S
- bands: Band 6  
  > "ALMA band 6 observations of the disks around DM Tau, MWC 480, and V4046 Sgr" (2 Observations)
- frequencies and spectral setup: continuum window at 232 GHz plus CO, 13CO, C18O (2-1) windows; 960 channels of 61.035 kHz (~80 m/s), binned by 2 to 0.16 km/s  
  > "For the spectral lines, the correlator was configured for 960 channels, each 61.035 kHz wide ($\sim$80 m s$^{-1}$)." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 2.6 km  
  > "with baselines ranging from 15 m to 2.6 km" (2 Observations)
- angular resolution: ~0.3-0.5 arcsec beam (natural weighting)  
  > "Using natural weighting results in $\sim$0.3$''$-0.5$''$ beam" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 2-4 mJy/beam per 0.16 km/s channel  
  > "with an rms of 2-4 mJy/beam per 0.16 km s$^{-1}$ wide channel" (2 Observations)
- time on source: 8-39 min per execution (Table 1)  
  > "DM Tau | 2017-07-05 | 32 min" (Table 1)
- observing dates: December 2016 to July 2017  
  > "Observations were taken between December 2016 and July 2017" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- External data: Gaia DR2 parallax distances  
  > "All distances are based on GAIA DR2 parallax measurements" (3 Models) [from (cite: gaia18; lin18)]
- External data: MWC 480 temperature structure (T_mid0=18.8 K) from 13CO  
  > "we use the temperature structure derived by (cite: pie07) based on observations of $^{13}$CO, which corresponds to $T_{\rm mid0}$=18.8 K" (3 Models) [from (cite: pie07)]
- External data: DM Tau CO freeze-out at 70 au (19 K) from chemical models  
  > "occurs at 70 au, as predicted by the chemical models of (cite: loo15)" (3 Models) [from (cite: loo15)]
- External data: Stellar masses, gas masses and CO abundances (Table 2)  
  > "References: (1) (cite: sim00), (2) (cite: and11), (3) (cite: mcc16)" (Table 2) [from (cite: sim00; and11; mcc16; ros12; ros13b)]

## Processing

### Calibration

- pipeline or manual: standard ALMA reduction scripts  
  > "The standard ALMA reduction scripts were used to produce calibrated visibilities." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: long baselines 1.06, 1.04, 0.93 times short baselines (DM Tau, MWC 480, V4046 Sgr); consistent with ALMA calibration uncertainty  
  > "We find that the long baseline observations are 1.06, 1.04, and 0.93 times brighter than the short baselines observations for DM Tau, MWC 480, and V4046 Sgr respectively" (2 Observations)
- self calibration: two rounds phase and one round amplitude, except no amplitude for short-baseline DM Tau  
  > "two rounds of phase self-calibration and one round of amplitude self-calibration was performed" (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Using natural weighting results in $\sim$0.3$''$-0.5$''$ beam" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: short and long baseline visibilities combined  
  > "Cleaned images were generated by combining the short and long baseline visibilities." (2 Observations)
- smoothing: spectra binned by factor of 2 (0.16 km/s)  
  > "The spectra were binned down by a factor of 2 (0.16 km s$^{-1}$)." (2 Observations)
- final beam: _not stated_
- final rms: 2-4 mJy/beam per channel  
  > "with an rms of 2-4 mJy/beam per 0.16 km s$^{-1}$ wide channel" (2 Observations)

### Inherited from earlier work

- Modeling code and methodology for turbulence  
  > "The modeling code used to derive the turbulence has been described previously in (cite: fla15), (cite: fla17), and (cite: fla18)" (3 Models) [from (cite: fla15), (cite: fla17), (cite: fla18); based on (cite: ros13), (cite: dar03)]
- Velocity field with height and pressure support corrections  
  > "with corrections for the height above the midplane and the pressure support of the gas, as in (cite: ros13)." (3 Models) [from (cite: ros13)]

### Not stated but needed to reproduce (our reading)

- CASA version used for the standard calibration and imaging
- Clean parameters (cell size, image size, masks, niter, threshold) for the images
- Which model visibilities/spectra were compared (how fit was done in uv-plane, binning of baselines)
- Source code of the modeling code (not released)
- Exact definition of the 99.7% interval and upper limit extraction
- Line-free channels used for noise estimate
- D'Alessio model T_mid0 for V4046 Sgr is a private communication
- Gas mass for MWC 480 is 'This work' without derivation

## Analysis recipe

1. **Align and rescale the two baseline datasets**: Compare continuum visibilities at <200 kλ to derive flux scale factors, fit elliptical Gaussian to continuum to derive positional offsets and apply phase shifts  
  > "we compare the continuum visibilities with baselines $<$200 k$\lambda$ among the two observational epochs." (2 Observations)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: Positions consistent with Gaia DR2 stellar positions  
  > "The observed locations of the disks are consistent with the stellar positions now available in the GAIA DR2 database" (2 Observations)
2. **Fit parametric CO disk models to visibilities**: Parametric disk with power-law/exponential surface density, vertical temperature gradient, hydrostatic equilibrium, Keplerian velocity, Gaussian line profile with non-thermal width proportional to sound speed; CO photodesorption layer for N_H2=1.3-4.8e21 cm-2 at T<20 K  
  > "The line profile is a Gaussian whose width is set by the thermal and non-thermal motions." (3 Models)
   - software: EMCEE
   - parameter: Free: T_atm0, q, R_c, i, δv_turb, R_in, v_sys; fixed PA, γ=1, T_mid0, Z_q0, masses  
  > "we allow $T_{\rm atm0}$, $q$, $R_c$, $i$, $\delta v_{\rm turb}$, and $R_{\rm in}$ to vary, along with the systemic velocity of the disk" (3 Models)
   - assumption: T_mid0 fixed from literature (DM Tau 19 K freeze-out at 70 au; MWC 480 18.8 K; V4046 Sgr 12 K); distances from Gaia DR2  
  > "For the disk around V4046 Sgr, we use a midplane normalization based on a D’Alessio model fitting of the SED, which results in $T_{\rm mid0}$=12 K" (3 Models)
   - fitting: emcee affine-invariant MCMC, 80 walkers, 800 steps, first 500 burn-in, uniform priors restricting to physical values, log(R_c) fitted; uncertainties from dispersion among baselines in line-free channels  
  > "Typical MCMC chains consist of 80 walkers and 800 steps, with convergence on the final solution occurring within 300 steps." (3 Models); "We assume uniform priors that simply restrict parameters to physically realistic values" (3 Models)
   - validation: Residual channel maps; sign of inclination chosen to minimize asymmetric residuals  
  > "The sign on the inclination is adjusted so as to minimize asymmetric residuals" (3 Models)
3. **Test significance and robustness of turbulence**: Rerun with turbulence fixed at zero and compare with AIC; fit unbinned spectra; scale model flux ±20%; lower T_mid0  
  > "Comparing the median models from both trials using the Akaike Information Criterion (cite: aka74) the difference is confirmed" (4.1 Non-zero turbulence around DM Tau)
   - software: EMCEE
   - parameter: flux scaling ±20%; T_mid0 = 11 K (DM Tau), 14 K (MWC 480), 8 K (V4046 Sgr)  
  > "we run additional trials in which the model is systematically scaled by $\pm$20%" (4.1 Non-zero turbulence around DM Tau)
   - fitting: _not stated_
   - validation: Zero-turbulence model systematically underestimates the DM Tau flux; for MWC 480 and V4046 Sgr it is nearly indistinguishable, so upper limits are given  
  > "For this reason we conservatively interpret the results for MWC 480 and V4046 Sgr as upper limits rather than detections." (4.2 Weak Turbulence around MWC 480 and V4046 Sgr)
4. **Test sensitivity to anisotropic/structured motion**: Toy model adding sinusoidal azimuthal velocity perturbation dv_phi = dv sin(2πR/dR) to DM Tau fiducial model, imaged with same procedure as data  
  > "we employ a toy model in which we add a velocity component in the orbital direction that varies as a function of radius" (4.1.1 Anisotropic vs Isotropic motion)
   - parameter: (dR, dv) = (150 au, 1.5 km/s), (70 au, 1.5 km/s), (150 au, 0.3 km/s)  
  > "(1) large spatial scale and high velocity ($dR$=150 au, $dv$=1.5 km s$^{-1}$)" (4.1.1 Anisotropic vs Isotropic motion)
   - fitting: _not stated_
   - validation: _not stated_
5. **Convert to alpha**: alpha ~ (δv_turb/c_s)^2  
  > "turbulent velocities from molecular line observations can be converted to $\alpha$ via $\alpha\sim$($\delta$v$_{\rm turb}$/c$_s$)$^2$" (5.1 Is weak turbulence common among planet-forming disks?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **EMCEE** : MCMC posterior estimation  
  > "The posterior distributions for each parameter are estimated using the MCMC routine EMCEE" (3 Models)
- **MIRIAD** : listed in Software section; specific use not stated  
  > "astropy (cite: astropy), EMCEE (cite: for13), MIRIAD" (Software)
- **astropy** : listed in Software section; specific use not stated  
  > "astropy (cite: astropy), EMCEE (cite: for13), MIRIAD" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DM Tau δv_turb (fiducial) | 0.279 | +0.005/-0.004 | c_s | 2 | 0.279$^{+0.005}_{-0.004}$c$_s$ |
| DM Tau δv_turb range including systematics | 0.25-0.33 | not stated | c_s | 3 | we find $\delta v_{\rm turb}=0.25-0.33$c$_s$ |
| DM Tau δv_turb, 20% faint disk | 0.300 | ±0.005 | c_s | 3 | $\delta v_{\rm turb}$=0.300$\pm$0.005c$_s$ for a faint disk |
| DM Tau δv_turb, low T_mid0=11 K | 0.328 | ±0.004 | c_s | 3 | $\delta v_{\rm turb}$=0.328$\pm$0.004c$_s$ |
| MWC 480 turbulence upper limit (unbinned) | <0.08 | not stated | c_s | 3 | Fitting to the un-binned data pushes the limit down to $<$0.08 c$_s$ |
| V4046 Sgr turbulence upper limit (unbinned) | <0.12 | not stated | c_s | 3 | pushes the upper limit down to $<$0.12c$_s$ |
| alpha DM Tau | 0.078 | ±0.002 | dimensionless | 5 | $\alpha$=0.078$\pm$0.002 for the disk around DM Tau |
| DM Tau inclination (fiducial) | 36.0 | +0.12/-0.09 | deg | 2 | 36.0$^{+0.12}_{-0.09}$ |

## Qualitative findings

- Models with zero turbulence systematically underestimate the DM Tau disk flux.  
  > "This results in a model that systematically underestimates the flux of the disk" (4.1 Non-zero turbulence around DM Tau)
- Structured motion from zonal flows or VSI at ~2H scales is hard to distinguish from isotropic turbulence at this resolution.  
  > "At these scales, zonal flows and VSI are difficult to distinguish from isotropic motion in our data" (4.1.1 Anisotropic vs Isotropic motion)

## Claim tuples

- H: Is there non-thermal motion in the DM Tau disk? | E: MCMC parametric fit of CO(2-1) with free vs zero turbulence plus systematic tests | R: δv_turb=0.279 c_s; 0.25-0.33 with systematics | F: Robust non-zero turbulence detected around DM Tau | **supported**
- H: Do MWC 480 and V4046 Sgr show turbulence? | E: Same fits with free and zero turbulence | R: <0.08 c_s and <0.12 c_s | F: Only stringent upper limits | **supported**
- H: Is weak turbulence common in planet-forming disks? | E: Compare with HD 163296, TW Hya and dust-based studies | R: Most gas-measured disks show upper limits | F: Weak turbulence (α≲1e-3) may be common but not universal | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Non-thermal term set proportional to local sound speed, motivated by simulations  
  > "This parameterization is physically motivated by numerical simulations that predict that the turbulence scales with the local sound speed" (3 Models)
- Alternative: Gravito-turbulence rejected for the sample since Toomre Q of 5-15  
  > "resulting in minimum Toomre Q values of 5-15, inconsistent with the presence of gravito-turbulence" (5.2 Physical conditions for turbulence)
- How they decided it was enough: _not stated_
- Limitation (authors): Systematic effects (midplane temperature, flux calibration) dominate over statistical uncertainties.  
  > "systematic uncertainties dominate over statistical uncertainties in our measurement of turbulence" (4.1 Non-zero turbulence around DM Tau)
- Limitation (authors): Unresolved central positive residuals and simple density/temperature prescriptions.  
  > "may be due to deviations from our simple prescriptions for density and temperature" (4.1 Non-zero turbulence around DM Tau)
- Caveat (inferred, ours): Result depends on assumed fixed midplane temperature and parametric structure
- Caveat (inferred, ours): Isotropic turbulence may be degenerate with unresolved structured motion
- Caveat (inferred, ours): Stellar masses fixed and not updated to newer values
- Caveat (inferred, ours): Derived alpha is only valid in the CO emitting layer

## Reproducibility

- Data public (paper): Project code and acknowledgement of ALMA data given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00724.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Modeling code (previous papers' code) not released
- Missing: CASA version and imaging parameters
- Missing: Details of baseline binning/likelihood in the uv-plane
- Missing: Private communication inputs
- Data volume (inferred): ~100-300 GB raw for six executions; a few GB after calibration
- Score (inferred): 3/5, Public data and clear model/MCMC description, but the custom modeling code and imaging details are unavailable.
- Rediscovery candidate: no, Requires unreleased custom modeling code and unstated settings, though results are numeric.

## Links

- Method: (cite: fla15), (cite: fla17), (cite: fla18) (Describe the modeling code and turbulence methodology)
- Method: (cite: ros13) (Basis of the disk model and velocity field)
- Companion: (cite: qi19) (N2H+ and dust settling comparison in DM Tau and V4046 Sgr)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 53,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
