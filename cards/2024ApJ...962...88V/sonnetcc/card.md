# The EDGE-CALIFA Survey: Molecular Gas and Star Formation Activity across the Green Valley

`2024ApJ...962...88V` | The Astrophysical Journal 2024 | first author: Villanueva, Vicente | arXiv: 2312.03995 | DOI: 10.3847/1538-4357/ad1387

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies
- Question: How do star formation quenching processes along the main sequence, green valley and red cloud change the molecular gas fraction and star formation efficiency (SFE_mol = SFR/M_mol), globally and as a function of radius, in massive nearby galaxies?  
  > "We test how star formation quenching processes affect the star formation rate (SFR) per unit molecular gas mass" (abstract); "We impose no selection on SFR in order to cover the full range of star formation activities in this mass range and enable the study of quenching." (2.1 The ACA EDGE sample)
- Target **ACA EDGE sample: 60 CALIFA galaxies (log M* > 10, dec < 30 deg), listed in Table 1**: coordinates per-galaxy R.A./Decl. (J2000) in Table 1  
  > "ACA EDGE targets a subsample of CALIFA galaxies with declination appropriate to observe with ALMA" (2.1 The ACA EDGE sample); "Optical inclinations and east-of-north position angles (PA) are taken from HyperLEDA" (2.1 The ACA EDGE sample); z/distance per-galaxy redshift and distance in Table 1 (z about 0.0049 to 0.0304; 17 to 163 Mpc)  
  > "ACA EDGE targets a subsample of CALIFA galaxies with declination appropriate to observe with ALMA" (2.1 The ACA EDGE sample); "Optical inclinations and east-of-north position angles (PA) are taken from HyperLEDA" (2.1 The ACA EDGE sample); distance from _not stated_

## Data provenance

- ALMA projects: 2019.2.00029.S
- bands: _not stated_
- frequencies and spectral setup: spectral bandwidth ~1980 MHz, raw spectral resolution ~1.938 MHz ~ 2.5 km/s; CO(2-1) line  
  > "We set a spectral bandwidth of $\approx$ 1980 MHz and a raw spectral resolution of $\sim$ 1.938 MHz $\approx$ 2.5 km s$^{-1}$." (2.2 The CO data)
- continuum bandwidth: _not stated_
- arrays: ACA 7m only (ACA-only project)  
  > "CO observations of our ACA-only project were taken between December 2019 and September 2021" (2.2 The CO data); "we obtained 7m ACA observations for 60" (2.2 The CO data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~5 to 7 arcsec (~1.5 kpc), depending on declination  
  > "and from $\sim$5$''$ to 7$''$  angular resolution (i.e., probing physical scales $\sim 1.5$ kpc at the distance of ACA EDGE galaxies), depending on the declination of the source." (2.2 The CO data)
- max recoverable scale: _not stated_
- sensitivity: design rms ~12 to 18 mK at 10 km/s channel width (~0.9 to 1.2 Msun/pc^2)  
  > "The scheduling blocks were designed to detect the CO(2-1) emission line down to a root mean square (rms) spanning from $\sim$12 to 18 mK at 10 km s$^{-1}$ channel width" (2.2 The CO data)
- time on source: 15 to 43 minutes per galaxy  
  > "spending between 15 and 43 minutes on-source for each galaxy" (2.2 The CO data)
- observing dates: December 2019 to September 2021  
  > "CO observations of our ACA-only project were taken between December 2019 and September 2021" (2.2 The CO data)
- pi or archival as stated: PI A. D. Bolatto, ALMA Cycle 7 project 2019.2.00029.S  
  > "A total of 60 galaxies were observed in CO(2–1) by the ALMA Cycle 7 project 2019.2.00029.S (P.I. A. D. Bolatto)." (2.1 The ACA EDGE sample)
- Line: 12CO J=2-1 (not stated)
- Other facility **CALIFA (PMAS/PPAK IFU, Calar Alto 3.5 m)**: Halpha and Hbeta fluxes (extinction-corrected SFR), stellar mass surface density and other maps via PIPE3D, Halpha velocity maps for CO masks  
  > "The data were acquired using the PMAS/PPAK IFU instrument (cite: Roth2005) at the 3.5 m telescope of the Calar Alto Observatory." (2.4 The CALIFA survey and ancillary data); "to generate maps of derived quantities" (2.4 The CALIFA survey and ancillary data)
- Other facility **SDSS z-band images**: ellipse fits to constrain galaxy inclination  
  > "to obtain a better constraint on the inclination" (3.1 Basic equations and assumptions)
- Other facility **APEX (APEX EDGE survey, Colombo et al. 2020)**: 12CO(2-1) single-dish fluxes for 51 of the galaxies, used to check ACA fluxes  
  > "for 51 of our galaxies using APEX observations at" (2.3 Data reduction and products)
- Other facility **HyperLEDA**: optical inclinations, position angles, and maximum apparent HI rotation velocity  
  > "Optical inclinations and east-of-north position angles (PA) are taken from HyperLEDA" (2.1 The ACA EDGE sample); "We adopt the maximum apparent rotation velocity reported in HI by HyperLEDA (cite: Bottinelli1982; Bottinelli1990)" (2.3 Data reduction and products)
- External data: 12CO(2-1) APEX integrated fluxes for comparison with ACA fluxes  
  > "for 51 of our galaxies using APEX observations at" (2.3 Data reduction and products) [from (cite: Colombo2020)]
- External data: Star-formation main sequence line used to define Delta SFMS  
  > "galaxies near the SFMS (black line; (cite: Cano-Diaz2016)) tend to have higher molecular gas masses" (4.1.1 SFR versus stellar and molecular gas masses) [from (cite: Cano-Diaz2016)]
- External data: Nuclear activity classification (SF/AGN/LINER) of CALIFA galaxies  
  > "we have used estimates of the nuclear activity of CALIFA galaxies from (cite: Garcia-Lorenzo2015)" (4.2.2 SFE and bulge properties) [from (cite: Garcia-Lorenzo2015)]
- External data: Additional AGN type classification  
  > "We complement the AGN classification using (cite: Lacerda2020)" (4.2.2 SFE and bulge properties) [from (cite: Lacerda2020)]
- External data: Metallicity-stellar mass relation for CALIFA galaxies (O3N2), used to get Z' for variable alpha_CO  
  > "using the metallicity-stellar mass relation (based on the O3N2 calibrator; (cite: Marino2013)) for CALIFA galaxies from (cite: Sanchez2017)" (3.1 Basic equations and assumptions) [from (cite: Sanchez2017); (cite: Marino2013)]
- External data: Line ratio R21 = 0.65 adopted from literature  
  > "based on (cite: Leroy2013) and (cite: denBrok2021), measured at kpc scales" (3.1 Basic equations and assumptions) [from (cite: Leroy2013); (cite: denBrok2021)]
- External data: Milky Way CO-to-H2 conversion factor X_CO = 2e20 (alpha_CO,MW = 4.3)  
  > "$X_{\rm CO} = 2 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (3.1 Basic equations and assumptions) [from (cite: Walter2008)]
- External data: Variable alpha_CO(Z', Sigma_total) prescription  
  > "using the CO-to-H$_2$ conversion factor from Equation 31 in (cite: Bolatto2013)" (3.1 Basic equations and assumptions) [from (cite: Bolatto2013)]
- External data: SFR calibration from Halpha  
  > "is obtained using (cite: RosaGonzalez2002)" (3.1 Basic equations and assumptions) [from (cite: RosaGonzalez2002)]
- External data: PHANGS-ALMA central-region pixels used for comparison of SFE_mol  
  > "of PHANGS-ALMA galaxies drawn from (cite: Querejeta2021) (black crosses)" (4.2.2 SFE and bulge properties) [from (cite: Querejeta2021)]

## Processing

### Calibration

- pipeline or manual: uv data as delivered by ALMA, calibrated by the observatory pipeline  
  > "We used $uv$ data delivered by ALMA and calibrated by the observatory pipeline (cite: Hunter2023)" (2.3 Data reduction and products)
- casa version: CASA 5.6.1-8 (2019 and 2020 data); CASA 6.2.1-7 (2021 data)  
  > "5.6.1-8 for data taken in 2019 and 2020" (2.3 Data reduction and products); "6.2.1-7 for data taken in 2021" (2.3 Data reduction and products)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: PHANGS-ALMA Imaging Pipeline Version 2.1 run in CASA 5.6.1-8; channel width 5.08 km/s, LSR, radio velocity definition  
  > "using the PHANGS–ALMA Imaging Pipeline Version 2.1" (2.3 Data reduction and products); "We ran the PHANGS–ALMA imaging pipeline in CASA version 5.6.1-8." (2.3 Data reduction and products); "We used a channel width of 5.08 km s$^{-1}$ and adopted the local standard of rest (LSR) as our velocity reference frame, using the radio definition of velocity." (2.3 Data reduction and products)
- deconvolver: multi-scale clean (S/N ~ 4 threshold) followed by single-scale clean down to S/N ~ 1  
  > "This includes an initial multi-scale clean (we used scales of $0$, 5, and 10$\ensuremath{''}$) with a relatively high S/N$\approx 4$ threshold" (2.3 Data reduction and products); "followed by a single scale clean that uses an automatically generated, more restrictive clean mask and cleans down to S/N$\approx1$ by default" (2.3 Data reduction and products)
- weighting robust: Briggs robust = 0.5  
  > "We used a Briggs weighting parameter of $=0.5$ (cite: Briggs1995)" (2.3 Data reduction and products)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: automatically generated, more restrictive clean mask for the single-scale clean  
  > "a single scale clean that uses an automatically generated, more restrictive clean mask" (2.3 Data reduction and products)
- multiscale scales: 0, 5, 10 arcsec  
  > "an initial multi-scale clean (we used scales of $0$, 5, and 10$\ensuremath{''}$)" (2.3 Data reduction and products)
- continuum subtraction: pipeline subtracts continuum emission (method details not given)  
  > "The pipeline combines all $uv$ data for a given target on a common spectral grid, subtracts continuum emission, and then carries out a multi-step deconvolution." (2.3 Data reduction and products)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cubes convolved to the APEX resolution (26.3 arcsec) for flux comparison  
  > "To compare the fluxes, we convolve our CO datacubes to match the APEX angular resolution" (2.3 Data reduction and products)
- final beam: cube convolved to a round synthesized beam and converted to Kelvin  
  > "After the initial imaging, the pipeline convolves the cube to have a round synthesized beam, converts the image to units of Kelvin" (2.3 Data reduction and products)
- final rms: _not stated_

### Inherited from earlier work

- Imaging recipe (details of deconvolution, masking, convolution, units)  
  > "See (cite: Leroy2021b) for more details." (2.3 Data reduction and products) [from PHANGS-ALMA Imaging Pipeline (cite: Leroy2021b)]
- Calibration done by the observatory pipeline  
  > "calibrated by the observatory pipeline (cite: Hunter2023)" (2.3 Data reduction and products) [from (cite: Hunter2023)]
- Noise modelling and product creation done with software from earlier EDGE work, not the PHANGS pipeline  
  > "We did not use the noise modeling or product creation portions of the PHANGS–ALMA pipeline, but instead used software based on previous EDGE work." (2.3 Data reduction and products) [from previous EDGE work (no citation given)]
- CO dilated mask construction  
  > "following the procedure for a “dilated mask” detailed in (cite: Bolatto2017)" (2.3 Data reduction and products) [from (cite: Bolatto2017)]
- Halpha mask velocity window (FWHM prescription)  
  > "following the FWHM prescription from Figure 2 in (cite: Villanueva2021)" (2.3 Data reduction and products) [from (cite: Villanueva2021)]
- Extinction estimate method for each spaxel  
  > "we estimate the extinction (cite: Bolatto2017)" (3.1 Basic equations and assumptions) [from (cite: Bolatto2017)]
- Bulge radius R_b = 1 kpc adopted for spirals without a clear break or with bars  
  > "Similar to (cite: Villanueva2022), we adopt $R_{\rm b}=1$ kpc for spiral galaxies where we do not identify a clear break" (3.3 Bulge radii and masses) [from (cite: Villanueva2022)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction and for the signal-free rms
- Image size, cell size and primary-beam correction/cutoff used in the PHANGS pipeline run
- Exact S/N thresholds and mask-generation parameters actually applied per galaxy, and the PHANGS pipeline config files
- The EDGE noise-modelling and moment-map software ('software based on previous EDGE work') is not named or released
- Per-galaxy choice of mask type beyond the counts given, and the velocity windows
- CALIFA data release version and PIPE3D products (dezonified maps) used, and how field stars were masked
- SFMS line parameters used to compute Delta SFMS (taken from Cano-Diaz et al. 2016, coefficients not given)
- Flux calibrator and flux-scale uncertainty for the ACA data
- Radial-profile bin edges for the elliptical annuli and how R_b breaks were identified per galaxy
- Details of the OLS bisector fits (software, error treatment) and how the exponential scale-length fits were performed

## Analysis recipe

1. **image the ACA CO(2-1) cubes**: Image observatory-calibrated uv data with the PHANGS-ALMA imaging pipeline (common spectral grid, continuum subtraction, multi-scale then single-scale clean, round beam, Kelvin units)  
  > "Briefly, the PHANGS–ALMA imaging pipeline is designed to produce accurate images of extended spectral line emission." (2.3 Data reduction and products)
   - software: CASA, PHANGS-ALMA Imaging Pipeline
   - parameter: Briggs robust = 0.5  
  > "We used a Briggs weighting parameter of $=0.5$ (cite: Briggs1995)" (2.3 Data reduction and products)
   - parameter: channel width 5.08 km/s, LSR, radio definition  
  > "We used a channel width of 5.08 km s$^{-1}$ and adopted the local standard of rest (LSR) as our velocity reference frame, using the radio definition of velocity." (2.3 Data reduction and products)
   - parameter: multi-scale clean scales 0, 5, 10 arcsec, S/N ~ 4 threshold  
  > "an initial multi-scale clean (we used scales of $0$, 5, and 10$\ensuremath{''}$) with a relatively high S/N$\approx 4$ threshold" (2.3 Data reduction and products)
   - fitting: _not stated_
   - validation: Cubes visually inspected for problems or imaging errors  
  > "All cubes were visually inspected for obvious problems or imaging errors." (2.3 Data reduction and products)
2. **build signal masks**: Combine (logical OR) a CO-based dilated mask with the best of three independent masks (Halpha-velocity, simple rotation, flat) chosen by maximum recovered CO flux  
  > "We first create a mask using the CO cube, following the procedure for a “dilated mask” detailed in (cite: Bolatto2017)." (2.3 Data reduction and products); "We then use three different procedures to generate this mask, and choose the one that recovers the most CO emission flux." (2.3 Data reduction and products)
   - parameter: dilated mask around spectral peaks at >~3.5 sigma  
  > "areas around spectral peaks detected at $\gtrsim3.5\sigma$ significance" (2.3 Data reduction and products)
   - parameter: Halpha mask used for 33 galaxies; rotation mask for 25; flat mask for 2  
  > "H$\alpha$ mask (33 galaxies)" (2.3 Data reduction and products); "Rotation mask (25 galaxies)" (2.3 Data reduction and products); "Flat mask (2 galaxies)" (2.3 Data reduction and products)
   - parameter: Halpha spaxels with SNR < 5 excluded from the Halpha mask  
  > "H$\alpha$ spaxels with SNR$<5$ in intensity are excluded from the mask." (2.3 Data reduction and products)
   - assumption: Halpha mask assumes CO kinematics similar to Halpha; rotation mask assumes a predominantly rotating galaxy with CO spanning the HI velocities  
  > "This approach assumes that the kinematics of the CO are similar to the kinematics of the H$\alpha$" (2.3 Data reduction and products); "This approach assumes that the galaxy is predominantly rotating, and that the CO emission spans the same velocities as the HI." (2.3 Data reduction and products)
   - fitting: _not stated_
   - validation: _not stated_
3. **make moment maps with uncertainties**: Moment 0, moment 1 and peak-SNR maps from masked cubes; per-spaxel uncertainty from rms of signal-free spectrum times sqrt(N) times channel width; blank pixels outside 2 sigma contour of M0  
  > "We generate moment 0 maps (integrated intensity of the spectrum along the spectral axis) from the CO(2-1) spectral line cubes, in units of Jy/beam km s$^{-1}$, and after multiplying them by our mask" (2.3 Data reduction and products); "To obtain the uncertainties of the moment 0 maps, we compute the rms in the signal-free part of the spectrum in each spaxel, $\sigma_{\rm i}$, and use the equation" (2.3 Data reduction and products)
   - parameter: pixels outside the 2 sigma contour of M0 blanked  
  > "Finally, we blank the pixels outside the 2$\sigma$ contour for $M_0$." (2.3 Data reduction and products)
   - fitting: _not stated_
   - validation: _not stated_
4. **check ACA fluxes against APEX**: Convolve ACA cubes to APEX resolution, take the central-pixel spectrum, correct APEX main-beam efficiency, integrate over a visually defined window and compare with APEX EDGE fluxes  
  > "To compare the fluxes, we convolve our CO datacubes to match the APEX angular resolution and we take the spectrum of the pixel located at the galaxy center," (2.3 Data reduction and products); "Finally, we integrate the spectra over a spectral window defined by visual inspection (typically $\sim$500 km s$^{-1}$ wide)." (2.3 Data reduction and products)
   - parameter: APEX main beam efficiency 0.80 (PI230)  
  > "correcting by the recommended APEX main beam antenna efficiency (for the PI230 receiver at this frequency, $\eta_{\rm mb}=0.80$)." (2.3 Data reduction and products)
   - fitting: _not stated_
   - validation: Median ACA-to-APEX flux ratio 0.82; discrepancies attributed to calibration, resolved-out flux, imperfect deconvolution or APEX pointing  
  > "On average, we find that the median ACA-to-APEX flux ratio is 0.82." (2.3 Data reduction and products)
5. **derive SFR and stellar mass surface density maps from CALIFA**: Balmer-decrement extinction per 1 arcsec spaxel, then SFR from extinction-corrected Halpha; stellar mass surface density from PIPE3D maps with dezonification and a Salpeter-to-Kroupa factor of 1.6  
  > "To compute the extinction-corrected SFRs, we estimate the extinction (cite: Bolatto2017) for each 1$''$ spaxel using the equation:" (3.1 Basic equations and assumptions); "We obtain the stellar mass surface density, $\Sigma_\star$, from the stellar maps derived by" (3.1 Basic equations and assumptions)
   - software: PIPE3D
   - parameter: correction factor 1.6 from Salpeter (PIPE3D) to Kroupa IMF  
  > "which includes a correction factor of 1.6 to move from a Salpeter IMF" (3.1 Basic equations and assumptions)
   - assumption: Cardelli et al. 1989 extinction curve and intrinsic Halpha/Hbeta of 2.86 (case B)  
  > "and the coefficients assume a (cite: Cardelli1989) extinction curve and an unextinguished flux ratio of 2.86 for case B recombination." (3.1 Basic equations and assumptions)
   - fitting: _not stated_
   - validation: _not stated_
6. **convert CO intensity to molecular gas surface density**: Sigma_mol = (alpha_CO / R21) cos(i) I_CO(2-1) with a constant Milky Way alpha_CO as default; a variable alpha_CO(Z', Sigma_total) as a test  
  > "The molecular gas surface density, $\Sigma_{\rm mol}$, is derived from the integrated CO intensity, $I_{\rm CO(2-1)}$, by adopting a constant CO-to-H$_2$ conversion factor" (3.1 Basic equations and assumptions); "using the CO-to-H$_2$ conversion factor from Equation 31 in (cite: Bolatto2013)" (3.1 Basic equations and assumptions)
   - parameter: X_CO = 2e20 cm^-2 (K km/s)^-1 (alpha_CO,MW = 4.3)  
  > "$X_{\rm CO} = 2 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (3.1 Basic equations and assumptions)
   - parameter: R21 = 0.65  
  > "which adopts the average line luminosity ratio of $R_{21}=I_{\rm CO(2-1)}/I_{\rm CO(1-0)}=0.65$" (3.1 Basic equations and assumptions)
   - parameter: variable alpha_CO computed with Sigma_GMC^100 = 1 and Z' from the CALIFA mass-metallicity relation  
  > "we adopt $\Sigma^{100}_{\rm GMC}=1$ and derive $Z'$ using the metallicity-stellar mass relation" (3.1 Basic equations and assumptions)
   - assumption: inclination from an ellipse fit to the SDSS z-band contour at ~1.2 r25, assuming an infinitely thin disk (arccos of axis ratio)  
  > "we fit an ellipse to the SDSS $z$-band contour for a major axis $A_{\rm maj}\sim 1.2 r_{25}$." (3.1 Basic equations and assumptions)
   - fitting: _not stated_
   - validation: Results repeated with the variable alpha_CO prescription to test dependence on alpha_CO  
  > "We also test how our results depend on our adopted prescription by using the CO-to-H$_2$ conversion factor from Equation 31 in (cite: Bolatto2013)" (3.1 Basic equations and assumptions)
7. **classify galaxies by Delta SFMS and derive global quantities**: Integrate surface densities within r25 for SFR, M*, M_mol; classify as main sequence, green valley or red cloud by Delta SFMS; compare R_mol_star and depletion time between groups  
  > "Green valley (11 galaxies, 9 with $5\sigma$ CO detections; green shaded area), encompassing galaxies with $-1.0$ dex$< \Delta$SFMS $\leq-0.5$ dex." (4.1.1 SFR versus stellar and molecular gas masses); "(with radius $r_{25}$ and centered at the optical center)" (3.1 Basic equations and assumptions)
   - parameter: main sequence: Delta SFMS > -0.5 dex; green valley: -1.0 < Delta SFMS <= -0.5 dex; red cloud: Delta SFMS <= -1.0 dex  
  > "Green valley (11 galaxies, 9 with $5\sigma$ CO detections; green shaded area), encompassing galaxies with $-1.0$ dex$< \Delta$SFMS $\leq-0.5$ dex." (4.1.1 SFR versus stellar and molecular gas masses)
   - fitting: _not stated_
   - validation: Compared with Colombo et al. 2020 and Sanchez et al. 2018 trends; small number of detected red cloud galaxies noted  
  > "However, these results have to be considered carefully due to the small number of CO-detected red cloud galaxies." (4.1.1 SFR versus stellar and molecular gas masses)
8. **measure radial profiles, bulge radii and bulge masses**: Average azimuthal CO, stellar and SFR surface densities in elliptical annuli (inclination-corrected) for 30 galaxies; bulge radius from the break in the stellar profile; bulge mass from integrating the stellar profile within R_b  
  > "We derive these profiles by measuring the average azimuthal CO, stellar, and SFR surface densities in elliptical annuli in the CO(2-1) datacubes." (3.2 Radial profiles); "We characterize the bulge-dominated region by identifying the galactocentric radius where there is a break with respect to the stellar radial profiles." (3.3 Bulge radii and masses)
   - parameter: 30 galaxies with i <= 70 deg and 5 sigma integrated CO detections; spaxels with 3 sigma CO detections  
  > "subsample of 30 galaxies with inclinations $\leq70^{\circ}$ and $5\sigma$ integrated CO detections" (3.2 Radial profiles)
   - parameter: annulus width ~5 arcsec (average of minor beam axes)  
  > "within an annulus $\sim$5$''$   wide (average of the minor beam axes)" (3.2 Radial profiles)
   - assumption: R_b = 1 kpc for spirals without a clear break or with a dominant bar  
  > "we adopt $R_{\rm b}=1$ kpc for spiral galaxies where we do not identify a clear break" (3.3 Bulge radii and masses)
   - fitting: _not stated_
   - validation: Bulge radii compared with Mendez-Abreu et al. 2017 decomposition for 28 galaxies (Pearson r = 0.92)  
  > "including 28 ACA EDGE galaxies in their analysis" (3.3 Bulge radii and masses)
9. **fit exponential scale lengths of gas and stars**: Fit exponential profiles to the 23 galaxies with decreasing Sigma_mol profiles (stellar fits restricted to disk) and compare l_mol with l_star via an OLS bisector fit y = alpha x  
  > "When we compute an ordinary least-square (OLS; blue solid line in Fig." (4.1.2 Exponential scale lengths); "we have selected 23 galaxies with decreasing $\Sigma_{\rm mol}$ profiles" (4.1.2 Exponential scale lengths)
   - parameter: bisector fit for model y = alpha x for main-sequence galaxies with at least 5 sigma l_mol measurements  
  > "bisector fit for the model $y=\alpha x$ for main sequence galaxies with at least $5\sigma$ $l_{\rm mol}$ measurements" (4.1.2 Exponential scale lengths)
   - fitting: OLS bisector, single slope through the origin; sampler and priors not applicable  
  > "bisector fit for the model $y=\alpha x$ for main sequence galaxies with at least $5\sigma$ $l_{\rm mol}$ measurements" (4.1.2 Exponential scale lengths)
   - validation: Repeated with CO moment 0 maps smoothed to 10 arcsec; slope stays above unity  
  > "We test how this relation varies with angular resolution by fitting the CO radial profiles derived from CO moment 0 maps smoothed at 10$''$ beamsize." (4.1.2 Exponential scale lengths)
10. **fit the resolved SFMS and resolved Kennicutt-Schmidt relations**: OLS bisector fits of log Sigma_SFR versus log Sigma_* and log Sigma_mol for main-sequence pixels of the 30 galaxies, compared with CARMA EDGE, PHANGS and ALMaQUEST  
  > "we compute an OLS bisector fit for main sequence pixels using the model $y = \alpha x+ \beta$" (4.2.1 SFR versus stellar and molecular gas surface densities)
   - parameter: pixels from 30 galaxies with 5 sigma global CO detections and i < 70 deg  
  > "The figure includes pixels from the 30 ACA EDGE galaxies with $5\sigma$ global CO detections and $i<70^\circ$." (4.2.1 SFR versus stellar and molecular gas surface densities)
   - fitting: OLS bisector y = alpha x + beta  
  > "we compute an OLS bisector fit for main sequence pixels using the model $y = \alpha x+ \beta$" (4.2.1 SFR versus stellar and molecular gas surface densities)
   - validation: Slopes compared with literature and noted to depend on fitting method and alpha_CO  
  > "However, we remark that these slopes are very sensitive to the fitting method and the $\alpha_{\rm CO}$ prescription adopted." (Summary and conclusions)
11. **compare SFE_mol, molecular-to-stellar fraction and sSFR by Delta SFMS and nuclear activity**: Resolved SFE_mol, rR_mol_star and sSFR in bulge pixels and in radial bins, split by Delta SFMS and by nuclear activity (NNA, LINER, AGN); fixed vs variable alpha_CO; Student t-tests on inner vs outer SFE distributions  
  > "versus galactocentric radius (in radial bins of $0.3 R_{\rm e}$, $\sim 1.5$ kpc resolution at the mean distance)" (4.2.3 What drives star-formation quenching in ACA EDGE galaxies?); "We perform a Student’s $t$-test to verify if the distribution of SFE$_{\rm mol}$ values in green valley galaxies are drawn from the same parent population." (4.2.3 What drives star-formation quenching in ACA EDGE galaxies?)
   - parameter: pixels at r < 0.5 Re rejected for LINER/AGN galaxies to avoid contamination; SFR removed at r < 0.5 Re in profiles  
  > "To avoid SFR contamination due to AGN/LINER, we reject pixels at $r<0.5 R_{\rm e}$." (4.2.3 What drives star-formation quenching in ACA EDGE galaxies?)
   - parameter: central vs outer split at r = Re for NNA galaxies; r = 1.2 Re for the nuclear-activity comparison  
  > "central pixels (i.e., pixels at $r<R_{\rm e}$) and outer pixels (i.e., pixels at $r>R_{\rm e}$)" (4.2.3 What drives star-formation quenching in ACA EDGE galaxies?)
   - assumption: Galaxies with no detected nuclear activity are classed as star-forming (SF)  
  > "Although galaxies may host an AGN and actively form stars, we classify galaxies as SF if no nuclear activity is detected." (4.2.2 SFE and bulge properties)
   - fitting: Student t-test (not a fit)  
  > "We perform a Student’s $t$-test to verify if the distribution of SFE$_{\rm mol}$ values in green valley galaxies are drawn from the same parent population." (4.2.3 What drives star-formation quenching in ACA EDGE galaxies?)
   - validation: Tendencies re-checked with the variable alpha_CO prescription; admitted that the 1.5 kpc resolution cannot resolve bulges  
  > "these tendencies do not change when adopting the variable $\alpha_{\rm CO}$ prescription" (4.2.2 SFE and bulge properties)

## Software

- **CASA** 5.6.1-8 (2019-2020 data and imaging); 6.2.1-7 (2021 data calibration): calibration and imaging  
  > "Both the calibration and imaging utilized the Common Astronomy Software Applications" (2.3 Data reduction and products)
- **PHANGS-ALMA Imaging Pipeline** 2.1: imaging the CO(2-1) emission  
  > "using the PHANGS–ALMA Imaging Pipeline Version 2.1" (2.3 Data reduction and products)
- **PIPE3D** : derived maps from CALIFA cubes (stellar mass, Halpha, Hbeta)  
  > "to generate maps of derived quantities" (2.4 The CALIFA survey and ancillary data)
- **Astropy** : listed in Software section; specific use not stated  
  > "Astropy (cite: AstropyCollaboration2018)" (Software)
- **Matplotlib** : listed in Software section; specific use not stated  
  > "MatPlotLib (cite: Hunter2007)" (Software)
- **NumPy** : listed in Software section; specific use not stated  
  > "NumPy (cite: Harris2020)" (Software)
- **SciPy** : listed in Software section; specific use not stated  
  > "SciPy (cite: 2020SciPy-NMeth)" (Software)
- **seaborn** : listed in Software section; specific use not stated  
  > "seaborn (cite: Waskom2021)" (Software)
- **Scikit-learn** : listed in Software section; specific use not stated  
  > "Scikit-learn (cite: scikit-learn)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 5 sigma CO detections among 60 ACA EDGE galaxies | 46 (~77%) | not stated | galaxies | 1 | we obtain 5$\sigma$ CO detections for 46 ACA EDGE galaxies |
| Median ACA-to-APEX integrated flux ratio | 0.82 | not stated | dimensionless | 4 | On average, we find that the median ACA-to-APEX flux ratio is 0.82. |
| Galaxy classification counts (main sequence / red sequence / green valley) | 36 / 13 / 11 | not stated | galaxies | 7 | Of the 60 galaxies in ACA EDGE, 36 are on the star-formation main sequence, 13 are on the red sequence, and 11 lie in the |
| Mean log R_mol_star of main sequence galaxies | ~ -1.6 | not stated | dex | 7 | with an average log$[R^{\rm mol}_{\star}]\sim -1.6$ dex |
| Red cloud depletion time relative to main sequence and green valley | ~3 and ~6 times longer | not stated | dimensionless | 7 | red cloud galaxies have $\tau_{\rm dep}$ around 3 and 6 times longer than main sequence and green valley galaxies, respectively |
| l_mol versus l_star slope (main sequence, 5 sigma l_mol) | 1.24 | 0.05 | dimensionless | 9 | we obtain $l_{\rm mol}=(1.24\pm 0.05)\times l_{\star}$ |
| l_mol versus l_star slope with CO smoothed to 10 arcsec | 1.15 | 0.05 | dimensionless | 9 | $l_{\rm mol}=(1.15\pm 0.05)\times l_{\star}$ |
| Pearson correlation of l_mol with l_star (main sequence and green valley) | 0.6 (p < 0.01) | not stated | dimensionless | 9 | Pearson $r_{\rm p}=0.6$; $p$-value $<0.01$ |
| Resolved SFMS slope | 1.20 | 0.07 | dimensionless | 10 | We find slopes of $\alpha_{\rm rSFMS}=[1.20\pm0.07]$ and $\alpha_{\rm rKS}=[1.19\pm0.07]$ for the rSFMS and rKS. |
| Resolved Kennicutt-Schmidt slope | 1.19 | 0.07 | dimensionless | 10 | We find slopes of $\alpha_{\rm rSFMS}=[1.20\pm0.07]$ and $\alpha_{\rm rKS}=[1.19\pm0.07]$ for the rSFMS and rKS. |
| SFE_mol within green valley bulges relative to main sequence (fixed alpha_CO) | ~3 times lower | not stated | dimensionless | 11 | We find that SFE$_{\rm mol}$ values within green valley bulges tend to be lower than for main sequence galaxies ($\sim3$ times lower). |
| rR_mol_star of green valley bulge pixels relative to main sequence (fixed alpha_CO) | ~3 times lower | not stated | dimensionless | 11 | values of green valley pixels are $\sim3$ times lower than those within main sequence bulges when adopting the fixed $\alpha_{\rm CO}$ |
| Bulge density of green valley relative to main sequence galaxies | ~3 times denser | not stated | dimensionless | 11 | green valley bulges are $\sim 3$ times denser than those of main sequence galaxies |
| Student t statistic, green valley inner versus outer SFE_mol (variable alpha_CO) | |t| = 0.89 (dof = 222) | not stated | dimensionless | 11 | We obtain $\lvert t \rvert =0.89$ for green valley (degrees of freedom = $222$) pixel distributions |
| Student t statistic, AGN inner versus outer SFE_mol (variable alpha_CO) | |t| = 1.89 (dof = 140) | not stated | dimensionless | 11 | we obtain $\lvert t \rvert =1.89$ (degrees of freedom = $140$) |

## Qualitative findings

- Gas depletion or removal seems the dominant driver of quenching through the green valley, but a reduction in star formation efficiency is also required.  
  > "our results suggest that although gas depletion (or removal) seems to be the most important driver of the star-formation quenching in galaxies transiting through the green valley, a reduction in star formation efficiency is also required during this stage." (abstract)
- Main sequence SFE_mol stays roughly constant with radius, while green valley galaxies show a systematic increase of SFE_mol, R_mol_star and sSFR with radius.  
  > "While efficiencies in main sequence galaxies remain almost constant with galactocentric radius, in green valley galaxies we note a systematic increase of SFE$_{\rm mol}$, $R^{\rm mol}_{\star}$, and specific star formation rate, sSFR, with increasing radius." (abstract)

## Claim tuples

- H: Green valley and red cloud galaxies have lower molecular gas fractions than main-sequence galaxies | E: Classify 60 ACA EDGE galaxies by Delta SFMS and compare R_mol_star = M_mol/M* among CO-detected galaxies | R: Green valley and red cloud fractions are about an order of magnitude lower than main sequence (mean log R ~ -1.6) | F: Molecular gas content decreases with decreasing star formation activity | **supported**
- H: The star formation efficiency of molecular gas is lower in green valley bulges than in main-sequence bulges | E: Resolved SFE_mol of star-forming pixels inside R_b for 23 main sequence and 5 green valley galaxies, with fixed and variable alpha_CO | R: Green valley bulge SFE_mol is ~3 times lower than for main sequence; tendency persists with variable alpha_CO | F: Reduced SFE in addition to gas depletion plays a role in quenching through the green valley | **supported**
- H: Molecular gas is distributed like the stellar disk in these galaxies (l_mol ~ l_star) | E: Exponential fits to 23 molecular gas and 30 stellar radial profiles; OLS bisector slope | R: l_mol = (1.24 +/- 0.05) l_star, 1.15 +/- 0.05 at 10 arcsec resolution | F: A close 6:5 relation, consistent with main-sequence spirals from the literature | **supported**
- H: The resolved SFMS and Kennicutt-Schmidt slopes of ACA EDGE galaxies match those of field star-forming spirals | E: OLS bisector fits to main-sequence pixels of 30 galaxies | R: Slopes 1.20 +/- 0.07 (rSFMS) and 1.19 +/- 0.07 (rKS), above CARMA EDGE and PHANGS values but consistent with ALMaQUEST | F: Slopes are above unity but sensitive to the fitting method and alpha_CO prescription | **partially**
- H: Morphological quenching or dynamical suppression in bulges reduces SFE in green valley galaxies | E: Compare bulge densities and Student t-tests of central versus outer SFE_mol distributions | R: Green valley bulges are ~3 times denser; t-tests show only a small difference (|t| = 0.89), with resolution limiting the test | F: These mechanisms seem to only complement gas depletion and/or removal | **partially**

## Reasoning

- Why this data: ACA EDGE avoids selecting on SFR or CO brightness, so that galaxies across the quenching sequence and early types are covered  
  > "We impose no selection on SFR in order to cover the full range of star formation activities in this mass range and enable the study of quenching." (2.1 The ACA EDGE sample)
- Why this method: Galaxies without a detected nuclear activity are grouped as SF because results for confirmed SF-only galaxies and SF plus undetected activity do not differ significantly  
  > "We adopt this since we do not see significant variations between the results for confirmed SF-only galaxies and SF+not-detected nuclear activity galaxies." (4.2.2 SFE and bulge properties)
- Alternative: A variable alpha_CO(Z', Sigma_total) was tested instead of the constant Milky Way value; main trends were retained  
  > "We also test how our results depend on our adopted prescription by using the CO-to-H$_2$ conversion factor from Equation 31 in (cite: Bolatto2013)" (3.1 Basic equations and assumptions)
- How they decided it was enough: _not stated_
- Limitation (authors): Four galaxies have incomplete CO line coverage; their fluxes are lower limits  
  > "NGC 0768, NGC 6427, NGC 7321, and UGC 12250 have incomplete CO line coverage since their emission peaks are located at the edge of the ACA spectral window." (2.3 Data reduction and products)
- Limitation (authors): Few CO-detected red cloud galaxies limit the red cloud conclusions  
  > "However, these results have to be considered carefully due to the small number of CO-detected red cloud galaxies." (4.1.1 SFR versus stellar and molecular gas masses)
- Limitation (authors): Poor spatial resolution (~1.5 kpc) may hide differences between bulge and disk SFE  
  > "the small difference between these two distributions may be caused by the poor spatial resolution of our CO observations" (4.2.3 What drives star-formation quenching in ACA EDGE galaxies?)
- Limitation (authors): SFE and related results are sensitive to the adopted alpha_CO prescription  
  > "We note however that these results are very sensitive to the adopted $\alpha_{\rm CO}$ prescription." (4.2.1 SFR versus stellar and molecular gas surface densities)
- Caveat (inferred, ours): The t-test sentences conclude that the null can be rejected even though |t| is below the critical value; the wording appears inverted and the inference is unclear
- Caveat (inferred, ours): Only 11 green valley galaxies (9 detected, 5 in the bulge analysis) support the central quenching claims
- Caveat (inferred, ours): Halpha-based SFR near the centres of LINER/AGN galaxies is contaminated, yet bulge SFE results rely on it
- Caveat (inferred, ours): The paper says ALMA data were observed in project 2019.2.00029.S while the archive manifest links 2019.2.00028.S

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Mask, noise-model and moment-map software from earlier EDGE work is neither named nor released
- Missing: PHANGS pipeline settings (line-free channels, image/cell size, cleaning mask parameters) are not listed
- Missing: SFMS line coefficients, bulge radii breaks, fit procedures and derived-quantity tables are only partly given
- Missing: Archive project code printed by the paper (2019.2.00029.S) differs from the code the archive links (2019.2.00028.S)
- Data volume (inferred): ACA 7m mosaics of 60 galaxies, 15 to 43 min each: roughly 50-150 GB of raw data (guess), plus a few GB of cubes
- Score (inferred): 3/5, ALMA observations and the PHANGS pipeline are public, and many numeric results are given, but CALIFA products, the in-house EDGE masking/moment software, and several imaging settings are not specified.
- Rediscovery candidate: yes, ACA data of a named project are archived and the imaging recipe is a public pipeline; numeric answer keys exist (flux ratio 0.82, l_mol/l_star = 1.24, slopes 1.20 and 1.19), though CALIFA maps and some steps would need extra sources.

## Links

- Method: (cite: Leroy2021b) (PHANGS-ALMA imaging pipeline used for the cubes)
- Method: (cite: Hunter2023) (ALMA observatory calibration pipeline)
- Method: (cite: Bolatto2017) (CARMA EDGE survey; dilated mask and extinction recipe)
- Method: (cite: Sanchez2016b) (CALIFA data release 3 and data reduction)
- Companion: (cite: Villanueva2021) (CARMA EDGE resolved SFE and scale-length results compared with here; Halpha mask prescription)
- Companion: (cite: Villanueva2022) (VERTICO Virgo galaxies scale lengths; bulge radius convention)
- Companion: (cite: Colombo2020) (APEX EDGE CO(2-1) fluxes used for comparison)
- Related: CALIFA
- Related: CARMA EDGE
- Related: APEX EDGE
- Related: PHANGS-ALMA
- Related: VERTICO
- Related: ALMaQUEST
- Related: HERACLES
- Related: xCOLD GASS

## Checks

```json
{
 "quotes": 151,
 "quotes_ok": 151,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2019.2.00029.S"
 ],
 "obscore_codes_not_in_card": [
  "2019.2.00028.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 137,
  "stated": 105,
  "rate": 0.766
 },
 "evidence_ok": true
}
```
