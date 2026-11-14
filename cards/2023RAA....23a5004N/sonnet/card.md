# Contributions of Rotation, Expansion and Line Broadening to the Morphology and Kinematics of the Inner CSE of Oxygen-rich AGB Star R Hya

`2023RAA....23a5004N` | Research in Astronomy and Astrophysics 2023 | first author: Nhung, Pham Tuyet | arXiv: 2207.06690 | DOI: 10.1088/1674-4527/aca06f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars
- Question: How do rotation, radial expansion and line broadening contribute to the morphology and kinematics of the inner CSE of R Hya, and is the SiO high-velocity emission Keplerian rotation or line broadening?  
  > "The aim of the present article is to illustrate this point using as an example the oxygen-rich AGB star R Hya." (Introduction)
- Target **R Hya**: coordinates _not stated_; z/distance 124 (+12/-10) pc Hipparcos; 148 (+11/-10) pc Gaia EDR3  
  > "Hipparcos estimates a distance of $124\substack{+12 \\ -10}$ pc (cite: vanLeeuwen2007) and Gaia EDR3 of $148\substack{+11 \\ -10}$ pc (cite: Gaia2021)." (Introduction); distance from van Leeuwen 2007; Gaia EDR3  
  > "Hipparcos estimates a distance of $124\substack{+12 \\ -10}$ pc (cite: vanLeeuwen2007) and Gaia EDR3 of $148\substack{+11 \\ -10}$ pc (cite: Gaia2021)." (Introduction)

## Data provenance

- ALMA projects: 2018.1.00659.L
- bands: _not stated_
- frequencies and spectral setup: SiO(5-4) 217.1049 GHz (spw 27); CO(2-1) 230.5380 GHz (spw 31)  
  > "Images of the SiO(5-4) emission (frequency of 217.1049 GHz, spectral window 27) and of the CO(2-1) emission (frequency of 230.5380 GHz, spectral window 31)" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration of ATOMIUM, 44 antennas  
  > "made on 11 July 2019 and using 44 antennas with baselines covering between 0.11 and 12.6 km" (Observations and data reduction)
- baselines: 0.11 to 12.6 km  
  > "baselines covering between 0.11 and 12.6 km" (Observations and data reduction)
- angular resolution: 64 x 30 mas PA 66 deg (SiO); 58 x 28 mas PA 65 deg (CO)  
  > "resulting in beams of 64 mas $\times$ 30 mas (FWHM), PA=66$^\circ$, for the SiO line and 58 mas $\times$ 28 mas, PA=65$^\circ$, for the CO line" (Observations and data reduction)
- max recoverable scale: 0.6 arcsec  
  > "corresponding to a maximum recoverable scale[^1] of 0.6 arcsec" (Observations and data reduction)
- sensitivity: 0.98 mJy/beam (continuum, SiO); 0.90 mJy/beam (CO)  
  > "noise level ($\sigma$) of 0.98 mJy beam$^{-1}$ for continuum and the SiO line and 0.90 mJy beam$^{-1}$ for the CO line" (Observations and data reduction)
- time on source: _not stated_
- observing dates: 11 July 2019  
  > "made on 11 July 2019" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: SiO 5-4 (217.1049 GHz)
- Line: CO 2-1 (230.5380 GHz)
- External data: Stellar distances (Hipparcos, Gaia EDR3)  
  > "Hipparcos estimates a distance of $124\substack{+12 \\ -10}$ pc" (Introduction) [from (cite: vanLeeuwen2007); (cite: Gaia2021)]
- External data: Rotation axis PA of -20 deg and companion/ring interpretation from Homan2021  
  > "Assuming the position angle of the projected rotation axis to be $-$20$^\circ$ as estimated by (cite: Homan2021)" (3.2 The inner region) [from (cite: Homan2021)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: GILDAS/IMAGER, no preliminary continuum subtraction  
  > "have been produced, without preliminary continuum subtraction, using GILDAS[^2]/IMAGER[^3] with robust weighting (weight=1)" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: robust weighting (weight=1)  
  > "using GILDAS[^2]/IMAGER[^3] with robust weighting (weight=1)" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: none before imaging  
  > "without preliminary continuum subtraction" (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation and calibration details deferred to ATOMIUM papers  
  > "We refer the reader to (cite: Homan2021) and (cite: Gottlieb2022) for details." (Observations and data reduction) [from (cite: Homan2021); (cite: Gottlieb2022)]
- Systemic velocity -10.1 km/s  
  > "Doppler velocities, $V_z$, are referred to a systemic velocity of $-$10.1 km s$^{-1}$." (Observations and data reduction) [from not stated]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA version and calibrated visibilities source
- Channel width and velocity resolution of the cubes
- Image size and cell size
- Masking/cleaning threshold and deconvolver settings
- Exact regions and velocity windows for moment maps
- Reason for the beam difference between GILDAS and CASA remains unresolved
- Self-calibration usage

## Analysis recipe

1. **Image SiO and CO cubes**: GILDAS/IMAGER imaging with robust weighting, no continuum subtraction  
  > "using GILDAS[^2]/IMAGER[^3] with robust weighting (weight=1)" (Observations and data reduction)
   - software: GILDAS, IMAGER
   - fitting: _not stated_
   - validation: Beam elongation 20% larger than CASA imaging, cause unknown  
  > "the elongation of the beam is 20% larger using GILDAS than using CASA[^4] for imaging" (Observations and data reduction)
2. **Moment maps and spectra**: Moment 0 and 1 maps of SiO; spectra integrated over circles of 35, 300, 500 mas  
  > "The Doppler velocity spectra are integrated over circles of different radii, 35 mas, 300 mas and 500mas." (3.1 Overview)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit rotation in inner region**: Sine-wave fit of CO mean Doppler velocity vs position angle averaged over ring 50<R<100 mas  
  > "A sine wave fit gives $\langle V_z \rangle=2.1\sin(\omega+4^\circ)$ km s$^{-1}$." (3.2 The inner region)
   - fitting: sine wave fit  
  > "A sine wave fit gives $\langle V_z \rangle=2.1\sin(\omega+4^\circ)$ km s$^{-1}$." (3.2 The inner region)
   - validation: Compared with Homan2021 axis estimate  
  > "a difference that is acceptable within errors" (3.2 The inner region)
4. **Measure line broadening vs radius**: Red-side end-point velocity of spectra in four quadrants of four rings, averaged per ring  
  > "In each spectrum we evaluate the Doppler velocity of the end point of the spectrum (above continuum) on the red side where absorption is unimportant." (3.2 The inner region)
   - fitting: _not stated_
   - validation: Rms scatter across the four quadrants  
  > "The values quoted after the $\pm$ sign are the rms deviations with respect to the mean for the four quadrants of a same ring." (3.2 The inner region)
5. **PV maps in outer region**: Vz vs position angle in rings 0.1-0.2, 0.2-0.3, 0.3-0.4 arcsec  
  > "integrated in three successive rings: $0.1<R<0.2$ arcsec, $0.2<R<0.3$ arcsec and $0.3<R<0.4$ arcsec" (3.3 The outer region)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS/IMAGER** : Imaging of SiO and CO cubes  
  > "using GILDAS[^2]/IMAGER[^3] with robust weighting (weight=1)" (Observations and data reduction)
- **CASA** : Comparison imaging showing different beam elongation  
  > "the elongation of the beam is 20% larger using GILDAS than using CASA[^4] for imaging" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sine fit of CO mean Vz in 50<R<100 mas | 2.1 sin(omega+4deg) | axis PA uncertainty at least ±10 deg | km/s | 3 | A sine wave fit gives $\langle V_z \rangle=2.1\sin(\omega+4^\circ)$ km s$^{-1}$. |
| Shift between blue- and red-shifted SiO spectra | 5 | ±1 | km/s | 2 | We evaluate the shift between the blue-shifted and red-shifted spectra as 5$\pm$1 km s$^{-1}$ |
| Red end-point velocity in ring 0-40 mas | 18.5 | 0.9 | km/s | 4 | 18.5$\pm$0.9 km s$^{-1}$, 15.0$\pm$0.8 km s$^{-1}$, 10.5$\pm$1.2 km s$^{-1}$ and 7.1$\pm$0.7 km s$^{-1}$ |
| Red end-point velocity in ring 40-80 mas | 15.0 | 0.8 | km/s | 4 | 18.5$\pm$0.9 km s$^{-1}$, 15.0$\pm$0.8 km s$^{-1}$, 10.5$\pm$1.2 km s$^{-1}$ and 7.1$\pm$0.7 km s$^{-1}$ |
| Red end-point velocity in ring 80-120 mas | 10.5 | 1.2 | km/s | 4 | 18.5$\pm$0.9 km s$^{-1}$, 15.0$\pm$0.8 km s$^{-1}$, 10.5$\pm$1.2 km s$^{-1}$ and 7.1$\pm$0.7 km s$^{-1}$ |
| Red end-point velocity in ring 120-160 mas | 7.1 | 0.7 | km/s | 4 | 18.5$\pm$0.9 km s$^{-1}$, 15.0$\pm$0.8 km s$^{-1}$, 10.5$\pm$1.2 km s$^{-1}$ and 7.1$\pm$0.7 km s$^{-1}$ |
| Line broadening at line base over 20-140 mas | ~25 | ±2 | km/s | 4 | This result implies a broadening of $\sim$25$\pm$2 km s$^{-1}$ at the base of the line |

## Qualitative findings

- Outer region (100-500 mas) shows radial expansion of an inclined equatorial enhancement with terminal velocity ~7 km/s  
  > "The terminal velocity reached within this region is $\sim$7 km s$^{-1}$" (Summary and discussion)

## Claim tuples

- H: Is the inner CSE dominated by rotation and line broadening? | E: Moment maps, ring spectra and sine fit of SiO and CO | R: Projected rotation ~2 km/s, line broadening confined within ~50-100 mas | F: Inner region within ~100 mas (14 au) is dominated by rotation and strong line broadening | **supported**
- H: Are the high velocities near the star Keplerian rotation (Homan2021)? | E: PV diagrams along PA 70 and 160 deg without continuum subtraction | R: Maximal Vz rises from ~8 to ~18 km/s from 80 to 30 mas, unlike a Keplerian trend | F: High velocities reflect line broadening, not Keplerian rotation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Keplerian rotation of a ring/disc with a companion (Homan2021) is disfavoured  
  > "Under such conditions it is difficult to reliably describe the rotation as Keplerian." (Summary and discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Subtracted continuum map is an order of magnitude smaller than its terms; no radiative transfer simulation, important uncertainties  
  > "Note that the subtracted intensity is an order of magnitude smaller than the terms of the subtraction, implying important uncertainties." (3.2 The inner region)
- Caveat (inferred, ours): Purely qualitative analysis without radiative transfer or kinematic modelling
- Caveat (inferred, ours): Resolution (~20 mas sigma) comparable to the region studied
- Caveat (inferred, ours): Opacity of SiO limits interpretation
- Caveat (inferred, ours): Line broadening vs rotation not quantitatively separated

## Reproducibility

- Data public (paper): ALMA open access data used (project 2018.1.00659.L)  
  > "whose open access policy means invaluable support and encouragement for Vietnamese astrophysics" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust weighting
- Missing: Exact velocity windows and region definitions
- Missing: Calibration details
- Data volume (inferred): ~50-100 GB for the extended-configuration ATOMIUM execution blocks
- Score (inferred): 3/5, Public data and simple analysis, but imaging parameters are sparse and results are mostly qualitative.
- Rediscovery candidate: no, Recipe incomplete and results mostly qualitative.

## Links

- Method: (cite: Homan2021) (ATOMIUM data and R Hya analysis)
- Method: (cite: Gottlieb2022) (ATOMIUM observations and reduction details)
- Companion: (cite: Homan2021) (Alternative Keplerian interpretation of same data)
- Related: ATOMIUM

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 32,
  "rate": 0.478
 },
 "evidence_ok": true
}
```
