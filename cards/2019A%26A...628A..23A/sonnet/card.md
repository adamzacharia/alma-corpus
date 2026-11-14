# Imaging the molecular interstellar medium in a gravitationally lensed star-forming galaxy at z = 5.7

`2019A&A...628A..23A` | Astronomy and Astrophysics 2019 | first author: Apostolovski, Yordanka | arXiv: 1905.12738 | DOI: 10.1051/0004-6361/201935308

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the intrinsic sizes, kinematics and ISM excitation of the lensed DSFG SPT0346-52 at z=5.66, as traced by mid/high-J CO, H2O and dust continuum in the source plane?  
  > "reconstruct the molecular gas emission in the source plane, (ii) derive their emitting sizes, resolve the gas distribution along the velocity axis and compare with previous observations" (Introduction)
- Target **SPT0346-52**: coordinates _not stated_; z/distance z=5.6556  
  > "The millimeter-bright, gravitationally lensed galaxy SPT0346-52 at $\text{z}=5.6556$ is among the most distant and intrinsically luminous DSFGs known to date." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00722.S, 2015.1.00117.S
- bands: ALMA Bands 3 and 4  
  > "Observations of SPT0346-52 were performed with ALMA bands 3 and 4" (2.1 ALMA Observations)
- frequencies and spectral setup: three tunings per band, four SPWs each in FDM, 1.875 GHz per SPW; 7.8125 and 15.625 MHz channels (23 and 31 km/s)  
  > "Each frequency tuning was observed using four spectral windows (SPWs) in Frequency Division Mode (FDM) and a bandwidth of 1.875 GHz per SPW." (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 0.31-0.86 hr per line (Table 1)  
  > "| ALMA | CO(9$-$8) | $155.78$ | $1036.91$ | $042315$ | $0.31$ |" (Table 1)
- observing dates: April-May 2015 (Cycle 2) and April 2016 (Cycle 3)  
  > "Cycle 2 and 3 observations were conducted during April and May of 2015, and during April of 2016, respectively." (2.1 ALMA Observations)
- pi or archival as stated: PI: M. Aravena  
  > "(PI: M. Aravena)" (2.1 ALMA Observations)
- Line: CO 6-5 (691.47 GHz)
- Line: CO 8-7 (921.79 GHz)
- Line: CO 9-8 (1036.91 GHz)
- Line: H2O 2_11-2_02 (752.03 GHz)
- Line: H2O 2_02-1_11 (987.92 GHz)
- Other facility **APEX SEPIA band 5**: CO(10-9) single-dish detection  
  > "its SEPIA band 5 receiver to observe the redshifted emission of the $^{12}$CO $J=10-9$ in SPT0346-52" (2.2 APEX Observations)
- Other facility **ATCA**: CO(2-1) data from Spilker et al. 2015  
  > "We use previous ATCA observations of the $^{12}$CO $J=$2$-$1 emission line toward SPT0346-52 obtained and described in detail by (cite: spilker15)." (2.3 ATCA Observations)
- External data: Fixed lens model (SIE plus external shear)  
  > "The lensing mass distribution used was fixed to that obtained by (cite: spilker16) using ALMA 870$\mu$m observations with a resolution of $\sim 0.5''$." (3.1 Lensed Source Reconstruction) [from (cite: spilker16)]
- External data: Herschel SPIRE 250/350/500 um fluxes and ALMA 0.87mm flux used in SED/LVG model  
  > "the ALMA 0.87mm flux (cite: spilker16), and the 250$\mu$m, 350$\mu$m and 500$\mu$m from Herschel/SPIRE observations (cite: ma16)" (4.2 CO SLED) [from (cite: spilker16); (cite: ma16)]

## Processing

### Calibration

- pipeline or manual: Independent manual reduction in CASA; no differences from ALMA pipeline calibration  
  > "We performed an independent reduction and calibration of the data, however we did not see differences with respect to the ALMA pipeline calibration." (2.1 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: quasars and Mars incl. J0411-5149, J0334-401, J0519-4546  
  > "bright quasars and Mars were used for bandpass, flux and phase calibration, including J0411-5149, J0334-401 and J0519-4546." (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "The visibilities were deconvolved using the `CLEAN` algorithm." (2.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robustness 0.5  
  > "finally used the Briggs weighting with a robustness factor of 0.5" (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: tight circular aperture radius 5", clean to 2 sigma  
  > "we masked this source using a tight circular aperture around it with a radius of $5''$, cleaning down to $2\sigma$" (2.1 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: power law fit to extracted spectra  
  > "We subtracted the continuum emission from the line profiles by fitting a power law to the extracted spectra." (2.1 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cubes averaged by 2, 4 and 8 channels  
  > "We created data cubes at different channel resolutions, averaging by 2, 4 and 8 original channels." (2.1 ALMA Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Lens model parameters and visibility-domain method  
  > "The method relies on modeling the visibilities instead of images and simultaneously determining self-calibration phases (cite: hezaveh13)." (3.1 Lensed Source Reconstruction) [from (cite: spilker16); (cite: spilker14); (cite: hezaveh13)]
- LVG radiative transfer method  
  > "using the method described in (cite: weiss07). This method is based on a spherical, multi-component, large velocity gradient (LVG) model." (4.2 CO SLED) [from (cite: weiss07)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum fit ranges
- Image size and cell size
- Lens-fit sampler, priors and likelihood details in visibility fitting
- VISILENS version and run configuration
- LVG fit priors and fitting procedure
- CASA version
- Lens centre value fixed

## Analysis recipe

1. **Image cubes and extract spectra**: CLEAN with Briggs 0.5; 7" aperture photometry on 4-channel-averaged cubes; Gaussian fits for FWHM; direct integration for fluxes  
  > "The line FWHM and central frequency are computed from single, one-dimensional Gaussian fits to the emission line profiles." (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Source-plane reconstruction per velocity bin**: Visibility-domain lens modelling with circular Gaussian source (4 free params), fixed SIE+shear lens, nine velocity bins of 100 km/s  
  > "The emission regions have been assumed to have a circularly symmetric Gaussian light profile with four free parameters: flux density F$_S$, scale radius R$_S$, and position offsets" (3.1 Lensed Source Reconstruction)
   - software: VISILENS
   - parameter: bins from -400 to 400 km/s; outer bins widened by 4x  
  > "Each of the lens-modeled lines in SPT0346-52 are split into nine velocity bins with a width of 100 km s$^{-1}$, ranging from $-400$ to $400$ km s$^{-1}$." (3.1 Lensed Source Reconstruction)
   - fitting: _not stated_
   - validation: Compared with single wide-channel reconstruction  
  > "we also performed a reconstruction of each line using a single, wide velocity channel (from $- 2\sigma_{vel}$ to $2\sigma_{vel}$) as a benchmark for comparison." (3.1 Lensed Source Reconstruction)
3. **CO line ratios vs velocity**: Compare observed and intrinsic (delensed) CO J/CO(2-1) intensity ratios and magnification per velocity bin  
  > "we explore the variation of the magnification and CO line ratios as a function of velocity (i.e. along the line of sight)." (4.1 CO Ratios)
   - fitting: _not stated_
   - validation: Compared with Dong et al.  
  > "This behaviour is broadly consistent with the results presented by (cite: dong18)" (4.1 CO Ratios)
4. **CO SLED LVG modelling**: Spherical multi-component LVG model fit to intrinsic CO and continuum fluxes  
  > "This method is based on a spherical, multi-component, large velocity gradient (LVG) model." (4.2 CO SLED)
   - parameter: fixed CO line width 642 km/s  
  > "we assume a fixed CO line width, corresponding to the weighted average line width value (642 km s$^{-1}$)." (4.2 CO SLED)
   - assumption: CO(2-1)/CO(1-0) brightness ratio R21=0.9 for SLED comparison  
  > "assuming a brightness temperature line ratio $R_{21}=T^B_{21}/T^B_{10}=0.9$ (cite: carilli&walter13)" (4.2 CO SLED)
   - fitting: _not stated_
   - validation: Gas mass compared with dynamical mass  
  > "even higher than the dynamical mass estimate of $1.5\times10^{11}\ M_\ensuremath{\odot}$ obtained from the high resolution CO($2-1$) imaging (cite: spilker15)" (4.2 CO SLED)

## Software

- **CASA** : reduction, calibration and imaging  
  > "The data were reduced and imaged using the Common Astronomy Software Application package `CASA`" (2.1 ALMA Observations)
- **CLASS** : APEX data calibration and flagging  
  > "Offline data calibration and flagging was performed using the `CLASS` software package" (2.2 APEX Observations)
- **VISILENS** : source-plane reconstruction  
  > "Using the `VISILENS` code and lens model parameters obtained in (cite: spilker16) we reconstructed the lensed galaxy in the source-plane" (Summary and Conclusions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(6-5) intrinsic r_eff | 0.92 | 0.02 | kpc | 2 | /       CO(6$-$5)        /   6.09 $\pm$ 0.07   / 0.92 $\pm$ 0.02  / |
| CO(9-8) intrinsic r_eff | 0.79 | 0.02 | kpc | 2 | /       CO(9$-$8)        /   5.36 $\pm$ 0.03   / 0.79 $\pm$ 0.02  / |
| CO(2-1) magnification | 8.30 | 0.39 | dimensionless | 2 | /       CO(2$-$1)        /   8.30 $\pm$ 0.39   / 1.15 $\pm$ 0.08  / |
| 2 mm continuum r_eff | 0.73 | 0.03 | kpc | 2 | /         $2$mm          /   $5.04 \pm 0.09$   / $0.73 \pm 0.03$  / |
| CO(10-9) integrated flux | 17.3 | 2.9 | Jy km/s | 1 | the single Gaussian fit yields an integrated flux of $\sim 17.3 \pm 2.9$ Jy km s$^{-1}$ |
| LVG kinetic temperature | 43 | 14 | K | 4 | $T_{\text{kin}}$     / $43   \pm 14$ K |
| LVG gas mass | 3.9e11 | 2.2e11 | Msun | 4 | $3.9      \pm 2.2 \times 10^{11} M_\odot$ |

## Qualitative findings

- Higher-J CO traces more compact regions; CO sizes larger than dust continuum sizes  
  > "The CO sizes show a clear trend of decreasing size with increasing $J$" (Summary and Conclusions)

## Claim tuples

- H: Do higher-J CO lines trace more compact regions? | E: Visibility-plane source reconstruction of CO 2-1, 6-5, 8-7, 9-8 | R: r_eff decreases from 1.15 to 0.79 kpc | F: Higher-J CO is more compact | **supported**
- H: Is the kinematics a merger or a disk? | E: Velocity-binned reconstruction | R: gradients suggest disk-like structure in some lines, size variations in CO(2-1) and H2O 2_11-2_02 | F: Merger scenario favoured but ambiguous | **partially**
- H: Is the ISM highly excited? | E: LVG modelling of the CO SLED | R: Tkin ~43 K, log n ~4.9, SLED peaks near J=8-7 | F: Dense warm gas, similar to quasar hosts; model not fully constrained | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Gaussian profile chosen to minimize free source parameters  
  > "the choice of a Gaussian profile compared to e.g. Sérsic or other commonly used source profiles is justified in order to minimize the number of free source parameters." (3.1 Lensed Source Reconstruction)
- How they decided it was enough: _not stated_
- Limitation (authors): LVG model not fully constrained because the CO SLED peak is not traced  
  > "our inability to trace the peak of the CO SLED with our current observations and thus our radiative transfer model is not fully constrained" (4.2 CO SLED)
- Caveat (inferred, ours): Single Gaussian source model may bias sizes and magnifications
- Caveat (inferred, ours): Lens model fixed from 870um data
- Caveat (inferred, ours): CO(10-9) possibly blended with H2O
- Caveat (inferred, ours): LVG gas mass exceeds dynamical mass

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: VISILENS settings and priors
- Missing: LVG code and fit details
- Missing: Line-free channel choices
- Data volume (inferred): ~50-100 GB for the six ALMA tunings
- Score (inferred): 3/5, Data are archival projects with named method, but lens-fit and LVG details are largely deferred to earlier papers.
- Rediscovery candidate: no, Key analysis depends on VISILENS and inherited lens model and LVG code with incomplete settings.

## Links

- Method: (cite: spilker16) (lens model)
- Method: (cite: weiss07) (LVG model)
- Method: (cite: hezaveh13) (visibility-plane lens modelling)
- Companion: (cite: litke18) ([CII] reconstruction of the same source)
- Companion: (cite: dong18) (CO(8-7) reconstruction of the same source)
- Companion: (cite: spilker15) (ALMA 870um and ATCA CO(2-1) data)
- Related: South Pole Telescope DSFG survey

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 36,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
