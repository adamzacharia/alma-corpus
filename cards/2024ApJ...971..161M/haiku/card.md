# SERENADE. II. An ALMA Multiband Dust Continuum Analysis of 28 Galaxies at 5 &lt; z &lt; 8 and the Physical Origin of the Dust Temperature Evolution

`2024ApJ...971..161M` | The Astrophysical Journal 2024 | first author: Mitsuhashi, Ikki | arXiv: 2311.16857 | DOI: 10.3847/1538-4357/ad5675

Card schema 1.0 | model claude-haiku-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: Measure the luminosity-weighted dust temperature and IR luminosity of z~5-8 UV-selected galaxies from multi-band ALMA continuum, and test the IRX-beta_UV relation, the dust-obscured SFR fraction, and the redshift evolution of T_dust.  
  > "allowing us to simultaneously measure the IR luminosity and dust temperature for a statistical sample of z ≳ 5 galaxies for the first time" (abstract); "we examine the FIR property of galaxies at z ∼ 6 with our new ALMA Band-6/8 observations" (Section 1 Introduction)
- Target **SERENADE LBG sample (28 galaxies at 5 < z < 8)**: coordinates _not stated_; z/distance 5 < z < 8 (individual z_spec listed in Table 1)  
  > "28 spectroscopicallyconfirmed bright Lyman-break galaxies at 5 < z < 8" (abstract); "We select 19 galaxies as our targets to encompass a broad dynamic range in a Star Formation Rate (SFR), including two lensed galaxies (see Table 1)." (Section 2.1 SERENADE overview); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00540.S, 2015.1.01406.S, 2016.1.00954.S, 2017.1.00190.S, 2017.1.00508.S, 2017.1.00697.S, 2017.1.00775.S, 2019.1.01634.L, 2021.1.01297.S, 2021.1.00318.S, 2022.1.00522.S
- bands: ALMA Band-6 and Band-8 (rest-frame 158 µm and 88 µm continuum)  
  > "we examine the FIR property of galaxies at z ∼ 6 with our new ALMA Band-6/8 observations" (Section 1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1/2/3  
  > "Observations were conducted between October and December 2022 using the C43-1/2/3 configuration." (Section 2.1 SERENADE overview)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: October to December 2022 (SERENADE Cycle-9 program)  
  > "Observations were conducted between October and December 2022 using the C43-1/2/3 configuration." (Section 2.1 SERENADE overview)
- pi or archival as stated: SERENADE program PI Yuichi Harikane for new data; other Band-6 and Band-8 data taken from the ALMA science archive  
  > "We collect galaxies at 5 < z < 8 with both Band-6 and Band-8 observations publicly available in the ALMA science archive." (Section 2.2 Additional 5<z<8 samples)
- Line: [C II] 158 µm fine structure line (not stated)
- Line: [O III] 88 µm fine structure line (not stated)
- Other facility **Subaru Hyper Suprime-Cam (HSC-SSP, HSC-PDR3)**: Parent sample selection and i, z, y-band photometry for UV fitting  
  > "We take _i_, _z_, and _y_ band photometry from the HSC-PDR3 catalog (Aihara et al. 2022)" (Section 3.1 Measurement of beta_UV and M_UV)
- Other facility **HST, VISTA, UKIDSS, COSMOS2020 and other catalogs**: Rest-frame UV broad-band photometry used to fit beta_UV and M_UV  
  > "For galaxies not covered by the aforementioned catalogs, we refer to the photometries measured in the literature (mostly from _HST_ observations" (Section 3.1 Measurement of beta_UV and M_UV)
- External data: Rest-frame UV photometry and beta_UV / M_UV values for 14 additional 5<z<8 galaxies with Band-6 and Band-8 data (re-analyzed here)  
  > "We incorporate an additional 14 galaxies at 5 < z < 8 with multi-band ALMA coverage in this study" (Section 2.2 Additional 5<z<8 samples) [from Faisst et al. 2020a; Watson et al. 2015; Knudsen et al. 2017; Hashimoto et al. 2019; Inoue et al. 2020; Sugahara et al. 2021; Bakx et al. 2021; Witstok et al. 2022; Akins et al. 2022; Algera et al. 2023b (cite keys as in paper)]
- External data: UV luminosity function from Harikane et al. 2022, used as starting point for SFRD  
  > "Our starting point is the galaxy UV luminosity function presented in Harikane et al. (2022)." (Section 4.2 SFR density at z~6) [from Harikane et al. 2022]
- External data: M_UV - beta_UV relation including fainter galaxies (Bouwens 2014)  
  > "the relation constrained with faint galaxies in Bouwens et al. (2014)." (Figure 1 caption) [from Bouwens et al. 2014 (B14)]
- External data: IRX-beta_UV relation of Fudamoto et al. 2020a adopted as fiducial extinction curve (intrinsic beta_UV = -2.62)  
  > "we adopt the extinction curve reported in Fudamoto et al. (2020a) as a fiducial one due to its alignment with our results." (Section 4.2 SFR density at z~6) [from Fudamoto et al. 2020a (cite: Fudamoto2020a)]
- External data: Literature IRX-beta and L_IR measurements at z~2-7 used for comparison (Fudamoto 2020b, Alvarez-Marquez 2019, Bowler 2023, Algera 2023a/b, Faisst 2020b, Inami 2022, Riechers 2013, Zavala 2018, Marrone 2018, Casey 2019, Reuter 2020)  
  > "The blue and green markers represent the previous measurements of the galaxies at z = 2 . 5–4" (Figure 6 caption) [from as listed in Figure 5 and Figure 6 captions]
- External data: T_dust compilation for z>=5 galaxies and stacking results (Schreiber 2018, Bethermin 2020, Viero 2022) and expected T_dust evolution  
  > "previous results based on the stacking analysis and the expected redshift evolution are shown in the blue, light blue, and green colors" (Figure 9 caption) [from Schreiber et al. 2018; Bethermin et al. 2020; Viero et al. 2022]
- External data: Gas depletion timescale evolution t_gas and metallicity evolution Z used in the T_dust model  
  > "observed redshift evolution of _t_ gas (Tacconi et al. 2020) and _Z_ (Sanders et al. 2021)" (Figure 9 caption) [from Tacconi et al. 2020; Sanders et al. 2021]
- External data: Reddy et al. 2018 prediction of shallow IRX-beta for low metallicity; used for comparison  
  > "They expect that galaxies with lower stellar metallicities at high redshift" (Section 4.1 beta_UV vs IRX relationship) [from Reddy et al. 2018]
- Simulation/model as data: Analytic T_dust model from Sommovigo et al. 2022 (equations 7-9) combined with observed t_gas and metallicity evolution; K1500 = 1.4e10 Lsun/(Msun/yr), tau_eff = 1.3, beta_dust = 1.8, D_sun = 1/162  
  > "We start with equations (7) and (9) in Sommovigo et al. (2022)," (Section 5 Discussion); "We use _K_ 1500 = 1 _._ 4 _×_ 10 [10] _L_ _⊙_ _/_ ( _M_ _⊙_ yr _[−]_ [1] ) following in Tacconi" (Section 5 Discussion)

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

- task: CASA/tclean for continuum images; CASA/imfit for fluxes  
  > "Subsequently, we generate continuum images with CASA/tclean." (Section 3.3 Dust continuum fluxes)
- deconvolver: _not stated_
- weighting robust: natural weighting for the fiducial and upper-limit images (robust value not stated)  
  > "in addition to the naturally-weighted image without tapering" (Section 3.3 Dust continuum fluxes)
- uv taper: 0.25, 0.5, 1.0, 2.0, 3.0 arcsec tapers in addition to natural weighting; 1.0 arcsec taper for 158 µm-only detections  
  > "we reconstruct images with uv taper of 0.25" (Section 3.3 Dust continuum fluxes); "we get the peak flux density and RMS in images with uv taper of 1.0" (Section 3.3 Dust continuum fluxes)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Channels within three times the line velocity dispersion masked (CASA/mstransform) when a line is detected; for non-detections frequencies at ±0.8 GHz (±500 km/s) around the prior redshift excluded  
  > "we mask a frequency range that is three times wider than the line velocity dispersion using CASA/mstransform" (Section 3.3 Dust continuum fluxes); "For cases with non-detection, we exclude the frequencies at ±0.8 GHz (equivalent to ±500 km s−1)" (Section 3.3 Dust continuum fluxes)
- primary beam correction: Noise measured on images without primary beam correction, within FoV where primary beam response exceeds 0.5  
  > "Noise levels are estimated in the images without primary beam corrections" (Section 3.3 Dust continuum fluxes)
- array combination: _not stated_
- smoothing: Stacked images convolved to a round 2.0 arcsec beam with CASA/imsmooth after a prior 1 arcsec taper  
  > "Given the variable nature of the ALMA beam sizes, we construct continuum images with a round" (Section 3.4 Stacking analysis)
- final beam: round 2.0 arcsec beam for stacked images; other beams per galaxy not stated in text  
  > "we construct continuum images with a round 2 ′′ . 0 beam by applying CASA/imsmooth" (Section 3.4 Stacking analysis)
- final rms: _not stated_

### Inherited from earlier work

- IRX-beta_UV relation and intrinsic beta_UV = -2.62 adopted as fiducial dust extinction curve for SFRD  
  > "we adopt the extinction curve reported in Fudamoto et al. (2020a) as a fiducial one due to its alignment with our results." (Section 4.2 SFR density at z~6) [from Fudamoto et al. 2020a (cite: Fudamoto2020a)]
- Analytic T_dust model and equations (7), (9) from Sommovigo et al. 2022  
  > "by combining the analytical model presented in Sommovigo et al. (2022) with" (Section 5 Discussion) [from Sommovigo et al. 2022]
- CMB correction applied to the MBB flux equation following da Cunha et al.  
  > "After considering these effects following da Cunha et al." (Section 3.5 T_dust and L_IR estimation) [from da Cunha et al. 2013]
- Upper-limit likelihood treatment (Gaussian integrated to 3-sigma upper limit)  
  > "we adopt the methodology described in Sawicki (2012), which accounts for the Gaussian noise distribution" (Section 3.5 T_dust and L_IR estimation) [from Sawicki 2012]
- Lyman-alpha brightness obtained following the methodology of Harikane et al. 2020b  
  > "The brightness of the Ly α line is obtained from the literature or calculated from spectra following the methodologies in Harikane et al. (2020b)." (Section 3.1 Measurement of beta_UV and M_UV) [from Harikane et al. 2020b]
- Photometry combination of NIR with i, z, y bands  
  > "we combine the photometries at NIR wavelengths with the _i_, _z_, and _y_ -band photometry following Matsuoka et al. (2019)." (Section 3.1 Measurement of beta_UV and M_UV) [from Matsuoka et al. 2019]
- Conversion of M_* to M_UV and f_obs comparison scaling relations  
  > "we convert them to _M_ UV based on the scaling relations in Song et al. (2016)." (Section 4.3 Obscured fraction of the star formation) [from Song et al. 2016]
- Milky Way dust opacity normalization [kappa*, nu*] = [10.41 cm^2 g^-1, 1900 GHz]  
  > "with the nomalization of Milky Way value" (Section 3.5 T_dust and L_IR estimation) [from Bakx et al. 2021; Algera et al. 2023b; Ferrara et al. 2022]
- Dust-to-gas ratio D_sun = 1/162 and K1500 conversion factor  
  > "following in Tacconi et al. (2020) for the Chabrier IMF" (Section 5 Discussion) [from Remy-Ruyer et al. 2014; Tacconi et al. 2020]

### Not stated but needed to reproduce (our reading)

- Exact CASA version, pipeline or manual calibration route, and calibrator/flux scale for each program
- Per-galaxy synthesized beam sizes and image cell/size settings for the tclean runs
- Deconvolution settings (niter, threshold, masking, cleaning mode) for tclean
- Which uv taper is used for each galaxy and how the fiducial flux is chosen among tapers
- Line-free channel selection for galaxies with detected lines beyond the mask width and the detected line widths
- Detailed imfit configuration (initial guesses, fitted component model, Gaussian vs point source treatment)
- Stacking details: reference position, pixel grid, bootstrap or uncertainty method, and which galaxies enter each stack
- emcee configuration: number of walkers, steps, burn-in, convergence test and initial state
- Treatment of the Ly-alpha contribution and redshift adopted for each galaxy when fitting beta_UV
- Photometric catalogs and Table 1 entries for galaxies with missing bands
- Rest-frame 88/158 µm flux measurements for the literature sample reproduced from the cited papers (not provided in this paper)
- Input values used for literature comparison points in Figures 5, 6, 9 (not tabulated here)
- Visibility-based fluxes from UVMultifit used in Appendix A (details deferred to a future paper)

## Analysis recipe

1. **measure UV slope beta_UV and M_UV**: Fit a power-law f_lambda ∝ lambda^beta_UV with truncation at 1216 Å to broad-band photometry; grid over normalization and slope; M_UV from model spectrum at 1500 Å  
  > "We fit the broad-band photometry from the catalogs to estimate β UV and M UV, assuming a simple power-law spectral shape" (Section 3.1 Measurement of beta_UV and M_UV)
   - parameter: Normalization log range [-0.5, 0.5] in y-band; beta_UV range [-5, 3]; truncation at λrest = 1216 Å  
  > "We fit model UV SEDs created with the logarithmic ranges of [-0.5, 0.5]" (Section 3.1 Measurement of beta_UV and M_UV)
   - assumption: Ly-alpha emission included when clearly detected in spectroscopy; IGM truncation at 1216 Å  
  > "We take into account the contribution of the Ly α emission line if the line is clearly detected in the spectroscopic observations." (Section 3.1 Measurement of beta_UV and M_UV)
   - fitting: Minimum chi-squared on the (beta_UV, normalization) grid; 1-sigma from delta chi-squared = 1  
  > "The best-fit value and associated 1 σ uncertainty of β UV and M UV are derived as the value showing the minimum χ2" (Section 3.1 Measurement of beta_UV and M_UV)
   - validation: Typical reduced chi-squared about 3.0 except for sources covered in two photometric bands  
  > "except for the sources covered in two photometric bands." (Section 3.1 Measurement of beta_UV and M_UV)
2. **measure dust continuum fluxes and S/N**: Identify lines via single Gaussian fit to spectrum at phase center, mask lines, image continuum with multiple tapers, measure peak flux within 0.5 arcsec radius and total flux via imfit or taper-based peak; S/N from highest image; detection S/N above threshold  
  > "apply a single Gaussian fitting to the spectra extracted at the phase center to identify" (Section 3.3 Dust continuum fluxes); "We obtain peak flux density within a" (Section 3.3 Dust continuum fluxes)
   - software: CASA
   - parameter: Fiducial S/N taken as highest S/N among images; detection threshold stated in the paper  
  > "As the fiducial signal-to-noise ratio (S/N) of each galaxy, we adopt the highest S/N among the images." (Section 3.3 Dust continuum fluxes)
   - assumption: Dust continuum emission contained within a single beam for peak flux  
  > "under the assumption that dust continuum emission is included within a single beam." (Section 3.3 Dust continuum fluxes)
   - fitting: imfit for galaxies detected in both bands; peak flux and RMS in 1 arcsec taper images for 158 µm-only detections; upper limits from natural weighting  
  > "we execute CASA/imfit" (Section 3.3 Dust continuum fluxes)
   - validation: Compared with visibility-fitting fluxes (UVMultifit) in Appendix A; consistent  
  > "we find that calculated fiducial fluxes, in any case, are consistent with those from the visibility analysis." (Section 3.3 Dust continuum fluxes)
3. **stack continuum images by beta_UV bin**: Stack 88 and 158 µm continuum in two beta_UV bins with UV-luminosity reciprocal weighting; stacked images re-measured with the same flux procedure  
  > "We perform the stacking of both rest-frame 88 µm and 158 µm dust continuums from galaxies in two distinct" (Section 3.4 Stacking analysis); "Then we also compute the weighted average with the following weight based on the" (Section 3.4 Stacking analysis)
   - software: CASA
   - parameter: beta_UV bins [-3, -1] and [-1, 1]; weight w_i = L_UV,mean / L_UV,i  
  > "We perform the stacking of both rest-frame 88 µm and 158 µm dust continuums from galaxies in two distinct" (Section 3.4 Stacking analysis)
   - parameter: Reference position is the phase center of ALMA observations (UV-derived central position)  
  > "we use central positions derived in the restframe UV continuum (i.e., phase center of the ALMA observations)." (Section 3.4 Stacking analysis)
   - assumption: Spatial UV-IR offsets below 0.35 arcsec do not significantly affect flux  
  > "spatial offsets identified in individual galaxies between UV and IR do not significantly impact the flux measurement" (Section 3.4 Stacking analysis)
   - fitting: _not stated_
   - validation: Weighted median instead of weighted average gives no major difference  
  > "We find that there is no major difference when we use the weighted median instead of the weighted aver" (Section 3.4 Stacking analysis)
4. **fit modified blackbody for T_dust, M_dust, L_IR**: Fit optically thin modified blackbody (eq. 4, with CMB term) to measured fluxes; L_IR from 8-1000 µm (paper text)  
  > "In this work, we use equation (4) to estimate" (Section 3.5 T_dust and L_IR estimation)
   - software: emcee
   - parameter: log10(M_dust/Msun) prior uniform in [4, 10]; T_dust prior uniform in [T_CMB,z, 120] K  
  > "We adopt a logarithmically uniform prior on the dust masses and dust temperatures with a range of" (Section 3.5 T_dust and L_IR estimation)
   - parameter: Gaussian prior beta_dust = 1.8 with sigma = 0.5  
  > "we adopt a Gaussian prior with a mean value of" (Section 3.5 T_dust and L_IR estimation)
   - parameter: kappa = kappa* (nu/nu*)^beta_dust with Milky Way normalization [10.41 cm^2 g^-1, 1900 GHz]  
  > "with the nomalization of Milky Way value" (Section 3.5 T_dust and L_IR estimation)
   - assumption: Optically thin limit assumed for the fits used in results; optically thick (lambda0 = 100 µm) gives higher T_dust with unchanged L_IR  
  > "In the optically thin limit" (Section 3.5 T_dust and L_IR estimation)
   - assumption: Galaxies without constrained T_dust assigned T_dust = 45 K  
  > "we assume the representative dust temperature of the SERENADE galaxies" (Table 2 note)
   - fitting: MCMC with emcee; best-fit and 1-sigma from modes with highest posterior density intervals; upper limits via Sawicki 2012 likelihood with 3-sigma cutoff  
  > "We use the Markov Chain Monte Carlo (MCMC) algorithm to fit the MBB profiles by utilizing the emcee library." (Section 3.5 T_dust and L_IR estimation); "We compute best-fit values and 1 σ uncertainties from the modes with the highest posterior density intervals." (Section 3.5 T_dust and L_IR estimation)
   - validation: Upper T_dust prior changed to 150 K and uniform beta_dust prior in [1.5, 2.5] tested; no significant impact on conclusions  
  > "Note that there is no significant impact on our conclusion if we change the upper edge of the prior distribution of" (Section 3.5 T_dust and L_IR estimation)
5. **derive IRX-beta_UV relation**: Compare IRX = L_IR/L_UV of individual and stacked galaxies with beta_UV for given intrinsic slope assumptions and literature relations (Calzetti, Meurer, SMC, Fudamoto 2020a)  
  > "We find that our result from the stacking analysis supports a shallower IRX" (Section 4.1 beta_UV vs IRX relationship)
   - parameter: Upper limits of undetected galaxies computed assuming T_dust = 45 K  
  > "the upper limits of the undetected galaxies are calculated by assuming" (Section 4.1 beta_UV vs IRX relationship)
   - parameter: Intrinsic beta_UV = -2.23 or -2.62 for SMC comparison  
  > "regardless of the intrinsic UV slope" (Section 4.1 beta_UV vs IRX relationship)
   - assumption: Dust extinction curve as in literature relations; beta_UV from power-law fit (alternative methods tested)  
  > "Some studies have implied that the methodology for estimating" (Section 4.1 beta_UV vs IRX relationship)
   - fitting: _not stated_
   - validation: Result unchanged when selecting only SHELLQs galaxies  
  > "find that the result remains consistent even when selecting galaxies only from the SHELLQs survey." (Section 4.1 beta_UV vs IRX relationship)
6. **compute total and dust-obscured SFRD at z~6**: Convert UV LF to total SFR using M_UV-beta and IRX-beta relations; integrate SFR function from M_UV = -17; uncertainties by bootstrap  
  > "We then integrate the SFR function with a range from" (Section 4.2 SFR density at z~6); "We estimate uncertainties using bootstrap techniques" (Section 4.2 SFR density at z~6)
   - parameter: SFR_UV = 0.76e-28 L_UV (erg/s/Hz); SFR_IR = 2.64e-44 L_IR (erg/s); Madau and Dickinson 2014 conversions with Chabrier 2003 IMF  
  > "following the conversion factors in Madau & Dickinson (2014) with Chabrier" (Section 4.2 SFR density at z~6)
   - assumption: Fiducial IRX-beta from Fudamoto et al. 2020a; alternatives SMC and Calzetti with linear M_UV-beta tested  
  > "We test the following two cases" (Section 4.2 SFR density at z~6)
   - fitting: _not stated_
   - validation: Maximum dust-obscured contribution about 45% under aggressive assumptions (not preferred)  
  > "the maximum contribution of the dust-obscured star formation is" (Section 4.2 SFR density at z~6)
7. **derive M_UV - f_obs relation and SFRD from it**: Split sample into three M_UV bins; stack 158 µm for the faintest bin; convert L_IR to SFR_IR and average L_UV to SFR_UV for f_obs; combine with UV LF  
  > "we split the sample into three distinct" (Section 4.3 Obscured fraction of the star formation); "we conduct the stacking analysis for just the rest-frame 158" (Section 4.3 Obscured fraction of the star formation)
   - parameter: M_UV bins [-24.5, -23.5], [-23.5, -22.0], [-22.0, -20.5]  
  > "we split the sample into three distinct" (Section 4.3 Obscured fraction of the star formation)
   - parameter: Stacked L_IR assuming optically thin MBB with T_dust = 45 K and beta_dust = 1.8  
  > "convert them to L IR assuming an optically-thin MBB profile with" (Section 4.3 Obscured fraction of the star formation)
   - assumption: Conversion of literature M_* to M_UV via Song et al. 2016 is for reference only  
  > "We note that the conversion is just for reference given the large uncertainties" (Section 4.3 Obscured fraction of the star formation)
   - fitting: Best-fit f_obs - M_UV relation with 1-sigma from bootstrap  
  > "The best-fit f obs - M UV relation and 1 σ uncertainties estimated by bootstrap are also shown" (Section 4.3 Obscured fraction of the star formation)
   - validation: Results compared with ALPINE, CRISTAL, REBELS f_obs measurements  
  > "Our results show a good agreement in the range of" (Section 4.3 Obscured fraction of the star formation)
8. **model T_dust evolution with redshift**: Analytic model of Sommovigo et al. 2022 combining t_gas and metallicity evolution; L_IR = (1 - exp(-tau_eff)) K1500 SFR; M_dust = D M_gas; tau_eff set to match z=0.5 T_dust observation; M_* = 1e10 Msun  
  > "Here we use _τ_ eff = 1 _._ 3 to match the _T_ dust observation" (Section 5 Discussion); "we assume a power-law dependence of" (Section 5 Discussion)
   - parameter: d log(O/H)/dz = -0.11 with z=0 value at M_* = 1e10 Msun (Sanders et al. 2021); no metallicity evolution at z>3.3 tested as alternative  
  > "we also compute the redshift evolution under the assumption of no metallicity evolution at" (Section 5 Discussion)
   - assumption: Continuous M_*-Z evolution (solid) or no evolution at z>3.3 (dashed)  
  > "under the assumption of continuous (solid) and no (dashed) M* - Z evolution at z > 3.3" (Figure 9 caption)
   - fitting: _not stated_
   - validation: Model T_dust matches observed z~6-7 stacked value and literature at z<5  
  > "The calculated T dust matches our observational estimate for" (Section 5 Discussion)

## Software

- **CASA** : mstransform for line masking; tclean for continuum imaging; imfit for source flux; imsmooth for stacked-image beam matching  
  > "we mask a frequency range that is three times wider than the line velocity dispersion using CASA/mstransform." (Section 3.3 Dust continuum fluxes); "Subsequently, we generate continuum images with CASA/tclean." (Section 3.3 Dust continuum fluxes); "by applying CASA/imsmooth for the images" (Section 3.4 Stacking analysis)
- **emcee** : MCMC fitting of modified blackbody profiles  
  > "We use the Markov Chain Monte Carlo (MCMC) algorithm to fit the MBB profiles by utilizing the emcee library." (Section 3.5 T_dust and L_IR estimation)
- **UVMultifit** : Visibility-based flux measurement with Sersic index n = 1 for flux comparison in Appendix A  
  > "we also measure the fluxes from visibility data with UVMultifit assuming" (Appendix A)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stacked average dust temperature at z~6-7 | 40.9 | +10.0/-9.1 | K | 4 | The stacked result suggests that an average dust temperature is |
| Scatter of individual T_dust at z=5-8 | 12 | not stated | K | 4 | The individual measurements have a large scatter of |
| Dust-obscured contribution to total SFRD at z~6 (M_UV-beta + IRX-beta) | 31 | +8/-8 | % | 6 | Our analyses indicate that the dust-obscured star formation in UV-selected galaxies contributes 31 |
| Dust-obscured contribution to total SFRD at z~6 (M_UV - f_obs) | 15 | +17/-8 | % | 7 | The contribution of dust-obscured star formation among LBGs based |
| M_UV - beta_UV best-fit relation at M_UV = -22 | beta_UV = -(0.76)(M_UV + 22) - (1.51) | 0.14 on slope coefficient; 0.15 on intercept (as stated) | dimensionless | 1 | is represented as β UV = − (0 . 76 ± 0 . 14)( M UV + 22) − (1 . 51 ± 0 . 15) |
| Stacked T_dust estimate for beta_UV = [-3, -1] sample | 25 | not stated | K | 4 | Our estimate of T dust ∼ 25 K for the stacking sample |
| Number of galaxies individually detected in dust continuum with T_dust estimate | 21 of 28 | not stated | galaxies | 0 | Among 28 galaxies, 21 are individually detected, and T dust can be estimated. |
| Number of [C II] emission lines detected at S/N > 3 among 20 observed | 16 | not stated | lines | 0 | Of these, 16 [C ii] and 10 [O iii] emission lines were detected with a signal-to-noise ratio (S/N) greater than 3. |
| Infrared luminosity range of SERENADE galaxies | log L_IR from ~11.5 to ~13.0 | not stated | log(Lsun) | 4 | from log L IR [L ⊙ ] ∼ 11 . 5 comparable to normal galaxies at z ∼ 7 |
| Lower limit on T_dust of MACS0416-Y1 at z=8.3 | >80 | lower limit | K | 0 | the measured lower limit of the dust temperature of |

## Qualitative findings

- Dust temperature increases gently with redshift from z=0 to z~6-7, with the linear (1+z) relation favored over the quadratic  
  > "supports a gentle increase of T dust from z = 0 to z ∼ 6–7." (abstract); "rather than the quadratic relation" (Section 4.4 T_dust evolution)
- The redshift evolution of T_dust could be reproduced by an increase in gas depletion timescale and decrease in metallicity  
  > "can be reproduced by an" (abstract)
- Dust-obscured SF contributes a limited fraction of total SFRD at z~6 and this is not strongly sensitive to the dust-correction assumption  
  > "the assumption of the dust correction does not strongly change the total SFRD at" (Section 4.2 SFR density at z~6)

## Claim tuples

- H: The IRX-beta_UV relation at z~6 differs from low-redshift relations once multi-band FIR SEDs are considered. | E: Multi-band MBB fits of individual and stacked galaxies, compared with Calzetti, Meurer, SMC and Fudamoto 2020a relations. | R: Stacked IRX-beta_UV lies below the Calzetti and Meurer relations and is shallower than the SMC relation, matching Fudamoto 2020a with intrinsic beta_UV = -2.62. | F: A shallower IRX-beta_UV relation at z~6, which the authors attribute to lower metallicity and lower T_dust than assumed in earlier work. | **supported**
- H: Average dust temperature at z~6-7 and its redshift trend. | E: Average stack of 22 galaxies observed in both bands, MBB fit with Gaussian beta_dust prior, compared with linear and quadratic (1+z) relations. | R: Stacked T_dust = 40.9 (+10.0/-9.1) K; linear relation favored. | F: T_dust increases mildly with redshift, consistent with a linear (1+z) trend. | **supported**
- H: Dust-obscured star formation contributes significantly to total SFR density of UV-selected galaxies at z~6. | E: Combine UV LF with M_UV-beta and IRX-beta relations, and independently with M_UV - f_obs from stacking. | R: Dust-obscured contribution 31 (+8/-8)% with IRX-beta and 15 (+17/-8)% with f_obs. | F: Dust-obscured star formation in LBGs is limited (about 15-30%) at z~6. | **supported**
- H: The T_dust redshift evolution and its scatter can be explained by gas depletion time, metallicity evolution and main-sequence/mass-metallicity scatter. | E: Analytic model of Sommovigo et al. 2022 with observed t_gas and Z evolution, tau_eff = 1.3, and scatter from main sequence and M*-Z relations. | R: Model T_dust matches z~6-7 observations and literature at z<5; combined MS and M*-Z dispersions give about ±12 K. | F: The gas depletion and metallicity evolution plausibly explain the T_dust evolution and its scatter. | **partially**

## Reasoning

- Why this data: Band-8 [O III] 88 µm and Band-6 [C II] 158 µm continuum together give a multi-band FIR SED so that T_dust and L_IR can be fitted simultaneously.  
  > "allowing us to simultaneously measure the IR luminosity and dust temperature for a statistical sample of z ≳ 5 galaxies for the first time" (abstract)
- Why this method: Band-8 covers rest-frame ~90 µm near the peak of dust emission at z~6, which constrains T_dust.  
  > "The ALMA Band-8, covering rest-frame ∼ 90 µm dust continuum near the peak of the dust thermal emission" (Section 1 Introduction)
- Alternative: Uniform beta_dust prior in [1.5, 2.5] instead of Gaussian prior: slightly lower beta and T_dust, not significantly different conclusions  
  > "The results do not strongly depend on the prior distribution of" (Section 3.5 T_dust and L_IR estimation)
- Alternative: Alternative tau_eff and optically thick MBB assumption: T_dust higher while L_IR unchanged  
  > "whereas T dust becomes higher than those with the optically thin assumption." (Section 3.5 T_dust and L_IR estimation)
- Alternative: Calzetti, Meurer and SMC IRX-beta relations rejected in favor of shallower relation  
  > "We find that our result from the stacking analysis supports a shallower IRX" (Section 4.1 beta_UV vs IRX relationship)
- Alternative: Power-law beta_UV versus SED-fit beta_UV and narrow versus wide wavelength range tested as sources of IRX bias  
  > "For instance, ´Alvarez-M´arquez et al. (2019) suggested that the" (Section 4.1 beta_UV vs IRX relationship)
- How they decided it was enough: Detection decided by highest S/N across tapered and natural images; galaxies with fiducial S/N above a set threshold counted as detected.  
  > "Galaxies with fiducial S/N > 3.5 in any band are considered as continuum detection." (Section 3.3 Dust continuum fluxes)
- Limitation (authors): Dusty galaxies such as SMGs and HST-dark galaxies are not sampled, so dust-obscured SFRD is underestimated  
  > "Note that our estimations of the dust-obscured star formation miss very dusty galaxies such as SMGs" (Section 4.2 SFR density at z~6)
- Limitation (authors): Sample selection may be biased by heterogeneous surveys; enlarging the sample is needed for robust conclusions  
  > "although enlarging the sample size is" (Section 3.2 M_UV vs beta_UV relationship)
- Limitation (authors): Lack of rest-frame optical coverage prevents stellar mass and metallicity estimates for the SERENADE galaxies  
  > "Although our targeted galaxies do not have stellar mass" (Section 5 Discussion)
- Caveat (inferred, ours): Mixing SERENADE and literature galaxies with a re-analysis that may not match original flux methods (flux measurement method differences acknowledged in Section 2.2).
- Caveat (inferred, ours): Beta_dust is not constrained by the data and is prior-driven; T_dust scatter attribution to beta_dust is weak.
- Caveat (inferred, ours): Undetected galaxies assigned T_dust = 45 K, which biases stacks and IRX upper limits.
- Caveat (inferred, ours): beta_UV from power-law fits of sparse photometry may be biased for redder slopes; the authors note this.
- Caveat (inferred, ours): Analytic T_dust model depends on tau_eff calibrated to one z=0.5 point and on assumed M*=1e10 Msun for all galaxies.
- Caveat (inferred, ours): Optically thin assumption may underestimate T_dust; AGN contribution to FIR not excluded.
- Caveat (inferred, ours): Stacked SFRD and f_obs depend on conversion of literature stellar masses via Song et al. 2016.
- Caveat (inferred, ours): Many key numbers are in tables and figures rather than in the text, limiting verification.

## Reproducibility

- Data public (paper): Archival Band-6/8 data for literature galaxies are publicly available in the ALMA archive; public status of the new SERENADE data is not stated  
  > "We collect galaxies at 5 < z < 8 with both Band-6 and Band-8 observations publicly available in the ALMA science archive." (Section 2.2 Additional 5<z<8 samples)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: CASA version and full tclean/imfit parameters
- Missing: Calibration details and per-galaxy beam sizes
- Missing: Photometry table values for all galaxies and the literature T_dust/L_IR inputs (partly in Table 1 and 2, not all fields)
- Missing: emcee run configuration and convergence
- Missing: Stacking pipeline details (pixel grid, bootstrap) and weighted-median alternative code
- Missing: Ly-alpha contribution values and redshifts used
- Missing: Code for the analytic T_dust model and its adopted parameters per equation
- Missing: Visibility-based UVMultifit analysis (deferred to another paper)
- Data volume (inferred): Small: roughly 28 galaxies with Band-6 and Band-8 continuum images and cubes, likely tens of GB at most (inferred).
- Score (inferred): 3/5, Methods are described with equations and key priors, but many imaging, calibration and MCMC settings and the literature inputs are missing or spread across tables and figures.
- Rediscovery candidate: no, Public status of the new SERENADE data is not stated, several imaging and fitting settings are missing, and the recipe mixes re-analysis of literature data with inputs not given in the text.

## Links

- Method: Sawicki 2012 (Likelihood treatment for upper limits in MBB fitting)
- Method: da Cunha et al. 2013 (CMB effects on MBB flux and T_dust measurement)
- Method: Fudamoto et al. 2020a (Fiducial IRX-beta relation and intrinsic beta_UV = -2.62)
- Method: Sommovigo et al. 2022 (Analytic T_dust evolution model)
- Method: Harikane et al. 2020b (Lyman-alpha brightness methodology)
- Companion: Harikane et al. in prep (Paper I) (Emission-line data analysis of the SERENADE sample)
- Companion: Mitsuhashi et al. in prep (Visibility-based flux analysis referenced in Appendix A and f_obs comparison)
- Related: SERENADE ALMA program
- Related: Hyper Suprime-Cam Subaru Strategic Program (HSC-SSP)
- Related: ALPINE
- Related: CRISTAL
- Related: REBELS
- Related: SHELLQs

## Checks

```json
{
 "quotes": 139,
 "quotes_ok": 138,
 "quote_pass_rate": 0.993,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 11,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 123,
  "stated": 92,
  "rate": 0.748
 },
 "evidence_ok": false
}
```

## Figures

- **Figure 1** (scatter_or_relation, 1 panel(s), data): UV slope beta_UV versus rest-frame UV absolute magnitude M_UV at z~6 for SERENADE galaxies (red), binned HST galaxies from Bouwens et al. 2014 (blue), Bowler et al. 2023 (green), with z~4 results in grey, plus linear fits showing redder bright-end slopes.
  - axes: x: rest-frame UV absolute magnitude M_UV [mag]; y: UV slope beta_UV [dimensionless]
  - supports step 1
  - read off the plot: approx. brightest bin beta_UV about -0.2 at M_UV about -23.9 mag; approx. M_UV about -22.7 mag bin beta_UV about -0.9; approx. faint blue points beta_UV about -2.2 at M_UV about -18.5 mag
  - reproduction target
- **Figure 3** (moment_map, 4 panel(s), data): Stacked continuum cutouts (6 arcsec square) at rest-frame 158 micron and 88 micron for two beta_UV bins, with contours every 1 sigma starting at 3 sigma and beam sizes shown.
  - axes: colour: stacked continuum flux density [not labelled]; contours: signal-to-noise [sigma]
  - supports step 3
  - read off the plot: approx. N=6 galaxies in each stacked bin; approx. 158 micron stack detected at >=3 sigma in -1 to 1 beta_UV bin
- **Figure 5** (scatter_or_relation, 1 panel(s), data, literature_comparison): Infrared luminosity of SERENADE galaxies and z>5 literature galaxies versus redshift, compared with ALMA large-program galaxies assuming fixed dust temperature and DSFGs at z>5.5.
  - axes: x: redshift [dimensionless]; y: infrared luminosity log L_IR [log solar luminosities]
  - supports step 4
  - read off the plot: approx. log L_IR 13.4 at z approx. 5.85 for a red point; approx. log L_IR 11.1 at z approx. 7.3; approx. DSFG log L_IR 13.6 at z approx. 5.7
  - reproduction target
- **Figure 6** (scatter_or_relation, 1 panel(s), data, literature_comparison, model): Infrared excess IRX (log L_IR/L_UV) versus UV slope beta_UV for individual SERENADE galaxies, stacks, galaxies with assumed 45 K dust, earlier-redshift measurements, and local and high-z IRX-beta relations.
  - axes: x: UV slope beta_UV [dimensionless]; y: infrared excess log IRX = L_IR/L_UV [dimensionless (log)]
  - supports step 5
  - read off the plot: approx. stacked points log IRX about 0.55 at beta_UV about 0.05; approx. stacked point log IRX about -0.2 at beta_UV about -1.7
  - reproduction target
- **Figure 7** (radial_profile, 1 panel(s), data, literature_comparison): Cosmic star formation rate density versus redshift from this work (total and dust-obscured) compared with Zavala 2021, Bouwens 2021, Madau and Dickinson 2014 and HST-dark galaxy contributions.
  - axes: x: redshift [dimensionless]; y: star formation rate density [M_sun yr^-1 Mpc^-3]
  - supports step 6
  - read off the plot: approx. total SFRD 0.015 M_sun/yr/Mpc^3 at z approx. 6; approx. dust-obscured SFRD 0.005 M_sun/yr/Mpc^3 at z approx. 6; approx. Madau and Dickinson peak 0.13 M_sun/yr/Mpc^3 at z approx. 2
  - reproduction target
- **Figure 8** (scatter_or_relation, 1 panel(s), data, model, literature_comparison): Obscured star formation fraction f_obs (SFR_IR/SFR_UV+IR) versus absolute UV magnitude M_UV for SERENADE galaxies with a fitted linear relation from stacks, compared with literature samples at z~4.5 to 7.
  - axes: x: absolute UV magnitude M_UV [mag]; y: obscured fraction f_obs = SFR_IR/SFR_UV+IR [dimensionless]; top x: stellar mass log M_* [log solar masses]
  - supports step 7
  - read off the plot: approx. stacked f_obs 0.52 at M_UV about -21.5 mag; approx. stacked f_obs 0.72 at M_UV about -23.8 mag; approx. f_obs upper limits near 0.3 at M_UV about -24 mag
  - reproduction target
- **Figure 9** (scatter_or_relation, 1 panel(s), data, model, literature_comparison): Dust temperature versus redshift for SERENADE galaxies, z>5 literature compilation, a magenta stack at z~6-7, previous stacking-based trends and model predictions, with red model lines from the Sommovigo et al. 2022 analytical model.
  - axes: x: redshift [dimensionless]; y: dust temperature T_dust [K]
  - supports step 8
  - validation: Compares the analytical T_dust evolution model (with gas temperature and metallicity evolution from observations) against the SERENADE and literature dust temperatures.
  - read off the plot: approx. magenta stack T_dust about 41 K at z approx. 6.4; approx. red model line T_dust about 40 K at z approx. 6; approx. T_dust of red SERENADE point about 76 K at z approx. 5.85
  - reproduction target
- **Figure 10** (scatter_or_relation, 2 panel(s), data): Comparison of continuum flux densities from different methods: visibility fitting versus image-based imfit or peak fluxes (left), and imfit and peak fluxes across taper scales of natural, 1 arcsec, 2 arcsec and 3 arcsec (right).
  - axes: x: flux density from imfit or taper [mJy]; y: flux density from UVMultifit or taper-based method [mJy]
  - supports step 2
  - validation: Checks consistency of dust continuum flux measurements across fitting methods and uv tapers, with one-to-one and ±0.3 dex (left) or ±0.5 dex (right) bands.
  - read off the plot: approx. brightest flux about 8 mJy agreement with one-to-one line; approx. faint flux about 0.05 mJy
