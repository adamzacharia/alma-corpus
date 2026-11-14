# ALMA Measurements of the HNC and HC<SUB>3</SUB>N Distributions in Titan's Atmosphere

`2014ApJ...795L..30C` | The Astrophysical Journal Letters 2014 | first author: Cordiner, M. A. | arXiv: 1408.6461 | DOI: 10.1088/2041-8205/795/2/L30

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What are the spatial distributions and vertical abundance profiles of HNC and HC3N in Titan's atmosphere as seen by ALMA?  
  > "Molecular emission maps and disk-averaged vertical mixing profiles are derived." (Introduction)
- Target **Titan**: coordinates not stated (ephemeris tracking)  
  > "This resolution element corresponds to $4240\times2440$ km at Titan’s geocentric distance of 10.84 AU at the time of observation, compared to Titan’s mean radius of 2,576 km." (Observations); z/distance 10.84 AU geocentric distance  
  > "This resolution element corresponds to $4240\times2440$ km at Titan’s geocentric distance of 10.84 AU at the time of observation, compared to Titan’s mean radius of 2,576 km." (Observations); distance from not stated (JPL Horizons used for radial velocity)  
  > "This resolution element corresponds to $4240\times2440$ km at Titan’s geocentric distance of 10.84 AU at the time of observation, compared to Titan’s mean radius of 2,576 km." (Observations)

## Data provenance

- ALMA projects: 2012.A.00033.S
- bands: Band 7, dual-sideband  
  > "a single 158 second integration of Titan was obtained using the dual-sideband Band 7 receiver." (Observations)
- frequencies and spectral setup: 350.34-351.28, 351.32-352.26 GHz (LSB); 362.18-363.12, 363.14-364.07 GHz (USB); 3840 channels per spw; 244 kHz spacing, 488 kHz resolution (0.40 km/s)  
  > "The channel spacing was 244 kHz which (after Hanning smoothing by the correlator) produced a spectral resolution of 488 kHz (or $0.40$ km $\rm{s}^{-1}$ at 363 GHz)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.54''x0.31''  
  > "The resulting spatial resolution (FWHM of the Gaussian restoring beam) was $0.54''\times0.31''$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS per channel 31 mJy (HNC), 38 mJy (HC3N)  
  > "The average RMS noise per channel was 31 mJy for HNC and 38 mJy for HC$_3$N." (Results and spectral line modeling)
- time on source: 158 s  
  > "a single 158 second integration of Titan was obtained" (Observations)
- observing dates: 2013 November 17  
  > "Observations of Titan were made on 2013 November 17 in Cycle 1 Early Science mode" (Observations)
- pi or archival as stated: Director's Discretionary Time project for comet ISON; Titan observed as flux calibrator  
  > "as part of an ALMA Director’s Discretionary Time project to observe comet C/2012 S1 (ISON)" (Observations)
- Line: HNC J=4-3 (362.630 GHz)
- Line: HC3N J=40-39 (363.785 GHz)
- External data: Titan temperature profile from Cassini CIRS and HASI  
  > "The atmospheric temperature profile was generated from a combination of Cassini CIRS and HASI measurements" (Results and spectral line modeling) [from (cite: fla05; ful05)]
- External data: Line parameters and partition functions from JPL catalog; frequencies from Okabayashi & Tanimoto (HNC), Thorwirth et al. (HC3N)  
  > "Spectral line parameters and partition functions were taken from the JPL catalog" (Results and spectral line modeling) [from (cite: oka93), (cite: tho00)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA data reduction scripts by NA ALMA Science Center  
  > "The data were flagged and calibrated by the North American ALMA Science Center using the standard data reduction scripts and protocols provided by the Joint ALMA Observatory." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, Butler-JPL-Horizons 2012 model; 3C 279 bandpass  
  > "The flux scale was determined by setting the observed continuum level to match the Butler-JPL-Horizons 2012 flux model for Titan" (Observations)
- flux scale uncertainty: 15%  
  > "Absolute flux calibration is thus expected to be accurate to within 15%." (Observations)
- self calibration: Phase self-calibration on Titan continuum  
  > "Titan’s strong, compact continuum permitted self-calibration of the phases." (Observations)

### Imaging

- task: CASA 4.2.0 standard routines  
  > "Continuum subtraction and imaging were performed using standard routines in the NRAO CASA software version 4.2.0" (Observations)
- deconvolver: Hogbom, per channel, threshold 2x RMS  
  > "Deconvolution (cleaning) of the ALMA point-spread function (PSF) was performed for each spectral channel using the Hogbom algorithm" (Observations)
- weighting robust: natural  
  > "with natural visibility weighting and a threshold flux level of twice the RMS noise" (Observations)
- uv taper: _not stated_
- cell size: 0.05'' x 0.05''  
  > "The image pixel sizes were set to $0.05\times0.05''$." (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.54''x0.31'', PA 57.3 deg  
  > "(long axis $57.3^{\circ}$ clockwise from celestial north)" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Flux scale model for Titan  
  > "(see ALMA Memo #594[^1])" (Observations) [from ALMA Memo #594]
- Nitrogen/methane isotope abundances and aerosols in model  
  > "the abundances of nitrogen and methane isotopes and aerosols were the same as used by (cite: tea13)" (Results and spectral line modeling) [from (cite: tea13)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum subtraction
- Self-calibration solution interval
- Exact CASA task parameters and clean mask
- Temperature/aerosol profile files used in NEMESIS
- Aperture centering details and HC3N/HNC profile grids

## Analysis recipe

1. **Calibrate and image data cubes**: Standard ALMA calibration, flux scaling to Titan model, continuum subtraction, Hogbom cleaning  
  > "Continuum subtraction and imaging were performed using standard routines in the NRAO CASA software version 4.2.0" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make integrated emission maps in Titan frame**: Transform to projected distances and Titan rest frame; integrate ±1 km/s (HNC), ±5 km/s (HC3N)  
  > "using integration ranges $\pm1.0$ km $\rm{s}^{-1}$ with respect to line center for HNC and $\pm5.0$ km $\rm{s}^{-1}$ for HC$_3$N." (Results and spectral line modeling)
   - parameter: Topocentric radial velocity -0.91 km/s  
  > "using the JPL Horizons Topocentric radial velocity of $-0.91$ km $\rm{s}^{-1}$." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract disk-integrated spectra**: Integrate cubes over 1.5'' diameter circular aperture centered on Titan  
  > "obtained by integrating the observed data cubes over a circular aperture $1.5''$ (12,000 km) in diameter, centered on Titan." (Results and spectral line modeling)
   - fitting: _not stated_
   - validation: _not stated_
4. **Retrieve VMR profiles**: NEMESIS line-by-line radiative transfer with two-parameter gradient model (abundance at z_r=293 km, slope as fraction of scale height); HNC step model above 400 km  
  > "A two-parameter ‘gradient model’ was used for the HNC and HC$_3$N vertical mixing ratio (VMR) profiles, with a variable abundance at reference altitude $z_r = 293$ km" (Results and spectral line modeling)
   - software: NEMESIS
   - parameter: 10-point trapezium-rule integration to model top at 782 km  
  > "fluxes were calculated as a function of frequency using a 10-point trapezium-rule integration from the center of the disk to the edge of the model (at an altitude of 782 km)." (Results and spectral line modeling)
   - assumption: Profiles do not vary with latitude/longitude; HC3N condenses below ~71 km; Lorentz half-widths 1.290 (HNC), 0.1 (HC3N) cm-1/bar, exponents 0.69, 0.75  
  > "The HC$_3$N was assumed to condense out at altitudes below $z_c \simeq 71$ km" (Results and spectral line modeling)
   - fitting: chi^2 minimization between modeled and observed spectra  
  > "Employing a $\chi^2$ minimization between the modeled and observed spectra" (Results and spectral line modeling)
   - validation: Compared with previous VMR profiles (Marten, Teanby, Vinatier, Koskinen; Moreno 2012)  
  > "Our HC$_3$N VMR profile is in reasonable agreement with these previous studies" (Results and spectral line modeling)
5. **Map HC3N line core vs wings**: Integrate core (-0.5 to 0.5 km/s) and wings (2.0-5.0 km/s) separately to probe altitude  
  > "just the line core ($-0.5$ to 0.5 km $\rm{s}^{-1}$) and (b) just the line wings (2.0 to 5.0 km $\rm{s}^{-1}$ either side of the line center)" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.0: Continuum subtraction and imaging  
  > "Continuum subtraction and imaging were performed using standard routines in the NRAO CASA software version 4.2.0" (Observations)
- **NEMESIS** : Retrieval of HNC and HC3N VMR profiles  
  > "The spatially-integrated HNC and HC$_3$N emission lines were modeled using the NEMESIS retrieval code" (Results and spectral line modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HC3N abundance at 293 km | 0.62 | 0.04 | ppb | 4 | $0.62 \pm 0.04$ ppb for HC$_3$N |
| HNC abundance at 293 km (gradient model) | 0.063 | 0.025 | ppb | 4 | $0.063 \pm 0.025$ ppb for HNC |
| HNC column density (gradient) | 1.9e13 | not stated | cm^-2 | 4 | $1.9\times10^{13}$ cm$^{-2}$ for HNC |
| HC3N column density | 2.3e14 | not stated | cm^-2 | 4 | $2.3\times10^{14}$ cm$^{-2}$ for HC$_3$N |
| HNC step-model abundance above 400 km | 4.85 | 0.28 | ppb | 4 | The best-fitting abundance above 400 km was found to be $4.85\pm0.28$ ppb |
| HNC line FWHM | 0.76 | not stated | km/s | 3 | (FWHM $= 0.76$ km $\rm{s}^{-1}$) |
| HNC peak clockwise offset | 40 | 5 | deg | 2 | are offset clockwise by $40\pm5^{\circ}$ in the plane of the sky |

## Qualitative findings

- HNC and HC3N emission are not co-spatial; HC3N peaks over poles, HNC offset  
  > "Differences between the spectrally-integrated flux distributions of HNC and HC$_3$N show that these species are not co-spatial." (abstract)

## Claim tuples

- H: Are HNC and HC3N distributions spatially the same? | E: Integrated line maps from ALMA Band 7 cubes | R: Double-peaked; HC3N peaks over poles, HNC offset 40±5 deg clockwise | F: Species are not co-spatial; mesosphere may be longitudinally variable | **supported**
- H: At what altitudes are HNC and HC3N found? | E: NEMESIS fits to disk-averaged line profiles | R: HNC at z≳400 km; HC3N across ~70-600 km | F: HNC confined to the upper atmosphere, HC3N broadly distributed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Diurnal chemical differentiation judged unlikely for HNC asymmetry because zonal winds mix longitudes in ~45 hr versus 382 hr day  
  > "which renders diurnal chemical differentiation an unlikely explanation for the observed structures" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Single line per species insufficient to constrain the true HNC distribution  
  > "High signal-to-noise ratio observations of multiple emission lines could help constrain the true HNC distribution." (Results and spectral line modeling)
- Caveat (inferred, ours): Models assume no latitude/longitude variation despite resolved asymmetries
- Caveat (inferred, ours): Only 158 s of data and low resolution relative to Titan's disk
- Caveat (inferred, ours): Gradient and step models degenerate for HNC

## Reproducibility

- Data public (paper): ALMA project 2012.A.00033.S data acknowledged  
  > "The article makes use of the following ALMA data: ADS/JAO.ALMA#2012.A.00033.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: NEMESIS input profiles and configuration
- Missing: CASA scripts and masks
- Missing: Line-free channels
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Imaging is described but the radiative-transfer inputs and scripts are not provided.
- Rediscovery candidate: yes, Data are public, imaging parameters are largely given, and results are numeric, though the NEMESIS modeling needs unstated inputs.

## Links

- Method: (cite: irw08) (NEMESIS retrieval code)
- Method: (cite: mcm07) (CASA)
- Companion: (cite: cor14) (ISON ALMA DDT project in which Titan was the flux calibrator)
- Related: ALMA DDT comet ISON project

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 70,
  "stated": 40,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
