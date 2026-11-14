# Morphological Complexity of NGC 628—A Multiwavelength Multiscale Analysis Using the Ordinal Pattern Framework

`2026ApJ..1003...50C` | The Astrophysical Journal 2026 | first author: Chanu, Athokpam Langlen | arXiv: 2604.08409 | DOI: 10.3847/1538-4357/ae5c98

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: How complex is the morphology of NGC 628 across NUV, NIR, MIR and mm (ALMA CO 2-1) images and smoothing scales, as measured with ordinal-pattern statistics (permutation entropy, disequilibrium, statistical complexity, ordinal network node entropy)?  
  > "In this study, using near-ultraviolet (NUV), near-infrared (NIR), mid-infrared (MIR), and millimeter (mm) images, we quantify its morphological complexity across wavelengths." (Introduction)
- Target **NGC 628**: coordinates _not stated_; z/distance 9.84 Mpc  
  > "grand design spiral galaxy (SA(s)C; (cite: 1991rc3..book.....D)) at a distance of 9.84 Mpc (cite: 10.1093/mnras/staa3668)" (3 NGC 628 Galaxy - multiwavelength view and observed data); distance from (cite: 10.1093/mnras/staa3668)  
  > "grand design spiral galaxy (SA(s)C; (cite: 1991rc3..book.....D)) at a distance of 9.84 Mpc (cite: 10.1093/mnras/staa3668)" (3 NGC 628 Galaxy - multiwavelength view and observed data)

## Data provenance

- ALMA projects: 2012.1.00650.S
- bands: mm; CO (J=2-1) moment 0 map  
  > "We use reduced archival data from the Atacama Large Millimeter/submillimeter Array (ALMA; (cite: Leroy_2021a; Leroy_2021b)) CO ($J=2\to 1$) moment 0 map" (3.1 Multiwavelength observed data of NGC 628)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Reduced archival PHANGS-ALMA data (PHANGS Treasury)  
  > "We use reduced archival data from the Atacama Large Millimeter/submillimeter Array (ALMA; (cite: Leroy_2021a; Leroy_2021b)) CO ($J=2\to 1$) moment 0 map" (3.1 Multiwavelength observed data of NGC 628); "both obtained from the PHANGS Treasury." (3.1 Multiwavelength observed data of NGC 628)
- Line: CO J=2-1 (not stated)
- Other facility **UVIT (AstroSat)**: NUV image (NUVB4 N263M filter, 1365 s exposure), archival Level 1 data from ISSDC  
  > "We use archival UV observations from the Ultraviolet Imaging Telescope (UVIT) on board the AstroSat telescope (cite: 2012SPIE.8443E..1NK)." (3.1 Multiwavelength observed data of NGC 628); "We use only the NUVB4 N263M filter (1365s exposure time)." (3.1 Multiwavelength observed data of NGC 628)
- Other facility **JWST (MIRI F2100W, NIRCam F360M)**: MIR and NIR images from the PHANGS Treasury  
  > "the James Webb Space Telescope (JWST; (cite: Lee_2023)) MIR instrument (MIRI)" (3.1 Multiwavelength observed data of NGC 628); "both obtained from the PHANGS Treasury." (3.1 Multiwavelength observed data of NGC 628)
- Other facility **PHANGS**: Program supplying the reduced ALMA CO(2-1), JWST MIRI and NIRCam images  
  > "NGC 628 is a part of the Physics at High Angular Resolution in Nearby GalaxieS (PHANGS) program" (3.1 Multiwavelength observed data of NGC 628)
- External data: Reduced PHANGS-ALMA CO(2-1) moment 0 map ('strict' map) of NGC 628  
  > "We use reduced archival data from the Atacama Large Millimeter/submillimeter Array (ALMA; (cite: Leroy_2021a; Leroy_2021b)) CO ($J=2\to 1$) moment 0 map" (3.1 Multiwavelength observed data of NGC 628); "With the ALMA strict map, diffuse emission is filtered out (cite: Leroy_2021a)." (3.2 Multiwavelength view of NGC 628) [from (cite: Leroy_2021a; Leroy_2021b)]
- External data: Distance to NGC 628: 9.84 Mpc  
  > "at a distance of 9.84 Mpc (cite: 10.1093/mnras/staa3668)" (3 NGC 628 Galaxy - multiwavelength view and observed data) [from (cite: 10.1093/mnras/staa3668)]
- External data: Inclination of NGC 628 (i=8.9 deg)  
  > "nearly face-on (i=8.9$^\circ$; (cite: Lang_2020))" (3 NGC 628 Galaxy - multiwavelength view and observed data) [from (cite: Lang_2020)]
- External data: Correlation length l_corr from the two-point correlation function of star clusters in NGC 628, used for comparison with the transition scale  
  > "is consistent with the correlation length, $l_{\rm corr}$, inferred using the two-point correlation function for NGC 628 (cite: Grasha_2017; 10.1093/mnras/stab2413)." (4.3 Surrogate analysis) [from (cite: Grasha_2017; 10.1093/mnras/stab2413)]
- Simulation/model as data: Gaussian random fields (zero mean, unit variance, 500 x 500 pixels, Gaussian-smoothed with standard deviation s) used as benchmarks; also GRFs with power spectra P(k) ~ k^-n, n=0,1,2,3  
  > "We simulate GRFs with zero mean and unit variance on a $500 \times 500$ pixel grid, approximately comparable to the galaxy data." (2.3 Ordinal pattern analysis for Gaussian random fields); "we generate GRFs with power spectra of the form $P(k)\propto k^{-n}$, where $n=0,1,2,$ and 3." (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Reduced archival PHANGS-ALMA moment 0 map used (no recalibration described)  
  > "We use reduced archival data from the Atacama Large Millimeter/submillimeter Array (ALMA; (cite: Leroy_2021a; Leroy_2021b)) CO ($J=2\to 1$) moment 0 map" (3.1 Multiwavelength observed data of NGC 628)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.417 arcsec/pix after interpolation; 19.89 pc per pixel  
  > "Each pixel corresponds to a physical size of 19.89 pc." (3.1 Multiwavelength observed data of NGC 628)
- image size: 530 x 311 pixels (10.54 x 6.19 kpc^2)  
  > "consist of $530 \times 311$ pixels" (3.1 Multiwavelength observed data of NGC 628)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: All images convolved to a common resolution of 1.2 arcsec (UVIT, the poorest), 57 pc; then further Gaussian coarse-graining with kernel sigma in pixel units  
  > "We convolve all images to a common resolution of $1.2^{''}$ (UVIT) (the poorest resolution among the maps), corresponding to the physical scale of 57 pc." (3.1 Multiwavelength observed data of NGC 628); "we systematically perform coarse-graining (smoothening) of the multi-wavelength images using Gaussian kernels with different standard deviations $\sigma$ (in units of pixel numbers)." (3.3 Coarse graining images)
- final beam: 1.2 arcsec (57 pc), common resolution  
  > "We convolve all images to a common resolution of $1.2^{''}$ (UVIT) (the poorest resolution among the maps), corresponding to the physical scale of 57 pc." (3.1 Multiwavelength observed data of NGC 628)
- final rms: _not stated_

### Inherited from earlier work

- ALMA CO(2-1) map reduction and map type (PHANGS-ALMA strict moment 0 map)  
  > "We use reduced archival data from the Atacama Large Millimeter/submillimeter Array (ALMA; (cite: Leroy_2021a; Leroy_2021b)) CO ($J=2\to 1$) moment 0 map" (3.1 Multiwavelength observed data of NGC 628); "With the ALMA strict map, diffuse emission is filtered out (cite: Leroy_2021a)." (3.2 Multiwavelength view of NGC 628) [from (cite: Leroy_2021a; Leroy_2021b)]
- Reduction of raw UVIT data  
  > "The raw UVIT data is reduced following (cite: Amrutha_2025)." (3.1 Multiwavelength observed data of NGC 628) [from (cite: Amrutha_2025)]
- Ordinal pattern, permutation entropy, complexity and ordinal network formalism  
  > "This section follows (cite: pessa2021ordpy)." (2 Framework of ordinal patterns) [from (cite: pessa2021ordpy)]

### Not stated but needed to reproduce (our reading)

- Exact PHANGS-ALMA data release / file name of the NGC 628 CO(2-1) moment 0 map and which angular-resolution version was used (native ALMA PSF is only given in Table 1 as a single number)
- Interpolation/regridding method and convolution kernel implementation used to bring all four images to 0.417 arcsec/pix and 1.2 arcsec
- How NaN / blanked pixels in the ALMA moment 0 map and the other images were treated before computing ordinal patterns
- Flattening order used for the sub-matrices (the paper says one fixed way is chosen) and the code actually used to compute H, D_E, C and node entropies
- Exact set of sigma values and the sigma grid used for Figures 4-9
- UVIT observation ID, reduction details and pointing, beyond the filter and exposure time
- Phase-randomisation algorithm and random seeds for the 60 surrogate realisations
- Fitting method and weights for the power-law fits to Delta S_gn
- How the transition sigma^(c) was identified beyond visual inspection

## Analysis recipe

1. **Homogenise the four images to a common grid and resolution**: Interpolate to a common plate size/area and convolve to the poorest resolution (UVIT 1.2 arcsec)  
  > "To ensure consistent spatial scales across all four images, we apply interpolation so that the plate size would cover the same area of the galaxy" (3.1 Multiwavelength observed data of NGC 628); "We convolve all images to a common resolution of $1.2^{''}$ (UVIT) (the poorest resolution among the maps), corresponding to the physical scale of 57 pc." (3.1 Multiwavelength observed data of NGC 628)
   - parameter: 19.89 pc per pixel; 530 x 311 pixels  
  > "Each pixel corresponds to a physical size of 19.89 pc." (3.1 Multiwavelength observed data of NGC 628); "consist of $530 \times 311$ pixels" (3.1 Multiwavelength observed data of NGC 628)
   - assumption: Distance 9.84 Mpc  
  > "at a distance of 9.84 Mpc (cite: 10.1093/mnras/staa3668)" (3 NGC 628 Galaxy - multiwavelength view and observed data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Coarse-grain images at multiple smoothing scales**: Gaussian smoothing with kernel standard deviation sigma in pixels, on top of the common smoothing sigma_a  
  > "we systematically perform coarse-graining (smoothening) of the multi-wavelength images using Gaussian kernels with different standard deviations $\sigma$ (in units of pixel numbers)." (3.3 Coarse graining images)
   - parameter: sigma_a = 1.22 pixels (24.2 pc) for the common 1.2 arcsec smoothing; effective scale sigma_eff converted to FWHM length L_FWHM  
  > "and the corresponding smoothing scale is 24.2 pc. In pixel units, this corresponds to a smoothing scale, denoted by $\sigma_a$, of 1.22." (3.3 Coarse graining images)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compute ordinal-pattern statistics H, D_E, C on each smoothed image**: Map each d_x x d_y sub-matrix to a permutation state, build the ordinal probability distribution, then compute normalised permutation entropy H, disequilibrium D_E (Jensen-Shannon based) and statistical complexity C = D_E H  
  > "The ordinal patterns framework, along with its associated statistical measures: permutation entropy ($H$), disequilibrium ($D_E$), statistical complexity ($C$), and ordinal network node entropy" (abstract)
   - parameter: Embedding dimensions (d_x,d_y) = (2,2), (2,3), (2,4); unit embedding delays  
  > "We use combinations of $(d_x,d_y)=$ (2,2), (2,3), and (2,4)." (4 Results for NGC 628); "Here we restrict to unit embedding delays." (2 Framework of ordinal patterns)
   - assumption: Embedding dimensions limited by the number of pixels to keep (d_x d_y)! much less than 164,830  
  > "These choices are constrained by the total number of available pixels in the data" (4 Results for NGC 628)
   - fitting: _not stated_
   - validation: Repeated all calculations with d_x and d_y interchanged; negligible effect  
  > "To test the effect of rotation of the data, we repeat all calculations for the four image data, as well as the GRFs, after interchanging $d_x$ and $d_y$" (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths)
4. **Estimate uncertainties on H, D_E and C**: Split the image into 20 equal patches, compute statistics per patch, take the standard deviation; propagate to C including the H-D_E covariance  
  > "We divide the data into 20 equal-sized patches" (4 Results for NGC 628); "and treat the standard deviations from the 20 values as the statistical uncertainties." (4 Results for NGC 628)
   - parameter: 20 patches  
  > "We divide the data into 20 equal-sized patches" (4 Results for NGC 628)
   - assumption: Patches treated as independent, although they are actually correlated, so errors are slightly underestimated  
  > "Note that this way of estimating errors will slightly underestimate the true errors since the different patches are actually correlated." (4 Results for NGC 628)
   - fitting: _not stated_
   - validation: _not stated_
5. **Identify the transition scale across wavelengths**: Visual inspection of D_E-H and C-H planes for the convergence of the four wavelengths with increasing sigma; convert sigma^(c) to a physical scale L_FWHM  
  > "We observe that, for all embedding dimensions, the values across the four wavelengths converge for $\sigma \ge 4$." (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths); "we obtain a value of 196 pc as the effective transition length scale." (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths)
   - parameter: sigma^(c) ~ 4 pixels; L_FWHM(sigma=3) ~ 152 pc used to estimate the error  
  > "However, a rough estimate using $L_{\rm FWHM}(\sigma=3) \simeq 152$ pc gives the error to be" (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths)
   - fitting: _not stated_
   - validation: Compared with the correlation length l_corr from star-cluster two-point correlation function; uncertainty acknowledged as not rigorously quantified  
  > "We note that this value is not precisely determined, and the uncertainty has not been rigorously quantified." (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths); "The close agreement between $L^{(c)}_{\rm FWHM}$ and $l_{\rm corr}$ supports the interpretation" (4.3 Surrogate analysis)
6. **Test the transition scale with phase-randomised surrogates**: Construct phase-randomised surrogate Gaussian random fields preserving the exact power spectrum of each image at each sigma and compare their mean (H,C) with the galaxy  
  > "we construct realizations of phase-randomized surrogate Gaussian random fields for each wavelength and smoothing scale $\sigma$." (4.3 Surrogate analysis); "obtained from 60 realizations of surrogate fields (with error bars) along with the galaxy results." (4.3 Surrogate analysis)
   - parameter: 60 surrogate realisations per case  
  > "obtained from 60 realizations of surrogate fields (with error bars) along with the galaxy results." (4.3 Surrogate analysis)
   - assumption: Surrogates retain linear correlations (power spectrum) but destroy nonlinear phase-dependent correlations  
  > "These surrogates preserve the exact power spectrum of the galaxy but have randomized Fourier phases" (4.3 Surrogate analysis)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare the C-H trajectories with Gaussian random fields of power-law spectra**: Generate GRFs with P(k) ~ k^-n (n=0,1,2,3), smooth with s, and overlay their (H,C) curves on the galaxy trajectories  
  > "we generate GRFs with power spectra of the form $P(k)\propto k^{-n}$, where $n=0,1,2,$ and 3." (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths)
   - parameter: n = 0, 1, 2, 3; fixed seeds  
  > "we generate GRFs with power spectra of the form $P(k)\propto k^{-n}$, where $n=0,1,2,$ and 3." (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths)
   - fitting: _not stated_
   - validation: _not stated_
8. **Compute ordinal-network global node entropies and fit power laws in sigma**: Map images to horizontal and vertical ordinal networks, compute S_gn^hor, S_gn^ver and their difference, fit Delta S_gn = a sigma^-b  
  > "We again fit inverse power-law functions (dashed lines): $\Delta$S$_{\rm gn}(\sigma)=a\sigma^{-b}$ to the data (markers)" (4.5 Ordinal Network Global Node entropy)
   - parameter: (d_x,d_y) = (2,3)  
  > "their difference ($\Delta$S$_{\rm gn}=$S$_{\rm gn}^{\rm hor}-$S$_{\rm gn}^{\rm ver}$) using $(d_x,d_y)=(2,3)$" (4.5 Ordinal Network Global Node entropy)
   - fitting: Inverse power-law fit Delta S_gn(sigma) = a sigma^-b; fitting method not stated  
  > "We again fit inverse power-law functions (dashed lines): $\Delta$S$_{\rm gn}(\sigma)=a\sigma^{-b}$ to the data (markers)" (4.5 Ordinal Network Global Node entropy)
   - validation: _not stated_

## Software

- **astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Transition length scale L_FWHM^(c) | 196 pc (quoted as ~200 pc) | ~10% (22 pc) | pc | 5 | we obtain a value of 196 pc as the effective transition length scale.; Hence the uncertainty must be around ten percent. |
| Critical transition smoothing scale sigma^(c) | ~4 | not stated | pixels | 5 | Hence, based on visual inspection, $\sigma = \sigma^{(c)} \sim 4$ emerges as a critical transition scale |
| Transition smoothing scale for NIR sigma^(c) | ~5 | not stated | pixels | 6 | We note that for NIR, $\sigma^{(c)}\sim 5$ and its $CH$-curve appears different |
| Power-law exponent b of Delta S_gn(sigma), NUV | 0.8705 | not stated | dimensionless | 8 | with exponents: $b=$ 0.8705 (NUV), 0.6730 (MIR), and 0.4854 (mm) |
| Power-law exponent b of Delta S_gn(sigma), MIR | 0.6730 | not stated | dimensionless | 8 | with exponents: $b=$ 0.8705 (NUV), 0.6730 (MIR), and 0.4854 (mm) |
| Power-law exponent b of Delta S_gn(sigma), mm (ALMA CO 2-1) | 0.4854 | not stated | dimensionless | 8 | with exponents: $b=$ 0.8705 (NUV), 0.6730 (MIR), and 0.4854 (mm) |
| Power-law exponent b of Delta S_gn(sigma), NIR, sigma < 5 | 0.7133 | not stated | dimensionless | 8 | For NIR, two $\sigma$ regimes emerge: $b=0.7133$ for $\sigma < 5$, and $b=1.2793$ for $\sigma \geq 5$ |
| Power-law exponent b of Delta S_gn(sigma), NIR, sigma >= 5 | 1.2793 | not stated | dimensionless | 8 | For NIR, two $\sigma$ regimes emerge: $b=0.7133$ for $\sigma < 5$, and $b=1.2793$ for $\sigma \geq 5$ |
| Physical pixel size after regridding | 19.89 | not stated | pc per pixel | 1 | Each pixel corresponds to a physical size of 19.89 pc. |
| Range of smoothing scales probed | 74 to 472 pc | not stated | pc | 2 | our analysis probes smoothing scales ranging from 74 to 472 pc |

## Qualitative findings

- For sigma < 4, H decreases with increasing wavelength for all embedding dimensions (NUV highest, mm lowest); for sigma >= 4 the wavelengths converge  
  > "For scales $\sigma<4$, $H$ decreases with increasing wavelength for all embedding dimensions, as seen in panel (a)." (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths)
- mm (CO) H varies only mildly with smoothing scale, attributed to cold clumpy emission without diffuse structure  
  > "At mm wavelength, however, $H$ shows only mild variation with $\sigma$" (4.1 Entropy, Disequilibrium, and Complexity for different wavelength images of NGC 628 across scales)
- CH-trajectories of GRFs with n=1 (pink noise) align most closely with the galaxy trajectories  
  > "the $CH$-trajectories of the GRFs with $n=1$ align most closely with those of the NGC 628 galaxy field" (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths)

## Claim tuples

- H: Is there a characteristic spatial scale in NGC 628 separating star-formation and feedback driven structure from dynamics-driven morphology? | E: Compare H, D_E, C of NUV, NIR, MIR and ALMA CO(2-1) images across Gaussian smoothing scales and embedding dimensions | R: The four wavelengths converge for sigma >= 4, corresponding to L_FWHM = 196 pc (~200 pc, ~10% uncertainty) | F: A transition scale of ~200 pc separates small-scale star-formation/feedback structure from larger-scale morphology set by galactic dynamics | **supported**
- H: Do C-H trajectories at all wavelengths converge to a common attractor curve resembling Gaussian random fields? | E: Plot C vs H for all wavelengths and smoothing scales and overlay GRFs with power spectra k^-n | R: Trajectories align along one curve per embedding dimension except mm at small sigma; GRFs with n=1 align most closely | F: A common attractor curve consistent with isotropic Gaussian random fields at large scales | **partially**
- H: Is the galaxy's CH-curve determined solely by its power spectrum? | E: Compare (H,C) of the galaxy with 60 phase-randomised surrogate fields per wavelength and smoothing scale | R: Surrogates track the galaxy for (2,2) but deviate for (2,3) and (2,4), strongly around sigma ~ 4 | F: Nonlinear phase-dependent correlations emerge at the transition scale | **supported**
- H: Does ordinal network global node entropy show scale-dependent structure and a hierarchical organisation? | E: Fit inverse power laws to Delta S_gn(sigma) for NUV, NIR, MIR and mm at (d_x,d_y)=(2,3) | R: Exponents b of 0.8705 (NUV), 0.6730 (MIR), 0.4854 (mm); NIR has two regimes (0.7133 and 1.2793) | F: Scale-free reduction of structural information pointing to hierarchical organisation | **supported**

## Reasoning

- Why this data: NGC 628 chosen as a well-studied face-on spiral with high-resolution multiwavelength public data  
  > "We select NGC 628 (the Phantom Galaxy), a well-studied, face-on spiral galaxy with high-resolution, multiwavelength data, meeting criteria for 2D-analysis, emission diversity, and data accessibility." (Introduction)
- Why this method: Embedding dimensions limited by number of pixels for statistical reliability  
  > "These choices are constrained by the total number of available pixels in the data" (4 Results for NGC 628)
- How they decided it was enough: _not stated_
- Limitation (authors): Transition scale not precisely determined; uncertainty not rigorously quantified  
  > "We note that this value is not precisely determined, and the uncertainty has not been rigorously quantified." (4.2 Entropy, Disequilibrium, and Complexity of NGC 628 across observing wavelengths)
- Limitation (authors): Patch-based errors slightly underestimate true errors because patches are correlated  
  > "Note that this way of estimating errors will slightly underestimate the true errors since the different patches are actually correlated." (4 Results for NGC 628)
- Limitation (authors): Study limited to the inner disk of NGC 628  
  > "However, this study is limited to the inner disk of NGC 628." (4.4 Disorder to order transition)
- Limitation (authors): ALMA strict map filters out diffuse emission  
  > "With the ALMA strict map, diffuse emission is filtered out (cite: Leroy_2021a)." (3.2 Multiwavelength view of NGC 628)
- Caveat (inferred, ours): Single galaxy (pilot study), so the 200 pc scale and universality claim are not tested on other galaxies
- Caveat (inferred, ours): Transition scale is chosen by visual inspection with a crude uncertainty
- Caveat (inferred, ours): The CO map has the narrowest dynamic range and is filtered by the strict mask, which may drive the mm behaviour rather than molecular gas structure
- Caveat (inferred, ours): Common 1.2 arcsec resolution set by UVIT discards the finer ALMA and JWST resolution in the main analysis, and the 200 pc scale is only about 3.5 beams
- Caveat (inferred, ours): Error bars from 20 correlated patches are underestimated

## Reproducibility

- Data public (paper): Publicly available multiwavelength imaging data (PHANGS Treasury, JWST MAST, ISSDC for UVIT)  
  > "Using publicly available multi-wavelength imaging data, we systematically analyze" (5 Conclusions)
- Products in archive: ALMA CO(2-1) moment 0 map obtained from the PHANGS Treasury  
  > "both obtained from the PHANGS Treasury." (3.1 Multiwavelength observed data of NGC 628)
- Missing: Exact PHANGS-ALMA map file and version, and the ALMA map resolution/regridding details
- Missing: Analysis code for H, D_E, C and node entropy, and the chosen flattening convention
- Missing: UVIT observation ID and reduction parameters
- Missing: Surrogate generation details and seeds
- Missing: Sigma grids and fitting procedure for the power laws
- Data volume (inferred): Under 1 GB (reduced PHANGS moment 0 map plus JWST and UVIT images; no raw ALMA data processing)
- Score (inferred): 3/5, Data are public and the statistics are well defined with numeric results, but the exact ALMA product, regridding/convolution and surrogate procedures, and the code are not given.
- Rediscovery candidate: no, The ALMA role is a single reduced PHANGS moment 0 map; the recipe lacks the flattening convention, regridding method, UVIT reduction and surrogate details, so exact numbers are hard to redo from the paper alone.

## Links

- Method: (cite: pessa2021ordpy) (Ordinal-pattern framework (ordpy) that the methods section follows)
- Method: (cite: rosso2007distinguishing) (Defines the statistical complexity measure and the complexity-entropy plane)
- Method: (cite: Leroy_2021a) (PHANGS-ALMA CO(2-1) data reduction and map products)
- Method: (cite: Amrutha_2025) (UVIT raw data reduction followed)
- Companion: (cite: Lee_2023) (PHANGS-JWST Treasury source of the MIRI and NIRCam images)
- Companion: (cite: Leroy_2021b) (PHANGS-ALMA survey paper cited with Leroy_2021a for the CO(2-1) data)
- Related: PHANGS
- Related: PHANGS-ALMA
- Related: PHANGS-JWST Treasury (JWST program 2107)

## Checks

```json
{
 "quotes": 89,
 "quotes_ok": 89,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 55,
  "rate": 0.561
 },
 "evidence_ok": true
}
```
