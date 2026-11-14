# An ALMA Study of the FU Ori-type Object V900 Mon: Implications for the Progenitor

`2019ApJ...884..146T` | The Astrophysical Journal 2019 | first author: Takami, Michihiro | arXiv: 1909.05520 | DOI: 10.3847/1538-4357/ab43c8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Are FUor outbursts associated with normal low-mass YSOs? What are the outflow, envelope and disk of V900 Mon, and does the FUor wind interact with them?  
  > "are FUor outbursts associated with most low-mass YSOs? In other words, are FUors peculiar YSOs, or is this a specific phase for the evolution of most low-mass YSOs?" (Introduction)
- Target **V900 Mon**: coordinates RA 06:57:22.224, Dec –08:23:17.64 (J2000)  
  > "The pointing and phase referencing center is R.A. (J2000) = 06:57:22.224, and Decl. (J2000) = –08:23:17.64." (2 Observations and Data Reduction); "Throughout the paper we adopt a distance of 1.5 kpc (cite: GaiaDR2)." (Introduction); z/distance 1.5 kpc  
  > "The pointing and phase referencing center is R.A. (J2000) = 06:57:22.224, and Decl. (J2000) = –08:23:17.64." (2 Observations and Data Reduction); "Throughout the paper we adopt a distance of 1.5 kpc (cite: GaiaDR2)." (Introduction); distance from Gaia DR2  
  > "The pointing and phase referencing center is R.A. (J2000) = 06:57:22.224, and Decl. (J2000) = –08:23:17.64." (2 Observations and Data Reduction); "Throughout the paper we adopt a distance of 1.5 kpc (cite: GaiaDR2)." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00209.S, 2017.1.00451.S
- bands: Band 6 (230 GHz, 1.3 mm)  
  > "Excluding the absolute flux uncertainty of 10 % for the ALMA Band 6 observations." (Table 2)
- frequencies and spectral setup: two 1.875 GHz continuum SPWs at 216.9 and 232.2 GHz; two 58.6 MHz SPWs for 13CO and C18O (0.083 km/s); one 58.6 MHz SPW for 12CO (0.040 km/s)  
  > "two 58.6 MHz wide spectral windows to cover $^{13}$CO $J$=2–1 and C$^{18}$O $J$=2–1 at a 0.083 km s$^{-1}$ velocity resolution" (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array and ACA  
  > "We observed V900 Mon with the ALMA 12 m array on 2017 April 20 and July 27, and with the ACA on 2016 October 11" (2 Observations and Data Reduction)
- configurations: _not stated_
- baselines: uv distance 20-3500 m (12 m), 9.3-46 m (ACA)  
  > "These observations covered *uv* distance ranges of 20-3500 m and 9.3-46 m, respectively." (2 Observations and Data Reduction)
- angular resolution: continuum 0.20"×0.15" beam  
  > "0.20$''$$\times$0.15$''$ | –72.3$^\circ$" (Table 2)
- max recoverable scale: 29 arcsec  
  > "These configurations provided a largest recoverable scale of 29 arcsec." (2 Observations and Data Reduction)
- sensitivity: continuum rms 55 μJy/beam (Briggs robust=0)  
  > "The Briggs Robust=0 weighted continuum image taken with ALMA achieved an 55 $\mu$Jy beam$^{-1}$ root-mean-square (RMS) noise level." (2 Observations and Data Reduction)
- time on source: 4.4 min (ACA), 3.0 min and 9.1 min (ALMA)  
  > "| 3 | 20170727 | ALMA | 0.5 | J0522-3627/J0510+1800 | J0654-0544 | 1.1/0.85 | 9.1 |" (Table 1)
- observing dates: 2016-10-11 (ACA), 2017-04-20 and 2017-07-27 (ALMA)  
  > "on 2017 April 20 and July 27, and with the ACA on 2016 October 11" (2 Observations and Data Reduction)
- pi or archival as stated: PI Michihiro Takami  
  > "PI: Michihiro Takami" (2 Observations and Data Reduction)
- Line: 12CO J=2–1 (230.5380 GHz)
- Line: 13CO J=2–1 (220.3987 GHz)
- Line: C18O J=2–1 (219.5604 GHz)
- Other facility **Gaia DR2**: distance of 1.5 kpc  
  > "Throughout the paper we adopt a distance of 1.5 kpc (cite: GaiaDR2)." (Introduction)
- External data: Envelope mass of V900 Mon (0.027 Msun) from SED modelling  
  > "The envelope mass derived by these authors is 0.027 $M_\ensuremath{\odot}$" (Introduction) [from (cite: Gramajo14)]
- External data: 1.3 mm fluxes and sizes of other FUors for comparison (V346 Nor, V883 Ori, HBC 494, V2775 Ori)  
  > "| V346 Nor  | FUor      | 135                      | 0.7   | $\sim$1980 | 27$\pm$3      | 13$\pm$1" (Table 4) [from (cite: Kospal17c); (cite: Cieza18)]
- External data: Outflow opening angles and envelope masses of Class 0-II YSOs for comparison  
  > "(cite: Arce06) observed the CO outflows and envelopes associated with Class 0, I, and II YSOs using millimeter interferometry." (5 Toward a Unified Scheme) [from (cite: Arce06)]
- External data: Optical P Cygni wind velocity ~200 km/s and outburst onset between 1953 and 2009  
  > "As reported by (cite: Thommes11; Reipurth12), the outburst began between 1953 and 2009." (4.3 Interaction with a Hot FUor Wind?) [from (cite: Reipurth12); (cite: Thommes11)]

## Processing

### Calibration

- pipeline or manual: manual calibration plus phase self-calibration  
  > "The data were manually calibrated and phase self-calibrated using the CASA software package (cite: McMullin07) version 5.4." (2 Observations and Data Reduction)
- casa version: CASA 5.4  
  > "version 5.4" (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (ACA, epoch 3), J0656-0323 (epoch 2)  
  > "| 2 | 20170420 | ALMA | 2.7 | J0656-0323/J0510+1800 | J0656-0323 | 2.3/0.56 | 3.0 |" (Table 1)
- flux scale uncertainty: 10 % absolute flux uncertainty  
  > "Excluding the absolute flux uncertainty of 10 % for the ALMA Band 6 observations." (Table 2)
- self calibration: phase self-cal, increased S/N only marginally  
  > "The self calibration increased the signal-to-noise ratio only marginally." (2 Observations and Data Reduction)

### Imaging

- task: tclean, all continuum data imaged jointly  
  > "jointly imaged all continuum data using the CASA task `tclean`" (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0 (continuum)  
  > "The Briggs Robust=0 weighted continuum image" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: 0.02" spatial and 0.2 km/s velocity sampling for CO cubes  
  > "spatial and velocity pixel sampling of 0.02$''$ and 0.2 km s$^{-1}$, respectively" (2 Observations and Data Reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub baseline fit  
  > "We fitted the continuum baselines using the CASA task `uvcontsub`" (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m and ACA data; no Total Power, probable missing flux ≳20 % in lines  
  > "The absence of the Total Power observations probably causes significant missing fluxes ($\gtrsim$20 %) for these line observations." (2 Observations and Data Reduction)
- smoothing: each channel convolved with 2D Gaussian (5, 8, 11 pixel FWHM for 12CO, 13CO, C18O)  
  > "| 5 | 0.22$''$ | 0.29$''$$\times$0.26$''$ |" (Table 2)
- final beam: continuum 0.20"×0.15"; after convolution 12CO 0.29"×0.26", 13CO 0.41"×0.39", C18O 0.51"×0.49"  
  > "0.41$''$$\times$0.39$''$" (Table 2)
- final rms: continuum 55 μJy/beam; lines 5.2/4.9/3.8 mJy/beam (0.2 km/s channel) before convolution  
  > "| 4.0       | 5.2               |" (Table 2)

### Inherited from earlier work

- Flat viscous disk temperature model  
  > "We use a simple conventional flat disk model, used extensively for FUors over many years (cite: Calvet91b; Zhu07; Zhu08)" (Appendix) [from (cite: Calvet91b; Zhu07; Zhu08)]
- Dust opacity 0.2 m^2/kg  
  > "We assume 0.2 m$^2$ kg$^{-1}$ following (cite: Beckwith90)." (Appendix) [from (cite: Beckwith90)]
- Surface density Σ ∝ r^-1 from Class II disks  
  > "Here we adopt $\Sigma (r) \propto r^{-1}$ based on previous observations of disks for Class II YSOs (cite: Williams11; Takami13)." (Appendix) [from (cite: Williams11; Takami13)]

### Not stated but needed to reproduce (our reading)

- tclean cleaning threshold, niter, mask, image size and cell size for continuum
- line-free channels used for uvcontsub
- self-calibration solution intervals
- how continuum Gaussian-fit uncertainties were derived
- flux calibrator model/flux values
- how the convolution FWHM and pseudo-beam for the Monte Carlo were set
- aperture definitions for line profile regions A–D'
- deprojection details for the 48 deg inclination limit and the 60-120 K temperature

## Analysis recipe

1. **Calibrate and image data**: Manual calibration and phase self-cal in CASA; uvcontsub; joint tclean of continuum; CO cubes made at 0.2 km/s and convolved spatially  
  > "The data were manually calibrated and phase self-calibrated using the CASA software package (cite: McMullin07) version 5.4." (2 Observations and Data Reduction)
   - software: CASA, tclean, uvcontsub
   - parameter: robust=0 continuum  
  > "The Briggs Robust=0 weighted continuum image" (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux and size**: 2D Gaussian fit with IMFIT in image plane, deconvolved from the beam  
  > "We use the IMFIT routine within CASA to fit two-dimensional Gaussians to the continuum data and derive both continuum fluxes and disk sizes (deconvolved from the beam)" (3.1 Continuum)
   - software: CASA
   - assumption: distance 1.5 kpc  
  > "Throughout the paper we adopt a distance of 1.5 kpc (cite: GaiaDR2)." (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Map CO outflow, envelope and extract line profiles**: Channel and moment 0 maps of three CO lines; line profiles from selected regions; peak and FWHM velocities of C18O  
  > "We tabulate the peak and FWHM velocities for the C$^{18}$O emission in Table [3](#tab:prof_params)." (3.4 CO Line Profiles)
   - software: python, numpy, scipy, matplotlib
   - parameter: reference velocity 13.9 km/s  
  > "which we tentatively define as 13.9 km s$^{-1}$" (3.4 CO Line Profiles)
   - assumption: Keplerian velocity for 1 Msun central mass  
  > "assuming 1 $M_\ensuremath{\odot}$" (4.2 Molecular Envelope)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model viscous-disk millimeter emission**: Flat viscous disk with T_eff(r), Σ∝r^-1, Σ0 tuned to match 9.0 mJy; Monte Carlo image convolved with a 0.18" beam and compared with the Gaussian disk  
  > "We adjusted $\Sigma_0$ to match the flux to the observations using `scipy.interpolate.interp1d`." (Appendix)
   - software: scipy
   - parameter: Lacc=100 Lsun, kappa=0.2 m2/kg, Ri=5 Rsun, rout=300 au, Tsub=1500 K, i=0 and 60 deg, 10^5 photons  
  > "Sublimation temperature $T_{\mathrm sub}$               | 1500 K$^{d}$" (Table 5)
   - assumption: Lacc about half of ~200 Lsun  
  > "We assume 100 $L_\ensuremath{\odot}$, about half of the observed bolometric luminosity" (Appendix)
   - fitting: _not stated_
   - validation: compared convolved model FWHM with Gaussian disk: 0.21" and 0.22" vs Gaussian  
  > "The viscous disk models yield a FWHM of the observations of 0.21$''$ and 0.22$''$, respectively." (Appendix)

## Software

- **CASA** 5.4: calibration, self-calibration, uvcontsub, tclean, IMFIT  
  > "manually calibrated and phase self-calibrated using the CASA software package (cite: McMullin07) version 5.4" (2 Observations and Data Reduction)
- **python (numpy, scipy, matplotlib)** : analysis of CO cubes and disk model  
  > "were analyzed using python (`numpy`, `scipy`, `matplotlib`)." (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm continuum flux | 9.0 | 0.9 | mJy | 2 | we derive a flux of 9.0$\pm$0.9 mJy |
| Deconvolved continuum FWHM (image plane) | 0.067" × 0.058" | 0.008" | arcsec | 2 | (0.067$''$$\pm$0.008$''$)$\times$(0.058$''$$\pm$0.008$''$) |
| Deconvolved size in au | 100×87 | +35/-24, +32/-22 | au | 2 | 100$_{-24}^{+35}$$\times$87$_{-22}^{+32}$ au |
| Disk temperature (optically thick uniform) | 60–120 | not stated | K | 2 | we derive a typical temperature of the disk of 60–120 K assuming an optically thick disk with a uniform temperature |
| Total dust mass of viscous disk model | 2.2e-3 (i=0), 3.0e-3 (i=60) | not stated | Msun | 4 | Total dust mass ($M_\ensuremath{\odot}$)                / 2.2$\times$10$^{-3}$ / 3.0$\times$10$^{-3}$ / |
| CO outflow opening angles at r~5000 au | ~70 (blue), ~120 (red) | not stated | degrees | 3 | $\sim$70$^\circ$ and $\sim$120$^\circ$ at $r$$\sim$5000 au for the blueshifted and redshifted lobes |
| Maximum disk inclination from face-on if continuum is disk only | 48 | not stated | degrees | 2 | the observed spatial scale implies a disk inclination of up to 48$^\circ$ from the face-on |

## Qualitative findings

- Extended bipolar CO outflow (~10^4 au) and rotating C18O envelope (>10^4 au) detected  
  > "We identified CO emission associated with a molecular bipolar outflow extending up to a $\sim$10$^4$ au scale and a rotating molecular envelope extending over $>$10$^4$ au." (abstract)
- Hot FUor wind interaction limited to within ~400-800 au  
  > "appears limited to a region within $\sim$400 au of the star" (abstract)

## Claim tuples

- H: The progenitor of V900 Mon is a normal low-mass Class I YSO | E: Compared envelope mass and CO outflow opening angle with Class 0-II YSOs | R: Low envelope mass and opening angles ~70/120 deg similar to Class I | F: Progenitor is a Class I YSO, consistent with FUor outbursts occurring in normal YSOs | **supported**
- H: The hot FUor wind has interacted with the extended molecular gas | E: Searched CO channel maps and profiles for wind interaction | R: High-velocity 12CO up to ~19 km/s and C18O deficit only within ~0.5" | F: Interaction limited to ~800 au; outburst began recently | **supported**
- H: What explains the compact warm mm continuum | E: Gaussian fit plus flat viscous-disk model and Monte Carlo convolution | R: Disk temperature 60-120 K; viscous model gives FWHM 9-16% larger than the Gaussian | F: Viscous heating explains warm compact emission; fragmentation and grain drift may contribute | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Free-free emission from wind/jet judged unlikely to dominate the flux (<0.1 mJy at 230 GHz for FU Ori)  
  > "free-free continuum emission from the ionized jet or the wind is $<$0.1 mJy at 230 GHz" (4.4 Continuum and Circumstellar Disk)
- How they decided it was enough: _not stated_
- Limitation (authors): No Total Power data; line fluxes likely missing ≳20 %  
  > "The absence of the Total Power observations probably causes significant missing fluxes ($\gtrsim$20 %) for these line observations." (2 Observations and Data Reduction)
- Limitation (authors): Systemic velocity not known exactly  
  > "We do not know the systemic velocity of the target exactly" (3.4 CO Line Profiles)
- Limitation (authors): Viscous disk model is simple; more realistic treatments beyond scope  
  > "More realistic models, which are beyond the scope of the paper, require the following treatments" (Appendix)
- Caveat (inferred, ours): Disk interpretation rests on a marginally resolved source
- Caveat (inferred, ours): Outflow vs envelope identification is qualitative, with no kinematic modelling or mass/momentum estimates
- Caveat (inferred, ours): Class I assignment depends on a literature envelope mass and comparison with a small sample
- Caveat (inferred, ours): Cloud contamination and missing flux affect 12CO and 13CO interpretation

## Reproducibility

- Data public (paper): Project code and PI given; no explicit public statement  
  > "(Project code: 2016.1.00209.S, PI: Michihiro Takami)" (2 Observations and Data Reduction)
- Products in archive: _not stated_
- Missing: tclean parameters and masks
- Missing: line-free channels
- Missing: region definitions for line profiles
- Missing: flux calibrator models
- Data volume (inferred): ~20-60 GB for three EBs (12 m plus ACA) with high-resolution line SPWs
- Score (inferred): 3/5, Observations and the central fit are described, but imaging parameters are sparse and much of the analysis is qualitative.
- Rediscovery candidate: no, Numeric results are limited to a Gaussian fit, while the line analysis is largely qualitative and imaging parameters are missing.

## Links

- Method: (cite: McMullin07) (CASA)
- Method: (cite: Zhu07) (viscous disk temperature model)
- Companion: (cite: Takami18) (near-IR polarimetry of FUors and proposed evolutionary sequence)
- Companion: (cite: Kospal17c) (ALMA observations of V346 Nor used for comparison)

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.00451.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 55,
  "rate": 0.714
 },
 "evidence_ok": true
}
```
