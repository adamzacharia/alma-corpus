# Characterizing the Accuracy of ALMA Linear-polarization Mosaics

`2020PASP..132i4501H` | Publications of the Astronomical Society of the Pacific 2020 | first author: Hull, Charles L. H. | arXiv: 2006.03671 | DOI: 10.1088/1538-3873/ab99cd

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, star_formation
- Question: How accurate are ALMA linear-polarization observations away from the pointing center, and how much do mosaics of overlapping pointings reduce the residual off-axis errors  
  > "A primary reason for characterizing the wide-field polarization performance of ALMA antennas is to understand the effect that wide-field polarization errors have in a polarization mosaic, where many pointings are stitched together." (Introduction)
- Target **3C 279**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Orion-KL**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00007.E, 2011.0.00008.E, 2011.0.00009.E
- bands: 3C 279: Bands 3, 5, 6, 7 (3, 1.6, 1.3, 0.87 mm); Orion-KL: Bands 3 and 6  
  > "at Bands 3, 5, 6, and 7 (3 mm, 1.6 mm, 1.3 mm, and 0.87 mm, respectively)" (abstract); "We observed Orion-KL using the 12 m array at Bands 3 and 6." (Orion-KL mosaic observations)
- frequencies and spectral setup: Standard correlator setup for continuum polarization: four 1.875 GHz-wide spectral windows with 64 channels each  
  > "which includes four 1.875 GHz-wide spectral windows with 64 channels each" (11x11 observations of 3C 279); "and had the standard correlator setup for continuum polarization observations" (Orion-KL mosaic observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "We observed Orion-KL using the 12 m array at Bands 3 and 6." (Orion-KL mosaic observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Orion-KL synthesized beams 1.43'' x 0.95'' (Band 3) and 0.65'' x 0.48'' (Band 6)  
  > "resulting in maps with synthesized beams (resolution elements) of 1.43$''$ $\times$ 0.95$''$ at Band 3 and 0.65$''$ $\times$ 0.48$''$ at Band 6." (Orion-KL mosaic observations)
- max recoverable scale: _not stated_
- sensitivity: Theoretical Stokes I sensitivity per pointing ~30 uJy/beam (Band 3, 7 min per field) and ~79 uJy/beam (Band 6, 2.2 min per field)  
  > "is estimated to be $\sim$ 30 $\mu$Jy beam$^{-1}$ given 7 min of integration time per field" (Footnote 9); "We see a similar situation in the Band 6 data, where the theoretical sensitivity $\sigma_I$ is $\sim$ 79 $\mu$Jy beam$^{-1}$ given 2.2 min of integration per field" (Footnote 9)
- time on source: Orion-KL: 7 min per field (Band 3), 2.2 min per field (Band 6)  
  > "given 7 min of integration time per field" (Footnote 9); "given 2.2 min of integration per field" (Footnote 9)
- observing dates: 3C 279: 2015 Mar 06 (B3), 2016 Nov 10 (B5), 2015 May 08 (B6), 2015 May 09 (B7); Orion-KL: 2018 Mar 17-18 (B3), 2019 Apr 12 (B6)  
  > "2015 Mar 06" (Table 1); "2016 Nov 10" (Table 1); "2019 Apr 12" (Table 3)
- pi or archival as stated: ALMA data from the ALMA Extension and Optimization of Capabilities (EOC) program; the CARMA comparison data are archival  
  > "were collected as part of the ALMA Extension and Optimization of Capabilities (EOC) program." (Introduction); "Here we compare those archival data from an independent instrument with our ALMA results" (Comparison with CARMA)
- Other facility **CARMA**: Archival 1.3 mm CARMA polarization mosaic of Orion-KL (Hull et al. 2014), taken in 2013, seven pointings, used for comparison with the ALMA mosaics  
  > "The 1.3 mm CARMA data were taken in 2013" (Comparison with CARMA); "and comprise a seven-pointing mosaic with a field of view similar to that of our ALMA observations" (Comparison with CARMA)
- External data: Archival 1.3 mm CARMA full-polarization mosaic of Orion-KL  
  > "Another mosaicked polarization observation of Orion-KL was performed by (cite: Hull2014)" (Comparison with CARMA) [from (cite: Hull2014)]
- External data: On-axis ALMA polarization angle uncertainty of ~0.4 deg used as a reference level  
  > "on-axis uncertainty of $\sim$ 0.4$\degree$ in the polarization angle calculated by (cite: Nagai2016)" (11x11 observations of 3C 279) [from (cite: Nagai2016)]

## Processing

### Calibration

- pipeline or manual: Manual on-axis polarization calibration with the standard ALMA polarization scheme, all steps done on 3C 279 for the 11x11 data  
  > "we perform every step of the reduction process using 3C 279" (11x11 observations of 3C 279); "we use these on-axis data to derive the on-axis polarization calibration via the current ALMA polarization calibration scheme" (11x11 observations of 3C 279)
- casa version: CASA 5.6.1 (11x11 imaging); CASA 5.4.0 (Orion-KL imaging); calibration version not stated  
  > "from CASA version 5.6.1 with standard imaging parameters" (11x11 observations of 3C 279); "from CASA version 5.4.0, using standard imaging parameters" (Orion-KL mosaic observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Orion-KL: flux scaling from the bandpass calibrator J0423-0120 and the polarization calibrator J0522-3627  
  > "We derive the bandpass solutions and the flux scaling from both the bandpass calibrator (J0423–0120) and the polarization calibrator (J0522–3627)" (Orion-KL mosaic observations)
- flux scale uncertainty: _not stated_
- self calibration: 3C 279: one round of phase-only self-calibration on every pointing; Orion-KL: none  
  > "we perform one round of phase-only self-calibration (selfcal) to correct the residual phase errors as a function of time for both the on-axis data and each off-axis pointing" (11x11 observations of 3C 279); "we do not perform self-calibration on any of the images of Orion-KL" (Orion-KL mosaic observations)

### Imaging

- task: 3C 279: clean (CASA 5.6.1); Orion-KL: tclean (CASA 5.4.0)  
  > "we produce $I$, $Q$, $U$, $V$ images using the task `clean` from CASA version 5.6.1" (11x11 observations of 3C 279); "We image the data using the task `tclean` from CASA version 5.4.0" (Orion-KL mosaic observations)
- deconvolver: _not stated_
- weighting robust: 3C 279: Briggs robust = 2.0 (natural weighting); Orion-KL: robust = 0.5  
  > "a Briggs visibility weighting of `robust` = 2.0 (i.e., natural weighting)" (11x11 observations of 3C 279); "a Briggs visibility weighting of `robust` = 0.5" (Orion-KL mosaic observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: None; spectral lines were not flagged before continuum imaging of Orion-KL  
  > "spectral lines were not flagged prior to making the continuum images (the default Band 6 spectral setup avoids major lines of interest)" (Orion-KL mosaic observations)
- line free channels: _not stated_
- primary beam correction: impbcor to the 20% sensitivity level of the Stokes I primary beam model (Orion-KL)  
  > "We primary-beam correct the final images using the CASA task `impbcor` to the 20% sensitivity level of the Stokes $I$ primary beam model." (Orion-KL mosaic observations)
- array combination: No total-power (single-dish) combination attempted  
  > "by combining the ALMA observations with total-power (single-dish) observations, but we do not attempt this here" (Footnote 10)
- smoothing: For the CARMA comparison: uvrange matched in clean and ALMA beam smoothed to the CARMA beam with imsmooth  
  > "we match the $uv$-range (using the `uvrange` keyword in the CASA task `clean`) and the synthesized-beam size (using the CASA task `imsmooth`) of the Band 3 and Band 6 ALMA data to those of CARMA" (Comparison with CARMA)
- final beam: Orion-KL: 1.43'' x 0.95'' (Band 3), 0.65'' x 0.48'' (Band 6)  
  > "resulting in maps with synthesized beams (resolution elements) of 1.43$''$ $\times$ 0.95$''$ at Band 3 and 0.65$''$ $\times$ 0.48$''$ at Band 6." (Orion-KL mosaic observations)
- final rms: Orion-KL Stokes I noise ~100 uJy/beam (Band 3 mosaics) and ~2 mJy/beam (Band 6)  
  > "whereas the estimated noise level in all of the Band 3 mosaic images is $\sim$ 100 $\mu$Jy beam$^{-1}$" (Footnote 9); "whereas the estimated noise from the Stokes $I$ maps is $\sim$ 2 mJy beam$^{-1}$" (Footnote 9)

### Inherited from earlier work

- Standard on-axis reduction of ALMA polarization data  
  > "For further details about standard, on-axis reduction of ALMA polarization data, see (cite: Nagai2016) as well as the 3C 286 Polarization CASA Guide." (11x11 observations of 3C 279) [from (cite: Nagai2016); 3C 286 Polarization CASA Guide]
- Orion-KL calibration follows standard ALMA polarization procedures  
  > "We calibrate the data using the standard procedures for processing ALMA polarization observations (see, e.g., (cite: Cortes2016; Nagai2016; Hull2017b; Hull2018a))." (Orion-KL mosaic observations) [from (cite: Cortes2016; Nagai2016; Hull2017b; Hull2018a)]
- Orion-KL observed in the standard sessions mode for ALMA polarization  
  > "The data were taken in the standard sessions mode used for ALMA polarization observations (cite: THB)" (Orion-KL mosaic observations) [from (cite: THB)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, masks, threshold, niter and deconvolver for clean/tclean in both datasets (only 'standard imaging parameters' given)
- Which fields and scans were treated as on-axis, and the self-calibration solution interval for the 3C 279 data
- CASA version used for calibration (only imaging versions are given)
- Which pointings of each 11x11 grid and which Orion-KL pointings were combined for each statistic, and exact pixel-selection regions for the inner 1/3 FWHM and donut
- Primary-beam FWHM values adopted per band for the inner and donut radii
- Exact definition of the polarization-angle error cutoffs applied in the 11x11 error maps
- Flux values and Stokes model assumed for the polarization calibrator J0522-3627 in the Orion-KL reduction

## Analysis recipe

1. **calibrate 3C 279 on-axis polarization**: Use the on-axis scans of 3C 279 to solve gains, cross-hand delay, XY-phase (ambiguity-resolved with xyamb) and D-terms with the standard ALMA polarization scheme  
  > "we use these on-axis data to derive the on-axis polarization calibration via the current ALMA polarization calibration scheme" (11x11 observations of 3C 279)
   - software: CASA, almapolhelpers.py (qufromgain, xyamb)
   - parameter: Cross-hand delay solved on the scans where the XX/YY ratio changes fastest  
  > "Next, we solve for the cross-hand delay using the scans where the $XX$/$YY$ polarization ratio is changing the fastest" (11x11 observations of 3C 279)
   - parameter: Three executions spaced ~1 hr give parallactic angle coverage for D-terms and XY-phase  
  > "which yields sufficient parallactic angle coverage to allow us to solve for the leakage terms" (11x11 observations of 3C 279)
   - assumption: Initial unpolarized source model for 3C 279, then polarization model from qufromgain and xyamb  
  > "assuming an initial unpolarized source model for 3C 279" (11x11 observations of 3C 279)
   - assumption: Calibrator Stokes V = 0  
  > "includes the assumption that the calibrator Stokes $V = 0$" (Footnote 5)
   - fitting: _not stated_
   - validation: _not stated_
2. **apply on-axis calibration to all pointings and self-calibrate**: Apply on-axis tables to all on- and off-axis data, then one round of phase-only self-calibration per pointing  
  > "we perform one round of phase-only self-calibration (selfcal) to correct the residual phase errors as a function of time for both the on-axis data and each off-axis pointing" (11x11 observations of 3C 279)
   - software: CASA
   - parameter: D-terms and XY-phase solved from on-axis data only, to mimic standard ALMA polarization calibration  
  > "this includes $D$-terms and $XY$-phase" (11x11 observations of 3C 279); "We do this to mimic the standard calibration method of ALMA polarization data." (11x11 observations of 3C 279)
   - fitting: _not stated_
   - validation: _not stated_
3. **image Stokes I,Q,U,V and measure peaks**: Make I,Q,U,V images with clean and extract peak values with imfit  
  > "we extract the $I$, $Q$, $U$, $V$ peak values using the CASA task `imfit`" (11x11 observations of 3C 279)
   - software: CASA clean, CASA imfit
   - parameter: Briggs robust = 2.0 (natural weighting), CASA 5.6.1  
  > "a Briggs visibility weighting of `robust` = 2.0 (i.e., natural weighting)" (11x11 observations of 3C 279)
   - fitting: _not stated_
   - validation: Stokes I dynamic range 10,000-100,000, P maps always >1000, so sensitivity does not explain the offset-pointing variations  
  > "are not caused by sensitivity limits, but rather by systematic polarization variations across the primary beam" (11x11 observations of 3C 279)
4. **derive off-axis error maps in Q, U, chi and Pfrac**: Divide off-axis Q and U by off-axis I, subtract the on-axis values to get dQ and dU, and take on- versus off-axis differences for chi and Pfrac  
  > "We then subtract the on-axis Stokes $Q_\textrm{on}$ or $U_\textrm{on}$ value from the normalized value in each pixel, leaving the residual errors $\delta Q$ and $\delta U$" (Results: 11x11 observations of 3C 279); "In the error maps of $\chi$ and $P_\textrm{frac}$, we subtract the central value from each pixel." (Results: 11x11 observations of 3C 279)
   - assumption: Circular, azimuthally symmetric primary beam in Stokes I  
  > "Assuming a circular, azimuthally symmetric primary beam in Stokes $I$" (Results: 11x11 observations of 3C 279)
   - fitting: _not stated_
   - validation: _not stated_
5. **calibrate the Orion-KL mosaic data**: Standard ALMA polarization calibration with J0522-3627 as polarization calibrator, J0423-0120 bandpass calibrator and J0529-0519 gain calibrator  
  > "We use J0522–3627 as the polarization calibrator, J0423–0120 as the bandpass calibrator, and J0529–0519 as the gain calibrator." (Orion-KL mosaic observations)
   - software: CASA
   - parameter: Bandpass scan taken only in the first execution of each session  
  > "A bandpass scan was performed only in the first execution of the observing session." (Orion-KL mosaic observations)
   - fitting: _not stated_
   - validation: _not stated_
6. **image each Orion-KL mosaic pattern separately**: Image Hyper-Nyquist, Super-Nyquist, Nyquist and single-field subsets independently with tclean, Stokes I, Q, U cleaned separately, then primary-beam correct and form P, Pfrac, chi  
  > "We independently image all four cases (i.e., Hyper-Nyquist, Super-Nyquist, Nyquist, and single field) in order to compare them with one another." (Orion-KL mosaic observations); "For each of the four patterns, we clean the Stokes $I$, $Q$, and $U$ maps separately." (Orion-KL mosaic observations)
   - software: CASA tclean, CASA impbcor, CASA imregrid
   - parameter: Briggs robust = 0.5  
  > "a Briggs visibility weighting of `robust` = 0.5" (Orion-KL mosaic observations)
   - assumption: Primary beam of each pointing is a 2D Gaussian peaked at the pointing center  
  > "The primary beam of each mosaic pointing is assumed (in CASA) to be a 2D Gaussian peaked at the center of the pointing." (Orion-KL mosaic observations)
   - fitting: _not stated_
   - validation: _not stated_
7. **compare mosaics with the inner 1/3 FWHM of single pointings in I, Q, U**: Build difference maps (mosaic minus single pointing) with immath, with and without a 5 sigma cutoff, and extract the inner 1/3 FWHM with imsubimage  
  > "where the cutoff limits the difference images to the region(s) where the emission in the single pointing images is 5 $\times$ the rms noise level" (Results: Orion-KL mosaic observations)
   - software: CASA immath, CASA imsubimage
   - fitting: _not stated_
   - validation: Difference-histogram widths compared with the rms noise of the single-pointing images  
  > "standard deviations that tend to be well below the rms noise level in the single-pointing images" (Results: Orion-KL mosaic observations)
8. **compare polarization angle in mosaic versus single pointings**: Difference maps of chi (Hyper-Nyquist mosaic minus single pointing) for the Band 3 data, histogrammed in the inner 1/3 FWHM and the outer donut, plus median differences in high-SNR patches  
  > "We compute difference maps of the polarization position angle $\chi$ in the Hyper-Nyquist mosaic versus single-pointing images in the same manner as described above." (Comparison of chi in the mosaics versus the inner region and outer donut region of single pointings)
   - software: CASA
   - parameter: 5 sigma_P cutoff in the chi maps  
  > "We use a conservative (5 $\sigma_P$) cutoff in the $\chi$ maps" (Comparison of chi in the mosaics versus the inner region and outer donut region of single pointings)
   - fitting: _not stated_
   - validation: High-SNR patches have P SNR > 15, corresponding to ~2 deg statistical uncertainty  
  > "corresponding to a statistical uncertainty of $\sim$ 2$\degree$" (Comparison of chi in the mosaics versus the inner region and outer donut region of single pointings)
9. **compare ALMA mosaics with archival CARMA mosaic**: Match uv-range and beam of ALMA Nyquist mosaics to CARMA, regrid to CARMA coordinates, then difference chi  
  > "We also re-grid the ALMA images to match the coordinates of the CARMA maps." (Comparison with CARMA); "We use the standard Nyquist mosaic pattern from our ALMA data for the comparison with the CARMA observations" (Comparison with CARMA)
   - software: CASA clean (uvrange), CASA imsmooth
   - assumption: Optically thin dust with grain alignment by radiative torques, so inferred field orientation is frequency independent  
  > "under the standard assumption that dust-grain alignment via radiative alignment torques (cite: Lazarian2007) is the cause of the dust polarization" (Comparison with CARMA)
   - fitting: _not stated_
   - validation: CARMA on-axis systematic angle error +-3 deg and ALMA < 1 deg quoted as reference  
  > "which is the result of systematic errors in the $XY$-phase correction" (Comparison with CARMA)
10. **estimate mosaic errors from the 11x11 data**: Standard error propagation from sigma_Q and sigma_U measured in the ring 1/3 FWHM < r < FWHM, versus direct standard deviation of the dPfrac and dchi maps  
  > "In order to estimate the error in the regions of a mosaic where multiple pointings overlap, we first use standard error propagation of the values in the maps of $\delta Q$ and $\delta U$." (Appendix 6.2)
   - assumption: sigma_Q approximately equals sigma_U equals sigma_P; no position-dependent error in Stokes I  
  > "this is justified since, almost always, $\sigma_Q \approx \sigma_U$" (Appendix 6.2)
   - fitting: _not stated_
   - validation: Two estimates agree within factors of <40% (Pfrac) and <30% (chi)  
  > "As mentioned above, the resulting errors are conservatively large, as they are derived from the entire region between the $\frac{1}{3}$ FWHM and the FWHM." (Appendix 6.2)

## Software

- **CASA** 5.6.1 (3C 279 imaging); 5.4.0 (Orion-KL imaging): Calibration, imaging (clean/tclean), imfit, immath, imsubimage, imregrid, impbcor, imsmooth  
  > "CASA (cite: McMullin2007)" (Acknowledgments); "We first produce difference maps (i.e., Hyper-Nyquist minus single pointing, Super-Nyquist minus single pointing, and Nyquist minus single pointing) for $I$, $Q$, and $U$ using the CASA task `immath`." (Results: Orion-KL mosaic observations)
- **almapolhelpers.py** : qufromgain for the first estimate of 3C 279 polarization; xyamb to resolve XY-phase ambiguity  
  > "we use the task `qufromgain` from `almapolhelpers.py`" (11x11 observations of 3C 279); "which we resolve by using the task `xyamb`" (11x11 observations of 3C 279)
- **APLpy** : Plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)
- **Astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Residual Pfrac and chi errors inside inner 1/3 FWHM (3C 279, all bands) | Pfrac <~ 0.001 (<~0.1% of I); chi <~ 1 deg | not stated | dimensionless; deg | 4 | the residual errors in $P_\textrm{frac}$ and $\chi$ are $\lesssim$ 0.001 ($\lesssim$ 0.1% of Stokes $I$) and $\lesssim$ 1$\degree$, respectively |
| Pfrac and chi errors near the FWHM of the primary beam (3C 279, all bands) | Pfrac ~0.003-0.005 (~0.3-0.5% of I); chi ~1-5 deg | not stated | dimensionless; deg | 4 | Near the FWHM, the errors increase to $\sim$ 0.003–0.005 ($\sim$ 0.3–0.5% of Stokes $I$) and $\sim$ 1–5$\degree$, respectively |
| Stokes V beam squint amplitude relative to on-axis Stokes I | 1-2% | not stated | percent of Stokes I | 3 | Each Stokes $V$ map exhibits a double-lobed “beam squint” pattern at the 1–2% level of the on-axis Stokes $I$ value |
| Stokes I dynamic range in 3C 279 maps | ~10,000-100,000 (lowest at Band 7, highest at Band 3) | not stated | dimensionless | 3 | in the Stokes $I$ continuum maps ranges from $\sim$ 10,000–100,000 |
| 3C 279 polarization fraction at observation | ~12% | not stated | dimensionless (percent) | 3 | which had $P_\textrm{frac} \approx 12\%$ at the time of observation |
| Orion-KL median polarization fraction in mosaics (Bands 3 and 6) | ~6-7% | not stated | percent | 6 | The mosaicked images of Orion-KL at both Bands 3 and 6 have median levels of $P_\textrm{frac} \approx 6-7\%$ across the maps. |
| Median SNR across the Orion-KL P maps (Bands 3 and 6) | 7-8 | not stated | dimensionless | 6 | the median SNR values across the $P$ maps at Bands 3 and 6 are between 7–8 |
| Std of chi differences in outer donut, single pointings 6 and 10 vs Hyper-Nyquist mosaic (Band 3) | 3.6 deg (point 6), 2.7 deg (point 10) | not stated | deg | 8 | having standard deviations of 3.6$\degree$ (point 6) and 2.7$\degree$ (point 10) |
| Median chi difference when emission is viewed off-axis (near FWHM of point 8) versus Hyper-Nyquist mosaic | ~3 deg | not stated | deg | 8 | the median difference with respect to the Hyper-Nyquist mosaic is $\sim$ 3$\degree$ |
| chi differences in inner 1/3 FWHM, Hyper-Nyquist mosaic vs single pointings (Band 3) | ~1 deg | not stated | deg | 8 | show that the differences are $\sim$ 1$\degree$ |
| Width of ALMA minus CARMA chi difference distribution (68% window) | +-12 deg | not stated | deg | 9 | with a width (defined as the minimum window necessary to encompass 68% of the data) of $\pm$ 12$\degree$ |

## Qualitative findings

- Off-axis Q and U errors come from beam squash (different widths of the orthogonal linear beams); the 11x11 grids only sample its inner part  
  > "The quadrupolar squash error patterns are approximately twice the linear extent of the double-lobed beam squint patterns" (Conclusions)
- Errors in the inner 1/3 FWHM of Orion-KL Q, U and I difference maps are dominated by missing large-scale emission, not off-axis polarization errors  
  > "are primarily caused by imaging artifacts stemming from the inability of our ALMA observations to recover emission at large spatial scales in Orion-KL" (Conclusions)
- No mosaic packing tighter than Nyquist is recommended for sources with complex multi-scale structure  
  > "we cannot recommend using a mosaic packing that is tighter than the standard Nyquist pattern" (Conclusions)

## Claim tuples

- H: Do residual polarization errors in single ALMA pointings stay small after on-axis calibration across the primary beam? | E: 11x11 grid of offset pointings on 3C 279 at Bands 3, 5, 6, 7 calibrated on-axis only | R: Pfrac and chi errors <~0.001 and <~1 deg in inner 1/3 FWHM, rising to ~0.003-0.005 and ~1-5 deg near FWHM | F: Residual errors are similar at all bands and modest near the beam center, larger near the FWHM | **supported**
- H: Are beam squint and beam squash visible in the 11x11 data? | E: Stokes V and Q/U error maps of the 3C 279 grids | R: Double-lobed squint at 1-2% of I in V; inner edge of the cloverleaf squash pattern in Q and U at Bands 3 and 7 | F: Squint is seen at all bands; squash is only partly sampled by the grid | **partially**
- H: Does mosaicking reduce off-axis polarization errors, and does denser packing help further? | E: Orion-KL Hyper-Nyquist, Super-Nyquist, Nyquist mosaics and single pointing at Bands 3 and 6, chi difference maps and histograms | R: Median chi differences <1 deg on-axis versus ~2-4 deg off-axis; no detectable difference among the three mosaic densities | F: Mosaicking improves accuracy over single pointings, but tighter-than-Nyquist packing gives no detectable gain | **partially**
- H: Are the ALMA Orion-KL polarization patterns consistent with an independent CARMA mosaic? | E: Match uv-range and beam, regrid, and difference chi of ALMA Band 3 and 6 mosaics against the archival 1.3 mm CARMA mosaic | R: Distribution of chi differences peaks near 0 deg with a 68% width of +-12 deg | F: Good consistency of polarization position angles, especially in the Northern Ridge | **supported**

## Reasoning

- Why this data: 3C 279 was extremely bright and highly linearly polarized at the time  
  > "We chose to observe 3C 279 because, at the time of observation in 2015/2016, it was both extremely bright and had an extremely high linear polarization fraction." (11x11 observations of 3C 279)
- Why this method: A full-array grid of offset pointings on a polarized point source characterizes the wide-field polarization errors across the primary beam  
  > "another method of characterizing the wide-field polarization errors across the primary beam of an interferometer is to use the full array to perform a grid of observations" (Introduction)
- Alternative: Fractional polarization errors not analyzed for Orion-KL because Q, U and I have different spatial structure; better done on point sources  
  > "When analyzing the Orion-KL results, we choose not to analyze the fractional polarization errors" (Results: Orion-KL mosaic observations)
- Alternative: Total-power (single-dish) combination not attempted  
  > "but we do not attempt this here" (Footnote 10)
- How they decided it was enough: Three executions spaced ~1 hr give enough parallactic angle coverage to solve D-terms and XY-phase  
  > "which yields sufficient parallactic angle coverage to allow us to solve for the leakage terms ($D$-terms) and the cross-hand phase ($XY$-phase)" (11x11 observations of 3C 279)
- Limitation (authors): 11x11 grid extent is too small to sample the full beam-squash pattern  
  > "and thus the extent of the 11$\times$11 observations is not sufficient to sample the entire pattern" (Q and U errors (beam squash))
- Limitation (authors): Orion-KL maps are dynamic-range limited, not thermal-noise limited  
  > "Note also that the maps are dynamic range limited; in no case have we reached the thermal noise limit." (Results: Orion-KL mosaic observations)
- Caveat (inferred, ours): Orion-KL mosaic comparison is limited by missing short spacings, so off-axis effects at the ~1 deg level are hard to separate from imaging artifacts
- Caveat (inferred, ours): Only one source (3C 279) and one night per band for the 11x11 grids; time variability of D-terms not tested
- Caveat (inferred, ours): Imaging parameters are only 'standard', so exact numbers may not reproduce without the released scripts
- Caveat (inferred, ours): Orion-KL chi analysis uses Band 3 only

## Reproducibility

- Data public (paper): Raw data and scripts are in the ALMA Science Archive under the listed EOC project codes  
  > "They can be found, along with the raw data, by visiting the ALMA Science Archive and searching for the ALMA project codes listed in the acknowledgements section." (Acknowledgments)
- Products in archive: Reduction and imaging scripts publicly available  
  > "All of the reduction and imaging scripts used to produce the results from this paper are publicly available." (Acknowledgments)
- Code: Reduction and imaging scripts released via the ALMA Science Archive  
  > "All of the reduction and imaging scripts used to produce the results from this paper are publicly available." (Acknowledgments)
- Missing: Full clean/tclean parameter set (cell, image size, masks, thresholds)
- Missing: Region and pointing selections for statistics
- Missing: Numeric values for the Q/U/chi error maps are only in figures
- Data volume (inferred): Large: 4 bands x 3 executions x 121 pointings of 3C 279, plus 5 Orion-KL executions of 15- and 45-pointing mosaics; likely tens to hundreds of GB raw
- Score (inferred): 4/5, Public EOC data and public reduction scripts exist, key task versions and calibrators are given, and results are numeric, but imaging parameters and region choices are not spelled out in the paper.
- Rediscovery candidate: yes, Data and scripts are public, the recipe is largely described, and the main results are numeric error levels; the work is data-heavy.

## Links

- Method: Nagai et al. 2016 (cite: Nagai2016) (Standard on-axis ALMA polarization calibration and its angle uncertainty)
- Method: Hull & Plambeck 2015 (cite: Hull2015b) (CARMA full-polarization system used for the comparison data)
- Companion: Cortes et al. 2020 (cite: Cortes2020) (Companion paper using the same EOC data)
- Companion: Hull et al. 2014 (cite: Hull2014) (Archival CARMA mosaic of Orion-KL)
- Related: ALMA Extension and Optimization of Capabilities (EOC) program

## Checks

```json
{
 "quotes": 113,
 "quotes_ok": 113,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00007.E",
  "2011.0.00009.E"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 107,
  "stated": 71,
  "rate": 0.664
 },
 "evidence_ok": true
}
```
