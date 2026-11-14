# ALMACAL VII: first interferometric number counts at 650 μm

`2020MNRAS.495.2332K` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Klitsch, A. | arXiv: 2005.01733 | DOI: 10.1093/mnras/staa1315

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, cosmology
- Question: What are the interferometric 650 micron cumulative number counts of dusty star-forming galaxies from ALMACAL Band 8 calibrator fields, and what fraction of the CIB do they resolve?  
  > "Here, we present interferometric 650$\mu$m submillimetre number counts." (abstract); "We assess what fraction of the cosmic infrared background (CIB) is resolved by our observations." (4.2 Resolving the 650$\mu$m Background Light)
- Target **81 ALMA calibrator fields (ALMACAL Band 8)**: coordinates _not stated_; z/distance calibrator redshifts in Table (e.g. 0.00512 to 2.25)  
  > "The observed fields are distributed quasi-randomly on the sky visible from the Atacama desert." (2 ALMACAL Data Reduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00020.S
- bands: Band 8 (385 – 500 GHz), mean wavelength 650 μm; Band 6 and 7 used for SEDs  
  > "All ALMA calibration data using Band 8 (385 – 500 GHz) are included in our dataset comprising a total of 112h of observing time." (2 ALMACAL Data Reduction); "The mean wavelength of all ALMACAL observations in Band 8 used here is 650$\mu$m." (2 ALMACAL Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.34'' - 0.98'' (median 0.53'')  
  > "resolutions of $0.34\ensuremath{''} - 0.98\ensuremath{''}$ with a median of $0.53\ensuremath{''}$" (2 ALMACAL Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 47 - 1022 μJy/beam, median 187 μJy/beam  
  > "We reach noise levels of $47 - 1022\mu$Jy beam$^{-1}$ with a median of $187\mu$Jy beam$^{-1}$" (2 ALMACAL Data Reduction)
- time on source: 112 h total  
  > "comprising a total of 112h of observing time" (2 ALMACAL Data Reduction)
- observing dates: all calibrator observations prior to 2018 December  
  > "We analyse all ALMA calibrator observations prior to 2018 December." (2 ALMACAL Data Reduction)
- pi or archival as stated: archival ALMA calibrator observations  
  > "using archival ALMA calibration observations from the ALMACAL survey" (1 Introduction)
- Other facility **VLA / ATCA**: radio maps to check for jet emission  
  > "we have examined radio images made ourselves from archival Karl G. Jansky Very Large Array (VLA) data, or from published maps" (3.5 Identifying jet emission from calibrators)
- External data: ATCA radio images of calibrators  
  > "particularly the Australia Telescope Compact Array (ATCA) images of (cite: Marshall2005)" (3.5 Identifying jet emission from calibrators) [from (cite: Marshall2005)]
- External data: COBE-FIRAS CIB at 650 μm: (0.22 ± 0.07) MJy/sr  
  > "I_{\nu} (650 \mu {\rm m}) = (0.22 \pm 0.07) {\rm MJy \; sr^{-1}}" (4.2 Resolving the 650$\mu$m Background Light) [from (cite: Fixsen1998)]
- External data: SIDES model number counts  
  > "we scale the semi-empirical and semi-analytical model predictions from (cite: Bethermin2017) and (cite: Lagos2019) to our data points." (4.2 Resolving the 650$\mu$m Background Light) [from (cite: Bethermin2017); (cite: Lagos2019)]

## Processing

### Calibration

- pipeline or manual: no flagging or recalibration; calibrator-subtracted pseudo-continuum visibilities used  
  > "Due to the overall dataset size and complexity, flagging and recalibration are impracticable." (2 ALMACAL Data Reduction)
- casa version: CASA 5.5.0  
  > "version 5.5.0" (2 ALMACAL Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: concat then tclean  
  > "We combine the data for each calibrator using the task concat and image the combined visibilities using the task tclean." (2 ALMACAL Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "A natural weighting scheme is chosen" (2 ALMACAL Data Reduction)
- uv taper: outer taper 0.3''; second set 0.8''  
  > "we set the outer taper to $0.3\ensuremath{''}$" (2 ALMACAL Data Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh  
  > "We define cleaning windows using the automatic masking procedure “auto-multithresh”." (2 ALMACAL Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: impbcor for final flux measurements; detection on uncorrected maps  
  > "for the final flux measurements, we correct for the primary beam attenuation using the task impbcor." (2 ALMACAL Data Reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data retrieval procedure  
  > "The data retrieval is described in detail in (cite: Oteo2016)." (2 ALMACAL Data Reduction) [from (cite: Oteo2016)]

### Not stated but needed to reproduce (our reading)

- cell size and image size for tclean
- clean threshold and niter
- exact weight-selection criterion for observations
- SExtractor configuration parameters
- list of the 81 selected fields/execution blocks
- fitted functional form of the effective area and spurious fraction
- how band 6/7 non-detection upper limits are defined

## Analysis recipe

1. **Select and image data**: Select resolution <1'' and central rms ≲1 mJy/beam, discard poor maps and outlier weights, concat per calibrator, tclean with taper  
  > "we use only fields for which we reach a central rms of $\lesssim 1 {\rm mJy \; beam^{-1}}$ in the combined maps of the same fields" (2 ALMACAL Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: visual inspection of maps  
  > "We visually inspect every map and discard those showing signs of poor calibration" (2 ALMACAL Data Reduction)
2. **Detect sources**: SExtractor on non-PB-corrected maps, ≥4.5σ peak, central 1'' masked  
  > "we use a detection threshold with a peak flux of at least $4.5$ times the r.m.s. noise in the image" (3.1 Source Detection)
   - software: SExtractor
   - fitting: _not stated_
   - validation: inverted maps give highest spurious detection at 4.7σ  
  > "We find that the highest SNR detection in the inverted map is at $4.7 \sigma$." (3.1 Source Detection)
3. **Completeness and flux deboosting**: Inject 20 artificial point sources per map in visibilities, 50 repeats, 2-25 times noise, re-image and recover; bootstrap errors; cubic spline of boosting vs SNR  
  > "We inject 20 sources per map and repeat this procedure 50 times." (3.3 Assessing Sample Completeness); "We resample the measured flux boosting in bins of 0.25 and fit a cubic spline to the mean in each bin." (3.4 Flux Deboosting)
   - software: CASA, SExtractor
   - fitting: cubic spline  
  > "We resample the measured flux boosting in bins of 0.25 and fit a cubic spline to the mean in each bin." (Flux Deboosting)
   - validation: _not stated_
4. **Measure fluxes and classify jets**: Aperture photometry radius 1.5 beam widths in PB-corrected maps; Band 6/7 flux ratios, alignment geometry and radio maps to flag jets  
  > "integrating the signal in a circular aperture with a radius of $1.5$ times the synthesized beam width" (3.5 Source Catalogue)
   - software: CASA
   - fitting: _not stated_
   - validation: 0.8'' maps give consistent fluxes  
  > "We find that within the errors the two flux measurements are consistent and no correction factor needs to be applied." (3.5 Source Catalogue)
5. **Derive cumulative number counts and CIB fraction**: Sum (1-fSP)/(C×A) over the 21 DSFGs; errors from 1000 bootstrap realizations plus Poisson errors (Gehrels) and jet-contamination error; scale SIDES and Shark models to the data and integrate  
  > "The total error is the quadratic sum of the bootstrap and Poissonian errors." (4.1 Number Counts)
   - fitting: models scaled to data points  
  > "we scale the semi-empirical and semi-analytical model predictions from (cite: Bethermin2017) and (cite: Lagos2019) to our data points." (Resolving the 650$\mu$m Background Light)
   - validation: jet classification sensitivity test; cosmic variance estimated ≪5 per cent  
  > "In both cases the cosmic variance is $\ll 5$ per cent." (3.7 Assessing cosmic variance effects)

## Software

- **CASA** 5.5.0: concat, tclean, impbcor  
  > "The data reduction is carried out using the Common Astronomy Software Application (CASA) (cite: McMullin2007) version 5.5.0." (2 ALMACAL Data Reduction)
- **SExtractor** : source detection  
  > "We perform the source detection using SExtractor (cite: Bertin1996)" (3.1 Source Detection)
- **Astropy** : general analysis  
  > "This research made use of Astropy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of DSFGs detected | 21 | not stated | sources | 2 | we have classified 21 sources as likely DSFGs, seven potential jets and ten jets. |
| Effective area | ~5.5 | not stated | arcmin^2 | 0 | We reach an effective area of $\sim 5.5$ arcmin$^2$ for a flux density of $\geqslant 5$ mJy |
| Mean flux boosting at 4.5σ | ~38 | not stated | per cent | 3 | the flux density for sources detected at $4.5 \sigma$ is boosted on average by $\sim 38$ per cent |
| Completeness | 100 per cent at SNR≥9; 50 per cent at SNR≥5 | not stated | per cent | 3 | Our survey is 100 per cent complete at a SNR $\geq 9$ and 50 per cent complete at an SNR $\geq 5$. |
| log N(>0.67 mJy) | 4.8 | ±4.7 | log deg^-2 | 5 | / 0.67        / $4.8\pm 4.7$                 / |
| Integrated intensity at 650 μm (SIDES scaled) | 0.34 | +0.26/-0.27 | MJy/sr | 5 | I_{\nu} (650 \mu {\rm m}) = 0.34 ^{+0.26}_{-0.27} {\rm MJy \; sr^{-1}} |
| CIB fraction resolved | 150 and 130 | ±120 and ±100 | per cent | 5 | we are resolving $150 \pm 120$ or $130 \pm 100$ per cent for the two models, respectively. |

## Qualitative findings

- DSFGs are not measurably clustered around the calibrators.  
  > "We find that our detected sample of DSFGs is not measurably clustered around the central calibrator" (3.6 Clustering of Sources)

## Claim tuples

- H: Interferometric 650 μm counts can be measured from ALMACAL Band 8 data free of blending | E: Detected sources at 4.5σ in 81 fields, corrected for completeness, area and boosting | R: 21 DSFGs ≥0.7 mJy; counts lie between 450 and 850 μm counts | F: First interferometric 650 μm number counts, consistent with SIDES and Shark | **supported**
- H: The detected population resolves the CIB at 650 μm | E: Integrated scaled models and compared to COBE-FIRAS | R: 150±120 or 130±100 per cent resolved | F: Majority of CIB resolved, though uncertainties are large | **partially**
- H: Calibrator jets and clustering contaminate the counts | E: Band ratios, alignment, radio maps, radial distribution | R: 17 jets or potential jets removed; no clustering found | F: Residual contamination by jets and lensing remains possible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Using calibrators avoids cosmic variance via many random sight lines.  
  > "present the first short wavelength number counts at $650\mu$m free of blending and cosmic variance" (Summary and Conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): Residual jet contamination and lensing remain possible; small survey area limits constraint on shape of counts.  
  > "A larger survey area would be beneficial to pin down the exact shape of the number counts at this wavelength." (Summary and Conclusion)
- Caveat (inferred, ours): Only two cumulative count points with very large errors
- Caveat (inferred, ours): Uncertainties on resolved CIB fraction exceed 100 per cent
- Caveat (inferred, ours): Cosmic variance estimate is model-based and may be underestimated for sight lines around blazars
- Caveat (inferred, ours): Weights could not be recalculated for pseudo-continuum data
- Caveat (inferred, ours): Jet classification partly subjective, 40 per cent effect in the lower flux bin

## Reproducibility

- Data public (paper): archival ALMA data  
  > "using archival ALMA calibration observations from the ALMACAL survey" (1 Introduction)
- Products in archive: _not stated_
- Missing: exact list of selected execution blocks
- Missing: SExtractor and tclean parameters
- Missing: per-field effective area and spurious fraction functions
- Data volume (inferred): Large: hundreds of GB to a few TB of pseudo-continuum visibilities across ~90 projects
- Score (inferred): 3/5, Data public and the recipe is described in good detail, but many settings are missing and data selection is heavy.
- Rediscovery candidate: no, Large heterogeneous archival dataset with unspecified selection and parameters; main results are loosely constrained.

## Links

- Method: (cite: Oteo2016) (ALMACAL data retrieval and earlier number counts method)
- Related: ALMACAL

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00048.S",
  "2013.1.00061.S",
  "2013.1.00071.S",
  "2013.1.00139.S",
  "2013.1.00170.S",
  "2013.1.00180.S",
  "2013.1.00227.S",
  "2013.1.00244.S",
  "2013.1.00368.S",
  "2013.1.00433.S",
  "2013.1.00448.S",
  "2013.1.00525.S",
  "2013.1.00527.S",
  "2013.1.00576.S",
  "2013.1.00749.S",
  "2013.1.00907.S",
  "2013.1.01010.S",
  "2013.1.01052.S",
  "2013.1.01099.S",
  "2013.1.01202.S",
  "2013.1.01230.S",
  "2015.1.00019.S",
  "2015.1.00025.S",
  "2015.1.00384.S",
  "2015.1.00420.S",
  "2015.1.00612.S",
  "2015.1.00631.S",
  "2015.1.00650.S",
  "2015.1.00656.S",
  "2015.1.00662.S",
  "2015.1.00717.S",
  "2015.1.00736.S",
  "2015.1.00770.S",
  "2015.1.00847.S",
  "2015.1.00942.S",
  "2015.1.01040.S",
  "2015.1.01133.S",
  "2015.1.01137.S",
  "2015.1.01163.S",
  "2015.1.01191.S",
  "2015.1.01486.S",
  "2015.1.01487.S",
  "2015.1.01518.S",
  "2015.1.01597.S",
  "2015.A.00018.S",
  "2015.A.00026.S",
  "2016.1.00089.S",
  "2016.1.00226.S",
  "2016.1.00234.S",
  "2016.1.00262.S",
  "2016.1.00263.S",
  "2016.1.00284.S",
  "2016.1.00333.S",
  "2016.1.00346.S",
  "2016.1.00441.S",
  "2016.1.00668.S",
  "2016.1.00805.S",
  "2016.1.00954.S",
  "2016.1.01093.S",
  "2016.1.01137.S",
  "2016.1.01253.S",
  "2016.1.01285.S",
  "2016.1.01293.S",
  "2016.1.01313.S",
  "2016.1.01399.S",
  "2016.1.01613.S",
  "2017.1.00005.S",
  "2017.1.00025.S",
  "2017.1.00043.S",
  "2017.1.00078.S",
  "2017.1.00118.S",
  "2017.1.00190.S",
  "2017.1.00201.S",
  "2017.1.00239.S",
  "2017.1.00337.S",
  "2017.1.00345.S",
  "2017.1.00370.S",
  "2017.1.00467.S",
  "2017.1.00508.S",
  "2017.1.00586.S",
  "2017.1.00753.S",
  "2017.1.00775.S",
  "2017.1.00814.S",
  "2017.1.00984.S",
  "2017.1.01052.S",
  "2017.1.01195.S",
  "2017.1.01209.S",
  "2017.1.01457.S",
  "2017.A.00024.S",
  "2017.A.00047.T",
  "2018.1.00065.S",
  "2018.1.00649.S"
 ],
 "codes_printed_but_missing": [
  "2013.1.00048.S",
  "2013.1.00061.S",
  "2013.1.00071.S",
  "2013.1.00139.S",
  "2013.1.00170.S",
  "2013.1.00180.S",
  "2013.1.00227.S",
  "2013.1.00244.S",
  "2013.1.00368.S",
  "2013.1.00433.S",
  "2013.1.00448.S",
  "2013.1.00527.S",
  "2013.1.00535.S",
  "2013.1.00576.S",
  "2013.1.00749.S",
  "2013.1.00907.S",
  "2013.1.01010.S",
  "2013.1.01052.S",
  "2013.1.01099.S",
  "2013.1.01202.S",
  "2013.1.01230.S",
  "2015.1.00019.S",
  "2015.1.00035.S",
  "2015.1.00384.S",
  "2015.1.00420.S",
  "2015.1.00612.S",
  "2015.1.00631.S",
  "2015.1.00650.S",
  "2015.1.00656.S",
  "2015.1.00662.S",
  "2015.1.00717.S",
  "2015.1.00736.S",
  "2015.1.00770.S",
  "2015.1.00847.S",
  "2015.1.00942.S",
  "2015.1.01040.S",
  "2015.1.01133.S",
  "2015.1.01137.S",
  "2015.1.01163.S",
  "2015.1.01191.S",
  "2015.1.01486.S",
  "2015.1.01487.S",
  "2015.1.01518.S",
  "2015.1.01597.S",
  "2015.A.00018.S",
  "2015.A.00026.S",
  "2016.1.00089.S",
  "2016.1.00226.S",
  "2016.1.00234.S",
  "2016.1.00262.S",
  "2016.1.00263.S",
  "2016.1.00284.S",
  "2016.1.00333.S",
  "2016.1.00346.S",
  "2016.1.00441.S",
  "2016.1.00668.S",
  "2016.1.00805.S",
  "2016.1.00954.S",
  "2016.1.01093.S",
  "2016.1.01137.S",
  "2016.1.01253.S",
  "2016.1.01285.S",
  "2016.1.01293.S",
  "2016.1.01313.S",
  "2016.1.01399.S",
  "2016.1.01613.S",
  "2017.1.00005.S",
  "2017.1.00025.S",
  "2017.1.00043.S",
  "2017.1.00078.S",
  "2017.1.00118.S",
  "2017.1.00190.S",
  "2017.1.00201.S",
  "2017.1.00239.S",
  "2017.1.00337.S",
  "2017.1.00345.S",
  "2017.1.00370.S",
  "2017.1.00467.S",
  "2017.1.00508.S",
  "2017.1.00586.S",
  "2017.1.00753.S",
  "2017.1.00775.S",
  "2017.1.00814.S",
  "2017.1.00984.S",
  "2017.1.01052.S",
  "2017.1.01195.S",
  "2017.1.01209.S",
  "2017.1.01457.S",
  "2017.A.00024.S",
  "2017.A.00047.T",
  "2018.1.00065.S",
  "2018.1.00649.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 38,
  "rate": 0.559
 },
 "evidence_ok": true
}
```
