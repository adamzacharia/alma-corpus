# Rotation in [C II]-emitting gas in two galaxies at a redshift of 6.8

`2018Natur.553..178S` | Nature 2018 | first author: Smit, Renske | arXiv: 1706.04614 | DOI: 10.1038/nature24631

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Can [C II] 158um confirm spectroscopically near-IR selected normal star-forming galaxies at z~7, and what are their [C II] luminosities, dust content and velocity structure?  
  > "for the first time, measurement of the velocity structure, for two galaxies at $z=6.8540\pm0.0003$ and $z=6.8076\pm0.0002$." (abstract)
- Target **COS-3018555981**: coordinates RA 10:00:30.185, Dec +02:15:59.81  
  > "COS-3018555981 (R.A. = 10:00:30.185, decl. = +02:15:59.81)" (Data); z/distance z_[CII]=6.8540±0.0003 (z_phot 6.76±0.07)  
  > "COS-3018555981 (R.A. = 10:00:30.185, decl. = +02:15:59.81)" (Data); distance from [C II] line from ALMA  
  > "COS-3018555981 (R.A. = 10:00:30.185, decl. = +02:15:59.81)" (Data)
- Target **COS-2987030247**: coordinates RA 10:00:29.870, Dec +02:13:02.47  
  > "COS-2987030247 (R.A. = 10:00:29.870, decl. = +02:13:02.47)" (Data); z/distance z_[CII]=6.8076±0.0002 (z_phot 6.66±0.14)  
  > "COS-2987030247 (R.A. = 10:00:29.870, decl. = +02:13:02.47)" (Data); distance from [C II] line from ALMA  
  > "COS-2987030247 (R.A. = 10:00:29.870, decl. = +02:13:02.47)" (Data)

## Data provenance

- ALMA projects: 2015.1.01111.S
- bands: Band 6, ~241-245 GHz  
  > "Three tunings were requested to cover the frequency range 1870.74-1971.43 GHz in band 6" (Data)
- frequencies and spectral setup: three spectral windows of 1.875 GHz bandwidth, 4.95 GHz total in single sideband; one tuning executed covering z_[CII]=6.74-6.90  
  > "three spectral windows having a bandwidth of 1.875 GHz were used to cover a frequency range of 4.95 GHz in a single sideband." (Data)
- continuum bandwidth: _not stated_
- arrays: 36 antennas  
  > "The array consisted of 36 antennas" (Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.1"x0.7" (PA -48 deg), 5.8x3.7 kpc  
  > "The primary beam has a resolution of 1.1"$\times$0.7" (PA = $-$48$^{\circ}$) for both targets." (Data)
- max recoverable scale: _not stated_
- sensitivity: 0.32 mJy/beam at 243 GHz in 50 km/s channel  
  > "reached an image rms sensitivity of 0.32 mJy beam$^{-1}$ at 243 GHz in a 50 km/s channel in both pointings" (Data)
- time on source: 24 min per target  
  > "with 24 min on source integration time for each of the targets" (Data)
- observing dates: April 14, 2016 (Cycle 3)  
  > "on April 14, 2016, in Cycle-3" (Data)
- pi or archival as stated: Filler program, PI Smit  
  > "as part of a filler program (project code: 2015.1.01111.S, PI: Smit)" (Data)
- Line: [C II] 158 um (2P3/2-2P1/2) (lambda 157.74 um (frequency not stated))
- Other facility **HST**: WFC3/F160W imaging and photometry used for selection and UV slope  
  > "We also make use of the $HST$ imaging in the WFC3/F160W ($H_{160}$) and the photometry of these objects" (Data)
- Other facility **Spitzer/IRAC**: 3.6 and 4.5 um photometry used for selection and SED fitting  
  > "measured in the 3.6 and 4.5$\ensuremath{\mu}m$ *Spitzer* photometric bands" (abstract)
- External data: HST and Spitzer photometry, photometric redshifts and [OIII]+Hbeta equivalent widths of the targets  
  > "the photometry of these objects that was used in the selection of these galaxies in previous work(cite: Smit2015)" (Data) [from (cite: Smit2015)]

## Processing

### Calibration

- pipeline or manual: automated pipeline  
  > "using the automated pipeline" (Data)
- casa version: CASA 4.5.3  
  > "(CASA)(cite: McMullin2007) version 4.5.3" (Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN, no iterations  
  > "we imaged the data with the CLEAN task (no iterations as no continuum sources are detected in the data)" (Data)
- deconvolver: _not stated_
- weighting robust: natural weighting; test with Briggs robust 0.5 (0.9"x0.7")  
  > "using a natural weighting for optimal signal-to-noise" (Data); "using a Briggs weighting with a robustness parameter 0.5" (Velocity structure and dynamical mass)
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
- final beam: 1.1"x0.7" PA -48 deg  
  > "1.1"$\times$0.7" (PA = $-$48$^{\circ}$) for both targets" (Data)
- final rms: 0.32 mJy/beam per 50 km/s channel  
  > "image rms sensitivity of 0.32 mJy beam$^{-1}$ at 243 GHz in a 50 km/s channel" (Data)

### Inherited from earlier work

- Velocity-gradient rotation criterion and dynamical mass approximations  
  > "can be classified as likely rotation dominated systems in cases where the data quality prevents reliable kinematic modelling(cite: ForsterSchreiber2009)" (Velocity structure and dynamical mass) [from (cite: ForsterSchreiber2009)]
- Thin-disk velocity field modelling method  
  > "Our method has been successfully applied to ALMA observations of \[C II\] emitting sources at $z\sim5$ (cite: Carniani2013; Williams2014)." (Velocity structure and dynamical mass) [from (cite: Carniani2013; Williams2014)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, and spectral cube channelization
- Which channels were used for continuum averaging
- Exact aperture/mask definitions for 1D spectra and half-max extraction
- MCMC sampler, priors and chain settings of disk model
- Conversion from continuum limit to L_IR (rest frequency, CMB correction)
- MAGPHYS settings and priors

## Analysis recipe

1. **Calibrate and image**: Pipeline calibration in CASA, CLEAN with natural weighting  
  > "calibrated and reduced with the Common Astronomy Software Application (CASA)(cite: McMullin2007) version 4.5.3, using the automated pipeline" (Data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect [C II] and measure redshift and width**: Extract spectrum, line-averaged map, Gaussian fit; S/N from 9000 random aperture measurements; blind line search with delta chi2>25  
  > "we repeat this measurement 9000 times at randomly selected positions of the image, resulting in an estimated signal-to-noise ratio of 8.2" (Line detections)
   - software: CASA
   - fitting: Gaussian line fit  
  > "we fit a Gaussian to the observed line to determine a line centre of $241.97\pm0.01\,\rm GHz$" (Line detections)
   - validation: Blind search found no other >5 sigma sources; alternative lines excluded by photometric z  
  > "we find no other sources with a $>5\sigma$ detection in both the one-dimensional spectrum and the spectral line-averaged map" (Line detections)
3. **Dust continuum limit and IR luminosity**: Average line-free data, 3 sigma limit, grey body with beta_IR=1-2 and T_dust=20-60 K  
  > "we vary both the slope in the range $\beta_{\rm IR}=1-2$ and the dust temperatures in the range $T_{\rm dust}=20-60\,\rm K$" (Dust)
   - assumption: grey body, beta_IR 1-2, T_dust 20-60 K  
  > "assuming a grey body approximation for the dust continuum" (Dust)
   - fitting: _not stated_
   - validation: _not stated_
4. **SFR and stellar mass**: Kennicutt scaling relations for SFR; MAGPHYS+HIGHZ SED fit excluding 3.6um  
  > "We use the Bayesian code MAGPHYS(cite: daCunha2008) with the HIGHZ extension(cite: daCunha2015) to fit the stellar population." (Star formation rate and Stellar mass)
   - software: MAGPHYS
   - assumption: Chabrier IMF  
  > "we adopt a Chabrier(cite: Chabrier2003) initial mass function (IMF)" (Definitions)
   - fitting: _not stated_
   - validation: _not stated_
5. **Velocity field and dynamical mass**: Per-pixel Gaussian fits (>5 sigma) for velocity gradient; estimates via Forster Schreiber approximation and thin exponential disk model fit with least squares and MCMC uncertainties  
  > "Our free parameters are simultaneously constrained from the velocity maps using least-squared fitting." (Velocity structure and dynamical mass)
   - software: CASA
   - assumption: symmetric rotating circularly symmetric thin disk with exponential mass density  
  > "We will assume that these galaxies can be described by symmetric rotating disks." (Velocity structure and dynamical mass)
   - fitting: least-squares with MCMC for uncertainties; free: inclination, PA, systemic velocity, dynamical mass within 5 kpc  
  > "We estimate uncertainties from the $\chi^2$ parameter space, which is constrained with Monte Carlo Markov chain simulations." (Velocity structure and dynamical mass)
   - validation: Robust 0.5 re-imaging gives same gradient; two mass methods agree  
  > "These values are all consistent within the uncertainties with our estimates derived in the previous section." (Velocity structure and dynamical mass)

## Software

- **CASA** 4.5.3: Calibration, imaging, ellipse fits to line maps  
  > "(CASA)(cite: McMullin2007) version 4.5.3" (Data)
- **MAGPHYS** : SED fit for stellar mass  
  > "We use the Bayesian code MAGPHYS(cite: daCunha2008) with the HIGHZ extension(cite: daCunha2015)" (Star formation rate and Stellar mass)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| z_[CII] COS-3018555981 | 6.8540 | 0.0003 | dimensionless | 2 | 6.8540$\pm$0.0003 |
| z_[CII] COS-2987030247 | 6.8076 | 0.0002 | dimensionless | 2 | 6.8076$\pm$0.0002 |
| L_[CII] (COS-3018555981, COS-2987030247) | 4.7, 3.6 | 0.5, 0.5 | 1e8 Lsun | 2 | 4.7$\pm$0.5 / 3.6$\pm$0.5 |
| FWHM [CII] | 232, 124 | 30, 18 | km/s | 2 | 232$\pm$30 / 124$\pm$18 |
| L_IR 3sigma upper limits | <1.3, <1.1 | not stated | 1e11 Lsun | 3 | We derive a 3$\sigma$ upper limit on the IR luminosity of 1.3 and 1.1$\times10^{11}\,L_\odot$ |
| Projected velocity difference | 111, 54 | 28, 20 | km/s | 5 | $111\pm28$ and $54\pm20$ $\rm km\,s^{-1}$ |
| Delta v_obs/2 sigma_tot | 0.57, 0.52 | 0.16, 0.21 | dimensionless | 5 | $0.57\pm0.16$ / $0.52\pm0.21$ |
| M_dyn (disk model) | 1.0e10, 0.4e10 | +0.3/-0.2, +0.9/-0.3 | Msun | 5 | dynamical masses of $1.0_{-0.2}^{+0.3}$ and $0.4_{-0.3}^{+0.9}\times 10^{10} \, M_\odot$ |
| [CII] half-light radius | 2.6, 3.1 | 0.8, 1.0 | kpc | 5 | $2.6\pm0.8$ / $3.1\pm1.0$ |
| Stellar mass | 1.4, 1.7 | +0.7/-0.2, +0.5/-0.2 | 1e9 Msun | 4 | $1.4_{-0.2}^{+0.7}$ / $1.7_{-0.2}^{+0.5}$ |

## Qualitative findings

- Targets are not [CII]-deficient, unlike Lyα-selected z>6.5 galaxies; consistent with local SFR-L[CII] relation  
  > "the \[C II\] line luminosity from these galaxies is higher than previously found in ‘normal’ star-forming galaxies at $z>6.5$" (abstract)

## Claim tuples

- H: Near-IR selected z~7 galaxies can be confirmed via [C II] | E: ALMA band 6 spectral scan of two LBGs | R: Lines at 241.97 and 243.42 GHz, S/N 8.2 and 5.1 | F: First ALMA [C II] confirmation of normal star-forming galaxies at z>6 | **supported**
- H: The galaxies have low dust content | E: Continuum upper limits and IRX-beta | R: SFR_IR<16-19 Msun/yr | F: Below Meurer relation; steeper attenuation curve like SMC likely | **supported**
- H: The [CII] velocity gradients indicate rotation | E: Pixel-wise Gaussian fits and disk model | R: Delta v/2sigma 0.57 and 0.52 >0.4 | F: Consistent with rotation-dominated disks but merger or outflow not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple velocity-gradient criterion used because data quality prevents reliable kinematic modelling  
  > "in cases where the data quality prevents reliable kinematic modelling" (Velocity structure and dynamical mass)
- Alternative: [O I] 63um, [O III] 88um and [O I] 145um identifications rejected by photometric redshifts  
  > "are inconsistent with the $HST$ photometry of this source" (Line detections)
- How they decided it was enough: _not stated_
- Limitation (authors): Low angular resolution allows merger, outflow or inflow interpretations; turbulence could raise dynamical mass  
  > "Given the low angular resolution of the observations, there are various ways to interpret these velocity gradients." (abstract)
- Caveat (inferred, ours): Only ~1 beam across source; gradients may be beam-smeared mergers
- Caveat (inferred, ours): Low S/N (5.1) for COS-2987030247 near atmospheric feature
- Caveat (inferred, ours): Dynamical mass from sin(i) poorly constrained

## Reproducibility

- Data public (paper): Data and pipeline available from ALMA archive  
  > "The reduction pipeline for this source can be downloaded as part of the ALMA observations with project code 2015.1.01111.S" (Code availability)
- Products in archive: _not stated_
- Code: Kinematic models available on request only  
  > "The kinematic models used for this study are available from the corresponding author upon request." (Code availability)
- Missing: Imaging cell/image size and cube channelization
- Missing: Disk model code and priors
- Missing: MAGPHYS configuration
- Data volume (inferred): ~ few GB (single short Band 6 execution)
- Score (inferred): 3/5, Public small dataset and key methods stated, but imaging parameters and model code missing.
- Rediscovery candidate: yes, Public data, simple recipe, numeric line detections and redshifts.

## Links

- Method: (cite: ForsterSchreiber2009) (Rotation-dominance criterion and dynamical mass approximation)
- Method: (cite: Carniani2013; Williams2014) (Thin disk velocity-field modelling)
- Companion: (cite: Smit2015) (Source selection and photometry)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
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
  "facts": 75,
  "stated": 46,
  "rate": 0.613
 },
 "evidence_ok": true
}
```
