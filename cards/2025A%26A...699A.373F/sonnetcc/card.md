# Inner disc and circumplanetary material in the PDS 70 system: Insights from multi-epoch, multi-frequency ALMA observations

`2025A&A...699A.373F` | Astronomy and Astrophysics 2025 | first author: Fasano, D. | arXiv: 2506.11709 | DOI: 10.1051/0004-6361/202554959

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Is compact circumplanetary dust re-detected around PDS 70 c (and b) in independent Band 6 and 7 datasets from 2019, 2021 and 2023, does it move with the planet, and is it variable?  
  > "to detect circumplanetary material in independent datasets taken at different epochs in 2019, 2021 and 2023 and assess its possible motion" (abstract)
- Target **PDS 70**: coordinates _not stated_; z/distance 112.4 pc  
  > "PDS 70 is a T Tauri star situated in the Upper Centaurus Lupus association (cite: Pecaut_Mamajek_2016), at a distance of $112.4~\rm pc$ (cite: Gaia_2021)" (Introduction); distance from Gaia (cite: Gaia_2021)  
  > "PDS 70 is a T Tauri star situated in the Upper Centaurus Lupus association (cite: Pecaut_Mamajek_2016), at a distance of $112.4~\rm pc$ (cite: Gaia_2021)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00888.S, 2018.A.00030.S, 2018.1.01774.S, 2019.1.01138.S, 2019.1.01619.S, 2021.1.00782.S, 2022.1.01695.S
- bands: Band 6 (220-260 GHz) and Band 7 (345-355 GHz)  
  > "Band 6 ($220-260~\rm GHz$)" (Conclusions)
- frequencies and spectral setup: B6 2021 LF median 220 GHz; B6 2021 HF median 260 GHz  
  > "with a median frequency of 220 GHz with LB data taken in July 2021 and SB data taken in March 2020" (2 Observations); "corresponding to a median frequency of 260 GHz, with LB data taken in June 2021 and SB data taken in March 2020" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Fiducial images (mas): B7 2019 52x45; B7 2021 60x45; B7 2023 72x62; B6 2021 LF 115x89; B6 2021 HF 110x79  
  > "Our fiducial images have the following resolutions (in mas): B7 2019, 52x45; B7 2021, 60x45; B7 2023, 72x62; B6 2021 LF, 115x89; B6 2021 HF, 110x79" (3 Methods)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: B7 2019: LB 2019, SB 2016; B7 2021: July and August 2021; B7 2023: March (SB) and June (LB) 2023; B6: SB March 2020, LB June/July 2021  
  > "B7 2019 uses LB data taken in 2019 and short baselines taken in 2016. B7 2021 combines SB and LB data taken in July and August 2021." (2 Observations); "B7 2023 includes SB and LB data taken in March and June 2023, respectively." (2 Observations)
- pi or archival as stated: archival data from multiple ALMA programs  
  > "We calibrate and analyse archival Atacama Large Millimetre/subMillimetre Array (ALMA) Band 6 and 7 observations of PDS 70" (abstract); "This work makes use of multiple datasets from different ALMA programs" (2 Observations)
- Other facility **HST and MagAO-X (literature Halpha detections)**: Published multi-epoch Halpha fluxes of PDS 70 c compared with the ALMA peak intensities  
  > "In Fig. [5](#fig:Variability) we compare the normalised fluxes reported in (cite: Zhou_2021; Zhou_2025; Close_2025) with the normalised peak intensities of $c_{\rm smm}$ we measure in our ALMA images." (5.2 c_smm variability)
- External data: Dust opacity 3.63 cm2/g (1 mm grains) and 0.79 cm2/g (1 micron grains)  
  > "In the former case we assume a typical dust opacity of $3.63~\rm cm^2g^{-1}$ (cite: Birnstiel_2018)." (4 Results); "Otherwise, we consider a dust opacity of $0.79~\rm cm^2g^{-1}$ (cite: Birnstiel_2018)" (4 Results) [from (cite: Birnstiel_2018)]
- External data: Temperature T=26 K for the circumplanetary material and T=22 K for the inner disc  
  > "We assume a temperature of $T=26~\rm K$, considering the contribution of viscous heating and irradiation from the accreting star and planet (cite: Benisty_2021)" (4 Results); "considering an average temperature of $T=22\rm~K$ from the model used in (cite: Benisty_2021)" (4 Results) [from (cite: Benisty_2021)]
- External data: Expected planet positions from the orbital fitting tool (whereistheplanet)  
  > "We compute the expected position of both PDS 70 b and c using the orbital fitting tool[^3] presented in (cite: Wang_2021)" (5.1 c_smm astrometry) [from (cite: Wang_2021)]
- External data: Stellar mass 0.8 Msun and age 5.4 Myr  
  > "With a mass of $0.8~M_\ensuremath{\odot}$ and an age of $5.4~\rm Myr$ (cite: Muller_2018)" (Introduction) [from (cite: Muller_2018)]
- External data: Distance of 112.4 pc  
  > "at a distance of $112.4~\rm pc$ (cite: Gaia_2021)" (Introduction) [from (cite: Gaia_2021)]
- External data: Inner-disc clump positions at 2017 and 2019 epochs  
  > "(cite: Casassus_2022) report two clumps in the inner disc at $0.03-0.04~\rm arcsec$ (Clump 1) and $0.08~\rm arcsec$ (Clump 2) at two different epochs (2017 and 2019)." (4 Results) [from (cite: Casassus_2022)]
- External data: Predicted spectral indices of alpha_D=3.2 and alpha_ID=3.6 from dust evolution models  
  > "predicted spectral indices of $\alpha_{\rm mm}^{\rm D}=3.2$ and $\alpha_{\rm mm}^{\rm ID}=3.6$ for the entire disc and the inner disc, respectively" (5.3 Spectral Index) [from (cite: Pinilla_2024)]

## Processing

### Calibration

- pipeline or manual: Iterative self-calibration following the exoALMA pipeline for 2018.1.01774.S and 2021.1.00782.S; other programs calibrated as in earlier papers  
  > "For data from 2018.1.01774.S; 2021.1.00782.S, we followed the iterative self-calibration following the exoALMA pipeline (cite: Loomis_2025)" (2 Observations)
- casa version: CASA 6.2.1.7  
  > "We performed the calibration using the version 6.2.1.7 of the CASA software (cite: CASA_2022)." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% ALMA flux calibration error for Band 6 and 7  
  > "adding in quadrature the RMS noise of the image together with the $10\%$ ALMA flux calibration error for Band 6 and 7" (3 Methods)
- self calibration: Phase-only rounds with solution intervals shortened from EB-long to 30s, then amplitude and phase with EB-long interval (2018.1.01774.S/2021.1.00782.S); 2019.1.01138.S combined with 2018.1.01774.S with phase-only down to 18s then two amplitude+phase rounds (EB-long, scan-long)  
  > "four rounds of phase-only self-calibration were executed with the solution intervals of EB-long, 360s, 120s, and 60s" (2 Observations); "amplitude and phase self-calibration were performed with an EB-long solution interval" (2 Observations); "The first round used EB-long solution intervals, while the second used scan-long intervals." (2 Observations)

### Imaging

- task: tclean in CASA  
  > "We image the data, the best fit `galario` model and the residuals for each dataset using the `tclean()` task of the CASA software" (3 Methods)
- deconvolver: _not stated_
- weighting robust: robust = 1.0 (B7 2019, B7 2021); robust = 0.0 (B7 2023, B6 2021 LF, B6 2021 HF)  
  > "using a robust parameter of 1.0 (B7 2019, B7 2021) and 0.0 (B7 2023, B6 2021 LF, B6 2021 HF), chosen to provide the best balance between resolution and sensitivity" (3 Methods)
- uv taper: uv-taper applied to Band 7 data to reach Band 6 resolution before Gaussian smoothing (value not given)  
  > "we CLEAN the Band 7 datasets using an $uv$-taper to reach a similar resolution before applying the Gaussian smoothing" (Footnote 5)
- cell size: 0.01 arcsec (Band 7), 0.02 arcsec (Band 6)  
  > "produce $1024\times1024$ pixels images with a pixel size of" (3 Methods)
- image size: 1024x1024 pixels (Band 7), 512x512 pixels (Band 6)  
  > "produce $1024\times1024$ pixels images with a pixel size of" (3 Methods)
- masking: Tailored masks around 3 sigma contours of outer ring, inner disc and compact emission at PDS 70 c; CLEAN down to 1 sigma with gain 0.02  
  > "we create tailored masks for each image around the $3\sigma$ contours of the outer ring, inner disc and the compact emission co-located with PDS 70 c" (3 Methods)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Spectral regions covering the listed lines flagged and remaining channels averaged (no channel ranges given)  
  > "were flagged and the remaining channels were averaged" (2 Observations)
- primary beam correction: _not stated_
- array combination: Short- and long-baseline EBs combined per block (e.g. B7 2021 combines SB and LB data)  
  > "B7 2021 combines SB and LB data taken in July and August 2021." (2 Observations)
- smoothing: imsmooth to the B7 2023 resolution (Band 7 comparison) or the B6 2021 LF resolution (spectral index)  
  > "we first use the task `imsmooth` of the CASA software to convolve the images with a Gaussian beam to the resolution of the B7 2023 images" (4 Results)
- final beam: B7 2019 52x45 mas; B7 2021 60x45; B7 2023 72x62; B6 2021 LF 115x89; B6 2021 HF 110x79  
  > "B7 2019, 52x45; B7 2021, 60x45; B7 2023, 72x62; B6 2021 LF, 115x89; B6 2021 HF, 110x79" (3 Methods)
- final rms: _not stated_

### Inherited from earlier work

- Calibration of 2015.1.00888.S and 2018.A.00030.S (B7 2019) and of 2022.1.01695.S  
  > "The calibration of data from 2015.1.00888.S and 2018.A.00030.S to build B7 2019 is described in (cite: Benisty_2021), and for 2022.1.01695.S in (cite: Rampinelli_2025)." (2 Observations) [from (cite: Benisty_2021); (cite: Rampinelli_2025)]
- Calibration of all Band 6 datasets  
  > "For the Band 6 datasets, the calibration procedures are detailed in (cite: Facchini2021), (cite: Law2024), and (cite: Rampinelli_2024)." (2 Observations) [from (cite: Facchini2021); (cite: Law2024); (cite: Rampinelli_2024)]
- Self-calibration and EB alignment procedure  
  > "They were then all aligned using the exoALMA alignment procedure (cite: Loomis_2025), with the B7 2023 dataset serving as the reference." (2 Observations) [from (cite: Loomis_2025)]
- Spectral-line flagging for 2019.1.01138.S  
  > "spectral lines in the Band 7 frequency range were flagged (cite: Rampinelli_2025)" (2 Observations) [from (cite: Rampinelli_2025)]
- Flux-density uncertainty from random-location apertures  
  > "according to the procedure presented in (cite: Rampinelli_2024)" (3 Methods) [from (cite: Rampinelli_2024)]
- Dust mass estimate approach  
  > "We follow the same approach of (cite: Benisty_2021) to estimate the dust mass of" (4 Results) [from (cite: Benisty_2021)]

### Not stated but needed to reproduce (our reading)

- Exact exoALMA pipeline scripts/version and alignment parameters used for each block
- Self-calibration solution intervals and spectral-window handling for the Band 6 datasets and for 2022.1.01695.S (only given by reference)
- Channel ranges of line-free data and the species names of the flagged lines
- tclean niter, threshold in Jy, deconvolver and mask definitions per image
- uv-taper value used to degrade Band 7 to Band 6 resolution
- Number and size of random apertures used for flux-density noise
- galario settings (grid size, image resolution) and how model visibilities were weighted
- Region definition and starting guesses for the imfit Gaussian fits
- Inputs to the whereistheplanet orbital solution
- Number of walkers for the Bayesian variability test (text says 100 steps and 4000 steps)

## Analysis recipe

1. **Calibrate, self-calibrate and align EBs into epoch blocks**: Phase-only then amplitude and phase self-calibration following exoALMA pipeline; EBs aligned onto a common uv-grid; blocks B7 2019, 2021, 2023 and B6 2021 LF/HF built; data averaged to one channel per spw and 30s bins  
  > "Finally, all datasets were averaged to one channel per spectral window and binned into 30s time intervals." (2 Observations); "that regrids the EBs onto a common *uv*-grid with natural weighting, retaining only overlapping grid cells and applying phase shifts to minimize visibility differences" (2 Observations)
   - software: CASA 6.2.1.7
   - parameter: EBs with >4% total flux deviation rescaled to the highest-SNR short-baseline EB  
  > "The EBs with $>4\%$ total flux deviation were rescaled to the total flux measured in a short-baseline EB with the highest signal-to-noise ratio." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit the outer-disc continuum in the visibility plane**: 2D parametric model of two Gaussian rings plus a Gaussian arc, fit with galario and emcee to each dataset  
  > "We consider two Gaussian components to model the outer ring in order to replicate the inner shoulder seen in the observations, while we use the arc to reproduce the overdensity in the North West of the ring." (3 Methods)
   - software: galario, emcee
   - parameter: Preliminary run 100 walkers ~10^3 steps; fiducial run 250 walkers and 10^4 steps; first 25% discarded as burn-in  
  > "For each dataset we set up 250 walkers and $10^4$ steps. We discard the first $25\%$ steps as burn-in." (3 Methods)
   - fitting: emcee with uniform priors; parameters sampled linearly except f1, f2, f1a (logarithmic); priors listed in Appendix  
  > "using uniform priors, sampling all the parameters linearly with the exception of $f_1$, $f_2$ and $f_1^a$, which are sampled logarithmically" (3 Methods)
   - validation: Test run on B7 2019 with an added central Gaussian gave best-fit parameters within 1 sigma of the fiducial run  
  > "We check that the resulting bestfit parameters are within $1\sigma$ uncertainties of those obtained in our fiducial run" (3 Methods)
3. **Subtract the model and image residuals**: Best-fit galario model evaluated at the observed uv points subtracted from the data; data, model and residuals imaged with tclean  
  > "We then subtract the best fit `galario` model evaluated at the same $uv$ points of the observations from the observed data in order to obtain the residuals." (3 Methods)
   - software: CASA tclean, galario
   - parameter: robust 1.0 (B7 2019, 2021) and 0.0 (others); CLEAN down to 1 sigma with gain 0.02  
  > "CLEAN the images down to $1\sigma$ using a very conservative" (3 Methods)
   - assumption: Subtraction uncertainties dominated by ALMA flux uncertainties  
  > "We assume that the uncertainties introduced with this subtraction are dominated by the ALMA flux uncertainties" (3 Methods)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure compact emission at PDS 70 c and test variability**: Peak intensity measured in images smoothed to the B7 2023 beam; epoch differences computed; Bayesian test with emcee for a constant flux F0 plus excess noise sigma0  
  > "We additionally perform a Bayesian test using `emcee`, assuming that the peak intensity of $c_{\rm smm}$ is a constant value $F_0$ across the three epochs and considering the presence of an excess noise $\sigma_0$" (4 Results)
   - software: CASA imsmooth, emcee
   - parameter: Priors F0 in [90,200] uJy/beam (linear) and log10 sigma0 in [log10 1, log10 1000]  
  > "sampling $F_0$ linearly and $\sigma_0$ logarithmically, with priors of $[90, 200]~\rm\mu Jy/beam$ and $\rm[log_{10}1,log_{10}1000]$, respectively" (4 Results)
   - assumption: Peak intensity used because the emission is unresolved  
  > "using the peak intensity as the emission is unresolved" (4 Results)
   - fitting: emcee; variability would show as non-zero sigma0  
  > "If our measurements are compatible with a constant flux, we expect to find $\sigma_0=0$" (4 Results)
   - validation: Smoothed-image peaks agree within 1 sigma with fiducial-image values  
  > "within $1\sigma$ error bars of the estimates from our fiducial images" (4 Results)
5. **Derive dust masses of c_smm and the inner disc**: Optically thin M = d^2 F / (kappa B(T)) with F integrated in an ellipse of twice the beam axes; inner disc uses an elliptical 3 sigma mask from B7 2023 (B6 2021 HF for Band 6)  
  > "We compute the integrated flux density $F_\nu$ inside an elliptical area with twice the beam semi-major and semi-minor axes centred on the brightest pixel." (4 Results); "we create a single elliptical mask covering the $3\sigma$ emission of the inner disc in B7 2023 and apply it to all the Band 7 datasets" (4 Results)
   - parameter: kappa = 3.63 cm2/g (1 mm grains), 0.79 cm2/g (1 micron grains)  
  > "Otherwise, we consider a dust opacity of $0.79~\rm cm^2g^{-1}$ (cite: Birnstiel_2018)" (4 Results)
   - assumption: Optically thin emission; T=26 K (c_smm) and T=22 K (inner disc); 1 mm or 1 micron grains  
  > "Assuming that the emission is optically thin, the dust mass can be estimated following (cite: Hildebrand_1983):" (4 Results); "We assume a temperature of $T=26~\rm K$, considering the contribution of viscous heating and irradiation from the accreting star and planet" (4 Results)
   - fitting: _not stated_
   - validation: Masses compared with Benisty et al. (2021) values  
  > "Our estimates are consistent with the range $0.08-0.36~M_\oplus$ reported in (cite: Benisty_2021)" (4 Results)
6. **Measure c_smm astrometry between Band 7 epochs**: Gaussian fit to CLEANed residual images with imfit; positions relative to the galario disc centre; compared with predicted planet c positions  
  > "we fit a Gaussian to the CLEANed residual images in the region around $c_{\rm smm}$ using the CASA task `imfit`" (5.1 c_smm astrometry)
   - software: CASA imfit, whereistheplanet
   - parameter: Position uncertainty = 1 mas alignment term plus theta_FWHM/SNR/0.9 in quadrature  
  > "which can be computed as $\theta\rm _{FWHM}/SNR/0.9$" (5.1 c_smm astrometry)
   - assumption: Disc centre from galario coincides with the star position  
  > "By doing so we assume that the centre fitted with `galario` coincides with the location of the star." (5.1 c_smm astrometry)
   - fitting: _not stated_
   - validation: Displacement compared with the orbital solution of planet c and with Halpha detections  
  > "with the peak intensity moving compatibly to the orbital solution of planet c by (cite: Wang_2021)" (5.1 c_smm astrometry)
7. **Fit spectral indices**: Fit log F = alpha log nu + log F0 to all datasets simultaneously with scipy curve_fit for the entire disc, inner disc and c_smm; per-epoch two-point indices for c_smm  
  > "We then estimate the spectral index for each region using all the datasets simultaneously by fitting Eq. [\[eq:spix general\]](#eq:spix general) with the `curve_fit` function of the `scipy` module" (5.3 Spectral Index)
   - software: scipy curve_fit, CASA imsmooth
   - parameter: For c_smm, images smoothed to B6 2021 LF resolution; Band 7 CLEANed with uv-taper first  
  > "we use the task `imsmooth` of the CASA software to smooth our fiducial images with a Gaussian beam to the same resolution of the B6 2021 LF dataset" (5.3 Spectral Index)
   - assumption: Thermal dust emission, self-scattering neglected; alpha=2 if optically thick, alpha=beta+2 if optically thin  
  > "Assuming that the emission is caused entirely by thermal emission from dust and neglecting self-scattering (cite: Zhu_2019), there are two possible scenarios." (5.3 Spectral Index)
   - fitting: _not stated_
   - validation: Compared with predicted indices of Pinilla et al. (2024)  
  > "that are within $1\sigma$ error bars of our measurements" (5.3 Spectral Index)

## Software

- **CASA** 6.2.1.7: Calibration, tclean imaging, imsmooth, imfit  
  > "We performed the calibration using the version 6.2.1.7 of the CASA software (cite: CASA_2022)." (2 Observations)
- **galario** : 2D visibility-plane fitting of the outer disc and model subtraction  
  > "We characterize the morphological structure of the continuum emission with the code `galario` (cite: Tazzari_2018)" (3 Methods)
- **emcee** : MCMC sampling for the visibility fit and the Bayesian variability test  
  > "following a Markov Chain Monte Carlo (MCMC) approach implemented with the package `emcee` (cite: Foreman-Mackey_2013)" (3 Methods)
- **scipy (curve_fit)** : Fitting the spectral index  
  > "with the `curve_fit` function of the `scipy` module (cite: Virtanen_2020)" (5.3 Spectral Index)
- **exoALMA pipeline and alignment procedure** : Iterative self-calibration and alignment of execution blocks  
  > "we followed the iterative self-calibration following the exoALMA pipeline (cite: Loomis_2025)" (2 Observations)
- **whereistheplanet** : Expected positions of PDS 70 b and c  
  > "We compute the expected position of both PDS 70 b and c using the orbital fitting tool[^3] presented in (cite: Wang_2021)" (5.1 c_smm astrometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak flux of c_smm, B7 2019 fiducial image | 94 | 18 | uJy/beam | 4 | we measure a peak flux emission of $94\pm18~\rm\mu Jy/beam$ |
| Peak intensity difference c_smm between 2019 and 2021 epochs | 64 | 34 | uJy/beam | 4 | We measure a peak flux difference of up to $64\pm34\rm~\mu Jy/beam$ at $1\sigma$ confidence level for the continuum emission coming from the region around PDS 70 c |
| Bayesian constant-flux F0 and excess noise sigma0 (1 sigma intervals) | F0 in [101,133] uJy/beam; sigma0 in [2,35] | 1 sigma interval | uJy/beam | 4 | We find $1\sigma$ confidence intervals of $[101,133]~\rm\mu Jy/beam$ and $[2,35]$ for $F_0$ and $\sigma_0$, respectively |
| Peak emission near PDS 70 b, B6 2021 LF and HF | 59 and 46 | 17 and 14 | uJy/beam | 4 | with a peak emission of $59\pm17~\rm\mu Jy/beam$ and $46\pm14~\rm\mu Jy/beam$ for B6 2021 LF and B6 2021 HF, respectively |
| Spectral index upper limits at PDS 70 b (B6 LF, HF) | alpha < 3.0 and alpha < 5.8 | 3 sigma upper limit | dimensionless | 7 | of $\alpha<3.0$ and $\alpha<5.8$ for the lower and higher frequency Band 6 datasets, respectively |
| Dust mass range of material at PDS 70 c and of the inner disc | 0.008-0.063 Mearth (c) and 0.04-0.31 Mearth (inner disc) | not stated | Earth masses | 5 | We measure the dust mass of the material co-located with PDS 70 c and the inner disc to be in the range $0.008-0.063~M_\oplus$ and $0.04-0.31~M_\oplus$, respectively |
| Inner disc radius (1 sigma mask approximated as Gaussian) | 0.10-0.14 arcsec (11-16 au) | not stated | arcsec | 5 | the radius of the inner disc is in the range $0.10-0.14~\rm arcsec$ ($11-16\rm~au$) |
| Total displacement of c_smm 2019 to 2021 and 2019 to 2023 | 35 and 44 | 15 and 15 | mas | 6 | We obtain a total displacement of $35\pm15~\rm mas$ ($\sim2\sigma$ significance) between the 2019 and 2021 epochs and $44\pm15~\rm mas$ ($\sim3\sigma$ significance) between the 2019 and 2023 epochs |
| Astrometric accuracy for 2019, 2021, 2023 | 9, 12, 12 | not stated | mas | 6 | we find an astrometric accuracy of $9~\rm mas$, $12~\rm mas$ and $12~\rm mas$, respectively. |
| Spectral index of the entire disc | 2.8 | 0.4 | dimensionless | 7 | We obtain spectral indices of $\alpha_{\rm mm}^{\rm D}=2.8\pm0.4$ |
| Spectral index of c_smm | 2.5 | 1.2 | dimensionless | 7 | $\alpha_{\rm mm}^{c_{\rm smm}}=2.5\pm1.2$ |
| Spectral index of the inner disc | 3.2 | 0.5 | dimensionless | 7 | $\alpha_{\rm mm}^{\rm ID}=3.2\pm0.5$ |
| Azimuthal shift of the outer-ring arc 2019 to 2023 | 7 | not stated | deg | 2 | an azimuthal shift of $7\deg$ from the 2019 to the 2023 epoch matches the Keplerian speed of PDS 70 c |

## Qualitative findings

- Outer ring morphology is unchanged across epochs while the cavity emission shows variable morphology  
  > "While the morphological structure of the ring appears unchanged at different epochs, the emission in the cavity, seen in an inset for each plot, shows a variable morphology." (4 Results)
- Clumps 1 and 2 are re-detected in B7 2019 but not significantly after subtracting a central Gaussian model  
  > "We re-detect Clump 1 at $\sim7\sigma$ and Clump 2 at $\sim4\sigma$ in the B7 2019 dataset" (4 Results)
- Inner disc emission is dominated by optically thin dust  
  > "suggesting the inner disc emission is dominated by optically thin dust" (abstract)

## Claim tuples

- H: Compact dust emission around PDS 70 c is present in independent datasets | E: Visibility modelling of the outer disc, model subtraction and imaging of the cavity in five Band 6/7 datasets | R: Compact emission detected in all datasets at more than 3.8 sigma | F: Independent re-detection confirms circumplanetary material at PDS 70 c | **supported**
- H: The compact emission moves with the planet | E: imfit Gaussian positions in Band 7 residuals at 2019, 2021, 2023 compared with the orbital prediction | R: Displacement of 35+/-15 mas and 44+/-15 mas (2-3 sigma) | F: Position is consistent with the planet's expected motion; tentative and needs more epochs | **partially**
- H: The emission around PDS 70 c is variable | E: Epoch-to-epoch peak intensity differences and a Bayesian constant-flux test | R: Difference up to 64+/-34 uJy/beam at 1 sigma; sigma0 interval [2,35] | F: Measurements are not consistent with significant variability | **partially**
- H: Compact emission is detectable around PDS 70 b | E: Residual imaging in Band 6 and 7 | R: Marginal ~3 sigma compact emission in Band 6 (59+/-17 and 46+/-14 uJy/beam); diffuse emission in Band 7 | F: Tentative first Band 6 detection of compact emission at b | **partially**
- H: Inner disc dust is optically thin and not variable | E: Flux densities and a Band 6-7 spectral index fit of the inner disc across epochs | R: alpha = 3.2+/-0.5; flux densities consistent across epochs | F: Inner disc emission is dominated by optically thin dust with no flux variability | **supported**

## Reasoning

- Why this data: Focus on long-baseline data within one month to resolve emission near planet c and study its motion  
  > "Since our primary focus is to spatially resolve the compact emission around planet c and study its motion, we focus on the LB observations taken within one month." (2 Observations)
- Why this method: Model the outer disc first because cavity emission is faint and overlaps with it  
  > "As the emission of the cavity is faint and partly overlapping with the outer disc, we first model the outer disc." (3 Methods)
- Alternative: Adding a central Gaussian for the inner disc to the model was tested on B7 2019 only; fiducial model omits it  
  > "we perform a test run with 100 walkers and 1000 steps on the B7 2019 dataset adding a central Gaussian" (3 Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 6 spectral index limits for PDS 70 b may be contaminated by inner disc material  
  > "these upper limits should be treated with care as the compact source is not well separated from the inner disc in Band 6 and the emission could be contaminated by material from the inner disc" (4 Results)
- Limitation (authors): No simultaneous ALMA and Halpha observations to test variability  
  > "the lack of simultaneous ALMA and H$\alpha$ observations limits the interpretation of the results" (5.2 c_smm variability)
- Limitation (authors): Astrometry cannot be absolute; star position assumed at the galario disc centre  
  > "preventing us to obtain absolute astrometric measurements, we can still define a relative coordinate system" (5.1 c_smm astrometry)
- Caveat (inferred, ours): Detections are 3.8-6.7 sigma on residuals that depend on the chosen outer-disc model
- Caveat (inferred, ours): Displacement is only 2-3 sigma with a coarse astrometric error budget
- Caveat (inferred, ours): Band 7 2021 peak is likely contaminated by inner disc emission
- Caveat (inferred, ours): Dust masses depend on assumed T, kappa and optically thin emission

## Reproducibility

- Data public (paper): Archival ALMA data from seven listed programs  
  > "We calibrate and analyse archival Atacama Large Millimetre/subMillimetre Array (ALMA) Band 6 and 7 observations of PDS 70" (abstract)
- Products in archive: _not stated_
- Missing: exoALMA pipeline scripts and alignment parameters
- Missing: Calibration details for Band 6 and prior-paper datasets only by reference
- Missing: tclean threshold, niter and mask definitions
- Missing: uv-taper value
- Missing: Aperture and imfit region definitions
- Data volume (inferred): Several hundred GB to ~1 TB raw across seven projects (inferred, not stated)
- Score (inferred): 3/5, Data are public and fits, priors and numeric results are given, but calibration is largely delegated to earlier papers and the exoALMA pipeline, and tclean and aperture settings are incomplete.
- Rediscovery candidate: no, Recipe is not complete without the exoALMA self-calibration scripts and prior-paper calibration, and results depend on residual-image details.

## Links

- Method: (cite: Loomis_2025) (exoALMA self-calibration and alignment procedure)
- Method: (cite: Tazzari_2018) (galario visibility fitting code)
- Method: (cite: Benisty_2021) (Previous analysis of the same system, calibration and dust-mass approach)
- Method: (cite: Rampinelli_2024) (Flux-density uncertainty procedure and Band 6 calibration)
- Companion: (cite: Benisty_2021) (Earlier detection of circumplanetary material in 2019 Band 7 data)
- Companion: (cite: Casassus_2022) (Inner disc clumps and variability)
- Companion: (cite: Close_2025) (Halpha variability of PDS 70 c)
- Companion: (cite: Aizawa_2024) (Independent disc asymmetry modelling)
- Related: exoALMA

## Checks

```json
{
 "quotes": 114,
 "quotes_ok": 114,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 7,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 78,
  "rate": 0.757
 },
 "evidence_ok": true
}
```
