# Methanol and its Relation to the Water Snowline in the Disk around the Young Outbursting Star V883 Ori

`2018ApJ...864L..23V` | The Astrophysical Journal Letters 2018 | first author: van 't Hoff, Merel L. R. | arXiv: 1808.08258 | DOI: 10.3847/2041-8213/aadb8a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry, star_formation
- Question: Is methanol in the V883 Ori disk thermally desorbed, and what does its distribution imply for the water snowline location?  
  > "Analysis of the methanol observations and comparison with earlier C$^{18}$O observations shows that the methanol is thermally desorbed and suggests that the water snowline can be as far out as $\sim100$ AU." (Introduction)
- Target **V883 Ori**: coordinates _not stated_; z/distance d ~ 400 pc  
  > "V883 Ori is a FU Orionis object in the Orion A L1641 molecular cloud ($d \sim 400$ pc; (cite: Kounkel2017))" (Introduction); distance from Kounkel et al. 2017  
  > "V883 Ori is a FU Orionis object in the Orion A L1641 molecular cloud ($d \sim 400$ pc; (cite: Kounkel2017))" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00041.S, 2013.1.00710.S
- bands: Band 7 (CH3OH); Band 6 (C18O)  
  > "V883 Ori was observed on 2016 September 6 and 2017 July 19 in Band 7" (Observations)
- frequencies and spectral setup: 937.5 MHz window (488 kHz) centered at 345.8 GHz contains methanol; continuum windows at 333 and 344 GHz  
  > "a 937.5 MHz spectral window (488 kHz $\approx$ 0.42 km s$^{-1}$ resolution) centered at 345.8 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 16.7 m to 3697 m  
  > "baselines between 16.7 m and 3697 m were covered" (Observations)
- angular resolution: 0.13'' x 0.14'' (Band 7); 0.23'' x 0.30'' (C18O)  
  > "This resulted in a synthesized beam size of $0.13\ensuremath{''} \times 0.14\ensuremath{''}$" (Observations)
- max recoverable scale: ~4'' for C18O; ~1.5'' for CH3OH  
  > "The largest angular scale (LAS) is $\sim4\ensuremath{''}$ ($\sim1650$ AU) for the C$^{18}$O observations and $\sim1.5\ensuremath{''}$ ($\sim600$ AU) for the CH$_3$OH observations." (3.3 Methanol outer radius)
- sensitivity: 21 mJy/beam per 0.5 km/s channel (Band 7); 9 mJy/beam (C18O)  
  > "a rms of 21 mJy beam$^{-1}$ per channel" (Observations)
- time on source: 54 seconds (Band 7)  
  > "The total on-source integration time was 54 seconds" (Observations)
- observing dates: 2016 September 6 and 2017 July 19  
  > "V883 Ori was observed on 2016 September 6 and 2017 July 19 in Band 7" (Observations)
- pi or archival as stated: _not stated_
- Line: CH3OH 5_4-6_3 A-/A+ (346.202719 / 346.204271 GHz)
- Line: CH3OH 16_1-15_2 A- (345.903916 GHz)
- Line: CH3OH 18_3-17_4 E2 (345.919260 GHz)
- Line: C18O 2-1 (219.560354 GHz)
- External data: Inclination 38 deg and position angle 32 deg used for deprojection  
  > "An inclination of $38^{\circ}$ and a position angle of $32^{\circ}$ east of north (cite: Cieza2016) are used for deprojection and azimuthally averaging." (3.3 Methanol outer radius) [from (cite: Cieza2016)]
- External data: Standard ISM 16O/18O ratio of 560  
  > "Assuming a standard interstellar medium (ISM) $^{16}$O/$^{18}$O ratio of 560 (cite: Wilson1994)" (3.2 Column density and excitation temperature) [from (cite: Wilson1994)]

## Processing

### Calibration

- pipeline or manual: Manual reduction by Dutch Allegro ARC Node  
  > "The data were reduced manually by the Dutch Allegro ARC Node to properly account for variation of quasar J0510+1800." (Observations)
- casa version: CASA 4.7.2  
  > "using version 4.7.2 of the Common Astronomy Software Application (CASA" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800, J0522-3627, J0750+1231  
  > "The absolute flux calibrators were J0510+1800, J0522-3627 and J0750+1231 for the respective executions" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only on continuum, applied to line data  
  > "phase-only self-calibration was performed on the continuum data" (Observations)

### Imaging

- task: CASA clean  
  > "using the CASA task *clean* with natural weighting and a velocity resolution of 0.5 km s$^{-1}$" (Observations)
- deconvolver: _not stated_
- weighting robust: natural  
  > "using the CASA task *clean* with natural weighting" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line data imaged after continuum subtraction  
  > "The line data was imaged after continuum subtraction" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.13'' x 0.14''  
  > "synthesized beam size of $0.13\ensuremath{''} \times 0.14\ensuremath{''}$" (Observations)
- final rms: 21 mJy/beam per channel  
  > "a rms of 21 mJy beam$^{-1}$ per channel" (Observations)

### Inherited from earlier work

- C18O data reduction  
  > "The C$^{18}$O data reduction is described by (cite: Cieza2016)." (Observations) [from (cite: Cieza2016)]
- Curve-of-growth outer radius method  
  > "We derive outer radii for the emission using a curve-of-growth method (cite: Tripathi2017; Ansdell2018)" (3.3 Methanol outer radius) [from (cite: Tripathi2017; Ansdell2018)]
- Keplerian mask for moment maps  
  > "only those pixels that are expected to emit for a Keplerian rotating disk are included (cite: Salinas2017; Loomis2018)" (3.1) [from (cite: Salinas2017; Loomis2018)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- Keplerian mask parameters (stellar mass, velocity range)
- Clean threshold, mask, cell and image size
- Flux-integration details and uncertainties for rotational diagram
- Partition function used
- Aperture center and exact self-cal solint

## Analysis recipe

1. **Image and detect lines**: Self-calibrate, continuum subtract, clean with natural weighting at 0.5 km/s  
  > "The line data was imaged after continuum subtraction, using the CASA task *clean* with natural weighting and a velocity resolution of 0.5 km s$^{-1}$." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps**: Moment zero maps with Keplerian mask, overlaid on C18O moment 1  
  > "These moment maps are constructed using a Keplerian mask to enhance the signal-to-noise" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Rotational diagram**: Linear fit to ln(N/g) vs Eup for fluxes in 0.6'' aperture or Keplerian mask  
  > "Fitting a linear function results in a rotation temperature of $104 \pm 8$ K when the flux is extracted within a 0.6$\ensuremath{''}$ aperture" (3.2)
   - assumption: Optically thin, LTE  
  > "If the emission is optically thin and in LTE, the rotational temperature equals the kinetic temperature of the gas." (3.2)
   - fitting: _not stated_
   - validation: Flux ratios consistent with optically thin LTE  
  > "The observed ratios of the integrated fluxes are consistent with optically thin emission based on a LTE calculation" (3.2)
4. **Outer radii**: Curve of growth to 90% of total flux on deprojected elliptical apertures  
  > "the flux is measured within successively larger photometric apertures until the measured flux is 90% of the total flux" (3.3)
   - assumption: i = 38 deg, PA = 32 deg  
  > "An inclination of $38^{\circ}$ and a position angle of $32^{\circ}$ east of north" (3.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: Self-calibration and imaging  
  > "using version 4.7.2 of the Common Astronomy Software Application (CASA" (Observations)
- **Splatalogue** : Line identification with JPL and CDMS  
  > "through Splatalogue[^1] we can assign transitions" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Trot (0.6'' aperture) | 104 | 8 | K | 3 | rotation temperature of $104 \pm 8$ K |
| Trot (Keplerian mask) | 92 | 6 | K | 3 | $T_{\rm{rot}} = 92 \pm 6$ K |
| CH3OH column density (0.6'' aperture) | 8.9e16 | 1.6e16 | cm-2 | 3 | $8.9 \pm 1.6 \times 10^{16}$ cm$^{-2}$ |
| CH3OH column density (Keplerian mask) | 1.4e17 | 0.2e17 | cm-2 | 3 | $1.4 \pm 0.2 \times 10^{17}$ cm$^{-2}$ |
| C18O outer radius | 361 | 23 | AU | 4 | 361 $\pm$ 23 |
| CH3OH outer radius (16_1-15_2) | 136 | 18 | AU | 4 | 136 $\pm$ 18 |
| CH3OH abundance | ~4e-7 | not stated | relative to H2 | 3 | we then derive a CH$_3$OH abundance of $\sim4 \times 10^{-7}$ with respect to H$_2$ |

## Qualitative findings

- CH3OH emission follows Keplerian rotation and is more compact than C18O  
  > "The CH$_3$OH emission is more compact than the C$^{18}$O emission" (3.1)

## Claim tuples

- H: Is the methanol thermally desorbed? | E: Rotational diagram and abundance comparison | R: Trot ~90-100 K, abundance ~4e-7 | F: Methanol is thermally desorbed | **supported**
- H: Does methanol trace the water snowline? | E: Compare CH3OH outer radii with 42 AU snowline | R: Rout 120-140 AU | F: Snowline may be as far as ~100 AU, depending on disk structure | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Emission from surface layers beyond the snowline with snowline at ~40 AU  
  > "It may thus be possible to see CH$_3$OH emission out to $\sim120-140$AU while the snowline is around 40 AU." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): A detailed physical model is required to derive the snowline location  
  > "a detailed physical model of the disk is required to derive the water snowline location from methanol emission" (4.1)
- Caveat (inferred, ours): Low S/N (~4-5) per channel
- Caveat (inferred, ours): Optical depth not constrained
- Caveat (inferred, ours): Snowline inference qualitative without modeling

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Exact imaging parameters and masks
- Missing: Keplerian mask parameters
- Missing: Flux extraction details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data identified, but processing details sparse.
- Rediscovery candidate: no, Recipe incomplete for exact reproduction and low S/N.

## Links

- Method: Tripathi et al. 2017; Ansdell et al. 2018 (Curve-of-growth outer radius)
- Companion: Cieza et al. 2016 (C18O data and snowline from continuum)
- Related: VANDAM Orion survey

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.1.00350.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 37,
  "rate": 0.552
 },
 "evidence_ok": true
}
```
