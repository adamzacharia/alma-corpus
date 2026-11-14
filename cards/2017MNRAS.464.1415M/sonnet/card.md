# Exocometary gas structure, origin and physical properties around β Pictoris through ALMA CO multitransition observations

`2017MNRAS.464.1415M` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Matrà, L. | arXiv: 1609.06718 | DOI: 10.1093/mnras/stw2415

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, astrochemistry
- Question: What are the structure, origin and physical conditions (electron/H2 density, CO mass, exocometary ice content) of CO gas in the beta Pic debris disk, from ALMA CO J=2-1 combined with archival J=3-2?  
  > "In this work, we focus on CO J=2-1 emission at 230 GHz, observed at an improved sensitivity and spatial resolution of $\sim5.5$ AU" (Introduction)
- Target **beta Pictoris**: coordinates _not stated_; z/distance not stated numerically (beam 0.30x0.26 arcsec = 5.8x5.1 AU)  
  > "corresponding to 5.8$\times$5.1 AU at the known distance to the system." (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00142.S, 2011.0.00087.S
- bands: Band 6 (CO J=2-1) new; Band 7 (CO J=3-2) archival  
  > "We observed the $\beta$ Pictoris disk with ALMA during its Cycle 2 (project code 2012.1.00142.S) using band 6 receivers." (Observations)
- frequencies and spectral setup: Two TDM continuum windows at 218.5 and 232.5 GHz; FDM windows on 12CO 2-1 (244.141 kHz channels, 0.64 km/s) and SiO 5-4  
  > "The corresponding velocity resolutions are 0.64 and 1.35 km/s (after Hanning smoothing)." (Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array and ACA (Band 6); 12-m only (Band 7)  
  > "Observations were performed using both the 12-m array and the Atacama Compact Array (ACA)." (Observations)
- configurations: _not stated_
- baselines: 9 to 1574 m (Band 6 combined); 16 to 382 m (Band 7)  
  > "(covering baselines from 9 to 1574 m)" (Observations)
- angular resolution: 0.30''x0.26'' (Band 6); 0.69''x0.55'' (Band 7)  
  > "resulting in a synthesised beam of size 0.30$''$$\times$0.26$''$" (Observations)
- max recoverable scale: sensitive to scales 0.3'' to 27'' (Band 6)  
  > "sensitivity to structure on scales between 0.3$''$ and 27$''$" (Observations)
- sensitivity: _not stated_
- time on source: 28, 114 and 50 min (12-m compact, 12-m extended, ACA)  
  > "The on-source times were 28, 114 and 50 minutes respectively for the 12-m (compact and extended) and ACA observations." (Observations)
- observing dates: Dec 2013 (compact), Aug 2015 (extended), Oct 2013 (ACA)  
  > "for the most compact one, observed in December 2013, a mosaic strategy was used" (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: CO J=3-2 (345.796 GHz)
- External data: Disk thermodynamical model: temperature profile (80 K at 50 AU, slope -0.8), C II density ~150 cm^-3 at 85 AU, C I column  
  > "we assume the temperature radial profile predicted by (cite: Kral2016a), i.e. a power law with slope of $-0.8$, normalised to a value of 80 K at 50 AU." (4.1) [from (cite: Kral2016a)]
- External data: Stellar mass 1.75 Msun  
  > "Keplerian rotation around a 1.75 M$_{\odot}$ star (cite: Crifo1997)" (3.3.1) [from (cite: Crifo1997)]
- External data: Fractional dust luminosity 2.1e-3 and stellar luminosity 8.7 Lsun  
  > "fractional luminosity $L_{\rm dust}/L_{\ast}$ of $2.1\times 10^{-3}$ around a star of 8.7 $L_{\odot}$ (cite: KennedyWyatt2014)" (5.2.1) [from (cite: KennedyWyatt2014)]
- External data: Disk PA 29.3 deg from scattered light  
  > "corresponding to 29.3$^\circ$$^{+0.2}_{-0.3}$ (cite: Lagrange2012)" (3.2) [from (cite: Lagrange2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3.0  
  > "The data calibration was carried out using the CASA software version 4.3.0" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus, Ganymede or J0519-454 (amplitude)  
  > "either Uranus, Ganymede or J0519-454 were used as amplitude calibrators" (Observations)
- flux scale uncertainty: 10%  
  > "the flux calibration is estimated to be accurate within 10% (ALMA Cycle 2 Technical Handbook)" (Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: CLEAN (Hogbom)  
  > "using the CLEAN algorithm (cite: Hogbom1974)" (Observations)
- weighting robust: Natural weighting  
  > "Natural weighting of the visibilities was applied" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on combined visibilities  
  > "we first subtracted the continuum from the combined visibility dataset using the *uvcontsub* task within CASA" (Observations)
- line free channels: _not stated_
- primary beam correction: fluxes measured on primary-beam-corrected moment-0 images  
  > "The total line flux was measured on the primary-beam-corrected moment-0 images" (3 Results)
- array combination: ACA and 12-m concatenated  
  > "The calibrated visibilities from the ACA and the 12-m datasets" (Observations)
- smoothing: Band 6 re-CLEANed to Band 7 beam/channel size and convolved spectrally with a Gaussian  
  > "convolution by a Gaussian of FWHM equal to the quadratic difference between the target resolution and the native resolution was necessary" (Appendix A)
- final beam: 0.30''x0.26'' PA -83.9 deg (B6); 0.69''x0.55'' PA 65.4 deg (B7)  
  > "final synthesised beam of size 0.69$''$$\times$0.55$''$ (13.4$\times$10.7 AU) and PA 65.4$^\circ$" (ALMA Band 7)
- final rms: _not stated_

### Inherited from earlier work

- Band 7 data reduction repeated in same way as Band 6; original described in Dent et al.  
  > "which are described in (cite: Dent2014)" (ALMA Band 7) [from (cite: Dent2014)]
- NLTE CO excitation methods  
  > "using the non-local thermodynamic equilibrium methods developed in (cite: Matra2015)" (Introduction) [from (cite: Matra2015)]
- Collisional cascade mass loss assumptions  
  > "We take the same assumptions as in Sect. 4.4 of (cite: Marino2016)" (5.2.1) [from (cite: Marino2016)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters: cell size, image size, masking, iterations, threshold
- Line-free channels for uvcontsub
- Self-calibration not mentioned
- Exact moment-0 integration region for flux
- Collisional rate files and NLTE code settings not given here
- Dust continuum and astrometric offsets deferred to forthcoming work

## Analysis recipe

1. **Calibrate, image, and match CO cubes**: CASA calibration, concatenation of ACA+12m, uvcontsub, CLEAN natural weighting; degrade 2-1 to 3-2 resolution  
  > "we also produced a final CO J=2-1 data cube at the degraded spatial and spectral resolution of the archival J=3-2 dataset" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure integrated fluxes and line ratio**: Spatially integrate primary-beam-corrected moment-0 maps; ratio errors summed in quadrature  
  > "we then summed the relative errors on both fluxes in quadrature (under the assumption that they are Gaussian in nature) to obtain the uncertainty on the line ratio" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit vertical disk structure (spine, scale height)**: 1D Gaussian fits to vertical cuts at each midplane position (>5 sigma); H from deconvolving beam  
  > "we can derive $H$ by simply deconvolving $\sigma_{\rm obs}$ by the observed instrumental resolution projected along the vertical axis" (3.2)
   - software: emcee
   - parameter: 300 walkers, 500 steps; uniform priors |y_obs|<20 AU, FWHM_beam<FWHM<80 AU  
  > "was sampled using 300 walkers through 500 steps" (Appendix B)
   - assumption: Edge-on disk, Gaussian vertical profile  
  > "Assuming that the disk is edge-on and that its true vertical structure can be represented by a Gaussian" (3.2)
   - fitting: Affine invariant ensemble MCMC, chi2 likelihood including flux and position errors  
  > "The likelihood function of the data given a model 1D Gaussian was defined through the $\chi^2$ distribution" (Appendix B)
   - validation: _not stated_
4. **Map PV diagrams to orbital plane and derive H(R), T(R)**: Keplerian PV-to-radius mapping; H vs R power law; T from hydrostatic equilibrium  
  > "the scale height can then be used to trace the disk temperature at a certain orbital radius" (3.3.1)
   - assumption: M*=1.75 Msun, mu=14, vertically isothermal, Keplerian  
  > "giving a mean molecular mass $\mu=14$" (3.3.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Constrain inclination and tilt via chi2 grid**: Model double-Gaussian of front/back flux fractions over grid of i and dPA  
  > "we therefore construct this model for a grid of $i$ and dPA and in each case evaluate how well it fits the observed data cube" (Appendix D)
   - fitting: reduced chi2 map  
  > "showing the resulting reduced $\chi^2$ map in Fig. [13](#fig:chisqmap)." (Breaking the deprojection degeneracy using the observed vertical structure)
   - validation: _not stated_
6. **NLTE line ratio modelling for electron and H2 density**: Compare 3-2/2-1 ratios per PV spaxel with NLTE grid in (Tk, ne) / (Tk, nH2), assuming Kral temperature profile  
  > "our measurements can confidently constrain the electron density in the disk to around $10^2$-$10^3$ cm$^{-3}$" (4.1)
   - parameter: mask highest 10% of ratios (>3.80); spaxels >4 sigma  
  > "we mask the highest 10% of the line ratios (i.e. those above 3.80)" (4.1)
   - assumption: Optically thin CO, electrons as only colliders (upper limits)  
  > "We begin by assuming CO line emission to be optically thin at the wavelengths of the observed transitions" (4)
   - fitting: _not stated_
   - validation: Optical depth check at brightest spaxel  
  > "we obtain an optical thickness $\tau_{3-2}=0.27\pm0.05$ for the 3-2 line at the clump location" (4.3)
7. **Derive CO mass**: Monte Carlo over flux samples (1e4) and line ratio samples (1e8), random (Tk,ne) on ratio contour, upper level population  
  > "For each integrated line flux, we sample this Gaussian 10$^4$ times and for each sample calculate the line ratio, which will itself be sampled 10$^8$ times." (4.3)
   - assumption: Uniform underlying (Tk,ne) distribution  
  > "randomly draw one of these pairs, assuming a uniform underlying $\left(T_{\rm k},n_{\rm e^-}\right)$ distribution" (4.3)
   - fitting: _not stated_
   - validation: _not stated_
8. **Exocomet CO+CO2 ice abundance**: Steady-state: CO destruction rate (photodissociation with shielding) divided by solid mass loss rate from collisional cascade  
  > "we can obtain the latter by dividing the destruction rate (derived in Sect. 5.2.2) by the production rate" (5.2.3)
   - assumption: Steady state; belt 50-150 AU; production rate is lower limit  
  > "Given that the production rate is a lower limit, we obtain an upper limit of 6% on the CO mass abundance" (5.2.3)
   - fitting: _not stated_
   - validation: Compared with Solar System comets and HD181327  
  > "Therefore, the 6% upper limit mass abundance of CO+CO$_2$ in $\beta$ Pictoris is consistent with Solar System cometary compositions" (Comparison with other cometary ices)

## Software

- **CASA** 4.3.0: Calibration, uvcontsub, CLEAN imaging  
  > "The data calibration was carried out using the CASA software version 4.3.0" (Observations)
- **emcee** : MCMC fitting of vertical Gaussians  
  > "implemented through the Python emcee package (cite: Foreman-Mackey2013)" (Appendix B)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO J=2-1 integrated flux | 3.5e-20 | 0.4e-20 | W m^-2 | 2 | $(3.5\pm0.4) \times10^{-20}$ W m$^{-2}$ for the J=2-1 transition |
| CO J=3-2 integrated flux | 6.7e-20 | 0.7e-20 | W m^-2 | 2 | $(6.7\pm0.7) \times10^{-20}$ W m$^{-2}$ for the J=3-2 transition |
| Integrated 3-2/2-1 ratio | 1.9 | 0.3 | dimensionless | 2 | indicating an integrated 3-2/2-1 line ratio of $1.9\pm0.3$ |
| Scale height at 85 AU | 7.0 | +/-0.6 | AU | 4 | H=7.0^{+0.6}_{-0.6} \times \left(\frac{R}{85 \rm AU}\right)^{0.75^{+0.02}_{-0.02}} |
| Scale height power-law index | 0.75 | +/-0.02 | dimensionless | 4 | H=7.0^{+0.6}_{-0.6} \times \left(\frac{R}{85 \rm AU}\right)^{0.75^{+0.02}_{-0.02}} |
| Temperature at 85 AU | 2.1e2 | +/-0.4e2 | K | 4 | T=\left(2.1^{+0.4}_{-0.4} \times 10^{2}\right) \times \left(\frac{R}{85 \rm AU}\right)^{-1.58} |
| Best-fit inclination / tilt | i~88 deg, dPA~3 deg | i>=86, dPA<=5 reasonable | deg | 5 | the formal best-fit (i.e. the $\chi^2$ minimum) is at $i\sim88^{\circ}$ and dPA $\sim3^{\circ}$ |
| Electron density | 10^2-10^3 | not stated | cm^-3 | 6 | our measurements can confidently constrain the electron density in the disk to around $10^2$-$10^3$ cm$^{-3}$ |
| H2 density upper limit | 10^3-10^5 | not stated | cm^-3 | 6 | its density would be between 10$^3$ and 10$^5$ cm$^{-3}$ at radii between 50 and 200 AU |
| Excitation temperature | 12 | 4 | K | 7 | corresponds to an excitation temperature $T_{\rm exc}=12\pm4$ K |
| Total CO mass | 3.4e-5 | +0.5/-0.4 e-5 | Earth masses | 7 | The CO mass range obtained is $3.4^{+0.5}_{-0.4} \times 10^{-5}$ M$_{\oplus}$ |
| CO optical depth at clump (3-2) | 0.27 | 0.05 | dimensionless | 7 | we obtain an optical thickness $\tau_{3-2}=0.27\pm0.05$ |
| CO photodissociation timescale (shielded) | ~300 | not stated | years | 8 | we estimate a photodissociation timescale in the clump midplane of $\sim$300 years |
| CO mass loss rate | 0.11 | not stated | Earth masses/Myr | 8 | yields a CO mass loss rate of 0.11 M$_{\oplus}$/Myr |
| Solid mass loss rate | 1.9 | not stated | Earth masses/Myr | 8 | The resulting total mass loss rate from the planetesimal belt is 1.9 M$_{\oplus}$/Myr |
| CO+CO2 ice abundance upper limit | 6% | upper limit | percent by mass | 8 | we obtain an upper limit of 6% on the CO mass abundance |
| CO-CII collision timescale | 0.19 | not stated | years | 0 | The timescale for CO-C II collision obtained is 0.19 years |

## Qualitative findings

- CO disk is vertically tilted relative to the main dust disk, consistent with the scattered-light warp  
  > "the CO disk is vertically tilted compared to the main dust disk, at an angle consistent with the scattered light warp" (abstract)

## Claim tuples

- H: Is the CO clump radially broad, discriminating giant impact from resonant migration? | E: Deprojected CO 2-1 PV diagram at 0.3'' resolution; collision timescale of CO with C II | R: CO detected over at least ~100 AU in radius at clump azimuth; CO-CII collision time 0.19 yr | F: Point-like giant impact ruled out; resonant migration favoured | **supported**
- H: Is the CO gas primordial or secondary? | E: NLTE analysis of 3-2/2-1 ratios assuming H2 colliders | R: nH2 ~1e3-1e5 cm^-3, column ~1e19 cm^-2 insufficient to shield CO | F: CO must be replenished; secondary origin | **supported**
- H: What are the CO scale height and electron density, and do they match thermodynamical models? | E: PV-based vertical fits and NLTE ratios | R: H ~ R^0.75, ne slope ~ -1 | F: ne radial dependence in agreement with models; scale height twice model prediction | **partially**
- H: What is the exocomet CO+CO2 ice abundance? | E: Steady-state production/destruction | R: At most ~6% by mass | F: Consistent with Solar System comets and HD181327 | **supported**

## Reasoning

- Why this data: Improved sensitivity and resolution compared with archival 3-2 data, and a second transition allows line ratio analysis  
  > "at an improved spectro-spatial resolution and sensitivity compared to previous CO J=3-2 observations" (abstract)
- Why this method: _not stated_
- Alternative: Giant impact scenario rejected since it requires implausible ~1200 km/s CO velocities  
  > "a point-like production location such as predicted in the giant impact scenario is ruled out" (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Electron densities are upper limits since other colliders may contribute  
  > "the electron densities probed here should strictly speaking be considered upper limits" (4.1)
- Limitation (authors): Edge-on assumption and degeneracy; CO abundance depends on uncertain cascade assumptions  
  > "We note that there is a considerable uncertainty on this number" (5.2.1)
- Caveat (inferred, ours): Scale height and temperature rely on edge-on and isothermal assumptions
- Caveat (inferred, ours): Temperature profile assumed from model in NLTE inversion
- Caveat (inferred, ours): Band 7 data had astrometric systematics
- Caveat (inferred, ours): Ice abundance depends on poorly known collisional cascade parameters

## Reproducibility

- Data public (paper): Both datasets identified by ALMA project codes and acknowledged as ALMA data; Band 7 described as archival  
  > "we retrieved archival ALMA Band 7 CO J=3-2 data obtained within Cycle 0" (ALMA Band 7)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, mask, threshold)
- Missing: Line-free channels
- Missing: NLTE code and collision data handling
- Missing: Moment-0 flux integration region
- Missing: Details of Appendix cube degradation parameters
- Data volume (inferred): ~50-100 GB raw (Band 6 12m+ACA, Band 7)
- Score (inferred): 3/5, Public data and clear analysis recipe, but missing imaging parameters and NLTE code details.
- Rediscovery candidate: yes, Data are archival, fluxes and H(R) fits are numeric and recipe is largely described.

## Links

- Method: (cite: Matra2015) (NLTE CO excitation methods and mass calculation)
- Companion: (cite: Dent2014) (Original CO J=3-2 ALMA detection and clump)
- Companion: (cite: Kral2016a) (Atomic gas disk model)
- Companion: (cite: Marino2016) (HD181327 comparison)

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 54,
  "rate": 0.621
 },
 "evidence_ok": true
}
```
