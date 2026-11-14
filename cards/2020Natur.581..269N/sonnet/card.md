# A cold, massive, rotating disk galaxy 1.5 billion years after the Big Bang

`2020Natur.581..269N` | Nature 2020 | first author: Neeleman, Marcel | arXiv: 2005.09661 | DOI: 10.1038/s41586-020-2276-y

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is the absorption-selected galaxy DLA0817g at z=4.26 a rotationally supported cold disk, and what are its dynamical and molecular masses?  
  > "These observations show that the emission arises from gas inside a cold, dusty, rotating disk with a rotational velocity of 272 kilometres per second." (abstract)
- Target **DLA0817g (QSO J081740.52+135134.5 absorber galaxy)**: coordinates _not stated_; z/distance z = 4.2603 ([C II])  
  > "ALMA observed the galaxy associated with the absorber toward QSO J081740.52+135134.5, DLA0817g" (ALMA observations and data reduction.); distance from [C II] emission line redshift  
  > "ALMA observed the galaxy associated with the absorber toward QSO J081740.52+135134.5, DLA0817g" (ALMA observations and data reduction.)

## Data provenance

- ALMA projects: 2017.1.01052.S
- bands: [C II] tuned at 361.312 GHz, plus three continuum bands, each 1.875 GHz wide  
  > "One of the four 1.875-GHz ALMA receiver bands was centred at 361.312 GHz, the redshifted frequency of the [C II] 158-$\upmu$m ([C II]) emission line" (ALMA observations and data reduction.)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-5, max baseline ~2.5 km  
  > "The nominal antenna configuration was C43-5, with a maximum baseline length of approximately 2.5 km." (ALMA observations and data reduction.)
- baselines: _not stated_
- angular resolution: 0.23" x 0.17" (natural), 0.16" x 0.12" (robust 0.5)  
  > "The resultant synthesized beams are 0.23$'' \times$ 0.17$''$ and 0.16$'' \times$ 0.12$''$" (ALMA observations and data reduction.)
- max recoverable scale: _not stated_
- sensitivity: continuum 23 uJy/beam (natural), 27 uJy/beam (robust 0.5); cube 0.35 mJy/beam per 25 km/s (natural)  
  > "r.m.s. sensitivities of 0.35 mJy beam$^{-1}$ per 25 km s$^{-1}$ for natural weighting" (ALMA observations and data reduction.)
- time on source: 100 minutes  
  > "for a total on-source time of 100 minutes" (ALMA observations and data reduction.)
- observing dates: 2018 January 6 and 2018 January 21  
  > "in two executions on 2018 January 6 and 2018 January 21" (ALMA observations and data reduction.)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um fine-structure (157.74 um)
- Line: CO 2-1 (JVLA) (observed at 43.828 GHz)
- Other facility **JVLA**: CO(2-1) detection, 9 h, D configuration  
  > "for a total on-source integration time of 9 h (programme ID 17-279, PI: Neeleman)" (JVLA observations and data reduction.)
- Other facility **HST WFC3 F160W**: rest-frame near-UV image, 0.31" resolution  
  > "The effective spatial resolution of the HST observations is $0.31''$" (HST observations, data reduction and analysis.)
- External data: Lower-resolution ALMA [C II] and continuum measurements for comparison  
  > "These measurements are consistent with the values obtained from the lower-resolution measurement(cite: Neeleman2017)" (Far-Infrared Continuum, [C II] Line, and CO(2-1) Line Luminosities.) [from (cite: Neeleman2017)]
- External data: alpha_CO = 3.0 and r21 = 0.81 conversion factors  
  > "We therefore assume r$_{\,2,1} =$ 0.81, as determined from these galaxies." (Molecular Gas Mass Estimates.) [from (cite: Dessauges-Zavadsky2015); (cite: Daddi2010)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline in CASA, then minor additional flagging  
  > "The raw data were calibrated using the ALMA calibration pipeline, which is part of the Common Astronomy Software Application (CASA) package" (ALMA observations and data reduction.)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0854+2006 (flux and bandpass); J0750+1231 phase  
  > "The blazar J0854+2006 was used as a flux and bandpass calibrator, and the blazar J0750+1231, as the phase calibrator." (ALMA observations and data reduction.)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean; natural and Briggs robust 0.5 versions; natural used for analysis  
  > "In this paper, we opted to use only the natural weighting scheme" (ALMA observations and data reduction.)
- deconvolver: _not stated_
- weighting robust: robust = 0.5 (Briggs alternative)  
  > "the other using Briggs weighting with a robust parameter of 0.5" (ALMA observations and data reduction.)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvsub then uvcontsub  
  > "we subtracted the continuum emission using the task *uvsub* and then subtracted any remaining residual continuum emission with *uvcontsub*" (ALMA observations and data reduction.)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- MCMC cube-fitting approach follows earlier papers  
  > "minimizes the residuals between the convolved model and the observed data cube using a Markov Chain Monte Carlo (MCMC) approach(cite: Banados2019; Neeleman2019b; Venemans2019)" (Kinematic Analysis of the [C II] Emission Line.) [from (cite: Banados2019; Neeleman2019b; Venemans2019)]
- Dynamical mass formula  
  > "is the circular velocity (in km s$^{-1}$) of the galaxy at the radius $R$(cite: Wang2013)" (Dynamical Mass Estimate.) [from (cite: Wang2013)]
- SFR calibrations from 160 um continuum and TIR  
  > "we use the observationally-determined calibration between SFR and 160 $\upmu$m continuum(cite: Calzetti2010)" (Star Formation Rate Estimates.) [from (cite: Calzetti2010); (cite: Kennicutt2012)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum and uvcontsub order
- tclean cell size, image size, masks, cleaning threshold, iterations
- MCMC priors, walker number, chain length, convergence criteria
- Channel range used for the velocity-integrated [C II] map
- Radial bin sizes for rotation curves
- JVLA calibrators and imaging details
- Flux-scale uncertainty for ALMA

## Analysis recipe

1. **Calibrate and image ALMA data**: Pipeline calibration, extra flagging, tclean continuum and cubes  
  > "The calibrated visibility data set was then re-examined within CASA, where minor additional flagging was performed." (ALMA observations and data reduction.)
   - software: CASA
   - parameter: cube 25 km/s channels, natural weighting  
  > "0.35 mJy beam$^{-1}$ per 25 km s$^{-1}$ for natural weighting" (ALMA observations and data reduction.)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure fluxes and sizes**: Flux within 1.5" radius per channel, integrate over line channels; 2D Gaussian fits for size  
  > "we measure the flux density within a radius of 1.5$''$ centered on DLA0817g for each channel" (Far-Infrared Continuum, [C II] Line, and CO(2-1) Line Luminosities.)
   - software: CASA imfit
   - assumption: TIR from modified blackbody with Td=35 K, beta=1.6  
  > "Assuming fiducial values of $T_{\rm d} =$ 35 K and $\beta =$ 1.6" (Far-Infrared Continuum, [C II] Line, and CO(2-1) Line Luminosities.)
   - fitting: _not stated_
   - validation: Compared with lower-resolution data to check no flux resolved out  
  > "indicating that the [C II] emission is not resolved out in the higher resolution observations" (Far-Infrared Continuum, [C II] Line, and CO(2-1) Line Luminosities.)
3. **Fit rotating disk model to [C II] cube**: Thin exponential disk with constant (or arctan) rotation, constant dispersion, convolved with beam, MCMC fit to cube  
  > "we assume a [C II] line emission model in which the [C II] emission arises from a thin disk in which the emission exponentially declines" (Kinematic Analysis of the [C II] Emission Line.)
   - software: custom Python MCMC code (qubefit)
   - parameter: 9 or 10 free parameters  
  > "these 9 or 10 parameters uniquely determine the [C II] line emission in the model cube" (Kinematic Analysis of the [C II] Emission Line.)
   - assumption: Infinitely thin disk; thick disk tested  
  > "In the above models, we assume the [C II] emission arises from an infinitely thin disk." (Kinematic Analysis of the [C II] Emission Line.)
   - fitting: MCMC minimizing residuals; priors not stated  
  > "The program convolves the model cube with the observed beam and then minimizes the residuals between the convolved model and the observed data cube using a Markov Chain Monte Carlo (MCMC) approach" (Kinematic Analysis of the [C II] Emission Line)
   - validation: Residuals below 3 sigma; compared with 3DBarolo (279 km/s)  
  > "which yields a rotational velocity of 279 km s$^{-1}$and a velocity dispersion of 72 km s$^{-1}$, consistent with our values" (Kinematic Analysis of the [C II] Emission Line.)
4. **Derive rotation curves, dynamical mass, Toomre Q**: Mean-velocity and peak-velocity rotation curves; Mdyn = 2.32e5 v^2 R; Q averaged over R=3Rd  
  > "$M_{\rm dyn}(R)$ = 2.32 $\times$ 10$^{5} v_{\rm rot}(R)^2 R$" (Dynamical Mass Estimate.)
   - parameter: R = 3 exponential scale lengths = 4.2 kpc  
  > "we will assume the extent of the galaxy to be three times the exponential scale length of the modeled emission" (Dynamical Mass Estimate.)
   - assumption: Spherical mass distribution (30% uncertainty added)  
  > "the mass distribution is implicitly assumed to be spherical" (Dynamical Mass Estimate.)
   - fitting: _not stated_
   - validation: Compared with FWHM-based v_rot of 300 +/- 50 km/s  
  > "we get a rotational velocity of 300 $\pm$ 50 km s$^{-1}$" (Dynamical Mass Estimate.)
5. **Molecular gas mass from CO(2-1)**: CMB-corrected CO flux to L'CO, then r21 and alpha_CO  
  > "we assume a conservative $\alpha_{\rm CO}$ of 3.0 M$_\odot$ ( K km s$^{-1}$ pc$^2$)$^{-1}$" (Molecular Gas Mass Estimates.)
   - assumption: r21 = 0.81, alpha_CO = 3.0, Texc 25-45 K  
  > "We therefore assume r$_{\,2,1} =$ 0.81, as determined from these galaxies." (Molecular Gas Mass Estimates.)
   - fitting: _not stated_
   - validation: Compared with FIR- and [C II]-based gas masses  
  > "The results from both methods are in agreement with the molecular gas mass estimate based on the CO(2$-$1) emission line." (Molecular Gas Mass Estimates.)

## Software

- **CASA** : Calibration, imaging, uvsub/uvcontsub, imfit  
  > "The raw data were calibrated using the ALMA calibration pipeline, which is part of the Common Astronomy Software Application (CASA) package" (ALMA observations and data reduction.)
- **3DBarolo** : Tilted-ring consistency check  
  > "we also fitted DLA0817g using the 'tilted-ring' fitting program $^{\rm 3D}$Barolo(cite: DiTeodoro2015)" (Kinematic Analysis of the [C II] Emission Line.)
- **qubefit** : Kinematic modelling code released  
  > "All of the code used to generate the kinematic modeling is available online at: (https://github.com/mneeleman/qubefit)." (Code Availability.)
- **Source Extractor** 2.5.0: HST photometry and shape  
  > "we used Source Extractor (v.2.5.0(cite: Bertin1996))" (HST observations, data reduction and analysis.)
- **AstroDrizzle/TweakReg** : HST mosaic and astrometric alignment to Gaia DR2  
  > "We created the image mosaic using AstroDrizzle and aligned the astrometry to the GAIA DR2 astrometry(cite: Gaia2018) using TweakReg" (HST observations, data reduction and analysis.)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inclination-corrected rotational velocity | 272 | +52/-13 | km/s | 3 | an inclination-corrected rotational velocity of $v_{\rm rot}$ = 272$^{+52}_{-13}$ km s$^{-1}$ |
| Position angle | 105.2 | 1.7 | deg | 3 | position angle of 105.2 $\pm$ 1.7$^{\rm o}$ |
| Inclination | 42 | +3/-8 | deg | 3 | an inclination angle of 42$^{+3}_{-8}$$^{\rm o}$ |
| Dynamical mass | 7.2e10 | 2.3e10 | Msun | 4 | $M_{\rm dyn}$ = (7.2 $\pm$ 2.3) $\times$ 10$^{10} M_\odot$ |
| vrot/sigma_v | 3.4 | +1.1/-0.3 | dimensionless | 3 | Our estimate for $v_{\rm rot}/\sigma_v$ is 3.4$^{+1.1}_{-0.3}$ |
| Disk-averaged Toomre Q | 0.96 | 0.30 | dimensionless | 4 | This yields $\bar{Q} = 0.96 \pm 0.30$ for DLA0817g. |
| Velocity-integrated [C II] flux | 5.8 | 0.4 | Jy km/s | 2 | The total velocity-integrated [C II] flux density from DLA0817g is 5.8 $\pm$ 0.4 Jy km s$^{-1}$ |
| 160 um continuum flux density | 1.28 | 0.15 | mJy | 2 | 1.28 $\pm$ 0.15 mJy |
| Molecular mass from CO(2-1) | 8.8e10 | 2.6e10 | Msun (r21=0.81, alpha_CO=3.0) | 5 | (8.8 $\pm$ 2.6) $\times$ 10$^{10}$ $\times$ (0.81 / r$_{\,2,1}$) |

## Qualitative findings

- [C II] emission arises from a rotating disk with flat rotation curve beyond ~1.8 kpc; dust and near-UV co-spatial with [C II]  
  > "The rotation curve is flat beyond a radius of about 1.8 kpc" (main text)

## Claim tuples

- H: DLA0817g hosts a rotationally supported disk | E: Fit disk model to the 0.19" [C II] cube | R: vrot=272 km/s, vrot/sigma=3.4, residuals <3 sigma | F: Cold, rotation-dominated disk at z=4.26 | **supported**
- H: Molecular gas mass is comparable to the dynamical mass | E: CO(2-1) JVLA detection converted with r21 and alpha_CO | R: Mmol=8.8e10 vs Mdyn=7.2e10 Msun | F: Large cold gas fraction | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Constant velocity model chosen as it has fewest free parameters  
  > "therefore we opt for the model with the least free parameters, the constant rotational velocity model" (Kinematic Analysis of the [C II] Emission Line.)
- Alternative: Arctangent velocity profile and thick-disk models gave no significant differences/ higher vrot  
  > "No significant differences are found between the two different models" (Kinematic Analysis of the [C II] Emission Line.)
- How they decided it was enough: _not stated_
- Limitation (authors): Unresolved JVLA only probes total molecular mass within ~15 kpc beam  
  > "the unresolved JVLA observations can only probe the total molecular mass within the beam of the JVLA observations" (main text)
- Caveat (inferred, ours): CO detection only 4.7 sigma
- Caveat (inferred, ours): Thin-disk and spherical mass assumptions
- Caveat (inferred, ours): Conversion factors alpha_CO, Texc, Td and beta poorly constrained
- Caveat (inferred, ours): [C II] as gas surface density tracer for Q

## Reproducibility

- Data public (paper): ALMA, JVLA and HST data in public archives  
  > "The data reported in this paper are available though the ALMA archive" (Data Availability.)
- Products in archive: _not stated_
- Code: qubefit on GitHub  
  > "(https://github.com/mneeleman/qubefit)" (Code Availability.)
- Missing: Exact tclean parameters and line-free channels
- Missing: MCMC priors and settings
- Missing: Radial binning choices
- Data volume (inferred): ~20-50 GB raw ALMA for two executions
- Score (inferred): 4/5, Public data, released code, and numeric results, but imaging and fit settings are only partly given.
- Rediscovery candidate: yes, Public ALMA data, released code, numeric kinematic results; some settings need inference.

## Links

- Method: (cite: DiTeodoro2015) (3DBarolo tilted-ring check)
- Companion: (cite: Neeleman2017) (Earlier lower-resolution ALMA observations of DLA0817g)
- Companion: (cite: Neeleman2019) (Sample of absorption-selected galaxies)
- Related: JVLA 17A-279
- Related: HST 15410

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 49,
  "rate": 0.605
 },
 "evidence_ok": true
}
```
