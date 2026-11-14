# The ALMA early science view of FUor/EXor objects - I. Through the looking-glass of V2775 Ori

`2017MNRAS.465..834Z` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Zurlo, Alice | arXiv: 1611.00765 | DOI: 10.1093/mnras/stw2845

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the disc and circumstellar outflow/envelope properties of the FUor V2775 Ori as seen in ALMA band 6 continuum and CO isotopologue lines?  
  > "we have observed the circumstellar environment of the star V2775 Ori." (abstract)
- Target **V2775 Ori**: coordinates RA 05h42m48.49s, Dec -8d16m34.72s (J2000)  
  > "at a distance of 414±7 pc (Menten et al. 2007)" (1 INTRODUCTION); "The center of the disc is found in the sky location α 2000 = 05 h 42 m 48 s .49" (3.1 Continuum emission); z/distance 414±7 pc  
  > "at a distance of 414±7 pc (Menten et al. 2007)" (1 INTRODUCTION); "The center of the disc is found in the sky location α 2000 = 05 h 42 m 48 s .49" (3.1 Continuum emission); distance from Menten et al. 2007  
  > "at a distance of 414±7 pc (Menten et al. 2007)" (1 INTRODUCTION); "The center of the disc is found in the sky location α 2000 = 05 h 42 m 48 s .49" (3.1 Continuum emission)

## Data provenance

- ALMA projects: 2013.1.00710.S
- bands: Band 6, Cycle 2  
  > "V2775 Ori has been observed three times with ALMA during Cycle-2 in band 6" (2.1 ALMA data)
- frequencies and spectral setup: Two 2 GHz continuum windows at 232.6 and 218.0 GHz plus three 59 MHz bands on 12CO, 13CO, C18O (2-1)  
  > "two spectral windows for the continuum, centered at 232.6 GHz and 218.0 GHz, 2 GHz wide, plus three narrow (59 MHz wide) bands" (2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 45 antennas (Dec/Apr), 35 antennas (Aug)  
  > "with 45 antennas" (2.1 ALMA data)
- configurations: _not stated_
- baselines: 14.6 to 348.5 m (Dec/Apr); 42-1574 m (Aug)  
  > "with baselines ranging from 14.6 to 348.5m" (2.1 ALMA data)
- angular resolution: ~0.25 arcsec (combined); ~0.8 arcsec for the two shorter-baseline epochs  
  > "The resolution of these datasets is ∼ 0.8 ′′ ." (2.1 ALMA data)
- max recoverable scale: 11.4 arcsec  
  > "the maximum recoverable scale of the emission is 11.4 ′′" (2.1 ALMA data)
- sensitivity: continuum rms 0.25 mJy/beam; line rms 15 mJy/beam km/s  
  > "0.25 mJy beam −1 and 15 mJy beam −1 km s −1, respectively." (2.1 ALMA data)
- time on source: _not stated_
- observing dates: 2014 Dec 12, 2015 Apr 5, 2015 Aug 30  
  > "The third and final observations were performed on August" (2.1 ALMA data)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.5380 GHz)
- Line: 13CO 2-1 (220.3987 GHz)
- Line: C18O 2-1 (219.5603 GHz)
- External data: Distance 414±7 pc  
  > "at a distance of 414±7 pc (Menten et al. 2007)" (1 INTRODUCTION) [from Menten et al. 2007]
- External data: 12CO/13CO abundance ratio of 62 and 12CO/H2 of 1e-4  
  > "a relative abundance between 12 CO and 13 CO of 62 (Langer & Penzias 1993)" (3.6 Outflow gas parameters) [from Langer & Penzias 1993]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v4.4  
  > "Common Astronomical Software Application (CASA v4.4)" (2.1 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede and J0423013  
  > "Ganymede and J0423013 were used as flux calibrators" (2.1 ALMA data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA, via pipeline using calibrated visibilities  
  > "were created with the pipeline using the calibrated visibilities and the CLEAN routine of CASA" (2.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in the visibility domain  
  > "Continuum subtraction was performed in the visibility domain." (2.1 ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Concatenated lower and higher resolution data from three epochs  
  > "First we concatenated the lower and higher resolutions data." (2.1 ALMA data)
- smoothing: _not stated_
- final beam: Continuum 0.25x0.17 arcsec PA -89.09; 12CO 0.35x0.27; 13CO 0.37x0.28; C18O 0.37x0.29  
  > "Major axis ( ′′ ) 0.25 0.35 0.37 0.37" (Table 1)
- final rms: continuum 0.25 mJy/beam; lines 15 mJy/beam km/s  
  > "The rms in the final continuum and line data are" (2.1 ALMA data)

### Inherited from earlier work

- Outflow column density, mass, momentum, energy formalism  
  > "we used the formalism presented in Perez et al. (2015)" (3.6 Outflow gas parameters) [from Perez et al. 2015]
- Disc gas mass lower limit from models  
  > "based on the models of Williams & Best (2014)" (3.5 Disc gas mass estimate) [from Williams & Best (2014)]
- More detailed continuum modelling  
  > "A more detailed analysis and modelling of the continuum can be found in Cieza et al. (2018)." (3.1 Continuum emission) [from Cieza et al. (2018)]

### Not stated but needed to reproduce (our reading)

- Robust/weighting, cell and image size, clean threshold and masks
- Line-free channels for continuum subtraction
- Whether pipeline calibration was standard; flux scale uncertainty
- Channel width of the final cubes and velocity ranges of moment integration beyond Table 2
- Region for outflow mass calculation and noise clipping
- Which phase calibrators applied to which epoch

## Analysis recipe

1. **Calibrate, combine and image**: Concatenate three epochs, image continuum and cubes with CLEAN, continuum subtraction in uv  
  > "The data from all three epochs were processed and combined" (2.1 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum disc size and inclination**: 2D Gaussian fit with IMFIT; inclination from aspect ratio assuming circular disc  
  > "we performed a gaussian 2-dimensional fit with the CASA routine IMFIT" (3.1 Continuum emission)
   - software: CASA imfit
   - assumption: Disc is circular  
  > "Assuming that the disc is circular" (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Line profiles and moment 0 maps**: Mean intensity in 19 arcsec circular region vs velocity; moment 0 for velocity ranges of blue, low-velocity, red components; systemic velocity from C18O Gaussian fit  
  > "We calculated the mean intensity of the molecular lines in a circular region centered on the continuum emission" (3.2 12CO moments)
   - parameter: channel width 0.25 km/s  
  > "The channel width used for this analysis is 0.25 km s −1" (3.2 12CO moments)
   - assumption: System velocity equals C18O velocity  
  > "We assume that the system velocity corresponds to the velocity of the C 18 O" (3.2 12CO moments)
   - fitting: Gaussian fit to C18O peak  
  > "This value has been obtained fitting a gaussian to the peak emission of the line." (3.2 12CO moments)
   - validation: _not stated_
4. **Disc gas mass lower limit**: C18O compact flux compared to Williams & Best (2014) models  
  > "We use this to estimate a lower limit to the disc gas mass of 3 M Jup based on the models of Williams & Best (2014)." (3.5 Disc gas mass estimate)
   - parameter: C18O flux 0.15 Jy km/s  
  > "The flux of this compact source is 0.15 Jy km s −1 ." (3.5 Disc gas mass estimate)
   - assumption: Dust temperature 20 K; kappa 2.2 cm2/g for dust mass  
  > "κ = 2.2 cm 2 g −1, and temperature, T dust = 20 K" (3.5 Disc gas mass estimate)
   - fitting: _not stated_
   - validation: _not stated_
5. **Outflow mass, momentum, energy**: Perez et al. (2015) formalism on 12CO and 13CO per channel, summed over velocity; lower limits (no optical depth correction)  
  > "The values presented are then lower limits of these quantities." (3.6 Outflow gas parameters)
   - parameter: Tex = 50 K, filling factor 1  
  > "has a value of T ex = 50 K in this analysis. The beam filling factor is assumed to be 1." (3.6 Outflow gas parameters)
   - assumption: 12CO/H2 = 1e-4, 12CO/13CO = 62  
  > "an abundance of the 12 CO relative to H 2 of 10 −4" (3.6 Outflow gas parameters)
   - fitting: _not stated_
   - validation: _not stated_
6. **Kinematic age of outflow**: Ring radius divided by highest velocity; geometric estimate from hourglass axis and opening angle  
  > "the kinetic age of the outflow would be less than ∼ 1600 yr" (3.6 Outflow gas parameters)
   - assumption: Constant velocity; axis normal to disc  
  > "assume that the axis of the hourglass is normal to the plane of the disc" (3.6 Outflow gas parameters)
   - fitting: _not stated_
   - validation: Compared with HL Tau and HBC 494 ages  
  > "the same order of magnitude is found for HL" (3.6 Outflow gas parameters)

## Software

- **CASA** 4.4: Data reduction, CLEAN imaging, IMFIT  
  > "Common Astronomical Software Application (CASA v4.4)" (2.1 ALMA data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum integrated flux | 106 | ±11 (Sec 3.1); ±2 (abstract) | mJy | 2 | an integrated flux is 106 ± 11 mJy |
| Continuum peak flux | 69 | ±0.43 | mJy/beam | 2 | a peak flux is 69 ± 0.43 |
| Disc inclination | 14.0 | +14.5/-7.0 (as printed) | deg | 2 | inclination of 14.0 |
| Systemic velocity | 3.1 | 0.3 | km/s | 3 | The velocity of the system is 3.1±0.3 km s −1 . |
| Disc gas mass lower limit | 3 | not stated | MJup | 4 | lower limit to the disc gas mass of 3 M Jup |
| Dust mass | 1.6e-3 | not stated | Msun | 4 | The dust mass is estimated to be ∼ 1.6 × 10 −3 M ⊙ |
| Total 12CO outflow mass | 12.3e-3 | not stated | Msun | 5 | Total 9.0 12.3 60.0 310 |
| Kinetic age of outflow | <1600 | not stated | yr | 6 | the kinetic age of the outflow would be less than ∼ 1600 yr |
| Blue/red expansion velocities (12CO) | -2.85 / 4.4 | not stated | km/s | 3 | R 6 ∼ 16 7.5 11.65 4.4 |

## Qualitative findings

- 12CO and 13CO show a blue-shifted shell and red-shifted ring consistent with remnant cavities of an ancient outflow seen along the line of sight; C18O is very weak.  
  > "We interpret the shapes that the gas traces as cavities excavated by an ancient outflow." (abstract)

## Claim tuples

- H: Does V2775 Ori host a resolved disc seen nearly face-on? | E: 2D Gaussian fit to band 6 continuum | R: Deconvolved size ~151x146 mas; inclination ~14 deg | F: Disc marginally resolved, nearly face-on | **supported**
- H: What is the origin of the CO structures? | E: Moment maps of 12CO and 13CO in velocity ranges | R: Shell and ring, no hourglass walls | F: Fossil cavities from an earlier outflow | **partially**
- H: How massive is the disc gas? | E: C18O flux with Williams & Best models | R: Lower limit 3 MJup, low gas-to-dust ratio | F: Gas depleted or CO chemically affected | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow quantities are lower limits because optical depth correction cannot be applied; face-on geometry makes age uncertain  
  > "As the disc is almost face-on, the uncertainties on these values are high." (3.6 Outflow gas parameters)
- Caveat (inferred, ours): Uncertainty on integrated flux inconsistent (±2 abstract vs ±11 text)
- Caveat (inferred, ours): Inclination from aspect ratio of a marginally resolved disc has large error
- Caveat (inferred, ours): Systemic velocity from faint C18O
- Caveat (inferred, ours): Assumed Tex, abundances not tested
- Caveat (inferred, ours): Continuum flux scale uncertainty not discussed

## Reproducibility

- Data public (paper): Project code given; ALMA archive data  
  > "ADS/JAO.ALMA#2013.1.00710.S" (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Imaging parameters (robust, cell, mask, threshold)
- Missing: Exact velocity ranges and regions for moment/mass calculation
- Missing: Line-free channels
- Data volume (inferred): ~50-100 GB raw for three EBs
- Score (inferred): 5/5, Public data and simple steps, but imaging parameters and details of mass calculation missing.
- Rediscovery candidate: no, Imaging recipe incomplete and several results depend on assumed parameters and external formalism.

## Links

- Method: Perez et al. 2015 (Outflow mass, momentum, energy formalism)
- Method: Williams & Best (2014) (Disc gas mass models)
- Companion: Cieza et al. (2018) (Detailed continuum modelling)
- Companion: Ruíz-Rodríguez et al. 2017a (HBC 494 from the same survey)
- Related: ALMA Orion FUor/EXor survey (2013.1.00710.S, PI Cieza)

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 44,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
