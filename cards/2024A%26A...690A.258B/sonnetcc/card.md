# ALMACAL: XII. Data characterisation and products

`2024A&A...690A.258B` | Astronomy and Astrophysics 2024 | first author: Bollo, Victoria | arXiv: 2409.07166 | DOI: 10.1051/0004-6361/202450336

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, agn_and_quasars, cosmology
- Question: Characterise the ALMACAL-22 survey of ALMA calibrator fields: calibration, pruned-sample selection, cube building, and survey properties (area, sensitivity, resolution, integration time, calibrator redshift)  
  > "As part of the strategy to exploit this large dataset, we present the details of processing and imaging data, along with different tests, to ensure the best quality of the sample selection." (1 Introduction); "Here, we provide the characteristics and properties of this new dataset." (1 Introduction)
- Target **ALMA calibrator fields (1047 in full sample, 401 in pruned sample)**: coordinates _not stated_; z/distance median z = 0.749 (max 3.788) full sample; median z = 0.797 (max 3.591) pruned sample  
  > "Out of the initial 1047 sources, 675 have robust redshifts and spectra." (3.4 Redshift); "The full sample of calibrators has a median redshift of $z = 0.749$, with a maximum of $z=3.788$." (3.4 Redshift); "The ALMACAL Redshift Catalogue relies primarily on a redshift database introduced by (cite: bonatoALMACALIVCatalogue2018a) for a substantial portion of the calibrator sample." (3.4 Redshift); distance from Bonato et al. 2018 redshift database, NED, SIMBAD, Mahony et al. 2011, VLT/X-Shooter spectra  
  > "Out of the initial 1047 sources, 675 have robust redshifts and spectra." (3.4 Redshift); "The full sample of calibrators has a median redshift of $z = 0.749$, with a maximum of $z=3.788$." (3.4 Redshift); "The ALMACAL Redshift Catalogue relies primarily on a redshift database introduced by (cite: bonatoALMACALIVCatalogue2018a) for a substantial portion of the calibrator sample." (3.4 Redshift)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 through Band 10 (full sample); Band 3 to Band 9 in the pruned sample (no Band 10)  
  > "This paper presents 1047 calibration field data points accumulated from Cycle 1 (July 2012 - May 2022) from Band 3 through Band 10, resulting in a dataset of more than 30 Terabytes." (2 ALMA calibrator data); "There are no Band 10 data available in the pruned sample." (2.2 Pruned sample selection)
- frequencies and spectral setup: Observations with overlapping frequency coverage are grouped in 1 GHz bins; cube channel width 31.2 MHz  
  > "We chose bins of 1 GHz to select all the files spanning the same frequency across the extent of the ALMA band’s frequency coverage." (2.2 Pruned sample selection); "We defined the channel width for all cubes to be 31.2 MHz, a value selected to strike a balance between spectral resolution, S/N, and manageable data volume." (2.3 Building cubes)
- continuum bandwidth: _not stated_
- arrays: 12-metre array only (pruned sample)  
  > "The pruned sample includes only observations made with the 12-metre array." (2.2 Pruned sample selection)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Full sample median 1.14 arcsec in Band 3 down to 0.13 arcsec in Band 10; pruned sample Band 4 median 0.87 arcsec, mean 0.23 arcsec in Band 9  
  > "In the ALMACAL$-22$ full sample, the median value in Band 3 is 1.14 arcsec." (3.2 Spatial resolution); "reaching a median spatial resolution of 0.13 arcsec in Band 10." (3.2 Spatial resolution); "Band 4 shows the maximum value in the median spatial resolution of 0.87 arcsec." (3.2 Spatial resolution)
- max recoverable scale: _not stated_
- sensitivity: mean ~0.78 mJy/beam in the pruned sample  
  > "The mean sensitivity value reached in the pruned sample is $\sim0.78$ mJy/beam" (3.3 Integration time)
- time on source: Pruned sample requires at least 10 minutes per frequency; median 0.78 h (full) and 0.48 h (pruned), max up to 7 h pruned  
  > "We imposed a lower limit of 10 minutes for the pruned sample across the whole frequency coverage." (3.3 Integration time); "The median value in the full sample is 0.78 hours; in the pruned sample, it is 0.48 hours." (3.3 Integration time)
- observing dates: Cycle 1 (July 2012) to May 2022  
  > "accumulated from Cycle 1 (July 2012 - May 2022)" (2 ALMA calibrator data)
- pi or archival as stated: Archival calibration data from every ALMA science project  
  > "The ALMACAL$-22$ survey comprises archival data compiled from the calibration data used in every science project carried out by ALMA" (2 ALMA calibrator data)
- Other facility **VLT/X-Shooter**: Optical spectroscopy of calibrator sources for the redshift catalogue  
  > "This catalogue is also supplemented by VLT/X-Shooter observations of calibrator sources (ID 111.253L.001, PI: S. Weng and ID 0101.A-0528, PI: E. Mahony)." (3.4 Redshift)
- Other facility **NED, SIMBAD and an optical catalogue of bright GHz sources (Mahony et al. 2011)**: Optical cross-matches used to enrich the calibrator redshift compilation  
  > "This compilation was further enriched after cross-matching radio sources with optical sources from NED, SIMBAD (cite: wengerSIMBADAstronomicalDatabase2000), and an optical catalogue of bright sources at gigahertz frequencies (cite: mahonyOpticalPropertiesHighfrequency2011)." (3.4 Redshift)
- External data: Redshift database for a substantial portion of the calibrators  
  > "The ALMACAL Redshift Catalogue relies primarily on a redshift database introduced by (cite: bonatoALMACALIVCatalogue2018a) for a substantial portion of the calibrator sample." (3.4 Redshift) [from (cite: bonatoALMACALIVCatalogue2018a)]
- External data: Sky coverage and sensitivity values of other surveys (ASPECS, COLDz, GOODS-ALMA, AS2UDS, DYNAMO) used for comparison in Fig. 7  
  > "we also plotted the sky coverage and sensitivity values reached by other surveys (cite: lenkicCOExcitationHighz2023; riechersCOLDzShapeCO2019; decarliALMASpectroscopicSurvey2019; gomez-guijarroGOODSALMASourceCatalog2022; stachALMASurveySCUBA22019)" (4.1 Survey area and sensitivity) [from (cite: lenkicCOExcitationHighz2023; riechersCOLDzShapeCO2019; decarliALMASpectroscopicSurvey2019; gomez-guijarroGOODSALMASourceCatalog2022; stachALMASurveySCUBA22019)]

## Processing

### Calibration

- pipeline or manual: Dedicated ALMACAL pipeline built on the delivered scriptForPI.py calibration scripts, followed by self-calibration  
  > "A dedicated ALMACAL pipeline was created to automate the processing of all delivered datasets." (2.1 Calibration); "Next, we applied self-calibration to correct the short-time variability of the phase and amplitude during integration, improving the final image’s dynamic range." (2.1 Calibration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Flux density scale of bandpass calibrators recovered from the flux calibration table of standardised calibrator values  
  > "the accurate flux density scale of the bandpass calibrators has to be recovered from the flux calibration table containing standardised values for each calibrator." (2.1 Calibration)
- flux scale uncertainty: _not stated_
- self calibration: Two steps on pseudo-continuum MS (phase only, then amplitude and phase); solution interval equal to the integration time; point-source model fitted to the uv data  
  > "These files facilitate the implementation of two steps of self-calibration, initially focusing solely on phase and subsequently incorporating both amplitude and phase calibration." (2.1 Calibration); "The solution interval for the calibration solution is set equal to the integration time." (2.1 Calibration); "During the intervals of the self-calibration steps, a point source model is applied and fitted to the uv data." (2.1 Calibration)

### Imaging

- task: CASA tclean with linear interpolation  
  > "Finally, we ran `tclean` in `CASA` for imaging using linear interpolation, natural weighting to optimise sensitivity, and 0.5 arcsec tapering." (2.3 Building cubes)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Finally, we ran `tclean` in `CASA` for imaging using linear interpolation, natural weighting to optimise sensitivity, and 0.5 arcsec tapering." (2.3 Building cubes)
- uv taper: 0.5 arcsec  
  > "Finally, we ran `tclean` in `CASA` for imaging using linear interpolation, natural weighting to optimise sensitivity, and 0.5 arcsec tapering." (2.3 Building cubes)
- cell size: synthesised beam / 3 (3 pixels per beam)  
  > "We sampled each beam with 3 pixels (using a pixel scale = synthesised beam / 3)" (2.3 Building cubes)
- image size: ~1.8 times the primary beam, using the number of pixels recommended by CASA  
  > "picked the image size to be $\sim1.8$ times that of the primary beam, selecting the number of pixels recommended by `CASA` to maximise the imaging efficiency." (2.3 Building cubes)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Calibrator continuum modelled as a point source and subtracted in the uv plane to build line cubes  
  > "The final step involves deriving the calibrated visibilities and subtracting the continuum of the calibrator source to build line emission data cubes" (2.1 Calibration)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Observations with sequential frequencies concatenated into one MS per cube, then statwt reweighting  
  > "First, we concatenated all the uv observations into a single file to obtain a data cube." (2.3 Building cubes); "Then we applied the `CASA` task `statwt` to the concatenated file to recalibrate the uv weighting of different observations based on the variance of data." (2.3 Building cubes)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Full ALMACAL calibration pipeline description  
  > "The complete pipeline description is available in (cite: oteoALMACALExploitingALMA2016), and the following is a brief overview of its essential components." (2.1 Calibration) [from (cite: oteoALMACALExploitingALMA2016)]
- Theoretical sensitivity calculation as in the ALMA Interferometric Pipeline  
  > "This function calculates the point source sensitivity in imaged cubes, accounting for image weights and visibility weights" (2.2 Pruned sample selection) [from (cite: hunterALMAInterferometricPipeline2023)]
- Redshift catalogue details deferred to a forthcoming paper  
  > "Further details will be presented in a forthcoming paper (Weng et al., in prep.)." (3.4 Redshift) [from Weng et al., in prep.]

### Not stated but needed to reproduce (our reading)

- The ALMACAL pipeline code itself (only referenced to Oteo et al. 2016 and not released here)
- Self-calibration solution interval in seconds and the point-source fitting recipe, plus any flagging applied
- tclean deconvolver, niter, threshold, masking and primary-beam-correction settings
- Exact gridder/imaging parameters beyond natural weighting and 0.5 arcsec taper (e.g. nchan, start, restfreq, specmode, interpolation reference frame)
- Which ms files and cubes constitute the pruned sample (list of MOUS/execution blocks) and the visual-rejection decisions
- Version of CASA and analysisUtils used
- Definition of the 'area' calculation (overlap handling, combination across cubes of the same field/band)
- Source of the continuum-image parameters used for the RMS criterion (image size, cell, bandwidth)

## Analysis recipe

1. **Calibrate and remove the calibrator continuum**: Run the delivered scriptForPI.py, self-calibrate on pseudo-continuum data with a point-source model, then subtract the model to leave blank-sky line cubes  
  > "This process enabled us to create a model and remove the bright calibrator from the visibility data, resulting in the equivalent of blank sky or deep field observations." (2.1 Calibration)
   - software: CASA, ALMACAL pipeline
   - parameter: Two self-calibration steps: phase-only, then amplitude and phase  
  > "These files facilitate the implementation of two steps of self-calibration, initially focusing solely on phase and subsequently incorporating both amplitude and phase calibration." (2.1 Calibration)
   - parameter: Solution interval equal to the integration time  
  > "The solution interval for the calibration solution is set equal to the integration time." (2.1 Calibration)
   - assumption: Calibrator is a point source, subtracted independently per observation to mitigate flux variability  
  > "This approach offers the advantage of subtracting the point-source model independently for each observation, mitigating the impact of any flux variability in the calibration source." (2.1 Calibration)
   - fitting: _not stated_
   - validation: _not stated_
2. **Select the pruned sample**: Keep 12-m data; image continuum per MS; cut on absolute RMS and on ratio of measured to theoretical RMS; visually inspect continuum maps; require at least 10 min integration per frequency  
  > "First, we created the continuum image for each measurement set using `CASA` and estimated the root-mean-square (RMS) noise." (2.2 Pruned sample selection); "After removing $\sim 15 \%$ of the files, we combined the data with the same frequency coverage, selecting observations that contribute to a total integration time of at least 10 minutes." (2.2 Pruned sample selection)
   - software: CASA, apparentsens
   - parameter: Reject RMS above 1e-5 Jy  
  > "We excluded files with an RMS value higher than $10^{-5}$ Jy, which introduced inconsistent noise patterns throughout the cube." (2.2 Pruned sample selection)
   - parameter: Measured RMS / theoretical sensitivity must not exceed a factor of 3  
  > "We insist that the measured RMS of each continuum imaged file compared with the theoretical sensitivity (ALMA pipeline) should not be greater than a factor of 3." (2.2 Pruned sample selection)
   - parameter: Visual rejection of stripes, blurring, shifted or elongated sources, ~15% of files removed  
  > "We visually identified the presence of stripes, blurring, artificial elongation or shifting of sources, and symmetric or asymmetric patterns, then discarded observations exhibiting these issues to ensure data quality." (2.2 Pruned sample selection)
   - assumption: Continuum image RMS is a good proxy for data quality, cheaper than cube imaging  
  > "We chose to use the continuum image instead of the data cube because imaging the continuum is much faster and provides a good approximation of the quality of the files." (2.2 Pruned sample selection)
   - fitting: _not stated_
   - validation: Inspected a few files removed by the RMS criterion; most showed strong interferometric patterns or calibration errors  
  > "We inspected a few files that were removed by the RMS criteria and found that most of them had strong interferometric patterns or errors in calibration." (2.2 Pruned sample selection)
3. **Build data cubes**: Concatenate sequential-frequency MS, reweight with statwt, set cell and image size from the synthesised beam and primary beam, image with tclean  
  > "First, we concatenated all the uv observations into a single file to obtain a data cube." (2.3 Building cubes); "We estimated the beam size using the `CASA` task `getsynthesizedbeam` from the `analysisUtils` package." (2.3 Building cubes)
   - software: CASA, tclean, statwt, analysisUtils
   - parameter: Channel width 31.2 MHz  
  > "We defined the channel width for all cubes to be 31.2 MHz, a value selected to strike a balance between spectral resolution, S/N, and manageable data volume." (2.3 Building cubes)
   - parameter: Natural weighting, 0.5 arcsec taper, linear interpolation  
  > "Finally, we ran `tclean` in `CASA` for imaging using linear interpolation, natural weighting to optimise sensitivity, and 0.5 arcsec tapering." (2.3 Building cubes)
   - parameter: Pixel scale = synthesised beam / 3; image size ~1.8 times the primary beam  
  > "picked the image size to be $\sim1.8$ times that of the primary beam, selecting the number of pixels recommended by `CASA` to maximise the imaging efficiency." (2.3 Building cubes)
   - parameter: CASA parallelised with eight cores and eight threads  
  > "We parallelised `CASA` using eight cores and eight threads, which reduces by a factor of 4 the execution time of `tclean` for some cubes." (2.3 Building cubes)
   - fitting: _not stated_
   - validation: _not stated_
4. **Characterise survey area, sensitivity, resolution and integration time**: Sum on-source time in a 1 GHz moving window; estimate per-cube sensitivity from integration time and central frequency; area taken as 1.8 times the primary beam per field, counting each field once  
  > "We added up the integration time in a 1 GHz moving window, selecting all the files spanning the same frequency." (3.3 Integration time); "To estimate the sensitivity reached in each data cube, we used the `sensitivity` task from `analysisUtils`, which takes the integration time and central frequency as inputs." (4.1 Survey area and sensitivity)
   - software: CASA, analysisUtils
   - parameter: Area per field is 1.8 times the primary beam size from primaryBeamArcsec  
  > "We considered an area 1.8 times the primary beam size for each field, which we calculated using the `primaryBeamArcsec` function from the `analysisUtils` package in `CASA`." (4.1 Survey area and sensitivity)
   - parameter: Total survey area counts each calibration field once, prioritising the largest area  
  > "The total survey area for both the full and the pruned sample accounts for each calibration field once, prioritising the largest area." (4.1 Survey area and sensitivity)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compile calibrator redshift catalogue**: Combine the Bonato et al. redshift database with NED, SIMBAD and Mahony et al. cross-matches, team member checks and VLT/X-Shooter spectra  
  > "Team members individually checked each source, noting the redshift and provenance." (3.4 Redshift)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare area and sensitivity with other surveys**: Plot survey area versus sensitivity per band for the pruned sample against ASPECS, COLDz, PHIBSS2, GOODS-ALMA and others  
  > "Figure [7](#fig:area_sensitivity) compares the total survey area reached by each band in the pruned ALMACAL$-22$ sample as a function of the sensitivity." (4.1 Survey area and sensitivity)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Continuum and cube imaging, calibration, weighting  
  > "First, we created the continuum image for each measurement set using `CASA` and estimated the root-mean-square (RMS) noise." (2.2 Pruned sample selection)
- **tclean** : Imaging the data cubes  
  > "Finally, we ran `tclean` in `CASA` for imaging using linear interpolation, natural weighting to optimise sensitivity, and 0.5 arcsec tapering." (2.3 Building cubes)
- **statwt** : Reweighting the concatenated visibilities  
  > "Then we applied the `CASA` task `statwt` to the concatenated file to recalibrate the uv weighting of different observations based on the variance of data." (2.3 Building cubes)
- **analysisUtils** : getsynthesizedbeam, primaryBeamArcsec and sensitivity functions  
  > "We estimated the beam size using the `CASA` task `getsynthesizedbeam` from the `analysisUtils` package." (2.3 Building cubes); "To estimate the sensitivity reached in each data cube, we used the `sensitivity` task from `analysisUtils`, which takes the integration time and central frequency as inputs." (4.1 Survey area and sensitivity)
- **apparentsens (CASA image toolkit)** : Theoretical point-source sensitivity of each observation  
  > "by using the `apparentsens` function of the `CASA` image `toolkit`." (2.2 Pruned sample selection)
- **scriptForPI.py** : Generating fully calibrated data from each delivered ALMA dataset  
  > "This pipeline uses the `scriptForPI.py` script included in every delivered ALMA dataset, which generates fully calibrated data." (2.1 Calibration)
- **ALMACAL pipeline** : Automated processing of all delivered datasets  
  > "A dedicated ALMACAL pipeline was created to automate the processing of all delivered datasets." (2.1 Calibration)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Measurement sets in the full sample | 34909 | not stated | dimensionless | 2 | We started from a total of 34909 measurement sets (ms), that is, raw visibility files, of which 25594 add up to at least 10 minutes of integration time. |
| Measurement sets with at least 10 min integration | 25594 | not stated | dimensionless | 2 | We started from a total of 34909 measurement sets (ms), that is, raw visibility files, of which 25594 add up to at least 10 minutes of integration time. |
| Files with acceptable RMS | 15270 | not stated | dimensionless | 2 | Among these, 15270 files have acceptable RMS levels. |
| Measurement sets in the pruned sample | 6494 | not stated | dimensionless | 2 | After removing visual artefacts and reapplying the integration time criterion, we used 6494 ms files to build the pruned sample. |
| Calibrator fields, full and pruned samples | 1047 full; 401 pruned | not stated | dimensionless | 2 | The right panel shows the distribution of calibrators, with 1047 in the full sample and 401 in the pruned sample. |
| Data cubes in the pruned sample | 1508 | not stated | dimensionless | 3 | The pruned sample is composed of 1508 cubes from Band 3 to Band 9. |
| Median measured/theoretical RMS ratio | 1.8 (pruned); 2.4 (full) | not stated | dimensionless | 2 | The pruned sample extends by up to a factor of 3 with a median value of 1.8, while the full sample has a median value of 2.4. |
| Median total integration time per cube | 0.78 (full); 0.48 (pruned) | not stated | hours | 4 | The median value in the full sample is 0.78 hours; in the pruned sample, it is 0.48 hours. |
| Mean sensitivity reached in the pruned sample | ~0.78 | not stated | mJy/beam | 4 | The mean sensitivity value reached in the pruned sample is $\sim0.78$ mJy/beam |
| Median spatial resolution, full sample Band 3 | 1.14 | not stated | arcsec | 4 | In the ALMACAL$-22$ full sample, the median value in Band 3 is 1.14 arcsec. |
| Total survey area, pruned sample | 1154 | not stated | arcmin^2 | 4 | Our pruned sample adds up to a total area of 1154 arcmin$^2$, shown as the light green dashed horizontal line, surpassing the total area covered by previous surveys. |
| Total survey area, full sample | 1887 | not stated | arcmin^2 | 4 | As the dark dashed horizontal line shows, the full sample area over all bands reaches 1887 arcmin$^2$. |
| Median calibrator redshift, full sample | 0.749 (max 3.788) | not stated | dimensionless | 5 | The full sample of calibrators has a median redshift of $z = 0.749$, with a maximum of $z=3.788$. |
| Median calibrator redshift, pruned sample | 0.797 (max 3.591) | not stated | dimensionless | 5 | In the pruned sample, the median redshift value is $z=0.797$, and the maximum is $z=3.591$. |
| Calibrators with robust redshifts and spectra (full) | 675 of 1047 | not stated | dimensionless | 5 | Out of the initial 1047 sources, 675 have robust redshifts and spectra. |
| Pruned-sample calibrators with spectroscopic redshift | 390/635 (61%) | not stated | dimensionless | 5 | For the pruned sample of this work, 390/635 ($61\%$) calibrators have confirmed spectroscopic redshifts. |
| Total data volume of the survey | more than 30 | not stated | TB | 0 | ALMACAL$-22$ is a large survey of ALMA calibrator observations, collecting over 30 TB of data and covering 1047 calibrator fields across the southern sky. |

## Qualitative findings

- Pruning by RMS and visual inspection removes artefact-dominated data without significantly biasing the redshift distribution  
  > "Therefore, we do not expect any significant bias related to redshift in the pruned sample." (3.4 Redshift)
- Two sparsely covered regions in the pruned sample lie near the projection of the Galactic plane  
  > "In the pruned sample, two areas have relatively sparse data." (3.1 Spatial distribution)

## Claim tuples

- H: Can ALMA calibrator data be turned into a homogeneous, high-quality deep-field survey? | E: Self-calibrated and subtracted calibrators, pruned by RMS, theoretical-sensitivity ratio, visual inspection and a 10 min integration cut, then built 31.2 MHz cubes | R: 401 calibrator fields and 1508 cubes from Band 3 to Band 9 in the pruned sample | F: A pruned sample of the highest-quality data is established | **supported**
- H: Does ALMACAL-22 cover a larger area than previous molecular gas surveys? | E: Summed 1.8 primary-beam areas per field and compared with ASPECS, COLDz, PHIBSS2 | R: Pruned sample area 1154 arcmin^2, full sample 1887 arcmin^2 | F: Footprint larger than any previous survey, helping to mitigate cosmic variance | **supported**
- H: Is the depth of the cubes competitive with existing deep surveys? | E: Estimated per-cube sensitivity with analysisUtils and compared with ASPECS and COLDz | R: Mean pruned sensitivity ~0.78 mJy/beam; wider range in some bands | F: Sensitivity comparable to ASPECS and COLDz in several bands | **partially**
- H: Does pruning bias the calibrator redshift distribution? | E: Compared redshift distributions of full and pruned samples | R: Median z 0.749 (full) vs 0.797 (pruned); high-z end also less populated after pruning | F: No significant redshift bias expected | **supported**

## Reasoning

- Why this data: Repeated calibrator observations form a deep, wide-area, untargeted dataset  
  > "Multiple observations of ALMA calibrators create a high-sensitivity dataset that covers a significant sky area ($> 1000$ arcmin$^2$)." (2 ALMA calibrator data)
- Why this method: Continuum images used for quality screening because they are much faster than cubes  
  > "We chose to use the continuum image instead of the data cube because imaging the continuum is much faster and provides a good approximation of the quality of the files." (2.2 Pruned sample selection)
- Alternative: Inspecting every observation in the uv plane to flag misbehaving antennas was judged infeasible, so continuum maps were inspected instead  
  > "Considering the large amount of data that the ALMACAL$-22$ survey contains, it is not possible to visualise all the observations in the uv plane to flag the possible misbehaved antennas." (2.2 Pruned sample selection)
- How they decided it was enough: _not stated_
- Limitation (authors): Pointed calibrator observations make the survey not truly blind, with possible overdensity biases  
  > "since ALMACAL consists of pointed observations of specific sources, it cannot be considered a truly blind survey, raising concerns about potential biases in cosmic overdensities" (4.1 Survey area and sensitivity)
- Caveat (inferred, ours): Quoted totals are internally inconsistent (area 1100 vs 1154 vs 1887 arcmin^2; Band 10 median resolution 0.13 arcsec in text vs 0.10 in table; 635 vs 401 pruned calibrators in the redshift paragraph)
- Caveat (inferred, ours): RMS cut is an absolute 1e-5 Jy irrespective of band, bandwidth or resolution, and visual rejection is subjective and not reproducible
- Caveat (inferred, ours): No quantitative check of flux-scale accuracy after self-calibration and point-source subtraction (possible residual calibrator flux or extended-jet residuals)
- Caveat (inferred, ours): Cubes are tapered to 0.5 arcsec, degrading resolution relative to the quoted median resolutions
- Caveat (inferred, ours): Area and sensitivity comparison with other surveys uses different depth definitions and a primary-beam-based area without a sensitivity-weighted effective area

## Reproducibility

- Data public (paper): Calibrator data are public in the ALMA archive once the science data pass quality assurance  
  > "These calibrator data are accessible to any user right after the main science dataset has passed quality assurance." (2 ALMA calibrator data)
- Products in archive: Processed cubes are available on request, not in a public archive  
  > "ALMACAL raw data and processed data cubes are available upon reasonable request." (Data Availability)
- Missing: Project and execution-block list defining the full and pruned samples
- Missing: ALMACAL pipeline code and self-calibration parameters
- Missing: tclean deconvolution, masking and threshold settings
- Missing: CASA and analysisUtils versions
- Missing: Visual-inspection rejection list
- Data volume (inferred): More than 30 TB of raw/calibrated visibilities for the full sample; the pruned sample (6494 ms) is a substantial fraction, likely several to ten TB
- Score (inferred): 2/5, ALMA data are public and the processing outline and many imaging parameters are given, but the pipeline is only referenced, the sample list is not published, key tclean and self-calibration settings are missing, and the processed cubes are available only on request
- Rediscovery candidate: no, The recipe is incomplete (no pipeline code, no sample list, deconvolution settings absent) and the visual pruning is subjective, so the survey statistics cannot be exactly redone

## Links

- Method: (cite: oteoALMACALExploitingALMA2016) (Full description of the ALMACAL calibration pipeline)
- Method: (cite: hunterALMAInterferometricPipeline2023) (ALMA Interferometric Pipeline whose theoretical sensitivity calculation is used)
- Method: (cite: mcmullinCASAArchitectureApplications2007) (CASA reference)
- Companion: (cite: hamanowiczALMACALVIIIPilot2022) (ALMACAL-CO pilot blind CO search in 38 calibrator fields)
- Companion: (cite: chenALMACALIXMultiband2022) (Multi-band DSFG number counts from 1001 calibration fields)
- Companion: (cite: bonatoALMACALIVCatalogue2018a) (Calibrator catalogue and redshift database)
- Companion: (cite: klitschALMACALVIMolecular2019) (Absorption line search with 749 calibrators)
- Related: ASPECS
- Related: PHANGS-ALMA
- Related: REBELS
- Related: ALPINE
- Related: CRISTAL
- Related: COLDz
- Related: PHIBSS2
- Related: GOODS-ALMA
- Related: AS2UDS

## Checks

```json
{
 "quotes": 103,
 "quotes_ok": 103,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00193.S",
  "2012.1.00268.S",
  "2012.1.00275.S",
  "2012.1.00303.S",
  "2012.1.00374.S",
  "2012.1.00496.S",
  "2012.1.00743.S",
  "2012.1.01069.S",
  "2012.1.01099.S",
  "2013.1.00111.S",
  "2013.1.00166.S",
  "2013.1.00553.S",
  "2013.1.00645.S",
  "2013.1.00658.S",
  "2013.1.00916.S",
  "2013.1.00988.S",
  "2013.1.01034.S",
  "2013.1.01110.S",
  "2013.1.01175.S",
  "2013.1.01195.S",
  "2015.1.00041.S",
  "2015.1.00188.S",
  "2015.1.00350.S",
  "2015.1.00410.S",
  "2015.1.00530.S",
  "2015.1.00669.S",
  "2015.1.00678.S",
  "2015.1.00856.S",
  "2015.1.00896.S",
  "2015.1.00986.S",
  "2015.1.01005.S",
  "2015.1.01054.S",
  "2015.1.01133.S",
  "2015.1.01222.S",
  "2015.1.01548.S",
  "2015.1.01602.S",
  "2016.1.00115.S",
  "2016.1.00119.S",
  "2016.1.00138.S",
  "2016.1.00447.S",
  "2016.1.00630.S",
  "2016.1.01135.S",
  "2016.1.01164.S",
  "2016.1.01284.S",
  "2016.1.01326.S",
  "2016.1.01398.S",
  "2016.1.01456.S",
  "2017.1.00280.S",
  "2017.1.00321.S",
  "2017.1.00707.S",
  "2017.1.00717.S",
  "2017.1.00941.S",
  "2017.1.00964.S",
  "2017.1.01027.S",
  "2017.1.01093.S",
  "2017.1.01347.S",
  "2017.1.01658.S",
  "2018.1.00035.L",
  "2018.1.00162.S",
  "2018.1.00276.S",
  "2018.1.00306.S",
  "2018.1.00538.S",
  "2018.1.00585.S",
  "2018.1.00781.S",
  "2018.1.00900.S",
  "2018.1.00992.S",
  "2018.1.01038.S",
  "2018.1.01119.S",
  "2018.1.01194.S",
  "2018.1.01241.S",
  "2018.1.01344.S",
  "2018.1.01438.S",
  "2018.1.01617.T",
  "2018.1.01740.S",
  "2018.1.01766.T",
  "2018.1.01812.S",
  "2018.A.00065.T",
  "2019.1.00061.S",
  "2019.1.00130.S",
  "2019.1.00260.S",
  "2019.1.00337.S",
  "2019.1.00397.S",
  "2019.1.00411.S",
  "2019.1.00447.S",
  "2019.1.00458.S",
  "2019.1.00597.S",
  "2019.1.00708.S",
  "2019.1.00801.S",
  "2019.1.01022.S",
  "2019.1.01027.S",
  "2019.1.01118.S",
  "2019.1.01136.S",
  "2019.1.01178.S",
  "2019.1.01190.S",
  "2019.1.01317.S",
  "2019.1.01337.S",
  "2019.1.01422.S",
  "2019.1.01437.S",
  "2019.1.01742.S",
  "2019.1.01813.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 63,
  "rate": 0.685
 },
 "evidence_ok": true
}
```
