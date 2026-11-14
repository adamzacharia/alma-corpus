# Resolving the ISM at the Peak of Cosmic Star Formation with ALMA: The Distribution of CO and Dust Continuum in z ∼ 2.5 Submillimeter Galaxies

`2018ApJ...863...56C` | The Astrophysical Journal 2018 | first author: Calistro Rivera, Gabriela | arXiv: 1804.06852 | DOI: 10.3847/1538-4357/aacffa

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How are molecular gas (CO 3-2), dust continuum and stars distributed in z~2-3 SMGs, and what do the kinematics imply for dynamical masses, alpha_CO and M*/L?  
  > "How is the molecular gas distributed in relation to the dusty ISM and the stellar populations?" (Introduction)
- Target **ALESS49.1**: coordinates 03:31:24.72, -27:50:47.1  
  > "R.A. (J2000) | 03:31:24.72" (Table 1); z/distance z(CO3-2)=2.943  
  > "R.A. (J2000) | 03:31:24.72" (Table 1); distance from CO(3-2) line in this work; optical z=2.95  
  > "R.A. (J2000) | 03:31:24.72" (Table 1)
- Target **ALESS57.1**: coordinates 03:31:51.92, -27:53:27.1  
  > "03:31:51.92" (Table 1); z/distance z(CO3-2)=2.943  
  > "$2.943 \pm 0.002$" (Table 1); distance from CO(3-2) line in this work  
  > "The CO detections are coincident with the expected ALMA Cycle 0 positions, and at frequencies which confirm the previously reported spectroscopic redshifts" (CO(3-2) line detections and continuum)
- Target **ALESS67.1**: coordinates 03:32:43.20, -27:55:14.3  
  > "03:32:43.20" (Table 1); z/distance z(CO3-2)=2.121  
  > "$2.121 \pm 0.004$" (Table 1); distance from CO(3-2) line in this work  
  > "The CO detections are coincident with the expected ALMA Cycle 0 positions, and at frequencies which confirm the previously reported spectroscopic redshifts" (CO(3-2) line detections and continuum)
- Target **ALESS122.1**: coordinates 03:31:39.54, -27:41:19.7  
  > "03:31:39.54" (Table 1); z/distance z(CO3-2)=2.024  
  > "$2.024 \pm 0.001$" (Table 1); distance from CO(3-2) line in this work  
  > "The CO detections are coincident with the expected ALMA Cycle 0 positions, and at frequencies which confirm the previously reported spectroscopic redshifts" (CO(3-2) line detections and continuum)

## Data provenance

- ALMA projects: 2013.1.00470.S, 2016.1.00754.S
- bands: Band 3  
  > "with a total integration time of $\sim$2.5 hours in ALMA Band 3" (2.1 Target selection ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "using the 12-meter array and under good phase stability/weather conditions" (2.1 Target selection ALMA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.34-0.67'' major axis FWHM; LAS 1.9-2.9''  
  > "achieving synthesized beam sizes that range between 0.34 – 0.67$''$ major axis FWHM with largest angular scales (LAS) between 1.9–2.9$''$" (2.1 Target selection ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~2.5 hours Cycle 2; ~2700 s Cycle 4 for ALESS49.1  
  > "a total integration time of ~2700 s and using the longest baselines of ~ 650 m" (2.1 Target selection ALMA observations)
- observing dates: Cycle 2: 2015 Sep 4, 6, 20; Cycle 4 (ALESS49.1): 2016 Nov 12, 16, 20  
  > "The sources were observed on 2015 September 4, 6 and 20, using the 12-meter array" (2.1 Target selection ALMA observations)
- pi or archival as stated: PI Hodge (Cycle 2); PI Wardlow (Cycle 4)  
  > "as part of the project 2013.1.00470.S (PI: Hodge)" (2.1 Target selection ALMA observations)
- Line: 12CO J=3-2 (not stated)
- Other facility **HST (WFC3/IR, ACS)**: Stellar emission imaging (H160, J125, Y105, I814), astrometry corrected with GAIA  
  > "stellar emission as traced by the WFC3/IR (bands $H_{160}, J_{125}, Y_{105}$) and/or ACS imaging ($I_{814}$) from *HST*" (2.3 Source size estimation)
- External data: CO(1-0) fluxes for ALESS67.1 and ALESS122.1  
  > "Using the measurements of $^{12}$CO($J$=1-0) by (cite: huynh17) for ALESS67.1 and ALESS122.1" (3.1 Molecular gas masses) [from (cite: huynh17)]
- External data: Stellar masses, SFRs, IR luminosities, H-band luminosities from SED fitting  
  > "$L_{H}$ is the rest-frame $H$-band luminosity corrected for dust obscuration (here estimated by (cite: dacunha15))" (3.4 Implications on alpha_CO) [from (cite: dacunha15)]
- External data: Dust continuum 0.16'' imaging of 16 ALESS sources, stacked  
  > "we also stack high-resolution dust continuum emission (0.16$''$ FWHM at rest-frame 250 $\mu$m) of 16 luminous ALESS sources studied by (cite: hodge16)" (4.2 Statistical analysis) [from (cite: hodge16)]
- External data: HST H160 imaging  
  > "the ratio of the *HST* $H_{160}$ imaging (cite: chen15) to CO half-light radii" (2.3 Source size estimation) [from (cite: chen15)]
- External data: CO excitation ratio r31=0.78±0.27  
  > "we estimate the $^{12}$CO(1-0) emission using the excitation ratio for SMGs derived by (cite: sharon16), $r_{3/1} = 0.78\pm0.27$" (3.1 Molecular gas masses) [from (cite: sharon16)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline plus manual flagging of a few corrupted time windows for ALESS57.1  
  > "Manual flagging of a few corrupted time windows for ALESS57.1 was required after an inspection of the calibration output." (2.1 Target selection ALMA observations)
- casa version: CASA 4.7.0 (imaging)  
  > "The imaging process was carried out using CASA tasks (version 4.7.0)." (2.1 Target selection ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Jupiter (bandpass J0334-4008, phase J0334-401)  
  > "The observations were calibrated based on Jupiter as the flux-calibrator" (2.1 Target selection ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "deconvolved from the point spread function using the CASA CLEAN algorithm" (2.1 Target selection ALMA observations)
- deconvolver: _not stated_
- weighting robust: Natural; also Briggs robust 0.5; tapering 1.5-2x native beam  
  > "then using a Briggs weighting with a robustness parameter 0.5" (2.1 Target selection ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Iterative cleaning with concentric circular masks (curve of growth)  
  > "Iterative cleaning consists of drawing concentric circular mask regions at increasing radii and applying the CLEAN task and line flux extraction within them." (2.1 Target selection ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: Continuum images made excluding CO line channels  
  > "Continuum images were made for all the sources after excluding the channels contributing to the CO(3-2) line emission." (2.2 CO(3-2) line detections and continuum)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 2 and Cycle 4 data concatenated for ALESS49.1  
  > "We concatenated both Cycle 2 and Cycle 4 datasets" (2.1 Target selection ALMA observations)
- smoothing: _not stated_
- final beam: 0.69x0.63, 0.67x0.60, 0.56x0.48, 0.45x0.35 arcsec (natural; 49.1/57.1/67.1/122.1)  
  > "Synthesized beam FWHM [''] | $0.69\times 0.63$ | $0.67\times 0.60$ | $0.56\times 0.48$ | $0.45 \times 0.35$" (Table 1)
- final rms: Continuum rms 17.6, 19.5, 18.2, 16.3 uJy/beam in table; channel rms 113-182 uJy/beam  
  > "Continuum RMS [$\mu$Jy beam$^{-1}$] | 17.6 | 19.5 | 18.2 | 16.3" (Table 1)

### Inherited from earlier work

- Iterative cleaning mask technique  
  > "We adopted an iterative cleaning technique (cite: chen17), in order to optimize the mask size estimation" (2.1 Target selection ALMA observations) [from (cite: chen17)]
- Radiative transfer model of dust and CO  
  > "we have used an extended version of the dust and line radiative transfer models of (cite: weiss07)" (4.3 Physical implications) [from (cite: weiss07); Weiß et al. (in prep)]
- Luminosity formula L'CO  
  > "These were calculated following (cite: solomon05) as" (3.1 Molecular gas masses) [from (cite: solomon05)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Image size and cell size
- Clean threshold and iteration count
- Mask radii procedure beyond table values
- GALPAK3D priors ranges, sampler settings and model profiles
- emcee walkers, steps, burn-in and Mdyn uncertainties used in likelihood
- Stacking details for continuum/HST data (centering, beam matching)
- Radiative transfer model parameters (temperature gradient, tau) not given
- Details of uv-fit binning

## Analysis recipe

1. **Image CO(3-2) cubes and continuum**: CASA CLEAN with iterative circular masks, natural/Briggs/tapered weighting; channel averaging to 16-82 MHz  
  > "we produced the final data cubes averaging the visibilities to channel widths of 16, 61, 82 and 77 MHz for ALESS49.1, 57.1, 67.1, 122.1, respectively." (2.1 Target selection ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Curve of growth convergence  
  > "a curve of growth is produced" (2.1 Target selection ALMA observations)
2. **Measure line parameters and half-light radii**: Gaussian fits to spectra; Gaussian fit to binned uv amplitudes to get r1/2  
  > "We fit a Gaussian profile to the data and measure the radius within which half of the light of the galaxy is contained." (2.3 Source size estimation)
   - software: CASA
   - fitting: Gaussian profile fits  
  > "Gaussian profile fits to the extracted spectra" (CO(3-2) line detections and continuum)
   - validation: _not stated_
3. **Kinematic analysis**: PV diagrams for all; GALPAK3D 3D disk modelling for ALESS122.1  
  > "we model the data using the modelling package GALPAK3D" (3.2.2 Kinematic Modelling)
   - software: CASA viewer, GALPAK3D
   - assumption: Rotating disk; first moment pixels with SNR<2 masked  
  > "we masked out all pixels with SNR\<2" (3.2.2 Kinematic Modelling)
   - fitting: Bayesian MCMC with uniform priors, minimizing reduced chi2  
  > "Starting from a set of uniform priors on the disk parameters" (3.2.2 Kinematic Modelling)
   - validation: reduced chi2 = 1.87; residuals consistent with noise  
  > "with a reduced $\chi^2_{\nu}$ of 1.87" (3.2.2 Kinematic Modelling)
4. **Derive dynamical masses**: Mdyn(r<2r1/2) = (Δv_rot/2 sin i)^2 × 2 r1/2 / G; inclination from IMFIT axis ratios  
  > "The total dynamical mass within a radius $r=2r_{1/2}$ is then given by" (3.3 Dynamical Masses)
   - software: CASA IMFIT
   - assumption: Disk thickness q0=0.1; vrot = half FWHM when not modelled  
  > "assuming $q_0=0.1$ (cite: nedyalkov93)" (3.3 Dynamical Masses)
   - fitting: _not stated_
   - validation: Compared with Huynh17 and Chen17  
  > "These values are in general agreement with previous measurements of the dynamical masses of two of these sources" (3.3 Dynamical Masses)
5. **Constrain alpha_CO and M*/L_H**: MCMC on Mdyn = [L_H M*/L_H + L_CO alpha_CO]/(1-fDM), fDM fixed at 0, 15, 30%; 100 Monte Carlo iterations over L_CO, L_H uncertainties, posteriors averaged  
  > "repeat the inference exercise presented above for 100 iterations" (3.4 Implications on alpha_CO)
   - software: emcee, corner
   - assumption: Fixed dark matter fractions  
  > "we will keep the $f_{\rm DM}$ value fixed" (3.4 Implications on alpha_CO)
   - fitting: emcee; likelihood on Mdyn uncertainties only  
  > "the likelihood function accounts only for the uncertainties in the dynamical masses" (3.4 Implications on alpha_CO)
   - validation: _not stated_
6. **Stack radial profiles and fit sizes**: 10x10'' thumbnails aligned, scaled to common peak, radially averaged; bootstrap 1000 for uncertainties; 1D exponential (Sersic) convolved with Gaussian beam  
  > "by creating 1000 different average profiles, where each iteration used a randomly resampled combination of sources" (4.2 Statistical analysis)
   - assumption: Dust profile points >7 kpc discarded due to sidelobes  
  > "we discarded the data points at radius of $>$7 kpc" (4.2 Statistical analysis)
   - fitting: 1D exponential; Sersic n free for stars  
  > "we fit a one-dimensional exponential to the CO and dust continuum profiles and find that they are well described by such a model" (Statistical analysis on the relative sizes of dust continuum, molecular gas and stellar emission in SMGs)
   - validation: _not stated_
7. **Radiative transfer model of CO vs dust sizes**: Extended Weiss07 model with exponential column density and linear temperature gradient, constant dust-to-gas ratio  
  > "we use an exponentially decreasing column density distribution (Sérsic index of $n=1$) and a linear temperature gradient" (4.3 Physical implications)
   - fitting: _not stated_
   - validation: Model reproduces stacked profiles  
  > "the model can reproduce the different radial behaviour of the dust continuum and the CO(3-2) line emission" (4.3 Physical implications)

## Software

- **CASA** 4.7.0: Calibration, imaging, IMFIT, viewer PV diagrams  
  > "The imaging process was carried out using CASA tasks (version 4.7.0)." (2.1 Target selection ALMA observations)
- **GALPAK3D** : 3D kinematic modelling of ALESS122.1  
  > "GALPAK3D is a Bayesian parametric Markov Chain Monte Carlo fitter for three-dimensional (3D) galaxy data" (3.2.2 Kinematic Modelling)
- **emcee** : Sampling posterior of alpha_CO and M*/L  
  > "using the open-source algorithm EMCEE (cite: fm13) for the sampling" (3.4 Implications on alpha_CO)
- **Astropy** : Python analysis  
  > "This research made use of ASTROPY" (Acknowledgements)
- **APLpy** : Plotting  
  > "the open-source plotting packages for Python APLPY (cite: aplpy), and CORNER (cite: corner)" (Acknowledgements)
- **corner** : Posterior plots  
  > "the open-source plotting packages for Python APLPY (cite: aplpy), and CORNER (cite: corner)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| alpha_CO (fDM=15%) | 1.1 | +0.8/-0.7 | Msun/(K km/s pc^2) | 5 | For a DM fraction of 15% we find a median value of $\alpha_{\rm CO}= 1.1^{+0.8}_{-0.7} |
| alpha_CO (fDM=30%) | 0.9 | +0.7/-0.6 | Msun/(K km/s pc^2) | 5 | $\alpha_{\rm CO}= 0.9^{+0.7}_{-0.6} |
| Exponential radius: dust continuum, CO, stars | 1.7, 3.8, 4.0 | 0.1, 0.1, 2.0 | kpc | 6 | radii of $r= 1.7\pm0.1, 3.8\pm0.1$ and $4.0\pm2.0$ kpc for the dust continuum, CO and stellar emission respectively |
| GALPAK3D ALESS122.1 vmax / sigma / i | 560 km/s / 130 km/s / 52 deg | not stated | km/s, deg | 3 | an inclination of $i \sim 52^{\circ}$, a maximum rotational velocity of $v_{\rm max} \sim 560$ km s$^{-1}$, and a velocity dispersion of $\sigma_v \sim 130$ km s$^{-1}$ |
| Mdyn(<2r1/2) ALESS49.1/57.1/67.1/122.1 | 1.1, 1.1, 3.6, 5.3 | 0.2, 0.5, 1.6, 1.6 | 1e11 Msun | 4 | $M_{\rm dyn}(r \leq 2 r_{1/2})$ [$10^{11}$ M$_{\odot}$] / $1.1 \pm 0.2$ / $1.1 \pm 0.5$ / $3.6 \pm 1.6$ / $5.3 \pm 1.6$ |
| CO(3-2) r1/2 (49.1/57.1/67.1/122.1) | 2.6, 3.1, 6.9, 3.6 | 0.4, 0.5, 0.8, 0.3 | kpc | 2 | CO(3-2) $r_{1/2}$ [kpc] / $2.6 \pm 0.4$ / $3.1 \pm 0.5$ / $6.9 \pm 0.8$ / $3.6 \pm 0.3$ |
| Intrinsic H2 exponential scale length from RT model | 3.4 kpc (0.4'') | not stated | kpc | 7 | we derive an intrinsic exponential scale length of 3.4 kpc (0.4$''$) for the underlying H$_2$ distribution |
| r31 for ALESS67.1 and ALESS122.1 | 1.01 and 0.77 | 0.36, 0.19 | dimensionless | 0 | which yields $r_{3/1} = 1.01 \pm 0.36$ and $r_{3/1} = 0.77 \pm 0.19$, respectively |

## Qualitative findings

- Gas and stellar emission in ALESS122.1 are offset by ~0.5'' with almost no overlap  
  > "separated by $\sim$ 0.5$''$ ($\sim$ 5 kpc at $z = 2$) as measured from their centroids" (4.1 Offset distributions)

## Claim tuples

- H: Are SMG CO velocity fields consistent with disk rotation? | E: PV diagrams for four sources and GALPAK3D model of ALESS122.1 | R: Velocity gradients in three of four sources; ALESS122.1 model reduced chi2 1.87 | F: Consistent with disk rotation to first order, though mergers not excluded | **supported**
- H: What alpha_CO is implied by dynamical masses given M*/L and fDM uncertainty? | E: MCMC on dynamical mass budget | R: alpha_CO=1.1 (+0.8/-0.7) for fDM=15% | F: Low alpha_CO, covariant with M*/L | **supported**
- H: Are CO gas and dust continuum co-spatial? | E: Stacked radial profiles of CO, 250 um dust and H160 | R: CO and stars >2x more extended than dust | F: Dust continuum sizes underestimate gas extent | **supported**
- H: Can temperature and optical depth gradients explain size difference at constant dust-to-gas ratio? | E: Radiative transfer model fit to stacked profiles | R: Model reproduces both profiles | F: Plausible explanation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dynamical masses plus stellar masses constrain gas mass independent of alpha_CO  
  > "allow us to make an estimate of the total gas mass independently of the above mentioned assumptions" (3.1 Molecular gas masses)
- Alternative: Three scenarios for stellar/gas offset in ALESS122.1: extreme extinction, physical misalignment, merger  
  > "We consider three scenarios for explaining the mismatch of the distributions of stellar and gas/dust continuum emission in ALESS122.1." (4.1 Offset distributions)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample (four sources) gives large uncertainties  
  > "the values recovered for the parameters are subject to large uncertainties due to our small sample size" (3.4 Implications on alpha_CO)
- Limitation (authors): CO(3-2) size is a lower limit for total molecular extent  
  > "the estimated size of the CO(3-2) emission should be considered a lower limit" (4.2 Statistical analysis)
- Caveat (inferred, ours): Only four sources; dust and CO stacks use mostly different samples (one in common)
- Caveat (inferred, ours): Inclinations very uncertain (e.g. 40±50 deg)
- Caveat (inferred, ours): Radiative transfer model not fully described (in prep)
- Caveat (inferred, ours): Mdyn for ALESS67.1 uses only one component

## Reproducibility

- Data public (paper): Project codes given in acknowledgements; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00470.S and #2016.1.00754.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: RT model details (Weiß et al. in prep)
- Missing: GALPAK3D configuration
- Missing: Stacking inputs and HST/continuum maps from other papers
- Missing: Clean parameters and line-free channels
- Data volume (inferred): ~20-60 GB raw for two Band 3 projects
- Score (inferred): 5/5, Data identified, main steps described, but many parameters missing and RT model unpublished.
- Rediscovery candidate: no, Recipe incomplete (RT model, GALPAK3D settings, external stacking data).

## Links

- Method: (cite: bouche15) (GALPAK3D kinematic fitter)
- Method: (cite: chen17) (Iterative cleaning technique)
- Method: (cite: weiss07) (Dust and CO radiative transfer model)
- Companion: Wardlow et al. 2018 (Environment of ALESS49.1 with Cycle 4 data)
- Companion: (cite: huynh17) (CO(1-0) of ALESS67.1 and 122.1)
- Companion: (cite: hodge16) (High-resolution dust continuum of ALESS sources used in stacking)
- Related: ALESS
- Related: LESS (LABOCA ECDFS Submm Survey)

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
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
  "facts": 96,
  "stated": 69,
  "rate": 0.719
 },
 "evidence_ok": true
}
```
