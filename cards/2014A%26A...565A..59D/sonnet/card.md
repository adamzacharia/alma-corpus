# ALMA resolves turbulent, rotating [CII] emission in a young starburst galaxy at z = 4.8

`2014A&A...565A..59D` | Astronomy and Astrophysics 2014 | first author: De Breuck, Carlos | arXiv: 1404.2295 | DOI: 10.1051/0004-6361/201323331

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the spatial distribution and kinematics of [CII] and rest-frame far-infrared emission in the z=4.76 SMG ALESS 73.1, and what do they imply for its dynamical mass, stability and metallicity?  
  > "Our new ALMA observations map the spatial distribution and kinematics of the [Cii] and rest-frame far-infrared emission within this system on $\sim$ kpc scales" (Introduction)
- Target **ALESS 73.1 (LESS J033229.4-275619, XID 403)**: coordinates RA 03:32:29.31, Dec -27:56:19.66 (J2000, [CII] position)  
  > "| $z_{\rm [CII]}$ | 4.7555 $\pm$ 0.0001 | 3 |" (Table 1); "| $\rm [$Cii\] $\delta$ (J2000) | $-$27:56:19.66 | 3 |" (Table 1); z/distance z = 4.7555 ([CII])  
  > "| $z_{\rm [CII]}$ | 4.7555 $\pm$ 0.0001 | 3 |" (Table 1); "| $\rm [$Cii\] $\delta$ (J2000) | $-$27:56:19.66 | 3 |" (Table 1); distance from [CII] redshift from these ALMA data; H0=73, Om=0.27, OL=0.73, 6.4 kpc/arcsec  
  > "| $z_{\rm [CII]}$ | 4.7555 $\pm$ 0.0001 | 3 |" (Table 1); "| $\rm [$Cii\] $\delta$ (J2000) | $-$27:56:19.66 | 3 |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00124.S
- bands: Band 7  
  > "We used the Band 7 receivers with the four basebands centered at 317.20, 319.07, 329.54, and 331.11 GHz." (2.1 ALMA)
- frequencies and spectral setup: four basebands at 317.20, 319.07, 329.54, 331.11 GHz; [CII] in the last two; 1875 MHz per baseband, 488.28 kHz x 3840 channels  
  > "The correlator was used in the frequency domain mode with a bandwidth of 1875 MHz (488.28 kHz $\times$ 3840 channels per baseband)." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: Cycle 0 compact configuration, 23 antennas  
  > "in the compact Cycle 0 configuration, with 23 antennas covering baselines between 18 m and 402 m" (2.1 ALMA)
- configurations: _not stated_
- baselines: 18 m to 402 m  
  > "with 23 antennas covering baselines between 18 m and 402 m" (2.1 ALMA)
- angular resolution: 0.65" x 0.40" PA 91 deg (natural weighting)  
  > "cleaned it using natural weighting, which provides a final synthesized beam size of 0.65$''$ $\times$ 0.40$''$ at position angle of 91$^{\circ}$" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.15 mJy in combined map  
  > "We also made a combined 318.13 + 330.34 GHz continuum map, which reaches an rms noise level of 0.15 mJy." (2.1 ALMA)
- time on source: 1.62 h  
  > "The total time on target was 1.62 h." (2.1 ALMA)
- observing dates: UT 2012 July 18 and 27  
  > "The ALMA observations of ALESS 73.1 were obtained on UT 2012 July 18 and 27" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um fine-structure line (not stated (lambda 157.74 um))
- Other facility **APEX/SHFI**: re-observation of [CII] (4.8 h) as consistency check on the earlier flux  
  > "we re-observed the [Cii] line in ALESS 73.1 on UT 2013 July 10 to 13 (ESO programme 092.A-0668)" (2.2 APEX)
- Other facility **HST/CANDELS**: F160W image for comparison with ALMA position  
  > "We find that the ALESS73.1 dust continuum detection is offset by 0.22$''$ from the *HST* F160W identification" (3.1 Integrated [Cii] and continuum emission)
- External data: H2 gas mass 1.6e10 Msun from CO(2-1), alpha_CO=0.8  
  > "derived from the $^{12}$CO(2–1) detection reported by (cite: coppin10)" (4.1) [from (cite: coppin10)]
- External data: L(8-1000um) = 5.6e12 Lsun used to derive SFR  
  > "(cite: swinbank14) find a very similar, $L_{\rm 8-1000\,\mu m}$= 5.6$^{+1.8}_{-1.1}\times$ 10$^{12}$ L$_{\odot}$" (4.1) [from (cite: swinbank14)]
- External data: [NII] 205 um data for velocity structure comparison and metallicity  
  > "We also compared the velocity structure of the [Cii] and the [Nii] data from (cite: nagao12)" (3.1) [from (cite: nagao12)]

## Processing

### Calibration

- pipeline or manual: standard CASA procedures  
  > "The data reduction followed the standard procedures in the Common Astronomy Software Applications (casa) package (cite: petry12)." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas, Neptune, Callisto (bandpass J0522-364, gain J0403-360)  
  > "the fluxes were calibrated with Pallas, Neptune, and Callisto" (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting used; robust = 0.5 maps also made  
  > "To search for spatially extended [Cii] and continuum emission, we also made maps with robust = 0.5" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from summing line-free channels in lower and upper sidebands separately: 318.13 and 330.34 GHz  
  > "we summed all line free channels in the lower and upper sidebands separately, resulting in two continuum maps at 318.13 and 330.34 GHz" (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 22 channel (24.85 km/s) binning  
  > "We applied a 22 channel (24.85 km s$^{-1}$) binning to the data cube" (2.1 ALMA)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Disk model with beam smearing  
  > "The model also includes the effect of beam smearing (cite: gnerucci10; gnerucci11)." (3.2 [Cii] velocity analysis) [from (cite: gnerucci10; gnerucci11)]
- Intrinsic velocity dispersion correction method  
  > "To derive the (model-independent) intrinsic velocity dispersion of the disk at each pixel (corrected for the contribution of the velocity gradient across the synthesised beam), we follow (cite: swinbank12a)." (3.2 [Cii] velocity analysis) [from (cite: swinbank12a)]
- PDR atomic gas mass parameters  
  > "Following (cite: debreuck11), we adopt a C$^+$ abundance 1.4$\times$10$^{-4}$" (4.1) [from (cite: debreuck11)]

### Not stated but needed to reproduce (our reading)

- Whether archive or self-produced calibration; CASA version
- Line-free channels and continuum/line mask
- Cell size, image size, clean threshold
- Initial guess and fitting details of the dynamical model code (Gnerucci-type) and priors
- MCMC priors and likelihood for M_dyn-i
- KinMS_fit setup (unpublished)
- Toomre Q aperture and weighting choices; [CII]-to-gas-surface-density conversion
- Details of the outflow fit and [NII]/[CII] metallicity model grid

## Analysis recipe

1. **Image cube and continuum**: CASA reduction, natural-weighted cube binned to 24.85 km/s; continuum from line-free channels  
  > "The data reduction followed the standard procedures in the Common Astronomy Software Applications (casa) package (cite: petry12)." (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit velocity field with rotating disk**: Single-Gaussian velocity field fit, then thin exponential-disk dynamical model convolved with beam  
  > "We fit the velocity field with a dynamical model assuming that the ionised gas is circularly rotating in a thin disk" (3.2 [Cii] velocity analysis)
   - assumption: exponential surface density, hydrodynamical effects neglected  
  > "We neglect all hydrodynamical effects, therefore the disk motion is entirely determined by the gravitational potential." (3.2 [Cii] velocity analysis)
   - fitting: _not stated_
   - validation: Compared with KinMS and arctan models giving similar results  
  > "Both the alternative models, which have significantly different flux distributions from the model described above, obtain similar results." (3.2 [Cii] velocity analysis)
3. **Dynamical mass and inclination**: M_dyn sin^2 i = R v^2/G with MCMC (1e5 realisations) over disk parameters; range from three models  
  > "we use a Monte Carlo Markov Chain (MCMC) with 10$^5$ realisations to investigate the uncertainties on the disk model parameters" (3.3.1 Dynamical mass)
   - software: KinMS, KinMS_fit
   - fitting: MCMC  
  > "To constrain the inclination, we use a Monte Carlo Markov Chain (MCMC) with 10$^5$ realisations to investigate the uncertainties on the disk model parameters" (3.3.1 Dynamical mass)
   - validation: _not stated_
4. **Toomre Q map**: Q = sqrt2 sigma V /(pi r G Sigma) per pixel using [CII] luminosity as proxy for Sigma, flat rotation curve  
  > "using the [Cii] luminosity distribution as a proxy to determine $\Sigma$" (3.4 Stability of the disk)
   - assumption: [CII] traces molecular gas kinematics  
  > "We therefore assume that the [Cii] emission traces well the kinematics of the underlying star-forming molecular gas component" (3.4 Stability of the disk)
   - fitting: _not stated_
   - validation: _not stated_
5. **Gas, stellar mass, alpha_CO, outflow limit**: Atomic gas mass from Hailey-Dunsheath eq. 1; mass budget; outflow from forced broad Gaussian component  
  > "we fitted the ALMA spectrum by forcing an additional broad component with a fwhm $>$ 500 km s$^{-1}$" (4.2 Limits on outflowing gas)
   - assumption: C+ abundance 1.4e-4, n_crit 2.7e3 cm^-3, PDR T ~300 K  
  > "a critical density $n_{\rm crit}$=2.7$\times$10$^3$ cm$^{-3}$ and a PDR surface temperature $\sim$300 K" (4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction and imaging  
  > "The data reduction followed the standard procedures in the Common Astronomy Software Applications (casa) package (cite: petry12)." (2.1 ALMA)
- **KinMS** : alternative kinematic disk model  
  > "we used the KINematic Molecular Simulation (*KinMS*) routines of (cite: davis13)" (3.2 [Cii] velocity analysis)
- **KinMS_fit** : Bayesian MCMC fitter for KinMS  
  > "coupled to the Bayesian Monte Carlo Markov Chain fitter *KinMS_fit* (Davis et al., in prep.)" (3.2 [Cii] velocity analysis)
- **CLASS** : APEX data reduction  
  > "the data were reduced using standard procedures in the Continuum and Line Analysis Single-dish Software" (2.2 APEX)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] integrated flux | 7.42 | 0.35 | Jy km/s | 1 | / $I_{\rm [CII]}$ / 7.42 $\pm$ 0.35 Jy km s$^{-1}$ / 3 / |
| max deprojected rotation velocity | 120 | 10 | km/s | 2 | yielding a maximum de-projected[^3] velocity $v_{\rm rot}$= 120$\pm$10 km s$^{-1}$ |
| intrinsic velocity dispersion | 40 | 10 | km/s | 2 | the intrinsic velocity dispersion of the disk is $\sigma_{\rm int}$ = 40 $\pm$ 10 km s$^{-1}$ |
| adopted dynamical mass | 3e10 | 2e10 | Msun | 3 | adopt $M_{\rm dyn}$= 3$\pm$2 $\times$ 10$^{10}$ M$_{\odot}$ |
| inclination (disk model) | 53 | 9 | deg | 3 | constrain the inclination $i=$ 53$^\circ$$\pm$9 |
| average Toomre Q | 0.58 | 0.15 | dimensionless | 4 | The average $Q$ over the disk is 0.58$\pm$0.15 |
| atomic gas mass | 4.7e9 | 0.5e9 | Msun | 5 | we derive M$_{\rm a}$$\simeq$ 4.7$\pm$0.5 $\times$ 10$^9$ M$_{\odot}$ |
| stellar mass limit | <3.1e10 | not stated | Msun | 5 | our dynamical mass constrains the stellar mass to $<$3.1$\times$ 10$^{10}$ M$_{\odot}$ |
| outflow rate upper limit | <=1400 | not stated | Msun/yr | 5 | to be $\lesssim$ 1400 M$_{\odot}$ yr$^{-1}$ |
| [NII]/[CII] ratio | 0.085 | 0.015 | dimensionless | 5 | [Nii]/[Cii] $=$ 0.085 $\pm$ 0.015 |

## Qualitative findings

- [CII] disk extends about twice as far as the dust continuum and shows rotation  
  > "the [Cii] emitting gas extends twice as far out as the dust continuum" (5 Conclusions)

## Claim tuples

- H: Is the [CII] emission in ALESS 73.1 a rotating disk? | E: Dynamical modelling of the velocity field with three models | R: v_rot=120 km/s, sigma=40 km/s, v/sigma=3.1 | F: A highly turbulent rotating disk | **supported**
- H: Is the gas disk gravitationally stable? | E: Spatially resolved Toomre Q | R: mean Q=0.58 | F: Disk unstable throughout, can fuel the starburst | **supported**
- H: Is the galaxy low in stellar mass and gas rich? | E: Mass budget from M_dyn, M_a, M_H2 | R: M_dyn=3e10 Msun, M*<3.1e10 Msun, alpha_CO<2.3 | F: First major burst of star formation | **partially**
- H: Is the metallicity close to solar? | E: [NII]/[CII] ratio with new ALMA [CII] | R: Z=0.6-3 Zsun | F: Close to solar, but PDR truncation may allow subsolar | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Stellar-dominated SED excluded due to light-to-mass ratio  
  > "We therefore exclude the possibility that the SED is dominated by stellar emission." (3.3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk barely resolved so flux distribution and dynamical mass uncertain  
  > "as we barely spatially resolve the flux distribution within the disk, we cannot distinguish which flux distribution is more appropriate" (3.2 [Cii] velocity analysis)
- Caveat (inferred, ours): Only ~2x2 beams across the disk; model dependence (M_dyn range 1.4-4.1e10)
- Caveat (inferred, ours): Assuming [CII] traces molecular gas surface density for Q
- Caveat (inferred, ours): Inclination poorly constrained and differs between models

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00124.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Disk model code and priors
- Missing: KinMS_fit unpublished
- Missing: Imaging parameters
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Data identifiable and recipe broad, but many modelling and imaging details missing.
- Rediscovery candidate: no, Key modelling steps use unpublished or underspecified code.

## Links

- Method: (cite: gnerucci11) (Kinematic disk modelling with beam smearing)
- Method: (cite: swinbank12a) (Velocity dispersion correction and arctan model)
- Method: (cite: davis13) (KinMS)
- Companion: (cite: debreuck11) (Previous APEX [CII] detection)
- Companion: (cite: nagao12) ([NII] 205 um detection)
- Related: ALESS
- Related: CANDELS
- Related: MUSYC

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 43,
  "rate": 0.566
 },
 "evidence_ok": true
}
```
