# ALMA Observations of the HH 46/47 Molecular Outflow

`2013ApJ...774...39A` | The Astrophysical Journal 2013 | first author: Arce, Héctor G. | arXiv: 1304.0674 | DOI: 10.1088/0004-637X/774/1/39

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What are the morphology, kinematics and entrainment mechanism of the HH 46/47 molecular outflow, as seen in high-resolution ALMA CO(1-0) data?  
  > "The morphology, kinematics and entrainment mechanism of the HH 46/47 molecular outflow were studied using new ALMA Cycle 0 observations." (abstract)
- Target **HH 46/47 outflow (driven by HH 47 IRS)**: coordinates mosaic center 08h25m41.5s, -51d00m47s (J2000)  
  > "centered on $08^h25^m41^s.5$, $-51\ensuremath{^\circ}00\ensuremath{'}47\ensuremath{''}$ (J2000)." (Observations); "located on the outskirts of the Gum Nebula at a distance of 450 pc" (Introduction); z/distance 450 pc  
  > "centered on $08^h25^m41^s.5$, $-51\ensuremath{^\circ}00\ensuremath{'}47\ensuremath{''}$ (J2000)." (Observations); "located on the outskirts of the Gum Nebula at a distance of 450 pc" (Introduction); distance from Schwartz77; Reipurth+00; Noriega-Crespo+04  
  > "centered on $08^h25^m41^s.5$, $-51\ensuremath{^\circ}00\ensuremath{'}47\ensuremath{''}$ (J2000)." (Observations); "located on the outskirts of the Gum Nebula at a distance of 450 pc" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00367.S
- bands: Band 3  
  > "The Band 3 data were obtained over eleven scheduling blocks" (Observations)
- frequencies and spectral setup: Three windows, 30.5 kHz resolution, 58.6 MHz bandwidth, centered at 115.27, 100.88 and 100.07 GHz; 0.08 km/s velocity resolution  
  > "three windows with the highest spectral resolution ($\delta\nu=30.5$ kHz), with a bandwidth of 58.6 MHz and centered at 115.27 GHz" (Observations)
- continuum bandwidth: 117.2 MHz  
  > "resulting in a bandwidth of 117.2 MHz" (Observations)
- arrays: _not stated_
- configurations: Cycle 0 compact configuration, 16-18 antennas  
  > "with 16 to 18 antennas in the (Cycle 0) compact configuration" (Observations)
- baselines: 12 to 277 m  
  > "consisting of projected baselines in the range of 12 to 277 m" (Observations)
- angular resolution: 3.2" x 2.4", PA 16.5 deg (CO cube)  
  > "synthesized beam for the $^{12}$CO(1–0) data cube is $3.2\ensuremath{''} \times 2.4\ensuremath{''}$" (Observations)
- max recoverable scale: not sensitive to structures ≳20"  
  > "the observations are not sensitive to large scale ($\gtrsim 20\ensuremath{''}$) structures" (Results)
- sensitivity: 25 mJy/beam at 0.5 km/s (CO); 0.33 mJy/beam continuum  
  > "the ($1 \sigma$) rms is 25 mJy beam$^{-1}$ in a (spectroscopically smoothed) map with a velocity resolution of 0.5 km s$^{-1}$" (Observations)
- time on source: _not stated_
- observing dates: 28 December 2011 to 25 January 2012  
  > "from 28 December 2011 to 25 January 2012" (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.27 GHz)
- External data: Dust opacity at 1.3 mm extrapolated to 3 mm (0.9 cm2/g)  
  > "by extrapolating the value of $\kappa$ at 1.3 mm obtained by (cite: OH94)" (Continuum Source) [from (cite: OH94)]
- External data: Jet mass loss rate 4e-7 Msun/yr  
  > "was estimated by (cite: Hartigan+94) to be about $4 \times 10^{-7}$ M$_{\ensuremath{\odot}}$ yr$^{-1}$" (Outflow Mass, Momentum and Energy) [from (cite: Hartigan+94)]
- External data: Dynamic age of 9000 yr for the parsec-scale HH flow  
  > "the dynamic age of the parsec-scale HH flow associated with HH 46/47, discovered by (cite: Stanke+99)" (Outflow Mass, Momentum and Energy) [from (cite: Stanke+99)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars; J0538-440 and 3c279 bandpass; J0845-5458 phase/gain  
  > "Flux calibration was carried out using observations of Mars, and J0538-440 and 3c279 were used as bandpass calibrators." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "The visibility data were edited, calibrated and imaged (using the CLEAN algorithm) in CASA" (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.5 arcsec  
  > "using 0.5$''$ cells and 1024 cells in each spacial dimension" (Observations)
- image size: 1024 cells per dimension  
  > "using 0.5$''$ cells and 1024 cells in each spacial dimension" (Observations)
- masking: different clean region per channel around brightest emission  
  > "we defined a different clean region for each channel, encircling the area with the brightest emission" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 3.1" x 2.2" (PA 15 deg)  
  > "The synthesized beam and rms for the continuum map are $3.1\ensuremath{''} \times 2.2\ensuremath{''}$ (PA$= 15\ensuremath{^\circ}$)" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Envelope mass method from continuum  
  > "we follow (cite: Schnee+10) and (cite: Dunham+12) to estimate the mass of the envelope using the dust continuum emission" (Continuum Source) [from (cite: Schnee+10); (cite: Dunham+12)]
- Outflow mass/momentum/energy method and CO abundance  
  > "We follow (cite: Bourke+97) to estimate the outflow properties from the CO(1–0) data" (Outflow Mass, Momentum and Energy) [from (cite: Bourke+97); abundance as in (cite: Olberg+92)]
- Wide-angle wind analytic model  
  > "We follow the simple analytical model by (cite: Lee+00) to describe the blue lobe of the HH 46/47 molecular outflow." (4.1) [from (cite: Lee+00)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration approach (manual vs pipeline)
- Clean threshold, weighting/robust, deconvolver and mosaic gridding details
- Flux scale uncertainty
- Cloud LSR velocity adopted for v_out (about 5 km/s)
- Line-free channels and continuum subtraction (none described)
- Primary beam correction
- Exact p-v cut widths and positions
- Method of fitting the parabola and p-v model

## Analysis recipe

1. **Image CO cube and continuum**: CLEAN in CASA of 29-pointing mosaic; per-channel clean regions; continuum from two line-free windows  
  > "The continuum was obtained by averaging the emission over all channels in the two windows close to 100 GHz with no detected line emission" (Observations)
   - software: CASA
   - parameter: 0.5" cells, 1024 pixels  
  > "using 0.5$''$ cells and 1024 cells in each spacial dimension" (Observations)
   - fitting: _not stated_
   - validation: Compared spectrum smoothed to 44" with Olberg et al. single-dish spectrum to assess recovered flux  
  > "the ALMA observations recover most (if not all) of the emission at LSR velocities greater than 6.5 km s$^{-1}$ and less than 3.5 km s$^{-1}$" (Line Data)
2. **Envelope mass from continuum**: Optically thin dust emission mass  
  > "assuming a dust temperature ($T_d$) of 30 K and gas-to-dust ratio of 100" (Continuum Source)
   - assumption: Td=30 K, gas-to-dust 100, kappa(3mm)=0.9 cm2/g, beta=1  
  > "We estimate the dust opacity ($\kappa$) at 3 mm to be 0.9 cm$^2$ g$^{-1}$" (Continuum Source)
   - fitting: Gaussian fit for continuum peak position  
  > "A Gaussian fit puts the continuum peak at" (Continuum Source)
   - validation: Variations of assumptions change mass by factor 2-3  
  > "Reasonable variations of these quantities lead to possible variations in the mass estimate by a factor of two to three." (Continuum Source)
3. **Outflow mass, momentum, energy**: Sum over channels with >3 sigma emission, optically thin CO, for Tex = 15, 50, 100 K, with and without inclination correction  
  > "over the velocity range where we detect outflow emission with intensity greater than $3\sigma$" (Outflow Mass, Momentum and Energy)
   - parameter: [12CO]/[H2]=1e-4; inclination 30 deg  
  > "assuming an abundance ratio of $[^{12}$CO$]/[$H$_2] = 10^{-4}$, as in (cite: Olberg+92)" (Outflow Mass, Momentum and Energy)
   - assumption: Optically thin; lower limits  
  > "Estimates are obtained assuming emission is optically thin. Values should be treated as lower limits." (Table 1)
   - fitting: _not stated_
   - validation: Using Olberg et al. Tex and velocity ranges gives 3.6e-2 Msun, similar to their 0.03 Msun  
  > "we obtain a total outflow mass of $3.6 \times 10^{-2}$ M$_{\ensuremath{\odot}}$, similar to the value of 0.03 M$_{\ensuremath{\odot}}$ obtained by Olberg et al." (Outflow Mass, Momentum and Energy)
4. **Fit blue lobe wide-angle wind model**: Fit parabola z=CR^2 to integrated map (-26 to -4 km/s, rotated -30 deg), and Hubble-law shell model to p-v diagram  
  > "We rotated the map by $-30\ensuremath{^\circ}$ and fit a parabola ($z = CR^2$) to the structure." (4.1)
   - parameter: i constrained to 30±10 deg; distance 450 pc  
  > "We constrain the inclination angle with respect to the plane of the sky ($i$) to $30 \pm 10\ensuremath{^\circ}$" (4.1)
   - fitting: Visual reasonable-fit ranges as errors  
  > "The errors indicate the range of values for which reasonable fits are attained" (4.1)
   - validation: Predicted shells compared to velocity-integrated maps  
  > "The model provides a reasonable match to the velocity range-integrated intensity maps" (4.1)
5. **Red clump ages and masses**: Clump distances and ages assuming constant 300 km/s jet velocity, i=30 deg; masses with Tex=50 K  
  > "we estimate that a major mass ejection event in HH 46/47 takes place approximately every 300 yr" (4.2)
   - assumption: v_jet = 300 km/s  
  > "Existing studies indicate that $\bar{v}_{jet} \sim 300$ km s$^{-1}$ for HH 46/47" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, editing and CLEAN imaging  
  > "The visibility data were edited, calibrated and imaged (using the CLEAN algorithm) in CASA" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak intensity at 100 GHz | 8.1 | not stated | mJy/beam | 1 | with a peak intensity of 8.1 mJy beam$^{-1}$ |
| Continuum total flux density | 14 | not stated | mJy | 1 | The total flux density is 14 mJy |
| Envelope total mass | 0.4 | factor 2-3 | Msun | 2 | we obtain a total (gas and dust) mass associated with the continuum emission of 0.4 M$_{\ensuremath{\odot}}$ |
| Red lobe momentum (Tex=50 K) | ~0.5 | not stated | Msun km/s | 3 | Assuming $T_{ex} = 50$ K, the momentum of the red lobe is $\sim 0.5$ M$_{\ensuremath{\odot}}$ km s$^{-1}$ |
| Parabola constant C | 0.3 | ±0.05 | arcsec^-1 | 4 | The fit gives a value for $C$ of $0.3\pm 0.05$ |
| v_o | 2.3 | ±0.2 | km/s/arcsec | 4 | We find that a value of $v_o = 2.3 \pm 0.2$ km s$^{-1}$ arcsec$^{-1}$ |
| Inclination from p-v fit | 29 | ±1 | deg | 4 | an value of $i = 29\ensuremath{^\circ} \pm 1\ensuremath{^\circ}$ result in a reasonable fit |
| Ejection timescale | ~300 | not stated | yr | 5 | a major mass ejection event in HH 46/47 takes place approximately every 300 yr |
| Clump masses R1, R2, R3 (Tex=50 K) | 2.1, 1.8, 0.7 | not stated | 1e-3 Msun | 5 | R1 / 42 / 0.1 / 360 / 2.1 |

## Qualitative findings

- Blue and red lobes differ strongly in size and morphology  
  > "The most striking aspect of this outflow is the clear difference in size and morphology between the two different lobes" (Line Data)
- Velocity gradients across the cavity are inconsistent with rotation  
  > "Yet, we are certain it is not consistent with outflow rotation." (Summary)

## Claim tuples

- H: Is the blue lobe entrained by a wide-angle wind? | E: Fit parabolic shell model to integrated map and p-v diagram | R: C=0.3±0.05, v_o=2.3±0.2, i=29±1 deg give reasonable fits | F: Blue lobe consistent with wide-angle wind entrainment, coexisting with a jet | **supported**
- H: Do the red clumps trace episodic ejections? | E: Clump spacing and p-v Hubble wedges | R: Three clumps at ~0.1 pc spacing with ages 360-945 yr | F: Bow-shock entrainment by episodes every few hundred years | **supported**
- H: Does higher sensitivity raise outflow energetics? | E: Measured mass, momentum, energy over >3σ velocity range | R: Emission to -30 and 40 km/s; higher momentum and energy than Olberg et al. | F: Outflows may be more energetic than previously thought | **supported**
- H: Does cavity velocity gradient indicate rotation? | E: Perpendicular p-v cuts | R: Velocity increases toward axis | F: Not rotation | **supported**

## Reasoning

- Why this data: High-resolution observations needed to study entrainment, wind and outflow properties  
  > "The high resolution data were obtained with the aim of studying the entrainment process, the underlying protostellar wind and the properties of the molecular outflow." (Introduction)
- Why this method: _not stated_
- Alternative: Jet precession alone cannot produce the wide cavity  
  > "It is therefore highly unlikely that precession of the jet alone could, by itself, produce the wide-angle cavity traced by the CO outflow." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Masses are lower limits (optically thin, Tex uncertain, missing large-scale flux)  
  > "We thus estimate the mass assuming the line is optically thin, and warn that our masses are very likely underestimated, by a factor of few or even as much as an order of magnitude" (Outflow Mass, Momentum and Energy)
- Caveat (inferred, ours): Tex range spans a factor of ~5 in mass/energy
- Caveat (inferred, ours): Fits judged by eye with no formal statistics
- Caveat (inferred, ours): Missing flux near cloud velocity; no short-spacing data
- Caveat (inferred, ours): Constant 300 km/s jet velocity assumed for clump ages

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00367.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Cloud velocity and p-v cut definitions
- Missing: Details of fitting procedure
- Data volume (inferred): ~50-100 GB raw for 11 execution blocks
- Score (inferred): 3/5, Data are archival-accessible and the mass computation is clear, but imaging parameters and fit procedures are sparse.
- Rediscovery candidate: no, Recipe lacks imaging and fitting details; the model fits are judged by eye.

## Links

- Method: (cite: Lee+00) (Wide-angle wind analytical model)
- Method: (cite: Bourke+97) (Outflow mass, momentum, energy calculation)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 75,
  "stated": 49,
  "rate": 0.653
 },
 "evidence_ok": true
}
```
