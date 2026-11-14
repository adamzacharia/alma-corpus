# exoALMA. VIII. Probabilistic Moment Maps and Data Products Using Nonparametric Linear Models

`2025ApJ...984L..13H` | The Astrophysical Journal Letters 2025 | first author: Hilder, Thomas | arXiv: 2504.19416 | DOI: 10.3847/2041-8213/adc435

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: Can a non-parametric linear model of per-channel intensity, with beam-correlated noise, give probabilistic moment maps and disk-fit uncertainties that are debiased from beam smearing?  
  > "Our method debiases peak intensity, peak velocity, and line width maps, particularly in disk substructures that are only partially resolved." (abstract); "We find that uncertainties in stellar mass and inclination increase by an order of magnitude due to the more realistic noise model." (abstract)
- Target **HD 135344B**: coordinates _not stated_; z/distance 135 pc (used in the benchmark model built to resemble HD 135344B)  
  > "and a distance of $135 \, {\rm pc}$ (cite: gaiacollaboration2023)" (Synthetic data and fit); "These sources were chosen due to their low inclination" (Data); distance from Gaia Collaboration 2023 (gaiacollaboration2023)  
  > "and a distance of $135 \, {\rm pc}$ (cite: gaiacollaboration2023)" (Synthetic data and fit); "These sources were chosen due to their low inclination" (Data)
- Target **MWC 758**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **CQ Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1842**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01123.L
- bands: _not stated_
- frequencies and spectral setup: 12CO J=3-2 fiducial exoALMA cubes; channel spacing 100 m/s; native spectral resolution 26 m/s  
  > "These have a circular synthesised beam with a full width half maximum (FWHM) of $0.15\ensuremath{''}$, and a channel spacing of $100 \, {\rm ms^{-1}}$." (Data); "comparable to or better than the native spectral resolution of 26 $\rm{m s^{-1}}$" (Moment maps)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: circular synthesised beam, FWHM 0.15 arcsec  
  > "These have a circular synthesised beam with a full width half maximum (FWHM) of $0.15\ensuremath{''}$, and a channel spacing of $100 \, {\rm ms^{-1}}$." (Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Other facility **Gaia**: distance of 135 pc used in the synthetic benchmark model  
  > "and a distance of $135 \, {\rm pc}$ (cite: gaiacollaboration2023)" (Synthetic data and fit)
- External data: Fiducial exoALMA 12CO J=3-2 cubes for HD 135344B, MWC 758, CQ Tau and J1842  
  > "We perform all analysis using the fiducial $^{12}$CO $J=3-2$ cubes (cite: Teague_exoALMA) for HD 135344B, MWC 758, CQ Tau and J1842." (Data) [from (cite: Teague_exoALMA)]
- External data: Stellar mass, inclination and position angle for the HD 135344B-like benchmark model (M = 1.61 Msun, i = 16.11 deg, PA = 242.94 deg)  
  > "For the model we use central mass $M_\star = 1.61 \, {\rm M_\odot}$, inclination $i = 16.11^\circ$ and position angle ${\rm PA} = 242.94^\circ$ (cite: Izquierdo_exoALMA)" (Synthetic data and fit) [from (cite: Izquierdo_exoALMA)]
- External data: Production DISCMINER fit for J1842 used across the other exoALMA papers, compared with the new fits  
  > "The production DISCMINER fit for J1842 used across the other exoALMA papers (cite: Teague_exoALMA; Izquierdo_exoALMA) used downsampling of $6\times6$ pixel blocks" (Discminer case study) [from (cite: Teague_exoALMA; Izquierdo_exoALMA)]
- Simulation/model as data: Synthetic benchmark cube: Gaussian line in each pixel with hand-chosen radial intensity, velocity (Keplerian with 3 Gaussian ring perturbations) and line-width profiles resembling HD 135344B, convolved with the 0.15 arcsec beam plus beam-correlated noise  
  > "For the benchmark model, we assume the line in each pixel is Gaussian, and choose radial intensity, velocity, and line width profiles, as well as other model parameters to create similar looking synthetic data to HD 135344B." (Synthetic data and fit); "with 3 Gaussian ring perturbations placed at different radii" (Benchmark model)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: cubes downsampled by a factor of 2 per spatial axis (2x2 block mean) and cropped to the signal region  
  > "We downsample each cube by a factor of 2 in each spatial axis, replacing $2 \times 2$ blocks of pixels with their mean value." (Data); "The cubes are also cropped spatially to include only the region where the signal is contained." (Data)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: circular, FWHM 0.15 arcsec (CLEAN beam taken as Gaussian)  
  > "These have a circular synthesised beam with a full width half maximum (FWHM) of $0.15\ensuremath{''}$, and a channel spacing of $100 \, {\rm ms^{-1}}$." (Data); "We assumed that the beam is Gaussian." (Caveats)
- final rms: _not stated_

### Inherited from earlier work

- Imaging/calibration of the fiducial exoALMA 12CO cubes  
  > "We perform all analysis using the fiducial $^{12}$CO $J=3-2$ cubes (cite: Teague_exoALMA) for HD 135344B, MWC 758, CQ Tau and J1842." (Data) [from (cite: Teague_exoALMA)]
- Fourier basis length scale L = 3 and weighting function w  
  > "and set $L=3$ following (cite: hoggvillar)." (Non-parametric model); "we choose (cite: hoggvillar)" (Non-parametric model) [from (cite: hoggvillar)]
- DISCMINER model and its use in exoALMA  
  > "We also combine our approach with DISCMINER (cite: izquierdo2021; izquierdo2022; izquierdo2023)" (Introduction) [from (cite: izquierdo2021; izquierdo2022; izquierdo2023)]
- Numerical solver design (avoid explicit matrix inverses)  
  > "following the advice of (cite: hoggvillar), we avoid directly calculating the inverse of matrices" (Numerical considerations) [from (cite: hoggvillar)]

### Not stated but needed to reproduce (our reading)

- DISCMINER setup for the J1842 fits: priors, walker/step counts, burn-in, emitting-layer parametrisation, initial values, number of channels and velocity range used
- The exact crop region and pixel size of each cube after downsampling, and which channels were deemed signal-free for the noise sigma
- The sigma value used for each real cube (only the synthetic benchmark sigma of 20 mJy is given)
- How imaging of the fiducial exoALMA cubes was done (robust, tclean settings, continuum subtraction); deferred entirely to Teague et al.
- Which cubes (e.g. native resolution vs. smoothed) are the 'fiducial' ones and where to obtain them; ALMA band and rest frequency of 12CO are not stated
- Numerical values of the benchmark radial profile parameters are only in an appendix equation set; the random-noise seed is not given
- Code or repository for the non-parametric model is not named

## Analysis recipe

1. **Prepare cubes**: Downsample each cube by 2 in each spatial axis (2x2 mean) and crop to the signal region  
  > "We downsample each cube by a factor of 2 in each spatial axis, replacing $2 \times 2$ blocks of pixels with their mean value." (Data); "The cubes are also cropped spatially to include only the region where the signal is contained." (Data)
   - parameter: downsampling factor 2 per spatial axis  
  > "We downsample each cube by a factor of 2 in each spatial axis" (Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit the non-parametric linear model per channel and draw posterior cube samples**: Each channel is modelled independently as a Fourier-series intensity map convolved with the beam, with beam-correlated Gaussian noise and a smoothness-promoting Gaussian prior; the posterior mean and covariance are analytic; 100 posterior cube samples are drawn  
  > "has an analytic form thanks to the linearity of the model, and because both the noise and prior are normal distributions" (Non-parametric model); "yielding 100 model cube samples, both before and after beam convolution." (Fitting and sampling)
   - software: NumPy, SciPy
   - parameter: hyperparameters lambda = s = 0.1  
  > "We somewhat arbitrarily choose values for the hyperparameters of $\lambda=s=0.1$, since we found them to be performant in terms of predicting the data" (Non-parametric model)
   - parameter: number of basis functions per axis = 1.25 x pixels per axis (over-parameterised)  
  > "We set the number of basis functions in each direction $p_x, p_y$ to be 1.25 times the number of pixels in each direction $n_x, n_y$, rounded to the nearest integer." (Non-parametric model)
   - parameter: same noise sigma for all pixels, from the standard deviation in channels with no significant signal  
  > "we assume the same $\sigma$ for all pixels in the cube, which we estimate from the standard deviation of the data in channels with no significant signal." (Non-parametric model)
   - parameter: L = 3, pixel coordinates uniformly spaced between 0 and 1  
  > "We choose spatial coordinates $x_i,y_i$ for the pixels uniformly spaced between 0 and 1, and set $L=3$ following (cite: hoggvillar)." (Non-parametric model)
   - parameter: numpy lstsq with RCOND = 1e-16 instead of explicit inverses  
  > "with RCOND set to $10^{-16}$ to zero out small eigenvalues near machine precision" (Numerical considerations)
   - assumption: Gaussian beam kernel (circular, FWHM 0.15 arcsec) and noise correlated on the scale of the beam; uv sampling not modelled  
  > "Let $h(x,y)$ be a function representing the kernel of the beam, a circular 2D gaussian" (Non-parametric model); "We assume that the noise is spatially correlated on the scale of the beam" (Non-parametric model)
   - fitting: Analytic Gaussian posterior (generalised least squares with Gaussian prior, mean zero, feature-weighted variances); samples drawn via Cholesky or spectral decomposition of the covariance  
  > "We choose a prior that penalises high frequency basis functions more than low frequency ones, in order to encourage smoothness." (Non-parametric model); "If $\boldsymbol{\Sigma}$ is positive definite then we use a Cholesky decomposition" (Numerical considerations)
   - validation: Benchmark on synthetic data; hyperparameter sensitivity of uncertainties checked in an appendix  
  > "To assess this, we calculated $\Sigma$ for a large range of possible $\lambda$ values for the fit to the HD 135344B data." (Impact of hyperparameter selection)
3. **Make probabilistic moment maps (new method) and conventional maps**: Fit a Gaussian line profile (peak intensity, centroid velocity, width) to each pixel of each unconvolved cube sample by maximum likelihood; take the median over 100 samples as best value and the standard deviation as 1 sigma; compare with the same fit applied directly to the data (conventional method)  
  > "We fit Gaussian line profiles to each pixel of each sample cube" (Probabilistic moment maps); "is taken as the median across the 100 cube samples, while the $1\sigma$ uncertainty is estimated from the standard deviation." (Probabilistic moment maps); "We also fit Gaussian line profiles to the data directly, as is typically done in studies of kinematics or other disk properties, for comparison." (Probabilistic moment maps)
   - software: SciPy
   - parameter: L-BFGS-B minimisation of negative log likelihood via scipy.optimize.minimize  
  > "implemented in SciPy’s `optimize.minimize` function (cite: virtanen2020) to fit." (Probabilistic moment maps)
   - parameter: noise cut-off of three times the cube RMS  
  > "A noise cut-off of three times the cube RMS was applied to avoid fitting lines with low signal-to-noise." (Probabilistic moment maps)
   - assumption: Single-peaked Gaussian line profile, normally distributed noise  
  > "allowing us to treat the line profile as single-peaked due to their lack of backside contamination" (Data); "and we assume the noise $\sigma$ is normally distributed." (Probabilistic moment maps)
   - fitting: Per-pixel maximum likelihood estimation with Gaussian likelihood  
  > "We use maximal likelihood estimation to perform the fit" (Probabilistic moment maps)
   - validation: Compared with the known truth in the synthetic benchmark; recovered spirals compared with known spirals in the sources  
  > "These disks are all known to contain spirals" (Moment maps)
4. **Benchmark on synthetic HD 135344B-like data**: Build a synthetic cube from radial intensity, line-width and velocity profiles, convolve with the 0.15 arcsec beam, add beam-correlated noise, fit with the non-parametric model, make moment maps by both methods and compare with the true maps  
  > "We then convolved the channels spatially with a circular Gaussian beam with FWHM $=0\ensuremath{''}{15}$ to match the data" (Synthetic data and fit); "and added beam-correlated noise with scale $\sigma = 20 \, {\rm mJy}$." (Synthetic data and fit)
   - software: NumPy, SciPy
   - parameter: channel increments 100 m/s; noise scale 20 mJy  
  > "with $v_{\rm ch}$ in increments of $100 \, {\rm ms^{-1}}$" (Synthetic data and fit)
   - assumption: M = 1.61 Msun, i = 16.11 deg, PA = 242.94 deg, distance 135 pc  
  > "For the model we use central mass $M_\star = 1.61 \, {\rm M_\odot}$, inclination $i = 16.11^\circ$ and position angle ${\rm PA} = 242.94^\circ$ (cite: Izquierdo_exoALMA), and a distance of $135 \, {\rm pc}$ (cite: gaiacollaboration2023)." (Synthetic data and fit)
   - fitting: _not stated_
   - validation: Residuals between model and truth are mostly noise except within the central few beams; conventional maps are biased, new maps are not  
  > "This indicates that the model effectively provides an unbiased estimate of the intensity, except within the central few beams." (Synthetic data and fit)
5. **Combine cube samples with DISCMINER for J1842**: Draw 30 beam-convolved cube samples, fit each with DISCMINER, then aggregate all DISCMINER posterior samples into a combined posterior; compare with DISCMINER on the data directly and with the production exoALMA fit  
  > "We fit each cube sample with DISCMINER, obtaining many posterior distributions, where each is conditioned on a single cube sample." (Discminer case study); "Finally, we estimate the combined posterior by aggregating the posterior DISCMINER samples from all fits." (Discminer case study)
   - software: DISCMINER
   - parameter: 30 cube samples (convolved); data downsampled 2x2 for the re-fit versus 6x6 in the production fit  
  > "30 such samples were used with DISCMINER for the combined approach outlined in Section" (Discminer); "used downsampling of $6\times6$ pixel blocks, whereas we used $2\times2$." (Discminer case study)
   - assumption: DISCMINER assumes Keplerian rotation; uncertainty is purely statistical  
  > "This uncertainty is purely statistical however, and if the data are more complicated than assumed in the model, there will be systematic uncertainty that is unaccounted for." (Discussion)
   - fitting: DISCMINER Bayesian inference with MCMC sampling; sampler settings and priors not stated  
  > "DISCMINER uses Bayesian inference to estimate the posterior distribution of the disk model, allowing for quantification of the model uncertainties." (Discminer case study)
   - validation: Posterior medians compared between data and combined fits; estimates stable at about 10-20 cube samples  
  > "However, we verified that the estimates of the medians and quantiles become stable at around 10–20 cube samples." (Discminer)

## Software

- **DISCMINER** : forward-model Bayesian fit of disk properties (stellar mass, inclination, position angle, surface height and intensity profiles) to cube samples of J1842  
  > "DISCMINER is a statistical inference tool for protoplanetary disk properties that uses a forward model of line emission" (Discminer case study)
- **SciPy** : scipy.optimize.minimize (L-BFGS-B) for the per-pixel Gaussian line fits  
  > "implemented in SciPy’s `optimize.minimize` function (cite: virtanen2020) to fit." (Probabilistic moment maps)
- **NumPy** : linalg.lstsq for solving the linear systems in the fit  
  > "We instead solve for products of the inverse using numerical least squares with NUMPY’s" (Numerical considerations)
- **Astropy** : _not stated_
- **matplotlib** : _not stated_
- **cmasher** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity perturbation underestimated by conventional method (benchmark) | 50-200 | not stated | m/s | 4 | resulting in the underestimation of the velocity perturbations of 50–200 |
| Peak intensity underestimated by conventional method (benchmark) | around 10 | not stated | percent | 4 | although only by around 10% |
| Line width overestimated by conventional method (benchmark) | around 25 | not stated | percent | 4 | the bias is greater, around 25% |
| HD 135344B velocity perturbation along spiral, new minus conventional | 50-100 | not stated | m/s | 3 | finding velocity perturbations along the spiral 50–100 |
| CQ Tau velocity perturbation along one-armed spiral, new minus conventional | 50-150 | not stated | m/s | 3 | with a difference along the large one-armed spiral in the top-left of 50–150 |
| MWC 758 velocity perturbation associated with spiral, new minus conventional | 50-150 | not stated | m/s | 3 | in the 50–150 |
| HD 135344B v0 1 sigma uncertainty across most of the disk | 5-10 | not stated | m/s | 3 | with an uncertainty of 5–10 |
| CQ Tau and MWC 758 v0 uncertainty | 10-30 | not stated | m/s | 3 | Both CQ Tau and MWC 758 have uncertainties in the range 10–30 |
| Increase in DISCMINER parameter uncertainties with correlated-noise model (J1842) | approximately an order of magnitude (a factor of a few for v_LSRK) | not stated | dimensionless | 5 | We find that for all the parameters, the uncertainties are increased by approximately an order of magnitude.; where the increase is only a factor of a few |
| Precision of M_star and i after combined fit | within approximately 1 | not stated | percent | 5 | are still constrained to within approximately 1% |
| Offset in M_star and i of production DISCMINER fit (extra downsampling) | order of one percent | not stated | percent | 5 | While this bias is only on the order of one percent |
| Number of cube samples for stable medians and quantiles | 10-20 | not stated | cube samples | 5 | become stable at around 10–20 cube samples |
| Increase in uncertainty from weakening regularisation by 4 orders of magnitude (HD 135344B) | around 30 | not stated | percent | 2 | only increases the uncertainty by a factor of around 30% |

## Qualitative findings

- The new method finds greater peak intensities, reduced line widths and greater velocity perturbation amplitudes than the conventional method in all three sources  
  > "the new method finds greater peak intensities and reduced line widths throughout the disk in each case" (Moment maps)
- Posterior medians of DISCMINER parameters are not significantly different between data and combined approach, so the non-parametric model does not bias them  
  > "The posterior medians are not different between the data and combined approach to a statistically significant level" (Discminer)

## Claim tuples

- H: Does the non-parametric model remove beam-smearing bias in moment maps? | E: Synthetic HD 135344B-like cube, moment maps by new and conventional methods compared with truth | R: Conventional method underestimates velocity perturbations by 50-200 m/s, peak intensity by about 10 percent and overestimates line width by about 25 percent; new method is unbiased apart from the inner few beams | F: The new method debiases velocity, intensity and width maps except within the central few beams | **supported**
- H: Do real exoALMA disks show larger velocity substructures than conventional maps indicate? | E: Probabilistic moment maps for HD 135344B, CQ Tau and MWC 758 | R: Velocity perturbations along spirals are 50-150 m/s larger with the new method | F: Conventional maps underestimate localised perturbations due to beam smearing | **supported**
- H: How much does accounting for spatially correlated noise change DISCMINER uncertainties? | E: Fit DISCMINER to 30 beam-convolved cube samples of J1842 and aggregate posteriors | R: Parameter uncertainties increase by about an order of magnitude with unbiased medians | F: Uncertainties on DISCMINER parameters are underestimated by the simplified noise model, but M_star and i remain constrained to about 1 percent | **supported**
- H: Is the fixed choice of hyperparameters adequate? | E: Vary lambda for HD 135344B and compute marginal model uncertainties | R: Uncertainty of the unconvolved model decreases roughly linearly with log lambda; a 4-order decrease in regularisation raises uncertainty only about 30 percent | F: Moment-map uncertainties are likely only mildly underestimated by the chosen regularisation | **partially**

## Reasoning

- Why this data: HD 135344B, MWC 758 and CQ Tau chosen for low inclination (single-peaked profiles) and large spirals; J1842 chosen as a typical source  
  > "These sources were chosen due to their low inclination, allowing us to treat the line profile as single-peaked due to their lack of backside contamination" (Data); "was chosen as a representative typical source from the sample" (Data)
- Why this method: Linearity makes the posterior analytic so that sampling is tractable with of order 1e4 parameters  
  > "is crucial for allowing for tractable sampling from the model posterior distribution" (Non-parametric model)
- Alternative: Cross-validation for hyperparameters judged unreliable because the CV metric compares data to the convolved model, which barely changes with the hyperparameters  
  > "this avenue does not provide a reliable way to ensure that the model prior to convolution is performant." (Impact of hyperparameter selection)
- How they decided it was enough: 10-20 cube samples were enough for stable DISCMINER medians and quantiles  
  > "we verified that the estimates of the medians and quantiles become stable at around 10–20 cube samples" (Discminer)
- Limitation (authors): Model fits CLEAN images, not visibilities, and ignores uv sampling  
  > "As already touched on, our model fits to the CLEAN image and not the raw visibilities." (Caveats)
- Limitation (authors): Hyperparameters were fixed arbitrarily, not fitted  
  > "We somewhat arbitrarily choose values for the hyperparameters of" (Non-parametric model)
- Limitation (authors): Computationally prohibitive for more than about 100 x 100 pixels  
  > "This makes it prohibitive to use more pixels than around $100 \times 100$." (Caveats)
- Limitation (authors): Boundary artefacts in the outermost couple of pixels; performance at low signal-to-noise untested  
  > "The unconvolved model channels show boundary artefacts in the outermost couple of pixels." (Caveats); "although we did not test this" (Discussion)
- Caveat (inferred, ours): Benchmark uses image-plane convolution with idealised Gaussian beam and noise, so sidelobes and uv sampling are not tested
- Caveat (inferred, ours): Only one synthetic case; the debiasing is shown only for Gaussian line profiles and low-inclination disks
- Caveat (inferred, ours): Results depend on arbitrary fixed lambda = s = 0.1 and a 2x downsampling choice
- Caveat (inferred, ours): Only 30 DISCMINER cube samples; posterior shapes are unreliable
- Caveat (inferred, ours): No comparison with RML or visibility-plane forward modelling for the same data

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Cube samples and probabilistic moment maps to be made publicly available  
  > "The following data products will be publicly available" (Conclusions)
- Missing: Code for the non-parametric model (not named or linked)
- Missing: DISCMINER run configuration and priors for J1842
- Missing: Exact crop and signal-free channel selection for each cube and measured noise sigma
- Missing: Access details and imaging parameters of the fiducial exoALMA cubes (deferred to Teague et al.)
- Data volume (inferred): Fiducial exoALMA 12CO cubes for four sources, likely a few GB each before downsampling; the fits need very large memory and about a few days on a 64-core node for the DISCMINER study
- Score (inferred): 3/5, The model equations, hyperparameters and moment-map procedure are fully given and exoALMA cubes are a public-release program product, but no code is released, DISCMINER settings and cube preparation details are missing, and results are mostly ranges rather than tabulated numbers.
- Rediscovery candidate: no, Data accessibility is not stated by the paper and key implementation details are missing; the main results are given as ranges and qualitative comparisons.

## Links

- Method: Hogg & Villar 2021 (hoggvillar) (Source of the Fourier-basis Gaussian process regression setup, weighting function and numerical advice)
- Method: Izquierdo et al. 2021 (izquierdo2021) (DISCMINER method used in the case study)
- Companion: Teague et al. 2024 (Teague_exoALMA) (Describes the exoALMA program and the fiducial cubes used)
- Companion: Izquierdo et al. 2024 (Izquierdo_exoALMA) (Provides the DISCMINER production fits and disk parameters used in the benchmark)
- Related: exoALMA large program (2021.1.01123.L)

## Checks

```json
{
 "quotes": 99,
 "quotes_ok": 99,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 56,
  "rate": 0.544
 },
 "evidence_ok": true
}
```
