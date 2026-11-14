# Unveiling a magnetized jet from a low-mass protostar

`2018NatCo...9.4636L` | Nature Communications 2018 | first author: Lee, Chin-Fei | arXiv: - | DOI: 10.1038/s41467-018-07143-8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is a magnetic field present in the jet of a low-mass protostar (HH 211), as shown by Goldreich-Kylafis SiO line polarization, and what is its morphology?  
  > "our observations show convincingly the presence of magnetic field in a jet from a low-mass protostar." (abstract)
- Target **HH 211**: coordinates central source RA(J2000)=03h43m56.8053s, Dec=32d00m50.192s  
  > "The cross marks the position of the central driving source at α ð2000Þ ¼ 03 [h] 43 [m] 56: [s] 8053," (Fig. 1 caption); "HH 211 is a nearby jet in the Perseus molecular cloud at a distance recently updated to be ~321 ± 10 pc [18] ." (Introduction); z/distance ~321 ± 10 pc  
  > "The cross marks the position of the central driving source at α ð2000Þ ¼ 03 [h] 43 [m] 56: [s] 8053," (Fig. 1 caption); "HH 211 is a nearby jet in the Perseus molecular cloud at a distance recently updated to be ~321 ± 10 pc [18] ." (Introduction); distance from Ortiz-León et al. 2018 (GOBELINS), ref 18  
  > "The cross marks the position of the central driving source at α ð2000Þ ¼ 03 [h] 43 [m] 56: [s] 8053," (Fig. 1 caption); "HH 211 is a nearby jet in the Perseus molecular cloud at a distance recently updated to be ~321 ± 10 pc [18] ." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00017.S
- bands: Band 7 (~350 GHz)  
  > "Polarization observations of the HH 211 protostellar jet were carried out with ALMA in Band 7 at ~350 GHz in Cycle 4" (Methods)
- frequencies and spectral setup: Five spectral windows: SO, CO 3-2, SiO 8-7, HCO+ 4-3, continuum at 358 GHz; SiO 0.42 km/s per channel  
  > "The correlator was set up to have five spectral windows" (Methods); "The velocity resolution is 0.42 km s [−][1] per channel in SiO." (Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 43 antennas, C40-7  
  > "with 43 antennas in C40-7 configuration" (Methods)
- baselines: ~20–1500 m projected  
  > "The projected baselines are ~20–1500 m." (Methods)
- angular resolution: 0.21" x 0.14" (67 x 45 au)  
  > "in SiO J = 8–7 at 0ʺ.21 × 0ʺ.14 (67 a.u. × 45 a.u.) resolution" (Results)
- max recoverable scale: ~1.1"  
  > "The maximum recoverable scale is ~1ʺ.1." (Methods)
- sensitivity: ~2.73 mJy/beam (Stokes I), ~0.64 mJy/beam (Q, U) in SiO mean maps  
  > "The noise level is ~2.73 mJy per beam in the Stokes I map and ~0.64 mJy per beam in the Stokes Q and U maps for the SiO line." (Methods)
- time on source: ~77 min total, two executions  
  > "with a total time of ~77 min on the HH 211 jet." (Methods)
- observing dates: 10 October 2016 (two executions)  
  > "Two executions were carried αout ð2000 on Þ ¼10 03October [h] 43 [m] 56: [s] 2016,8053," (Methods)
- pi or archival as stated: _not stated_
- Line: SiO J = 8–7 (347.330631 GHz)
- External data: Jet volume density n_H2 ≳ 2.0e6 cm^-3, updated for new jet radius/distance  
  > "According to Lee et al. [35], the volume density in the jet n H 2 ≳ 2:0 ´ 10 [6] cm [�][3] (updated for the new jet radius because of new distance)" (Discussion) [from Lee et al. 2010 (ref 35)]
- External data: SiO velocity width Δv_los ~ 15 km/s (FWHM towards knot BK1)  
  > "Also from Figure 8a in Lee et al. [19], we have Δv los ~ 15 km s [−][1]" (Discussion) [from Lee et al. 2009 (ref 19)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7  
  > "The data were calibrated with the CASA package (versions 4.7)" (Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasar J0238+1636  
  > "with Quasar J0238 + 1636 as a flux calibrator" (Methods)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-calibration using Stokes I continuum towards central source  
  > "A phase-only self-calibration of the data was performed to improve the map fidelity using the continuum intensity (Stokes I) map towards the central source." (Methods)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 2  
  > "We used a robust factor of 2 for the visibility weighting to generate the SiO maps (including Stokes I, Q, and U parameters)" (Methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: not applied  
  > "No primary beam correction is applied to the maps here" (Methods)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.21" x 0.14"  
  > "The resolution is 0ʺ.21 × 0ʺ.14" (Figure 2 caption)
- final rms: _not stated_

### Inherited from earlier work

- Polarization imaging accuracy limit (<0.3% within inner 1/3 of primary beam) taken from ALMA Technical Handbook  
  > "According to ALMA Technical Handbook in Cycle 4, polarization imaging with accuracy better than 0.3% can be achieved within the inner 1/3 of the primary beam" (Methods) [from ALMA Technical Handbook Cycle 4]

### Not stated but needed to reproduce (our reading)

- CASA task parameters, cell size, image size, masking, cleaning threshold
- Polarization calibration details (leakage/angle calibration, how Q and U were derived)
- Velocity ranges for imaging and continuum-subtraction/line-free channels
- Polarization debiasing treatment
- Self-calibration solution interval
- Method of fitting subknot widths and angle dispersion Δφ

## Analysis recipe

1. **calibrate and image Stokes I, Q, U in SiO**: CASA calibration, phase-only self-cal on continuum, imaging with robust=2  
  > "A phase-only self-calibration of the data was performed to improve the map fidelity using the continuum intensity (Stokes I) map towards the central source." (Methods)
   - software: CASA
   - parameter: robust = 2; resolution ~0.2"  
  > "We used a robust factor of 2 for the visibility weighting to generate the SiO maps (including Stokes I, Q, and U parameters) at a resolution of ~0ʺ.2." (Methods)
   - fitting: _not stated_
   - validation: Polarization mapped reliably only within ~3" of the phase centre  
  > "we can only map the polarization of the jet reliably within ~3ʺ of the central source." (Methods)
2. **make velocity-averaged polarization maps**: Average over ~30 km/s for blue and red components; two ~14 km/s wide channels; P = sqrt(Q²+U²)/I; E vectors  
  > "Linear polarization
degree (fraction) is defined as P ¼ pQ [2] þ U [2] =I." (Methods)
   - parameter: blue −22 to 8 km/s; red 11 to 42 km/s  
  > "The blueshifted component (blue contours) is obtained by averaging the emission from −22 to 8 km s [−][1]" (Figure 2 caption)
   - fitting: _not stated_
   - validation: _not stated_
3. **estimate magnetic field strength in subknots**: Chandrasekhar-Fermi (Ostriker et al.) estimate from density, velocity dispersion, angle dispersion  
  > "the field strength in
the plane of the sky can be estimated with the following equation" (Discussion)
   - parameter: Δv_los ~ 15 km/s; Δφ ~ 30° ± 20°; n_H2 ≳ 2.0e6 cm^-3  
  > "From our observations, we have Δϕ ~ 30° ± 20°" (Discussion)
   - assumption: ρ = 1.4 n_H2 m_H2  
  > "thus ρ ¼ 1:4n H 2 m H 2 ≳ 9:3 ´ 10 [�][18] g cm [�][3] ." (Discussion)
   - fitting: _not stated_
   - validation: Compared with X-wind expected ≳6 mG  
  > "the estimated field strength from our observations is about 2.5 times as
high as the expected" (Discussion)

## Software

- **CASA** 4.7: data calibration (and imaging)  
  > "The data were calibrated with the CASA package (versions 4.7)" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SiO polarization degree in blueshifted jet | 1 to 2 (mean ~1.5) | not stated | percent | 2 | The polarization degree is about 1 to 2%, with a mean of ~1.5% |
| Polarized noise level (Stokes Q,U) | 0.64 | not stated | mJy/beam | 1 | ~0.64 mJy per beam in the Stokes Q and U maps |
| Magnetic field strength in plane of sky | ≳15 | +30/−6 | mG | 3 | B ≳ 15 [þ] � [30] 6 [mG.] |
| Magnetic pressure | ≳8.9e-6 | not stated | dyne cm^-2 | 3 | The resulting magnetic pressure will be B [2] /8π ≳
8.9 × 10 [−][6] dyne cm [−][2] . |
| Jet launching radius upper limit | ≲0.06 | not stated | au | 3 | the jet-launching radius is
estimated to be ≲0:06 a:u: [36] |

## Qualitative findings

- Polarization orientations are almost parallel to the jet axis; field could be toroidal (perpendicular), consistent with X-wind launching  
  > "Interestingly, all
the polarization orientations are almost parallel to the jet axis." (Results)

## Claim tuples

- H: Is SiO line polarization detectable in a low-mass protostellar jet? | E: ALMA Band 7 full-polarization SiO J=8-7 observations of HH 211 | R: Polarization detected at 4–7σ in subknots A and B, ~1.5% degree, parallel to jet axis | F: First convincing detection of SiO line polarization in a low-mass protostellar jet, implying a magnetic field | **supported**
- H: Is the field strong enough to collimate the jet if toroidal? | E: Chandrasekhar-Fermi field estimate and pressure comparison | R: B ≳ 15 mG; magnetic pressure exceeds thermal pressure | F: A toroidal field could confine the jet | **partially**

## Reasoning

- Why this data: SiO J=8-7 is brightest, optical depth near 1, optimal for GK effect  
  > "The SiO emission of
the jet is brightest at J = 8–7 transition." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Polarization cannot be mapped reliably beyond ~3"; redshifted component not detected; field ambiguity (poloidal vs toroidal) unresolved  
  > "Thus, deeper
observations are needed to detect SiO line polarization in the redshifted jet component." (Results)
- Caveat (inferred, ours): Single SiO line cannot break poloidal/toroidal ambiguity
- Caveat (inferred, ours): Δφ with large uncertainty; CF method assumptions (turbulence, density) uncertain
- Caveat (inferred, ours): Instrumental polarization and calibration details not shown
- Caveat (inferred, ours): No debiasing or leakage checks described

## Reproducibility

- Data public (paper): ALMA data cited as ADS/JAO.ALMA#2016.1.00017.S; supporting data on reasonable request  
  > "The data that support the plots within this paper and other findings of this study are
available from the corresponding author upon reasonable request." (Data availability)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, threshold)
- Missing: Polarization calibration specifics
- Missing: Method for Δφ determination
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Data are archival-type but imaging and polarization-processing details are sparse.
- Rediscovery candidate: no, Recipe incomplete for polarization processing, and main results rely on literature inputs.

## Links

- Companion: Lee et al. 2009 (ref 19) (Earlier SiO observations of HH 211 jet providing velocity widths and radius)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 36,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
