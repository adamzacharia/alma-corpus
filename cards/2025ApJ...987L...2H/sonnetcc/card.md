# Dissecting the Massive Pristine, Neutral Gas Reservoir of a Remarkably Bright Galaxy at z = 14.179

`2025ApJ...987L...2H` | The Astrophysical Journal Letters 2025 | first author: Heintz, Kasper E. | arXiv: 2502.06016 | DOI: 10.3847/2041-8213/ade393

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Reanalyse the JWST/NIRSpec prism spectrum of GS-z14 to measure its H I column density from the damped Lyman-alpha profile and combine it with published ALMA [O III]-88um, [C II]-158um and dust-continuum constraints to determine the gas content, gas fraction and dust-to-gas ratio  
  > "In this Letter, we reanalyze the JWST/NIRSpec Prism spectrum of GS-z14 in the context of its H i gas content, corroborated by recent far-infrared line emission and continuum measurements." (Introduction)
- Target **JADES-GS-z14-0 (GS-z14)**: coordinates _not stated_; z/distance z = 14.1796 +/- 0.0006 (from [O III]-88um); abstract quotes z=14.179  
  > "The line-redshift was thus confirmed to be at $z=14.1796\pm 0.0006$" (Introduction); "This is also used to infer cosmological parameters such as the luminosity distance to GS-z14 and age of the Universe with the" (Introduction); distance from [O III]-88um line redshift from ALMA (Carniani24b; Schouws24); Planck18 cosmology with Astropy for luminosity distance  
  > "The line-redshift was thus confirmed to be at $z=14.1796\pm 0.0006$" (Introduction); "This is also used to infer cosmological parameters such as the luminosity distance to GS-z14 and age of the Universe with the" (Introduction)

## Data provenance

- ALMA projects: 2023.A.00037.S, 2024.A.00007.S
- bands: _not stated_
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
- pi or archival as stated: ALMA programs 2023.A.00037.S ([O III]-88um) and 2024.A.00007.S ([C II]-158um), PI Schouws; results taken from earlier papers  
  > "Prog. ID: 2023.A.00037.S, PI: Schouws" (Observations); "Prog. ID: 2024.A.00007.S, PI: Schouws" (Observations)
- Line: [O III] 88 um (not stated)
- Line: [C II] 158 um (not stated)
- Other facility **JWST/NIRSpec prism (MSA, Prog. ID 1287)**: Prism spectrum 0.6-5.3 um, R=30-300, 9.3 h on source, used for the Lyman-alpha damping-wing (DLA) fit  
  > "The data were obtained using the NIRSpec (cite: Jakobsen22) Micro-Shutter Assembly (cite: Ferruit22), with three-shutter slitlets (Prog. ID 1287, PI: Luetzgendorf)." (Observations); "This sequence (about 2.33 h total integration) was repeated four times, for a final on-source time of 9.3 h." (Observations)
- Other facility **JWST/NIRCam imaging (JADES, FRESCO, JADES Origins Field)**: Multi-band imaging used for forcepho photometry that scales the spectrum  
  > "Multi-band JWST/NIRCam imaging was obtained as part of the JWST Advanced Deep Extragalactic Survey (cite: Eisenstein23a)" (Observations)
- Other facility **JWST/MIRI**: 7.7 um detection implying strong nebular emission lines  
  > "GS-z14 has further been detected in $7.7\mu$m imaging with JWST/MIRI (cite: Helton24)" (Observations)
- External data: SFR = 14.5 +/- 3 Msun/yr and log(M*/Msun) = 8.29 +0.09/-0.10 from prospector SED modelling (Chabrier IMF)  
  > "Throughout this work, we adopt the spectral and physical galaxy measurements reported in (cite: Carniani24b)." (Observations) [from (cite: Carniani24b)]
- External data: z = 14.1796 +/- 0.0006 systemic redshift from [O III]-88um  
  > "The significant detection of the far-infrared \[O iii\]-$88\mu$m emission line reveals the systemic redshift to be $z=14.1796\pm 0.0006$ (cite: Carniani24b; Schouws24)." (Analysis and results) [from (cite: Carniani24b; Schouws24)]
- External data: [O III]-88um luminosity (2.0 +/- 0.5)e8 Lsun  
  > "\[O iii\]-$88\mu$m is detected at $>6\sigma$ with a line luminosity $L_{\rm [OIII]} = (2.0\pm 0.5)\times 10^{8}\,L_\odot$ (cite: Schouws24; Carniani24b)." (Observations) [from (cite: Schouws24; Carniani24b)]
- External data: [C II]-158um non-detection limit < 6e7 Lsun  
  > "resulted in a non-detection at a limit $<6\times 10^{7}\,L_\odot$ (cite: Schouws25)" (Observations) [from (cite: Schouws25)]
- External data: Molecular gas mass upper bound M_mol < 10^9.2 Msun from [C II]  
  > "substantially higher than the previously reported upper bound inferred on the (molecular) gas mass, $M_{\rm mol} < 10^{9.2}\,M_\odot$ (cite: Schouws25)" (Analysis and results) [from (cite: Schouws25)]
- External data: Dust mass upper bound < 1e6 Msun from the far-infrared continuum  
  > "the upper bound on the dust mass $<10^{6}\,M_\odot$ from the far-infrared continuum (cite: Schouws24)" (Discussion and conclusions) [from (cite: Schouws24)]
- External data: UV half-light radius R_UV = 0.26 kpc and Sersic index 1 from forcepho; lensing magnification mu = 1.17  
  > "The fiducial `forcepho` model yields a half-light semi-major axis of $R_{\rm UV} = 0.26$ kpc and a Sérsic index of 1." (Observations); "is estimated to be only $\mu=1.17$ (cite: Carniani24a)" (Observations) [from (cite: Carniani24a)]
- External data: Absolute UV magnitude M_UV = -20.81 +/- 0.16 mag  
  > "With an absolute UV magnitude, $M_{\rm UV} = -20.81\pm 0.16$ mag (cite: Carniani24a)" (Analysis and results) [from (cite: Carniani24a)]
- External data: Visual attenuation A_V = 0.25 +/- 0.10 from full SED and line modelling  
  > "the visual attenuation $A_V = 0.25\pm 0.10$ inferred from the full spectro-photometric modeling of the SED and line emission for GS-z14 (cite: Carniani24b)" (Analysis and results) [from (cite: Carniani24b)]
- External data: Dynamical mass log(M_dyn/Msun) = 9.0 +/- 0.2 within the [O III] region  
  > "($\log (M_{\rm dyn}/M_\odot) = 9.0\pm 0.2$) and the non-detection of the \[C ii\]-$158\mu$m emission line (cite: Carniani24b; Schouws25)" (Discussion and conclusions) [from (cite: Carniani24b; Schouws25)]
- External data: Metallicity-dependent [C II]-to-H I conversion  
  > "we consider the metallicity-dependent relation converting the \[C ii\]-$158\mu$m line luminosity into a H i gas mass (cite: Heintz21)" (Analysis and results) [from (cite: Heintz21)]
- External data: Global Kennicutt-Schmidt relations (molecular and total gas)  
  > "we consider the Kennicutt-Schmidt relation (cite: Kennicutt12), universally connecting the SFR and gas surface density." (Analysis and results) [from (cite: Kennicutt12)]
- External data: [O III]-to-metal-mass calibration log(M_Z/L_[OIII]) = -1.0 +/- 0.2 for L_[OIII]/L_[CII] > 3  
  > "such that $\log (M_Z / L_{\rm [OIII]}) = -1.0\pm 0.2$ for $L_{\rm [OIII]} / L_{\rm [CII]}>3$" (Analysis and results) [from (cite: Heintz23_mz)]
- External data: Gamma-ray burst sightline compilation of A_V/N_HI and MW/SMC/LMC averages for comparison  
  > "We compare this to equivalent measures from the compilation of $\gamma$-ray burst sightlines through high-redshift ($z=1.7-6.3$) star-forming galaxies presented in (cite: Heintz23_GRB)" (Analysis and results) [from (cite: Heintz23_GRB); (cite: Konstantopoulou24)]
- External data: SMC-like reddening curve  
  > "requires $A_V = 0.3$ mag for a SMC-like reddening curve (cite: Gordon03)" (Analysis and results) [from (cite: Gordon03)]
- External data: Nebular continuum parameters T = 20,000 K and n_e = 1e2 cm^-3  
  > "assuming $T = 20,000$ K and $n_e = 10^2$ cm$^{-3}$ from (cite: Schirmer16)" (Analysis and results) [from (cite: Schirmer16)]
- External data: Solar oxygen abundance 12+log(O/H) = 8.69 and Z_sun,ref = 0.018  
  > "a solar oxygen abundance of $12+\log ({\rm O/H})_\odot = 8.69$; (cite: Asplund09)" (Analysis and results) [from (cite: Asplund09)]
- Simulation/model as data: Analytical model of the star formation history and physical properties of GS-z14, used for comparison (predicts dust-to-gas mass ratio 10^-3.5)  
  > "particularly predicts a low dust-to-gas mass ratio of $10^{-3.5}$" (Discussion and conclusions)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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

- Flux correction applied to the reduced NIRSpec spectrum to match forcepho photometry  
  > "Following (cite: Carniani24a), we apply a flux correction factor to the reduced spectrum" (Observations) [from (cite: Carniani24a)]
- Photometry used to scale the spectrum from forcepho Sersic modelling  
  > "The photometry implicitly used in this article (to scale the spectrum) was obtained by modeling the galaxy with a Sérsic profile," (Observations) [from as described in (cite: Carniani24a)]
- JWST NIRCam data reduction  
  > "The data reduction is outlined in (cite: Rieke23; Eisenstein23a; Eisenstein23b)." (Observations) [from (cite: Rieke23; Eisenstein23a; Eisenstein23b)]
- Voigt-profile DLA model with approximation of Tepper-Garcia  
  > "We model the DLA absorption with a Voigt profile following (cite: Heintz24_z54), using the approximation from (cite: TepperGarcia06)" (Analysis and results) [from (cite: Heintz24_z54); (cite: TepperGarcia06)]
- SFR, stellar mass and other galaxy properties adopted from prospector SED fitting  
  > "Throughout this work, we adopt the spectral and physical galaxy measurements reported in (cite: Carniani24b)." (Observations) [from (cite: Carniani24b)]
- ALMA data reduction and line measurements are taken from the original ALMA papers  
  > "Deep ALMA observations targeting the \[C ii\]-$158\mu$m line, however, resulted in a non-detection at a limit $<6\times 10^{7}\,L_\odot$ (cite: Schouws25)" (Observations) [from (cite: Schouws24; Carniani24b); (cite: Schouws25)]

### Not stated but needed to reproduce (our reading)

- Priors and bounds for log N_HI, x_HI and beta_UV in the dynesty fit, and the nested-sampling settings (live points, stopping criterion)
- Wavelength range of the prism spectrum used in the fit and how the 'full spectrum' chi^2 and BIC were counted (degrees of freedom, error treatment)
- Which version of the NIRSpec reduction and which spectral extraction were used (spectrum is on Zenodo but pipeline version not stated)
- Exact Kennicutt-Schmidt relations (coefficients, slopes, adopted CO-to-H2 factor) for the molecular and total gas surface densities
- How the spherical H I mass was computed from N_HI and R_HI = 3 R_UV (explicit formula, mean molecular weight)
- All ALMA observing setups, calibration, imaging and the [O III]/[C II]/continuum measurements themselves (not reprocessed here; only published values from other papers are used)
- Method used to derive the A_V = 0.3 mag from the slope (fit procedure and wavelength range)

## Analysis recipe

1. **Flux-correct the NIRSpec prism spectrum to the NIRCam photometry**: Apply a wavelength-dependent polynomial correction to the reduced spectrum so that it matches the forcepho photometry, to correct slit losses and flux-calibration uncertainty  
  > "This effectively takes into account and corrects for potential slit losses and/or uncertainties in the overall flux calibration." (Observations)
   - software: forcepho
   - parameter: F_corr = F_red x (0.18 x lambda(um) + 1)  
  > "using a simple polynomial $F_{\rm corr} = F_{\rm red} \times (0.18\times \lambda(\mu{\rm m}) + 1)$" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit the DLA Lyman-alpha damping wing for N_HI**: Voigt-profile DLA plus IGM x_HI absorption on a power-law rest-UV continuum, convolved with the spectral resolution at each step; free parameters log N_HI, x_HI, beta_UV at fixed DLA redshift z = 14.1796  
  > "convolve the best-fit model with the spectral resolution at each step during the optimization" (Analysis and results); "We assume that the rest-frame UV continuum can be approximated by a smooth power-law function" (Analysis and results)
   - software: dynesty, Astropy
   - parameter: Fixed DLA redshift z = 14.1796; sampled parameters log N_HI, x_HI, beta_UV  
  > "assuming a fixed DLA redshift of $z=14.1796$" (Analysis and results)
   - assumption: IGM expected to be fully neutral at z ~ 14  
  > "which we expect to be fully neutral at $z\approx 14$" (Analysis and results)
   - assumption: Smooth power-law rest-UV continuum; more complex shapes or Lya emission do not significantly affect N_HI  
  > "Introducing more complex spectral shapes or prominent Ly$\alpha$ emission does not significantly affect the derived $N_{\rm HI}$ (cite: Heintz24_DLA)" (Analysis and results)
   - fitting: dynesty nested sampling; priors not stated  
  > "nested sampling (cite: Speagle20) to sample the posteriors of the parameters" (Analysis and results)
   - validation: Compared with IGM-only and nebular-continuum models using reduced chi^2 and BIC (step 3)  
  > "Additionally, the difference in Bayesian Information Criteria between the models $\Delta \rm BIC = 82$ indicates a strong statistical preference for the IGM+DLA model" (Analysis and results)
3. **Test alternative continuum models against the DLA model**: Fit an IGM-only model (x_HI = 1) and a purely nebular two-photon continuum model, and compare chi^2_nu and BIC with the IGM+DLA fit  
  > "We also compare the DLA model to a purely nebular continuum model, dominated by the two-photon ($2\gamma$) emission at rest-frame UV wavelengths" (Analysis and results)
   - parameter: Nebular model T = 20,000 K, n_e = 1e2 cm^-3  
  > "assuming $T = 20,000$ K and $n_e = 10^2$ cm$^{-3}$ from (cite: Schirmer16)" (Analysis and results)
   - fitting: _not stated_
   - validation: chi^2_nu 1.23 (DLA), 1.69 (IGM only), 1.53 (nebular); Delta BIC = 82  
  > "This matches well the slope of the spectrum, but the strong UV turnover is inconsistent with the data ($\chi_\nu^2 = 1.53$)." (Analysis and results)
4. **Convert N_HI to a total H I gas mass**: Assume a spherical gas distribution with half-mass radius 3x the rest-UV size and use the line-of-sight N_HI  
  > "For a spherically distributed gas, this yields an H i gas mass of $M_{\rm HI} = 5\times 10^{9}\,M_\odot$" (Analysis and results)
   - parameter: R_HI ~ 3 x R_UV, with R_UV = 0.26 kpc  
  > "assume that the half-mass radius of the neutral gas is $\sim 3\times$ the rest-frame UV size (cite: Fujimoto20; Fudamoto22)" (Analysis and results)
   - assumption: Spherical geometry (admitted to be an over-simplification, high covering factor argued)  
  > "While a spherical geometry is an over-simplification, the high detection rate of DLA around galaxies at $z>10$ (cite: Heintz25) almost certainly implies a high covering factor" (Discussion and conclusions)
   - fitting: _not stated_
   - validation: Cross-checked against Kennicutt-Schmidt gas mass (step 6)  
  > "this estimate is consistent with the bulk of the interstellar medium (ISM) in GS-z14 being in the form of H i" (Analysis and results)
5. **Upper bound on H I mass from the [C II] non-detection**: Apply the metallicity-dependent [C II]-to-H I conversion calibrated on gamma-ray burst sightlines to the [C II] luminosity limit  
  > "we derive an upper bound of $M_{\rm HI} < 10^{9.9}\,M_\odot$ ($3\sigma$)" (Analysis and results)
   - parameter: [C II] limit L < 6e7 Lsun; metallicity Z/Zsun = 0.17  
  > "resulted in a non-detection at a limit $<6\times 10^{7}\,L_\odot$ (cite: Schouws25)" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
6. **Gas mass from SFR surface density and Kennicutt-Schmidt relation**: Compute Sigma_SFR = SFR_UV / (2 pi R_UV^2), apply the global Kennicutt-Schmidt relations to get molecular and total gas surface densities and masses within the star-forming region, then f_gas = M_gas/(M* + M_gas)  
  > "We determine the star-formation rate surface density as $\Sigma_{\rm SFR} = {\rm SFR}_{\rm UV} / 2\pi R^2_{\rm UV}$" (Analysis and results)
   - parameter: SFR = 14.5 +/- 3 Msun/yr (30% error adopted), R_UV = 0.26 kpc, log M* = 8.29  
  > "(assuming an inflated $30\%$ error on the SFR)" (Analysis and results)
   - assumption: Global-galaxy Kennicutt-Schmidt relation applies at z = 14  
  > "following the global-galaxy Kennicutt-Schmidt relation" (Analysis and results)
   - fitting: _not stated_
   - validation: Compared with M_H2 upper bound from [C II] and with DLA-derived M_HI  
  > "which we convert to a molecular gas mass of $\log (M_{\rm H_2}/M_\odot) = 9.2\pm 0.3$ within the star-forming region" (Analysis and results)
7. **Gas mass from the [O III]-based metal mass**: Convert L_[OIII] to metal mass with the calibration from Heintz23_mz, then divide by metallicity Z/Zsun x Z_sun,ref to obtain gas mass  
  > "The metal mass in the ISM is defined as $M_Z = M_{\rm gas}\times Z/Z_\odot \times Z_{\rm \odot,ref}$ with $Z_{\rm \odot,ref} = 0.018$." (Analysis and results)
   - parameter: log(M_Z/L_[OIII]) = -1.0 +/- 0.2 for L_[OIII]/L_[CII] > 3  
  > "such that $\log (M_Z / L_{\rm [OIII]}) = -1.0\pm 0.2$ for $L_{\rm [OIII]} / L_{\rm [CII]}>3$" (Analysis and results)
   - assumption: Oxygen abundance log(O/H) = 7.92 (Z/Zsun = 0.17; solar 12+log(O/H) = 8.69)  
  > "the metallicity quantified as an oxygen abundance, $\log ({\rm O/H}) = 7.92$" (Analysis and results)
   - fitting: _not stated_
   - validation: Result described as consistent with the other gas mass estimates  
  > "which implies a total gas mass of $\sim 10^{9.8}\,M_\odot$ when taking the metallicity of GS-z14 into account, consistent with the above estimates" (Analysis and results)
8. **Line-of-sight dust-to-gas ratio A_V/N_HI**: Derive A_V from the observed rest-UV slope assuming an intrinsic beta_UV = -3 and an SMC-like reddening curve, divide by N_HI from the DLA fit, and compare with GRB sightlines and MW/SMC/LMC averages  
  > "Assuming a steep, intrinsic power-law with $\beta_{\rm UV} = -3$ requires $A_V = 0.3$ mag for a SMC-like reddening curve (cite: Gordon03)" (Analysis and results)
   - parameter: Intrinsic beta_UV = -3; A_V = 0.3 mag  
  > "This quantity is effectively the maximum allowed amount of dust in the line-of-sight that will extinguish the light" (Analysis and results)
   - assumption: SMC-like reddening curve; intrinsic slope beta_UV = -3 (A_V is an upper limit)  
  > "for a SMC-like reddening curve (cite: Gordon03) to match the observed rest-frame UV spectral slope" (Analysis and results)
   - fitting: _not stated_
   - validation: Consistent with SED-modelling A_V = 0.25 +/- 0.10 from Carniani24b  
  > "This upper bound is also consistent with the visual attenuation $A_V = 0.25\pm 0.10$" (Analysis and results)

## Software

- **dynesty** : Nested sampling of log N_HI, x_HI and beta_UV posteriors  
  > "nested sampling (cite: Speagle20) to sample the posteriors of the parameters" (Analysis and results)
- **Astropy** : Cosmological parameters such as luminosity distance and age of the Universe  
  > "This is also used to infer cosmological parameters such as the luminosity distance to GS-z14 and age of the Universe with the" (Introduction)
- **forcepho** : Sersic-profile modelling of NIRCam photometry used to scale the spectrum (from Carniani24a)  
  > "The photometry implicitly used in this article (to scale the spectrum) was obtained by modeling the galaxy with a Sérsic profile," (Observations)
- **prospector** : SED modelling that gave the adopted SFR and stellar mass (from Carniani24b)  
  > "taking into account the full multi-wavelength spectroscopic and imaging data obtained for GS-z14" (Observations)
- **Matplotlib** : Listed in the Software section; specific use not stated  
  > "Astropy (cite: Astropy), Matplotlib (cite: Matplotlib), Numpy (cite: Numpy)" (Software)
- **Numpy** : Listed in the Software section; specific use not stated  
  > "Astropy (cite: Astropy), Matplotlib (cite: Matplotlib), Numpy (cite: Numpy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H I column density log(N_HI/cm^-2) | 22.27 | +0.08/-0.09 | dex (cm^-2) | 2 | we determine a substantial neutral atomic hydrogen (H i) column density, $\log (N_{\rm HI} / {\rm cm^{-2}}) = 22.27^{+0.08}_{-0.09}$ |
| IGM neutral fraction x_HI | > 0.41 | 1 sigma from the 68% highest density interval | dimensionless | 2 | $x_{\rm HI} > 0.41$ ($1\sigma$ from the $68\%$ highest density interval) |
| UV slope beta_UV | -1.93 | 0.08 | dimensionless | 2 | and $\beta_{\rm UV} = -1.93\pm 0.08$ |
| Reduced chi^2 of IGM+DLA fit | 1.23 | not stated | dimensionless | 3 | compared to $\chi_\nu^2 = 1.23$ for the fit with a DLA component |
| Reduced chi^2 of IGM-only fit | 1.69 | not stated | dimensionless | 3 | provides a statistically worse fit to the data with $\chi_\nu^2 = 1.69$ |
| Reduced chi^2 of nebular continuum model | 1.53 | not stated | dimensionless | 3 | but the strong UV turnover is inconsistent with the data ($\chi_\nu^2 = 1.53$) |
| Delta BIC (IGM-only vs IGM+DLA) | 82 | not stated | dimensionless | 3 | the difference in Bayesian Information Criteria between the models $\Delta \rm BIC = 82$ |
| H I gas mass from DLA (spherical) | 5e9 | not stated | Msun | 4 | For a spherically distributed gas, this yields an H i gas mass of $M_{\rm HI} = 5\times 10^{9}\,M_\odot$ |
| H I mass upper bound from [C II] non-detection | < 10^9.9 | 3 sigma | Msun | 5 | we derive an upper bound of $M_{\rm HI} < 10^{9.9}\,M_\odot$ ($3\sigma$) |
| SFR surface density log(Sigma_SFR) | 1.5 | 0.30 | Msun yr^-1 kpc^-2 (dex) | 6 | yields $\log (\Sigma_{\rm SFR} / M_{\odot}\,{\rm yr}^{-1}\,{\rm kpc}^{-2}) = 1.5\pm 0.30$ |
| Molecular gas surface density log(Sigma_H2) | 3.6 | 0.3 | Msun pc^-2 (dex) | 6 | This implies a molecular gas surface density of $\log (\Sigma_{\rm H_2} / M_{\odot}\,{\rm pc}^{-2}) = 3.6\pm 0.3$ |
| Molecular gas mass log(M_H2) | 9.2 | 0.3 | Msun (dex) | 6 | which we convert to a molecular gas mass of $\log (M_{\rm H_2}/M_\odot) = 9.2\pm 0.3$ within the star-forming region |
| Total gas surface density log(Sigma_gas) | 4.2 | 0.3 | Msun pc^-2 (dex) | 6 | predicts a higher total gas surface density $\log (\Sigma_{\rm gas} / M_{\odot}\,{\rm pc}^{-2}) = 4.2\pm 0.3$ |
| Total gas mass log(M_gas) | 9.8 | 0.3 | Msun (dex) | 6 | the total gas mass of GS-z14 is of the order $\log (M_{\rm gas} / M_\odot) = 9.8\pm 0.3$ |
| Gas mass fraction f_gas | >~ 0.9 | not stated | dimensionless | 6 | Taken at face value, this implies a large gas fraction $f_{\rm gas} = M_{\rm gas} / (M_\star + M_{\rm gas}) \gtrsim 0.9$. |
| Total metal mass M_Z | 2.0e7 | 0.6e7 | Msun | 7 | This yields a total metal mass in the ISM of $M_Z = (2.0\pm 0.6)\times 10^{7}\,M_\odot$ |
| Upper limit visual extinction A_V | 0.3 | not stated | mag | 8 | requires $A_V = 0.3$ mag for a SMC-like reddening curve (cite: Gordon03) |
| Dust-to-gas ratio A_V/N_HI | 1.3e-23 | 0.6e-23 | mag cm^2 | 8 | This yields a dust-to-gas ratio of $A_V/N_{\rm HI} = (1.3\pm 0.6)\times 10^{-23}$ mag cm$^{2}$. |
| Gas-phase metallicity range from dust-to-gas relation | -1.95 < [M/H] < -1.15 | not stated | dex | 8 | indicate a gas-phase metallicity of $-1.95 < {\rm [M/H]} < -1.15$ |

## Qualitative findings

- The [O III]-88um emission arises from the central star-forming region and is not a reliable tracer of the total baryonic matter  
  > "this line transition is arguably not a reliable tracer of the total baryonic matter in the galaxy" (Discussion and conclusions)
- The DLA gas is argued to be more pristine than the central star-forming region  
  > "we determined that the metallicity of the DLA is lower than that of the central star-forming region" (Discussion and conclusions)
- The dust-to-gas ratio is consistent with the most metal-poor GRB sightlines  
  > "It is evident that GS-z14 has a relatively low dust-to-gas ratio, consistent with the most metal-poor" (Analysis and results)

## Claim tuples

- H: Does the NIRSpec prism spectrum of GS-z14 show a DLA with a substantial H I column density? | E: Voigt-profile DLA plus power-law continuum fit with dynesty at fixed z = 14.1796, compared with IGM-only and nebular models | R: log N_HI = 22.27 +0.08/-0.09; IGM+DLA chi^2_nu 1.23 vs 1.69 (IGM only) and 1.53 (nebular); Delta BIC = 82 | F: A strong DLA with high N_HI is present and statistically preferred | **supported**
- H: Is the total gas mass of GS-z14 large, despite the low gas fraction previously inferred from ALMA? | E: Three independent estimates: H I mass from N_HI, Kennicutt-Schmidt relation from Sigma_SFR, and the metal-mass route from [O III] | R: M_HI = 5e9 Msun; log M_gas = 9.8 +/- 0.3 (KS); M_Z = (2.0 +/- 0.6)e7 Msun giving ~10^9.8 Msun | F: Total gas mass ~10^9.8 Msun and f_gas >~ 0.9, with the ISM mostly H I | **supported**
- H: Is the derived gas mass compatible with the [C II]-158um non-detection? | E: Convert the [C II] limit to an H I mass using the metallicity-dependent relation | R: M_HI < 10^9.9 Msun (3 sigma) vs M_HI from DLA = 5e9 Msun | F: The gas mass is consistent with the [C II] non-detection when the scaling is applied to the neutral gas | **supported**
- H: Is the absorbing gas more pristine than the star-forming regions probed by [O III]? | E: Derive A_V from the UV slope and divide by N_HI; compare to GRB sightlines and local galaxies | R: A_V/N_HI = (1.3 +/- 0.6)e-23 mag cm^2; implied -1.95 < [M/H] < -1.15 | F: The line-of-sight gas has a low dust-to-gas ratio and lower metallicity than the emission-line value | **supported**

## Reasoning

- Why this data: Combine JWST DLA measurement with the ALMA far-infrared constraints to probe the full baryonic matter budget  
  > "Here we examine the constraints delivered from the far-infrared line transitions in context of the H i column density and physical properties to probe the full baryonic matter budget of GS-z14." (Observations)
- Why this method: A smooth power-law continuum is adequate because more complex shapes do not change N_HI at high column density  
  > "Introducing more complex spectral shapes or prominent Ly$\alpha$ emission does not significantly affect the derived $N_{\rm HI}$ (cite: Heintz24_DLA)" (Analysis and results)
- Alternative: IGM-only (x_HI = 1) absorption model gave a worse fit than IGM+DLA  
  > "provides a statistically worse fit to the data with $\chi_\nu^2 = 1.69$" (Analysis and results)
- Alternative: Purely nebular two-photon continuum model rejected because the UV turnover is inconsistent with the data  
  > "This matches well the slope of the spectrum, but the strong UV turnover is inconsistent with the data ($\chi_\nu^2 = 1.53$)." (Analysis and results)
- How they decided it was enough: _not stated_
- Limitation (authors): H I mass from N_HI depends heavily on the assumed geometry  
  > "However, this estimate of $M_{\rm HI}$ from the DLA $N_{\rm HI}$ is heavily dependent on the assumed geometry of the system." (Analysis and results)
- Limitation (authors): A_V is only an upper bound on the dust in the line of sight  
  > "This quantity is effectively the maximum allowed amount of dust in the line-of-sight that will extinguish the light" (Analysis and results)
- Caveat (inferred, ours): Gas mass fraction rests on a single-sightline N_HI, an assumed R_HI = 3 R_UV and spherical geometry; the three gas-mass routes are not fully independent (all use the same R_UV, SFR and metallicity)
- Caveat (inferred, ours): Conclusions quote log M_gas = 9.5 +/- 0.3 and f_gas ~ 0.7-0.9 while the abstract and results give 9.8 +/- 0.3 and >~ 0.9; the numbers are not reconciled
- Caveat (inferred, ours): No ALMA data are reprocessed; all far-infrared constraints depend on other papers, so the ALMA contribution cannot be checked here
- Caveat (inferred, ours): Priors and the continuum/IGM model details of the dynesty fit are not given, and A_V relies on an assumed intrinsic slope of -3 and an SMC curve

## Reproducibility

- Data public (paper): JWST data from MAST; prism spectrum posted on Zenodo; ALMA public status not stated  
  > "The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute" (Observations); "Available at <https://doi.org/10.5281/zenodo.12578542>" (footnote 1)
- Products in archive: _not stated_
- Missing: Priors and sampler settings for the DLA fit
- Missing: Explicit Kennicutt-Schmidt coefficients and H I mass formula
- Missing: ALMA line fluxes and limits are quoted from other papers; no reprocessing recipe here
- Missing: Pipeline version for the NIRSpec reduction
- Data volume (inferred): Small: one 1-D prism spectrum (kB-MB) for the main fit; ALMA data not reprocessed
- Score (inferred): 3/5, The main spectral fit can be redone from the public Zenodo prism spectrum, and numeric results are given, but priors, K-S coefficients and mass formulas are missing and the ALMA inputs are taken from other papers.
- Rediscovery candidate: no, Recipe is incomplete (priors, K-S relations, geometry formulas) and the ALMA measurements are inherited from other papers, so the key numbers cannot be rebuilt solely from this text.

## Links

- Method: (cite: Carniani24a) (Original NIRSpec spectrum, forcepho photometry, flux correction and galaxy size and magnification)
- Method: (cite: Heintz24_z54) (Voigt-profile DLA fitting method followed here)
- Method: (cite: Heintz21) (Metallicity-dependent [C II]-to-H I conversion)
- Method: (cite: Heintz23_mz) ([O III] luminosity to metal mass calibration)
- Companion: (cite: Carniani24b) (ALMA [O III] detection, SED modelling and physical properties of GS-z14)
- Companion: (cite: Schouws24) (ALMA [O III]-88um and dust continuum observations of GS-z14)
- Companion: (cite: Schouws25) (Deep ALMA [C II]-158um non-detection and molecular gas limit)
- Related: JADES (JWST Advanced Deep Extragalactic Survey)
- Related: FRESCO
- Related: JADES Origins Field
- Related: JWST programs 1210, 1287, 3215
- Related: ALMA 2023.A.00037.S
- Related: ALMA 2024.A.00007.S

## Checks

```json
{
 "quotes": 112,
 "quotes_ok": 112,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 121,
  "stated": 76,
  "rate": 0.628
 },
 "evidence_ok": true
}
```
