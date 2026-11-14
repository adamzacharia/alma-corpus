# A Photoionized Accretion Disk around a Young High-mass Star

`2020ApJ...904...77G` | The Astrophysical Journal 2020 | first author: Guzmán, Andrés E. | arXiv: 2010.00244 | DOI: 10.3847/1538-4357/abbe09

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Can a photo-ionized disk survive around G345.49+1.47 and sustain continued accretion?  
  > "the data present direct observational evidence of how disks can effectively survive the photo-ionization feedback from young high-mass stars." (Abstract); "Can the disk around G345.49+1.47 sustain these accretion rates?" (Accretion onto G345.49+1.47)
- Target **G345.4938+01.4677 (G345.49+1.47)**: coordinates Pointing center: R.A. 16h59m41.63s, decl. -40°03'43.5'' (ICRS)  
  > "the high-mass young stellar object (HMYSO) G345.4938+01.4677" (Abstract); "R.A.=16$^{\rm h}$59$^{\rm m}$41.63s, decl.=$-40\ensuremath{^\circ}03\ensuremath{'}43.5\ensuremath{''}$ (ICRS)" (Observations.); "For this work, we use the spectrophotometric distance of 2.38 kpc (cite: Moises2011MNRAS) instead of the kinematic distance of 1.7 kpc used by several authors before." (Results); z/distance 2.38 kpc  
  > "the high-mass young stellar object (HMYSO) G345.4938+01.4677" (Abstract); "R.A.=16$^{\rm h}$59$^{\rm m}$41.63s, decl.=$-40\ensuremath{^\circ}03\ensuremath{'}43.5\ensuremath{''}$ (ICRS)" (Observations.); "For this work, we use the spectrophotometric distance of 2.38 kpc (cite: Moises2011MNRAS) instead of the kinematic distance of 1.7 kpc used by several authors before." (Results); distance from Spectrophotometric distance (cite: Moises2011MNRAS)  
  > "the high-mass young stellar object (HMYSO) G345.4938+01.4677" (Abstract); "R.A.=16$^{\rm h}$59$^{\rm m}$41.63s, decl.=$-40\ensuremath{^\circ}03\ensuremath{'}43.5\ensuremath{''}$ (ICRS)" (Observations.); "For this work, we use the spectrophotometric distance of 2.38 kpc (cite: Moises2011MNRAS) instead of the kinematic distance of 1.7 kpc used by several authors before." (Results)
- Target **Source 10a**: coordinates R.A. 16h59m41.6430s, decl. -40°03'43.853'' (ICRS)  
  > "| Source 10a | 41.6430s | 43.853$''$ | $0.403\pm0.06$ |  unresolved | $0.39\pm0.1$ |" (Table 3); "|  | (16$^{\rm h}$:59$^{\rm m}$:) | ($-40$$^\circ$:03$'$:) | (mJy) | (mas $\times$ mas, $^\circ$) | (mJy) |" (Table 3); "| Source | R.A. | Decl. | Flux | Deconvolved size | Integrated |" (Table 3); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00385.S
- bands: Band 6 (~1.3 mm)  
  > "Observations of G345.49+1.47 were taken using the ALMA Band 6" (Observations.); "We focus our analysis on the 1875 MHz wide SpW centered at 222.75 GHz ($\sim1.3$ mm)." (Observations.)
- frequencies and spectral setup: SpW centers: 219.54, 220.41, 220.43, 222.75, 224.72 GHz; widths: 1875, 234.4, 234.4, 1875, 234.4 MHz; H38β channels 1.32 km s^-1, resolution 2.64 km s^-1  
  > "in five spectral windows (SpWs) centered at the frequencies of 219.54, 220.41, 220.43, 222.75, and 224.72 GHz and covering 1875, 234.4, 234.4, 1875, and 234.4 MHz, respectively." (Observations.); "The velocity width of the channels covering the H38$\beta$ line is 1.32 km s$^{-1}$, and the spectral resolution of the data cubes is 2.64 km s$^{-1}$." (Observations.)
- continuum bandwidth: 1875 MHz SpW; continuum determined from line-free channels  
  > "Continuum images of the 1875 MHz SpW were obtained with the task `tclean`" (Observations.); "A continuum level was determined from the calibrated uv-data from the line-free channels of the SpW and subtracted using the task `uvcontsub`." (Observations.)
- arrays: 12m-array single pointing; 46 and 44 antennae  
  > "12m-array single pointing" (Observations.); "| 6              | 46             | 222.747        | 116.5          | 08-07-2019     | 2624                    | 18.5           | 1.12           | 85             |" (Table 1); "| 6              | 44             | 222.747        | 111.4          | 09-07-2017     | 2622                    | 19.9           | 1.12           | 75             |" (Table 1)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ≈22 mas (52 au)  
  > "high-angular resolution ($\approx22$ mas, equivalent to 52 au)" (Introduction.)
- max recoverable scale: 1.12'' in both sessions  
  > "| 6              | 46             | 222.747        | 116.5          | 08-07-2019     | 2624                    | 18.5           | 1.12           | 85             |" (Table 1); "| 6              | 44             | 222.747        | 111.4          | 09-07-2017     | 2622                    | 19.9           | 1.12           | 75             |" (Table 1)
- sensitivity: _not stated_
- time on source: 2624 s and 2622 s  
  > "| 6              | 46             | 222.747        | 116.5          | 08-07-2019     | 2624                    | 18.5           | 1.12           | 85             |" (Table 1); "| 6              | 44             | 222.747        | 111.4          | 09-07-2017     | 2622                    | 19.9           | 1.12           | 75             |" (Table 1)
- observing dates: 8 and 9 July 2019 (UT) in text; Table 1 prints 08-07-2019 and 09-07-2017  
  > "two sessions taken the 8th and 9th of July 2019 (UT)." (Observations.); "| 6              | 44             | 222.747        | 111.4          | 09-07-2017     | 2622                    | 19.9           | 1.12           | 75             |" (Table 1)
- pi or archival as stated: _not stated_
- Line: Hydrogen H38β (222011.75545 MHz)
- Line: SO2 (v=0) 11_{1,11} → 10_{0,10} (221965.22 MHz)
- Other facility **Gaia**: Parallax and extinction information used to assess the adopted distance  
  > "results from (cite: GAIA2018AA; GAIA2016AA) make the 2.38 kpc distance estimation more plausible" (Results); "This work has made use of data from the European Space Agency (ESA) mission *Gaia*" (Acknowledgments)
- Other facility **Red MSX Source survey database**: Survey database information  
  > "This paper made use of information from the Red MSX Source survey database" (Acknowledgments)
- Other facility **Harvard Dataverse**: Replication data, calibrated images, HRL cubes and computational routines  
  > "Calibrated images and cubes of the HRL can be found in (cite: Guzman2020Dataset_G345disk)." (Observations.); "Computational routines can be found in (cite: Guzman2020Dataset_G345disk)." (A Photoionized Disk); "Replication Data for "A photoionized accretion disk around a young high-mass star", Harvard Dataverse" (References)
- External data: Spectrophotometric distance: 2.38 kpc  
  > "For this work, we use the spectrophotometric distance of 2.38 kpc (cite: Moises2011MNRAS) instead of the kinematic distance of 1.7 kpc used by several authors before." (Results) [from (cite: Moises2011MNRAS)]
- External data: Bolometric luminosity: 1.5×10^5 L_sun  
  > "a $L_{\rm bol}=1.5\times10^5 L_\ensuremath{\odot}$ HMYSO located at 2.38 kpc (cite: Lumsden2013ApJ; Mottram2011AA; Moises2011MNRAS)." (Introduction.) [from (cite: Lumsden2013ApJ; Mottram2011AA; Moises2011MNRAS)]
- External data: 220 GHz extragalactic source counts  
  > "we extrapolate with a power-law the source counts from the survey of (cite: Mocanu2013ApJ) at 220 GHz" (Results) [from (cite: Mocanu2013ApJ)]
- External data: Gaia-field extinction values A_G=2.84 and 1.82  
  > "the low extinction levels $A_G=2.84$ and 1.82 (cite: Andrae2018AA)" (Results) [from (cite: Andrae2018AA)]
- External data: Field-source parallax distances: 1983^{+490}_{-330} and 2020^{+200}_{-160} pc  
  > "the parallax distance estimations of $1983^{+490}_{-330}$ and $2020^{+200}_{-160}$ pc (cite: Luri2018AA)" (Results) [from (cite: Luri2018AA)]
- External data: 1.2 mm dust emission and molecular clump model  
  > "from the 1.2 mm dust emission and the molecular clump model of (cite: Guzman2010ApJ)" (Results) [from (cite: Guzman2010ApJ)]
- External data: Partially optically thick free-free power-law  
  > "the power-law — characteristic of partially optically thick free-free emission — determined in (cite: Guzman2016ApJ)" (HRL and Continuum Emission) [from (cite: Guzman2016ApJ)]
- External data: 92 GHz dust-emission upper limit: 11 mJy  
  > "the upper limit on the dust emission at 92 GHz of 11 mJy set by (cite: Guzman2014ApJ)." (Accretion onto G345.49+1.47) [from (cite: Guzman2014ApJ)]
- External data: Stellar parameters used to convert luminosity into stellar mass  
  > "using the stellar parameters from (cite: Davies2011MNRAS)." (A Photoionized Disk) [from (cite: Davies2011MNRAS)]
- External data: 3 mm SO2 7_{3,5} → 8_{2,6} moment 1 map  
  > "the 3 mm SO$_2$ $7_{3,5}\rightarrow8_{2,6}$ ($E_u/k=47.8$ K) moment 1 presented in (cite: Guzman2014ApJ)." (An Oppositely Rotating Molecular Envelope) [from (cite: Guzman2014ApJ)]
- External data: Dust opacity κ_231GHz=0.00899 cm^2 gr^-1, including gas-to-dust mass ratio 100  
  > "$\kappa_{\rm 231\,GHz}=0.00899$ cm$^2$ gr$^{-1}$ is the dust opacity (cite: Ossenkopf1994AA) including a gas-to-dust mass ratio of 100." (Accretion onto G345.49+1.47) [from (cite: Ossenkopf1994AA)]
- External data: Accretion-rate lower bound: 10^-5 M_sun yr^-1  
  > "$10^{-5}$ $M_\ensuremath{\odot}$ yr$^{-1}$ (the lower bound of the accretion rate onto G345.49+1.47, (cite: Guzman2016ApJ))" (Accretion onto G345.49+1.47) [from (cite: Guzman2016ApJ)]
- External data: Gas linewidths toward IRAS 16562-3959: 4–7 km s^-1  
  > "Measurements of $\Delta v$ of the gas toward IRAS 16562$-$3959 range between 4 and 7 km s$^{-1}$ depending on the molecular tracer (cite: Guzman2018ApJS; Miettinen2006AA; Bronfman1996AAS)" (A likely binary system.) [from (cite: Guzman2018ApJS; Miettinen2006AA; Bronfman1996AAS)]
- Simulation/model as data: Thin circular ionized disk with Keplerian rotation, constant-magnitude radial motion and radial electron emission measure truncated at R_e  
  > "The model consists of a thin circular disk of ionized gas whose position, orientation, and $v_{\rm LSR}$ define five free parameters." (A Photoionized Disk); "The rotation is assumed to be Keplerian defined by a central mass, and the radial motion has a constant magnitude." (A Photoionized Disk); "The disk is characterized by a radial electron emission measure (cite: ToRA6) distribution, truncated at an external radius $R_e$." (A Photoionized Disk)
- Simulation/model as data: Simulated observations of the best-fit brightness model, with noisy and noiseless uv-data  
  > "we simulated observations of a theoretical brightness model" (Simulated observations); "the moment 1 of the `simobserve` cube including simulated observational noise into the uv-data" (Simulated observations); "the moment 1 of the `simobserve` cube deconvolved from simulated noiseless uv-data" (Simulated observations)

## Processing

### Calibration

- pipeline or manual: A priori calibration based on external calibrators by the ALMA East-Asia regional center  
  > "A priori calibration based on external calibrators was carried out by the ALMA East-Asia regional center." (Observations.)
- casa version: 5.4  
  > "Calibration and reduction of these data were done using the *Common Astronomy and Software Applications* (cite: McMullin2007ASPC) v. 5.4." (Observations.)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 8 July: J1924-2914, 2.817 Jy; 9 July: J1427-4206, 1.077 Jy; fixed at 222.75 GHz  
  > "The bandpass and primary flux calibrators for the 8th and 9th of July sessions were J1924$-$2914 and J1427$-4206$" (Observations.); "whose fluxes at 222.75 GHz were fixed at 2.817 and 1.077 Jy, respectively." (Observations.)
- flux scale uncertainty: 10%  
  > "The absolute flux calibration of ALMA in band 6 is estimated to be accurate within 10% (cite: ATH7)." (Observations.)
- self calibration: Several phase self-calibration iterations on continuum; final gain sampling 15 s; gains applied to continuum-subtracted uv-data  
  > "Several iterations of phase self-calibration were applied to the continuum, until reaching a gain calibration solution sampled every 15 s." (Observations.); "These gain tables were later applied to the continuum subtracted uv-data" (Observations.)

### Imaging

- task: tclean; multi-frequency synthesis for continuum; channel per channel for line  
  > "Continuum images of the 1875 MHz SpW were obtained with the task `tclean` using multi-frequency synthesis" (Observations.); "image cubes were synthesized following the same procedure and uv-weighting scheme as with the continuum, but channel per channel." (Observations.)
- deconvolver: _not stated_
- weighting robust: Briggs weighting, robust = 0  
  > "Briggs weighting (cite: Briggs1995PhD) using robust parameter set to 0." (Observations.)
- uv taper: _not stated_
- cell size: _not stated_
- image size: ≈39'' diameter around phase center, covering primary beam response above 0.2  
  > "The total mapped region in both continuum and line was selected to cover the region where the primary beam response is above 0.2, corresponding to a diameter of $\approx39\ensuremath{''}$ around the phase center." (Observations.)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on calibrated uv-data using line-free channels of the SpW  
  > "A continuum level was determined from the calibrated uv-data from the line-free channels of the SpW and subtracted using the task `uvcontsub`." (Observations.)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Continuum: 24×20 mas, P.A. 81.4°; H38β: 24×20 mas, P.A. 82.0°  
  > "| Continuum | ... | $24\times20$, $81.4$ | 30 | 2300 |" (Table 2); "| H38$\beta$ cube | 2.64 | $24\times20$, $82.0$ | 696 | 12 |" (Table 2)
- final rms: Continuum: 30 μJy beam^-1; H38β cube: 696 μJy beam^-1  
  > "| Continuum | ... | $24\times20$, $81.4$ | 30 | 2300 |" (Table 2); "| H38$\beta$ cube | 2.64 | $24\times20$, $82.0$ | 696 | 12 |" (Table 2); "($\mu$Jy beam$^{-1}$)" (Table 2)

### Inherited from earlier work

- Adopted spectrophotometric distance  
  > "For this work, we use the spectrophotometric distance of 2.38 kpc (cite: Moises2011MNRAS)" (Results) [from (cite: Moises2011MNRAS)]
- Definition of integrated HRL optical depth  
  > "$\mathcal{T}_L$ is defined in (cite: Guzman2014ApJ)" (HRL and Continuum Emission) [from (cite: Guzman2014ApJ)]
- T_e=7000 K for the source's Galactocentric distance  
  > "Hereafter, we will use $T_e=7000$ K which is adequate for HII regions located at the Galactocentric distance of G345.49+1.47 (cite: Paladini2004MNRAS)." (HRL and Continuum Emission) [from (cite: Paladini2004MNRAS)]
- Keplerian disk emission model used for G17.64+0.16  
  > "a simple model for the emission is that of a Keplerian disk as used in G17.64+0.16 by (cite: Maud2018AA)." (A Photoionized Disk) [from (cite: Maud2018AA)]
- Voigt HRL profile with thermal Gaussian and collisional Lorentz broadening  
  > "the shape of an HRL is a Voigt profile, defined as the convolution of a Gaussian with a thermal width and a Lorentz profile with width parameter given by (cite: Gordon2009ASSL)." (A Photoionized Disk) [from (cite: Gordon2009ASSL)]
- Spatial convolution of model diagnostics  
  > "we calculate the simulated spectrum, moment 1, and pv-diagram and convolved them with the spatial resolution (cite: Richer1991MNRAS)." (A Photoionized Disk) [from (cite: Richer1991MNRAS)]
- Stellar luminosity-to-mass conversion  
  > "using the stellar parameters from (cite: Davies2011MNRAS)." (A Photoionized Disk) [from (cite: Davies2011MNRAS)]
- Inclination constraint from jet-lobe proper motion compared with stellar escape velocity  
  > "(cite: Guzman2016ApJ), by comparing the jet lobes’ proper motion velocity with the escape velocity of the star" (A Photoionized Disk); "using this same argument, we obtain $i<160\ensuremath{^\circ}$." (A Photoionized Disk) [from (cite: Guzman2016ApJ)]
- Alternative disk-width prescription w_d(r)=2H(r)  
  > "Models A.1 shows the best-fit results assuming that the disk width increases with radius as $w_d(r)=2H(r)$, with $H(r)$ as in the prescription of (cite: Hollenbach1994ApJ)." (Disk Models with Different Parameters) [from (cite: Hollenbach1994ApJ)]
- Pressure-driven wind Mach-number prescription  
  > "the Mach number at a distance $R$ from the origin is given by (cite: Lamers1999CUP)" (Expansion of the HC HII Region and Photo-Ionized Wind.) [from (cite: Lamers1999CUP)]
- Dust opacity and gas-to-dust mass ratio  
  > "$\kappa_{\rm 231\,GHz}=0.00899$ cm$^2$ gr$^{-1}$ is the dust opacity (cite: Ossenkopf1994AA) including a gas-to-dust mass ratio of 100." (Accretion onto G345.49+1.47) [from (cite: Ossenkopf1994AA)]
- Dust-sublimation temperature constraint  
  > "considering that $T_d$ should be less than the dust sublimation temperature (cite: Kama2009AA)" (Accretion onto G345.49+1.47) [from (cite: Kama2009AA)]
- Binary orbital-energy versus stellar-encounter-energy criterion  
  > "we compare the orbital energy of the purported binary with the average energy of stellar encounters (cite: gady)." (A likely binary system.) [from (cite: gady)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel selections and uvcontsub fit order.
- Observed-image pixel size, pixel dimensions, CLEAN masks, stopping thresholds and deconvolver.
- Full self-calibration iteration sequence, solution intervals before 15 s, reference antenna and solution acceptance settings.
- Whether and how primary-beam correction was applied.
- Explicit radial emission-measure functional form and normalization convention.
- Exact objective-function construction across spectrum, moment 1 and position–velocity diagnostics, including covariance treatment.
- Fit initialization, parameter bounds, convergence settings and confidence-interval convention.
- Exact jet-orientation measurements used to fix P.A. and determine the near side.

## Analysis recipe

1. **Produce continuum and line images**: Subtract continuum in uv-data; image continuum with multi-frequency synthesis; phase self-calibrate; transfer gains and image line channel by channel  
  > "A continuum level was determined from the calibrated uv-data from the line-free channels of the SpW and subtracted using the task `uvcontsub`." (Observations.); "Continuum images of the 1875 MHz SpW were obtained with the task `tclean` using multi-frequency synthesis" (Observations.); "These gain tables were later applied to the continuum subtracted uv-data, from where image cubes were synthesized following the same procedure and uv-weighting scheme as with the continuum, but channel per channel." (Observations.)
   - software: CASA, uvcontsub, tclean
   - parameter: Briggs robust = 0  
  > "Briggs weighting (cite: Briggs1995PhD) using robust parameter set to 0." (Observations.)
   - parameter: Final phase self-calibration gain sampling: 15 s  
  > "Several iterations of phase self-calibration were applied to the continuum, until reaching a gain calibration solution sampled every 15 s." (Observations.)
   - fitting: _not stated_
   - validation: Final continuum and H38β image dynamic ranges: 2300 and 12  
  > "| Continuum | ... | $24\times20$, $81.4$ | 30 | 2300 |" (Table 2); "| H38$\beta$ cube | 2.64 | $24\times20$, $82.0$ | 696 | 12 |" (Table 2)
2. **Measure continuum sources**: Fit a 2D Gaussian to the HMYSO continuum and measure aperture-integrated fluxes  
  > "We fit a 2D Gaussian to the continuum emission using the task `imfit` within CASA." (Results); "We integrate the intensity within 0.3$''$ around G345.49+1.47" (Results)
   - software: CASA, imfit
   - parameter: Apertures: within 0.3'' for G345.49+1.47; within 50 mas for Source 10a  
  > "Within 0.3$''$ for G345.49+1.47 and within 50 mas for 10a." (Table 3)
   - fitting: 2D Gaussian using imfit  
  > "We fit a 2D Gaussian to the continuum emission using the task `imfit` within CASA." (Results)
   - validation: Source 10a detected with SNR >6.5; extended continuum may be partially filtered  
  > "we are able to detect it with a SNR $>6.5$." (Results); "likely are being partially filtered." (Results)
3. **Measure ionized-gas kinematics**: Extract H38β spectrum, construct thresholded moment 1 map and beam-averaged position–velocity diagram, and measure velocity gradient  
  > "the H38$\beta$ spectrum integrated in a circle of 50 mas around G345.49+1.47." (Results); "The position velocity diagram shows the average intensity over one beam width across a P.A.$=10\ensuremath{^\circ}$ line centered on the position of G345.49+1.47" (Results); "We measure a velocity gradient in the P.A.$=11\ensuremath{^\circ}$ direction" (Results)
   - parameter: Moment 1: -58 ≤ v_LSR ≤ +35 km s^-1; emission above 4.5σ; line wings excluded  
  > "$-58\le v_{\rm LSR}(\text{km s}^{-1})\le+35$, including only emission above $4.5\sigma$ and excluding the line wings." (Results)
   - parameter: Position–velocity cut: P.A. 10°, averaged over one beam width  
  > "The position velocity diagram shows the average intensity over one beam width across a P.A.$=10\ensuremath{^\circ}$ line" (Results)
   - fitting: _not stated_
   - validation: 4.5σ threshold suppresses SO2 absorption; velocity-map statistical uncertainty 2.7–3.8 km s^-1  
  > "This threshold allows us to negate the influence of the SO$_2$ absorption affecting the red-shifted slope of the line." (Results); "The statistical uncertainty derived of the velocity map ranges between $2.7$–$3.8$ km s$^{-1}$" (Results)
4. **Separate free-free and dust continuum**: Use the LTE H38β line-to-continuum equivalent width to infer free-free emission; assign continuum excess to thermal dust  
  > "we can use the H38$\beta$ line to estimate the free-free contribution to the observed continuum emission." (HRL and Continuum Emission); "we can derive the LTE ratio between the integrated line flux to the free-free continuum." (HRL and Continuum Emission); "we propose that the excess continuum emission relative to that inferred from the HRL arises from thermal dust emission." (HRL and Continuum Emission)
   - parameter: Observed integrated line-to-continuum ratio: 9.84±0.2 km s^-1  
  > "the integrated line flux to continuum ratio in G345.49+1.47 is $9.84\pm0.2$ km s$^{-1}$" (HRL and Continuum Emission)
   - assumption: LTE; electron density high enough for collisional thermalization  
  > "We argue that LTE should be a reasonable approximation in G345.49+1.47 because the electron density is high enough to ensure thermalization via collisions." (HRL and Continuum Emission)
   - assumption: T_e=7000 K  
  > "Hereafter, we will use $T_e=7000$ K" (HRL and Continuum Emission)
   - assumption: Free-free emission at 220 GHz likely optically thin  
  > "it is likely that the free-free emission at 220 GHz from the HC HII region is already optically thin." (HRL and Continuum Emission)
   - fitting: _not stated_
   - validation: Derived dust emission compared with the 92 GHz upper limit and observed dust mm spectral-index ranges  
  > "Considering that the dust emission estimated by (cite: Guzman2014ApJ) at 92 GHz is $\le11$ mJy" (HRL and Continuum Emission); "the derived 220 GHz dust emission is consistent with the observed ranges of dust mm spectral indices (cite: Orozco2017ApJ)." (HRL and Continuum Emission)
5. **Fit an ionized rotating disk**: Fit a thin ionized disk with Keplerian rotation and constant radial motion using spatially convolved spectrum, moment 1 and position–velocity diagnostics  
  > "The model consists of a thin circular disk of ionized gas" (A Photoionized Disk); "The rotation is assumed to be Keplerian defined by a central mass, and the radial motion has a constant magnitude." (A Photoionized Disk); "we calculate the simulated spectrum, moment 1, and pv-diagram and convolved them with the spatial resolution (cite: Richer1991MNRAS)." (A Photoionized Disk)
   - software: Minuit, Perl Data Language
   - parameter: Fixed M_star=33 M_sun, P.A.=100°, T_e=7000 K  
  > "| $M_\star$ | $33$ $M_\ensuremath{\odot}$(fixed) |  |" (Table 4); "| P.A. | $100\ensuremath{^\circ}$ (fixed) |  |" (Table 4); "| $T_e$ | $7000$ K (fixed) |  |" (Table 4)
   - assumption: Disk axis consistent with jet direction; angular momentum points toward observer, i>90°  
  > "We will consider models in which the axis of the disk is consistent with the jet direction and rotation" (A Photoionized Disk); "$\vec{\ell}$ points toward us (that is, $\vec{\ell}\cdot\hat{z}<0$ or $i>90^\circ$)." (A Photoionized Disk)
   - assumption: Radial electron emission measure truncated at R_e; n_e=sqrt(EM(r)/w_d)  
  > "The disk is characterized by a radial electron emission measure (cite: ToRA6) distribution, truncated at an external radius $R_e$." (A Photoionized Disk); "n_e= \sqrt{\frac{{\rm EM}(r)}{w_d}}" (A Photoionized Disk)
   - assumption: Voigt HRL profile; H38β Lorentz width 8.75 n_e,8 km s^-1, n_e,8 in 10^8 cm^-3  
  > "the shape of an HRL is a Voigt profile" (A Photoionized Disk); "For H38$\beta$, the Lorentz width parameter is $8.75\,n_{e,8}$ km s$^{-1}$, where $n_{e,8}$ is the electron density in units of $10^8$ cm$^{-3}$." (A Photoionized Disk)
   - fitting: Minimize squared model-data differences weighted by inverse data variance; Minuit in PDL calculates minimization and statistical errors  
  > "We calculate the difference between the convolved model and the data, and minimize the squared difference weighted by the inverse variance of the data." (A Photoionized Disk); "The minimization and errors were calculated using the Minuit package (cite: MINUIT1975), as implemented in the Perl Data Language." (A Photoionized Disk); "Error bars in Table [4](#tab:fit) represent statistical uncertainties." (A Photoionized Disk)
   - validation: Inspect residuals; test masses 15 and 56 M_sun, radius-dependent width and P.A.=120° alternatives  
  > "the pv-diagram shows some negative residuals (overestimation of the model) at the $\sim3\sigma$ level." (A Photoionized Disk); "Models A.2 and A.3 show the best-fit models assuming a mass of 15 and 56 $M_\ensuremath{\odot}$" (Disk Models with Different Parameters); "Models A.4 to A.6 show the fitted model with the same masses as in models A1 to A3, but with P.A.$=120$$^\circ$." (Disk Models with Different Parameters)
6. **Check interferometric model distortions**: Simulate observations of the theoretical brightness model with execution-block antenna configurations and matching LST coverage; deconvolve with the original imaging parameters  
  > "We created the configuration antenna file for the two execution blocks of our observations using the `buildConfigurationFile` task of the CASA extensions" (Simulated observations); "using the same LST range as with our visibilities, we run `simobserve` to create the simulated measurement sets." (Simulated observations); "We restored the cubes to the image plane and deconvolved the simulated datacubes using the task `tclean` with the same parameters as described in Section 2." (Simulated observations)
   - software: CASA, CASA extensions, buildConfigurationFile, simobserve, tclean
   - parameter: At least around 200 channels; 11,000×11,000 pixels per channel  
  > "Given the width of the HRL, this process requires generating cubes of around 200 channels wide at least." (Simulated observations); "creating large cubes of $11,000\times 11,000$ pixels per channel." (Simulated observations)
   - assumption: Best-fit disk brightness model  
  > "simulated observations of the best-fit model whose parameters are in Table [4](#tab:fit)." (Simulated observations)
   - fitting: Simulations excluded from optimization because of computational cost  
  > "Partly because of this computational cost, we decided not to implement this approach in the optimization steps." (Simulated observations)
   - validation: Compare simulated moment 1 maps with observations and clean-beam convolution; curvature better preserved, with noise-threshold dependence  
  > "the main finding being that the -shape feature is slightly better preserved compared with the simple convolution." (A Photoionized Disk); "this depends somewhat on the noise level up to which we can effectively calculate the moment 1" (Simulated observations)
7. **Compare molecular and ionized rotation**: Calculate SO2 11_{1,11}→10_{0,10} moment 1 and compare with the published 3 mm SO2 map and H38β rotation  
  > "The SO$_2$ $11_{1,11}\rightarrow 10_{0,10}$ moment 1 image was calculated using the CASA task `immoments`" (An Oppositely Rotating Molecular Envelope); "the 3 mm SO$_2$ $7_{3,5}\rightarrow8_{2,6}$ ($E_u/k=47.8$ K) moment 1 presented in (cite: Guzman2014ApJ)." (An Oppositely Rotating Molecular Envelope); "it seems to run opposite to the rotation pattern of H38$\beta$." (An Oppositely Rotating Molecular Envelope)
   - software: CASA, immoments
   - parameter: -36 to 12 km s^-1; emission above 2σ  
  > "between $-36$ and $12$ km s$^{-1}$ and considering only emission above the 2$\sigma$ level." (An Oppositely Rotating Molecular Envelope)
   - fitting: _not stated_
   - validation: Molecular moment 1 broadly agrees with the 3 mm velocity pattern, despite severe missing-short-baseline filtering  
  > "our data is heavily filtered out due to the lack of short baseline coverage" (An Oppositely Rotating Molecular Envelope); "the moment 1 shows a velocity pattern roughly consistent with that traced by SO$_2$ at 3 mm" (An Oppositely Rotating Molecular Envelope)
8. **Assess confinement and wind driving**: Compare ionized-region size with the Bondi-Parker radius and fitted wind speed with a pressure-driven wind prediction  
  > "r_{\!\scriptscriptstyle B}= \frac{GM_\star }{2a^2}" (Expansion of the HC HII Region and Photo-Ionized Wind.); "the ionized region we are probing likely lies inside the Bondi radius." (Expansion of the HC HII Region and Photo-Ionized Wind.); "We therefore rule out this wind coming from pressure driven expansion." (Expansion of the HC HII Region and Photo-Ionized Wind.)
   - parameter: Wind comparison at R≈50 au  
  > "at distances comparable with the size of the disk $R\approx 50$ au" (Expansion of the HC HII Region and Photo-Ionized Wind.)
   - assumption: Ionized-gas sound speed a=9.08 km s^-1 sqrt(T_e/10^4 K)  
  > "$a = 9.08~\text{km~s$^{-1}$}\sqrt{T_e/10^4~{\rm K}}$ is the sound speed of the ionized gas" (Expansion of the HC HII Region and Photo-Ionized Wind.)
   - fitting: _not stated_
   - validation: Pressure-driven prediction M=0.20 is at least five times below the inferred transonic wind  
  > "which is lower by a factor of at least $5$ compared with the derived $\mathcal{M}\gtrsim1$." (Expansion of the HC HII Region and Photo-Ionized Wind.)
9. **Constrain disk mass and accretion supply**: Estimate ionized mass from electron density; constrain circumstellar mass and dust temperature using continuum excess, the 92 GHz upper limit and a homogeneous dust-emission model  
  > "First, the ionized mass in the disk is negligible, reaching only about $8\times10^{-6}$ $M_\ensuremath{\odot}$" (Accretion onto G345.49+1.47); "We can constrain the circumstellar mass of G345.49+1.47 by using the continuum excess over the free-free" (Accretion onto G345.49+1.47); "S_\nu=\Omega B_\nu(T_d)\left(1-\exp\left(-\frac{\kappa_\nu M}{\Omega d^2}\right)\right)" (Accretion onto G345.49+1.47)
   - parameter: 220 GHz dust excess 119 mJy; 92 GHz upper limit 11 mJy  
  > "This dust emission contribution is about $119$ mJy." (HRL and Continuum Emission); "the upper limit on the dust emission at 92 GHz of 11 mJy set by (cite: Guzman2014ApJ)." (Accretion onto G345.49+1.47)
   - parameter: Accretion-rate comparison: 10^-5 M_sun yr^-1  
  > "$10^{-5}$ $M_\ensuremath{\odot}$ yr$^{-1}$ (the lower bound of the accretion rate onto G345.49+1.47, (cite: Guzman2016ApJ))" (Accretion onto G345.49+1.47)
   - assumption: Homogeneous dust source; Ω≈3×10^-3 arcsec^2  
  > "we assume that the thermal dust emission comes from an homogeneous source covering a solid angle $\Omega\approx 3\times 10^{-3}$ arcsec$^2$" (Accretion onto G345.49+1.47)
   - assumption: κ_nu ∝ nu^β; β=1.7; κ_231GHz=0.00899 cm^2 gr^-1; gas-to-dust mass ratio 100  
  > "The dust opacity is given by $\kappa_\nu\propto \nu^\beta$ with $\beta=1.7$" (Accretion onto G345.49+1.47); "$\kappa_{\rm 231\,GHz}=0.00899$ cm$^2$ gr$^{-1}$ is the dust opacity (cite: Ossenkopf1994AA) including a gas-to-dust mass ratio of 100." (Accretion onto G345.49+1.47)
   - assumption: Dust temperature below sublimation temperature  
  > "considering that $T_d$ should be less than the dust sublimation temperature (cite: Kama2009AA)" (Accretion onto G345.49+1.47)
   - assumption: Mean mass per electron μ_e=1.3 m_H for fully ionized HII and HeI region  
  > "$\mu_e=1.3 m_{\rm H}$ (the mean mass per electron in a fully ionized HII and HeI region)." (Accretion onto G345.49+1.47)
   - fitting: _not stated_
   - validation: Use both frequency constraints; compare supply lifetime with jet-phase duration; no clear molecular disk counterpart  
  > "Taking into account the flux limit at both frequencies" (Accretion onto G345.49+1.47); "a time comparable with estimations of the jet phase duration (cite: Purser2016MNRAS; Guzman2012ApJ)." (Accretion onto G345.49+1.47); "we found no clear molecular counterpart of this disk in the rest of the frequency coverage of our data." (Accretion onto G345.49+1.47)
10. **Assess Source 10a membership and binarity**: Extrapolate extragalactic source counts; deproject separation; compare binary binding energy with typical stellar-encounter energy  
  > "we extrapolate with a power-law the source counts from the survey of (cite: Mocanu2013ApJ) at 220 GHz" (Results); "we correct this distance by $4/\pi$ assuming a random orientation between these sources, obtaining 880 au." (A likely binary system.); "we compare the orbital energy of the purported binary with the average energy of stellar encounters (cite: gady)." (A likely binary system.)
   - parameter: Projected separation 690 au; corrected separation 880 au; M=33 M_sun  
  > "Source 10a is at a projected separation of 690 au from G345.49+1.47" (A likely binary system.); "Using $r=880$ au and $M=33$ $M_\ensuremath{\odot}$" (A likely binary system.)
   - parameter: Adopted gas linewidth Δv=5.5 km s^-1; σ_3D=4.05 km s^-1  
  > "we use $\Delta v=5.5$ km s$^{-1}$(or $\sigma_{\!\scaleto{3D}{4.5pt}}=\sqrt{3}\Delta v/2.35 = 4.05$ km s$^{-1}$) as an average value." (A likely binary system.)
   - assumption: Random relative orientation for separation correction  
  > "assuming a random orientation between these sources" (A likely binary system.)
   - assumption: Young-star 3D velocity dispersion equals observed gas velocity dispersion  
  > "we assume that the 3D velocity dispersion $\sigma$ of the young stars is the same as the observed velocity dispersion of the gas." (A likely binary system.)
   - assumption: Source 10a mass comparable to typical individual stellar mass in the clump; gas-potential perturbations ignored  
  > "the mass of Source 10a is comparable to the typical individual mass of the stellar component" (A likely binary system.); "Since the distances involved are small compared with the clump size, we ignore the perturbing effect of the gas mass potential." (A likely binary system.)
   - fitting: _not stated_
   - validation: Expected extragalactic contamination ≲6×10^-3 sources per primary beam; orbital speed exceeds adopted stellar dispersion  
  > "$\lesssim6\times10^{-3}$ sources within the primary beam of our observations." (Results); "the orbital velocity is 5.8 km s$^{-1}$, larger than $\sigma_{\!\scaleto{3D}{4.5pt}}=4.05$ km s$^{-1}$." (A likely binary system.)

## Software

- **CASA** 5.4: Calibration and reduction  
  > "Calibration and reduction of these data were done using the *Common Astronomy and Software Applications* (cite: McMullin2007ASPC) v. 5.4." (Observations.)
- **uvcontsub** : Continuum subtraction in calibrated uv-data  
  > "A continuum level was determined from the calibrated uv-data from the line-free channels of the SpW and subtracted using the task `uvcontsub`." (Observations.)
- **tclean** : Continuum imaging and deconvolution of simulated cubes  
  > "Continuum images of the 1875 MHz SpW were obtained with the task `tclean`" (Observations.); "deconvolved the simulated datacubes using the task `tclean` with the same parameters as described in Section 2." (Simulated observations)
- **imfit** : 2D Gaussian continuum fit  
  > "We fit a 2D Gaussian to the continuum emission using the task `imfit` within CASA." (Results)
- **immoments** : SO2 moment 1 image  
  > "The SO$_2$ $11_{1,11}\rightarrow 10_{0,10}$ moment 1 image was calculated using the CASA task `immoments`" (An Oppositely Rotating Molecular Envelope)
- **Minuit** : Disk-model minimization and error calculation  
  > "The minimization and errors were calculated using the Minuit package (cite: MINUIT1975), as implemented in the Perl Data Language." (A Photoionized Disk)
- **Perl Data Language (PDL)** : Analysis and implementation of Minuit fitting  
  > "The minimization and errors were calculated using the Minuit package (cite: MINUIT1975), as implemented in the Perl Data Language." (A Photoionized Disk)
- **simobserve** : Simulated measurement sets from the theoretical brightness model  
  > "using the same LST range as with our visibilities, we run `simobserve` to create the simulated measurement sets." (Simulated observations)
- **CASA extensions** : Execution-block antenna configuration files  
  > "We created the configuration antenna file for the two execution blocks of our observations using the `buildConfigurationFile` task of the CASA extensions" (Simulated observations)
- **buildConfigurationFile** : Antenna configuration files for the two execution blocks  
  > "We created the configuration antenna file for the two execution blocks of our observations using the `buildConfigurationFile` task of the CASA extensions" (Simulated observations)
- **Red MSX Source survey database** : Survey information  
  > "This paper made use of information from the Red MSX Source survey database" (Acknowledgments)
- **Harvard Dataverse** : Distribution of replication products and computational routines  
  > "Calibrated images and cubes of the HRL can be found in (cite: Guzman2020Dataset_G345disk)." (Observations.); "Computational routines can be found in (cite: Guzman2020Dataset_G345disk)." (A Photoionized Disk); "Replication Data for "A photoionized accretion disk around a young high-mass star", Harvard Dataverse" (References)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| G345.49+1.47 Gaussian continuum flux density | 165.6 | ±1 | mJy | 2 | / G345.49+1.47 / 41.6264s / 43.641$''$ / $165.6\pm1$ / $35.93\pm0.3\times16.32\pm0.2$, $86.8\pm1$ / $173\pm1$ / |
| G345.49+1.47 aperture-integrated continuum flux density | 173 | ±1 | mJy | 2 | / G345.49+1.47 / 41.6264s / 43.641$''$ / $165.6\pm1$ / $35.93\pm0.3\times16.32\pm0.2$, $86.8\pm1$ / $173\pm1$ / |
| G345.49+1.47 deconvolved continuum major axis | 35.93 | ±0.3 | mas | 2 | $35.93\pm0.3\times16.32\pm0.2$, $86.8\pm1$ |
| G345.49+1.47 deconvolved continuum minor axis | 16.32 | ±0.2 | mas | 2 | $35.93\pm0.3\times16.32\pm0.2$, $86.8\pm1$ |
| G345.49+1.47 deconvolved continuum position angle | 86.8 | ±1 | ° | 2 | $35.93\pm0.3\times16.32\pm0.2$, $86.8\pm1$ |
| Source 10a continuum flux density | 0.403 | ±0.06 | mJy | 2 | / Source 10a / 41.6430s / 43.853$''$ / $0.403\pm0.06$ /  unresolved / $0.39\pm0.1$ / |
| Source 10a aperture-integrated flux density | 0.39 | ±0.1 | mJy | 2 | / Source 10a / 41.6430s / 43.853$''$ / $0.403\pm0.06$ /  unresolved / $0.39\pm0.1$ / |
| H38β integrated-spectrum width | 58.4 | ±1 | km s^-1 | 3 | The HRL is characterized by a width of $58.4\pm1$ km s$^{-1}$ |
| H38β integrated-spectrum central velocity | -11.0 | ±1 | km s^-1 | 3 | is centered around $-11.0\pm1$ km s$^{-1}$ |
| H38β total line flux | 1.629 | ±0.03 | Jy km s^-1 | 3 | has a total flux of $W_L=1.629\pm0.03$ Jy km s$^{-1}$. |
| H38β peak line flux | 8.12 | not stated | mJy beam^-1 | 3 | The line flux peaks at $8.12$ mJy beam$^{-1}$ ($T_B\approx420$ K). |
| H38β velocity gradient at P.A. 11° | +1.13 | not stated | km s^-1 mas^-1 | 3 | We measure a velocity gradient in the P.A.$=11\ensuremath{^\circ}$ direction of $+1.13$ km s$^{-1}$ mas$^{-1}$ |
| H38β physical velocity gradient at 2.38 kpc | +0.47 | not stated | km s^-1 au^-1 | 3 | ($+0.47$ km s$^{-1}$ au$^{-1}$ at 2.38 kpc). |
| Integrated line-to-continuum ratio | 9.84 | ±0.2 | km s^-1 | 4 | the integrated line flux to continuum ratio in G345.49+1.47 is $9.84\pm0.2$ km s$^{-1}$ |
| Dust continuum contribution | 119 | not stated | mJy | 4 | This dust emission contribution is about $119$ mJy. |
| Stellar mass derived from bolometric luminosity | 33 | not stated | M_sun | 5 | we derive that the mass of this HMYSO is $M_\star=33$ $M_\ensuremath{\odot}$ using the stellar parameters from (cite: Davies2011MNRAS). |
| Disk-model systemic velocity | -11.78 | ±0.4 | km s^-1 | 5 | / $v_{\rm LSR}$ / $-11.78\pm0.4$ km s$^{-1}$ /  / |
| Disk-model log(EM), with EM in cm^-6 pc | 11.504 | ±0.05 | dimensionless | 5 | / $\log({\rm EM})$$^{\scriptsize\dag}$ / $11.504\pm0.05$ /  /; EM units: cm$^{-6}$ pc. |
| Disk-model inclination | 144.8 | ±0.1 | ° | 5 | / $i$ / $144.8\ensuremath{^\circ}\pm0.1$$^\circ$ /  / |
| Disk-model external radius | 52 | ±0.1 | au | 5 | / $R_e$ / $52\pm0.1$ au /  / |
| Disk-model radial expansion speed | 10.9 | ±3 | km s^-1 | 5 | / $V_{\rm exp}$ / $10.9\pm3$ km s$^{-1}$ /  / |
| Disk-model width | 5.39 | ±1 | au | 5 | / $w_d$ / $5.39\pm1$ au /  / |
| Inclination span under luminosity-consistent stellar masses | at least ±20 | not stated | ° | 5 | a range of inclinations which span at least $\pm 20\ensuremath{^\circ}$ around the best-fit value |
| Bondi radius for fiducial best-fit parameters | 178 | not stated | au | 8 | $r_{\!\scriptscriptstyle B}=$178 au. |
| Bondi radius reported for 15 M_sun lower-mass case | 115 | not stated | au | 8 | we obtain $r_{\!\scriptscriptstyle B}=115$ au. |
| Inferred radial-wind Mach number | ≳1 | not stated | dimensionless | 8 | The best-fit parameters of this wind indicate it is transonic, with Mach number $\mathcal{M}\gtrsim1$. |
| Ionized disk mass | 8×10^-6 | not stated | M_sun | 9 | First, the ionized mass in the disk is negligible, reaching only about $8\times10^{-6}$ $M_\ensuremath{\odot}$ |
| Circumstellar disk mass range | 0.3–1.0 | not stated | M_sun | 9 | A disk mass of 0.3–1.0 $M_\ensuremath{\odot}$ |
| Dust temperature constraint | 1500 ≥ T_d ≥ 960 | not stated | K | 9 | $1500\,{\rm K}\ge T_d \ge 960\,{\rm K}$ |
| Accretion supply duration at 10^-5 M_sun yr^-1 | 30,000–100,000 | not stated | yr | 9 | for 30,000–100,000 yr, a time comparable with estimations of the jet phase duration |
| Expected extragalactic sources within primary beam as bright as Source 10a | ≲6×10^-3 | not stated | sources | 10 | $\lesssim6\times10^{-3}$ sources within the primary beam of our observations. |
| Source 10a projected separation | 690 | not stated | au | 10 | Source 10a is at a projected separation of 690 au from G345.49+1.47 |
| Orientation-corrected binary separation | 880 | not stated | au | 10 | we correct this distance by $4/\pi$ assuming a random orientation between these sources, obtaining 880 au. |
| Binary orbital velocity | 5.8 | not stated | km s^-1 | 10 | the orbital velocity is 5.8 km s$^{-1}$ |

## Qualitative findings

- H38β traces an ionized disk rotating perpendicular to the ionized jet  
  > "The H38$\beta$ HRL reveals a $\sim100$ au ionized disk around G345.49+1.47, rotating perpendicularly to the previously detected ionized jet." (Conclusions.)
- Ionized-gas rotation is opposite to larger-scale sulfur-oxide rotation  
  > "The sense of rotation observed in the ionized gas is opposite to that detected in sulfur oxides at larger scales." (Conclusions.)
- Current disk contributes little to final stellar mass  
  > "even if the entire disk were accreted, it would only affect minimally the mass of the HMYSO." (Accretion onto G345.49+1.47)
- Source 10a is likely a low-mass YSO and binary companion  
  > "We report in this work the detection of Source 10a, a likely low-mass YSO." (Conclusions.); "This source is probably a binary stellar companion of G345.49+1.47." (Conclusions.)

## Claim tuples

- H: A compact ionized disk survives around an HII-region-exciting high-mass young star. | E: Resolve H38β kinematics and fit an ionized rotating-disk model. | R: A ~100 au structure rotates perpendicular to the previously detected jet. | F: The ionized emission traces a surviving photoionized disk. | **supported**
- H: The ionized disk has radial expansion in addition to rotation. | E: Fit moment 1, spectrum and position–velocity diagnostics with rotation plus constant radial motion; compare alternative orientation. | R: Fiducial expansion speed is 10.9±3 km s^-1, but a differently oriented disk without expansion fits only slightly worse. | F: A transonic expanding wind is suggested, with substantial model ambiguity. | **partially**
- H: Inner ionized and larger-scale molecular gas share a rotation direction. | E: Compare H38β rotation with sulfur-oxide moment 1 maps. | R: The measured rotation senses are opposite. | F: The inner ionized structure and larger-scale sulfur-oxide structure are oppositely rotating. | **refuted**
- H: The present disk can supply substantial further stellar growth. | E: Infer dust emission and disk mass from continuum constraints; compare the reservoir with the stellar mass and accretion-rate lower bound. | R: Disk mass is 0.3–1.0 M_sun and can supply the adopted rate for 30,000–100,000 yr. | F: The present disk can sustain some accretion but adds little to the final stellar mass. | **refuted**
- H: Accretion proceeds through strong bursts separated by disk-replenishment intervals. | E: Interpret the small current reservoir together with prior jet activity and the surrounding clump. | R: The current disk is insufficient for substantial further mass growth. | F: The source may currently lie between accretion episodes. | **partially**
- H: Source 10a is a physical companion rather than contamination or an unbound neighbor. | E: Estimate background-source contamination and compare orbital speed with the assumed stellar velocity dispersion. | R: Orbital speed 5.8 km s^-1 exceeds the adopted dispersion 4.05 km s^-1. | F: G345.49+1.47 and Source 10a likely form a binary. | **partially**

## Reasoning

- Why this data: High-angular-resolution H38β and adjacent continuum probe ionized-gas dynamics around the HMYSO  
  > "High angular resolution HRL observations have been used to trace the dynamics (rotation and outflows) of ionized gas around HMYSOs" (Introduction.); "targeting the H38$\beta$ HRL and the 1.3 mm continuum emission." (Conclusions.)
- Why this method: Add radial motion to explain curvature in the systemic-velocity locus; moment 1 is more informative than the broad-line position–velocity diagram  
  > "in order to reproduce this observed feature, we include radial motions in the disk in addition to rotation." (A Photoionized Disk); "the main indication of radial motions relies on the aspect of the moment 1 map rather than that of the pv-diagram." (A Photoionized Disk)
- Alternative: Rotation without expansion at P.A.=120° gives only a slightly worse fit  
  > "a disk without expansion but inclined with P.A.$=120\ensuremath{^\circ}$ gives only a slightly worse fit" (A Photoionized Disk)
- Alternative: Alternative masses 15 and 56 M_sun and radius-dependent disk width  
  > "Models A.1 shows the best-fit results assuming that the disk width increases with radius as $w_d(r)=2H(r)$" (Disk Models with Different Parameters); "Models A.2 and A.3 show the best-fit models assuming a mass of 15 and 56 $M_\ensuremath{\odot}$" (Disk Models with Different Parameters)
- Alternative: Pressure-driven origin of fitted radial wind rejected  
  > "We therefore rule out this wind coming from pressure driven expansion." (Expansion of the HC HII Region and Photo-Ionized Wind.)
- Alternative: Stellar-wind entrainment and magneto-centrifugal acceleration considered; wind origin remains speculative  
  > "A second alternative is that this wind corresponds to photoionized gas being dragged by a stellar wind." (Expansion of the HC HII Region and Photo-Ionized Wind.); "the wind corresponds to magneto-centrifugal acceleration." (Expansion of the HC HII Region and Photo-Ionized Wind.); "the true nature of the G345.49+1.47 wind remains speculative." (Expansion of the HC HII Region and Photo-Ionized Wind.)
- Alternative: Accretion essentially ended versus future accretion after disk replenishment  
  > "(i) Accretion onto the HMYSO has essentially ended." (Accretion onto G345.49+1.47); "(ii) Accretion will resume in the future." (Accretion onto G345.49+1.47)
- Alternative: Source 10a may be close only in projection or a high-velocity fly-by young star  
  > "Alternative hypotheses are that Source 10a is far away from G345.49+1.47, and only close in projection, or that it is a high-velocity fly-by young star." (A likely binary system.)
- How they decided it was enough: About three beams resolve the velocity gradient; avoid further model sophistication; full simulated-observation optimization too costly  
  > "Considering that our current data is able to resolve the velocity gradient with about three beams across, we refrain in this work, from including additional sophistication to the model." (A Photoionized Disk); "Partly because of this computational cost, we decided not to implement this approach in the optimization steps." (Simulated observations)
- Limitation (authors): Extended emission partially filtered; molecular data heavily affected by missing short baselines  
  > "likely are being partially filtered." (Results); "our data is heavily filtered out due to the lack of short baseline coverage" (An Oppositely Rotating Molecular Envelope)
- Limitation (authors): Stellar mass and inclination are degenerate  
  > "This mass is degenerate with the inclination, resulting in higher mass estimations for smaller angles." (A Photoionized Disk)
- Limitation (authors): Table 4 errors are statistical; inclination uncertainty from mass assumptions spans at least ±20°  
  > "Error bars in Table [4](#tab:fit) represent statistical uncertainties." (A Photoionized Disk); "a range of inclinations which span at least $\pm 20\ensuremath{^\circ}$ around the best-fit value" (A Photoionized Disk)
- Limitation (authors): Disk model omits polar expansion and does not explain extended emission  
  > "expansion of the HC HII region along the polar axis" (A Photoionized Disk); "which is not included in the model." (A Photoionized Disk); "The main difficulty we have now is the disagreement between the rotating compact system and the more extended emission." (A Photoionized Disk)
- Limitation (authors): Radial-motion signatures are subtle after convolution  
  > "after convolution the effect is subtle" (A Photoionized Disk); "a disk without expansion but inclined with P.A.$=120\ensuremath{^\circ}$ gives only a slightly worse fit" (A Photoionized Disk)
- Limitation (authors): Clean-beam convolution approximates interferometric distortions; simulated observations not used during optimization  
  > "Convolving the model with the clean beam is a simple approximation of the observational distortions introduced by the interferometer." (A Photoionized Disk); "Partly because of this computational cost, we decided not to implement this approach in the optimization steps." (Simulated observations)
- Limitation (authors): Velocity gradient resolved by only about three beams  
  > "our current data is able to resolve the velocity gradient with about three beams across" (A Photoionized Disk)
- Limitation (authors): Wind origin remains speculative  
  > "the true nature of the G345.49+1.47 wind remains speculative." (Expansion of the HC HII Region and Photo-Ionized Wind.)
- Caveat (inferred, ours): Expansion is not uniquely established because changing disk P.A. produces a nearly competitive non-expanding fit.
- Caveat (inferred, ours): Statistical errors should not be used as total answer-key tolerances; mass, inclination, geometry and flux calibration introduce larger uncertainties.
- Caveat (inferred, ours): Check consistency between the displayed equivalent-width temperature law, the quoted 13.74 km s^-1 at 7000 K and the inferred 119 mJy dust excess.
- Caveat (inferred, ours): Check the printed Bondi radii against the stated equation and temperatures before using them as numerical validation targets.
- Caveat (inferred, ours): The second observing date disagrees between the narrative and Table 1.
- Caveat (inferred, ours): Binary membership lacks direct orbital or common-motion confirmation in the supplied text.
- Caveat (inferred, ours): The dust-mass range depends on an adopted opacity, solid angle, temperature ceiling and literature upper limit.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Calibrated images and HRL cubes in (cite: Guzman2020Dataset_G345disk), Harvard Dataverse, doi:10.7910/DVN/1OBDQQ  
  > "Calibrated images and cubes of the HRL can be found in (cite: Guzman2020Dataset_G345disk)." (Observations.); "Harvard Dataverse, doi:" (References); "10.7910/DVN/1OBDQQ" (References)
- Code: Computational routines in (cite: Guzman2020Dataset_G345disk)  
  > "Computational routines can be found in (cite: Guzman2020Dataset_G345disk)." (A Photoionized Disk)
- Missing: Explicit statement of public access and exact contents of the linked replication dataset.
- Missing: Exact continuum-channel selections and complete calibration and imaging scripts.
- Missing: Full disk-model prescription, fit configuration and diagnostic weighting unless supplied by the linked routines.
- Missing: Exact prior jet geometry, free-free spectral constraints and 92 GHz dust upper-limit derivation.
- Missing: Resolution of the observing-date, equivalent-width and Bondi-radius inconsistencies.
- Missing: Software dependency versions beyond CASA 5.4 and the Minuit/PDL implementation details.
- Data volume (inferred): Observed-data volume cannot be estimated reliably. The stated simulated-cube dimensions imply tens of GB per cube at minimum, with larger working storage for multiple products.
- Score (inferred): 7/5, Project code, CASA version, weighting, extraction thresholds, numerical fit results, replication products and routines are identified. Exact reduction settings and model-fitting details remain incomplete, with internal numerical inconsistencies to resolve.
- Rediscovery candidate: no, Strong candidate for reproducing numerical results from linked products and routines, but the supplied text does not explicitly establish public access and leaves important reduction and model details unresolved.

## Links

- Method: (cite: McMullin2007ASPC) (CASA calibration and reduction.)
- Method: (cite: Briggs1995PhD) (Briggs visibility weighting.)
- Method: (cite: ATH7) (Flux calibration accuracy and maximum-recoverable-scale definition.)
- Method: (cite: MINUIT1975) (Model minimization and error calculation.)
- Method: (cite: Richer1991MNRAS) (Spatial convolution of disk-model diagnostics.)
- Method: (cite: Gordon2009ASSL) (HRL pressure broadening and Voigt profiles.)
- Method: (cite: ToRA6) (Electron emission measure.)
- Method: (cite: Davies2011MNRAS) (Stellar parameters for luminosity-based mass.)
- Method: (cite: Ossenkopf1994AA) (Dust opacity used for circumstellar mass.)
- Method: (cite: Hollenbach1994ApJ) (Alternative radial disk-width prescription and photoionized-disk interpretation.)
- Method: (cite: Lamers1999CUP) (Pressure-driven wind Mach-number comparison.)
- Method: (cite: gady) (Binary binding-energy versus encounter-energy criterion.)
- Companion: (cite: Guzman2014ApJ) (Earlier sulfur-oxide rotation, electron-density constraints and 92 GHz dust upper limit.)
- Companion: (cite: Guzman2016ApJ) (Jet proper motions, geometry, free-free spectrum and accretion-rate lower bound.)
- Companion: (cite: Guzman2010ApJ) (Earlier dust emission and molecular-clump model used for the distance argument.)
- Companion: (cite: Guzman2011ApJ) (Molecular outflow and contracting clump context.)
- Companion: (cite: Guzman2018ApJS) (Molecular chemistry and gas velocity dispersion.)
- Companion: (cite: Guzman2020Dataset_G345disk) (Replication data products and computational routines.)
- Related: Red MSX Source survey
- Related: Gaia
- Related: IRAS 16562-3959

## Checks

```json
{
 "quotes": 289,
 "quotes_ok": 289,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 34,
 "numeric_problems": 0,
 "fill": {
  "facts": 167,
  "stated": 142,
  "rate": 0.85
 },
 "evidence_ok": true
}
```
