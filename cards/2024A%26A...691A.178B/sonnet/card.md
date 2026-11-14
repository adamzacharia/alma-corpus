# KASHz+SUPER: Evidence of cold molecular gas depletion in AGN hosts at cosmic noon

`2024A&A...691A.178B` | Astronomy and Astrophysics 2024 | first author: Bertola, E. | arXiv: 2408.16821 | DOI: 10.1051/0004-6361/202450420

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Do X-ray-selected AGN hosts at cosmic noon (z=1-2.6) have lower cold molecular gas content (CO luminosity, gas fraction) than matched non-active galaxies?  
  > "we assess the effects of AGN feedback on the molecular gas content of host galaxies in a statistically-robust, uniformly-selected, coherently-analyzed sample of AGN at $z=1-2.6$, drawn from the KASH*z* and SUPER surveys." (abstract)
- Target **KASHz and SUPER X-ray AGN with ALMA CO(2-1/3-2/4-3) (e.g. cid_108, cdfs_794, lid_1639; 46 AGN total)**: coordinates per-source RA/Dec in the sample tables (e.g. cdfs_258 03:32:14.43 -27:51:10.7)  
  > "cdfs_258 | 03:32:14.43 | -27:51:10.7  |      1.54      |   1    |" (Table 1); z/distance z=1-2.6 (spectroscopic, from KASHz NIR spectra)  
  > "cdfs_258 | 03:32:14.43 | -27:51:10.7  |      1.54      |   1    |" (Table 1); distance from KASHz NIR IFS spectral fits; some from literature (Luo+2017, Marchesi+2016)  
  > "cdfs_258 | 03:32:14.43 | -27:51:10.7  |      1.54      |   1    |" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00092.S, 2013.1.00470.S, 2015.1.00228.S, 2016.1.00171.S, 2016.1.00726.S, 2016.1.00990.S, 2016.1.01001.S, 2018.1.00164.S, 2018.1.00251.S, 2019.1.00337.S, 2019.1.00678.S
- bands: Band 3 and 4 (none in Band 5)  
  > "ALMA observations in Band 3 and 4 are available for $\simeq$10% of the KASH*z* sample" (4.1 Data selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 22 ALMA fields from 13 ALMA projects  
  > "for a total of 22 ALMA fields from 13 ALMA projects" (4.1 Data selection)
- pi or archival as stated: _not stated_
- Line: CO J=2-1, 3-2, 4-3 (not stated)
- Other facility **NOEMA**: CO(3-2) of J1333+1649  
  > "We also present here the CO(3-2) NOEMA data of J1333+1649 (project code S21CG, PI Mainieri)" (4.1 Data selection)
- Other facility **VLT/KMOS**: NIR spectroscopy and redshifts of KASHz  
  > "The KASH*z* survey ((cite: harrison2016)) is a VLT/KMOS GTO survey of X-ray selected AGN" (2.1 KASHz survey)
- Other facility **Herschel, Spitzer, HST etc. photometry**: Multiwavelength photometry for SED fitting  
  > "We collect the Near-UV to FIR photometry referring to the latest Near-UV-to-FIR multi-wavelength catalogs provided by the collaborations of the deep surveys" (12.2)
- External data: Control sample of non-active galaxies (molecular gas, FIR luminosity)  
  > "We select star-forming, non-active galaxies from the Plateau de Bure high-*z* Blue Sequence Survey catalog (cite: tacconi2018)" (3 Control sample) [from (cite: tacconi2018)]
- External data: ASPECS non-active galaxies  
  > "the non-active galaxies of ASPECS (cite: boogaard2020_aspecs)" (3 Control sample) [from (cite: boogaard2020_aspecs)]
- External data: SMG survey in COSMOS, UDS, ECDFS  
  > "We include also the ALMA/NOEMA survey of sub-$mm$ galaxies in the COSMOS, UDS, and extended CDFS (ECDFS) fields by (cite: birkin2021)" (3 Control sample) [from (cite: birkin2021)]
- External data: AGN CO line ratios r41, r31, r21  
  > "($r_{41}=0.37\pm0.11$, $r_{31}=0.59\pm0.18$, $r_{21}=0.68\pm0.17$, (cite: kirkpatrick2019))" (4.2) [from (cite: kirkpatrick2019)]
- External data: SUPER ALMA CO(3-2) luminosities  
  > "The CO luminosity of SUPER targets (flag=2 and 3) is taken from ." (Table 3 notes) [from Circosta et al. 2021 (SUPER ALMA paper)]
- Simulation/model as data: TNG, EAGLE, Simba outputs at z=2 via Ward et al. 2022 approach  
  > "We thus filter the simulations’ output at $z=2$ to select galaxies with stellar masses larger than $10^{10} \,{{\rm  M}_{\odot}}$" (6)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 6.4  
  > "using the task `tclean` in CASA 6.4" (4.2)
- pipeline version: _not stated_
- archive products used as is: Calibrated measurement sets from European ARC service  
  > "We retrieved the calibrated measurement sets using the dedicated service provided by the European ALMA Regional Center." (4.2)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, mfs for continuum, velocity mode for cubes  
  > "We produced continuum maps and (continuum-subtracted) spectral cubes using the task `tclean` in CASA 6.4, ran in “mfs” or “velocity” mode, respectively." (4.2)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We imaged all fields using a natural weighting scheme of the visibilities" (4.2)
- uv taper: _not stated_
- cell size: ~1/5 of beam FWHM  
  > "pixel size of $\simeq1/5$ of the beam FWHM" (4.2)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, continuum from all spws with line channels masked  
  > "masking the channels with line emission, and then subtracted with the `uvcontsub` CASA task" (4.2)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Bayesian bisector fit and hierarchical framework and SUPER ALMA analysis  
  > "We performed our analysis within a Bayesian framework as presented in , which allows us to take into account the upper (and lower) limits on both dependent and independent variables." (5) [from Circosta et al. 2021 (SUPER ALMA)]
- CIGALE model setup same as SUPER  
  > "We use the same setup of models presented in to reduce the possible sources of systematics between the KASH*z* and SUPER AGN" (12.1) [from Circosta et al. 2021]
- Simulation filtering approach  
  > "Following (cite: ward2022), we compare the predictions for the molecular gas fraction of galaxies at cosmic noon of TNG, EAGLE and SIMBA" (6) [from (cite: ward2022)]

### Not stated but needed to reproduce (our reading)

- Channel ranges used for line-free continuum identification per source
- Exact spectrum extraction apertures per source
- MCMC settings (walkers, steps, convergence) for emcee
- Prior ranges for the uniform priors
- Control-sample CO fluxes from PHIBSS were private communication
- Simulation catalog selections and H2 post-processing details

## Analysis recipe

1. **Image ALMA data**: tclean continuum and cubes, uvcontsub, natural weighting, channel width sampling line FWHM with >=7 elements  
  > "We produced the final cubes by setting a channel width that allows to sample the line FWHM with at least 7 spectral resolution elements" (4.2)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure CO flux**: Extract spectrum at peak/aperture, Gaussian line fit, moment-0 maps over ±3σ; upper limits 3 rms_p Δv sqrt(n) with FWHM=300 km/s  
  > "we fit the line with one Gaussian to measure its centroid and FWHM" (11)
   - software: CASA, imfit
   - parameter: non-detection if S/N<3  
  > "Non-detections were defined as sources with signal-to-noise ratio S/N$<$3 in the velocity-integrated maps." (4.2)
   - fitting: single and double Gaussian, F-test  
  > "Almost all of our CO lines are well fitted by a single Gaussian component based on the F-test" (11)
   - validation: Compared spectral fit flux with moment-0 integrated flux and imfit 2D fits  
  > "validated by the comparison with the spatially-integrated line flux and two-dimensional fits of the line velocity-integrated maps (0th order moment)" (4.2)
3. **Convert to CO(1-0) luminosity**: L'CO equation of Carilli & Walter with AGN line ratios r21=0.68, r31=0.59, r41=0.37  
  > "assuming the line ratios measured for a sample of IR-selected AGN up to $z\simeq4$" (4.2)
   - assumption: Control sample uses r21=0.6, r31=0.5  
  > "retrieve the CO(1-0) using $r_{21}=0.6$ and $r_{31}=0.5$" (3)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fitting for M*, LFIR, Lbol**: X-CIGALE with X-ray module, delayed SFH, Bruzual&Charlot, modified Calzetti, Dale/Fritz dust/AGN templates  
  > "performing SED fitting with CIGALE v.2022.1" (12)
   - software: CIGALE
   - assumption: Chabrier IMF, solar metallicity  
  > "stellar population models with solar metallicity (cite: bruzual_charlot2003), a delayed SF history" (12.1)
   - fitting: Bayesian-like PDF mean taken as best fit  
  > "In this work, we refer to the Bayesian output as the best-fit SED." (12.1)
   - validation: Bayesian/best-fit ratio within 0.5-5; reduced chi2  
  > "the ratio of the Bayesian and the best fit value falls in the 0.5–5 range" (12.3)
5. **Build matched control sample**: Two redshift bins, 0.5 dex M* bins, select controls with SFR within +0.2 dex of or below AGN  
  > "we then select all those non-active galaxies with a SFR consistent with (within $+0.2$dex to consider the uncertainties) or lower than that of AGN hosts in a given mass (and redshift) bin" (Control sample of non-active galaxies)
   - fitting: _not stated_
   - validation: KS test of M* and SFR distributions  
  > "significantly different for what concerns SFR distribution of the high-*z* bin (p-value$\simeq$1%)" (3)
6. **Bayesian bisector fits and gas fraction distributions**: OLS bisector in Bayesian framework, Gaussian likelihood with error-function upper limits, uniform priors, intrinsic scatter free; hierarchical Gaussian for fgas  
  > "Upper limits were included in the likelihood function as error functions (cite: lamperti2019)" (5.1)
   - software: emcee, scipy
   - fitting: emcee ensemble MCMC, scipy.optimize initial guess, median and 16/84 percentiles  
  > "We then sample the yielded likelihood function through the `emcee` library" (5.1)
   - validation: Repeat with only well-matched samples and MS-only targets; KS test  
  > "This result holds in both parameter spaces also when excluding non-active galaxies and AGN hosts without a proper match in the other sample" (5.3)
7. **Compare to simulations**: Filter TNG/EAGLE/Simba at z=2: 10<logM*<11.7, logSFR 0.7-2.8, logLbol>44.3, lambda_Edd>1% for AGN, <0.1% for non-active; fH2=alphaCO fgas  
  > "We use $\log{L_{\rm bol}}>44.3$ erg s$^{-1}$to span the same bolometric luminosity range as our observations" (6)
   - assumption: alpha_CO=3.6 (and 0.8 shown)  
  > "we present the comparison between observed data and simulations assuming $\alpha_{\rm CO}=3.6" (6)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4: tclean imaging, uvcontsub, imfit  
  > "using the task `tclean` in CASA 6.4" (4.2)
- **CIGALE (X-CIGALE)** v.2022.1: SED fitting  
  > "performing SED fitting with CIGALE v.2022.1" (12)
- **emcee** : MCMC sampling of likelihood  
  > "We then sample the yielded likelihood function through the `emcee` library" (5.1)
- **scipy** : initial guess optimisation  
  > "using the best fit obtained through the python module scipy.optimize" (5.1)
- **spectral-cube** : cube handling (acknowledged)  
  > "This research made use of the `spectral-cube`" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AGN sample size | 46 | not stated | AGN | 0 | The total AGN sample totals 46 AGN and presents a CO detection rate of $\simeq$50%. |
| Control sample size | 98 | not stated | galaxies | 5 | The control sample totals 98 galaxies, with a CO detection rate of $\simeq$90%. |
| AGN LCO-LFIR slope m | 1.16 | +0.15/-0.12 | dimensionless | 6 | $1.16_{-0.12}^{+0.15}$ |
| Non-active LCO-LFIR slope m | 0.99 | +0.07/-0.06 | dimensionless | 6 | $0.99 ^{+0.07}_{-0.06}$ |
| Mean log(L'CO/M*) AGN | -1.09 | +0.21/-0.19 | dex | 6 | $-1.09^{+0.21}_{-0.19}$ |
| Mean log(L'CO/M*) non-active | -0.62 | +0.07/-0.06 | dex | 6 | $-0.62^{+0.07}_{-0.06}$ |
| KS p-value of fgas distributions | <1e-7 | not stated | dimensionless | 6 | significantly different according to the KS test (p-value \< $10^{-7}$) |

## Qualitative findings

- AGN hosts are CO-depleted at fixed FIR luminosity at 3 sigma, depletion increases for decreasing LFIR  
  > "Moreover, CO depletion is differential in $L_{\rm FIR}$, meaning that it increases for decreasing $L_{\rm FIR}$." (7)
- None of the three simulations reproduces observed gas depletion; AGN hosts match or exceed non-active gas fractions  
  > "cosmological simulations suggest that AGN hosts should match or exceed non-active galaxies in gas fraction, which is the opposite of the observed trend" (7)

## Claim tuples

- H: AGN hosts are CO depleted at fixed FIR luminosity | E: Bayesian bisector fits of L'CO vs LFIR for AGN vs matched controls | R: Relations differ at 3 sigma | F: AGN hosts have reduced cold gas | **supported**
- H: Gas fraction distributions differ | E: Hierarchical Bayesian and KS test of L'CO/M* | R: KS p<1e-7, means differ at 2 sigma, AGN skewed low | F: AGN distribution skewed to lower values | **supported**
- H: Differences at fixed stellar mass | E: Bisector fits vs M* | R: <~2 sigma | F: Only hints at fixed M* | **partially**
- H: Simulations reproduce observed gas depletion | E: Compare TNG, EAGLE, Simba filtered samples | R: Simulations predict AGN hosts match or exceed gas fraction | F: Discrepancies with observations | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Use L'CO instead of alpha_CO-based masses to avoid conversion uncertainties  
  > "Our analysis remains free of the additional uncertainties inherent to the $\alpha_{\rm CO}$ conversion factor" (5)
- Alternative: Excluded cdfs_718 due to dust lane contaminating FIR emission  
  > "due to the presence of a dust lane as seen in HST data (cite: boogaard2019) that contaminates the FIR emission" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Different AGN and galaxy timescales, spatial scales, many upper limits, alpha_CO unknown  
  > "First, we are comparing two phenomena that occur on very different timescales" (7)
- Caveat (inferred, ours): Control-sample matching misses low-SFR galaxies at z>1.8
- Caveat (inferred, ours): About half of AGN have upper limits on LFIR; ~44% upper limits on both
- Caveat (inferred, ours): CO SLED assumed rather than measured
- Caveat (inferred, ours): SED-derived M* and SFR depend on AGN decomposition
- Caveat (inferred, ours): Heterogeneous archival data

## Reproducibility

- Data public (paper): Archival ALMA data; Zenodo for maps and spectra  
  > "Those of the rest of the sample are available on Zenodo at the following link: <https://doi.org/10.5281/zenodo.13149280>." (4.2)
- Products in archive: _not stated_
- Missing: PHIBSS CO fluxes were private communication
- Missing: MCMC settings
- Missing: Line-free channel choices
- Data volume (inferred): ~100-300 GB for 21 archival fields
- Score (inferred): 3/5, Archival ALMA data and many settings are stated, but control-sample data partly private and several processing details missing.
- Rediscovery candidate: no, Control sample partly private and the full pipeline is long; the main results depend on heavy SED fitting and a Bayesian hierarchical method.

## Links

- Method: (cite: circosta2021) (Bayesian framework and SUPER ALMA analysis)
- Method: (cite: kirkpatrick2019) (CO line ratios)
- Method: (cite: ward2022) (simulation comparison method)
- Companion: (cite: harrison2016) (KASHz survey)
- Companion: (cite: circosta2018) (SUPER survey)
- Related: KASHz
- Related: SUPER
- Related: PHIBSS
- Related: ASPECS

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 11,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 53,
  "rate": 0.596
 },
 "evidence_ok": true
}
```
