# ALMA detection of the rotating molecular disk wind from the young star HD 163296

`2013A&A...555A..73K` | Astronomy and Astrophysics 2013 | first author: Klaassen, P. D. | arXiv: 1304.5436 | DOI: 10.1051/0004-6361/201321129

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Is there a molecular disk wind or outflow from the Herbig Ae star HD 163296 associated with the HH 409 jet, and what are its morphology, kinematics and energetics?  
  > "In Section [3](#sec:results) we describe the morphology and energetics of the observed disk wind." (Introduction)
- Target **HD 163296**: coordinates pointing center 17:56:21.28, -21:57:22.36  
  > "It is at a distance of 122 pc, and has an age of 4 Myr (cite: vandenancker98)." (Introduction); "The pointing center is $\alpha$=17:56:21.28, $\delta$=-21:57:22.36" (3 Results); z/distance 122 pc  
  > "It is at a distance of 122 pc, and has an age of 4 Myr (cite: vandenancker98)." (Introduction); "The pointing center is $\alpha$=17:56:21.28, $\delta$=-21:57:22.36" (3 Results); distance from van den Ancker et al. 1998  
  > "It is at a distance of 122 pc, and has an age of 4 Myr (cite: vandenancker98)." (Introduction); "The pointing center is $\alpha$=17:56:21.28, $\delta$=-21:57:22.36" (3 Results)

## Data provenance

- ALMA projects: 2011.0.00010.SV
- bands: Band 6 (CO 2-1) and Band 7 (CO 3-2)  
  > "$J$=2-1 (Band 6, 230.538 GHz) and $J$=3-2 (Band 7, 345.796 GHz)" (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 18-20 antennas, extended configuration, ~20-400 m baselines  
  > "with 18 - 20 antennas in an extended configuration ($\sim$20-400 m baselines)" (2 Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: 0.80x0.68'' (CO 2-1), 0.68x0.44'' (CO 3-2)  
  > "| $J$=3-2 | 4.2 | 0.68$''\times$0.44$''$, 91$^\circ$ | 17$''$  | 8$''$            |" (Table 1)
- max recoverable scale: 11'' (Band 6), 8'' (Band 7)  
  > "| $J$=2-1 | 6.9 | 0.80$''\times$0.68$''$, 75$^\circ$ | 26$''$  | 11$''$           |" (Table 1)
- sensitivity: per-channel rms 6.9 (Band 6) and 4.2 (Band 7) mJy/beam after self-calibration  
  > "The per-channel rms noises in these two datasets are 6.9 and 4.2 mJy beam$^{-1}$ after self-calibration." (2 Observations and Data Reduction)
- time on source: 46 min (Band 6), 59 min (Band 7)  
  > "The total time on source in each band was 46 and 59 minutes, respectively." (2 Observations and Data Reduction)
- observing dates: June and July 2012  
  > "Both datasets were observed in June and July 2012" (2 Observations and Data Reduction)
- pi or archival as stated: ALMA Science Verification data  
  > "These $^{12}$CO $J$=2-1 and $J$=3-2 observations were taken with ALMA as part of the Science Verification program" (2 Observations and Data Reduction)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 12CO J=3-2 (345.796 GHz)
- External data: HH knot A proper motion 0.49'' /yr and PA 42 deg  
  > "For knot A they suggest a proper motion of $0.\!''49$ yr$^{-1}$." (Discussion) [from Wassell06]
- External data: Ambient density 1.9e3 cm^-3  
  > "Using an ambient density of 1.9$\times10^{3}$ cm$^{-3}$ (cite: Wassell06)" (Discussion) [from Wassell06]
- External data: Mass accretion rate ~1e-7 Msun/yr  
  > "A mass accretion rate of $\sim10^{-7}$ M$_\odot$ yr$^{-1}$ was previously determined for this source" (Discussion) [from Garcia06; Hubrig09]
- External data: Disk mass of order 1e-2 Msun  
  > "The disk itself has a mass of order 10$^{-2}$ M$_\odot$ (cite: Tilling12)" (Discussion) [from Tilling12]

## Processing

### Calibration

- pipeline or manual: Data reduction in CASA; antennas PM01 and DV03 removed for July Band 6  
  > "Data from two antennas (PM01 and DV03) were removed for the July observations in Band 6 because of anomalously high amplitudes." (2 Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 6: Juno, Neptune, Mars; Band 7: Neptune (Juno bootstrapped for one execution)  
  > "For the Band 6 data, Juno, Neptune and Mars were used for amplitude calibration." (2 Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-cal using line-free continuum channels in all four spectral windows  
  > "Both datasets were self-calibrated in both phase and amplitude using line-free continuum channels in all four spectral windows." (2 Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Both data sets were cleaned using natural weighting" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Not applied to main figures; applied to Band 7 map in Fig. 4, to 20% attenuation level  
  > "Neither of the datasets shown in Figures [2](#fig:CO_21_mom0) and [3](#fig:CO_21_mom1) are primary beam corrected." (3 Results)
- array combination: _not stated_
- smoothing: Band 6 shortest baselines masked to match Band 7 LAS (16.6 klambda)  
  > "We masked the shortest baselines in the Band 6 data to match the largest angular scales recoverable in the Band 7 data" (3 Results)
- final beam: 0.80x0.68'' PA 75 (Band 6); 0.68x0.44'' PA 91 (Band 7)  
  > "| $J$=2-1 | 6.9 | 0.80$''\times$0.68$''$, 75$^\circ$ | 26$''$  | 11$''$           |" (Table 1)
- final rms: 6.9 and 4.2 mJy/beam per channel  
  > "The rms noise values listed below have units of mJy beam$^{-1}$ per channel." (Table 1)

### Inherited from earlier work

- Largest angular scale formula from the ALMA Cycle 1 Technical Handbook Sec 6.2  
  > "the formula for determining the approximate largest angular scales (LAS) is given in Section 6.2 of the ALMA Cycle 1 Technical Handbook" (2 Observations and Data Reduction) [from ALMA Cycle 1 Technical Handbook]
- HCO+ J=4-3 and disk gas results presented elsewhere  
  > "These data are presented in Mathews et al. (Submitted)." (2 Observations and Data Reduction) [from Mathews et al. (Submitted) (cite: HDDCOp)]
- CO abundance 1e-4 and mean molecular mass 2.8  
  > "using a CO abundance of 10$^{-4}$ with respect to molecular hydrogen, and a mean molecular mass of 2.8 (cite: Kauffmann08)" (Discussion) [from Kauffmann08]

### Not stated but needed to reproduce (our reading)

- Spectral window setup and line-free channels used for self-calibration
- Self-calibration solution intervals
- CASA version
- Cell size, image size, clean threshold and masks
- Velocity integration limits for moment maps
- Flux scale uncertainty
- Details of the uv mask for filtering and the exact RADEX inputs (linewidth, background)
- Aperture regions used for fluxes

## Analysis recipe

1. **Calibrate and image CO data**: Calibration, self-calibration and natural-weighted cleaning in CASA; spectral resampling to 0.32 and 0.25 km/s  
  > "Data reduction and imaging were all performed using the Common Astronomy Software Applications (cite: CASA)." (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Inspect visibility spectra and make moment maps**: Averaged visibility spectra of two shortest baselines to select velocity ranges; moment 0/1 maps clipped at 3.5 and 4 sigma per channel  
  > "the data were clipped at 3.5 and 4 $\sigma$ in each channel when creating the zeroth and first moment maps (respectively)" (Discussion)
   - software: CASA
   - fitting: _not stated_
   - validation: Phase coherence offset from zero in visibilities indicates emission offset from phase center  
  > "there is phase coherence, and it is offset from zero." (3 Results)
3. **Test spatial filtering**: Mask shortest Band 6 baselines to match Band 7 LAS and compare morphology  
  > "8$''$ at 230.5 GHz corresponds to 16.6 k$\lambda$" (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive excitation temperature and column density**: RADEX non-LTE modelling of the CO 2-1/3-2 peak-intensity ratio near knot A3 using filtered Band 6 data  
  > "Using RADEX, a non-LTE 1D radiative transfer calculator (cite: vandertak07), we determined the excitation temperature and column density" (Discussion)
   - software: RADEX
   - parameter: ambient density 1.9e3 cm^-3; N=1e15 cm^-2; T>900 K; adopted 960 K  
  > "We therefore use an excitation temperature of 960 for further calculations." (Discussion)
   - assumption: Spherical symmetry; emitting size = N/n  
  > "Dividing this derived column density by the assumed volume density recovers our observed emitting region when we make the assumption of spherical symmetry." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute wind mass, momentum, energy and rates**: LTE CO column from integrated intensity at 960 K, CO/H2 = 1e-4, mu=2.8; momentum = m*v; E=0.5mv^2; rates divided by 400 yr age  
  > "assuming local thermodynamical equilibrium, a temperature of 960 K" (Discussion)
   - assumption: Wind age 400 yr from mean velocity -18.6 km/s and extent ~13''  
  > "We assume a wind age of 400 yr based on the average velocity in the wind (-18.6 km s$^{-1}$)" (Discussion)
   - fitting: _not stated_
   - validation: Using RADEX column density the mass drops by almost an order of magnitude  
  > "Using the column density derived from the RADEX calculation, the outflow mass drops by almost an order of magnitude." (Discussion)

## Software

- **CASA** : Data reduction and imaging  
  > "Data reduction and imaging were all performed using the Common Astronomy Software Applications (cite: CASA)." (2 Observations and Data Reduction)
- **RADEX** : Non-LTE excitation analysis  
  > "Using RADEX, a non-LTE 1D radiative transfer calculator (cite: vandertak07)" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO 2-1 integrated flux | 2.58 | not stated | Jy km/s | 2 | The integrated and peak intensities of the CO $J$=2-1 emission are 2.58 Jy km s$^{-1}$ |
| Excitation temperature adopted | 960 | not stated | K | 4 | We therefore use an excitation temperature of 960 for further calculations. |
| CO column density | 1e15 | not stated | cm^-2 | 4 | requires a column density of 1$\times10^{15}$ cm$^{-2}$ |
| Wind mass (CO 2-1 integrated) | 73.1e-6 | 0.8e-6 | Msun | 5 | / M (10$^{-6}$ M$_\odot$)                                / 5.7           / 0.06          / 73.1          / 0.8           / 24.6          / 0.3           / |
| Mass loss rate (CO 2-1 integrated) | 18.3e-8 | 2e-8 | Msun/yr | 5 | / 1.4           / 0.2           / 18.3          / 2             / 6.2           / 0.7           / |
| Wind energy (CO 2-1 integrated) | 25.1e40 | 1.0e40 | erg | 5 | / E (10$^{40}$ erg)                                      / 1.98          / 0.04          / 25.1          / 1.0           / 8.7           / 0.5           / |
| Wind mean velocity | -18.6 | not stated | km/s | 2 | offset from the disk by -18.6 km s$^{-1}$ |
| Disk dispersal timescale | 1e5 | not stated | yr | 5 | suggests a disk dispersal timescale of 10$^5$ yr |

## Qualitative findings

- Blue-shifted CO emission with double corkscrew morphology, extending over 10'' and coincident with HH 409 knots  
  > "The emission has a double corkscrew morphology and extends more than 10$''$ from the disk" (abstract)
- Red-shifted wind not imaged, likely filtered out by the interferometer  
  > "It is likely that the redshifted wind is filtered out by the interferometer." (3 Results)

## Claim tuples

- H: CO emission near HH 409 traces a molecular disk wind rather than jet-entrained outflow | E: CO 2-1 and 3-2 imaging and moment maps compared with HH knot positions | R: Double-armed velocity structure, with blue gas ahead of any HH knot | F: Emission is a rotating disk wind heated by the jet | **supported**
- H: The wind mass loss exceeds the stellar accretion rate | E: Energetics from CO column and assumed 400 yr age | R: Mass loss rate 2e-7 Msun/yr vs accretion ~1e-7 | F: The star disperses the disk faster than it accretes | **partially**
- H: The compact CO 3-2 knots are hot jet-heated gas | E: RADEX line ratio analysis | R: T>900 K needed | F: Gas in knots is heated by the jet | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photoevaporative wind rejected: 18.6 km/s sound speed implies 1e5 K, too hot for molecular gas  
  > "Thus, we are not seeing a photo evaporative wind." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 7 data heavily spatially filtered, redshifted wind not detected, wind age may be underestimated  
  > "Followup observations covering a wider areas, and recovering larger scale structures are required to confirm this hypothesis." (3 Results)
- Caveat (inferred, ours): Temperature of 960 K and density assumed from literature drive the masses; very uncertain
- Caveat (inferred, ours): Wind age of 400 yr is crude
- Caveat (inferred, ours): Single-pointing observations with emission beyond the primary beam
- Caveat (inferred, ours): Uncertainties include only flux errors
- Caveat (inferred, ours): Mass from LTE differs from RADEX by an order of magnitude

## Reproducibility

- Data public (paper): ALMA Science Verification data (public)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00010.SV." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and script
- Missing: Imaging parameters and masks
- Missing: Velocity ranges and flux extraction regions
- Missing: RADEX inputs
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public SV data and simple recipe, but many imaging and analysis parameters are missing.
- Rediscovery candidate: no, Data are public but the recipe lacks key parameters and results depend on assumptions.

## Links

- Method: van der Tak et al. 2007 (cite: vandertak07) (RADEX)
- Companion: Mathews et al. (Submitted) (HCO+ and disk data)
- Companion: de Gregorio-Monsalvo et al. 2013 (Disk CO gas)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.000010.SV"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 44,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
