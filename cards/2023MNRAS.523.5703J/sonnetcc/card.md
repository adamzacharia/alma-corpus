# Double SSA spectrum and magnetic field strength of the FSRQ 3C 454.3

`2023MNRAS.523.5703J` | Monthly Notices of the Royal Astronomical Society 2023 | first author: Jeong, Hyeon-Woo | arXiv: 2306.04888 | DOI: 10.1093/mnras/stad1736

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Radio spectral variability of blazar 3C 454.3 (3-340 GHz): are there two SSA components, where are they located, and what are their magnetic field strengths?  
  > "In this paper, we present a detailed analysis of radio flux and spectral variability of a blazar, 3C454.3, to understand the B-field properties of the emission region(s)." (1 Introduction)
- Target **3C 454.3**: coordinates _not stated_; z/distance z = 0.859; D_L = 5489 Mpc  
  > "The redshift of the source is known to be $z=0.859$ (cite: jackson1991), resulting in a luminosity distance of the source is $D_{\rm L} = 5489~{\rm Mpc}$." (1 Introduction); distance from z from (cite: jackson1991); cosmology (cite: komatsu2009)  
  > "The redshift of the source is known to be $z=0.859$ (cite: jackson1991), resulting in a luminosity distance of the source is $D_{\rm L} = 5489~{\rm Mpc}$." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.01234.S
- bands: _not stated_
- frequencies and spectral setup: ALMA flux densities at 91, 103, 233, 337 and 343 GHz; mean cadences 17, 17, 130, 26 and 32 days  
  > "we obtained the multi-wavelength data at 91, 103, 233, 337, and 343 GHz." (2.7 ALMA Data); "The mean cadences were 17, 17, 130, 26, and 32 days, respectively." (2.7 ALMA Data)
- continuum bandwidth: _not stated_
- arrays: ALMA, 66 antennas (general description)  
  > "The Atacama Large Millimeter/submillimeter Array (ALMA) consists of 66 antennas operating at 84 – 950 GHz in the Atacama desert, Chile." (2.7 ALMA Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: MJD 56010 to MJD 57385  
  > "This work used the ALMA data from MJD 56010 to MJD 57385." (2.7 ALMA Data)
- pi or archival as stated: Public ALMA Calibrator Source Catalogue (3C 454.3 observed as a calibrator)  
  > "The ALMA data are available at the ALMA Calibrator Source Catalogue, found at https://almascience.eso.org/sc/." (DATA AVAILABILITY)
- Other facility **Effelsberg 100 m (F-GAMMA)**: Single-dish flux densities at 2.64-43 GHz, taken from the published F-GAMMA data  
  > "We used the F-GAMMA data obtained at 2.64 – 43 GHz, published by (cite: angelakis2019)." (2.1 F-GAMMA Data)
- Other facility **OVRO 40 m**: 15 GHz single-dish light curve, Jan 2012 to Dec 2015  
  > "We used this data from January 2012 to December 2015 (MJD 55932 – 57383)." (2.2 OVRO Data)
- Other facility **CARMA (MARMOT)**: 94.75 GHz monitoring flux densities  
  > "The source 3C 454.3 was monitored with a mean cadence of $\sim6$ day at a center frequency of 94.75 GHz" (2.3 CARMA Data)
- Other facility **SMA**: 1.3 mm (225 GHz) and 850 micron (343 GHz) calibrator flux densities  
  > "We used the SMA data in the period of MJD 55935 – 57384." (2.4 SMA Data)
- Other facility **KVN single dish**: 22 and 43 GHz flux densities, reduced with GILDAS-CLASS  
  > "This work uses the KVN single-dish data obtained at 22 and 43 GHz during MJD 55928 – 57284." (2.5 KVN Observations and Data Reduction)
- Other facility **EVN**: Pipeline-calibrated ~5 GHz data used to model the low-frequency core and component sizes  
  > "data of 3C 454.3 observed at $\rm \sim5~GHz$ to estimate the size of the low-frequency radio core." (2.6 EVN Data)
- Other facility **VLBA (MOJAVE, VLBA-BU-BLAZAR, NRAO archive)**: 15 and 43 GHz monitoring UVFITS plus additional archival 22/43 GHz epochs  
  > "The VLBA data is provided on the website in the form of UVFITS." (2.8 VLBA Data)
- Other facility **GMVA**: Calibrated 86 GHz data from September 2015 for jet structure  
  > "This work used the calibrated GMVA data observed in September 2015." (2.9 GMVA Data)
- External data: F-GAMMA flux densities at 2.64-43 GHz  
  > "We used the F-GAMMA data obtained at 2.64 – 43 GHz, published by (cite: angelakis2019)." (2.1 F-GAMMA Data) [from (cite: angelakis2019)]
- External data: Doppler factors of jet components (means for components beyond and within 0.4 mas)  
  > "which are the mean values of components $\Delta r>0.4~{\rm mas}$ and $\Delta r\leq0.4~{\rm mas}$, respectively" (3.3 Magnetic Field Strength Estimation) [from (cite: jorstad2005; jorstad2017; weaver2022)]
- External data: SMBH mass 3.4e9 Msun  
  > "The source 3C 454.3 hosts a supermassive black hole (SMBH) with a mass of $3.4\times10^{9}~{\rm M}_{\odot}$ (cite: titarchuk2020)." (1 Introduction) [from (cite: titarchuk2020)]
- External data: Viewing angle 1.3 deg  
  > "by adopting the viewing angle $\theta_{\rm v}\approx1.3^{\circ}$ (cite: jorstad2005)" (3.5 Jet Ridgeline Analysis) [from (cite: jorstad2005)]
- External data: Core-shift parameters Omega = 43 pc GHz^(1/k), k = 0.7 for jet geometry  
  > "Following (cite: kutkin2014), we adopt $\Omega=43\pm10~{\rm pc \, GHz}^{1/k}$, $k=0.7$ and $\theta=1.3^{\circ}$." (7 Jet Geometry) [from (cite: kutkin2014)]
- External data: Proper motion of component K14 (0.471 and 0.466 mas/yr)  
  > "The proper motion of K14 resulted in as $\rm 0.471\pm0.003~mas/yr$ (cite: liodakis2020) and $\rm 0.466\pm0.002~mas/yr$ (cite: weaver2022)." (4.2 Location of SSA Emitting Regions) [from (cite: liodakis2020); (cite: weaver2022)]
- External data: Redshift z = 0.859  
  > "The redshift of the source is known to be $z=0.859$ (cite: jackson1991)" (1 Introduction) [from (cite: jackson1991)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA flux densities taken from the public calibrator catalogue; no ALMA reduction described  
  > "Since 3C 454.3 is one of the calibrators for the ALMA observations, we obtained the multi-wavelength data at 91, 103, 233, 337, and 343 GHz." (2.7 ALMA Data)
- flux calibrator: _not stated_
- flux scale uncertainty: ~2.5 % typical fractional measurement error (ALMA)  
  > "The typical fractional measurement error in the frequency range was $\sim2.5~\%$." (2.7 ALMA Data)
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

- Flare decomposition model with decay-to-rise ratio fixed at 1.3  
  > "We used a 1.3 ratio of decaying to rising timescales by following (cite: valtaoja1999) and found good fitting results with the fixed ratio." (3.1 Quiescent Flux Density Determination) [from (cite: valtaoja1999)]
- SSA spectrum model (Equation 4)  
  > "The SSA spectrum model was introduced by (cite: turler1999) as follows" (3.2 SSA Spectra Fitting) [from (cite: turler1999)]
- B_SSA formula for a uniform sphere  
  > "Following (cite: marscher1983), the magnetic field strength ($B_{\rm SSA}$) of an SSA region is estimated, assuming a uniform sphere" (3.3 Magnetic Field Strength Estimation) [from (cite: marscher1983)]
- Equipartition field B_EQ formula  
  > "following (cite: kataoka&stawarz2005), who estimated the magnetic field strength ($B_{\rm EQ}$) under an equipartition condition" (3.3 Magnetic Field Strength Estimation) [from (cite: kataoka&stawarz2005)]
- Model-fit uncertainties of VLBI components  
  > "The errors in the models were determined using residual r.m.s. noise level following (cite: fomalont1999)." (3.4 Milli-arcsecond Scale Structures) [from (cite: fomalont1999)]
- Jet width uncertainties along the ridgeline  
  > "The uncertainties of the jet width along the jet ridgeline were calculated by following (cite: pushkarev2017)." (3.5 Jet Ridgeline Analysis) [from (cite: pushkarev2017)]
- GMVA data reduction  
  > "The data reduction procedures for the GMVA data are described in (cite: casadio2019)." (2.9 GMVA Data) [from (cite: casadio2019)]
- Core-shift based jet geometry parameters and VLBA data set for core sizes  
  > "We reduced the same VLBA data that was used in (cite: kutkin2014) to obtain core sizes with their uncertainties." (7 Jet Geometry) [from (cite: kutkin2014)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA calibrator-catalogue flux densities per epoch and band (values, dates and the band-to-frequency mapping); the paper only lists central frequencies and cadences and no flux table
- Which ALMA flux densities were excluded or combined when binning to 30-day epochs
- emcee settings for the flare decomposition (walkers, steps, priors, burn-in) and the sampler or optimiser used for the SSA fits
- Final fitted flare parameters (S_max, t_max, t_r) at each frequency
- b(alpha) value actually used per epoch (only the range 1.8-3.8 is given)
- Doppler factor and angular-size assignment rule per epoch and the jet-geometry fit procedure details (priors, sampler)
- How KVN, VLBA, EVN and GMVA data selections and flagging were done in detail (DIFMAP parameters, weighting for VLBA, self-cal intervals)
- Per-epoch flux densities of the other single-dish data (OVRO, CARMA, KVN, SMA, F-GAMMA) as used, since some data are only available on request

## Analysis recipe

1. **Collect and bin multi-frequency light curves**: Bin each frequency light curve into 30-day epochs using weighted means  
  > "we binned the data at each frequency with a bin size of 30 days (i.e., the largest cadence)." (2 Multi-wavelength Data); "all measurements in the epoch and at each frequency were averaged to obtain a weighted mean." (2 Multi-wavelength Data)
   - parameter: 30-day bins  
  > "we binned the data at each frequency with a bin size of 30 days (i.e., the largest cadence)." (2 Multi-wavelength Data)
   - fitting: _not stated_
   - validation: Noted that variability shorter than 30 days could be lost; shorter bins would leave too few points for double-SSA fitting  
  > "We note that some information could be lost because of binning if variability is shorter than 30 days." (3.2 SSA Spectra Fitting)
2. **Decompose light curves into flares and derive quiescent spectrum**: Fit successive exponential flares to the light curve until residual peaks are below 3 sigma, then fit a power law to the quiescent fluxes at 3, 5, 15 and 225 GHz  
  > "we used an exponential flare model to decompose the light curve." (3.1 Quiescent Flux Density Determination); "The quiescent spectrum of the source was fitted to a simple power-law model ($F(\nu)=C_{\rm q}\nu^{\alpha}$)." (3.1 Quiescent Flux Density Determination)
   - software: emcee
   - parameter: Stop when peak residual <= 3 sigma_rms  
  > "(i.e., a peak residual flux density $\leq 3 \times \sigma_{\rm rms}$, where $\sigma_{\rm rms}$ is the r.m.s. noise level of a light curve)" (3.1 Quiescent Flux Density Determination)
   - parameter: Decay/rise timescale ratio fixed at 1.3  
  > "We used a 1.3 ratio of decaying to rising timescales by following (cite: valtaoja1999) and found good fitting results with the fixed ratio." (3.1 Quiescent Flux Density Determination)
   - parameter: Light curves at 15 and 225 GHz (plus 3 and 5 GHz) used for the quiescent spectrum  
  > "We selected light curves at 15 and 225 GHz to estimate the quiescent spectrum of the source" (3.1 Quiescent Flux Density Determination)
   - assumption: Quiescent emission is optically thin and described by a single power law  
  > "A broken power-law model diverges when used to fit the observed minimum flux densities." (3.1 Quiescent Flux Density Determination)
   - fitting: MCMC (emcee) for flare models; priors and likelihood not stated  
  > "which is an implementation of the Markov Chain Monte Carlo (MCMC)." (3.1 Quiescent Flux Density Determination)
   - validation: Number of flares chosen by reduced chi-squared and BIC minimum  
  > "and then estimated both reduced-$\chi^2$ and Bayesian information criterion (BIC) value to select the most statistically reasonable total number of flares." (3.1 Quiescent Flux Density Determination)
3. **Fit double SSA spectra to quiescent-subtracted spectra**: Subtract quiescent spectrum, then fit two SSA components (LSS and HSS) per 30-day epoch  
  > "In this work, we fitted the variable spectra with two SSA models rather than three or more models due to the lack of data points." (3.2 SSA Spectra Fitting); "After binning, the quiescent spectrum was subtracted from the light curves." (3.2 SSA Spectra Fitting)
   - parameter: alpha_thick fixed at 2.5  
  > "In this work, we fixed $\alpha_{\rm thick}$=$2.5$" (3.2 SSA Spectra Fitting)
   - parameter: alpha_thin limited to -3 to 0; nu_m bounds 0.1-10 GHz (LSS) and 10-200 GHz (HSS) for first epoch  
  > "$\alpha_{\rm thin}$ was limited from -3 to 0, and $\nu_{\rm m}$ was constrained from $\rm 0.1-10~GHz$ and $\rm 10-200~GHz$ for the LSS and the HSS, respectively." (3.2 SSA Spectra Fitting)
   - parameter: At ~340 GHz the flux density extrapolated from the quiescent spectrum was used  
  > "At $\rm \sim340~GHz$, we used the flux density extrapolated from the obtained quiescent spectrum." (3.2 SSA Spectra Fitting)
   - assumption: Only the HSS modelled when 3 GHz data are missing or comparable to the quiescent uncertainty  
  > "only the single SSA model (i.e., HSS) was used because the $\nu_{\rm m}$ of the LSS could not be determined appropriately." (3.2 SSA Spectra Fitting)
   - fitting: _not stated_
   - validation: Single SSA model compared and rejected for late 2014 because it failed to fit flattening at high frequency  
  > "a single SSA model failed to fit the observed spectra properly due to the flattening in high frequency." (3.2 SSA Spectra Fitting)
4. **Model jet geometry to get SSA region sizes**: Fit a broken power law of core width versus de-projected distance from multi-frequency VLBA core sizes, then interpolate theta_FWHM at nu_m  
  > "The angular size of SSA regions, $d_{\rm m}$, can be interpolated (or extrapolated) from the model-fitted angular size of the radio core by using the jet geometry of the source." (7 Jet Geometry)
   - software: DIFMAP
   - parameter: Omega = 43 +/- 10 pc GHz^(1/k), k = 0.7, theta = 1.3 deg  
  > "Following (cite: kutkin2014), we adopt $\Omega=43\pm10~{\rm pc \, GHz}^{1/k}$, $k=0.7$ and $\theta=1.3^{\circ}$." (7 Jet Geometry)
   - assumption: Core-shift relation of Lobanov (1998) for core position versus frequency  
  > "the de-projected distance of a radio core at frequency $\nu$ is estimated by using the equation (cite: lobanov1998)" (7 Jet Geometry)
   - fitting: _not stated_
   - validation: Transition point compared with Kovalev et al. 2020 (10^5-10^6 r_g)  
  > "This result is consistent with that estimated by (cite: kovalev2020)." (7 Jet Geometry)
5. **Estimate magnetic field strengths (SSA and equipartition)**: B_SSA from S_m, nu_m, d_m = 1.8 theta_FWHM and Doppler factor; B_EQ from the Kataoka and Stawarz formula for leptonic and hadronic cases  
  > "where $d_{\rm m}=1.8 \times \theta_{\rm FWHM}$ is the size of the SSA region at $\nu_{\rm m}$." (3.3 Magnetic Field Strength Estimation); "In this work, we used two pure cases (i.e., leptonic and hadronic) to estimate the field strengths." (3.3 Magnetic Field Strength Estimation)
   - parameter: delta_LSS = 20.3 +/- 1.8, delta_HSS = 28.6 +/- 2.1  
  > "We adopted $\delta_{\rm LSS}=20.3\pm1.8$ and $\delta_{\rm HSS}=28.6\pm2.1$ as the Doppler factors" (3.3 Magnetic Field Strength Estimation)
   - parameter: b(alpha) can vary from 1.8 to 3.8  
  > "The factor $b(\alpha)$ can vary from 1.8 to 3.8 (cite: marscher1983)." (3.3 Magnetic Field Strength Estimation)
   - assumption: Uniform spherical emitting region; radio core and component C in a steady state  
  > "because we assume both the radio core and the component C are in a steady state rather than exhibiting a moving feature" (3.3 Magnetic Field Strength Estimation)
   - assumption: Cosmology Omega_M=0.27, Omega_Lambda=0.73, H0=71; z=0.859  
  > "Throughout this paper, we adopt the cosmological parameters $\Omega_M = 0.27$, $\Omega_{\Lambda} = 0.73$" (1 Introduction)
   - fitting: _not stated_
   - validation: B_SSA compared with B_EQ to infer magnetic or particle dominance  
  > "These indicate that the LSS region possibly deviates from an equipartition condition." (3.3 Magnetic Field Strength Estimation)
6. **Model-fit VLBI data to locate SSA regions**: Imaging in DIFMAP with uniform weighting and Gaussian model fitting of EVN 5 GHz and VLBA 43 GHz data, compared with SSA-inferred flux densities  
  > "In the imaging, we used uniform weight rather than natural weight to focus on the core region." (2.6 EVN Data); "we model-fitted the EVN 5 GHz and the VLBA 43 GHz data with circular Gaussian models." (3.4 Milli-arcsecond Scale Structures)
   - software: DIFMAP, AIPS
   - parameter: Add Gaussians until peak residual below three times the r.m.s. noise  
  > "repeated the processes until the peak residual intensity was lower than three times the r.m.s. noise level." (2.6 EVN Data)
   - fitting: Iterative Gaussian modelfit until reduced chi-squared stops changing  
  > "The initial models were then fitted until no reduced-$\chi^2$ value change appeared." (2.6 EVN Data)
   - validation: Model errors from residual r.m.s. following Fomalont (1999)  
  > "The errors in the models were determined using residual r.m.s. noise level following (cite: fomalont1999)." (3.4 Milli-arcsecond Scale Structures)
7. **Jet ridgeline and width analysis**: Select brightest pixel per radial interval, slice transversely and fit Gaussians to get jet width and brightness; deconvolve beam  
  > "We used radial coordinates to find the jet ridgeline and selected one pixel with the highest brightness in every radial distance interval from the core." (3.5 Jet Ridgeline Analysis); "The convolution effect of the restoring beam can be removed by deconvolving the FWHM of the restoring beam from a fitted Gaussian FWHM" (3.5 Jet Ridgeline Analysis)
   - parameter: 10-sigma threshold on peak brightness; sigma about 6 mJy at 43 GHz and 3 mJy at 86 GHz  
  > "we dropped fit results if the peak brightness was lower than 10-$\sigma$ level, $\sigma_{\rm 43GHz} \approx {\rm 6~mJy}$, and $\sigma_{\rm 86GHz} \approx {\rm 3~mJy}$)." (3.5 Jet Ridgeline Analysis)
   - assumption: Viewing angle 1.3 deg and M_SMBH = 3.4e9 Msun for de-projected distance  
  > "adopting the viewing angle $\theta_{\rm v}\approx1.3^{\circ}$ (cite: jorstad2005)" (3.5 Jet Ridgeline Analysis)
   - fitting: Gaussian fit to each transverse slice; priors not stated  
  > "The obtained brightness profile from every slice was fitted to a Gaussian model to estimate jet width and peak brightness." (3.5 Jet Ridgeline Analysis)
   - validation: Two quasi-simultaneous observations (43 and 86 GHz) compared for robustness  
  > "therefore providing robustness to the analysis by allowing a comparison of the two results." (3.5 Jet Ridgeline Analysis)
8. **Compute brightness temperatures**: Observed T_B from S, theta_FWHM and nu; intrinsic T_B = (1+z) T_B,obs / delta  
  > "$T_{\rm B, int} = (1+z) \, T_{\rm B, obs} / \delta_{\rm LSS} \approx (4-15)\times10^{9}~{\rm K}$" (5.1 Interpretations of Magnetic Field Strength and Brightness Temperature)
   - parameter: delta = 28.8 +/- 2.2 for K14 (typical Doppler factor)  
  > "By adopting the typical Doppler factor of 3C 454.3 as $\delta = 28.8\pm2.2$ (cite: weaver2022)" (5.1 Interpretations of Magnetic Field Strength and Brightness Temperature)
   - fitting: _not stated_
   - validation: Compared with equipartition and inverse-Compton limits  
  > "which is close to the inverse-Compton limit." (5.1 Interpretations of Magnetic Field Strength and Brightness Temperature)
9. **Stack 43 GHz polarization maps**: Align 38 VLBA 43 GHz maps on the core, convolve with a common beam, stack Stokes I, Q and U, derive polarization intensity and degree of polarization  
  > "we stacked the 38 VLBA 43 GHz data observed between 2013 and 2016 and recorded in dual-polarization mode." (3.6 Stacking the 43 VLBI Maps); "Before stacking the maps, all were aligned by setting the core position to (0,0)." (3.6 Stacking the 43 VLBI Maps)
   - parameter: Common circular beam 0.2 x 0.2 mas^2  
  > "Aligned maps were then convolved with a common circular restoring beam, whose size was $\rm 0.2 \times 0.2~mas^{2}$." (3.6 Stacking the 43 VLBI Maps)
   - assumption: Core-shift between 22 and 43 GHz cores (~0.05 mas) treated as negligible for alignment  
  > "we assumed the core-shift on the 43 GHz core was negligible based on the small offset between 22 and 43 GHz" (3.6 Stacking the 43 VLBI Maps)
   - fitting: _not stated_
   - validation: Checked that high core DP/polarization is seen in individual epochs, not only in the stack  
  > "Those polarimetric characteristics are seen in most individual epochs" (4.3 Time-averaged Characteristics in Jet)

## Software

- **emcee** : MCMC fitting of exponential flare models to light curves  
  > "which is an implementation of the Markov Chain Monte Carlo (MCMC)." (3.1 Quiescent Flux Density Determination)
- **GILDAS-CLASS** : Calibrating KVN single-dish scans and computing flux densities  
  > "software to calibrate and calculate the source’s flux density." (2.5 KVN Observations and Data Reduction)
- **DIFMAP** : Imaging and Gaussian model fitting of EVN and VLBA data  
  > "The CLEAN image was obtained after repetitive CLEAN and self-calibration processes." (2.6 EVN Data)
- **AIPS** : Calibration of additional VLBA archive data (VLBAEOPS, VLBATECR, FRING, BPASS)  
  > "Amplitude calibration was performed using the observed gain curves and system temperatures." (2.8 VLBA Data)
- **Astropy** : Acknowledged general-purpose Python package  
  > "a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Quiescent flux density at 3, 5, 15, 225 GHz | 10.2; 7.85; 4.47; 1.2 | 0.11; 0.06; 0.07; 0.02 | Jy | 2 | The estimated quiescent fluxes were $\rm 10.2\pm0.11~Jy$ (3 GHz), $\rm 7.85\pm0.06~Jy$ (5 GHz), $\rm 4.47\pm0.07~Jy$ (15 GHz) and $\rm 1.2\pm0.02~Jy$ (225 GHz). |
| Quiescent power-law normalisation C_q and index alpha | C_q = 16.66 Jy; alpha = -0.48 | C_q +/- 0.07 Jy; alpha very small (not quantified) | Jy; dimensionless | 2 | The model parameters resulted in $C_{\rm q}=16.66\pm0.07~{\rm Jy}$ and $\alpha=-0.48$ with very small uncertainty. |
| LSS turnover frequency range | 3-37 | not stated | GHz | 3 | The one SSA had a relatively low turnover frequency ($\nu_{\rm m}$) in the range of $\rm 3-37~GHz$ (lower $\nu_{\rm m}$ SSA spectrum, LSS) |
| HSS turnover frequency range | 55-124 | not stated | GHz | 3 | and the other one had a relatively high $\nu_{\rm m}$ of $\rm 55-124~GHz$ (higher $\nu_{\rm m}$ SSA spectrum, HSS). |
| B_SSA lower limits for LSS and HSS (abstract) | >7 (LSS); >0.2 (HSS) | lower limits | mG | 5 | The estimated magnetic field strengths were $\rm >7~mG$ and $\rm >0.2~mG$ for the LSS and HSS, respectively. |
| B_SSA,HSS range versus B_EQ,HSS range | B_SSA,HSS 0.2-7 mG; B_EQ,HSS 27-1200 mG | not stated | mG | 5 | most of the estimated $B_{\rm SSA, HSS}~{\rm (0.2-7~mG)}$ is lower than $B_{\rm EQ, HSS}~{\rm (27-1200~mG)}$ |
| B_SSA,LSS before June 2014 flare versus B_EQ,LSS | B_SSA,LSS > 37 mG; B_EQ,LSS 1-25 mG | lower limit | mG | 5 | the estimated $B_{\rm SSA, LSS}~(\rm > 37~mG)$ was higher than $B_{\rm EQ, LSS}~(\rm 1-25~mG)$ |
| Jet geometry indices epsilon_1, epsilon_2 and transition distance r_t | epsilon_1 = 0.35; epsilon_2 = 1.32; r_t = 79 pc | +0.09/-0.10; +0.30/-0.15; +33/-15 pc | dimensionless; dimensionless; pc | 4 | The fit parameters resulted in $\epsilon_{1}=0.35^{+0.09}_{-0.10}$, $\epsilon_{2}=1.32^{+0.30}_{-0.15}$, $r_{\rm t}=79^{+33}_{-15}~{\rm pc}$. |
| Transition distance in gravitational radii | 2.4e5 | not stated | r_g | 4 | $r_{\rm t}$ is converted into $2.4 \times 10^5~r_{\rm g}$. |
| Proper motion of K14 from modelfit | 0.47 | 0.01 | mas/yr | 6 | yielding $\rm 0.47\pm0.01~mas/yr$. |
| De-projected distance of component C | ~6e5 | not stated | r_g | 7 | The calculated de-projected distance was $\sim6\times10^{5}~r_{\rm g}$. |
| Observed brightness temperature of LSS before gamma-2014 flare | (4-16)e10 | not stated | K | 8 | the observed brightness temperatures $T_{\rm B, obs}$ were estimated to be $(4-16)\times10^{10}~{\rm K}$. |
| Intrinsic brightness temperature of component C (LSS) | (4-15)e9 | not stated | K | 8 | $T_{\rm B, int} = (1+z) \, T_{\rm B, obs} / \delta_{\rm LSS} \approx (4-15)\times10^{9}~{\rm K}$ |
| Intrinsic brightness temperature of K14 around gamma-2015 flare | 7.0e11 | 1.0e11 | K | 8 | $T_{\rm B, int} \approx (7.0\pm1.0) \times 10^{11}~{\rm K}$ from the jet component after the 2015 August $\gamma$-ray flare |
| Linear polarization and DP of component C versus core (stacked 43 GHz map) | C: ~200 mJy/beam, ~8 %; core: ~30 mJy/beam, ~1 % | not stated | mJy/beam; percent | 9 | The obtained linear polarization intensity and DP are higher in component C ($\rm \sim200~mJy/beam$, $\sim8\%$) than at the core ($\rm \sim30~mJy/beam$, $\sim1\%$). |
| Turnover frequency of component C in January 2016 | ~22 | not stated | GHz | 6 | Component C had a $\nu_{\rm m}$ at $\sim$22 GHz in January 2016. |

## Qualitative findings

- A decrease in jet width is found near the quasi-stationary component C (~0.6 mas), with local brightness maximum  
  > "The jet ridgeline analysis showed a local minimal jet width and a local maximal brightness near component C" (3.5 Jet Ridgeline Analysis)
- K14 flux density rises while its angular size shrinks as it approaches component C  
  > "As a moving component, K14 approached component C, and the flux density of the component was enhanced while the angular size decreased." (abstract)

## Claim tuples

- H: Does the 3-340 GHz spectrum of 3C 454.3 contain more than one SSA component? | E: Subtracted a quiescent power-law spectrum and fitted 30-day binned spectra with one or two SSA models | R: Two SSA spectra: LSS with nu_m 3-37 GHz and HSS with nu_m 55-124 GHz | F: The quiescent-subtracted spectrum shows two individual SSA features | **supported**
- H: Where are the LSS and HSS emitting regions? | E: Compared SSA-inferred flux densities with VLBI model-fit flux of core, jet components and component C, plus VLBA spectra of C | R: HSS tracks the 43 GHz core; LSS tracks component C before the 2014 flare and K14 after | F: HSS is the 43 GHz core and LSS is component C (then K14) | **supported**
- H: Is the LSS emitting region magnetically dominated? | E: Compared B_SSA to B_EQ (leptonic and hadronic) for each epoch | R: B_SSA,LSS exceeds B_EQ,LSS before the June 2014 flare, while B_SSA,HSS is below B_EQ,HSS | F: LSS region magnetically dominated before the June 2014 flare; HSS particle dominated | **supported**
- H: Does K14 reach the inverse-Compton limit near component C? | E: Computed T_B,obs of K14 from VLBA modelfit and converted with delta = 28.8 | R: T_B,int approx (7.0 +/- 1.0)e11 K near MJD 57287 | F: Efficient energy loss to gamma-ray production in component C | **supported**
- H: Is there a recollimation shock in component C? | E: Jet ridgeline width and brightness at 43 and 86 GHz; K14 size and flux evolution | R: Local minimum jet width and re-brightening near 0.6 mas | F: A recollimation shock is suggested in component C | **partially**

## Reasoning

- Why this data: Radio multi-wavelength data are needed to measure the flux density at the turnover frequency for SSA-based B-field estimates  
  > "Therefore, radio multi-wavelength data is essential for measuring magnetic field strength using the SSA effect." (1 Introduction)
- Why this method: Two SSA components were used instead of three or more because of too few data points  
  > "In this work, we fitted the variable spectra with two SSA models rather than three or more models due to the lack of data points." (3.2 SSA Spectra Fitting)
- Alternative: Broken power-law quiescent spectrum rejected  
  > "A broken power-law model diverges when used to fit the observed minimum flux densities." (3.1 Quiescent Flux Density Determination)
- Alternative: Single SSA model rejected for late 2014 spectra  
  > "a single SSA model failed to fit the observed spectra properly due to the flattening in high frequency." (3.2 SSA Spectra Fitting)
- How they decided it was enough: Number of flares chosen at the BIC minimum  
  > "Meanwhile, the BIC value showed a minimum value in the best-fit result." (3.1 Quiescent Flux Density Determination)
- Limitation (authors): 30-day binning can lose shorter variability  
  > "We note that some information could be lost because of binning if variability is shorter than 30 days." (3.2 SSA Spectra Fitting)
- Limitation (authors): De-projected distance may be inaccurate because core-shift and viewing angle vary with time  
  > "However, note that the de-projected distance may not be accurate since both the core-shift effect and the viewing angle vary with time." (3.5 Jet Ridgeline Analysis)
- Limitation (authors): Map alignment for stacking may be inaccurate because core-shift offsets are not zero and vary  
  > "the map alignments may not be accurate as the averaged core-shift offsets were not zero, and the core-shift effect varies with time." (3.6 Stacking the 43 VLBI Maps)
- Caveat (inferred, ours): ALMA contributes only a few catalogue flux points (about 2.5 % error) to a spectrum dominated by single-dish and VLBI data; ALMA-specific reduction is not described
- Caveat (inferred, ours): Abstract B_SSA limits (>7 mG LSS) differ from the Section 3.3 text (>37 mG before the 2014 flare), so the quoted numbers depend on epoch selection
- Caveat (inferred, ours): Doppler factors are borrowed from literature and assigned by distance from core; b(alpha) varies by 2x, so B_SSA (steeply dependent on d_m and nu_m) is highly uncertain
- Caveat (inferred, ours): Double-SSA decomposition is under-constrained with sparse low-frequency points and 30-day bins; sampler and priors are not given
- Caveat (inferred, ours): Quiescent spectrum rests on four frequencies; 340 GHz values are extrapolated rather than measured

## Reproducibility

- Data public (paper): Mixed: ALMA, SMA, MOJAVE and VLBA-BU data public; OVRO and others by request  
  > "The data underlying this article will be shared on reasonable request to the corresponding author." (DATA AVAILABILITY); "The ALMA data are available at the ALMA Calibrator Source Catalogue, found at https://almascience.eso.org/sc/." (DATA AVAILABILITY)
- Products in archive: _not stated_
- Missing: Tabulated per-epoch input flux densities (including ALMA) used in the SSA fits
- Missing: emcee and SSA fit configuration (priors, walkers, convergence)
- Missing: Doppler-factor and b(alpha) choices per epoch, and the interpolated theta_FWHM table inputs
- Missing: Some single-dish data (OVRO, GMVA) only available on request
- Missing: Analysis code is not released
- Data volume (inferred): Small for the ALMA part (flux table from the calibrator catalogue); the VLBI portion (EVN pipeline data, VLBA UVFITS, 38 epochs at 43 GHz) is of order tens of GB
- Score (inferred): 2/5, Equations and key parameters are given for flare decomposition, SSA fits and B-field, but input data tables, fit priors and several choices are missing, some data only on request, no code, and ALMA is a minor input.
- Rediscovery candidate: no, Not all data are public, the ALMA flux values are not tabulated, and fit settings are incomplete, so the main numeric results cannot be redone from the paper alone.

## Links

- Method: (cite: valtaoja1999) (Exponential flare light-curve decomposition)
- Method: (cite: turler1999) (SSA spectrum model)
- Method: (cite: marscher1983) (B_SSA estimate for a uniform sphere)
- Method: (cite: kataoka&stawarz2005) (Equipartition B_EQ formula)
- Method: (cite: fomalont1999) (Model-fit error estimation)
- Companion: (cite: kutkin2014) (Earlier multi-frequency VLBA core-shift study of 3C 454.3 supplying jet-geometry inputs)
- Companion: (cite: weaver2022) (VLBA-BU-BLAZAR 43 GHz results with Doppler factors and K14 proper motion)
- Companion: (cite: liodakis2020) (Reported the K14 component ejection and its proper motion)
- Related: F-GAMMA
- Related: OVRO 40 m monitoring
- Related: MARMOT (CARMA)
- Related: KVN MOGABA
- Related: MOJAVE
- Related: VLBA-BU-BLAZAR
- Related: SMA calibrator list
- Related: ALMA Calibrator Source Catalogue

## Checks

```json
{
 "quotes": 123,
 "quotes_ok": 123,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.01234.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 126,
  "stated": 90,
  "rate": 0.714
 },
 "evidence_ok": true
}
```
