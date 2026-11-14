# ALMA Observations of Asymmetric Molecular Gas Emission from a Protoplanetary Disk in the Orion Nebula

`2017AJ....153..233F` | The Astronomical Journal 2017 | first author: Factor, Samuel M. | arXiv: 1704.01970 | DOI: 10.3847/1538-3881/aa6c2c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the temperature, density, abundance structure and central stellar mass of the d216-0939 disk in the ONC, and what is the nature of an asymmetric high-velocity emission feature?  
  > "We model the spectrally resolved HCO$^+$ (4–3), CO (3–2), and HCN (4–3) lines observed at 0.5$''$ resolution to fit the temperature and density structure of the disk." (abstract)
- Target **d216-0939**: coordinates pointing center RA 5h35m21.5s, Dec -5d09m42.0s (J2000)  
  > "the J2000 pointing center of the observations is $\alpha$ = $5^\mathrm{h}35^\mathrm{m}21.5^\mathrm{s}$, $\delta$ = $-5^\circ09'42.0\ensuremath{''}$" (4.2 Fitting Procedure); "at 414 pc, the distance of Orion we chose to adopt in this work" (2 Observations); z/distance 414 pc  
  > "the J2000 pointing center of the observations is $\alpha$ = $5^\mathrm{h}35^\mathrm{m}21.5^\mathrm{s}$, $\delta$ = $-5^\circ09'42.0\ensuremath{''}$" (4.2 Fitting Procedure); "at 414 pc, the distance of Orion we chose to adopt in this work" (2 Observations); distance from most recent trigonometric parallax measurement of the Orion Nebula  
  > "the J2000 pointing center of the observations is $\alpha$ = $5^\mathrm{h}35^\mathrm{m}21.5^\mathrm{s}$, $\delta$ = $-5^\circ09'42.0\ensuremath{''}$" (4.2 Fitting Procedure); "at 414 pc, the distance of Orion we chose to adopt in this work" (2 Observations)

## Data provenance

- ALMA projects: 2011.0.00028.S
- bands: Band 7 (350 GHz, ~850 um)  
  > "The observations were made on October 24, 2012, using the Band 7 (350 GHz, $\sim850\,\mu$m) receivers." (2 Observations)
- frequencies and spectral setup: Four 1.875 GHz windows; 3840 channels of 488.28 kHz (0.42 km/s)  
  > "Each window was divided into 3840 channels of 488.28 kHz width, corresponding to a velocity resolution of 0.42 km s$^{-1}$." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 22 12-m antennas, Cycle 0  
  > "22 12-m antennas were online in a hybrid configuration with baselines ranging from 21.2 m to 384.2 m." (2 Observations)
- configurations: _not stated_
- baselines: 21.2 m to 384.2 m  
  > "baselines ranging from 21.2 m to 384.2 m" (2 Observations)
- angular resolution: 0.5 arcsec (190 au)  
  > "results in a largest recoverable scale of $8''$ and an angular resolution of 0.5$''$" (2 Observations)
- max recoverable scale: 8 arcsec (2.9 arcsec with baselines >70 klambda)  
  > "resulting in a largest recoverable scale of 2.9$''$ (1,200 au; see Section [3](#res) below for details)" (2 Observations)
- sensitivity: 0.41 mJy/beam continuum; 6 mJy/beam per channel  
  > "achieving an rms noise of 0.41 mJy beam$^{-1}$ in the aggregate continuum data and 6 mJy beam$^{-1}$ in each channel" (2 Observations)
- time on source: 22 minutes  
  > "represent 22 minutes of on-source time" (2 Observations)
- observing dates: October 24, 2012  
  > "The observations were made on October 24, 2012" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HCO+ 4-3 (356.734 GHz)
- Line: HCN 4-3 (354.505 GHz)
- Line: CO 3-2 (345.796 GHz)
- Line: CS 7-6 (342.883 GHz)
- External data: Continuum disk mass 0.0445 Msun used as fixed value/prior center  
  > "Log-normal prior on the disk mass was centered on previous continuum mass measurements $\mu= 0.0445\,\mathrm{M_\odot}$ (cite: MassiveOrion; ALMAOri)" (Table 3 notes) [from (cite: MassiveOrion; ALMAOri)]
- External data: Spectral type K5 and Teff 4400 K  
  > "We first use the spectral type of the star, K5 (cite: SpT), to estimate an effective temperature of 4400 K" (5.3 Dynamical Mass of a Pre-Main Sequence Star) [from (cite: SpT)]
- External data: Pre-main-sequence evolutionary tracks  
  > "Figure [12](#fig:isochrones) shows evolutionary tracks presented by (cite: GFisochrones)" (5.3 Dynamical Mass of a Pre-Main Sequence Star) [from (cite: GFisochrones)]
- External data: Molecular data (A_ul, B_0)  
  > "Values for $A_{u\ell}$ and $B_0$ were taken from molecular data made available by (cite: moldat)." (3 Results) [from (cite: moldat)]

## Processing

### Calibration

- pipeline or manual: Calibrated by ALMA staff with standard CASA procedures  
  > "Data was calibrated by ALMA staff using the standard procedures in the Common Astronomy Software Applications (cite: CASA) package." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (model of Butler 2012)  
  > "The absolute flux calibration was determined from observations of Callisto." (2 Observations)
- flux scale uncertainty: ~10%  
  > "Absolute flux calibration is estimated to be accurate to within $\sim10\%$ (cite: ALMAOri)." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: MIRIAD inversion/deconvolution/restoration; cvel and uvcontsub in CASA  
  > "Visibilities were then inverted with natural weighting, deconvolved, and restored using the standard procedures in the Multichannel Image Reconstruction Image Analysis and Display (cite: miriad) package." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Visibilities were then inverted with natural weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub in uv plane  
  > "continuum subtraction in the uv plane was performed using the CASA task `uvcontsub`" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.57x0.52 arcsec PA 88.8 deg (all baselines); 0.51x0.47 arcsec PA 89.5 deg (>70 klambda)  
  > "When excluding baselines shorter than $70\,k\lambda$, the synthesized beam was $0.51\ensuremath{''}\times0.47\ensuremath{''}$ with a position angle of 89.5$^\circ$." (2 Observations)
- final rms: 6 mJy/beam per channel  
  > "6 mJy beam$^{-1}$ in each channel" (2 Observations)

### Inherited from earlier work

- Data collection and continuum analysis  
  > "Data collection methods and analysis of the continuum results are presented in (cite: ALMAOri)." (2 Observations) [from (cite: ALMAOri)]
- Temperature structure parameterization  
  > "We adopt the parameterization of disk temperature structure from (cite: temp)" (4.1 Gas Disk Model) [from (cite: temp)]
- T_mid,150 and z_q,150 fixed to values from another disk  
  > "which are the best-fit values found in an analysis of a much closer and therefore higher-quality set of observations of a protoplanetary disk around a star with very similar mass (cite: weakTurb)" (4.2 Fitting Procedure) [from (cite: weakTurb)]
- CO freeze-out and photodissociation thresholds  
  > "The freeze-out temperature and column density values were adopted from an analysis of the HD 163296 disk by (cite: qi11)" (4.1 Gas Disk Model) [from (cite: qi11)]
- Ray-tracing code  
  > "we then use a ray tracing code originally written in IDL by (cite: IDL2; IDL3) and translated into Python by (cite: weakTurb)" (4.1 Gas Disk Model) [from (cite: IDL2; IDL3; weakTurb)]

### Not stated but needed to reproduce (our reading)

- Calibration script / CASA version used by ALMA staff
- Line-free channels for uvcontsub
- Number of MCMC walkers, steps and exact autocorrelation times
- MCMC likelihood form and noise treatment
- Model image grid size and Hanning smoothing details
- Details of imspec spectrum extraction region
- Model code is not released

## Analysis recipe

1. **Remove cloud contamination via uv cut**: Exclude baselines shorter than 70 klambda, chosen using HCO+ data  
  > "We found that excluding baselines shorter than $70\,k\lambda$ (corresponding to an angular scale of $\sim3''$) best minimized the intensity of the cloud contamination feature" (3 Results)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps, line fluxes and Gaussian visibility fits**: Integrate zeroth moment within 3 sigma with cgcurs; fit elliptical Gaussians with uvfit  
  > "Elliptical Gaussian fits to the visibilities were performed using the MIRIAD task `uvfit`." (3 Results)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate gas mass from HCO+ flux**: Optically thin LTE mass formula scaled by abundance  
  > "Assuming optically thin emission (consistent with the best-fit model presented in Section [4.1](#sec:gasmod)) and Local Thermodynamic Equilibrium (LTE)" (3 Results)
   - parameter: T_ex = 17 K  
  > "This calculation uses an excitation temperature of 17 K" (3 Results)
   - assumption: HCO+ abundance 1e-9  
  > "The mass calculation also assumes an HCO$^+$ fractional abundance of $10^{-9}$." (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Grid search for systemic velocity and position offset**: Grid search on HCO+ with nominal temperature/density, steps 0.01 km/s and 0.01 arcsec  
  > "The grid searches for systemic velocity and position offset had step sizes of 0.01 km s$^{-1}$ and 0.01$''$, respectively." (4.2 Fitting Procedure)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
5. **MCMC fit of disk model to each line**: Parametric LTE disk model ray-traced, Hanning smoothed, sampled with uvmodel, chi^2 in visibility domain; affine-invariant MCMC  
  > "We then fit the model of the disk temperature, density, and velocity to the data using a Markov Chain Monte Carlo (MCMC) algorithm with an affine invariant sampler." (4.2 Fitting Procedure)
   - software: emcee, corner.py, MIRIAD
   - parameter: Fixed: Rc 600 au, T_mid,150 17.5 K, z_q,150 70 au, gamma 1, v_turb 1% sound speed, d 414 pc  
  > "In all fits $d$ was fixed at 414 pc, $R_\mathrm{c}$ at 600 au, $T_\mathrm{mid,150}$ at 17.5 K, $z_{q,150}$ at 70 au" (Table 4 notes)
   - assumption: Mgas = Mdisk; 80% H2 by weight, mean molecular mass 2.37; constant abundance with freeze-out/photodissociation cuts  
  > "We also assume a molecular gas composition that is 80% molecular hydrogen by weight with a mean molecular mass of 2.37." (4.1 Gas Disk Model)
   - fitting: emcee; priors per Table 3 (log-uniform, uniform, log-normal on mass); burn-in >=3 autocorrelation times  
  > "We exclude the first $\gtrsim3$ autocorrelation times for burn-in and use at least 3 more in our statistical analysis." (4.2 Fitting Procedure)
   - validation: Residual channel maps; HCN fit with/without short baselines consistent within 1 sigma  
  > "A test that involved fitting HCN with and without baselines shorter than 70 k$\lambda$ resulted in outer radii, and all other parameters, that were consistent to within $<1\sigma$." (4.2 Fitting Procedure)
6. **Test LTE assumption with non-LTE model**: Compare best-fit LTE model images to LIME models for HCO+ and HCN  
  > "We therefore investigated the differences between our LTE model and a non-LTE model using LIME (cite: LIME)." (4.3 Evaluation of the LTE Assumption)
   - software: LIME, MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
7. **Characterize high-velocity feature**: Gaussian fit to residual spectrum (imspec) and residual visibilities; compare to Keplerian velocity; mass from integrated flux via cgcurs  
  > "To measure the velocity of the feature relative to the star, we fit a Gaussian to the spectrum generated (using the MIRIAD task `imspec`) from the residual emission." (5.4 High Velocity Asymmetry)
   - software: MIRIAD
   - assumption: Optically thin HCO+ emission  
  > "Finally, we estimated a gas mass of the feature assuming optically thin HCO$^+$ (4–3) emission." (5.4 High Velocity Asymmetry)
   - fitting: _not stated_
   - validation: Predicted Keplerian velocity -5.3+-1.0 km/s agrees with measured -6.0 km/s  
  > "the predicted line of sight velocity of an object in Keplerian orbit at the measured positional offset is $-5.3\pm1.0$ km s$^{-1}$, which agrees well with the measured velocity of the feature" (5.4 High Velocity Asymmetry)

## Software

- **CASA** : Calibration by ALMA staff; cvel and uvcontsub  
  > "The velocity reference frame was converted from the ALMA standard topocentric to LSRK (kinematical local standard-of-rest) using the CASA task `cvel`" (2 Observations)
- **MIRIAD** : Imaging, cgcurs, uvfit, uvmodel, imspec  
  > "deconvolved, and restored using the standard procedures in the Multichannel Image Reconstruction Image Analysis and Display (cite: miriad) package" (2 Observations)
- **emcee** : Affine-invariant MCMC  
  > "We used the open source `emcee` software package, written by (cite: emcee)." (4.2 Fitting Procedure)
- **corner.py** : Posterior corner plots  
  > "made with the associated open source python package `corner.py` (cite: corner)" (4.2 Fitting Procedure)
- **LIME** : Non-LTE comparison  
  > "using LIME (cite: LIME)" (4.3 Evaluation of the LTE Assumption)
- **Astropy** : Named in acknowledgments and software list  
  > "*Software:* CASA (cite: CASA), MIRIAD (cite: miriad), LIME (cite: LIME), emcee (cite: emcee), corner.py (cite: corner), Astropy (cite: astropy)" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dynamical stellar mass | 2.17 | 0.07 | Msun | 5 | We dynamically measure the mass of the central star to be $2.17\pm0.07\,M_\ensuremath{\odot}$ |
| HCO+ integrated flux (all baselines) | 1.8 | 0.1 | Jy km/s | 2 | / HCO$^+$ (4–3) / All / $1.8\pm0.1$ / |
| HCN integrated flux | 0.84 | 0.03 | Jy km/s | 2 | / HCN (4–3) / All / $0.84\pm0.03$ / |
| Disk mass from HCO+ flux | 0.013 | 0.001 | Msun | 3 | we calculate a total disk mass of $0.013\pm0.001$ $M_\odot$ ($14\pm1\,M_\mathrm{Jupiter}$) |
| HCO+ log abundance | -10.07 | +0.20/-0.03 | dimensionless | 5 | $-10.07_{-0.03}^{+0.20}$ |
| HCN log abundance | -6.7 | +0.6/-0.4 | dimensionless | 5 | our best fit fractional abundance of $10^{-6.7_{-0.4}^{+0.6}}$ |
| CO atmospheric temperature at 150 au | 80 | +20/-10 | K | 5 | The best-fit atmospheric temperature for the CO line ($80^{+20}_{-10}$ K) |
| Systemic velocity (HCO+) | 10.7 | 0.1 | km/s | 4 | These fits yielded a systemic velocity of $10.7\pm0.1$ km s$^{-1}$ |
| Feature deprojected orbital radius | 57 | 22 | au | 7 | this corresponds to a deprojected orbital radius of $57\pm22$ au |
| Feature integrated flux (HCO+) | 28 | 10 | mJy km/s | 7 | We determined the integrated flux in the line, $28\pm10$ mJy km s$^{-1}$ |
| Feature gas mass (thermal broadening temperature) | 8 | 4 | M_Jupiter | 7 | results in a mass of $8\pm4\,M_\mathrm{Jupiter}$ |
| HCN/HCO+ peak flux ratio | 0.58 | 0.04 | dimensionless | 2 | We measure the ratio of HCN/HCO$^+$ peak flux in the d216-0939 disk to be $0.58\pm0.04$ |

## Qualitative findings

- CO fit gives q consistent with literature, HCO+ gives slightly positive q attributed to freeze-out surface  
  > "The slightly positive value of $q$ derived for HCO$^+$ is most likely due to the effect of observing an optically thin line of a molecule that freezes out in the midplane." (5.1 Best Fit Temperature and Abundance Structure)

## Claim tuples

- H: Does the dynamical stellar mass agree with the K5 spectral type? | E: Keplerian disk model MCMC fits to HCO+, CO, HCN | R: M* = 2.17+-0.07 Msun versus ~1 Msun expected | F: Inconsistent with K5; possible extinction/radiative transfer effects or a tight binary | **supported**
- H: Are molecular abundances consistent with chemical models? | E: Fit abundance in optically thin HCO+ and HCN lines with fixed continuum mass | R: HCO+ log X = -10.07; HCN log X = -6.7 | F: HCO+ roughly consistent; HCN higher than predicted, not fully explained by non-LTE | **partially**
- H: Is the high-velocity blue-shifted feature a Keplerian local enhancement? | E: Gaussian fits to residual spectrum and visibilities after subtracting symmetric model | R: Offset 0.11 arcsec, velocity -6.0 km/s, Keplerian prediction -5.3+-1.0 km/s; mass 1.8-8 MJ | F: Local temperature/density enhancement, vortex or protoplanet envelope; cannot distinguish | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: LTE chosen for computational efficiency enabling MCMC  
  > "The computational efficiency of the LTE assumption enables the use of the Markov Chain Monte Carlo (MCMC) technique" (4.1 Gas Disk Model)
- Alternative: Simultaneous fit of all three lines failed to give insignificant residuals  
  > "We attempted to fit all three lines simultaneously but were unable to identify a model with insignificant residuals." (4.2 Fitting Procedure)
- Alternative: Jet/outflow origin for feature rejected  
  > "Such features would be expected to occur at a position angle corresponding to the minor axis of the disk (83$^\circ$), which is inconsistent with the observed position angle of the feature" (5.4 High Velocity Asymmetry)
- How they decided it was enough: _not stated_
- Limitation (authors): HCN LTE model significantly fainter than LIME model; vertical structure unresolved  
  > "for HCN (4–3) our LTE model is significantly fainter than the LIME model throughout the entire line." (4.3 Evaluation of the LTE Assumption)
- Limitation (authors): CO heavily contaminated by cloud, blue side excluded  
  > "we excluded the entire blue-shifted side of the line as well as the contaminated channels near the systemic velocity" (4.2.2 CO (3–2) Fit)
- Caveat (inferred, ours): Lines fitted separately with many parameters fixed from other disks, so temperature/abundance uncertainties are underestimated
- Caveat (inferred, ours): Uncertainty in the stellar mass depends on fixed inclination/geometry assumptions and on excluded channels
- Caveat (inferred, ours): Feature mass depends strongly on HCO+ abundance and assumed temperature
- Caveat (inferred, ours): Single short observation limits feature characterization

## Reproducibility

- Data public (paper): ALMA data from project 2011.0.00028.S acknowledged  
  > "This work makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00028.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom ray-tracing model code (IDL/Python) is not released
- Missing: MCMC settings (walkers, steps, likelihood)
- Missing: Line-free channels for continuum subtraction
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Public Cycle 0 data and well described model, but custom code and several fit settings are not given.
- Rediscovery candidate: no, Recipe relies on a non-public custom ray-tracing code and MIRIAD workflow with missing settings.

## Links

- Method: (cite: ALMAOri) Mann et al. 2014 (Data collection and continuum analysis of the same observations)
- Method: (cite: weakTurb) Flaherty et al. 2015 (Python translation of ray-tracing code and fixed temperature values)
- Method: (cite: temp) Dartois et al. 2003 (Temperature structure parameterization)
- Companion: (cite: MassiveOrion) Mann & Williams 2009a (Previous SMA continuum and CO observations of d216-0939)
- Related: ALMA survey of Orion proplyds (2011.0.00028.S)

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 58,
  "rate": 0.652
 },
 "evidence_ok": true
}
```
