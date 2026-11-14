# JWST and ALMA Multiple-line Study in and around a Galaxy at z = 8.496: Optical to Far-Infrared Line Ratios and the Onset of an Outflow Promoting Ionizing Photon Escape

`2024ApJ...964..146F` | The Astrophysical Journal 2024 | first author: Fujimoto, Seiji | arXiv: 2212.06863 | DOI: 10.3847/1538-4357/ad235c

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the FIR line (and dust continuum) properties of the lensed z=8.496 galaxy ID4590 from ALMA, and how do they combine with JWST data to explain its [OIII]/[CII] ratio, electron density and signs of outflow  
  > "Previous ALMA observations have also raised questions about what causes large diversity in EoR galaxies and the difference from local galaxies." (Introduction); "providing a timely, unique reference for future follow-up of EoR galaxies in the coming decade." (Introduction)
- Target **ID4590 (lensed galaxy in SMACS J0723.3-7327, SM0723)**: coordinates Cluster field 07h23m13.3s, -73d27m25s (ID4590 JWST position 07:23:26.255, -73:26:57.041 listed in Table 2, not quoted)  
  > "The target was a strongly lensed star-forming galaxy, ID4590, spectroscopically confirmed at $z=8.496$ with the robust detection of rest-frame optical emission lines including the" (ALMA); "The target field, SMACS J0723.3-7327 (hereafter SM0723), is a massive galaxy cluster at $z=0.390$ ($07^{h}23^{m}13.3^{s}$, $-73^{d}27^{m}25^{s}$)" (SMACS J0723.3-7327); "based on the source redshift spectroscopically determined by NIRSpec." (3.2 Continuum & Line Measurements); z/distance z = 8.496 (spectroscopic); lensing magnification mu = 8.69  
  > "The target was a strongly lensed star-forming galaxy, ID4590, spectroscopically confirmed at $z=8.496$ with the robust detection of rest-frame optical emission lines including the" (ALMA); "The target field, SMACS J0723.3-7327 (hereafter SM0723), is a massive galaxy cluster at $z=0.390$ ($07^{h}23^{m}13.3^{s}$, $-73^{d}27^{m}25^{s}$)" (SMACS J0723.3-7327); "based on the source redshift spectroscopically determined by NIRSpec." (3.2 Continuum & Line Measurements); distance from JWST/NIRSpec spectroscopic redshift; magnification from Glafic mass model  
  > "The target was a strongly lensed star-forming galaxy, ID4590, spectroscopically confirmed at $z=8.496$ with the robust detection of rest-frame optical emission lines including the" (ALMA); "The target field, SMACS J0723.3-7327 (hereafter SM0723), is a massive galaxy cluster at $z=0.390$ ($07^{h}23^{m}13.3^{s}$, $-73^{d}27^{m}25^{s}$)" (SMACS J0723.3-7327); "based on the source redshift spectroscopically determined by NIRSpec." (3.2 Continuum & Line Measurements)

## Data provenance

- ALMA projects: 2022.A.00022.S
- bands: Band 5 and Band 7  
  > "ALMA Band 5 and Band 7 follow-up observations of" (ALMA)
- frequencies and spectral setup: Frequency Division Mode; lines near 357.3 GHz (Band 7) and 200.2 GHz (Band 5)  
  > "Both observations used the Frequency Division Mode" (ALMA); "we identify positive signals in several consecutive channels at around 357.3 GHz and 200.2 GHz in Band 7 and Band 5, respectively" (3.2 Continuum & Line Measurements)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C-3 configuration, baselines 15-457 m (text)  
  > "baseline ranges 15–457 m in the C-3 configuration." (ALMA)
- baselines: _not stated_
- angular resolution: Natural-weighted beams 1.35"x1.25" (Band 5) and 0.71"x0.58" (Band 7)  
  > "$1.35\ensuremath{''}\times1.25\ensuremath{''}$ and $0.71\ensuremath{''}\times0.58\ensuremath{''}$" (ALMA)
- max recoverable scale: _not stated_
- sensitivity: Continuum (line, 20 km/s channel) 1 sigma: 11.6 (225) uJy/beam Band 5; 20.9 (420) uJy/beam Band 7  
  > "of 11.6 (225) $\mu$Jy beam$^{-1}$ and 20.9 (420) $\mu$Jy beam$^{-1}$ in Band 5 and Band 7, respectively." (ALMA)
- time on source: 85.7 min (Band 5), 99.8 min (Band 7)  
  > "the on-source integration times were 85.7 mins and 99.8 mins in Band 5 and Band 7, respectively." (ALMA)
- observing dates: 2022-10-17 (Band 5), 2022-10-14 (Band 7)  
  > "were carried out on October 17th and 14th 2022, respectively" (ALMA)
- pi or archival as stated: Cycle 8 DDT program, PI S. Fujimoto  
  > "as a Cycle 8 DDT program (#2022.A.00022.S, PI: S. Fujimoto)." (ALMA)
- Line: [O III] 88 um fine-structure line (not stated)
- Line: [C II] 158 um fine-structure line (not stated)
- Other facility **JWST (NIRCam, MIRI, NIRSpec)**: ERO imaging photometry and NIRSpec spectrum used for redshift, emission lines, metallicity, Te, SED  
  > "As part of the *JWST* ERO (#ERO-2736; (cite: pontoppidan2022)), SM0723 was observed with *JWST*/NIRCam, NIRSpec, MIRI, and NIRISS in June 2022." (JWST)
- Other facility **HST (RELICS, WFC3 archival)**: Archival WFC3 imaging photometry and RELICS lens models  
  > "Existing multi-wavelength WFC3 archival imaging from *HST* was also processed with `grizli`" (JWST)
- External data: NIRSpec emission-line fluxes, Te, 12+log(O/H), log U limit, used as inputs  
  > "In our paper, we use results from (cite: nakajima2023) due to requirements of specific parameter sets for the photoionization model analysis" (JWST) [from (cite: nakajima2023)]
- External data: C/O abundance range from NIRSpec  
  > "The lower and upper boundaries of the C/O abundance are also estimated to be" (JWST) [from (cite: isobe2023b)]
- External data: Lens model magnification mu=8.69 (Glafic) for ID4590  
  > "In this paper, we use the latest Glafic model." (3.1 Mass Model); "The magnification factor for ID4590 is estimated to be $\mu=8.69$" (3.1 Mass Model) [from (cite: harikane2022b); (cite: oguri2021b)]
- External data: Gas mass of ID4590 listed in Table 2  
  > "$a$ (cite: heintz2022c)" (Table 2) [from (cite: heintz2022c)]
- External data: Literature compilations of z~6-9 ALMA line luminosities and local dwarf galaxies for comparison  
  > "we also present compilations of recent ALMA results for $z\sim6$–9 galaxies in literature" (4.2 SFR-L_[CII], L_[OIII], and L_[OIII]/L_[CII] Relations) [from (cite: harikane2020; fujimoto2021); (cite: delooze2014; cormier2015)]

## Processing

### Calibration

- pipeline or manual: Standard pipeline script  
  > "with the pipeline script in the standard manner." (ALMA)
- casa version: CASA 6.4.1.12  
  > "The ALMA data were reduced and calibrated with the Common Astronomy Software Applications package version 6.4.1.12" (ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-4546 (flux and bandpass)  
  > "J0519-4546 was observed as a flux and bandpass calibrator in both observations" (ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "and a primary beam limit down to 0.2 by running the CASA task tclean." (ALMA)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We imaged the calibrated visibilities using natural weighting" (ALMA)
- uv taper: _not stated_
- cell size: 0.05 arcsec  
  > "a pixel scale of $0.05\ensuremath{''}$" (ALMA)
- image size: _not stated_
- masking: automask mode (continuum); 100,000 max iterations, cleaned to 1 sigma  
  > "with a maximum iteration number of 100,000 in the automask mode" (ALMA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: central +-120 km/s channels masked for the continuum map  
  > "We mask the central $\pm120$ km s$^{-1}$ channels to avoid contamination from the" (ALMA)
- primary beam correction: primary beam limit down to 0.2  
  > "and a primary beam limit down to 0.2 by running the CASA task tclean." (ALMA)
- array combination: _not stated_
- smoothing: cubes made at 20, 30, 40 km/s channels; 20 km/s used  
  > "we used 20 km/s resolution cubes in the following analyses." (ALMA)
- final beam: 1.35"x1.25" (Band 5), 0.71"x0.58" (Band 7)  
  > "$1.35\ensuremath{''}\times1.25\ensuremath{''}$ and $0.71\ensuremath{''}\times0.58\ensuremath{''}$" (ALMA)
- final rms: continuum 11.6 uJy/beam (B5), 20.9 uJy/beam (B7); line 225 and 420 uJy/beam per 20 km/s  
  > "of 11.6 (225) $\mu$Jy beam$^{-1}$ and 20.9 (420) $\mu$Jy beam$^{-1}$ in Band 5 and Band 7, respectively." (ALMA)

### Inherited from earlier work

- Continuum automask mode in tclean  
  > "with a maximum iteration number of 100,000 in the automask mode (cite: kepley2020)." (ALMA) [from (cite: kepley2020)]
- CMB effect correction on submm/mm fluxes  
  > "following the recipe presented by (cite: dacunha2013)" (Introduction) [from (cite: dacunha2013)]
- NIRSpec reduction, line fluxes, Te, metallicity, slit-loss correction  
  > "In our paper, we use results from (cite: nakajima2023) due to requirements of specific parameter sets for the photoionization model analysis" (JWST) [from (cite: nakajima2023)]
- JWST NIRCam/MIRI reduction details deferred to a future paper  
  > "The detailed calibration and reduction procedures will be presented in Brammer et al. (in prep.)" (JWST) [from Brammer et al. (in prep.)]
- Fiducial dust temperature of 60 K  
  > "based on the extrapolation of the best-fit redshift evolution model of" (3.5 FIR SED) [from (cite: sommovigo2022)]
- CIGALE SED fitting setup  
  > "The fitting was performed similarly as in (cite: fujimoto2022b)" (3.6 Full SED analysis) [from (cite: fujimoto2022b)]
- Cloudy comparison plane drawn in the same manner  
  > "drawn in the same manner as (cite: harikane2020)" (4.5 Physical origins) [from (cite: harikane2020)]

### Not stated but needed to reproduce (our reading)

- Cloudy input grid and settings (SED, geometry, grid steps) for the [OIII]/SFR vs [CII]/SFR comparison
- Exact velocity channels and aperture used for the moment 0 maps and line fluxes
- Which of the two stated baseline ranges (15-457 m in text vs 15.1-629.3 m in Table 1) applies
- Spectral windows and continuum bandwidth for each band
- Self-calibration choice, flux scale uncertainty and flux density of calibrators
- CIGALE module parameter values not printed in the table (many entries blank), and priors
- NIRSpec slit-loss corrected line fluxes (in Nakajima et al. 2023)
- Lenstool/Glafic model files for the magnification and source-plane reconstruction
- Rest frequencies used for the line cubes
- PyNeb atomic data sets and the Te and extinction values used to map the line ratio to n_e

## Analysis recipe

1. **Image calibrated visibilities into continuum maps and line cubes**: tclean with natural weighting, 0.05 arcsec pixels, 20 km/s channels, automask for continuum  
  > "We imaged the calibrated visibilities using natural weighting" (ALMA); "we used 20 km/s resolution cubes in the following analyses." (ALMA)
   - software: CASA tclean
   - parameter: primary beam limit 0.2; 100,000 iterations (continuum)  
  > "with a maximum iteration number of 100,000 in the automask mode" (ALMA)
   - fitting: _not stated_
   - validation: Results unchanged within 10% for 20, 30, 40 km/s channel choices  
  > "We confirmed the results unchanged much ($<$10 %) in the following analyses via the choice of the spectral resolutions" (ALMA)
2. **Measure line and continuum fluxes, redshifts, widths**: Moment 0 maps from line-detected channels; single Gaussian fit to spectra; 2 arcsec aperture for [CII]; peak pixel for unresolved [OIII]; 2 sigma continuum upper limits from map standard deviation  
  > "From a single Gaussian fit in the spectra, we estimate the frequency center and the line redshifts as" (3.2 Continuum & Line Measurements); "With a 2$''$-diameter aperture in the moment 0 maps, we measure the line intensities" (3.2 Continuum & Line Measurements); "based on the standard deviation of the maps." (3.2 Continuum & Line Measurements)
   - software: CASA
   - assumption: Continuum emission assumed unresolved; [OIII] assumed spatially unresolved  
  > "We assume that the emission is unresolved in the continuum maps with the current ALMA beam" (3.2 Continuum & Line Measurements)
   - fitting: Single Gaussian line profile fit  
  > "From a single Gaussian fit in the spectra, we estimate the frequency center and the line redshifts as" (3.2 Continuum & Line Measurements)
   - validation: Removing three channels around [OIII] secondary peak keeps peak S/N 4.0 but lowers flux by ~20%  
  > "We confirm that removing the three channels around the secondary peak" (3.2 Continuum & Line Measurements)
3. **Test chance projection of noise for the [CII] line**: Blind line search with Findclump in Interferopy on the Band 5 20 km/s cube, spatial tolerance 1.2 arcsec, frequency tolerance 100 MHz  
  > "running a blind line search algorithm of Findclump implemented in a Python library of Interferopy (cite: interferopy)" (3.2 Continuum & Line Measurements)
   - software: Interferopy (Findclump)
   - parameter: ~180 features at similar or higher S/N in 259793 independent beams within 20 arcsec radius and 274 channels  
  > "We find that $\sim180$ line features are identified with similar or higher S/N in the entire data cube" (3.2 Continuum & Line Measurements)
   - fitting: _not stated_
   - validation: Chance projection 0.07%, purity >99.9%  
  > "we estimate the chance projection of the random noise is 0.07% (= 180 / 259793 $\times$ 1)" (3.2 Continuum & Line Measurements)
4. **Measure sizes of [CII], [OIII], UV and optical continuum**: CASA imfit 2D elliptical Gaussian (no fixed parameters) for lines; galfit 2D Sersic with WebbPSF PSFs on NIRCam F150W and F356W  
  > "we perform CASA imfit task to apply the 2D elliptical Gaussian fitting." (3.3 Sizes); "We conduct a 2D Sérsic profile fitting with galfit (cite: peng2010)." (3.3 Sizes)
   - software: CASA imfit, galfit, WebbPSF
   - parameter: F356W fit fixes axis ratio, PA and Sersic index from F150W  
  > "In the F356W fit for the rest-frame optical continuum, we fix the best-fit axis ratio, PA, and Seŕsic index from the F150W results" (3.3 Sizes)
   - fitting: 2D Gaussian / Sersic least-squares fits; priors not stated  
  > "we perform CASA imfit task to apply the 2D elliptical Gaussian fitting. We do not fix any parameters in the fitting." (Sizes)
   - validation: Residual maps show no significant signal; [OIII] 2 sigma size upper limit from interferometric size limits  
  > "We thus place a $2\sigma$ upper limit of FWHM $<0.31\ensuremath{''}$" (3.3 Sizes)
5. **Apply gravitational lensing correction**: Glafic mass model magnification mu=8.69 with 30% systematic uncertainty; radial and tangential magnifications used for morphology  
  > "we use $\mu=8.69$ and add a systematic uncertainty from the mass models of 30%." (3.1 Mass Model)
   - software: Glafic
   - parameter: mu_rad = 1.37, mu_tang = 6.35, PA -39.5 deg  
  > "$\mu_{\rm rad.}=1.37$ and $\mu_{\rm tang.}=6.35$" (3.1 Mass Model)
   - assumption: Differential magnification neglected for physical values  
  > "we do not account for differential magnification in the following analysis" (3.1 Mass Model)
   - fitting: _not stated_
   - validation: Compared with other models, Delta mu ~15-30%  
  > "the $\Delta\mu$ value is estimated to be $\sim$15–30% for ID4590." (3.1 Mass Model)
6. **Constrain FIR SED, IR luminosity and dust mass from upper limits**: Single modified blackbody normalized to the Band 7 upper limit, CMB effect included  
  > "we assume the single modified black body (MBB) for the FIR SED of ID4590." (3.5 FIR SED); "In Figure [3](#fig:fir_sed), we show three MBB models with $T_{\rm d}=30$ K, 60 K, and 90 K normalized to the upper limit of Band 7." (3.5 FIR SED)
   - parameter: Td = 60 K fiducial (+-30 K); beta_d = 1.8; L_IR over 8-1000 um  
  > "We adopt a fiducial $T_{\rm d}$ estimate of 60 K" (3.5 FIR SED)
   - assumption: Dust opacity kappa_nu = 5.1 (nu/nu_250um)^beta_d; beta_d = 1.8  
  > "with the dust opacity coefficient of $\kappa_{\nu}=5.1(\nu/\nu_{250\mu{\rm m}})^{\beta_{\rm d}}$" (3.5 FIR SED)
   - fitting: No fit; MBB scaled to upper limit  
  > "we show three MBB models with $T_{\rm d}=30$ K, 60 K, and 90 K normalized to the upper limit of Band 7." (FIR SED)
   - validation: Td changes of +-30 K change estimates by ~0.5-1.0 dex; consistent with CIGALE L_IR  
  > "where a $T_{\rm d}$ difference by $\pm30$ K changes the estimates by $\sim\pm$0.5–1.0 dex" (Table 2)
7. **Full optical-mm SED fitting for SFR, stellar mass, UV slope, E(B-V)**: CIGALE with delayed SFH plus burst, BC03 stellar models, SMC attenuation, Casey (2012) dust emission, no AGN, fitted on non-lens-corrected photometry with 10% systematic flux error  
  > "we perform SED fitting to the optical–mm photometry using cigale (cite: burgarella2005; noll2009; boquien2019)." (3.6 Full SED analysis); "Because no evidence of the presence of AGN has been reported, we do not include an AGN component in the model." (CIGALE parameters)
   - software: CIGALE, EAZY, grizli
   - parameter: Td range 30-90 K; beta_d = 1.8; alpha_d = 2.0; Chabrier IMF  
  > "We fix $\beta_{\rm d}=1.8$ and the mid-infrared power-law slope $\alpha_{\rm d}=2.0$ and adopt the $T_{\rm d}$ range of 30–90 K." (CIGALE parameters)
   - assumption: Delayed SFH SFR(t) ∝ t/tau^2 exp(-t/tau); SMC extinction curve; same E(B-V) for stars and nebula  
  > "During the SED fitting, the same $E(B-V)$ is used between stellar and nebular emission." (CIGALE parameters)
   - fitting: CIGALE fit; sampler/priors beyond table not stated; 1 sigma errors used for measurements below 2 sigma upper limits  
  > "In the fitting, we use the photometry with the $1\sigma$ error also for the measurements below the $2\sigma$ upper limits." (CIGALE parameters)
   - validation: Reduced chi2 0.99; outputs unchanged by 5-10% with/without ALMA limits  
  > "with the reduced $\chi^{2}$ value of 0.99" (3.6 Full SED analysis); "Note that we confirm that the SED outputs are unchanged beyond 5–10% with and without the ALMA upper limits" (3.6 Full SED analysis)
8. **Derive electron density from [OIII]88um/[OIII]5007**: PyNeb line ratio vs Te for different ne, evaluated at the NIRSpec Te with slit-loss corrected [OIII]5007 and ALMA [OIII]88um, after removing 8% extended F444W contribution  
  > "we derive the \[O iii\]88$\mu$m/$\lambda$5007 line ratio for ID4590" (4.1 Electron density); "we remove this 8% contribution of the extended ionized gas to the total flux measurement in the F444W filter." (Morphology)
   - software: PyNeb
   - assumption: Te from direct method (NIRSpec); same emitting region for the two lines  
  > "which provides us with the robust measure of $T_{\rm e}$" (4.1 Electron density)
   - fitting: 1 sigma interval from ratio uncertainty  
  > "Based on the $1\sigma$ uncertainties, we evaluate $n_{\rm e}=220^{+230}_{-130}$ cm$^{-3}$." (4.1 Electron density)
   - validation: Compared with other n_e measurements across redshift  
  > "Our measurement is also broadly consistent with recent NIRSpec measurements for $z\sim4-9$ galaxies using the \[O ii\] doublet" (4.1 Electron density)
9. **Compare [OIII]/SFR and [CII]/SFR with Cloudy predictions**: Cloudy photoionization region for ID4590 with fiducial Zgas, ne, log U and C/O from NIRSpec; SFR from dust-corrected Halpha  
  > "We also show the magenta-shaded region that corresponds to the possible space for ID4590 calculated by Cloudy with our fiducial estimates of" (4.5 Physical origins); "we use the SFR value based on the dust-corrected H$\alpha$ luminosity estimated from NIRSpec" (4.5 Physical origins)
   - software: Cloudy
   - fitting: _not stated_
   - validation: Observed ID4590 point lies within the magenta region within errors  
  > "is consistent with the magenta-shaded region within the errors." (4.5 Physical origins)

## Software

- **CASA** 6.4.1.12: Pipeline reduction, tclean imaging, imfit  
  > "The ALMA data were reduced and calibrated with the Common Astronomy Software Applications package version 6.4.1.12" (ALMA)
- **Interferopy** : Findclump blind line search  
  > "running a blind line search algorithm of Findclump implemented in a Python library of Interferopy (cite: interferopy)" (3.2 Continuum & Line Measurements)
- **galfit** : Sersic fits to NIRCam images  
  > "We conduct a 2D Sérsic profile fitting with galfit (cite: peng2010)." (3.3 Sizes)
- **grizli** : Reduction and drizzling of NIRCam, MIRI and HST images  
  > "were retrieved and processed with the `grizli` pipeline (cite: brammer2021; brammer2023)" (JWST)
- **EAZY** : Photometric redshifts of nearby objects  
  > "We run the SED fitting code `EAZY` (cite: brammer2008) for these two nearby objects" (Morphology)
- **CIGALE** : Optical-mm SED fitting  
  > "we perform SED fitting to the optical–mm photometry using cigale (cite: burgarella2005; noll2009; boquien2019)." (3.6 Full SED analysis)
- **PyNeb** : [OIII]88/5007 line ratio vs Te and ne  
  > "drawn by using the nebular emission code `PyNeb`" (4.1 Electron density)
- **Cloudy** : Photoionization model for [OIII]/SFR vs [CII]/SFR  
  > "We also show the magenta-shaded region that corresponds to the possible space for ID4590 calculated by Cloudy with our fiducial estimates of" (4.5 Physical origins)
- **Glafic** : Lens mass model and magnification  
  > "In this paper, we use the latest Glafic model." (3.1 Mass Model)
- **WebbPSF** : NIRCam PSFs for galfit  
  > "which are generated from the `WebbPSF` model" (3.3 Sizes)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [OIII]88um line redshift | 8.4963 | 0.0009 | dimensionless | 2 | $z_{\rm [OIII]88}=8.4963 \pm 0.0009$ and $z_{\rm [CII]}=8.4931 \pm 0.0005$ |
| [CII]158um line redshift | 8.4931 | 0.0005 | dimensionless | 2 | $z_{\rm [OIII]88}=8.4963 \pm 0.0009$ and $z_{\rm [CII]}=8.4931 \pm 0.0005$ |
| [CII] FWHM | 118 | 36 | km/s | 2 | FWHM$_{\rm [CII]}=$ $118\pm36$ km s$^{-1}$ |
| [CII] luminosity (observed frame, no lens correction) | 1.45e8 | 0.32e8 | Lsun | 2 | $L_{\rm [CII]}=(1.45\pm0.32)\times10^{8}\,L_{\odot}$ in the observed frame (i.e., no lens correction) |
| [OIII]88um luminosity (observed frame) | 3.12e8 | 0.76e8 (text; plus 20% systematic) | Lsun | 2 | $L_{\rm [OIII]}=(3.12\pm0.76)\times10^{8}\,L_{\odot}$ from the peak pixel count |
| Continuum 2 sigma upper limits | <41.8 (Band 7, 0.85 mm); <23.2 (Band 5, 1.54 mm) | not stated | uJy | 2 | place 2$\sigma$ upper limits of 41.8 $\mu$Jy beam$^{-1}$ and 23.2 $\mu$Jy beam$^{-1}$ in Band 7 and Band 5, respectively |
| Chance projection probability of [CII] line | 0.07% | not stated | percent | 3 | we estimate the chance projection of the random noise is 0.07% (= 180 / 259793 $\times$ 1) |
| [CII] best-fit FWHM (major, minor) | 1.90 and 0.99 arcsec | 0.82 and 0.57 arcsec | arcsec | 4 | We obtain the best-fit FWHM of $1.90\ensuremath{''}\pm0.82\ensuremath{''}$ and $0.99\ensuremath{''}\pm0.57\ensuremath{''}$ in the major and minor axis |
| Circularized effective radii ([CII], UV, optical) | 0.69, 0.056, 0.059 arcsec | 0.42, 0.012, 0.010 arcsec | arcsec | 4 | we obtain the best-fit circularized effective radii of $0.69\ensuremath{''}\pm0.42\ensuremath{''}$, $0.056\ensuremath{''}\pm0.012\ensuremath{''}$, and $0.059\ensuremath{''}\pm0.010\ensuremath{''}$ for |
| Magnification of ID4590 | 8.69 | 30% systematic | dimensionless | 5 | The magnification factor for ID4590 is estimated to be $\mu=8.69$ |
| IR luminosity and dust mass upper limits (observed frame, Td=60 K) | log(LIR/Lsun)<11.2; log(Mdust/Msun)<6.0 | +-0.5-1.0 dex for Td +-30 K | dex | 6 | we obtain the upper limits of $\log(L_{\rm IR}/L_{\odot})<11.2$ and $\log(M_{\rm dust}/M_{\odot})<6.0$ with the fiducial $T_{\rm d}$ value of 60 K |
| SFR and stellar mass from SED (observed frame) | SFR = 26 Msun/yr; Mstar = 5.3e8 Msun | +9/-4 ; +5.6/-2.6 (x1e8) | Msun/yr; Msun | 7 | We obtain the best-fit values of SFR = 26$^{+9}_{-4}\,M_{\odot}$ yr$^{-1}$, $M_{\rm star}=5.3^{+5.6}_{-2.6}\times10^{8}\, M_{\odot}$ |
| Electron density | 220 | +230/-130 | cm^-3 | 8 | Based on the $1\sigma$ uncertainties, we evaluate $n_{\rm e}=220^{+230}_{-130}$ cm$^{-3}$. |
| [OIII]88um/[CII]158um line ratio at galaxy position | >4 | lower limit | dimensionless | 9 | ID4590 shows a $L_{\rm [OIII]}/L_{\rm [CII]}$ ratio of $>4$ |

## Qualitative findings

- [CII] is blue-shifted by ~90 km/s and spatially offset by ~0.5 arcsec from the JWST source while [OIII] coincides with it  
  > "while the \[C ii\] line appears blue-shifted by $\sim90$ km s$^{-1}$ beyond the errors." (3.2 Continuum & Line Measurements)
- NIRCam F444W emission is extended beyond the stellar continuum, interpreted as extended ionized gas  
  > "We interpret this extended emission attributed to strong emission lines of" (Morphology)

## Claim tuples

- H: Is the [CII] velocity and spatial offset a noise fluctuation | E: Blind line search with Findclump in the Band 5 cube | R: Chance projection probability 0.07% | F: [CII] offsets are real and associated with ID4590 | **supported**
- H: Does ID4590 show electron density evolution compared with z~2-3 galaxies | E: [OIII]88um/[OIII]5007 ratio with PyNeb at NIRSpec Te | R: ne = 220 (+230/-130) cm^-3 | F: ne is similar to z~2-3 galaxies and higher than local galaxies | **supported**
- H: Has ID4590 already experienced outflows promoting ionizing photon escape | E: Compare [CII] offset, F444W extended emission and sizes relative to stellar continuum | R: Extended [OIII]5007+Hbeta structure >8x the stellar effective radius and offset [CII] | F: Past and/or ongoing outflow is likely, which may help ionizing photon escape | **partially**
- H: What explains the high [OIII]/[CII] ratio in ID4590 | E: Compare ratio with Cloudy predictions using NIRSpec Zgas, ne, log U and C/O | R: Observed point consistent with the Cloudy region within errors | F: High ne, low Zgas, high U and low C/O can explain the ratio; low PDR covering fraction not constrained | **partially**

## Reasoning

- Why this data: Provide a benchmark FIR characterization for an EoR galaxy with a direct-method metallicity  
  > "providing a timely, unique reference for future follow-up of EoR galaxies in the coming decade." (Introduction)
- Why this method: Fiducial Td extrapolated from a redshift-evolution model since the dust continuum is undetected  
  > "Because of the limited constraints due to lack of the detection in both ALMA Bands, we assume the single modified black body (MBB) for the FIR SED of ID4590." (3.5 FIR SED)
- Alternative: Two nearby objects or faint satellites rejected as the cause of the extended F444W structure  
  > "We thus conclude that this diffuse, extended structure in the F444W filter is hardly explained either by these two nearby objects or further faint satellites." (Morphology)
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N (4.0 and 4.5 sigma) limits size and morphology conclusions; [CII] size may be affected by noise  
  > "we cannot exclude the possibility that these best-fit sizes are affected by the noise fluctuation with the current S/N" (3.3 Sizes)
- Limitation (authors): Dust continuum not detected so FIR SED is poorly constrained  
  > "Because of the limited constraints due to lack of the detection in both ALMA Bands" (3.5 FIR SED)
- Caveat (inferred, ours): Detections are only ~4 sigma; [CII] offset and extent depend on the noise and on the spatial resolution of 1.3 arcsec
- Caveat (inferred, ours): Text baseline range (15-457 m) conflicts with Table 1 (15.1-629.3 m)
- Caveat (inferred, ours): Manifest lists project 2021.A.00022.S while the paper prints 2022.A.00022.S
- Caveat (inferred, ours): [OIII]88um/[OIII]5007 ratio depends on slit-loss and aperture corrections from NIRSpec that are not reproducible from this paper
- Caveat (inferred, ours): Dust temperature of 60 K is assumed, so LIR and Mdust limits vary by up to 1 dex

## Reproducibility

- Data public (paper): JWST NIRCam/MIRI reduced products are public via grizli; ALMA data availability not stated  
  > "we use publicly available reduced and calibrated imaging products via the `grizli` pipeline." (JWST)
- Products in archive: _not stated_
- Missing: Cloudy and PyNeb input details
- Missing: NIRSpec reduced spectrum and slit-loss corrected line fluxes
- Missing: Exact moment-0 channel ranges and apertures
- Missing: CIGALE priors and full parameter grid
- Missing: Lens model files
- Data volume (inferred): Two ALMA execution blocks (Band 5 and 7, 44 antennas, ~1.5-2 h each); raw data roughly 10-30 GB total; calibrated products a few GB
- Score (inferred): 3/5, ALMA imaging recipe is mostly given (CASA 6.4.1.12, tclean natural weighting, 20 km/s cubes) and numeric results are listed, but line-extraction apertures, Cloudy/PyNeb inputs and the NIRSpec-derived inputs come from other papers or are missing
- Rediscovery candidate: no, ALMA data public status is not stated in the paper, and key inputs (NIRSpec line fluxes, Cloudy setup) are not fully specified; detections are only ~4 sigma

## Links

- Method: (cite: casa2022) (CASA reduction software)
- Method: (cite: kepley2020) (automask algorithm used in tclean)
- Companion: (cite: nakajima2023) (NIRSpec line fluxes, Te, metallicity used as inputs)
- Companion: (cite: heintz2022c) (Independent NIRCam/NIRSpec analysis of the same galaxy; gas mass)
- Companion: (cite: isobe2023b) (C/O abundance)
- Companion: (cite: harikane2022b) (Glafic lens model)
- Companion: (cite: fujimoto2022b) (CIGALE fitting setup)
- Related: JWST ERO program ERO-2736 (SMACS0723)
- Related: HST RELICS (GO-14096)

## Checks

```json
{
 "quotes": 131,
 "quotes_ok": 131,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2022.A.00022.S"
 ],
 "obscore_codes_not_in_card": [
  "2021.A.00022.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 90,
  "rate": 0.818
 },
 "evidence_ok": true
}
```
