# The [C II] emission as a molecular gas mass tracer in galaxies at low and high redshifts

`2018MNRAS.481.1976Z` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Zanella, A. | arXiv: 1808.10331 | DOI: 10.1093/mnras/sty2394

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Are z~2 main-sequence galaxies [C II] deficient, and what physical parameter drives [C II] luminosity (is [C II] an empirical molecular gas mass tracer)?  
  > "The main motivation of this work is to understand which is the dominant physical parameter affecting the" (3 Results and Discussion); "Interestingly we find that its luminosity traces galaxies’ molecular gas mass and could therefore be used as an alternative to other proxies" (1 Introduction)
- Target **10 main-sequence galaxies at 1.73 < z < 1.94 in GOODS-S (IDs 9347, 6515, 10076, 9834, 9681, 10049, 2861, 2910, 7118, 8490)**: coordinates Per-source RA/DEC in degrees in Table 1 (e.g. ID9347: 53.154900, -27.809397); uncorrected HST coordinates  
  > "we selected targets in the GOODS-S field" (2.1 Sample selection and ancillary data); "Our sample therefore consists of 10 typical star-forming, main-sequence galaxies at redshift" (2.1 Sample selection and ancillary data); "Spectroscopic redshifts for our sources are all publicly available and were determined in different ways" (2.1 Sample selection and ancillary data); "53.154900 | -27.809397" (Table 1); z/distance 1.73 <= z <= 1.94 (spectroscopic); Table 1 gives z_opt and z_[CII] per source  
  > "we selected targets in the GOODS-S field" (2.1 Sample selection and ancillary data); "Our sample therefore consists of 10 typical star-forming, main-sequence galaxies at redshift" (2.1 Sample selection and ancillary data); "Spectroscopic redshifts for our sources are all publicly available and were determined in different ways" (2.1 Sample selection and ancillary data); "53.154900 | -27.809397" (Table 1); distance from Spectroscopic redshifts from GMASS (Kurk2013), K20, Popesso2009, Pope2008 and own Keck/LRIS data, refined by template fitting; cosmology H0 = 70, Om = 0.3, OL = 0.7  
  > "we selected targets in the GOODS-S field" (2.1 Sample selection and ancillary data); "Our sample therefore consists of 10 typical star-forming, main-sequence galaxies at redshift" (2.1 Sample selection and ancillary data); "Spectroscopic redshifts for our sources are all publicly available and were determined in different ways" (2.1 Sample selection and ancillary data); "53.154900 | -27.809397" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00775.S
- bands: Band 9 ([C II] line plus ~450 um continuum) and Band 7 (850 um continuum)  
  > "We carried out ALMA Band 9 observations for our sample during Cycle 1" (2.2 Details of ALMA observations); "we also requested additional observations in Band 7 to detect the 850" (2.2 Details of ALMA observations)
- frequencies and spectral setup: [C II] observed at 645-696 GHz; four sidebands of 1.875 GHz each; spectral resolution 0.976 MHz (later binned)  
  > "in the frequency range $\nu_{\mathrm{obs}} = 645$ – $696$ GHz" (2.2 Details of ALMA observations); "ALMA observations are carried out using four, sometimes adjacent, sidebands (SBs) covering 1.875 GHz each" (2.1 Sample selection and ancillary data); "We set a spectral resolution of 0.976 MHz" (2.2 Details of ALMA observations)
- continuum bandwidth: 850 um continuum from the full spectral range; 450 um continuum excluding [C II] line channels  
  > "We created averaged continuum maps by integrating the full spectral range for the observations at 850" (2.4 Continuum emission); "we made sure to exclude the channels where the flux is dominated by the" (2.4 Continuum emission)
- arrays: _not stated_
- configurations: C32-3 (C32-1 was requested)  
  > "the observations were taken in the C32-3 configuration" (2.2 Details of ALMA observations)
- baselines: _not stated_
- angular resolution: Band 9 synthesized beam 0.3" x 0.2"; Band 7 synthesised beam 1" x 0.5"  
  > "with a synthesized beam FWHM $=$ 0.3” $\times$ 0.2”" (2.2 Details of ALMA observations); "The synthesised beam has FWHM $=$ 1” $\times$ 0.5”" (2.2 Details of ALMA observations)
- max recoverable scale: ~3.5" (Band 9); ~6" (Band 7)  
  > "and a maximum recoverable scale of $\sim$ 3.5”" (2.2 Details of ALMA observations); "the maximum recoverable scale is $\sim$ 6”" (2.2 Details of ALMA observations)
- sensitivity: Band 9 target 1.5-2 mJy/beam over a 350 km/s bandwidth; Band 7 continuum 140 uJy/beam  
  > "to reach a homogeneous sensitivity of 1.5 – 2 mJy/beam over a bandwidth of 350" (2.2 Details of ALMA observations); "For each galaxy we reached a sensitivity of 140" (2.2 Details of ALMA observations)
- time on source: Band 9: 8-13 min per galaxy including overheads; Band 7: ~2 min on source  
  > "for 8 – 13 minutes including overheads" (2.2 Details of ALMA observations); "minutes on source" (2.2 Details of ALMA observations)
- observing dates: 3 and 4 November 2013 (Band 9)  
  > "03 Nov 2013" (Table 1 (observing log)); "04 Nov 2013" (Table 1 (observing log))
- pi or archival as stated: Own Cycle 1 program (PI: E. Daddi)  
  > "(PI: E. Daddi, Project ID: 2012.1.00775.S)" (2.2 Details of ALMA observations)
- Line: C+ ([C II]) 2P3/2 - 2P1/2 (158 um) (1900.54 GHz)
- Other facility **HST (CANDELS)**: Optical and near-IR imaging used for stellar mass/SFR maps, sizes and positions  
  > "are available from the CANDELS survey" (2.1 Sample selection and ancillary data)
- Other facility **Spitzer and Herschel**: 24-500 um photometry for IR SED fitting  
  > "photometry in the wavelength range 24 $\mu$m – 500 $\mu$m is also available" (2.1 Sample selection and ancillary data)
- Other facility **VLA**: 6 GHz radio observations used to check ALMA positions  
  > "were taken with the Karl G. Jansky Very Large Array (VLA) with 0.3” $\times$ 0.6” resolution" (2.1 Sample selection and ancillary data); "The ALMA target positions are consistent with those from VLA." (2.2 Details of ALMA observations)
- Other facility **VLT/FORS2 and Keck/LRIS spectroscopy**: Rest-frame UV spectra used to refine redshifts  
  > "we applied to our VLT/FORS2 and Keck UV rest-frame spectra the same approach described in (cite: Gobat2017)" (2.1 Sample selection and ancillary data)
- External data: Spitzer/Herschel IR photometry (deblended)  
  > "The estimated continuum fluxes were used, together with the available *Spitzer* and *Herschel* data (cite: Elbaz2011)" (2.4 Continuum emission) [from (cite: Elbaz2011), (cite: Wang2017)]
- External data: Spectroscopic redshifts for most targets  
  > "5 of them are from the GMASS survey (cite: Kurk2013)" (2.1 Sample selection and ancillary data) [from (cite: Kurk2013), (cite: Cimatti2002), (cite: Mignoli2005), (cite: Popesso2009), (cite: Pope2008)]
- External data: Global-SED stellar masses used in the analysis  
  > "in good agreement with that estimated by (cite: Santini2014) fitting the global ultraviolet (UV) to IR SED" (2.1 Sample selection and ancillary data) [from (cite: Santini2014)]
- External data: Main-sequence definition used to select targets and compute sSFR/sSFR_MS  
  > "as defined by (cite: Rodighiero2014)" (2.1 Sample selection and ancillary data) [from (cite: Rodighiero2014)]
- External data: Mass-metallicity relation used for gas-phase metallicity  
  > "Given their stellar mass and the mass-metallicity relation by (cite: Zahid2014) we estimated their gas phase metallicity." (2.4 Continuum emission) [from (cite: Zahid2014)]
- External data: Metallicity-dependent gas-to-dust ratio  
  > "depending on its metallicity, as prescribed by (cite: Magdis2012)" (2.4 Continuum emission) [from (cite: Magdis2012)]
- External data: Integrated Schmidt-Kennicutt relation for main-sequence galaxies (molecular gas masses)  
  > "the integrated Schmidt-Kennicutt relation for main-sequence sources reported by (cite: Sargent2014)" (2.4 Continuum emission) [from (cite: Sargent2014)]
- External data: Literature [C II], IR, CO, gas mass, sSFR and metallicity compilations at low and high redshift  
  > "datasets from the literature, both at low and high redshift" (2.5 Other samples from the literature) [from (cite: Stacey1991), (cite: Stacey2010), (cite: Gullberg2015), (cite: Capak2015), (cite: Diaz-Santos2017), (cite: Cormier2015), (cite: Brauher2008), (cite: Contursi2017), (cite: Magdis2014), (cite: Huynh2014), (cite: Ferkinhoff2014), (cite: Schaerer2015), (cite: Brisbin2015), (cite: Hughes2017), (cite: Accurso2017)]
- External data: Depletion-time versus sSFR models compared with [C II]/IR  
  > "we considered two models ((cite: Sargent2014), (cite: Scoville2017)) predicting how the depletion time of galaxies changes as a function of their distance from the main-sequence" (3.3 The dependence of the [C II]-to-IR ratio) [from (cite: Sargent2014), (cite: Scoville2017)]
- Simulation/model as data: CASA simobserve mock observations of 2D Gaussians (FWHM 0.1-2 arcsec) at ~0.2 arcsec resolution to test flux/size recovery in the uv plane  
  > "we simulated 2D Gaussians with increasing FWHM (in the range 0.1” – 2”)" (A. Resolution)

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline based on CASA  
  > "The data were reduced with the standard ALMA pipeline based on the CASA software" (2.3 [C II] emission line measurements)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: No imaging; sources fitted directly in the uv plane with GILDAS uv_fit (Fourier transform of a 2D exponential); CASA uvmodelfit as a cross-check  
  > "using the Fourier Transform of the 2D exponential model, with the GILDAS task `uv_fit`" (2.3 [C II] emission line measurements); "We checked that fluxes and uncertainties determined with the `uvmodelfit` task provided by CASA would give consistent results." (2.3.1 Individual [C II] detections)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: 450 um continuum maps made excluding [C II] channels; [C II] fluxes corrected by subtracting the rest-frame 158 um continuum  
  > "we made sure to exclude the channels where the flux is dominated by the" (2.4 Continuum emission); "We subtracted from the" (2.3 [C II] emission line measurements)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Data binned to much lower velocity resolution than 0.45 km/s; line maps averaged over 719 km/s for non-detections  
  > "later binning the data to substantially lower velocity resolutions" (2.2 Details of ALMA observations); "we created emission line maps by averaging channels over 719 km s$^{-1}$" (2.3.2 Tentative and non detections)
- final beam: Band 9: 0.3" x 0.2" synthesized beam; Band 7: 1" x 0.5"  
  > "with a synthesized beam FWHM $=$ 0.3” $\times$ 0.2”" (2.2 Details of ALMA observations); "The synthesised beam has FWHM $=$ 1” $\times$ 0.5”" (2.2 Details of ALMA observations)
- final rms: Band 7 continuum 140 uJy/beam; Band 9 noise r.m.s. per source in Table 1 (about 11.6-51 mJy/beam)  
  > "For each galaxy we reached a sensitivity of 140" (2.2 Details of ALMA observations)

### Inherited from earlier work

- Iterative uv-plane spectral extraction / line search procedure  
  > "similar to what described in Daddi et al. (2015 and in preparation) and (cite: Coogan2017)" (2.3 [C II] emission line measurements) [from Daddi et al. (2015 and in preparation) and (cite: Coogan2017)]
- Reliability of redshift uncertainties from the line detection procedure  
  > "Following (cite: Coogan2017) simulations of a similar line detection procedure" (2.3.1 Individual [C II] detections) [from (cite: Coogan2017)]
- Resolved stellar mass and SFR maps from pixel-by-pixel SED fitting  
  > "following the method described by (cite: Cibinel2015)" (2.1 Sample selection and ancillary data) [from (cite: Cibinel2015)]
- Redshift refinement of optical spectra with Lyman break galaxy templates  
  > "we applied to our VLT/FORS2 and Keck UV rest-frame spectra the same approach described in (cite: Gobat2017)" (2.1 Sample selection and ancillary data) [from (cite: Gobat2017), templates from (cite: Shapley2003)]
- IR SED fitting with Draine & Li models plus modified black body  
  > "Following the method presented in (cite: Magdis2012), we fitted the IR photometry with (cite: Draine2007) models" (2.4 Continuum emission) [from (cite: Magdis2012)]
- Monte Carlo estimation of L_IR and M_dust uncertainties  
  > "were quantified using Monte Carlo simulations, as described by (cite: Magdis2012)" (2.4 Continuum emission) [from (cite: Magdis2012)]
- Deblending of Spitzer and Herschel photometry with prior sources  
  > "The *Spitzer* and *Herschel* data were deblended using prior sources" (2.4 Continuum emission) [from (cite: Bethermin2010), (cite: Roseboom2010), (cite: Elbaz2011), (cite: Lee2013), (cite: Bethermin2015), (cite: Liu2017)]

### Not stated but needed to reproduce (our reading)

- CASA and pipeline version used for the Band 9 and Band 7 reductions, and whether the archive-delivered calibration was used as is
- Flux, bandpass and phase calibrators and the Band 9 flux scale uncertainty
- Whether any self-calibration was done
- Which array (12-m / 7-m) and antenna numbers were used
- Exact channel ranges (optimal channel range) used for each detection and the line-free channels used for continuum
- Final velocity binning used for the 1D spectra
- Table of GILDAS uv_fit initial parameters and fitted effective radii used for the exponential models (only listed as R_e from HST in Table 2)
- GALFIT settings (PSF, mask, sky) used for the stellar-mass-map size fits
- Details of the stack weighting (visibility weights, alignment shifts, how the size correction for position uncertainty was derived)
- Parameters of the Draine2007 / MBB fits (grid ranges, treatment of Spitzer/Herschel priors) and the exact IR luminosity pipeline for the literature samples
- Full per-galaxy literature compilation (only an excerpt appears in the paper; the full table is stated to be online)

## Analysis recipe

1. **Reduce and convert the ALMA data**: Standard ALMA pipeline in CASA, then conversion of calibrated cubes to uvfits for analysis in GILDAS  
  > "The data were reduced with the standard ALMA pipeline based on the CASA software" (2.3 [C II] emission line measurements); "The calibrated data cubes were then converted to *uvfits* format and analyzed with the software GILDAS" (2.3 [C II] emission line measurements)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Quantify flux and size recovery and noise penalty for resolved sources**: Simulated 2D Gaussians of varying FWHM with simobserve, fitted in the uv plane with uvmodelfit; repeated with GILDAS on the highest S/N source (ID9347) to derive noise vs size relation  
  > "We then fitted these mock data in the *uv* plane with the task `uvmodelfit`." (A. Resolution); "We fitted its velocity-integrated map multiple times with the GILDAS algorithm, first with a point source model and then adopting a Gaussian profile with increasing FWHM." (A. Resolution)
   - software: CASA, GILDAS
   - parameter: Polynomial relation y = 1.00 + 0.79x + 0.14x^2 + 0.01x^3 between noise ratio y and FWHM ratio x  
  > "y = 1.00 + 0.79x + 0.14x^2 + 0.01x^3" (A. Resolution)
   - assumption: The correct source position and FWHM are known  
  > "We notice however that these predictions assume that the correct position and FWHM of the source are known." (A. Resolution)
   - fitting: Polynomial fit to the noise ratio versus FWHM ratio  
  > "By fitting the datapoints with a polynomial curve we obtained the following relation" (A. Resolution)
   - validation: Fluxes and sizes well recovered for large galaxies given enough S/N; similar results with GILDAS simulations  
  > "Both sizes and fluxes are very well recovered even for large galaxies provided the data had large enough S/N." (A. Resolution); "Very similar results are obtained when simulating sources with GILDAS instead of CASA." (A. Resolution)
3. **Derive optical sizes, positions and astrometric shift from HST**: Pixel-by-pixel SED fitting of HST bands (PSF-matched to F160W) gives stellar mass/SFR maps; exponential profile fit with GALFIT to the stellar mass maps gives sizes and peak positions; HST frame shifted to match ALMA  
  > "we performed pixel-by-pixel spectral energy distribution (SED) fitting considering all the available *HST* filters mentioned above" (2.1 Sample selection and ancillary data); "We therefore determined the size of the galaxy disks by fitting the stellar mass maps with an exponential profile" (2.3.1 Individual [C II] detections)
   - software: GALFIT
   - parameter: Stellar population age 100 Myr - 2 Gyr, fixed solar metallicity, constant-SFR templates  
  > "The stellar population age in the models varied between 100 Myr and 2 Gyr, assuming fixed solar metallicity." (2.1 Sample selection and ancillary data); "templates with constant SFR to limit the degeneracy with dust extinction" (2.1 Sample selection and ancillary data)
   - parameter: Coordinate shifts Delta RA = 0 arcsec, Delta DEC = -0.2 arcsec applied to HST  
  > "In our analysis we adopt the following coordinate shifts $\Delta RA = 0$”, $\Delta DEC = -0.2$”." (B. Astrometry)
   - assumption: Calzetti dust extinction; Bruzual & Charlot templates  
  > "We corrected the fluxes for dust extinction following the prescriptions by (cite: Calzetti2000)." (2.1 Sample selection and ancillary data)
   - fitting: _not stated_
   - validation: No structured residuals after subtracting the best-fit model; stellar mass from maps agrees with global SED mass within 30%  
  > "We checked that there were not structured residuals when subtracting the best-fit model from the stellar mass maps." (2.3 [C II] emission line measurements); "(they differ $<$ 30% with no systematic trends)" (2.1 Sample selection and ancillary data)
4. **Search for [C II] emission by iterative uv-plane spectral extraction**: Fit a source model (PSF, Gaussian or exponential) in the uv plane channel by channel to all four sidebands at the astrometry-corrected HST position; average channels maximising S/N, refit position, and iterate to convergence  
  > "to all four sidebands and channel per channel" (2.3 [C II] emission line measurements); "we averaged the data over the channels maximizing the detection S/N" (2.3 [C II] emission line measurements)
   - software: GILDAS
   - parameter: Secure detection: emission line significance > 5 sigma in the optimal channel range  
  > "they have emission line significance $> 5 \sigma$ in the optimal channel range" (2.3.1 Individual [C II] detections)
   - fitting: _not stated_
   - validation: Detections robust against the model used for the 1D spectrum extraction; positions consistent with HST peaks  
  > "The detections are robust against the model used for the extraction of the 1D spectra" (2.3.1 Individual [C II] detections)
5. **Measure [C II] redshifts of detections**: Signal-weighted mean frequency within the line channels and Gaussian fit of the 1D spectrum  
  > "1) we computed the signal-weighted average frequency within the line channels, and 2) we fitted the 1D spectrum with a Gaussian function" (2.3.1 Individual [C II] detections)
   - software: GILDAS
   - fitting: Gaussian fit to the 1D spectrum (details not stated)  
  > "2) we fitted the 1D spectrum with a Gaussian function" (2.3.1 Individual [C II] detections)
   - validation: Compared with optical redshifts: no systematic difference, MAD of 200 km/s  
  > "They generally agree, with no significant systematic difference and a median absolute deviation (MAD) of 200 km s$^{-1}$" (2.3.1 Individual [C II] detections)
6. **Measure total [C II] fluxes of the four detections**: Fit velocity-averaged line maps in the uv plane with the Fourier transform of a 2D exponential with fixed size and centre from the optical images (GILDAS uv_fit)  
  > "by fitting their average emission line maps in the *uv* plane with exponential models" (2.3.1 Individual [C II] detections); "We fixed the size and center of the model on the basis of the effective radius and peak coordinates derived from the optical images" (2.3 [C II] emission line measurements)
   - software: GILDAS, CASA
   - parameter: Exponential model size = effective radius from HST stellar mass map (R_e in Table 2)  
  > "We fixed the size and center of the model on the basis of the effective radius and peak coordinates derived from the optical images" (2.3 [C II] emission line measurements)
   - assumption: [C II] emission follows an exponential disk with the optical size; a PSF model would underestimate fluxes  
  > "whereas by using a PSF model instead we would have underestimated the fluxes" (2.3.1 Individual [C II] detections)
   - fitting: uv-plane model fit with GILDAS; uncertainties from the fit  
  > "We then extracted the" (2.3 [C II] emission line measurements)
   - validation: CASA uvmodelfit gives consistent fluxes; Gaussian model also consistent; channel-to-channel scatter consistent with errors  
  > "We checked that fluxes and uncertainties determined with the `uvmodelfit` task provided by CASA would give consistent results." (2.3.1 Individual [C II] detections); "we verified that the uncertainties associated to the flux measurement in each channel are consistent with the channel to channel fluctuations" (2.3.1 Individual [C II] detections)
7. **Stack the four detections to measure the average [C II] size**: Align detections at HST positions, co-add visibilities and fit an exponential profile with free size  
  > "stacked them (coadding all visibilities) to increase the S/N" (2.3.1 Individual [C II] detections); "We then fitted the stacked data with an exponential profile, leaving its size free to vary during the fit." (2.3.1 Individual [C II] detections)
   - software: GILDAS
   - fitting: Exponential profile with free scale length fitted in uv space  
  > "We then fitted the stacked data with an exponential profile, leaving its size free to vary during the fit." (2.3.1 Individual [C II] detections)
   - validation: Size uncertainty from GILDAS checked against amplitude versus uv range; unresolved-source probability < 1e-5  
  > "The reported size uncertainty was estimated by GILDAS in the fit and the modelling of the signal amplitude versus *uv* range signal shows that it is reliable" (2.3.1 Individual [C II] detections)
8. **Tentative detections, upper limits and average [C II] stack**: For undetected sources, measure at fixed HST position with exponential models of fixed optical size, averaging over 719 km/s around the optical redshift; 3 sigma upper limits; stack detections plus tentative detections plus ID2910 in the uv plane  
  > "using exponential models with the fixed optical size for each galaxy and conservatively averaging" (2.3.2 Tentative and non detections); "For the four sources with no detected signal we considered $3\sigma$ flux upper limits" (2.3.2 Tentative and non detections); "We aligned the detections and tentative detections and stacked them coadding all visibilities." (2.3.3 Average [C II] signal)
   - software: GILDAS
   - parameter: Line map averaged over 719 km/s (3 x MAD redshift accuracy summed in quadrature with average detected line FWHM)  
  > "we created emission line maps by averaging channels over 719 km s$^{-1}$" (2.3.2 Tentative and non detections)
   - parameter: Rest-frame 158 um continuum removed from the stack by reducing the flux by 10%  
  > "We finally subtracted the contribution of the rest-frame 158 $\mu$m continuum by decreasing the estimated flux by 10%" (2.3.3 Average [C II] signal)
   - assumption: Stack size fixed to the average optical size of the sources entering the stack  
  > "We fitted the resulting map with an exponential model with size fixed to the average optical size of the sources entering the stacking." (2.3.3 Average [C II] signal)
   - fitting: _not stated_
   - validation: Expected false detections < 0.1 among the six sources for the 2.3 sigma tentative signals; average ratio from stacking agrees with the mean of individual ratios  
  > "Furthermore, when considering the six sources discussed above, we expect to find $<0.1$ false detections." (2.3.2 Tentative and non detections)
9. **Measure continuum fluxes and fit IR SEDs for L_IR, M_dust and <U>**: Exponential-profile uv fits of the 450 and 850 um continuum, combined with Spitzer and Herschel photometry in Draine & Li model and modified black body fits  
  > "We extracted the continuum flux by fitting the data with an exponential profile, adopting the same procedure described in Section" (2.4 Continuum emission); "we fitted the IR photometry with (cite: Draine2007) models, supplemented by the use of a single temperature modified black body (MBB) fit to derive a representative dust temperature of the ISM" (2.4 Continuum emission)
   - software: GILDAS
   - parameter: L_IR integrated over 8-1000 um from SED fitting  
  > "IR luminosity integrated over the wavelength range 8 – 1000 $\mu$m as estimated from SED fitting" (Table 1)
   - parameter: <U> = L_IR/(125 M_dust)  
  > "We also determined the average radiation field intensity as $\langle U\rangle = L_{\mathrm{IR}}/(125 M_{\mathrm{dust}})$" (2.4 Continuum emission)
   - assumption: Modified black body beta = 2.0  
  > "with fixed $\beta$ = 2.0 (the same as used in the SED fitting for our sample galaxies)" (3.1 The [C II] deficit)
   - assumption: Measured fluxes with uncertainties used even when S/N < 3 instead of upper limits  
  > "In these fits we considered the measured *Spitzer*, *Herschel*, and ALMA flux (even if S/N $<$ 3, e.g. there is no detection)" (2.4 Continuum emission)
   - fitting: Uncertainties on L_IR and M_dust by Monte Carlo simulations; points weighted by their uncertainties  
  > "Uncertainties on $L_{\mathrm{IR}}$ and $M_{\mathrm{dust}}$ were quantified using Monte Carlo simulations" (2.4 Continuum emission); "The contribution of each photometric point to the best fit is weighted by its associated uncertainty." (2.4 Continuum emission)
   - validation: Conclusions unchanged if upper limits are used in the fits; median L_IR and M_dust agree with literature MS values  
  > "If we were to use upper limits in these fits instead our conclusions would not have changed." (2.4 Continuum emission)
10. **Estimate molecular gas masses of the sample**: (1) M_mol = delta_GDR x M_dust with metallicity from stellar mass via a mass-metallicity relation; (2) integrated Schmidt-Kennicutt relation from SFR; the Schmidt-Kennicutt masses are adopted; [C II]-based masses use alpha_[CII] = 31 Msun/Lsun  
  > "Given their stellar mass and the mass-metallicity relation by (cite: Zahid2014) we estimated their gas phase metallicity." (2.4 Continuum emission); "In the following we use the $M_{\mathrm{mol}}$ obtained from the Schmit-Kennicutt relation" (2.4 Continuum emission); "conversion factor $\alpha_{\mathrm{[C~{\small II}]}} = 31$ M$_\odot$/L$_\odot$" (Table 2)
   - parameter: SFR = 1e-10 L_IR (Kennicutt 1998); SK relation dispersion 0.2 dex  
  > "$SFR = 10^{-10}L_{\mathrm{IR}}$" (Table 2)
   - assumption: Chabrier IMF; flat LCDM with Om = 0.3, OL = 0.7, H0 = 70  
  > "We assumed a (cite: Chabrier2003) initial mass function (IMF)" (1 Introduction)
   - fitting: _not stated_
   - validation: Dust-based and Schmidt-Kennicutt gas masses consistent for galaxies with 850 um detections  
  > "we concluded that both methods give consistent results" (2.4 Continuum emission)
11. **Compile literature samples and fit L_[CII] versus M_mol and alpha_[CII]**: Homogenise literature samples (IR luminosities to 8-1000 um, metallicities to Pettini2004 calibration, alpha_CO = f(metallicity) for CO-based masses), fit the log-log L_[CII]-M_mol relation, and compute alpha_[CII] = L_[CII]/M_mol medians for sub-samples  
  > "Also we homogenized all the IR luminosities reporting them to the 8 – 1000 $\mu$m range." (C. Literature data); "we converted all metallicity estimates to the calibration by (cite: Pettini2004) using the parametrizations by (cite: Kewley2008)" (3.4 Invariance of alpha_[CII] with gas phase metallicity); "we complemented our sample with all literature data we could assemble" (3.2 [C II] as a tracer of molecular gas)
   - parameter: alpha_CO metallicity dependence: log alpha_CO = 0.64 - 1.5 (12 + log(O/H) - 8.7)  
  > "\log \alpha_{\mathrm{CO}} = 0.64 - 1.5 (12 + \log (O/H) - 8.7)" (3.4 Invariance of alpha_[CII] with gas phase metallicity)
   - assumption: alpha_CO slope of -1 or -2 would not change conclusions  
  > "would not change our conclusions" (3.4 Invariance of alpha_[CII] with gas phase metallicity)
   - fitting: Linear fit in log space; Pearson correlation coefficient quoted  
  > "The Pearson test yields a coefficient $\rho = 0.97$" (3.2 [C II] as a tracer of molecular gas)
   - validation: Scatter of L_[CII]-L'_CO relation compared with that of alpha_[CII]; starburst (SPT) and local samples compared  
  > "The mean absolute deviation of the relation is $\sim$ 0.2 dex, similar to that of the $L_{\rm [C~{\small II}]}$ - $M_{\rm mol}$ relation." (3.2 [C II] as a tracer of molecular gas)
12. **Compare L_[CII]/L_IR versus sSFR/sSFR_MS with depletion-time models**: Bin samples by distance from the main sequence, overplot Sargent2014 and Scoville2017 depletion-time models rescaled to the main-sequence [CII]/IR ratio and convolved with a 0.2 dex Gaussian  
  > "predicting how the depletion time of galaxies changes as a function of their distance from the main-sequence and rescaled them" (3.3 The dependence of the [C II]-to-IR ratio); "we convolved the models by (cite: Sargent2014) and (cite: Scoville2017) with a Gaussian function with FWHM $\sim$ 0.2 dex" (3.3 The dependence of the [C II]-to-IR ratio)
   - parameter: Rescaling implies L_[CII]/L_CO ~ 6000  
  > "we estimated $L_{\mathrm{[C~{\small II}]}}/L_{\mathrm{CO}} \sim 6000$" (3.3 The dependence of the [C II]-to-IR ratio)
   - assumption: Starbursts defined as > 4 times above the main sequence  
  > "Throughout this paper we will consider as starbursts all the sources that fall $> 4$ times above the main sequence (cite: Rodighiero2011)." (1 Introduction)
   - fitting: _not stated_
   - validation: Rescaled [CII]/CO ratio compared with the 2000-10000 range in the literature  
  > "This is in good agreement with the typical values reported in the literature and ranging between 2000 – 10000" (3.3 The dependence of the [C II]-to-IR ratio)
13. **Test dependence of alpha_[CII] on metallicity and of L_[CII]/SFR on metallicity**: Linear fits of alpha_[CII] versus metallicity and of L_[CII]/SFR_TOT versus SFR_IR/SFR_TOT and metallicity for local low-metallicity galaxies  
  > "When fitting the data with a linear function we obtain a slope of $-0.2 \pm 0.2$" (3.4 Invariance of alpha_[CII] with gas phase metallicity)
   - assumption: SFR estimates from the literature taken at face value  
  > "taking at face value the SFR estimates from the literature" (3.5 Implications for surveys at z > 2)
   - fitting: Linear fits with quoted slopes and scatter  
  > "and a standard deviation of 0.3 dex" (3.4 Invariance of alpha_[CII] with gas phase metallicity)
   - validation: _not stated_

## Software

- **CASA** : Standard ALMA pipeline reduction, simobserve simulations and uvmodelfit cross-checks  
  > "The data were reduced with the standard ALMA pipeline based on the CASA software" (2.3 [C II] emission line measurements); "We then fitted these mock data in the *uv* plane with the task `uvmodelfit`." (A. Resolution)
- **GILDAS** : uv-plane spectral extraction, source fitting (uv_fit), stacking and size fits  
  > "The calibrated data cubes were then converted to *uvfits* format and analyzed with the software GILDAS" (2.3 [C II] emission line measurements); "with the GILDAS task `uv_fit`" (2.3 [C II] emission line measurements)
- **GALFIT** : Exponential-profile fits to HST stellar mass maps to get disk sizes  
  > "using the GALFIT algorithm (cite: Peng2010)" (2.3 [C II] emission line measurements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C II] luminosity, ID9347 (detection) | 0.95 | 0.30 | 1e9 Lsun | 6 | 21.28 $\pm$ 6.73 / 0.95 $\pm$ 0.30 / 11.80 $\pm$ 0.05 / $1.51^{+0.51}_{-0.50}$ |
| [C II] luminosity, ID6515 (detection) | 1.23 | 0.33 | 1e9 Lsun | 6 | 24.50 $\pm$ 6.57 / 1.23 $\pm$ 0.33 / 11.68 $\pm$ 0.04 / $2.57^{+0.73}_{-0.73}$ |
| [C II] luminosity, ID10076 (detection) | 2.40 | 0.76 | 1e9 Lsun | 6 | 29.03 $\pm$ 9.14 / 2.40 $\pm$ 0.76 / 11.91 $\pm$ 0.03 / $2.95^{+0.96}_{-0.96}$ |
| [C II] luminosity, ID9834 (detection) | 1.29 | 0.19 | 1e9 Lsun | 6 | 15.34 $\pm$ 2.21 / 1.29 $\pm$ 0.19 / 11.99 $\pm$ 0.02 / $1.32^{+0.22}_{-0.22}$ |
| [C II] flux and luminosity of the average stack (7 galaxies) | F_[CII] = 15.59 mJy; L_[CII] = 1.25 (1e9 Lsun) | 1.79 (flux); 0.14 (luminosity) | mJy; 1e9 Lsun | 8 | 15.59 $\pm$ 1.79 / 1.25 $\pm$ 0.14 / 11.81 $\pm$ 0.05 |
| Average L_[CII]/L_IR of the stack | 1.94e-3 | +0.34/-0.32 (1e-3) | dimensionless | 8 | stacking of the seven targets mentioned above is $(1.94^{+0.34}_{-0.32})\times 10^{-3}$ |
| [C II] exponential scale length of the 4-detection stack | 0.65 arcsec (~4-7 kpc) | 0.15 arcsec | arcsec | 7 | $0.65\pm0.15''$ (corresponding to $\sim$ 4 – 7 kpc) |
| Range of L_IR (8-1000 um) of the sample | 3.5e11 - 1.2e12 | not stated | Lsun | 9 | lie between $3.5 \times 10^{11}$ – $1.2 \times 10^{12}$ L$_{\odot}$ |
| Average L_[CII]/L_IR of our data and scatter | ~1.9e-3; scatter ~0.15 dex | not stated | dimensionless | 8 | The average $L_{\mathrm{[C~{\small II}]}}/L_{\mathrm{IR}}$ ratio of our data is $\sim 1.9 \times 10^{-3}$, and has a scatter of $\sim$ 0.15 dex |
| L_[CII]-M_mol relation: log L = -1.28 + 0.98 log M_mol (dispersion 0.3 dex) | intercept -1.28, slope 0.98 | +/-0.21 (intercept), +/-0.02 (slope) | dimensionless | 11 | \log L_{\mathrm{[C~{\small II}]}} = -1.28(\pm 0.21) + 0.98(\pm 0.02) \log M_{\mathrm{mol}}; with a dispersion of 0.3 dex |
| Median alpha_[CII] for main-sequence galaxies | 31 | MAD 0.2 dex (standard deviation 0.3 dex) | Msun/Lsun | 11 | we get a median $\alpha_{\mathrm{[C~{\small II}]}} = 31$ M$_\odot$/L$_\odot$ with a median absolute deviation of 0.2 dex |
| Median alpha_[CII], local sample | 28 | MAD 0.2 dex | Msun/Lsun | 11 | / Local / 30 / 0.3 / 28 / 0.2 / |
| Median alpha_[CII], high-z sample | 38 | MAD 0.1 dex | Msun/Lsun | 11 | / High-$z$ / 35 / 0.2 / 38 / 0.1 / |
| Median alpha_[CII], SPT lensed starburst sample | 22 | not stated | Msun/Lsun | 11 | We obtained a median $\alpha_{\mathrm{[CII]}} = 22$ M$_\odot$/L$_\odot$ for this sample |
| L_[CII]/L_CO implied by rescaled depletion-time models | ~6000 | not stated | dimensionless | 12 | we estimated $L_{\mathrm{[C~{\small II}]}}/L_{\mathrm{CO}} \sim 6000$ |
| Slope of alpha_[CII] versus metallicity | -0.2 | 0.2 | dimensionless | 13 | we obtain a slope of $-0.2 \pm 0.2$ |
| Fit of local L_[CII]/L_IR versus <U> (Diaz-Santos sample): intercept and slope | intercept -2.1, slope 0.7 (dispersion 0.3 dex) | +/-0.1, +/-0.1 | dimensionless | 0 | -2.1(\pm 0.1) + 0.7(\pm 0.1) \log(<{\mathrm{U}}>) |
| Fit of L_[CII]/SFR_TOT versus metallicity: intercept and slope | intercept -3.8, slope 1.3 (dispersion 0.2 dex) | +/-2.8, +/-0.3 | dimensionless | 13 | -3.8(\pm 2.8) + 1.3(\pm 0.3) [12 + \log (O/H)] |
| Astrometric offset of HST relative to ALMA in declination | -0.2 | > 3 sigma significant | arcsec | 3 | instead significant in declination ($\Delta DEC = -0.2$”, $> 3\sigma$ significant) |

## Qualitative findings

- z~2 main-sequence galaxies are not [C II] deficient; L_[CII]/L_IR is similar to local main-sequence galaxies and ~10 times higher than starbursts  
  > "is similar to that of local main-sequence galaxies ($\sim2\times10^{-3}$), and $\sim$ 10 times higher than that of starbursts" (abstract)
- [C II] emission is spatially extended on scales consistent with the optical size  
  > "has an average spatial extent of 4 – 7 kpc, consistent with the optical size" (abstract)
- Starburst [C II] deficit can be explained mainly by their higher star formation efficiency  
  > "the \[C II\]  deficiency of starbursts can be explained as mainly due to their higher star formation efficiency" (3.3 The dependence of the [C II]-to-IR ratio)

## Claim tuples

- H: z~2 main-sequence galaxies are [C II] deficient like local (U)LIRGs given their SFRs and radiation fields | E: Measured [C II] fluxes with uv-plane fits and compared L_[CII]/L_IR with literature compilations | R: L_[CII]/L_IR ~ 2e-3 for the stack, similar to local main-sequence galaxies and ~10x higher than starbursts | F: High-z main-sequence galaxies are not [C II] deficient; the ratio is not set by L_IR, dust temperature or <U> alone | **supported**
- H: [C II] emission in these galaxies has an extent comparable to the optical disk | E: uv-plane stack of the four detections fitted with a free-size exponential profile | R: Exponential scale length 0.65 +/- 0.15 arcsec (~4-7 kpc), ~4 sigma significance in size | F: [C II] extent is consistent with the optical size | **supported**
- H: [C II] luminosity is a tracer of molecular gas mass | E: Combined the sample with literature [C II] and M_mol data and fitted L_[CII] versus M_mol | R: Linear relation, slope 0.98 +/- 0.02, dispersion 0.3 dex, rho = 0.97 | F: [C II] luminosity correlates with molecular gas mass with a mean absolute deviation of 0.2 dex | **supported**
- H: alpha_[CII] is independent of depletion time, metallicity and redshift | E: Compared alpha_[CII] medians for main-sequence, starburst, low- and high-z samples and fitted alpha_[CII] against metallicity | R: Median alpha_[CII] ~ 30 Msun/Lsun; metallicity slope -0.2 +/- 0.2, consistent with zero | F: [C II] is a convenient molecular gas tracer regardless of starburst or main-sequence nature and for metal-poor galaxies | **supported**
- H: alpha_[CII] stays constant even for the most extreme starbursts | E: Estimated gas masses for local (U)LIRGs from depletion-time models and compared alpha_[CII] | R: alpha_[CII] decreases by 0.3 dex for the most extreme starbursts with the averaged-model gas masses but stays constant with the Scoville2017 model only | F: More observations are needed to explore the extreme starburst regime | **partially**

## Reasoning

- Why this data: Band 9 [C II] observations of the largest sample at this redshift; ALMA Band 7 added for dust masses  
  > "Currently this is the largest sample of galaxies observed with ALMA at this redshift" (2.2 Details of ALMA observations)
- Why this method: Sources are resolved, so fluxes are measured in the uv plane with extended models  
  > "We concluded that, when fitting the sources in the *uv* plane, we could measure their correct total fluxes" (2.2 Details of ALMA observations)
- Alternative: PSF model for total fluxes rejected because it underestimates fluxes of extended sources  
  > "whereas by using a PSF model instead we would have underestimated the fluxes" (2.3.1 Individual [C II] detections)
- Alternative: Gaussian profile instead of exponential gives consistent [C II] fluxes  
  > "fitting the data with a Gaussian profile instead of an exponential would give consistent" (2.3.1 Individual [C II] detections)
- Alternative: Dust-based gas masses not adopted; Schmidt-Kennicutt masses used as more robust for galaxies without 850 um detections  
  > "In the following we use the $M_{\mathrm{mol}}$ obtained from the Schmit-Kennicutt relation" (2.4 Continuum emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Fluxes depend critically on the assumed model size taken from optical images  
  > "However, the returned fluxes critically depend on the model size that we used and that we determined from the optical images." (2.3.1 Individual [C II] detections)
- Limitation (authors): Source size cannot be constrained from individual sources because of low S/N  
  > "Unfortunately, the size of the emission cannot be constrained from the data on individual sources, given the limited S/N ratio." (2.3.1 Individual [C II] detections)
- Limitation (authors): Observed in a more extended configuration than requested, giving 5-10 times higher flux errors  
  > "Our sources were therefore resolved." (2.2 Details of ALMA observations); "we obtained a flux measurement error 5 – 10 times higher than expected" (2.2 Details of ALMA observations)
- Caveat (inferred, ours): Total [C II] fluxes rest on optical-size exponential models; a different size changes flux linearly, so L_[CII] and alpha_[CII] are model dependent
- Caveat (inferred, ours): Detections at 2.3 sigma are called real from a posteriori reasoning; small numbers (4 secure, 2 tentative)
- Caveat (inferred, ours): Stack excludes three non-detections (incl. an AGN and two poor-weather sources), which may bias the average ratio high
- Caveat (inferred, ours): alpha_[CII] derived from heterogeneous literature gas masses (different alpha_CO, SK relation, depletion-time models) that partly share assumptions with the SFR used in L_IR
- Caveat (inferred, ours): Single Cycle 1 execution; no flux calibrator or calibration uncertainty stated for Band 9

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA/pipeline versions, calibrators and flux scale uncertainty
- Missing: Exact channel ranges, GILDAS fit settings and HST-derived sizes/positions per galaxy (only R_e listed)
- Missing: HST, Spitzer and Herschel inputs and SED-fit settings needed to reproduce L_IR and M_dust
- Missing: Full literature compilation table (stated to be online)
- Data volume (inferred): Roughly 10-50 GB raw for 10 Band 9 fields plus Band 7 (inferred; two Cycle 1 observing nights)
- Score (inferred): 5/5, ALMA data and main procedure are described and the GILDAS uv-fitting approach is documented, but calibration details, per-source fit inputs and the literature compilation are incomplete.
- Rediscovery candidate: no, The paper does not state that the data are public, and key inputs (HST-derived sizes, SED-based L_IR, full literature table, channel ranges) are not fully given.

## Links

- Method: (cite: Coogan2017) (Similar iterative uv-plane line detection procedure and redshift-uncertainty simulations)
- Method: (cite: Cibinel2015) (Method for resolved stellar mass and SFR maps from pixel-by-pixel SED fitting)
- Method: (cite: Magdis2012) (IR SED fitting method, gas-to-dust ratio and Monte Carlo uncertainties)
- Method: (cite: Gobat2017) (Redshift refinement from rest-frame UV spectra with LBG templates)
- Companion: Daddi et al. (2015 and in preparation) (Earlier and forthcoming use of the same uv-plane extraction procedure)
- Related: GOODS-S
- Related: CANDELS
- Related: GMASS survey
- Related: ALMA Cycle 1 program 2012.1.00775.S

## Checks

```json
{
 "quotes": 184,
 "quotes_ok": 184,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 137,
  "stated": 108,
  "rate": 0.788
 },
 "evidence_ok": true
}
```
