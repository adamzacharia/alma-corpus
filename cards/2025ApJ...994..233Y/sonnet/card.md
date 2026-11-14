# ALMA-IMF. XX. Core Fragmentation in the W51 High-mass Star-forming Region

`2025ApJ...994..233Y` | The Astrophysical Journal 2025 | first author: Yoo, T. | arXiv: 2509.06749 | DOI: 10.3847/1538-4357/ae0619

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: How do ALMA-IMF cores in the W51-E and W51-IRS2 protoclusters fragment into compact sources, and how does fragmentation depend on core mass and compare with thermal Jeans fragmentation?  
  > "We present a study of core fragmentation in the W51-E and W51-IRS2 protoclusters in the W51 high-mass star-forming region." (abstract)
- Target **W51-E**: coordinates _not stated_; z/distance d = 5.4 kpc (W51)  
  > "the nearest ($5.1$–$5.41\,{\rm kpc}$; (cite: xu09; sato10)) extreme high-mass" (1 Introduction); distance from Xu09; Sato10 (range 5.1-5.41 kpc); 5.4 kpc used  
  > "the nearest ($5.1$–$5.41\,{\rm kpc}$; (cite: xu09; sato10)) extreme high-mass" (1 Introduction)
- Target **W51-IRS2**: coordinates _not stated_; z/distance d = 5.4 kpc (W51)  
  > "$d=5.4\,{\rm kpc}$ is the distance to W51" (4.2 Mass dependence of fragmentation); distance from Xu09; Sato10 (range 5.1-5.41 kpc); 5.4 kpc used  
  > "$d=5.4\,{\rm kpc}$ is the distance to W51" (4.2 Mass dependence of fragmentation)

## Data provenance

- ALMA projects: 2017.1.01355.L, 2015.1.01596.S, 2017.1.00293.S
- bands: Band 3 (3 mm) and Band 6 (1.3 mm)  
  > "We utilized the $3\,{\rm mm}$ (Band 3) and $1.3\,{\rm mm}$ (Band 6) continuum archival data of the W51" (2.1 ALMA-IMF continuum images and core catalog)
- frequencies and spectral setup: central frequency ~86 GHz (Band 3) and 218 GHz (Band 6)  
  > "The central frequency of each image is approximately $86\,{\rm GHz}$ in Band 3 and $218\,{\rm GHz}$ in Band 6." (2.2 High-resolution ALMA continuum image)
- continuum bandwidth: _not stated_
- arrays: 12 m array (long-baseline data); 12 m mosaic (ALMA-IMF)  
  > "Both observations used 12 m array with a baseline ranging from 85 to 16196$\,{\rm m}$." (2.2 High-resolution ALMA continuum image)
- configurations: _not stated_
- baselines: 85 to 16196 m (high-resolution data)  
  > "Both observations used 12 m array with a baseline ranging from 85 to 16196$\,{\rm m}$." (2.2 High-resolution ALMA continuum image)
- angular resolution: High-res: 27.3x20.0 mas (1.3 mm), 66.1x41.8 mas (3 mm); ALMA-IMF W51-E 0.28"/0.30" (3/1.3 mm), W51-IRS2 0.27"/0.48"  
  > "The angular resolution of the continuum images is $27.3\,{\rm mas}\times20.0\,{\rm mas}$ in $1.3\,{\rm mm}$ and $66.1\,{\rm mas}\times41.8\,{\rm mas}$ in $3\,{\rm mm}$" (2.2 High-resolution ALMA continuum image)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data; PIs Goddi (2015.1.01596.S), Ginsburg (2017.1.00293.S), ALMA-IMF large program  
  > "we utilized archival high-resolution ALMA datasets from the ALMA cycle 3 program 2015.1.01596.S (PI: C. Goddi)" (2.2 High-resolution ALMA continuum image)
- External data: ALMA-IMF core catalog (getsf cores, masses, FWHM sizes, PPMAP temperatures, completeness limits)  
  > "we used the core catalogs created by `getsf` from the $1.3\,{\rm mm}$ and $3\,{\rm mm}$ image smoothed to $2700\,{\rm AU}$ resolution as described in (cite: louvet24)." (2.1 ALMA-IMF continuum images and core catalog) [from (cite: louvet24)]
- External data: Hot core catalog (CH3OCHO-based) used to assign 100 K / 300 K temperatures  
  > "For 1 W51-E and 5 W51-IRS2 cores associated with hot cores candidates found in (cite: bonfand24) where ${\rm CH_3OCHO}$ map is used, $100\,{\rm K}$ dust temperature is adopted." (4.2 Mass dependence of fragmentation) [from (cite: bonfand24)]
- External data: Dust opacities kappa_1.3mm=0.0083 and kappa_3mm=0.0017 cm2/g (thin ice mantles, 1e5 yr, 1e6 cm-3)  
  > "we adopted the dust opacity $\kappa_{1.3\,{\rm mm}}=0.0083\,{\rm cm^2\,g^{-1}}$ and $\kappa_{3\,{\rm mm}}=0.0017\,{\rm cm^2\,g^{-1}}$" (3.5 Temperature constraints through modified blackbody model) [from (cite: ossenkopf94)]
- External data: Infall rates ~1-5e-3 Msun/yr for W51e2e, W51e8, W51North  
  > "The mass infall rates estimated by (cite: goddi20) for the three hot cores based on the outflow rates are $\sim1$–$5\times10^{-3}\,M_\odot/{\rm yr}$." (5.1.2 Discussion on insufficient Jeans mass) [from (cite: goddi20)]

## Processing

### Calibration

- pipeline or manual: ALMA ScriptforPI.py and ScriptforImaging.py, then eight-stage iterative phase self-calibration  
  > "To produce the image files, we run Python scripts provided with ALMA raw data, `ScriptforPI.py` and `ScriptforImaging.py`." (2.2 High-resolution ALMA continuum image)
- casa version: CASA 5.7.0  
  > "The data reduction and self-calibration were conducted by the Common Astronomy Software Applications (CASA) package ((cite: mcmullin07); version 5.7.0)." (2.2 High-resolution ALMA continuum image)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: absolute calibration errors assumed 10% at 1.3 mm and 5% at 3 mm  
  > "absolute calibration errors—assumed to be 10% at $1.3\,{\rm mm}$ and 5% at $3\,{\rm mm}$" (3.2 Spectral indices)
- self calibration: eight stages of iterative phase self-calibration with tclean, gaincal, applycal  
  > "start eight stages of iterative phase self-calibration process with `tclean`, `gaincal`, and `applycal`." (2.2 High-resolution ALMA continuum image)

### Imaging

- task: tclean  
  > "produce a dirty image of the long-baseline data with `tclean` task." (2.2 High-resolution ALMA continuum image)
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0  
  > "For the weighting scheme, we employed Briggs weighting with robust=0." (2.2 High-resolution ALMA continuum image)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Two cleanmasks: shallower in steps 1-3, deeper in steps 4-8; covers visually identified sources  
  > "We also applied two different types of *cleanmask*, the shallower one in steps 1 to 3 and the deeper one in steps 4 to 8." (2.2 High-resolution ALMA continuum image)
- multiscale scales: _not stated_
- continuum subtraction: cleanest continuum images using only line-free channels (ALMA-IMF)  
  > "We use `cleanest` continuum images, which use only the line-free channels, in this study." (2.1 ALMA-IMF continuum images and core catalog)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA-IMF continuum model image used as tclean startmodel to supply short-baseline flux  
  > "we used the ALMA-IMF continuum model image as *startmodel* to complement the flux from the short baseline." (2.2 High-resolution ALMA continuum image)
- smoothing: 1.3 mm image convolved to the 3 mm beam (common beam) for spectral index and surface brightness  
  > "This means that only the $1.3\,{\rm mm}$ continuum image needs to be convolved with the common beam." (3.2 Spectral indices)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Detailed ALMA-IMF continuum data processing  
  > "The detailed data processing of the continuum image is described in (cite: motte22) and (cite: ginsburg22)." (2.1 ALMA-IMF continuum images and core catalog) [from (cite: motte22); (cite: ginsburg22)]
- Details of the 1.3 mm high-resolution observations  
  > "The details about the observation in $1.3\,{\rm mm}$ can be found in (cite: goddi20)." (2.2 High-resolution ALMA continuum image) [from (cite: goddi20)]
- Core extraction and selection criteria (S/N, ellipticity, free-ff removal)  
  > "We adopt the selection criteria described in (cite: menshchikov21) and (cite: pouteau22) to filter out sources with low signal-to-noise and high ellipticity in each band." (2.1 ALMA-IMF continuum images and core catalog) [from (cite: menshchikov21); (cite: pouteau22); (cite: louvet24)]
- MBB model of optically thick core plus optically thin envelope  
  > "Following (cite: budaiev24), who analyzed similar-resolution data of the Sgr B2 region in the same ALMA bands" (3.5 Temperature constraints through modified blackbody model) [from (cite: budaiev24)]
- Jeans analysis (Jeans number and efficiency)  
  > "Following the description in (cite: pokhrel18), we measured Jeans masses of cores using the equation (cite: binney87)" (5.1 Jeans analysis) [from (cite: pokhrel18)]
- Completeness test by synthetic source injection  
  > "as it was done in the ALMA-IMF project (cite: pouteau22)" (8 The completeness test) [from (cite: pouteau22)]

### Not stated but needed to reproduce (our reading)

- Exact tclean image size, cell size, deconvolver and niter for the self-calibrated images
- Self-calibration solution intervals and gain types per stage
- Which line-free channels were used for the high-resolution continuum
- Flux calibration/scale adopted for the high-res datasets
- Exact cutout size and fitting window used in TGIF
- Percentile/threshold definitions of the robust measurement criteria in the core catalog
- linmix setup (priors, chain length) beyond '100 MCMC'
- Dendrogram rms sigma values per image
- Details for Fisher/KS/Spearman tests beyond stated p-values

## Analysis recipe

1. **Self-calibrate and image high-resolution continuum**: Eight stages of iterative phase self-calibration with tclean using ALMA-IMF model as startmodel  
  > "start eight stages of iterative phase self-calibration process with `tclean`, `gaincal`, and `applycal`." (2.2 High-resolution ALMA continuum image)
   - software: CASA
   - parameter: threshold 1.3 mm: [0.2,0.2,0.15,0.15,0.15,0.15,0.1,0.1] mJy; 3 mm: [0.1,0.075x7] mJy; robust=0  
  > "*threshold*=\[0.2, 0.2, 0.15, 0.15, 0.15, 0.15, 0.1, 0.1\]$\,{\rm mJy}$ for $1.3\,{\rm mm}$" (2.2 High-resolution ALMA continuum image)
   - fitting: _not stated_
   - validation: Visual evaluation of final image quality, parameters tweaked from experiments  
  > "We visually evaluated the quality of the final image produced by self-calibration and tweaked parameters to find the optimal set." (2.2 High-resolution ALMA continuum image)
2. **Identify compact high-res sources**: Visual selection by three coauthors (compact, centrally peaked, significant, independent) confirmed with dendrogram  
  > "To minimize the ambiguity, only the sources identified by more than two of the three coauthors are included into the final catalog." (3.1 High-res sources identification)
   - software: astrodendro
   - parameter: min_value=3sigma, min_delta=1.5sigma, min_npix=15  
  > "*min_value*=$3\sigma$, *min_delta*=$1.5\sigma$, *min_npix*=15" (3.1 High-res sources identification)
   - fitting: _not stated_
   - validation: Completeness test with injected 2D Gaussian sources  
  > "The completeness level is defined as the fraction of synthetic sources identified in the `dendrogram` with the same parameters used in finding our PPO samples." (8 The completeness test)
3. **Measure integrated flux and sizes with 2D Gaussians**: TGIF: sub-pixel peak adjustment, 2D Gaussian chi-square fit with penalty on negative residuals, local annulus background subtraction, refit  
  > "The modeling process consists of three steps: sub-pixel offset adjustment, local background noise estimation, and the flux measurement from the 2D Gaussian model." (7 PPO Flux measurement with a 2D Gaussian model)
   - software: TGIF, LMFIT, scipy, radio_beam
   - parameter: penalty factor lambda=100; background annulus 2x and 3x FWHM  
  > "$\lambda=100$ is a penalty factor" (7 PPO Flux measurement with a 2D Gaussian model)
   - assumption: Source radius encloses 95% of flux, equal to FWHM/sqrt(2 ln 2) for Gaussian  
  > "the disk radius is equivalent to $1/(\sqrt{2\ln(2)}) \times {\rm FWHM}$ of the Gaussian model" (3.3 Sizes)
   - fitting: Linear chi-square minimization with LMFIT  
  > "We use the linear chi-square method to minimize the residual function defined as the difference between the image and the 2D Gaussian model." (7 PPO Flux measurement with a 2D Gaussian model)
   - validation: _not stated_
4. **Spectral indices from peak fluxes**: Peak fluxes at 3 mm and 1.3 mm convolved to common (3 mm) beam; alpha = log(F3/F1.3)/log(nu3/nu1.3); classify dust-dominated (>2), 1.5-2, <1.5  
  > "We measured a spectral index using Eq. [\[eq:alpha\]](#eq:alpha) with the peak flux, which is the brightest pixel value, rather than the integrated flux." (3.2 Spectral indices)
   - software: astropy, radio_beam
   - assumption: Central frequencies computed assuming alpha=2 power law  
  > "When we assume a power-law slope, $\alpha=2$, we obtain the central frequencies" (3.2 Spectral indices)
   - fitting: _not stated_
   - validation: Calibration error propagation (10%/5%) to test group membership  
  > "the number of dust-dominated sources could vary between 54 and 62 in W51-E and between 10 and 15 in W51-IRS2." (3.2 Spectral indices)
5. **Dust temperature and mass lower limits of PPOs**: Grid MBB model (optically thick core plus optically thin envelope) for T; optically thin mass at fixed T=40 K (100/300 K for hot cores) from 3 mm flux  
  > "To constrain the PPO masses, we adopt $40\,{\rm K}$ dust temperature." (3.6 Constraints to PPO masses)
   - parameter: Sigma=1e21-1e27 g cm^-2 and T=5-400 K grid  
  > "$\Sigma=10^{21}$–$10^{27}\,{\rm g\,cm^{-2}}$ and $T=5$–$400\,{\rm K}$" (3.5 Temperature constraints through modified blackbody model)
   - assumption: Ossenkopf & Henning dust opacity; d=5.4 kpc; optically thin dust for mass  
  > "the dust mass can be inferred by assuming optically thin dust emission (cite: hildebrand83)" (3.6 Constraints to PPO masses)
   - fitting: _not stated_
   - validation: _not stated_
6. **Associate PPOs with cores and measure fragment numbers**: PPO within core boundary (core FWHM extended by the ALMA-IMF beam); count fragments; fit log Mcore vs Nfrag; Spearman correlations  
  > "The core boundary is defined as core FWHM extended slightly further by the size of the ALMA-IMF beam." (4.1 Overview of fragmentation)
   - software: linmix
   - fitting: linmix, 100 MCMC runs for each region  
  > "We utilized the Python package `linmix` (cite: kelly07) to run 100 MCMC for W51-E and W51-IRS2 data, respectively." (4.2.1 Cores with high fragment numbers are preferentially massive)
   - validation: Spearman p-values, residual-flux test  
  > "p-values are still low ($<0.05$), indicating that the trend is not an output of the interdependence of cores and fragment fluxes." (4.2.1 Cores with high fragment numbers are preferentially massive)
7. **Jeans analysis**: Thermal Jeans mass from core density and PPMAP temperature; Jeans number and efficiency eps_J = Nfrag/NJ; compare PPO masses with Jeans masses  
  > "We also measure the Jeans efficiency, representing the ratio of actual fragments to the Jeans number ($\epsilon_J\equiv N_{\rm frag}/N_J$)." (5.1 Jeans analysis)
   - assumption: Only thermal pressure considered  
  > "We note that only thermal pressure is considered in the analysis." (5.1 Jeans analysis)
   - fitting: _not stated_
   - validation: Compared with Perseus (Pokhrel18) and Tang22  
  > "Since we followed the Jeans analysis in (cite: pokhrel18), we can directly compare our results with the Perseus region" (5.1.1 Comparison to other studies)
8. **Compare unfragmented and fragmented cores and core-independent PPOs**: Two-sample KS tests on size, mass, density, temperature, flux  
  > "We evaluate the p-value from the two-population KS test, $3.18\times10^{-3}$, $8.25\times10^{-4}$, and $1.09\times10^{-6}$ for size, mass, and mass density, respectively." (5.2 Unfragmented/fragmented cores)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.7.0: data reduction, self-calibration and imaging  
  > "The data reduction and self-calibration were conducted by the Common Astronomy Software Applications (CASA) package ((cite: mcmullin07); version 5.7.0)." (2.2 High-resolution ALMA continuum image)
- **astrodendro** : dendrogram source significance check  
  > "we used a watershed-based algorithm (`dendrogram`[^1]; (cite: rosolowsky08))" (3.1 High-res sources identification)
- **TGIF** : 2D Gaussian flux and size measurement  
  > "We use the FWHM of the major axis of the Gaussian model produced by our fitting method, `TGIF`" (3.3 Sizes)
- **radio_beam** : common beam and deconvolution  
  > "the common beam size is calculated by `radio_beam`" (3.2 Spectral indices)
- **astropy** : image convolution  
  > "The convolution of the image was conducted with the `astropy` Python package" (3.2 Spectral indices)
- **lifelines** : Kaplan-Meier survival analysis of size distribution  
  > "We perform survival analysis with the Kaplan-Meier estimator implemented in the Python package `lifelines`" (3.3 Sizes)
- **linmix** : linear MCMC fit of log Mcore vs Nfrag  
  > "We utilized the Python package `linmix` (cite: kelly07) to run 100 MCMC" (4.2.1 Cores with high fragment numbers are preferentially massive)
- **LMFIT** : optimizing 2D Gaussian model  
  > "We utilize the minimizer tool `LMFIT` (cite: lmfit) to optimize the 2D Gaussian model." (7 PPO Flux measurement with a 2D Gaussian model)
- **scipy** : curve_fit for 1D Gaussian peak refinement  
  > "we utilized `curve_fit` of `scipy` (cite: scipy20) Python package" (7 PPO Flux measurement with a 2D Gaussian model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of high-res sources in W51-E | 118 | not stated | sources | 2 | As a result, we identified 118 high-res sources in W51-E |
| Number of high-res sources in W51-IRS2 | 93 | not stated | sources | 2 | For W51-IRS2, out of 93 high-res sources, we have 23 matched sources |
| Cores with fragments, W51-E | 15 of 20 | not stated | cores | 6 | In W51-E and W51-IRS2, 15/20 and 41/87 cores have fragments, respectively. |
| Cores with fragments, W51-IRS2 | 41 of 87 | not stated | cores | 6 | In W51-E and W51-IRS2, 15/20 and 41/87 cores have fragments, respectively. |
| Spearman coefficient, log 1.3mm core flux vs Nfrag (W51-E) | 0.733 (p=2.37e-4) | not stated | dimensionless | 6 | are 0.733 (p-value=$2.37\times10^{-4}$) and 0.466 (p-value=$5.42\times10^{-6}$) at $1.3\,{\rm mm}$ |
| Spearman coefficient, log 1.3mm core flux vs Nfrag (W51-IRS2) | 0.466 (p=5.42e-6) | not stated | dimensionless | 6 | are 0.733 (p-value=$2.37\times10^{-4}$) and 0.466 (p-value=$5.42\times10^{-6}$) at $1.3\,{\rm mm}$ |
| linmix slope/intercept log Mcore-Nfrag | W51-E 2.55, -1.18; W51-IRS2 1.46, -0.18 | 1sigma slope 1.85-3.16 (E), 1.23-1.68 (IRS2) | dimensionless | 6 | We obtain the medians of slopes and intercepts, 1.46 and -0.18 in W51-IRS2, and 2.55 and -1.18 in W51-E. |
| Dust-dominated cross-matched PPOs | 59 (W51-E), 13 (W51-IRS2) | 54-62 (E), 10-15 (IRS2) with calibration errors | sources | 4 | a) dust-dominated / 59 / 13 |
| PPO mass lower limits range | 0.1-200 | not stated | Msun | 5 | The mass lower limits from the constant temperature model span $\sim0.1$–$200\,M_\odot$. |
| MBB dust temperature range | 5-60 | not stated | K | 5 | The inferred dust temperature from MBB is distributed over $5$–$60\,{\rm K}$ |
| Mean Jeans efficiency | 0.05 (W51-E), 0.20 (W51-IRS2) | not stated | dimensionless | 7 | The average Jeans efficiency is estimated to be 0.05 and 0.20 in W51-E and W51-IRS2, respectively |
| Thermal Jeans masses of cores | ~0.2-6 | not stated | Msun | 7 | Thermal Jeans masses of cores measured from Eq. [\[eq:Jeans\]](#eq:Jeans) have a range of $\sim0.2$–$6\,M_\odot$ |
| Completeness limits at 3 mm | 0.25 mJy (W51-E), 0.20 mJy (W51-IRS2) | not stated | mJy | 2 | we obtain the completeness limits of W51-E and W51-IRS2, $0.25\,{\rm mJy}$ and $0.20\,{\rm mJy}$, respectively, in Band 3 |
| KS p-values unfragmented vs fragmented cores (size, mass, density), W51-IRS2 | 3.18e-3, 8.25e-4, 1.09e-6 | not stated | dimensionless | 8 | $3.18\times10^{-3}$, $8.25\times10^{-4}$, and $1.09\times10^{-6}$ for size, mass, and mass density, respectively. |

## Qualitative findings

- High-res sources are pre/protostellar objects (PPOs): prestellar dust or dust disks/envelopes around protostars.  
  > "We will use the term “pre/protostellar objects (PPOs)" to refer to the high-res sources." (3.4 Classification of high-res sources: Pre/Protostellar objects (PPOs))
- Fragmented cores are smaller, more massive and denser than unfragmented cores in W51-IRS2.  
  > "We find that the fragmented cores are systematically smaller in size, more massive, and denser than the unfragmented cores." (6.1 Summary)

## Claim tuples

- H: Does the number of fragments depend on core mass? | E: Associated PPOs with ALMA-IMF cores and correlated Nfrag with core flux/mass | R: Positive Spearman correlations; all multi-fragment cores >~4 Msun | F: Massive cores host more PPOs | **supported**
- H: Is thermal Jeans fragmentation sufficient to explain fragment masses/numbers? | E: Computed Jeans numbers/efficiencies and compared PPO masses with parent-core Jeans masses | R: Mean Jeans efficiency 0.05 and 0.20; fragment masses up to ~20x Jeans mass | F: Thermal Jeans masses insufficient, more so at high core mass | **supported**
- H: Do bright PPOs form preferentially in massive cores? | E: Compared brightest-PPO flux with core flux | R: Clear correlation in both regions and bands | F: Bright (possibly massive) PPOs reside in bright cores | **supported**
- H: Does protostellar heating suppress fragmentation in massive cores? | E: Compared fragmentation efficiency with brightest PPO flux, Fisher's exact test | R: Fisher p-values 1.0 and 0.27 | F: Suggestive trend only, not statistically significant (N=4) | **partially**
- H: Do unfragmented cores differ from fragmented cores? | E: KS tests on temperature, size, mass, density in W51-IRS2 | R: Unfragmented are larger, less massive, less dense | F: Statistically distinct populations | **supported**

## Reasoning

- Why this data: Combine ALMA-IMF core-scale images with long-baseline high-resolution images to link cores and compact fragments  
  > "By spatially associating high-res sources with cores found in low-resolution ALMA-IMF images in W51, we will see how each ALMA-IMF core fragments in a high-mass star-forming region." (1 Introduction)
- Why this method: T=40 K chosen because recent YSO models show it recovers true mass better than 20 K  
  > "This is motivated by the recent YSO model study that demonstrated that the choice of dust temperature $T=40\,{\rm K}$, warmer than the commonly adopted temperature $T=20\,{\rm K}$" (3.6 Constraints to PPO masses)
- Alternative: Fourth core group (robust 1.3 and 3 mm within 1.3 mm FOV) not used since no analysis requires it  
  > "is not used in this study because no analyses require this sample." (2.1 ALMA-IMF continuum images and core catalog)
- How they decided it was enough: _not stated_
- Limitation (authors): PPO masses are lower limits owing to optically thick emission; no PPO mass function attempted  
  > "Therefore, we will not attempt to build a PPO mass function in this paper." (3.6 Constraints to PPO masses)
- Limitation (authors): Heating-suppression trend relies on tiny samples  
  > "we cannot rule out that this trend is due to the low number of samples ($N=4$)" (4.3 Fragmentation efficiency and thermal suppression of fragmentation)
- Caveat (inferred, ours): Visual source identification by three coauthors is subjective and dendrogram parameters strongly change fragment counts (cf. Tang22 comparison)
- Caveat (inferred, ours): Core temperatures from 2.5" PPMAP may be mismatched to ~1" core size
- Caveat (inferred, ours): Fixed T=40 K and optically thick emission make masses and Jeans comparisons uncertain
- Caveat (inferred, ours): Core mass uses different opacity than ALMA-IMF catalog (factor ~1.3)
- Caveat (inferred, ours): Small-number statistics in W51-E unfragmented sample

## Reproducibility

- Data public (paper): Archival ALMA data; PPO catalog on Zenodo  
  > "The full machine-readable form of the catalogs is available at <https://zenodo.org/records/16235156>." (9 PPO catalog)
- Products in archive: _not stated_
- Code: TGIF code on GitHub and Zenodo  
  > "The source code of TGIF can be found at Github page (<https://github.com/tyoo37/TGIF>) and Zenodo (<https://zenodo.org/records/13973837>)." (7 PPO Flux measurement with a 2D Gaussian model)
- Missing: Full tclean image parameters and self-cal solints
- Missing: ALMA-IMF core catalog (Louvet+24) needed as external input
- Missing: Dendrogram rms values
- Missing: Exact selection of cleanmasks
- Data volume (inferred): ~100s of GB (long-baseline Band 3 and 6 12 m datasets of two fields plus ALMA-IMF images)
- Score (inferred): 3/5, Data public and catalog/code released, but self-calibration and imaging details are incomplete and core catalog is external.
- Rediscovery candidate: no, Recipe depends on visual source selection, self-calibration details not fully given, and external core catalog.

## Links

- Method: (cite: motte22) (ALMA-IMF survey description and data processing)
- Method: (cite: ginsburg22) (ALMA-IMF data reduction)
- Method: (cite: louvet24) (ALMA-IMF core catalog and masses)
- Method: (cite: pokhrel18) (Jeans analysis methodology)
- Method: (cite: budaiev24) (MBB model and spectral-index interpretation)
- Method: (cite: tgif) (2D Gaussian fitting code)
- Companion: (cite: goddi20) (1.3 mm high-resolution W51 observations and massive YSOs)
- Companion: (cite: tang22) (Previous fragmentation/Jeans study of W51-IRS2)
- Related: ALMA-IMF

## Checks

```json
{
 "quotes": 95,
 "quotes_ok": 95,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 72,
  "rate": 0.699
 },
 "evidence_ok": true
}
```
