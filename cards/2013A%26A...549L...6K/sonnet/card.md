# ALMA CO J = 6-5 observations of IRAS 16293-2422. Shocks and entrainment

`2013A&A...549L...6K` | Astronomy and Astrophysics 2013 | first author: Kristensen, L. E. | arXiv: 1212.1685 | DOI: 10.1051/0004-6361/201220668

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Where does outflow energy feed back into the envelope of IRAS16293-2422, and is source B driving the blue-shifted arch/outflow or is it a bow shock from source A?  
  > "Observations of higher-excited transitions of abundant molecules such as CO are important for determining where energy in the form of shocks is fed back into the parental envelope of forming stars." (abstract)
- Target **IRAS16293-2422 (sources A and B)**: coordinates _not stated_; z/distance not stated numerically (5'' = ~600 AU implies ~120 pc)  
  > "At the distance to the source (cite: loinard08), these angular separations correspond to physical distances of $\sim$600 AU and 36 AU respectively." (Introduction); distance from Loinard et al. 2008 (cite: loinard08)  
  > "At the distance to the source (cite: loinard08), these angular separations correspond to physical distances of $\sim$600 AU and 36 AU respectively." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00007.SV
- bands: Band 9, seven-point mosaic  
  > "The observations consist of a seven-point mosaic in Band 9" (Observations and results)
- frequencies and spectral setup: 4 spectral windows, 3840 channels each, 488 kHz (0.21 km/s) spacing, 1.875 GHz bandwidth  
  > "All four spectral windows consist of 3840 channels with a channel separation of $\unit[488]{kHz}$ ($\unit[0.21]{km\,s^{-1}}$ at 690 GHz) and a total bandwidth of 1.875 GHz." (Observations and results)
- continuum bandwidth: _not stated_
- arrays: 15 antennas  
  > "using 15 antennas and a configuration with baselines ranging from 26 to $\unit[402]{m}$" (Observations and results)
- configurations: _not stated_
- baselines: 26 to 402 m (62 to 943 klambda at 690 GHz)  
  > "baselines ranging from 26 to $\unit[402]{m}$ (62 to $\unit[943]{k\lambda}$ at $\unit[690]{GHz}$)" (Observations and results)
- angular resolution: 0.29'' x 0.16'', PA 110 deg  
  > "The resulting spatial resolution is 0.29$''$$\times$0.16$''$ at a position angle of $\unit[110]{\ensuremath{^\circ}}$." (Observations and results)
- max recoverable scale: _not stated_
- sensitivity: 100 mJy/beam per 0.21 km/s channel  
  > "The rms noise is $\unit[100]{mJy\,beam^{-1}}$ per 0.21 km s$^{-1}$ channel." (Observations and results)
- time on source: ~18 minutes per pointing  
  > "The on-source integration time was $\sim$18 minutes per pointing" (Observations and results)
- observing dates: April 16 (1 execution) and 17, 2012 (3 executions)  
  > "on April 16 (1 execution) and 17, 2012 (3 executions)" (Observations and results)
- pi or archival as stated: ALMA Science Verification data  
  > "were taken as one of the ALMA Science Verification datasets" (Observations and results)
- Line: CO J=6-5 (691.473 GHz)
- Other facility **JCMT**: CO J=6-5 single-dish spectrum (July 2000, 8'' beam) to quantify spatial filtering  
  > "we compare emission to a CO J=6–5 spectrum from the James Clerk Maxwell Telescope (JCMT) towards I16293-A." (Observations and results)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated data taken from CASA guides website  
  > "The calibrated data were taken from the CASA guides website" (Observations and results)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-calibration on continuum, confirming CASA guide; solution applied to the measurement set  
  > "We performed phase and amplitude self calibration on the continuum, confirming the results from the CASA guide." (Observations and results)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "The visibilities were imaged using a robust weighting of 0.5." (Observations and results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Cube and continuum corrected for primary-beam attenuation  
  > "The spectral cube and the continuum image were corrected for primary-beam attenuation" (Observations and results)
- array combination: _not stated_
- smoothing: Smoothed to 0.84 km/s effective velocity resolution  
  > "smoothed to an effective resolution of $\unit[0.84]{km\,s^{-1}}$" (Observations and results)
- final beam: 0.29'' x 0.16'', PA 110 deg  
  > "The resulting spatial resolution is 0.29$''$$\times$0.16$''$ at a position angle of $\unit[110]{\ensuremath{^\circ}}$." (Observations and results)
- final rms: 100 mJy/beam per 0.21 km/s channel  
  > "The rms noise is $\unit[100]{mJy\,beam^{-1}}$ per 0.21 km s$^{-1}$ channel." (Observations and results)

### Inherited from earlier work

- Calibration and self-calibration following CASA guide  
  > "We performed phase and amplitude self calibration on the continuum, confirming the results from the CASA guide." (Observations and results) [from CASA guides website (casaguides.nrao.edu)]
- JCMT spectrum similar to earlier published one  
  > "is similar to that presented in (cite: stark04)" (Observations and results) [from (cite: stark04)]

### Not stated but needed to reproduce (our reading)

- CASA version and specific CASA guide used
- Self-calibration solution intervals and reference antenna
- Imaging task, deconvolver, cell and image size, cleaning masks and threshold
- Continuum subtraction method and line-free channels
- Continuum image construction details
- Source coordinates
- JCMT data reduction details
- Pointing/phase centers of mosaic

## Analysis recipe

1. **Flag bad baselines**: Compared visibilities of two executions with near-identical uv coverage; flagged baselines with questionable amplitudes  
  > "Two out of 105 baselines exhibited questionable amplitudes and were therefore flagged." (Observations and results)
   - parameter: Flagged DA47&DV14 and DA41&DV09  
  > "we flag the baseline DA47&DV14, which is the only one that samples spatial scales above 3$^{\prime}$$^{\prime}$." (Data reduction details)
   - fitting: _not stated_
   - validation: Cross-checked between execution blocks observed ~24 h apart  
  > "We made use of the fact that two execution blocks were observed almost exactly 24 hours apart, leading to almost identical $uv$ coverage." (Data reduction details)
2. **Image the cube and continuum**: Robust 0.5 weighting, primary-beam correction, smoothing to 0.84 km/s  
  > "The visibilities were imaged using a robust weighting of 0.5." (Observations and results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Quantify spatial filtering vs JCMT**: Convolved ALMA data with 8'' beam at JCMT position and compared spectra; JCMT converted to Jy with 34.0 Jy/beam/K  
  > "The JCMT data were converted to flux density using a conversion factor of 34.0 Jy beam$^{-1}$ K$^{-1}$." (Observations and results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Morphology and kinematics of outflow knots**: Blue/red integrated maps, channel maps, and position-velocity diagram with 1.25'' wide slit  
  > "we created a position-velocity (pv) diagram with a wide slit of 1.25$''$ to capture the red-shifted emission NW of source A" (Discussion: origin of the emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test whether source B drives the arch**: Radiative-transfer argument comparing emission ratio and opacity toward A and B assuming equal tau and source function but different recovered fractions  
  > "We do so by assuming that the opacity towards the continuum peaks of sources A and B are the same" (Comparison of outflow emission at sources A and B)
   - parameter: R = 3.05/1.13 = 2.69  
  > "The value of $R$ is 3.05 Jy beam$^{-1}$ / 1.13 Jy beam$^{-1}$ = 2.69." (Comparison of outflow emission at sources A and B)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration guide followed; self-calibration  
  > "confirming the results from the CASA guide" (Observations and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Flux recovered by ALMA, full velocity range | ~5 | not stated | % | 3 | ALMA recovers $\sim$5% of the flux density in the full velocity range |
| Recovered emission in blue/red wings (excl. ±3 km/s) | ~15 and ~10 | not stated | % | 3 | approximately 15 and 10% of emission is recovered, respectively |
| Recovered emission blue/red wings (excl. ±8 km/s) | ~50 and 15 | not stated | % | 3 | $\sim$ 50 and 15% of emission is recovered in the blue and red wings, respectively |
| Space velocity of E-W red knot | ~90 | not stated | km/s | 4 | implies a space velocity of $\sim$90 km s$^{-1}$ with an inclination angle of $\sim$5$^\circ$ |
| Maximum eta toward B for emission ratio 0.5 | ≤0.5 | not stated | dimensionless | 5 | For an observed emission ratio of 0.5, $\eta$ is at most 0.5, irrespective of $\tau$ |
| Dynamic age of blue arch | ≲300 | not stated | yr | 4 | The dynamic age of the blue arch is $\lesssim$ 300 yrs for a flow velocity of 10 km s$^{-1}$ |

## Qualitative findings

- Blue arch near B is a bow shock from source A, not driven by B; B shows no current outflow  
  > "Instead, a blue-shifted bow shock from source A is overlapping with source B in the plane of the sky." (Summary and conclusions)

## Claim tuples

- H: Is source B driving the blue-shifted arch? | E: Morphology, velocity structure and radiative-transfer argument with channel maps | R: Source B is not at the arch apex; highest velocities not nearest B; eta ≤0.5 | F: Arch is a bow shock from source A overlapping B by chance alignment | **supported**
- H: How much emission does the interferometer recover? | E: Compared ALMA convolved to 8'' with JCMT spectrum | R: ~5% overall; higher fraction at high velocity | F: High-velocity structures are less affected by filtering | **supported**
- H: Where does entrainment occur? | E: PV diagram of NW red-shifted knots | R: Rapid deceleration over ~0.5'' | F: Entrainment over scales >~100 AU, turbulent-wind-like, in localised hotspots | **supported**

## Reasoning

- Why this data: Band 9 data give high resolution and a high-temperature tracer weakly affected by chemistry  
  > "a high-temperature tracer only weakly affected by chemistry are a perfect combination to re-examine the origin of molecular emission" (Introduction)
- Why this method: _not stated_
- Alternative: Loinard et al. interpretation of B as first hydrostatic core origin of arch rejected since B is not at apex  
  > "However, for that to be the case, source B must be located at the apex of the arch." (Comparison of outflow emission at sources A and B)
- How they decided it was enough: _not stated_
- Limitation (authors): Large-scale emission filtered out; full ALMA with ACA and TP needed  
  > "full ALMA (with the Atacama Compact Array, ACA, and Total Power, TP, telescopes included) will be required to capture this emission" (Discussion: origin of the emission)
- Caveat (inferred, ours): Flagging two baselines changes spectra near blue arch; result sensitivity to flagging only shown qualitatively
- Caveat (inferred, ours): Equal tau and source-function assumption for A and B is strong
- Caveat (inferred, ours): No uncertainties on recovered fractions
- Caveat (inferred, ours): Imaging parameters incomplete

## Reproducibility

- Data public (paper): ALMA Science Verification data, calibrated data on CASA guides  
  > "The calibrated data were taken from the CASA guides website" (Observations and results)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Self-calibration details
- Missing: JCMT spectrum
- Missing: Source coordinates
- Data volume (inferred): ~tens of GB (SV band 9 mosaic, four executions; CASA guide calibrated set smaller)
- Score (inferred): 3/5, Public data and some key settings (robust, flags) given, but imaging details and JCMT data missing; results largely qualitative.
- Rediscovery candidate: no, Main results are mostly qualitative morphology and imaging details are incomplete.

## Links

- Companion: Loinard et al. 2012 (cite: loinard12) (Alternative interpretation of source B and the arch)
- Companion: Pineda et al. 2012 (cite: Pineda2012) (Other ALMA SV observations of IRAS16293 source B)
- Related: ALMA Science Verification

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 36,
  "rate": 0.537
 },
 "evidence_ok": true
}
```
