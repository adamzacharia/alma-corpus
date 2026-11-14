# Fitting pseudo-Sérsic (Spergel) light profiles to galaxies in interferometric data: The excellence of the uυ-plane

`2024A&A...684A..23T` | Astronomy and Astrophysics 2024 | first author: Tan, Qing-Hua | arXiv: 2312.05425 | DOI: 10.1051/0004-6361/202347255

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: high_z_galaxies, instrumentation
- Question: How well does Spergel profile fitting in the uv-plane (GILDAS uv_fit) recover galaxy morphology compared with Sersic fitting in the image plane (galfit), and can Spergel and Sersic indices be converted?  
  > "we aim to provide a technical assessment of the use of the Spergel profile." (1 Introduction)
- Target **PACS-787**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HZ7**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01359.S, 2016.1.01426.S
- bands: Band 7 (noise data); Band 7 (HZ7); Band 6 (PACS-787)  
  > "The noise was obtained from real data using ALMA band 7 observed visibilities from galaxies in a recent survey" (3.1 Realistic noise map)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: HZ7 C43-4; PACS-787 C40-6 and C40-1  
  > "in the C43-4 configuration with 47/45 12m antennas in band 7" (6.4 The power of Spergel fitting)
- baselines: _not stated_
- angular resolution: Noise dataset: natural-weighting beam 1.0 arcsec  
  > "the FWHM of the synthesized beam using natural weighting is $\theta_{\rm b}=1.0''$" (3.1 Realistic noise map)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: HZ7 80 min; PACS-787 19.7 and 10.2 min  
  > "with 19.7 and 10.2 minutes of on-source integration time in ALMA Cycle 4" (6.4 The power of Spergel fitting)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] HZ7 (303.93 GHz)
- Line: CO 5-4 (PACS-787) (228.17 GHz)
- External data: Band 7 calibrated visibilities used as noise realisations  
  > "The noise was obtained from real data using ALMA band 7 observed visibilities from galaxies in a recent survey" (3.1 Realistic noise map) [from (cite: puglisi19; puglisi21; valentino20)]
- External data: Spergel c_nu tabulated values every 0.05 for nu from -0.90 to 0.85  
  > "tabulates the values of $c_{\nu}$ every $0.05$ for a range of $\nu$ from $-0.90$ to $0.85$." (10.1 Definition and Fourier Transform) [from (cite: spergel10)]
- Simulation/model as data: Monte Carlo simulated Spergel sources (R_e/theta_b 0.1-0.7, nu 0.5 to -0.7, S/N 25-400) inserted into empty real-noise visibilities  
  > "The model sources were created using GILDAS through the MAPPING task `uv`$\_$`fit`." (3.2 Source models)

## Processing

### Calibration

- pipeline or manual: Calibrated visibilities exported from CASA  
  > "the calibrated ALMA visibilities for several targets were exported from CASA using the `exportuvfits`." (3.1 Realistic noise map)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Dirty maps from Fourier transform of visibilities, no cleaning, for galfit  
  > "The *galfit* run is performed on the dirty maps, which are created by Fourier transforming visibilities without cleaning." (3.4 Image model-fitting)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "the FWHM of the synthesized beam using natural weighting is $\theta_{\rm b}=1.0''$" (3.1 Realistic noise map)
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

- Spergel profile definition and c_nu table  
  > "(cite: spergel10) introduced an alternative to the S${\rm \acute{e}}$rsic model for galactic luminosity profiles" (2.2 The Spergel profile) [from (cite: spergel10)]

### Not stated but needed to reproduce (our reading)

- Which specific targets/ALMA project of the noise visibilities and their codes
- Number of Monte Carlo realisations per grid cell
- galfit image size, pixel size and fitting region
- Exact uv_fit initial-guess ranges for the real-data fits
- Fitted Spergel parameter uncertainties for PACS-787 and HZ7
- Axis ratio and PA used for simulations

## Analysis recipe

1. **Build empty noise datasets**: Export calibrated visibilities, convert to uv tables, merge spws, subtract best-fit Spergel models of detected sources  
  > "any detected sources were subtracted from the visibility data using the best-fitting Spergel model to the visibilities." (3.1 Realistic noise map)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Residual pixel distribution Gaussian, noise 40 uJy/beam  
  > "The noise level measured from the Gaussian fit is 40 $\mu$Jy beam$^{-1}$." (3.1 Realistic noise map)
2. **Simulate Spergel sources**: Insert elliptical Spergel models into noise data with a grid in S/N and R_e/theta_b and nu  
  > "$R_{\rm e}/\theta_{\rm b}$ = 0.1, 0.2, 0.4, and 0.7" (3.2 Source models)
   - software: GILDAS uv_fit
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit in uv-plane and image plane**: uv_fit Levenberg-Marquardt of Spergel models on visibilities; galfit Sersic on dirty maps with the dirty beam as PSF  
  > "The `uv_fit` command uses the `SLATEC/DNLS1E` implementation of the Levenberg-Marquardt algorithm" (3.5 Details of the UV_FIT)
   - software: GILDAS uv_fit, galfit
   - fitting: Levenberg-Marquardt minimising reduced chi2; multiple initial guesses within a factor 2  
  > "We test the fit by setting the starting range parameters of initial guesses within a factor of 2 centered on the input mock values" (3.3 Visibility model-fitting)
   - validation: Compare recovered to input; scatter as 1.48xMAD  
  > "converted to $\sigma$ using $\sigma=$1.48$\times$MAD" (4.2 Comparison of the relative measurement uncertainty)
4. **Derive Spergel-Sersic conversions**: Fit galfit Sersic to noise-free Spergel images; fit empirical functions; cross-check with emcee analytic matching  
  > "we create noise-free images of Spergel two-dimensional models, as described in the next section, and use *galfit* to measure the corresponding S${\rm \acute{e}}$rsic index." (2.4)
   - software: galfit, emcee
   - fitting: _not stated_
   - validation: Residuals within 10% for nu>-0.7  
  > "The residuals of the fit indicate that the uncertainties of S${\rm \acute{e}}$rsic $n$ are largely within 10% for model sources" (2.4)
5. **Refit archival halo cases**: uv-plane Spergel fits to PACS-787 (two components) and HZ7 (one)  
  > "For PACS-787, which contains two galaxies in the process of merging, we used two Spergel components (one for each galaxy), while for HZ7, we used a single Spergel." (6.4)
   - software: GILDAS uv_fit
   - fitting: _not stated_
   - validation: Residuals clean  
  > "The residuals are clean, and no further components are needed" (6.4)

## Software

- **GILDAS (MAPPING uv_fit)** : Spergel uv-plane fitting and simulations  
  > "Fitting elliptical Spergel models to the simulated dataset is performed using the task `uv`$\_$`fit`." (3.3)
- **galfit** : Sersic image-plane fitting  
  > "fitted with a single-component S${\rm \acute{e}}$rsic profile using *galfit*" (3.4)
- **CASA** : exportuvfits of calibrated visibilities  
  > "exported from CASA using the `exportuvfits`" (3.1)
- **emcee** : MCMC matching of Spergel and Sersic profiles  
  > "We use the `emcee` package (cite: foreman-mackey2013) in Python to perform Markov chain Monte Carlo (MCMC) search for the best-fit." (Appendix A)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| nu to n conversion coefficients p1..p5 | 0.0249, -7.72, 0.191, -0.721, 1.32 | within 10% | dimensionless | 4 | $p_1 = 0.0249$, $p_2 = -7.72$, $p_3 = 0.191$, $p_4 = -0.721$, and $p_5 = 1.32$ |
| Median sigma(n)/n at S/N=50 | 0.36 | not stated | dimensionless | 3 | with a median value of $\sigma$($n$)/$n$ of 0.36 |
| uv_fit error underestimate factors (flux, Re, q, nu) | 1.6, 2.5, 2.1, 1.5 | not stated | dimensionless | 3 | with a mean value of 1.6, 2.5, 2.1, and 1.5 for the parameter estimates of flux density, effective radius, axis ratio, and Spergel index |
| Median scatter ratio uv/image (flux, Re, q, n) | 0.5, 0.5, 0.6, 0.5 | not stated | dimensionless | 3 | the median scatter ratios are 0.5, 0.6, and 0.5, respectively |
| Spergel nu for HZ7 | -0.42 | not stated | dimensionless | 5 | For HZ7, we find $\nu=-0.42$ and $R_{\rm e}/\theta_{\rm b}\sim1.3$. |

## Qualitative findings

- galfit image-plane fits show larger biases and scatter than uv-plane fits; cleaning is not needed  
  > "image-based measurements obtained from *galfit* using a S${\rm \acute{e}}$rsic model tend to have higher systematic biases and larger uncertainties" (7 Conclusions)

## Claim tuples

- H: uv-plane Spergel fitting outperforms image-plane Sersic fitting | E: Monte Carlo simulations with real noise | R: Smaller bias and scatter by about a factor of two in the uv-plane | F: uv-plane fitting is preferred | **supported**
- H: Minimum S/N needed for a Spergel index | E: sigma(n)/n vs S/N | R: S_tot/sigma_b >= 50 | F: S/N of at least 50 is required | **supported**
- H: Reported halos are distinct structures | E: Single Spergel uv fits to PACS-787 and HZ7 | R: Single models fit both core and halo | F: Halos may be extended wings of high-n profiles | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibilities are independent while image pixels are correlated  
  > "working directly in the $uv$-plane would be preferable because the measured data points are independent there-in." (1 Introduction)
- Alternative: Aperture photometry tested for point sources; consistent with uv fits  
  > "flux density estimates obtained through aperture photometry are fully consistent to those measured in the $uv$-plane" (6.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Whether Spergel or Sersic fits real galaxies better remains open  
  > "The question of whether Spergel or S${\rm \acute{e}}$rsic models provide better fits to actual galaxies remains open" (6.1)
- Caveat (inferred, ours): Simulations use only Band 7 noise from three configurations
- Caveat (inferred, ours): Halo re-analysis has no quantitative goodness-of-fit comparison
- Caveat (inferred, ours): galfit run on dirty maps is a particular choice that may disadvantage it

## Reproducibility

- Data public (paper): PACS-787 and HZ7 data downloaded from archive  
  > "We have downloaded the data for both datasets as described below." (6.4)
- Products in archive: _not stated_
- Missing: Noise-source project codes and uv_fit settings for real-data fits
- Missing: galfit setup details
- Data volume (inferred): Tens of GB (archival calibrated visibilities for several datasets)
- Score (inferred): 3/5, Simulation recipe is mostly described and GILDAS is public, but key settings and noise datasets are unspecified.
- Rediscovery candidate: no, Main results come from simulations with unidentified noise data and missing settings.

## Links

- Method: (cite: spergel10) (Spergel profile definition)
- Method: (cite: tsukui23) (noise correlation in interferometric images)
- Companion: Q. Tan et al. in preparation (Spergel modeling of ~100 archival ALMA galaxies)
- Related: Silverman et al. 2018 PACS-787
- Related: Lambert et al. 2023 HZ7

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 31,
  "rate": 0.431
 },
 "evidence_ok": true
}
```
