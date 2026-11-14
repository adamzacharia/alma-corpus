# Violent Quenching: Molecular Gas Blown to 1000 km s<SUP>-1</SUP> during a Major Merger

`2018ApJ...864L...1G` | The Astrophysical Journal Letters 2018 | first author: Geach, J. E. | arXiv: 1807.09789 | DOI: 10.3847/2041-8213/aad8b6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: Does the compact post-merger starburst SDSS J1341-0321 host a high-velocity (~1000 km/s) molecular outflow, and what is its mass outflow rate and likely driver?  
  > "In this Letter, we present new, more sensitive, CO J (2 → 1) observations of another galaxy in the sample with the Atacama Large Millimeter/submillimeter Array (ALMA)." (1. INTRODUCTION)
- Target **SDSS J1341−0321**: coordinates 13h41m36.80s, -03d21m25.3s (J2000)  
  > "SDSS J1341−0321 ( z = 0 . 66) at α = 13 h 41 m 36.80 s, δ = −03 ◦ 21 ′ 25.3 ′′ (J2000)" (2. OBSERVATIONS AND DATA REDUCTION); z/distance z = 0.66 (z = 0.6611 from stellar absorption lines)  
  > "SDSS J1341−0321 ( z = 0 . 66) at α = 13 h 41 m 36.80 s, δ = −03 ◦ 21 ′ 25.3 ′′ (J2000)" (2. OBSERVATIONS AND DATA REDUCTION); distance from stellar absorption lines in MagE spectrum  
  > "SDSS J1341−0321 ( z = 0 . 66) at α = 13 h 41 m 36.80 s, δ = −03 ◦ 21 ′ 25.3 ′′ (J2000)" (2. OBSERVATIONS AND DATA REDUCTION)

## Data provenance

- ALMA projects: 2016.1.01072.S, 2017.1.01318.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m antennas (41 in Cycle 4; 43–46 in Cycle 5)  
  > "Number of 12 m antennas 41 43–46" (Table 1)
- configurations: _not stated_
- baselines: Cycle 4: 15–331 m; Cycle 5: 15–2517 m  
  > "Baseline separation 15–331 m 15–2517 m" (Table 1)
- angular resolution: natural beam 0.42″×0.32″; Briggs R=0 0.25″×0.18″  
  > "which has a full width at half maximum of (0 . 42 ′′ × 0 . 32 ′′ ) with position angle of 88 degrees." (2. OBSERVATIONS AND DATA REDUCTION); "With R = 0 we can image the CO J (2 → 1) emission at a resolution of (0 . 25 ′′ × 0 . 18 ′′ )." (3.3. CO J(2→1) emission)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 123 min (Cycle 4); 292 min (Cycle 5)  
  > "Time on source 123 min 292 min" (Table 1)
- observing dates: Mar 8 2017 (Cycle 4); Dec 30 2017, Jan 6, 7 2018 (Cycle 5)  
  > "Dates of observation Mar 8 2017 Dec 30 2017" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **HST WFC3 (UVIS F475W, F814W; IR F160W)**: Optical/near-IR imaging showing compact core and tidal tails; morphology  
  > "The target was observed with the Wide Field Camera 3 (WFC3) Ultraviolet Imaging Spectrograph (UVIS) channel using the F475W and F814W filters" (3.1. Optical and near-infrared imaging)
- Other facility **Magellan/MagE**: Rest-frame UV-optical spectrum (Mg II, Fe II absorption, Hβ, [O II]) for stellar populations and outflow  
  > "obtained with the Magellan Echellette (MagE) spectrograph (Marshall et al. 2008) on the Magellan Clay telescope with a 1 ′′ slit and 2 hours of integration time." (3.2. Optical spectroscopy and stellar population modelling)
- Other facility **Keck/NIRSPEC**: Hα and [N II] for BPT diagram  
  > "We combine the MagE spectrum with Keck/NIRSPEC data" (3.2. Optical spectroscopy and stellar population modelling)
- Other facility **WISE**: W1-W2 colour and 12/22 µm fluxes  
  > "the galaxy’s WISE (Wright et al. 2010) W1 − W2 color is 0.258 ± 0.005" (3.2. Optical spectroscopy and stellar population modelling)
- External data: WISE 12 and 22 µm fluxes used for IR luminosity template fits  
  > "Chary & Elbaz (2001) template fits to the WISE" (4.1. Violent quenching) [from Diamond-Stanic et al. 2012]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1.0  
  > "We concatenate the calibrated Cycle 4 and 5 measurement sets in CASA (version 5.1.0)" (2. OBSERVATIONS AND DATA REDUCTION)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Cycle 4: Ganymede, Titan; Cycle 5: J1337−1257  
  > "Flux calibrators Ganymede J1337−1257" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "image them using the clean command" (2. OBSERVATIONS AND DATA REDUCTION)
- deconvolver: multi-scale with four components: delta function and Gaussians of 1, 2, 5 × natural beam  
  > "We employ multi-scale cleaning with four components corresponding to a delta function and Gaussians with widths of 1, 2 and 5 × the synthesized natural beam" (2. OBSERVATIONS AND DATA REDUCTION)
- weighting robust: natural and Briggs with R = 0  
  > "we image the visibilities using natural and Briggs weighting, with robust parameter R = 0 for the latter." (2. OBSERVATIONS AND DATA REDUCTION)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: circular mask radius 5″ centred on source; clean to 1σ threshold  
  > "We then clean to a stopping threshold of 1 σ, using a circular mask of radius 5 ′′ centered on the source" (2. OBSERVATIONS AND DATA REDUCTION)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 4 and 5 calibrated measurement sets concatenated  
  > "We concatenate the calibrated Cycle 4 and 5 measurement sets in CASA" (2. OBSERVATIONS AND DATA REDUCTION)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- HST image processing and morphological analysis details  
  > "Further details on image processing and morphological analysis can be found in Sell et al. (2014)." (3.1. Optical and near-infrared imaging) [from Sell et al. (2014)]
- Thin-shell time-averaged outflow rate formalism  
  > "assuming a time-averaged thin shell approximation (Rupke et al. 2005)" (4.1. Violent quenching) [from Rupke et al. 2005]

### Not stated but needed to reproduce (our reading)

- Whether the ALMA data were reduced with the pipeline or manually, and pipeline version
- Spectral setup, frequencies and channel widths
- Continuum subtraction method and line-free channels
- Image size and cell size
- Final rms noise values per channel
- Primary beam correction details
- Exact aperture/spectral extraction for the CO spectrum and wing masses
- Value of alpha_CO used (0.34 L'CO form given; uncertainty not specified)
- Details of the SSP fit (masking, regularization)

## Analysis recipe

1. **Image CO(2-1) cube**: Concatenate Cycle 4+5 data, clean with natural and Briggs R=0 weighting, multiscale  
  > "We concatenate the calibrated Cycle 4 and 5 measurement sets in CASA (version 5.1.0) and image them using the clean command." (2. OBSERVATIONS AND DATA REDUCTION)
   - software: CASA
   - parameter: stopping threshold 1σ; mask radius 5″  
  > "We then clean to a stopping threshold of 1 σ, using a circular mask of radius 5 ′′ centered on the source" (2. OBSERVATIONS AND DATA REDUCTION)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit stellar populations to MagE spectrum**: SSP models (FSPS, Padova 2008, Salpeter, C3K) with Calzetti reddening, fit with pPXF  
  > "We perform the fit with the Penalized Pixel-Fitting (pPXF) software (Cappellari & Emsellem 2004; Cappellari 2017)." (3.2. Optical spectroscopy and stellar population modelling)
   - software: FSPS, pPXF
   - parameter: solar metallicity, 43 ages 1 Myr–8.9 Gyr  
  > "We utilize solar metallicity SSP templates with 43 ages spanning 1 Myr–8.9 Gyr." (3.2. Optical spectroscopy and stellar population modelling)
   - assumption: Salpeter IMF, converted to Chabrier for SFR  
  > "after converting to a Chabrier IMF (Chabrier et al. 2003)" (3.2. Optical spectroscopy and stellar population modelling)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive molecular outflow rate**: Thin-shell time-averaged approximation; mass from optically thin CO, Mdot integrated over -500 to -1500 km/s; R_out from offset of -1000 km/s peak  
  > "To estimate M H 2 , out we only consider emission between −500 km s −1 and −1500 km s −1 and assume the optically thin case appropriate for a turbulent outflow" (4.1. Violent quenching)
   - parameter: R_out = 2.0±0.1 kpc (offset 0.28±0.02″)  
  > "corresponding to a projected distance of (2 . 0 ± 0 . 1) kpc" (4.1. Violent quenching)
   - assumption: M_H2 = 0.34 L'CO (optically thin); thermalized CO; velocities not deprojected  
  > "We take a conservative approach and do not deproject the velocities" (4.1. Violent quenching)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.0: Concatenation and imaging with clean  
  > "We concatenate the calibrated Cycle 4 and 5 measurement sets in CASA (version 5.1.0)" (2. OBSERVATIONS AND DATA REDUCTION)
- **GALFIT** 3: Sérsic fits for HST compactness  
  > "When quantifying the compactness with GALFIT (version 3; Peng et al. 2010)" (3.1. Optical and near-infrared imaging)
- **tweakreg** : HST image registration  
  > "All images were registered to one another with tweakreg" (3.1. Optical and near-infrared imaging)
- **MASE** : MagE data reduction  
  > "The data were reduced and calibrated using the MASE pipeline (Bochanski et al. 2009)." (3.2. Optical spectroscopy and stellar population modelling)
- **pPXF** : Stellar population fitting  
  > "We perform the fit with the Penalized Pixel-Fitting (pPXF) software" (3.2. Optical spectroscopy and stellar population modelling)
- **FSPS** : Generate SSP templates  
  > "We employed the Flexible Stellar Population Synthesis code (Conroy, Gunn & White 2009; Conroy & Gunn 2010)" (3.2. Optical spectroscopy and stellar population modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated CO(2-1) line flux | 3.4 | 0.1 | Jy km/s | 1 | The integrated line flux is S CO ∆ V = 3 . 4 ± 0 . 1 Jy km s −1 |
| CO luminosity L'CO | 2.0e10 | 0.1e10 | K km/s pc^2 | 1 | corresponding to a luminosity of L CO ′ = (2 . 0 ± 0 . 1) × 10 10 K km s −1 pc 2 |
| Molecular mass outflow rate | 310 | 70 | Msun/yr | 3 | This gives M ˙ H 2 , out = 310 ± 70 M ⊙ yr −1 |
| Outflow kinetic power | 0.8e44 | 0.3e44 | erg/s | 3 | yielding P k = ( 0 . 8 ± 0 . 3) × 10 44 erg s −1 |
| Outflow momentum rate | 1.8e36 | 0.5e36 | dyne | 3 | (1 . 8 ± 0 . 5) × 10 36 dyne |
| 10 Myr-averaged SFR | 900 | not stated | Msun/yr | 2 | The 10 Myr-averaged SFR inferred from the SSP modelling is M ⋆ ≈ 900 M ⊙ yr −1 |
| WISE W1-W2 | 0.258 | 0.005 | mag | 0 | W1 − W2 color is 0.258 ± 0.005 |

## Qualitative findings

- CO(2-1) wing out to -1000 km/s, similar to Mg II/Fe II absorption and nebular emission velocities  
  > "The nebular and absorption lines extend to similar blueshifted velocities as seen in CO J (2 → 1) emission" (3.3. CO J(2→1) emission)

## Claim tuples

- H: The compact merger remnant hosts a molecular outflow reaching ~1000 km/s | E: ALMA CO(2-1) mapping and spectrum compared with MagE lines | R: Significant wing to ΔV≈-1000 km/s | F: Molecular component of a multiphase outflow | **supported**
- H: An AGN is not currently present | E: BPT, WISE colours, Hβ width | R: Composite BPT, W1-W2=0.258, narrow Hβ | F: Unlikely currently to host an AGN | **supported**
- H: Starburst momentum can drive the outflow | E: Compared outflow momentum rate with L/c | R: 1.8e36 vs 8e35 dyne | F: Insufficient unless extras; relic AGN not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Tidal debris explanation for -1000 km/s gas rejected  
  > "cannot plausibly be associated with purely tidal debris resulting from the merger" (4. INTERPRETATION)
- How they decided it was enough: _not stated_
- Limitation (authors): Wind geometry poorly constrained; alpha_CO and projection uncertain  
  > "poor constraints on the wind geometry are a major systematic uncertainty in the calculation." (4.1. Violent quenching)
- Caveat (inferred, ours): Single object; outflow radius from a single centroid offset
- Caveat (inferred, ours): Outflow rate depends strongly on alpha_CO and geometry
- Caveat (inferred, ours): Wing significance not quantified in text
- Caveat (inferred, ours): Mass outflow rate uncertainty likely understates systematics

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Spectral setup and channelization
- Missing: Continuum subtraction details
- Missing: Pipeline calibration specifics
- Missing: Spectrum extraction details for wing
- Data volume (inferred): ~50-100 GB raw for two ALMA Band 3 execution sets
- Score (inferred): 3/5, Project codes and imaging basics stated, but spectral setup, extraction and mass calculation details are sparse.
- Rediscovery candidate: no, Key recipe details (spectral extraction, wing integration limits, alpha_CO) are incomplete.

## Links

- Method: Sell et al. (2014) (HST image processing and morphology)
- Method: Rupke et al. (2005) (Thin-shell outflow rate)
- Companion: Geach et al. (2013 & 2014) (Earlier CO(2-1) detections of sample galaxies)
- Companion: Diamond-Stanic et al. 2012 (Discovery of compact starburst outflows)
- Related: SDSS compact massive galaxy sample

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2017.1.0318.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 40,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
