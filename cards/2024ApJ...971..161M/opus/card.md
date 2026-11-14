# SERENADE. II. An ALMA Multiband Dust Continuum Analysis of 28 Galaxies at 5 &lt; z &lt; 8 and the Physical Origin of the Dust Temperature Evolution

`2024ApJ...971..161M` | The Astrophysical Journal 2024 | first author: Mitsuhashi, Ikki | arXiv: 2311.16857 | DOI: 10.3847/1538-4357/ad5675

Card schema 1.0 | model claude-opus-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Constrain dust temperature, IR luminosity, the IRX-beta_UV relation and dust-obscured SFR density for UV-bright LBGs at z~6 using multi-band (rest 88 and 158 micron) ALMA continuum, and explain the redshift evolution of T_dust.  
  > "In this paper, we examine the FIR property of galaxies at" (1. INTRODUCTION); "Hence, obtaining representative" (1. INTRODUCTION)
- Target **SERENADE Cycle-9 LBGs (18 observed, e.g. J135348-001026, J091436+044231, J142824+015934)**: coordinates _not stated_; z/distance z_spec = 5.82-6.32 (Table 1)  
  > "We select 19 galaxies as our targets to encompass a broad dynamic range in a Star Formation Rate (SFR), including two lensed galaxies (see Table 1)." (2.1. SERENADE overview); distance from spectroscopic redshifts from [C ii]/[O iii] or Lya/UV absorption lines  
  > "We select 19 galaxies as our targets to encompass a broad dynamic range in a Star Formation Rate (SFR), including two lensed galaxies (see Table 1)." (2.1. SERENADE overview)
- Target **SERENADE pilot (J1211+0118, J0217+0208, J0235+0532)**: coordinates _not stated_; z/distance z_spec = 6.0293, 6.2037, 6.0901 (Table 1)  
  > "We have also incorporated three galaxies reported in Harikane et al. (2020b) for the" (2.1. SERENADE overview); distance from _not stated_
- Target **z~7 literature LBGs (COS-2987030247, COS-3018555981, UVISTA-Z-001, UVISTA-Z-007, UVISTA-Z-019, A1689-zD1, B14-65666, REBELS-12, REBELS-25, REBELS-38)**: coordinates _not stated_; z/distance z_spec = 6.577-7.3459 (Table 1)  
  > "We collect galaxies at 5 < z < 8 with both Band-6 and Band-8 observations publicly available in the ALMA science archive." (2.2. Addtional 5 < z < 8 samples); distance from literature (Table 1 references)  
  > "We collect galaxies at 5 < z < 8 with both Band-6 and Band-8 observations publicly available in the ALMA science archive." (2.2. Addtional 5 < z < 8 samples)
- Target **z~5.5 LBGs HZ4, HZ6, HZ9, HZ10**: coordinates _not stated_; z/distance z_spec = 5.293-5.657 (Table 1)  
  > "HZ6 5.293" (Table 1); distance from Faisst et al. 2020b (Table 1)  
  > "z ∼ 5.5 LBGs (Faisst et al. 2020b)" (Table 1)

## Data provenance

- ALMA projects: 2022.1.00522.S, 2015.1.00540.S, 2015.1.01406.S, 2016.1.00954.S, 2017.1.00190.S, 2017.1.00508.S, 2017.1.00697.S, 2017.1.00775.S, 2019.1.01634.L, 2021.1.01297.S, 2021.1.00318.S
- bands: Band-6 (rest 158 um) and Band-8 (rest ~88 um); archival also covers rest 205, 122, 110, 52 um for some galaxies (Table 2)  
  > "The ALMA Band-8, covering rest-frame" (1. INTRODUCTION); "Since one targeting galaxy (J023536-031737) was not observed in either Band-6 or Band-8, we address the remaining 18 LBGs in this paper." (2.1. SERENADE overview)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1/2/3  
  > "Observations were conducted between October and December 2022 using the C43-1/2/3 configuration." (2.1. SERENADE overview)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: October-December 2022 (SERENADE Cycle-9)  
  > "Observations were conducted between October and December 2022 using the C43-1/2/3 configuration." (2.1. SERENADE overview)
- pi or archival as stated: PI program (SERENADE, PI Harikane) plus pilot data from Harikane et al. 2020b and public archival data for 14 literature galaxies  
  > "an ALMA program (ID:#2022.1.00522.S, PI: Yuichi Harikane)" (2.1. SERENADE overview); "We collect galaxies at 5 < z < 8 with both Band-6 and Band-8 observations publicly available in the ALMA science archive." (2.2. Addtional 5 < z < 8 samples)
- Line: [C ii] 158 um fine structure (not stated)
- Line: [O iii] 88 um fine structure (not stated)
- Other facility **Subaru/HSC (HSC-SSP)**: parent sample and i, z, y photometry; z-band background images  
  > "band photometry from the HSC-PDR3 catalog (Aihara et al. 2022) for the galaxies originally identified in the wide layer of the HSC-SSP survey" (3.1. Measurement of beta_UV and M_UV)
- Other facility **HST**: photometry for some galaxies and Y105J125H160 background images for lensed galaxies  
  > "mostly from _HST_ observations" (3.1. Measurement of beta_UV and M_UV)
- Other facility **VISTA / UKIDSS / VIKING**: NIR photometry  
  > "we combine the photometries at NIR wavelengths with the" (3.1. Measurement of beta_UV and M_UV)
- External data: Broad-band photometry from COSMOS2020, SPLASH-SXDF and VISTA Deep Extragalactic Observations catalogs  
  > "SPLASHSXDF multi-wavelength catalog (Mehta et al. 2018)," (3.1. Measurement of beta_UV and M_UV) [from Weaver et al. 2022; Mehta et al. 2018; Jarvis et al. 2013]
- External data: Directly adopted beta_UV and/or M_UV when photometry not public  
  > "when the photometries are not publicly available." (3.1. Measurement of beta_UV and M_UV) [from e.g., Huang et al. 2016; Smit et al. 2018]
- External data: Lens magnification factors 2.5 and 4.4  
  > "Lens magnification factors are 2.5 and 4.4 for J024801-033258 and J045408-030014, respectively" (Table 1) [from Bradley et al. 2014; Huang et al. 2016]
- External data: UV luminosity function at z~6  
  > "Our starting point is the galaxy UV luminosity function presented in" (4.2. SFR density at z ~ 6) [from Harikane et al. (2022)]
- External data: IRX-beta_UV relation (extinction curve) used as fiducial  
  > "we adopt the extinction curve reported in Fudamoto et al. (2020a) as a fiducial one due to its alignment with our results." (4.2. SFR density at z ~ 6) [from Fudamoto et al. (2020a)]
- External data: M_UV-beta_UV relation of fainter HST galaxies  
  > "constrained with our galaxies and the fainter galaxies in Bouwens et al. (2014)." (Figure 7 caption) [from Bouwens et al. (2014)]
- External data: UV/IR SFR conversion factors  
  > "following the conversion factors in Madau & Dickinson (2014) with Chabrier" (4.2. SFR density at z ~ 6) [from Madau & Dickinson (2014); Chabrier (2003)]
- External data: Stellar mass to M_UV scaling relations  
  > "we convert them to _M_ UV based on the scaling relations in Song et al. (2016)." (4.3. Obscured fraction of the star formation) [from Song et al. (2016)]
- External data: Gas depletion timescale and metallicity redshift evolution, K1500, D_sun  
  > "For the redshift evolution of the metallicity, we assume a power-law dependence of" (5. DISCUSSION); "following in Tacconi et al. (2020) for the Chabrier IMF." (5. DISCUSSION) [from Tacconi et al. 2020; Sanders et al. 2021; Rémy-Ruyer et al. 2014]
- External data: z=0.5 T_dust of 27.2 K used to calibrate tau_eff  
  > "in Schreiber et al. (2018) for galaxies with" (5. DISCUSSION) [from Schreiber et al. (2018)]
- Simulation/model as data: Analytical T_dust model of Sommovigo et al. (2022) combined with observed t_gas and Z evolution  
  > "by combining the analytical model presented in Sommovigo et al. (2022) with recent observational constraints." (5. DISCUSSION)

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

- task: CASA/tclean  
  > "Subsequently, we generate continuum images with CASA/tclean." (3.3. Dust continuum fluxes)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "in addition to the naturally-weighted image without tapering." (3.3. Dust continuum fluxes)
- uv taper: 0.25, 0.5, 1.0, 2.0 and 3.0 arcsec plus untapered; 1.0 arcsec taper for line search cubes  
  > "To recover all possible extended structures, we reconstruct images with" (3.3. Dust continuum fluxes); "in addition to the naturally-weighted image without tapering." (3.3. Dust continuum fluxes)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: mask 3x line velocity dispersion around detected [C ii]/[O iii]; for non-detections exclude +-0.8 GHz (+-500 km/s) around expected frequency  
  > "we mask a frequency range that is three times wider than the line velocity dispersion using CASA/mstransform." (3.3. Dust continuum fluxes); "For cases with non-detection, we exclude the frequencies at" (3.3. Dust continuum fluxes)
- primary beam correction: noise measured in non-PB-corrected images within FoV where PB > 0.5  
  > "Noise levels are estimated in the images without primary beam corrections as the root-mean-square (RMS) of pixel values within the Field-of-View (FoV) where the primary beam correction value exceeds 0.5." (3.3. Dust continuum fluxes)
- array combination: _not stated_
- smoothing: stacking images smoothed to round 2.0 arcsec beam with CASA/imsmooth from 1 arcsec tapered images  
  > "beam by applying CASA/imsmooth for the images with a prior" (3.4. Stacking analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CMB heating and background correction of MBB  
  > "After considering these effects following da Cunha et al. (2013), the equation (2) becomes" (3.5. T_dust and L_IR estimation) [from da Cunha et al. (2013)]
- Lya line flux from spectra  
  > "calculated from spectra following the methodologies in Harikane et al. (2020b)." (3.1. Measurement of beta_UV and M_UV) [from Harikane et al. (2020b)]
- Combining NIR survey photometry with HSC izy  
  > "photometry following Matsuoka et al. (2019)." (3.1. Measurement of beta_UV and M_UV) [from Matsuoka et al. (2019)]
- Treatment of upper limits in likelihood  
  > "In the case that the measured ALMA fluxes in any bands are upper limit, we adopt the methodology described in Sawicki (2012)" (3.5. T_dust and L_IR estimation) [from Sawicki (2012)]
- Dust opacity normalization (Milky Way value) kappa*=10.41 cm2/g at 1900 GHz  
  > "with the nomalization of Milky Way value" (3.5. T_dust and L_IR estimation) [from e.g., Bakx et al. 2021; Algera et al. 2023b; Ferrara et al. 2022]
- SFR function integrated down to M_UV = -17  
  > "We then integrate the SFR function with a range from" (4.2. SFR density at z ~ 6) [from previous studies (e.g., Bouwens et al. 2012, 2021)]
- Equations (7) and (9) of analytic T_dust model  
  > "We start with equations (7) and (9) in Sommovigo et al. (2022)," (5. DISCUSSION) [from Sommovigo et al. (2022)]
- Pilot data for 3 galaxies  
  > "We have also incorporated three galaxies reported in Harikane et al. (2020b) for the" (2.1. SERENADE overview) [from Harikane et al. 2020b]

### Not stated but needed to reproduce (our reading)

- Calibration procedure (pipeline vs manual), CASA version, flux calibrators and flux-scale uncertainty
- Whether self-calibration was applied
- tclean deconvolver, cleaning threshold, masks, cell size and image size
- Continuum bandwidth and spectral setup/frequencies per target
- Achieved beam sizes and rms per band (only shown in Figure 2 thumbnails)
- Which sources had modest tapers applied before imfit and taper values
- emcee walkers, steps, burn-in and convergence criteria
- Whether flux calibration uncertainty is added to flux errors in MBB fitting
- Functional form of the best-fit f_obs-M_UV relation and bootstrap details
- Exact archival dataset-to-galaxy mapping and any data selection for the 14 literature galaxies
- UVMultifit model setup beyond Sersic n=1

## Analysis recipe

1. **measure UV slope and absolute magnitude**: chi^2 fit of power-law f_lambda ∝ lambda^beta with IGM truncation at 1216 A to broad-band photometry, including Lya where detected; M_UV from model at rest 1500 A  
  > "We take into account the contribution of the Ly _α_ emission line if the line is clearly detected in the spectroscopic observations." (3.1. Measurement of beta_UV and M_UV)
   - parameter: grid: log normalization [-0.5,0.5] in y-band, beta_UV in [-5,3]; 1 sigma from Delta chi^2 = 1  
  > "We fit model UV SEDs created with the logarithmic ranges of [-0.5, 0.5] for the normalization flux in the" (3.1. Measurement of beta_UV and M_UV)
   - assumption: lensed M_UV corrected for magnification  
  > "The absolute magnitudes, _M_ UV, are corrected for the magnification factors, while the observed magnitudes are not." (Table 1)
   - fitting: minimum chi^2 grid  
  > "showing the minimum _χ_ [2] and the deviation at which" (3.1. Measurement of beta_UV and M_UV)
   - validation: SHELLQs-only subsample to test selection bias  
  > "As a result, there is no major change if we calculate the average values only with the galaxies from the SHELLQs survey." (6)
2. **identify lines and make line-free continuum images**: Gaussian fit to spectra at phase center from 1 arcsec tapered cubes; mask line channels with mstransform; tclean continuum images with multiple uv tapers  
  > "we mask a frequency range that is three times wider than the line velocity dispersion using CASA/mstransform." (3.3. Dust continuum fluxes); "Subsequently, we generate continuum images with CASA/tclean." (3.3. Dust continuum fluxes)
   - software: CASA mstransform, CASA tclean
   - parameter: non-detection exclusion +-0.8 GHz (+-500 km/s)  
  > "For cases with non-detection, we exclude the frequencies at" (3.3. Dust continuum fluxes)
   - fitting: _not stated_
   - validation: _not stated_
3. **detect and measure continuum fluxes**: peak flux within 0.5 arcsec radius; S/N = highest among tapered images; detection S/N>3.5; total fluxes via imfit (both bands detected), 1 arcsec taper peak (158 only), or upper limits from natural images  
  > "As the fiducial signal-to-noise ratio (S/N) of each galaxy, we adopt the highest S/N among the images." (3.3. Dust continuum fluxes); "To avoid the flux misestimation in imfit due to the mismatch of dirty and clean beams, we apply modest tapers for some sources before running imfit." (3.3. Dust continuum fluxes)
   - software: CASA imfit
   - assumption: continuum emission within a single beam  
  > "under the assumption that dust continuum emission is included within a single beam." (3.3. Dust continuum fluxes)
   - fitting: _not stated_
   - validation: compared to visibility fitting with UVMultifit (Sersic n=1)  
  > "we also measure the fluxes from visibility data with UVMultifit" (A. FLUX COMPARISON); "We find a very good consistency between visibility- and image-based flux densities we used in this work." (A. FLUX COMPARISON)
4. **stack continuum in beta_UV bins**: stack Band-6 and Band-8 images smoothed to 2 arcsec round beam at UV positions in bins beta_UV=[-3,-1] and [-1,1], weighted by L_UV^mean/L_UV,i  
  > "Only galaxies observed in both Band-6 and Band-8 are used in the stacking analysis for the sake of homogeneity." (3.4. Stacking analysis); "allows us to avoid bias towards bright galaxies." (3.4. Stacking analysis)
   - software: CASA imsmooth
   - assumption: UV-IR offsets (<0.35 arcsec) do not affect flux  
  > "spatial offsets identified in individual galaxies between UV and IR do not significantly impact the flux measurement" (3.4. Stacking analysis)
   - fitting: _not stated_
   - validation: weighted median gives no major difference  
  > "We find that there is no major difference when we use the weighted median instead of the weighted aver" (3.4. Stacking analysis)
5. **fit modified blackbody for T_dust, M_dust, L_IR**: optically thin MBB with CMB correction fitted by MCMC (emcee); upper limits via Sawicki (2012)  
  > "We use the Markov Chain Monte Carlo (MCMC) algorithm to fit the MBB profiles by utilizing the emcee library." (3.5. T_dust and L_IR estimation); "In this work, we use equation (4) to estimate" (3.5. T_dust and L_IR estimation)
   - software: emcee
   - parameter: log-uniform priors log M_dust in [4,10], T_dust in [T_CMB,z,120] K; Gaussian beta_dust prior mean 1.8 sigma 0.5  
  > "We adopt a logarithmically uniform prior on the dust masses and dust temperatures with a range of" (3.5. T_dust and L_IR estimation); "we adopt a Gaussian prior with a mean value of" (3.5. T_dust and L_IR estimation)
   - assumption: kappa_nu = kappa*(nu/nu*)^beta, Milky Way normalization [10.41 cm2/g, 1900 GHz]; T_dust=45 K assumed when unconstrained  
  > "with the nomalization of Milky Way value" (3.5. T_dust and L_IR estimation); "For the galaxies whose dust temperatures are not constrained due to insufficient observations or non-detections, we assume" (Table 2)
   - fitting: MCMC; best fit and 1 sigma from modes with highest posterior density intervals  
  > "uncertainties from the modes with the highest posterior density intervals." (3.5. T_dust and L_IR estimation)
   - validation: T_dust prior upper edge 150 K and uniform beta prior [1.5,2.5] give no significant change; optically thick lambda0=100 um leaves L_IR unchanged  
  > "Note that there is no significant impact on our conclusion if we change the upper edge of the prior distribution of" (3.5. T_dust and L_IR estimation); "We note that the resulting _L_ IR does not change under the assumption of the optically thick MBB with" (3.5. T_dust and L_IR estimation)
6. **derive IRX-beta_UV relation**: compare individual and stacked IRX vs beta_UV with Calzetti, Meurer, SMC and Fudamoto relations  
  > "We find that our result from the stacking analysis supports a shallower" (4.1. beta_UV vs IRX relationship)
   - assumption: upper limits assume T_dust = 45 K  
  > "Meanwhile, the upper limits of the undetected galaxies are calculated by assuming" (4.1. beta_UV vs IRX relationship)
   - fitting: _not stated_
   - validation: SHELLQs-only subsample consistent; beta_UV shift test  
  > "find that the result remains consistent even when selecting galaxies only from the SHELLQs survey." (4.1. beta_UV vs IRX relationship)
7. **compute obscured and total SFRD at z~6**: convert UV LF via M_UV-beta_UV and Fudamoto IRX-beta relations into UV+IR SFRs; bootstrap errors; integrate to M_UV=-17  
  > "We estimate uncertainties using bootstrap techniques, ensuring the propagation of uncertainties in each relationship." (4.2. SFR density at z ~ 6)
   - parameter: SFR_UV = 0.76e-28 L_UV, SFR_IR = 2.64e-44 L_IR (Chabrier IMF)  
  > "following the conversion factors in Madau & Dickinson (2014) with Chabrier" (4.2. SFR density at z ~ 6)
   - fitting: _not stated_
   - validation: alternative SMC and Calzetti/Meurer combinations (Table 3)  
  > "For a further comparison, we also calculate the SFRD with the different combinations of the" (4.2. SFR density at z ~ 6)
8. **obscured fraction vs M_UV**: stack rest-158 um in three M_UV bins, convert to L_IR with T_dust=45 K, beta=1.8; fit f_obs-M_UV with bootstrap; integrate with UV LF  
  > "assuming an optically-thin MBB profile with" (4.3. Obscured fraction of the star formation)
   - assumption: T_dust = 45 K, beta_dust = 1.8  
  > "to perform a fair comparison with the previous results" (4.3. Obscured fraction of the star formation)
   - fitting: best fit with bootstrap 1 sigma  
  > "The best-fit _f_ obs - _M_ UV relation and 1 _σ_ uncertainties estimated by bootstrap are also shown" (4.3. Obscured fraction of the star formation)
   - validation: _not stated_
9. **measure average T_dust at z~6-7 and model its evolution**: average stack of 22 galaxies, MBB fit; compare with analytic Sommovigo et al. (2022) model using t_gas and Z evolution for M*=1e10 Msun  
  > "resulting in a total of 22 galaxies for the stacking analysis." (4.4. T_dust evolution); "by combining the analytical model presented in Sommovigo et al. (2022) with recent observational constraints." (5. DISCUSSION)
   - software: emcee
   - parameter: tau_eff = 1.3 calibrated to Schreiber et al. z=0.5 T_dust; beta_dust=1.8; D_sun=1/162; K1500=1.4e10  
  > "in Schreiber et al. (2018) for galaxies with" (5. DISCUSSION)
   - assumption: metallicity d log(O/H)/dz = -0.11; also case of no Z evolution at z>3.3  
  > "For the redshift evolution of the metallicity, we assume a power-law dependence of" (5. DISCUSSION); "we also compute the redshift evolution under the assumption of no metallicity evolution at" (5. DISCUSSION)
   - fitting: MBB MCMC with Gaussian beta prior as step 5  
  > "We conduct an average stack and estimate" (4.4. T_dust evolution)
   - validation: median stack gives no major difference  
  > "There is no major difference in the resulting" (4.4. T_dust evolution)

## Software

- **CASA (mstransform, tclean, imfit, imsmooth)** : line masking, continuum imaging, flux fitting, smoothing for stacking  
  > "Subsequently, we generate continuum images with CASA/tclean." (3.3. Dust continuum fluxes); "we execute CASA/imfit" (3.3. Dust continuum fluxes)
- **emcee** : MCMC MBB fitting  
  > "We use the Markov Chain Monte Carlo (MCMC) algorithm to fit the MBB profiles by utilizing the emcee library." (3.5. T_dust and L_IR estimation)
- **UVMultifit** : visibility-based flux check  
  > "we also measure the fluxes from visibility data with UVMultifit" (A. FLUX COMPARISON)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| average (stacked) T_dust at z~6-7 | 40.9 | +10.0/-9.1 | K | 9 | The stacked result suggests that an average dust temperature is |
| scatter of individual T_dust at z=5-8 | ~12 | not stated | K | 9 | The individual measurements have a large scatter of |
| dust-obscured fraction of total SFRD at z~6 (IRX-beta method) | 31 | +8/-8 | % | 7 | the dust-obscured star formation in UV-selected galaxies contributes |
| maximum dust-obscured contribution (Calzetti case) | ~45 | not stated | % | 7 | but the maximum contribution of the dust-obscured star formation is |
| dust-obscured fraction of SFRD (f_obs-M_UV method) | 15 | +17/-8 | % | 8 | The contribution of dust-obscured star formation among LBGs based on the |
| log total SFRD (B14+this work, Fudamoto IRX) | -1.82 | +0.17/-0.17 | log Msun yr^-1 Mpc^-3 | 7 | The calculated SFRDs are listed in Table 3. |
| log dust-obscured SFRD (B14+this work, Fudamoto IRX) | -2.33 | +0.23/-0.25 | log Msun yr^-1 Mpc^-3 | 7 | The calculated SFRDs are listed in Table 3. |
| M_UV-beta_UV slope (normalized at M_UV=-22) | -0.76 | ±0.14 | dimensionless | 1 | Our best-fit _M_ UV _−_ _β_ UV relationship normal |
| M_UV-beta_UV intercept at M_UV=-22 | -1.51 | ±0.15 | dimensionless | 1 | Our best-fit _M_ UV _−_ _β_ UV relationship normal |
| IRX offset from T_dust difference vs literature assumptions | ~0.7 | not stated | dex | 6 | and it leads to |
| number of individually detected galaxies with T_dust | 21 of 28 | not stated | galaxies | 3 | Among 28 galaxies, 21 are individually detected |

## Qualitative findings

- Of 14 SERENADE galaxies with both bands, six detected in both, two only at 158 um, six undetected  
  > "six galaxies are detected in both the rest-frame 158" (3.3. Dust continuum fluxes)
- UV-selected SERENADE galaxies span L_IR from normal galaxies to dusty starburst levels  
  > "While our target galaxies were originally selected by their bright UV emission, the" (3.5. T_dust and L_IR estimation)
- Positive trend between UV brightness and f_obs at z~6  
  > "a positive trend between the UV brightness and" (4.3. Obscured fraction of the star formation)
- Bright galaxies (M_UV<-22) redder than B14 extrapolation  
  > "generally exhibit redder slopes than the extrapolation of the relation constrained with faint galaxies in Bouwens et al. (2014)." (Figure 1 caption)

## Claim tuples

- H: IRX-beta_UV relation at z~6 differs from local/z~2-4 relations | E: multi-band MBB-based L_IR for individual and stacked galaxies vs beta_UV | R: shallower than Calzetti, Meurer and SMC; matches Fudamoto et al. 2020a | F: IRX-beta relation at z~6 is shallower (~1 dex lower than z~3 at beta~0) | **supported**
- H: Dust-obscured star formation in LBGs dominates z~6 SFRD | E: UV LF converted via M_UV-beta and IRX-beta relations, and via f_obs-M_UV | R: 31+8-8% and 15+17-8%; max ~45% with Calzetti | F: obscured star formation of LBGs is not dominant (~30%) | **refuted**
- H: T_dust increases with redshift; steepness of evolution | E: stacked MBB fit of 22 galaxies at z~6-7 | R: T_dust = 40.9 +10.0/-9.1 K | F: supports linear (1+z) evolution rather than quadratic | **supported**
- H: T_dust evolution driven by gas depletion time and metallicity evolution | E: analytic Sommovigo et al. 2022 model with Tacconi t_gas and Sanders Z evolution | R: model matches z~6-7 stack and lower-z results | F: evolution reproduced by ~0.6 dex increase in t_gas and ~0.4 dex Z decrease; scatter by MS and MZR scatter | **supported**

## Reasoning

- Why this data: Band-8 samples rest ~90 um near dust SED peak, enabling T_dust with Band-6  
  > "continuum near the peak of the dust thermal emission" (1. INTRODUCTION)
- Why this method: homogeneous re-analysis of archival data for fair comparison; stacking to avoid detection bias  
  > "We re-analyze the archival data in a homogeneous way to our target galaxies at" (1. INTRODUCTION); "to obtain an average representation that is not biased by individual detection." (3.4. Stacking analysis)
- Alternative: Optically thick MBB with lambda0=100 um: L_IR unchanged, T_dust higher  
  > "whereas _T_ dust becomes higher than those with the optically thin assumption." (3.5. T_dust and L_IR estimation)
- Alternative: Uniform beta_dust prior [1.5,2.5]  
  > "The results do not strongly depend on the prior distribution of" (3.5. T_dust and L_IR estimation)
- Alternative: SMC and Calzetti IRX-beta combinations for SFRD  
  > "which is not preferred from the IRX measurements in this study." (4.2. SFR density at z ~ 6)
- Alternative: Peak fluxes in tapered images vs imfit; imfit preferred  
  > "We also find that CASA/imfit achieves better flux recovering than that from the images with the multiple taper scales." (3.3. Dust continuum fluxes)
- How they decided it was enough: _not stated_
- Limitation (authors): Misses very dusty galaxies (SMGs, HST-dark)  
  > "Note that our estimations of the dust-obscured star formation miss very dusty galaxies such as SMGs" (4.2. SFR density at z ~ 6)
- Limitation (authors): Heterogeneous selection may bias beta_UV; sample size small  
  > "although enlarging the sample size is imperative to draw robust conclusions." (6)
- Limitation (authors): beta_UV may be overestimated due to limited wavelength coverage; NIR needed  
  > "To secure robust measurements of UV slopes, NIR observations that cover the" (4.1. beta_UV vs IRX relationship)
- Limitation (authors): Some galaxies need shorter-wavelength or deeper data  
  > "need observations at shorter wavelengths or deeper observations are necessary to obtain more robust constraints on the parameters." (3.5. T_dust and L_IR estimation)
- Limitation (authors): No stellar mass or metallicity estimates for targets  
  > "do not have stellar mass _M_ _∗_ or the metallicity _Z_ estimates due to the lack of rest-frame optical coverage" (5. DISCUSSION)
- Limitation (authors): Possible AGN boosting of L_IR and T_dust  
  > "may suggest that the IR luminosity and the dust temperature are boosted by the possible presence of Type-2 AGN" (6. SUMMARY AND CONCLUSIONS)
- Caveat (inferred, ours): Text states T_dust ~25 K for the beta_UV=[-3:-1] stack, but Table 2 gives 50.4 K for that bin and 26.0 K for [-1,1]; possible label swap.
- Caveat (inferred, ours): T_dust with only two bands and beta_dust prior is highly prior-dependent; upper limits rely on assumed 45 K.
- Caveat (inferred, ours): Fiducial flux method varies by detection category (imfit vs peak in tapered image), which may introduce systematics between subsamples.
- Caveat (inferred, ours): Fudamoto 2020a and 2020c appear as the same reference, creating citation ambiguity in Table 3.

## Reproducibility

- Data public (paper): Archival literature datasets stated as public in ALMA science archive; SERENADE public status not stated  
  > "We collect galaxies at 5 < z < 8 with both Band-6 and Band-8 observations publicly available in the ALMA science archive." (2.2. Addtional 5 < z < 8 samples)
- Products in archive: _not stated_
- Missing: Calibration details and CASA version
- Missing: tclean parameters (cell, imsize, threshold, deconvolver)
- Missing: Per-source taper choices before imfit
- Missing: MCMC sampler configuration
- Missing: Exact mapping of archival projects to galaxies
- Missing: f_obs-M_UV fit form and bootstrap specifics
- Data volume (inferred): Tens of Band-6/Band-8 measurement sets across 11 projects; likely ~0.5-2 TB raw, much less as calibrated continuum.
- Score (inferred): 3/5, Analysis recipe (masking, tapers, MBB priors, stacking weights) is clearly described, but calibration and imaging parameters, MCMC settings and per-source choices are missing, and several inputs come from the literature.
- Rediscovery candidate: no, Archival data are stated public and results are numeric, but SERENADE data public status is not stated and key processing details (calibration, tclean, per-source tapers) are missing.

## Links

- Method: da Cunha et al. (2013) (CMB correction to MBB)
- Method: Sawicki (2012) (upper-limit likelihood)
- Method: Sommovigo et al. (2022) (analytic T_dust model)
- Method: Madau & Dickinson (2014) (SFR conversion factors)
- Companion: Paper I; Harikane et al. in prep (SERENADE emission line data)
- Companion: Harikane et al. 2020b (SERENADE pilot study)
- Companion: Mitsuhashi et al. (in prep) (visibility-based analysis details)
- Related: SERENADE
- Related: HSC-SSP
- Related: SHELLQs
- Related: REBELS
- Related: ALPINE
- Related: CRISTAL
- Related: COSMOS2020

## Checks

```json
{
 "quotes": 143,
 "quotes_ok": 143,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 11,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 130,
  "stated": 92,
  "rate": 0.708
 },
 "evidence_ok": true
}
```
