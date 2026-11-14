# ALMA Detection of Dark Chromospheric Holes in the Quiet Sun

`2019ApJ...877L..26L` | The Astrophysical Journal Letters 2019 | first author: Loukitcheva, Maria A. | arXiv: 1905.06763 | DOI: 10.3847/2041-8213/ab2191

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: Does ALMA Band 3 reveal quiet-Sun chromospheric structure, in particular dark/cool regions, that is not seen in UV, visible or magnetogram data?  
  > "report the first detection of particular dark (i.e. cool) regions in ALMA images" (Introduction)
- Target **Quiet-Sun region near disk center**: coordinates about 200'' south-west of disk center  
  > "A single quiet-Sun target about 200$''$ south-west of disk center, tracked for solar rotation" (Data Collection and Reduction); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00202.S
- bands: Band 3 (100 GHz, 3 mm)  
  > "acquired on 2017 April 27 in Band 3 (100 GHz, i.e., a wavelength of 3 mm) in configuration C40-3" (Data Collection and Reduction)
- frequencies and spectral setup: four 2 GHz-wide spectral windows at 93, 95, 105 and 107 GHz  
  > "The four 2 GHz-wide spectral windows at 93, 95, 105 and 107 GHz were combined in the mapping" (Data Collection and Reduction)
- continuum bandwidth: _not stated_
- arrays: 12m and 7m arrays plus total power antennae  
  > "supplemented by single-dish images of the full Sun with a cadence of $\approx$ 10 minutes, made with ALMA’s total power antennae at a resolution of 60$''$" (Data Collection and Reduction)
- configurations: C40-3  
  > "in configuration C40-3, which included 38$\times$12m antennae and 8$\times$7m antennae" (Data Collection and Reduction)
- baselines: _not stated_
- angular resolution: 1.6'' restored beam  
  > "then restored with a synthesized beam of 1.6$''$" (Data Collection and Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 37 minutes total, 10.5 min scans  
  > "observed in 10.5 minute scans separated by 2-minute calibration scans, with 2-second integrations, for a total of 37 minutes" (Data Collection and Reduction)
- observing dates: 2017 April 27, 16:00-16:45 UT  
  > "The Sun was observed in the time interval 16:00–16:45 UT (45 minutes)." (Data Collection and Reduction)
- pi or archival as stated: _not stated_
- Other facility **SDO/HMI**: 60 photospheric magnetograms, 45 s cadence  
  > "60 photospheric magnetograms with a 45-sec cadence from the Helioseismic and Magnetic Imager" (Data Collection and Reduction)
- Other facility **SDO/AIA**: 220 images at 1600, 1700, 304 Å, 12 s cadence  
  > "220 images at 1600 Å, 1700 Å, and 304 Å, obtained with a 12-sec cadence by the Atmospheric Imaging Assembly" (Data Collection and Reduction)
- Other facility **IRIS**: 82 slit-jaw images in Mg II k 2796 Å  
  > "82 IRIS slit-jaw images with a 32-sec cadence in the 2796 Å Mg II k line" (Data Collection and Reduction)
- Other facility **BBSO and GONG/CTIO**: Halpha full-disk images  
  > "38 images from the BBSO and 35 images from the GONG telescope at CTIO" (Data Collection and Reduction)

## Processing

### Calibration

- pipeline or manual: standard CASA software, calibration following solar commissioning papers  
  > "calibrations followed the prescriptions given therein" (Data Collection and Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: images mapped and self-calibrated  
  > "Individual 2-second interferometric images were mapped and self-calibrated using standard CASA software" (Data Collection and Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.3''  
  > "The images were made 401 pixels square, with a cell size of 0.3$''$" (Data Collection and Reduction)
- image size: 401 pixels square; FOV about 120''  
  > "The mapped field of view (FOV) was about 120$''$" (Data Collection and Reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "corrected for the primary beam response" (Data Collection and Reduction)
- array combination: interferometer images plus single-dish brightness offset of 7236 K added  
  > "7236 K (derived from the target location in the single-dish images) was added to each image" (Data Collection and Reduction)
- smoothing: _not stated_
- final beam: 1.6''  
  > "restored with a synthesized beam of 1.6$''$" (Data Collection and Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Solar ALMA calibration and flux-to-brightness-temperature conversion follow commissioning papers  
  > "Solar observing with ALMA is described in the commissioning papers by (cite: 2017SoPh..292...87S) and (cite: 2017SoPh..292...88W)" (Data Collection and Reduction) [from (cite: 2017SoPh..292...87S); (cite: 2017SoPh..292...88W)]

### Not stated but needed to reproduce (our reading)

- CASA version and solar-specific scripts
- Imaging task, deconvolver, weighting/robust, and cleaning details
- Self-calibration solution intervals
- How the 7236 K offset was derived from total-power maps
- Co-alignment and mask details for the ROI rectangles

## Analysis recipe

1. **Make ALMA brightness temperature cube**: Per-2s images mapped, self-calibrated, converted to Tb, single-dish offset added  
  > "the interferometric images were converted from flux to brightness temperature, and then 7236 K" (Data Collection and Reduction)
   - software: CASA
   - parameter: 4 spws combined, 1.6'' beam, 0.3'' cells, 1090 images  
  > "The final data cube $T_b(x,y,t)$ contains 1090 images." (Data Collection and Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Co-align multiwavelength data**: Cross-correlation of 45-min averaged images against SDO full-disk reference  
  > "all other images were coaligned by cross-correlating images averaged over 45 minutes" (Data Collection and Reduction)
   - fitting: _not stated_
   - validation: Remaining displacements below 1''  
  > "The remaining image displacements are less than 1$''$" (Data Collection and Reduction)
3. **Compare time-averaged images and histograms for ChAH, network and internetwork regions**: Time-averaged maps and brightness/DN histograms for four equal-size rectangles  
  > "we complemented it with three other regions of the same size in the FOV" (Results)
   - fitting: _not stated_
   - validation: Stability checked via histograms of full time sequence  
  > "To confirm the ChAH’s stability over the duration of the observations" (Results)

## Software

- **CASA** : mapping and self-calibration  
  > "mapped and self-calibrated using standard CASA software" (Data Collection and Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Minimum ALMA Band 3 Tb in ChAH | 4370 | not stated | K | 3 | in the ChAH data cube it drops as low as 4370 K, which is about 60% of the quiet-Sun brightness temperature |
| ChAH size | approx. 20'' x 20'' | not stated | arcsec | 3 | With horizontal dimensions of approx. 20$''$ x 20$''$ |
| Fraction of frames with Tb<5000 K in ChAH rectangle | 57 | not stated | % | 3 | In 57% of the 2s frames there are regions within the blue ChAH rectangle where the brightness temperature is below 5000 K. |
| Time-averaged ChAH Tb range | 5600-7500 | not stated | K | 3 | The brightness temperature ranges from 5600 K to 7500 K in the Band 3 image |

## Qualitative findings

- ChAH is long-lasting and not distinguishable in UV or magnetogram data; Halpha is relatively bright there  
  > "the ChAH remains quite stable over the whole time series, demonstrating that it is a long lasting phenomenon" (Results)

## Claim tuples

- H: Does ALMA detect cool chromospheric regions missed by other diagnostics? | E: Compare Band 3 maps and histograms with HMI, AIA, IRIS, Halpha for dark, network and internetwork regions | R: ChAH has histogram maximum ~1000 K below internetwork in Band 3 only | F: ALMA senses cool chromospheric gas missed by shorter-wavelength diagnostics | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Interferometric missing flux handled by a single constant offset
- Caveat (inferred, ours): Single region, single epoch; a cool-gas interpretation is speculative
- Caveat (inferred, ours): Possible imaging artifacts not assessed

## Reproducibility

- Data public (paper): ALMA project code cited in acknowledgments  
  > "This paper makes use of the following ALMA data: $ADS/JAO.ALMA\#2016.1.00202.S$." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Solar ALMA imaging scripts and parameters
- Missing: ROI rectangle coordinates
- Data volume (inferred): tens to hundreds of GB
- Score (inferred): 3/5, Public data and clear region definitions, but the imaging recipe is mostly delegated to commissioning papers.
- Rediscovery candidate: no, Solar imaging recipe incomplete.

## Links

- Method: (cite: 2017SoPh..292...87S) (Solar ALMA observing)
- Method: (cite: 2017SoPh..292...88W) (Solar ALMA calibration)

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 30,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
