# WISDOM project - XXVIII. Molecular gas measurement of the supermassive black hole mass of the galaxy NGC 1387

`2026MNRAS.548ag546D` | Monthly Notices of the Royal Astronomical Society 2026 | first author: Dominiak, Pandora | arXiv: 2603.12945 | DOI: 10.1093/mnras/stag546

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Measure the supermassive black hole (SMBH) mass and stellar mass-to-light ratio of the early-type galaxy NGC 1387 using ALMA $^{12}$CO(2–1) molecular gas kinematics.  
  > "Here we present high angular resolution ($0.12$ arcsec or $\approx11$ pc) Atacama Large Millimeter/submillimeter Array observations of the $^{12}$CO(2–1) line emission of the early-type galaxy NGC 1387." (Abstract); "In this work, we apply the CO dynamical modelling method to estimate the mass of the SMBH at the centre of the galaxy NGC 1387, the data for which were obtained as a part of the mm-Wave Interferometric Survey of Dark Object Masses (WISDOM) project." (Introduction)
- Target **NGC 1387**: coordinates 03h36m57.06s, -35d30m23.9s (J2000.0)  
  > "NGC 1387 is a barred lenticular (SB0) galaxy located at $03^{\text{h}}36^{\text{m}}57\rlap{.}^\text{s}06$, $-35\degree30\ensuremath{'}23.9\ensuremath{''}$ (J2000.0) within the Fornax Cluster." (NGC 1387); "Throughout this paper we adopt a distance of $19.3\pm0.8$ Mpc, calculated using surface brightness fluctuations (cite: Blakeslee_2009)." (NGC 1387); z/distance 19.3 ± 0.8 Mpc  
  > "NGC 1387 is a barred lenticular (SB0) galaxy located at $03^{\text{h}}36^{\text{m}}57\rlap{.}^\text{s}06$, $-35\degree30\ensuremath{'}23.9\ensuremath{''}$ (J2000.0) within the Fornax Cluster." (NGC 1387); "Throughout this paper we adopt a distance of $19.3\pm0.8$ Mpc, calculated using surface brightness fluctuations (cite: Blakeslee_2009)." (NGC 1387); distance from Blakeslee_2009 (surface brightness fluctuations)  
  > "NGC 1387 is a barred lenticular (SB0) galaxy located at $03^{\text{h}}36^{\text{m}}57\rlap{.}^\text{s}06$, $-35\degree30\ensuremath{'}23.9\ensuremath{''}$ (J2000.0) within the Fornax Cluster." (NGC 1387); "Throughout this paper we adopt a distance of $19.3\pm0.8$ Mpc, calculated using surface brightness fluctuations (cite: Blakeslee_2009)." (NGC 1387)

## Data provenance

- ALMA projects: 2016.1.00437.S, 2016.2.00053.S
- bands: Band 6  
  > "The $^{12}$CO(2–1) emission line of NGC 1387 was observed with ALMA in band 6 using both the $12$-m array and the $7$-m Atacama Compact Array (ACA) as a part of projects 2016.1.00437.S (PI: Davis) and 2016.2.00053.S (PI: Liu), respectively." (ALMA Observations)
- frequencies and spectral setup: 4 spectral windows per track. Line spw: 12-m: 1.875 GHz (3840 channels, ~488 kHz / ~0.64 km s^-1); ACA: 2.0 GHz (2048 channels, ~977 kHz / ~1.27 km s^-1). 3 continuum spws: 2.0 GHz (128 channels, ~16 MHz / ~20 km s^-1).  
  > "For the three $12$-m array tracks, this spectral window had a bandwidth of $1.875$ GHz ($\approx2440$ km s$^{-1}$) subdivided into $3840$ channels of width $\approx488$ kHz ($\approx0.64$ km s$^{-1}$)." (ALMA Observations); "For the ACA track this spectral window had a bandwidth of $2.0$ GHz ($\approx 2600$ km s$^{-1}$) subdivided into $2048$ channels of width $\approx977$ kHz ($\approx1.27$ km s$^{-1}$)." (ALMA Observations); "The remaining spectral windows for both the $12$-m array and the ACA tracks had a bandwidth of $2.0$ GHz ($\approx2600$ km s$^{-1}$) subdivided into $128$ channels of width $\approx16$ MHz ($\approx20$ km s$^{-1}$)." (ALMA Observations)
- continuum bandwidth: 3 continuum spectral windows of 2.0 GHz each plus line-free channels of the line spectral window, central frequency 239.4 GHz (1.25 mm)  
  > "The remaining spectral windows for both the $12$-m array and the ACA tracks had a bandwidth of $2.0$ GHz ($\approx2600$ km s$^{-1}$) subdivided into $128$ channels of width $\approx16$ MHz ($\approx20$ km s$^{-1}$)." (ALMA Observations); "The line-free channels of the line spectral windows as well as the continuum spectral windows were used, resulting in a central frequency of $239.4$ GHz ($1.25$ mm)." (Continuum emission)
- arrays: 12-m array and 7-m Atacama Compact Array (ACA)  
  > "The $^{12}$CO(2–1) emission line of NGC 1387 was observed with ALMA in band 6 using both the $12$-m array and the $7$-m Atacama Compact Array (ACA) as a part of projects 2016.1.00437.S (PI: Davis) and 2016.2.00053.S (PI: Liu), respectively." (ALMA Observations)
- configurations: _not stated_
- baselines: 12-m array: 15 m to 7.5 km; ACA: 9 to 45 m  
  > "The baselines range from $15$ m to $7.5$ km, yielding a maximum recoverable scale (MRS) of $5.9$ arcsec ($\approx0.6$ kpc)." (ALMA Observations); "The baselines range from $9$ to $45$ m, yielding a MRS of $28.4$ arcsec ($\approx2.7$ kpc)." (ALMA Observations)
- angular resolution: Continuum: 0.09 x 0.06 arcsec (8 x 6 pc); High-res CO cube: 0.13 x 0.10 arcsec (12 x 10 pc); Low-res CO cube: 0.42 x 0.35 arcsec (39 x 33 pc)  
  > "| Synthesised beam (arcsec) | $0.09\times0.06$ |" (Table 1); "The resulting data cube has a synthesised beam of $0.13$ arcsec $\times$ $0.10$ arcsec ($\approx12\times10$ pc$^2$) with a RMS noise of $0.65$ mJy beam$^{-1}$ channel$^{-1}$." (Line emission); "The resulting data cube has a synthesised beam of $0.42$ arcsec $\times$ $0.35$ arcsec ($\approx39\times33$ pc$^2$) with a RMS noise of $0.80$ mJy beam$^{-1}$ channel$^{-1}$, and its properties are also summarised in Table [2](#tab:CO)." (Low-resolution cube and inclination prior)
- max recoverable scale: 12-m array: 5.9 arcsec (~0.6 kpc); ACA: 28.4 arcsec (~2.7 kpc)  
  > "The baselines range from $15$ m to $7.5$ km, yielding a maximum recoverable scale (MRS) of $5.9$ arcsec ($\approx0.6$ kpc)." (ALMA Observations); "The baselines range from $9$ to $45$ m, yielding a MRS of $28.4$ arcsec ($\approx2.7$ kpc)." (ALMA Observations)
- sensitivity: Continuum: 0.03 mJy beam^-1; High-res CO cube: 0.65 mJy beam^-1 channel^-1 (10 km s^-1 channels); Low-res CO cube: 0.80 mJy beam^-1 channel^-1 (10 km s^-1 channels)  
  > "We adopted the multi-frequency synthesis mode, Briggs weighting with a robust parameter of $0.5$ and cleaned the image to a threshold of $3$ times the root-mean-square (RMS) noise of $0.03$ mJy beam$^{-1}$." (Continuum emission); "The resulting data cube has a synthesised beam of $0.13$ arcsec $\times$ $0.10$ arcsec ($\approx12\times10$ pc$^2$) with a RMS noise of $0.65$ mJy beam$^{-1}$ channel$^{-1}$." (Line emission); "The resulting data cube has a synthesised beam of $0.42$ arcsec $\times$ $0.35$ arcsec ($\approx39\times33$ pc$^2$) with a RMS noise of $0.80$ mJy beam$^{-1}$ channel$^{-1}$, and its properties are also summarised in Table [2](#tab:CO)." (Low-resolution cube and inclination prior)
- time on source: 12-m array: 20 min total (726 s, 242 s, 242 s); ACA: 17 min (1028 s)  
  > "The $12$-m array data are comprised of three tracks taken on 2016 November 4, 2016 December 21 and 2017 September 7 for a total of $20$ min on source." (ALMA Observations); "The ACA data are comprised of one track taken on 2017 July 28 for a total of $17$ min on source." (ALMA Observations)
- observing dates: 12-m: 2016 November 4, 2016 December 21, 2017 September 7; ACA: 2017 July 28  
  > "The $12$-m array data are comprised of three tracks taken on 2016 November 4, 2016 December 21 and 2017 September 7 for a total of $20$ min on source." (ALMA Observations); "The ACA data are comprised of one track taken on 2017 July 28 for a total of $17$ min on source." (ALMA Observations)
- pi or archival as stated: 2016.1.00437.S (PI: Davis) and 2016.2.00053.S (PI: Liu)  
  > "The $^{12}$CO(2–1) emission line of NGC 1387 was observed with ALMA in band 6 using both the $12$-m array and the $7$-m Atacama Compact Array (ACA) as a part of projects 2016.1.00437.S (PI: Davis) and 2016.2.00053.S (PI: Liu), respectively." (ALMA Observations)
- Line: 12CO 2-1 (230.5380 GHz)
- Other facility **Hubble Space Telescope (HST) WFC3**: F160W-filter (H-band) and F110W-filter (J-band) images used to model the stellar gravitational potential and perform dust correction  
  > "We thus parameterise the intrinsic (i.e. ‘deconvolved’) stellar light distribution using a multi-Gaussian expansion (MGE) model (cite: Emsellem1994; Cappellari2002) of a *HST* Wide Field Camera 3 (WFC3) F160W-filter ($H$-band) image." (Stellar potential); "For this we use a WFC3 F110W-filter ($J$-band) image alongside the F160W-filter ($H$-band) image." (Systematic uncertainties)
- Other facility **NASA/IPAC Extragalactic Database (NED)**: Galactic extinction value of 0.006 mag  
  > "We adopt a Galactic extinction of $0.006$ mag (cite: Schlafly_2011) from the NASA/IPAC Extragalactic Database to correct for interstellar reddening." (Stellar potential)
- External data: Galaxy distance of 19.3 ± 0.8 Mpc from surface brightness fluctuations  
  > "Throughout this paper we adopt a distance of $19.3\pm0.8$ Mpc, calculated using surface brightness fluctuations (cite: Blakeslee_2009)." (NGC 1387) [from (cite: Blakeslee_2009)]
- External data: Total stellar mass of 4.70 x 10^10 M_sun, i-band absolute magnitude of -21.81, and M/L_i = 1.31 M_sun/L_sun,i  
  > "NGC 1387 has a total stellar mass of $4.70 \times 10^{10}$ M$_\odot$, derived using an $i$-band absolute magnitude of $-21.81$ and a stellar mass-to-light ratio ($M/L$) in the $i$-band $M/L_i=1.31$ M$_\odot/\text{L}_{\odot,i}$ (cite: Iodice_2019)." (NGC 1387) [from (cite: Iodice_2019)]
- External data: Effective stellar velocity dispersion sigma_e = 170.2 (+12.2 / -11.4) km s^-1  
  > "Adopting $\sigma_\text{e}=170.2^{+12.2}_{-11.4}$ km s$^{-1}$ (cite: Wegner_2003), a SMBH mass of $\approx9^{+4}_{-3}\times10^7$ M$_\odot$ is expected." (NGC 1387) [from (cite: Wegner_2003)]
- External data: M_BH - sigma_e relation  
  > "NGC 1387 does not have an existing SMBH mass measurement in the literature, but an estimate can be obtained using the relationship between SMBH mass and stellar velocity dispersion within one effective (i.e. half-light) radius ($M_\text{BH}$ – $\sigma_\text{e}$ relation) of (cite: Bosch_2016)." (NGC 1387) [from (cite: Bosch_2016)]
- External data: Total corrected CO(2-1) integrated flux of 255 ± 3 Jy km s^-1  
  > "The total flux of NGC 1387 was calculated to be $255\pm3$ Jy km s$^{-1}$ in (cite: Liang_2024), the companion paper to this work." (Line emission) [from (cite: Liang_2024)]
- External data: Previous continuum flux density measurement of 1.00 ± 0.05 mJy  
  > "This continuum flux density is similar to, but inconsistent with, a previous measurement by (cite: WISDOM_XVI) of $1.00\pm0.05$ mJy." (Continuum emission) [from (cite: WISDOM_XVI)]
- External data: Circularised MGE parameterisation of the HST WFC3 F160W PSF  
  > "These Gaussian components are first convolved with the spatial point spread function (PSF) of the F160W-filter (generated using TINYTIM; (cite: TinyTim)), itself parameterised using a circularised MGE (see Table 6 of (cite: Dominiak_2024_MASSIVE)), to reproduce instrumental effects, before being compared and fit to the *HST* image using the MGEFIT[^8] (cite: Cappellari2002) algorithm." (Stellar potential) [from (cite: Dominiak_2024_MASSIVE)]
- External data: Solar absolute magnitude of 4.60 mag in F160W (AB system)  
  > "The surface brightnesses of the Gaussian components can then be converted to luminosity surface densities using the AB magnitude system with a Solar absolute magnitude of $4.60$ mag (cite: Willmer2018) and a zero-point of $25.94$ mag (cite: WFC3)." (Stellar potential) [from (cite: Willmer2018)]
- External data: WFC3 F160W AB zero-point of 25.94 mag  
  > "The surface brightnesses of the Gaussian components can then be converted to luminosity surface densities using the AB magnitude system with a Solar absolute magnitude of $4.60$ mag (cite: Willmer2018) and a zero-point of $25.94$ mag (cite: WFC3)." (Stellar potential) [from (cite: WFC3)]
- External data: Galactic extinction of 0.006 mag  
  > "We adopt a Galactic extinction of $0.006$ mag (cite: Schlafly_2011) from the NASA/IPAC Extragalactic Database to correct for interstellar reddening." (Stellar potential) [from (cite: Schlafly_2011)]
- External data: Standard Galactic extinction curve with R_V = 3.1  
  > "This is then converted into an $H$-band extinction $A_H$ map by dividing it by the ratio of the total extinctions obtained from the standard Galactic extinction curve with a total-to-selective extinction ratio $R_V=3.1$ (cite: Fitzpatrick_1999), leading to an average $A_H$ of $0.14$ mag with a peak of $0.26$ mag." (Systematic uncertainties) [from (cite: Fitzpatrick_1999)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "The data were reduced using the COMMON ASTRONOMY SOFTWARE APPLICATIONS (CASA) package version 4.7.2 (cite: McMullin) and the standard ALMA pipeline." (ALMA Observations)
- casa version: CASA 4.7.2 (reduction) and CASA 6.4.3 (imaging)  
  > "The data were reduced using the COMMON ASTRONOMY SOFTWARE APPLICATIONS (CASA) package version 4.7.2 (cite: McMullin) and the standard ALMA pipeline." (ALMA Observations); "The following imaging steps were carried out using CASA version 6.4.3." (ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "An image of the continuum emission of NGC 1387 was created using the $(u,v)$ components from all four tracks and cleaned with the CASA task `tclean`." (Continuum emission); "These continuum-subtracted $uv$ data were then imaged and cleaned using the cube mode of the CASA task `tclean`." (Line emission)
- deconvolver: multi-frequency synthesis (continuum) and cube mode (line)  
  > "We adopted the multi-frequency synthesis mode, Briggs weighting with a robust parameter of $0.5$ and cleaned the image to a threshold of $3$ times the root-mean-square (RMS) noise of $0.03$ mJy beam$^{-1}$." (Continuum emission); "These continuum-subtracted $uv$ data were then imaged and cleaned using the cube mode of the CASA task `tclean`." (Line emission)
- weighting robust: Briggs weighting: robust = 0.5 (continuum), robust = 0.8 (high-res CO cube), robust = 2.0 (low-res CO cube)  
  > "We adopted the multi-frequency synthesis mode, Briggs weighting with a robust parameter of $0.5$ and cleaned the image to a threshold of $3$ times the root-mean-square (RMS) noise of $0.03$ mJy beam$^{-1}$." (Continuum emission); "For the imaging we used a kinematic local-standard-of-rest velocity reference frame and Briggs weighting with a robust parameter of $0.8$." (Line emission); "The same continuum-subtracted $uv$ data as for the high-resolution cube were imaged and cleaned in an analogous manner, but this time using Briggs weighting with a robust parameter of $2.0$, corresponding to natural weighting and providing a decreased angular resolution but increased sensitivity." (Low-resolution cube and inclination prior)
- uv taper: FWHM taper of 600 kilolambda (~780 m) for the low-resolution CO cube  
  > "Additionally, we used the `uvtaper` option to apply a FWHM taper of $600$ kilolambda ($\approx780$ m), to further degrade the angular and thus spatial resolution (to $\approx3$ times that of our high-resolution data cube) and improve the sensitivity of the data cube." (Low-resolution cube and inclination prior)
- cell size: Continuum: 0.02 arcsec pix^-1 (1.9 pc pix^-1); High-res CO cube: 0.03 arcsec pix^-1 (2.8 pc pix^-1); Low-res CO cube: 0.1 arcsec pix^-1 (9.4 pc pix^-1)  
  > "| Pixel scale (arcsec pix$^{-1}$) | $0.02$ |" (Table 1); "| | Pixel scale (arcsec pix$^{-1}$) | $0.03$ |" (Table 2); "| | Pixel scale (arcsec pix$^{-1}$) | $0.1$ |" (Table 2)
- image size: Continuum: 1000 x 1000 pix (20 x 20 arcsec); High-res CO cube: 1000 x 1000 pix (30.0 x 30.0 arcsec); Low-res CO cube: 300 x 300 pix (30.0 x 30.0 arcsec)  
  > "| Spatial extent (pix) | $1000\times1000$ |" (Table 1); "| | Spatial extent (pix) | $1000\times1000$ |" (Table 2); "| | Spatial extent (pix) | $300\times300$ |" (Table 2)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub with fit order 0 on the line-free channels of the line spws and the continuum spws  
  > "We fitted the same spectral windows used to image the continuum with a fit order of $0$, and this fit was subtracted from the $uv$-plane data using the CASA task `uvcontsub`." (Line emission)
- line free channels: _not stated_
- primary beam correction: Moment masks created on primary beam-uncorrected data cubes and applied to primary beam-corrected data cubes  
  > "This mask was then applied to the unsmoothed primary beam-corrected data cube to create the moment maps." (Line emission)
- array combination: Concatenated (u,v) components from all four tracks (three 12-m tracks and one 7-m ACA track) imaged jointly in tclean  
  > "An image of the continuum emission of NGC 1387 was created using the $(u,v)$ components from all four tracks and cleaned with the CASA task `tclean`." (Continuum emission); "The $^{12}$CO(2–1) line was similarly imaged using the $(u,v)$ components from all four tracks to create a data cube with high angular resolution." (Line emission)
- smoothing: 3D Gaussian kernel smoothing for moment masking (high-res: spatial FWHM = 3 x beam major axis FWHM, velocity FWHM = channel width; low-res: spatial FWHM = 1 x beam major axis FWHM, velocity FWHM = channel width)  
  > "The primary beam-uncorrected data cube was smoothed with a three-dimensional (3D) Gaussian kernel whose full width at half maximum (FWHM) in each spatial direction is equal to $3$ times the FWHM of the major axis of the synthesised beam, and whose FWHM in the velocity direction is equal to the channel width." (Line emission); "Moment maps were again created, using the same method as described in Section [3.2](#section:highres data cube), but in this case the Gaussian kernel’s FWHM in each spatial direction was equal to the FWHM of the major axis of the synthesised beam." (Low-resolution cube and inclination prior)
- final beam: Continuum: 0.09 x 0.06 arcsec (8 x 6 pc); High-res CO cube: 0.13 x 0.10 arcsec (12 x 10 pc); Low-res CO cube: 0.42 x 0.35 arcsec (39 x 33 pc)  
  > "| Synthesised beam (arcsec) | $0.09\times0.06$ |" (Table 1); "The resulting data cube has a synthesised beam of $0.13$ arcsec $\times$ $0.10$ arcsec ($\approx12\times10$ pc$^2$) with a RMS noise of $0.65$ mJy beam$^{-1}$ channel$^{-1}$." (Line emission); "The resulting data cube has a synthesised beam of $0.42$ arcsec $\times$ $0.35$ arcsec ($\approx39\times33$ pc$^2$) with a RMS noise of $0.80$ mJy beam$^{-1}$ channel$^{-1}$, and its properties are also summarised in Table [2](#tab:CO)." (Low-resolution cube and inclination prior)
- final rms: Continuum: 0.03 mJy beam^-1; High-res CO cube: 0.65 mJy beam^-1 channel^-1; Low-res CO cube: 0.80 mJy beam^-1 channel^-1  
  > "We adopted the multi-frequency synthesis mode, Briggs weighting with a robust parameter of $0.5$ and cleaned the image to a threshold of $3$ times the root-mean-square (RMS) noise of $0.03$ mJy beam$^{-1}$." (Continuum emission); "The resulting data cube has a synthesised beam of $0.13$ arcsec $\times$ $0.10$ arcsec ($\approx12\times10$ pc$^2$) with a RMS noise of $0.65$ mJy beam$^{-1}$ channel$^{-1}$." (Line emission); "The resulting data cube has a synthesised beam of $0.42$ arcsec $\times$ $0.35$ arcsec ($\approx39\times33$ pc$^2$) with a RMS noise of $0.80$ mJy beam$^{-1}$ channel$^{-1}$, and its properties are also summarised in Table [2](#tab:CO)." (Low-resolution cube and inclination prior)

### Inherited from earlier work

- Masked-moment technique for generating moment maps  
  > "We used the masked-moment technique of (cite: Dame_2011), implemented in a modified version of the PYMAKEPLOTS package[^3], to create the zeroth (integrated-intensity), first (intensity-weighted mean line-of-sight velocity) and second (intensity-weighted line-of-sight velocity dispersion) moment maps." (Line emission) [from (cite: Dame_2011)]
- Rescaling data cube uncertainties by (2N)^0.25 to account for systematic uncertainties in Bayesian MCMC fitting  
  > "(cite: Mitzkus2017) first applied this idea in a Bayesian context, where it involves rescaling the uncertainties of the data cube by a factor of $(2N)^{0.25}$, where $N$ is the number of constraints (i.e. the number of pixels with detected emission, as defined by the mask in Section [3](#section:ALMA Observations) and listed in Table [2](#tab:CO))." (Modelling method) [from (cite: vandenBosch2009); (cite: Mitzkus2017); (cite: WISDOM_IV)]
- Circularised MGE parameterisation of the HST WFC3 F160W PSF  
  > "These Gaussian components are first convolved with the spatial point spread function (PSF) of the F160W-filter (generated using TINYTIM; (cite: TinyTim)), itself parameterised using a circularised MGE (see Table 6 of (cite: Dominiak_2024_MASSIVE)), to reproduce instrumental effects, before being compared and fit to the *HST* image using the MGEFIT[^8] (cite: Cappellari2002) algorithm." (Stellar potential) [from Table 6 of (cite: Dominiak_2024_MASSIVE)]
- Fixing the axial ratios of all MGE Gaussians to the single value fitted in the outer regions across a barred galaxy  
  > "In such a case, a standard procedure is to fit a single Gaussian axial ratio in the outer regions of the galaxy (far away from the bar) and to fix the axial ratios of all the Gaussians to this, even across the barred region (see (cite: SAURON_XIV) for further details)." (Stellar potential) [from (cite: SAURON_XIV)]
- Sampling the deconvolved clean components of the molecular gas emission using SKYSAMPLER  
  > "We implement this using the custom-made KINMS plugin SKYSAMPLER[^10], described by (cite: WISDOM_IV)." (Molecular gas distribution) [from (cite: WISDOM_IV)]

### Not stated but needed to reproduce (our reading)

- Exact channel ranges or velocity intervals selected as line-free channels in the line spectral window for continuum imaging and uvcontsub.
- How the cleaning masks ('regions containing emission') in tclean were constructed (e.g., auto-multithresh vs. interactive manual masking).
- Exact relative visibility weights applied when combining the three 12-m tracks and one 7-m ACA track.
- Exact HST observation Dataset IDs / Proposal IDs for the WFC3 F160W and F110W images.
- Priors (search ranges) for the additional parameters in the low-resolution cube MCMC fit (specifically R_0, R_hole, and RA/Dec centre offsets).

## Analysis recipe

1. **Image continuum emission and fit central continuum source**: Combine (u,v) data from all four tracks and image line-free and continuum channels using CASA tclean in multi-frequency synthesis mode, then fit a 2D Gaussian using CASA imfit.  
  > "An image of the continuum emission of NGC 1387 was created using the $(u,v)$ components from all four tracks and cleaned with the CASA task `tclean`." (Continuum emission); "A Gaussian fit using the CASA task `imfit` confirms that the deconvolved source size is consistent with a point (i.e. an unresolved) source." (Continuum emission)
   - software: CASA, tclean, imfit
   - parameter: Briggs weighting robust = 0.5, threshold = 3 x RMS (0.03 mJy beam^-1), pixel scale = 0.02 arcsec pix^-1, image size = 1000 x 1000 pix  
  > "We adopted the multi-frequency synthesis mode, Briggs weighting with a robust parameter of $0.5$ and cleaned the image to a threshold of $3$ times the root-mean-square (RMS) noise of $0.03$ mJy beam$^{-1}$." (Continuum emission); "| Spatial extent (pix) | $1000\times1000$ |" (Table 1); "| Pixel scale (arcsec pix$^{-1}$) | $0.02$ |" (Table 1)
   - fitting: Gaussian fit using CASA task imfit  
  > "A Gaussian fit using the CASA task `imfit` confirms that the deconvolved source size is consistent with a point (i.e. an unresolved) source." (Continuum emission)
   - validation: Comparison with previous continuum measurement from WISDOM_XVI (1.00 ± 0.05 mJy)  
  > "This continuum flux density is similar to, but inconsistent with, a previous measurement by (cite: WISDOM_XVI) of $1.00\pm0.05$ mJy." (Continuum emission)
2. **Create high-resolution and low-resolution 12CO(2-1) data cubes, moment maps, and PVD**: Subtract continuum in uv-plane with uvcontsub, image cubes in tclean (high-res and tapered low-res), generate masked moment maps with PYMAKEPLOTS, and extract kinematic PA with PAFIT and major-axis PVD.  
  > "We fitted the same spectral windows used to image the continuum with a fit order of $0$, and this fit was subtracted from the $uv$-plane data using the CASA task `uvcontsub`." (Line emission); "We used the masked-moment technique of (cite: Dame_2011), implemented in a modified version of the PYMAKEPLOTS package[^3], to create the zeroth (integrated-intensity), first (intensity-weighted mean line-of-sight velocity) and second (intensity-weighted line-of-sight velocity dispersion) moment maps." (Line emission); "The same continuum-subtracted $uv$ data as for the high-resolution cube were imaged and cleaned in an analogous manner, but this time using Briggs weighting with a robust parameter of $2.0$, corresponding to natural weighting and providing a decreased angular resolution but increased sensitivity." (Low-resolution cube and inclination prior)
   - software: CASA, uvcontsub, tclean, PYMAKEPLOTS, PAFIT
   - parameter: High-res cube: robust = 0.8, channel width = 10 km s^-1, clean threshold = 1.5 x RMS, 1000x1000 pix at 0.03 arcsec/pix, velocity range 1100-1400 km s^-1, moment mask clip = 2.5 x RMS after 3x beam FWHM smoothing  
  > "For the imaging we used a kinematic local-standard-of-rest velocity reference frame and Briggs weighting with a robust parameter of $0.8$." (Line emission); "All pixels above a clipping threshold equal to $2.5$ times the RMS noise (measured in the unsmoothed primary beam-uncorrected data cube) were selected, creating a mask." (Line emission)
   - parameter: Low-res cube: robust = 2.0, uvtaper = 600 kilolambda (~780 m), channel width = 10 km s^-1, 300x300 pix at 0.1 arcsec/pix, moment mask clip = 5 x RMS after 1x beam FWHM smoothing  
  > "Additionally, we used the `uvtaper` option to apply a FWHM taper of $600$ kilolambda ($\approx780$ m), to further degrade the angular and thus spatial resolution (to $\approx3$ times that of our high-resolution data cube) and improve the sensitivity of the data cube." (Low-resolution cube and inclination prior); "The mask was obtained by clipping the smoothed primary beam-uncorrected data cube to a threshold of $5$ times its RMS noise." (Low-resolution cube and inclination prior)
   - fitting: uvcontsub fit order 0; PAFIT kinematic position angle determination (242.5 deg)  
  > "We fitted the same spectral windows used to image the continuum with a fit order of $0$, and this fit was subtracted from the $uv$-plane data using the CASA task `uvcontsub`." (Line emission); "The kinematic major-axis position-velocity diagram (PVD) was constructed by taking a $10$-pixel wide cut through the masked data cube along a position angle (PA) of $242.5\ensuremath{^\circ}$, determined using PAFIT[^4]." (Line emission)
   - validation: _not stated_
3. **Construct stellar gravitational potential via Multi-Gaussian Expansion (MGE) of HST image**: Fit a 2D MGE model to the HST WFC3 F160W image using MGEFIT with PSF convolution from TINYTIM, and deproject to a 3D mass density and circular velocity curve using JAMPY mge_vcirc.  
  > "These Gaussian components are first convolved with the spatial point spread function (PSF) of the F160W-filter (generated using TINYTIM; (cite: TinyTim)), itself parameterised using a circularised MGE (see Table 6 of (cite: Dominiak_2024_MASSIVE)), to reproduce instrumental effects, before being compared and fit to the *HST* image using the MGEFIT[^8] (cite: Cappellari2002) algorithm." (Stellar potential); "Alongside the free model parameters of inclination $i$, constant stellar $M/L$ and SMBH mass, we input our 2D MGE luminosity surface density model into the `mge_vcirc` routine of the JEANS ANISOTROPIC MODELLING Python package (JAMPY[^9]; (cite: Cappellari_2020)) to calculate the circular velocity curve." (Stellar potential)
   - software: TINYTIM, MGEFIT, JAMPY
   - parameter: PA fixed to 242.5 deg, axial ratio fixed to q' = 0.98 for all 8 Gaussians, Solar absolute magnitude = 4.60 mag (AB), zero-point = 25.94 mag, Galactic extinction = 0.006 mag  
  > "The surface brightnesses of the Gaussian components can then be converted to luminosity surface densities using the AB magnitude system with a Solar absolute magnitude of $4.60$ mag (cite: Willmer2018) and a zero-point of $25.94$ mag (cite: WFC3). We adopt a Galactic extinction of $0.006$ mag (cite: Schlafly_2011) from the NASA/IPAC Extragalactic Database to correct for interstellar reddening." (Stellar potential); "We then orient the MGE along this kinematic PA of $242.5\ensuremath{^\circ}$. For NGC 1387, we derive an axial ratio of $0.98$ by inspecting the outer regions of the *HST* image and assuming an infinitely-thin disc." (Stellar potential)
   - assumption: Axisymmetric stellar potential (bar treated as a first-order perturbation), infinitely-thin outer disc to estimate axial ratio q'=0.98, minimum deprojection inclination i = 11.5 deg, spatially-constant stellar M/L  
  > "MGE modelling can still be employed despite this, as the dominant disc is axisymmetric and the bar can be treated as a first-order perturbation of an otherwise axisymmetric system." (Stellar potential); "As all of our Gaussians have a fixed axial ratio $q^\prime=0.98$, the minimum inclination for which we are able to deproject is $i=11.5\degree$, which is sufficient for our purposes." (Stellar potential)
   - fitting: 2D Multi-Gaussian Expansion fit using MGEFIT  
  > "These Gaussian components are first convolved with the spatial point spread function (PSF) of the F160W-filter (generated using TINYTIM; (cite: TinyTim)), itself parameterised using a circularised MGE (see Table 6 of (cite: Dominiak_2024_MASSIVE)), to reproduce instrumental effects, before being compared and fit to the *HST* image using the MGEFIT[^8] (cite: Cappellari2002) algorithm." (Stellar potential)
   - validation: Visual comparison of MGE model isophotes overlaid on HST F160W data at small and large radii  
  > "The fit is superficially poor in the barred region of the galaxy (see the left panel of Fig. [4](#fig:MGE contours)), but the resulting MGE model is clearly an excellent fit at small radii (see the right panel of Fig. [4](#fig:MGE contours)), the most important region to constrain the SMBH mass, as well as the outermost radii unaffected by the bar." (Stellar potential)
4. **Fit low-resolution CO data cube to constrain galaxy inclination prior**: Forward model the low-resolution CO data cube using KINMS and GASTIMATOR (via KINMS_FITTER) with an analytical truncated exponential gas surface brightness profile, then smooth the inclination posterior with SCIKIT-LEARN KDE.  
  > "Second, due to the lower resolution, the molecular gas disc appears smoother and more regular, allowing to model it assuming an infinitely-thin axisymmetric disc with an exponential radial surface brightness profile." (Low-resolution cube and inclination prior); "The MCMC chain in that first stage modelling had $200,000$ steps, yielding a best-fitting inclination $i=13.6\degree^{+0.9}_{-1.2}$." (Low-resolution cube and inclination prior); "To achieve this, we used the `neighbors.KernelDensity` task, part of the SCIKIT-LEARN library, with a kernel width of $0.07$, which provides sufficient smoothing of the histogram data but does not erase the overall shape of the posterior probability distribution." (Low-resolution cube and inclination prior)
   - software: KINMS, GASTIMATOR, KINMS_FITTER, JAMPY, SCIKIT-LEARN
   - parameter: 11 free parameters (M_BH, M/L, R_0, R_hole, integrated flux, sigma_gas, PA, i, V_sys, RA offset, Dec offset), 200,000 MCMC steps (~10% burn-in), N = 188,777 constraints, uncertainty rescaling factor (2N)^0.25, KDE bandwidth = 0.07  
  > "This model has a total of $11$ free parameters: SMBH mass ($M_\text{BH}$), spatially-constant stellar mass-to-light ratio ($M/L$), molecular gas disc scale length ($R_0$), truncation radius ($R_{\text{hole}}$), integrated flux density and spatially-constant velocity dispersion ($\sigma_\text{gas}$), as well as the "nuisance" parameters describing the disc geometry position angle, inclination ($i$), systemic velocity ($V_\text{sys}$) and centre position (offsets in right ascension and declination from the image phase centre)." (Low-resolution cube and inclination prior); "The MCMC chain in that first stage modelling had $200,000$ steps, yielding a best-fitting inclination $i=13.6\degree^{+0.9}_{-1.2}$." (Low-resolution cube and inclination prior); "| | Number of constraints | $188,777$ |" (Table 2)
   - assumption: Infinitely-thin axisymmetric disc with an inner-truncated exponential radial surface brightness profile  
  > "Second, due to the lower resolution, the molecular gas disc appears smoother and more regular, allowing to model it assuming an infinitely-thin axisymmetric disc with an exponential radial surface brightness profile." (Low-resolution cube and inclination prior); "Due to the small central depression in both the higher- and the lower-resolution data cube, we also allowed for the possibility of an inner truncation in the radial surface brightness profile." (Low-resolution cube and inclination prior)
   - fitting: Bayesian MCMC using Gibbs sampler with adaptive stepping (GASTIMATOR), log-likelihood ln P proportional to -0.5 chi^2 with pixel uncertainties rescaled by (2N)^0.25; uniform priors (log-uniform for M_BH)  
  > "The KINMS model and ALMA data cubes are then compared in a Bayesian way using the general Gibbs sampler with adaptive stepping GASTIMATOR[^6]." (Modelling method); "The priors of all the parameters are uniform, apart from that of the SMBH mass which is uniform in the logarithm due to its large dynamic range." (Low-resolution cube and inclination prior)
   - validation: Check 1D marginalisation histograms for a well-defined central peak and tapering edges indicating MCMC convergence  
  > "The convergence of the chain is indicated by the fact that both histograms have a well-defined large central peak which tapers out towards the edges." (Low-resolution cube and inclination prior)
5. **Fit high-resolution CO data cube using SKYSAMPLER to measure SMBH mass and stellar M/L**: Sample the deconvolved clean components with SKYSAMPLER (5x10^6 particles), deproject with transformClouds, and forward model the high-resolution data cube with KINMS and GASTIMATOR using the KDE inclination prior and fixed continuum centre.  
  > "SKYSAMPLER first obtains the kinematics-independent intrinsic distribution of the gas by integrating the point source model (i.e. the clean components yielded by the CASA task `tclean`) of the gas distribution along the velocity axis. This distribution is then sampled with $5\times10^6$ particles." (Molecular gas distribution); "Our final results are generated by comparing the high-resolution data cube described in Section [3.2](#section:highres data cube) to a KINMS model created using the stellar potential described in Section [4.2](#subsection:stellar potential) and SKYSAMPLER, together with the inclination prior derived in Section [4.4](#subsection: inclination prior)." (Results); "The final MCMC chain in this second stage of our modelling had $150,000$ steps." (Results)
   - software: KINMS, SKYSAMPLER, GASTIMATOR, KINMS_FITTER, JAMPY
   - parameter: 5x10^6 particles, 7 free parameters (log M_BH [7, 11], M/L [0.0, 5.0], sigma_gas [0.0, 50.0], integrated intensity [0, 300], inclination [11.5, 20.0] with KDE prior, PA [0.0, 359.9], V_sys [1100, 1400]), centre fixed to 03h36m57.0335s -35d30m23.682s, 150,000 MCMC steps, N = 347,024 constraints  
  > "This model has a total of $7$ free parameters: SMBH mass, spatially-constant stellar mass-to-light ratio, molecular gas disc integrated flux density and spatially-constant molecular gas velocity dispersion, and the nuisance parameters position angle, inclination and systemic velocity." (Results); "*Note.* The centre position is fixed to that of the unresolved continuum source, $03^{\text{h}}36^{\text{m}}57\rlap{.}^\text{s}0335$, $-35\degree 30\ensuremath{'} 23\rlap{.}''682$ (J2000.0)." (Results); "| | Number of constraints | $347,024$ |" (Table 2)
   - assumption: Flat axisymmetric rotating gas disc, spatially-constant gas velocity dispersion, spatially-constant stellar M/L, kinematic centre coincident with unresolved continuum source, distance = 19.3 Mpc  
  > "However, the dominant sources of uncertainties are in fact systematic, such as our assumption of a perfectly flat axisymmetric disc or our density deprojection." (Modelling method); "We have opted to fix the centre position that of the detected continuum emission, as the latter is consistent with the kinematic centre determined in the previous modelling step (low-resolution data cube) and the reduction of the model dimensionality leads to a decrease of the computing time." (Results)
   - fitting: Bayesian MCMC (GASTIMATOR, 150,000 steps) with KDE prior on inclination, log-uniform prior on M_BH, uniform priors on remaining parameters, and pixel uncertainties rescaled by (2N)^0.25  
  > "The SMBH mass prior is again uniform in the logarithm, the inclination prior is set by the previous low-resolution data cube modelling (see Section [4.4](#subsection: inclination prior)), and all remaining parameters again have uniform priors." (Results); "The final MCMC chain in this second stage of our modelling had $150,000$ steps." (Results)
   - validation: Comparison of PVD overlays and reduced chi^2 between best-fitting SMBH model (chi^2_red = 1.117), no-SMBH model (chi^2_red = 1.134), and overly-massive SMBH model (chi^2_red = 1.125)  
  > "The model with the best-fitting SMBH has $\chi^2_\text{red}=1.117$, whereas the no SMBH model has $\chi^2_\text{red}=1.134$ (see Table [4](#table:chi2 values))." (Results); "| Model with over-massive SMBH | $1.125$ | | |" (Table 4)
6. **Quantify systematic uncertainties on SMBH mass and stellar M/L**: Run alternative dynamical models with (1) a dust-corrected F160W MGE derived using HST F110W-F160W colour excess, (2) fixed MGE axial ratios q' in [0.94, 1.00], and (3) a radially linearly-varying stellar M/L profile.  
  > "For this we use a WFC3 F110W-filter ($J$-band) image alongside the F160W-filter ($H$-band) image." (Systematic uncertainties); "To investigate the effect of our choice of fixed axial ratio on the final best-fitting parameters, we generated a series of best-fitting dynamical models whose MGE models had different fixed axial ratios in the range $0.94\leq q'\leq1.00$." (Systematic uncertainties); "We thus tested a linearly-varying $M/L$ radial profile." (Systematic uncertainties)
   - software: MGEFIT, JAMPY, KINMS, GASTIMATOR, KINMS_FITTER, SKYSAMPLER
   - parameter: Intrinsic colour (J-H)_int = 0.75 (Vega), Galactic extinction curve R_V = 3.1; axial ratios q' = 0.94, 0.96, 0.98, 1.00; linear M/L radial gradient  
  > "We then examine the outskirts of this image, away from the dustiest regions, to estimate the intrinsic $J-H$ colour of the galaxy, $(J-H)_\text{int}=0.75$." (Systematic uncertainties); "This is then converted into an $H$-band extinction $A_H$ map by dividing it by the ratio of the total extinctions obtained from the standard Galactic extinction curve with a total-to-selective extinction ratio $R_V=3.1$ (cite: Fitzpatrick_1999), leading to an average $A_H$ of $0.14$ mag with a peak of $0.26$ mag." (Systematic uncertainties)
   - assumption: Galactic extinction law with R_V = 3.1; systematic uncertainty bounds defined by maximum upper and minimum lower deviations among all tested model variants  
  > "For each parameter we adopt the maximum upper bound and minimum lower bound obtained among all model variants, therefore representing the largest deviations from the fiducial model permitted by the explored systematic tests." (Systematic uncertainties)
   - fitting: Same Bayesian MCMC framework as fiducial model for each systematic variant  
  > "Lastly, this dust-corrected image is used to generate a new MGE model as in Section [4.2](#subsection:stellar potential), and in turn a new dynamical model." (Systematic uncertainties)
   - validation: Compare reduced chi^2 across variants (1.116 for dust correction, 1.108 for linearly-varying M/L) and verify consistency within 3-sigma statistical uncertainties  
  > "| Model with dust correction | $1.116$ | | |" (Table 4); "| Model with linearly-varying $M/L$ | $1.108$ | | |" (Table 4)

## Software

- **CASA** 4.7.2 and 6.4.3: Data reduction via standard ALMA pipeline (4.7.2) and continuum and line imaging (6.4.3)  
  > "The data were reduced using the COMMON ASTRONOMY SOFTWARE APPLICATIONS (CASA) package version 4.7.2 (cite: McMullin) and the standard ALMA pipeline. The following imaging steps were carried out using CASA version 6.4.3." (ALMA Observations)
- **tclean** : Cleaning continuum image and high/low-resolution CO(2-1) data cubes  
  > "An image of the continuum emission of NGC 1387 was created using the $(u,v)$ components from all four tracks and cleaned with the CASA task `tclean`." (Continuum emission); "These continuum-subtracted $uv$ data were then imaged and cleaned using the cube mode of the CASA task `tclean`." (Line emission)
- **imfit** : 2D Gaussian fitting of the central continuum source  
  > "A Gaussian fit using the CASA task `imfit` confirms that the deconvolved source size is consistent with a point (i.e. an unresolved) source." (Continuum emission)
- **uvcontsub** : Subtracting continuum emission in the uv-plane with a 0th-order polynomial fit  
  > "We fitted the same spectral windows used to image the continuum with a fit order of $0$, and this fit was subtracted from the $uv$-plane data using the CASA task `uvcontsub`." (Line emission)
- **PYMAKEPLOTS** : Creating masked zeroth, first, and second moment maps and position-velocity diagrams  
  > "We used the masked-moment technique of (cite: Dame_2011), implemented in a modified version of the PYMAKEPLOTS package[^3], to create the zeroth (integrated-intensity), first (intensity-weighted mean line-of-sight velocity) and second (intensity-weighted line-of-sight velocity dispersion) moment maps." (Line emission)
- **PAFIT** : Determining the kinematic position angle of the molecular gas disc  
  > "The kinematic major-axis position-velocity diagram (PVD) was constructed by taking a $10$-pixel wide cut through the masked data cube along a position angle (PA) of $242.5\ensuremath{^\circ}$, determined using PAFIT[^4]." (Line emission)
- **KINMS** : Forward modelling the molecular gas distribution and kinematics into simulated data cubes  
  > "Dynamical modelling of our data was carried out by fitting a model data cube to the observed molecular gas distribution and kinematics using KINEMATIC MOLECULAR SIMULATION (KINMS; (cite: Davis2013a))[^5]." (Modelling method)
- **GASTIMATOR** : Bayesian MCMC parameter estimation using a general Gibbs sampler with adaptive stepping  
  > "The KINMS model and ALMA data cubes are then compared in a Bayesian way using the general Gibbs sampler with adaptive stepping GASTIMATOR[^6]." (Modelling method)
- **KINMS_FITTER** : Python wrapper interfacing GASTIMATOR and KINMS, and deprojecting cloudlet positions via transformClouds  
  > "We implement GASTIMATOR and KINMS using the Python wrapper KINMS_FITTER[^7], which provides a simple interface between the two and an easily-accessible integrated library of surface brightness radial profiles." (Modelling method); "Assuming a certain position angle and inclination of the galaxy, the particle positions generated by SKYSAMPLER can then be deprojected into their intrinsic positions in the galaxy plane using the KINMS_FITTER task `transformClouds`." (Molecular gas distribution)
- **TINYTIM** : Generating the spatial PSF of the HST WFC3 F160W filter  
  > "These Gaussian components are first convolved with the spatial point spread function (PSF) of the F160W-filter (generated using TINYTIM; (cite: TinyTim)), itself parameterised using a circularised MGE (see Table 6 of (cite: Dominiak_2024_MASSIVE)), to reproduce instrumental effects, before being compared and fit to the *HST* image using the MGEFIT[^8] (cite: Cappellari2002) algorithm." (Stellar potential)
- **MGEFIT** : Fitting a Multi-Gaussian Expansion (MGE) model to the HST image  
  > "These Gaussian components are first convolved with the spatial point spread function (PSF) of the F160W-filter (generated using TINYTIM; (cite: TinyTim)), itself parameterised using a circularised MGE (see Table 6 of (cite: Dominiak_2024_MASSIVE)), to reproduce instrumental effects, before being compared and fit to the *HST* image using the MGEFIT[^8] (cite: Cappellari2002) algorithm." (Stellar potential)
- **JAMPY** : Deprojecting the 2D MGE model and calculating the circular velocity curve via the mge_vcirc routine  
  > "Alongside the free model parameters of inclination $i$, constant stellar $M/L$ and SMBH mass, we input our 2D MGE luminosity surface density model into the `mge_vcirc` routine of the JEANS ANISOTROPIC MODELLING Python package (JAMPY[^9]; (cite: Cappellari_2020)) to calculate the circular velocity curve." (Stellar potential)
- **SKYSAMPLER** : Sampling the deconvolved tclean point source model of the molecular gas emission with 5x10^6 particles  
  > "We implement this using the custom-made KINMS plugin SKYSAMPLER[^10], described by (cite: WISDOM_IV)." (Molecular gas distribution)
- **SCIKIT-LEARN** : Smoothing the inclination posterior distribution via neighbors.KernelDensity to create a continuous prior  
  > "To achieve this, we used the `neighbors.KernelDensity` task, part of the SCIKIT-LEARN library, with a kernel width of $0.07$, which provides sufficient smoothing of the histogram data but does not erase the overall shape of the posterior probability distribution." (Low-resolution cube and inclination prior)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMBH mass (M_BH) | 1.10e8 | +1.71e8/-0.95e8 [stat, 3sigma] +2.45e8/-1.09e8 [sys] | M_odot | 5 | We infer a SMBH mass of $1.10^{+1.71}_{-0.95}[\text{stat},3\sigma]^{+2.45}_{-1.09}[\text{sys}]\times 10^8$ M$_\odot$ and a F160W-filter stellar mass-to-light ratio of $0.90^{+0.44}_{-0.35}[\text{stat}, 3\sigma]^{+0.46}_{-0.36}[\text{sys}]$ M$_\odot$/L$_{\odot,\text{F160W}}$. |
| Log SMBH mass log(M_BH/M_odot) | 8.04 | -0.23/+0.18 (1sigma), -0.87/+0.41 (3sigma) | dex | 5 | / $\log(M_\text{BH}/\text{M}_\odot)$ / $7$ / $\rightarrow$ / $11$ / $8.04$ / $-0.23,+0.18$ / $-0.87,+0.41$ / |
| Stellar mass-to-light ratio (M/L_F160W) | 0.90 | +0.44/-0.35 [stat, 3sigma] +0.46/-0.36 [sys] (-0.14/+0.16 at 1sigma) | M_odot/L_odot,F160W | 5 | We infer a SMBH mass of $1.10^{+1.71}_{-0.95}[\text{stat},3\sigma]^{+2.45}_{-1.09}[\text{sys}]\times 10^8$ M$_\odot$ and a F160W-filter stellar mass-to-light ratio of $0.90^{+0.44}_{-0.35}[\text{stat}, 3\sigma]^{+0.46}_{-0.36}[\text{sys}]$ M$_\odot$/L$_{\odot,\text{F160W}}$.; / Stellar $M/L_{\text{F160W}}$ (M$_\odot$/L$_{\odot,\text{F160W}}$) / $0.0$ / $\rightarrow$ / $5.0$ / $0.90$ / $-0.14, +0.16$ / $-0.35,+0.44$ / |
| Molecular gas velocity dispersion | 6.0 | ±0.3 (1sigma), -0.8/+0.9 (3sigma) | km s^-1 | 5 | / Velocity dispersion (km s$^{-1}$) / $0.0$ / $\rightarrow$ / $50.0$ / $6.0$ / $\pm0.3$ / $-0.8,+0.9$ / |
| Molecular gas disc integrated intensity (model) | 264 | ±9 (1sigma), -26/+25 (3sigma) | Jy km s^-1 | 5 | / Integrated intensity (Jy km s$^{-1}$) / $0$ / $\rightarrow$ / $300$ / $264$ / $\pm9$ / $-26, +25$ / |
| Inclination (fiducial high-res model) | 14.2 | -1.1/+1.3 (1sigma), -2.6/+4.1 (3sigma) | degree | 5 | / Inclination (degree) / $11.5$ / $\rightarrow$ / $20.0$ / $14.2$ / $-1.1, +1.3$ / $-2.6, +4.1$ / |
| Position angle (fiducial high-res model) | 243.9 | ±0.3 (1sigma), -1.0/+0.9 (3sigma) | degree | 5 | / Position angle (degree) / $0.0$ / $\rightarrow$ / $359.9$ / $243.9$ / $\pm0.3$ / $-1.0, +0.9$ / |
| Systemic velocity (fiducial high-res model) | 1267.2 | ±0.3 (1sigma), -0.7/+0.8 (3sigma) | km s^-1 | 5 | / Systemic velocity (km s$^{-1}$) / $1100$ / $\rightarrow$ / $1400$ / $1267.2$ / $\pm0.3$ / $-0.7, +0.8$ / |
| Inclination (low-res cube fit) | 13.6 | +0.9/-1.2 | degree | 4 | The MCMC chain in that first stage modelling had $200,000$ steps, yielding a best-fitting inclination $i=13.6\degree^{+0.9}_{-1.2}$. |
| Continuum integrated flux density (239.4 GHz) | 1.23 | ±0.06 | mJy | 1 | We detect a small central source of continuum emission with an integrated flux density of $1.23\pm0.06$ mJy and a peak intensity of $1.20\pm0.03$ mJy beam$^{-1}$. |
| Continuum peak intensity (239.4 GHz) | 1.20 | ±0.03 | mJy beam^-1 | 1 | We detect a small central source of continuum emission with an integrated flux density of $1.23\pm0.06$ mJy and a peak intensity of $1.20\pm0.03$ mJy beam$^{-1}$. |
| Continuum source Right Ascension (J2000.0) | 03h36m57.0335s | ±0.0001s | hms | 1 | / Right ascension (J2000.0) / $03^{\text{h}}36^{\text{m}}57\rlap{.}^\text{s}0335\pm0\rlap{.}^\text{s}0001$ / |
| Continuum source Declination (J2000.0) | -35d30m23.682s | ±0.001 arcsec | dms | 1 | / Declination (J2000.0) / $-35\degree30\ensuremath{'}23.682\ensuremath{''}\pm0.001\ensuremath{''}$ / |
| SMBH sphere of influence radius (best-fit M_BH) | 16 (0.17) | not stated | pc (arcsec) | 5 | Using the standard approximation of a SMBH SoI (see Section [2](#section:NGC1387)) and the best-fitting SMBH mass yields $R_\text{SoI}\approx16$ pc ($\approx0.17$ arcsec). |
| Radius of equal mass contribution (R_eq) | 19 (0.20) | not stated | pc (arcsec) | 5 | Figure [9](#fig:cummulative mass function) shows this radius of equal mass contribution to be $R_\text{eq}\approx19$ pc ($\approx0.20$ arcsec), slightly larger than $R_\text{SoI}$. |
| Central molecular gas depression radius (R_hole) | 19 (0.2) | not stated | pc (arcsec) | 2 | We also detect a small central depression $\approx0.2$ arcsec ($\approx19$ pc) in radius. |
| SMBH mass (dust-corrected MGE model) | 1.91e8 | +1.64e8/-1.22e8 | M_odot | 6 | This leads to a best-fitting SMBH mass of $1.91^{+1.64}_{-1.22}\times10^8$ M$_\odot$ and a best-fitting $M/L$ of $0.86_{-0.26}^{+0.28}$ M$_\odot$/L$_{\odot,\text{F160W}}$, representing a $74$ per cent increase of the SMBH mass and a $5$ per cent decrease of the $M/L$ compared to our fiducial model. |
| SMBH mass (linearly-varying M/L model) | 4.3e7 | +11.5e7/-4.2e7 | M_odot | 6 | Keeping all other parameters as before, a model with a radially linearly-varying $M/L$ yields a best-fitting SMBH mass of $4.3^{+11.5}_{-4.2}\times10^7$ M$_\odot$, a $61$ per cent decrease compared to out fiducial model, but nevertheless consistent with it within the $3\sigma$ statistical uncertainties reported in Table [\[tab:Best Fit\]](#tab:Best Fit). |

## Qualitative findings

- NGC 1387 hosts a face-on, flocculent, regularly-rotating central molecular gas disc ~18 arcsec (~1.7 kpc) in diameter with a central depression of radius ~0.2 arcsec (~19 pc).  
  > "In NGC 1387 we detect a disc of flocculent, regularly-rotating molecular gas approximately $18$ arcsec ($\approx1.7$ kpc) in diameter, coincident with the central dust disc of the galaxy (see Fig. [1](#fig:HST)). We also detect a small central depression $\approx0.2$ arcsec ($\approx19$ pc) in radius." (Line emission)
- An unresolved central continuum point source is detected at 239.4 GHz (1.25 mm) with an integrated flux density of 1.23 ± 0.06 mJy.  
  > "We detect a small central source of continuum emission with an integrated flux density of $1.23\pm0.06$ mJy and a peak intensity of $1.20\pm0.03$ mJy beam$^{-1}$." (Continuum emission); "A Gaussian fit using the CASA task `imfit` confirms that the deconvolved source size is consistent with a point (i.e. an unresolved) source." (Continuum emission)
- Due to the low inclination (14.2 deg), there is a strong degeneracy between inclination and M/L and a positive correlation between M_BH and M/L.  
  > "As expected due to the face on nature of the galaxy, Fig. [7](#fig:cornerPlot) shows a very strong degeneracy between $M/L$ and inclination and a weaker degeneracy between $M_{\text{BH}}$ and inclination. Figure [7](#fig:cornerPlot) also reveals a positive correlation between $M_{\text{BH}}$ and $M/L$ (cite: WISDOM_IV), as the effects of inclination are sufficiently strong in this face-on system to overwhelm the usual degeneracy arising from the conservation of total dynamical mass." (Results)
- The measured SMBH mass is consistent with the M_BH - sigma_e relation of Bosch_2016.  
  > "We thus compare our best-fitting NGC 1387 SMBH mass measurement to the $M_{\text{BH}}$ – $\sigma_\text{e}$ relation of (cite: Bosch_2016) in Fig. [10](#fig:m-sigma), revealing that our best-fitting SMBH mass is in very good agreement with the relation." (Best-fitting mass model)

## Claim tuples

- H: NGC 1387 hosts a central supermassive black hole whose mass can be dynamically measured from high-resolution ALMA 12CO(2-1) kinematics despite a central depression in the molecular gas. | E: Forward model the 0.13 x 0.10 arcsec ALMA 12CO(2-1) data cube using KINMS, SKYSAMPLER, and GASTIMATOR with an HST F160W MGE stellar mass model and an inclination prior from a low-resolution data cube, comparing models with and without a SMBH. | R: Best-fitting SMBH mass is 1.10 (+1.71/-0.95 [stat, 3sigma], +2.45/-1.09 [sys]) x 10^8 M_odot and stellar M/L_F160W is 0.90 (+0.44/-0.35 [stat, 3sigma], +0.46/-0.36 [sys]) M_odot/L_odot,F160W; the model with a SMBH has chi^2_red = 1.117 compared to 1.134 for no SMBH (Delta chi^2_red = 0.017 >> sqrt(2/N) = 0.0024). | F: A model with a non-zero central SMBH mass is quantitatively preferred over a model without a SMBH, and at the innermost radius probed (~19 pc), ~49% of the enclosed mass is due to the SMBH. | **supported**
- H: The SMBH mass of NGC 1387 follows the empirical SMBH mass - stellar velocity dispersion (M_BH - sigma_e) relation. | E: Compare the dynamically inferred SMBH mass of NGC 1387 against the M_BH - sigma_e relation of Bosch_2016 using sigma_e = 170.2 (+12.2/-11.4) km s^-1. | R: The measured SMBH mass of 1.10 x 10^8 M_odot matches the expected value of ~9 (+4/-3) x 10^7 M_odot from the relation. | F: The inferred SMBH mass of NGC 1387 is in very good agreement with the M_BH - sigma_e relation. | **supported**
- H: Systematic uncertainties from dust attenuation, fixed MGE axial ratio, and radial M/L variations do not invalidate the fiducial SMBH mass measurement. | E: Construct and fit alternative dynamical models incorporating a J-H colour-excess dust-corrected MGE, MGE axial ratios from 0.94 to 1.00, and a linearly-varying radial M/L profile. | R: Dust correction increases M_BH by 74% to 1.91 (+1.64/-1.22) x 10^8 M_odot; varying q' changes log(M_BH/M_odot) between 8.02 and 8.06; a linearly-varying M/L decreases M_BH by 61% to 4.3 (+11.5/-4.2) x 10^7 M_odot. All variants remain within the 3-sigma statistical uncertainty of the fiducial model. | F: Systematic variations of the SMBH mass and M/L are comparable to and consistent within the 3-sigma statistical uncertainties. | **supported**

## Reasoning

- Why this data: High angular resolution ALMA 12CO(2-1) observations (~0.12 arcsec / ~11 pc) are needed to resolve the SMBH sphere of influence (~0.13 arcsec / ~12 pc), while HST WFC3 F160W (H-band) is the longest wavelength HST image available to constrain the stellar gravitational potential with minimal dust extinction.  
  > "We adopted a channel width of $10$ km s$^{-1}$, again selected to achieve angular (and thus spatial) and velocity resolutions effectively probing the predicted SMBH SoI while providing adequate sensitivity." (Line emission); "We selected the longest wavelength *HST* image available to minimise dust extinction." (Stellar potential)
- Why this method: Briggs robust = 0.8 trades off between poor S/N at robust = 0.5 and insufficient resolution at robust = 1.0. SKYSAMPLER is required to reproduce the flocculent molecular gas distribution, while a tapered low-resolution cube with an exponential profile is required first to constrain the inclination prior because SKYSAMPLER removes disc geometry constraints. KDE smoothing is used for the inclination prior because the posterior is multi-peaked.  
  > "The conventional robust parameter of $0.5$ yielded very poor signal-to-noise ratios in regions of emission, whereas a parameter of $1.0$ yielded a synthesised beam size that did not sufficiently sample the predicted SoI. A robust parameter of $0.8$ represents a trade-off between the two." (Line emission); "Nevertheless, due to the flocculence of the molecular gas, using SKYSAMPLER is the only way we can reliably reproduce the surface brightness of NGC 1387 (an analytic surface brightness distribution would have too many parameters)." (Low-resolution cube and inclination prior); "However, in the case of NGC 1387, the inclination posterior probability distribution cannot be easily approximated using a parametric function, as it has an irregular shape with three smaller peaks around a central dominant one (see Fig. [6](#fig:cornerPlot_inc))." (Low-resolution cube and inclination prior)
- Alternative: Briggs weighting with robust = 0.5 or robust = 1.0 for the high-resolution CO cube (rejected due to poor S/N and insufficient spatial resolution of the SoI, respectively).  
  > "The conventional robust parameter of $0.5$ yielded very poor signal-to-noise ratios in regions of emission, whereas a parameter of $1.0$ yielded a synthesised beam size that did not sufficiently sample the predicted SoI." (Line emission)
- Alternative: Fitting the detailed surface brightness of the bar in the MGE model or masking dust in the HST image (rejected because fitting the bar as an axisymmetric structure would misrepresent the 3D density, and dust is too uniform to mask manually).  
  > "If we were to incorrectly interpret the bar as a nearly edge-on axisymmetric disc embedded into a spherical spheroid, and fit its detailed surface brightness, the deprojected intrinsic density would completely misrepresent the true density distribution." (Stellar potential); "There is rather uniform dust extinction across the entire extent of the galaxy, so we have opted not to mask any part of the disc." (Stellar potential)
- Alternative: Using an analytic surface brightness profile for the high-resolution CO cube or fitting inclination directly with SKYSAMPLER without a prior (rejected because the gas is too flocculent for an analytic profile, and SKYSAMPLER alone leaves a ±5 deg inclination uncertainty).  
  > "When using SKYSAMPLER, the inclination of the galaxy remained poorly constrained ($\pm5\degree$ uncertainty), most likely due to the the face-on orientation of the galaxy and the sparsity of gas in the outer regions of the disc." (Low-resolution cube and inclination prior); "Nevertheless, due to the flocculence of the molecular gas, using SKYSAMPLER is the only way we can reliably reproduce the surface brightness of NGC 1387 (an analytic surface brightness distribution would have too many parameters)." (Low-resolution cube and inclination prior)
- Alternative: Fitting a parametric Gaussian function to the low-resolution inclination posterior (rejected because the posterior has an irregular shape with three smaller peaks around the central peak).  
  > "However, in the case of NGC 1387, the inclination posterior probability distribution cannot be easily approximated using a parametric function, as it has an irregular shape with three smaller peaks around a central dominant one (see Fig. [6](#fig:cornerPlot_inc))." (Low-resolution cube and inclination prior)
- How they decided it was enough: _not stated_
- Limitation (authors): A central depression (~0.2 arcsec / ~19 pc radius) in the molecular gas is similar in size to the SMBH sphere of influence, preventing a clear Keplerian velocity rise within R_SoI.  
  > "This depression is similar in extent to the predicted $R_\text{SoI}$, and thus prevents the innermost parts of the gravitational potential from being probed robustly. This is likely the reason why no clear Keplerian rise of the velocities is present within $R_\text{SoI}$." (Line emission)
- Limitation (authors): Deprojection of the 2D MGE surface brightness to 3D volume density is mathematically non-unique, and the degeneracy between inclination and dynamical mass is severe at the low inclination of NGC 1387.  
  > "The deprojection inferring the intrinsic density from the observed surface brightness is mathematically non unique and the degeneracy becomes particularly severe at low inclination (cite: Rybicki1987), as in our case." (Stellar potential); "Figure [6](#fig:cornerPlot_inc) reveals a very strong degeneracy between $i$ and $M/L$, but this is to be expected given the small inclination." (Low-resolution cube and inclination prior)
- Limitation (authors): The heuristic rescaling of pixel uncertainties by (2N)^0.25 is not rigorously justified.  
  > "Although not rigorously justified, this method has been adopted in several WISDOM papers and has been shown to yield sensible uncertainties consistent with those derived using a bootstrap approach to systematic effects in (cite: WISDOM_IV)." (Modelling method)
- Limitation (authors): The MGE model assumes axisymmetry and provides a superficially poor fit across the non-axisymmetric bar region, and the axial ratio q'=0.98 was determined by eye.  
  > "The fit is superficially poor in the barred region of the galaxy (see the left panel of Fig. [4](#fig:MGE contours)), but the resulting MGE model is clearly an excellent fit at small radii (see the right panel of Fig. [4](#fig:MGE contours)), the most important region to constrain the SMBH mass, as well as the outermost radii unaffected by the bar." (Stellar potential); "The adopted $q'=0.98$ was determined by eye and as such is somewhat uncertain." (Systematic uncertainties)
- Limitation (authors): Galaxy distance uncertainty is not included in the final SMBH mass uncertainty budget.  
  > "As is standard practice, however, we do not include the distance uncertainty in our final uncertainty budget, as our fiducial mass can be trivially (linearly) scaled to any other adopted distance." (Systematic uncertainties)
- Caveat (inferred, ours): Because the central molecular gas hole (R_hole ~ 19 pc) is slightly larger than the formal sphere of influence (R_SoI ~ 16 pc) and no central Keplerian velocity upturn is observed, the SMBH mass measurement relies heavily on the accuracy of the inner stellar mass profile (MGE + M/L assumption) inside ~0.2 arcsec.
- Caveat (inferred, ours): The linearly-varying M/L model achieves a better reduced chi^2 (1.108) than the fiducial constant-M/L model (1.117) and yields a 61% lower SMBH mass (4.3 x 10^7 M_odot) whose 3-sigma lower bound approaches zero (0.1 x 10^7 M_odot), highlighting sensitivity to inner stellar population/dust gradients.
- Caveat (inferred, ours): The near-face-on inclination (i ~ 14.2 deg) lies very close to the MGE deprojection limit (11.5 deg for q' = 0.98), amplifying any small systematic error in inclination into large fractional changes in enclosed dynamical mass.

## Reproducibility

- Data public (paper): Observations are publicly available in the ALMA archive and the Hubble Science Archive.  
  > "The observations underlying this article are available in the ALMA archive, at <https://almascience.eso.org/asax/>, and in the Hubble Science Archive, at <https://hst.esac.esa.int/ehst/>." (Data Availability)
- Products in archive: _not stated_
- Code: Publicly available packages linked in footnotes: PYMAKEPLOTS, PAFIT, KINMS, GASTIMATOR, KINMS_FITTER, MGEFIT, JAMPY, and SKYSAMPLER.  
  > "We used the masked-moment technique of (cite: Dame_2011), implemented in a modified version of the PYMAKEPLOTS package[^3], to create the zeroth (integrated-intensity), first (intensity-weighted mean line-of-sight velocity) and second (intensity-weighted line-of-sight velocity dispersion) moment maps." (Line emission); "We implement GASTIMATOR and KINMS using the Python wrapper KINMS_FITTER[^7], which provides a simple interface between the two and an easily-accessible integrated library of surface brightness radial profiles." (Modelling method)
- Missing: Exact line-free frequency/channel selections used for continuum imaging and uvcontsub.
- Missing: Exact tclean masking procedure (manual vs automated masking parameters).
- Missing: Exact HST observation IDs for the WFC3 F160W and F110W images.
- Missing: Prior ranges used for R_0, R_hole, and centre offsets in the low-resolution data cube MCMC fit.
- Data volume (inferred): ~5–15 GB (three 12-m tracks totaling 20 min on-source and one 7-m ACA track of 17 min on-source with one 3840/2048-channel spectral window and three 128-channel spectral windows, plus 1000x1000x30 spectral cubes).
- Score (inferred): 85/5, Raw ALMA project codes and track UIDs are explicitly tabulated, CASA versions and imaging parameters (robust, cell size, image size, taper, channel width, thresholds, smoothing kernels) are thoroughly documented, deprojected MGE parameters are fully tabulated in Table 3, and all modelling codes and priors for the main fit are open-source and explicitly stated. Minor deductions only for unstated line-free channel ranges and low-res cube nuisance priors.
- Rediscovery candidate: yes, Both ALMA datasets (2016.1.00437.S, 2016.2.00053.S) and HST WFC3 images are public, all software tools (CASA, KinMS, GAStimator, KinMS_fitter, skySampler, MGEfit, JamPy) are open-source, the MGE table is provided, and the primary goal is a clear numeric measurement of the SMBH mass and stellar M/L.

## Links

- Method: (cite: Dame_2011) (Masked-moment technique used to create moment maps)
- Method: (cite: Davis2013a) (KINMS forward modelling code for molecular gas kinematics)
- Method: (cite: WISDOM_IV) (SKYSAMPLER plugin and Bayesian uncertainty rescaling validation)
- Method: (cite: Emsellem1994) (Multi-Gaussian Expansion (MGE) formalism)
- Method: (cite: Cappellari2002) (MGEFIT algorithm and MGE deprojection)
- Method: (cite: Cappellari_2020) (JAMPY package used to compute circular velocity curves from MGE models)
- Method: (cite: vandenBosch2009) (Heuristic rescaling of statistical uncertainties to account for systematics)
- Method: (cite: Mitzkus2017) (Bayesian implementation of (2N)^0.25 uncertainty rescaling)
- Method: (cite: SAURON_XIV) (Procedure for fixing MGE axial ratios across barred galaxies)
- Companion: (cite: Liang_2024) (Parallel WISDOM paper investigating giant molecular clouds and total CO flux in NGC 1387)
- Companion: (cite: WISDOM_XVI) (Previous WISDOM paper reporting the millimetre continuum emission of NGC 1387)
- Related: WISDOM (mm-Wave Interferometric Survey of Dark Object Masses)

## Checks

```json
{
 "quotes": 208,
 "quotes_ok": 208,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 36,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 118,
  "stated": 106,
  "rate": 0.898
 },
 "evidence_ok": true
}
```
