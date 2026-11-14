# The Complex Morphology of the Young Disk MWC 758: Spirals and Dust Clumps around a Large Cavity

`2018ApJ...853..162B` | The Astrophysical Journal 2018 | first author: Boehler, Y. | arXiv: 1712.08845 | DOI: 10.3847/1538-4357/aaa19c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the dust and gas morphology of the MWC 758 disk (cavity, clumps, spirals) and what do they imply about its origin?  
  > "The outer disk features two bright emission clumps at radii of $\sim$ 47 and 82 au that present azimuthal extensions and form a double-ring structure." (abstract)
- Target **MWC 758**: coordinates RA 05h30m27.536s, Dec +25d19m56.70s  
  > "R.A. = 05$^h$30$^m$27$^s$.536 and decl. = +25$^\circ$ 19$'$ 56$''$.70, cospatial with the Herbig star position." (3.1 Dust continuum emission); "located at a distance of 151 $\pm$ 9 pc, based on the stellar parallax measured by the Gaia space telescope" (Introduction); z/distance 151 ± 9 pc  
  > "R.A. = 05$^h$30$^m$27$^s$.536 and decl. = +25$^\circ$ 19$'$ 56$''$.70, cospatial with the Herbig star position." (3.1 Dust continuum emission); "located at a distance of 151 $\pm$ 9 pc, based on the stellar parallax measured by the Gaia space telescope" (Introduction); distance from Gaia parallax  
  > "R.A. = 05$^h$30$^m$27$^s$.536 and decl. = +25$^\circ$ 19$'$ 56$''$.70, cospatial with the Herbig star position." (3.1 Dust continuum emission); "located at a distance of 151 $\pm$ 9 pc, based on the stellar parallax measured by the Gaia space telescope" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00725.S
- bands: Band 7, Cycle 3  
  > "We observed MWC 758 using ALMA in Cycle 3 at Band 7 as part of the project 2012.1.00725.S." (2 Observations and data reduction)
- frequencies and spectral setup: four spws at 329.34, 330.60, 341.01, 343.01 GHz; line spws 234.4 MHz wide, 61.0 kHz channels (0.055 km/s), Hanning smoothed  
  > "four separate spectral windows centered at 329.34, 330.60, 341.01 and 343.01 GHz." (2 Observations and data reduction); "The channel width in these two spectral windows is 61.0 kHz (0.055 km s$^{-1}$)." (2 Observations and data reduction)
- continuum bandwidth: about 3.6 GHz total, centered 342 GHz  
  > "with a total bandwidth of about 3.6 GHz." (2 Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m–1.6 km (Sep 1); 43.3 m–2.3 km (Sep 24)  
  > "Baseline lengths ranged between 15.1 m and 1.6 km on September 1, and between 43.3 m and 2.3 km on September 24." (2 Observations and data reduction)
- angular resolution: 0.1''-0.2'' (beams 0.16x0.14'' Briggs 0; 0.12x0.11'' super-uniform; 0.23x0.18'' gas)  
  > "This gives an FWHM beam size of 0.12$''$$\times$0.11$''$ and an rms noise of 115 $\mu$Jy beam$^{-1}$." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 83 uJy/beam (Briggs 0), 115 uJy/beam (super-uniform); 13CO 8 mJy/beam/channel, C18O 11.0 mJy/beam/channel  
  > "an rms noise of 8 mJy beam$^{-1}$ per channel in $^{13}$CO and 11.0 mJy beam$^{-1}$ per channel in C$^{18}$O." (2 Observations and data reduction)
- time on source: about 58 minutes  
  > "The total on-source time spent on MWC 758 was about 58 minutes." (2 Observations and data reduction)
- observing dates: 2015 September 1 and 24  
  > "Observations were performed on September 1 and 24, 2015, when 35 and 34 antennas were available, respectively." (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 13CO J=3-2 (not stated)
- Line: C18O J=3-2 (not stated)
- Other facility **VLT/SPHERE (Benisty 2015)**: near-IR Y-band scattered light images compared with ALMA  
  > "(cite: Beni2015) redetected the spirals with VLT/SPHERE in scattered light in $Y$ Band (1.04 $\mu$m)" (4.2 Comparison)
- Other facility **Gaia**: parallax distance  
  > "based on the stellar parallax measured by the Gaia space telescope" (Introduction)
- External data: Near-IR scattered light images of the spirals  
  > "that we also compare with previous images obtained in near-IR scattered light (cite: Beni2015)" (Introduction) [from (cite: Beni2015)]
- External data: Stellar temperature 8130 K (A5e)  
  > "with a temperature at the surface of 8130 K (cite: vdA1998)" (4.1 Modeling) [from (cite: vdA1998)]
- External data: 13CO and C18O abundances 9e-7 and 1.35e-7  
  > "are assumed to be 9$\times$10$^{-7}$, and 1.35$\times$10$^{-7}$, respectively (cite: Qi2011)" (4.1 Modeling) [from (cite: Qi2011)]
- External data: Disk inclination 21 deg  
  > "considering an inclination of 21 degrees (cite: Isel2010)" (3.3 Disk dynamic) [from (cite: Isel2010)]

## Processing

### Calibration

- pipeline or manual: calibrated by NRAO staff  
  > "The data were calibrated by the National Radio Astronomy Observatory (NRAO) staff using the CASA software package version 4.3.1" (2 Observations and data reduction)
- casa version: CASA 4.3.1  
  > "using the CASA software package version 4.3.1" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+180, ~2.3 Jy adopted  
  > "The flux scale was determined with observations of J0510$+$180, for which a flux of $\approx 2.3$ Jy was adopted." (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: phase solint 30 s, then amplitude with scan length (~5 min); derived on dust, applied to lines  
  > "We used a time interval of 30 seconds for self-calibrating the phase and in a second step the scan length ($\sim$ 5 mn) for the amplitude calibration." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: gas: natural (continuum Briggs 0; super-uniform for 0.12'' image; CO moment maps Briggs 2)  
  > "First, we used a Briggs parameter equal to 0, an intermediate value" (2 Observations and data reduction); "imaged using a Briggs factor of 2, to optimize the signal-to-noise ratio" (3.2 13CO and C18O)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: applied for moment 0 maps; peak intensity maps made without subtracting continuum  
  > "the peak emission map was obtained without subtracting the continuum emission" (3.2 13CO and C18O)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.16x0.14'' (Briggs 0), 0.12x0.11'' (super-uniform), 0.23x0.18'' (gas)  
  > "yielding an FWHM beam size of 0.16$''$$\times$0.14$''$ and an rms noise of 83 $\mu$Jy beam$^{-1}$." (2 Observations and data reduction)
- final rms: 83 uJy/beam and 115 uJy/beam continuum  
  > "an rms noise of 83 $\mu$Jy beam$^{-1}$" (2 Observations and data reduction)

### Inherited from earlier work

- Modeling approach (double-Gaussian surface density, radiative transfer)  
  > "The model discussed below follows the analysis presented in (cite: Boeh2017)." (4.1 Modeling) [from (cite: Boeh2017)]
- Dust properties (size distribution, composition)  
  > "These dust properties were previously used in (cite: Boeh2017)" (4.1 Modeling) [from (cite: Boeh2017)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, clean threshold, masks and deconvolver
- Line-free channels and continuum subtraction method
- Channel width/velocity resolution of the CO imaging
- Moment map clipping thresholds
- Fit cost function and ranges for manual model fitting
- Dust spiral fit procedure (deferred to Shen, Tang et al. in prep.)
- Beam convolution for model comparison

## Analysis recipe

1. **Image continuum and CO lines**: Imaging with Briggs 0 and super-uniform for continuum, natural/Briggs 2 for lines after self-calibration  
  > "We imaged the gas emission with natural weighting." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Morphology and kinematics**: Deprojected intensity maps with i=21 deg, PA=62 deg; crests, peak maps, moment maps; Keplerian comparison  
  > "The orbital radius has been calculated by assuming an inclination of 21$^\circ$ and a P.A. of 62$^\circ$ for the disk." (3.1 Dust continuum emission)
   - fitting: _not stated_
   - validation: Compared with warped disk simulations of Facchini 2018  
  > "we compared our observations with the simulations of (cite: Facc2018)" (3.3 Disk dynamic)
3. **Radiative transfer modeling of dust and gas surface density**: Two-Gaussian surface density in three azimuthal sectors; RADMC-3D temperature; fit dust continuum and integrated CO radial profiles  
  > "The temperature in the disk is determined by carrying out a two-dimensional (r,z) radiative transfer using the code RADMC-3D" (4.1 Modeling)
   - software: RADMC-3D
   - assumption: gas-to-dust 100; opacity 2.9 cm2/g at 0.88 mm; grain size power law -3.5 from 0.05 um to 1 mm; L=15.3 Lsun, R=2.0 Rsun, M=1.4 Msun; hydrostatic gas, dust mixed  
  > "yields an opacity at 0.88 millimeter of 2.9 cm$^{2}$ g$^{-1}$" (4.1 Modeling)
   - fitting: best models found manually  
  > "The models that best fit the data are represented by dotted lines and were found manually." (4.1 Modeling)
   - validation: Settling tests (scale height reduced by 5 and 10) gave negligible changes  
  > "only negligible changes were observed between the models" (4.1 Modeling)
4. **Fit spiral pitch angles to near-IR and 13CO**: Linear regression fit of logarithmic spirals R=R0 exp[tan(alpha)(theta-theta0)]  
  > "Using a linear regression method, we fitted the position of the IR radial maxima by spirals, with a constant pitch angle" (4.2 Comparison)
   - fitting: linear regression  
  > "Using a linear regression method, we fitted the position of the IR radial maxima by spirals, with a constant pitch angle" (Comparison of the dust and $^{13}$CO peak emission with the IR Scattered Light)
   - validation: _not stated_

## Software

- **CASA** 4.3.1: calibration (by NRAO) and imaging  
  > "using the CASA software package version 4.3.1" (2 Observations and data reduction)
- **RADMC-3D** : 2D radiative transfer for disk temperature  
  > "using the code RADMC-3D (cite: Dull2012)" (4.1 Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| North clump peak intensity (Briggs 0) | 17.2 | not stated | mJy/beam | 2 | The brightest clump has a peak intensity of 17.2 mJy beam$^{-1}$ |
| South clump peak intensity (Briggs 0) | 13.7 | not stated | mJy/beam | 2 | The second clump has a peak intensity of 13.7 mJy beam$^{-1}$ |
| Systemic velocity | 5.90 | 0.05 | km/s | 2 | the disk has a systemic velocity of 5.90 $\pm$ 0.05 km s$^{-1}$ |
| Stellar mass from Keplerian rotation | 1.4 | 0.3 | Msun | 2 | Keplerian rotation around a central star of 1.4 $\pm$ 0.3 solar masses |
| Dust surface density enhancement south/north clump | 2.5 / 6.5 | not stated | dimensionless | 3 | have surface densities of about 2.5 and 6.5 times, respectively, the values encountered in the underlying rings |
| Gas mass | 1.3e-3 | not stated | Msun | 3 | the gas mass in the disk is about 1.3$\times$10$^{-3}$ M$_\odot$ and the dust mass about 3.0$\times$10$^{-5}$ M$_\odot$ |
| Dust mass | 3.0e-5 | not stated | Msun | 3 | the gas mass in the disk is about 1.3$\times$10$^{-3}$ M$_\odot$ and the dust mass about 3.0$\times$10$^{-5}$ M$_\odot$ |
| SE spiral pitch angle | 12.7 | not stated | deg | 4 | has a pitch angle of 12.7$^\circ$ and is located at $R_0$ = 43.0 au at P.A. = 50$^\circ$ |
| NW spiral pitch angle | 12.9 | not stated | deg | 4 | features a similar pitch angle of 12.9$^\circ$ |
| Dust-to-gas ratio in clumps | ~0.1 | not stated | dimensionless | 3 | increase of the dust-to-gas ratio in the dust clumps to a value of about 0.1 |

## Qualitative findings

- Spirals seen in near-IR are also seen in 13CO peak emission and (slightly offset outward) in dust continuum  
  > "The spirals seen in the dust continuum emission present, however, a slight shift of a few au towards larger radii" (abstract)

## Claim tuples

- H: Are the dust clumps local dust enhancements? | E: Radiative transfer fits of dust and gas profiles along clump sectors | R: Dust surface density higher by 2.5 (south) and 6.5 (north); no gas enhancement | F: Dust trapping with raised dust-to-gas ~0.1 | **supported**
- H: Do the near-IR spirals appear at the midplane and in gas? | E: Compared 13CO peak and continuum with SPHERE image | R: Spirals in 13CO coincide with IR; dust spirals shifted outward | F: Spirals seen with three tracers | **supported**
- H: Is there a warped inner disk? | E: Detected inner continuum source, velocity twist, azimuthal minimum | R: Unresolved source 0.83 mJy/beam within cavity | F: Consistent with mildly warped inner disk | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational instability rejected because disk mass is too low  
  > "is not massive enough to be gravitationally unstable" (5.1 Structure of the disk)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas resolution (~0.2'') is lower and S/N lower, so gas substructure cannot be probed  
  > "does not allow to probe as efficiently substructures" (4.1 Modeling)
- Caveat (inferred, ours): Manual model fits without uncertainties
- Caveat (inferred, ours): Warp interpretation is qualitative
- Caveat (inferred, ours): Only three azimuthal sectors modeled

## Reproducibility

- Data public (paper): project code given; public status not stated  
  > "as part of the project 2012.1.00725.S" (2 Observations and data reduction)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Fitting details
- Missing: Dust spiral fit
- Data volume (inferred): ~50-100 GB raw for two Band 7 executions
- Score (inferred): 3/5, Data identified and key settings partly given, but imaging details and manual fitting are underspecified.
- Rediscovery candidate: no, Manual model fitting and missing imaging parameters hinder exact reproduction.

## Links

- Method: (cite: Boeh2017) (Modeling approach followed)
- Companion: (cite: Beni2015) (Near-IR SPHERE images compared)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 69,
  "stated": 43,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
