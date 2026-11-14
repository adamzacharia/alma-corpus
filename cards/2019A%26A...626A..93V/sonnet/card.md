# The ALMA-PILS survey: gas dynamics in IRAS 16293-2422 and the connection between its two protostars

`2019A&A...626A..93V` | Astronomy and Astrophysics 2019 | first author: van der Wiel, M. H. D. | arXiv: 1903.12606 | DOI: 10.1051/0004-6361/201833695

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: How do the two protostars A and B in IRAS 16293-2422 relate to each other, and what are the kinematics, density and outflow structure of the gas bridging them at 60 au to ~10^3 au scales?  
  > "We aim to study the relation and interplay between the two protostars A and B at spatial scales of 60 au up to ∼10 [3] au." (abstract)
- Target **IRAS 16293-2422 (sources A and B)**: coordinates A: 16h32m22.873s −24°28′36.54″; B: 16h32m22.6147s −24°28′32.566″ (J2000)  
  > "source B 16 [h] 32 [m] 22 [s] .6147 −24 [◦] 28 [′] 32 [′′] . 566" (Table 1); "we adopt a distance estimate of 120 pc based on extinction measurements and VLBI parallax measurements of two stars in the core of the complex (Loinard et al. 2008)." (1. Introduction); z/distance 120 pc  
  > "source B 16 [h] 32 [m] 22 [s] .6147 −24 [◦] 28 [′] 32 [′′] . 566" (Table 1); "we adopt a distance estimate of 120 pc based on extinction measurements and VLBI parallax measurements of two stars in the core of the complex (Loinard et al. 2008)." (1. Introduction); distance from Loinard et al. 2008 (extinction and VLBI parallax of two stars in the core of the complex)  
  > "source B 16 [h] 32 [m] 22 [s] .6147 −24 [◦] 28 [′] 32 [′′] . 566" (Table 1); "we adopt a distance estimate of 120 pc based on extinction measurements and VLBI parallax measurements of two stars in the core of the complex (Loinard et al. 2008)." (1. Introduction)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7  
  > "covering the uninterrupted spectral range 329–363 GHz (all in ALMA band 7) in spectral channels of 0.244 MHz in width." (2. Observations)
- frequencies and spectral setup: 329–363 GHz continuous, 0.244 MHz channels (cubes at 0.2 km/s resolution)  
  > "covering the uninterrupted spectral range 329–363 GHz (all in ALMA band 7) in spectral channels of 0.244 MHz in width." (2. Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m main array plus 7-m ACA  
  > "using both the main array of 12-m dishes and the shorter baselines available in the array of 7-m dishes in the Atacama Compact Array (ACA)." (2. Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5″ (60 au)  
  > "sampling the two binary components of IRAS 16293 and their surroundings with a synthesized beam FWHM of 0.5 [′′] ." (2. Observations)
- max recoverable scale: ~13″  
  > "the addition of ACA baselines ensures that large scale emission up to ∼13 [′′] is recovered." (2. Observations)
- sensitivity: ~8 mJy/beam/channel  
  > "roughly uniform at ∼8 mJy beam [−][1] channel [−][1] across the full spectral range" (2. Observations)
- time on source: _not stated_
- observing dates: June 2014 to May 2015  
  > "The PILS program was conducted with ALMA between June 2014 and May 2015" (2. Observations)
- pi or archival as stated: _not stated_
- Line: C17O J=3–2 (337.061 GHz)
- Line: 12C16O J=3–2 (345.796 GHz)
- Line: H13CN J=4–3 (345.33977 GHz)
- Line: o-H2CO 5(1,5)–4(1,4) (351.76864 GHz)
- Line: SiO J=8–7 (347.33058 GHz)
- Line: C34S J=7–6 (337.39646 GHz)
- Line: C2H N=4–3, J=7/2–5/2 (349.39997 GHz)
- External data: 3D dust filament/envelope model (Rotating Toroid model 1) with temperature structure and luminosities 18 and 3 Lsun for A and B  
  > "The fiducial model adopted in this paper is equivalent to ‘Rotating Toroid model 1’ in J2018." (4.1) [from Jacobsen et al. 2018 (cite: J2018)]
- External data: Systemic velocities of source A (+3.2) and B (+2.7 km/s)  
  > "For the systemic velocities of each of the protostars, we adopt the statistically averaged values based on the multiline analy" (3. Results) [from Jørgensen et al. 2011]
- External data: 16O/17O ratio of 2.005×10^3  
  > "Using a [16] O/ [17] O ratio [3] of 2.005×10 [3] (Wilson 1999)" (4.2) [from Wilson 1999]
- Simulation/model as data: LIME synthetic cubes of H2CO 5(1,5)-4(1,4) and H13CN 4-3 from the J2018 density/temperature model, with abundance jump freeze-out  
  > "is used to obtain synthetic line emission cubes of the H 2 CO 5 1,5 –4 1,4 and H [13] CN 4–3 gas line emission" (4.1)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Visibility phase self-calibration based on continuum  
  > "Self-calibration of the visibility phases was applied, based on the continuum signal." (2. Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m plus ACA data  
  > "the addition of ACA baselines ensures that large scale emission up to ∼13 [′′] is recovered." (2. Observations)
- smoothing: _not stated_
- final beam: 0.5″ circular  
  > "The circular synthesized beam of 0.5 [′′] in FWHM is indicated in the bottom right of all panels" (Figure 2 caption)
- final rms: _not stated_

### Inherited from earlier work

- Observing conditions, data characteristics and data processing strategy  
  > "We refer to Jørgensen et al. (2016) for additional details of observing conditions, data characteristics, and the data processing strategy." (2. Observations) [from Jørgensen et al. 2016]
- Model definition and radiative transfer approach  
  > "We refer to J2018 for further details of the model definition and the radiative transfer approach." (4.1) [from Jacobsen et al. 2018 (J2018)]

### Not stated but needed to reproduce (our reading)

- CASA version, pipeline details and imaging parameters (robust, deconvolver, masks), deferred to Jørgensen et al. 2016
- Continuum subtraction method and line-free channels
- Exact LIME settings (photon number, grid) and J2018 model files
- Source/disk mask sizes
- Flux calibration scale and uncertainty

## Analysis recipe

1. **Locate continuum peaks**: 2D Gaussian fits on PILS 0.826–0.912 mm continuum image  
  > "measured using two-dimensional Gaussian fits on the PILS 0.826–0.912 mm continuum image, are listed in Table 1." (3. Results)
   - fitting: _not stated_
   - validation: Consistent with Oya et al. 2018 peaks within 0.05″  
  > "consistent with the 1.15–1.30 mm continuum peak locations reported by Oya et al. (2018) to within 0.05 [′′]" (3. Results)
2. **Make velocity maps and channel maps**: Intensity-weighted mean velocity per pixel with disks masked, threshold 40 mJy/beam  
  > "weighted mean velocity for each pixel, excluding all flux density values below 40 mJy beam" (3. Results: observed dynamics and morphology)
   - software: CASA
   - parameter: Vlsr range [−4,+11] km/s (C2H: [−1,+7])  
  > "channels with _V_ lsr in the range [−4,+11] km s [−][1] (except for C 2 H, where we choose [−1,+7] km s [−][1]" (3. Results)
   - fitting: _not stated_
   - validation: Line contamination checked in spectra (Appendix A)  
  > "it is important to consider the effect of contamination of other species contributing to the observed signal of a selected tracer." (Appendix A)
3. **Radiative transfer model of the bridge**: LIME on J2018 static filament+envelope model, abundance jump freeze-out, convolved with 0.5″ beam in MIRIAD, compared to observed [+2,+4] km/s moment maps  
  > "After LIME produces a synthetic line emission cube, it is convolved with a 0.5 [′′] × 0.5 [′′] beam in the image analysis software package MIRIAD." (4.1)
   - software: LIME, MIRIAD
   - parameter: Doppler b = 1 km/s; 20 abundance values per molecule; depletion factor 100  
  > "Twenty different abundance values are run for each molecule in the range given in Table 3." (4.1)
   - assumption: Static velocity field; gas-to-dust 100; Ossenkopf & Henning dust opacities  
  > "Moreover, the canonical gas-to-dust mass ratio of 100 was used" (4.2)
   - fitting: Abundance is the only free parameter; no formal fit  
  > "The only free parameter is the molecular abundance." (4.1)
   - validation: Run without freeze-out to test cause of missing emission  
  > "which we confirm with a separate radiative transfer model run in which freeze-out is neglected completely" (4.1)
4. **Bridge mass and Ostriker stability**: RADEX non-LTE C17O column from mean 600 mJy/beam, convert to N(H2), mass in 200x600 au cylinder; compare with isothermal-cylinder M/L  
  > "use RADEX (Van der Tak et al. 2007) non-LTE radiative transfer calculations to convert to a C [17] O column density." (4.2)
   - software: RADEX
   - parameter: Tkin = 25, 30, 40 K; n(H2)=10^5 cm^-3  
  > "With _T_ kin =[25, 30, 40] K, we obtain a C [17] O column density of [6.2, 5.4, 4.8]×10 [15] cm [−][2]" (4.2)
   - assumption: CO/H2=1e-4, 16O/17O=2.005e3, mu=2.0, bridge width 200 au  
  > "Using a [16] O/ [17] O ratio [3] of 2.005×10 [3] (Wilson 1999) and CO/H 2 =10 [−][4]" (4.2)
   - fitting: _not stated_
   - validation: Compared with model-integrated mass of 0.055 Msun  
  > "integrating the mass of all dust and gas in the bridge component of the model described in Sect. 4.1 yields a tenfold higher total mass of 0.055 _M_ ⊙ ." (4.2)

## Software

- **LIME** : Line radiative transfer synthetic cubes  
  > "The line radiative transfer code LIME (Brinch & Hogerheijde 2010) is used to obtain synthetic line emission cubes" (4.1)
- **MIRIAD** : Convolving model cubes with beam  
  > "it is convolved with a 0.5 [′′] × 0.5 [′′] beam in the image analysis software package MIRIAD" (4.1)
- **RADEX** : C17O column density  
  > "use RADEX (Van der Tak et al. 2007) non-LTE radiative transfer calculations" (4.2)
- **CASA** : Data processing package  
  > "the CASA data processing package (McMullin et al. 2007)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Bridge density range | 4×10^4 to ~3×10^7 | not stated | cm^-3 | 3 | with an inferred density between 4×10 [4] cm [−][3] and ∼3×10 [7] cm [−][3] |
| C17O column density | 6.2, 5.4, 4.8 ×10^15 for Tkin 25, 30, 40 K | not stated | cm^-2 | 4 | we obtain a C [17] O column density of [6.2, 5.4, 4.8]×10 [15] cm [−][2] |
| Bridge mass from C17O | 0.0056, 0.0049, 0.0044 | not stated | Msun | 4 | [0.0056, 0.0049, 0.0044] _M_ ⊙ . |
| Stability threshold M/L per 600 au | 0.14, 0.17, 0.23 for 25, 30, 40 K | not stated | Msun | 4 | we arrive at a stability threshold of [0.14, 0.17, 0.23] _M_ ⊙ per 600 au |
| Model bridge mass | 0.055 | not stated | Msun | 3 | yields a tenfold higher total mass of 0.055 _M_ ⊙ . |
| Source A–B separation | 5.3″ = 636 au | not stated | arcsec / au | 0 | the angular distance of 5.3 [′′] between the two submillimeter sources A and B corresponds to a projected distance of 636 au. |

## Qualitative findings

- C17O traces a kinematically quiescent bridge cospatial with dust; other tracers follow outflows  
  > "The bridge is therefore kinematically quiescent, that is, we find no evidence that the bridge is part of an outflow motion nor that it is a rotating structure." (3. Results)
- A C2H-only straight filament crosses source B with flat kinematics  
  > "Its velocity structure is flat, restricted to _V_ lsr values between +2 and +4 km s [−][1]" (3. Results)

## Claim tuples

- H: Is the A–B bridge a quiescent structure unrelated to outflows? | E: Velocity maps of CO isotopologues and other tracers | R: C17O velocities within ±1 km/s of systemic across bridge | F: Bridge is kinematically quiescent, not a circumbinary disk segment | **supported**
- H: Is the bridge gravitationally stable against radial collapse? | E: RADEX-based mass vs Ostriker threshold | R: Mass 0.0044–0.0056 Msun (0.055 from model) below 0.14–0.23 Msun threshold | F: Bridge stable against radial collapse in its current state | **supported**
- H: Does the J2018 model explain high-density tracers in the bridge? | E: LIME models of H2CO and H13CN vs observations | R: Model matches C17O qualitatively but not H2CO/H13CN | F: Bridge density likely 4e4–3e7 cm^-3; H2CO/H13CN trace outflow-impacted gas | **partially**
- H: Is source B less evolved than A? | E: Compare outflow evidence, disk structure, chemistry | R: No unambiguous outflow from B; chemistry ambiguous | F: B is at same stage or less evolved than A | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Intensity ratio analysis across tracers refused because multiple partially resolved dynamical components make line emission origin uncertain  
  > "We therefore refrain from embarking on such an analysis." (4.1)
- Alternative: Bridge as circumbinary disk segment rejected; disk fragmentation disfavored in favor of turbulent fragmentation  
  > "we conclude that the formation of protostars A and B has probably occurred through turbulent fragmentation." (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Fiducial model not necessarily unique best fit; dust opacity, gas-to-dust ratio uncertainties could change density by 10–100  
  > "The fiducial model (RTM 1 from J2018) is not necessarily the only and best fit to the data." (4.1)
- Limitation (authors): Much C2H flux filtered out by interferometer  
  > "it is evident that the majority of C 2 H flux is filtered out in our interferometric ALMA observations" (5.4)
- Caveat (inferred, ours): Density range is indirect and relies on a non-fitted model and a critical-density argument
- Caveat (inferred, ours): Mass estimate depends on assumed n(H2), CO/H2 and Tkin
- Caveat (inferred, ours): Line contamination possible near sources
- Caveat (inferred, ours): Distance 120 pc versus newer measurements scales results

## Reproducibility

- Data public (paper): ALMA data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00278.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrated PILS cubes processing details (in Jørgensen et al. 2016)
- Missing: J2018 model files and LIME input
- Missing: Mask definitions
- Data volume (inferred): Large: full PILS band 7 12m+ACA cubes, likely hundreds of GB raw; selected line cubes a few GB
- Score (inferred): 3/5, Public data but processing and model deferred to earlier papers; analysis qualitative with few numeric results.
- Rediscovery candidate: no, Recipe depends on inherited processing and model; results mostly qualitative.

## Links

- Method: Jørgensen et al. 2016 (PILS data reduction and characteristics)
- Method: Jacobsen et al. 2018 (3D filament/envelope model)
- Companion: Calcutt et al. 2018 (PILS methyl cyanide emission peaks of A)
- Companion: Murillo et al. 2018 (C2H morphology in IRAS 16293)
- Related: ALMA PILS (Protostellar Interferometric Line Survey)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
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
  "facts": 75,
  "stated": 45,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
