# Constraining the properties of the potential embedded planets in the disk around HD 100546

`2021A&A...656A.150P` | Astronomy and Astrophysics 2021 | first author: Pyerin, Max Ackermann | arXiv: 2110.03373 | DOI: 10.1051/0004-6361/202141998

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Constrain masses and orbital radii of potential embedded planets in the HD 100546 disk, assuming they induce the observed rings and gaps; test whether one or two planets are required  
  > "Our aim is to constrain some of the properties of potential planets embedded in the disk, assuming that they induce the observed rings and gaps." (abstract); "Particularly, we wish to determine whether one or two planets are required to explain the observed substructures and to obtain their masses and distances from the central star." (Introduction)
- Target **HD 100546**: coordinates RA 11h 33m 25.3s, Dec -70d 11' 41.2'' (Gaia EDR3)  
  > "This target is found at a distance of $108.1\pm 0.5\,$pc ((cite: gaia_edr3_2021))" (Introduction); "with a right ascension of $11^h\, 33^m\, 25.3^s$ and a declination of $-70^\circ\, 11'\, 41.2''$ ((cite: gaia_edr3_2021))" (Introduction); z/distance 108.1 +/- 0.5 pc  
  > "This target is found at a distance of $108.1\pm 0.5\,$pc ((cite: gaia_edr3_2021))" (Introduction); "with a right ascension of $11^h\, 33^m\, 25.3^s$ and a declination of $-70^\circ\, 11'\, 41.2''$ ((cite: gaia_edr3_2021))" (Introduction); distance from Gaia EDR3 (cite: gaia_edr3_2021)  
  > "This target is found at a distance of $108.1\pm 0.5\,$pc ((cite: gaia_edr3_2021))" (Introduction); "with a right ascension of $11^h\, 33^m\, 25.3^s$ and a declination of $-70^\circ\, 11'\, 41.2''$ ((cite: gaia_edr3_2021))" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00497.S, 2015.1.00806.S, 2015.1.00934.S, 2016.1.01511.S
- bands: Band 7 (0.9 mm)  
  > "ALMA observations of HD 100546 at $0.9$ mm wavelength (ALMA Band 7) under ALMA projects 2016.1.00497.S. (PI: A. Pohl) and 2015.1.00806.S (PI: J. Pineda)" (ALMA Observations / Calibration)
- frequencies and spectral setup: SB: four continuum spws centred at 336.495, 338.432, 348.494, 350.494 GHz (2 GHz each); LB: two continuum spws at 331.988 and 343.488 GHz plus two spws on 12CO(3-2) and 13CO(3-2)  
  > "the correlator was configured to observe dust continuum in its four spectral windows centered at $336.495\,$GHz, $338.432\,$GHz, $348.494\,$GHz, and $350.494\,$GHz, each with a bandwidth of $2\,$GHz" (ALMA Observations / Calibration); "the correlator was configured to observe two spectral windows with dust continuum at $331.988\,$GHz and $343.488\,$GHz, and the two remaining windows were aimed at the molecular lines $^{12}$CO ($J:3-2$) and $^{13}$CO ($J:3-2$)" (ALMA Observations / Calibration)
- continuum bandwidth: 2 GHz per continuum spw (SB and LB); 0.469 GHz for the LB line spws  
  > "The bandwidth of the dust continuum spectral windows in the LB dataset was also $2\,$GHz and $0.469\,$GHz for the remaining windows." (ALMA Observations / Calibration)
- arrays: _not stated_
- configurations: Extended (LB) and Compact (SB)  
  > "2015.1.00934.S | 2015-12-02 | 27.8 | 36 | 17.4 - 10803.7 | Extended (LB)" (Table obs_log (Observation details)); "2016.1.01511.S | 2016-10-26 | 69.4 | 43 | 15.1 - 1124.3 | Compact (SB)" (Table obs_log (Observation details))
- baselines: 17.4 - 10803.7 m (LB); 15.1 - 1124.3 m and 15.1 - 460.0 m (SB)  
  > "2015.1.00934.S | 2015-12-02 | 27.8 | 36 | 17.4 - 10803.7 | Extended (LB)" (Table obs_log (Observation details)); "2016.1.01511.S | 2016-10-26 | 69.4 | 43 | 15.1 - 1124.3 | Compact (SB)" (Table obs_log (Observation details)); "2017-04-23 | 104.1 | 44 | 15.1 - 460.0 | Compact (SB)" (Table obs_log (Observation details))
- angular resolution: Observed beam not stated; synthetic images convolved with a 0.3'' Gaussian beam 'similar to the actual observations'  
  > "all synthetic observations are convolved with a $0.3''$ Gaussian beam similar to the actual observations" (Synthetic observations with RADMC-3D)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Exp. time 27.8 min (LB, 2015-12-02); 69.4 min and 104.1 min (SB)  
  > "2015.1.00934.S | 2015-12-02 | 27.8 | 36 | 17.4 - 10803.7 | Extended (LB)" (Table obs_log (Observation details)); "2016.1.01511.S | 2016-10-26 | 69.4 | 43 | 15.1 - 1124.3 | Compact (SB)" (Table obs_log (Observation details)); "2017-04-23 | 104.1 | 44 | 15.1 - 460.0 | Compact (SB)" (Table obs_log (Observation details))
- observing dates: 2015-12-02 (LB); 2016-10-26 and 2017-04-23 (SB)  
  > "2015.1.00934.S | 2015-12-02 | 27.8 | 36 | 17.4 - 10803.7 | Extended (LB)" (Table obs_log (Observation details)); "2016.1.01511.S | 2016-10-26 | 69.4 | 43 | 15.1 - 1124.3 | Compact (SB)" (Table obs_log (Observation details)); "2017-04-23 | 104.1 | 44 | 15.1 - 460.0 | Compact (SB)" (Table obs_log (Observation details))
- pi or archival as stated: PI A. Pohl (SB, 2016.1.00497.S); PI J. Pineda (LB, 2015.1.00806.S)  
  > "ALMA observations of HD 100546 at $0.9$ mm wavelength (ALMA Band 7) under ALMA projects 2016.1.00497.S. (PI: A. Pohl) and 2015.1.00806.S (PI: J. Pineda)" (ALMA Observations / Calibration)
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Other facility **Gaia EDR3**: Distance (108.1 pc) and coordinates of HD 100546  
  > "This target is found at a distance of $108.1\pm 0.5\,$pc ((cite: gaia_edr3_2021))" (Introduction)
- External data: Distance 108.1 +/- 0.5 pc and coordinates of HD 100546  
  > "This target is found at a distance of $108.1\pm 0.5\,$pc ((cite: gaia_edr3_2021))" (Introduction) [from (cite: gaia_edr3_2021)]
- External data: Disk geometry for deprojection: inclination 45 deg, PA 150 deg  
  > "When the disk is deprojected using the geometry from (cite: casassus_2019), with an inclination of $45^\circ$ and a position angle (PA) of $150^\circ$" (Observational results: Outer ring) [from (cite: casassus_2019)]
- External data: Dust mass absorption coefficient kappa_nu = 2.3 (nu/230 GHz)^0.4 cm^2 g^-1  
  > "$\kappa_\nu=2.3 \times (\nu/230\,\rm{GHz})^{0.4}\,\rm{cm}^{2}\rm{g}^{-1}$ is the frequency-dependent mass absorption coefficient (cite: andrews2013)" (Observational results: Outer ring) [from (cite: andrews2013)]
- External data: Inner planet position of 13 au taken from earlier studies  
  > "we reverted to the estimated planet position from previous studies, specifically (cite: p15; w14), suggesting that the inner planet is located at $13\,$au." (Planet locations) [from (cite: p15; w14)]
- External data: Gap-width to planet-mass relation with K between 7 and 10  
  > "The precise relation of gap width and planet mass was studied by ((cite: Dodson_Robinson_2011; Pinilla_2012; rosotti2016; Fung_2016; 2018facchini)), yielding the dependence" (Planet mass estimates); "has been found to lie within the interval $7\leq K \leq 10$" (Planet mass estimates) [from (cite: Dodson_Robinson_2011; Pinilla_2012; rosotti2016; Fung_2016; 2018facchini)]
- External data: Minimum gap-opening planet mass criteria  
  > "following the studies of (cite: c6) and (cite: l19)" (Planet mass estimates) [from (cite: c6); (cite: l19)]
- External data: System age 4.8 Myr  
  > "which has been estimated to be $4.8\,\rm{Myr}$ ((cite: Wichittanakom_2020))" (Hydrodynamic simulations with FARGO3D) [from (cite: Wichittanakom_2020)]
- External data: Silicate composition with optical constants from the Jena database  
  > "We assumed the disk to be composed of silicates ((cite: d95))" (Synthetic observations with RADMC-3D) [from (cite: d95)]
- Simulation/model as data: 2D multifluid FARGO3D simulations (one gas and four dust fluids) of seven model setups I-VII with one or two embedded planets  
  > "We used a multifluid approach and model the gaseous dusty disk around HD 100546 as five fluids: one fluid represents the gas, and the four remaining fluids describe the dust" (Hydrodynamic simulations with FARGO3D); "Then, we executed simulations with two planets for both initial conditions (model III with the power law, and model IV with the self-similar solution)." (Parameter space exploration)
- Simulation/model as data: RADMC-3D synthetic 0.9 mm images of the FARGO3D outputs, convolved with a 0.3'' Gaussian beam  
  > "we performed a radiative transfer simulation and rendered a synthetic observation" (Synthetic observations with RADMC-3D); "all synthetic observations are convolved with a $0.3''$ Gaussian beam similar to the actual observations" (Synthetic observations with RADMC-3D)

## Processing

### Calibration

- pipeline or manual: ALMA standard pipeline calibration, then manual self-calibration in CASA  
  > "After ALMA standard pipeline calibration, we used" (ALMA Observations / Calibration); "to handle and self-calibrate the datasets" (ALMA Observations / Calibration)
- casa version: CASA 5.6.2  
  > "CASA 5.6.2" (ALMA Observations / Calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% ALMA flux uncertainty (not included in the quoted ring flux error)  
  > "We detect the ring to be $4.5\pm0.2\,$mJy, which does not include the $10\%$ ALMA flux uncertainty." (Observational results: Outer ring)
- self calibration: SB: two stages (shortest-baseline April 2017 data first, then joined with October 2016 data); phase solints 360, 150, 60, 24 s and amplitude 150 s. LB independently: phase solints 360 and 150 s, amplitude 360 s  
  > "First, we self-calibrated the shortest baseline observations, taken in April 2017, with solution intervals of $360\,$s, $150\,$s, $60\,$s, and $24\,$s for the phase calibration and $150\,$s for the amplitude calibration." (ALMA Observations / Calibration); "The LB data were self-calibrated independently from the SB data, with solution intervals of $360\,$s and $150\,$s for the phase calibration and $360\,$s for the amplitude." (ALMA Observations / Calibration)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum extracted by flagging channels within +/-25 km/s of each targeted line (line spws of LB)  
  > "we flagged the channels located at $\pm 25\,$km s$^{-1}$ from each targeted spectral line" (ALMA Observations / Calibration)
- line free channels: All channels beyond +/-25 km/s of the 12CO and 13CO lines, averaged into 125 MHz channels  
  > "we flagged the channels located at $\pm 25\,$km s$^{-1}$ from each targeted spectral line" (ALMA Observations / Calibration); "the remaining channels from all spectral windows were averaged into 125 MHz channels" (ALMA Observations / Calibration)
- primary beam correction: _not stated_
- array combination: SB and LB combined after shifting all phase centres to the LB phase centre  
  > "Before combining the datasets, we corrected their phase centers such that the center of all observations was the center of the LB dataset." (ALMA Observations / Calibration)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Channel averaging of continuum data into 125 MHz channels follows the DSHARP calibration  
  > "Similarly to the calibration of the DSHARP sources (cite: andrews2018), the remaining channels from all spectral windows were averaged into 125 MHz channels." (ALMA Observations / Calibration) [from (cite: andrews2018) DSHARP]
- JvM correction of the images  
  > "as described in (cite: jorsater1995) and also used in (cite: andrews2021)" (ALMA Observations / Calibration) [from (cite: jorsater1995); (cite: andrews2021)]
- Optically thin dust mass formula (Hildebrand)  
  > "We followed (cite: h83)," (Observational results: Outer ring) [from (cite: h83)]
- Constant dust temperature of 20 K  
  > "assuming that the flux ($F_\nu$) received at $0.9\,$mm is being emitted by dust with a constant temperature of $T=20\,$K (cite: ansdell2016; pinilla2018)" (Observational results: Outer ring) [from (cite: ansdell2016; pinilla2018)]
- Mass-tapering of the planet is a variation of the algorithm already in FARGO3D  
  > "This formula is a variation of the mass-tapering algorithm that is included in `FARGO3D`." (Mass-tapering model) [from FARGO3D (cite: b16; m0; 2019fargomulti; 2019diffusionfargo)]
- Self-similar initial gas surface density profile  
  > "The other initial condition used in this work is the self-similar solution from (cite: lynden-bell_pringle_1974)" (Initial conditions) [from (cite: lynden-bell_pringle_1974)]
- Initial dust size distribution follows an MRN distribution  
  > "following an MRN distribution ((cite: mathis_1977))" (Initial conditions) [from (cite: mathis_1977)]
- Vertical dust scale-height model  
  > "with the disk height model of (cite: d4)" (Synthetic observations with RADMC-3D) [from (cite: d4)]

### Not stated but needed to reproduce (our reading)

- The observation log table lists program IDs 2015.1.00934.S and 2016.1.01511.S while the text names 2015.1.00806.S (LB) and 2016.1.00497.S (SB); which execution blocks were actually used is unclear
- Imaging recipe for SB, LB and combined images: tclean parameters, weighting and robust value, uv taper, cell and image size, masks, clean threshold, deconvolver, and final beam and rms
- Self-calibration details: reference antenna, spectral-window combination, solution mode and number of iterations, clean masks per round, and SNR cuts
- Whether the 12CO and 13CO line spws were used only for continuum (after flagging) and any other flagging beyond the +/-25 km/s channels
- How the radial profile was extracted (annulus widths, centre, deprojection angles used) and how the per-radius sigma used for the '3 sigma' criterion was computed
- Image normalisation and any peak or beam used before comparing normalised radial profiles of the models and the data
- FARGO3D setup not given: aspect ratio or temperature profile and flaring index, equation of state, planet potential smoothing, dust diffusion and drag settings, number of outputs and the output snapshot used for comparison
- The modified FARGO3D mass-taper code (Delta_i offset parameter) is not stated to be released
- RADMC-3D settings: how dust temperatures were obtained, stellar parameters, opacity treatment per grain size, number of photon packages, scattering, and the inclination and PA applied to the model images
- galario settings used for the model VII visibilities and the imaging parameters applied to the simulated visibilities
- Gas temperature, H/r and Stokes numbers used when computing M_K and the minimum masses (Crida and Lodato) for alpha = 1e-4 and 1e-3
- Versions of FARGO3D, RADMC-3D and galario

## Analysis recipe

1. **Self-calibrate and combine SB and LB continuum data**: After pipeline calibration, flag +/-25 km/s around each line, average to 125 MHz channels, self-calibrate SB in two stages and LB separately, align phase centres, then average to one channel per spw and 30 s  
  > "First, we self-calibrated the shortest baseline observations, taken in April 2017, with solution intervals of $360\,$s, $150\,$s, $60\,$s, and $24\,$s for the phase calibration and $150\,$s for the amplitude calibration." (ALMA Observations / Calibration); "The LB data were self-calibrated independently from the SB data, with solution intervals of $360\,$s and $150\,$s for the phase calibration and $360\,$s for the amplitude." (ALMA Observations / Calibration); "After self-calibration, we reduced the data volume by averaging the continuum emission into one channel per spectral window and $30$ s of time binning." (ALMA Observations / Calibration)
   - software: CASA 5.6.2
   - parameter: Line channels flagged at +/-25 km/s  
  > "we flagged the channels located at $\pm 25\,$km s$^{-1}$ from each targeted spectral line" (ALMA Observations / Calibration)
   - parameter: 125 MHz channel averaging before self-calibration  
  > "the remaining channels from all spectral windows were averaged into 125 MHz channels" (ALMA Observations / Calibration)
   - parameter: SB second stage repeats the same solution intervals on SB joined with the October 2016 data  
  > "This calibrated dataset was joined with the remaining observations from SB taken on October 2016 and was again self-calibrated by repeating the same solution intervals." (ALMA Observations / Calibration)
   - parameter: Phase centres of all data shifted to the LB phase centre before combining  
  > "Before combining the datasets, we corrected their phase centers such that the center of all observations was the center of the LB dataset." (ALMA Observations / Calibration)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image SB, LB and combined data with JvM correction**: Images of SB, LB and SB+LB combined were made from the self-calibrated data and corrected with the JvM factor  
  > "Finally, we applied the JvM correction to the images generated from the self-calibrated datasets." (ALMA Observations / Calibration)
   - parameter: epsilon_v = 0.69 for SB and LB images; 0.88 for SB+LB combined  
  > "We find $\epsilon_v=0.69$ for the SB and LB images and $\epsilon_v=0.88$ for the images with SB and LB combined." (ALMA Observations / Calibration)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure the outer ring position, flux, optical depth and dust mass**: Deproject with inclination 45 deg and PA 150 deg to locate the outer ring peak; integrate SB-only image flux between 1.1'' and 2.5'' in an elliptical mask; estimate optical depth from the brightness temperature; estimate dust mass in the optically thin limit  
  > "we calculated the flux density from the image generated using only the SB dataset with an elliptical mask with the inclination and position angle of the source, and we integrated the emission between $1.1''-2.5''$" (Observational results: Outer ring); "When the disk is deprojected using the geometry from (cite: casassus_2019), with an inclination of $45^\circ$ and a position angle (PA) of $150^\circ$" (Observational results: Outer ring)
   - parameter: Integration annulus 1.1''-2.5'' in the SB-only image  
  > "we integrated the emission between $1.1''-2.5''$" (Observational results: Outer ring)
   - parameter: kappa_nu = 2.3 (nu/230 GHz)^0.4 cm^2 g^-1  
  > "$\kappa_\nu=2.3 \times (\nu/230\,\rm{GHz})^{0.4}\,\rm{cm}^{2}\rm{g}^{-1}$ is the frequency-dependent mass absorption coefficient (cite: andrews2013)" (Observational results: Outer ring)
   - parameter: Dust mass uncertainty taken as 10%  
  > "we obtained a dust mass of $0.7\pm0.07\,M_\oplus$, where we assumed a conservative uncertainty of $10\%$" (Observational results: Outer ring)
   - assumption: Optically thin emission with constant dust temperature T = 20 K  
  > "assuming that the flux ($F_\nu$) received at $0.9\,$mm is being emitted by dust with a constant temperature of $T=20\,$K (cite: ansdell2016; pinilla2018)" (Observational results: Outer ring)
   - assumption: Midplane physical temperature of 20 K constant for the optical depth estimate  
  > "and $T_{\text{phys}}$ is the physical temperature of the midplane, which we assumed to be $T_{\text{phys}}=20\,$K constant" (Observational results: Outer ring)
   - fitting: _not stated_
   - validation: Authors note the optical depth is highly uncertain because the physical temperature estimate is uncertain  
  > "This is highly uncertain, however, because the underlying estimate of $T_{\text{phys}}$ has a high level of uncertainty." (Observational results: Outer ring)
4. **Derive planet locations and masses from the radial profile**: Planet radii from local minima in the combined-image radial profile (inner 13 au taken from earlier work, outer 143 au from the local minimum); masses from gap-width relation M_K with K between 7 and 10, bounded below by the larger of the Crida and Lodato minimum gap-opening masses  
  > "We estimate the orbital separation of the outer planet to be at $143\,$au, corresponding to the local minimum in the observed intensity profile." (Planet locations); "where $M_K$ is the planet mass estimate, which depends on the dimensionless parameter $K$, the stellar mass $M_\star$, the orbit of the planet $r$, and the gap width in the millimeter dust continuum $D$" (Planet mass estimates); "From these two criteria, we estimated the minimum planet mass by choosing the maximum of the two models," (Planet mass estimates)
   - parameter: Gap widths D1 = 14 au (inner), D2 = 79 au (outer)  
  > "This yields $D_1=14$ au for the inner and $D_2=79$ au for the outer gap" (Planet mass estimates)
   - parameter: alpha = 1e-4 and 1e-3 used for the minimum-mass criteria  
  > "For $\alpha=10^{-4}$, we obtain $M_{\rm{min},1}=0.3\,M_{\rm{Jup}}$ for the inner and $M_{\rm{min},2}=1.7\,M_{\rm{Jup}}$ for the outer planet." (Planet mass estimates)
   - assumption: One planet per gap  
  > "It is important to note that the assumption that exactly one planet is responsible for each gap is a simplification." (Planet locations)
   - assumption: Lowest possible planet mass adopted for the simulations  
  > "We took the lowest possible mass for each of the planets for our simulations because planets have not directly been observed in this disk, and thus a lower-mass companion is more likely to exist." (Planet mass estimates)
   - fitting: _not stated_
   - validation: _not stated_
5. **Run 2D multifluid FARGO3D planet-disk simulations (models I-VII)**: Two-dimensional polar-grid FARGO3D runs with one gas and four dust fluids, with one or two planets of fixed orbit and time-tapered mass, for seven combinations of initial profile, taper timing and viscosity  
  > "The `FARGO3D` simulations were performed in two dimensions on a polar grid" (Hydrodynamic simulations with FARGO3D); "We used a multifluid approach and model the gaseous dusty disk around HD 100546 as five fluids: one fluid represents the gas, and the four remaining fluids describe the dust" (Hydrodynamic simulations with FARGO3D)
   - software: FARGO3D
   - parameter: Grid n_r = 540, n_phi = 1024, one cell per tenth of the pressure scale height  
  > "which equates to an azimuthal resolution of $n_\phi = 1024$ cells and a radial resolution of $n_r = 540$ cells" (Hydrodynamic simulations with FARGO3D)
   - parameter: r_min = 2.6 au, r_max = 500 au  
  > "They were calculated based on the planet Hill radius $R_H$ as $r_{\rm{min}}=(r_1-3 R_{H,1})/3 =2.6\,$au and $r_{\rm{max}}=3(r_2+3 R_{H,2})=500\,$au." (Hydrodynamic simulations with FARGO3D)
   - parameter: Run time 0.74 Myr  
  > "We instead ran our simulations for $0.74\,$Myr (corresponding to $2.3\times 10^4$ orbits of the inner planet or $6.3\times 10^2$ orbits of the outer planet)" (Hydrodynamic simulations with FARGO3D)
   - parameter: Self-similar initial profile with critical radius R_c = 80 au  
  > "Here, $R_c = 80\,$au is the critical radius" (Initial conditions)
   - parameter: Dust-to-gas mass ratio 1e-2  
  > "Here, $\epsilon = 10^{-2}$ corresponds to the dust-to-gas mass ratio, taken to be equal to the interstellar value" (Initial conditions)
   - parameter: Fiducial planet mass taper: delays zero, tapers 16 Kyr  
  > "We fiducially set the delays $\Delta_1$ and $\Delta_2$ to zero and the tapers $\tau_1$ and $\tau_2$ to $16\,$Kyr." (Mass-tapering model)
   - parameter: Model V: outer planet delay 6e5 yr; model VI: outer planet taper 6e5 yr  
  > "In model V we set $\Delta_2 = 6\times 10^5\,$yr while keeping $\tau_2 =16\,$Kyr, while in model VI, we kept $\Delta_2 = 0$ and set $\tau_2 = 6\times 10^5\,$yr." (Parameter space exploration)
   - parameter: Model VII: alpha = 1e-3 with outer planet 3 M_Jup  
  > "We chose a higher viscosity of $\alpha=10^{-3}$ in model VII." (Parameter space exploration)
   - assumption: Disk reaches a quasi-steady state within the simulated time  
  > "assuming that, qualitatively, the disk reaches a quasi-steady state within this time" (Hydrodynamic simulations with FARGO3D)
   - assumption: No accretion onto the planet  
  > "the actual physical accretion process is ignored in this present work, that is, there is no mass transfer from the dust or gas fluids onto the planet." (Mass-tapering model)
   - assumption: Planet orbit fixed, no migration  
  > "We also fixed the planets orbit and neglected its potential migration." (Mass-tapering model)
   - assumption: Dust growth neglected  
  > "In our current approach, however, we modeled gas and dust evolution simultaneously, but we neglected dust growth." (Discussion)
   - fitting: _not stated_
   - validation: Convergence in time (gas surface density stable from 200 Kyr) and a higher-resolution run (one-twentieth scale height) that changes the result little  
  > "show that our gas surface density does not vary significantly from $200\,$Kyr." (Convergence and resolution tests); "The result does not change significantly by the higher resolution." (Convergence and resolution tests)
6. **Generate synthetic observations with RADMC-3D (and galario for model VII)**: Expand FARGO3D 2D dust densities to 3D with a Gaussian vertical profile, run RADMC-3D at 0.9 mm with silicate opacities, convolve with a 0.3'' Gaussian beam; for model VII also compute visibilities with galario at the observed uv-coverage and image them  
  > "This requires expanding the two-dimensional dust surface density distributions into three dimensions, which we did by using a Gaussian distribution along the vertical ($z$) axis, assuming hydrostatic equilibrium in this direction" (Synthetic observations with RADMC-3D); "used the package `galario` to calculate the visibilities with the same uv-coverage as the observations" (Results)
   - software: RADMC-3D, galario
   - parameter: Wavelength 0.9 mm  
  > "the wavelength was fixed at $\lambda=0.9\,$mm" (Synthetic observations with RADMC-3D)
   - parameter: Convolution with a 0.3'' Gaussian beam  
  > "all synthetic observations are convolved with a $0.3''$ Gaussian beam similar to the actual observations" (Synthetic observations with RADMC-3D)
   - parameter: Dust settling factor chi = 3% for grains larger than 1 micron  
  > "and $\chi=3\%$ is the scale height reduction factor encoding the effect of dust settling" (Synthetic observations with RADMC-3D)
   - assumption: Disk composed of silicates with Jena-database optical constants  
  > "We assumed the disk to be composed of silicates ((cite: d95))" (Synthetic observations with RADMC-3D)
   - fitting: _not stated_
   - validation: Image-plane and visibility-plane synthetic images of model VII agree and reproduce the observed radial profile  
  > "Both images are consistent with each another and reproduce the observed radial profile, proving the observability of the structures generated in our simulations." (Results)
7. **Compare normalised radial profiles of models and ALMA data to select the best model**: Compare each synthetic image with the combined ALMA image, both normalised to their maxima, using azimuthally averaged normalised radial profiles and the deviation in sigma  
  > "For each setup, we present the corresponding synthetic observation and the combined ALMA image, both normalized to their respective maximum, and using the same color map." (Results); "In addition, we display the azimuthally averaged normalized radial profiles as a metric to compare the two images quantitatively." (Results)
   - parameter: Acceptance criterion: normalised radial profile within 3 sigma of the observation  
  > "Model IV is within a $3\sigma$ range around the observation in the normalized radial profile." (Results)
   - fitting: No sampler or likelihood; manual iteration over model setups until agreement is reached  
  > "we tested different planet setup scenarios until we reached the best possible agreement between the synthetic and real observations by comparing their respective images and radial profiles" (Introduction)
   - validation: Higher-viscosity model VII gives an azimuthally symmetric ring and a profile within 3 sigma  
  > "Consequently, model VII leads to the best agreement between our synthetic observation and the real one." (Results)

## Software

- **CASA** 5.6.2: Handling and self-calibrating the ALMA datasets  
  > "to handle and self-calibrate the datasets" (ALMA Observations / Calibration)
- **FARGO3D** : Multifluid 2D hydrodynamic planet-disk simulations (with modified mass-tapering)  
  > "The `FARGO3D` simulations were performed in two dimensions on a polar grid" (Hydrodynamic simulations with FARGO3D)
- **RADMC-3D** : Radiative transfer to render synthetic 0.9 mm observations  
  > "we performed a radiative transfer simulation and rendered a synthetic observation" (Synthetic observations with RADMC-3D)
- **galario** : Computing model visibilities at the observed uv-coverage  
  > "used the package `galario` to calculate the visibilities with the same uv-coverage as the observations" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| JvM epsilon_v, SB and LB images | 0.69 | not stated | dimensionless | 2 | We find $\epsilon_v=0.69$ for the SB and LB images and $\epsilon_v=0.88$ for the images with SB and LB combined. |
| JvM epsilon_v, SB+LB combined images | 0.88 | not stated | dimensionless | 2 | We find $\epsilon_v=0.69$ for the SB and LB images and $\epsilon_v=0.88$ for the images with SB and LB combined. |
| Outer ring peak radius | 1.85'' (200 au) | 0.1'' (11 au) | arcsec; au | 3 | we find that the outer disk peaks at $\approx1.85''\pm0.1''\,$ from the disk center, which is $200\pm11\,$au at the distance of the source |
| Outer ring flux density | 4.5 | 0.2 (excludes 10% flux-scale uncertainty) | mJy | 3 | We detect the ring to be $4.5\pm0.2\,$mJy, which does not include the $10\%$ ALMA flux uncertainty. |
| Outer ring peak optical depth | 0.005 | not stated | dimensionless | 3 | this very low temperature translates into an equally low estimated optical depth of $\tau_{\text{peak}}=0.005$ |
| Outer ring dust mass | 0.7 | 0.07 | Earth masses | 3 | we obtained a dust mass of $0.7\pm0.07\,M_\oplus$, where we assumed a conservative uncertainty of $10\%$ |
| Total dust disk mass (from combined 435 mJy continuum flux) | 66 | not stated | Earth masses | 3 | $M_{\rm{dust}}=66\,M_\oplus$ is the total dust disk mass obtained from the total observed flux of our combined ALMA dust continuum emission of $435$ mJy |
| Gap widths D1 (inner) and D2 (outer) | 14 au and 79 au | not stated | au | 4 | This yields $D_1=14$ au for the inner and $D_2=79$ au for the outer gap |
| Gap-width planet mass ranges M_K | 8-24 M_Jup (inner), 1.1-3.3 M_Jup (outer) | not stated | Jupiter masses | 4 | $8\,M_{\rm{Jup}}\leq M_{K,1} \leq 24\,M_{\rm{Jup}}$ for the inner and $1.1\,M_{\rm{Jup}} \leq M_{K,2} \leq 3.3\,M_{\rm{Jup}}$ for the outer planet |
| Minimum gap-opening masses for alpha = 1e-4 | 0.3 M_Jup (inner), 1.7 M_Jup (outer) | not stated | Jupiter masses | 4 | For $\alpha=10^{-4}$, we obtain $M_{\rm{min},1}=0.3\,M_{\rm{Jup}}$ for the inner and $M_{\rm{min},2}=1.7\,M_{\rm{Jup}}$ for the outer planet. |
| Best-fit planet orbits and masses (model VII) | inner 13 au, 8 M_Jup; outer 143 au, 3 M_Jup | not stated | au; Jupiter masses | 7 | an inner planet located at $r_1 = 13\,$au with a mass $M_1 = 8 M_{\rm{Jup}}$ and an outer planet located at $r_2 = 143\,$au with a mass $M_2 = 3 M_{\rm{Jup}}$ |
| Single-planet model I largest deviation (at 110 au) and model II deviation (at 200 au) | 133 sigma and 4 sigma | not stated | sigma | 7 | Model I reaches its largest deviation at $110\,$au with $133\sigma$, while it is $4\sigma$ at $200\,$au for model II. |
| Model III relative outer-to-inner peak intensity versus ALMA | 86 times higher | not stated | dimensionless | 7 | the relative peak intensity of the outer ring is $86$ times higher than in the ALMA observation |
| Reduction of outer substructure strength, model V relative to IV | ~80% | not stated | percent | 7 | This reduces the relative strength of the outer substructure by $\sim 80\%$ compared to model IV. |
| Reduction of outer ring flux, model VI relative to IV | ~40% | not stated | percent | 7 | This reduces the outer rings flux by $\sim 40\%$ relative to the base model IV. |

## Qualitative findings

- Two-planet models IV-VII stay within 3 sigma of the normalised radial profile, while one-planet models deviate by more than 3 sigma  
  > "the models with a single planet have an above-significant deviation ($>3\sigma$) from the observation, while the models with two planets IV-VII have a deviation of less than $3\sigma$ in the radial profile" (Discussion)
- alpha = 1e-3 removes the azimuthal asymmetry of the outer ring seen at alpha = 1e-4  
  > "The outer substructure in the synthetic observation of model VII agrees well with the ALMA observation because it does not display the asymmetry seen in previous models." (Results)
- The proposed planets (8 and 3 M_Jup) are below current ALMA direct-detection capability  
  > "This means that the detection of the proposed planets with $8\,M_{\rm{Jup}}$ and $3\,M_{\rm{Jup}}$ is still beyond our current ALMA capabilities." (Conclusions)

## Claim tuples

- H: Two embedded planets, not one, are needed to explain both the inner and the newly resolved outer ring | E: Compared one-planet (I, II) and two-planet (III-VII) FARGO3D plus RADMC-3D models with the combined ALMA image via normalised radial profiles | R: One-planet models deviate by more than 3 sigma (model I up to 133 sigma); two-planet models IV-VII are within 3 sigma | F: Two planets are required to reproduce both rings | **supported**
- H: The initial gas surface density profile affects the inner-to-outer ring brightness ratio | E: Ran power-law (models I, III) and self-similar (models II, IV) initial profiles | R: The power-law model III overestimates the outer ring peak intensity relative to the inner ring by a factor of 86; model IV reproduces the ratio | F: An exponentially tapered (self-similar) initial profile is needed | **supported**
- H: Planet masses and orbits can be constrained by matching the ALMA continuum | E: Planet radii and masses from the radial profile and gap-width relations, then tested in seven FARGO3D and RADMC-3D model setups | R: Model VII (alpha = 1e-3, self-similar profile) gives the best agreement and an azimuthally symmetric outer ring, with inner planet 8 M_Jup at 13 au and outer 3 M_Jup at 143 au | F: The best matching setup has inner planet 8 M_Jup at 13 au and outer planet 3 M_Jup at 143 au | **supported**
- H: The outer planet needs to be old and massive to produce the outer ring | E: Delayed the outer planet by 6e5 yr (model V) and tapered its mass over 6e5 yr (model VI) | R: Models IV, V and VI all stay within 3 sigma; a 1.7 M_Jup planet that began forming 140 Kyr before the end still induces the outer ring | F: Outer planet mass can be as low as 1.7-3 M_Jup, lower than earlier estimates, with formation timing not strongly constrained | **partially**
- H: The disk viscosity can be constrained by the symmetry of the outer ring | E: Compared alpha = 1e-4 models with alpha = 1e-3 model VII | R: Low alpha gives an asymmetric outer ring with strong accumulation absent in the ALMA image; alpha = 1e-3 gives a symmetric ring | F: Favours alpha of about 1e-3 or higher, though the asymmetry at low alpha may be an artefact of not modelling planetary accretion | **partially**

## Reasoning

- Why this data: Recent ALMA observations resolve the faint outer ring suggested in earlier work  
  > "we calibrated and analyzed recent ALMA observations of the system to identify the main features and focused on resolving the outer ring that was suggested in (cite: w14; p15)." (Introduction)
- Why this method: Assume planet-disk interaction drives the observed substructures and model it with hydrodynamics plus radiative transfer  
  > "in this work we assume the planet-disk interaction to be the main driver for the observed substructures of HD 100546" (Introduction)
- Alternative: Single-planet models I and II rejected because they produce no outer ring  
  > "However, these models do not create an outer ring because there is no second planet that might induce an outer trap." (Results)
- Alternative: Power-law initial gas profile rejected because the outer ring comes out too bright relative to the inner ring  
  > "In model III the outer structures are relatively bright compared to the inner ring, which is strongly overestimated" (Results)
- Alternative: Other ring-forming mechanisms (dead-zone edge, ice lines, magnetic disk winds) are mentioned but not tested  
  > "in this work we assume the planet-disk interaction to be the main driver for the observed substructures of HD 100546" (Introduction)
- How they decided it was enough: Iterated model setups until normalised radial profiles were within 3 sigma and the outer ring was azimuthally symmetric  
  > "Its normalized radial profile resides within a frame of $3\sigma$ around the detection." (Results); "we tested different planet setup scenarios until we reached the best possible agreement between the synthetic and real observations by comparing their respective images and radial profiles" (Introduction)
- Limitation (authors): Planet accretion not simulated; accumulation near the outer planet may be an artefact  
  > "the actual physical accretion process is ignored in this present work, that is, there is no mass transfer from the dust or gas fluids onto the planet." (Mass-tapering model)
- Limitation (authors): Planet orbits fixed, migration neglected  
  > "We also fixed the planets orbit and neglected its potential migration." (Mass-tapering model)
- Limitation (authors): Dust growth neglected  
  > "In our current approach, however, we modeled gas and dust evolution simultaneously, but we neglected dust growth." (Discussion)
- Limitation (authors): Simulations run for 0.74 Myr rather than the system age because of computational cost  
  > "However, a simulation of such a duration is computationally unfeasible because we need to choose a high grid resolution" (Hydrodynamic simulations with FARGO3D)
- Limitation (authors): Inner planet orbit could not be taken from a resolved local minimum  
  > "Because we were unable to resolve the corresponding local minimum, we reverted to the estimated planet position from previous studies" (Planet locations)
- Limitation (authors): One planet per gap is a simplification  
  > "It is important to note that the assumption that exactly one planet is responsible for each gap is a simplification." (Planet locations)
- Caveat (inferred, ours): Model selection is by eye over seven hand-picked setups with a 3 sigma criterion; no parameter grid, likelihood or uncertainties on planet mass or radius
- Caveat (inferred, ours): Planet masses are largely set by the gap-width formula (lowest K) and the Crida/Lodato floor, so the results depend on the assumed K, alpha and temperature rather than a fit
- Caveat (inferred, ours): The inner planet radius (13 au) is inherited from earlier work and not measured here
- Caveat (inferred, ours): Observation log table program IDs differ from those in the text
- Caveat (inferred, ours): Radial-profile sigma and the effect of image-plane normalisation on the comparison are not described
- Caveat (inferred, ours): Degeneracy between alpha, planet mass and formation timing is only partly explored

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: tclean and imaging parameters for the SB, LB and combined images
- Missing: Self-calibration details beyond solution intervals
- Missing: FARGO3D temperature, aspect ratio and numerical setup, and the modified mass-taper code
- Missing: RADMC-3D and galario settings, and the model inclination and PA
- Missing: Radial profile extraction and sigma definition used in the model comparison
- Missing: Resolution of the program ID discrepancy between text and observation table
- Data volume (inferred): Roughly 50-150 GB of raw ALMA data for the three execution blocks (one extended with 10.8 km baselines and two compact), with the 2D FARGO3D runs needing substantial compute but small data products
- Score (inferred): 3/5, ALMA data are public and self-calibration intervals are given, and the simulation grid and main parameters are tabulated, but imaging parameters, FARGO3D thermal setup, the modified code, and the profile-comparison details are missing, and the model comparison is manual
- Rediscovery candidate: no, Imaging recipe and simulation setup are incomplete and model selection is a manual iteration, so the main numbers (13 au/8 M_Jup, 143 au/3 M_Jup) could not be rederived without extra choices

## Links

- Method: Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41 (cite: andrews2018) (DSHARP calibration procedure followed for channel averaging)
- Method: Jorsater & van Moorsel 1995 (cite: jorsater1995); Andrews et al. 2021 (cite: andrews2021) (JvM correction of the images)
- Method: Benitez-Llambay & Masset 2016 (cite: b16); Masset 2000 (cite: m0) (FARGO3D code)
- Method: Dullemond et al. 2012 (cite: d12) (RADMC-3D radiative transfer code)
- Method: Casassus & Pérez 2019 (cite: casassus_2019) (Disk inclination and position angle used for deprojection)
- Companion: Pinilla, Birnstiel & Walsh 2015 (cite: p15) (Earlier two-planet model of HD 100546; source of the 13 au inner planet location and mass comparisons)
- Companion: Fedele et al. 2021 (cite: fedele2021) (Independent ALMA 870 micron analysis and SPH modelling of the same disk, compared in the discussion)
- Companion: Walsh et al. 2014 (cite: w14) (Earlier ALMA detection of the faint outer ring)
- Companion: Pérez et al. 2020 (cite: perez_2020) (Prior ALMA observations of the compact disk of HD 100546)
- Related: DSHARP

## Checks

```json
{
 "quotes": 158,
 "quotes_ok": 158,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.00934.S",
  "2016.1.01511.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 130,
  "stated": 101,
  "rate": 0.777
 },
 "evidence_ok": true
}
```
