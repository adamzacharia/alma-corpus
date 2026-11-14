# High-mass Star Formation Triggered by Collision between CO Filaments in N159 West in the Large Magellanic Cloud

`2015ApJ...807L...4F` | The Astrophysical Journal Letters 2015 | first author: Fukui, Yasuo | arXiv: 1503.03540 | DOI: 10.1088/2041-8205/807/1/L4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies
- Question: Is high-mass star formation in N159 West (LMC) triggered by collision between CO filaments, and what is the filament and outflow structure at sub-pc scale?  
  > "we set up a hypothesis that the two filaments collided with each other" (abstract)
- Target **N159 West (N159W-N, N159W-S) in the LMC**: coordinates 5h39m35.34s, -69d45m33.2s (J2000, pointing center)  
  > "The observations centered at (α J2000.0, δ J2000.0 ) =" (2. Observations); "at a distance of 50 kpc (Schaefer 2008) and 61 kpc (Szewczyk et al. 2009)," (1. Introduction); z/distance 50 kpc (LMC)  
  > "The observations centered at (α J2000.0, δ J2000.0 ) =" (2. Observations); "at a distance of 50 kpc (Schaefer 2008) and 61 kpc (Szewczyk et al. 2009)," (1. Introduction); distance from Schaefer 2008  
  > "The observations centered at (α J2000.0, δ J2000.0 ) =" (2. Observations); "at a distance of 50 kpc (Schaefer 2008) and 61 kpc (Szewczyk et al. 2009)," (1. Introduction)

## Data provenance

- ALMA projects: 2012.1.00554.S
- bands: Band 3 (86–116 GHz) and Band 6 (211–275 GHz), Cycle 1  
  > "We carried out ALMA Cycle 1 Band 3 (86–116 GHz) and Band 6 (211–275 GHz)" (2. Observations)
- frequencies and spectral setup: Line windows 58.6 MHz (15.3 kHz x 3840 channels)  
  > "with a bandwidth of 58.6 MHz (15.3 kHz × 3840 channels)." (2. Observations)
- continuum bandwidth: 1875.0 MHz (488.3 kHz x 3840 channels)  
  > "a bandwidth of 1875.0 MHz (488.3 kHz × 3840 channels)." (2. Observations)
- arrays: 12m main array and ACA 7m  
  > "both with the main array 12m antennas and the Atacama Compact Array (ACA) 7m antennas." (2. Observations)
- configurations: _not stated_
- baselines: 12m: 16–395 m; ACA: 9–37 m  
  > "The projected baseline length of the 12m array ranges from 16 m to 395 m. The ACA covers 9 m to 37 m baselines." (2. Observations)
- angular resolution: ~2.5x1.8 arcsec (Band 3), ~1.3x0.8 arcsec (Band 6)  
  > "providing synthesized beam sizes" (2. Observations)
- max recoverable scale: _not stated_
- sensitivity: line rms ~40 mJy/beam (Band 3), ~20 mJy/beam (Band 6) in emission-free channels  
  > "are ∼40 mJy beam [−][1] and ∼20 mJy" (2. Observations)
- time on source: _not stated_
- observing dates: October 2013 to May 2014  
  > "were carried out between October 2013 to May 2014." (2. Observations)
- pi or archival as stated: _not stated_
- Line: 13CO J=2-1 (not stated)
- Line: 12CO J=2-1 (not stated)
- Line: CS J=2-1 (not stated)
- Other facility **Spitzer and Herschel**: YSO photometry/SED data (1.2–500 µm) and IRS spectra  
  > "we model all the available data including the Spitzer and Herschel fluxes (1.2–500 µm)" (3.3. YSO characteristics)
- External data: X(CO)=7e20 cm-2 conversion factor  
  > "X(CO)=7 × 10 [20] cm [−][2]" (3.1. A complex filamentary structure) [from Fukui et al. 2008]
- External data: Dust opacity 0.77 cm2/g at 1.2 mm and dust-to-gas ratio 3.5e-3  
  > "0.77 cm [2] g [−][1] and 3.5 × 10 [−][3], respectively" (3.1. A complex filamentary structure) [from Herrera et al. 2013]
- External data: 12CO(2-1)/(1-0) ratio 0.85  
  > "of 0.85 (the ratio in the Orion-KL region of Nishimura et al. 2015)" (3.1. A complex filamentary structure) [from Nishimura et al. 2015]
- Simulation/model as data: Robitaille et al. (2006, 2007) YSO model grid and SED fitter  
  > "Using the Robitaille et al. (2006, 2007) YSO model grid and spectral energy distribution (SED) fitter" (3.3. YSO characteristics)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: five solar system objects, Butler-JPL-Horizons 2012 model  
  > "we used the Butler-JPL-Horizons 2012 model" (2. Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for Band 3 and Band 6  
  > "We used the natural weighting for both the Band 3 and Band 6 data" (2. Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration
- Rest frequencies/spectral window assignments and velocity resolution of images
- Combination of 12m and ACA data and imaging parameters (cell, size, masks, deconvolver)
- Continuum subtraction and line-free channels
- Continuum flux/rms values and 5 sigma definition
- Outflow wing velocity ranges and how masses and timescales were derived
- Primary beam correction
- Which quasars were used for calibration

## Analysis recipe

1. **Image 13CO and Band 6 continuum and characterize filaments**: Velocity-integrated 13CO(2-1) image 234–240 km/s; filament width as full-width of emission at 3 sigma  
  > "defined as a full-width of the emission area at the 3σ level of the intensity integrated over" (3.1. A complex filamentary structure)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared ALMA cloud mass with single-dish; missing flux not significant  
  > "suggests that the missing flux of the present ALMA observation is not significant." (2. Observations)
2. **Estimate cloud and clump masses**: CO-based mass from 12CO(2-1) with X(CO); dust mass from Band 6 continuum  
  > "The cloud mass is estimated from the [12] CO(J=2–1) intensity by assuming a conversion" (3.1. A complex filamentary structure)
   - assumption: Dust temperature 20 K  
  > "by assuming the dust temperature 20 K." (3.1. A complex filamentary structure)
   - fitting: _not stated_
   - validation: CO and dust masses agree  
  > "as is consistent with the dust-emission estimate." (3.1. A complex filamentary structure)
3. **Identify outflows from 12CO high-velocity wings**: Integrate 12CO(2-1) red/blue wings and compare with continuum peak and YSOs  
  > "We have discovered two molecular outflows having velocity span of 10–20 km s [−][1]" (3.2. Outflows)
   - fitting: _not stated_
   - validation: Dynamical ages consistent with SED fitter ages  
  > "The dynamical ages of the two outflows are consistent with the ages output from the SED" (3.3. YSO characteristics)
4. **Derive YSO mass and luminosity from SED fitting**: Robitaille YSO model grid fit to Spitzer/Herschel/IRS data  
  > "Using the Robitaille et al. (2006, 2007) YSO model grid and spectral energy distribution (SED) fitter" (3.3. YSO characteristics)
   - software: Robitaille SED fitter
   - fitting: _not stated_
   - validation: Consistent with Chen et al. (2010)  
  > "These results are consistent with those from" (3.3. YSO characteristics)
5. **Estimate collision timescale and accretion rate**: Collision time = ~0.5 pc / 8 km/s; accretion rate = stellar mass / timescale  
  > "∼0.5 pc divided by 8 km s [−][1]," (4. Discussion on the high-mass star formation processes)
   - assumption: Velocity span 8 km/s taken as actual collision velocity, scaled from Inoue & Fukui (2013) simulations  
  > "We therefore assume the velocity span in N 159W-S, 8" (3.4. Filamentary collision in N159W-S)
   - fitting: _not stated_
   - validation: Consistent with Kudryavtseva et al. 2012 age spread  
  > "the present time-scale estimate is consistent with that of Kudryavtseva et al. (2012)." (4. Discussion on the high-mass star formation processes)

## Software

- **CASA** : Data reduction and imaging  
  > "The data were reduced using the Common Astronomy Software" (2. Observations)
- **Robitaille SED fitter** : YSO SED model fitting  
  > "Using the Robitaille et al. (2006, 2007) YSO model grid and spectral energy distribution (SED) fitter" (3.3. YSO characteristics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Filament molecular mass in N159W | 2.4e5 | not stated | Msun | 2 | the filaments have molecular mass of 2.4 × 10 [5] M ⊙ in |
| YSO-S mass | 37 | ±2 | Msun | 4 | 37 ± 2 M ⊙ and (2.0 ± 0.3) × 10 [5] L ⊙ for YSO-S |
| YSO-N mass | 31 | ±8 | Msun | 4 | 31 ± 8 M ⊙ and (1.4 ± 0.4) × 10 [5] L ⊙ for YSO-N |
| Average filament line-mass near N159W-S | 8.9e2 | not stated | Msun/pc | 2 | 8.9 × 10 [2] M ⊙ pc [−][1] |
| Collision timescale | ~6e4 | not stated | yr | 5 | i.e., ∼6 × 10 [4] years ago. |
| Mass accretion rate | ~6e-4 | not stated | Msun/yr | 5 | 37 M ⊙ /6 × 10 [4] yrs ∼6 × 10 [−][4] M ⊙ yr [−][1] |

## Qualitative findings

- Filaments 0.5–1.0 pc wide and 5–10 pc long; all known YSOs lie on filaments  
  > "All the known infrared YSOs are" (abstract)
- First discovery of protostellar outflows in external galaxies  
  > "This is the first discovery of protostellar out" (abstract)

## Claim tuples

- H: N159W-S high-mass star formation was triggered by collision of two filaments | E: 13CO(2-1) mapping, PV diagrams, and timescale estimates | R: Two filaments intersect at N159W-S with velocity span enhanced to 8 km/s; collision ~6e4 yr ago; accretion ~6e-4 Msun/yr | F: Filament collision plausibly triggered formation of a ~37 Msun star | **partially**
- H: Protostellar outflows exist toward high-mass YSOs in the LMC | E: 12CO(2-1) wing maps | R: Two outflows with velocity span 10–20 km/s, timescale ~1e4 yr | F: First extragalactic protostellar outflows | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: N159W-S chosen for simple morphology to allow unambiguous interpretation  
  > "because the simple morphology allows us to understand the" (3.4. Filamentary collision in N159W-S)
- How they decided it was enough: _not stated_
- Limitation (authors): Collision velocity is a lower limit due to projection; red lobe of N159W-N may be masked  
  > "The actual collision velocity should be higher than 2–3 km s [−][1] because of the projection effect." (3.4. Filamentary collision in N159W-S)
- Caveat (inferred, ours): Collision interpretation rests on a single source and an assumed velocity scaling
- Caveat (inferred, ours): Outflow properties poorly resolved (lobes smaller than beam)
- Caveat (inferred, ours): Timescale from 0.5 pc / 8 km/s is crude
- Caveat (inferred, ours): No uncertainties on masses or timescales

## Reproducibility

- Data public (paper): Project code given in acknowledgments; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00554.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Outflow velocity ranges and mass calculations
- Missing: Details of SED data and fitting inputs
- Data volume (inferred): ~100–300 GB for 12m+ACA Band 3 and 6
- Score (inferred): 3/5, Data identifiable and key numbers given, but processing and imaging parameters sparse (Letter format).
- Rediscovery candidate: no, Imaging recipe incomplete and key results rely on interpretation.

## Links

- Method: Inoue & Fukui 2013 (MHD simulations of colliding flows used to scale collision velocity)
- Companion: Carlson et al. 2015 in preparation (HST near-IR image of the filament extension)
- Related: NANTEN LMC CO survey
- Related: Spitzer and Herschel LMC surveys

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 70,
  "stated": 38,
  "rate": 0.543
 },
 "evidence_ok": true
}
```
