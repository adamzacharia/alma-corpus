# ALMA Mapping of Rapid Gas and Dust Variations in Comet C/2012 S1 (ISON):New Insights into the Origin of Cometary HNC

`2017ApJ...838..147C` | The Astrophysical Journal 2017 | first author: Cordiner, M. A. | arXiv: 1702.03322 | DOI: 10.3847/1538-4357/aa6590

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system, astrochemistry
- Question: How do the gas (HNC, CH3OH, H2CO) and dust distributions in comet ISON vary on timescales of minutes to an hour, and what does this say about the origin of cometary HNC?  
  > "we use temporally-resolved ALMA observations to examine the detailed spatial distribution and time variability of emission from dust and molecules in comet ISON on 2013 November 16-17." (Introduction)
- Target **Comet C/2012 S1 (ISON)**: coordinates not stated (tracked with JPL Horizons ephemeris solution #45)  
  > "Comet ISON was observed pre-perihelion on UT 2013-11-16 at 10:10-11:00 (at a heliocentric distance $r_H=0.58$ AU and geocentric distance $\Delta=0.89$ AU)" (2 Observations); "The comet’s position was tracked using JPL Horizons ephemeris solution #45" (2 Observations); z/distance r_H=0.58 AU, Delta=0.89 AU (Nov 16); r_H=0.54 AU, Delta=0.88 AU (Nov 17)  
  > "Comet ISON was observed pre-perihelion on UT 2013-11-16 at 10:10-11:00 (at a heliocentric distance $r_H=0.58$ AU and geocentric distance $\Delta=0.89$ AU)" (2 Observations); "The comet’s position was tracked using JPL Horizons ephemeris solution #45" (2 Observations); distance from JPL Horizons ephemeris  
  > "Comet ISON was observed pre-perihelion on UT 2013-11-16 at 10:10-11:00 (at a heliocentric distance $r_H=0.58$ AU and geocentric distance $\Delta=0.89$ AU)" (2 Observations); "The comet’s position was tracked using JPL Horizons ephemeris solution #45" (2 Observations)

## Data provenance

- ALMA projects: 2012.A.00033.S
- bands: Band 7, 350.3-352.3 GHz (LSB) and 362.2-364.1 GHz (USB)  
  > "using the (dual sideband) ALMA band 7 receiver, covering frequencies 350.3-352.3 GHz (lower sideband) and 362.2-364.1 GHz (upper sideband)" (2 Observations)
- frequencies and spectral setup: four spectral windows; 244 kHz channel spacing, 488 kHz resolution (~0.4 km/s) after Hanning smoothing  
  > "The ALMA correlator was configured with four spectral windows to simultaneously observe all the lines of interest plus continuum on each day" (2 Observations); "The correlator channel spacing of 244 kHz resulted in a spectral resolution of 488 kHz (about 0.4 km $\rm{s}^{-1}$) after Hanning smoothing in the time domain." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 28 x 12-m antennas  
  > "Using $28\times12$-m antennae (with baseline lengths in the range 17.3-1284 m)" (2 Observations)
- configurations: _not stated_
- baselines: 17.3-1284 m  
  > "Using $28\times12$-m antennae (with baseline lengths in the range 17.3-1284 m)" (2 Observations)
- angular resolution: 0.28''x0.44'' (0.40''x0.54'' after excluding distant antennas)  
  > "the angular resolution was $0.28''\times0.44''$" (2 Observations); "resulting in a corresponding improvement in image quality at the expense of a small degradation in angular resolution (to $0.40''\times0.54''$)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 13.7 min per period (pairs of scans), 3 periods per day, ~17 min between periods  
  > "Each period had a total on-source integration time of 13.7 min and the time interval between periods was approx. 17 min." (2 Observations)
- observing dates: 2013-11-16 10:10-11:00 UT and 2013-11-17 12:30-13:20 UT  
  > "Observations were made in Cycle 1 Early Science mode" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HNC 4-3 (362.630 GHz)
- Line: H2CO 5(1,5)-4(1,4) (351.769 GHz)
- Line: CH3OH 4_0-3_-1, 1_1-0_0, 16_1-16_0, 7_2-6_1 (350687.7, 350905.1, 363440.4, 363739.9 MHz)
- External data: H2CO photodissociation rate 6.7e-4 s^-1 at r_H=0.58 AU  
  > "a photodissociation rate of $6.7\times10^{-4}$ s$^{-1}$ (appropriate for $r_H=0.58$ AU; (cite: hue92))" (4 Discussion) [from (cite: hue92)]
- External data: Sublimation lifetime of icy sub-mm grains ~ few thousand seconds at 0.5 AU  
  > "(cite: bee06) calculated a lifetime (for complete sublimation) on the order of a few thousand seconds." (4 Discussion) [from (cite: bee06)]

## Processing

### Calibration

- pipeline or manual: standard CASA routines for flagging, calibration and imaging  
  > "The data were flagged, calibrated and imaged using standard routines in CASA version 4.1.0 (cite: mcm07)." (2 Observations)
- casa version: CASA 4.1.0  
  > "The data were flagged, calibrated and imaged using standard routines in CASA version 4.1.0 (cite: mcm07)." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (Nov 16) and Titan (Nov 17); 3C 279 for bandpass/phase/gain  
  > "For calibration of the flux scale, observations of the Solar System bodies Pallas and Titan were used, resulting in absolute fluxes accurate to within about 15%." (2 Observations)
- flux scale uncertainty: about 15%  
  > "resulting in absolute fluxes accurate to within about 15%" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean; each science scan imaged individually, then scans 4&6, 8&10, 12&14 averaged into 3 periods  
  > "the scans taken on each day were combined into pairs, by averaging scans 4&6, scans 8&10 and scans 12&14 into three discrete observation periods" (2 Observations)
- deconvolver: Högbom, threshold twice expected RMS noise per channel  
  > "Deconvolution of the point-spread function (PSF) was performed using the Högbom algorithm, with natural visibility weighting and a flux threshold of twice the expected RMS noise per channel in each image." (2 Observations)
- weighting robust: natural weighting  
  > "with natural visibility weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum imaged by averaging all line-free channels  
  > "Comet ISON’s 0.8 mm continuum was imaged by averaging the observed data over all line-free channels." (2 Observations)
- line free channels: _not stated_
- primary beam correction: Gaussian primary beam, HPBW = 16'' at 363 GHz  
  > "the interferometric images were corrected for the Gaussian spatial response of the ALMA primary beam (half-power beam-width = $16''$ at 363 GHz)" (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.40''x0.54''  
  > "(to $0.40''\times0.54''$)" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Haser daughter model visibility-amplitude fitting of HNC  
  > "We followed the same methodology as (cite: cor14) to fit the visibility (Fourier) amplitude components of the observed HNC data using a Haser daughter model." (3 Results) [from (cite: cor14)]
- Outflow velocity of 1.0 km/s (and coma parameters) for H2CO model  
  > "fixed temperature of $T=90$ K, $v_{out}=1.0$ km $\rm{s}^{-1}$ (see (cite: cor14))" (4 Discussion) [from (cite: cor14)]

### Not stated but needed to reproduce (our reading)

- Which antennas/array details and flagging beyond DV07, DV19, DV25
- Line-free channel ranges for continuum
- Clean mask, image size and cell size
- Haser model code and non-linear least-squares implementation details
- Rebinning grid for visibility analysis
- Parent-scale-length priors/fitting method
- CASA simulator configuration
- Flux scale model for Pallas/Titan

## Analysis recipe

1. **Calibrate and image data into time periods**: Standard CASA calibration; exclude distant antennas; Högbom clean with natural weighting; combine scan pairs into 3 periods per day  
  > "the most distant antennae (DV07, DV19 and DV25; $>500$ m from the array center) were excluded during imaging" (2 Observations)
   - software: CASA
   - parameter: clean threshold 2x expected RMS per channel  
  > "a flux threshold of twice the expected RMS noise per channel in each image" (2 Observations)
   - fitting: _not stated_
   - validation: Phase calibrator 3C 279 showed uniform point-source intensity throughout  
  > "our images of the phase calibrator 3C 279 (less than 10$^{\circ}$ away on the sky) showed a uniform intensity point-source over throughout the observations" (2013 November 16)
2. **Make moment maps and measure fluxes**: Integrate cubes over -2 to +2 km/s; sum CH3OH lines; integrate flux in 2.5'' (1600 km) radius circle; errors from RMS of emission-free regions  
  > "the total flux was obtained by integrating over the emission maps within a circle of radius $2.5''$ (1600 km) centered on the origin" (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit HNC visibilities with Haser daughter model**: Rebin real visibility amplitudes to uniform baseline grid; fit Haser daughter model for parent scale length  
  > "The real parts of the visibility amplitudes (visibilities) were first rebinned to a uniform antenna separation (baseline) grid" (2013 November 17)
   - fitting: Haser model fit following cor14; details not stated  
  > "We followed the same methodology as (cite: cor14) to fit the visibility (Fourier) amplitude components of the observed HNC data using a Haser daughter model." (Results, 2013 November 17)
   - validation: _not stated_
4. **Model H2CO flux decline on Nov 16**: Time-dependent Haser daughter model with step change in production rate; synthetic images with CASA simulator; fit Q_i, Q_f/Q_i, t  
  > "Synthetic images were generated using the CASA simulator, with the same observational and imaging characteristics as for our ALMA observations." (4 Discussion)
   - software: CASA simulator
   - parameter: parent scale length 280 km, H2CO mixing ratio 0.8%, T=90 K, v_out=1.0 km/s  
  > "fixed parent scale length of 280 km, H$_2$CO mixing ratio of 0.8%, fixed temperature of $T=90$ K" (4 Discussion)
   - fitting: best fit to measured H2CO fluxes  
  > "The best fit to our measured H$_2$CO fluxes is for $Q_{i}=1.05\times10^{29}$ s$^{-1}$, $Q_{f}/Q_i=0.49$ and $t=3.5$ min" (4 Discussion)
   - validation: _not stated_
5. **Model HNC clump production rate (Nov 17 period 3)**: Two-component isotropic outflow model, sources at nucleus and clump; nonlinear least-squares  
  > "Optimizing the HNC production rates of the two sources using a nonlinear least-squares procedure, an excellent fit to the observed image was obtained" (4.2)
   - parameter: v_out = 1 km/s, T = 90 K  
  > "both with $v_{out}=1$ km $\rm{s}^{-1}$ and $T=90$ K" (4.2)
   - fitting: nonlinear least squares  
  > "Optimizing the HNC production rates of the two sources using a nonlinear least-squares procedure, an excellent fit to the observed image was obtained" (Discussion, Elucidating the nature of cometary HNC release)
   - validation: noise-like residuals in observation-minus-model image  
  > "the noise-like residuals indicate the quality of fit" (4.2)

## Software

- **CASA** 4.1.0: flagging, calibration, imaging, simulation of synthetic observations  
  > "The data were flagged, calibrated and imaged using standard routines in CASA version 4.1.0 (cite: mcm07)." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HNC parent scale length L_p (periods 1-2, Nov 17) | 450 | range 250-1200 km | km | 3 | the best-fitting HNC parent scale length ($L_p$) was found to be 450 km (with possible values in the range $L_p=250$-1200 km due to statistical uncertainties) |
| HNC parent scale length lower limit (period 3) | >750 | lower limit | km | 3 | it was only possible to derive a lower limit from our data of $L_p>750$ km |
| Continuum flux decline Nov 16 | >=42 | not stated | percent | 2 | falling by at least 42% during our observations |
| H2CO flux decline Nov 16 | 52-72 | not stated | percent | 2 | the flux fell in an approximately linear fashion by 52-72% between periods 1-3 |
| H2CO production drop Q_f/Q_i | 0.49 | not stated | dimensionless | 4 | $Q_{i}=1.05\times10^{29}$ s$^{-1}$, $Q_{f}/Q_i=0.49$ and $t=3.5$ min |
| Q_i (H2O production rate) | 1.05e29 | not stated | s^-1 | 4 | $Q_{i}=1.05\times10^{29}$ s$^{-1}$ |
| HNC clump distance from nucleus (period 3) | 870 | 25 km | km | 2 | at a position $870\pm25$ km north-west of the nominal nucleus position |
| HNC clump mean velocity (sky plane) | 0.41 | not stated | km/s | 2 | at an average velocity of 0.41 km $\rm{s}^{-1}$ (in the plane of the sky) |
| Q(HNC) nucleus | 2.9e25 | not stated | s^-1 | 5 | $Q({\rm HNC})=2.9\times10^{25}$ s$^{-1}$ for the nucleus |
| Q(HNC) clump | 3.2e25 | not stated | s^-1 | 5 | $Q({\rm HNC})=3.2\times10^{25}$ s$^{-1}$ for the clump |
| Continuum offset from ephemeris | 5.7 (Nov 16), 6.6 (Nov 17) | not stated | arcsec | 1 | offset by $5.7''$ from the predicted ephemeris position at the start of observations on Nov 16, and by $6.6''$ on Nov 17 |

## Qualitative findings

- HNC morphology varied strongly on Nov 17 while CH3OH, H2CO and continuum stayed stable, indicating a clumpy intermittent HNC outflow  
  > "The HNC maps, on the other hand, reveal a striking time variability that is most evident when comparing observation periods 1 and 3." (2013 November 17)

## Claim tuples

- H: Did ISON's gas and dust activity drop abruptly on Nov 16? | E: Time-resolved fluxes in 3 periods and time-dependent Haser model of H2CO | R: Line and continuum fluxes fell >42%; H2CO consistent with ~50% production-rate drop | F: Abrupt reduction in activity during observations, with dust loss aided by outflow and sublimation | **supported**
- H: Is the HNC clumpy structure transient and tied to refractory material? | E: Time series of HNC maps on Nov 17, 1-D profiles, two-component model | R: Isolated HNC clump appears 870 km from nucleus in period 3, not seen in H2CO or CH3OH | F: At least part of HNC arises from degradation of N-rich organic refractory material released intermittently | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Calibration error or array problem ruled out as cause of flux drop, since 3C 279 stayed constant  
  > "A calibration error or problem with the telescope array can be ruled out as the source of this variation" (2013 November 16)
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N prevented velocity information and tracking HNC structure on Nov 16; many time-variability scenarios fit the data  
  > "the signal-to-noise of our spectral profiles was insufficient to derive any useful radial velocity information for the gases" (2013 November 17)
- Caveat (inferred, ours): Few time points; model degeneracy for production-rate history
- Caveat (inferred, ours): Flux uncertainties large for HNC and CH3OH
- Caveat (inferred, ours): Clump detected at ~6 sigma in single period
- Caveat (inferred, ours): Table error notation inconsistent (e.g. 1.03±20)

## Reproducibility

- Data public (paper): ALMA data set 2012.A.00033.S used  
  > "It makes use of ALMA data set #2012.A.00033.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Haser/outflow model code
- Missing: Image parameters (cell, size, masks)
- Missing: Details of flagging and flux models
- Data volume (inferred): ~50-200 GB raw (Cycle 1, 28 antennas, 4 spws, 2 days)
- Score (inferred): 3/5, Public data and standard CASA, but modelling code and imaging details are missing.
- Rediscovery candidate: no, Key results rely on unreleased modelling and unspecified imaging parameters.

## Links

- Companion: (cite: cor14) (Earlier ALMA observations of ISON on Nov 17 whose methodology is followed)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
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
  "facts": 69,
  "stated": 43,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
