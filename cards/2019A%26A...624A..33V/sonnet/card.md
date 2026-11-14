# ALMA study of the HD 100453 AB system and the tidal interaction of the companion with the disk

`2019A&A...624A..33V` | Astronomy and Astrophysics 2019 | first author: van der Plas, G. | arXiv: 1902.00720 | DOI: 10.1051/0004-6361/201834134

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Resolve the dust and gas distribution in the HD 100453 A disk and quantify the interaction of HD 100453 B with the circumprimary disk  
  > "To resolve the dust and gas distribution in the disk around HD 100453 A and to quantify the interaction of HD 100453 B with the circumprimary disk." (abstract)
- Target **HD 100453 AB**: coordinates _not stated_; z/distance 103 pc  
  > "**HD 100453 A** at 103$^{+3}_{-4}$ pc (cite: 2016A&A...595A...1G) is an A9Ve star with an age of 10$\pm$2 Myr and a mass of 1.7 M$_\odot$" (Introduction); distance from Gaia Collaboration 2016  
  > "**HD 100453 A** at 103$^{+3}_{-4}$ pc (cite: 2016A&A...595A...1G) is an A9Ve star with an age of 10$\pm$2 Myr and a mass of 1.7 M$_\odot$" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00192.S
- bands: Band 6 (1.4 mm)  
  > "Using ALMA band 6 dust continuum and CO isotopologue observations" (abstract)
- frequencies and spectral setup: Two TDM continuum windows at 234.16 and 216.98 GHz (128 channels, 1.875 GHz); two FDM windows for 12CO, 13CO, C18O J=2-1 at 61, 122, 122 kHz resolution  
  > "These two TDM spectral windows were centered at 234.16 GHz and 216.98 GHz." (2 Observations); "with a spectral resolution of 61 kHz, 122 kHz, and 122 kHz respectively" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: Compact and extended configurations (Cycle 3)  
  > "ALMA Early Science Cycle 3 observations were conducted in a compact configuration" (2 Observations)
- configurations: _not stated_
- baselines: 15-463 m (compact) and 15-2483 m (extended)  
  > "The array configuration provided baselines ranging between respectively 15 and 463 meters, and between 15 and 2483 meters." (2 Observations)
- angular resolution: 0.17'' x 0.09'' (superuniform), 0.23'' x 0.15'' (Briggs); CO natural 0.29'' x 0.23''  
  > "respectively 0.23$''$ $\times$ 0.15$''$ at PA = 25.1 degrees (Briggs) and 0.17$''$ $\times$ 0.09$''$ at PA = 14.1 degrees (superuniform)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.05 mJy/beam (superuniform), 0.04 mJy/beam (Briggs)  
  > "resulting in a final RMS of 0.05 mJy/beam (peak SNR ratio of 159) for the images created using superuniform weighting" (2 Observations)
- time on source: 13.1 min (compact) and 26.2 min (extended)  
  > "with 13.1 minutes of total time on-source and in an extended configuration on September 8$^{\mathrm{th}}$ 2016 with 26.2 minutes of total time on-source" (2 Observations)
- observing dates: 2016 Apr 23 and 2016 Sep 08  
  > "| 2016 Apr 23 | 42       | 15 to 463      | 1.64   | J1107-4449 | J1107-4449 | J1132-5606 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **SPHERE (scattered light, Benisty et al. 2017)**: Scattered light image compared with ALMA residuals  
  > "We show these residuals together with the SPHERE image published in (cite: 2017A&A...597A..42B)" (3.1.2)
- External data: Astrometry of HD 100453 B used for orbit fitting  
  > "The orbital fit we performed uses the observed astrometry measurements given in (cite: 2018ApJ...854..130W)" (4.3 Orbital fitting) [from Wagner et al. 2018 (cite: 2018ApJ...854..130W)]
- External data: Grid of disk models for gas mass from CO isotopologue ratio  
  > "We use the grid of disk models calculated by (cite: 2014ApJ...788...59W) to estimate a total gas mass" (3.2.1) [from Williams & Best 2014 (cite: 2014ApJ...788...59W)]
- Simulation/model as data: PHANTOM SPH simulation of coplanar companion (7.5e5 gas, 2.5e5 dust particles) post-processed with MCFOST  
  > "using $7.5\times10^5$ SPH particles for the gas and $2.5\times10^5$ for the dust and setting the initial dust-to-gas mass ratio to 1%" (4.1 SPH Simulations)

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were calibrated and combined using the *Common Astronomy Software Applications* pipeline (cite: 2007ASPC..376..127M)." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-4449  
  > "| 2016 Sep 08 | 36       | 15 to 2483     | 0.56   | J1107-4449 | J1107-4449 | J1132-5606 |" (Table 1)
- flux scale uncertainty: ~20%; compact data scaled to extended (16% difference)  
  > "We estimate the absolute flux calibration to be accurate within $\sim$20%" (2 Observations)
- self calibration: Two rounds of phase-only self-calibration on continuum, applied to CO  
  > "we performed two rounds of phase only self-calibration" (2 Observations)

### Imaging

- task: CLEAN in CASA  
  > "We imaged the continuum visibilities with the CLEAN task in CASA" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs and superuniform (continuum); natural (CO); robust value not given  
  > "using Briggs and superuniform weightings" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "subtracted the continuum emission using the CASA task *uvcontsub*" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.23''x0.15'' (Briggs), 0.17''x0.09'' (superuniform), CO 0.29''x0.23''  
  > "which results in a restored beam of 0.29$''$ $\times$ 0.23$''$" (2 Observations)
- final rms: 0.04-0.05 mJy/beam continuum; 3.0 mJy/beam per 0.2 km/s channel for 12CO  
  > "| $^{12}$CO J = 2-1 | 2.34 | 0.06 | 200 | 3.0 | 1.10 | 49 $\pm$ 5 |" (Table 3)

### Inherited from earlier work

- SPH binary orbit and disk parameters  
  > "We adopt for our simulations the same parameters for the binary orbit and for the disk as in (cite: 2016ApJ...816L..12D)." (4.1 SPH Simulations) [from Dong et al. 2016 (cite: 2016ApJ...816L..12D)]
- CO velocity-field fitting methodology  
  > "we fit the observed velocity field of the CO gas using the methodology introduced in (cite: 2015ApJ...798...85P)" (4.2) [from Perez et al. 2015 (cite: 2015ApJ...798...85P)]
- MCFOST radial decomposition for dust temperature  
  > "as was previously done for HL Tau by (cite: 2016ApJ...816...25P)" (3.1.3) [from Pinte et al. 2016 (cite: 2016ApJ...816...25P)]
- Orbit fitting methods (LSLM and MCMC) and priors  
  > "We used two complementary fitting methods, as described in (cite: 2012A&A...542A..41C)" (4.3) [from Chauvin et al. 2012 (cite: 2012A&A...542A..41C)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, clean thresholds, masks, cell and image size
- Line-free channels for uvcontsub
- Self-calibration solution intervals
- uvmultifit starting values and model component definitions
- Details of the MCFOST disk model for temperature and SPH post-processing
- MCMC chain lengths and burn-in
- Moment map clipping thresholds details

## Analysis recipe

1. **Calibrate, self-calibrate and image continuum and CO**: CASA pipeline calibration, flux scaling of compact to extended, two rounds phase self-cal, CLEAN, uvcontsub, moment maps  
  > "we decide to scale the flux of the compact array configuration to match the extended array configuration data" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum visibilities for disk geometry**: Add components (uniform disk, ring, Gaussian, point source) progressively until residuals show no structure; fit each window separately  
  > "we start by fitting the most obvious component (i.e., a uniform disk) to the visibilities after which we progressively add components to the model based on the imaged residuals" (3.1.1)
   - software: uvmultifit
   - fitting: _not stated_
   - validation: Residual imaging; order of components does not affect result  
  > "The order in which these components are added does not influence the final fitting results." (3.1.1)
3. **Derive dust masses**: Optically thin single-temperature; temperature from MCFOST radial decomposition; limit for companion from 3 sigma  
  > "To convert the measured continuum emission into a dust mass we assume that the emission is optically thin and of a single temperature" (3.1.3)
   - software: MCFOST
   - assumption: kappa = 2.31 cm2/g at 1.28 mm, astronomical silicate, sizes 0.1-3000 micron, slope -3.5; d=103 pc; Tdust 27 K (disk), 22 K (companion)  
  > "We adopt a dust opacity of 2.31 $cm^{2}~g^{-1}$ at 1.28 mm" (3.1.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate CO optical depth and gas mass**: Isothermal slab line ratios; gas mass from Williams & Best grid  
  > "We make an estimate of the optical depths for each isotopologue from the detected line ratios under the assumption that the emission comes from an isothermal slab" (3.2)
   - assumption: 12CO/13CO 76, 16O/18O 500 ratios; 13CO/C18O ratio 550 or 1650 for grid  
  > "We adopt a to ratio of 76 (cite: 2008A&A...477..865S) and a to C ratio of 500 (cite: 1994ARA&A..32..191W)" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **SPH simulation of coplanar companion**: PHANTOM gas+dust, 10 binary orbits, MCFOST synthetic images convolved with beam  
  > "We run the simulation for 10 orbits of the binary, at which time the disk has reached a quasi-steady state." (4.1)
   - software: PHANTOM, MCFOST
   - parameter: MA=1.7, MB=0.3 Msun, a=120 au, circular, rin=12, rout=96 au, Md=0.003 Msun, H/r=0.05, alpha_SS=5e-3, grain 1 mm  
  > "are separated by $a=120$ au on a circular orbit, co-planar with the disk" (4.1)
   - fitting: _not stated_
   - validation: Qualitative comparison with observed maps  
  > "We show the simulated 1.4 mm continuum map, the integrated CO intensity, and the CO velocity field, together with the observed maps" (4.1)
6. **Fit CO velocity field with warp**: Parametric 12CO model; iterative chi2 grid search on inclination and PA of inner and outer disk in 0.5 deg steps, comparing moment 1 maps  
  > "First, we performed a simple $\chi^2$ search using 0.5 degrees steps" (4.2)
   - parameter: outer disk starts at 38 au; H/r=0.05; gamma=1; Rc=10 au; pixels with moment 0 above 5 sigma  
  > "The comparison is done only in the pixels where the observed signal in the zeroth moment is above $5\sigma$." (4.2)
   - fitting: chi2 grid search, no sampler  
  > "First, we performed a simple $\chi^2$ search using 0.5 degrees steps around $\{i_{\rm out}, {\rm PA}_{\rm out}\} = {25, 140}$." (4.2 Quantifying the disk warp)
   - validation: Comparison with purely Keplerian model residuals  
  > "A mildly warped disk (represented here by an inner region with different PA and inclination) yields, as expected, a better fit to the data than the purely Keplerian model." (4.2)
7. **Fit orbit of HD 100453 B and relative inclination**: LSLM and MCMC on Wagner et al. astrometry; relative inclination computed with disk i and PA  
  > "(i) a least squares Levenberg-Marquardt (LSLM) algorithm to search for the model with the minimal reduced $\chi^2$" (4.3)
   - parameter: d=103 pc, total mass 1.9 Msun; ten chains; 500,000 orbits sampled  
  > "The system distance and total mass used for the fitting are 103 pc and 1.9 M$_\odot$." (4.3)
   - fitting: MCMC with Gelman-Rubin convergence, priors uniform in (ln P, e, cos i, Omega+omega, omega-Omega, tp)  
  > "We chose the priors to be uniform in x = $(\ln P,e,\cos i,\Omega+\omega,\omega-\Omega,t_p)$ following (cite: 2006ApJ...642..505F)." (4.3)
   - validation: Reduced chi2 between 0.5 and 2  
  > "we obtain a consistent fit to the orbit with $\chi _r ^2$ values between 0.5 and 2" (4.3)

## Software

- **CASA** : Calibration, CLEAN imaging, uvcontsub  
  > "We imaged the continuum visibilities with the CLEAN task in CASA" (2 Observations)
- **uvmultifit** : Fitting disk components to visibilities  
  > "We use the fitting library *uvmultifit* (cite: 2014A&A...563A.136M)" (3.1.1)
- **MCFOST** : Dust temperature, synthetic images from SPH  
  > "we use the radiative transfer code MCFOST to convert the results of our simulation into images" (4.1)
- **PHANTOM** : SPH simulations  
  > "Smoothed Particle Hydrodynamics (SPH) code PHANTOM" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inclination (continuum) | 29.5 | 0.5 | deg | 2 | inclined by 29.5 $\pm$ 0.5$^\circ$ with a position angle of 151.0 $\pm$ 0.5$^\circ$ |
| Disk PA (continuum) | 151.0 | 0.5 | deg | 2 | inclined by 29.5 $\pm$ 0.5$^\circ$ with a position angle of 151.0 $\pm$ 0.5$^\circ$ |
| Uniform disk radial extent | 0.22-0.40 | 0.01 | arcsec | 2 | 0.22 (0.01), 0.40 (0.01)$^{\mathrm{b}}$ |
| Gaussian (northern arm) flux at 234 GHz | 8.7 | 0.3 | mJy | 2 | / Gaussian / 0.09$^{\mathrm{c}}$ / 0.20$^{\mathrm{c}}$ / 8.7 (0.3) / 3.6 (0.6) / 0.19 (0.01) / 52.2 (5.0) / 104.7 (3.0) / |
| Total flux, all components | 149.2 | 3.0 | mJy | 2 | the combined flux of all components is 149.2 $\pm$ 3.0 mJy |
| Disk spectral index | 2.4 | 0.1 | dimensionless | 2 | The spectral index for the disk component is 2.4 $\pm$ 0.1 |
| Dust disk mass | 0.09 | not stated | M_Jup | 3 | which translates in a dust disk mass of 0.09 M$_{\mathrm{jup}}$ |
| Dust upper limit around HD 100453 B | 0.03 | 3 sigma limit | M_Earth | 3 | This puts an upper limit of 0.03 M$_{Earth}$ on the amount of dust around HD 100453 B. |
| 12CO outer radius | 1.10 | not stated | arcsec | 1 | The outer radius as measured from emission above 3$\sigma$ in the moment maps is 1.10$''$. |
| Line fluxes 12CO, 13CO, C18O | 2.34, 0.90, 0.39 | 0.06, 0.03, 0.02 | Jy km/s | 1 | / $^{13}$CO J = 2-1 / 0.90 / 0.03 / 200 / 3.0 / 0.70 / 31 $\pm$ 5 / |
| Systemic velocity | 5.25 | 0.10 | km/s | 1 | v$_{LSR}$ = 5.25 $\pm$ 0.10 km s$^{-1}$ |
| Gas-to-dust ratio | 15 to 45 | not stated | dimensionless | 4 | we arrive at a gas to dust ratio of 15 to 45 |
| Warp best-fit outer disk (i, PA) | 19.5, 139.5 | not stated | deg | 6 | $\{i_{\rm out}, {\rm PA}_{\rm out}\} = \{19.5, 139.5\}$ |
| Warp best-fit inner disk (i, PA) | 24.0, 146.0 | not stated | deg | 6 | $\{i_{\rm in}, {\rm PA}_{\rm in}\} = \{24.0, 146.0\}$ |
| Most likely relative inclination of orbit | 60 | not stated | deg | 7 | a co-planar orbit is not favoured with a most likely relative inclination of 60$^\circ$ |

## Qualitative findings

- Excess mm emission is cospatial with the northern scattered-light spiral arm  
  > "excess mm emission cospatial with the northern spiral arm which was previously detected using scattered light observations" (abstract)

## Claim tuples

- H: Is a coplanar orbit of HD 100453 B consistent with the disk observations? | E: Compared ALMA continuum and CO with PHANTOM SPH simulations and orbit fitting | R: CO extends to 1.10'', mm emission at northern arm, relative inclination peaks near 60 deg | F: Orbit is likely significantly misaligned; coplanar orbit disfavoured | **supported**
- H: Does the outer CO disk show a warp from the companion? | E: Moment 1 fitting with inclination and PA of inner and outer disk | R: Outer CO i and PA differ by up to 10 deg from continuum | F: Interpreted as gravitational interaction with HD 100453 B | **partially**
- H: Could an undetected inner companion explain the spirals? | E: Discussion of precessing shadows and cavity size | R: Qualitative consistency, no direct test | F: Proposed as alternative scenario | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational instability and recent fly-by deemed unlikely for the spirals  
  > "A gravitationally unstable disk is unlikely to be the cause for the detected spiral arms." (5.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Unclear whether mm excess is spiral counterpart or vortex; higher resolution needed  
  > "Future higher resolution observations are needed to disentangle the nature of the excess mm emission." (3.1.2)
- Caveat (inferred, ours): Warp chi2 defined without squaring and with no uncertainties
- Caveat (inferred, ours): Orbit fit covers small orbital fraction; relative inclination poorly constrained
- Caveat (inferred, ours): SPH uses 0.3 Msun companion and coplanar orbit only; misaligned orbit not simulated
- Caveat (inferred, ours): Flux scaling between configurations is ad hoc

## Reproducibility

- Data public (paper): ALMA programme 2015.1.00192.S acknowledged  
  > "This paper makes use of data from ALMA programme 2015.1.00192.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging and self-calibration parameters
- Missing: Warp model and MCFOST model details
- Missing: MCMC settings
- Data volume (inferred): ~20-50 GB raw, two EBs
- Score (inferred): 3/5, Data public and main numbers given, but many imaging and model details are missing.
- Rediscovery candidate: no, Recipe incomplete and relies on simulations and external model grids.

## Links

- Method: Martí-Vidal et al. 2014 (cite: 2014A&A...563A.136M) (uvmultifit visibility fitting)
- Method: Perez et al. 2015 (cite: 2015ApJ...798...85P) (CO velocity-field fitting method)
- Companion: Wagner et al. 2018 (cite: 2018ApJ...854..130W) (Used part of the same ALMA data and provided astrometry)

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 54,
  "rate": 0.643
 },
 "evidence_ok": true
}
```
