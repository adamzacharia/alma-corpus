# ALMA Detection of Bipolar Outflows: Evidence for Low-mass Star Formation within 1 pc of Sgr A*

`2017ApJ...850L..30Y` | The Astrophysical Journal Letters 2017 | first author: Yusef-Zadeh, F. | arXiv: 1711.10573 | DOI: 10.3847/2041-8213/aa96a2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, star_formation
- Question: Are there bipolar outflows, signatures of young protostars, within ~1 pc of Sgr A*, and what star formation rate do they imply?  
  > "Here, we report the discovery of a population of bipolar outflows, an unambiguous signature of young protostars within 0.8 parsec (pc) of Sgr A*." (1. Introduction)
- Target **Sgr A* inner parsec (bipolar sources BP1-BP11)**: coordinates Sgr A* at RA 17h45m40.038s, Dec -29d00m28.069s (J2000)  
  > "coinicide with the position of Sgr A* at α, δ ( J2000) = 17 h 45 m 40 s . 038 , − 29 ◦ 00 ′ 28 ′′ . 069." (Figure 1 caption); "equivalent to ∼ 1 . 2 × 10 [4] AU at the 8 kpc distance of the Galactic center." (2. Data Reduction and Results); z/distance 8 kpc  
  > "coinicide with the position of Sgr A* at α, δ ( J2000) = 17 h 45 m 40 s . 038 , − 29 ◦ 00 ′ 28 ′′ . 069." (Figure 1 caption); "equivalent to ∼ 1 . 2 × 10 [4] AU at the 8 kpc distance of the Galactic center." (2. Data Reduction and Results); distance from assumed Galactic center distance  
  > "coinicide with the position of Sgr A* at α, δ ( J2000) = 17 h 45 m 40 s . 038 , − 29 ◦ 00 ′ 28 ′′ . 069." (Figure 1 caption); "equivalent to ∼ 1 . 2 × 10 [4] AU at the 8 kpc distance of the Galactic center." (2. Data Reduction and Results)

## Data provenance

- ALMA projects: 2015.A.00021.S, 2011.0.00005.SV
- bands: Band 6  
  > "we used calibrated Band 6 archival data" (2. Data Reduction and Results)
- frequencies and spectral setup: 13CO(2-1) 220.398, H30alpha 231.901, SiO(5-4) 217.105 GHz; spectral resolutions 1.33 and 1.26 km/s  
  > "emission at 220.398, 231.901, 217.105 GHz respectively" (2. Data Reduction and Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.49" x 0.39" (robust 0.5) and 0.51" x 0.39" (robust 2)  
  > "giving spatial resolutions of 0 . 49 ′′ × 0 . 39 ′′ (PA=-68.9 ◦ ) and 0 . 51 ′′ × 0 . 39 ′′ (PA=-79.9 ◦ ), respectively." (2. Data Reduction and Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: July 12/13, 2016  
  > "observed on July 12/13, 2016." (2. Data Reduction and Results)
- pi or archival as stated: archival Cycle 3 data  
  > "we used calibrated Band 6 archival data" (2. Data Reduction and Results)
- Line: 13CO J=2-1 (220.398 GHz)
- Line: H30alpha RRL (231.901 GHz)
- Line: SiO 5-4 (217.105 GHz)
- Other facility **OVRO**: HCN (1-0) interferometric data  
  > "This data set is taken from interferometric observations (Owens Valley Radio Observatory)" (Figure 1 caption)
- Other facility **ALMA (Moser et al. 2017)**: CS (5-4) and SiO (6-5) data  
  > "taken from an ALMA observation (Moser et al. 2017)" (2. Data Reduction and Results)
- External data: HCN (1-0) data  
  > "archival and published HCN (1-0) (Christopher et al. 2005) data" (2. Data Reduction and Results) [from Christopher et al. 2005]
- External data: CS (5-4) map  
  > "taken from an ALMA observation (Moser et al. 2017)" (2. Data Reduction and Results) [from Moser et al. 2017]
- External data: 34 GHz continuum image  
  > "superimposed on a grayscale 34 GHz continuum image (Yusef-Zadeh et al. 2015a)" (2. Data Reduction and Results) [from Yusef-Zadeh et al. 2015a]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.2  
  > "using CASA version 4.7.2" (2. Data Reduction and Results)
- pipeline version: _not stated_
- archive products used as is: calibrated archival data used  
  > "we used calibrated Band 6 archival data" (2. Data Reduction and Results)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal with solints scan length, 30.25 s, integration time; then phase+amp at integration time; transferred to line spws  
  > "phase self-calibration solutions were derived and subsequently applied for three solution intervals: scan length, 30.25 seconds, and the integration time." (2. Data Reduction and Results)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 and 2  
  > "used Brigg’s weighting with robust parameters of 0.5 and 2" (2. Data Reduction and Results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed before transferring self-cal solutions to line spws  
  > "After continuum subtraction, these phase and amplitude solutions were transferred" (2. Data Reduction and Results)
- line free channels: _not stated_
- primary beam correction: applied in some figures, not others (e.g. Fig 1c not applied)  
  > "A primary beam correction has not been applied." (Figure 1 caption)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.49x0.39 (PA -68.9) and 0.51x0.39 (PA -79.9) arcsec  
  > "0 . 49 ′′ × 0 . 39 ′′ (PA=-68.9 ◦ )" (2. Data Reduction and Results)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Cell size and image size
- Cleaning threshold, mask and deconvolver
- Line-free channels for continuum subtraction
- Which robust value applies to which line (13CO vs H30alpha) and rms noise
- Velocity ranges used for lobe integration per source
- Details of mass, momentum rate and dynamical age calculation (abundance, inclination treatment, formulas)
- Spectral window combination for continuum
- Source identification criteria

## Analysis recipe

1. **Self-calibrate and image continuum and lines**: Phase then amp+phase self-cal on continuum, transferred to continuum-subtracted line windows; imaged with Briggs weighting  
  > "After all spectral windows were combined, phase self-calibration solutions were derived" (2. Data Reduction and Results)
   - software: CASA
   - parameter: robust 0.5 and 2; channel widths 1.33 and 1 km/s  
  > "We imaged the spectral line data cubes with channel widths of 1.33 and 1 km s − 1 , respectively." (2. Data Reduction and Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive outflow lobe masses and momentum rates**: 13CO lobe masses assuming optically thin LTE emission; inclination handled by assuming isotropic axis distribution  
  > "assuming that 13 CO emission is optically thin and is in LTE with T ∼ 100 − 300 K." (3. Discussion)
   - assumption: T ~100-300 K; isotropic outflow orientation; 8 kpc distance  
  > "assuming that the intrinsic distribution of outflow axis orientation in three dimensions is isotropic." (3. Discussion)
   - fitting: _not stated_
   - validation: compared with outflows in Galactic disk (Dunham et al. 2014)  
  > "consistent with young protostellar outflows found throughout the disk of the Galaxy (Dunham et al. 2014)." (3. Discussion)
3. **Estimate dynamical age and star formation rate**: Mean dynamical age of population with 95% CI; SFR from 11 YSOs formed in last 6500 yr with mean mass 0.3 Msun  
  > "The 11 detected low-mass YSOs formed within the last 6500 years imply a star formation rate ∼ 5 × 10 − 4 M ⊙ yr − 1 assuming a mean stellar mass of ∼ 0 . 3 M ⊙ ." (3. Discussion)
   - assumption: mean stellar mass ~0.3 Msun  
  > "assuming a mean stellar mass of ∼ 0 . 3 M ⊙ ." (3. Discussion)
   - fitting: _not stated_
   - validation: Kuiper's test on PA distribution shows no significance  
  > "Kuipers’s test applied to the distribution of PAs shows no statistical significance because of the small sample size." (3. Discussion)
4. **Estimate disk mass of BP1 continuum source**: Dust mass from 226 GHz flux  
  > "The disk mass, assuming a dust temperature of 50 K, and dust opacity κ ν = 0 . 068 cm [2] g − 1 is ∼ 0.05 M ⊙ ." (2. Data Reduction and Results)
   - assumption: Td = 50 K; kappa = 0.068 cm2/g  
  > "assuming a dust temperature of 50 K, and dust opacity κ ν = 0 . 068 cm [2] g − 1" (2. Data Reduction and Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: self-calibration and imaging  
  > "using CASA version 4.7.2" (2. Data Reduction and Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of bipolar outflows | 11 | not stated | dimensionless | 1 | We report the discovery of 11 bipolar outflows within a projected distance of 1pc from Sgr A* |
| Mean dynamical age | 6.5e3 | +8/-3.1 x10^3 (95% CI) | years | 3 | The mean dynamical age of the outflow population is estimated to be |
| Star formation rate | ~5e-4 | not stated | Msun/yr | 3 | imply a star formation rate ∼ 5 × 10 − 4 M ⊙ yr − 1 |
| BP1 lobe masses (NW, SE) | 0.19, 0.12 | not stated | Msun | 2 | The total mass swept up in the NW and SE lobes is estimated to be ∼ 0.19 and 0.12 M ⊙ , respectively. |
| BP1-226GHz flux density | 0.74 | 0.19 | mJy | 1 | between the two lobes at 0.74 ± 0 . 19 mJy |
| BP1 disk mass | ~0.05 | not stated | Msun | 4 | dust opacity κ ν = 0 . 068 cm [2] g − 1 is ∼ 0.05 M ⊙ . |

## Qualitative findings

- 13CO emission fills the interior of the molecular ring, contrary to the view of an empty cavity  
  > "It is clear that 13 CO emission fills the interior of the molecular ring" (2. Data Reduction and Results)
- Outflow axis anisotropy suggestive but not statistically significant  
  > "However, this anisotropy is not significant statistically." (3. Discussion)

## Claim tuples

- H: Is low-mass star formation occurring within ~1 pc of Sgr A*? | E: Searched ALMA 13CO, H30a, SiO cubes for bipolar lobes | R: 11 bipolar outflows found with masses and momentum rates like Galactic-disk protostellar outflows | F: Star formation is occurring close to Sgr A* despite tidal disruption | **supported**
- H: What SFR do the outflows imply? | E: Dynamical ages from isotropic inclination assumption | R: mean age 6.5e3 yr; SFR ~5e-4 Msun/yr | F: Low-mass star formation could contribute significantly to the central few pc stellar mass | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Evolved-star outflows rejected as generally isotropic or more extreme in velocity  
  > "Evolved stars also drive outflows, but they are generally isotropic" (2. Data Reduction and Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Interferometric data lack short spacings, filtering extended emission; absorption against continuum  
  > "suffer from the lack of short UV spacings, thus diffuse, extended and low density molecular emission is filtered out." (2. Data Reduction and Results)
- Caveat (inferred, ours): Inclination and LTE/optically thin assumptions are uncertain
- Caveat (inferred, ours): Small sample; possible contamination by gas colliding flows or evolved stars
- Caveat (inferred, ours): Low spectral resolution mixes lobes
- Caveat (inferred, ours): Few methodological details given

## Reproducibility

- Data public (paper): archival ALMA data used  
  > "we used calibrated Band 6 archival data" (2. Data Reduction and Results)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, threshold, masks)
- Missing: Mass/age computation details and abundances
- Missing: Source selection criteria and velocity integration ranges
- Data volume (inferred): ~50-200 GB
- Score (inferred): 3/5, Public data and some processing stated, but imaging and derivation details are missing.
- Rediscovery candidate: no, Recipe lacks key parameters and source identification is subjective.

## Links

- Companion: Moser et al. 2017 (CS (5-4) ALMA data of the same region)
- Companion: Yusef-Zadeh et al. 2015b (earlier SiO and YSO candidates near Sgr A*)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 37,
  "rate": 0.536
 },
 "evidence_ok": true
}
```
