# Comparisons between Resolved Star Formation Rate and Gas Tracers in the Strongly Lensed Galaxy SDSS J0901+1814 at Cosmic Noon

`2024ApJ...972..147C` | The Astrophysical Journal 2024 | first author: Chen, Qingxiang | arXiv: 2407.01685 | DOI: 10.3847/1538-4357/ad5ceb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How do the choices of SFR tracer (Halpha, 1.2 mm IR, radio continuum) and gas tracer (CO, CI) change the resolved Schmidt-Kennicutt relation in lensed galaxy J0901 at z=2.26?  
  > "In order to constrain the effects of observational tracer choice in measuring the Schmidt-Kennicutt relation at high redshift, we have observed a single galaxy using three SFR tracers" (Introduction)
- Target **SDSS J090122.37+181432.3 (J0901)**: coordinates VLA pointing centre RA 09h01m22.45s, Dec +18d14m31.5s  
  > "a strongly lensed star-forming galaxy at $z=2.26$" (abstract); z/distance z=2.26 (Halpha systemic z=2.2586)  
  > "a strongly lensed star-forming galaxy at $z=2.26$" (abstract); distance from Hainline et al. 2009 Halpha redshift  
  > "a strongly lensed star-forming galaxy at $z=2.26$" (abstract)

## Data provenance

- ALMA projects: 2013.1.00952.S
- bands: Band 6 (1.2 mm)  
  > "(observed frequency , or ${\lambda_{\rm obs}\sim1.2\,{\rm mm}}$; band 6)" (3 ALMA Observations & Data Reduction)
- frequencies and spectral setup: CO(7-6) centred at 247.5 GHz in upper sideband; lower sideband centred at 232.9 GHz for continuum; 488.281 kHz channels in upper sideband  
  > "The lower sideband was centered at $232.9\,{\rm GHz}$ to capture continuum emission." (3 ALMA Observations & Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12m Array, ACA 7m and Total Power  
  > "with both the 12m Array and Atacama Compact Array (including both the 7m and Total Power Arrays)" (3 ALMA Observations & Data Reduction)
- configurations: _not stated_
- baselines: 15.1–348.5 m (12m)  
  > "Baseline lengths for the then-available 36 antennas ranged from $15.1$–$348.5\,{\rm m}$." (3 ALMA Observations & Data Reduction)
- angular resolution: 1.6x1.0 arcsec (lines), 1.7x1.1 arcsec (continuum)  
  > "$1.\ensuremath{''}7\times1.\ensuremath{''}1$ at a position angle of $58^{\degree}$ for the continuum map" (3 ALMA Observations & Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.47 mJy/beam (CO 7-6), 0.61 mJy/beam (CI) per 14 km/s channel; 35 uJy/beam continuum  
  > "for a final map noise of $35\,{\rm \mu Jy\,beam^{-1}}$ over the nearly $4\,{\rm GHz}$ of bandwidth" (3 ALMA Observations & Data Reduction)
- time on source: 12m 34 min; 7m 66 min; TP 5.5 hr  
  > "Observations using the 12m Array were taken on 2014 April 30 for a total of $34\,{\rm minutes}$ on source." (3 ALMA Observations & Data Reduction)
- observing dates: 12m 2014 Apr 30; 7m 2014 Apr 30, May 2, May 19; TP Dec 2014–Jan 2015  
  > "Observations using the 7m Array were taken on 2014 April 30, May 2, and May 19" (3 ALMA Observations & Data Reduction)
- pi or archival as stated: Cycle 2 project, PI Sharon  
  > "J0901 was observed during ALMA Cycle 2" (3 ALMA Observations & Data Reduction)
- Line: CO 7-6 (not stated)
- Line: CI 3P2-3P1 (not stated)
- Other facility **VLA**: 1.4 GHz and 3 GHz continuum maps  
  > "Our VLA observations were taken in S-band ($\nu_{\rm obs}=3\,{\rm GHz}$) and L-band ($\nu_{\rm obs}=1.4\,{\rm GHz}$)." (2 VLA Continuum Observations & data reduction)
- External data: Herschel IR photometry, L_TIR=1.8e12 Lsun, T_dust=36 K  
  > "We adopt the total infrared (TIR) luminosity from (cite: Saintonge:2013a)" (5.2 The Infrared-Radio Correlation) [from (cite: Saintonge:2013a)]
- External data: ALMA Band 3 continuum flux density 1.47±0.19 mJy  
  > "which yields $S_{\rm 3\,mm}=\rm 1.47\pm 0.19\,m Jy$" (5.1 Radio Spectrum) [from (cite: Liu:2023a)]
- External data: CO(1-0), CO(3-2) maps, r31 and gas mass, lens models, Halpha maps  
  > "CO(1–0) line fluxes and the $r_{3,1}$ values are from ." (Table 7 notes) [from previous J0901 paper (citation key lost in text; Sharon et al. 2019 likely)]
- External data: Ka-band 35 GHz continuum  
  > "We therefore combine these VLA continuum flux density measurements with the Ka-band (${\nu_{\rm obs}=35\,{\rm GHz}}$) continuum emission detected in" (5.1 Radio Spectrum) [from earlier paper (key lost)]

## Processing

### Calibration

- pipeline or manual: 12m: NAASC script with manual inspection; 7m: observatory script; TP: observatory-provided manual calibration  
  > "we used a script provided by the North American ALMA Science Center and CASA version 4.5.0 in order to more closely examine the outputs of the pipeline calibration." (3 ALMA Observations & Data Reduction)
- casa version: 12m CASA 4.5.0; 7m CASA 4.2.2; imaging CASA 4.5.0  
  > "we used the observatory-generated calibration script for CASA version 4.2.2" (3 ALMA Observations & Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 12m: Ganymede; 7m: Pallas or Ceres  
  > "Ganymede was used for amplitude and flux calibration" (3 ALMA Observations & Data Reduction)
- flux scale uncertainty: 10% for band 6  
  > "We assume the standard 10% flux scale uncertainties for band 6" (3 ALMA Observations & Data Reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (ALMA)  
  > "We used natural weighting to produce the final maps (in CASA 4.5.0)" (3 ALMA Observations & Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane continuum subtraction, separately for 12m and 7m  
  > "continuum subtraction was performed separately for the 12m and 7m Array data" (3 ALMA Observations & Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m and 7m combined; Total Power excluded  
  > "we did not include the Total Power data when making our final maps" (3 ALMA Observations & Data Reduction)
- smoothing: channels binned to 14 km/s (11.5 MHz)  
  > "We binned the frequency axis into $14\,{\rm km\,s^{-1}}$ ($11.5\,{\rm MHz}$) channels" (3 ALMA Observations & Data Reduction)
- final beam: 1.6x1.0 arcsec PA 58 (lines); 1.7x1.1 arcsec PA 58 (continuum)  
  > "$1.\ensuremath{''}6\times1.\ensuremath{''}0$ at a position angle of $58^{\degree}$ for the two emission lines" (3 ALMA Observations & Data Reduction)
- final rms: 35 uJy/beam continuum; 0.47 and 0.61 mJy/beam per 14 km/s channel  
  > "our final average per-channel noise is $0.47\,{\rm mJy\,beam^{-1}}$ for the CO(7–6) line" (3 ALMA Observations & Data Reduction)

### Inherited from earlier work

- Radio SED decomposition and MCMC method, Gaussian prior on alpha_NT (mean -0.85, sd 0.5)  
  > "we fit the emission to FF and non-thermal components using the methods in (cite: Algera:2021a)." (5.1 Radio Spectrum) [from (cite: Algera:2021a)]
- Modified blackbody fitting for dust contribution at 35 GHz  
  > "we employ the modified blackbody (MBB) fitting procedure outlined in (cite: Algera:2023a)" (5.1 Radio Spectrum) [from (cite: Algera:2023a)]
- Schmidt-Kennicutt fitting method  
  > "we employ the methodology described in (cite: Leroy:2013a) (which was based on (cite: Blanc:2009a)) as modified in ." (5.6 Schmidt-Kennicutt relation) [from (cite: Leroy:2013a); (cite: Blanc:2009a); modification from earlier J0901 paper]
- LVG grid modelling  
  > "The sample spacing and ranges probed are the same as in (cite: Sharon:2015a)." (5.5 CO SLED) [from (cite: Sharon:2015a)]
- Lens models and magnification (mu~30)  
  > "the lensing models presented in ." (Introduction) [from earlier J0901 paper (key lost)]

### Not stated but needed to reproduce (our reading)

- ALMA clean thresholds, mask, cell and image size
- Line-free channels for ALMA continuum subtraction
- Aperture definitions for flux extraction
- Lens models and magnification maps (cited, not given)
- Halpha, CO(1-0), CO(3-2) maps used in the S-K fits
- Number of MCMC walkers/steps and sampler
- Gridding of the S-K parameters
- Smoothing kernels used for matching resolutions
- Rest frequencies used for the lines

## Analysis recipe

1. **Image ALMA continuum and line cubes**: Calibrate 12m and 7m data, natural-weighted imaging, uv continuum subtraction, bin to 14 km/s  
  > "We used natural weighting to produce the final maps (in CASA 4.5.0)" (3 ALMA Observations & Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line fluxes**: Double-Gaussian fits to line profiles per image  
  > "Fitting the combined line profiles to a double Gaussian gives integrated line fluxes" (4.2 Line detections)
   - fitting: Two Gaussians  
  > "Fitting the combined line profiles to a double Gaussian gives integrated line fluxes of $8.4\pm1.4\,{\rm Jy\,km\,s^{-1}}$ for the CO(7–6) line" (Line detections)
   - validation: _not stated_
3. **Decompose radio spectrum**: Smooth 1.4 and 3 GHz to the 35 GHz beam, add noise to match peak SNR, MCMC fit of FF + non-thermal power laws  
  > "We run a Markov chain Monte Carlo (MCMC) analysis to constrain the three fit parameters for the radio SED." (5.1 Radio Spectrum)
   - parameter: FF index fixed at -0.10; flat prior 0<=f_th<=1; Gaussian prior alpha_NT mean -0.85, sd 0.5  
  > "set a Gaussian prior on $\rm{\alpha^{NT}}$ with a mean of $-0.85$ and a standard deviation of 0.5" (5.1 Radio Spectrum)
   - fitting: MCMC, flat and Gaussian priors  
  > "We run two series of MCMC simulations, with flat and Gaussian priors on the non-thermal spectral index." (Summary)
   - validation: Cold-dust 35 GHz contribution checked with MBB and cmcirsed  
  > "We obtain similar results (20.9 $\rm \mu Jy$) when using the IR fitting tool `cmcirsed`" (5.1 Radio Spectrum)
4. **IRRC and radio SFRs**: q_TIR and Murphy et al. 2012 calibrations for FF, non-thermal and combined SFR  
  > "we can calculate and compare the radio-derived SFR from these two components following (cite: Murphy:2012a)" (5.3 Radio-derived Star Formation Rates)
   - assumption: Te=1e4 K, rest-frame 1.4 GHz, mu=30  
  > "which we assume to be $\rm 10^4\,K$." (Radio-derived Star Formation Rates)
   - fitting: _not stated_
   - validation: _not stated_
5. **Gas masses from CI and 1.2 mm**: Weiss et al. 2003 CI mass with X_CI; Scoville et al. 2016 dust-based mass  
  > "Following the work of (cite: Scoville:2016a), we calculate the gas mass using" (5.4 C i and 1.2 mm derived gas masses)
   - assumption: Tex=30 K, X_CI=6.8e-5, Td=36 or 25 K  
  > "We assume $T_{ex}=30\,{\rm K}$" (5.4 C i and 1.2 mm derived gas masses)
   - fitting: _not stated_
   - validation: Compared with CO(1-0) gas mass  
  > "This gas mass is consistent with the (magnification-corrected) CO(1–0)-derived gas mass of $(1.6^{+0.3}_{-0.2})\times10^{11}(\alpha_{\rm CO}/4.6)\,M_\ensuremath{\odot}$" (C i and 1.2 mm derived gas masses)
6. **LVG modelling of CO SLED**: Grid LVG with chi2 and Bayesian analysis  
  > "We use both minimum-$\chi^2$ and Bayesian analyses" (5.5 CO SLED)
   - assumption: spherical cloud, CMB heating  
  > "This model assumes a spherical cloud geometry and accounts for heating from the CMB." (CO SLED and radiative transfer modeling)
   - fitting: minimum chi2 / uniform priors; optional Tkin=Tdust prior  
  > "We use both minimum-$\chi^2$ and Bayesian analyses to evaluate how well each combination of model parameters reproduces our observations." (CO SLED and radiative transfer modeling)
   - validation: _not stated_
7. **Fit resolved Schmidt-Kennicutt relation**: Compare 2D histograms of data to model with perturbations; 100 repeats, third-order polynomial minima  
  > "We repeat this procedure 100 times, each time generating new statistical and flux calibration perturbations and excluding a randomly chosen pixel." (5.6 Schmidt-Kennicutt relation)
   - parameter: 10,000 resamplings; 2 sigma gas cut  
  > "we sample the per-pixel gas mass measurements 10,000 times (with replacement)" (Schmidt-Kennicutt relation)
   - assumption: SFR maps scaled to TIR total SFR (Kroupa IMF); gas maps scaled by CO line ratios  
  > "we scale each map such that its total SFR matches that determined from the TIR in (cite: Saintonge:2013a) with a Kroupa IMF" (Schmidt-Kennicutt relation)
   - fitting: chi2 minimisation over A, n, sigma  
  > "to calculate a $\chi^2$ goodness-of-fit statistic for all combinations of the three model parameters." (Schmidt-Kennicutt relation)
   - validation: Smoothing test: slopes flatten by at most ~10%  
  > "since the slopes flatten by at most $\sim10\%$ for the smoothing necessary to match all data" (Schmidt-Kennicutt relation)

## Software

- **CASA** 4.2.2, 4.5.0 (ALMA); 5.4.1-32 and 6.2.1.7 (VLA): calibration, tclean imaging, uvsub, widebandpbcor  
  > "We used the CASA (cite: McMullin:2007a) pipeline appropriate for the given observation date" (2.1 VLA S-band)
- **cmcirsed** : IR SED fit to check dust contribution at 35 GHz  
  > "using the IR fitting tool `cmcirsed` (cite: Casey:2012a)" (5.1 Radio Spectrum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.2 mm total flux density | 14 | 1.4 | mJy | 1 | $S_{\rm 1.2\,mm}=14\pm1.4\,{\rm mJy}$ |
| CO(7-6) integrated flux | 8.4 | 1.4 | Jy km/s | 2 | $8.4\pm1.4\,{\rm Jy\,km\,s^{-1}}$ for the CO(7–6) line |
| CI(2-1) integrated flux | 13.4 | 2.0 | Jy km/s | 2 | $13.4\pm2.0\,{\rm Jy\,km\,s^{-1}}$ |
| VLA 3 GHz flux density | 328 | 28 | uJy | 0 | ${S_{\rm 3\,GHz}=328\pm28\,{\rm \mu Jy}}$ |
| VLA 1.4 GHz flux density | 503 | 42 | uJy | 0 | ${S_{\rm 1.4\,GHz}=503\pm42\,{\rm \mu Jy}}$ |
| Non-thermal index (Gaussian prior) | -1.00 | +0.44/-0.45 | dimensionless | 3 | ${{\rm \alpha^{NT}=-1.00^{+0.44}_{-0.45}}}$ |
| Thermal fraction at rest 1.4 GHz | 0.31 | +0.31/-0.19 | dimensionless | 3 | ${0.31_{-0.19}^{+0.31}}$ |
| q_TIR | 2.65 | +0.24/-0.31 | dimensionless | 4 | ${q_{\rm TIR}=2.65_{-0.31}^{+0.24}}$ for J0901 |
| SFR free-free | 620 | +280/-220 | Msun/yr | 4 | ${\rm SFR^T}={620}_{-220}^{+280}\,M_\odot\,\rm{yr}^{-1}$ |
| SFR combined | 280 | +460/-120 | Msun/yr | 4 | $\rm{SFR^{T+NT}}={280}_{-120}^{+460}\,M_\odot\,{\rm yr}^{-1}$ |
| Gas mass from CI (X_CI=6.8e-5) | 1.22e11 | 0.18e11 | Msun | 5 | $M_{\rm gas}=(1.22\pm0.18)\times10^{11}(\mu/30)(6.8\times10^{-5}/X_{\rm C{\textsc i}})\,M_\odot$ |
| Gas mass from 1.2 mm (Td=25 K) | 6.65e10 | 0.67e10 | Msun | 5 | $(6.65\pm 0.67)(\mu/30)\times 10^{10}\,M_\odot$ |
| S-K slope, CO(1-0) vs 1.2 mm | 2.14 | 0.07 | dimensionless | 7 | / CO(1–0) / H$\rm \alpha$ / $4227$ / $52.6$ / $0.34\pm0.10$ / $1.74\pm0.07$ / $0.22\pm0.01$ / |
| S-K slope, CO(7-6) vs 1.4 GHz | 0.71 | 0.02 | dimensionless | 7 | / CO(7–6) / H$\rm \alpha$ / $2360$ / $29.4$ / $0.02\pm0.07$ / $1.00\pm0.04$ / $0.29\pm0.01$ / |

## Qualitative findings

- Radio continuum maps give the flattest S-K slopes, attributed to poorer spatial correspondence with other tracers  
  > "The flatter Schmidt-Kennicutt slopes for the radio continuum are likely driven by the poorer spatial correspondence between the radio emission and other gas and SFR tracers." (6 Summary)

## Claim tuples

- H: Is the radio continuum of J0901 star-formation dominated? | E: q_TIR, r parameter and radio spectral decomposition | R: q_TIR=2.65, r=21.2 below the AGN threshold | F: AGN is not a significant radio source | **supported**
- H: Do radio SFRs agree with the IR SFR? | E: Decomposition and Murphy calibrations | R: SFRs 620/230/280 Msun/yr vs 268 TIR | F: Consistent within large uncertainties, except for FF | **supported**
- H: Do CI and dust give gas masses consistent with CO(1-0)? | E: CI and 1.2 mm gas masses | R: CI 1.2e11 consistent; dust 2–3x lower | F: CI agrees; dust-based mass suggests lower alpha_CO | **partially**
- H: Does the S-K slope depend on gas and SFR tracers? | E: Pixel-by-pixel fits for 4 gas x 4 SFR tracers | R: 1.2 mm steepest, radio flattest; slope decreases with critical density | F: Mid- and high-J CO and CI are unsuitable for bulk gas in such galaxies | **supported**

## Reasoning

- Why this data: Radio is extinction-free SFR tracer; 1.2 mm maps obscured SF; CO(7-6) and CI give alternative gas probes  
  > "the long wavelength radio emission is a SFR tracer that should be free of dust attenuation effects" (Introduction)
- Why this method: _not stated_
- Alternative: Briggs0 and uniform weighting discarded for low SNR  
  > "Briggs0 and uniform weighting result in maps whose source region SNR is low" (2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): LVG parameters highly degenerate; large uncertainty in non-thermal index; unknown CI excitation  
  > "Due to the degeneracies in the LVG model, it is difficult to estimate uncertainties on the best-fit model parameters" (5.5)
- Caveat (inferred, ours): Single galaxy; conclusions may not generalise
- Caveat (inferred, ours): Many results depend on global scaling of maps to TIR SFR and CO line ratios
- Caveat (inferred, ours): Lensing model uncertainties and differential magnification not propagated
- Caveat (inferred, ours): ALMA lines at modest resolution; pixel correlations

## Reproducibility

- Data public (paper): ALMA project number given; VLA IDs 20A-289, 22A-157  
  > "(ID: 20A-289; PI C. Sharon)" (2 VLA)
- Products in archive: _not stated_
- Missing: Lens models
- Missing: Halpha, CO(1-0), CO(3-2) maps
- Missing: Details of S-K fitting code and grids
- Missing: ALMA imaging parameters
- Data volume (inferred): ALMA ~10s GB; VLA tens to hundreds GB
- Score (inferred): 3/5, ALMA data are archival and the radio steps are described, but the S-K inputs depend on unreleased maps and lens models.
- Rediscovery candidate: no, Key S-K analysis needs external maps and lens models not stated.

## Links

- Method: (cite: Algera:2021a) (radio SED decomposition)
- Method: (cite: Leroy:2013a) (S-K fitting method)
- Method: (cite: Scoville:2016a) (dust-based gas mass)
- Companion: (cite: Sharon:2019a) (previous resolved CO and Halpha study)

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
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 60,
  "rate": 0.706
 },
 "evidence_ok": true
}
```
