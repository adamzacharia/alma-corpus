# ALMA High-resolution Observation for the Transitional Disk Around IRAS 04125+2902

`2025ApJ...993...90S` | The Astrophysical Journal 2025 | first author: Shoshi, Ayumu | arXiv: 2509.01896 | DOI: 10.3847/1538-4357/ae045a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: What are the dust and gas structures of the transitional disk around the transiting-planet host IRAS 04125+2902, and is there an inner disk misaligned with the outer disk?  
  > "we use the same observation data, including dust continuum and $^{12}$CO $J$=2–1, to investigate the dust and gas structures in greater detail." (Introduction)
- Target **IRAS 04125+2902**: coordinates _not stated_; z/distance 160.1 pc  
  > "located at 160.1 pc from the Sun (cite: Gaia_2023)" (Introduction); distance from Gaia (Gaia_2023)  
  > "located at 160.1 pc from the Sun (cite: Gaia_2023)" (Introduction)

## Data provenance

- ALMA projects: 2022.1.01302.S
- bands: Band 6 (1.3 mm)  
  > "We used a subset of ALMA archival Band 6 data" (2.1 Data Reduction)
- frequencies and spectral setup: Continuum SPWs at 218 and 233 GHz, 2 GHz each; line SPWs of 0.23 GHz at 219.99 and 230.53 GHz  
  > "two SPWs with the central frequencies of 218 and 233 GHz and the bandwidth of 2 GHz each for imaging dust continuum" (2.2.1 CLEAN); "two SPWs with bandwidths of 0.23 GHz and central frequencies of 219.99 and 230.53 GHz" (2.3 Imaging Molecular Line Emission)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C-6 and C-7  
  > "using the C-6 and C-7 configurations, with baselines ranging from 27 m to 3638 m" (2.1 Data Reduction)
- baselines: _not stated_
- angular resolution: CLEAN continuum beam 0.151''x0.107'', PA 21.0 deg; SpM effective 0.109''x0.090''  
  > "The beam size is $0.151\ensuremath{''}\times0.107\ensuremath{''}$ with a position angle (PA) of 21.0$^\circ$" (2.2.1 CLEAN)
- max recoverable scale: ~2.1 arcsec  
  > "within the maximum recoverable scale ($\sim$2.1 arcsec)" (2.2.2 Sparse Modeling)
- sensitivity: continuum rms 1.0 mJy arcsec^-2 (~19 uJy/beam); CO 3.8 mJy/beam at 0.2 km/s  
  > "the RMS noise level ($\sigma_{\rm dust}$) is 1.0 mJy arcsec$^{-2}$ ($\sim$19 $\mu$Jy beam$^{-1}$)" (2.2.1 CLEAN)
- time on source: ~30 minutes  
  > "an on-source integration time of approximately 30 minutes" (2.1 Data Reduction)
- observing dates: 2023 May 21 and 23  
  > "Observations were conducted on May 21st and May 23rd, 2023" (2.1 Data Reduction)
- pi or archival as stated: Archival, PI Gijs D. Mulders  
  > "ALMA archival Band 6 data from the Cycle 9 project #2022.1.01302.S (PI: Gijs D. Mulders)" (2.1 Data Reduction)
- Line: 12CO J=2-1 (not stated)
- Other facility **VLASS (VLA)**: 2-4 GHz non-detection, rms 70 uJy/beam, used as upper limit for free-free test  
  > "We extracted the dataset from the Very Large Array Sky Survey (VLASS) project (cite: Lacy_2020), which had an RMS noise level of 70 $\mu$Jy beam$^{-1}$" (5.1 Presence of the Inner Disk)
- External data: SMA 345 GHz flux ~41.0±1.0 mJy used for spectral index  
  > "Based on the flux density of the SMA observations in (cite: Espaillat_2015) ($\sim$41.0$\pm$1.0 mJy at 345 GHz)" (3.1 1.3 mm Dust Continuum) [from (cite: Espaillat_2015)]
- External data: Stellar mass 0.7 Msun for Keplerian curve; planet and binary inclinations ~90 deg  
  > "The Keplerian curve for a stellar mass $M_\ast$=0.7 $M_\odot$ (cite: Barber_2024)" (3.2 12CO J=2-1 Emission) [from (cite: Barber_2024)]
- External data: Stellar luminosity 0.4-0.5 Lsun used for RADMC temperature  
  > "estimated from the stellar luminosity $L_\ast$=0.4-0.5 $L_\odot$ (cite: Espaillat_2015; Testi_2022)" (5.2 Inner Disk Shadow) [from (cite: Espaillat_2015; Testi_2022)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA  
  > "The raw data were calibrated using the ALMA pipeline within the Common Astronomy Software Applications package (cite: CASA_2022)." (2.1 Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute calibration error assumed  
  > "attributed to a 10% absolute calibration error in ALMA observations" (3.1 1.3 mm Dust Continuum)
- self calibration: Two rounds: phase-only with solint = on-source time, then amp+phase with OST/5  
  > "we applied phase self-calibration (`calmode=p`) with an integration time equal to the on-source time (OST). Next, we performed amplitude and phase self-calibration (`calmode=ap`) with an integration time of OST/5." (2.2.1 CLEAN)

### Imaging

- task: tclean (CASA 6.1.0), MFS, Cotton-Schwab  
  > "The continuum data were imaged using the CASA task `tclean` of CASA version 6.1.0." (2.2.1 CLEAN)
- deconvolver: multi-scale for line  
  > "we used `tclean` with Briggs weighting (`robust`=0.5) and the `multi-scale` algorithm." (2.3 Imaging Molecular Line Emission)
- weighting robust: Briggs robust=0.5 (continuum and line)  
  > "using Briggs weighting with `robust`=0.5" (2.2.1 CLEAN)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh for line  
  > "Mask regions for CLEAN imaging were automatically determined using the `auto-multithresh` scheme" (2.3 Imaging Molecular Line Emission)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO velocity resolution rebinned to 0.6 km/s with imrebin for channel maps  
  > "The velocity resolution was adjusted using the CASA task `imrebin`." (3.2 12CO J=2-1 Emission)
- final beam: CO beam 0.155''x0.106'', PA 27.4 deg  
  > "$0.155\ensuremath{''}\times0.106\ensuremath{''}$ with a PA of 27.4$^\circ$" (2.3 Imaging Molecular Line Emission)
- final rms: 1.0 mJy arcsec^-2 continuum; 3.8 mJy/beam CO  
  > "The RMS noise level ($\sigma_{\rm CO}$) at a velocity resolution of 0.2 km s$^{-1}$ was 3.8 mJy beam$^{-1}$." (2.3 Imaging Molecular Line Emission)

### Inherited from earlier work

- SpM imaging l1+TSV with cross-validation methodology  
  > "following the methodology of (cite: Yamaguchi_2024) and (cite: Shoshi_2025)" (2.2.2 Sparse Modeling) [from (cite: Yamaguchi_2024); (cite: Shoshi_2025)]
- Ellipse fitting of ring for inclination and PA  
  > "following the method described in (cite: Yamaguchi_2021) and (cite: Shoshi_2024)" (3.1 1.3 mm Dust Continuum) [from (cite: Yamaguchi_2021); (cite: Shoshi_2024)]
- Gas mass lower limit method  
  > "Following the method of (cite: Dunham_2014), we derived a lower limit to the gas mass" (3.2 12CO J=2-1 Emission) [from (cite: Dunham_2014)]
- Curve-growth for gas flux and radius on redshifted component  
  > "to determine the flux and the radius of the gas disk, following (cite: Deng_2025)" (3.2 12CO J=2-1 Emission) [from (cite: Deng_2025)]

### Not stated but needed to reproduce (our reading)

- Number of CLEAN iterations, threshold, cell and image size, masks for continuum
- Pipeline version and flux calibrator
- Line-free channels / continuum subtraction for CO
- Multi-scale scales for CO
- Priors on the protomidpy MCMC and Fourier-Bessel setup
- RADMC-3D photon counts, grid extent, dust-to-gas details
- Gridding and range of hyperparameter search for SpM
- Exact moment-map thresholds and clipping

## Analysis recipe

1. **CLEAN continuum imaging with self-calibration**: tclean MFS, Briggs, two rounds self-cal  
  > "We consistently employed multi-frequency synthesis (cite: Rau_2011) and the Cotton-Schwab algorithm (cite: Schwab_1984), using Briggs weighting with `robust`=0.5." (2.2.1 CLEAN)
   - software: CASA
   - parameter: robust=0.5; final peak SNR 62.3  
  > "(the final peak SNR=62.3)" (2.2.1 CLEAN)
   - fitting: _not stated_
   - validation: SNR improved by factor 1.5 after self-cal  
  > "The final continuum image shows an improvement in SNR by a factor of 1.5 after self-calibration" (2.2.1 CLEAN)
2. **Super-resolution sparse modeling image**: PRIISM l1+TSV imaging with 10-fold cross validation  
  > "We selected the optimal combination for each image by minimizing the cost function using the 10-fold CV approach" (2.2.2 Sparse Modeling)
   - software: PRIISM, CASA
   - parameter: (Lambda_l, Lambda_tsv)=(1e5, 1e13)  
  > "we obtained the final model image with $(\Lambda_l, \Lambda_{tsv})=(10^5, 10^{13})$" (2.2.2 Sparse Modeling)
   - fitting: Cost-function minimization with cross-validated hyperparameters  
  > "We selected the optimal combination for each image by minimizing the cost function using the 10-fold CV approach" (Sparse Modeling)
   - validation: Point-source injection (5% of total flux) to get effective resolution 0.109''x0.090''  
  > "we adopted the ‘point-source injection’ method, as described in (cite: Yamaguchi_2021)" (2.2.2 Sparse Modeling)
3. **Disk geometry and ring/flux/radius measurement and dust mass**: Ellipse fit to ring, Gaussian fit to deprojected radial profile, curve-of-growth flux and R95, optically thin dust mass  
  > "We then applied the curve-growth method (cite: Ansdell_2016) to measure the flux density $F_\nu$ and the disk radius $R_{95\%, {\rm dust}}$" (3.1 1.3 mm Dust Continuum)
   - software: SciPy
   - assumption: kappa=2.3 cm^2/g, T_dust=20 K, d=160.1 pc, optically thin  
  > "We adopted $T_{\rm dust}$=20 K, which is the standard value for Class II systems (cite: Pascucci_2016)." (3.1 1.3 mm Dust Continuum)
   - fitting: scipy optimize.leastsq Gaussian  
  > "We applied the Gaussian fitting using the `optimize.leastsq` function in the `Scipy` module" (3.1 1.3 mm Dust Continuum)
   - validation: _not stated_
4. **12CO kinematics and gas mass**: Moment maps, PV diagram vs Keplerian curves, LTE optically thin column density, curve of growth on redshifted side doubled  
  > "Assuming that $F_{^{12}\rm CO,red}$ is half of the total gas flux density, we then obtained the corrected total gas flux density" (3.2 12CO J=2-1 Emission)
   - software: CASA
   - parameter: 3 sigma_CO threshold  
  > "measured in the region exceeding 3 $\sigma_{\rm CO}$" (3.2 12CO J=2-1 Emission)
   - assumption: X_CO=1e-4, T_ex=50 K; alternative CO-to-H2 factor 2.0e20  
  > "Assuming $X_{\rm CO}$=10$^{-4}$ (cite: Frerking_1982) and $T_{\rm ex}$=50 K (cite: Ginsburg_2011)" (3.2 12CO J=2-1 Emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **1D axisymmetric brightness model from visibilities**: protomidpy Fourier-Bessel series with Gaussian Process kernel, MCMC, baselines limited to 1.2 Mlambda; residual dirty map via tclean zero iterations  
  > "These six parameters are simultaneously estimated using Bayesian inference with Markov Chain Monte Carlo (MCMC) to derive the optimal 1D model." (4.1 1D Visibility Analyses Methods)
   - software: protomidpy, CASA
   - parameter: 1000 iterations, 32 walkers, init from SpM cos i and PA  
  > "we set the number of iterations to 1000 and the number of walkers to 32." (4.1 1D Visibility Analyses Methods)
   - fitting: MCMC over 6 parameters (center, cos i, PA, alpha, gamma)  
  > "These six parameters are simultaneously estimated using Bayesian inference with Markov Chain Monte Carlo (MCMC) to derive the optimal 1D model." (1D Visibility Analyses Methods)
   - validation: Compared baseline cuts of 1.0, 1.2, 1.5 Mlambda and full data; 1.2 gave fewest artifacts  
  > "the model with a 1.2 M$\lambda$ baseline exhibits the fewest negative components and sidelobes with relatively weak intensity." (Data Flag for Disk Modeling)
6. **Free-free test with VLASS**: Spectral index between VLASS 70 uJy upper limit and 0.13 mJy SpM inner flux  
  > "the spectral index calculated from it and the flux of 0.13 mJy measured in the SpM image was approximately 0.14" (5.1 Presence of the Inner Disk)
   - fitting: _not stated_
   - validation: _not stated_
7. **Radiative transfer test of inner-disk misalignment**: RADMC-3D mctherm with Gaussian ring surface densities, inner disk tilted by Delta i of 10 and 50 deg, convolved to SpM resolution  
  > "We used `RADMC-3D` `mctherm` run to recalculate the temperature profile of the disk and then obtained a model image." (5.2 Inner Disk Shadow)
   - software: RADMC-3D, astropy
   - parameter: T0=230 K at 1 au with r^-0.5; Mstar=1.0 Msun; inner r_peak 3 au sigma 2 au; outer r_peak 41 au sigma 5 au; Delta PA=-18.8 deg  
  > "We used the fixed values of $r_{\rm preak, in}$=3.0 au and $\sigma_{\rm in}$=2.0 au." (5.2 Inner Disk Shadow)
   - assumption: f_set=1.0, amorphous olivine opacity (50% Mg, 50% Fe)  
  > "we used the models of amorphous olivine with 50% Mg and 50% Fe (cite: Jaeger_1994; Dorschner_1995)" (5.2 Inner Disk Shadow)
   - fitting: Hand-tuned Sigma_in to match 0.13 mJy (<15 au) and 13.0 mJy (<60 au); no formal fit  
  > "we adjusted $\Sigma_{\rm d, in}$ so that the final model image reproduces the flux densities within $r<$ 15 au and $r<$ 60 au measured in the SpM image" (Inner Disk Shadow)
   - validation: Qualitative comparison of asymmetry and radial profile with observations; Delta i=10 deg matches better  
  > "The peak intensity profile of the RADMC model seems to match better in the case of $\Delta i_{\rm disk}$=10$^\circ$ than in the case of $\Delta i_{\rm disk}$=50$^\circ$" (5.2 Inner Disk Shadow)

## Software

- **CASA** 6.1.0: Calibration, tclean imaging, imrebin  
  > "CASA task `tclean` of CASA version 6.1.0" (2.2.1 CLEAN)
- **PRIISM** 0.11.5: Sparse modeling imaging  
  > "version 0.11.5 on CASA version 6.1.0" (2.2.2 Sparse Modeling)
- **protomidpy** : 1D brightness profile modeling  
  > "We used `protomidpy`[^2], (cite: Aizawa_2024), to reconstruct the radial surface brightness distribution" (4.1 1D Visibility Analyses Methods)
- **RADMC-3D** : Radiative transfer models  
  > "using `RADMC-3D` (cite: Dullemond_2012)" (5.2 Inner Disk Shadow)
- **SciPy** : Gaussian fits of radial profile  
  > "`optimize.leastsq` function in the `Scipy` module" (3.1 1.3 mm Dust Continuum)
- **astropy** : Convolution of RADMC model images  
  > "using `convolution.Gaussian2DKernel` and `convolution.convolve` from the `astropy` module" (5.2 Inner Disk Shadow)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inclination | 35.6 | 0.2 | deg | 3 | The values of $i_{\rm disk}$ and PA$_{\rm disk}$ were estimated to be 35.6$\pm$0.2$^\circ$ and 175.1$\pm$0.5$^\circ$ |
| Disk PA | 175.1 | 0.5 | deg | 3 | 175.1$\pm$0.5$^\circ$ |
| Ring FWHM (SpM) | 21.7 | 7.4 | au | 3 | the width (FWHM) of the ring in the SpM image was estimated to be 21.7$\pm$7.4 au |
| Dust flux density | 13.0 | 1.3 | mJy | 3 | $F_\nu$=13.0$\pm$1.3 mJy |
| Dust R95% | 52.8 | 7.4 | au | 3 | $R_{95\%, {\rm dust}}$=52.8$\pm$7.4 au |
| Dust mass | 3.0e-5 Msun (10.1 Mearth) | not stated | Msun | 3 | We then obtained $M_{\rm dust}\sim$3.0$\times$10$^{-5}$ $M_\odot$ ($\sim$10.1 $M_\oplus$). |
| Spectral index (SMA 345 to ALMA 225 GHz) | ~2.7 | not stated | dimensionless | 3 | we estimated the spectral index of $\sim$2.7 |
| Systemic velocity | ~7.7 | not stated | km/s | 4 | We estimated that the systemic velocity was $\sim$7.7 km s$^{-1}$. |
| Gas disk R95% | 98.4 | 10.5 | au | 4 | $R_{95\%,\rm gas}$ to be $98.4\pm10.5\,{\rm au}$ |
| Corrected 12CO flux | 702.2 | 5.9 | mJy km/s | 4 | $F_{^{12}\rm CO}^{\rm corr}=702.2\pm5.9\,{\rm mJy\,km\,s^{-1}}$ |
| Gas mass lower limit | 0.2-5.8e-5 | not stated | Msun | 4 | We therefore consider that the lower limit of gas mass is 0.2-5.8$\times 10^{-5}\,M_{\odot}$. |
| Stellar dynamical mass | 0.7-1.0 | not stated | Msun | 4 | the dynamical mass of the central star is estimated to be 0.7-1.0 $M_{\odot}$ |
| Ring width (1D model) | 17.4 | 3.9 | au | 5 | we estimated the ring width in the 1D model image to be 17.4$\pm$3.9 au |
| 1D model cos i | 0.825 | +0.0029/-0.0028 | dimensionless | 5 | $\cos i=0.825^{+0.0029}_{-0.0028}$ |
| 1D model gamma | 0.058 | +0.012/-0.014 | arcsec | 5 | $\gamma=0.058^{+0.012}_{-0.014}$ arcsec |
| Spectral index inner emission vs VLASS limit | ~0.14 | not stated | dimensionless | 6 | was approximately 0.14 |

## Qualitative findings

- Ring-gap transitional disk with weak emission in the gap, nearly face-on  
  > "The dust continuum emission reveals a ring-gap transitional disk structure with an inclination of 35.6$^{\circ}$." (abstract)
- Weak asymmetry and no velocity distortion imply any inner disk is not highly misaligned  
  > "suggesting that the inner disk, if it exists, is not highly inclined with respect to the outer disk" (abstract)

## Claim tuples

- H: Is there emission inside the dust gap? | E: SpM imaging and protomidpy 1D modeling | R: Weak inner emission ~10x fainter than ring, ~0.13 mJy within 15 au | F: Inner emission exists; origin may be inner disk but free-free not ruled out | **partially**
- H: Is the outer disk misaligned with the planet and binary orbits? | E: Ring ellipse fitting | R: i=35.6±0.2 deg versus ~90 deg for planet and binary | F: Outer disk is nearly face-on and misaligned | **supported**
- H: Can a modestly misaligned inner disk explain weak asymmetry? | E: RADMC-3D models with Delta i = 10 and 50 deg | R: Both give weak asymmetry; 10 deg matches profile better | F: ~10 deg misalignment possible; preliminary | **partially**
- H: Is gas present within the ring, and what is the stellar mass? | E: 12CO moment maps, PV, LTE mass | R: Keplerian with 0.7-1.0 Msun, gas mass lower limit 0.2-5.8e-5 Msun | F: Non-negligible gas remains in the inner region | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: SpM gives super-resolution beyond CLEAN  
  > "to reconstruct a super-resolution image surpassing the CLEAN image in quality" (2.2.2 Sparse Modeling)
- Alternative: Baseline cuts of 1.0, 1.5 Mlambda and full data rejected for 1D modeling due to artifacts  
  > "Thus, we did not adopt the disk model derived from the full observed visibility." (Data Flag for Disk Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): 12CO affected by foreground absorption; gas mass a lower limit  
  > "We note that the value of $M_{{\rm H}_2}$ represents a lower limit due to the absorption or depletion of $^{12}$CO emission." (3.2 12CO J=2-1 Emission)
- Limitation (authors): Dust mass depends heavily on opacity and temperature  
  > "depends heavily on the assumed opacity and temperature" (3.1 1.3 mm Dust Continuum)
- Caveat (inferred, ours): Inner emission is only about resolution-sized and could be a SpM/uv artifact or free-free
- Caveat (inferred, ours): RADMC models were hand-tuned, not fitted, with fixed DeltaPA from a weak dip
- Caveat (inferred, ours): Table lists i=35.2 while text gives 35.6
- Caveat (inferred, ours): Ring width text 21.7 vs 21.4 inconsistent
- Caveat (inferred, ours): Gas mass relies on 12CO that is affected by absorption

## Reproducibility

- Data public (paper): Archival ALMA data from project 2022.1.01302.S  
  > "We used a subset of ALMA archival Band 6 data from the Cycle 9 project #2022.1.01302.S" (2.1 Data Reduction)
- Products in archive: _not stated_
- Code: PRIISM and protomidpy are public on GitHub; the authors' own analysis scripts are not stated  
  > "[^1]: <https://github.com/tnakazato/priism>" (2.2.2 Sparse Modeling)
- Missing: CLEAN cell/image size, iterations, thresholds
- Missing: Line-free channels and CO continuum subtraction
- Missing: protomidpy priors
- Missing: RADMC-3D numerical settings
- Missing: Pipeline version and calibrators
- Data volume (inferred): ~10-50 GB for the subset of one target in the archive (calibrated MS smaller)
- Score (inferred): 3/5, Public data and many parameters are given, but key imaging and fitting settings are missing and some values are inconsistent.
- Rediscovery candidate: yes, Public data, main results numeric (inclination, flux, R95, dust mass), and the recipe is largely stated.

## Links

- Method: (cite: Yamaguchi_2021) (SpM imaging, ellipse fitting and point-source injection)
- Method: (cite: Aizawa_2024) (protomidpy 1D visibility modeling)
- Method: (cite: Dunham_2014) (gas mass from CO)
- Companion: Bosschaart et al. (submitted) (survey paper presenting the same ALMA dataset)
- Companion: (cite: Barber_2024) (discovery of the transiting planet)
- Related: ALMA 2022.1.01302.S (PI Mulders)
- Related: VLASS

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 67,
  "rate": 0.728
 },
 "evidence_ok": true
}
```
