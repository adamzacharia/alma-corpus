# A first search of transients in the Galactic center from 230 GHz ALMA observations

`2022A&A...666A..39M` | Astronomy and Astrophysics 2022 | first author: Mus, A. | arXiv: 2208.08248 | DOI: 10.1051/0004-6361/202243335

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: transients, milky_way_ism, agn_and_quasars
- Question: Can second-to-minute timescale millimeter-wave radio transients be detected in the Galactic Center at 230 GHz using a novel two-component self-calibration procedure on ALMA observations?  
  > "In this work, we present a novel and nonstandard self-calibration procedure that overcomes most of the instrumental and atmospheric limitations of mm-wave transient studies." (Introduction); "The superb sensitivity of ALMA and the high time cadence of the ALMA-VLBI observations of the GC performed during the 2017 EHT campaign, allowed us to perform a search down to second/minute scale radio transients in the GC field at arc-second resolution." (Summary and conclusions)
- Target **Sgr A***: coordinates 17:45:40.04 -29.00.28.17 (J2000)  
  > "Fig. [1](#fig:fitting_error) shows how optimal elevations present less offset on the relative right ascension (RA) and relative declination (DEC) with respect to Sgr A$^*$ correlation coordinates (17:45:40.04 -29.00.28.17(J2000)." (Two-components’ self-calibration algorithm); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (230 GHz)  
  > "The campaign was divided in two parts, each one observing in a different frequency band: April 1 to April 3 in Band 3 (86 GHz) and April 5 to April 11 in Band 6 (230 GHz)." (Observations); "In this work, we focus on 230 GHz." (Observations)
- frequencies and spectral setup: Two sidebands (LO and HI) with four spectral windows of 2 GHz bandwidth each (240 spectral channels), centered at 213.1, 215.1, 227.1, and 229.1 GHz  
  > "For the frequency set up there were two sidebands (called “lower sideband" and “upper sideband", or LO and HI) with four frequency spectral windows (two per sideband), with a bandwidth of 2 GHz each (divided in 240 spectral channels) two centered at 213.1 and 215.1 GHz (lower sideband), and two centered at 227.1 and 229.1 GHz (upper sideband)." (Observations)
- continuum bandwidth: 8 GHz (four spectral windows of 2 GHz each)  
  > "with four frequency spectral windows (two per sideband), with a bandwidth of 2 GHz each (divided in 240 spectral channels)" (Observations)
- arrays: 12 m array (median 37 antennas)  
  > "The GC was observed in three tracks, hereafter called Track B (April 6), Track C (April 7), and Track E (April 11) with a typical duration of 4-10 hours and a median number of 37 antennas of 12 m diameter giving a effective field of view of the GC field of $\sim30$ arcsec." (Observations)
- configurations: C40-3  
  > "The VLBI observations of ALMA during year 2017 were part of its Cycle 4 campaign, which was carried out in compact configuration C40-3 (baseline lengths between 15 m and 460 m)." (Observations)
- baselines: 15 m to 460 m  
  > "The VLBI observations of ALMA during year 2017 were part of its Cycle 4 campaign, which was carried out in compact configuration C40-3 (baseline lengths between 15 m and 460 m)." (Observations)
- angular resolution: arc-second resolution  
  > "allowed us to perform a search down to second/minute scale radio transients in the GC field at arc-second resolution." (Summary and conclusions)
- max recoverable scale: _not stated_
- sensitivity: 0.5 mJy/beam to 1.0 mJy/beam in 4 seconds (standard weather); instantaneous rms 2.138-7.210 mJy/beam (April 6), 0.287-16.602 mJy/beam (April 7), 2.522-15.661 mJy/beam (April 11)  
  > "The integration time of the ALMA correlator in VLBI mode is set to 4 seconds, which corresponds to the shortest cadence for our variability study, resulting in a sensitivity, in standard weather conditions, of 0.5 mJy/beam to 1.0 mJy/beam." (Observations); "the instantaneous root-mean-square (rms) of our ALMA observations, ranged between $2.138-7.210$ mJy/beam in April 6, $0.287-16.602$ mJy/beam in April 7 and $2.522-15.661$ mJy/beam in April 11" (Strategy for finding transients)
- time on source: typical track duration of 4-10 hours  
  > "The GC was observed in three tracks, hereafter called Track B (April 6), Track C (April 7), and Track E (April 11) with a typical duration of 4-10 hours" (Observations)
- observing dates: 2017 April 6 (Track B), April 7 (Track C), and April 11 (Track E)  
  > "The VLBI observations of ALMA during year 2017 were part of its Cycle 4 campaign" (Observations); "The GC was observed in three tracks, hereafter called Track B (April 6), Track C (April 7), and Track E (April 11)" (Observations)
- pi or archival as stated: EHT 2017 campaign intra-ALMA byproduct visibilities  
  > "We then apply this method to the ALMA observations of Sgr A$^*$ at 230 GHz taken during the EHT 2017 campaign" (Introduction); "The intra-ALMA visibilities were a “byproduct" of the VLBI observations." (Observations)
- External data: Sgr A* millimeter flux density variation range of 3.2 +/- 1.2 Jy and integrated mini-spiral flux density of ~1.1 Jy  
  > "The compact component has the property of being highly variable at millimeter wavelengths on short timescales, with flux density varying within $3.2 \pm 1.2$ Jy (cite: Wielgus21)" (Two-components’ self-calibration algorithm); "Wielgus et al. (2022) considered the integrated flux density of the mini-spiral to be $\sim$ 1.1 Jy." (Two-components’ self-calibration algorithm) [from Wielgus et al. (2022) (cite: Wielgus21)]
- Simulation/model as data: Simulated 230 GHz ALMA observations of Sgr A* for Track B (April 6) generated with CASA simalma, including a flat-spectrum compact source, the extended mini-spiral model, and a synthetic Gaussian-like transient of ~207 mJy peak and ~42 s duration  
  > "We have simulated ALMA observations of Sgr A$^*$ corresponding to the array configuration, and exact observing times, of the true visibilities of Track B (April 6) in the 2017 EHT campaign by using the CASA task `simalma` with its default parameters for 230 GHz." (Simulated data); "In addition to this, we have inserted a short transient, with amplitude evolution Gaussian-like, with a duration of $\sim42$ seconds and centered on 10:52:01 UT and located at 5 arcsec to the east of Sgr A$^*$ and 1 arcsec to the north. The peak flux density of the transient is $\sim207$ mJy (see Fig. [3](#fig:trans_ampl))." (Simulated data)

## Processing

### Calibration

- pipeline or manual: ALMA-VLBI QA2 calibration pipeline followed by custom nonstandard two-component self-calibration  
  > "For this work, we have applied the visibility calibration following the procedure of (cite: CiriacoRefMini) plus subsequent calibration steps described in (cite: Wielgus21)." (Observations); "The QA2 calibration “pipeline" (cite: APPRef; CiriacoRefb) is the procedure used to generate the intra-ALMA calibration tables and all the metadata needed for the correct polarimetry processing of the ALMA-VLBI observations." (Two-components’ self-calibration)
- casa version: v5.7  
  > "We use the CLEAN algorithm (cite: Hogbom1974) implemented in the Common Astronomy Software Applications (CASA) framework v5.7[^1] as the `tclean` task" (Strategy for finding transients)
- pipeline version: _not stated_
- archive products used as is: no (QA2 calibration refined to remove constant flux density restriction)  
  > "However, the high variability of Sgr A$^*$ makes it necessary to refine the QA2 calibration by removing such a restriction." (Two-components’ self-calibration)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Two-component self-calibration at 4 s cadence scaling amplitudes via constant extended mini-spiral flux (gain Gt), followed by one standard amplitude and phase self-calibration iteration using the two-component model visibilities  
  > "Following (cite: Wielgus21), we have modeled these two components across the FOV at each integration time of 4s." (Two-components’ self-calibration algorithm); "In addition to the use of $G_t$, we have also performed one standard self-calibration iteration(i.e., computed the antenna-wise time-dependent complex gains) correcting at the same time amplitudes and phases using the model visibilities from Eq. [\[eq:model\]](#eq:model)" (Two-components’ self-calibration algorithm)

### Imaging

- task: tclean  
  > "We use the CLEAN algorithm (cite: Hogbom1974) implemented in the Common Astronomy Software Applications (CASA) framework v5.7[^1] as the `tclean` task" (Strategy for finding transients)
- deconvolver: CLEAN (Hogbom 1974)  
  > "We use the CLEAN algorithm (cite: Hogbom1974) implemented in the Common Astronomy Software Applications (CASA) framework v5.7[^1] as the `tclean` task" (Strategy for finding transients)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: not applied  
  > "An important point to highlight is that, with this strategy, the primary-beam response is not corrected." (Strategy for finding transients)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: Instantaneous rms: 2.138-7.210 mJy/beam (April 6), 0.287-16.602 mJy/beam (April 7), 2.522-15.661 mJy/beam (April 11); Mean rms: 2.628 mJy/beam (Track B), 2.490 mJy/beam (Track C), 3.096 mJy/beam (Track E)  
  > "the instantaneous root-mean-square (rms) of our ALMA observations, ranged between $2.138-7.210$ mJy/beam in April 6, $0.287-16.602$ mJy/beam in April 7 and $2.522-15.661$ mJy/beam in April 11" (Strategy for finding transients); "| 3.660 | 2.628 | 0.494 |" (Real data); "| 4.537 | 2.490 | 0.749 |" (Real data)

### Inherited from earlier work

- Initial visibility calibration and intra-ALMA VLBI QA2 calibration procedure  
  > "For this work, we have applied the visibility calibration following the procedure of (cite: CiriacoRefMini) plus subsequent calibration steps described in (cite: Wielgus21)." (Observations) [from (cite: CiriacoRefMini); (cite: Wielgus21); (cite: APPRef); (cite: CiriacoRefb)]
- Two-component visibility modeling and self-calibration approach decomposing the field into Sgr A* and the extended mini-spiral  
  > "In the following section, we present a nonstandard self-calibration procedure, similar to the one described in (cite: Wielgus21)" (Two-components’ self-calibration); "Following (cite: Wielgus21), we have modeled these two components across the FOV at each integration time of 4s." (Two-components’ self-calibration algorithm) [from (cite: Wielgus21)]
- Flagging of beginning and end of Phasing System subscans  
  > "Especially notorious are the beginning and end of the Phasing System subscans, when the ALMA phase corrections have not converged yet (cite: APPRef). We have flagged such points following (cite: CiriacoRefb)." (Strategy for finding transients) [from (cite: CiriacoRefb)]

### Not stated but needed to reproduce (our reading)

- Exact tclean imaging parameters (weighting scheme, robust parameter, cell size, image pixel dimensions, niter, stopping threshold, and clean mask definition)
- ALMA project code in the paper text (linked as 2016.1.01154.V only in archive metadata)
- Quantitative threshold value used to flag visibilities with 'extremely high and nonrealistic rms'
- Length (number of frames) of the running median window used to define the time-search intervals

## Analysis recipe

1. **Initial calibration and flagging of ALMA phased-array visibilities**: Apply ALMA-VLBI QA2 calibration pipeline and subsequent visibility calibration steps, flag the start and end of Phasing System subscans where phase corrections have not converged, and flag visibilities with nonrealistic high rms.  
  > "For this work, we have applied the visibility calibration following the procedure of (cite: CiriacoRefMini) plus subsequent calibration steps described in (cite: Wielgus21)." (Observations); "Especially notorious are the beginning and end of the Phasing System subscans, when the ALMA phase corrections have not converged yet (cite: APPRef). We have flagged such points following (cite: CiriacoRefb)." (Strategy for finding transients); "(visibilities with an extremely high and nonrealistic rms have been flagged)." (Strategy for finding transients)
   - software: CASA
   - parameter: 4 s integration time  
  > "The integration time of the ALMA correlator in VLBI mode is set to 4 seconds, which corresponds to the shortest cadence for our variability study" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Two-component self-calibration and extended mini-spiral modeling**: Decompose the GC field of view into a time-variable point source (Sgr A*) and a stable extended component (mini-spiral). Iteratively solve for the mini-spiral image model using CASA tclean, fit the 4-parameter visibility model at each 4 s integration time to derive amplitude scaling gains Gt, recalibrate visibilities, and perform one standard amplitude and phase self-calibration iteration.  
  > "Following (cite: Wielgus21), we have modeled these two components across the FOV at each integration time of 4s." (Two-components’ self-calibration algorithm); "In addition to the use of $G_t$, we have also performed one standard self-calibration iteration(i.e., computed the antenna-wise time-dependent complex gains) correcting at the same time amplitudes and phases using the model visibilities from Eq. [\[eq:model\]](#eq:model)" (Two-components’ self-calibration algorithm); "We use the CLEAN algorithm (cite: Hogbom1974) implemented in the Common Astronomy Software Applications (CASA) framework v5.7[^1] as the `tclean` task, iteratively minimizing the difference of the residuals and the model by recalibrating the data with $G_t$, and updating $\mathcal{V}^{\mathrm{obs}}_t$." (Strategy for finding transients)
   - software: CASA, tclean
   - parameter: 4 s cadence  
  > "Following (cite: Wielgus21), we have modeled these two components across the FOV at each integration time of 4s." (Two-components’ self-calibration algorithm)
   - parameter: 4 fitted parameters per integration time: F_ext, F_SgrA*, delta_ra, delta_dec  
  > "Eq. [\[eq:model\]](#eq:model) can be seen as four-dimensional fitting whose variables are $F^{\text{ext}}, F^{\text{SgrA*}}, \Delta \text{ra}, \Delta \text{dec}$." (Mathematical details of the two-components’ self-calibration)
   - assumption: The morphology and integrated flux density of the extended mini-spiral are constant within each observing track (varying only between tracks from 1.16 to 1.18 Jy)  
  > "The morphology of the large scale minispiral emission, on the other hand, is stable in time on relevant timescales of several days, hence we assume this in the presented analysis. Nevertheless we allow for the total flux density scale of the extended emission component to vary between the three observed tracks, finding values between 1.16 and 1.18 Jy." (Two-components’ self-calibration algorithm); "Since the integrated flux density of the mini-spiral is assumed to be constant, we can use the values of $G_t$ to remove the residual corruption effects in the Sgr A$^*$ flux density estimates $F^{\text{SgrA*}}$." (Two-components’ self-calibration algorithm)
   - fitting: Chi-square minimization at each integration time using a recursive Newton method with first-order Taylor expansion for position offsets  
  > "The observed visibility vector at a time $t$ given a baseline $j$, denoted by $\mathcal{V}_{j,t}^{\text{obs}}$, can be model-fitted to $\mathcal{V}_{j,t}^{\text{mod}}$ by minimizing the chi-square distribution function" (Two-components’ self-calibration algorithm); "Then, the fitting minimization problem can be solved applying a simple Newton method, whose recursive formulation reads" (Mathematical details of the two-components’ self-calibration)
   - validation: Incremental antenna gains checked to be close to unity (amplitude ~1, phase ~0), and residual image rms compared against QA2 data showing a factor of ~5 improvement  
  > "In all cases, we see that the incremental gains are actually close to unity, as expected." (Calibration plots); "In addition, Fig. [9](#fig:rms_vs_time) right panel shows a comparison of the rms obtained by taking the QA2 data and cleaning with the same mask and `CLEAN` parameters used for the two-components’ self-calibration. We can see an improvement on the rms by a factor of $\sim$5." (Calibration plots)
3. **Validate transient detection pipeline on synthetic data**: Simulate Track B (April 6) 230 GHz observations using CASA simalma with real Sgr A* light curves, the mini-spiral model, thermal noise, real antenna gains, and an injected Gaussian-like transient. Apply the two-component self-calibration, subtract the Sgr A* and mini-spiral models, image the residual visibilities at 4 s and 12 s cadences, and search for the transient.  
  > "We have simulated ALMA observations of Sgr A$^*$ corresponding to the array configuration, and exact observing times, of the true visibilities of Track B (April 6) in the 2017 EHT campaign by using the CASA task `simalma` with its default parameters for 230 GHz." (Simulated data); "Once convergence of the self-calibration was achieved, we computed the residual visibilities (i.e., by subtracting the model of the minispiral and Sgr A$^*$) and generated the corresponding residual images for each integration time." (Simulated data)
   - software: CASA, simalma, tclean
   - parameter: Synthetic transient: peak ~207 mJy, duration ~42 s, centered at 10:52:01 UT, offset 5 arcsec East and 1 arcsec North of Sgr A*  
  > "In addition to this, we have inserted a short transient, with amplitude evolution Gaussian-like, with a duration of $\sim42$ seconds and centered on 10:52:01 UT and located at 5 arcsec to the east of Sgr A$^*$ and 1 arcsec to the north. The peak flux density of the transient is $\sim207$ mJy (see Fig. [3](#fig:trans_ampl))." (Simulated data)
   - fitting: Same two-component chi-square self-calibration as step 2  
  > "We have calibrated the synthetic observations using the two-components’ self-calibration explained in Sect [4](#sec:stgy)." (Simulated data)
   - validation: Successful recovery of the injected synthetic transient in both 4 s and 12 s residual images with peak S/N of 15.194 and peak brightness ~200 mJy  
  > "From time 10:51:27 UT (h) to 10:52:33 UT (h) we can see how a transient point source is appearing $\sim5$ arcsec to the East of Sgr A$^*$. The brightness peak is notably increasing to reach a maximum of $\sim$ 200 mJy, while the duration of the transient is approximately to 1 min." (Simulated data); "Now, we can easily follow the evolution of the S/N and rms. In both cases, they start with relative low (close to the mean) and they start to increase progressively while they are advancing in time, until their maximum (15.19 , 1.32 mJy/beam respectively) is reached." (Some details on the synthetic transient)
4. **Search for transients in real ALMA residual snapshot images**: Subtract the converged Sgr A* and mini-spiral model visibilities from each track (April 6, 7, 11), generate residual snapshot images at 4 s and 12 s cadences, track peak dynamic range (S/N) and rms using a running median window, apply detection threshold and duration criteria, and manually inspect candidate residual frames.  
  > "We have thus set the detection threshold of transients to peak excursion of 7 times the instantaneous rms between consecutive images, which also gives a very low probability of false detection from thermal noise." (Strategy for finding transients); "In particular, the transient search has been performed considering two different time-search intervals, one defined by the observation cadence time (4 s) and the other one by three times the cadence time (12 s)." (Strategy for finding transients); "The potential detections are then manually inspected in the residual images to ensure physical feasibility, (i.e. that they are not due to artifacts in the image plane)." (Strategy for finding transients)
   - software: CASA, tclean
   - parameter: Detection threshold: peak excursion of 7 times the instantaneous rms between consecutive images; at least 3 standard deviations in maxima between two consecutive time-search intervals  
  > "We have thus set the detection threshold of transients to peak excursion of 7 times the instantaneous rms between consecutive images, which also gives a very low probability of false detection from thermal noise." (Strategy for finding transients); "Excursions of at least three standard deviation in the maxima between two consecutive time-search intervals are considered as a potential transient." (Strategy for finding transients)
   - parameter: Minimum duration: 12 s (three 4 s integration times)  
  > "Therefore, on the one hand the minimum duration of a transient would be three times the integration time." (Strategy for finding transients); "by tracking events occurring for a duration of at least 12s (three times the ALMA integration time)." (Summary and conclusions)
   - assumption: Noise is assumed to follow a Gaussian distribution across ~10^4 beams in the field of view to estimate false positive probability (~10^-8 at 7 sigma)  
  > "Supposing that noise follows a normal distribution, we have computed the number of beams that form the image Fig. [2](#fig:minispirals) (which is $\approx10^4$), and we have found that the probability of getting at least one false positive transient detection in the field of view with a confidence of 7$\sigma$ is $\approx 10^{4}\times 10^{-12}= 10^{-8}$." (Strategy for finding transients)
   - fitting: Running median window applied to dynamic range time series  
  > "Such time-search intervals are defined following running median window at each epoch." (Strategy for finding transients)
   - validation: Manual inspection of residual snapshot sequences and verification against antenna elevation (< 25 deg exhibits significant quality loss)  
  > "It is important to note that data corresponding to source elevation below 25$^\circ$ is exhibiting significant quality loss." (Real data); "In any case, in Appendix [11](#sec:appendix_plots), detailed sequences of snapshots of transient candidates are shown. The aim of these plots is to verify whether the higher dynamic range in a particular UT is related to a point source in the image plane, or if the image is contaminated by systematic artifacts" (Real data)

## Software

- **CASA** v5.7: Visibility calibration, imaging via tclean, and synthetic data generation via simalma  
  > "We use the CLEAN algorithm (cite: Hogbom1974) implemented in the Common Astronomy Software Applications (CASA) framework v5.7[^1] as the `tclean` task" (Strategy for finding transients); "by using the CASA task `simalma` with its default parameters for 230 GHz." (Simulated data)
- **tclean** v5.7: Deconvolving the extended mini-spiral model and generating residual snapshot images  
  > "We use the CLEAN algorithm (cite: Hogbom1974) implemented in the Common Astronomy Software Applications (CASA) framework v5.7[^1] as the `tclean` task, iteratively minimizing the difference of the residuals and the model by recalibrating the data with $G_t$, and updating $\mathcal{V}^{\mathrm{obs}}_t$." (Strategy for finding transients)
- **simalma** v5.7: Simulating 230 GHz ALMA observations of Sgr A*, the mini-spiral, and a synthetic transient for Track B  
  > "We have simulated ALMA observations of Sgr A$^*$ corresponding to the array configuration, and exact observing times, of the true visibilities of Track B (April 6) in the 2017 EHT campaign by using the CASA task `simalma` with its default parameters for 230 GHz." (Simulated data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Extended mini-spiral integrated flux density across tracks | 1.16 to 1.18 | not stated | Jy | 2 | Nevertheless we allow for the total flux density scale of the extended emission component to vary between the three observed tracks, finding values between 1.16 and 1.18 Jy. |
| Instantaneous rms range on April 6 (Track B) | 2.138-7.210 | not stated | mJy/beam | 4 | the instantaneous root-mean-square (rms) of our ALMA observations, ranged between $2.138-7.210$ mJy/beam in April 6, $0.287-16.602$ mJy/beam in April 7 and $2.522-15.661$ mJy/beam in April 11 |
| Instantaneous rms range on April 7 (Track C) | 0.287-16.602 | not stated | mJy/beam | 4 | the instantaneous root-mean-square (rms) of our ALMA observations, ranged between $2.138-7.210$ mJy/beam in April 6, $0.287-16.602$ mJy/beam in April 7 and $2.522-15.661$ mJy/beam in April 11 |
| Instantaneous rms range on April 11 (Track E) | 2.522-15.661 | not stated | mJy/beam | 4 | the instantaneous root-mean-square (rms) of our ALMA observations, ranged between $2.138-7.210$ mJy/beam in April 6, $0.287-16.602$ mJy/beam in April 7 and $2.522-15.661$ mJy/beam in April 11 |
| Residual image mean S/N for Track B (April 6) | 3.660 | not stated | dimensionless | 4 | / 3.660 / 2.628 / 0.494 / |
| Residual image mean rms for Track B (April 6) | 2.628 | 0.494 | mJy/beam | 4 | / 3.660 / 2.628 / 0.494 / |
| Residual image mean S/N for Track C (April 7) | 4.537 | not stated | dimensionless | 4 | / 4.537 / 2.490 / 0.749 / |
| Residual image mean rms for Track C (April 7) | 2.490 | 0.749 | mJy/beam | 4 | / 4.537 / 2.490 / 0.749 / |
| Residual image mean S/N for Track E (April 11) | 5.005 | not stated | dimensionless | 4 | / 5.005 / 3.096 / 0.521 / |
| Residual image mean rms for Track E (April 11) | 3.096 | 0.521 | mJy/beam | 4 | / 5.005 / 3.096 / 0.521 / |
| RMS improvement factor of two-component self-calibration over QA2 data | ~5 | not stated | dimensionless | 2 | We can see an improvement on the rms by a factor of $\sim$5. |
| Number of reliable transient detections in 2017 EHT ALMA campaign | 0 | not stated | dimensionless | 4 | Thus we can conclude that we have not found any reliable detection of transients in the ALMA observation during the 2017 EHT Campaign.; Using the criteria defined in section [4](#sec:stgy), we have not observed any transient event with sufficient statistical significance. |

## Qualitative findings

- No statistically significant millimeter transient events were detected in the Galactic Center field during the 2017 EHT ALMA 230 GHz observations.  
  > "Thus we can conclude that we have not found any reliable detection of transients in the ALMA observation during the 2017 EHT Campaign." (Real data); "Using the criteria defined in section [4](#sec:stgy), we have not observed any transient event with sufficient statistical significance." (Summary and conclusions)
- Even at the 4-second correlator integration time, the ALMA 230 GHz snapshot images of the Galactic Center are limited by dynamic range rather than thermal noise due to the bright, variable Sgr A* emission and finite fidelity of the extended mini-spiral model.  
  > "Even with integration times as short as 4 s, the ALMA images still show clear signatures of dynamic-range limitation, which indicates that the thermal noise sensitivity level is not reached." (Summary and conclusions); "Our analysis is, thus, limited by the contrast with respect to the total flux density of the model (i.e., Sgr A$^*$ and minispiral), likely due to the finite fidelity of our model (in particular, the minispiral image)." (Calibration plots)
- The two-component self-calibration method successfully corrects instrumental and atmospheric amplitude variations using all baselines and improves the residual rms by a factor of ~5 compared to standard QA2 calibration.  
  > "In the following section, we present a nonstandard self-calibration procedure, similar to the one described in (cite: Wielgus21) that allows us, on the one hand, to correct the instrumental and atmospheric effects in the ALMA observations of the GC and, on the other hand, to use the complete set of visibilities" (Two-components’ self-calibration); "In addition, Fig. [9](#fig:rms_vs_time) right panel shows a comparison of the rms obtained by taking the QA2 data and cleaning with the same mask and `CLEAN` parameters used for the two-components’ self-calibration. We can see an improvement on the rms by a factor of $\sim$5." (Calibration plots)

## Claim tuples

- H: A two-component self-calibration procedure tying visibility amplitudes to the extended mini-spiral can overcome atmospheric and instrumental limitations to enable sensitive short-timescale transient searches in the Galactic Center using all ALMA baselines. | E: Applied the two-component self-calibration to both a CASA simalma synthetic dataset containing an injected ~207 mJy, ~42 s transient and to real 230 GHz ALMA observations, and compared residual rms with standard QA2 calibration. | R: The synthetic transient was clearly recovered at 4 s and 12 s cadences (peak S/N = 15.194), and on real data the method reduced residual rms by a factor of ~5 relative to QA2 calibration. | F: The two-component self-calibration method is effective at mitigating atmospheric and instrumental corruptions and enables sensitive variability and transient analyses across the full ALMA baseline range. | **supported**
- H: Short-timescale (seconds to minutes) 230 GHz radio transients are present and detectable in the inner parsec of the Galactic Center during the 2017 EHT ALMA campaign. | E: Subtracted the Sgr A* and mini-spiral models from three tracks of 230 GHz ALMA data (April 6, 7, 11, 2017) and searched 4 s and 12 s residual snapshot images for excursions exceeding 7 times the instantaneous rms lasting at least 12 s. | R: All candidate S/N excursions either appeared in only a single 4 s integration, failed the threshold criterion, or showed systematic non-point-like artifacts upon visual inspection. | F: No reliable transient events with sufficient statistical significance were detected in the 2017 EHT ALMA 230 GHz observations. | **refuted**
- H: The 4-second snapshot residual images of the Galactic Center at 230 GHz are limited by dynamic range rather than thermal noise. | E: Measured the residual image rms on April 6 as a function of integration time and inspected residual snapshot frames during high S/N excursions. | R: The residual rms remained almost flat with increasing integration time rather than decreasing as the square root of time, and candidate snapshot frames displayed systematic non-Gaussian spatial artifacts. | F: The ALMA 230 GHz transient search is limited by dynamic range (due to contrast with Sgr A* and finite fidelity of the mini-spiral model) even at a 4-second integration time. | **supported**

## Reasoning

- Why this data: ALMA 230 GHz phased-array observations from the 2017 EHT campaign provide superb sensitivity and a short 4-second correlator integration time, allowing the most sensitive millimeter-wave search for second-to-minute transients in the Galactic Center.  
  > "Thanks to the superb sensitivity of ALMA, the transient search reported here is the most sensitive one (1.0 mJy/beam in terms of flux density per unit time) reported to date at mm wavelengths." (Introduction); "The superb sensitivity of ALMA and the high time cadence of the ALMA-VLBI observations of the GC performed during the 2017 EHT campaign, allowed us to perform a search down to second/minute scale radio transients in the GC field at arc-second resolution." (Summary and conclusions)
- Why this method: Standard QA2 calibration assumes constant flux density, and discarding short baselines to isolate Sgr A* sacrifices sensitivity; the two-component self-calibration ties amplitude gains to the stable extended mini-spiral, retaining all baselines while correcting atmospheric and instrumental effects. A running median window is used because the median is robust against large excursions in skewed distributions.  
  > "This procedure, even though it can reduce the impact of the extended component in the analysis of the Sgr A$^*$ variability, involves the discarding of a large amount of data, which may considerably affect the sensitivity." (Two-components’ self-calibration); "In the following section, we present a nonstandard self-calibration procedure, similar to the one described in (cite: Wielgus21) that allows us, on the one hand, to correct the instrumental and atmospheric effects in the ALMA observations of the GC and, on the other hand, to use the complete set of visibilities" (Two-components’ self-calibration); "The choice of the median is not arbitrary: while the mean would bias the window containing a very large excursion, the median is better suited for skewed distributions." (Strategy for finding transients)
- Alternative: Using only the longest available baselines to separate variable compact Sgr A* emission from the extended mini-spiral (rejected because discarding short baselines sacrifices a large amount of data and sensitivity)  
  > "A typical strategy to deal with interferometric observations of a variable compact source is to use only a selection of the longest available baselines (cite: Brinkerink15; Iwata20; Wielgus21)." (Two-components’ self-calibration); "This procedure, even though it can reduce the impact of the extended component in the analysis of the Sgr A$^*$ variability, involves the discarding of a large amount of data, which may considerably affect the sensitivity." (Two-components’ self-calibration)
- Alternative: Using a running mean window instead of a running median window to define time-search intervals (rejected because the mean is biased by large excursions)  
  > "The choice of the median is not arbitrary: while the mean would bias the window containing a very large excursion, the median is better suited for skewed distributions." (Strategy for finding transients)
- How they decided it was enough: _not stated_
- Limitation (authors): The observations and residual snapshot images are dynamic-range limited rather than thermal-noise limited, even at 4-second integration times, due to finite fidelity of the mini-spiral model and suboptimal calibration in bad weather.  
  > "Indeed, and as we discuss in Sect. [6](#sec:realdata), we are limited by dynamic range (rather than by sensitivity) even at the level of the integration time used in the ALMA correlator (four seconds)." (Introduction); "Our analysis is, thus, limited by the contrast with respect to the total flux density of the model (i.e., Sgr A$^*$ and minispiral), likely due to the finite fidelity of our model (in particular, the minispiral image)." (Calibration plots)
- Limitation (authors): The statistical false-positive calculation assumes a Gaussian noise distribution, which does not strictly hold because the snapshot residuals are dynamic-range limited and non-Gaussian.  
  > "In addition, one important assumption we have made is that we are working on a Gaussian distribution of the noise. This is not true, as as we are dynamic range limited in snapshots where potential excursions are seen." (Strategy for finding transients)
- Limitation (authors): Primary-beam attenuation is not corrected during the search, which reduces sensitivity toward the edges of the field of view.  
  > "An important point to highlight is that, with this strategy, the primary-beam response is not corrected. In the case a transient would be found, the primary-beam correction should be applied." (Strategy for finding transients)
- Limitation (authors): Data taken at low antenna elevations (< 25 degrees) suffer severe atmospheric opacity and turbulence, causing high rms and quality loss.  
  > "Final parts of the experiments are also pathological, when the antenna elevations are low and, as a consequence, the limitations due to the atmospheric opacity and turbulence are more severe." (Strategy for finding transients); "It is important to note that data corresponding to source elevation below 25$^\circ$ is exhibiting significant quality loss." (Real data)
- Caveat (inferred, ours): The injected synthetic transient (~207 mJy peak) is much brighter than the typical 7-sigma thermal/residual rms threshold (~18-25 mJy/beam); completeness and recovery efficiency for fainter transients near the detection threshold are not quantified.
- Caveat (inferred, ours): Requiring transients to persist for at least three consecutive 4 s integrations (12 s) makes the search insensitive to fast sub-second or few-second bursts (such as individual pulsar giant pulses or fast radio bursts).
- Caveat (inferred, ours): Because primary beam correction is omitted prior to detection, the effective flux density threshold is higher by up to a factor of 2 near the half-power radius of the 30 arcsec field of view.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Custom script/code implementing the Newton-method 4-parameter visibility fitting and two-component self-calibration loop
- Missing: Exact CASA tclean imaging parameters (cell size, image size, weighting/robust, cleaning mask, stopping threshold)
- Missing: Exact definition of the running median window size and flagging thresholds for high-rms visibilities
- Data volume (inferred): ~50-200 GB (three 4-10 hour tracks of 37-antenna 12m data with 4 spectral windows of 240 channels at 4-second integration time, plus thousands of snapshot images)
- Score (inferred): 55/5, The mathematical formulation of the two-component self-calibration and the transient selection criteria are thoroughly documented, including full Hessian expressions in the Appendix, and the ALMA data are public EHT 2017 campaign observations. However, the custom self-calibration code is not released, and key CASA tclean imaging parameters (pixel size, image dimensions, weighting, masks) and running-median window sizes are omitted.
- Rediscovery candidate: no, Although the underlying 2017 EHT ALMA dataset is public and the mathematical recipe is well described, the primary scientific result is a non-detection relying on unshared custom calibration scripts and manual visual inspection of dynamic-range-limited snapshot residuals.

## Links

- Method: (cite: Wielgus21) (Introduces the two-component (Sgr A* plus mini-spiral) visibility modeling and intra-source amplitude scaling methodology adapted in this work)
- Method: (cite: CiriacoRefMini) (Describes the initial visibility calibration and mini-spiral modeling for the 2017 ALMA-VLBI observations of Sgr A*)
- Method: (cite: CiriacoRefb) (Details the ALMA Phasing System QA2 calibration pipeline and subscan flagging procedures)
- Method: (cite: APPRef) (Describes the ALMA Phasing Project hardware and VLBI phased-array operational framework)
- Companion: (cite: EHT1; EHT2; EHT3; EHT4; EHT5; EHT6) (Main Event Horizon Telescope Collaboration 2017 Sgr A* campaign papers from which the 230 GHz ALMA observations originate)
- Companion: (cite: Wielgus21) (Companion EHT light-curve paper analyzing the 2017 ALMA millimeter variability of Sgr A* on the same tracks)
- Related: Event Horizon Telescope (EHT) 2017 campaign
- Related: ALMA Phasing Project (APP)

## Checks

```json
{
 "quotes": 114,
 "quotes_ok": 114,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 22,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.01154.V"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 58,
  "rate": 0.725
 },
 "evidence_ok": true
}
```
