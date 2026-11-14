# The ALMA Discovery of the Rotating Disk and Fast Outflow of Cold Molecular Gas in NGC 1275

`2019ApJ...883..193N` | The Astrophysical Journal 2019 | first author: Nagai, H. | arXiv: 1905.06017 | DOI: 10.3847/1538-4357/ab3e6e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies, galaxy_clusters_and_sz
- Question: What are the morphology and kinematics of the cold molecular gas in the inner kpc to ~30 pc of NGC 1275, how is the AGN fed, what do the blue-shifted absorption features imply, and what is the SMBH mass from gas dynamics?  
  > "We discuss the relation of the AGN feeding with cold accretion, the origin of blue-shifted absorption, and estimate of black hole mass using the molecular gas dynamics." (abstract)
- Target **NGC 1275 (3C 84)**: coordinates _not stated_; z/distance z=0.017; 0.1 arcsec = 34.4 pc (H0=70.5, OmegaM=0.27, OmegaL=0.73)  
  > "The Perseus cluster is a nearby (z=0.017) cluster of galaxies and has been the subject of extensive research over years at all wavelengths." (1 Introduction); "At the 3C 84 distance, $0.1\ensuremath{''}$ corresponds to 34.4 pc." (1 Introduction); distance from redshift with stated cosmology  
  > "The Perseus cluster is a nearby (z=0.017) cluster of galaxies and has been the subject of extensive research over years at all wavelengths." (1 Introduction); "At the 3C 84 distance, $0.1\ensuremath{''}$ corresponds to 34.4 pc." (1 Introduction)

## Data provenance

- ALMA projects: 2017.1.01257.S, 2013.1.01102.S
- bands: Band 6 (1.3 mm)  
  > "The observations were done in ALMA Band 6 ($\lambda=$1.3 mm) with 47 antennas" (2 OBSERVATIONS and DATA ANALYSIS)
- frequencies and spectral setup: CO: 1920 ch at 0.977 MHz (~1.3 km/s) in LSB, 64 ch in USB; HCN/HCO+: 1920 ch (~1.1 km/s) in USB  
  > "with 1920 channels per spw (0.977 MHz channels resolution or $\sim$1.3 km/s velocity resolution)" (2 OBSERVATIONS and DATA ANALYSIS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended C43-7 (compact C43-4 not presented)  
  > "This paper presents the results from the observations with the extended configuration." (2 OBSERVATIONS and DATA ANALYSIS)
- baselines: 92.1 m to 2.5 km  
  > "The maximum and minimum baseline lengths are 2.5 km and 92.1 m." (2 OBSERVATIONS and DATA ANALYSIS)
- angular resolution: CO natural 0.144x0.077 arcsec; Briggs 0.110x0.048 arcsec  
  > "| CO(2-1) | $0.144\ensuremath{''}\times0.077\ensuremath{''}$ at $4.0\ensuremath{^\circ}$ |" (Table 2)
- max recoverable scale: 1.8 arcsec (CO), 1.5 arcsec (HCN/HCO+)  
  > "$1.8\ensuremath{''}$ (610 pc)" (Table 1)
- sensitivity: _not stated_
- time on source: 45 min (CO), 39 min (HCN/HCO+)  
  > "| CO(2-1) | 45 | 47 | J0237+2848 | J0313+4120 | 100 K |" (Table 1)
- observing dates: 2017 Nov 27 (CO) and Nov 28 (HCN/HCO+)  
  > "on 2017 November 27 and 2017 November 28 for the CO(2-1) and HCN(3-2)/HCO$^{+}$(3-2), respectively" (2 OBSERVATIONS and DATA ANALYSIS)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (230.538 GHz)
- Line: HCN 3-2 (265.886 GHz)
- Line: HCO+ 3-2 (267.558 GHz)
- Other facility **HST WFPC2 F814W**: archival I-band image for stellar mass MGE model  
  > "We use *HST* $I$-band archival image taken with the F814W filter on Wide Field Planetary Camera 2 to model the stellar mass component." (5 Black Hole Mass)
- External data: Inner filament total gas mass 1.8e9 Msun used for missing-flux estimate  
  > "total gas mass of the inner filament of $1.8\times10^{9}~M_{\ensuremath{\odot}}$ (cite: Lim2008)" (5 Black Hole Mass) [from (cite: Lim2008)]
- External data: Bondi accretion rate 7.4e-5 Msun/yr  
  > "The resultant Bondi accretion rate was $7.4\times10^{-5}M_{\ensuremath{\odot}}$ yr$^{-1}$" (4.1 Filaments) [from (cite: Fujita2016)]
- External data: Stellar velocity dispersion 250 km/s and M_BH 10^8.61 Msun giving SoI of 60 pc  
  > "Using the stellar dispersion velocity of $250$ km s$^{-1}$ and $M_{\rm BH}$ of $10^{8.61}M_{\ensuremath{\odot}}$ (cite: Bettoni2003)" (5 Black Hole Mass) [from (cite: Bettoni2003)]

## Processing

### Calibration

- pipeline or manual: ALMA Pipeline plus extra manual delay calibration and self-calibration  
  > "we calibrated the residual delay using the CASA task `gaincal` with `gaintype=K`." (2 OBSERVATIONS and DATA ANALYSIS)
- casa version: CASA 5.1.1-5  
  > "The data were processed at EA-ARC with the CASA 5.1.1-5 and ALMA Pipeline version 40896." (2 OBSERVATIONS and DATA ANALYSIS)
- pipeline version: ALMA Pipeline version 40896  
  > "The data were processed at EA-ARC with the CASA 5.1.1-5 and ALMA Pipeline version 40896." (2 OBSERVATIONS and DATA ANALYSIS)
- archive products used as is: _not stated_
- flux calibrator: bandpass calibrator J0237+2848; flux from JAO interpolation (spectral index -0.63) of Band 3 and 7 measurements  
  > "The referenced flux was derived with the interpolation (power-law spectral index of $-0.63$) from measurements in Bands 3 and 7 on 2017 November 27." (2 OBSERVATIONS and DATA ANALYSIS)
- flux scale uncertainty: _not stated_
- self calibration: phase self-cal per integration time, amplitude per scan, on NGC 1275 continuum  
  > "The phase and amplitude self-calibration were done per integration time and scan, respectively." (2 OBSERVATIONS and DATA ANALYSIS)

### Imaging

- task: tclean, non-interactive  
  > "Deconvolution was done with the CLEAN algorithm using the CASA task `tclean` non-interactively." (2 OBSERVATIONS and DATA ANALYSIS)
- deconvolver: _not stated_
- weighting robust: natural and Briggs robust 0.5  
  > "we show images with both naturally weighting and Briggs weighting (cite: Briggs1995) of robust parameter 0.5." (2 OBSERVATIONS and DATA ANALYSIS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, first order, line-free channels  
  > "The continuum emission was identified at line-free channels with the fitting order of one using the CASA task `uvcontsub`." (2 OBSERVATIONS and DATA ANALYSIS)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 20 km/s channels, nearest interpolation  
  > "Images were created with the velocity resolution of 20 km/s with the “nearest" interpolation in frequency." (2 OBSERVATIONS and DATA ANALYSIS)
- final beam: see Table 2 (e.g., CO natural 0.144x0.077 arcsec)  
  > "| HCN(3-2) | $0.129\ensuremath{''}\times0.076\ensuremath{''}$ at $12.1\ensuremath{^\circ}$ |" (Table 2)
- final rms: off-position image rms ~1 mJy; spectral-dynamic-range limited uncertainty 5.5-6.8 mJy  
  > "These uncertainties dominate the off-position image rms of $\sim1$ mJy" (2 OBSERVATIONS and DATA ANALYSIS)

### Inherited from earlier work

- SMBH dynamical modelling procedure  
  > "by following a standard procedure as described in (cite: Onishi2017; Davis2017; Davis2018)" (5 Black Hole Mass) [from (cite: Onishi2017; Davis2017; Davis2018)]
- Error scaling of chi2 by (2N_dof)^(1/4)  
  > "we follow the approach of (cite: vandenBosch2009) to conservatively increase the $\Delta\chi^{2}$ level" (5 Black Hole Mass) [from (cite: vandenBosch2009)]
- H2 mass via Solomon & Vanden Bout equations (3) and (4)  
  > "We calculate the total H$_{2}$ gas mass using equations (3) and (4) in (cite: Solomon2005)" (4.2 Inner Gas Disk) [from (cite: Solomon2005)]

### Not stated but needed to reproduce (our reading)

- Image sizes, cell sizes, cleaning thresholds and masks for tclean
- Line-free channel ranges for uvcontsub
- Self-calibration solution parameters and reference model
- Exact reduction of archival 2013.1.01102.S data
- mpfit settings and grid spacing for the SMBH search
- MGE fit parameters and Gaussian components
- Target coordinates

## Analysis recipe

1. **Calibrate, correct delays and self-calibrate**: ALMA pipeline then gaincal gaintype=K residual delay correction and phase/amplitude self-cal on bright continuum  
  > "Thus, we performed self-calibration using the continuum emission of NGC 1275 in both phase and amplitude." (2 OBSERVATIONS and DATA ANALYSIS)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract continuum and image cubes**: uvcontsub order 1 then tclean with natural and Briggs 0.5 weighting at 20 km/s  
  > "The continuum emission was identified at line-free channels with the fitting order of one using the CASA task `uvcontsub`." (2 OBSERVATIONS and DATA ANALYSIS)
   - software: CASA
   - fitting: _not stated_
   - validation: Residual rms in line-free spws ~0.9 mJy below estimated sigma_T  
  > "The measured rms is about 0.9 mJy, which is smaller than $\sigma_{\rm T}$." (2 OBSERVATIONS and DATA ANALYSIS)
3. **Estimate spectral dynamic range uncertainty**: D_spec = I_BP/sigma_BP, sigma_T = I_T/D_spec propagated into spectra  
  > "we can estimate the spectral dynamic range $D_{\rm spec}$ as $D_{\rm spec}=I_{\rm BP}/\sigma_{\rm BP}$" (2 OBSERVATIONS and DATA ANALYSIS)
   - fitting: _not stated_
   - validation: consistent with dynamic range 1000 in the ALMA handbook  
  > "The estimated spectral dynamic range is nearly consistent with the demonstrated spectral dynamic range of $1000$" (2 OBSERVATIONS and DATA ANALYSIS)
4. **Derive H2 gas mass and accretion rates**: Solomon & Vanden Bout CO luminosity to mass; accretion rate M/t_dyn and M/tau  
  > "Here we get the CO(2-1) integrated flux density of 40 Jy$\cdot$km s$^{-1}$ within the central $1\ensuremath{''}$ with a velocity FWHM of 400  km s$^{-1}$." (4.2 Inner Gas Disk)
   - assumption: CO(2-1)/CO(1-0) = 1; alpha_CO = 4.8 (alternative 0.6-0.8); thin disk h=0.1r; v~25 km/s  
  > "We assumed the CO(2-1)-to-CO(1-0) ratio of one and the CO luminosity-to-H$_{2}$ mass conversion factor in our Galaxy" (4.2 Inner Gas Disk)
   - fitting: _not stated_
   - validation: compared with accretion rate from bolometric luminosity within factor of two  
  > "within a factor of two" (4.2 Inner Gas Disk)
5. **Absorption optical depth and column density**: tau from 40 mJy absorption against 7 Jy continuum; LTE, covering factor 1, Tex 100 K, HCN/H2 = 1e-9  
  > "Under the assumption of the local thermodynamic equilibrium and a covering factor of 1, we obtain the H$_{2}$ column density of $2.3\times10^{22}$ cm$^{-2}$." (3.2 The HCN(3-2) and HCO+(3-2) Lines)
   - assumption: HCN-H2 abundance 1e-9  
  > "Here we assume a HCN-H$_{2}$ abundance ratio of $10^{-9}$ (cite: Smith2014)." (3.2 The HCN(3-2) and HCO+(3-2) Lines)
   - fitting: _not stated_
   - validation: spectra on continuum-unsubtracted images and archival data  
  > "To check that these features are not an artifact caused by the process of continuum subtraction, we also show the spectrum measured on the continuum unsubtracted images" (3.2 The HCN(3-2) and HCO+(3-2) Lines)
6. **Model stellar mass with MGE**: MGE fit to HST F814W image with TinyTim PSF, masking AGN and dust region, uniform M/L  
  > "fit the luminosity distribution by using the PSF and the procedure `mge_fit_sectors_regularized`" (5 Black Hole Mass)
   - software: MGE_fit_sectors, TinyTim
   - fitting: _not stated_
   - validation: _not stated_
7. **Fit gas disk kinematics for SMBH mass**: KinMS models with circular velocity from MGE_circular_velocity, exponential disk; mpfit minimization then grid search over M_BH and inclination  
  > "We first searched for a set of parameters to minimize the difference between the observed data and the model by using `mpfit` that is developed in `IDL`." (5 Black Hole Mass)
   - software: KinMS, mpfit, JAM, IDL
   - parameter: fitting area 1.55x1.55 arcsec, 4687-5580 km/s, 129x129x47 pixels, natural-weighted cube  
  > "thus $129\times129\times47$ pixels" (5 Black Hole Mass)
   - assumption: axisymmetric potential, circular motion, exponential gas disk, uniform dispersion  
  > "assuming an axisymmetric potential and circular motion" (5 Black Hole Mass)
   - fitting: chi2-like residual (obs-model)^2/rms^2; errors from residual < 9+chi2_min after rms scaled by (2N_dof)^(1/4)  
  > "we judge the error by allowing all parameters that realize residuals less than $9+\chi_{\rm min}^{2}$" (5 Black Hole Mass)
   - validation: M/L varied 0.05, 0.5, 5.0; two gas masses; missing mass estimate 2e7 Msun  
  > "We confirm this by giving three different $M/L_{I}$ values, $0.05$, $0.50$ and $5.00$ to see negligible difference" (5 Black Hole Mass)

## Software

- **CASA** 5.1.1-5: calibration, uvcontsub, tclean imaging  
  > "The data were processed at EA-ARC with the CASA 5.1.1-5 and ALMA Pipeline version 40896." (2 OBSERVATIONS and DATA ANALYSIS)
- **KinMS** : kinematic modelling of molecular gas disk  
  > "By utilizing the `KinMS`, we take observational effects such as beam smearing and velocity resolution into account" (5 Black Hole Mass)
- **MGE_fit_sectors** : MGE fit of HST I-band image  
  > "contained in the `MGE_fit_sectors` IDL package[^3] of (cite: Cappellari2002)" (5 Black Hole Mass)
- **JAM (MGE_circular_velocity)** : circular velocity curve  
  > "`MGE_circular_velocity` procedure contained in the `JAM` package of (cite: Cappellari2008)" (5 Black Hole Mass)
- **mpfit** : best-fit parameter search  
  > "by using `mpfit` that is developed in `IDL`" (5 Black Hole Mass)
- **TinyTim** 6.3: HST PSF  
  > "The *HST* PSF for this observation was estimated by using TinyTim Version 6.3 (cite: Krist2011)." (5 Black Hole Mass)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2 gas mass of inner disk (alpha_CO=4.8) | ~4e8 | not stated | Msun | 4 | obtain $\sim4\times10^{8}~M_{\ensuremath{\odot}}$ |
| H2 column density of absorber | 2.3e22 | not stated | cm^-2 | 5 | we obtain the H$_{2}$ column density of $2.3\times10^{22}$ cm$^{-2}$ |
| Absorption optical depth | 0.0057 | not stated | dimensionless | 5 | yielding the optical depth of 0.0057 |
| SMBH mass (gas 4e8 Msun) | 1.1e9 | +0.3/-0.5 e9 | Msun | 7 | $M_{\rm BH}=(1.1 ^{+0.3}_{-0.5})\times10^{9}M_{\ensuremath{\odot}}$ and inclination of $46^{+11}_{-6}$ deg |
| SMBH mass (gas 5e7 Msun) | 1.2e9 | +0.1/-0.6 e9 | Msun | 7 | $M_{\rm BH}=(1.2^{+0.1}_{-0.6}) \times10^{9}M_{\ensuremath{\odot}}$ and inclination of $45^{+14}_{-5}$ deg |
| Disk accretion timescale | ~4e7 (r/100pc)(v/25 km/s)^-1 | not stated | yr | 4 | \tau\sim4\times10^{7}\times\left[\frac{r}{\rm 100~pc}\right]\left[\frac{v}{\rm25~km~s^{-1}}\right]^{-1} {\rm yr} |
| Cold accretion rate of disk | 1-2 (for 5-7e7 Msun) and 10 (for 4e8 Msun) | not stated | Msun/yr | 4 | we get $\dot{M}_{\rm gas}=1$-$2~M_{\odot}$ yr$^{-1}$ and $\dot{M}_{\rm gas}=10~M_{\odot}$ yr$^{-1}$, respectively |

## Qualitative findings

- Filaments A-E cannot be represented by a single infalling stream, consistent with chaotic cold accretion  
  > "seems to be hardly reproduced by a single stream of infalling gas since all the components are not aligned in the same position angle" (3.1 The CO(2-1) Line)
- Blue-shifted HCN/HCO+ absorption by 300-600 km/s against the jet suggests outflowing gas  
  > "The absorption features are blue-shifted from the systemic velocity by $\sim$300-600 km s$^{-1}$, suggesting the presence of outflowing gas" (abstract)

## Claim tuples

- H: Is there a massive rotating cold gas disk in the central 100 pc? | E: Imaging of CO(2-1), HCN(3-2), HCO+(3-2) at ~20 pc resolution | R: Velocity gradient ~±250 km/s at PA~70 deg; H2 mass ~4e8 Msun | F: A rotating molecular disk exists, with axis roughly aligned with the jet | **supported**
- H: Is cold accretion more important than hot (Bondi) accretion? | E: Crude accretion rate estimates from gas mass and timescales | R: Mdot > 0.1 Msun/yr (kpc) and 1-10 Msun/yr (disk) versus Bondi 7.4e-5 | F: Cold accretion can dominate | **partially**
- H: Are there outflowing absorbers? | E: Spectra at the continuum peak, checked without continuum subtraction and in archival data | R: Absorption at 4600-4900 km/s, >3 sigma HCN and >4 sigma HCO+; marginal in archive | F: Likely jet-cloud interaction or CND outflow | **partially**
- H: What is the SMBH mass from molecular gas dynamics? | E: KinMS disk modelling of the CO cube with MGE stellar mass | R: M_BH ~1.1e9 Msun | F: Agrees with warm H2 dynamics, disagrees with virial BLR mass | **supported**

## Reasoning

- Why this data: High-resolution ALMA needed to resolve inner kpc to <50 pc scale  
  > "High resolution observations of the cold molecular gas with ALMA are key to uncovering the missing link between the outer kpc and the inner $\lesssim50$ pc" (1 Introduction)
- Why this method: _not stated_
- Alternative: alpha_CO = 0.6-0.8 considered, giving 5-7e7 Msun  
  > "we obtain the total gas mass of $\sim$5-7$\times10^{7} M_{\ensuremath{\odot}}$" (4.2 Inner Gas Disk)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux from lack of short baselines, so masses are lower limits  
  > "Note that the estimated mass should be a lower limit since the total emissions cannot be recovered because of the lack of short interferometric baselines." (4.1 Filaments)
- Limitation (authors): Residual is not a true chi2 because neighbouring pixels are correlated; modelling assumptions simple  
  > "This residual is useful to judge the fitting results but is not equivalent to the $\chi^{2}$, as the neighboring pixels in the observed cube are correlated." (5 Black Hole Mass)
- Caveat (inferred, ours): Accretion rates are crude order-of-magnitude estimates with large alpha_CO uncertainty
- Caveat (inferred, ours): SMBH error from rescaled residuals, not a proper chi2 or MCMC; inclination hits search limit
- Caveat (inferred, ours): Absorption significance only 3-4 sigma and marginal in archive
- Caveat (inferred, ours): Self-calibration on a variable source may affect line and absorption fluxes

## Reproducibility

- Data public (paper): Project codes cited; archival data identified  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.0.01257.S and ADS/JAO.ALMA#2013.1.01102.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks)
- Missing: Self-cal details
- Missing: Line-free channel selection
- Missing: Fitting grid details
- Data volume (inferred): ~100-300 GB raw for the two extended-configuration EBs; plus archival data
- Score (inferred): 3/5, Public data and a clear modelling approach, but imaging, self-cal and fitting details are partly unstated.
- Rediscovery candidate: yes, Data are public, the processing and the modelling are largely described, and results (gas mass, M_BH) are numeric.

## Links

- Method: (cite: Onishi2017; Davis2017; Davis2018) (SMBH dynamical modelling procedure)
- Method: (cite: vandenBosch2009) (error scaling of chi2)
- Method: (cite: Cappellari2002) (MGE fitting)
- Companion: (cite: Lim2008) (previous CO observations of filaments)
- Companion: (cite: Scharwachter2013) (warm H2 disk kinematics and BH mass)

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2017.0.01257.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 59,
  "rate": 0.686
 },
 "evidence_ok": true
}
```
