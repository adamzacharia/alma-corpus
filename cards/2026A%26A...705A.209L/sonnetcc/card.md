# A search for cold molecular outflows in cosmic-noon galaxies

`2026A&A...705A.209L` | Astronomy and Astrophysics 2026 | first author: Langan, I. | arXiv: 2511.16733 | DOI: 10.1051/0004-6361/202554297

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Do typical main-sequence star-forming galaxies at cosmic noon (z_med~1.3) show cold molecular gas extended to CGM scales or broad CO(2-1) wings indicating molecular outflows, via stacking of ALMA Band 3 CO(2-1) data compared with Ks-band stellar emission  
  > "we aim to search for cold molecular gas in the CGM of typical main-sequence (MS) star-forming galaxies (SFGs) at cosmic noon" (abstract); "We also search for broad wings in the stacked spectrum which can be indicative of ongoing outflows." (abstract)
- Target **26 CO(2-1)-detected SFGs from the Valentino et al. 2020 COSMOS sample (IDs listed in appendix tables)**: coordinates per-galaxy RA/DEC given in the appendix table (COSMOS field)  
  > "In the end, our sample contains 26 galaxies, with CO(2–1) emission line detection with" (Observations and sample description); "redshifts $z=1.15-1.63$" (Observations and sample description); "The sample is located in the COSMOS field" (Observations and sample description); z/distance z = 1.15-1.63 (median z_med ~ 1.3)  
  > "In the end, our sample contains 26 galaxies, with CO(2–1) emission line detection with" (Observations and sample description); "redshifts $z=1.15-1.63$" (Observations and sample description); "The sample is located in the COSMOS field" (Observations and sample description); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00171.S
- bands: Band 3, CO(2-1)  
  > "observed with the Atacama Large Millimeter and submillimeter Array (ALMA) in band 3, targeting the CO(2–1) emission line" (Observations and sample description)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 5 galaxies had multiple executions in very different array configurations; only executions giving ~1.5 arcsec beam were used  
  > "For 5 galaxies the ALMA observations consisted of multiple executions taken with very different array configurations" (Observations and sample description)
- baselines: _not stated_
- angular resolution: homogeneous ~1.5 arcsec  
  > "These observations are taken with a homogenous resolution" (Observations and sample description)
- max recoverable scale: _not stated_
- sensitivity: average 0.60 mJy/beam per 30 km/s channel (0.73 mJy/beam for the 5 multi-execution galaxies)  
  > "average sensitivity of 0.60 mJy/beam in channels of" (Observations and sample description); "which results in cleaned CO(2–1) cubes with an average sensitivity of 0.73 mJy/beam in channels of" (Observations and sample description)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival ALMA Cycle 4 programme, PI E. Daddi; observations originally reported in Valentino et al. 2020  
  > "These galaxies are part of an ALMA cycle 4 programme (#2016.1.00171.S, PI: E. Daddi)" (Observations and sample description); "we stacked the ALMA archival CO(2–1) intensity maps of our sample" (Summary and outlook)
- Line: CO J=2-1 (not stated)
- Other facility **VISTA/VIRCAM Ks (UltraVISTA), via IRSA COSMOS cutout service**: Ks-band cutouts tracing the stellar component of the sample  
  > "generate cutouts of the VISTA telescope data in the with VIRCAM/Ks filters" (Observations and sample description); "We specifically use the IRSA COSMOS cutout service" (Observations and sample description)
- Other facility **Herschel**: original identification of the SFGs in COSMOS  
  > "originally identified by Herschel in the COSMOS area" (Observations and sample description)
- External data: CO(2-1) observations description and per-galaxy stellar mass, infrared luminosity and SFR measurements for the sample  
  > "for a complete report of the observations" (Observations and sample description); "stellar mass and infrared luminosity measurements" (Observations and sample description) [from Valentino et al. 2020 (cite: Valentino2020)]
- External data: Ks-band PSF information used to build the 2D Moffat PSF model (UltraVISTA / ESO programme 179.A-2005)  
  > "to compute a 2D PSF Moffat model with FWHM" (Comparison to the stellar component) [from McCracken et al. 2012 (cite: McCracken2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 6.5.5.21 (used for the reduction steps described: uvcontsub, tclean, immoments); calibration itself not described  
  > "We use the Common Astronomy Software Applications (CASA 6.5.5.21) data processing software" (Observations and sample description)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean with natural weighting, 30 km/s channels  
  > "We image the CO(2–1) emission with natural weighting and channel width" (Observations and sample description)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We image the CO(2–1) emission with natural weighting and channel width" (Observations and sample description)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane, polynomial of order 0 (uvcontsub)  
  > "We subtract the continuum in the uv-plane with a polynomial of order 0" (Observations and sample description)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: none; for the 5 multi-execution galaxies only executions giving ~1.5 arcsec beam were used  
  > "For those 5 galaxies we only use the observations providing a beam size of" (Observations and sample description)
- smoothing: spectra rebinned from 30 to 60 km/s for the stacked-spectrum analysis  
  > "We rebin the spectra to 60" (Spectrum stacking)
- final beam: ~1.5 arcsec average  
  > "These observations are taken with a homogenous resolution" (Observations and sample description)
- final rms: average 0.60 mJy/beam per 30 km/s channel (0.73 mJy/beam for 5 multi-execution galaxies)  
  > "average sensitivity of 0.60 mJy/beam in channels of" (Observations and sample description)

### Inherited from earlier work

- Full report of the ALMA observations (and sample selection/properties) is deferred to the earlier paper  
  > "for a complete report of the observations" (Observations and sample description) [from Valentino et al. 2020 (cite: Valentino2020)]
- Definition of MS versus starburst bins by distance to the main sequence (3.5 times)  
  > "(following the definition set in" (Subsample intensity map stacks) [from Valentino et al. 2020 (cite: Valentino2020)]
- Ks-band PSF parameters taken from the UltraVISTA survey paper  
  > "to compute a 2D PSF Moffat model with FWHM" (Comparison to the stellar component) [from McCracken et al. 2012 (cite: McCracken2012)]
- Exclusion of ID 51599 because its CO(2-1) shows signs of merging  
  > "shows signs of merging (ID 51599, see" (Observations and sample description) [from Langan et al. 2024 (cite: Langan2024)]

### Not stated but needed to reproduce (our reading)

- Calibration route (pipeline vs manual), CASA pipeline version and flux calibrator/flux-scale handling for the 2016.1.00171.S data
- tclean parameters: image size, cell size, deconvolver, niter/threshold, masking, restoring beam handling and whether maps are primary-beam corrected
- Spectral window, rest frequency and line-free channel ranges used for uvcontsub and the cube frequency range
- Which phase centre or position defines the 'centre of the cube' for the 2 arcsec aperture and how the peak is re-centred
- Gaussian fit details (initial guesses, bounds, fit routine) and how the 1 sigma noise used for perturbations is measured
- Two-Gaussian fit constraints (width and centre bounds, initial guesses) and the degrees of freedom used for reduced chi-squared
- Sersic fit routine and weighting; how the normalisation by the peak and radial-profile centring are done
- Richardson-Lucy iteration count and Ks cutout size, and the sigma-clipping/segmentation thresholds used in photutils
- Number of galaxies per bin in the subsample stacks, and the exact IDs of the 5 multi-execution galaxies

## Analysis recipe

1. **Select the sample**: Take the S/N>=3 CO(2-1) detections from the 75-SFG ALMA programme, remove a merger and galaxies without stellar mass, leaving 26 galaxies  
  > "we select the galaxies with a detection of the CO(2–1) emission line at a signal-to-noise ratio" (Observations and sample description); "In the end, our sample contains 26 galaxies, with CO(2–1) emission line detection with" (Observations and sample description)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make continuum-subtracted CO(2-1) cubes**: uv-plane continuum subtraction then tclean imaging with natural weighting and 30 km/s channels, homogeneously for all galaxies  
  > "We subtract the continuum in the uv-plane with a polynomial of order 0" (Observations and sample description); "We image the CO(2–1) emission with natural weighting and channel width" (Observations and sample description)
   - software: CASA, uvcontsub, tclean
   - parameter: continuum polynomial order 0; natural weighting; 30 km/s channels  
  > "We subtract the continuum in the uv-plane with a polynomial of order 0" (Observations and sample description)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract each galaxy spectrum and fit a Gaussian**: Extract spectrum in a 2 arcsec radius aperture at the cube centre, perturb it by its 1 sigma noise, fit a Gaussian, repeat 500 times and take the median fit  
  > "radius aperture located at the centre of the cube" (Intensity map stacking); "We repeat this noise perturbation procedure 500 times and take the median fit of those 500 iterations as the final best Gaussian fit." (Intensity map stacking)
   - parameter: 2 arcsec radius aperture; 500 noise perturbations  
  > "We repeat this noise perturbation procedure 500 times and take the median fit of those 500 iterations as the final best Gaussian fit." (Intensity map stacking)
   - fitting: Gaussian fit to the noise-perturbed spectrum; median of 500 fits taken as best fit (sampler/priors not stated)  
  > "We repeat this noise perturbation procedure 500 times and take the median fit of those 500 iterations as the final best Gaussian fit." (Intensity map stacking)
   - validation: example spectra and fits shown in appendix figure  
  > "We show examples of the extracted spectra and their fit in the appendix" (Intensity map stacking)
4. **Build moment-0 maps and stack them**: Make intensity maps over +/-FWHM of the best Gaussian with immoments, realign each map to its emission peak, and take the uniform (unweighted) mean; the stacked synthesised beam is computed the same way  
  > "We spatially realign each CO(2–1) intensity map to the peak of the emission before stacking each of them." (Intensity map stacking); "We computed the stacked synthesised beam in the exact same way." (Intensity map stacking)
   - software: CASA, immoments
   - parameter: uniform weights w_n=1; noise-weighted stack gave very similar results  
  > "The noise-weighted stack showed very similar results due to the homogeneity of the observations" (Intensity map stacking)
   - parameter: no position-angle alignment performed  
  > "here we note that we did not perform further morphological alignments" (Intensity map stacking)
   - fitting: _not stated_
   - validation: random-rotation restacking in the appendix to show orientation dependence of the 2D stack  
  > "we show uniformly-weighted stack intensity maps resulting from randomly rotating the individual intensity maps prior to stacking" (Intensity map stacking)
5. **Measure surface-brightness radial profiles of the stack**: Mean flux normalised by the peak in annuli of 4 pixels width (~0.4 arcsec) out to 4 arcsec; error is the standard deviation within each annulus; same for the stacked beam  
  > "we measure the mean flux normalised by the peak of the emission within annuli of increasing radius" (Surface brightness radial profiles); "and width of 4 pixels" (Surface brightness radial profiles); "The associated error is the standard deviation within each annulus." (Surface brightness radial profiles)
   - parameter: annulus width 4 pixels; profile out to 4 arcsec  
  > "and width of 4 pixels" (Surface brightness radial profiles)
   - fitting: _not stated_
   - validation: 500 resamplings each removing a random 30% of the sample; all iterations stay more extended than the beam  
  > "randomly removing 30% of the sample each time" (Surface brightness radial profiles)
6. **Deconvolve the beam and get intrinsic CO extent**: Fit Sersic profiles to the CO and beam radial profiles (Re, Ie, n free); since n~0.5 for both, subtract the beam half-light radius in quadrature from the CO one  
  > "to the observed CO(2–1) and synthesised beam radial profiles with" (Surface brightness radial profiles); "In other words, we subtract in quadrature" (Surface brightness radial profiles)
   - parameter: Re, Ie and Sersic index n free parameters  
  > "the Sérisc index, as free parameters" (Surface brightness radial profiles)
   - assumption: Gaussian (n~0.5) profiles so analytical 1D Gaussian deconvolution applies  
  > "we can apply an analytical 1D Gaussian deconvolution to the observed stacked CO(2–1) emission" (Surface brightness radial profiles)
   - assumption: Cosmology H0=70, Om=0.3, OL=0.7 for converting arcsec to kpc  
  > "The cosmology assumed throughout this work follows the" (Introduction)
   - fitting: Sersic profile fits to radial profiles; sampler, priors and likelihood not stated  
  > "to the observed CO(2–1) and synthesised beam radial profiles with" (Surface brightness radial profiles)
   - validation: _not stated_
7. **Repeat with cube stacking**: Align each cube in velocity to the Gaussian-fit peak and in position to the intensity-map peak, stack cubes (and beam cubes), then image moment 0 and compute radial profiles as before  
  > "We align each cube in the velocity space to the peak of the CO(2–1) emission, according to the best Gaussian fit" (CO cube stacking); "As an alternative to intensity map stacking, we explore cube stacking." (CO cube stacking)
   - fitting: _not stated_
   - validation: results consistent with intensity-map stacking  
  > "we observe consistent results between the two intensity maps" (CO cube stacking)
8. **Stack subsamples by galaxy properties**: Bin the sample by stellar mass, L_IR, sSFR (split at sample medians) and MS vs starburst (3.5 times above MS), stack radial profiles and spectra per bin  
  > "defined with respect to the median value of the sample for the property of interest" (Subsample intensity map stacks); "(following the definition set in" (Subsample intensity map stacks)
   - fitting: _not stated_
   - validation: profiles consistent within 1 sigma across bins  
  > "In all binned stacks, we do not observe a significant difference" (Subsample intensity map stacks)
9. **Stack Ks-band images and compare with CO**: Richardson-Lucy PSF deconvolution of each Ks image with a Moffat PSF, segmentation maps for source isolation and background subtraction, uniform stack, then compare radial profile with the intrinsic CO profile  
  > "perform a Richard-Lucy PSF deconvolution on each Ks band image using" (Comparison to the stellar component); "to create segmentation maps to isolate sources from the background sky" (Comparison to the stellar component); "We uniformly stack the realigned, PSF-deconvolved and background-subtracted images" (Comparison to the stellar component)
   - software: scikit-image, photutils
   - parameter: Moffat PSF FWHM = 0.78 arcsec, beta = 3.5  
  > "to compute a 2D PSF Moffat model with FWHM $=0.78\ensuremath{''}$ and $\beta=3.5$" (Comparison to the stellar component)
   - fitting: _not stated_
   - validation: 500 stack resamplings shown for the Ks profile; CO and Ks profiles follow each other closely  
  > "Within the respective noise level of the Ks band and CO stacked maps, we find that the two Ks band and CO radial profiles follow each other closely." (Comparison to the stellar component)
10. **Stack the CO(2-1) spectra**: Extract spectrum in a 2 arcsec aperture, fit a Gaussian, realign spectra to the fitted line centre, rebin to 60 km/s and uniformly stack  
  > "aperture centred on the cube" (Spectrum stacking); "We use the centre found in the best Gaussian fit to realign each spectrum to the peak of the CO(2–1) emission." (Spectrum stacking); "We rebin the spectra to 60" (Spectrum stacking)
   - parameter: 2 arcsec aperture; 60 km/s rebinned channels (30 km/s version in appendix)  
  > "We rebin the spectra to 60" (Spectrum stacking)
   - fitting: Gaussian fit per galaxy as in step 3  
  > "We use the centre found in the best Gaussian fit to realign each spectrum to the peak of the CO(2–1) emission." (Spectrum stacking)
   - validation: _not stated_
11. **Test for broad outflow wings**: Fit single- and two-Gaussian models to the stacked spectrum and compare reduced chi-squared; a significantly better two-Gaussian fit would indicate outflowing material  
  > "If the combination of a narrow component and a broad component (two-Gaussian fit) results in a fit with a significantly higher quality" (Spectrum stacking); "We compute the residuals and the corresponding reduced chi-squared" (Spectrum stacking)
   - fitting: single vs two-Gaussian fit compared by reduced chi-squared (fit routine, priors and bounds not stated)  
  > "We compute the residuals and the corresponding reduced chi-squared" (Spectrum stacking)
   - validation: 500 resamplings removing 30% of galaxies; also repeated with cube stacking and on subsamples  
  > "we repeat the uniform stacking of the spectra, 500 times, randomly removing 30% galaxies of the full sample at each iteration" (Spectrum stacking)

## Software

- **CASA** 6.5.5.21: data reduction (uvcontsub, tclean, immoments)  
  > "We use the Common Astronomy Software Applications (CASA 6.5.5.21) data processing software" (Observations and sample description)
- **uvcontsub** : uv-plane continuum subtraction (order 0 polynomial)  
  > "We subtract the continuum in the uv-plane with a polynomial of order 0" (Observations and sample description)
- **tclean** : imaging CO(2-1) cubes  
  > "We image the CO(2–1) emission with natural weighting and channel width" (Observations and sample description)
- **immoments** : creating intensity (moment 0) maps over the Gaussian FWHM range  
  > "of the best Gaussian fit, using" (Intensity map stacking)
- **scikit-image** : Richardson-Lucy PSF deconvolution of Ks images  
  > "perform a Richard-Lucy PSF deconvolution on each Ks band image using" (Comparison to the stellar component)
- **photutils** : segmentation maps to isolate sources from the sky background in Ks images  
  > "to create segmentation maps to isolate sources from the background sky" (Comparison to the stellar component)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Noise level of stacked CO(2-1) intensity map | 0.029 | not stated | Jy/beam km/s | 4 | The stacked intensity map has a noise level of 0.029 Jy/beam |
| Peak S/N of stacked intensity map | 27 | not stated | dimensionless | 4 | a CO(2–1) peak detection with $S/N=27$ |
| Observed CO(2-1) emission extent in stack (r_max) | ~1.9 arcsec (~16 kpc at z=1.3) | not stated | arcsec / kpc | 5 | $r_{max}\sim1.9\ensuremath{''}$ ($\sim16$ kpc at $z=1.3$) |
| Sersic index of CO radial profile (n_CO) | 0.50 | 0.03 | dimensionless | 6 | $n_{\text{CO}}=0.50\pm0.03$ |
| Observed half-light radius of stacked CO (R_e,CO) | 1.02 | 0.04 | arcsec | 6 | $R_{e,\text{CO}}=1.02\ensuremath{''} \pm 0.04\ensuremath{''}$ |
| Half-light radius of stacked synthesised beam (R_e,beam) | 0.84 | 0.04 | arcsec | 6 | $R_{e,\text{beam}}=0.84\ensuremath{''} \pm 0.04\ensuremath{''}$ |
| Beam-corrected CO half-light radius (R_e,CO_i) | 0.6 | 0.06 | arcsec | 6 | $R_{e,\text{CO}_i}=0.6\ensuremath{''} \pm 0.06$ |
| Intrinsic CO(2-1) half-light radius | 5 | not stated | kpc | 6 | with a half-light radius of $R_e=5$ kpc |
| Intrinsic CO(2-1) extent (R_CO) | ~12 | not stated | kpc | 6 | spatially extends to scales of $R_{\text{CO}}\sim12$ kpc |
| Ks-band (stellar) extent (R_Ks) | ~13 | not stated | kpc | 9 | ($R_{\text{Ks}}\sim13$ kpc) |
| Stacked spectrum peak flux | 1.36 | not stated | mJy | 10 | a peak flux of 1.36 mJy |
| Stacked spectrum noise level | 0.11 | not stated | mJy | 10 | and a noise level of 0.11 mJy |
| Stacked CO(2-1) line FWHM (spectrum stack) | 393 | 18 | km/s | 10 | a line width FWHM$=393\pm18$ km$^{-1}$ |
| Reduced chi-squared, single vs two-Gaussian fit of stacked spectrum | 0.832 (single) vs 0.830 (two-Gaussian) | not stated | dimensionless | 11 | $\tilde{\chi}^2=0.832$ and in the two-Gaussian fit, $\tilde{\chi}^2=0.830$ |
| Stacked CO(2-1) line FWHM (cube stack) | 399 | 19 | km/s | 10 | line width FWHM $=399 \pm 19$ km$^{-1}$ |
| CO(2-1) FWHM in MS bin | 478 | 27 | km/s | 8 | FWHM $= 478 \pm 27 \text{km\,s}^{-1}$ and FWHM$= 249 \pm 18 \text{km\,s}^{-1}$ |
| CO(2-1) FWHM in SB bin | 249 | 18 | km/s | 8 | FWHM $= 478 \pm 27 \text{km\,s}^{-1}$ and FWHM$= 249 \pm 18 \text{km\,s}^{-1}$ |

## Qualitative findings

- No broad wings in the stacked CO(2-1) spectrum, so no prominent ongoing molecular outflows  
  > "we do not observe the presence of prominent molecular outflows traced by broad wings" (Summary and outlook)
- Intrinsic CO extent is similar to the stellar (Ks) extent; no CO beyond the stellar emission  
  > "There is therefore no evidence of CO emission significantly more extended than the Ks band emission." (Comparison to the stellar component)
- Tentative blue excess in stacked spectra that may indicate outflows with optically thick redshifted gas  
  > "we note the presence of a tentative excess of CO(2–1) emission at negative velocities" (Discussion)

## Claim tuples

- H: Cold molecular gas of typical cosmic-noon MS SFGs extends to large (CGM-like, >~10 kpc) scales | E: Stack 26 ALMA CO(2-1) intensity maps, compute radial profiles, deconvolve the stacked beam by Sersic/Gaussian subtraction | R: Resolved emission out to ~1.9 arcsec (~16 kpc); beam-corrected extent ~1.4 arcsec (~12 kpc) | F: Marginally resolved CO emission exceeds 10 kpc in the stack | **partially**
- H: CO extends beyond the stellar component, as expected if outflows entrain gas to CGM scales | E: Compare stacked intrinsic CO(2-1) profile with the deconvolved stacked UltraVISTA Ks profile | R: Both profiles follow each other with similar extent (~13 kpc) | F: No evidence that CO is more extended than the stellar emission | **refuted**
- H: Ongoing molecular outflows appear as broad wings in the stacked CO(2-1) spectrum | E: Stack 26 spectra and compare single- and two-Gaussian fits (also cube stack, resamplings, subsamples) | R: No difference in fit quality (reduced chi-squared 0.832 vs 0.830) | F: No broad wings, so molecular outflows traced by CO(2-1) are weak in these galaxies | **refuted**
- H: A blue-shifted CO excess hints at outflows with optically thick redshifted side | E: Inspect residuals of stacked and binned spectra for negative-velocity excess | R: Weak asymmetry in nearly all stacks; 3 channels at SNR of 3 in high L_IR and high sSFR bins | F: Tentative evidence only | **partially**
- H: Radial extent depends on stellar mass, L_IR, sSFR or distance to the main sequence | E: Stack in bins split at the sample median (and MS vs SB) | R: Profiles consistent within 1 sigma in all bins | F: No galaxy property found to drive the profile | **refuted**

## Reasoning

- Why this data: CO(2-1) is a low-J tracer of the bulk molecular gas and the sample has homogeneous resolution  
  > "It provides CO(2–1) emission line observations, one of the lowest CO transitions observable at cosmic noon, allowing us to directly trace the bulk of the molecular gas." (Observations and sample description); "These observations are taken with a homogenous resolution" (Observations and sample description)
- Why this method: Stacking gains sensitivity to reveal faint broad wings and extended emission  
  > "We stack the individual CO(2–1) emission line spectra to gain sensitivity and reveal such potentially faint broad wings." (Spectrum stacking)
- Alternative: Noise-weighted stacking tested but gave very similar results, so uniform stacks only  
  > "The noise-weighted stack showed very similar results due to the homogeneity of the observations" (Intensity map stacking)
- Alternative: Jones et al. 2023 error method (Gaussian noise convolved with beam) tested but gave lower errors than the annulus standard deviation, so the latter was adopted  
  > "but we find that the standard deviation within the annulus gives higher error values" (Surface brightness radial profiles)
- Alternative: Cube stacking tried as an alternative to intensity-map stacking  
  > "As an alternative to intensity map stacking, we explore cube stacking." (CO cube stacking)
- How they decided it was enough: Resampling by removing 30% of the sample 500 times was used to check that a handful of galaxies do not drive the result  
  > "To test whether or not only a handful of galaxies drive the observed profiles" (Surface brightness radial profiles)
- Limitation (authors): No position-angle alignment of the galaxies before stacking  
  > "A caveat to our analysis to note is that we did not perform PA alignment." (Discussion)
- Limitation (authors): Stacked spectra may lack the S/N or depth to detect faint outflow wings  
  > "we cannot exclude that the S/N of our stacked spectra might prevent us from detecting an outflow signature" (Spectrum stacking)
- Limitation (authors): Analysis done in the image plane; a uv-plane analysis would be complementary  
  > "We have conducted our analysis in the image-plane." (Discussion)
- Caveat (inferred, ours): Extent is defined by where the profile meets an ad hoc noise level, and radial-profile errors (annulus standard deviation) ignore correlated noise, so the ~12 kpc number is soft
- Caveat (inferred, ours): Beam deconvolution relies on a Gaussian (n~0.5) assumption and a quadrature subtraction of two similar widths (1.02 vs 0.84 arcsec), which amplifies uncertainty
- Caveat (inferred, ours): Without PA/inclination alignment, a stacked 'extended' signal can come from orientation mixing; only partly addressed by random-rotation tests
- Caveat (inferred, ours): Sample requires S/N>=3 CO detections and so is biased to brighter CO emitters and possibly to compact or well-resolved sources
- Caveat (inferred, ours): Ks deconvolution by Richardson-Lucy with a single Moffat PSF may bias the stellar extent that CO is compared to
- Caveat (inferred, ours): Calibration, flux scaling and primary-beam correction are not described, so flux-based profiles cannot be checked

## Reproducibility

- Data public (paper): ALMA archival data (project 2016.1.00171.S) and public UltraVISTA Ks cutouts from IRSA  
  > "we stacked the ALMA archival CO(2–1) intensity maps of our sample" (Summary and outlook); "We specifically use the IRSA COSMOS cutout service" (Observations and sample description)
- Products in archive: _not stated_
- Missing: tclean imaging parameters (image size, cell, masks, threshold, primary-beam handling)
- Missing: Calibration route and pipeline version
- Missing: Line-free channel selection and spectral setup used for uvcontsub
- Missing: Fit initial guesses/bounds for single and two-Gaussian models and Sersic fits
- Missing: Ks cutout size and Richardson-Lucy settings
- Data volume (inferred): Roughly several to tens of GB of raw Band 3 data for 26-33 short (about 270-730 s) executions; working CO cubes are small
- Score (inferred): 3/5, Public ALMA project and numeric results with a clear stacking recipe, but imaging, calibration and fit settings are not given and no code is released
- Rediscovery candidate: yes, Data are public, the stacking and radial-profile recipe is mostly stated, and the main results (extent in kpc, Sersic parameters, line FWHM, chi-squared) are numeric

## Links

- Method: Valentino et al. 2020 (cite: Valentino2020) (Full report of the ALMA observations and sample properties)
- Method: McCracken et al. 2012 (cite: McCracken2012) (UltraVISTA Ks data and PSF information)
- Method: Jones et al. 2023 (cite: Jones2023) (Stacking/radial-profile method and error test followed or compared)
- Companion: Barfety et al. 2025 (cite: Barfety2025) (CO spectral stacking of typical SFGs, similar no-outflow result)
- Companion: Puglisi et al. 2019 (cite: Puglisi2019) (ALMA vs Ks sizes for MS SFGs, consistent with this work)
- Companion: Rybak et al. 2024 (cite: Rybak2024) (uv-plane stacking of CO(1-0) for comparison)
- Related: ALMA 2016.1.00171.S (PI E. Daddi)
- Related: COSMOS
- Related: UltraVISTA (ESO programme 179.A-2005)

## Checks

```json
{
 "quotes": 126,
 "quotes_ok": 126,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 109,
  "stated": 75,
  "rate": 0.688
 },
 "evidence_ok": true
}
```
