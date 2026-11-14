# An ALMA 3 mm continuum census of Westerlund 1

`2018A&A...617A.137F` | Astronomy and Astrophysics 2018 | first author: Fenech, D. M. | arXiv: 1804.04675 | DOI: 10.1051/0004-6361/201832754

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, stellar_physics, milky_way_ism
- Question: Determine mass-loss rates and mm properties of the post-main-sequence massive stars (WR, OB super/hypergiants, cool hypergiants) in the cluster Westerlund 1 from a 3 mm ALMA continuum census  
  > "We aim to study the constituent stars of the Galactic cluster Westerlund 1 in order to determine mass-loss rates for the diverse post-main sequence population of massive stars." (abstract)
- Target **Westerlund 1 (Wd1)**: coordinates _not stated_; z/distance 5 kpc (adopted)  
  > "for the purpose of this paper we adopt a distance, d = 5 kpc to Wd1." (1. Introduction); distance from literature estimates between 4-5 kpc (Clark et al. 2005; Crowther et al. 2006a; Kothes & Dougherty 2007; others)  
  > "for the purpose of this paper we adopt a distance, d = 5 kpc to Wd1." (1. Introduction)

## Data provenance

- ALMA projects: 2013.1.00897.S
- bands: Band 3 (~100 GHz)  
  > "Atacama Large Millimetre Array (ALMA) Band 3 (100 GHz) continuum observations of Wd1 in 2015." (1. Introduction)
- frequencies and spectral setup: 4 spectral windows centred on 92.5, 97.5, 102.5 & 104.5 GHz; 128 channels of 15.625 MHz each (120 usable)  
  > "total usable bandwidth of 7.5 GHz over four spectral windows centred on 92.5, 97.5, 102.5 & 104.5 GHz respectively." (2.1 Observations and imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 40 to 1500 m, 42 antennas  
  > "The array consisted of 42 antennas with baselines ranging from 40 to 1500 m" (2.1 Observations and imaging)
- angular resolution: fitted beam 750×570 mas  
  > "The final image has a fitted beam of 750×570 mas." (2.1 Observations and imaging)
- max recoverable scale: _not stated_
- sensitivity: ~28 µJy/beam noise in central regions  
  > "The noise level in the central regions of the Westerlund 1 field is ∼28 µJy beam" (3.2 Mm sources lacking counterparts)
- time on source: 242.3 s per pointing, 27 pointings  
  > "a total on-source integration time per pointing of 242.3 secs (∼4 mins)." (2.1 Observations and imaging)
- observing dates: 30 June and 1 July 2015  
  > "ALMA was used to observe Wd1 on the 30th June and the 1st July 2015" (2.1 Observations and imaging)
- pi or archival as stated: _not stated_
- Other facility **ATCA 8.6 GHz radio (Do10)**: 3.6 cm flux densities for spectral indices; astrometric reference; contours  
  > "the absolute astrometry of the final images were checked utilising the 8.6 GHz radio image and the FORS R-band image" (2.1 Observations and imaging)
- Other facility **FORS R-band image**: optical image for astrometric alignment and overlay  
  > "ALMA 3-mm contours (from the non-PB corrected image) overlaid on a FORS R-band image" (Figure 2 caption)
- External data: 3.6 cm radio flux densities and limits used for spectral indices  
  > "3.6 cm flux densities and spectral indices taken from Do10 are also listed." (Table 2) [from Dougherty et al. 2010 (Do10)]
- External data: Teff and v_inf for B supergiants, WN and WC stars  
  > "we have adopted the (observational) compilations of Crowther et al. (2006b) and Searle et al. (2008) for B0-B5 supergiants; Crowther (2007) and Sander et al. (2012) for WN stars" (3.1.3 Mass-loss determination) [from Crowther et al. (2006b); Searle et al. (2008); Crowther (2007); Sander et al. (2012)]
- External data: Spectral types of stars  
  > "Spectral type identifications have been taken from Crowther et al. (2006a) for WR stars, Clark et al. (2010) for the YHGs and RSGs" (Table 2) [from Crowther et al. 2006a; Clark et al. 2010; Negueruela et al. 2010]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline, then re-calibrated with less flagging; REMCLOUD applied to 30 June data only; phase self-calibration  
  > "We therefore proceeded using re-calibrated 30th June data with REMCLOUD and re-calibrated 1st July data without REMCLOUD." (2.1 Observations and imaging)
- casa version: _not stated_
- pipeline version: CASA pipeline version 4.3.1: r34044  
  > "(CASA; pipeline version 4.3.1: r34044)" (2.1 Observations and imaging)
- archive products used as is: _not stated_
- flux calibrator: Titan and Pallas (228.96 and 82.01 mJy at 91.495 GHz); J1617-5848 for phase and bandpass  
  > "observations of Titan and Pallas were used to amplitude calibrate the data with assumed flux densities of 228.96 and 82.01 mJy respectively (at 91.495 GHz)." (2.1 Observations and imaging)
- flux scale uncertainty: 5%  
  > "the expected absolute amplitude calibration error for ALMA which is taken to be 5% (see ALMA Cycle 2 Technical Handbook)" (3.1 3-mm star characteristics)
- self calibration: Several iterations of phase self-cal using models of bright compact sources, then a final amplitude+phase round with Wd1-9 and Wd1-26 in the model  
  > "A final round of amplitude and phase calibration was also performed incorporating information from both Wd1-9 and Wd1-26 in the model." (2.1 Observations and imaging)

### Imaging

- task: CASA CLEAN with mosaicing and multi-frequency synthesis  
  > "initially imaged using the mosaicing and multi-frequency synthesis functions in the CASA CLEAN software." (2.1 Observations and imaging)
- deconvolver: multi-scale, Cotton-Schwab, scales 1, 14, 12, 37 & 119  
  > "This utilised Cotton-Schwab cleaning and natural weighting with scale sizes set at 1, 14, 12, 37 & 119." (2.1 Observations and imaging)
- weighting robust: natural weighting  
  > "This utilised Cotton-Schwab cleaning and natural weighting" (2.1 Observations and imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Initial cleaning only on the bright compact component of Wd1-9 (153 mJy) to subtract it  
  > "Cleaning was done only on the bright compact component of Wd1-9 (which has a flux density of 153 mJy)" (2.1 Observations and imaging)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied after cleaning to the full-field image  
  > "The final full-field image was primary beam corrected following cleaning" (2.1 Observations and imaging)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 750×570 mas  
  > "The final image has a fitted beam of 750×570 mas." (2.1 Observations and imaging)
- final rms: _not stated_

### Inherited from earlier work

- Astrometric alignment procedure (HGEOM, JMFIT on Wd1-9 vs FORS/radio)  
  > "Following the procedure from Do10, we determined any offset between the ALMA and FORS image" (2.1 Observations and imaging) [from Dougherty et al. 2010 (Do10)]
- SEAC source extraction software  
  > "the SEAC source extraction software was used (see Peck 2014; Morford et al. 2017, for further details)." (2.2 Identification of 3 mm stars) [from Peck 2014; Morford et al. 2017]
- Paper structure mirrors radio study  
  > "we choose to mirror the structure of that work in this paper" (1. Introduction) [from Do10]
- Mass-loss formalism  
  > "(see e.g. Wright & Barlow 1975)" (3.1.3 Mass-loss determination) [from Wright & Barlow 1975]

### Not stated but needed to reproduce (our reading)

- SEAC code availability/parameters beyond 5σ/3σ thresholds and 6x6 grid
- Which pointings and model components were used in each self-cal iteration; solints
- CLEAN threshold, mask, cell and image size, iteration counts
- Exact scale-size units (listed '1, 14, 12, 37 & 119' appear garbled)
- Exact Teff/v_inf choices for stars not in tables and values of fcl used (assumed 1)
- REMCLOUD parameters

## Analysis recipe

1. **Re-calibrate and self-calibrate**: Pipeline calibration, re-calibration with less flagging and REMCLOUD for 30 June, phase self-cal then final amp+phase  
  > "Following initial calibration (both with initial and recalibrated data), several iterations of phase self-calibration were applied to the data." (2.1 Observations and imaging)
   - software: CASA, REMCLOUD, GAINCAL, APPLYCAL
   - fitting: _not stated_
   - validation: Checked that resolved sizes are not due to phase errors  
  > "In order to ensure that this is not the result of potential phase errors in the data" (2.1 Observations and imaging)
2. **Image mosaic**: Multi-scale mosaic CLEAN with natural weighting after subtracting Wd1-9 compact component; PB correction  
  > "The final images were produced using the mosaicing and multi-scale capabilities within CLEAN including data from all pointings" (2.1 Observations and imaging)
   - software: CASA CLEAN
   - fitting: _not stated_
   - validation: _not stated_
3. **Astrometric alignment**: Gaussian fit to Wd1-9 compact component in ALMA and FORS images and shift ALMA image  
  > "we chose to shift the ALMA image in order to bring the peak positions of Wd1-9 (as determined by the Gaussian fit) into alignment." (2.1 Observations and imaging)
   - software: AIPS, HGEOM, JMFIT
   - fitting: _not stated_
   - validation: _not stated_
4. **Source detection and catalogue**: SEAC flood-fill with 5σ seed and 3σ flood thresholds on local rms; lower seeds 4.5/4σ for optically known undetected stars; cross-match with catalogues  
  > "Thresholds of 5 σ and 3 σ were set for the initial use of SEAC on the ALMA wide-field image" (2.2 Identification of 3 mm stars)
   - software: SEAC
   - parameter: σ from rms in 6×6 grid cells  
  > "σ is a regionalised noise level calculated by determining the rms level in individual cells of a 6×6 grid across the whole image." (2.2 Identification of 3 mm stars)
   - fitting: _not stated_
   - validation: _not stated_
5. **Measure flux densities and sizes**: Gaussian fits (JMFIT) to pixels >3×local rms, or SEAC island integrated flux; LAS for non-Gaussian; IRING annular profiles; 5% calibration error added in quadrature  
  > "Primarily a Gaussian fit was performed using the AIPS task JMFIT." (3.1.1 Spatial resolution)
   - software: AIPS JMFIT, IRING, SEAC
   - fitting: Gaussian least squares via JMFIT  
  > "only pixels >3 times the rms local to the source were included in the fit." (3.1.1 Spatial resolution)
   - validation: Visual assessment of 3D plots of fit  
  > "Three dimensional plots of the source structure and the resulting model fit were used to visually assess the fit" (3.1.1 Spatial resolution)
6. **Derive spectral indices**: Two-point index between 8.6 GHz (3.6 cm) Do10 fluxes and 3 mm; limits from 170 µJy/beam radio limit  
  > "we calculate the two-point mm-radio spectral index, α, for each star." (4.2.1 mm-radio spectral indices)
   - fitting: _not stated_
   - validation: _not stated_
7. **Derive mass-loss rates**: Wright & Barlow free-free relation (Eq. 1) with Gaunt factor approximation, smooth wind (fcl=1)  
  > "A given flux can therefore be interpreted as a certain mass-loss rate for a smooth wind ( f cl = 1)" (3.1.3 Mass-loss determination)
   - parameter: Te = 0.5 Teff; d = 5 kpc; mu=1.4,Z=1,gamma=1 for OB; mu=4.0 (WN6 or earlier), 2.0 (later WN), 4.7 (WC8/9); mu=1.6, gamma=0.8, Z=0.9 for BHGs  
  > "we adopt T e = 0.5 T e f f (e.g. Drew 1989)" (3.1.3 Mass-loss determination)
   - assumption: mm flux not affected by binarity; wind emission thermal; two non-thermal sources excluded  
  > "Our mass-loss estimates assume the mm fluxes are not affected by binarity" (3.1.3 Mass-loss determination)
   - fitting: _not stated_
   - validation: Compared with radio mass-loss rates and non-LTE model values for WR F and S (within factor ~2)  
  > "shows an encouraging consistency in mass-loss rates to within a factor of ∼ 2." (4.2.2 Mass-loss rates)
8. **Test whether sources are resolved and wind photosphere size**: Compare fitted sizes with analytic mm-photosphere radius from Wright & Barlow  
  > "These range from 0.1 (WR K) to 3.8 (WR L) milliarcsec" (4.2.3 Spatially resolved emission)
   - fitting: _not stated_
   - validation: Analytic estimate agrees within factor ~2 with non-LTE for WR S  
  > "shows coincidence to within a factor of ∼ 2" (4.2.3 Spatially resolved emission)

## Software

- **CASA** pipeline 4.3.1 (r34044): calibration and CLEAN imaging  
  > "Common Astronomy Software Applications (CASA; pipeline version 4.3.1: r34044)" (2.1 Observations and imaging)
- **REMCLOUD** : water vapour/cloud phase correction for 30 June data  
  > "making use of the REMCLOUDs package (Maud et al. 2017)" (2.1 Observations and imaging)
- **AIPS** : HGEOM, JMFIT Gaussian fits, IRING profiles  
  > "the images were transferred to the AIPS (Astronomical Image Processing Software) environment." (2.1 Observations and imaging)
- **SEAC** : source extraction  
  > "the SEAC source extraction software was used" (2.2 Identification of 3 mm stars)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 3 mm sources detected | 101 | not stated | sources | 4 | The total 3 mm catalogue list therefore contains 101 sources. |
| Stellar sources detected | 50 | not stated | stars | 4 | Of the total 101 objects detected in these observations, 50 have been identified as stellar sources |
| Mean WR mass-loss rate (excl. WR S, Wd1-13) | 3.6e-5 | ±0.4e-5 | Msun/yr | 7 | ( M [˙] ∼ 3.6 ± 0.4 × 10 [−][5] _M_ ⊙ yr [−][1] ; excluding WR S and Wd1-13) |
| Mean WC mass-loss rate | 4.2e-5 | ±0.7e-5 | Msun/yr | 7 | ∼ 4.2 ± 0.7 × 10 [−][5] _M_ ⊙ yr [−][1] ) are entirely consistent |
| Beam / 3σ-like noise | 750×570 mas; ~28 µJy/beam | not stated | mas; µJy/beam | 2 | The final image has a fitted beam of 750×570 mas. |
| Mass-loss rate of LBV Wd1-243 (3 mm) | log Mdot ~ -4.6 | not stated | log Msun/yr | 7 | mm determinations (log( M [˙] /M ⊙ yr [−][1] ) ∼−4.6; data obtained in 2015) |
| Upper limit on magnetar continuum | 65 | not stated | µJy/beam | 4 | our ALMA observations yield only an upper limit to the continuum flux of 65 µJy beam [−][1] . |

## Qualitative findings

- All 21 WRs in the field detected; many hot stars appear spatially resolved; cool hypergiants show cometary nebulae oriented away from cluster core  
  > "comprising all 21 Wolf-Rayets within the field of view, plus eight cool and 21 OB super-/hypergiants." (abstract)

## Claim tuples

- H: Mass-loss rates increase through post-MS evolution | E: Derive 3 mm free-free mass-loss rates for WR, OB, LBV stars | R: WRs log Mdot -4.1 to -4.8; B super/hypergiants -5.1 to -5.8 | F: Significant increase from OB supergiant to WR | **supported**
- H: Hot stars' extended 3 mm emission is not the stellar wind | E: Compare Gaussian sizes with analytic mm-photosphere radii | R: Photospheres 0.1-3.8 mas versus ~0.6 arcsec sizes | F: Compact wind-blown bubbles/haloes proposed, tentative | **partially**
- H: Binarity does not make WRs systematically brighter, but Wd1-9 is extreme | E: Compare binary and single WR mass-loss rates | R: No systematic excess for binaries | F: Wd1-9 mass-loss comparable to most extreme WRs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Free-free mm emission arises at large radii where terminal velocity reached, so less dependent on velocity law  
  > "the emission due to electron-ion interactions in their ionised winds arises at large radii, where the terminal velocity will have been reached." (3.1.3 Mass-loss determination)
- Alternative: Binary or LBV ejection mechanisms and resolved WCRs rejected as explanation for extended hot-star emission  
  > "it unlikely that we have resolved the (putative) WCRs of these objects." (8.2 Resolved emission associated with the OB super/hyper-giant and WR cohorts)
- How they decided it was enough: _not stated_
- Limitation (authors): Heterogeneous S/N precludes flux-limited survey; non-detections bias OB sample; mm flux of extended sources partly resolved out  
  > "the heterogeneous S/N ratio across the field precludes consideration of our results as a flux-limited survey of OB stars within Wd1." (6.1 The OB super- and hypergiants)
- Caveat (inferred, ours): Mass-loss rates rely on adopted Teff, v_inf, fcl=1 and 5 kpc distance, error ~0.2 dex only from flux
- Caveat (inferred, ours): Self-calibration on bright sources and astrometric shift may affect resolved-size claims
- Caveat (inferred, ours): Resolved-source interpretation (bubbles) speculative
- Caveat (inferred, ours): Possible contamination of ALMA-only sources by background galaxies

## Reproducibility

- Data public (paper): Project code and ALMA data acknowledged; archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00897.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Full CLEAN parameters
- Missing: Self-cal details
- Missing: SEAC code
- Missing: Adopted stellar parameters for all stars
- Data volume (inferred): ~50-100 GB raw (27-pointing mosaic, two EBs)
- Score (inferred): 5/5, Data public and main steps described, but imaging/self-cal parameters and SEAC details missing; results mostly numeric tables.
- Rediscovery candidate: yes, Public data, numeric flux catalogue and mass-loss formula given, though imaging details partial.

## Links

- Method: Wright & Barlow 1975 (mass-loss formalism)
- Method: Maud et al. 2017 (REMCLOUD)
- Method: Morford et al. 2017 (SEAC)
- Companion: Fenech et al. 2017 (ALMA results on Wd1-9)
- Companion: Dougherty et al. 2010 (radio study of Wd1)
- Companion: Andrews et al. 2018 (ATCA 8.6 GHz images)

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 55,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
