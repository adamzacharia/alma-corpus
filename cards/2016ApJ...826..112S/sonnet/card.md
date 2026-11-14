# ALMA Imaging and Gravitational Lens Models of South Pole Telescope—Selected Dusty, Star-Forming Galaxies at High Redshifts

`2016ApJ...826..112S` | The Astrophysical Journal 2016 | first author: Spilker, J. S. | arXiv: 1604.05723 | DOI: 10.3847/0004-637X/826/2/112

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the lens models, magnifications and intrinsic sizes of SPT-selected lensed DSFGs, and what do the sizes imply for the size distribution, dust optical depth wavelength and [CII]/FIR ratio?  
  > "In this paper, we present lens models of a sample of 47 DSFGs discovered in South Pole Telescope data and observed by ALMA at $\sim0.5$” resolution." (1 Introduction)
- Target **47 SPT-selected DSFGs (e.g. SPT0020-51 ... SPT2357-51)**: coordinates Table 1 lists ALMA phase centers for each source  
  > "SPT0418-47 | SPT-S J041839-4751.9 | 04:18:39.27 | -47:51:50.10" (Table 1); z/distance source z=1.87-5.81 where known (Table 1, z_S)  
  > "SPT0418-47 | SPT-S J041839-4751.9 | 04:18:39.27 | -47:51:50.10" (Table 1); distance from Weiss et al. 2013 and Strandet et al. 2016 (spectroscopic redshifts)  
  > "SPT0418-47 | SPT-S J041839-4751.9 | 04:18:39.27 | -47:51:50.10" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00958.S, 2011.0.00957.S, 2012.1.00844.S, 2012.1.00994.S
- bands: 870 um (Band 7), four basebands near 336.8, 338.8, 348.8, 350.8 GHz  
  > "Four basebands, each processing 2 GHz of telescope bandwidth, were centered near 336.8, 338.8, 348.8, and 350.8 GHz." (2 Sample Selection and Observations)
- frequencies and spectral setup: 128 channels of 15.6 MHz per baseband  
  > "The correlator was configured to provide 128 channels of 15.6 MHz width for each baseband." (2 Sample Selection and Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: two configurations per source group, ~0.5 and 1.5 arcsec resolution; 14-25 antennas  
  > "each group of sources was observed with two different array configurations, corresponding to approximately 0.5 and 1.5$''$ resolution" (2 Sample Selection and Observations)
- baselines: _not stated_
- angular resolution: ~0.5 arcsec in higher-resolution tracks  
  > "We present 0.5$''$ resolution 870 $\mu\rm{m}$ Atacama Large Millimeter/submillimeter Array imaging" (abstract)
- max recoverable scale: _not stated_
- sensitivity: per-track average rms 0.21-0.72 mJy  
  > "15 June 2012 | 0.9 | Callisto | 20 | 0.64 | 0.5”$\times$0.7”" (Table 2)
- time on source: 60-90 s per source per configuration; total 9.4 h including calibrators  
  > "Each source was observed for 60–90 s per array configuration. The total observing time for all calibrators and science targets was 9.4 hours." (2 Sample Selection and Observations)
- observing dates: eight sessions, Nov 2011 to Aug 2012  
  > "The ALMA observations were carried out in eight sessions from November 2011 to August 2012" (2 Sample Selection and Observations)
- pi or archival as stated: _not stated_
- Other facility **LABOCA/APEX**: 870 um single-dish flux densities and refined positions  
  > "typically at 870 $\mu\rm{m}$ using the Large Apex BOlometer CAmera (LABOCA) or at 1.3 mm using the Submillimeter Array (SMA)" (2 Sample Selection and Observations)
- Other facility **HST, VLT, Magellan, Spitzer/IRAC**: optical/NIR imaging used to guide lens models  
  > "we make use of optical and infrared imaging data obtained from a variety of facilities, including the *Hubble* Space Telescope, Very Large Telescope, Magellan-Baade telescope, and *Spitzer*/IRAC." (2 Sample Selection and Observations)
- External data: Source and lens redshifts  
  > "Source redshifts are given in (cite: weiss13) and Strandet et al.(submitted). Lens redshifts are given in Rotermund et al., in prep." (Table 1) [from (cite: weiss13); (cite: strandet16)]
- External data: Multiwavelength photometry for SED fitting  
  > "We perform the fitting described using the source photometry in (cite: weiss13; strandet16), and an MCMC fitting routine." (4.3 Constraining the Dust Opacity) [from (cite: weiss13; strandet16)]
- External data: Unlensed DSFG sizes for comparison  
  > "(cite: simpson15b) measure sizes of 22 sources based on 870 $\mu\rm{m}$ ALMA imaging" (4.2 Size Distribution) [from (cite: simpson15b); (cite: ikarashi15)]
- External data: Herschel-selected lens model sizes/magnifications  
  > "for both the SPT sample and the *Herschel*-selected samples of (cite: bussmann13; bussmann15)" (4.2 Size Distribution) [from (cite: bussmann13; bussmann15)]
- External data: [CII]/FIR vs Sigma_FIR slope from GOALS  
  > "the slope is exactly as determined by (cite: diazsantos13), i.e., $[C{\scriptsize II}]/\ensuremath{L_{\rm{FIR}}}\propto \ensuremath{\Sigma_{\rm{FIR}}}^{-0.35}$." (4.4 Revisiting the [CII]/FIR Ratio) [from (cite: diazsantos13)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune, Callisto or quasar J0403-360 per track  
  > "28 Nov. 2011 | 1.4 | J0403-360 | 14 | 0.60 | 0.8”$\times$2.2”" (Table 2)
- flux scale uncertainty: 10%, with amplitude rescaling between tracks allowed in modeling  
  > "This flux scale is estimated to be correct to within 10%, although we allow an amplitude re-scaling between the two observations of each group of sources in our modeling" (2 Sample Selection and Observations)
- self calibration: antenna-based phase errors fit in the lens modeling following Hezaveh et al. 2013  
  > "We also calibrate uncorrected antenna-based phase errors using the procedure described in (cite: hezaveh13)." (3 Visibility-Based Lens Modeling)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = -0.5  
  > "the data from each track were combined and imaged using Briggs weighting (robust parameter $= -0.5$)" (2 Sample Selection and Observations)
- uv taper: 50 kλ taper for total flux measurement  
  > "we first image the data using a taper in the $uv$-plane at 50 k$\lambda$, corresponding to a resolution of $\gtrsim4$”." (4.2 Flux Recovery)
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN to 3 sigma threshold; total flux is sum of CLEAN components  
  > "We then CLEAN the images to a 3$\sigma$ threshold and correct for the response of the primary beam." (4.2 Flux Recovery)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied for total flux  
  > "We then CLEAN the images to a 3$\sigma$ threshold and correct for the response of the primary beam." (4.2 Flux Recovery)
- array combination: tracks of both configurations combined and imaged together  
  > "After calibration, the data from each track were combined and imaged using Briggs weighting" (2 Sample Selection and Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Lens modeling procedure (visibility-based, phase-error calibration)  
  > "Our lens modeling procedure is based on the work of (cite: hezaveh13)" (3 Visibility-Based Lens Modeling) [from (cite: hezaveh13)]
- Sample selection criteria  
  > "The selection criteria used to generate the SPT DSFG sample are described in detail by (cite: weiss13)." (2 Sample Selection and Observations) [from (cite: weiss13)]
- External shear deflection calculation  
  > "with deflections calculated as in (cite: keeton00)" (3 Visibility-Based Lens Modeling) [from (cite: keeton00)]

### Not stated but needed to reproduce (our reading)

- MCMC settings (walkers, steps, burn-in, convergence)
- Priors/bounds on lens and source parameters
- CASA version and calibration/flagging details
- Software used for imaging (CLEAN) not named
- Flux standard model versions
- SED fit priors and MCMC settings; outlier model for the lambda0-Tdust fit
- Source-plane component number choices per source beyond DIC
- Photometry values used in SED fits

## Analysis recipe

1. **Calibrate and combine tracks**: Standard calibration with quasar bandpass/phase calibrators; visibility noise from differencing successive visibilities; tracks combined  
  > "We estimate the noise on each visibility measurement by calculating the scatter after differencing successive visibilities on the same baseline, baseband, and polarization." (2 Sample Selection and Observations)
   - fitting: _not stated_
   - validation: ICRF sources observed to verify astrometry and baseline solutions  
  > "Additional sources with precisely known positions from the International Celestial Reference Frame (ICRF; (cite: ma98)) were observed to verify the astrometric and antenna baseline solutions." (2 Sample Selection and Observations)
2. **Visibility-plane lens modeling**: SIE lenses (plus optional shear) and point-source or Sersic background components; model image Fourier transformed and sampled at data uv points; chi^2 likelihood; free amplitude rescaling, astrometric offset and antenna phase errors  
  > "We then invert this image to the Fourier plane and measure the modeled visibilities at the $uv$ coordinates of each dataset. The quality of fit is calculated using the $\chi^2$ metric." (3 Visibility-Based Lens Modeling)
   - software: emcee, visilens
   - assumption: Flat WMAP9 cosmology, h=0.693, Om=0.286  
  > "we assume a flat WMAP9 $\Lambda$CDM cosmology, $h=0.693$, $\Omega_m = 0.286$, and $\Omega_\Lambda = 0.713$" (1 Introduction)
   - fitting: emcee MCMC; DIC for model selection between numbers of components  
  > "We employ a Markov Chain Monte Carlo (MCMC) fitting procedure, using the `emcee` (cite: foremanmackey13) code to sample the posterior probability function." (3 Visibility-Based Lens Modeling)
   - validation: Residual maps; model flux compared to total ALMA flux; comparison with Hezaveh et al. models; high-baseline imaging  
  > "The models contain a median of 102% of the total ALMA flux densities, indicating that no significant sources of emission remain unaccounted for by the models." (4.2 Flux Recovery)
3. **Flux recovery test vs LABOCA**: Taper at 50 klambda, CLEAN, sum components, compare to LABOCA  
  > "The total ALMA flux is then defined as the sum of the CLEAN components, in order to avoid the need to define an aperture" (4.2 Flux Recovery)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare lensed vs unlensed size distributions**: Two-sample K-S test of sizes of strongly lensed (mu>2) SPT and Herschel sources vs unlensed samples  
  > "The two-sample K–S test confirms that we cannot reject the hypothesis that both distributions are drawn from the same parent distribution ($p=0.84$)." (4.2 Size Distribution)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit modified blackbody SED to constrain lambda0**: Fit rest wavelengths >50 um with modified blackbody with free normalization, Tdust, lambda0; likelihood includes lens-model intrinsic flux and size at 870 um; lambda0-Tdust relation by orthogonal distance regression with outlier marginalization  
  > "The free parameters are the SED normalization (which stands in for the source solid angle at wavelengths without size measurements; see below), $T_{\rm{dust}}$, and $\lambda_0$." (4.3 Constraining the Dust Opacity)
   - software: MCMC (unnamed)
   - parameter: beta = 2  
  > "assuming $\beta = 2$ and allowing $\lambda_0$ to be a free parameter, although allowing $\beta$ as a free parameter does not alter our results" (4.3 Constraining the Dust Opacity)
   - assumption: Uniform source emission with single Tdust and lambda0  
  > "at present we assume that the source emission is uniform, mirroring the assumptions which must be made with unresolved photometry." (4.3 Constraining the Dust Opacity)
   - fitting: MCMC; log-likelihood of unresolved photometry plus resolved 870 um flux  
  > "At each MCMC step, we calculate the log-likelihood of producing the spatially unresolved continuum measurements given the proposed combination of parameters" (4.3 Constraining the Dust Opacity)
   - validation: Checked hot dust component and short-wavelength power law do not change conclusions  
  > "We have verified that neither a hot dust component nor a short-wavelength power-law significantly affect our conclusions." (4.3 Constraining the Dust Opacity)
6. **Compare [CII]/LFIR with Sigma_FIR**: Refit photometry for uniform LFIR, compute Sigma_FIR from lens-model sizes, compare with GOALS relation  
  > "We have re-fit the photometry of all sources to ensure a uniform determination of $L_{\rm{FIR}}$." (4.4 Revisiting the [CII]/FIR Ratio)
   - assumption: LFIR integrated over rest-frame 42.5-122.5 um  
  > "We define the far-infrared luminosity $L_{\rm{FIR}}$ to be integrated over rest-frame $42.5-122.5$ $\mu\rm{m}$" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **emcee** : MCMC sampling of lens model posteriors  
  > "using the `emcee` (cite: foremanmackey13) code to sample the posterior probability function" (3 Visibility-Based Lens Modeling)
- **visilens** : visibility-based lens modeling code  
  > "The code used to generate all the models in this work, along with example usage scripts, is available at <https://github.com/jspilker/visilens>." (3 Visibility-Based Lens Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median magnification, strongly lensed subset | 6.3 | not stated | dimensionless | 2 | with a median magnification of 5.5 for all sources, or 6.3 for the strongly lensed subset alone |
| Median magnification, all sources | 5.5 | not stated | dimensionless | 2 | with a median magnification of 5.5 for all sources |
| Median Einstein radius | 0.64 | not stated | arcsec | 2 | We find a median Einstein radius of 0.64$''$ |
| Sources strongly lensed | 38 of 47 (81%) | not stated | sources | 2 | for 38 sources (81%), strong gravitational lensing is the most plausible explanation for the ALMA emission |
| Median ALMA/LABOCA flux recovery | 91 | 24 | percent | 3 | We recover a median of ($91\pm24$)% of the LABOCA flux density |
| Median intrinsic FWHM | 0.28 | not stated | arcsec | 2 | We find a median intrinsic FWHM of 0.28”. |
| K-S p-value lensed vs unlensed sizes | 0.84 | not stated | dimensionless | 4 | ($p=0.84$) |
| Median lambda0 | 140 | 40 | um | 5 | We find a median value of $\lambda_0$= 140 $\pm$ 40 $\mu\rm{m}$ |
| lambda0-Tdust relation slope | 3.0 | 0.7 | um/K | 5 | \ensuremath{\lambda_0}= (3.0 \pm 0.7) \times (\ensuremath{T_{\rm{dust}}}- 40) + (118 \pm 12) \ensuremath{\mu\rm{m}}. |
| Multiplicity fraction | 13% (6/47) | not stated | percent | 2 | only 13% (6/47) of sources contain multiple components at $>5\sigma$ significance |

## Qualitative findings

- Dust mass assuming lambda0 = 100 um is overpredicted by more than a factor of 2 for the hottest sources.  
  > "reaching more than a factor of 2 for the hottest sources" (4.3 Constraining the Dust Opacity)

## Claim tuples

- H: Do lensed and unlensed DSFG size distributions differ given size-magnification bias? | E: Compared sizes of strongly lensed SPT and Herschel sources with two unlensed samples via K-S test | R: p = 0.84 | F: No significant difference; the true size distribution may be narrow | **supported**
- H: Is lambda0 correlated with dust temperature, and does assuming fixed lambda0 bias dust mass? | E: Modified blackbody fits using lens-model sizes | R: median lambda0 140 +/- 40 um, correlated with Tdust | F: Fixed lambda0=100 um overestimates dust mass by up to >2 for hot sources | **supported**
- H: Does [CII]/LFIR correlate with Sigma_FIR at high z as at low z? | E: Compared high-z sources with GOALS relation using lens-model sizes | R: Decline continues to Sigma_FIR ~1e13 Lsun/kpc^2 | F: Compactness of IR-emitting region drives the [CII] deficit | **supported**
- H: What fraction of SPT DSFGs are strongly lensed and how magnified? | E: Visibility-based lens modeling of 47 sources | R: At least 70% strongly lensed, median mu 6.3, tail to >30 | F: SPT sample is mostly strongly lensed with higher magnifications than Herschel sample | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Modeling visibilities directly avoids correlated image noise and allows accounting for residual calibration errors  
  > "Instead, a better option is to model the visibilities directly, where the noise and measurement are well understood." (3 Visibility-Based Lens Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Lens model uncertainties on source properties are dominated by systematics from source parameterization  
  > "the model uncertainties on the properties of the background sources are dominated by systematic, rather than statistical, uncertainty" (4.1 Reliability of Lens Models)
- Caveat (inferred, ours): Smooth elliptical Sersic sources ignore clumpy structure, so magnifications may be biased
- Caveat (inferred, ours): Lensed and unlensed comparison samples are small and incomplete
- Caveat (inferred, ours): Normalization freedom at non-870 um wavelengths weakens the SED constraint on lambda0

## Reproducibility

- Data public (paper): ALMA project codes listed; code public on GitHub  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2011.0.00957.S, #2011.0.00958.S, #2012.1.00844.S, and #2012.1.00994.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: visilens at https://github.com/jspilker/visilens  
  > "The code used to generate all the models in this work, along with example usage scripts, is available at <https://github.com/jspilker/visilens>." (3 Visibility-Based Lens Modeling)
- Missing: MCMC and prior settings
- Missing: Photometry tables and lens-redshift data (in prep.)
- Missing: CASA version and calibration scripts
- Data volume (inferred): ~10-50 GB (Cycle 0, eight short tracks, 128 channels x 4 basebands)
- Score (inferred): 4/5, Public Cycle 0 data, public code and full parameter tables; but MCMC and calibration details are sparse.
- Rediscovery candidate: yes, Data and code are public and results are numeric (magnifications, sizes), though some settings are missing.

## Links

- Method: (cite: hezaveh13) (Original visibility-based lens modeling technique)
- Companion: (cite: weiss13) (Sample selection and LABOCA fluxes)
- Companion: (cite: strandet16) (Redshifts and photometry of SPT DSFGs)
- Related: South Pole Telescope survey
- Related: Herschel-ATLAS lensed sample (Bussmann et al.)
- Related: ALESS
- Related: GOALS

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 51,
  "rate": 0.637
 },
 "evidence_ok": true
}
```
