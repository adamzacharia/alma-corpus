# Detection of Lensing Substructure Using ALMA Observations of the Dusty Galaxy SDP.81

`2016ApJ...823...37H` | The Astrophysical Journal 2016 | first author: Hezaveh, Yashar D. | arXiv: 1601.01388 | DOI: 10.3847/0004-637X/823/1/37

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, other
- Question: How abundant is dark matter substructure near the lens galaxy of SDP.81, measured by fitting ALMA visibilities, and is it consistent with LCDM?  
  > "We study the abundance of substructure in the matter density near galaxies using ALMA Science Verification observations of the strong lensing system SDP.81." (abstract)
- Target **SDP.81**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: Bands 6 and 7, continuum only  
  > "We used only the calibrated continuum data from bands 6 and 7." (5 Results for SDP.81)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA long-baseline campaign observations  
  > "For ALMA long-baseline campaign observations of SDP.81 (cite: Fomalont:15), visibilities were typically recorded every 0.5 seconds" (4 implementation, simulations, and tests)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA Science Verification data  
  > "We use the recent ALMA Science Verification observations of the strongly lensed system SDP.81 (cite: SDP81)" (5 Results for SDP.81)
- Other facility **HST**: Image of the lensing galaxy shown against the ALMA arcs  
  > "Figure [4](#fig:SDP81ALMAHST) shows the lensing galaxy observed by the *Hubble Space Telescope* (greyscale) superimposed on the lensed arcs observed by ALMA." (5 Results for SDP.81)
- Other facility **SDSS**: Lens galaxy r-band magnitude and environment (RedMaPPer cluster membership)  
  > "which is $M_r = -21.88 \pm 0.015$ using the SDSS DR10 magnitudes" (6 Comparison to LCDM Predictions)
- External data: RedMaPPer cluster catalog membership and mass-richness relation for the SDP.81 environment  
  > "Assuming the mass–richness relationship of (cite: Rykoff:14), this corresponds to a mass of $\sim 2.6\times 10^{14} M_{\odot}$." (6 Comparison to LCDM Predictions) [from (cite: Rykoff:14)]
- External data: AGES luminosity function used for abundance matching  
  > "we assume the AGES luminosity function (cite: Kochanek:12)" (6 Comparison to LCDM Predictions) [from (cite: Kochanek:12)]
- Simulation/model as data: Mock ALMA observations of lensed clumpy sources made with an independent code and CASA, used to test the pipeline  
  > "the lensed images were used to simulate ALMA observations using the Common Astronomy Software Applications package (CASA)." (4.1 Mock observations)
- Simulation/model as data: Dark Sky Simulation ds14_i and zoom-in simulations used to calibrate the subhalo mass function  
  > "($4096^3$ particles in a $400~\text{Mpc}/h$ box, `ds14_i`) from the Dark Sky Simulations (cite: Skillman:14)" (6 Comparison to LCDM Predictions)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used the calibrated continuum data provided  
  > "We used only the calibrated continuum data from bands 6 and 7." (5 Results for SDP.81)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Subhalo modeled as a pseudo-Jaffe profile, following the earlier proposal for ALMA substructure detection  
  > "We follow (cite: Hezaveh13A) and model the subhalo deflection field using a truncated isothermal surface density profile" (5.1 Initial subhalo search) [from (cite: Hezaveh13A)]
- Pixelated source framework and Bayesian evidence normalization of source prior  
  > "The general framework of fitting strongly lensed images with pixelated sources is described in detail in (cite: warren:03) and (cite: suyu:06)." (2 Framework) [from (cite: warren:03); (cite: suyu:06)]
- Subhalo mass function model and calibration methodology  
  > "we follow the methodology presented in (cite: Mao:15)" (6 Comparison to LCDM Predictions) [from (cite: Mao:15)]
- MCMC sampler of Goodman and Weare, implemented following emcee  
  > "we have implemented the Markov chain Monte Carlo (MCMC) algorithm proposed by (cite: mcmchammer). We follow the procedure described in (cite: emcee)." (4.1 Mock observations) [from (cite: mcmchammer); (cite: emcee)]

### Not stated but needed to reproduce (our reading)

- Source pixel grid size and extent for the actual fits (only 10 mas pixels for reconstruction shown)
- Exact source prior form used for SDP.81 (gradient, curvature or clump power spectrum) and its parameters
- MCMC settings: number of walkers, steps, burn-in, convergence criteria
- Priors on antenna phase errors and time segmentation details
- Which SV execution blocks and spectral windows were used for continuum
- Phase center and target coordinates and redshifts
- Subhalo mass grid and sampling for linearized maps
- Code availability: pipeline not released

## Analysis recipe

1. **Bin visibilities and estimate noise**: Bin visibilities sharing a baseline within a short time into uv cells; estimate noise from differences of visibilities that null the sky, scaling Tsys  
  > "We estimate the noise variance for each visibility using the procedure described above and bin the visibilities in 12 meter cells." (5 Results for SDP.81)
   - software: Elemental
   - parameter: 12 m cells; bins within ≲20 min on the same baseline; ~0.5 million binned visibilities from ~10 million  
  > "This results in $\sim0.5$ million binned visibilities, a factor of $\sim 20$ fewer than the original $\sim10$ million." (5 Results for SDP.81)
   - parameter: Retain binned visibilities with noise below 5.0 mJy (band 6) and 5.5 mJy (band 7)  
  > "We, therefore, decide to model binned visibilities with noise lower than 5.0 and 5.5 mJy in bands 6 and 7 respectively" (5 Results for SDP.81)
   - assumption: Noise rms proportional to Tsys; variance of differenced visibilities equals twice noise variance  
  > "we can simply assume that the variance in the subtracted visibilities is equal to twice the noise variance" (4 implementation, simulations, and tests)
   - fitting: _not stated_
   - validation: Both noise methods give consistent results  
  > "We try both methods and find that they provide consistent results." (4 implementation, simulations, and tests)
2. **Fit smooth lens model to visibilities**: Fit visibilities with a pixelated source, analytic marginalization over source pixels, antenna phase errors per baseline and time, and MCMC over lens parameters; initial localization with baselines <2 km  
  > "We first use only the subset of baselines shorter than 2 km in our initial MCMC analysis to localize the neighborhood of the best fit." (5 Results for SDP.81)
   - software: emcee-style MCMC, Elemental, MPI
   - parameter: Singular elliptical power law plus m=3,4 multipoles plus external shear; 12 free parameters  
  > "Overall, therefore, our primary lens model contains 12 freely adjustable parameters." (5 Results for SDP.81)
   - assumption: Flat LCDM with Omega_M = 0.267, H0 = 71  
  > "we assume a flat $\Lambda$CDM expansion history with mean matter density $\Omega_M = 0.267$ and current expansion rate $H_0 = 71$ km Mpc$^{-1}$ s$^{-1}$." (1 Introduction)
   - assumption: No prior on lens parameters (C_eta^-1 = 0)  
  > "we set ${\bf C}_\eta^{-1} = 0$, i.e., we assume no prior on the lens model parameters." (2 Framework)
   - fitting: Gaussian likelihood with Gaussian source prior; MCMC after Goodman and Weare, following emcee  
  > "We follow the procedure described in (cite: emcee)." (4.1 Mock observations)
   - validation: Tested on mock ALMA data; parameters recovered without bias with gradient and curvature priors  
  > "in both cases we successfully manage to recover the parameters with no apparent biases." (4.1 Mock observations)
3. **Linearized subhalo search**: Map Delta E, twice the marginalized log-posterior difference, over subhalo position and mass using a linear approximation about the smooth model, marginalizing over lens, source and phase parameters  
  > "We search for subhalos over a range of subhalo masses, over a $8\times8$ arcsec area around the lens center." (Initial subhalo search)
   - parameter: Pseudo-Jaffe subhalo with r_t = (sigma_v/(sqrt2 sigma_G)) r_E; initial search at M=10^8.6 Msun  
  > "we assume that $r_t$ is related to $\sigma_v$ by $r_t = (\sigma_v/\sqrt{2}\sigma_G)r_{\rm E}$" (5.1 Initial subhalo search)
   - fitting: _not stated_
   - validation: Bands 6 and 7 analyzed separately give a consistent pattern; alternative literature lens models give similar results  
  > "Our analysis reveals a consistent pattern between the two bands (see Figure [5](#initial_search))" (5.1 Initial subhalo search)
4. **Nonlinear fit with subhalo and MCMC**: Add a subhalo with 3 parameters (mass, 2-D position), refit jointly in bands 6 and 7 fully nonlinearly, then sample with MCMC  
  > "we then expanded our lens model to include a subhalo, with 3 adjustable parameters: mass $M_{\rm sub}$, and 2-D location $\bm{x}_{\rm sub}$." (5.1 Initial subhalo search)
   - software: emcee-style MCMC
   - fitting: MCMC over smooth lens and subhalo parameters; 68% uncertainties  
  > "Best-fit lens parameters with 68% uncertainties" (Table 1)
   - validation: No significant degeneracy between subhalo and smooth lens parameters including multipoles  
  > "We do not find evidence for significant degeneracies between the subhalo parameters and the parameters of the smooth lens model" (5.1 Initial subhalo search)
5. **Search for additional substructure**: Repeat the linearized search about the model including the detected subhalo; nonlinear fit of a second subhalo  
  > "We repeated our search for a second subhalo, by linearly expanding about a smooth model now containing a subhalo of mass $M_{\rm sub}=10^{8.96} M_{\odot}$." (5.2 Search for additional substructure)
   - fitting: _not stated_
   - validation: Second object marginal (<5 sigma) and possibly a modeling artifact, so not claimed as detection  
  > "First, the detection is marginal $(<5\sigma)$." (5.2 Search for additional substructure)
6. **Constrain subhalo mass function**: Combine Poisson likelihood from detected subhalos with exclusion areas from Delta E maps, assuming linear addition of Delta E; fit dn/dlogM = A (M/Mpivot)^-eta  
  > "We describe the mass function using a simple parametrization, $dn/d\log M = A\,(M/M_{\rm pivot})^{-\eta}$" (5.3 Bounds on the subhalo mass function)
   - assumption: Poisson process with spatially uniform mean projected density; subhalo effects add linearly  
  > "We assume that the incidence of subhalos is a Poisson process with mean projected number density $n(M)$ that is spatially uniform" (5.3 Bounds on the subhalo mass function)
   - fitting: _not stated_
   - validation: Linear addition tends to underestimate decrease in posterior for overlapping subhalos, so bounds slightly conservative  
  > "suggesting that our bounds below are (slightly) conservative." (5.3 Bounds on the subhalo mass function)
7. **Compare with LCDM predictions**: Predict projected subhalo mass function from calibrated M0(Mhost, chost) relation with NFW radial distribution, marginalizing over host mass and concentration from abundance matching  
  > "we treat it as a free parameter, along with other parameters describing the lens halo: the host halo mass and concentration ($M_\text{host}$, $c_\text{host}$), and the log–log slope ($\eta$)" (6 Comparison to LCDM Predictions)
   - parameter: eta=0.9; c_subs/c_host = 0.2 and 1.0; abundance matching with 0.2 dex scatter  
  > "we assume the mass function slope is $\eta=0.9$, and we show two possible values for the subhalo concentration, $c_\text{subs}/c_\text{host}=0.2$ and 1.0" (6 Comparison to LCDM Predictions)
   - assumption: Subhalo spatial distribution independent of mass, isotropic, NFW radial profile  
  > "the subhalo spatial distribution is *independent* from the subhalo mass function" (6 Comparison to LCDM Predictions)
   - fitting: _not stated_
   - validation: Limits consistent with theory but parameters degenerate  
  > "substructure limits from SDP.81 are currently consistent with theoretical predictions." (6 Comparison to LCDM Predictions)

## Software

- **CASA** : Simulating mock ALMA observations  
  > "the lensed images were used to simulate ALMA observations using the Common Astronomy Software Applications package (CASA)." (4.1 Mock observations)
- **Elemental** : Distributed dense linear algebra for the Fourier operator  
  > "we take advantage of the “*Elemental*” dense linear algebra library, which efficiently performs linear algebra operations over distributed cores" (4 implementation, simulations, and tests)
- **emcee** : MCMC sampling procedure, parallelized with MPI  
  > "Our implementation allows sampling the posterior in parallel, over many cores, taking advantage of the MPI message-passing system." (4.1 Mock observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Subhalo mass log10(M_sub) | 8.96 | 0.12 | log10 Msun | 4 | $\log_{10} (M_{\rm sub})$ / subhalo mass ($M_\odot$) / $8.96 \pm 0.12$ |
| Detection significance, joint bands 6 and 7 | 6.9 | not stated | sigma | 4 | with a significance of $6.9\sigma$ in a joint fit to data from bands 6 and 7 |
| Delta E improvement from adding subhalo, joint fit | -47.3 | not stated | dimensionless | 4 | improves the marginalized log posterior fit by $\Delta\ensuremath{{\cal  E} }= -47.3$ in the joint fit |
| Subhalo position (x, y) | (-0.694, 0.749) | 0.025, 0.044 | arcsec | 4 | $x_{\rm sub}$ / subhalo position x ($^{\prime\prime}$) / $-0.694 \pm 0.025$ |
| Radial slope alpha | 1.06 | 0.03 | dimensionless | 2 | $\alpha$ / radial slope / $1.06  \pm 0.03$ |
| Delta E for second subhalo (~1e8 Msun) | ≈ -22 | not stated | dimensionless | 5 | could improve the fit marginally, with $\Delta\ensuremath{{\cal  E} }\approx -22$, compared to the 1-subhalo model. |
| 95% central range of n at 1e9 Msun | 0.012 < n < 0.2 | 95% interval | arcsec^-2 | 6 | the central 95% confidence region is $0.012\ {\rm arcsec}^{-2} < n < 0.2\ {\rm arcsec}^{-2}$ |
| Chi-squared of smooth fit over 5x5 arcsec region | 2e5 for 1.7e5 dof | not stated | dimensionless | 2 | our model obtains $\chi^2 = 2\times 10^5$ for $1.7\times 10^5$ degrees of freedom |
| Lens host halo mass from abundance matching | 8.7e12 | factor of 3.5 | Msun/h | 7 | The typical halo mass we found with this procedure is roughly $8.7 \times 10^{12} M_\odot h^{-1}$, with an approximate uncertainty of a factor of 3.5. |

## Qualitative findings

- Sensitivity to individual subhalos is lost at masses below ~1e7 Msun  
  > "the SDP.81 data set loses sensitivity for detecting individual subhalos at masses $\lesssim 10^7 M_\odot$." (7 Discussion)
- Marginalizing over antenna phase errors removes false positives that appear in uncorrected mock analyses  
  > "when phase errors are marginalized over appropriately, resulting in the disappearance of the false detections." (4.2 Phase corruption)

## Claim tuples

- H: Does ALMA visibility data of SDP.81 reveal a dark matter subhalo? | E: Linearized search then nonlinear fit of bands 6 and 7 continuum visibilities | R: Subhalo of log M = 8.96±0.12 with Delta E = -47.3, 6.9 sigma, seen in both bands | F: A subhalo is detected in projected mass | **supported**
- H: Is there additional lower-mass substructure? | E: Second linearized search about model with one subhalo | R: ~1e8 Msun candidate with Delta E ≈ -22, <5 sigma, near the first subhalo | F: Hints only, not a detection | **partially**
- H: Is the measured substructure abundance consistent with LCDM? | E: Compare constraints with predicted subhalo mass function including host halo uncertainties | R: Limits consistent with predictions, possibly hinting lower normalization | F: Consistent given current host halo uncertainties | **supported**
- H: Should substructure analyses use visibilities rather than CLEAN images? | E: Mock tests with and without phase error marginalization | R: Uncorrected phase errors give numerous false positives | F: Visibility modeling with marginalization is needed; may explain disagreement with Inoue et al. | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility-domain modeling allows marginalizing antenna phase errors and has well-characterized noise, unlike CLEAN images  
  > "In addition, CLEAN images are produced through a non-linear deconvolution procedure whose effects on the data and the correlated noise properties can not be well quantified." (4.2 Phase corruption)
- Alternative: Gradient and curvature source priors compared on mock data; DC mode removed from the clump power-spectrum prior to avoid magnification bias  
  > "To fix this issue, we removed the DC mode from this covariance matrix" (4.1 Mock observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple spherical pseudo-Jaffe subhalo profile may leave residuals fitted by lower-mass substructure  
  > "We have assumed an extremely simple mass profile for the subhalos, a spherical tidally truncated pseudo-Jaffe model" (5.2 Search for additional substructure)
- Limitation (authors): Only continuum used; CO line data not analyzed; weaker data corruptions such as decorrelation not studied  
  > "The effects of decorrelation, visibility smearing due to frequency averaging, choice of parameterization for antenna phase error corrections, and antenna amplitude errors are among these effects." (7 Discussion)
- Caveat (inferred, ours): Only ~40% of visibilities used, selected by noise cut; effect on result not tested
- Caveat (inferred, ours): Result depends on pseudo-Jaffe profile and fixed truncation relation
- Caveat (inferred, ours): Significance from Laplace/linearized Delta E; no independent validation on real data
- Caveat (inferred, ours): Host halo mass and subhalo concentration degenerate, limiting LCDM test
- Caveat (inferred, ours): Detection near a cluster member may be affected by environment

## Reproducibility

- Data public (paper): ALMA Science Verification data, cited and acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00016.SV." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Custom lens-fitting pipeline not released
- Missing: MCMC and prior details
- Missing: Source prior choice and grid for SDP.81
- Missing: Specific visibility selection beyond noise cuts
- Data volume (inferred): Tens to hundreds of GB for SV continuum visibilities of bands 6 and 7; heavy compute needed
- Score (inferred): 3/5, Public data and clear formalism, but bespoke code, missing sampler and prior details, and cluster-scale compute make exact reproduction hard.
- Rediscovery candidate: no, Data are public but the recipe needs a custom visibility-domain lens pipeline with incomplete settings.

## Links

- Method: (cite: Hezaveh13A) (Proposed ALMA subhalo detection and linearized treatment)
- Method: (cite: suyu:06) (Pixelated source lens modeling with evidence-based regularization)
- Method: (cite: Mao:15) (Subhalo mass function model used for LCDM comparison)
- Companion: (cite: SDP81) (ALMA Science Verification observations of SDP.81)
- Companion: (cite: Inoue2015) (Independent CLEAN-image substructure analysis of SDP.81 with different conclusions)
- Related: ALMA Science Verification
- Related: SDSS
- Related: Dark Sky Simulations

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 51,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
