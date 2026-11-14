# Highly structured disk around the planet host PDS 70 revealed by high-angular resolution observations with ALMA

`2019A&A...625A.118K` | Astronomy and Astrophysics 2019 | first author: Keppler, M. | arXiv: 1902.07639 | DOI: 10.1051/0004-6361/201935034

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: What direct and indirect imprints does the planet PDS 70 b leave on the gas and dust of its circumstellar disk, and what limits can be placed on circumplanetary material?  
  > "We aim to trace direct and indirect imprints of PDS 70 b on the gas and dust emission of the circumstellar disk" (abstract)
- Target **PDS 70**: coordinates _not stated_; z/distance 113.4±0.5 pc  
  > "113.4$\pm$0.5 pc distant (cite: gaia16; gaia18) T Tauri star PDS 70" (Introduction); distance from Gaia (gaia16; gaia18)  
  > "113.4$\pm$0.5 pc distant (cite: gaia16; gaia18) T Tauri star PDS 70" (Introduction)

## Data provenance

- ALMA projects: 2017.A.00006.S, 2015.1.00888.S
- bands: Band 7  
  > "of PDS 70 in band 7 on 2, 3 and 6 December 2017" (2 Observations and data reduction)
- frequencies and spectral setup: 3 continuum SPWs at 357.2, 355.3, 344.3 GHz (2.0 GHz each); 12CO(3-2) SPW at 345.8 GHz, 0.938 GHz bandwidth  
  > "The fourth spectral window was centered around the $^{12}$CO(3-2) transition at 345.8 GHz with a bandwidth of 0.938 GHz." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: continuum 74×57 mas; CO 76×61 mas  
  > "is $74\times57$ mas (8.4$\times$6.5 au) with a position angle ($PA$) of 63$^{\mathrm{o}}$." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.026 mJy/beam; CO 1.26 mJy/beam per channel  
  > "We measured an rms noise level of 0.026 $\ \rm mJy\ beam^{-1}\ $from emission-free regions." (2 Observations and data reduction)
- time on source: 1.9 hours (Cycle 5)  
  > "The total on-source integration time was 1.9 hours." (2 Observations and data reduction)
- observing dates: 2, 3 and 6 December 2017 (Cycle 5 DDT)  
  > "on 2, 3 and 6 December 2017 under very good weather conditions" (2 Observations and data reduction)
- pi or archival as stated: New Cycle 5 DDT data (PI Keppler) combined with archival Cycle 3 data of Long18  
  > "we made use of the archival Cycle 3 data taken in a similar spectral setup and presented by (cite: Long18)" (2 Observations and data reduction)
- Line: 12CO J=3-2 (345.8 GHz)
- Other facility **VLT/SPHERE**: Discovery of PDS 70 b and NIR scattered light (earlier work)  
  > "we recently discovered a companion to the 5.4$\pm$1.0 Myr old" (Introduction)
- External data: Planet luminosity L_p ~1.5e-4 Lsun  
  > "where we used $L_{p}\sim$1.5$\times10^{-4} L_{\odot}$ as the luminosity of PDS 70 b (cite: mueller2018)" (3.1.4 Upper limits on CPD dust mass) [from (cite: mueller2018)]
- External data: Accretion rate ~1e-8 MJup/yr  
  > "Following (cite: Wagner2018), we assumed $\dot{M}_{acc}\,\sim\,10^{-8}\,\rm M_{\rm Jup}\,\rm yr^{-1}$" (3.1.4 Upper limits on CPD dust mass) [from (cite: Wagner2018)]
- External data: Dust opacity 3.5 cm2/g at 855 um, scaled from Andrews+12  
  > "which we assumed to be 3.5 $\rm cm^2 g^{-1}$ at 855 $\rm \mu m$, linearly scaled from (cite: Andrews+12)" (3.1.4 Upper limits on CPD dust mass) [from (cite: Andrews+12)]
- Simulation/model as data: FARGO3D hydrodynamic simulations with 2, 5, 10 MJup planets, post-processed with RADMC3D and simobserve  
  > "We tested three planet masses: 2, 5, and 10 $\rm M_{Jup}$" (4.1 Model setup)

## Processing

### Calibration

- pipeline or manual: CASA calibration  
  > "The calibration was performed using the Common Astronomy Software Package (CASA), version 5.1.1." (2 Observations and data reduction)
- casa version: 5.1.1 calibration; 5.3.0 for later processing  
  > "We transferred both Cycle 3 and Cycle 5 data to `CASA v.5.3.0`" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206, J1337-1257, J1517-2422 used as bandpass, phase, flux calibrators  
  > "The quasars J1427-4206, J1337-1257, and J1517-2422 were used as bandpass, phase, and flux calibrators." (2 Observations and data reduction)
- flux scale uncertainty: ~10% absolute amplitude calibration  
  > "dominated by the $\sim$10$\%$ uncertainty of the absolute amplitude calibration of ALMA in Band 7" (3.1 855 um dust continuum)
- self calibration: Tried, no significant improvement; not used  
  > "Because self-calibration of both continuum and CO data did not significantly improve the images, we will base our analysis on the non-self-calibrated data." (2 Observations and data reduction)

### Imaging

- task: TCLEAN  
  > "We finally used the task `TCLEAN` for imaging, applying Briggs weighting with a robust parameter of 0.5." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "applying Briggs weighting with a robust parameter of 0.5" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB on line data  
  > "subtracted the continuum emission from the line data using the task `UVCONTSUB`" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 3 and Cycle 5 data combined after proper-motion phase-center correction and shift by (0.509'', 0.490'')  
  > "We then combined the two data sets and shifted the phase center by an amount of (0.509$''$, 0.490$''$)" (2 Observations and data reduction)
- smoothing: _not stated_
- final beam: continuum 74×57 mas PA 63°; CO 76×61 mas PA 60°, 425 m/s channels  
  > "we obtained a beam size of $76\times61$ mas (8.6$\times$6.9 au) with a $PA$ of $60^{\mathrm{o}}$ and a channel width of 425 m/s." (2 Observations and data reduction)
- final rms: 0.026 mJy/beam continuum; 1.26 mJy/beam per channel CO  
  > "The noise level per channel is determined to be 1.26 $\ \rm mJy\ beam^{-1}\ $." (2 Observations and data reduction)

### Inherited from earlier work

- Cycle 3 observing strategy and setup  
  > "Details regarding the observing strategy and setup are described in (cite: Long18)." (2 Observations and data reduction) [from (cite: Long18)]
- Ring fitting approach with deprojected visibilities  
  > "we used the same approach as (cite: 2018ApJ...859...32P)" (3.1.1 Disk radial and azimuthal morphology) [from (cite: 2018ApJ...859...32P)]
- CPD temperature and flux model  
  > "we followed the approach presented by (cite: Isella+14)" (3.1.4 Upper limits on CPD dust mass) [from (cite: Isella+14)]
- Rotation curve and emission surface methods  
  > "Following the method described in (cite: Teague+2018b), we inferred the rotation profile" (3.2.2 12CO rotation curve) [from (cite: Teague+2018b)]
- Disk density, aspect ratio and dust model for hydro/RT  
  > "We adopted the disk density and aspect ratio profiles used in (cite: keppler18)" (4.1 Model setup) [from (cite: keppler18)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, masks, image size and cell size
- Which Cycle 3 execution blocks and any flux rescaling between epochs
- Line-free channels for continuum subtraction
- MCMC priors, walker number and step count for ring fit and rotation-surface fit
- Annulus bin parameters and exact uv-weighting used for visibility fits
- Primary beam correction details

## Analysis recipe

1. **Combine Cycle 3 and 5 data and image**: Continuum subtract, correct proper motion, shift phase center, combine and tclean  
  > "We corrected the phase center of the Cycle 3 data for the shift due to the proper motion of the star" (2 Observations and data reduction)
   - software: CASA, tclean, uvcontsub, uvmodelfit
   - parameter: robust = 0.5  
  > "applying Briggs weighting with a robust parameter of 0.5" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Self-calibration tested and found not to improve images  
  > "self-calibration of both continuum and CO data did not significantly improve the images" (2 Observations and data reduction)
2. **Disk geometry from continuum**: 2D Gaussian fit in uv-plane for inclination and PA; cross-checked with short baselines and disk model  
  > "By fitting a two-dimensional Gaussian to the two data sets using the task `UVMODELFIT`, we find a disk inclination of 51.7$\pm$0.1$^{\mathrm{o}}$" (3.1 855 um dust continuum)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: Inclination consistent within 3° across methods  
  > "the values for the inclination were consistently within 3$^{\mathrm{o}}$" (3.1 855 um dust continuum)
3. **Fit dust ring profile**: Fit real part of deprojected visibilities with radially asymmetric Gaussian ring  
  > "fit the real part of the deprojected visibilities with a radially asymmetric Gaussian ring using a Markov chain Monte Carlo (MCMC) method using *emcee*" (3.1.1 Disk radial and azimuthal morphology)
   - software: emcee
   - parameter: inclination 51.7°  
  > "We first deprojected the data assuming an inclination of 51.7$^{\mathrm{o}}$" (3.1.1 Disk radial and azimuthal morphology)
   - fitting: MCMC with emcee; priors not stated  
  > "fit the real part of the deprojected visibilities with a radially asymmetric Gaussian ring using a Markov chain Monte Carlo (MCMC) method using *emcee*" (3.1.1 Disk radial and azimuthal morphology)
   - validation: _not stated_
4. **CPD dust mass upper limit**: Isella+14 model with three-component temperature, Sigma ∝ r^-3/4, optically thin/thick flux integral compared to 5 sigma noise  
  > "we assumed a power-law surface density $\Sigma(r) = C\times\ r^{-3/4}$" (3.1.4 Upper limits on CPD dust mass)
   - parameter: outer radius 0.3-0.7 R_H; T_irr,star = 19 K at 22 au; kappa 3.5 cm2/g  
  > "considering outer CPD radii of 0.3-0.7 $r_H$" (3.1.4 Upper limits on CPD dust mass)
   - assumption: CPD inclination equal to disk inclination; accretion rate 1e-8 MJup/yr; r_p 3 RJup  
  > "assumed to be equal to the inclination of the circumstellar disk (51.7$^{\mathrm{o}}$)" (3.1.4 Upper limits on CPD dust mass)
   - fitting: _not stated_
   - validation: Dependence on planet mass and accretion rate explored in Appendix  
  > "We explore the dependency of the CPD detection limit on the planetary mass and accretion rate." (Appendix 6.1)
5. **12CO emission surface and Keplerian fit**: Rotation map with bettermoments, fit Keplerian with flared surface z0 (r/1'')^phi, inclination fixed  
  > "We then fit a Keplerian rotation pattern to the data, including a flared emission surface parameterized as $z(r) = z_0 \times (r \,/ \, 1\ensuremath{''})^{\varphi}$" (3.2.1 Deriving a 12CO emission surface)
   - software: bettermoments
   - parameter: i fixed at 51.7°  
  > "fixed the inclination at $i = 51.7\ensuremath{^\circ}$ to break the degeneracy with the stellar mass" (3.2.1 Deriving a 12CO emission surface)
   - fitting: Posterior percentiles (16th-84th) reported; sampler not stated  
  > "These uncertainties describe the 16th to 84th percentile range of the posterior distributions" (3.2.1 Deriving a 12CO emission surface)
   - validation: Statistical uncertainties only; systematics may be larger  
  > "do not take into account the systematic uncertainties that may be significantly larger" (3.2.1 Deriving a 12CO emission surface)
6. **Deprojected CO radial profiles**: Deproject using emission surface, azimuthally average in constant-radius bins  
  > "the data were deprojected into bins of constant radius and were azimuthally averaged" (3.2.1 Deriving a 12CO emission surface)
   - fitting: _not stated_
   - validation: _not stated_
7. **CO rotation curve and deviation from Keplerian**: Shift annulus spectra to common velocity; ten realizations randomizing pixels and annuli; quarter-beam bin width  
  > "We ran ten different realizations of this, randomizing the pixels taken from each annulus" (3.2.2 12CO rotation curve)
   - software: eddy
   - parameter: radial bin width a quarter beam  
  > "maintaining a radial bin width of a quarter beam width" (3.2.2 12CO rotation curve)
   - fitting: _not stated_
   - validation: Zero-point uncertainty from 3 sigma stellar mass; beam smearing assessed in Appendix  
  > "the green hatched area marks the uncertainty of the zero-point of $\mathrm{\delta v_{rot}}$ inferred by the 3$\sigma$ statistical uncertainties of the stellar mass" (3.2.2 12CO rotation curve)
8. **Hydrodynamic and RT comparison**: FARGO3D 3D hydro with 2, 5, 10 MJup for 1000 orbits; RADMC3D 12CO cubes; simobserve; same moment and rotation analysis  
  > "we carried out three-dimensional hydrodynamic calculations using FARGO3D" (4.1 Model setup)
   - software: FARGO3D, RADMC3D, CASA simobserve
   - parameter: alpha=1e-3; gas mass 0.003 Msun; 12CO/H2 = 1e-4; microturbulence 30 m/s  
  > "A disk viscosity of $\alpha=10^{-3}$ was added to the simulations." (4.1 Model setup)
   - assumption: Vertically isothermal disk, LTE CO  
  > "We assumed a vertically isothermal disk temperature structure and used an isothermal equation of state." (4.1 Model setup)
   - fitting: Qualitative comparison by eye; no formal fit  
  > "The width and depth of the depleted flux density in the observations are reasonably well reproduced by a 5 $\rm M_{Jup}$ planet." (4.1.2 Comparison with observations)
   - validation: Gap width and depth match 5 MJup; kinematic depth matches 10 MJup  
  > "the radial location and the amplitude of the minimum $\delta v_{\rm rot}$ of the rotation curve of the PDS 70 disk is best matched by the perturbations created by a 10 $\rm M_{Jup}$ planet" (4.1.2 Comparison with observations)

## Software

- **CASA** 5.1.1 (calibration), 5.3.0 (processing), 5.1.2 (simobserve): Calibration, uvcontsub, uvmodelfit, tclean, simobserve  
  > "We finally used the task `TCLEAN` for imaging" (2 Observations and data reduction)
- **emcee** : MCMC fit of dust ring  
  > "using a Markov chain Monte Carlo (MCMC) method using *emcee*" (3.1.1 Disk radial and azimuthal morphology)
- **bettermoments** : Rotation velocity map  
  > "using `bettermoments` (cite: bettermoments)" (Footnote 3)
- **eddy** : Python implementation of the rotation profile method  
  > "A Python implementation of this method, `eddy` (cite: eddy), is publicly available" (Footnote 5)
- **FARGO3D** : 3D hydrodynamic simulations  
  > "we carried out three-dimensional hydrodynamic calculations using FARGO3D (cite: benitez16; masset00)" (4.1 Model setup)
- **RADMC3D** 0.41: Thermal structure and 12CO image cubes  
  > "We generated $^{12}$CO image cubes using the radiative transfer code RADMC3D version 0.41" (4.1 Model setup)
- **BHMIE** : Mie opacities  
  > "The grain opacity was computed according to the Mie theory using the BHMIE code" (4.1 Model setup)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum integrated flux density within 1.3'' | 230 | ±23 | mJy | 1 | is 230$\pm$23 mJy |
| Disk inclination (Cycle 5) | 51.7 | ±0.1 | deg | 2 | we find a disk inclination of 51.7$\pm$0.1$^{\mathrm{o}}$ and 52.1$\pm$0.1$^{\mathrm{o}}$ |
| Dust ring peak radius | 73.7 | ±0.1 | au | 3 | The best-fit model has a peak radial position of 73.7$\pm$0.1 au |
| Ring inner and outer width | 14.8 and 13.4 | ±0.1 each | au | 3 | an inner and outer width of 14.8$\pm$0.1 au and 13.4$\pm$0.1 au |
| 5-sigma CPD dust mass upper limit | ~0.01 | not stated | Earth masses | 4 | we find a 5$\sigma$ upper dust mass limit of $\sim$0.01 $\rm M_{\oplus}$ |
| Stellar mass from Keplerian fit | 0.875 | ±0.03 | Msun | 5 | $M_{\rm star} = 0.875 \pm 0.03~M_{\rm sun}$ |
| CO emission surface z0 and exponent | 0.33 and 0.76 | ±0.01 each | arcsec; dimensionless | 5 | z(r) [\ensuremath{''}] = \left(0.33 \pm 0.01\right) \times \left( \frac{r}{1\ensuremath{''}} \right)^{0.76 \pm 0.01} |
| Maximum deviation from Keplerian rotation at ~0.2'' | ~12 | not stated | percent | 7 | A significant deviation of up to $\sim 12\%$ at $\sim 0.2\ensuremath{''}$ is observed |

## Qualitative findings

- Inner disk and possible dust/gas bridge toward the NW; spur at PA ~285° in continuum  
  > "We detect a spur that projects from the dust ring into the gap in the direction of the inner disk at a $PA$ of about 285$^{\mathrm{o}}$" (3.1.3 Possible bridge feature)
- Tentative 12CO point source at ~0.39'' and PA ~260°  
  > "We tentatively detect a point source in the $^{12}$CO emission maps at a projected separation of $\sim$0.39$\ensuremath{''}$ and a PA of $\sim$260$^{\mathrm{o}}$." (3.2.3 Potential point source)

## Claim tuples

- H: Can circumplanetary dust around PDS 70 b be detected? | E: Compare 5 sigma continuum limit at the planet location with CPD thermal models | R: Upper limit ~0.01 Earth masses; marginal S/N~3 signal at 0.2'' | F: No CPD detected; emission likely optically thin at limit | **supported**
- H: Is the CO gap at 0.2'' consistent with a gap carved by PDS 70 b? | E: Compare CO radial profiles to hydro+RT simulations | R: Gap width and depth reproduced by 5 MJup planet | F: Inner CO gap is likely carved by PDS 70 b | **supported**
- H: Does a single planet at PDS 70 b's orbit explain the wide gap and the distant dust ring? | E: Compare rotation curve residual to simulated rotation curves | R: Depth matches ~10 MJup but super-Keplerian region extends farther than models | F: An additional low-mass companion or other mechanism may be needed | **partially**

## Reasoning

- Why this data: Extended configuration filters large scales, so archival Cycle 3 data were added for short baselines  
  > "Because the extended antenna configuration filters out the largest spatial scales in the disk" (2 Observations and data reduction)
- Why this method: _not stated_
- Alternative: Secondary pressure bump scenario for the ring (single planet making multiple gaps or vortex-induced secondary ring)  
  > "An alternative scenario to explain the distant location of the ring compared to the position of PDS 70 b is to consider that the ring traces a secondary pressure bump." (4.1.2 Comparison with observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Hydro models assume vertically isothermal disk; delta v_rot may be underestimated  
  > "our hydrodynamic models consider a vertically isothermal temperature structure" (4.1.2 Comparison with observations)
- Limitation (authors): Beam smearing and limited spectral resolution complicate rotation-curve interpretation  
  > "this makes a direct analysis challenging" (3.2.2 12CO rotation curve)
- Caveat (inferred, ours): Planet mass inferred by eye comparison of three simulations, no quantitative fit
- Caveat (inferred, ours): CO emission surface and Keplerian fit assume a simple power-law flared surface
- Caveat (inferred, ours): Point source and bridge are tentative, ~5-6 sigma, and need confirmation
- Caveat (inferred, ours): CPD limit depends on assumed opacity, temperature and accretion rate

## Reproducibility

- Data public (paper): Archival Cycle 3 data used and ALMA data acknowledged; public status of DDT data not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2017.A.00006.S, ADS/JAO.ALMA$\#$2015.1.00888.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: eddy publicly available on GitHub  
  > "A Python implementation of this method, `eddy` (cite: eddy), is publicly available at <https://github.com/richteague/eddy>." (Footnote 5)
- Missing: CLEAN masks, thresholds, image and cell sizes
- Missing: MCMC priors and settings
- Missing: Details of hydro-to-RT post-processing and simobserve configuration
- Missing: Cycle 3 execution blocks used
- Data volume (inferred): ~100-300 GB raw for the two projects
- Score (inferred): 3/5, Data archival and software named, but many imaging and fitting settings are missing; model comparison is largely qualitative.
- Rediscovery candidate: no, Key results rely on hydro simulations and several unstated settings, though some numerics (ring fit, CPD limit) are repeatable.

## Links

- Method: (cite: Teague+2018b) (Rotation curve method)
- Method: (cite: Teague_Foreman-Mackey_2018) (Rotation velocity map method (bettermoments))
- Method: (cite: Isella+14) (CPD temperature and flux model)
- Method: (cite: 2018ApJ...859...32P) (Ring fitting approach)
- Companion: (cite: Long18) (Archival Cycle 3 ALMA data of PDS 70)
- Companion: (cite: keppler18) (Discovery of PDS 70 b and disk radiative transfer model)
- Companion: (cite: mueller2018) (Atmospheric characterization of PDS 70 b)

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 71,
  "rate": 0.724
 },
 "evidence_ok": true
}
```
