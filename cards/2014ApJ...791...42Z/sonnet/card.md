# Comparison of the Dust and Gas Radial Structure in the Transition Disk [PZ99] J160421.7-213028

`2014ApJ...791...42Z` | The Astrophysical Journal 2014 | first author: Zhang, Ke | arXiv: 1406.6974 | DOI: 10.1088/0004-637X/791/1/42

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How do the radial structures of mm-sized dust and CO gas compare in the transition disk J1604-2130, and what do they imply for the cavity formation mechanism?  
  > "The large separation of the dust and gas cavity edges, as well as the high radial concentration of millimeter-sized dust grains, is qualitatively consistent with the predictions of pressure trap models" (abstract)
- Target **[PZ99] J160421.7-213028 (J1604-2130)**: coordinates _not stated_; z/distance 145 pc  
  > "J1604-2130 is a member of the Upper Scorpius OB association at a distance of 145 pc (cite: deZeeuw99), with a spectral type of K2, a stellar mass of 1.0  M$_\odot$" (Introduction); distance from de Zeeuw et al. 1999 (Upper Sco association distance)  
  > "J1604-2130 is a member of the Upper Scorpius OB association at a distance of 145 pc (cite: deZeeuw99), with a spectral type of K2, a stellar mass of 1.0  M$_\odot$" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00526.S
- bands: ~880 um (Band 7), cycle 0  
  > "We present ALMA observations of the 880 $\,{\rm \mu m}$ continuum and CO $J$= 3-2 line emission" (abstract)
- frequencies and spectral setup: four windows at 345.77, 347.65, 335.65, 333.77 GHz, 1.875 GHz each, 488 kHz channels (0.42 km/s), Hanning smoothed  
  > "The spectral setup consists of four windows centered at 345.77, 347.65, 335.65, and 333.77 GHz, respectively, each providing a total bandwidth of 1.875 GHz in 488 kHz (0.42 km s$^{-1}$) channels." (2 Observations)
- continuum bandwidth: 7.5 GHz total coverage, line-free channels  
  > "Continuum emission from J1604-2130 was extracted from the total 7.5 GHz coverage by combining the line-free channels from all four windows after flagging the edge channels." (2 Observations)
- arrays: 28 12-m antennas  
  > "as part of the ALMA cycle 0 project 2011.0.00526.S (cite: Carpenter14) with 28 12-meter antennas" (2 Observations)
- configurations: _not stated_
- baselines: 21 to 402 m (23-457 klambda)  
  > "Baselines ranged from 21 to 402 m (23-457 k$\lambda$)." (2 Observations)
- angular resolution: 0.73"x0.46" (106x67 AU), PA 105 deg  
  > "restored with a synthesized beam of size 0$''$.73$\times$0$''$.46 (106$\times$67 AU at 145 pc)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.18 mJy/beam  
  > "The synthesized continuum image has an rms noise level of 0.18 mJy beam$^{-1}$" (3 Results)
- time on source: 315 s  
  > "The total integration time on J1604-2130 was 315 seconds." (2 Observations)
- observing dates: 28 August 2012  
  > "The observations of J1604-2130 were carried out on 28 August 2012" (2 Observations)
- pi or archival as stated: Cycle 0 project; Carpenter et al. 2014 cited  
  > "as part of the ALMA cycle 0 project 2011.0.00526.S (cite: Carpenter14)" (2 Observations)
- Line: CO J=3-2 (345.795 GHz)
- Line: H13CO+ J=4-3 (346.998 GHz)
- Line: H13CN J=4-3 (345.339 GHz)
- Line: HN13C J=4-3 (348.340 GHz)
- Other facility **Keck NIRSPEC**: CO 4.7 um rovibrational non-detection  
  > "we do not detect any CO rovibrational emission at 4.7 $\,{\rm \mu m}$ with Keck NIRSPEC" (3 Results)
- Other facility **SMA**: earlier 880 um continuum and CO 3-2 data (Mathews et al. 2012) used for comparison  
  > "reported a lower continuum flux of 165$\pm$6 mJy (20% absolute flux uncertainty) from SMA observations" (3 Results)
- External data: Broadband SED (1-200 um; IRAC, IRS, WISE photometry) used for dust model  
  > "the IRAC photometric data for J1604-2130 are discrepant from its IRS spectra and the WISE photometry results between 3 and 16 $\,{\rm \mu m}$ (cite: Carpenter06; Dahm09; Luhman12)" (4.2 Dust emission: fitting procedure and results) [from (cite: Carpenter06; Dahm09; Luhman12)]
- External data: Millimeter SED slope alpha=3.2+-0.2, beta=1.2  
  > "$\alpha =  3.2\pm$0.2, leading to $\beta$ = 1.2 (cite: Mathews12)" (4.2 Dust emission: fitting procedure and results) [from (cite: Mathews12)]
- External data: Stellar parameters Teff=4550 K, R*=1.41 Rsun, M*=1 Msun  
  > "$T_{\rm eff}$ = 4550 K, R$_\star$ = 1.41 R$_\odot$, and M$_\star$ = 1 M$_\odot$ (cite: Preibisch02)" (4.1 Dust emission: model description) [from (cite: Preibisch02)]
- External data: Disk inclination of 6 deg  
  > "assuming a disk inclination angle of 6$^\circ$ as measured by (cite: Mathews12)" (4.3 CO emission: model description) [from (cite: Mathews12)]
- External data: Transition disk sample of 13 for compactness comparison  
  > "we compare $\Delta W$/$\overline{R}$ for J1604-2130 with that for the transition disks studied in (cite: Andrews11)" (5.1 Comparing J1604-2130 with other transition disks) [from (cite: Andrews11)]

## Processing

### Calibration

- pipeline or manual: Manual-style CASA reduction with self-calibration on continuum  
  > "Reduction and calibration of the data were performed using the Common Astronomy Software Application (CASA) version 4.1 (cite: McMullin07)." (2 Observations)
- casa version: CASA 4.1  
  > "Common Astronomy Software Application (CASA) version 4.1" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan; bandpass J1751+0939 and J1924-292; phase J1625-2527  
  > "The bandpass was calibrated with the radio sources J1751+0939 and J1924-292, and the visibility amplitude scale was calibrated from observations of Titan" (2 Observations)
- flux scale uncertainty: ~10%  
  > "calibrated from observations of Titan with an estimated uncertainty of $\sim$10%" (2 Observations)
- self calibration: self-calibrated on continuum of science source  
  > "the visibilities were self-calibrated on the continuum emission of the science source to reduce atmospheric decoherence" (2 Observations)

### Imaging

- task: CLEAN  
  > "deconvolved with the CLEAN algorithm using natural weighting" (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "deconvolved with the CLEAN algorithm using natural weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-domain subtraction  
  > "The spectral lines were first continuum-subtracted in the $uv$ domain" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.73"x0.46", PA 105 deg  
  > "The beam major axis position angle is 105$^{\circ}$ east of north." (2 Observations)
- final rms: 0.18 mJy/beam  
  > "The synthesized continuum image has an rms noise level of 0.18 mJy beam$^{-1}$" (3 Results)

### Inherited from earlier work

- Three-region dust surface density model  
  > "We adopt a model for the mass surface density of the dusty disk similar to that presented in (cite: Mathews12)" (4.1 Dust emission: model description) [from (cite: Mathews12)]
- Fourier-domain fitting procedure  
  > "The model fitting is performed in the Fourier domain adopting the procedure discussed in (cite: Isella09)." (4.2 Dust emission: fitting procedure and results) [from (cite: Isella09)]
- CO model  
  > "The model used to analyze the ALMA $^{12}$CO $J$= 3-2 spectral line observations is similar to that presented in (cite: Isella07)." (4.3 CO emission: model description) [from (cite: Isella07)]
- gamma=1 adopted for comparison with prior work  
  > "we adopt $\gamma=1$ (cite: Andrews07; Andrews11)" (4.2 Dust emission: fitting procedure and results) [from (cite: Andrews07; Andrews11)]
- Hybrid LM + MCMC approach; Hessian-based uncertainties for CO  
  > "we use the Hessian matrix to derive the the uncertainties on the model free parameters following the method presented in (cite: Pitu07)" (4.4 CO emission: fitting procedure and results) [from (cite: Pitu07; Isella09)]
- Dust composition and opacity  
  > "optical constants as in (cite: Draine03) and (cite: Zubko96), respectively, and at relative abundances as in (cite: Pollack94)" (4.1 Dust emission: model description) [from (cite: Draine03; Zubko96; Pollack94; Miyake93)]

### Not stated but needed to reproduce (our reading)

- Archive/pipeline version and calibration scripts beyond CASA 4.1
- Self-calibration solution intervals and number of iterations
- Line-free channel ranges for continuum and CO continuum subtraction
- CLEAN mask, threshold, cell and image size
- Parameter priors/bounds for LM and MCMC; MCMC step settings, burn-in
- Model grid setup (RADMC/RADLite resolution) and SED photometry values
- Velocity range used for CO moment maps

## Analysis recipe

1. **Image continuum and CO, measure fluxes**: Continuum from line-free channels; line cubes uv continuum-subtracted, CLEANed with natural weighting; flux in central boxes  
  > "the composite visibilities then Fourier inverted, deconvolved with the CLEAN algorithm using natural weighting" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: CO flux compared with single-dish 21.7 Jy km/s  
  > "consistent with CO 3-2 line flux from single dish observations of 21.7$\pm$0.8 Jy km s$^{-1}$ (cite: Mathews13)" (3 Results)
2. **Constrain amax and inner-disk structure from SED**: Beta from mm slope gives amax; LM chi2 fit of h0, phi, Rgap to 1-200 um SED with RADMC models  
  > "We then use the Levenberg-Marquardt $\chi^2$ minimization algorithm (LM) to search for the optimum values of $h_0$, $\phi$, and $R_{gap}$" (4.2 Dust emission: fitting procedure and results)
   - software: RADMC
   - parameter: amax ~0.05 mm; kappa(880um)=7.26 cm2/g  
  > "The dust opacity at 880 $\,{\rm \mu m}$ is 7.26 cm$^2$ g$^{-1}$." (4.2 Dust emission: fitting procedure and results)
   - assumption: Grain size distribution n(a)∝a^-3.5, amin=0.005 um; Mie spheres; silicates+carbonaceous  
  > "We assume a power-law grain size distribution, $n(a) \propto a^{-3.5}$, from $a_{ \rm min}$= 0.005 $\,{\rm \mu m}$ to a given $a_{\rm max}$." (4.1 Dust emission: model description)
   - fitting: LM chi2 minimization  
  > "We then use the Levenberg-Marquardt $\chi^2$ minimization algorithm (LM) to search for the optimum values of $h_0$, $\phi$, and $R_{gap}$ by comparing the synthetic disk emission with the measured SED" (Dust emission: fitting procedure and results)
   - validation: WISE-based alternative blackbody ring fit gives larger Rgap  
  > "Fitting the WISE photometry with an optically thick blackbody component results in a larger R$_{gap}$ = 26.5$\pm$2.8 AU" (4.2 Dust emission: fitting procedure and results)
3. **Fit dust continuum visibilities**: Model images FT'd and interpolated to observed uv points; fit Sigma_t, R_t, Rcav, delta with gamma=1 and fixed i=6 deg, PA=77 deg  
  > "the synthetic image is Fourier transformed to calculate the synthetic visibilities on a regular *uv* grid, which are then interpolated at the $uv$ coordinates sampled by the ALMA observations" (4.2 Dust emission: fitting procedure and results)
   - software: RADMC
   - parameter: 150 LM runs, then 10 MCMC chains, 5x10^4 models total  
  > "we launch 150 independent LM algorithms with random initial values to avoid local minima." (4.2 Dust emission: fitting procedure and results)
   - fitting: Hybrid LM + MCMC; chi2 of real and imaginary visibilities weighted by w as likelihood  
  > "is used as the likelihood estimator" (4.2 Dust emission: fitting procedure and results)
   - validation: Residual image; repeat with gamma=0.5 and 1.5  
  > "we repeated the dust continuum modeling assuming $\gamma=0.5$ and $\gamma=1.5$" (4.5 Uncertainties from the choice of $\gamma$)
4. **Fit CO 3-2 cube**: RADLite ray-tracing in LTE; synthetic channel maps FT'd to uv; chi2 minimization of T0, q, xi, RCO, PA  
  > "we calculate the synthetic CO $J$= 3-2 line emission using the ray-tracing code RADLite (cite: Pontoppidan09) under LTE assumption" (4.4 CO emission: fitting procedure and results)
   - software: RADLite
   - parameter: 150 LM runs; uncertainties from Hessian  
  > "we start with 150 independent LM runs and random initial values in the search" (4.4 CO emission: fitting procedure and results)
   - assumption: Gas-to-dust 100, CO/H2 5e-5, Keplerian rotation M*=1 Msun, i=6 deg, T_CO power law, CO outer edge at 17 K  
  > "a constant gas-to-dust mass ratio of 100. The CO number density at each grid point of the disk is then calculated by assuming a constant CO/H$_2$ abundance ratio of 5$\times10^{-5}$" (4.3 CO emission: model description)
   - fitting: LM chi2 minimization; no MCMC  
  > "the computational time required to generate synthetic CO data cubes precludes an efficient sampling of the four dimensional $\chi^2$ surface using a MCMC procedure." (CO emission: fitting procedure and results)
   - validation: Residual channel maps  
  > "The residual maps presented in Figure [6](#fig:co_model) reveal that our model reproduces the main kinematic features of the CO emission." (4.4 CO emission: fitting procedure and results)
5. **Compare dust concentration with other transition disks**: Characteristic width DeltaW containing 80% of mass beyond Rcav; DeltaW/Rbar vs 13 disks of Andrews et al. 2011  
  > "The $\Delta W$/$\overline{R}$ ratio can be used as an tracer of the compactness of the mass distribution." (5.1 Comparing J1604-2130 with other transition disks)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.1: Calibration and reduction  
  > "Common Astronomy Software Application (CASA) version 4.1 (cite: McMullin07)" (2 Observations)
- **RADMC** : 2D Monte Carlo dust radiative transfer  
  > "2D Monte Carlo radiative transfer code RADMC (cite: Dullemond04)" (4.1 Dust emission: model description)
- **RADLite** : CO line ray-tracing  
  > "ray-tracing code RADLite (cite: Pontoppidan09)" (4.4 CO emission: fitting procedure and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density (4" box) | 226 | ±1 mJy (10% absolute) | mJy | 1 | The continuum flux density integrated over a central 4$''$ square box is 226$\pm$1 mJy |
| CO 3-2 integrated intensity (6" box) | 21.4 | ±0.2 | Jy km/s | 1 | We measure an integrated intensity of 21.4$\pm$0.2 Jy km s$^{-1}$ over a central 6$''$ square box |
| Dust cavity radius Rcav | 78.8 | ±0.1 | AU | 3 | Cavity radius        / R$_{\rm cav}$ (AU)                     / 78.8$\pm$0.1 |
| Depletion factor log(delta) | -1.86 | ±0.03 | dimensionless | 3 | log($\delta$)                          / -1.86$\pm$0.03 |
| Transition radius Rt | 10.6 | ±0.2 | AU | 3 | R$_t$ (AU)                             / 10.6$\pm$0.2 |
| CO cavity radius | 31.2 | ±0.3 | AU | 4 | R$_{\rm CO}$ (AU)                      / 31.2$\pm$0.3 |
| CO temperature at 100 AU | 45.8 | ±0.2 | K | 4 | T$_0$ (K)                              / 45.8$\pm$0.2 |
| CO temperature index q | -0.64 | ±0.01 | dimensionless | 4 | Temperature index    / $q$                                    / -0.64$\pm$0.01 |
| Turbulence factor xi | 0.25 | ±0.01 | dimensionless | 4 | Turbulence factor    / $\xi$                                  / 0.25$\pm$0.01 |
| Disk PA from CO | 76.8 | ±0.5 | deg | 4 | Position angle       / PA ($^\circ$)                          / 76.8$\pm$0.5 |
| Total dust mass | 0.16 | not stated | MJup | 3 | the total mass in dust is 0.16 M$_{\rm Jup}$ |
| Radial range holding 80% of dust mass | 79-114 | not stated | AU | 3 | approximately 80% of the mass contained between 79 AU and 114 AU |
| Rgap from SED | 14.6 | ±2.5 | AU | 2 | R$_{gap}$ = 14.6$\pm$2.5 AU, $\phi$ = 0.6$\pm$0.1, and $h_{100 {\rm AU}}$ = 4.0$\pm$0.2 AU |

## Qualitative findings

- Dust is detected inside the cavity at ~100x lower surface density than just outside.  
  > "Dust inside the cavity is detected in the 880 $\,{\rm \mu m}$ continuum, but with a surface density 100 times lower than that just beyond the dust truncation radius." (6 Summary)

## Claim tuples

- H: Gas and dust cavities have different sizes | E: Separate model fits of 880 um continuum visibilities and CO 3-2 cube | R: RCO=31 AU vs Rcav=79 AU | F: Gas cavity is about half the dust cavity; rules out grain growth as main mechanism | **supported**
- H: Dust mass is radially concentrated, consistent with a pressure trap | E: Cumulative mass of fitted models for gamma=0.5,1,1.5 | R: 80% of dust mass in 79-114 AU; most compact among 13 disks | F: Consistent with planet-induced pressure bump | **partially**
- H: Depressed CO in the cavity reflects gas depletion rather than temperature | E: Argument from CO 4.7 um non-detection and physical plausibility | R: No hot CO detected with Keck NIRSPEC | F: Gas is largely depleted inside the cavity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust and CO fit separately because they probe different optical depths and regions  
  > "For this reason, we fit models to the dust and CO observations in separate steps." (4 Modeling Analysis)
- Alternative: Grain growth, photoevaporation and brown dwarf companions disfavored; planet-disk interaction favored  
  > "We thus compare the CO and dust radial structure with the predictions of disk tidal interactions with planets." (5.2 Formation of the J1604-2130 transition disk)
- How they decided it was enough: _not stated_
- Limitation (authors): Fit uncertainties underestimate true uncertainty due to gamma degeneracy  
  > "Thus the uncertainties in Table [1](#table:paras) should be used with caution." (4.5 Uncertainties from the choice of $\gamma$)
- Caveat (inferred, ours): Parametric CO temperature and fixed gas-to-dust ratio of 100 drive the gas cavity inference
- Caveat (inferred, ours): Inclination fixed at 6 deg and PA fixed from CO
- Caveat (inferred, ours): Formal errors very small and not representative
- Caveat (inferred, ours): Single short 315 s observation; discrepant IRAC vs WISE SED affects Rgap

## Reproducibility

- Data public (paper): ALMA Cycle 0 archival project cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00526.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom Fourier-domain LM/MCMC fitting code (Isella09) not released
- Missing: SED photometry table not given
- Missing: Priors and parameter bounds
- Data volume (inferred): ~10-30 GB raw Cycle 0 single-execution data
- Score (inferred): 3/5, Data public and models described, but fitting code, priors, SED data and imaging details missing.
- Rediscovery candidate: no, Requires custom radiative-transfer fitting code and unspecified settings.

## Links

- Method: Isella et al. 2009 (cite: Isella09) (Fourier-domain fitting procedure and surface density parameterization)
- Method: Isella et al. 2007 (cite: Isella07) (CO emission model)
- Method: Pietu et al. 2007 (cite: Pitu07) (LM/MCMC and Hessian uncertainty method)
- Companion: Mathews et al. 2012 (cite: Mathews12) (Previous SMA study of this disk and base dust model)
- Companion: Carpenter et al. 2014 (cite: Carpenter14) (Parent ALMA Upper Sco survey data)
- Related: ALMA Cycle 0 project 2011.0.00526.S

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 61,
  "rate": 0.744
 },
 "evidence_ok": true
}
```
