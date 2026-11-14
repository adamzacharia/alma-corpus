# Double DCO<SUP>+</SUP> Rings Reveal CO Ice Desorption in the Outer Disk Around IM Lup

`2015ApJ...810..112O` | The Astrophysical Journal 2015 | first author: Öberg, Karin I. | arXiv: 1508.07296 | DOI: 10.1088/0004-637X/810/2/112

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Where is CO ice desorbed in the IM Lup disk, as traced by the DCO+ emission morphology compared with C18O and H13CO+ and a disk chemistry model?  
  > "Non-thermal desorption should result in volatile-enriched gas in disk-regions where complete freeze-out is otherwise expected." (abstract)
- Target **IM Lup**: coordinates _not stated_; z/distance 155 pc  
  > "the IM Lup disk, located at a distance of 155 pc (cite: Lombardi08)" (Introduction); "We assumed an inclination of 49$^\circ$ and a position angle of -35$^\circ$ for these calculations (cite: Pinte08; Panic09)." (Observational Results); distance from Lombardi et al. 2008  
  > "the IM Lup disk, located at a distance of 155 pc (cite: Lombardi08)" (Introduction); "We assumed an inclination of 49$^\circ$ and a position angle of -35$^\circ$ for these calculations (cite: Pinte08; Panic09)." (Observational Results)

## Data provenance

- ALMA projects: 2013.1.00226.S
- bands: Band 6  
  > "the correlator was configured to process 14 SPWs in a different part of the Band 6 spectrum." (Observations and Data Reduction)
- frequencies and spectral setup: July 6: 13 SPWs, 12 with 61 kHz resolution and 59 MHz bandwidth, one with 469 MHz bandwidth; July 17: 14 SPWs, 61 kHz resolution  
  > "The spectral resolution $\delta\nu$ and bandwidth for 12 of the SPW were 61 kHz and 59 MHz, respectively; the remaining SPW had a coarser resolution with a bandwidth of 469 MHz." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 31 antennas (2014 July 6) and 32 antennas (2014 July 17)  
  > "on 2014 July 6 with 31 antennas (targeting DCO$^+$ and C$^{18}$O) and on 2014 July 17 with 32 antennas (targeting H$^{13}$CO$^+$)." (Observations and Data Reduction)
- configurations: _not stated_
- baselines: 15–650 m  
  > "The antenna separations spanned baselines of 15–650 m." (Observations and Data Reduction)
- angular resolution: ~0.7'' x 0.5'' synthesized beam  
  > "The CLEANed maps were restored with a synthesized beam with FWHM dimensions of $\sim0.7\ensuremath{''} \times 0.5\ensuremath{''}$." (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum RMS ~0.24 mJy/beam; 4-6 mJy in 0.2 km/s channels  
  > "The resulting RMS noise level in 0.2 km s$^{-1}$ binned channels is 4-6 mJy." (Observations and Data Reduction)
- time on source: ~21 minutes in each execution  
  > "The total on source integration time was $\sim$21 minutes in each execution." (Observations and Data Reduction)
- observing dates: 2014 July 6 and 2014 July 17  
  > "on 2014 July 6 with 31 antennas (targeting DCO$^+$ and C$^{18}$O) and on 2014 July 17 with 32 antennas" (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: DCO+ J=3–2 (216.1126 GHz)
- Line: C18O J=2–1 (219.5604 GHz)
- Line: H13CO+ J=3–2 (260.2553 GHz)
- External data: IM Lup inclination 49 deg and position angle -35 deg  
  > "We assumed an inclination of 49$^\circ$ and a position angle of -35$^\circ$ for these calculations (cite: Pinte08; Panic09)." (Observational Results) [from (cite: Pinte08; Panic09)]
- External data: Distance to IM Lup 155 pc  
  > "located at a distance of 155 pc (cite: Lombardi08)" (Introduction) [from (cite: Lombardi08)]
- Simulation/model as data: Generic T Tauri disk chemistry model (M*=0.5 Msun, disk mass 1.7e-2 Msun), post-processed with LIME into line cubes  
  > "This model adopts a generic steady, axisymmetric Keplerian disk around a T Tauri star with stellar mass, radius, and effective temperature of $M_{\ast}=0.5$ $M_{\odot}$" (4.1 Model Description)

## Processing

### Calibration

- pipeline or manual: Calibrated by ALMA staff; delivered calibration used unchanged, then self-calibrated per SPW  
  > "The visibility data were calibrated by ALMA staff. The calibration plots were inspected, deemed adequate, and no changes to the delivered calibration were made." (Observations and Data Reduction)
- casa version: CASA 4.2.2  
  > "Each individual SPW was further phase and amplitude self-calibrated in CASA 4.2.2." (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: Delivered calibration used without changes  
  > "no changes to the delivered calibration were made." (Observations and Data Reduction)
- flux calibrator: Titan (absolute amplitude); J1534-3526 gain; J1427-4206 bandpass  
  > "Titan was observed to calibrate the absolute amplitude scale." (Observations and Data Reduction)
- flux scale uncertainty: 10%  
  > "which includes a 10% flux calibration uncertainty" (Observations and Data Reduction)
- self calibration: Phase and amplitude self-calibration on each SPW  
  > "Each individual SPW was further phase and amplitude self-calibrated in CASA 4.2.2." (Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 continuum, 1.0 lines  
  > "the robust parameter was set 0.5 for the continuum and 1.0 for the spectral lines." (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Manual CLEAN mask from bright C18O 2–1, applied to H13CO+ and DCO+  
  > "A CLEAN mask was manually generated based on the bright C$^{18}$O 2–1 line, and then applied to the H$^{13}$CO$^+$ and DCO$^+$ lines." (Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: Subtracted using line-free channels in each SPW  
  > "In each SPW, the continuum was subtracted using line-free channels." (Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.7'' x 0.5''; per-line beams in Table 1  
  > "The CLEANed maps were restored with a synthesized beam with FWHM dimensions of $\sim0.7\ensuremath{''} \times 0.5\ensuremath{''}$." (Observations and Data Reduction)
- final rms: continuum ~0.24 mJy/beam; 4-6 mJy per 0.2 km/s channel  
  > "The 1.4 mm continuum has an RMS noise level of $\sim$0.24 mJy beam$^{-1}$ (dynamic range limited)." (Observations and Data Reduction)

### Inherited from earlier work

- Disk chemistry model from earlier work, updated with deuterium and ortho/para chemistry  
  > "we explored the relevant predictions of the disk chemistry model presented by (cite: Furuya14; Aikawa15), updated with deuterium chemistry" (4.1 Model Description) [from (cite: Furuya14; Aikawa15)]
- Disk physical structure calculation  
  > "The gas temperature, dust temperature and density distributions of the disk are calculated self-consistently, considering various heating and cooling mechanisms (cite: Nomura07)." (4.1 Model Description) [from (cite: Nomura07)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction
- Self-calibration solution intervals and reference SPWs
- CLEAN threshold, cell size, image size
- Which SPW/channels were used for the continuum image
- Integration velocity range and radial bin widths of the profiles
- LIME setup (grid, inclination, beam convolution)
- Model parameters not given (full chemistry network inputs, the small parameter-study grid)

## Analysis recipe

1. **Image continuum and lines**: Fourier inversion and CLEAN of self-calibrated, continuum-subtracted visibilities with Briggs weighting  
  > "The fully calibrated visibilities were Fourier inverted and CLEANed using the Briggs weighting scheme" (Observations and Data Reduction)
   - software: CASA
   - parameter: robust 0.5 continuum, 1.0 lines; 0.2 km/s channels  
  > "the robust parameter was set 0.5 for the continuum and 1.0 for the spectral lines." (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Continuum flux compared with previous SMA measurements  
  > "consistent with previous SMA measurements (cite: Oberg11a)" (Observations and Data Reduction)
2. **Make moment-0 maps and radial profiles**: Sum 0.2 km/s channels above 2 sigma; also unclipped moment-0 maps deprojected and azimuthally averaged  
  > "we also produced moment-0 maps without any clipping, deprojected and azimuthally averaged them into radial brightness profiles" (Observational Results)
   - parameter: inclination 49 deg, PA -35 deg  
  > "We assumed an inclination of 49$^\circ$ and a position angle of -35$^\circ$ for these calculations" (Observational Results)
   - assumption: Inclination and PA from Pinte08, Panic09  
  > "(cite: Pinte08; Panic09)" (Observational Results)
   - fitting: _not stated_
   - validation: Unclipped maps used to mitigate clipping bias  
  > "to mitigate any bias introduced by the applied clipping threshold" (Observational Results)
3. **Model disk chemistry and compare to observed profiles**: Time-dependent gas-grain chemistry (300 kyr) on a generic T Tauri disk, LIME line emission, radial profiles compared qualitatively  
  > "integrating a time-dependent system of gas and grain surface rate equations for 300 kyr, assuming the physical structure is static" (4.1 Model Description)
   - software: LIME
   - parameter: CO binding energy 1150 K (1000 K tested); CO photodesorption yield 7e-3; cosmic ray ionization rate lowered to 1e-20 s-1 test  
  > "The CO photodesorption yield is set to $7\times10^{-3}$ (cite: Fayolle13)." (4.1 Model Description)
   - assumption: CO and HCO+ densities scaled by 500 and 70 for C18O and H13CO+ (ISM 16O/18O, 12C/13C)  
  > "we have scaled the calculated CO and HCO$^+$ densities by factors of 500 and 70, respectively" (4.2 Model Results and Comparison to Observations)
   - fitting: No fitting; qualitative comparison  
  > "The differences in temperature and density structure clearly precludes any quantitative comparison between the model and data." (4.1 Model Description)
   - validation: Small parameter study of binding energy, density/temperature structure, and cosmic ionization rate  
  > "we performed a small parameter study where we varied the CO binding energy, the disk density and temperature structure, and the cosmic ionization rate." (4.1 Model Description)

## Software

- **CASA** 4.2.2: Self-calibration, continuum subtraction, imaging  
  > "Each individual SPW was further phase and amplitude self-calibrated in CASA 4.2.2." (Observations and Data Reduction)
- **LIME** : 3D Monte Carlo radiative transfer to produce model line cubes  
  > "We calculated disk emission spectral data cubes using the 3D Monte Carlo radiative transfer code LIME (cite: Brinch10)" (4.2 Model Results and Comparison to Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.4 mm continuum integrated flux density | 181 | 18 mJy (includes 10% calibration) | mJy | 1 | The integrated flux density is 181$\pm$18 mJy |
| DCO+ 3–2 integrated flux | 450 | 45 | mJy km/s | 2 | $450\pm45$ |
| C18O 2–1 integrated flux | 1460 | 150 | mJy km/s | 2 | $1460\pm150$ |
| H13CO+ 3–2 integrated flux | 484 | 48 | mJy km/s | 2 | $484\pm48$ |
| DCO+ ring radii | ~0.6'' (~90 AU) and 2'' (~300 AU) | not stated | arcsec / AU | 2 | peak at radii of $\sim$0.6$''$ and 2$''$ ($\sim$90 and 300 AU, respectively) |
| H13CO+ peak radius | 0.8'' (~125 AU) | not stated | arcsec | 2 | the H$^{13}$CO$^+$ line peaks at 0.8$''$ ($\sim$125 AU) |
| Peak continuum flux density at 1.4 mm | 66 | 7 | mJy/beam | 1 | 66$\pm$7 mJy beam$^{-1}$ at 1.4 mm |
| Central continuum brightness temperature | ~6 | not stated | K | 1 | corresponding to a brightness temperature of $\sim$6 K |

## Qualitative findings

- All three lines show a central depression, not seen in the continuum  
  > "all three molecular species show a clear central depression" (Observational Results)

## Claim tuples

- H: Does DCO+ emission trace CO ice desorbed non-thermally in the cold outer disk? | E: ALMA imaging of DCO+, C18O, H13CO+ compared with a disk chemistry model plus LIME | R: DCO+ shows two rings at ~90 and ~300 AU; the model reproduces both rings, with the outer ring from non-thermally desorbed CO | F: The outer DCO+ ring traces non-thermal (likely UV photodesorption) CO release in the low-density outer disk | **supported**
- H: Is the inner DCO+ ring tied to the CO snowline? | E: Compare ring radius with the previously inferred midplane temperature profile and the model | R: Inner ring may coincide with onset of CO freeze-out, but multiple formation pathways complicate this | F: Inner ring is associated with the balance of freeze-out and thermal desorption, with caveats | **partially**
- H: What causes the central depression in the line emission? | E: Evaluate four scenarios against the data | R: Gas depletion and cloud absorption disfavoured; chemistry alone insufficient; optical depth requires strong beam dilution | F: Origin unresolved | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: A generic model is used qualitatively because it is not tuned to IM Lup  
  > "qualitative comparisons still provide valuable insight into the origins of the observed molecular emission structure" (4.1 Model Description)
- Alternative: A radial thermal inversion in the outer disk was considered but the non-thermal desorption scenario is favored  
  > "Of the two scenarios we favor the former, since it naturally explains the large DCO$^+$ enhancement and the much smaller H$^{13}$CO$^+$ enhancement at large disk radii." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Model is not tuned to IM Lup, so no quantitative comparison is possible  
  > "The differences in temperature and density structure clearly precludes any quantitative comparison between the model and data." (4.1 Model Description)
- Limitation (authors): Outer-ring intensity is model dependent and may vary from disk to disk  
  > "the expected intensity of the second DCO$^+$ ring *is* model dependent." (Discussion)
- Caveat (inferred, ours): Model is generic with colder, lower-mass disk than IM Lup; conclusions are qualitative only
- Caveat (inferred, ours): UV photodesorption vs cosmic-ray desorption is not discriminated observationally
- Caveat (inferred, ours): No radiative transfer fit or abundance retrieval from data
- Caveat (inferred, ours): Central depression unexplained

## Reproducibility

- Data public (paper): Project code given; data publicly archived is implied by project citation only  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00226.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channel ranges and self-calibration parameters
- Missing: Chemical model code and exact disk model outputs
- Missing: LIME configuration
- Data volume (inferred): ~10-30 GB for two Band 6 executions
- Score (inferred): 3/5, Data are public and imaging steps are simple, but imaging and self-cal details are sparse and the model is not released.
- Rediscovery candidate: no, Main result is morphological (rings) and the model comparison is qualitative and not reproducible from the text.

## Links

- Method: (cite: Furuya14; Aikawa15) (Disk chemistry model used)
- Method: (cite: Brinch10) (LIME radiative transfer)
- Companion: (cite: Favre15) (Alternative DCO+ formation pathways in disk models)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 47,
  "rate": 0.691
 },
 "evidence_ok": true
}
```
