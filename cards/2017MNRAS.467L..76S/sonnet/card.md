# Vertical structure of the transition zone from infalling rotating envelope to disc in the Class 0 protostar, IRAS 04368+2557

`2017MNRAS.467L..76S` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Sakai, Nami | arXiv: - | DOI: 10.1093/mnrasl/slx002

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the radial and vertical structures of the envelope/disk transition zone around the centrifugal barrier in the Class 0 protostar L1527?  
  > "Here we report detailed distributions of the gas around the centrifugal barrier by resolving radial and vertical structures of the disk/envelope system in L1527." (1 INTRODUCTION)
- Target **L1527 (IRAS04368+2557)**: coordinates 04h39m53.87s, +26d03m09.6s (J2000)  
  > "The field centre is (α 2000, δ 2000 ) = (04 h 39 m 53 s .87, 26 ◦ 03 ′ 09 ′′ .6)" (2 OBSERVATIONS); "(78 au × 21 au at a distance of 137 pc)" (3.1 Continuum); z/distance 137 pc  
  > "The field centre is (α 2000, δ 2000 ) = (04 h 39 m 53 s .87, 26 ◦ 03 ′ 09 ′′ .6)" (2 OBSERVATIONS); "(78 au × 21 au at a distance of 137 pc)" (3.1 Continuum); distance from _not stated_

## Data provenance

- ALMA projects: 2013.0.00858.S
- bands: Band 6 (1.2 mm) and Band 7 (0.8 mm)  
  > "The observations were carried out on 2015 July 18 (Band 6) and July 18and20(Band7)" (2 OBSERVATIONS)
- frequencies and spectral setup: 16 windows, each 59 MHz wide with 61 kHz channels  
  > "The backend correlator was split into 16 small windows, each of which has the bandwidth and channel spacing of 59 MHz and 61 kHz, respectively." (2 OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-7  
  > "in the C34-7 ALMA EarlyScienceconfiguration." (2 OBSERVATIONS)
- baselines: 19.51-158.0 m (Band 6), 33.0-1565.0 m (Band 7)  
  > "The data were obtained over a baseline range of 19.51158.0 m for Band 6, and 33.0-1565.0 m for Band 7" (2 OBSERVATIONS)
- angular resolution: 0.25''x0.13'' (0.8 mm), 0.37''x0.23'' (1.2 mm)  
  > "0.25 ′′ ×0.13 ′′ and 0.37 ′′ ×0.23 ′′ at 0.8 mm and 1.2 mm, respectively" (abstract)
- max recoverable scale: Emission extended more than 5.6'' (Band 6) and 2.4'' (Band 7) is resolved out  
  > "so that the emission extended more than 5.6 ′′ and 2.4 ′′ for Band 6 and Band 7, respectively, is solved out." (2 OBSERVATIONS)
- sensitivity: _not stated_
- time on source: 40.95 min (Band 6), 58.06 min (Band 7)  
  > "The total integration time and the typical system temperature were 40.95 min, 58.06 min" (2 OBSERVATIONS)
- observing dates: 2015 July 18 (Band 6), July 18 and 20 (Band 7)  
  > "The observations were carried out on 2015 July 18 (Band 6)" (2 OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: CCH N=4-3, J=9/2-7/2, F=5-4 and 4-3 (349.3377056 and 349.3389882 GHz)
- Line: SO J_N=7_8-6_7 (340.7141550 GHz)
- Line: SO J_N=7_6-6_5 (261.8437210 GHz)
- Line: CCH N=3-2, J=7/2-5/2 (262.0042600 and 262.0064820 GHz)
- External data: Temperature model of L1527 used for dust opacity and inner-region temperature estimates  
  > "assuming the temperature model for this source reported by Tobin et al. (2013)" (3.2 CCH) [from Tobin et al. (2013)]
- External data: Cycle 0 integrated 0.8 mm flux 485 ± 7 mJy  
  > "observed by ALMA Cycle 0 at the same frequency (485 ± 7 mJy)" (3.1 Continuum) [from Sakai et al. 2014a]
- External data: Protostellar mass 0.18 Msun from IRE kinematics  
  > "by using the mass (0.18 M ⊙ ) derived from the kinematics of the IRE (Sakai et al. 2014a)" (3.3 SO) [from Sakai et al. 2014a]
- Simulation/model as data: Ballistic IRE model and a Keplerian model overlaid on PV diagrams  
  > "position velocity (PV) diagram of CCH along the mid-plane overlaid to the IRE model (Sakai et al. 2014b; Oya et al. 2015)" (3.2 CCH)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013 and J0510+1800  
  > "The absolute flux density scale was derived from J0423013 and J0510+1800." (2 OBSERVATIONS)
- flux scale uncertainty: less than 10 %  
  > "uncertainties are less than 10 %" (2 OBSERVATIONS)
- self calibration: Applied using continuum data after normal calibration  
  > "After the normal calibration, self-calibration was applied by using the continuum data" (2 OBSERVATIONS)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted directly from visibilities; continuum from line-free channels  
  > "Line images were obtained after subtracting the continuum directly from the visibilities." (2 OBSERVATIONS)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Band 7 continuum 0.26'' x 0.13'', PA -27.0 deg  
  > "The synthesized beam size for the continuum map in Band 7 is 0.26 ′′ × 0.13 ′′ with the position angle (PA) of -27.0 ◦ ." (2 OBSERVATIONS)
- final rms: 1σ = 0.9 mJy/beam (0.8 mm continuum)  
  > "where 1σ is 0.9 mJy beam −1" (Figure 1 caption)

### Inherited from earlier work

- IRE ballistic model  
  > "The IRE model assumes a constant molecular abundance, and does not consider excitation effects." (3.2 CCH) [from Sakai et al. 2014b; Oya et al. 2015]
- H2 density 1e8 cm-3 and line width 0.5 km/s adopted in RADEX  
  > "the H 2 density and the line width were assumed to be 10 8 cm −3 and 0.5 km s −1, respectively (Sakai et al. 2014a,b)" (3.3 SO) [from Sakai et al. 2014a,b]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Imaging weighting/robust, cell and image size, deconvolver
- Line-free channels and self-calibration solution intervals
- Details of Gaussian fit for thickness profile
- Parameters of the IRE and Keplerian models (inclination, outer radius beyond 160 au)
- Flux values of J0423-013 and J0510+1800
- Apertures and velocity ranges for moment maps

## Analysis recipe

1. **Measure continuum size and thickness**: 2D Gaussian fit to the 0.8 mm continuum; Gaussian fit of east-west intensity profile as a function of offset  
  > "The FWHM thickness of the disk-like structure is measured by the Gaussian fit, as a function of the radial offset from the protostar." (3.1 Continuum)
   - assumption: Distance 137 pc  
  > "78 au × 21 au at a distance of 137 pc" (3.1 Continuum)
   - fitting: _not stated_
   - validation: Compared with Cycle 0 flux  
  > "The integrated flux is 15 % lower than that observed by ALMA Cycle 0 at the same frequency" (3.1 Continuum)
2. **Map CCH and SO kinematics**: Moment 0, velocity channel maps and PV diagrams along the mid-plane compared with IRE and Keplerian models  
  > "we prepared the PV diagram along the mid-plane, as shown in Figure 2c." (3.3 SO)
   - parameter: Keplerian model mass 0.18 Msun, outer radius 160 au  
  > "Here, the outer radius is arbitrarily set to be 160 au." (3.3 SO)
   - fitting: _not stated_
   - validation: Visual comparison with models  
  > "Nevertheless, the model well reproduces the characteristic kinematic behaviour of the observed PV diagram." (3.2 CCH)
3. **Derive SO gas kinetic temperature**: Non-LTE LVG analysis of the two SO lines in two 0.4'' circular apertures at 100 and 150 au  
  > "We used the RADEX code (van der Tak et al. 2007), where the H 2 density and the line width were assumed to be 10 8 cm −3 and 0.5 km s −1" (3.3 SO)
   - software: RADEX
   - assumption: n(H2)=1e8 cm-3, linewidth 0.5 km/s  
  > "10 8 cm −3 and 0.5 km s −1, respectively" (3.3 SO)
   - fitting: _not stated_
   - validation: Optical depth lower than 0.3  
  > "the optical depth of the lines are lower than 0.3" (3.3 SO)

## Software

- **RADEX** : Non-LTE LVG SO excitation analysis  
  > "We used the RADEX code (van der Tak et al. 2007)" (3.3 SO)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak flux (0.8 mm) | 96.71 | 0.08 | mJy/beam | 1 | The peak flux is determined to be 96.71 ± 0.08 mJy beam −1 from the 2D Gaussian fit |
| Continuum integrated flux | 410.6 | 0.4 | mJy | 1 | the integrated flux is 410.6 ± 0.4 mJy |
| Deconvolved continuum size | 0.57'' x 0.15'' (78 au x 21 au), PA 2.9 deg | not stated | arcsec | 1 | A deconvolved size is 0.57 ′′ × 0.15 ′′ (78 au × 21 au at a distance of 137 pc) with PA of 2.9 ◦ . |
| Deconvolved thickness at continuum peak | 0.12 (16 au) | not stated | arcsec | 1 | The thickness deconvolved with the synthesized beam is 0.12 ′′ (16 au) at the continuum peak |
| SO total flux | 2.0 | not stated | Jy km/s | 2 | The total flux is 2.0 Jy km s −1 . |
| SO temperature at 100 au | 194 | +146/-60 | K | 3 | The result is 194 ( + − 146 60 ) K at 100 au |
| SO temperature at 150 au | 29 | +26/-11 | K | 3 | 29( + − 26 11 ) K at 150 au. |

## Qualitative findings

- CCH emission is absent inside 100 au on the mid-plane, and the envelope thickness doubles inward of about 150 au.  
  > "the envelope thickness is abruptly increased by a factor of 2 inward of it." (3.2 CCH)

## Claim tuples

- H: Is the IRE thickness changed near the centrifugal barrier? | E: CCH moment 0 and channel maps at ~0.2'' resolution | R: Thickness 40-60 au outside ~150 au, doubled inside | F: The IRE is broadened in front of the centrifugal barrier, consistent with gas stagnation | **supported**
- H: Does SO trace shocked gas at the centrifugal barrier and show lower rotation? | E: SO moment 0, PV diagram and RADEX temperatures | R: SO concentrated at the barrier; rotation slower than the IRE model; T ~194 K at 100 au | F: Angular momentum may be extracted by gas moving off the mid-plane, possibly linking the barrier to disk winds | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Absence of CCH inside the barrier is not due to self-absorption or dust opacity (opacity <0.1 at 100 au)  
  > "Hence, the absence of the CCH emission is not due to the high opacity of the dust continuum emission, either." (3.2 CCH)
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature has large errors and cannot be derived inside the barrier because of poor S/N  
  > "Unfortunately, the temperature cannot be derived there because of the poor S/N ratio" (3.3 SO)
- Caveat (inferred, ours): Temperatures from two SO lines carry huge uncertainties and assume a fixed density
- Caveat (inferred, ours): Wind-launching interpretation is speculative
- Caveat (inferred, ours): Models are not fitted quantitatively to the new data

## Reproducibility

- Data public (paper): Project code given in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following ALMA data:" (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Model parameters for IRE overlays
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data identified and key numbers given but imaging and model details are missing.
- Rediscovery candidate: no, Imaging recipe incomplete and model-dependent comparisons.

## Links

- Method: Sakai et al. 2014a (Cycle 0 observations and IRE ballistic model)
- Method: Oya et al. 2015 (IRE model)
- Companion: Ohashi et al. 2014 (C18O and SO ALMA observations of L1527)

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
 "codes_not_in_obscore": [
  "2013.0.00858.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00858.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 37,
  "rate": 0.569
 },
 "evidence_ok": true
}
```
