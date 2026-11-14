# The ALMA early science view of FUor/EXor objects - II. The very wide outflow driven by HBC 494

`2017MNRAS.466.3519R` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Ruíz-Rodríguez, D. | arXiv: 1612.08799 | DOI: 10.1093/mnras/stw3378

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the structure, kinematics and mass of the outflow and envelope of the FU Ori-like object HBC 494, traced by 12CO, 13CO and C18O?  
  > "We use 12 CO, 13 CO and C 18 O spectral line data to independently describe the outflow and envelope structures associated with HBC 494." (abstract)
- Target **HBC 494**: coordinates 05h40m27.45s +07d27m29.65s (as printed)  
  > "ALMA observations for HBC 494, located at 05 h 40 s 27.45 s 07 o 27 ′ 29.65 ′′" (2 OBSERVATIONS); "located in the Orion molecular cloud, which has an estimated distance of 414 ±7 pc (Menten et al. 2007)" (1 INTRODUCTION); z/distance 414 ± 7 pc  
  > "ALMA observations for HBC 494, located at 05 h 40 s 27.45 s 07 o 27 ′ 29.65 ′′" (2 OBSERVATIONS); "located in the Orion molecular cloud, which has an estimated distance of 414 ±7 pc (Menten et al. 2007)" (1 INTRODUCTION); distance from Menten et al. 2007  
  > "ALMA observations for HBC 494, located at 05 h 40 s 27.45 s 07 o 27 ′ 29.65 ′′" (2 OBSERVATIONS); "located in the Orion molecular cloud, which has an estimated distance of 414 ±7 pc (Menten et al. 2007)" (1 INTRODUCTION)

## Data provenance

- ALMA projects: 2013.1.00710.S
- bands: Band 6 (230 GHz/1.3 mm)  
  > "Here, we present ALMA band-6 (230 GHz/1.3 mm) continuum and 12 CO, 13 CO and C 18 O J=2-1 line observations of HBC 494." (1 INTRODUCTION)
- frequencies and spectral setup: 12CO, 13CO, C18O J=2-1; resolution 0.04 km/s (12CO), 0.08 km/s (13CO, C18O)  
  > "The correlator was configured to provide a spectral resolution of 0.04 km s −1 for 12 CO and of 0.08 km s −1 for 13 CO and C 18 O." (2 OBSERVATIONS)
- continuum bandwidth: 3.9 GHz  
  > "The total bandwidth available for continuum observa tions was 3.9 GHz." (2 OBSERVATIONS)
- arrays: _not stated_
- configurations: C34-2/1, C34/2 and C34-7/6  
  > "using 37 and 39 antennas on the C34-2/1 and C34/2 configurations, respectively." (2 OBSERVATIONS); "HBC 494 was observed with 35 antennas in the C34-7/6 configuration" (2 OBSERVATIONS)
- baselines: 14 m to 350 m (first two nights); 42 m to 1.5 km (third night)  
  > "with the shortest baseline of ∼ 14 m and longest of ∼ 350 m." (2 OBSERVATIONS); "with baselines ranging from 42 m to 1.5 km" (2 OBSERVATIONS)
- angular resolution: _not stated_
- max recoverable scale: 11 arcsec  
  > "The maximum resolvable angle is 11 arc sec." (2 OBSERVATIONS)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014 Dec 12, 2015 Apr 15, 2015 Aug 30  
  > "The first two nights are December 12 th, 2014 and April 15 th, 2015" (2 OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5380 GHz)
- Line: 13CO J=2-1 (220.3987 GHz)
- Line: C18O J=2-1 (219.5603 GHz)
- Other facility **2MASS**: H-band image used for overlay of outflow contours  
  > "an image of the Re50N nebula taken as part of The Two Micron All Sky Survey (Skrutskie et al. 2006) in H band (1.6 µm)" (4.1 The Wide Angle Outflow)
- External data: Disc inclination ~70.2±2.5 deg, flux density 113±2.5 mJy, disc mass 0.2 Msun  
  > "Cieza et al. (Prep) found a very high inclina ◦ tion ( i ) of ∼ 70.2 ± 2.5" (1 INTRODUCTION) [from Cieza et al. (Prep)]
- External data: 12CO/13CO abundance ratio of 62  
  > "is taken as 62" (3.4 Outflow Masses and Kinematics) [from Langer & Penzias 1993]
- External data: CO abundance relative to H2 of 1e-4  
  > "X co = 10 −4, which is the abundance of CO relative to H 2 taken from Frerking et al. (1982)" (3.4 Outflow Masses and Kinematics) [from Frerking et al. (1982)]

## Processing

### Calibration

- pipeline or manual: Edited, calibrated and imaged in CASA; manual vs pipeline not stated  
  > "The visibility data were edited, calibrated and imaged in CASA v4.4 (McMullin et al. 2007)." (2 OBSERVATIONS)
- casa version: CASA v4.4  
  > "calibrated and imaged in CASA v4.4 (McMullin et al. 2007)" (2 OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013 and Ganymede  
  > "J0423-013 and Ganymede were used as Flux calibrators" (2 OBSERVATIONS)
- flux scale uncertainty: 10%  
  > "The uncertainty for calibrated flux is estimated to be 10 %." (2 OBSERVATIONS)
- self calibration: _not stated_

### Imaging

- task: CLEAN algorithm  
  > "We used the CLEAN algorithm to image the data" (2 OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0  
  > "using a robust parameter equal to zero, a briggs weighting was performed" (2 OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: All three nights concatenated and processed together  
  > "The observations from all three nights were concatenated and processed together to increase the signal to noise" (2 OBSERVATIONS)
- smoothing: _not stated_
- final beam: 12CO 0.35x0.27 arcsec PA -90; 13CO 0.37x0.28 PA 86.5; C18O 0.37x0.29 PA 87; continuum 0.25x0.17 PA -85.5  
  > "0.35 [′′] × 0.27 [′′] with P.A. = -90 for" (2 OBSERVATIONS)
- final rms: _not stated_

### Inherited from earlier work

- Optical-depth correction method for outflow mass, momentum and energy  
  > "we corrected our molecular line data following standard methods such as those found in Arce & Goodman (2001), Curtis et al. (2010) and Dunham et al. (2014)" (3.4 Outflow Masses and Kinematics) [from Arce & Goodman (2001), Curtis et al. (2010), Dunham et al. (2014)]
- Column density and mass calculation details  
  > "The interested reader can find a detailed description available in Appendix C of Dunham et al. (2014)." (3.4 Outflow Masses and Kinematics) [from Dunham et al. (2014)]
- Continuum disc properties and asymmetry  
  > "a more detailed description and analysis can be found in Cieza et al. (Prep)" (1 INTRODUCTION) [from Cieza et al. (Prep)]

### Not stated but needed to reproduce (our reading)

- Whether calibration used the ALMA pipeline or manual scripts, and the pipeline version
- Continuum channel selection and line-free channels used for continuum subtraction
- Cell size, image size, clean masks, thresholds and deconvolver
- Channel width and smoothing used for 12CO and 13CO cubes (only C18O 0.25 km/s given)
- Primary beam correction details
- Explicit formulas and the 3sigma/5sigma noise reference for the mass calculation
- Inclination correction (values not corrected for inclination)
- Which ALMA execution blocks were used and their calibrator assignments per night

## Analysis recipe

1. **Image continuum and CO cubes**: Concatenate three nights, CLEAN with Briggs robust 0  
  > "The observations from all three nights were concatenated and processed together to increase the signal to noise" (2 OBSERVATIONS)
   - software: CASA
   - parameter: robust = 0  
  > "using a robust parameter equal to zero, a briggs weighting was performed" (2 OBSERVATIONS)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps, PV diagram and spectra**: Integrate channels over chosen velocity ranges for moment 0/1; PV cut at PA ~50 deg, width ~0.45 arcsec; integrate spectra over regions  
  > "the image- ◦
space PV diagram cut at a position angle of ∼ 50 and the averaging

′′
width is ∼ 0.45 ." (3.2.1 Position-Velocity Diagram)
   - parameter: 12CO blue -5.25 to 4.75 km/s, red 6.75 to 18 km/s  
  > "between -5.25 and 4.75 km s −1 for the blue-shifted region and between 6.75 and 18 km s −1 for the red-shifted emission" (3.1 12 CO Moment Maps)
   - fitting: Systemic velocity from C18O line centre  
  > "is centred at 4.60 ± 0.02 km s −1, which is taken as the systemic velocity" (3.5 Spectral Lines)
   - validation: _not stated_
3. **Derive 12CO optical-depth correction**: Ratio of 12CO to 13CO brightness temperatures per channel, T12/T13 = X(1-exp(-tau12))... with weighted mean; parabola fit extrapolated to channels without 13CO detection  
  > "To compute the [12] CO

10 _D. Ruíz-Rodríguez et al._


mass, we apply the correction factor to all the channels with [13] CO
detection above 5σ." (3.4 Outflow Masses and Kinematics)
   - parameter: T12/T13 = 0.2 + 0.23(v-vLSR)^2; chi2 = 0.4; channels above 3 sigma used in fit  
  > "Figure 10 shows the fit with a χ 2 of 0.4 as a solid green line" (3.4 Outflow Masses and Kinematics)
   - assumption: Identical beam-filling factors and same excitation temperature for both isotopes; 13CO optically thin at low velocities; [12CO]/[13CO]=62  
  > "assuming identical beam-filling factors and the same excitation temperature for both isotopes" (3.4 Outflow Masses and Kinematics)
   - fitting: Parabola fit to weighted mean ratios; last three points excluded  
  > "For this fit, we did not use the last three points, presented as the red dots, because at these velocities 12 CO starts becoming optically thin." (3.4 Outflow Masses and Kinematics)
   - validation: _not stated_
4. **Compute outflow and envelope mass, momentum, energy, luminosity, mass loss**: Optically thin LTE column density from pixels above 5 sigma, N(H2) with X_CO = 1e-4, summed over pixels and channels; central 1.5 arcsec masked; kinematic age ~5400 yr  
  > "we built a mask around HBC 494 of radius size ∼ 1.5 ”, where pixels inside this area were removed from the final analysis." (3.4 Outflow Masses and Kinematics)
   - parameter: Excitation temperatures 20 and 50 K  
  > "we adopted for this quantity, values of 20 and 50 K in our analysis." (3.4 Outflow Masses and Kinematics)
   - assumption: Optically thin, LTE, X_CO=1e-4; no inclination correction  
  > "we start from the assumption that the emission is optically thin and in Local Thermodynamic Equilibrium (LTE)" (3.4 Outflow Masses and Kinematics)
   - fitting: _not stated_
   - validation: Compared with previous outflow masses (Arce & Sargent 2006, Curtis et al. 2010, Dunham et al. 2014)  
  > "are on the order of outflows previously presented using a similar approach" (4.2 Role of Outflows in Star Formation)

## Software

- **CASA** v4.4: Calibration, editing and imaging of visibilities  
  > "The visibility data were edited, calibrated and imaged in CASA v4.4 (McMullin et al. 2007)." (2 OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO outflow opening angle | ~150 | not stated | deg | 2 | reach an apparent opening angle of ∼ 150 with an extension of at least 8000 au |
| Outflow position angle | ~145 | not stated | deg | 2 | compute the outflow position angle (PA) of ∼ 145 north through east. |
| Systemic velocity (C18O line centre) | 4.60 | 0.02 | km/s | 2 | is centred at 4.60 ± 0.02 km s −1, which is taken as the systemic velocity |
| C18O line FWHM | 0.84 | 0.04 | km/s | 2 | The observed C 18 O line has a FWHM of 0.84 ± 0.04 |
| 12CO integrated flux, Northern cavity | 39.65 | 0.09 | Jy km/s | 2 | At the Northern cavity the integrated flux is 39.65 ± 0.09 Jy km s −1 |
| 12CO integrated flux, Southern cavity | 93.32 | 0.12 | Jy km/s | 2 | at the Southern cavity a value of 93.32 ± 0.12 Jy km s −1 |
| Kinematic age | ~5400 | not stated | yr | 4 | we estimated a kinematic age for HBC 494 of ∼5400 years |
| Optical-depth corrected blue-shifted 12CO outflow mass (20 K) | 52.00e-2 | not stated | Msun | 4 | Mass (10 −2 M ⊙ ) 3.40 (52.00) 5.03 (77.00) 5.54 (50.00) 8.20 (74.00) |
| Estimated accretion rate | ~3e-5 | not stated | Msun/yr | 0 | then its accretion rate is ∼ 3x10 −5 M ⊙ y −1 |

## Qualitative findings

- 12CO shows the widest outflow cavities known for a Class I object; 13CO and C18O trace rotating, infalling envelope with a velocity gradient perpendicular to the outflow  
  > "The low-velocity blue- and red-shifted 13 CO and C 18 O emission trace the rotation and infall motion of the circumstellar envelope." (abstract)

## Claim tuples

- H: HBC 494 drives a very wide-angle outflow | E: 12CO moment maps | R: Opening angle ~150 deg, extension at least 8000 au | F: Widest cavities known in a Class I object, likely from wind-envelope interaction | **supported**
- H: 13CO and C18O trace infall and rotation of the envelope | E: Moment maps, PV diagram, spectra | R: Velocity gradient at PA ~50 deg, perpendicular to the outflow | F: Envelope is rotating and infalling | **supported**
- H: Optical depth correction significantly raises outflow properties | E: 13CO-based correction of 12CO | R: Properties increase by factor ~10-20; mass ~1e-1 Msun | F: Outflows are more massive and energetic than commonly reported, supporting wind-driven disc evolution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 12CO is optically thick so masses underestimated without optical depth correction  
  > "can be considerably underestimated if they are not corrected for optical depth effects" (3.4 Outflow Masses and Kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow property estimates are lower limits, affected by the 11 arcsec maximum recoverable scale, spatial filtering and incomplete field coverage  
  > "these property estimations are lower limits of the outflow because HBC 494 is not detected completely in the" (3.4 Outflow Masses and Kinematics)
- Caveat (inferred, ours): Excitation temperature only assumed (20, 50 K), driving large mass uncertainty
- Caveat (inferred, ours): Optical-depth correction extrapolated by a parabola and uncertainty not propagated
- Caveat (inferred, ours): No inclination correction applied to momentum and energy
- Caveat (inferred, ours): Missing short spacings affect 13CO and outflow fluxes
- Caveat (inferred, ours): Key continuum parameters rely on unpublished paper

## Reproducibility

- Data public (paper): Program code given; public status not explicitly stated  
  > "were taken under program 2013.1.00710.S during Cycle-2 phase and over three different nights." (2 OBSERVATIONS)
- Products in archive: _not stated_
- Missing: Calibration scripts
- Missing: Imaging parameters beyond robust
- Missing: Exact formulas and noise thresholds for mass calculation
- Data volume (inferred): ~50-100 GB raw for three execution blocks
- Score (inferred): 4/5, Data identified and main recipe sketched, but imaging and calibration details and exact computations are thin.
- Rediscovery candidate: no, Imaging and mass computation details are incomplete, although results are numeric.

## Links

- Method: Dunham et al. (2014) (Outflow mass and kinematics method with optical-depth correction)
- Method: Arce & Goodman (2001) (Optical depth correction)
- Method: Curtis et al. (2010) (Outflow property method)
- Companion: Cieza et al. (Prep) (Continuum analysis of HBC 494 from the same program)
- Companion: Ruíz-Rodríguez et al. (Sub) (V883 Ori outflow from the same program)
- Companion: Zurlo et al. (2017) (V2775 Ori from the same program)
- Related: ALMA program 2013.1.00710.S (FUor/EXor survey)

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 44,
  "rate": 0.62
 },
 "evidence_ok": true
}
```
