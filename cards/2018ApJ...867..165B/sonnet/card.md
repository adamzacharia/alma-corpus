# Dense Molecular Filaments Feeding a Starburst: ALMA Maps of CO(3-2) in Henize 2-10

`2018ApJ...867..165B` | The Astrophysical Journal 2018 | first author: Beck, Sara C. | arXiv: 1809.01339 | DOI: 10.3847/1538-4357/aae481

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What are the distribution, excitation and kinematics of the warm dense molecular gas in the starburst dwarf galaxy He 2-10 at ~12 pc resolution, and how does it relate to the starburst?  
  > "We have obtained ALMA observations of He 2-10 at 0″.3 resolution in the CO(3-2) emission line at 345 GHz." (1. INTRODUCTION)
- Target **Henize 2-10 (He 2-10)**: coordinates pointing center 08:36:15.134, -26:24:33.768 (ICRS)  
  > "the pointing center was 08:36:15.134, -26;24;33.768 (all coordinates are ICRS)" (2. OBSERVATIONS); "He 2-10 (D= 9 Mpc; 1″=43 pc)" (1. INTRODUCTION); z/distance D = 9 Mpc; 1″ = 43 pc; systemic velocity 872 km/s  
  > "the pointing center was 08:36:15.134, -26;24;33.768 (all coordinates are ICRS)" (2. OBSERVATIONS); "He 2-10 (D= 9 Mpc; 1″=43 pc)" (1. INTRODUCTION); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00492.S
- bands: CO(3-2) at 345 GHz  
  > "in the CO(3-2) emission line at 345 GHz" (1. INTRODUCTION)
- frequencies and spectral setup: 4 spectral windows (one line, three continuum); 109 planes of 1.5 MHz (1.3 km/s)  
  > "Each cube has beam size 0″.3 × 0″.27 and 109 spectral planes, each 1.5 MHz wide (1.3 km s−1)." (2. OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-4  
  > "He 2-10 was observed with ALMA in the C40-4 array on 15 November 2016" (2. OBSERVATIONS)
- baselines: _not stated_
- angular resolution: 0.3″ × 0.27″ (~12 pc)  
  > "Each cube has beam size 0″.3 × 0″.27" (2. OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: ~2 mJy/beam rms in off-line channel  
  > "The r.m.s. noise in an off-line channel, off-source, was ∼ 2 mJy/beam." (2. OBSERVATIONS)
- time on source: _not stated_
- observing dates: 15 November 2016  
  > "He 2-10 was observed with ALMA in the C40-4 array on 15 November 2016" (2. OBSERVATIONS)
- pi or archival as stated: PI program (S. Beck)  
  > "in the program 2016.1.00492 (S. Beck, PI)" (2. OBSERVATIONS)
- Line: CO J=3-2 (345 GHz)
- Other facility **HST**: V-band (F555W) and F658W images from Hubble Legacy Archive  
  > "overlaid on an HST-WFC/ACS F555W image of He 2-10 from the Hubble Legacy Archive" (Figure 1 caption)
- Other facility **VLA**: 3.6 cm radio continuum from archive (project AJ314)  
  > "a 3.6 cm thermal radio continuum image from the VLA archive (project AJ314)" (3.1.2)
- Other facility **Chandra**: X-ray map (Kobulnicky & Martin 2010)  
  > "the adaptively smoothed Chandra map of the 0.3-6 keV emission from Kobulnicky & Martin (2010)" (Figure 8 caption)
- External data: CO(2-1) SMA map used for ratios and masses  
  > "the CO(2-1) map of Santangelo et al. (2009) from the Submillimeter Array had a 1″.9 × 1″.3 beam" (3.1.1) [from Santangelo et al. 2009]
- External data: Single dish CO(3-2) flux  
  > "Meier et al. (2001) found 16.6K ± 0.6 km s−1 in the central position of their 22″ beam" (2. OBSERVATIONS) [from Meier et al. (2001)]
- External data: Single dish CO(1-0) flux 165 ± 8 Jy km/s  
  > "The single dish CO(1-0) flux is 165 ± 8 Jy km s−1 (Kobulnicky et al. 1995)" (3.1.3) [from Kobulnicky et al. 1995]

## Processing

### Calibration

- pipeline or manual: calibrated in the ALMA pipeline  
  > "The data were calibrated and imaged in the pipeline and analyzed in CASA 4.7.0 and AIPS." (2. OBSERVATIONS)
- casa version: CASA 4.7.0  
  > "The data were calibrated and imaged in the pipeline and analyzed in CASA 4.7.0 and AIPS." (2. OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0538-4405 (flux), J0846-2607 (phase)  
  > "The flux and phase calibrators were J0538-4405 and J0846-2607" (2. OBSERVATIONS)
- flux scale uncertainty: 10%  
  > "dominated by the estimated 10% uncertainty in the absolute flux calibration" (2. OBSERVATIONS)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.053″ pixels  
  > "Pixels are 0.053″." (Appendix A)
- image size: _not stated_
- masking: MOM0 sums emission >±1.5σ; MOM1/MOM2 cutoff ±4σ in channel maps  
  > "The integrated intensity image (MOM0 map) was produced by summing all emission > ±1.5 σ in the channel maps." (2. OBSERVATIONS)
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted before imaging  
  > "Continuum was subtracted before imaging." (2. OBSERVATIONS)
- line free channels: _not stated_
- primary beam correction: applied; edge effects at diameter 18″ (PB 25″ FWHM)  
  > "edge affects become obvious at diameter 18″" (2. OBSERVATIONS)
- array combination: _not stated_
- smoothing: Hanning-smoothed channel maps, 2.6 km/s; also convolved to 1.9″ beam for comparison  
  > "The maps have been Hanning-smoothed in velocity giving a channel width of 2.6 km s−1." (Figure 10 caption)
- final beam: 0.3″ × 0.27″  
  > "The beam of the CO observations is 0″.3 × 0″.27." (Figure 1 caption)
- final rms: ~0.15 Jy km/s in MOM0 toward center  
  > "The rms in the MOM0 image is ∼ 0.15 Jy km s−1 toward the center of the image." (2. OBSERVATIONS)

### Inherited from earlier work

- Clump finding following cprops method  
  > "We ran the cprops code on our CO(3-2) image cube as described in Rosolowsky & Leroy (2006)" (Appendix A) [from Rosolowsky & Leroy (2006)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, deconvolver, cell size, mask) beyond pipeline
- Line-free channels used for continuum subtraction
- Exact flux calibrator flux density
- How the 1.9″ convolution and ratios in Table 1 were computed (peak fluxes, regions)
- Details of the energy and mass estimates for the outflow (geometry, assumptions)
- Shear and velocity-gradient measurement procedure
- HST astrometry registration details

## Analysis recipe

1. **Image and make moment maps**: Pipeline-calibrated, continuum-subtracted cubes; MOM0 summing emission >1.5σ, MOM1/MOM2 with 4σ cutoff  
  > "Intensity-weighted velocity (MOM1) and dispersion (MOM2) maps were produced using a cutoff of ±4 σ in the channel maps." (2. OBSERVATIONS)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: Compared total flux to single dish: 850 ± 100 vs 1000 ± 200 Jy km/s  
  > "the ALMA maps appear to detect most (>70%) of the CO(3–2) emission within the ALMA primary beam in He 2-10." (2. OBSERVATIONS)
2. **CO(3-2)/CO(2-1) ratios and excitation**: Convolve ALMA CO(3-2) to SMA CO(2-1) beam; compute R32 per GMA, LTE temperature, PDR Toolbox  
  > "applying the PDR Toolbox (Pound & Wolfire 2008) tells us that the line ratios of the east and north regions are consistent with gas of density" (3.1.1)
   - software: PDR Toolbox
   - assumption: PDR emission, optically thick gas  
  > "If we assume that the emission arises in PDRs (Hollenbach & Tielens 1999) and that the gas is optically thick" (3.1.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive molecular masses**: Scale CO(3-2) to CO(1-0) with flux ratio 6 and apply Xco  
  > "we adopt the CO(3-2)/CO(1-0) flux ratio of 6 and conversion factor of Xco = 4 × 1020 cm−2 (K km s−1)−1." (3.1.3)
   - assumption: CO(3-2)/CO(1-0) = 6; Xco = 4e20  
  > "we adopt the CO(3-2)/CO(1-0) flux ratio of 6 and conversion factor of Xco = 4 × 1020 cm−2 (K km s−1)−1." (3.1.3)
   - fitting: _not stated_
   - validation: Compared with Santangelo et al. mass from CO(2-1)  
  > "Santangelo et al. (2009) find a mass of ∼ 7 × 107 M⊙, based on lower resolution CO(2–1) maps" (4.2)
4. **Clump census**: cprops/cpropstoo on cube: 6σ in two consecutive channels, extended to 2σ; min area 25 pixels, min volume 32 pixels; detection on non-PB-corrected, measurement on PB-corrected image  
  > "Once a 6 σ detection is made in two consecutive channels, the surrounding emission is mapped down to a two-sigma detection limit in a minimum of two consecutive channels." (Appendix A)
   - software: cprops, cpropstoo
   - assumption: Brightness temperature ratio 0.82; cprops XCO 4.35e20  
  > "the default cprops XCO of 4.35 × 1020 cm−2 (K km/s)−1" (Appendix A)
   - fitting: _not stated_
   - validation: _not stated_
5. **Kinematics and outflow energy**: Inspect moment and channel maps for shear, gradients, dispersion; minimum outflow energy from mass and FWZI assuming expanding shell  
  > "If we assume that the gas is an expanding shell of material, a minimum energy of ≳ 1053 ergs is needed to produce the observed outflow" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: analysis of pipeline-calibrated data  
  > "The data were calibrated and imaged in the pipeline and analyzed in CASA 4.7.0 and AIPS." (2. OBSERVATIONS)
- **AIPS** : analysis  
  > "The data were calibrated and imaged in the pipeline and analyzed in CASA 4.7.0 and AIPS." (2. OBSERVATIONS)
- **cprops/cpropstoo** : clump identification  
  > "We ran the cprops code on our CO(3-2) image cube as described in Rosolowsky & Leroy (2006)" (Appendix A)
- **PDR Toolbox** : line ratio to density/G0  
  > "applying the PDR Toolbox (Pound & Wolfire 2008)" (3.1.1)
- **astropy** : listed in software statement  
  > "Software: astropy(AstropyCollaboration2013)" (Software list)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(3-2) flux in 15″ field | 850 | 100 | Jy km/s | 1 | The CO(3-2) flux summed over a 15″ field in the ALMA maps is 850 ± 100 Jy km s−1 |
| CO(3-2)/CO(1-0) flux ratio | 6.1 | 1 | dimensionless | 3 | we obtain a CO(3-2)/CO(1-0) flux ratio of 6.1 ± 1 |
| Total molecular gas mass, central 18″ | 1.2e8 | not stated | Msun | 3 | M H2 gas = 1.2 × 108 M⊙ for the central 18″ region including the starburst |
| R32 West Starburst | 2.7 | ~25% | dimensionless | 2 | West Starburst 55 20 2.7 > 100 |
| East filament shear across width | 20-40 (max ≈55) | not stated | km/s | 5 | its magnitude is 20-40 km s−1 across the filament’s 30 to 50 pc width, with a maximum of ≈ 55 km s−1 |
| Bird outflow mass | 0.3-1e7 | not stated | Msun | 5 | it involves between 0.3 − 1 × 107 M⊙ of molecular gas |
| Bird outflow minimum energy | >=1e53 | not stated | erg | 5 | a minimum energy of ≳ 1053 ergs is needed to produce the observed outflow |
| Number of CO clumps | 70 | not stated | clumps | 4 | This resulted in 70 total clumps. |
| Source C virial mass | 4e6 | not stated | Msun | 5 | has virial mass derived with an assumed ρ ∝ 1/r density distibution of ≈ 4 × 106 M⊙ |

## Qualitative findings

- CO(3-2) is in clumpy filaments with no preferred orientation, many along dust lanes  
  > "The CO(3-2) in He 2-10 is in clumps that form filamentary systems, and many of the filaments correlate with optical dust lanes." (5. DISCUSSION AND SUMMARY)
- No CO clump or unusual kinematics at the non-thermal radio source  
  > "There is no CO(3–2) clump coincident with the non-thermal radio source that has been suggested to be an AGN, nor unusual kinematics." (abstract)

## Claim tuples

- H: Do filaments feed the starburst? | E: Channel maps and velocity field of the West filament | R: Velocity gradient increasing toward western starburst | F: West filament is accelerating onto the embedded cluster | **supported**
- H: Is the East filament a tidal tail? | E: Moment 1 map along and across filament | R: Shear of 20-40 km/s across width, no gradient along length | F: Tidal tail identification questioned; shear unexplained | **partially**
- H: Is there a molecular outflow in the south? | E: Velocity dispersion map and channel maps of the Bird | R: σ up to 40 km/s, FWZI ~140 km/s | F: Molecular outflow with energy >=1e53 erg and no identified source | **supported**
- H: Does the non-thermal source sit on a CO clump (AGN?) | E: Compare CO map with VLA 3.6 cm | R: Source lies on a molecular spur with quiescent kinematics | F: May argue for SNR rather than AGN | **partially**

## Reasoning

- Why this data: Subarcsecond resolution needed to reach embedded cluster scales  
  > "they could not get down to the scale of the embedded clusters, which requires subarcsecond resolution." (1. INTRODUCTION)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO(3-2) excitation unconstrained, so masses uncertain and likely overestimated in the starburst  
  > "For the starburst region, these will likely be overestimates, perhaps significant, of the gas" (3.1.3)
- Caveat (inferred, ours): Masses depend on assumed R31=6 and Galactic Xco in a low-metallicity galaxy
- Caveat (inferred, ours): Qualitative kinematic claims without quantitative fitting
- Caveat (inferred, ours): Missing short spacing not assessed; only ~one pointing
- Caveat (inferred, ours): Outflow energy is a rough estimate

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "in the program 2016.1.00492 (S. Beck, PI)" (2. OBSERVATIONS)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Imaging parameters and channel selection
- Missing: Region definitions for flux and ratio measurements
- Missing: Outflow energy calculation details
- Data volume (inferred): ~10-50 GB raw single execution band 7
- Score (inferred): 3/5, Single dataset and standard steps, but many processing and measurement details not stated.
- Rediscovery candidate: no, Results are mostly qualitative or loosely specified; recipe incomplete.

## Links

- Method: Rosolowsky & Leroy (2006) (cprops clump finding)
- Companion: Consiglio et al. 2016, 2017 (similar CO studies of II Zw 40 and NGC 5253)
- Related: VLA project AJ314

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
  "facts": 77,
  "stated": 48,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
