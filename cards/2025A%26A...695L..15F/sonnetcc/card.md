# Spatially resolved dust properties over 50 kpc in a hyperluminous galaxy merger at z = 4.6

`2025A&A...695L..15F` | Astronomy and Astrophysics 2025 | first author: Fernández Aranda, Román | arXiv: 2502.10503 | DOI: 10.1051/0004-6361/202453214

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the spatially resolved dust properties (mass, emissivity index, emitting area, temperature) across the ~50 kpc W2246-0526 hot DOG merger system, and what heats the dust in the hot DOG, streams and companions?  
  > "we present spatially resolved dust observations and properties for the entire W2246–0526 merging system over" (Introduction); "suggesting it is most likely heated by recent, in-situ star formation" (abstract)
- Target **WISE J224607.6-052634.9 (W2246-0526) hot DOG and its merging companions**: coordinates _not stated_; z/distance z = 4.6 (z=4.601 used for the CMB temperature)  
  > "W2246–0526), at redshift $z=4.6$" (abstract); "is the most distant known hot DOG" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00576.S, 2015.1.00883.S, 2016.1.00668.S, 2017.1.00899.S, 2018.1.00119.S, 2018.1.00333.S, 2019.1.00219.S, 2021.1.00726.S
- bands: Bands 3-10, eight datasets (rest-frame ~60 to ~600 um)  
  > "(bands 3–10)" (abstract); "detected in four of the eight datasets used in this work" (Observations and analysis)
- frequencies and spectral setup: Central rest-frame wavelengths 63, 88, 123, 149, 155, 211, 357, 572 um (Table 1); spectral windows not stated  
  > "(1) Central rest-frame wavelength" (Table 1)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array, multiple cycles  
  > "The W2246–0526 merger system was observed with the ALMA 12-m array during multiple cycles." (Observations and analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Native beams 0.54x0.46 to 0.35x0.30 arcsec (without uv-taper); homogenised to a common circular 1.0 arcsec beam  
  > "(4) Average size (FWHM) of the native beam, without uv-tapering" (Table 1); "to a common circular beam of FWHM=1.0" (Observations and analysis)
- max recoverable scale: 2.9 to 6.1 arcsec across the eight datasets (Table 1 MRS column)  
  > "(5) Maximum recoverable scale" (Table 1)
- sensitivity: Continuum rms of collapsed datasets from 0.007 to 1.36 mJy/beam (Table 1)  
  > "(3) Root mean square of the collapsed dataset" (Table 1)
- time on source: 30 to 380 min per dataset (Table 1)  
  > "(2) Integration time on-source" (Table 1)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Dust opacity kappa_850um = 0.0968 kg^-1 m^2 at nu_0 = 352.7 GHz, following Scoville et al. 2014  
  > "Following (cite: scoville2014) and assuming a gas-to-dust ratio of" (Observations and analysis); "we adopt $\kappa_0=\kappa_{850\upmu\mathrm{m}}=0.0968\ \mathrm{kg}^{-1} \mathrm{m}^2$ and $\nu_0 = 352.7$ GHz (850$\upmu\mathrm{m}$)" (Observations and analysis) [from (cite: scoville2014)]
- External data: Hot DOG metallicity ~0.5 Zsun, used to justify gas-to-dust ratio 200  
  > "given that the metallicity in the hot DOG is $\sim0.5$ Z$_{\odot}$ (cite: fernandez2024)" (Observations and analysis) [from (cite: fernandez2024)]

## Processing

### Calibration

- pipeline or manual: CASA with standard data reduction procedures; pipeline vs manual not specified  
  > "We reduced and calibrated the data using the Common Astronomy Software Applications (cite: mcmullin2007) with the standard data reduction procedures." (Observations and analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA v6.5 tclean, continuum imaging  
  > "To image the continuum using the tclean task of CASA v6.5" (Observations and analysis)
- deconvolver: Hogbom, cleaned to a threshold of 2 x rms of each cube  
  > "we ran the Hogbom cleaning algorithm (cite: 1974A&AS...15..417H) to a flux density threshold of two times the root mean square (rms) of each cube" (Observations and analysis)
- weighting robust: Briggs, robust = 2.0 (close to natural weighting)  
  > "with the Briggs weighting mode set to robustness = 2.0 (close to natural weighting)" (Observations and analysis)
- uv taper: 0.8 arcsec  
  > "with a uv-taper imaging weight equal to 0.8" (Observations and analysis)
- cell size: _not stated_
- image size: _not stated_
- masking: circular mask of radius 7 arcsec covering the whole merging system  
  > "The cleaning was done using a circular mask with a radius of 7" (Observations and analysis)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: all emission line-free channels combined for the continuum; channel ranges not given  
  > "all emission line-free channels were combined to create the continuum intensity maps" (Observations and analysis)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: common circular beam, FWHM = 1.0 arcsec, set as the restoring beam in tclean  
  > "matching the largest beam after the uv-tapering, by setting the restoring beam in" (Observations and analysis); "to a common circular beam of FWHM=1.0" (Observations and analysis)
- final rms: _not stated_

### Inherited from earlier work

- SFR estimated from L_IR using the Kennicutt & Evans 2012 calibration  
  > "The SFR is estimated from $L_{IR}$ as in (cite: kennicutevans2012)" (Results) [from as in (cite: kennicutevans2012)]
- Dust opacity kappa_850um adopted following Scoville et al. 2014  
  > "Following (cite: scoville2014) and assuming a gas-to-dust ratio of" (Observations and analysis) [from Following (cite: scoville2014)]

### Not stated but needed to reproduce (our reading)

- Whether the pipeline or manual calibration was used for each of the eight datasets, and the CASA version used for calibration
- Flux, bandpass and phase calibrators, absolute flux-scale uncertainties, and whether any flux uncertainty was added to the fit
- Self-calibration, if any, and the spectral windows and line-free channel ranges used for each continuum
- Cell size and image size for tclean, and whether primary-beam correction was applied
- How the central-beam flux densities in Table 1 were measured (aperture or single pixel, and how the uncertainties were derived)
- The pixel selection threshold for 'every pixel with emission' and how the per-pixel flux uncertainty was set
- emcee settings: likelihood form, number of walkers, steps, burn-in, convergence test, and how best-fit values and uncertainties were taken from the posterior
- How the Kennicutt & Evans 2012 conversion was applied (IMF, scaling) and how the CMB term was computed
- Whether the 2013.1.00576.S data, listed in the acknowledgements but not in Table 1, were used
- Luminosity distance value used (cosmology H0=70, Omega_M=0.3 given)

## Analysis recipe

1. **calibrate the ALMA data**: Reduce and calibrate each dataset with CASA using standard data reduction procedures  
  > "We reduced and calibrated the data using the Common Astronomy Software Applications (cite: mcmullin2007) with the standard data reduction procedures." (Observations and analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **image the continuum at a common 1.0 arcsec resolution**: tclean continuum imaging of line-free channels with Hogbom cleaning, Briggs weighting and a uv-taper, restored to a common circular beam  
  > "To image the continuum using the tclean task of CASA v6.5" (Observations and analysis); "all emission line-free channels were combined to create the continuum intensity maps" (Observations and analysis)
   - software: CASA tclean
   - parameter: robust = 2.0 (Briggs)  
  > "with the Briggs weighting mode set to robustness = 2.0 (close to natural weighting)" (Observations and analysis)
   - parameter: uv-taper 0.8 arcsec; restoring beam circular FWHM 1.0 arcsec  
  > "with a uv-taper imaging weight equal to 0.8" (Observations and analysis); "to a common circular beam of FWHM=1.0" (Observations and analysis)
   - parameter: clean threshold 2 x rms of each cube; circular mask radius 7 arcsec  
  > "to a flux density threshold of two times the root mean square (rms) of each cube" (Observations and analysis); "The cleaning was done using a circular mask with a radius of 7" (Observations and analysis)
   - fitting: _not stated_
   - validation: Extended structures detected in four of eight datasets; non-detections attributed to smaller maximum recoverable scales  
  > "The non-detection of the extended structures in the other four datasets may be due to smaller maximum recoverable scales in those observations" (Observations and analysis)
3. **fit a modified blackbody to the integrated central beam (hot DOG) with all eight datasets**: Fit the modified blackbody of Eq. 1 (area A, T_d, M_d, beta free; CMB contrast term included) to the eight central-beam fluxes  
  > "To characterize the FIR continuum emission in the system, we use a modified blackbody." (Observations and analysis); "for the integrated central beam, corresponding to the hot DOG, for which we have emission from all eight datasets" (Observations and analysis)
   - software: emcee
   - parameter: Flat priors 1e-2<A<33 kpc^2, 12.6<T_d<300 K, 1e6<M_d<1e10 Msun, 1<beta<3  
  > "flat priors of $10^{-2}<A<33$ kpc$^2$, $12.6<T_d<300$ K, $10^6<M_d<10^{10}$ $M_{\odot}$, and $1<\beta<3$" (Observations and analysis)
   - assumption: Gas-to-dust ratio 200 (hot DOG metallicity ~0.5 Zsun); kappa_850um = 0.0968 kg^-1 m^2 at 352.7 GHz  
  > "assuming a gas-to-dust ratio of $\delta_{GDR}=200$, given that the metallicity in the hot DOG is $\sim0.5$ Z$_{\odot}$ (cite: fernandez2024)" (Observations and analysis); "we adopt $\kappa_0=\kappa_{850\upmu\mathrm{m}}=0.0968\ \mathrm{kg}^{-1} \mathrm{m}^2$ and $\nu_0 = 352.7$ GHz (850$\upmu\mathrm{m}$)" (Observations and analysis)
   - assumption: Flat LCDM, H0 = 70 km/s/Mpc, Omega_M = 0.3; lower T limit set by T_CMB at z=4.601  
  > "we assume a flat $\Lambda$CDM cosmology with $H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$ and $\Omega_{\mathrm{M}}=0.3$" (Introduction); "the lower temperature limit corresponds to $T_{\mathrm{CMB}}$ at $z=4.601$" (Observations and analysis)
   - fitting: MCMC with emcee, four free parameters with flat priors  
  > "We use a Markov chain Monte Carlo approach using the emcee (cite: foreman2013) Python package" (Observations and analysis)
   - validation: Compared with SED-fit temperature of Sun et al. 2024 (~92 K) and optically thin estimates of ~70 K  
  > "our result for the temperature of the hot DOG is close to that obtained from the W2246–0526 SED fit" (Results)
4. **derive resolved dust parameter maps pixel by pixel**: Fit the same modified blackbody to every pixel with emission in the four datasets with extended detections (rest-frame 149 to 357 um)  
  > "to every pixel with emission from the four spatially resolved datasets to derive the properties of the dust in the resolved structures." (Observations and analysis); "using the four datasets where extended emission is detected, from rest-frame 149 to 357" (Results)
   - software: emcee
   - parameter: Same flat priors on A, T_d, M_d, beta as the central-beam fit  
  > "allowing $A$, $T_d$, $M_d$, and $\beta$ to vary freely using flat priors of" (Observations and analysis)
   - parameter: Upper limit on A set by the beam area  
  > "The beam area limits the physical area of emission $A$" (Observations and analysis)
   - assumption: Same gas-to-dust ratio (200), kappa_850um and cosmology as step 3  
  > "assuming a gas-to-dust ratio of $\delta_{GDR}=200$, given that the metallicity in the hot DOG is $\sim0.5$ Z$_{\odot}$ (cite: fernandez2024)" (Observations and analysis)
   - fitting: MCMC with emcee, flat priors  
  > "We use a Markov chain Monte Carlo approach using the emcee (cite: foreman2013) Python package" (Observations and analysis)
   - validation: Optical depth anisotropy disappears when beta is fixed, showing it is driven by beta  
  > "The optical depth map shows the same anisotropy, but it virtually disappears if we fix" (Discussion)
5. **derive optical depth, IR luminosity, SFR surface density and star formation efficiency maps**: tau at rest-frame 158 um from Eq. 3; L_3-1100um by integrating each pixel's modified blackbody; SFR from L_IR; Sigma_SFR = SFR/A; SFE = SFR/M_gas  
  > "We also present the total IR luminosity ($3-1100 \upmu\mathrm{m}$) map derived by integrating the fitted modified blackbody of each pixel." (Results); "we show the star formation efficiency (SFE), calculated as $\mathrm{SFE=SFR}/M_{gas}$, with $M_{gas}=M_{d}\times\delta_{GDR}$" (Results)
   - parameter: Sigma_SFR = SFR/A with A the intrinsic emitting area from the fit  
  > "and $A$ is the intrinsic area derived from the modified blackbody fitting" (Results)
   - assumption: SFR from L_IR following Kennicutt & Evans 2012; M_gas = M_d x gas-to-dust ratio 200  
  > "The SFR is estimated from $L_{IR}$ as in (cite: kennicutevans2012)" (Results); "with $M_{gas}=M_{d}\times\delta_{GDR}$" (Results)
   - fitting: _not stated_
   - validation: _not stated_
6. **estimate the SFR of the extended component and compare with theory**: Integrate the luminosity outside the central 2 arcsec region to get the extended SFR; compare central L_IR and Sigma_SFR with the Eddington limit for starbursts and with quasar heating predictions  
  > "by integrating the luminosity of the system outside the central 2" (Discussion); "suggesting that an obscured AGN is a more likely source of heating than an obscured, compact, extreme starburst" (Discussion)
   - fitting: _not stated_
   - validation: Extended SFR consistent with Sun et al. 2024 total values and Diaz-Santos et al. 2018 companion limits  
  > "This is consistent with previous SFR estimations for W2246–0526 from total source integrated values" (Discussion)

## Software

- **CASA** 6.5 (stated for imaging): Data reduction and calibration; continuum imaging with tclean  
  > "We reduced and calibrated the data using the Common Astronomy Software Applications (cite: mcmullin2007)" (Observations and analysis); "To image the continuum using the tclean task of CASA v6.5" (Observations and analysis)
- **emcee** : MCMC fitting of the modified blackbody  
  > "We use a Markov chain Monte Carlo approach using the emcee (cite: foreman2013) Python package" (Observations and analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Central beam dust emissivity index beta | 1.74 | ±0.08 | dimensionless | 3 | with $\beta=1.74\pm0.08$, $M_d=0.84_{-0.19}^{+0.20}\times10^8 M_{\odot}$, $T_d=109_{-15}^{+24}$ K, and $A=0.90_{-0.38}^{+0.60}$ kpc$^2$ |
| Central beam dust mass M_d | 0.84e8 | +0.20/-0.19 (x10^8) | Msun | 3 | with $\beta=1.74\pm0.08$, $M_d=0.84_{-0.19}^{+0.20}\times10^8 M_{\odot}$, $T_d=109_{-15}^{+24}$ K, and $A=0.90_{-0.38}^{+0.60}$ kpc$^2$ |
| Central beam dust temperature T_d | 109 | +24/-15 | K | 3 | with $\beta=1.74\pm0.08$, $M_d=0.84_{-0.19}^{+0.20}\times10^8 M_{\odot}$, $T_d=109_{-15}^{+24}$ K, and $A=0.90_{-0.38}^{+0.60}$ kpc$^2$ |
| Central beam emitting area A | 0.90 | +0.60/-0.38 | kpc^2 | 3 | with $\beta=1.74\pm0.08$, $M_d=0.84_{-0.19}^{+0.20}\times10^8 M_{\odot}$, $T_d=109_{-15}^{+24}$ K, and $A=0.90_{-0.38}^{+0.60}$ kpc$^2$ |
| Central beam optical depth tau at rest-frame 158 um | 0.39 | +0.26/-0.18 | dimensionless | 3 | $0.39_{-0.18}^{+0.26}$ |
| Integrated 3-1100 um luminosity of the central beam modified blackbody | 6.4e13 | not stated | Lsun | 3 | results in a $L_{3-1100\upmu\mathrm{m}}=6.4\times10^{13}\ L_{\odot}$ |
| Central beam flux densities (63, 88, 123, 149, 155, 211, 357, 572 um) | 51.0, 29.6, 12.5, 7.4, 7.3, 2.7, 0.40, 0.068 | ±0.8, ±0.6, ±0.3, ±0.2, ±0.2, ±0.1, ±0.04, ±0.037 | mJy | 3 | The corresponding fluxes are presented in Table |
| Peak dust temperature at the hot DOG (resolved maps) | ~110 | not stated | K | 4 | The peak temperature at the location of the hot DOG, $\sim$ 110 K |
| Dust temperature at radius ~8 kpc | ~40 at ~8 kpc | not stated | K | 4 | The dust temperature drops to $\sim$ 40 K at a radius of $\sim$ 8 kpc |
| Dust temperature in the connecting streams | 30-40 | not stated | K | 4 | The dust in the connecting streams between the host and companion galaxies is at temperatures between $30-40$ K |
| Total dust mass of the whole system | 5.1e8 | not stated | Msun | 4 | The system contains an estimated total mass of dust of $5.1\times10^8M_{\odot}$ |
| Dust emissivity index range in resolved maps | ~1.4-2.0 | not stated | dimensionless | 4 | The dust emissivity index $\beta$ takes values between $\sim$ 1.4–2.0. |
| Physical emitting area per pixel | ~500 pc^2 to ~1 kpc^2 | not stated | pc^2 to kpc^2 | 4 | The physical areas of emission vary between $\sim$ 500 pc$^2$ and $\sim$ 1 kpc$^2$ |
| Areal filling factor of dust | 3% or smaller | upper limit | percent | 4 | implying areal filling factors of dust of 3$\%$ or smaller |
| Maximum star formation efficiency | 10^-7.25 | not stated | yr^-1 | 5 | reaching values as high as $10^{-7.25}$ yr$^{-1}$ |
| Sigma_SFR required to reproduce the central luminosity | ~1e4 | not stated | Msun yr^-1 kpc^-2 | 6 | we would require a $\Sigma_{SFR}\sim10^4\ M_{\odot}\ \mathrm{yr}^{-1}\ \mathrm{kpc}^{-2}$ |
| SFR in the extended component | ~800 | not stated | Msun yr^-1 | 6 | We also estimate the SFR in the extended component to be $\sim800\ M_{\odot}\ \mathrm{yr}^{-1}$ |
| Molecular gas depletion time of companions C2 and C3 | <100 | upper limit | Myr | 5 | while their SFE correspond to molecular gas depletion times of less than 100 Myr |

## Qualitative findings

- Dust temperature peaks at the quasar position and falls radially to ~40 K by ~8 kpc, interpreted as quasar heating out to that distance  
  > "The dust temperature peaks at the position of the hot DOG at" (Summary); "suggesting that heating by the quasar beyond that distance is nondominant" (abstract)
- Temperature is fairly constant across the tidal streams and companions, with no evident gradient, favouring in-situ star formation heating  
  > "our results show a fairly constant dust temperature across the tidal streams and companion galaxies" (Discussion)
- Central anisotropy in A, beta and tau; the higher beta toward the southwest drives the higher optical depth  
  > "Therefore, higher optical depths are mainly driven by higher values of" (Discussion)

## Claim tuples

- H: Does the central quasar heat dust in the hot DOG host beyond the nucleus? | E: Pixel-by-pixel modified blackbody fits to the four resolved ALMA continuum datasets at a common 1.0 arcsec resolution | R: T_d peaks at ~110 K at the hot DOG and drops to ~40 K at a radius of ~8 kpc | F: Quasar heating dominates out to ~8 kpc and is nondominant beyond | **supported**
- H: What heats the dust in the tidal streams and companion galaxies? | E: Resolved dust temperature maps over ~50 kpc compared with model expectations of quasar heating | R: T_d of 30-40 K, fairly uniform, with no gradient away from the quasar | F: Dust in streams and companions is most likely heated by in-situ star formation, though quasar heating cannot be entirely ruled out | **partially**
- H: Is the hot DOG far-IR luminosity powered by a compact starburst or by an obscured AGN? | E: Integrate the central-beam modified blackbody and compare the implied Sigma_SFR with the Eddington limit for starbursts | R: L_3-1100um = 6.4e13 Lsun would need Sigma_SFR ~1e4 Msun/yr/kpc^2, above the ~1e3 limit | F: An obscured AGN is a more likely heating source than a compact extreme starburst | **supported**
- H: Is star formation efficiency enhanced in the merging companions? | E: Map SFE = SFR/M_gas with M_gas = M_d x gas-to-dust ratio | R: SFE enhanced to as high as 10^-7.25 yr^-1 at companions C2 and C3, with depletion times under 100 Myr | F: Agrees with mergers enhancing the SFE | **supported**

## Reasoning

- Why this data: ALMA is one of the few facilities able to reach the sensitivity needed for resolved high-redshift dust temperatures  
  > "is one of the few facilities capable of reaching the necessary sensitivity" (Introduction)
- Why this method: Modified blackbody to characterise the FIR continuum; datasets homogenised to one resolution; uv-taper to enhance extended emission  
  > "To characterize the FIR continuum emission in the system, we use a modified blackbody." (Observations and analysis); "to enhance any extended emission" (Observations and analysis)
- Alternative: Starburst-only heating of the central dust rejected because the required Sigma_SFR (~1e4) exceeds the ~1e3 Eddington limit  
  > "This is well above the characteristic Eddington limit set by radiation pressure on dust grains" (Discussion)
- Alternative: Additional obscured AGN in the companions cannot be ruled out but judged minor for dust heating  
  > "Although we cannot rule out the presence of additional obscured AGN in these companions" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): The area parameter A is poorly constrained, making its observed asymmetry tentative  
  > "which makes the observed asymmetry in $A$ tentative" (Discussion)
- Limitation (authors): Extended structures are not detected in four of eight datasets, possibly due to smaller maximum recoverable scales  
  > "may be due to smaller maximum recoverable scales in those observations" (Observations and analysis)
- Limitation (authors): Quasar heating of the extended structures cannot be excluded if optical depth varies along the line of sight  
  > "especially if optical depth variations are present along the quasar’s line of sight" (Discussion)
- Limitation (authors): The integrated modified blackbody excludes hotter dust that dominates the mid- and near-IR  
  > "this does not include emission from hotter dust, which dominates the mid- and near-IR" (Discussion)
- Caveat (inferred, ours): Single modified blackbody with fixed kappa_850 and gas-to-dust ratio 200 gives dust masses and T_d tied to those choices; T_d and beta are degenerate with few bands in the resolved fits
- Caveat (inferred, ours): The common 1.0 arcsec beam is much larger than the fitted emitting areas (filling factor <=3%), so the 'temperature' is a beam-averaged mixture
- Caveat (inferred, ours): Datasets with different uv coverage and maximum recoverable scales were combined, and no flux-scale uncertainty is stated
- Caveat (inferred, ours): The uniform 30-40 K in the streams is attributed to star formation without testing against a quasar-heating radiative transfer model

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Per-dataset calibration choices, calibrators and flux-scale uncertainties
- Missing: Line-free channel selection, cell and image size, primary-beam correction
- Missing: Central-beam flux extraction method and per-pixel fitting threshold and error model
- Missing: emcee configuration and likelihood
- Missing: Analysis code (no release stated)
- Data volume (inferred): Eight 12-m array datasets, roughly 1200 min on source in total; raw measurement sets likely ~100-300 GB, with continuum images only a few GB
- Score (inferred): 3/5, Project codes and nearly all tclean settings, priors, opacity and cosmology are given, and the central-beam numbers are tabulated; but calibration details, flux extraction, pixel selection and MCMC settings are missing, and the resolved maps are only shown as figures.
- Rediscovery candidate: yes, ALMA projects are listed by code, the imaging recipe and fit model with priors are specified, and results are numeric (central-beam beta, M_d, T_d, A and luminosity); data public status is inferred from the archive projects.

## Links

- Method: Foreman-Mackey et al. 2013, PASP, 125, 306 (cite: foreman2013) (emcee MCMC sampler used for the modified blackbody fits)
- Method: Scoville et al. 2014, ApJ, 783, 84 (cite: scoville2014) (Dust opacity and gas-to-dust approach adopted)
- Method: Kennicutt & Evans 2012, ARA&A, 50, 531 (cite: kennicutevans2012) (SFR from L_IR calibration)
- Method: McMullin et al. 2007 (cite: mcmullin2007) (CASA reference)
- Companion: Diaz-Santos et al. 2018, Science, 362, 1034 (cite: diaz2018) (Earlier ALMA Band 6 detection of the dust streams and companions in W2246-0526)
- Companion: Fernandez Aranda et al. 2024, A&A, 682, A166 (cite: fernandez2024) (Hot DOG metallicity and FIR fine-structure line region size)
- Companion: Sun et al. 2024, ApJ, 964, 95 (cite: sun2024) (UV to submillimeter SED fit of W2246-0526 used for comparison)
- Related: ALMA project 2013.1.00576.S is listed in the acknowledgements but not in Table 1

## Checks

```json
{
 "quotes": 109,
 "quotes_ok": 109,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 57,
  "rate": 0.655
 },
 "evidence_ok": true
}
```
