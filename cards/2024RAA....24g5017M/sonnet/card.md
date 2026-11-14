# Investigating Sulfur Chemistry in the HD163296 Disk

`2024RAA....24g5017M` | Research in Astronomy and Astrophysics 2024 | first author: Ma, Rong | arXiv: 2406.07896 | DOI: 10.1088/1674-4527/ad5771

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Detect and image CS 7-6 in the HD 163296 disk and use Nautilus chemical models to study sulfur chemistry and the C/O ratio  
  > "we present the detection of CS 7-6 toward HD 163296, using the data obtained with Atacama Large Millimeter/submillimeter Array (ALMA) and illustrate our astrochemical modeling on HD 163296" (Introduction)
- Target **HD 163296**: coordinates _not stated_; z/distance 101 pc  
  > "HD 163296 | A1$^1$ | 101$^3$ | 46.7$^2$ | 133.3$^2$" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01086.S
- bands: CS 7-6 near 342.883 GHz (band not named)  
  > "corresponding to a velocity width 0.85 km s$^{-1}$ at 342.883 GHz" (2.1 Observational Details)
- frequencies and spectral setup: Bandwidth 1.875 GHz, 1920 channels, channel width 976.562 kHz (0.85 km/s)  
  > "the bandwidth is 1.875 GHz and the channel number is 1920, resulting in a channel width 976.562 kHz" (2.1 Observational Details)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21.0 m to 3.6 km; 42 antennas  
  > "Forty-two antennas were used during the observations and the length of baselines ranges from 21.0 m to 3.6 km." (2.1 Observational Details)
- angular resolution: ~0.066 arcsec  
  > "resulting in a spatial resolution of $\sim$0.066$^{''}$" (2.1 Observational Details)
- max recoverable scale: 0.953 arcsec  
  > "The maximum recoverable scales of the observations is 0.953$^{''}$" (2.1 Observational Details)
- sensitivity: 1.9 mJy/beam per channel  
  > "The noise level of the line cube is 1.9 mJy beam$^{-1}$ per channel." (2.1 Observational Details)
- time on source: 28 minutes  
  > "The total on-source integration time was 28 minutes." (2.1 Observational Details)
- observing dates: _not stated_
- pi or archival as stated: Archival, PI Isella  
  > "extracted from the ALMA archive (project code 2016.1.01086.S; PI: Isella)" (2.1 Observational Details)
- Line: CS 7-6 (342.8828 GHz)
- External data: Disk density structure parameters (gas/dust surface density, Rc, gamma, scale height, etc.)  
  > "Surface density exponent $\gamma$ | 0.8 | (cite: 2021ApJS..257....5Z)" (Table 3) [from (cite: 2021ApJS..257....5Z)]
- External data: Gas temperature structure parameters  
  > "$z_0$ (AU) | 9 | (cite: 2021ApJS..257....4L)" (Table 3) [from (cite: 2021ApJS..257....4L)]
- External data: CS 2-1 column density and C2S, SO upper limits  
  > "derived the disk-integrated column density of the CS in the HD 163296 disk by observed the CS 2-1." (5.1) [from (cite: 2021ApJS..257...12L)]

## Processing

### Calibration

- pipeline or manual: ALMA supplied pipeline scripts  
  > "The data was calibrated by ALMA supplied pipeline scripts" (2.1 Observational Details)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 (phase J1751-1950, bandpass J1924-2914)  
  > "J1733 - 1304 was used as flux calibrator, J1751 - 1950 as phase calibrator and J1924 - 2914 as bandpass calibrator." (2.1 Observational Details)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "The line-only uv data was cleaned using “tclean” with “multiscale” algorithm" (2.1 Observational Details)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "a Briggs robustness parameter of 0.5" (2.1 Observational Details)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask from Czekala et al. 2021 parameters  
  > "The Keplerian mask was built based on the HD 163296 disk and star parameters used in (cite: 2021ApJS..257....2C)." (2.1 Observational Details)
- multiscale scales: _not stated_
- continuum subtraction: Subtracted in uv data  
  > "The continuum was subtracted towards the uv data." (2.1 Observational Details)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Keplerian mask built from disk and star parameters  
  > "The Keplerian mask was built based on the HD 163296 disk and star parameters used in (cite: 2021ApJS..257....2C)." (2.1 Observational Details) [from (cite: 2021ApJS..257....2C)]
- Gaussian-component modeling of radial profile  
  > "Following the method proposed by (cite: 2018ApJ...869L..42H), we modeled the radial profile of CS 7-6 as a sum of one or more Gaussian components" (2.2) [from (cite: 2018ApJ...869L..42H)]
- Dust grain population description  
  > "The following description of the dust grain population used in this study is adopted from (cite: 2021ApJS..257....5Z)." (3.2) [from (cite: 2021ApJS..257....5Z)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum subtraction
- tclean multiscale scales, image size, cell size, niter/threshold
- Keplerian mask parameters (width, rms threshold)
- bettermoments clip/mask details and GoFish settings
- Number of Gaussian components and initial guesses
- Nautilus run setup, final sizes of grain/dust, C/O variation implementation
- CASA/pipeline version

## Analysis recipe

1. **Image CS 7-6 cube**: tclean multiscale with Keplerian mask after uv continuum subtraction  
  > "The line-only uv data was cleaned using “tclean” with “multiscale” algorithm" (2.1 Observational Details)
   - software: CASA
   - parameter: Briggs robust 0.5  
  > "a Briggs robustness parameter of 0.5" (2.1 Observational Details)
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment map and radial profile**: Zeroth-moment with hybrid Keplerian+1sigma mask; shifted-and-stacked radial profile  
  > "We used a hybrid mask combining a Keplerian mask and 1$\sigma$ clip to mask any pixels below this threshold." (2.2)
   - software: bettermoments, GoFish
   - assumption: Inclination 46.7, PA 133.3, M*=2 Msun, d=101 pc  
  > "HD 163296 | A1$^1$ | 101$^3$ | 46.7$^2$ | 133.3$^2$" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit ring structure**: Sum of Gaussians fit to radial profile  
  > "we modeled the radial profile of CS 7-6 as a sum of one or more Gaussian components using the Levenberg-Marquardt minimization implementation in `LMFIT`" (2.2)
   - software: LMFIT
   - fitting: Levenberg-Marquardt least squares  
  > "using the Levenberg-Marquardt minimization implementation in `LMFIT`" (2.2)
   - validation: _not stated_
4. **Chemical modeling**: Nautilus three-phase model run for 1 Myr cloud stage then 1e7 yr disk with parametrized disk, RADMC3D dust temperature, two-layer gas temperature; vary C/O 0.5-1.5  
  > "we simulated the chemical composition of the disk for $10^7$ years using a cosmic-ray ionization rate of $\rm 1.3\times10^{-17}\,s^{-1}$." (3.2)
   - software: Nautilus, RADMC3D
   - assumption: Cloud stage: T=10 K, nH=2e4 cm-3, Av=15, zeta=1.3e-17 s-1  
  > "a grain and gas temperature of 10 K, the gas density of $\rm n_H= 2\times10^4\,cm^{-3}$, the visual extinction of 15 mag" (3.1)
   - fitting: _not stated_
   - validation: Compared column densities to Le Gal et al. 2021 LTE values and upper limits  
  > "We compared the model results against existing observationally deduced fractional column densities" (5.1)

## Software

- **CASA** : calibration and imaging  
  > "then was imaged using Common Astronomy Software Application package (CASA)" (2.1 Observational Details)
- **bettermoments** : moment maps  
  > "we used the Python package `bettermoments`" (2.2)
- **GoFish** : radial profile of stacked spectra  
  > "using the `radial profile` function in `GoFish`" (2.2)
- **LMFIT** 1.0.1: Gaussian fits to radial profile  
  > "Levenberg-Marquardt minimization implementation in `LMFIT`" (2.2)
- **Nautilus** : three-phase chemical model  
  > "we use the Nautilus three-phase model" (3.1)
- **RADMC3D** : dust temperature  
  > "we calculate the dust temperature structure using the Monte Carlo radiative transfer code RADMC3D" (3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CS 7-6 detection significance | 24 | not stated | sigma | 2 | The detection is made at a 24 $\sigma$ confidence level |
| Peak integrated intensity | 104 | rms 4.3 | mJy beam-1 km s-1 | 2 | with a peak flux of 104 mJy beam$^{-1}$ km s$^{-1}$, and rms of 4.3 mJy beam$^{-1}$ km s$^{-1}$ |
| Disk-integrated flux S_v Δv (Rmax) | 4.95 | 0.32 | Jy beam-1 (as printed) | 2 | 2.000$\pm$0.017 / 4.95$\pm$0.32 |
| CS 7-6 ring centers | ~26 to ~49 (gap ~41) | not stated | AU | 3 | CS 7-6 emission has two bright rings with centers ranging from $\sim$26 to $\sim$49 AU |

## Qualitative findings

- Modeled CS column density ~1e13 cm-2 beyond 100 AU, within an order of magnitude of observed; C2S below upper limit  
  > "Our model results are consistent with the observationally deduced fractional CS column density (Within an order of magnitude range)." (5.1)

## Claim tuples

- H: Is CS 7-6 detected and structured in HD 163296? | E: Imaged archival ALMA data | R: 24 sigma detection, rings at ~26 and ~49 AU | F: CS 7-6 shows a central hole and ring structure | **supported**
- H: Does CS/SO trace C/O? | E: Varied C/O 0.5-1.5 in models | R: N[CS]/N[SO] changes by over one order of magnitude | F: N[CS]/N[SO] is a promising C/O probe; C/O may be >1.1 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot determine best-fit C/O due to observational limitations  
  > "Due to observational limitations, we are unable to determine the best fitting model for the C/O ratio in the HD 163296 disk." (5.2)
- Caveat (inferred, ours): Model not fit to the CS 7-6 data; comparison only with CS 2-1 LTE column densities
- Caveat (inferred, ours): C/O>1.1 inference weak, based on SO upper limits only
- Caveat (inferred, ours): Typos in Table 3 (q_atm/q_mid labels) and Table 2 units

## Reproducibility

- Data public (paper): Data from ALMA archive  
  > "extracted from the ALMA archive" (2.1 Observational Details)
- Products in archive: _not stated_
- Missing: tclean parameters and line-free channels
- Missing: Nautilus setup details and C/O implementation
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Public data and partial imaging recipe, but many imaging and modeling settings missing.
- Rediscovery candidate: no, Imaging recipe incomplete and main modeling results are not easily reproducible.

## Links

- Method: (cite: 2021ApJS..257....2C) (Keplerian mask parameters)
- Method: (cite: 2021ApJS..257....5Z) (Disk density model)
- Companion: (cite: 2021ApJS..257...12L) (CS 2-1 observations and column densities)
- Related: MAPS

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 40,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
