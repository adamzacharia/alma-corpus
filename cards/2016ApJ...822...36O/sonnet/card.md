# ALMACAL I: First Dual-band Number Counts from a Deep and Wide ALMA Submillimeter Survey, Free from Cosmic Variance

`2016ApJ...822...36O` | The Astrophysical Journal 2016 | first author: Oteo, I. | arXiv: 1508.05099 | DOI: 10.3847/0004-637X/822/1/36

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Can archival ALMA calibrator observations be combined into a deep, wide submm survey to detect faint DSFGs and measure cumulative number counts in bands 6 and 7?  
  > "Gathering together data acquired during multiple visits to many ALMA calibrators, it is possible to reach noise levels which allow the detection of faint dusty, star-forming galaxies (DSFGs) over a significant area." (abstract)
- Target **69 ALMA calibrator fields (e.g. J1058+0133, J0108+0135, J1744-3116)**: coordinates see calibrator table (e.g. J1058+0133 10:58:29.6 +01:33:58.8)  
  > "J1058+0133 | 10:58:29.6 | +01:33:58.8 | 0.890" (Table 1); z/distance calibrator z listed in table; DSFG redshifts unknown  
  > "J1058+0133 | 10:58:29.6 | +01:33:58.8 | 0.890" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (~250 GHz, 1.2 mm) and Band 7 (~345 GHz, 870 um)  
  > "we retrieved data in ALMA bands 6 (B6, around 250 GHz or 1.2 mm) and 7 (B7, around 345 GHz or 870 $\mu$m)" (2 Extracting and calibrating ALMA calibrator data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: mostly sub-arcsec  
  > "most of our ALMA maps have sub-arcsec resolution" (2 Extracting and calibrating ALMA calibrator data)
- max recoverable scale: _not stated_
- sensitivity: rms ~25 uJy/beam in the deepest maps; typically ~30 uJy/beam  
  > "reaching depths of $\sim 25 \, {\rm \mu Jy \, beam^{-1}}$ at sub-arcsec resolution" (abstract)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public archival calibrator data observed before July 2015; proprietary data obtained via helpdesk request  
  > "We first used the ALMA calibrator archive to find all calibrators observed prior to 2015 July as part of science projects that passed quality control." (2 Extracting and calibrating ALMA calibrator data)
- External data: Composite LESS SMG SED used for the band 870 um to 1.2 mm conversion and the SED templates  
  > "The counts have been converted from 870 $\mu$m to 1.2 mm using the composite SMG SED from the LESS survey (cite: Swinbank2014MNRAS.438.1267S), redshifted to $z = 2.3$" (4 Number counts) [from Swinbank2014MNRAS.438.1267S]
- External data: Literature ALMA number counts for comparison  
  > "Previous results based on ALMA data, from (cite: Karim2013MNRAS.432....2K), (cite: Simpson2015ApJ...807..128S), (cite: Hatsukade2013ApJ...769L..27H), (cite: Ono2014ApJ...795....5O) and (cite: Fujimoto2015arXiv150503523F) are also shown." (4 Number counts) [from Karim2013; Simpson2015c; Hatsukade2013; Ono2014; Fujimoto2015]

## Processing

### Calibration

- pipeline or manual: Delivered calibration reapplied to bandpass calibrators; pseudo-continuum self-calibration with a point-source uv model; statwt reweighting  
  > "we needed to recover the correct flux density scale of the bandpass calibrators from the flux tables in the data delivery packages and re-apply the calibration tables to the calibrators." (2 Extracting and calibrating ALMA calibrator data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Two rounds (phase, then amplitude+phase), solution interval = integration time, point-source model fitted in uv  
  > "Two rounds of self-calibration were applied, at first only in phase, then in both amplitude and phase, both with a solution interval equal to the integration time." (2 Extracting and calibrating ALMA calibrator data)

### Imaging

- task: CASA clean, per scheduling block; then concat of all data per calibrator per band  
  > "The calibrator-subtracted visibilities for every SB were then imaged individually, without combining data for a given calibrator, using the clean task." (2 Extracting and calibrating ALMA calibrator data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Cleaning window radius 1.5x PB FWHM (23'' B6, 17'' B7), cleaned to the rms of the dirty image; 1.5'' box around detections for flux measurement  
  > "we defined a cleaning window of radius 1.5$\times$ the expected fwhm of the PB (23$''$ and 17$''$ in B6 and B7, respectively) in each band" (2 Extracting and calibrating ALMA calibrator data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: impbcor after cleaning; source detection done before PB correction  
  > "After cleaning, the maps were corrected for PB attenuation using impbcor" (3.2 Source catalogue)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Individual project codes, execution blocks and calibrator-to-dataset list
- Which datasets were discarded as poorly calibrated
- Weighting scheme/robust, cell size, image size, and deconvolver
- CASA version
- SExtractor detection parameters
- Method of flux deboosting correction applied to sources
- Spectral window selection per band

## Analysis recipe

1. **Calibrate calibrator data and subtract the calibrator**: Re-apply calibration, create pseudo-continuum, self-calibrate, fit and subtract point-source uv model per observation  
  > "Finally, the point-source model was subtracted from the visibility data." (2 Extracting and calibrating ALMA calibrator data)
   - software: CASA
   - fitting: _not stated_
   - validation: Maps and visibilities inspected by eye; ~20% of datasets discarded  
  > "This led to the loss of a significant number of datasets ($\approx 20$%)" (2 Extracting and calibrating ALMA calibrator data)
2. **Combine and image data per calibrator**: statwt reweighting, concat, clean to dirty-map rms  
  > "re-calculated the weights of the visibilities of the remaining datasets using statwt" (2 Extracting and calibrating ALMA calibrator data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Detect sources**: SExtractor on non-PB-corrected clean maps within 1.5x PB FWHM, peak >=5 sigma; B6 used where both bands exist  
  > "we selected sources with peak flux densities at least 5$\times$ the r.m.s. noise" (3.1 Source detection)
   - software: SExtractor
   - fitting: _not stated_
   - validation: Multi-band and B3/B4 archival data used to reject jets (S_B3,4 > S_B6,7 discarded)  
  > "We have, however, discarded from our sample any submm detections with $S_{\rm B3,B4} > S_{\rm B6,B7}$." (3.4 Caveats)
4. **Measure flux densities**: Re-clean in a 1.5'' box, impbcor, imfit in the PB-corrected map  
  > "the flux densities and uncertainties were then determined in the PB-corrected maps using imfit, with the same box used during cleaning" (3.2 Source catalogue)
   - software: CASA
   - fitting: imfit  
  > "the flux densities and uncertainties were then determined in the PB-corrected maps using imfit, with the same box used during cleaning." (3.2 Source catalogue)
   - validation: _not stated_
5. **Completeness and flux boosting simulations**: Inject point sources of 0.1-10 mJy in steps of 0.025 mJy in the uv plane, 100 repeats per flux, recover with SExtractor at >=5 sigma  
  > "inserted artificial, point-like sources with flux densities ranging from 0.1 to 10 mJy in steps of 0.025 mJy" (3.6 Completeness)
   - software: CASA, SExtractor
   - fitting: _not stated_
   - validation: S_out/S_in ~1 for >10 sigma  
  > "$S_{\rm out} / S_{\rm in} \sim 1$ for sources detected at $>10\sigma$" (3.8 Flux boosting)
6. **Effective area and cumulative counts**: Compute r_lim where SNR falls to 5 per map; counts N(>S)=sum (1-f_sp)/(C*A), with f_sp=0  
  > "the fraction of spurious sources is expected to be zero: $f_{\rm sp} = 0$ for any $S_i$." (4 Number counts)
   - fitting: _not stated_
   - validation: Compared with literature ALMA counts  
  > "It can be seen from the left panel of Figure [5](#fig_number_counts) that the cumulative 1.2-mm number counts we obtain at the present stage of the survey are lower than previous claims." (4 Number counts)

## Software

- **CASA** : calibration, imaging, statwt, concat, impbcor, imfit  
  > "The analysis of all interferometric data presented in this paper has been carried out with the Common Astronomy Software Applications" (Acknowledgements)
- **SExtractor** : source detection  
  > "our source detection has been performed using SExtractor (cite: Bertin1996) on the clean maps" (3.1 Source detection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DSFGs detected in B6 | 8 | not stated | sources | 3 | we have found eight and 11 submm detections in B6 and B7, respectively |
| DSFGs detected in B7 | 11 | not stated | sources | 3 | we have found eight and 11 submm detections in B6 and B7, respectively |
| Cumulative count N(>0.4 mJy) at 870 um | 17.0 | +14.3/-14.0 (as tabulated) | x10^3 deg^-2 | 6 | / 0.4 / $17.0^{14.3}_{14.0}$ / |
| Cumulative count N(>0.2 mJy) at 1.2 mm | 5.6 | +4.7/-4.6 (as tabulated) | x10^3 deg^-2 | 6 | / 0.2 / $5.6^{4.7}_{4.6}$ / |
| Area covered B6 / B7 | ~16 / ~6 | not stated | arcmin^2 | 6 | the total area covered in B6 (around $16 \, {\rm arcmin^2}$) is considerably higher than that covered in B7 (around $6 \, {\rm arcmin^2}$) |
| Completeness at SNR>=7 / >=6 | ~100% / ~80% | not stated | percent | 5 | our survey is nearly 100% complete at ${\rm SNR} \geq 7$ and $\sim$80% complete at ${\rm SNR} \geq 6$ |
| Flux boosting at SNR~5 | up to 20% | not stated | percent | 5 | the flux density is over-estimated by up to 20% for sources detected at ${\rm SNR} \sim 5$ |

## Qualitative findings

- Faintest DSFGs would be missed by the deepest Herschel surveys  
  > "our faintest DSFGs would not have been detected by the deepest survey carried out by *Herschel*" (3.2 Source catalogue)

## Claim tuples

- H: Calibrator fields can yield a deep, wide submm survey of faint DSFGs | E: Combine archival B6/B7 calibrator data for 69 pointings, subtract calibrator, detect at >=5 sigma | R: 8 (B6) and 11 (B7) DSFGs found, down to ~0.2 mJy at 1.2 mm | F: The method works; dynamic range is not a strong limitation | **supported**
- H: Faint number counts agree with previous ALMA estimates | E: Cumulative counts corrected for completeness and area, compared with the literature | R: Counts lower by a factor of at least 2 | F: Earlier counts, based on lower-SNR thresholds, are probably overestimated | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Conservative 5 sigma threshold to avoid spurious sources so that multi-band follow-up is reliable  
  > "we have opted to be conservative – to reduce as much as possible the contamination from spurious sources" (3.5 Spurious sources)
- How they decided it was enough: _not stated_
- Limitation (authors): Possible jet contamination and a possible low-level bias from over-densities around calibrators  
  > "we concede that selection of DSFGs around bright submm calibrators may be biased at a low level" (3.4 Caveats)
- Caveat (inferred, ours): Small samples (8 and 11 sources) give large Poisson errors
- Caveat (inferred, ours): Deboosting method is not specified
- Caveat (inferred, ours): The 870 um to 1.2 mm conversion depends on an assumed SED and z=2.3
- Caveat (inferred, ours): Calibrator-subtraction residuals could cause spurious detections

## Reproducibility

- Data public (paper): Public ALMA calibrator data from the archive; some proprietary data obtained via helpdesk  
  > "For datasets outside the proprietary time period, we retrieved the full data deliveries from the ALMA archive." (2 Extracting and calibrating ALMA calibrator data)
- Products in archive: _not stated_
- Missing: Project and execution block list
- Missing: Detailed clean and SExtractor parameters
- Missing: Deboosting prescription
- Data volume (inferred): Large: hundreds of GB to TB of archival measurement sets for 69 fields
- Score (inferred): 3/5, The data are public and the recipe is outlined, but the dataset selection and imaging parameters are missing.
- Rediscovery candidate: no, Dataset selection and key parameters are not given, and the data volume is large.

## Links

- Related: ALMACAL
- Related: LESS

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00076.S",
  "2012.1.00080.S",
  "2012.1.00088.S",
  "2012.1.00090.S",
  "2012.1.00123.S",
  "2012.1.00175.S",
  "2012.1.00225.S",
  "2012.1.00242.S",
  "2012.1.00275.S",
  "2012.1.00374.S",
  "2012.1.00391.S",
  "2012.1.00453.S",
  "2012.1.00463.S",
  "2012.1.00469.S",
  "2012.1.00501.S",
  "2012.1.00523.S",
  "2012.1.00566.S",
  "2012.1.00602.S",
  "2012.1.00608.S",
  "2012.1.00610.S",
  "2012.1.00619.S",
  "2012.1.00635.S",
  "2012.1.00650.S",
  "2012.1.00676.S",
  "2012.1.00688.S",
  "2012.1.00719.S",
  "2012.1.00729.S",
  "2012.1.00756.S",
  "2012.1.00759.S",
  "2012.1.00762.S",
  "2012.1.00781.S",
  "2012.1.00786.S",
  "2012.1.00789.S",
  "2012.1.00869.S",
  "2012.1.00882.S",
  "2012.1.00900.S",
  "2012.1.00915.S",
  "2012.1.00932.S",
  "2012.1.00953.S",
  "2012.1.00984.S",
  "2012.1.00988.S",
  "2012.1.00997.S",
  "2012.A.00040.S",
  "2013.1.00020.S",
  "2013.1.00032.S",
  "2013.1.00033.S",
  "2013.1.00034.S",
  "2013.1.00047.S",
  "2013.1.00092.S",
  "2013.1.00096.S",
  "2013.1.00099.S",
  "2013.1.00100.S",
  "2013.1.00122.S",
  "2013.1.00139.S",
  "2013.1.00164.S",
  "2013.1.00170.S",
  "2013.1.00226.S",
  "2013.1.00229.S",
  "2013.1.00244.S",
  "2013.1.00278.S",
  "2013.1.00280.S",
  "2013.1.00331.S",
  "2013.1.00395.S",
  "2013.1.00403.S",
  "2013.1.00437.S",
  "2013.1.00448.S",
  "2013.1.00449.S",
  "2013.1.00468.S",
  "2013.1.00521.S",
  "2013.1.00523.S",
  "2013.1.00526.S",
  "2013.1.00534.S",
  "2013.1.00576.S",
  "2013.1.00668.S",
  "2013.1.00694.S",
  "2013.1.00783.S",
  "2013.1.00803.S",
  "2013.1.00815.S",
  "2013.1.00861.S",
  "2013.1.00879.S",
  "2013.1.00884.S",
  "2013.1.00902.S",
  "2013.1.00989.S",
  "2013.1.00999.S",
  "2013.1.01004.S",
  "2013.1.01013.S",
  "2013.1.01052.S",
  "2013.1.01102.S",
  "2013.1.01153.S",
  "2013.1.01166.S",
  "2013.1.01172.S",
  "2013.1.01231.S",
  "2013.1.01239.S",
  "2013.1.01268.S",
  "2013.1.01292.S"
 ],
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
