# ALMA Resolves the Nuclear Disks of Arp 220

`2017ApJ...836...66S` | The Astrophysical Journal 2017 | first author: Scoville, Nick | arXiv: 1605.09381 | DOI: 10.3847/1538-4357/836/1/66

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the internal gas and dust distributions, kinematics and optical depths of the two nuclear disks of Arp 220 at 90 mas resolution?  
  > "The internal gas distribution and kinematics of both galactic nuclei are well-resolved for the first time." (abstract)
- Target **Arp 220 (West and East nuclei)**: coordinates West 15:34:57.224 +23:30:11.48; East 15:34:57.286 +23:30:11.32 (J2000, Table 1)  
  > "we adopt a luminosity distance D L = 87.9 Mpc and angular size distance D A = 85.0 Mpc (Armus et al. 2009)" (1. INTRODUCTION); "The Arp 220 observations were centered on z = 0.018486" (2. ALMA OBSERVATIONS AND DATA REDUCTION); z/distance z = 0.018486; D_L = 87.9 Mpc; D_A = 85.0 Mpc  
  > "we adopt a luminosity distance D L = 87.9 Mpc and angular size distance D A = 85.0 Mpc (Armus et al. 2009)" (1. INTRODUCTION); "The Arp 220 observations were centered on z = 0.018486" (2. ALMA OBSERVATIONS AND DATA REDUCTION); distance from Armus et al. 2009; redshift from Sanders et al. 1991  
  > "we adopt a luminosity distance D L = 87.9 Mpc and angular size distance D A = 85.0 Mpc (Armus et al. 2009)" (1. INTRODUCTION); "The Arp 220 observations were centered on z = 0.018486" (2. ALMA OBSERVATIONS AND DATA REDUCTION)

## Data provenance

- ALMA projects: 2015.1.00113.S
- bands: Band 3  
  > "The observations discussed here were in receiver Band 3" (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: TDM, 4 spectral windows, 1875 MHz each, 1.95 MHz channels; centered at 113.253, 103.073, 101.139 GHz plus CO(1-0)  
  > "Each window had a full bandwidth of 1875 MHz with 1.95 MHz resolution spectral channels." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: 40 12 m antennas  
  > "The data were taken with 40 12 m antennas" (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- configurations: _not stated_
- baselines: up to 11 km  
  > "The observations were done in a very extended configuration with baselines up to 11 km" (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- angular resolution: 0.08 x 0.10 arcsec at PA 25.7 deg (90 mas, 37 pc)  
  > "For all of the observations the synthesized beam was 0.08 × 0.10′′ at PA = 25.7◦." (Table 2)
- max recoverable scale: ~0.4 arcsec  
  > "good flux recovery is expected out to scales of ∼ 0.4′′" (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- sensitivity: 0.6 mJy/beam per 40 km/s channel (lower sideband), 0.8 mJy/beam (upper sideband)  
  > "an rms noise of 0.6 mJy beam −1 in 40 km s −1 channels in the lower sideband at ∼ 110 GHz) and 0.8 mJy beam −1 in 40 km s −1 channels in the upper sideband at 114 GHz." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- time on source: 30 minutes  
  > "the total integration time was 30 minutes (excluding calibrations)" (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- observing dates: 2015 November  
  > "were obtained in 2015 November for project #2015.1.00113.S" (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (115.2712 GHz)
- External data: Continuum fluxes at 4.7-32.5 GHz for both nuclei (Table 3)  
  > "32.5 0.08 × 0.06 33.4 6.5 ± 0.8 1570 Barcos-Muñoz et al. (2015)" (Table 3) [from Barcos-Muñoz et al. (2015)]
- External data: Submm dust optical depths and temperatures (tau434um=5.3 West, 1.7 East; 691 GHz fluxes)  
  > "Wilson et al. (2014) derive dust optical depths τ 434 µm = 5.3 and 1.7 for the West and East nuclei" (1. INTRODUCTION) [from Wilson et al. (2014)]
- External data: Empirical dust-emission to ISM mass calibration alpha_nu = (6.7±1.7)e19 erg/s/Hz/Msun  
  > "Scoville et al. (2015b) empirically calibrated the long wavelength dust emission from Herschel SPIRE with the CO(1-0) ISM masses" (3.5. West Nucleus ISM column densities and Mass) [from Scoville et al. (2015b)]
- External data: Single-dish CO(1-0) flux used for recovered fraction  
  > "This is 19% of the total single dish CO (1-0) line flux measured by Sanders et al. (1991) and Solomon et al. (1997)." (2. ALMA OBSERVATIONS AND DATA REDUCTION) [from Sanders et al. (1991); Solomon et al. (1997)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration done to improve dynamic range (no details)  
  > "Self-calibration was done to improve the dynamic range." (2. ALMA OBSERVATIONS AND DATA REDUCTION)

### Imaging

- task: CASA; Robust = 0, 1, 2 images made, only Robust = 1 used  
  > "The images were made with the parameter Robust = 0, 1 and 2; only the Robust = 1 images are used here." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum image from line- and absorption-free channels; subtraction done in image plane  
  > "The continuum subtraction was then done in the image plane." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Averaged 8 channels to 40 km/s resolution  
  > "Channel averaging over 8 of the original channels was done to reduce noise, resulting in data with velocity resolution of 40 km s−1" (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- final beam: 0.08 x 0.10 arcsec, PA 25.7 deg  
  > "For all of the observations the synthesized beam was 0.08 × 0.10′′ at PA = 25.7◦." (Table 2)
- final rms: _not stated_

### Inherited from earlier work

- Maximum-likelihood disk fitting procedure, modified to allow different emissivities on + and - sides of the major axis  
  > "This was carried out using the maximum likelihood procedure developed in Scoville et al. (1983)" (5. CO EMISSION DISTRIBUTION AND KINEMATICS) [from Scoville et al. (1983)]
- Dust-to-ISM-mass calibration and 25 K dust assumption  
  > "The bulk of the ISM dust in the nearby galaxies used for the calibration is at ∼ 25 K (see Scoville et al. 2015b)." (3.5. West Nucleus ISM column densities and Mass) [from Scoville et al. (2015b)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, deconvolver, masks, clean threshold
- Line-free channel ranges for continuum
- Self-calibration solution intervals and number of rounds
- CASA version and calibration/flux calibrator details
- Flux scale uncertainty
- Fitting free parameters, parametrization of rotation curve and emissivity, optimization details and uncertainties
- Primary beam correction treatment
- Details of IDL Gaussian fit setup

## Analysis recipe

1. **Re-reduce and image data**: Re-reduced and imaged in CASA, self-calibrated, Robust=1 images, image-plane continuum subtraction, 8-channel averaging  
  > "the data were rereduced and imaged using the Common Astronomy Software Applications package (CASA)." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
   - software: CASA
   - parameter: Robust = 1; 40 km/s channels  
  > "only the Robust = 1 images are used here" (2. ALMA OBSERVATIONS AND DATA REDUCTION)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure source fluxes and sizes**: 2D Gaussian fits to continuum and line images; deconvolved sizes via maximum likelihood  
  > "Sizes (FWHM) and major axis PA estimates obtained from 2d Gaussian fits using the IDL routine CURVEFIT." (Table 2)
   - software: IDL CURVEFIT, IDL MAX_LIKELIHOOD
   - fitting: Formal Gaussian fit errors  
  > "The uncertainties in the parameters were the formal errors from the Gaussian fitting." (Table 2)
   - validation: _not stated_
3. **Derive dust-only brightness temperature and optical depth**: Extrapolate 32 GHz flux with spectral index -0.60 to remove synchrotron/free-free at 112.3 GHz; compare TB with Wilson et al. tau scaled as nu^1.8  
  > "with a spectral index α = −0.60 determined between 7 and 32 GHz (see Figure 2)" (3.3. Dust Emission Fluxes and Brightness Temperatures)
   - assumption: Dust opacity kappa ∝ nu^1.8  
  > "If the dust opacity varies with the standard Galactic power-law ν1.8" (3.4. West Nucleus Luminosity)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive column density and mass in West nucleus**: Convert alpha_nu calibration to kappa_850um at 25 K, scale to 2.6 mm, find N_H2 for tau=1  
  > "Thus an H 2 column of 2.21 × 1026 H 2 cm−2 is required in order for τ 2.6mm ≃ 1." (3.5. West Nucleus ISM column densities and Mass)
   - assumption: Dust has standard Galactic properties; 25 K calibration temperature; filling factor of order unity  
  > "Clearly, these estimates are uncertain, given the assumption that the dust has standard interstellar dust properties and abundance" (3.5. West Nucleus ISM column densities and Mass)
   - fitting: _not stated_
   - validation: Compared with dynamical mass (factor 2 higher)  
  > "The mass so derived is approximately a factor 2 higher than the dynamical mass in the same region" (3.5. West Nucleus ISM column densities and Mass)
5. **Fit rotating-disk kinematic models to CO line profiles**: 2D thin planar disk with parametrized rotation curve and constant velocity dispersion fit to line profiles on a 60 mas grid; maximum likelihood  
  > "This model, including a parametrized rotation curve and gas velocity dispersion, was then fit to the observed CO line profiles on a well-sampled grid (60 mas spacing)" (5. CO EMISSION DISTRIBUTION AND KINEMATICS)
   - assumption: Infinitesimally thin disk, constant velocity dispersion, spherical approximation for dynamical mass M=RV^2/G  
  > "This modeling is with a 2D, infinitesimally thin planar disk with constant velocity dispersion as a function of radius." (5. CO EMISSION DISTRIBUTION AND KINEMATICS)
   - fitting: Maximum likelihood (Scoville et al. 1983 with modification)  
  > "with the modification that emissivities were allowed to be different on the + and - offset sides of the major axis." (5. CO EMISSION DISTRIBUTION AND KINEMATICS)
   - validation: Reduced chi2 ~4-6; observed vs model spectra in Appendix A  
  > "overall reduced χ2 ∼ 4 − 6 for both disks" (5. CO EMISSION DISTRIBUTION AND KINEMATICS)
6. **Disk thickness, dissipation timescale and energetics**: Scale height from equilibrium with sigma_v and Vrot (Eq. 8); dissipation time H/sigma; compare radiation and gas momentum  
  > "indicating H ranging from 1 to 30 pc at r < 50 pc." (5.6. Disk Thickness)
   - parameter: sigma_v(1d)=FWHM/2.3; f_a=1  
  > "velocity dispersions σ v(1d) = ∆v(FWHM)/2.3 from Table 4" (Figure 8 caption)
   - assumption: Mestel disk, self-gravitating; constant vertical dispersion; equilibrium  
  > "the vertical velocity dispersion is constant with radius and that the disks are in equilibrium" (5.6. Disk Thickness)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Re-reduction, self-calibration, imaging  
  > "the data were rereduced and imaged using the Common Astronomy Software Applications package (CASA)." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- **IDL CURVEFIT** : 2D Gaussian fits to sources  
  > "Peak position and fluxes obtained from 2d Gaussian fits using the IDL routine CURVEFIT." (Table 1)
- **IDL MAX_LIKELIHOOD** : Deconvolved sizes  
  > "The deconvolved sizes were obtained using the IDL routine MAX ~~L~~ IKELIHOOD." (Table 2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| West 112 GHz continuum peak flux | 13.1 | 0.05 | mJy/beam | 2 | Arp 220 West 112.26 15:34:57.224 23:30:11.48 32.1 13.1 ± 0.05 147.2 |
| East 112 GHz continuum peak flux | 3.1 | 0.04 | mJy/beam | 2 | Arp 220 East 112.26 15:34:57.286 23:30:11.32 14.0 3.1 ± 0.04 30.5 |
| West CO(1-0) total flux | 47.3 | not stated | Jy km/s | 2 | Arp 220 West CO (1 - 0) 15:34:57.224 23:30:11.49 47.3 3.33 ± 0.01 187 [b] |
| East CO(1-0) total flux | 27.8 | not stated | Jy km/s | 2 | Arp 220 East CO (1 - 0) 15:34:57.290 23:30:11.34 27.8 1.78 ± 0.01 175 [b] |
| West dust brightness temperature at 112 GHz | 121 (abstract: ~147) | not stated | K | 3 | 112.3 0.10 × 0.08 29.0 13.1 ± 0.5 121 [b] Scoville et al 2017 |
| West H2 column density for tau(2.6mm)~1 | 2.21e26 | not stated | cm^-2 | 4 | Thus an H 2 column of 2.21 × 1026 H 2 cm−2 is required in order for τ 2.6mm ≃ 1. |
| West central point mass | ~8e8 | not stated | Msun | 5 | Rotation curve: Point mass ∼ 8 × 10 [8] M ⊙ |
| Intrinsic line FWHM West / East | 250 / 120 | not stated | km/s | 5 | ∆v(FWHM) = 250 (West) and 120 (East) km s −1 |
| Disk inclination West / East | 30 / 45 | not stated | deg | 5 | Disk inclination i 30 ◦ |
| Dissipation timescale | 1e5 to 4e5 | not stated | yr | 6 | are 10 [5] to 4 × 10 [5] yrs. |
| Recovered CO flux fraction | 19% | not stated | percent of single-dish flux | 0 | This is 19% of the total single dish CO (1-0) line flux |

## Qualitative findings

- West nucleus shows a factor ~3 CO dip at the dust continuum peak  
  > "The depth of the hole is approximately a factor three compared with the immediately exterior ring" (4.1. CO Hole on the West Nucleus)

## Claim tuples

- H: Is the West nucleus dust optically thick at 2.6 mm? | E: Compare 112 GHz dust brightness temperature with submm results | R: TB ~147 K requires tau(2.6mm)~1 | F: Very high column N_H2>=2e26 cm^-2 | **supported**
- H: Do the nuclei host rotating disks with a central mass? | E: Disk model fit to CO line profiles | R: Point mass ~8e8 Msun in West; <1e8 in East | F: Central Keplerian component in West (possibly gas concentration) | **partially**
- H: Are line widths due to dissipative turbulence? | E: Estimate disk thickness and dissipation time | R: ~1e5 yr with no energy source | F: Line widths may be semi-coherent motions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust continuum at long wavelengths used as independent linear ISM probe; long wavelengths penetrate optically thick dust  
  > "The dust continuum provides an independent and linear probe of the overall ISM mass" (1. INTRODUCTION)
- Alternative: CO hole explanation via foreground self-absorption disfavored; favor thermalization or optically thin CO  
  > "We thus favor the first or second explanations to reasonably account for the CO hole in the West nucleus." (4.1. CO Hole on the West Nucleus)
- How they decided it was enough: _not stated_
- Limitation (authors): Only long-baseline data, no short spacings; large-scale flux resolved out  
  > "they do not recover flux associated with the large scale structures ≳0.5′′ or 200 pc" (5.2. Physical Structure of the Nuclear Disks)
- Limitation (authors): Simplified thin-disk model with constant dispersion; results preliminary  
  > "This is obviously a much simplified model to describe the central disks in a merger system" (5. CO EMISSION DISTRIBUTION AND KINEMATICS)
- Caveat (inferred, ours): No fit parameter uncertainties given; reduced chi2 of 4-6
- Caveat (inferred, ours): Mass from dust relies on Galactic opacity and 25 K calibration
- Caveat (inferred, ours): Point mass degenerate with velocity dispersion gradient
- Caveat (inferred, ours): Continuum contamination correction depends on extrapolated synchrotron

## Reproducibility

- Data public (paper): Project data linked via ALMA archive  
  > "This paper makes use of the following ALMA data:" (7. SUMMARY DISCUSSION)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Kinematic model parametrization and fit code
- Missing: Self-cal details
- Data volume (inferred): ~50-200 GB raw for the single long-baseline Band 3 execution
- Score (inferred): 3/5, Public data and clear flux measurements, but imaging and kinematic fitting details are sparse.
- Rediscovery candidate: no, Kinematic modeling recipe is incomplete, though continuum and line peaks could be re-measured.

## Links

- Method: Scoville et al. (1983) (Maximum likelihood disk fitting procedure)
- Method: Scoville et al. (2015b) (Dust emission to ISM mass calibration)
- Companion: Scoville et al. (2017) (Full modeling with complete datasets, planned)
- Related: Wilson et al. 2014 SMA 691 GHz
- Related: Barcos-Muñoz et al. 2015 VLA

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 67,
 "quote_pass_rate": 0.971,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 49,
  "rate": 0.613
 },
 "evidence_ok": false
}
```
