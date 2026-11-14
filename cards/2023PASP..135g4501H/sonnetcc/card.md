# The ALMA Interferometric Pipeline Heuristics

`2023PASP..135g4501H` | Publications of the Astronomical Society of the Pacific 2023 | first author: Hunter, Todd R. | arXiv: 2306.07420 | DOI: 10.1088/1538-3873/ace216

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation
- Question: What calibration, flagging, imaging and continuum-channel-finding heuristics does the ALMA interferometric pipeline apply (as of the Cycle 9 release), and how is it tested and validated?  
  > "We describe the calibration and imaging heuristics developed and deployed in the Atacama Large Millimeter/sub-millimeter Array (ALMA) interferometric data processing pipeline, as of ALMA Cycle 9 operations." (abstract)
- Target **massive star-forming region (3-point mosaic, unnamed; used only to illustrate continuum finding)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00314.S, 2017.1.00983.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m array (50 antennas, baseline correlator), 7 m ACA (12 antennas, ACA correlator); pipeline also handles Total Power Array single-dish data  
  > "observations obtained with either the 50-antenna array of 12 m antennas processed on the baseline correlator" (Introduction); "the 12-antenna Atacama Compact Array (ACA) of 7 m antennas processed on the ACA correlator" (Introduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Nobeyama Radio Observatory 45 m telescope**: A pipeline built on the same framework processes NRO 45 m data  
  > "The pipeline framework allows modifications to extend support for other similar observatories, as evidenced by the recently-deployed pipeline to process data from the 45 m telescope of the Nobeyama Radio Observatory" (2.1 Framework)
- External data: ALMA Calibrator Source Catalog: flux densities and spectral indices of grid calibrators queried at processing time  
  > "which are bright sources in the ALMA Calibrator Source Catalog" (3.10 Flux calibrator model); "retrieve the best estimate of the flux density and spectral index at the center frequency of each spw for the date of observation of each EB" (3.3 Data import) [from (cite: Fomalont2014)]
- External data: Solar system object flux calibrator models available in CASA  
  > "Low resolution projects typically observe one object, if available, from a list SSOs for which accurate models exist in CASA" (3.10 Flux calibrator model) [from (cite: ButlerALMAMemo594)]
- Simulation/model as data: CASA atmospheric model tool (ATM) used to predict transmission for low-transmission spw flagging  
  > "The transmission is computed using the atmospheric model tool in CASA, which is based on the package Atmospheric Transmission at Microwaves" (4.1.10 Low transmission)

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline (automated calibration and imaging)  
  > "The ALMA Science Pipeline provides automated calibration and imaging of ALMA interferometric and single-dish data." (Introduction)
- casa version: CASA 6.4.1.12 (Python 3.6)  
  > "we describe the heuristics of the ALMA interferometric data processing pipeline as of the 2022.2.0.64 release for ALMA Cycle 9 (2022 October) based on CASA 6.4.1.12 Python 3.6" (Introduction)
- pipeline version: 2022.2.0.64 (Cycle 9 release)  
  > "we describe the heuristics of the ALMA interferometric data processing pipeline as of the 2022.2.0.64 release for ALMA Cycle 9 (2022 October) based on CASA 6.4.1.12 Python 3.6" (Introduction)
- archive products used as is: _not stated_
- flux calibrator: Solar system object for low-resolution projects, otherwise one of 49 grid quasars from the ALMA calibrator catalog  
  > "ALMA observations choose from two types of flux calibrators depending on the angular resolution of the data." (3.10 Flux calibrator model); "Otherwise, one of the quasars is observed from the list of 49" (3.10 Flux calibrator model)
- flux scale uncertainty: _not stated_
- self calibration: Not part of the 2022 release; optional self-calibration stage expected in the 2023 release  
  > "Initial deployment of an optional self-calibration stage is expected in the 2023 release." (9.2 Self-calibration)

### Imaging

- task: tclean (via the pipeline imaging task) for all imaging stages  
  > "Imaging is performed using the task within the pipeline task" (5.4 General imaging heuristics); "designed to guard against unexpected changes in tclean affecting critical functionality needed for the ALMA pipeline" (8.1 Testing of CASA tasks critical to the pipeline)
- deconvolver: hogbom for continuum mfs; mtmfs (2 Taylor terms) when fractional bandwidth exceeds 0.1  
  > "All continuum imaging uses the multi-frequency synthesis (MFS) algorithm in (cite: Rau2011) with =‘hogbom’ (cite: hogbom1974)." (5.5 MFS continuum imaging); "In cases where the fractional bandwidth of the total frequency range spanned by the image exceeds 0.1, higher order Taylor terms are needed" (5.5 MFS continuum imaging)
- weighting robust: Briggs robust chosen from 0.0, +0.5 (default), +1.0, +2.0: the value closest to +0.5 whose predicted beam area meets the requested range  
  > "four possible values of the weighting parameter (cite: Briggs): 0.0, +0.5 (default), +1.0, and +2.0" (5.2 Image weighting selection)
- uv taper: _not stated_
- cell size: 5 pixels per beam by default; 3.25 or 3.0 under product size mitigation  
  > "change the pixels per beam () from 5 to 3.25 if =+2, or to 3.0 otherwise." (5.3 Product size mitigation)
- image size: _not stated_
- masking: automasking (top-down, residual-image based) for continuum and cubes  
  > "It takes a top-down approach to producing cleaning masks: it uses the residual images to identify significant peaks and then expands the mask to include emission associated with these peaks down to lower signal-to-noise noise." (5.4.5 Automasking for cleaning)
- multiscale scales: _not stated_
- continuum subtraction: Continuum channels identified automatically by the findContinuum algorithm with moment difference analysis, then continuum subtracted before cube imaging  
  > "In the 2020 release, the algorithm to identify channels to use for continuum subtraction and imaging was substantially improved by the addition of a moment difference analysis." (abstract)
- line free channels: Derived from dirty Stokes I image cubes (image plane), not from the uv plane  
  > "we developed a method to derive continuum channels by examining Stokes I image cubes, prior to cleaning" (6.1 Advantages of the image plane technique)
- primary beam correction: _not stated_
- array combination: Not supported: 12 m, 7 m and total power combinations are not yet done by the pipeline  
  > "Such combinations are not yet supported in the pipeline, and the implementation of self-calibration and polarization calibration have a higher priority." (9.4 Group OUS processing)
- smoothing: _not stated_
- final beam: Cubes use a common (constant) restoring beam across all channels  
  > "which produces a constant beam size across all channels of the cube" (5.7.1 Cube imaging parameters)
- final rms: _not stated_

### Inherited from earlier work

- Automasking control parameters and algorithm details  
  > "Details can be found in (cite: Kepley2020); the only changes since that publication are that the was decreased." (5.4.5 Automasking for cleaning) [from (cite: Kepley2020)]
- Possible spectral setups of ALMA observations  
  > "Further details on the possible spectral setups can be found in (cite: Remijan2019)." (3.2.1 Types of spws supported) [from (cite: Remijan2019)]
- Meaning of WVR per-antenna RMS and Disc columns  
  > "Further information on the meaning of these columns can be found in (cite: Nikolic2012) and the CASA documentation." (3.9 WVR corrections) [from (cite: Nikolic2012)]
- Multi-frequency synthesis continuum imaging algorithm  
  > "All continuum imaging uses the multi-frequency synthesis (MFS) algorithm in (cite: Rau2011)" (5.5 MFS continuum imaging) [from (cite: Rau2011)]

### Not stated but needed to reproduce (our reading)

- Which two MOUS (2016.1.00314.S, 2017.1.00983.S) are used in which figure, and their MOUS/EB identifiers, are not given in the text.
- Many CASA task names and parameter names are blank in the supplied text (conversion loss), so exact parameter settings of each stage cannot be read from this version.
- Exact pipeline source code revision, the PPR recipe XML files and analysisUtils version are not given beyond the 2022.2.0.64 release label.
- The flux density measurements and antenna position corrections file used for any specific run are inputs that must be fixed for reproducibility but are not given.
- The list of the 96 benchmark MOUS and the shared spreadsheet of their properties are not provided.
- Initialisation values of the findContinuum sigma_fc parameter are shown only in a flow chart figure.
- Observational details (band, configuration, integration time, target coordinates) of the illustrative datasets are not stated.

## Analysis recipe

1. **import raw data and fetch calibrator flux densities**: Import each ASDM into a CASA MS, fill SIGMA and WEIGHT from the radiometer equation, and query the ALMA calibrator catalog for flux density and spectral index  
  > "each ASDM of the MOUS is imported into a CASA MS" (3.3 Data import); "It also populates the SIGMA column of the MS using the following relation based on the radiometer equation" (3.3 Data import)
   - software: CASA, ALMA Science Pipeline
   - parameter: Flux density and spectral index retrieved for the date of each EB  
  > "retrieve the best estimate of the flux density and spectral index at the center frequency of each spw for the date of observation of each EB" (3.3 Data import)
   - fitting: _not stated_
   - validation: _not stated_
2. **apply and flag system temperature calibration**: Tsys spectra from the SYSCAL table are turned into a caltable and flagged with six metrics, then pre-applied to all later solves  
  > "There are six separate flagging metrics, where each metric creates its own flagging view and has its own corresponding flagging rule(s)." (3.7 Flagging of Tsys caltables)
   - software: CASA, ALMA Science Pipeline
   - parameter: Metric order: nmedian, derivative, fieldshape, edgechans, birdies, toomany  
  > "(default order: nmedian, derivative, fieldshape, edgechans, birdies, toomany)" (3.7 Flagging of Tsys caltables)
   - parameter: nmedian outlier threshold factor default 2.0 times median of unflagged points  
  > "larger than a threshold factor (: default=2.0) times the median of all non-flagged data points" (3.7.1 Tsys median heuristic)
   - fitting: _not stated_
   - validation: _not stated_
3. **correct antenna positions and water vapor phase fluctuations**: Compute WVR phase correction tables, compare antenna phase RMS with and without the correction, and keep the correction only if it improves the data  
  > "the improvement ratio is used to determine if the WVR correction helps overall" (3.9 WVR corrections); "then the WVR solution table is rejected and will not be added to the CalLibrary" (3.9 WVR corrections)
   - software: CASA, analysisUtils
   - assumption: Atmosphere is non-dispersive  
  > "The atmosphere is assumed to be non-dispersive" (3.9 WVR corrections)
   - fitting: _not stated_
   - validation: Phase RMS improvement ratio per antenna  
  > "the improvement ratio is used to determine if the WVR correction helps overall" (3.9 WVR corrections)
4. **set flux model, flag gain outliers, solve bandpass, spw offsets and low-SNR strategy**: Point source model for the flux calibrator, outlier amplitude gain flagging on the bandpass scan, phased-up bandpass solution, spw phase offsets, and SNR-driven spw mapping or combination for phase solutions  
  > "the stage will create a point source model of the specified Stokes I flux density for the observed visibilities" (3.10 Flux calibrator model); "If the SNR prediction does not meet the threshold of 32 for a given spw" (3.14.1 Spw mapping and combination)
   - software: CASA, ALMA Science Pipeline
   - parameter: Gain outlier lower threshold factor default 0.7 of median  
  > "Their value is smaller than a threshold factor times the median of all non-flagged data points, where the threshold is (default: 0.7)" (3.11 Flagging of antenna/spw combinations with outlier amplitude gain solutions)
   - parameter: Minimum of 8 bandpass solution intervals across each spw  
  > "the minimum number of solutions intervals across each spw is 8 in order to be able to measure (and thereby remove) a slope or coarse ripple" (3.12 Bandpass)
   - parameter: If no spw meets the SNR threshold, all spws are vector averaged for phase solves  
  > "if no spw meets the SNR threshold, then the data from all spws are combined (vector averaged) in all subsequent phase solves" (3.14.1 Spw mapping and combination)
   - fitting: _not stated_
   - validation: _not stated_
5. **set flux scale, solve time-dependent gains, apply calibration, renormalize spectra**: Amplitude gains on the flux calibrator give the flux scale factor; gains on other calibrators are solved per scan; all caltables are applied through the CASA callibrary; FDM spectra with strong lines are renormalized using autocorrelations  
  > "The amplitude gains provide the flux scaling factor." (3.15 Fluxscale); "Phase and amplitude solutions are computed for each scan" (3.16 Time dependent gain)
   - software: CASA, ALMA Science Pipeline
   - parameter: Renormalization scaling spectrum applied when above 1.02 (default)  
  > "if any scaling spectrum is found to be above the =1.02 level (the default), then the scaling spectrum is directly applied to the cross correlation data" (3.18 Renormalization)
   - fitting: Baseline of renormalization spectrum fit iteratively up to a fifth order polynomial  
  > "This is done through iteratively fitting the baseline with increasing polynomial orders up to a fifth order polynomial." (3.18 Renormalization)
   - validation: _not stated_
6. **flag outlier visibilities in calibrators and science targets**: Temporary calibration is applied and outliers in corrected-minus-model amplitude are flagged in tiers; for science targets only ultra high outliers are flagged within overlapping uv bins  
  > "There are several tiers of flagging: regular, high, very high, and ultra high." (4.4.1 Calibrators); "this stage uses the midhinge (the mean of the first and third quartiles) as the midpoint of the visibilities within each uv bin rather than the median." (4.4.2 Science targets)
   - software: CASA, ALMA Science Pipeline
   - parameter: Regular outliers above +3.2 sigma or below -3.4 sigma of the median  
  > "Regular outliers are points that are $>+3.2\sigma$ or $<-3.4\sigma$ relative to the median." (4.4.1 Calibrators)
   - assumption: Science targets modelled as point sources for the amplitude comparison (no a priori source model)  
  > "Because it lacks an *a priori* source model, it still simply assumes a point source model" (4.4.2 Science targets)
   - fitting: _not stated_
   - validation: _not stated_
7. **prepare target data and choose image weighting**: Split science targets into a new MS and pick the Briggs robust that best matches the requested beam area  
  > "The value chosen is the one closest to the default (+0.5) that predicts a beam area" (5.2 Image weighting selection)
   - software: CASA, ALMA Science Pipeline
   - parameter: Candidate robust values 0.0, +0.5, +1.0, +2.0  
  > "four possible values of the weighting parameter (cite: Briggs): 0.0, +0.5 (default), +1.0, and +2.0" (5.2 Image weighting selection)
   - fitting: _not stated_
   - validation: _not stated_
8. **mitigate product sizes**: Cascade of mitigations (channel averaging, smaller field of view, coarser pixels, fewer targets, fewer large cubes) until predicted sizes fall below limits  
  > "The mitigations are done in a priority order, with the mitigation halted once the predicted sizes fall below the thresholds." (5.3 Product size mitigation)
   - software: ALMA Science Pipeline
   - parameter: Mitigation starts at 40 GB cube size  
  > "(40 GB): cube size at which to start triggering mitigation" (5.3 Product size mitigation)
   - parameter: Maximum cube size 60 GB  
  > "(60 GB): maximum cube size that will be produced." (5.3 Product size mitigation)
   - parameter: Maximum product size 500 GB  
  > "(500 GB): maximum size of products that will be produced" (5.3 Product size mitigation)
   - fitting: _not stated_
   - validation: _not stated_
9. **find line-free continuum channels**: Build a representative spectrum from a joint moment 0 and moment 8 mask of the dirty cube, select baseline channels and thresholds, pick and trim candidate continuum ranges, then refine with moment difference analysis  
  > "The algorithm first generates a representative spectrum designed to highlight all of the line emission in the cube and then identifies a list of channels from that spectrum." (6.2 Overview of algorithm)
   - software: CASA, ALMA Science Pipeline, NumPy
   - parameter: Baseline assumed to be the 19% most line-free channels, possibly scattered across the spw  
  > "we assume that there is some minority of channels that are mostly line-free (19%), but that they might be scattered across the spw" (6.5.1 Spectral baseline selection)
   - parameter: Joint mask from moment images above N0=5 and N8=4 times MAD  
  > "The pixels of moment image $i$ with intensity higher than $N_i \times MAD_i$ above $Median_i$ forms its mask, where $N_0$=5 and $N_8$=4." (6.3 Formation of the representative spectrum)
   - parameter: Amend-mask iteration triggers when at least 9 pixels outside the joint mask exceed thresholds  
  > "If at least 9 pixels in the original momDiff image outside the joint mask have a signal" (6.6.2 Iteration 1: Amend mask)
   - fitting: _not stated_
   - validation: Result codes from changes in moment 8 statistics; revert to the earlier selection if the code is HHHH or HHHS. Defaults tuned on a test set of about 200 cubes.  
  > "The continuum selection will be reverted to the value obtained prior to initiating the moment difference analysis if the four-letter string is either HHHH or HHHS." (6.6.6 Result codes); "The default values were established based on experience with running the code on an extensive test set of $\sim$200 ALMA image cubes" (6.2 Overview of algorithm)
10. **image continuum and cubes with tclean**: Two-pass cleaning (dirty image then clean) with automasking to a threshold set from the theoretical sensitivity, mfs continuum and common-beam cubes in LSRK  
  > "As many imaging heuristics require knowledge about properties of the resultant image (e.g. dynamic range), the imaging process is broken down into two sequential calls" (5.4.2 Cleaning strategy); "The frequency frame used for cubes is LSRK, with the exception of SSO targets" (5.7.1 Cube imaging parameters)
   - software: CASA, tclean, ALMA Science Pipeline
   - parameter: Cleaning threshold nominally 2 times the expected image sensitivity  
  > "is nominally set to =2 times the expected image sensitivity" (5.4.3 Cleaning threshold)
   - parameter: Default loop gain 0.1 used to set the iteration limit  
  > "computed based on the default loop gain ($g_{\rm loop}$=0.1)" (5.4.4 Cleaning iteration limit)
   - fitting: _not stated_
   - validation: Achieved noise compared with theoretical noise times a dynamic range correction factor  
  > "to the theoretical noise" (7.4.1 Achieved RMS)
11. **assign quality assessment scores**: Each stage gets a 0 to 1 QA score from subscores; the stage score is the minimum of its subscores, and WebLog is reviewed by ALMA staff  
  > "In these cases, the overall stage QA score is set to the minimum of all the QA subscores." (7 QA Scores)
   - software: ALMA Science Pipeline
   - fitting: _not stated_
   - validation: _not stated_
12. **test and validate pipeline releases**: CASA stakeholder tests, automated nightly regression tests, a 96-MOUS benchmark suite, and a repeat validation of about 15 datasets at JAO  
  > "Regression tests ensure the consistency of pipeline results by quickly identifying unexpected changes to the pipeline output during pipeline software development." (8.2 Pipeline regression testing); "These 96 MOUS have been selected to cover a wide parameter space" (8.3 Pipeline benchmark testing)
   - software: pytest, Bamboo, CASA
   - fitting: _not stated_
   - validation: Results at JAO should be identical to those from the working group, including flagged data, imaging statistics and calibrated flux densities  
  > "Everything should be identical, from flagged data to imaging statistics, including flagging statistics and calibrated flux densities." (8.4 Pipeline validation)

## Software

- **ALMA Science Pipeline** 2022.2.0.64: Automated calibration and imaging of ALMA data (the subject of the paper)  
  > "The ALMA Science Pipeline provides automated calibration and imaging of ALMA interferometric and single-dish data." (Introduction)
- **CASA** 6.4.1.12: Provides the tasks and toolkit functions on which every pipeline stage is built  
  > "with each data reduction stage layered on top of tasks and toolkit functions provided by the Common Astronomy Software Applications package" (abstract)
- **Python** 3.6: Language of the pipeline framework  
  > "The pipeline software framework is written in Python" (abstract)
- **tclean** : CASA imaging task used for all calibrator, continuum and cube imaging stages  
  > "Imaging is performed using the task within the pipeline task" (5.4 General imaging heuristics)
- **analysisUtils** : Source of the antenna position corrections file  
  > "the origin of the text file is the function of the analysisUtils Python package" (3.8 Antenna position corrections)
- **Astropy** : Compute target elevation for the low-transmission heuristic  
  > "This heuristic uses the Astropy package" (4.1.10 Low transmission)
- **ATM (Atmospheric Transmission at Microwaves)** : Atmospheric transmission model behind the CASA atmospheric tool  
  > "which is based on the package Atmospheric Transmission at Microwaves" (4.1.10 Low transmission)
- **SciPy** : Minimization and fitting of calibrated gains vs. frequency for QA scores  
  > "The minimization is performed with the SciPy module" (7.3.6 Calibrator gain vs. frequency behavior)
- **NumPy** : Discrete differences and medians in heuristics  
  > "using the NumPy function to produce the second discrete difference in units of percentage" (6.5.3 Adjustment of MAD)
- **pytest** : Framework for regression tests  
  > "The regression tests use the pytest Python testing framework" (8.2 Pipeline regression testing)
- **Bamboo** : Continuous integration to run automated tests  
  > "Bamboo, a continuous integration tool from Atlassian, is used to run the automated tests." (8.2 Pipeline regression testing)
- **JIRA** : Tracking pipeline developments  
  > "The historical and ongoing developments of the pipeline are tracked using the JIRA ticket system from Atlassian." (Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fraction of ALMA datasets calibrated and imaged with the pipeline, Cycle 7 | 96.5 | not stated | percent | 0 | During Cycle 7 and 8, 96.5% and 97.2% of ALMA datasets were calibrated and imaged with the pipeline. |
| Fraction of ALMA datasets calibrated and imaged with the pipeline, Cycle 8 | 97.2 | not stated | percent | 0 | During Cycle 7 and 8, 96.5% and 97.2% of ALMA datasets were calibrated and imaged with the pipeline. |
| Fraction of ALMA datasets calibrated and imaged with the pipeline, two most recent Cycles | 97 | not stated | percent | 0 | In the two most recent Cycles, 97% of ALMA datasets were calibrated and imaged with the pipeline |
| Number of MOUS in the pipeline benchmark suite | 96 | not stated | MOUS | 12 | These 96 MOUS have been selected to cover a wide parameter space |
| Number of CASA imaging stakeholder test cases | 22 | not stated | test cases | 12 | It currently consists of 22 test cases whose inputs match those used by the ALMA pipeline |
| Quantities compared in each pipeline regression test | 19 | not stated | quantities | 12 | At this time, 19 quantities (some per-field, spw, or scan) are used for this comparison |

## Qualitative findings

- Pipeline calibrated visibilities are generally accepted as reliable and feed customized imaging pipelines for large programs  
  > "One of the main products of the pipeline is calibrated visibilities, which have been generally accepted by the user community to be reliable" (3 Calibration Heuristics)
- Calibration pipeline entered ALMA operations in 2014 October  
  > "The calibration portion of the interferometric pipeline was first placed into operation by ALMA in 2014 October" (Introduction)
- Imaging pipeline entered operations in Cycle 4, first automated images delivered in 2017  
  > "The imaging portion of the pipeline was introduced in operations during Cycle 4 with the first automated image products delivered to users in 2017." (Introduction)
- Line wings and faint hot core lines are visible in the image-plane spectrum but buried in the uv spectrum  
  > "the line wings and the fainter lines from hot core species (complex organic molecules) are buried in the noise of the uv spectrum, but are visible in the image plane spectrum" (6.1 Advantages of the image plane technique)

## Claim tuples

- H: Can the automated pipeline calibrate and image nearly all ALMA datasets? | E: Count the fraction of ALMA datasets processed by the pipeline in recent Cycles | R: 96.5% (Cycle 7), 97.2% (Cycle 8), 97% over the two most recent Cycles | F: The pipeline handles nearly all ALMA data, supporting long-term automated reproducibility | **supported**
- H: Is continuum channel finding better done on image cubes than on uv spectra? | E: Compare the visibility spectrum of a 3-point mosaic of a massive star-forming region with the pipeline image-plane mean spectrum | R: Line wings and faint hot core lines are visible in the image plane but buried in the uv spectrum | F: The image-plane technique is more sensitive and handles multiple EBs and mosaics | **supported**
- H: Does the moment difference analysis improve continuum channel selection? | E: Run iterations 1, 2a and 2b of the analysis on a cube with extended 13CO emission | R: Intersection of amended-mask and original ranges removes nearly all contamination; extra mask removes the remaining faint contamination | F: The moment difference analysis reduces line contamination of the selected continuum channels | **supported**
- H: Do WVR corrections reduce phase RMS? | E: Compare antenna phase RMS with and without WVR corrections | R: Phase RMS is reduced in the majority of cases but not in cloudy conditions | F: WVR correction is generally beneficial; hydrosol continuum from clouds can spoil it | **supported**
- H: Can pipeline results be reproduced across systems at the observatory? | E: Process about 15 benchmark datasets at JAO and compare WebLogs with those produced by the working group | R: Results are expected to be identical; differences are investigated (no outcome numbers given) | F: Reproducibility is verified by a validation step with fixed inputs | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Image-plane continuum finding avoids uv-plane problems with off-center emission, multiple EBs and mosaics  
  > "there are several complications and limitations of the uv plane approach" (6.1 Advantages of the image plane technique); "we developed a method to derive continuum channels by examining Stokes I image cubes, prior to cleaning" (6.1 Advantages of the image plane technique)
- Alternative: Excluding SSO data by uvrange instead of antenna selection was rejected because it can leave very little data for some antennas  
  > "An alternative strategy that excludes data based solely on uvrange instead of antenna selection can sometimes lead to cases where there is very little data included for some antennas, which can bias the results for all antennas." (3.15 Fluxscale)
- Alternative: Power-law fit of calibrator fluxes across spws not applied, to avoid noise bias in low SNR spws  
  > "By not applying a power law fit, we ensure that spws with low SNR, which suffer noise bias" (3.15 Fluxscale)
- How they decided it was enough: Thresholds and bin factors set empirically from tests  
  > "Empirical tests show that the bins need to be closer together at short uv distances and can become wider at longer distances." (4.4.2 Science targets)
- Limitation (authors): No heuristic to identify interstellar absorption lines in the flux calibrator data  
  > "There is no heuristic to identify and flag such lines" (3.15 Fluxscale)
- Limitation (authors): Channel-based flagging sometimes triggers on strong atmospheric ozone lines  
  > "Currently, the stage sometimes triggers on strong atmospheric ozone lines" (4.3 Channel-based flags)
- Limitation (authors): Channelized weights are not yet used  
  > "The use of channelized weighting is a future improvement" (3.7 Flagging of Tsys caltables)
- Limitation (authors): Bandwidth switching and band-to-band transfer are not supported  
  > "which means that the more complicated calibration methods of bandwidth switching and band-to-band (B2B) transfer under development" (3.2 Observing modes supported)
- Limitation (authors): Combining multiple configurations or total power data is not supported  
  > "Such combinations are not yet supported in the pipeline" (9.4 Group OUS processing)
- Caveat (inferred, ours): Few quantitative performance tests of individual heuristics are shown; thresholds are mostly empirical without error analysis.
- Caveat (inferred, ours): Illustrative datasets are not described, so figures cannot be reproduced from the text alone.
- Caveat (inferred, ours): Many thresholds depend on tuning with an internal benchmark set not released with the paper.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Pipeline products that pass QA are stored in the ALMA Science Archive and delivered to users  
  > "and, if satisfactory, are stored into the ALMA Science Archive" (2.3 Products)
- Code: Pipeline releases and CASA versions with downloadable tarballs are listed on the ALMA science portal  
  > "A list of the pipeline releases, including the corresponding CASA versions and downloadable tarballs, is hosted on the ALMA science portal" (Introduction)
- Missing: Exact stage parameter values (names missing in this text)
- Missing: Per-run flux density and antenna position input files
- Missing: Benchmark MOUS list
- Missing: Specification of the two illustration datasets
- Data volume (inferred): Not applicable to the paper itself; the two illustration datasets are unspecified and are likely tens of GB each as ALMA MOUS
- Score (inferred): 2/5, Scale 1 to 5. Describes software behaviour rather than a data analysis; no measurable results to redo from archive data, though the pipeline itself is public.
- Rediscovery candidate: no, The paper documents pipeline algorithms and validation, with no science result to recover from public data.

## Links

- Method: (cite: Kepley2020) (Automasking algorithm used in pipeline cleaning)
- Method: (cite: Nikolic2012) (WVR phase correction method)
- Method: (cite: Remijan2019) (ALMA technical handbook for spectral setups and QA)
- Method: (cite: Rau2011) (Multi-frequency synthesis algorithm used in tclean)
- Companion: (cite: Kent2020) (VLA pipeline sharing tasks with the ALMA pipeline)
- Companion: (cite: Nakazato2022) (NRO 45 m pipeline built on the same framework)
- Companion: (cite: Masters2020) (WebLog description)
- Companion: (cite: phangs2021; maps2021) (Large-program imaging pipelines using pipeline-calibrated visibilities)
- Related: PHANGS-ALMA and MAPS large programs (customized imaging pipelines starting from pipeline-calibrated visibilities)

## Checks

```json
{
 "quotes": 116,
 "quotes_ok": 116,
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
  "facts": 130,
  "stated": 87,
  "rate": 0.669
 },
 "evidence_ok": true
}
```
