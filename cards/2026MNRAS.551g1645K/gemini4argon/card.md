# A high-velocity SiO jet from S255N SMA3

`2026MNRAS.551g1645K` | Monthly Notices of the Royal Astronomical Society 2026 | first author: Klaassen, P. D. | arXiv: 2608.28177 | DOI: 10.1093/mnras/stag1645

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Characterize the shape, velocity structure, and physical and kinematic properties of the SiO jet from S255N SMA3, and evaluate whether it is driven by a steady-state magneto-centrifugal disk wind or wide-angle entrainment-driven outflows.  
  > "1. characterize the shape and velocity structure of the SiO jet 2. derive physical and kinematic properties of the jet, including temperature, mass, momentum, energy, and dynamical age" (Introduction); "3. evaluate whether the observed jet exhibits the velocity structure expected for steady-state magneto-centrifugal jets or wide-angle, entrainment-driven outflows" (Introduction)
- Target **S255N SMA3**: coordinates RA = 06:12:53.6384 +- 0.0002s, DEC = +18.00.18.467 +- 0.003''  
  > "Using the casa task imfit, we fit a 2D Gaussian profile to the continuum emission peak and find a peak position of RA = 06:12:53.6384 $\pm$ 0.0002s and DEC = +18.00.18.467 $\pm$ 0.003$''$" (Continuum emission and Core properties); "Maser parallax observations place SMA1 at a distance of 1.78 kpc (cite: Burns16)." (Introduction); "The local standard of rest velocity (V$_\textrm{LSR}$) of this region is 7.8 km s$^{-1}$." (Observations); z/distance 1.78 kpc; V_LSR = 7.8 km s^-1  
  > "Using the casa task imfit, we fit a 2D Gaussian profile to the continuum emission peak and find a peak position of RA = 06:12:53.6384 $\pm$ 0.0002s and DEC = +18.00.18.467 $\pm$ 0.003$''$" (Continuum emission and Core properties); "Maser parallax observations place SMA1 at a distance of 1.78 kpc (cite: Burns16)." (Introduction); "The local standard of rest velocity (V$_\textrm{LSR}$) of this region is 7.8 km s$^{-1}$." (Observations); distance from (cite: Burns16)  
  > "Using the casa task imfit, we fit a 2D Gaussian profile to the continuum emission peak and find a peak position of RA = 06:12:53.6384 $\pm$ 0.0002s and DEC = +18.00.18.467 $\pm$ 0.003$''$" (Continuum emission and Core properties); "Maser parallax observations place SMA1 at a distance of 1.78 kpc (cite: Burns16)." (Introduction); "The local standard of rest velocity (V$_\textrm{LSR}$) of this region is 7.8 km s$^{-1}$." (Observations)

## Data provenance

- ALMA projects: 2023.1.01346.S
- bands: Band 6  
  > "We present ALMA Band 6 observations of the compact source SMA3 in the S255IR region" (Abstract); "Observations of S255N were obtained as part of project 2023.1.01346.S (PI: K. Tanaka) in Cycle 10 using two 12-m array configurations (C-4 and C-7) of band 6 observations" (Observations)
- frequencies and spectral setup: Two spectral setups centred around 225 GHz and 250 GHz  
  > "covering two spectral setups: the first centred around 225 GHz, the other at 250 GHz." (Observations); "These setups allowed us to observe two transitions of SiO (the J=5-4 transition at 217.105 GHz, and the J=6-5 transition at 260.518 GHz) along with a large number of other molecular species and the dust continuum emission in both setups." (Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "using two 12-m array configurations (C-4 and C-7) of band 6 observations" (Observations)
- configurations: C-4 and C-7  
  > "using two 12-m array configurations (C-4 and C-7) of band 6 observations" (Observations)
- baselines: 15 m to 8500 m (C-4: 15-784 m; C-7: 67-8500 m)  
  > "| X408f | 225 GHz | 2023-10-01 | C-7 | 45 | 845 | 92 | 92 | 8500 | J0750+1231 |" (Table 1); "| X7d9d | 250 GHz | 2023-10-27 | C-7 | 48 | 917 | 85 | 67 | 8300 | J0423-0120 |" (Table 1); "| X136cb | 250 GHz | 2024-01-02 | C-4 | 46 | 212 | 94 | 15 | 784 | J0423-0120 |" (Table 1)
- angular resolution: Continuum: 0.08 x 0.06 arcsec; CS 5-4: 0.16 x 0.12 arcsec; SiO 5-4: 0.11 x 0.08 arcsec; SiO 6-5: 0.10 x 0.07 arcsec  
  > "| Continuum | 0.08 | 0.06 | 47.05 | 0.16 |" (Table 2); "| CS 5-4 | 0.16 | 0.12 | 30.58 | 1.04 |" (Table 2); "| SiO 5-4 | 0.11 | 0.08 | 135.25 | 1.34 |" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: Continuum: 0.16 mJy/beam; CS 5-4: 1.04 mJy/beam; SiO 5-4: 1.34 mJy/beam; SiO 6-5: 1.61 mJy/beam  
  > "| Continuum | 0.08 | 0.06 | 47.05 | 0.16 |" (Table 2); "| SiO 5-4 | 0.11 | 0.08 | 135.25 | 1.34 |" (Table 2); "| SiO 6-5 | 0.10 | 0.07 | 40.87 | 1.61 |" (Table 2)
- time on source: 845 s, 165 s, 917 s, 212 s, 213 s, 273 s, 273 s across 7 execution blocks  
  > "| X408f | 225 GHz | 2023-10-01 | C-7 | 45 | 845 | 92 | 92 | 8500 | J0750+1231 |" (Table 1); "| X375d | 250 GHz | 2023-10-26 | C-7 | 48 | 165 | 82 | 92 | 8500 | J0423-0120 |" (Table 1); "| X7d9d | 250 GHz | 2023-10-27 | C-7 | 48 | 917 | 85 | 67 | 8300 | J0423-0120 |" (Table 1)
- observing dates: 2023-10-01, 2023-10-26, 2023-10-27, 2024-01-01, 2024-01-02, 2024-05-19  
  > "| X408f | 225 GHz | 2023-10-01 | C-7 | 45 | 845 | 92 | 92 | 8500 | J0750+1231 |" (Table 1); "| X136cb | 250 GHz | 2024-01-02 | C-4 | 46 | 212 | 94 | 15 | 784 | J0423-0120 |" (Table 1); "| X28a0 | 250 GHz | 2024-05-19 | C-4 | 45 | 213 | 86 | 15 | 784 | J0423-0120 |" (Table 1)
- pi or archival as stated: PI: K. Tanaka, downloaded from the ALMA archive  
  > "Observations of S255N were obtained as part of project 2023.1.01346.S (PI: K. Tanaka) in Cycle 10" (Observations); "The data were downloaded from the ALMA archive, and the uv-plane calibrated measurement sets were restored using the CASA pipeline (cite: ALMA_pipeline)." (Observations)
- Line: SiO J = 5-4 (217.105 GHz)
- Line: SiO J = 6-5 (260.518 GHz)
- Line: CS J = 5-4 (not stated)
- Line: SiO J = 6-5 (v=1) (not stated)
- Line: CH3CN not stated (not stated)
- Other facility **Spitzer**: IR context emission  
  > "Figure 1 shows the ALMA continuum emission (in white contours) on the broader Spitzer IR emission in this region to put our observations into context." (Observations)
- Other facility **Cologne Database for Molecular Spectroscopy (CDMS)**: Spectroscopic data to derive molecular properties  
  > "The Cologne Database for Molecular Spectroscopy (CDMS) for spectroscopic data was used to derive molecular properties in this paper (cite: CDMS1; CDMS2)" (Acknowledgements)
- External data: Maser parallax distance to SMA1 of 1.78 kpc  
  > "Maser parallax observations place SMA1 at a distance of 1.78 kpc (cite: Burns16)." (Introduction) [from (cite: Burns16)]
- External data: SiO abundance of 10^-7 with respect to molecular hydrogen in shocked regions  
  > "Using an SiO abundance of $10^{-7}$ with respect to molecular hydrogen, appropriate for the shocked regions (cite: Schilke97)" (Derived Flow Dynamics) [from (cite: Schilke97)]
- External data: Mean molecular weight mu_mol  
  > "where $A_{\text{pixel}}$ is the pixel area in cm$^2$, $\mu_{\text{mol}}$ is the mean molecular weight (cite: Kauffmann08), and $m_p$ is the proton mass." (Derived Flow Dynamics) [from (cite: Kauffmann08)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were downloaded from the ALMA archive, and the uv-plane calibrated measurement sets were restored using the CASA pipeline (cite: ALMA_pipeline)." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Restored uv-plane calibrated measurement sets and pipeline self-calibrated continuum products used  
  > "The data were downloaded from the ALMA archive, and the uv-plane calibrated measurement sets were restored using the CASA pipeline (cite: ALMA_pipeline). Self calibration of the continuum was done in the pipeline, and those final data products were used here." (Observations)
- flux calibrator: J0750+1231, J0423-0120, J0510+1800  
  > "| X408f | 225 GHz | 2023-10-01 | C-7 | 45 | 845 | 92 | 92 | 8500 | J0750+1231 |" (Table 1); "| X375d | 250 GHz | 2023-10-26 | C-7 | 48 | 165 | 82 | 92 | 8500 | J0423-0120 |" (Table 1); "| X96e4 | 225 GHz | 2024-01-01 | C-4 | 49 | 273 | 102 | 15 | 784 | J0510+1800 |" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: Self calibration of the continuum was done in the pipeline  
  > "Self calibration of the continuum was done in the pipeline, and those final data products were used here." (Observations)

### Imaging

- task: tclean  
  > "and then jointly inverted into the image plane using tclean with interactively assigned clean boxes and natural weighting." (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "and then jointly inverted into the image plane using tclean with interactively assigned clean boxes and natural weighting." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: interactively assigned clean boxes  
  > "and then jointly inverted into the image plane using tclean with interactively assigned clean boxes and natural weighting." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "To image the spectral line data, we first used uvcontsub to subtract the continuum from the data in both observing configurations" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Combined uv-plane data from C-4 and C-7 configurations using concat and jointly inverted and cleaned  
  > "The datasets from the two array configurations were then combined, and jointly inverted and cleaned." (Observations); "combined the uv-plane data using concat, and then jointly inverted into the image plane using tclean" (Observations)
- smoothing: _not stated_
- final beam: Continuum: 0.08 x 0.06 arcsec (PA 47.05 deg); CS 5-4: 0.16 x 0.12 arcsec (PA 30.58 deg); SiO 5-4: 0.11 x 0.08 arcsec (PA 135.25 deg); SiO 6-5: 0.10 x 0.07 arcsec (PA 40.87 deg)  
  > "| Continuum | 0.08 | 0.06 | 47.05 | 0.16 |" (Table 2); "| CS 5-4 | 0.16 | 0.12 | 30.58 | 1.04 |" (Table 2); "| SiO 5-4 | 0.11 | 0.08 | 135.25 | 1.34 |" (Table 2)
- final rms: Continuum: 0.16 mJy/beam; CS 5-4: 1.04 mJy/beam; SiO 5-4: 1.34 mJy/beam; SiO 6-5: 1.61 mJy/beam  
  > "| Continuum | 0.08 | 0.06 | 47.05 | 0.16 |" (Table 2); "| CS 5-4 | 0.16 | 0.12 | 30.58 | 1.04 |" (Table 2); "| SiO 6-5 | 0.10 | 0.07 | 40.87 | 1.61 |" (Table 2)

### Inherited from earlier work

- Equation for deriving dust mass from continuum flux  
  > "we can derive the mass of emitting dust using the following equation derived from equation 4 of (cite: Hildebrand1983):" (Continuum emission and Core properties) [from (cite: Hildebrand1983)]
- Contour-tracing method for deriving jet opening angle (adapted to use half-power contour instead of quarter-power contour)  
  > "This method is similar to that used in (cite: Offner2011) and (cite: Dunham2024), however they instead used the ‘quarter power’ contour for their analysis because of better signal to noise ratios in their moment maps." (Opening and inclination angles and their implications for velocities and jet age) [from (cite: Offner2011) and (cite: Dunham2024)]
- Equations and methodology for deriving outflow kinematic properties (mass, momentum, energy)  
  > "Using the equations and methodology shown in (cite: Lopez09), we derive the kinematic properties of our jet." (Derived Flow Dynamics) [from (cite: Lopez09)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and ALMA pipeline version used for restoring measurement sets and imaging
- Value of dust opacity kappa_nu at 250 GHz used in Equation 1 to derive dust mass
- Spectral channel width / velocity resolution of the imaged spectral cubes
- Pixel size (cell size) and image dimensions used in tclean
- Whether primary beam correction was applied (important since SMA3 is offset by 6.5 arcsec from phase centre)
- Which SiO transition (5-4 or 6-5) is reported in the final kinematic summary table (Table 3)
- Line-free channel ranges used for uvcontsub
- Exact numerical value of mean molecular weight mu_mol adopted from Kauffmann et al. (2008)

## Analysis recipe

1. **Fit 250 GHz continuum source properties and derive core/disk inclination and mass**: Fit a 2D Gaussian profile to the 250 GHz continuum emission peak using CASA imfit; derive disk inclination from deconvolved axis ratio and compute dust and total gas+dust mass from integrated flux.  
  > "Using the casa task imfit, we fit a 2D Gaussian profile to the continuum emission peak" (Continuum emission and Core properties); "If we assume that the major and minor axes of the continuum emission are indicative of major and minor axes of a geometrically thin and circular protostellar disk, then we can derive an inclination angle for that disk." (Continuum emission and Core properties); "Using a temperature of 20K for the emission surrounding the protostar, we can derive the mass of emitting dust using the following equation derived from equation 4 of (cite: Hildebrand1983):" (Continuum emission and Core properties)
   - software: CASA
   - parameter: nu = 250 GHz  
  > "and $B_\nu(T_{\textrm{dust}})$ is the blackbody function with $\nu =$ 250 GHz and $T_\textrm{dust}$ = 20K." (Continuum emission and Core properties)
   - assumption: Geometrically thin and circular protostellar disk for inclination lower limit  
  > "If we assume that the major and minor axes of the continuum emission are indicative of major and minor axes of a geometrically thin and circular protostellar disk, then we can derive an inclination angle for that disk." (Continuum emission and Core properties)
   - assumption: T_dust = 20 K, distance d = 1.78 kpc, gas-to-dust ratio = 100  
  > "Using the integrated flux calculated above, and the distance to source of 1.78 kpc, we find a dust mass of $\sim$0.007$\pm$0.005 M$_\odot$, or a total gas and dust mass of $\sim$0.7$\pm$0.05 M$_\odot$ assuming a gas to dust ratio of 100." (Continuum emission and Core properties)
   - fitting: 2D Gaussian fit using CASA imfit  
  > "Using the casa task imfit, we fit a 2D Gaussian profile to the continuum emission peak" (Continuum emission and Core properties)
   - validation: _not stated_
2. **Construct moment maps, measure jet collimation, opening angle, inclination, de-projected velocity, length, and dynamical age**: Create moment 0 and moment 1 maps over +- 5-60 km/s; measure collimation ratio from red lobe extent over largest width; measure jet opening angle from half-power contour of SiO 5-4 integrated intensity; average disk and flow inclinations; de-project velocity and length to compute dynamical age for SiO and CS.  
  > "For both transitions, the velocity ranges (with respect to the local standard of rest, LSR, velocity) used for creating the moment maps was $\pm$ 5-60 km s$^{-1}$." (Jet Morphology and Velocity); "Deriving a jet collimation ratio from the red lobe (in both transitions of SiO), by dividing the full jet lobe extent by its largest width, we find a collimation ratio of 4.75." (Jet Morphology and Velocity); "We used the position of the protostar fitted in section 3.1 as the starting point for the jet, and the ‘half power’ contour from the integrated intensity of SiO (J=5-4) as shown in Figure 7." (Opening and inclination angles and their implications for velocities and jet age)
   - parameter: Velocity range for moment maps: +- 5 to 60 km s^-1 relative to V_LSR = 7.8 km s^-1  
  > "For both transitions, the velocity ranges (with respect to the local standard of rest, LSR, velocity) used for creating the moment maps was $\pm$ 5-60 km s$^{-1}$." (Jet Morphology and Velocity)
   - assumption: Azimuthal symmetry of the jet; opening angle is an upper limit on inclination angle; gas travelled at constant velocity since ejection  
  > "Assuming azimuthal symmetry, we can use the plane of sky opening angle as a proxy for and upper limit on the overall opening angle." (Opening and inclination angles and their implications for velocities and jet age); "we can derive an dynamical age of the outflow assuming that that gas initially left the protostellar environment at that same velocity." (Opening and inclination angles and their implications for velocities and jet age)
   - fitting: Opening angle measured by eye from three positions (protostar and inflection points on half-power contour)  
  > "From the three positions labelled in Figure 7, we derived an opening angle of 54.5$^\circ$." (Opening and inclination angles and their implications for velocities and jet age); "We only have formal uncertainties on the ‘disk’ derived inclination angle, since the ‘flow’ derived value was measured by eye." (Opening and inclination angles and their implications for velocities and jet age)
   - validation: Compare blue lobe size between SiO J=6-5 and J=5-4 to verify missing high-velocity blue-shifted bandpass in SiO 6-5 has minimal effect on lobe length  
  > "However, the blue jet lobe as seen in the J=6-5 transition in Figure 4 does appear to have a similar size as that in the J=5-4 transition in Figure 3, suggesting any missing jet length is minimal." (Jet Morphology and Velocity)
3. **Construct Position-Velocity (PV) diagrams along the jet axis and analyze episodic knots**: Extract PV diagrams along the jet axis for SiO J=5-4 and J=6-5; identify triangular velocity morphology and periodic vertical stripes of emission peaks at 0.2 arcsec intervals to calculate de-projected knot separation, ejection timescale, and Keplerian disk radius.  
  > "In Figure 8, we present PV diagrams for the SiO emission (J=5-4 and J=6-5, respectively in the left and right panels) along the jet axis" (Position-velocity diagrams, terminal velocities and episodic emission); "They are consistent between the two transitions and appear at roughly 0.2$''$ intervals in both the red- and blue-shifted parts of the diagrams." (Position-velocity diagrams, terminal velocities and episodic emission); "The periodic spacing of $\sim0.2''$ corresponds to a de-projected knot separation of $\sim540$ au and an ejection timescale of $\sim32$ yr, when using the derived jet velocity of 80 km s$^{-1}$." (Episodic Ejection)
   - parameter: PV contour levels: starting at 3 sigma in increments of 3 sigma; knot interval = 0.2 arcsec  
  > "The contours in Figure 8 start at 3 sigma, and increase in increments of 3 sigma." (Position-velocity diagrams, terminal velocities and episodic emission)
   - assumption: Keplerian disk rotation around a 0.7 M_sun protostar for translating periodicity timescale to disk radius  
  > "If this periodicity reflects a dynamical timescale in a Keplerian disk, this implies a radius of $\sim9$ au given the derived mass of 0.7 M$_\odot$." (Episodic Ejection)
   - fitting: _not stated_
   - validation: Consistency of 0.2 arcsec spacing between SiO 5-4 and 6-5 transitions and correspondence with temperature enhancements in excitation temperature map  
  > "They are consistent between the two transitions and appear at roughly 0.2$''$ intervals in both the red- and blue-shifted parts of the diagrams." (Position-velocity diagrams, terminal velocities and episodic emission); "Especially evident in the blue-shifted lobe (top-right of the figure) are temperature enhancements in the SiO gas periodically on these intervals, with gas temperatures reaching an excess of 60K." (Episodic Ejection)
4. **Derive pixel-by-pixel SiO excitation temperature across the jet**: Convert spectral cubes from Jy/beam to brightness temperature (K) using beam solid angle from radio_beam; mask both SiO cubes at 5 sigma and integrate over channels with signal; perform a two-level rotation diagram analysis on a pixel-by-pixel basis between SiO J=6-5 and J=5-4 to compute T_ex, and take the mean across the core of the two outflow lobes.  
  > "With observations of two rotational transitions of SiO, we derived an excitation temperature for the jet emission using a two-level rotation diagram analysis." (Excitation Conditions Along the Jet); "We used the common_beam method in the radio_beam package to derive $\Omega$ directly from the headers of the input FITS files, and as presented in Table 1." (Excitation Conditions Along the Jet); "We masked the data cubes for both SiO transitions at 5 sigma, and then created integrated intensity maps of the emission by summing over the channels with signal." (Excitation Conditions Along the Jet)
   - software: radio_beam, Astropy
   - parameter: 5 sigma masking threshold for integrated intensity maps  
  > "We masked the data cubes for both SiO transitions at 5 sigma, and then created integrated intensity maps of the emission by summing over the channels with signal." (Excitation Conditions Along the Jet)
   - assumption: Local thermodynamic equilibrium (LTE) and optically thin emission  
  > "Using the assumption that the overall gas population is in local thermodynamic equilibrium (LTE), and that the emission is optically thin, the column density in a given energy level can be related to the overall column density of that species" (Excitation Conditions Along the Jet)
   - fitting: Two-level rotation diagram slope between SiO J=6-5 and J=5-4 per pixel  
  > "We calculated $\text{ln}(N_u/g_u)$ in both transitions and subsequently derived the excitation temperature on a pixel-by-pixel basis because our maps were created on the same pixel grid." (Excitation Conditions Along the Jet)
   - validation: Excluded northern edge near target where derived temperature (>200 K) and uncertainty are high  
  > "Near the target, on the northern edge of the jet, the derived temperature is quite high (in excess of 200 K), as is the uncertainty on the estimate in that region. Therefore, we take a mean temperature of the gas from the core of the two outflow lobes, excluding this region." (Excitation Conditions Along the Jet)
5. **Derive outflow column densities, mass, momentum, kinetic energy, mass flow rate, force, and power**: Mask SiO cubes at 3 sigma; calculate SiO column density per velocity channel using T_ex = 42 K and partition function; convert to H2 column density using SiO abundance of 10^-7; sum over pixels and velocity channels to compute mass, inclination-corrected momentum and kinetic energy, and divide by dynamical age (343 yr) for rates.  
  > "With the intensity expressed as a temperature, and the data masked at 3 sigma, the column density in each velocity channel can be derived using the intensity of the line." (Derived Flow Dynamics); "Using an SiO abundance of $10^{-7}$ with respect to molecular hydrogen, appropriate for the shocked regions (cite: Schilke97), this SiO column density was then converted to an average molecular column density per velocity channel using this conversion factor." (Derived Flow Dynamics); "With the jet age derived in Section 3.2.1, we can further derive mass loss ($\dot{\textrm{M}}$), outflow force ($\dot{\textrm{P}}$) and power ($\dot{\textrm{E}}$) by dividing these values by the outflow age." (Derived Flow Dynamics)
   - software: Astropy
   - parameter: 3 sigma masking threshold; T_ex = 42 K; V_LSR = 7.8 km s^-1; inclination i = 48.6 +- 15 deg; dynamical age = 343 +- 181 yr  
  > "We find a mean excitation temperature of 42 K. We use this temperature in our kinematic calculations below." (Excitation Conditions Along the Jet); "With the intensity expressed as a temperature, and the data masked at 3 sigma, the column density in each velocity channel can be derived using the intensity of the line." (Derived Flow Dynamics)
   - assumption: Optically thin emission; LTE at T_ex = 42 K; SiO/H2 abundance = 10^-7; distance = 1.78 kpc  
  > "Using an SiO abundance of $10^{-7}$ with respect to molecular hydrogen, appropriate for the shocked regions (cite: Schilke97)" (Derived Flow Dynamics); "Given the distance to the target (1.78 kpc) we can quantify the linear area of each pixel" (Derived Flow Dynamics); "Since, in the optically thin regime, this calculation is a summation of particles along the line of sight, no correction for inclination is required." (Derived Flow Dynamics)
   - fitting: _not stated_
   - validation: Uncertainties propagated in quadrature from spectral rms noise and half the velocity resolution; compared derived values against Ophiuchus and Serpens flows  
  > "The uncertainties used in these calculations come from the rms noise in the spectra, and half the velocity resolution of the observations, which are propogated through the calculations in quadrature." (Derived Flow Dynamics); "We can compare these values to those derived for flows in Ophiucus (cite: Nienke13) and Serpens (cite: Plunkett2015), which themselves have a wide range in flow force values ($10^{-3}$-10$^{-7}$ M$_\odot$ km s$^{-1}$ yr$^{-1}$) ." (Derived Flow Dynamics)

## Software

- **CASA** : Pipeline restoration of measurement sets, continuum subtraction (uvcontsub), concatenating configurations (concat), imaging (tclean), and 2D Gaussian continuum fitting (imfit)  
  > "The data were downloaded from the ALMA archive, and the uv-plane calibrated measurement sets were restored using the CASA pipeline (cite: ALMA_pipeline)." (Observations); "To image the spectral line data, we first used uvcontsub to subtract the continuum from the data in both observing configurations, combined the uv-plane data using concat, and then jointly inverted into the image plane using tclean" (Observations); "Using the casa task imfit, we fit a 2D Gaussian profile to the continuum emission peak" (Continuum emission and Core properties)
- **radio_beam** : Deriving beam solid angle Omega from FITS headers using the common_beam method  
  > "We used the common_beam method in the radio_beam package to derive $\Omega$ directly from the headers of the input FITS files, and as presented in Table 1." (Excitation Conditions Along the Jet)
- **Astropy** : Core Python astronomy package used in analysis  
  > "This work made use of Astropy: a community-developed core Python package and an ecosystem of tools and resources for astronomy (cite: astropy:2013; astropy:2018; astropy:2022)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMA3 250 GHz continuum deconvolved major axis | 110.1 | +- 10.3 | mas | 1 | and a resolved source size of 110.1 $\pm$ 10.3 mas $\times$ 80.9$\pm$8.9 mas at a position angle of 16$\pm$17 deg when deconvolved from the synthesised beam. |
| SMA3 250 GHz continuum deconvolved minor axis | 80.9 | +- 8.9 | mas | 1 | and a resolved source size of 110.1 $\pm$ 10.3 mas $\times$ 80.9$\pm$8.9 mas at a position angle of 16$\pm$17 deg when deconvolved from the synthesised beam. |
| SMA3 250 GHz continuum deconvolved position angle | 16 | +- 17 | deg | 1 | and a resolved source size of 110.1 $\pm$ 10.3 mas $\times$ 80.9$\pm$8.9 mas at a position angle of 16$\pm$17 deg when deconvolved from the synthesised beam. |
| Disk inclination angle (from continuum axis ratio) | 42.7 | +- 9 | deg | 1 | Using the values and uncertainties above, we derive an inclination of 42.7$\pm9^{\circ}$. |
| SMA3 250 GHz continuum integrated flux density | 18.6 | +- 1.2 | mJy | 1 | The integrated intensity of the fit to the continuum emission is 18.6 $\pm$ 1.2 mJy, which we can use to derive a mass for the protostellar disk/envelope. |
| SMA3 core dust mass | 0.007 | +- 0.005 | M_sun | 1 | Using the integrated flux calculated above, and the distance to source of 1.78 kpc, we find a dust mass of $\sim$0.007$\pm$0.005 M$_\odot$, or a total gas and dust mass of $\sim$0.7$\pm$0.05 M$_\odot$ assuming a gas to dust ratio of 100. |
| SMA3 core total gas and dust mass | 0.7 | +- 0.05 | M_sun | 1 | Using the integrated flux calculated above, and the distance to source of 1.78 kpc, we find a dust mass of $\sim$0.007$\pm$0.005 M$_\odot$, or a total gas and dust mass of $\sim$0.7$\pm$0.05 M$_\odot$ assuming a gas to dust ratio of 100. |
| SiO jet collimation ratio | 4.75 | not stated | dimensionless | 2 | Deriving a jet collimation ratio from the red lobe (in both transitions of SiO), by dividing the full jet lobe extent by its largest width, we find a collimation ratio of 4.75. |
| SiO jet opening angle | 54.5 | not stated | deg | 2 | From the three positions labelled in Figure 7, we derived an opening angle of 54.5$^\circ$. |
| Adopted mean system inclination angle | 48.6 | +- 15 | deg | 2 | However, expanding the uncertainty on the mean to include the lower limit from the ‘disk’ derived inclination results in roughly $48.6\pm15^\circ$, which we will use for the remainder of this work. |
| SiO jet peak line-of-sight velocity | 60 | not stated | km s^-1 | 2 | The radial velocities of the SiO gas peak around $\pm$ 60 km s$^{-1}$ from the LSR velocity of the target in both the red and blue shifted lobes. |
| SiO jet de-projected total velocity | 80 | +- 18 | km s^-1 | 2 | Using this equation, we find $v_{\textrm{tot}} \simeq 80\pm18$ km s$^{-1}$. |
| SiO jet de-projected length | 5800 | +- 1700 | au | 2 | Using the same inclination angle to de-project the plane-of-sky jet length, the average measured plane of sky SiO jet lobe length of 2.15$''$ (or 3830 au at a distance of 1.78 kpc) translates to a jet length of 5800$\pm$1700 au. |
| SiO jet dynamical age | 343 | +- 181 | yr | 2 | We derive a kinematic age for the SiO outflow 343$\pm$181 yr. |
| CS outflow peak line-of-sight velocity | 50 | not stated | km s^-1 | 2 | We can also apply the same age analysis to the CS emission, which has a peak line of sight velocity of 50 km s$^{-1}$ in both the red and blue lobes. |
| CS outflow de-projected length | 7270 | +- 2160 | au | 2 | Using the same inclination angle as the SiO jet, we calculate an outflow length of 7270$\pm$2160 au and derive a kinematic age of 520$\pm$270 yr for the high velocity CS emission |
| CS outflow kinematic age | 520 | +- 270 | yr | 2 | Using the same inclination angle as the SiO jet, we calculate an outflow length of 7270$\pm$2160 au and derive a kinematic age of 520$\pm$270 yr for the high velocity CS emission |
| Mean SiO excitation temperature | 42 | not stated | K | 4 | We find a mean excitation temperature of 42 K. We use this temperature in our kinematic calculations below. |
| De-projected episodic knot separation | 540 | not stated | au | 3 | The periodic spacing of $\sim0.2''$ corresponds to a de-projected knot separation of $\sim540$ au and an ejection timescale of $\sim32$ yr, when using the derived jet velocity of 80 km s$^{-1}$. |
| Episodic ejection timescale | 32 | not stated | yr | 3 | The periodic spacing of $\sim0.2''$ corresponds to a de-projected knot separation of $\sim540$ au and an ejection timescale of $\sim32$ yr, when using the derived jet velocity of 80 km s$^{-1}$. |
| Inferred Keplerian disk modulation radius | 9 | not stated | au | 3 | If this periodicity reflects a dynamical timescale in a Keplerian disk, this implies a radius of $\sim9$ au given the derived mass of 0.7 M$_\odot$. |
| Red lobe SiO column density N[SiO] | 6.34 | +- 0.02 | 10^16 cm^-2 | 5 | / Red / 6.34$\pm$0.02 / 6.35$\pm$0.02 / 2.183$\pm$0.008 / 1.111$\pm$0.004 / 6.11$\pm$0.03 / 0.6$\pm$0.3 / 3$\pm$2 / 18$\pm$9 / |
| Blue lobe SiO column density N[SiO] | 6.32 | +- 0.02 | 10^16 cm^-2 | 5 | / Blue / 6.32$\pm$0.02 / 6.32$\pm$0.02 / 2.129$\pm$0.008 / -0.899$\pm$0.004 / 4.23$\pm$0.02 / 0.6$\pm$0.3 / 3$\pm$1 / 12$\pm$7 / |
| Red lobe H2 column density N[H2] | 6.35 | +- 0.02 | 10^23 cm^-2 | 5 | / Red / 6.34$\pm$0.02 / 6.35$\pm$0.02 / 2.183$\pm$0.008 / 1.111$\pm$0.004 / 6.11$\pm$0.03 / 0.6$\pm$0.3 / 3$\pm$2 / 18$\pm$9 / |
| Blue lobe H2 column density N[H2] | 6.32 | +- 0.02 | 10^23 cm^-2 | 5 | / Blue / 6.32$\pm$0.02 / 6.32$\pm$0.02 / 2.129$\pm$0.008 / -0.899$\pm$0.004 / 4.23$\pm$0.02 / 0.6$\pm$0.3 / 3$\pm$1 / 12$\pm$7 / |
| Red lobe outflow mass | 2.183 | +- 0.008 | 10^-3 M_sun | 5 | / Red / 6.34$\pm$0.02 / 6.35$\pm$0.02 / 2.183$\pm$0.008 / 1.111$\pm$0.004 / 6.11$\pm$0.03 / 0.6$\pm$0.3 / 3$\pm$2 / 18$\pm$9 / |
| Blue lobe outflow mass | 2.129 | +- 0.008 | 10^-3 M_sun | 5 | / Blue / 6.32$\pm$0.02 / 6.32$\pm$0.02 / 2.129$\pm$0.008 / -0.899$\pm$0.004 / 4.23$\pm$0.02 / 0.6$\pm$0.3 / 3$\pm$1 / 12$\pm$7 / |
| Red lobe outflow momentum | 1.111 | +- 0.004 | 10^-1 M_sun km/s | 5 | / Red / 6.34$\pm$0.02 / 6.35$\pm$0.02 / 2.183$\pm$0.008 / 1.111$\pm$0.004 / 6.11$\pm$0.03 / 0.6$\pm$0.3 / 3$\pm$2 / 18$\pm$9 / |
| Blue lobe outflow momentum | -0.899 | +- 0.004 | 10^-1 M_sun km/s | 5 | / Blue / 6.32$\pm$0.02 / 6.32$\pm$0.02 / 2.129$\pm$0.008 / -0.899$\pm$0.004 / 4.23$\pm$0.02 / 0.6$\pm$0.3 / 3$\pm$1 / 12$\pm$7 / |
| Red lobe outflow kinetic energy | 6.11 | +- 0.03 | 10^43 erg | 5 | / Red / 6.34$\pm$0.02 / 6.35$\pm$0.02 / 2.183$\pm$0.008 / 1.111$\pm$0.004 / 6.11$\pm$0.03 / 0.6$\pm$0.3 / 3$\pm$2 / 18$\pm$9 / |
| Blue lobe outflow kinetic energy | 4.23 | +- 0.02 | 10^43 erg | 5 | / Blue / 6.32$\pm$0.02 / 6.32$\pm$0.02 / 2.129$\pm$0.008 / -0.899$\pm$0.004 / 4.23$\pm$0.02 / 0.6$\pm$0.3 / 3$\pm$1 / 12$\pm$7 / |
| Red lobe mass flow rate | 0.6 | +- 0.3 | 10^-5 M_sun/yr | 5 | / Red / 6.34$\pm$0.02 / 6.35$\pm$0.02 / 2.183$\pm$0.008 / 1.111$\pm$0.004 / 6.11$\pm$0.03 / 0.6$\pm$0.3 / 3$\pm$2 / 18$\pm$9 / |
| Blue lobe mass flow rate | 0.6 | +- 0.3 | 10^-5 M_sun/yr | 5 | / Blue / 6.32$\pm$0.02 / 6.32$\pm$0.02 / 2.129$\pm$0.008 / -0.899$\pm$0.004 / 4.23$\pm$0.02 / 0.6$\pm$0.3 / 3$\pm$1 / 12$\pm$7 / |
| Red lobe outflow force | 3 | +- 2 | 10^-4 M_sun km/s/yr | 5 | / Red / 6.34$\pm$0.02 / 6.35$\pm$0.02 / 2.183$\pm$0.008 / 1.111$\pm$0.004 / 6.11$\pm$0.03 / 0.6$\pm$0.3 / 3$\pm$2 / 18$\pm$9 / |
| Blue lobe outflow force | 3 | +- 1 | 10^-4 M_sun km/s/yr | 5 | / Blue / 6.32$\pm$0.02 / 6.32$\pm$0.02 / 2.129$\pm$0.008 / -0.899$\pm$0.004 / 4.23$\pm$0.02 / 0.6$\pm$0.3 / 3$\pm$1 / 12$\pm$7 / |
| Red lobe outflow power | 18 | +- 9 | 10^40 erg/yr | 5 | / Red / 6.34$\pm$0.02 / 6.35$\pm$0.02 / 2.183$\pm$0.008 / 1.111$\pm$0.004 / 6.11$\pm$0.03 / 0.6$\pm$0.3 / 3$\pm$2 / 18$\pm$9 / |
| Blue lobe outflow power | 12 | +- 7 | 10^40 erg/yr | 5 | / Blue / 6.32$\pm$0.02 / 6.32$\pm$0.02 / 2.129$\pm$0.008 / -0.899$\pm$0.004 / 4.23$\pm$0.02 / 0.6$\pm$0.3 / 3$\pm$1 / 12$\pm$7 / |

## Qualitative findings

- The SiO emission traces a highly collimated, symmetric bipolar jet spine, while CS emission traces lower-velocity gas near the protostar and only reaches high velocities further downstream where SiO declines.  
  > "The emission shows clear chemical and kinematic differentiation: SiO traces the high-velocity jet spine, while CS is observed at lower velocities close to the protostar, and only reaches high velocities at larger distances." (Abstract)
- Position-velocity diagrams show a continuous triangular velocity structure with a velocity spread at the base of the flow, consistent with a steady magneto-centrifugal disk wind launched over a range of radii rather than an X-wind or wide-angle entrained flow.  
  > "Importantly, and consistently within the first moment maps in Figures 3 and 4, the base of the flow exhibits a clear velocity spread rather than a single narrow high-velocity spike." (Position-velocity diagrams, terminal velocities and episodic emission); "The PV structure with its layered velocity distribution close to the source and moderate inclination-corrected terminal speeds of $\sim$80 km s$^{-1}$, is therefore most consistent with a magneto-centrifugal disk wind." (Position-velocity diagrams, terminal velocities and episodic emission)
- Vertical emission stripes in the PV diagrams and periodic temperature enhancements (>60 K) spaced by ~0.2 arcsec (~540 au, ~32 yr) indicate quasi-periodic modulation of the wind likely originating from disk processes at ~9 au.  
  > "Especially evident in the blue-shifted lobe (top-right of the figure) are temperature enhancements in the SiO gas periodically on these intervals, with gas temperatures reaching an excess of 60K." (Episodic Ejection); "We favour an interpretation in which the observed knots in the wind launched from within 1 au arise from some form of modulation process or structure further out in the disk (at the $\sim9$ au radius)." (Implications for Jet Launching and Disk–Jet Coupling)
- Well-ordered, narrowly collimated, disk-driven jets can be launched and maintained even within dense, clustered high-mass star-forming regions.  
  > "This demonstrates that well-ordered, narrowly collimated, disk-driven jets can be launched and maintained even in the dense, competitive environments characteristic of high-mass star formation." (Abstract)

## Claim tuples

- H: The SMA3 jet is driven by a steady magneto-centrifugal disk wind launched over a range of disk radii rather than an X-wind or wide-angle entrainment-driven outflow. | E: Analyze the spatial morphology, moment 0 and 1 maps, and position-velocity (PV) diagrams of SiO (J=5-4 and 6-5) emission along the jet axis. | R: The jet has a collimation ratio of 4.75, de-projected velocity of ~80 km s^-1, and a two-sided triangular PV morphology with a broad velocity spread at the base and layered velocity stratification (lower velocities along the edges, highest velocities along the central axis). | F: The SMA3 jet is powered by a steady magneto-centrifugal disk wind launched from radii of order 0.5-1 au rather than an X-wind or wide-angle entrained flow. | **supported**
- H: Shock processing along the SMA3 jet produces chemical and kinematic stratification between grain-sputtering tracers (SiO) and denser post-shock/entrained gas tracers (CS). | E: Compare moment 0 and moment 1 maps and spectra of SiO (J=5-4, 6-5) and CS (J=5-4) across the SMA3 outflow. | R: SiO traces the high-velocity (+-60 km s^-1 LOS) jet spine over ~5800 au (age ~343 yr) with little emission at V_LSR, whereas CS peaks at V_LSR near the core and shows high-velocity (+-50 km s^-1 LOS) knots further out at ~7270 au (age ~520 yr) after SiO intensity declines. | F: The jet is chemically and kinematically stratified: SiO forms promptly in fast grain-processing shocks along the spine, while CS traces cooler, denser post-shock and entrained gas further downstream. | **supported**
- H: Periodic emission peaks and temperature enhancements along the jet trace quasi-periodic modulation of the wind from the protostellar disk. | E: Measure spacing of vertical emission stripes in SiO PV diagrams and compare with pixel-by-pixel LTE excitation temperature maps derived from the SiO (6-5)/(5-4) ratio. | R: Emission peaks and temperature enhancements (>60 K vs mean 42 K) recur at ~0.2 arcsec intervals, corresponding to a de-projected separation of ~540 au and an ejection timescale of ~32 yr, which matches a Keplerian orbital timescale at ~9 au around a 0.7 M_sun protostar. | F: While the 80 km s^-1 jet is launched within <1 au, its mass-loading or ejection is quasi-periodically modulated on a ~32 yr timescale by disk processes or substructures at ~9 au. | **supported**
- H: Compact, well-ordered, disk-driven jets can form and persist without disruption inside dense, clustered high-mass star-forming regions. | E: Measure the symmetry, collimation, dynamical age, and energetics (mass, momentum, energy) of the SMA3 jet embedded within the S255N massive star-forming clump. | R: The red and blue lobes have nearly identical masses (~2.18x10^-3 and 2.13x10^-3 M_sun), column densities, and mass flow rates (0.6x10^-5 M_sun/yr), maintaining a collimation ratio of 4.75 and linear axis over ~343-520 yr. | F: Even within a clustered high-mass star-forming environment, a protostar can launch and maintain a highly symmetric, collimated, and dynamically coherent disk-driven jet similar to those in isolated low-mass protostars. | **supported**

## Reasoning

- Why this data: High angular resolution (<0.1 arcsec) Band 6 ALMA observations in two configurations (C-4 and C-7) resolve the compact SMA3 continuum core and two rotational transitions of SiO (5-4 and 6-5) plus CS (5-4) to probe shock excitation, morphology, and kinematics.  
  > "This paper presents new ALMA Band 6 observations of SMA3, providing sub-arcsecond resolution imaging of the sub-mm continuum, SiO, and CS emission." (Introduction)
- Why this method: Using the mean of the continuum-axis inclination (lower limit) and jet opening angle (upper limit) brackets the true system inclination; per-channel column density integration provides more accurate momentum and kinetic energy estimates than integrated line profiles.  
  > "We explore both options below and use their mean value for further analysis, since the former defines a lower limit and the latter an upper limit on the true inclination angle." (Opening and inclination angles and their implications for velocities and jet age); "This per-channel method allows for more detailed momentum calculations." (Derived Flow Dynamics)
- Alternative: X-wind jet launching model: rejected because PV diagrams show a broad velocity spread at the base of the flow rather than a single narrow high-velocity spike from a narrow launching annulus.  
  > "Importantly, and consistently within the first moment maps in Figures 3 and 4, the base of the flow exhibits a clear velocity spread rather than a single narrow high-velocity spike. This morphology matches the expected PV signature of a disk wind launched over a range of radii, rather than an X-wind confined to a narrow launching annulus." (Position-velocity diagrams, terminal velocities and episodic emission)
- Alternative: Quarter-power contour for jet opening angle measurement (as in Offner et al. 2011 and Dunham et al. 2024): replaced with half-power contour due to signal-to-noise ratio considerations.  
  > "This method is similar to that used in (cite: Offner2011) and (cite: Dunham2024), however they instead used the ‘quarter power’ contour for their analysis because of better signal to noise ratios in their moment maps." (Opening and inclination angles and their implications for velocities and jet age)
- Alternative: Rotational signature analysis in dense core tracers (CS, CH3CN): not pursued because jet velocities dominate the kinematics and rotational signals cannot be distinguished.  
  > "It could be expected that these higher density tracers might show rotational signatures in the protostellar core or potentially even a protostellar disk, however their dynamics are dominated by the jet velocities, and any rotational signal cannot be distinguished from their emission profiles." (Continuum emission and Core properties)
- How they decided it was enough: _not stated_
- Limitation (authors): The 260 GHz spectral window did not have SiO 6-5 at its centre, so the highest blue-shifted emission from SiO 6-5 was not captured in the bandpass.  
  > "We note that the 260 GHz spectral window was not setup with SiO 6-5 in its centre, and the highest blue-shifted emission from that line is not captured in our bandpass." (Observations)
- Limitation (authors): The continuum emission may trace a geometrically thick protostellar envelope rather than a thin disk, making the disk-derived inclination angle only a lower limit.  
  > "However, since this is expected to be a very young region, it is unclear whether this assumption is valid, and we could instead be seeing a geometrically thick protostellar envelope." (Continuum emission and Core properties)
- Limitation (authors): The flow-derived opening angle (54.5 deg) was measured by eye and lacks formal uncertainties.  
  > "We only have formal uncertainties on the ‘disk’ derived inclination angle, since the ‘flow’ derived value was measured by eye." (Opening and inclination angles and their implications for velocities and jet age)
- Limitation (authors): Internal shocks may decelerate the overall flow velocity, affecting kinematic age estimates.  
  > "we calculate an outflow length of 7270$\pm$2160 au and derive a kinematic age of 520$\pm$270 yr for the high velocity CS emission, with the caveat that any internal shocks may be decreasing the overall flow velocity." (Opening and inclination angles and their implications for velocities and jet age)
- Limitation (authors): High excitation temperatures (>200 K) and large uncertainties on the northern edge of the jet near the target required excluding that region when computing the mean excitation temperature.  
  > "Near the target, on the northern edge of the jet, the derived temperature is quite high (in excess of 200 K), as is the uncertainty on the estimate in that region." (Excitation Conditions Along the Jet)
- Caveat (inferred, ours): The dust opacity value kappa_nu at 250 GHz used to compute the 0.007 M_sun dust mass (and 0.7 M_sun total mass) is never stated in the text.
- Caveat (inferred, ours): The SiO J=6-5 (0.10 x 0.07 arcsec) and J=5-4 (0.11 x 0.08 arcsec) maps have slightly different synthesized beams and position angles (40.87 deg vs 135.25 deg), and it is not explicitly stated whether the cubes were smoothed to a common resolution before the pixel-by-pixel excitation temperature ratio was computed (though radio_beam's common_beam method is mentioned).
- Caveat (inferred, ours): Slight internal numerical inconsistencies in the text: the plane-of-sky SiO lobe length is stated as 2.15 arcsec in Section 3.2.1 but 1.65 arcsec in Section 5, and the terminal velocity is stated as ~80 km/s throughout but ~74 km/s at the end of Section 4.2.
- Caveat (inferred, ours): Assuming optically thin SiO emission and a fixed SiO/H2 abundance of 10^-7 introduces substantial systematic uncertainty in the outflow mass, momentum, and energy that dwarfs the small formal statistical uncertainties reported in Table 3.

## Reproducibility

- Data public (paper): Available in the ALMA Science Archive under project code 2023.1.01346.S  
  > "The data underlying this article are available in the ALMA Science Archive at https://almascience.eso.org/asax/, under project code 2023.1.01346.S" (Data Availability)
- Products in archive: _not stated_
- Missing: Value of dust opacity kappa_nu at 250 GHz used in Equation 1
- Missing: Exact spatial masks/regions used to define the red and blue lobes and to exclude the noisy northern edge in the excitation temperature average
- Missing: Exact velocity channel width used in tclean and whether cubes were convolved to a common beam prior to pixel-by-pixel ratio
- Missing: Which SiO transition (or combination) is tabulated in Table 3
- Missing: Interactive clean masks used during tclean
- Data volume (inferred): ~50-150 GB (7 execution blocks of Cycle 10 Band 6 12-m data in C-4 and C-7 configurations)
- Score (inferred): 72/5, Archival ALMA project code, calibrators, execution blocks, weighting, continuum subtraction task, and all analytic equations for physical and kinematic quantities are clearly stated. However, a few key numerical parameters (dust opacity kappa_nu, channel width, cell size, exact spatial integration polygons, and which SiO transition is shown in Table 3) are omitted.
- Rediscovery candidate: yes, The ALMA data (2023.1.01346.S) are public, the reduction uses standard pipeline-restored visibilities plus natural-weighted tclean, and the main results (continuum Gaussian fit, jet velocity, collimation ratio, LTE excitation temperature, and outflow mass/momentum/energy) are concrete numeric targets.

## Links

- Method: (cite: Hildebrand1983) (Dust mass derivation from submillimetre continuum flux (Equation 1))
- Method: (cite: Offner2011) (Contour-based method for measuring outflow opening angles)
- Method: (cite: Dunham2024) (Contour-based method for measuring outflow opening angles)
- Method: (cite: Lopez09) (Equations and per-channel methodology for deriving outflow column density, mass, momentum, and kinetic energy)
- Method: (cite: Kauffmann08) (Mean molecular weight mu_mol used in mass derivation)

## Checks

```json
{
 "quotes": 177,
 "quotes_ok": 177,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 3,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 37,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 74,
  "rate": 0.804
 },
 "evidence_ok": true
}
```
