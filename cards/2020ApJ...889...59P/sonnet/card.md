# Resolving the FU Orionis System with ALMA: Interacting Twin Disks?

`2020ApJ...889...59P` | The Astrophysical Journal 2020 | first author: Pérez, Sebastián | arXiv: 1911.11282 | DOI: 10.3847/1538-4357/ab5c1b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the sizes, orientations and masses of the dust disks around FU Ori north and south, and what does the CO kinematics say about disk rotation and interaction?  
  > "we present 40 mas resolution ALMA observations of the FU Ori system which resolve the continuum emitting regions around each stellar component" (Introduction)
- Target **FU Ori (north and south)**: coordinates _not stated_; z/distance 416±9 pc  
  > "Throughout this work we use a distance to FU Ori of 416$\pm$9 pc (cite: GAIA2018)" (Introduction); distance from Gaia (Gaia Collaboration 2018)  
  > "Throughout this work we use a distance to FU Ori of 416$\pm$9 pc (cite: GAIA2018)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.01228.S
- bands: 1.3 mm (Cycle 4)  
  > "FU Ori was observed during ALMA Cycle 4 on September 6$^{\rm th}$ 2017" (Observations and data reduction)
- frequencies and spectral setup: Two 1.875 GHz continuum SPWs at 232.005 and 218.505 GHz; CO isotopologue SPWs; 122.070 kHz (~0.2 km/s) resolution  
  > "Two spectral windows with 1.875 GHz bandwidth were set up for detecting the dust continuum, centered at 232.005 GHz and 218.505 GHz, respectively." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 12m array extended C40-8, 42 antennas  
  > "using ALMA’s 12m array in extended (C40-8) configuration, with 42 antennas with baselines ranging from 41 m to 7.5 km" (Observations and data reduction)
- baselines: _not stated_
- angular resolution: ~0.05 arcsec (~21 au); continuum beam 60x42 mas  
  > "This configuration yields an angular resolution of $\sim$0.05$''$ ($\sim$21 au)" (Observations and data reduction)
- max recoverable scale: ~1.05 arcsec (~437 au)  
  > "a Maximum Recoverable Scale of $\sim$1.05$''$ ($\sim$437 au) at 1.3 mm" (Observations and data reduction)
- sensitivity: _not stated_
- time on source: 39.8 minutes  
  > "The total time spent on-source was 39.8 minutes." (Observations and data reduction)
- observing dates: 6 September 2017  
  > "FU Ori was observed during ALMA Cycle 4 on September 6$^{\rm th}$ 2017" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538 GHz)
- Line: 13CO 2-1 (220.399 GHz)
- Line: C18O 2-1 (219.560 GHz)
- External data: Previous FU Ori accretion disk model (0.3 Msun, 2.4e-4 Msun/yr at 55 deg inclination) updated here  
  > "previous SED fitting to its optical-IR spectrum suggests that FU Ori N harbors a disk accreting at a rate of $\dot{M}\approx2.4\times" (5.2 Update on the FU Ori accretion disk model) [from Zhu2007]
- External data: Dust opacity mix (amorphous carbon and astrosilicate), kappa_abs=2.2 cm2/g at 1.3 mm  
  > "we use a mix of amorphous carbon grains and astrosilicate grains (cite: Cieza2018)" (3.1 Radiative transfer) [from Cieza2018]

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline r39732 in CASA, run by ALMA staff  
  > "All data were calibrated by the ALMA staff using the ALMA Science Pipeline version r39732 in the CASA package" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (bandpass J0510+1800, phase J0532+0732)  
  > "The primary flux calibrator was the quasar J0423$-$0120, while J0510+1800 was used as bandpass calibrator." (Observations and data reduction)
- flux scale uncertainty: 10%  
  > "errors include the 10% uncertainty in the absolute flux calibration" (2.1 ALMA continuum imaging)
- self calibration: One iteration of phase-only self-cal, SNR improved by 1.7 (30 uJy RMS); second iteration marginal  
  > "A single iteration of phase-only (i.e., no amplitude) calibration resulted in a 1.7 factor improvement in the resulting SNR (30 $\mu$Jy RMS)" (2.1 ALMA continuum imaging)

### Imaging

- task: CLEAN in CASA  
  > "Imaging of the 1.3 mm continuum emission was performed using the CLEAN task in CASA with uniform weighting" (2.1 ALMA continuum imaging)
- deconvolver: _not stated_
- weighting robust: Continuum: uniform; CO: Briggs robust = 1.0  
  > "We used a Briggs weighting scheme with a robust parameter of 1.0." (2.2 ALMA 12CO imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CO imaged from continuum-subtracted data  
  > "a CLEAN procedure was performed on the continuum-subtracted data" (2.2 ALMA 12CO imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Continuum 60x42 mas PA 68.8 deg; CO 0.1x0.09 arcsec  
  > "resulting in a synthesized beam size of 60$\times$42 mas and position angle of 68.8$^{\circ}$" (2.1 ALMA continuum imaging)
- final rms: Continuum 30 uJy; CO 1.2 mJy/beam per 1 km/s channel  
  > "Each channel map has an RMS noise of 1.2 mJy beam$^{-1}$" (2.2 ALMA 12CO imaging)

### Inherited from earlier work

- RT modeling procedure  
  > "The radiative transfer (RT) modeling procedure described in (cite: Cieza2018) and (cite: Hales2018) is used to derive disk structural parameters." (3.1 Radiative transfer) [from (cite: Cieza2018); (cite: Hales2018)]
- Model visibility sampling via FFT  
  > "The model visibilities are interpolated to the same *uv* points as the observations via a Fast Fourier Transform (cite: Cieza2018; Marino2017)." (3.1 Radiative transfer) [from (cite: Cieza2018; Marino2017)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters for continuum (cell size, image size, mask, niter, threshold)
- Self-calibration solution interval and reference antenna
- Line-free channels and continuum subtraction method
- MCMC priors and parameter ranges
- Vis-fitting details (weights, centering)
- Method for deriving inclination from deconvolved axes

## Analysis recipe

1. **measure continuum sizes and fluxes**: CLEAN image then imfit to get deconvolved FWHM, PA, inclination from axis ratio  
  > "The deconvolved source sizes (as FWHM) measured using the CASA task `imfit` are 50.4$\pm$0.5$\times$39.9$\pm0.6$ (mas)" (2.1 ALMA continuum imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **radiative transfer fit of visibilities**: Passive-disk radmc-3d models compared to observed visibilities (chi2) of each component, sampled with emcee; inclination and PA fixed to imfit values  
  > "The inclination angle $i$ and PA of the model are fixed to the values obtained from `imfit`" (3.1 Radiative transfer)
   - software: radmc-3d, emcee
   - parameter: Free: Mdisk, gamma, Rc, H100, Psi plus centroid shift; 240 walkers, 2000 iterations  
  > "after running 2000 iterations ($\sim$10 times the autocorrelation time) with 240 walkers" (3.2 Modeling results)
   - parameter: Grid 256x64, 1200 K sublimation inner edge, outer radius 100 au  
  > "Radial and colatitude domains are sampled with a grid of 256 by 64 cells, respectively." (3.1 Radiative transfer)
   - assumption: Star Teff 1e4 K, R*=5 Rsun; dust n(a)~a^-3.5 from 0.1 um to 3 mm; kappa_abs=2.2 cm2/g at 1.3 mm  
  > "Here we assume an effective stellar temperature of $10^4$ K and a stellar radius of 5 $R_\odot$" (3.1 Radiative transfer)
   - fitting: emcee MCMC, chi2 likelihood on visibility plane; priors not stated  
  > "via a $\chi^2$ comparison computed on the visibility plane" (3.1 Radiative transfer)
   - validation: Posteriors single peaked and narrow; ~10 autocorrelation times  
  > "The posterior distributions of the disk structural parameters are single peaked and relatively narrow, for both components." (3.2 Modeling results)
3. **inspect 12CO kinematics**: 1 km/s channel maps; look for blue/red asymmetry along continuum PA; systemic velocities from Gaussian fit to line wings in 0.15 arcsec apertures  
  > "The location of each disk is indicated with white (dashed) crosses, with major axes parallel to the disk PA inferred from the continuum data." (4.1 Evidence of disk rotation around each component)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **update FU Ori N accretion disk model**: Rescale Zhu et al. disk model for inclination ~35 deg to reproduce the line width  
  > "to produce the same line-width that explains the optical spectrum of FU Ori (cite: Zhu2009a), the stellar mass has to increase to 0.6 M$_{\odot}$" (5.2 Update on the FU Ori accretion disk model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** pipeline r39732: calibration, CLEAN imaging, imfit  
  > "measured using the CASA task `imfit`" (2.1 ALMA continuum imaging)
- **radmc-3d** : disk radiative transfer models  
  > "computed using the radiative transfer code radmc-3d" (3.1 Radiative transfer)
- **emcee** : MCMC posterior sampling  
  > "sampled with the emcee MCMC algorithm" (3.1 Radiative transfer)
- **astropy** : listed in Software section  
  > "astropy (cite: 2013A&A...558A..33A)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| FU Ori N total flux density | 14.30 | 1.5 | mJy | 1 | FU Ori north has a total flux density of 14.30$\pm$1.5 mJy |
| FU Ori S total flux density | 7.94 | 0.8 | mJy | 1 | the southern component has a flux density of 7.94$\pm$0.8 mJy |
| Inclination N / S | 37.7 / 36.4 | 0.8 / 1.2 | deg | 1 | an inclination angle of 37.7$^{\circ}$$\pm$0.8$^{\circ}$ and 36.4$^{\circ}$$\pm$1.2$^{\circ}$ |
| In-band spectral index | 2.1 | not stated | dimensionless | 1 | of 2.1 for both FU Ori and FU Ori S |
| Dust mass N / S | 22 / 8.8 | 2 / 1.4 | Earth masses | 2 | 22$\pm$2 $M_\oplus$ for FU Ori N and 8.8$\pm$1.4 $M_\oplus$ for FU Ori S |
| Characteristic radius | ~11 | not stated | au | 2 | characteristic radii of approximately 11 au for both disks |
| Updated stellar mass and accretion rate of FU Ori N | 0.6 Msun; 3.8e-5 Msun/yr | not stated | Msun; Msun/yr | 4 | $\dot{M}$ is 3.8$\times 10^{-5}$ M$_{\odot}$ yr$^{-1}$ with the new central star mass |
| Systemic velocities N / S | 11.4 / 10.1 | 0.2 | km/s | 3 | The systemic speeds of the northern and southern components are thus 11.4 and 10.1 km s$^{-1}$, respectively |

## Qualitative findings

- CO shows rotation signatures around N and weaker around S, skewed, plus an arc coincident with scattered-light arc  
  > "The emission revealing disk rotation also appears asymmetric and skewed, suggesting the disks are subject to interaction in the form of a flyby." (7 Concluding remarks)

## Claim tuples

- H: Both FU Ori disks can be resolved and are compact with similar geometry | E: 40 mas 1.3 mm imaging, imfit and RT visibility modeling | R: Rc~11 au for both; i~37 deg; dust masses 22 and 8.8 Mearth | F: Twin compact, mostly optically thick disks with low dust mass | **supported**
- H: The revised inclination changes the FU Ori N accretion model | E: Rescale Zhu et al. model for i~35 deg | R: M*=0.6 Msun, Mdot=3.8e-5 Msun/yr | F: Lower accretion rate and higher stellar mass than previous | **supported**
- H: The disks are dynamically perturbed by interaction | E: 12CO channel maps | R: Skewed rotation patterns and an arc east of N | F: Suggests flyby/disk-disk or cloudlet capture; not conclusive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Wide 1 km/s channels used to pinpoint fast Keplerian kinematics versus slow outflows  
  > "These broad channels are needed to pinpoint fast Keplerian kinematics as opposed to slow outflows." (2.2 ALMA 12CO imaging)
- Alternative: Internal perturbation by self-gravity judged unlikely given low disk masses  
  > "An internal perturbation, e.g. driven by self-gravity, is unlikely given the low mass of the disks." (5.3 Dynamically perturbed kinematics?)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust masses likely underestimated because disks are optically thick  
  > "therefore the inferred total dust masses are likely underestimated" (3.2 Modeling results)
- Limitation (authors): Inclination and PA fixed since emission spans only 2-3 beams  
  > "This is a compromise we think necessary as the emission subtends only 2-3 resolution beams." (3.1 Radiative transfer)
- Caveat (inferred, ours): Disk model is passive and neglects viscous heating, so temperatures and masses are uncertain
- Caveat (inferred, ours): Inclination from marginally resolved axis ratio
- Caveat (inferred, ours): Interaction interpretation is qualitative
- Caveat (inferred, ours): Kinematics not fitted quantitatively

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: MCMC priors
- Missing: CLEAN parameters
- Missing: Self-cal solint
- Missing: Details of the Zhu accretion model rescaling
- Data volume (inferred): ~50-100 GB raw; one execution block
- Score (inferred): 3/5, Single archival-style dataset with clear numbers, but priors and imaging parameters are missing, and the Zhu model update is not reproducible from the text.
- Rediscovery candidate: no, The paper does not state the data are public, and the recipe lacks priors and imaging details.

## Links

- Method: Cieza et al. 2018 (cite: Cieza2018) (RT modeling procedure and dust opacities)
- Method: Hales et al. 2018 (cite: Hales2018) (RT modeling procedure)
- Companion: Hales et al. in prep (global CO kinematics and outflow)
- Companion: Hales et al. 2015 (cite: Hales2015) (earlier ALMA observations of FU Ori)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 41,
  "rate": 0.586
 },
 "evidence_ok": true
}
```
