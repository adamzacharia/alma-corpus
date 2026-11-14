# An ALMA survey of submillimetre galaxies in the Extended Chandra Deep Field South: radio properties and the far-infrared/radio correlation

`2014MNRAS.442..577T` | Monthly Notices of the Royal Astronomical Society 2014 | first author: Thomson, A. P. | arXiv: 1404.7128 | DOI: 10.1093/mnras/stu839

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the radio spectral indices and far-infrared/radio correlation (q_IR) of ALMA-identified 870 µm SMGs in the ECDFS, and do q_IR and alpha evolve with age as starburst models predict?  
  > "We present a study of the radio properties of 870 µm-selected submillimetre galaxies (SMGs), observed at high resolution with ALMA in the Extended Chandra Deep Field South." (abstract)
- Target **ALESS SMGs in the ECDFS (76-source full sample)**: coordinates _not stated_; z/distance photometric redshifts, median <z_phot> = 2.57 for the stack 1 subset; individual values in Table 3  
  > "we restrict our analysis to the 76 ALMA 870 µm-detected SMGs with measured z phot" (2.5 Final sample); distance from Simpson et al. (2013)  
  > "we restrict our analysis to the 76 ALMA 870 µm-detected SMGs with measured z phot" (2.5 Final sample)

## Data provenance

- ALMA projects: 2011.0.00294.S
- bands: Band 7 (870 µm)  
  > "with ALMA’s Band 7 receivers (870-µm) in Cycle 0" (2.1 ALMA 870-µm observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: typical synthesized beam ~1.6 x 1.2 arcsec  
  > "we achieve a typical synthesized beam of ∼ 1.6 × 1.2 [′′]" (2.1 ALMA 870-µm observations)
- max recoverable scale: _not stated_
- sensitivity: typical RMS ~0.4 mJy/beam  
  > "reach a typical RMS sensitivity of σ ∼ 0.4 mJy beam [−][1]" (2.1 ALMA 870-µm observations)
- time on source: ~120 s per source  
  > "with on-source integration times of ∼ 120 s per source" (2.1 ALMA 870-µm observations)
- observing dates: 2011 October 18 – November 3  
  > "between 2011 October 18 – November 3" (2.1 ALMA 870-µm observations)
- pi or archival as stated: _not stated_
- Other facility **VLA 1.4 GHz**: Public ECDFS DR2 map, RMS 6 µJy/beam, 2.8x1.6 arcsec resolution  
  > "reaches an RMS sensitivity at the centre of the field of 6 µJy beam [−][1]." (2.3 VLA 1.4-GHz observations)
- Other facility **GMRT 610 MHz**: New 610 MHz mosaic, RMS 45 µJy/beam, beam 4.4x3.0 arcsec  
  > "reaches an RMS sensitivity of 45 µJy beam [−][1] over 70 [′] × 70 [′]" (2.2 GMRT 610-MHz observations)
- Other facility **Herschel SPIRE**: 250-500 µm photometry used by Swinbank et al. for far-IR luminosities  
  > "Swinbank et al. (2014) fit the deblended 250–500 µm _Her-_ _schel_ SPIRE photometry" (2.4 Optical–far-IR data and photometric redshifts)
- External data: Photometric redshifts for the ALESS SMGs  
  > "Simpson et al. (2013) derived photometric redshifts (z phot ) for the ALESS SMGs" (2.4 Optical–far-IR data and photometric redshifts) [from Simpson et al. (2013)]
- External data: Far-IR luminosities, dust temperatures, SFR, dust and stellar masses  
  > "Full details of the deblending process, and of the derived far-IR properties of each ALESS SMG are presented in Swinbank et al. (2014)." (2.4 Optical–far-IR data and photometric redshifts) [from Swinbank et al. (2014)]
- External data: VLA 1.4 GHz ECDFS DR2 map  
  > "We rely on data from the VLA 1.4-GHz Survey of the ECDFS DR2 (Miller et al. 2013)" (2.3 VLA 1.4-GHz observations) [from Miller et al. (2013)]
- External data: Starburst evolutionary model tracks of alpha vs q_IR  
  > "Bressan et al. (2002) provide model tracks of α and q IR for evolving starburst galaxies" (4.4 Trends in α and q IR in high-redshift ULIRGs) [from Bressan et al. (2002)]

## Processing

### Calibration

- pipeline or manual: GMRT data reduced with AIPS; ALMA reduction described in Hodge et al. (2013)  
  > "Data reduction was accomplished using AIPS." (2.2 GMRT 610-MHz observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: ALMA: natural weighting; GMRT: Briggs ROBUST = 0  
  > "using CLEAN with natural weighting" (2.1 ALMA 870-µm observations); "with Briggs weighting ( RMODE = ‘norm’, ROBUST = 0)" (2.2 GMRT 610-MHz observations)
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
- final beam: ALMA ~1.6x1.2 arcsec  
  > "typical synthesized beam of ∼ 1.6 × 1.2 [′′]" (2.1 ALMA 870-µm observations)
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction and imaging  
  > "in which detailed descriptions of the data reduction and imaging are given." (2.1 ALMA 870-µm observations) [from Hodge et al. (2013)]
- Bandwidth smearing map technique  
  > "follow the technique of Arumugam et al. (2014, _in prep_ ) to create a map of BWS as a function of position" (2.3 VLA 1.4-GHz observations) [from Arumugam et al. (2014, in prep)]

### Not stated but needed to reproduce (our reading)

- ALMA reduction details (CASA version, calibrators) only in Hodge et al. 2013
- Bandwidth smearing technique unpublished (Arumugam in prep)
- Stacking implementation and bootstrap details
- Exact rest-frame K-correction and q_IR calculation procedure for upper limits
- Mock catalogue generation details for selection boundary
- Age-bin assignment from Bressan tracks

## Analysis recipe

1. **measure radio flux densities**: Peak pixel within 2 arcsec aperture at each ALMA position, with bandwidth-smearing correction; BLSUM in AIPS for extended sources; 3σ limits for non-detections  
  > "we measure the radio flux densities of these sources by taking the peak pixel value in each map within a 2arcsec aperture centred on each ALMA ID" (3 ANALYSIS AND RESULTS)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **stack non-detections**: Bootstrap median stacking of both maps at positions of undetected SMGs  
  > "we measure bootstrap median flux densities of S 1.4GHz = 10 ± 1 µJy and S 610MHz = 38 ± 5 µJy" (3 ANALYSIS AND RESULTS)
   - fitting: _not stated_
   - validation: _not stated_
3. **derive spectral indices and q_IR**: Power law S ∝ ν^α between 610 MHz and 1.4 GHz; K-correct VLA flux to rest-frame 1.4 GHz; q_IR from L_IR (Swinbank) and L_1.4GHz  
  > "which we assume to follow a simple power law, S ν ∝ ν [α]" (3.1 Radio spectral index measurement)
   - assumption: Cosmology H0 = 71, Ωm = 0.27, ΩΛ = 0.73  
  > "we use a cosmology with H 0 = 71 km s [−][1] Mpc [−][1], Ω m = 0.27, and Ω Λ = 0.73" (1 INTRODUCTION)
   - fitting: Fit q_IR ∝ (1+z)^γ  
  > "we fit q IR ∝ (1 + z) [γ], where γ = −0.15±0.17" (4.2 Far-infrared/radio correlation)
   - validation: _not stated_
4. **test selection effects and compare with starburst tracks**: 500,000 mock galaxies with L_IR, α, q_IR drawn from the data and random z in 1.5-3.5; observability thresholds; compare with Bressan tracks in three age groups  
  > "generating a catalogue of 500,000 mock galaxies with L IR, α and q IR drawn randomly from the data, with random redshifts in the range 1.5 < z < 3.5" (4.4 Trends in α and q IR in high-redshift ULIRGs)
   - fitting: _not stated_
   - validation: Mock-catalogue selection boundary check  
  > "We see no evidence of a selection boundary within the plot range affecting our ability to detect steep spectrum SMGs with low q IR ." (4.4 Trends in α and q IR in high-redshift ULIRGs)

## Software

- **AIPS** : GMRT data reduction and BLSUM flux measurements  
  > "Data reduction was accomplished using AIPS." (2.2 GMRT 610-MHz observations)
- **HYPERZ** : photometric redshifts (by Simpson et al. 2013)  
  > "Using the HYPERZ code of Bolzonella et al. (2000)" (2.4 Optical–far-IR data and photometric redshifts)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median spectral index alpha (610 MHz-1.4 GHz), 52 VLA-detected SMGs | -0.79 | 0.06 | dimensionless | 3 | we measure a median spectral index of α all = −0.79 ± 0.06 |
| Median q_IR, full sample | 2.56 | 0.05 | dimensionless | 3 | we measure a median q IR = 2.56 ± 0.05 for our full sample of SMGs |
| Median q_IR, VLA-detected | 2.58 | 0.07 | dimensionless | 3 | Restricting our analysis to the 52 SMGs detected at the VLA gives q IR = 2.58 ± 0.07. |
| Evolution index gamma of q_IR ∝ (1+z)^γ | -0.15 | 0.17 | dimensionless | 3 | where γ = −0.15±0.17 |
| Stack 1 spectral index | -1.57 | 0.08 | dimensionless | 2 | we measure α stack = −1.57 ± 0.08 |
| Stack 2 spectral index | -0.29 | 0.08 | dimensionless | 2 | we measure α stack = −0.29 ± 0.08 |

## Qualitative findings

- No ALMA-blank LABOCA fields show evidence of missed luminous SMGs; they likely reflect multiplicity or extended emission  
  > "we conclude that there is no reason to believe our ALMA source extraction process has missed a significant number of _bona-fide_ luminous z ∼ 2 SMGs." (3.3 ALMA-blank maps)

## Claim tuples

- H: ALMA-identified SMGs have higher q_IR than single-dish selected samples because they are not radio-biased | E: Measure q_IR with individual K-corrections for 76 ALMA SMGs | R: median q_IR = 2.56 ± 0.05 vs ~2.4 previously | F: Higher q_IR consistent with removing radio-bias in counterpart identification | **supported**
- H: q_IR evolves with redshift | E: Fit q_IR ∝ (1+z)^γ | R: γ = -0.15 ± 0.17 | F: No compelling evidence for evolution | **refuted**
- H: alpha and q_IR evolve with starburst age as in Bressan models | E: Segregate SMGs into age groups along model tracks and compare M* and Mdust | R: weak correlations of M* and Mdust with age | F: Tentative support for the models | **partially**

## Reasoning

- Why this data: ALMA gives precise positions so radio counterparts are identified without statistical association  
  > "The ALMA observations allow us to obtain precise positions for a sample of SMGs" (1 INTRODUCTION)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small number of SMGs per age bin makes correlations weak; upper-limit spectral indices boost L1.4GHz and lower q_IR  
  > "These correlations are weak due to the small number of SMGs in each “age” bin" (4.4 Trends in α and q IR in high-redshift ULIRGs)
- Caveat (inferred, ours): Photometric redshifts have large uncertainties that propagate into K-corrections and q_IR
- Caveat (inferred, ours): Spectral index limits from 3σ GMRT limits bias results
- Caveat (inferred, ours): Age-bin correlations are low significance
- Caveat (inferred, ours): Median alpha is for the detected subset, which is biased

## Reproducibility

- Data public (paper): All ALMA, Herschel, VLA and Spitzer data available through public archives  
  > "All of the ALMA, Herschel, VLA and _Spitzer_ data employed in this analysis are available through the ESO, _Her-_ _schel_, VLA and _Spitzer_ archives." (ACKNOWLEDGMENTS)
- Products in archive: _not stated_
- Missing: GMRT 610 MHz map not stated to be public
- Missing: Bandwidth smearing method unpublished
- Missing: Derived L_IR, z_phot taken from Swinbank 2014 and Simpson 2013
- Data volume (inferred): Radio map analysis dominates; ALMA maps from the earlier release are small (~tens of GB raw)
- Score (inferred): 3/5, Simple measurements and Table 3 values enable checks, but the GMRT map and upstream catalogs are needed and ALMA plays only a minor role.
- Rediscovery candidate: no, The GMRT map is not stated as public and the inputs depend on other papers' catalogs; ALMA is used only for positions.

## Links

- Method: Hodge et al. (2013) (ALMA data reduction and source extraction)
- Method: Arumugam et al. (2014, in prep) (Bandwidth smearing correction)
- Companion: Simpson et al. (2013) (Photometric redshifts)
- Companion: Swinbank et al. (2014) (Far-IR properties)
- Related: ALESS
- Related: LESS
- Related: ECDFS
- Related: HerMES

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
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
  "facts": 69,
  "stated": 33,
  "rate": 0.478
 },
 "evidence_ok": true
}
```
