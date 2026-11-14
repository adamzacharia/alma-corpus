# ALMA CN Zeeman Observations of AS 209: Limits on Magnetic Field Strength and Magnetically Driven Accretion Rate

`2021ApJ...908..141H` | The Astrophysical Journal 2021 | first author: Harrison, Rachel E. | arXiv: 2101.01846 | DOI: 10.3847/1538-4357/abd94e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Can CN 2-1 Zeeman splitting observations of AS 209 constrain the line-of-sight magnetic field strength (toroidal and vertical) and the magnetically driven accretion rate?  
  > "observations of circular polarization in molecular lines produced by Zeeman splitting offer a direct measure of the line-of-sight magnetic field strength in disks." (abstract)
- Target **AS 209**: coordinates _not stated_; z/distance 126 pc  
  > "AS 209 is a protoplanetary disk located in the Ophiuchus star forming region at a distance of 126 pc from the Sun (cite: 2016A&A...595A...2G)." (Introduction); "The protostar has a mass of 1.25 $M_\odot$ (cite: 2018ApJ...868..113T)" (Introduction); distance from Gaia Collaboration 2016 (cite: 2016A&A...595A...2G)  
  > "AS 209 is a protoplanetary disk located in the Ophiuchus star forming region at a distance of 126 pc from the Sun (cite: 2016A&A...595A...2G)." (Introduction); "The protostar has a mass of 1.25 $M_\odot$ (cite: 2018ApJ...868..113T)" (Introduction)

## Data provenance

- ALMA projects: 2018.1.01030.S
- bands: _not stated_
- frequencies and spectral setup: Two line windows centered 226.64013 and 226.88081 GHz, 122.070 kHz channels, 117.1875 MHz bandwidth each  
  > "The spectral line windows are centered on 226.64013 GHz and 226.88081 GHz." (Observations); "two spectral line windows with a channel width of 122.070 kHz and a total bandwidth of 117.1875 MHz each" (Observations)
- continuum bandwidth: Two continuum windows, 937.5 MHz each, 976.562 kHz channels  
  > "two continuum windows with a channel width of 976.562 kHz and a total bandwidth of 937.5000 MHz each" (Observations)
- arrays: ALMA, configuration C43-1  
  > "while the array was in configuration C43-1." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.40" x 1.27"  
  > "The images have a beam size of 1.40$\ensuremath{''}$ $\times$ 1.27$\ensuremath{''}$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: Cube rms ~0.88-0.96 mJy/beam per 0.25 km/s channel (I,Q,U,V)  
  > "$\sigma_{(I, Q, U, V)}$ = (0.91, 0.95, 0.96, 0.95) mJy beam$^{-1}$ per 0.25 km/s channel in the spectral window containing lines 1-4" (Observations)
- time on source: 2.7 h on AS 209 (6.1 h total)  
  > "The total observing time was 6.1 hours, of which 2.7 hours were spent on AS 209." (Observations)
- observing dates: 6-7 March 2019, four execution blocks  
  > "The observations were taken in four execution blocs between 6 March and 7 March 2019" (Observations)
- pi or archival as stated: PI data (PI: Rachel Harrison)  
  > "ALMA project 2018.1.01030.S (PI: Rachel Harrison)" (Observations)
- Line: CN N=2-1 hyperfine line 1 (J,F 3/2,3/2 -> 1/2,3/2) (226.63217 GHz)
- Line: CN N=2-1 hyperfine lines 2-9 (226.65956-226.89213 GHz)
- External data: Zeeman splitting factors Z for the nine CN hyperfine lines (Shinnaga and Yamamoto)  
  > "We quote Shinnaga and Yamamoto’s Zeeman factor values to the second decimal place" (Observations) [from Shinnaga and Yamamoto; agree with (cite: 2019A&A...624L...7V)]
- External data: Disk inclination 35.3 deg, ring and gap locations  
  > "The disk’s inclination angle ($i$) of 35.3$^\circ$ (cite: 2018A&A...610A..24F)" (Introduction) [from (cite: 2018A&A...610A..24F)]
- External data: Stellar mass 1.25 Msun  
  > "The protostar has a mass of 1.25 $M_\odot$ (cite: 2018ApJ...868..113T)" (Introduction) [from (cite: 2018ApJ...868..113T)]
- External data: Previous CN integrated intensity 3.32 +/- 0.14 Jy km/s (SMA)  
  > "consistent with the value of 3.32 $\pm$ 0.14 Jy km/s from (cite: 2011ApJ...734...98O)" (Results) [from (cite: 2011ApJ...734...98O)]

## Processing

### Calibration

- pipeline or manual: initial calibration performed by NAASC data analysts; method not detailed  
  > "We would like the North American ALMA Science Center data analysts for performing the initial data calibration and imaging." (Acknowledgements)
- casa version: CASA 5.4.0  
  > "All data reduction was performed using the Common Astronomy Software Applications (CASA) version 5.4.0." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ±10% amplitude calibration  
  > "We estimate that the uncertainty on the amplitude calibration is $\pm$10%" (Observations)
- self calibration: One round phase-only self-cal on continuum I, solint = scan length  
  > "We performed one round of phase-only self calibration on the continuum $I$ data, with the solution interval set to the scan length." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The data were cleaned using Briggs weighting with a robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted from line windows before cubes  
  > "Before making the line image cubes, we subtracted the continuum emission from the spectral line windows." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.40" x 1.27"  
  > "The images have a beam size of 1.40$\ensuremath{''}$ $\times$ 1.27$\ensuremath{''}$." (Observations)
- final rms: Continuum I 0.33 mJy/beam after self-cal (0.60 before)  
  > "The continuum I rms value was 0.60 mJy beam$^{-1}$ before self calibration and 0.33 mJy beam$^{-1}$ after self calibration." (Observations)

### Inherited from earlier work

- Zeeman fitting technique solving for instrumental terms C1, C2  
  > "we use the technique developed by (cite: 1996ApJ...456..217C)." (Line circular polarization) [from (cite: 1996ApJ...456..217C)]
- Polarized intensity debiasing estimator  
  > "an estimator used by e.g. (cite: 1974ApJ...194..249W) and (cite: 2016MNRAS.461..698V):" (Observations) [from (cite: 1974ApJ...194..249W); (cite: 2016MNRAS.461..698V)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum subtraction
- Image size, cell size, masks, clean threshold
- Details of initial calibration/pipeline version and flux calibrator
- Disk position angle and centre used in gofish Kepler correction
- Regions/radii used for averaging and for rms estimation
- Details of the mass accretion rate derivation and disk model (discussion text is truncated)
- Line weights w_I and w_Z definitions for stacking

## Analysis recipe

1. **Image Stokes I,Q,U,V cubes and continuum**: Briggs-weighted cleaning with robust 0.5; continuum subtraction; 0.25 km/s channels; phase-only self-cal on continuum I  
  > "The data were cleaned using Briggs weighting with a robust parameter of 0.5 to create image cubes and continuum images for all four Stokes parameters." (Observations)
   - software: CASA
   - parameter: robust = 0.5; 0.25 km/s channels  
  > "The image cubes were created with a spectral resolution of 0.25 km/s." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Correct for Keplerian rotation**: Shift velocities in Stokes I and V cubes by expected Keplerian velocity per pixel to common centroid  
  > "we used the package `gofish` (cite: 2019JOSS....4.1632T) to shift the velocities in the Stokes $I$ and Stokes $V$ cubes by the amounts appropriate to correct for Keplerian motion." (Line circular polarization)
   - software: gofish
   - assumption: Inclination, position angle, distance, stellar mass fixed (i=35.3 deg, 126 pc, 1.25 Msun)  
  > "Based on the disk’s inclination angle, position angle, distance, and stellar mass, `gofish` calculates the expected Keplerian velocity for each pixel in the image cube." (Line circular polarization)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Stokes V profiles for B_LOS (red and blue sides)**: Fit V_j = C1 I_j + C2 dI_j/dnu + 0.5 B Z_j dI_j/dnu to unblended line portions of the Kepler-corrected red and blue side spectra  
  > "This technique fits the observed Stokes $V$ profile of each hyperfine component to the expression" (Line circular polarization)
   - software: gofish
   - parameter: Only low-frequency part of line 5 and high-frequency part of line 7 used because of blending  
  > "We therefore used only the lower-frequency portion of the Kepler-corrected line 5 data and the higher-frequency portion of the Kepler-corrected line 7 data" (Line circular polarization)
   - assumption: Fit uncertainties taken as 1 sigma; 3 sigma used for upper limits  
  > "we have calculated 3-$\sigma$ upper limits on the net toroidal and vertical magnetic field strengths." (Discussion)
   - fitting: Least-squares-type fit; per-channel rms from region outside disk as uncertainties  
  > "we calculated the per-channel rms in a region outside the disk from spectral line cubes whose velocities had been Kepler-corrected in `gofish`." (Line circular polarization)
   - validation: Cross-check with stacking of red and mirrored blue unblended lines (no detection)  
  > "stacking the lines in this way did not lead to a detection of circularly polarized emission." (Line circular polarization)

## Software

- **CASA** 5.4.0: data reduction, imaging, self-calibration  
  > "All data reduction was performed using the Common Astronomy Software Applications (CASA) version 5.4.0." (Observations)
- **gofish** : Keplerian velocity shifting and spectra extraction  
  > "we used the package `gofish` (cite: 2019JOSS....4.1632T) to shift the velocities" (Line circular polarization)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum Stokes I total flux | 215.0 | 1.8 | mJy | 1 | the disk has a peak flux of 127.4 mJy/beam and a total intensity of 215.0 $\pm$ 1.8 mJy. |
| Integrated CN intensity lines 5-7 | 3.874 | 0.015 | Jy km/s | 1 | is 3.874 $\pm$ 0.015 Jy km/s |
| B_LOS limit, redshifted side | 5.0 | not stated | mG | 3 | the limit on the net line-of-sight magnetic field strength is 5.0 mG on the redshifted side of the disk and 4.2 mG on the blueshifted side |
| B_LOS limit, blueshifted side | 4.2 | not stated | mG | 3 | the limit on the net line-of-sight magnetic field strength is 5.0 mG on the redshifted side of the disk and 4.2 mG on the blueshifted side |

## Qualitative findings

- Continuum linear polarization pattern at 1.3 mm matches scattering predictions, similar to 870 um observations  
  > "This pattern closely matches the polarization from scattering in a disk with a similar inclination to AS 209’s predicted by the model in (cite: 2016MNRAS.456.2794Y)." (Continuum linear polarization)

## Claim tuples

- H: Zeeman splitting of CN 2-1 reveals a magnetic field in the AS 209 disk | E: Fit Stokes V of nine hyperfine lines, with Kepler correction, on red and blue sides | R: No Zeeman detection; limits 5.0 mG (red) and 4.2 mG (blue) | F: Only upper limits on net B_LOS can be set | **supported**
- H: Continuum polarization traces magnetic alignment vs scattering | E: Mapped 1.3 mm linear polarization | R: Pattern parallel to minor axis inside, azimuthal outside | F: Consistent with self-scattering | **supported**

## Reasoning

- Why this data: AS 209 chosen for inclination, bright CN line, high accretion rate  
  > "This source was selected as a target source based on its inclination angle, the presence of a bright CN line" (Introduction)
- Why this method: _not stated_
- Alternative: Stacking method rejected for final limits because it does not account for instrumental circular polarization  
  > "Because this method does not account for circular polarization from instrumental effects, we report the results of using the first fitting technique" (Line circular polarization)
- How they decided it was enough: _not stated_
- Limitation (authors): Stacking destroys signal from a vertical field; lines 5-7 remain blended  
  > "this method of stacking would destroy any Stokes $V$ signal from a vertical magnetic field" (Line circular polarization)
- Caveat (inferred, ours): Upper limits taken as 3 sigma of fit uncertainty; vertical field limits and accretion rate derivation not visible in provided text
- Caveat (inferred, ours): Self-cal and Keplerian shifting details limit reproducibility

## Reproducibility

- Data public (paper): Data from ALMA project 2018.1.01030.S; public status not stated  
  > "This paper makes use of the following ALMA data: ALMA #2018.1.01030.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (mask, size, cell)
- Missing: gofish parameters (PA, regions)
- Missing: Accretion-rate derivation details
- Data volume (inferred): ~50-100 GB raw for 4 EBs with polarization; moderate
- Score (inferred): 3/5, Single dataset and recipe partly given, but several key parameters and the discussion/accretion derivation are missing.
- Rediscovery candidate: no, Key analysis settings and accretion-rate derivation are missing; results are only upper limits.

## Links

- Method: (cite: 1996ApJ...456..217C) (Zeeman fitting technique removing instrumental terms)
- Method: (cite: 2019JOSS....4.1632T) (gofish package)
- Companion: (cite: 2019A&A...624L...7V) (Previous ALMA CN Zeeman attempt)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
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
  "facts": 67,
  "stated": 41,
  "rate": 0.612
 },
 "evidence_ok": true
}
```
