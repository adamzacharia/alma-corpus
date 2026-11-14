# IRAS 16547-4247: A New Candidate of a Protocluster Unveiled with ALMA

`2015ApJ...798L..33H` | The Astrophysical Journal Letters 2015 | first author: Higuchi, Aya E. | arXiv: 1411.7485 | DOI: 10.1088/2041-8205/798/2/L33

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What are the spatial distribution and velocity structure of gas (outflows, shocked CH3OH) around the center of IRAS 16547-4247, and does the region host a protocluster?  
  > "The goal is to determine the spatial distribution and velocity structure of the gas around the center of IRAS 16547$-$4247" (INTRODUCTION)
- Target **IRAS 16547-4247**: coordinates core-A peak: 16h58m17.217s, -42d52m07.47s (J2000)  
  > "located at a distance of $\sim$2.9 kpc (cite: rod08)" (INTRODUCTION); "The peak position of core-A, ($\alpha_{J2000}$, $\delta_{J2000}$)=16$^{\mbox h}$58$^{\mbox m}$17$^{\mbox s}.$217," (3.1 880 $\mu$m continuum emission); z/distance ~2.9 kpc  
  > "located at a distance of $\sim$2.9 kpc (cite: rod08)" (INTRODUCTION); "The peak position of core-A, ($\alpha_{J2000}$, $\delta_{J2000}$)=16$^{\mbox h}$58$^{\mbox m}$17$^{\mbox s}.$217," (3.1 880 $\mu$m continuum emission); distance from Rodríguez et al. 2008 (cite: rod08)  
  > "located at a distance of $\sim$2.9 kpc (cite: rod08)" (INTRODUCTION); "The peak position of core-A, ($\alpha_{J2000}$, $\delta_{J2000}$)=16$^{\mbox h}$58$^{\mbox m}$17$^{\mbox s}.$217," (3.1 880 $\mu$m continuum emission)

## Data provenance

- ALMA projects: 2011.0.00419.S
- bands: Band 7 (880 um)  
  > "during Early Science Cycle 0 in its extended configuration, using the band 7 receivers." (OBSERVATIONS)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m, 32 antennas, 4 executions  
  > "The observations were done in 4 executions with 32 12-m antennas at an angular resolution of $\sim$0.5$''$." (OBSERVATIONS)
- configurations: Cycle 0 extended configuration  
  > "during Early Science Cycle 0 in its extended configuration" (OBSERVATIONS)
- baselines: _not stated_
- angular resolution: ~0.5 arcsec  
  > "The observations were done in 4 executions with 32 12-m antennas at an angular resolution of $\sim$0.5$''$." (OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.796 GHz)
- Line: CH3OH vt=0, JK=7_0-6_0 A (338.409 GHz)
- Other facility **APEX**: Large-scale 12CO(3-2) outflow (previous study)  
  > "From Atacama Pathfinder Experiment (APEX) observations (angular resolution $\sim$ 20$''$)" (3.2.1)
- External data: H2O maser positions (g1, g2)  
  > "the positions of the H$_{2}$O (g1 and g2 in Figure [2](#fig2)(a)) and CH$_{3}$OH maser clusters" (3.2.1) [from Franco-Hernández et al. 2009 (cite: fra09)]
- External data: Class I CH3OH maser cluster positions  
  > "CH$_{3}$OH maser clusters (pink crosses in Figure [4](#fig4)) detected by (cite: fra09) and (cite: vor06), respectively." (3.2.1) [from Voronkov et al. 2006 (cite: vor06)]
- External data: Jet precession rate 0.08 deg/yr, jet velocity ~490 km/s, opening angle 15 deg  
  > "derived a precession rate, $\beta$, of 0$^{\circ}$.08 yr$^{-1}$" (4.2) [from Rodríguez et al. 2008 (cite: rod08)]
- External data: Dust mass opacity 1.8 cm2/g at 880 um  
  > "a dust mass opacity of $\kappa_{880\ensuremath{\mu}m}$=1.8 cm$^{2}$g$^{-1}$ (cite: oss94)" (3.1) [from Ossenkopf & Henning 1994 (cite: oss94)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 3.4  
  > "Data reduction was performed using version 3.4 of the Common Astronomy Software Applications package" (OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Amplitude calibration was done using Titan." (OBSERVATIONS)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, 0.44 km/s velocity interval  
  > "The CASA task $\it{CLEAN}$ was used to Fourier-transform the visibility data and deconvolve the dirty images, at an velocity interval of 0.44 km s$^{-1}$." (OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = +0.5, continuum and lines  
  > "Briggs weighting with a robust parameter of $+$0.5 was used in both continuum and line images." (OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum from all line-free channels  
  > "The continuum map was obtained from a combination of all the line-free channels." (OBSERVATIONS)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Spectral window setup and line-free channel ranges
- Cell size, image size, clean masks and thresholds
- Final synthesized beam and rms noise
- Bandpass/gain calibrator details beyond names; flux scale uncertainty
- Moment map clipping thresholds
- Polygon/area definition for cores A and B

## Analysis recipe

1. **Measure continuum cores**: Gaussian fit to 880 um continuum  
  > "By using the CASA task $\it{imfit}$, a Gaussian fit to the continuum emission was performed." (3.1)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: Core-A position compared with SMA 1.3 mm peak  
  > "agrees with the peak position derived from the SMA observations at 1.3 mm (cite: fra09)." (3.1)
2. **Estimate core H2 masses**: Optically thin dust emission mass  
  > "Assuming that the emission at 880 $\ensuremath{\mu}m$ corresponds to optically thin thermal dust emission" (3.1)
   - assumption: gas-to-dust 100, Td 100 K, kappa=1.8 cm2/g, d=2.9 kpc  
  > "a gas-to-dust ratio of 100, a dust temperature of 100 K (cite: guz14; san14)" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Map outflows and CH3OH shocks**: Velocity-integrated maps of blue/red 12CO wings; CH3OH moment 0, 1, 2 maps  
  > "we produced first and second moment maps (Figures [3](#fig3)(b) and [3](#fig3)(c), respectively)" (3.2.2)
   - software: CASA
   - parameter: Blue -70 to -45.8 km/s; red -15.9 to +8.8 km/s  
  > "blue-shifted (velocity range from $-$70 to $-$45.8 km s$^{-1}$) and red-shifted (velocity range from $-$15.9 to $+$8.8 km s$^{-1}$)" (3.2.1)
   - fitting: _not stated_
   - validation: Compared with maser positions  
  > "In addition, there is a good correlation between the spatial distribution of the CH$_{3}$OH(7–6) emission and the CH$_{3}$OH maser spots." (Shock-enhanced regions: CH3OH(7–6) line emission)
4. **Jet precession timescale**: Opening angle 45 deg minus jet 15 deg = 30 deg precession at literature rate  
  > "we estimated that it would take the collimated precessing jet about $\sim$ 380 yr to produce the observed morphology." (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4: Data reduction, CLEAN imaging, imfit  
  > "Data reduction was performed using version 3.4 of the Common Astronomy Software Applications package" (OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core-A peak flux density (880 um) | 420 | 30 | mJy/beam | 1 | 420$\pm$30 mJy beam$^{-1}$ for core-A |
| Core-B peak flux density | 100 | 10 | mJy/beam | 1 | 100$\pm$10 mJy beam$^{-1}$ for core-B |
| Core-A integrated flux | 2.2 | not stated | Jy | 1 | (integrated flux: 2.2 Jy) for core-A |
| Core-B integrated flux | 1.7 | not stated | Jy | 1 | (integrated flux: 1.7 Jy) for core-B |
| H2 mass core-A | 15 | not stated | Msun | 2 | of 15 $M_\odot$ for core-A and 12 $M_\odot$ for core-B |
| H2 mass core-B | 12 | not stated | Msun | 2 | of 15 $M_\odot$ for core-A and 12 $M_\odot$ for core-B |
| Precession timescale | ~380 | not stated | yr | 4 | it would take the collimated precessing jet about $\sim$ 380 yr to produce the observed morphology. |

## Qualitative findings

- Two bipolar 12CO outflows (NE-SW and NW-SE) misaligned with the large-scale APEX outflow  
  > "we identified two bipolar outflows, one aligned in the northeast-southwest direction" (3.2.1)
- CH3OH(7-6) traces an hourglass of post-shock gas  
  > "the CH$_{3}$OH(7–6) emission traces zones of post shocked gas produced by the interaction of multiple outflows" (3.2.2)

## Claim tuples

- H: Does the region contain multiple outflow driving sources? | E: ALMA 12CO(3-2) integrated wing maps at 0.5 arcsec | R: Two cross-aligned bipolar outflows | F: IRAS 16547-4247 is an early-phase protocluster candidate | **supported**
- H: What produces the CH3OH hourglass? | E: CH3OH moment maps compared with outflows and masers | R: Walls lie at outflow lobe edges, correlate with maser spots | F: Shocked gas from outflow interaction; precessing jet or multiple sources both possible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single precessing jet vs. multiple driving sources; not distinguished  
  > "we discuss two possible scenarios that may be responsible for the hourglass structure" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Higher resolution needed to identify driving sources  
  > "Higher angular resolution observations are required to identify the driving sources" (4.1)
- Caveat (inferred, ours): Mass estimates assume a single 100 K temperature and ignore optical depth
- Caveat (inferred, ours): No noise levels or beam sizes given
- Caveat (inferred, ours): Outflow separation is by-eye, with velocity ranges chosen subjectively
- Caveat (inferred, ours): Precession timescale relies on literature rates

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, thresholds)
- Missing: Line-free channel selection
- Missing: Moment map thresholds
- Missing: Calibration scripts
- Data volume (inferred): ~20-50 GB (Cycle 0 Band 7, 4 executions)
- Score (inferred): 3/5, Project code and key imaging choices given, but many details missing; results are few numbers and mostly qualitative.
- Rediscovery candidate: no, Main results are largely qualitative morphology and recipe is incomplete.

## Links

- Companion: Franco-Hernández et al. 2009 (cite: fra09) (SMA continuum and SO2 and H2O masers)
- Companion: Rodríguez et al. 2008 (cite: rod08) (VLA jet and precession)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 67,
  "stated": 31,
  "rate": 0.463
 },
 "evidence_ok": true
}
```
