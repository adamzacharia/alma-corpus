# Gas and star formation from HD and dust emission in a strongly lensed galaxy

`2020MNRAS.498.4109J` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Jones, G. C. | arXiv: 2009.00674 | DOI: 10.1093/mnras/staa2689

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: Can HD(1-0) emission in the lensed z=5.656 galaxy SPT 0346-52 be used as a molecular gas tracer, and how do HD and dust-SED based gas masses constrain alpha_CO and the starburst nature of the source?  
  > "To test this, we search for emission from the fundamental rotational transition HD(J=1-0) from the energetic, strongly lensed galaxy SPT 0346-52." (Introduction); "This is used to find a limit on the $L'_{CO}$ conversion factor of $\rm\alpha_{CO}<5.8$ M$_{\odot}$(K km s$^{-1}$ pc$^2$)$^{-1}$." (abstract)
- Target **SPT-S J034640-5204.9 (SPT 0346-52)**: coordinates not stated (only the SPT-S J034640-5204.9 name)  
  > "SPT-S J034640-5204.9 (hereafter SPT 0346-52) is a strongly lensed dusty starforming galaxy (DSFG) at $z=5.656$" (Introduction); "$D_L$ is the luminosity distance ($1.70\times10^{27}$ m)" (3.1 Observations and Data Reduction); "We will assume ($\Omega_{\Lambda}$,$\Omega_m$,h)=(0.692,0.308,0.678) (cite: plan16) throughout." (Introduction); z/distance z = 5.656; D_L = 1.70e27 m; lensing magnification mu = 5.6  
  > "SPT-S J034640-5204.9 (hereafter SPT 0346-52) is a strongly lensed dusty starforming galaxy (DSFG) at $z=5.656$" (Introduction); "$D_L$ is the luminosity distance ($1.70\times10^{27}$ m)" (3.1 Observations and Data Reduction); "We will assume ($\Omega_{\Lambda}$,$\Omega_m$,h)=(0.692,0.308,0.678) (cite: plan16) throughout." (Introduction); distance from Planck 2016 cosmology (cite: plan16) assumed for D_L; origin of z not stated in this paper  
  > "SPT-S J034640-5204.9 (hereafter SPT 0346-52) is a strongly lensed dusty starforming galaxy (DSFG) at $z=5.656$" (Introduction); "$D_L$ is the luminosity distance ($1.70\times10^{27}$ m)" (3.1 Observations and Data Reduction); "We will assume ($\Omega_{\Lambda}$,$\Omega_m$,h)=(0.692,0.308,0.678) (cite: plan16) throughout." (Introduction)

## Data provenance

- ALMA projects: 2016.1.01313.S, 2015.1.01580.S, 2013.1.01231.S, 2016.1.00654.S
- bands: Band 8  
  > "Using band 8 of ALMA, we observed SPT 0346-52 from 24 October - 1 November, 2016, using 41-46 antennas." (2 Observations and Data Reduction)
- frequencies and spectral setup: Two sidebands, each two SPWs of 128 channels x 15.625 MHz; lower sideband 387.562-391.031 GHz, upper sideband 399.757-403.351 GHz (HD(1-0) at 401.891 GHz in upper)  
  > "Our frequency range was covered by two sidebands, each composed of two spectral windows (SPWs), made of 128 channels of width 15.625 MHz." (2 Observations and Data Reduction); "The lower sideband ($387.562-391.031$ GHz) was expected not to contain prominent emission or absorption lines" (2 Observations and Data Reduction); "falls in the upper sideband ($399.757-403.351$ GHz)." (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.19'' x 0.17'' at PA 57 deg (final continuum-subtracted cube)  
  > "Our final continuum subtracted cube has a synthesized beam of $0.19''\times0.17''$ at a position angle of $57^{\circ}$" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.25 mJy/beam per 15.625 MHz channel (cube); 0.11 mJy/beam (continuum image)  
  > "channels of width 15.625 MHz ($\sim12$ km s$^{-1}$), and an RMS noise level per channel of 0.25 mJy beam$^{-1}$." (2 Observations and Data Reduction); "resulting in a final RMS noise level in the cleaned image of $0.11$ mJy beam$^{-1}$." (2 Observations and Data Reduction)
- time on source: 6.4 hours on-source out of 12.9 hours total  
  > "Out of a total observation time of 12.9 hours, 6.4 hours were on-source." (2 Observations and Data Reduction)
- observing dates: 24 October - 1 November 2016; 41-46 antennas  
  > "Using band 8 of ALMA, we observed SPT 0346-52 from 24 October - 1 November, 2016, using 41-46 antennas." (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: HD J=1-0 (2674.986094 GHz (observed 401.891 GHz))
- Other facility **Herschel (PACS/SPIRE)**: Published far-infrared flux densities (rest 24-75 um) used in the SED fit  
  > "we choose to include all of the Herschel data ($\lambda_{rest}=24-75$ $\mu$m), which trace the peak of the dust emission." (4.1.2 Model Implementation)
- Other facility **HST, ACT, SPIRE and other instruments (literature continuum)**: Previously published continuum observations compiled into the SED (Table 1)  
  > "it has been observed in continuum emission by a host of instruments (e.g., HST, ACT, SPIRE). We compile these observations in Table [1](#tab:sed)." (4.1 SED Modeling)
- External data: Lensing magnification mu=5.6 applied to all flux densities  
  > "Each observed flux density was corrected for magnification by assuming a constant lensing magnification of $\mu=5.6$, based on the detailed modelling of $\lambda_{obs}=870\,\mu$m continuum emission (cite: spil16)." (4.1.2 Model Implementation) [from (cite: spil16)]
- External data: Source radius R_gal ~0.76 kpc from averaged source-plane effective radii  
  > "we average the source-plane $\lambda_{\rm obs}=$2.0 mm and 3.0 mm effective radii of (cite: apos19), resulting in $R_{gal}\sim0.76$ kpc." (4.1.1 Model Description) [from (cite: apos19)]
- External data: Dust absorption coefficient kappa_o = 0.04 m^2 kg^-1 at 250 GHz  
  > "we assume the dust absorption coefficient $\kappa_o=0.04$ m$^2$ kg$^{-1}$ at $\nu_o=250$ GHz (cite: beel06)." (4.1.1 Model Description) [from (cite: beel06)]
- External data: CO FWHM = 613+/-30 km/s used to set line-free channel exclusion and the assumed HD line width  
  > "based on FWHM$_{\rm CO}=613\pm30$ km s$^{-1}$ (cite: arav16)" (2 Observations and Data Reduction) [from (cite: arav16)]
- External data: Archival/published continuum flux densities used in the SED (Table 1 entries 1,3-11, 12; ALMA archive projects 2015.1.01580.S, 2013.1.01231.S, 2016.1.00654.S)  
  > "Includes previously published values, values from the ALMA archive, and new values from this paper." (Table 1 caption); "we use the ALMA-staff calibrated continuum images (i.e., no further calibration has been performed)." (4.1 SED Modeling) [from (cite: ma15; spil16; jone19; mars14; apos19; dong19; arav16; ma16) and ALMA archive projects as listed in Table 1]
- External data: Gas temperature T~60 K from CO LVG modelling, used for f_u in the HD mass  
  > "We assume a gas temperature of $T\sim60$ K, based on Large Velocity Gradient (LVG) modelling of CO(8-7) and CO(2-1) data (cite: dong19)." (4.2.1 HD-Based Estimate) [from (cite: dong19)]
- External data: Primordial D/H = (2.6+/-0.1)e-5  
  > "We also adopt the primordial value of D/H=$(2.6\pm0.1)\times10^{-5}$ ((cite: coc04; plan16; novo17))" (4.2.1 HD-Based Estimate) [from (cite: coc04; plan16; novo17)]
- External data: Assumed (HD/H2)/(D/H)=1  
  > "we assume that (HD/H$_2$)/(D/H)=1, based on observations of $z\sim2.5$ galaxies with high metallicity and HI column density (cite: lisz15)." (4.2.1 HD-Based Estimate) [from (cite: lisz15)]
- External data: L'CO(2-1)/L'CO(1-0)=0.85 and CO(2-1) flux of earlier work used for alpha_CO  
  > "We convert the CO(2-1) integrated flux density of (cite: arav16) to a CO(1-0) luminosity using $L'_{CO(2-1)}/L'_{CO(1-0)}=0.85$ (appropriate for starburst galaxies) from table 2 of (cite: cari13)" (4.2.1 HD-Based Estimate) [from (cite: arav16; cari13)]

## Processing

### Calibration

- pipeline or manual: Originally calibrated by ALMA staff; authors recalibrated flagging only 3 edge channels per SPW instead of the default 10  
  > "The data were originally calibrated by ALMA staff, but excessive flagging of edge channels resulted in a gap in the resulting frequency coverage." (2 Observations and Data Reduction); "we recalibrated the data, flagging only 3 channels at each edge of the spectral windows, rather than the default of 10 channels." (2 Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: For archival continuum measurements in the SED, ALMA-staff calibrated continuum images used with no further calibration  
  > "For each of these measurements, we use the ALMA-staff calibrated continuum images (i.e., no further calibration has been performed)." (4.1 SED Modeling)
- flux calibrator: J0519-4546 (gain J0253-5441, bandpass J0522-3627)  
  > "Our complex gain, bandpass, and flux calibrators were J0253-5441, J0522-3627, and J0519-4546, respectively." (2 Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA TCLEAN  
  > "we first create full (i.e., line and continuum) data cubes using the CASA task TCLEAN, natural weighting, and a clean threshold of $3\sigma$" (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we first create full (i.e., line and continuum) data cubes using the CASA task TCLEAN, natural weighting, and a clean threshold of $3\sigma$" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: clean threshold 3 sigma, sigma = RMS per channel of the dirty image  
  > "a clean threshold of $3\sigma$, where $\sigma$ is the RMS noise level per channel of the dirty image." (2 Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: IMCONTSUB 1st-order polynomial on the upper-sideband cube, excluding +/-250 km/s around HD(1-0); UVCONTSUB and full-range IMCONTSUB rejected  
  > "we re-examine the IMCONTSUB approach (both 0th and 1st-order) for the upper sideband, but only excluding $\pm250$ km s$^{-1}$ on either side of the HD(1-0) line." (2 Observations and Data Reduction); "The 1st order approach returns a flatter spectrum, so we proceed with this continuum-subtracted cube." (2 Observations and Data Reduction)
- line free channels: Continuum image uses all line- and atmospheric-feature-free channels of both sidebands (exact ranges not given); UVCONTSUB test avoided absorption near 400.0, 401.3, 402.4 GHz and 400.888-402.899 GHz  
  > "A continuum image was created by applying TCLEAN to all line- and atmospheric feature-free channels of both sidebands" (2 Observations and Data Reduction); "resulting in theoretical line channels of $400.888-402.899$ GHz." (2 Observations and Data Reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Native 15.625 MHz channels kept after testing 2-5 channel averaging  
  > "We explore both the native channel width and 2, 3, 4, and 5-channel averaging. None of these data cubes shows an obvious HD(1-0) signal, so we proceed with the native channel width." (2 Observations and Data Reduction)
- final beam: 0.19'' x 0.17'' at PA 57 deg  
  > "Our final continuum subtracted cube has a synthesized beam of $0.19''\times0.17''$ at a position angle of $57^{\circ}$" (2 Observations and Data Reduction)
- final rms: 0.25 mJy/beam per channel (cube); 0.11 mJy/beam (continuum)  
  > "an RMS noise level per channel of 0.25 mJy beam$^{-1}$." (2 Observations and Data Reduction); "resulting in a final RMS noise level in the cleaned image of $0.11$ mJy beam$^{-1}$." (2 Observations and Data Reduction)

### Inherited from earlier work

- HD(1-0) flux to H2 mass relation (equation 2)  
  > "We begin by using our HD(1-0) flux density and equation 2 of (cite: berg13)" (4.2.1 HD-Based Estimate) [from (cite: berg13)]
- CMB correction on dust temperature and background  
  > "we include the effects of the cosmic microwave background (CMB) on the observed dust continuum, as outlined in (cite: dacu13) and implemented in (cite: carn19)." (4.1.1 Model Description) [from (cite: dacu13); (cite: carn19)]
- Modified blackbody (greybody) form  
  > "We choose a modified blackbody (also known as a greybody; e.g., (cite: grev12))" (4.1.1 Model Description) [from (cite: grev12)]
- SFR from FIR luminosity scaling relation  
  > "Using the scaling relation from (cite: kenn98A), this corresponds to a SFR=$3800\pm100$ M$_{\odot}$ year$^{-1}$." (4.1.3 Model Results) [from (cite: kenn98A)]
- Scoville et al. continuum gas-mass estimator (equation A14)  
  > "equation A14 of (cite: scov16) may be applied to our four continuum flux density values that satisfy their $\lambda_{\rm rest}>250$ $\mu$m criterion" (4.2.2 Continuum-Based Estimates) [from (cite: scov16)]
- Standard gas-to-dust ratio prescription  
  > "a standard gas to dust (GDR) ratio of $\rm \delta_{GDR}=M_{H_2}/M_{dust}=100\times10^{Z-Z_{\odot}}$ (cite: drai07)" (4.2.2 Continuum-Based Estimates) [from (cite: drai07)]

### Not stated but needed to reproduce (our reading)

- CASA version and the exact recalibration script / flagging of atmospheric-line channels
- Image cell size, image size, niter and mask for the TCLEAN cubes and continuum image
- Exact channel ranges used for the continuum image and the upper-sideband continuum fit
- How the 2 sigma continuum contour mask was built and how the spectrum (and 2.15 mJy RMS at the HD frequency) was extracted
- Which images and apertures were used to measure each archival ALMA flux density in Table 1 (and which projects map to which points)
- Flux uncertainty treatment (absolute calibration error) in the SED likelihood and MultiNest settings (live points, tolerance, likelihood form)
- Partition function Q(T) source and the IMF/calibration behind the SFR scaling
- Luminosity-distance calculation details and which dust-mass value (10^8.92 vs 10^9.38) enters the gas-to-dust estimate
- Target coordinates and the source of the redshift z=5.656

## Analysis recipe

1. **Image continuum and measure flux density**: TCLEAN continuum image from line-free channels (natural weighting, MFS, 3 sigma threshold); total flux integrated inside the 2 sigma contour; 2D Gaussian fits to the three components  
  > "A continuum image was created by applying TCLEAN to all line- and atmospheric feature-free channels of both sidebands" (2 Observations and Data Reduction); "Using the $2\sigma$ contour as a spatial mask, we determine the total $\lambda_{\rm rest}\sim114\,\mu$m continuum flux density of this source to be $171.5\pm1.0$ mJy." (3.1 Continuum)
   - software: CASA tclean
   - parameter: natural weighting, multi-frequency synthesis, 3 sigma clean threshold  
  > "natural weighting, multi-frequency synthesis, and a clean threshold of $3\sigma$" (2 Observations and Data Reduction)
   - assumption: Observed image-plane (not de-lensed) values reported  
  > "Note that in this section, we will state the observed (i.e., image-plane) continuum parameters, rather than the de-lensed (or source-plane) values." (3.1 Continuum)
   - fitting: Two-dimensional Gaussian fits to the northern, southeastern and southwestern components  
  > "A two-dimensional Gaussian fit to the northern component in the continuum image returns a deconvolved size of" (3.1 Continuum)
   - validation: _not stated_
2. **Continuum-subtract the cube**: Tested UVCONTSUB (1st-order, visibilities) and IMCONTSUB on both sidebands; adopted 1st-order IMCONTSUB on the upper sideband excluding +/-250 km/s around HD(1-0)  
  > "we used the CASA task UVCONTSUB to fit and subtract a first-order polynomial continuum model directly to the visibilities of both sidebands" (2 Observations and Data Reduction); "we re-examine the IMCONTSUB approach (both 0th and 1st-order) for the upper sideband, but only excluding $\pm250$ km s$^{-1}$ on either side of the HD(1-0) line." (2 Observations and Data Reduction)
   - software: CASA uvcontsub, CASA imcontsub
   - parameter: Initial conservative line exclusion: HD frequency +/-750 km/s (400.888-402.899 GHz) based on CO FWHM  
  > "we adopted a conservative line channel range of the expected HD frequency $\pm750$ km s$^{-1}$" (2 Observations and Data Reduction)
   - assumption: HD line width unknown, so conservative channel exclusion used  
  > "Since the linewidth of HD is unknown, we adopted a conservative line channel range" (2 Observations and Data Reduction)
   - fitting: 1st-order polynomial fit per image-space spectrum  
  > "The 1st order approach returns a flatter spectrum, so we proceed with this continuum-subtracted cube." (2 Observations and Data Reduction)
   - validation: Visual inspection: UVCONTSUB left obvious continuum under-subtraction and was rejected  
  > "This resulted in an obvious under-subtraction of the continuum, so this continuum subtraction method was disregarded." (2 Observations and Data Reduction)
3. **Search for HD(1-0) and derive an upper limit on its flux**: Channel-by-channel cube search, immoments collapse over -350 to 350 km/s, and spectrum extraction from the 2 sigma continuum mask; undetected, so a 2 sigma upper limit from a Gaussian of FWHM 613 km/s on the RMS at the expected frequency  
  > "Since no definite emission is detected through inspecting the data cube, collapsing a wide channel range, or extracting a spectrum from a large area, we conclude that HD(1-0) is undetected in these observations." (3.2 HD(J=1-0) Emission); "Next, we assume a wide Gaussian line profile (FWHM$_{\rm HD}=613$ km s$^{-1}\sim0.8$ GHz; (cite: arav16)) with an amplitude limit of $<2\sigma$" (3.2 HD(J=1-0) Emission)
   - software: CASA immoments
   - parameter: RMS ~2.15 mJy at the expected frequency; amplitude limit 2 sigma; FWHM 613 km/s  
  > "finding an RMS noise level of $\sim2.15$ mJy at the expected frequency." (3.2 HD(J=1-0) Emission)
   - assumption: HD emission has the same spatial distribution as the FIR continuum and the CO line width  
  > "Assuming the same spatial distribution as the FIR continuum emission, we extract a spectrum from our continuum-subtracted cube" (3.2 HD(J=1-0) Emission)
   - fitting: _not stated_
   - validation: Four tentative features examined and dismissed as noise (Appendix)  
  > "By searching the cube, two tentative line features are detected, but they are believed to be noise." (3.2 HD(J=1-0) Emission)
4. **Fit the dust SED with a modified blackbody**: Single-temperature optically-thick modified blackbody with CMB correction, fit to magnification-corrected flux densities (Herschel 24-75 um rest through ALMA/ACT/SPT to rest 451 um; 8 mm point excluded) with 3 free parameters  
  > "it is possible to fit the full FIR dust SED with only three free parameters: the dust emissivity spectral index ($\beta$), dust temperature ($T_{dust}$), and dust mass ($M_{dust}$)." (4.1.1 Model Description); "we do not include the low-frequency $\lambda_{\rm obs}=$8 mm data point." (4.1.2 Model Implementation)
   - software: MultiNest, PyMultiNest
   - parameter: kappa_o = 0.04 m^2 kg^-1 at 250 GHz; R_gal ~0.76 kpc; mu = 5.6; T_o = 2.73 K  
  > "where we assume the dust absorption coefficient $\kappa_o=0.04$ m$^2$ kg$^{-1}$ at $\nu_o=250$ GHz (cite: beel06)." (4.1.1 Model Description)
   - assumption: Constant magnification mu=5.6, circular source of constant radius, luminosity-weighted single dust temperature, no MIR power law, synchrotron or free-free  
  > "Our model assumes a circular source with a constant radius, luminosity-weighted dust temperature, lensing magnification, and set of dust emission properties" (4.1.4 Discussion of Uncertainties); "This model also assumes no contributions from separate MIR" (4.1.4 Discussion of Uncertainties)
   - fitting: MultiNest nested sampling with uniform priors log10(Mdust/Msun)=8-10, beta=1-3, Tdust=10-200 K; uncertainties are posterior standard deviations  
  > "We assume uniform priors for each variable, with log$_{10}$(M$_{\rm dust}/$M$_{\odot})=8-10$, $\beta=1-3$, and T$_{\rm dust}=10-200$ K." (4.1.2 Model Implementation); "are simply the standard deviations of the posterior deviations for each parameter as found by MultiNest" (4.1.4 Discussion of Uncertainties)
   - validation: Refits with beta fixed to 2 and Tdust fixed to 52 K, and an optically-thin fit, compared via Bayesian evidence; a posteriori optical-depth check  
  > "we fixed each parameter to their literature value, and fit a model using only two or one free variables." (4.1.3 Model Results); "This *a posteriori* calculation verifies that the optically thin assumption cannot be applied to this source." (4.1.4 Discussion of Uncertainties)
5. **Derive FIR luminosity and star formation rate**: Integrate the best-fit model over 42.5-122.5 um and convert with the Kennicutt (1998) scaling  
  > "This model exhibits a FIR luminosity (i.e., 42.5-122.5 $\mu$m) of L$_{\rm FIR}=(2.2\pm0.1)\times10^{13}\,$L$_{\odot}$." (4.1.3 Model Results)
   - fitting: _not stated_
   - validation: Compared with CIGALE and IR-conversion SFRs from earlier work (<2 sigma lower)  
  > "Our value of SFR is only slightly (i.e., $<2\sigma$) lower than these estimates." (4.1.3 Model Results)
6. **HD-based molecular gas mass and alpha_CO limit**: Convert the HD(1-0) flux limit to M_H2 using N_HD, A10, f_u(T) and primordial D/H; divide by L'CO(1-0) derived from the literature CO(2-1) flux to get alpha_CO  
  > "We begin by using our HD(1-0) flux density and equation 2 of (cite: berg13)" (4.2.1 HD-Based Estimate); "This gas mass estimate may be used to place a constraint on the CO luminosity—H$_2$ mass conversion ratio $\alpha_{CO}=M_{H_2}/L'_{CO}$." (4.2.1 HD-Based Estimate)
   - parameter: T~60 K; D/H=(2.6+/-0.1)e-5; A10=5.44e-8 s^-1; D_L=1.70e27 m; F_L<3.8e-20 W m^-2  
  > "$A_{10}$ is the Einstein coefficient for spontaneous emission ($5.44\times10^{-8}$ s$^{-1}$; (cite: mull05))" (4.2.1 HD-Based Estimate)
   - assumption: (HD/H2)/(D/H)=1; near-primordial D/H at z=5.656; HD kinetic temperature equals CO temperature; only H2 mass (no He or heavy elements)  
  > "Next, we assume that (HD/H$_2$)/(D/H)=1" (4.2.1 HD-Based Estimate); "The above values assume that the kinetic temperature of HD is equal to that of CO, as derived by (cite: dong19)." (4.2.1 HD-Based Estimate)
   - fitting: _not stated_
   - validation: Compared with CO(2-1)-based gas mass; alternative gas temperatures (dust temperature 78.6 K, mass-weighted 25 K) tested  
  > "This is in agreement with the CO(2-1) based gas mass of (cite: arav16)" (4.2.1 HD-Based Estimate)
7. **Continuum-based gas masses and alpha_CO**: Gas-to-dust ratio applied to the fitted dust mass (sub-solar metallicity limit) and the Scoville et al. (2016) long-wavelength estimator applied to four flux densities; alpha_CO from each M_H2  
  > "Since no metallicity information is available, we assume sub-solar metallicity for this early galaxy, resulting in M$_{H_2,GDR}<2.4\times10^{11}$ M$_{\odot}$." (4.2.2 Continuum-Based Estimates); "Using our derived dust temperature, this yields a magnification-corrected average value of $M_{H_2}=(5.1\pm0.3)\times10^{11}$ M$_{\odot}$." (4.2.2 Continuum-Based Estimates)
   - parameter: Scoville estimator applied to the four points with lambda_rest>250 um (lambda_obs>1664 um); GDR = 100 x 10^(Z-Zsun)  
  > "equation A14 of (cite: scov16) may be applied to our four continuum flux density values that satisfy their $\lambda_{\rm rest}>250$ $\mu$m criterion" (4.2.2 Continuum-Based Estimates)
   - assumption: Sub-solar metallicity assumed (no metallicity information); Scoville calibration derived from high-metallicity z~0-3 galaxies  
  > "It should be noted that this equation was derived using a calibration sample of $z\sim0-3$ galaxies with high stellar masses, and thus high metallicities." (4.2.2 Continuum-Based Estimates)
   - fitting: _not stated_
   - validation: Estimates compared with each other and with MW and starburst alpha_CO values  
  > "Both the (cite: scov16) and GDR approaches result in values between the Milky Way (4.6) and starburst (0.8) limits" (4.2.2 Continuum-Based Estimates)

## Software

- **CASA** : tclean imaging of cubes and continuum, uvcontsub/imcontsub continuum subtraction, immoments  
  > "we first create full (i.e., line and continuum) data cubes using the CASA task TCLEAN" (2 Observations and Data Reduction); "we used the CASA task UVCONTSUB to fit and subtract a first-order polynomial continuum model directly to the visibilities of both sidebands" (2 Observations and Data Reduction)
- **MultiNest** : Bayesian nested-sampling fit of the modified blackbody SED  
  > "Models were fit to the SED using the Bayesian inference code MultiNest (cite: fero08) and its python wrapper (PyMultiNest; (cite: buch14))." (4.1.2 Model Implementation)
- **PyMultiNest** : Python wrapper for MultiNest  
  > "and its python wrapper (PyMultiNest; (cite: buch14))." (4.1.2 Model Implementation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total continuum flux density (rest ~114 um, Band 8) | 171.5 | 1.0 | mJy | 1 | The total continuum flux density is $171.5\pm1.0$ mJy. |
| Maximum continuum significance | ~185 | not stated | sigma | 1 | The continuum is well detected, with a maximum significance of $\sim185\sigma$. |
| Sum of integrated flux densities of the three Gaussian components | 147 | 5 | mJy | 1 | This value is greater than the sum of each integrated flux density ($147\pm5$ mJy) |
| HD(1-0) integrated intensity upper limit | <3.8e-20 | not stated | W m^-2 | 3 | resulting in a conservative upper limit on the integrated intensity of HD(1-0) of $F_L<3.8\times10^{-20}$ W m$^{-2}$. |
| RMS noise at the expected HD(1-0) frequency in the extracted spectrum | ~2.15 | not stated | mJy | 3 | finding an RMS noise level of $\sim2.15$ mJy at the expected frequency. |
| Molecular gas mass from HD(1-0) (T~60 K), upper limit | <6.4e11 (x 5.6/mu) | not stated | Msun | 6 | While no HD(1-0) emission is detected, we are able to place an upper limit on the gas mass of $\rm M_{H_2}<6.4\times10^{11}\,M_{\odot}$. |
| alpha_CO limit from HD | <5.8 | not stated | Msun (K km/s pc^2)^-1 | 6 | This results in a limit of $\alpha_{CO}<5.8$. |
| HD gas-mass limit if Tgas = Tdust = 78.6 K | <4.4e11 | not stated | Msun | 6 | resulting in a slightly less conservative upper limit on the gas mass: $\rm M_{H_2}<4.4\times10^{11}\,M_{\odot}$. |
| HD gas-mass limit if Tgas = 25 K (mass-weighted dust temperature) | <9.9e12 | not stated | Msun | 6 | then we find a more conservative gas mass limit of $\rm M_{H_2}<9.9\times10^{12}\,M_{\odot}$. |
| Dust temperature (best fit) | 78.6 | 0.5 | K | 4 | Fitting a modified blackbody model to our combined dataset yields best-fit values of T$_d=78.6\pm0.5$ K, $\beta=1.81\pm0.03$, and log($M_{dust}/M_{\odot})=8.92\pm0.02$. |
| Dust emissivity spectral index beta | 1.81 | 0.03 | dimensionless | 4 | Fitting a modified blackbody model to our combined dataset yields best-fit values of T$_d=78.6\pm0.5$ K, $\beta=1.81\pm0.03$, and log($M_{dust}/M_{\odot})=8.92\pm0.02$. |
| log10 dust mass | 8.92 | 0.02 | log10(Msun) | 4 | Fitting a modified blackbody model to our combined dataset yields best-fit values of T$_d=78.6\pm0.5$ K, $\beta=1.81\pm0.03$, and log($M_{dust}/M_{\odot})=8.92\pm0.02$. |
| FIR luminosity (42.5-122.5 um) | 2.2e13 | 0.1e13 | Lsun | 5 | This model exhibits a FIR luminosity (i.e., 42.5-122.5 $\mu$m) of L$_{\rm FIR}=(2.2\pm0.1)\times10^{13}\,$L$_{\odot}$. |
| Star formation rate | 3800 | 100 | Msun/yr | 5 | Using the scaling relation from (cite: kenn98A), this corresponds to a SFR=$3800\pm100$ M$_{\odot}$ year$^{-1}$. |
| Optical depth range across the SED | 0.22 at lambda_obs=3.0 mm to 43.99 at lambda_obs=160 um; tau~1 at ~200 um | not stated | dimensionless | 4 | We find that $\tau_{\nu}$ ranges from the marginally optically thin regime (0.22 at $\lambda_{obs}=3.0$ mm) to optically thick (43.99 at $\lambda_{obs}=160$ $\mu$m) |
| Gas mass from gas-to-dust ratio (sub-solar metallicity), upper limit | <2.4e11 | not stated | Msun | 7 | Since no metallicity information is available, we assume sub-solar metallicity for this early galaxy, resulting in M$_{H_2,GDR}<2.4\times10^{11}$ M$_{\odot}$. |
| Gas mass from Scoville et al. 2016 estimator | 5.1e11 | 0.3e11 | Msun | 7 | this yields a magnification-corrected average value of $M_{H_2}=(5.1\pm0.3)\times10^{11}$ M$_{\odot}$. |
| alpha_CO from GDR and Scoville methods | <2.2 (GDR); 4.0 (Scoville) | 0.4 (Scoville) | Msun (K km/s pc^2)^-1 | 7 | resulting in $<5.8$, $<2.2$, and $4.0\pm0.4$ for the HD, GDR, and (cite: scov16) approaches, respectively. |

## Qualitative findings

- No HD(1-0) emission detected; four tentative features judged to be noise  
  > "While there are no significant detections of HD(J=1-0)112.2 $\mu$m line emission in these data" (Appendix Tentative Detections)
- Dust is not optically thin over the examined frequencies, so an optically-thin fit is nonphysical  
  > "we find that our source is not optically thin over the examined frequency range (see Section [4.1.4](#DoU)), so this fit is nonphysical." (4.1.3 Model Results)
- Fitted beta is lower and Tdust higher than earlier work assuming beta=2  
  > "this discrepancy in $T_{\rm dust}$ is due to their assumption of $\beta\equiv2.0$." (4.1.3 Model Results)
- Surface density estimates place the source in the starburst region of a Kennicutt-Schmidt diagram  
  > "This places SPT 0346-52 squarely in the starburst region of a Kennicutt-Schmidt diagram" (Conclusions)

## Claim tuples

- H: HD(1-0) can trace the molecular gas of the lensed z=5.656 galaxy SPT 0346-52 | E: ALMA Band 8 observation of HD(1-0) at 401.891 GHz with continuum subtraction and cube, moment and spectral searches | R: No HD(1-0) detected; F_L<3.8e-20 W m^-2 gives M_H2<6.4e11 Msun and alpha_CO<5.8 | F: HD is undetected; upper limit is consistent with the CO(2-1) gas mass | **supported**
- H: A single-temperature optically-thick modified blackbody describes the full FIR SED and gives dust properties and SFR | E: MultiNest fit to compiled Herschel, ALMA, ACT and SPT flux densities including the new Band 8 point | R: Tdust=78.6+/-0.5 K, beta=1.81+/-0.03, log Mdust=8.92+/-0.02, SFR=3800+/-100 Msun/yr | F: Source is a heavily starbursting, dusty galaxy with higher Tdust and lower beta than earlier assumptions | **supported**
- H: Continuum-based methods give gas masses and alpha_CO consistent with or between MW and starburst values | E: Gas-to-dust ratio applied to dust mass and the Scoville et al. 2016 estimator on four flux densities | R: M_H2<2.4e11 Msun (alpha_CO<2.2) and 5.1+/-0.3e11 Msun (alpha_CO=4.0+/-0.4) | F: alpha_CO lies between the starburst (0.8) and MW-like (4.6) standard values, though the estimates are disparate | **partially**
- H: The HD non-detection constrains gas in an extended source | E: Searches assuming compact and continuum-extended emission | R: Observations were designed for compact emission and the line lies in a region of variable atmospheric transmission | F: Non-detection may be partly due to extended emission; higher-z sources (z>7.5) may suit HD(1-0) better | **partially**

## Reasoning

- Why this data: High-redshift galaxies put the low-J HD transition in reach of sensitive ground-based telescopes such as ALMA  
  > "High-redshift galaxies allow us to search for the lowest J transitions of HD using sensitive ground based telescopes, such as ALMA." (Introduction)
- Why this method: HD abundance relative to H2 is expected to be constant, giving a direct H2 mass unlike CO  
  > "Unlike CO, HD is expected to have a constant abundance relative to H$_2$ throughout the dense molecular material" (Introduction)
- Alternative: UVCONTSUB visibility-space continuum subtraction rejected for obvious continuum under-subtraction  
  > "This resulted in an obvious under-subtraction of the continuum, so this continuum subtraction method was disregarded." (2 Observations and Data Reduction)
- Alternative: Optically-thin dust fit rejected as nonphysical  
  > "so this fit is nonphysical." (4.1.3 Model Results)
- Alternative: Lower sideband judged unsuitable for continuum fitting  
  > "The above tests reveal that the lower sideband is unsuitable for continuum fitting" (2 Observations and Data Reduction)
- How they decided it was enough: Concluded non-detection after cube inspection, wide channel collapse and a large-area spectrum all showed no definite emission  
  > "Since no definite emission is detected through inspecting the data cube, collapsing a wide channel range, or extracting a spectrum from a large area, we conclude that HD(1-0) is undetected in these observations." (3.2 HD(J=1-0) Emission)
- Limitation (authors): Observations designed for compact emission; atmospheric lines coincide with HD and give nonconstant noise  
  > "In addition, the expected line is coincident with a series of atmospheric transmission lines, resulting in a nonconstant noise level." (Conclusions)
- Limitation (authors): Fit uncertainties are posterior standard deviations only and do not include model-assumption uncertainty  
  > "are simply the standard deviations of the posterior deviations for each parameter as found by MultiNest, and thus do not account for the additional sources of uncertainty discussed here." (4.1.4 Discussion of Uncertainties)
- Limitation (authors): Model assumptions (uniform source, constant magnification, single temperature) affect physicality of best-fit values  
  > "Therefore, we note that these assumptions have a detrimental effect on the physicality of our best-fit values." (4.1.4 Discussion of Uncertainties)
- Caveat (inferred, ours): The text uses a dust mass of 10^9.38 Msun for the gas-to-dust estimate while the best fit is 10^8.92; the optically-thin fit gives about 10^9.36, so the input may be inconsistent
- Caveat (inferred, ours): The HD upper limit depends on an assumed CO line width, T=60 K and (HD/H2)/(D/H)=1, none tested for a lensed, differentially magnified source
- Caveat (inferred, ours): Constant mu=5.6 applied across all wavelengths although magnification varies with wavelength
- Caveat (inferred, ours): SED fit includes mixed-resolution flux densities from different archival projects with undocumented measurement apertures
- Caveat (inferred, ours): Tentative features are dismissed by eye without a quantified false-alarm analysis

## Reproducibility

- Data public (paper): Data available from the ALMA archive under 2016.1.01313.S (Band 8)  
  > "The data analyzed in this work are available from the ALMA data archive (https://almascience.nrao.edu/asax/) under project code 2016.1.01313.S (Band 8)." (Data Availability)
- Products in archive: _not stated_
- Missing: CASA version and recalibration script
- Missing: Cell size, image size, niter and masks for tclean
- Missing: Exact line-free channel lists for the continuum image
- Missing: Measurement method for archival ALMA flux densities in Table 1
- Missing: MultiNest configuration and flux error treatment
- Data volume (inferred): Band 8 12.9 h execution with 41-46 antennas and four 128-channel SPWs: roughly 10-30 GB for the project MS, plus archival continuum images from three other projects
- Score (inferred): 3/5, Public ALMA data, an explicit continuum-subtraction recipe, priors and numeric results, but imaging parameters, recalibration details, CASA version and archival flux measurement methods are missing.
- Rediscovery candidate: yes, Data are public and the upper limit, SED fit (priors, formula, table of fluxes) and gas-mass numbers are explicit; some tclean parameters must be chosen by the reproducer.

## Links

- Method: (cite: berg13) (HD(1-0) flux to H2 mass equation)
- Method: (cite: scov16) (continuum gas-mass estimator)
- Method: (cite: dacu13) (CMB correction on dust emission)
- Companion: (cite: arav16) (CO(2-1) gas mass, line width and L'CO used for comparison)
- Companion: (cite: apos19) (continuum data and source-plane sizes)
- Companion: (cite: dong19) (CO LVG modelling for the gas temperature)
- Companion: (cite: spil16) (lens model and magnification)
- Related: SPT-S survey (South Pole Telescope)

## Checks

```json
{
 "quotes": 137,
 "quotes_ok": 137,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.01580.S",
  "2013.1.01231.S",
  "2016.1.00654.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 106,
  "stated": 83,
  "rate": 0.783
 },
 "evidence_ok": true
}
```
